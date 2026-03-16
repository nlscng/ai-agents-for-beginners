# AGENTS.md

## Projekto apžvalga

Šiame saugykloje yra „AI Agentai pradedantiesiems“ – išsamus mokomasis kursas, apimantis viską, ko reikia AI agentų kūrimui. Kursą sudaro daugiau nei 15 pamokų, aptariančių pagrindus, dizaino šablonus, karkasus ir AI agentų diegimą gamyboje.

**Pagrindinės technologijos:**
- Python 3.12+
- Jupyter užrašų knygelės interaktyviam mokymuisi
- AI karkasai: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI paslaugos: Microsoft Foundry, Azure AI Agent Service
- GitHub Modelių turgus (yra nemokamas lygis)

**Architektūra:**
- Pamokų struktūra (00-15+ katalogai)
- Kiekvienoje pamokoje yra: README dokumentacija, kodo pavyzdžiai (Jupyter užrašų knygelės) ir paveikslėliai
- Daugiakalbė paramą užtikrina automatinė vertimo sistema
- Kiekvienai pamokai galimi keli karkasai (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Diegimo komandos

### Reikalavimai
- Python 3.12 ar naujesnė versija
- GitHub paskyra (GitHub modeliams – nemokamas lygis)
- Azure prenumerata (neprivaloma, Azure AI paslaugoms)

### Pradinė sąranka

1. **Klonuoti arba įforkinti saugyklą:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ARBA
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Sukurti ir aktyvuoti Python virtualią aplinką:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Windows sistemoje: venv\Scripts\activate
   ```

3. **Įdiegti priklausomybes:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Nustatyti aplinkos kintamuosius:**
   ```bash
   cp .env.example .env
   # Redaguokite .env su savo API raktais ir galiniais taškais
   ```

### Būtini aplinkos kintamieji

GitHub modeliams (nemokamai):
- `GITHUB_TOKEN` – Asmeninis prieigos žetonas iš GitHub

Azure AI paslaugoms (neprivaloma):
- `PROJECT_ENDPOINT` – Microsoft Foundry projekto pabaigos taškas
- `AZURE_OPENAI_API_KEY` – Azure OpenAI API raktas
- `AZURE_OPENAI_ENDPOINT` – Azure OpenAI galinis taškas URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` – Pokalbių modelio diegimo pavadinimas
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` – Įterpimų diegimo pavadinimas
- Papildoma Azure konfigūracija nurodyta `.env.example`

## Kūrimo darbo eiga

### Jupyter užrašų knygelių paleidimas

Kiekvienoje pamokoje yra keli Jupyter užrašų knygelių pavyzdžiai skirtingiems karkasams:

1. **Paleisti Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Eiti į pamokos katalogą** (pvz., `01-intro-to-ai-agents/code_samples/`)

3. **Atidaryti ir vykdyti užrašų knygeles:**
   - `*-semantic-kernel.ipynb` – naudoja Semantic Kernel karkasą
   - `*-autogen.ipynb` – naudoja AutoGen karkasą
   - `*-python-agent-framework.ipynb` – naudoja Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` – naudoja Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` – naudoja Azure AI Agent Service

### Darbas su skirtingais karkasais

**Semantic Kernel + GitHub Modeliai:**
- Nemokamas lygis su GitHub paskyra
- Puikiai tinka mokymuisi ir eksperimentams
- Failų pavadinimai: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Modeliai:**
- Nemokamas lygis su GitHub paskyra
- Multi-agentų koordinacijos galimybės
- Failų pavadinimai: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Naujausias Microsoft karkasas
- Pasiekiamas Python ir .NET
- Failų pavadinimai: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Reikalinga Azure prenumerata
- Gamybinio lygio funkcijos
- Failų pavadinimai: `*-azureaiagent.ipynb`

## Testavimo instrukcijos

Tai yra mokomasis saugykla su pavyzdiniu kodu, o ne gamybinis kodas su automatizuotais testais. Norint patikrinti diegimą ir pakeitimus:

### Rankinis testavimas

1. **Patikrinkite Python aplinką:**
   ```bash
   python --version  # Turi būti 3.12 ar naujesnė versija
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Patikrinkite užrašų knygelių vykdymą:**
   ```bash
   # Konvertuoti užrašų knygelę į scenarijų ir paleisti (testuoja importus)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Patikrinkite aplinkos kintamuosius:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Vykdyti atskiras užrašų knygeles

Atidarykite užrašų knygeles Jupyter ir paleiskite langelius iš eilės. Kiekviena užrašų knygelė yra savarankiška ir turi:
- Importo sakinius
- Konfigūracijos užkrovimą
- Pavyzdinius agentų įgyvendinimus
- Laukiamus rezultatus markdown langeliuose

## Kodo stilius

### Python konvencijos

- **Python versija**: 3.12+
- **Kodo stilius**: Laikykitės standartinių Python PEP 8 konvencijų
- **Užrašų knygelės**: Naudokite aiškius markdown langelius koncepcijoms paaiškinti
- **Importai**: Grupėmis pagal standartinę biblioteką, trečiųjų šalių ir vietinius importus

### Jupyter užrašų knygelių konvencijos

- Įtraukite aprašomuosius markdown langelius prieš kodo langelius
- Užrašų knygelėse pateikite rezultatų pavyzdžius
- Naudokite aiškius kintamųjų pavadinimus, atitinkančius pamokos sąvokas
- Laikykitės linijinio vykdymo eiliškumo (langelis 1 → 2 → 3...)

### Failų organizavimas

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

## Kompiliavimas ir diegimas

### Dokumentacijos kūrimas

Ši saugykla naudoja Markdown dokumentacijai:
- README.md failai kiekviename pamokos kataloge
- Pagrindinis README.md saugyklos šaknyje
- Automatinė vertimo sistema per GitHub Actions

### CI/CD Tiekimas

Vietoje `.github/workflows/`:

1. **co-op-translator.yml** – automatinis vertimas į daugiau nei 50 kalbų
2. **welcome-issue.yml** – pasveikina naujus issue kūrėjus
3. **welcome-pr.yml** – pasveikina naujus pull request sėkėjus

### Diegimas

Tai mokomoji saugykla – diegimo proceso nėra. Vartotojai:
1. Forkina arba klonuoja saugyklą
2. Vykdo užrašų knygeles vietoje arba GitHub Codespaces
3. Mokosi keisdami ir eksperimentuodami su pavyzdžiais

## Pull Request gairės

### Prieš pateikiant

1. **Išbandykite savo pakeitimus:**
   - Atlikite paveiktų užrašų knygelių visas eilutes
   - Patikrinkite, kad visos eilutės vyksta be klaidų
   - Įsitikinkite, kad rezultatai yra tinkami

2. **Dokumentacijos atnaujinimai:**
   - Atnaujinkite README.md, jei pridedate naujų sąvokų
   - Įrašykite komentarus sudėtingame kode
   - Patikrinkite, kad markdown langeliai paaiškina paskirtį

3. **Failų keitimai:**
   - Venkite `.env` failų įsipareigojimo (naudokite `.env.example`)
   - Nekomituokite `venv/` ar `__pycache__/` katalogų
   - Laikykite užrašų knygelių išvestis, jei jos demonstruoja koncepcijas
   - Pašalinkite laikinuosius failus ir atsargines užrašų knygeles (`*-backup.ipynb`)

### PR pavadinimo formatas

Naudokite aprašomuosius pavadinimus:
- `[Lesson-XX] Pridėti naują pavyzdį <sąvokai>`
- `[Fix] Pataisyti klaidą lesson-XX README`
- `[Update] Patobulinti kodo pavyzdį lesson-XX`
- `[Docs] Atnaujinti diegimo instrukcijas`

### Būtini patikrinimai

- Užrašų knygelės vykdomos be klaidų
- README failai aiškūs ir tikslūs
- Laikytis saugyklos egzistuojančių kodo šablonų
- Išlaikyti nuoseklumą su kitomis pamokomis

## Papildomos pastabos

### Dažniausios problemos

1. **Python versijos nesuderinamumas:**
   - Naudokite Python 3.12+
   - Kai kurios bibliotekos neveikia su senesnėmis versijomis
   - Naudokite `python3 -m venv` norint aiškiai nurodyti Python versiją

2. **Aplinkos kintamieji:**
   - Visada sukurkite `.env` iš `.env.example`
   - Nekomituokite `.env` failo (jis įtrauktas į `.gitignore`)
   - GitHub tokenui reikalingos tinkamos teisės

3. **Paketo konfliktai:**
   - Naudokite švarią virtualią aplinką
   - Įdiekite per `requirements.txt`, o ne atskirus paketus
   - Kai kurios užrašų knygelės gali reikėti papildomų paketų, nurodytų jų markdown langeliuose

4. **Azure paslaugos:**
   - Azure AI paslaugoms reikalinga aktyvi prenumerata
   - Kai kurios funkcijos priklauso nuo regiono
   - GitHub modeliams galioja nemokamo lygio apribojimai

### Mokymosi kelias

Rekomenduojamas pamokų eiliškumas:
1. **00-course-setup** – pradėkite nuo aplinkos konfigūracijos
2. **01-intro-to-ai-agents** – supraskite AI agentų pagrindus
3. **02-explore-agentic-frameworks** – susipažinkite su skirtingais karkasais
4. **03-agentic-design-patterns** – pagrindiniai dizaino šablonai
5. Toliau darbinės pamokos numeriu seka

### Karkaso pasirinkimas

Pasirinkite karkasą pagal savo tikslus:
- **Mokymasis/Prototipavimas**: Semantic Kernel + GitHub Modeliai (nemokama)
- **Multi-agentų sistemos**: AutoGen
- **Naujausios funkcijos**: Microsoft Agent Framework (MAF)
- **Gamybinis diegimas**: Azure AI Agent Service

### Pagalba

- Prisijunkite prie [Microsoft Foundry bendruomenės Discord](https://aka.ms/ai-agents/discord)
- Peržiūrėkite pamokų README failus specifinėms instrukcijoms
- Žiūrėkite pagrindinį [README.md](./README.md) kurso apžvalgai
- Žr. [Course Setup](./00-course-setup/README.md) išsamiai pradžiai

### Indėlis

Tai atviras mokomasis projektas. Kviečiame prisidėti:
- Tobulinti kodo pavyzdžius
- Taisyti klaidas ir rašybos klaidas
- Pridėti paaiškinamuosius komentarus
- Pasiūlyti naujų pamokų temų
- Versti į papildomas kalbas

Dabartinės poreikiai skelbiami [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues).

## Projekto specifinis kontekstas

### Daugiakalbė parama

Ši saugykla naudoja automatinę vertimo sistemą:
- Palaikoma daugiau nei 50 kalbų
- Vertimai saugomi `/translations/<lang-code>/` kataloguose
- Vertimo naujinimą atlieka GitHub Actions darbo eiga
- Šaltinio failai anglų kalba saugyklos šaknyje

### Pamokos struktūra

Kiekviena pamoka turi nuoseklią struktūrą:
1. Vaizdo miniatiūra su nuoroda
2. Rašytinė pamokos medžiaga (README.md)
3. Kodo pavyzdžiai keliuose karkasuose
4. Mokymosi tikslai ir reikalavimai
5. Papildomi mokymosi šaltiniai su nuorodomis

### Kodo pavyzdžių vardai

Formatas: `<pamokos-numeris>-<karkaso-pavadinimas>.ipynb`
- `04-semantic-kernel.ipynb` – 4 pamoka, Semantic Kernel
- `07-autogen.ipynb` – 7 pamoka, AutoGen
- `14-python-agent-framework.ipynb` – 14 pamoka, MAF Python
- `14-dotnet-agent-framework.ipynb` – 14 pamoka, MAF .NET

### Specialūs katalogai

- `translated_images/` – lokalizuoti paveikslėliai vertimams
- `images/` – originalūs paveikslėliai anglų kalbai
- `.devcontainer/` – VS Code kūrimo konteinerio konfigūracija
- `.github/` – GitHub Actions darbo eigos ir šablonai

### Priklausomybės

Svarbiausios priklausomybės iš `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` – AutoGen karkasas
- `semantic-kernel` – Semantic Kernel karkasas
- `agent-framework` – Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` – Azure AI paslaugos
- `azure-search-documents` – Azure AI paieškos integracija
- `chromadb` – vektorinė duomenų bazė RAG pavyzdžiams
- `chainlit` – pokalbių vartotojo sąsajos karkasas
- `browser_use` – naršyklės automatizavimas agentams
- `mcp[cli]` – Model Context Protocol palaikymas
- `mem0ai` – atminties valdymas agentams

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:  
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors stengiamės užtikrinti tikslumą, atkreipkite dėmesį, kad automatizuoti vertimai gali turėti klaidų ar netikslumų. Originalus dokumentas gimtąja kalba turi būti laikomas autentišku šaltiniu. Kritinei informacijai rekomenduojamas profesionalus žmogaus vertimas. Mes neatsakome už bet kokius nesusipratimus ar neteisingas interpretacijas, kylančias dėl šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->