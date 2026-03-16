# AGENTS.md

## Pregled projekta

Ta repozitorij vsebuje "AI agente za začetnike" - obsežen izobraževalni tečaj, ki uči vse, kar je potrebno za izdelavo AI agentov. Tečaj obsega več kot 15 lekcij, ki pokrivajo osnove, oblikovne vzorce, ogrodja in uvajanje v produkcijo AI agentov.

**Ključne tehnologije:**
- Python 3.12+
- Jupyter zvezki za interaktivno učenje
- AI ogrodja: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI storitve: Microsoft Foundry, Azure AI Agent Service
- Tržnica modelov GitHub (na voljo brezplačni nivo)

**Arhitektura:**
- Struktura na osnovi lekcij (imeniki 00-15+)
- Vsaka lekcija vsebuje: dokumentacijo README, vzorce kode (Jupyter zvezke) in slike
- Večjezična podpora preko avtomatiziranega prevajalskega sistema
- Več možnosti ogrodij za vsako lekcijo (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Ukazi za namestitev

### Zahteve
- Python 3.12 ali novejši
- GitHub račun (za GitHub modele - brezplačni nivo)
- Azure naročnina (neobvezno, za Azure AI storitve)

### Začetna namestitev

1. **Klonirajte ali forkajte repozitorij:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ALI
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Ustvarite in aktivirajte Python virtualno okolje:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # V sistemu Windows: venv\Scripts\activate
   ```

3. **Namestite odvisnosti:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Nastavite sistemske spremenljivke:**
   ```bash
   cp .env.example .env
   # Uredite .env z vašimi API ključi in končnimi točkami
   ```

### Zahtevane sistemske spremenljivke

Za **GitHub modele (brezplačno)**:
- `GITHUB_TOKEN` - osebni dostopni žeton iz GitHub-a

Za **Azure AI storitve** (neobvezno):
- `PROJECT_ENDPOINT` - Microsoft Foundry projektna točka
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API ključ
- `AZURE_OPENAI_ENDPOINT` - URL končne točke Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - ime uvedbe za klepetalni model
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - ime uvedbe za upodobitve
- Dodatne nastavitve Azure kot prikazano v `.env.example`

## Delovni potek razvoja

### Zagon Jupyter zvezkov

Vsaka lekcija vsebuje več Jupyter zvezkov za različna ogrodja:

1. **Zaženi Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Pomaknite se do imenika lekcije** (npr. `01-intro-to-ai-agents/code_samples/`)

3. **Odprite in zaženite zvezke:**
   - `*-semantic-kernel.ipynb` - uporaba ogrodja Semantic Kernel
   - `*-autogen.ipynb` - uporaba ogrodja AutoGen
   - `*-python-agent-framework.ipynb` - uporaba Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - uporaba Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - uporaba Azure AI Agent Service

### Delo z različnimi ogrodji

**Semantic Kernel + GitHub modeli:**
- Brezplačni nivo z GitHub računom
- Dobro za učenje in eksperimentiranje
- Vzorec imena datoteke: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub modeli:**
- Brezplačni nivo z GitHub računom
- Možnosti orkestracije več agentov
- Vzorec imena datoteke: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Najnovejše ogrodje Microsofta
- Na voljo v Python in .NET različici
- Vzorec imena datoteke: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Zahteva naročnino Azure
- Funkcije, primerne za produkcijo
- Vzorec imena datoteke: `*-azureaiagent.ipynb`

## Navodila za testiranje

To je izobraževalni repozitorij z vzorčno kodo in ne produkcijska koda z avtomatiziranimi testi. Za preverjanje nastavitve in sprememb:

### Ročno testiranje

1. **Testirajte Python okolje:**
   ```bash
   python --version  # Mora biti 3.12 ali novejša
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Preizkusite zagon zvezkov:**
   ```bash
   # Pretvori zvezek v skripto in zaženi (preizkusi uvoze)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Preverite sistemske spremenljivke:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Zagon posameznih zvezkov

Odprite zvezke v Jupyterju in po vrsti izvajajte celice. Vsak zvezek je samostojen in vsebuje:
- Izjave za uvoz
- Nalaganje nastavitev
- Primerne implementacije agentov
- Pričakovane izhode v markdown celicah

## Stil kode

### Python konvencije

- **Različica Pythona:** 3.12+
- **Stil kode:** sledite standardnim PEP 8 konvencijam za Python
- **Zvezki:** uporabite jasne markdown celice za razlago konceptov
- **Uvozi:** združujte po skupinah: standardna knjižnica, tretje osebe, lokalni uvozi

### Konvencije za Jupyter zvezke

- Vključite opisne markdown celice pred celicami s kodo
- Dodajte primere izhodov za referenco
- Uporabljajte jasna imena spremenljivk, ki ustrezajo konceptom lekcije
- Ohranjajte linearni vrstni red izvajanja zvezka (celica 1 → 2 → 3...)

### Organizacija datotek

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

## Gradnja in uvajanje

### Gradnja dokumentacije

Ta repozitorij uporablja Markdown za dokumentacijo:
- Datoteke README.md v vsakem imeniku lekcije
- Glavna README.md v korenu repozitorija
- Avtomatiziran prevajalski sistem preko GitHub Actions

### CI/CD potek

Nahaja se v `.github/workflows/`:

1. **co-op-translator.yml** - avtomatski prevod v več kot 50 jezikov
2. **welcome-issue.yml** - pozdrav novim ustvarjalcem zahtevkov
3. **welcome-pr.yml** - pozdrav novim prispevkom pull request

### Uvajanje

To je izobraževalni repozitorij - brez procesa uvajanja. Uporabniki:
1. Forkajo ali klonirajo repozitorij
2. Zaženejo zvezke lokalno ali v GitHub Codespaces
3. Se učijo z modifikacijo in eksperimentiranjem primerov

## Smernice za Pull Request-e

### Pred oddajo

1. **Preizkusite svoje spremembe:**
   - Zaženite vse zvezke, ki so vplivani
   - Preverite, da se vse celice izvršijo brez napak
   - Preverite, ali so izhodi primerni

2. **Posodobitve dokumentacije:**
   - Posodobite README.md, če dodajate nove koncepte
   - Dodajte komentarje v zapletene dele kode v zvezkih
   - Poskrbite, da markdown celice razložijo namen

3. **Spremembe datotek:**
   - Izogibajte se commitu `.env` datotek (uporabite `.env.example`)
   - Ne commiteajte imenikov `venv/` ali `__pycache__/`
   - Ohranjajte izhode zvezkov, če prikazujejo koncepte
   - Odstranite začasne datoteke in varnostne kopije zvezkov (`*-backup.ipynb`)

### Oblika naslova PR-ja

Uporabite opisne naslove:
- `[Lesson-XX] Dodaj nov primer za <koncept>`
- `[Fix] Popravi tipkarsko napako v lesson-XX README`
- `[Update] Izboljšaj primer kode v lesson-XX`
- `[Docs] Posodobi navodila za namestitev`

### Potrebne kontrole

- Zvezki naj se izvajajo brez napak
- Datoteke README naj bodo jasne in natančne
- Sledite obstoječim vzorcem kode v repozitoriju
- Ohranjajte skladnost z ostalimi lekcijami

## Dodatne opombe

### Pogoste pasti

1. **Neujemanje različic Pythona:**
   - Poskrbite, da uporabljate Python 3.12 ali novejši
   - Nekateri paketi ne delujejo z starejšimi različicami
   - Uporabite `python3 -m venv` za eksplicitno določitev verzije

2. **Sistemske spremenljivke:**
   - Vedno ustvarite `.env` iz `.env.example`
   - Ne commiteajte `.env` datoteke (je v `.gitignore`)
   - GitHub žeton mora imeti ustrezna dovoljenja

3. **Konflikti paketov:**
   - Uporabite sveže virtualno okolje
   - Namestite preko `requirements.txt` namesto posameznih paketov
   - Nekateri zvezki zahtevajo dodatne pakete, navedene v njihovih markdown celicah

4. **Azure storitve:**
   - Azure AI storitve zahtevajo aktivno naročnino
   - Nekatere funkcije so specifične za regijo
   - Brezplačni nivo velja za GitHub modele

### Pot učenja

Priporočena zaporedna izvedba lekcij:
1. **00-course-setup** - za začetek s pripravo okolja
2. **01-intro-to-ai-agents** - razumevanje osnov AI agentov
3. **02-explore-agentic-frameworks** - spoznavanje različnih ogrodij
4. **03-agentic-design-patterns** - osnovni oblikovni vzorci
5. Nadaljujte po številkah lekcij zaporedoma

### Izbira ogrodja

Izberite ogrodje glede na vaše cilje:
- **Učenje/prototipiranje:** Semantic Kernel + GitHub modeli (brezplačno)
- **Več-agentni sistemi:** AutoGen
- **Najnovejše funkcije:** Microsoft Agent Framework (MAF)
- **Produkcijsko uvajanje:** Azure AI Agent Service

### Kje iskati pomoč

- Pridružite se [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Preberite README datoteke lekcij za specifična navodila
- Poglejte glavni [README.md](./README.md) za pregled tečaja
- Oglejte si [Course Setup](./00-course-setup/README.md) za podrobna navodila za namestitev

### Prispevanje

To je odprt izobraževalni projekt. Prispevki so dobrodošli:
- Izboljšanje primerov kode
- Popravljanje tipkarskih napak ali napak
- Dodajanje razlagajočih komentarjev
- Predlaganje novih tem lekcij
- Prevajanje v dodatne jezike

Trenutne potrebe si oglejte na [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues).

## Kontekst specifičen za projekt

### Večjezična podpora

Ta repozitorij uporablja avtomatiziran prevajalski sistem:
- Podpora za več kot 50 jezikov
- Prevodi v imenikih `/translations/<lang-code>/`
- Potek dela GitHub Actions skrbi za posodobitve prevodov
- Izvorne datoteke so v angleščini v korenu repozitorija

### Struktura lekcije

Vsaka lekcija sledi doslednemu vzorcu:
1. Vidni posnetek videa z povezavo
2. Pisane vsebine lekcije (README.md)
3. Kode primere v več ogrodjih
4. Cilji učenja in predznanja
5. Dodatni učni viri povezani

### Poimenovanje vzorcev kode

Format: `<stevilka-lekcije>-<ime-ogrodja>.ipynb`
- `04-semantic-kernel.ipynb` - Lekcija 4, Semantic Kernel
- `07-autogen.ipynb` - Lekcija 7, AutoGen
- `14-python-agent-framework.ipynb` - Lekcija 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lekcija 14, MAF .NET

### Posebni imeniki

- `translated_images/` - lokalizirane slike za prevode
- `images/` - izvirne slike za angleško vsebino
- `.devcontainer/` - konfiguracija razvojnega kontejnerja za VS Code
- `.github/` - GitHub Actions poteki dela in predloge

### Odvisnosti

Ključni paketi iz `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen ogrodje
- `semantic-kernel` - Semantic Kernel ogrodje
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI storitve
- `azure-search-documents` - Azure AI Search integracija
- `chromadb` - vektorska baza podatkov za RAG primere
- `chainlit` - ogrodje za klepetalni UI
- `browser_use` - avtomatizacija brskalnika za agente
- `mcp[cli]` - podpora za Model Context Protocol
- `mem0ai` - upravljanje spomina za agente

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Omejitev odgovornosti**:
To besedilo je bilo prevedeno z uporabo storitve za strojno prevajanje [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da lahko avtomatizirani prevodi vsebujejo napake ali netočnosti. Izvirni dokument v njegovem izvirnem jeziku naj velja za avtoritativni vir. Za pomembne informacije priporočamo strokovni človeški prevod. Nismo odgovorni za morebitna nesporazume ali napačne razlage, ki izhajajo iz uporabe tega prevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->