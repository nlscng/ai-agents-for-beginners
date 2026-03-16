[![如何設計良好的 AI 代理人](../../../translated_images/zh-HK/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(點擊上方圖片以觀看本課程的影片)_

# 工具使用設計模式

工具之所以有趣，是因為它們可以令 AI 代理人擁有更廣泛的能力。與代理人只能執行一組有限操作不同，透過新增工具，代理人便能執行更廣泛的動作。在本章中，我們將探討工具使用設計模式，說明 AI 代理人如何使用特定工具來達成其目標。

## 介紹

在本課程中，我們希望回答以下問題：

- 什麼是工具使用設計模式？
- 可以應用於哪些使用情境？
- 實作該設計模式需要哪些要素/構建塊？
- 在使用工具使用設計模式構建值得信賴的 AI 代理人時，有哪些特別需要注意的地方？

## 學習目標

完成本課程後，你將能夠：

- 定義工具使用設計模式及其目的。
- 辨識適用於工具使用設計模式的使用案例。
- 了解實作該設計模式所需的關鍵要素。
- 辨識在使用此設計模式的 AI 代理人中，確保值得信賴性時的考量。

## 什麼是工具使用設計模式？

The **工具使用設計模式** 著重於賦予 LLMs 與外部工具互動以達成特定目標的能力。工具是可以由代理人執行以執行動作的程式碼。工具可以是簡單的函數，例如計算機，或是呼叫第三方服務的 API，例如查詢股價或天氣預報。在 AI 代理人的上下文中，工具被設計為由代理人在回應 **模型生成的函式呼叫** 時執行。

## 可以應用於哪些使用情境？

AI 代理人可以利用工具來完成複雜任務、檢索資訊或做出決策。工具使用設計模式通常用於需要與外部系統動態互動的情境，例如資料庫、網路服務或程式碼解譯器。此能力對多種使用情境非常有用，包括：

- **動態資訊檢索：** 代理人可以查詢外部 API 或資料庫以取得最新資料（例如，查詢 SQLite 資料庫以進行資料分析、擷取股價或天氣資訊）。
- **程式碼執行與解釋：** 代理人可以執行程式碼或腳本來解決數學問題、產生報告或進行模擬。
- **工作流程自動化：** 透過整合排程、電子郵件服務或資料管線等工具，自動化重複或多步驟的工作流程。
- **客戶支援：** 代理人可以與 CRM 系統、工單平台或知識庫互動以解決使用者查詢。
- **內容產生與編輯：** 代理人可以利用語法檢查器、文本摘要器或內容安全評估工具等協助內容創作工作。

## 實作工具使用設計模式所需的要素/構建塊是什麼？

這些構建塊允許 AI 代理人執行廣泛的任務。以下是實作工具使用設計模式所需的關鍵要素：

- **函數/工具結構描述 (Function/Tool Schemas)：** 可用工具的詳細定義，包括函數名稱、用途、必要參數與預期輸出。這些結構描述讓 LLM 能理解有哪些工具可用，以及如何構造有效的請求。

- **函式執行邏輯：** 決定何時以及如何根據使用者意圖與對話上下文來呼叫工具的邏輯。這可能包含規劃器模組、路由機制或條件流程，以動態決定工具的使用方式。

- **訊息處理系統：** 管理使用者輸入、LLM 回應、工具呼叫與工具輸出之間對話流程的元件。

- **工具整合框架：** 將代理人與各種工具連接的基礎建設，無論它們是簡單函數或複雜的外部服務。

- **錯誤處理與驗證：** 處理工具執行失敗、驗證參數以及管理意外回應的機制。

- **狀態管理：** 追蹤對話上下文、先前的工具互動與持久化資料，以確保跨多輪互動的一致性。

接下來，我們將更詳細地看看函式/工具呼叫。

### 函式/工具呼叫

函式呼叫是讓大型語言模型（LLMs）與工具互動的主要方式。你經常會看到「Function（函式）」和「Tool（工具）」被互換使用，因為「函式」（可重用的程式碼區塊）就是代理人用來執行任務的「工具」。為了能夠調用函式的程式碼，LLM 必須將使用者的請求與函式的描述進行比較。為此，會將包含所有可用函式描述的結構描述（schema）送給 LLM。LLM 然後選擇最適合該任務的函式並回傳其名稱與參數。選定的函式被呼叫，該函式的回應會被送回給 LLM，LLM 使用該資訊來回應使用者的請求。

要讓開發者為代理人實作函式呼叫，你需要：

1. 支援函式呼叫的 LLM 模型
2. 包含函式描述的結構描述（schema）
3. 所描述的每個函式的程式碼

讓我們用取得某城市當前時間的範例來說明：

1. **初始化支援函式呼叫的 LLM：**

    並非所有模型都支援函式呼叫，所以確認你所使用的 LLM 是否支援非常重要。     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> 支援函式呼叫。我們可以先啟動 Azure OpenAI 的 client。 

    ```python
    # 初始化 Azure OpenAI 客戶端
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **建立函式結構描述：**

    接下來我們會定義一個 JSON 結構描述，其中包含函式名稱、函式的用途說明，以及函式參數的名稱與說明。
    然後我們會將此結構描述與先前建立的 client 一併傳給模型，以及使用者要查詢舊金山時間的請求。重要的是要注意，回傳的是一個 **工具呼叫**，而不是該問題的最終答案。如前所述，LLM 會回傳它為任務所選擇的函式名稱，以及將傳給該函式的參數。

    ```python
    # 供模型閱讀的函數說明
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
  
    # 初始用戶訊息
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # 第一次 API 呼叫：要求模型使用該函數
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

    現在 LLM 已選擇需要執行的函式，我們需要實作並執行該函式的程式碼來完成任務。
    我們可以用 Python 實作取得當前時間的程式碼。還需要撰寫程式碼來從 response_message 中擷取名稱與參數，以取得最終結果。

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
     # 處理函數呼叫
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

函式呼叫是大多數（如果不是全部）代理工具使用設計的核心，然而從頭實作有時可能具有挑戰性。
如我們在[Lesson 2](../../../02-explore-agentic-frameworks)所學，代理框架（agentic frameworks）為我們提供預先構建的組件來實作工具使用。
 
## 使用代理框架的工具使用範例

以下示範如何使用不同的代理框架來實作工具使用設計模式的範例：

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> 是一個為 .NET、Python 與 Java 開發者使用大型語言模型（LLMs）所設計的開源 AI 框架。它透過稱為 <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">序列化（serializing）</a> 的過程，自動將你的函式與其參數描述化並傳給模型，簡化了使用函式呼叫的過程。它也處理模型與你的程式碼之間來回的通訊。使用像 Semantic Kernel 這類的代理框架的另一個好處是，你可以使用預建的工具，例如 <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">檔案搜尋 (File Search)</a> 與 <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">程式碼解釋器 (Code Interpreter)</a>。

下圖說明了使用 Semantic Kernel 進行函式呼叫的流程：

![函式呼叫](../../../translated_images/zh-HK/functioncalling-diagram.a84006fc287f6014.webp)

在 Semantic Kernel 中，函式/工具被稱為 <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">外掛程式 (Plugins)</a>。我們可以將之前看到的 `get_current_time` 函式轉換成外掛程式，方法是把它放到一個包含該函式的類別中。我們也可以匯入 `kernel_function` 裝飾器，該裝飾器帶入函式的說明。當你用 GetCurrentTimePlugin 建立 kernel 時，kernel 會自動將函式及其參數序列化，在過程中建立要傳給 LLM 的結構描述（schema）。

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

# 建立外掛
get_current_time_plugin = GetCurrentTimePlugin(location)

# 將外掛加入核心
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> 是一個較新的代理框架，旨在讓開發者能夠安全地建立、部署與擴展高品質且可擴充的 AI 代理，而無需管理底層的運算與儲存資源。它對企業應用特別有用，因為它是一項具有企業級安全性的完全管理服務。

與直接使用 LLM API 開發相比，Azure AI Agent Service 提供了一些優勢，包括：

- 自動工具呼叫 – 不需要解析工具呼叫、呼叫工具並處理回應；所有這些現在都在伺服器端完成
- 安全管理的資料 – 你可以依賴 threads 來儲存所有所需的對話狀態，而不是自己管理會話狀態
- 現成工具 – 可用來與資料來源互動的工具，如 Bing、Azure AI Search 與 Azure Functions

Azure AI Agent Service 中可用的工具可分為兩類：

1. 知識工具：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">使用 Bing Search 做為基礎檢索</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">檔案搜尋 (File Search)</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. 動作工具：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">函式呼叫 (Function Calling)</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">程式碼解釋器 (Code Interpreter)</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">以 OpenAPI 定義的工具</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service 允許我們將這些工具作為一個 `toolset` 一同使用。它也利用 `threads` 來追蹤特定對話的訊息歷史。

想像你是名在 Contoso 任職的銷售代理人。你希望開發一個會話型代理人，能回答有關你銷售資料的問題。

下圖說明了你如何使用 Azure AI Agent Service 來分析你的銷售資料：

![代理服務運作示意](../../../translated_images/zh-HK/agent-service-in-action.34fb465c9a84659e.webp)

要在服務中使用任何這些工具，我們可以建立一個 client 並定義一個工具或工具集。實作上，我們可以使用以下 Python 程式碼。LLM 將能夠查看該 toolset 並決定是否使用使用者建立的函式 `fetch_sales_data_using_sqlite_query`，或是依使用者請求使用預建的程式碼解釋器。

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # 位於 fetch_sales_data_functions.py 檔案中的 fetch_sales_data_using_sqlite_query 函式。
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# 初始化工具集
toolset = ToolSet()

# 初始化一個可呼叫 fetch_sales_data_using_sqlite_query 函式的代理程式，並將其加入工具集
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# 初始化 Code Interpreter 工具，並將其加入工具集。
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## 在使用工具使用設計模式構建值得信賴的 AI 代理人時，有哪些特別的注意事項？

LLM 動態產生的 SQL 常見的關切是安全性，特別是 SQL 注入或惡意操作的風險，例如刪除或竄改資料庫。雖然這些擔憂是合理的，但透過正確設定資料庫存取權限，可以有效地加以減輕。對大多數資料庫而言，這涉及將資料庫設定為唯讀。對於像 PostgreSQL 或 Azure SQL 這類資料庫服務，應為應用程式指派唯讀（SELECT）角色。

在安全環境中執行應用程式可以進一步增強防護。在企業情境中，資料通常會從營運系統中萃取並轉換到一個具有易於使用結構描述的唯讀資料庫或資料倉儲。這種做法確保資料的安全性、優化效能與可及性，並且應用程式具有受限的唯讀存取權。

## 範例程式碼
- Python: [代理框架](./code_samples/04-python-agent-framework.ipynb)
- .NET: [代理框架](./code_samples/04-dotnet-agent-framework.md)

## 對工具使用的設計模式有更多疑問嗎？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，與其他學習者交流、參加辦公時段，並獲得你有關 AI 代理人的問題解答。

## 額外資源

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents 服務工作坊</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer 多代理工作坊</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel 函數呼叫教學</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel 程式碼解譯器</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen 工具</a>

## 上一課

[理解 Agentic 設計模式](../03-agentic-design-patterns/README.md)

## 下一課

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免責聲明：
本文件已使用人工智能翻譯服務 Co-op Translator（https://github.com/Azure/co-op-translator）進行翻譯。雖然我們力求準確，但請注意自動翻譯可能包含錯誤或不準確之處。原始語言的文件應被視為權威來源。若涉及重要資訊，建議委託專業人工翻譯。我們對因使用本翻譯而引致的任何誤解或曲解概不負責。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->