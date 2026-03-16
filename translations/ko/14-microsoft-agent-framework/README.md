# Microsoft Agent Framework 탐색

![에이전트 프레임워크](../../../translated_images/ko/lesson-14-thumbnail.90df0065b9d234ee.webp)

### 소개

이 수업에서는 다음을 다룹니다:

- Microsoft Agent Framework 이해: 주요 기능 및 가치  
- Microsoft Agent Framework의 핵심 개념 탐색
- MAF와 Semantic Kernel 및 AutoGen 비교: 마이그레이션 가이드

## 학습 목표

이 수업을 완료한 후 다음을 수행할 수 있게 됩니다:

- Microsoft Agent Framework를 사용하여 프로덕션 준비가 된 AI 에이전트를 구축하는 방법
- Microsoft Agent Framework의 핵심 기능을 에이전트 기반 사용 사례에 적용하는 방법
- 기존 에이전트 프레임워크와 도구를 마이그레이션하고 통합하는 방법  

## 코드 샘플 

이 저장소에서는 [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok)의 코드 샘플을 `xx-python-agent-framework` 및 `xx-dotnet-agent-framework` 파일에서 찾을 수 있습니다.

## Microsoft Agent Framework 이해

![프레임워크 소개](../../../translated_images/ko/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok)은 Semantic Kernel 및 AutoGen의 경험과 학습을 기반으로 합니다. 이는 프로덕션 및 연구 환경에서 관찰되는 다양한 에이전트 사용 사례를 해결할 수 있는 유연성을 제공합니다. 포함된 사례는 다음과 같습니다:

- **순차적 에이전트 오케스트레이션** - 단계별 워크플로가 필요한 시나리오에서.
- **동시 오케스트레이션** - 에이전트가 동시에 작업을 완료해야 하는 시나리오에서.
- **그룹 채팅 오케스트레이션** - 에이전트가 하나의 작업을 함께 협업할 수 있는 시나리오에서.
- **핸드오프 오케스트레이션** - 하위 작업이 완료됨에 따라 에이전트가 작업을 서로 인계하는 시나리오에서.
- **마그네틱 오케스트레이션** - 매니저 에이전트가 작업 목록을 생성 및 수정하고 서브에이전트의 조정을 처리하여 작업을 완료하는 시나리오에서.

AI 에이전트를 프로덕션에 제공하기 위해 MAF는 다음과 같은 기능도 포함하고 있습니다:

- **관찰 가능성(Observability)** - OpenTelemetry를 사용하여 도구 호출, 오케스트레이션 단계, 추론 흐름 및 Microsoft Foundry 대시보드를 통한 성능 모니터링 등 AI 에이전트의 모든 동작을 추적할 수 있습니다.
- **보안** - Microsoft Foundry에서 에이전트를 네이티브로 호스팅하여 역할 기반 액세스, 개인 데이터 처리 및 내장 콘텐츠 안전성과 같은 보안 제어를 제공합니다.
- **내구성(Durability)** - 에이전트 스레드와 워크플로는 일시 중지, 재개 및 오류 복구가 가능하여 장기간 실행되는 프로세스를 지원합니다.
- **제어** - 사람의 개입(Human-in-the-loop) 워크플로를 지원하여 작업이 사람의 승인을 필요로 하는 것으로 표시될 수 있습니다.

Microsoft Agent Framework는 다음 측면에서 상호 운용성을 지향합니다:

- **클라우드 비종속(Cloud-agnostic)** - 에이전트는 컨테이너, 온프레미스 및 여러 클라우드에서 실행될 수 있습니다.
- **프로바이더 비종속(Provider-agnostic)** - 에이전트는 Azure OpenAI 및 OpenAI를 포함한 선호하는 SDK를 통해 생성할 수 있습니다
- **오픈 표준 통합** - 에이전트는 Agent-to-Agent(A2A) 및 Model Context Protocol (MCP)과 같은 프로토콜을 사용하여 다른 에이전트와 도구를 발견하고 사용할 수 있습니다.
- **플러그인 및 커넥터** - Microsoft Fabric, SharePoint, Pinecone 및 Qdrant와 같은 데이터 및 메모리 서비스에 연결할 수 있습니다.

이제 이러한 기능들이 Microsoft Agent Framework의 핵심 개념들에 어떻게 적용되는지 살펴보겠습니다.

## Microsoft Agent Framework의 핵심 개념

### 에이전트

![에이전트 프레임워크](../../../translated_images/ko/agent-components.410a06daf87b4fef.webp)

**에이전트 생성**

에이전트 생성은 추론 서비스(LLM Provider), AI 에이전트가 따를 지침 집합 및 지정된 `name`을 정의하여 수행됩니다:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

위 예시는 `Azure OpenAI`를 사용하고 있지만 에이전트는 `Microsoft Foundry Agent Service`를 포함한 다양한 서비스를 사용하여 생성할 수 있습니다:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

또는 A2A 프로토콜을 사용하는 원격 에이전트:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**에이전트 실행**

에이전트는 비스트리밍 또는 스트리밍 응답을 위해 `.run` 또는 `.run_stream` 메서드를 사용하여 실행됩니다.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

각 에이전트 실행은 에이전트가 사용하는 `max_tokens`, 에이전트가 호출할 수 있는 `tools`, 심지어 에이전트에 사용되는 `model` 자체와 같은 매개변수를 사용자화하는 옵션을 가질 수 있습니다.

이는 특정 모델이나 도구가 사용자 작업을 완료하는 데 필요한 경우에 유용합니다.

**도구**

도구는 에이전트를 정의할 때 다음과 같이 지정할 수 있습니다:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# ChatAgent를 직접 생성할 때

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

또한 에이전트를 실행할 때에도:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # 이 실행을 위해서만 제공된 도구 )
```

**에이전트 스레드**

에이전트 스레드는 다중 턴 대화를 처리하는 데 사용됩니다. 스레드는 다음 중 하나로 생성할 수 있습니다:

- `get_new_thread()`를 사용하면 스레드를 시간이 지나도 저장할 수 있습니다
- 에이전트를 실행할 때 자동으로 스레드를 생성하고 해당 스레드는 현재 실행 중에만 지속되게 합니다.

스레드를 생성하려면 코드가 다음과 같습니다:

```python
# 새 스레드를 생성합니다.
thread = agent.get_new_thread() # 해당 스레드에서 에이전트를 실행합니다.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

그런 다음 스레드를 직렬화하여 나중에 사용하기 위해 저장할 수 있습니다:

```python
# 새 스레드를 생성합니다.
thread = agent.get_new_thread() 

# 스레드를 사용하여 에이전트를 실행합니다.

response = await agent.run("Hello, how are you?", thread=thread) 

# 저장을 위해 스레드를 직렬화합니다.

serialized_thread = await thread.serialize() 

# 저장소에서 로드한 후 스레드 상태를 역직렬화합니다.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**에이전트 미들웨어**

에이전트는 도구와 LLM과 상호작용하여 사용자의 작업을 완료합니다. 특정 시나리오에서는 이러한 상호작용 사이에서 작업을 실행하거나 추적하려는 경우가 있습니다. 에이전트 미들웨어는 이를 다음과 같이 가능하게 합니다:

*함수 미들웨어*

이 미들웨어는 에이전트와 호출할 함수/도구 사이에서 액션을 실행할 수 있게 합니다. 이 미들웨어가 사용되는 예로는 함수 호출에 대한 로깅을 수행하고자 할 때가 있습니다.

아래 코드에서 `next`는 다음 미들웨어를 호출할지 실제 함수를 호출할지를 정의합니다.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # 사전 처리: 함수 실행 전에 로그를 기록
    print(f"[Function] Calling {context.function.name}")

    # 다음 미들웨어 또는 함수 실행으로 계속 진행
    await next(context)

    # 사후 처리: 함수 실행 후에 로그를 기록
    print(f"[Function] {context.function.name} completed")
```

*채팅 미들웨어*

이 미들웨어는 에이전트와 LLM에 대한 요청 사이에서 동작을 실행하거나 로그를 남길 수 있게 합니다.

여기에는 AI 서비스로 전송되는 `messages`와 같은 중요한 정보가 포함됩니다.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # 전처리: AI 호출 전에 로그 기록
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # 다음 미들웨어 또는 AI 서비스로 계속 진행
    await next(context)

    # 후처리: AI 응답 후 로그 기록
    print("[Chat] AI response received")

```

**에이전트 메모리**

`Agentic Memory` 수업에서 다룬 바와 같이, 메모리는 에이전트가 다양한 컨텍스트에서 작동하도록 하는 데 중요한 요소입니다. MAF는 여러 유형의 메모리를 제공합니다:

*인메모리 저장소*

이는 애플리케이션 런타임 동안 스레드에 저장되는 메모리입니다.

```python
# 새 스레드를 생성합니다.
thread = agent.get_new_thread() # 스레드를 사용하여 에이전트를 실행합니다.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*영구 메시지*

이 메모리는 서로 다른 세션에 걸쳐 대화 기록을 저장할 때 사용됩니다. `chat_message_store_factory`를 사용하여 정의됩니다:

```python
from agent_framework import ChatMessageStore

# 사용자 정의 메시지 저장소를 생성합니다
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*동적 메모리*

이 메모리는 에이전트를 실행하기 전에 컨텍스트에 추가됩니다. 이러한 메모리는 mem0과 같은 외부 서비스에 저장될 수 있습니다:

```python
from agent_framework.mem0 import Mem0Provider

# 고급 메모리 기능을 위해 Mem0 사용
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**에이전트 관찰성**

관찰성은 신뢰할 수 있고 유지 관리 가능한 에이전트 시스템을 구축하는 데 중요합니다. MAF는 OpenTelemetry와 통합되어 더 나은 관찰성을 위해 트레이싱 및 미터를 제공합니다.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # 무언가를 수행한다
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### 워크플로

MAF는 작업을 완료하기 위한 미리 정의된 단계인 워크플로를 제공하며, 이러한 단계에 AI 에이전트를 구성요소로 포함합니다.

워크플로는 더 나은 흐름 제어를 가능하게 하는 다양한 구성 요소로 구성됩니다. 워크플로는 또한 **다중 에이전트 오케스트레이션** 및 워크플로 상태를 저장하기 위한 **체크포인팅**을 지원합니다.

워크플로의 핵심 구성 요소는 다음과 같습니다:

**실행자(Executors)**

실행자는 입력 메시지를 수신하고, 할당된 작업을 수행한 다음 출력 메시지를 생성합니다. 이는 워크플로를 진행시켜 더 큰 작업을 완료하는 데 기여합니다. 실행자는 AI 에이전트이거나 커스텀 로직일 수 있습니다.

**엣지(Edges)**

엣지는 워크플로에서 메시지의 흐름을 정의하는 데 사용됩니다. 종류는 다음과 같습니다:

*직접 엣지(Direct Edges)* - 실행자 간의 단순한 1:1 연결:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*조건부 엣지(Conditional Edges)* - 특정 조건이 충족된 후 활성화됩니다. 예를 들어 호텔 객실이 이용 불가한 경우 실행자가 다른 옵션을 제안할 수 있습니다.

*스위치-케이스 엣지(Switch-case Edges)* - 정의된 조건에 따라 메시지를 다른 실행자에게 라우팅합니다. 예: 여행 고객이 우선 접근 권한이 있어 그들의 작업이 다른 워크플로에서 처리되는 경우.

*팬아웃 엣지(Fan-out Edges)* - 하나의 메시지를 여러 대상에 전송합니다.

*팬인 엣지(Fan-in Edges)* - 서로 다른 실행자들로부터 여러 메시지를 수집하여 하나의 대상에 전송합니다.

**이벤트**

워크플로에 대한 더 나은 관찰성을 제공하기 위해 MAF는 실행 시 다음과 같은 내장 이벤트를 제공합니다:

- `WorkflowStartedEvent`  - 워크플로 실행이 시작됩니다
- `WorkflowOutputEvent` - 워크플로가 출력을 생성합니다
- `WorkflowErrorEvent` - 워크플로가 오류를 만납니다
- `ExecutorInvokeEvent`  - 실행자가 처리를 시작합니다
- `ExecutorCompleteEvent`  -  실행자가 처리를 완료합니다
- `RequestInfoEvent` - 요청이 발행됩니다

## 다른 프레임워크에서 마이그레이션 (Semantic Kernel 및 AutoGen)

### MAF와 Semantic Kernel의 차이점

**간소화된 에이전트 생성**

Semantic Kernel은 각 에이전트마다 Kernel 인스턴스를 생성하는 것에 의존합니다. MAF는 주요 제공업체에 대한 확장을 사용하여 더 간단한 접근 방식을 사용합니다.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**에이전트 스레드 생성**

Semantic Kernel은 스레드를 수동으로 생성해야 합니다. MAF에서는 에이전트에 직접 스레드가 할당됩니다.

```python
thread = agent.get_new_thread() # 스레드로 에이전트를 실행합니다.
```

**도구 등록**

Semantic Kernel에서는 도구가 Kernel에 등록되고 해당 Kernel이 에이전트에 전달됩니다. MAF에서는 도구가 에이전트 생성 과정에서 직접 등록됩니다.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF와 AutoGen의 차이점

**Teams vs Workflows**

`Teams`는 AutoGen에서 에이전트와의 이벤트 기반 활동을 위한 이벤트 구조입니다. MAF는 그래프 기반 아키텍처를 통해 데이터를 실행자에게 라우팅하는 `Workflows`를 사용합니다.

**도구 생성**

AutoGen은 에이전트가 호출할 수 있도록 함수를 래핑하기 위해 `FunctionTool`을 사용합니다. MAF는 유사하게 동작하는 @ai_function을 사용하지만 각 함수에 대한 스키마를 자동으로 유추하기도 합니다.

**에이전트 동작**

AutoGen에서는 기본적으로 에이전트가 단일 턴(single-turn)이며 `max_tool_iterations`가 더 높게 설정되지 않는 한 그렇습니다. MAF에서는 `ChatAgent`가 기본적으로 다중 턴(multi-turn)이어서 사용자의 작업이 완료될 때까지 계속해서 도구를 호출합니다.

## 코드 샘플 

Microsoft Agent Framework의 코드 샘플은 이 저장소의 `xx-python-agent-framework` 및 `xx-dotnet-agent-framework` 파일에서 찾을 수 있습니다.

## Microsoft Agent Framework에 대해 더 궁금한 점이 있으신가요?

다른 학습자들과 만나고, 오피스 아워에 참석하며 AI 에이전트 관련 질문에 대한 답변을 얻으려면 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)에 참여하세요.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
면책조항:
이 문서는 AI 번역 서비스 Co-op Translator(https://github.com/Azure/co-op-translator)를 사용하여 번역되었습니다. 당사는 정확성을 위해 노력하지만 자동 번역에는 오류나 부정확성이 포함될 수 있음을 알려드립니다. 원문(원어로 된 문서)을 최종적인 기준으로 간주하시기 바랍니다. 중요한 정보의 경우에는 전문적인 인간 번역을 권장합니다. 이 번역의 사용으로 인해 발생하는 모든 오해나 잘못된 해석에 대해 당사는 책임을 지지 않습니다.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->