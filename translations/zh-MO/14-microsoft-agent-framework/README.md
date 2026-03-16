# 探索 Microsoft Agent Framework

![Agent Framework](../../../translated_images/zh-MO/lesson-14-thumbnail.90df0065b9d234ee.webp)

### 介紹

本課程將涵蓋：

- 了解 Microsoft Agent Framework：關鍵功能與價值  
- 探索 Microsoft Agent Framework 的核心概念
- 比較 MAF 與 Semantic Kernel 和 AutoGen：遷移指南

## 學習目標

完成本課程後，您將能夠：

- 使用 Microsoft Agent Framework 建立生產級 AI Agents
- 將 Microsoft Agent Framework 核心功能應用於您的 Agentic 使用案例
- 遷移並整合現有的 Agentic 框架與工具  

## 程式碼範例

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) 的程式碼範例可在本儲存庫中的 `xx-python-agent-framework` 與 `xx-dotnet-agent-framework` 檔案內找到。

## 認識 Microsoft Agent Framework

![Framework Intro](../../../translated_images/zh-MO/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) 建立於 Semantic Kernel 和 AutoGen 的經驗與學習之上。它提供靈活性以處理生產與研究環境中各種 agentic 使用案例，包括：

- **順序式 Agent 編排**：適用於需要逐步工作流程的場景。
- **並行編排**：適用於代理需同時完成任務的場景。
- **群組聊天編排**：適用於多個代理可共同合作完成一項任務的場景。
- **任務轉接編排**：適用於代理在完成子任務後，將任務交接給彼此的場景。
- **磁吸式編排**：適用於管理代理建立與修改任務清單，並協調子代理完成任務的場景。

為了在生產環境中交付 AI Agents，MAF 還包含以下功能：

- **可觀察性**：透過使用 OpenTelemetry，AI Agent 的每個動作包括工具調用、編排步驟、推理流程，以及透過 Microsoft Foundry 儀表板進行效能監控均可追蹤。
- **安全性**：透過 Microsoft Foundry 原生運行代理，包含角色基礎存取控制、私人資料處理以及內建內容安全防護。
- **耐久性**：代理執行緒與工作流程可暫停、恢復並從錯誤中復原，使長時間運作的流程成為可能。
- **控制性**：支援人工審核工作流程，可標示任務需人工核准。

Microsoft Agent Framework 亦著重於互通性：

- **雲端中立性**—代理可於容器、本地端與多種不同雲端運行。
- **供應商中立性**—代理可透過您偏好的 SDK 建立，包括 Azure OpenAI 與 OpenAI。
- **整合開放標準**—代理可利用 Agent-to-Agent (A2A) 與 Model Context Protocol (MCP) 等協定發現並使用其他代理與工具。
- **外掛與連接器**—可連接至資料與記憶服務，如 Microsoft Fabric、SharePoint、Pinecone 與 Qdrant。

接下來讓我們看看這些功能如何應用於 Microsoft Agent Framework 的核心概念。

## Microsoft Agent Framework 的核心概念

### 代理 (Agents)

![Agent Framework](../../../translated_images/zh-MO/agent-components.410a06daf87b4fef.webp)

**建立代理**

建立代理是定義推理服務（LLM 提供者）、AI Agent 欲遵循的一組指令，以及指定 `name`：

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

上述使用的是 `Azure OpenAI`，但代理也可透過各種服務建立，包括 `Microsoft Foundry Agent Service`：

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

或使用 A2A 協定的遠端代理：

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**執行代理**

代理可使用 `.run` 或 `.run_stream` 方法執行，分別對應非串流或串流回應。

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

每次代理執行也可以透過選項自訂參數，如代理所用的 `max_tokens`、代理能調用的 `tools`，甚至代理所使用的 `model`。

此功能對於需要特定模型或工具完成任務的情況非常有用。

**工具 (Tools)**

工具可在定義代理時設定：

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# 直接建立 ChatAgent 時

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

也可在執行代理時設定：

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # 僅供本次運行使用的工具 )
```

**代理執行緒 (Agent Threads)**

代理執行緒用於管理多輪對話。執行緒可透過以下方式建立：

- 使用 `get_new_thread()` 允許執行緒隨時間儲存
- 在執行代理時自動建立執行緒，且該執行緒只在當前執行期間有效

建立執行緒的程式碼如下：

```python
# 創建一個新的線程。
thread = agent.get_new_thread() # 用該線程運行代理。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

然後可將執行緒序列化以便後續使用：

```python
# 建立一個新的執行緒。
thread = agent.get_new_thread() 

# 使用該執行緒運行代理。

response = await agent.run("Hello, how are you?", thread=thread) 

# 序列化執行緒以便儲存。

serialized_thread = await thread.serialize() 

# 從儲存中載入後反序列化執行緒狀態。

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**代理中介軟體 (Agent Middleware)**

代理與工具及 LLM 互動以完成使用者任務。在某些場景中，我們希望能在交互過程中執行或追蹤特定動作。代理中介軟體透過以下方式實現此功能：

*函式中介軟體 (Function Middleware)*

此中介軟體允許我們在代理與所呼叫的函式/工具之間執行動作。例如，可能會在函式呼叫時進行日誌記錄。

以下程式碼中，`next` 定義是否呼叫下一個中介軟體或實際函式。

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # 前置處理：函數執行前記錄日誌
    print(f"[Function] Calling {context.function.name}")

    # 繼續至下一個中間件或執行函數
    await next(context)

    # 後置處理：函數執行後記錄日誌
    print(f"[Function] {context.function.name} completed")
```

*聊天中介軟體 (Chat Middleware)*

此中介軟體允許我們在代理與 LLM 間的請求間執行或記錄動作。

這包含重要資訊，如傳送給 AI 服務的 `messages`。

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # 預處理：在 AI 呼叫前記錄日誌
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # 繼續到下一個中介軟件或 AI 服務
    await next(context)

    # 後處理：在 AI 回應後記錄日誌
    print("[Chat] AI response received")

```

**代理記憶 (Agent Memory)**

如「Agentic Memory」課程所述，記憶是讓代理在不同上下文中操作的重要元素。MAF 提供多種類型的記憶：

*記憶體內儲存 (In-Memory Storage)*

指應用程式執行期間於執行緒中儲存的記憶。

```python
# 建立一個新執行緒。
thread = agent.get_new_thread() # 用該執行緒運行代理。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*持久訊息 (Persistent Messages)*

用於跨不同工作階段儲存對話歷史。透過 `chat_message_store_factory` 定義：

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

此類記憶於代理執行前加入上下文，可儲存在外部服務，如 mem0：

```python
from agent_framework.mem0 import Mem0Provider

# 使用Mem0以獲得進階的記憶體功能
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

**代理可觀察性 (Agent Observability)**

可觀察性是建立可靠且易維護 agentic 系統的重要關鍵。MAF 與 OpenTelemetry 整合，提供追蹤與計量功能以提升可觀察性。

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

### 工作流程 (Workflows)

MAF 提供預先定義的工作流程步驟以完成任務，並將 AI 代理作為這些步驟中的元件。

工作流程由不同元件構成，增強流程控制。工作流程亦支援 **多代理編排** 及 **檢查點**，以儲存工作流程狀態。

工作流程的核心元件有：

**執行者 (Executors)**

執行者接收輸入訊息，執行其指派的任務，然後產出輸出訊息，推動工作流程向完成整體任務前進。執行者可為 AI 代理或自訂邏輯。

**邊 (Edges)**

邊用來定義工作流程中的訊息流向。類型包括：

*直接邊* - 執行者間一對一簡單連接：

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*條件邊* - 在特定條件達成後啟動。例如，當飯店房間不可用時，執行者可以建議其他選項。

*切換-案例邊* - 根據定義的條件將訊息導向不同執行者。例如，若旅遊客戶有優先權，其任務將透過另一工作流程處理。

*分散邊* - 將一則訊息發送至多個目標。

*匯聚邊* - 集合多個不同執行者的訊息並發送至單一目標。

**事件 (Events)**

為提供更佳的工作流程可觀察性，MAF 提供內建的執行事件，包括：

- `WorkflowStartedEvent`  - 工作流程執行開始
- `WorkflowOutputEvent` - 工作流程產生輸出
- `WorkflowErrorEvent` - 工作流程發生錯誤
- `ExecutorInvokeEvent`  - 執行者開始處理
- `ExecutorCompleteEvent`  - 執行者完成處理
- `RequestInfoEvent` - 發出請求

## 從其他框架遷移（Semantic Kernel 和 AutoGen）

### MAF 與 Semantic Kernel 的差異

**簡化的代理建立**

Semantic Kernel 需要為每個代理建立 Kernel 實例。MAF 採用簡化方式，透過主要提供者的擴充套件進行。

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**代理執行緒建立**

Semantic Kernel 需手動建立執行緒。MAF 將執行緒直接指派給代理。

```python
thread = agent.get_new_thread() # 使用執行緒運行代理。
```

**工具註冊**

Semantic Kernel 將工具註冊至 Kernel，然後將 Kernel 傳給代理。MAF 則在建立代理時直接註冊工具。

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF 與 AutoGen 的差異

**Teams 與 Workflows**

AutoGen 中的 `Teams` 是事件驅動代理活動的事件結構。MAF 使用 `Workflows`，透過圖形架構將資料路由至執行者。

**工具建立**

AutoGen 使用 `FunctionTool` 將函式包裝供代理調用。MAF 使用 @ai_function，操作相似，且自動推斷每個函式的結構。

**代理行為**

AutoGen 中代理預設為單輪代理，除非設定 `max_tool_iterations` 為更高值。MAF 中的 `ChatAgent` 預設為多輪代理，意即會持續調用工具直到使用者任務完成。

## 程式碼範例

Microsoft Agent Framework 的程式碼範例可在本儲存庫中的 `xx-python-agent-framework` 與 `xx-dotnet-agent-framework` 檔案內找到。

## 對 Microsoft Agent Framework 有更多疑問嗎？

歡迎加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，與其他學習者交流、參加辦公時間並獲得您關於 AI Agents 的問題解答。

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件已使用人工智能翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們努力確保翻譯的準確性，但請注意，機器自動翻譯可能存在錯誤或不準確之處。原文檔的母語版本應被視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們不對因使用本翻譯而產生的任何誤解或誤譯承擔責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->