# AGENTS.md

## परियोजना अवलोकन

यह रिपॉजिटरी "शुरुआती के लिए AI एजेंट" रखती है - एक व्यापक शैक्षिक पाठ्यक्रम जो AI एजेंट बनाने के लिए आवश्यक सभी चीजें सिखाता है। यह पाठ्यक्रम 15+ पाठों का संग्रह है जो AI एजेंट के मूल तत्वों, डिज़ाइन पैटर्न, फ्रेमवर्क्स, और उत्पादन परिनियोजन को कवर करता है।

**मुख्य तकनीकें:**
- Python 3.12+
- इंटरेक्टिव शिक्षण के लिए Jupyter नोटबुक्स
- AI फ्रेमवर्क: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI सेवाएं: Microsoft Foundry, Azure AI Agent Service
- GitHub Models मार्केटप्लेस (मुफ्त टियर उपलब्ध)

**आर्किटेक्चर:**
- पाठ-आधारित संरचना (00-15+ निर्देशिकाएँ)
- प्रत्येक पाठ में शामिल हैं: README दस्तावेज़, कोड उदाहरण (Jupyter नोटबुक्स), और चित्र
- स्वचालित अनुवाद प्रणाली के माध्यम से बहुभाषी समर्थन
- प्रत्येक पाठ के लिए कई फ्रेमवर्क विकल्प (Semantic Kernel, AutoGen, Azure AI Agent Service)

## सेटअप कमांड्स

### पूर्व आवश्यकताएँ
- Python 3.12 या उससे ऊपर
- GitHub खाता (GitHub Models के लिए - मुफ्त टियर)
- Azure सदस्यता (वैकल्पिक, Azure AI सेवाओं के लिए)

### प्रारंभिक सेटअप

1. **रिपॉजिटरी को क्लोन या फोर्क करें:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # या
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Python वर्चुअल वातावरण बनाएं और सक्रिय करें:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # विंडोज पर: venv\Scripts\activate
   ```

3. **निर्भरता स्थापित करें:**
   ```bash
   pip install -r requirements.txt
   ```

4. **पर्यावरण चर सेट करें:**
   ```bash
   cp .env.example .env
   # अपनी API कुंजियों और एंडपॉइंट्स के साथ .env को संपादित करें
   ```

### आवश्यक पर्यावरण चर

**GitHub Models (मुफ्त)** के लिए:
- `GITHUB_TOKEN` - GitHub से व्यक्तिगत एक्सेस टोकन

**Azure AI सेवाओं** (वैकल्पिक):
- `PROJECT_ENDPOINT` - Microsoft Foundry परियोजना एंडपॉइंट
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API कुंजी
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI एंडपॉइंट URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - चैट मॉडल के लिए परिनियोजन नाम
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - एम्बेडिंग के लिए परिनियोजन नाम
- अतिरिक्त Azure कॉन्फ़िगरेशन `.env.example` में दिखाया गया

## विकास कार्यप्रवाह

### Jupyter नोटबुक्स चलाना

प्रत्येक पाठ में विभिन्न फ्रेमवर्क के लिए कई Jupyter नोटबुक्स होती हैं:

1. **Jupyter प्रारंभ करें:**
   ```bash
   jupyter notebook
   ```

2. **किसी पाठ निर्देशिका में नेविगेट करें** (जैसे, `01-intro-to-ai-agents/code_samples/`)

3. **नोटबुक्स खोलें और चलाएँ:**
   - `*-semantic-kernel.ipynb` - Semantic Kernel फ्रेमवर्क का उपयोग
   - `*-autogen.ipynb` - AutoGen फ्रेमवर्क का उपयोग
   - `*-python-agent-framework.ipynb`` - Microsoft Agent Framework (Python) का उपयोग
   - `*-dotnet-agent-framework.ipynb` - Microsoft Agent Framework (.NET) का उपयोग
   - `*-azureaiagent.ipynb` - Azure AI Agent Service का उपयोग

### विभिन्न फ्रेमवर्क्स के साथ काम करना

**Semantic Kernel + GitHub Models:**
- GitHub खाते के साथ मुफ्त टियर उपलब्ध
- सीखने और प्रयोग के लिए अच्छा
- फ़ाइल पैटर्न: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- GitHub खाते के साथ मुफ्त टियर उपलब्ध
- मल्टी-एजेंट समन्वय क्षमताएँ
- फ़ाइल पैटर्न: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Microsoft का नवीनतम फ्रेमवर्क
- Python और .NET दोनों में उपलब्ध
- फ़ाइल पैटर्न: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Azure सदस्यता आवश्यक
- उत्पादन-तैयार विशेषताएं
- फ़ाइल पैटर्न: `*-azureaiagent.ipynb`

## परीक्षण निर्देश

यह एक शैक्षिक रिपॉजिटरी है जिसमें उदाहरण कोड है, न कि स्वचालित परीक्षण के साथ उत्पादन कोड। अपने सेटअप और परिवर्तनों की पुष्टि के लिए:

### मैनुअल परीक्षण

1. **Python वातावरण का परीक्षण करें:**
   ```bash
   python --version  # 3.12+ होना चाहिए
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **नोटबुक निष्पादन का परीक्षण करें:**
   ```bash
   # नोटबुक को स्क्रिप्ट में कनवर्ट करें और चलाएं (परीक्षण आयात)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **पर्यावरण चर सत्यापित करें:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### व्यक्तिगत नोटबुक्स चलाना

नोटबुक्स को Jupyter में खोलें और कक्षों को क्रमशः निष्पादित करें। प्रत्येक नोटबुक स्व-निहित है और निम्न शामिल हैं:
- इम्पोर्ट स्टेटमेंट्स
- कॉन्फ़िगरेशन लोडिंग
- उदाहरण एजेंट क्रियान्वयन
- मार्कडाउन कक्षों में अपेक्षित आउटपुट

## कोड शैली

### Python सम्मेलन

- **Python संस्करण**: 3.12+
- **कोड शैली**: मानक Python PEP 8 सम्मेलन का पालन करें
- **नोटबुक्स**: अवधारणाओं को स्पष्ट करने के लिए स्पष्ट मार्कडाउन कक्षों का उपयोग करें
- **इम्पोर्ट्स**: मानक लाइब्रेरी, थर्ड-पार्टी, स्थानीय इम्पोर्ट्स को समूहबद्ध करें

### Jupyter नोटबुक सम्मेलन

- कोड कक्षों से पहले वर्णनात्मक मार्कडाउन कक्ष शामिल करें
- संदर्भ के लिए नोटबुक में आउटपुट उदाहरण जोड़ें
- पाठ अवधारणाओं के अनुसार स्पष्ट चर नामों का उपयोग करें
- नोटबुक निष्पादन क्रम को रैखिक रखें (कोष्ठ 1 → 2 → 3...)

### फ़ाइल आयोजन

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

## निर्माण और परिनियोजन

### दस्तावेज़ीकरण निर्माण

यह रिपॉजिटरी दस्तावेज़ीकरण के लिए Markdown का उपयोग करती है:
- प्रत्येक पाठ फ़ोल्डर में README.md फ़ाइलें
- रिपॉजिटरी रूट पर मुख्य README.md
- GitHub Actions के माध्यम से स्वचालित अनुवाद प्रणाली

### CI/CD पाइपलाइन

`.github/workflows/` में स्थित:

1. **co-op-translator.yml** - 50+ भाषाओं में स्वचालित अनुवाद
2. **welcome-issue.yml** - नए मुद्दा निर्माता का स्वागत करता है
3. **welcome-pr.yml** - नए पुल अनुरोध योगदानकर्ताओं का स्वागत करता है

### परिनियोजन

यह एक शैक्षिक रिपॉजिटरी है - कोई परिनियोजन प्रक्रिया नहीं। उपयोगकर्ता:
1. रिपॉजिटरी को फोर्क या क्लोन करें
2. नोटबुक्स स्थानीय या GitHub Codespaces में चलाएँ
3. उदाहरणों को संशोधित करके और प्रयोग करके सीखें

## पुल अनुरोध दिशानिर्देश

### जमा करने से पहले

1. **अपने परिवर्तनों का परीक्षण करें:**
   - प्रभावित नोटबुक्स को पूरी तरह से चलाएँ
   - सुनिश्चित करें कि सभी कक्ष त्रुटि-रहित चलें
   - आउटपुट सही हों

2. **दस्तावेज़ीकरण अद्यतन:**
   - यदि नए अवधारणाएँ जोड़ रहे हैं तो README.md अपडेट करें
   - जटिल कोड के लिए नोटबुक में टिप्पणियाँ जोड़ें
   - सुनिश्चित करें कि मार्कडाउन कक्ष उद्देश्य स्पष्ट करें

3. **फ़ाइल परिवर्तन:**
   - `.env` फ़ाइलें कमिट न करें (`.env.example` का उपयोग करें)
   - `venv/` या `__pycache__/` निर्देशिकाएं कमिट न करें
   - जब अवधारणाएँ प्रदर्शित होती हों तो नोटबुक आउटपुट रखें
   - अस्थायी फ़ाइलें और बैकअप नोटबुक्स (`*-backup.ipynb`) हटाएँ

### PR शीर्षक प्रारूप

वर्णनात्मक शीर्षक उपयोग करें:
- `[Lesson-XX] <concept> के लिए नया उदाहरण जोड़ें`
- `[Fix] lesson-XX README में टाइपो सुधारें`
- `[Update] lesson-XX में कोड उदाहरण सुधारें`
- `[Docs] सेटअप निर्देश अपडेट करें`

### आवश्यक जांच

- नोटबुक त्रुटि-रहित निष्पादित होनी चाहिए
- README फ़ाइल स्पष्ट और सटीक होनी चाहिए
- रिपॉजिटरी में मौजूदा कोड पैटर्न का पालन करें
- अन्य पाठों के साथ संगति बनाए रखें

## अतिरिक्त नोट्स

### सामान्य त्रुटियाँ

1. **Python संस्करण असंगति:**
   - Python 3.12+ का उपयोग सुनिश्चित करें
   - कुछ पैकेज पुराने संस्करणों में काम नहीं कर सकते
   - Python संस्करण स्पष्ट करने के लिए `python3 -m venv` का उपयोग करें

2. **पर्यावरण चर:**
   - हमेशा `.env.example` से `.env` बनाएं
   - `.env` फ़ाइल कमिट न करें (यह `.gitignore` में है)
   - GitHub टोकन के लिए उपयुक्त अनुमतियाँ आवश्यक

3. **पैकेज संघर्ष:**
   - ताजा वर्चुअल वातावरण का उपयोग करें
   - पैकेज अलग-अलग इंस्टॉल करने के बजाय `requirements.txt` से इंस्टॉल करें
   - कुछ नोटबुक्स को अतिरिक्त पैकेजों की जरूरत हो सकती है जो उनके मार्कडाउन कक्षों में उल्लेखित हैं

4. **Azure सेवाएं:**
   - Azure AI सेवाओं के लिए सक्रिय सदस्यता आवश्यक
   - कुछ सुविधाएँ क्षेत्र-विशिष्ट हो सकती हैं
   - GitHub Models के मुफ्त टियर पर सीमाएँ लागू होती हैं

### सीखने का रास्ता

अनुशंसित क्रम में पाठ:
1. **00-course-setup** - पर्यावरण सेटअप के लिए शुरुआत यहां करें
2. **01-intro-to-ai-agents** - AI एजेंट के मूल तत्व समझें
3. **02-explore-agentic-frameworks** - विभिन्न फ्रेमवर्क सीखें
4. **03-agentic-design-patterns** - मुख्य डिज़ाइन पैटर्न
5. क्रमशः नंबर वाले पाठ जारी रखें

### फ्रेमवर्क चयन

अपने लक्ष्य के अनुसार फ्रेमवर्क चुनें:
- **सीखना/प्रोटोटाइपिंग:** Semantic Kernel + GitHub Models (मुफ्त)
- **मल्टी-एजेंट सिस्टम:** AutoGen
- **नवीनतम विशेषताएं:** Microsoft Agent Framework (MAF)
- **उत्पादन परिनियोजन:** Azure AI Agent Service

### मदद प्राप्त करना

- [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord) में शामिल हों
- विशिष्ट मार्गदर्शन के लिए पाठ README फ़ाइलें देखें
- कोर्स अवलोकन के लिए मुख्य [README.md](./README.md) देखें
- विस्तृत सेटअप निर्देश के लिए [Course Setup](./00-course-setup/README.md) देखें

### योगदान

यह एक खुला शैक्षिक प्रोजेक्ट है। योगदान स्वागत योग्य हैं:
- कोड उदाहरणों में सुधार करें
- टाइपो या त्रुटियां ठीक करें
- स्पष्ट करने वाली टिप्पणियां जोड़ें
- नए पाठ विषय सुझाएँ
- अतिरिक्त भाषाओं में अनुवाद करें

वर्तमान आवश्यकताओं के लिए [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) देखें।

## परियोजना-विशिष्ट संदर्भ

### बहुभाषी समर्थन

यह रिपॉजिटरी स्वचालित अनुवाद प्रणाली का उपयोग करती है:
- 50+ भाषाएँ समर्थित
- अनुवाद `/translations/<lang-code>/` निर्देशिकाओं में
- GitHub Actions वर्कफ्लो अनुवाद अद्यतनों को संभालता है
- स्रोत फ़ाइलें अंग्रेजी में रिपॉजिटरी रूट पर

### पाठ संरचना

प्रत्येक पाठ एक समान पैटर्न का पालन करता है:
1. लिंक के साथ वीडियो थम्बनेल
2. लिखित पाठ सामग्री (README.md)
3. कई फ्रेमवर्क्स में कोड उदाहरण
4. सीखने के उद्देश्य और पूर्व आवश्यकताएँ
5. अतिरिक्त शिक्षण संसाधन लिंक

### कोड उदाहरण नामकरण

फ़ॉर्मेट: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - पाठ 4, Semantic Kernel
- `07-autogen.ipynb` - पाठ 7, AutoGen
- `14-python-agent-framework.ipynb` - पाठ 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - पाठ 14, MAF .NET

### विशेष निर्देशिकाएं

- `translated_images/` - अनुवाद के लिए स्थानीयकृत चित्र
- `images/` - अंग्रेज़ी सामग्री के लिए मूल चित्र
- `.devcontainer/` - VS Code डेवलपमेंट कंटेनर कॉन्फ़िगरेशन
- `.github/` - GitHub Actions वर्कफ़्लोज़ और टेम्पलेट्स

### निर्भरता

`requirements.txt` से प्रमुख पैकेज:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen फ्रेमवर्क
- `semantic-kernel` - Semantic Kernel फ्रेमवर्क
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI सेवाएं
- `azure-search-documents` - Azure AI Search एकीकरण
- `chromadb` - RAG उदाहरणों के लिए वेक्टर डेटाबेस
- `chainlit` - चैट UI फ्रेमवर्क
- `browser_use` - एजेंट के लिए ब्राउज़र ऑटोमेशन
- `mcp[cli]` - मॉडल कॉन्टेक्सट प्रोटोकॉल समर्थन
- `mem0ai` - एजेंटों के लिए मेमोरी प्रबंधन

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**अस्वीकरण**:
यह दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियाँ या अस्पष्टताएँ हो सकती हैं। मूल दस्तावेज़ अपनी मूल भाषा में प्रामाणिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सिफारिश की जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->