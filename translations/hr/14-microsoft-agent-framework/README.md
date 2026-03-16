# Istraživanje Microsoft Agent Frameworka

![Okvir agenata](../../../translated_images/hr/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Uvod

Ova lekcija će obuhvatiti:

- Razumijevanje Microsoft Agent Frameworka: ključne značajke i vrijednost  
- Istraživanje ključnih koncepata Microsoft Agent Frameworka
- Usporedba MAF-a sa Semantic Kernel i AutoGen: vodič za migraciju

## Ciljevi učenja

Nakon dovršetka ove lekcije znat ćete kako:

- Izgraditi AI agente spremne za produkciju koristeći Microsoft Agent Framework
- Primijeniti osnovne značajke Microsoft Agent Frameworka na vaše agentne slučajeve upotrebe
- Migrirati i integrirati postojeće agentne okvire i alate  

## Primjeri koda

Primjeri koda za [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) mogu se pronaći u ovom spremištu pod `xx-python-agent-framework` i `xx-dotnet-agent-framework` datotekama.

## Razumijevanje Microsoft Agent Frameworka

![Uvod u okvir](../../../translated_images/hr/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) nadograđuje se na iskustva i spoznaje iz Semantic Kernel i AutoGen. Nudi fleksibilnost za rješavanje širokog spektra agentnih slučajeva upotrebe viđenih u produkciji i istraživanju, uključujući:

- **Sekvencijalna orkestracija agenata** u scenarijima gdje su potrebni korak-po-korak radni tokovi.
- **Istovremena orkestracija** u scenarijima gdje agenti trebaju dovršiti zadatke istovremeno.
- **Orkestracija grupnog chata** u scenarijima gdje agenti mogu surađivati na jednom zadatku.
- **Handoff orkestracija** u scenarijima gdje agenti prepuštaju zadatak jedni drugima kako se podzadatci dovršavaju.
- **Magnetic orkestracija** u scenarijima gdje menadžerski agent stvara i mijenja popis zadataka i upravlja koordinacijom podagenata za dovršetak zadatka.

Za isporuku AI agenata u produkciji, MAF također uključuje značajke za:

- **Promatrivost** kroz upotrebu OpenTelemetry gdje je svaka akcija AI agenta uključujući poziv alata, korake orkestracije, tokove rezoniranja i nadzor performansi prikazana putem Microsoft Foundry nadzornih ploča.
- **Sigurnost** hostanjem agenata nativno na Microsoft Foundry koja uključuje sigurnosne kontrole poput pristupa temeljenog na ulogama, rukovanja privatnim podacima i ugrađene sigurnosti sadržaja.
- **Trajnost** budući da se agentni niti i radni tokovi mogu pauzirati, nastaviti i oporaviti od pogrešaka što omogućuje dugotrajnije procese.
- **Kontrola** jer su podržani radni tokovi s ljudskim sudjelovanjem gdje su zadaci označeni kao zahtijevajući ljudsko odobrenje.

Microsoft Agent Framework također je usmjeren na interoperabilnost kroz:

- **Biti neovisan o oblaku** - Agenti mogu raditi u kontejnerima, on-prem i preko više različitih oblaka.
- **Biti neovisan o davatelju** - Agenti se mogu kreirati putem vašeg preferiranog SDK-a uključujući Azure OpenAI i OpenAI
- **Integracija otvorenih standarda** - Agenti mogu koristiti protokole poput Agent-to-Agent (A2A) i Model Context Protocol (MCP) za otkrivanje i korištenje drugih agenata i alata.
- **Pluginovi i konektori** - Mogu se uspostaviti veze s podacima i memorijskim servisima poput Microsoft Fabric, SharePoint, Pinecone i Qdrant.

Pogledajmo kako se ove značajke primjenjuju na neke od temeljnih koncepata Microsoft Agent Frameworka.

## Ključni koncepti Microsoft Agent Frameworka

### Agenti

![Okvir agenata](../../../translated_images/hr/agent-components.410a06daf87b4fef.webp)

**Kreiranje agenata**

Kreiranje agenta vrši se definiranjem servisa za inferenciju (LLM Provider), skupa uputa koje AI agent treba slijediti i dodijeljenog `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Gore koristi `Azure OpenAI` ali agenti se mogu stvarati pomoću različitih servisa uključujući `Microsoft Foundry Agent Service`:

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

ili udaljene agente koristeći A2A protokol:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Pokretanje agenata**

Agenti se pokreću korištenjem metoda `.run` ili `.run_stream` za ne-streaming ili streaming odgovore.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Svako izvođenje agenta također može imati opcije za prilagodbu parametara kao što su `max_tokens` koje agent koristi, `tools` koje agent može pozivati, pa čak i sam `model` koji se koristi za agenta.

Ovo je korisno u slučajevima kada su potrebni specifični modeli ili alati za dovršetak zadatka korisnika.

**Alati**

Alati se mogu definirati i prilikom definiranja agenta:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Prilikom izravnog stvaranja ChatAgenta

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

i također prilikom pokretanja agenta:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Alat je dostavljen samo za ovo pokretanje )
```

**Agentne niti**

Agentne niti služe za rukovanje višekratnim razgovorima. Niti se mogu stvoriti na jedan od sljedećih načina:

- Korištenjem `get_new_thread()` što omogućuje da se nit sprema kroz vrijeme
- Automatskim stvaranjem niti prilikom pokretanja agenta pri čemu nit traje samo tijekom trenutnog izvođenja.

Za stvaranje niti, kod izgleda ovako:

```python
# Stvori novu nit.
thread = agent.get_new_thread() # Pokreni agenta s tom niti.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Nakon toga nit možete serijalizirati za pohranu za kasniju upotrebu:

```python
# Stvori novu nit.
thread = agent.get_new_thread() 

# Pokreni agenta s nitom.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serijaliziraj nit za pohranu.

serialized_thread = await thread.serialize() 

# Deserijaliziraj stanje niti nakon učitavanja iz pohrane.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent Middleware**

Agenti komuniciraju s alatima i LLM-ovima kako bi dovršili zadatke korisnika. U određenim scenarijima želimo izvršiti ili pratiti što se događa između tih interakcija. Agent middleware nam to omogućuje kroz:

*Function Middleware*

Ovaj middleware omogućuje nam izvršavanje akcije između agenta i funkcije/alata koji će se pozivati. Primjer kada bi se to koristilo je kada želite zapisivati logove o pozivu funkcije.

U donjem kodu `next` definira hoće li se pozvati sljedeći middleware ili stvarna funkcija.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Predobrada: Zabilježi prije izvršavanja funkcije
    print(f"[Function] Calling {context.function.name}")

    # Nastavi na sljedeći middleware ili izvršavanje funkcije
    await next(context)

    # Naknadna obrada: Zabilježi nakon izvršavanja funkcije
    print(f"[Function] {context.function.name} completed")
```

*Chat Middleware*

Ovaj middleware omogućuje nam izvršavanje ili bilježenje akcije između agenta i zahtjeva prema LLM-u.

Ovo sadrži važne informacije poput `messages` koje se šalju AI servisu.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Predobrada: Zabilježi prije poziva AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Nastavi na sljedeći middleware ili AI uslugu
    await next(context)

    # Postobrada: Zabilježi nakon odgovora AI
    print("[Chat] AI response received")

```

**Agentna memorija**

Kao što je obrađeno u lekciji `Agentic Memory`, memorija je važan element koji omogućuje agentu rad u različitim kontekstima. MAF nudi nekoliko različitih tipova memorija:

*Memorija u radnom prostoru (In-Memory Storage)*

Ovo je memorija pohranjena u nitima tijekom rada aplikacije.

```python
# Stvori novu nit.
thread = agent.get_new_thread() # Pokreni agenta s nitom.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Trajne poruke (Persistent Messages)*

Ova se memorija koristi za pohranu povijesti razgovora kroz različite sesije. Definira se pomoću `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Stvorite prilagođeno spremište poruka
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dinamička memorija*

Ova se memorija dodaje u kontekst prije nego što se agenti pokrenu. Te se memorije mogu pohraniti u vanjskim servisima poput mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Korištenje Mem0 za napredne memorijske mogućnosti
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

**Agentna promatrivost**

Promatrivost je važna za izgradnju pouzdanih i održivih agentnih sustava. MAF se integrira s OpenTelemetry za pružanje praćenja i mjera za bolju promatrivost.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # uradi nešto
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Radni tokovi

MAF nudi radne tokove koji su unaprijed definirani koraci za dovršetak zadatka i uključuju AI agente kao komponente u tim koracima.

Radni tokovi se sastoje od različitih komponenti koje omogućuju bolju kontrolu toka. Radni tokovi također omogućuju **orkestraciju više agenata** i **checkpointing** za spremanje stanja radnog toka.

Temeljne komponente radnog toka su:

**Izvršitelji (Executors)**

Izvršitelji primaju ulazne poruke, obavljaju zadane zadatke i zatim proizvode izlaznu poruku. To pomiče radni tok prema dovršetku većeg zadatka. Izvršitelji mogu biti AI agenti ili prilagođena logika.

**Ivice (Edges)**

Ivice se koriste za definiranje toka poruka u radnom toku. One mogu biti:

*Direktne ivice* - Jednostavne veze jedan-na-jedan između izvršitelja:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Uvjetne ivice* - Aktiviraju se nakon što je ispunjen određeni uvjet. Na primjer, kada sobe u hotelu nisu dostupne, izvršitelj može predložiti druge opcije.

*Switch-case ivice* - Usmjeravaju poruke različitim izvršiteljima na temelju definiranih uvjeta. Na primjer, ako putnik ima prioritetni pristup, njegovi će se zadaci obraditi kroz drugi radni tok.

*Fan-out ivice* - Šalju jednu poruku na više ciljeva.

*Fan-in ivice* - Prikupljaju više poruka od različitih izvršitelja i šalju ih jednom cilju.

**Događaji**

Kako bi se pružila bolja promatrivost radnih tokova, MAF nudi ugrađene događaje za izvršenje, uključujući:

- `WorkflowStartedEvent`  - pokretanje izvršavanja radnog toka
- `WorkflowOutputEvent` - radni tok proizvodi izlaz
- `WorkflowErrorEvent` - radni tok nailazi na pogrešku
- `ExecutorInvokeEvent`  - izvršitelj počinje s obradom
- `ExecutorCompleteEvent`  - izvršitelj završava obradu
- `RequestInfoEvent` - izdaje se zahtjev

## Migracija iz drugih okvira (Semantic Kernel i AutoGen)

### Razlike između MAF-a i Semantic Kernel-a

**Pojednostavljeno stvaranje agenata**

Semantic Kernel se oslanja na stvaranje instance Kernela za svakog agenta. MAF koristi pojednostavljeni pristup koristeći ekstenzije za glavne pružatelje.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Stvaranje agentnih niti**

Semantic Kernel zahtijeva ručno stvaranje niti. U MAF-u agentu se izravno dodjeljuje nit.

```python
thread = agent.get_new_thread() # Pokreni agenta u niti.
```

**Registracija alata**

U Semantic Kernel-u alati se registriraju u Kernel, a Kernel se potom prosljeđuje agentu. U MAF-u alati se registriraju izravno tijekom procesa stvaranja agenta.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Razlike između MAF-a i AutoGen-a

**Teams vs Workflows**

`Teams` su struktura događaja za aktivnosti vođene događajima s agentima u AutoGen-u. MAF koristi `Workflows` koji usmjeravaju podatke izvršiteljima kroz arhitekturu temeljenu na grafu.

**Stvaranje alata**

AutoGen koristi `FunctionTool` za omatanje funkcija koje agenti pozivaju. MAF koristi @ai_function koji radi slično, ali također automatski izvodi sheme za svaku funkciju.

**Ponašanje agenata**

Agenți su po defaultu jednokratni (single-turn) u AutoGen-u osim ako se `max_tool_iterations` ne postavi na veću vrijednost. U okviru MAF `ChatAgent` je po defaultu višekratni (multi-turn), što znači da će nastaviti pozivati alate dok se zadatak korisnika ne dovrši.

## Primjeri koda

Primjeri koda za Microsoft Agent Framework mogu se pronaći u ovom spremištu pod `xx-python-agent-framework` i `xx-dotnet-agent-framework` datotekama.

## Imate li još pitanja o Microsoft Agent Frameworku?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) da biste se povezali s drugim učenicima, sudjelovali na radnim satima i dobili odgovore na pitanja o AI agentima.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Odricanje odgovornosti:
Ovaj je dokument preveden pomoću AI usluge za prevođenje [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo biti točni, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za kritične informacije preporučuje se profesionalan prijevod od strane ljudskog prevoditelja. Ne odgovaramo za bilo kakve nesporazume ili pogrešna tumačenja koja proizlaze iz korištenja ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->