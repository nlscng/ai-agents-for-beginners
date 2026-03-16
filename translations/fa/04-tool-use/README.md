[![چگونه نمایندگان خوب هوش مصنوعی طراحی کنیم](../../../translated_images/fa/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(برای مشاهده ویدیو این درس روی تصویر بالا کلیک کنید)_

# الگوی طراحی استفاده از ابزار

ابزارها جالب هستند زیرا به نمایندگان هوش مصنوعی امکان می‌دهند دامنه وسیع‌تری از قابلیت‌ها را داشته باشند. به جای اینکه نماینده تنها مجموعه محدودی از عملیات را انجام دهد، با افزودن یک ابزار، نماینده اکنون می‌تواند طیف گسترده‌ای از عملیات را انجام دهد. در این فصل، به الگوی طراحی استفاده از ابزار می‌پردازیم که توضیح می‌دهد چگونه نمایندگان هوش مصنوعی می‌توانند از ابزارهای خاصی برای دستیابی به اهدافشان استفاده کنند.

## معرفی

در این درس، قصد داریم به سوالات زیر پاسخ دهیم:

- الگوی طراحی استفاده از ابزار چیست؟
- در چه مواردی می‌توان از آن استفاده کرد؟
- عناصر / قطعات سازنده مورد نیاز برای پیاده‌سازی الگو چیست؟
- ملاحظات ویژه برای استفاده از الگوی طراحی استفاده از ابزار برای ساخت نمایندگان هوش مصنوعی قابل اعتماد چیست؟

## اهداف یادگیری

پس از پایان این درس، شما قادر خواهید بود:

- الگوی طراحی استفاده از ابزار و هدف آن را تعریف کنید.
- مواقعی را که الگوی طراحی استفاده از ابزار قابل اعمال است، شناسایی کنید.
- عناصر کلیدی مورد نیاز برای پیاده‌سازی الگو را درک کنید.
- ملاحظات مربوط به اطمینان از اعتمادپذیری نمایندگان هوش مصنوعی با استفاده از این الگو را بشناسید.

## الگوی طراحی استفاده از ابزار چیست؟

**الگوی طراحی استفاده از ابزار** بر توانمندسازی مدل‌های زبانی بزرگ (LLMها) برای تعامل با ابزارهای خارجی به منظور دستیابی به اهداف خاص تمرکز دارد. ابزارها کدهایی هستند که یک نماینده می‌تواند آنها را برای انجام عملیات اجرا کند. یک ابزار می‌تواند یک تابع ساده مانند ماشین حساب یا یک درخواست API به یک سرویس شخص ثالث مانند دریافت قیمت سهام یا پیش‌بینی آب و هوا باشد. در زمینه نمایندگان هوش مصنوعی، ابزارها طوری طراحی شده‌اند که توسط نمایندگان در پاسخ به **تماس‌های تابع تولید شده توسط مدل** اجرا شوند.

## موارد استفاده‌ای که می‌توان به آنها اعمال کرد چیست؟

نمایندگان هوش مصنوعی می‌توانند از ابزارها برای انجام وظایف پیچیده، بازیابی اطلاعات یا تصمیم‌گیری استفاده کنند. الگوی طراحی استفاده از ابزار اغلب در سناریوهایی کاربرد دارد که نیاز به تعامل پویا با سیستم‌های خارجی مانند پایگاه‌های داده، سرویس‌های وب یا مفسرهای کد دارند. این توانایی برای موارد مختلفی کاربرد دارد از جمله:

- **بازیابی اطلاعات پویا:** نمایندگان می‌توانند از APIهای خارجی یا پایگاه‌های داده برای به‌دست آوردن داده‌های به‌روز استفاده کنند (مثلاً پرس و جو از یک پایگاه داده SQLite برای تحلیل داده، گرفتن قیمت سهام یا اطلاعات هواشناسی).
- **اجرای کد و تفسیر آن:** نمایندگان می‌توانند کد یا اسکریپت‌ها را برای حل مسائل ریاضی، تولید گزارش‌ها یا انجام شبیه‌سازی‌ها اجرا کنند.
- **اتوماسیون گردش کار:** خودکارسازی گردش کارهای تکراری یا چندمرحله‌ای با ادغام ابزارهایی مانند زمان‌بندهای کار، سرویس‌های ایمیل یا خطوط داده.
- **پشتیبانی مشتری:** نمایندگان می‌توانند با سیستم‌های CRM، پلتفرم‌های تیکت دهی یا پایگاه‌های دانشی برای حل پرسش‌های کاربران تعامل داشته باشند.
- **تولید و ویرایش محتوا:** نمایندگان می‌توانند از ابزارهایی مانند بررسی دستور زبان، خلاصه‌ساز متن یا ارزیاب‌های ایمنی محتوا برای کمک به وظایف تولید محتوا استفاده کنند.

## عناصر / قطعات سازنده لازم برای پیاده‌سازی الگوی طراحی استفاده از ابزار چیست؟

این قطعات سازنده به نماینده هوش مصنوعی اجازه می‌دهند طیف وسیعی از کارها را انجام دهد. بیایید به عناصر کلیدی مورد نیاز برای پیاده‌سازی الگوی طراحی استفاده از ابزار نگاه کنیم:

- **اسکیمای توابع / ابزارها**: تعاریف دقیق ابزارهای در دسترس، شامل نام تابع، هدف، پارامترهای مورد نیاز، و خروجی‌های مورد انتظار. این اسکیم‌ها به LLM کمک می‌کند بفهمد چه ابزارهایی موجود است و چگونه درخواست‌های معتبر بسازد.

- **منطق اجرای تابع**: تعیین‌کننده زمان و چگونگی فراخوانی ابزارها بر اساس قصد کاربر و زمینه گفتگو است. این ممکن است شامل ماژول‌های برنامه‌ریز، مکانیزم‌های مسیریابی یا جریان‌های شرطی باشد که استفاده از ابزار را به‌صورت پویا مشخص می‌کند.

- **سیستم مدیریت پیام**: اجزایی که جریان گفتگویی میان ورودی‌های کاربر، پاسخ‌های LLM، تماس‌های ابزار و خروجی‌های ابزار را مدیریت می‌کنند.

- **چارچوب یکپارچه‌سازی ابزار**: زیرساختی که نماینده را به ابزارهای مختلف متصل می‌کند، چه توابع ساده یا سرویس‌های خارجی پیچیده.

- **مدیریت خطا و اعتبارسنجی**: مکانیزم‌هایی برای مدیریت خطاها در اجرای ابزار، اعتبارسنجی پارامترها و مدیریت پاسخ‌های غیرمنتظره.

- **مدیریت حالت**: ردیابی زمینه گفتگو، تعاملات قبلی با ابزار و داده‌های پایدار برای اطمینان از هماهنگی در تعاملات چند مرحله‌ای.

حال بیایید به جزئیات بیشتر تماس با تابع / ابزار بپردازیم.

### تماس با تابع / ابزار

تماس با تابع روش اصلی است که به مدل‌های زبانی بزرگ (LLMها) امکان تعامل با ابزارها را می‌دهد. اغلب 'تابع' و 'ابزار' به جای هم استفاده می‌شوند زیرا 'توابع' (بلوک‌های کد قابل استفاده مجدد) همان 'ابزارهایی' هستند که نمایندگان برای انجام کارها به کار می‌برند. برای فراخوانی کد یک تابع، یک LLM باید درخواست کاربر را با توصیف توابع مقایسه کند. برای این کار، اسکیمایی که توصیفات همه توابع موجود را دارد به LLM ارسال می‌شود. سپس LLM مناسب‌ترین تابع را برای انجام وظیفه انتخاب کرده و نام و آرگومان‌های آن را برمی‌گرداند. تابع انتخاب شده فراخوانی شده، پاسخ آن به LLM ارسال می‌شود که از این اطلاعات برای پاسخ به درخواست کاربر استفاده می‌کند.

برای توسعه‌دهندگان جهت پیاده‌سازی تماس با تابع برای نمایندگان، به موارد زیر نیاز دارید:

1. یک مدل LLM که از تماس با تابع پشتیبانی کند
2. اسکیمایی که توصیفات توابع را شامل شود
3. کد هر تابع توصیف شده

بیایید مثال گرفتن زمان فعلی یک شهر را برای توضیح استفاده کنیم:

1. **راه‌اندازی یک LLM که تماس با تابع را پشتیبانی کند:**

    همه مدل‌ها تماس با تابع را پشتیبانی نمی‌کنند، پس مهم است مطمئن شوید مدلی که استفاده می‌کنید این قابلیت را دارد. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> تماس با تابع را پشتیبانی می‌کند. می‌توانیم با ایجاد مشتری Azure OpenAI شروع کنیم.

    ```python
    # مقداردهی اولیه مشتری Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **ایجاد اسکیمای تابع**:

    سپس یک اسکیمای JSON تعریف می‌کنیم که حاوی نام تابع، توضیح وظیفه تابع و نام‌ها و توضیحات پارامترهای تابع است.
    این اسکیم را به مشتری ایجاد شده قبلی همراه با درخواست کاربر برای پیدا کردن زمان در سانفرانسیسکو ارسال می‌کنیم. نکته مهم این است که **تماس با ابزار** چیزی است که بازگردانده می‌شود، **نه** پاسخ نهایی به سوال. همانطور که قبلاً گفته شد، LLM نام تابع انتخاب شده برای وظیفه و آرگومان‌هایی که به آن داده می‌شود را بازمی‌گرداند.

    ```python
    # توضیح عملکرد برای مدل جهت خواندن
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
  
    # پیام اولیه کاربر
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # اولین تماس API: درخواست از مدل برای استفاده از تابع
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # پردازش پاسخ مدل
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **کد تابع لازم برای انجام وظیفه:**

    حال که LLM تابع مورد نیاز را انتخاب کرده، کد مربوط به انجام وظیفه باید پیاده‌سازی و اجرا شود.
    می‌توانیم کدی به زبان پایتون برای گرفتن زمان فعلی بنویسیم. همچنین باید کدی برای استخراج نام و آرگومان‌ها از response_message جهت دریافت نتیجه نهایی بنویسیم.

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
     # مدیریت تماس‌های تابع
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
  
      # دومین فراخوانی API: دریافت پاسخ نهایی از مدل
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


تماس با تابع در مرکز اکثر، اگر نه همه، طراحی‌های استفاده از ابزار نمایندگان است، اما پیاده‌سازی آن از ابتدا گاهی چالش‌برانگیز است.
همانطور که در [درس ۲](../../../02-explore-agentic-frameworks) یاد گرفتیم، چارچوب‌های عاملی بلوک‌های سازنده از پیش ساخته شده‌ای برای پیاده‌سازی استفاده از ابزار در اختیار ما قرار می‌دهند.

## مثال‌هایی از استفاده از ابزار با چارچوب‌های عاملی

در اینجا چند مثال از نحوه پیاده‌سازی الگوی طراحی استفاده از ابزار با استفاده از چارچوب‌های عاملی مختلف آمده است:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> یک چارچوب منبع‌باز هوش مصنوعی برای توسعه‌دهندگان .NET، پایتون و جاوا است که با مدل‌های زبانی بزرگ (LLM) کار می‌کنند. این چارچوب فرآیند استفاده از تماس با تابع را ساده می‌کند به طوری که توابع و پارامترهای آنها را به‌طور خودکار از طریق فرآیندی به نام <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">سریال‌سازی</a> به مدل معرفی می‌کند. همچنین ارتباط دوطرفه میان مدل و کد شما را مدیریت می‌کند. یکی دیگر از مزایای استفاده از چارچوب عاملی مانند Semantic Kernel این است که به شما امکان دسترسی به ابزارهای از پیش ساخته شده مانند <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">جستجوی فایل</a> و <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">مفسر کد</a> را می‌دهد.

نمودار زیر فرآیند تماس با تابع در Semantic Kernel را نشان می‌دهد:

![function calling](../../../translated_images/fa/functioncalling-diagram.a84006fc287f6014.webp)

در Semantic Kernel توابع / ابزارها <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">پلاگین</a> نامیده می‌شوند. می‌توانیم تابع `get_current_time` که قبلاً دیدیم را با تبدیل آن به یک کلاس حاوی آن تابع به پلاگین تبدیل کنیم. همچنین می‌توانیم دکوراتور `kernel_function` را وارد کنیم که توضیح تابع را دریافت می‌کند. وقتی یک کرنل با GetCurrentTimePlugin ایجاد کنید، کرنل به‌طور خودکار تابع و پارامترهای آن را سریال‌سازی کرده و اسکیمایی را برای ارسال به LLM می‌سازد.

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

# کرنل را ایجاد کنید
kernel = Kernel()

# پلاگین را ایجاد کنید
get_current_time_plugin = GetCurrentTimePlugin(location)

# پلاگین را به کرنل اضافه کنید
kernel.add_plugin(get_current_time_plugin)
```
  
### سرویس نماینده هوش مصنوعی Azure

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">سرویس نماینده هوش مصنوعی Azure</a> یک چارچوب عاملی جدیدتر است که برای توانمندسازی توسعه‌دهندگان جهت ساخت امن، استقرار و مقیاس‌پذیری نمایندگان هوش مصنوعی با کیفیت بالا و قابل توسعه طراحی شده است بدون نیاز به مدیریت منابع محاسباتی و ذخیره‌سازی زیرساختی. این سرویس برای برنامه‌های سازمانی بسیار مفید است چون کاملاً مدیریت شده و دارای امنیت درجه سازمانی است.

در مقایسه با توسعه مستقیم با API مدل‌های زبانی بزرگ، سرویس نماینده هوش مصنوعی Azure مزایایی از جمله:

- فراخوانی خودکار ابزار — نیازی به تجزیه تماس ابزار، فراخوانی ابزار و مدیریت پاسخ نیست؛ همه اینها به صورت سروری انجام می‌شود
- مدیریت امن داده‌ها — به جای مدیریت وضعیت گفتگو توسط خودتان، می‌توانید به رشته‌ها تکیه کنید تا همه اطلاعات مورد نیاز را ذخیره کنند
- ابزارهای آماده استفاده — ابزارهایی که می‌توانید برای تعامل با منابع داده مانند بینگ، جستجوی Azure AI و Azure Functions استفاده کنید.

ابزارهای موجود در سرویس نماینده Azure می‌توانند به دو دسته تقسیم شوند:

1. ابزارهای دانش:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">زمینه‌سازی با جستجوی Bing</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">جستجوی فایل</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">جستجوی Azure AI</a>

2. ابزارهای عملیاتی:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">تماس با تابع</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">مفسر کد</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">ابزارهای تعریف‌شده با OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">توابع Azure</a>

این سرویس به ما امکان می‌دهد تا این ابزارها را به صورت یک `مجموعه ابزار` با هم استفاده کنیم. همچنین از `رشته‌ها` استفاده می‌کند که تاریخچه پیام‌های یک گفتگوی خاص را ردیابی می‌کنند.

تصور کنید شما یک نماینده فروش در شرکتی به نام Contoso هستید. می‌خواهید یک نماینده مکالمه‌ای بسازید که بتواند به سوالات درباره داده‌های فروش شما پاسخ دهد.

تصویر زیر نشان می‌دهد چگونه می‌توانید از سرویس نماینده هوش مصنوعی Azure برای تحلیل داده‌های فروش استفاده کنید:

![Agentic Service In Action](../../../translated_images/fa/agent-service-in-action.34fb465c9a84659e.webp)

برای استفاده از هر یک از این ابزارها با این سرویس، می‌توانیم یک مشتری ایجاد کرده و یک ابزار یا مجموعه ابزار تعریف کنیم. برای پیاده‌سازی عملی می‌توانیم از کد پایتون زیر استفاده کنیم. مدل LLM می‌تواند مجموعه ابزار را بررسی کرده و تصمیم بگیرد که از تابع ایجاد شده توسط کاربر یعنی `fetch_sales_data_using_sqlite_query` استفاده کند یا مفسر کد پیش ساخته، بسته به درخواست کاربر.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # تابع fetch_sales_data_using_sqlite_query که می‌توان آن را در فایل fetch_sales_data_functions.py یافت.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# مقداردهی اولیه مجموعه ابزار
toolset = ToolSet()

# مقداردهی اولیه ایجنت فراخوانی تابع با تابع fetch_sales_data_using_sqlite_query و افزودن آن به مجموعه ابزار
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# مقداردهی اولیه ابزار مفسر کد و افزودن آن به مجموعه ابزار.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## ملاحظات ویژه برای استفاده از الگوی طراحی استفاده از ابزار جهت ساخت نمایندگان هوش مصنوعی قابل اعتماد چیست؟

یکی از نگرانی‌های رایج درباره SQL تولید شده به صورت پویا توسط LLMها، امنیت است، به خصوص خطر تزریق SQL یا اقدام‌های مخرب مانند حذف یا دستکاری پایگاه داده. در حالی که این نگرانی‌ها منطقی هستند، می‌توان آنها را با تنظیم صحیح مجوزهای دسترسی پایگاه داده به طور مؤثری کاهش داد. برای اکثر پایگاه‌های داده، این شامل پیکربندی پایگاه داده به صورت فقط خواندنی است. برای سرویس‌های پایگاه داده مانند PostgreSQL یا Azure SQL، باید به اپلیکیشن یک نقش فقط‌خواندنی (SELECT) داده شود.

اجرای اپلیکیشن در محیط امن محافظت را بیشتر می‌کند. در سناریوهای سازمانی، داده‌ها معمولاً از سیستم‌های عملیاتی استخراج و به پایگاه داده یا انبار داده فقط خواندنی با اسکیمای کاربر پسند منتقل می‌شوند. این روش اطمینان می‌دهد که داده‌ها ایمن، بهینه شده برای عملکرد و دسترسی، و اپلیکیشن دارای دسترسی محدود فقط خواندنی است.

## کدهای نمونه
- پایتون: [چارچوب عامل](./code_samples/04-python-agent-framework.ipynb)
- دات‌نت: [چارچوب عامل](./code_samples/04-dotnet-agent-framework.md)

## سوالات بیشتری درباره استفاده از الگوهای طراحی ابزار دارید؟

به [دیسکورد Microsoft Foundry](https://aka.ms/ai-agents/discord) بپیوندید تا با دیگر یادگیرندگان ملاقات کنید، در ساعات اداری شرکت کنید و سوالات خود درباره عامل‌های هوش مصنوعی را پاسخ دهید.

## منابع اضافی

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">کارگاه سرویس عامل‌های هوش مصنوعی آژور</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">کارگاه چندعاملی نویسنده خلاق کانتوسو</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">آموزش فراخوانی تابع کرنل معنایی</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">مفسر کد کرنل معنایی</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">ابزارهای Autogen</a>

## درس قبلی

[درک الگوهای طراحی عاملی](../03-agentic-design-patterns/README.md)

## درس بعدی

[آژانس RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**سلب مسئولیت**:  
این سند با استفاده از سرویس ترجمه هوش مصنوعی [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا ناآگاهی‌هایی باشند. سند اصلی به زبان بومی آن باید منبع معتبر در نظر گرفته شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما در برابر هرگونه سوءتفاهم یا تفسیر نادرست ناشی از استفاده از این ترجمه مسئولیتی نداریم.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->