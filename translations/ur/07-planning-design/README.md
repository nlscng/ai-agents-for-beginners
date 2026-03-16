[![منصوبہ بندی ڈیزائن پیٹرن](../../../translated_images/ur/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(ویڈیو دیکھنے کے لیے اوپر موجود تصویر پر کلک کریں)_

# منصوبہ بندی ڈیزائن

## تعارف

یہ سبق درج ذیل موضوعات کا احاطہ کرے گا:

* ایک واضح مجموعی مقصد کی تعریف اور پیچیدہ کام کو قابلِ انتظام حصّوں میں تقسیم کرنا۔
* مزید قابلِ اعتماد اور مشین-قابلِ مطالعہ جوابات کے لیے ساختہ آؤٹ پٹ کا استعمال۔
* ڈائنامک کاموں اور غیر متوقع ان پٹس کو سنبھالنے کے لیے ایونٹ پر مبنی طریقہ کار کا اطلاق۔

## سیکھنے کے اہداف

اس سبق کو مکمل کرنے کے بعد، آپ درج ذیل باتوں کا ادراک حاصل کریں گے:

* AI ایجنٹ کے لیے ایک مجموعی مقصد کی شناخت اور تعین کریں، تاکہ اسے واضح طور پر معلوم ہو کہ کیا حاصل کرنا ہے۔
* پیچیدہ کام کو قابلِ انتظام ذیلی کاموں میں تقسیم کریں اور انہیں منطقی ترتیب میں منظم کریں۔
* ایجنٹس کو مناسب ٹولز (مثلاً تلاش کے ٹولز یا ڈیٹا اینالیٹکس ٹولز) سے لیس کریں، فیصلہ کریں کہ کب اور کیسے استعمال کیے جائیں، اور پیدا ہونے والی غیر متوقع صورتحال کو سنبھالیں۔
* ذیلی کام کے نتائج کا جائزہ لیں، کارکردگی کی پیمائش کریں، اور حتمی نتیجہ بہتر بنانے کے لیے کارروائیوں میں تکرار کریں۔

## مجموعی مقصد کی تعریف اور کام کو تقسیم کرنا

![مقاصد اور کاموں کی تعریف](../../../translated_images/ur/defining-goals-tasks.d70439e19e37c47a.webp)

زیادہ تر حقیقی دنیا کے کام ایک قدم میں حل کرنے کے لیے بہت پیچیدہ ہوتے ہیں۔ ایک AI ایجنٹ کو اپنی منصوبہ بندی اور اقدامات کی رہنمائی کے لیے ایک مختصر مقصد درکار ہوتا ہے۔ مثال کے طور پر، اس مقصد پر غور کریں:

    "3 دن کا سفرنامہ تیار کریں۔"

اگرچہ اسے بیان کرنا آسان ہے، پھر بھی اسے مزید وضاحت کی ضرورت ہے۔ جتنا واضح مقصد ہوگا، اتنے ہی بہتر طور پر ایجنٹ (اور کوئی بھی انسانی معاونین) درست نتیجہ حاصل کرنے پر توجہ مرکوز کر سکتے ہیں، مثال کے طور پر ایک جامع سفرنامہ تیار کرنا جس میں پرواز کے اختیارات، ہوٹل کی تجاویز، اور سرگرمیوں کی سفارشات شامل ہوں۔

### ذیلی کاموں کی تقسیم

بڑے یا پیچیدہ کام چھوٹے، مقصد-مرکوز ذیلی کاموں میں تقسیم ہونے پر زیادہ قابلِ انتظام بن جاتے ہیں۔
سفرنامے کی مثال کے لیے، آپ مقصد کو درج ذیل ذیلی کاموں میں تقسیم کر سکتے ہیں:

* پرواز کی بکنگ
* ہوٹل کی بکنگ
* کار کرایہ پر لینا
* شخصی ترتیب

ہر ذیلی کام کو پھر مخصوص ایجنٹس یا عمل کے ذریعے نمٹایا جا سکتا ہے۔ ایک ایجنٹ بہترین پرواز ڈیلز تلاش کرنے میں مہارت رکھ سکتا ہے، دوسرا ہوٹل کی بکنگ پر توجہ مرکوز کر سکتا ہے، وغیرہ۔ ایک ہم آہنگ کرنے والا یا "ڈاؤن اسٹریم" ایجنٹ پھر ان نتائج کو ایک مربوط سفرنامے میں مرتب کر کے آخری صارف کو پیش کر سکتا ہے۔

یہ ماڈیولر طریقہ کار بتدریج بہتری کی اجازت بھی دیتا ہے۔ مثال کے طور پر، آپ خوراک کی تجاویز یا مقامی سرگرمیوں کی تجاویز کے لیے مخصوص ایجنٹس شامل کر سکتے ہیں اور وقت کے ساتھ سفرنامے کو بہتر بنا سکتے ہیں۔

### ساختہ آؤٹ پٹ

بڑے لینگویج ماڈلز (LLMs) ساختہ آؤٹ پٹ (مثلاً JSON) تیار کر سکتے ہیں جو ڈاؤن اسٹریم ایجنٹس یا سروسز کے لیے پارس اور پروسیس کرنا آسان بناتا ہے۔ یہ خاص طور پر کثیر-ایجنٹ سیاق و سباق میں مفید ہے، جہاں ہم منصوبہ بندی کے آؤٹ پٹ موصول ہونے کے بعد ان کاموں پر عملدرآمد کر سکتے ہیں۔ ایک مختصر جائزے کے لیے اس <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">بلاگ پوسٹ</a> کا حوالہ لیں۔

درج ذیل Python کوڈ کا ٹکڑا ایک سادہ پلاننگ ایجنٹ دکھاتا ہے جو ایک مقصد کو ذیلی کاموں میں تقسیم کرتا ہے اور ایک ساختہ منصوبہ تیار کرتا ہے:

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

# سفر کے ذیلی کام کا ماڈل
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # ہم یہ کام ایجنٹ کو تفویض کرنا چاہتے ہیں

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # ماڈل کے ساتھ توثیق کرنے کے لیے آپ کو اپنی GitHub سیٹنگز میں ایک ذاتی رسائی ٹوکن (PAT) تیار کرنا ہوگا۔
    # اپنا PAT ٹوکن بنانے کے لیے یہاں دی گئی ہدایات پر عمل کریں: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# صارف کا پیغام متعین کریں
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

# # لوڈ کرنے سے پہلے اس بات کو یقینی بنائیں کہ جواب کا مواد ایک درست JSON سٹرنگ ہے
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Response content is not a valid JSON string")

# # JSON کے طور پر لوڈ کرنے کے بعد جواب کے مواد کو پرنٹ کریں
# pprint(json.loads(response_content))

# جواب کے مواد کو MathReasoning ماڈل کے ساتھ تصدیق کریں
# TravelPlan.model_validate(json.loads(response_content))
```

### ملٹی-ایجنٹ آرکسٹریشن کے ساتھ پلاننگ ایجنٹ

اس مثال میں، ایک سیمانٹک روٹر ایجنٹ صارف کی درخواست وصول کرتا ہے (مثلاً، "مجھے اپنی سفر کے لیے ہوٹل پلان چاہیے۔").

پلانر پھر:

* ہوٹل پلان وصول کرتا ہے: پلانر صارف کا پیغام لیتا ہے اور ایک سسٹم پرامپٹ کی بنیاد پر (جس میں دستیاب ایجنٹس کی تفصیلات شامل ہیں) ایک ساختہ سفری منصوبہ تیار کرتا ہے۔
* ایجنٹس اور ان کے ٹولز کی فہرست بناتا ہے: ایجنٹ رجسٹری میں ایجنٹس کی فہرست ہوتی ہے (مثلاً پرواز، ہوٹل، کار کرایہ، اور سرگرمیوں کے لیے) اور وہ کون سے فنکشنز یا ٹولز فراہم کرتے ہیں۔
* منصوبہ متعلقہ ایجنٹس تک بھیجتا ہے: ذیلی کاموں کی تعداد کے مطابق، پلانر پیغام کو یا تو براہِ راست ایک مخصوص ایجنٹ کو بھیجتا ہے (ایک ہی کام کے منظرنامے کے لیے) یا کثیر-ایجنٹ تعاون کے لیے گروپ چیٹ مینیجر کے ذریعے ہم آہنگی کرتا ہے۔
* نتیجہ کا خلاصہ کرتا ہے: آخر میں، پلانر وضاحت کے لیے تیار کردہ منصوبے کا خلاصہ کرتا ہے۔
درج ذیل Python کوڈ نمونہ ان مراحل کی عکاسی کرتا ہے:

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

# سفر کا ذیلی کام ماڈل

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # ہم چاہتے ہیں کہ یہ کام ایجنٹ کو تفویض کیا جائے

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# ٹائپ چیک کیے گئے ماحولیاتی متغیرات کے ساتھ کلائنٹ بنائیں

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# صارف کا پیغام متعین کریں

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

# لوڈ کرنے سے پہلے جواب کے مواد کو ایک درست JSON سٹرنگ ہونا یقینی بنائیں

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# JSON کے طور پر لوڈ کرنے کے بعد جواب کے مواد کو پرنٹ کریں

pprint(json.loads(response_content))
```

جو کچھ ذیل میں ہے وہ پچھلے کوڈ کا آؤٹ پٹ ہے اور آپ اس ساختہ آؤٹ پٹ کو `assigned_agent` کی جانب بھیجنے اور اختتامی صارف کے لیے سفرنامہ کا خلاصہ تیار کرنے کے لیے استعمال کر سکتے ہیں۔

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

پچھلے کوڈ نمونے کے ساتھ ایک مثال نوٹ بک [یہاں](07-autogen.ipynb) دستیاب ہے۔

### تکراری منصوبہ بندی

کچھ کاموں کے لیے باہمی رد و بدل یا دوبارہ منصوبہ بندی کی ضرورت ہوتی ہے، جہاں ایک ذیلی کام کا نتیجہ اگلے کو متاثر کرتا ہے۔ مثال کے طور پر، اگر ایجنٹ پروازیں بک کرتے ہوئے کوئی غیر متوقع ڈیٹا فارمیٹ دریافت کرتا ہے، تو ہوٹل بکنگ پر جانے سے پہلے اسے اپنی حکمتِ عملی میں تبدیلی کرنے کی ضرورت پڑ سکتی ہے۔

مزید برآں، صارف کی رائے (مثلاً کوئی انسان یہ فیصلہ کرے کہ وہ جلدی والی پرواز کو ترجیح دیتے ہیں) جزوی دوبارہ منصوبہ بندی کو متحرک کر سکتی ہے۔ یہ متحرک، تکراری طریقہ کار یقینی بناتا ہے کہ حتمی حل حقیقی دنیا کی حدود اور ارتقائی صارف ترجیحات کے مطابق ہو۔

مثلاً نمونہ کوڈ

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. پچھلے کوڈ کی طرح ہی اور صارف کی تاریخ، موجودہ منصوبہ آگے بھیجیں
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
# .. دوبارہ منصوبہ بندی کریں اور کام متعلقہ ایجنٹس کو بھیجیں
```

مزید جامع منصوبہ بندی کے لیے پیچیدہ کام حل کرنے کے لیے Magentic One کی <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">بلاگ پوسٹ</a> دیکھیں۔

## خلاصہ

اس مضمون میں ہم نے ایک ایسے پلانر کی مثال دیکھی ہے جو متعین شدہ دستیاب ایجنٹس کو متحرک طور پر منتخب کر سکتا ہے۔ پلانر کا آؤٹ پٹ کاموں کو تقسیم کرتا ہے اور ایجنٹس کو اسائن کرتا ہے تاکہ وہ عملدرآمد کیے جا سکیں۔ یہ فرض کیا جاتا ہے کہ ایجنٹس کو وہ فنکشنز/ٹولز دستیاب ہیں جو کام انجام دینے کے لیے درکار ہیں۔ ایجنٹس کے علاوہ آپ مزید تخصیص کے لیے عکاسی، خلاصہ ساز، اور راؤنڈ رابن چیٹ جیسے دیگر پیٹرنز بھی شامل کر سکتے ہیں۔

## اضافی وسائل

AutoGen Magentic One - ایک جنرلِسٹ ملٹی-ایجنٹ سسٹم جو پیچیدہ کام حل کرنے کے لیے ہے اور متعدد چیلنجنگ ایجنٹک بینچ مارکس پر متاثر کن نتائج حاصل کر چکا ہے۔ حوالہ: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. اس امپلیمنٹیشن میں آرکسٹریٹر مخصوص کام کا منصوبہ بناتا ہے اور ان کاموں کو دستیاب ایجنٹس کو تفویض کرتا ہے۔ منصوبہ بندی کے علاوہ آرکسٹریٹر ایک ٹریکنگ میکانزم بھی استعمال کرتا ہے تاکہ کام کی پیش رفت کی نگرانی کی جا سکے اور ضرورت پڑنے پر دوبارہ منصوبہ بندی کی جا سکے۔

### پلاننگ ڈیزائن پیٹرن کے بارے میں مزید سوالات؟

دیگر سیکھنے والوں سے ملنے، آفس آورز میں شرکت کرنے اور اپنے AI ایجنٹس کے سوالات کے جوابات حاصل کرنے کے لیے [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) میں شامل ہوں۔

## پچھلا سبق

[قابلِ اعتماد AI ایجنٹس بنانا](../06-building-trustworthy-agents/README.md)

## اگلا سبق

[کثیر-ایجنٹ ڈیزائن پیٹرن](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
دستبرداری:
یہ دستاویز AI ترجمہ سروس Co-op Translator (https://github.com/Azure/co-op-translator) کے ذریعے ترجمہ کی گئی ہے۔ اگرچہ ہم درستگی کے لیے کوشاں ہیں، براہِ کرم نوٹ کریں کہ خودکار تراجم میں غلطیاں یا عدم مطابقت ہو سکتی ہے۔ اصل دستاویز اپنی مادری زبان میں مستند ماخذ سمجھی جائے گی۔ اہم معلومات کے لیے پیشہ ورانہ انسانی ترجمہ کی سفارش کی جاتی ہے۔ ہم اس ترجمے کے استعمال سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تعبیر کے لیے ذمہ دار نہیں ہیں۔
<!-- CO-OP TRANSLATOR DISCLAIMER END -->