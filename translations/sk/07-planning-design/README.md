[![Plánovací návrhový vzor](../../../translated_images/sk/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Kliknite na obrázok vyššie pre zobrazenie videa tejto lekcie)_

# Plánovací návrh

## Úvod

Táto lekcia pokryje

* Definovanie jasného celkového cieľa a rozdelenie zložitej úlohy na spravovateľné úlohy.
* Využitie štruktúrovaného výstupu pre spoľahlivejšie a strojovo čitateľné odpovede.
* Použitie prístupu riadeného udalosťami na zvládanie dynamických úloh a neočakávaných vstupov.

## Ciele učenia

Po dokončení tejto lekcie budete mať pochopenie o:

* Identifikovať a stanoviť celkový cieľ pre AI agenta, zabezpečiť, aby jasne vedel, čo sa má dosiahnuť.
* Rozložiť zložitú úlohu na spravovateľné podúlohy a usporiadať ich do logickej postupnosti.
* Vybaviť agentov správnymi nástrojmi (napr. vyhľadávacie nástroje alebo nástroje na analýzu dát), rozhodnúť, kedy a ako sa používajú, a zvládať neočakávané situácie.
* Vyhodnotiť výsledky podúloh, merať výkonnosť a iterovať akcie na zlepšenie konečného výstupu.

## Definovanie celkového cieľa a rozdelenie úlohy

![Definovanie cieľov a úloh](../../../translated_images/sk/defining-goals-tasks.d70439e19e37c47a.webp)

Väčšina úloh v reálnom svete je príliš zložitá na riešenie v jednom kroku. AI agent potrebuje stručný cieľ, ktorý bude riadiť jeho plánovanie a činnosti. Napríklad si predstavte cieľ:

    "Vytvoriť trojdňový cestovný itinerár."

Aj keď je jednoduché to vyjadriť, stále to potrebuje upresnenie. Čím jasnejší cieľ, tým lepšie sa agent (a akýkoľvek ľudský spolupracovník) môže sústrediť na dosiahnutie správneho výsledku, ako je vytvorenie komplexného itinerára s možnosťami letov, odporúčaniami hotelov a návrhmi aktivít.

### Rozklad úlohy

Veľké alebo zložité úlohy sa stávajú spravovateľnejšími po ich rozdelení na menšie, na cieľ orientované podúlohy.
Pre príklad cestovného itinerára môžete cieľ rozložiť na:

* Rezervácia letu
* Rezervácia hotela
* Prenájom auta
* Personalizácia

Každá podúloha môže byť riešená samostatnými agentmi alebo procesmi. Jeden agent sa môže špecializovať na vyhľadávanie najlepších ponúk letov, iný sa sústredí na rezervácie hotelov a tak ďalej. Koordinujúci alebo „downstream“ agent potom môže tieto výsledky skompilovať do jedného súdržného itinerára pre koncového používateľa.

Tento modulárny prístup tiež umožňuje postupné vylepšenia. Napríklad môžete pridať špecializovaných agentov pre odporúčania jedál alebo miestnych aktivít a itinerár priebežne zdokonaľovať.

### Štruktúrovaný výstup

Jazykové modely veľkého rozsahu (LLM) môžu generovať štruktúrovaný výstup (napr. JSON), ktorý je jednoduchší na spracovanie downstream agentmi alebo službami. To je obzvlášť užitočné v kontexte viacerých agentov, kde môžeme tieto úlohy vykonať po prijatí plánovacieho výstupu. Pozrite si tento <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogový príspevok</a> pre rýchly prehľad.

Nasledujúci úryvok Pythonu demonštruje jednoduchého plánovacieho agenta, ktorý rozkladá cieľ na podúlohy a generuje štruktúrovaný plán:

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

# Model podúlohy cestovania
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # chceme priradiť úlohu agentovi

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Na autentifikáciu s modelom budete potrebovať vygenerovať osobný prístupový token (PAT) vo vašich nastaveniach GitHubu.
    # Vytvorte si svoj PAT token podľa pokynov tu: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definujte používateľskú správu
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

# # Uistite sa, že obsah odpovede je platný JSON reťazec pred jeho načítaním
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# ak je response_content None:
#     vyvolajte ValueError("Obsah odpovede nie je platný JSON reťazec")

# # Vytlačte obsah odpovede po načítaní ako JSON
# pprint(json.loads(response_content))

# Overte obsah odpovede pomocou modelu MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Plánovací agent s orchestráciou viacerých agentov

V tomto príklade Semantic Router Agent prijíma požiadavku používateľa (napr. "Potrebujem plán hotela na moju cestu").

Plánovač potom:

* Prijme plán hotela: Plánovač prevezme správu používateľa a na základe systémového promptu (vrátane dostupných detailov agentov) generuje štruktúrovaný cestovný plán.
* Vypíše agentov a ich nástroje: Register agentov obsahuje zoznam agentov (napr. pre lety, hotely, prenájom áut a aktivity) spolu s funkciami alebo nástrojmi, ktoré ponúkajú.
* Smeruje plán k príslušným agentom: V závislosti od počtu podúloh plánovač buď odošle správu priamo určenému agentovi (pri jedinej úlohe), alebo koordinuje cez správcu skupinového chatu pre spoluprácu viacerých agentov.
* Zhrnie výsledok: Nakoniec plánovač zhrnie vygenerovaný plán pre prehľadnosť.
Nasledujúci príklad kódu v Pythone ilustruje tieto kroky:

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

# Model cestovnej podúlohy

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # chceme priradiť úlohu agentovi

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Vytvorte klienta s typovo overenými premennými prostredia

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definujte správu používateľa

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

# Zabezpečte, aby bol obsah odpovede platným reťazcom JSON pred jeho načítaním

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Vytlačte obsah odpovede po načítaní ako JSON

pprint(json.loads(response_content))
```

Nasleduje výstup z predchádzajúceho kódu a potom môžete použiť tento štruktúrovaný výstup na smerovanie k `assigned_agent` a sumarizáciu cestovného plánu pre koncového používateľa.

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

Príklad notebooku s predchádzajúcim kódom je dostupný [tu](07-autogen.ipynb).

### Iteratívne plánovanie

Niektoré úlohy vyžadujú vzájomnú spätnú väzbu alebo preplánovanie, kde výsledok jednej podúlohy ovplyvňuje ďalšiu. Napríklad, ak agent zistí neočakávaný formát údajov počas rezervácie leteniek, môže potrebovať prispôsobiť svoju stratégiu predtým, než prejde k rezervácii hotela.

Okrem toho používateľská spätná väzba (napr. keď si človek želá skorší let) môže spustiť čiastočné preplánovanie. Tento dynamický, iteratívny prístup zabezpečuje, že konečné riešenie bude súladné s reálnymi obmedzeniami a vyvíjajúcimi sa preferenciami používateľa.

napr. ukážkový kód

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. rovnaké ako predchádzajúci kód a pokračovať v histórii používateľa, aktuálnom pláne
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
# .. preplánovať a poslať úlohy príslušným agentom
```

Pre komplexnejšie plánovanie si pozrite Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogový príspevok</a> o riešení zložitých úloh.

## Zhrnutie

V tomto článku sme si ukázali príklad, ako môžeme vytvoriť plánovač, ktorý dynamicky vyberá dostupných definovaných agentov. Výstup plánovača rozkladá úlohy a priraďuje agentov, aby mohli byť vykonané. Predpokladá sa, že agenti majú prístup k funkciám/nástrojom, ktoré sú potrebné na vykonanie úlohy. Okrem agentov môžete zahrnúť aj ďalšie vzory, ako je reflexia, sumarizátor a round robin chat, na ďalšie prispôsobenie.

## Ďalšie zdroje

AutoGen Magentic One – všeobecný systém viacerých agentov na riešenie zložitých úloh, ktorý dosiahol pôsobivé výsledky na viacerých náročných benchmarkoch. Referencia: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. V tejto implementácii orchestrátor vytvára plán špecifický pre úlohu a deleguje tieto úlohy dostupným agentom. Okrem plánovania orchestrátor tiež využíva sledovací mechanizmus na monitorovanie priebehu úlohy a podľa potreby preplánováva.

### Máte ďalšie otázky o Plánovacom návrhovom vzore?

Pridajte sa na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) a stretnite sa s ďalšími študentmi, zúčastnite sa konzultačných hodín a získajte odpovede na vaše otázky o AI agentech.

## Predchádzajúca lekcia

[Budovanie dôveryhodných AI agentov](../06-building-trustworthy-agents/README.md)

## Nasledujúca lekcia

[Návrhový vzor viacerých agentov](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zrieknutie sa zodpovednosti**:  
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Napriek snahe o presnosť si prosím uvedomte, že automatizované preklady môžu obsahovať chyby alebo nepresnosti. Pôvodný dokument v jeho rodnom jazyku by mal byť považovaný za autoritatívny zdroj. Pre dôležité informácie sa odporúča profesionálny ľudský preklad. Nie sme zodpovední za akékoľvek nedorozumenia alebo chybné interpretácie vyplývajúce z použitia tohto prekladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->