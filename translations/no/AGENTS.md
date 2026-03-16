# AGENTS.md

## Project Overview

Dette arkivet inneholder "AI Agents for Beginners" - et omfattende pedagogisk kurs som lærer alt som trengs for å bygge AI-agenter. Kurset består av 15+ leksjoner som dekker grunnprinsipper, designmønstre, rammeverk og produksjonsutrulling av AI-agenter.

**Nøkkelteknologier:**
- Python 3.12+
- Jupyter Notebooks for interaktiv læring
- AI-rammeverk: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI-tjenester: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (gratisnivå tilgjengelig)

**Arkitektur:**
- Leksjonsbasert struktur (00-15+ directories)
- Hver leksjon inneholder: README-dokumentasjon, kodeeksempler (Jupyter-notatbøker) og bilder
- Flerspråklig støtte via automatisert oversettelsessystem
- Flere rammeverksvalg per leksjon (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Setup Commands

### Prerequisites
- Python 3.12 or higher
- GitHub account (for GitHub Models - free tier)
- Azure subscription (optional, for Azure AI services)

### Initial Setup

1. **Clone or fork the repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ELLER
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Create and activate Python virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # På Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # Rediger .env med dine API-nøkler og endepunkter
   ```

### Required Environment Variables

For **GitHub Models (gratis)**:
- `GITHUB_TOKEN` - Personlig tilgangstoken fra GitHub

For **Azure AI-tjenester** (valgfritt):
- `PROJECT_ENDPOINT` - Microsoft Foundry prosjektendepunkt
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API-nøkkel
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI endepunkt-URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Navn på distribusjon for chatmodell
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Navn på distribusjon for embedding-modellen
- Additional Azure configuration as shown in `.env.example`

## Development Workflow

### Running Jupyter Notebooks

Hver leksjon inneholder flere Jupyter-notatbøker for forskjellige rammeverk:

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigate to a lesson directory** (e.g., `01-intro-to-ai-agents/code_samples/`)

3. **Open and run notebooks:**
   - `*-semantic-kernel.ipynb` - Bruke Semantic Kernel-rammeverket
   - `*-autogen.ipynb` - Bruke AutoGen-rammeverket
   - `*-python-agent-framework.ipynb` - Bruke Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Bruke Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Bruke Azure AI Agent Service

### Working with Different Frameworks

**Semantic Kernel + GitHub Models:**
- Gratisnivå tilgjengelig med GitHub-konto
- Bra for læring og eksperimentering
- Filnavnmønster: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Gratisnivå tilgjengelig med GitHub-konto
- Multi-agent orkestreringsmuligheter
- Filnavnmønster: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Nyeste rammeverk fra Microsoft
- Tilgjengelig i Python og .NET
- Filnavnmønster: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Krever Azure-abonnement
- Produksjonsklare funksjoner
- Filnavnmønster: `*-azureaiagent.ipynb`

## Testing Instructions

Dette er et pedagogisk arkiv med eksempelkode snarere enn produksjonskode med automatiske tester. For å verifisere oppsettet og endringene dine:

### Manual Testing

1. **Test Python environment:**
   ```bash
   python --version  # Bør være 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test notebook execution:**
   ```bash
   # Konverter notatbok til skript og kjør (tester importene)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verify environment variables:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Running Individual Notebooks

Åpne notatbøker i Jupyter og kjør cellene sekvensielt. Hver notatbok er selvstendig og inkluderer:
- Import-setninger
- Konfigurasjonslasting
- Eksempelimplementeringer av agenter
- Forventede utskrifter i markdown-celler

## Code Style

### Python Conventions

- **Python Version**: 3.12+
- **Code Style**: Følg standard Python PEP 8-konvensjoner
- **Notebooks**: Bruk tydelige markdown-celler for å forklare konsepter
- **Imports**: Gruppér etter standardbibliotek, tredjepart og lokale imports

### Jupyter Notebook Conventions

- Inkluder beskrivende markdown-celler før kodeceller
- Legg til eksempler på utdata i notatbøkene for referanse
- Bruk tydelige variabelnavn som matcher leksjonskonsepter
- Hold notatbøkenes kjørerekkefølge lineær (celle 1 → 2 → 3...)

### File Organization

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

## Build and Deployment

### Building Documentation

Dette arkivet bruker Markdown for dokumentasjon:
- README.md-filer i hver leksjonsmappe
- Hoved-README.md i repository root
- Automatisert oversettelsessystem via GitHub Actions

### CI/CD Pipeline

Ligger i `.github/workflows/`:

1. **co-op-translator.yml** - Automatisk oversettelse til 50+ språk
2. **welcome-issue.yml** - Ønsker nye issue-skaper velkommen
3. **welcome-pr.yml** - Ønsker nye pull request-bidragsytere velkommen

### Deployment

Dette er et pedagogisk arkiv - ingen distribusjonsprosess. Brukere:
1. Fork eller klon arkivet
2. Kjør notatbøkene lokalt eller i GitHub Codespaces
3. Lær ved å endre og eksperimentere med eksemplene

## Pull Request Guidelines

### Before Submitting

1. **Test your changes:**
   - Kjør berørte notatbøker helt gjennom
   - Bekreft at alle celler kjøres uten feil
   - Sjekk at utdataene er passende

2. **Documentation updates:**
   - Oppdater README.md hvis du legger til nye konsepter
   - Legg til kommentarer i notatbøker for kompleks kode
   - Sørg for at markdown-celler forklarer formålet

3. **File changes:**
   - Unngå å commite `.env`-filer (bruk `.env.example`)
   - Ikke commite `venv/` eller `__pycache__/` kataloger
   - Behold notatbokutdata når de demonstrerer konsepter
   - Fjern midlertidige filer og sikkerhetskopierte notatbøker (`*-backup.ipynb`)

### PR Title Format

Bruk beskrivende titler:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Correct typo in lesson-XX README`
- `[Update] Improve code sample in lesson-XX`
- `[Docs] Update setup instructions`

### Required Checks

- Notatbøker bør kjøre uten feil
- README-filer bør være klare og korrekte
- Følg eksisterende kode-mønstre i arkivet
- Oppretthold konsistens med andre leksjoner

## Additional Notes

### Common Gotchas

1. **Uoverensstemmelse i Python-versjon:**
   - Sørg for at Python 3.12+ brukes
   - Noen pakker kan ikke fungere med eldre versjoner
   - Bruk `python3 -m venv` for å spesifisere Python-versjon eksplisitt

2. **Miljøvariabler:**
   - Opprett alltid `.env` fra `.env.example`
   - Ikke commite `.env`-filen (den er i `.gitignore`)
   - GitHub-token trenger passende tillatelser

3. **Pakkekonflikter:**
   - Bruk et nytt virtuelt miljø
   - Installer fra `requirements.txt` i stedet for individuelle pakker
   - Noen notatbøker kan kreve tilleggspakker nevnt i deres markdown-celler

4. **Azure-tjenester:**
   - Azure AI-tjenester krever aktivt abonnement
   - Noen funksjoner er regionsspesifikke
   - Begrensninger for gratisnivå gjelder for GitHub Models

### Learning Path

Anbefalt rekkefølge gjennom leksjonene:
1. **00-course-setup** - Start her for miljøoppsett
2. **01-intro-to-ai-agents** - Forstå grunnleggende om AI-agenter
3. **02-explore-agentic-frameworks** - Lær om forskjellige rammeverk
4. **03-agentic-design-patterns** - Kjerne designmønstre
5. Fortsett gjennom de nummererte leksjonene sekvensielt

### Framework Selection

Velg rammeverk basert på dine mål:
- **Læring/Prototyping**: Semantic Kernel + GitHub Models (gratis)
- **Multi-agent-systemer**: AutoGen
- **Nyeste funksjoner**: Microsoft Agent Framework (MAF)
- **Produksjonsutrulling**: Azure AI Agent Service

### Getting Help

- Bli med i [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Gå gjennom leksjonens README-filer for spesifikk veiledning
- Se hoved-[README.md](./README.md) for en oversikt over kurset
- Referer til [Course Setup](./00-course-setup/README.md) for detaljerte oppsettinstruksjoner

### Contributing

Dette er et åpent pedagogisk prosjekt. Bidrag velkomne:
- Forbedre kodeeksempler
- Rette skrivefeil eller feil
- Legge til forklarende kommentarer
- Foreslå nye leksjonstemaer
- Oversette til flere språk

Se [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) for nåværende behov.

## Project-Specific Context

### Multi-Language Support

Dette arkivet bruker et automatisert oversettelsessystem:
- 50+ språk støttet
- Oversettelser i `/translations/<lang-code>/` kataloger
- GitHub Actions workflow håndterer oversettelsesoppdateringer
- Kildefiler er på engelsk i repoets rot

### Lesson Structure

Hver leksjon følger et konsistent mønster:
1. Videominibilde med lenke
2. Skriftlig leksjonsinnhold (README.md)
3. Kodeeksempler i flere rammeverk
4. Læringsmål og forutsetninger
5. Ekstra læringsressurser med lenker

### Code Sample Naming

Format: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Leksjon 4, Semantic Kernel
- `07-autogen.ipynb` - Leksjon 7, AutoGen
- `14-python-agent-framework.ipynb` - Leksjon 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Leksjon 14, MAF .NET

### Special Directories

- `translated_images/` - Lokaliserte bilder for oversettelser
- `images/` - Originale bilder for engelsk innhold
- `.devcontainer/` - VS Code development container configuration
- `.github/` - GitHub Actions workflows og maler

### Dependencies

Nøkkelpakker fra `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen-rammeverket
- `semantic-kernel` - Semantic Kernel-rammeverket
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI-tjenester
- `azure-search-documents` - Azure AI Search-integrasjon
- `chromadb` - Vektordatabasen for RAG-eksempler
- `chainlit` - Chat UI-rammeverk
- `browser_use` - Nettleserautomatisering for agenter
- `mcp[cli]` - Støtte for Model Context Protocol
- `mem0ai` - Hukommelseshåndtering for agenter

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfraskrivelse:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Det opprinnelige dokumentet i sitt originalspråk bør betraktes som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->