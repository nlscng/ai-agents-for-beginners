# Kurssin asetukset

## Johdanto

Tässä oppitunnissa käsitellään, miten tämän kurssin koodiesimerkit suoritetaan.

## Liity muiden oppijoiden joukkoon ja saa apua

Ennen kuin alat kloonata repoasi, liity [AI Agents For Beginners Discord channel](https://aka.ms/ai-agents/discord) -kanavalle saadaksesi apua asennuksessa, kysymyksiä kurssista tai yhteyden muihin oppijoihin.

## Kloonaa tai forkkaa tämä repositorio

Aloittaaksesi kloonaa tai forkkaa GitHub-repositorio. Tämä luo oman version kurssimateriaalista, jotta voit suorittaa, testata ja hienosäätää koodia!

Tämän voi tehdä klikkaamalla linkkiä <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">forkkaa repositorio</a>

Sinulla pitäisi nyt olla oma forkkaamasi versio tästä kurssista seuraavassa linkissä:

![Forkattu repositorio](../../../translated_images/fi/forked-repo.33f27ca1901baa6a.webp)

### Matala kloonaus (suositeltu työpajalle / Codespaces)

> Koko repositorio voi olla suuri (~3 GB), kun lataat koko historian ja kaikki tiedostot. Jos osallistut vain työpajaan tai tarvitset vain muutaman oppituntikansion, matala kloonaus (tai sparse-kloonaus) välttää suurimman osan latauksesta katkaisemalla historian ja/tai ohittamalla blobit.

#### Nopea matala kloonaus — minimaalinen historia, kaikki tiedostot

Korvaa `<your-username>` alla olevissa komennoissa fork-URL:llasi (tai upstream-URL:llä, jos haluat).

Kloonaa vain viimeisin commit-historia (pieni lataus):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Kloonaa tietty haara:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Osittainen (sparse) kloonaus — minimaaliset blobit + vain valitut kansiot

Tämä käyttää osittaista kloonausta ja sparse-checkoutia (vaatii Git 2.25+ ja suositeltu moderni Git osittaisen kloonauksen tuella):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Siirry repositorion kansioon:

```bash|powershell
cd ai-agents-for-beginners
```

Määritä sitten, mitkä kansiot haluat (esimerkissä alla näkyy kaksi kansiota):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Kloonaamisen ja tiedostojen tarkistamisen jälkeen, jos tarvitset vain tiedostot ja haluat vapauttaa tilaa (ei git-historiaa), poista repositorion metatiedot (💀 peruuttamaton — menetät kaiken Git-toiminnallisuuden: ei committeja, pull- tai push-toimintoja tai historian käyttöä).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### GitHub Codespacesin käyttö (suositeltu paikallisten suurten latausten välttämiseksi)

- Luo tälle repositoriolle uusi Codespace [GitHubin käyttöliittymän](https://github.com/codespaces) kautta.  

- Uuden Codespacen terminaalissa suorita jokin yllä olevista matala-/sparse-kloonauskomennoista tuodaksesi vain tarvitsemasi oppituntikansiot Codespace-työtilaan.
- Valinnainen: kloonauksen jälkeen Codespacessa poista .git vapauttaaksesi tilaa (katso poistokomennot yllä).
- Huom: Jos haluat avata repositorion suoraan Codespacessa (ilman ylimääräistä kloonausta), huomioi, että Codespaces rakentaa devcontainer-ympäristön ja saattaa silti provisoida enemmän kuin tarvitset. Kloonaamalla matalan kopion uudessa Codespacessa saat enemmän hallintaa levytilankäyttöön.

#### Vinkkejä

- Vaihda aina kloonaus-URL forkkiisi, jos haluat muokata/commitata.
- Jos tarvitset myöhemmin enemmän historiaa tai tiedostoja, voit hakea ne tai säätää sparse-checkoutia sisällyttääksesi lisäkansioita.

## Koodin suorittaminen

Tässä kurssissa on joukko Jupyter Notebook -tiedostoja, joita voit suorittaa saadaksesi käytännön kokemusta AI-agenttien rakentamisesta.

Koodiesimerkit käyttävät jompaakumpaa seuraavista:

**Vaatii GitHub-tilin - Ilmainen**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Merkitty nimellä (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Merkitty nimellä (autogen.ipynb)

**Vaatii Azure-tilauksen**:
3) Azure AI Foundry + Azure AI Agent Service. Merkitty nimellä (azureaiagent.ipynb)

Kannustamme sinua kokeilemaan kaikkia kolmea esimerkkityyppiä nähdäksesi, mikä toimii parhaiten sinulle.

Valitsemasi vaihtoehdon mukaan määräytyy, mitä asennusvaiheita sinun tarvitsee seurata alla:

## Vaatimukset

- Python 3.12+
  - **HUOM**: Jos sinulla ei ole Python3.12 asennettuna, asenna se. Luo sitten venv käyttämällä python3.12 varmistaaksesi, että oikeat versiot asennetaan requirements.txt-tiedostosta.
  
    >Esimerkki

    Luo Python-venv-hakemisto:

    ```bash|powershell
    python -m venv venv
    ```

    Aktivoi sitten venv-ympäristö:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: .NET:iä käyttävien esimerkkien kohdalla varmista, että asennat [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) tai uudemman. Tarkista sitten asennettu .NET SDK -versiosi:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub-tili - GitHub Models Marketplaceen pääsyä varten
- Azure-tilaus - Microsoft Foundry -käyttöoikeutta varten
- Microsoft Foundry -tili - Azure AI Agent Serviceen pääsyä varten

Olemme lisänneet tämän repositorion juureen `requirements.txt`-tiedoston, joka sisältää kaikki tarvittavat Python-paketit koodiesimerkkien suorittamiseen.

Voit asentaa ne suorittamalla seuraavan komennon terminaalissasi repositorion juurikansiossa:

```bash|powershell
pip install -r requirements.txt
```

Suosittelemme Python-virtuaaliympäristön luomista konfliktien ja ongelmien välttämiseksi.

## VSCode:n asetukset

Varmista, että käytät oikeaa Python-versiota VSCode:ssa.

![kuva](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Asetukset GitHub-malleja käyttäville esimerkeille

### Vaihe 1: Hanki GitHub-henkilökohtainen käyttöoikeustunnus (PAT)

Tämä kurssi hyödyntää GitHub Models Marketplacea, tarjoten ilmaisen pääsyn suuriin kielimalleihin (LLM:t), joita käytät AI-agenttien rakentamiseen.

GitHub-mallien käyttämiseksi sinun täytyy luoda [GitHub-henkilökohtainen käyttöoikeustunnus](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Tämän voit tehdä menemällä GitHub-tilisi <a href="https://github.com/settings/personal-access-tokens" target="_blank">Henkilökohtaisten käyttöoikeustunnusten asetuksiin</a>.

Noudata luodessasi tokenia [vähimmän etuoikeuden periaatetta](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely). Tämä tarkoittaa, että sinun tulisi antaa tokenille vain ne oikeudet, joita tarvitaan tämän kurssin koodiesimerkkien suorittamiseen.

1. Valitse vasemmalta puolelta `Fine-grained tokens` -vaihtoehto siirtymällä **Developer settings** -kohtaan

   ![Kehittäjäasetukset](../../../translated_images/fi/profile_developer_settings.410a859fe749c755.webp)

   Valitse sitten `Generate new token`.

   ![Luo tunnus](../../../translated_images/fi/fga_new_token.1c1a234afe202ab3.webp)

2. Anna tokenille kuvaava nimi, joka heijastaa sen tarkoitusta, jotta sen tunnistaminen myöhemmin on helppoa.

    🔐 Tokenin voimassaoloajan suositus

    Suositeltu kesto: 30 päivää
    Turvallisuussyistä voit valita lyhyemmän ajan — esimerkiksi 7 päivää 🛡️
    Tämä on loistava tapa asettaa henkilökohtainen tavoite ja suorittaa kurssi samalla kun oppimismotivaatiosi on korkealla 🚀.

    ![Tokenin nimi ja vanheneminen](../../../translated_images/fi/token-name-expiry-date.a095fb0de6386864.webp)

3. Rajoita tokenin laajuus forkkaamaasi tähän repositorioon.

    ![Rajoita laajuus forkkiin](../../../translated_images/fi/token_repository_limit.924ade5e11d9d8bb.webp)

4. Rajoita tokenin käyttöoikeuksia: Under **Permissions**, click **Account** tab, and click the "+ Add permissions" button. A dropdown will appear. Please search for **Models** and check the box for it.

    ![Lisää Models-oikeus](../../../translated_images/fi/add_models_permissions.c0c44ed8b40fc143.webp)

5. Vahvista vaaditut oikeudet ennen tokenin luomista. ![Vahvista oikeudet](../../../translated_images/fi/verify_permissions.06bd9e43987a8b21.webp)

6. Ennen tokenin luomista varmista, että olet valmis tallentamaan tokenin turvalliseen paikkaan, kuten salasananhallintatyökaluun, sillä sitä ei näytetä uudelleen luomisen jälkeen. ![Tallenna token turvallisesti](../../../translated_images/fi/store_token_securely.08ee2274c6ad6caf.webp)

Kopioi juuri luomasi token. Lisää se nyt tämän kurssin mukana tulevaan `.env`-tiedostoon.

### Vaihe 2: Luo `.env`-tiedostosi

Luo `.env`-tiedostosi suorittamalla seuraava komento terminaalissasi.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Tämä kopioi esimerkkitiedoston ja luo `.env`-tiedoston hakemistoosi, johon täytät ympäristömuuttujien arvot.

Kun olet kopioinut tokenin, avaa `.env`-tiedosto suosikkitekstieditorissasi ja liitä token `GITHUB_TOKEN`-kenttään.

![GitHub-token-kenttä](../../../translated_images/fi/github_token_field.20491ed3224b5f4a.webp)

Sinun pitäisi nyt pystyä suorittamaan tämän kurssin koodiesimerkit.

## Asetukset Microsoft Foundryn ja Azure AI Agent Servicen esimerkeille

### Vaihe 1: Hanki Azure-projektisi päätepiste


Noudata ohjeita hubin ja projektin luomiseen Azure AI Foundryssa tästä: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Kun olet luonut projektisi, sinun täytyy hakea projektisi yhteysmerkkijono.

Tämän voit tehdä menemällä projektisi Microsoft Foundry -portaalissa projektisi **Overview**-sivulle.

![Projektin yhteysmerkkijono](../../../translated_images/fi/project-endpoint.8cf04c9975bbfbf1.webp)

### Vaihe 2: Luo `.env`-tiedostosi

Luo `.env`-tiedostosi suorittamalla seuraava komento terminaalissasi.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Tämä kopioi esimerkkitiedoston ja luo `.env`-tiedoston hakemistoosi, johon täytät ympäristömuuttujien arvot.

Kun olet kopioinut tokenin, avaa `.env`-tiedosto suosikkitekstieditorissasi ja liitä token `PROJECT_ENDPOINT`-kenttään.

### Vaihe 3: Kirjaudu Azureen

Turvallisuuskäytännön mukaisesti käytämme [avaimetonta todennusta](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) autentikoitumiseen Azure OpenAI:iin Microsoft Entra ID:n avulla. 

Avaa sitten terminaali ja suorita `az login --use-device-code` kirjautuaksesi Azure-tilillesi.

Kun olet kirjautunut, valitse tilauksesi terminaalissa.

## Lisäympäristömuuttujat - Azure Search ja Azure OpenAI 

Agentic RAG -oppitunnilla (Oppitunti 5) on esimerkkejä, jotka käyttävät Azure Searchia ja Azure OpenAI:ta.

Jos haluat suorittaa nämä esimerkit, sinun täytyy lisätä seuraavat ympäristömuuttujat `.env`-tiedostoosi:

### Yleiskatsaus-sivu (projekti)

- `AZURE_SUBSCRIPTION_ID` - Tarkista **Project details** projektisi **Overview**-sivulta.

- `AZURE_AI_PROJECT_NAME` - Katso projektisi **Overview**-sivun yläosasta.

- `AZURE_OPENAI_SERVICE` - Löydät tämän **Included capabilities** -välilehdeltä kohdasta **Azure OpenAI Service** **Overview**-sivulla.

### Hallintakeskus

- `AZURE_OPENAI_RESOURCE_GROUP` - Siirry **Project properties** -kohtaan **Overview**-sivulla **Management Center**issä.

- `GLOBAL_LLM_SERVICE` - Etsi **Connected resources** -kohdasta **Azure AI Services** -yhteyden nimi. Jos sitä ei ole luettelossa, tarkista Azure-portaalista resurssiryhmäsi alta AI Services -resurssin nimi.

### Mallit ja päätepisteet

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Valitse upotemalli (esim. `text-embedding-ada-002`) ja huomioi mallin tiedoista **Deployment name**.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Valitse chat-malli (esim. `gpt-4o-mini`) ja huomioi mallin tiedoista **Deployment name**.

### Azure-portaali

- `AZURE_OPENAI_ENDPOINT` - Etsi **Azure AI services**, klikkaa sitä, mene **Resource Management**, **Keys and Endpoint**, selaa alas kohtaan "Azure OpenAI endpoints" ja kopioi se, jossa lukee "Language APIs".

- `AZURE_OPENAI_API_KEY` - Kopioi samalta näytöltä KEY 1 tai KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Etsi **Azure AI Search** -resurssisi, klikkaa sitä ja katso **Overview**.

- `AZURE_SEARCH_API_KEY` - Siirry sitten **Settings**-kohtaan ja sieltä **Keys** kopioidaksesi ensisijaisen tai toissijaisen admin-avaimen.

### Ulkoinen verkkosivu

- `AZURE_OPENAI_API_VERSION` - Käy [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) -sivulla kohdassa **Latest GA API release**.

### Aseta avaimeton todennus

Sen sijaan, että kovakoodaisimme tunnistetietosi, käytämme avaimetonta yhteyttä Azure OpenAI:iin. Tätä varten tuomme `DefaultAzureCredential`-luokan ja kutsumme myöhemmin `DefaultAzureCredential`-funktiota saadaksemme tunnistetiedon.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Jumiuduitko?
Jos sinulla on ongelmia tämän asennuksen suorittamisessa, liity <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a>-palvelimeemme tai <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">avaa issue</a>.

## Seuraava oppitunti

Olet nyt valmis suorittamaan tämän kurssin koodin. Hyvää oppimista tekoälyagenttien maailmasta! 

[Johdatus tekoälyagentteihin ja agenttien käyttötapauksiin](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Vastuuvapauslauseke:
Tämä asiakirja on käännetty käyttämällä tekoälykäännöspalvelua Co-op Translator (https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, ota huomioon, että automaattisissa käännöksissä voi esiintyä virheitä tai epätarkkuuksia. Alkuperäistä asiakirjaa sen alkuperäiskielellä tulee pitää auktoritatiivisena lähteenä. Tärkeiden tietojen osalta suositellaan ammattimaista, ihmisen tekemää käännöstä. Emme ole vastuussa mahdollisista väärinymmärryksistä tai virheellisistä tulkinnoista, jotka aiheutuvat tämän käännöksen käytöstä.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->