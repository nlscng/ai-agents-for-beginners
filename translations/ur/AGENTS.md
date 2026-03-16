# AGENTS.md

## منصوبے کا جائزہ

یہ ریپوزیٹری "AI Agents for Beginners" پر مشتمل ہے - ایک جامع تعلیمی کورس جو AI ایجنٹس بنانے کے لیے درکار تمام چیزیں سکھاتا ہے۔ کورس میں 15+ اسباق شامل ہیں جو بنیادی تصورات، ڈیزائن پیٹرنز، فریم ورکس، اور AI ایجنٹس کی پروڈکشن ڈپلائمنٹ کا احاطہ کرتے ہیں۔

**Key Technologies:**
- Python 3.12+
- Jupyter Notebooks for interactive learning
- AI Frameworks: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Services: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (free tier available)

**Architecture:**
- Lesson-based structure (00-15+ directories)
- Each lesson contains: README documentation, code samples (Jupyter notebooks), and images
- Multi-language support via automated translation system
- Multiple framework options per lesson (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Setup Commands

### ضروریات
- Python 3.12 یا اس سے جدید
- GitHub اکاؤنٹ (GitHub Models کے لیے - مفت ٹئیر)
- Azure سبسکرپشن (اختیاری، Azure AI سروسز کے لیے)

### ابتدائی ترتیب

1. **ریپوزیٹری کلون یا فورک کریں:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # یا
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Python ورچوئل اینوائرنمنٹ بنائیں اور فعال کریں:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # ونڈوز پر: venv\Scripts\activate
   ```

3. **انحصارات انسٹال کریں:**
   ```bash
   pip install -r requirements.txt
   ```

4. **ماحول کے متغیرات مرتب کریں:**
   ```bash
   cp .env.example .env
   # .env فائل کو اپنی API کلیدوں اور اینڈپوائنٹس کے ساتھ ترمیم کریں
   ```

### مطلوبہ ماحول کے متغیرات

برائے **GitHub Models (Free)**:
- `GITHUB_TOKEN` - GitHub سے ذاتی رسائی ٹوکن

برائے **Azure AI Services** (اختیاری):
- `PROJECT_ENDPOINT` - Microsoft Foundry پروجیکٹ اینڈ پوائنٹ
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API کی
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI اینڈ پوائنٹ URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - چیٹ ماڈل کے لیے ڈپلائمنٹ نام
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - ایمبیڈنگ کے لیے ڈپلائمنٹ نام
- اضافی Azure کنفیگریشن `.env.example` میں دکھائی گئی ہے

## Development Workflow

### Jupyter Notebooks چلانا

ہر سبق میں مختلف فریم ورکس کے لیے متعدد Jupyter نوٹ بکس شامل ہیں:

1. **Jupyter شروع کریں:**
   ```bash
   jupyter notebook
   ```

2. **سبق ڈائریکٹری میں نیویگیٹ کریں** (مثلاً `01-intro-to-ai-agents/code_samples/`)

3. **نوٹ بکس کھولیں اور چلائیں:**
   - `*-semantic-kernel.ipynb` - Semantic Kernel فریم ورک استعمال کرتے ہوئے
   - `*-autogen.ipynb` - AutoGen فریم ورک استعمال کرتے ہوئے
   - `*-python-agent-framework.ipynb` - Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Azure AI Agent Service استعمال کرتے ہوئے

### مختلف فریم ورکس کے ساتھ کام کرنا

**Semantic Kernel + GitHub Models:**
- GitHub اکاؤنٹ کے ساتھ مفت ٹئیر دستیاب
- سیکھنے اور تجربہ کرنے کے لیے موزوں
- فائل پیٹرن: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- GitHub اکاؤنٹ کے ساتھ مفت ٹئیر دستیاب
- ملٹی-ایجنٹ آركیسٹریشن کی صلاحیتیں
- فائل پیٹرن: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Microsoft کا تازہ ترین فریم ورک
- Python اور .NET میں دستیاب
- فائل پیٹرن: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Azure سبسکرپشن درکار ہے
- پروڈکشن-ریڈی خصوصیات
- فائل پیٹرن: `*-azureaiagent.ipynb`

## ٹیسٹنگ کی ہدایات

یہ ایک تعلیمی ریپوزیٹری ہے جس میں پروڈکشن کے خودکار ٹیسٹس کی بجائے مثال کے کوڈ شامل ہیں۔ اپنی سیٹ اپ اور تبدیلیوں کی تصدیق کے لیے:

### دستی ٹیسٹنگ

1. **Python ماحول کی جانچ کریں:**
   ```bash
   python --version  # 3.12+ ہونا چاہیے
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **نوٹ بک ایکزیکیوشن کی جانچ کریں:**
   ```bash
   # نوٹ بک کو اسکرپٹ میں تبدیل کریں اور چلائیں (ٹیسٹ امپورٹس)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **ماحول کے متغیرات کی تصدیق کریں:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### انفرادی نوٹ بکس چلانا

Jupyter میں نوٹ بکس کھولیں اور سیلز کو ترتیب وار چلائیں۔ ہر نوٹ بک خود مختار ہے اور اس میں شامل ہیں:
- Import statements
- Configuration loading
- Example agent implementations
- متوقع آؤٹ پٹس مارک ڈاون سیلز میں

## کوڈ اسٹائل

### Python کنونشنز

- **Python Version**: 3.12+
- **Code Style**: معیاری Python PEP 8 کنونشنز پر عمل کریں
- **Notebooks**: تصورات کی وضاحت کے لیے واضح مارک ڈاون سیلز استعمال کریں
- **Imports**: standard library, third-party, local imports کے حساب سے گروپ کریں

### Jupyter Notebook کنونشنز

- کوڈ سیلز سے پہلے تشریحی مارک ڈاون سیلز شامل کریں
- حوالہ کے لیے نوٹ بکس میں آؤٹ پٹ مثالیں شامل کریں
- واضح ویریبل نام استعمال کریں جو سبق کے تصورات سے میل کھاتے ہوں
- نوٹ بک ایکزیکیوشن آرڈر کو خطی رکھیں (cell 1 → 2 → 3...)

### فائل کی ترتیب

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

### دستاویزات بنانا

یہ ریپوزیٹری ڈاکیومنٹیشن کے لیے مارک ڈاؤن استعمال کرتی ہے:
- ہر سبق کے فولڈر میں README.md فائلیں
- ریپوزیٹری روٹ پر مرکزی README.md
- خودکار ترجمہ سسٹم GitHub Actions کے ذریعے

### CI/CD پائپ لائن

موقع واقع ہے `.github/workflows/` میں:

1. **co-op-translator.yml** - 50+ زبانوں میں خودکار ترجمہ
2. **welcome-issue.yml** - نئے issue بنانے والوں کو خوش آمدید کہتا ہے
3. **welcome-pr.yml** - نئے pull request contributors کو خوش آمدید کہتا ہے

### ڈپلائمنٹ

یہ ایک تعلیمی ریپوزیٹری ہے - کوئی ڈپلائمنٹ پروسس نہیں۔ صارفین:
1. ریپوزیٹری کو فورک یا کلون کریں
2. نوٹ بکس مقامی طور پر یا GitHub Codespaces میں چلائیں
3. مثالوں میں ترمیم اور تجربہ کرکے سیکھیں

## پل ریکویسٹ رہنما اصول

### جمع کروانے سے پہلے

1. **اپنی تبدیلیوں کا ٹیسٹ کریں:**
   - متاثرہ نوٹ بکس کو مکمل طور پر چلائیں
   - تصدیق کریں کہ تمام سیلز بغیر ایرر کے چلتی ہیں
   - چیک کریں کہ آؤٹ پٹس مناسب ہیں

2. **دستاویزات کی اپ ڈیٹس:**
   - اگر نئے تصورات شامل کر رہے ہیں تو README.md اپ ڈیٹ کریں
   - پیچیدہ کوڈ کے لیے نوٹ بکس میں کمنٹس شامل کریں
   - یقینی بنائیں کہ مارک ڈاون سیلز مقصد کی وضاحت کریں

3. **فائل تبدیلیاں:**
   - `.env` فائلیں کمٹ کرنے سے گریز کریں (`.env.example` استعمال کریں)
   - `venv/` یا `__pycache__/` ڈائریکٹریز کمٹ نہ کریں
   - جب وہ تصورات کی وضاحت کریں تو نوٹ بک آؤٹ پٹس رکھیں
   - عارضی فائلیں اور بیک اپ نوٹ بکس (`*-backup.ipynb`) ہٹا دیں

### PR عنوانی شکل

وضاحتی عنوانات استعمال کریں:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Correct typo in lesson-XX README`
- `[Update] Improve code sample in lesson-XX`
- `[Docs] Update setup instructions`

### ضروری چیکس

- نوٹ بکس بغیر ایرر کے چلنے چاہئیں
- README فائلیں واضح اور درست ہونی چاہئیں
- ریپوزیٹری میں موجود دیگر اسباق کے کوڈ پیٹرنز کی پیروی کریں
- دیگر اسباق کے ساتھ مطابقت برقرار رکھیں

## اضافی نوٹس

### عام مسائل

1. **Python ورژن کا میل نہ کھانا:**
   - یقینی بنائیں کہ Python 3.12+ استعمال ہو رہا ہے
   - کچھ پیکیجز پرانے ورژنز کے ساتھ کام نہیں کر سکتے
   - Python ورژن مخصوص کرنے کے لیے `python3 -m venv` استعمال کریں

2. **ماحول کے متغیرات:**
   - ہمیشہ `.env` کو `.env.example` سے بنائیں
   - `.env` فائل کمٹ نہ کریں (یہ `.gitignore` میں ہے)
   - GitHub ٹوکن کو مناسب اجازتیں درکار ہوتی ہیں

3. **پیکیج تنازعات:**
   - تازہ ورچوئل اینوائرنمنٹ استعمال کریں
   - انفرادی پیکیجز کی بجائے `requirements.txt` سے انسٹال کریں
   - کچھ نوٹ بکس کو اضافی پیکیجز کی ضرورت ہو سکتی ہے جو ان کے مارک ڈاؤن سیلز میں ذکر ہیں

4. **Azure سروسز:**
   - Azure AI سروسز کے لیے فعال سبسکرپشن درکار ہے
   - کچھ خصوصیات خطہ مخصوص ہو سکتی ہیں
   - GitHub Models پر مفت ٹئیر کی حدود لاگو ہوتی ہیں

### سیکھنے کا راستہ

سبقوں کے ذریعے تجویز کردہ ترتیب:
1. **00-course-setup** - ماحول کی ترتیب کے لیے یہاں سے شروع کریں
2. **01-intro-to-ai-agents** - AI ایجنٹس کے بنیادی اصول سمجھیں
3. **02-explore-agentic-frameworks** - مختلف فریم ورکس کے بارے میں جانیں
4. **03-agentic-design-patterns** - بنیادی ڈیزائن پیٹرنز
5. نمبر والے اسباق کو تسلسل کے ساتھ پڑھتے رہیں

### فریم ورک کا انتخاب

اپنے مقاصد کی بنیاد پر فریم ورک منتخب کریں:
- **Learning/Prototyping**: Semantic Kernel + GitHub Models (free)
- **Multi-agent systems**: AutoGen
- **Latest features**: Microsoft Agent Framework (MAF)
- **Production deployment**: Azure AI Agent Service

### مدد حاصل کرنا

- شمولیت کریں [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- مخصوص رہنمائی کے لیے سبق کے README فائلز دیکھیں
- کورس جائزے کے لیے مرکزی [README.md](./README.md) دیکھیں
- تفصیلی سیٹ اپ ہدایات کے لیے رجوع کریں [Course Setup](./00-course-setup/README.md)

### تعاون

یہ ایک اوپن تعلیمی پراجیکٹ ہے۔ تعاون کا خیرمقدم ہے:
- کوڈ کی مثالوں کو بہتر بنائیں
- ٹائپوز یا غلطیوں کو درست کریں
- وضاحتی کمنٹس شامل کریں
- نئے سبق کے موضوعات تجویز کریں
- اضافی زبانوں میں ترجمہ کریں

موجودہ ضروریات کے لیے دیکھیں [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues)۔

## پراجیکٹ مخصوص سیاق و سباق

### کثیر لسانی معاونت

یہ ریپوزیٹری خود کار ترجمہ سسٹم استعمال کرتی ہے:
- 50+ زبانیں معاونت یافتہ ہیں
- ترجمے `/translations/<lang-code>/` ڈائریکٹریز میں موجود ہیں
- GitHub Actions ورک فلو ترجمہ اپڈیٹس کو ہینڈل کرتا ہے
- سورس فائلیں انگریزی میں ریپوزیٹری روٹ پر ہیں

### سبق کی ساخت

ہر سبق ایک مستقل پیٹرن پر عمل کرتا ہے:
1. ویڈیو تھمب نیل کے ساتھ لنک
2. تحریری سبق کا مواد (README.md)
3. مختلف فریم ورکس میں کوڈ سیمپلز
4. سیکھنے کے مقاصد اور پیش درکاریاں
5. اضافی سیکھنے کے وسائل لنک کیے گئے

### کوڈ نمونہ نام رکھنے کا طریقہ

فارمیٹ: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - سبق 4، Semantic Kernel
- `07-autogen.ipynb` - سبق 7، AutoGen
- `14-python-agent-framework.ipynb` - سبق 14، MAF Python
- `14-dotnet-agent-framework.ipynb` - سبق 14، MAF .NET

### مخصوص ڈائریکٹریز

- `translated_images/` - ترجموں کے لیے مقامی تصاویر
- `images/` - انگریزی مواد کے لیے اصل تصاویر
- `.devcontainer/` - VS Code ڈویلپمنٹ کنٹینر کنفیگریشن
- `.github/` - GitHub Actions ورک فلو اور ٹیمپلیٹس

### انحصارات

اہم پیکجز `requirements.txt` سے:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen فریم ورک
- `semantic-kernel` - Semantic Kernel فریم ورک
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI سروسز
- `azure-search-documents` - Azure AI Search انضمام
- `chromadb` - RAG مثالوں کے لیے ویکٹر ڈیٹا بیس
- `chainlit` - چیٹ UI فریم ورک
- `browser_use` - ایجنٹس کے لیے براؤزر آٹو میشن
- `mcp[cli]` - Model Context Protocol سپورٹ
- `mem0ai` - ایجنٹس کے لیے میموری مینجمنٹ

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
دستبرداری:
یہ دستاویز AI ترجمہ سروس [Co-op Translator](https://github.com/Azure/co-op-translator) کے ذریعے ترجمہ کی گئی ہے۔ اگرچہ ہم درستگی کے لئے کوشاں ہیں، براہِ مہربانی نوٹ کریں کہ خودکار تراجم میں غلطیاں یا نواقص ہو سکتے ہیں۔ اصل دستاویز اپنی مادری زبان میں معتبر ماخذ سمجھی جائے۔ اہم معلومات کے لیے پیشہ ور انسانی ترجمے کی سفارش کی جاتی ہے۔ اس ترجمے کے استعمال سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تشریح کے لیے ہم ذمہ دار نہیں ہیں۔
<!-- CO-OP TRANSLATOR DISCLAIMER END -->