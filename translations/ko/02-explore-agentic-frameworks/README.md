[![Exploring AI Agent Frameworks](../../../translated_images/ko/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(위 이미지를 클릭하면 이 강의의 동영상을 볼 수 있습니다)_

# AI 에이전트 프레임워크 탐색

AI 에이전트 프레임워크는 AI 에이전트의 생성, 배포 및 관리를 단순화하도록 설계된 소프트웨어 플랫폼입니다. 이 프레임워크들은 개발자에게 복잡한 AI 시스템 개발을 간소화하는 사전 구축된 구성 요소, 추상화 및 도구를 제공합니다.

이 프레임워크들은 AI 에이전트 개발의 공통 과제에 대한 표준화된 접근 방식을 제공함으로써 개발자가 자신의 애플리케이션 고유의 측면에 집중할 수 있도록 돕습니다. 또한 AI 시스템 구축의 확장성, 접근성 및 효율성을 향상시킵니다.

## 소개

본 강의에서는 다음 내용을 다룹니다:

- AI 에이전트 프레임워크란 무엇이며, 개발자들이 무엇을 달성할 수 있게 해주는가?
- 팀이 이를 사용하여 에이전트의 기능을 빠르게 프로토타입하고 반복 개선할 수 있는 방법은?
- Microsoft의 <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, 그리고 <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>에서 만든 프레임워크와 도구들의 차이점은 무엇인가?
- 기존의 Azure 생태계 도구를 직접 통합할 수 있는가, 아니면 독립 실행형 솔루션이 필요한가?
- Azure AI 에이전트 서비스란 무엇이며, 이것이 어떻게 도움이 되는가?

## 학습 목표

이 강의의 목표는 다음을 이해하는 데 도움을 주는 것입니다:

- AI 개발에서 AI 에이전트 프레임워크의 역할
- AI 에이전트 프레임워크를 활용해 지능형 에이전트를 구축하는 방법
- AI 에이전트 프레임워크가 제공하는 주요 기능
- AutoGen, Semantic Kernel, Azure AI Agent Service 간의 차이점

## AI 에이전트 프레임워크란 무엇이며, 개발자들이 무엇을 할 수 있게 해주나요?

전통적인 AI 프레임워크는 AI를 앱에 통합하고 앱을 개선하는 다음과 같은 방법을 제공합니다:

- **개인화**: AI가 사용자 행동과 선호도를 분석하여 맞춤형 추천, 콘텐츠 및 경험을 제공합니다.
  예: Netflix와 같은 스트리밍 서비스는 시청 기록을 기반으로 영화와 쇼를 추천하여 사용자 참여도와 만족도를 향상시킵니다.
- **자동화 및 효율성**: AI가 반복 작업을 자동화하고, 작업 흐름을 간소화하며 운영 효율성을 개선합니다.
  예: 고객 서비스 앱은 AI 기반 챗봇을 사용해 자주 묻는 질문을 처리함으로써 응답 시간을 단축하고 복잡한 문제에 더 많은 인력을 할당할 수 있게 합니다.
- **향상된 사용자 경험**: AI가 음성 인식, 자연어 처리 및 예측 텍스트 같은 지능형 기능을 제공하여 전반적인 사용자 경험을 개선합니다.
  예: Siri나 Google Assistant와 같은 가상 비서는 음성 명령을 이해하고 응답하여 사용자가 기기와 쉽게 상호작용할 수 있도록 합니다.

### 모두 훌륭해 보이는데, 왜 AI 에이전트 프레임워크가 필요할까요?

AI 에이전트 프레임워크는 단순한 AI 프레임워크 이상의 것을 의미합니다. 이들은 사용자, 다른 에이전트 및 환경과 상호작용하여 특정 목표를 달성할 수 있는 지능형 에이전트 생성을 가능하게 하도록 설계되었습니다. 이러한 에이전트는 자율적으로 행동하고, 의사 결정을 내리며, 변화하는 조건에 적응할 수 있습니다. AI 에이전트 프레임워크가 제공하는 주요 기능 몇 가지를 살펴보겠습니다:

- **에이전트 협업 및 조정**: 여러 AI 에이전트가 함께 작업하고, 소통하며, 협력하여 복잡한 작업을 해결할 수 있도록 합니다.
- **작업 자동화 및 관리**: 다단계 작업 흐름 자동화, 작업 위임 및 에이전트 간 동적 작업 관리를 위한 메커니즘을 제공합니다.
- **상황 인식 및 적응**: 에이전트가 상황을 이해하고 변화하는 환경에 적응하며 실시간 정보를 기반으로 결정을 내릴 수 있도록 합니다.

요약하자면, 에이전트를 사용하면 더 많은 일을 할 수 있고, 자동화를 한 단계 높이며, 환경에서 학습하고 적응할 수 있는 더 지능적인 시스템을 만들 수 있습니다.

## 에이전트의 기능을 빠르게 프로토타입하고 반복 개선하는 방법은?

이 분야는 빠르게 변하고 있지만, 대부분 AI 에이전트 프레임워크에 공통적으로 존재하는 몇 가지가 있습니다: 모듈형 구성 요소, 협업 도구, 실시간 학습. 각각을 살펴보겠습니다:

- **모듈형 구성 요소 사용**: AI SDK는 AI 및 메모리 커넥터, 자연어 또는 코드 플러그인으로 함수 호출, 프롬프트 템플릿 등 사전 구축된 구성 요소를 제공합니다.
- **협업 도구 활용**: 특정 역할과 작업으로 에이전트를 설계하여 협업 작업 흐름을 테스트하고 개선할 수 있도록 합니다.
- **실시간 학습**: 에이전트가 상호작용에서 학습하고 동적으로 동작을 조정하는 피드백 루프를 구현합니다.

### 모듈형 구성 요소 사용

Microsoft Semantic Kernel 및 LangChain과 같은 SDK는 AI 커넥터, 프롬프트 템플릿, 메모리 관리 등의 사전 구축된 구성 요소를 제공합니다.

**팀에서 활용하는 방법**: 팀은 이러한 구성 요소를 빠르게 조합해 기능적 프로토타입을 만들어 낼 수 있어, 처음부터 개발하지 않고도 빠른 실험과 반복이 가능합니다.

**실제로 어떻게 작동하는가**: 사용자 입력에서 정보를 추출하는 사전 구축된 파서, 데이터를 저장 및 검색하는 메모리 모듈, 사용자와 상호작용하기 위한 프롬프트 생성기를 사용할 수 있습니다. 이 모든 것을 처음부터 만들 필요 없이 활용할 수 있습니다.

**예제 코드**. 다음은 Semantic Kernel Python 및 .Net에서 자동 함수 호출을 사용해 모델이 사용자 입력에 응답하도록 하는 사전 구축 AI 커넥터 사용 예입니다:

``` python
# Semantic Kernel 파이썬 예제

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# 대화의 컨텍스트를 보관할 ChatHistory 객체를 정의합니다
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# 여행 예약 함수를 포함하는 샘플 플러그인을 정의합니다
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Kernel을 생성합니다
kernel = Kernel()

# 샘플 플러그인을 Kernel 객체에 추가합니다
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Azure OpenAI AI 커넥터를 정의합니다
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# 모델의 자동 함수 호출을 구성하기 위한 요청 설정을 정의합니다
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # 주어진 채팅 기록과 요청 설정으로 모델에 요청을 보냅니다
    # Kernel에는 모델이 호출하도록 요청할 샘플이 포함되어 있습니다
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # `귀하의 뉴욕행 항공편이 2025년 1월 1일에 성공적으로 예약되었습니다. 안전한 여행 되세요! ✈️🗽`

    # 모델의 응답을 채팅 기록 컨텍스트에 추가합니다
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```
  
이 예제에서 볼 수 있듯, 출발지, 도착지, 날짜 같은 항공권 예약 요청의 주요 정보를 사용자 입력에서 추출하는 사전 구축된 파서를 활용하는 방식을 보여줍니다. 이렇게 모듈화하면 고수준 로직에 집중할 수 있습니다.

### 협업 도구 활용

CrewAI, Microsoft AutoGen, Semantic Kernel과 같은 프레임워크는 여러 에이전트가 함께 작동하도록 지원합니다.

**팀에서 활용하는 방법**: 팀은 특정 역할과 작업이 지정된 에이전트를 설계하여 협업 작업 흐름을 테스트 및 개선하고 시스템 효율성을 높일 수 있습니다.

**실제로 어떻게 작동하는가**: 데이터 검색, 분석, 의사 결정 등 각자 전문 기능을 가진 에이전트 팀을 만들 수 있습니다. 이 에이전트들은 통신하고 정보를 공유하여 사용자 질문에 답하거나 작업을 완료하는 공동 목표를 달성합니다.

**예제 코드 (AutoGen)**:

```python
# 에이전트를 생성한 다음, 이 경우 순서대로 작업할 수 있도록 라운드로빈 스케줄을 만듭니다

# 데이터 검색 에이전트
# 데이터 분석 에이전트
# 의사결정 에이전트

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# 사용자가 "APPROVE"라고 말하면 대화가 종료됩니다
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# 스크립트에서 실행할 때는 asyncio.run(...)을 사용하세요
await Console(stream)
```
  
이전 코드에서 여러 에이전트가 함께 데이터를 분석하는 작업을 만드는 방법을 볼 수 있습니다. 각 에이전트가 특정 기능을 수행하며, 작업은 에이전트 간 조정을 통해 원하는 결과를 달성합니다. 전문 역할을 가진 에이전트를 만들어 작업 효율과 성능을 향상할 수 있습니다.

### 실시간 학습

고급 프레임워크들은 실시간 상황 인식과 적응 기능을 제공합니다.

**팀에서 활용하는 방법**: 에이전트가 상호작용에서 학습하고 동작을 동적으로 조정하는 피드백 루프를 구현해 지속적인 개선을 도모할 수 있습니다.

**실제로 어떻게 작동하는가**: 에이전트는 사용자 피드백, 환경 데이터, 작업 결과를 분석하여 지식 기반을 업데이트하고 의사 결정 알고리즘을 조정하며 시간이 지남에 따라 성능을 향상시킵니다. 이 반복 학습 과정은 에이전트가 변화하는 조건과 사용자 선호에 적응하도록 하여 전반적인 시스템 효과를 높입니다.

## AutoGen, Semantic Kernel 및 Azure AI Agent Service 프레임워크 간의 차이점은 무엇인가?

이 프레임워크들을 비교하는 방법은 다양하지만, 설계, 기능 및 대상 사용 사례 측면에서 몇 가지 주요 차이점을 살펴보겠습니다.

## AutoGen

AutoGen은 Microsoft Research의 AI Frontiers Lab에서 개발한 오픈 소스 프레임워크입니다. 이벤트 기반의 분산 *에이전틱* 애플리케이션에 중점을 두어 여러 LLM 및 SLM, 도구, 고급 다중 에이전트 설계 패턴을 지원합니다.

AutoGen은 환경을 인지하고 의사 결정을 내리며 특정 목표를 달성하기 위해 행동하는 자율적 엔터티인 에이전트 개념을 중심으로 구축되었습니다. 에이전트는 비동기 메시지를 통해 소통하여 독립적이고 병렬로 작업할 수 있어 시스템 확장성과 응답성이 향상됩니다.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">에이전트는 액터 모델을 기반으로 합니다</a>. 위키피디아에 따르면, 액터는 _동시 계산의 기본 단위입니다. 수신한 메시지에 따라 액터는 지역 결정을 내리고, 더 많은 액터를 생성하며, 더 많은 메시지를 보내고, 다음에 수신할 메시지에 대응하는 방법을 결정할 수 있습니다_.

**사용 사례**: 코드 생성 자동화, 데이터 분석 작업, 계획 및 연구 기능을 위한 맞춤 에이전트 구축.

AutoGen의 주요 핵심 개념은 다음과 같습니다:

- **에이전트**. 에이전트는 소프트웨어 엔터티로서:
  - **메시지로 소통합니다**. 이 메시지는 동기 또는 비동기일 수 있습니다.
  - **자기 상태를 유지하며**, 이는 수신 메시지에 의해 변경될 수 있습니다.
  - **수신 메시지나 상태 변화에 대응하여 행동을 수행합니다**. 이 행동은 에이전트 상태를 수정하고 메시지 로그 업데이트, 새 메시지 발송, 코드 실행, API 호출 같은 외부 효과를 일으킬 수 있습니다.

  아래는 채팅 기능이 있는 에이전트를 생성하는 간단한 코드 예입니다:

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
  
이전 코드에서 `MyAgent`가 생성되어 `RoutedAgent`를 상속합니다. 메시지 핸들러는 메시지 내용을 출력하고, 이어서 `AssistantAgent` 대리자를 사용해 응답을 보냅니다. 특히 `self._delegate`에 사전 구축된 챗 완성 처리 에이전트인 `AssistantAgent` 인스턴스를 할당하는 부분을 주목하세요.

다음으로 AutoGen에 이 에이전트 유형을 알리고 프로그램을 시작해봅니다:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # 백그라운드에서 메시지 처리를 시작합니다.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```
  
이전 코드에서 에이전트가 런타임에 등록되고, 에이전트로 메시지를 보내면 다음과 같은 출력이 나타납니다:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```
  
- **다중 에이전트**. AutoGen은 여러 에이전트가 함께 작동하여 복잡한 작업을 수행하도록 지원합니다. 에이전트는 통신, 정보 공유, 행동 조정을 통해 문제를 더 효율적으로 해결합니다. 다중 에이전트 시스템을 만들려면 데이터 검색, 분석, 의사 결정, 사용자 상호작용 등 각기 전문 기능과 역할을 가진 다양한 유형의 에이전트를 정의할 수 있습니다. 다음 예제를 보면 대략적인 구조를 알 수 있습니다:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # 에이전트를 선언하는 예
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # 에이전트 유형으로 토픽 타입 사용
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # 나머지 선언은 간결성을 위해 생략됨

    # 그룹 채팅
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```
  
이전 코드에서는 `GroupChatManager`가 런타임에 등록되어 있습니다. 이 관리자는 작가, 일러스트레이터, 편집자, 사용자와 같은 다양한 에이전트 유형 간 상호작용을 조정하는 역할을 합니다.

- **에이전트 런타임**. 프레임워크는 에이전트 간 통신을 가능하게 하고, 신원과 수명 주기를 관리하며 보안과 개인정보 경계를 시행하는 런타임 환경을 제공합니다. 이를 통해 에이전트를 안전하고 통제된 환경에서 실행해 안전하고 효율적으로 상호작용할 수 있습니다. 주요 런타임은 두 가지입니다:
  - **독립형 런타임**. 모든 에이전트가 같은 프로그래밍 언어로 동일 프로세스 내에서 실행되는 단일 프로세스 앱에 적합합니다. 작동 방식은 다음과 같습니다:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">독립형 런타임</a>  
애플리케이션 스택

    *에이전트는 런타임을 통해 메시지를 주고받으며, 런타임은 에이전트 수명 주기를 관리합니다*

  - **분산 에이전트 런타임**. 에이전트가 다른 프로그래밍 언어로 구현되거나 서로 다른 머신에서 실행되는 다중 프로세스 앱에 적합합니다. 작동 방식은 다음과 같습니다:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">분산 런타임</a>

## Semantic Kernel + 에이전트 프레임워크

Semantic Kernel은 기업용 AI 오케스트레이션 SDK입니다. AI 및 메모리 커넥터와 에이전트 프레임워크로 구성되어 있습니다.

먼저 일부 핵심 구성 요소를 다뤄보겠습니다:

- **AI 커넥터**: Python과 C# 모두에서 사용할 수 있는 외부 AI 서비스 및 데이터 소스와의 인터페이스입니다.

  ```python
  # 시맨틱 커널 파이썬
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  
  
    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```
  
  여기서는 간단한 예로 커널을 생성하고 챗 완성 서비스를 추가하는 방법을 보여줍니다. Semantic Kernel은 외부 AI 서비스인 Azure OpenAI Chat Completion과 연결을 만듭니다.

- **플러그인**: 애플리케이션이 사용할 수 있는 기능을 캡슐화합니다. 준비된 플러그인과 생성 가능한 사용자 정의 플러그인이 있습니다. 관련 개념으로 "프롬프트 함수"가 있는데, 함수 호출을 위한 자연어 힌트를 제공하는 대신 특정 함수를 모델에 브로드캐스트합니다. 현재 채팅 컨텍스트에 따라 모델은 이 함수들 중 하나를 호출해 요청이나 쿼리를 완료할 수 있습니다. 다음은 그 예입니다:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```
  
    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```
  
  여기서는 먼저 사용자 입력 `$userInput` 공간을 남긴 템플릿 프롬프트 `skPrompt`가 있습니다. 그 다음 `SummarizeText`라는 커널 함수를 생성한 후 `SemanticFunctions`라는 플러그인 이름으로 커널에 가져옵니다. 함수 이름은 Semantic Kernel이 함수의 역할과 호출 시점을 이해하는 데 도움을 줍니다.

- **네이티브 함수**: 프레임워크가 직접 호출할 수 있는 네이티브 함수도 있습니다. 예를 들어 파일에서 내용을 가져오는 함수가 있습니다:

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```
  
- **메모리**: AI 앱을 위한 컨텍스트 관리를 추상화하고 단순화합니다. 메모리는 LLM이 알아야 할 정보를 저장하는 개념입니다. 이 정보는 인메모리 데이터베이스나 벡터 데이터베이스 같은 벡터 저장소에 저장할 수 있습니다. 다음은 사실들을 메모리에 추가하는 아주 단순화된 시나리오 예입니다:

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```
  
이러한 사실들은 메모리 컬렉션 `SummarizedAzureDocs`에 저장됩니다. 이것은 아주 단순화된 예이지만, LLM이 사용할 수 있도록 정보를 메모리에 저장하는 방법을 볼 수 있습니다.

이제 Semantic Kernel 프레임워크의 기본을 알았으니, Agent Framework는 어떨까요?

## Azure AI Agent Service

Azure AI Agent Service는 Microsoft Ignite 2024에서 도입된 최신 기능입니다. Llama 3, Mistral, Cohere 같은 오픈 소스 LLM을 직접 호출하는 등 더 유연한 모델을 활용할 수 있는 AI 에이전트를 개발하고 배포할 수 있게 해줍니다.

Azure AI Agent Service는 강력한 엔터프라이즈 보안 메커니즘과 데이터 저장 방식을 제공하여 엔터프라이즈 애플리케이션에 적합합니다.

AutoGen, Semantic Kernel 같은 멀티 에이전트 오케스트레이션 프레임워크와도 즉시 사용할 수 있습니다.

현재 이 서비스는 공개 프리뷰 중이며, 에이전트 빌드를 위해 Python과 C#을 지원합니다.

Semantic Kernel Python을 사용하여 사용자 정의 플러그인이 포함된 Azure AI Agent를 만들 수 있습니다:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# 샘플을 위한 예제 플러그인을 정의합니다
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # 에이전트 정의를 생성합니다
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # 정의된 클라이언트와 에이전트 정의를 사용하여 AzureAI 에이전트를 생성합니다
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # 대화를 담을 스레드를 생성합니다
        # 스레드가 제공되지 않으면 새 스레드가
        # 초기 응답과 함께 생성되어 반환됩니다
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # 지정된 스레드에 대해 에이전트를 호출합니다
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### 핵심 개념

Azure AI Agent Service에는 다음과 같은 핵심 개념이 있습니다:

- **Agent**. Azure AI Agent Service는 Microsoft Foundry와 통합됩니다. AI Foundry 내에서 AI Agent는 질문에 답변(RAG), 작업 수행 또는 워크플로 완전 자동화를 위한 "스마트" 마이크로서비스 역할을 합니다. 이는 생성 AI 모델의 강력한 기능과 실제 데이터 소스에 접근하고 상호작용할 수 있는 도구를 결합하여 이루어집니다. 다음은 에이전트 예시입니다:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    이 예에서 에이전트는 `gpt-4o-mini` 모델, 이름 `my-agent`, 지침 `You are helpful agent`로 만들어졌습니다. 에이전트는 코드 해석 작업을 수행할 도구와 자원을 갖추고 있습니다.

- **스레드와 메시지**. 스레드는 또 다른 중요한 개념입니다. 이는 에이전트와 사용자 간의 대화 또는 상호작용을 나타냅니다. 스레드는 대화의 진행 상황을 추적하고 컨텍스트 정보를 저장하며 상호작용 상태를 관리하는 데 사용될 수 있습니다. 다음은 스레드 예시입니다:

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    이전 코드에서 스레드가 생성됩니다. 이후 메시지가 스레드에 전송됩니다. `create_and_process_run`을 호출해서 에이전트에 스레드 작업 수행을 요청합니다. 마지막으로 메시지를 가져와 에이전트의 응답을 기록합니다. 메시지는 사용자와 에이전트 간 대화 진행 사항을 나타냅니다. 메시지는 텍스트, 이미지, 파일 등 다양한 유형일 수 있다는 점도 중요합니다. 예를 들면 작업 결과로 이미지나 텍스트 응답이 생성될 수 있습니다. 개발자는 이 정보를 활용하여 응답을 추가 처리하거나 사용자에게 제시할 수 있습니다.

- **다른 AI 프레임워크와의 통합**. Azure AI Agent Service는 AutoGen, Semantic Kernel 같은 다른 프레임워크와 상호작용할 수 있습니다. 즉, 앱의 일부를 이러한 프레임워크 중 하나에서 빌드하고 예를 들어 Agent Service를 오케스트레이터로 사용할 수 있으며, 또는 모든 것을 Agent Service 내에서 빌드할 수도 있습니다.

**사용 사례**: Azure AI Agent Service는 보안성, 확장성, 유연한 AI 에이전트 배포가 필요한 엔터프라이즈 애플리케이션용으로 설계되었습니다.

## 이 프레임워크들 간 차이는 무엇인가요?

이 프레임워크들 간에 상당한 중복이 있는 것처럼 들리지만, 설계, 기능, 대상 사용 사례 측면에서 몇 가지 주요 차이가 있습니다:

- **AutoGen**: 최첨단 다중 에이전트 시스템 연구에 초점을 둔 실험용 프레임워크입니다. 복잡한 다중 에이전트 시스템을 실험하고 프로토타입화하기에 가장 적합한 곳입니다.
- **Semantic Kernel**: 엔터프라이즈 에이전트 애플리케이션 구축을 위한 프로덕션 준비가 된 에이전트 라이브러리입니다. 이벤트 중심, 분산 에이전트 애플리케이션에 중점을 두고 여러 LLM 및 SLM, 도구, 단일/다중 에이전트 설계 패턴을 지원합니다.
- **Azure AI Agent Service**: Azure Foundry 내 에이전트를 위한 플랫폼 및 배포 서비스입니다. Azure OpenAI, Azure AI Search, Bing Search, 코드 실행 등을 지원하는 Azure Foundry 서비스와의 연결 구축 기능을 제공합니다.

아직 어떤 걸 선택해야 할지 모르겠나요?

### 사용 사례

일부 일반적인 사용 사례를 살펴보며 도움을 드려 보겠습니다:

> Q: 실험하고 배우며 개념 증명용 에이전트 애플리케이션을 빠르게 빌드하고 실험하고 싶어요.

> A: 이 시나리오에는 AutoGen이 좋은 선택입니다. 이벤트 중심, 분산 에이전트 애플리케이션에 중점을 두고 고급 다중 에이전트 설계 패턴을 지원하기 때문입니다.

> Q: 이 사용 사례에서 왜 Semantic Kernel이나 Azure AI Agent Service보다 AutoGen이 더 나은 선택인가요?

> A: AutoGen은 이벤트 중심, 분산 에이전트 애플리케이션에 특화되어 있어 코드 생성과 데이터 분석 작업 자동화에 적합합니다. 복잡한 다중 에이전트 시스템을 효율적으로 구축할 도구와 기능을 제공합니다.

> Q: Azure AI Agent Service도 여기에 어울릴 것 같은데요, 코드 생성 도구도 있고요?

> A: 네, Azure AI Agent Service는 에이전트를 위한 플랫폼 서비스로 여러 모델, Azure AI Search, Bing Search, Azure Functions를 내장해 지원합니다. Foundry 포털에서 쉽게 에이전트를 빌드하고 대규모로 배포할 수 있습니다.

> Q: 아직 헷갈리는데 하나만 추천해 주세요.

> A: Semantic Kernel에서 애플리케이션을 먼저 구축하고 Azure AI Agent Service를 이용해 에이전트를 배포하는 접근법이 좋습니다. 이렇게 하면 Semantic Kernel에서 다중 에이전트 시스템을 구축하는 강력함을 유지하면서 에이전트를 쉽게 유지할 수 있습니다. 추가로 Semantic Kernel은 AutoGen과의 커넥터도 제공해 두 프레임워크를 함께 쉽게 사용할 수 있습니다.

주요 차이점을 표로 정리해 봅시다:

| Framework | 집중 분야 | 핵심 개념 | 사용 사례 |
| --- | --- | --- | --- |
| AutoGen | 이벤트 중심, 분산 에이전트 애플리케이션 | 에이전트, 페르소나, 함수, 데이터 | 코드 생성, 데이터 분석 작업 |
| Semantic Kernel | 인간 같은 텍스트 이해 및 생성 | 에이전트, 모듈형 구성 요소, 협업 | 자연어 이해, 콘텐츠 생성 |
| Azure AI Agent Service | 유연한 모델, 엔터프라이즈 보안, 코드 생성, 도구 호출 | 모듈화, 협업, 프로세스 오케스트레이션 | 보안성, 확장성, 유연한 AI 에이전트 배포 |

각 프레임워크에 이상적인 사용 사례는 무엇일까요?

## 기존 Azure 에코시스템 도구를 직접 통합할 수 있나요, 아니면 독립형 솔루션이 필요한가요?

답은 예입니다. 특히 Azure AI Agent Service는 다른 Azure 서비스와 원활하게 작동하도록 구축되어 기존 Azure 에코시스템 도구를 직접 통합할 수 있습니다. 예를 들어 Bing, Azure AI Search, Azure Functions를 통합할 수 있습니다. Microsoft Foundry와도 깊게 통합되어 있습니다.

AutoGen과 Semantic Kernel도 Azure 서비스를 통합할 수 있으나, 코드에서 Azure 서비스를 호출해야 할 수 있습니다. 또 다른 방법으로는 Azure SDK를 사용해 에이전트에서 Azure 서비스와 상호작용하는 것입니다. 추가로 앞서 언급했듯이, AutoGen이나 Semantic Kernel에서 만든 에이전트를 오케스트레이터 역할을 하는 Azure AI Agent Service를 사용하는 것도 Azure 생태계에 쉽게 접근할 수 있는 방법입니다.

## 샘플 코드

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## AI Agent Framework 관련 추가 질문이 있나요?

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)에 참여하여 다른 학습자들과 만나고, 오피스 아워에 참석하며 AI 에이전트 관련 질문에 답을 얻으세요.

## 참고 문헌

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel and AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## 이전 수업

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## 다음 수업

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**면책 조항**:  
본 문서는 AI 번역 서비스 [Co-op Translator](https://github.com/Azure/co-op-translator)를 사용하여 번역되었습니다. 정확성을 위해 최선을 다하고 있으나, 자동 번역본에는 오류나 부정확성이 포함될 수 있음을 유의하시기 바랍니다. 원문은 해당 언어로 작성된 원본 문서를 권위 있는 출처로 간주해야 합니다. 중요한 정보에 대해서는 전문가의 인간 번역을 권장합니다. 본 번역 사용으로 인한 오해나 잘못된 해석에 대해서는 당사는 책임을 지지 않습니다.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->