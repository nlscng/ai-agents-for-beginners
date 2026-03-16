# Udforskning af Microsoft Agent Framework

![Agent Framework](../../../translated_images/da/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introduktion

Denne lektion vil dække:

- Forståelse af Microsoft Agent Framework: Nøglefunktioner og værdi  
- Udforskning af nøglebegreberne i Microsoft Agent Framework
- Sammenligning af MAF med Semantic Kernel og AutoGen: Migreringsguide

## Læringsmål

Efter at have gennemført denne lektion vil du vide, hvordan du:

- Bygger produktionsklare AI-agenter ved hjælp af Microsoft Agent Framework
- Anvender kernefunktionerne i Microsoft Agent Framework på dine agentbaserede brugssager
- Migrerer og integrerer eksisterende agentiske frameworks og værktøjer  

## Kodeeksempler 

Kodeeksempler for [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) kan findes i dette repository under filerne `xx-python-agent-framework` og `xx-dotnet-agent-framework`.

## Forståelse af Microsoft Agent Framework

![Framework Intro](../../../translated_images/da/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) bygger videre på erfaringerne og læringerne fra Semantic Kernel og AutoGen. Det tilbyder fleksibilitet til at håndtere en bred vifte af agentbaserede brugssager, der ses både i produktions- og forskningsmiljøer, herunder:

- **Sekventiel agentorkestrering** i scenarier, hvor trin-for-trin workflows er nødvendige.
- **Samtidig orkestrering** i scenarier, hvor agenter skal udføre opgaver samtidigt.
- **Gruppechat orkestrering** i scenarier, hvor agenter kan samarbejde om én opgave.
- **Overdragelsesorkestrering** i scenarier, hvor agenter afleverer opgaven til hinanden, efterhånden som delopgaverne færdiggøres.
- **Magnetisk orkestrering** i scenarier, hvor en lederagent opretter og modificerer en opgaveliste og håndterer koordineringen af underagenter for at fuldføre opgaven.

For at levere AI-agenter i produktion inkluderer MAF også funktioner for:

- **Observabilitet** gennem brug af OpenTelemetry, hvor hver handling af AI-agenten, herunder værktøjsinvokation, orkestreringstrin, ræsonnement og ydeevneovervågning via Microsoft Foundry dashboards, bliver logget.
- **Sikkerhed** ved at hoste agenter nativt på Microsoft Foundry, som inkluderer sikkerhedskontroller som rollebaseret adgang, håndtering af private data og indbygget indholdssikkerhed.
- **Holdbarhed** idet agenttråde og workflows kan pause, genoptage og komme sig efter fejl, hvilket muliggør længerevarende processer.
- **Kontrol** da menneskelig inddragelse understøttes i workflow, hvor opgaver markereres som krævende menneskelig godkendelse.

Microsoft Agent Framework fokuserer også på interoperabilitet ved at:

- **Være cloud-agnostisk** - Agenter kan køre i containere, on-premises og på tværs af flere forskellige cloud-miljøer.
- **Være leverandør-agnostisk** - Agenter kan oprettes gennem dit foretrukne SDK, inklusive Azure OpenAI og OpenAI.
- **Integrere åbne standarder** - Agenter kan anvende protokoller som Agent-to-Agent (A2A) og Model Context Protocol (MCP) til at opdage og bruge andre agenter og værktøjer.
- **Plugins og connectorer** - Forbindelser kan oprettes til data- og hukommelsestjenester som Microsoft Fabric, SharePoint, Pinecone og Qdrant.

Lad os se på, hvordan disse funktioner anvendes på nogle af kernebegreberne i Microsoft Agent Framework.

## Nøglebegreber i Microsoft Agent Framework

### Agenter

![Agent Framework](../../../translated_images/da/agent-components.410a06daf87b4fef.webp)

**Oprettelse af agenter**

Agentoprettelse sker ved at definere inferenstjenesten (LLM-udbyder), et sæt instruktioner for AI-agenten at følge og et tildelt `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Ovenstående bruger `Azure OpenAI`, men agenter kan oprettes ved hjælp af en række tjenester, herunder `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` API'er

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

eller fjernagenter ved brug af A2A-protokollen:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Kørsel af agenter**

Agenter køres ved hjælp af `.run` eller `.run_stream` metoderne for enten ikke-streaming eller streaming svar.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Hver agentkørsel kan også have indstillinger for tilpasning af parametre som `max_tokens` brugt af agenten, `tools` som agenten kan kalde og endda den model, der anvendes for agenten.

Dette er nyttigt i tilfælde, hvor specifikke modeller eller værktøjer kræves for at fuldføre brugerens opgave.

**Værktøjer**

Værktøjer kan defineres både ved oprettelsen af agenten:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Når du opretter en ChatAgent direkte

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

og også når agenten kører:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Værktøj leveret kun til denne kørsel )
```

**Agenttråde**

Agenttråde bruges til at håndtere samtaler med flere omgange. Tråde kan oprettes enten ved:

- At bruge `get_new_thread()`, som muliggør at tråden gemmes over tid
- Automatisk oprettelse af en tråd ved kørsel af en agent, hvor tråden kun varer under den aktuelle kørsel.

For at oprette en tråd ser koden sådan ud:

```python
# Opret en ny tråd.
thread = agent.get_new_thread() # Kør agenten med tråden.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Du kan derefter serialisere tråden til senere brug:

```python
# Opret en ny tråd.
thread = agent.get_new_thread() 

# Kør agenten med tråden.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serialiser tråden til lagring.

serialized_thread = await thread.serialize() 

# Deserialiser trådens tilstand efter indlæsning fra lagring.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent Middleware**

Agenter interagerer med værktøjer og LLM'er for at fuldføre brugerens opgaver. I visse scenarier ønsker vi at udføre eller spore handlinger mellem disse interaktioner. Agent middleware muliggør dette gennem:

*Funktions-Middleware*

Dette middleware giver os mulighed for at udføre en handling mellem agenten og en funktion/værktøj, som den vil kalde. Et eksempel på brug kan være at lave logning ved funktionskald.

I koden nedenfor definerer `next`, om den næste middleware eller den faktiske funktion skal kaldes.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Forbehandling: Log før funktionens udførelse
    print(f"[Function] Calling {context.function.name}")

    # Fortsæt til næste middleware eller funktionsudførelse
    await next(context)

    # Efterbehandling: Log efter funktionens udførelse
    print(f"[Function] {context.function.name} completed")
```

*Chat-Middleware*

Dette middleware giver mulighed for at udføre eller logge en handling mellem agenten og anmodningerne til LLM'en.

Det indeholder vigtig information såsom de `messages`, der sendes til AI-tjenesten.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Forbehandling: Log før AI-opkald
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Fortsæt til næste middleware eller AI-service
    await next(context)

    # Efterbehandling: Log efter AI-svar
    print("[Chat] AI response received")

```

**Agenthukommelse**

Som dækket i lektionen `Agentic Memory`, er hukommelse et vigtigt element for at gøre det muligt for agenten at operere over forskellige kontekster. MAF tilbyder flere forskellige typer hukommelser:

*In-Memory Storage*

Dette er hukommelsen, der lagres i tråde under applikationens kørsel.

```python
# Opret en ny tråd.
thread = agent.get_new_thread() # Kør agenten med tråden.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Vedvarende beskeder*

Denne hukommelse bruges til at gemme samtalehistorik på tværs af forskellige sessioner. Den defineres ved hjælp af `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Opret en brugerdefineret meddelelseslager
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamisk hukommelse*

Denne hukommelse tilføjes til konteksten, før agenterne kører. Disse hukommelser kan gemmes i eksterne tjenester som mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Brug af Mem0 til avancerede hukommelsesfunktioner
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

Observabilitet er vigtigt for at opbygge pålidelige og vedligeholdbare agentiske systemer. MAF integrerer med OpenTelemetry for at tilbyde tracing og målinger for bedre observabilitet.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # gør noget
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Workflows

MAF tilbyder workflows, som er foruddefinerede trin til at fuldføre en opgave og inkluderer AI-agenter som komponenter i disse trin.

Workflows består af forskellige komponenter, der tillader bedre styring af flow. Workflows muliggør også **multi-agent orkestrering** og **checkpointing** for at gemme workflow-tilstande.

Kernekomponenterne i et workflow er:

**Executors** 

Executors modtager indgangsbeskeder, udfører deres tildelte opgaver og producerer derefter en outputbesked. Dette bevæger workflowet fremad mod at fuldføre den større opgave. Executors kan være enten AI-agentere eller brugerdefineret logik.

**Edges**

Edges bruges til at definere flowet af beskeder i et workflow. Disse kan være:

*Direkte edges* - Enkle én-til-én forbindelser mellem executors:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Betingede edges* - Aktiveres, når en bestemt betingelse er opfyldt. For eksempel, når hotelværelser ikke er tilgængelige, kan en executor foreslå andre muligheder.

*Switch-case edges* - Ruter beskeder til forskellige executors baseret på definerede betingelser. For eksempel, hvis en rejsekunde har prioriteret adgang, håndteres deres opgaver gennem et andet workflow.

*Fan-out edges* - Sender én besked til flere mål.

*Fan-in edges* - Samler flere beskeder fra forskellige executors og sender til ét mål.

**Events**

For at tilbyde bedre observabilitet i workflows tilbyder MAF indbyggede events for eksekvering, herunder:

- `WorkflowStartedEvent`  - Workflow eksekvering starter
- `WorkflowOutputEvent` - Workflow producerer et output
- `WorkflowErrorEvent` - Workflow støder på en fejl
- `ExecutorInvokeEvent`  - Executor starter behandling
- `ExecutorCompleteEvent`  -  Executor færdiggør behandling
- `RequestInfoEvent` - En anmodning bliver foretaget

## Migration fra andre frameworks (Semantic Kernel og AutoGen)

### Forskelle mellem MAF og Semantic Kernel

**Forenklet agentoprettelse**

Semantic Kernel kræver oprettelse af en Kernel-instans for hver agent. MAF bruger en forenklet tilgang ved at anvende udvidelser for de primære udbydere.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Agent trådoprettelse**

Semantic Kernel kræver manuel oprettelse af tråde. I MAF tildeles agenten direkte en tråd.

```python
thread = agent.get_new_thread() # Kør agenten med tråden.
```

**Registrering af værktøjer**

I Semantic Kernel registreres værktøjer til Kernel, som derefter sendes til agenten. I MAF registreres værktøjer direkte under agentoprettelsesprocessen.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Forskelle mellem MAF og AutoGen

**Teams vs Workflows**

`Teams` er hændelsesstrukturen til hændelsesdrevet aktivitet med agenter i AutoGen. MAF bruger `Workflows`, som dirigerer data til executors via en grafbaseret arkitektur.

**Værktøjsoprettelse**

AutoGen bruger `FunctionTool` til at pakke funktioner, som agenter kan kalde. MAF bruger @ai_function, som fungerer på lignende vis, men også automatisk udleder skemaer for hver funktion.

**Agentadfærd**

Agenter i AutoGen er som udgangspunkt enkelt-omgangs agenter, medmindre `max_tool_iterations` sættes til en højere værdi. I MAF er `ChatAgent` som standard en multi-turn agent, hvilket betyder, at den fortsætter med at kalde værktøjer, indtil brugerens opgave er fuldført.

## Kodeeksempler 

Kodeeksempler for Microsoft Agent Framework kan findes i dette repository under filerne `xx-python-agent-framework` og `xx-dotnet-agent-framework`.

## Har du flere spørgsmål om Microsoft Agent Framework?

Deltag i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for at møde andre elever, deltage i kontortimer og få svar på dine spørgsmål om AI-agenter.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, bedes du være opmærksom på, at automatiserede oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets modersmål bør betragtes som den autoritative kilde. For kritiske oplysninger anbefales professionel menneskelig oversættelse. Vi påtager os intet ansvar for misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->