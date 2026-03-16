[![योजना डिझाइन पॅटर्न](../../../translated_images/mr/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(वरील प्रतिमा क्लिक करून या धड्याचा व्हिडिओ पाहा)_

# योजना रचना

## परिचय

या धड्यामध्ये खालील गोष्टींचा समावेश आहे

* एक स्पष्ट एकूण उद्दिष्ट निश्चित करणे आणि एका जटिल कार्याचे व्यवस्थापनीय उपकार्यात विभाजन करणे.
* अधिक विश्वसनीय आणि मशीन-पठनीय प्रतिसादांसाठी संरचित आउटपुटचा वापर करणे.
* डायनॅमिक कार्ये आणि अनपेक्षित इनपुट हाताळण्यासाठी इव्हेंट-चालित पध्दतीचा अवलंब करणे.

## शिकण्याची उद्दिष्टे

हा धडा पूर्ण केल्यानंतर, आपल्याला खालील गोष्टींबाबत समज मिळेल:

* एआय एजंटसाठी एकूण उद्दिष्ट ओळखणे आणि सेट करणे, ज्यामुळे त्याला स्पष्टपणे कळेल की काय साध्य करायचे आहे.
* एका जटिल कार्याचे छोटे, उद्दिष्ट-केन्द्रित उपकार्यांमध्ये विभाजन करणे आणि ते तार्किक क्रमाने आयोजित करणे.
* एजंट्सना योग्य साधने (उदा., शोध साधने किंवा डेटा विश्लेषण साधने) उपलब्ध करून देणे, ते कधी आणि कसे वापरायची हे ठरवणे, आणि उघड्या परिस्थितींना हाताळणे.
* उपकार्यांचे परिणाम मूल्यांकन करणे, कार्यक्षमतेचे मोजमाप करणे, आणि अंतिम आउटपुट सुधारण्यासाठी क्रियेत पुनरावृत्ती करणे.

## एकूण उद्दिष्ट निश्चित करणे आणि कार्य विभाजन करणे

![उद्दिष्टे आणि कार्यांचे निर्धारण](../../../translated_images/mr/defining-goals-tasks.d70439e19e37c47a.webp)

बहुतांश वास्तविक जगातील कामे एकाच टप्प्यात हाताळण्यासाठी खूप जटिल असतात. एआय एजंटला त्याच्या नियोजनासाठी आणि कृतीसाठी मार्गदर्शन करण्यासाठी एक संक्षिप्त उद्दिष्टाची आवश्यकता असते. उदाहरणार्थ, खालील उद्दिष्ट विचारात घ्या:

    "3-दिवसीय प्रवास दिनदर्शिका तयार करा."

हे सांगणे सोपे असले तरीही, त्यात अजून संशोधनाची गरज असते. उद्दिष्ट जितके स्पष्ट असेल, तितके एजंट (आणि कोणतेही मानवी सहकारी) योग्य परिणाम साध्य करण्यावर लक्ष केंद्रित करू शकतात, जसे की फ्लाइटपर्याय, हॉटेल शिफारसी, आणि क्रियाकलापांचे सुचवणूक असलेली सर्वसमावेशक दिनदर्शिका तयार करणे.

### कार्य विभाजन

मोठी किंवा सूक्ष्म कामे छोटे, उद्देश-आधारित उपकार्यांमध्ये विभागल्यास ती अधिक व्यवस्थापनीय होतात.
प्रवास दिनदर्शिकेच्या उदाहरणासाठी, आपण उद्दिष्ट खालीलप्रमाणे विभाजित करू शकता:

* फ्लाइट बुकिंग
* हॉटेल बुकिंग
* कार भाड्याने घेणे
* वैयक्तिकरण

प्रत्येक उपकार्य नंतर समर्पित एजंट्स किंवा प्रक्रियांद्वारे हाताळले जाऊ शकते. एक एजंट सर्वोत्तम फ्लाइट डील शोधण्यात तज्ज्ञ असू शकतो, दुसरा हॉटेल बुकिंगवर लक्ष केंद्रित करेल, इत्यादी. एक समन्वयक किंवा "डाऊनस्ट्रीम" एजंट नंतर हे परिणाम एका सुसंगत दिनदर्शिकेत अंतिम वापरकर्त्यास देऊ शकतो.

ही मॉड्युलर पध्दत आणखी सुधारणा करण्याची परवानगी देते. उदाहरणार्थ, आपण फूड शिफारसी किंवा स्थानिक क्रियाकलाप सुचवणारे विशेष एजंट जोडू शकता आणि कालांतराने दिनदर्शिका सुधारू शकता.

### संरचित आउटपुट

Large Language Models (LLMs) संरचित आउटपुट (उदा. JSON) तयार करू शकतात जे डाउनस्ट्रीम एजंट्स किंवा सेवांसाठी पार्स आणि प्रक्रिया करणे सोपे असते. हे बहु-एजंट संदर्भात विशेषतः उपयुक्त आहे, जिथे आपण नियोजन आउटपुट प्राप्त झाल्यानंतर हे कार्ये अंमलात आणू शकतो. तात्काळ आढाव्यासाठी या <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">ब्लॉगपोस्ट</a> ला पाहा.

खालील Python तुकडा एका साध्या नियोजन एजंटद्वारे उद्दिष्ट उपकार्यांमध्ये विभाजित करताना आणि संरचित योजना तयार करताना दाखवतो:

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

# प्रवास उपकार्य मॉडेल
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # आम्हाला हे कार्य एजंटला नियुक्त करायचे आहे.

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # मॉडेलसोबत प्रमाणीकरण करण्यासाठी तुम्हाला तुमच्या GitHub सेटिंग्जमध्ये वैयक्तिक प्रवेश टोकन (PAT) तयार करावे लागेल.
    # येथील सूचनांचे पालन करून तुमचे PAT टोकन तयार करा: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# वापरकर्ता संदेश परिभाषित करा
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

# # लोड करण्यापूर्वी प्रतिसाद सामग्री वैध JSON स्ट्रिंग आहे याची खात्री करा
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Response content is not a valid JSON string")

# # JSON म्हणून लोड केल्यानंतर प्रतिसाद सामग्री छापा
# pprint(json.loads(response_content))

# प्रतिक्रिया सामग्री MathReasoning मॉडेलद्वारे सत्यापित करा
# TravelPlan.model_validate(json.loads(response_content))
```

### मल्टी-एजंट ऑर्केस्ट्रेशनसह नियोजन एजंट

या उदाहरणात, एक Semantic Router Agent वापरकर्ता विनंती (उदा., "माझ्या प्रवासासाठी मला हॉटेल योजना हवी आहे.") प्राप्त करतो.

प्लॅनर नंतर:

* हॉटेल योजना प्राप्त करतो: प्लॅनर वापरकर्त्याचा संदेश घेतो आणि सिस्टम प्रॉम्प्टच्या (उपलब्ध एजंट तपशीलांसहित) आधारावर एक संरचित प्रवास योजना तयार करतो.
* एजंट्स आणि त्यांच्या साधनांची यादी बनवतो: एजंट रजिस्ट्रीमध्ये एजंट्सची यादी (उदा., फ्लाइट, हॉटेल, कार भाडे, आणि क्रियाकलापांसाठी) आणि ते प्रदान करणार्‍या फंक्शन्स किंवा साधनांचा समावेश असतो.
* योजनाला संबंधित एजंटकडे मार्गक्रमण करतो: उपकार्यांच्या संख्येनुसार, प्लॅनर एकदाच एखाद्या समर्पित एजंटला संदेश पाठवू शकतो (एकट्या-कार्याच्या परिस्थितीत) किंवा बहु-एजंट सहकार्यासाठी समूह चॅट व्यवस्थापकाद्वारे समन्वयित करतो.
* निकालाचा सारांश करतो: शेवटी, प्लॅनर स्पष्टतेसाठी तयार केलेल्या योजनेचा सारांश देतो.
खालील Python कोड नमुना हे पायऱ्या स्पष्ट करतो:

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

# प्रवास उपकार्य मॉडेल

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # आम्ही कार्य एजंटला नियुक्त करू इच्छितो

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# प्रकार तपासलेले पर्यावरण चलांसह क्लायंट तयार करा

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# वापरकर्त्याचा संदेश परिभाषित करा

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

# लोड करण्यापूर्वी प्रतिसादाची सामग्री वैध JSON स्ट्रिंग आहे याची खात्री करा

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# JSON म्हणून लोड केल्यानंतर प्रतिसादाची सामग्री प्रिंट करा

pprint(json.loads(response_content))
```

खालील गोष्ट मागील कोडमधून आउटपुट आहे आणि आपण हे संरचित आउटपुट नंतर `assigned_agent` कडे मार्गदर्शन करण्यासाठी आणि अंतिम वापरकर्त्यास प्रवास योजना सारांशित करण्यासाठी वापरू शकता.

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

पूर्वीच्या कोड नमुन्यांसह एक उदाहरण नोटबुक [इथे](07-autogen.ipynb) उपलब्ध आहे.

### पुनरावृत्ती नियोजन

काही कार्यांमध्ये परस्पर संवाद किंवा पुनर्नियोजन आवश्यक असते, जिथे एका उपकार्याचा निकाल पुढच्या उपकार्यावर परिणाम करतो. उदाहरणार्थ, जर एजंट फ्लाइट बुक करताना अनपेक्षित डेटा स्वरूप सापडले, तर त्याला हॉटेल बुकिंगकडे जाण्यापूर्वी आपली रणनीती अनुकूल करावी लागू शकते.

याशिवाय, वापरकर्त्याच्या अभिप्रायाने (उदा., एखाद्या माणसाने आधीची फ्लाइट पसंत केली नाही असे ठरवणे) आंशिक पुनर-योजना सुरू होऊ शकते. ही डायनॅमिक, आवर्ती पध्दत सुनिश्चित करते की अंतिम समाधान वास्तविक-विश्व मर्यादा आणि बदलणाऱ्या वापरकर्त्याच्या आवडीनुसार जुळून येते.

उदा. नमुना कोड

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. मागील कोडप्रमाणेच आणि वापरकर्त्याचा इतिहास आणि सध्याची योजना पुढे द्या
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
# .. पुन्हा योजना तयार करा आणि संबंधित एजंटांना कार्ये पाठवा
```

अधिक व्यापक नियोजनासाठी, क्लिष्ट कार्य सोडवण्यासाठी Magnetic One बद्दलचा हा <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">ब्लॉगपोस्ट</a> पहा.

## सारांश

या लेखात आपण कसे एक प्लॅनर तयार करू शकतो ज्यामुळे ते परिभाषित झालेल्या उपलब्ध एजंट्समधून डायनॅमिकपणे निवड करू शकते हे पाहिले. प्लॅनरचे आउटपुट कार्यांचे विभाजन करते आणि एजंट्सना असाइन करते जेणेकरून ती अंमलात आणली जाऊ शकतात. गृहित धरले आहे की एजंट्सकडे ते कार्य पार पडण्यासाठी आवश्यक फंक्शन्स/साधने उपलब्ध आहेत. एजंट्सव्यतिरिक्त आपण प्रतिबिंबन, सारांशकार, आणि राउंड रॉबिन चॅट सारख्या इतर पॅटर्न्स देखील समाविष्ट करू शकता जेणेकरून अधिक सानुकूलन करता येईल.

## अधिक संसाधने

AutoGen Magentic One - क्लिष्ट कार्ये सोडवण्यासाठी एक जनरलिस्ट मल्टी-एजंट सिस्टम असून अनेक आव्हानात्मक एजंटिक बेंचमार्कवर उल्लेखनीय परिणाम मिळविला आहे. संदर्भ: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. या अंमलबजावणीत ऑर्केस्ट्रेटर कार्य-विशिष्ट योजना तयार करतो आणि उपलब्ध एजंट्सना ही कामे सुपूर्त करतो. नियोजनाशिवाय ऑर्केस्ट्रेटरमध्ये कार्याची प्रगती ट्रॅक करण्यासाठी आणि आवश्यकतेनुसार पुनर्नियोजन करण्यासाठी एक ट्रॅकिंग यंत्रणा देखील वापरली जाते.

### योजना डिझाइन पॅटर्नबद्दल अधिक प्रश्न आहेत का?

इतर शिकणाऱ्यांशी भेटण्यासाठी, ऑफिस आवर्समध्ये भाग घेण्यासाठी आणि आपल्या AI एजंट्सबाबतचे प्रश्न सोडवण्यासाठी [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) मध्ये सहभागी व्हा.

## मागील धडा

[विश्वसनीय AI एजंट तयार करणे](../06-building-trustworthy-agents/README.md)

## पुढील धडा

[मुल्टी-एजंट डिझाइन पॅटर्न](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
अस्वीकरण:
हा दस्तऐवज AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून अनुवादित केला आहे. आम्ही अचूकतेसाठी प्रयत्न करतो, परंतु कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये चुका किंवा अचूकतेच्या त्रुटी असू शकतात. मूळ दस्तऐवज त्याच्या मूळ भाषेत अधिकृत स्रोत मानला जावा. महत्वाच्या माहितीसाठी व्यावसायिक मानवी अनुवादाची शिफारस केली जाते. या अनुवादाच्या वापरामुळे उद्भवणाऱ्या कोणत्याही गैरसमजुती किंवा चुकीच्या अर्थ लावण्याबद्दल आम्ही जबाबदार नाही.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->