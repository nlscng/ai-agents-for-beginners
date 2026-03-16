[![Agenti AI Affidabili](../../../translated_images/it/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Clicca sull'immagine sopra per visualizzare il video di questa lezione)_

# Costruire Agenti AI Affidabili

## Introduzione

Questa lezione tratterà:

- Come costruire e distribuire Agenti AI sicuri ed efficaci
- Considerazioni importanti sulla sicurezza durante lo sviluppo di Agenti AI.
- Come mantenere la privacy dei dati e degli utenti durante lo sviluppo di Agenti AI.

## Obiettivi di Apprendimento

Dopo aver completato questa lezione, saprai come:

- Identificare e mitigare i rischi durante la creazione di Agenti AI.
- Implementare misure di sicurezza per garantire che dati e accessi siano gestiti correttamente.
- Creare Agenti AI che mantengano la privacy dei dati e forniscano un'esperienza utente di qualità.

## Sicurezza

Iniziamo esaminando come costruire applicazioni agentiche sicure. Sicurezza significa che l'agente AI opera come progettato. Come sviluppatori di applicazioni agentiche, disponiamo di metodi e strumenti per massimizzare la sicurezza:

### Costruire un Framework per i Messaggi di Sistema

Se hai mai costruito un'applicazione AI usando Large Language Models (LLM), conosci l'importanza di progettare un prompt di sistema robusto o messaggio di sistema. Questi prompt stabiliscono le meta-regole, istruzioni e linee guida su come l’LLM interagirà con l’utente e i dati.

Per gli Agenti AI, il prompt di sistema è ancora più importante poiché gli Agenti AI necessiteranno di istruzioni altamente specifiche per completare i compiti che abbiamo progettato per loro.

Per creare prompt di sistema scalabili, possiamo utilizzare un framework per messaggi di sistema per costruire uno o più agenti nella nostra applicazione:

![Costruire un Framework per i Messaggi di Sistema](../../../translated_images/it/system-message-framework.3a97368c92d11d68.webp)

#### Passo 1: Creare un Messaggio Meta di Sistema 

Il meta prompt sarà usato da un LLM per generare i prompt di sistema per gli agenti che creeremo. Lo progettiamo come un modello in modo da poter creare efficientemente più agenti se necessario.

Ecco un esempio di messaggio meta di sistema che potremmo fornire all’LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Passo 2: Creare un prompt base

Il passo successivo è creare un prompt base per descrivere l'Agente AI. Devi includere il ruolo dell'agente, i compiti che l'agente completerà e ogni altra responsabilità dell'agente.

Ecco un esempio:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Passo 3: Fornire il Messaggio di Sistema Base all’LLM

Ora possiamo ottimizzare questo messaggio di sistema fornendo il messaggio meta di sistema come messaggio di sistema insieme al nostro messaggio di sistema base.

Questo produrrà un messaggio di sistema meglio progettato per guidare i nostri Agenti AI:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Passo 4: Iterare e Migliorare

Il valore di questo framework per i messaggi di sistema è quello di poter scalare più facilmente la creazione di messaggi di sistema da molteplici agenti così come migliorare i tuoi messaggi di sistema nel tempo. È raro avere un messaggio di sistema che funzioni perfettamente al primo tentativo per il tuo caso d’uso completo. Essere in grado di fare piccole modifiche e miglioramenti cambiando il messaggio di sistema base ed eseguendolo attraverso il sistema ti permetterà di confrontare e valutare i risultati.

## Comprendere le Minacce

Per costruire agenti AI affidabili, è importante capire e mitigare i rischi e le minacce al tuo agente AI. Vediamo solo alcune delle diverse minacce agli Agenti AI e come puoi pianificare e prepararti meglio per esse.

![Comprendere le Minacce](../../../translated_images/it/understanding-threats.89edeada8a97fc0f.webp)

### Compito e Istruzioni

**Descrizione:** Gli aggressori cercano di modificare le istruzioni o gli obiettivi dell’agente AI tramite prompting o manipolando gli input.

**Mitigazione**: Eseguire controlli di validazione e filtri sugli input per rilevare prompt potenzialmente pericolosi prima che vengano elaborati dall’Agente AI. Poiché questi attacchi di solito richiedono frequenti interazioni con l’Agente, limitare il numero di turni in una conversazione è un altro modo per prevenire questi tipi di attacchi.

### Accesso a Sistemi Critici

**Descrizione:** Se un agente AI ha accesso a sistemi e servizi che memorizzano dati sensibili, gli aggressori possono compromettere la comunicazione tra l’agente e questi servizi. Questi possono essere attacchi diretti o tentativi indiretti di ottenere informazioni su questi sistemi tramite l’agente.

**Mitigazione:** Gli agenti AI dovrebbero avere accesso ai sistemi solo in base al principio del bisogno per prevenire questi tipi di attacchi. La comunicazione tra l’agente e il sistema dovrebbe essere anche sicura. Implementare autenticazione e controllo accessi è un altro modo per proteggere queste informazioni.

### Sovraccarico di Risorse e Servizi

**Descrizione:** Gli agenti AI possono accedere a diversi strumenti e servizi per completare i compiti. Gli aggressori possono usare questa capacità per attaccare questi servizi inviando un alto volume di richieste tramite l’Agente AI, il che può causare malfunzionamenti del sistema o costi elevati.

**Mitigazione:** Implementare politiche per limitare il numero di richieste che un agente AI può effettuare a un servizio. Limitare il numero di turni di conversazione e richieste al tuo agente AI è un altro modo per prevenire questi tipi di attacchi.

### Avvelenamento della Base di Conoscenza

**Descrizione:** Questo tipo di attacco non prende di mira direttamente l’agente AI ma la base di conoscenza e altri servizi che l’agente AI utilizzerà. Potrebbe coinvolgere la corruzione dei dati o delle informazioni che l’agente AI utilizzerà per completare un compito, portando a risposte distorte o non intenzionali all’utente.

**Mitigazione:** Effettuare verifiche regolari dei dati che l’agente AI utilizzerà nei suoi flussi di lavoro. Assicurarsi che l'accesso a questi dati sia sicuro e modificato solo da persone affidabili per evitare questo tipo di attacco.

### Errori a Catena

**Descrizione:** Gli agenti AI accedono a vari strumenti e servizi per completare compiti. Errori causati dagli aggressori possono provocare guasti in altri sistemi a cui l’agente AI è connesso, rendendo l’attacco più diffuso e difficile da diagnosticare.

**Mitigazione**: Un metodo per evitare ciò è far operare l’Agente AI in un ambiente limitato, come eseguire compiti in un contenitore Docker, per prevenire attacchi diretti al sistema. Creare meccanismi di fallback e logiche di ritentativo quando certi sistemi rispondono con errori è un altro modo per prevenire guasti più ampi del sistema.

## Humano nella Loop

Un altro modo efficace per costruire sistemi di Agenti AI affidabili è usare un Humano-in-the-loop. Questo crea un flusso dove gli utenti possono fornire feedback agli Agenti durante l’esecuzione. Gli utenti agiscono essenzialmente come agenti in un sistema multi-agente fornendo approvazione o terminando il processo in corso.

![Umano nella Loop](../../../translated_images/it/human-in-the-loop.5f0068a678f62f4f.webp)

Ecco un frammento di codice che utilizza AutoGen per mostrare come questo concetto è implementato:

```python

# Crea gli agenti.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Usa input() per ottenere l'input dell'utente dalla console.

# Crea la condizione di terminazione che finirà la conversazione quando l'utente dice "APPROVE".
termination = TextMentionTermination("APPROVE")

# Crea il team.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Esegui la conversazione e trasmettila alla console.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Usa asyncio.run(...) quando si esegue in uno script.
await Console(stream)

```

## Conclusione

Costruire agenti AI affidabili richiede una progettazione accurata, misure di sicurezza robuste e iterazione continua. Implementando sistemi strutturati di meta prompting, comprendendo le potenziali minacce e applicando strategie di mitigazione, gli sviluppatori possono creare agenti AI sicuri ed efficaci. Inoltre, incorporare un approccio con Humano-in-the-loop garantisce che gli agenti AI rimangano allineati ai bisogni degli utenti riducendo i rischi. Con l’evolversi dell’AI, mantenere un approccio proattivo su sicurezza, privacy e considerazioni etiche sarà fondamentale per favorire fiducia e affidabilità nei sistemi guidati dall’AI.

### Hai altre domande su come costruire Agenti AI Affidabili?

Unisciti al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) per incontrare altri studenti, partecipare a office hours e ricevere risposte alle tue domande sugli Agenti AI.

## Risorse Aggiuntive

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Panoramica sull’AI responsabile</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Valutazione di modelli AI generativi e applicazioni AI</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Messaggi di sistema per la sicurezza</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Modello di Valutazione del Rischio</a>

## Lezione Precedente

[Agentic RAG](../05-agentic-rag/README.md)

## Lezione Successiva

[Pattern di Progettazione per la Pianificazione](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Avvertenza**:  
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica [Co-op Translator](https://github.com/Azure/co-op-translator). Pur impegnandoci per garantire accuratezza, si prega di notare che le traduzioni automatiche possono contenere errori o imprecisioni. Il documento originale nella sua lingua nativa deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda una traduzione professionale effettuata da traduttori umani. Non siamo responsabili per eventuali incomprensioni o interpretazioni errate derivanti dall’uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->