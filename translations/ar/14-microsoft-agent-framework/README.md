# استكشاف إطار عمل مايكروسوفت للوكيل

![Agent Framework](../../../translated_images/ar/lesson-14-thumbnail.90df0065b9d234ee.webp)

### المقدمة

ستغطي هذه الدرس:

- فهم إطار عمل مايكروسوفت للوكيل: الميزات الرئيسية والقيمة  
- استكشاف المفاهيم الرئيسية لإطار عمل مايكروسوفت للوكيل
- مقارنة MAF مع Semantic Kernel و AutoGen: دليل الهجرة

## أهداف التعلم

بعد إكمال هذا الدرس، ستعرف كيف:

- بناء وكلاء ذكاء اصطناعي جاهزين للإنتاج باستخدام إطار عمل مايكروسوفت للوكيل
- تطبيق الميزات الأساسية لإطار عمل مايكروسوفت للوكيل على حالات الاستخدام المتعلقة بالوكلاء
- الهجرة والتكامل مع أطر وأدوات الوكلاء الحالية  

## عينات البرمجة 

يمكن العثور على عينات البرمجة لـ [إطار عمل مايكروسوفت للوكيل (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) في هذا المستودع تحت ملفي `xx-python-agent-framework` و`xx-dotnet-agent-framework`.

## فهم إطار عمل مايكروسوفت للوكيل

![Framework Intro](../../../translated_images/ar/framework-intro.077af16617cf130c.webp)

[إطار عمل مايكروسوفت للوكيل (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) يبني على خبرات وتعلميات من Semantic Kernel وAutoGen. يوفر المرونة للتعامل مع مجموعة متنوعة من حالات الاستخدام المتعلقة بالوكلاء التي تُرى في بيئات الإنتاج والبحثية بما في ذلك:

- **تنسيق الوكيل التسلسلي** في السيناريوهات التي تتطلب سير عمل خطوة بخطوة.
- **التنسيق المتزامن** في السيناريوهات التي تحتاج فيها الوكلاء إلى إكمال المهام في نفس الوقت.
- **تنسيق محادثة المجموعة** في السيناريوهات التي يمكن فيها للوكلاء التعاون معًا على مهمة واحدة.
- **تنسيق تسليم المهام** في السيناريوهات التي يقوم فيها الوكلاء بتسليم المهام لبعضهم البعض مع إكمال المهام الفرعية.
- **التنسيق المغناطيسي** في السيناريوهات التي يقوم فيها وكيل المدير بإنشاء وتعديل قائمة المهام والتعامل مع تنسيق الوكلاء الفرعيين لإكمال المهمة.

لتقديم وكلاء الذكاء الاصطناعي في الإنتاج، يتضمن MAF أيضًا ميزات لـ:

- **الرصد** من خلال استخدام OpenTelemetry حيث يتم تتبع كل إجراء لوكيل الذكاء الاصطناعي بما في ذلك استدعاء الأدوات، خطوات التنسيق، تدفقات الاستدلال، ورصد الأداء عبر لوحات تحكم Microsoft Foundry.
- **الأمان** باستضافة الوكلاء أصليًا على Microsoft Foundry والتي تشمل ضوابط أمنية مثل الوصول المعتمد على الأدوار، التعامل مع البيانات الخاصة، والسلامة المضمنة للمحتوى.
- **التحمل** حيث يمكن لخطوط الوكلاء وسير العمل التوقف مؤقتًا، الاستئناف، والتعافي من الأخطاء مما يتيح عمل طويل الأمد.
- **التحكم** حيث يتم دعم سير العمل مع تدخل بشري حيث تُعلَم المهام بأنها تتطلب موافقة بشرية.

يركز إطار عمل مايكروسوفت للوكيل أيضًا على قابلية التشغيل البيني من خلال:

- **عدم التوغل في السحابة** - يمكن تشغيل الوكلاء في الحاويات، في المقر، وعبر عدة سحابات مختلفة.
- **عدم التوغل في المزود** - يمكن إنشاء الوكلاء من خلال SDK المفضل لديك بما في ذلك Azure OpenAI وOpenAI
- **تكامل المعايير المفتوحة** - يمكن للوكلاء استخدام بروتوكولات مثل Agent-to-Agent (A2A) وModel Context Protocol (MCP) لاكتشاف واستخدام وكلاء وأدوات أخرى.
- **الإضافات والموصلات** - يمكن إجراء الاتصالات مع خدمات البيانات والذاكرة مثل Microsoft Fabric, SharePoint, Pinecone وQdrant.

لننظر إلى كيف تُطبّق هذه الميزات على بعض المفاهيم الأساسية لإطار عمل مايكروسوفت للوكيل.

## المفاهيم الرئيسية لإطار عمل مايكروسوفت للوكيل

### الوكلاء

![Agent Framework](../../../translated_images/ar/agent-components.410a06daf87b4fef.webp)

**إنشاء الوكلاء**

يتم إنشاء الوكيل من خلال تعريف خدمة الاستدلال (مزود LLM)، مجموعة من التعليمات التي يتبعها وكيل الذكاء الاصطناعي، و`اسم` معين:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

المثال أعلاه يستخدم `Azure OpenAI` ولكن يمكن إنشاء الوكلاء باستخدام مجموعة متنوعة من الخدمات بما في ذلك `Microsoft Foundry Agent Service`:

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

أو وكلاء عن بعد باستخدام بروتوكول A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**تشغيل الوكلاء**

يتم تشغيل الوكلاء باستخدام طرق `.run` أو `.run_stream` للحصول على استجابات غير متدفقة أو متدفقة.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

يمكن أيضًا لكل تشغيل لوكيل أن يحتوي على خيارات لتخصيص معلمات مثل `max_tokens` المستخدمة من قبل الوكيل، `tools` التي يمكن للوكيل استدعاؤها، وحتى `model` نفسه المستخدم للوكيل.

وهذا مفيد في الحالات التي تتطلب نماذج أو أدوات محددة لإكمال مهمة المستخدم.

**الأدوات**

يمكن تعريف الأدوات عند إنشاء الوكيل:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# عند إنشاء وكيل الدردشة مباشرةً

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

وأيضًا عند تشغيل الوكيل:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # الأداة مقدمة لهذه الجولة فقط )
```

**خيوط الوكيل**

تُستخدم خيوط الوكيل للتعامل مع المحادثات متعددة الأدوار. يمكن إنشاء الخيوط إما عن طريق:

- استخدام `get_new_thread()` والتي تتيح حفظ الخيط بمرور الوقت
- إنشاء خيط تلقائيًا عند تشغيل الوكيل ويستمر الخيط فقط أثناء التشغيل الحالي.

لإنشاء خيط، يبدو الكود هكذا:

```python
# إنشاء مؤشر ترابط جديد.
thread = agent.get_new_thread() # تشغيل الوكيل مع مؤشر الترابط.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

يمكنك بعد ذلك تسلسل الخيط ليتم تخزينه لاستخدام لاحق:

```python
# إنشاء مؤشر ترابط جديد.
thread = agent.get_new_thread() 

# تشغيل الوكيل مع مؤشر الترابط.

response = await agent.run("Hello, how are you?", thread=thread) 

# تسلسل مؤشر الترابط للتخزين.

serialized_thread = await thread.serialize() 

# فك تسلسل حالة مؤشر الترابط بعد التحميل من التخزين.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**وسيط الوكيل**

يتفاعل الوكلاء مع الأدوات وLLMs لإكمال مهام المستخدم. في بعض السيناريوهات، نريد تنفيذ أو تتبع إجراءات بين هذه التفاعلات. يتيح لنا وسيط الوكيل القيام بذلك من خلال:

*وسيط الدالة*

يتيح هذا الوسيط لنا تنفيذ إجراء بين الوكيل والدالة/الأداة التي سيستدعيها. مثال عن استخدامه هو عندما تريد تسجيل استدعاء الدالة.

في الكود أدناه، `next` يحدد ما إذا كان ينبغي استدعاء الوسيط التالي أو الدالة الفعلية.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # المعالجة المسبقة: تسجيل قبل تنفيذ الدالة
    print(f"[Function] Calling {context.function.name}")

    # الاستمرار إلى الوسيط التالي أو تنفيذ الدالة
    await next(context)

    # المعالجة اللاحقة: تسجيل بعد تنفيذ الدالة
    print(f"[Function] {context.function.name} completed")
```

*وسيط الدردشة*

يتيح هذا الوسيط لنا تنفيذ أو تسجيل إجراء بين الوكيل والطلبات بين LLM.

يحتوي هذا على معلومات مهمة مثل `الرسائل` التي تُرسل إلى خدمة الذكاء الاصطناعي.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # المعالجة المسبقة: تسجيل قبل استدعاء الذكاء الاصطناعي
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # الاستمرار إلى الوسيط التالي أو خدمة الذكاء الاصطناعي
    await next(context)

    # المعالجة اللاحقة: تسجيل بعد استجابة الذكاء الاصطناعي
    print("[Chat] AI response received")

```

**ذاكرة الوكيل**

كما تم تغطيته في درس `Agentic Memory`، تعد الذاكرة عنصرًا مهمًا لتمكين الوكيل من العمل عبر سياقات مختلفة. يوفر MAF عدة أنواع مختلفة من الذاكرات:

*التخزين في الذاكرة*

هذه هي الذاكرة المخزنة داخل الخيوط أثناء تشغيل التطبيق.

```python
# إنشاء مؤشر ترابط جديد.
thread = agent.get_new_thread() # تشغيل الوكيل مع مؤشر الترابط.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*الرسائل الدائمة*

تستخدم هذه الذاكرة لتخزين تاريخ المحادثة عبر جلسات مختلفة. يتم تعريفها باستخدام `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# إنشاء مخزن رسائل مخصص
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*الذاكرة الديناميكية*

تُضاف هذه الذاكرة إلى السياق قبل تشغيل الوكلاء. يمكن تخزين هذه الذكريات في خدمات خارجية مثل mem0:

```python
from agent_framework.mem0 import Mem0Provider

# استخدام Mem0 لقدرات الذاكرة المتقدمة
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

**رصد الوكيل**

يعد الرصد مهمًا لبناء أنظمة وكيل موثوقة وقابلة للصيانة. يتكامل MAF مع OpenTelemetry لتوفير التتبع والعدادات لرصد أفضل.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # افعل شيئًا
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### سير العمل

يقدم MAF سير عمل تتكون من خطوات محددة مسبقًا لإكمال مهمة ويشمل وكلاء الذكاء الاصطناعي كعناصر في تلك الخطوات.

يتكون سير العمل من مكونات مختلفة تسمح بتحكم أفضل في التدفق. كما تمكّن سير العمل من **تنسيق متعدد الوكلاء** و**نقاط التحقق** لحفظ حالات سير العمل.

المكونات الأساسية لسير العمل هي:

**المنفذون**

يتلقون رسائل الإدخال، يؤدون مهامهم المعينة، ثم ينتجون رسالة إخراج. هذا يدفع سير العمل نحو إكمال المهمة الكبيرة. يمكن أن يكون المنفذون وكلاء ذكاء اصطناعي أو منطق مخصص.

**الحواف**

تُستخدم لتحديد تدفق الرسائل في سير العمل. يمكن أن تكون:

*الحواف المباشرة* - اتصالات بسيطة واحد إلى واحد بين المنفذين:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*الحواف الشرطية* - تُفعل بعد تحقق شرط معين. على سبيل المثال، عندما تكون غرف الفنادق غير متوفرة، يمكن للمنفذ اقتراح خيارات أخرى.

*حواف التبديل-الحالة* - توجه الرسائل إلى منفذين مختلفين بناءً على شروط معرفة. مثلًا، إذا كان لدى عميل السفر وصول أولوية فستتم معالجة مهامه عبر سير عمل آخر.

*حواف التوزيع* - ترسل رسالة واحدة إلى عدة أهداف.

*حواف الدمج* - تجمع عدة رسائل من منفذين مختلفين وترسل إلى هدف واحد.

**الأحداث**

لتوفير رصد أفضل لسير العمل، يقدم MAF أحداثًا مدمجة للتنفيذ تشمل:

- `WorkflowStartedEvent`  - بدأ تنفيذ سير العمل
- `WorkflowOutputEvent` - أخرج سير العمل مخرجات
- `WorkflowErrorEvent` - واجه سير العمل خطأ
- `ExecutorInvokeEvent`  - بدأ المنفذ المعالجة
- `ExecutorCompleteEvent`  - أنهى المنفذ المعالجة
- `RequestInfoEvent` - تم إصدار طلب

## الهجرة من أطر عمل أخرى (Semantic Kernel و AutoGen)

### الفروق بين MAF و Semantic Kernel

**إنشاء الوكلاء المبسط**

يعتمد Semantic Kernel على إنشاء مثيل Kernel لكل وكيل. يستخدم MAF نهجًا مبسطًا باستخدام الامتدادات للمزودين الرئيسيين.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**إنشاء خيوط الوكيل**

يتطلب Semantic Kernel إنشاء الخيوط يدويًا. في MAF، يتم تعيين الخيط مباشرة للوكيل.

```python
thread = agent.get_new_thread() # تشغيل الوكيل مع الخيط.
```

**تسجيل الأدوات**

في Semantic Kernel، تُسجل الأدوات في Kernel ثم يُمرر Kernel إلى الوكيل. في MAF، تُسجل الأدوات مباشرة أثناء إنشاء الوكيل.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### الفروق بين MAF و AutoGen

**الفرق بين Teams و Workflows**

`Teams` هي الهيكل الحدثي للنشاط المُدار بالأحداث مع الوكلاء في AutoGen. يستخدم MAF `Workflows` التي توجه البيانات إلى المنفذين عبر بنية قائمة على الرسم البياني.

**إنشاء الأدوات**

يستخدم AutoGen `FunctionTool` لتغليف الدوال لاستدعاءات الوكلاء. يستخدم MAF @ai_function التي تعمل بشكل مشابه ولكنها تستنتج المخططات تلقائيًا لكل دالة.

**سلوك الوكيل**

الوكلاء في AutoGen هم من نوع الدور الواحد بشكل افتراضي ما لم يتم تعيين `max_tool_iterations` لعدد أعلى. داخل MAF، يكون `ChatAgent` متعدد الأدوار بشكل افتراضي مما يعني أنه سيستمر في استدعاء الأدوات حتى تكتمل مهمة المستخدم.

## عينات البرمجة 

يمكن العثور على عينات البرمجة لإطار عمل مايكروسوفت للوكيل في هذا المستودع تحت ملفي `xx-python-agent-framework` و`xx-dotnet-agent-framework`.

## هل لديك المزيد من الأسئلة حول إطار عمل مايكروسوفت للوكيل؟

انضم إلى [مايكروسوفت فاوندري ديسكورد](https://aka.ms/ai-agents/discord) للقاء المتعلمين الآخرين، وحضور ساعات العمل، والحصول على إجابات لأسئلتك حول وكلاء الذكاء الاصطناعي.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**إخلاء مسؤولية**:
تم ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية هو المصدر المعتمد. للمعلومات الهامة، يُنصح باستخدام الترجمة البشرية المهنية. نحن غير مسؤولين عن أي سوء فهم أو تفسير خاطئ ينشأ عن استخدام هذه الترجمة.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->