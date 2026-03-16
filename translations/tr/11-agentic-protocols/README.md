# Agentik Protokollerin Kullanımı (MCP, A2A ve NLWeb)

[![Agentik Protokoller](../../../translated_images/tr/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Dersin videosunu görüntülemek için yukarıdaki resme tıklayın)_

Yapay zeka ajanlarının kullanımı arttıkça, standartlaştırma, güvenlik ve açık inovasyonu destekleyen protokollere olan ihtiyaç da artıyor. Bu derste, bu ihtiyacı karşılamayı amaçlayan 3 protokolü ele alacağız - Model Context Protocol (MCP), Agent to Agent (A2A) ve Natural Language Web (NLWeb).

## Giriş

Bu derste ele alacaklarımız:

• **MCP**'nin Yapay Zeka Ajanlarının kullanıcı görevlerini tamamlamak için harici araçlara ve verilere erişmesini nasıl sağladığı.

• **A2A**'nın farklı yapay zeka ajanları arasında iletişim ve iş birliği olanağı nasıl sunduğu.

• **NLWeb**'in herhangi bir web sitesine doğal dil arayüzleri getirerek Yapay Zeka Ajanlarının içeriği keşfetmesini ve etkileşim kurmasını nasıl sağladığı.

## Öğrenme Hedefleri

• **Tanımlamak**: MCP, A2A ve NLWeb'in yapay zeka ajanları bağlamındaki temel amacı ve faydalarını belirlemek.

• **Açıklamak**: Her protokolün LLM'ler, araçlar ve diğer ajanlar arasındaki iletişim ve etkileşimi nasıl kolaylaştırdığını açıklamak.

• **Farkına varmak**: Karmaşık ajan sistemleri oluştururken her protokolün oynadığı ayrı rolleri tanımak.

## Model Context Protocol

**Model Context Protocol (MCP)**, uygulamaların LLM'lere bağlam ve araçlar sağlaması için standartlaştırılmış bir yol sunan açık bir standarttır. Bu, Yapay Zeka Ajanlarının tutarlı bir şekilde bağlanabileceği farklı veri kaynakları ve araçlara yönelik bir "evrensel adaptör" olanağı sağlar.

MCP'nin bileşenlerine, doğrudan API kullanımına kıyasla sağladığı faydalara ve Yapay Zeka ajanlarının bir MCP sunucusunu nasıl kullanabileceğine dair bir örneğe bakalım.

### MCP Temel Bileşenleri

MCP, **istemci-sunucu mimarisi** üzerinde çalışır ve temel bileşenler şunlardır:

• **Hosts** (Barındırıcılar) MCP Sunucularına bağlantıları başlatan LLM uygulamalarıdır (örneğin VSCode gibi bir kod editörü).

• **Clients** (İstemciler) barındırıcı uygulama içindeki, sunucularla birebir bağlantıyı sürdüren bileşenlerdir.

• **Servers** (Sunucular) belirli yetenekleri açığa çıkaran hafif programlardır.

Protokolde yer alan üç temel ilkel, bir MCP Sunucusunun yetenekleridir:

• **Tools** (Araçlar): Bunlar bir Yapay Zeka ajanının bir eylemi gerçekleştirmek için çağırabileceği ayrık eylemler veya işlevlerdir. Örneğin, bir hava durumu servisi "hava durumu al" aracını açığa çıkarabilir veya bir e-ticaret sunucusu "ürün satın al" aracını sunabilir. MCP sunucuları, yetenekler listesinde her aracın adını, açıklamasını ve giriş/çıkış şemasını bildirir.

• **Resources** (Kaynaklar): Bunlar MCP sunucusunun sağlayabileceği salt okunur veri öğeleri veya belgeler olup istemciler bunları talep üzerine alabilir. Örnekler arasında dosya içerikleri, veritabanı kayıtları veya log dosyaları bulunur. Kaynaklar metin (kod veya JSON gibi) veya ikili (görseller veya PDF'ler gibi) olabilir.

• **Prompts**: Bunlar daha karmaşık iş akışlarına olanak tanıyan önerilen istemleri sağlayan ön tanımlı şablonlardır.

### MCP'nin Faydaları

MCP, Yapay Zeka Ajanları için önemli avantajlar sunar:

• **Dinamik Araç Keşfi**: Ajanlar, bir sunucudan hangi araçların mevcut olduğunu ve ne yaptıklarına dair açıklamalarla dinamik olarak bir liste alabilir. Bu, entegrasyon için genellikle statik kodlama gerektiren geleneksel API'lerle tezat oluşturur; API'de herhangi bir değişiklik kod güncellemesi gerektirir. MCP, "bir kez entegre et" yaklaşımı sunarak daha yüksek uyarlanabilirlik sağlar.

• **LLM'ler Arası Birlikte Çalışabilirlik**: MCP, farklı LLM'ler arasında çalışarak çekirdek modelleri değiştirme esnekliği sağlar ve daha iyi performans için değerlendirme olanağı verir.

• **Standartlaştırılmış Güvenlik**: MCP, standart bir kimlik doğrulama yöntemi içerir ve ek MCP sunucularına erişim eklenirken ölçeklenebilirliği artırır. Bu, çeşitli geleneksel API'ler için farklı anahtarlar ve kimlik doğrulama türlerini yönetmekten daha basittir.

### MCP Örneği

![MCP Diyagramı](../../../translated_images/tr/mcp-diagram.e4ca1cbd551444a1.webp)

Bir kullanıcının MCP ile çalışan bir Yapay Zeka asistanı kullanarak uçak bileti rezervasyonu yapmak istediğini hayal edelim.

1. **Bağlantı**: Yapay Zeka asistanı (MCP istemcisi), bir havayolu tarafından sağlanan bir MCP sunucusuna bağlanır.

2. **Araç Keşfi**: İstemci havayolunun MCP sunucusuna, "Hangi araçlara sahipsiniz?" diye sorar. Sunucu "uçuş ara" ve "uçuş rezervasyonu yap" gibi araçlarla yanıt verir.

3. **Araç Çağrısı**: Ardından asistanınıza, "Portland'dan Honolulu'ya bir uçuş ara lütfen" dersiniz. Yapay Zeka asistanı, LLM'ini kullanarak "uçuş ara" aracını çağırması gerektiğini belirler ve ilgili parametreleri (kalkış, varış) MCP sunucusuna iletir.

4. **Yürütme ve Yanıt**: MCP sunucusu bir sarma (wrapper) olarak hareket eder, havayolu iç rezervasyon API'sine gerçek çağrıyı yapar. Ardından uçuş bilgilerini (ör. JSON verisi) alır ve Yapay Zeka asistanına geri gönderir.

5. **İleri Etkileşim**: Yapay Zeka asistanı uçuş seçeneklerini sunar. Bir uçuş seçildiğinde, asistan aynı MCP sunucusunda "uçuş rezervasyonu yap" aracını çağırarak rezervasyonu tamamlayabilir.

## Ajanlar Arası Protokol (A2A)

MCP, LLM'leri araçlara bağlamaya odaklanırken, **Agent-to-Agent (A2A) protokolü** bir adım daha ileri giderek farklı yapay zeka ajanları arasında iletişim ve iş birliğine olanak tanır. A2A, farklı kuruluşlar, ortamlar ve teknoloji yığınları arasındaki yapay zeka ajanlarını paylaşılan bir görevi tamamlamak için birbirine bağlar.

A2A'nın bileşenlerini ve faydalarını inceleyeceğiz ve bunun seyahat uygulamamızda nasıl uygulanabileceğine dair bir örnek vereceğiz.

### A2A Temel Bileşenleri

A2A, ajanlar arasındaki iletişimi etkinleştirmeye ve onların kullanıcı için bir alt görevi birlikte tamamlamasına odaklanır. Protokolün her bileşeni buna katkıda bulunur:

#### Agent Card

MCP sunucusunun bir araç listesi paylaşmasına benzer şekilde, bir Agent Card şunları içerir:
- Ajanın Adı .
- Tamamladığı genel görevlerin **açıklaması**.
- Diğer ajanların (ve hatta insan kullanıcıların) bir ajana ne zaman ve neden çağrı yapmaları gerektiğini anlamalarına yardımcı olacak açıklamalı **özgül beceriler listesi**.
- Ajanın **mevcut Endpoint URL'si**
- Ajanın **sürümü** ve akışlı yanıtlar ile push bildirimleri gibi **yetenekleri**.

#### Agent Executor

Agent Executor, **kullanıcı sohbetinin bağlamını uzak ajana iletmekten** sorumludur; uzak ajanın tamamlanması gereken görevi anlaması için buna ihtiyacı vardır. Bir A2A sunucusunda, bir ajan gelen istekleri ayrıştırmak ve kendi dahili araçlarını kullanarak görevleri yürütmek için kendi Büyük Dil Modelini (LLM) kullanır.

#### Artifact

Uzak ajan istenen görevi tamamladığında, yaptığı iş bir artifact olarak oluşturulur. Bir artifact, **ajanın çalışmasının sonucunu**, **tamamlanan işin açıklamasını** ve protokol aracılığıyla gönderilen **metin bağlamını** içerir. Artifact gönderildikten sonra uzak ajanla olan bağlantı, tekrar ihtiyaç duyulana kadar kapatılır.

#### Event Queue

Bu bileşen, **güncellemeleri işlemek ve mesajları iletmek** için kullanılır. Ajanik sistemlerde, görev tamamlama süreleri daha uzun olabileceği için, bir görevin tamamlanmasından önce ajanlar arasındaki bağlantının kapanmasını önlemek amacıyla üretimde özellikle önemlidir.

### A2A'nin Faydaları

• **Gelişmiş İş Birliği**: Farklı satıcılar ve platformlardan gelen ajanların etkileşimde bulunmasını, bağlam paylaşmasını ve birlikte çalışmasını sağlayarak geleneksel olarak ayrık sistemler arasında kesintisiz otomasyon kolaylaştırır.

• **Model Seçimi Esnekliği**: Her A2A ajanı, isteklerini hizmet vermek için hangi LLM'yi kullanacağına karar verebilir; bu, bazı MCP senaryolarındaki tek bir LLM bağlantısının aksine, ajan başına optimize edilmiş veya ince ayarlı modellerin kullanılmasına izin verir.

• **Yerleşik Kimlik Doğrulama**: Kimlik doğrulama A2A protokolüne doğrudan entegre edilmiştir ve ajan etkileşimleri için sağlam bir güvenlik çerçevesi sağlar.

### A2A Örneği

![A2A Diyagramı](../../../translated_images/tr/A2A-Diagram.8666928d648acc26.webp)

Seyahat rezervasyon senaryomuzu genişletelim, ancak bu sefer A2A kullanarak.

1. **Kullanıcı Çoklu Ajan İsteği**: Bir kullanıcı "Sıradaki hafta için Honolulu'ya tam bir seyahat rezerve et, uçuşlar, otel ve kiralık araba dahil" gibi bir istekte bulunarak bir "Seyahat Acentesi" A2A istemcisi/ajanı ile etkileşime geçer.

2. **Seyahat Acentesi Tarafından Orkestrasyon**: Seyahat Acentesi bu karmaşık isteği alır. Görev hakkında akıl yürütmek ve diğer uzman ajanlarla etkileşime geçmesi gerektiğini belirlemek için kendi LLM'sini kullanır.

3. **Ajanlar Arası İletişim**: Seyahat Acentesi daha sonra A2A protokolünü kullanarak farklı şirketler tarafından oluşturulan "Havayolu Ajanı", "Otel Ajanı" ve "Araç Kiralama Ajanı" gibi alt akış ajanlarına bağlanır.

4. **Yetkilendirilmiş Görev Yürütme**: Seyahat Acentesi, bu uzman ajanlara belirli görevleri delegeler (ör. "Honolulu'ya uçuş bul", "Bir otel rezervasyonu yap", "Araba kirala"). Kendi LLM'lerini çalıştıran ve kendi araçlarını kullanan (bunlar kendileri MCP sunucuları da olabilir) her bir uzman ajan rezervasyonun kendi bölümünü gerçekleştirir.

5. **Konsolide Yanıt**: Tüm alt akış ajanları görevlerini tamamladığında, Seyahat Acentesi sonuçları (uçuş detayları, otel onayı, araç kiralama rezervasyonu) derler ve kullanıcıya kapsamlı, sohbet tarzında bir yanıt gönderir.

## Natural Language Web (NLWeb)

Web siteleri, kullanıcıların internette bilgi ve verilere erişmesi için uzun zamandır birincil yol olmuştur.

NLWeb'in farklı bileşenlerine, NLWeb'in faydalarına ve seyahat uygulamamız örneği ile NLWeb'in nasıl çalıştığına bakalım.

### NLWeb Bileşenleri

- **NLWeb Uygulaması (Çekirdek Servis Kodu)**: Doğal dil sorularını işleyen sistem. Platformun farklı parçalarını bağlayarak yanıtlar oluşturur. Bunu bir web sitesinin doğal dil özelliklerini güçlendiren **motor** olarak düşünebilirsiniz.

- **NLWeb Protokolü**: Bir web sitesiyle doğal dil etkileşimi için **temel kurallar dizisi**dir. Yanıtları JSON formatında (genellikle Schema.org kullanarak) gönderir. Amacı, HTML'in belgeleri çevrimiçi paylaşmayı mümkün kılması gibi, “AI Web” için basit bir temel yaratmaktır.

- **MCP Sunucusu (Model Context Protocol Uç Noktası)**: Her NLWeb kurulumu aynı zamanda bir **MCP sunucusu** olarak da çalışır. Bu, diğer AI sistemleriyle **araçları (ör. bir `ask` yöntemi) ve veriyi** paylaşabileceği anlamına gelir. Pratikte, bu web sitesinin içerik ve yeteneklerinin Yapay Zeka ajanları tarafından kullanılmasını sağlar ve sitenin daha geniş “ajan ekosistemi”nin bir parçası olmasına olanak tanır.

- **Embedding Modelleri**: Bu modeller, web sitesi içeriğini bilgisayarların karşılaştırıp arama yapabileceği şekilde anlamı yakalayan sayısal temsillere, yani vektörlere (embedding) dönüştürmek için kullanılır. Bu vektörler özel bir veritabanında saklanır ve kullanıcılar hangi embedding modelini kullanmak istediklerini seçebilir.

- **Vektör Veritabanı (Getirme Mekanizması)**: Bu veritabanı, web sitesi içeriğinin embedding'lerini saklar. Birisi bir soru sorduğunda, NLWeb en alakalı bilgiyi hızla bulmak için vektör veritabanını kontrol eder. Benzerliğe göre sıralanmış hızlı bir olası yanıt listesi sağlar. NLWeb, Qdrant, Snowflake, Milvus, Azure AI Search ve Elasticsearch gibi farklı vektör depolama sistemleriyle çalışır.

### Örnek Üzerinden NLWeb

![NLWeb](../../../translated_images/tr/nlweb-diagram.c1e2390b310e5fe4.webp)

Seyahat rezervasyon web sitemizi tekrar düşünün, ancak bu sefer NLWeb tarafından güçlendiriliyor.

1. **Veri Alımı**: Seyahat web sitesinin mevcut ürün katalogları (ör. uçuş listeleri, otel açıklamaları, tur paketleri) Schema.org kullanılarak formatlanır veya RSS beslemeleri yoluyla yüklenir. NLWeb'in araçları bu yapılandırılmış veriyi alır, embedding'ler oluşturur ve bunları yerel veya uzak bir vektör veritabanında saklar.

2. **Doğal Dil Sorgusu (İnsan)**: Bir kullanıcı siteyi ziyaret eder ve menülerde gezinmek yerine sohbet arayüzüne şu cümleyi yazar: "Gelecek hafta için havuzlu, aile dostu bir Honolulu oteli bul."

3. **NLWeb İşleme**: NLWeb uygulaması bu sorguyu alır. Sorguyu anlamak için bir LLM'ye gönderir ve eşzamanlı olarak ilgili otel listelerini bulmak için vektör veritabanında arama yapar.

4. **Doğru Sonuçlar**: LLM, veritabanından gelen arama sonuçlarını yorumlamaya, "aile dostu", "havuz" ve "Honolulu" kriterlerine göre en iyi eşleşmeleri belirlemeye yardımcı olur ve ardından doğal dilde bir yanıt biçimlendirir. Kritik olarak, yanıt web sitesinin kataloğundaki gerçek otellere atıfta bulunur; uydurma bilgi üretmekten kaçınır.

5. **Yapay Zeka Ajanı Etkileşimi**: NLWeb bir MCP sunucusu olarak hizmet verdiği için, harici bir Yapay Zeka seyahat ajanı da bu web sitesinin NLWeb örneğine bağlanabilir. Yapay zeka ajanı daha sonra siteyi doğrudan sorgulamak için `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")` MCP yöntemini kullanabilir. NLWeb örneği bunu işler, restoran bilgisi veritabanını (yüklenmişse) kullanır ve yapılandırılmış bir JSON yanıtı döndürür.

### MCP/A2A/NLWeb Hakkında Daha Fazla Sorunuz mu Var?

Diğer öğrenenlerle tanışmak, danışma saatlerine katılmak ve Yapay Zeka Ajanlarınızla ilgili sorularınızı yanıtlatmak için [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)'a katılın.

## Kaynaklar

- [MCP for Beginners](https://aka.ms/mcp-for-beginners)  
- [MCP Documentation](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb Repo](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel Guides](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Feragatname**:
Bu belge AI çeviri hizmeti [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstermemize rağmen, otomatik çevirilerin hatalar veya yanlışlıklar içerebileceğini lütfen unutmayın. Orijinal belge, kendi dilindeki hâli yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanılması sonucu ortaya çıkabilecek herhangi bir yanlış anlama veya yanlış yorumdan sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->