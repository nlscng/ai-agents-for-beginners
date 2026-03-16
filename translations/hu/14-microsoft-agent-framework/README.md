# Microsoft Agent Framework felfedezése

![Agent Keretrendszer](../../../translated_images/hu/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Bevezetés

Ez a lecke a következőket fogja áttekinteni:

- A Microsoft Agent Framework megértése: kulcsjellemzők és érték  
- A Microsoft Agent Framework kulcsfogalmainak feltérképezése
- MAF összehasonlítása a Semantic Kernel és az AutoGen keretrendszerekkel: Migrációs útmutató

## Tanulási célok

A lecke elvégzése után tudni fogod, hogyan kell:

- Termelésre kész AI ügynököket építeni a Microsoft Agent Framework használatával
- Alkalmazni a Microsoft Agent Framework alapvető funkcióit az ügynöki use case-ekre
- Migrálni és integrálni meglévő ügynöki keretrendszereket és eszközöket  

## Kódpéldák

A [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) kódpéldái megtalálhatók ebben a tárolóban a `xx-python-agent-framework` és a `xx-dotnet-agent-framework` fájlok alatt.

## A Microsoft Agent Framework megértése

![Keretrendszer bemutatása](../../../translated_images/hu/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) a Semantic Kernel és az AutoGen tapasztalataira és tanulságaira épít. Rugalmasságot kínál a különféle ügynöki use case-ek kezelésére mind termelési, mind kutatási környezetben, többek között:

- **Szekvenciális ügynökorchesztráció** olyan scenáriókban, ahol lépésről lépésre történő munkafolyamatokra van szükség.
- **Egyidejű orchesztráció** olyan esetekben, ahol az ügynököknek egyszerre kell elvégezniük feladatokat.
- **Csoportos csevegés-orchesztráció** olyan helyzetekben, ahol az ügynökök együttműködnek egy feladaton.
- **Átadás-orchesztráció** olyan scenáriókban, ahol az ügynökök átadják egymásnak a feladatot, ahogy az alfeladatok elkészülnek.
- **Mágneses orchesztráció** olyan esetekre, ahol egy menedzser ügynök létrehoz és módosít egy feladatlistát, és koordinálja az alügynököket a feladat teljesítéséhez.

Az AI ügynökök termelési bevezetéséhez a MAF további funkciókat is tartalmaz:

- **Megfigyelhetőség** OpenTelemetry használatával, ahol az AI ügynök minden műveletét nyomon lehet követni, beleértve az eszközhívásokat, orchesztrációs lépéseket, érvelési folyamatokat és teljesítményfigyelést a Microsoft Foundry irányítópultjain keresztül.
- **Biztonság** azáltal, hogy az ügynököket natívan a Microsoft Foundry-ban lehet futtatni, amely olyan biztonsági vezérlőket tartalmaz, mint a szerepalapú hozzáférés, privát adatkezelés és beépített tartalombiztonság.
- **Tartósság** mivel az ügynök szálak és munkafolyamatok szüneteltethetők, folytathatók és hibatűrően helyreállíthatók, ami hosszabb futású folyamatokat tesz lehetővé.
- **Irányítás** ember a hurkon (human-in-the-loop) munkafolyamatok támogatásával, ahol a feladatok emberi jóváhagyást igénylőként jelölhetők meg.

A Microsoft Agent Framework interoperábilisra is törekszik:

- **Felhőfüggetlen** - Az ügynökök konténerekben, helyben és több különböző felhőn keresztül is futhatnak.
- **Szolgáltatófüggetlen** - Az ügynökök létrehozhatók a kedvenc SDK-don keresztül, beleértve az Azure OpenAI és OpenAI szolgáltatásokat.
- **Nyílt szabványok integrálása** - Az ügynökök olyan protokollokat használhatnak, mint az Agent-to-Agent (A2A) és a Model Context Protocol (MCP), hogy felfedezzék és használják a többi ügynököt és eszközt.
- **Bővítmények és csatlakozók** - Kapcsolódások hozhatók létre adatokhoz és memória szolgáltatásokhoz, mint a Microsoft Fabric, SharePoint, Pinecone és Qdrant.

Nézzük meg, hogyan alkalmazzák ezeket a funkciókat a Microsoft Agent Framework néhány alapfogalmára.

## A Microsoft Agent Framework kulcsfogalmai

### Ügynökök

![Agent Keretrendszer](../../../translated_images/hu/agent-components.410a06daf87b4fef.webp)

**Ügynökök létrehozása**

Az ügynök létrehozása úgy történik, hogy definiáljuk az inferencia szolgáltatást (LLM Provider), egy
utasításkészletet, amelyet az AI ügynök követ, és egy hozzárendelt `name` mezőt:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

A fenti példa `Azure OpenAI`-t használ, de ügynökök létrehozhatók különféle szolgáltatásokkal, beleértve a `Microsoft Foundry Agent Service`-t is:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` API-k

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

vagy távoli ügynökök az A2A protokollt használva:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Ügynökök futtatása**

Az ügynököket a `.run` vagy `.run_stream` metódusokkal kell futtatni nem-streaming vagy streaming válaszokhoz.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Minden ügynök futtatásnál megadhatók opciók a paraméterek testreszabásához, például az ügynök által használt `max_tokens`, az ügynök által hívható `tools` és akár maga a `model`.

Ez hasznos olyan esetekben, amikor egy felhasználó feladatának elvégzéséhez konkrét modellekre vagy eszközökre van szükség.

**Eszközök**

Eszközök definiálhatók már az ügynök definiálásakor:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Amikor egy ChatAgentet közvetlenül hoz létre

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

és futtatáskor is megadhatók az ügynök számára:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Az eszköz csak erre a futásra érhető el )
```

**Ügynök szálak**

Az ügynök szálak többmenetes beszélgetések kezelésére szolgálnak. A szálak létrehozhatók az alábbi módok valamelyikével:

- A `get_new_thread()` használatával, amely lehetővé teszi, hogy a szál idővel el legyen mentve
- A szál automatikus létrehozásával, amikor az ügynököt futtatjuk, és a szál csak az aktuális futás idejére él.

A szál létrehozása a kód valahogy így néz ki:

```python
# Hozzon létre egy új szálat.
thread = agent.get_new_thread() # Futtassa az ügynököt a szálban.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

A szál későbbi tároláshoz való serializálása így történik:

```python
# Hozzon létre egy új szálat.
thread = agent.get_new_thread() 

# Futtassa az ügynököt a szállal.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serializálja a szálat tároláshoz.

serialized_thread = await thread.serialize() 

# Deserializálja a szál állapotát a tárolóból való betöltés után.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Ügynök közbeékelődés (Middleware)**

Az ügynökök eszközökkel és LLM-ekkel lépnek interakcióba a felhasználói feladatok elvégzéséhez. Bizonyos esetekben szeretnénk műveleteket végrehajtani vagy nyomon követni ezeket a kölcsönhatásokat. Az ügynök middleware lehetővé teszi ezt az alábbiak révén:

*Funkció middleware*

Ez a middleware lehetővé teszi, hogy egy műveletet hajtsunk végre az ügynök és a funkció/eszköz hívása között. Például akkor használható, ha naplózást szeretnénk végezni a funkcióhívásoknál.

A lenti kódban a `next` határozza meg, hogy a következő middleware-t vagy a tényleges funkciót kell-e meghívni.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Előfeldolgozás: Naplózás a függvény végrehajtása előtt
    print(f"[Function] Calling {context.function.name}")

    # Tovább a következő middleware-hez vagy a függvény végrehajtásához
    await next(context)

    # Utófeldolgozás: Naplózás a függvény végrehajtása után
    print(f"[Function] {context.function.name} completed")
```

*Chat middleware*

Ez a middleware lehetővé teszi, hogy egy műveletet hajtsunk végre vagy naplózzunk az ügynök és az LLM közötti kérések között.

Ez tartalmaz fontos információkat, például az AI szolgáltatásnak küldött `messages`-eket.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Előfeldolgozás: Naplózás az MI-hívás előtt
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Folytassa a következő köztes réteghez vagy MI-szolgáltatáshoz
    await next(context)

    # Utófeldolgozás: Naplózás az MI-válasz után
    print("[Chat] AI response received")

```

**Ügynök memória**

Ahogy az `Agentic Memory` leckében is tárgyaltuk, a memória fontos eleme annak, hogy az ügynök különböző kontextusokban tudjon működni. A MAF többféle memóriatípust kínál:

*Memória a futásidőben (In-Memory Storage)*

Ez az a memória, amely a szálakban tárolódik az alkalmazás futása során.

```python
# Hozz létre egy új szálat.
thread = agent.get_new_thread() # Futtassa az ügynököt a szállal.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Perzisztens üzenetek*

Ezt a memóriát a beszélgetés előzményeinek különböző munkamenetek közötti tárolására használjuk. A `chat_message_store_factory` használatával definiálható:

```python
from agent_framework import ChatMessageStore

# Hozzon létre egy egyedi üzenettárolót
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dinamikus memória*

Ez a memória a kontextushoz adódik hozzá, mielőtt az ügynököket futtatnánk. Ezek a memóriák külső szolgáltatásokban is tárolhatók, például mem0-ban:

```python
from agent_framework.mem0 import Mem0Provider

# Mem0 használata fejlett memóriafunkciókhoz
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

**Ügynök megfigyelhetősége**

A megfigyelhetőség fontos a megbízható és karbantartható ügynöki rendszerek építéséhez. A MAF integrálódik az OpenTelemetry-vel, hogy jobb követést és mérőszámokat biztosítson a megfigyelhetőséghez.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # csinálj valamit
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Munkafolyamatok

A MAF munkafolyamatokat kínál, amelyek előre definiált lépések egy feladat elvégzéséhez, és az AI ügynököket is komponensekként tartalmazzák ezeken a lépéseken belül.

A munkafolyamatok különböző összetevőkből állnak, amelyek jobb vezérlési folyamatot tesznek lehetővé. A munkafolyamatok támogatják a **többügynökös orchesztrációt** és a **checkpointinget** a munkafolyamat állapotának mentéséhez.

A munkafolyamat alapvető összetevői:

**Végrehajtók (Executors)**

A végrehajtók bemeneti üzeneteket fogadnak, elvégzik a rájuk bízott feladatokat, majd kimeneti üzenetet állítanak elő. Ez előreviszi a munkafolyamatot a nagyobb feladat teljesítése felé. A végrehajtók lehetnek AI ügynökök vagy egyedi logikák.

**Élek (Edges)**

Az élek a munkafolyamatban az üzenetek áramlását határozzák meg. Ezek lehetnek:

*Direkt élek* - Egyszerű egy-az-egyhez kapcsolatok a végrehajtók között:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Feltételes élek* - Akkor aktiválódnak, ha bizonyos feltétel teljesül. Például, ha a szállodai szobák nem elérhetők, egy végrehajtó más lehetőségeket javasolhat.

*Switch-case élek* - Az üzeneteket különböző végrehajtókhoz irányítják a meghatározott feltételek alapján. Például ha az utazó ügyfél prioritási hozzáféréssel rendelkezik, a feladatait egy másik munkafolyamat kezeli.

*Fan-out élek* - Egy üzenetet több célhoz küldenek.

*Fan-in élek* - Több üzenetet gyűjtenek össze különböző végrehajtóktól, és egy célhoz továbbítanak.

**Események**

A munkafolyamatok jobb megfigyelhetősége érdekében a MAF beépített eseményeket kínál a végrehajtáshoz, többek között:

- `WorkflowStartedEvent`  - A munkafolyamat végrehajtása elindul
- `WorkflowOutputEvent` - A munkafolyamat kimenetet állít elő
- `WorkflowErrorEvent` - A munkafolyamat hibát tapasztal
- `ExecutorInvokeEvent`  - A végrehajtó elkezdi a feldolgozást
- `ExecutorCompleteEvent`  -  A végrehajtó befejezi a feldolgozást
- `RequestInfoEvent` - Egy kérés kiadásra kerül

## Migráció más keretrendszerekről (Semantic Kernel és AutoGen)

### Különbségek a MAF és a Semantic Kernel között

**Egyszerűsített ügynöklétrehozás**

A Semantic Kernel megköveteli egy Kernel példány létrehozását minden ügynökhöz. A MAF egyszerűsített megközelítést használ, kiterjesztésekkel a fő szolgáltatókhoz.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Ügynök szál létrehozása**

A Semantic Kernel megköveteli, hogy a szálakat kézzel hozzuk létre. A MAF-ben az ügynöknek közvetlenül rendelnek szálat.

```python
thread = agent.get_new_thread() # Futtassa az ügynököt a szálban.
```

**Eszközregisztráció**

A Semantic Kernel-ben az eszközök a Kernel-hez vannak regisztrálva, és a Kernel kerül átadásra az ügynöknek. A MAF-ben az eszközök közvetlenül az ügynök létrehozásakor regisztrálhatók.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Különbségek a MAF és az AutoGen között

**Teams vs Workflows**

A `Teams` az eseményalapú tevékenységek eseményszerkezete az AutoGen-ben. A MAF `Workflows`-t használ, amelyek graf alapú architektúra révén irányítják az adatokat a végrehajtókhoz.

**Eszköz létrehozása**

Az AutoGen a `FunctionTool`-t használja a funkciók becsomagolására, hogy az ügynökök meghívhassák azokat. A MAF az @ai_function-t használja, amely hasonlóan működik, de automatikusan kikövetkezteti a sémákat minden funkcióhoz.

**Ügynök viselkedés**

Az AutoGen-ben az ügynökök alapértelmezetten egyfordulósak, hacsak a `max_tool_iterations` nincs magasabb értékre állítva. A MAF-ben a `ChatAgent` alapértelmezetten többfordulós, ami azt jelenti, hogy tovább hívja az eszközöket, amíg a felhasználó feladata be nem fejeződik.

## Kódpéldák

A Microsoft Agent Framework kódpéldái megtalálhatók ebben a tárolóban a `xx-python-agent-framework` és `xx-dotnet-agent-framework` fájlok alatt.

## További kérdéseid vannak a Microsoft Agent Framework-ről?

Csatlakozz a [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)-hoz, hogy találkozz más tanulókkal, részt vegyél irodai órákon és megválaszolják az AI ügynökökkel kapcsolatos kérdéseidet.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Felelősségkizáró nyilatkozat:
Ezt a dokumentumot a Co-op Translator (https://github.com/Azure/co-op-translator) AI-fordítószolgáltatásával fordítottuk. Bár törekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti dokumentum az anyanyelvén tekintendő hiteles forrásnak. Kritikus fontosságú információk esetén professzionális emberi fordítás ajánlott. Nem vállalunk felelősséget a jelen fordítás használatából eredő félreértésekért vagy téves értelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->