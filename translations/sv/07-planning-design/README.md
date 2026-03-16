[![Planning Design Pattern](../../../translated_images/sv/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Klicka på bilden ovan för att se videon för denna lektion)_

# Planeringsdesign

## Introduktion

Denna lektion kommer att täcka

* Att definiera ett tydligt övergripande mål och bryta ner en komplex uppgift i hanterbara uppgifter.
* Att utnyttja strukturerad output för mer pålitliga och maskinläsbara svar.
* Att tillämpa ett händelsestyrt tillvägagångssätt för att hantera dynamiska uppgifter och oväntade indata.

## Lärandemål

Efter att ha genomfört denna lektion kommer du att ha en förståelse för:

* Identifiera och sätta ett övergripande mål för en AI-agent, för att säkerställa att den tydligt vet vad som behöver uppnås.
* Dela upp en komplex uppgift i hanterbara deluppgifter och organisera dem i en logisk ordning.
* Utrusta agenter med rätt verktyg (t.ex. sökverktyg eller dataanalysverktyg), bestämma när och hur de används och hantera oväntade situationer som uppstår.
* Utvärdera resultat av deluppgifter, mäta prestation och iterera på åtgärder för att förbättra det slutliga resultatet.

## Definiera det övergripande målet och bryta ner en uppgift

![Definiera mål och uppgifter](../../../translated_images/sv/defining-goals-tasks.d70439e19e37c47a.webp)

De flesta verkliga uppgifter är för komplexa för att hanteras i en enda steg. En AI-agent behöver ett koncist mål för att vägleda sin planering och sina åtgärder. Till exempel, betrakta målet:

    "Generera en resplan för 3 dagar."

Även om det är enkelt att ange, behöver det fortfarande förfinas. Ju tydligare målet är, desto bättre kan agenten (och eventuella mänskliga medarbetare) fokusera på att uppnå rätt resultat, som att skapa en omfattande resplan med flygalternativ, hotellrekommendationer och aktivitetsförslag.

### Uppgiftsuppdelning

Stora eller invecklade uppgifter blir mer hanterbara när de delas upp i mindre, målorienterade deluppgifter.
För exemplet med resplanen kan du dela upp målet i:

* Flygbokning
* Hotellbokning
* Biluthyrning
* Personalisering

Varje deluppgift kan sedan hanteras av dedikerade agenter eller processer. En agent kan specialisera sig på att söka de bästa flygerbjudandena, en annan fokuserar på hotellbokningar och så vidare. En koordinerande eller "nedströms" agent kan sedan sammanställa dessa resultat till en sammanhängande resplan för slutanvändaren.

Detta modulära tillvägagångssätt tillåter också stegvisa förbättringar. Till exempel kan du lägga till specialiserade agenter för matrekommendationer eller lokala aktivitetsförslag och förfina resplanen över tid.

### Strukturerad output

Stora språkliga modeller (LLMs) kan generera strukturerad output (t.ex. JSON) som är lättare för nedströmsagenter eller tjänster att tolka och bearbeta. Detta är särskilt användbart i ett kontext med flera agenter, där vi kan agera på dessa uppgifter efter att planeringsoutput mottagits. Se detta <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogginlägg</a> för en snabb översikt.

Följande Python-exempel visar en enkel planeringsagent som delar upp ett mål i deluppgifter och genererar en strukturerad plan:

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

# Resa Deluppgiftsmodell
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # vi vill tilldela uppgiften till agenten

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # För att autentisera med modellen behöver du skapa en personlig åtkomsttoken (PAT) i dina GitHub-inställningar.
    # Skapa din PAT-token genom att följa instruktionerna här: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definiera användarmeddelandet
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

# # Säkerställ att svarsinnehållet är en giltig JSON-sträng innan den laddas
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Svarsinnehållet är inte en giltig JSON-sträng")

# # Skriv ut svarsinnehållet efter att det laddats som JSON
# pprint(json.loads(response_content))

# Validera svarsinnehållet med MathReasoning-modellen
# TravelPlan.model_validate(json.loads(response_content))
```

### Planeringsagent med multi-agent orkestrering

I detta exempel tar en Semantic Router Agent emot en användarförfrågan (t.ex. "Jag behöver en hotellplan för min resa.").

Planeraren gör sedan följande:

* Tar emot hotellplanen: Planeraren tar användarens meddelande och baserat på en systemprompt (inklusive tillgängliga agentdetaljer) genererar en strukturerad reseplan.
* Lista agenter och deras verktyg: Agentregistret innehåller en lista över agenter (t.ex. för flyg, hotell, biluthyrning och aktiviteter) tillsammans med de funktioner eller verktyg de erbjuder.
* Dirigerar planen till respektive agenter: Beroende på antalet deluppgifter skickar planeraren antingen meddelandet direkt till en dedikerad agent (vid enkeluppgiftsfall) eller koordinerar via en gruppchattmanager för samarbete mellan flera agenter.
* Sammanfattar resultatet: Slutligen sammanfattar planeraren den genererade planen för tydlighet.
Följande Python-kodexempel illustrerar dessa steg:

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

# Resa Deluppgiftsmodell

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # vi vill tilldela uppgiften till agenten

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Skapa klienten med typkontrollerade miljövariabler

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definiera användarmeddelandet

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

# Säkerställ att svarsinnehållet är en giltig JSON-sträng innan den laddas

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Skriv ut svarsinnehållet efter att det har laddats som JSON

pprint(json.loads(response_content))
```

Nedan följer output från föregående kod och du kan sedan använda denna strukturerade output för att dirigera till `assigned_agent` och sammanfatta reseplanen för slutanvändaren.

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

Ett exempel på ett anteckningsblock med föregående kodexempel finns [här](07-autogen.ipynb).

### Iterativ planering

Vissa uppgifter kräver fram- och tillbaka eller omplanering, där resultatet av en deluppgift påverkar nästa. Till exempel, om agenten upptäcker ett oväntat dataformat när den bokar flyg kan det behöva anpassa sin strategi innan det går vidare till hotellbokningarna.

Dessutom kan användarfeedback (t.ex. en person som bestämmer sig för att de föredrar en tidigare flygning) utlösa en partiell omplanering. Detta dynamiska, iterativa tillvägagångssätt säkerställer att den slutliga lösningen stämmer överens med verkliga begränsningar och föränderliga användarpreferenser.

t.ex exempel kod

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. samma som föregående kod och vidarebefordra användarhistoriken, nuvarande plan
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
# .. planera om och skicka uppgifterna till respektive agenter
```

För mer omfattande planering, kolla Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogginlägg</a> för att lösa komplexa uppgifter.

## Sammanfattning

I denna artikel har vi tittat på ett exempel på hur vi kan skapa en planerare som dynamiskt kan välja tillgängliga agenter som definieras. Planerarens output delar upp uppgifterna och tilldelar agenter så att de kan utföras. Det förutsätts att agenterna har tillgång till de funktioner/verktyg som krävs för att utföra uppgiften. Utöver agenterna kan du inkludera andra mönster som reflektion, sammanfattare och "round robin"-chatt för att anpassa ytterligare.

## Ytterligare resurser

AutoGen Magnetic One - Ett generalistiskt multi-agent-system för att lösa komplexa uppgifter och har uppnått imponerande resultat på flera utmanande agentiska benchmarks. Referens: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. I denna implementation skapar orkestratorn en uppgiftsspecifik plan och delegerar dessa uppgifter till de tillgängliga agenterna. Förutom planeringen använder orkestratorn även en spårningsmekanism för att övervaka uppgiftens framsteg och omplanerar vid behov.

### Har du fler frågor om planeringsdesignmönstret?

Anslut till [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) för att träffa andra elever, delta i kontorstider och få dina frågor om AI-agenter besvarade.

## Föregående lektion

[Skapa pålitliga AI-agenter](../06-building-trustworthy-agents/README.md)

## Nästa lektion

[Multi-Agent Design Pattern](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfriskrivning**:
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet, bör du vara medveten om att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på dess ursprungliga språk ska betraktas som den auktoritativa källan. För viktig information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för eventuella missförstånd eller feltolkningar som uppstår från användningen av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->