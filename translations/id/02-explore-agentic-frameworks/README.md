[![Menjelajahi Kerangka Agen AI](../../../translated_images/id/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Klik gambar di atas untuk melihat video pelajaran ini)_

# Jelajahi Kerangka Agen AI

Kerangka agen AI adalah platform perangkat lunak yang dirancang untuk menyederhanakan pembuatan, penyebaran, dan pengelolaan agen AI. Kerangka ini menyediakan komponen pra-bangun, abstraksi, dan alat yang mempermudah pengembangan sistem AI yang kompleks.

Kerangka ini membantu pengembang fokus pada aspek unik dari aplikasi mereka dengan menyediakan pendekatan standar untuk tantangan umum dalam pengembangan agen AI. Mereka meningkatkan skalabilitas, aksesibilitas, dan efisiensi dalam membangun sistem AI.

## Pendahuluan 

Pelajaran ini akan membahas:

- Apa itu Kerangka Agen AI dan apa yang memungkinkan pengembang untuk mencapai?
- Bagaimana tim dapat menggunakan ini untuk dengan cepat membuat prototipe, mengiterasi, dan meningkatkan kemampuan agen mereka?
- Apa perbedaan antara kerangka kerja dan alat yang dibuat oleh Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, dan <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Bisakah saya mengintegrasikan alat ekosistem Azure saya yang sudah ada secara langsung, atau apakah saya memerlukan solusi mandiri?
- Apa itu Azure AI Agents service dan bagaimana hal ini membantu saya?

## Tujuan pembelajaran

Tujuan pelajaran ini adalah membantu Anda memahami:

- Peran Kerangka Agen AI dalam pengembangan AI.
- Cara memanfaatkan Kerangka Agen AI untuk membangun agen cerdas.
- Kemampuan utama yang diaktifkan oleh Kerangka Agen AI.
- Perbedaan antara AutoGen, Semantic Kernel, dan Azure AI Agent Service.

## Apa itu Kerangka Agen AI dan apa yang memungkinkan pengembang lakukan?

Kerangka AI tradisional dapat membantu Anda mengintegrasikan AI ke dalam aplikasi Anda dan membuat aplikasi tersebut menjadi lebih baik dengan cara-cara berikut:

- **Personalisasi**: AI dapat menganalisis perilaku dan preferensi pengguna untuk memberikan rekomendasi, konten, dan pengalaman yang dipersonalisasi.
Example: Layanan streaming seperti Netflix menggunakan AI untuk menyarankan film dan acara berdasarkan riwayat tontonan, meningkatkan keterlibatan dan kepuasan pengguna.
- **Otomatisasi dan Efisiensi**: AI dapat mengotomatisasi tugas-tugas berulang, merampingkan alur kerja, dan meningkatkan efisiensi operasional.
Example: Aplikasi layanan pelanggan menggunakan chatbot bertenaga AI untuk menangani pertanyaan umum, mengurangi waktu respons dan membebaskan agen manusia untuk menangani masalah yang lebih kompleks.
- **Peningkatan Pengalaman Pengguna**: AI dapat memperbaiki pengalaman pengguna secara keseluruhan dengan menyediakan fitur cerdas seperti pengenalan suara, pemrosesan bahasa alami, dan teks prediktif.
Example: Asisten virtual seperti Siri dan Google Assistant menggunakan AI untuk memahami dan merespons perintah suara, memudahkan pengguna berinteraksi dengan perangkat mereka.

### Semua itu terdengar bagus, bukan? Jadi kenapa kita membutuhkan Kerangka Agen AI?

Kerangka Agen AI mewakili sesuatu yang lebih dari sekadar kerangka AI. Mereka dirancang untuk memungkinkan pembuatan agen cerdas yang dapat berinteraksi dengan pengguna, agen lain, dan lingkungan untuk mencapai tujuan tertentu. Agen-agen ini dapat menunjukkan perilaku otonom, membuat keputusan, dan beradaptasi dengan kondisi yang berubah. Mari kita lihat beberapa kemampuan utama yang diaktifkan oleh Kerangka Agen AI:

- **Kolaborasi dan Koordinasi Agen**: Memungkinkan pembuatan beberapa agen AI yang dapat bekerja bersama, berkomunikasi, dan berkoordinasi untuk menyelesaikan tugas-tugas kompleks.
- **Otomatisasi dan Manajemen Tugas**: Menyediakan mekanisme untuk mengotomatisasi alur kerja multi-langkah, pendelegasian tugas, dan manajemen tugas dinamis di antara agen.
- **Pemahaman Kontekstual dan Adaptasi**: Membekali agen dengan kemampuan untuk memahami konteks, beradaptasi dengan lingkungan yang berubah, dan membuat keputusan berdasarkan informasi waktu nyata.

Jadi, sebagai ringkasan, agen memungkinkan Anda melakukan lebih banyak, membawa otomatisasi ke tingkat berikutnya, menciptakan sistem yang lebih cerdas yang dapat beradaptasi dan belajar dari lingkungan mereka.

## Bagaimana cara dengan cepat membuat prototipe, mengiterasi, dan meningkatkan kemampuan agen?

Lanskap ini bergerak cepat, tetapi ada beberapa hal yang umum di sebagian besar Kerangka Agen AI yang dapat membantu Anda dengan cepat membuat prototipe dan mengiterasi, yaitu komponen modular, alat kolaboratif, dan pembelajaran waktu nyata. Mari selami ini:

- **Gunakan Komponen Modular**: SDK AI menawarkan komponen pra-bangun seperti konektor AI dan memori, pemanggilan fungsi menggunakan bahasa alami atau plugin kode, template prompt, dan lainnya.
- **Manfaatkan Alat Kolaboratif**: Rancang agen dengan peran dan tugas spesifik, memungkinkan mereka untuk menguji dan menyempurnakan alur kerja kolaboratif.
- **Belajar Secara Waktu Nyata**: Terapkan loop umpan balik di mana agen belajar dari interaksi dan menyesuaikan perilaku mereka secara dinamis.

### Gunakan Komponen Modular

SDK seperti Microsoft Semantic Kernel dan LangChain menawarkan komponen pra-bangun seperti konektor AI, template prompt, dan manajemen memori.

**How teams can use these**: Tim dapat dengan cepat merakit komponen-komponen ini untuk membuat prototipe fungsional tanpa memulai dari nol, memungkinkan eksperimen dan iterasi yang cepat.

**How it works in practice**: Anda dapat menggunakan parser pra-bangun untuk mengekstrak informasi dari input pengguna, modul memori untuk menyimpan dan mengambil data, dan generator prompt untuk berinteraksi dengan pengguna, semua tanpa harus membangun komponen-komponen ini dari awal.

**Example code**. Let's look at examples of how you can use a pre-built AI Connector with Semantic Kernel Python and .Net that uses auto-function calling to have the model respond to user input:

``` python
# Contoh Semantic Kernel Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definisikan objek ChatHistory untuk menyimpan konteks percakapan
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definisikan plugin contoh yang berisi fungsi untuk memesan perjalanan
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Buat Kernel
kernel = Kernel()

# Tambahkan plugin contoh ke objek Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definisikan konektor AI Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definisikan pengaturan permintaan untuk mengonfigurasi model dengan pemanggilan fungsi otomatis
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Buat permintaan ke model untuk riwayat obrolan dan pengaturan permintaan yang diberikan
    # Kernel berisi contoh yang akan diminta model untuk dipanggil
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
    # Contoh Respon Model AI: `Penerbangan Anda ke New York pada 1 Januari 2025 telah berhasil dipesan. Selamat jalan! ✈️🗽`

    # Tambahkan respons model ke konteks riwayat obrolan kita
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

What you can see from this example is how you can leverage a pre-built parser to extract key information from user input, such as the origin, destination, and date of a flight booking request. This modular approach allows you to focus on the high-level logic.

### Manfaatkan Alat Kolaboratif

Kerangka seperti CrewAI, Microsoft AutoGen, dan Semantic Kernel memfasilitasi pembuatan beberapa agen yang dapat bekerja bersama.

**How teams can use these**: Tim dapat merancang agen dengan peran dan tugas khusus, sehingga memungkinkan mereka menguji dan menyempurnakan alur kerja kolaboratif dan meningkatkan efisiensi sistem secara keseluruhan.

**How it works in practice**: Anda dapat membuat tim agen di mana setiap agen memiliki fungsi khusus, seperti pengambilan data, analisis, atau pengambilan keputusan. Agen-agen ini dapat berkomunikasi dan berbagi informasi untuk mencapai tujuan bersama, seperti menjawab pertanyaan pengguna atau menyelesaikan tugas.

**Contoh kode (AutoGen)**:

```python
# membuat agen, lalu buat jadwal round robin di mana mereka dapat bekerja sama, dalam hal ini secara berurutan

# Agen Pengambilan Data
# Agen Analisis Data
# Agen Pengambil Keputusan

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

# percakapan berakhir ketika pengguna mengatakan "SETUJUI"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Gunakan asyncio.run(...) saat menjalankan dalam skrip.
await Console(stream)
```

What you see in the previous code is how you can create a task that involves multiple agents working together to analyze data. Each agent performs a specific function, and the task is executed by coordinating the agents to achieve the desired outcome. By creating dedicated agents with specialized roles, you can improve task efficiency and performance.

### Belajar Secara Waktu Nyata

Kerangka lanjutan menyediakan kemampuan untuk pemahaman konteks waktu nyata dan adaptasi.

**How teams can use these**: Tim dapat menerapkan loop umpan balik di mana agen belajar dari interaksi dan menyesuaikan perilaku mereka secara dinamis, yang mengarah pada peningkatan dan penyempurnaan kemampuan secara berkelanjutan.

**How it works in practice**: Agen dapat menganalisis umpan balik pengguna, data lingkungan, dan hasil tugas untuk memperbarui basis pengetahuan mereka, menyesuaikan algoritme pengambilan keputusan, dan meningkatkan kinerja dari waktu ke waktu. Proses pembelajaran iteratif ini memungkinkan agen beradaptasi dengan kondisi yang berubah dan preferensi pengguna, meningkatkan efektivitas sistem secara keseluruhan.

## Apa perbedaan antara kerangka kerja AutoGen, Semantic Kernel dan Azure AI Agent Service?

Ada banyak cara untuk membandingkan kerangka-kerangka ini, tetapi mari kita lihat beberapa perbedaan utama dalam hal desain, kemampuan, dan kasus penggunaan yang ditargetkan:

## AutoGen

AutoGen adalah kerangka sumber terbuka yang dikembangkan oleh AI Frontiers Lab di Microsoft Research. Ini berfokus pada aplikasi *agentic* terdistribusi berbasis peristiwa, memungkinkan banyak LLM dan SLM, alat, dan pola desain multi-agen tingkat lanjut.

AutoGen dibangun di sekitar konsep inti agen, yang merupakan entitas otonom yang dapat memahami lingkungan mereka, membuat keputusan, dan mengambil tindakan untuk mencapai tujuan tertentu. Agen berkomunikasi melalui pesan asinkron, memungkinkan mereka bekerja secara mandiri dan paralel, meningkatkan skalabilitas dan responsivitas sistem.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agen didasarkan pada model aktor</a>. Menurut Wikipedia, seorang aktor adalah _blok bangunan dasar komputasi konkuren. Sebagai respons terhadap sebuah pesan yang diterimanya, seorang aktor dapat: membuat keputusan lokal, membuat lebih banyak aktor, mengirim lebih banyak pesan, dan menentukan bagaimana merespons pesan berikutnya yang diterima_.

**Use Cases**: Mengotomatisasi pembuatan kode, tugas analisis data, dan membangun agen khusus untuk fungsi perencanaan dan penelitian.

Here are some important core concepts of AutoGen:

- **Agents**. An agent is a software entity that:
  - **Communicates via messages**, these messages can be synchronous or asynchronous.
  - **Maintains its own state**, which can be modified by incoming messages.
  - **Performs actions** in response to received messages or changes in its state. These actions may modify the agent’s state and produce external effects, such as updating message logs, sending new messages, executing code, or making API calls.
    
  Here you have a short code snippet in which you create your own agent with Chat capabilities:

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
    
    In the previous code, `MyAgent` has been created and inherits from `RoutedAgent`. It has a message handler that prints the content of the message and then sends a response using the `AssistantAgent` delegate. Especially note how we assign to `self._delegate` an instance of `AssistantAgent` which is a pre-built agent that can handle chat completions.


    Let's let AutoGen know about this agent type and kick off the program next:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Mulai memproses pesan di latar belakang.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    In the previous code the agents are registered with the runtime and then a message is sent to the agent resulting in the following output:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multi agents**. AutoGen supports the creation of multiple agents that can work together to achieve complex tasks. Agents can communicate, share information, and coordinate their actions to solve problems more efficiently. To create a multi-agent system, you can define different types of agents with specialized functions and roles, such as data retrieval, analysis, decision-making, and user interaction. Let's see how such a creation looks like so we get a sense of it:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Contoh mendeklarasikan sebuah Agen
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Menggunakan tipe topik sebagai tipe agen.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # deklarasi lainnya dipersingkat untuk ringkasan

    # Grup obrolan
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

    In the previous code we have a `GroupChatManager` that is registered with the runtime. This manager is responsible for coordinating the interactions between different types of agents, such as writers, illustrators, editors, and users.

- **Agent Runtime**. The framework provides a runtime environment, enabling communication between agents, manages their identities and lifecycles, and enforce security and privacy boundaries. This means that you can run your agents in a secure and controlled environment, ensuring that they can interact safely and efficiently. There are two runtimes of interest:
  - **Stand-alone runtime**. This is a good choice for single-process applications where all agents are implemented in the same programming language and run in the same process. Here's an illustration of how it works:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Runtime mandiri</a>   
Application stack

    *agen berkomunikasi melalui pesan melalui runtime, dan runtime mengelola siklus hidup agen*

  - **Distributed agent runtime**, is suitable for multi-process applications where agents may be implemented in different programming languages and running on different machines. Here's an illustration of how it works:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Runtime terdistribusi</a>

## Semantic Kernel + Agent Framework

Semantic Kernel adalah SDK Orkestrasi AI yang siap untuk perusahaan. Ia terdiri dari konektor AI dan memori, bersama dengan sebuah Kerangka Agen.

Mari kita bahas beberapa komponen inti:

- **AI Connectors**: This is an interface with external AI services and data sources for use in both Python and C#.

  ```python
  # Semantic Kernel Python
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

    Here you have a simple example of how you can create a kernel and add a chat completion service. Semantic Kernel creates a connection to an external AI service, in this case, Azure OpenAI Chat Completion.

- **Plugins**: These encapsulate functions that an application can use. There are both ready-made plugins and custom ones you can create. A related concept is "prompt functions." Instead of providing natural language cues for function invocation, you broadcast certain functions to the model. Based on the current chat context, the model may choose to call one of these functions to complete a request or query. Here's an example:

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

    Here, you first have a template prompt `skPrompt` that leaves room for the user to input text, `$userInput`. Then you create the kernel function `SummarizeText` and then import it into the kernel with the plugin name `SemanticFunctions`. Note the name of the function that helps Semantic Kernel understand what the function does and when it should be called.

- **Native function**: There's also native functions that the framework can call directly to carry out the task. Here's an example of such a function retrieving the content from a file:

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

- **Memory**:  Abstracts and simplifies context management for AI apps. The idea with memory is that this is something the LLM should know about. You can store this information in a vector store which ends up being an in-memory database or a vector database or similar. Here's an example of a very simplified scenario where *fakta* are added to the memory:

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

    Fakta-fakta ini kemudian disimpan dalam koleksi memori `SummarizedAzureDocs`. Ini adalah contoh yang sangat disederhanakan, tetapi Anda dapat melihat bagaimana Anda dapat menyimpan informasi dalam memori untuk digunakan oleh LLM.

Jadi itu dasar-dasar kerangka kerja Semantic Kernel, bagaimana dengan Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service adalah penambahan yang lebih baru, diperkenalkan di Microsoft Ignite 2024. Layanan ini memungkinkan pengembangan dan penyebaran agen AI dengan model yang lebih fleksibel, seperti pemanggilan langsung model LLM sumber terbuka seperti Llama 3, Mistral, dan Cohere.

Azure AI Agent Service menyediakan mekanisme keamanan perusahaan dan metode penyimpanan data yang lebih kuat, sehingga cocok untuk aplikasi perusahaan.

Layanan ini bekerja langsung dengan kerangka orkestrasi multi-agen seperti AutoGen dan Semantic Kernel.

Layanan ini saat ini dalam Public Preview dan mendukung Python dan C# untuk membangun agen.

Menggunakan Semantic Kernel Python, kita dapat membuat Azure AI Agent dengan plugin yang didefinisikan pengguna:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definisikan plugin contoh untuk contoh tersebut
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
        # Buat definisi agen
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Buat AzureAI Agent menggunakan klien dan definisi agen yang telah ditentukan
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Buat sebuah thread untuk menampung percakapan
        # Jika tidak ada thread yang disediakan, sebuah thread baru akan
        # dibuat dan dikembalikan bersama dengan respons awal
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
                # Panggil agen untuk thread yang ditentukan
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

### Konsep inti

Azure AI Agent Service memiliki konsep inti berikut:

- **Agent**. Azure AI Agent Service terintegrasi dengan Microsoft Foundry. Di dalam AI Foundry, sebuah Agen AI bertindak sebagai microservice "pintar" yang dapat digunakan untuk menjawab pertanyaan (RAG), melakukan tindakan, atau sepenuhnya mengotomatisasi alur kerja. Ini dicapai dengan menggabungkan kekuatan model generatif AI dengan alat yang memungkinkannya mengakses dan berinteraksi dengan sumber data dunia nyata. Berikut adalah contoh agen:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Dalam contoh ini, sebuah agen dibuat dengan model `gpt-4o-mini`, nama `my-agent`, dan instruksi `You are helpful agent`. Agen ini dilengkapi dengan alat dan sumber daya untuk melakukan tugas interpretasi kode.

- **Thread and messages**. Thread adalah konsep penting lainnya. Thread merepresentasikan sebuah percakapan atau interaksi antara agen dan pengguna. Thread dapat digunakan untuk melacak kemajuan percakapan, menyimpan informasi konteks, dan mengelola status interaksi. Berikut adalah contoh sebuah thread:

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

    Dalam kode sebelumnya, sebuah thread dibuat. Setelah itu, sebuah pesan dikirim ke thread. Dengan memanggil `create_and_process_run`, agen diminta untuk mengerjakan thread tersebut. Akhirnya, pesan-pesan diambil dan dicatat untuk melihat respons agen. Pesan-pesan tersebut menunjukkan kemajuan percakapan antara pengguna dan agen. Penting juga untuk memahami bahwa pesan-pesan dapat berupa berbagai tipe seperti teks, gambar, atau file, yang merupakan hasil kerja agen misalnya sebuah gambar atau respons teks. Sebagai pengembang, Anda kemudian dapat menggunakan informasi ini untuk memproses respons lebih lanjut atau menyajikannya kepada pengguna.

- **Integrates with other AI frameworks**. Azure AI Agent service dapat berinteraksi dengan kerangka kerja lain seperti AutoGen dan Semantic Kernel, yang berarti Anda dapat membangun sebagian aplikasi Anda di salah satu kerangka ini dan misalnya menggunakan layanan Agent sebagai orkestrator atau Anda dapat membangun semuanya di layanan Agent.

**Kasus Penggunaan**: Azure AI Agent Service dirancang untuk aplikasi perusahaan yang membutuhkan penyebaran agen AI yang aman, dapat diskalakan, dan fleksibel.

## What's the difference between these frameworks?
 
Memang terdengar seperti ada banyak tumpang tindih antara kerangka-kerangka ini, tetapi ada beberapa perbedaan kunci dalam hal desain, kapabilitas, dan kasus penggunaan yang ditargetkan:
 
- **AutoGen**: Adalah kerangka eksperimen yang berfokus pada penelitian terdepan tentang sistem multi-agen. Ini adalah tempat terbaik untuk bereksperimen dan membuat prototipe sistem multi-agen yang canggih.
- **Semantic Kernel**: Adalah pustaka agen siap-produksi untuk membangun aplikasi agenik perusahaan. Berfokus pada aplikasi agenik yang didorong oleh event dan terdistribusi, memungkinkan beberapa LLM dan SLM, alat, dan pola desain agen tunggal/multi.
- **Azure AI Agent Service**: Adalah platform dan layanan penyebaran di Azure Foundry untuk agen. Ini menawarkan konektivitas ke layanan yang didukung oleh Azure Found seperti Azure OpenAI, Azure AI Search, Bing Search dan eksekusi kode.
 
Masih belum yakin mana yang harus dipilih?

### Use Cases
 
Mari kita lihat apakah kami dapat membantu Anda dengan menelusuri beberapa kasus penggunaan umum:
 
> Q: Saya sedang bereksperimen, belajar dan membangun aplikasi agen proof-of-concept, dan saya ingin dapat membangun dan bereksperimen dengan cepat
>

>A: AutoGen akan menjadi pilihan yang baik untuk skenario ini, karena ia berfokus pada aplikasi agenik yang didorong oleh event dan terdistribusi serta mendukung pola desain multi-agen yang canggih.

> Q: Apa yang membuat AutoGen menjadi pilihan yang lebih baik daripada Semantic Kernel dan Azure AI Agent Service untuk kasus penggunaan ini?
>
> A: AutoGen secara spesifik dirancang untuk aplikasi agenik yang didorong oleh event dan terdistribusi, menjadikannya sangat cocok untuk mengotomatisasi pembuatan kode dan tugas analisis data. Ia menyediakan alat dan kapabilitas yang diperlukan untuk membangun sistem multi-agen yang kompleks secara efisien.

>Q: Kedengarannya Azure AI Agent Service juga bisa bekerja di sini, ia memiliki alat untuk pembuatan kode dan lainnya?

>
> A: Ya, Azure AI Agent Service adalah layanan platform untuk agen dan menambahkan kapabilitas bawaan untuk beberapa model, Azure AI Search, Bing Search dan Azure Functions. Ini memudahkan membangun agen Anda di Portal Foundry dan menyebarkannya secara besar-besaran.
 
> Q: Saya masih bingung beri saya satu opsi saja
>
> A: Pilihan yang bagus adalah membangun aplikasi Anda di Semantic Kernel terlebih dahulu dan kemudian menggunakan Azure AI Agent Service untuk menyebarkan agen Anda. Pendekatan ini memungkinkan Anda dengan mudah menyimpan agen Anda sambil memanfaatkan kekuatan untuk membangun sistem multi-agen di Semantic Kernel. Selain itu, Semantic Kernel memiliki konektor di AutoGen, sehingga mudah untuk menggunakan kedua kerangka bersama-sama.
 
Mari kita ringkas perbedaan kunci dalam sebuah tabel:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Aplikasi agenik yang didorong oleh event dan terdistribusi | Agen, Persona, Fungsi, Data | Pembuatan kode, tugas analisis data |
| Semantic Kernel | Memahami dan menghasilkan konten teks mirip manusia | Agen, Komponen Modular, Kolaborasi | Pemahaman bahasa alami, pembuatan konten |
| Azure AI Agent Service | Model fleksibel, keamanan perusahaan, pembuatan kode, pemanggilan alat | Modularitas, Kolaborasi, Orkestrasi Proses | Penyebaran agen AI yang aman, dapat diskalakan, dan fleksibel |

Apa kasus penggunaan ideal untuk masing-masing kerangka ini?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

Jawabannya adalah ya, Anda dapat mengintegrasikan alat ekosistem Azure yang sudah ada langsung dengan Azure AI Agent Service terutama, ini karena layanan ini dibangun untuk bekerja mulus dengan layanan Azure lainnya. Anda bisa misalnya mengintegrasikan Bing, Azure AI Search, dan Azure Functions. Ada juga integrasi mendalam dengan Microsoft Foundry.

Untuk AutoGen dan Semantic Kernel, Anda juga dapat berintegrasi dengan layanan Azure, tetapi mungkin mengharuskan Anda memanggil layanan Azure dari kode Anda. Cara lain untuk berintegrasi adalah menggunakan SDK Azure untuk berinteraksi dengan layanan Azure dari agen Anda. Selain itu, seperti yang disebutkan, Anda dapat menggunakan Azure AI Agent Service sebagai orkestrator untuk agen Anda yang dibangun di AutoGen atau Semantic Kernel yang akan memberi akses mudah ke ekosistem Azure.

## Sample Codes

- Python: [Kerangka Agen](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Kerangka Agen](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Bergabunglah dengan [Discord Microsoft Foundry](https://aka.ms/ai-agents/discord) untuk bertemu dengan pelajar lain, menghadiri jam kantor dan mendapatkan jawaban atas pertanyaan Anda tentang Agen AI.

## References

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Layanan Agen Azure</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel dan AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Kerangka Agen Semantic Kernel Python</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Kerangka Agen Semantic Kernel .Net</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Layanan Agen Azure AI</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Menggunakan Layanan Agen Azure AI dengan AutoGen / Semantic Kernel untuk membangun solusi multi-agen</a>

## Previous Lesson

[Pengenalan Agen AI dan Kasus Penggunaan Agen](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Memahami Pola Desain Agenik](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Penafian:
Dokumen ini telah diterjemahkan menggunakan layanan penerjemahan berbasis AI Co-op Translator (https://github.com/Azure/co-op-translator). Meskipun kami berupaya mencapai akurasi, harap diperhatikan bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang berwenang. Untuk informasi yang bersifat kritis, disarankan menggunakan jasa penerjemah profesional manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau penafsiran yang keliru yang timbul akibat penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->