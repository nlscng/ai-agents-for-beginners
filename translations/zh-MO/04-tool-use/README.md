[![如何設計優秀的 AI 代理](../../../translated_images/zh-MO/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(點擊上方圖片觀看本課程影片)_

# 工具使用設計模式

工具之所以有趣，是因為它們讓 AI 代理擁有更廣泛的能力範圍。代理不再只能執行有限的一組動作，藉由加入工具，代理現在可以執行廣泛的動作。在本章中，我們將探討工具使用設計模式，描述 AI 代理如何使用特定工具來達成目標。

## 簡介

本課程旨在回答以下問題：

- 什麼是工具使用設計模式？
- 它可應用於哪些使用情境？
- 實作該設計模式所需的要素／構建方塊是什麼？
- 使用工具使用設計模式來建構值得信賴的 AI 代理有什麼特別考量？

## 學習目標

完成本課程後，您將能夠：

- 定義工具使用設計模式及其目的。
- 辨識適合應用工具使用設計模式的使用情境。
- 了解實作該設計模式所需的關鍵要素。
- 認識使用此設計模式確保 AI 代理值得信賴的考量因素。

## 什麼是工具使用設計模式？

**工具使用設計模式**著重於賦予大型語言模型（LLM）與外部工具互動的能力，以達成特定目標。工具是可由代理執行以完成動作的程式碼。工具可以是簡單的函式，例如計算器，或是呼叫第三方服務的 API，如股票價格查詢或天氣預報。在 AI 代理的語境中，工具設計為由代理根據**模型產生的函式呼叫**來執行。

## 可應用於哪些使用案例？

AI 代理可以利用工具完成複雜任務、檢索資訊或做出決策。工具使用設計模式常用於需要與外部系統動態互動的情境，例如資料庫、網路服務或程式碼解釋器。這種能力對多種使用案例很有用，包括：

- **動態資訊檢索：** 代理能查詢外部 API 或資料庫以取得最新資料（例如查詢 SQLite 資料庫做資料分析、取得股票價格或天氣資訊）。
- **程式碼執行與解釋：** 代理可以執行程式碼或腳本，解決數學問題、產生報告或進行模擬。
- **工作流程自動化：** 透過整合任務排程器、電子郵件服務或資料管線，達成重複性或多步驟工作流程的自動化。
- **客服支援：** 代理能與 CRM 系統、工單平台或知識庫互動，以解決用戶問題。
- **內容產生與編輯：** 代理可利用語法檢查、文字摘要或內容安全評估工具，協助內容創作任務。

## 實作工具使用設計模式所需的要素／構建方塊？

這些構建方塊允許 AI 代理執行廣泛任務。讓我們來看實作工具使用設計模式所需的關鍵要素：

- **函式／工具結構描述（Schemas）：** 詳細定義可用工具，包括函式名稱、用途、必要參數和預期輸出。這些結構使 LLM 能理解可用工具及如何構造有效請求。

- **函式執行邏輯：** 控制何時及如何根據用戶意圖和對話上下文調用工具。可能包含規劃模組、路由機制或條件流程，以動態決定工具使用。

- **訊息處理系統：** 管理用戶輸入、LLM 回應、工具呼叫與工具輸出間對話流程的組件。

- **工具整合框架：** 連接代理與各種工具的基礎設施，無論是簡單函式或複雜外部服務。

- **錯誤處理與驗證：** 處理工具執行失敗、驗證參數及管理意外回應的機制。

- **狀態管理：** 追蹤對話上下文、先前工具交互與持久資料，確保多輪互動的一致性。

接下來，我們更詳細探討函式／工具呼叫。

### 函式／工具呼叫

函式呼叫是讓大型語言模型（LLM）與工具互動的主要方式。您會常看到「函式」和「工具」互換使用，因為「函式」（可重用的程式碼塊）是代理用來執行任務的「工具」。為使函式程式碼被調用，LLM 必須將用戶請求與函式描述對比。為此，一個包含所有可用函式描述的結構會傳送給 LLM。LLM 接著選擇最合適的函式及其參數，回傳函式名稱與引數。之後呼叫該函式，將回應送回 LLM，LLM 使用資訊回應用戶請求。

開發者若要為代理實作函式呼叫，需具備：

1. 支援函式呼叫的 LLM 模型
2. 包含函式描述的結構
3. 每個描述函式的程式碼

用取得某城市當前時間的範例說明：

1. **初始化支援函式呼叫的 LLM：**

   並非所有模型都支援函式呼叫，因此請確認您使用的 LLM 支援。<a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> 支援函式呼叫。我們可以先啟動 Azure OpenAI 用戶端。

    ```python
    # 初始化 Azure OpenAI 用戶端
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **建立函式結構描述（Schema）：**

   接著定義一個 JSON 結構，包含函式名稱、描述及函式參數名稱和說明。接著將此結構與用戶查詢舊金山時間的請求一併傳給先前建立的客戶端。需注意的是，回傳的是**工具呼叫**，並非問題的最終答案。如前所述，LLM 回傳它為任務選擇的函式名稱與要傳遞的引數。

    ```python
    # 模型可讀的功能描述
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
  
    # 第一次API調用：請模型使用該功能
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
  
1. **執行任務的函式程式碼：**

   LLM 選定要執行的函式後，實作且執行完成任務的程式碼。我們可用 Python 實作取得當前時間的程式，並從回應訊息中擷取函式名稱與參數，取得最終結果。

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
  
      # 第二次 API 呼叫：從模型獲取最終回應
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

函式呼叫是大部分（若非全部）代理工具使用設計的核心，但自行實作時可能會遇到挑戰。
正如我們在 [課程 2](../../../02-explore-agentic-frameworks) 中學到的，代理框架為我們提供預建的構建方塊來實作工具使用。

## 使用代理框架實作工具使用範例

以下是使用不同代理框架實作工具使用設計模式的範例：

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> 是一個針對 .NET、Python 和 Java 開發者處理大型語言模型（LLM）的開源 AI 框架。它透過「<a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">序列化</a>」自動描述您的函式及其參數給模型，簡化函式呼叫使用流程。它也處理模型與程式碼之間的互動。使用像 Semantic Kernel 這類代理框架的另一個優點是，可以用預建工具，如<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">檔案搜尋</a>和<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">程式碼解譯器</a>。

下圖展示了使用 Semantic Kernel 進行函式呼叫的流程：

![function calling](../../../translated_images/zh-MO/functioncalling-diagram.a84006fc287f6014.webp)

在 Semantic Kernel 中，函式／工具稱為<a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">插件</a>。我們可以將之前看到的 `get_current_time` 函式轉成插件，把它封裝成一個類別並包含該函式。同時可引入 `kernel_function` 裝飾器，帶入函式描述。建立包含 GetCurrentTimePlugin 的 kernel 時，kernel 會自動序列化函式及參數，在此過程中產生傳送給 LLM 的結構描述。

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

# 建立插件
get_current_time_plugin = GetCurrentTimePlugin(location)

# 將插件加入核心
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> 是較新的代理框架，旨在讓開發者能安全地建構、部署及擴展高品質、可擴充的 AI 代理，而無需管理基礎運算與存儲資源。它特別適合企業應用，因為它是全方位管理的服務，具企業級安全性。

與直接使用 LLM API 開發相比，Azure AI Agent Service 有以下優勢：

- 自動工具呼叫 —— 無需自行解析工具呼叫、調用工具及處理回應，這些皆由伺服器端完成
- 安全管理資料 —— 可依賴「對話串（threads）」儲存所有所需資訊，無需自己管理對話狀態
- 開箱即用的工具 —— 可用於與資料來源互動，例如 Bing、Azure AI Search 和 Azure Functions 等工具。

Azure AI Agent Service 中的工具可分兩類：

1. 知識工具：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">以 Bing 搜尋提供基礎資料</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">檔案搜尋</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI 搜尋</a>

2. 動作工具：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">函式呼叫</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">程式碼解譯器</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI 定義工具</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service 讓我們能將這些工具組合成一個 `toolset`。它也使用 `threads` 來追蹤特定對話的訊息歷史。

假設您是 Contoso 公司的銷售代理，想打造一個能回答銷售資料問題的對話型代理。

下圖說明如何使用 Azure AI Agent Service 分析您的銷售資料：

![Agentic Service In Action](../../../translated_images/zh-MO/agent-service-in-action.34fb465c9a84659e.webp)

想要用這些工具配合服務，我們可以建立客戶端並定義工具或工具組。以下 Python 程式碼示範實作。LLM 能檢視工具組，並根據用戶請求決定使用用戶自建的函式 `fetch_sales_data_using_sqlite_query`，或是預建的程式碼解譯器。

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query 函數，可在 fetch_sales_data_functions.py 檔案中找到。
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# 初始化工具組
toolset = ToolSet()

# 使用 fetch_sales_data_using_sqlite_query 函數初始化函數調用代理，並將其加入工具組
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# 初始化程式碼解譯器工具並加入工具組。
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## 使用工具使用設計模式建構值得信賴 AI 代理的特別考量？

對 LLM 動態生成的 SQL 一般關注安全風險，特別是 SQL 注入或惡意操作（如刪除或竄改資料庫）的風險。雖然風險存在，但可透過適當配置資料庫存取權限有效降低。大部分資料庫可設為唯讀。像 PostgreSQL 或 Azure SQL 這類資料庫服務，應將應用程式授權為唯讀（SELECT）角色。

在安全環境中執行應用程式更能加強保護。在企業場景中，資料通常是從營運系統擷取並轉換至唯讀資料庫或資料倉儲，且採用易用的結構描述。此方法可確保資料安全，優化效能和可及性，且應用程式只有受限的唯讀存取。

## 程式碼範例
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## 對工具使用設計模式有更多疑問？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，與其他學習者交流，參加開放時間，並獲得你的 AI Agents 問題解答。

## 其他資源

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service 工作坊</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer 多代理工作坊</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel 函數呼叫教學</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel 代碼解釋器</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen 工具</a>

## 上一課

[理解代理設計模式](../03-agentic-design-patterns/README.md)

## 下一課

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：
本文件乃使用人工智能翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 所翻譯。儘管我們致力於確保準確性，但請注意，自動翻譯可能包含錯誤或不準確之處。原始語言文件應被視為權威來源。對於重要資訊，建議採用專業人工翻譯。本公司不對因使用本翻譯而引起的任何誤解或誤釋承擔責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->