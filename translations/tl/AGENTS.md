# AGENTS.md

## Project Overview

Ang repository na ito ay naglalaman ng "AI Agents para sa mga Nagsisimula" - isang komprehensibong kursong pang-edukasyon na nagtuturo ng lahat ng kailangan para makabuo ng AI Agents. Ang kurso ay binubuo ng 15+ aralin na sumasaklaw sa mga pundasyon, mga disenyo ng pattern, mga framework, at production deployment ng mga AI agent.

**Pangunahing Teknolohiya:**
- Python 3.12+
- Jupyter Notebooks para sa interaktibong pag-aaral
- AI Frameworks: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Services: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (may libreng tier)

**Arkitektura:**
- Estruktura batay sa aralin (00-15+ na mga direktoryo)
- Bawat aralin ay naglalaman ng: README na dokumentasyon, mga halimbawa ng code (Jupyter notebooks), at mga larawan
- Suporta sa maraming wika sa pamamagitan ng automated translation system
- Maraming opsyon sa framework bawat aralin (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Setup Commands

### Prerequisites
- Python 3.12 o mas mataas
- GitHub account (para sa GitHub Models - libreng tier)
- Azure subscription (opsyonal, para sa Azure AI services)

### Initial Setup

1. **I-clone o i-fork ang repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # O
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Gumawa at i-activate ang Python virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Sa Windows: venv\Scripts\activate
   ```

3. **I-install ang mga dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **I-set up ang mga environment variables:**
   ```bash
   cp .env.example .env
   # I-edit ang .env gamit ang iyong mga API key at mga endpoint
   ```

### Kailangan na Environment Variables

Para sa **GitHub Models (Libre)**:
- `GITHUB_TOKEN` - Personal access token mula sa GitHub

Para sa **Azure AI Services** (opsyonal):
- `PROJECT_ENDPOINT` - Microsoft Foundry project endpoint
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API key
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI endpoint URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Pangalan ng deployment para sa chat model
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Pangalan ng deployment para sa embeddings
- Karagdagang Azure configuration tulad ng ipinapakita sa `.env.example`

## Development Workflow

### Pagpapatakbo ng Jupyter Notebooks

Bawat aralin ay naglalaman ng maraming Jupyter notebooks para sa iba't ibang mga framework:

1. **Simulan ang Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Mag-navigate sa direktoryo ng aralin** (halimbawa, `01-intro-to-ai-agents/code_samples/`)

3. **Buksan at patakbuhin ang mga notebooks:**
   - `*-semantic-kernel.ipynb` - Gumagamit ng Semantic Kernel framework
   - `*-autogen.ipynb` - Gumagamit ng AutoGen framework
   - `*-python-agent-framework.ipynb` - Gumagamit ng Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Gumagamit ng Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Gumagamit ng Azure AI Agent Service

### Paggamit ng Iba't ibang Frameworks

**Semantic Kernel + GitHub Models:**
- May libreng tier gamit ang GitHub account
- Magandang gamitin para sa pag-aaral at eksperimento
- Pattern ng file: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- May libreng tier gamit ang GitHub account
- Kakayahan para sa multi-agent orchestration
- Pattern ng file: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Pinakabagong framework mula sa Microsoft
- Available sa Python at .NET
- Pattern ng file: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Nangangailangan ng Azure subscription
- Handa para sa production na mga feature
- Pattern ng file: `*-azureaiagent.ipynb`

## Testing Instructions

Ito ay isang edukasyonal na repository na may mga halimbawa ng code sa halip na production code na may automated tests. Para mapatunayan ang iyong setup at mga pagbabago:

### Manual Testing

1. **Subukan ang Python environment:**
   ```bash
   python --version  # Dapat ay 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Subukan ang pagpapatakbo ng notebook:**
   ```bash
   # I-convert ang notebook sa script at patakbuhin (sinusubukan ang mga import)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Suriin ang mga environment variables:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Pagpatakbo ng Bawat Notebook

Buksan ang mga notebooks sa Jupyter at patakbuhin ang mga cell nang sunod-sunod. Ang bawat notebook ay self-contained at naglalaman ng:
- Mga import statement
- Pag-load ng configuration
- Mga halimbawa ng implementasyon ng agent
- Inaasahang output sa mga markdown cells

## Code Style

### Mga Kumbensiyon sa Python

- **Bersyon ng Python**: 3.12+
- **Estilo ng Code**: Sundin ang karaniwang Python PEP 8 na kumbensiyon
- **Mga Notebooks**: Gumamit ng malinaw na markdown cells para ipaliwanag ang mga konsepto
- **Imports**: Pangkatin ayon sa standard library, third-party, at local imports

### Kumbensiyon sa Jupyter Notebook

- Maglagay ng mga deskriptibong markdown cells bago ang mga code cells
- Magdagdag ng mga halimbawa ng output sa notebooks bilang sanggunian
- Gumamit ng malinaw na mga pangalan ng variable na tumutugma sa mga konsepto ng aralin
- Panatilihing linear ang order ng pagpapatakbo ng notebook (cell 1 → 2 → 3...)

### Organisasyon ng Files

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

### Pagbuo ng Dokumentasyon

Ang repository na ito ay gumagamit ng Markdown para sa dokumentasyon:
- Mga README.md file sa bawat folder ng aralin
- Pangunahing README.md sa root ng repository
- Automated translation system gamit ang GitHub Actions

### CI/CD Pipeline

Matatagpuan sa `.github/workflows/`:

1. **co-op-translator.yml** - Awtomatikong pagsasalin sa 50+ na mga wika
2. **welcome-issue.yml** - Pagsalubong sa mga bagong gumawa ng isyu
3. **welcome-pr.yml** - Pagsalubong sa mga bagong nag-contribute ng pull request

### Deployment

Ito ay isang edukasyonal na repository - walang proseso ng deployment. Mga user:
1. Mag-fork o mag-clone ng repository
2. Patakbuhin ang mga notebooks nang lokal o sa GitHub Codespaces
3. Matuto sa pamamagitan ng pag-modify at eksperimento sa mga halimbawa

## Pull Request Guidelines

### Bago Mag-submit

1. **Subukan ang mga pagbabago:**
   - Patakbuhin nang buo ang mga naapektuhang notebooks
   - Siguraduhing walang error sa pag-execute ng lahat ng cells
   - Tiyaking ang mga output ay angkop

2. **Pag-update ng Dokumentasyon:**
   - I-update ang README.md kung may idinagdag na bagong konsepto
   - Magdagdag ng mga komento sa mga notebooks para sa mas kumplikadong code
   - Siguraduhing ang markdown cells ay nagpapaliwanag ng layunin

3. **Mga pagbabago sa file:**
   - Iwasang i-commit ang mga `.env` files (gumamit ng `.env.example`)
   - Huwag i-commit ang `venv/` o `__pycache__/` na mga direktoryo
   - Panatilihin ang output ng notebook kapag ipinapakita ang mga konsepto
   - Alisin ang mga pansamantalang file at backup notebooks (`*-backup.ipynb`)

### Format ng PR Title

Gumamit ng deskriptibong mga pamagat:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Correct typo in lesson-XX README`
- `[Update] Improve code sample in lesson-XX`
- `[Docs] Update setup instructions`

### Kinakailangang Mga Check

- Dapat magpatakbo ang mga notebooks ng walang error
- Dapat malinaw at tumpak ang mga README files
- Sundin ang umiiral na mga pattern ng code sa repository
- Panatilihin ang pagkakatugma sa ibang mga aralin

## Additional Notes

### Mga Karaniwang Problema

1. **Hindi tugmang bersyon ng Python:**
   - Siguraduhing ginagamit ang Python 3.12+
   - Ang ilang mga pakete ay maaaring hindi gumana sa mas lumang bersyon
   - Gamitin ang `python3 -m venv` para tukuyin nang eksakto ang bersyon ng Python

2. **Environment variables:**
   - Laging gawin ang `.env` mula sa `.env.example`
   - Huwag i-commit ang `.env` file (nasa `.gitignore` ito)
   - Kailangan ng GitHub token ng tamang mga permiso

3. **Mga conflict sa package:**
   - Gumamit ng bagong virtual environment
   - Mag-install mula sa `requirements.txt` kaysa sa mga indibidwal na pakete
   - Ang ilang notebooks ay maaaring mangailangan ng karagdagang pakete na nabanggit sa kanilang mga markdown cells

4. **Azure services:**
   - Nangangailangan ang Azure AI services ng aktibong subscription
   - Ang ilang feature ay region-specific
   - May mga limitasyon ang libreng tier para sa GitHub Models

### Learning Path

Inirerekomendang mahigpit na pagsunod sa mga aralin:
1. **00-course-setup** - Simulan dito para sa setup ng environment
2. **01-intro-to-ai-agents** - Unawain ang mga pundasyon ng AI agent
3. **02-explore-agentic-frameworks** - Matutunan ang tungkol sa iba't ibang frameworks
4. **03-agentic-design-patterns** - Mga pangunahing disenyo na pattern
5. Ipagpatuloy ang sunud-sunod sa mga numbered lessons

### Pagpili ng Framework

Pumili ng framework batay sa iyong mga layunin:
- **Pag-aaral/Prototyping**: Semantic Kernel + GitHub Models (libre)
- **Multi-agent systems**: AutoGen
- **Pinakabagong feature**: Microsoft Agent Framework (MAF)
- **Production deployment**: Azure AI Agent Service

### Pagkuha ng Tulong

- Sumali sa [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Suriin ang mga README files ng aralin para sa partikular na gabay
- Tingnan ang pangunahing [README.md](./README.md) para sa overview ng kurso
- Sumangguni sa [Course Setup](./00-course-setup/README.md) para sa detalyadong instruksyon sa setup

### Pag-aambag

Ito ay isang bukas na proyektong pang-edukasyon. Malugod ang mga kontribusyon:
- Pagbutihin ang mga halimbawa ng code
- Itama ang mga typo o error
- Magdagdag ng mga paliwanag na komento
- Magmungkahi ng mga bagong paksa sa aralin
- Isalin sa iba pang mga wika

Tingnan ang [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) para sa kasalukuyang mga pangangailangan.

## Project-Specific Context

### Suporta sa Maramihang Wika

Ang repository na ito ay gumagamit ng automated translation system:
- Suporta sa 50+ na mga wika
- Mga pagsasalin sa `/translations/<lang-code>/` na mga direktoryo
- Pinapatakbo ng GitHub Actions workflow ang mga update sa pagsasalin
- Ang mga source file ay nasa Ingles sa root ng repository

### Estruktura ng Aralin

Bawat aralin ay sumusunod sa isang pare-parehong pattern:
1. Video thumbnail na may link
2. Nakalathalang nilalaman ng aralin (README.md)
3. Mga halimbawa ng code sa maraming framework
4. Mga layunin ng pag-aaral at mga kinakailangan
5. Mga dagdag na mapagkukunan ng pag-aaral na naka-link

### Pagpapangalan ng Code Sample

Format: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Aralin 4, Semantic Kernel
- `07-autogen.ipynb` - Aralin 7, AutoGen
- `14-python-agent-framework.ipynb` - Aralin 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Aralin 14, MAF .NET

### Espesyal na Mga Direktoryo

- `translated_images/` - Mga larawang lokal na isinalin para sa pagsasalin
- `images/` - Orihinal na mga larawan para sa nilalaman sa Ingles
- `.devcontainer/` - VS Code development container configuration
- `.github/` - Mga workflow at template ng GitHub Actions

### Mga Dependencies

Pangunahing mga pakete mula sa `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen framework
- `semantic-kernel` - Semantic Kernel framework
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI services
- `azure-search-documents` - Azure AI Search integration
- `chromadb` - Vector database para sa RAG na mga halimbawa
- `chainlit` - Chat UI framework
- `browser_use` - Browser automation para sa mga agent
- `mcp[cli]` - Suporta para sa Model Context Protocol
- `mem0ai` - Pamamahala ng memorya para sa mga agent

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Paunawa**:  
Ang dokumentong ito ay isinalin gamit ang AI translation service na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagamat nagsusumikap kaming maging tumpak, pakatandaan na ang mga awtomatikong salin ay maaaring maglaman ng mga pagkakamali o di-tumpak na impormasyon. Ang orihinal na dokumento sa kanyang katutubong wika ang dapat ituring na opisyal na sanggunian. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasaling-tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na maaaring magmula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->