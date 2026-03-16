[![探索 AI 代理框架](../../../translated_images/zh-HK/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(點擊上方圖片觀看本課程影片)_

# 探索 AI 代理框架

AI 代理框架是為簡化 AI 代理的創建、部署與管理而設計的軟件平台。這些框架為開發人員提供預建的元件、抽象層和工具，幫助簡化複雜 AI 系統的開發。

這些框架協助開發人員聚焦於應用的獨特部分，並提供解決 AI 代理開發中常見挑戰的標準化方法。它們提升 AI 系統建置的可擴展性、可及性和效率。

## 介紹

本課將涵蓋：

- AI 代理框架是什麼？它們能讓開發人員達成什麼目標？
- 團隊如何利用這些框架快速建立原型、反覆迭代並提升代理的能力？
- 微軟的 <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>、<a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> 和 <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> 框架與工具有何異同？
- 我可以直接整合現有的 Azure 生態系工具嗎？還是需要獨立方案？
- 什麼是 Azure AI Agents 服務？它如何幫助我？

## 學習目標

本課的目標是幫助你理解：

- AI 代理框架在 AI 開發中的角色。
- 如何利用 AI 代理框架建構智能代理。
- AI 代理框架所啟用的關鍵能力。
- AutoGen、Semantic Kernel 和 Azure AI Agent Service 之間的差異。

## 什麼是 AI 代理框架？它們讓開發者能做什麼？

傳統 AI 框架可協助你將 AI 整合進應用程式，並提升應用的以下方面：

- **個人化**：AI 可分析使用者行為和偏好，提供個人化推薦、內容和體驗。  
  例子：Netflix 等串流服務會根據觀影紀錄使用 AI 推薦電影和節目，提升用戶參與度與滿意度。

- **自動化與效率**：AI 可自動執行重複性任務、優化流程並提升營運效率。  
  例子：客服應用用 AI 驅動的聊天機器人處理常見詢問，縮短回應時間並讓人工作客服專注於較複雜問題。

- **提升使用者體驗**：AI 可提供語音識別、自然語言處理與預測文字等智能功能，提升整體用戶體驗。  
  例子：Siri 和 Google Assistant 等虛擬助理利用 AI 理解並回應語音指令，使使用裝置更方便。

### 聽起來都很好，為什麼我們還需要 AI 代理框架？

AI 代理框架不僅僅是一般的 AI 框架。它們旨在創建能與使用者、其他代理及環境互動，以達成特定目標的智能代理。這些代理可展現自主行為、做決策並適應變化條件。讓我們來看 AI 代理框架啟用的一些關鍵能力：

- **代理協作與協調**：支援創建多個能協同工作、溝通與協調以解決複雜任務的 AI 代理。
- **任務自動化與管理**：提供自動化多步工作流程、任務委派與代理間動態任務管理的機制。
- **情境理解與適應**：賦予代理理解情境、適應變化環境並基於即時資訊做決策的能力。

總結來說，代理讓你能做到更多、更進一步自動化，建構更智能化系統，能從環境中學習與適應。

## 如何快速建立原型、反覆迭代並提升代理能力？

這領域快速發展，但大多數 AI 代理框架有一些共通點能幫助你快速原型與迭代，包含模組元件、協作工具及即時學習。讓我們深入了解：

- **使用模組元件**：AI SDK 提供預先構建的元件，如 AI 與記憶連接器、使用自然語言或程式碼外掛的函式調用、提示模板等。
- **善用協作工具**：設計具特定角色與任務的代理，使其能測試和改良協同工作流程。
- **即時學習**：實作反饋迴圈，讓代理從互動中學習並動態調整行為。

### 使用模組元件

像 Microsoft Semantic Kernel 和 LangChain 這類 SDK 提供預建元件，如 AI 連接器、提示模板與記憶管理。

**團隊如何使用這些元件**：團隊可快速組裝這些元件，建立功能性原型，省去從零開始的時間，促進快速實驗與迭代。

**實際作法**：你可以用預建的解析器從使用者輸入中擷取資訊，使用記憶模組存取資料，及用提示產生器與使用者互動，全無須自己建立這些元件。

**範例程式碼**。以下展示如何使用 Semantic Kernel Python 和 .Net 版的預建 AI 連接器，利用自動函式調用讓模型回應使用者輸入：

``` python
# Semantic Kernel Python 範例

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# 定義一個 ChatHistory 物件以儲存對話的上下文
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# 定義一個範例插件，內含用於預訂旅程的函數
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# 建立 Kernel
kernel = Kernel()

# 將範例插件新增到 Kernel 物件
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# 定義 Azure OpenAI AI 連接器
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# 定義請求設定以配置模型並啟用自動函數呼叫
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # 針對給定的聊天歷史和請求設定向模型發出請求
    # Kernel 包含模型會請求調用的範例
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
    # 示例 AI 模型回應: `你已成功預訂 2025 年 1 月 1 日飛往紐約的航班。祝旅途平安！✈️🗽`

    # 將模型的回應新增到我們的聊天歷史上下文中
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
  
這個範例展示如何利用預建解析器從使用者輸入擷取關鍵資訊，如航班訂票的起點、目的地與日期。此模組化方法讓你能專注於高階邏輯。

### 利用協作工具

像 CrewAI、Microsoft AutoGen 和 Semantic Kernel 的框架，方便創建多代理系統共同協作。

**團隊如何運用**：設計具特定角色及任務的代理，讓他們能測試、優化協作流程，提升整體系統效率。

**實際案例**：你可以建立一組代理團隊，每個代理專司資料擷取、分析或決策等功能。代理間可溝通分享資訊，共同完成使用者查詢或任務。

**範例程式碼 (AutoGen)**：

```python
# 建立代理人，然後建立一個輪流排程讓它們協同工作，在這個例子中按順序

# 資料擷取代理人
# 資料分析代理人
# 決策代理人

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

# 當使用者說「APPROVE」時，對話結束
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# 在腳本中執行時使用 asyncio.run(...)
await Console(stream)
```
  
上例展示如何創建需多個代理協同分析資料的任務。每個代理執行專門功能，系統透過協調代理實作該任務。專責代理讓任務更有效率與表現更佳。

### 即時學習

進階框架提供即時情境理解與適應的能力。

**團隊如何應用**：實作讓代理從互動中學習、動態調整行為的反饋迴圈，以持續提升與優化能力。

**實際應用**：代理會分析使用者回饋、環境數據及任務結果，更新知識庫、調整決策演算法，並隨時間提升表現。透過持續學習，代理能適應變化環境與使用者偏好，增強系統整體效能。

## AutoGen、Semantic Kernel 和 Azure AI Agent Service 三者有何差異？

框架比較有多種方式，這裡聚焦其設計、能力和目標用例上的關鍵差異：

## AutoGen

AutoGen 是微軟研究院 AI Frontiers Lab 開發的開源框架。它專注於事件驅動的分散式 *Agentic* 應用，支持多個大型語言模型（LLMs）和小型語言模型（SLMs）、工具及先進的多代理設計模式。

AutoGen 核心圍繞代理的概念，代理為自主實體，能感知環境，做決策並行動以達成特定目標。代理透過非同步訊息溝通，使其能獨立並行工作，提升系統擴展性及響應速度。

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">代理基於演員模型 (actor model)</a>。維基百科指出，演員是 _並行計算的基本構建單元。針對收到的訊息，演員可做出本地決策、建立更多演員、傳送訊息，並決定如何回應下一個訊息_。

**應用場景**：自動化程式碼生成、資料分析任務及建構自訂規劃和研究用代理。

AutoGen 的核心概念：

- **代理**。代理是一個軟件實體，具有：
  - **透過訊息溝通**，訊息可同步或非同步。
  - **維護自身狀態**，並可透過訊息修改狀態。
  - **根據接收訊息或狀態變化執行行為**，這些行為可能修改代理狀態並產生外部效果，如更新訊息日誌、傳送新訊息、執行程式碼或呼叫 API。
    
  以下是一段建立具聊天功能代理的簡短程式碼範例：

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
    
    上述程式碼中，`MyAgent` 繼承自 `RoutedAgent`。它的訊息處理器會輸出訊息內容，然後用 `AssistantAgent` 委派發送回應。特別注意 `self._delegate` 被設定為 `AssistantAgent` 實例，這是預建用來處理聊天完成的代理。

    
    接著讓 AutoGen 註冊這代理類型並啟動程式：

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # 在背景開始處理訊息。
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    先前程式碼中，代理被註冊至執行環境，接著發送訊息給代理，產生以下輸出：

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **多代理系統**。AutoGen 支援多個代理協同完成複雜任務。代理間可溝通、共享資訊及協調行動，更高效解決問題。你可以定義具不同專長與角色的代理，例如資料檢索、分析、決策及使用者互動。以下看一個實例：

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # 示範如何宣告一個 Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # 使用 topic 類型作為 agent 的類型。
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # 為簡潔起見，其他宣告已被縮短

    # 群組聊天
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

    在上方程式碼中，一個 `GroupChatManager` 被註冊至執行環境。該管理者負責協調寫手、插畫師、編輯及使用者等不同類型代理間的互動。

- **代理執行環境**。框架提供執行環境，促進代理之間溝通，管理身分與生命週期，並實施安全及隱私邊界。這可確保代理安全高效互動。兩種主要執行環境：
  - **單一執行環境**。適合單程序應用，所有代理以相同程式語言實作且執行於同一程序。下圖示意運作方式：
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">單一執行環境</a>   
應用堆疊

    *代理透過執行環境以訊息溝通，執行環境管理代理生命週期*

  - **分散式代理執行環境**，適合多程序應用，代理可使用不同語言實作並部署於不同機器。下圖示意運作方式：
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">分散式執行環境</a>

## Semantic Kernel + 代理框架

Semantic Kernel 是企業級 AI 編排 SDK。它包含 AI 與記憶連接器，並配有代理框架。

先介紹幾個核心元件：

- **AI 連接器**：這是介接外部 AI 服務與資料源的介面，適用於 Python 和 C#。

  ```python
  # 語意核心 Python
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

    範例示範如何建立 kernel 並加入聊天完成服務。Semantic Kernel 與外部 AI 服務連線，如此處的 Azure OpenAI 聊天完成。

- **外掛**：將應用可用的函式封裝起來。有現成外掛，也可自訂。相關概念為「提示函式」。不只是以自然語言提示調用函式，而是向模型廣播特定函式，模型會依當前對話上下文選擇呼叫這些函式完成請求。範例如下：

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

    此處先有一個提示模板 `skPrompt`，留出 `$userInput` 讓使用者輸入文字。接著建立 kernel 函式 `SummarizeText`，並以 `SemanticFunctions` 外掛名匯入 kernel。注意函式名稱助 Semantic Kernel 理解函式功能與呼叫時機。

- **本地函式**：框架也能直接調用本地函式執行任務。以下為從檔案讀取內容的示例：

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

- **記憶**：抽象化並簡化 AI 應用的上下文管理。記憶即為 LLM 需「知道」的資訊。你可以將這些資料存於向量庫，最終可能是記憶體內資料庫或向量資料庫等。以下為非常簡化情境示例，將「事實」加入記憶：

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

這些事實然後被儲存在記憶集合 `SummarizedAzureDocs`。這是一個非常簡化的範例，但你可以看到如何將資訊儲存在記憶中，供 LLM 使用。

以上就是 Semantic Kernel 框架的基礎，那代理框架呢？

## Azure AI 代理服務

Azure AI 代理服務是較新的新增功能，於 Microsoft Ignite 2024 發佈。它允許開發和部署更靈活模型的 AI 代理，例如直接呼叫開源 LLMs 如 Llama 3、Mistral 和 Cohere。

Azure AI 代理服務提供更強的企業安全機制和資料儲存方法，使其適合企業應用。

它可即時與多代理協調框架如 AutoGen 和 Semantic Kernel 配合使用。

此服務目前處於公開預覽階段，並支援使用 Python 和 C# 建立代理。

使用 Semantic Kernel Python，我們可以創建具有用戶定義插件的 Azure AI 代理：

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# 為範例定義一個插件
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
        # 建立代理定義
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # 使用已定義的客戶端與代理定義建立 AzureAI 代理
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # 建立一個執行緒以儲存對話
        # 如果沒有提供執行緒，將會
        # 被建立並與初始回應一併返回
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
                # 為指定的執行緒呼叫代理
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

### 核心概念

Azure AI 代理服務具有以下核心概念：

- **代理 (Agent)**。Azure AI 代理服務整合了 Microsoft Foundry。在 AI Foundry 中，AI 代理作為一個「智慧」微服務，可用於回答問題（RAG）、執行操作或完全自動化工作流程。它透過結合生成式 AI 模型的能力和允許訪問及互動現實世界資料來源的工具來實現。以下是代理的範例：

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    在此範例中，代理使用模型 `gpt-4o-mini`，名稱為 `my-agent`，並附加指令 `You are helpful agent`。代理配備工具和資源以執行程式碼解釋任務。

- **主題與訊息 (Thread and messages)**。主題是另一個重要概念。它代表代理與使用者間的對話或互動。主題可用於追蹤對話進度、儲存上下文資訊和管理互動狀態。以下是主題的範例：

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

    在之前的程式碼中，建立了一個主題。之後，發送訊息到主題。透過呼叫 `create_and_process_run`，代理被要求在該主題上執行工作。最后，擷取訊息並記錄以查看代理的回應。這些訊息顯示使用者與代理間對話的進展。同時重要的是理解訊息可能是不同類型，如文字、圖片或檔案，代表代理的工作結果可能是一張圖片或一段文字回應。作為開發者，您可以利用這些資訊進一步處理回應或呈現給使用者。

- **整合其他 AI 框架**。Azure AI 代理服務可與其他框架如 AutoGen 和 Semantic Kernel 互動，意味著您可以在這些框架中構建應用部分，並例如使用代理服務作為協調者，或者您也可以完全在代理服務中建立您的應用。

**使用案例**：Azure AI 代理服務為需要安全、可擴展和靈活 AI 代理部署的企業應用設計。

## 這些框架有什麼差別？

看起來這些框架確實有很多重疊，但在設計、能力與目標使用案例上有一些關鍵差異：

- **AutoGen**：是一個集中於多代理系統前沿研究的實驗框架。非常適合用來實驗和原型設計複雜的多代理系統。
- **Semantic Kernel**：是可用於生產環境的代理函式庫，用於構建企業級代理應用。著重事件驅動、分散式代理應用，支援多種 LLM 和 SLM，工具，以及單一/多代理設計模式。
- **Azure AI 代理服務**：是 Azure Foundry 中的代理平台與部署服務。提供連接 Azure Foundry 支援的服務，如 Azure OpenAI、Azure AI 搜尋、Bing 搜尋及代碼執行。

還是不確定選哪個？

### 使用案例

讓我們看看常見使用情境，或許有助選擇：

> 問：我正在實驗、學習並構建概念驗證代理應用，希望能快速建立和測試。
>

> 答：AutoGen 是此情境的好選擇，因其聚焦於事件驅動、分散式代理應用，並支援先進的多代理設計模式。

> 問：為什麼 AutoGen 比 Semantic Kernel 和 Azure AI 代理服務更適合這個用例？
>
> 答：AutoGen 專門設計為事件驅動、分散式代理應用，非常適合自動化代碼生成和資料分析任務。它提供構建複雜多代理系統的必要工具和能力。

> 問：聽起來 Azure AI 代理服務也能使用嗎？它有代碼生成和更多工具？
>
> 答：是的，Azure AI 代理服務是一個代理平台服務，內建多模型、Azure AI 搜尋、Bing 搜尋和 Azure Functions 功能。讓您可以輕鬆在 Foundry 入口網站建立代理並大規模部署。

> 問：我還是困惑，給我一個選擇吧
>
> 答：推薦先使用 Semantic Kernel 建構您的應用，再利用 Azure AI 代理服務部署代理。這種方法讓你輕鬆持久化代理，同時善用 Semantic Kernel 的多代理系統構建能力。此外，Semantic Kernel 在 AutoGen 中也有連接器，使兩框架輕易配合使用。

我們用表格總結各框架的主要差異：

| 框架 | 專注領域 | 核心概念 | 使用案例 |
| --- | --- | --- | --- |
| AutoGen | 事件驅動、分散式代理應用 | 代理、角色、函式、資料 | 代碼生成、資料分析任務 |
| Semantic Kernel | 理解與生成類人語言內容 | 代理、模組組件、協作 | 自然語言理解、內容生成 |
| Azure AI 代理服務 | 靈活模型、企業安全、代碼生成、工具呼叫 | 模組化、協作、流程編排 | 安全、可擴展且靈活的 AI 代理部署 |

各框架的理想使用案例是什麼？

## 我可以直接整合現有的 Azure 生態系統工具嗎？還是必須使用獨立方案？

答案是可以，尤其是 Azure AI 代理服務，因為它設計時已確保與其他 Azure 服務無縫對接。例如，你可以整合 Bing、Azure AI 搜尋和 Azure Functions。它亦與 Microsoft Foundry 深度整合。

至於 AutoGen 和 Semantic Kernel，您也可整合 Azure 服務，但可能須在程式碼中呼叫這些服務。另一種整合方式是使用 Azure SDK 直接從代理與 Azure 服務互動。此外，如前所述，您也可以用 Azure AI 代理服務作為 AutoGen 或 Semantic Kernel 代理的協調者，輕鬆存取 Azure 生態系。

## 範例程式碼

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## 有更多關於 AI 代理框架的問題嗎？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，與其他學習者交流，參加答疑時間，解答你的 AI 代理相關問題。

## 參考資料

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure 代理服務</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel 和 AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python 代理框架</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net 代理框架</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI 代理服務</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">使用 Azure AI 代理服務與 AutoGen / Semantic Kernel 建立多代理解決方案</a>

## 前一課程

[AI 代理與代理使用案例導論](../01-intro-to-ai-agents/README.md)

## 下一課程

[理解代理設計模式](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件是透過人工智能翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 翻譯而成。雖然我們致力於確保準確性，但請注意自動翻譯可能包含錯誤或不準確之處。原始文件的母語版本應被視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們概不就使用本翻譯所引致的任何誤解或誤譯負責。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->