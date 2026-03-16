[![Planning Design Pattern](../../../translated_images/tr/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Bu dersin videosunu izlemek için yukarıdaki görüntüye tıklayın)_

# Planlama Tasarımı

## Giriş

Bu ders şunları kapsayacak

* Net bir genel hedef tanımlamak ve karmaşık bir görevi yönetilebilir görevlere bölmek.
* Daha güvenilir ve makine tarafından okunabilir yanıtlar için yapılandırılmış çıktı kullanmak.
* Dinamik görevleri ve beklenmedik girdileri ele almak için olay odaklı yaklaşım uygulamak.

## Öğrenme Hedefleri

Bu dersi tamamladıktan sonra şunları anlayabileceksiniz:

* Bir yapay zeka ajanı için genel bir hedef belirlemek ve hedefin ne olduğu konusunda net olmasını sağlamak.
* Karmaşık bir görevi yönetilebilir alt görevlere ayırmak ve bunları mantıklı bir sıraya göre düzenlemek.
* Ajanları uygun araçlarla donatmak (örn. arama araçları veya veri analizi araçları), ne zaman ve nasıl kullanılacaklarına karar vermek ve ortaya çıkan beklenmedik durumları yönetmek.
* Alt görev sonuçlarını değerlendirmek, performansı ölçmek ve nihai çıktıyı geliştirmek için eylemleri yinelemek.

## Genel Hedefin Tanımlanması ve Görevin Parçalara Bölünmesi

![Defining Goals and Tasks](../../../translated_images/tr/defining-goals-tasks.d70439e19e37c47a.webp)

Çoğu gerçek dünya görevi tek adımda ele alınamayacak kadar karmaşıktır. Bir yapay zeka ajanının planlama ve eylemlerine rehberlik etmesi için özlü bir hedefe ihtiyacı vardır. Örneğin, şu hedefi düşünün:

    "3 günlük bir seyahat programı oluştur."

Bu ifade basit olmasına rağmen, yine de biraz detaylandırılmaya ihtiyaç duyar. Hedef ne kadar net olursa, ajan (ve varsa insan işbirlikçileri) doğru sonuca odaklanabilir; örneğin, uçuş seçenekleri, otel önerileri ve etkinlik tavsiyeleri içeren kapsamlı bir program hazırlamak gibi.

### Görev Parçalara Ayrımı

Büyük veya karmaşık görevler, daha küçük ve hedefe yönelik alt görevlere ayrıldığında daha yönetilebilir hale gelir.
Seyahat programı örneğinde, hedefi şunlara bölebilirsiniz:

* Uçuş Rezervasyonu
* Otel Rezervasyonu
* Araç Kiralama
* Kişiselleştirme

Her alt görev, ilgili ajanlar veya süreçler tarafından ele alınabilir. Bir ajan en iyi uçuş fırsatlarını arayabilirken, bir başkası otel rezervasyonlarına odaklanabilir ve benzeri. Koordine eden veya "aşağı akış" ajanı ise bu sonuçları kullanıcıya tek, uyumlu bir program olarak sunabilir.

Bu modüler yaklaşım aynı zamanda aşamalı geliştirmelere imkan tanır. Örneğin, Yiyecek Önerileri veya Yerel Etkinlik Tavsiyeleri için özel ajanlar ekleyebilir ve programı zamanla iyileştirebilirsiniz.

### Yapılandırılmış Çıktı

Büyük Dil Modelleri (LLM'ler), aşağı akış ajanlarının veya servislerin daha kolay ayrıştırıp işleyebileceği yapılandırılmış çıktı (örneğin JSON) üretebilir. Bu, çok ajanlı bağlamda özellikle faydalıdır; planlama çıktısını aldıktan sonra bu görevleri eyleme geçirebiliriz. Hızlı bir genel bakış için şu <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blog yazısına</a> bakabilirsiniz.

Aşağıdaki Python kodu, bir planlayıcı ajanın nasıl bir hedefi alt görevlere bölüp yapılandırılmış bir plan oluşturduğunu göstermektedir:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Seyahat AltGörev Modeli
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # Görevi ajan'a atamak istiyoruz

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Model ile kimlik doğrulaması yapmak için GitHub ayarlarınızda kişisel erişim belirteci (PAT) oluşturmanız gerekmektedir.
    # PAT belirtecinizi burada verilen talimatları izleyerek oluşturun: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Kullanıcı mesajını tanımlayın
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Yanıt içeriğinin geçerli bir JSON dizesi olduğundan emin olunmadan önce yükleyin
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Yanıt içeriği geçerli bir JSON dizesi değil")

# # Yanıt içeriğini JSON olarak yükledikten sonra yazdırın
# pprint(json.loads(response_content))

# Yanıt içeriğini MathReasoning modeli ile doğrulayın
# TravelPlan.model_validate(json.loads(response_content))
```

### Çok Ajanlı Orkestrasyon ile Planlama Ajanı

Bu örnekte, Semantik Yönlendirici Ajan bir kullanıcı isteği alır (örn. "Seyahatim için bir otel planına ihtiyacım var.").

Planlayıcı şunları yapar:

* Otel Planını Alır: Planlayıcı, kullanıcının mesajını alır ve sistem istemi (mevcut ajan detayları dahil) temelinde yapılandırılmış bir seyahat planı oluşturur.
* Ajanlar ve Araçlarını Listeler: Ajan kaydı, uçuş, otel, araç kiralama ve aktiviteler için ajanlar ve kullandıkları fonksiyon veya araçları tutar.
* Planı İlgili Ajanlara Yönlendirir: Alt görev sayısına bağlı olarak, planlayıcı mesajı ya doğrudan ilgili ajana (tek görev senaryoları için) ya da çok ajanlı işbirliği için grup sohbet yöneticisine iletir.
* Sonucu Özetler: Son olarak, planlayıcı oluşturulan planı açıklık için özetler.
Aşağıdaki Python kodu bu adımları göstermektedir:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Seyahat AltGörev Modeli

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # Görevi ajana atamak istiyoruz

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Türü kontrol edilmiş ortam değişkenleri ile istemciyi oluştur

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Kullanıcı mesajını tanımla

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Yanıt içeriğinin yüklemeden önce geçerli bir JSON dizesi olduğundan emin ol

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Yanıt içeriğini JSON olarak yükledikten sonra yazdır

pprint(json.loads(response_content))
```

Sonrasında, önceki kodun çıktısı olarak elde edilen yapılandırılmış çıktıyı `assigned_agent`'a yönlendirebilir ve seyahat planını son kullanıcıya özetleyebilirsiniz.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Önceki kod örneğini içeren örnek bir not defteri [burada](../../../07-planning-design) mevcuttur.

### Yinelemeli Planlama

Bazı görevler, bir alt görevin sonucu diğerini etkilediğinde ileri geri veya yeniden planlama gerektirir. Örneğin, ajan uçuş rezervasyonu sırasında beklenmedik bir veri formatıyla karşılaşırsa, otel rezervasyonuna geçmeden önce stratejisini değiştirmeniz gerekebilir.

Ayrıca, kullanıcı geri bildirimi (ör. bir insanın daha erken bir uçuşu tercih etmesi) kısmi bir yeniden planlamaya yol açabilir. Bu dinamik ve yinelemeli yaklaşım, son çözümün gerçek dünya kısıtlamalarına ve değişen kullanıcı tercihlerine uyumlu olmasını sağlar.

örnek kod

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. önceki kodla aynı ve kullanıcı geçmişi, mevcut planı aktar
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. yeniden planla ve görevleri ilgili ajanlara gönder
```

Daha kapsamlı planlamalar için karmaşık görevleri çözmek üzere Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blog Yazısını</a> inceleyebilirsiniz.

## Özet

Bu yazıda, tanımlı ajanları dinamik olarak seçebilen bir planlayıcı örneğine baktık. Planlayıcının çıktısı, görevleri parçalara ayırır ve ajanlara atar, böylece bunlar gerçekleştirilebilir. Ajanların görevi yerine getirmek için gerekli fonksiyonlara/araçlara erişimi olduğu varsayılır. Ayrıca, yansıtma, özetleyici ve döngü sohbeti gibi kalıplar da ekleyerek özelleştirme yapabilirsiniz.

## Ek Kaynaklar

AutoGen Magentic One - Karmaşık görevleri çözmek için genel amaçlı çok ajanlı bir sistemdir ve birçok zorlu ajanlı benchmarklarda etkileyici sonuçlar elde etmiştir. Kaynak: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Bu uygulamada, orkestratör görev bazlı plan oluşturur ve bu görevleri mevcut ajanlara delege eder. Planlamanın yanı sıra, orkestratör görevin ilerlemesini izlemek ve gerekirse yeniden planlamak için takip mekanizması kullanır.

### Planlama Tasarım Deseni Hakkında Daha Fazla Sorunuz mu Var?

Diğer öğrenenlerle tanışmak, ofis saatlerine katılmak ve Yapay Zeka Ajanları ile ilgili sorularınızı sormak için [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) topluluğuna katılın.

## Önceki Ders

[Güvenilir Yapay Zeka Ajanları Oluşturma](../06-building-trustworthy-agents/README.md)

## Sonraki Ders

[Çok Ajanlı Tasarım Deseni](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Feragatname**:
Bu belge, AI çeviri servisi [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstermemize rağmen, otomatik çevirilerin hata veya yanlışlıklar içerebileceğini lütfen unutmayın. Orijinal belge, kendi dilinde yetkili kaynak olarak kabul edilmelidir. Önemli bilgiler için profesyonel insan çevirisi tavsiye edilir. Bu çevirinin kullanımı sonucunda ortaya çıkabilecek yanlış anlamalar veya yorum hatalarından sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->