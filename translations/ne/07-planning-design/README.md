[![Planning Design Pattern](../../../translated_images/ne/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(यो पाठको भिडियो हेर्न माथिको छवि क्लिक गर्नुहोस्)_

# योजना डिजाइन

## परिचय

यो पाठमा समावेश हुने विषयहरू:

* स्पष्ट समग्र लक्ष्य निर्धारण र एक जटिल कार्यलाई व्यवस्थापनयोग्य कार्यहरूमा विभाजन।
* विश्वसनीय र मेसिन-यन्त्रले पढ्न सकिने प्रतिक्रियाका लागि संरचित आउटपुटको उपयोग।
* गतिशील कार्यहरू र अनपेक्षित इनपुटहरू सम्हाल्न कार्यक्रम-चालित दृष्टिकोणको प्रयोग।

## सिकाइ लक्ष्यहरू

यस पाठ पूरा गरेपछि, तपाईंलाई निम्न विषयमा बुझाइ हुनेछ:

* एक AI एजेन्टका लागि समग्र लक्ष्य पहिचान गर्नु र सेट गर्नु, जसले स्पष्ट रूपमा थाहा पाउँछ कि के हासिल गर्न आवश्यक छ।
* जटिल कार्यलाई व्यवस्थापनयोग्य उपकार्यहरूमा विभाजन गर्नु र तिनीहरूलाई तार्किक क्रममा व्यवस्थित गर्नु।
* एजेन्टहरूलाई सही उपकरणहरू (जस्तै, खोज उपकरण वा डाटा विश्लेषण उपकरण) प्रदान गर्नु, कहिले र कसरी प्रयोग गर्ने निर्णय गर्नु, र आउन सक्ने अनपेक्षित परिस्थितिहरूको सामना गर्नु।
* उपकार्यहरूको नतिजा मूल्यांकन गर्नु, प्रदर्शन मापन गर्नु, र अन्तिम आउटपुट सुधार गर्न कारबाहीहरू पुनरावृत्ति गर्नु।

## समग्र लक्ष्य निर्धारण र कार्यको विभाजन

![Defining Goals and Tasks](../../../translated_images/ne/defining-goals-tasks.d70439e19e37c47a.webp)

प्रायः वास्तविक संसारका कार्यहरू एकै पटकमा समाधान गर्न धेरै जटिल हुन्छन्। एक AI एजेन्टलाई आफ्नो योजना र क्रियाकलापहरूलाई निर्देशन दिन संक्षिप्त उद्देश्य आवश्यक हुन्छ। उदाहरणको रूपमा, निम्न लक्ष्य विचार गर्नुहोस्:

    "३-दिने यात्रा कार्यक्रम तयार पार्नु।"

यो भन्छ गर्दा सरल जस्तो लाग्छ, तर अझै यसको सुधार आवश्यक छ। लक्ष्य जतिसुकै स्पष्ट हुन्छ, एजेन्ट (र कुनै मानव सहकर्मीहरू) सही नतिजा हासिल गर्न केन्द्रित हुन सजिलो हुन्छ, जस्तै एउटा व्यापक यात्रा कार्यक्रम तयार पार्ने जसमा उडान विकल्पहरू, होटल सिफारिसहरू, र गतिविधि सुझावहरू समावेश हुन्छन्।

### कार्य विभाजन

ठूलो वा जटिल कार्यहरू साना, लक्ष्य-केन्द्रित उपकार्यहरूमा विभाजन गर्दा व्यवस्थापनयोग्य हुन्छन्। यात्राको उदाहरणमा, तपाईं लक्ष्यलाई यसरी विभाजन गर्न सक्नुहुन्छ:

* उडान बुकिंग
* होटल बुकिंग
* कार भाडामा लिने
* वैयक्तिकरण

प्रत्येक उपकार्यलाई समर्पित एजेन्ट वा प्रक्रियाले सम्बोधन गर्न सक्छ। एउटा एजेन्टले सबैभन्दा राम्रो उडान सम्झौता खोज्न विशेषज्ञता राख्न सक्छ, अर्को होटल बुकिंगमा केन्द्रित हुन्छ, आदि। एक समन्वय गर्ने वा "डाउनस्ट्रीम" एजेन्टले यी परिणामहरूलाई अन्तिम प्रयोगकर्ताका लागि एक सम्पूर्ण यात्रा कार्यक्रममा समेट्न सक्छ।

यो मोड्युलर दृष्टिकोणले क्रमिक सुधार गर्न पनि अनुमति दिन्छ। उदाहरणका लागि, तपाईं खानाको सिफारिस वा स्थानीय गतिविधि सुझावका लागि विशेषज्ञ एजेन्टहरू थप्न सक्नुहुन्छ र समयक्रममा यात्रा कार्यक्रम सुधार गर्न सक्नुहुन्छ।

### संरचित आउटपुट

ठूला भाषा मोडेलहरूले (LLMs) संरचित आउटपुट (जस्तै JSON) उत्पन्न गर्न सक्छन् जुन डाउनस्ट्रीम एजेन्ट वा सेवाहरूसँग पार्स र प्रक्रिया गर्न सजिलो हुन्छ। यो बहु-एजेन्ट सन्दर्भमा विशेष उपयोगी हुन्छ, जहाँ हामी योजना आउटपुट प्राप्त भएपछि यी कार्यहरू सञ्चालन गर्न सक्छौं। यसका लागि एक छिटो अवलोकनका लागि <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">ब्लगपोष्ट</a> हेर्नुहोस्।

तलको Python स्निपेटले एक सरल योजना एजेन्टले लक्ष्यलाई उपकार्यहरूमा विभाजित गर्दै संरचित योजना बनाएको देखाउँछ:

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

# यात्रा उपकार्य मोडेल
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # हामी कार्य एजेन्टलाई असाइन गर्न चाहन्छौं

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # मोडेलसँग प्रमाणीकरण गर्न तपाईंलाई आफ्नो GitHub सेटिङहरूमा व्यक्तिगत पहुँच टोकन (PAT) सिर्जना गर्न आवश्यक हुनेछ।
    # यहाँका निर्देशनहरू पालना गरेर तपाईंको PAT टोकन सिर्जना गर्नुहोस्: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# प्रयोगकर्ता सन्देश परिभाषित गर्नुहोस्
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

# # लोड गर्नु अघि प्रतिक्रिया सामग्री मान्य JSON स्ट्रिंग हो कि होइन सुनिश्चित गर्नुहोस्
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# यदि response_content None छ भने:
#     ValueError उठाउनुहोस्("प्रतिक्रियाको सामग्री मान्य JSON स्ट्रिंग होइन")

# # JSON को रूपमा लोड गरेपछि प्रतिक्रिया सामग्री प्रिन्ट गर्नुहोस्
# pprint(json.loads(response_content))

# MathReasoning मोडेलसँग प्रतिक्रिया सामग्री प्रमाणीकरण गर्नुहोस्
# TravelPlan.model_validate(json.loads(response_content))
```

### बहु-एजेन्ट समन्वय सहित योजना एजेन्ट

यस उदाहरणमा, एक सेमान्टिक राउटर एजेन्टले प्रयोगकर्ताको अनुरोध प्राप्त गर्दछ (जस्तै, "म मेरो यात्राको लागि होटल योजना चाहन्छु।")।

योजनाकारले त्यसपछि:
* होटल योजना प्राप्त गर्दछ: योजनाकारले प्रयोगकर्ताको सन्देशलाई लिन्छ र सिस्टम प्रॉम्प्ट (उपलब्ध एजेन्ट विवरण सहित) आधारमा संरचित यात्रा योजना उत्पन्न गर्छ।
* एजेन्टहरू र तिनीहरूको उपकरणहरू सूचीबद्ध गर्छ: एजेन्ट दर्ताले एजेन्टहरूको सूची राख्छ (जस्तै, उडान, होटल, कार भाडा, र गतिविधि) र तिनीहरूका उपकरण वा कार्यहरू।
* योजना सम्बन्धित एजेन्टहरूमा मार्गनिर्देशन गर्छ: उपकार्यहरूको संख्यामा निर्भर गर्दै, योजनाकारले सिधै समर्पित एजेन्टलाई सन्देश पठाउँछ (एकल कार्य अवस्थामा) वा बहु-एजेन्ट सहकार्यका लागि समूह च्याट प्रबन्धक मार्फत समन्वय गर्छ।
* परिणाम सारांश गर्दछ: अन्त्यमा, योजनाकारले उत्पन्न योजनाको स्पष्ट सारांश प्रस्तुत गर्छ।
तलको Python कोड नमूनाले यी चरणहरू देखाउँछ:

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

# यात्रा उपकार्य मोडेल

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # हामी एजेन्टलाई कार्य असाइन गर्न चाहन्छौं

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# प्रकार जाँच गरिएको वातावरण चरहरूसँग क्लाइन्ट सिर्जना गर्नुहोस्

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# प्रयोगकर्ता सन्देश परिभाषित गर्नुहोस्

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

# प्रतिक्रिया सामग्री लोड गर्नु अघि यो वैध JSON स्ट्रिङ हो सुनिश्चित गर्नुहोस्

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# प्रतिक्रिया सामग्री JSON को रूपमा लोड गरेपछि मुद्रण गर्नुहोस्

pprint(json.loads(response_content))
```

तलको आउटकमले अघिल्लो कोडबाट प्राप्त संरचित आउटपुट प्रदर्शन गर्छ र त्यसपछि तपाईं यसलाई `assigned_agent` मा मार्गनिर्देशित गरी यात्रा योजना अन्तिम प्रयोगकर्तालाई सारांश गर्न प्रयोग गर्न सक्नुहुन्छ।

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

अघिल्लो कोड नमूनासहितको उदाहरण नोटबुक [यहाँ](07-autogen.ipynb) उपलब्ध छ।

### पुनरावृत्त योजना

केही कार्यहरूको लागि पछाडोपछि वा पुन: योजना आवश्यक पर्छ, जहाँ एउटा उपकार्यको परिणाम अर्को उपकार्यलाई असर गर्छ। उदाहरणका लागि, यदि एजेन्टले उडान बुक गर्दा अनपेक्षित डाटा ढाँचा पाउँछ भने, यसले आफ्ना रणनीति समायोजन गर्नुपर्ने हुन सक्छ र त्यसपछि होटल बुकिंगतर्फ बढ्नुपर्ने हुन्छ।

थप रूपमा, प्रयोगकर्ताको प्रतिक्रिया (जस्तै, मानवले पहिले उडान रोज्ने निर्णय गर्नु) ले आंशिक पुन: योजना सुरु गर्न सक्छ। यो गतिशील, पुनरावृत्त दृष्टिकोणले अन्तिम समाधानलाई वास्तविक संसारको सिमा र विकासशील प्रयोगकर्ता प्राथमिकताहरू अनुरूप बनाउँछ।

उदाहरण कोड

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. पहिलेको कोड जस्तै र प्रयोगकर्ता इतिहास, वर्तमान योजना पास गर्नुहोस्
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
# .. पुनः योजना बनाउनुहोस् र कार्यहरू सम्बन्धित एजेन्टहरूलाई पठाउनुहोस्
```

अझ विस्तृत योजना बनाउन Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">ब्लगपोष्ट</a> हेर्नुहोस् जुन जटिल कार्यहरू समाधान गर्नको लागि बनाइएको छ।

## सारांश

यस लेखमा हामीले हेरेका छौं कि कसरी हामी यस्तो योजनाकार बनाउन सक्छौं जसले उपलब्ध एजेन्टहरूलाई गतिशील रूपमा चयन गर्न सक्छ। योजनाकारले कार्यहरूलाई विभाजन गरी एजेन्टहरूलाई कार्यहरू असाइन गर्छ र तिनलाई कार्यान्वयन गरिन्छ। यो मानिन्छ कि एजेन्टहरूलाई आवश्यक कार्यहरू सम्पन्न गर्न आवश्यक कार्य/उपकरणहरूको पहुँच छ। एजेन्टहरू बाहेक तपाईं प्रतिबिम्ब, सारांशकर्ता, र राउन्ड रोबिन च्याट जस्ता अन्य ढाँचाहरू पनि समावेश गर्न सक्नुहुन्छ अझ अनुकूलनका लागि।

## अतिरिक्त स्रोतहरू

AutoGen Magnetic One - एक सामान्य बहु-एजेन्ट प्रणाली जसले जटिल कार्यहरू समाधान गर्न प्रतिष्ठित नतिजा हासिल गरेको छ। सन्दर्भ: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>। यस कार्यान्वयनमा, ऑर्केस्ट्रेटरले कार्य-विशिष्ट योजना बनाउँछ र ती कार्यहरू उपलब्ध एजेन्टहरूलाई निर्देशन गर्छ। योजना सँगसँगै ऑर्केस्ट्रेटरले कामको प्रगति अनुगमन गर्न र आवश्यक अनुसार पुनः योजना बनाउन ट्रयाकिङ मेकानिज्म प्रयोग गर्छ।

### योजना डिजाइन नमुना सम्बन्धी थप प्रश्नहरू छन्?

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) मा सहभागी हुनुहोस् जहाँ तपाईं अन्य सिक्नेहरूका साथ भेट गर्न, कार्यालय समयहरूमा भाग लिन, र तपाईंका AI एजेन्ट सम्बन्धी प्रश्नहरूको जवाफ पाउनुहुनेछ।

## विगतको पाठ

[विश्वसनीय AI एजेन्टहरू निर्माण](../06-building-trustworthy-agents/README.md)

## अर्को पाठ

[बहु-एजेन्ट डिजाइन नमुना](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**अस्वीकरण**:
यस कागजातलाई AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) को प्रयोग गरेर अनुवाद गरिएको हो। हामी शुद्धताका लागि प्रयासरत छौँ, तर कृपया जानकार हुनुहोस् कि स्वचालित अनुवादहरूमा त्रुटि वा अशुद्धता हुन सक्छ। मूल कागजातलाई यसको मातृ भाषामा अधिकारिक स्रोत मानिनुपर्छ। महत्वपूर्ण जानकारीका लागि व्यावसायिक मानवीय अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट हुने कुनै पनि गलतफहमी वा गलत व्याख्याप्रति हामी जिम्मेवार छैनौं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->