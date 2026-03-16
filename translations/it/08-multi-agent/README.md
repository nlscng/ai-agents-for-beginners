[![Multi-Agent Design](../../../translated_images/it/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Clicca sull'immagine sopra per vedere il video di questa lezione)_

# Modelli di progettazione multi-agente

Non appena inizi a lavorare su un progetto che coinvolge più agenti, dovrai prendere in considerazione il modello di progettazione multi-agente. Tuttavia, potrebbe non essere immediatamente chiaro quando passare a più agenti e quali siano i vantaggi.

## Introduzione

In questa lezione, cercheremo di rispondere alle seguenti domande:

- Quali sono gli scenari in cui i multi-agenti sono applicabili?
- Quali sono i vantaggi di usare più agenti rispetto a un singolo agente che svolge più compiti?
- Quali sono i blocchi fondamentali per implementare il modello di progettazione multi-agente?
- Come possiamo avere visibilità su come i vari agenti interagiscono tra loro?

## Obiettivi di apprendimento

Dopo questa lezione, dovresti essere in grado di:

- Identificare scenari in cui i multi-agenti sono applicabili
- Riconoscere i vantaggi di usare più agenti rispetto a un singolo agente.
- Comprendere i blocchi fondamentali per implementare il modello di progettazione multi-agente.

Qual è il quadro generale?

*I multi-agenti sono un modello di progettazione che permette a più agenti di lavorare insieme per raggiungere un obiettivo comune*.

Questo modello è ampiamente utilizzato in diversi campi, inclusi la robotica, i sistemi autonomi e il calcolo distribuito.

## Scenari in cui i multi-agenti sono applicabili

Quali sono quindi gli scenari dove è utile usare più agenti? La risposta è che ci sono molti scenari in cui impiegare più agenti è vantaggioso, specialmente nei seguenti casi:

- **Carichi di lavoro elevati**: Grandi carichi di lavoro possono essere suddivisi in compiti più piccoli e assegnati a diversi agenti, permettendo l'elaborazione parallela e un completamento più rapido. Un esempio è un grande compito di elaborazione dati.
- **Compiti complessi**: Come i carichi di lavoro elevati, anche i compiti complessi possono essere divisi in sotto-compiti più piccoli e assegnati a diversi agenti, ciascuno specializzato in un aspetto specifico del compito. Un buon esempio sono i veicoli autonomi in cui diversi agenti gestiscono la navigazione, il rilevamento degli ostacoli e la comunicazione con gli altri veicoli.
- **Esperienze diverse**: Agenti diversi possono avere competenze differenziate, permettendo loro di gestire aspetti differenti di un compito in modo più efficace rispetto a un singolo agente. Un esempio è nell'ambito sanitario, dove agenti possono gestire diagnosi, piani di trattamento e monitoraggio del paziente.

## Vantaggi dell'uso di multi-agenti rispetto a un singolo agente

Un sistema con un solo agente potrebbe funzionare bene per compiti semplici, ma per compiti più complessi, usare più agenti può offrire diversi vantaggi:

- **Specializzazione**: Ogni agente può essere specializzato in un compito specifico. La mancanza di specializzazione in un singolo agente significa che si ha un agente che può fare tutto, ma potrebbe confondersi su cosa fare quando affronta un compito complesso. Potrebbe, ad esempio, finire per svolgere un compito per il quale non è il più adatto.
- **Scalabilità**: È più facile scalare i sistemi aggiungendo più agenti piuttosto che sovraccaricare un singolo agente.
- **Tolleranza ai guasti**: Se un agente fallisce, gli altri possono continuare a funzionare, garantendo l'affidabilità del sistema.

Facciamo un esempio, prenotiamo un viaggio per un utente. Un sistema con un singolo agente dovrebbe gestire tutti gli aspetti del processo di prenotazione del viaggio, dalla ricerca dei voli alla prenotazione di hotel e auto a noleggio. Per farlo con un singolo agente, questo dovrebbe avere gli strumenti per gestire tutti questi compiti. Ciò potrebbe portare a un sistema complesso e monolitico, difficile da mantenere e scalare. Un sistema multi-agente, invece, potrebbe avere agenti diversi specializzati nella ricerca di voli, nella prenotazione di hotel e di auto a noleggio. Questo renderebbe il sistema più modulare, più facile da mantenere e scalabile.

Confronta questo con un'agenzia di viaggi gestita come un negozio a conduzione familiare rispetto a un'agenzia di viaggi gestita come una franchigia. Nel primo caso, un singolo agente gestisce tutti gli aspetti della prenotazione, mentre nella franchigia agenti diversi gestiscono aspetti diversi del processo di prenotazione.

## Blocchi fondamentali per l'implementazione del modello multi-agente

Prima di poter implementare il modello multi-agente, devi capire i blocchi fondamentali che compongono il modello.

Rendiamo questo più concreto tornando all'esempio della prenotazione di un viaggio per un utente. In questo caso, i blocchi fondamentali includono:

- **Comunicazione tra agenti**: Gli agenti per trovare voli, prenotare hotel e auto a noleggio devono comunicare e condividere informazioni sulle preferenze e i vincoli dell'utente. Devi decidere i protocolli e i metodi per questa comunicazione. In pratica, l'agente per trovare voli deve comunicare con l'agente per prenotare hotel per assicurarsi che l'hotel sia prenotato nelle stesse date del volo. Ciò significa che gli agenti devono condividere informazioni sulle date di viaggio dell'utente, cioè devi decidere *quali agenti condividono le informazioni e come le condividono*.
- **Meccanismi di coordinamento**: Gli agenti devono coordinare le loro azioni per assicurare che le preferenze e i vincoli dell'utente siano rispettati. Una preferenza dell'utente potrebbe essere volere un hotel vicino all'aeroporto, mentre un vincolo potrebbe essere che le auto a noleggio sono disponibili solo all'aeroporto. Ciò significa che l'agente per prenotare hotel deve coordinarsi con l'agente per prenotare auto a noleggio per assicurarsi che preferenze e vincoli siano rispettati. Devi quindi decidere *come gli agenti coordinano le loro azioni*.
- **Architettura degli agenti**: Gli agenti devono avere una struttura interna per prendere decisioni e imparare dalle interazioni con l'utente. Questo significa che l'agente per trovare voli deve avere una struttura interna per decidere quali voli consigliare all'utente. Devi decidere *come gli agenti prendono decisioni e imparano dalle interazioni con l'utente*. Un esempio è che l'agente per trovare voli potrebbe usare un modello di apprendimento automatico per raccomandare voli all'utente basandosi sulle preferenze passate.
- **Visibilità sulle interazioni multi-agente**: Hai bisogno di visibilità su come i vari agenti interagiscono tra loro. Ciò significa che devi avere strumenti e tecniche per tracciare le attività e le interazioni degli agenti. Questo può essere sotto forma di strumenti per logging e monitoraggio, strumenti di visualizzazione e metriche di performance.
- **Pattern multi-agente**: Esistono diversi modelli per implementare sistemi multi-agente, come architetture centralizzate, decentralizzate e ibride. Devi scegliere il modello che meglio si adatta al tuo caso d'uso.
- **Umano nel ciclo**: Nella maggior parte dei casi, avrai un umano nel ciclo e devi istruire gli agenti su quando chiedere l'intervento umano. Questo potrebbe consistere in un utente che richiede uno specifico hotel o volo che gli agenti non hanno raccomandato o che chiede conferma prima di prenotare.

## Visibilità sulle interazioni multi-agente

È importante avere visibilità su come i vari agenti interagiscono tra loro. Questa visibilità è essenziale per il debugging, l'ottimizzazione e per assicurare l'efficacia complessiva del sistema. Per raggiungere questo, devi avere strumenti e tecniche per tracciare le attività e le interazioni degli agenti. Questo può essere sotto forma di strumenti di logging e monitoraggio, strumenti di visualizzazione, e metriche di performance.

Ad esempio, nel caso della prenotazione di un viaggio per un utente, potresti avere una dashboard che mostra lo stato di ogni agente, le preferenze e i vincoli dell'utente, e le interazioni tra agenti. Questa dashboard potrebbe mostrare le date di viaggio dell'utente, i voli raccomandati dall'agente voli, gli hotel raccomandati dall'agente hotel e le auto a noleggio raccomandate dall'agente auto. Questo ti darebbe una visione chiara di come gli agenti interagiscono e se le preferenze e vincoli dell'utente sono rispettati.

Analizziamo più in dettaglio ciascuno di questi aspetti.

- **Strumenti di logging e monitoraggio**: Vuoi che venga effettuato il logging per ogni azione intrapresa da un agente. Una voce di log potrebbe contenere informazioni sull'agente che ha effettuato l'azione, l'azione compiuta, l'orario e l'esito dell'azione. Queste informazioni possono poi essere usate per il debugging, l'ottimizzazione e altro.
- **Strumenti di visualizzazione**: Gli strumenti di visualizzazione possono aiutarti a vedere le interazioni tra agenti in maniera più intuitiva. Per esempio, potresti avere un grafo che mostra il flusso di informazioni tra agenti. Questo può aiutarti a identificare colli di bottiglia, inefficienze e altri problemi nel sistema.
- **Metriche di performance**: Le metriche di performance possono aiutarti a tracciare l'efficacia del sistema multi-agente. Per esempio, potresti tracciare il tempo necessario per completare un compito, il numero di compiti completati per unità di tempo e l'accuratezza delle raccomandazioni fatte dagli agenti. Queste informazioni possono aiutarti a individuare aree di miglioramento e ottimizzare il sistema.

## Pattern multi-agente

Esploriamo alcuni pattern concreti che possiamo usare per creare applicazioni multi-agente. Ecco alcuni pattern interessanti da considerare:

### Chat di gruppo

Questo pattern è utile quando vuoi creare un'applicazione di chat di gruppo in cui più agenti possono comunicare tra loro. Gli usi tipici includono collaborazione in team, supporto clienti e social networking.

In questo pattern, ogni agente rappresenta un utente nella chat di gruppo, e i messaggi sono scambiati tra agenti usando un protocollo di messaggistica. Gli agenti possono inviare messaggi alla chat di gruppo, ricevere messaggi dalla chat di gruppo e rispondere ai messaggi degli altri agenti.

Questo pattern può essere implementato usando un'architettura centralizzata, dove tutti i messaggi passano attraverso un server centrale, o un'architettura decentralizzata, dove i messaggi sono scambiati direttamente.

![Group chat](../../../translated_images/it/multi-agent-group-chat.ec10f4cde556babd.webp)

### Passaggio di compiti

Questo pattern è utile quando vuoi creare un'applicazione in cui più agenti possono passarsi compiti a vicenda.

Gli usi tipici includono supporto clienti, gestione dei compiti e automazione dei flussi di lavoro.

In questo pattern, ogni agente rappresenta un compito o un passaggio in un flusso di lavoro, e gli agenti possono passare compiti ad altri agenti basandosi su regole predefinite.

![Hand off](../../../translated_images/it/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Filtraggio collaborativo

Questo pattern è utile quando vuoi creare un'applicazione in cui più agenti collaborano per fare raccomandazioni agli utenti.

Il motivo per cui vuoi che più agenti collaborino è che ciascuno può avere competenze diverse e contribuire al processo di raccomandazione in modi differenti.

Prendiamo l'esempio di un utente che vuole una raccomandazione sul miglior titolo azionario da comprare sul mercato.

- **Esperto di settore**: Un agente potrebbe essere esperto in un settore specifico.
- **Analisi tecnica**: Un altro agente potrebbe essere esperto in analisi tecnica.
- **Analisi fondamentale**: Un altro ancora esperto in analisi fondamentale. Collaborando, questi agenti possono fornire una raccomandazione più completa all'utente.

![Recommendation](../../../translated_images/it/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenario: processo di rimborso

Considera uno scenario in cui un cliente sta cercando di ottenere un rimborso per un prodotto; possono essere coinvolti parecchi agenti in questo processo, ma dividiamoli tra agenti specifici per questo processo e agenti generici che possono essere usati in altri processi.

**Agenti specifici per il processo di rimborso**:

Ecco alcuni agenti che potrebbero essere coinvolti nel processo di rimborso:

- **Agente cliente**: Questo agente rappresenta il cliente ed è responsabile di iniziare il processo di rimborso.
- **Agente venditore**: Questo agente rappresenta il venditore ed è responsabile di gestire il rimborso.
- **Agente pagamento**: Questo agente rappresenta il processo di pagamento ed è responsabile di rimborsare il cliente.
- **Agente risoluzione**: Questo agente rappresenta il processo di risoluzione ed è responsabile di risolvere eventuali problemi sorti durante il processo di rimborso.
- **Agente conformità**: Questo agente rappresenta il processo di conformità ed è responsabile di assicurare che il processo di rimborso rispetti normative e politiche.

**Agenti generali**:

Questi agenti possono essere usati in altre parti del tuo business.

- **Agente spedizione**: Questo agente rappresenta il processo di spedizione ed è responsabile della spedizione del prodotto indietro al venditore. Può essere usato sia per il processo di rimborso che per spedizioni generali, ad esempio tramite un acquisto.
- **Agente feedback**: Questo agente rappresenta il processo di raccolta feedback ed è responsabile per raccogliere feedback dal cliente. Il feedback può essere raccolto in qualsiasi momento, non solo durante il rimborso.
- **Agente escalation**: Questo agente rappresenta il processo di escalation ed è responsabile di portare problemi a un livello di supporto superiore. Puoi usare questo agente in qualsiasi processo dove è necessaria un'escalation.
- **Agente notifiche**: Questo agente rappresenta il processo di notifiche ed è responsabile di inviare notifiche al cliente in varie fasi del processo di rimborso.
- **Agente analisi**: Questo agente rappresenta il processo di analisi ed è responsabile di analizzare i dati relativi al processo di rimborso.
- **Agente audit**: Questo agente rappresenta il processo di audit ed è responsabile di verificare che il processo di rimborso sia svolto correttamente.
- **Agente report**: Questo agente rappresenta il processo di reportistica ed è responsabile di generare report sul processo di rimborso.
- **Agente conoscenza**: Questo agente rappresenta il processo di gestione della conoscenza ed è responsabile di mantenere una base di conoscenza relativa al processo di rimborso. Potrebbe avere conoscenza sia su rimborsi che su altre parti del business.
- **Agente sicurezza**: Questo agente rappresenta il processo di sicurezza ed è responsabile di garantire la sicurezza del processo di rimborso.
- **Agente qualità**: Questo agente rappresenta il processo di qualità ed è responsabile di assicurare la qualità del processo di rimborso.

Sono elencati diversi agenti sia specifici per il rimborso che generali usabili in altre parti del business. Speriamo che questo ti dia un'idea di come puoi decidere quali agenti usare nel tuo sistema multi-agente.

## Compito

Progetta un sistema multi-agente per un processo di supporto clienti. Identifica gli agenti coinvolti nel processo, i loro ruoli e responsabilità, e come interagiscono tra loro. Considera sia agenti specifici per il processo di supporto clienti che agenti generali utilizzabili in altre parti del tuo business.
> Rifletti prima di leggere la soluzione seguente, potresti aver bisogno di più agenti di quanto pensi.

> SUGGERIMENTO: Pensa alle diverse fasi del processo di supporto clienti e considera anche gli agenti necessari per qualsiasi sistema.

## Soluzione

[Solution](./solution/solution.md)

## Verifiche di conoscenza

Domanda: Quando dovresti considerare l'uso di multi-agenti?

- [ ] A1: Quando hai un carico di lavoro piccolo e un compito semplice.
- [ ] A2: Quando hai un carico di lavoro grande
- [ ] A3: Quando hai un compito semplice.

[Solution quiz](./solution/solution-quiz.md)

## Riepilogo

In questa lezione, abbiamo esaminato il modello di progettazione multi-agente, inclusi gli scenari in cui i multi-agenti sono applicabili, i vantaggi dell'uso di multi-agenti rispetto a un agente singolo, i blocchi costitutivi per implementare il modello di progettazione multi-agente e come avere visibilità su come i molteplici agenti interagiscono tra loro.

### Hai altre domande sul modello di progettazione Multi-Agente?

Unisciti al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) per incontrare altri studenti, partecipare a ore d'ufficio e ottenere risposte alle tue domande sugli AI Agents.

## Risorse aggiuntive

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Modelli di progettazione AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Modelli di progettazione agentici</a>


## Lezione precedente

[Planning Design](../07-planning-design/README.md)

## Lezione successiva

[Metacognition in AI Agents](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica AI [Co-op Translator](https://github.com/Azure/co-op-translator). Sebbene ci impegniamo per la massima accuratezza, si prega di considerare che le traduzioni automatizzate possono contenere errori o inesattezze. Il documento originale nella sua lingua madre deve essere considerato la fonte autorevole. Per informazioni critiche, si consiglia una traduzione professionale effettuata da un umano. Non ci assumiamo nessuna responsabilità per eventuali incomprensioni o interpretazioni errate derivanti dall’uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->