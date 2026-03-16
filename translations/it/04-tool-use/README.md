[![Come Progettare Buoni Agenti AI](../../../translated_images/it/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Clicca sull'immagine sopra per vedere il video di questa lezione)_

# Pattern di Progettazione per l'Uso di Strumenti

Gli strumenti sono interessanti perché permettono agli agenti AI di avere una gamma più ampia di capacità. Invece di avere un insieme limitato di azioni che può compiere, aggiungendo uno strumento, l'agente può ora eseguire una vasta gamma di azioni. In questo capitolo, esamineremo il Pattern di Progettazione per l'Uso di Strumenti, che descrive come gli agenti AI possono utilizzare strumenti specifici per raggiungere i loro obiettivi.

## Introduzione

In questa lezione, cerchiamo di rispondere alle seguenti domande:

- Cos'è il pattern di progettazione per l'uso di strumenti?
- Quali sono i casi d'uso a cui può essere applicato?
- Quali sono gli elementi/blocchi costitutivi necessari per implementare il pattern di progettazione?
- Quali sono le considerazioni speciali per utilizzare il Pattern di Progettazione per l'Uso di Strumenti per costruire agenti AI affidabili?

## Obiettivi di Apprendimento

Dopo aver completato questa lezione, sarai in grado di:

- Definire il Pattern di Progettazione per l'Uso di Strumenti e il suo scopo.
- Identificare i casi d'uso in cui il Pattern di Progettazione per l'Uso di Strumenti è applicabile.
- Comprendere gli elementi chiave necessari per implementare il pattern di progettazione.
- Riconoscere le considerazioni per garantire l'affidabilità negli agenti AI che utilizzano questo pattern di progettazione.

## Cos'è il Pattern di Progettazione per l'Uso di Strumenti?

Il **Pattern di Progettazione per l'Uso di Strumenti** si concentra sul fornire ai LLM la capacità di interagire con strumenti esterni per raggiungere obiettivi specifici. Gli strumenti sono codice che può essere eseguito da un agente per svolgere azioni. Uno strumento può essere una funzione semplice come una calcolatrice, o una chiamata API a un servizio di terze parti come la ricerca del prezzo delle azioni o le previsioni meteorologiche. Nel contesto degli agenti AI, gli strumenti sono progettati per essere eseguiti dagli agenti in risposta a **chiamate di funzione generate dal modello**.

## A quali casi d'uso può essere applicato?

Gli agenti AI possono sfruttare gli strumenti per completare compiti complessi, recuperare informazioni o prendere decisioni. Il pattern di progettazione per l'uso di strumenti è spesso utilizzato in scenari che richiedono interazione dinamica con sistemi esterni, come database, servizi web o interpreti di codice. Questa capacità è utile per diversi casi d'uso, tra cui:

- **Recupero Dinamico di Informazioni:** Gli agenti possono interrogare API esterne o database per ottenere dati aggiornati (es. interrogare un database SQLite per analisi dati, recuperare prezzi azionari o informazioni meteo).
- **Esecuzione e Interpretazione di Codice:** Gli agenti possono eseguire codice o script per risolvere problemi matematici, generare report o effettuare simulazioni.
- **Automazione dei Flussi di Lavoro:** Automazione di flussi di lavoro ripetitivi o articolati integrando strumenti come scheduler di attività, servizi email o pipeline di dati.
- **Assistenza Clienti:** Gli agenti possono interagire con sistemi CRM, piattaforme di ticketing o basi di conoscenza per risolvere richieste degli utenti.
- **Generazione e Modifica di Contenuti:** Gli agenti possono sfruttare strumenti come correttori grammaticali, riassuntori di testo o valutatori della sicurezza del contenuto per assistere nelle attività di creazione contenuti.

## Quali sono gli elementi/blocchi costitutivi necessari per implementare il pattern di progettazione per l'uso di strumenti?

Questi blocchi costitutivi permettono all'agente AI di svolgere una vasta gamma di compiti. Vediamo gli elementi chiave necessari per implementare il Pattern di Progettazione per l'Uso di Strumenti:

- **Schemi di Funzione/Strumento**: Definizioni dettagliate degli strumenti disponibili, inclusi nome della funzione, scopo, parametri richiesti e output attesi. Questi schemi permettono al LLM di capire quali strumenti sono disponibili e come costruire richieste valide.

- **Logica di Esecuzione della Funzione**: Regola come e quando gli strumenti vengono invocati in base all'intento dell'utente e al contesto della conversazione. Può includere moduli di pianificazione, meccanismi di instradamento o flussi condizionali che determinano l'uso dinamico degli strumenti.

- **Sistema di Gestione dei Messaggi**: Componenti che gestiscono il flusso conversazionale tra input dell'utente, risposte LLM, chiamate a strumenti e output degli strumenti.

- **Framework di Integrazione degli Strumenti**: Infrastruttura che collega l'agente ai vari strumenti, siano essi semplici funzioni o servizi esterni complessi.

- **Gestione degli Errori e Validazione**: Meccanismi per gestire fallimenti nell'esecuzione degli strumenti, validare i parametri e gestire risposte inaspettate.

- **Gestione dello Stato**: Tiene traccia del contesto della conversazione, delle interazioni precedenti con gli strumenti e dei dati persistenti per garantire coerenza nelle interazioni multi-turno.

Successivamente, esaminiamo più nel dettaglio la Chiamata di Funzione/Strumento.

### Chiamata di Funzione/Strumento

La chiamata di funzione è il modo principale con cui permettiamo ai Large Language Models (LLM) di interagire con gli strumenti. Spesso vedrai “Funzione” e “Strumento” usati in modo intercambiabile perché le “funzioni” (blocchi di codice riutilizzabile) sono gli “strumenti” che gli agenti usano per svolgere i compiti. Affinché il codice di una funzione venga invocato, un LLM deve confrontare la richiesta dell'utente con la descrizione delle funzioni. Per fare questo, uno schema contenente le descrizioni di tutte le funzioni disponibili viene inviato al LLM. Il LLM seleziona quindi la funzione più appropriata per il compito e restituisce il suo nome e gli argomenti. La funzione selezionata viene invocata, la sua risposta viene inviata di nuovo al LLM, che usa queste informazioni per rispondere alla richiesta dell'utente.

Per gli sviluppatori che vogliono implementare la chiamata di funzione per agenti, serve:

1. Un modello LLM che supporti la chiamata di funzione
2. Uno schema contenente le descrizioni delle funzioni
3. Il codice per ciascuna funzione descritta

Usiamo l'esempio del recupero dell'ora corrente in una città per illustrare:

1. **Inizializzare un LLM che supporta la chiamata di funzione:**

    Non tutti i modelli supportano la chiamata di funzione, quindi è importante verificare che il LLM che usi lo faccia. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> supporta la chiamata di funzione. Possiamo iniziare avviando il client di Azure OpenAI.

    ```python
    # Inizializza il client Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Creare uno Schema di Funzione**:

    Successivamente definiremo uno schema JSON che contiene il nome della funzione, la descrizione di cosa fa la funzione e i nomi e le descrizioni dei parametri della funzione.
    Passeremo quindi questo schema al client creato in precedenza, insieme alla richiesta dell'utente per trovare l'ora a San Francisco. È importante notare che ciò che viene restituito è una **chiamata a uno strumento**, **non** la risposta finale alla domanda. Come detto prima, il LLM restituisce il nome della funzione selezionata per il compito e gli argomenti che saranno passati ad essa.

    ```python
    # Descrizione della funzione per il modello da leggere
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # Messaggio iniziale dell'utente
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Prima chiamata API: chiedi al modello di usare la funzione
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Elabora la risposta del modello
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Il codice della funzione necessario per svolgere il compito:**

    Ora che il LLM ha scelto quale funzione deve essere eseguita, il codice che realizza il compito deve essere implementato ed eseguito.
    Possiamo implementare il codice per ottenere l'ora corrente in Python. Serve anche il codice per estrarre il nome e gli argomenti dalla response_message per ottenere il risultato finale.

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # Gestire le chiamate di funzione
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # Seconda chiamata API: Ottieni la risposta finale dal modello
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

La chiamata di funzione è al centro della maggior parte, se non di tutti, i design per l'uso di strumenti negli agenti, tuttavia implementarla da zero può a volte essere complesso.
Come abbiamo imparato in [Lezione 2](../../../02-explore-agentic-frameworks), i framework agentici ci forniscono blocchi pre-costruiti per implementare l'uso di strumenti.

## Esempi di Uso di Strumenti con Framework Agentici

Ecco alcuni esempi di come puoi implementare il Pattern di Progettazione per l'Uso di Strumenti utilizzando diversi framework agentici:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> è un framework AI open-source per sviluppatori .NET, Python e Java che lavorano con Large Language Models (LLM). Semplifica il processo di uso della chiamata di funzione descrivendo automaticamente le tue funzioni e i loro parametri al modello tramite un processo chiamato <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializzazione</a>. Gestisce anche la comunicazione tra il modello e il tuo codice. Un altro vantaggio di usare un framework agentico come Semantic Kernel è che ti permette di accedere a strumenti pre-costruiti come <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> e <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Il seguente diagramma illustra il processo di chiamata di funzione con Semantic Kernel:

![function calling](../../../translated_images/it/functioncalling-diagram.a84006fc287f6014.webp)

In Semantic Kernel le funzioni/strumenti sono chiamati <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugin</a>. Possiamo convertire la funzione `get_current_time` vista prima in un plugin trasformandola in una classe che la contiene. Possiamo anche importare il decoratore `kernel_function`, che riceve la descrizione della funzione. Quando poi si crea un kernel con GetCurrentTimePlugin, il kernel serializzerà automaticamente la funzione e i suoi parametri, creando così lo schema da inviare al LLM.

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# Crea il kernel
kernel = Kernel()

# Crea il plugin
get_current_time_plugin = GetCurrentTimePlugin(location)

# Aggiungi il plugin al kernel
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> è un framework agentico più recente progettato per permettere agli sviluppatori di costruire, distribuire e scalare agenti AI di alta qualità e estensibili in modo sicuro, senza dover gestire direttamente le risorse di calcolo e storage sottostanti. È particolarmente utile per applicazioni enterprise in quanto è un servizio completamente gestito con sicurezza di livello enterprise.

Rispetto allo sviluppo diretto con l'API LLM, Azure AI Agent Service offre alcuni vantaggi, tra cui:

- Chiamata degli strumenti automatica – non serve analizzare la chiamata allo strumento, invocare lo strumento e gestire la risposta; tutto questo ora è eseguito lato server
- Dati gestiti in modo sicuro – invece di gestire lo stato della conversazione da sé, si può fare affidamento sui thread per immagazzinare tutte le informazioni necessarie
- Strumenti pronti all'uso – strumenti per interagire con le tue sorgenti dati, come Bing, Azure AI Search e Azure Functions.

Gli strumenti disponibili in Azure AI Agent Service si dividono in due categorie:

1. Strumenti di Conoscenza:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding con Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Strumenti di Azione:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">Strumenti definiti da OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

L'Agent Service ci permette di utilizzare questi strumenti insieme come un `toolset`. Utilizza anche i `thread` che tengono traccia della cronologia dei messaggi di una determinata conversazione.

Immagina di essere un agente di vendita presso un'azienda chiamata Contoso. Vuoi sviluppare un agente conversazionale che possa rispondere a domande sui dati di vendita.

La seguente immagine illustra come potresti usare Azure AI Agent Service per analizzare i dati delle tue vendite:

![Agentic Service In Action](../../../translated_images/it/agent-service-in-action.34fb465c9a84659e.webp)

Per utilizzare uno di questi strumenti con il servizio possiamo creare un client e definire uno strumento o un toolset. Per implementare praticamente questo possiamo usare il seguente codice Python. Il LLM potrà consultare il toolset e decidere se usare la funzione creata dall'utente, `fetch_sales_data_using_sqlite_query`, o il Code Interpreter pre-costruito, a seconda della richiesta dell'utente.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # funzione fetch_sales_data_using_sqlite_query che si trova in un file fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Inizializza il set di strumenti
toolset = ToolSet()

# Inizializza l'agente di chiamata funzione con la funzione fetch_sales_data_using_sqlite_query e la aggiunge al set di strumenti
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Inizializza lo strumento Code Interpreter e lo aggiunge al set di strumenti.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Quali sono le considerazioni speciali per utilizzare il Pattern di Progettazione per l'Uso di Strumenti per costruire agenti AI affidabili?

Una preoccupazione comune con l'SQL generato dinamicamente dai LLM è la sicurezza, in particolare il rischio di SQL injection o azioni dannose, come la cancellazione o la manomissione del database. Sebbene queste preoccupazioni siano valide, possono essere efficacemente mitigate configurando correttamente i permessi di accesso al database. Per la maggior parte dei database ciò comporta la configurazione del database in sola lettura. Per servizi database come PostgreSQL o Azure SQL, all'app dovrebbe essere assegnato un ruolo di sola lettura (SELECT).

Eseguire l'app in un ambiente sicuro migliora ulteriormente la protezione. Negli scenari enterprise, i dati vengono tipicamente estratti e trasformati da sistemi operativi in un database o data warehouse in sola lettura con uno schema user-friendly. Questo approccio garantisce che i dati siano sicuri, ottimizzati per prestazioni e accessibilità, e che l'app abbia accesso limitato e in sola lettura.

## Codici di esempio
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Hai altre domande sull'uso delle Design Patterns degli Strumenti?

Unisciti al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) per incontrare altri studenti, partecipare alle ore di ufficio e ricevere risposte alle tue domande sugli AI Agents.

## Risorse Aggiuntive

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Workshop sul servizio Azure AI Agents</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Workshop Multi-Agent Contoso Creative Writer</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Tutorial Semantic Kernel Function Calling</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## Lezione Precedente

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## Lezione Successiva

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Avvertenza**:  
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica [Co-op Translator](https://github.com/Azure/co-op-translator). Sebbene ci impegniamo per garantire l’accuratezza, si prega di notare che le traduzioni automatiche possono contenere errori o imprecisioni. Il documento originale nella sua lingua originale deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda una traduzione professionale eseguita da un traduttore umano. Non siamo responsabili per eventuali malintesi o interpretazioni errate derivanti dall’uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->