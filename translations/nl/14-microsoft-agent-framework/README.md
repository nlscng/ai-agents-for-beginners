# Verkenning van Microsoft Agent Framework

![Agent Framework](../../../translated_images/nl/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Inleiding

Deze les behandelt:

- Begrip van Microsoft Agent Framework: Belangrijkste Kenmerken en Waarde  
- Verkenning van de Kernconcepten van Microsoft Agent Framework
- Vergelijking van MAF met Semantic Kernel en AutoGen: Migratiehandleiding

## Leerdoelen

Na het voltooien van deze les weet je hoe je:

- Productieklaar AI Agents bouwt met Microsoft Agent Framework
- De kernfuncties van Microsoft Agent Framework toepast op je Agent-gebaseerde gebruiksscenario's
- Bestaande Agent-frameworks en tools migreert en integreert  

## Codesamples

Codesamples voor [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) zijn te vinden in deze repository onder `xx-python-agent-framework` en `xx-dotnet-agent-framework` bestanden.

## Begrip van Microsoft Agent Framework

![Framework Intro](../../../translated_images/nl/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) bouwt voort op de ervaring en inzichten van Semantic Kernel en AutoGen. Het biedt flexibiliteit om een breed scala aan agent-gebaseerde gebruiksscenario's aan te pakken die voorkomen in zowel productie- als onderzoekomgevingen, waaronder:

- **Sequentiële Agent-orchestratie** in scenario's waar stap-voor-stap workflows nodig zijn.
- **Gelijktijdige orchestratie** in scenario's waar agents tegelijkertijd taken moeten voltooien.
- **Groepschat-orchestratie** in scenario's waar agents samen aan één taak kunnen samenwerken.
- **Handoff Orchestratie** in scenario's waar agents de taak aan elkaar overdragen na voltooiing van subtaken.
- **Magnetische Orchestratie** in scenario's waar een manager-agent een takenlijst maakt en wijzigt en de coördinatie van subagents afhandelt om de taak te voltooien.

Om AI Agents in productie te leveren, heeft MAF ook functies opgenomen voor:

- **Observeerbaarheid** via het gebruik van OpenTelemetry waarbij iedere actie van de AI Agent gevolgd wordt, inclusief tool-aanroepen, orchestratiestappen, redeneerstromen en prestatiebewaking via Microsoft Foundry dashboards.
- **Beveiliging** door agents native te hosten op Microsoft Foundry, met beveiligingscontroles zoals rolgebaseerde toegang, private data handling en ingebouwde contentveiligheid.
- **Duurzaamheid** doordat Agent-threads en workflows kunnen pauzeren, hervatten en herstellen van fouten, wat langere procesruns mogelijk maakt.
- **Controle** aangezien menselijke tussenkomst ondersteund wordt in workflows waar taken als goedkeuring door mensen worden gemarkeerd.

Microsoft Agent Framework richt zich ook op interoperabiliteit door:

- **Cloud-onafhankelijk te zijn** - Agents kunnen in containers draaien, on-premises en over meerdere clouds.
- **Provider-onafhankelijk te zijn** - Agents kunnen gemaakt worden via je favoriete SDK, waaronder Azure OpenAI en OpenAI.
- **Integratie van Open Standaarden** - Agents kunnen protocollen zoals Agent-to-Agent (A2A) en Model Context Protocol (MCP) gebruiken om andere agents en tools te ontdekken en gebruiken.
- **Plugins en Connectors** - Verbindingen kunnen gemaakt worden met data- en geheugenservices zoals Microsoft Fabric, SharePoint, Pinecone en Qdrant.

Laten we bekijken hoe deze functies worden toegepast op enkele kernconcepten van Microsoft Agent Framework.

## Kernconcepten van Microsoft Agent Framework

### Agents

![Agent Framework](../../../translated_images/nl/agent-components.410a06daf87b4fef.webp)

**Agents Maken**

Het maken van een agent gebeurt door het definiëren van de inference service (LLM Provider), een reeks instructies voor de AI Agent om te volgen, en een toegewezen `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Bovenstaand gebruikt `Azure OpenAI`, maar agents kunnen ook worden gemaakt met verschillende diensten, zoals de `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

of remote agents via het A2A-protocol:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Agents Uitvoeren**

Agents worden uitgevoerd met de `.run` of `.run_stream` methoden voor respectievelijk niet-streaming of streaming reacties.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Elke agent-run kan ook parameters hebben om aan te passen zoals `max_tokens` gebruikt door de agent, `tools` die de agent kan aanroepen, en zelfs het gebruikte `model` voor de agent.

Dit is nuttig in gevallen waar specifieke modellen of tools vereist zijn om de taak van een gebruiker te voltooien.

**Tools**

Tools kunnen worden gedefinieerd bij het maken van de agent:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Bij het direct aanmaken van een ChatAgent

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

en ook bij het uitvoeren van de agent:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Hulpmiddel alleen voor deze run beschikbaar )
```

**Agent Threads**

Agent Threads worden gebruikt om meer-gesprekstromen af te handelen. Threads kunnen worden gemaakt door:

- Gebruik te maken van `get_new_thread()` waarmee de thread over tijd kan worden opgeslagen
- Automatisch een thread te maken bij het uitvoeren van een agent waarbij de thread alleen tijdens die run bestaat.

Om een thread te maken ziet de code er als volgt uit:

```python
# Maak een nieuwe thread aan.
thread = agent.get_new_thread() # Voer de agent uit met de thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Je kunt vervolgens de thread serialiseren om later op te slaan:

```python
# Maak een nieuwe thread aan.
thread = agent.get_new_thread() 

# Voer de agent uit met de thread.

response = await agent.run("Hello, how are you?", thread=thread) 

# Seriëleer de thread voor opslag.

serialized_thread = await thread.serialize() 

# Deserialiseer de threadstatus na het laden uit opslag.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent Middleware**

Agents communiceren met tools en LLM's om taken voor gebruikers te voltooien. In bepaalde scenario's willen we acties uitvoeren of volgen tussen deze interacties. Agent middleware maakt dit mogelijk via:

*Function Middleware*

Deze middleware maakt het mogelijk een actie uit te voeren tussen de agent en een functie/tool die wordt aangeroepen. Bijvoorbeeld om logging te doen bij een functieroep.

In onderstaande code bepaalt `next` of de volgende middleware of de daadwerkelijke functie wordt aangeroepen.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Voorbewerking: Log voor het uitvoeren van de functie
    print(f"[Function] Calling {context.function.name}")

    # Ga door naar de volgende middleware of functie-uitvoering
    await next(context)

    # Nabewerking: Log na het uitvoeren van de functie
    print(f"[Function] {context.function.name} completed")
```

*Chat Middleware*

Deze middleware maakt het mogelijk een actie uit te voeren of te loggen tussen de agent en de verzoeken naar de LLM.

Het bevat belangrijke informatie zoals de `messages` die naar de AI-service worden gestuurd.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Voorverwerking: Loggen voor AI-aanroep
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Ga verder naar de volgende middleware of AI-service
    await next(context)

    # Naverwerking: Loggen na AI-respons
    print("[Chat] AI response received")

```

**Agent Geheugen**

Zoals behandeld in de les `Agentic Memory`, is geheugen een belangrijk element om de agent te laten opereren over verschillende contexten. MAF biedt verschillende types geheugen:

*In-Memory Opslag*

Dit is het geheugen dat is opgeslagen in threads tijdens de runtime van de applicatie.

```python
# Maak een nieuwe thread aan.
thread = agent.get_new_thread() # Voer de agent uit met de thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Persistent Messages*

Dit geheugen wordt gebruikt voor het opslaan van gesprekshistorie over verschillende sessies. Het wordt gedefinieerd via de `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Maak een aangepaste berichtopslag
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamisch Geheugen*

Dit geheugen wordt toegevoegd aan de context voordat agents worden uitgevoerd. Dit geheugen kan worden opgeslagen in externe services zoals mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Mem0 gebruiken voor geavanceerde geheugencapaciteiten
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

**Agent Observeerbaarheid**

Observeerbaarheid is belangrijk om betrouwbare en onderhoudbare agent-systemen te bouwen. MAF integreert met OpenTelemetry om tracing en meters te bieden voor betere observeerbaarheid.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # doe iets
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Workflows

MAF biedt workflows die vooraf gedefinieerde stappen zijn om een taak te voltooien en AI agents als componenten in die stappen omvatten.

Workflows bestaan uit verschillende componenten die betere controle over de flow bieden. Workflows maken ook **multi-agent orchestratie** en **checkpointing** mogelijk om workflowstatussen op te slaan.

De kerncomponenten van een workflow zijn:

**Executors**

Executors ontvangen invoermeldingen, voeren de toegewezen taken uit en produceren daarna een uitvoermelding. Dit brengt de workflow vooruit naar het voltooien van de grotere taak. Executors kunnen AI agents zijn of aangepaste logica.

**Edges**

Edges worden gebruikt om de flow van berichten in een workflow te definiëren. Dit kan zijn:

*Directe Edges* - Eenvoudige een-op-een verbindingen tussen executors:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Conditionele Edges* - Actief nadat aan een bepaalde voorwaarde is voldaan. Bijvoorbeeld wanneer hotelkamers niet beschikbaar zijn, kan een executor andere opties voorstellen.

*Switch-case Edges* - Routeert berichten naar verschillende executors op basis van gedefinieerde voorwaarden. Bijvoorbeeld als een reisgebruiker prioriteitstoegang heeft en zijn taken via een andere workflow worden afgehandeld.

*Fan-out Edges* - Stuurt één bericht naar meerdere doelen.

*Fan-in Edges* - Verzamelt meerdere berichten van verschillende executors en stuurt naar één doel.

**Events**

Om betere observeerbaarheid van workflows te bieden, biedt MAF ingebouwde gebeurtenissen voor uitvoering, waaronder:

- `WorkflowStartedEvent`  - Workflowuitvoering begint
- `WorkflowOutputEvent` - Workflow produceert een output
- `WorkflowErrorEvent` - Workflow ondervindt een fout
- `ExecutorInvokeEvent`  - Executor begint met verwerken
- `ExecutorCompleteEvent`  - Executor voltooit verwerken
- `RequestInfoEvent` - Een verzoek wordt gedaan

## Migreren van Andere Frameworks (Semantic Kernel en AutoGen)

### Verschillen tussen MAF en Semantic Kernel

**Vereenvoudigde Agentcreatie**

Semantic Kernel vereist het maken van een Kernel-instantie voor elke agent. MAF gebruikt een vereenvoudigde aanpak door extensies te gebruiken voor de hoofdproviders.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Agent Thread Creatie**

Semantic Kernel vereist dat threads handmatig worden aangemaakt. In MAF krijgt de agent direct een toegewezen thread.

```python
thread = agent.get_new_thread() # Voer de agent uit met de thread.
```

**Tool Registratie**

In Semantic Kernel worden tools geregistreerd bij de Kernel en wordt de Kernel doorgegeven aan de agent. In MAF worden tools direct geregistreerd tijdens het maken van de agent.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Verschillen tussen MAF en AutoGen

**Teams versus Workflows**

`Teams` zijn de eventstructuur voor event-gedreven activiteiten met agents in AutoGen. MAF gebruikt `Workflows` die data routeren naar executors via een graf-gebaseerde architectuur.

**Tool Creatie**

AutoGen gebruikt `FunctionTool` om functies te wikkelen die agents kunnen aanroepen. MAF gebruikt @ai_function die vergelijkbaar werkt, maar ook automatisch de schema's voor elke functie afleidt.

**Agent Gedrag**

Agents zijn standaard single-turn in AutoGen, tenzij `max_tool_iterations` hoger wordt gezet. Binnen MAF is de `ChatAgent` standaard multi-turn, wat betekent dat hij tools blijft aanroepen tot de taak van de gebruiker voltooid is.

## Codesamples

Codesamples voor Microsoft Agent Framework zijn te vinden in deze repository onder `xx-python-agent-framework` en `xx-dotnet-agent-framework` bestanden.

## Meer Vragen over Microsoft Agent Framework?

Word lid van de [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) om andere lerenden te ontmoeten, aanwezig te zijn bij kantooruren en je vragen over AI Agents beantwoord te krijgen.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dit document is vertaald met behulp van de AI-vertalingsdienst [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel we streven naar nauwkeurigheid, dient u er rekening mee te houden dat automatische vertalingen fouten of onjuistheden kunnen bevatten. Het originele document in de oorspronkelijke taal moet als het gezaghebbende document worden beschouwd. Voor cruciale informatie wordt professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->