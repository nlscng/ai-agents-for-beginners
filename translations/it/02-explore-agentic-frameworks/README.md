[![Esplorare i framework per agenti AI](../../../translated_images/it/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Fai clic sull'immagine sopra per guardare il video di questa lezione)_

# Esplora i framework per agenti AI

I framework per agenti AI sono piattaforme software progettate per semplificare la creazione, il deploy e la gestione di agenti AI. Questi framework forniscono agli sviluppatori componenti predefiniti, astrazioni e strumenti che snelliscono lo sviluppo di sistemi AI complessi.

Questi framework aiutano gli sviluppatori a concentrarsi sugli aspetti unici delle loro applicazioni fornendo approcci standardizzati alle sfide comuni nello sviluppo di agenti AI. Migliorano la scalabilità, l'accessibilità e l'efficienza nella costruzione di sistemi AI.

## Introduzione 

Questa lezione tratterà:

- Cosa sono i framework per agenti AI e cosa permettono agli sviluppatori di realizzare?
- Come possono i team usare questi framework per prototipare rapidamente, iterare e migliorare le capacità del loro agente?
- Quali sono le differenze tra i framework e gli strumenti creati da Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, e <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Posso integrare direttamente i miei strumenti dell'ecosistema Azure esistenti, o ho bisogno di soluzioni standalone?
- Cos'è il servizio Azure AI Agents e come mi aiuta?

## Obiettivi di apprendimento

Gli obiettivi di questa lezione sono aiutarti a comprendere:

- Il ruolo dei framework per agenti AI nello sviluppo AI.
- Come sfruttare i framework per agenti AI per costruire agenti intelligenti.
- Le capacità chiave abilitate dai framework per agenti AI.
- Le differenze tra AutoGen, Semantic Kernel e Azure AI Agent Service.

## Cosa sono i framework per agenti AI e cosa permettono agli sviluppatori di fare?

I framework AI tradizionali possono aiutarti a integrare l'AI nelle tue app e rendere queste app migliori nei seguenti modi:

- **Personalizzazione**: l'AI può analizzare il comportamento e le preferenze degli utenti per fornire raccomandazioni, contenuti ed esperienze personalizzate.
Esempio: servizi di streaming come Netflix usano l'AI per suggerire film e serie in base alla cronologia di visione, aumentando l'engagement e la soddisfazione degli utenti.
- **Automazione ed efficienza**: l'AI può automatizzare compiti ripetitivi, snellire i flussi di lavoro e migliorare l'efficienza operativa.
Esempio: le app di assistenza clienti utilizzano chatbot alimentati da AI per gestire richieste comuni, riducendo i tempi di risposta e liberando gli operatori umani per questioni più complesse.
- **Esperienza utente migliorata**: l'AI può migliorare l'esperienza utente complessiva fornendo funzionalità intelligenti come riconoscimento vocale, elaborazione del linguaggio naturale e testo predittivo.
Esempio: assistenti virtuali come Siri e Google Assistant utilizzano l'AI per comprendere e rispondere ai comandi vocali, facilitando l'interazione degli utenti con i loro dispositivi.

### Tutto ciò suona fantastico, quindi perché abbiamo bisogno di un framework per agenti AI?

I framework per agenti AI rappresentano qualcosa di più rispetto ai semplici framework AI. Sono progettati per consentire la creazione di agenti intelligenti che possono interagire con gli utenti, con altri agenti e con l'ambiente per raggiungere obiettivi specifici. Questi agenti possono esibire comportamenti autonomi, prendere decisioni e adattarsi a condizioni in cambiamento. Vediamo alcune capacità chiave abilitate dai framework per agenti AI:

- **Collaborazione e coordinamento tra agenti**: consentono la creazione di più agenti AI che possono lavorare insieme, comunicare e coordinarsi per risolvere compiti complessi.
- **Automazione e gestione dei compiti**: forniscono meccanismi per automatizzare flussi di lavoro multi-step, delega dei compiti e gestione dinamica dei task tra gli agenti.
- **Comprensione contestuale e adattamento**: dotano gli agenti della capacità di comprendere il contesto, adattarsi a ambienti in cambiamento e prendere decisioni basate su informazioni in tempo reale.

In sintesi, gli agenti ti permettono di fare di più, portare l'automazione al livello successivo e creare sistemi più intelligenti che possono adattarsi e apprendere dal loro ambiente.

## Come prototipare rapidamente, iterare e migliorare le capacità dell'agente?

Questo è un settore in rapida evoluzione, ma ci sono alcuni elementi comuni alla maggior parte dei framework per agenti AI che possono aiutarti a prototipare e iterare rapidamente, in particolare componenti modulari, strumenti collaborativi e apprendimento in tempo reale. Approfondiamo questi aspetti:

- **Usa componenti modulari**: gli SDK AI offrono componenti predefiniti come connettori AI e di memoria, function calling usando linguaggio naturale o plugin di codice, template di prompt e altro.
- **Sfrutta strumenti collaborativi**: progetta agenti con ruoli e compiti specifici, permettendo loro di testare e perfezionare i flussi di lavoro collaborativi.
- **Apprendi in tempo reale**: implementa loop di feedback in cui gli agenti apprendono dalle interazioni e adattano il loro comportamento dinamicamente.

### Usa componenti modulari

SDK come Microsoft Semantic Kernel e LangChain offrono componenti predefiniti come connettori AI, template di prompt e gestione della memoria.

**Come i team possono usare questi componenti**: i team possono assemblare rapidamente questi componenti per creare un prototipo funzionale senza partire da zero, permettendo sperimentazione e iterazione rapida.

**Come funziona in pratica**: puoi usare un parser predefinito per estrarre informazioni dall'input dell'utente, un modulo di memoria per memorizzare e recuperare dati, e un generatore di prompt per interagire con gli utenti, tutto senza dover costruire questi componenti da zero.

**Codice di esempio**. Vediamo degli esempi di come puoi usare un AI Connector predefinito con Semantic Kernel Python e .Net che utilizza chiamate automatiche a funzioni per far sì che il modello risponda all'input dell'utente:

``` python
# Esempio di Semantic Kernel in Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definire un oggetto ChatHistory per contenere il contesto della conversazione
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definire un plugin di esempio che contiene la funzione per prenotare un viaggio
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Creare il Kernel
kernel = Kernel()

# Aggiungere il plugin di esempio all'oggetto Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definire il connettore AI di Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definire le impostazioni della richiesta per configurare il modello con chiamata automatica di funzione
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Effettuare la richiesta al modello per la cronologia chat e le impostazioni di richiesta date
    # Il Kernel contiene l'esempio che il modello richiederà di invocare
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # Risposta di esempio del modello AI: `Il tuo volo per New York il 1° gennaio 2025 è stato prenotato con successo. Buon viaggio! ✈️🗽`

    # Aggiungere la risposta del modello al nostro contesto della cronologia chat
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```

Quello che si può vedere da questo esempio è come puoi sfruttare un parser predefinito per estrarre informazioni chiave dall'input dell'utente, come origine, destinazione e data di una richiesta di prenotazione di un volo. Questo approccio modulare ti permette di concentrarti sulla logica ad alto livello.

### Sfrutta strumenti collaborativi

Framework come CrewAI, Microsoft AutoGen e Semantic Kernel facilitano la creazione di più agenti che possono lavorare insieme.

**Come i team possono usare questi strumenti**: i team possono progettare agenti con ruoli e compiti specifici, permettendo loro di testare e perfezionare flussi di lavoro collaborativi e migliorare l'efficienza complessiva del sistema.

**Come funziona in pratica**: puoi creare un team di agenti in cui ogni agente ha una funzione specializzata, come recupero dati, analisi o presa di decisioni. Questi agenti possono comunicare e condividere informazioni per raggiungere un obiettivo comune, come rispondere a una richiesta dell'utente o completare un compito.

**Esempio di codice (AutoGen)**:

```python
# creazione degli agenti, poi crea un programma round robin dove possono lavorare insieme, in questo caso in ordine

# Agente di Recupero Dati
# Agente di Analisi Dati
# Agente di Presa di Decisioni

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# la conversazione termina quando l'utente dice "APPROVA"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Usa asyncio.run(...) quando si esegue in uno script.
await Console(stream)
```

Quello che vedi nel codice precedente è come puoi creare un task che coinvolge più agenti che lavorano insieme per analizzare i dati. Ogni agente svolge una funzione specifica e il task viene eseguito coordinando gli agenti per ottenere il risultato desiderato. Creando agenti dedicati con ruoli specializzati, puoi migliorare l'efficienza e le prestazioni del task.

### Apprendere in tempo reale

I framework avanzati forniscono funzionalità per la comprensione contestuale e l'adattamento in tempo reale.

**Come i team possono usare queste funzionalità**: i team possono implementare loop di feedback in cui gli agenti apprendono dalle interazioni e adeguano il loro comportamento dinamicamente, portando a miglioramenti continui e al perfezionamento delle capacità.

**Come funziona in pratica**: gli agenti possono analizzare il feedback degli utenti, i dati ambientali e i risultati dei task per aggiornare la loro base di conoscenza, adattare gli algoritmi di decisione e migliorare le prestazioni nel tempo. Questo processo di apprendimento iterativo permette agli agenti di adattarsi a condizioni e preferenze utente in evoluzione, migliorando l'efficacia complessiva del sistema.

## Quali sono le differenze tra i framework AutoGen, Semantic Kernel e Azure AI Agent Service?

Ci sono molti modi per confrontare questi framework, ma vediamo alcune differenze chiave in termini di design, capacità e casi d'uso target:

## AutoGen

AutoGen è un framework open-source sviluppato dal Microsoft Research AI Frontiers Lab. Si concentra su applicazioni *agentiche* distribuite e guidate da eventi, abilitando più LLM e SLM, strumenti e pattern avanzati di progettazione multi-agente.

AutoGen è costruito attorno al concetto centrale di agenti, che sono entità autonome in grado di percepire il loro ambiente, prendere decisioni e intraprendere azioni per raggiungere obiettivi specifici. Gli agenti comunicano tramite messaggi asincroni, permettendo loro di lavorare in modo indipendente e in parallelo, migliorando la scalabilità e la reattività del sistema.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Gli agenti si basano sul modello degli attori</a>. Secondo Wikipedia, un attore è _l'unità di base della computazione concorrente. In risposta a un messaggio che riceve, un attore può: prendere decisioni locali, creare altri attori, inviare altri messaggi e determinare come rispondere al prossimo messaggio ricevuto_.

**Casi d'uso**: automatizzazione della generazione di codice, task di analisi dei dati e costruzione di agenti personalizzati per funzioni di pianificazione e ricerca.

Ecco alcuni concetti core importanti di AutoGen:

- **Agenti**. Un agente è un'entità software che:
  - **Comunica tramite messaggi**, questi messaggi possono essere sincroni o asincroni.
  - **Mantiene il proprio stato**, che può essere modificato dai messaggi in arrivo.
  - **Esegue azioni** in risposta a messaggi ricevuti o cambiamenti del suo stato. Queste azioni possono modificare lo stato dell'agente e produrre effetti esterni, come aggiornare log dei messaggi, inviare nuovi messaggi, eseguire codice o effettuare chiamate API.
    
  Qui hai un breve snippet di codice in cui crei il tuo agente con capacità di Chat:

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
    
    Nel codice precedente, `MyAgent` è stato creato ed eredita da `RoutedAgent`. Ha un handler dei messaggi che stampa il contenuto del messaggio e poi invia una risposta usando il delegato `AssistantAgent`. Nota in particolare come assegniamo a `self._delegate` un'istanza di `AssistantAgent`, che è un agente predefinito in grado di gestire le chat completions.


    Diamo ora ad AutoGen informazioni su questo tipo di agente e avviamo il programma:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Avvia l'elaborazione dei messaggi in background.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Nel codice precedente gli agenti sono registrati con il runtime e poi viene inviato un messaggio all'agente, risultando nell'output seguente:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multi agenti**. AutoGen supporta la creazione di più agenti che possono lavorare insieme per raggiungere compiti complessi. Gli agenti possono comunicare, condividere informazioni e coordinare le loro azioni per risolvere problemi in modo più efficiente. Per creare un sistema multi-agente, puoi definire diversi tipi di agenti con funzioni e ruoli specializzati, come recupero dati, analisi, presa di decisioni e interazione con l'utente. Vediamo come appare una tale creazione per farti un'idea:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Esempio di dichiarazione di un Agente
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Utilizzo del tipo topic come tipo di agente.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # dichiarazioni rimanenti abbreviate per brevità

    # Chat di gruppo
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```

    Nel codice precedente abbiamo un `GroupChatManager` che è registrato con il runtime. Questo manager è responsabile del coordinamento delle interazioni tra diversi tipi di agenti, come scrittori, illustratori, editor e utenti.

- **Agent Runtime**. Il framework fornisce un ambiente runtime, permettendo la comunicazione tra agenti, gestisce le loro identità e i loro cicli di vita, e applica confini di sicurezza e privacy. Questo significa che puoi eseguire i tuoi agenti in un ambiente sicuro e controllato, assicurando che possano interagire in modo efficiente e protetto. Ci sono due runtime di interesse:
  - **Runtime stand-alone**. Questa è una buona scelta per applicazioni single-process in cui tutti gli agenti sono implementati nello stesso linguaggio di programmazione e vengono eseguiti nello stesso processo. Ecco un'illustrazione di come funziona:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Runtime stand-alone</a>   
Stack dell'applicazione

    *gli agenti comunicano tramite messaggi attraverso il runtime, e il runtime gestisce il ciclo di vita degli agenti*

  - **Runtime distribuito**, è adatto per applicazioni multi-processo in cui gli agenti possono essere implementati in diversi linguaggi di programmazione e in esecuzione su macchine diverse. Ecco un'illustrazione di come funziona:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Runtime distribuito</a>

## Semantic Kernel + Agent Framework

Semantic Kernel è un SDK di orchestrazione AI pronto per l'impiego in ambito enterprise. Consiste di connettori AI e di memoria, insieme a un Agent Framework.

Copriamo prima alcuni componenti core:

- **AI Connectors**: questa è un'interfaccia con servizi AI esterni e sorgenti di dati per l'uso sia in Python che in C#.

  ```python
  # Semantic Kernel Python
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  

    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```

    Qui hai un semplice esempio di come puoi creare un kernel e aggiungere un servizio di chat completion. Semantic Kernel crea una connessione a un servizio AI esterno, in questo caso Azure OpenAI Chat Completion.

- **Plugin**: questi incapsulano funzioni che un'applicazione può usare. Ci sono sia plugin pronti all'uso che plugin personalizzati che puoi creare. Un concetto correlato è quello di "prompt functions". Invece di fornire suggerimenti in linguaggio naturale per l'invocazione di una funzione, pubblichi certe funzioni al modello. In base al contesto della chat corrente, il modello può scegliere di chiamare una di queste funzioni per completare una richiesta o una query. Ecco un esempio:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```

    Qui, prima hai un prompt template `skPrompt` che lascia spazio all'utente per inserire il testo, `$userInput`. Poi crei la funzione del kernel `SummarizeText` e la importi nel kernel con il nome del plugin `SemanticFunctions`. Nota il nome della funzione che aiuta Semantic Kernel a capire cosa fa la funzione e quando dovrebbe essere chiamata.

- **Funzione nativa**: ci sono anche funzioni native che il framework può chiamare direttamente per svolgere il compito. Ecco un esempio di una tale funzione che recupera il contenuto da un file:

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```

- **Memoria**: astrattezza e semplificazione della gestione del contesto per le app AI. L'idea con la memoria è che si tratta di informazioni che l'LLM dovrebbe conoscere. Puoi memorizzare queste informazioni in un vector store che finisce per essere un database in memoria o un database vettoriale o simili. Ecco un esempio di uno scenario molto semplificato in cui *fatti* vengono aggiunti alla memoria:

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```

    Questi fatti vengono poi memorizzati nella raccolta di memoria `SummarizedAzureDocs`. Questo è un esempio molto semplificato, ma puoi vedere come è possibile memorizzare informazioni nella memoria affinché l'LLM le utilizzi.

Quindi queste sono le basi del framework Semantic Kernel, e per quanto riguarda l'Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service è un'aggiunta più recente, introdotta a Microsoft Ignite 2024. Consente lo sviluppo e il deployment di agenti AI con modelli più flessibili, come la chiamata diretta di LLM open-source come Llama 3, Mistral e Cohere.

Azure AI Agent Service fornisce meccanismi di sicurezza aziendale più robusti e metodi di archiviazione dei dati, rendendolo adatto per applicazioni enterprise. 

Funziona immediatamente con framework di orchestrazione multi-agente come AutoGen e Semantic Kernel.

Questo servizio è attualmente in Anteprima Pubblica e supporta Python e C# per la creazione di agenti.

Usando Semantic Kernel Python, possiamo creare un Azure AI Agent con un plugin definito dall'utente:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definisci un plugin di esempio per il campione
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # Crea la definizione dell'agente
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Crea l'agente AzureAI utilizzando il client definito e la definizione dell'agente
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Crea un thread per contenere la conversazione
        # Se non viene fornito alcun thread, ne verrà creato uno nuovo
        # creato e restituito con la risposta iniziale
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # Invoca l'agente per il thread specificato
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### Concetti principali

Azure AI Agent Service ha i seguenti concetti principali:

- **Agente**. Azure AI Agent Service si integra con Microsoft Foundry. All'interno di AI Foundry, un Agente AI agisce come un microservizio "intelligente" che può essere utilizzato per rispondere a domande (RAG), eseguire azioni o automatizzare completamente workflow. Ciò si ottiene combinando la potenza dei modelli generativi con strumenti che gli consentono di accedere e interagire con fonti di dati reali. Ecco un esempio di agente:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    In questo esempio, un agente viene creato con il modello `gpt-4o-mini`, un nome `my-agent` e le istruzioni `You are helpful agent`. L'agente è dotato di strumenti e risorse per eseguire attività di interpretazione del codice.

- **Thread e messaggi**. Il thread è un altro concetto importante. Rappresenta una conversazione o un'interazione tra un agente e un utente. I thread possono essere utilizzati per tracciare l'andamento di una conversazione, memorizzare informazioni di contesto e gestire lo stato dell'interazione. Ecco un esempio di thread:

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    Nel codice precedente viene creato un thread. Successivamente, viene inviato un messaggio al thread. Chiamando `create_and_process_run`, si chiede all'agente di lavorare sul thread. Infine, i messaggi vengono recuperati e registrati per vedere la risposta dell'agente. I messaggi indicano l'avanzamento della conversazione tra l'utente e l'agente. È anche importante capire che i messaggi possono essere di tipi diversi come testo, immagine o file, ossia il lavoro dell'agente ha prodotto ad esempio un'immagine o una risposta testuale. Come sviluppatore, puoi poi usare queste informazioni per elaborare ulteriormente la risposta o presentarla all'utente.

- **Si integra con altri framework AI**. Azure AI Agent Service può interagire con altri framework come AutoGen e Semantic Kernel, il che significa che puoi costruire parte della tua app in uno di questi framework e, ad esempio, usare il servizio Agent come orchestratore oppure puoi costruire tutto nel servizio Agent.

**Casi d'uso**: Azure AI Agent Service è progettato per applicazioni enterprise che richiedono deployment di agenti AI sicuri, scalabili e flessibili.

## What's the difference between these frameworks?
 
Sembra che ci sia molta sovrapposizione tra questi framework, ma ci sono alcune differenze chiave in termini di design, capacità e casi d'uso target:
 
- **AutoGen**: È un framework di sperimentazione focalizzato sulla ricerca all'avanguardia sui sistemi multi-agente. È il posto migliore per sperimentare e prototipare sistemi multi-agente sofisticati.
- **Semantic Kernel**: È una libreria pronta per la produzione per costruire applicazioni agentiche enterprise. Si concentra su applicazioni agentiche event-driven e distribuite, abilitando più LLM e SLM, strumenti e pattern di design single/multi-agent.
- **Azure AI Agent Service**: È una piattaforma e un servizio di deployment in Azure Foundry per agenti. Offre connettività ai servizi supportati da Azure Foundry come Azure OpenAI, Azure AI Search, Bing Search ed esecuzione di codice.
 
Ancora indeciso su quale scegliere?

### Casi d'uso
 
Vediamo se possiamo aiutarti esaminando alcuni casi d'uso comuni:
 
> Q: I'm experimenting, learning and building proof-of-concept agent applications, and I want to be able to build and experiment quickly
>

>A: AutoGen would be a good choice for this scenario, as it focuses on event-driven, distributed agentic applications and supports advanced multi-agent design patterns.

> Q: What makes AutoGen a better choice than Semantic Kernel and Azure AI Agent Service for this use case?
>
> A: AutoGen is specifically designed for event-driven, distributed agentic applications, making it well-suited for automating code generation and data analysis tasks. It provides the necessary tools and capabilities to build complex multi-agent systems efficiently.

>Q: Sounds like Azure AI Agent Service could work here too, it has tools for code generation and more?

>
> A: Yes, Azure AI Agent Service is a platform service for agents and add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. It makes it easy to build your agents in the Foundry Portal and deploy them at scale.
 
> Q: I'm still confused just give me one option
>
> A: A great choice is to build your application in Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. This approach allows you to easily persist your agents while leveraging the power to build multi-agent systems in Semantic Kernel. Additionally, Semantic Kernel has a connector in AutoGen, making it easy to use both frameworks together.
 
Riassumiamo le differenze chiave in una tabella:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Applicazioni agentiche event-driven e distribuite | Agenti, Persone, Funzioni, Dati | Generazione di codice, attività di analisi dei dati |
| Semantic Kernel | Comprensione e generazione di contenuti testuali in linguaggio naturale | Agenti, Componenti modulari, Collaborazione | Comprensione del linguaggio naturale, generazione di contenuti |
| Azure AI Agent Service | Modelli flessibili, sicurezza aziendale, generazione di codice, chiamata di strumenti | Modularità, Collaborazione, Orchestrazione dei processi | Deployment di agenti AI sicuri, scalabili e flessibili |

Qual è il caso d'uso ideale per ciascuno di questi framework?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

La risposta è sì, puoi integrare direttamente i tuoi strumenti dell'ecosistema Azure con Azure AI Agent Service in particolare, questo perché è stato costruito per funzionare senza soluzione di continuità con altri servizi Azure. Potresti ad esempio integrare Bing, Azure AI Search e Azure Functions. C'è anche una profonda integrazione con Microsoft Foundry.

Per AutoGen e Semantic Kernel, puoi anche integrarti con i servizi Azure, ma potrebbe essere necessario chiamare i servizi Azure dal tuo codice. Un altro modo per integrare è utilizzare gli SDK di Azure per interagire con i servizi Azure dai tuoi agenti. Inoltre, come menzionato, puoi usare Azure AI Agent Service come orchestratore per i tuoi agenti costruiti in AutoGen o Semantic Kernel, il che darebbe un accesso semplice all'ecosistema Azure.

## Sample Codes

- Python: [Framework agenti](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Framework agenti](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Unisciti al [Discord di Microsoft Foundry](https://aka.ms/ai-agents/discord) per incontrare altri studenti, partecipare alle office hours e ottenere risposte alle tue domande sugli agenti AI.

## References

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Servizio Azure Agent</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel e AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Servizio Azure AI Agent</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Utilizzare Azure AI Agent Service con AutoGen / Semantic Kernel per costruire una soluzione multi-agente</a>

## Previous Lesson

[Introduzione agli agenti AI e ai casi d'uso degli agenti](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Comprendere i pattern di design agentico](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Dichiarazione di non responsabilità**:
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica basato sull'intelligenza artificiale [Co-op Translator](https://github.com/Azure/co-op-translator). Sebbene ci impegniamo a garantire l'accuratezza, si prega di tenere presente che le traduzioni automatiche possono contenere errori o imprecisioni. Il documento originale nella lingua di origine dovrebbe essere considerato la versione autorevole. Per informazioni critiche, si raccomanda una traduzione professionale effettuata da un traduttore umano. Non ci assumiamo alcuna responsabilità per eventuali incomprensioni o interpretazioni errate derivanti dall'uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->