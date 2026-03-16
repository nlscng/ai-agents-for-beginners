[![نمایندگان هوش مصنوعی قابل اعتماد](../../../translated_images/fa/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(برای مشاهده ویدئوی این درس روی تصویر بالا کلیک کنید)_

# ساخت نمایندگان هوش مصنوعی قابل اعتماد

## معرفی

این درس مباحث زیر را پوشش خواهد داد:

- نحوه ساخت و استقرار نمایندگان هوش مصنوعی ایمن و موثر
- ملاحظات مهم امنیتی هنگام توسعه نمایندگان هوش مصنوعی.
- نحوه حفظ داده‌ها و حریم خصوصی کاربران هنگام توسعه نمایندگان هوش مصنوعی.

## اهداف یادگیری

پس از اتمام این درس، شما خواهید دانست چگونه:

- خطرات را هنگام ایجاد نمایندگان هوش مصنوعی شناسایی و کاهش دهید.
- اقدامات امنیتی را به منظور مدیریت صحیح داده‌ها و دسترسی‌ها پیاده‌سازی کنید.
- نمایندگان هوش مصنوعی‌ای ایجاد کنید که حریم خصوصی داده‌ها را حفظ کرده و تجربه کاربری با کیفیتی ارائه دهند.

## ایمنی

ابتدا بیایید به ساخت برنامه‌های عامل محور ایمن بپردازیم. ایمنی به این معنی است که نماینده هوش مصنوعی طبق طراحی عمل کند. به عنوان سازندگان برنامه‌های عامل محور، روش‌ها و ابزارهایی داریم تا حداکثر ایمنی را تضمین کنیم:

### ساختار فریمورک پیام سیستم

اگر تاکنون برنامه هوش مصنوعی با استفاده از مدل‌های زبانی بزرگ (LLMs) ساخته‌اید، اهمیت طراحی یک پرامپت سیستم یا پیام سیستم قوی را می‌دانید. این پرامپت‌ها قوانین اصلی، دستورالعمل‌ها و راهنمایی‌هایی را تعیین می‌کنند که چگونه LLM با کاربر و داده‌ها تعامل خواهد داشت.

برای نمایندگان هوش مصنوعی، پرامپت سیستم اهمیت بیشتری دارد چون نمایندگان به دستورالعمل‌های بسیار خاصی نیاز دارند تا کارهای طراحی شده را انجام دهند.

برای ایجاد پرامپت‌های سیستمی مقیاس‌پذیر، می‌توانیم از یک فریمورک پیام سیستم برای ساخت یک یا چند نماینده در برنامه خود استفاده کنیم:

![ساختار فریمورک پیام سیستم](../../../translated_images/fa/system-message-framework.3a97368c92d11d68.webp)

#### گام ۱: ایجاد یک پیام متا سیستم

پرامپت متا توسط یک LLM استفاده می‌شود تا پرامپت‌های سیستمی برای نمایندگانی که می‌سازیم تولید کند. آن را به صورت قالبی طراحی می‌کنیم تا اگر لازم باشد بتوانیم به صورت بهینه چند نماینده ایجاد کنیم.

مثالی از یک پیام متا سیستم که به LLM می‌دهیم در اینجا آمده است:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### گام ۲: ایجاد یک پرامپت پایه

گام بعدی ایجاد یک پرامپت پایه برای توصیف نماینده هوش مصنوعی است. باید نقش نماینده، کارهایی که نماینده انجام می‌دهد و هر مسئولیت دیگری از نماینده را شامل شود.

مثالی در اینجا آمده است:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### گام ۳: ارائه پیام پایه سیستم به LLM

اکنون می‌توانیم این پیام سیستم را با ارائه پیام متا سیستم به عنوان پیام سیستم و پیام پایه خود بهینه کنیم.

این باعث تولید پیام سیستمی می‌شود که برای هدایت نمایندگان هوش مصنوعی ما بهتر طراحی شده است:

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

#### گام ۴: تکرار و بهبود

ارزش این فریمورک پیام سیستم در این است که بتوانیم ساخت پیام‌های سیستمی از چند نماینده را آسان‌تر کنیم و همچنین پیام‌های سیستم خود را در طول زمان بهبود دهیم. به ندرت پیش می‌آید که پیام سیستمی از همان ابتدا برای کل مورد استفاده شما کار کند. توانایی ایجاد اصلاحات کوچک و بهبودها با تغییر پیام پایه سیستم و اجرای آن از طریق سیستم به شما امکان می‌دهد نتایج را مقایسه و ارزیابی کنید.

## درک تهدیدها

برای ساخت نمایندگان هوش مصنوعی قابل اعتماد، مهم است که خطرات و تهدیدها را درک کرده و کاهش دهید. بیایید به برخی از تهدیدهای مختلف نمایندگان هوش مصنوعی نگاه کنیم و ببینیم چگونه می‌توانید بهتر برنامه‌ریزی و آماده شوید.

![درک تهدیدها](../../../translated_images/fa/understanding-threats.89edeada8a97fc0f.webp)

### دستور کار و راهنمایی

**توضیح:** مهاجمان تلاش می‌کنند با استفاده از پرامپت‌دهی یا دستکاری ورودی‌ها، دستورالعمل‌ها یا اهداف نماینده هوش مصنوعی را تغییر دهند.

**کاهش:** بررسی‌های اعتبارسنجی و فیلترهای ورودی را برای شناسایی پرامپت‌های خطرناک احتمالی قبل از پردازش توسط نماینده هوش مصنوعی اجرا کنید. از آنجا که این حملات معمولاً نیاز به تعامل مکرر با نماینده دارند، محدود کردن تعداد گردش‌های مکالمه روش دیگری برای جلوگیری از این نوع حملات است.

### دسترسی به سیستم‌های حیاتی

**توضیح:** اگر نماینده هوش مصنوعی به سیستم‌ها و خدماتی که داده‌های حساس ذخیره می‌کنند دسترسی داشته باشد، مهاجمان می‌توانند ارتباط بین نماینده و این خدمات را به خطر بیندازند. این ممکن است حملات مستقیم یا تلاش‌های غیرمستقیم برای کسب اطلاعات از طریق نماینده باشد.

**کاهش:** نمایندگان هوش مصنوعی باید فقط در صورت نیاز به سیستم‌ها دسترسی داشته باشند تا از این نوع حملات جلوگیری شود. ارتباط بین نماینده و سیستم نیز باید ایمن باشد. اجرای احراز هویت و کنترل دسترسی روش دیگری برای حفاظت از این اطلاعات است.

### بارگذاری بیش از حد منابع و خدمات

**توضیح:** نمایندگان هوش مصنوعی می‌توانند به ابزارها و خدمات مختلفی برای انجام وظایف دسترسی داشته باشند. مهاجمان می‌توانند از این قابلیت برای حمله به این خدمات با ارسال حجم بالایی از درخواست‌ها از طریق نماینده استفاده کنند که ممکن است منجر به خرابی سیستم یا هزینه‌های بالا شود.

**کاهش:** سیاست‌هایی برای محدود کردن تعداد درخواست‌هایی که یک نماینده هوش مصنوعی می‌تواند به یک خدمت ارسال کند پیاده‌سازی کنید. محدود کردن تعداد گردش‌های مکالمه و درخواست‌ها به نماینده هوش مصنوعی شما نیز روش دیگری برای جلوگیری از این نوع حملات است.

### مسمومیت پایگاه دانش

**توضیح:** این نوع حمله مستقیماً نماینده هوش مصنوعی را هدف قرار نمی‌دهد بلکه پایگاه دانش و سایر خدماتی که نماینده استفاده می‌کند را هدف می‌گیرد. این ممکن است شامل خراب کردن داده‌ها یا اطلاعاتی باشد که نماینده برای انجام کار استفاده می‌کند که منجر به پاسخ‌های جانبدارانه یا ناخواسته به کاربر می‌شود.

**کاهش:** بررسی منظم داده‌هایی که نماینده هوش مصنوعی در جریان کار خود استفاده می‌کند را انجام دهید. اطمینان حاصل کنید که دسترسی به این داده‌ها ایمن است و فقط توسط افراد مورد اعتماد تغییر می‌کند تا از این نوع حمله جلوگیری شود.

### خطاهای زنجیره‌ای

**توضیح:** نمایندگان هوش مصنوعی به ابزارها و خدمات مختلفی برای انجام وظایف دسترسی دارند. خطاهای ایجاد شده توسط مهاجمان می‌تواند منجر به خرابی سایر سیستم‌هایی شود که نماینده به آن‌ها متصل است و باعث شود حمله گسترده‌تر شده و سخت‌تر رفع خطا شود.

**کاهش:** یکی از روش‌ها برای جلوگیری از این موضوع این است که نماینده هوش مصنوعی در محیط محدودی مانند اجرای وظایف در یک کانتینر داکر فعالیت کند تا از حملات مستقیم به سیستم جلوگیری شود. ایجاد مکانیزم‌های پشتیبان و منطق تکرار در مواقعی که برخی سیستم‌ها با خطا پاسخ می‌دهند روش دیگری برای جلوگیری از خرابی‌های گسترده‌تر است.

## حضور انسان در چرخه

روش مؤثر دیگر برای ساخت سیستم‌های نماینده هوش مصنوعی قابل اعتماد، استفاده از حضور انسان در چرخه است. این روشی ایجاد می‌کند که کاربران می‌توانند در حین اجرا به نمایندگان بازخورد دهند. کاربران عملاً به عنوان نمایندگانی در یک سیستم چند نماینده‌ای فعالیت می‌کنند و با ارائه تأیید یا پایان روند اجرا مشارکت دارند.

![انسان در چرخه](../../../translated_images/fa/human-in-the-loop.5f0068a678f62f4f.webp)

در اینجا یک قطعه کد با استفاده از AutoGen برای نشان دادن نحوه پیاده‌سازی این مفهوم آمده است:

```python

# ایجاد نمایندگان.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # استفاده از input() برای دریافت ورودی کاربر از کنسول.

# ایجاد شرط خاتمه که وقتی کاربر "APPROVE" می‌گوید، گفتگو را پایان می‌دهد.
termination = TextMentionTermination("APPROVE")

# ایجاد تیم.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# اجرای گفتگو و پخش آن به کنسول.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# استفاده از asyncio.run(...) هنگام اجرای اسکریپت.
await Console(stream)

```

## نتیجه‌گیری

ساخت نمایندگان هوش مصنوعی قابل اعتماد نیازمند طراحی دقیق، اقدامات امنیتی قوی و تکرار مداوم است. با اجرای سیستم‌های ساختاریافته متاپرامپت، درک تهدیدات احتمالی و اعمال راهکارهای کاهش، توسعه‌دهندگان می‌توانند نمایندگانی بسازند که ایمن و مؤثر باشند. علاوه بر این، استفاده از رویکرد حضور انسان در چرخه اطمینان می‌دهد که نمایندگان هوش مصنوعی با نیازهای کاربران همسو باقی بمانند و در عین حال ریسک‌ها کاهش یابند. همانطور که هوش مصنوعی پیشرفت می‌کند، حفظ رویکرد پیشگیرانه نسبت به امنیت، حریم خصوصی و ملاحظات اخلاقی برای ایجاد اعتماد و اطمینان در سیستم‌های مبتنی بر هوش مصنوعی حیاتی خواهد بود.

### سوالات بیشتری درباره ساخت نمایندگان هوش مصنوعی قابل اعتماد دارید؟

به [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) بپیوندید تا با سایر یادگیرندگان دیدار کنید، در ساعات اداری شرکت کنید و سوالات خود درباره نمایندگان هوش مصنوعی را پاسخ بگیرید.

## منابع اضافی

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">نمای کلی هوش مصنوعی مسئولانه</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">ارزیابی مدل‌های هوش مصنوعی مولد و برنامه‌های هوش مصنوعی</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">پیام‌های سیستم ایمنی</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">قالب ارزیابی ریسک</a>

## درس قبلی

[Agentic RAG](../05-agentic-rag/README.md)

## درس بعدی

[الگوی طراحی برنامه‌ریزی](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**سلب مسئولیت**:
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نواقصی باشند. سند اصلی به زبان اصلی آن باید به‌عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، استفاده از ترجمه حرفه‌ای توسط انسان توصیه می‌شود. ما مسئول هیچ گونه سوءتفاهم یا برداشت نادرست ناشی از استفاده از این ترجمه نیستیم.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->