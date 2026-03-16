# AGENTS.md

## Project Overview

ဒီ repository မှာ "AI Agents for Beginners" ဆိုတဲ့ AI Agents တည်ဆောက်ဖို့ လိုအပ်တဲ့ အကြောင်းအရာအားလုံး ကို သင်ကြားပေးတဲ့ ပညာရေး အသုံးချမှု အပြည့်အစုံ ပါဝင်ပါတယ်။ ၎င်း သင်တန်းတွင် အခြေခံ သင်ခန်းစာ ၁၅ ကျော် ပါဝင်ပြီး AI agents များ၏ အခြေခံအကြောင်းအရာများ၊ ဒီဇိုင်းပုံစံများ၊ framework များနှင့် စက်ရုပ်ထုတ်လုပ်မှုအဆင့်များကို ဖုံးကွယ်ပြသထားသည်။

**Key Technologies:**
- Python 3.12+
- interactive သင်ကြားရန် Jupyter Notebooks
- AI Framework များ: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Services: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (အခမဲ့ အဆင့် ရရှိနိုင်)

**Architecture:**
- သင်ခန်းစာအလိုက် ဖွဲ့စည်းမှု (00-15+ ဖိုလ်ဒါများ)
- သင်ခန်းစာတိုင်းတွင် ပါရှိသည်- README စာရွက်, ကုဒ်နမူနာများ (Jupyter notebooks), ပုံများ
- ဘာသာစကား များအလိုက် အလိုအလျောက် ပြောင်းလဲပေးသည့် အစီအစဉ်ပါဝင်မှု
- သင်ခန်းစာအားလုံးကို framework များ သုံးမျိုး (Semantic Kernel, AutoGen, Azure AI Agent Service) ဖြင့် အသုံးပြုနိုင်ခြင်း

## Setup Commands

### Prerequisites
- Python 3.12 သို့မဟုတ် အထက်
- GitHub အကောင့် (GitHub Models အတွက် အခမဲ့ အဆင့်)
- Azure subscription (optional, Azure AI services အတွက်)

### Initial Setup

1. **Repository ကို clone သို့မဟုတ် fork လုပ်ပါ:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # သို့မဟုတ်
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Python virtual environment ဖန်တီးပြီး ဖွင့်ပါ:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Windows တွင်: venv\Scripts\activate
   ```

3. **လိုအပ်သော package များ ထည့်သွင်းပါ:**
   ```bash
   pip install -r requirements.txt
   ```

4. **ပတ်ဝန်းကျင်ตัวแปรများ ပြင်ဆင်ပါ:**
   ```bash
   cp .env.example .env
   # သင့် API key များနှင့် endpoints များဖြင့် .env ကိုတည်းဖြတ်ပါ
   ```

### Required Environment Variables

GitHub Models (အခမဲ့) အတွက်:
- `GITHUB_TOKEN` - GitHub မှ ကိုယ်ပိုင် access token

Azure AI Services အတွက် (optional):
- `PROJECT_ENDPOINT` - Microsoft Foundry project endpoint
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API key
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI endpoint URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - စကားပြော model ထည့်သွင်းမှု အမည်
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - embedding deployment အမည်
- `.env.example` တွင် ပြထားသည့် Azure configuration အပိုများ

## Development Workflow

### Jupyter Notebooks ကို တက်ရောက်ခြင်း

သင်ခန်းစာတိုင်းတွင် framework များအလိုက် Jupyter notebook များပါရှိပြီး:

1. **Jupyter ကို စတင်ပါ:**
   ```bash
   jupyter notebook
   ```

2. **သင်ခန်းစာ ဖိုလ်ဒါသို့ သွားပါ** (ဥပမာ `01-intro-to-ai-agents/code_samples/`)

3. **Notebook များကို ဖွင့်ပြီး အသုံးပြုပါ:**
   - `*-semantic-kernel.ipynb` - Semantic Kernel framework အသုံးပြုခြင်း
   - `*-autogen.ipynb` - AutoGen framework အသုံးပြုခြင်း
   - `*-python-agent-framework.ipynb` - Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Azure AI Agent Service

### Framework များ ဖြင့် လုပ်ဆောင်ခြင်း

**Semantic Kernel + GitHub Models:**
- GitHub အကောင့်ဖြင့် အခမဲ့ အဆင့် ရရှိနိုင်
- သင်ယူခြင်းနှင့် စမ်းသပ်မှုအတွက် သင့်တော်
- ဖိုင် pattern: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- GitHub အကောင့်ဖြင့် အခမဲ့ အဆင့် ရရှိနိုင်
- Multi-agent orchestration အတွက် သင့်တော်
- ဖိုင် pattern: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Microsoft မှ ထုတ်လုပ်သည့် နောက်ဆုံး framework
- Python နှင့် .NET မှာ အသုံးပြုနိုင်
- ဖိုင် pattern: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Azure subscription လိုအပ်
- Production အဆင့် အသုံးပြုနိုင်သော features ပါရှိ
- ဖိုင် pattern: `*-azureaiagent.ipynb`

## Testing Instructions

ဒီ repository သည် ပညာရေးအတွက် ဥပမာကုဒ်များ ပါရှိသဖြင့် စက်ထုတ်ကုဒ်အတိုင်း automated test များ မပါဝင်ပါ။ သင့် စနစ်နှင့် ပြင်ဆင်မှုများကို စစ်ဆေးရန်:

### ကိုယ်ပိုင် စစ်ဆေးခြင်း

1. **Python ပတ်ဝန်းကျင် စစ်ဆေးပါ:**
   ```bash
   python --version  # 3.12 သို့အထက် ဖြစ်သင့်သည်။
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Notebook အတတ်ပညာ စမ်းသပ်ခြင်း:**
   ```bash
   # နိုတ်ဘုတ်ကို စကရစ်ပ်သို့ ပြောင်းပြီး ထည့်သွင်းပြီး စမ်းသပ်ပါ (တင်သွင်းမှုများကို စစ်ဆေးသည်)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **ပတ်ဝန်းကျင် variable များ စစ်ဆေးပါ:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### တစ်ခုချင်းစီ Notebook များ စမ်းသပ်ခြင်း

Jupyter တွင် notebooks ဖွင့်ပြီး အစီအစဉ်အတိုင်း cell များကို လည်ပတ်စေပါ။ Notebook တစ်ခုစီတွင်ပါဝင်သည် -
- import statements
- configuration load လုပ်ခြင်း
- agent အပေါ် မူတည်သော နမူနာများ
- markdown cells တွင် ရလာသော အဖြေများ

## Code Style

### Python စံနှုန်း

- **Python Version**: 3.12+
- **Code Style**: Python PEP 8 စံ
- **Notebook များ**: မျိုးချောင်းသော markdown cells ဖြင့် အကြောင်းအရာ ရှင်းလင်းရေးသားမှု
- **Imports**: စံ library, third-party, ဒေသဆိုင်ရာ imports သို့ ခွဲခြားထားခြင်း

### Jupyter Notebook စံနစ်

- code cell မတိုင်မီ ရှင်းလင်းသော markdown cells ထည့်သွင်းပါ
- notebook များတွင်အထွက်အတွက် ဥပမာများ ထည့်ပါ
- သင်ခန်းစာအပေါ် သပ်ရပ်သော variable နာမည်များကို သုံးပါ
- Notebook cell execute အဆင့်သည် စဉ်လိုက် ဖြစ်စေရန် (cell ၁ → ၂ → ၃...)

### ဖိုင် စီမံခန့်ခွဲမှု

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

### Documentation တည်ဆောက်ခြင်း

ဒီ repository မှာ Markdown ဖြင့် စာရွက်စာတမ်းများရေးသားသည် -
- သင်ခန်းစာ folder တစ်ခုစီအား README.md ဖိုင်များ
- repository အခြေတွင် Main README.md
- GitHub Actions ဖြင့် automated translation system

### CI/CD Pipeline

`.github/workflows/` ဖိုလ်ဒါတွင်ရှိသည်:

1. **co-op-translator.yml** - ဘာသာစကား ၅၀ ကျော်သို့ အလိုအလျောက် ဘာသာပြန်ခြင်း
2. **welcome-issue.yml** - issue တင်သူများကို ကြိုဆိုခြင်း
3. **welcome-pr.yml** - pull request တင်သူများကို ကြိုဆိုခြင်း

### Deployment

ဒီ repository သည် ပညာရေးအတွက် ဖြစ်သောကြောင့် deployment လုပ်ငန်းစဉ် မရှိပါ။ အသုံးပြုသူများသည်:
1. Fork သို့မဟုတ် clone ယူခြင်း
2. ပန်းချီ၏ notebook များကို တိုင်းပြည်၌ သို့မဟုတ် GitHub Codespaces တွင် အလုပ်လုပ်ခြင်း
3. ဥပမာ များကို ပြင်ဆင်၍ သင်ယူခြင်း

## Pull Request Guidelines

### တင်သည့်အရင်

1. **ပြင်ဆင်မှုများ စမ်းသပ်ပါ:**
   - သက်ဆိုင်ရာ notebooks အားလုံး အလုပ်လုပ်ခြင်း
   - cell များ error မရှိစွာ လည်ပတ်ခြင်း
   - ထွက်ရှိလာသော အဖြေများ သင့်တော်မှု စစ်ဆေးခြင်း

2. **စာရွက်စာတမ်း ပြင်ဆင်မှု:**
   - README.md တွင် အသစ်ထည့်မည့်အကြောင်းအရာများ ထည့်သွင်းခြင်း
   - code ရှုပ်ထွေးမှုများ အတွက် notebook တွင် မှတ်ချက်များ ထည့်သွင်းခြင်း
   - markdown cells အား အကျဉ်းချုပ် ရေးသားခြင်း

3. **ဖိုင် ပြင်ဆင်မှုများ:**
   - `.env` ဖိုင် မတင်ပါနှင့် (`.env.example` ကို သုံးပါ)
   - `venv/` သို့မဟုတ် `__pycache__/` ဖိုလ်ဒါ မတင်ပါနှင့်
   - သင်ခန်းစာ အကြောင်းအရာ ဖော်ပြတဲ့ notebook outputs များ ထားပါ
   - ယာယီဖိုင် သို့မဟုတ် backup notebooks (`*-backup.ipynb`) များ ဖယ်ရှားပါ

### PR Title ပုံစံ

ဖော်ပြချက်ရှင်းပြသောခေါင်းစဉ်များကို သုံးပါ:
- `[Lesson-XX] <concept> အတွက် နမူနာအသစ် ဖြည့်စွက်ခြင်း`
- `[Fix] lesson-XX README အတွင်း အမှား ပြင်ဆင်ခြင်း`
- `[Update] lesson-XX အတွက် ကုဒ် နမူနာ မြှင့်တင်ခြင်း`
- `[Docs] setup အသုံးပြုနည်း ပြင်ဆင်ခြင်း`

### လိုအပ်သော စစ်ဆေးမှုများ

- notebooks များ error မရှိစွာ လည်ပတ်ရမည်
- README ဖိုင်များ ပြတ်သားသာလွန်ရမည်
- repository အောက်ရှိ ကုဒ် စံနစ်နှင့် ကိုက်ညီရမည်
- သင်ခန်းစာများနှင့် ယှဉ်တင်ဆောင်ရန်တွက် ကိုက်ညီမှုရှိရမည်

## Additional Notes

### အထူး သတိပြုရန်အချက်များ

1. **Python ဗားရှင်း မကိုက်ညီခြင်း:**
   - Python 3.12+ ကို သုံးရန် သေချာစေပါ
   - အဟောင်းဗားရှင်းများနှင့် အချို့ package မအလုပ်လုပ်နိုင်ပါ
   - python3 -m venv ဖြင့် Python ဗားရှင်း ထောက်ပံ့မှု ပြုလုပ်ပါ

2. **ပတ်ဝန်းကျင် variable များ:**
   - `.env.example` မှ `.env` ဖိုင် ဖန်တီးထားပါ
   - `.env` ကို commit မလုပ်ပါ (အဆိုပါဖိုင် `.gitignore` တွင်ပါသည်)
   - GitHub token သည် အထောက်အပံ့ ဖြစ်စေရန် လိုအပ်သော အခွင့်အရေးရှိရမည်

3. **Package conflicts များ:**
   - အသစ်သော virtual environment သုံးပါ
   - package များကို တစ်ခုချင်း installs မှမလုပ်ဘဲ `requirements.txt` မှ install လုပ်ပါ
   - notebook တချို့တွင် markdown cells တွင် ပြောထားသည့် အပိုင်း packages လိုအပ်နိုင်သည်

4. **Azure services:**
   - Azure AI services အတွက် subscription တက်ရောက်ထားရမည်
   - အချို့ features များက ဒေသအလိုက် ကန့်သတ်ထားသည်
   - GitHub Models အတွက် free tier ကန့်သတ်ချက်များ ရှိသည်

### သင်ယူဖို့လမ်းညွှန်

သင်ခန်းစာများအား စဉ်လိုက် လေ့လာရန် အကြံပြုသည် -
1. **00-course-setup** - ပတ်ဝန်းကျင် စတင်အတွက်
2. **01-intro-to-ai-agents** - AI agent များ အခြေခံ နားလည်ခြင်း
3. **02-explore-agentic-frameworks** - framework များ လေ့လာခြင်း
4. **03-agentic-design-patterns** - အခြေခံ ဒီဇိုင်း ပုံစံများ
5. အနောက်စဉ်အတိုင်း ယိုးဆောင်ပါ

### Framework ရွေးချယ်မှု

ပန်းတိုင်အပေါ် မူတည်ပါ -
- **သင်ယူမှု / prototype**: Semantic Kernel + GitHub Models (အခမဲ့)
- **Multi-agent system များ**: AutoGen
- **နောက်ဆုံး features များ**: Microsoft Agent Framework (MAF)
- **ထုတ်လုပ်မှု အဆင့်**: Azure AI Agent Service

### အကူအညီ ရယူရန်

- [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord) တွင် တက်ရောက်ပါ
- သင်ခန်းစာ README files ကို သုံးသပ်ပါ
- [README.md](./README.md) မှာ သင်တန်းအနှစ်ချုပ် ကြည့်ပါ
- [Course Setup](./00-course-setup/README.md) မှ setup အသေးစိတ် အကြောင်းအရာ ကြည့်ပါ

### မိတ္တူပေးခြင်း

ဒီဟာ သင်ကြားပေးသည့် ပရောဂျက်ဖြစ်ပါသည်။ အကူအညီ သို့မဟုတ် ပြုပြင်ထောက်ပံ့မှုများ လက်ခံပါသည်:
- ကုဒ် နမူနာများ တိုးတက်စေရန်
- အမှားများ ပြင်ဆင်ရန်
- မှတ်ချက်များ ထည့်သွင်းရန်
- သင်ခန်းစာ အသစ်များ အကြံပြုရန်
- ဘာသာစကားအသစ်များသို့ ဘာသာပြန်ရန်

လတ်တလော လိုအပ်ချက်များအတွက် [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) ကြည့်ပါ။

## Project-Specific Context

### ဘာသာစကား များစွာ ထောက်ခံမှု

ဒီ repository သည် အလိုအလျောက် ဘာသာပြန် စနစ် အသုံးပြုသည် -
- ဘာသာစကား ၅၀ ကျော် ပံ့ပိုးမှုရှိ
- `/translations/<lang-code>/` ဖိုလ်ဒါတွင် ဘာသာပြန်ဖိုင်များရှိ
- GitHub Actions workflow မှ ဘာသာပြန်သတင်းအချက်အလက်များ အပ်ဒိတ်လုပ်သည်
- ရင်းမြစ်ဖိုင်များသည် English တွင် repository အခြေတွင်ရှိ

### သင်ခန်းစာ ဖွဲ့စည်းပုံ

သင်ခန်းစာတိုင်းသည် အတူတူသောပုံစံများကြားတွင်ရှိသည် -
1. ဗီဒီယို thumbnail နှင့် လင့်ခ်
2. စာရွက်စာတမ်း (README.md)
3. Framework များ အလိုက် ကုဒ် နမူနာများ
4. သင်ယူရမည့် ရည်မှန်းချက်များနှင့်လိုအပ်ချက်များ
5. ပိုပြီး သင်ယူနိုင်မည့် ရင်းမြစ်များ လင့်ခ်

### ကုဒ် နမူနာ အမည်ပုံစံ

ပုံစံ: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - သင်ခန်းစာ ၄၊ Semantic Kernel
- `07-autogen.ipynb` - သင်ခန်းစာ ၇၊ AutoGen
- `14-python-agent-framework.ipynb` - သင်ခန်းစာ ၁၄၊ MAF Python
- `14-dotnet-agent-framework.ipynb` - သင်ခန်းစာ ၁၄၊ MAF .NET

### အထူးဖိုလ်ဒါများ

- `translated_images/` - ဘာသာပြန်ထားသော ပုံများရိှသည်
- `images/` - အင်္ဂလိပ်အကြောင်းအရာ ပုံများ
- `.devcontainer/` - VS Code development container configuration
- `.github/` - GitHub Actions workflow များ နှင့် template များ

### လိုအပ်ချက်များ

`requirements.txt` မှ အဓိက package များ -
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen framework များ
- `semantic-kernel` - Semantic Kernel framework
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI services
- `azure-search-documents` - Azure AI Search ပေါင်းစပ်မှု
- `chromadb` - RAG examples များအတွက် vector database
- `chainlit` - စကားပြော UI framework
- `browser_use` - Agent များအတွက် browser automation
- `mcp[cli]` - Model Context Protocol ထောက်ပံ့မှု
- `mem0ai` - agent များအတွက် memory management

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**လူကြီးမင်းအတည်ပြုချက်**  
ဤစာတမ်းကို AI ဘာသာပြန်ဝန်ဆောင်မှုဖြစ်သော [Co-op Translator](https://github.com/Azure/co-op-translator) ဖြင့် ဘာသာပြန်ထားပါသည်။ ကျွန်ုပ်တို့မှ တိကျမှုအတွက်ကြိုးစားနေသော်လည်း၊ အလိုအလျောက် ဘာသာပြန်မှုများတွင် အမှားများ သို့မဟုတ် မှားယွင်းချက်များ ရှိနိုင်ကြောင်း သတိပြုပါရန်အလားအလာရှိသည်။ မူရင်းစာတမ်းကို အခြေခံဘာသာစကားဖြင့်သာ ထိပ်တန်းအချက်အလက်အဖြစ် ယူဆသင့်ပါသည်။ အရေးကြီးသောအချက်အလက်များအတွက် အတတ်ပညာရှင် လူသား ဘာသာပြန်သူမှ ဘာသာပြန်ထားမှုကို အကြံပြုပါသည်။ ဤဘာသာပြန်ချက်ကို အသုံးပြုမှုကြောင့် ဖြစ်ပေါ်နိုင်သော နားလည်မှုမမှန်မှုများ သို့မဟုတ် မှားယွင်းချက်များအတွက် ကျွန်ုပ်တို့မှ တာဝန်မယူပါ။
<!-- CO-OP TRANSLATOR DISCLAIMER END -->