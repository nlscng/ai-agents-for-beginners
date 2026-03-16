# AGENTS.md

## Prezentare generală a proiectului

This repository contains "AI Agents for Beginners" - a comprehensive educational course teaching everything needed to build AI Agents. The course consists of 15+ lessons covering fundamentals, design patterns, frameworks, and production deployment of AI agents.

**Tehnologii cheie:**
- Python 3.12+
- Jupyter Notebooks pentru învățare interactivă
- Framework-uri AI: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Servicii Azure AI: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (nivel gratuit disponibil)

**Arhitectură:**
- Structură bazată pe lecții (directoare 00-15+)
- Fiecare lecție conține: documentație README, exemple de cod (Jupyter notebooks) și imagini
- Suport pentru mai multe limbi printr-un sistem automatizat de traducere
- Multiple opțiuni de framework per lecție (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Comenzi de configurare

### Cerințe prealabile
- Python 3.12 sau mai recent
- Cont GitHub (pentru GitHub Models - nivel gratuit)
- Abonament Azure (opțional, pentru serviciile Azure AI)

### Configurare inițială

1. **Clonați sau faceți fork la repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # SAU
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Creați și activați mediu virtual Python:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Pe Windows: venv\Scripts\activate
   ```

3. **Instalați dependențele:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configurați variabilele de mediu:**
   ```bash
   cp .env.example .env
   # Editează fișierul .env cu cheile tale API și endpoint-urile.
   ```

### Variabile de mediu necesare

Pentru **GitHub Models (gratuit)**:
- `GITHUB_TOKEN` - token de acces personal GitHub

Pentru **Azure AI Services** (opțional):
- `PROJECT_ENDPOINT` - endpointul proiectului Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - cheie API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL endpoint Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - numele implementării pentru modelul de chat
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - numele implementării pentru embeddings
- Configurare Azure suplimentară, așa cum se arată în `.env.example`

## Flux de lucru pentru dezvoltare

### Rularea notebook-urilor Jupyter

Fiecare lecție conține mai multe notebook-uri Jupyter pentru diferite framework-uri:

1. **Porniți Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigați la un director de lecție** (de ex., `01-intro-to-ai-agents/code_samples/`)

3. **Deschideți și rulați notebook-urile:**
   - `*-semantic-kernel.ipynb` - Using Semantic Kernel framework
   - `*-autogen.ipynb` - Using AutoGen framework
   - `*-python-agent-framework.ipynb` - Using Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Using Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Using Azure AI Agent Service

### Lucrul cu diferite framework-uri

**Semantic Kernel + GitHub Models:**
- Nivel gratuit disponibil cu cont GitHub
- Bun pentru învățare și experimentare
- File pattern: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Nivel gratuit disponibil cu cont GitHub
- Capabilități de orchestrare multi-agent
- File pattern: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Cel mai recent framework de la Microsoft
- Disponibil în Python și .NET
- File pattern: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Necesită abonament Azure
- Funcționalități pregătite pentru producție
- File pattern: `*-azureaiagent.ipynb`

## Instrucțiuni de testare

This is an educational repository with example code rather than production code with automated tests. To verify your setup and changes:

### Testare manuală

1. **Testați mediul Python:**
   ```bash
   python --version  # Ar trebui să fie 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Testați execuția notebook-urilor:**
   ```bash
   # Convertește notebook-ul în script și rulează (testează importurile)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verificați variabilele de mediu:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Rularea notebook-urilor individuale

Deschideți notebook-urile în Jupyter și executați celulele secvențial. Fiecare notebook este autonom și include:
- Instrucțiuni de import
- Încărcare configurație
- Implementări de exemplu ale agenților
- Output-uri așteptate în celulele markdown

## Stilul codului

### Convenții Python

- **Versiune Python**: 3.12+
- **Stilul codului**: Urmați convențiile standard Python PEP 8
- **Notebooks**: Folosiți celule markdown clare pentru a explica conceptele
- **Imports**: Grupează după biblioteca standard, terțe, importuri locale

### Convenții pentru Jupyter Notebook-uri

- Includeți celule markdown descriptive înaintea celulelor de cod
- Adăugați exemple de output în notebook-uri pentru referință
- Folosiți nume de variabile clare care corespund conceptelor lecției
- Mențineți ordinea de execuție a notebook-ului liniară (celula 1 → 2 → 3...)

### Organizarea fișierelor

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

## Construire și implementare

### Generarea documentației

Acest repository folosește Markdown pentru documentație:
- Fișiere README.md în fiecare folder de lecție
- README.md principal la rădăcina depozitului
- Sistem automatizat de traducere prin GitHub Actions

### Pipeline CI/CD

Situat în `.github/workflows/`:

1. **co-op-translator.yml** - Traducere automată în peste 50 de limbi
2. **welcome-issue.yml** - Primește creatorii de issue-uri noi
3. **welcome-pr.yml** - Primește noii contribuitori de pull request-uri

### Implementare

Acesta este un repository educațional - nu există proces de implementare. Utilizatorii:
1. Faceți fork sau clonați repository-ul
2. Rulați notebook-urile local sau în GitHub Codespaces
3. Învățați modificând și experimentând cu exemplele

## Ghid pentru Pull Request-uri

### Înainte de trimitere

1. **Testați modificările:**
   - Rulați complet notebook-urile afectate
   - Verificați că toate celulele se execută fără erori
   - Verificați că output-urile sunt adecvate

2. **Actualizări ale documentației:**
   - Actualizați README.md dacă adăugați concepte noi
   - Adăugați comentarii în notebook-uri pentru cod complex
   - Asigurați-vă că celulele markdown explică scopul

3. **Modificări de fișiere:**
   - Evitați să comiteți fișiere `.env` (folosiți `.env.example`)
   - Nu comiteți directoarele `venv/` sau `__pycache__/`
   - Păstrați output-urile notebook-urilor când demonstrează concepte
   - Eliminați fișierele temporare și notebook-urile de backup (`*-backup.ipynb`)

### Format titlu PR

Folosiți titluri descriptive:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Correct typo in lesson-XX README`
- `[Update] Improve code sample in lesson-XX`
- `[Docs] Update setup instructions`

### Verificări obligatorii

- Notebook-urile ar trebui să se execute fără erori
- Fișierele README ar trebui să fie clare și precise
- Urmați modelele existente de cod din repository
- Mențineți consistența cu celelalte lecții

## Note suplimentare

### Probleme comune

1. **Incompatibilitate a versiunii Python:**
   - Asigurați-vă că folosiți Python 3.12+
   - Unele pachete pot să nu funcționeze cu versiuni mai vechi
   - Folosiți `python3 -m venv` pentru a specifica explicit versiunea Python

2. **Variabilele de mediu:**
   - Întotdeauna creați `.env` pornind de la `.env.example`
   - Nu comiteți fișierul `.env` (este în `.gitignore`)
   - Token-ul GitHub necesită permisiuni adecvate

3. **Conflicte între pachete:**
   - Folosiți un mediu virtual proaspăt
   - Instalați din `requirements.txt` în loc de pachete individuale
   - Unele notebook-uri pot necesita pachete suplimentare menționate în celulele lor markdown

4. **Servicii Azure:**
   - Serviciile Azure AI necesită un abonament activ
   - Unele funcționalități sunt specifice regiunii
   - Se aplică limitările nivelului gratuit pentru GitHub Models

### Parcurs de învățare

Progresie recomandată prin lecții:
1. **00-course-setup** - Începeți aici pentru configurarea mediului
2. **01-intro-to-ai-agents** - Înțelegeți elementele fundamentale ale agenților AI
3. **02-explore-agentic-frameworks** - Aflați despre diferite framework-uri
4. **03-agentic-design-patterns** - Modele de design de bază
5. Continuați prin lecțiile numerotate în ordine secvențială

### Alegerea framework-ului

Alegeți framework-ul în funcție de obiectivele dvs.:
- **Învățare/Prototipare**: Semantic Kernel + GitHub Models (free)
- **Sisteme multi-agent**: AutoGen
- **Funcționalități de ultimă oră**: Microsoft Agent Framework (MAF)
- **Implementare în producție**: Azure AI Agent Service

### Obținerea ajutorului

- Alăturați-vă [Comunității Microsoft Foundry pe Discord](https://aka.ms/ai-agents/discord)
- Consultați fișierele README ale lecțiilor pentru ghidaj specific
- Verificați [README.md](./README.md) principal pentru prezentarea cursului
- Consultați [Configurarea cursului](./00-course-setup/README.md) pentru instrucțiuni detaliate de configurare

### Contribuții

Acesta este un proiect educațional deschis. Contribuțiile sunt binevenite:
- Îmbunătățiți exemplele de cod
- Remediați greșeli de tastare sau erori
- Adăugați comentarii clarificatoare
- Sugerați subiecte noi pentru lecții
- Traduceți în limbi suplimentare

Vezi [Issue-uri GitHub](https://github.com/microsoft/ai-agents-for-beginners/issues) pentru nevoi curente.

## Context specific proiectului

### Suport pentru mai multe limbi

Acest repository folosește un sistem de traducere automatizat:
- Suport pentru peste 50 de limbi
- Traduceri în directoarele `/translations/<lang-code>/`
- Workflow-ul GitHub Actions se ocupă de actualizările traducerilor
- Fișierele sursă sunt în engleză la rădăcina repository-ului

### Structura lecțiilor

Fiecare lecție urmează un tipar consistent:
1. Miniatură video cu link
2. Conținut scris al lecției (README.md)
3. Exemple de cod în multiple framework-uri
4. Obiective de învățare și cerințe prealabile
5. Resurse suplimentare de învățare legate

### Numele fișierelor exemple de cod

Format: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Lecția 4, Semantic Kernel
- `07-autogen.ipynb` - Lecția 7, AutoGen
- `14-python-agent-framework.ipynb` - Lecția 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lecția 14, MAF .NET

### Directoare speciale

- `translated_images/` - Imagini localizate pentru traduceri
- `images/` - Imagini originale pentru conținutul în engleză
- `.devcontainer/` - Configurare container dezvoltare VS Code
- `.github/` - Workflow-uri și template-uri GitHub Actions

### Dependențe

Pachete cheie din `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - framework-ul AutoGen
- `semantic-kernel` - Framework-ul Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Servicii Azure AI
- `azure-search-documents` - Integrare Azure AI Search
- `chromadb` - Bază de date vectorială pentru exemple RAG
- `chainlit` - Framework UI pentru chat
- `browser_use` - Automatizare browser pentru agenți
- `mcp[cli]` - Suport Model Context Protocol
- `mem0ai` - Managementul memoriei pentru agenți

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Declinare de responsabilitate**:
Acest document a fost tradus folosind serviciul de traducere AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim să fim cât mai corecți, vă rugăm să rețineți că traducerile automatizate pot conține erori sau inexactități. Documentul original în limba sa nativă trebuie considerat sursa autorizată. Pentru informații critice, se recomandă o traducere profesională realizată de un traducător uman. Nu ne asumăm răspunderea pentru eventualele neînțelegeri sau interpretări greșite rezultate din utilizarea acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->