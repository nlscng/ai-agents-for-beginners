# Raziščimo Microsoft Agent Framework

![Agent Framework](../../../translated_images/sl/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Uvod

Ta lekcija bo obravnavala:

- Razumevanje Microsoft Agent Framework: Ključne funkcije in vrednost  
- Raziščite ključne koncepte Microsoft Agent Framework
- Primerjava MAF z Semantic Kernel in AutoGen: Vodnik za migracijo

## Cilji učenja

Po zaključku te lekcije boste znali:

- Zgraditi produkcijsko pripravljene AI agente z uporabo Microsoft Agent Framework
- Uporabiti osnovne funkcije Microsoft Agent Framework za vaše agentne primere uporabe
- Migrirati in integrirati obstoječe agentne okvire in orodja  

## Primeri kode

Primeri kode za [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) so na voljo v tem repozitoriju v datotekah `xx-python-agent-framework` in `xx-dotnet-agent-framework`.

## Razumevanje Microsoft Agent Framework

![Framework Intro](../../../translated_images/sl/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) gradi na izkušnjah in spoznanjih iz Semantic Kernel in AutoGen. Ponuja prilagodljivost za reševanje širokega nabora agentnih primerov uporabe, ki jih vidimo tako v produkcijskem kot raziskovalnem okolju, vključno z:

- **Zaporedna orkestracija agentov** v scenarijih, kjer so potrebni korak za korakom delovni tokovi.
- **Sočasna orkestracija** v scenarijih, kjer agenti potrebujejo opraviti naloge istočasno.
- **Orkestracija skupinskega klepeta** v scenarijih, kjer lahko agenti sodelujejo skupaj pri eni nalogi.
- **Prenos nalog (Handoff Orchestration)** v scenarijih, kjer agenti prenašajo nalogo drug drugemu, ko so podnaloge dokončane.
- **Magnetna orkestracija** v scenarijih, kjer agent vodja ustvari in spremeni seznam nalog ter usklajuje podagente za dokončanje naloge.

Za omogočanje AI agentov v produkciji MAF vključuje tudi funkcije za:

- **Opazovanje** z uporabo OpenTelemetry, kjer je vsaka akcija AI agenta, vključno z uporabo orodij, koraki orkestracije, procesi razmišljanja in spremljanjem zmogljivosti prek Microsoft Foundry nadzornih plošč.
- **Varnost** z gostovanjem agentov nativno na Microsoft Foundry, ki vključuje varnostne kontrole kot so dostop na osnovi vlog, obravnavo zasebnih podatkov in vgrajeno varnost vsebine.
- **Vzdržljivost**, saj se lahko agentne niti in delovni tokovi ustavijo, nadaljujejo in obnovijo po napakah, kar omogoča daljše procese.
- **Nadzor**, kjer so podprti delovni tokovi z vnosom človeka v zanko, kjer so naloge označene kot zahtevajo človeško odobritev.

Microsoft Agent Framework se prav tako osredotoča na interoperabilnost z:

- **Neodvisnostjo od oblaka** – Agenti lahko tečejo v kontejnerjih, lokalno ali preko različnih oblakov.
- **Neodvisnostjo od ponudnika** – Agenti se lahko ustvarijo z vašim priljubljenim SDK, vključno z Azure OpenAI in OpenAI.
- **Integracijo odprtih standardov** – Agenti lahko uporabljajo protokole, kot so Agent-to-Agent (A2A) in Model Context Protocol (MCP), za odkrivanje in uporabo drugih agentov in orodij.
- **Vtičniki in priključki** – Povezave se lahko vzpostavijo do podatkovnih in pomnilniških storitev, kot so Microsoft Fabric, SharePoint, Pinecone in Qdrant.

Poglejmo kako so te funkcije uporabljene v nekaterih osnovnih konceptih Microsoft Agent Framework.

## Ključni koncepti Microsoft Agent Framework

### Agenti

![Agent Framework](../../../translated_images/sl/agent-components.410a06daf87b4fef.webp)

**Ustvarjanje agentov**

Ustvarjanje agenta poteka z definiranjem storitve za sklepanje (LLM ponudnik), niza navodil, ki jim mora AI agent slediti, in dodeljenega `imena`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Zgornji primer uporablja `Azure OpenAI`, vendar se agenti lahko ustvarijo z različnimi storitvami, vključno z `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

API-ji OpenAI `Responses`, `ChatCompletion`

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

ali z uporabo oddaljenih agentov preko protokola A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Zagon agentov**

Agente se zažene z metodo `.run` ali `.run_stream` za nepretakan odgovor ali pretakanje.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Vsak zagon agenta lahko vsebuje tudi možnosti za prilagoditev parametrov, kot so `max_tokens`, ki jih agent uporablja, `orodja`, ki jih agent lahko pokliče, pa tudi sam `model`, uporabljen za agenta.

To je uporabno v primerih, kjer so za dokončanje uporabnikove naloge potrebni specifični modeli ali orodja.

**Orodja**

Orodja je mogoče definirati tako ob definiciji agenta:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Ko neposredno ustvarjate ChatAgent

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

kot tudi ob zagonu agenta:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Orodje zagotovljeno samo za to izvajanje )
```

**Agentne niti**

Agentne niti se uporabljajo za upravljanje večvrstičnih pogovorov. Niti se lahko ustvarijo na dva načina:

- Z uporabo `get_new_thread()`, ki omogoča shranjevanje niti skozi čas.
- Samodejno ob zagonu agenta, kjer nit traja le med trenutnim zagonom.

Za ustvarjanje niti izgledajo kode takole:

```python
# Ustvari novo nit.
thread = agent.get_new_thread() # Zaženi agenta z nitjo.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Nato lahko nit serializirate za shranjevanje za kasnejšo uporabo:

```python
# Ustvari novo nit.
thread = agent.get_new_thread() 

# Zaženi agenta z nitjo.

response = await agent.run("Hello, how are you?", thread=thread) 

# Seriliziraj nit za shranjevanje.

serialized_thread = await thread.serialize() 

# Deseriliziraj stanje niti po nalaganju iz shrambe.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agentni middleware**

Agenti sodelujejo z orodji in LLM-ji za izvedbo uporabnikovih nalog. V določenih scenarijih želimo izvršiti ali slediti dogajanju med temi interakcijami. Agentni middleware nam to omogoča preko:

*Funkcijski middleware*

Ta middleware omogoča izvedbo akcije med agentom in funkcijo/orodjem, ki ga kliče. Primer uporabe je, če želite zabeležiti klic funkcije.

V spodnji kodi `next` določa, ali se bo poklical naslednji middleware ali dejanska funkcija.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Predobdelava: Beleženje pred izvajanjem funkcije
    print(f"[Function] Calling {context.function.name}")

    # Nadaljuj na naslednji vmesni sloj ali izvajanje funkcije
    await next(context)

    # Poročanje po obdelavi: Beleženje po izvajanju funkcije
    print(f"[Function] {context.function.name} completed")
```

*Middleware klepeta*

Ta middleware nam omogoča izvedbo ali beleženje akcije med agentom in zahtevami do LLM.

Vsebuje pomembne informacije, kot so `messages`, ki se pošiljajo AI storitvi.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Predobdelava: Zabeleži pred klicem AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Nadaljuj na naslednjo vmesno programsko opremo ali AI storitev
    await next(context)

    # Poročanje: Zabeleži po odgovoru AI
    print("[Chat] AI response received")

```

**Agentni spomin**

Kot omenjeno v lekciji `Agentic Memory`, je spomin pomemben element, ki omogoča agentu delovanje v različnih kontekstih. MAF ponuja več različnih vrst spomina:

*Shranjevanje v spominu*

To je spomin, shranjen v nitih med izvajanjem aplikacije.

```python
# Ustvari novo nit.
thread = agent.get_new_thread() # Zaženi agenta z nitjo.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Vztrajne sporočilne zgodovine*

Ta spomin se uporablja za shranjevanje zgodovine pogovora med različnimi sejami. Definira se z uporabo `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Ustvari lasten skladišče sporočil
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dinamični spomin*

Ta spomin se doda v kontekst pred zagonom agentov. Ti spomini so lahko shranjeni v zunanjih storitvah, kot je mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Uporaba Mem0 za napredne zmogljivosti pomnilnika
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

**Agentna opazljivost**

Opazljivost je pomembna za gradnjo zanesljivih in vzdržljivih agentnih sistemov. MAF se integrira z OpenTelemetry, da zagotovi sledenje in metriko za boljšo opazljivost.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # naredi nekaj
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Delovni tokovi

MAF ponuja delovne tokove, ki so vnaprej definirani koraki za dokončanje naloge in vključujejo AI agente kot komponente teh korakov.

Delovni tokovi so sestavljeni iz različnih komponent, ki omogočajo boljšo kontrolo poteka. Omogočajo tudi **večagentno orkestracijo** in **shranjevanje stanj delovnega toka**.

Osnovne komponente delovnega toka so:

**Izvajalci**

Izvajalci sprejmejo vhodna sporočila, opravijo dodeljene naloge in proizvedejo izhodno sporočilo. S tem premikajo delovni tok naprej k dokončanju večje naloge. Izvajalec je lahko AI agent ali prilagojena logika.

**Povezave**

Povezave se uporabljajo za definicijo pretoka sporočil v delovnem toku. Te so lahko:

*Neposredne povezave* – enostavne ena-na-ena povezave med izvajalci:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Pogojne povezave* – aktivirajo se po izpolnitvi določenega pogoja. Na primer, če sobe v hotelu niso na voljo, lahko izvajalec predlaga druge možnosti.

*Povezave tipa switch-case* – usmerjajo sporočila različnim izvajalcem glede na definirane pogoje. Na primer če ima potnik prioriteto, se njegove naloge obravnavajo prek drugega delovnega toka.

*Razvejajoče povezave* – Pošljejo eno sporočilo več prejemnikom.

*Združevalne povezave* – Zberejo več sporočil iz različnih izvajalcev in jih pošljejo enemu cilju.

**Dogodki**

Za boljšo opazljivost delovnih tokov MAF ponuja vgrajene dogodke za izvajanje, med drugim:

- `WorkflowStartedEvent`  - Začetek izvajanja delovnega toka
- `WorkflowOutputEvent` - Delovni tok proizvaja izhod
- `WorkflowErrorEvent` - V delovnem toku nastopi napaka
- `ExecutorInvokeEvent`  - Izvajalec začne s procesiranjem
- `ExecutorCompleteEvent`  - Izvajalec konča procesiranje
- `RequestInfoEvent` - Izdan je zahtevek

## Migracija iz drugih ogrodij (Semantic Kernel in AutoGen)

### Razlike med MAF in Semantic Kernel

**Poenostavljeno ustvarjanje agentov**

Semantic Kernel zahteva ustvarjanje instance jedra (Kernel) za vsakega agenta. MAF uporablja poenostavljen pristop z razširitvami za glavne ponudnike.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Ustvarjanje agentnih niti**

Semantic Kernel zahteva ročno ustvarjanje niti. V MAF je agentu neposredno dodeljena nit.

```python
thread = agent.get_new_thread() # Zaženite agenta z nitjo.
```

**Registracija orodij**

V Semantic Kernel so orodja registrirana v jedro, ki se nato poda agentu. V MAF so orodja registrirana neposredno med ustvarjanjem agenta.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Razlike med MAF in AutoGen

**Teams vs Workflows**

`Teams` so struktura dogodkov za dogodkovno usmerjeno aktivnost z agenti v AutoGen. MAF uporablja `Workflows`, ki usmerjajo podatke do izvajalcev preko arhitekture na osnovi grafov.

**Ustvarjanje orodij**

AutoGen uporablja `FunctionTool` za ovijanje funkcij, ki jih agenti kličejo. MAF uporablja @ai_function, ki deluje podobno, vendar tudi samodejno sklepa sheme za vsako funkcijo.

**Obnašanje agentov**

Agenti so v AutoGen privzeto enostopenjski, razen če je nastavljen `max_tool_iterations` na višjo vrednost. V MAF je `ChatAgent` privzeto večstopenjski, kar pomeni, da bo vztrajno klical orodja, dokler uporabnikova naloga ni zaključena.

## Primeri kode

Primeri kode za Microsoft Agent Framework so na voljo v tem repozitoriju v datotekah `xx-python-agent-framework` in `xx-dotnet-agent-framework`.

## Imate več vprašanj o Microsoft Agent Framework?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), da se srečate z drugimi učenci, udeležite pisarnic in dobite odgovore na vaša vprašanja o AI agentih.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Omejitev odgovornosti**:  
Ta dokument je bil preveden z uporabo AI prevajalske storitve [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da avtomatizirani prevodi lahko vsebujejo napake ali netočnosti. Izvirni dokument v izvorni jezik je treba šteti za pooblastilo vir. Za pomembne informacije priporočamo strokovni človeški prevod. Nismo odgovorni za morebitne nesporazume ali napačne interpretacije, ki izhajajo iz uporabe tega prevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->