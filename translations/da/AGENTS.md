# AGENTS.md

## Projektoversigt

Dette repository indeholder "AI-agenter for begyndere" - et omfattende undervisningsforløb, der lærer alt, hvad der er nødvendigt for at bygge AI-agenter. Kurset består af 15+ lektioner, der dækker grundlæggende principper, designmønstre, frameworks og produktions-udrulning af AI-agenter.

**Nøgle teknologier:**
- Python 3.12+
- Jupyter Notebooks til interaktiv læring
- AI Frameworks: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Services: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (gratis niveau tilgængeligt)

**Arkitektur:**
- Lektionbaseret struktur (mapper 00-15+)
- Hver lektion indeholder: README-dokumentation, kodeeksempler (Jupyter notebooks), og billeder
- Flersproget support via automatiseret oversættelsessystem
- Flere frameworkmuligheder pr. lektion (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Setup-kommandoer

### Forudsætninger
- Python 3.12 eller nyere
- GitHub-konto (til GitHub Models - gratis niveau)
- Azure abonnement (valgfrit, til Azure AI tjenester)

### Første opsætning

1. **Klon eller fork repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ELLER
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Opret og aktiver Python virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # På Windows: venv\Scripts\activate
   ```

3. **Installer afhængigheder:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Opsæt miljøvariabler:**
   ```bash
   cp .env.example .env
   # Rediger .env med dine API-nøgler og slutpunkter
   ```

### Påkrævede miljøvariabler

For **GitHub Models (gratis):**
- `GITHUB_TOKEN` - Personlig adgangstoken fra GitHub

For **Azure AI Services** (valgfrit):
- `PROJECT_ENDPOINT` - Microsoft Foundry projektendepunkt
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API-nøgle
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI endepunkt URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Udrulningsnavn for chatmodel
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Udrulningsnavn for embeddings
- Yderligere Azure-konfiguration som vist i `.env.example`

## Udviklingsarbejdsgang

### Kørsel af Jupyter Notebooks

Hver lektion indeholder flere Jupyter notebooks til forskellige frameworks:

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Naviger til en lektionsmappe** (f.eks. `01-intro-to-ai-agents/code_samples/`)

3. **Åbn og kør notebooks:**
   - `*-semantic-kernel.ipynb` - Brug af Semantic Kernel framework
   - `*-autogen.ipynb` - Brug af AutoGen framework
   - `*-python-agent-framework.ipynb` - Brug af Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Brug af Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Brug af Azure AI Agent Service

### Arbejde med forskellige frameworks

**Semantic Kernel + GitHub Models:**
- Gratis niveau tilgængeligt med GitHub-konto
- Godt til læring og eksperimenter
- Fil-mønster: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Gratis niveau tilgængeligt med GitHub-konto
- Multi-agent orkestreringsmuligheder
- Fil-mønster: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Seneste framework fra Microsoft
- Tilgængeligt i Python og .NET
- Fil-mønster: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Kræver Azure abonnement
- Produktionsklare funktioner
- Fil-mønster: `*-azureaiagent.ipynb`

## Testinstruktioner

Dette er et undervisningsrepository med eksempel kode fremfor produktionskode med automatiserede tests. For at verificere opsætning og ændringer:

### Manuel testning

1. **Test Python-miljø:**
   ```bash
   python --version  # Skal være 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test notebook-eksekvering:**
   ```bash
   # Konverter notebook til script og kør (tester imports)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verificer miljøvariabler:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Kørsel af individuelle notebooks

Åbn notebooks i Jupyter og udfør celler sekventielt. Hver notebook er selvstændig og indeholder:
- Importerklæringer
- Indlæsning af konfiguration
- Eksempel på agent-implementeringer
- Forventede outputs i markdown-celler

## Kode Stil

### Python Konventioner

- **Python version:** 3.12+
- **Kode stil:** Følg standard Python PEP 8 konventioner
- **Notebooks:** Brug klare markdown-celler til at forklare koncepter
- **Importer:** Grupper efter standardbibliotek, tredjepart, lokale imports

### Jupyter Notebook Konventioner

- Inkluder beskrivende markdown-celler før kodeceller
- Tilføj output-eksempler i notebooks til reference
- Brug klare variabelnavne, der matcher lektionsbegreber
- Hold notebook-eksekveringsordren lineær (celle 1 → 2 → 3...)

### Filorganisation

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

## Build og Deployment

### Byg dokumentation

Dette repository bruger Markdown til dokumentation:
- README.md filer i hver lektionsmappe
- Hoved-README.md i repository roden
- Automatiseret oversættelsessystem via GitHub Actions

### CI/CD Pipeline

Ligger i `.github/workflows/`:

1. **co-op-translator.yml** - Automatisk oversættelse til 50+ sprog
2. **welcome-issue.yml** - Byder nye issue-oprettelser velkommen
3. **welcome-pr.yml** - Byder nye pull request bidrag velkommen

### Deployment

Dette er et undervisningsrepository - ingen deploymentsproces. Brugere:
1. Forker eller kloner repository
2. Kører notebooks lokalt eller i GitHub Codespaces
3. Lærer ved at modificere og eksperimentere med eksempler

## Retningslinjer for Pull Requests

### Før indsendelse

1. **Test dine ændringer:**
   - Kør berørte notebooks fuldstændigt
   - Verificer at alle celler kører uden fejl
   - Kontroller at outputs er passende

2. **Dokumentationsopdateringer:**
   - Opdater README.md hvis nye koncepter tilføjes
   - Tilføj kommentarer i notebooks for kompleks kode
   - Sørg for at markdown-celler forklarer formålet

3. **Filændringer:**
   - Undgå at commite `.env` filer (brug `.env.example`)
   - Commit ikke `venv/` eller `__pycache__/` mapper
   - Behold notebook-output når de demonstrerer koncepter
   - Fjern midlertidige filer og sikkerhedskopierede notebooks (`*-backup.ipynb`)

### PR-titelformat

Brug beskrivende titler:
- `[Lesson-XX] Tilføj nyt eksempel for <koncept>`
- `[Fix] Korriger slåfejl i lesson-XX README`
- `[Update] Forbedr kodeeksempel i lesson-XX`
- `[Docs] Opdater setup instruktioner`

### Påkrævede checks

- Notebooks skal køre uden fejl
- README-filer skal være klare og korrekte
- Følg eksisterende kode mønstre i repository
- Bevar konsistens med øvrige lektioner

## Yderligere bemærkninger

### Almindelige faldgruber

1. **Python version mismatch:**
   - Sørg for at bruge Python 3.12+
   - Nogle pakker virker ikke med ældre versioner
   - Brug `python3 -m venv` for eksplicit at vælge Python-version

2. **Miljøvariabler:**
   - Opret altid `.env` ud fra `.env.example`
   - Commit ikke `.env` filen (den er i `.gitignore`)
   - GitHub-token kræver passende rettigheder

3. **Pakke-konflikter:**
   - Brug et frisk virtual environment
   - Installer fra `requirements.txt` fremfor enkeltpakker
   - Nogle notebooks kræver ekstra pakker nævnt i markdown-celler

4. **Azure tjenester:**
   - Azure AI tjenester kræver aktivt abonnement
   - Nogle funktioner er regionsspecifikke
   - Begrænsninger for gratis niveau gælder for GitHub Models

### Læringsvej

Anbefalet progression gennem lektionerne:
1. **00-course-setup** - Start her for miljøopsætning
2. **01-intro-to-ai-agents** - Forstå AI agent grundprincipper
3. **02-explore-agentic-frameworks** - Lær om forskellige frameworks
4. **03-agentic-design-patterns** - Kerne designmønstre
5. Fortsæt i nummereret rækkefølge

### Framework valg

Vælg framework baseret på dine mål:
- **Læring/prototyper:** Semantic Kernel + GitHub Models (gratis)
- **Multi-agent systemer:** AutoGen
- **Nyeste funktioner:** Microsoft Agent Framework (MAF)
- **Produktionsudrulning:** Azure AI Agent Service

### Få hjælp

- Deltag i [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Gennemgå lektionernes README-filer for specifik vejledning
- Se hoved-[README.md](./README.md) for kursusoversigt
- Se [Course Setup](./00-course-setup/README.md) for detaljerede opsætningsinstruktioner

### Bidrag

Dette er et åbent undervisningsprojekt. Bidrag er velkomne:
- Forbedr kodeeksempler
- Ret slåfejl eller fejl
- Tilføj forklarende kommentarer
- Foreslå nye lektionsemner
- Oversæt til flere sprog

Se [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) for aktuelle behov.

## Projekt-specifik kontekst

### Flersproget support

Dette repository bruger et automatiseret oversættelsessystem:
- 50+ sprog understøttet
- Oversættelser i `/translations/<lang-code>/` mapper
- GitHub Actions workflow håndterer oversættelsesopdateringer
- Kildefiler er på engelsk i repository roden

### Lektionsstruktur

Hver lektion følger et konsistent mønster:
1. Videominiature med link
2. Skriftligt lektionsindhold (README.md)
3. Kodeeksempler i flere frameworks
4. Læringsmål og forudsætninger
5. Ekstra læringsressourcer linket

### Navngivning af kodeeksempler

Format: `<lektion-nummer>-<framework-navn>.ipynb`
- `04-semantic-kernel.ipynb` - Lektion 4, Semantic Kernel
- `07-autogen.ipynb` - Lektion 7, AutoGen
- `14-python-agent-framework.ipynb` - Lektion 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lektion 14, MAF .NET

### Specielle mapper

- `translated_images/` - Lokaliserede billeder til oversættelser
- `images/` - Originale billeder til engelsk indhold
- `.devcontainer/` - VS Code udviklingscontainer konfiguration
- `.github/` - GitHub Actions workflows og skabeloner

### Afhængigheder

Nøglepakker fra `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen framework
- `semantic-kernel` - Semantic Kernel framework
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI tjenester
- `azure-search-documents` - Azure AI Search integration
- `chromadb` - Vektordatabase til RAG eksempler
- `chainlit` - Chat UI framework
- `browser_use` - Browser automatisering til agenter
- `mcp[cli]` - Model Context Protocol support
- `mem0ai` - Hukommelsesstyring for agenter

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, skal du være opmærksom på, at automatiske oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets modersmål bør betragtes som den autoritative kilde. For kritisk information anbefales professionel menneskelig oversættelse. Vi påtager os ikke ansvar for misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->