# AGENTS.md

## Muhtasari wa Mradi

Hili hifadhi lina "Maajenti wa AI kwa Waanzilishi" - kozi ya elimu kamili inayofundisha kila kitu kinachohitajika kujenga Maajenti wa AI. Kozi ina masomo 15+ yanayojumuisha misingi, mifano ya muundo, mifumo, na utoaji wa maajenti wa AI kwa uzalishaji.

**Teknolojia Muhimu:**
- Python 3.12+
- Daftari za Jupyter kwa kujifunza kwa mwingiliano
- Mifumo ya AI: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Huduma za Azure AI: Microsoft Foundry, Azure AI Agent Service
- Soko la Modeli la GitHub (kipindi cha bure kinapatikana)

**Usanifu:**
- Muundo wa masomo (dira za 00-15+)
- Kila somo lina: hati ya README, mifano ya msimbo (daftari za Jupyter), na picha
- Msaada wa lugha nyingi kupitia mfumo wa tafsiri wa moja kwa moja
- Chaguzi mbalimbali za mifumo kwa kila somo (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Amri za Kusanidi

### Mahitaji ya Awali
- Python 3.12 au juu zaidi
- Akaunti ya GitHub (kwa Modeli za GitHub - kipindi cha bure)
- Usajili wa Azure (hiari, kwa huduma za Azure AI)

### Kusanidi Awali

1. **Nakili au vula hifadhi:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # AU
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Tengeneza na wezesha mazingira ya virtual ya Python:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Kwenye Windows: venv\Scripts\activate
   ```

3. **Sakinisha utegemezi:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Sanidi mabadiliko ya mazingira:**
   ```bash
   cp .env.example .env
   # Hariri .env na funguo zako za API na maeneo ya mwisho
   ```

### Mabadiliko ya Mazingira Yanayohitajika

Kwa **Modeli za GitHub (Bure)**:
- `GITHUB_TOKEN` - Tokeni ya upatikanaji binafsi kutoka GitHub

Kwa **Huduma za Azure AI** (hiari):
- `PROJECT_ENDPOINT` - Mwisho wa mradi wa Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - Kitufe cha API cha Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - Anuani ya mwisho ya Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Jina la utekelezaji kwa mfano wa mazungumzo
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Jina la utekelezaji kwa maingizo
- Mipangilio mingine ya Azure kama ilivyo kwenye `.env.example`

## Mtiririko wa Maendeleo

### Kuendesha Daftari za Jupyter

Kila somo lina daftari nyingi za Jupyter kwa mifumo tofauti:

1. **Anzisha Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Nenda kwenye dhairekteri ya somo** (mfano, `01-intro-to-ai-agents/code_samples/`)

3. **Fungua na endesha daftari:**
   - `*-semantic-kernel.ipynb` - Kutumia mfumo wa Semantic Kernel
   - `*-autogen.ipynb` - Kutumia mfumo wa AutoGen
   - `*-python-agent-framework.ipynb` - Kutumia Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Kutumia Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Kutumia Azure AI Agent Service

### Kufanya Kazi na Mifumo Tofauti

**Semantic Kernel + Modeli za GitHub:**
- Kipindi cha bure kinapatikana na akaunti ya GitHub
- Nzuri kwa kujifunza na majaribio
- Mfano wa faili: `*-semantic-kernel*.ipynb`

**AutoGen + Modeli za GitHub:**
- Kipindi cha bure kinapatikana na akaunti ya GitHub
- Uwezo wa kuendeshana kwa maajenti wengi
- Mfano wa faili: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Mfumo wa hivi karibuni kutoka Microsoft
- Unapatikana kwa Python na .NET
- Mfano wa faili: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Inahitaji usajili wa Azure
- Sifa za uzalishaji zimeandaliwa
- Mfano wa faili: `*-azureaiagent.ipynb`

## Maelekezo ya Upimaji

Hii ni hifadhi ya elimu yenye mifano ya msimbo badala ya msimbo wa uzalishaji wenye vipimo vya moja kwa moja. Ili kuthibitisha usanidi wako na mabadiliko:

### Upimaji wa Mkono

1. **Jaribu mazingira ya Python:**
   ```bash
   python --version  # Inapaswa kuwa 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Jaribu utekelezaji wa daftari:**
   ```bash
   # Badilisha daftari kuwa iwezekano na endesha (jaribu uingizaji)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Hakiki mabadiliko ya mazingira:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Kuendesha Daftari Pamoja Pamoja

Fungua daftari ndani ya Jupyter na endesha seli mfululizo. Kila daftari lina:
- Kauli kuingiza
- Kupakia mipangilio
- Mifano ya utekelezaji wa maajenti
- Matokeo yanayotarajiwa katika seli za markdown

## Mtindo wa Msimbo

### Kanuni za Python

- **Toleo la Python**: 3.12+
- **Mtindo wa Msimbo**: Fuata kanuni za kawaida za Python PEP 8
- **Daftari**: Tumia seli za markdown wazi kuelezea dhana
- **Kuagiza**: Pangilia kwa maktaba ya kawaida, wa tatu, na wa kienyeji

### Kanuni za Daftari la Jupyter

- Jumuisha seli za maelezo kabla ya seli za msimbo
- Ongeza mifano ya matokeo katika daftari kwa marejeleo
- Tumia majina ya mabadiliko yaliyo wazi yanayolingana na dhana za somo
- Dumisha mfuatano wa utekelezaji wa daftari (seli 1 → 2 → 3...)

### Mpangilio wa Faili

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

## Ujenzi na Utoaji

### Ujenzi wa Hati

Hifadhi hii hutumia Markdown kwa hati:
- Faili za README.md katika kila folda ya somo
- README.md kuu kwenye mzizi wa hifadhi
- Mfumo wa tafsiri wa moja kwa moja kupitia GitHub Actions

### Mlolongo wa CI/CD

Upo katika `.github/workflows/`:

1. **co-op-translator.yml** - Tafsiri ya moja kwa moja kwa lugha 50+
2. **welcome-issue.yml** - Kumkaribisha mtengenezaji wa masuala mapya
3. **welcome-pr.yml** - Kumkaribisha mchangiaji wa maombi ya kuvuta

### Utoaji

Hii ni hifadhi ya elimu - hakuna mchakato wa utoaji. Watumiaji:
1. Fanya forokopi au nakili hifadhi
2. Endesha daftari kwa mtaa au kwenye GitHub Codespaces
3. Jifunze kwa kubadilisha na kujaribu mifano

## Miongozo ya Maombi ya Kuvuta

### Kabla ya Kusubmitia

1. **Jaribu mabadiliko yako:**
   - Endesha daftari zilizoathirika kabisa
   - Hakiki seli zote zinaendesha bila makosa
   - Angalia matokeo ni sahihi

2. **Sasisha nyaraka:**
   - Sasisha README.md ikiwa unatoa dhana mpya
   - Ongeza maelezo katika daftari kwa msimbo mgumu
   - Hakikisha seli za markdown zinaelezea madhumuni

3. **Mabadiliko ya faili:**
   - Epuka kujituma `.env` faili (tumii `.env.example`)
   - Usijitume dira za `venv/` au `__pycache__/`
   - Dumisha matokeo ya daftari yanapoonyesha dhana
   - Ondoa faili za muda na nakala za daftari (`*-backup.ipynb`)

### Muundo wa Kichwa cha PR

Tumia vichwa vya kuelezea:
- `[Lesson-XX] Ongeza mfano mpya kwa <concept>`
- `[Fix] Rekebisha makosa ya tahajia katika lesson-XX README`
- `[Update] Boreshaji la mfano wa msimbo katika lesson-XX`
- `[Docs] Sasisha maelekezo ya usanidi`

### Ukaguzi Unaohitajika

- Daftari zinapaswa kuendeshwa bila makosa
- Faili za README ziwe wazi na sahihi
- Fuata mifumo ya msimbo iliyopo kwenye hifadhi
- Dumisha muafaka na masomo mengine

## Vidokezo Zaidi

### Makosa Yanayojirudia

1. **Toleo la Python lisilolingana:**
   - Hakikisha unatumia Python 3.12+
   - Baadhi ya vifurushi haviendani na matoleo ya kale
   - Tumia `python3 -m venv` kuanzisha toleo la Python wazi

2. **Mabadiliko ya mazingira:**
   - Daima tengeneza `.env` kutoka `.env.example`
   - Usijitume faili `.env` (iko kwenye `.gitignore`)
   - Tokeni ya GitHub inahitaji ruhusa zinazofaa

3. **Migongano ya kifurushi:**
   - Tumia mazingira safi ya virtual
   - Sakinisha kutoka `requirements.txt` badala ya vifurushi binafsi
   - Baadhi ya daftari zinaweza kuhitaji vifurushi vya ziada vilivyotajwa kwenye seli za markdown

4. **Huduma za Azure:**
   - Huduma za Azure AI zinahitaji usajili hai
   - Baadhi ya sifa ni maalum kwa mikoa fulani
   - Vizingiti vya bure vinaweza kuathiri Modeli za GitHub

### Njia ya Kujifunza

Ufuate msururu huu wa kuendelea kupitia masomo:
1. **00-course-setup** - Anza hapa kwa usanidi wa mazingira
2. **01-intro-to-ai-agents** - Elewa misingi ya maajenti wa AI
3. **02-explore-agentic-frameworks** - Jifunze kuhusu mifumo tofauti
4. **03-agentic-design-patterns** - Mifano ya msingi ya muundo
5. Endelea kupitia masomo yaliyopangwa kwa mfuatano

### Uchaguaji wa Mfumo

Chagua mfumo kulingana na malengo yako:
- **Kujifunza/Kujaribu**: Semantic Kernel + Modeli za GitHub (bure)
- **Mifumo ya maajenti wengi**: AutoGen
- **Sifa za hivi karibuni**: Microsoft Agent Framework (MAF)
- **Utoaji kwa uzalishaji**: Azure AI Agent Service

### Kupata Msaada

- Jiunge na [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Angalia faili za README za masomo kwa mwongozo maalum
- Angalia [README.md](./README.md) kuu kwa muhtasari wa kozi
- Rejelea [Course Setup](./00-course-setup/README.md) kwa maelekezo ya kina

### Kuchangia

Huu ni mradi wa elimu wa wazi. Mchango unakaribishwa:
- Boreshaji mifano ya msimbo
- Rekebisha makosa ya tahajia au makosa
- Ongeza maelezo ya ufafanuzi
- Pendekeza mada mpya za masomo
- Tafsiri kwenda lugha nyingine zaidi

Angalia [Masuala ya GitHub](https://github.com/microsoft/ai-agents-for-beginners/issues) kwa mahitaji ya sasa.

## Muktadha Maalum wa Mradi

### Msaada wa Lugha nyingi

Hifadhi hii hutumia mfumo wa tafsiri wa moja kwa moja:
- Lugha 50+ zinasaidiwa
- Tafsiri ziko katika dira `/translations/<lang-code>/`
- Mlolongo wa GitHub Actions unashughulikia masasisho ya tafsiri
- Faili za chanzo ziko kwa Kiingereza kwenye mzizi wa hifadhi

### Muundo wa Somo

Kila somo lina muundo sawa:
1. Picha ya video yenye kiungo
2. Maudhui yaliyoandikwa ya somo (README.md)
3. Mifano ya msimbo katika mifumo mingi
4. Malengo ya kujifunza na mahitaji
5. Rasilimali za ziada za kujifunza zilizoambatanishwa

### Jina la Mfano wa Msimbo

Muundo: `<nambari-ya-somo>-<jina-la-mfumo>.ipynb`
- `04-semantic-kernel.ipynb` - Somo 4, Semantic Kernel
- `07-autogen.ipynb` - Somo 7, AutoGen
- `14-python-agent-framework.ipynb` - Somo 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Somo 14, MAF .NET

### Dira Maalum

- `translated_images/` - Picha zilizotafsiriwa kwa lugha tofauti
- `images/` - Picha za awali kwa maudhui ya Kiingereza
- `.devcontainer/` - Mpangilio wa kontena ya maendeleo wa VS Code
- `.github/` - Mlolongo wa GitHub Actions na mifano

### Vitegemezi

Vifurushi muhimu kutoka `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - Mfumo wa AutoGen
- `semantic-kernel` - Mfumo wa Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Huduma za Azure AI
- `azure-search-documents` - Uunganisho wa Azure AI Search
- `chromadb` - Hifadhi ya data ya vector kwa mifano ya RAG
- `chainlit` - Mfumo wa UI wa mazungumzo
- `browser_use` - Uendeshaji wa kivinjari kwa maajenti
- `mcp[cli]` - Msaada wa Model Context Protocol
- `mem0ai` - Usimamizi wa kumbukumbu kwa maajenti

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Kiarifu cha Kutohusika**:
Hati hii imefasiriwa kwa kutumia huduma ya tafsiri ya AI [Co-op Translator](https://github.com/Azure/co-op-translator). Ingawa tunajitahidi kuwa sahihi, tafadhali fahamu kuwa tafsiri za kiotomatiki zinaweza kuwa na makosa au upungufu wa usahihi. Hati asili kwa lugha yake ya asili inapaswa kuchukuliwa kama chanzo cha mamlaka. Kwa taarifa muhimu, tafsiri ya kitaalamu inayotolewa na binadamu inashauriwa. Hatuna wajibu kwa kutoelewana au tafsiri potofu zitokanazo na matumizi ya tafsiri hii.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->