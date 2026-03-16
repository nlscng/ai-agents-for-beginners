[![探索 AI 代理框架](../../../translated_images/zh-MO/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(按上方圖像以觀看本課程的影片)_

# 探索 AI 代理框架

AI 代理框架是為了簡化建立、部署與管理 AI 代理而設計的軟體平台。這些框架提供預先構建的元件、抽象層和工具，能夠簡化複雜 AI 系統的開發流程。

這些框架透過為 AI 代理開發中的常見挑戰提供標準化的方法，幫助開發者專注於其應用的獨特面向。它們提升了建立 AI 系統時的可擴展性、可及性與效率。

## 介紹

本課程將涵蓋：

- 何謂 AI 代理框架，以及它們能讓開發人員達成什麼目標？
- 團隊如何使用這些框架快速原型、反覆改良並提升代理的能力？
- 由 Microsoft 所推出的 <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>、<a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>，以及 <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> 這些框架與工具之間有何差異？
- 我可以直接整合現有的 Azure 生態系工具，還是需要獨立的解決方案？
- 甚麼是 Azure AI Agents 服務，以及它如何幫助我？

## 學習目標

本課程的目標是幫助您理解：

- AI 代理框架在 AI 開發中的角色。
- 如何利用 AI 代理框架來構建智慧代理。
- AI 代理框架所啟用的關鍵能力。
- AutoGen、Semantic Kernel 與 Azure AI Agent Service 之間的差異。

## 何謂 AI 代理框架，以及它們讓開發人員能做些什麼？

傳統的 AI 框架可以幫助您將 AI 整合到應用程式中，並透過以下方式改善這些應用程式：

- **個性化**：AI 可以分析使用者行為與偏好，提供個人化的推薦、內容與體驗。
範例：像 Netflix 這類串流服務會使用 AI 根據觀看歷史推薦電影與節目，提升使用者參與度與滿意度。
- **自動化與效率**：AI 能自動化重複性任務、簡化工作流程並提升營運效率。
範例：客服應用使用 AI 驅動的聊天機器人處理常見詢問，減少回應時間並讓人工客服能處理更複雜的問題。
- **強化使用者體驗**：AI 能透過語音辨識、自然語言處理與預測文字等智慧功能改善整體使用者體驗。
範例：像 Siri 與 Google Assistant 的虛擬助理使用 AI 理解並回應語音指令，使用戶更容易與裝置互動。

### 聽起來都很棒，那為什麼我們還需要 AI 代理框架？

AI 代理框架代表的不僅僅是一般的 AI 框架。它們旨在促成可與使用者、其他代理及環境互動以達成特定目標的智慧代理。這些代理能展現自主行為、做出決策，並適應變化的條件。讓我們來看一些 AI 代理框架所啟用的主要能力：

- **代理協作與協調**：使得可建立多個能一起工作、互相溝通並協調以解決複雜任務的 AI 代理。
- **任務自動化與管理**：提供自動化多步驟工作流程、任務委派以及代理之間動態任務管理的機制。
- **情境理解與適應**：為代理配備理解情境、適應變化環境並根據即時資訊做出決策的能力。

總而言之，代理讓您能做更多事，把自動化提升到新的層次，創造能從環境中適應與學習的更智慧系統。

## 如何快速原型、反覆改良與提升代理的能力？

這是一個快速演進的領域，但大多數 AI 代理框架中有一些共通的東西可以幫助您快速原型與反覆改良，主要是模組化元件、協作工具與即時學習。讓我們深入看看這些：

- **使用模組化元件**：AI SDK 提供預建元件，例如 AI 與記憶體連接器、以自然語言或程式碼插件進行的函式呼叫、提示模板等。
- **利用協作工具**：設計具有特定角色與任務的代理，使其能測試並精煉協作工作流程。
- **即時學習**：實作回饋迴路，使代理從互動中學習並動態調整其行為。

### 使用模組化元件

像 Microsoft Semantic Kernel 與 LangChain 等 SDK 提供預建元件，例如 AI 連接器、提示模板與記憶體管理。

如何讓團隊使用這些：團隊可以快速組裝這些元件來建立功能性原型，而不需從零開始，從而允許快速實驗與反覆改良。

實際運作方式：您可以使用預建的解析器從使用者輸入中擷取資訊、使用記憶模組儲存與檢索資料，並使用提示產生器與使用者互動，全部不需自行建立這些元件。

範例程式碼。讓我們看看如何使用具有自動函式呼叫功能的預建 AI Connector，分別在 Semantic Kernel Python 與 .Net 中讓模型回應使用者輸入的範例：

``` python
# 語義核心 Python 範例

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# 定義一個 ChatHistory 物件以保存對話的上下文
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# 定義一個包含預訂旅遊功能的範例插件
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# 建立核心
kernel = Kernel()

# 將範例插件加入核心物件
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# 定義 Azure OpenAI AI 連接器
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# 定義請求設定以使用自動函數調用配置模型
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # 對模型發送請求，使用指定的對話歷史和請求設定
    # 核心包含模型將請求調用的範例
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
    # 範例 AI 模型回應：`您 2025 年 1 月 1 日飛往紐約的航班已成功預訂。旅途愉快！✈️🗽`

    # 將模型的回應加入我們的對話歷史上下文
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

從這個範例您可以看到如何利用預建解析器從使用者輸入中擷取關鍵資訊，例如航班預訂請求的出發地、目的地與日期。這種模組化的方法讓您能專注於高階邏輯。

### 利用協作工具

像 CrewAI、Microsoft AutoGen 與 Semantic Kernel 這類框架促進建立多個能協同工作的代理。

如何讓團隊使用這些：團隊可以設計具有特定角色與任務的代理，使其能測試並精煉協作工作流程並提升整體系統效率。

實際運作方式：您可以建立一個代理團隊，每個代理具有專門功能，例如資料擷取、分析或決策。這些代理可以互相溝通與分享資訊，以達成共同目標，例如回應使用者查詢或完成任務。

範例程式碼（AutoGen）：

```python
# 建立代理，然後建立一個輪流排程讓他們可以一起工作，在這個案例中是依順序進行

# 數據檢索代理
# 數據分析代理
# 決策代理

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

# 當用戶說「批准」時對話結束
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# 在腳本中運行時使用 asyncio.run(...)。
await Console(stream)
```

在前面的程式碼中，您可以看到如何建立一個涉及多個代理協同分析資料的任務。每個代理執行特定功能，任務透過協調代理來達成預期結果。透過建立具專門角色的專屬代理，您能提升任務效率與效能。

### 即時學習

進階框架提供即時情境理解與適應的能力。

如何讓團隊使用這些：團隊可以實作回饋迴路，使代理從互動中學習並動態調整其行為，進而持續改進與精煉能力。

實際運作方式：代理可以分析使用者反饋、環境資料與任務結果，來更新其知識庫、調整決策演算法，並隨時間提升效能。這種反覆學習流程使代理能適應變化的條件與使用者偏好，增強整體系統效能。

## AutoGen、Semantic Kernel 與 Azure AI Agent Service 之間有何差異？

有很多方式可以比較這些框架，但讓我們從其設計、功能與目標使用案例的角度看一些關鍵差異：

## AutoGen

AutoGen 是由 Microsoft Research 的 AI Frontiers Lab 開發的開源框架。它專注於事件驅動、分散式的代理化（agentic）應用，支援多個 LLM 與 SLM、工具及先進的多代理設計模式。

AutoGen 是以代理為核心概念所構建，代理是能感知環境、做出決策並採取行動以達成特定目標的自主實體。代理透過非同步訊息進行溝通，允許它們獨立且並行地工作，提升系統可擴展性與回應性。

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">代理是基於演員模型</a>。根據 Wikipedia，演員是「並行計算的基本建構塊。作為對所接收訊息的回應，演員可以：做本地決策、創建更多演員、發送更多訊息，並決定如何回應下一個接收到的訊息」。

**使用案例**：自動化程式碼生成、資料分析任務，以及為規劃與研究功能建立自訂代理。

以下是 AutoGen 的一些重要核心概念：

- **代理**。代理是一種軟體實體，會：
  - **透過訊息溝通**，這些訊息可以是同步或非同步的。
  - **維護自身狀態**，該狀態可由進來的訊息修改。
  - **執行動作**以回應接收到的訊息或狀態變更。這些動作可能修改代理的狀態並產生外部效果，例如更新訊息日誌、發送新訊息、執行程式碼或呼叫 API。
    
  這裡有一段簡短的程式碼片段，示範如何建立具備聊天功能的自訂代理：

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
    
    在先前的程式碼中，`MyAgent` 已被建立並繼承自 `RoutedAgent`。它有一個訊息處理器會列印訊息內容，然後使用 `AssistantAgent` 委派來發送回應。特別注意我們如何將 `self._delegate` 指派為 `AssistantAgent` 的實例，該實例是一個可處理聊天完成的預建代理。


    接著讓 AutoGen 知道此代理類型並啟動程式：

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # 在背景中開始處理訊息。
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    在先前的程式碼中，代理已向執行環境註冊，然後向代理發送訊息，導致下列輸出結果：

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **多代理**。AutoGen 支援建立多個可協同工作的代理以完成複雜任務。代理可以溝通、分享資訊並協調其動作以更有效地解決問題。要建立多代理系統，您可以定義具有專門功能與角色的不同類型代理，例如資料擷取、分析、決策與使用者互動。讓我們看一下這樣的建立流程，來理解其運作方式：

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # 宣告一個代理人的例子
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # 使用主題類型作為代理人類型。
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # 其餘聲明為簡潔起見縮短

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

    在先前的程式碼中，我們有一個已向執行環境註冊的 `GroupChatManager`。該管理者負責協調不同類型代理之間的互動，例如撰稿者、插畫家、編輯和使用者。

- **代理執行環境**。該框架提供一個執行環境，能促進代理之間的通訊，管理它們的身分與生命週期，並強制執行安全與隱私邊界。這表示您可以在安全且受控的環境中執行代理，確保它們能安全且有效地互動。有兩種類型的執行環境值得注意：
  - **單機執行環境**。這對於所有代理都在同一程式語言並在同一處理程序中實作的單程序應用程式是一個不錯的選擇。以下示意其如何運作：
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">單機執行環境</a>   
應用程式堆疊

    *agents communicate via messages through the runtime, and the runtime manages the lifecycle of agents*

  - **分散式代理執行環境**，適用於代理可能以不同程式語言實作並在不同主機上執行的多程序應用程式。以下示意其如何運作：
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">分散式執行環境</a>

## Semantic Kernel + 代理框架

Semantic Kernel 是一個適用於企業的 AI 協調 SDK。它包含 AI 與記憶體連接器，以及一個代理框架。

讓我們先介紹一些核心元件：

- **AI 連接器**：這是一個用於在 Python 與 C# 中連接外部 AI 服務與資料來源的介面。

  ```python
  # 語義核心 Python
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

    這裡有一個簡單的範例，示範如何建立一個 kernel 並加入聊天完成服務。Semantic Kernel 與外部 AI 服務建立連線，在此案例中為 Azure OpenAI Chat Completion。

- **外掛（Plugins）**：這些封裝了應用程式可使用的函式。既有現成的外掛，也可建立自訂外掛。相關概念為「提示函式（prompt functions）」。與其為函式呼叫提供自然語言提示，不如向模型廣播某些函式。根據當前聊天情境，模型可能選擇呼叫這些函式之一以完成請求或查詢。以下是一個範例：

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

    在此，您首先有一個模板提示 `skPrompt`，留出使用者輸入文字 `$userInput` 的位置。接著您建立 kernel 函式 `SummarizeText`，然後以外掛名稱 `SemanticFunctions` 將其匯入到 kernel。請注意函式名稱有助於 Semantic Kernel 理解該函式的用途與何時應該被呼叫。

- **原生函式**：框架也有可以直接呼叫以執行任務的原生函式。以下是一個從檔案擷取內容的範例：

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

- **記憶體**：抽象化並簡化 AI 應用的情境管理。記憶體的概念是 LLM 應該知道的一些資訊。您可以將這些資訊儲存在向量庫中，該向量庫最終會成為記憶體資料庫（可為記憶體內資料庫或向量資料庫等）。以下是一個非常簡化的場景範例，展示如何將「事實」加入記憶體：

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

    這些事實然後被儲存在記憶集合 `SummarizedAzureDocs`。這是一個非常簡化的範例，但您可以看到如何將資訊儲存在記憶中供 LLM 使用。

So that's the basics of the Semantic Kernel framework, what about the Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service 是最近新增的服務，在 Microsoft Ignite 2024 發表。它允許使用更靈活的模型開發與部署 AI 代理，例如直接呼叫開源的 LLMs，如 Llama 3、Mistral 和 Cohere。

Azure AI Agent Service 提供更強的企業安全機制與資料儲存方法，適合企業應用。

它與像 AutoGen 和 Semantic Kernel 這類多代理協調框架開箱即用地相容。

此服務目前處於公開預覽階段，支援使用 Python 與 C# 來建構代理。

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# 定義一個範例插件作為範例
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

        # 使用定義的客戶端和代理定義來建立 AzureAI 代理
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # 建立一個線程以保存對話
        # 如果沒有提供線程，將會
        # 建立一個新線程並隨初始回應一同返回
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
                # 為指定的線程呼叫代理
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

Azure AI Agent Service 有以下幾個核心概念：

- **代理人**. Azure AI Agent Service 與 Microsoft Foundry 整合。在 AI Foundry 內，AI 代理扮演一個「智慧」微服務的角色，可用來回答問題（RAG）、執行動作，或完全自動化工作流程。它透過結合生成式 AI 模型的能力與允許存取與互動真實世界資料來源的工具來達成這些功能。這裡是一個代理的範例：

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    In this example, an agent is created with the model `gpt-4o-mini`, a name `my-agent`, and instructions `You are helpful agent`. The agent is equipped with tools and resources to perform code interpretation tasks.

- **執行緒與訊息**. 執行緒是另一個重要的概念。它代表代理與使用者之間的對話或互動。執行緒可用來追蹤對話進度、儲存上下文資訊，以及管理互動狀態。這裡是一個執行緒的範例：

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

    In the previous code, a thread is created. Thereafter, a message is sent to the thread. By calling `create_and_process_run`, the agent is asked to perform work on the thread. Finally, the messages are fetched and logged to see the agent's response. The messages indicate the progress of the conversation between the user and the agent. It's also important to understand that the messages can be of different types such as text, image, or file, that is the agents work has resulted in for example an image or a text response for example. As a developer, you can then use this information to further process the response or present it to the user.

- **整合其他 AI 框架**. Azure AI Agent Service 可以與 AutoGen 和 Semantic Kernel 等其他框架互動，這表示您可以在這些框架之一中構建應用的一部分，例如使用 Agent 服務作為協調者，或者直接在 Agent 服務中構建全部內容。

**使用情境**: Azure AI Agent Service 是為需要安全、可擴充與靈活 AI 代理部署的企業應用而設計。

## 這些框架之間有什麼差別？
 
聽起來這些框架之間確實有很多重疊，但在設計、能力與目標使用情境上有一些重要差異：
 
- **AutoGen**: 是一個以實驗為主的框架，重點在多代理系統的前沿研究。它是進行複雜多代理系統實驗與原型開發的最佳場所。
- **Semantic Kernel**: 是一個可投入生產的代理程式庫，用於構建企業級的代理應用。專注於事件驅動、分散式的代理應用，支援多個 LLM 與 SLM、工具，以及單代理/多代理設計模式。
- **Azure AI Agent Service**: 是在 Azure Foundry 中提供代理的平臺與部署服務。它提供與 Azure Foundry 所支援服務（如 Azure OpenAI、Azure AI Search、Bing Search 與程式碼執行）的連接能力。
 
還是不確定要選哪一個？

### 使用情境
 
讓我們透過一些常見的使用情境來幫助您：
 
> Q: 我正在實驗、學習並建立概念驗證的代理應用，我想能夠快速建構和試驗
>
>
>A: AutoGen 會是此情境的好選擇，因為它專注於事件驅動、分散式的代理應用，並支援進階的多代理設計模式。

> Q: 為什麼 AutoGen 比 Semantic Kernel 和 Azure AI Agent Service 更適合這個使用情境？
>
> A: AutoGen 是專為事件驅動、分散式的代理應用設計，使其非常適合自動化程式碼生成與資料分析任務。它提供必要的工具與功能來有效地建立複雜的多代理系統。

>Q: 聽起來 Azure AI Agent Service 也可行，它有用於程式碼生成等的工具嗎？
>
> 
> A: 是的，Azure AI Agent Service 是一個代理的平臺服務，並內建對多種模型、Azure AI Search、Bing Search 與 Azure Functions 的支援。它讓您能夠輕鬆在 Foundry 入口網站中建立代理並大規模部署。

> Q: 我還是搞不清楚，請只給我一個選項
>
> A: 很好的選擇是先在 Semantic Kernel 中構建您的應用，然後使用 Azure AI Agent Service 部署您的代理。此方法讓您能輕鬆持久化代理，同時利用在 Semantic Kernel 中構建多代理系統的能力。另外，Semantic Kernel 在 AutoGen 中也有連接器，使得兩個框架能輕鬆一起使用。
 
讓我們將主要差異總結在表格中：

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | 事件驅動、分散式代理應用 | 代理、角色、函數、資料 | 程式碼生成、資料分析任務 |
| Semantic Kernel | 理解與產生類人文本內容 | 代理、模組化元件、協作 | 自然語言理解、內容生成 |
| Azure AI Agent Service | 彈性模型、企業級安全、程式碼生成、工具呼叫 | 模組化、協作、流程編排 | 安全、可擴充且彈性的 AI 代理部署 |

What's the ideal use case for each of these frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

答案是可以，您可以直接將現有的 Azure 生態系工具整合到 Azure AI Agent Service，特別是因為它是為了與其他 Azure 服務無縫運作而建置。舉例來說，您可以整合 Bing、Azure AI Search 與 Azure Functions。它也與 Microsoft Foundry 有深度整合。

對於 AutoGen 與 Semantic Kernel，您也可以與 Azure 服務整合，但可能需要您在程式碼中呼叫 Azure 服務。另一種整合方式是使用 Azure SDK 從代理與 Azure 服務互動。此外，如前所述，您可以使用 Azure AI Agent Service 作為在 AutoGen 或 Semantic Kernel 中構建代理的協調者，從而更容易存取 Azure 生態系。

## 範例程式碼

- Python: [代理框架](./code_samples/02-python-agent-framework.ipynb)
- .NET: [代理框架](./code_samples/02-dotnet-agent-framework.md)

## 還有關於 AI 代理框架的更多問題嗎？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) 與其他學習者交流、參加辦公時間，並獲得您的 AI 代理問題解答。

## 參考資料

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure AI Agent 服務</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel 與 AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python 代理框架</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net 代理框架</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent 服務</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">使用 Azure AI Agent Service 與 AutoGen / Semantic Kernel 建構多代理解決方案</a>

## 前一課

[介紹 AI 代理與代理使用情境](../01-intro-to-ai-agents/README.md)

## 下一課

[理解代理設計模式](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免責聲明：
本文件已使用 AI 翻譯服務 [Co-op Translator]（https://github.com/Azure/co-op-translator）進行翻譯。雖然我們力求準確，但請注意自動翻譯可能包含錯誤或不準確之處。原始語言版本應視為權威來源。對於重要或關鍵資訊，建議採用專業人工翻譯。我們不對因使用本翻譯而引致的任何誤解或錯誤詮釋承擔任何責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->