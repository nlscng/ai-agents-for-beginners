# AGENTS.md

## ਪ੍ਰਾਜੈਕਟ ਓਵerview

ਇਹ ਰਿਪੋਜ਼ੀਟਰੀ "ਨਵੀਆਂ ਲਈ AI ਏਜੰਟ" ਸ਼ਾਮਲ ਹੈ - ਇੱਕ ਵਿਸਤ੍ਰਿਤ ਸਿੱਖਿਆ ਕੋਰਸ ਜੋ AI ਏਜੰਟ ਬਣਾਉਣ ਲਈ ਜ਼ਰੂਰੀ ਹਰ ਚੀਜ਼ ਸਿਖਾਉਂਦਾ ਹੈ। ਕੋਰਸ ਵਿੱਚ 15+ ਪਾਠ ਹਨ ਜੋ ਮੂਲ ਸਰੂਤੀਆਂ, ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ, ਫਰੇਮਵਰਕ, ਅਤੇ AI ਏਜੰਟਾਂ ਦੀ ਉਤਪਾਦਨ ਸਥਾਪਨਾ ਨੂੰ ਕਵਰ ਕਰਦੇ ਹਨ।

**ਮੁੱਖ ਤਕਨਾਲੋਜੀਜ਼:**
- Python 3.12+
- ਇੰਟਰਐਕਟਿਵ ਸਿੱਖਿਆ ਲਈ Jupyter ਨੋਟਬੁੱਕਾਂ
- AI ਫਰੇਮਵਰਕਸ: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI ਸੇਵਾਵਾਂ: Microsoft Foundry, Azure AI Agent Service
- GitHub ਮਾਡਲ ਮਾਰਕੀਟਪਲੇਸ (ਮਫ਼ਤ ਟੀਅਰ ਉਪਲਬਧ)

**ਆਰਕੀਟੈਕਚਰ:**
- ਪਾਠ ਆਧਾਰਿਤ ਢਾਂਚਾ (00-15+ ਡਾਇਰੈਕਟਰੀਜ਼)
- ਹਰ ਪਾਠ ਵਿੱਚ: README ਦਸਤਾਵੇਜ਼, ਕੋਡ ਨਮੂਨੇ (Jupyter ਨੋਟਬੁੱਕ), ਅਤੇ ਤਸਵੀਰਾਂ
- ਆਟੋਮੈਟਿਕ ਅਨੁਵਾਦ ਪ੍ਰਣਾਲੀ ਰਾਹੀਂ ਬਹੁ-ਭਾਸ਼ਾਈ ਸਮਰਥਨ
- ਹਰ ਪਾਠ ਵਿੱਚ ਕਈ ਫਰੇਮਵਰਕ ਵਿਕਲਪ (Semantic Kernel, AutoGen, Azure AI Agent Service)

## ਸੈਟਅਪ ਕਮਾਂਡਜ਼

### ਲੋੜੀਂਦੇ ਚੀਜ਼ਾਂ
- Python 3.12 ਜਾਂ ਉੱਪਰ
- GitHub ਖਾਤਾ (GitHub ਮਾਡਲ ਲਈ - ਮਫ਼ਤ ਟੀਅਰ)
- Azure ਸਬਸਕ੍ਰਿਪਸ਼ਨ (ਵਿਕਲਪਿਕ, Azure AI ਸੇਵਾਵਾਂ ਲਈ)

### ਸ਼ੁਰੂਆਤੀ ਸੈਟਅਪ

1. **ਰਿਪੋਜ਼ੀਟਰੀ ਨੂੰ ਕਲੋਨ ਜਾਂ ਫੋਰਕ ਕਰੋ:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ਜਾਂ
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Python ਵਰਚੁਅਲ ਇਨਵਾਇਰਨਮੈਂਟ ਬਣਾਓ ਅਤੇ ਐਕਟੀਵੇਟ ਕਰੋ:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # ਵਿਂਡੋਜ਼ 'ਤੇ: venv\Scripts\activate
   ```

3. **ਨਿਰਭਰਤਾਵਾਂ ਸਥਾਪਿਤ ਕਰੋ:**
   ```bash
   pip install -r requirements.txt
   ```

4. **ਇਨਵਾਇਰਨਮੈਂਟ ਵੈਰੀਏਬਲ ਸੈੱਟ ਕਰੋ:**
   ```bash
   cp .env.example .env
   # ਆਪਣੇ API ਕੁੰਜੀਆਂ ਅਤੇ ਐਂਡਪੌਇੰਟਸ ਨਾਲ .env ਨੂੰ ਸੰਪਾਦਿਤ ਕਰੋ
   ```

### ਲੋੜੀਂਦੇ ਇਨਵਾਇਰਨਮੈਂਟ ਵੈਰੀਏਬਲ

**GitHub ਮਾਡਲ (ਮਫ਼ਤ):**
- `GITHUB_TOKEN` - GitHub ਤੋਂ ਪਰਸਨਲ ਐਕਸੈਸ ਟੋਕਨ

**Azure AI ਸੇਵਾਵਾਂ** (ਵਿਕਲਪਿਕ):
- `PROJECT_ENDPOINT` - Microsoft Foundry ਪ੍ਰਾਜੈਕਟ ਐਂਡਪੋਇੰਟ
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API ਚਾਬੀ
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI ਐਂਡਪੋਇੰਟ URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - ਚੈਟ ਮਾਡਲ ਲਈ ਡਿਪਲੋਇਮੈਂਟ ਨਾਮ
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - ਐਂਬੈਡਿੰਗਜ਼ ਲਈ ਡਿਪਲੋਇਮੈਂਟ ਨਾਮ
- `.env.example` ਵਿੱਚ ਦਰਸਾਈ ਗਈ ਵਾਧੂ Azure ਵਿਵਸਥਾ

## ਵਿਕਾਸ ਕਾਰਜਪ੍ਰਵਾਹ

### Jupyter ਨੋਟਬੁੱਕ ਚਲਾਉਣਾ

ਹਰ ਪਾਠ ਵਿੱਚ ਕਈ ਫਰੇਮਵਰਕਸ ਲਈ Jupyter ਨੋਟਬੁੱਕ ਹਨ:

1. **Jupyter ਸ਼ੁਰੂ ਕਰੋ:**
   ```bash
   jupyter notebook
   ```

2. **ਕਿਸੇ ਪਾਠ ਡਾਇਰੈਕਟਰੀ ਵਿੱਚ ਜਾਓ** (ਉਦਾਹਰਨ ਵਜੋਂ `01-intro-to-ai-agents/code_samples/`)

3. **ਨੋਟਬੁੱਕ ਖੋਲ੍ਹੋ ਅਤੇ ਚਲਾਓ:**
   - `*-semantic-kernel.ipynb` - Semantic Kernel ਫਰੇਮਵਰਕ ਵਰਤਦੇ ਹੋਏ
   - `*-autogen.ipynb` - AutoGen ਫਰੇਮਵਰਕ ਵਰਤਦੇ ਹੋਏ
   - `*-python-agent-framework.ipynb` - Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Azure AI Agent Service

### ਵੱਖ-ਵੱਖ ਫਰੇਮਵਰਕ ਨਾਲ ਕੰਮ ਕਰਨਾ

**Semantic Kernel + GitHub ਮਾਡਲ:**
- GitHub ਖਾਤੇ ਨਾਲ ਮਫ਼ਤ ਟੀਅਰ ਉਪਲਬਧ
- ਸਿੱਖਣ ਅਤੇ ਪ੍ਰਯੋਗ ਲਈ ਚੰਗਾ
- ਫਾਇਲ ਪੈਟਰਨ: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub ਮਾਡਲ:**
- GitHub ਖਾਤੇ ਨਾਲ ਮਫ਼ਤ ਟੀਅਰ ਉਪਲਬਧ
- ਬਹੁ ਏਜੰਟ ਨਿਰਦੇਸ਼ਕ ਸਮਰਥਾ
- ਫਾਇਲ ਪੈਟਰਨ: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Microsoft ਤੋਂ ਤਾਜ਼ਾ ਫਰੇਮਵਰਕ
- Python ਅਤੇ .NET ਦੋਨੋਂ ਵਿੱਚ ਉਪਲਬਧ
- ਫਾਇਲ ਪੈਟਰਨ: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Azure ਸਬਸਕ੍ਰਿਪਸ਼ਨ ਦੀ ਲੋੜ
- ਉਤਪਾਦਨ-ਤਈ ਤਿਆਰ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ
- ਫਾਇਲ ਪੈਟਰਨ: `*-azureaiagent.ipynb`

## ਟੈਸਟਿੰਗ ਨਿਰਦੇਸ਼

ਇਹ ਇੱਕ ਸਿੱਖਣ ਵਾਲੀ ਰਿਪੋਜ਼ੀਟਰੀ ਹੈ ਜਿਸ ਵਿੱਚ ਉਦਾਹਰਣ ਕੋਡ ਹੈ, ਉਤਪਾਦਨ ਕੋਡ ਨਹੀਂ; ਕਿਸੇ ਆਟੋਮੈਟਿਕ ਟੈਸਟਾਂ ਦੀ ਗੱਲ ਨਹੀਂ। ਆਪਣਾ ਸੈਟਅਪ ਅਤੇ ਬਦਲਾਵ ਜਾਂਚਣ ਵਾਸਤੇ:

### ਮੈਨੁਅਲ ਟੈਸਟਿੰਗ

1. **Python ਇਨਵਾਇਰਨਮੈਂਟ ਟੈਸਟ ਕਰੋ:**
   ```bash
   python --version  # 3.12+ ਹੋਣਾ ਚਾਹੀਦਾ ਹੈ
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **ਨੋਟਬੁੱਕ ਚਲਾਉਣਾ ਟੈਸਟ ਕਰੋ:**
   ```bash
   # ਨੋਟਬੁੱਕ ਨੂੰ ਸਕ੍ਰਿਪਟ ਵਿੱਚ ਬਦਲੋ ਅਤੇ ਚਲਾਓ (ਟੈਸਟ ਇੰਪੋਰਟ)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **ਇਨਵਾਇਰਨਮੈਂਟ ਵੈਰੀਏਬਲ ਜਾਂਚੋ:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### ਅਲੱਗ-ਅਲੱਗ ਨੋਟਬੁੱਕ ਚਲਾਉਣਾ

Jupyter ਵਿੱਚ ਨੋਟਬੁੱਕ ਖੋਲ੍ਹੋ ਅਤੇ ਕ੍ਰਮਵਾਰ ਸੈਲ ਚਲਾਉ। ਹਰ ਨੋਟਬੁੱਕ ਸਵੈ ਸੰਚਾਲਿਤ ਹੈ ਅਤੇ ਸ਼ਾਮਲ ਕਰਦਾ ਹੈ:
- ਇੰਪੋਰਟ ਵਾਕਾਂਸ਼
- ਵਿਵਸਥਾ ਲੋਡ ਕਰਨਾ
- ਉਦਾਹਰਣ ਏਜੰਟ ਲਾਗੂ ਕਰਨ
- ਉਮੀਦ ਕੀਤੇ ਫਲ ਨੋਟਬੁੱਕ ਦੇ ਮਾਰਕਡਾਊਨ ਸੈਲ ਵਿੱਚ

## ਕੋਡ ਸ਼ੈਲੀ

### Python ਰੀਤੀਆਂ

- **Python ਵਰਜ਼ਨ**: 3.12+
- **ਕੋਡ ਸ਼ੈਲੀ**: ਮਿਆਰੀ Python PEP 8 ਦੀ ਪਾਲਨਾ ਕਰੋ
- **ਨੋਟਬੁੱਕ**: ਧਾਰਣਾ ਸਮਝਾਉਣ ਲਈ ਸਾਫ਼ ਮਾਰਕਡਾਊਨ ਸੈਲ ਵਰਤੋਂ
- **ਇੰਪੋਰਟ**: ਮਿਆਰੀ ਲਾਇਬ੍ਰੇਰੀ, ਤੀਜੀ-ਪੱਖੀ, ਸਥਾਨਕ ਆਯਾਤਾਂ ਦੌਰਾਨ ਸਮੂਹ ਬਣਾਉ

### Jupyter ਨੋਟਬੁੱਕ ਰੀਤੀਆਂ

- ਕੋਡ ਸੈਲ ਤੋਂ ਪਹਿਲਾਂ ਵੇਰਣਾਤਮਕ ਮਾਰਕਡਾਊਨ ਸੈਲ ਸ਼ਾਮਲ ਕਰੋ
- ਸੰਦਰਭ ਲਈ ਨੋਟਬੁੱਕ ਵਿੱਚ ਨਤੀਜੇ ਸ਼ਾਮਲ ਕਰੋ
- ਪਾਠ ਧਾਰਣਾ ਨਾਲ ਮੇਲ ਖਾਂਦੇ ਸਾਫ਼ ਵੈਰੀਏਬਲ ਨਾਂ ਵਰਤੋਂ
- ਨੋਟਬੁੱਕ ਚਲਾਉਣ ਲਈ ਕ੍ਰਮਵਾਰ ਢੰਗ ਨਾਲ (ਸੈਲ 1 → 2 → 3…)

### ਫਾਈਲ ਸੰਗਠਨ

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

## ਬਿਲਡ ਅਤੇ ਡਿਪਲੋਇਮੈਂਟ

### ਡਾਕੂਮੈਂਟੇਸ਼ਨ ਬਣਾਉਣਾ

ਇਹ ਰਿਪੋਜ਼ੀਟਰੀ ਡਾਕੂਮੈਂਟੇਸ਼ਨ ਲਈ Markdown ਵਰਤਦੀ ਹੈ:
- ਹਰ ਪਾਠ ਫੋਲਡਰ ਵਿੱਚ README.md ਫਾਇਲਾਂ
- ਰਿਪੋਜ਼ੀਟਰੀ ਦੇ ਜੜ ਵਿਚ ਮੁੱਖ README.md
- GitHub ਐਕਸ਼ਨਾਂ ਰਾਹੀਂ ਆਟੋਮੈਟਿਕ ਅਨੁਵਾਦ ਪ੍ਰਣਾਲੀ

### CI/CD ਪਾਈਪਲਾਈਨ

`.github/workflows/` ਵਿੱਚ:

1. **co-op-translator.yml** - 50+ ਭਾਸ਼ਾਵਾਂ ਵਿੱਚ ਆਟੋਮੈਟਿਕ ਅਨੁਵਾਦ
2. **welcome-issue.yml** - ਨਵੇਂ ਮੁੱਦੇ ਬਣਾਉਣ ਵਾਲਿਆਂ ਦਾ ਸਵਾਗਤ
3. **welcome-pr.yml** - ਨਵੇਂ ਪੁੱਲ ਰਿਕਵੇਸਟ ਦਾਤਾ ਦਾ ਸਵਾਗਤ

### ਡਿਪਲੋਇਮੈਂਟ

ਇਹ ਸਿੱਖਣ ਵਾਲੀ ਰਿਪੋਜ਼ੀਟਰੀ ਹੈ - ਕੋਈ ਡਿਪਲੋਇਮੈਂਟ ਪ੍ਰਕਿਰਿਆ ਨਹੀਂ। ਯੂਜ਼ਰ:
1. ਰਿਪੋਜ਼ੀਟਰੀ ਨੂੰ ਫੋਰਕ ਜਾਂ ਕਲੋਨ ਕਰੋ
2. ਨੋਟਬੁੱਕ ਨੂੰ ਲੋਕਲ ਜਾਂ GitHub ਕੋਡਸਪੇਸ ਵਿੱਚ ਚਲਾਓ
3. ਨਮੂਨਿਆਂ ਨਾਲ ਤਬਦੀਲ ਕਰਕੇ ਅਤੇ ਪ੍ਰਯੋਗ ਕਰਕੇ ਸਿੱਖੋ

## ਪੁੱਲ ਰਿਕਵੇਸਟ ਦਿਸ਼ਾ-ਨਿਰਦੇਸ਼

### ਸਬਮਿਟ ਕਰਨ ਤੋਂ ਪਹਿਲਾਂ

1. **ਆਪਣੇ ਬਦਲਾਅ ਦੀ ਜਾਂਚ ਕਰੋ:**
   - ਪ੍ਰਭਾਵਿਤ ਨੋਟਬੁੱਕ ਨੂੰ ਪੂਰੀ ਤਰ੍ਹਾਂ ਚਲਾਓ
   - ਸਾਰੇ ਸੈਲ ਬਿਨਾਂ ਗਲਤੀ ਦੇ ਚਲਣ ਯੋਗ ਹੋਣ
   - ਨਤੀਜੇ ਢੰਗ ਨਾਲ ਹਨ ਇਹ ਚੈੱਕ ਕਰੋ

2. **ਡਾਕੂਮੈਂਟੇਸ਼ਨ ਅੱਪਡੇਟ:**
   - ਜੇ ਨਵੇਂ ਧਾਰਣਾ ਜੋੜ ਰਹੇ ਹੋ ਤਾਂ README.md ਨੂੰ ਅੱਪਡੇਟ ਕਰੋ
   - ਕੁਝ ਔਖਾ ਕੋਡ ਹੋਵੇ ਤਾਂ ਨੋਟਬੁੱਕ ਵਿੱਚ ਟਿੱਪਣੀਆਂ ਜੋੜੋ
   - ਮਾਰਕਡਾਊਨ ਸੈਲ ਵਿਚ ਵਜ੍ਹਾ ਸਪਸ਼ਟ ਕਰੋ

3. **ਫਾਈਲ ਬਦਲਾਵ:**
   - `.env` ਫਾਈਲ ਨਾ ਜੋੜੋ (ਸਦਾ `.env.example` ਵਰਤੋ)
   - `venv/` ਜਾਂ `__pycache__/` ਡਾਇਰੈਕਟਰੀਆਂ ਕਮਿੱਟ ਨਾ ਕਰੋ
   - ਜਦ ਨੋਟਬੁੱਕ ਵਿਚ ਵਜ੍ਹਾ ਦਰਸਾਉਂਦੇ ਨਤੀਜੇ ਹਨ ਤਾਂ ਇਨ੍ਹਾਂ ਨੂੰ ਸੁਰੱਖਿਅਤ ਕਰੋ
   - ਅਸਥਾਈ ਫਾਈਲਾਂ ਅਤੇ ਬੈਕਅਪ ਨੋਟਬੁੱਕ (`*-backup.ipynb`) ਹਟਾਓ

### PR ਸ਼ੀਰਸ਼ਕ ਫਾਰਮੈਟ

ਸਪੱਸ਼ਟ ਸਿਰਲੇਖ ਵਰਤੋ:
- `[Lesson-XX] <ਧਾਰਣਾ> ਲਈ ਨਵਾਂ ਉਦਾਹਰਣ ਜੋੜੋ`
- `[Fix] ਪਾਠ-XX README ਵਿੱਚ ਟਾਈਪੋ ਸਹੀ ਕਰੋ`
- `[Update] ਪਾਠ-XX ਵਿੱਚ ਕੋਡ ਨਮੂਨਾ ਸੁਧਾਰੋ`
- `[Docs] ਸੈਟਅਪ ਹਦਾਇਤਾਂ ਅੱਪਡੇਟ ਕਰੋ`

### ਲੋੜੀਂਦੇ ਜਾਂਚ

- ਨੋਟਬੁੱਕ ਬਿਨਾਂ ਗਲਤੀ ਚਲਣੇ ਚਾਹੀਦੇ ਹਨ
- README ਫਾਈਲਾਂ ਸਪੱਸ਼ਟ ਅਤੇ ਸਹੀ ਹੋਣ
- ਮੌਜੂਦਾ ਕੋਡ ਪੈਟਰਨ ਫਾਲੋ ਕਰੋ
- ਹੋਰ ਪਾਠਾਂ ਨਾਲ ਇੱਕਸਾਰਤਾ ਬਣਾਈ ਰੱਖੋ

## ਵਾਧੂ ਨੋਟਸ

### ਆਮ ਮੁਸ਼ਕਿਲਾਂ

1. **Python ਵਰਜ਼ਨ ਗ਼ਲਤ:**
   - ਯਕੀਨੀ ਬਣਾਓ ਕਿ Python 3.12+ ਵਰਤ ਰਹੇ ਹੋ
   - ਕੁਝ ਪੈਕੇਜ ਪੁਰਾਣੇ ਵਰਜ਼ਨਾਂ ਤੌਂ ਕੰਮ ਨਹੀਂ ਕਰਦੇ
   - Python ਵਰਜ਼ਨ ਦਰਸਾਉਣ ਲਈ `python3 -m venv` ਵਰਤੋਂ

2. **ਇਨਵਾਇਰਨਮੈਂਟ ਵੈਰੀਏਬਲ:**
   - ਹਮੇਸ਼ਾ `.env.example` ਤੋਂ `.env` ਬਣਾਓ
   - `.env` ਨੂੰ ਕਮਿੱਟ ਨਾ ਕਰੋ (ਇਹ `.gitignore` ਵਿੱਚ ਹੈ)
   - GitHub ਟੋਕਨ ਦੇ ਲਈ ਢੰਗ ਦੀ ādhikāra ਚਾਹੀਦੇ

3. **ਪੈਕੇਜ ਟਕਰਾਅ:**
   - ਨਵਾਂ ਵਰਚੁਅਲ ਇਨਵਾਇਰਨਮੈਂਟ ਬਣਾਓ
   - ਇੰਡਿਵਿਡਯੂਅਲ ਬਜਾਏ `requirements.txt` ਤੋਂ ਇੰਸਟਾਲ ਕਰੋ
   - ਕੁਝ ਨੋਟਬੁੱਕ ਵਿੱਚ ਵਾਧੂ ਪੈਕੇਜ ਦੀ ਲੋੜ ਹੋ ਸਕਦੀ ਹੈ ਜੋ ਮਾਰਕਡਾਊਨ ਸੈਲਾਂ ਵਿੱਚ ਦੱਸਿਆ ਗਿਆ

4. **Azure ਸੇਵਾਵਾਂ:**
   - Azure AI ਸੇਵਾਵਾਂ ਲਈ ਚਾਲੂ ਸਬਸਕ੍ਰਿਪਸ਼ਨ ਜ਼ਰੂਰੀ
   - ਕੁਝ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਖੇਤਰ ਦੇ ਮੁਤਾਬਕ ਹੁੰਦੀਆਂ ਹਨ
   - GitHub ਮਾਡਲ ਲਈ ਮਫ਼ਤ ਟੀਅਰ ਦੀਆਂ ਹੱਦਾਂ ਹਨ

### ਸਿੱਖਣ ਦਾ ਰਸਤਾ

ਸੁਝਾਏ ਗਏ ਲੜੀਵਾਰ ਪਾਠ:
1. **00-course-setup** - ਇਥੇ ਸੈਟਅਪ ਸ਼ੁਰੂ ਕਰੋ
2. **01-intro-to-ai-agents** - AI ਏਜੰਟ ਦੀ ਬੁਨਿਆਦੀ ਜਾਣਕਾਰੀ ਪ੍ਰਾਪਤ ਕਰੋ
3. **02-explore-agentic-frameworks** - ਵੱਖ-ਵੱਖ ਫਰੇਮਵਰਕ ਬਾਰੇ ਜਾਣੋ
4. **03-agentic-design-patterns** - ਮੁੱਖ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਸਿੱਖੋ
5. ਅੰਕਿਤ ਪਾਠਾਂ ਨੂੰ ਲੜੀਵਾਰ ਜਾਰੀ ਰੱਖੋ

### ਫਰੇਮਵਰਕ ਚੋਣ

ਆਪਣੇ ਲੱਕੜ-ਲੱਛੇ ਅਨੁਸਾਰ ਚੁਣੋ:
- **ਸਿੱਖਣਾ/ਪ੍ਰੋਟੋਟਾਈਪਿੰਗ**: Semantic Kernel + GitHub ਮਾਡਲ (ਮਫ਼ਤ)
- **ਬਹੁ ਏਜੰਟ ਸਿਸਟਮ**: AutoGen
- **ਤਾਜ਼ਾ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ**: Microsoft Agent Framework (MAF)
- **ਉਤਪਾਦਨ ਡਿਪਲੋਇਮੈਂਟ**: Azure AI Agent Service

### ਮਦਦ ਲੈਣ ਲਈ

- [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord) ਵਿੱਚ ਸ਼ਾਮਿਲ ਹੋਵੋ
- ਹਰ ਪਾਠ ਦੇ README ਫਾਈਲਾਂ ਵਿੱਚ ਨਿਰਦੇਸ਼ ਦੇਖੋ
- ਮੁੱਖ [README.md](./README.md) ਵਿੱਚ ਕੋਰਸ ਓਵerview ਵੇਖੋ
- [Course Setup](./00-course-setup/README.md) ਵਿੱਚ ਵਿਸਤ੍ਰਿਤ ਸੈਟਅਪ ਹਦਾਇਤਾਂ ਵੇਖੋ

### ਯੋਗਦਾਨ

ਇਹ ਇੱਕ ਖੁੱਲ੍ਹਾ ਸਿੱਖਿਆ ਪ੍ਰਾਜੈਕਟ ਹੈ। ਯੋਗਦਾਨ ਸਵਾਗਤ ਹੈ:
- ਕੋਡ ਉਦਾਹਰਣ ਸੁਧਾਰੋ
- ਟਾਈਪੋ ਜਾਂ ਗਲਤੀਆਂ ਦੁਰੁਸਤ ਕਰੋ
- ਸਪਸ਼ਟੀਕਰਨ ਲਈ ਟਿੱਪਣੀਆਂ ਜੋੜੋ
- ਨਵੇਂ ਪਾਠ ਵਿਸ਼ੇ ਸੁਝਾਅ ਦਿਓ
- ਹੋਰ ਭਾਸ਼ਾਵਾਂ ਵਿੱਚ ਅਨੁਵਾਦ ਕਰੋ

ਮੌਜੂਦਾ ਲੋੜਾਂ ਲਈ [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) ਵੇਖੋ।

## ਪ੍ਰਾਜੈਕਟ-ਵਿਸ਼ੇਸ਼ ਸੰਦਰਭ

### ਬਹੁ-ਭਾਸ਼ਾਈ ਸਮਰਥਨ

ਇਹ ਰਿਪੋਜ਼ੀਟਰੀ ਆਟੋਮੈਟਿਕ ਅਨੁਵਾਦ ਪ੍ਰਣਾਲੀ ਵਰਤਦੀ ਹੈ:
- 50+ ਭਾਸ਼ਾਵਾਂ ਲਈ ਸਮਰਥਿਤ
- `/translations/<lang-code>/` ਡਾਇਰੈਕਟਰੀਜ਼ ਵਿੱਚ ਅਨੁਵਾਦ
- GitHub Actions ਵਰਕਫਲੋ ਅਨੁਵਾਦ ਅੱਪਡੇਟ ਸਾਂਭਦਾ ਹੈ
- ਸੋਰਸ ਫਾਇਲਾਂ ਅੰਗ੍ਰੇਜ਼ੀ ਵਿੱਚ ਰਿਪੋਜ਼ੀਟਰੀ ਜੜ੍ਹ ਵਿੱਚ ਹਨ

### ਪਾਠ ਦਾ ਢਾਂਚਾ

ਹਰ ਪਾਠ ਇੱਕ ਸਥਿਰ ਪੈਟਰਨ ਫਾਲੋ ਕਰਦਾ ਹੈ:
1. ਲਿੰਕ ਨਾਲ ਵੀਡੀਓ ਥੰਬਨੇਲ
2. ਲਿਖਤ ਪਾਠ ਸਮੱਗਰੀ (README.md)
3. ਕਈ ਫਰੇਮਵਰਕਸ ਵਿੱਚ ਕੋਡ ਨਮੂਨੇ
4. ਸਿੱਖਣ ਦੇ ਲੱਛੇ ਅਤੇ ਲੋੜੀਂਦੇ ਪਹਿਲੂ
5. ਵਾਧੂ ਸਿੱਖਣ ਸਰੋਤ ਲਿੰਕ ਆਦਿ

### ਕੋਡ ਨਮੂਨਾ ਨਾਂਵਾਂ

ਫਾਰਮੈਟ: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - ਪਾਠ 4, Semantic Kernel
- `07-autogen.ipynb` - ਪਾਠ 7, AutoGen
- `14-python-agent-framework.ipynb` - ਪਾਠ 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - ਪਾਠ 14, MAF .NET

### ਵਿਸ਼ੇਸ਼ ਡਾਇਰੈਕਟਰੀਜ਼

- `translated_images/` - ਅਨੁਵਾਦ ਲਈ ਸਥਾਨਕ ਤਸਵੀਰਾਂ
- `images/` - ਅੰਗ੍ਰੇਜ਼ੀ ਸਮੱਗਰੀ ਲਈ ਅਸਲੀ ਤਸਵੀਰਾਂ
- `.devcontainer/` - VS ਕੋਡ ਵਿਕਾਸ ਕੰਟੇਨਰ ਵਿਵਸਥਾ
- `.github/` - GitHub ਐਕਸ਼ਨ ਵਰਕਫਲੋ ਅਤੇ ਟੈਮਪਲੇਟ

### ਨਿਰਭਰਤਾਵਾਂ

`requirements.txt` ਵਿੱਚ ਮੁੱਖ ਪੈਕੇਜ:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen ਫਰੇਮਵਰਕ
- `semantic-kernel` - Semantic Kernel ਫਰੇਮਵਰਕ
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI ਸੇਵਾਵਾਂ
- `azure-search-documents` - Azure AI ਖੋਜ ਇੰਟੀਗ੍ਰੇਸ਼ਨ
- `chromadb` - RAG ਉਦਾਹਰਣ ਲਈ ਵੈਕਟਰ ਡੇਟਾਬੇਸ
- `chainlit` - ਚੈਟ UI ਫਰੇਮਵਰਕ
- `browser_use` - ਏਜੰਟਾਂ ਲਈ ਬਰਾਊਜ਼ਰ ਆਟੋਮੇਸ਼ਨ
- `mcp[cli]` - ਮਾਡਲ ਕਾਂਟੈਕਸਟ ਪ੍ਰੋਟੋਕਾਲ ਸਮਰਥਨ
- `mem0ai` - ਏਜੰਟਾਂ ਲਈ ਯਾਦਾਸ਼ਤ ਪ੍ਰਬੰਧਨ

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**ਅਸਵੀਕਾਰ**:  
ਇਸ ਦਸਤਾਵੇਜ਼ ਦਾ ਅਨੁਵਾਦ ਏਆਈ ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀਤਾ ਲਈ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਵਿੱਚ ਰੱਖੋ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸਪਸ਼ਟਤਾਵਾਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼ ਇਸ ਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਪ੍ਰਮਾਣਿਕ ਸ੍ਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਜਰੂਰੀ ਮਾਹਿਤੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫ਼ਾਰਿਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਨਾਲ ਉੱਪਜਣ ਵਾਲੀਆਂ ਕੋਈ ਵੀ ਗਲਤ ਫਹਿਮੀਆਂ ਜਾਂ ਭਰਮ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾੰ।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->