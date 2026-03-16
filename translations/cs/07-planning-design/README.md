[![Planning Design Pattern](../../../translated_images/cs/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Klikněte na obrázek výše pro zhlédnutí videa této lekce)_

# Návrh Plánování

## Úvod

Tato lekce pokryje

* Definování jasného celkového cíle a rozdělení složité úlohy na zvládnutelné úkoly.
* Využití strukturovaného výstupu pro spolehlivější a strojově čitelnou odpověď.
* Použití přístupu založeného na událostech pro zvládání dynamických úkolů a neočekávaných vstupů.

## Cíle učení

Po dokončení této lekce budete mít znalost o:

* Identifikaci a nastavení celkového cíle pro AI agenta, aby jasně věděl, čeho je třeba dosáhnout.
* Rozložení složité úlohy do zvládnutelných podúkolů a jejich uspořádání do logické posloupnosti.
* Vybavení agentů správnými nástroji (např. vyhledávacími nástroji nebo nástroji pro analýzu dat), rozhodování, kdy a jak je použít, a zvládání neočekávaných situací, které nastanou.
* Hodnocení výsledků podúkolů, měření výkonu a iteraci akcí k vylepšení konečného výstupu.

## Definování celkového cíle a rozložení úkolu

![Definování cílů a úkolů](../../../translated_images/cs/defining-goals-tasks.d70439e19e37c47a.webp)

Většina reálných úkolů je příliš složitá na to, aby je bylo možné řešit jedním krokem. AI agent potřebuje stručný cíl, který jej bude vést při plánování a jednání. Například zvažte cíl:

    "Vytvořit itinerář cesty na 3 dny."

I když je snadné jej formulovat, potřebuje ještě upřesnění. Čím jasnější cíl, tím lépe se agent (a jakýkoli lidský spolupracovník) může zaměřit na dosažení správného výsledku, například vytvoření komplexního itineráře zahrnujícího letenky, doporučení hotelů a návrhy aktivit.

### Rozklad úkolu

Velké nebo složité úkoly se stávají zvládnutelnějšími, pokud je rozdělíme na menší, na cíl zaměřené podúkoly.
V případě itineráře cesty můžete cíl rozdělit na:

* Rezervace letenek
* Rezervace hotelu
* Pronájem auta
* Personalizace

Každý podúkol pak může řešit vyhrazený agent nebo proces. Jeden agent může být specialista na vyhledávání nejvýhodnějších letů, jiný se zaměřuje na rezervace hotelů a tak dále. Koordinující nebo „následující“ agent může pak tyto výsledky sestavit do jednotného itineráře pro uživatele.

Tento modulární přístup také umožňuje postupné vylepšování. Například můžete přidat specializované agenty pro doporučení jídla nebo místních aktivit a itinerář časem zdokonalovat.

### Strukturovaný výstup

Velké jazykové modely (LLM) mohou generovat strukturovaný výstup (např. JSON), který je jednodušší pro další agenty nebo služby k analýze a zpracování. To je obzvláště užitečné v multi-agentním kontextu, kde můžeme akce provádět po přijetí plánovacího výstupu. Podívejte se na tento <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogový příspěvek</a> pro rychlý přehled.

Následující ukázka v Pythonu demonstruje jednoduchého plánovacího agenta rozkládajícího cíl na podúkoly a generujícího strukturovaný plán:

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

# Model podúkolu cesty
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # chceme přiřadit úkol agentovi

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # K ověření pomocí modelu budete muset v nastavení GitHubu vygenerovat osobní přístupový token (PAT).
    # Vytvořte svůj PAT token podle pokynů zde: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definujte zprávu uživatele
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

# # Zajistěte, že obsah odpovědi je platný JSON řetězec před jeho načtením
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Obsah odpovědi není platný JSON řetězec")

# # Vytiskněte obsah odpovědi po načtení jako JSON
# pprint(json.loads(response_content))

# Ověřte obsah odpovědi modelem MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Plánovací agent s multi-agentním orchestrací

V tomto příkladu agent Semantic Router přijímá uživatelskou žádost (např. „Potřebuji plán hotelu pro svou cestu.“).

Plánovač pak:

* Přijímá Plán Hotelu: Plánovač vezme uživatelovu zprávu a na základě systémového promptu (včetně detailů dostupných agentů) vygeneruje strukturovaný cestovní plán.
* Vypisuje agenty a jejich nástroje: Registr agentů obsahuje seznam agentů (např. pro lety, hotel, pronájem auta a aktivity) spolu s funkcemi či nástroji, které nabízí.
* Směruje plán k příslušným agentům: Podle počtu podúkolů buď posílá zprávu přímo vyhrazenému agentu (pro úlohy s jedním úkolem), nebo koordinuje přes správce skupinového chatu pro spolupráci více agentů.
* Shrnuje výsledek: Nakonec plánovač shrne vygenerovaný plán pro přehlednost.
Následující ukázka kódu v Pythonu ilustruje tyto kroky:

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

# Model podúkolu cesty

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # chceme přiřadit úkol agentovi

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Vytvořte klienta s typově kontrolovanými proměnnými prostředí

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definujte uživatelskou zprávu

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

# Zajistěte, aby obsah odpovědi byl platný řetězec JSON před jeho načtením

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Vytiskněte obsah odpovědi po načtení jako JSON

pprint(json.loads(response_content))
```

Následuje výstup z předchozího kódu a můžete tento strukturovaný výstup využít k odeslání do `assigned_agent` a shrnutí cestovního plánu koncovému uživateli.

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

Příklad notebooku s předchozím ukázkovým kódem naleznete [zde](07-autogen.ipynb).

### Iterativní plánování

Některé úkoly vyžadují zpětnou vazbu nebo přeplánování, kdy výsledek jednoho podúkolu ovlivňuje další. Například pokud agent objeví neočekávaný formát dat při rezervaci letenek, může být potřeba upravit strategii před pokračováním k rezervaci hotelu.

Navíc zpětná vazba uživatele (například rozhodnutí člověka, že dává přednost dřívějšímu letu) může vyvolat částečné přeplánování. Tento dynamický, iterativní přístup zajišťuje, že konečné řešení odpovídá reálným omezením a měnícím se preferencím uživatelů.

např. ukázkový kód

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. stejně jako předchozí kód a předat historii uživatele, aktuální plán
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
# .. přeplánovat a poslat úkoly příslušným agentům
```

Pro komplexnější plánování si prohlédněte Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">blogový příspěvek</a> zaměřený na řešení složitých úkolů.

## Shrnutí

V tomto článku jsme se podívali na příklad, jak vytvořit plánovač, který může dynamicky vybírat dostupné definované agenty. Výstup plánovače rozkládá úkoly a přiřazuje agenty, aby je mohli vykonat. Předpokládá se, že agenti mají přístup ke funkcím/nástrojům potřebným k vykonání úkolu. Kromě agentů můžete přidat i jiné vzory jako reflexi, shrnující modul a round robin chat pro další přizpůsobení.

## Další zdroje

AutoGen Magnetic One - Generalistický multi-agentní systém pro řešení složitých úkolů, který dosáhl působivých výsledků na několika náročných benchmarkových testech agentů. Reference: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. V této implementaci orchestrátor vytváří plán specifický pro úkol a deleguje tyto úkoly dostupným agentům. Kromě plánování orchestrátor také používá mechanismus sledování pro monitorování pokroku úkolu a podle potřeby přeplánovává.

### Máte další otázky ohledně návrhového vzoru Plánování?

Připojte se k [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kde se setkáte s dalšími studenty, zúčastníte se konzultací a odpovíte na své otázky týkající se AI agentů.

## Předchozí lekce

[Budování důvěryhodných AI agentů](../06-building-trustworthy-agents/README.md)

## Následující lekce

[Návrhový vzor Multi-Agent](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Prohlášení o vyloučení odpovědnosti**:  
Tento dokument byl přeložen pomocí automatické překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). I když usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho mateřském jazyce by měl být považován za závazný zdroj. Pro důležité informace se doporučuje profesionální lidský překlad. Nenese odpovědnost za žádné nedorozumění nebo špatné interpretace vyplývající z použití tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->