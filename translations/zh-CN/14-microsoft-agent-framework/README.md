# 探索 Microsoft Agent Framework

![Agent Framework](../../../translated_images/zh-CN/lesson-14-thumbnail.90df0065b9d234ee.webp)

### 介绍

本课将涵盖：

- 理解 Microsoft Agent Framework：关键特性与价值  
- 探索 Microsoft Agent Framework 的关键概念
- 比较 MAF 与 Semantic Kernel 和 AutoGen：迁移指南

## 学习目标

完成本课后，您将了解如何：

- 使用 Microsoft Agent Framework 构建生产就绪的 AI 代理
- 将 Microsoft Agent Framework 的核心功能应用于您的代理用例
- 迁移和整合现有的代理框架和工具  

## 代码示例

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) 的代码示例可在本仓库的 `xx-python-agent-framework` 和 `xx-dotnet-agent-framework` 文件夹中找到。

## 了解 Microsoft Agent Framework

![Framework Intro](../../../translated_images/zh-CN/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) 以 Semantic Kernel 和 AutoGen 的经验与学习为基础构建，提供灵活性以应对生产和研究环境中各种代理用例，包括：

- **顺序代理编排**，适用于需要逐步工作流程的场景。
- **并发编排**，适用于代理需要同时完成任务的场景。
- **群聊编排**，适用于代理协作完成同一任务的场景。
- **任务交接编排**，适用于代理在完成子任务后相互交接任务的场景。
- **磁性编排**，适用于管理代理创建和修改任务列表并协调子代理完成任务的场景。

为了在生产环境中交付 AI 代理，MAF 还包含以下功能：

- **可观察性**，通过 OpenTelemetry 实现，监控 AI 代理的每一个操作，包括工具调用、编排步骤、推理流程，以及通过 Microsoft Foundry 仪表板进行性能监控。
- **安全性**，代理原生托管于 Microsoft Foundry，提供基于角色的访问控制、私有数据处理和内置内容安全等安全控制。
- **持久性**，代理线程和工作流程支持暂停、恢复和错误恢复，支持长时间运行。
- **控制性**，支持人工介入的工作流程，任务可标记为需要人工审批。

Microsoft Agent Framework 同时注重互操作性：

- **云无关**——代理可运行于容器、本地以及多个不同云环境。
- **提供商无关**——代理可通过您偏好的 SDK 创建，包括 Azure OpenAI 和 OpenAI。
- **集成开放标准**——代理支持使用代理间协议(Agent-to-Agent, A2A)和模型上下文协议(Model Context Protocol, MCP)来发现和调用其他代理与工具。
- **插件和连接器**——支持连接到 Microsoft Fabric、SharePoint、Pinecone 和 Qdrant 等数据和存储服务。

接下来让我们看看这些功能如何应用于 Microsoft Agent Framework 的一些核心概念。

## Microsoft Agent Framework 的关键概念

### 代理

![Agent Framework](../../../translated_images/zh-CN/agent-components.410a06daf87b4fef.webp)

**创建代理**

代理的创建需要定义推理服务（LLM 提供者）、一组供 AI 代理遵循的指令，以及一个分配的 `name`：

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```
  
以上示例使用了 `Azure OpenAI`，但代理也可以通过多种服务创建，包括 `Microsoft Foundry Agent Service`：

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```
  
OpenAI 的 `Responses`、`ChatCompletion` API  

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```
  
```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```
  
或者使用 A2A 协议创建远程代理：

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```
  
**运行代理**

代理通过 `.run` 或 `.run_stream` 方法运行，分别用于非流式和流式响应。

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```
  
```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```
  
每次代理运行也可以自定义参数，如代理使用的 `max_tokens`，代理可调用的 `tools`，甚至用于代理的具体 `model`。

当任务需要特定模型或工具时，此功能非常有用。

**工具**

工具既可以在定义代理时配置：

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# 当直接创建一个 ChatAgent 时

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```
  
也可以在运行代理时配置：

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # 仅为此次运行提供的工具 )
```
  
**代理线程**

代理线程用于处理多轮对话。线程可以通过以下方式创建：

- 使用 `get_new_thread()`，线程可以长时间保存
- 在运行代理时自动创建线程，线程仅在当前运行期间有效

创建线程的代码示例如下：

```python
# 创建一个新线程。
thread = agent.get_new_thread() # 使用该线程运行代理。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```
  
您还可以将线程序列化以便后续使用：

```python
# 创建一个新线程。
thread = agent.get_new_thread() 

# 使用线程运行代理。

response = await agent.run("Hello, how are you?", thread=thread) 

# 将线程序列化以便存储。

serialized_thread = await thread.serialize() 

# 从存储加载后反序列化线程状态。

resumed_thread = await agent.deserialize_thread(serialized_thread)
```
  
**代理中间件**

代理通过与工具和大语言模型交互完成用户任务。在某些场景下，我们需要在这些交互之间执行或追踪操作。代理中间件允许我们实现这一点：

*函数中间件*

该中间件允许我们在代理与其调用的函数/工具之间执行操作。例如，您可能想要记录函数调用日志。

以下代码中，`next` 定义了是否调用下一个中间件或实际函数。

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # 预处理：函数执行前记录日志
    print(f"[Function] Calling {context.function.name}")

    # 继续执行下一个中间件或函数
    await next(context)

    # 后处理：函数执行后记录日志
    print(f"[Function] {context.function.name} completed")
```
  
*聊天中间件*

该中间件允许我们在代理与 LLM 请求之间执行或记录操作。

其中包含重要信息，比如发送给 AI 服务的 `messages`。

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # 预处理：AI调用前的日志记录
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # 继续到下一个中间件或AI服务
    await next(context)

    # 后处理：AI响应后的日志记录
    print("[Chat] AI response received")

```
  
**代理记忆**

如“Agentic Memory”课程所述，记忆是支持代理在不同上下文中操作的重要元素。MAF 提供多种类型的记忆：

*内存存储*

这部分记忆存储于线程中，存在于应用运行时。

```python
# 创建一个新线程。
thread = agent.get_new_thread() # 使用该线程运行代理。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```
  
*持久消息*

此类记忆用于跨不同会话存储对话历史，由 `chat_message_store_factory` 定义：

```python
from agent_framework import ChatMessageStore

# 创建自定义消息存储
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```
  
*动态记忆*

此记忆在代理运行前添加至上下文，存储于诸如 mem0 的外部服务：

```python
from agent_framework.mem0 import Mem0Provider

# 使用 Mem0 实现高级内存功能
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
  
**代理可观察性**

可观察性对于构建可靠且易维护的代理系统至关重要。MAF 集成了 OpenTelemetry，提供追踪和监控数据以实现更好的可观察性。

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # 做某事
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```
  
### 工作流程

MAF 提供了预定义步骤的工作流程，用于完成任务，并将 AI 代理作为这些步骤中的组件。

工作流程由不同组件构成，可实现更好的控制流程。工作流程还支持 **多代理编排** 和 **检查点** 保存工作流程状态。

工作流程的核心组件包括：

**执行器**

执行器接收输入消息，执行分配任务，然后生成输出消息，推动工作流程向完成更大任务前进。执行器可以是 AI 代理或自定义逻辑。

**边缘**

边缘用于定义工作流程中消息的流向。包括：

*直接边缘* — 执行器之间的一对一简单连接：

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```
  
*条件边缘* — 满足特定条件后激活。例如，当酒店无空房时，执行器可推荐其他选项。

*开关-案例边缘* — 根据定义的条件将消息路由到不同执行器。例如，某旅行客户拥有优先访问权限，其任务将通过不同工作流程处理。

*分发边缘* — 一条消息发送到多个目标。

*汇聚边缘* — 收集来自多个执行器的消息并发送至一个目标。

**事件**

为了提升工作流程的可观察性，MAF 提供内置的执行事件，包括：

- `WorkflowStartedEvent` — 工作流程执行开始
- `WorkflowOutputEvent` — 工作流程产生输出
- `WorkflowErrorEvent` — 工作流程发生错误
- `ExecutorInvokeEvent` — 执行器开始处理
- `ExecutorCompleteEvent` — 执行器完成处理
- `RequestInfoEvent` — 发起请求

## 从其他框架迁移（Semantic Kernel 和 AutoGen）

### MAF 与 Semantic Kernel 的区别

**简化的代理创建**

Semantic Kernel 依赖为每个代理创建 Kernel 实例。MAF 通过为主要提供者使用扩展，采用了简化方法。

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```
  
**代理线程创建**

Semantic Kernel 需要手动创建线程。MAF 直接为代理分配线程。

```python
thread = agent.get_new_thread() # 使用线程运行代理。
```
  
**工具注册**

Semantic Kernel 将工具注册到 Kernel 中，再将 Kernel 传递给代理。MAF 中工具直接在代理创建时注册。

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```
  
### MAF 与 AutoGen 的区别

**团队 vs 工作流程**

`Teams` 是 AutoGen 中基于事件的代理活动结构。MAF 使用基于图架构将数据路由至执行器的 `Workflows`。

**工具创建**

AutoGen 使用 `FunctionTool` 包装函数供代理调用。MAF 使用 @ai_function，操作类似但还自动推断每个函数的 schema。

**代理行为**

在 AutoGen 中，代理默认为单轮代理，除非设置了更高的 `max_tool_iterations`。而 MAF 的 `ChatAgent` 默认支持多轮，会持续调用工具直至用户任务完成。

## 代码示例

Microsoft Agent Framework 的代码示例可在本仓库的 `xx-python-agent-framework` 和 `xx-dotnet-agent-framework` 文件夹中找到。

## 关于 Microsoft Agent Framework 有更多疑问吗？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，与其他学习者交流，参加办公时间，获取您的 AI 代理问题解答。

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免责声明**：  
本文档由AI翻译服务[Co-op Translator](https://github.com/Azure/co-op-translator)翻译。虽然我们力求准确，但请注意，自动翻译可能存在错误或不准确之处。以源语言的原始文档为权威依据。对于重要信息，建议采用专业人工翻译。对于因使用此翻译而产生的任何误解或曲解，我们不承担任何责任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->