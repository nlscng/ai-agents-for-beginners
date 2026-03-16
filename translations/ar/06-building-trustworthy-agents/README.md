[![وكلاء الذكاء الاصطناعي الموثوق بهم](../../../translated_images/ar/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(انقر على الصورة أعلاه لمشاهدة فيديو هذا الدرس)_

# بناء وكلاء ذكاء اصطناعي موثوق بهم

## المقدمة

سيغطي هذا الدرس:

- كيفية بناء ونشر وكلاء ذكاء اصطناعي آمنين وفعالين  
- اعتبارات أمنية هامة عند تطوير وكلاء الذكاء الاصطناعي  
- كيفية الحفاظ على خصوصية البيانات والمستخدم عند تطوير وكلاء الذكاء الاصطناعي  

## أهداف التعلم

بعد إكمال هذا الدرس، ستعرف كيف:

- تحديد وتخفيف المخاطر عند إنشاء وكلاء ذكاء اصطناعي  
- تنفيذ تدابير أمنية لضمان إدارة البيانات والوصول بشكل صحيح  
- إنشاء وكلاء ذكاء اصطناعي يحافظون على خصوصية البيانات ويوفرون تجربة مستخدم ذات جودة  

## السلامة

دعونا ننظر أولاً إلى بناء تطبيقات وكيلة آمنة. تعني السلامة أن وكيل الذكاء الاصطناعي يعمل كما هو مصمم. كمطورين لتطبيقات وكيلة، لدينا أساليب وأدوات لتعظيم السلامة:

### بناء إطار عمل لرسالة النظام

إذا سبق وأنشأت تطبيق ذكاء اصطناعي باستخدام نماذج اللغة الكبيرة (LLMs)، فأنت تعرف أهمية تصميم موجه نظام قوي أو رسالة نظام. هذه الموجهات تحدد القواعد الميتا، والتعليمات، والإرشادات لكيفية تفاعل نموذج اللغة الكبير مع المستخدم والبيانات.

لوكلاء الذكاء الاصطناعي، تعد موجهات النظام أكثر أهمية لأن الوكلاء سيحتاجون إلى تعليمات دقيقة للغاية لإكمال المهام التي صممناها لهم.

لإنشاء موجهات نظام قابلة للتوسع، يمكننا استخدام إطار عمل رسالة النظام لبناء واحد أو أكثر من الوكلاء في تطبيقنا:

![بناء إطار عمل رسالة النظام](../../../translated_images/ar/system-message-framework.3a97368c92d11d68.webp)

#### الخطوة 1: إنشاء رسالة نظام ميتا

سيُستخدم الموجه الميتا بواسطة نموذج اللغة الكبير لتوليد موجهات النظام للوكلاء الذين ننشئهم. نصممه كقالب حتى نتمكن من إنشاء وكلاء متعددين بكفاءة إذا لزم الأمر.

إليك مثال على رسالة نظام ميتا سنعطيها لنموذج اللغة الكبير:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```
  
#### الخطوة 2: إنشاء موجه أساسي

الخطوة التالية هي إنشاء موجه أساسي لوصف وكيل الذكاء الاصطناعي. يجب أن تتضمن دور الوكيل، والمهام التي سيكملها، وأي مسؤوليات أخرى للوكيل.

إليك مثالًا:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```
  
#### الخطوة 3: توفير رسالة نظام أساسية لنموذج اللغة الكبير

الآن يمكننا تحسين رسالة النظام هذه من خلال تقديم رسالة النظام الميتا كرسالة النظام ورسالة النظام الأساسية الخاصة بنا.

هذا سيولد رسالة نظام مصممة بشكل أفضل لتوجيه وكلاء الذكاء الاصطناعي لدينا:

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
  
#### الخطوة 4: التكرار والتحسين

قيمة إطار عمل رسالة النظام هذا هي القدرة على توسيع إنشاء رسائل النظام من عدة وكلاء بسهولة وكذلك تحسين رسائل النظام بمرور الوقت. نادرًا ما يكون لديك رسالة نظام تعمل من المرة الأولى لاستخدامك الكامل. القدرة على إجراء تعديلات وتحسينات صغيرة عن طريق تغيير رسالة النظام الأساسية وتشغيلها عبر النظام ستتيح لك مقارنة النتائج وتقييمها.

## فهم التهديدات

لبناء وكلاء ذكاء اصطناعي موثوقين، من المهم فهم وتخفيف المخاطر والتهديدات التي تواجه وكيل الذكاء الاصطناعي الخاص بك. دعونا نلقي نظرة على بعض التهديدات المختلفة لوكلاء الذكاء الاصطناعي وكيف يمكنك التخطيط والاستعداد بشكل أفضل لها.

![فهم التهديدات](../../../translated_images/ar/understanding-threats.89edeada8a97fc0f.webp)

### المهام والتعليمات

**الوصف:** يحاول المهاجمون تغيير تعليمات أو أهداف وكيل الذكاء الاصطناعي من خلال الموجهات أو التلاعب بالإدخالات.

**التخفيف:** قم بتنفيذ فحوصات التحقق ومرشحات الإدخال لاكتشاف الموجهات الخطرة المحتملة قبل معالجتها من قبل الوكيل. ونظرًا لأن هذه الهجمات عادة تتطلب تفاعلًا متكررًا مع الوكيل، فإن تحديد عدد الأدوار في المحادثة هو طريقة أخرى لمنع هذه الأنواع من الهجمات.

### الوصول إلى الأنظمة الحرجة

**الوصف:** إذا كان لوكيل الذكاء الاصطناعي وصول إلى أنظمة وخدمات تخزن بيانات حساسة، يمكن للمهاجمين اختراق الاتصال بين الوكيل وهذه الخدمات. يمكن أن تكون هذه هجمات مباشرة أو محاولات غير مباشرة للحصول على معلومات حول هذه الأنظمة عبر الوكيل.

**التخفيف:** يجب أن يكون لوكلاء الذكاء الاصطناعي وصول إلى الأنظمة فقط عند الحاجة لمنع هذه الأنواع من الهجمات. كما يجب أن يكون الاتصال بين الوكيل والنظام آمنًا. تنفيذ المصادقة والتحكم في الوصول هو طريقة أخرى لحماية هذه المعلومات.

### تحميل الموارد والخدمات بشكل زائد

**الوصف:** يمكن للوكلاء الوصول إلى أدوات وخدمات مختلفة لإكمال المهام. يمكن للمهاجمين استخدام هذه القدرة للهجوم على هذه الخدمات عن طريق إرسال طلبات بكميات كبيرة عبر وكيل الذكاء الاصطناعي، مما قد يؤدي إلى فشل الأنظمة أو تكاليف مرتفعة.

**التخفيف:** تنفيذ سياسات لتحديد عدد الطلبات التي يمكن أن يرسلها وكيل الذكاء الاصطناعي إلى خدمة ما. تحديد عدد أدوار المحادثة والطلبات لوكيلك هو طريقة أخرى لمنع هذه الأنواع من الهجمات.

### تسميم قاعدة المعرفة

**الوصف:** لا يستهدف هذا النوع من الهجمات وكيل الذكاء الاصطناعي مباشرة، بل يستهدف قاعدة المعرفة والخدمات الأخرى التي سيستخدمها الوكيل. قد ينطوي ذلك على إفساد البيانات أو المعلومات التي سيستخدمها الوكيل لإكمال مهمة، مما يؤدي إلى استجابات متحيزة أو غير مقصودة للمستخدم.

**التخفيف:** قم بالتحقق المنتظم من البيانات التي سيستخدمها وكيل الذكاء الاصطناعي في سير العمل الخاصة به. تأكد من أن الوصول إلى هذه البيانات آمن ولا يتم تعديلها إلا من قبل أشخاص موثوقين لتجنب هذا النوع من الهجمات.

### الأخطاء المتسلسلة

**الوصف:** يصل وكلاء الذكاء الاصطناعي إلى أدوات وخدمات مختلفة لإكمال المهام. يمكن أن تؤدي الأخطاء التي يسببها المهاجمون إلى فشل أنظمة أخرى يرتبط بها الوكيل، مما يؤدي إلى انتشار الهجوم وجعله أصعب في التشخيص.

**التخفيف:** إحدى الطرق لتجنب ذلك هي تشغيل وكيل الذكاء الاصطناعي في بيئة محدودة، مثل أداء المهام في حاوية Docker، لمنع الهجمات المباشرة على النظام. إنشاء آليات نسخ احتياطي ومنطق إعادة المحاولة عند استجابة أنظمة معينة بخطأ هو طريقة أخرى لمنع فشل الأنظمة الكبيرة.

## الإنسان في الحلقة

طريقة فعالة أخرى لبناء أنظمة وكلاء ذكاء اصطناعي موثوق بها هي استخدام الإنسان في الحلقة. هذا يخلق تدفقًا يمكن للمستخدمين فيه تقديم ملاحظات للوكلاء أثناء التشغيل. يتصرف المستخدمون أساسًا كوكيل في نظام تعدد الوكلاء من خلال تقديم الموافقة أو إنهاء العملية الجارية.

![الإنسان في الحلقة](../../../translated_images/ar/human-in-the-loop.5f0068a678f62f4f.webp)

إليك قطعة كود تستخدم AutoGen لعرض كيفية تنفيذ هذا المفهوم:

```python

# إنشاء الوكلاء.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # استخدم input() للحصول على إدخال المستخدم من وحدة التحكم.

# أنشئ شرط الإنهاء الذي سينهي المحادثة عندما يقول المستخدم "APPROVE".
termination = TextMentionTermination("APPROVE")

# إنشاء الفريق.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# تشغيل المحادثة والبث إلى وحدة التحكم.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# استخدم asyncio.run(...) عند التشغيل في سكريبت.
await Console(stream)

```
  
## الخلاصة

يتطلب بناء وكلاء ذكاء اصطناعي موثوق بهم تصميمًا دقيقًا، وتدابير أمنية قوية، وتكرارًا مستمرًا. من خلال تنفيذ أنظمة موجهات ميتا منظمة، وفهم التهديدات المحتملة، وتطبيق استراتيجيات التخفيف، يمكن للمطورين إنشاء وكلاء ذكاء اصطناعي آمنين وفعالين. بالإضافة إلى ذلك، يضمن دمج نهج الإنسان في الحلقة بقاء وكلاء الذكاء الاصطناعي متوافقين مع احتياجات المستخدم مع تقليل المخاطر. مع استمرار تطور الذكاء الاصطناعي، ستظل المحافظة على موقف استباقي بشأن الأمان والخصوصية والاعتبارات الأخلاقية مفتاحًا لتعزيز الثقة والموثوقية في أنظمة الذكاء الاصطناعي.

### هل لديك المزيد من الأسئلة حول بناء وكلاء ذكاء اصطناعي موثوق بهم؟

انضم إلى [خادم Microsoft Foundry على Discord](https://aka.ms/ai-agents/discord) للقاء متعلمين آخرين، وحضور ساعات المكتب، والحصول على إجابات لأسئلتك حول وكلاء الذكاء الاصطناعي.

## موارد إضافية

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">نظرة عامة على الذكاء الاصطناعي المسؤول</a>  
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">تقييم نماذج الذكاء الاصطناعي التوليدية والتطبيقات</a>  
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">رسائل نظام الأمان</a>  
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">نموذج تقييم المخاطر</a>  

## الدرس السابق

[Agentic RAG](../05-agentic-rag/README.md)

## الدرس التالي

[نمط تصميم التخطيط](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**تنويه**:  
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). وعلى الرغم من سعينا لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الرسمي والمعتمد. للمعلومات الحيوية، يُنصح بالاعتماد على الترجمة المهنية البشرية. نحن غير مسؤولين عن أي سوء فهم أو تفسير خاطئ ناتج عن استخدام هذه الترجمة.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->