[![Planeerimise disainimuster](../../../translated_images/et/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Klõpsa ülaloleval pildil, et vaadata selle tunni videot)_

# Planeerimise disain

## Sissejuhatus

See õppetund hõlmab

* Selge üldeesmärgi määratlemist ja keeruka ülesande jaotamist hallatavateks osadeks.
* Struktureeritud väljundi kasutamist usaldusväärsemate ja masinloetavamate vastuste saamiseks.
* Sündmustepõhise lähenemise kasutamist dünaamiliste ülesannete ja ootamatute sisendite käsitlemiseks.

## Õpieesmärgid

Pärast selle õppetunni läbimist saate aru:

* Määratleda ja seada AI-agendile üldeesmärk, tagades, et see teab selgelt, mida tuleb saavutada.
* Jagada keerukas ülesanne hallatavateks alameesmärkideks ja korraldada need loogilisse järjekorda.
* Varustada agendid õige tööriistavaraga (nt otsingutööriistad või andmeanalüüsi tööriistad), otsustada, millal ja kuidas neid kasutada, ning käsitleda tekkivaid ootamatuid olukordi.
* Hinnata alameesmärkide tulemusi, mõõta sooritusvõimet ja iteratiivselt korrigeerida tegevusi lõpptulemuse parandamiseks.

## Üldeesmärgi määratlemine ja ülesande jaotamine

![Eesmärkide ja ülesannete määratlemine](../../../translated_images/et/defining-goals-tasks.d70439e19e37c47a.webp)

Enamik reaalse maailma ülesandeid on liiga keerulised ühe sammuga lahendamiseks. AI-agent vajab oma planeerimise ja tegevuste juhendamiseks lühikest eesmärki. Näiteks võite seada eesmärgi:

    "Koosta 3-päevane reisiplaan."

Kuigi seda on lihtne sõnastada, vajab see siiski täpsustamist. Mida selgem on eesmärk, seda paremini suudab agent (ja kõik kaasatud inimesed) keskenduda õige tulemuse saavutamisele, näiteks koostada põhjalik reisiplaan koos lennuvalikutega, hotellisoovitustega ja tegevuste ettepanekutega.

### Ülesande jaotamine

Suured või keerukad ülesanded muutuvad hallatavamaks, kui need jagada väiksemateks, eesmärgipõhiseks alameesmärkideks.
Reisiplaani näite puhul võiksite eesmärgi jagada järgmistesse alameesmärkidesse:

* Lendude broneerimine
* Hotellibroneering
* Autorent
* Isikupärastamine

Iga alameesmärgiga saab seejärel tegeleda pühendatud agendid või protsessid. Üks agent võib spetsialiseeruda parimate lennupakkumiste otsimisele, teine keskendub hotellibroneeringutele jne. Koordineeriv või "edasesse torusse" suunatud agent saab seejärel need tulemused lõppkasutajale ühtseks reisikavaks koondada.

See modulaarne lähenemine võimaldab ka järkjärgulisi täiustusi. Näiteks võiksite lisada spetsialiseeritud agente Toidusoovituste või Kohalike tegevuste soovituste jaoks ning aja jooksul reisikava täpsustada.

### Struktureeritud väljund

Suurte keelemudelite (LLM-ide) väljund võib olla struktureeritud (nt JSON), mida on allagentide või teenuste jaoks lihtsam parsida ja töödelda. See on eriti kasulik mitmeagendilise konteksti puhul, kus planeerimisväljundi saab kätte ja seejärel tegutseda. Tutvu selle <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogipostitusega</a> kiire ülevaate saamiseks.

The following Python snippet demonstrates a simple planning agent decomposing a goal into subtasks and generating a structured plan:

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

# Reisi alamülesande mudel
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # me tahame ülesande agendile määrata

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Mudeli autentimiseks peate looma oma GitHubi seadetes isikliku juurdepääsutokeni (PAT).
    # Looge oma PAT-token, järgides juhiseid siin: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Määrake kasutaja sõnum
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

# # Veenduge, et vastuse sisu oleks kehtiv JSON-string enne selle laadimist
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Vastuse sisu ei ole kehtiv JSON-string")

# # Trüki vastuse sisu pärast selle JSON-ina laadimist
# pprint(json.loads(response_content))

# Valideeri vastuse sisu MathReasoning-mudeliga
# TravelPlan.model_validate(json.loads(response_content))
```

### Planeerimisagent mitmeagendilise orkestreerimisega

Selles näites võtab Semantic Router Agent vastu kasutaja päringu (nt "I need a hotel plan for my trip.").

Planeerija teeb seejärel:

* Vastu võtab hotelliplaani: planeerija võtab kasutaja sõnumi ja, lähtudes süsteemi promptist (mis sisaldab saadavalolevate agentide detaile), genereerib struktureeritud reisiplaani.
* Loetleb agendid ja nende tööriistad: agentide registris on nimekiri agentidest (nt lendude, hotellide, autorendi ja tegevuste jaoks) koos nende pakutavate funktsioonide või tööriistadega.
* Suunab plaani vastavatele agentidele: sõltuvalt alameesmärkide arvust saadab planeerija sõnumi kas otse pühendatud agendile (ülesande puhul) või koordineerib mitme agendi koostööd grupivestluse halduri kaudu.
* Kokkuvõtte koostamine: lõpuks võtab planeerija genereeritud plaani kokku selguse huvides.
The following Python code sample illustrates these steps:

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

# Reisi alamülesande mudel

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # soovime ülesande agendile määrata

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Loo klient tüübikontrollitud keskkonnamuutujatega

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Määra kasutaja sõnum

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

# Enne selle laadimist veendu, et vastuse sisu oleks kehtiv JSON-i string

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Prindi vastuse sisu pärast selle laadimist JSON-ina

pprint(json.loads(response_content))
```

What follows is the output from the previous code and you can then use this structured output to route to `assigned_agent` and summarize the travel plan to the end user.

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

Näidis-notebook eelmise koodinäitega on saadaval [siin](07-autogen.ipynb).

### Iteratiivne planeerimine

Mõned ülesanded vajavad edasi-tagasi suhtlust või ümberplaneerimist, kus ühe alameesmärgi tulemus mõjutab järgmist. Näiteks kui agent leiab lennu broneerimisel ootamatu andmeformaadi, võib tal olla vaja enne hotellibroneeringute juurde liikumist oma strateegiat kohandada.

Lisaks võib kasutaja tagasiside (nt inimene otsustab, et eelistab varasemat lendu) esile kutsuda osalise ümberplaneerimise. See dünaamiline, iteratiivne lähenemine tagab, et lõplik lahendus vastab reaalse maailma piirangutele ja kasutaja muutuvatele eelistustele.

nt. näidiskood

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. sama mis eelnevas koodis ja edastada kasutaja ajalugu ja praegune plaan
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
# .. uuesti planeerida ja saata ülesanded vastavatele agentidele
```

Lisateabe saamiseks põhjalikuma planeerimise kohta vaadake Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">blogipostitust</a>, mis käsitleb keerukate ülesannete lahendamist.

## Kokkuvõte

Selles artiklis vaatasime näidet, kuidas luua planeerijat, mis suudab dünaamiliselt valida määratletud saadavalolevaid agente. Planeerija väljund jagab ülesanded osadeks ja määrab agentidele ülesanded, et neid saaks täita. Eeldatakse, et agentidel on juurdepääs ülesande täitmiseks vajalikele funktsioonidele/tööriistadele. Lisaks agentidele võite lisada muid mustreid, nagu refleksioon, kokkuvõtte tegija ja round robin chat, et veelgi kohandada.

## Täiendavad ressursid

AutoGen Magentic One — üldotstarbeline mitmeagendiline süsteem keerukate ülesannete lahendamiseks, mis on saavutanud muljetavaldavaid tulemusi mitmetel väljakutsuvatel agendipõhistel võrdlusalustel. Viide: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Selles implementeeringus loob orkestreerija ülesandepõhise plaani ja delegeerib need ülesanded saadavalolevatele agentidele. Planeerimise kõrval kasutab orkestreerija ka jälgimismehhanismi ülesande edenemise jälgimiseks ning vajadusel uuesti planeerimiseks.

### Kas sul on veel küsimusi planeerimisdisainimustri kohta?

Liitu [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kogukonnaga, kohtuge teiste õppuritega, osalege konsultatsioonitundides ja saate vastused oma AI-agentide küsimustele.

## Eelmine õppetund

[Usaldusväärsete AI-agentide loomine](../06-building-trustworthy-agents/README.md)

## Järgmine õppetund

[Mitmeagendiline disainimuster](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Vastutusest loobumine:
See dokument on tõlgitud tehisintellekti tõlketeenuse [Co-op Translator](https://github.com/Azure/co-op-translator) abil. Kuigi püüame tagada täpsust, tuleb arvestada, et automaatsed tõlked võivad sisaldada vigu või ebatäpsusi. Originaaldokument selle algkeeles tuleks pidada autoriteetseks allikaks. Olulise teabe puhul soovitatakse kasutada professionaalset inimtõlget. Me ei vastuta käesoleva tõlke kasutamisest tulenevate arusaamatuste ega valesti tõlgendamise eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->