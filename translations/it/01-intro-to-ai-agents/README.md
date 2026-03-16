[![Introduzione agli Agenti AI](../../../translated_images/it/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Fai clic sull'immagine sopra per guardare il video di questa lezione)_


# Introduzione agli Agenti AI e casi d'uso

Benvenuti al corso "Agenti AI per principianti"! Questo corso fornisce conoscenze fondamentali ed esempi pratici per la costruzione di Agenti AI.

Unisciti alla <a href="https://discord.gg/kzRShWzttr" target="_blank">Community Discord di Azure AI</a> per incontrare altri studenti e sviluppatori di Agenti AI e porre qualsiasi domanda tu abbia su questo corso.

Per iniziare questo corso, cominciamo con una migliore comprensione di cosa sono gli Agenti AI e di come possiamo usarli nelle applicazioni e nei flussi di lavoro che costruiamo.

## Introduzione

In questa lezione vedremo:

- Cosa sono gli Agenti AI e quali sono i diversi tipi di agenti.
- In quali casi d'uso gli Agenti AI sono più adatti e come possono aiutarci.
- Quali sono alcuni dei blocchi di base nella progettazione di soluzioni agentiche.

## Obiettivi di apprendimento
Dopo aver completato questa lezione, dovresti essere in grado di:

- Comprendere i concetti degli Agenti AI e come si differenziano da altre soluzioni AI.
- Applicare gli Agenti AI nel modo più efficiente.
- Progettare soluzioni agentiche in modo produttivo per utenti e clienti.

## Definizione di Agenti AI e tipi di Agenti AI

### Cosa sono gli Agenti AI?

Gli Agenti AI sono **sistemi** che permettono ai **Large Language Models(LLMs)** di **eseguire azioni** estendendo le loro capacità fornendo agli LLM **accesso a strumenti** e **conoscenza**.

Scomponiamo questa definizione in parti più piccole:

- **System** - È importante pensare agli agenti non come a un singolo componente ma come a un sistema di molti componenti. A livello base, i componenti di un Agente AI sono:
  - **Environment** - Lo spazio definito in cui l'Agente AI opera. Ad esempio, se avessimo un Agente AI per prenotazioni di viaggio, l'ambiente potrebbe essere il sistema di prenotazione che l'Agente AI utilizza per completare i compiti.
  - **Sensors** - Gli ambienti contengono informazioni e forniscono feedback. Gli Agenti AI utilizzano sensori per raccogliere e interpretare queste informazioni sullo stato corrente dell'ambiente. Nell'esempio dell'Agente per prenotazioni di viaggio, il sistema di prenotazione può fornire informazioni come disponibilità degli hotel o prezzi dei voli.
  - **Actuators** - Una volta che l'Agente AI riceve lo stato corrente dell'ambiente, per il compito attuale l'agente determina quale azione eseguire per modificare l'ambiente. Per l'agente di prenotazioni di viaggio, potrebbe essere prenotare una camera disponibile per l'utente.

![Cosa sono gli Agenti AI?](../../../translated_images/it/what-are-ai-agents.1ec8c4d548af601a.webp)

**Large Language Models** - Il concetto di agenti esisteva prima della creazione degli LLM. Il vantaggio di costruire Agenti AI con gli LLM è la loro capacità di interpretare il linguaggio umano e i dati. Questa capacità consente agli LLM di interpretare le informazioni ambientali e definire un piano per modificare l'ambiente.

**Perform Actions** - Al di fuori dei sistemi Agente, gli LLM sono limitati a situazioni in cui l'azione è generare contenuti o informazioni basate sul prompt dell'utente. All'interno dei sistemi Agente, gli LLM possono portare a termine attività interpretando la richiesta dell'utente e usando gli strumenti disponibili nel loro ambiente.

**Access To Tools** - A quali strumenti l'LLM ha accesso è definito da 1) l'ambiente in cui opera e 2) lo sviluppatore dell'Agente AI. Nel nostro esempio dell'agente di viaggio, gli strumenti dell'agente sono limitati dalle operazioni disponibili nel sistema di prenotazione e/o lo sviluppatore può limitare l'accesso agli strumenti dell'agente ai soli voli.

**Memory+Knowledge** - La memoria può essere a breve termine nel contesto della conversazione tra l'utente e l'agente. A lungo termine, al di fuori delle informazioni fornite dall'ambiente, gli Agenti AI possono anche recuperare conoscenza da altri sistemi, servizi, strumenti e persino da altri agenti. Nell'esempio dell'agente di viaggio, questa conoscenza potrebbe essere l'informazione sulle preferenze di viaggio dell'utente contenuta in un database clienti.

### I diversi tipi di agenti

Ora che abbiamo una definizione generale degli Agenti AI, vediamo alcuni tipi specifici di agenti e come si applicherebbero a un agente AI per prenotazioni di viaggio.

| **Tipo di Agente**                | **Descrizione**                                                                                                                       | **Esempio**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Agenti a Riflesso Semplice**      | Eseguono azioni immediate basate su regole predefinite.                                                                                  | L'agente di viaggio interpreta il contesto dell'email e inoltra reclami di viaggio al servizio clienti.                                                                                                                          |
| **Agenti a Riflesso Basati su Modello** | Eseguono azioni basate su un modello del mondo e sui cambiamenti a quel modello.                                                              | L'agente di viaggio dà priorità agli itinerari con variazioni di prezzo significative basandosi sull'accesso ai dati storici dei prezzi.                                                                                                             |
| **Agenti Basati su Obiettivi**         | Creano piani per raggiungere obiettivi specifici interpretando l'obiettivo e determinando le azioni per raggiungerlo.                                  | L'agente di viaggio prenota un viaggio determinando gli arrangiamenti necessari (auto, trasporto pubblico, voli) dalla posizione attuale alla destinazione.                                                                                |
| **Agenti Basati sull'Utilità**      | Considerano le preferenze e valutano i compromessi numericamente per determinare come raggiungere gli obiettivi.                                               | L'agente di viaggio massimizza l'utilità valutando comodità vs costo quando prenota un viaggio.                                                                                                                                          |
| **Agenti Apprendenti**           | Migliorano nel tempo rispondendo al feedback e aggiustando le azioni di conseguenza.                                                        | L'agente di viaggio migliora utilizzando il feedback dei clienti proveniente da sondaggi post-viaggio per apportare modifiche alle prenotazioni future.                                                                                                               |
| **Agenti Gerarchici**       | Presentano più agenti in un sistema a livelli, con agenti di livello superiore che suddividono i compiti in sotto-compiti che gli agenti di livello inferiore completano. | L'agente di viaggio annulla un viaggio suddividendo il compito in sotto-compiti (per esempio, annullare prenotazioni specifiche) e facendo completare tali sotto-compiti agli agenti di livello inferiore, che riferiscono all'agente di livello superiore.                                     |
| **Sistemi Multi-Agente (MAS)** | Gli agenti completano compiti in modo indipendente, sia cooperativo che competitivo.                                                           | Cooperativo: più agenti prenotano servizi di viaggio specifici come hotel, voli e intrattenimento. Competitivo: più agenti gestiscono e competono su un calendario condiviso di prenotazioni alberghiere per assegnare clienti all'hotel. |

## Quando usare gli Agenti AI

Nella sezione precedente, abbiamo usato il caso d'uso dell'Agente di Viaggio per spiegare come i diversi tipi di agenti possano essere usati in diversi scenari di prenotazione di viaggio. Continueremo a usare questa applicazione durante il corso.

Vediamo i tipi di casi d'uso per i quali gli Agenti AI sono più indicati:

![Quando usare gli Agenti AI?](../../../translated_images/it/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Problemi aperti** - permettere all'LLM di determinare i passaggi necessari per completare un compito poiché non sempre possono essere codificati rigidamente in un flusso di lavoro.
- **Processi multi-step** - compiti che richiedono un livello di complessità in cui l'Agente AI deve usare strumenti o informazioni su più interazioni invece che in un'unica operazione.  
- **Miglioramento nel tempo** - compiti in cui l'agente può migliorare nel tempo ricevendo feedback dall'ambiente o dagli utenti al fine di fornire una maggiore utilità.

Affronteremo altre considerazioni sull'uso degli Agenti AI nella lezione Costruire Agenti AI Affidabili.

## Basi delle soluzioni agentiche

### Sviluppo degli agenti

Il primo passo nella progettazione di un sistema Agente AI è definire gli strumenti, le azioni e i comportamenti. In questo corso, ci concentriamo sull'uso del **Azure AI Agent Service** per definire i nostri Agenti. Offre funzionalità come:

- Selezione di modelli aperti come OpenAI, Mistral e Llama
- Uso di dati con licenza tramite fornitori come Tripadvisor
- Utilizzo di strumenti standardizzati OpenAPI 3.0

### Pattern agentici

La comunicazione con gli LLM avviene tramite prompt. Data la natura semi-autonoma degli Agenti AI, non è sempre possibile o necessario ripromptare manualmente l'LLM dopo un cambiamento nell'ambiente. Usiamo i **pattern agentici** che ci permettono di fornire prompt all'LLM su più passaggi in modo più scalabile.

Questo corso è suddiviso in alcuni dei pattern agentici più popolari attualmente.

### Framework agentici

I framework agentici permettono agli sviluppatori di implementare pattern agentici tramite codice. Questi framework offrono template, plugin e strumenti per una migliore collaborazione degli Agenti AI. Questi vantaggi forniscono capacità migliori per l'osservabilità e la risoluzione dei problemi dei sistemi di Agenti AI.

In questo corso esploreremo l'framework AutoGen orientato alla ricerca e il framework pronto per la produzione Agent di Semantic Kernel.

## Esempi di codice

- Python: [Framework Agente](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Framework Agente](./code_samples/01-dotnet-agent-framework.md)

## Hai altre domande sugli Agenti AI?

Unisciti al [Discord di Microsoft Foundry](https://aka.ms/ai-agents/discord) per incontrare altri studenti, partecipare alle office hours e ottenere risposte alle tue domande sugli Agenti AI.

## Lezione precedente

[Impostazione del corso](../00-course-setup/README.md)

## Lezione successiva

[Esplorare i framework agentici](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Dichiarazione di non responsabilità:
Questo documento è stato tradotto utilizzando il servizio di traduzione basato sull'intelligenza artificiale (IA) [Co-op Translator](https://github.com/Azure/co-op-translator). Pur impegnandoci per l'accuratezza, si prega di notare che le traduzioni automatiche possono contenere errori o imprecisioni. Il documento originale nella sua lingua nativa deve essere considerato la fonte autorevole. Per informazioni critiche si consiglia di ricorrere a una traduzione professionale effettuata da un traduttore umano. Non siamo responsabili per eventuali malintesi o interpretazioni errate derivanti dall'uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->