# Microsoft Agent Framework'ü Keşfetmek

![Agent Framework](../../../translated_images/tr/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Giriş

Bu ders şunları kapsayacaktır:

- Microsoft Agent Framework'ü Anlama: Temel Özellikler ve Değer  
- Microsoft Agent Framework'ün Temel Kavramlarını Keşfetme
- MAF'yi Semantic Kernel ve AutoGen ile Karşılaştırma: Geçiş Rehberi

## Öğrenme Hedefleri

Bu dersi tamamladıktan sonra şunları bileceksiniz:

- Microsoft Agent Framework kullanarak Üretime Hazır AI Ajanları oluşturma
- Microsoft Agent Framework'ün temel özelliklerini Ajanik Kullanım Senaryolarınıza uygulama
- Mevcut Ajanik çerçeveleri ve araçları taşıma ve entegre etme  

## Kod Örnekleri 

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) için kod örnekleri bu depoda `xx-python-agent-framework` ve `xx-dotnet-agent-framework` dosyaları altında bulunabilir.

## Microsoft Agent Framework'ü Anlamak

![Framework Intro](../../../translated_images/tr/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok), Semantic Kernel ve AutoGen'den elde edilen deneyim ve öğrenimler üzerine inşa edilmiştir. Üretim ve araştırma ortamlarında görülen çok çeşitli ajan kullanım senaryolarına hitap etmek için esneklik sunar:

- Adım adım iş akışlarının gerektiği senaryolarda **Sıralı Ajan orkestrasyonu**.
- Ajanların aynı anda görevleri tamamlaması gereken senaryolarda **Eşzamanlı orkestrasyon**.
- Ajanların bir görev üzerinde birlikte işbirliği yapabildiği senaryolarda **Grup sohbeti orkestrasyonu**.
- Alt görevler tamamlandıkça ajanların görevleri birbirine devrettiği senaryolarda **Devir orkestrasyonu**.
- Bir yönetici ajanın görev listesi oluşturup değiştirdiği ve alt ajanların görevi tamamlamasını koordine ettiği senaryolarda **Manyetik orkestrasyon**.

Üretimde AI Ajanları sunmak için MAF ayrıca şunları içerir:

- AI Ajanın her eyleminin, araç çağrısı, orkestrasyon adımları, mantık akışları ve Microsoft Foundry panoları aracılığıyla performans izlemeyi içeren **OpenTelemetry kullanarak gözlemlenebilirlik**.
- Güvenlik kontrolleri, rol tabanlı erişim, özel veri işleme ve yerleşik içerik güvenliği gibi özellikleri içeren Microsoft Foundry üzerinde ajanların yerel olarak barındırılması yoluyla **Güvenlik**.
- Ajan iş parçacıkları ve iş akışlarının duraklatılması, devam ettirilmesi ve hatalardan kurtarılması yoluyla uzun süreli süreçlere olanak veren **Dayanıklılık**.
- Görevlerin insan onayı gerektirdiği iş akışlarının desteklendiği **Kontrol**.

Microsoft Agent Framework ayrıca birlikte çalışabilirliği hedefler:

- **Bulut bağımsızlığı** - Ajanlar konteynerlerde, yerel ortamda ve birden çok farklı bulut üzerinde çalışabilir.
- **Sağlayıcı bağımsızlığı** - Ajanlar sizin tercih ettiğiniz SDK ile, Azure OpenAI ve OpenAI dahil olmak üzere oluşturulabilir.
- **Açık Standartların Entegrasyonu** - Ajanlar, diğer ajanları ve araçları keşfetmek ve kullanmak için Agent-to-Agent (A2A) ve Model Context Protocol (MCP) gibi protokolleri kullanabilir.
- **Eklentiler ve Bağlayıcılar** - Microsoft Fabric, SharePoint, Pinecone ve Qdrant gibi veri ve bellek hizmetlerine bağlantılar yapılabilir.

Bu özelliklerin Microsoft Agent Framework'ün bazı temel kavramlarına nasıl uygulandığına bakalım.

## Microsoft Agent Framework'ün Temel Kavramları

### Ajanlar

![Agent Framework](../../../translated_images/tr/agent-components.410a06daf87b4fef.webp)

**Ajan Oluşturma**

Ajan oluşturma, çıkarım hizmeti (LLM Sağlayıcısı), AI Ajanın izleyeceği bir dizi talimat ve atanmış bir `name` tanımlanarak yapılır:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Yukarıda `Azure OpenAI` kullanılıyor ancak ajanlar `Microsoft Foundry Agent Service` gibi çeşitli hizmetler kullanılarak da oluşturulabilir:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` API'leri

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

ya da A2A protokolü kullanarak uzak ajanlar:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Ajanları Çalıştırma**

Ajanlar, akışsız veya akış yanıtları için sırasıyla `.run` veya `.run_stream` metodları kullanılarak çalıştırılır.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Her ajan çalıştırma, ajan tarafından kullanılan `max_tokens`, çağrılabilecek `tools` ve hatta ajan için kullanılan `model` gibi parametreleri özelleştirmek için de seçeneklere sahip olabilir.

Bu, kullanıcı görevinin tamamlanması için belirli model veya araçların gerekmesi durumlarında faydalıdır.

**Araçlar**

Araçlar, hem ajan tanımlanırken:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Bir ChatAgent doğrudan oluşturulurken

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

hem de ajan çalıştırılırken tanımlanabilir:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Bu çalışma için sağlanan araç )
```

**Ajan İş Parçacıkları**

Ajan İş Parçacıkları çok tur sohbetleri yönetmek için kullanılır. İş parçacıkları şunlarla oluşturulabilir:

- Zaman içinde iş parçacığının kaydedilmesini sağlayan `get_new_thread()` kullanarak
- Bir ajan çalıştırılırken otomatik bir iş parçacığı oluşturularak ve sadece mevcut çalışma süresi boyunca iş parçacığının sürmesi şeklinde.

Bir iş parçacığı oluşturmak için kod şöyle görünür:

```python
# Yeni bir iş parçacığı oluştur.
thread = agent.get_new_thread() # Ajanı iş parçacığı ile çalıştır.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Sonra iş parçacığını daha sonra kullanmak üzere seri hale getirebilirsiniz:

```python
# Yeni bir iş parçacığı oluştur.
thread = agent.get_new_thread() 

# İş parçacığı ile ajanı çalıştır.

response = await agent.run("Hello, how are you?", thread=thread) 

# Depolama için iş parçacığını serileştir.

serialized_thread = await thread.serialize() 

# Depolamadan yüklendikten sonra iş parçacığı durumunu serileştirmeden çıkar.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Ajan Arayüz Yazılımı (Middleware)**

Ajanlar, kullanıcıların görevlerini tamamlamak için araçlar ve LLM'lerle etkileşime girerler. Belirli senaryolarda, bu etkileşimler arasında işlem yapmak veya izlemek isteyebiliriz. Ajan arayüz yazılımı bunu sağlar:

*Fonksiyon Arayüz Yazılımı*

Bu arayüz yazılımı, ajan ile çağıracağı fonksiyon/araç arasındaki bir eylemin yürütülmesine izin verir. Buna örnek olarak, fonksiyon çağrısı üzerinde günlükleme yapmak isteyebilirsiniz.

Aşağıdaki kodda `next`, sonraki arayüz yazılımının mı yoksa gerçek fonksiyonun mu çağrılacağını tanımlar.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Ön işleme: Fonksiyon çalıştırılmadan önce kayıt tut
    print(f"[Function] Calling {context.function.name}")

    # Sonraki ara yazılıma veya fonksiyon çalıştırmaya devam et
    await next(context)

    # Son işlem: Fonksiyon çalıştırıldıktan sonra kayıt tut
    print(f"[Function] {context.function.name} completed")
```

*Sohbet Arayüz Yazılımı*

Bu arayüz yazılımı, ajan ile LLM arasındaki istekler arasında bir eylemi yürütmeye veya kaydetmeye izin verir.

Bu, AI servisine gönderilen `messages` gibi önemli bilgileri içerir.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Ön işleme: AI çağrısından önce kaydet
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Sonraki ara katmana veya AI servisine devam et
    await next(context)

    # Son işlem: AI yanıtından sonra kaydet
    print("[Chat] AI response received")

```

**Ajan Belleği**

`Agentic Memory` dersinde bahsedildiği gibi, belleğin ajanların farklı bağlamlarda çalışmasını mümkün kılan önemli bir unsurudur. MAF, çeşitli bellek türleri sunar:

*Hafıza İçi Depolama*

Bu, uygulama çalışma süresi boyunca iş parçacıklarında tutulan bellektir.

```python
# Yeni bir iş parçacığı oluştur.
thread = agent.get_new_thread() # İş parçacığı ile ajanı çalıştır.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Kalıcı Mesajlar*

Bu bellek, farklı oturumlar arasında konuşma geçmişi saklamak için kullanılır. `chat_message_store_factory` ile tanımlanır:

```python
from agent_framework import ChatMessageStore

# Özel bir mesaj deposu oluşturun
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dinamik Bellek*

Bu bellek, ajanlar çalıştırılmadan önce bağlama eklenir. Bu bellekler mem0 gibi dış servislerde saklanabilir:

```python
from agent_framework.mem0 import Mem0Provider

# Gelişmiş bellek yetenekleri için Mem0 kullanımı
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**Ajan Gözlemlenebilirliği**

Gözlemlenebilirlik, güvenilir ve sürdürülebilir ajanik sistemler kurmak için önemlidir. MAF, daha iyi gözlemlenebilirlik için izleme ve ölçüm sağlamak üzere OpenTelemetry ile entegre olur.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # bir şey yap
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### İş Akışları

MAF, bir görevi tamamlamak için önceden tanımlanmış adımlardan oluşan ve bu adımlarda AI ajanlarını içeren iş akışları sunar.

İş akışları, daha iyi kontrol akışı sağlayan farklı bileşenlerden oluşur. İş akışları ayrıca **çoklu ajan orkestrasyonu** ve iş akışı durumlarını kaydetmek için **checkpointing** sağlar.

Bir iş akışının temel bileşenleri:

**Yürütücüler**

Yürütücüler girdi mesajlarını alır, kendilerine atanmış görevleri yerine getirir ve ardından çıktı mesajı üretir. Bu, iş akışını daha büyük görevi tamamlamaya doğru ilerletir. Yürütücüler AI ajanı veya özel mantık olabilir.

**Kenarlar**

Kenarlar iş akışındaki mesaj akışını tanımlamak için kullanılır. Bunlar şunlar olabilir:

*Doğrudan Kenarlar* - Yürütücüler arasında basit bire bir bağlantılar:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Koşullu Kenarlar* - Belirli bir koşul karşılandığında etkinleşir. Örneğin, otel odaları müsait değilse bir yürütücü başka seçenekler önerebilir.

*Switch-case Kenarlar* - Tanımlanmış koşullara göre mesajları farklı yürütücülere yönlendirir. Örneğin, seyahat müşterisi öncelikli erişime sahipse ve görevleri başka bir iş akışı üzerinden ele alınacaksa.

*Fan-out Kenarlar* - Bir mesajı birden çok hedefe gönderir.

*Fan-in Kenarlar* - Farklı yürütücülerden gelen birden fazla mesajı toplayarak bir hedefe gönderir.

**Olaylar**

İş akışları üzerinde daha iyi gözlemlenebilirlik sağlamak için MAF, yürütme için yerleşik olaylar sunar:

- `WorkflowStartedEvent` - İş akışı yürütmesi başlar
- `WorkflowOutputEvent` - İş akışı çıktı üretir
- `WorkflowErrorEvent` - İş akışında hata oluşur
- `ExecutorInvokeEvent` - Yürütücü işlemeye başlar
- `ExecutorCompleteEvent` - Yürütücü işlemi tamamlar
- `RequestInfoEvent` - Bir istek yapılır

## Diğer Çerçevelerden Geçiş (Semantic Kernel ve AutoGen)

### MAF ile Semantic Kernel Arasındaki Farklar

**Basitleştirilmiş Ajan Oluşturma**

Semantic Kernel her ajan için bir Kernel örneği oluşturmayı gerektirir. MAF, ana sağlayıcılar için uzantılar kullanarak basitleştirilmiş bir yaklaşım kullanır.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Ajan İş Parçacığı Oluşturma**

Semantic Kernel'de iş parçacıkları manuel olarak oluşturulmalıdır. MAF'de ajan doğrudan bir iş parçacığına atanır.

```python
thread = agent.get_new_thread() # Ajanı iş parçacığı ile çalıştırın.
```

**Araç Kaydı**

Semantic Kernel'de araçlar Kernel'e kaydedilir ve sonra Kernel ajanlara geçirilir. MAF'de araçlar doğrudan ajan oluşturma sürecinde kaydedilir.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF ile AutoGen Arasındaki Farklar

**Takımlar ve İş Akışları**

`Teams`, AutoGen'deki olay odaklı etkinlik yapısıdır. MAF, verileri yürütücülere grafik tabanlı bir mimari ile yönlendiren `Workflows` kullanır.

**Araç Oluşturma**

AutoGen, ajanların çağırması için fonksiyonları sarmak üzere `FunctionTool` kullanır. MAF, @ai_function kullanır, bu benzer çalışır ancak her fonksiyon için şemaları otomatik olarak çıkarır.

**Ajan Davranışı**

AutoGen'de ajanlar varsayılan olarak tek turludur, `max_tool_iterations` daha yüksek bir değere ayarlanmadıkça. MAF'de ise `ChatAgent` varsayılan olarak çok turdur, yani kullanıcının görevi tamamlanana kadar araçları çağırmaya devam eder.

## Kod Örnekleri 

Microsoft Agent Framework için kod örnekleri bu depoda `xx-python-agent-framework` ve `xx-dotnet-agent-framework` dosyaları altında bulunabilir.

## Microsoft Agent Framework Hakkında Daha Fazla Sorunuz mu Var?

Diğer öğrenenlerle tanışmak, ofis saatlerine katılmak ve AI Ajanları hakkında sorularınızı sormak için [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) topluluğuna katılın.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Feragatname**:
Bu belge, AI çeviri servisi [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba gösterilse de, otomatik çevirilerin hatalar veya yanlışlıklar içerebileceğini lütfen unutmayın. Orijinal belge, kendi dilinde yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanımı sonucunda ortaya çıkabilecek yanlış anlamalar veya yorum hatalarından sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->