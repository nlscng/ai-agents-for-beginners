# AGENTS.md

## Přehled projektu

Tento repozitář obsahuje "AI Agenty pro začátečníky" - komplexní vzdělávací kurz, který učí vše potřebné k vytvoření AI agentů. Kurz se skládá z více než 15 lekcí pokrývajících základy, návrhové vzory, frameworky a nasazení AI agentů do produkce.

**Klíčové technologie:**
- Python 3.12+
- Jupyter Notebooks pro interaktivní výuku
- AI Frameworky: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI služby: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (bezplatná verze dostupná)

**Architektura:**
- Struktura založená na lekcích (adresáře 00-15+)
- Každá lekce obsahuje: dokumentaci README, ukázky kódu (Jupyter notebooky) a obrázky
- Podpora více jazyků díky automatizovanému systému překladu
- Více možností frameworků na jednu lekci (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Příkazy pro nastavení

### Požadavky
- Python 3.12 nebo vyšší
- GitHub účet (pro GitHub Models - bezplatná verze)
- Azure předplatné (volitelné, pro Azure AI služby)

### Inicializace

1. **Klonujte nebo forkněte repozitář:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # NEBO
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Vytvořte a aktivujte virtuální prostředí Pythonu:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Ve Windows: venv\Scripts\activate
   ```

3. **Nainstalujte závislosti:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Nastavte proměnné prostředí:**
   ```bash
   cp .env.example .env
   # Upravit .env s vašimi klíči API a koncovými body
   ```

### Požadované proměnné prostředí

Pro **GitHub Models (zdarma)**:
- `GITHUB_TOKEN` - Osobní přístupový token z GitHubu

Pro **Azure AI služby** (volitelné):
- `PROJECT_ENDPOINT` - Microsoft Foundry endpoint projektu
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API klíč
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI endpoint URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Název nasazení pro chat model
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Název nasazení pro embeddings
- Další konfigurace Azure jak je uvedeno v `.env.example`

## Vývojový proces

### Spuštění Jupyter Notebooků

Každá lekce obsahuje více Jupyter notebooků pro různé frameworky:

1. **Spusťte Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Přejděte do adresáře lekce** (např. `01-intro-to-ai-agents/code_samples/`)

3. **Otevřete a spusťte notebooky:**
   - `*-semantic-kernel.ipynb` - Použití Semantic Kernel frameworku
   - `*-autogen.ipynb` - Použití AutoGen frameworku
   - `*-python-agent-framework.ipynb` - Použití Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Použití Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Použití Azure AI Agent Service

### Práce s různými frameworky

**Semantic Kernel + GitHub Models:**
- Zdarma dostupné s účtem na GitHubu
- Vhodné pro výuku a experimentování
- Vzor názvu souboru: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Zdarma dostupné s účtem na GitHubu
- Podpora multi-agentní orchestraci
- Vzor názvu souboru: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Nejnovější framework od Microsoftu
- K dispozici v Pythonu i .NET
- Vzor názvu souboru: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Vyžaduje Azure předplatné
- Funkce připravené pro produkci
- Vzor názvu souboru: `*-azureaiagent.ipynb`

## Instrukce pro testování

Tento repozitář je vzdělávací s ukázkovým kódem, nikoliv produkčním kódem s automatizovanými testy. Pro ověření nastavení a změn:

### Manuální testování

1. **Otestujte Python prostředí:**
   ```bash
   python --version  # Mělo by být 3.12 a vyšší
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Otestujte spuštění notebooku:**
   ```bash
   # Převést poznámkový blok na skript a spustit (testuje importy)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Ověřte nastavení proměnných prostředí:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Spuštění jednotlivých notebooků

Otevřete notebooky v Jupyteru a provádějte buňky postupně. Každý notebook je samostatný a obsahuje:
- Importy
- Načítání konfigurace
- Ukázky implementace agentů
- Očekávané výstupy v markdown buňkách

## Styl kódu

### Python konvence

- **Verze Pythonu**: 3.12+
- **Styl kódu**: Dodržujte standardní Python PEP 8
- **Notebooks**: Používejte přehledné markdown buňky pro vysvětlení
- **Importy**: Skupinové řazení - standardní knihovny, třetí strany, lokální importy

### Konvence Jupyter notebooku

- Zařazujte popisné markdown bloky před kódem
- Přidávejte příklady výstupů pro referenci
- Používejte jasné názvy proměnných odpovídající konceptům lekce
- Udržujte lineární pořadí spuštění buněk (buňka 1 → 2 → 3...)

### Organizace souborů

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

## Sestavení a nasazení

### Tvorba dokumentace

Tento repozitář používá Markdown pro dokumentaci:
- README.md soubory v každém adresáři lekce
- Hlavní README.md v kořenovém adresáři repozitáře
- Automatizovaný systém překladu pomocí GitHub Actions

### CI/CD Pipeline

Nachází se v `.github/workflows/`:

1. **co-op-translator.yml** - Automatický překlad do více než 50 jazyků
2. **welcome-issue.yml** - Přivítání nových autorů issue
3. **welcome-pr.yml** - Přivítání nových přispěvatelů pull requestů

### Nasazení

Toto je vzdělávací repozitář - žádný proces nasazení není potřeba. Uživatelé:
1. Forkují nebo klonují repozitář
2. Spouští notebooky lokálně nebo v GitHub Codespaces
3. Učí se modifikací a experimentováním pomocí ukázek

## Pravidla pro pull requesty

### Před odesláním

1. **Otestujte vaše změny:**
   - Kompletně spusťte ovlivněné notebooky
   - Ověřte, že všechny buňky proběhnou bez chyb
   - Zkontrolujte, že výstupy odpovídají očekáváním

2. **Aktualizace dokumentace:**
   - Aktualizujte README.md pokud přidáváte nové koncepty
   - Přidejte komentáře v notebookech pro složitější kód
   - Ujistěte se, že markdown buňky vysvětlují účel

3. **Změny souborů:**
   - Nezasílejte `.env` soubory (používejte `.env.example`)
   - Nezasílejte adresáře `venv/` nebo `__pycache__/`
   - Zachovejte výstupy notebooků, pokud demonstrují koncepty
   - Odstraňte dočasné soubory a záložní notebooky (`*-backup.ipynb`)

### Formát názvu PR

Používejte popisné názvy:
- `[Lesson-XX] Přidat nový příklad pro <koncept>`
- `[Fix] Opravit překlep v README lekce-XX`
- `[Update] Vylepšit ukázku kódu v lekci-XX`
- `[Docs] Aktualizovat instrukce nastavení`

### Požadované kontroly

- Notebooky musí bez chyb projít spuštěním
- README soubory musí být jasné a přesné
- Dodržujte stávající vzory kódu v repozitáři
- Zachovejte konzistenci s ostatními lekcemi

## Další poznámky

### Časté problémy

1. **Nesoulad verze Python:**
   - Používejte Python 3.12 a vyšší
   - Některé balíčky nemusí fungovat na starších verzích
   - Použijte `python3 -m venv` pro explicitní nastavení verze

2. **Proměnné prostředí:**
   - Vždy vytvořte `.env` z `.env.example`
   - Neblokujte `.env` do verzovacího systému (je v `.gitignore`)
   - GitHub token musí mít správná oprávnění

3. **Konflikty balíčků:**
   - Používejte čisté virtuální prostředí
   - Instalujte přes `requirements.txt`, ne jednotlivé balíčky
   - Některé notebooky mohou vyžadovat další balíčky uvedené v markdown buňkách

4. **Azure služby:**
   - Azure AI služby vyžadují aktivní aktivní předplatné
   - Některé funkce jsou regionálně omezeny
   - Bezplatná vrstva platí pro GitHub Models

### Doporučená výuka

Doporučené pořadí lekcí:
1. **00-course-setup** - Začněte zde s nastavením prostředí
2. **01-intro-to-ai-agents** - Pochopení základů AI agentů
3. **02-explore-agentic-frameworks** - Seznamte se s různými frameworky
4. **03-agentic-design-patterns** - Hlavní návrhové vzory
5. Pokračujte seřazeně podle čísel lekcí

### Výběr frameworku

Volba frameworku podle cíle:
- **Výuka/Prototypování**: Semantic Kernel + GitHub Models (zdarma)
- **Multi-agentní systémy**: AutoGen
- **Nejnovější funkce**: Microsoft Agent Framework (MAF)
- **Produkční nasazení**: Azure AI Agent Service

### Kde hledat pomoc

- Připojte se k [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Prohlédněte si README soubory lekcí pro specifické pokyny
- Zkontrolujte hlavní [README.md](./README.md) pro přehled kurzu
- Odkažte na [Course Setup](./00-course-setup/README.md) pro podrobné instrukce

### Přispívání

Toto je otevřený vzdělávací projekt. Přispěvatelé vítáni:
- Vylepšení příkladů kódu
- Opravy překlepů a chyb
- Přidání vysvětlujících komentářů
- Návrhy nových témat lekcí
- Překlady do dalších jazyků

Viz [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) pro aktuální potřeby.

## Kontext specifický pro projekt

### Podpora více jazyků

Tento repozitář používá automatizovaný překladový systém:
- Podpora více než 50 jazyků
- Překlady v adresářích `/translations/<lang-code>/`
- GitHub Actions workflow zajišťuje aktualizace překladů
- Zdrojové soubory jsou v angličtině v kořenovém adresáři repozitáře

### Struktura lekcí

Každá lekce má konzistentní vzor:
1. Náhled videa s odkazem
2. Psaný obsah lekce (README.md)
3. Ukázky kódu v několika frameworcích
4. Výukové cíle a požadavky
5. Dodatečné vzdělávací zdroje s odkazy

### Pojmenování ukázek kódu

Formát: `<číslo-lekce>-<název-frameworku>.ipynb`
- `04-semantic-kernel.ipynb` - Lekce 4, Semantic Kernel
- `07-autogen.ipynb` - Lekce 7, AutoGen
- `14-python-agent-framework.ipynb` - Lekce 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lekce 14, MAF .NET

### Speciální adresáře

- `translated_images/` - Přeložené obrázky pro překlady
- `images/` - Originální obrázky pro anglický obsah
- `.devcontainer/` - Konfigurace VS Code vývojového kontejneru
- `.github/` - GitHub Actions workflow a šablony

### Závislosti

Klíčové balíčky z `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen framework
- `semantic-kernel` - Semantic Kernel framework
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI služby
- `azure-search-documents` - Azure AI Search integrace
- `chromadb` - Vektorová databáze pro RAG příklady
- `chainlit` - Chat UI framework
- `browser_use` - Automatizace prohlížeče pro agenty
- `mcp[cli]` - Podpora Model Context Protocolu
- `mem0ai` - Správa paměti pro agenty

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Prohlášení o vyloučení odpovědnosti**:  
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). Přestože usilujeme o co nejvyšší přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Originální dokument v jeho rodném jazyce by měl být považován za závazný zdroj. Pro zásadní informace se doporučuje využít profesionální lidský překlad. Nepřebíráme odpovědnost za jakékoliv nedorozumění nebo nesprávné výklady vzniklé použitím tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->