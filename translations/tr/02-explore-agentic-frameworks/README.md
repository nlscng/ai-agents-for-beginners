[![Yapay Zeka Ajan Çerçevelerini Keşfetme](../../../translated_images/tr/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Yukarındaki görsele tıklayarak bu dersin videosunu izleyin)_

# Yapay Zeka Ajan Çerçevelerini Keşfedin

Yapay zeka ajan çerçeveleri, AI ajanlarının oluşturulmasını, dağıtılmasını ve yönetilmesini basitleştirmek için tasarlanmış yazılım platformlarıdır. Bu çerçeveler, geliştiricilere karmaşık AI sistemlerinin geliştirilmesini hızlandıran önceden oluşturulmuş bileşenler, soyutlamalar ve araçlar sağlar.

Bu çerçeveler, geliştiricilerin AI ajan geliştirmedeki ortak zorluklara standartlaştırılmış yaklaşımlar sunarak uygulamalarının benzersiz yönlerine odaklanmasına yardımcı olur. Ölçeklenebilirlik, erişilebilirlik ve verimlilik açısından AI sistemleri oluşturmayı geliştirirler.

## Giriş 

Bu ders şunları kapsayacaktır:

- Yapay Zeka Ajan Çerçeveleri nedir ve geliştiricilerin neler başarmasını sağlar?
- Takımlar ajanlarının yeteneklerini hızla nasıl prototipleyip yineleyebilir ve geliştirebilir?
- Microsoft tarafından oluşturulan <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> ve <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> tarafından yaratılan çerçeveler ve araçlar arasındaki farklar nelerdir?
- Mevcut Azure ekosistemi araçlarımı doğrudan entegre edebilir miyim, yoksa ayrı çözümler mi gereklidir?
- Azure AI Agents hizmeti nedir ve bu bana nasıl yardımcı oluyor?

## Öğrenme hedefleri

Bu dersin amaçları size şunları anlamada yardımcı olmaktır:

- Yapay Zeka Ajan Çerçevelerinin AI geliştirmedeki rolü.
- Yapay Zeka Ajan Çerçevelerinden yararlanarak akıllı ajanlar oluşturma.
- Yapay Zeka Ajan Çerçeveleri tarafından sağlanan temel yetenekler.
- AutoGen, Semantic Kernel ve Azure AI Agent Service arasındaki farklar.

## Yapay Zeka Ajan Çerçeveleri nedir ve geliştiricilerin neler yapmasını sağlar?

Geleneksel AI Çerçeveleri, AI'yı uygulamalarınıza entegre etmenize ve bu uygulamaları şu yollarla iyileştirmenize yardımcı olabilir:

- **Kişiselleştirme**: AI, kullanıcı davranışını ve tercihlerini analiz ederek kişiselleştirilmiş öneriler, içerik ve deneyimler sunabilir.
Örnek: Netflix gibi yayın hizmetleri, izleme geçmişine göre film ve diziler önererek kullanıcı etkileşimini ve memnuniyetini artırır.
- **Otomasyon ve Verimlilik**: AI, tekrarlayan görevleri otomatikleştirebilir, iş akışlarını düzene sokabilir ve operasyonel verimliliği artırabilir.
Örnek: Müşteri hizmetleri uygulamaları, sık sorulan soruları ele almak için AI destekli chatbot'lar kullanarak yanıt sürelerini azaltır ve insan temsilcilerin daha karmaşık konulara odaklanmasını sağlar.
- **Geliştirilmiş Kullanıcı Deneyimi**: AI, ses tanıma, doğal dil işleme ve tahmini metin gibi akıllı özellikler sunarak genel kullanıcı deneyimini iyileştirebilir.
Örnek: Siri ve Google Assistant gibi sanal asistanlar, sesli komutları anlamak ve yanıtlamak için AI kullanarak kullanıcıların cihazlarıyla etkileşimini kolaylaştırır.

### Hepsi kulağa harika geliyor, peki neden Yapay Zeka Ajan Çerçevesine ihtiyacımız var?

Yapay Zeka Ajan çerçeveleri, sadece AI çerçevelerinden daha fazlasını temsil eder. Kullanıcılarla, diğer ajanlarla ve çevreyle etkileşime girerek belirli hedeflere ulaşabilen akıllı ajanların oluşturulmasını mümkün kılmak üzere tasarlanmıştır. Bu ajanlar otonom davranış sergileyebilir, kararlar alabilir ve değişen koşullara uyum sağlayabilir. Yapay Zeka Ajan Çerçevelerinin sağladığı bazı temel yeteneklere bakalım:

- **Ajan İşbirliği ve Koordinasyonu**: Birden fazla AI ajanının birlikte çalışabilmesini, iletişim kurabilmesini ve karmaşık görevleri çözmek için koordinasyon sağlayabilmesini mümkün kılar.
- **Görev Otomasyonu ve Yönetimi**: Çok adımlı iş akışlarını otomatikleştirme, görev delegasyonu ve ajanlar arasında dinamik görev yönetimi mekanizmaları sağlar.
- **Bağlamsal Anlayış ve Uyarlanabilirlik**: Ajanlara bağlamı anlama, değişen ortamlara uyum sağlama ve gerçek zamanlı bilgilere dayanarak karar alma yeteneği kazandırır.

Özetle, ajanlar size daha fazlasını yapma, otomasyonu bir sonraki seviyeye taşıma, çevrelerinden öğrenen ve uyum sağlayan daha akıllı sistemler oluşturma imkânı verir.

## Ajanın yeteneklerini nasıl hızlıca prototipleyip yineleyebilir ve geliştirebilirim?

Bu alan hızla değişiyor, ancak çoğu Yapay Zeka Ajan Çerçevesinde hızlıca prototip oluşturmanıza ve yinelemenize yardımcı olan bazı ortak özellikler vardır; bunlar modül bileşenleri, işbirliği araçları ve gerçek zamanlı öğrenmedir. Bunlara daha yakından bakalım:

- **Modüler Bileşenleri Kullanın**: AI SDK'ları AI ve Bellek bağlayıcıları, doğal dil veya kod eklentileri kullanarak fonksiyon çağırma, istem (prompt) şablonları ve daha fazlası gibi önceden oluşturulmuş bileşenler sunar.
- **İşbirliği Araçlarından Yararlanın**: Ajanları belirli roller ve görevlerle tasarlayın; bu, işbirlikçi iş akışlarını test etmelerini ve iyileştirmelerini sağlar.
- **Gerçek Zamanlı Öğrenin**: Ajanların etkileşimlerden öğrenip davranışlarını dinamik olarak ayarladığı geri bildirim döngüleri uygulayın.

### Modüler Bileşenleri Kullanın

Semantic Kernel ve LangChain gibi SDK'lar AI bağlayıcıları, istem şablonları ve bellek yönetimi gibi önceden oluşturulmuş bileşenler sunar.

**Takımlar bunları nasıl kullanabilir**: Takımlar bu bileşenleri sıfırdan başlamak zorunda kalmadan hızlıca bir araya getirip işlevsel bir prototip oluşturabilir, bu da hızlı deney yapma ve yineleme imkânı sağlar.

**Uygulamada nasıl çalışır**: Bir kullanıcı girdisinden bilgi çıkarmak için önceden oluşturulmuş bir ayrıştırıcı (parser), verileri saklamak ve almak için bir bellek modülü ve kullanıcılarla etkileşim için bir istem üreticisi kullanabilirsiniz; bunların tümü sıfırdan inşa edilmeden kullanılabilir.

**Örnek kod**. Modelin kullanıcı girdisine yanıt vermesi için otomatik işlev çağırma kullanan önceden oluşturulmuş bir AI Bağlayıcısını Semantic Kernel Python ve .Net ile nasıl kullanabileceğinize dair örneklere bakalım:

``` python
# Semantic Kernel Python Örneği

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Sohbetin bağlamını tutmak için bir ChatHistory nesnesi tanımlayın
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Seyahat rezervasyonu yapmak için fonksiyon içeren bir örnek eklenti tanımlayın
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Kernel'i oluşturun
kernel = Kernel()

# Örnek eklentiyi Kernel nesnesine ekleyin
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Azure OpenAI AI Bağlantısını tanımlayın
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Modeli otomatik fonksiyon çağrısı ile yapılandırmak için istek ayarlarını tanımlayın
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Verilen sohbet geçmişi ve istek ayarları ile modele istekte bulunun
    # Kernel, modelin çağırmasını isteyeceği örneği içerir
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
    # Örnek AI Modeli Yanıtı: `1 Ocak 2025 tarihindeki New York uçuşunuz başarıyla rezerve edildi. İyi yolculuklar! ✈️🗽`

    # Modelin yanıtını sohbet geçmişi bağlamımıza ekleyin
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

Bu örnekten görebileceğiniz, kullanıcı girdisinden uçuş rezervasyon isteğinin kalkış yeri, varış yeri ve tarihi gibi ana bilgileri çıkarmak için önceden oluşturulmuş bir ayrıştırıcıdan nasıl yararlanabileceğinizdir. Bu modüler yaklaşım, yüksek seviyeli mantığa odaklanmanızı sağlar.

### İşbirliği Araçlarından Yararlanın

CrewAI, Microsoft AutoGen ve Semantic Kernel gibi çerçeveler, birlikte çalışabilen birden çok ajan oluşturmayı kolaylaştırır.

**Takımlar bunları nasıl kullanabilir**: Takımlar belirli rollere ve görevlere sahip ajanlar tasarlayabilir; bu, işbirlikçi iş akışlarını test etmelerini ve ince ayar yapmalarını ve genel sistem verimliliğini artırmalarını sağlar.

**Uygulamada nasıl çalışır**: Veri alma, analiz veya karar verme gibi uzmanlaşmış fonksiyonlara sahip ajanlardan oluşan bir ekip oluşturabilirsiniz. Bu ajanlar ortak bir hedefe ulaşmak için iletişim kurup bilgi paylaşabilirler; örneğin bir kullanıcı sorgusunu yanıtlamak veya bir görevi tamamlamak gibi.

**Örnek kod (AutoGen)**:

```python
# ajanlar oluşturuluyor, ardından sırayla birlikte çalışabilecekleri bir round robin programı oluşturuluyor

# Veri Alma Ajanı
# Veri Analizi Ajanı
# Karar Verme Ajanı

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

# kullanıcı "ONAYLA" dediğinde konuşma sona erer
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Bir betikte çalıştırılırken asyncio.run(...) kullanın.
await Console(stream)
```

Önceki kodda gördüğünüz, birden fazla ajanın birlikte çalışarak verileri analiz ettiği bir görevi nasıl oluşturabileceğinizdir. Her ajan belirli bir fonksiyonu yerine getirir ve görev, istenen sonuca ulaşmak için ajanların koordinasyonuyla yürütülür. Uzman rollere sahip özel ajanlar oluşturarak görev verimliliğini ve performansını artırabilirsiniz.

### Gerçek Zamanlı Öğrenme

Gelişmiş çerçeveler gerçek zamanlı bağlam anlayışı ve uyum sağlama yetenekleri sunar.

**Takımlar bunları nasıl kullanabilir**: Takımlar, ajanların etkileşimlerden öğrenip davranışlarını dinamik olarak ayarladığı geri bildirim döngüleri uygulayabilir; bu da yeteneklerin sürekli iyileştirilmesini ve rafine edilmesini sağlar.

**Uygulamada nasıl çalışır**: Ajanlar, kullanıcı geri bildirimlerini, çevresel verileri ve görev sonuçlarını analiz ederek bilgi tabanlarını güncelleyebilir, karar alma algoritmalarını ayarlayabilir ve zaman içinde performansı artırabilir. Bu yinelemeli öğrenme süreci, ajanların değişen koşullara ve kullanıcı tercihlerine uyum sağlamasını sağlayarak genel sistem etkinliğini artırır.

## AutoGen, Semantic Kernel ve Azure AI Agent Service çerçeveleri arasındaki farklar nelerdir?

Bu çerçeveleri karşılaştırmanın birçok yolu vardır, ancak tasarım, yetenekler ve hedef kullanım senaryoları açısından bazı temel farklılıklara bakalım:

## AutoGen

AutoGen, Microsoft Research'in AI Frontiers Lab tarafından geliştirilmiş açık kaynaklı bir çerçevedir. Olay güdümlü, dağıtılmış *ajanik* uygulamalara odaklanır; birden fazla LLM ve SLM, araçlar ve gelişmiş çok ajanlı tasarım desenlerini mümkün kılar.

AutoGen, çevresini algılayabilen, kararlar alabilen ve belirli hedeflere ulaşmak için eylemde bulunabilen otonom varlıklar olan ajan kavramı etrafında inşa edilmiştir. Ajanlar asenkron mesajlar aracılığıyla iletişim kurar; bu, onların bağımsız ve paralel olarak çalışmasına, sistem ölçeklenebilirliğinin ve yanıt verebilirliğinin artmasına olanak tanır.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Ajanlar aktör modeline dayanır</a>. Wikipedia'ya göre, bir aktör _eşzamanlı hesaplamanın temel yapı taşıdır. Aldığı bir mesaja yanıt olarak, bir aktör: yerel kararlar alabilir, daha fazla aktör oluşturabilir, daha fazla mesaj gönderebilir ve alınan bir sonraki mesaja nasıl yanıt verileceğini belirleyebilir_.

**Kullanım Durumları**: Kod üretiminin otomasyonu, veri analiz görevleri ve planlama ile araştırma işlevleri için özel ajanlar oluşturma.

İşte AutoGen'in bazı önemli temel kavramları:

- **Ajanlar**. Bir ajan bir yazılım varlığıdır ve:
  - **Mesajlar aracılığıyla iletişim kurar**, bu mesajlar eşzamanlı veya eşzamansız olabilir.
  - **Kendi durumunu korur**, bu durum gelen mesajlarla değiştirilebilir.
  - **Eylemler gerçekleştirir**; alınan mesajlara veya durumundaki değişikliklere yanıt olarak eylemler gerçekleştirir. Bu eylemler ajanın durumunu değiştirebilir ve mesaj kayıtlarını güncelleme, yeni mesaj gönderme, kod yürütme veya API çağrıları yapma gibi dışsal etkiler üretebilir.
    
    Burada kendi Chat yeteneklerine sahip bir ajan oluşturduğunuz kısa bir kod snippet'ine sahipsiniz:

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
    
    Önceki kodda, `MyAgent` oluşturulmuş ve `RoutedAgent`'den miras almıştır. Mesaj içeriğini yazdıran bir mesaj işleyicisi vardır ve ardından `AssistantAgent` delege kullanılarak bir yanıt gönderir. Özellikle `self._delegate`'e sohbet tamamlama işlemlerini gerçekleştirebilen önceden oluşturulmuş bir ajan olan `AssistantAgent` örneğini nasıl atadığımıza dikkat edin.


    Şimdi AutoGen'e bu ajan türünü bildirip programı başlatalım:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Arka planda mesaj işlemeye başla.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Önceki kodda ajanlar çalışma zamanına kaydedilir ve ardından ajana bir mesaj gönderilir; bu da aşağıdaki çıktıyı oluşturur:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Çoklu ajanlar**. AutoGen, birden fazla ajanın birlikte çalışarak karmaşık görevleri başarmasını destekler. Ajanlar iletişim kurabilir, bilgi paylaşabilir ve eylemlerini koordineli şekilde gerçekleştirerek problemleri daha verimli çözebilir. Çoklu ajan sistemi oluşturmak için veri alma, analiz, karar verme ve kullanıcı etkileşimi gibi uzmanlaşmış işlevlere ve rollere sahip farklı ajan türleri tanımlayabilirsiniz. Böyle bir oluşturmanın nasıl göründüğünü anlamak için şuna bakalım:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Bir Ajan tanımlama örneği
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Ajan tipi olarak konu türünün kullanılması.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # Geri kalan bildirimler kısalık için kısaltıldı

    # Grup sohbeti
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

    Önceki kodda çalışma zamanına kaydedilmiş bir `GroupChatManager`'ımız var. Bu yönetici, yazarlar, çizerler, editörler ve kullanıcılar gibi farklı ajan türleri arasındaki etkileşimleri koordine etmekten sorumludur.

- **Ajan Çalışma Zamanı**. Çerçeve, ajanlar arasındaki iletişimi sağlayan, kimliklerini ve yaşam döngülerini yöneten ve güvenlik ile gizlilik sınırlarını uygulayan bir çalışma zamanı ortamı sunar. Bu, ajanlarınızı güvenli ve kontrollü bir ortamda çalıştırabileceğiniz anlamına gelir. İlgilenilmesi gereken iki çalışma zamanı vardır:
  - **Bağımsız (Stand-alone) çalışma zamanı**. Tüm ajanların aynı programlama dilinde uygulandığı ve aynı süreçte çalıştığı tek işlemli uygulamalar için iyi bir seçenektir. İşleyişine ilişkin bir görselleştirme şu şekildedir:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Stand-alone runtime</a>   
Uygulama yığını

    *ajanlar çalışma zamanı aracılığıyla mesajlarla iletişim kurar ve çalışma zamanı ajanların yaşam döngüsünü yönetir*

  - **Dağıtık ajan çalışma zamanı**, ajanların farklı programlama dillerinde uygulanmış olabileceği ve farklı makinelerde çalışabileceği çok işlemlik uygulamalar için uygundur. İşleyişine ilişkin bir görselleştirme şu şekildedir:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distributed runtime</a>

## Semantic Kernel + Ajan Çerçevesi

Semantic Kernel, kurumsal seviyede hazır bir AI Orkestrasyon SDK'sıdır. AI ve bellek bağlayıcılarından oluşur ve ayrıca bir Ajan Çerçevesi içerir.

Önce bazı temel bileşenleri ele alalım:

- **AI Bağlayıcıları**: Hem Python hem de C# için harici AI hizmetleri ve veri kaynaklarıyla arayüz sağlayan bileşendir.

  ```python
  # Anlamsal Çekirdek Python
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

    Burada bir kernel oluşturup bir sohbet tamamlama servisi eklemenin basit bir örneğini görebilirsiniz. Semantic Kernel, bu durumda Azure OpenAI Chat Completion ile harici bir AI servisine bağlantı kurar.

- **Eklentiler (Plugins)**: Bunlar bir uygulamanın kullanabileceği işlevleri kapsülleyen yapılardır. Hem hazır eklentiler hem de sizin oluşturabileceğiniz özel eklentiler vardır. İlgili bir kavram "istem işlevleri"dir (prompt functions). Doğal dil ipuçları sağlamak yerine, belirli işlevleri modele yayınlarsınız. Mevcut sohbet bağlamına göre model, bir isteği veya sorguyu tamamlamak için bu işlevlerden birini çağırmayı seçebilir. İşte bir örnek:

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

    Burada önce kullanıcı için metin girmeye yer bırakan bir şablon istem `skPrompt` bulunur, `$userInput`. Ardından `SummarizeText` adlı kernel işlevini oluşturur ve `SemanticFunctions` eklenti adıyla kernela aktarırız. Semantic Kernel'in işlevin ne yaptığını ve ne zaman çağrılması gerektiğini anlamasına yardımcı olan işlev adına dikkat edin.

- **Native function (Yerel işlev)**: Çerçevenin görevi gerçekleştirmek için doğrudan çağırabileceği yerel işlevler de vardır. İşte bir dosyadan içerik alan böyle bir işlev örneği:

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

- **Bellek**: AI uygulamaları için bağlam yönetimini soyutlar ve basitleştirir. Bellekle ilgili fikir, bunun LLM'in bilmesi gereken bir şey olduğudur. Bu bilgiyi, bellekte bir veritabanı olan veya bir vektör veritabanına dönüşen bir vektör deposunda saklayabilirsiniz. İşte *olguların* belleğe eklendiği çok basitleştirilmiş bir senaryonun örneği:

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

    Bu bilgiler daha sonra bellek koleksiyonu `SummarizedAzureDocs` içinde saklanır. Bu çok basitleştirilmiş bir örnek, ancak LLM'nin kullanması için bilgileri bellekte nasıl saklayabileceğinizi görebilirsiniz.

Dolayısıyla bu Semantic Kernel çerçevesinin temelleriydi, peki Agent Framework ne durumda?

## Azure AI Agent Service

Azure AI Agent Service, Microsoft Ignite 2024'te tanıtılan daha yeni bir ektir. Llama 3, Mistral ve Cohere gibi açık kaynak LLM'leri doğrudan çağırmak gibi daha esnek modellerle yapay zeka ajanlarının geliştirilmesine ve dağıtılmasına olanak tanır.

Azure AI Agent Service, kurumsal uygulamalar için uygun hale getiren daha güçlü kurumsal güvenlik mekanizmaları ve veri depolama yöntemleri sağlar.

AutoGen ve Semantic Kernel gibi çoklu ajan orkestrasyon çerçeveleriyle kutudan çıktığı gibi çalışır.

Bu hizmet şu anda Public Preview aşamasındadır ve ajan oluşturmak için Python ve C#'ı desteklemektedir.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Örnek için bir örnek eklenti tanımlayın
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
        # Ajan tanımı oluşturun
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Tanımlanan istemci ve ajan tanımı kullanılarak AzureAI Ajanı oluşturun
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Konuşmayı tutacak bir konu oluşturun
        # Eğer bir konu sağlanmazsa, yeni bir konu
        # oluşturulacak ve ilk yanıtla birlikte döndürülecektir
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
                # Belirtilen konu için ajanı çağırın
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

### Temel kavramlar

Azure AI Agent Service'in aşağıdaki temel kavramları vardır:

- **Agent**. Azure AI Agent Service, Microsoft Foundry ile entegre olur. AI Foundry içinde bir AI Agent, soruları cevaplamak (RAG), eylemler gerçekleştirmek veya iş akışlarını tamamen otomatikleştirmek için kullanılabilen "akıllı" bir mikroservis görevi görür. Bunu, üretken AI modellerinin gücünü gerçek dünya veri kaynaklarına erişmesine ve onlarla etkileşime geçmesine izin veren araçlarla birleştirerek başarır. İşte bir ajan örneği:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Bu örnekte, `gpt-4o-mini` modeli, `my-agent` adı ve `You are helpful agent` talimatlarıyla bir ajan oluşturulur. Ajan, kod yorumlama görevlerini gerçekleştirebilmesi için araçlar ve kaynaklarla donatılmıştır.

- **Thread and messages**. Thread (konu) başka bir önemli kavramdır. Bu, bir ajan ile kullanıcı arasındaki konuşmayı veya etkileşimi temsil eder. Thread'ler bir konuşmanın ilerlemesini takip etmek, bağlam bilgisi saklamak ve etkileşimin durumunu yönetmek için kullanılabilir. İşte bir thread örneği:

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

    Önceki kodda bir thread oluşturulmuştur. Daha sonra, thread'e bir mesaj gönderilir. `create_and_process_run` çağrılarak, ajandan thread üzerinde iş yapması istenir. Son olarak, ajanın yanıtını görmek için mesajlar alınır ve günlüğe kaydedilir. Mesajlar, kullanıcı ile ajan arasındaki konuşmanın ilerlemesini gösterir. Ayrıca mesajların metin, resim veya dosya gibi farklı türlerde olabileceğini anlamak önemlidir; yani ajanın çalışması sonucunda örneğin bir resim ya da bir metin yanıtı oluşmuş olabilir. Bir geliştirici olarak, bu bilgiyi yanıtı daha fazla işlemek veya kullanıcıya sunmak için kullanabilirsiniz.

- **Integrates with other AI frameworks**. Azure AI Agent service, AutoGen ve Semantic Kernel gibi diğer çerçevelerle etkileşime girebilir; bu, uygulamanızın bir kısmını bu çerçevelerden birinde oluşturabileceğiniz ve örneğin Agent servisini bir orkestratör olarak kullanabileceğiniz veya her şeyi Agent servisi içinde oluşturabileceğiniz anlamına gelir.

**Kullanım Örnekleri**: Azure AI Agent Service, güvenli, ölçeklenebilir ve esnek AI ajan dağıtımı gerektiren kurumsal uygulamalar için tasarlanmıştır.

## Bu çerçeveler arasındaki fark nedir?
 
Görünüşe göre bu çerçeveler arasında çok fazla örtüşme var, ancak tasarım, yetenekler ve hedef kullanım durumları açısından bazı temel farklılıklar vardır:
 
- **AutoGen**: Çok ajanlı sistemlerde öncü araştırmalara odaklanan bir deneme çerçevesidir. Karmaşık çok ajanlı sistemleri denemek ve prototiplemek için en iyi yerdir.
- **Semantic Kernel**: Kurumsal ajanik uygulamalar oluşturmak için üretime hazır bir ajan kütüphanesidir. Olay güdümlü, dağıtık ajanik uygulamalara odaklanır; birden fazla LLM ve SLM, araçlar ve tekli/çoklu ajan tasarım desenlerini etkinleştirir.
- **Azure AI Agent Service**: Ajanlar için Azure Foundry'de bir platform ve dağıtım servisidir. Azure OpenAI, Azure AI Search, Bing Search ve kod yürütme gibi Foundry tarafından desteklenen hizmetlere bağlantı kurma desteği sunar.
 
Hangi seçeneği seçeceğinizden hâlâ emin değil misiniz?

### Kullanım Örnekleri
 
Bazı yaygın kullanım durumlarına göz atarak size yardımcı olup olamayacağımıza bakalım:
 
> Q: Deney yapıyorum, öğreniyorum ve kanıt kavramı uygulamaları (POC) inşa ediyorum ve hızlıca oluşturup denemek istiyorum
>

>A: Bu senaryo için AutoGen iyi bir seçim olur; AutoGen olay güdümlü, dağıtık ajanik uygulamalara odaklanır ve gelişmiş çoklu ajan tasarım desenlerini destekler.

> Q: Bu kullanım durumu için AutoGen'i Semantic Kernel ve Azure AI Agent Service'e göre daha iyi yapan nedir?
>
> A: AutoGen, özellikle olay güdümlü, dağıtık ajanik uygulamalar için tasarlanmıştır; bu da onu kod üretimi ve veri analiz görevlerini otomatikleştirmeye uygun hale getirir. Karmaşık çoklu ajan sistemlerini verimli bir şekilde oluşturmak için gerekli araçları ve yetenekleri sağlar.

>Q: Azure AI Agent Service burada da işe yarayabilir gibi görünüyor, kod üretimi ve daha fazlası için araçları var değil mi?

>
> A: Evet, Azure AI Agent Service ajanlar için bir platform hizmetidir ve birden fazla model, Azure AI Search, Bing Search ve Azure Functions için yerleşik yetenekler ekler. Foundry Portal'da ajanlarınızı kolayca oluşturmanızı ve ölçeklenebilir şekilde dağıtmanızı sağlar.
 
> Q: Hâlâ kafam karışık, bana sadece bir seçenek ver
>
> A: Harika bir seçenek önce uygulamanızı Semantic Kernel'de oluşturmak ve ardından ajanınızı dağıtmak için Azure AI Agent Service'i kullanmaktır. Bu yaklaşım, ajanlarınızı kolayca kalıcı hale getirirken Semantic Kernel'de çoklu ajan sistemleri oluşturma gücünden yararlanmanıza olanak tanır. Ayrıca, Semantic Kernel'in AutoGen'de bir konektörü olduğu için her iki çerçeveyi birlikte kullanmak kolaydır.
 
Ana farkları bir tabloda özetleyelim:

| Framework | Odak | Temel Kavramlar | Kullanım Örnekleri |
| --- | --- | --- | --- |
| AutoGen | Olay güdümlü, dağıtık ajanik uygulamalar | Agents, Personas, Functions, Data | Kod üretimi, veri analiz görevleri |
| Semantic Kernel | İnsan benzeri metin içeriğini anlama ve üretme | Agents, Modular Components, Collaboration | Doğal dil anlama, içerik üretimi |
| Azure AI Agent Service | Esnek modeller, kurumsal güvenlik, Kod üretimi, Araç çağırma | Modularity, Collaboration, Process Orchestration | Güvenli, ölçeklenebilir ve esnek AI ajan dağıtımı |

Bu çerçevelerin her biri için ideal kullanım durumu nedir?

## Mevcut Azure ekosistem araçlarımı doğrudan entegre edebilir miyim, yoksa bağımsız çözümler mi gerekiyor?

Cevap evet, özellikle Azure AI Agent Service ile mevcut Azure ekosistem araçlarınızı doğrudan entegre edebilirsiniz; bunun nedeni bu servisin diğer Azure hizmetleriyle sorunsuz çalışacak şekilde inşa edilmiş olmasıdır. Örneğin Bing, Azure AI Search ve Azure Functions'ı entegre edebilirsiniz. Ayrıca Microsoft Foundry ile derin entegrasyon vardır.

AutoGen ve Semantic Kernel için de Azure hizmetleriyle entegrasyon yapabilirsiniz, ancak bunlar genellikle kodunuzdan Azure hizmetlerini çağırmanızı gerektirebilir. Entegre etmenin bir diğer yolu, ajanlarınızdan Azure hizmetleriyle etkileşim kurmak için Azure SDK'larını kullanmaktır. Ek olarak, daha önce bahsedildiği gibi, AutoGen veya Semantic Kernel'de oluşturduğunuz ajanlar için bir orkestratör olarak Azure AI Agent Service'i kullanabilirsiniz; bu da Azure ekosistemine kolay erişim sağlar.

## Örnek Kodlar

- Python: [Ajan Çerçevesi](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Ajan Çerçevesi](./code_samples/02-dotnet-agent-framework.md)

## AI Agent Frameworkleri hakkında daha fazla sorum mu var?

Diğer öğrenenlerle tanışmak, ofis saatlerine katılmak ve AI Ajanlarıyla ilgili sorularınıza yanıt almak için [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)'a katılın.

## Referanslar

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel ve AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Ajan Çerçevesi</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Ajan Çerçevesi</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent servisi</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">AutoGen / Semantic Kernel ile Çok Ajanlı Bir Çözüm Oluşturmak İçin Azure AI Agent Service'in Kullanımı</a>

## Önceki Ders

[AI Ajanlarına ve Ajan Kullanım Durumlarına Giriş](../01-intro-to-ai-agents/README.md)

## Sonraki Ders

[Ajanik Tasarım Desenlerini Anlamak](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Sorumluluk Reddi**:
Bu belge, yapay zeka çeviri hizmeti [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstermemize rağmen, otomatik çevirilerin hatalar veya yanlışlıklar içerebileceğini lütfen unutmayın. Orijinal dilindeki belge yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanımı sonucunda ortaya çıkabilecek herhangi bir yanlış anlama veya yanlış yorumdan sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->