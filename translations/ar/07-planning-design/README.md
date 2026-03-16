[![نمط تصميم التخطيط](../../../translated_images/ar/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(انقر على الصورة أعلاه لعرض فيديو هذا الدرس)_

# تصميم التخطيط

## مقدمة

سيغطي هذا الدرس

* تحديد هدف واضح شامل وتقسيم مهمة معقدة إلى مهام يمكن التحكم فيها.
* الاستفادة من المخرجات المهيكلة للحصول على ردود أكثر موثوقية وقابلة للقراءة آليًا.
* تطبيق نهج مدفوع بالأحداث للتعامل مع المهام الديناميكية والمدخلات غير المتوقعة.

## أهداف التعلم

بعد إتمام هذا الدرس، سيكون لديك فهم حول:

* تحديد وتعيين هدف شامل لوكيل الذكاء الاصطناعي، مع ضمان معرفته الواضحة بما يجب تحقيقه.
* تفكيك مهمة معقدة إلى مهام فرعية يمكن التحكم فيها وتنظيمها في تسلسل منطقي.
* تزويد الوكلاء بالأدوات المناسبة (مثل أدوات البحث أو أدوات تحليل البيانات)، تحديد متى وكيف يتم استخدامها، والتعامل مع الحالات غير المتوقعة التي تنشأ.
* تقييم نتائج المهام الفرعية، قياس الأداء، والتكرار على الإجراءات لتحسين المخرجات النهائية.

## تحديد الهدف الشامل وتقسيم المهمة

![تحديد الأهداف والمهام](../../../translated_images/ar/defining-goals-tasks.d70439e19e37c47a.webp)

معظم المهام الواقعية معقدة جدًا للتعامل معها في خطوة واحدة. يحتاج وكيل الذكاء الاصطناعي إلى هدف مختصر لتوجيه تخطيطه وأفعاله. على سبيل المثال، اعتبر الهدف:

    "إنشاء خطة سفر لمدة 3 أيام."

على الرغم من سهولة صياغته، فإنه لا يزال بحاجة إلى تنقيح. كلما كان الهدف أوضح، كان بوسع الوكيل (وأي متعاونين بشريين) التركيز بشكل أفضل على تحقيق النتيجة الصحيحة، مثل إنشاء خطة شاملة تحتوي على خيارات الطيران، توصيات الفنادق، واقتراحات الأنشطة.

### تفكيك المهمة

تصبح المهام الكبيرة أو المعقدة أكثر قابلية للإدارة عند تقسيمها إلى مهام فرعية موجهة نحو هدف.
في مثال خطة السفر، يمكنك تفكيك الهدف إلى:

* حجز الطيران
* حجز الفندق
* تأجير السيارة
* التخصيص

يمكن بعد ذلك التعامل مع كل مهمة فرعية بواسطة وكلاء أو عمليات مخصصة. قد يتخصص وكيل واحد في البحث عن أفضل عروض الطيران، وآخر يركز على حجوزات الفنادق، وهكذا. يمكن لوكيل منسق أو "التالي في السلسلة" جمع هذه النتائج في خط سير متماسك للمستخدم النهائي.

يسمح هذا النهج الوحدوي أيضًا بإجراء تحسينات تدريجية. على سبيل المثال، يمكنك إضافة وكلاء متخصصين في التوصيات الغذائية أو اقتراحات الأنشطة المحلية وتنقيح خطة السفر مع مرور الوقت.

### المخرجات المهيكلة

يمكن لنماذج اللغة الكبيرة (LLMs) توليد مخرجات مهيكلة (مثل JSON) يسهل على الوكلاء أو الخدمات التالية تحليلها ومعالجتها. هذا مفيد بشكل خاص في سياق تعدد الوكلاء، حيث يمكننا تنفيذ هذه المهام بعد استلام مخطط التخطيط. راجع هذا <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">المدونة</a> لمحة سريعة.

المقتطف البرمجي التالي بلغة بايثون يوضح وكيل تخطيط بسيط يقوم بتفكيك هدف إلى مهام فرعية ويُولد خطة مهيكلة:

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

# نموذج مهمة فرعية للسفر
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # نريد تعيين المهمة للوكيل

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # للمصادقة مع النموذج ستحتاج إلى إنشاء رمز وصول شخصي (PAT) في إعدادات GitHub الخاصة بك.
    # أنشئ رمز PAT الخاص بك باتباع التعليمات هنا: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# تحديد رسالة المستخدم
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

# # تأكد من أن محتوى الاستجابة هو سلسلة JSON صالحة قبل تحميلها
# response_content: Optional[str] = response.content إذا كان النوع هو (
#     response.content، str) وإلا يكون None
# إذا كان response_content هو None:
#     ارفع خطأ ValueError("محتوى الرد ليس سلسلة JSON صالحة")

# # اطبع محتوى الرد بعد تحميله كـ JSON
# pprint(json.loads(response_content))

# تحقق من صحة محتوى الرد باستخدام نموذج MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### وكيل التخطيط مع تنظيم متعدد الوكلاء

في هذا المثال، يتلقى وكيل الموجه الدلالي طلب المستخدم (مثل "أحتاج خطة فندق لرحلتي.").

ثم يقوم المخطط بـ:

* استلام خطة الفندق: يأخذ المخطط رسالة المستخدم وبناءً على موجه النظام (بما في ذلك تفاصيل الوكلاء المتاحة)، يُولد خطة سفر مهيكلة.
* سرد الوكلاء وأدواتهم: يحتفظ سجل الوكلاء بقائمة من الوكلاء (مثل الطيران، الفندق، تأجير السيارات، والأنشطة) إلى جانب الوظائف أو الأدوات التي يقدمونها.
* توجيه الخطة إلى الوكلاء المعنيين: بناءً على عدد المهام الفرعية، يرسل المخطط الرسالة مباشرة إلى وكيل مخصص (للسيناريوهات ذات المهمة الواحدة) أو ينسق عبر مدير محادثة جماعية لتعاون متعدد الوكلاء.
* تلخيص النتيجة: أخيرًا، يلخص المخطط الخطة المولدة للوضوح.
العينة البرمجية التالية بلغة بايثون توضح هذه الخطوات:

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

# نموذج مهمة فرعية للسفر

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # نريد تعيين المهمة للوكلاء

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# إنشاء العميل باستخدام متغيرات بيئية تم التحقق من نوعها

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# تحديد رسالة المستخدم

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

# تأكد من أن محتوى الاستجابة هو سلسلة JSON صالحة قبل تحميلها

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# طباعة محتوى الاستجابة بعد تحميلها كـ JSON

pprint(json.loads(response_content))
```

ما يلي هو ناتج الشيفرة السابقة ويمكنك بعد ذلك استخدام هذه المخرجات المهيكلة لتوجه إلى `assigned_agent` وتلخيص خطة السفر للمستخدم النهائي.

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

دفتر ملاحظات تجريبي مع عينة الشيفرة السابقة متوفرة [هنا](07-autogen.ipynb).

### التخطيط التكراري

بعض المهام تتطلب ذهابًا وإيابًا أو إعادة تخطيط، حيث تؤثر نتائج مهمة فرعية على التالية. على سبيل المثال، إذا اكتشف الوكيل تنسيق بيانات غير متوقع أثناء حجز الرحلات، فقد يحتاج لتعديل استراتيجيته قبل الانتقال إلى حجز الفنادق.

بالإضافة إلى ذلك، يمكن أن تؤدي ملاحظات المستخدم (مثل قرار بشري يفضّل رحلة أبكر) إلى إعادة تخطيط جزئية. يضمن هذا النهج الديناميكي والتكراري أن الحل النهائي يتماشى مع القيود الواقعية وتفضيلات المستخدم المتطورة.

كمثال على الشفرة

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. نفس الكود السابق وتمرير تاريخ المستخدم والخطة الحالية
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
# .. إعادة التخطيط وإرسال المهام إلى الوكلاء المعنيين
```

للتخطيط الأكثر شمولاً اطلع على Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">مدونة</a> لحل المهام المعقدة.

## الخلاصة

في هذا المقال نظرنا إلى مثال على كيفية إنشاء مخطط يمكنه اختيار الوكلاء المتاحين المحددين بشكل ديناميكي. مخرجات المخطط تفكك المهام وتخصص الوكلاء ليتم تنفيذها. من المفترض أن الوكلاء لديهم الوصول إلى الوظائف/الأدوات المطلوبة لأداء المهمة. بالإضافة إلى الوكلاء يمكنك تضمين أنماط أخرى مثل الانعكاس، المُلخص، ودردشة التناوب لمزيد من التخصيص.

## موارد إضافية

AutoGen Magnetic One - نظام متعدد الوكلاء عام لحل المهام المعقدة وقد حقق نتائج مثيرة للإعجاب على عدة معايير وكيل تحدي. المرجع: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. في هذا التنفيذ يقوم المنسق بإنشاء خطة تمكينية خاصة بالمهمة ويفوض هذه المهام إلى الوكلاء المتاحين. بالإضافة إلى التخطيط يستخدم المنسق أيضًا آلية تتبع لرصد تقدم المهمة وإعادة التخطيط حسب الحاجة.

### هل لديك المزيد من الأسئلة حول نمط تصميم التخطيط؟

انضم إلى [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) للقاء المتعلمين الآخرين، وحضور ساعات المكتب والحصول على إجابات لاستفساراتك عن وكلاء الذكاء الاصطناعي.

## الدرس السابق

[بناء وكلاء ذكاء اصطناعي جديرين بالثقة](../06-building-trustworthy-agents/README.md)

## الدرس التالي

[نمط تصميم متعدد الوكلاء](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**إخلاء المسؤولية**:
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية [Co-op Translator](https://github.com/Azure/co-op-translator). بينما نسعى لتحقيق الدقة، يرجى العلم أن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر الرسمي والمعتمد. للمعلومات الحساسة أو الحرجة، يُنصح بالترجمة الاحترافية البشرية. نحن غير مسؤولين عن أي سوء فهم أو تفسير خاطئ ناتج عن استخدام هذه الترجمة.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->