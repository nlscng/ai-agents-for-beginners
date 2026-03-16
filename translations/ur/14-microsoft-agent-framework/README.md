# مائیکروسافٹ ایجنٹ فریم ورک کا جائزہ

![ایجنٹ فریم ورک](../../../translated_images/ur/lesson-14-thumbnail.90df0065b9d234ee.webp)

### تعارف

اس سبق میں شامل ہیں:

- مائیکروسافٹ ایجنٹ فریم ورک کو سمجھنا: کلیدی خصوصیات اور اہمیت  
- مائیکروسافٹ ایجنٹ فریم ورک کے کلیدی تصورات کی تلاش
- MAF کا موازنہ Semantic Kernel اور AutoGen سے: ہجرت کا رہنما

## سیکھنے کے اہداف

اس سبق کو مکمل کرنے کے بعد، آپ جانیں گے کہ کیسے:

- مائیکروسافٹ ایجنٹ فریم ورک استعمال کرتے ہوئے پروڈکشن کے لیے تیار AI ایجنٹس بنائیں
- مائیکروسافٹ ایجنٹ فریم ورک کی بنیادی خصوصیات کو اپنے ایجنٹک استعمال کے کیسز پر نافذ کریں
- موجودہ ایجنٹک فریم ورکس اور ٹولز کو مائگریٹ اور انٹیگریٹ کریں  

## کوڈ نمونے 

کوڈ نمونے برائے [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) اس مخزن میں `xx-python-agent-framework` اور `xx-dotnet-agent-framework` فائلوں کے تحت مل سکتے ہیں۔

## مائیکروسافٹ ایجنٹ فریم ورک کو سمجھنا

![فریم ورک کا تعارف](../../../translated_images/ur/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) تجربات اور Semantic Kernel اور AutoGen سے حاصل ہونے والے اسباق کی بنیاد پر بنایا گیا ہے۔ یہ پروڈکشن اور تحقیق کے دونوں ماحول میں دیکھے جانے والے متنوع ایجنٹک استفاده کے کیسز کو حل کرنے کے لیے لچک فراہم کرتا ہے، بشمول:

- **تسلسل میں ایجنٹ آرکسٹریشن** ایسے منظرناموں میں جہاں قدم بہ قدم ورک فلو کی ضرورت ہوتی ہے۔
- **متوازی آرکسٹریشن** ایسے منظرناموں میں جہاں ایجنٹس کو ایک ساتھ کام مکمل کرنے کی ضرورت ہوتی ہے۔
- **گروپ چیٹ آرکسٹریشن** ایسے منظرناموں میں جہاں ایجنٹس ایک کام پر مل کر تعاون کر سکتے ہیں۔
- **ہینڈآف آرکسٹریشن** ایسے منظرناموں میں جہاں ذیلی کام مکمل ہونے پر ایجنٹس آپس میں کام ہینڈ آف کرتے ہیں۔
- **مقناطیسی آرکسٹریشن** ایسے منظرناموں میں جہاں ایک مینیجر ایجنٹ ٹاسک لسٹ بناتا اور تبدیل کرتا ہے اور ذیلی ایجنٹس کی مربوطی کو ہینڈل کرتا ہے تاکہ کام مکمل ہو۔

پروڈکشن میں AI ایجنٹس پہنچانے کے لیے، MAF میں یہ خصوصیات بھی شامل ہیں:

- **قابلِ مشاہدہ** OpenTelemetry کے استعمال کے ذریعے جہاں AI ایجنٹ کا ہر عمل بشمول ٹول کال، آرکسٹریشن کے مراحل، استدلالی بہاؤ اور Microsoft Foundry ڈیش بورڈز کے ذریعے کارکردگی کی نگرانی شامل ہے۔
- **سیکورٹی** Microsoft Foundry پر مقامی طور پر ایجنٹس ہوسٹ کر کے، جو رول بیسڈ ایکسیس، نجی ڈیٹا ہینڈلنگ اور بلٹ-ان مواد کی حفاظت جیسے سیکورٹی کنٹرولز شامل کرتا ہے۔
- **پائیداری** کیونکہ ایجنٹ تھریڈز اور ورک فلو وقفہ کر سکتے ہیں، دوبارہ شروع ہو سکتے ہیں اور غلطیوں سے بحال ہو سکتے ہیں جو طویل دورانیے کے عمل کو ممکن بناتا ہے۔
- **کنٹرول** کیونکہ انسان کے مداخلت والے ورک فلو کی حمایت کی جاتی ہے جہاں کاموں کو انسان کی منظوری درکار کے طور پر نشان زد کیا جاتا ہے۔

مائیکروسافٹ ایجنٹ فریم ورک نے باہمی عمل پذیری (interoperability) پر بھی توجہ دی ہے:

- **کلاؤڈ-نیوٹرل** - ایجنٹس کنٹینرز میں، آن-پرائمز اور مختلف کلاؤڈز میں چل سکتے ہیں۔
- **پرووائیڈر-نیوٹرل** - ایجنٹس آپ کے پسندیدہ SDK کے ذریعے بنائے جا سکتے ہیں بشمول Azure OpenAI اور OpenAI
- **اوپن اسٹینڈرڈز کا انضمام** - ایجنٹس Agent-to-Agent(A2A) اور Model Context Protocol (MCP) جیسے پروٹوکولز استعمال کر کے دوسرے ایجنٹس اور ٹولز کو دریافت اور استعمال کر سکتے ہیں۔
- **پلگ انز اور کنیکٹرز** - کنیکشنز ڈیٹا اور میموری سروسز جیسے Microsoft Fabric، SharePoint، Pinecone اور Qdrant سے بنائے جا سکتے ہیں۔

آئیں دیکھتے ہیں کہ یہ خصوصیات مائیکروسافٹ ایجنٹ فریم ورک کے کچھ بنیادی تصورات پر کیسے لاگو ہوتی ہیں۔

## مائیکروسافٹ ایجنٹ فریم ورک کے کلیدی تصورات

### ایجنٹس

![ایجنٹ فریم ورک](../../../translated_images/ur/agent-components.410a06daf87b4fef.webp)

**ایجنٹس بنانا**

ایجنٹ بنانے کا عمل inference سروس (LLM Provider)، AI ایجنٹ کے لیے پیروی کرنے کے لیے ہدایات کا ایک سیٹ، اور ایک مقررہ `name` بتا کر کیا جاتا ہے:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

اوپر `Azure OpenAI` استعمال کیا گیا ہے لیکن ایجنٹس مختلف خدمات استعمال کرتے ہوئے بنائے جا سکتے ہیں بشمول `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

یا A2A پروٹوکول استعمال کرتے ہوئے ریموٹ ایجنٹس:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**ایجنٹس چلانا**

ایجنٹس کو `.run` یا `.run_stream` میتھڈز استعمال کرتے ہوئے چلایا جاتا ہے، یا تو غیر اسٹریمنگ یا اسٹریمنگ جوابات کے لیے۔

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

ہر ایجنٹ رن میں اختیارات بھی ہو سکتے ہیں تاکہ ایسے پیرامیٹرز کو حسبِ ضرورت بنایا جا سکے جیسے ایجنٹ کے ذریعے استعمال ہونے والا `max_tokens`، وہ `tools` جنہیں ایجنٹ کال کر سکتا ہے، اور حتیٰ کہ خود `model` جو ایجنٹ کے لیے استعمال ہوتا ہے۔

یہ ایسے معاملات میں مفید ہے جہاں کسی صارف کے کام کو مکمل کرنے کے لیے مخصوص ماڈلز یا ٹولز درکار ہوں۔

**ٹولز**

ٹولز کو ایجنٹ کی تعریف کرتے وقت بھی متعین کیا جا سکتا ہے:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# جب براہِ راست ChatAgent بنایا جائے

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

اور ایجنٹ چلانے کے وقت بھی:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # یہ ٹول صرف اس رن کے لیے فراہم کیا گیا ہے )
```

**ایجنٹ تھریڈز**

ایجنٹ تھریڈز کا استعمال ملٹی ٹرن گفتگو کو ہینڈل کرنے کے لیے ہوتا ہے۔ تھریڈز کو یا تو درج ذیل طریقوں سے بنایا جا سکتا ہے:

- `get_new_thread()` استعمال کرنا جو وقت کے ساتھ تھریڈ کو محفوظ کرنے کے قابل بناتا ہے
- ایجنٹ چلانے پر خود بخود ایک تھریڈ بنانا اور صرف موجودہ رن کے دوران ہی تھریڈ کو برقرار رکھنا۔

تھریڈ بنانے کے لیے، کوڈ اس طرح دکھتا ہے:

```python
# ایک نیا تھریڈ بنائیں۔
thread = agent.get_new_thread() # ایجنٹ کو اس تھریڈ کے ساتھ چلائیں۔
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

اس کے بعد آپ تھریڈ کو سیریلائز کر کے بعد میں استعمال کے لیے محفوظ کر سکتے ہیں:

```python
# ایک نیا تھریڈ بنائیں۔
thread = agent.get_new_thread() 

# ایجنٹ کو تھریڈ کے ساتھ چلائیں۔

response = await agent.run("Hello, how are you?", thread=thread) 

# تھریڈ کو ذخیرہ کرنے کے لیے سیریلائز کریں۔

serialized_thread = await thread.serialize() 

# ذخیرہ سے لوڈ کرنے کے بعد تھریڈ کی حالت کو ڈیسیریلائز کریں۔

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**ایجنٹ مڈل ویئر**

ایجنٹس صارف کے کاموں کو مکمل کرنے کے لیے ٹولز اور LLMs کے ساتھ تعامل کرتے ہیں۔ بعض منظرناموں میں، ہم ان تعاملات کے درمیان کچھ عمل انجام دینا یا ٹریک کرنا چاہتے ہیں۔ ایجنٹ مڈل ویئر ہمیں یہ کرنے کے قابل بناتا ہے:

*فنکشن مڈل ویئر*

یہ مڈل ویئر ہمیں ایجنٹ اور اس فنکشن/ٹول کے درمیان کوئی ایکشن انجام دینے کی اجازت دیتا ہے جسے وہ کال کرے گا۔ اس کا استعمال اس وقت کیا جا سکتا ہے جب آپ فنکشن کال پر کچھ لاگنگ کرنا چاہیں۔

In the code below `next` defines if the next middleware or the actual function should be called.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # قبل از عمل: فنکشن کے اجرا سے پہلے لاگ کریں
    print(f"[Function] Calling {context.function.name}")

    # اگلے مڈل ویئر یا فنکشن کے اجرا پر جاری رکھیں
    await next(context)

    # بعد از عمل: فنکشن کے اجرا کے بعد لاگ کریں
    print(f"[Function] {context.function.name} completed")
```

*چیٹ مڈل ویئر*

یہ مڈل ویئر ہمیں ایجنٹ اور LLM کے درمیان درخواستوں کے دوران کوئی ایکشن انجام دینے یا لاگ کرنے کی اجازت دیتا ہے۔

اس میں وہ اہم معلومات شامل ہوتی ہیں جیسے کہ AI سروس کو بھیجے جانے والے `messages`۔

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # پری پروسیسنگ: اے آئی کال سے پہلے لاگ کریں
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # اگلے مڈل ویئر یا اے آئی سروس پر جاری رکھیں
    await next(context)

    # پوسٹ پروسیسنگ: اے آئی کے جواب کے بعد لاگ کریں
    print("[Chat] AI response received")

```

**ایجنٹ میموری**

جیسا کہ `Agentic Memory` سبق میں بیان کیا گیا ہے، میموری ایجنٹ کو مختلف سیاق و سباق میں کام کرنے کے قابل بنانے کا ایک اہم عنصر ہے۔ MAF مختلف قسم کی میموریز فراہم کرتا ہے:

*ان-میموری اسٹوریج*

یہ وہ میموری ہے جو ایپلیکیشن رن ٹائم کے دوران تھریڈز میں محفوظ ہوتی ہے۔

```python
# ایک نئی تھریڈ بنائیں۔
thread = agent.get_new_thread() # ایجنٹ کو تھریڈ کے ساتھ چلائیں۔
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*مستقل پیغامات*

اس میموری کو مختلف سیشنز میں گفتگو کی تاریخ ذخیرہ کرنے کے لیے استعمال کیا جاتا ہے۔ اسے `chat_message_store_factory` کے ذریعے متعین کیا جاتا ہے:

```python
from agent_framework import ChatMessageStore

# ایک حسبِ ضرورت پیغام اسٹور بنائیں
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*ڈائنامک میموری*

یہ میموری ایجنٹس چلائے جانے سے پہلے کانٹیکسٹ میں شامل کی جاتی ہے۔ یہ میموریز بیرونی سروسز جیسے mem0 میں محفوظ کی جا سکتی ہیں:

```python
from agent_framework.mem0 import Mem0Provider

# Mem0 کا استعمال اعلیٰ میموری صلاحیتوں کے لیے
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

**ایجنٹ مشاہدہ (Observability)**

مشاہدہ معتبر اور قابلِ دیکھ بھال ایجنٹک سسٹمز بنانے کے لیے اہم ہے۔ MAF بہتر مشاہدے کے لیے tracing اور meters فراہم کرنے کے لیے OpenTelemetry کے ساتھ انٹیگریٹ کرتا ہے۔

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # کچھ کرو
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### ورک فلو

MAF ایسے ورک فلو پیش کرتا ہے جو کسی کام کو مکمل کرنے کے لیے پیشگی متعین کیے گئے مراحل ہوتے ہیں اور ان مراحل میں AI ایجنٹس کو اجزاء کے طور پر شامل کرتا ہے۔

ورک فلو مختلف اجزاء پر مشتمل ہوتے ہیں جو بہتر کنٹرول فلو کی اجازت دیتے ہیں۔ ورک فلو **ملٹی-ایجنٹ آرکسٹریشن** اور **چیک پوائنٹنگ** کو بھی فعال کرتے ہیں تاکہ ورک فلو کے اسٹیٹس کو محفوظ کیا جا سکے۔

ورک فلو کے بنیادی اجزاء یہ ہیں:

**ایگزیکیوٹرز**

ایگزیکیوٹرز ان پٹ پیغامات وصول کرتے ہیں، اپنی تفویض شدہ ذمہ داریاں انجام دیتے ہیں، اور پھر ایک آؤٹ پٹ پیغام پیدا کرتے ہیں۔ یہ ورک فلو کو بڑے کام کی تکمیل کی طرف آگے بڑھاتا ہے۔ ایگزیکیوٹرز یا تو AI ایجنٹس ہو سکتے ہیں یا کسٹم لاجک۔

**ایجز**

ایجز ورک فلو میں پیغامات کے بہاؤ کی تعریف کے لیے استعمال ہوتے ہیں۔ یہ ہو سکتے ہیں:

*ڈائریکٹ ایجز* - ایگزیکیوٹرز کے درمیان سادہ ایک سے ایک کنکشنز:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*کنڈیشنل ایجز* - جب مخصوص شرط پوری ہو تو فعال ہوتے ہیں۔ مثال کے طور پر، جب ہوٹل کے کمرے دستیاب نہ ہوں تو ایک ایگزیکیوٹر دوسرے اختیارات تجویز کر سکتا ہے۔

*سوئچ-کیس ایجز* - پیغامات کو متعین کردہ شرائط کی بنیاد پر مختلف ایگزیکیوٹرز کی طرف روانہ کرتے ہیں۔ مثال کے طور پر، اگر سفر کا صارف پرائیوریٹی ایکسس رکھتا ہو تو ان کے کام کسی اور ورک فلو کے ذریعے سنبھالے جائیں گے۔

*فین-آؤٹ ایجز* - ایک پیغام کو متعدد ہدفوں پر بھیجیں۔

*فین-ان ایجز* - مختلف ایگزیکیوٹرز سے متعدد پیغامات اکٹھا کریں اور ایک ہدف کو بھیجیں۔

**ایونٹس**

ورک فلو میں بہتر مشاہدہ فراہم کرنے کے لیے، MAF عملدرآمد کے لیے بلٹ-ان ایونٹس پیش کرتا ہے جن میں شامل ہیں:

- `WorkflowStartedEvent`  - ورک فلو کی تنفیذ شروع ہوتی ہے
- `WorkflowOutputEvent` - ورک فلو ایک آؤٹ پٹ پیدا کرتا ہے
- `WorkflowErrorEvent` - ورک فلو کو ایک خرابی درپیش ہوتی ہے
- `ExecutorInvokeEvent`  - ایگزیکیوٹر پروسیسنگ شروع کرتا ہے
- `ExecutorCompleteEvent`  -  ایگزیکیوٹر پروسیسنگ مکمل کرتا ہے
- `RequestInfoEvent` - ایک درخواست جاری کی جاتی ہے

## دیگر فریم ورکس سے مائیگریشن (Semantic Kernel اور AutoGen)

### MAF اور Semantic Kernel کے درمیان فرق

**سادہ ایجنٹ تخلیق**

Semantic Kernel ہر ایجنٹ کے لیے Kernel کی ایک مثال بنانے پر منحصر ہے۔ MAF بنیادی فراہم کنندگان کے لیے ایکسٹینشنز استعمال کر کے ایک سادہ طریقہ کار اختیار کرتا ہے۔

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**ایجنٹ تھریڈ بنانا**

Semantic Kernel میں تھریڈز کو دستی طور پر بنانا ضروری ہوتا ہے۔ MAF میں، ایجنٹ کو براہِ راست ایک تھریڈ تفویض کیا جاتا ہے۔

```python
thread = agent.get_new_thread() # ایجنٹ کو تھریڈ کے ساتھ چلائیں۔
```

**ٹول رجسٹریشن**

Semantic Kernel میں، ٹولز کو Kernel میں رجسٹر کیا جاتا ہے اور پھر Kernel کو ایجنٹ کو پاس کیا جاتا ہے۔ MAF میں، ٹولز براہِ راست ایجنٹ کی تخلیق کے عمل کے دوران رجسٹر کیے جاتے ہیں۔

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF اور  AutoGen کے درمیان فرق

**ٹیمز بمقابلہ ورک فلو**

`Teams` AutoGen میں ایجنٹس کے ساتھ ایونٹ ڈریون سرگرمی کے لیے ایونٹ سٹرکچر ہیں۔ MAF `Workflows` استعمال کرتا ہے جو گراف بیسڈ آرکیٹیکچر کے ذریعے ڈیٹا کو ایگزیکیوٹرز تک پہنچاتا ہے۔

**ٹول تخلیق**

AutoGen ایجنٹس کے کال کرنے کے لیے فنکشنز کو لپیٹنے کے لیے `FunctionTool` استعمال کرتا ہے۔ MAF @ai_function استعمال کرتا ہے جو اسی طرح کام کرتا ہے لیکن ہر فنکشن کے لیے اسکیموں کا خود بخود اندازہ بھی لگا لیتا ہے۔

**ایجنٹ برتاؤ**

AutoGen میں ایجنٹس بطورِ ڈیفالٹ سنگل-ٹرن ایجنٹس ہوتے ہیں جب تک کہ `max_tool_iterations` کو زیادہ سیٹ نہ کیا جائے۔ MAF کے اندر `ChatAgent` بطورِ ڈیفالٹ ملٹی-ٹرن ہوتا ہے جس کا مطلب ہے کہ یہ صارف کے کام مکمل ہونے تک ٹولز کو بار بار کال کرتا رہے گا۔

## کوڈ نمونے 

Microsoft Agent Framework کے کوڈ نمونے اس مخزن میں `xx-python-agent-framework` اور `xx-dotnet-agent-framework` فائلوں کے تحت مل سکتے ہیں۔

## کیا آپ کے پاس مائیکروسافٹ ایجنٹ فریم ورک کے بارے میں مزید سوالات ہیں؟

دیگر سیکھنے والوں سے ملنے، آفس آورز میں شرکت کرنے اور اپنے AI ایجنٹس کے سوالات کے جواب حاصل کرنے کے لیے [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) میں شامل ہوں۔

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
ذمہ داری سے دستبرداری:
یہ دستاویز AI ترجمہ سروس [Co-op Translator](https://github.com/Azure/co-op-translator) کے ذریعے ترجمہ کی گئی ہے۔ اگرچہ ہم درستگی کے لیے کوشاں ہیں، براہِ کرم نوٹ کریں کہ خودکار ترجموں میں غلطیاں یا غیر درستیاں شامل ہو سکتی ہیں۔ اصل دستاویز کو اس کی مادری زبان میں ہی مستند ماخذ سمجھا جانا چاہیے۔ اہم معلومات کے لیے پیشہ ورانہ انسانی ترجمہ کی سفارش کی جاتی ہے۔ اس ترجمے کے استعمال کی وجہ سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تعبیر کی ذمہ داری ہم پر عائد نہیں ہوتی۔
<!-- CO-OP TRANSLATOR DISCLAIMER END -->