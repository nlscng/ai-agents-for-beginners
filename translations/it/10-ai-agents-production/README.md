# Agenti AI in Produzione: Osservabilità e Valutazione

[![Agenti AI in Produzione](../../../translated_images/it/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

Man mano che gli agenti AI si spostano da prototipi sperimentali ad applicazioni nel mondo reale, diventa importante la capacità di comprendere il loro comportamento, monitorarne le prestazioni e valutare sistematicamente i loro output.

## Obiettivi di Apprendimento

Dopo aver completato questa lezione, saprai/avrai compreso:
- Concetti fondamentali di osservabilità e valutazione degli agenti
- Tecniche per migliorare le prestazioni, i costi e l'efficacia degli agenti
- Cosa e come valutare sistematicamente i tuoi agenti AI
- Come controllare i costi quando distribuisci agenti AI in produzione
- Come strumentare agenti costruiti con AutoGen

L'obiettivo è dotarti delle conoscenze per trasformare i tuoi agenti "scatola nera" in sistemi trasparenti, gestibili e affidabili.

_**Nota:** È importante distribuire Agenti AI che siano sicuri e affidabili. Consulta anche la lezione [Costruire Agenti AI Affidabili](./06-building-trustworthy-agents/README.md)._

## Tracce e Span

Gli strumenti di osservabilità come [Langfuse](https://langfuse.com/) o [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) solitamente rappresentano le esecuzioni degli agenti come tracce e span.

- **Traccia** rappresenta un'attività completa dell'agente dall'inizio alla fine (come gestire una richiesta utente).
- **Span** sono passaggi individuali all'interno della traccia (come chiamare un modello linguistico o recuperare dati).

![Albero delle tracce in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Senza osservabilità, un agente AI può sembrare una "scatola nera" - il suo stato interno e il suo ragionamento sono opachi, rendendo difficile diagnosticare problemi o ottimizzare le prestazioni. Con l'osservabilità, gli agenti diventano "scatole di vetro", offrendo trasparenza vitale per costruire fiducia e assicurare che operino come previsto. 

## Perché l'Osservabilità Conta negli Ambienti di Produzione

La transizione degli agenti AI verso ambienti di produzione introduce una nuova serie di sfide e requisiti. L'osservabilità non è più un "bel-to-have" ma una capacità critica:

*   **Debugging e Analisi delle Cause Radice**: Quando un agente fallisce o produce un output inatteso, gli strumenti di osservabilità forniscono le tracce necessarie per individuare la fonte dell'errore. Questo è particolarmente importante in agenti complessi che possono coinvolgere molte chiamate LLM, interazioni con strumenti e logica condizionale.
*   **Gestione della Latency e dei Costi**: Gli agenti AI spesso si affidano a LLM e altre API esterne che sono fatturate per token o per chiamata. L'osservabilità permette un tracciamento preciso di queste chiamate, aiutando a identificare operazioni eccessivamente lente o costose. Questo consente ai team di ottimizzare i prompt, selezionare modelli più efficienti o riprogettare i flussi di lavoro per gestire i costi operativi e garantire una buona esperienza utente.
*   **Fiducia, Sicurezza e Conformità**: In molte applicazioni è importante garantire che gli agenti si comportino in modo sicuro ed etico. L'osservabilità fornisce una traccia di audit delle azioni e delle decisioni dell'agente. Questo può essere usato per rilevare e mitigare problemi come prompt injection, la generazione di contenuti dannosi o la gestione scorretta di informazioni personali identificabili (PII). Ad esempio, puoi esaminare le tracce per capire perché un agente ha fornito una certa risposta o ha utilizzato uno strumento specifico.
*   **Cicli di Miglioramento Continuo**: I dati di osservabilità sono la base di un processo di sviluppo iterativo. Monitorando come gli agenti performano nel mondo reale, i team possono identificare aree di miglioramento, raccogliere dati per il fine-tuning dei modelli e validare l'impatto delle modifiche. Questo crea un ciclo di feedback in cui gli insight di produzione derivanti dalla valutazione online informano la sperimentazione offline e il perfezionamento, portando a prestazioni dell'agente progressivamente migliori.

## Metriche Chiave da Monitorare

Per monitorare e comprendere il comportamento degli agenti, è opportuno tracciare una serie di metriche e segnali. Sebbene le metriche specifiche possano variare in base allo scopo dell'agente, alcune sono universalmente importanti.

Ecco alcune delle metriche più comuni che gli strumenti di osservabilità monitorano:

**Latency:** Quanto velocemente risponde l'agente? Tempi di attesa lunghi impattano negativamente l'esperienza utente. Dovresti misurare la latency per attività e passaggi individuali tracciando le esecuzioni dell'agente. Ad esempio, un agente che impiega 20 secondi per tutte le chiamate al modello potrebbe essere accelerato usando un modello più veloce o eseguendo le chiamate al modello in parallelo.

**Costi:** Qual è la spesa per esecuzione dell'agente? Gli agenti AI si affidano a chiamate LLM fatturate per token o ad API esterne. L'uso frequente di strumenti o molteplici prompt può aumentare rapidamente i costi. Per esempio, se un agente chiama un LLM cinque volte per un miglioramento marginale della qualità, devi valutare se il costo è giustificato o se puoi ridurre il numero di chiamate o usare un modello più economico. Il monitoraggio in tempo reale può anche aiutare a identificare picchi inaspettati (ad es. bug che causano loop eccessivi di API).

**Errori di Richiesta:** Quante richieste ha fallito l'agente? Questo può includere errori API o chiamate a strumenti non riuscite. Per rendere il tuo agente più robusto in produzione, puoi quindi impostare fallback o retry. Esempio: se il provider LLM A è down, passi al provider LLM B come backup.

**Feedback degli Utenti:** Implementare valutazioni dirette degli utenti fornisce preziose informazioni. Questo può includere valutazioni esplicite (👍pollice-su/👎pollice-giù, ⭐1-5 stelle) o commenti testuali. Feedback negativo costante dovrebbe allertarti in quanto è un segno che l'agente non sta funzionando come previsto. 

**Feedback Utente Implicito:** I comportamenti degli utenti forniscono feedback indiretto anche senza valutazioni esplicite. Questo può includere riformulazioni immediate della domanda, richieste ripetute o il clic su un pulsante di retry. Esempio: se vedi che gli utenti chiedono ripetutamente la stessa domanda, è un segno che l'agente non sta funzionando come previsto.

**Accuratezza:** Quanto frequentemente l'agente produce output corretti o desiderabili? Le definizioni di accuratezza variano (ad es. correttezza nella risoluzione di problemi, accuratezza nel recupero di informazioni, soddisfazione dell'utente). Il primo passo è definire cosa significa successo per il tuo agente. Puoi monitorare l'accuratezza tramite controlli automatizzati, punteggi di valutazione o etichette di completamento attività. Ad esempio, contrassegnare le tracce come "riuscite" o "non riuscite". 

**Metriche di Valutazione Automatizzata:** Puoi anche impostare valutazioni automatiche. Per esempio, puoi usare un LLM per valutare l'output dell'agente, ad es. se è utile, accurato o meno. Esistono anche diverse librerie open source che aiutano a valutare diversi aspetti dell'agente. Ad esempio [RAGAS](https://docs.ragas.io/) per agenti RAG o [LLM Guard](https://llm-guard.com/) per rilevare linguaggio dannoso o prompt injection. 

Nella pratica, una combinazione di queste metriche fornisce la miglior copertura dello stato di salute di un agente AI. In questo capitolo, nel [notebook di esempio](./code_samples/10_autogen_evaluation.ipynb), ti mostreremo come queste metriche appaiono in esempi reali ma prima, impareremo come appare tipicamente un flusso di valutazione.

## Strumenta il tuo Agente

Per raccogliere i dati di tracing, dovrai strumentare il tuo codice. L'obiettivo è strumentare il codice dell'agente per emettere tracce e metriche che possano essere catturate, processate e visualizzate da una piattaforma di osservabilità.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) è emerso come standard industriale per l'osservabilità degli LLM. Fornisce un set di API, SDK e strumenti per generare, raccogliere ed esportare dati di telemetria. 

Esistono molte librerie di strumentazione che avvolgono i framework di agenti esistenti e facilitano l'esportazione degli span OpenTelemetry verso uno strumento di osservabilità. Di seguito un esempio su come strumentare un agente AutoGen con la libreria di strumentazione [OpenLit](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

Il [notebook di esempio](./code_samples/10_autogen_evaluation.ipynb) in questo capitolo dimostrerà come strumentare il tuo agente AutoGen.

**Creazione Manuale di Span:** Sebbene le librerie di strumentazione forniscano una buona base, ci sono spesso casi in cui sono necessarie informazioni più dettagliate o personalizzate. Puoi creare manualmente span per aggiungere logica applicativa personalizzata. Più importante, puoi arricchire gli span creati automaticamente o manualmente con attributi personalizzati (noti anche come tag o metadata). Questi attributi possono includere dati specifici di business, calcoli intermedi o qualsiasi contesto che possa essere utile per il debug o l'analisi, come `user_id`, `session_id` o `model_version`.

Esempio su come creare tracce e span manualmente con il [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3): 

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Valutazione dell'Agente

L'osservabilità ci fornisce metriche, ma la valutazione è il processo di analisi di quei dati (e di esecuzione di test) per determinare quanto bene un agente AI stia performando e come possa essere migliorato. In altre parole, una volta che hai quelle tracce e metriche, come le usi per giudicare l'agente e prendere decisioni?

La valutazione regolare è importante perché gli agenti AI sono spesso non deterministici e possono evolvere (tramite aggiornamenti o deriva del comportamento del modello) – senza valutazione, non sapresti se il tuo "agente intelligente" sta effettivamente svolgendo bene il suo lavoro o se ha subito regressioni.

Esistono due categorie di valutazioni per gli agenti AI: **valutazione online** e **valutazione offline**. Entrambe sono preziose e si completano a vicenda. Di solito si comincia con la valutazione offline, in quanto è il passaggio minimo necessario prima di distribuire qualsiasi agente.

### Valutazione Offline

![Elementi del dataset in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

Questo comporta la valutazione dell'agente in un ambiente controllato, tipicamente utilizzando dataset di test, non query utente live. Si usano dataset curati dove si conosce qual è l'output atteso o il comportamento corretto, e poi si esegue l'agente su quelli. 

Ad esempio, se hai costruito un agente per problemi matematici, potresti avere un [dataset di test](https://huggingface.co/datasets/gsm8k) di 100 problemi con risposte note. La valutazione offline viene spesso svolta durante lo sviluppo (e può far parte delle pipeline CI/CD) per verificare miglioramenti o prevenire regressioni. Il vantaggio è che è **ripetibile e puoi ottenere metriche di accuratezza chiare dato che hai il ground truth**. Potresti anche simulare query utente e misurare le risposte dell'agente rispetto alle risposte ideali o usare metriche automatiche come descritto sopra. 

La sfida chiave della valutazione offline è assicurarsi che il tuo dataset di test sia completo e rimanga rilevante – l'agente potrebbe performare bene su un set di test fisso ma incontrare query molto diverse in produzione. Pertanto, dovresti mantenere i set di test aggiornati con nuovi casi limite ed esempi che riflettano scenari reali​. Una combinazione di piccoli casi di "smoke test" e set di valutazione più ampi è utile: set piccoli per controlli rapidi e set più grandi per metriche di performance più ampie​.

### Valutazione Online 

![Panoramica delle metriche di osservabilità](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Si riferisce alla valutazione dell'agente in un ambiente live e reale, cioè durante l'uso effettivo in produzione. La valutazione online comporta il monitoraggio delle prestazioni dell'agente sulle interazioni reali con gli utenti e l'analisi continua dei risultati. 

Ad esempio, potresti tracciare tassi di successo, punteggi di soddisfazione degli utenti o altre metriche sul traffico live. Il vantaggio della valutazione online è che **cattura cose che potresti non prevedere in laboratorio** – puoi osservare la deriva del modello nel tempo (se l'efficacia dell'agente diminuisce man mano che cambiano i pattern di input) e rilevare query o situazioni inaspettate che non erano presenti nei tuoi dati di test​. Fornisce un quadro veritiero di come l'agente si comporta sul campo. 

La valutazione online spesso comporta la raccolta di feedback implicito ed esplicito degli utenti, come discusso, e possibilmente l'esecuzione di test shadow o A/B (dove una nuova versione dell'agente gira in parallelo per confrontarsi con la vecchia). La sfida è che può essere difficile ottenere etichette o punteggi affidabili per le interazioni live – potresti dover fare affidamento sul feedback degli utenti o su metriche downstream (come ad es. se l'utente ha cliccato sul risultato). 

### Combinare i due

La valutazione online e offline non sono mutualmente esclusive; sono altamente complementari. Gli insight dal monitoraggio online (ad es. nuovi tipi di query utente dove l'agente performa male) possono essere usati per arricchire e migliorare i dataset di test offline. Al contrario, agenti che performano bene nei test offline possono essere distribuiti con maggiore fiducia e monitorati online. 

Infatti, molti team adottano un ciclo: 

_valuta offline -> distribuisci -> monitora online -> raccogli nuovi casi di errore -> aggiungi al dataset offline -> affina l'agente -> ripeti_.

## Problemi Comuni

Man mano che distribuisci agenti AI in produzione, potresti incontrare varie sfide. Ecco alcuni problemi comuni e le potenziali soluzioni:

| **Problema**    | **Soluzione Potenziale**   |
| ------------- | ------------------ |
| AI Agent not performing tasks consistently | - Affina il prompt fornito all'Agente AI; sii chiaro sugli obiettivi.<br>- Individua dove suddividere i compiti in sottoattività e gestirli con più agenti può aiutare. |
| AI Agent running into continuous loops  | - Assicurati di avere termini e condizioni di terminazione chiari in modo che l'Agente sappia quando interrompere il processo.<br>- Per compiti complessi che richiedono ragionamento e pianificazione, usa un modello più grande specializzato per attività di reasoning. |
| AI Agent tool calls are not performing well   | - Testa e valida l'output dello strumento al di fuori del sistema dell'agente.<br>- Affina i parametri definiti, i prompt e la denominazione degli strumenti.  |
| Multi-Agent system not performing consistently | - Affina i prompt dati a ciascun agente per assicurarti che siano specifici e distinti l'uno dall'altro.<br>- Costruisci un sistema gerarchico usando un agente "router" o controller per determinare quale agente è quello corretto. |

Molti di questi problemi possono essere identificati più efficacemente con l'osservabilità in atto. Le tracce e le metriche di cui abbiamo parlato aiutano a individuare esattamente dove nel flusso di lavoro dell'agente si verificano i problemi, rendendo il debug e l'ottimizzazione molto più efficienti.

## Gestione dei Costi
Ecco alcune strategie per gestire i costi della messa in produzione degli agenti AI:

**Using Smaller Models:** Piccoli modelli linguistici (SLMs) possono funzionare bene in alcuni casi d'uso basati su agenti e ridurranno significativamente i costi. Come accennato in precedenza, creare un sistema di valutazione per determinare e confrontare le prestazioni rispetto ai modelli più grandi è il modo migliore per capire quanto bene uno SLM si comporterà nel tuo caso d'uso. Prendi in considerazione l'uso di SLMs per compiti più semplici come la classificazione delle intenzioni o l'estrazione di parametri, riservando invece i modelli più grandi per il ragionamento complesso.

**Using a Router Model:** Una strategia simile è utilizzare una diversità di modelli e dimensioni. Puoi usare un LLM/SLM o una funzione serverless per instradare le richieste in base alla complessità verso i modelli più adatti. Questo aiuterà anche a ridurre i costi garantendo le prestazioni sui compiti giusti. Ad esempio, instrada le query semplici verso modelli più piccoli e veloci, e usa i modelli grandi e costosi solo per compiti di ragionamento complessi.

**Caching Responses:** Identificare richieste e attività comuni e fornire le risposte prima che passino attraverso il tuo sistema basato su agenti è un buon modo per ridurre il volume di richieste simili. Puoi persino implementare un flusso per identificare quanto una richiesta sia simile alle richieste memorizzate nella cache usando modelli di IA più semplici. Questa strategia può ridurre significativamente i costi per le domande frequenti o per flussi di lavoro comuni.

## Vediamo come funziona nella pratica

Nel [notebook d'esempio di questa sezione](./code_samples/10_autogen_evaluation.ipynb), vedremo esempi di come possiamo usare strumenti di osservabilità per monitorare e valutare il nostro agente.


### Hai altre domande sugli agenti AI in produzione?

Unisciti al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) per incontrare altri studenti, partecipare alle ore di ricevimento e ottenere risposte alle tue domande sugli agenti AI.

## Lezione precedente

[Pattern di metacognizione](../09-metacognition/README.md)

## Lezione successiva

[Protocolli agentici](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Esclusione di responsabilità:
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica Co-op Translator (https://github.com/Azure/co-op-translator). Sebbene ci impegniamo a garantire l'accuratezza, si prega di notare che le traduzioni automatiche possono contenere errori o inesattezze. Il documento originale nella sua lingua nativa deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda una traduzione professionale eseguita da un traduttore umano. Non ci assumiamo responsabilità per eventuali fraintendimenti o interpretazioni errate derivanti dall'uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->