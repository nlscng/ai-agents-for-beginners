[![Mipango ya Muundo wa Mipango](../../../translated_images/sw/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Bonyeza picha hapo juu kutazama video ya somo hili)_

# Muundo wa Mipango

## Utangulizi

Somo hili litashughulikia

* Kuweka lengo kuu wazi na kugawanya kazi tata kuwa kazi ndogo zinazoweza kusimamiwa.
* Kutumia matokeo yaliyopangwa kwa muundo kwa majibu ya kuaminika zaidi na yanayoweza kusomeka na mashine.
* Kutumia mbinu inayoendeshwa na matukio kushughulikia kazi zinazobadilika na taarifa zisizotarajiwa.

## Malengo ya Kujifunza

Baada ya kukamilisha somo hili, utakuwa na ufahamu kuhusu:

* Kutambua na kuweka lengo kuu kwa wakala wa AI, kuhakikisha anajua wazi kinachotakiwa kufanikishwa.
* Kugawanya kazi tata kuwa kazi ndogo zinazoweza kusimamiwa na kuzipanga kwa mfuatano wa mantiki.
* Kuwasidia mawakala na zana sahihi (mfano, zana za utafutaji au uchambuzi wa data), kuamua ni lini na jinsi zinavyotumika, na kushughulikia hali zisizotarajiwa zinazotokea.
* Kutathmini matokeo ya kazi ndogo, kupima utendaji, na kurudia hatua za kuboresha matokeo ya mwisho.

## Kuweka Lengo Kuu na Kugawanya Kazi

![Kuweka Malengo na Kazi](../../../translated_images/sw/defining-goals-tasks.d70439e19e37c47a.webp)

Kazi nyingi halisi ni tata mno kushughulikia kwa hatua moja. Wakala wa AI anahitaji lengo fupi la kuelekeza mipango na vitendo vyake. Kwa mfano, fikiria lengo:

    "Tengeneza ratiba ya safari ya siku 3."

Ingawa ni rahisi kusema, bado linahitaji kuboreshwa. Kadri lengo linavyokuwa wazi zaidi, ndivyo wakala (na washirika wa binadamu) wanavyoweza kuzingatia kufanikisha matokeo sahihi, kama kutengeneza ratiba kamilifu yenye chaguzi za ndege, mapendekezo ya hoteli, na mapendekezo ya shughuli.

### Ugawaji Kazi

Kazi kubwa au ngumu zinakuwa rahisi kusimamia wakati zikitenganishwa kuwa kazi ndogo zinazolenga malengo.
Kwa mfano wa ratiba ya safari, unaweza kugawanya lengo kubaki:

* Uhifadhi wa Ndege
* Uhifadhi wa Hoteli
* Kukodisha Gari
* Ubinafsishaji

Kila kazi ndogo inaweza kushughulikiwa na mawakala au michakato maalum. Wakala mmoja anaweza kuanzia kwa kutafuta ofa bora za ndege, mwingine akahusika na uhifadhi wa hoteli, n.k. Wakala anayeongoza au “wa nyuma” anaweza kuchanganya matokeo haya kuwa ratiba moja sawa kwa mtumiaji.

Mbinu hii ya moduli pia inaruhusu maboresho ya hatua kwa hatua. Kwa mfano, unaweza kuongeza mawakala maalum kwa Mapendekezo ya Chakula au Shughuli za Mtaa na kuboresha ratiba kwa muda.

### Matokeo Yaliyopangwa kwa Muundo

Mifano Mikubwa ya Lugha (LLMs) inaweza kuzalisha matokeo yaliyo na muundo (k.m. JSON) ambayo ni rahisi kwa mawakala au huduma za nyuma kuyasoma na kuyashughulikia. Hii ni muhimu hasa katika muktadha wa mawakala wengi, ambapo tunaweza kutekeleza kazi hizi baada ya kupokea matokeo ya mipango. Rejelea <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogi hii</a> kwa muhtasari wa haraka.

Mfano wa Python hapa chini unaonyesha wakala wa mipango akigawanya lengo kuwa kazi ndogo na kuzalisha mpango uliopangwa kwa muundo:

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

# Mfano wa Kazi Ndogo ya Safari
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # tunataka kugawa kazi kwa wakala

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Ili kuthibitisha na mfano utahitaji kuzalisha tokeni ya ufikiaji wa kibinafsi (PAT) katika mipangilio yako ya GitHub.
    # Tengeneza tokeni yako ya PAT kwa kufuata maelekezo hapa: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Tafsiri ujumbe wa mtumiaji
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

# # Hakikisha maudhui ya jibu ni mfuatano halali wa JSON kabla ya kuipakia
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# kama response_content ni None:
#     inuka ValueError("Maudhui ya jibu si mfuatano halali wa JSON")

# # Chapisha maudhui ya jibu baada ya kuipakia kama JSON
# pprint(json.loads(response_content))

# Thibitisha maudhui ya jibu na mfano wa MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Wakala wa Mipango na Usimamizi wa Mawakala Wengi

Katika mfano huu, Wakala wa Mtaani wa Semantic anapokea ombi la mtumiaji (mfano, "Nahitaji mpango wa hoteli kwa safari yangu.").

Mupango kisha:

* Kupokea Mpango wa Hoteli: Mupango hupokea ujumbe wa mtumiaji na, kulingana na agizo la mfumo (ikiwa ni pamoja na maelezo ya mawakala waliopo), huzalisha mpango wa safari ulio na muundo.
* Orodhesha Wakala na Zana Zao: Usajili wa mawakala una orodha ya mawakala (mfano, kwa ndege, hoteli, kukodisha gari, na shughuli) pamoja na kazi au zana wanazotoa.
* Kutuma Mpango kwa Mawakala Husika: Kulingana na idadi ya kazi ndogo, mupango hutuma ujumbe moja kwa moja kwa wakala maalum (kwa hali za kazi moja) au kuandaa kupitia meneja wa mazungumzo ya kikundi kwa ushirikiano wa mawakala wengi.
* Kufupisha Matokeo: Hatimaye, mupango hufupisha mpango uliotengenezwa kwa uwazi.
Mfano wa msimbo wa Python unaonyesha hatua hizi:

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

# Mfano wa Kazi Ndogo ya Safari

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # tunataka kugawa kazi kwa wakala

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Unda mteja kwa mazingira yaliyopimwa aina

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Eleza ujumbe wa mtumiaji

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

# Hakikisha maudhui ya jibu ni mnyororo wa JSON halali kabla ya kuipakia

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Chapisha maudhui ya jibu baada ya kuipakia kama JSON

pprint(json.loads(response_content))
```

Kinachofuata ni matokeo kutoka kwa msimbo uliotangulia na unaweza kutumia matokeo haya iliyopangwa kwa muundo kupeleka kwa `assigned_agent` na kufupisha mpango wa safari kwa mtumiaji wa mwisho.

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

Mfano wa daftari la maelezo na msimbo uliotangulia upo [hapa](07-autogen.ipynb).

### Mipango ya Kurudia

Baadhi ya kazi zinahitaji kurudia au kupanga upya, ambapo matokeo ya kazi moja ndogo yanaathiri ifuatayo. Kwa mfano, ikiwa wakala atagundua muundo wa data usiotarajiwa wakati wa kuhifadhi ndege, anaweza kuhitaji kubadilisha mkakati kabla ya kuhifadhi hoteli.

Aidha, maoni ya mtumiaji (mfano, mtu kuamua anapendelea ndege ya mapema) yanaweza kusababisha kupanga upya sehemu. Mbinu hii ya kurudia na kusonga mbele huhakikisha suluhisho la mwisho linaendana na vizingiti halisi vya dunia na mabadiliko ya mapendekezo ya mtumiaji.

mfano wa msimbo

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. sawa na msimbo wa awali na kuendelea na historia ya mtumiaji, mpango wa sasa
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
# .. re-panga na tuma kazi kwa maajenti husika
```

Kwa mipango kamili zaidi angalia Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogi</a> kwa utatuzi wa kazi tata.

## Muhtasari

Katika makala hii tumeangalia mfano wa jinsi tunavyoweza kuunda mupango unaoweza kuchagua kwa mabadiliko mawakala waliopo waliotajwa. Matokeo ya Mupango hugawanya kazi na kuagiza mawakala ili kutekelezwa. Inadhaniwa mawakala wana ufikiaji wa kazi/zana zinazohitajika kutekeleza kazi. Zaidi ya mawakala, unaweza kujumuisha mifumo mingine kama tafakari, mfinyanzi, na mazungumzo ya mzunguko wa robin ili kubinafsisha zaidi.

## Rasilimali Zaidi

AutoGen Magentic One - Mfumo wa wakala wengi wa jumla wa kutatua kazi tata na umefanikiwa kupata matokeo mazuri katika vipimo kadhaa vigumu vya wakala. Marejeleo: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Katika utekelezaji huu mratibu huunda mpango maalum wa kazi na kuagiza kazi hizi kwa mawakala waliopo. Zaidi ya kupanga, mratibu pia hutumia mfumo wa kufuatilia maendeleo ya kazi na kupanga upya inapohitajika.

### Una Maswali Zaidi kuhusu Muundo wa Mipango?

Jiunge na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kukutana na wanafunzi wengine, kuhudhuria saa za ofisi na kupata majibu kwa maswali yako kuhusu Wakala wa AI.

## Somo Lililotangulia

[Kuunda Wakala wa AI wa Kuaminika](../06-building-trustworthy-agents/README.md)

## Somo Linalofuata

[Muundo wa Wakala Wengi](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Hati ya kutotegemea**:
Nyaraka hii imetafsiriwa kwa kutumia huduma ya utafsiri wa AI [Co-op Translator](https://github.com/Azure/co-op-translator). Ingawa tunajitahidi kupata usahihi, tafadhali fahamu kwamba tafsiri za kiotomatiki zinaweza kuwa na makosa au upungufu wa usahihi. Nyaraka asili katika lugha yake ya asili inapaswa kuchukuliwa kama chanzo cha mamlaka. Kwa taarifa muhimu, tafsiri ya mtaalamu wa binadamu inashauriwa. Hatuhusiki kwa dhana au tafsiri potovu zinazotokana na matumizi ya tafsiri hii.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->