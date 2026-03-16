# „Microsoft Agent Framework“ tyrinėjimas

![Agent Framework](../../../translated_images/lt/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Įvadas

Ši pamoka apims:

- „Microsoft Agent Framework“ supratimą: pagrindinės funkcijos ir vertė  
- Pagrindinių „Microsoft Agent Framework“ sąvokų tyrinėjimą
- MAF palyginimą su Semantic Kernel ir AutoGen: migracijos vadovas

## Mokymosi tikslai

Baigę šią pamoką, žinosite, kaip:

- Kurti gamybai paruoštus AI agentus naudojant „Microsoft Agent Framework“
- Taikyti pagrindines „Microsoft Agent Framework“ funkcijas savo agentinių naudojimo atvejuose
- Migratuoti ir integruoti esamus agentinius pagrindus ir įrankius  

## Kodo pavyzdžiai 

„Microsoft Agent Framework (MAF)“ kodo pavyzdžius rasite šiame saugykloje po failais `xx-python-agent-framework` ir `xx-dotnet-agent-framework`.

## „Microsoft Agent Framework“ supratimas

![Framework Intro](../../../translated_images/lt/framework-intro.077af16617cf130c.webp)

[„Microsoft Agent Framework (MAF)“](https://aka.ms/ai-agents-beginners/agent-framewrok) remiasi patirtimi ir žiniomis, gautomis iš Semantic Kernel ir AutoGen. Jis siūlo lankstumą spręsti įvairius agentinius naudojimo atvejus, matomus tiek gamyboje, tiek tyrimų aplinkoje, įskaitant:

- **Sekvencinę agentų orkestraciją** scenarijuose, kai reikalingi žingsnis po žingsnio darbo procesai.
- **Konkuruojančią orkestraciją** scenarijuose, kai agentai turi užduotis atlikti vienu metu.
- **Grupinę pokalbių orkestraciją** scenarijuose, kai agentai gali bendradarbiauti vykdydami vieną užduotį.
- **Perdavimų orkestraciją** scenarijuose, kai agentai perduoda užduotį vienas kitam, kaip uždaviniai yra užbaigiami.
- **Magnetinę orkestraciją** scenarijuose, kai vadovaujantis agentas kuria ir keičia užduočių sąrašą ir koordinuoja pagalagentus užduoties įvykdymui.

Norėdamas pristatyti AI agentus gamyboje, MAF taip pat apima funkcijas:

- **Stebimumui** naudojant OpenTelemetry, kur kiekvienas AI agento veiksmas, įskaitant įrankių iškvietimus, orkestracijos žingsnius, samprotavimų srautus ir Microsoft Foundry prietaisų skydelio našumo stebėjimą.
- **Saugumui** talpinant agentus natūraliai Microsoft Foundry aplinkoje, į kurią įeina saugumo kontrolės, tokios kaip prieigos valdymas pagal vaidmenis, privačių duomenų tvarkymas ir įmontuota turinio sauga.
- **Patvarumui**, nes agentų gijos ir darbo procesai gali būti pristabdyti, atnaujinti ir atstatyti po klaidų, leidžiantys vykdyti ilgai trunkančius procesus.
- **Kontrolei**, nes remiasi žmogumi grandinėje, kai užduotys žymimos kaip reikalaujančios žmogaus patvirtinimo.

„Microsoft Agent Framework“ taip pat orientuotas į tarpoperabilumą:

- **Debesų nepriklausomumas** – agentai gali veikti konteineriuose, vietinėse aplinkose ir įvairiuose debesyse.
- **Tiekėjų nepriklausomumas** – agentus galima kurti naudojant pageidaujamą SDK, įskaitant Azure OpenAI ir OpenAI.
- **Atvirų standartų integracija** – agentai gali naudoti protokolus, tokius kaip Agent-to-Agent (A2A) ir Model Context Protocol (MCP), kad atrastų ir naudotų kitus agentus bei įrankius.
- **Įskiepius ir jungtis** – galima jungtis prie duomenų ir atminties paslaugų, tokių kaip Microsoft Fabric, SharePoint, Pinecone ir Qdrant.

Pažvelkime, kaip šios funkcijos taikomos pagrindinėms „Microsoft Agent Framework“ sąvokoms.

## „Microsoft Agent Framework“ pagrindinės sąvokos

### Agentai

![Agent Framework](../../../translated_images/lt/agent-components.410a06daf87b4fef.webp)

**Agentų kūrimas**

Agentų kūrimas vykdomas apibrėžiant išvados paslaugą (LLM tiekėją), instrukcijų rinkinį AI agentui sekti ir paskirtą `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Aukščiau naudojamas `Azure OpenAI`, tačiau agentus galima kurti naudojant įvairias paslaugas, įskaitant `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` API metodai

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

arba nuotolinius agentus naudojant A2A protokolą:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Agentų paleidimas**

Agentai paleidžiami naudojant `.run` arba `.run_stream` metodus, skirtus ne srautinėms arba srautinėms atsakomosioms reakcijoms.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Kiekvienam agentui galima nustatyti pasirinkimus, kurie pritaiko tokius parametrus kaip `max_tokens`, kuriuos naudoja agentas, `tools`, kuriuos agentas gali iškviesti, ir net patį `model`, naudojamą agentui.

Tai naudinga atvejais, kai uždavinio įvykdymui reikalingi konkretūs modeliai ar įrankiai.

**Įrankiai**

Įrankiai gali būti apibrėžiami tiek kuriant agentą:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Kai kuriate ChatAgent tiesiogiai

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

tiek paleidžiant agentą:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Įrankis skirtas naudoti tik šiame vykdyme )
```

**Agentų gijos**

Agentų gijos naudojamos tvarkyti daugiaposūkiniams pokalbiams. Gijos gali būti sukuriamos:

- Naudojant `get_new_thread()`, kas leidžia giją išsaugoti laikui bėgant
- Automatiškai sukuriant giją paleidžiant agentą, kuri egzistuoja tik dabartinio paleidimo metu.

Gijos kūrimo kodas atrodo taip:

```python
# Sukurkite naują giją.
thread = agent.get_new_thread() # Paleiskite agentą su gija.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Po to giją galima serializuoti, kad būtų išsaugota ateičiai:

```python
# Sukurkite naują giją.
thread = agent.get_new_thread() 

# Vykdykite agentą su gija.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serializuokite giją saugojimui.

serialized_thread = await thread.serialize() 

# Deserializuokite gijos būseną po įkėlimo iš saugyklos.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agentų tarpinės programos**

Agentai sąveikauja su įrankiais ir LLM, kad įvykdytų vartotojo užduotis. Tam tikrais atvejais norime vykdyti ar sekti veiksmus tarp šių sąveikų. Agentų tarpinės programos leidžia tai padaryti per:

*Funkcinė tarpinė programa*

Ši tarpinė programa leidžia vykdyti veiksmą tarp agento ir funkcijos/įrankio, kurį agentas iškvies. Pavyzdys, kada ji naudojama, yra kai norime registruoti funkcijos iškvietimą.

Žemiau pateiktame kode `next` apibrėžia, ar turi būti iškviečiama kita tarpinė programa, ar pati funkcija.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Išankstinis apdorojimas: Įrašas prieš funkcijos vykdymą
    print(f"[Function] Calling {context.function.name}")

    # Tęsti prie kito tarpinio programos arba funkcijos vykdymo
    await next(context)

    # Po apdorojimo: Įrašas po funkcijos vykdymo
    print(f"[Function] {context.function.name} completed")
```

*Pokalbių tarpinė programa*

Ši tarpinė programa leidžia vykdyti arba registruoti veiksmą tarp agento ir pokalbių su LLM užklausų.

Čia yra svarbi informacija, pavyzdžiui, `messages`, kurie siunčiami į AI paslaugą.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Išankstinis apdorojimas: žurnalas prieš AI kvietimą
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Tęsti kitam tarpinio programos sluoksnio arba AI paslaugos žingsniui
    await next(context)

    # Galutinis apdorojimas: žurnalas po AI atsakymo
    print("[Chat] AI response received")

```

**Agentų atmintis**

Kaip buvo aptarta pamokoje „Agentinė atmintis“, atmintis yra svarbi siekiant agentui veikti skirtinguose kontekstuose. MAF siūlo keletą skirtingų atminties tipų:

*Operatyvioji atmintis*

Tai atmintis saugoma gijų metu programos veikimo metu.

```python
# Sukurkite naują giją.
thread = agent.get_new_thread() # Paleiskite agentą su šia gija.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Išliekamosios žinutės*

Ši atmintis naudojama saugant pokalbių istoriją per skirtingas sesijas. Ji apibrėžiama naudojant `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Sukurti pasirinktinių pranešimų saugyklą
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dinaminė atmintis*

Ši atmintis pridedama prie konteksto prieš paleidžiant agentus. Šias atmintis galima saugoti išorinėse paslaugose, tokiose kaip mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Naudojama Mem0 pažangioms atminties funkcijoms
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

**Agentų stebimumas**

Stebimumas svarbus kuriant patikimas ir prižiūrimas agentines sistemas. MAF integruojasi su OpenTelemetry, kad teiktų trasavimą ir matavimus geresniam stebimumui.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # daryti kažką
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Darbo procesai

MAF siūlo darbo procesus, kurie yra iš anksto apibrėžti žingsniai užduočiai atlikti, ir apima AI agentus kaip šių žingsnių komponentus.

Darbo procesai susideda iš skirtingų komponentų, leidžiančių geresnį valdymą. Darbo procesai taip pat leidžia **multi-agentų orkestraciją** ir **žymių uždaviniams kaupimą** (checkpointing) darbų procesų būsenų išsaugojimui.

Pagrindiniai darbo proceso komponentai yra:

**Vykdytojai**

Vykdytojai gauna įvesties pranešimus, atlieka paskirtas užduotis ir kuria išvesties pranešimą. Tai leidžia procesui eiti į priekį link didesnės užduoties pabaigos. Vykdytojai gali būti AI agentai arba vartotojo logika.

**Kraštai**

Kraštai naudojami apibrėžti pranešimų srautą darbo procese. Jie gali būti:

*Tiesioginiai kraštai* – paprasti vienas prie vieno jungimai tarp vykdytojų:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Sąlyginiai kraštai* – aktyvuojami, kai įvykdoma tam tikra sąlyga. Pavyzdžiui, kai viešbučių kambariai nepasiekiami, vykdytojas gali pasiūlyti kitas galimybes.

*Perjungimo (switch-case) kraštai* – nukreipia pranešimus skirtingiems vykdytojams pagal apibrėžtas sąlygas. Pavyzdžiui, jei kelionių klientas turi prioritetinę prieigą, jo užduotys bus tvarkomos kitu darbo procesu.

*Išskirstymo (fan-out) kraštai* – siunčia vieną pranešimą keliems tikslams.

*Surinkimo (fan-in) kraštai* – renka kelis pranešimus iš skirtingų vykdytojų ir siunčia vienam tikslui.

**Įvykiai**

Geram darbo procesų stebimumui MAF siūlo įmontuotus vykdymo įvykius kaip:

- `WorkflowStartedEvent`  - prasideda darbo proceso vykdymas
- `WorkflowOutputEvent` - darbo procesas pateikia išvestį
- `WorkflowErrorEvent` - darbo procese įvyksta klaida
- `ExecutorInvokeEvent`  - vykdytojas pradeda apdorojimą
- `ExecutorCompleteEvent`  -  vykdytojas užbaigia apdorojimą
- `RequestInfoEvent` - įvykdoma užklausa

## Migracija iš kitų pagrindų (Semantic Kernel ir AutoGen)

### Skirtumai tarp MAF ir Semantic Kernel

**Agentų kūrimo supaprastinimas**

Semantic Kernel reikalauja sukurti Kernel egzempliorių kiekvienam agentui. MAF naudoja supaprastintą požiūrį, naudodama plėtinius pagrindiniams tiekėjams.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Agentų gijų kūrimas**

Semantic Kernel reikalauja gijas kurti rankiniu būdu. MAF agentui tiesiogiai priskiria giją.

```python
thread = agent.get_new_thread() # Paleiskite agentą su gija.
```

**Įrankių registracija**

Semantic Kernel įrankiai registruojami Kernelyje, kuris perduodamas agentui. MAF įrankiai registruojami tiesiogiai agento kūrimo metu.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Skirtumai tarp MAF ir AutoGen

**Komandos prieš darbo procesus**

„Teams“ yra AutoGen įvykių struktūra agentų įvykių veiklai. MAF naudoja „Workflows“, kurie nukreipia duomenis vykdytojams per grafų architektūrą.

**Įrankių kūrimas**

AutoGen naudoja `FunctionTool`, kad apvyniotų funkcijas agentų iškvietimui. MAF naudoja @ai_function, kuri veikia panašiai bet taip pat automatiškai nuspėja kiekvienos funkcijos schemas.

**Agentų elgsena**

Agentai pagal nutylėjimą AutoGen yra vienapotinkiniai, nebent `max_tool_iterations` nustatytas didesnis. MAF `ChatAgent` yra daugapotinkinis pagal nutylėjimą, reiškiantis, kad jis nuolat kviečia įrankius tol, kol vartotojo užduotis bus užbaigta.

## Kodo pavyzdžiai 

„Microsoft Agent Framework“ kodo pavyzdžius rasite šiame saugykloje po failais `xx-python-agent-framework` ir `xx-dotnet-agent-framework`.

## Turite daugiau klausimų apie „Microsoft Agent Framework“?

Prisijunkite prie [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kad susipažintumėte su kitais besimokančiais, dalyvautumėte biurų valandose ir gautumėte atsakymus į savo AI agentų klausimus.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors siekiame tikslumo, atkreipkite dėmesį, kad automatizuoti vertimai gali turėti klaidų ar netikslumų. Pirminis dokumentas jo gimtąja kalba yra laikomas autoritetingu šaltiniu. Kritinei informacijai rekomenduojamas profesionalus žmogaus atliktas vertimas. Mes neatsakome už bet kokius nesusipratimus ar klaidingus aiškinimus, kilusius dėl šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->