# Průzkum rámce Microsoft Agent

![Agent Framework](../../../translated_images/cs/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Úvod

Tato lekce pokryje:

- Pochopení rámce Microsoft Agent: Klíčové funkce a hodnota  
- Prozkoumání klíčových konceptů rámce Microsoft Agent
- Srovnání MAF s Semantic Kernel a AutoGen: Průvodce migrací

## Cíle učení

Po dokončení této lekce budete umět:

- Vytvářet AI agenty připravené k produkci pomocí rámce Microsoft Agent
- Aplikovat základní funkce rámce Microsoft Agent na vaše agentní scénáře
- Migrovat a integrovat existující agentní rámce a nástroje  

## Ukázky kódu

Ukázky kódu pro [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) naleznete v tomto repozitáři pod soubory `xx-python-agent-framework` a `xx-dotnet-agent-framework`.

## Pochopení rámce Microsoft Agent

![Framework Intro](../../../translated_images/cs/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) staví na zkušenostech a poznatcích z Semantic Kernel a AutoGen. Nabízí flexibilitu pro řešení široké škály agentních scénářů viděných jak v produkčních, tak ve výzkumných prostředích, včetně:

- **Sekvenční orchestrace agentů** v situacích, kde jsou potřeba krok za krokem pracovní postupy.
- **Současná orchestrace** v situacích, kdy agenti musí dokončit úkoly současně.
- **Orchestrace skupinového chatu** v situacích, kdy agenti mohou spolupracovat na jednom úkolu.
- **Orchestrace předávání** v situacích, kdy si agenti předávají úkol, jak jsou jednotlivé dílčí úkoly dokončeny.
- **Magnetická orchestrace** v situacích, kdy manažerský agent vytváří a upravuje seznam úkolů a koordinuje podřízené agenty k dokončení úkolu.

Pro doručení AI agentů v produkci má MAF také zahrnuté funkce pro:

- **Pozorovatelnost** pomocí OpenTelemetry, kde každá akce AI agenta včetně vyvolání nástroje, kroků orchestrace, toků uvažování a monitorování výkonu přes Microsoft Foundry dashboardy je sledována.
- **Bezpečnost** hostováním agentů nativně na Microsoft Foundry, které zahrnuje bezpečnostní kontroly jako řízení přístupu na základě rolí, ochranu soukromých dat a vestavěnou bezpečnost obsahu.
- **Odolnost** protože agentní vlákna a pracovní postupy mohou být pozastaveny, obnoveny a zotaveny z chyb, což umožňuje dlouhodobé procesy.
- **Kontrolu** protože jsou podporovány pracovní toky s lidským zásahem, kde jsou úkoly označeny jako vyžadující lidské schválení.

Microsoft Agent Framework se také zaměřuje na interoperabilitu tím, že:

- **Je nezávislý na cloudu** – agenti mohou běžet v kontejnerech, lokálně i napříč různými cloudy.
- **Je nezávislý na poskytovateli** – agenti mohou být vytvořeni pomocí vámi preferovaného SDK včetně Azure OpenAI a OpenAI
- **Integruje otevřené standardy** – agenti mohou využívat protokoly jako Agent-to-Agent (A2A) a Model Context Protocol (MCP) k vyhledávání a využívání jiných agentů a nástrojů.
- **Pluginy a konektory** – lze navazovat spojení k datovým a paměťovým službám jako Microsoft Fabric, SharePoint, Pinecone a Qdrant.

Podívejme se, jak jsou tyto funkce aplikovány na některé základní koncepty rámce Microsoft Agent.

## Klíčové koncepty rámce Microsoft Agent

### Agenti

![Agent Framework](../../../translated_images/cs/agent-components.410a06daf87b4fef.webp)

**Vytváření agentů**

Vytvoření agenta se provádí definováním inferenční služby (poskytovatel LLM), sady instrukcí, které má AI agent následovat, a přiřazením `jména`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```
  
Výše uvedený příklad používá `Azure OpenAI`, ale agenti mohou být vytvářeni pomocí různých služeb včetně `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```
  
OpenAI `Responses`, `ChatCompletion` API

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```
  
```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```
  
nebo vzdálených agentů používajících protokol A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```
  
**Spouštění agentů**

Agent se spouští pomocí metod `.run` nebo `.run_stream`, a to buď pro ne-streamingové, nebo streamingové odpovědi.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```
  
```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```
  
Každé spuštění agenta může mít také možnosti pro přizpůsobení parametrů jako `max_tokens`, které agent používá, `tools` (nástroje), které agent může volat, a dokonce i samotný `model` použitý agentem.

To je užitečné v případech, kdy jsou pro dokončení úkolu uživatele vyžadovány specifické modely nebo nástroje.

**Nástroje**

Nástroje lze definovat jak při definování agenta:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Při přímém vytváření ChatAgenta

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```
  
tak i při spuštění agenta:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Nástroj poskytovaný pouze pro tento běh )
```
  
**Vlákna agentů**

Vlákna agentů slouží k vedení víceturnových konverzací. Vlákna lze vytvořit buď:

- Použitím `get_new_thread()`, který umožňuje vlákno časem uložit
- Automatickým vytvořením vlákna během spuštění agenta, přičemž vlákno existuje pouze během aktuálního spuštění.

Pro vytvoření vlákna vypadá kód takto:

```python
# Vytvořit nové vlákno.
thread = agent.get_new_thread() # Spusťte agenta s vláknem.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```
  
Vlákno můžete následně serializovat a uložit pro pozdější použití:

```python
# Vytvořte nový vlákno.
thread = agent.get_new_thread() 

# Spusťte agenta s vláknen.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serializujte vlákno pro uložení.

serialized_thread = await thread.serialize() 

# Deserializujte stav vlákna po načtení z úložiště.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```
  
**Prostředníci agenta**

Agenti interagují s nástroji a LLM k dokončení úkolů uživatelů. V určitých scénářích chceme mezi těmito interakcemi provádět nebo sledovat akce. Prostředníci agentů nám to umožňují prostřednictvím:

*Funkčního prostředníka*

Tento prostředník nám umožňuje provádět akci mezi agentem a funkcí/nástrojem, který agent volá. Příklad použití je, když chcete zaznamenat volání funkce (logování).

V níže uvedeném kódu `next` definuje, zda se má zavolat další prostředník nebo skutečná funkce.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Předzpracování: Zaznamenejte před vykonáním funkce
    print(f"[Function] Calling {context.function.name}")

    # Pokračujte k dalšímu middleware nebo vykonání funkce
    await next(context)

    # Pozpracování: Zaznamenejte po vykonání funkce
    print(f"[Function] {context.function.name} completed")
```
  
*Chat prostředníka*

Tento prostředník umožňuje provádět nebo zaznamenávat akci mezi agentem a požadavky mezi LLM.

Obsahuje důležité informace jako `messages`, které jsou odesílány AI službě.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Předzpracování: Protokol před voláním AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Pokračujte k dalšímu middleware nebo AI službě
    await next(context)

    # Následné zpracování: Protokol po odpovědi AI
    print("[Chat] AI response received")

```
  
**Paměť agenta**

Jak bylo rozebráno v lekci `Agentic Memory`, paměť je důležitým prvkem umožňujícím agentovi pracovat v různých kontextech. MAF nabízí několik různých typů paměti:

*Paměť v rámci běhu aplikace*

Toto je paměť uchovávaná ve vláknech během běhu aplikace.

```python
# Vytvořte nový vlákno.
thread = agent.get_new_thread() # Spusťte agenta s vláknem.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```
  
*Perzistentní zprávy*

Tato paměť se používá pro ukládání historie konverzací napříč různými relacemi. Definuje se pomocí `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Vytvořit vlastní úložiště zpráv
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```
  
*Dynamická paměť*

Tato paměť je přidána do kontextu před spuštěním agentů. Tyto paměti mohou být uloženy v externích službách jako mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Použití Mem0 pro pokročilé paměťové schopnosti
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
  
**Pozorovatelnost agenta**

Pozorovatelnost je důležitá pro vytváření spolehlivých a udržitelných agentních systémů. MAF integruje OpenTelemetry pro poskytování trasování a metrik pro lepší pozorovatelnost.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # udělej něco
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```
  
### Pracovní postupy

MAF nabízí pracovní postupy, což jsou předdefinované kroky k dokončení úkolu a zahrnují AI agenty jako součást těchto kroků.

Pracovní postupy jsou složeny z různých komponent, které umožňují lepší řízení toku. Pracovní postupy také umožňují **multi-agentní orchestrace** a **využívaní checkpointů** pro ukládání stavů pracovního postupu.

Základními komponentami pracovního postupu jsou:

**Spouštěče (Executors)**

Spouštěče přijímají vstupní zprávy, provádějí přiřazené úkoly a poté generují výstupní zprávu. Posouvají tak pracovní postup směrem k dokončení většího úkolu. Spouštěče mohou být agenti AI nebo vlastní logika.

**Hrany (Edges)**

Hrany definují tok zpráv v pracovním postupu. Mohou být:

*Přímé hrany* – jednoduchá jedno-na-jedno spojení mezi spouštěči:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```
  
*Podmíněné hrany* – aktivují se po splnění určité podmínky. Například když nejsou k dispozici hotelové pokoje, může spouštěč navrhnout jiné možnosti.

*Switch-case hrany* – směrují zprávy k různým spouštěčům na základě definovaných podmínek. Například pokud má cestující prioritní přístup, jeho úkoly budou zpracovávány jiným pracovním postupem.

*Fan-out hrany* – odesílají jednu zprávu na více cílů.

*Fan-in hrany* – shromažďují více zpráv od různých spouštěčů a posílají je jednomu cíli.

**Události**

Pro lepší pozorovatelnost pracovních postupů nabízí MAF vestavěné události provedení včetně:

- `WorkflowStartedEvent` – spuštění pracovního postupu
- `WorkflowOutputEvent` – pracovní postup produkuje výstup
- `WorkflowErrorEvent` – pracovní postup má chybu
- `ExecutorInvokeEvent` – spouštěč začíná zpracovávat
- `ExecutorCompleteEvent` – spouštěč dokončil zpracování
- `RequestInfoEvent` – byl odeslán požadavek

## Migrace z jiných rámců (Semantic Kernel a AutoGen)

### Rozdíly mezi MAF a Semantic Kernel

**Zjednodušené vytváření agentů**

Semantic Kernel vyžaduje vytvoření instance Kernel pro každého agenta. MAF používá zjednodušený přístup pomocí rozšíření pro hlavní poskytovatele.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```
  
**Vytváření vláken agentů**

Semantic Kernel vyžaduje ruční vytváření vláken. V MAF je vláknu přímo přiřazen agent.

```python
thread = agent.get_new_thread() # Spusťte agenta s vláknem.
```
  
**Registrace nástrojů**

V Semantic Kernel jsou nástroje registrovány do Kernel, který je pak předán agentovi. V MAF jsou nástroje registrovány přímo během vytváření agenta.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```
  
### Rozdíly mezi MAF a AutoGen

**Týmy vs Pracovní postupy**

`Teams` jsou struktura událostí pro událostmi řízenou aktivitu s agenty v AutoGen. MAF využívá `Workflows`, které směrují data ke spouštěčům přes grafovou architekturu.

**Vytváření nástrojů**

AutoGen používá `FunctionTool` k zabalení funkcí, které agenti volají. MAF používá @ai_function, která funguje podobně, ale také automaticky odvozuje schémata pro každou funkci.

**Chování agentů**

Agenti jsou v AutoGen ve výchozím nastavení jednokoloví, pokud není `max_tool_iterations` nastaveno na vyšší hodnotu. V MAF je `ChatAgent` ve výchozím nastavení vícekrokový, což znamená, že bude nadále volat nástroje, dokud úkol uživatele nebude dokončen.

## Ukázky kódu

Ukázky kódu pro Microsoft Agent Framework naleznete v tomto repozitáři pod soubory `xx-python-agent-framework` a `xx-dotnet-agent-framework`.

## Máte další otázky ohledně Microsoft Agent Framework?

Připojte se k [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), setkejte se s ostatními studenty, účastněte se konzultací a získejte odpovědi na své otázky ohledně AI agentů.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Upozornění**:  
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). Přestože usilujeme o přesnost, mějte prosím na paměti, že automatizované překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho mateřském jazyce by měl být považován za autoritativní zdroj. Pro kritické informace se doporučuje profesionální lidský překlad. Nejsme odpovědní za jakákoliv nedorozumění nebo chybné výklady vyplývající z použití tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->