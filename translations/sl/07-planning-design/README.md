[![Vzorec načrtovanja](../../../translated_images/sl/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Kliknite zgornjo sliko za ogled videoposnetka te lekcije)_

# Načrtovanje

## Uvod

V tej lekciji bomo obravnavali

* Določitev jasnega splošnega cilja in razčlenitev zapletene naloge na obvladljive naloge.
* Uporabo strukturiranega izhoda za bolj zanesljive in strojno berljive odgovore.
* Uporabo dogodkovno usmerjenega pristopa za obravnavo dinamičnih nalog in nepričakovanih vhodov.

## Cilji učenja

Po zaključku te lekcije boste razumeli:

* Kako prepoznati in določiti splošni cilj za AI agenta, da jasno ve, kaj je treba doseči.
* Kako razčleniti zapleteno nalogo na obvladljive podnaloge in jih organizirati v logičen zaporedje.
* Kako opremiti agente z ustreznimi orodji (npr. orodja za iskanje ali orodja za analitiko podatkov), odločiti, kdaj in kako jih uporabljati ter obravnavati nepričakovane situacije.
* Kako oceniti rezultate podnalog, meriti uspešnost in iterirati ukrepe za izboljšanje končnega izhoda.

## Določitev splošnega cilja in razčlenitev naloge

![Določitev ciljev in nalog](../../../translated_images/sl/defining-goals-tasks.d70439e19e37c47a.webp)

Večina resničnih nalog je preveč zapletena, da bi jih rešili v enem koraku. AI agent potrebuje jedrnat cilj, ki vodi njegovo načrtovanje in ukrepe. Na primer, razmislimo o cilju:

    "Ustvari 3-dnevni potovalni načrt."

Čeprav je enostaven za zapis, še vedno potrebuje izpopolnitev. Bolj jasen kot je cilj, bolj se lahko agent (in morebitni človeški sodelavci) osredotoči na doseganje pravega rezultata, na primer na ustvarjanje celovitega načrta potovanja z možnostmi letov, priporočili hotelov in predlogi aktivnosti.

### Razčlenitev naloge

Velike ali zapletene naloge postanejo bolj obvladljive, če jih razdelimo na manjše, ciljno usmerjene podnaloge.
Za primer potovalnega načrta bi lahko cilj razčlenili na:

* Rezervacija letov
* Rezervacija hotela
* Najem avtomobila
* Personalizacija

Vsako podnalogo lahko nato obvladujejo namenski agenti ali procesi. Eden agent je lahko specializiran za iskanje najboljših ponudb letov, drugi se osredotoča na rezervacije hotelov in tako dalje. Koordinacijski ali "nadaljnji" agent pa lahko združi te rezultate v enoten načrt za končnega uporabnika.

Ta modularni pristop omogoča tudi postopne izboljšave. Na primer, lahko dodate specializirane agente za Priporočila jedi ali Predloge lokalnih aktivnosti in skozi čas izpopolnite načrt.

### Strukturiran izhod

Veliki jezikovni modeli (LLM) lahko ustvarjajo strukturiran izhod (npr. JSON), ki ga je lažje analizirati in obdelati posrednim agentom ali storitvam. To je še posebej koristno v kontekstu večagentnih sistemov, kjer lahko ukrepamo na teh nalogah po prejetju izhoda načrtovanja. Za hitri pregled glejte ta <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blog</a>.

Naslednji Python prikaz prikazuje preprost načrtovalni agent, ki razčleni cilj na podnaloge in ustvari strukturiran načrt:

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

# Model potovalne podnaloge
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # želimo dodeliti nalogo agentu

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Za overjanje z modelom boste morali ustvariti osebni dostopni žeton (PAT) v nastavitvah GitHub.
    # Ustvarite svoj PAT žeton tako, da sledite navodilom tukaj: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Določite uporabniško sporočilo
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

# # Preverite, da je vsebina odgovora veljavna JSON niz preden jo naložite
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# če je response_content None:
#     sproži ValueError("Vsebina odgovora ni veljaven JSON niz")

# # Izpiši vsebino odgovora po nalaganju kot JSON
# pprint(json.loads(response_content))

# Preveri vsebino odgovora z modelom MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Načrtovalni agent z orkestracijo več agentov

V tem primeru prejme Semantic Router Agent uporabniški zahtevek (npr. "Potrebujem načrt hotela za svoje potovanje.").

Načrtovalec nato:

* Prejme načrt hotela: Načrtovalec vzame sporočilo uporabnika in na podlagi sistemskega poziva (vključno z informacijami o razpoložljivih agentih) ustvari strukturiran potovalni načrt.
* Našteje agente in njihova orodja: Registracija agentov vsebuje seznam agentov (npr. za lete, hotele, najem avtomobila in aktivnosti) skupaj s funkcijami ali orodji, ki jih ponujajo.
* Usmeri načrt ustreznim agentom: Glede na število podnalog, načrtovalec sporočilo pošlje neposredno namenskemu agentu (za enonalogne scenarije) ali usklajuje prek upravitelja skupinskega klepeta za sodelovanje več agentov.
* Povzame izid: Na koncu načrtovalec povzame ustvarjeni načrt za jasnost. 
Naslednji Python primer kode ilustrira te korake:

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

# Model potovalne podnaloge

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # želimo dodeliti nalogo agentu

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Ustvari odjemalca z okoljsko spremenljivko, preverjeno s tipom

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Določi uporabnikovo sporočilo

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

# Zagotovi, da je vsebina odgovora veljavna JSON nizek, preden jo naložiš

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Izpiši vsebino odgovora po naložitvi kot JSON

pprint(json.loads(response_content))
```

Spodaj je izhod iz prejšnje kode, ki ga lahko uporabite za usmerjanje k `assigned_agent` in povzemanje potovalnega načrta za končnega uporabnika.

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

Primer zvezka s prejšnjim vzorcem kode je na voljo [tukaj](07-autogen.ipynb).

### Iterativno načrtovanje

Nekatere naloge zahtevajo nazaj-v-naprej ali ponovno načrtovanje, kjer izid ene podnaloge vpliva na naslednjo. Na primer, če agent med rezervacijo letov odkrije nepričakovano obliko podatkov, bo morda moral prilagoditi svojo strategijo, preden nadaljuje z rezervacijami hotelov.

Poleg tega lahko povratne informacije uporabnika (npr. če se človek odloči za zgodnejši let) sprožijo delno ponovno načrtovanje. Ta dinamičen, iterativni pristop zagotavlja, da končna rešitev ustreza resničnim omejitvam in spreminjajočim se željam uporabnikov.

npr. primer kode

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. enako kot prej v kodi in posreduj zgodovino uporabnika, trenutni načrt
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
# .. ponovno načrtuj in pošlji naloge ustreznim agentom
```

Za obsežnejše načrtovanje si oglejte Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blog</a> za reševanje zapletenih nalog.

## Povzetek

V tem članku smo si ogledali primer, kako ustvariti načrtovalca, ki lahko dinamično izbira razpoložljive agente, ki so definirani. Izhod načrtovalca razčleni naloge in dodeli agente, da jih lahko izvedejo. Predpostavljeno je, da imajo agenti dostop do funkcij/orodij, ki so potrebna za izvedbo naloge. Poleg agentov lahko vključite še druge vzorce, kot so refleksija, povzemanje in krožni klepet za dodatno prilagoditev.

## Dodatni viri

AutoGen Magnetic One - Splošni večagentni sistem za reševanje zapletenih nalog, ki je dosegel impresivne rezultate na več zahtevnih agentnih preizkusih. Referenca: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. V tej implementaciji orkestrator ustvarja načrt, specifičen za nalogo, in te naloge delegira razpoložljivim agentom. Poleg načrtovanja orkestrator uporablja tudi mehanizem spremljanja napredka naloge in po potrebi ponovno načrtuje.

### Imate več vprašanj o vzorcu načrtovanja?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kjer boste spoznali druge učence, se udeležili urnikov in dobili odgovore na vprašanja o AI agentih.

## Predhodna lekcija

[Gradnja zaupanja vrednih AI agentov](../06-building-trustworthy-agents/README.md)

## Naslednja lekcija

[Vzorec večagentnega načrtovanja](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Omejitev odgovornosti**:
Ta dokument je bil preveden z uporabo storitve za strojno prevajanje AI [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da lahko avtomatizirani prevodi vsebujejo napake ali netočnosti. Izvirni dokument v njegovem izvirnem jeziku velja za uradni vir. Za kritične informacije priporočamo strokoven prevod, opravljen s strani človeka. Ne odgovarjamo za morebitne nesporazume ali napačne interpretacije, ki izhajajo iz uporabe tega prevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->