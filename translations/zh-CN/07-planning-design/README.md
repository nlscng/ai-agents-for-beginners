[![Planning Design Pattern](../../../translated_images/zh-CN/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(点击上方图片观看本课视频)_

# 规划设计

## 介绍

本课将涵盖

* 定义明确的总体目标，并将复杂任务分解为可管理的子任务。
* 利用结构化输出以获得更可靠、更易机器读取的响应。
* 应用事件驱动的方法来处理动态任务和意外输入。

## 学习目标

完成本课后，您将了解：

* 确定并设定 AI 代理的总体目标，确保其明确知道需要达成的内容。
* 将复杂任务分解成可管理的子任务，并将它们组织成逻辑顺序。
* 为代理配备合适的工具（例如搜索工具或数据分析工具），决定何时以及如何使用这些工具，并处理出现的意外情况。
* 评估子任务结果，衡量性能，并迭代操作以改进最终输出。

## 定义总体目标与分解任务

![Defining Goals and Tasks](../../../translated_images/zh-CN/defining-goals-tasks.d70439e19e37c47a.webp)

多数现实任务复杂，无法一步完成。AI 代理需要一个简明目标来指导其规划和行动。例如，考虑以下目标：

    “生成三天的旅行行程。”

虽然表述简单，但仍需细化。目标越明确，代理（以及任何人类协作者）越能专注于实现正确的结果，比如创建包含航班选择、酒店推荐和活动建议的全面行程。

### 任务分解

大型或复杂任务在分解为较小的、面向目标的子任务后更易管理。
以旅行行程为例，可以将目标分解为：

* 机票预订
* 酒店预订
* 租车
* 个性化定制

每个子任务可以由专门的代理或流程处理。一个代理可能专注于寻找最佳机票优惠，另一个专门负责酒店预订，依此类推。一个协调或“下游”代理可以将这些结果整合成一个统一的行程提供给最终用户。

此模块化方法也支持逐步增添功能。例如，您可以添加专门负责餐饮推荐或本地活动建议的代理，并随时间完善行程。

### 结构化输出

大型语言模型（LLMs）可生成结构化输出（如 JSON），使下游代理或服务更易解析和处理。这在多代理环境中特别有用，我们可以在收到规划输出后执行相应任务。请参考此<a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">博客文章</a>以快速了解。

以下 Python 代码演示了一个简单的规划代理如何将目标分解为子任务并生成结构化计划：

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

# 旅行子任务模型
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # 我们想将任务分配给代理

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # 要认证该模型，您需要在GitHub设置中生成个人访问令牌（PAT）。
    # 按照此处的说明创建您的PAT令牌：https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# 定义用户消息
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

# # 在加载之前确保响应内容是有效的JSON字符串
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("响应内容不是有效的JSON字符串")

# # 作为JSON加载后打印响应内容
# pprint(json.loads(response_content))

# 用MathReasoning模型验证响应内容
# TravelPlan.model_validate(json.loads(response_content))
```

### 带多代理编排的规划代理

本示例中，语义路由代理接收用户请求（如“我需要一份旅行酒店计划”）。

规划者接着：

* 接收酒店计划：规划者根据用户消息和系统提示（含可用代理详情），生成结构化的旅行计划。
* 列出代理及其工具：代理注册表保存代理列表（如机票、酒店、租车和活动代理）及其提供的函数/工具。
* 将计划路由到相应代理：根据子任务数量，规划者要么直接发送消息给专属代理（单任务场景），要么通过群聊管理器协调多代理协作。
* 汇总结果：最后，规划者总结生成的计划以增强清晰度。

以下 Python 代码示例展示上述步骤：

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

# 旅行子任务模型

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # 我们想要将任务分配给代理

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# 使用类型检查的环境变量创建客户端

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# 定义用户消息

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

# 确保响应内容是有效的JSON字符串后再加载

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# 在将响应内容加载为JSON后打印它

pprint(json.loads(response_content))
```

以下是上述代码的输出，您可以使用此结构化输出路由至 `assigned_agent` 并向最终用户汇总旅行计划。

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

含上述代码示例的示范笔记本可在[此处](07-autogen.ipynb)获取。

### 迭代规划

部分任务需反复沟通或重新规划，一个子任务的结果会影响下一个。例如，若代理在预订机票时发现意外的数据格式，则可能需要调整策略后再进行酒店预订。

此外，用户反馈（如用户偏好提前航班）可触发局部重新规划。这种动态迭代的方法保证最终方案符合真实限制和不断变化的用户偏好。

示例代码：

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. 与之前的代码相同，并传递用户历史记录、当前计划
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
# .. 重新规划并将任务发送给相应的代理
```

如需更全面的规划，建议查看 Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">博客文章</a>，它专注于解决复杂任务。

## 总结

本文示例展示了如何构建一个规划者动态选择可用代理。规划者输出分解任务并分配代理以执行。假设代理拥有执行任务所需的函数/工具。除了代理，还可加入反思、汇总和轮询聊天等模式以进一步定制。

## 额外资源

AutoGen Magnetic One——一款通用多代理系统，用于解决复杂任务，并在多个具有挑战性的代理基准上取得优异成绩。参考：[autogen-magentic-one](https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one)。该实现中，编排者创建特定任务计划并将任务分配给可用代理。除了规划，编排者还采用跟踪机制监控任务进展，并根据需要重新规划。

### 对规划设计模式有更多疑问？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) ，与其他学习者交流，参加答疑时段，获取 AI 代理相关问题解答。

## 上一课

[构建可信赖的 AI 代理](../06-building-trustworthy-agents/README.md)

## 下一课

[多代理设计模式](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免责声明**：  
本文件是使用AI翻译服务[Co-op Translator](https://github.com/Azure/co-op-translator)翻译的。虽然我们力求准确，但请注意自动翻译可能包含错误或不准确之处。原始文件的母语版本应被视为权威来源。对于重要信息，建议使用专业人工翻译。因使用本翻译而引起的任何误解或误释，我们概不负责。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->