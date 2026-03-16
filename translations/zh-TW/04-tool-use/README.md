[![如何設計優秀的 AI 代理](../../../translated_images/zh-TW/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(點擊上方圖片觀看本課程影片)_

# 工具使用設計模式

工具很有趣，因為它們讓 AI 代理可以擁有更廣泛的能力範圍。不再侷限於代理自身有限的行動集合，透過加入工具，代理現在能執行更多元的行動。在本章節，我們將探討工具使用設計模式，說明 AI 代理如何使用特定工具來達成目標。

## 簡介

本課程將嘗試回答以下問題：

- 什麼是工具使用設計模式？
- 它適用於哪些使用案例？
- 實作此設計模式需要哪些元素／構建塊？
- 使用工具使用設計模式構建值得信賴的 AI 代理有哪些特殊考量？

## 學習目標

完成本課程後，你將能夠：

- 定義工具使用設計模式及其目的。
- 辨識適用工具使用設計模式的使用案例。
- 瞭解實作該設計模式所需的關鍵元素。
- 認識使用此設計模式確保 AI 代理可信度的考量。

## 什麼是工具使用設計模式？

**工具使用設計模式**著重於賦予大型語言模型（LLM）與外部工具互動的能力，以達成特定目標。工具是能由代理執行以執行行動的程式碼。工具可以是簡單的函式（例如計算機），或是第三方服務的 API 呼叫（例如查詢股價或天氣預報）。在 AI 代理情境中，工具設計為在回應 **模型生成的函式呼叫** 時由代理執行。

## 它適用於哪些使用案例？

AI 代理能利用工具完成複雜任務、擷取資訊或做出決策。工具使用設計模式常見於需要與外部系統（如資料庫、網路服務或程式碼解譯器）動態互動的場景。這項能力適用於多種使用案例，包括：

- **動態資訊擷取：** 代理能查詢外部 API 或資料庫以取得最新資料（例如查詢 SQLite 資料庫做資料分析，獲取股價或天氣資訊）。
- **程式碼執行與解譯：** 代理能執行程式碼或腳本來解決數學問題、產生報告或執行模擬。
- **工作流程自動化：** 整合工具如任務排程器、電子郵件服務或資料管線，實現重複或多步驟工作流程的自動化。
- **客戶支援：** 代理能與 CRM 系統、票務平台或知識庫互動，解決使用者問題。
- **內容生成與編輯：** 利用語法檢查器、文字摘要器或內容安全評估工具協助內容創作。

## 實作工具使用設計模式需要哪些元素／構建塊？

這些構建塊讓 AI 代理能執行多種任務。以下為實作工具使用設計模式所需的關鍵元素：

- **函式／工具結構定義（Schemas）：** 詳細定義可用工具，包括函式名稱、用途、所需參數及預期輸出。這些結構定義讓 LLM 能理解可用工具與如何構建有效請求。

- **函式執行邏輯：** 根據使用者意圖與對話上下文決定何時及如何調用工具。可包含規劃模組、路由機制或條件流程，動態決定工具使用。

- **訊息處理系統：** 管理使用者輸入、LLM 回應、工具呼叫及工具輸出間的對話流程。

- **工具整合框架：** 連結代理與各種工具的基礎建設，無論是簡單函式還是複雜的外部服務。

- **錯誤處理與驗證：** 處理工具執行失敗、驗證參數及管理非預期回應的機制。

- **狀態管理：** 追蹤對話上下文、先前工具互動及持續性資料，確保多輪互動間的一致性。

接下來，我們更詳細探討函式／工具呼叫。

### 函式／工具呼叫

函式呼叫是讓大型語言模型（LLM）與工具互動的主要方式。常會看到「函式（Function）」和「工具（Tool）」互換使用，因為「函式」（可重用的程式碼區塊）即是代理用來執行任務的「工具」。為了讓函式程式碼被呼叫，LLM 必須將使用者請求與函式描述進行比對。為此，會將包含所有可用函式描述的結構定義（schema）傳給 LLM。LLM 接著選擇最適合該任務的函式並回傳其名稱及參數。選擇的函式被呼叫，回應傳回給 LLM，LLM 利用此資訊回應使用者請求。

開發者若要為代理實作函式呼叫，需要：

1. 支援函式呼叫的 LLM 模型
2. 包含函式描述的結構定義
3. 每個函式對應的程式碼

利用查詢城市當前時間範例說明：

1. **初始化支援函式呼叫的 LLM：**

    並非所有模型都支援函式呼叫，因此確認所用的 LLM 是否支援非常重要。<a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> 支援函式呼叫。我們可先啟動 Azure OpenAI 用戶端。

    ```python
    # 初始化 Azure OpenAI 用戶端
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **建立函式結構定義：**

    接著我們定義包含函式名稱、函式功能描述，以及函式參數名稱和描述的 JSON 結構定義（schema）。
    接著將此結構定義與使用者請求（例如查詢舊金山時間）傳給前述用戶端。重要的是 **返回的是工具呼叫**，**不是問題的最終答案**。如前所述，LLM 會回傳其選擇用於任務的函式名稱及將傳入的參數。

    ```python
    # 函式說明供模型閱讀
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # 初始使用者訊息
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # 第一個 API 呼叫：請模型使用該函式
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # 處理模型的回應
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **執行任務所需的函式程式碼：**

    LLM 選定要執行的函式後，需實作並執行該函式的程式碼。
    這裡我們用 Python 實作獲得當前時間的程式碼。也需撰寫程式碼從 response_message 擷取函式名稱及參數以取得最終結果。

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # 處理函式呼叫
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # 第二次 API 呼叫：從模型取得最終回應
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

函式呼叫是大多數（如果不是全部）代理工具使用設計的核心，然而自行從零實作有時具有挑戰性。
正如我們在 [Lesson 2](../../../02-explore-agentic-frameworks) 學到，代理框架提供預先構建的構建塊來實作工具使用。

## 使用代理框架的工具使用範例

以下為使用不同代理框架實作工具使用設計模式的範例：

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> 是一個針對 .NET、Python 及 Java 開發者設計的開源 AI 框架，適用於大型語言模型（LLM）。它透過稱為<a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">序列化</a>的過程，自動描述函式及其參數給模型，簡化函式呼叫的過程。它同時管理模型與程式碼間的雙向通信。使用像 Semantic Kernel 這類代理框架的另一優點是，能使用預建工具如<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">檔案搜尋</a>與<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">程式碼解譯器</a>。

下圖說明 Semantic Kernel 的函式呼叫流程：

![function calling](../../../translated_images/zh-TW/functioncalling-diagram.a84006fc287f6014.webp)

在 Semantic Kernel 中，函式／工具稱為<a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">插件（Plugins）</a>。我們可以將先前看到的 `get_current_time` 函式轉成插件，方法是用類別包裝該函式，並引入帶有函式描述的 `kernel_function` 裝飾器。建立包含 GetCurrentTimePlugin 的 kernel 後，kernel 會自動序列化函式與參數，建立送給 LLM 的結構定義。

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# 建立核心
kernel = Kernel()

# 建立外掛程式
get_current_time_plugin = GetCurrentTimePlugin(location)

# 將外掛程式加入核心
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI 代理服務

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> 是一個較新的代理框架，旨在協助開發者安全地建構、部署並擴展高品質、可擴充的 AI 代理，無需管理底層的計算與儲存資源。此服務特別適合企業應用，因為它是全託管服務並具備企業級安全。

相較於直接透過 LLM API 開發，Azure AI Agent Service 提供諸多優勢，包括：

- 自動工具呼叫：不需自行解析工具呼叫、執行工具與處理回應，這些皆由伺服器端完成
- 安全管理資料：無需管理對話狀態，可依賴「threads」儲存所有需要的資訊
- 現成工具：可用於與資料源互動的工具，例如 Bing、Azure AI Search 和 Azure Functions

Azure AI Agent Service 所提供的工具可分為兩大類：

1. 知識工具：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">結合 Bing 搜尋</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">檔案搜尋</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI 搜尋</a>

2. 動作工具：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">函式呼叫</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">程式碼解譯器</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI 定義工具</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service 允許我們將這些工具作為 `toolset` 一起使用。它同時利用 `threads` 追蹤特定對話的訊息歷史。

假設你是名為 Contoso 公司的銷售人員，想開發能回答銷售數據相關問題的對話代理。

下圖展示如何使用 Azure AI Agent Service 來分析銷售數據：

![Agentic Service In Action](../../../translated_images/zh-TW/agent-service-in-action.34fb465c9a84659e.webp)

要使用服務中任一工具，我們可建立客戶端並定義工具或工具集。以下 Python 程式碼示範實作方法。LLM 將會檢視工具集，根據使用者請求決定使用自訂函式 `fetch_sales_data_using_sqlite_query` 或預建的程式碼解譯器。

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query 函數，可以在 fetch_sales_data_functions.py 檔案中找到。
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# 初始化工具組
toolset = ToolSet()

# 使用 fetch_sales_data_using_sqlite_query 函數初始化函數調用代理並將其添加到工具組
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# 初始化程式碼解讀器工具並將其添加到工具組。
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## 使用工具使用設計模式構建值得信賴 AI 代理的特殊考量？

LLM 動態產生 SQL 時，常見的疑慮是安全性，特別是 SQL 注入或惡意操作（如刪除或竄改資料庫）風險。這些疑慮確實存在，但可透過適當配置資料庫存取權限有效緩解。大部分資料庫可設成唯讀。對於 PostgreSQL 或 Azure SQL 等資料庫服務，應分配唯讀（SELECT）角色給應用程式。

在安全環境中執行應用程式可進一步提升防護。在企業場景中，資料通常會從營運系統提取並轉換至唯讀資料庫或資料倉儲，並設計易用的資料架構。此舉確保資料安全、性能優化且易於存取，同時應用程式存取有限且為唯讀。

## 範例程式碼
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## 對工具使用設計模式有更多疑問嗎？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，與其他學習者交流，參加辦公時間，並獲得 AI Agents 問題的解答。

## 額外資源

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service 工作坊</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso 創意作家多代理人工作坊</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel 函數呼叫教學</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel 程式碼解譯器</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen 工具</a>

## 上一課程

[理解 Agentic 設計模式](../03-agentic-design-patterns/README.md)

## 下一課程

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們致力於確保準確性，但請注意，自動翻譯可能包含錯誤或不準確之處。原始文件的母語版本應被視為權威來源。對於關鍵資訊，建議採用專業人工翻譯。我們不對因使用本翻譯所產生的任何誤解或誤譯承擔責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->