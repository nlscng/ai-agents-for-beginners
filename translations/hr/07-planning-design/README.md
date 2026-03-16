[![Obrazac dizajna planiranja](../../../translated_images/hr/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Kliknite sliku iznad za pregled videa ove lekcije)_

# Dizajn planiranja

## Uvod

Ova lekcija će obuhvatiti

* Definiranje jasnog glavnog cilja i razbijanje kompleksnog zadatka na upravljive zadatke.
* Korištenje strukturiranog izlaza za pouzdanije i strojno čitljive odgovore.
* Primjenu događajno vođenog pristupa za rukovanje dinamičnim zadacima i neočekivanim ulazima.

## Ciljevi učenja

Nakon završetka ove lekcije razumjet ćete:

* Identificirati i postaviti opći cilj za AI agenta, osiguravajući da jasno zna što treba postići.
* Decomponirati složen zadatak na upravljive podzadatke i organizirati ih u logičan slijed.
* Opremljivati agente odgovarajućim alatima (npr. alati za pretraživanje ili alati za analizu podataka), odlučiti kada i kako se koriste te rukovati neočekivanim situacijama koje se pojave.
* Procijeniti rezultate podzadataka, mjeriti izvedbu i iterirati radnje kako bi se poboljšao konačni ishod.

## Definiranje općeg cilja i razbijanje zadatka

![Definiranje ciljeva i zadataka](../../../translated_images/hr/defining-goals-tasks.d70439e19e37c47a.webp)

Većina zadataka u stvarnom svijetu je previše složena za rješavanje u jednom koraku. AI agent treba sažeti cilj koji vodi njegovo planiranje i akcije. Na primjer, razmotrite cilj:

    "Izradi 3-dnevni plan putovanja."

Iako je jednostavno izreći, potrebno ga je dodatno razraditi. Što je cilj jasniji, to se agent (i bilo koji ljudski suradnici) može bolje usredotočiti na postizanje ispravnog rezultata, poput izrade sveobuhvatnog itinerera s opcijama letova, preporukama hotela i prijedlozima aktivnosti.

### Razbijanje zadatka

Veliki ili složeni zadaci postaju upravljiviji kad se podijele na manje, na cilj usmjerene podzadatke.
Za primjer plana putovanja, cilj možete razložiti na:

* Rezervacija leta
* Rezervacija hotela
* Najam automobila
* Personalizacija

Svaki podzadatak tada može rješavati poseban agent ili procesi. Jedan agent može biti specijaliziran za pronalaženje najboljih ponuda letova, drugi se fokusira na rezervacije hotela, i tako dalje. Koordinirajući ili "downstream" agent može zatim objediniti ove rezultate u jedan kohezivan itinerer za krajnjeg korisnika.

Ovakav modularan pristup također omogućuje postupna poboljšanja. Na primjer, možete dodati specijalizirane agente za preporuke hrane ili prijedloge lokalnih aktivnosti i s vremenom doraditi itinerer.

### Strukturirani izlaz

Veliki jezični modeli (LLM-ovi) mogu generirati strukturirani izlaz (npr. JSON) koji je lakše za parsirati i obraditi od strane downstream agenata ili servisa. Ovo je posebno korisno u kontekstu više agenata, gdje možemo izvršavati ove zadatke nakon što primimo planiranje. Pogledajte ovu <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">objavu na blogu</a> za kratak pregled.

Sljedeći Python isječak demonstrira jednostavan agent za planiranje koji razlaže cilj na podzadatke i generira strukturirani plan:

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

# Model podzadatka za putovanje
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # želimo dodijeliti zadatak agentu

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Za autentifikaciju s modelom morat ćete generirati osobni pristupni token (PAT) u postavkama vašeg GitHub računa.
    # Stvorite svoj PAT token slijedeći upute ovdje: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definirajte poruku korisnika
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

# # Osigurajte da je sadržaj odgovora valjani JSON niz prije učitavanja
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Sadržaj odgovora nije valjani JSON niz")

# # Ispišite sadržaj odgovora nakon učitavanja kao JSON
# pprint(json.loads(response_content))

# Provjerite sadržaj odgovora pomoću modela MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Agent za planiranje s orkestracijom više agenata

U ovom primjeru, Semantic Router Agent prima korisnički zahtjev (npr. "Trebam plan hotela za svoje putovanje.").

Planer zatim:

* Prima plan hotela: planer uzima poruku korisnika i, na temelju sistemskog prompta (uključujući dostupne detalje agenata), generira strukturirani plan putovanja.
* Navodi agente i njihove alate: registar agenata sadrži popis agenata (npr. za letove, hotele, najam automobila i aktivnosti) zajedno s funkcijama ili alatima koje nude.
* Usmjerava plan odgovarajućim agentima: ovisno o broju podzadataka, planer ili šalje poruku izravno posvećenom agentu (za scenarije s jednim zadatkom), ili koordinira putem upravitelja grupnog chata za suradnju više agenata.
* Sažima ishod: na kraju, planer sažima generirani plan radi jasnoće.
Sljedeći Python primjer koda ilustrira ove korake:

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

# Model podzadatka putovanja

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # želimo dodijeliti zadatak agentu

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Kreirajte klijenta s varijablama okruženja provjerenima po tipu

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definirajte poruku korisnika

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

# Osigurajte da je sadržaj odgovora valjan JSON niz prije učitavanja

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Ispišite sadržaj odgovora nakon što ga učitate kao JSON

pprint(json.loads(response_content))
```

Ispod je izlaz iz prethodnog koda i možete potom upotrijebiti ovaj strukturirani izlaz za usmjeravanje prema `assigned_agent` i sažimanje plana putovanja za krajnjeg korisnika.

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

Primjer bilježnice s prethodnim primjerom koda dostupan je [ovdje](07-autogen.ipynb).

### Iterativno planiranje

Neki zadaci zahtijevaju povratne iteracije ili ponovno planiranje, gdje ishod jednog podzadatka utječe na sljedeći. Na primjer, ako agent otkrije neočekivani format podataka prilikom rezervacije letova, možda će trebati prilagoditi svoju strategiju prije nego što prijeđe na rezervacije hotela.

Dodatno, povratne informacije korisnika (npr. čovjek koji odluči da preferira raniji let) mogu pokrenuti djelomično ponovno planiranje. Ovaj dinamičan, iterativni pristup osigurava da se konačno rješenje uskladi s ograničenjima iz stvarnog svijeta i evoluirajućim preferencijama korisnika.

npr. primjer koda

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. isto kao prethodni kod i proslijedi povijest korisnika, trenutni plan
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
# .. ponovno planiraj i pošalji zadatke odgovarajućim agentima
```

Za sveobuhvatnije planiranje pogledajte Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">objavu na blogu</a> za rješavanje složenih zadataka.

## Sažetak

U ovom članku pogledali smo primjer kako možemo stvoriti planer koji može dinamički odabrati dostupne agente definirane u sustavu. Izlaz Planera razlaže zadatke i dodjeljuje agente kako bi se mogli izvršiti. Pretpostavlja se da agenti imaju pristup funkcijama/alatima potrebnim za obavljanje zadatka. Osim agenata, možete uključiti i druge obrasce poput refleksije, sažimača i rotirajućeg chata za daljnju prilagodbu.

## Dodatni resursi

AutoGen Magentic One - A Generalist multi-agent system for solving complex tasks and has achieved impressive results on multiple challenging agentic benchmarks. Reference: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. U ovoj implementaciji orkestrator stvara zadatku specifičan plan i delegira te zadatke dostupnim agentima. Osim planiranja, orkestrator također koristi mehanizam praćenja za nadzor napretka zadatka i ponovno planira po potrebi.

### Imate li dodatna pitanja o obrascu dizajna planiranja?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kako biste se susreli s drugim polaznicima, sudjelovali na radnim satima konzultacija i dobili odgovore na pitanja o vašim AI agentima.

## Prethodna lekcija

[Izgradnja pouzdanih AI agenata](../06-building-trustworthy-agents/README.md)

## Sljedeća lekcija

[Obrazac dizajna za više agenata](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Odricanje odgovornosti**:
Ovaj je dokument preveden pomoću AI usluge za prevođenje [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo biti točni, imajte na umu da automatizirani prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za važne informacije preporučuje se profesionalni ljudski prijevod. Ne odgovaramo za bilo kakve nesporazume ili pogrešna tumačenja koja nastanu korištenjem ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->