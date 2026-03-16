[![Planning Design Pattern](../../../translated_images/nl/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Klik op de afbeelding hierboven om de video van deze les te bekijken)_

# Planningontwerp

## Introductie

Deze les behandelt

* Het definiëren van een duidelijk overkoepelend doel en het opsplitsen van een complexe taak in beheersbare taken.
* Het benutten van gestructureerde output voor betrouwbaardere en machinaal leesbare responsen.
* Het toepassen van een event-driven benadering om dynamische taken en onverwachte invoer af te handelen.

## Leerdoelen

Na het voltooien van deze les heb je inzicht in:

* Het identificeren en vaststellen van een overkoepelend doel voor een AI-agent, zodat deze duidelijk weet wat er bereikt moet worden.
* Het ontleden van een complexe taak in beheersbare subtaken en deze organiseren in een logische volgorde.
* Het voorzien van agenten van de juiste tools (bijv. zoektools of data-analysesoftware), bepalen wanneer en hoe deze worden gebruikt, en omgaan met onverwachte situaties die zich voordoen.
* Het evalueren van de uitkomsten van subtaken, het meten van prestaties en het itereren op acties om de uiteindelijke output te verbeteren.

## Het Vaststellen van het Overkoepelend Doel en het Opsplitsen van een Taak

![Defining Goals and Tasks](../../../translated_images/nl/defining-goals-tasks.d70439e19e37c47a.webp)

De meeste echte taken zijn te complex om in één stap aan te pakken. Een AI-agent heeft een beknopt doel nodig om zijn planning en acties te sturen. Overweeg bijvoorbeeld het doel:

    "Genereer een reisplan voor 3 dagen."

Hoewel het eenvoudig te formuleren is, vereist het nog verfijning. Hoe duidelijker het doel, hoe beter de agent (en eventuele menselijke samenwerkers) zich kan richten op het bereiken van het juiste resultaat, zoals het maken van een uitgebreid reisschema met vluchtopties, hotelaanbevelingen en activiteitenvoorstellen.

### Taakontleding

Grote of ingewikkelde taken worden beter beheersbaar wanneer ze worden opgesplitst in kleinere, doelgerichte subtaken.
Bij het voorbeeld van het reisplan kun je het doel opsplitsen in:

* Vlucht Boeken
* Hotel Boeken
* Auto Huren
* Personalisatie

Elke subtaak kan vervolgens worden aangepakt door gespecialiseerde agenten of processen. De ene agent richt zich bijvoorbeeld op het zoeken naar de beste vluchtdeals, een andere op hotelboekingen, enzovoort. Een coördinerende of "downstream" agent kan deze resultaten vervolgens samenvoegen tot één samenhangend reisschema voor de eindgebruiker.

Deze modulaire aanpak maakt ook stapsgewijze verbeteringen mogelijk. Zo kun je gespecialiseerde agenten toevoegen voor Etenaanbevelingen of Lokale Activiteiten Suggesties en het reisschema in de loop der tijd verfijnen.

### Gestructureerde output

Grote taalmodellen (LLM's) kunnen gestructureerde output genereren (bijv. JSON) die gemakkelijker te verwerken is voor downstream agenten of services. Dit is vooral nuttig in een multi-agent context, waarbij we deze taken kunnen uitvoeren nadat de planningsoutput is ontvangen. Zie deze <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogpost</a> voor een snel overzicht.

De volgende Python-code toont een eenvoudige planningagent die een doel ontleedt in subtaken en een gestructureerd plan genereert:

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

# Reis SubTaak Model
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # we willen de taak aan de agent toewijzen

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Om te authenticeren met het model moet je een persoonlijk toegangstoken (PAT) genereren in je GitHub-instellingen.
    # Maak je PAT-token aan door de instructies hier te volgen: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definieer het gebruikersbericht
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

# # Zorg ervoor dat de antwoordinhoud een geldige JSON-string is voordat je deze laadt
# response_content: Optioneel[str] = response.content als isinstance(
#     response.content, str) anders None
# als response_content None is:
#     raise ValueError("Antwoordinhoud is geen geldige JSON-string")

# # Print de antwoordinhoud nadat deze als JSON is geladen
# pprint(json.loads(response_content))

# Valideer de antwoordinhoud met het MathReasoning-model
# TravelPlan.model_validate(json.loads(response_content))
```

### Planningagent met Multi-Agent Orkestratie

In dit voorbeeld ontvangt een Semantic Router Agent een gebruikersverzoek (bijv. "Ik heb een hotelplan nodig voor mijn reis.").

De planner doet vervolgens:

* Ontvangt het Hotelplan: De planner neemt het bericht van de gebruiker en genereert, op basis van een systeem-prompt (inclusief beschikbare agentdetails), een gestructureerd reisplan.
* Lijst met Agenten en Hun Tools: Het agentenregister bevat een lijst met agenten (bijv. voor vlucht, hotel, autoverhuur en activiteiten) samen met de functies of tools die ze bieden.
* Stuurt het Plan naar de Betreffende Agenten: Afhankelijk van het aantal subtaken stuurt de planner het bericht direct naar een toegewijde agent (voor scenario's met één taak) of coördineert via een groepschatmanager voor samenwerking tussen meerdere agenten.
* Vat de Uitkomst samen: Ten slotte vat de planner het gegenereerde plan samen voor duidelijkheid.
Het volgende Python-codevoorbeeld illustreert deze stappen:

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

# Reis SubTaak Model

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # we willen de taak toewijzen aan de agent

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Maak de cliënt aan met type-gecontroleerde omgevingsvariabelen

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definieer het gebruikersbericht

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

# Zorg ervoor dat de antwoordinhoud een geldige JSON-string is voordat je deze inlaadt

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Druk de antwoordinhoud af nadat deze als JSON is ingeladen

pprint(json.loads(response_content))
```

Wat volgt is de output van de vorige code en je kunt deze gestructureerde output gebruiken om naar `assigned_agent` te routeren en het reisplan samen te vatten voor de eindgebruiker.

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

Een voorbeeld-notebook met de vorige code is beschikbaar [hier](07-autogen.ipynb).

### Iteratieve Planning

Sommige taken vereisen een heen-en-weer proces of herplanning, waarbij de uitkomst van een subtaak de volgende beïnvloedt. Bijvoorbeeld als de agent een onverwacht dataformaat ontdekt tijdens het boeken van vluchten, moet hij mogelijk de strategie aanpassen voordat hij verdergaat met hotelboekingen.

Daarnaast kan feedback van de gebruiker (bijv. als iemand kiest voor een eerdere vlucht) een gedeeltelijke herplanning activeren. Deze dynamische, iteratieve benadering zorgt ervoor dat de uiteindelijke oplossing aansluit bij de praktische beperkingen en veranderende voorkeuren van de gebruiker.

bijv. voorbeeldcode

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. hetzelfde als vorige code en geef de gebruikersgeschiedenis, huidig plan door
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
# .. herplan en stuur de taken naar respectievelijke agenten
```

Voor meer uitgebreide planning, bekijk Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogpost</a> voor het oplossen van complexe taken.

## Samenvatting

In dit artikel hebben we gekeken naar een voorbeeld van hoe we een planner kunnen maken die dynamisch de beschikbare gedefinieerde agenten selecteert. De output van de planner splitst de taken op en wijst de agenten toe zodat deze kunnen worden uitgevoerd. Er wordt vanuit gegaan dat de agenten toegang hebben tot de functies/tools die nodig zijn om de taak uit te voeren. Naast de agenten kun je ook andere patronen toevoegen zoals reflectie, samenvatter en round robin chat om verder te personaliseren.

## Aanvullende bronnen

AutoGen Magentic One - een generalistisch multi-agent systeem voor het oplossen van complexe taken en heeft indrukwekkende resultaten behaald op meerdere uitdagende agent benchmarks. Referentie: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. In deze implementatie maakt de orkestrator taak-specifieke plannen en delegeert deze taken aan beschikbare agenten. Naast planning past de orkestrator ook een trackingsmechanisme toe om de voortgang van de taak te monitoren en herplant waar nodig.

### Meer vragen over het Planning Design Pattern?

Sluit je aan bij de [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) om andere leerlingen te ontmoeten, deel te nemen aan office hours en de vragen over AI Agents beantwoord te krijgen.

## Vorige les

[Vertrouwwaardige AI-agenten bouwen](../06-building-trustworthy-agents/README.md)

## Volgende les

[Multi-Agent Design Pattern](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Dit document is vertaald met behulp van de AI-vertalingsdienst [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel we streven naar nauwkeurigheid, dient u er rekening mee te houden dat automatische vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het oorspronkelijke document in de oorspronkelijke taal wordt beschouwd als de gezaghebbende bron. Voor belangrijke informatie wordt professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->