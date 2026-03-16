# AGENTS.md

## Pregled projekta

Ovaj repozitorij sadrži "AI Agents for Beginners" - sveobuhvatan edukacijski tečaj koji podučava sve potrebno za izgradnju AI agenata. Tečaj se sastoji od 15+ lekcija koje pokrivaju osnove, dizajnerske obrasce, okvire i produkcijsko postavljanje AI agenata.

**Ključne tehnologije:**
- Python 3.12+
- Jupyter bilježnice za interaktivno učenje
- AI okviri: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI usluge: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (dostupan besplatni sloj)

**Arhitektura:**
- Struktura temeljena na lekcijama (direktoriji 00-15+)
- Svaka lekcija sadrži: README dokumentaciju, primjere koda (Jupyter bilježnice) i slike
- Podrška za više jezika putem automatiziranog sustava za prijevod
- Više opcija okvira po lekciji (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Komande za postavljanje

### Preduvjeti
- Python 3.12 ili noviji
- GitHub račun (za GitHub Models - besplatni sloj)
- Azure pretplata (opcionalno, za Azure AI usluge)

### Početno postavljanje

1. **Klonirajte ili forkajte repozitorij:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ILI
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Kreirajte i aktivirajte Python virtualno okruženje:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Na Windowsu: venv\Scripts\activate
   ```

3. **Instalirajte ovisnosti:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Postavite varijable okoline:**
   ```bash
   cp .env.example .env
   # Uredi .env s API ključevima i endpointima
   ```

### Potrebne varijable okoline

Za **GitHub Models (Free)**:
- `GITHUB_TOKEN` - Osobni pristupni token s GitHub-a

Za **Azure AI usluge** (opcionalno):
- `PROJECT_ENDPOINT` - Microsoft Foundry project endpoint
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API ključ
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI endpoint URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Ime deploymenta za chat model
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Ime deploymenta za embeddings
- Dodatna Azure konfiguracija kao u `.env.example`

## Razvojni tijek

### Pokretanje Jupyter bilježnica

Svaka lekcija sadrži više Jupyter bilježnica za različite okvire:

1. **Pokrenite Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigirajte do direktorija lekcije** (npr., `01-intro-to-ai-agents/code_samples/`)

3. **Otvorite i pokrenite bilježnice:**
   - `*-semantic-kernel.ipynb` - Korištenje Semantic Kernel okvira
   - `*-autogen.ipynb` - Korištenje AutoGen okvira
   - `*-python-agent-framework.ipynb` - Korištenje Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Korištenje Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Korištenje Azure AI Agent Service

### Rad s različitim okvirima

**Semantic Kernel + GitHub Models:**
- Dostupan besplatni sloj s GitHub računom
- Dobar za učenje i eksperimentiranje
- Uzorak datoteke: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Dostupan besplatni sloj s GitHub računom
- Sposobnosti orkestracije višestrukih agenata
- Uzorak datoteke: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Najnoviji okvir od Microsofta
- Dostupan u Pythonu i .NET-u
- Uzorak datoteke: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Potrebna Azure pretplata
- Značajke spremne za produkciju
- Uzorak datoteke: `*-azureaiagent.ipynb`

## Upute za testiranje

Ovo je edukacijski repozitorij s primjerima koda, a ne produkcijski kod s automatiziranim testovima. Za provjeru vaše postavke i promjena:

### Ručno testiranje

1. **Testirajte Python okruženje:**
   ```bash
   python --version  # Treba biti 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Testirajte izvođenje bilježnica:**
   ```bash
   # Pretvori bilježnicu u skriptu i pokreni (uvozi za testove)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Provjerite varijable okoline:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Pokretanje pojedinačnih bilježnica

Otvorite bilježnice u Jupyteru i izvršavajte ćelije redom. Svaka bilježnica je samostalna i uključuje:
- Izjave za uvoz (import statements)
- Učitavanje konfiguracije
- Primjer implementacija agenata
- Očekivane izlaze u markdown ćelijama

## Stil koda

### Python konvencije

- **Verzija Pythona**: 3.12+
- **Stil koda**: Slijedite standardne Python PEP 8 konvencije
- **Bilježnice**: Koristite jasne markdown ćelije za objašnjenje koncepata
- **Uvozi**: Grupirajte po standardnoj biblioteci, third-party i lokalnim uvozima

### Konvencije za Jupyter bilježnice

- Uključite opisne markdown ćelije prije kodnih ćelija
- Dodajte primjere izlaza u bilježnicama za referencu
- Koristite jasne nazive varijabli koji odgovaraju konceptima lekcije
- Održavajte linearni redoslijed izvršavanja bilježnica (ćelija 1 → 2 → 3...)

### Organizacija datoteka

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

## Izgradnja i distribucija

### Izgradnja dokumentacije

Ovaj repozitorij koristi Markdown za dokumentaciju:
- README.md datoteke u svakom folderu lekcije
- Glavni README.md u korijenu repozitorija
- Automatizirani sustav za prijevod putem GitHub Actions

### CI/CD pipeline

Nalazi se u `.github/workflows/`:

1. **co-op-translator.yml** - Automatski prijevod na 50+ jezika
2. **welcome-issue.yml** - Pozdravlja autore novih issue-a
3. **welcome-pr.yml** - Pozdravlja suradnike prijavljenih pull requestova

### Distribucija

Ovo je edukacijski repozitorij - nema proces distribucije. Korisnici:
1. Forkaju ili kloniraju repozitorij
2. Pokreću bilježnice lokalno ili u GitHub Codespaces
3. Uče modificirajući i eksperimentirajući s primjerima

## Smjernice za pull requestove

### Prije slanja

1. **Testirajte svoje promjene:**
   - Potpuno pokrenite pogođene bilježnice
   - Provjerite da se sve ćelije izvršavaju bez grešaka
   - Provjerite jesu li izlazi prikladni

2. **Ažuriranja dokumentacije:**
   - Ažurirajte README.md ako dodajete nove koncepte
   - Dodajte komentare u bilježnice za složenije dijelove koda
   - Osigurajte da markdown ćelije objašnjavaju svrhu

3. **Promjene datoteka:**
   - Izbjegavajte commitanje `.env` datoteka (koristite `.env.example`)
   - Nemojte committati `venv/` ili `__pycache__/` direktorije
   - Zadržite izlaze bilježnica kada demonstriraju koncepte
   - Uklonite privremene datoteke i backup bilježnice (`*-backup.ipynb`)

### Format naslova PR-a

Koristite opisne naslove:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Correct typo in lesson-XX README`
- `[Update] Improve code sample in lesson-XX`
- `[Docs] Update setup instructions`

### Potrebne provjere

- Bilježnice bi se trebale izvršavati bez grešaka
- README datoteke trebaju biti jasne i točne
- Slijedite postojeće obrasce koda u repozitoriju
- Održavajte dosljednost s ostalim lekcijama

## Dodatne bilješke

### Uobičajene zamke

1. **Neslaganje verzije Pythona:**
   - Osigurajte da koristite Python 3.12+
   - Neki paketi možda neće raditi s starijim verzijama
   - Koristite `python3 -m venv` za eksplicitno specificiranje verzije Pythona

2. **Varijable okoline:**
   - Uvijek kreirajte `.env` iz `.env.example`
   - Nemojte committati `.env` datoteku (nalazi se u `.gitignore`)
   - GitHub token treba odgovarajuće dozvole

3. **Sukobi paketa:**
   - Koristite svježe virtualno okruženje
   - Instalirajte iz `requirements.txt` umjesto pojedinačnih paketa
   - Neke bilježnice mogu zahtijevati dodatne pakete navedene u njihovim markdown ćelijama

4. **Azure usluge:**
   - Azure AI usluge zahtijevaju aktivnu pretplatu
   - Neke značajke su specifične za regiju
   - Ograničenja besplatnog sloja primjenjuju se na GitHub Models

### Put učenja

Preporučeni napredak kroz lekcije:
1. **00-course-setup** - Počnite ovdje za postavljanje okoline
2. **01-intro-to-ai-agents** - Razumite osnove AI agenata
3. **02-explore-agentic-frameworks** - Saznajte o različitim okvirima
4. **03-agentic-design-patterns** - Glavni dizajnerski obrasci
5. Nastavite kroz numerirane lekcije redom

### Odabir okvira

Odaberite okvir prema svojim ciljevima:
- **Učenje/Prototipiranje**: Semantic Kernel + GitHub Models (besplatno)
- **Sustavi s više agenata**: AutoGen
- **Najnovije značajke**: Microsoft Agent Framework (MAF)
- **Produkcijsko postavljanje**: Azure AI Agent Service

### Dobivanje pomoći

- Pridružite se Microsoft Foundry zajednici na Discordu: [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Pregledajte README datoteke lekcija za specifične smjernice
- Provjerite glavni [README.md](./README.md) za pregled tečaja
- Pogledajte [Course Setup](./00-course-setup/README.md) za detaljne upute za postavljanje

### Doprinos

Ovo je otvoreni edukacijski projekt. Doprinosi su dobrodošli:
- Poboljšajte primjere koda
- Ispravite tipfeler ili greške
- Dodajte pojašnjavajuće komentare
- Predložite nove teme lekcija
- Prevedite na dodatne jezike

Pogledajte [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) za trenutne potrebe.

## Kontekst specifičan za projekt

### Podrška za više jezika

Ovaj repozitorij koristi automatizirani sustav za prijevod:
- Podržano 50+ jezika
- Prijevodi u direktorijima `/translations/<lang-code>/`
- GitHub Actions workflow upravlja ažuriranjima prijevoda
- Izvorne datoteke su na engleskom u korijenu repozitorija

### Struktura lekcije

Svaka lekcija slijedi dosljedan obrazac:
1. Video thumbnail s linkom
2. Pisani sadržaj lekcije (README.md)
3. Primjeri koda u više okvira
4. Ciljevi učenja i preduvjeti
5. Dodatni resursi za učenje povezani

### Imenovanje primjera koda

Format: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Lekcija 4, Semantic Kernel
- `07-autogen.ipynb` - Lekcija 7, AutoGen
- `14-python-agent-framework.ipynb` - Lekcija 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lekcija 14, MAF .NET

### Posebni direktoriji

- `translated_images/` - Lokalizirane slike za prijevode
- `images/` - Originalne slike za engleski sadržaj
- `.devcontainer/` - Konfiguracija VS Code development containera
- `.github/` - GitHub Actions workflows i predlošci

### Ovisnosti

Ključni paketi iz `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen okvir
- `semantic-kernel` - Semantic Kernel okvir
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI usluge
- `azure-search-documents` - Integracija Azure AI Search
- `chromadb` - Vektorska baza podataka za RAG primjere
- `chainlit` - Chat UI okvir
- `browser_use` - Automatizacija preglednika za agente
- `mcp[cli]` - Podrška za Model Context Protocol
- `mem0ai` - Upravljanje memorijom za agente

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Odricanje odgovornosti:
Ovaj je dokument preveden pomoću AI usluge prevođenja Co-op Translator (https://github.com/Azure/co-op-translator). Iako težimo točnosti, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za kritične informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakve nesporazume ili pogrešna tumačenja koja proizlaze iz uporabe ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->