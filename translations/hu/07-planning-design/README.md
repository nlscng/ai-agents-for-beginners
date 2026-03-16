[![Tervezési minta](../../../translated_images/hu/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Kattintson a fenti képre a lecke videójának megtekintéséhez)_

# Tervezési minta

## Bevezetés

Ez a lecke a következő témákat fedi:

* Egyértelmű, átfogó cél meghatározása és egy összetett feladat lebontása kezelhető részfeladatokra.
* Strukturált kimenet használata a megbízhatóbb és géppel olvashatóbb válaszokhoz.
* Eseményvezérelt megközelítés alkalmazása dinamikus feladatok és váratlan bemenetek kezelésére.

## Tanulási célok

A lecke elvégzése után a következőket fogja érteni:

* Megfogalmazni és meghatározni egy átfogó célt egy MI-ügynök számára, biztosítva, hogy pontosan tudja, mit kell elérnie.
* Egy összetett feladat lebontása kezelhető részfeladatokra és azok logikus sorrendbe rendezése.
* Az ügynökök felszerelése a megfelelő eszközökkel (pl. keresőeszközök vagy adat-analitikai eszközök), meghatározva, mikor és hogyan használják őket, valamint a felmerülő váratlan helyzetek kezelése.
* A részfeladatok eredményeinek értékelése, a teljesítmény mérése és az intézkedések iterálása a végső kimenet javítása érdekében.

## Átfogó cél meghatározása és egy feladat lebontása

![Célok és feladatok meghatározása](../../../translated_images/hu/defining-goals-tasks.d70439e19e37c47a.webp)

A legtöbb valós feladat túl összetett ahhoz, hogy egyetlen lépésben oldjuk meg. Egy MI-ügynöknek tömör célt kell kapnia, ami irányítja a tervezését és a cselekvéseit. Például vegyük a következő célt:

    "Készíts egy 3 napos utazási útitervet."

Habár egyszerű megfogalmazni, mégis finomításra szorul. Minél világosabb a cél, annál jobban tud az ügynök (és az emberi közreműködők) a megfelelő eredmény elérésére összpontosítani, például egy átfogó útiterv létrehozására járatokkal, szállásajánlásokkal és programjavaslatokkal.

### Feladatlebontás

A nagy vagy bonyolult feladatok kezelhetőbbé válnak, ha kisebb, célorientált részfeladatokra bontjuk őket.
Az útiterv példájánál a célt a következőkre bonthatja:

* Járatfoglalás
* Szállásfoglalás
* Autóbérlés
* Személyre szabás

Ezeket a részfeladatokat dedikált ügynökök vagy folyamatok kezelhetik. Az egyik ügynök például a legjobb járatkedvezmények keresésére specializálódhat, egy másik a szállásfoglalásokra, és így tovább. Egy koordináló vagy „downstream” ügynök ezután összeállíthatja ezeket az eredményeket egy koherens útitervvé a végfelhasználó számára.

Ez a moduláris megközelítés lehetővé teszi a fokozatos fejlesztéseket is. Például hozzáadhat specializált ügynököket ételajánlásokhoz vagy helyi programjavaslatokhoz, és idővel tovább finomíthatja az útitervet.

### Strukturált kimenet

A nagy nyelvi modellek (LLM-ek) strukturált kimenetet (pl. JSON) képesek előállítani, amelyet a downstream ügynökök vagy szolgáltatások könnyebben fel tudnak dolgozni és értelmezni. Ez különösen hasznos több-ügynökös környezetben, ahol a tervezési kimenet beérkezése után végrehajthatjuk a feladatokat. Tekintse meg ezt a <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogbejegyzést</a> rövid áttekintésért.

Az alábbi Python kivonat egy egyszerű tervezőügynököt mutat be, amely egy célt bont részfeladatokra és strukturált tervet generál:

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

# Utazási alfeladat modell
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # a feladatot az ügynöknek szeretnénk kiosztani

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # A modell hitelesítéséhez létre kell hoznia egy személyes hozzáférési tokent (PAT) a GitHub beállításaiban.
    # Hozza létre a PAT tokenjét a következő utasítások szerint: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Határozza meg a felhasználói üzenetet
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

# # Győződjön meg róla, hogy a válasz tartalma érvényes JSON-szöveg, mielőtt betöltené
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Response content is not a valid JSON string")

# # Írja ki a válasz tartalmát, miután JSON-ként betöltötte
# pprint(json.loads(response_content))

# Ellenőrizze a válasz tartalmát a MathReasoning modellel
# TravelPlan.model_validate(json.loads(response_content))
```

### Tervezőügynök többügynökös orkestrációval

Ebben a példában egy Semantic Router Agent kap egy felhasználói kérést (pl. "Szükségem van egy szállástervre az utazásomhoz.").

A tervező ezután:

* Megkapja a szállástervet: A tervező fogadja a felhasználó üzenetét, és egy rendszerprompt alapján (beleértve az elérhető ügynökök részleteit) strukturált utazási tervet generál.
* Felsorolja az ügynököket és eszközeiket: Az ügynökregiszter tartalmazza az ügynökök listáját (pl. járat, szállás, autóbérlés és programok) és az általuk kínált funkciókat vagy eszközöket.
* A terv továbbítása a megfelelő ügynökökhöz: A részfeladatok számától függően a tervező vagy közvetlenül egy dedikált ügynökhöz küldi az üzenetet (egyfeladatos esetekben), vagy többügynökös együttműködéshez egy csoportos chatkezelőn keresztül koordinál.
* Összegzi az eredményt: Végül a tervező összefoglalja a létrehozott tervet az érthetőség érdekében.
Az alábbi Python kódminta illusztrálja ezeket a lépéseket:

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

# Utazási alfeladat-modell

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # szeretnénk a feladatot az ügynöknek kiosztani

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Hozza létre a klienst típusellenőrzött környezeti változókkal

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Határozza meg a felhasználói üzenetet

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

# Győződjön meg arról, hogy a válasz tartalma érvényes JSON-karakterlánc, mielőtt betöltené

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Írja ki a válasz tartalmát a JSON-ként történő betöltés után

pprint(json.loads(response_content))
```

A következő a fenti kód kimenete, és ezt a strukturált kimenetet használhatja arra, hogy továbbítsa a `assigned_agent`-hez és összefoglalja az útitervet a végfelhasználónak.

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

A fenti kódmintát tartalmazó példanapló elérhető [itt](07-autogen.ipynb).

### Iteratív tervezés

Egyes feladatok igényelnek oda-vissza kommunikációt vagy újratervezést, ahol az egyik részfeladat eredménye befolyásolja a következőt. Például ha az ügynök egy váratlan adatformátumot fedez fel a járatfoglalás közben, előfordulhat, hogy módosítania kell a stratégiáját, mielőtt tovább lépne a szállásfoglalásokra.

Emellett a felhasználói visszajelzés (pl. amikor egy ember úgy dönt, hogy korábbi járatot preferál) részleges újratervezést válthat ki. Ez a dinamikus, iteratív megközelítés biztosítja, hogy a végső megoldás igazodjon a valós korlátokhoz és a változó felhasználói preferenciákhoz.

példakód

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. ugyanaz, mint az előző kód, és továbbítani a felhasználói előzményeket és az aktuális tervet
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
# .. újratervezni és elküldeni a feladatokat a megfelelő ügynököknek
```

További, átfogóbb tervezéshez tekintse meg a Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">blogbejegyzését</a> az összetett feladatok megoldásáról.

## Összefoglalás

Ebben a cikkben megvizsgáltunk egy példát arra, hogyan hozhatunk létre egy tervezőt, amely dinamikusan képes kiválasztani a definiált elérhető ügynököket. A tervező kimenete lebontja a feladatokat és hozzárendeli az ügynököket, hogy azokat végre lehessen hajtani. Feltételezzük, hogy az ügynökök hozzáférnek a feladat végrehajtásához szükséges funkciókhoz/eszközökhöz. Az ügynökök mellett további mintákat is bevonhat, mint például reflektálás, összefoglaló és körkörös chat a további testreszabáshoz.

## További források

AutoGen Magentic One - A Generalist multi-agent system for solving complex tasks and has achieved impressive results on multiple challenging agentic benchmarks. Reference: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Ebben a megvalósításban az orchestrator létrehozza a feladatra szabott tervet és delegálja ezeket a feladatokat az elérhető ügynököknek. A tervezés mellett az orchestrator nyomkövető mechanizmust is alkalmaz a feladat előrehaladásának figyelésére és szükség szerint újratervezésre.

### Van még kérdése a tervezési mintával kapcsolatban?

Csatlakozzon a [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)-hoz, hogy találkozzon más tanulókkal, részt vegyen konzultációs órákon és választ kapjon az AI ügynökökkel kapcsolatos kérdéseire.

## Előző lecke

[Megbízható MI-ügynökök építése](../06-building-trustworthy-agents/README.md)

## Következő lecke

[Többügynökös tervezési minta](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Felelősségkizárás:
Ezt a dokumentumot a Co-op Translator (https://github.com/Azure/co-op-translator) mesterséges intelligencia alapú fordító szolgáltatásával fordítottuk. Bár törekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti dokumentum az anyanyelvén tekintendő irányadónak. Fontos információk esetén professzionális, emberi fordítást javasolunk. Nem vállalunk felelősséget a jelen fordítás használatából eredő félreértésekért vagy félreértelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->