[![Planning Design Pattern](../../../translated_images/tl/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(I-click ang larawan sa itaas para panoorin ang video ng leksyon na ito)_

# Planning Design

## Panimula

Sasaklawin ng leksyon na ito ang

* Pagpapaliwanag ng malinaw na pangkalahatang layunin at paghahati ng isang komplikadong gawain sa mga kayang pamahalaang bahagi.
* Paggamit ng nakaayos na output para sa mas maaasahan at makinang nababasang mga tugon.
* Paglalapat ng event-driven na pamamaraan upang hawakan ang mga dinamikong gawain at mga hindi inaasahang input.

## Mga Layunin sa Pagkatuto

Pagkatapos tapusin ang leksyon na ito, magkakaroon ka ng pag-unawa tungkol sa:

* Tukuyin at itakda ang isang pangkalahatang layunin para sa isang AI agent, na tinitiyak na malinaw nitong alam kung ano ang kailangang makamit.
* Hatiin ang isang komplikadong gawain sa mga kayang pamahalaang sub-gawain at ayusin ang mga ito sa isang lohikal na pagkakasunod-sunod.
* Lagyan ng kagamitan ang mga agent ng tamang mga tool (hal., mga search tool o mga data analytics tool), magpasya kung kailan at paano sila gagamitin, at hawakan ang mga hindi inaasahang sitwasyon na lumilitaw.
* Suriin ang mga resulta ng sub-gawain, sukatin ang performance, at ulitin ang mga aksyon upang mapabuti ang panghuling output.

## Pagbibigay Kahulugan sa Pangunahing Layunin at Paghahati ng Gawain

![Defining Goals and Tasks](../../../translated_images/tl/defining-goals-tasks.d70439e19e37c47a.webp)

Karamihan sa mga gawain sa totoong mundo ay masyadong komplikado upang harapin sa isang hakbang lamang. Nangangailangan ang isang AI agent ng maikling layunin upang gabayan ang kanyang pagpa-plano at mga aksyon. Halimbawa, isipin ang layunin:

    "Gumawa ng 3-araw na travel itinerary."

Bagama't madali itong sabihin, kailangan pa rin itong linawin. Mas malinaw ang layunin, mas maganda ang pokus ng agent (at ng anumang katuwang na tao) sa pagtamo ng tamang resulta, tulad ng paggawa ng kumpletong itinerary na may mga opsyon sa flight, rekomendasyon sa hotel, at mga suhestiyon sa aktibidad.

### Paghahati ng Gawain

Ang malalaki o masalimuot na gawain ay nagiging mas kayang pamahalaan kapag hinati sa mas maliliit na sub-gawain na nakatuon sa layunin.  
Para sa halimbawang travel itinerary, maari mong hatiin ang layunin sa:

* Pag-book ng Flight
* Pag-book ng Hotel
* Pag-abang ng Sasakyan
* Personalization

Ang bawat sub-gawain ay maaaring asikasuhin ng mga dedikadong agent o proseso. Maaaring may isang agent na dalubhasa sa paghahanap ng pinakamahusay na flight deals, isa naman ang nakatuon sa booking ng hotel, atbp. Ang isang coordinating o “downstream” agent ang magtitipon ng mga resulta na ito upang makabuo ng isang pinag-isang itinerary para sa end user.

Pinapahintulutan din ng modular na pamamaraan na ito ang unti-unting mga pagpapahusay. Halimbawa, maaari kang magdagdag ng mga espesyalisadong agent para sa Food Recommendations o Local Activity Suggestions at pinuhin ang itinerary nang habang panahon.

### Nakaayos na Output

Makakagawa ang Large Language Models (LLMs) ng nakaayos na output (hal., JSON) na mas madaling i-parse at iproseso ng mga downstream agent o serbisyo. Mahalaga ito lalo na sa konteksto ng multi-agent, kung saan maaari nating isakilos ang mga gawain pagkatapos matanggap ang planning output. Tingnan ang <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogpost</a> para sa mabilisang pangkalahatang ideya.

Ipinapakita ng sumusunod na piraso ng Python ang isang simpleng planning agent na naghahati ng layunin sa mga sub-gawain at gumagawa ng nakaayos na plano:

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

# Modelo ng Travel SubTask
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # nais naming i-assign ang gawain sa ahente

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Upang makapag-authenticate gamit ang modelo, kailangan mong gumawa ng personal access token (PAT) sa iyong mga setting sa GitHub.
    # Gumawa ng iyong PAT token sa pagsunod sa mga tagubilin dito: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# I-defina ang mensahe ng user
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

# # Siguraduhing ang sagot na nilalaman ay isang valid na JSON string bago ito i-load
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# kung ang response_content ay None:
#     magtapon ng ValueError("Ang nilalaman ng sagot ay hindi isang valid na JSON string")

# # I-print ang nilalaman ng sagot pagkatapos itong i-load bilang JSON
# pprint(json.loads(response_content))

# I-validate ang nilalaman ng sagot gamit ang MathReasoning model
# TravelPlan.model_validate(json.loads(response_content))
```

### Planning Agent na may Multi-Agent Orchestration

Sa halimbawa na ito, isang Semantic Router Agent ang tumatanggap ng kahilingan ng user (hal., "Kailangan ko ng plano ng hotel para sa aking biyahe.").

Ang planner ay:

* Tumatanggap ng Plano ng Hotel: Kinukuha ng planner ang mensahe ng user at, base sa system prompt (kasama ang detalye ng mga agent na available), gumagawa ng nakaayos na travel plan.  
* Nagtatala ng Mga Agent at Kanilang Mga Tool: Ang rehistro ng agent ay naglalaman ng listahan ng mga agent (hal., para sa flight, hotel, car rental, at mga aktibidad) kasama ang mga function o tool na kanilang inaalok.  
* Inaabot ang Plano sa Mga Nararapat na Agent: Depende sa dami ng sub-gawain, ang planner ay nagse-send ng mensahe direkta sa isang dedikadong agent (para sa sitwasyong single-task) o nakikipagkoordina sa pamamagitan ng group chat manager para sa multi-agent na pagsasama-sama.  
* Nilalagom ang Resulta: Sa huli, nilalagom ng planner ang nabuo na plano para sa kalinawan.  
Ipinapakita ng sumusunod na Python na sample code ang mga hakbang na ito:

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

# Modelo ng SubTask ng Paglalakbay

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # Nais naming i-assign ang gawain sa ahente

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Gumawa ng kliyente gamit ang type-checked na environment variables

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Tukuyin ang mensahe ng user

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

# Tiyakin na ang nilalaman ng tugon ay isang valid na JSON string bago ito i-load

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# I-print ang nilalaman ng tugon pagkatapos itong i-load bilang JSON

pprint(json.loads(response_content))
```

Ang susunod ay ang output mula sa naunang code at maaari mong gamitin ang nakaayos na output na ito upang i-route sa `assigned_agent` at lagumin ang travel plan para sa end user.

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

Isang halimbawa ng notebook na may naunang sample code ay makukuha [dito](07-autogen.ipynb).

### Paulit-ulit na Pagpaplano

Ang ilang gawain ay nangangailangan ng paurong at pasulong na proseso o muling pagpaplano, kung saan ang resulta ng isang sub-gawain ay nakakaapekto sa susunod. Halimbawa, kung matuklasan ng agent ang isang hindi inaasahang format ng data habang nagbo-book ng mga flight, maaaring kailanganin nitong baguhin ang estratehiya bago sumunod sa pag-book ng hotel.

Dagdag pa rito, ang feedback ng user (hal. isang tao na nagpapasya na gusto nila ng mas maagang flight) ay maaaring mag-trigger ng bahagyang muling pagpaplano. Ang dinamikong, paulit-ulit na pamamaraan na ito ay nagsisiguro na ang panghuling solusyon ay naaayon sa mga totoong pagsasaalang-alang at nagbabagong kagustuhan ng user.

hal. sample code

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. pareho ng nakaraang code at ipasa ang kasaysayan ng user, kasalukuyang plano
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
# .. muling magplano at ipadala ang mga gawain sa kani-kanilang mga ahente
```

Para sa mas komprehensibong pagpaplano, tingnan ang Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogpost</a> para sa paglutas ng mas komplikadong mga gawain.

## Buod

Sa artikulong ito tiningnan natin ang halimbawa kung paano tayo makakagawa ng planner na maaaring pabago-bagong pumili ng mga available na agent na na-define. Ang output ng Planner ay naghahati sa mga gawain at nag-aassign ng mga agent upang maipatupad ang mga ito. Pinapalagay na may access ang mga agent sa mga function/tool na kinakailangan upang gawin ang gawain. Bilang karagdagan sa mga agent, maaari mong isama ang iba pang mga pattern tulad ng reflection, summarizer, at round robin chat para higit pang i-customize.

## Karagdagang mga Mapagkukunan

AutoGen Magentic One - Isang Generalist na multi-agent system sa paglutas ng komplikadong gawain at nakamit ang kahanga-hangang resulta sa iba't ibang mahihirap na benchmark ng agentic. Sanggunian: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Sa implementasyong ito, ang orchestrator ay gumagawa ng task-specific plan at nagtatalaga ng mga gawain sa mga available na agent. Bukod sa pagpaplano, gumagamit din ang orchestrator ng tracking mechanism upang subaybayan ang progreso ng gawain at mag-replan kung kinakailangan.

### May Karagdagang Tanong tungkol sa Planning Design Pattern?

Sumali sa [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para makipagkita sa ibang mga nag-aaral, dumalo sa office hours, at masagot ang iyong mga tanong tungkol sa AI Agents.

## Nakaraang Leksiyon

[Building Trustworthy AI Agents](../06-building-trustworthy-agents/README.md)

## Susunod na Leksiyon

[Multi-Agent Design Pattern](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Paunawa**:  
Ang dokumentong ito ay isinalin gamit ang AI na serbisyo sa pagsasalin na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagaman nagsusumikap kami para sa katumpakan, pakatandaan na maaaring may mga pagkakamali o hindi tumpak na bahagi ang awtomatikong pagsasalin. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring na pangunahing sanggunian. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasaling-tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na maaaring magmula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->