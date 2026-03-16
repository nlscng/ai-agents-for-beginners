# Microsoft Agent Frameworki uurimine

![Agentiraamistik](../../../translated_images/et/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Sissejuhatus

See õppetund hõlmab:

- Microsoft Agent Frameworki mõistmine: peamised omadused ja väärtus  
- Microsoft Agent Frameworki põhikontseptsioonide uurimine
- MAF võrdlus Semantic Kerneli ja AutoGeniga: migratsioonijuhend

## Õpieesmärgid

Pärast selle õppetunni läbimist oskad:

- Luua tootmiseks valmis AI-agente Microsoft Agent Frameworki abil
- Rakendada Microsoft Agent Frameworki põhifunktsioone oma agentsete kasutusjuhtude puhul
- Migreerida ja integreerida olemasolevaid agentseid raamistikke ja tööriistu  

## Koodinäited 

Koodinäited [Microsoft Agent Frameworki (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) kohta asuvad selles repositoris failides `xx-python-agent-framework` ja `xx-dotnet-agent-framework`.

## Microsoft Agent Frameworki mõistmine

![Raamistiku sissejuhatus](../../../translated_images/et/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) tugineb Semantic Kerneli ja AutoGeni kogemustele ja õppetundidele. See pakub paindlikkust, et lahendada laia valikut agentseid kasutusjuhtumeid, mida nähakse nii tootmises kui teadusuuringutes, sealhulgas:

- **Järjestikune agentide orkestreerimine** olukordades, kus on vaja samm-sammult töövooge.
- **Samaaegne orkestreerimine** olukordades, kus agentidel on vaja täita ülesandeid samaaegselt.
- **Rühma vestluse orkestreerimine** olukordades, kus agentid saavad üheskoos ühel ülesandel koostööd teha.
- **Ülesande üleandmise orkestreerimine** olukordades, kus agentid annavad ülesandeid üksteisele alülesannete täitmisel.
- **Magnetiline orkestreerimine** olukordades, kus manager-agent loob ja muudab ülesannete nimekirja ning koordineerib subagentide tegevust ülesande täitmiseks.

AI-agentide tootmisse toomiseks sisaldab MAF ka järgmisi funktsioone:

- **Jälgitavus** OpenTelemetry kasutamise kaudu, kus iga AI-agendi tegevus, sealhulgas tööriistakutsed, orkestreerimise sammud, mõtlemisvood ja jõudluse jälgimine Microsoft Foundry armatuurlaudade kaudu.
- **Turvalisus** agendi majutamisel natiivselt Microsoft Foundryl, mis sisaldab turvakontrolle nagu rollipõhine ligipääs, privaatandmete käitlemine ja sisseehitatud sisuohutus.
- **Püsivus** kuna agendi lõimed ja töövood võivad peatuda, jätkuda ja taastuda vigadest, mis võimaldab pikemaajalisi protsesse.
- **Juhitavus** toetades inimeste kaasamist töövoogudesse, kus ülesanded märgitakse nõudma inimlikku kinnitust.

Microsoft Agent Framework keskendub ka koostalitlusvõimele, olles:

- **Pilve-agnostiline** - agentid võivad töötada konteinerites, kohalikes keskkondades ja mitmetes pilvkeskkondades.
- **Pakkuja-agnostiline** - agente saab luua eelistatud SDK kaudu, sealhulgas Azure OpenAI ja OpenAI
- **Avatud standardite integreerimine** - agentid saavad kasutada protokolle nagu Agent-to-Agent(A2A) ja Model Context Protocol (MCP), et avastada ja kasutada teisi agente ning tööriistu.
- **Pistikprogrammid ja ühendused** - saab luua ühendusi andmete ja mäluteenustega nagu Microsoft Fabric, SharePoint, Pinecone ja Qdrant.

Vaatame, kuidas neid funktsioone rakendatakse Microsoft Agent Frameworki mõnedes põhikontseptsioonides.

## Microsoft Agent Frameworki põhikontseptsioonid

### Agendid

![Agentiraamistik](../../../translated_images/et/agent-components.410a06daf87b4fef.webp)

**Agentide loomine**

Agendi loomine toimub ennustus-teenuse (LLM Provider), AI-agendile järgimiseks mõeldud juhiste kogumi ja määratud `name` määratlemisega:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Ülaltoodud kasutab `Azure OpenAI`, kuid agente saab luua erinevate teenuste abil, sh `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` API-d

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

või kaugagente, kasutades A2A protokolli:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Agentide käivitamine**

Agente käivitatakse, kasutades `.run` või `.run_stream` meetodeid vastavalt mittevoo- või voovastuste jaoks.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Igal agendi käivitusel võivad olla ka valikud parameetrite kohandamiseks, nagu agenti kasutatav `max_tokens`, `tools`, mida agent saab kutsuda, ja isegi agenti kasutatav `model`.

See on kasulik juhtudel, kui ülesande täitmiseks on vaja konkreetseid mudeleid või tööriistu.

**Tööriistad**

Tööriistu saab määratleda nii agendi loomisel:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Kui ChatAgenti luuakse otse

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

ja ka agendi käivitamisel:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # See tööriist on saadaval ainult selle jooksu jaoks )
```

**Agendi lõimed**

Agendi lõime kasutatakse mitmekäiguliste vestluste käsitlemiseks. Lõime saab luua kas:

- Kasutades `get_new_thread()`, mis võimaldab lõime aja jooksul salvestada
- Lõi luua automaatselt agendi käivitamisel, kus lõim kestab ainult praeguse käigu jooksul.

Lõime loomiseks näeb kood välja järgmiselt:

```python
# Loo uus lõim.
thread = agent.get_new_thread() # Käivita agent koos lõimiga.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Seejärel saate lõime serialiseerida hilisemaks salvestamiseks:

```python
# Loo uus lõim.
thread = agent.get_new_thread() 

# Käivita agent koos lõimiga.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serialiseeri lõim salvestamiseks.

serialized_thread = await thread.serialize() 

# Deserialiseeri lõimi olek pärast salvestusest laadimist.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agendi vahevara**

Agendid suhtlevad tööriistade ja LLM-idega, et täita kasutaja ülesandeid. Teatud stsenaariumites tahame nende interaktsioonide vahel midagi käivitada või jälgida. Agendi vahevara võimaldab meil seda teha läbi:

*Funktsiooni vahevara*

See vahevara võimaldab meil sooritada tegevuse agendi ja funktsiooni/tööriista vahel, mida see kutsub. Näide kasutusest on, kui soovite funktsioonikutsest logi pidada.

Allolevas koodis määrab `next`, kas kutsutakse järgmine vahevara või tegelik funktsioon.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Eeltöötlus: Logi enne funktsiooni käivitamist
    print(f"[Function] Calling {context.function.name}")

    # Jätka järgmise middleware'i või funktsiooni käivitamisega
    await next(context)

    # Järeltöötlus: Logi pärast funktsiooni käivitamist
    print(f"[Function] {context.function.name} completed")
```

*Vestluse vahevara*

See vahevara võimaldab meil sooritada või logida toimingut agendi ja LLM-ile saatvate päringute vahel.

See sisaldab olulist teavet, nagu AI-teenusele saadetavad `messages`.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Eeltöötlus: Logi enne AI-päringut
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Jätka järgmise vahendusmooduli või AI-teenuse juurde
    await next(context)

    # Järeltöötlus: Logi pärast AI-vastust
    print("[Chat] AI response received")

```

**Agendi mälu**

Nagu käsitleti õppetunnis `Agentic Memory`, on mälu oluline element, mis võimaldab agendil töötada erinevates kontekstides. MAF pakub mitut erinevat tüüpi mälu:

*Mälusalvestus*

See on mälu, mis salvestatakse lõimedes rakenduse jooksuajal.

```python
# Loo uus lõim.
thread = agent.get_new_thread() # Käivita agent koos lõimiga.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Püsivad sõnumid*

Seda mälu kasutatakse vestluse ajaloo salvestamiseks erinevate sessioonide vahel. See määratletakse kasutades `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Loo kohandatud sõnumihoidla
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dünaamiline mälu*

See mälu lisatakse konteksti enne agentide käivitamist. Need mälud võivad olla salvestatud välistes teenustes, näiteks mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Mem0 kasutamine täiustatud mäluvõimaluste jaoks
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

**Agendi jälgitavus**

Jälgitavus on oluline usaldusväärsete ja hooldatavate agentsete süsteemide loomisel. MAF integreerub OpenTelemetryga, et pakkuda jälgimist ja mõõdikuid parema jälgitavuse jaoks.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # tee midagi
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Töövood

MAF pakub töövooge, mis on eelmääratletud sammud ülesande täitmiseks ja hõlmavad AI-agente nende sammude komponendina.

Töövood koosnevad erinevatest komponentidest, mis võimaldavad paremat juhtimisvoogu. Töövood võimaldavad ka **mitmeagendilist orkestreerimist** ja **checkpointimist**, et salvestada töövoo olekud.

Töövoo põhikomponendid on:

**Täideviijad**

Täideviijad saavad sisend-sõnumeid, täidavad neile määratud ülesandeid ja seejärel toodavad väljund-sõnumi. See viib töövoogu edasi suurema ülesande lõpetamise suunas. Täideviijad võivad olla kas AI-agendid või kohandatud loogika.

**Servad**

Servasid kasutatakse töövoos sõnumite voolu määratlemiseks. Need võivad olla:

*Otsesed servad* - lihtsad ühe-ühe vastu ühendused täideviijate vahel:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Tingimuslikud servad* - aktiveeritakse pärast teatud tingimuse täitumist. Näiteks kui hotellitoad pole saadaval, võib täideviija soovitada muid valikuid.

*Switch-case servad* - suunavad sõnumeid erinevatele täideviijatele vastavalt määratletud tingimustele. Näiteks kui reisiklientel on prioriteetne ligipääs, käsitletakse nende ülesandeid teise töövoo kaudu.

*Hajutusservad* - saadab ühe sõnumi mitmele sihtmärgile.

*Kogumiservad* - kogub mitu sõnumit erinevatelt täideviijatelt ja saadab ühe sihtmärgini.

**Sündmused**

Parema jälgitavuse tagamiseks töövoogudes pakub MAF sisseehitatud täitmissündmusi, sealhulgas:

- `WorkflowStartedEvent`  - Workflow execution begins
- `WorkflowOutputEvent` - Workflow produces an output
- `WorkflowErrorEvent` - Workflow encounters an error
- `ExecutorInvokeEvent`  - Executor starts processing
- `ExecutorCompleteEvent`  -  Executor finishes processing
- `RequestInfoEvent` - A request is issued

## Kuidas migreerida teistest raamistikest (Semantic Kernel ja AutoGen)

### Erinevused MAFi ja Semantic Kerneli vahel

**Lihtsustatud agendi loomine**

Semantic Kernel tugineb iga agendi puhul Kernel'i instantsi loomisele. MAF kasutab lihtsustatud lähenemist, kasutades laiendusi peamiste pakkujate jaoks.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Agendi lõime loomine**

Semantic Kernel nõuab lõimede manuaalset loomist. MAFis määratakse agendile lõim otse.

```python
thread = agent.get_new_thread() # Käivita agent koos lõimega.
```

**Tööriista registreerimine**

Semantic Kernelis registreeritakse tööriistad Kerneli külge ja Kernel antakse seejärel agendile. MAFis registreeritakse tööriistad otse agendi loomise protsessi ajal.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Erinevused MAFi ja  AutoGeni vahel

**Meeskonnad vs töövood**

`Teams` on AutoGenis sündmuspõhiste tegevuste jaoks agendiga seotud sündmuste struktuur. MAF kasutab `Workflows`, mis suunavad andmeid täideviijatele graafipõhise arhitektuuri kaudu.

**Tööriista loomine**

AutoGen kasutab `FunctionTool`, et ümber pakkida funktsioone, mida agendid kutsuvad. MAF kasutab @ai_function, mis toimib sarnaselt, kuid järeldab ka iga funktsiooni skeemid automaatselt.

**Agendi käitumine**

AutoGenis on agendid vaikimisi ühekäigulised, välja arvatud juhul, kui `max_tool_iterations` on seatud suuremaks. MAFis on `ChatAgent` vaikimisi mitmekäiguline, mis tähendab, et see jätkab tööriistade kutsumist, kuni kasutaja ülesanne on täidetud.

## Koodinäited 

Microsoft Agent Frameworki koodinäiteid leiate selles repositoris failidest `xx-python-agent-framework` ja `xx-dotnet-agent-framework`.

## Kas sul on veel küsimusi Microsoft Agent Frameworki kohta?

Liitu [Microsoft Foundry Discordiga](https://aka.ms/ai-agents/discord), et kohtuda teiste õppijatega, osaleda kontorituundides ja saada vastuseid oma AI-agentidega seotud küsimustele.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastutusest loobumine**:
See dokument on tõlgitud tehisintellekti-põhise tõlketeenuse [Co-op Translator](https://github.com/Azure/co-op-translator) abil. Kuigi püüame olla täpsed, palun pange tähele, et automatiseeritud tõlked võivad sisaldada vigu või ebatäpsusi. Algset dokumenti selle algkeeles tuleks pidada autoriteetseks allikaks. Olulise teabe puhul soovitatakse kasutada professionaalset inimtõlget. Me ei vastuta selle tõlke kasutamisest tulenevate arusaamatuste või väärtõlgenduste eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->