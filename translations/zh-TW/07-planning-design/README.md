[![規劃設計模式](../../../translated_images/zh-TW/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(點擊上圖以觀看本課程影片)_

# 規劃設計

## 介紹

本課程將涵蓋

* 定義明確的整體目標並將複雜任務拆解為可管理的子任務。
* 利用結構化輸出以獲得更可靠且機器可讀的回應。
* 採用事件驅動的方式來處理動態任務及意外輸入。

## 學習目標

完成本課程後，您將了解：

* 識別並設定 AI 代理的整體目標，確保其清楚了解需要達成的事項。
* 將複雜任務拆分為可管理的子任務，並將其組織成合乎邏輯的順序。
* 配置代理所需的工具（例如搜尋工具或數據分析工具），決定何時及如何使用，並處理突發情況。
* 評估子任務成果、衡量效能，並透過迭代行動提升最終輸出。

## 定義整體目標並拆解任務

![定義目標與任務](../../../translated_images/zh-TW/defining-goals-tasks.d70439e19e37c47a.webp)

大多數現實世界的任務過於複雜，無法一次完成。AI 代理需要一個簡明的目標以指導其規劃和行動。例如，考慮以下目標：

    「生成一份 3 天的旅遊行程。」

雖然敘述簡單，但仍需加以細化。目標越清晰，代理（以及任何人類協作者）就能越專注於達成正確的結果，比如製作包含航班選擇、飯店推薦和活動建議的完整行程。

### 任務拆解

將大型或複雜任務拆分成小且具目標性的子任務，使其更易管理。
以旅遊行程為例，可將目標拆解為：

* 訂機票
* 訂飯店
* 租車
* 個人化需求

每個子任務可由專屬的代理或流程處理。一個代理可能專注搜尋最優惠的機票，另一個專注飯店訂房，如此類推。接著由協調或「下游」代理將這些結果整合成一份完整的行程提供給最終使用者。

此模組化方式也方便逐步升級。例如，你可以增設專門的代理，提供餐飲推薦或當地活動建議，並隨時間優化行程。

### 結構化輸出

大型語言模型 (LLMs) 可以產生結構化輸出（例如 JSON），供下游代理或服務更輕鬆解析和處理。這在多代理上下文中特別有用，因為我們可在規劃輸出完成後，針對這些任務採取行動。請參考這篇 <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">部落格文章</a> 以快速了解。

以下 Python 程式碼片段示範一個簡單的規劃代理如何拆解目標為子任務並生成結構化計畫：

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
    assigned_agent: AgentEnum  # 我們想將任務指派給代理人

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # 要驗證模型，您需要在 GitHub 設定中產生個人存取權杖 (PAT)
    # 請按照此處說明建立您的 PAT 權杖：https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
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

# # 載入前確保回應內容為有效的 JSON 字串
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# 如果 response_content 是 None：
#     拋出 ValueError("回應內容不是有效的 JSON 字串")

# # 在將回應載入為 JSON 後列印內容
# pprint(json.loads(response_content))

# 使用 MathReasoning 模型驗證回應內容
# TravelPlan.model_validate(json.loads(response_content))
```

### 帶有多代理協調的規劃代理

此範例中，語義路由代理接收使用者請求（例如「我需要一份旅程飯店計畫。」）。

規劃者接著：

* 收取飯店計畫：規劃者根據系統提示（包含可用代理詳細資訊）並搭配使用者訊息，產生結構化的旅行計畫。
* 列出代理與其工具：代理登錄表列有代理清單（例如負責航班、飯店、租車和活動）及其提供的功能或工具。
* 將計畫路由至對應代理：視子任務數量，規劃者會直接將訊息送給專門代理（單一任務場景），或透過群組聊天管理員協調多代理合作。
* 彙整結果摘要：最後，規劃者將產生的計畫做出摘要說明以利理解。

下方 Python 範例程式碼說明這些步驟：

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

# 旅遊子任務模型

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # 我們想要將任務指派給代理

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# 使用類型檢查的環境變數建立客戶端

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

# 確保回應內容是有效的 JSON 字串後再進行載入

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# 以 JSON 格式載入後列印回應內容

pprint(json.loads(response_content))
```

接下來是前述程式碼的輸出，您可以利用此結構化輸出將任務路由給 `assigned_agent`，並將旅遊計畫摘要呈現給最終使用者。

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

先前程式碼範例的筆記本示例可於[此處](07-autogen.ipynb)取得。

### 迭代規劃

有些任務需來回調整或重新規劃，其間一個子任務的結果會影響下一步。例如，若代理在訂機票時發現意外的資料格式，可能必須調整策略後再繼續飯店預訂。

此外，使用者回饋（例如決定改訂較早航班）也會觸發部分重新規劃。這種動態且迭代的方法能確保最終解決方案符合實際限制與不斷演變的使用者偏好。

範例程式碼

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. 與先前代碼相同並傳遞用戶歷史記錄、當前計劃
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
# .. 重新規劃並將任務發送給各相應代理人
```

欲深入瞭解更完整的規劃，請參考 Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">部落格文章</a>，探討如何解決複雜任務。

## 總結

本文示範了如何建立一個能動態選擇已定義代理的規劃者。規劃者的輸出會拆解任務並分配代理以執行任務。假設這些代理具備執行任務所需的功能或工具。除了代理外，你還可以加入反思、摘要器和輪流聊天等模式，進一步客製化流程。

## 其他資源

AutoGen Magentic One — 一個通用型多代理系統，專門用來解決複雜任務，並在多個具挑戰性的代理基準中取得亮眼成果。參考：<a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>。此實作中，協調者會制定專門任務計畫並將任務分派給可用代理。除了規劃，協調者還會利用追蹤機制監控任務進展並在需要時重新規劃。

### 想了解更多規劃設計模式的疑問？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，與其他學習者交流，參加辦公時間並取得 AI 代理相關問題解答。

## 前一課

[打造可靠的 AI 代理](../06-building-trustworthy-agents/README.md)

## 下一課

[多代理設計模式](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件係使用人工智慧翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們致力於翻譯的準確性，但請注意自動翻譯結果可能包含錯誤或不準確之處。原始文件的母語版本應視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們對因使用本翻譯所產生之任何誤解或誤釋不負任何責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->