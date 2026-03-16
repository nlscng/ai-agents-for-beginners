# 探索 Microsoft Agent Framework

![Agent Framework](../../../translated_images/zh-TW/lesson-14-thumbnail.90df0065b9d234ee.webp)

### 簡介

本課程將涵蓋：

- 了解 Microsoft Agent Framework：主要功能與價值  
- 探索 Microsoft Agent Framework 的關鍵概念
- 比較 MAF 與 Semantic Kernel 及 AutoGen：遷移指南

## 學習目標

完成本課程後，您將能夠：

- 使用 Microsoft Agent Framework 建立生產就緒的 AI Agent
- 將 Microsoft Agent Framework 的核心功能應用於您的 Agentic 用例
- 遷移並整合現有的 Agentic 框架和工具  

## 程式碼範例

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) 的程式碼範例可在本儲存庫中的 `xx-python-agent-framework` 與 `xx-dotnet-agent-framework` 檔案中找到。

## 了解 Microsoft Agent Framework

![Framework Intro](../../../translated_images/zh-TW/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) 建立在 Semantic Kernel 和 AutoGen 的經驗與學習之上。它提供靈活性，以應對在生產和研究環境中所見的各種代理用例，包括：

- **序列式代理調度**，適用於需要逐步工作流程的場景。
- **並行調度**，適用於代理需要同時完成任務的場景。
- **群組聊天調度**，適用於代理能共同合作完成同一任務的場景。
- **交接調度**，適用於當子任務完成時代理彼此交接工作的場景。
- **磁性調度**，適用於管理型代理建立及修改任務清單並協調子代理完成任務的場景。

為了提供生產階段的 AI Agent，MAF 還包含以下功能：

- **可觀察性**，透過 OpenTelemetry 監控包括工具呼叫、調度步驟、推理流程及透過 Microsoft Foundry 儀表板監控效能的每個 AI Agent 行動。
- **安全性**，在 Microsoft Foundry 原生托管代理，包含角色基礎存取、私有資料處理及內建內容安全控管。
- **耐久性**，代理執行緒與工作流程可暫停、恢復與錯誤復原，支援較長時間運行流程。
- **控制力**，支援人機互動流程，任務可標記為需要人工審核。

Microsoft Agent Framework 也重視互操作性：

- **跨雲平台** - 代理可在容器、內部部署及多個不同雲端環境中執行。
- **供應商非限定性** - 可透過您偏好的 SDK（包括 Azure OpenAI 與 OpenAI）建立代理。
- **整合開放標準** - 代理可利用 Agent-to-Agent (A2A) 與 Model Context Protocol (MCP) 等協定來發現及使用其他代理和工具。
- **外掛與連接器** - 可連接至資料和記憶服務，例如 Microsoft Fabric、SharePoint、Pinecone 與 Qdrant。

讓我們來看看這些功能如何應用於 Microsoft Agent Framework 的一些核心概念。

## Microsoft Agent Framework 的關鍵概念

### 代理 (Agents)

![Agent Framework](../../../translated_images/zh-TW/agent-components.410a06daf87b4fef.webp)

**建立代理**

代理的建立是透過定義推理服務（LLM 提供者）、代理應遵循的一組指令，以及分配一個 `name` 來完成：

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

上述範例使用的是 `Azure OpenAI`，但代理也可使用多種服務建立，包括 `Microsoft Foundry Agent Service`：

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

**運行代理**

代理可使用 `.run` 或 `.run_stream` 方法運行，分別對應非串流與串流回應。

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

每次代理運行也可以設定選項，客製化使用的參數，如代理使用的 `max_tokens`、代理可呼叫的 `tools`，甚至是該代理本身使用的 `model`。

這在完成特定用戶任務時需要特定模型或工具的情況下非常有用。

**工具**

工具可以在定義代理時設定：

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# 直接建立 ChatAgent 時

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

也可以在運行代理時設定：

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # 僅提供此執行的工具 )
```

**代理執行緒 (Agent Threads)**

代理執行緒用於處理多輪對話。執行緒的建立可以通過：

- 使用 `get_new_thread()`，讓執行緒可隨時間保存
- 在運行代理時自動建立執行緒，且執行緒僅在當前運行期間存在。

建立執行緒的程式碼如下：

```python
# 建立一個新的執行緒。
thread = agent.get_new_thread() # 使用該執行緒執行代理。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

您也可以序列化該執行緒以供日後使用：

```python
# 建立一個新的執行緒。
thread = agent.get_new_thread() 

# 使用該執行緒運行代理。

response = await agent.run("Hello, how are you?", thread=thread) 

# 將執行緒序列化以供儲存。

serialized_thread = await thread.serialize() 

# 從儲存中載入後反序列化執行緒狀態。

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**代理中介軟體 (Agent Middleware)**

代理與工具及 LLM 互動以完成用戶的任務。在某些情境下，我們希望在這些互動之間執行或追蹤動作。代理中介軟體使這成為可能，包含：

*函式中介軟體*

此中介軟體讓我們可在代理與其呼叫的函式/工具之間執行動作。用途例如在函式呼叫時做一些記錄。

代碼中 `next` 定義是否呼叫下一個中介軟體或實際函式。

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # 預處理：函式執行前記錄日誌
    print(f"[Function] Calling {context.function.name}")

    # 繼續到下一個中介軟體或函式執行
    await next(context)

    # 後處理：函式執行後記錄日誌
    print(f"[Function] {context.function.name} completed")
```

*聊天中介軟體*

此中介軟體可在代理與 LLM 間的請求之間執行或記錄動作。

它包含重要資訊，如傳送給 AI 服務的 `messages`。

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # 預處理：AI 調用前記錄日誌
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # 繼續至下一個中介軟體或 AI 服務
    await next(context)

    # 後處理：AI 回應後記錄日誌
    print("[Chat] AI response received")

```

**代理記憶 (Agent Memory)**

如同在 `Agentic Memory` 課程中所介紹，記憶是支援代理在不同語境中運作的重要元素。MAF 提供多種不同類型的記憶：

*記憶體儲存*

即在應用程式運行期間儲存在執行緒中的記憶。

```python
# 建立一個新的執行緒。
thread = agent.get_new_thread() # 使用該執行緒執行代理。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*持久訊息*

用於跨不同會話儲存對話歷史。透過 `chat_message_store_factory` 來定義：

```python
from agent_framework import ChatMessageStore

# 建立自訂訊息儲存區
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*動態記憶*

此記憶會在代理運行前加入到上下文中。這些記憶可儲存在如 mem0 等外部服務：

```python
from agent_framework.mem0 import Mem0Provider

# 使用 Mem0 進行進階記憶體功能
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

**代理可觀察性**

可觀察性是建立可靠且易維護 agentic 系統的重要環節。MAF 整合 OpenTelemetry，提供追蹤與計量器，以提升可觀察性。

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

MAF 提供了預先定義步驟以完成任務的工作流程，並將 AI 代理作為這些步驟中的元件。

工作流程由不同元件組成，以便更好地控制流程。工作流程也支援 **多代理調度** 及 **檢查點**，用以保存工作流程狀態。

工作流程的核心元件是：

**執行者 (Executors)**

執行者接收輸入訊息，執行指派的任務，然後產生輸出訊息，促使工作流程朝完成較大任務前進。執行者可為 AI 代理或自訂邏輯。

**連結 (Edges)**

連結用於定義工作流程中訊息的流向。類型包括：

*直接連結* - 執行者間簡單的一對一連接：

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*條件連結* - 在達成特定條件後啟動。例如，當旅館房間不可用時，執行者可建議其他選項。

*分支連結* - 根據定義條件將訊息分派給不同執行者。例如，若旅遊客戶有優先權，則其任務會由另一工作流程處理。

*擴散連結* - 將一則訊息傳送給多個目標。

*匯集連結* - 收集多個來自不同執行者的訊息並傳送給一個目標。

**事件 (Events)**

為了提供更好的工作流程觀察性，MAF 提供內建的執行事件，包括：

- `WorkflowStartedEvent`  - 工作流程開始執行
- `WorkflowOutputEvent` - 工作流程產生輸出
- `WorkflowErrorEvent` - 工作流程發生錯誤
- `ExecutorInvokeEvent`  - 執行者開始處理
- `ExecutorCompleteEvent`  -  執行者完成處理
- `RequestInfoEvent` - 發出請求

## 從其他框架遷移（Semantic Kernel 及 AutoGen）

### MAF 與 Semantic Kernel 的差異

**簡化代理建立**

Semantic Kernel 需要為每個代理建立一個 Kernel 實例。MAF 採用較簡化的方法，使用主要供應者的擴充套件。

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**代理執行緒建立**

Semantic Kernel 需手動建立執行緒。在 MAF 中，代理直接被分配給執行緒。

```python
thread = agent.get_new_thread() # 使用執行緒運行代理。
```

**工具註冊**

Semantic Kernel 中，工具註冊至 Kernel，然後 Kernel 傳給代理。MAF 中，工具直接在代理建立時被註冊。

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF 與 AutoGen 的差異

**團隊 (Teams) 對比 工作流程 (Workflows)**

`Teams` 是 AutoGen 中帶有事件驅動代理活動的結構。MAF 使用以圖形架構路由資料給執行者的 `Workflows`。

**工具建立**

AutoGen 使用 `FunctionTool` 將函式包裝供代理呼叫。MAF 使用 @ai_function，操作類似，但也會自動推斷每個函式的結構。

**代理行為**

在 AutoGen 中，除非設定了較高的 `max_tool_iterations`，否則代理預設是單回合。MAF 中 `ChatAgent` 預設為多回合，會持續呼叫工具直到用戶任務完成。

## 程式碼範例

Microsoft Agent Framework 的程式碼範例可在本儲存庫中的 `xx-python-agent-framework` 與 `xx-dotnet-agent-framework` 檔案中找到。

## 想了解更多關於 Microsoft Agent Framework？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) 與其他學習者會面，參加交流時間並獲得您的 AI Agent 問題解答。

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件係使用人工智慧翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 所翻譯。雖然我們致力於翻譯的準確性，但請注意自動翻譯可能包含錯誤或不準確之處。原始文件的母語版本應視為具權威性的來源。對於關鍵資訊，建議採用專業人工翻譯。我們不對因使用本翻譯而產生的任何誤解或誤譯負責。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->