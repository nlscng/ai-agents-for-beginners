[![Planning Design Pattern](../../../translated_images/ta/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(இந்த பாடத்தின் வீடியோவை பார்ப்பதற்கு மேலே உள்ள படத்தை கிளிக் செய்யவும்)_

# திட்டமிடல் வடிவமைப்பு

## தொடக்கம்

இந்த பாடத்தில் கீழ்காணும்தை கற்றுக்கொள்வீர்கள்

* தெளிவான ஒரு மொத்த இலக்கை வரையறுத்து சிக்கலான பணியை கையாளக்கூடிய பகுதிகளாகப் பிரித்தல்.
* நம்பகத்தன்மை மற்றும் இயந்திரம் வாசிக்கக்கூடிய பதில்களுக்கு கட்டமைக்கப்பட்ட வெளியீட்டை பயன்படுத்துதல்.
* நிகழ்வு சார்ந்த அணுகுமுறையை உபயோகிப்பதன் மூலம் பரிணாம பணிகள் மற்றும் எதிர்பாராத உள்ளீடுகளை கையாளுதல்.

## கற்றல் இலக்குகள்

இந்த பாடத்தை முடித்தவுடன், நீங்கள் கீழ்காணும் விஷயங்களை புரிந்துகொள்வீர்கள்:

* ஒரு செயற்கை நுண்ணறிவு முகவருக்கான மொத்த இலக்கை நிர்ணயித்தல், அவன் என்ன செய்ய வேண்டும் என்பதை தெளிவாக அறிந்திருப்பதை உறுதிப்படுத்துதல்.
* சிக்கலான பணியை கையாளக்கூடிய துணைப் பணிகளாகப் பிரித்து, அவற்றை தார்க்கீகமாக அமைத்தல்.
* முகவர்களுக்கு சரியான கருவிகள் (எ.கா., தேடல் கருவிகள் அல்லது தரவு பகுப்பாய்வு கருவிகள்) வழங்குதல், அவை எப்போது மற்றும் எப்படி பயன்படுத்தப்பட வேண்டும் என்பதை தீர்மானித்தல், எதிர்பாராத சூழ்நிலைகளுக்கு பதிலளித்தல்.
* துணைப் பணிகளின் முடிவுகளை மதிப்பிடுத்தல், செயல்திறனை அளவிடுதல் மற்றும் இறுதி வெளியீட்டை மேம்படுத்த விருப்பப்படி நடவடிக்கை எடுக்குதல்.

## மொத்த இலக்கை வரையறுத்தல் மற்றும் பணியை பிரித்தல்

![Defining Goals and Tasks](../../../translated_images/ta/defining-goals-tasks.d70439e19e37c47a.webp)

பல حقیقي உலக பணிகள் ஒரே கட்டத்தில் கையாள முடியாதほど சிக்கலானவை. ஒரு செயற்கை நுண்ணறிவு முகவர் தன் திட்டமிடல் மற்றும் நடவடிக்கைகளை வழிநடத்த ஒரு சுருக்கமான இலக்கை தேவைப்படுத்தி நல்வருத்து வேண்டும். உதாரணமாக, கீழ்காணும் இலக்கை எடுத்துக்கொள்ளலாம்:

    "3-நாள் பயணத் திட்டத்தை உருவாக்குதல்."

இது எளிதாகக் கூறப்படுவதாக இருந்தாலும், அதன் மேல் மேலும் சீரமைப்பு தேவைப்படும். இலக்கு தெளிவாக இருப்பதால், முகவர் (மற்றும் அவன் சக மனித ஒத்துழைப்பாளர்கள்) சரியான முடிவை அடைவதில் கவனம் செலுத்தக்கூடும், உதாரணமாக விமான விருப்பங்கள், ஹோட்டல் பரிந்துரைகள் மற்றும் செயல்பாடுகளுக்கான பரிந்துரைகளுடன் முழுமையான பயணத் திட்டத்தை உருவாக்குதல்.

### பணியை துணைப் பணிகளா பிரித்தல்

பெரிய அல்லது சிக்கலான பணிகள் சிறு, இலக்குக்களை நோக்கிச் செல்லும் துணைப் பணிகளாக பிரிக்கப்பட்டால் கையாள எளிதாக இருக்கும்.
பயணத் திட்ட உதாரணத்திற்கு, நீங்கள் இலக்கை பின்வருவிதமாக பிரிக்கலாம்:

* விமான முன்பதிவு
* ஹோட்டல் முன்பதிவு
* வாகனம் வாடகை
* தனிப்பயன் அமைப்பு

ஒவ்வொரு துணைப் பணியும் தனித்தனி முகவர்களால் அல்லது செயலிகளால் கையாளப்படலாம். ஒருவருக்கு சிறந்த விமானக் கூட்டு ஒப்பந்தங்களை தேடுதல் சிறப்பானது, மற்றொருவர் ஹோட்டல் முன்பதிவிற்கு கவனம் செலுத்தலாம். ஒருங்கிணைப்பாளர் அல்லது "தாழ்வான" முகவர் இந்த முடிவுகளை ஒரே ஒருங்கிணைந்த பயணத் திட்டமாக இறுதி பயனருக்காக தொகுத்து வழங்கலாம்.

இந்த மொடியூலர் அணுகுமுறை பரிணாம மேம்பாடுகளையும் அனுமதிக்கிறது. உதாரணமாக உணவு பரிந்துரைகள் அல்லது உள்ளூர் செயல்பாடுகளுக்கான சிறப்பு முகவர்களைச் சேர்க்கவும், மேலும் நேரத்தின்போது பயணத் திட்டத்தை மேம்படுத்தலாம்.

### கட்டமைக்கப்பட்ட வெளியீடு

பெரிய மொழி மாதிரிகள் (LLMs) கட்டமைக்கப்பட்ட வெளியீட்டை (எ.கா., JSON) உருவாக்க முடியும், இது தாழ்வான முகவர்களோ அல்லது சேவைகளோ பின்வட்டத்தில் எளிதாக எடுத்து செயலாக்க முடியும். இது பல முகவரிகள் உள்ள சூழலில் மிகவும் பயனுள்ளதாகும், இங்கு திட்டமிடல் வெளியீட்டை பெறுவதற்குப் பிறகு நாம் இந்த பணிகளை செயல்படுத்தலாம். விரைவு பார்வைக்காக இத்தொடர்பான <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">வலைப்பதிவு</a> பயன் படுத்தலாம்.

பின்வரும் Python குறியீட்டு துணுக்கில் ஒரு எளிய திட்டமிடல் முகவர்தான் இலக்கை துணைப் பணிகளாக பிரித்து கட்டமைக்கப்பட்ட திட்டத்தை உருவாக்குகிறது என்பதை எடுத்துக்காட்டுகிறது:

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

# பயணம் துணைபணி மாதிரி
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # பணி முகவருக்கு ஒப்படைக்க விரும்புகிறோம்

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # மாதிரியை உண்மையாக்க, உங்கள் GitHub அமைப்புகளில் தனிப்பட்ட அணுகல் டோக்கன் (PAT) உருவாக்க வேண்டும்.
    # இங்கே உள்ள வழிமுறைகளை பின்பற்றி உங்கள் PAT டோக்கனை உருவாக்கவும்: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# பயனர் செய்தியை வரையறு
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

# # பதில் உள்ளடக்கம் செல்லுபடியாகும் JSON சரங்கள் எனில் ஏற்றப்படுகிறது என்பதை உறுதி செய்க
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     ValueError("பதில் உள்ளடக்கம் செல்லுபடியாகும் JSON சரம் இல்லை") எழுப்பவும்

# # JSON ஆக ஏற்றிய பிறகு பதில் உள்ளடக்கத்தை அச்சிடவும்
# pprint(json.loads(response_content))

# MathReasoning மாதிரியுடன் பதில் உள்ளடக்கத்தை சரிபார்க்கவும்
# TravelPlan.model_validate(json.loads(response_content))
```

### பல முகவர் ஒருங்கிணைப்பு கொண்ட திட்டமிடல் முகவர்

இந்த உதாரணத்தில், ஒரு Semantic Router முகவர் பயனர் கோரிக்கையை (எ.கா., "எனது பயணத்திற்கான ஹோட்டல் திட்டம் தேவை.") பெறுகிறார்.

திட்டமிடுபவர் அப்பொழுது:

* ஹோட்டல் திட்டத்தை பெறுகிறார்: பயனருடைய செய்தியை எடுத்துக் கொண்டு, உபயோகிக்கக்கூடிய முகவர்களுக்கான விவரங்களுடன் கூடிய அமைப்பு அமைப்பின் அடிப்படையில், கட்டமைக்கப்பட்ட பயண திட்டத்தை உருவாக்குகிறார்.
* முகவர்களையும் அவர்களுடைய கருவிகளையும் பட்டியலிடுகிறார்: முகவர் பதிவு பயண, ஹோட்டல், வாகனம் வாடகை மற்றும் செயல்பாடுகளுக்கான முகவர்களின் பட்டியலை மற்றும் அவர்கள் வழங்கும் செயல்கள் அல்லது கருவிகளை வைத்துள்ளது.
* திட்டத்தை தகுதியுள்ள முகவர்களுக்கு வழிமாற்றுகிறார்: துணைப் பணிகளின் எண்ணிக்கையின் அடிப்படையில், ஒரே பணி இருப்பின் நேரடியாக ஒரு தனி முகவருக்கு அனுப்புகிறார், பல முகவர்கள் இருந்தால் குழு உரையாடல் மேலாளரின் மூலம் ஒருங்கிணைக்கிறார்.
* முடிவை சுருக்குகிறார்: இறுதியில், திட்டத்தை தெளிவாக சுருக்குகிறார்.
பின்வரும் Python குறியீடு இந்த படிகளை விளக்குகிறது:

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

# பயணம் துணைப் பணியின் மாதிரி

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # பணி முகவருக்கு அளிக்க விரும்புகிறோம்

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# வகை-சரிபார்க்கப்பட்ட சுற்றுப்புற மாறிகளுடன் கிளையன்ட் உருவாக்கவும்

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# பயனர் செய்தியை வரையறுக்கவும்

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

# பதிலின் உள்ளடக்கம் சரியான JSON சரம் என்பதை ஏற்றுவதற்கு முன் உறுதிபடுத்துங்கள்

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# JSON ஆக ஏற்றிய பின்பு பதிலின் உள்ளடக்கத்தை அச்சிடுக

pprint(json.loads(response_content))
```

அடுத்து வரும் வெளியீடு மேல்கூறிய குறியீட்டின் முடிவு, இதை நீங்கள் `assigned_agent`க்கு வழிமாற்றி பயணத் திட்டத்தை இறுதி பயனருக்கு சுருக்குவதற்குப் பயன்படுத்தலாம்.

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

மேலே கொடுத்துள்ள குறியீடு உதாரணத்துடன் கூடிய நோட்புக் [இங்கே](07-autogen.ipynb) கிடைக்கிறது.

### மறுபடியும் திட்டமிடல்

சில பணிகள் பின்னோக்கம் மற்றும் மறுபடியும் திட்டமிடலை தேவைப்படுத்தும், இங்கு ஒரே துணைப் பணியின் முடிவு அடுத்த பணியை பாதிக்கக்கூடும். உதாரணமாக, முகவர் விமான முன்பதிவு செய்யும்போது எதிர்பாராத தரவு வடிவத்தை கண்டுபிடித்தால், அடுத்த ஹோட்டல் முன்பதிவுக்கு செல்லும் முன் தன் நெறியமைப்பை மாற்ற வேண்டியிருக்கும்.

மேலும், பயனர் கருத்து (எ.கா. மனிதர் விரைவான விமானத்தை விரும்புகிறார் என்று முடிவு செய்தால்) பகுதி மறுபதிவை தூண்டலாம். இந்த நடவடிக்கையான, மறுபடியும் திட்டமிடும் அணுகுமுறை இறுதி தீர்வு உண்மை உலக கட்டுப்பாடுகளுடனும் வளரும் பயனர் விருப்பங்களுடனும் சேர்ந்து பொருந்தும் என்பதைக் உறுதி செய்கிறது.

எ.கா., குறியீடு

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. முந்தையக் குறியீட்டைப் போலவே மற்றும் பயனர் வரலாறையும், தற்போதைய திட்டத்தையும் கடத்தவும்
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
# .. மறுபடியும் திட்டமிட்டு பணிகளை தொடர்புடைய முகவர்களிடம் அனுப்பவும்
```

மேலும் விரிவான திட்டமிடலுக்காக Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">வலைப்பதிவு</a> பார்க்கவும்.

## சுருக்கம்

இந்த கட்டுரையில், நாம் ஒரு திட்டமிடலை உருவாக்கும் விதத்தை பார்த்தோம், அது வரையறுக்கப்பட்ட முகவர்களை தானாக தேர்ந்தெடுக்கிறது. திட்டமிடல் வெளியீடு பணிகளை துணைப் பணிகளாக பிரித்து அவற்றை செயல்படுத்த முகவர்களுக்கு ஒதுக்குகிறது. முகவர்கள் பணியை செய்ய தேவையான செயல்கள்/கருவிகளுக்கு அணுகல் உள்ளதாக கருதப்படுகிறது. முகவர்களுடன் சேர்த்து நீங்கள் பிரதிபலிப்பு, சுருக்கம் மற்றும் சுற்றுப் உரையாடல் போன்ற மற்ற வடிவங்களையும் சேர்க்கலாம்.

## கூடுதல் வளங்கள்

AutoGen Magentic One - சிக்கலான பணிகளை தீர்க்க ஒரு பொதுமக்கள் பல முகவர் அமைப்பு ஆகும் மற்றும் பல சவாலான முகவர் மதிப்பீடுகளில் சிறந்த முடிவுகளை பெற்றுள்ளது. குறிப்பாக: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. இந்த செயலாக்கத்தில் ஒருங்கிணைப்பாளர் பணிக்கான திட்டத்தை உருவாக்கி, அந்த பணிகளை கிடைக்கக்கூடிய முகவர்களுக்கு வழங்குகிறது. திட்டமிடலோடு கூடிய ஒருங்கிணைப்பாளர் பணியின் முன்னேற்றத்தைக் கண்காணிப்பதற்கும் மறுபடியும் திட்டமிடலுக்கும் கண்காணிப்பு முறையையும் பயன்படுத்துகிறான்.

### திட்டமிடல் வடிவமைப்பு பற்றிய மேலும் கேள்விகள் உள்ளனவா?

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) இல் சேர்ந்து மற்ற கற்றல் பெறுநர்களுடன் சந்தித்து, அலுவலக நேரங்களில் கலந்துரையாடி உங்கள் செயற்கை நுண்ணறிவு முகவர் தொடர்பான கேள்விகளுக்கு பதில்கள் பெறலாம்.

## முந்தைய பாடம்

[விசுவாசமாக்கக்கூடிய செயற்கை நுண்ணறிவு முகவர்கள் உருவாக்குதல்](../06-building-trustworthy-agents/README.md)

## அடுத்த பாடம்

[பல முகவர் வடிவமைப்பு](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**வெளியறிக்கை**:
இந்த ஆவணம் [Co-op Translator](https://github.com/Azure/co-op-translator) என்ற ஏ.ஐ. மொழிபெயர்ப்பு சேவையை பயன்படுத்தி மொழிபெயர்க்கப்பட்டது. துல்லியத்துக்கு நாம் முயலுகின்றபோதும், தானாக இயங்கும் மொழிபெயர்ப்புகளில் பிழைகள் அல்லது தவறுகள் இருக்கக்கூடும் என்பதை தயவுசெய்து கவனத்தில் கொள்ளவும். மூல ஆவணம் தன its native language மொழியில் தான் அதிகாரப்பூர்வ ஆதாரமாகக் கருதப்பட வேண்டும். முக்கியமான தகவல்களுக்காக, திறமையான மனித மொழிபெயர்ப்பை பரிந்துரைக்கின்றோம். இந்த மொழிபெயர்ப்பின் பயன்படுத்துதலால் ஏற்படும் ஏதேனும் தவறான புரிதல்கள் அல்லது தவறான விளக்கங்களுக்கு நாங்கள் பொறுப்பில்லாதவர்கள் என்பதை அறிவிப்போம்.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->