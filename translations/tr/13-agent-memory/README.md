# AI Ajanları için Bellek 
[![Ajan Belleği](../../../translated_images/tr/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

AI Ajanları oluşturmanın benzersiz faydalarını tartışırken, iki şey esas olarak konuşulur: görevleri tamamlamak için araç çağırabilme yeteneği ve zaman içinde gelişebilme yeteneği. Bellek, kullanıcılarımıza daha iyi deneyimler yaratabilen kendi kendini geliştiren bir ajan oluşturmanın temelidir.

Bu derste, AI Ajanları için belleğin ne olduğunu ve uygulamalarımızın yararına nasıl yöneteceğimizi ve kullanacağımızı inceleyeceğiz.

## Giriş

Bu ders şu konuları kapsayacaktır:

• **AI Ajan Belleğini Anlamak**: Belleğin ne olduğu ve ajanlar için neden önemli olduğu.

• **Belleği Uygulama ve Depolama**: AI ajanlarınıza bellek yetenekleri eklemek için kısa vadeli ve uzun vadeli belleğe odaklanan pratik yöntemler.

• **AI Ajanlarını Kendi Kendine Geliştirir Hale Getirme**: Belleğin ajanların geçmiş etkileşimlerden öğrenmesini ve zaman içinde iyileşmesini nasıl sağladığı.

## Mevcut Uygulamalar

Bu ders iki kapsamlı notebook öğreticisi içerir:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Mem0 ve Azure AI Search kullanarak Semantic Kernel framework ile belleği uygular

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Cognee kullanarak yapılandırılmış belleği uygular, gömülere dayalı otomatik bilgi grafiği oluşturur, grafiği görselleştirir ve akıllı sorgulama sağlar

## Öğrenme Hedefleri

Bu dersi tamamladıktan sonra şunları bileceksiniz:

• **Çalışma, kısa vadeli ve uzun vadeli bellekler dahil olmak üzere çeşitli AI ajan belleği türlerini ayırt etmek**, ayrıca persona ve episodik bellek gibi özel biçimleri anlamak.

• **Semantic Kernel framework kullanarak AI ajanları için kısa vadeli ve uzun vadeli belleği uygulamak ve yönetmek**, Mem0, Cognee, Whiteboard memory gibi araçlardan yararlanmak ve Azure AI Search ile entegre etmek.

• **Kendi kendini geliştiren AI ajanlarının arkasındaki prensipleri anlamak** ve sağlam bellek yönetimi sistemlerinin sürekli öğrenme ve adaptasyona nasıl katkıda bulunduğunu kavramak.

## AI Ajan Belleğini Anlamak

Özünde, **AI ajanları için bellek, onların bilgiyi tutmalarına ve hatırlamalarına olanak veren mekanizmaları ifade eder**. Bu bilgi bir konuşmayla ilgili belirli ayrıntılar, kullanıcı tercihleri, geçmiş eylemler veya öğrenilmiş desenler olabilir.

Bellek olmadan, AI uygulamaları genellikle durumdan bağımsızdır (stateless), yani her etkileşim baştan başlar. Bu, ajanın önceki bağlamı veya tercihleri "unuttuğu" tekrarlı ve sinir bozucu bir kullanıcı deneyimine yol açar.

### Bellek Neden Önemlidir?

Bir ajanın zekası, geçmiş bilgiyi hatırlama ve kullanma yeteneğiyle yakından bağlantılıdır. Bellek, ajanların şunlar olmasını sağlar:

• **Yansıtıcı**: Geçmiş eylemlerden ve sonuçlardan öğrenme.

• **Etkileşimli**: Devam eden bir konuşma boyunca bağlamı koruma.

• **Proaktif ve Reaktif**: Tarihsel verilere dayanarak ihtiyaçları tahmin etme veya uygun şekilde yanıt verme.

• **Otonom**: Depolanmış bilgiden yararlanarak daha bağımsız çalışma.

Belleği uygulamanın amacı, ajanları daha **güvenilir ve yetenekli** hale getirmektir.

### Bellek Türleri

#### Çalışma Belleği

Bunu, bir ajanın tek bir devam eden görev veya düşünce sürecinde kullandığı bir not kağıdı parçası olarak düşünebilirsiniz. Bir sonraki adımı hesaplamak için gereken ani bilgileri tutar.

AI ajanları için çalışma belleği genellikle bir konuşmanın en alakalı bilgilerini yakalar, tam sohbet geçmişi uzun veya kırpılmış olsa bile. Gereksinimler, öneriler, kararlar ve eylemler gibi ana unsurların çıkarılmasına odaklanır.

**Çalışma Belleği Örneği**

Bir seyahat rezervasyon ajanında, çalışma belleği kullanıcının şu anki isteğini yakalayabilir, örneğin "Paris'e bir gezi rezervasyonu yapmak istiyorum". Bu spesifik gereksinim, mevcut etkileşimi yönlendirmek için ajanın ani bağlamında tutulur.

#### Kısa Süreli Bellek

Bu bellek türü, bir konuşma veya oturum süresi boyunca bilgileri tutar. Mevcut sohbetin bağlamıdır ve ajanın diyalogdaki önceki turlara atıfta bulunmasına olanak tanır.

**Kısa Süreli Bellek Örneği**

Eğer bir kullanıcı "Paris'e bir uçak ne kadar tutar?" diye sorar ve sonra "Orada konaklama ne durumda?" diye takip ederse, kısa süreli bellek ajanın aynı konuşma içinde "orada"nın "Paris"i ifade ettiğini bilmesini sağlar.

#### Uzun Süreli Bellek

Bu, birden fazla konuşma veya oturum boyunca sürdürülen bilgidir. Ajanların kullanıcı tercihlerini, geçmiş etkileşimleri veya genel bilgileri uzun süreler boyunca hatırlamasına olanak tanır. Bu kişiselleştirme için önemlidir.

**Uzun Süreli Bellek Örneği**

Uzun süreli bellek, "Ben kayak yapmayı ve açık hava etkinliklerini sever, dağ manzaralı kahveyi sever ve geçmişteki bir sakatlanma nedeniyle ileri düzey kayak pistlerinden kaçınmak istiyor" bilgisini saklayabilir. Bu bilgi, önceki etkileşimlerden öğrenilmiş olup gelecekteki seyahat planlama oturumlarında önerileri büyük ölçüde kişiselleştirir.

#### Persona Belleği

Bu özel bellek türü, bir ajanın tutarlı bir "kişilik" veya "persona" geliştirmesine yardımcı olur. Ajanın kendisi veya üstlendiği rol hakkında ayrıntıları hatırlamasına izin verir ve etkileşimleri daha akıcı ve odaklı hale getirir.

**Persona Belleği Örneği**
Eğer seyahat ajanı "uzman kayak planlayıcısı" olacak şekilde tasarlandıysa, persona belleği bu rolü pekiştirebilir ve yanıtlarını bir uzmanın tonu ve bilgisine uygun hale getirebilir.

#### İş Akışı/Episodik Bellek

Bu bellek, bir ajanın karmaşık bir görev sırasında attığı adımların sırasını, başarılarını ve başarısızlıklarını depolar. Belirli "epizodları" veya geçmiş deneyimleri hatırlamak gibidir ve bu deneyimlerden öğrenmeyi sağlar.

**Episodik Bellek Örneği**

Eğer ajan belirli bir uçuşu rezerve etmeyi denediyse fakat uygunluk nedeniyle başarısız olduysa, episodik bellek bu hatayı kaydedebilir ve ajanın alternatif uçuşları denemesine veya sonraki bir denemede kullanıcıyı daha bilinçli bir şekilde bilgilendirmesine olanak tanır.

#### Varlık Belleği

Bu, konuşmalardan belirli varlıkları (insanlar, yerler veya nesneler gibi) ve olayları çıkarmayı ve hatırlamayı içerir. Ajanın tartışılan ana unsurların yapılandırılmış bir anlayışını oluşturmasına izin verir.

**Varlık Belleği Örneği**

Geçmiş bir gezi hakkında bir konuşmadan, ajan "Paris", "Eyfel Kulesi" ve "Le Chat Noir restoranında akşam yemeği" gibi varlıkları çıkarabilir. Gelecekteki bir etkileşimde ajan "Le Chat Noir"u hatırlayabilir ve orada yeni bir rezervasyon yapmayı teklif edebilir.

#### Yapılandırılmış RAG (Retrieval Augmented Generation)

RAG daha geniş bir teknik olmasına rağmen, "Yapılandırılmış RAG" güçlü bir bellek teknolojisi olarak vurgulanır. Konuşmalar, e-postalar ve resimler gibi çeşitli kaynaklardan yoğun, yapılandırılmış bilgi çıkarır ve yanıtların doğruluğunu, hatırlama gücünü ve hızını artırmak için kullanır. Klasik RAG'in yalnızca semantik benzerliğe dayanmasının aksine, Yapılandırılmış RAG bilginin içsel yapısıyla çalışır.

**Yapılandırılmış RAG Örneği**

Sadece anahtar kelimeleri eşleştirmek yerine, Yapılandırılmış RAG bir e-postadan uçuş ayrıntılarını (varış yeri, tarih, saat, hava yolu) ayrıştırabilir ve bunları yapılandırılmış bir şekilde depolayabilir. Bu, "Salı günü Paris için hangi uçuşu rezerve ettim?" gibi kesin sorgulara olanak tanır.

## Belleği Uygulama ve Depolama

AI ajanları için belleği uygulamak, **bellek yönetimi**nin sistematik bir sürecini içerir; bu süreç, bilginin üretilmesi, depolanması, geri çağrılması, entegrasyonu, güncellenmesi ve hatta "unutulması" (veya silinmesi) aşamalarını kapsar. Geri çağırma özellikle kritik bir konudur.

### Özel Bellek Araçları

#### Mem0

Ajan belleğini depolamak ve yönetmenin bir yolu, Mem0 gibi özel araçları kullanmaktır. Mem0, ajanların ilgili etkileşimleri hatırlamasına, kullanıcı tercihlerini ve gerçek bağlamı saklamasına ve zaman içinde başarılar ve hatalardan öğrenmesine olanak veren kalıcı bir bellek katmanı olarak çalışır. Buradaki fikir, durumdan bağımsız ajanların durum bilgisine sahip hale gelmesidir.

Bu, **iki aşamalı bir bellek hattı: çıkarım ve güncelleme** yoluyla çalışır. Önce, bir ajanın iş parçasına eklenen mesajlar Mem0 hizmetine gönderilir; bu hizmet bir Large Language Model (LLM) kullanarak konuşma geçmişini özetler ve yeni anıları çıkartır. Ardından, LLM odaklı bir güncelleme aşaması bu anıların eklenip eklenmemesine, değiştirilmesine veya silinmesine karar verir ve bunları vektör, grafik ve anahtar-değer veritabanlarını içerebilen hibrit bir veri deposunda saklar. Bu sistem çeşitli bellek türlerini destekler ve varlıklar arasındaki ilişkileri yönetmek için grafik belleği de entegre edebilir.

#### Cognee

Başka güçlü bir yaklaşım, yapılandırılmış ve yapılandırılmamış verileri gömülere dayalı sorgulanabilir bilgi grafikleri haline dönüştüren açık kaynaklı bir semantik bellek olan **Cognee** kullanmaktır. Cognee, vektör benzerlik araması ile grafik ilişkilerini birleştiren bir **çift-depo mimarisi** sağlar ve ajanların hangi bilgilerin benzer olduğunu değil, kavramların birbirleriyle nasıl ilişkili olduğunu da anlamalarını sağlar.

Ham parça aramasından grafik-donanımlı soru cevaplamaya kadar vektör benzerliği, grafik yapısı ve LLM mantığını harmanlayan **hibrit getirime** (hybrid retrieval) mükemmeldir. Sistem, kısa vadeli oturum bağlamını ve uzun vadeli kalıcı belleği desteklerken, evrimleşen ve büyüyen sorgulanabilir bir "canlı bellek" olarak kalır.

Cognee öğretici notebook'u ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) bu birleşik bellek katmanını kurmayı gösterir; çeşitli veri kaynaklarını alma, bilgi grafiğini görselleştirme ve belirli ajan ihtiyaçlarına göre farklı arama stratejileriyle sorgulama örnekleri içerir.

### RAG ile Bellek Depolama

Mem0 gibi özel bellek araçlarının ötesinde, özellikle yapılandırılmış RAG için **Azure AI Search gibi sağlam arama hizmetlerini bellekleri depolamak ve geri çağırmak için arka uç olarak kullanabilirsiniz**.

Bu, ajanın yanıtlarını kendi verilerinizle temellendirmenize olanak tanır ve daha alakalı ve doğru cevaplar sağlar. Azure AI Search, kullanıcıya özel seyahat anılarını, ürün kataloglarını veya herhangi bir alanla ilgili bilgileri depolamak için kullanılabilir.

Azure AI Search, konuşma geçmişleri, e-postalar veya hatta görüntüler gibi büyük veri kümelerinden yoğun, yapılandırılmış bilgileri çıkarma ve geri çağırmada mükemmel olan **Yapılandırılmış RAG** yeteneklerini destekler. Bu, geleneksel metin parçalama ve gömme yaklaşımlarına kıyasla "insanüstü doğruluk ve hatırlama" sağlar.

## AI Ajanlarını Kendi Kendine Geliştirme

Kendi kendini geliştiren ajanlar için yaygın bir desen, bir **"bilgi ajanı"** tanımlamayı içerir. Bu ayrı ajan, kullanıcı ile birincil ajan arasındaki ana konuşmayı gözlemler. Rolü şunlardır:

1. **Değerli bilgiyi belirlemek**: Konuşmanın herhangi bir bölümünün genel bilgi veya belirli bir kullanıcı tercihi olarak kaydedilmeye değip değmediğini tespit etmek.

2. **Çıkarma ve özetleme**: Konuşmadan temel öğrenmeyi veya tercihi özümlemek.

3. **Bilgi tabanına kaydetme**: Bu çıkarılmış bilgiyi genellikle bir vektör veritabanında kalıcı hale getirmek.

4. **Gelecekteki sorguları zenginleştirme**: Kullanıcı yeni bir sorgu başlattığında, bilgi ajanı ilgili saklanan bilgileri alır ve birincil ajana kritik bağlam sağlamak için kullanıcının istemine ekler (RAG'e benzer şekilde).

### Bellek için Optimizasyonlar

• **Gecikme Yönetimi**: Kullanıcı etkileşimlerini yavaşlatmamak için, önce bilgilerin saklanmaya veya geri çağrılmaya değer olup olmadığını hızlıca kontrol etmek için daha ucuz ve daha hızlı bir model kullanılabilir; yalnızca gerektiğinde daha karmaşık çıkarım/geri çağırma süreci devreye sokulur.

• **Bilgi Tabanı Bakımı**: Büyüyen bir bilgi tabanı için daha az kullanılan bilgiler maliyetleri yönetmek amacıyla "soğuk depolamaya" taşınabilir.

## Ajan Belleği Hakkında Daha Fazla Sorunuz mu Var?

Katılmak için [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) adresine gidin; diğer öğrenenlerle tanışın, ofis saatlerine katılın ve AI Ajanlarıyla ilgili sorularınızı yanıtlatın.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Sorumluluk Reddi:
Bu belge, yapay zeka çeviri hizmeti [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstersek de, otomatik çevirilerin hata veya yanlışlık içerebileceğini unutmayın. Orijinal belge, kendi dilindeki metin itibarıyla yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanımı sonucu ortaya çıkabilecek herhangi bir yanlış anlaşılma veya yanlış yorumlamadan sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->