[![Planning Design Pattern](../../../translated_images/it/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Clicca sull'immagine sopra per vedere il video di questa lezione)_

# Planning Design

## Introduzione

Questa lezione tratterà

* Definire un obiettivo chiaro complessivo e suddividere un compito complesso in compiti gestibili.
* Sfruttare l'output strutturato per risposte più affidabili e leggibili dalle macchine.
* Applicare un approccio guidato dagli eventi per gestire compiti dinamici e input imprevisti.

## Obiettivi di Apprendimento

Dopo aver completato questa lezione, avrai una comprensione di:

* Identificare e impostare un obiettivo complessivo per un agente AI, assicurandosi che sappia chiaramente cosa deve essere raggiunto.
* Decomporre un compito complesso in sotto-compiti gestibili e organizzarli in una sequenza logica.
* Dotare gli agenti degli strumenti giusti (ad es., strumenti di ricerca o strumenti di analisi dati), decidere quando e come vengono utilizzati, e gestire situazioni impreviste che si presentano.
* Valutare i risultati dei sotto-compiti, misurare le prestazioni e iterare sulle azioni per migliorare il risultato finale.

## Definire l'Obiettivo Complessivo e Suddividere un Compito

![Defining Goals and Tasks](../../../translated_images/it/defining-goals-tasks.d70439e19e37c47a.webp)

La maggior parte dei compiti del mondo reale è troppo complessa per essere affrontata in un unico passo. Un agente AI ha bisogno di un obiettivo conciso per guidare la sua pianificazione e azioni. Ad esempio, considera l'obiettivo:

    "Generare un itinerario di viaggio di 3 giorni."

Anche se è semplice da enunciare, necessita ancora di affinamento. Più chiaro è l'obiettivo, meglio l'agente (e qualsiasi collaboratore umano) può concentrarsi sul raggiungimento del risultato corretto, come creare un itinerario completo con opzioni di volo, raccomandazioni di hotel e suggerimenti di attività.

### Decomposizione del Compito

Compiti grandi o complessi diventano più gestibili se suddivisi in sotto-compiti più piccoli e orientati all’obiettivo.
Per l'esempio dell'itinerario di viaggio, potresti decomporre l’obiettivo in:

* Prenotazione Volo
* Prenotazione Hotel
* Noleggio Auto
* Personalizzazione

Ogni sotto-compito può poi essere affrontato da agenti o processi dedicati. Un agente potrebbe specializzarsi nella ricerca delle migliori offerte di volo, un altro si concentra sulle prenotazioni degli hotel, e così via. Un agente di coordinamento o “downstream” può quindi compilare questi risultati in un unico itinerario coerente per l’utente finale.

Questo approccio modulare consente anche miglioramenti incrementali. Per esempio, potresti aggiungere agenti specializzati per Raccomandazioni Alimentari o Suggerimenti su Attività Locali e perfezionare l’itinerario nel tempo.

### Output Strutturato

I Large Language Models (LLMs) possono generare output strutturati (ad es. JSON) che sono più facili da analizzare e processare per agenti o servizi downstream. Questo è particolarmente utile in un contesto multi-agente, dove possiamo agire su questi compiti una volta ricevuto l'output della pianificazione. Consulta questo <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogpost</a> per una rapida panoramica.

Lo snippet Python seguente mostra un semplice agente di pianificazione che scompone un obiettivo in sotto-compiti e genera un piano strutturato:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Modello SubTask di Viaggio
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # vogliamo assegnare il compito all'agente

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Per autenticarti con il modello dovrai generare un token di accesso personale (PAT) nelle impostazioni di GitHub.
    # Crea il tuo token PAT seguendo le istruzioni qui: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definisci il messaggio dell'utente
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Assicurati che il contenuto della risposta sia una stringa JSON valida prima di caricarla
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Il contenuto della risposta non è una stringa JSON valida")

# # Stampa il contenuto della risposta dopo averlo caricato come JSON
# pprint(json.loads(response_content))

# Valida il contenuto della risposta con il modello MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Agente di Pianificazione con Orchestrazione Multi-Agente

In questo esempio, un agente Semantic Router riceve una richiesta dell’utente (ad esempio, "Ho bisogno di un piano hotel per il mio viaggio.").

Il pianificatore quindi:

* Riceve il Piano Hotel: Il pianificatore prende il messaggio dell’utente e, basandosi su un prompt di sistema (inclusi i dettagli degli agenti disponibili), genera un piano di viaggio strutturato.
* Elenca Agenti e Loro Strumenti: Il registro degli agenti contiene una lista di agenti (ad esempio per volo, hotel, noleggio auto e attività) insieme alle funzioni o agli strumenti offerti.
* Instrada il Piano ai Rispettivi Agenti: A seconda del numero di sotto-compiti, il pianificatore invia il messaggio direttamente a un agente dedicato (per scenari a singolo compito) o coordina tramite un gestore di chat di gruppo per la collaborazione multi-agente.
* Riassume il Risultato: Infine, il pianificatore sintetizza il piano generato per chiarezza.
Il codice Python seguente illustra questi passaggi:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Modello SottoCompito di Viaggio

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # vogliamo assegnare il compito all'agente

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Crea il client con variabili d'ambiente verificate tramite tipo

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definisci il messaggio dell'utente

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Assicurati che il contenuto della risposta sia una stringa JSON valida prima di caricarlo

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Stampa il contenuto della risposta dopo averlo caricato come JSON

pprint(json.loads(response_content))
```

Quanto segue è l’output del codice precedente e puoi quindi usare questo output strutturato per instradare verso `assigned_agent` e riassumere il piano di viaggio per l’utente finale.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Un notebook di esempio con il codice precedente è disponibile [qui](07-autogen.ipynb).

### Pianificazione Iterativa

Alcuni compiti richiedono un rimando o una ripianificazione, in cui il risultato di un sotto-compito influenza il successivo. Ad esempio, se l’agente scopre un formato dati inatteso durante la prenotazione di voli, potrebbe dover adattare la sua strategia prima di passare alla prenotazione dell’hotel.

Inoltre, il feedback dell’utente (ad esempio un umano che decide di preferire un volo anticipato) può innescare una ripianificazione parziale. Questo approccio dinamico e iterativo assicura che la soluzione finale sia in linea con vincoli reali e preferenze utente in evoluzione.

e.g codice di esempio

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. uguale al codice precedente e passa la cronologia dell'utente, piano attuale
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. ripianifica e invia i compiti agli agenti rispettivi
```

Per una pianificazione più completa, dai un’occhiata a Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogpost</a> per risolvere compiti complessi.

## Riepilogo

In questo articolo abbiamo visto un esempio di come possiamo creare un pianificatore che possa selezionare dinamicamente gli agenti disponibili definiti. L’output del Pianificatore scompone i compiti e assegna gli agenti così che possano essere eseguiti. Si presume che gli agenti abbiano accesso alle funzioni/strumenti richiesti per svolgere il compito. Oltre agli agenti puoi includere altri pattern come reflection, summarizer e round robin chat per personalizzare ulteriormente.

## Risorse Aggiuntive

AutoGen Magentic One - Un sistema multi-agente generalista per risolvere compiti complessi che ha ottenuto risultati impressionanti su molteplici benchmark agentici sfidanti. Riferimento: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. In questa implementazione l’orchestratore crea un piano specifico per il compito e delega questi compiti agli agenti disponibili. Oltre alla pianificazione, l’orchestratore impiega anche un meccanismo di tracciamento per monitorare il progresso del compito e ripianificare se necessario.

### Hai altre domande sul Pattern di Planning Design?

Unisciti al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) per incontrare altri studenti, partecipare a sessioni di office hours e ottenere risposte alle tue domande sugli AI Agents.

## Lezione Precedente

[Building Trustworthy AI Agents](../06-building-trustworthy-agents/README.md)

## Lezione Successiva

[Multi-Agent Design Pattern](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica [Co-op Translator](https://github.com/Azure/co-op-translator). Pur impegnandoci per garantire accuratezza, si prega di considerare che le traduzioni automatiche possono contenere errori o inesattezze. Il documento originale nella sua lingua natìa deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda una traduzione professionale umana. Non siamo responsabili per eventuali fraintendimenti o interpretazioni errate derivanti dall’uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->