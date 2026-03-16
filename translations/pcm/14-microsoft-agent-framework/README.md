# Exploring Microsoft Agent Framework

![Agent Framework](../../../translated_images/pcm/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introduction

Dis lesson go cover:

- Understanding Microsoft Agent Framework: Key Features and Value  
- Exploring di Key Concepts of Microsoft Agent Framework
- Comparing MAF to Semantic Kernel and AutoGen: Migration Guide

## Learning Goals

After you don finish dis lesson, you go sabi how to:

- Build Production Ready AI Agents usin Microsoft Agent Framework
- Apply di core features of Microsoft Agent Framework to your Agentic Use Cases
- Migrate and join together existing Agentic frameworks and tools  

## Code Samples 

Code samples for [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) fit dey inside dis repository under `xx-python-agent-framework` and `xx-dotnet-agent-framework` files.

## Understanding Microsoft Agent Framework

![Framework Intro](../../../translated_images/pcm/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) build ontop di experience and learnings from Semantic Kernel and AutoGen. E dey offer di flexibility to handle di wide kain agentic use cases wey dey for both production and research environments including:

- **Sequential Agent orchestration** for places wey workflow need follow step-by-step.
- **Concurrent orchestration** for places wey agents need finish task together at di same time.
- **Group chat orchestration** for places wey agents fit join body to work on one task.
- **Handoff Orchestration** for places wey agents dey pass task from one to another as di subtasks dey complete.
- **Magnetic Orchestration** for places wey manager agent dey create and change task list and manage di coordination of subagents to finish di task.

To deliver AI Agents for Production, MAF also add features for:

- **Observability** through di use of OpenTelemetry wey go catch every action of di AI Agent including tool invocation, orchestration steps, reasoning flows and performance monitoring through Microsoft Foundry dashboards.
- **Security** by hosting agents natively on Microsoft Foundry wey get controls like role-based access, private data handling and built-in content safety.
- **Durability** as Agent threads and workflows fit pause, resume and recover from errors wey allow longer running process.
- **Control** as human for loop workflows dey supported where tasks need human approval.

Microsoft Agent Framework sef focus to dey interoperable by:

- **Being Cloud-agnostic** - Agents fit run for containers, on-prem and across different clouds.
- **Being Provider-agnostic** - Agents fit build through your preferred SDK including Azure OpenAI and OpenAI
- **Integrating Open Standards** - Agents fit use protocols like Agent-to-Agent(A2A) and Model Context Protocol (MCP) to find and use other agents and tools.
- **Plugins and Connectors** - Connections fit join data and memory services like Microsoft Fabric, SharePoint, Pinecone and Qdrant.

Make we see how these features dey put to work for some core concepts of Microsoft Agent Framework.

## Key Concepts of Microsoft Agent Framework

### Agents

![Agent Framework](../../../translated_images/pcm/agent-components.410a06daf87b4fef.webp)

**Creating Agents**

Agent creation happen by defining di inference service (LLM Provider), a
set of instructions wey di AI Agent go follow, and an assigned `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Dis one dey use `Azure OpenAI` but agents fit create using many services including `Microsoft Foundry Agent Service`:

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

or remote agents using di A2A protocol:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Running Agents**

Agents dey run using di `.run` or `.run_stream` methods for either non-streaming or streaming responses.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Each agent run fit get options to customize parameters like `max_tokens` wey di agent go use, `tools` wey di agent fit call, and even the `model` wey di agent go use.

Dis one useful when specific models or tools need to complete user task.

**Tools**

Tools fit define both when you dey define di agent:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Wen yu de make ChatAgent direct

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

and also when you dey run di agent:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Tool we dem provide just for dis run)
```

**Agent Threads**

Agent Threads dey used to handle multi-turn conversations. Threads fit create by either:

- Using `get_new_thread()` wey pipo go fit save di thread over time
- Create thread automatically when dem run agent but thread go last only during di current run.

To create thread di code be like dis:

```python
# Make new thread.
thread = agent.get_new_thread() # Run di agent wit di thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

You fit then serialize di thread to keep am for later use:

```python
# Make new thread.
thread = agent.get_new_thread() 

# Run di agent wit di thread.

response = await agent.run("Hello, how are you?", thread=thread) 

# Put di thread put for storage.

serialized_thread = await thread.serialize() 

# Bring back di thread state after e come from storage.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent Middleware**

Agents dey interact with tools and LLMs to complete user's tasks. For some cases, we want run or track wetin dey happen between these interactions. Agent middleware go help us do dis through:

*Function Middleware*

Dis middleware dey allow us execute action between di agent and di function/tool wey e go call. One example na when you want do some logging on top function call.

For di code wey dey below `next` na wetin go decide if the next middleware or di real function go call.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Pre-processing: Log before function execution
    print(f"[Function] Calling {context.function.name}")

    # Continue to next middleware or function execution
    await next(context)

    # Post-processing: Log after function execution
    print(f"[Function] {context.function.name} completed")
```

*Chat Middleware*

Dis middleware dey allow us do or log action between di agent and requests wey dey pass between LLM .

Dis one get important information like di `messages` wey dem dey send to AI service.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Pre-processing: Di log wey we go take before we call AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Continue go next middleware or AI service
    await next(context)

    # Post-processing: Di log wey we go take after AI don respond
    print("[Chat] AI response received")

```

**Agent Memory**

Like we cover for `Agentic Memory` lesson, memory na important part to make di agent fit work through different contexts. MAF get many kinds of memory:

*In-Memory Storage*

Na dis memory dey store inside threads during application runtime.

```python
# Make new thread.
thread = agent.get_new_thread() # Run the agent wit di thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Persistent Messages*

Dis memory dey used when you want keep conversation history across different sessions. E dey defined using di `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Make one custom message store
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamic Memory*

Dis memory go add inside context before agents go run. These memories fit dey stored for external services like mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Di Mem0 dey use for beta memory use dem
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

**Agent Observability**

Observability important to build reliable and maintainable agentic systems. MAF dey join OpenTelemetry to provide tracing and meters for better observability.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # do sometin
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Workflows

MAF get workflows wey be pre-defined steps to complete task and include AI agents as part for those steps.

Workflows get different components wey help control flow better. Workflows also fit do **multi-agent orchestration** and **checkpointing** to save workflow states.

Main components for workflow na:

**Executors**

Executors receive input messages, do their assigned tasks, then dem produce output message. E dey push workflow go ahead to complete big task. Executors fit be AI agent or custom logic.

**Edges**

Edges dey used to define how messages dey flow for workflow. These fit be:

*Direct Edges* - Simple connections one to one between executors:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Conditional Edges* - Go activate once condition don meet. For example, when hotel rooms no dey, executor fit suggest other options.

*Switch-case Edges* - Go route messages to different executors based on defined conditions. For example. if travel customer get priority access and their tasks go handle through another workflow.

*Fan-out Edges* - Send one message to many targets.

*Fan-in Edges* - Gather many messages from different executors then send am to one target.

**Events**

To help observability inside workflows, MAF get built-in events for execution including:

- `WorkflowStartedEvent`  - Workflow don start
- `WorkflowOutputEvent` - Workflow don produce output
- `WorkflowErrorEvent` - Workflow get error
- `ExecutorInvokeEvent`  - Executor start to process
- `ExecutorCompleteEvent`  -  Executor finish processing
- `RequestInfoEvent` - Request don issue

## Migrating From Other Frameworks (Semantic Kernel and AutoGen)

### Differences between MAF and Semantic Kernel

**Simplified Agent Creation**

Semantic Kernel dey require you create Kernel instance for every agent. MAF dey use simplified way by using extensions for main providers.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Agent Thread Creation**

Semantic Kernel want make you create threads by hand. For MAF, agent dey directly assign thread.

```python
thread = agent.get_new_thread() # Make de agent run wit de thread.
```

**Tool Registration**

For Semantic Kernel, tools go register to Kernel and Kernel go pass am to agent. For MAF, tools register direct during agent creation.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Differences between MAF and  AutoGen

**Teams vs Workflows**

`Teams` na event structure for event driven activity with agents for AutoGen. MAF dey use `Workflows` wey dey route data to executors through graph based architecture.

**Tool Creation**

AutoGen dey use `FunctionTool` to wrap functions for agents to call. MAF dey use @ai_function wey dey work similar but e also automatic infer schemas for each function.

**Agent Behaviour**

Agents na single-turn agents by default for AutoGen unless dem set `max_tool_iterations` to higher value. For MAF, `ChatAgent` na multi-turn by default mean say e go continue to call tools until user's task finish.

## Code Samples 

Code samples for Microsoft Agent Framework fit dey for this repository under `xx-python-agent-framework` and `xx-dotnet-agent-framework` files.

## Got More Questions About Microsoft Agent Framework?

Join di [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet other learners, attend office hours and get your AI Agents questions answered.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dis dokiment don translate wit AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator). Even tho we dey try make am correct, abeg sabi say automated translations fit get mistakes or no too correct. Di original dokiment for im own language na di correct source. For important matter, e better make person wey sabi human translation do am. We no responsible for any kasala or waka wey fit happen because of dis translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->