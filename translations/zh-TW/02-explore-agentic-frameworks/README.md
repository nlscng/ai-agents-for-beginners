[![探索 AI 代理框架](../../../translated_images/zh-TW/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(點擊上方圖片以觀看此課程的影片)_

# 探索 AI 代理框架

AI 代理框架是用來簡化 AI 代理建立、部署與管理的軟體平台。這些框架為開發人員提供預建元件、抽象層與工具，幫助理順複雜 AI 系統的開發流程。

這些框架透過為 AI 代理開發中的常見挑戰提供標準化的方法，幫助開發人員專注於應用程式的獨特面向。它們提升了構建 AI 系統的可擴充性、可取得性與效率。

## 介紹 

本課程將涵蓋：

- 什麼是 AI 代理框架，以及它們能讓開發人員達成什麼？
- 團隊如何使用這些框架快速建立原型、迭代並改進代理的能力？
- 由 Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>、<a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> 與 <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> 所建立的框架與工具之間有何差異？
- 我可以直接整合我現有的 Azure 生態系工具，還是需要獨立解決方案？
- 什麼是 Azure AI Agents 服務，它如何幫助我？

## 學習目標

本課程的目標是幫助你了解：

- AI 代理框架在 AI 開發中的角色。
- 如何運用 AI 代理框架來構建智慧代理。
- AI 代理框架所啟用的主要能力。
- AutoGen、Semantic Kernel 與 Azure AI Agent Service 之間的差異。

## 什麼是 AI 代理框架，以及它們讓開發人員能做什麼？

傳統的 AI 框架可以幫助你將 AI 整合到應用程式中，並在下列方面使這些應用程式更優化：

- **個人化**: AI 可以分析使用者行為與偏好，提供客製化的推薦、內容與體驗。
Example: 影音串流服務如 Netflix 使用 AI 根據觀看歷史建議電影與節目，提升使用者的互動率與滿意度。
- **自動化與效率**: AI 可以自動化重複性工作、簡化工作流程並提升營運效率。
Example: 客服應用使用 AI 驅動的聊天機器人處理常見詢問，減少回應時間並釋放真人客服處理較複雜問題。
- **強化使用者體驗**: AI 可以透過語音辨識、自然語言處理與預測文字等智慧功能改善整體使用者體驗。
Example: 虛擬助理如 Siri 與 Google Assistant 使用 AI 來理解並回應語音指令，讓使用者更容易與裝置互動。

### 這一切聽起來很棒，為什麼我們還需要 AI 代理框架？

AI 代理框架不只是一般的 AI 框架。它們旨在啟用能與使用者、其他代理與環境互動以達成特定目標的智慧代理。這些代理可以展現自治行為、做出決策並適應變化的條件。讓我們來看看 AI 代理框架所啟用的一些關鍵能力：

- **代理協作與協調**: 允許建立多個可一起工作的 AI 代理，彼此溝通與協作以解決複雜任務。
- **任務自動化與管理**: 提供用於自動化多步驟工作流程、任務委派與代理之間動態任務管理的機制。
- **情境理解與適應**: 賦予代理理解情境、適應變化環境並根據即時資訊做出決策的能力。

總結來說，代理可以讓你做到更多，將自動化提升到下一個層次，創造出能從環境中適應與學習的更智慧系統。

## 如何快速原型、迭代與改進代理的能力？

這是一個變動迅速的領域，但在大多數 AI 代理框架中，有一些共通項目能幫助你快速建立原型與迭代，特別是模組元件、協作工具與即時學習。讓我們深入這些面向：

- **使用模組化元件**: AI SDK 提供預建元件，例如 AI 與記憶體連接器、使用自然語言或程式碼外掛的函式呼叫、提示模板等。
- **利用協作工具**: 設計具有特定角色與任務的代理，使它們能測試並優化協作工作流程。
- **即時學習**: 實作回饋循環，讓代理從互動中學習並動態調整其行為。

### 使用模組化元件

像 Microsoft Semantic Kernel 和 LangChain 這類的 SDK 提供預建元件，例如 AI 連接器、提示模板與記憶管理。

**團隊如何使用這些**: 團隊可以快速組裝這些元件以建立功能性原型，而無需從零開始，從而允許快速實驗與迭代。

**實作方式**: 你可以使用預建的解析器從使用者輸入中擷取資訊、使用記憶模組來儲存與檢索資料，並使用提示產生器與使用者互動，全部都不需自行重建這些元件。

**範例程式碼**. 讓我們看一下如何在 Semantic Kernel Python 與 .Net 中使用預建 AI Connector 的範例，該範例使用自動函式呼叫讓模型回應使用者輸入：

``` python
# 語意核心 Python 範例

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# 定義一個 ChatHistory 物件來保存對話的上下文
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

# 建立 Kernel
kernel = Kernel()

# 將範例插件新增至 Kernel 物件
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
    # 依給予的聊天歷史和請求設定向模型提出請求
    # Kernel 含有模型將請求調用的範例
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
    # 範例 AI 模型回應：`您於 2025 年 1 月 1 日飛往紐約的航班已成功預訂。祝旅途愉快！✈️🗽`

    # 將模型的回應新增至我們的聊天歷史上下文
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

從此範例你可以看到如何利用預建解析器從使用者輸入中擷取關鍵資訊，例如航班預訂請求的出發地、目的地與日期。這種模組化方法讓你可以專注於高階邏輯。

### 利用協作工具

像 CrewAI、Microsoft AutoGen 與 Semantic Kernel 這類框架促進建立可協同工作的多個代理。

**團隊如何使用這些**: 團隊可以設計具有特定角色與任務的代理，使它們能測試並優化協作式工作流程，並提升整體系統效率。

**實作方式**: 你可以建立一群代理，每個代理有專門職能，例如資料檢索、分析或決策。這些代理可以互相溝通並共享資訊以達成共同目標，例如回應使用者查詢或完成任務。

**範例程式碼（AutoGen）**：

```python
# 建立代理，然後建立一個輪流排程讓他們可以一起工作，在此情況下是依序進行

# 資料擷取代理
# 資料分析代理
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

# 當使用者說「APPROVE」時結束對話
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# 在執行腳本時使用 asyncio.run(...)。
await Console(stream)
```

在前面的程式碼中，你可以看到如何建立一個涉及多個代理共同協作分析資料的任務。每個代理執行特定功能，並透過協調代理的方式來執行任務以達成預期結果。透過建立具有專門角色的專注代理，你可以提升任務的效率與效能。

### 即時學習

先進的框架提供即時情境理解與適應能力。

**團隊如何使用這些**: 團隊可以實作回饋迴路，讓代理從互動中學習並動態調整其行為，進而持續改進與精進其能力。

**實作方式**: 代理可以分析使用者回饋、環境資料與任務結果，以更新其知識庫、調整決策演算法並隨時間提升效能。這種反覆的學習流程使代理能適應變化的條件與使用者偏好，增強整體系統效能。

## AutoGen、Semantic Kernel 與 Azure AI Agent Service 這些框架有何不同？

有很多比較方式，但我們先從設計、能力與目標使用案例的差異來看幾個要點：

## AutoGen

AutoGen 是由 Microsoft Research 的 AI Frontiers Lab 所開發的開源框架。它專注於事件驅動、分散式的「代理式」應用，支援多個 LLM 與 SLM、工具與進階的多代理設計模式。

AutoGen 的核心概念是代理（agents），代理是能感知其環境、做決策並採取行動以達成特定目標的自主實體。代理透過非同步訊息進行溝通，允許它們獨立且並行地工作，提升系統的可擴充性與回應性。

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">代理基於 actor model（演員模型）</a>。根據 Wikipedia，演員是 _並行計算的基本建構塊。在收到訊息後，演員可以：做出本地決策、建立更多演員、傳送更多訊息，並決定如何回應下一個收到的訊息_。

**使用案例**：自動化程式碼生成、資料分析任務，與為規劃與研究功能構建自訂代理。

以下是 AutoGen 的一些重要核心概念：

- **Agents（代理）**。代理是一種軟體實體，會：
  - **透過訊息進行溝通**，這些訊息可以是同步或非同步的。
  - **維護自己的狀態**，該狀態可被入站訊息修改。
  - **執行動作**以回應收到的訊息或狀態變更。這些動作可能會修改代理的狀態並產生外部效果，例如更新訊息記錄、傳送新訊息、執行程式碼或呼叫 API。
    
  下面有一個簡短的程式碼片段，展示如何建立具備聊天功能的自訂代理：

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
    
    在前面的程式碼中，`MyAgent` 已被建立並繼承自 `RoutedAgent`。它有一個訊息處理器會印出訊息內容，然後使用 `AssistantAgent` delegate 發送回應。特別要注意我們如何將 `self._delegate` 指派為 `AssistantAgent` 的實例，該實例是一個可處理聊天補完的預建代理。


    接著讓 AutoGen 知道這個代理類型並啟動程式：

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # 在背景中開始處理訊息。
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    在先前的程式碼中，代理已向執行環境註冊，然後向該代理發送一個訊息，結果產生以下輸出：

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **多代理**。AutoGen 支援建立多個代理共同協作以完成複雜任務。代理可以互相溝通、分享資訊並協調其動作以更有效地解決問題。要建立多代理系統，你可以定義具有專門功能與角色的不同代理類型，例如資料檢索、分析、決策與使用者互動。讓我們看看這類建立方式長什麼樣子，以便對其有一個概念：

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # 宣告一個代理人的範例
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

    # 其餘宣告為簡潔起見略寫

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

    在先前的程式碼中，我們有一個已在執行環境中註冊的 `GroupChatManager`。此管理者負責協調不同類型代理之間的互動，例如撰稿者、插畫家、編輯與使用者。

- **Agent Runtime（代理執行環境）**。該框架提供執行時環境，啟用代理之間的通訊、管理其身份與生命週期，並強制安全與隱私邊界。這意味著你可以在受控且安全的環境中執行代理，確保它們能安全且有效地互動。有兩種值得關注的執行環境：
  - **獨立執行環境（Stand-alone runtime）**。這是單一程序應用的良好選擇，所有代理都在相同的程式語言中實作並在相同的程序中執行。以下是一個運作示意：
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Stand-alone runtime</a>   
Application stack

    *agents communicate via messages through the runtime, and the runtime manages the lifecycle of agents*

  - **分散式代理執行環境（Distributed agent runtime）**，適用於多程序應用，其中代理可能以不同程式語言實作並在不同機器上執行。以下是一個運作示意：
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distributed runtime</a>

## Semantic Kernel + Agent Framework

Semantic Kernel 是一個企業級的 AI 編排 SDK。它包含 AI 與記憶體連接器，以及一個代理框架。

我們先來介紹一些核心元件：

- **AI Connectors（AI 連接器）**：這是在 Python 與 C# 中與外部 AI 服務和資料來源介接的介面。

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

    這裡有一個簡單範例，示範如何建立一個 kernel 並新增一個聊天補完服務。Semantic Kernel 與外部 AI 服務建立連接，在此例中為 Azure OpenAI Chat Completion。

- **Plugins（外掛）**：這些封裝了應用程式可以使用的函式。既有現成的外掛，也可以建立自訂外掛。相關概念是「提示函式」。你不是以自然語言提示去呼叫函式，而是將某些函式廣播給模型。根據當前聊天上下文，模型可能會選擇呼叫其中一個函式來完成請求或查詢。以下是一個範例：

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

    在這裡，你先有一個模板提示 `skPrompt`，它保留讓使用者輸入文字的空間 `$userInput`。接著你建立 kernel 函式 `SummarizeText`，然後以外掛名稱 `SemanticFunctions` 將它匯入到 kernel。請注意函式的名稱，這有助於 Semantic Kernel 理解該函式的用途以及何時應該被呼叫。

- **Native function（原生函式）**：框架也有可以直接被呼叫以執行任務的原生函式。以下是一個從檔案檢索內容的範例：

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

- **Memory（記憶體）**：為 AI 應用抽象化並簡化情境管理。記憶體的概念是指這些資訊是模型應該知道的內容。你可以將這些資訊儲存在向量資料庫中，該資料庫通常是記憶體中的資料庫或向量資料庫或類似的系統。以下是一個非常簡化的情境範例，將「事實」加入到記憶體中：

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

    這些事實接著會儲存在記憶集合 `SummarizedAzureDocs` 中。這是一個非常簡化的範例，但你可以看到如何將資訊儲存在記憶中供 LLM 使用。

So that's the basics of the Semantic Kernel framework, what about the Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service is a more recent addition, introduced at Microsoft Ignite 2024. It allows for the development and deployment of AI agents with more flexible models, such as directly calling open-source LLMs like Llama 3, Mistral, and Cohere.

Azure AI Agent Service provides stronger enterprise security mechanisms and data storage methods, making it suitable for enterprise applications. 

It works out-of-the-box with multi-agent orchestration frameworks like AutoGen and Semantic Kernel.

This service is currently in Public Preview and supports Python and C# for building agents.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# 定義一個範例插件作為示範
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

        # 使用已定義的用戶端和代理定義來建立 AzureAI 代理
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # 建立一個對話串以保存對話內容
        # 如果未提供對話串，
        # 將建立一個新的對話串並隨初始回應返回
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
                # 調用指定對話串的代理
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

### Core concepts

Azure AI Agent Service has the following core concepts:

- **Agent**. Azure AI Agent Service integrates with Microsoft Foundry. Within AI Foundry, an AI Agent acts as a "smart" microservice that can be used to answer questions (RAG), perform actions, or completely automate workflows. It achieves this by combining the power of generative AI models with tools that allow it to access and interact with real-world data sources. Here's an example of an agent:

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

- **Thread and messages**. The thread is another important concept. It represents a conversation or interaction between an agent and a user. Threads can be used to track the progress of a conversation, store context information, and manage the state of the interaction. Here's an example of a thread:

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

- **Integrates with other AI frameworks**. Azure AI Agent service can interact with other frameworks like AutoGen and Semantic Kernel, which means you can build part of your app in one of these frameworks and for example using the Agent service as an orchestrator or you can build everything in the Agent service.

**Use Cases**: Azure AI Agent Service is designed for enterprise applications that require secure, scalable, and flexible AI agent deployment.

## What's the difference between these frameworks?
 
It does sound like there is a lot of overlap between these frameworks, but there are some key differences in terms of their design, capabilities, and target use cases:
 
- **AutoGen**: Is an experimentation framework focused on leading-edge research on multi-agent systems. It is the best place to experiment and prototype sophisticated multi-agent systems.
- **Semantic Kernel**: Is a production-ready agent library for building enterprise agentic applications. Focuses on event-driven, distributed agentic applications, enabling multiple LLMs and SLMs, tools, and single/multi-agent design patterns.
- **Azure AI Agent Service**: Is a platform and deployment service in Azure Foundry for agents. It offers building connectivity to services support by Azure Found like Azure OpenAI, Azure AI Search, Bing Search and code execution.
 
Still not sure which one to choose?

### Use Cases
 
Let's see if we can help you by going through some common use cases:
 
> Q: I'm experimenting, learning and building proof-of-concept agent applications, and I want to be able to build and experiment quickly
>

>A: AutoGen would be a good choice for this scenario, as it focuses on event-driven, distributed agentic applications and supports advanced multi-agent design patterns.

> Q: What makes AutoGen a better choice than Semantic Kernel and Azure AI Agent Service for this use case?
>
> A: AutoGen is specifically designed for event-driven, distributed agentic applications, making it well-suited for automating code generation and data analysis tasks. It provides the necessary tools and capabilities to build complex multi-agent systems efficiently.

>Q: Sounds like Azure AI Agent Service could work here too, it has tools for code generation and more?

>
> A: Yes, Azure AI Agent Service is a platform service for agents and add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. It makes it easy to build your agents in the Foundry Portal and deploy them at scale.
 
> Q: I'm still confused just give me one option
>
> A: A great choice is to build your application in Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. This approach allows you to easily persist your agents while leveraging the power to build multi-agent systems in Semantic Kernel. Additionally, Semantic Kernel has a connector in AutoGen, making it easy to use both frameworks together.
 
Let's summarize the key differences in a table:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Event-driven, distributed agentic applications | Agents, Personas, Functions, Data | Code generation, data analysis tasks |
| Semantic Kernel | Understanding and generating human-like text content | Agents, Modular Components, Collaboration | Natural language understanding, content generation |
| Azure AI Agent Service | Flexible models, enterprise security, Code generation, Tool calling | Modularity, Collaboration, Process Orchestration | Secure, scalable, and flexible AI agent deployment |

What's the ideal use case for each of these frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

The answer is yes, you can integrate your existing Azure ecosystem tools directly with Azure AI Agent Service especially, this because it has been built to work seamlessly with other Azure services. You could for example integrate Bing, Azure AI Search, and Azure Functions. There's also deep integration with Microsoft Foundry.

For AutoGen and Semantic Kernel, you can also integrate with Azure services, but it may require you to call the Azure services from your code. Another way to integrate is to use the Azure SDKs to interact with Azure services from your agents. Additionally, like was mentioned, you can use Azure AI Agent Service as an orchestrator for your agents built in AutoGen or Semantic Kernel which would give easy access to the Azure ecosystem.

## Sample Codes

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet with other learners, attend office hours and get your AI Agents questions answered.

## References

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel and AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## Previous Lesson

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免責聲明：
本文件係使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們力求準確，但請注意，自動翻譯可能包含錯誤或不精確之處。原始語言之原文應被視為具權威性的版本。若涉及重要資訊，建議採用專業人工翻譯。對因使用本翻譯而產生之任何誤解或誤釋，概不負責。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->