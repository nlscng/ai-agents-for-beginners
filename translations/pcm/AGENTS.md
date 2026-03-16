# AGENTS.md

## Project Overview

Dis repository get "AI Agents for Beginners" - na complete educational course wey dey teach everything wey person need sabi build AI Agents. Di course get over 15 lessons wey cover fundamentals, design patterns, frameworks, plus how to put AI agents for production deployment.

**Key Technologies:**
- Python 3.12+
- Jupyter Notebooks for interactive learning
- AI Frameworks: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Services: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (free tier available)

**Architecture:**
- Lesson-based structure (00-15+ directories)
- Each lesson get: README documentation, code samples (Jupyter notebooks), and pictures
- Multi-language support through automated translation system
- Multiple framework options per lesson (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Setup Commands

### Prerequisites
- Python 3.12 or above
- GitHub account (for GitHub Models - free tier)
- Azure subscription (optional, for Azure AI services)

### Initial Setup

1. **Clone or fork di repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # OR
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Create and activate Python virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # For Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # Make you edit .env wit your API keys and endpoints
   ```

### Required Environment Variables

For **GitHub Models (Free)**:
- `GITHUB_TOKEN` - Personal access token from GitHub

For **Azure AI Services** (optional):
- `PROJECT_ENDPOINT` - Microsoft Foundry project endpoint
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API key
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI endpoint URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Deployment name for chat model
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Deployment name for embeddings
- Additional Azure configuration as e dey for `.env.example`

## Development Workflow

### Running Jupyter Notebooks

Each lesson get plenty Jupyter notebooks for different frameworks:

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Go enter lesson directory** (for example, `01-intro-to-ai-agents/code_samples/`)

3. **Open and run notebooks:**
   - `*-semantic-kernel.ipynb` - Using Semantic Kernel framework
   - `*-autogen.ipynb` - Using AutoGen framework
   - `*-python-agent-framework.ipynb` - Using Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Using Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Using Azure AI Agent Service

### Working with Different Frameworks

**Semantic Kernel + GitHub Models:**
- Free tier dey with GitHub account
- Good for learning and testing
- File pattern: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Free tier dey with GitHub account
- Get multi-agent orchestration powers
- File pattern: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Latest framework from Microsoft
- Available for Python and .NET
- File pattern: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Need Azure subscription
- Features ready for production
- File pattern: `*-azureaiagent.ipynb`

## Testing Instructions

Dis one na educational repository with example code, no be production code wey get automated tests. To confirm say your setup and changes dey okay:

### Manual Testing

1. **Test Python environment:**
   ```bash
   python --version  # E suppose dey 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test notebook execution:**
   ```bash
   # Change notebook go script and run am (test say imports dey work)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Check environment variables:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Running Individual Notebooks

Open notebooks for Jupyter and run the cells one by one. Every notebook be self-contained and get:
- Import statements
- Configuration loading
- Example agent implementations
- Expected outputs inside markdown cells

## Code Style

### Python Conventions

- **Python Version:** 3.12+
- **Code Style:** Follow standard Python PEP 8 conventions
- **Notebooks:** Use clear markdown cells to explain stuff
- **Imports:** Group by standard library, third-party, local imports

### Jupyter Notebook Conventions

- Include clear markdown cells before code cells
- Add output samples inside notebooks for reference
- Use clear variable names wey go match lesson concepts
- Keep notebook execution order linear (cell 1 → 2 → 3...)

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

Dis repository use Markdown for documentation:
- README.md files for every lesson folder
- Main README.md for repository root
- Automated translation system with GitHub Actions

### CI/CD Pipeline

E dey for `.github/workflows/`:

1. **co-op-translator.yml** - Automatic translation for 50+ languages
2. **welcome-issue.yml** - Welcomes new issue creators
3. **welcome-pr.yml** - Welcomes new pull request contributors

### Deployment

Dis one na educational repository - no deployment process. Users:
1. Fork or clone the repository
2. Run notebooks locally or inside GitHub Codespaces
3. Learn by changing and experimenting with examples

## Pull Request Guidelines

### Before Submitting

1. **Test your changes:**
   - Run affected notebooks completely
   - Confirm all cells run without errors
   - Make sure outputs dey okay

2. **Documentation updates:**
   - Fix README.md if you add new concepts
   - Add comments in notebooks for complex code
   - Make sure markdown cells explain wetin dem try do

3. **File changes:**
   - No commit `.env` files (use `.env.example`)
   - No commit `venv/` or `__pycache__/` folders
   - Keep notebook outputs if e show concepts well
   - Remove temporary files and backup notebooks (`*-backup.ipynb`)

### PR Title Format

Use clear titles:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Correct typo for lesson-XX README`
- `[Update] Improve code sample for lesson-XX`
- `[Docs] Update setup instructions`

### Required Checks

- Notebooks must run without errors
- README files must clear and correct
- Follow code patterns wey dey repository
- Keep style consistent with other lessons

## Additional Notes

### Common Gotchas

1. **Python version wahala:**
   - Make sure you dey use Python 3.12+
   - Some packages no go work with old versions
   - Use `python3 -m venv` to specify Python version sharp sharp

2. **Environment variables:**
   - Always create `.env` from `.env.example`
   - No commit `.env` file (e dey `.gitignore`)
   - GitHub token need correct permissions

3. **Package conflicts:**
   - Use fresh virtual environment
   - Install from `requirements.txt` better than separate packages
   - Some notebooks fit need extra packages wey dem talk inside markdown cells

4. **Azure services:**
   - Azure AI services need active subscription
   - Some features fit depend on region
   - Free tier get limits for GitHub Models

### Learning Path

Recommended order to follow lessons:
1. **00-course-setup** - Start here for environment setup
2. **01-intro-to-ai-agents** - Understand AI agent basics
3. **02-explore-agentic-frameworks** - Learn about different frameworks
4. **03-agentic-design-patterns** - Core design patterns
5. Continue in sequence with numbered lessons

### Framework Selection

Choose framework based on wetin you want:
- **Learning/Prototyping:** Semantic Kernel + GitHub Models (free)
- **Multi-agent systems:** AutoGen
- **Latest features:** Microsoft Agent Framework (MAF)
- **Production deployment:** Azure AI Agent Service

### Getting Help

- Join di [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Check lesson README files for detailed guide
- See main [README.md](./README.md) for course overview
- Refer to [Course Setup](./00-course-setup/README.md) for full setup instructions

### Contributing

Dis one na open educational project. Contributions dey welcome:
- Improve code examples
- Fix typos or errors
- Add better comments
- Suggest new lesson topics
- Translate to more languages

Check [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) for current needs.

## Project-Specific Context

### Multi-Language Support

Dis repository get automated translation system:
- 50+ languages supported
- Translations dey inside `/translations/<lang-code>/` folders
- GitHub Actions workflow dey update translations
- Source files dey English at repository root

### Lesson Structure

Every lesson get di same pattern:
1. Video thumbnail with link
2. Written lesson content (README.md)
3. Code samples for many frameworks
4. Learning objectives and prerequisites
5. Extra learning resources linked

### Code Sample Naming

Format: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Lesson 4, Semantic Kernel
- `07-autogen.ipynb` - Lesson 7, AutoGen
- `14-python-agent-framework.ipynb` - Lesson 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lesson 14, MAF .NET

### Special Directories

- `translated_images/` - Localized images for translations
- `images/` - Original pictures for English content
- `.devcontainer/` - VS Code development container config
- `.github/` - GitHub Actions workflows and templates

### Dependencies

Key packages from `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen framework
- `semantic-kernel` - Semantic Kernel framework
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI services
- `azure-search-documents` - Azure AI Search integration
- `chromadb` - Vector database for RAG examples
- `chainlit` - Chat UI framework
- `browser_use` - Browser automation for agents
- `mcp[cli]` - Model Context Protocol support
- `mem0ai` - Memory management for agents

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Warning**:
Dis kain dokument don translate by AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator). As we dey try make am correct, abeg sabi say machine fit make mistake for translation. Di original document wey dey dia pesin language na di correct one. If na serious matter, better make person wey sabi human translation do am. We no go take blame if pesin no understand or if mistake show for dis translated version.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->