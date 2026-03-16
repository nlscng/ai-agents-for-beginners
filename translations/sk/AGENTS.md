# AGENTS.md

## Prehľad projektu

Tento repozitár obsahuje "AI Agentov pre začiatočníkov" - komplexný vzdelávací kurz, ktorý učí všetko potrebné na vytváranie AI Agentov. Kurz pozostáva z viac ako 15 lekcií pokrývajúcich základy, návrhové vzory, frameworky a produkčné nasadenie AI agentov.

**Kľúčové technológie:**
- Python 3.12+
- Jupyter Notebooky pre interaktívne učenie
- AI Frameworky: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI služby: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (dostupná bezplatná úroveň)

**Architektúra:**
- Štruktúra podľa lekcií (adresáre 00-15+)
- Každá lekcia obsahuje: dokumentáciu README, príklady kódu (Jupyter notebooky) a obrázky
- Podpora viacerých jazykov pomocou automatizovaného systému prekladu
- Viaceré možnosti frameworkov na lekciu (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Príkazy na nastavenie

### Predpoklady
- Python 3.12 alebo novší
- GitHub účet (pre GitHub Models - bezplatná vrstva)
- Predplatné Azure (voliteľné, pre Azure AI služby)

### Počiatočné nastavenie

1. **Naklonujte alebo forknite repozitár:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ALEBO
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Vytvorte a aktivujte Python virtuálne prostredie:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Vo Windows: venv\Scripts\activate
   ```

3. **Nainštalujte závislosti:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Nastavte premenné prostredia:**
   ```bash
   cp .env.example .env
   # Upraviť .env s vašimi API kľúčmi a koncovými bodmi
   ```

### Povinné premenné prostredia

Pre **GitHub Models (bezplatne)**:
- `GITHUB_TOKEN` - osobný prístupový token z GitHubu

Pre **Azure AI služby** (voliteľné):
- `PROJECT_ENDPOINT` - endpoint projektu Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - kľúč API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL endpointu Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - názov nasadenia chat modelu
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - názov nasadenia embeddingov
- Ďalšie Azure konfigurácie podľa `.env.example`

## Vývojový workflow

### Spustenie Jupyter notebookov

Každá lekcia obsahuje viacero Jupyter notebookov pre rôzne frameworky:

1. **Spustite Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Prejdite do adresára lekcie** (napr. `01-intro-to-ai-agents/code_samples/`)

3. **Otvorte a spustite notebooky:**
   - `*-semantic-kernel.ipynb` - Použitie frameworku Semantic Kernel
   - `*-autogen.ipynb` - Použitie frameworku AutoGen
   - `*-python-agent-framework.ipynb` - Použitie Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Použitie Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Použitie Azure AI Agent Service

### Práca s rôznymi frameworkmi

**Semantic Kernel + GitHub Models:**
- Bezplatná vrstva dostupná s GitHub účtom
- Vhodné na učenie a experimentovanie
- Vzor súboru: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Bezplatná vrstva dostupná s GitHub účtom
- Podpora orchestrácie viacerých agentov
- Vzor súboru: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Najnovší framework od Microsoftu
- Dostupný v Python a .NET
- Vzor súboru: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Vyžaduje predplatné Azure
- Produkčné funkcie pripravené na nasadenie
- Vzor súboru: `*-azureaiagent.ipynb`

## Inštrukcie na testovanie

Toto je vzdelávací repozitár s ukážkovým kódom, nie produkčný kód s automatizovanými testami. Na overenie nastavenia a zmien:

### Manuálne testovanie

1. **Otestujte Python prostredie:**
   ```bash
   python --version  # Malo by byť 3.12 a vyšší
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Otestujte spustenie notebooku:**
   ```bash
   # Prekonvertujte zápisník do skriptu a spustite (testuje importy)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Overte premenné prostredia:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Spustenie jednotlivých notebookov

Otvorte notebooky v Jupyter a vykonávajte bunky postupne. Každý notebook je samostatný a obsahuje:
- importy
- načítanie konfigurácie
- príklady implementácie agentov
- očakávané výstupy v markdown bunkách

## Štýl kódu

### Python konvencie

- **Verzia Pythonu**: 3.12+
- **Štýl kódu**: dodržiavajte štandardné konvencie PEP 8
- **Notebooky**: používajte jasné markdown bunky na vysvetlenie pojmov
- **Importy**: zoskupujte podľa štandardnej knižnice, tretích strán a lokálne

### Konvencie Jupyter notebookov

- Zahrňte popisné markdown bunky pred kódovými bunkami
- Pridajte príklady výstupov v notebookoch pre referenciu
- Používajte zrozumiteľné premenné, ktoré zodpovedajú konceptom lekcie
- Dodržujte lineárny poradie vykonávania buniek (bunka 1 → 2 → 3...)

### Organizácia súborov

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

## Skladanie a nasadenie

### Skladanie dokumentácie

Tento repozitár používa Markdown na dokumentáciu:
- README.md súbory v každom adresári lekcie
- Hlavný README.md v koreňovom adresári repozitára
- Automatizovaný systém prekladu cez GitHub Actions

### CI/CD pipeline

Nachádza sa v `.github/workflows/`:

1. **co-op-translator.yml** - automatický preklad do viac ako 50 jazykov
2. **welcome-issue.yml** - vítanie nových autorov issues
3. **welcome-pr.yml** - vítanie nových autorov pull requestov

### Nasadenie

Tento repozitár je vzdelávací - bez nasadzovacieho procesu. Používatelia:
1. Forknú alebo naklonujú repozitár
2. Spúšťajú notebooky lokálne alebo v GitHub Codespaces
3. Učia sa úpravou a experimentovaním na príkladoch

## Pokyny k pull requestom

### Pred odoslaním

1. **Otestujte zmeny:**
   - Spustite úplné notebooky, ktorých sa zmeny týkajú
   - Overte, že všetky bunky sa vykonajú bez chýb
   - Skontrolujte, či výstupy dávajú zmysel

2. **Aktualizácia dokumentácie:**
   - Aktualizujte README.md ak pridávate nové koncepty
   - Pridajte komentáre v notebookoch pri zložitejšom kóde
   - Uistite sa, že markdown bunky vysvetľujú účel

3. **Zmeny v súboroch:**
   - Vyhnite sa commitovaniu `.env` súborov (používajte `.env.example`)
   - Nekommitujte adresáre `venv/` alebo `__pycache__/`
   - Zachovajte výstupy notebookov, ak ilustrujú koncepty
   - Odstráňte dočasné súbory a zálohy notebookov (`*-backup.ipynb`)

### Formát názvu PR

Používajte popisné názvy:
- `[Lesson-XX] Pridanie nového príkladu pre <koncept>`
- `[Fix] Oprava preklepu v README lekcie XX`
- `[Update] Vylepšenie príkladu kódu v lekcii XX`
- `[Docs] Aktualizácia inštrukcií na nastavenie`

### Povinné kontroly

- Notebooky sa majú vykonať bez chýb
- README súbory majú byť jasné a presné
- Dodržiavajte existujúce vzory kódu v repozitári
- Zachovajte konzistenciu s ostatnými lekciami

## Ďalšie poznámky

### Bežné problémy

1. **Nezladená verzia Pythonu:**
   - Uistite sa, že používate Python 3.12+
   - Niektoré balíky nemusia fungovať na starších verziách
   - Použite `python3 -m venv` pre explicitné určenie verzie Pythonu

2. **Premenné prostredia:**
   - Vždy vytvorte `.env` z `.env.example`
   - Necommitujte `.env` (je v `.gitignore`)
   - GitHub token vyžaduje primerané povolenia

3. **Konflikty balíkov:**
   - Použite čisté virtuálne prostredie
   - Inštalujte z `requirements.txt`, nie jednotlivo
   - Niektoré notebooky môžu vyžadovať ďalšie balíky uvedené v ich markdown bunkách

4. **Azure služby:**
   - Azure AI služby vyžadujú aktívne predplatné
   - Niektoré funkcie sú regiónovo obmedzené
   - Bezplatná vrstva platí pre GitHub Models

### Učebná cesta

Odporúčané poradie lekcií:
1. **00-course-setup** - Začnite tu s nastavením prostredia
2. **01-intro-to-ai-agents** - Zoznámte sa so základmi AI agentov
3. **02-explore-agentic-frameworks** - Naučte sa o rôznych frameworkoch
4. **03-agentic-design-patterns** - Základné návrhové vzory
5. Pokračujte v očíslovaných lekciách postupne

### Výber frameworku

Vyberte framework podľa vašich cieľov:
- **Učenie/prototypy**: Semantic Kernel + GitHub Models (bezplatne)
- **Multi-agent systémy**: AutoGen
- **Najnovšie funkcie**: Microsoft Agent Framework (MAF)
- **Produkčné nasadenie**: Azure AI Agent Service

### Hľadanie pomoci

- Pripojte sa k [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Prejdite README súbory lekcií pre špecifické návody
- Pozrite hlavný [README.md](./README.md) pre prehľad kurzu
- Pre detaily ohľadom nastavenia nájdete inštrukcie v [Course Setup](./00-course-setup/README.md)

### Spolupráca

Toto je otvorený vzdelávací projekt. Príspevky sú vítané:
- Vylepšujte príklady kódu
- Opravujte preklepy alebo chyby
- Pridávajte vysvetľujúce komentáre
- Navrhujte nové témy lekcií
- Prekladajte do ďalších jazykov

Pozrite si [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) pre aktuálne potreby.

## Kontext špecifický pre projekt

### Podpora viacerých jazykov

Tento repozitár používa automatizovaný systém prekladu:
- Podpora viac ako 50 jazykov
- Preklady sú v priečinkoch `/translations/<lang-code>/`
- GitHub Actions workflow spravuje aktualizácie prekladov
- Zdrojové súbory sú v angličtine v koreňovom adresári repozitára

### Štruktúra lekcie

Každá lekcia sleduje konzistentný vzor:
1. Náhľad videa s odkazom
2. Písaný obsah lekcie (README.md)
3. Príklady kódu v rôznych frameworkoch
4. Výukové ciele a predpoklady
5. Odkazy na doplnkové materiály na učenie

### Názvy ukážok kódu

Formát: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Lekcia 4, Semantic Kernel
- `07-autogen.ipynb` - Lekcia 7, AutoGen
- `14-python-agent-framework.ipynb` - Lekcia 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lekcia 14, MAF .NET

### Špeciálne adresáre

- `translated_images/` - lokalizované obrázky pre preklady
- `images/` - originálne obrázky pre anglický obsah
- `.devcontainer/` - konfigurácia vývojového kontajnera VS Code
- `.github/` - GitHub Actions workflowy a šablóny

### Závislosti

Kľúčové balíky z `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - framework AutoGen
- `semantic-kernel` - framework Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI služby
- `azure-search-documents` - integrácia Azure AI Search
- `chromadb` - vektorová databáza pre RAG príklady
- `chainlit` - framework pre chatovacie UI
- `browser_use` - automatizácia prehliadača pre agentov
- `mcp[cli]` - podpora Model Context Protocol
- `mem0ai` - správa pamäte pre agentov

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zrieknutie sa zodpovednosti**:  
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Aj keď sa snažíme o presnosť, prosím vezmite na vedomie, že automatizované preklady môžu obsahovať chyby alebo nepresnosti. Originálny dokument v jeho pôvodnom jazyku by mal byť považovaný za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny ľudský preklad. Nie sme zodpovední za žiadne nedorozumenia alebo nesprávne interpretácie vyplývajúce z použitia tohto prekladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->