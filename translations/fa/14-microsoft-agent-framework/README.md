# بررسی چارچوب عامل مایکروسافت

![Agent Framework](../../../translated_images/fa/lesson-14-thumbnail.90df0065b9d234ee.webp)

### مقدمه

این درس شامل موارد زیر است:

- درک چارچوب عامل مایکروسافت: ویژگی‌های کلیدی و ارزش آن  
- بررسی مفاهیم کلیدی چارچوب عامل مایکروسافت
- مقایسه MAF با Semantic Kernel و AutoGen: راهنمای مهاجرت

## اهداف یادگیری

پس از اتمام این درس، شما خواهید دانست چگونه:

- عوامل هوش مصنوعی آماده تولید را با استفاده از چارچوب عامل مایکروسافت بسازید
- ویژگی‌های اصلی چارچوب عامل مایکروسافت را در موارد استفاده عاملیت خود به کار ببرید
- چارچوب‌ها و ابزارهای عاملی موجود را مهاجرت داده و ادغام کنید  

## نمونه‌های کد  

نمونه‌های کد برای [چارچوب عامل مایکروسافت (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) در این مخزن در فایل‌های `xx-python-agent-framework` و `xx-dotnet-agent-framework` قرار دارند.

## درک چارچوب عامل مایکروسافت

![Framework Intro](../../../translated_images/fa/framework-intro.077af16617cf130c.webp)

[چارچوب عامل مایکروسافت (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) بر اساس تجربیات و یادگیری‌های Semantic Kernel و AutoGen ساخته شده است. این چارچوب انعطاف‌پذیری لازم برای پاسخگویی به انواع زیادی از موارد استفاده عاملی که هم در محیط‌های تولید و هم تحقیق دیده می‌شود را ارائه می‌دهد، از جمله:

- **ارکستراسیون عامل ترتیبی** در سناریوهایی که گردش‌های کاری مرحله به مرحله لازم است.
- **ارکستراسیون همزمان** در سناریوهایی که عوامل باید وظایف را هم‌زمان انجام دهند.
- **ارکستراسیون چت گروهی** در سناریوهایی که عوامل می‌توانند با هم روی یک وظیفه همکاری کنند.
- **ارکستراسیون انتقال وظیفه** در سناریوهایی که عوامل هنگام تکمیل زیروظایف وظیفه را به یکدیگر واگذار می‌کنند.
- **ارکستراسیون مغناطیسی** در سناریوهایی که عامل مدیر فهرست وظایف را ایجاد و اصلاح می‌کند و هماهنگی زیرعوامل برای تکمیل وظیفه را برعهده دارد.

برای ارائه عوامل هوش مصنوعی در تولید، MAF ویژگی‌های زیر را نیز شامل شده است:

- **مشاهده‌پذیری** با استفاده از OpenTelemetry که هر اقدام عامل هوش مصنوعی از جمله فراخوانی ابزار، مراحل ارکستراسیون، جریان‌های استدلال و مانیتورینگ عملکرد از طریق داشبوردهای Microsoft Foundry را دنبال می‌کند.
- **امنیت** با میزبانی عوامل به صورت بومی در Microsoft Foundry که شامل کنترل‌های امنیتی مانند دسترسی مبتنی بر نقش، مدیریت داده‌های خصوصی و ایمنی محتوای تعبیه‌شده است.
- **مقاومت** چون رشته‌ها و گردش‌های کاری عامل می‌توانند متوقف، از سر گرفته شده و از خطاها بازیابی شوند که این امکان را برای فرآیندهای طولانی‌تر فراهم می‌کند.
- **کنترل** چون گردش‌های کاری با دخالت انسان پشتیبانی می‌شوند که در آن وظایف نیاز به تأیید انسانی دارند.

چارچوب عامل مایکروسافت همچنین تمرکز بر قابلیت همکاری دارد از طریق:

- **مستقل از ابر بودن** – عوامل می‌توانند در کانتینرها، در محل یا در چند ابر مختلف اجرا شوند.
- **مستقل از ارائه‌دهنده بودن** – عوامل می‌توانند از طریق SDK ترجیحی شما از جمله Azure OpenAI و OpenAI ایجاد شوند.
- **ادغام استانداردهای باز** – عوامل می‌توانند از پروتکل‌هایی مانند Agent-to-Agent (A2A) و Model Context Protocol (MCP) برای کشف و استفاده از عوامل و ابزارهای دیگر بهره ببرند.
- **افزونه‌ها و کانکتورها** – اتصال به خدمات داده و حافظه مانند Microsoft Fabric، SharePoint، Pinecone و Qdrant امکان‌پذیر است.

بیایید ببینیم چگونه این ویژگی‌ها در برخی از مفاهیم اصلی چارچوب عامل مایکروسافت به کار گرفته شده‌اند.

## مفاهیم کلیدی چارچوب عامل مایکروسافت

### عوامل

![Agent Framework](../../../translated_images/fa/agent-components.410a06daf87b4fef.webp)

**ایجاد عوامل**

ایجاد عامل با تعریف سرویس استنتاج (ارائه‌دهنده LLM)، مجموعه‌ای از دستورالعمل‌ها برای پیروی عامل هوش مصنوعی و یک `name` مشخص انجام می‌شود:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

کد بالا از `Azure OpenAI` استفاده می‌کند اما عوامل می‌توانند با استفاده از سرویس‌های متنوعی از جمله `Microsoft Foundry Agent Service` ایجاد شوند:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`، `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

یا عوامل از راه دور با استفاده از پروتکل A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**اجرای عوامل**

عوامل با استفاده از متدهای `.run` یا `.run_stream` اجرا می‌شوند برای پاسخ‌های غیرجاری یا جریانی.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

هر اجرای عامل همچنین می‌تواند گزینه‌هایی برای سفارشی‌سازی پارامترهایی مانند `max_tokens` که عامل استفاده می‌کند، `tools` هایی که عامل قادر به فراخوانی آنها است، و حتی خود `model` استفاده شده برای عامل داشته باشد.

این امر در مواردی که مدل‌ها یا ابزارهای خاصی برای تکمیل وظیفه کاربر لازم است مفید است.

**ابزارها**

ابزارها می‌توانند هم هنگام تعریف عامل:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# هنگام ایجاد مستقیم یک ChatAgent

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

و هم هنگام اجرای عامل:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # ابزار ارائه شده فقط برای این اجرا )
```

تعریف شوند.

**رشته‌های عامل**

رشته‌های عامل برای مدیریت مکالمات چند نوبتی استفاده می‌شوند. رشته‌ها می‌توانند با یکی از دو روش زیر ایجاد شوند:

- استفاده از `get_new_thread()` که امکان ذخیره رشته در طول زمان را فراهم می‌کند
- ایجاد خودکار یک رشته هنگام اجرای عامل که فقط در طول اجرای فعلی باقی می‌ماند.

برای ایجاد یک رشته، کد به این صورت است:

```python
# یک رشته جدید ایجاد کنید.
thread = agent.get_new_thread() # عامل را با رشته اجرا کنید.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

سپس می‌توانید رشته را سریال کرده و برای استفاده بعدی ذخیره کنید:

```python
# یک رشته جدید ایجاد کنید.
thread = agent.get_new_thread() 

# عامل را با رشته اجرا کنید.

response = await agent.run("Hello, how are you?", thread=thread) 

# رشته را برای ذخیره‌سازی رشته‌بندی کنید.

serialized_thread = await thread.serialize() 

# حالت رشته را پس از بارگذاری از ذخیره‌سازی بازیابی کنید.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**میان‌افزار عامل**

عوامل برای تکمیل وظایف کاربر با ابزارها و LLM ها تعامل دارند. در برخی سناریوها، ما می‌خواهیم اجرای بین این تعاملات را اجرا یا رصد کنیم. میان‌افزار عامل به ما این امکان را می‌دهد از طریق:

*میان‌افزار عملکردی*

این میان‌افزار به ما اجازه می‌دهد عمل خاصی بین عامل و یک تابع/ابزاری که فراخوانی می‌کند اجرا شود. مثالی از کاربرد آن زمانی است که می‌خواهید روی تماس تابع لاگ‌برداری انجام دهید.

در کد زیر، `next` تعیین می‌کند که میان‌افزار بعدی یا تابع واقعی باید فراخوانی شود.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # پیش‌پردازش: ثبت لاگ قبل از اجرای تابع
    print(f"[Function] Calling {context.function.name}")

    # ادامه به میان‌افزار بعدی یا اجرای تابع
    await next(context)

    # پس‌پردازش: ثبت لاگ بعد از اجرای تابع
    print(f"[Function] {context.function.name} completed")
```

*میان‌افزار چت*

این میان‌افزار امکان اجرای اقدام یا لاگ‌برداری بین عامل و درخواست‌های بین LLM را فراهم می‌کند.

این شامل اطلاعات مهمی مانند `messages` است که به سرویس هوش مصنوعی ارسال می‌شوند.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # پردازش پیش‌زمینه: ثبت لاگ قبل از فراخوانی هوش مصنوعی
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # ادامه به میان‌افزار بعدی یا سرویس هوش مصنوعی
    await next(context)

    # پردازش پس‌زمینه: ثبت لاگ پس از پاسخ هوش مصنوعی
    print("[Chat] AI response received")

```

**حافظه عامل**

همانطور که در درس `Agentic Memory` پوشش داده شد، حافظه عنصر مهمی برای فعال کردن عامل برای کارکرد در زمینه‌های مختلف است. MAF چند نوع حافظه مختلف ارائه می‌دهد:

*حافظه درون رشته*

این حافظه در طول اجرای برنامه در رشته‌ها ذخیره می‌شود.

```python
# ایجاد یک رشته جدید.
thread = agent.get_new_thread() # اجرای عامل با رشته.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*پیام‌های پایدار*

این حافظه هنگام ذخیره سابقه مکالمه در جلسات مختلف استفاده می‌شود. با استفاده از `chat_message_store_factory` تعریف می‌شود:

```python
from agent_framework import ChatMessageStore

# ایجاد یک فروشگاه پیام سفارشی
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*حافظه پویا*

این حافظه قبل از اجرای عوامل به متن اضافه می‌شود. این حافظه‌ها می‌توانند در خدمات خارجی مانند mem0 ذخیره شوند:

```python
from agent_framework.mem0 import Mem0Provider

# استفاده از Mem0 برای قابلیت‌های پیشرفته حافظه
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

**مشاهده‌پذیری عامل**

مشاهده‌پذیری برای ساخت سیستم‌های عاملی قابل اعتماد و نگهداری‌پذیر مهم است. MAF با OpenTelemetry ادغام شده است تا ردیابی و اندازه‌گیری‌های بهتری برای مشاهده‌پذیری فراهم کند.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # انجام دادن کاری
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### گردش‌های کاری

MAF گردش‌های کاری از پیش تعریف شده‌ای را ارائه می‌دهد که مراحل از پیش تعیین شده برای تکمیل یک وظیفه هستند و عوامل هوش مصنوعی به عنوان اجزا در آن مراحل هستند.

گردش‌های کاری از اجزای مختلفی ساخته شده‌اند که امکان کنترل بهتر جریان را فراهم می‌کند. گردش‌های کاری همچنین **ارکستراسیون چندعاملی** و **ثبت وضعیت** برای ذخیره حالات گردش کار را فعال می‌کنند.

اجزای اصلی یک گردش کار عبارتند از:

**اجراکننده‌ها**

اجراکننده‌ها پیام‌های ورودی را دریافت کرده، وظایف محول شده را انجام می‌دهند و سپس پیام خروجی تولید می‌کنند. این جریان کار را به سمت تکمیل وظیفه بزرگ‌تر پیش می‌برد. اجراکننده‌ها می‌توانند عامل هوش مصنوعی یا منطق سفارشی باشند.

**لبه‌ها**

لبه‌ها برای تعریف جریان پیام‌ها در گردش کار استفاده می‌شوند. این‌ها می‌توانند شامل موارد زیر باشند:

*لبه‌های مستقیم* - اتصالات ساده یک به یک بین اجراکننده‌ها:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*لبه‌های شرطی* - زمانی فعال می‌شوند که شرط خاصی برآورده شود. برای مثال، وقتی اتاق‌های هتل در دسترس نیستند، یک اجراکننده می‌تواند گزینه‌های دیگر پیشنهاد دهد.

*لبه‌های سوئیچ-کیس* - پیام‌ها را بسته به شرایط تعریف شده به اجراکننده‌های مختلف مسیریابی می‌کنند. مثلاً اگر مسافر اولویت دسترسی داشته باشد، وظایف او از طریق یک گردش کار دیگر مدیریت می‌شود.

*لبه‌های پخش* - یک پیام را به چندین هدف ارسال می‌کند.

*لبه‌های جمع‌آوری* - چندین پیام از اجراکننده‌های مختلف جمع‌آوری کرده و به یک هدف ارسال می‌کند.

**رویدادها**

برای ارائه مشاهده‌پذیری بهتر در گردش‌های کاری، MAF رویدادهای داخلی برای اجرا ارائه می‌دهد از جمله:

- `WorkflowStartedEvent`  - شروع اجرای گردش کار
- `WorkflowOutputEvent` - خروجی گردش کار تولید می‌شود
- `WorkflowErrorEvent` - خطایی در گردش کار رخ می‌دهد
- `ExecutorInvokeEvent`  - اجراکننده شروع به پردازش می‌کند
- `ExecutorCompleteEvent`  -  اجراکننده پردازش را تمام می‌کند
- `RequestInfoEvent` - یک درخواست صادر شده است

## مهاجرت از چارچوب‌های دیگر (Semantic Kernel و AutoGen)

### تفاوت‌های بین MAF و Semantic Kernel

**ایجاد ساده‌تر عامل**

Semantic Kernel به ایجاد یک نمونه Kernel برای هر عامل وابسته است. MAF از رویکرد ساده‌تری استفاده می‌کند که با استفاده از افزونه‌ها برای ارائه‌دهندگان اصلی انجام می‌شود.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**ایجاد رشته عامل**

Semantic Kernel نیاز دارد رشته‌ها به صورت دستی ایجاد شوند. در MAF، رشته مستقیماً به عامل تخصیص داده می‌شود.

```python
thread = agent.get_new_thread() # عامل را با نخ اجرا کنید.
```

**ثبت ابزار**

در Semantic Kernel، ابزارها به Kernel ثبت می‌شوند و سپس Kernel به عامل داده می‌شود. در MAF، ابزارها مستقیماً در فرآیند ایجاد عامل ثبت می‌شوند.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### تفاوت‌های بین MAF و AutoGen

**تیم‌ها در مقابل گردش‌های کاری**

`Teams` ساختار رویداد برای فعالیت رویداد محور با عوامل در AutoGen هستند. MAF از `Workflows` استفاده می‌کند که داده‌ها را از طریق معماری گراف به اجراکننده‌ها مسیر می‌دهند.

**ایجاد ابزار**

AutoGen از `FunctionTool` برای پوشش توابعی که عوامل آن را فراخوانی می‌کنند استفاده می‌کند. MAF از @ai_function استفاده می‌کند که مشابه عمل می‌کند اما همچنین اسکیمای توابع را به صورت خودکار استنتاج می‌کند.

**رفتار عامل**

در AutoGen عوامل به طور پیش‌فرض تک نوبتی هستند مگر اینکه `max_tool_iterations` به عدد بالاتری تنظیم شده باشد. در MAF، `ChatAgent` به طور پیش‌فرض چند نوبتی است به این معنی که تا تکمیل وظیفه کاربر به فراخوانی ابزارها ادامه می‌دهد.

## نمونه‌های کد  

نمونه‌های کد برای چارچوب عامل مایکروسافت در این مخزن در فایل‌های `xx-python-agent-framework` و `xx-dotnet-agent-framework` قرار دارند.

## سوالات بیشتری درباره چارچوب عامل مایکروسافت دارید؟

به [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) بپیوندید تا با سایر یادگیرندگان ملاقات کنید، در ساعت‌های اداری شرکت کنید و سوالات خود درباره عوامل هوش مصنوعی را پاسخ بگیرید.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است شامل خطاها یا نواقصی باشند. سند اصلی به زبان بومی خود باید منبع معتبر و اصلی محسوب شود. برای اطلاعات حیاتی، توصیه می‌شود از ترجمه حرفه‌ای توسط انسان استفاده شود. ما مسئول هیچ سوءتفاهم یا تفسیر نادرستی ناشی از استفاده از این ترجمه نیستیم.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->