# Esplorando Microsoft Agent Framework

![Agent Framework](../../../translated_images/it/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introduzione

Questa lezione coprirà:

- Comprendere Microsoft Agent Framework: Caratteristiche chiave e valore  
- Esplorare i concetti chiave di Microsoft Agent Framework
- Confronto tra MAF, Semantic Kernel e AutoGen: Guida alla migrazione

## Obiettivi di Apprendimento

Al termine di questa lezione, saprai come:

- Costruire agenti AI pronti per la produzione usando Microsoft Agent Framework
- Applicare le caratteristiche principali di Microsoft Agent Framework ai tuoi casi d'uso agentici
- Migrare e integrare framework e strumenti agentici esistenti  

## Esempi di Codice 

Esempi di codice per [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) si trovano in questo repository nei file `xx-python-agent-framework` e `xx-dotnet-agent-framework`.

## Comprendere Microsoft Agent Framework

![Framework Intro](../../../translated_images/it/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) si basa sull’esperienza e sugli apprendimenti da Semantic Kernel e AutoGen. Offre la flessibilità per affrontare la vasta gamma di casi d'uso agentici visti sia in ambienti di produzione che di ricerca, inclusi:

- **Orchestrazione sequenziale degli agenti** in scenari dove sono necessari flussi di lavoro passo-passo.
- **Orchestrazione concorrente** in scenari dove gli agenti devono completare compiti contemporaneamente.
- **Orchestrazione di chat di gruppo** in scenari dove gli agenti possono collaborare insieme su un compito.
- **Orchestrazione del passaggio di consegne** in scenari dove gli agenti passano il compito tra loro man mano che i sotto-compiti sono completati.
- **Orchestrazione magnetica** in scenari dove un agente manager crea e modifica una lista di compiti e gestisce il coordinamento dei sotto-agenti per completare il compito.

Per fornire agenti AI in produzione, MAF include anche caratteristiche per:

- **Osservabilità** attraverso l'uso di OpenTelemetry dove ogni azione dell'agente AI, inclusa l'invocazione di strumenti, i passaggi di orchestrazione, i flussi di ragionamento e il monitoraggio delle prestazioni tramite i dashboard di Microsoft Foundry.
- **Sicurezza** ospitando gli agenti nativamente su Microsoft Foundry che include controlli di sicurezza quali accesso basato su ruoli, gestione dei dati privati e sicurezza dei contenuti integrata.
- **Durabilità** poiché i thread e i flussi di lavoro degli agenti possono mettere in pausa, riprendere e recuperare dagli errori, consentendo processi più lunghi.
- **Controllo** con workflow human-in-the-loop supportati dove i compiti sono contrassegnati come richiedenti approvazione umana.

Microsoft Agent Framework si concentra inoltre sull'interoperabilità tramite:

- **Essere cloud-agnostico** - Gli agenti possono girare in container, on-premise e su molteplici diversi cloud.
- **Essere provider-agnostico** - Gli agenti possono essere creati tramite il tuo SDK preferito inclusi Azure OpenAI e OpenAI
- **Integrazione di standard aperti** - Gli agenti possono utilizzare protocolli come Agent-to-Agent (A2A) e Model Context Protocol (MCP) per scoprire e usare altri agenti e strumenti.
- **Plugin e connettori** - Si possono effettuare connessioni a servizi di dati e memoria come Microsoft Fabric, SharePoint, Pinecone e Qdrant.

Vediamo come queste caratteristiche sono applicate ad alcuni concetti chiave di Microsoft Agent Framework.

## Concetti Chiave di Microsoft Agent Framework

### Agenti

![Agent Framework](../../../translated_images/it/agent-components.410a06daf87b4fef.webp)

**Creazione degli Agenti**

La creazione di un agente avviene definendo il servizio di inferenza (fornitore LLM), una serie di istruzioni che l'agente AI deve seguire e un `nome` assegnato:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

L'esempio sopra utilizza `Azure OpenAI` ma gli agenti possono essere creati usando diversi servizi incluso `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

API OpenAI `Responses`, `ChatCompletion`

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

o agenti remoti usando il protocollo A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Esecuzione degli Agenti**

Gli agenti vengono eseguiti usando i metodi `.run` o `.run_stream` rispettivamente per risposte non in streaming o in streaming.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Ogni esecuzione dell’agente può inoltre avere opzioni per personalizzare parametri come `max_tokens` usati dall’agente, gli `tools` a cui l'agente può accedere e persino il `model` utilizzato dall’agente.

Questo è utile in casi dove modelli o strumenti specifici sono richiesti per completare il compito dell'utente.

**Strumenti**

Gli strumenti possono essere definiti sia durante la definizione dell'agente:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Quando si crea direttamente un ChatAgent

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

sia durante l'esecuzione dell'agente:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Strumento fornito solo per questa esecuzione )
```

**Thread degli Agenti**

I thread degli agenti sono usati per gestire conversazioni multi-turno. I thread possono essere creati in due modi:

- Usando `get_new_thread()` che consente al thread di essere salvato nel tempo
- Creando automaticamente un thread durante l'esecuzione di un agente in modo che il thread persista solo durante l'esecuzione corrente.

Per creare un thread, il codice è simile a questo:

```python
# Crea un nuovo thread.
thread = agent.get_new_thread() # Esegui l'agente con il thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Il thread può poi essere serializzato per essere memorizzato per un uso successivo:

```python
# Crea un nuovo thread.
thread = agent.get_new_thread() 

# Esegui l'agente con il thread.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serializza il thread per la memorizzazione.

serialized_thread = await thread.serialize() 

# Deserializza lo stato del thread dopo il caricamento dalla memoria.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware degli Agenti**

Gli agenti interagiscono con strumenti e LLM per completare i compiti degli utenti. In certi scenari, vogliamo eseguire o tracciare azioni tra queste interazioni. Il middleware degli agenti ci permette di farlo tramite:

*Middleware Funzionale*

Questo middleware permette di eseguire un’azione tra l’agente e una funzione/strumento che esso chiamerà. Un esempio di utilizzo è fare logging sulla chiamata alla funzione.

Nel codice sottostante, `next` definisce se deve essere chiamato il middleware successivo o la funzione vera e propria.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Pre-elaborazione: Registra prima dell'esecuzione della funzione
    print(f"[Function] Calling {context.function.name}")

    # Continua al middleware successivo o all'esecuzione della funzione
    await next(context)

    # Post-elaborazione: Registra dopo l'esecuzione della funzione
    print(f"[Function] {context.function.name} completed")
```

*Middleware Chat*

Questo middleware consente di eseguire o registrare un’azione tra l’agente e le richieste tra l’LLM.

Contiene informazioni importanti come i `messages` che vengono inviati al servizio AI.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Pre-elaborazione: registra prima della chiamata all'IA
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Continua al middleware o servizio IA successivo
    await next(context)

    # Post-elaborazione: registra dopo la risposta dell'IA
    print("[Chat] AI response received")

```

**Memoria degli Agenti**

Come trattato nella lezione `Agentic Memory`, la memoria è un elemento importante per permettere all’agente di operare su contesti diversi. MAF offre diversi tipi di memorie:

*Archiviazione In-Memory*

Questa è la memoria conservata nei thread durante il runtime dell’applicazione.

```python
# Crea un nuovo thread.
thread = agent.get_new_thread() # Esegui l'agente con il thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Messaggi Persistenti*

Questa memoria è usata per mantenere la cronologia della conversazione attraverso diverse sessioni. È definita tramite `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Crea un archivio di messaggi personalizzato
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Memoria Dinamica*

Questa memoria viene aggiunta al contesto prima che gli agenti vengano eseguiti. Queste memorie possono essere archiviate in servizi esterni come mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Uso di Mem0 per capacità di memoria avanzate
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

**Osservabilità degli Agenti**

L’osservabilità è importante per costruire sistemi agentici affidabili e mantenibili. MAF integra OpenTelemetry per fornire tracing e contatori per una migliore osservabilità.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # fare qualcosa
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Workflow

MAF offre workflow che sono passi predefiniti per completare un compito e includono agenti AI come componenti di questi passi.

I workflow sono composti da diversi componenti che permettono un migliore controllo del flusso. Consentono anche **orchestrazione multi-agente** e **checkpointing** per salvare gli stati del workflow.

I componenti principali di un workflow sono:

**Esecutori**

Gli esecutori ricevono messaggi di input, svolgono i compiti assegnati e producono un messaggio di output. Questo fa avanzare il workflow verso il completamento del compito più ampio. Gli esecutori possono essere agenti AI o logica personalizzata.

**Bordi**

I bordi sono usati per definire il flusso dei messaggi all'interno di un workflow. Questi possono essere:

*Bordi Diretti* - Connessioni semplici uno a uno tra gli esecutori:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Bordi Condizionali* - Attivati dopo che una certa condizione è soddisfatta. Ad esempio, quando le camere d’albergo non sono disponibili, un esecutore può suggerire altre opzioni.

*Bordi a scelta multipla (switch-case)* - Instradano messaggi verso diversi esecutori basati su condizioni definite. Ad esempio, se un cliente di viaggi ha accesso prioritario e i suoi compiti saranno gestiti tramite un altro workflow.

*Bordi di fan-out* - Invia un messaggio a più destinazioni.

*Bordi di fan-in* - Raccoglie più messaggi da diversi esecutori e li invia a una destinazione.

**Eventi**

Per fornire migliore osservabilità nei workflow, MAF offre eventi integrati per l’esecuzione tra cui:

- `WorkflowStartedEvent`  - Inizio esecuzione workflow
- `WorkflowOutputEvent` - Workflow produce un output
- `WorkflowErrorEvent` - Workflow riscontra un errore
- `ExecutorInvokeEvent`  - L’esecutore inizia l’elaborazione
- `ExecutorCompleteEvent`  -  L’esecutore termina l’elaborazione
- `RequestInfoEvent` - Viene emessa una richiesta

## Migrazione da Altri Framework (Semantic Kernel e AutoGen)

### Differenze tra MAF e Semantic Kernel

**Creazione semplificata degli agenti**

Semantic Kernel si basa sulla creazione di un'istanza Kernel per ogni agente. MAF usa un approccio semplificato usando estensioni per i principali provider.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Creazione dei Thread degli Agenti**

Semantic Kernel richiede che i thread siano creati manualmente. In MAF, il thread è assegnato direttamente all’agente.

```python
thread = agent.get_new_thread() # Esegui l'agente con il thread.
```

**Registrazione degli Strumenti**

In Semantic Kernel gli strumenti sono registrati al Kernel e quest’ultimo viene passato all’agente. In MAF, gli strumenti sono registrati direttamente durante il processo di creazione dell’agente.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Differenze tra MAF e AutoGen

**Teams vs Workflows**

`Teams` sono la struttura eventi per attività guidata da eventi con agenti in AutoGen. MAF usa `Workflows` che instradano dati agli esecutori attraverso un'architettura basata su grafo.

**Creazione degli Strumenti**

AutoGen usa `FunctionTool` per incapsulare funzioni che gli agenti possono chiamare. MAF usa @ai_function che funziona in modo simile ma deduce anche automaticamente gli schemi per ogni funzione.

**Comportamento degli Agenti**

Gli agenti sono agenti a singolo turno di default in AutoGen, a meno che `max_tool_iterations` non sia impostato a un valore più alto. In MAF il `ChatAgent` è multi-turno di default, il che significa che continuerà a chiamare strumenti finché il compito dell'utente non sarà completato.

## Esempi di Codice 

Gli esempi di codice per Microsoft Agent Framework si trovano in questo repository nei file `xx-python-agent-framework` e `xx-dotnet-agent-framework`.

## Hai altre domande su Microsoft Agent Framework?

Unisciti al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) per incontrare altri studenti, partecipare agli orari di ufficio e ricevere risposte alle tue domande sugli agenti AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Avvertenza**:  
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica [Co-op Translator](https://github.com/Azure/co-op-translator). Pur impegnandoci per l’accuratezza, si prega di notare che le traduzioni automatiche potrebbero contenere errori o inesattezze. Il documento originale nella sua lingua madre deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda una traduzione professionale effettuata da un traduttore umano. Non ci assumiamo alcuna responsabilità per eventuali malintesi o interpretazioni errate derivanti dall’uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->