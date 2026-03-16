[![الگوی طراحی برنامه‌ریزی](../../../translated_images/fa/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(برای دیدن ویدئوی این درس روی تصویر بالا کلیک کنید)_

# طراحی برنامه‌ریزی

## مقدمه

این درس شامل موارد زیر است

* تعریف هدف کلی روشن و تقسیم یک وظیفه پیچیده به وظایف قابل مدیریت.
* بهره‌برداری از خروجی ساختارمند برای پاسخ‌های قابل اطمینان‌تر و قابل خواندن توسط ماشین.
* به‌کارگیری رویکردی مبتنی بر رویداد برای مدیریت وظایف داینامیک و ورودی‌های غیرمنتظره.

## اهداف یادگیری

پس از اتمام این درس، شما درباره موارد زیر درک خواهید داشت:

* شناسایی و تعیین هدف کلی برای یک عامل هوش مصنوعی، به گونه‌ای که دقیقاً بداند چه چیزی باید حاصل شود.
* تجزیه یک وظیفه پیچیده به زیر وظایف قابل مدیریت و سازماندهی آن‌ها در یک ترتیب منطقی.
* تجهیز عوامل به ابزارهای مناسب (مثل ابزارهای جستجو یا تحلیل داده)، تصمیم‌گیری درباره زمان و نحوه استفاده از آن‌ها و مدیریت شرایط غیرمنتظره‌ای که پیش می‌آید.
* ارزیابی نتایج زیر وظایف، اندازه‌گیری عملکرد و تکرار روی اقدامات برای بهبود خروجی نهایی.

## تعریف هدف کلی و تقسیم‌بندی یک وظیفه

![تعریف اهداف و وظایف](../../../translated_images/fa/defining-goals-tasks.d70439e19e37c47a.webp)

اکثر وظایف دنیای واقعی برای انجام در یک گام بسیار پیچیده هستند. یک عامل هوش مصنوعی به هدفی مختصر نیاز دارد تا برنامه‌ریزی و اقدام‌های خود را هدایت کند. به عنوان مثال، هدف زیر را در نظر بگیرید:

    "تولید یک برنامه سفر ۳ روزه."

اگرچه بیان این هدف ساده است، اما نیاز به پالایش دارد. هر چه هدف واضح‌تر باشد، عامل (و هر همکار انسانی) بهتر می‌تواند روی رسیدن به نتیجه درست متمرکز شود، مثل ایجاد یک برنامه سفر جامع با گزینه‌های پرواز، پیشنهاد هتل و فعالیت‌ها.

### تقسیم‌بندی وظیفه

وظایف بزرگ یا پیچیده زمانی که به بخش‌های کوچکتر و هدفمند تقسیم شوند قابل مدیریت‌تر خواهند بود.
برای مثال برنامه سفر، می‌توانید هدف را به موارد زیر تقسیم کنید:

* رزرو پرواز
* رزرو هتل
* اجاره خودرو
* شخصی‌سازی

سپس هر زیر وظیفه می‌تواند توسط عوامل یا فرآیندهای اختصاصی پردازش شود. یک عامل ممکن است در جستجوی بهترین پیشنهادات پرواز تخصص داشته باشد، دیگری روی رزرو هتل متمرکز باشد و غیره. یک عامل هماهنگ‌کننده یا «پایین‌دستی» می‌تواند این نتایج را جمع‌آوری و یک برنامه منسجم برای کاربر نهایی ایجاد کند.

این رویکرد مدولار همچنین امکان بهبود تدریجی را فراهم می‌کند. به طور مثال، می‌توانید عوامل تخصصی برای پیشنهاد غذا یا فعالیت‌های محلی اضافه کنید و برنامه سفر را به مرور ارتقا دهید.

### خروجی ساختارمند

مدل‌های زبانی بزرگ (LLMها) قادرند خروجی ساختارمندی (مثل JSON) تولید کنند که برای تحلیل و پردازش توسط عوامل یا سرویس‌های پایین‌دستی راحت‌تر است. این موضوع به‌ویژه در زمینه چندعاملی مفید است، جایی که پس از دریافت خروجی برنامه‌ریزی می‌توانیم این وظایف را اجرا کنیم. برای یک مرور سریع به این <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">بلاگ‌پست</a> مراجعه کنید.

قطعه کد پایتون زیر نمونه‌ای ساده از یک عامل برنامه‌ریز است که هدف را به زیر وظایف تجزیه کرده و یک برنامه ساختارمند تولید می‌کند:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# مدل زیرکار سفر
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # ما می‌خواهیم وظیفه را به نماینده اختصاص دهیم

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # برای احراز هویت با مدل شما باید یک توکن دسترسی شخصی (PAT) در تنظیمات GitHub خود ایجاد کنید.
    # توکن PAT خود را با پیروی از دستورالعمل‌های اینجا ایجاد کنید: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# پیام کاربر را تعریف کنید
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # مطمئن شوید که محتوای پاسخ قبل از بارگذاری رشته JSON معتبری است
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# اگر محتوای پاسخ None بود:
#     یک ValueError با پیام "محتوای پاسخ رشته JSON معتبری نیست" ایجاد کنید

# # چاپ محتوای پاسخ پس از بارگذاری به صورت JSON
# pprint(json.loads(response_content))

# محتوای پاسخ را با مدل MathReasoning اعتبارسنجی کنید
# TravelPlan.model_validate(json.loads(response_content))
```

### عامل برنامه‌ریز با هماهنگی چند عاملی

در این مثال، یک عامل مسیریاب معنایی (Semantic Router Agent) درخواست کاربر را دریافت می‌کند (مثل «من نیاز به برنامه هتل برای سفرم دارم.»).

سپس برنامه‌ریز:

* دریافت برنامه هتل: برنامه‌ریز پیام کاربر را گرفته و بر اساس یک راهنمای سیستمی (شامل جزئیات عوامل موجود)، یک برنامه سفر ساختارمند تولید می‌کند.
* فهرست عوامل و ابزارهای آن‌ها: ثبت‌نام عوامل لیستی از عوامل (مثل پرواز، هتل، اجاره خودرو و فعالیت‌ها) به همراه تابع‌ها یا ابزارهای مورد استفاده‌شان در اختیار دارد.
* مسیریابی برنامه به عوامل مربوطه: بسته به تعداد زیر وظایف، برنامه‌ریز پیام را مستقیماً به یک عامل اختصاصی ارسال می‌کند (در سناریوهای تک‌وظیفه‌ای) یا از طریق مدیر چت گروهی برای همکاری چندعاملی هماهنگ می‌کند.
* خلاصه‌سازی نتیجه: در نهایت، برنامه‌ریز برنامه تولیدشده را برای وضوح خلاصه می‌کند.
قطعه کد زیر این مراحل را نشان می‌دهد:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# مدل زیرکار سفر

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # ما می‌خواهیم این وظیفه را به عامل اختصاص دهیم

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# ایجاد کلاینت با متغیرهای محیطی دارای بررسی نوع

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# تعریف پیام کاربر

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# اطمینان از اینکه محتوای پاسخ یک رشته JSON معتبر است قبل از بارگذاری آن

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# چاپ محتوای پاسخ پس از بارگذاری به صورت JSON

pprint(json.loads(response_content))
```

خروجی زیر نتیجه کد قبلی است و شما سپس می‌توانید از این خروجی ساختارمند برای مسیریابی به `assigned_agent` و خلاصه کردن برنامه سفر برای کاربر نهایی استفاده کنید.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

یک نوت‌بوک نمونه با کد فوق [اینجا](07-autogen.ipynb) در دسترس است.

### برنامه‌ریزی تکراری

برخی وظایف نیازمند بازگشت و برنامه‌ریزی مجدد هستند، جایی که نتیجه یک زیر وظیفه بر بعدی تاثیر می‌گذارد. برای مثال، اگر عامل در حین رزرو پرواز با فرمت داده غیرمنتظره‌ای مواجه شود، ممکن است لازم باشد پیش از ادامه دادن به رزرو هتل، استراتژی خود را تطبیق دهد.

علاوه بر این، بازخورد کاربر (مثل تصمیم یک انسان برای پرواز زودتر) می‌تواند موجب برنامه‌ریزی جزئی دوباره شود. این رویکرد پویا و تکراری تضمین می‌کند که راه‌حل نهایی با محدودیت‌های دنیای واقعی و ترجیحات متغیر کاربر هماهنگ باشد.

مثال کد

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. همانند کد قبلی و ارسال تاریخچه کاربر، طرح فعلی
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. بازبرنامه‌ریزی و ارسال وظایف به نمایندگان مربوطه
```

برای برنامه‌ریزی جامع‌تر به بلاگ‌پست <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Magnetic One</a> مراجعه کنید که برای حل وظایف پیچیده است.

## خلاصه

در این مقاله مثالی از نحوه ایجاد یک برنامه‌ریز که بتواند عوامل موجود را به صورت پویا انتخاب کند، بررسی کردیم. خروجی برنامه‌ریز وظایف را تجزیه کرده و عوامل را برای اجرا تخصیص می‌دهد. فرض بر این است که عوامل به توابع/ابزارهای لازم برای انجام وظایف دسترسی دارند. علاوه بر عوامل، می‌توانید الگوهای دیگری مانند بازتاب، خلاصه‌ساز و چت رو به رو برای سفارشی‌سازی بیشتر اضافه کنید.

## منابع اضافی

AutoGen Magentic One - سیستمی چندعاملی و عمومی برای حل وظایف پیچیده که نتایج قابل توجهی در معیارهای چالش‌برانگیز عامل‌محور کسب کرده است. مرجع: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. در این پیاده‌سازی، هماهنگ‌کننده برنامه‌ای خاص برای هر وظیفه ایجاد کرده و وظایف را به عوامل موجود واگذار می‌کند. علاوه بر برنامه‌ریزی، هماهنگ‌کننده مکانیزمی برای رصد پیشرفت وظیفه دارد و در صورت نیاز برنامه را مجدداً طراحی می‌کند.

### سوالات بیشتری درباره الگوی طراحی برنامه‌ریزی دارید؟

به [دیسکورد Microsoft Foundry](https://aka.ms/ai-agents/discord) بپیوندید تا با دیگر یادگیرندگان ملاقات کنید، در جلسات اداری شرکت کنید و سوالات خود را درباره عوامل هوش مصنوعی مطرح کنید.

## درس قبلی

[ساخت عوامل هوش مصنوعی قابل اعتماد](../06-building-trustworthy-agents/README.md)

## درس بعدی

[الگوی طراحی چندعاملی](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**سلب مسئولیت**:
این سند با استفاده از سرویس ترجمه خودکار [Co-op Translator](https://github.com/Azure/co-op-translator) ترجمه شده است. در حالی که ما برای دقت تلاش می‌کنیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است حاوی خطاها یا نواقصی باشند. سند اصلی به زبان بومی آن باید منبع معتبر تلقی شود. برای اطلاعات حیاتی، ترجمه حرفه‌ای انسانی توصیه می‌شود. ما مسئول هیچ گونه سوءتفاهم یا تفسیر نادرستی که از استفاده این ترجمه ناشی شود، نیستیم.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->