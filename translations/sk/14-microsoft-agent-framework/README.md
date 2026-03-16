# Preskúmanie Microsoft Agent Framework

![Agent Framework](../../../translated_images/sk/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Úvod

Táto lekcia pokryje:

- Pochopenie Microsoft Agent Framework: Kľúčové vlastnosti a hodnota  
- Preskúmanie kľúčových konceptov Microsoft Agent Framework
- Porovnanie MAF so Semantic Kernel a AutoGen: Sprievodca migráciou

## Ciele učenia

Po dokončení tejto lekcie budete vedieť, ako:

- Vytvárať produkčne pripravené AI agentov pomocou Microsoft Agent Framework
- Použiť základné funkcie Microsoft Agent Framework vo vašich agentických scenároch
- Migrovať a integrovať existujúce agentické rámce a nástroje  

## Ukážky kódu

Ukážky kódu pre [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) nájdete v tomto repozitári v súboroch `xx-python-agent-framework` a `xx-dotnet-agent-framework`.

## Pochopenie Microsoft Agent Framework

![Framework Intro](../../../translated_images/sk/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) nadväzuje na skúsenosti a poznatky zo Semantic Kernel a AutoGen. Ponúka flexibilitu na riešenie širokej škály agentických prípadov použitia v produkčnom a výskumnom prostredí, vrátane:

- **Sekvenčnej orchestrácie agentov** v scenároch, kde sú potrebné pracovné postupy krok za krokom.
- **Súbežnej orchestrácie** v scenároch, kde agenti musia dokončiť úlohy súčasne.
- **Orchestrácie skupinového chatu** v scenároch, kde agenti môžu spolupracovať na jednej úlohe.
- **Odovzdávacej orchestrácie** v scenároch, kde si agenti medzi sebou odovzdávajú úlohu, keď sú podúlohy dokončené.
- **Magnetickej orchestrácie** v scenároch, kde správcovský agent tvorí a mení zoznam úloh a riadi koordináciu podagentov na dokončenie úlohy.

Pre dodanie AI agentov v produkcii MAF tiež obsahuje funkcie pre:

- **Pozorovateľnosť** prostredníctvom použitia OpenTelemetry, kde každá akcia AI agenta vrátane volania nástrojov, orchestrácie krokov, logického toku a monitorovania výkonu cez Microsoft Foundry dashboardy.
- **Bezpečnosť** hosťovaním agentov natívne na Microsoft Foundry, čo zahŕňa bezpečnostné kontroly ako prístup na základe rolí, spracovanie súkromných dát a zabudovanú bezpečnosť obsahu.
- **Trvácnosť** pretože vlákna a pracovné postupy agenta môžu byť pozastavené, obnovené a zotaviť sa z chýb, čo umožňuje dlhšie bežiace procesy.
- **Kontrolu** ako sú podporené pracovné postupy s človekom v slučke, kde sú úlohy označené ako vyžadujúce schválenie človekom.

Microsoft Agent Framework je tiež zameraný na interoperabilitu tým, že:

- **Je nezávislý od cloudu** - agenti môžu bežať v kontajneroch, on-premise a naprieč viacerými rôznymi cloudmi.
- **Je nezávislý od poskytovateľa** - agenti môžu byť vytváraní prostredníctvom vášho preferovaného SDK vrátane Azure OpenAI a OpenAI
- **Integruje otvorené štandardy** - agenti môžu využívať protokoly ako Agent-to-Agent (A2A) a Model Context Protocol (MCP) na objavovanie a používanie iných agentov a nástrojov.
- **Pluginy a konektory** - pripojenia môžu byť vytvorené k dátovým a pamäťovým službám ako Microsoft Fabric, SharePoint, Pinecone a Qdrant.

Pozrime sa, ako sa tieto funkcie aplikujú na niektoré zo základných konceptov Microsoft Agent Framework.

## Kľúčové koncepty Microsoft Agent Framework

### Agenti

![Agent Framework](../../../translated_images/sk/agent-components.410a06daf87b4fef.webp)

**Vytváranie agentov**

Vytvorenie agenta sa vykonáva definovaním inferenčnej služby (poskytovateľ LLM), súboru inštrukcií, ktoré má AI agent nasledovať, a priradením `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Vyššie uvedené používa `Azure OpenAI`, ale agenti môžu byť vytvorení pomocou rôznych služieb vrátane `Microsoft Foundry Agent Service`:

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

alebo vzdialení agenti používajúci protokol A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Spúšťanie agentov**

Agenti sa spúšťajú pomocou metód `.run` alebo `.run_stream` pre nereálne alebo streamované odpovede.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Každé spustenie agenta môže mať aj voľby na prispôsobenie parametrov ako `max_tokens` používaných agentom, `tools`, ktoré agent môže volať, a dokonca aj samotný `model` použitý agentom.

To je užitočné v prípadoch, kde sú pre splnenie používateľovej úlohy potrebné určité modely alebo nástroje.

**Nástroje**

Nástroje môžu byť definované pri definovaní agenta:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Pri priamej tvorbe ChatAgenta

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

a tiež pri spúšťaní agenta:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Nástroj poskytnutý iba pre tento beh )
```

**Vlákna agenta**

Vlákna agenta sa používajú na spracovanie viackolových konverzácií. Vlákna môžu byť vytvorené buď:

- Použitím `get_new_thread()` čo umožňuje vlákno ukladať v čase
- Automatickým vytvorením vlákna pri spúšťaní agenta, pričom vlákno trvá iba počas aktuálneho spustenia.

Na vytvorenie vlákna vyzerá kód takto:

```python
# Vytvorte nový vlákno.
thread = agent.get_new_thread() # Spustite agenta s vláknom.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Môžete potom serializovať vlákno na jeho uloženie na neskoršie použitie:

```python
# Vytvorte novú vlákno.
thread = agent.get_new_thread() 

# Spustite agenta s vláknom.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serializujte vlákno na uloženie.

serialized_thread = await thread.serialize() 

# Deserializujte stav vlákna po načítaní z úložiska.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware agenta**

Agenti komunikujú s nástrojmi a LLM, aby dokončili používateľské úlohy. V určitých situáciách chceme vykonať alebo sledovať akcie medzi týmito interakciami. Middleware agenta nám to umožňuje pomocou:

*Funkčný middleware*

Tento middleware umožňuje vykonať akciu medzi agentom a funkciou/nástrojom, ktorý bude volať. Príklad použitia je napríklad zaznamenávanie volania funkcie.

V kóde nižšie `next` definuje, či má byť zavolaný ďalší middleware alebo skutočná funkcia.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Predspracovanie: Zaznamenať pred vykonaním funkcie
    print(f"[Function] Calling {context.function.name}")

    # Pokračovať na ďalší middleware alebo vykonanie funkcie
    await next(context)

    # Následné spracovanie: Zaznamenať po vykonaní funkcie
    print(f"[Function] {context.function.name} completed")
```

*Chat middleware*

Tento middleware umožňuje vykonať alebo zaznamenať akciu medzi agentom a požiadavkami medzi LLM.

Obsahuje dôležité informácie ako správy `messages`, ktoré sú posielané AI službe.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Predspracovanie: Zaznamenať pred volaním AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Pokračovať na ďalší middleware alebo AI službu
    await next(context)

    # Postspracovanie: Zaznamenať po odpovedi AI
    print("[Chat] AI response received")

```

**Pamäť agenta**

Ako sme pokryli v lekcii `Agentic Memory`, pamäť je dôležitý prvok na umožnenie agenta operovať v rôznom kontexte. MAF ponúka niekoľko rôznych typov pamätí:

*Pamäť v pamäti (In-Memory Storage)*

Toto je pamäť uložená vo vláknach počas behu aplikácie.

```python
# Vytvorte nový vlákn.
thread = agent.get_new_thread() # Spustite agenta s vláknom.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Trvácne správy (Persistent Messages)*

Táto pamäť sa používa na ukladanie histórie konverzácie naprieč rôznymi reláciami. Definuje sa pomocou `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Vytvorte vlastné úložisko správ
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamická pamäť*

Táto pamäť sa pridáva do kontextu pred spustením agentov. Tieto pamäte môžu byť uložené v externých službách, ako je mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Použitie Mem0 pre pokročilé pamäťové schopnosti
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

**Pozorovateľnosť agenta**

Pozorovateľnosť je dôležitá pre vytváranie spoľahlivých a udržiavateľných agentických systémov. MAF sa integruje s OpenTelemetry na poskytovanie trasovania a meradiel pre lepšiu pozorovateľnosť.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # urob niečo
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Pracovné postupy

MAF ponúka pracovné postupy, ktoré sú preddefinované kroky na dokončenie úlohy a zahŕňajú AI agentov ako komponenty týchto krokov.

Pracovné postupy sa skladajú z rôznych komponentov, ktoré umožňujú lepšiu kontrolu toku. Tiež umožňujú **multi-agent orchestráciu** a **checkpointing** na uloženie stavov pracovného procesu.

Základné komponenty pracovného procesu sú:

**Výkonníky (Executors)**

Výkonníci prijímajú vstupné správy, vykonávajú priradené úlohy a potom produkujú výstupnú správu. Tým posúvajú pracovný postup smerom k dokončeniu väčšej úlohy. Výkonníci môžu byť AI agenti alebo vlastná logika.

**Hrany (Edges)**

Hrany sa používajú na definovanie toku správ v pracovnom procese. Môžu byť:

*Priame hrany* - jednoduché jedno-na-jedno spojenia medzi výkonníkmi:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Podmienené hrany* - aktivujú sa po splnení určitej podmienky. Napríklad, keď nie sú dostupné hotelové izby, výkonník môže navrhnúť iné možnosti.

*Switch-case hrany* - smerujú správy k rôznym výkonníkom na základe definovaných podmienok. Napríklad ak má cestovateľ prioritu, jeho úlohy budú spracované inom pracovnom procese.

*Fan-out hrany* - posielajú jednu správu viacerým cieľom.

*Fan-in hrany* - zbierajú viacero správ od rôznych výkonníkov a posielajú ich jednému cieľu.

**Udalosti**

Aby sa zlepšila pozorovateľnosť pracovných postupov, MAF ponúka zabudované udalosti počas vykonávania vrátane:

- `WorkflowStartedEvent`  - začiatok vykonávania pracovného postupu
- `WorkflowOutputEvent` - pracovný postup produkuje výstup
- `WorkflowErrorEvent` - pracovný postup narazí na chybu
- `ExecutorInvokeEvent`  - výkonník začína spracovávanie
- `ExecutorCompleteEvent`  - výkonník dokončuje spracovanie
- `RequestInfoEvent` - je vydaná požiadavka

## Migrácia z iných rámcov (Semantic Kernel a AutoGen)

### Rozdiely medzi MAF a Semantic Kernel

**Zjednodušené vytváranie agentov**

Semantic Kernel vyžaduje vytvorenie inštancie Kernel pre každého agenta. MAF používa zjednodušený prístup pomocou rozšírení pre hlavných poskytovateľov.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Vytváranie vlákien agenta**

Semantic Kernel vyžaduje manuálne vytváranie vlákien. V MAF je priamo agentovi priradené vlákno.

```python
thread = agent.get_new_thread() # Spustiť agenta s vláknom.
```

**Registrácia nástrojov**

V Semantic Kernel sú nástroje registrované v Kernel a Kernel je potom odovzdaný agentovi. V MAF sa nástroje registrujú priamo počas procesu tvorby agenta.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Rozdiely medzi MAF a AutoGen

**Tímy vs Pracovné postupy**

`Teams` sú štruktúra udalostí pre event-driven aktivity s agentmi v AutoGen. MAF používa `Workflows`, ktoré smerujú dáta k výkonníkom cez architektúru založenú na grafe.

**Vytváranie nástrojov**

AutoGen používa `FunctionTool` na zabalenie funkcií pre volanie agentmi. MAF používa @ai_function, ktorý funguje podobne a zároveň automaticky odvádza schémy pre každú funkciu.

**Správanie agenta**

Agenti sú v AutoGen predvolene jedno-koloví, pokiaľ nie je nastavené `max_tool_iterations` na vyššiu hodnotu. V MAF je `ChatAgent` predvolene viac-kolový, čo znamená, že bude pokračovať v volaní nástrojov, kým nie je používateľova úloha dokončená.

## Ukážky kódu

Ukážky kódu pre Microsoft Agent Framework nájdete v tomto repozitári v súboroch `xx-python-agent-framework` a `xx-dotnet-agent-framework`.

## Máte ďalšie otázky o Microsoft Agent Framework?

Pridajte sa do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kde sa môžete stretnúť s ďalšími študentmi, zúčastniť sa konzultačných hodín a získať odpovede na vaše otázky o AI agentoch.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vyhlásenie o vylúčení zodpovednosti**:
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Aj keď sa snažíme o presnosť, majte prosím na pamäti, že automatické preklady môžu obsahovať chyby alebo nepresnosti. Pôvodný dokument v jeho materskom jazyku by mal byť považovaný za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny ľudský preklad. Za akékoľvek nepochopenia alebo nesprávne interpretácie vyplývajúce z použitia tohto prekladu nezodpovedáme.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->