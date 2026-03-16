[![Güvenilir AI Ajanları](../../../translated_images/tr/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Bu dersin videosunu görüntülemek için yukarıdaki resme tıklayın)_

# Güvenilir AI Ajanları Oluşturma

## Giriş

Bu ders şunları kapsayacaktır:

- Güvenli ve etkili AI Ajanları nasıl oluşturulur ve dağıtılır
- AI Ajanları geliştirirken önemli güvenlik hususları
- AI Ajanları geliştirirken veri ve kullanıcı gizliliğinin nasıl korunacağı

## Öğrenme Hedefleri

Bu dersi tamamladıktan sonra şunları bileceksiniz:

- AI Ajanları oluştururken riskleri tanımlamak ve azaltmak
- Verilerin ve erişimin düzgün yönetilmesini sağlamak için güvenlik önlemleri uygulamak
- Veri gizliliğini koruyan ve kaliteli bir kullanıcı deneyimi sunan AI Ajanları oluşturmak

## Güvenlik

Öncelikle güvenli ajanik uygulamalar oluşturmayı inceleyelim. Güvenlik, AI ajanının tasarlandığı gibi çalışması demektir. Ajanik uygulamaların geliştiricileri olarak, güvenliği en üst düzeye çıkarmak için yöntem ve araçlara sahibiz:

### Bir Sistem Mesajı Çerçevesi Oluşturma

Eğer daha önce Büyük Dil Modelleri (LLM'ler) kullanarak bir AI uygulaması oluşturduysanız, sağlam bir sistem istemi ya da sistem mesajı tasarlamanın önemini biliriniz. Bu istemler, LLM'nin kullanıcı ve veriyle nasıl etkileşime gireceğine dair üst kuralları, talimatları ve yönergeleri belirler.

AI Ajanları için, sistem istemi daha da önemlidir çünkü AI Ajanları, onlara tasarladığımız görevleri tamamlamak için çok özel talimatlara ihtiyaç duyacaktır.

Ölçeklenebilir sistem istemleri oluşturmak için, uygulamamızda bir veya daha fazla ajan oluşturmak üzere bir sistem mesajı çerçevesi kullanabiliriz:

![Bir Sistem Mesajı Çerçevesi Oluşturma](../../../translated_images/tr/system-message-framework.3a97368c92d11d68.webp)

#### Adım 1: Bir Meta Sistem Mesajı Oluşturun

Meta istem, oluşturduğumuz ajanlar için sistem istemlerini üretmek üzere bir LLM tarafından kullanılacaktır. İhtiyaç halinde birden fazla ajanı verimli bir şekilde oluşturabilmek için bunu bir şablon olarak tasarlarız.

İşte LLM'ye vereceğimiz bir meta sistem mesajı örneği:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Adım 2: Temel bir istem oluşturun

Sonraki adım, AI Ajanını tanımlayan temel bir istem oluşturmaktır. Ajanın rolünü, tamamlayacağı görevleri ve diğer sorumluluklarını dahil etmelisiniz.

İşte bir örnek:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Adım 3: Temel Sistem Mesajını LLM'ye Sağlayın

Şimdi, bu sistem mesajını meta sistem mesajını sistem mesajı ve temel sistem mesajımız olarak sağlayarak optimize edebiliriz.

Bu, AI ajanlarımızı yönlendirmek için daha iyi tasarlanmış bir sistem mesajı üretir:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Adım 4: Yineleyin ve İyileştirin

Bu sistem mesajı çerçevesinin değeri, birden fazla ajandan sistem mesajları oluşturmayı kolayca ölçeklendirmek ve zaman içinde sistem mesajlarınızı iyileştirmektir. Tam kullanım durumunuz için sistem mesajınızın ilk seferde işe yaraması nadirdir. Temel sistem mesajını küçük değişikliklerle düzenleyip sistemden geçirerek sonuçları karşılaştırıp değerlendirebilme imkanı sağlar.

## Tehditleri Anlama

Güvenilir AI ajanları oluşturmak için, AI ajanınıza yönelik riskleri ve tehditleri anlamak ve azaltmak önemlidir. AI ajanlarına yönelik bazı farklı tehditlere ve bunlara nasıl daha iyi hazırlanabileceğinize bakalım.

![Tehditleri Anlama](../../../translated_images/tr/understanding-threats.89edeada8a97fc0f.webp)

### Görev ve Talimat

**Açıklama:** Saldırganlar, istem veya girdileri manipüle ederek AI ajanının talimatlarını veya hedeflerini değiştirmeye çalışır.

**Azaltma:** Potansiyel tehlikeli istemleri AI Ajanı işlemden önce tespit etmek için doğrulama kontrolleri ve girdi filtreleri uygulayın. Bu saldırılar genellikle ajanla sık etkileşim gerektirdiğinden, sohbetteki tur sayısını sınırlamak bu tür saldırıları önlemenin diğer bir yoludur.

### Kritik Sistemlere Erişim

**Açıklama:** AI ajanı, hassas veriler tutan sistemlere ve hizmetlere erişim sağlıyorsa, saldırganlar ajan ile bu hizmetler arasındaki iletişimi ele geçirebilir. Bunlar doğrudan saldırılar veya ajan aracılığıyla bu sistemler hakkında bilgi edinme girişimleri olabilir.

**Azaltma:** AI ajanlarının bu tür saldırıları önlemek için sistemlere sadece ihtiyaç duydukça erişimi olmalıdır. Ajan ile sistem arasındaki iletişim de güvenli olmalıdır. Kimlik doğrulama ve erişim kontrolünün uygulanması, bu bilgiyi korumanın başka bir yoludur.

### Kaynak ve Hizmet Aşırı Yüklenmesi

**Açıklama:** AI ajanları görevleri tamamlamak için farklı araçlar ve hizmetlere erişebilir. Saldırganlar, AI Ajanı üzerinden yüksek hacimli istekler göndererek bu hizmetlere saldırabilir, bu da sistem arızalarına veya yüksek maliyetlere yol açabilir.

**Azaltma:** AI ajanının bir hizmete yapabileceği istek sayısını sınırlayan politikalar uygulayın. Sohbet dönüş sayılarını ve AI ajanına yapılan istekleri sınırlandırmak bu tür saldırıları önlemenin diğer bir yoludur.

### Bilgi Tabanı Zehirlenmesi

**Açıklama:** Bu saldırı türü AI ajanını doğrudan hedef almaz, ancak AI ajanının kullanacağı bilgi tabanı ve diğer hizmetleri hedefler. Bu, AI ajanının bir görevi tamamlamak için kullanacağı verilerin veya bilgilerin bozulmasını içerebilir; bu da kullanıcılara taraflı veya istenmeyen yanıtlar verilmesine yol açabilir.

**Azaltma:** AI ajanının iş akışlarında kullanacağı verileri düzenli olarak doğrulayın. Bu verilere erişimin güvenli olduğundan ve yalnızca güvenilen kişiler tarafından değiştirildiğinden emin olun.

### Zincirleme Hatalar

**Açıklama:** AI ajanları görevleri tamamlamak için çeşitli araçlara ve hizmetlere erişir. Saldırganların neden olduğu hatalar, AI ajanının bağlı olduğu diğer sistemlerin arızalanmasına sebep olabilir; bu da saldırının daha yaygınlaşmasına ve sorun gidermesinin zorlaşmasına yol açar.

**Azaltma:** Bunu önlemenin bir yolu, AI Ajanını, örneğin bir Docker konteynerinde görevleri yerine getirerek, sınırlı bir ortamda çalıştırmaktır; böylece doğrudan sistem saldırıları önlenir. Belirli sistemler hata verdiğinde devreye giren yedekleme mekanizmaları ve yeniden deneme mantığı oluşturmak da daha büyük sistem hatalarını önlemenin diğer bir yoludur.

## İnsan Döngüde (Human-in-the-Loop)

Güvenilir AI Ajan sistemleri oluşturmanın bir diğer etkili yolu ise İnsan Döngüde yaklaşımıdır. Bu, kullanıcıların çalışma sırasında Ajanlara geri bildirim sağlayabildiği bir akış oluşturur. Kullanıcılar temelde çok ajanlı bir sistemde ajanlar gibi hareket eder ve çalışan sürecin onaylanması veya sonlandırılması görevini üstlenir.

![Döngüde İnsan](../../../translated_images/tr/human-in-the-loop.5f0068a678f62f4f.webp)

Bu kavramın nasıl uygulandığını göstermek için AutoGen kullanan bir kod örneği:

```python

# Ajanları oluşturun.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Kullanıcı girdisini konsoldan almak için input() kullanın.

# Kullanıcı "ONAYLA" dediğinde sohbeti sonlandıracak bitiş koşulunu oluşturun.
termination = TextMentionTermination("APPROVE")

# Takımı oluşturun.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Sohbeti çalıştırın ve konsola aktarın.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Bir betikte çalıştırılırken asyncio.run(...) kullanın.
await Console(stream)

```

## Sonuç

Güvenilir AI ajanları oluşturmak dikkatli tasarım, sağlam güvenlik önlemleri ve sürekli yineleme gerektirir. Yapılandırılmış meta istem sistemleri uygulayarak, potansiyel tehditleri anlayarak ve azaltma stratejileri uygulayarak, geliştiriciler hem güvenli hem de etkili AI ajanlar yaratabilir. Ayrıca insan döngüde yaklaşımını entegre etmek, AI ajanlarının kullanıcı ihtiyaçlarıyla uyumlu kalmasını sağlarken riskleri minimize eder. AI geliştikçe, güvenlik, gizlilik ve etik hususlarda proaktif bir duruş sürdürmek, AI ile çalışan sistemlerde güven ve güvenilirliği artırmanın anahtarı olacaktır.

### Güvenilir AI Ajanları Oluşturma ile İlgili Daha Fazla Sorunuz mu Var?

Diğer öğrenenlerle tanışmak, danışma saatlerine katılmak ve AI Ajanları ile ilgili sorularınızı sormak için [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)’a katılın.

## Ek Kaynaklar

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Sorumlu AI genel bakışı</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Jeneratif AI modelleri ve AI uygulamalarının değerlendirilmesi</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Güvenlik sistem mesajları</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Risk Değerlendirme Şablonu</a>

## Önceki Ders

[Agentic RAG](../05-agentic-rag/README.md)

## Sonraki Ders

[Planlama Tasarım Deseni](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Feragatname**:
Bu belge, AI çeviri servisi [Co-op Translator](https://github.com/Azure/co-op-translator) kullanılarak çevrilmiştir. Doğruluk için çaba göstersek de, otomatik çevirilerin hatalar veya yanlışlıklar içerebileceğini lütfen unutmayınız. Orijinal belge, kendi diliyle yetkili kaynak olarak kabul edilmelidir. Kritik bilgiler için profesyonel insan çevirisi önerilir. Bu çevirinin kullanımı sonucu oluşabilecek yanlış anlamalar veya yorum hatalarından sorumlu değiliz.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->