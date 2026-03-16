[![Multi-Agent Design](../../../translated_images/tr/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Bu dersin videosunu izlemek için yukarıdaki resme tıklayın)_

# Çoklu ajan tasarım kalıpları

Birden fazla ajan içeren bir projede çalışmaya başladığınız anda, çoklu ajan tasarım kalıbını göz önünde bulundurmanız gerekir. Ancak, ne zaman çoklu ajanlara geçileceği ve avantajlarının ne olduğu hemen net olmayabilir.

## Giriş

Bu derste şu sorulara cevap arıyoruz:

- Çoklu ajanların uygulanabileceği senaryolar nelerdir?
- Birden fazla görevi yapan tek bir ajan yerine çoklu ajan kullanmanın avantajları nelerdir?
- Çoklu ajan tasarım kalıbını uygulamanın yapı taşları nelerdir?
- Birden fazla ajanın birbirleriyle nasıl etkileşimde bulunduğunu nasıl görebiliriz?

## Öğrenme Hedefleri

Bu dersten sonra şunları yapabilmelisiniz:

- Çoklu ajanların uygulanabileceği senaryoları tanımlamak
- Tek bir ajan yerine çoklu ajan kullanmanın avantajlarını anlamak
- Çoklu ajan tasarım kalıbını uygulamanın yapı taşlarını kavramak

Büyük resim nedir?

*Çoklu ajanlar, birden fazla ajanın ortak bir hedefe ulaşmak için birlikte çalışmasını sağlayan bir tasarım kalıbıdır*.

Bu kalıp, robotik, otonom sistemler ve dağıtık bilişim gibi çeşitli alanlarda yaygın olarak kullanılmaktadır.

## Çoklu Ajanların Uygulanabilir Olduğu Senaryolar

Peki hangi senaryolar çoklu ajan kullanımı için iyi birer örnektir? Cevap, özellikle aşağıdaki durumlarda çoklu ajanların kullanılmasının faydalı olduğu birçok senaryo vardır:

- **Büyük iş yükleri**: Büyük iş yükleri daha küçük görevlere bölünebilir ve farklı ajanlara atanabilir, bu da paralel işleme ve daha hızlı bitirme sağlar. Bunun bir örneği, büyük bir veri işleme görevidir.
- **Karmaşık görevler**: Karmaşık görevler, büyük iş yüklerinde olduğu gibi, daha küçük alt görevlere bölünebilir ve her biri görevde belirli bir alanda uzmanlaşmış farklı ajanlara atanabilir. İyi bir örnek, otonom araçlarda farklı ajanların navigasyon, engel algılama ve diğer araçlarla iletişim gibi görevleri yönetmesidir.
- **Çeşitli uzmanlıklar**: Farklı ajanlar çeşitli uzmanlıklara sahip olabilir, bu da onların bir tek ajandan daha etkili bir şekilde görevin farklı yönlerini ele almasını sağlar. Bu duruma sağlık sektörü iyi bir örnektir; ajanlar tanı, tedavi planları ve hasta takibi yapabilirler.

## Tek Bir Ajana Karşı Çoklu Ajan Kullanmanın Avantajları

Basit görevler için tek bir ajan sistemi iyi çalışabilir, ancak daha karmaşık görevlerde çoklu ajan kullanmak birkaç avantaj sağlar:

- **Uzmanlaşma**: Her ajan belirli bir görev için uzmanlaşabilir. Tek bir ajandaki uzmanlaşma eksikliği, ajanın her şeyi yapabilmesi ancak karmaşık bir görevle karşılaştığında ne yapacağını şaşırabilmesi anlamına gelir. Örneğin, en iyi olmadığı bir görevi yapmaya çalışabilir.
- **Ölçeklenebilirlik**: Tek bir ajanı aşırı yüklemek yerine daha fazla ajan ekleyerek sistemleri ölçeklendirmek daha kolaydır.
- **Hata Toleransı**: Eğer bir ajan başarısız olursa, diğerleri çalışmaya devam eder ve sistemin güvenilirliği sağlanır.

Bir örnek verelim: bir kullanıcı için bir seyahat rezervasyonu yapalım. Tek ajandan oluşan bir sistem, uçuş bulmaktan otel ve araç kiralamaya kadar rezervasyon sürecinin tüm yönlerini yönetmek zorunda kalır. Bunu tek bir ajanla yapmak için, tüm bu görevleri yapabilen araçlara sahip olması gerekir. Bu, bakımı zor ve ölçeklendirilmesi güç, karmaşık ve monolitik bir sisteme yol açabilir. Birden çok ajandan oluşan sistem ise, uçuş bulmak, otel ve araç kiralamak konusunda uzmanlaşmış farklı ajanlara sahip olabilir. Bu, sistemi daha modüler, bakımı daha kolay ve ölçeklenebilir yapar.

Bunu, seyahat bürosunu tek bir aile işletmesi olarak yürütmek ile bir franchise olarak yürütmek arasındaki farkla karşılaştırabilirsiniz. Aile işletmesinde tek bir ajan seyahat rezervasyon sürecinin tüm yönlerini yönetirken, franchise'da farklı ajanlar farklı yönleri yönetir.

## Çoklu Ajan Tasarım Kalıbının Uygulama Yapı Taşları

Çoklu ajan tasarım kalıbını uygulamadan önce, kalıbı oluşturan yapı taşlarını anlamanız gerekir.

Bunu daha somut hale getirmek için yine bir kullanıcı için seyahat rezervasyonu örneğine bakalım. Bu durumda yapı taşları şunları içerecektir:

- **Ajan İletişimi**: Uçuş bulma, otel rezervasyonu ve araç kiralama ajanlarının, kullanıcının tercihleri ve kısıtlamaları hakkında bilgi paylaşmak için iletişim kurması gerekir. Bu iletişim için protokolleri ve yöntemleri belirlemelisiniz. Bu, uçuş bulma ajanının otel rezervasyon ajanıyla iletişim kurarak otelin uçuş tarihleriyle aynı günler için rezerve edilmesini sağlaması anlamına gelir. Bu, ajanların kullanıcının seyahat tarihleri hakkında bilgi paylaşması gerektiği anlamına gelir; yani *hangi ajanların bilgi paylaştığı ve bilgiyi nasıl paylaştıklarını* karar vermelisiniz.
- **Koordinasyon Mekanizmaları**: Ajanlar, kullanıcının tercihleri ve kısıtlamalarının karşılanmasını sağlamak için eylemlerini koordine etmelidir. Örneğin, kullanıcının tercihi havalimanına yakın bir otel isterken, bir kısıtlama da araçların sadece havalimanında mevcut olması olabilir. Bu durumda otel rezervasyon ajanı, araç kiralama ajanıyla koordinasyon kurmalıdır. Bu, ajanların *eylemlerini nasıl koordine ettiklerine* karar verilmesi demektir.
- **Ajan Mimarisi**: Ajanların, kullanıcının etkileşimlerinden karar verip öğrenebilecek iç yapıya sahip olması gerekir. Bu, uçuş bulma ajanının kullanıcıya hangi uçuşları önereceğine karar verme yapısına sahip olması demektir. Bu, ajanların *kullanıcıyla etkileşimlerinden nasıl karar verdiğine ve öğrenmeye* karar verilmesi demektir. Bir ajanın öğrenmesi ve gelişmesi için örnek olarak, uçuş bulma ajanının geçmiş tercihlere göre uçuş önerisinde bulunmak için makine öğrenimi modeli kullanması verilebilir.
- **Çoklu Ajan Etkileşimlerinin Görünürlüğü**: Birden çok ajanın birbirleriyle nasıl etkileşimde bulunduğunu görebilmelisiniz. Bu, ajan aktiviteleri ve etkileşimlerini takip etmek için araçlar ve teknikler gerektirir. Bunlar, günlük kaydı ve izleme araçları, görselleştirme araçları ve performans metrikleri biçiminde olabilir.
- **Çoklu Ajan Kalıpları**: Merkezi, merkezi olmayan ve hibrit mimariler gibi çoklu ajan sistemleri için farklı kalıplar vardır. Kullanım durumunuza en uygun kalıbı seçmelisiniz.
- **İnsan müdahalesi**: Çoğu durumda bir insan müdahalesi olacaktır ve ajanlara ne zaman insan müdahalesi isteneceğini öğretmeniz gerekir. Bu, ajanların önermediği belirli bir otel veya uçuş isteyen kullanıcı ya da uçuş ya da otel rezervasyonundan önce onay isteyen kullanıcı şeklinde olabilir.

## Çoklu Ajan Etkileşimlerine Görünürlük

Birden fazla ajanın birbirleriyle nasıl etkileşimde bulunduğunu görebiliyor olmak önemlidir. Bu görünürlük, hata ayıklama, optimizasyon ve genel sistem etkinliğinin sağlanması için gereklidir. Bunu sağlamak için ajan etkinliklerini ve etkileşimlerini takip etmek için araçlar ve teknikler olmalıdır. Bunlar, günlük kaydı ve izleme araçları, görselleştirme araçları ve performans metrikleri biçiminde olabilir.

Örneğin, bir kullanıcı için seyahat rezervasyonu yaparken, her ajanın durumu, kullanıcının tercihleri ve kısıtlamaları ile ajanlar arasındaki etkileşimleri gösteren bir gösterge tablonuz olabilir. Bu gösterge tablosu, kullanıcının seyahat tarihlerini, uçuş ajanının önerdiği uçuşları, otel ajanının önerdiği otelleri ve araç kiralama ajanının önerdiği araçları gösterebilir. Bu size ajanların birbirleriyle nasıl etkileştiklerine ve kullanıcının tercihleri ve kısıtlamalarının karşılanıp karşılanmadığına dair net bir görünüm verir.

Bunların her birine daha detaylı bakalım.

- **Günlük Kaydı ve İzleme Araçları**: Her bir aksiyon için günlük kaydı yapılmasını istersiniz. Bir günlük girdisi, işlemi yapan ajan, yapılan işlem, işlemin zamanı ve işlemin sonucu hakkında bilgi tutabilir. Bu bilgiler hata ayıklama, optimizasyon ve daha fazlası için kullanılabilir.
- **Görselleştirme Araçları**: Görselleştirme araçları, ajanlar arasındaki etkileşimleri daha sezgisel bir şekilde görmenize yardımcı olabilir. Örneğin, ajanlar arasındaki bilgi akışını gösteren bir grafik olabilir. Bu, sistemdeki darboğazları, verimsizlikleri ve diğer sorunları tespit etmenize yardımcı olur.
- **Performans Metrikleri**: Performans metrikleri, çoklu ajan sisteminin etkinliğini takip etmenize yardımcı olur. Örneğin, bir görevin tamamlanma süresi, birim zamanda tamamlanan görev sayısı ve ajanların yaptığı önerilerin doğruluğunu takip edebilirsiniz. Bu bilgiler iyileştirme alanlarını belirlemenize ve sistemi optimize etmenize yardımcı olur.

## Çoklu Ajan Kalıpları

Çoklu ajan uygulamaları oluşturmak için kullanabileceğimiz bazı somut kalıplara bakalım. İşte dikkate alınması gereken bazı ilginç kalıplar:

### Grup sohbeti

Bu kalıp, birden fazla ajanın birbirleriyle iletişim kurabildiği bir grup sohbeti uygulaması oluşturmak istediğinizde faydalıdır. Bu kalıp için tipik kullanım senaryoları, ekip işbirliği, müşteri desteği ve sosyal ağlar gibi alanlardır.

Bu kalıpta, her ajan grup sohbetindeki bir kullanıcıyı temsil eder ve mesajlar ajanlar arasında bir mesajlaşma protokolü kullanılarak değiş tokuş edilir. Ajanlar grup sohbetine mesaj gönderebilir, grup sohbetinden mesaj alabilir ve diğer ajanların mesajlarına yanıt verebilir.

Bu kalıp, tüm mesajların merkezi bir sunucu üzerinden yönlendirildiği merkezi bir mimari ile ya da mesajların doğrudan değiş tokuş edildiği merkezi olmayan bir mimari ile uygulanabilir.

![Group chat](../../../translated_images/tr/multi-agent-group-chat.ec10f4cde556babd.webp)

### Görev Devri

Bu kalıp, birden fazla ajanın görevleri birbirine devrettiği bir uygulama oluşturmak istediğinizde faydalıdır.

Bu kalıp için tipik kullanım örnekleri müşteri destek, görev yönetimi ve iş akışı otomasyonudur.

Bu kalıpta, her ajan bir görevi veya iş akışındaki bir adımı temsil eder ve ajanlar önceden tanımlanmış kurallar doğrultusunda görevleri diğer ajanlara devredebilir.

![Hand off](../../../translated_images/tr/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### İşbirlikçi Filtreleme

Bu kalıp, birden fazla ajanın kullanıcılar için önerilerde bulunmak üzere işbirliği yaptığı bir uygulama oluşturmak istediğinizde faydalıdır.

Birden fazla ajanla işbirliği yapmak istemenizin nedeni, her ajanın farklı uzmanlıklara sahip olabilmesi ve öneri sürecine farklı şekillerde katkıda bulunabilmesidir.

Örneğin, bir kullanıcı borsada en iyi hisse senedi önerisi istiyor diyelim.

- **Sektör uzmanı**: Bir ajan belirli bir sektörün uzmanı olabilir.
- **Teknik analiz**: Bir başka ajan teknik analiz uzmanı olabilir.
- **Temel analiz**: Bir diğer ajan ise temel analiz uzmanı olabilir. Bu ajanlar işbirliği yaparak kullanıcıya daha kapsamlı bir öneri sunabilirler.

![Recommendation](../../../translated_images/tr/multi-agent-filtering.d959cb129dc9f608.webp)

## Senaryo: İade süreci

Bir müşterinin bir ürün için iade almak istediği bir senaryoyu düşünün, bu süreçte oldukça fazla ajan yer alabilir, ancak bunu özel iade süreci için ajanlar ve işinizin diğer bölümlerinde kullanılabilecek genel ajanlar olarak bölelim.

**İade sürecine özgü ajanlar**:

İade sürecinde yer alabilecek bazı ajanlar şunlardır:

- **Müşteri ajanı**: Bu ajan müşteriyi temsil eder ve iade sürecini başlatmaktan sorumludur.
- **Satıcı ajanı**: Bu ajan satıcıyı temsil eder ve iadeyi işlemden geçirmekten sorumludur.
- **Ödeme ajanı**: Bu ajan ödeme sürecini temsil eder ve müşterinin ödemesinin iade edilmesinden sorumludur.
- **Çözüm ajanı**: Bu ajan çözüm sürecini temsil eder ve iade sürecinde ortaya çıkan sorunları çözmekten sorumludur.
- **Uyum ajanı**: Bu ajan uyum sürecini temsil eder ve iade sürecinin düzenlemelere ve politikalara uygunluğunu sağlamaktan sorumludur.

**Genel ajanlar**:

Bu ajanlar işinizin diğer bölümlerinde kullanılabilir.

- **Gönderim ajanı**: Bu ajan gönderim sürecini temsil eder ve ürünü satıcıya geri göndermekten sorumludur. Bu ajan hem iade süreci hem de örneğin bir satın alma yoluyla ürünün genel gönderimi için kullanılabilir.
- **Geri bildirim ajanı**: Bu ajan geri bildirim sürecini temsil eder ve müşteriden geri bildirim toplamakla sorumludur. Geri bildirim herhangi bir zamanda alınabilir, sadece iade sürecinde değil.
- **Yükseltme ajanı**: Bu ajan yükseltme sürecini temsil eder ve sorunları daha üst destek seviyesine yükseltmekten sorumludur. Bu tür bir ajan, herhangi bir süreçte bir sorunu yükseltmeniz gerektiğinde kullanılabilir.
- **Bildirim ajanı**: Bu ajan bildirim sürecini temsil eder ve iade sürecinin çeşitli aşamalarında müşteriye bildirim göndermekten sorumludur.
- **Analitik ajanı**: Bu ajan analitik sürecini temsil eder ve iade süreciyle ilişkili verileri analiz etmekten sorumludur.
- **Denetim ajanı**: Bu ajan denetim sürecini temsil eder ve iade sürecinin doğru şekilde yürütüldüğünden emin olmak için denetim yapmaktan sorumludur.
- **Raporlama ajanı**: Bu ajan raporlama sürecini temsil eder ve iade süreci üzerine raporlar hazırlamaktan sorumludur.
- **Bilgi ajanı**: Bu ajan bilgi sürecini temsil eder ve iade süreciyle ilgili bilgilerin bulunduğu bir bilgi tabanını sürdürmekten sorumludur. Bu ajan, iade ve işinizin diğer bölümleri hakkında bilgi sahibi olabilir.
- **Güvenlik ajanı**: Bu ajan güvenlik sürecini temsil eder ve iade sürecinin güvenliğini sağlamaktan sorumludur.
- **Kalite ajanı**: Bu ajan kalite sürecini temsil eder ve iade sürecinin kalitesini sağlamaktan sorumludur.

Daha önce hem iade sürecine özgü hem de işinizin diğer bölümlerinde kullanılabilecek genel ajanlar için oldukça fazla ajan listelendi. Umarım bu, çoklu ajan sisteminizde hangi ajanları kullanacağınıza karar vermeniz için size bir fikir vermiştir.

## Ödev

Bir müşteri destek süreci için çoklu ajan sistemi tasarlayın. Süreçte yer alan ajanları, rolleri ve sorumluluklarını belirleyin ve birbirleriyle nasıl etkileştiklerini açıklayın. Hem müşteri destek sürecine özgü ajanları hem de işinizin diğer bölümlerinde kullanılabilecek genel ajanları göz önünde bulundurun.
> Aşağıdaki çözümü okumadan önce bir düşünün, düşündüğünüzden daha fazla ajana ihtiyacınız olabilir.

> İPUCU: Müşteri destek sürecinin farklı aşamalarını düşünün ve ayrıca herhangi bir sistem için gereken ajanları da göz önünde bulundurun.

## Çözüm

[Çözüm](./solution/solution.md)

## Bilgi Kontrolleri

Soru: Çoklu ajan kullanmayı ne zaman düşünmelisiniz?

- [ ] A1: Küçük bir iş yükünüz ve basit bir göreviniz olduğunda.
- [ ] A2: Büyük bir iş yükünüz olduğunda
- [ ] A3: Basit bir göreviniz olduğunda.

[Çözüm testi](./solution/solution-quiz.md)

## Özet

Bu derste, çoklu ajan tasarım desenine baktık; çoklu ajanların geçerli olduğu senaryoları, tek bir ajan yerine çoklu ajan kullanmanın avantajlarını, çoklu ajan tasarım desenini uygulamanın yapı taşlarını ve birden fazla ajanın birbirleriyle nasıl etkileşimde bulunduğunu görebilmeyi inceledik.

### Çoklu Ajan Tasarım Deseni Hakkında Daha Fazla Sorunuz mu Var?

Diğer öğrenenlerle tanışmak, ofis saatlerine katılmak ve Yapay Zeka Ajanları sorularınızı sormak için [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) topluluğuna katılın.

## Ek kaynaklar

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen tasarım desenleri</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Ajanik tasarım desenleri</a>

## Önceki Ders

[Tasarım Planlama](../07-planning-design/README.md)

## Sonraki Ders

[Yapay Zeka Ajanlarında Meta-biliş](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Feragatname**:
Bu belge, AI çeviri hizmeti [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba gösterilse de, otomatik çevirilerin hatalar veya yanlışlıklar içerebileceğini lütfen unutmayın. Orijinal belge, kendi ana dilinde yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanımı sonucunda oluşabilecek yanlış anlamalar veya yorum hatalarından sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->