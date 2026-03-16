[![Planning Design Pattern](../../../translated_images/da/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Klik på billedet ovenfor for at se videoen til denne lektion)_

# Planlægningsdesign

## Introduktion

Denne lektion vil dække

* Definition af et klart overordnet mål og opdeling af en kompleks opgave i håndterbare delopgaver.
* Udnyttelse af struktureret output for mere pålidelige og maskinlæsbare svar.
* Anvendelse af en hændelsesdrevet tilgang til at håndtere dynamiske opgaver og uventede input.

## Læringsmål

Efter at have gennemført denne lektion vil du have en forståelse af:

* At identificere og sætte et overordnet mål for en AI-agent og sikre, at den klart ved, hvad der skal opnås.
* At nedbryde en kompleks opgave i håndterbare delopgaver og organisere dem i en logisk rækkefølge.
* At udstyre agenter med de rigtige værktøjer (f.eks. søgeværktøjer eller dataanalyseværktøjer), beslutte hvornår og hvordan de skal bruges, og håndtere uventede situationer, der opstår.
* At evaluere delopgavens resultater, måle ydeevne og gentage handlinger for at forbedre det endelige output.

## Definition af det overordnede mål og opdeling af en opgave

![Defining Goals and Tasks](../../../translated_images/da/defining-goals-tasks.d70439e19e37c47a.webp)

De fleste opgaver i virkeligheden er for komplekse til at løses i ét enkelt trin. En AI-agent har brug for et præcist mål for at styre sin planlægning og sine handlinger. For eksempel, overvej målet:

    "Generer en rejseplan for 3 dage."

Selvom det er simpelt at formulere, kræver det stadig forfining. Jo klarere målet er, desto bedre kan agenten (og eventuelle menneskelige samarbejdspartnere) fokusere på at opnå det rette resultat, såsom at skabe en omfattende rejseplan med flymuligheder, hotelanbefalinger og aktivitetsforslag.

### Opdeling af opgaver

Store eller indviklede opgaver bliver mere håndterbare, når de opdeles i mindre, målorienterede delopgaver.  
For rejseplans-eksemplet kan du opdele målet i følgende:

* Flybestilling  
* Hotelbestilling  
* Biludlejning  
* Personalisering

Hver delopgave kan så tackles af dedikerede agenter eller processer. Én agent kan specialisere sig i at finde de bedste flytilbud, en anden fokuserer på hotelbookinger osv. En koordinerende eller "downstream" agent kan derefter samle disse resultater til én sammenhængende rejseplan til slutbrugeren.

Denne modulære tilgang tillader også inkrementelle forbedringer. For eksempel kan du tilføje specialiserede agenter til madanbefalinger eller lokale aktivitetsforslag og løbende forfine rejseplanen.

### Struktureret output

Store sprogmodeller (LLMs) kan generere struktureret output (f.eks. JSON), der er nemmere for downstream-agenter eller -tjenester at parse og bearbejde. Dette er særligt nyttigt i en multi-agent sammenhæng, hvor vi kan handle på disse opgaver efter modtagelsen af planlægningsoutputtet. Se denne <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogpost</a> for en hurtig oversigt.

Det følgende Python-udsnit demonstrerer en simpel planlægningsagent, der nedbryder et mål i delopgaver og genererer en struktureret plan:

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

# Rejse Underopgave Model
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # vi vil tildele opgaven til agenten

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # For at godkende med modellen skal du generere en personlig adgangstoken (PAT) i dine GitHub-indstillinger.
    # Opret din PAT-token ved at følge instruktionerne her: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definer brugermeddelelsen
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

# # Sørg for at svarindholdet er en gyldig JSON-streng, før det indlæses
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Svarindholdet er ikke en gyldig JSON-streng")

# # Udskriv svarindholdet efter at have indlæst det som JSON
# pprint(json.loads(response_content))

# Valider svarindholdet med MathReasoning-modellen
# TravelPlan.model_validate(json.loads(response_content))
```

### Planlægningsagent med multi-agent orkestrering

I dette eksempel modtager en Semantic Router Agent en brugerforespørgsel (f.eks. "Jeg har brug for en hotelplan til min rejse.").

Planlæggeren gør derefter:

* Modtager Hotelplanen: Planlæggeren tager brugerens besked og genererer baseret på et systemprompt (inklusive detaljer om tilgængelige agenter) en struktureret rejseplan.
* Liste over agenter og deres værktøjer: Agentregistret indeholder en liste af agenter (f.eks. til fly, hotel, biludlejning og aktiviteter) sammen med de funktioner eller værktøjer, de tilbyder.
* Sender planen til de respektive agenter: Afhængigt af antal delopgaver sender planlæggeren enten beskeden direkte til en dedikeret agent (for enkelopgave-scenarier) eller koordinerer via en gruppechat-manager for multi-agent samarbejde.
* Opsummerer resultatet: Endelig opsummerer planlæggeren den genererede plan for klarhed.
Følgende Python-kodeeksempel illustrerer disse trin:

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

# Rejse underopgave model

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # vi vil tildele opgaven til agenten

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Opret klienten med typekontrollerede miljøvariabler

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definer brugermeddelelsen

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

# Sørg for, at svarets indhold er en gyldig JSON-streng, inden det indlæses

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Udskriv svarindholdet efter at det er indlæst som JSON

pprint(json.loads(response_content))
```

Det følgende er outputtet fra den foregående kode, og du kan så bruge dette strukturerede output til at sende til `assigned_agent` og opsummere rejseplanen til slutbrugeren.

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

En eksempelnote bog med det foregående kodeeksempel er tilgængelig [her](07-autogen.ipynb).

### Iterativ planlægning

Nogle opgaver kræver en frem og tilbage proces eller omplanlægning, hvor resultatet af en delopgave påvirker næste trin. For eksempel, hvis agenten opdager et uventet dataformat under flybogning, kan den være nødt til at tilpasse sin strategi, før den går videre til hotelbestilling.

Desuden kan brugertilbagemeldinger (f.eks. en person som ønsker en tidligere flyafgang) udløse en delvis omplanlægning. Denne dynamiske, iterative tilgang sikrer, at den endelige løsning stemmer overens med virkelighedens begrænsninger og brugernes skiftende præferencer.

f.eks. eksempel kode

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. det samme som tidligere kode og videregive brugerens historik, nuværende plan
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
# .. omplanlæg og send opgaverne til de respektive agenter
```

For mere omfattende planlægning kan du tjekke Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogpost</a> for løsning af komplekse opgaver.

## Resumé

I denne artikel har vi set et eksempel på, hvordan vi kan skabe en planlægger, der dynamisk kan vælge de tilgængelige agenter, der er defineret. Planlæggerens output nedbryder opgaverne og tildeler agenter, så de kan eksekveres. Det antages, at agenterne har adgang til de funktioner/værktøjer, der er nødvendige for at udføre opgaven. Ud over agenterne kan du inkludere andre mønstre som refleksion, opsummering og round robin chat for yderligere tilpasning.

## Yderligere ressourcer

AutoGen Magnetic One - Et generalistisk multi-agent system til løsning af komplekse opgaver, som har opnået imponerende resultater på flere udfordrende agentbaserede benchmarks. Reference: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. I denne implementering skaber orkestratoren opgavespecifikke planer og delegerer disse opgaver til de tilgængelige agenter. Ud over planlægning anvender orkestratoren også en sporingsmekanisme til at overvåge opgavens fremskridt og omplanlægger efter behov.

### Har du flere spørgsmål om planlægningsdesignmønsteret?

Deltag i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for at møde andre elever, deltage i kontortimer og få svar på dine spørgsmål om AI-agenter.

## Forrige lektion

[Opbygning af pålidelige AI-agenter](../06-building-trustworthy-agents/README.md)

## Næste lektion

[Multi-agent designmønster](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:  
Dette dokument er oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi stræber efter nøjagtighed, bedes du være opmærksom på, at automatiserede oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets modersmål bør betragtes som den autoritative kilde. For kritisk information anbefales professionel menneskelig oversættelse. Vi påtager os intet ansvar for misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->