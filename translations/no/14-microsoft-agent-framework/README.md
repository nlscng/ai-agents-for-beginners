# Utforske Microsoft Agent Framework

![Agent-rammeverk](../../../translated_images/no/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introduksjon

Denne leksjonen vil dekke:

- Forstå Microsoft Agent Framework: Nøkkelfunksjoner og verdi  
- Utforske de sentrale konseptene i Microsoft Agent Framework
- Sammenligne MAF med Semantic Kernel og AutoGen: Migrasjonsveiledning

## Læringsmål

Etter å ha fullført denne leksjonen, vil du vite hvordan du:

- Bygge produksjonsklare AI-agenter ved hjelp av Microsoft Agent Framework
- Anvende kjernegenskapene i Microsoft Agent Framework på dine agentiske brukstilfeller
- Migrere og integrere eksisterende agentiske rammeverk og verktøy  

## Kodeeksempler 

Kodeeksempler for [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) finnes i dette depotet under `xx-python-agent-framework` og `xx-dotnet-agent-framework` filer.

## Forstå Microsoft Agent Framework

![Rammeverksintro](../../../translated_images/no/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) bygger videre på erfaringene og lærdommene fra Semantic Kernel og AutoGen. Det tilbyr fleksibiliteten til å håndtere det brede spekteret av agentiske brukstilfeller som sees både i produksjon og forskningsmiljøer, inkludert:

- **Sekvensiell agentorkestrering** i scenarier der trinnvise arbeidsflyter er nødvendige.
- **Konkurrent orkestrering** i scenarier der agenter må fullføre oppgaver samtidig.
- **Gruppechat-orkestrering** i scenarier der agenter kan samarbeide om én oppgave.
- **Overleveringsorkestrering** i scenarier der agenter overleverer oppgaver til hverandre etter hvert som deloppgaver fullføres.
- **Magnetisk orkestrering** i scenarier der en lederagent oppretter og endrer en oppgaveliste og håndterer koordineringen av subagenter for å fullføre oppgaven.

For å levere AI-agenter i produksjon, inkluderer MAF også funksjoner for:

- **Observabilitet** gjennom bruk av OpenTelemetry hvor hver handling av AI-agenten, inkludert verktøykall, orkestreringstrinn, resonnementsflyt og ytelssovervåking, kan vises i Microsoft Foundry-dashboards.
- **Sikkerhet** ved å hoste agenter nativt på Microsoft Foundry, som inkluderer sikkerhetskontroller som rollebasert tilgang, håndtering av private data og innebygd innholdssikkerhet.
- **Varighet** ettersom agenttråder og arbeidsflyter kan pause, gjenoppta og komme seg etter feil, noe som muliggjør lengre kjørende prosesser.
- **Kontroll** ettersom arbeidsflyter med mennesket i løkken støttes, hvor oppgaver merkes som krever menneskelig godkjenning.

Microsoft Agent Framework er også fokusert på å være interoperabel ved å:

- **Være sky-agnostisk** - Agenter kan kjøre i containere, lokalt og på tvers av flere forskjellige skyer.
- **Være leverandør-agnostisk** - Agenter kan opprettes gjennom ditt foretrukne SDK inkludert Azure OpenAI og OpenAI
- **Integrere åpne standarder** - Agenter kan benytte protokoller som Agent-to-Agent (A2A) og Model Context Protocol (MCP) for å oppdage og bruke andre agenter og verktøy.
- **Plugins og Connectors** - Tilkoblinger kan gjøres til data- og minnetjenester som Microsoft Fabric, SharePoint, Pinecone og Qdrant.

La oss se på hvordan disse funksjonene anvendes på noen av kjernebegrepene i Microsoft Agent Framework.

## Nøkkelkonsepter i Microsoft Agent Framework

### Agenter

![Agent-rammeverk](../../../translated_images/no/agent-components.410a06daf87b4fef.webp)

**Opprette agenter**

Agentopprettelse gjøres ved å definere inferensservicen (LLM-leverandør), et
sett med instruksjoner for AI-agenten å følge, og et tildelt `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Ovenfor bruker `Azure OpenAI` men agenter kan opprettes ved hjelp av en rekke tjenester inkludert `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` API-er

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

eller eksterne agenter ved bruk av A2A-protokollen:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Kjøre agenter**

Agenter kjøres ved å bruke metodene `.run` eller `.run_stream` for enten ikke-strømmende eller strømmende svar.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Hver agentkjøring kan også ha alternativer for å tilpasse parametere som `max_tokens` brukt av agenten, `tools` som agenten kan kalle, og til og med selve `model` som brukes for agenten.

Dette er nyttig i tilfeller hvor spesifikke modeller eller verktøy er påkrevd for å fullføre en brukers oppgave.

**Verktøy**

Verktøy kan defineres både når agenten defineres:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Når du oppretter en ChatAgent direkte

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

og også når agenten kjøres:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Verktøy levert kun for denne kjøringen )
```

**Agenttråder**

Agenttråder brukes for å håndtere samtaler med flere runder. Tråder kan opprettes enten ved:

- Å bruke `get_new_thread()` som gjør at tråden kan lagres over tid
- Å opprette en tråd automatisk når agenten kjøres og kun la tråden vare under den aktuelle kjøringen.

For å opprette en tråd ser koden slik ut:

```python
# Opprett en ny tråd.
thread = agent.get_new_thread() # Kjør agenten med tråden.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Du kan deretter serialisere tråden for å lagres for senere bruk:

```python
# Opprett en ny tråd.
thread = agent.get_new_thread() 

# Kjør agenten med tråden.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serialiser tråden for lagring.

serialized_thread = await thread.serialize() 

# Deserialiser trådens tilstand etter lasting fra lagring.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent-mellomvare**

Agenter samhandler med verktøy og LLM-er for å fullføre brukerens oppgaver. I visse scenarioer ønsker vi å utføre eller spore handlinger mellom disse interaksjonene. Agent-mellomvare gjør oss i stand til å gjøre dette gjennom:

*Funksjonsmellomvare*

Denne mellomvaren lar oss utføre en handling mellom agenten og en funksjon/et verktøy som den kommer til å kalle. Et eksempel på når dette kan brukes er når du ønsker å gjøre noe logging ved funksjonskallet.

I koden under definerer `next` om neste mellomvare eller den faktiske funksjonen skal kalles.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Forbehandling: Logg før funksjonskjøring
    print(f"[Function] Calling {context.function.name}")

    # Fortsett til neste mellomvare eller funksjonskjøring
    await next(context)

    # Etterbehandling: Logg etter funksjonskjøring
    print(f"[Function] {context.function.name} completed")
```

*Chat-mellomvare*

Denne mellomvaren lar oss utføre eller loggføre en handling mellom agenten og forespørslene til LLM-en.

Dette inneholder viktig informasjon som `messages` som sendes til AI-tjenesten.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Forbehandling: Logg før AI-kall
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Fortsett til neste mellomvare eller AI-tjeneste
    await next(context)

    # Etterbehandling: Logg etter AI-svar
    print("[Chat] AI response received")

```

**Agentminne**

Som dekket i leksjonen `Agentic Memory`, er minne et viktig element for å gjøre agenten i stand til å operere over forskjellige kontekster. MAF tilbyr flere ulike typer minner:

*Minne i minnet (In-Memory Storage)*

Dette er minnet som lagres i tråder under applikasjonens kjøretid.

```python
# Opprett en ny tråd.
thread = agent.get_new_thread() # Kjør agenten med tråden.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Vedvarende meldinger*

Dette minnet brukes når man lagrer samtalehistorikk på tvers av forskjellige økter. Det defineres ved hjelp av `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Opprett et egendefinert meldingslager
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamisk minne*

Dette minnet legges til konteksten før agenter kjøres. Disse minnene kan lagres i eksterne tjenester som mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Bruker Mem0 for avanserte minnefunksjoner
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**Agentobservabilitet**

Observabilitet er viktig for å bygge pålitelige og vedlikeholdbare agentiske systemer. MAF integreres med OpenTelemetry for å gi sporing og målere for bedre observabilitet.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # gjør noe
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Arbeidsflyter

MAF tilbyr arbeidsflyter som er forhåndsdefinerte trinn for å fullføre en oppgave og inkluderer AI-agenter som komponenter i disse trinnene.

Arbeidsflyter består av forskjellige komponenter som muliggjør bedre kontrollflyt. Arbeidsflyter muliggjør også **orkestrering med flere agenter** og **sjekkpunkter** for å lagre arbeidsflytens tilstand.

Kjernekomponentene i en arbeidsflyt er:

**Executors**

Executors mottar inndatameldinger, utfører sine tildelte oppgaver, og produserer deretter en utgangsmelding. Dette flytter arbeidsflyten fremover mot å fullføre den større oppgaven. Executors kan være enten AI-agenter eller egendefinert logikk.

**Edges**

Edges brukes til å definere flyten av meldinger i en arbeidsflyt. Disse kan være:

*Direct Edges* - Enkle en-til-en koblinger mellom executors:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Conditional Edges* - Aktiveres etter at en viss betingelse er oppfylt. For eksempel, når hotellrom ikke er tilgjengelige, kan en executor foreslå andre alternativer.

*Switch-case Edges* - Ruter meldinger til forskjellige executors basert på definerte betingelser. For eksempel, hvis en reise kunde har prioritert tilgang, kan deres oppgaver håndteres gjennom en annen arbeidsflyt.

*Fan-out Edges* - Sender én melding til flere mål.

*Fan-in Edges* - Samler flere meldinger fra forskjellige executors og sender til ett mål.

**Hendelser**

For å gi bedre observabilitet i arbeidsflyter tilbyr MAF innebygde hendelser for eksekvering, inkludert:

- `WorkflowStartedEvent`  - Arbeidsflytekjøring begynner
- `WorkflowOutputEvent` - Arbeidsflyten produserer en utgang
- `WorkflowErrorEvent` - Arbeidsflyten opplever en feil
- `ExecutorInvokeEvent`  - Executor begynner prosessering
- `ExecutorCompleteEvent`  -  Executor fullfører prosessering
- `RequestInfoEvent` - En forespørsel blir utstedt

## Migrere fra andre rammeverk (Semantic Kernel og AutoGen)

### Forskjeller mellom MAF og Semantic Kernel

**Forenklet agentopprettelse**

Semantic Kernel er avhengig av opprettelsen av en Kernel-instans for hver agent. MAF har en forenklet tilnærming ved å bruke utvidelser for hovedleverandørene.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Opprettelse av agenttråd**

Semantic Kernel krever at tråder opprettes manuelt. I MAF blir tråden direkte tildelt agenten.

```python
thread = agent.get_new_thread() # Kjør agenten med tråden.
```

**Registrering av verktøy**

I Semantic Kernel blir verktøy registrert til Kernel og Kernelen blir deretter sendt til agenten. I MAF blir verktøy registrert direkte under agentopprettelsesprosessen.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Forskjeller mellom MAF og AutoGen

**Teams vs Arbeidsflyter**

`Teams` er hendelsesstrukturen for hendelsesdrevet aktivitet med agenter i AutoGen. MAF bruker `Workflows` som ruter data til executors gjennom en grafbasert arkitektur.

**Opprettelse av verktøy**

AutoGen bruker `FunctionTool` for å pakke inn funksjoner som agenter kan kalle. MAF bruker @ai_function som fungerer på lignende måte, men som også utleder skjemaene automatisk for hver funksjon.

**Agentatferd**

Agenter er en-omgangs-agenter som standard i AutoGen med mindre `max_tool_iterations` er satt til et høyere tall. I MAF er `ChatAgent` fleretur som standard, noe som betyr at den vil fortsette å kalle verktøy inntil brukerens oppgave er fullført.

## Kodeeksempler 

Kodeeksempler for Microsoft Agent Framework finnes i dette depotet under `xx-python-agent-framework` og `xx-dotnet-agent-framework` filer.

## Har du flere spørsmål om Microsoft Agent Framework?

Bli med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for å treffe andre elever, delta på kontortimer og få svar på dine spørsmål om AI-agenter.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfraskrivelse:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Det opprinnelige dokumentet i sitt originalspråk bør anses som den autoritative kilden. For kritisk informasjon anbefales profesjonell, menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår som følge av bruken av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->