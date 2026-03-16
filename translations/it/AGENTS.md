# AGENTS.md

## Panoramica del Progetto

Questo repository contiene "AI Agents for Beginners" - un corso educativo completo che insegna tutto il necessario per costruire Agenti AI. Il corso è composto da oltre 15 lezioni che coprono i fondamenti, i design pattern, i framework e il deployment in produzione degli agenti AI.

**Tecnologie Chiave:**
- Python 3.12+
- Jupyter Notebooks per apprendimento interattivo
- Framework AI: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Servizi Azure AI: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (disponibile con piano gratuito)

**Architettura:**
- Struttura basata su lezioni (cartelle 00-15+)
- Ogni lezione contiene: documentazione README, esempi di codice (Jupyter notebooks) e immagini
- Supporto multilingue tramite sistema di traduzione automatica
- Opzioni multiple di framework per ogni lezione (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Comandi di Configurazione

### Prerequisiti
- Python 3.12 o superiore
- Account GitHub (per GitHub Models - piano gratuito)
- Abbonamento Azure (opzionale, per servizi Azure AI)

### Configurazione Iniziale

1. **Clona o fai il fork del repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # O
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Crea e attiva un ambiente virtuale Python:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Su Windows: venv\Scripts\activate
   ```

3. **Installa le dipendenze:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configura le variabili d'ambiente:**
   ```bash
   cp .env.example .env
   # Modifica .env con le tue chiavi API e gli endpoint
   ```

### Variabili d'Ambiente Richieste

Per **GitHub Models (Gratuito)**:
- `GITHUB_TOKEN` - Token di accesso personale da GitHub

Per **Servizi Azure AI** (opzionale):
- `PROJECT_ENDPOINT` - Endpoint progetto Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - Chiave API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL endpoint Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Nome deployment per modello chat
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Nome deployment per embeddings
- Ulteriori configurazioni Azure come indicato in `.env.example`

## Flusso di Lavoro per lo Sviluppo

### Esecuzione dei Jupyter Notebooks

Ogni lezione contiene più notebook Jupyter per differenti framework:

1. **Avvia Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Naviga nella cartella della lezione** (es. `01-intro-to-ai-agents/code_samples/`)

3. **Apri ed esegui i notebook:**
   - `*-semantic-kernel.ipynb` - Usando il framework Semantic Kernel
   - `*-autogen.ipynb` - Usando il framework AutoGen
   - `*-python-agent-framework.ipynb` - Usando Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Usando Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Usando Azure AI Agent Service

### Lavorare con Differenti Framework

**Semantic Kernel + GitHub Models:**
- Piano gratuito disponibile con account GitHub
- Ottimo per apprendimento e sperimentazione
- Pattern file: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Piano gratuito disponibile con account GitHub
- Capacità di orchestrazione multi-agente
- Pattern file: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Framework più recente di Microsoft
- Disponibile in Python e .NET
- Pattern file: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Richiede abbonamento Azure
- Funzionalità pronte per la produzione
- Pattern file: `*-azureaiagent.ipynb`

## Istruzioni per i Test

Questo è un repository educativo con codice di esempio piuttosto che codice di produzione con test automatizzati. Per verificare la tua configurazione e modifiche:

### Test Manuale

1. **Test ambiente Python:**
   ```bash
   python --version  # Deve essere 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test esecuzione notebook:**
   ```bash
   # Converti il notebook in script ed esegui (verifica le importazioni)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verifica variabili d'ambiente:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Esecuzione di Singoli Notebook

Apri i notebook in Jupyter ed esegui le celle sequenzialmente. Ogni notebook è autonomo e include:
- Importazioni
- Caricamento configurazioni
- Esempi di implementazioni agenti
- Output attesi in celle markdown

## Stile di Codice

### Convenzioni Python

- **Versione Python**: 3.12+
- **Stile codice**: Seguire le convenzioni standard Python PEP 8
- **Notebook**: Usare chiare celle markdown per spiegare i concetti
- **Importazioni**: Raggruppare per libreria standard, terze parti e locali

### Convenzioni Jupyter Notebook

- Includere celle markdown descrittive prima delle celle di codice
- Aggiungere esempi di output nei notebook come riferimento
- Usare nomi variabili chiari che rispecchiano i concetti della lezione
- Mantenere ordine di esecuzione lineare (cella 1 → 2 → 3...)

### Organizzazione dei File

```
<lesson-number>-<lesson-name>/
├── README.md                     # Lesson documentation
├── code_samples/
│   ├── <number>-semantic-kernel.ipynb
│   ├── <number>-autogen.ipynb
│   ├── <number>-python-agent-framework.ipynb
│   └── <number>-azureaiagent.ipynb
└── images/
    └── *.png
```

## Compilazione e Distribuzione

### Compilazione Documentazione

Questo repository usa Markdown per la documentazione:
- File README.md in ogni cartella di lezione
- README.md principale alla radice del repository
- Sistema di traduzione automatica tramite GitHub Actions

### Pipeline CI/CD

Situata in `.github/workflows/`:

1. **co-op-translator.yml** - Traduzione automatica in oltre 50 lingue
2. **welcome-issue.yml** - Accoglie nuovi creatori di issue
3. **welcome-pr.yml** - Accoglie i nuovi contributori di pull request

### Distribuzione

Questo è un repository educativo - nessun processo di deployment. Gli utenti:
1. Fanno fork o clonano il repository
2. Eseguono i notebook localmente o in GitHub Codespaces
3. Imparano modificando e sperimentando con gli esempi

## Linee Guida per le Pull Request

### Prima di Inviare

1. **Testa le tue modifiche:**
   - Esegui completamente i notebook coinvolti
   - Verifica che tutte le celle si eseguano senza errori
   - Controlla che gli output siano appropriati

2. **Aggiornamenti documentazione:**
   - Aggiorna README.md se aggiungi nuovi concetti
   - Aggiungi commenti nei notebook per codice complesso
   - Assicurati che le celle markdown spieghino lo scopo

3. **Modifiche ai file:**
   - Evita di committare file `.env` (usa `.env.example`)
   - Non includere cartelle `venv/` o `__pycache__/`
   - Mantieni output notebook quando dimostrano concetti
   - Rimuovi file temporanei e backup di notebook (`*-backup.ipynb`)

### Formato del Titolo PR

Usa titoli descrittivi:
- `[Lesson-XX] Aggiungi nuovo esempio per <concetto>`
- `[Fix] Correggi refuso in README della lezione-XX`
- `[Update] Migliora esempio di codice in lezione-XX`
- `[Docs] Aggiorna istruzioni di configurazione`

### Controlli Richiesti

- I notebook devono eseguirsi senza errori
- I file README devono essere chiari e accurati
- Seguire i pattern di codice esistenti nel repository
- Mantenere coerenza con le altre lezioni

## Note Aggiuntive

### Errori Comuni

1. **Versione Python non corretta:**
   - Assicurarsi di usare Python 3.12+
   - Alcuni pacchetti potrebbero non funzionare con versioni precedenti
   - Usare `python3 -m venv` per specificare espressamente la versione

2. **Variabili d'ambiente:**
   - Creare sempre `.env` a partire da `.env.example`
   - Non includere il file `.env` nel commit (è presente in `.gitignore`)
   - Il token GitHub necessita permessi appropriati

3. **Conflitti tra pacchetti:**
   - Usare un ambiente virtuale nuovo
   - Installare da `requirements.txt` anziché pacchetti singoli
   - Alcuni notebook potrebbero richiedere pacchetti aggiuntivi indicati nelle celle markdown

4. **Servizi Azure:**
   - I servizi Azure AI richiedono abbonamento attivo
   - Alcune funzionalità sono specifiche per regione
   - Limiti del piano gratuito si applicano a GitHub Models

### Percorso di Apprendimento

Progressione raccomandata tra le lezioni:
1. **00-course-setup** - Inizio con configurazione ambiente
2. **01-intro-to-ai-agents** - Fondamenti di agenti AI
3. **02-explore-agentic-frameworks** - Scoprire diversi framework
4. **03-agentic-design-patterns** - Pattern di design fondamentali
5. Continuare con lezioni numerate in sequenza

### Scelta del Framework

Scegli il framework in base ai tuoi obiettivi:
- **Apprendimento/Prototipazione**: Semantic Kernel + GitHub Models (gratuito)
- **Sistemi multi-agente**: AutoGen
- **Ultime funzionalità**: Microsoft Agent Framework (MAF)
- **Deployment in produzione**: Azure AI Agent Service

### Ottenere Aiuto

- Unisciti al [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Consulta i file README delle lezioni per indicazioni specifiche
- Controlla il [README.md principale](./README.md) per panoramica corso
- Consulta [Course Setup](./00-course-setup/README.md) per istruzioni dettagliate

### Contribuire

Questo è un progetto educativo aperto. Contributi benvenuti:
- Migliorare esempi di codice
- Correggere refusi o errori
- Aggiungere commenti esplicativi
- Suggerire nuovi argomenti per lezioni
- Tradurre in ulteriori lingue

Vedi [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) per necessità correnti.

## Contesto Specifico del Progetto

### Supporto Multilingue

Questo repository usa un sistema di traduzione automatica:
- Supporta oltre 50 lingue
- Traduzioni in directory `/translations/<codice-lingua>/`
- Workflow GitHub Actions si occupa di aggiornare le traduzioni
- File sorgente sono in inglese nella radice repository

### Struttura della Lezione

Ogni lezione segue uno schema consistente:
1. Miniatura video con link
2. Contenuto scritto della lezione (README.md)
3. Esempi di codice in molteplici framework
4. Obiettivi di apprendimento e prerequisiti
5. Risorse aggiuntive di approfondimento linkate

### Nomenclatura Esempi Codice

Formato: `<numero-lezione>-<nome-framework>.ipynb`
- `04-semantic-kernel.ipynb` - Lezione 4, Semantic Kernel
- `07-autogen.ipynb` - Lezione 7, AutoGen
- `14-python-agent-framework.ipynb` - Lezione 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lezione 14, MAF .NET

### Cartelle Speciali

- `translated_images/` - Immagini localizzate per traduzioni
- `images/` - Immagini originali per contenuto in inglese
- `.devcontainer/` - Configurazione contenitore sviluppo VS Code
- `.github/` - Workflow e template GitHub Actions

### Dipendenze

Pacchetti chiave da `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - Framework AutoGen
- `semantic-kernel` - Framework Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Servizi Azure AI
- `azure-search-documents` - Integrazione Azure AI Search
- `chromadb` - Database vettoriale per esempi RAG
- `chainlit` - Framework interfaccia chat
- `browser_use` - Automazione browser per agenti
- `mcp[cli]` - Supporto Model Context Protocol
- `mem0ai` - Gestione memoria per agenti

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica [Co-op Translator](https://github.com/Azure/co-op-translator). Pur impegnandoci per garantire accuratezza, si prega di notare che le traduzioni automatiche possono contenere errori o inesattezze. Il documento originale nella sua lingua madre deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda la traduzione professionale effettuata da un essere umano. Non ci assumiamo alcuna responsabilità per eventuali malintesi o interpretazioni errate derivanti dall’uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->