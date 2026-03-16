[![Model de proiectare pentru Planificare](../../../translated_images/ro/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Faceți clic pe imaginea de mai sus pentru a viziona videoclipul acestei lecții)_

# Planificare

## Introducere

Această lecție va acoperi

* Definirea unui obiectiv general clar și împărțirea unei sarcini complexe în sarcini gestionabile.
* Folosirea rezultatelor structurate pentru răspunsuri mai fiabile și ușor de procesat de către mașini.
* Aplicarea unei abordări orientate pe evenimente pentru a gestiona sarcini dinamice și intrări neașteptate.

## Obiective de învățare

După parcurgerea acestei lecții, veți înțelege:

* Identificarea și stabilirea unui obiectiv general pentru un agent AI, asigurându-vă că acesta știe clar ce trebuie realizat.
* Descompunerea unei sarcini complexe în sub-sarcini gestionabile și organizarea lor într-o secvență logică.
* Dotarea agenților cu instrumentele potrivite (de ex., unelte de căutare sau instrumente de analiză a datelor), deciderea momentului și modului în care sunt folosite și gestionarea situațiilor neașteptate care apar.
* Evaluarea rezultatelor sub-sarcinilor, măsurarea performanței și iterarea acțiunilor pentru a îmbunătăți rezultatul final.

## Definirea obiectivului general și descompunerea unei sarcini

![Definirea obiectivelor și sarcinilor](../../../translated_images/ro/defining-goals-tasks.d70439e19e37c47a.webp)

Majoritatea sarcinilor din lumea reală sunt prea complexe pentru a fi abordate într-un singur pas. Un agent AI are nevoie de un obiectiv concis pentru a-și ghida planificarea și acțiunile. De exemplu, luați în considerare obiectivul:

    "Generează un itinerariu de călătorie de 3 zile."

Deși este simplu de enunțat, necesită totuși rafinare. Cu cât obiectivul este mai clar, cu atât agentul (și orice colaboratori umani) se pot concentra mai bine pe atingerea rezultatului dorit, cum ar fi crearea unui itinerar cuprinzător cu opțiuni de zbor, recomandări de hoteluri și sugestii de activități.

### Decompozirea sarcinii

Sarcinile mari sau complicate devin mai ușor de gestionat când sunt împărțite în sub-sarcini mai mici, orientate către un obiectiv.
Pentru exemplul itinerarului de călătorie, ați putea descompune obiectivul în:

* Rezervare zbor
* Rezervare hotel
* Închiriere mașină
* Personalizare

Fiecare sub-sarcină poate fi apoi abordată de agenți sau procese dedicate. Un agent s-ar putea specializa în căutarea celor mai bune oferte de zbor, altul se concentrează pe rezervările de hotel și așa mai departe. Un agent coordonator sau „downstream” poate apoi să compileze aceste rezultate într-un itinerar coerent pentru utilizatorul final.

Această abordare modulară permite, de asemenea, îmbunătățiri treptate. De exemplu, puteți adăuga agenți specializați pentru Recomandări culinare sau Sugestii pentru activități locale și rafina itinerarul în timp.

### Ieșire structurată

Modelele de limbaj mari (LLM-uri) pot genera ieșiri structurate (de ex. JSON) care sunt mai ușor de analizat și procesat de către agenții sau serviciile downstream. Acest lucru este deosebit de util într-un context multi-agent, unde putem executa aceste sarcini după ce este primit rezultatul planificării. Consultați acest <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">articol pe blog</a> pentru o prezentare rapidă.

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

# Model pentru sub-sarcină de călătorie
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # dorim să atribuim sarcina agentului

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Pentru a vă autentifica cu modelul, va trebui să generați un token de acces personal (PAT) în setările GitHub.
    # Creați tokenul PAT urmând instrucțiunile de aici: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definiți mesajul utilizatorului
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

# # Asigurați-vă că conținutul răspunsului este un șir JSON valid înainte de a-l încărca
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Response content is not a valid JSON string")

# # Afișați conținutul răspunsului după ce este încărcat ca JSON
# pprint(json.loads(response_content))

# Validați conținutul răspunsului cu modelul MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Planning Agent with Multi-Agent Orchestration

In this example, a Semantic Router Agent receives a user request (e.g., "I need a hotel plan for my trip.").

The planner then:

* Receives the Hotel Plan: The planner takes the user’s message and, based on a system prompt (including available agent details), generates a structured travel plan.
* Lists Agents and Their Tools: The agent registry holds a list of agents (e.g., for flight, hotel, car rental, and activities) along with the functions or tools they offer.
* Routes the Plan to the Respective Agents: Depending on the number of subtasks, the planner either sends the message directly to a dedicated agent (for single-task scenarios) or coordinates via a group chat manager for multi-agent collaboration.
* Summarizes the Outcome: Finally, the planner summarizes the generated plan for clarity.
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

# Model de sub-sarcină pentru călătorii

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # vrem să atribuim sarcina agentului

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Creează clientul folosind variabile de mediu verificate de tip

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definește mesajul utilizatorului

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

# Asigură-te că conținutul răspunsului este un șir JSON valid înainte de a-l încărca

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Afișează conținutul răspunsului după ce l-ai încărcat ca JSON

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

An example notebook with the previous code sample is available [here](07-autogen.ipynb).

### Planificare iterativă

Some tasks require a back-and-forth or re-planning, where the outcome of one subtask influences the next. For example, if the agent discovers an unexpected data format while booking flights, it might need to adapt its strategy before moving on to hotel bookings.

Additionally, user feedback (e.g. a human deciding they prefer an earlier flight) can trigger a partial re-plan. This dynamic, iterative approach ensures that the final solution aligns with real-world constraints and evolving user preferences.

de ex. cod exemplu

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. la fel ca în codul anterior și transmite istoricul utilizatorului, planul curent
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
# .. replanifică și trimite sarcinile agenților corespunzători
```

For more comprehensive planning do checkout Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">articol pe blog</a> for solving complex tasks.

## Rezumat

În acest articol am analizat un exemplu despre cum putem crea un planificator care poate selecta dinamic agenții disponibili. Ieșirea planificatorului descompune sarcinile și atribuie agenții astfel încât acestea să poată fi executate. Se presupune că agenții au acces la funcțiile/uneltele necesare pentru a îndeplini sarcina. Pe lângă agenți, puteți include și alte pattern-uri precum reflection, summarizer, și round robin chat pentru personalizare suplimentară.

## Resurse suplimentare

AutoGen Magentic One - Un sistem multi-agent generalist pentru rezolvarea sarcinilor complexe și care a obținut rezultate impresionante pe multiple benchmark-uri agentice provocatoare. Referință: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. În această implementare orchestratorul creează un plan specific sarcinii și delegă aceste sarcini agenților disponibili. Pe lângă planificare, orchestratorul folosește și un mecanism de urmărire pentru a monitoriza progresul sarcinii și replanifică după cum este necesar.

### Aveți mai multe întrebări despre Modelul de design pentru planificare?

Alăturați-vă [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la ore de consultanță și a primi răspunsuri la întrebările despre agenții AI.

## Lecția precedentă

[Crearea agenților AI de încredere](../06-building-trustworthy-agents/README.md)

## Lecția următoare

[Modelul de proiectare multi-agent](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Declinare de responsabilitate**:
Acest document a fost tradus folosind serviciul de traducere AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original, în limba sa de origine, trebuie considerat sursa autorizată. Pentru informații critice, se recomandă traducerea profesională efectuată de un traducător uman. Nu suntem răspunzători pentru nicio neînțelegere sau interpretare greșită rezultată din utilizarea acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->