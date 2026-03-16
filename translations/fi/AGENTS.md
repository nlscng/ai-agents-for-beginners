# AGENTS.md

## Projektin yleiskatsaus

Tämä repositorio sisältää "AI Agents for Beginners" - laajan opetuskursin, joka opettaa kaiken tarpeellisen tekoälyagenttien rakentamiseen. Kurssi koostuu yli 15 oppitunnista, jotka kattavat perusteet, suunnittelumallit, kehykset ja tekoälyagenttien tuotantoon käyttöönoton.

**Keskeiset teknologiat:**
- Python 3.12+
- Jupyter Notebookit interaktiiviseen oppimiseen
- Tekoälykehykset: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI -palvelut: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (ilmainen taso saatavilla)

**Arkkitehtuuri:**
- Oppituntipohjainen rakenne (00-15+ hakemistoja)
- Jokaisessa oppitunnissa: README-dokumentaatio, koodiesimerkit (Jupyter notebookit) ja kuvat
- Monikielinen tuki automatisoidun käännösjärjestelmän kautta
- Useita kehysvaihtoehtoja per oppitunti (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Asennuskäskyt

### Vaatimukset
- Python 3.12 tai uudempi
- GitHub-tili (GitHub Models - ilmainen taso)
- Azure-tilaus (valinnainen, Azure AI -palveluita varten)

### Alustus

1. **Kloonaa tai lohkaise repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # TAI
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Luo ja aktivoi Python virtuaaliympäristö:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Windowsilla: venv\Scripts\activate
   ```

3. **Asenna riippuvuudet:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Aseta ympäristömuuttujat:**
   ```bash
   cp .env.example .env
   # Muokkaa .env tiedostoa API-avaimillasi ja päätepisteilläsi
   ```

### Vaadittavat ympäristömuuttujat

GitHub Models (Ilmainen):
- `GITHUB_TOKEN` - Henkilökohtainen käyttöoikeustunnus GitHubista

Azure AI -palvelut (valinnainen):
- `PROJECT_ENDPOINT` - Microsoft Foundryn projektin päätepiste
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API -avain
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI päätepisteen URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Chat-mallin käyttöönoton nimi
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Upotusten käyttöönoton nimi
- Muita Azuren asetuksia kuten `.env.example` tiedostossa

## Kehitystyön kulku

### Jupyter Notebookien suorittaminen

Jokaisessa oppitunnissa on useita Jupyter-notebookeja eri kehyksille:

1. **Käynnistä Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Siirry oppitunnin hakemistoon** (esim. `01-intro-to-ai-agents/code_samples/`)

3. **Avaa ja suorita notebookit:**
   - `*-semantic-kernel.ipynb` - Semantic Kernel kehyksellä
   - `*-autogen.ipynb` - AutoGen kehyksellä
   - `*-python-agent-framework.ipynb` - Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Azure AI Agent Service

### Eri kehysten käyttö

**Semantic Kernel + GitHub Models:**
- Ilmainen taso GitHub-tilin kanssa
- Hyvä oppimiseen ja kokeiluun
- Tiedostokuvio: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Ilmainen taso GitHub-tilin kanssa
- Moni-agenttien orkestrointi
- Tiedostokuvio: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Microsoftin uusin kehys
- Saatavilla Python- ja .NET-versioina
- Tiedostokuvio: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Vaatii Azure-tilauksen
- Tuotantovalmiit ominaisuudet
- Tiedostokuvio: `*-azureaiagent.ipynb`

## Testausohjeet

Tämä on opetuskäyttöön tarkoitettu repositorio, jossa on esimerkkikoodia eikä automatisoituja tuotantotestejä. Tarkista asennuksesi ja muutoksesi seuraavasti:

### Manuaalinen testaus

1. **Testaa Python-ympäristö:**
   ```bash
   python --version  # Pitäisi olla 3.12 tai uudempi
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Testaa notebookin suoritus:**
   ```bash
   # Muunna muistikirja skriptiksi ja suorita (testaa tuonnit)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Varmista ympäristömuuttujat:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Yksittäisten notebookien suoritus

Avaa notebookit Jupyterissa ja suorita solut peräkkäin. Jokainen notebook on itsenäinen ja sisältää:
- Tuontilauseet
- Konfiguraation latauksen
- Esimerkkitoimivat agentit
- Odotetut tulosteet markdown-solussa

## Koodityyli

### Python-käytännöt

- **Python-versio**: 3.12+
- **Koodityyli**: Noudata Pythonin PEP 8 -standardeja
- **Notebookit**: Käytä selkeitä markdown-soluja selityksiin
- **Tuonnit**: Ryhmittele standardikirjasto, kolmannen osapuolen, paikalliset tuonnit

### Jupyter Notebook -käytännöt

- Lisää kuvaavia markdown-soluja ennen koodisoluja
- Sisällytä notebookeihin tulosten esimerkit
- Käytä selkeitä muuttujien nimiä, jotka vastaavat oppitunnin käsitteitä
- Säilytä notebookin suoritusjärjestys loogisena (solu 1 → 2 → 3...)

### Tiedostojen järjestely

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

## Rakentaminen ja käyttöönotto

### Dokumentaation rakentaminen

Tämä repositorio käyttää Markdownia dokumentaatiossa:
- README.md tiedostot jokaisessa oppitunnin kansiossa
- Pää-README.md repositorion juuressa
- Automaattinen käännösjärjestelmä GitHub Actionsin kautta

### CI/CD-putki

Sijaitsee kansiossa `.github/workflows/`:

1. **co-op-translator.yml** - Automaattinen käännös yli 50 kielelle
2. **welcome-issue.yml** - Tervetulotoivotus uusille issueiden tekijöille
3. **welcome-pr.yml** - Tervetulotoivotus uusille pull request -tekijöille

### Käyttöönotto

Tämä on opetuskäyttöön tarkoitettu repositorio - ei tuotantoon menoprosessia. Käyttäjät:
1. Lohkaise tai kloonaa repositorio
2. Aja notebookit paikallisesti tai GitHub Codespacesissä
3. Opiskele muokkaamalla ja kokeilemalla esimerkkejä

## Pull Request -ohjeet

### Ennen lähettämistä

1. **Testaa muutoksesi:**
   - Suorita vaikuttavat notebookit kokonaan
   - Varmista, että kaikki solut suorittuvat ilman virheitä
   - Tarkista, että tulosteet ovat tarkoituksenmukaisia

2. **Dokumentaation päivitykset:**
   - Päivitä README.md, jos lisäät uusia käsitteitä
   - Lisää kommentteja monimutkaisiin koodeihin notebookeissa
   - Varmista, että markdown-solut selittävät tarkoituksen

3. **Tiedostomuutokset:**
   - Vältä `.env`-tiedostojen committaamista (käytä `.env.example`)
   - Älä committaa `venv/` tai `__pycache__/` -hakemistoja
   - Säilytä notebookien tulosteet, kun ne demonstroivat käsitteitä
   - Poista väliaikaiset tiedostot ja varmuuskopioatut notebookit (`*-backup.ipynb`)

### PR-otsikon muotoilu

Käytä kuvaavia otsikoita:
- `[Lesson-XX] Lisää uusi esimerkki <käsite>`
- `[Fix] Korjaa kirjoitusvirhe lesson-XX README:ssä`
- `[Update] Paranna koodiesimerkkiä lesson-XX:ssa`
- `[Docs] Päivitä asennusohjeet`

### Pakolliset tarkistukset

- Notebookien on suorituttava ilman virheitä
- README-tiedostojen on oltava selkeitä ja oikeellisia
- Noudata olemassa olevia koodimalleja repositoriossa
- Säilytä johdonmukaisuus muiden oppituntien kanssa

## Lisähuomiot

### Yleisiä sudenkuoppia

1. **Python-version yhteensopimattomuus:**
   - Varmista, että käytössä on Python 3.12+
   - Jotkin paketit eivät toimi vanhemmilla versioilla
   - Käytä `python3 -m venv` määrittääksesi version eksplisiittisesti

2. **Ympäristömuuttujat:**
   - Luo aina `.env` `.env.example` pohjalta
   - Älä committaa `.env` (on `.gitignore`-tiedostossa)
   - GitHub-token tarvitsee sopivat oikeudet

3. **Paketin ristiriidat:**
   - Käytä puhdasta virtuaaliympäristöä
   - Asenna `requirements.txt` kautta, älä erikseen paketteja
   - Jotkin notebookit saattavat vaatia lisäpaketteja, jotka mainitaan markdown-soluissa

4. **Azure-palvelut:**
   - Azure AI palvelut vaativat aktiivisen tilauksen
   - Ominaisuudet voivat olla aluekohtaisia
   - GitHub Models -ilmainen taso on rajattu

### Oppimispolku

Suositeltu eteneminen oppitunneissa:
1. **00-course-setup** - Aloita tästä ympäristön asetuksella
2. **01-intro-to-ai-agents** - Ymmärrä tekoälyagenttien perusteet
3. **02-explore-agentic-frameworks** - Tutustu eri kehyksiin
4. **03-agentic-design-patterns** - Keskeiset suunnittelumallit
5. Jatka numeroitujen oppituntien mukaisesti

### Kehyksen valinta

Valitse kehys tavoitteidesi mukaan:
- **Oppiminen/Prototyyppi**: Semantic Kernel + GitHub Models (ilmainen)
- **Moni-agenttijärjestelmät**: AutoGen
- **Uusimmat ominaisuudet**: Microsoft Agent Framework (MAF)
- **Tuotantokäyttöön**: Azure AI Agent Service

### Apua saadaksesi

- Liity [Microsoft Foundry Community Discordiin](https://aka.ms/ai-agents/discord)
- Tutustu oppituntien README-tiedostoihin tarkempaa ohjeistusta varten
- Katso pääsivu [README.md](./README.md) kurssikatsaukseen
- Viittaa [Kurssin asennusohjeisiin](./00-course-setup/README.md) yksityiskohtaiseen asennukseen

### Osallistuminen

Tämä on avoin opetushanke. Osallistu vapaaehtoisesti:
- Paranna koodiesimerkkejä
- Korjaa kirjoitusvirheitä tai virheitä
- Lisää selventäviä kommentteja
- Ehdota uusia oppitunteja
- Käännä lisää kieliä

Katso [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) nykyisistä tarpeista.

## Projektiin liittyvä konteksti

### Monikielinen tuki

Tämä repositorio käyttää automatisoitua käännösjärjestelmää:
- Yli 50 kieltä tuettu
- Käännökset sijaitsevat `/translations/<lang-code>/` -hakemistoissa
- GitHub Actions -työnkulku huolehtii käännösten päivityksistä
- Lähdetiedostot ovat englanniksi repositorion juuressa

### Oppituntirakenne

Jokainen oppitunti noudattaa johdonmukaista kaavaa:
1. Videon pikkukuva linkillä
2. Kirjallinen oppituntisisältö (README.md)
3. Koodiesimerkit eri kehyksillä
4. Oppimistavoitteet ja vaatimukset
5. Lisäoppimateriaalilinkit

### Koodiesimerkkien nimeäminen

Muoto: `<oppitunnus-numero>-<kehys-nimi>.ipynb`
- `04-semantic-kernel.ipynb` - Oppitunti 4, Semantic Kernel
- `07-autogen.ipynb` - Oppitunti 7, AutoGen
- `14-python-agent-framework.ipynb` - Oppitunti 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Oppitunti 14, MAF .NET

### Erityishakemistot

- `translated_images/` - Paikallistettuja kuvia käännöksiin
- `images/` - Alkuperäiset kuvat englanninkielisille sisällöille
- `.devcontainer/` - VS Code kehityssäiliön asetukset
- `.github/` - GitHub Actions -työnkulut ja templaatit

### Riippuvuudet

Keskeiset paketit `requirements.txt` tiedostosta:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen kehys
- `semantic-kernel` - Semantic Kernel kehys
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI -palvelut
- `azure-search-documents` - Azure AI Hakuratkaisu
- `chromadb` - Vektorikanta RAG-esimerkeissä
- `chainlit` - Keskustelukäyttöliittymäkehys
- `browser_use` - Selaimen automaatio agenteille
- `mcp[cli]` - Model Context Protocol -tuki
- `mem0ai` - Muistinhallinta agenteille

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastuuvapauslauseke**:
Tämä asiakirja on käännetty käyttämällä tekoälypohjaista käännöspalvelua [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, huomioithan, että automaattiset käännökset saattavat sisältää virheitä tai epätarkkuuksia. Alkuperäinen asiakirja sen alkuperäiskielisessä muodossa on virallinen lähde. Tärkeiden tietojen osalta suosittelemme ammattimaista ihmiskäännöstä. Emme ole vastuussa tämän käännöksen käytöstä aiheutuvista väärinymmärryksistä tai tulkinnoista.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->