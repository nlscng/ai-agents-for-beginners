[![كيفية تصميم وكلاء ذكاء اصطناعي جيدين](../../../translated_images/ar/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(انقر على الصورة أعلاه لمشاهدة فيديو هذا الدرس)_

# نمط تصميم استخدام الأدوات

الأدوات مثيرة للاهتمام لأنها تتيح لوكلاء الذكاء الاصطناعي امتلاك نطاق أوسع من القدرات. بدلاً من أن يكون لدى الوكيل مجموعة محدودة من الإجراءات التي يمكنه تنفيذها، من خلال إضافة أداة، يمكن للوكيل الآن أداء مجموعة واسعة من الإجراءات. في هذا الفصل، سننظر في نمط تصميم استخدام الأدوات، الذي يصف كيف يمكن لوكلاء الذكاء الاصطناعي استخدام أدوات محددة لتحقيق أهدافهم.

## مقدمة

في هذا الدرس، نسعى للإجابة على الأسئلة التالية:

- ما هو نمط تصميم استخدام الأدوات؟
- ما هي الحالات التي يمكن تطبيقه عليها؟
- ما هي العناصر/الوحدات البنائية اللازمة لتنفيذ نمط التصميم؟
- ما هي الاعتبارات الخاصة باستخدام نمط تصميم استخدام الأدوات لبناء وكلاء ذكاء اصطناعي جديرين بالثقة؟

## أهداف التعلم

بعد إكمال هذا الدرس، ستكون قادرًا على:

- تعريف نمط تصميم استخدام الأدوات وهدفه.
- تحديد الحالات التي يمكن تطبيق نمط تصميم استخدام الأدوات فيها.
- فهم العناصر الرئيسية اللازمة لتنفيذ نمط التصميم.
- التعرف على الاعتبارات لضمان موثوقية وكلاء الذكاء الاصطناعي باستخدام نمط التصميم هذا.

## ما هو نمط تصميم استخدام الأدوات؟

يركز **نمط تصميم استخدام الأدوات** على تمكين نماذج اللغات الكبيرة (LLMs) من التفاعل مع الأدوات الخارجية لتحقيق أهداف محددة. الأدوات هي شيفرة يمكن تنفيذها بواسطة الوكيل لأداء إجراءات. يمكن أن تكون الأداة دالة بسيطة مثل آلة حاسبة، أو استدعاء API لخدمة طرف ثالث مثل الاطلاع على أسعار الأسهم أو توقعات الطقس. في سياق وكلاء الذكاء الاصطناعي، تم تصميم الأدوات ليتم تنفيذها بواسطة الوكلاء استجابةً لـ **استدعاءات الدوال التي يولدها النموذج**.

## ما هي الحالات التي يمكن تطبيقه عليها؟

يمكن لوكلاء الذكاء الاصطناعي الاستفادة من الأدوات لإتمام مهام معقدة، استرجاع المعلومات، أو اتخاذ القرارات. غالبًا ما يُستخدم نمط تصميم استخدام الأدوات في السيناريوهات التي تتطلب تفاعلًا ديناميكيًا مع أنظمة خارجية، مثل قواعد البيانات، خدمات الويب، أو مفسري الأكواد. هذه القدرة مفيدة لعدة حالات مختلفة تشمل:

- **استرجاع المعلومات الديناميكي:** يمكن للوكلاء الاستعلام عن واجهات API الخارجية أو قواعد البيانات لجلب بيانات محدثة (مثل الاستعلام عن قاعدة بيانات SQLite لتحليل البيانات، جلب أسعار الأسهم أو معلومات الطقس).
- **تنفيذ وتفسير الكود:** يمكن للوكلاء تنفيذ الأكواد أو السكريبتات لحل المسائل الرياضية، إنشاء التقارير، أو إجراء المحاكاة.
- **أتمتة سير العمل:** أتمتة الأعمال المتكررة أو متعددة الخطوات عبر دمج أدوات مثل جدولة المهام، خدمات البريد الإلكتروني، أو خطوط البيانات.
- **دعم العملاء:** يمكن للوكلاء التفاعل مع أنظمة إدارة علاقات العملاء، أنظمة التذاكر، أو قواعد المعرفة لحل استفسارات المستخدمين.
- **إنشاء المحتوى وتحريره:** يمكن للوكلاء الاستفادة من أدوات مثل مدققات القواعد النحوية، ملخصات النصوص، أو مقيمي سلامة المحتوى لمساعدة في مهام إنشاء المحتوى.

## ما هي العناصر/الوحدات البنائية اللازمة لتطبيق نمط تصميم استخدام الأدوات؟

تتيح هذه الوحدات البنائية للوكيل أداء مجموعة واسعة من المهام. لننظر في العناصر الرئيسية اللازمة لتطبيق نمط تصميم استخدام الأدوات:

- **مخططات الوظائف/الأدوات**: تعريفات مفصلة للأدوات المتاحة، بما في ذلك اسم الدالة، الغرض منها، المعلمات المطلوبة، والمخرجات المتوقعة. تمكّن هذه المخططات النموذج اللغوي الكبير من فهم الأدوات المتوفرة وكيفية إنشاء طلبات صحيحة.

- **منطق تنفيذ الدوال**: يتحكم في كيفية ووقت استدعاء الأدوات بناءً على نية المستخدم وسياق المحادثة. قد يشمل هذا وحدات تخطيط، آليات توجيه، أو تدفقات شرطية تحدد استخدام الأداة بشكل ديناميكي.

- **نظام معالجة الرسائل**: مكونات تدير تدفق المحادثة بين مدخلات المستخدم، استجابات النموذج اللغوي، استدعاءات الأدوات، ومخرجات الأدوات.

- **إطار تكامل الأدوات**: بنية تحتية تربط الوكيل بمختلف الأدوات، سواء كانت دوال بسيطة أو خدمات خارجية معقدة.

- **معالجة الأخطاء والتحقق**: آليات للتعامل مع فشل تنفيذ الأدوات، التحقق من المعلمات، وإدارة الاستجابات غير المتوقعة.

- **إدارة الحالة**: تتبع سياق المحادثة، التفاعلات السابقة مع الأدوات، والبيانات المستمرة لضمان الاتساق خلال التفاعلات متعددة الأدوار.

بعد ذلك، لننظر في استدعاء الدوال/الأدوات بمزيد من التفصيل.

### استدعاء الدوال/الأدوات

استدعاء الدوال هو الطريقة الأساسية التي نُتيح بها لنماذج اللغات الكبيرة (LLMs) التفاعل مع الأدوات. غالبًا ما ترى "الدالة" و"الأداة" تُستخدمان بالتبادل لأن "الدوال" (كتل شفرة قابلة لإعادة الاستخدام) هي "الأدوات" التي يستخدمها الوكلاء لأداء المهام. لكي يُستدعى كود دالة، يجب على النموذج اللغوي الكبير مقارنة طلب المستخدم مع وصف الدوال. للقيام بذلك، يتم إرسال مخطط يحتوي على أوصاف جميع الدوال المتاحة إلى النموذج. ثم يختار النموذج الدالة الأنسب للمهمة ويعيد اسمها ومعاملاتها. يتم استدعاء الدالة المختارة، ويتم إرسال استجابتها إلى النموذج، الذي يستخدم المعلومات للرد على طلب المستخدم.

لكي ينفذ المطورون استدعاء الدوال للوكلاء، ستحتاج إلى:

1. نموذج LLM يدعم استدعاء الدوال
2. مخطط يحتوي على أوصاف الدوال
3. الشيفرة الخاصة بكل دالة موصوفة

لنستخدم مثال الحصول على الوقت الحالي في مدينة لتوضيح ذلك:

1. **تهيئة نموذج LLM يدعم استدعاء الدوال:**

    ليست كل النماذج تدعم استدعاء الدوال، لذا من المهم التحقق من أن النموذج الذي تستخدمه يفعل ذلك. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> يدعم استدعاء الدوال. يمكننا البدء بإنشاء عميل Azure OpenAI.

    ```python
    # تهيئة عميل Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

2. **إنشاء مخطط دالة**:

    بعد ذلك، سنحدد مخطط JSON يحتوي على اسم الدالة، وصف ما تقوم به، وأسماء ووصف معلمات الدالة.
    بعد ذلك نمرر هذا المخطط إلى العميل الذي أنشأناه سابقًا، مع طلب المستخدم للعثور على الوقت في سان فرانسيسكو. المهم أن نلاحظ أن **استدعاء الأداة** هو ما يُعاد، **وليس** الجواب النهائي على السؤال. كما ذُكر سابقًا، يعيد النموذج اسم الدالة التي اختارها للمهمة والمعاملات التي ستمريرها إليها.

    ```python
    # وصف دالة للنموذج للقراءة
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # رسالة المستخدم الأولية
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # أول طلب API: اطلب من النموذج استخدام الدالة
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # معالجة رد النموذج
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
3. **الكود الخاص بالدالة لتنفيذ المهمة:**

    الآن بعد أن اختار النموذج الدالة التي يجب تشغيلها، يجب تنفيذ الكود الذي يؤدي المهمة.
    يمكننا تنفيذ كود للحصول على الوقت الحالي بلغة Python. سنحتاج أيضًا لكتابة كود لاستخراج الاسم والمعاملات من response_message للحصول على النتيجة النهائية.

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # التعامل مع استدعاءات الدالة
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # استدعاء API الثاني: الحصول على الاستجابة النهائية من النموذج
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

استدعاء الدوال هو جوهر معظم، إن لم يكن كل، تصميم استخدام الأدوات للوكيل، ومع ذلك قد يكون تنفيذه من الصفر تحديًا أحيانًا.
كما تعلمنا في [الدرس 2](../../../02-explore-agentic-frameworks) توفر الأطر الوكيلة لنا وحدات بناء جاهزة لتنفيذ استخدام الأدوات.
 
## أمثلة على استخدام الأدوات مع الأُطُر الوكيلية

إليك بعض الأمثلة على كيفية تنفيذ نمط تصميم استخدام الأدوات باستخدام أطر وكيلية مختلفة:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> هو إطار عمل ذكاء اصطناعي مفتوح المصدر لمطوري .NET وPython وJava العاملين مع نماذج اللغات الكبيرة (LLMs). يُبسط عملية استخدام استدعاء الدوال من خلال وصف دوالك ومعاملاتها للنموذج تلقائيًا عبر عملية تسمى <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">التسلسل</a>. كما يتعامل مع التواصل ذهابًا وإيابًا بين النموذج والشيفرة الخاصة بك. ميزة أخرى لاستخدام إطار وكيل مثل Semantic Kernel هي أنه يسمح لك بالوصول إلى أدوات جاهزة مثل <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">البحث في الملفات</a> و<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">مفسر الكود</a>.

يوضح المخطط التالي عملية استدعاء الدوال مع Semantic Kernel:

![function calling](../../../translated_images/ar/functioncalling-diagram.a84006fc287f6014.webp)

في Semantic Kernel تُسمى الدوال/الأدوات <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">الإضافات</a>. يمكننا تحويل الدالة `get_current_time` التي رأيناها سابقًا إلى إضافة بتحويلها إلى صنف يحتوي على الدالة. يمكننا أيضًا استيراد الزخرفة `kernel_function`، التي تأخذ وصف الدالة. عند إنشاء kernel مع GetCurrentTimePlugin، يقوم kernel تلقائيًا بتسلسل الدالة ومعاملاتها، مما يُنشئ المخطط لإرساله إلى النموذج اللغوي الكبير خلال العملية.

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# إنشاء النواة
kernel = Kernel()

# إنشاء المكون الإضافي
get_current_time_plugin = GetCurrentTimePlugin(location)

# إضافة المكون الإضافي إلى النواة
kernel.add_plugin(get_current_time_plugin)
```
  
### خدمة Azure AI Agent

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">خدمة Azure AI Agent</a> هي إطار وكيل أحدث مصمم لتمكين المطورين من بناء ونشر وتوسيع نطاق وكلاء ذكاء اصطناعي عالي الجودة وقابل للتوسع بأمان دون الحاجة لإدارة موارد الحوسبة والتخزين الأساسية. هي مفيدة بشكل خاص لتطبيقات المؤسسات لأنها خدمة مُدارة بالكامل مع أمان على مستوى مؤسسي.

عند المقارنة بالتطوير مباشرة باستخدام API لنموذج اللغات الكبيرة، توفر خدمة Azure AI Agent بعض المزايا، بما في ذلك:

- استدعاء الأدوات تلقائيًا – لا حاجة لتحليل استدعاء أداة، استدعاء الأداة، والتعامل مع الاستجابة؛ كل ذلك يتم الآن على الخادم
- إدارة البيانات بأمان – بدلاً من إدارة حالة المحادثة الخاصة بك، يمكنك الاعتماد على threads لتخزين كل المعلومات التي تحتاجها
- أدوات جاهزة للاستخدام – أدوات يمكنك استخدامها للتفاعل مع مصادر بياناتك، مثل Bing، Azure AI Search، وAzure Functions.

يمكن تقسيم الأدوات المتاحة في خدمة Azure AI Agent إلى فئتين:

1. أدوات المعرفة:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">التأسيس مع Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">البحث في الملفات</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. أدوات الإجراء:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">استدعاء الدوال</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">مفسر الكود</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">أدوات معرفة بـ OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

تتيح خدمة الوكيل إمكانية استخدام هذه الأدوات معًا كمجموعة أدوات `toolset`. كما تستخدم `threads` التي تتتبع تاريخ الرسائل من محادثة معينة.

تخيل أنك وكيل مبيعات في شركة تدعى Contoso. تريد تطوير وكيل محادثة يمكنه الإجابة على الأسئلة حول بيانات مبيعاتك.

الصورة التالية توضح كيف يمكن استخدام خدمة Azure AI Agent لتحليل بيانات المبيعات الخاصة بك:

![Agentic Service In Action](../../../translated_images/ar/agent-service-in-action.34fb465c9a84659e.webp)

لاستخدام أي من هذه الأدوات مع الخدمة يمكننا إنشاء عميل وتحديد أداة أو مجموعة أدوات. لتنفيذ ذلك عمليًا يمكننا استخدام كود Python التالي. سيتمكن نموذج اللغات الكبير من النظر إلى مجموعة الأدوات وتحديد ما إذا كان سيستخدم الدالة التي أنشأها المستخدم `fetch_sales_data_using_sqlite_query`، أو مفسر الكود المدمج بناءً على طلب المستخدم.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # دالة fetch_sales_data_using_sqlite_query الموجودة في ملف fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# تهيئة مجموعة الأدوات
toolset = ToolSet()

# تهيئة وكيل استدعاء الدالة مع دالة fetch_sales_data_using_sqlite_query وإضافتها إلى مجموعة الأدوات
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# تهيئة أداة مفسر الكود وإضافتها إلى مجموعة الأدوات.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## ما هي الاعتبارات الخاصة باستخدام نمط تصميم استخدام الأدوات لبناء وكلاء ذكاء اصطناعي جديرين بالثقة؟

هناك قلق شائع من استعلامات SQL التي يُنشئها النموذج اللغوي الكبير بشكل ديناميكي يتعلّق بالأمان، خصوصًا خطر حقن SQL أو الإجراءات الخبيثة، مثل حذف أو التلاعب بقاعدة البيانات. في حين أن هذه المخاوف صحيحة، يمكن التخفيف منها بشكل فعّال عن طريق تكوين أذونات الوصول إلى قاعدة البيانات بشكل صحيح. بالنسبة لمعظم قواعد البيانات، يشمل ذلك تكوين قاعدة البيانات على وضع للقراءة فقط. بالنسبة لخدمات قواعد البيانات مثل PostgreSQL أو Azure SQL، يجب تعيين دور قراءة فقط (SELECT) للتطبيق.

تشغيل التطبيق في بيئة آمنة يعزز الحماية كذلك. في سيناريوهات المؤسسات، يتم عادة استخراج البيانات وتحويلها من أنظمة التشغيل إلى قاعدة بيانات قراءة فقط أو مستودع بيانات مع مخطط سهل الاستخدام. يضمن هذا أن تكون البيانات آمنة، ومحسنة للأداء وسهولة الوصول، وأن يكون للتطبيق وصول مقيد للقراءة فقط.

## عينات الأكواد
- Python: [إطار العمل الوكيل](./code_samples/04-python-agent-framework.ipynb)
- .NET: [إطار العمل الوكيل](./code_samples/04-dotnet-agent-framework.md)

## هل لديك المزيد من الأسئلة حول استخدام أنماط التصميم للأدوات؟

انضم إلى [خادم Discord الخاص بـ Microsoft Foundry](https://aka.ms/ai-agents/discord) لتلتقي بمتعلمين آخرين، وتحضر ساعات المكتب، وتحصل على إجابات لأسئلتك حول وكلاء الذكاء الاصطناعي.

## موارد إضافية

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">ورشة عمل خدمة وكلاء Azure AI</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">ورشة عمل كاتب Contoso الإبداعي متعدد الوكلاء</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">دليل استدعاء دوال Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">مفسر الأكواد في Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">أدوات Autogen</a>

## الدرس السابق

[فهم أنماط التصميم الوكيلة](../03-agentic-design-patterns/README.md)

## الدرس التالي

[وكالة RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**إخلاء المسؤولية**:
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى إلى الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الموثوق به. بالنسبة للمعلومات الهامة، يُنصح بالاستعانة بالترجمة البشرية الاحترافية. نحن غير مسؤولين عن أي سوء فهم أو تفسير ناتج عن استخدام هذه الترجمة.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->