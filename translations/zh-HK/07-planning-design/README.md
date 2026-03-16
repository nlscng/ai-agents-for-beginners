[![規劃設計模式](../../../translated_images/zh-HK/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(按上方圖片以觀看本課影片)_

# 規劃設計

## 簡介

本課將涵蓋

* 定義清晰的整體目標，並將複雜任務拆解為可管理的子任務。
* 利用結構化輸出以獲得更可靠和機器可讀的回應。
* 採用事件驅動的方法來處理動態任務和意外輸入。

## 學習目標

完成本課後，你將會了解：

* 為 AI 代理識別並設定整體目標，確保其清楚知道需要達成什麼。
* 將複雜任務分解為可管理的子任務，並按邏輯順序組織。
* 為代理配備合適的工具（例如：搜尋工具或數據分析工具），決定何時及如何使用，並處理出現的意外情況。
* 評估子任務結果、衡量表現，並反覆調整行動以改進最終輸出。

## 定義整體目標並拆解任務

![定義目標與任務](../../../translated_images/zh-HK/defining-goals-tasks.d70439e19e37c47a.webp)

大多數真實世界的任務過於複雜，無法一步完成。AI 代理需要一個簡潔的目標來指導其規劃與行動。例如，考慮目標：

    "生成一個 3 日旅遊行程。"

雖然陳述起來很簡單，但仍需要進一步細化。目標越清晰，代理（以及任何人類協作者）就越能專注於達成正確的結果，例如建立包含航班選項、酒店推薦及活動建議的完整行程。

### 任務拆解

將大型或複雜任務拆分為較小、以目標為導向的子任務，可使任務更易管理。
以旅遊行程為例，你可以將目標拆解為：

* 機票預訂
* 酒店預訂
* 租車
* 個人化

每個子任務都可以由專責的代理或流程處理。一個代理可能專注於搜尋最划算的航班交易，另一個則專注於酒店預訂，依此類推。一個協調或「下游」代理可以將這些結果彙整成一個對最終使用者一致的行程。

這種模組化的方法也允許逐步增強。例如，你可以新增專門提供餐飲推薦或本地活動建議的代理，並隨時間持續優化行程內容。

### 結構化輸出

大型語言模型（LLMs）能產生結構化輸出（例如 JSON），下游代理或服務更容易解析與處理。這在多代理情境中特別有用，當我們在接收到規劃輸出後可以據此執行這些任務。參考這篇 <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">文章</a> 以獲取快速概述。

以下 Python 範例展示一個簡單的規劃代理，將目標分解為子任務並產生結構化計劃：

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# 旅遊子任務模型
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # 我們想把任務分配給代理人

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # 要對模型進行驗證，你需要在 GitHub 設定中產生個人存取權杖 (PAT)。
    # 按照以下說明建立你的 PAT 令牌： https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# 定義使用者訊息
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # 在載入前確保回應內容為有效的 JSON 字串
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Response content is not a valid JSON string")

# # 在以 JSON 載入後印出回應內容
# pprint(json.loads(response_content))

# 使用 MathReasoning 模型驗證回應內容
# TravelPlan.model_validate(json.loads(response_content))
```

### 具多代理協同的規劃代理

在此範例中，一個語意路由代理（Semantic Router Agent）接收使用者請求（例如：「我需要一個旅行的酒店計劃。」）。

規劃器接著會：

* 接收酒店計劃：規劃器接收使用者訊息，並根據系統提示（包括可用代理的詳細資訊）產生結構化的旅遊計劃。
* 列出代理及其工具：代理註冊表保存代理清單（例如：航班、酒店、租車和活動）以及它們提供的函數或工具。
* 將計劃路由給相應代理：根據子任務數量，規劃器要麼直接將訊息發送給專門代理（單一任務情境），要麼透過群組聊天管理器協調多代理合作。
* 總結結果：最後，規劃器會將產生的計劃進行總結以便說明。
以下 Python 範例程式碼說明這些步驟：

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# 旅行子任務模型

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # 我們想把任務指派給代理人

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# 使用經過型別檢查的環境變數建立客戶端

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# 定義使用者訊息

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# 在載入之前確保回應內容是有效的 JSON 字串

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# 在以 JSON 載入後印出回應內容

pprint(json.loads(response_content))
```

接下來是先前程式碼的輸出，你可以使用這個結構化輸出來路由到 `assigned_agent` 並向最終使用者總結旅遊計劃。

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

包含先前程式碼範例的示例 notebook 可在 [這裡](07-autogen.ipynb) 取得。

### 迭代規劃

有些任務需要來回反覆或重新規劃，其中一個子任務的結果會影響下一步。例如，若代理在訂航班時發現意外的資料格式，可能需要在繼續處理酒店預訂前調整策略。

此外，使用者反饋（例如人類決定偏好較早的班機）也會觸發部分重新規劃。這種動態、迭代的方法可確保最終解決方案與實際限制及不斷變化的使用者偏好一致。

e.g sample code

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. 與之前的程式相同，並傳遞用戶的歷史紀錄及當前計劃
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. 重新規劃並將任務發送給各自的代理
```

如需更全面的規劃，請參閱 Magnetic One 的 <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">文章</a>，以解決複雜任務。

## 總結

在本文中，我們示範了如何建立一個能動態選擇定義好之可用代理的規劃器。規劃器的輸出會將任務拆解並指派給代理，以便執行。假設代理能存取執行任務所需的函數/工具。除了代理之外，你還可以加入其他模式，如反思（reflection）、總結器（summarizer）以及輪詢聊天（round robin chat）來進一步自訂流程。

## 其他資源

AutoGen Magentic One - 一個通用的多代理系統，用於解決複雜任務，並在多個具有挑戰性的代理基準上取得令人印象深刻的成果。參考：<a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>。在此實作中，協調者會建立任務特定的計劃並將這些任務委派給可用的代理。除了規劃之外，協調者還採用追蹤機制來監控任務進度並在需要時重新規劃。

### 想進一步了解規劃設計模式嗎？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) 與其他學習者交流、參加辦公時段，並獲得有關 AI 代理的問題解答。

## 前一課

[建立值得信賴的 AI 代理](../06-building-trustworthy-agents/README.md)

## 下一課

[多代理設計模式](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：
本文件已使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們力求準確，但請注意自動翻譯可能包含錯誤或不準確之處。原文應視為具權威性的版本。對於關鍵資訊，建議採用專業人工翻譯。對於因使用此翻譯而引致的任何誤解或曲解，我們概不負責。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->