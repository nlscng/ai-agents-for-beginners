[![Yapay Zeka Ajanlarına Giriş](../../../translated_images/tr/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Yukarıdaki görüntüye tıklayarak bu dersin videosunu izleyin)_


# Yapay Zeka Ajanlarına ve Ajan Kullanım Örneklerine Giriş

“AI Agents for Beginners” kursuna hoş geldiniz! Bu kurs, Yapay Zeka Ajanları oluşturmak için temel bilgileri ve uygulamalı örnekleri sağlar.

Diğer öğrenenlerle ve AI Agent Oluşturucularıyla tanışmak ve bu kursta sahip olduğunuz herhangi bir soruyu sormak için <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord Community</a>'ye katılın.

Bu kursa başlamak için, önce Yapay Zeka Ajanlarının ne olduğunu ve bunları oluşturduğumuz uygulamalarda ve iş akışlarında nasıl kullanabileceğimizi daha iyi anlamaya çalışacağız.

## Giriş

Bu ders şunları kapsar:

- Yapay Zeka Ajanları nedir ve farklı ajan türleri nelerdir?
- Hangi kullanım senaryoları Yapay Zeka Ajanları için en uygunudur ve bize nasıl yardımcı olurlar?
- Ajan Tabanlı Çözümler tasarlarken bazı temel yapı taşları nelerdir?

## Öğrenme Hedefleri
Bu dersi tamamladıktan sonra şunları yapabilmelisiniz:

- Yapay Zeka Ajanı kavramlarını ve bunların diğer AI çözümlerinden nasıl farklılaştığını anlamak.
- Yapay Zeka Ajanlarını en verimli şekilde uygulamak.
- Hem kullanıcılar hem de müşteriler için üretken Ajan Tabanlı çözümler tasarlamak.

## Yapay Zeka Ajanlarını Tanımlama ve Ajan Türleri

### Yapay Zeka Ajanları nedir?

Yapay Zeka Ajanları, Büyük Dil Modelleri (LLM'ler) ile LLM'lere araçlara ve bilgiye erişim sağlayarak yeteneklerini genişletip eylem gerçekleştirmelerini mümkün kılan birer sistemdir.

Bu tanımı daha küçük parçalara bölelim:

- Sistem - Ajanları sadece tek bir bileşen olarak değil, birçok bileşenden oluşan bir sistem olarak düşünmek önemlidir. Temel seviyede, bir Yapay Zeka Ajanının bileşenleri şunlardır:
  - Ortam - Yapay Zeka Ajanının çalıştığı tanımlı alan. Örneğin, bir seyahat rezervasyon yapma ajanımız olsaydı, ortam ajanın görevleri tamamlamak için kullandığı seyahat rezervasyon sistemi olabilir.
  - Sensörler - Ortamlar bilgi içerir ve geri bildirim sağlar. Yapay Zeka Ajanları, ortamın mevcut durumu hakkında bilgi toplamak ve yorumlamak için sensörleri kullanır. Seyahat Rezervasyon Ajanı örneğinde, rezervasyon sistemi otel müsaitliği veya uçuş fiyatları gibi bilgiler sağlayabilir.
  - Aktüatörler - Yapay Zeka Ajanı ortamın mevcut durumunu aldıktan sonra, mevcut görev için ortamı değiştirmek amacıyla hangi eylemi gerçekleştireceğine karar verir. Seyahat rezervasyon ajanı için bu, kullanıcı için mevcut bir odayı rezerve etmek olabilir.

![Yapay Zeka Ajanları Nedir?](../../../translated_images/tr/what-are-ai-agents.1ec8c4d548af601a.webp)

Büyük Dil Modelleri - Ajanlar kavramı LLM'lerin oluşturulmasından önce de vardı. LLM'lerle Yapay Zeka Ajanları oluşturmanın avantajı, insan dilini ve veriyi yorumlayabilme yetenekleridir. Bu yetenek, LLM'lerin ortam bilgilerini yorumlamasını ve ortamı değiştirmek için bir plan tanımlamasını sağlar.

Eylem Gerçekleştirme - AI Ajanı sistemlerinin dışında, LLM'ler genellikle kullanıcının istemine dayanarak içerik veya bilgi üretme durumlarıyla sınırlıdır. AI Ajanı sistemleri içinde, LLM'ler kullanıcının isteğini yorumlayarak ve ortamlarında bulunan araçları kullanarak görevleri yerine getirebilir.

Araçlara Erişim - LLM'nin hangi araçlara erişimi olduğu 1) çalıştığı ortam tarafından ve 2) AI Ajanı geliştiricisi tarafından tanımlanır. Seyahat ajanı örneğimizde, ajanın araçları rezervasyon sisteminde mevcut olan işlemlerle sınırlıdır ve/veya geliştirici ajanın uçuşlara erişimini sınırlayabilir.

Bellek+Bilgi - Bellek, kullanıcı ile ajan arasındaki konuşma bağlamında kısa süreli olabilir. Uzun vadede, ortam tarafından sağlanan bilgilerin dışında, Yapay Zeka Ajanları diğer sistemlerden, hizmetlerden, araçlardan ve hatta diğer ajanlardan bilgi alabilir. Seyahat ajanı örneğinde, bu bilgi kullanıcının seyahat tercihleriyle ilgili müşteri veritabanında bulunan bilgiler olabilir.

### Farklı ajan türleri

Şimdi Yapay Zeka Ajanlarının genel bir tanımına sahip olduğumuza göre, bazı spesifik ajan türlerine ve bunların bir seyahat rezervasyon ajanına nasıl uygulanacağına bakalım.

| **Ajan Türü**                | **Açıklama**                                                                                                                       | **Örnek**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Basit Refleks Ajanlar**      | Önceden tanımlanmış kurallara dayalı olarak anında eylemler gerçekleştirir.                                                                                  | Seyahat ajanı e-posta bağlamını yorumlar ve seyahat şikayetlerini müşteri hizmetlerine iletir.                                                                                                                          |
| **Model Tabanlı Refleks Ajanlar** | Dünya modeline ve bu modeldeki değişikliklere dayalı olarak eylemler gerçekleştirir.                                                              | Seyahat ajanı, geçmiş fiyat verilerine erişim sayesinde önemli fiyat değişikliklerine sahip rotaları önceliklendirir.                                                                                                             |
| **Hedef Tabanlı Ajanlar**         | Hedefi yorumlayarak ve hedefe ulaşmak için gerekli eylemleri belirleyerek belirli hedefleri gerçekleştirmek için planlar oluşturur.                                  | Seyahat ajanı, mevcut konumdan varış noktasına gerekli seyahat düzenlemelerini (araç, toplu taşıma, uçuşlar) belirleyerek bir yolculuğu rezerve eder.                                                                                |
| **Fayda Tabanlı Ajanlar**      | Tercihleri dikkate alır ve hedeflere nasıl ulaşılacağını sayısal olarak değerlendirmek için takasları tartar.                                               | Seyahat ajanı, seyahat rezervasyonu yaparken rahatlık ile maliyeti tartarak faydayı maksimize eder.                                                                                                                                          |
| **Öğrenen Ajanlar**           | Geri bildirime yanıt vererek ve buna göre eylemlerini ayarlayarak zamanla gelişir.                                                        | Seyahat ajanı, yolculuk sonrası anketlerden gelen müşteri geri bildirimlerini kullanarak gelecekteki rezervasyonlarda iyileştirmeler yapar.                                                                                                               |
| **Hiyerarşik Ajanlar**       | Çok seviyeli bir sistemde birden fazla ajan bulunur; üst düzey ajanlar görevleri alt düzey ajanların tamamlayacağı alt görevlere böler. | Seyahat ajanı, bir geziyi iptal ederken görevi alt görevlere (örneğin belirli rezervasyonları iptal etme) bölerek alt düzey ajanların bunları tamamlamasını sağlar ve üst düzey ajana rapor verir.                                     |
| **Çok Ajanlı Sistemler (MAS)** | Ajanlar görevleri bağımsız olarak, ya işbirlikçi ya da rekabetçi şekilde tamamlar.                                                           | İşbirlikçi: Birden fazla ajan oteller, uçuşlar ve eğlence gibi belirli seyahat hizmetlerini rezerve eder. Rekabetçi: Birden fazla ajan, müşterileri otelde kaydetmek için paylaşılan bir otel rezervasyon takvimi üzerinde yönetim ve rekabet eder. |

## Yapay Zeka Ajanları Ne Zaman Kullanılmalı

Önceki bölümde, farklı ajan türlerinin seyahat rezervasyonunun farklı senaryolarında nasıl kullanılabileceğini açıklamak için Seyahat Ajanı kullanım örneğini kullandık. Bu uygulamayı ders boyunca kullanmaya devam edeceğiz.

Yapay Zeka Ajanlarının en iyi kullanıldığı kullanım senaryolarına bakalım:

![Yapay Zeka Ajanları Ne Zaman Kullanılmalı?](../../../translated_images/tr/when-to-use-ai-agents.54becb3bed74a479.webp)


- Açık Uçlu Problemler - LLM'nin bir görevi tamamlamak için gerekli adımları belirlemesine izin vermek, çünkü bunlar her zaman iş akışına sert kodlanamaz.
- Çok Adımlı Süreçler - Ajanın araçları veya bilgileri birden çok adım boyunca kullanması gereken, tek seferlik bilgi çekmenin yeterli olmadığı bir karmaşıklık düzeyi gerektiren görevler.
- Zaman İçinde İyileşme - Ajanın, daha iyi fayda sağlamak için ortamından veya kullanıcılardan geri bildirim alarak zaman içinde gelişebileceği görevler.

AI Ajanlarını kullanmaya ilişkin daha fazla dikkate alınması gereken noktaları Güvenilir AI Ajanları Oluşturma dersinde ele alıyoruz.

## Ajan Tabanlı Çözümlerin Temelleri

### Ajan Geliştirme

Bir Yapay Zeka Ajanı sistemi tasarlamanın ilk adımı araçları, eylemleri ve davranışları tanımlamaktır. Bu kursta, Ajanlarımızı tanımlamak için **Azure AI Agent Service** kullanmaya odaklanıyoruz. Bu hizmet şu gibi özellikler sunar:

- OpenAI, Mistral ve Llama gibi Açık Modellerin seçimi
- Tripadvisor gibi sağlayıcılar aracılığıyla Lisanslı Verilerin kullanımı
- Standartlaştırılmış OpenAPI 3.0 araçlarının kullanımı

### Ajan Tabanlı Desenler

LLM'lerle iletişim istemlerle (prompts) sağlanır. AI Ajanlarının yarı otonom doğası göz önüne alındığında, ortamda bir değişiklik olduğunda LLM'yi elle tekrar istemlemek her zaman mümkün veya gerekli değildir. LLM'yi daha ölçeklenebilir bir şekilde birden çok adım boyunca istemlememize olanak veren **Ajan Tabanlı Desenler** kullanıyoruz.

Bu kurs, şu anda popüler olan bazı Ajan Tabanlı desenlere ayrılmıştır.

### Ajan Tabanlı Çerçeveler

Ajan Tabanlı Çerçeveler, geliştiricilerin kod yoluyla ajan desenlerini uygulamalarına olanak tanır. Bu çerçeveler, daha iyi AI Ajanı iş birliği için şablonlar, eklentiler ve araçlar sunar. Bu avantajlar, AI Ajanı sistemlerinin daha iyi gözlemlenebilirliği ve sorun giderilebilirliği için yetenekler sağlar.

Bu kursta araştırma odaklı AutoGen çerçevesini ve üretime hazır Semantic Kernel'den Agent çerçevesini inceleyeceğiz.

## Örnek Kodlar

- Python: [Ajan Çerçevesi](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Ajan Çerçevesi](./code_samples/01-dotnet-agent-framework.md)

## Yapay Zeka Ajanları Hakkında Daha Fazla Sorunuz Mu Var?

Diğer öğrenenlerle buluşmak, ofis saatlerine katılmak ve Yapay Zeka Ajanları sorularınıza cevap almak için [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) ile görüşün.

## Önceki Ders

[Kurs Kurulumu](../00-course-setup/README.md)

## Sonraki Ders

[Ajan Tabanlı Çerçeveleri Keşfetme](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Sorumluluk Reddi:**
Bu belge yapay zeka (AI) çeviri hizmeti [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstersek de, otomatik çevirilerin hatalar veya yanlışlıklar içerebileceğini lütfen unutmayın. Belgenin orijinal dili yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanılması sonucunda ortaya çıkabilecek herhangi bir yanlış anlama veya yanlış yorumdan sorumlu tutulamayız.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->