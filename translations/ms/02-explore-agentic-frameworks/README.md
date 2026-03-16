[![Meneroka Rangka Kerja Ejen AI](../../../translated_images/ms/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Klik imej di atas untuk melihat video pelajaran ini)_

# Terokai Rangka Kerja Ejen AI

Rangka kerja ejen AI adalah platform perisian yang direka untuk memudahkan penciptaan, pelaksanaan, dan pengurusan ejen AI. Rangka kerja ini menyediakan pembangun dengan komponen siap sedia, abstraksi, dan alat yang memudahkan pembangunan sistem AI yang kompleks.

Rangka kerja ini membantu pembangun menumpukan perhatian pada aspek unik aplikasi mereka dengan menyediakan pendekatan standard untuk cabaran biasa dalam pembangunan ejen AI. Ia meningkatkan kebolehskalaan, aksesibiliti, dan kecekapan dalam membina sistem AI.

## Pengenalan 

Pelajaran ini akan merangkumi:

- Apakah Rangka Kerja Ejen AI dan apa yang mereka benarkan pembangun capai?
- Bagaimana pasukan boleh menggunakan ini untuk membuat prototaip dengan cepat, iterasi, dan memperbaiki keupayaan ejen mereka?
- Apakah perbezaan antara rangka kerja dan alat yang dihasilkan oleh Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, dan <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Bolehkah saya mengintegrasikan alat ekosistem Azure saya yang sedia ada secara langsung, atau adakah saya memerlukan penyelesaian berdiri sendiri?
- Apakah perkhidmatan Azure AI Agents dan bagaimana ini membantu saya?

## Matlamat pembelajaran

Matlamat pelajaran ini adalah untuk membantu anda memahami:

- Peranan Rangka Kerja Ejen AI dalam pembangunan AI.
- Cara memanfaatkan Rangka Kerja Ejen AI untuk membina ejen pintar.
- Keupayaan utama yang dibolehkan oleh Rangka Kerja Ejen AI.
- Perbezaan antara AutoGen, Semantic Kernel, dan Perkhidmatan Ejen Azure AI.

## Apakah Rangka Kerja Ejen AI dan apa yang mereka benarkan pembangun lakukan?

Rangka Kerja AI tradisional boleh membantu anda mengintegrasikan AI ke dalam aplikasi anda dan menjadikan aplikasi ini lebih baik dalam cara berikut:

- **Personalisasi**: AI boleh menganalisis kelakuan dan keutamaan pengguna untuk menyediakan cadangan, kandungan, dan pengalaman yang diperibadikan.
Contoh: Perkhidmatan penstriman seperti Netflix menggunakan AI untuk mencadangkan filem dan rancangan berdasarkan sejarah tontonan, meningkatkan penglibatan dan kepuasan pengguna.
- **Automasi dan Kecekapan**: AI boleh mengautomasikan tugas berulang, melicinkan aliran kerja, dan meningkatkan kecekapan operasi.
Contoh: Aplikasi perkhidmatan pelanggan menggunakan chatbot bertenaga AI untuk menangani pertanyaan biasa, mengurangkan masa respon dan membebaskan ejen manusia untuk isu yang lebih kompleks.
- **Pengalaman Pengguna Dipertingkatkan**: AI boleh meningkatkan pengalaman pengguna secara keseluruhan dengan menyediakan ciri pintar seperti pengecaman suara, pemprosesan bahasa semula jadi, dan teks ramalan.
Contoh: Pembantu maya seperti Siri dan Google Assistant menggunakan AI untuk memahami dan menjawab arahan suara, memudahkan pengguna berinteraksi dengan peranti mereka.

### Semua itu kedengaran hebat bukan, jadi mengapa kita perlukan Rangka Kerja Ejen AI?

Rangka Kerja Ejen AI mewakili sesuatu yang lebih daripada sekadar rangka kerja AI. Ia direka untuk membolehkan penciptaan ejen pintar yang boleh berinteraksi dengan pengguna, ejen lain, dan persekitaran untuk mencapai matlamat tertentu. Ejen ini boleh menunjukkan tingkah laku autonomi, membuat keputusan, dan menyesuaikan diri dengan keadaan yang berubah. Mari kita lihat beberapa keupayaan utama yang dibolehkan oleh Rangka Kerja Ejen AI:

- **Kerjasama dan Penyelarasan Ejen**: Membolehkan penciptaan beberapa ejen AI yang boleh bekerjasama, berkomunikasi, dan menyelaras untuk menyelesaikan tugas kompleks.
- **Automasi dan Pengurusan Tugas**: Menyediakan mekanisme untuk mengautomasikan aliran kerja berbilang langkah, pendelegasian tugas, dan pengurusan tugas dinamik antara ejen.
- **Pemahaman Kontekstual dan Penyesuaian**: Melengkapi ejen dengan keupayaan untuk memahami konteks, menyesuaikan diri dengan persekitaran yang berubah, dan membuat keputusan berdasarkan maklumat masa nyata.

Jadi secara ringkas, ejen membolehkan anda melakukan lebih banyak, membawa automasi ke tahap seterusnya, mencipta sistem yang lebih pintar yang boleh menyesuaikan diri dan belajar dari persekitarannya.

## Bagaimana untuk membuat prototaip dengan cepat, iterasi, dan memperbaiki keupayaan ejen?

Ini adalah lanskap yang bergerak pantas, tetapi terdapat beberapa perkara yang biasa dalam kebanyakan Rangka Kerja Ejen AI yang boleh membantu anda membuat prototaip dan iterasi dengan cepat iaitu komponen modul, alat kolaboratif, dan pembelajaran masa nyata. Mari kita terokai ini:

- **Gunakan Komponen Modular**: SDK AI menawarkan komponen siap sedia seperti penyambung AI dan Memori, panggilan fungsi menggunakan bahasa semula jadi atau plugin kod, templat arahan, dan lain-lain.
- **Manfaatkan Alat Kolaboratif**: Reka ejen dengan peranan dan tugas khusus, membolehkan mereka menguji dan memperhalusi aliran kerja kolaboratif.
- **Belajar dalam Masa Nyata**: Laksanakan gelung maklum balas di mana ejen belajar dari interaksi dan menyesuaikan tingkah laku mereka secara dinamik.

### Gunakan Komponen Modular

SDK seperti Microsoft Semantic Kernel dan LangChain menawarkan komponen siap sedia seperti penyambung AI, templat arahan, dan pengurusan memori.

**Bagaimana pasukan boleh gunakan ini**: Pasukan boleh dengan cepat menyusun komponen ini untuk mencipta prototaip berfungsi tanpa bermula dari kosong, membolehkan eksperimen dan iterasi pantas.

**Bagaimana ia berfungsi dalam amalan**: Anda boleh menggunakan parser siap sedia untuk mengekstrak maklumat dari input pengguna, modul memori untuk menyimpan dan mengambil data, dan penjana arahan untuk berinteraksi dengan pengguna, semua tanpa perlu membina komponen ini dari awal.

**Kod contoh**. Mari lihat contoh bagaimana anda boleh menggunakan Penyambung AI siap sedia dengan Semantic Kernel Python dan .Net yang menggunakan panggilan fungsi auto untuk membolehkan model memberi respons kepada input pengguna:

``` python
# Contoh Semantic Kernel Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Tentukan objek ChatHistory untuk menyimpan konteks perbualan
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Tentukan pemalam contoh yang mengandungi fungsi untuk menempah perjalanan
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Cipta Kernel
kernel = Kernel()

# Tambah pemalam contoh ke objek Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Tentukan Penyambung AI Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Tentukan tetapan permintaan untuk mengkonfigurasi model dengan pemanggilan fungsi automatik
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Buat permintaan kepada model untuk sejarah perbualan dan tetapan permintaan yang diberikan
    # Kernel mengandungi contoh yang model akan minta untuk dipanggil
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
    # Contoh Respons Model AI: `Penerbangan anda ke New York pada 1 Januari 2025 telah berjaya ditempah. Selamat jalan! ✈️🗽`

    # Tambah respons model ke konteks sejarah perbualan kita
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

Apa yang anda boleh lihat dari contoh ini adalah bagaimana anda boleh memanfaatkan parser siap sedia untuk mengekstrak maklumat utama dari input pengguna, seperti asal, destinasi, dan tarikh permintaan tempahan penerbangan. Pendekatan modular ini membolehkan anda fokus pada logik aras tinggi.

### Manfaatkan Alat Kolaboratif

Rangka kerja seperti CrewAI, Microsoft AutoGen, dan Semantic Kernel memudahkan penciptaan beberapa ejen yang boleh bekerjasama.

**Bagaimana pasukan boleh gunakan ini**: Pasukan boleh mereka ejen dengan peranan dan tugas khusus, membolehkan mereka menguji dan memperhalusi aliran kerja kolaboratif serta meningkatkan kecekapan sistem keseluruhan.

**Bagaimana ia berfungsi dalam amalan**: Anda boleh mencipta satu pasukan ejen di mana setiap ejen mempunyai fungsi khusus, seperti pengambilan data, analisis, atau pembuatan keputusan. Ejen ini boleh berkomunikasi dan berkongsi maklumat untuk mencapai matlamat bersama, seperti menjawab pertanyaan pengguna atau menyelesaikan tugasan.

**Kod contoh (AutoGen)**:

```python
# mencipta ejen, kemudian membuat jadual round robin di mana mereka boleh bekerja bersama, dalam kes ini secara berurutan

# Ejen Pengambilan Data
# Ejen Analisis Data
# Ejen Pembuat Keputusan

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

# perbualan berakhir apabila pengguna berkata "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Gunakan asyncio.run(...) apabila menjalankan dalam skrip.
await Console(stream)
```

Apa yang anda lihat dalam kod sebelumnya adalah bagaimana anda boleh mencipta tugas yang melibatkan beberapa ejen yang bekerja bersama untuk menganalisis data. Setiap ejen melaksanakan fungsi spesifik, dan tugas dilakukan dengan menyelaraskan ejen untuk mencapai hasil yang diingini. Dengan mencipta ejen khusus dengan peranan khusus, anda boleh meningkatkan kecekapan dan prestasi tugas.

### Belajar dalam Masa Nyata

Rangka kerja maju menyediakan keupayaan untuk pemahaman konteks masa nyata dan penyesuaian.

**Bagaimana pasukan boleh gunakan ini**: Pasukan boleh melaksanakan gelung maklum balas di mana ejen belajar dari interaksi dan menyesuaikan tingkah laku mereka secara dinamik, membawa kepada peningkatan dan penyempurnaan keupayaan secara berterusan.

**Bagaimana ia berfungsi dalam amalan**: Ejen boleh menganalisis maklum balas pengguna, data persekitaran, dan hasil tugasan untuk mengemas kini pangkalan pengetahuan mereka, menyesuaikan algoritma pembuatan keputusan, dan meningkatkan prestasi dari masa ke masa. Proses pembelajaran iteratif ini membolehkan ejen menyesuaikan diri dengan keadaan berubah dan keutamaan pengguna, meningkatkan keberkesanan sistem keseluruhan.

## Apakah perbezaan antara rangka kerja AutoGen, Semantic Kernel dan Perkhidmatan Ejen Azure AI?

Terdapat banyak cara untuk membandingkan rangka kerja ini, tetapi mari kita lihat beberapa perbezaan utama dari segi reka bentuk, keupayaan, dan kes penggunaan sasaran:

## AutoGen

AutoGen adalah rangka kerja sumber terbuka yang dibangunkan oleh Makmal AI Frontiers Microsoft Research. Ia memfokus kepada aplikasi *agentic* yang didorong acara dan diedarkan, membolehkan pelbagai LLM dan SLM, alat, dan corak reka bentuk multi-ejen yang maju.

AutoGen dibina di sekitar konsep teras ejen, yang merupakan entiti autonomi yang boleh merasakan persekitarannya, membuat keputusan, dan mengambil tindakan untuk mencapai matlamat tertentu. Ejen berkomunikasi melalui mesej tidak serentak, membolehkan mereka bekerja secara bebas dan selari, meningkatkan kebolehskalaan dan kepekaan sistem.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Ejen berdasarkan model pelakon</a>. Menurut Wikipedia, seorang pelakon adalah _blok binaan asas pengiraan serentak. Sebagai tindak balas kepada mesej yang diterimanya, pelakon boleh: membuat keputusan tempatan, mencipta lebih banyak pelakon, menghantar lebih banyak mesej, dan menentukan bagaimana untuk bertindak balas terhadap mesej seterusnya yang diterima_.

**Kes Penggunaan**: Automasi penjanaan kod, tugasan analisis data, dan membina ejen khusus untuk fungsi perancangan dan penyelidikan.

Berikut adalah beberapa konsep teras penting AutoGen:

- **Ejen**. Ejen adalah entiti perisian yang:
  - **Berkomunikasi melalui mesej**, mesej ini boleh serentak atau tidak serentak.
  - **Mengekalkan keadaan sendiri**, yang boleh diubah oleh mesej masuk.
  - **Melaksanakan tindakan** sebagai tindak balas kepada mesej diterima atau perubahan dalam keadaannya. Tindakan ini mungkin mengubah keadaan ejen dan menghasilkan kesan luaran, seperti mengemas kini log mesej, menghantar mesej baru, menjalankan kod, atau membuat panggilan API.
    
  Berikut anda mempunyai petikan kod ringkas di mana anda mencipta ejen sendiri dengan keupayaan Chat:

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
    
    Dalam kod sebelumnya, `MyAgent` telah dicipta dan mewarisi dari `RoutedAgent`. Ia mempunyai pengendali mesej yang mencetak kandungan mesej dan kemudian menghantar respons menggunakan delegasi `AssistantAgent`. Terutamanya perhatikan bagaimana kami menetapkan kepada `self._delegate` satu contoh `AssistantAgent` iaitu ejen siap sedia yang boleh mengendalikan penyelesaian chat.

    Mari beritahu AutoGen tentang jenis ejen ini dan mulakan program seterusnya:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Mulakan pemprosesan mesej di latar belakang.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Dalam kod sebelumnya ejen didaftar dengan runtime dan kemudian mesej dihantar kepada ejen yang menghasilkan output berikut:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multi ejen**. AutoGen menyokong penciptaan pelbagai ejen yang boleh bekerjasama untuk mencapai tugasan kompleks. Ejen boleh berkomunikasi, berkongsi maklumat, dan menyelaraskan tindakan mereka untuk menyelesaikan masalah dengan lebih cekap. Untuk mencipta sistem multi-ejen, anda boleh mendefinisikan jenis ejen yang berbeza dengan fungsi dan peranan khusus, seperti pengambilan data, analisis, pembuatan keputusan dan interaksi pengguna. Mari kita lihat bagaimana ciptaan sedemikian kelihatan supaya kita mendapat gambaran:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Contoh pengisytiharan Ejen
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Menggunakan jenis topik sebagai jenis ejen.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # pengisytiharan yang tinggal dipendekkan untuk ringkasan

    # Sembang kumpulan
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

    Dalam kod sebelumnya kami mempunyai `GroupChatManager` yang didaftarkan dengan runtime. Pengurus ini bertanggungjawab untuk menyelaraskan interaksi antara jenis ejen yang berbeza, seperti penulis, pelukis ilustrasi, editor, dan pengguna.

- **Runtime Ejen**. Rangka kerja menyediakan persekitaran runtime, membolehkan komunikasi antara ejen, menguruskan identiti dan kitar hayat mereka, dan menguatkuasakan sempadan keselamatan dan privasi. Ini bermakna anda boleh menjalankan ejen anda dalam persekitaran yang selamat dan terkawal, memastikan mereka boleh berinteraksi dengan selamat dan cekap. Terdapat dua runtime yang menarik perhatian:
  - **Runtime berdiri sendiri**. Ini adalah pilihan yang baik untuk aplikasi proses tunggal di mana semua ejen dilaksanakan dalam bahasa pengaturcaraan yang sama dan berjalan dalam proses yang sama. Berikut ialah ilustrasi bagaimana ia berfungsi:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Runtime berdiri sendiri</a>   
Tumpukan aplikasi

    *ejen berkomunikasi melalui mesej melalui runtime, dan runtime menguruskan kitar hayat ejen*

  - **Runtime ejen diedarkan**, sesuai untuk aplikasi berbilang proses di mana ejen mungkin dilaksanakan dalam bahasa pengaturcaraan yang berbeza dan berjalan pada mesin berbeza. Berikut ialah ilustrasi bagaimana ia berfungsi:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Runtime diedarkan</a>

## Semantic Kernel + Rangka Kerja Ejen

Semantic Kernel adalah SDK Orkestrasi AI siap perusahaan. Ia terdiri daripada penyambung AI dan memori, bersama dengan Rangka Kerja Ejen.

Mari mula dengan beberapa komponen teras:

- **Penyambung AI**: Ini adalah antara muka dengan perkhidmatan AI luaran dan sumber data untuk digunakan dalam Python dan C#.

  ```python
  # Kernel Semantik Python
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

    Di sini anda mempunyai contoh ringkas bagaimana anda boleh mencipta kernel dan menambah perkhidmatan penyelesaian chat. Semantic Kernel mewujudkan sambungan ke perkhidmatan AI luaran, dalam kes ini, Penyelesaian Chat Azure OpenAI.

- **Plugin**: Ini mengandungi fungsi yang boleh digunakan oleh aplikasi. Terdapat kedua-dua plugin siap dan plugin tersuai yang anda boleh cipta. Konsep berkaitan ialah "fungsi prompt." Daripada memberikan petunjuk bahasa semula jadi untuk panggilan fungsi, anda menyiarkan fungsi tertentu kepada model. Berdasarkan konteks chat semasa, model mungkin memilih untuk memanggil salah satu fungsi ini untuk melengkapkan permintaan atau pertanyaan. Berikut adalah contoh:

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

    Di sini, anda mula-mula mempunyai templat prompt `skPrompt` yang membenarkan ruang untuk pengguna memasukkan teks, `$userInput`. Kemudian anda cipta fungsi kernel `SummarizeText` dan import ke dalam kernel dengan nama plugin `SemanticFunctions`. Perhatikan nama fungsi yang membantu Semantic Kernel memahami apa yang fungsi itu lakukan dan bila ia perlu dipanggil.

- **Fungsi asli**: Terdapat juga fungsi asli yang boleh dipanggil terus oleh rangka kerja untuk menjalankan tugasan. Berikut adalah contoh fungsi sebegitu yang mengambil kandungan daripada fail:

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

- **Memori**: Merangkum dan memudahkan pengurusan konteks untuk aplikasi AI. Idea dengan memori adalah bahawa ini adalah sesuatu yang LLM perlu ketahui. Anda boleh menyimpan maklumat ini dalam stor vektor yang akhirnya menjadi pangkalan data dalam memori atau pangkalan data vektor atau yang serupa. Berikut adalah contoh senario yang sangat dipermudahkan di mana *fakta* ditambah ke dalam memori:

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

    Fakta-fakta ini kemudian disimpan dalam koleksi memori `SummarizedAzureDocs`. Ini adalah contoh yang sangat mudah, tetapi anda boleh lihat bagaimana anda boleh menyimpan maklumat dalam memori untuk digunakan oleh LLM.

Jadi itulah asas rangka kerja Semantic Kernel, bagaimana pula dengan Rangka Kerja Agen?

## Perkhidmatan Agen Azure AI

Perkhidmatan Agen Azure AI adalah penambahan terbaru, diperkenalkan di Microsoft Ignite 2024. Ia membolehkan pembangunan dan penyebaran agen AI dengan model yang lebih fleksibel, seperti memanggil terus LLM sumber terbuka seperti Llama 3, Mistral, dan Cohere.

Perkhidmatan Agen Azure AI menyediakan mekanisme keselamatan perusahaan yang lebih kukuh dan kaedah penyimpanan data, menjadikannya sesuai untuk aplikasi perusahaan.

Ia berfungsi terus dengan rangka kerja orkestrasi multi-agen seperti AutoGen dan Semantic Kernel.

Perkhidmatan ini kini dalam Pratonton Awam dan menyokong Python dan C# untuk membina agen.

Menggunakan Semantic Kernel Python, kita boleh membuat Agen Azure AI dengan plugin yang ditakrifkan pengguna:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Tentukan plugin contoh untuk sampel
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
        # Buat definisi ejen
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Buat Ejen AzureAI menggunakan klien dan definisi ejen yang ditakrifkan
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Cipta utas untuk menampung perbualan
        # Jika tiada utas disediakan, sebuah utas baru akan
        # dibuat dan dikembalikan dengan respons awal
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
                # Panggil ejen untuk utas yang ditentukan
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

### Konsep teras

Perkhidmatan Agen Azure AI mempunyai konsep teras berikut:

- **Agen**. Perkhidmatan Agen Azure AI berintegrasi dengan Microsoft Foundry. Dalam AI Foundry, Agen AI bertindak sebagai mikroservis "pintar" yang boleh digunakan untuk menjawab soalan (RAG), melaksanakan tindakan, atau mengautomasikan alur kerja sepenuhnya. Ia mencapai ini dengan menggabungkan kuasa model AI generatif dengan alat yang membolehkannya mengakses dan berinteraksi dengan sumber data dunia nyata. Berikut adalah contoh agen:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Dalam contoh ini, agen dicipta dengan model `gpt-4o-mini`, nama `my-agent`, dan arahan `You are helpful agent`. Agen ini dilengkapi dengan alat dan sumber untuk melaksanakan tugas tafsiran kod.

- **Thread dan mesej**. Thread adalah konsep penting lain. Ia mewakili perbualan atau interaksi antara agen dan pengguna. Thread boleh digunakan untuk mengesan kemajuan perbualan, menyimpan maklumat konteks, dan menguruskan keadaan interaksi. Berikut adalah contoh thread:

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

    Dalam kod sebelumnya, satu thread dicipta. Kemudian, satu mesej dihantar ke thread tersebut. Dengan memanggil `create_and_process_run`, agen diminta untuk melakukan kerja pada thread itu. Akhirnya, mesej diambil dan direkod untuk melihat respons agen. Mesej-mesej menunjukkan kemajuan perbualan antara pengguna dan agen. Penting juga untuk memahami bahawa mesej boleh dalam pelbagai jenis seperti teks, imej, atau fail; ini menunjukkan kerja agen seperti contohnya respons imej atau teks. Sebagai pembangun, anda boleh menggunakan maklumat ini untuk memproses respons lebih lanjut atau membentangkannya kepada pengguna.

- **Berintegrasi dengan rangka kerja AI lain**. Perkhidmatan Agen Azure AI boleh berinteraksi dengan rangka kerja lain seperti AutoGen dan Semantic Kernel, yang bermakna anda boleh membina sebahagian aplikasi anda dalam salah satu rangka kerja ini dan contohnya menggunakan Perkhidmatan Agen sebagai pengorkestrasian atau anda boleh membina semuanya dalam Perkhidmatan Agen.

**Kes Penggunaan**: Perkhidmatan Agen Azure AI direka untuk aplikasi perusahaan yang memerlukan penyebaran agen AI yang selamat, boleh diskala, dan fleksibel.

## Apakah perbezaan antara rangka kerja-rangka kerja ini?

Ini memang kedengaran ada banyak pertindihan antara rangka kerja ini, tetapi terdapat beberapa perbezaan utama dari segi reka bentuk, keupayaan, dan kes penggunaan sasaran:

- **AutoGen**: Adalah rangka kerja eksperimen yang menumpukan pada penyelidikan termaju tentang sistem multi-agen. Ia adalah tempat terbaik untuk bereksperimen dan membuat prototaip sistem multi-agen yang kompleks.
- **Semantic Kernel**: Adalah perpustakaan agen yang siap untuk pengeluaran bagi membina aplikasi agen berasaskan perusahaan. Menumpukan pada aplikasi agen berasaskan peristiwa yang diedarkan, membolehkan pelbagai LLM dan SLM, alat, dan corak reka bentuk agen tunggal/berbilang.
- **Perkhidmatan Agen Azure AI**: Adalah platform dan perkhidmatan penyebaran dalam Azure Foundry untuk agen. Ia menawarkan sambungan kepada perkhidmatan disokong oleh Azure Foundry seperti Azure OpenAI, Azure AI Search, Bing Search dan pelaksanaan kod.

Masih tidak pasti yang mana satu untuk dipilih?

### Kes Penggunaan

Mari kita lihat jika kami boleh membantu anda dengan meneliti beberapa kes penggunaan biasa:

> Q: Saya sedang bereksperimen, belajar dan membina aplikasi agen sebagai bukti konsep, dan saya mahu dapat membina dan bereksperimen dengan cepat
>

> A: AutoGen adalah pilihan yang baik untuk senario ini, kerana ia memberi tumpuan kepada aplikasi agen berasaskan peristiwa yang diedarkan dan menyokong corak reka bentuk multi-agen maju.

> Q: Apakah yang menjadikan AutoGen pilihan lebih baik berbanding Semantic Kernel dan Perkhidmatan Agen Azure AI untuk kes penggunaan ini?
>
> A: AutoGen direka khas untuk aplikasi agen berasaskan peristiwa yang diedarkan, menjadikannya sesuai untuk mengautomasikan penjanaan kod dan tugas analisis data. Ia menyediakan alat dan keupayaan yang diperlukan untuk membina sistem multi-agen yang kompleks dengan cekap.

> Q: Nampaknya Perkhidmatan Agen Azure AI juga boleh berfungsi di sini, ia mempunyai alat untuk penjanaan kod dan banyak lagi?

>
> A: Ya, Perkhidmatan Agen Azure AI adalah perkhidmatan platform untuk agen dan menambah keupayaan terbina dalam untuk pelbagai model, Azure AI Search, Bing Search dan Azure Functions. Ia memudahkan anda membina agen anda di Portal Foundry dan menyebarkannya secara berskala.

> Q: Saya masih keliru, berikan saya satu pilihan sahaja
>
> A: Pilihan terbaik adalah membina aplikasi anda di Semantic Kernel terlebih dahulu dan kemudian menggunakan Perkhidmatan Agen Azure AI untuk menyebarkan agen anda. Pendekatan ini membolehkan anda mengekalkan agen anda dengan mudah sambil memanfaatkan keupayaan untuk membina sistem multi-agen dalam Semantic Kernel. Selain itu, Semantic Kernel mempunyai penyambung dalam AutoGen, menjadikannya mudah untuk menggunakan kedua-dua rangka kerja bersama-sama.

Mari kita ringkaskan perbezaan utama dalam jadual:

| Rangka Kerja | Fokus | Konsep Teras | Kes Penggunaan |
| --- | --- | --- | --- |
| AutoGen | Aplikasi agen berasaskan peristiwa yang diedarkan | Agen, Personas, Fungsi, Data | Penjanaan kod, tugas analisis data |
| Semantic Kernel | Memahami dan menjana kandungan teks seperti manusia | Agen, Komponen Modular, Kolaborasi | Pemahaman bahasa semula jadi, penjanaan kandungan |
| Perkhidmatan Agen Azure AI | Model fleksibel, keselamatan perusahaan, Penjanaan kod, Panggilan alat | Modulasi, Kolaborasi, Orkestrasi Proses | Penyebaran agen AI yang selamat, boleh diskala dan fleksibel |

Apakah kes penggunaan ideal untuk setiap rangka kerja ini?

## Bolehkah saya mengintegrasi alat ekosistem Azure saya yang sedia ada secara langsung, atau adakah saya memerlukan penyelesaian berdiri sendiri?

Jawapannya ialah ya, anda boleh mengintegrasi alat ekosistem Azure sedia ada anda secara langsung dengan Perkhidmatan Agen Azure AI khususnya, ini kerana ia telah dibina untuk berfungsi lancar dengan perkhidmatan Azure lain. Anda boleh contohnya mengintegrasi Bing, Azure AI Search, dan Azure Functions. Terdapat juga integrasi mendalam dengan Microsoft Foundry.

Untuk AutoGen dan Semantic Kernel, anda juga boleh mengintegrasi dengan perkhidmatan Azure, tetapi mungkin memerlukan anda memanggil perkhidmatan Azure dari kod anda. Cara lain untuk mengintegrasi ialah menggunakan Azure SDK untuk berinteraksi dengan perkhidmatan Azure dari agen anda. Selain itu, seperti yang disebutkan, anda boleh gunakan Perkhidmatan Agen Azure AI sebagai pengorkestrasian untuk agen anda yang dibina dalam AutoGen atau Semantic Kernel yang memberikannya akses mudah ke ekosistem Azure.

## Kod Contoh

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Ada Lagi Soalan tentang Rangka Kerja Agen AI?

Sertai [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk berjumpa dengan pembelajar lain, hadir waktu pejabat dan dapatkan soalan anda berkenaan Agen AI dijawab.

## Rujukan

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Perkhidmatan Agen Azure AI</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel dan AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Perkhidmatan Agen Azure AI</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Menggunakan Perkhidmatan Agen Azure AI dengan AutoGen / Semantic Kernel untuk membina penyelesaian multi-agen</a>

## Pelajaran Sebelumnya

[Pengenalan kepada Agen AI dan Kes Penggunaan Agen](../01-intro-to-ai-agents/README.md)

## Pelajaran Seterusnya

[Memahami Corak Reka Bentuk Agenik](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk mencapai ketepatan, sila ambil maklum bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidakakuratan. Dokumen asal dalam bahasa asalnya hendaklah dianggap sebagai sumber yang sahih. Untuk maklumat penting, disyorkan menggunakan terjemahan profesional oleh manusia. Kami tidak bertanggungjawab atas sebarang salah faham atau salah tafsir yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->