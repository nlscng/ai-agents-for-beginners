[![Planleggingsdesignmønster](../../../translated_images/no/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Klikk på bildet ovenfor for å se videoen av denne leksjonen)_

# Planleggingsdesign

## Introduksjon

Denne leksjonen vil dekke

* Å definere et klart overordnet mål og bryte en kompleks oppgave ned i håndterbare oppgaver.
* Å bruke strukturert utdata for mer pålitelige og maskinlesbare svar.
* Å anvende en hendelsesdrevet tilnærming for å håndtere dynamiske oppgaver og uventede inndata.

## Læringsmål

Etter å ha fullført denne leksjonen, vil du ha forståelse for:

* Identifisere og sette et overordnet mål for en AI-agent, og sikre at den tydelig vet hva som må oppnås.
* Dele en kompleks oppgave inn i håndterbare deloppgaver og organisere dem i en logisk rekkefølge.
* Utstyre agenter med riktige verktøy (f.eks. søkeverktøy eller dataanalyseverktøy), bestemme når og hvordan de skal brukes, og håndtere uventede situasjoner som oppstår.
* Vurdere deloppgavers resultater, måle ytelse, og iterere på handlinger for å forbedre sluttresultatet.

## Definere det overordnede målet og bryte ned en oppgave

![Definere mål og oppgaver](../../../translated_images/no/defining-goals-tasks.d70439e19e37c47a.webp)

De fleste oppgaver i den virkelige verden er for komplekse til å håndteres i ett enkelt trinn. En AI-agent trenger et konsist mål for å styre planleggingen og handlingene sine. For eksempel, vurder målet:

    "Generer en 3-dagers reiserute."

Selv om det er enkelt å formulere, trenger det fortsatt presisering. Jo klarere målet er, desto bedre kan agenten (og eventuelle menneskelige samarbeidspartnere) fokusere på å oppnå riktig resultat, for eksempel å lage en omfattende reiseplan med flyalternativer, hotellanbefalinger og aktivitetsforslag.

### Oppgavedekomponering

Store eller intrikate oppgaver blir mer håndterbare når de deles opp i mindre, målrettede deloppgaver.
For reiseruteeksemplet kan du dele målet inn i:

* Flybestilling
* Hotellbestilling
* Bilutleie
* Personlig tilpasning

Hver deloppgave kan deretter håndteres av dedikerte agenter eller prosesser. En agent kan spesialisere seg på å finne de beste flytilbudene, en annen fokuserer på hotellbestillinger, og så videre. En koordinerende eller «nedstrøms» agent kan deretter sammenstille disse resultatene til én sammenhengende reiseplan for sluttbrukeren.

Denne modulære tilnærmingen åpner også for trinnvise forbedringer. For eksempel kan du legge til spesialiserte agenter for matanbefalinger eller lokale aktivitetsforslag og raffinere reiseplanen over tid.

### Strukturert utdata

Store språkmodeller (LLMs) kan generere strukturert utdata (f.eks. JSON) som er enklere for nedstrømsagenter eller tjenester å analysere og behandle. Dette er spesielt nyttig i en fleragent-kontekst, hvor vi kan iverksette disse oppgavene etter at planleggingsutdataene er mottatt. Se dette <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogginnlegg</a> for en rask oversikt.

Følgende Python-snutt demonstrerer en enkel planleggingsagent som dekomponerer et mål til deloppgaver og genererer en strukturert plan:

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

# Modell for reise-underoppgave
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # vi vil tildele oppgaven til agenten

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # For å autentisere mot modellen må du generere et personlig tilgangstoken (PAT) i GitHub-innstillingene dine.
    # Opprett ditt PAT-token ved å følge instruksjonene her: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definer brukermeldingen
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

# # Sørg for at responsinnholdet er en gyldig JSON-streng før du laster det
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Response content is not a valid JSON string")

# # Skriv ut responsinnholdet etter at det er lastet inn som JSON
# pprint(json.loads(response_content))

# Valider responsinnholdet med MathReasoning-modellen
# TravelPlan.model_validate(json.loads(response_content))
```

### Planleggingsagent med fleragentorkestrering

I dette eksemplet mottar en Semantisk ruteragent en brukerforespørsel (f.eks. "Jeg trenger en hotellplan for reisen min.").

Planleggeren gjør deretter:

* Mottar hotellplanen: Planleggeren tar brukerens melding og, basert på et systemprompt (inkludert tilgjengelige agentdetaljer), genererer en strukturert reiseplan.
* Lister agenter og deres verktøy: Agentregisteret inneholder en liste over agenter (f.eks. for fly, hotell, bilutleie og aktiviteter) sammen med funksjonene eller verktøyene de tilbyr.
* Ruter planen til de respektive agentene: Avhengig av antall deloppgaver sender planleggeren enten meldingen direkte til en dedikert agent (for enkeltsaks-scenarier) eller koordinerer via en gruppechatsleder for fleragent-samarbeid.
* Oppsummerer resultatet: Til slutt oppsummerer planleggeren den genererte planen for klarhet.
Følgende Python-kodeeksempel illustrerer disse trinnene:

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

# Reise-underoppgave-modell

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # vi vil tildele oppgaven til agenten

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Opprett klienten med typekontrollerte miljøvariabler

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definer brukermeldingen

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

# Sørg for at responsinnholdet er en gyldig JSON-streng før du laster det inn

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Skriv ut responsinnholdet etter at det er lastet inn som JSON

pprint(json.loads(response_content))
```

Det som følger er utdata fra forrige kode, og du kan deretter bruke denne strukturerte utdataen til å rute til `assigned_agent` og oppsummere reiseplanen for sluttbrukeren.

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

Et eksempel-notatbok med forrige kodeeksempel er tilgjengelig [her](07-autogen.ipynb).

### Iterativ planlegging

Noen oppgaver krever en frem og tilbake-prosess eller re-planlegging, der resultatet av én deloppgave påvirker den neste. For eksempel, hvis agenten oppdager et uventet dataformat mens den bestiller fly, kan den måtte tilpasse strategien før den går videre til hotellbestillinger.

I tillegg kan tilbakemeldinger fra brukeren (f.eks. at et menneske bestemmer seg for at de foretrekker et tidligere fly) utløse en delvis re-planlegging. Denne dynamiske, iterative tilnærmingen sikrer at den endelige løsningen samsvarer med virkelige begrensninger og brukeres endrede preferanser.

f.eks. eksempelkode

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. det samme som forrige kode og videreformidle brukerens historikk og gjeldende plan
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
# .. planlegg på nytt og send oppgavene til respektive agenter
```

For mer omfattende planlegging, sjekk ut Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">blogginnlegg</a> for å løse komplekse oppgaver.

## Oppsummering

I denne artikkelen har vi sett på et eksempel på hvordan vi kan lage en planlegger som dynamisk kan velge de tilgjengelige agentene som er definert. Utdataene fra planleggeren dekomponerer oppgavene og tildeler agentene slik at de kan utføres. Det forutsettes at agentene har tilgang til funksjonene/verktøyene som kreves for å utføre oppgaven. I tillegg til agentene kan du inkludere andre mønstre som refleksjon, oppsummeringsmodul og round-robin-chat for å ytterligere tilpasse løsningen.

## Ytterligere ressurser

AutoGen Magentic One - A Generalist multi-agent system for solving complex tasks and has achieved impressive results on multiple challenging agentic benchmarks. Reference: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. I denne implementasjonen oppretter orkestratoren oppgavespesifikke planer og delegerer disse oppgavene til de tilgjengelige agentene. I tillegg til planlegging bruker orkestratoren også en sporingsmekanisme for å overvåke fremdriften i oppgaven og re-planlegger etter behov.

### Har du flere spørsmål om planleggingsdesignmønsteret?

Bli med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for å møte andre lærende, delta på kontortid og få spørsmålene dine om AI-agenter besvart.

## Forrige leksjon

[Bygge pålitelige AI-agenter](../06-building-trustworthy-agents/README.md)

## Neste leksjon

[Fleragent-designmønster](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfraskrivelse:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten Co-op Translator (https://github.com/Azure/co-op-translator). Selv om vi legger vekt på nøyaktighet, vennligst vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Originaldokumentet på det opprinnelige språket bør betraktes som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->