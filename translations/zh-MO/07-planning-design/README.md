[![Planning Design Pattern](../../../translated_images/zh-MO/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(點擊上方圖片觀看本課程影片)_

# 規劃設計

## 介紹

本課程將涵蓋

* 訂立清晰的整體目標，並將複雜任務拆解成可管理的任務。
* 利用結構化輸出以獲得更可靠且機器可讀的回應。
* 採用事件驅動方法來處理動態任務和意外輸入。

## 學習目標

完成本課程後，您將了解：

* 確定並設定 AI 代理的一個整體目標，確保其清楚知道需要達成的事項。
* 將複雜任務拆解成可管理的子任務，並將它們組織成合乎邏輯的順序。
* 為代理配備合適的工具（例如搜尋工具或資料分析工具），決定何時以及如何使用，並處理出現的意外狀況。
* 評估子任務結果、衡量表現，並透過迭代行動以改進最終輸出。

## 訂定整體目標及拆解任務

![Defining Goals and Tasks](../../../translated_images/zh-MO/defining-goals-tasks.d70439e19e37c47a.webp)

大多數現實世界的任務複雜到無法一步完成。AI 代理需要一個簡明的目標來指導其規劃與行動。例如，考慮以下目標：

    「產生一個三天的旅行行程。」

雖然目標簡單明確，但仍需進一步細化。目標越清晰，代理（以及任何人類協作者）越能專注於達成正確的結果，如製作包含航班選項、飯店推薦與活動建議的完整行程。

### 任務拆解

大型或複雜的任務在分割成較小且具目標導向的子任務後會變得更易處理。
對於旅行行程範例，可以拆解成：

* 航班預訂
* 飯店預訂
* 租車服務
* 個人化選項

每個子任務可由專屬代理或流程處理。一個代理可能專注於搜尋最佳航班優惠，另一個專注飯店預訂，以此類推。最後由協調或「下游」代理將這些結果彙整成一個完整的行程給最終使用者。

此模組化方法也方便增量改良。例如，您可以新增專門負責美食推薦或當地活動建議的代理，並隨時間優化行程。

### 結構化輸出

大型語言模型（LLMs）可產出結構化輸出（如 JSON），便於下游代理或服務解析與處理。在多代理系統中尤其有用，能在取得規劃結果後執行相關任務。可參考此<a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">部落格文章</a>快速了解。

以下 Python 範例展示一個簡單的規劃代理如何將目標拆解成子任務並生成結構化計劃：

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
    assigned_agent: AgentEnum  # 我們想要將任務分配給代理

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # 要與模型進行身份驗證，您需要在 GitHub 設定中產生個人存取權杖（PAT）。
    # 按照此處的指示建立您的 PAT 權杖：https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
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

# # 確保回應內容為有效的 JSON 字串後再進行載入
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# 如果 response_content 為空：
#     觸發 ValueError("回應內容不是有效的 JSON 字串")

# # 載入 JSON 後列印回應內容
# pprint(json.loads(response_content))

# 使用 MathReasoning 模型驗證回應內容
# TravelPlan.model_validate(json.loads(response_content))
```

### 多代理協調的規劃代理範例

在本範例中，一個語義路由代理接收使用者請求（例如，「我需要一個旅行飯店規劃。」）。

規劃代理接著：

* 接收飯店計劃：根據系統提示（包含可用代理資訊），將使用者訊息轉換為結構化旅行計劃。
* 列出代理與其工具：代理登錄表包含代理清單（例如航班、飯店、租車和活動代理）以及它們所提供的功能或工具。
* 將計劃分派給各代理：視子任務數量，規劃者要麼直接傳送訊息給單一專項代理（單任務情況），要麼透過群組聊天管理器協調多代理合作。
* 總結結果：最後，規劃者會針對產生的計劃提供摘要說明。

以下 Python 程式碼示範這些步驟：

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
    assigned_agent: AgentEnum # 我們想將任務分配給代理

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# 使用類型檢查過的環境變量創建客戶端

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# 定義用戶訊息

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

# 在加載響應內容前，確保其為有效的 JSON 字串

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# 將響應內容作為 JSON 加載後列印

pprint(json.loads(response_content))
```

以下為先前程式碼的輸出，您可以利用此結構化輸出將工作指派給 `assigned_agent`，並將旅行計劃摘要回傳給最終使用者。

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

示範筆記本包含先前程式碼範例，[請點此查看](07-autogen.ipynb)。

### 迭代規劃

有些任務需要反覆溝通或重新規劃，其中一個子任務的結果會影響下一步。例如，若代理在訂購航班時發現意外的資料格式，可能需調整策略後再進行飯店預訂。

此外，使用者回饋（例如人類決定偏好較早航班）也可觸發部分重新規劃。這種動態迭代方法確保最終解決方案符合現實限制和持續變化的使用者偏好。

範例程式碼如下

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. 與之前的代碼相同並傳遞用戶歷史、當前計劃
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
# .. 重新計劃並將任務發送給相應的代理
```

想要更完整的規劃功能，請參考 Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">部落格文章</a>，該系統專門解決複雜任務。

## 總結

本文示範如何打造一個能動態選擇可用代理的規劃者。規劃者的輸出會拆解任務並分配代理執行，前提是假設代理能存取執行任務所需的功能與工具。除代理之外，您還可以加入其他模式，如反思、摘要及輪流聊天，以進一步自訂。

## 其他資源

AutoGen Magentic One — 一個通用多代理系統，擅長解決複雜任務，且在多個具挑戰性的代理基準測試中取得亮眼成果。參考資料：<a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>。該實作中，調度者會製作任務專用規劃，並將任務委派給可用代理，除此之外還採用追蹤機制監控任務進度，並按需重新規劃。

### 對於規劃設計模式還有疑問嗎？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) 與其他學習者交流，參加線上辦公時間，並獲得您的 AI 代理相關問題解答。

## 上一課

[打造可信賴的 AI 代理](../06-building-trustworthy-agents/README.md)

## 下一課

[多代理設計模式](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件係使用人工智能翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 翻譯而成。雖然我們致力於確保翻譯的準確性，但請留意自動翻譯可能包含錯誤或不準確之處。原始文件之原文版本應視為具權威性的來源。對於重要資訊，建議採用專業人工翻譯。我們對因使用本翻譯所引致之任何誤解或誤釋概不負責。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->