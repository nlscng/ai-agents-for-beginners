# Memoria per Agenti AI 
[![Memoria Agenti](../../../translated_images/it/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Quando si discutono i vantaggi unici della creazione di Agenti AI, si parla principalmente di due aspetti: la capacità di chiamare strumenti per completare compiti e la capacità di migliorare nel tempo. La memoria è alla base della creazione di agenti che si auto-migliorano e che possono creare esperienze migliori per i nostri utenti.

In questa lezione, esamineremo cos'è la memoria per gli Agenti AI e come possiamo gestirla e usarla a vantaggio delle nostre applicazioni.

## Introduzione

Questa lezione coprirà:

• **Comprendere la memoria degli Agenti AI**: Cos'è la memoria e perché è essenziale per gli agenti.

• **Implementazione e archiviazione della memoria**: Metodi pratici per aggiungere capacità di memoria ai tuoi agenti AI, con un focus sulla memoria a breve e lungo termine.

• **Rendere gli Agenti AI auto-miglioranti**: Come la memoria permette agli agenti di apprendere dalle interazioni passate e migliorare nel tempo.

## Implementazioni disponibili

Questa lezione include due tutorial completi in notebook:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementa la memoria usando Mem0 e Azure AI Search con il framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementa memoria strutturata usando Cognee, costruendo automaticamente un knowledge graph supportato da embeddings, visualizzando il grafo e permettendo il recupero intelligente

## Obiettivi di apprendimento

Dopo aver completato questa lezione, saprai come:

• **Differenziare tra i vari tipi di memoria degli agenti AI**, includendo memoria di lavoro, a breve termine e a lungo termine, oltre a forme specializzate come memoria della persona e memoria episodica.

• **Implementare e gestire memoria a breve e lungo termine per gli Agenti AI** usando il framework Semantic Kernel, sfruttando strumenti come Mem0, Cognee, Whiteboard memory e integrandoli con Azure AI Search.

• **Comprendere i principi alla base degli agenti AI auto-miglioranti** e come sistemi di gestione della memoria robusti contribuiscano all'apprendimento continuo e all'adattamento.

## Comprendere la memoria degli Agenti AI

Alla base, **la memoria per gli Agenti AI si riferisce ai meccanismi che permettono loro di trattenere e richiamare informazioni**. Queste informazioni possono essere dettagli specifici su una conversazione, preferenze dell'utente, azioni passate o anche pattern appresi.

Senza memoria, le applicazioni AI sono spesso prive di stato, il che significa che ogni interazione ricomincia da capo. Questo porta a un'esperienza utente ripetitiva e frustrante in cui l'agente "dimentica" il contesto o le preferenze precedenti.

### Perché la memoria è importante?

L'intelligenza di un agente è profondamente legata alla sua capacità di ricordare e utilizzare informazioni passate. La memoria permette agli agenti di essere:

• **Riflessivi**: Imparare da azioni e risultati passati.

• **Interattivi**: Mantenere il contesto durante una conversazione in corso.

• **Proattivi e reattivi**: Anticipare bisogni o rispondere in modo appropriato basandosi sui dati storici.

• **Autonomi**: Operare più indipendentemente attingendo a conoscenze memorizzate.

L'obiettivo dell'implementazione della memoria è rendere gli agenti più **affidabili e capaci**.

### Tipi di memoria

#### Memoria di lavoro

Pensalo come un pezzo di carta su cui un agente lavora durante un singolo compito o processo di pensiero in corso. Contiene informazioni immediate necessarie per calcolare il prossimo passo.

Per gli Agenti AI, la memoria di lavoro spesso cattura le informazioni più rilevanti da una conversazione, anche se l'intera cronologia della chat è lunga o troncata. Si concentra sull'estrazione di elementi chiave come requisiti, proposte, decisioni e azioni.

**Esempio di memoria di lavoro**

In un agente per prenotazioni di viaggio, la memoria di lavoro potrebbe catturare la richiesta corrente dell'utente, come "Voglio prenotare un viaggio a Parigi". Questo requisito specifico viene mantenuto nel contesto immediato dell'agente per guidare l'interazione corrente.

#### Memoria a breve termine

Questo tipo di memoria conserva le informazioni per la durata di una singola conversazione o sessione. È il contesto della chat corrente, permettendo all'agente di riferirsi ai turni precedenti del dialogo.

**Esempio di memoria a breve termine**

Se un utente chiede, "Quanto costerebbe un volo per Parigi?" e poi aggiunge "E per l'alloggio là?", la memoria a breve termine garantisce che l'agente sappia che "là" si riferisce a "Parigi" nella stessa conversazione.

#### Memoria a lungo termine

Queste sono informazioni che persistono attraverso più conversazioni o sessioni. Permettono agli agenti di ricordare preferenze dell'utente, interazioni storiche o conoscenze generali su lunghi periodi. Questo è importante per la personalizzazione.

**Esempio di memoria a lungo termine**

Una memoria a lungo termine potrebbe memorizzare che "Ben ama sciare e le attività all'aperto, gradisce il caffè con vista sulle montagne e vuole evitare piste da sci avanzate a causa di un infortunio passato". Questa informazione, appresa da interazioni precedenti, influenza le raccomandazioni in future sessioni di pianificazione di viaggi, rendendole altamente personalizzate.

#### Memoria della persona (Persona Memory)

Questo tipo di memoria specializzato aiuta un agente a sviluppare una "personalità" o "persona" coerente. Permette all'agente di ricordare dettagli su se stesso o sul ruolo previsto, rendendo le interazioni più fluide e mirate.

**Esempio di Persona Memory**
Se l'agente di viaggio è progettato per essere un "esperto pianificatore di sci", la memoria della persona potrebbe rinforzare questo ruolo, influenzando le risposte per allinearle al tono e alle conoscenze di un esperto.

#### Memoria di flusso/episodica (Workflow/Episodic Memory)

Questa memoria conserva la sequenza di passi che un agente compie durante un compito complesso, inclusi successi e fallimenti. È come ricordare episodi specifici o esperienze passate per imparare da esse.

**Esempio di memoria episodica**

Se l'agente ha provato a prenotare un volo specifico ma ha fallito a causa di indisponibilità, la memoria episodica potrebbe registrare questo fallimento, permettendo all'agente di provare voli alternativi o informare l'utente sul problema in modo più informato durante un tentativo successivo.

#### Memoria di entità (Entity Memory)

Questo implica l'estrazione e la memorizzazione di entità specifiche (come persone, luoghi o cose) ed eventi dalle conversazioni. Permette all'agente di costruire una comprensione strutturata degli elementi chiave discussi.

**Esempio di Entity Memory**

Da una conversazione su un viaggio passato, l'agente potrebbe estrarre "Parigi", "Torre Eiffel" e "cena al ristorante Le Chat Noir" come entità. In un'interazione futura, l'agente potrebbe richiamare "Le Chat Noir" e offrire di fare una nuova prenotazione lì.

#### Structured RAG (Retrieval Augmented Generation strutturato)

Sebbene RAG sia una tecnica più ampia, lo "Structured RAG" è evidenziato come una potente tecnologia di memoria. Estrae informazioni dense e strutturate da varie fonti (conversazioni, email, immagini) e le usa per migliorare precisione, recall e velocità nelle risposte. A differenza del RAG classico che si basa esclusivamente sulla similarità semantica, lo Structured RAG lavora con la struttura intrinseca dell'informazione.

**Esempio di Structured RAG**

Invece di limitarsi a corrispondere parole chiave, lo Structured RAG potrebbe analizzare i dettagli di un volo (destinazione, data, ora, compagnia) da un'email e memorizzarli in modo strutturato. Questo permette query precise come "Quale volo ho prenotato per Parigi martedì?"

## Implementazione e archiviazione della memoria

Implementare la memoria per gli Agenti AI comporta un processo sistematico di **gestione della memoria**, che include generazione, archiviazione, recupero, integrazione, aggiornamento e persino "dimenticanza" (o cancellazione) delle informazioni. Il recupero è un aspetto particolarmente cruciale.

### Strumenti di memoria specializzati

#### Mem0

Un modo per archiviare e gestire la memoria degli agenti è usare strumenti specializzati come Mem0. Mem0 funziona come uno strato di memoria persistente, permettendo agli agenti di richiamare interazioni rilevanti, memorizzare preferenze dell'utente e contesto fattuale, e apprendere da successi e fallimenti nel tempo. L'idea è che agenti senza stato si trasformino in agenti con stato.

Funziona attraverso una **pipeline di memoria in due fasi: estrazione e aggiornamento**. Prima, i messaggi aggiunti al thread di un agente vengono inviati al servizio Mem0, che usa un Large Language Model (LLM) per riassumere la cronologia della conversazione ed estrarre nuove memorie. Successivamente, una fase di aggiornamento guidata da LLM determina se aggiungere, modificare o eliminare queste memorie, memorizzandole in un archivio ibrido che può includere database vettoriali, grafici e key-value. Questo sistema supporta anche vari tipi di memoria e può incorporare una memoria grafica per gestire le relazioni tra entità.

#### Cognee

Un altro approccio potente è usare **Cognee**, una memoria semantica open-source per Agenti AI che trasforma dati strutturati e non strutturati in knowledge graph interrogabili supportati da embeddings. Cognee fornisce un'**architettura a doppio storage** che combina la ricerca per similarità vettoriale con le relazioni di grafo, consentendo agli agenti di comprendere non solo quali informazioni sono simili, ma come i concetti sono correlati tra loro.

Eccelle nel **recupero ibrido** che fonde similarità vettoriale, struttura del grafo e ragionamento LLM — dal semplice lookup di chunk grezzi fino a un question answering consapevole del grafo. Il sistema mantiene una **memoria viva** che evolve e cresce rimanendo interrogabile come un grafo connesso, supportando sia il contesto di sessione a breve termine sia la memoria persistente a lungo termine.

Il notebook tutorial di Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) dimostra la costruzione di questo livello di memoria unificato, con esempi pratici di ingestione di diverse sorgenti di dati, visualizzazione del knowledge graph e query con diverse strategie di ricerca su misura per le esigenze specifiche dell'agente.

### Archiviare la memoria con RAG

Oltre a strumenti di memoria specializzati come Mem0, puoi sfruttare servizi di ricerca robusti come **Azure AI Search come backend per archiviare e recuperare memorie**, specialmente per lo Structured RAG.

Questo ti permette di fondare le risposte del tuo agente sui tuoi dati, garantendo risposte più pertinenti e accurate. Azure AI Search può essere usato per memorizzare memorie di viaggio specifiche degli utenti, cataloghi di prodotti o qualsiasi altra conoscenza di dominio.

Azure AI Search supporta funzionalità come **Structured RAG**, che eccelle nell'estrazione e nel recupero di informazioni dense e strutturate da grandi dataset come cronologie di conversazioni, email o persino immagini. Questo fornisce "precisione e recall sovrumani" rispetto agli approcci tradizionali di chunking di testo e embeddings.

## Rendere gli Agenti AI auto-miglioranti

Un pattern comune per agenti che si auto-migliorano prevede l'introduzione di un **"agente della conoscenza"**. Questo agente separato osserva la conversazione principale tra l'utente e l'agente primario. Il suo ruolo è:

1. **Identificare informazioni preziose**: Determinare se una parte della conversazione vale la pena essere salvata come conoscenza generale o come preferenza specifica dell'utente.

2. **Estrarre e riassumere**: Distillare l'apprendimento essenziale o la preferenza dalla conversazione.

3. **Archiviare in una base di conoscenza**: Persistere queste informazioni estratte, spesso in un database vettoriale, così che possano essere recuperate in seguito.

4. **Arricchire query future**: Quando l'utente avvia una nuova query, l'agente della conoscenza recupera informazioni pertinenti memorizzate e le aggiunge al prompt dell'utente, fornendo contesto cruciale all'agente primario (simile al RAG).

### Ottimizzazioni per la memoria

• **Gestione della latenza**: Per evitare di rallentare le interazioni degli utenti, può essere usato inizialmente un modello più economico e veloce per verificare rapidamente se un'informazione è preziosa da salvare o recuperare, invocando il processo di estrazione/recupero più complesso solo quando necessario.

• **Manutenzione della base di conoscenza**: Per una knowledge base in crescita, le informazioni usate meno frequentemente possono essere spostate in "cold storage" per gestire i costi.

## Hai altre domande sulla memoria degli agenti?

Unisciti al [Discord di Microsoft Foundry](https://aka.ms/ai-agents/discord) per incontrare altri studenti, partecipare alle ore di supporto e ottenere risposte alle tue domande sugli Agenti AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Esclusione di responsabilità:
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica basato su IA Co-op Translator (https://github.com/Azure/co-op-translator). Pur impegnandoci per garantire l’accuratezza, si segnala che le traduzioni automatiche possono contenere errori o inesattezze. Il documento originale nella sua lingua deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda una traduzione professionale eseguita da un traduttore umano. Non ci assumiamo responsabilità per eventuali malintesi o interpretazioni errate derivanti dall’uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->