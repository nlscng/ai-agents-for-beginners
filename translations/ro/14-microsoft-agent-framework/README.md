# Explorarea Microsoft Agent Framework

![Framework pentru agenți](../../../translated_images/ro/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introducere

Această lecție va acoperi:

- Înțelegerea Microsoft Agent Framework: Caracteristici cheie și valoare  
- Explorarea conceptelor cheie ale Microsoft Agent Framework
- Compararea MAF cu Semantic Kernel și AutoGen: Ghid de migrare

## Obiective de învățare

După parcurgerea acestei lecții, veți ști cum să:

- Dezvoltați agenți AI pregătiți pentru producție folosind Microsoft Agent Framework
- Aplicați funcționalitățile de bază ale Microsoft Agent Framework la cazurile dvs. de utilizare agentice
- Migrați și integrați framework-uri și instrumente agentice existente  

## Exemple de cod 

Code samples for [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) can be found in this repository under `xx-python-agent-framework` and `xx-dotnet-agent-framework` files.

## Înțelegerea Microsoft Agent Framework

![Introducere în Framework](../../../translated_images/ro/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) se bazează pe experiența și învățăturile din Semantic Kernel și AutoGen. Oferă flexibilitatea de a aborda o gamă largă de cazuri de utilizare agentice întâlnite atât în medii de producție, cât și de cercetare, inclusiv:

- **Orchestrare secvențială a agenților** în scenarii în care sunt necesare fluxuri de lucru pas cu pas.
- **Orchestrare concurentă** în scenarii în care agenții trebuie să finalizeze sarcini în același timp.
- **Orchestrare pentru chat de grup** în scenarii în care agenții pot colabora împreună la o singură sarcină.
- **Orchestrare de predare** în scenarii în care agenții predă sarcina unul altuia pe măsură ce sub-sarcinile sunt finalizate.
- **Orchestrare magnetică** în scenarii în care un agent manager creează și modifică o listă de sarcini și se ocupă de coordonarea subagenților pentru a finaliza sarcina.

Pentru a livra agenți AI în producție, MAF include și funcționalități pentru:

- **Observabilitate** prin utilizarea OpenTelemetry, unde fiecare acțiune a agentului AI, inclusiv apelul instrumentelor, pașii de orchestrare, fluxurile de raționament și monitorizarea performanței sunt vizibile prin panourile Microsoft Foundry.
- **Securitate** prin găzduirea agenților nativ pe Microsoft Foundry, care include controale de securitate precum accesul bazat pe roluri, gestionarea datelor private și protecția conținutului încorporată.
- **Durabilitate** deoarece firele și fluxurile de lucru ale agenților pot fi întrerupte, reluate și recuperate după erori, permițând procese care rulează pe durate mai lungi.
- **Control** deoarece sunt suportate fluxuri de lucru cu intervenție umană, în care sarcinile sunt marcate ca necesitând aprobare umană.

Microsoft Agent Framework se concentrează, de asemenea, pe interoperabilitate prin:

- **Independenți de cloud** - Agenții pot rula în containere, on‑premises și în mai multe cloud-uri diferite.
- **Agnostici în privința furnizorului** - Agenții pot fi creați prin SDK-ul preferat, inclusiv Azure OpenAI și OpenAI
- **Integrarea standardelor deschise** - Agenții pot utiliza protocoale precum Agent-to-Agent (A2A) și Model Context Protocol (MCP) pentru a descoperi și folosi alți agenți și instrumente.
- **Pluginuri și conectori** - Pot fi realizate conexiuni la servicii de date și memorie precum Microsoft Fabric, SharePoint, Pinecone și Qdrant.

Să vedem cum sunt aplicate aceste funcționalități unor dintre conceptele cheie ale Microsoft Agent Framework.

## Concepte cheie ale Microsoft Agent Framework

### Agenți

![Framework pentru agenți](../../../translated_images/ro/agent-components.410a06daf87b4fef.webp)

**Crearea agenților**

Crearea agenților se realizează prin definirea serviciului de inferență (furnizor LLM), a unui set de instrucțiuni pe care agentul AI trebuie să le urmeze și a unui `name` atribuit:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Exemplul de mai sus folosește `Azure OpenAI`, dar agenții pot fi creați folosind o varietate de servicii, inclusiv `Microsoft Foundry Agent Service`:

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

sau agenți de la distanță folosind protocolul A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Rularea agenților**

Agenții sunt rulați folosind metodele `.run` sau `.run_stream` pentru răspunsuri fără streaming sau cu streaming.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Fiecare execuție a unui agent poate avea, de asemenea, opțiuni pentru a personaliza parametri precum `max_tokens` folosit de agent, `tools` pe care agentul le poate apela și chiar `model` folosit de agent.

Acest lucru este util în cazurile în care sunt necesare modele sau instrumente specifice pentru a finaliza sarcina unui utilizator.

**Instrumente**

Instrumentele pot fi definite atât la definirea agentului:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Când se creează un ChatAgent direct

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

și de asemenea când se rulează agentul:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Instrument furnizat doar pentru această rulare )
```

**Fire ale agenților**

Firele agenților sunt folosite pentru a gestiona conversații multi-turn. Firele pot fi create fie prin:

- Utilizarea `get_new_thread()` care permite salvarea firului în timp
- Crearea automată a unui fir la rularea unui agent, fir care există doar pe durata execuției curente.

Pentru a crea un fir, codul arată astfel:

```python
# Creează un fir de execuție nou.
thread = agent.get_new_thread() # Rulează agentul folosind firul de execuție.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Apoi puteți serializa firul pentru a fi stocat pentru utilizare ulterioară:

```python
# Creează un fir de execuție nou.
thread = agent.get_new_thread() 

# Rulează agentul pe fir.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serializează firul pentru stocare.

serialized_thread = await thread.serialize() 

# Deserializează starea firului după încărcarea din stocare.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware pentru agenți**

Agenții interacționează cu instrumente și LLM-uri pentru a finaliza sarcinile utilizatorilor. În anumite scenarii, dorim să executăm sau să urmărim interacțiunile dintre acestea. Middleware-ul pentru agenți ne permite să facem acest lucru prin:

*Middleware de funcții*

Acest middleware ne permite să executăm o acțiune între agent și o funcție/instrument pe care îl va apela. Un exemplu de utilizare este când doriți să realizați înregistrări (logging) la apelul funcției.

În codul de mai jos, `next` definește dacă trebuie apelat următorul middleware sau funcția propriu-zisă.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Pre-procesare: Jurnalizare înainte de executarea funcției
    print(f"[Function] Calling {context.function.name}")

    # Continuă la următorul middleware sau la executarea funcției
    await next(context)

    # Post-procesare: Jurnalizare după executarea funcției
    print(f"[Function] {context.function.name} completed")
```

*Middleware de chat*

Acest middleware ne permite să executăm sau să înregistrăm o acțiune între agent și solicitările către LLM.

Acesta conține informații importante, cum ar fi `messages` care sunt trimise către serviciul AI.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Preprocesare: Înregistrare înainte de apelul AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Continuați la următorul middleware sau serviciu AI
    await next(context)

    # Postprocesare: Înregistrare după răspunsul AI
    print("[Chat] AI response received")

```

**Memoria agenților**

După cum s-a acoperit în lecția `Agentic Memory`, memoria este un element important pentru a permite agentului să opereze în diferite contexte. MAF oferă mai multe tipuri de memorii:

*Stocare în memorie*

Aceasta este memoria stocată în fire pe durata rulării aplicației.

```python
# Creează un fir nou.
thread = agent.get_new_thread() # Rulează agentul cu firul.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Mesaje persistente*

Această memorie este folosită pentru stocarea istoricului conversațiilor între diferite sesiuni. Este definită folosind `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Creați un depozit personalizat de mesaje
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Memorie dinamică*

Această memorie este adăugată în context înainte ca agenții să fie rulați. Aceste memorii pot fi stocate în servicii externe precum mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Folosind Mem0 pentru capabilități avansate de memorie
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

**Observabilitatea agenților**

Observabilitatea este importantă pentru construirea unor sisteme agentice fiabile și ușor de întreținut. MAF se integrează cu OpenTelemetry pentru a oferi trasare și metri pentru o observabilitate mai bună.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # fă ceva
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Fluxuri de lucru

MAF oferă fluxuri de lucru care sunt pași predefiniți pentru a finaliza o sarcină și includ agenți AI ca componente în acești pași.

Fluxurile de lucru sunt compuse din diferite componente care permit un control mai bun al fluxului. Fluxurile de lucru permit de asemenea **orchestrare multi-agent** și **checkpointing** pentru a salva stările fluxului de lucru.

Componentele de bază ale unui flux de lucru sunt:

**Executorii**

Executorii primesc mesaje de intrare, își îndeplinesc sarcinile atribuite și apoi produc un mesaj de ieșire. Acest lucru propulsează fluxul de lucru înainte, spre finalizarea sarcinii mai ample. Executorii pot fi fie agenți AI, fie logică personalizată.

**Conexiuni**

Conexiunile sunt folosite pentru a defini fluxul mesajelor într-un flux de lucru. Acestea pot fi:

*Conexiuni directe* - Conexiuni simple unu-la-unu între executori:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Conexiuni condiționate* - Activate după îndeplinirea unei anumite condiții. De exemplu, când camerele de hotel nu sunt disponibile, un executor poate sugera alte opțiuni.

*Conexiuni switch-case* - Direcționează mesajele către diferiți executori pe baza unor condiții definite. De exemplu, dacă un client de călătorie are acces prioritar, sarcinile lor vor fi gestionate printr-un alt flux de lucru.

*Conexiuni de tip fan-out* - Trimite un mesaj către multiple destinații.

*Conexiuni de tip fan-in* - Colectează multiple mesaje de la diferiți executori și le trimite către o singură destinație.

**Evenimente**

Pentru a oferi o observabilitate mai bună a fluxurilor de lucru, MAF oferă evenimente încorporate pentru execuție, inclusiv:

- `WorkflowStartedEvent`  - Execuția fluxului de lucru începe
- `WorkflowOutputEvent` - Fluxul de lucru produce un rezultat
- `WorkflowErrorEvent` - Fluxul de lucru întâmpină o eroare
- `ExecutorInvokeEvent`  - Executorul începe procesarea
- `ExecutorCompleteEvent`  -  Executorul termină procesarea
- `RequestInfoEvent` - Se emite o cerere

## Migrarea din alte framework-uri (Semantic Kernel și AutoGen)

### Diferențe între MAF și Semantic Kernel

**Creare simplificată a agenților**

Semantic Kernel se bazează pe crearea unei instanțe Kernel pentru fiecare agent. MAF folosește o abordare simplificată, utilizând extensii pentru principalii furnizori.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Crearea firelor agenților**

Semantic Kernel cere ca firele să fie create manual. În MAF, agentului i se atribuie direct un fir.

```python
thread = agent.get_new_thread() # Rulează agentul cu firul de execuție.
```

**Înregistrarea instrumentelor**

În Semantic Kernel, instrumentele sunt înregistrate în Kernel, iar Kernel-ul este apoi transmis agentului. În MAF, instrumentele sunt înregistrate direct în timpul procesului de creare a agentului.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Diferențe între MAF și  AutoGen

**Teams vs Workflows**

`Teams` reprezintă structura de evenimente pentru activități conduse de evenimente cu agenți în AutoGen. MAF folosește `Workflows` care direcționează date către executori printr-o arhitectură bazată pe graf.

**Crearea instrumentelor**

AutoGen folosește `FunctionTool` pentru a înfășura funcțiile pe care agenții le pot apela. MAF folosește @ai_function care funcționează similar, dar deduce și schemele în mod automat pentru fiecare funcție.

**Comportamentul agenților**

Agenții sunt agenți single-turn implicit în AutoGen, cu excepția cazului în care `max_tool_iterations` este setat la o valoare mai mare. În MAF, `ChatAgent` este multi-turn implicit, ceea ce înseamnă că va continua să apeleze instrumente până când sarcina utilizatorului este finalizată.

## Exemple de cod 

Exemplele de cod pentru Microsoft Agent Framework pot fi găsite în acest depozit în fișierele `xx-python-agent-framework` și `xx-dotnet-agent-framework`.

## Aveți mai multe întrebări despre Microsoft Agent Framework?

Alăturați-vă [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la ore de consultanță și a obține răspunsuri la întrebările dvs. despre agenți AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Declinare de responsabilitate:
Acest document a fost tradus folosind serviciul de traducere AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original în limba sa nativă ar trebui să fie considerat sursa autorizată. Pentru informații critice, se recomandă o traducere profesională realizată de un traducător uman. Nu ne asumăm răspunderea pentru eventuale neînțelegeri sau interpretări greșite rezultate din utilizarea acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->