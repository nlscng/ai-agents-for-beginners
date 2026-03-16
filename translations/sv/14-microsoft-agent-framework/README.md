# Utforska Microsoft Agent Framework

![Agent Framework](../../../translated_images/sv/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introduktion

Den här lektionen täcker:

- Förstå Microsoft Agent Framework: Nyckelfunktioner och värde  
- Utforska de viktigaste koncepten i Microsoft Agent Framework
- Jämföra MAF med Semantic Kernel och AutoGen: Guide för migrering

## Lärandemål

Efter att ha genomfört denna lektion kommer du att kunna:

- Bygga produktionsklara AI-agenter med Microsoft Agent Framework
- Tillämpa kärnfunktionerna i Microsoft Agent Framework på dina agentrelaterade användningsfall
- Migrera och integrera befintliga agentramverk och verktyg  

## Kodexempel

Kodexempel för [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) finns i detta repo under filerna `xx-python-agent-framework` och `xx-dotnet-agent-framework`.

## Förstå Microsoft Agent Framework

![Framework Intro](../../../translated_images/sv/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) bygger vidare på erfarenheter och lärdomar från Semantic Kernel och AutoGen. Det erbjuder flexibiliteten att hantera en bred variation av agentbaserade användningsfall som ses både i produktion och forskningsmiljöer, inklusive:

- **Sekventiell agentorkestrering** i scenarier där steg-för-steg arbetsflöden behövs.
- **Samtida orkestrering** i scenarier där agenter måste slutföra uppgifter samtidigt.
- **Gruppchattorkestrering** i scenarier där agenter kan samarbeta tillsammans i en uppgift.
- **Överföringsorkestrering** i scenarier där agenter överlämnar uppgiften till varandra när deluppgifter är klara.
- **Magnetisk orkestrering** i scenarier där en chef-agent skapar och ändrar en uppgiftslista och hanterar samordningen av subagenter för att slutföra uppgiften.

För att leverera AI-agenter i produktion inkluderar MAF även funktioner för:

- **Observerbarhet** genom användning av OpenTelemetry där varje åtgärd från AI-agenten, inklusive verktygsanrop, orkestreringssteg, resonemangsflöden och prestandaövervakning via Microsoft Foundry-instrumentpaneler.
- **Säkerhet** genom att hosta agenter nativt på Microsoft Foundry vilket inkluderar säkerhetskontroller såsom rollbaserad åtkomst, hantering av privat data och inbyggd innehållssäkerhet.
- **Hållbarhet** eftersom agenttrådar och arbetsflöden kan pausa, återupptas och återhämta sig från fel vilket möjliggör längre körningar.
- **Kontroll** eftersom arbetsflöden med mänsklig inblandning stödjs där uppgifter markeras som kräver godkännande från människa.

Microsoft Agent Framework fokuserar också på interoperabilitet genom:

- **Molnagnostisk** - Agenter kan köras i container, lokalt och över flera olika moln.
- **Leverantörsagnostisk** - Agenter kan skapas via din föredragna SDK inklusive Azure OpenAI och OpenAI
- **Integrerar öppna standarder** - Agenter kan använda protokoll såsom Agent-to-Agent (A2A) och Model Context Protocol (MCP) för att upptäcka och använda andra agenter och verktyg.
- **Plugins och kopplingar** - Anslutningar kan skapas till data- och minnestjänster som Microsoft Fabric, SharePoint, Pinecone och Qdrant.

Låt oss se hur dessa funktioner används i några av kärnkoncepten i Microsoft Agent Framework.

## Nyckelkoncept i Microsoft Agent Framework

### Agenter

![Agent Framework](../../../translated_images/sv/agent-components.410a06daf87b4fef.webp)

**Skapa Agenter**

Agenterskapande sker genom att definiera inferenstjänsten (LLM-leverantör), en
uppsättning instruktioner för AI-agenten att följa, och ett tilldelat `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Ovan använder `Azure OpenAI` men agenter kan skapas med en rad olika tjänster inklusive `Microsoft Foundry Agent Service`:

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

eller fjärragenter med A2A-protokollet:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Köra Agenter**

Agenter körs med metoderna `.run` eller `.run_stream` för antingen icke-strömmade eller strömmade svar.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Varje agentkörning kan dessutom ha alternativ för att anpassa parametrar såsom `max_tokens` som agenten använder, `tools` som agenten kan anropa, och även själva `model` som används för agenten.

Detta är användbart i fall där specifika modeller eller verktyg krävs för att slutföra användarens uppgift.

**Verktyg**

Verktyg kan definieras både när agenten skapas:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# När du skapar en ChatAgent direkt

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

och även när agenten körs:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Verktyg tillhandahållet endast för denna körning )
```

**Agenttrådar**

Agenttrådar används för att hantera fleromgångssamtal. Trådar kan skapas antingen genom:

- Använda `get_new_thread()` som möjliggör att tråden sparas över tid
- Skapa en tråd automatiskt när agenten körs och endast ha tråden under den aktuella körningen.

Så här ser koden ut för att skapa en tråd:

```python
# Skapa en ny tråd.
thread = agent.get_new_thread() # Kör agenten med tråden.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Du kan sedan serialisera tråden för att lagra den för senare användning:

```python
# Skapa en ny tråd.
thread = agent.get_new_thread() 

# Kör agenten med tråden.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serialisera tråden för lagring.

serialized_thread = await thread.serialize() 

# Avserialisera trådtillståndet efter inläsning från lagring.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent Mellanprogram**

Agenter interagerar med verktyg och LLM:er för att slutföra användarens uppgifter. I vissa scenarier vill vi utföra eller spåra åtgärder mellan dessa interaktioner. Agent mellanprogram möjliggör detta genom:

*Funktion Mellanprogram*

Detta mellanprogram tillåter att en åtgärd körs mellan agenten och en funktion/verktyg som den kommer att anropa. Ett exempel där detta kan användas är när du vill logga funktionsanropet.

I koden nedan definierar `next` om nästa mellanprogram eller den faktiska funktionen ska anropas.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Förbehandling: Logga före funktionsutförande
    print(f"[Function] Calling {context.function.name}")

    # Fortsätt till nästa middleware eller funktionsutförande
    await next(context)

    # Efterbehandling: Logga efter funktionsutförande
    print(f"[Function] {context.function.name} completed")
```

*Chatt Mellanprogram*

Detta mellanprogram tillåter att åtgärder körs eller loggas mellan agenten och förfrågningar mellan LLM.

Detta innehåller viktig information såsom `messages` som skickas till AI-tjänsten.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Förbehandling: Logga innan AI-anrop
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Fortsätt till nästa middleware eller AI-tjänst
    await next(context)

    # Efterbehandling: Logga efter AI-svar
    print("[Chat] AI response received")

```

**Agentminne**

Som täcktes i lektionen `Agentic Memory`, är minne en viktig del för att möjliggöra att agenten arbetar över olika kontexter. MAF erbjuder flera olika typer av minnen:

*Minne i minnet (In-Memory Storage)*

Detta är minnet som lagras i trådar under applikationens körning.

```python
# Skapa en ny tråd.
thread = agent.get_new_thread() # Kör agenten med tråden.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Persistenta Meddelanden*

Detta minne används för att lagra konversationshistorik över olika sessioner. Det definieras med `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Skapa en anpassad meddelandelagring
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamiskt Minne*

Detta minne läggs till i kontexten innan agenter körs. Dessa minnen kan lagras i externa tjänster såsom mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Använder Mem0 för avancerade minnesfunktioner
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

**Agent Observerbarhet**

Observerbarhet är viktigt för att bygga pålitliga och underhållbara agentbaserade system. MAF integrerar med OpenTelemetry för att tillhandahålla spårning och mätare för bättre observabilitet.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # gör något
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Arbetsflöden

MAF erbjuder arbetsflöden som är fördefinierade steg för att slutföra en uppgift och inkluderar AI-agenter som komponenter i dessa steg.

Arbetsflöden består av olika komponenter som möjliggör bättre kontrollflöde. Arbetsflöden möjliggör också **multi-agent orkestrering** och **checkpointing** för att spara arbetsflödets status.

Kärnkomponenterna i ett arbetsflöde är:

**Exekutörer**

Exekutörer tar emot inmatningsmeddelanden, utför sina tilldelade uppgifter och producerar sedan ett utmatningsmeddelande. Detta driver arbetsflödet framåt mot att slutföra den större uppgiften. Exekutörer kan vara antingen AI-agent eller anpassad logik.

**Kanter**

Kanterna används för att definiera flödet av meddelanden i ett arbetsflöde. Dessa kan vara:

*Direkta Kanter* – Enkla en-till-en kopplingar mellan exekutörer:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Villkorade Kanter* – Aktiveras efter att ett visst villkor uppfyllts. Till exempel när hotellrum inte är tillgängliga kan en exekutör föreslå andra alternativ.

*Switch-case Kanter* – Dirigerar meddelanden till olika exekutörer baserat på definierade villkor. Till exempel om en resekund har prioriterad åtkomst och deras uppgifter hanteras via ett annat arbetsflöde.

*Fan-out Kanter* – Skickar ett meddelande till flera mål.

*Fan-in Kanter* – Samlar in flera meddelanden från olika exekutörer och skickar till ett mål.

**Händelser**

För att ge bättre observabilitet i arbetsflöden erbjuder MAF inbyggda händelser för exekvering, inklusive:

- `WorkflowStartedEvent` - Arbetsflödesexekvering börjar
- `WorkflowOutputEvent` - Arbetsflödet producerar en utdata
- `WorkflowErrorEvent` - Arbetsflödet stöter på ett fel
- `ExecutorInvokeEvent` - Exekutör börjar bearbetning
- `ExecutorCompleteEvent` - Exekutör avslutar bearbetning
- `RequestInfoEvent` - En förfrågan görs

## Migrera Från Andra Ramverk (Semantic Kernel och AutoGen)

### Skillnader mellan MAF och Semantic Kernel

**Förenklad agentskapande**

Semantic Kernel förlitar sig på skapandet av en Kernel-instans för varje agent. MAF har en förenklad metod genom att använda extensioner för huvudleverantörer.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Agenttrådsskapande**

Semantic Kernel kräver att trådar skapas manuellt. I MAF tilldelas agenten direkt en tråd.

```python
thread = agent.get_new_thread() # Kör agenten med tråden.
```

**Verktygsregistrering**

I Semantic Kernel registreras verktyg i Kernel och Kernel skickas sedan till agenten. I MAF registreras verktyg direkt under agentens skapande.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Skillnader mellan MAF och AutoGen

**Teams vs Arbetsflöden**

`Teams` är händelsestrukturen för händelsedrivna aktiviteter med agenter i AutoGen. MAF använder `Workflows` som dirigerar data till exekutörer genom en grafbaserad arkitektur.

**Verktygsskapande**

AutoGen använder `FunctionTool` för att kapsla in funktioner som agenter kan anropa. MAF använder @ai_function som fungerar liknande men som också automatiskt härleder scheman för varje funktion.

**Agentbeteende**

Agenter är enkelomgångsagenter som standard i AutoGen om inte `max_tool_iterations` sätts högre. Inom MAF är `ChatAgent` en fleromgångsagent som standard vilket innebär att den fortsätter anropa verktyg tills användarens uppgift är slutförd.

## Kodexempel

Kodexempel för Microsoft Agent Framework finns i detta repo under filerna `xx-python-agent-framework` och `xx-dotnet-agent-framework`.

## Fler frågor om Microsoft Agent Framework?

Gå med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) för att möta andra studenter, delta i öppna kontorstider och få svar på dina frågor om AI-agenter.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfriskrivning**:
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Även om vi eftersträvar noggrannhet, bör du vara medveten om att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på dess modersmål ska betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för eventuella missförstånd eller feltolkningar som uppstår vid användning av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->