[![İyi AI Ajanları Nasıl Tasarlanır](../../../translated_images/tr/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Bu dersin videosunu görüntülemek için yukarıdaki resme tıklayın)_

# Araç Kullanımı Tasarım Deseni

Araçlar ilginçtir çünkü AI ajanlarının daha geniş bir yetenek yelpazesine sahip olmalarını sağlar. Ajanın gerçekleştirebileceği sınırlı sayıda eylem yerine, bir araç ekleyerek, ajan artık çok çeşitli eylemler gerçekleştirebilir. Bu bölümde, AI ajanlarının hedeflerine ulaşmak için belirli araçları nasıl kullanabileceğini tanımlayan Araç Kullanımı Tasarım Deseni'ne bakacağız.

## Giriş

Bu derste şu soruları yanıtlamaya çalışıyoruz:

- Araç kullanımı tasarım deseni nedir?
- Hangi kullanım durumlarına uygulanabilir?
- Tasarım desenini uygulamak için gerekli öğeler/yapı taşları nelerdir?
- Güvenilir AI ajanları oluşturmak için Araç Kullanımı Tasarım Deseni kullanırken özel dikkate alınması gerekenler nelerdir?

## Öğrenme Hedefleri

Bu dersi tamamladıktan sonra şunları yapabileceksiniz:

- Araç Kullanımı Tasarım Deseni'ni ve amacını tanımlamak.
- Araç Kullanımı Tasarım Deseni'nin uygulanabileceği kullanım durumlarını belirlemek.
- Tasarım desenini uygulamak için gereken temel öğeleri anlamak.
- Bu tasarım desenini kullanan AI ajanlarında güvenilirliği sağlamaya yönelik dikkate alınması gerekenleri fark etmek.

## Araç Kullanımı Tasarım Deseni Nedir?

**Araç Kullanımı Tasarım Deseni**, Büyük Dil Modellerine (LLM) belirli hedeflere ulaşmak için harici araçlarla etkileşim kurma yeteneği kazandırmaya odaklanır. Araçlar, bir ajanın eylemler gerçekleştirmek için çalıştırabileceği koddur. Bir araç basit bir hesap makinesi fonksiyonu olabileceği gibi, hisse senedi fiyatı sorgulama veya hava durumu tahmini gibi üçüncü parti bir servise yapılan API çağrısı da olabilir. AI ajanları bağlamında, araçlar **model tarafından oluşturulan fonksiyon çağrılarına** yanıt olarak ajanlar tarafından yürütülmek üzere tasarlanır.

## Hangi kullanım durumlarına uygulanabilir?

AI Ajanları, karmaşık görevleri tamamlamak, bilgi almak veya karar vermek için araçlardan yararlanabilir. Araç kullanımı tasarım deseni, veri tabanları, web servisleri veya kod yorumlayıcılarla dinamik etkileşim gerektiren senaryolarda sıklıkla kullanılır. Bu yetenek, aşağıdakiler de dahil olmak üzere birçok farklı kullanım durumu için yararlıdır:

- **Dinamik Bilgi Alımı:** Ajanlar, güncel verileri almak için dış API'lere veya veri tabanlarına sorgu yapabilir (örneğin; SQLite veri tabanını veri analizi için sorgulamak, hisse senedi fiyatları veya hava durumu bilgileri almak).
- **Kod Yürütme ve Yorumlama:** Ajanlar matematiksel problemleri çözmek, raporlar oluşturmak veya simülasyonlar yapmak için kod veya betikleri çalıştırabilir.
- **İş Akışı Otomasyonu:** Görev zamanlayıcılar, e-posta servisleri veya veri hatları gibi araçları entegre ederek tekrarlayan veya çok adımlı iş akışlarını otomatikleştirebilir.
- **Müşteri Desteği:** Ajanlar, kullanıcı sorgularını çözmek için CRM sistemleri, ticket platformları veya bilgi tabanlarıyla etkileşime geçebilir.
- **İçerik Üretme ve Düzenleme:** Ajanlar, dilbilgisi denetleyicileri, metin özetleyiciler veya içerik güvenliği değerlendiricileri gibi araçları içerik oluşturma görevlerinde kullanabilir.

## Araç kullanımı tasarım desenini uygulamak için gereken öğeler/yapı taşları nelerdir?

Bu yapı taşları, AI ajanının çok çeşitli görevleri gerçekleştirmesine olanak tanır. Araç Kullanımı Tasarım Deseni'ni uygulamak için gerekli temel öğelere bakalım:

- **Fonksiyon/Araç Şemaları:** Mevcut araçların fonksiyon adı, amacı, gereken parametreler ve beklenen çıktılar dahil olmak üzere ayrıntılı tanımları. Bu şemalar, LLM'nin hangi araçların mevcut olduğunu ve geçerli istekleri nasıl oluşturacağını anlamasını sağlar.

- **Fonksiyon Yürütme Mantığı:** Araçların ne zaman ve nasıl çağrılacağını belirler; kullanıcının niyeti ve konuşma bağlamına göre planlayıcı modüller, yönlendirme mekanizmaları veya koşullu akışlar içerebilir.

- **Mesaj Yönetim Sistemi:** Kullanıcı girdileri, LLM yanıtları, araç çağrıları ve araç çıktıları arasındaki konuşma akışını yönetir.

- **Araç Entegrasyon Çerçevesi:** Basit fonksiyonlar veya karmaşık harici servisler olsun ajanın çeşitli araçlara bağlanmasını sağlayan altyapı.

- **Hata Yönetimi ve Doğrulama:** Araç yürütme hatalarını ele alma, parametreleri doğrulama ve beklenmeyen yanıtları yönetme mekanizmaları.

- **Durum Yönetimi:** Çok turlu etkileşimlerde tutarlılığı sağlamak için konuşma bağlamını, önceki araç etkileşimlerini ve kalıcı verileri izler.

Şimdi, Fonksiyon/Araç Çağrısına daha detaylı bakalım.

### Fonksiyon/Araç Çağrısı

Fonksiyon çağrısı, Büyük Dil Modellerinin (LLM) araçlarla etkileşimini sağlayan birincil yöntemdir. 'Fonksiyon' ve 'Araç' terimleri sıklıkla birbirinin yerine kullanılır çünkü 'fonksiyonlar' (yeniden kullanılabilir kod blokları) ajanların görevleri yerine getirmek için kullandığı 'araçlardır'. Bir fonksiyonun kodu çağrılabilmesi için, bir LLM kullanıcının isteğini fonksiyonun tanımıyla karşılaştırmalıdır. Bunu yapmak için mevcut tüm fonksiyonların tanımlarını içeren bir şema LLM'ye gönderilir. LLM ardından göreve en uygun fonksiyonu seçer ve fonksiyonun adını ile argümanlarını döner. Seçilen fonksiyon çağrılır, yanıtı LLM'ye iletilir ve LLM bu bilgiyi kullanarak kullanıcının isteğine yanıt verir.

Geliştiricilerin ajanlar için fonksiyon çağrısını uygulayabilmesi için şunlara ihtiyacı olacaktır:

1. Fonksiyon çağrısını destekleyen bir LLM modeli
2. Fonksiyon tanımlarını içeren bir şema
3. Tanımlanan her fonksiyon için kod

Şimdi, bir şehirdeki mevcut saati alma örneğini kullanarak gösterebiliriz:

1. **Fonksiyon çağrısını destekleyen bir LLM'yi başlatın:**

    Tüm modeller fonksiyon çağrısını desteklemez, bu yüzden kullandığınız LLM'nin desteklediğini kontrol etmek önemlidir. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> fonksiyon çağrısını destekler. Öncelikle Azure OpenAI istemcisini başlatabiliriz.

    ```python
    # Azure OpenAI istemcisini başlatın
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Bir Fonksiyon Şeması oluşturun:**

    Sonra, fonksiyon adı, fonksiyonun ne yaptığına dair açıklama ve fonksiyon parametrelerinin adları ve açıklamalarını içeren bir JSON şeması tanımlayacağız.
    Ardından bu şemayı, daha önce oluşturduğumuz istemciye ve kullanıcının San Francisco'daki saati öğrenme isteğine göndereceğiz. Önemli olan nokta, **bir araç çağrısı** döndürüldüğüdür, **soruya verilen nihai cevap değil**. Yukarıda belirtildiği gibi, LLM göreve seçtiği fonksiyonun adını ve ona geçilecek argümanları döner.

    ```python
    # Modelin okuması için fonksiyon açıklaması
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
  
    # Başlangıç kullanıcı mesajı
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # İlk API çağrısı: Modelden fonksiyonu kullanmasını isteyin
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Modelin yanıtını işleyin
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Görevi yürütmek için gerekli fonksiyon kodu:**

    Artık LLM hangi fonksiyonun çalıştırılması gerektiğini seçtiğine göre, görevi gerçekleştiren kod uygulanmalı ve çalıştırılmalıdır.
    Python'da mevcut saati alma kodunu uygulayabiliriz. Ayrıca, sonucun alınması için response_message'dan fonksiyon adı ve argümanların çıkarılması için kullanılan kodu yazmamız gerekecek.

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
     # Fonksiyon çağrılarını yönet
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
  
      # İkinci API çağrısı: Modelden son cevabı al
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

Fonksiyon çağrısı, neredeyse tüm ajan araç kullanımı tasarımının kalbindedir; ancak sıfırdan uygulamak bazen zor olabilir. 
[2. Derste](../../../02-explore-agentic-frameworks) öğrendiğimiz gibi, agentik çerçeveler, araç kullanımını uygulamak için önceden hazırlanmış yapı taşları sağlar.
 
## Araç Kullanımı Örnekleri ile Agentik Çerçeveler

Farklı agentik çerçeveler kullanarak Araç Kullanımı Tasarım Deseni'ni nasıl uygulayabileceğinize dair bazı örnekler:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a>, Büyük Dil Modelleri (LLM) ile çalışan .NET, Python ve Java geliştiricileri için açık kaynak kodlu bir AI çerçevesidir. Fonksiyon çağrısını, fonksiyonlarınızı ve parametrelerini otomatik olarak adlandırma işlemi olarak bilinen <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">seri hale getirme</a> işlemi ile kolaylaştırır. Ayrıca model ile kodunuz arasındaki gidip gelmeleri de yönetir. Semantic Kernel gibi bir agentik çerçeve kullanmanın diğer avantajı, <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> ve <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a> gibi önceden hazırlanmış araçlara erişim imkanı sunmasıdır.

Aşağıdaki diyagram Semantic Kernel ile fonksiyon çağrısı sürecini göstermektedir:

![fonksiyon çağrısı](../../../translated_images/tr/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernel'da fonksiyonlar/araçlar <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Eklentiler</a> olarak adlandırılır. Daha önce gördüğümüz `get_current_time` fonksiyonunu, içinde fonksiyonun bulunduğu bir sınıfa dönüştürerek eklenti haline getirebiliriz. Ayrıca fonksiyonun açıklamasını alan `kernel_function` dekoratörünü içe aktarabiliriz. GetCurrentTimePlugin ile bir kernel oluşturduğunuzda kernel, fonksiyonu ve parametrelerini otomatik olarak seri hale getirir, böylece LLM'ye gönderilecek şema oluşturulur.

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

# Çekirdeği oluştur
kernel = Kernel()

# Eklentiyi oluştur
get_current_time_plugin = GetCurrentTimePlugin(location)

# Eklentiyi çekirdeğe ekle
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a>, geliştiricilerin temel bilgi işlem ve depolama kaynaklarını yönetmeden yüksek kaliteli, genişletilebilir AI ajanları güvenle geliştirmelerine, dağıtmalarına ve ölçeklendirmelerine olanak sağlayan yeni bir agentik çerçevedir. Özellikle kurumsal uygulamalar için kullanışlıdır çünkü tamamen yönetilen ve kurumsal düzeyde güvenlik sunan bir hizmettir.

LLM API ile doğrudan geliştirme ile karşılaştırıldığında Azure AI Agent Service bazı avantajlar sağlar, bunlar arasında:

- Otomatik araç çağrısı – bir araç çağrısını ayrıştırma, aracı çalıştırma ve yanıtı işleme gerekmeksizin; tümü artık sunucu tarafında gerçekleştirilir.
- Güvenle yönetilen veri – kendi konuşma durumunuzu yönetmek yerine, gerekli tüm bilgileri saklamak için thread'lere güvenebilirsiniz.
- Hazır araçlar – Bing, Azure AI Search ve Azure Functions gibi veri kaynaklarınızla etkileşim için kullanabileceğiniz araçlar.

Azure AI Agent Service'deki araçlar iki kategoriye ayrılabilir:

1. Bilgi Araçları:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing Arama ile Dayanak</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Dosya Araması</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Eylem Araçları:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Fonksiyon Çağrısı</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Kod Yorumlayıcı</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI tanımlı araçlar</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure İşlevleri</a>

Agent Service, bu araçların birlikte bir `araç seti` olarak kullanılmasına olanak tanır. Ayrıca belirli bir konuşmadan gelen mesaj geçmişini takip eden `thread`leri kullanır.

Contoso adlı bir şirkette satış temsilcisi olduğunuzu hayal edin. Satış verileriniz hakkında soruları cevaplayabilen bir konuşma ajanı geliştirmek istiyorsunuz.

Aşağıdaki görsel, Azure AI Agent Service kullanarak satış verilerinizi nasıl analiz edebileceğinizi göstermektedir:

![Agent Service Uygulamada](../../../translated_images/tr/agent-service-in-action.34fb465c9a84659e.webp)

Bu araçlardan herhangi birini hizmetle kullanmak için bir istemci oluşturup bir araç veya araç seti tanımlayabiliriz. Pratikte bunu uygulamak için aşağıdaki Python kodunu kullanabiliriz. LLM, araç setine bakarak kullanıcı tarafından oluşturulan `fetch_sales_data_using_sqlite_query` fonksiyonunu mu yoksa önceden hazırlanmış Kod Yorumlayıcıyı mı kullanacağına karar verecektir.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_functions.py dosyasında bulunan fetch_sales_data_using_sqlite_query fonksiyonu.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Araç setini başlat
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query fonksiyonu ile fonksiyon çağırma ajanını başlat ve araç setine ekle
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Kod Yorumlayıcı aracını başlat ve araç setine ekle.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Güvenilir AI ajanları oluşturmak için Araç Kullanımı Tasarım Deseni kullanırken özel dikkat edilmesi gerekenler nelerdir?

LLM tarafından dinamik oluşturulan SQL ile ilgili yaygın bir endişe, özellikle SQL enjeksiyonu veya veritabanını silme ya da değiştirme gibi kötü niyetli eylem riskleri üzerine güvenliktir. Bu endişeler geçerli olsa da, veritabanı erişim izinlerinin doğru yapılandırılmasıyla etkin şekilde azaltılabilir. Çoğu veritabanı için bu, veritabanını salt okunur olarak yapılandırmayı içerir. PostgreSQL veya Azure SQL gibi veritabanı servislerinde uygulamanın salt okunur (SELECT) rolüne atanması gerekir.

Uygulamayı güvenli bir ortamda çalıştırmak korumayı artırır. Kurumsal senaryolarda, veriler tipik olarak operasyonel sistemlerden okunabilir bir şema ile hazırlanan salt okunur veri tabanı veya veri ambarına çıkarılıp dönüştürülür. Bu yöntem verilerin güvenli, performans ve erişilebilirlik açısından optimize edilmesini sağlar ve uygulamanın sınırlı, salt okunur erişime sahip olmasını garanti eder.

## Örnek Kodlar
- Python: [Agent Çerçevesi](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Çerçevesi](./code_samples/04-dotnet-agent-framework.md)

## Araç Kullanımı Tasarım Desenleri Hakkında Daha Fazla Sorunuz mu Var?

Diğer öğrenenlerle tanışmak, ofis saatlerine katılmak ve AI Agent sorularınızı yanıtlamak için [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)’a katılın.

## Ek Kaynaklar

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Servis Atölyesi</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Çoklu Agent Atölyesi</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Fonksiyon Çağırma Eğitimi</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Kod Yorumlayıcı</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Araçları</a>

## Önceki Ders

[Agentik Tasarım Desenlerini Anlamak](../03-agentic-design-patterns/README.md)

## Sonraki Ders

[Agentik RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Feragatname**:  
Bu belge, yapay zekâ çeviri hizmeti [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstersek de, otomatik çevirilerin hata veya yanlışlık içerebileceğini lütfen unutmayınız. Orijinal belge, kendi dilinde yetkin kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi tavsiye edilir. Bu çevirinin kullanımı nedeniyle oluşabilecek herhangi bir yanlış anlama veya yanlış yorumdan sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->