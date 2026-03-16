[![Planning Design Pattern](../../../translated_images/hi/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(इस पाठ का वीडियो देखने के लिए ऊपर की छवि पर क्लिक करें)_

# योजना डिजाइन

## प्रस्तावना

इस पाठ में निम्नलिखित विषय कवर होंगे

* एक स्पष्ट समग्र लक्ष्य को परिभाषित करना और एक जटिल कार्य को प्रबंधनीय कार्यों में तोड़ना।
* अधिक विश्वासनीय और मशीन-पठनीय प्रतिक्रियाओं के लिए संरचित आउटपुट का लाभ उठाना।
* गतिशील कार्यों और अप्रत्याशित इनपुट को संभालने के लिए एक इवेंट-ड्रिवन दृष्टिकोण लागू करना।

## सीखने के लक्ष्य

इस पाठ को पूरा करने के बाद, आपके पास निम्न बिंदुओं की समझ होगी:

* एक एआई एजेंट के लिए एक समग्र लक्ष्य की पहचान और सेट करना, यह सुनिश्चित करना कि उसे स्पष्ट रूप से पता हो कि क्या प्राप्त करना है।
* एक जटिल कार्य को प्रबंधनीय उपकार्य में विभाजित करना और उन्हें तर्कसंगत क्रम में व्यवस्थित करना।
* एजेंट्स को सही उपकरणों (जैसे, खोज उपकरण या डेटा एनालिटिक्स उपकरण) के साथ सज्जित करना, तय करना कि उन्हें कब और कैसे उपयोग किया जाए, और उत्पन्न अप्रत्याशित परिस्थितियों को संभालना।
* उपकार्य के परिणामों का मूल्यांकन करना, प्रदर्शन मापना, और अंतिम आउटपुट को सुधारने के लिए कार्रवाइयों पर पुनरावृत्ति करना।

## समग्र लक्ष्य को परिभाषित करना और एक कार्य को तोड़ना

![Defining Goals and Tasks](../../../translated_images/hi/defining-goals-tasks.d70439e19e37c47a.webp)

अधिकांश वास्तविक जीवन के कार्य इतने जटिल होते हैं कि उन्हें एक ही चरण में पूरा करना मुश्किल होता है। एक एआई एजेंट को अपनी योजना और क्रियाओं का मार्गदर्शन करने के लिए एक संक्षिप्त उद्देश्य की आवश्यकता होती है। उदाहरण के लिए, लक्ष्य पर विचार करें:

    "3-दिन की यात्रा कार्यक्रम तैयार करें।"

हालांकि इसे व्यक्त करना सरल है, लेकिन इसे अभी भी सुधारने की जरूरत है। जितना स्पष्ट लक्ष्य होगा, एजेंट (और कोई भी मानव सहयोगी) उतना ही बेहतर फोकस कर सकते हैं सही परिणाम प्राप्त करने पर, जैसे एक व्यापक यात्रा कार्यक्रम तैयार करना जिसमें उड़ान विकल्प, होटल सिफारिशें, और गतिविधि सुझाव शामिल हों।

### कार्य विभाजन

बड़े या जटिल कार्य छोटे, लक्ष्य-केंद्रित उपकार्य में विभाजित होने पर अधिक प्रबंधनीय हो जाते हैं।
यात्रा कार्यक्रम के उदाहरण के लिए, आप लक्ष्य को इस प्रकार विभाजित कर सकते हैं:

* उड़ान बुकिंग
* होटल बुकिंग
* कार किराया
* व्यक्तिगतकरण

प्रत्येक उपकार्य को समर्पित एजेंट या प्रक्रियाओं द्वारा संभाला जा सकता है। एक एजेंट सर्वश्रेष्ठ उड़ान सौदों की खोज में विशेषज्ञ हो सकता है, एक अन्य होटल बुकिंग पर ध्यान केंद्रित करता है, और इसी तरह। एक समन्वयक या "डाउनस्ट्रीम" एजेंट फिर इन परिणामों को एक संगठित यात्रा कार्यक्रम में अंतिम उपयोगकर्ता के लिए संकलित कर सकता है।

यह मॉड्यूलर दृष्टिकोण क्रमिक सुधारों की भी अनुमति देता है। उदाहरण के लिए, आप भोजन सिफारिशों या स्थानीय गतिविधि सुझावों के लिए विशेष एजेंट जोड़ सकते हैं और समय के साथ यात्रा कार्यक्रम को परिष्कृत कर सकते हैं।

### संरचित आउटपुट

लार्ज लैंग्वेज मॉडल्स (LLMs) संरचित आउटपुट (जैसे JSON) उत्पन्न कर सकते हैं जिन्हें डाउनस्ट्रीम एजेंट या सेवाएं आसानी से पार्स और प्रोसेस कर सकती हैं। यह विशेष रूप से मल्टी-एजेंट संदर्भ में उपयोगी है, जहाँ योजना आउटपुट प्राप्त होने के बाद हम इन कार्यों को लागू कर सकते हैं। त्वरित अवलोकन के लिए इस <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">ब्लॉगपोस्ट</a> का संदर्भ लें।

निम्न Python स्निपेट एक सरल योजना एजेंट को दिखाता है जो लक्ष्य को उपकार्य में विभाजित करता है और एक संरचित योजना उत्पन्न करता है:

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

# ट्रैवल सबटास्क मॉडल
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # हम एजेंट को टास्क असाइन करना चाहते हैं

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # मॉडल के साथ प्रमाणीकरण करने के लिए आपको अपनी GitHub सेटिंग्स में एक व्यक्तिगत एक्सेस टोकन (PAT) जनरेट करना होगा।
    # यहां दिए गए निर्देशों का पालन करके अपना PAT टोकन बनाएं: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# यूज़र संदेश परिभाषित करें
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

# # लोड करने से पहले सुनिश्चित करें कि प्रतिक्रिया सामग्री एक वैध JSON स्ट्रिंग है
# response_content: Optional[str] = response.content अगर यह isinstance(
#     response.content, str) है तो वरना None
# अगर response_content None है:
#     ValueError उठाएं ("प्रतिक्रिया सामग्री एक वैध JSON स्ट्रिंग नहीं है")

# # JSON के रूप में लोड करने के बाद प्रतिक्रिया सामग्री प्रिंट करें
# pprint(json.loads(response_content))

# MathReasoning मॉडल के साथ प्रतिक्रिया सामग्री सत्यापित करें
# TravelPlan.model_validate(json.loads(response_content))
```

### मल्टी-एजेंट ऑर्केस्ट्रेशन के साथ योजना एजेंट

इस उदाहरण में, एक सेमांटिक राउटर एजेंट उपयोगकर्ता से अनुरोध प्राप्त करता है (जैसे, "मुझे मेरी यात्रा के लिए होटल योजना चाहिए।")।

फिर योजनाकार निम्न करता है:

* होटल योजना प्राप्त करता है: योजनाकार उपयोगकर्ता के संदेश को लेकर, एक सिस्टम प्रॉम्प्ट (जिसमें उपलब्ध एजेंट विवरण शामिल हैं) के आधार पर, एक संरचित यात्रा योजना उत्पन्न करता है।
* एजेंटों और उनके उपकरणों की सूची बनाता है: एजेंट रजिस्ट्री में एजेंटों की सूची होती है (उदाहरण के लिए, उड़ान, होटल, कार किराया, और गतिविधि के लिए), साथ ही उनके द्वारा उपलब्ध कराए गए फंक्शन या उपकरण।
* योजना को संबंधित एजेंटों को राउट करता है: उपकार्य की संख्या के आधार पर, योजनाकार या तो संदेश सीधे एक समर्पित एजेंट को भेजता है (एकल कार्य स्थिति में) या मल्टी-एजेंट सहयोग के लिए ग्रुप चैट मैनेजर के माध्यम से समन्वय करता है।
* परिणाम का सारांश प्रस्तुत करता है: अंत में, योजनाकार स्पष्टता के लिए उत्पन्न योजना का सारांश प्रस्तुत करता है।
निम्न Python कोड नमूना इन चरणों को दर्शाता है:

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

# यात्रा उपकार्य मॉडल

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # हम एजेंट को कार्य सौंपना चाहते हैं

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# प्रकार-निर्धारित पर्यावरण चर के साथ क्लाइंट बनाएँ

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# उपयोगकर्ता संदेश परिभाषित करें

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

# लोड करने से पहले प्रतिक्रिया सामग्री एक मान्य JSON स्ट्रिंग है यह सुनिश्चित करें

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# JSON के रूप में लोड करने के बाद प्रतिक्रिया सामग्री प्रिंट करें

pprint(json.loads(response_content))
```

इसके बाद पूर्व कोड का आउटपुट आता है और आप इस संरचित आउटपुट का उपयोग `assigned_agent` को भेजने और अंतिम उपयोगकर्ता को यात्रा योजना का सारांश प्रस्तुत करने के लिए कर सकते हैं।

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

पूर्व कोड नमूने के साथ एक उदाहरण नोटबुक [यहाँ उपलब्ध](07-autogen.ipynb) है।

### पुनरावृत्त योजना

कुछ कार्यों के लिए आगे-पीछे या पुनः योजना की आवश्यकता होती है, जहाँ एक उपकार्य का परिणाम अगले उपकार्य को प्रभावित करता है। उदाहरण के लिए, यदि एजेंट उड़ान बुकिंग करते हुए अप्रत्याशित डेटा फॉर्मेट पाता है, तो उसे होटल बुकिंग पर जाने से पहले अपनी रणनीति में समायोजन करना पड़ सकता है।

इसके अतिरिक्त, उपयोगकर्ता प्रतिक्रिया (जैसे कोई व्यक्ति जो पहले फ्लाइट को प्राथमिकता देता है) आंशिक पुनरावृत्ति को ट्रिगर कर सकती है। इस गतिशील, पुनरावृत्त दृष्टिकोण से अंतिम समाधान वास्तविक दुनिया की सीमाओं और विकसित हो रही उपयोगकर्ता प्राथमिकताओं के अनुरूप होता है।

उदाहरण कोड

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. पिछली कोड की तरह ही और उपयोगकर्ता इतिहास, वर्तमान योजना को पास करें
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
# .. पुन: योजना बनाएं और कार्यों को संबंधित एजेंटों को भेजें
```

अधिक व्यापक योजना के लिए Magnetic One देखें <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">ब्लॉगपोस्ट</a> जो जटिल कार्यों को हल करता है।

## सारांश

इस लेख में हमने देखा कि कैसे एक योजना निर्माता बनाना संभव है जो उपलब्ध एजेंटों को गतिशील रूप से चयनित कर सकता है। योजनाकार का आउटपुट कार्यों को तोड़ता है और एजेंटों को सौंपता है ताकि वे क्रियान्वित हो सकें। यह माना जाता है कि एजेंटों के पास कार्य को पूरा करने के लिए आवश्यक फंक्शन/उपकरणों की पहुंच है। एजेंटों के अलावा, आप अन्य पैटर्न जैसे रिफ्लेक्शन, सारांशकार, और राउंड रॉबिन चैट भी शामिल कर सकते हैं ताकि कस्टमाइजेशन और बढ़ाया जा सके।

## अतिरिक्त संसाधन

AutoGen Magnetic One - एक जनरलिस्ट मल्टी-एजेंट सिस्टम जो जटिल कार्यों के समाधान के लिए है और जो कई चुनौतीपूर्ण एजेंटिक बेन्चमार्क पर प्रभावशाली परिणाम प्राप्त कर चुका है। संदर्भ: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>। इस कार्यान्वयन में ऑर्केस्ट्रेटर कार्य-विशिष्ट योजना बनाता है और उपलब्ध एजेंटों को ये कार्य सौंपता है। योजना बनाने के अलावा ऑर्केस्ट्रेटर एक ट्रैकिंग तंत्र भी लागू करता है ताकि कार्य की प्रगति की निगरानी हो सके और आवश्यकता अनुसार पुनः योजना बनाई जा सके।

### योजना डिजाइन पैटर्न के बारे में और प्रश्न हैं?

अन्य शिक्षार्थियों से मिलने, कार्यालय समय में भाग लेने और अपनी एआई एजेंट से संबंधित प्रश्नों के उत्तर पाने के लिए [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) से जुड़ें।

## पिछला पाठ

[विश्वसनीय AI एजेंट बनाना](../06-building-trustworthy-agents/README.md)

## अगला पाठ

[मल्टी-एजेंट डिजाइन पैटर्न](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**अस्वीकरण**:  
इस दस्तावेज़ का अनुवाद एआई अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके किया गया है। हम सटीकता के लिए प्रयासरत हैं, लेकिन कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियाँ या गलतियाँ हो सकती हैं। मूल दस्तावेज़ उसकी मूल भाषा में आधिकारिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए पेशेवर मानव अनुवाद की सलाह दी जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम उत्तरदायी नहीं हैं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->