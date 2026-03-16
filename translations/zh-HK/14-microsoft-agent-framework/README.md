# 探索 Microsoft Agent Framework

![代理框架](../../../translated_images/zh-HK/lesson-14-thumbnail.90df0065b9d234ee.webp)

### 介紹

本課程將涵蓋：

- 了解 Microsoft Agent Framework：關鍵功能與價值  
- 探索 Microsoft Agent Framework 的關鍵概念
- 將 MAF 與 Semantic Kernel 及 AutoGen 作比較：遷移指南

## 學習目標

完成本課程後，你將會知道如何：

- 使用 Microsoft Agent Framework 建立可投入生產的 AI 代理
- 將 Microsoft Agent Framework 的核心功能套用到你的代理化使用案例
- 遷移並整合既有的代理框架與工具  

## 範例程式碼 

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) 的範例程式碼可在此儲存庫的 `xx-python-agent-framework` 與 `xx-dotnet-agent-framework` 檔案中找到。

## 了解 Microsoft Agent Framework

![框架介紹](../../../translated_images/zh-HK/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) 建構於從 Semantic Kernel 與 AutoGen 的經驗與學習之上。它提供靈活性來處理生產與研究環境中各種代理化使用案例，包括：

- 在需要逐步工作流程的情境中，提供 **序列式代理協調 (Sequential Agent orchestration)**。
- 在代理需要同時完成任務的情境中，提供 **併發協調 (Concurrent orchestration)**。
- 在多個代理可以共同協作完成單一任務的情境中，提供 **群組聊天協調 (Group chat orchestration)**。
- 在子任務完成後代理互相移交任務的情境中，提供 **移交協調 (Handoff Orchestration)**。
- 在管理者代理建立並修改任務清單並處理子代理協調以完成任務的情境中，提供 **磁性協調 (Magnetic Orchestration)**。

為了在生產環境交付 AI 代理，MAF 還包含下列功能：

- 透過使用 OpenTelemetry 提供 **可觀測性 (Observability)**，記錄 AI 代理的每個操作，包括工具調用、協調步驟、推理流程，並可透過 Microsoft Foundry 儀表板進行效能監控。
- 透過在 Microsoft Foundry 原生託管代理來提供 **安全性 (Security)**，包含角色存取控制、私有資料處理與內建內容安全性等控管。
- 提供 **持久性 (Durability)**，代理執行緒與工作流程可以暫停、恢復並從錯誤中復原，支援長時間執行的流程。
- 提供 **控制 (Control)**，支援人為介入的工作流程，當任務標示為需要人工核可時可進行處理。

Microsoft Agent Framework 亦著重於互通性，包含：

- **雲端無關 (Being Cloud-agnostic)** — 代理可以在容器、內部部署與多個不同雲端上執行。
- **供應商無關 (Being Provider-agnostic)** — 代理可以透過你喜好的 SDK 建立，包括 Azure OpenAI 與 OpenAI。
- **整合開放標準 (Integrating Open Standards)** — 代理可利用像是 Agent-to-Agent (A2A) 與 Model Context Protocol (MCP) 等協定來探索並使用其他代理與工具。
- **外掛與連接器 (Plugins and Connectors)** — 可連接到資料與記憶服務，例如 Microsoft Fabric、SharePoint、Pinecone 與 Qdrant。

下面我們來看看這些功能如何應用於 Microsoft Agent Framework 的一些核心概念。

## Microsoft Agent Framework 的關鍵概念

### Agents

![代理組件](../../../translated_images/zh-HK/agent-components.410a06daf87b4fef.webp)

**建立代理**

代理的建立是透過定義推理服務（LLM Provider）、一組供 AI 代理遵循的指示，以及指定的 `name` 來完成：

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

上例使用的是 `Azure OpenAI`，但代理也可以使用多種服務來建立，包括 `Microsoft Foundry Agent Service`：

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

或使用 A2A 協定的遠端代理：

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**執行代理**

代理可透過 `.run` 或 `.run_stream` 方法執行，分別用於非串流或串流回應。

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

每次代理執行也可以有選項來自訂參數，例如代理使用的 `max_tokens`、代理能呼叫的 `tools`，甚至代理所使用的 `model`。

當完成使用者任務需要特定模型或工具時，這點相當有用。

**工具 (Tools)**

工具可以在定義代理時一併定義：

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# 當直接建立 ChatAgent 時

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

也可以在執行代理時指定：

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # 此工具僅於本次執行期間提供 )
```

**代理執行緒 (Agent Threads)**

代理執行緒用於處理多回合對話。執行緒可透過以下方式建立：

- 使用 `get_new_thread()`，使該執行緒能夠長時間儲存
- 在執行代理時自動建立執行緒，該執行緒僅於當前執行期間存在

建立執行緒的程式碼如下：

```python
# 建立一個新執行緒。
thread = agent.get_new_thread() # 使用該執行緒執行代理程式。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

你也可以將執行緒序列化以便日後使用：

```python
# 建立一個新的執行緒。
thread = agent.get_new_thread() 

# 用該執行緒執行代理。

response = await agent.run("Hello, how are you?", thread=thread) 

# 將執行緒序列化以便儲存。

serialized_thread = await thread.serialize() 

# 從儲存載入後反序列化執行緒狀態。

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**代理中介軟體 (Agent Middleware)**

代理會與工具與 LLM 互動以完成使用者的任務。在某些情境下，我們希望在這些互動之間執行或追蹤動作。代理中介軟體使我們能夠透過下列方式做到這點：

*函式中介軟體 (Function Middleware)*

此中介軟體允許我們在代理與其將呼叫的函式/工具之間執行一個動作。舉例來說，當你想在函式呼叫時做一些記錄時會使用到它。

在下列程式碼中，`next` 定義是否應呼叫下一個中介軟體或實際的函式。

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # 前置處理：在函數執行前記錄日誌
    print(f"[Function] Calling {context.function.name}")

    # 繼續執行下一個中介軟體或函數
    await next(context)

    # 後置處理：在函數執行後記錄日誌
    print(f"[Function] {context.function.name} completed")
```

*聊天中介軟體 (Chat Middleware)*

此中介軟體允許我們在代理與 LLM 之間的請求流程中執行或記錄某個動作。

它包含像是正在傳送給 AI 服務的 `messages` 等重要資訊。

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # 預處理：於呼叫 AI 之前紀錄
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # 繼續到下一個中介軟件或 AI 服務
    await next(context)

    # 後處理：於 AI 回應後紀錄
    print("[Chat] AI response received")

```

**代理記憶 (Agent Memory)**

如在「Agentic Memory」課程中所述，記憶是讓代理能在不同上下文中運作的重要元素。MAF 提供數種不同類型的記憶：

*記憶體內儲存 (In-Memory Storage)*

這是應用程式執行期間，執行緒中所儲存的記憶。

```python
# 建立一個新執行緒。
thread = agent.get_new_thread() # 使用該執行緒執行代理程式。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*持久化訊息 (Persistent Messages)*

當要在不同工作階段之間儲存對話歷史時會使用此記憶。它是使用 `chat_message_store_factory` 定義的：

```python
from agent_framework import ChatMessageStore

# 建立自訂訊息儲存庫
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*動態記憶 (Dynamic Memory)*

此記憶會在代理執行前加入到上下文中。這些記憶可以儲存在像 mem0 之類的外部服務中：

```python
from agent_framework.mem0 import Mem0Provider

# 使用 Mem0 以啟用進階記憶體功能
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

**代理可觀測性 (Agent Observability)**

可觀測性對於建立可靠且可維護的代理系統很重要。MAF 整合了 OpenTelemetry，以提供追蹤與計量，增進可觀測性。

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # 做啲嘢
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### 工作流程 (Workflows)

MAF 提供預先定義的步驟來完成任務的工作流程，並將 AI 代理作為這些步驟中的元件之一。

工作流程由不同的元件組成，以便更好地控制流程。工作流程也支援 **多代理協調 (multi-agent orchestration)** 與 **檢查點 (checkpointing)**，以儲存工作流程狀態。

工作流程的核心元件包括：

**執行器 (Executors)**

執行器接收輸入訊息，執行其指派的任務，然後產生輸出訊息。這推動工作流程向完成較大任務的方向前進。執行器可以是 AI 代理或自訂邏輯。

**邊 (Edges)**

邊用來定義工作流程中訊息的流向。這些可以是：

*直接邊 (Direct Edges)* - 執行器之間的一對一簡單連接：

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*條件邊 (Conditional Edges)* - 在滿足特定條件後啟動。例如，當飯店房間不可用時，某個執行器可以建議其他選項。

*切換分支邊 (Switch-case Edges)* - 根據定義的條件將訊息導向不同的執行器。例如，若旅客具有優先權存取，則其任務可能會透過另一個工作流程處理。

*分發邊 (Fan-out Edges)* - 將一則訊息發送到多個目標。

*匯聚邊 (Fan-in Edges)* - 收集來自不同執行器的多則訊息並發送到單一目標。

**事件 (Events)**

為了提供對工作流程更佳的可觀測性，MAF 提供內建的執行事件，包括：

- `WorkflowStartedEvent`  - 工作流程執行開始
- `WorkflowOutputEvent` - 工作流程產生輸出
- `WorkflowErrorEvent` - 工作流程遇到錯誤
- `ExecutorInvokeEvent`  - 執行器開始處理
- `ExecutorCompleteEvent`  - 執行器完成處理
- `RequestInfoEvent` - 發出了一個請求

## 從其他框架遷移（Semantic Kernel 與 AutoGen）

### MAF 與 Semantic Kernel 的差異

**簡化的代理建立流程**

Semantic Kernel 需要為每個代理建立一個 Kernel 實例。MAF 採用較簡化的作法，使用主要提供者的擴充套件。

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**代理執行緒建立**

Semantic Kernel 需要手動建立執行緒。在 MAF 中，代理會直接被指派一個執行緒。

```python
thread = agent.get_new_thread() # 使用該執行緒執行代理。
```

**工具註冊**

在 Semantic Kernel 中，工具會註冊到 Kernel，然後將 Kernel 傳遞給代理。在 MAF 中，工具則是在建立代理的過程中直接註冊。

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF 與 AutoGen 的差異

**Teams 與 Workflows**

`Teams` 是 AutoGen 中用於事件驅動代理活動的事件結構。MAF 使用將資料透過圖形架構路由到執行器的 `Workflows`。

**工具建立**

AutoGen 使用 `FunctionTool` 來包裝供代理呼叫的函式。MAF 使用 @ai_function，操作方式相似，但也會自動推斷每個函式的 schema。

**代理行為**

在 AutoGen 中，代理預設為單回合代理，除非將 `max_tool_iterations` 設為較高值。在 MAF 中，`ChatAgent` 預設為多回合，這表示它會持續呼叫工具，直到使用者的任務完成為止。

## 範例程式碼 

Microsoft Agent Framework 的範例程式碼可在此儲存庫的 `xx-python-agent-framework` 與 `xx-dotnet-agent-framework` 檔案中找到。

## 對 Microsoft Agent Framework 有更多問題嗎？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) 與其他學習者交流、參加辦公時間，並獲得你的 AI 代理相關問題解答。

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免責聲明：
本文件已使用 AI 翻譯服務 Co-op Translator (https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們力求準確，但自動翻譯可能包含錯誤或不準確之處。原文件的母語版本應被視為具權威性的版本。對於重要資訊，建議採用專業人工翻譯。我們不會對因使用本翻譯而引致的任何誤解或誤釋承擔責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->