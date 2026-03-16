# AGENTS.md

## Projektöversikt

Detta repository innehåller "AI Agents for Beginners" – en omfattande utbildningskurs som lär ut allt som behövs för att bygga AI-agenter. Kursen består av över 15 lektioner som täcker grunder, designmönster, ramverk och produktionssättning av AI-agenter.

**Nyckelteknologier:**
- Python 3.12+
- Jupyter Notebooks för interaktivt lärande
- AI-ramverk: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI-tjänster: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (gratisnivå tillgänglig)

**Arkitektur:**
- Lektionbaserad struktur (00-15+ kataloger)
- Varje lektion innehåller: README-dokumentation, kodexempel (Jupyter notebooks) och bilder
- Flerspråkigt stöd via automatiserat översättningssystem
- Flera ramverksalternativ per lektion (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Installationskommandon

### Förutsättningar
- Python 3.12 eller högre
- GitHub-konto (för GitHub Models – gratisnivå)
- Azure-prenumeration (valfritt, för Azure AI-tjänster)

### Initial installation

1. **Klona eller fork:a repositoryt:**  
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ELLER
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```
  
2. **Skapa och aktivera Python virtuellt miljö:**  
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # På Windows: venv\Scripts\activate
   ```
  
3. **Installera beroenden:**  
   ```bash
   pip install -r requirements.txt
   ```
  
4. **Konfigurera miljövariabler:**  
   ```bash
   cp .env.example .env
   # Redigera .env med dina API-nycklar och slutpunkter
   ```
  
### Obligatoriska miljövariabler

För **GitHub Models (gratisnivå)**:  
- `GITHUB_TOKEN` – Personlig access-token från GitHub

För **Azure AI Services** (valfritt):  
- `PROJECT_ENDPOINT` – Microsoft Foundry projektendpoint  
- `AZURE_OPENAI_API_KEY` – Azure OpenAI API-nyckel  
- `AZURE_OPENAI_ENDPOINT` – Azure OpenAI endpoint-URL  
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` – Deploymentsnamn för chatmodell  
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` – Deploymentsnamn för embeddingar  
- Ytterligare Azure-konfiguration enligt `.env.example`

## Utvecklingsarbetsflöde

### Köra Jupyter Notebooks

Varje lektion innehåller flera Jupyter notebooks för olika ramverk:

1. **Starta Jupyter:**  
   ```bash
   jupyter notebook
   ```
  
2. **Navigera till en lektionskatalog** (t.ex. `01-intro-to-ai-agents/code_samples/`)

3. **Öppna och kör notebooks:**  
   - `*-semantic-kernel.ipynb` – Använder Semantic Kernel ramverk  
   - `*-autogen.ipynb` – Använder AutoGen ramverk  
   - `*-python-agent-framework.ipynb` – Använder Microsoft Agent Framework (Python)  
   - `*-dotnet-agent-framework.ipynb` – Använder Microsoft Agent Framework (.NET)  
   - `*-azureaiagent.ipynb` – Använder Azure AI Agent Service

### Arbeta med olika ramverk

**Semantic Kernel + GitHub Models:**  
- Gratisnivå tillgänglig med GitHub-konto  
- Bra för lärande och experiment  
- Filnamnsmönster: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**  
- Gratisnivå tillgänglig med GitHub-konto  
- Multi-agent orkestreringsmöjligheter  
- Filnamnsmönster: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**  
- Senaste ramverket från Microsoft  
- Finns för Python och .NET  
- Filnamnsmönster: `*-agent-framework.ipynb`

**Azure AI Agent Service:**  
- Kräver Azure-prenumeration  
- Produktionsklara funktioner  
- Filnamnsmönster: `*-azureaiagent.ipynb`

## Testinstruktioner

Detta är ett utbildningsrepository med exempel på kod snarare än produktionskod med automatiska tester. För att verifiera din installation och ändringar:

### Manuell testning

1. **Testa Python-miljön:**  
   ```bash
   python --version  # Bör vara 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```
  
2. **Testa notebook-exekvering:**  
   ```bash
   # Konvertera anteckningsbok till skript och kör (testar importer)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```
  
3. **Verifiera miljövariabler:**  
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```
  
### Köra individuella notebooks

Öppna notebooks i Jupyter och kör celler sekventiellt. Varje notebook är självständig och innehåller:  
- Import-satser  
- Konfigurationsladdning  
- Exempelagent-implementationer  
- Förväntade utdata i markdown-celler

## Kodstil

### Python-konventioner

- **Python-version:** 3.12+  
- **Kodstil:** Följ standarden PEP 8  
- **Notebooks:** Använd tydliga markdown-celler för förklaringar  
- **Imports:** Gruppera standardbibliotek, tredjepart, lokala imports

### Jupyter Notebook-konventioner

- Inkludera beskrivande markdown-celler före kodceller  
- Lägg till exempelutdata i notebooks som referens  
- Använd tydliga variabelnamn som matchar lektionskoncept  
- Håll notebook-körningen linjär (cell 1 → 2 → 3 …)

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
  
## Bygg och distribution

### Bygga dokumentation

Detta repository använder Markdown för dokumentationen:  
- README.md-filer i varje lektionsmapp  
- Huvudsaklig README.md i repositoryts rot  
- Automatiserat översättningssystem via GitHub Actions

### CI/CD-pipeline

Finns i `.github/workflows/`:

1. **co-op-translator.yml** – Automatisk översättning till 50+ språk  
2. **welcome-issue.yml** – Hälsar nya issue-skapare välkomna  
3. **welcome-pr.yml** – Hälsar nya pull requests välkomna

### Distribution

Detta är ett utbildningsrepository – ingen distributionsprocess. Användare:  
1. Forkar eller klonar repositoryt  
2. Kör notebooks lokalt eller i GitHub Codespaces  
3. Lär sig genom att modifiera och experimentera med exempel

## Riktlinjer för Pull Requests

### Innan inskickning

1. **Testa dina ändringar:**  
   - Kör berörda notebooks helt  
   - Bekräfta att alla celler kör utan fel  
   - Kontrollera att utdata är adekvata

2. **Dokumentationsuppdateringar:**  
   - Uppdatera README.md vid tillägg av nya koncept  
   - Lägg till kommentarer i notebooks vid komplex kod  
   - Säkerställ att markdown-celler förklarar innehållet

3. **Filändringar:**  
   - Undvik att committa `.env`-filer (använd `.env.example`)  
   - Committa inte `venv/` eller `__pycache__/`-kataloger  
   - Behåll notebook-utdata när de visar koncept  
   - Ta bort temporära filer och backup-notebooks (`*-backup.ipynb`)

### PR-titelformat

Använd beskrivande titlar:  
- `[Lesson-XX] Lägg till nytt exempel för <concept>`  
- `[Fix] Rätta skrivfel i lesson-XX README`  
- `[Update] Förbättra kodexempel i lesson-XX`  
- `[Docs] Uppdatera installationsinstruktioner`

### Obligatoriska kontroller

- Notebooks ska köras utan fel  
- README-filer ska vara tydliga och korrekta  
- Följ befintliga kodmönster i repositoryt  
- Behåll konsekvens med andra lektioner

## Ytterligare anmärkningar

### Vanliga fallgropar

1. **Python-version stämmer inte:**  
   - Säkerställ att Python 3.12+ används  
   - Vissa paket fungerar inte med äldre versioner  
   - Använd `python3 -m venv` för att explicit ange Python-version

2. **Miljövariabler:**  
   - Skapa alltid `.env` från `.env.example`  
   - Committa inte `.env` (finns i `.gitignore`)  
   - GitHub-token måste ha lämpliga behörigheter

3. **Paketkonflikter:**  
   - Använd en färsk virtuell miljö  
   - Installera från `requirements.txt` istället för enskilda paket  
   - Vissa notebooks kan kräva extra paket enligt markdown-celler

4. **Azure-tjänster:**  
   - Azure AI-tjänster kräver aktiv prenumeration  
   - Vissa funktioner är regionsspecifika  
   - Gratisnivåbegränsningar gäller för GitHub Models

### Inlärningsväg

Rekommenderad ordning på lektionerna:  
1. **00-course-setup** – Börja här för miljöinstallation  
2. **01-intro-to-ai-agents** – Förstå grunderna i AI-agenter  
3. **02-explore-agentic-frameworks** – Lär om olika ramverk  
4. **03-agentic-design-patterns** – Kärndesignmönster  
5. Fortsätt genom numrerade lektioner sekventiellt

### Ramverksval

Välj ramverk baserat på dina mål:  
- **Lärande/prototyping:** Semantic Kernel + GitHub Models (gratis)  
- **Multi-agent system:** AutoGen  
- **Senaste funktioner:** Microsoft Agent Framework (MAF)  
- **Produktionssättning:** Azure AI Agent Service

### Få hjälp

- Gå med i [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)  
- Granska lektions-README för specifika instruktioner  
- Läs huvudsakliga [README.md](./README.md) för kursöversikt  
- Se [Course Setup](./00-course-setup/README.md) för detaljerade installationsinstruktioner

### Bidra

Detta är ett öppet utbildningsprojekt. Bidrag är välkomna:  
- Förbättra kodexempel  
- Åtgärda stavfel eller fel  
- Lägg till förtydligande kommentarer  
- Föreslå nya lektionsämnen  
- Översätt till fler språk

Se [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) för aktuella behov.

## Projekt-specifik kontext

### Flerspråkigt stöd

Detta repository använder ett automatiserat översättningssystem:  
- Stöd för över 50 språk  
- Översättningar i `/translations/<lang-code>/` kataloger  
- GitHub Actions workflow hanterar översättningsuppdateringar  
- Källfiler är på engelska i repositoryts rot

### Lektionsstruktur

Varje lektion följer ett konsekvent mönster:  
1. Videominiatyr med länk  
2. Skrivet lektionsinnehåll (README.md)  
3. Kodexempel i flera ramverk  
4. Lärandemål och förkunskaper  
5. Extra lärresurser med länkar

### Namngivning av kodexempel

Format: `<lesson-number>-<framework-name>.ipynb`  
- `04-semantic-kernel.ipynb` – Lektion 4, Semantic Kernel  
- `07-autogen.ipynb` – Lektion 7, AutoGen  
- `14-python-agent-framework.ipynb` – Lektion 14, MAF Python  
- `14-dotnet-agent-framework.ipynb` – Lektion 14, MAF .NET

### Särskilda kataloger

- `translated_images/` – Lokalt översatta bilder för olika språk  
- `images/` – Originalbilder för engelskt innehåll  
- `.devcontainer/` – Konfiguration för VS Code utvecklingscontainer  
- `.github/` – GitHub Actions workflows och mallar

### Beroenden

Viktiga paket från `requirements.txt`:  
- `autogen-agentchat`, `autogen-core`, `autogen-ext` – AutoGen ramverk  
- `semantic-kernel` – Semantic Kernel ramverk  
- `agent-framework` – Microsoft Agent Framework  
- `azure-ai-inference`, `azure-ai-projects` – Azure AI-tjänster  
- `azure-search-documents` – Azure AI Search-integration  
- `chromadb` – Vektor-databas för RAG-exempel  
- `chainlit` – Chat UI-ramverk  
- `browser_use` – Browser-automation för agenter  
- `mcp[cli]` – Model Context Protocol-stöd  
- `mem0ai` – Minneshantering för agenter

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfriskrivning**:
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet, vänligen var medveten om att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på dess modersmål ska betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår till följd av användningen av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->