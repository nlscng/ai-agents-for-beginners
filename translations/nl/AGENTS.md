# AGENTS.md

## Projectoverzicht

Deze repository bevat "AI Agents for Beginners" - een uitgebreide educatieve cursus die alles leert wat nodig is om AI-agents te bouwen. De cursus bestaat uit 15+ lessen die de basisprincipes, ontwerp patronen, frameworks en productie-implementatie van AI-agents behandelen.

**Belangrijke Technologieën:**
- Python 3.12+
- Jupyter Notebooks voor interactief leren
- AI-frameworks: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Services: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (gratis tier beschikbaar)

**Architectuur:**
- Lesgebaseerde structuur (mappen 00-15+)
- Elke les bevat: README-documentatie, codevoorbeelden (Jupyter notebooks) en afbeeldingen
- Meertalige ondersteuning via geautomatiseerd vertaalsysteem
- Meerdere frameworkopties per les (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Setup-commando's

### Vereisten
- Python 3.12 of hoger
- GitHub-account (voor GitHub Models - gratis tier)
- Azure-abonnement (optioneel, voor Azure AI services)

### Eerste setup

1. **Clone of fork de repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # OF
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Maak en activeer een Python virtuele omgeving aan:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Op Windows: venv\Scripts\activate
   ```

3. **Installeer afhankelijkheden:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Stel omgevingsvariabelen in:**
   ```bash
   cp .env.example .env
   # Bewerk .env met uw API-sleutels en eindpunten
   ```

### Vereiste Omgevingsvariabelen

Voor **GitHub Models (Gratis)**:
- `GITHUB_TOKEN` - Persoonlijke toegangs-token van GitHub

Voor **Azure AI Services** (optioneel):
- `PROJECT_ENDPOINT` - Microsoft Foundry project endpoint
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API-sleutel
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI endpoint URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Deploy naam voor chatmodel
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Deploy naam voor embeddings
- Extra Azure configuratie zoals weergegeven in `.env.example`

## Ontwikkelworkflow

### Jupyter Notebooks draaien

Elke les bevat meerdere Jupyter notebooks voor verschillende frameworks:

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigeer naar een lesmap** (bijv. `01-intro-to-ai-agents/code_samples/`)

3. **Open en run notebooks:**
   - `*-semantic-kernel.ipynb` - Gebruik van het Semantic Kernel framework
   - `*-autogen.ipynb` - Gebruik van het AutoGen framework
   - `*-python-agent-framework.ipynb` - Gebruik van Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Gebruik van Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Gebruik van Azure AI Agent Service

### Werken met verschillende frameworks

**Semantic Kernel + GitHub Models:**
- Gratis tier beschikbaar met GitHub-account
- Geschikt voor leren en experimenteren
- Bestandsnaam patroon: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Gratis tier beschikbaar met GitHub-account
- Multi-agent orchestration mogelijkheden
- Bestandsnaam patroon: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Laatste framework van Microsoft
- Beschikbaar in Python en .NET
- Bestandsnaam patroon: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Vereist Azure-abonnement
- Productieklaar met uitgebreide functies
- Bestandsnaam patroon: `*-azureaiagent.ipynb`

## Testinstructies

Dit is een educatieve repository met voorbeeldcode in plaats van productiecode met geautomatiseerde tests. Om je setup en wijzigingen te verifiëren:

### Handmatig testen

1. **Test Python-omgeving:**
   ```bash
   python --version  # Moet 3.12+ zijn
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test notebook-uitvoering:**
   ```bash
   # Converteer notebook naar script en voer uit (test imports)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Controleer omgevingsvariabelen:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Individuele notebooks draaien

Open notebooks in Jupyter en voer cellen na elkaar uit. Elke notebook is zelfstandig en bevat:
- Import statements
- Configuratieladen
- Voorbeeldimplementaties van agents
- Verwachte uitvoer in markdown cellen

## Code stijl

### Python conventies

- **Python versie**: 3.12+
- **Code stijl**: Volg standaard Python PEP 8 conventies
- **Notebooks**: Gebruik duidelijke markdown cellen om concepten uit te leggen
- **Imports**: Groepeer op standaardbibliotheek, derde partijen, lokale imports

### Jupyter Notebook conventies

- Gebruik beschrijvende markdown cellen voor codecellen
- Voeg uitvoervoorbeelden in de notebooks toe voor referentie
- Gebruik duidelijke variabelenamen die overeenkomen met lesconcepten
- Houd de notebook uitvoeringsvolgorde lineair (cel 1 → 2 → 3…)

### Bestandsorganisatie

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

## Build en Deploy

### Documentatie bouwen

Deze repository gebruikt Markdown voor documentatie:
- README.md-bestanden in elke lesmap
- Hoofd README.md in de root van de repository
- Geautomatiseerd vertaalsysteem via GitHub Actions

### CI/CD Pipeline

Te vinden in `.github/workflows/`:

1. **co-op-translator.yml** - Automatische vertaling naar 50+ talen
2. **welcome-issue.yml** - Verwelkomt nieuwe issue-makers
3. **welcome-pr.yml** - Verwelkomt nieuwe pull request bijdragers

### Deployment

Dit is een educatieve repository - geen deployment proces. Gebruikers:
1. Forken of clonen de repository
2. Runnen notebooks lokaal of in GitHub Codespaces
3. Leren door voorbeelden te wijzigen en experimenteren

## Richtlijnen voor Pull Requests

### Voor het indienen

1. **Test je wijzigingen:**
   - Voer de aangescherpte notebooks volledig uit
   - Zorg dat alle cellen zonder fouten draaien
   - Controleer of de output passend is

2. **Documentatie-updates:**
   - Update README.md bij toevoegen van nieuwe concepten
   - Voeg commentaar toe in notebooks bij complexe code
   - Zorg dat markdown cellen het doel uitleggen

3. **Bestandswijzigingen:**
   - Vermijd committen van `.env` bestanden (gebruik `.env.example`)
   - Commit geen `venv/` of `__pycache__/` mappen
   - Houd notebook-uitvoeren indien ze concepten laten zien
   - Verwijder tijdelijke bestanden en backup notebooks (`*-backup.ipynb`)

### Formaat PR-titel

Gebruik beschrijvende titels:
- `[Lesson-XX] Voeg nieuw voorbeeld toe voor <concept>`
- `[Fix] Corrigeer typefout in lesson-XX README`
- `[Update] Verbeter codevoorbeeld in lesson-XX`
- `[Docs] Update setup instructies`

### Vereiste checks

- Notebooks moeten foutloos uitvoeren
- README-bestanden moeten duidelijk en accuraat zijn
- Volg bestaande codepatronen in de repository
- Houd consistentie met andere lessen

## Extra Notities

### Veelvoorkomende valkuilen

1. **Python-versie mismatch:**
   - Zorg dat Python 3.12+ wordt gebruikt
   - Sommige pakketten werken niet met oudere versies
   - Gebruik `python3 -m venv` om expliciet de Python-versie te kiezen

2. **Omgevingsvariabelen:**
   - Maak altijd `.env` aan op basis van `.env.example`
   - Commit het `.env`-bestand niet (staat in `.gitignore`)
   - GitHub token heeft juiste permissies nodig

3. **Pakketconflicten:**
   - Gebruik een schone virtuele omgeving
   - Installeer via `requirements.txt` in plaats van losse pakketten
   - Sommige notebooks vereisen extra pakketten, genoemd in markdown cellen

4. **Azure diensten:**
   - Azure AI services vereisen actief abonnement
   - Sommige functies zijn regiogebonden
   - Gratis tier beperkingen gelden voor GitHub Models

### Leerpad

Aanbevolen volgorde door de lessen:
1. **00-course-setup** - Start hier voor setup van de omgeving
2. **01-intro-to-ai-agents** - Begrijp de basis van AI-agents
3. **02-explore-agentic-frameworks** - Leer over verschillende frameworks
4. **03-agentic-design-patterns** - Kernontwerp patronen
5. Ga verder met genummerde lessen in volgorde

### Framework keuze

Kies framework op basis van je doelen:
- **Leren/Prototyping**: Semantic Kernel + GitHub Models (gratis)
- **Multi-agent systemen**: AutoGen
- **Laatste features**: Microsoft Agent Framework (MAF)
- **Productie deployment**: Azure AI Agent Service

### Hulp krijgen

- Word lid van de [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Bekijk de README-bestanden van de lessen voor specifieke richtlijnen
- Raadpleeg de hoofd [README.md](./README.md) voor cursusoverzicht
- Zie [Course Setup](./00-course-setup/README.md) voor gedetailleerde setup instructies

### Bijdragen

Dit is een open educatief project. Bijdragen zijn welkom:
- Verbeter codevoorbeelden
- Corrigeer typfouten of fouten
- Voeg verduidelijkende opmerkingen toe
- Stel nieuwe lesthema's voor
- Vertaal naar extra talen

Zie [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) voor actuele behoeften.

## Projectspecific Context

### Meertalige ondersteuning

Deze repository gebruikt een geautomatiseerd vertaalsysteem:
- 50+ talen ondersteund
- Vertalingen in `/translations/<lang-code>/` mappen
- GitHub Actions workflow beheert vertaalupdates
- Bronbestanden zijn in het Engels in de root van de repository

### Lesstructuur

Elke les volgt een consistent patroon:
1. Videominiatuur met link
2. Geschreven lesinhoud (README.md)
3. Codevoorbeelden in meerdere frameworks
4. Leerdoelen en vereisten
5. Extra leermaterialen gelinkt

### Naamgeving codevoorbeelden

Formaat: `<les-nummer>-<framework-naam>.ipynb`
- `04-semantic-kernel.ipynb` - Les 4, Semantic Kernel
- `07-autogen.ipynb` - Les 7, AutoGen
- `14-python-agent-framework.ipynb` - Les 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Les 14, MAF .NET

### Speciale mappen

- `translated_images/` - Gelokaliseerde afbeeldingen voor vertalingen
- `images/` - Originele afbeeldingen voor Engelse inhoud
- `.devcontainer/` - VS Code ontwikkelcontainer configuratie
- `.github/` - GitHub Actions workflows en templates

### Afhankelijkheden

Belangrijke pakketten uit `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen framework
- `semantic-kernel` - Semantic Kernel framework
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI services
- `azure-search-documents` - Azure AI Search integratie
- `chromadb` - Vector database voor RAG voorbeelden
- `chainlit` - Chat UI framework
- `browser_use` - Browser automatisering voor agents
- `mcp[cli]` - Model Context Protocol ondersteuning
- `mem0ai` - Geheugenbeheer voor agents

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Dit document is vertaald met behulp van de AI vertaaldienst [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel wij streven naar nauwkeurigheid, dient u zich ervan bewust te zijn dat automatische vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het originele document in de oorspronkelijke taal moet als de gezaghebbende bron worden beschouwd. Voor kritieke informatie wordt professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->