# Nastavitev tečaja

## Uvod

Ta lekcija bo razložila, kako zagnati primere kode iz tega tečaja.

## Pridružite se drugim učečim in poiščite pomoč

Preden začnete klonirati svoj repo, se pridružite kanalu [AI Agents For Beginners Discord channel](https://aka.ms/ai-agents/discord) za pomoč pri nastavitvi, vprašanja o tečaju ali za povezavo z drugimi učečimi.

## Klonirajte ali forkajte ta repo

Za začetek, prosimo, klonirajte ali forkajte GitHub repozitorij. S tem si boste naredili svojo različico gradiva tečaja, tako da boste lahko zagnali, preizkusili in prilagodili kodo!

To lahko storite s klikom na povezavo za <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">ustvarite fork tega repozitorija</a>

Zdaj bi morali imeti svojo forkano različico tega tečaja na naslednji povezavi:

![Forkan repozitorij](../../../translated_images/sl/forked-repo.33f27ca1901baa6a.webp)

### Plitek klon (priporočeno za delavnico / Codespaces)

  >Celoten repozitorij je lahko velik (~3 GB), če prenesete celotno zgodovino in vse datoteke. Če obiskujete samo delavnico ali potrebujete le nekaj map lekcij, plitek klon (ali redek klon) prepreči večino tega prenosa z obrezovanjem zgodovine in/ali preskakovanjem blobov.

#### Hiter plitek klon — minimalna zgodovina, vse datoteke

Zamenjajte `<your-username>` v spodnjih ukazih z URL-jem vašega forka (ali z upstream URL-jem, če želite).

Za kloniranje samo najnovejše zgodovine commitov (majhen prenos):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Za kloniranje določenega branch-a:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Delni (sparse) klon — minimalni blobi + le izbrane mape

To uporablja delni klon in sparse-checkout (zahteva Git 2.25+ in priporočen sodoben Git s podporo delnim klonom):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Vstopite v mapo repozitorija:

```bash|powershell
cd ai-agents-for-beginners
```

Nato navedite, katere mape želite (primer spodaj prikazuje dve mapi):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Po kloniranju in preverjanju datotek, če potrebujete samo datoteke in želite sprostiti prostor (brez zgodovine git), prosimo izbrišite metapodatke repozitorija (💀nepreklicno — izgubili boste vso funkcionalnost Gita: brez commitov, pullov, pushov ali dostopa do zgodovine).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Uporaba GitHub Codespaces (priporočeno za izogibanje velikim lokalnim prenosom)

- Ustvarite nov Codespace za ta repo preko [GitHub UI](https://github.com/codespaces).  

- V terminalu novoustanovljenega codespace-a zaženite enega izmed zgornjih ukazov za plitek/sparse klon, da v Codespace delovno okolje prenesete le mape lekcij, ki jih potrebujete.
- Izbirno: po kloniranju znotraj Codespaces odstranite .git, da povrnete dodatni prostor (glejte ukaze za odstranjevanje zgoraj).
- Opomba: Če želite odpreti repo neposredno v Codespaces (brez dodatnega kloniranja), upoštevajte, da bo Codespaces ustvaril devcontainer okolje in morda še vedno pripravil več, kot potrebujete. Kloniranje plitve kopije znotraj svežega Codespace-a vam daje več nadzora nad porabo diska.

#### Nasveti

- Vedno zamenjajte URL za kloniranje s svojim forkom, če želite urejati/commitati.
- Če boste kasneje potrebovali več zgodovine ali datotek, jih lahko pridobite ali prilagodite sparse-checkout, da vključite dodatne mape.

## Zagon kode

Ta tečaj ponuja vrsto Jupyter Notebookov, ki jih lahko zaženete za praktično izkušnjo pri izdelavi AI agentov.

Vzorec kode uporablja eno od naslednjih možnosti:

**Zahteva GitHub račun - brezplačno**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Oznaka (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Oznaka (autogen.ipynb)

**Zahteva Azure naročnino**:
3) Azure AI Foundry + Azure AI Agent Service. Oznaka (azureaiagent.ipynb)

Spodbujamo vas, da preizkusite vse tri vrste primerov, da ugotovite, katera najbolj ustreza vam.

Katera koli možnost izberete, bo določila, katere korake nastavitve morate slediti spodaj:

## Zahteve

- Python 3.12+
  - **OPOMBA**: Če nimate nameščenega Python3.12, poskrbite, da ga namestite. Nato ustvarite svoj venv z uporabo python3.12, da zagotovite pravilne različice, ki so navedene v datoteki requirements.txt.
  
    >Primer

    Ustvarite Python venv mapo:

    ```bash|powershell
    python -m venv venv
    ```

    Nato aktivirajte venv okolje za:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Za primere kode, ki uporabljajo .NET, poskrbite, da namestite [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) ali novejšo različico. Nato preverite svojo nameščeno različico .NET SDK:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub račun - za dostop do GitHub Models Marketplace
- Azure naročnina - za dostop do Microsoft Foundry
- Microsoft Foundry račun - za dostop do Azure AI Agent Service

V korenu tega repozitorija smo vključili datoteko `requirements.txt`, ki vsebuje vse potrebne Python pakete za zagon primerov kode.

Namestite jih lahko z zagonom naslednjega ukaza v terminalu v korenu repozitorija:

```bash|powershell
pip install -r requirements.txt
```

Priporočamo ustvarjanje Python virtualnega okolja, da se izognete konfliktom in težavam.

## Nastavitev VSCode

Prepričajte se, da v VSCode uporabljate pravilno različico Pythona.

![slika](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Nastavitev za primere, ki uporabljajo GitHub modele

### Korak 1: Pridobite svoj GitHub osebni dostopni žeton (PAT)

Ta tečaj uporablja GitHub Models Marketplace, ki omogoča brezplačen dostop do velikih jezikovnih modelov (LLM), ki jih boste uporabljali za izdelavo AI agentov.

Za uporabo GitHub modelov boste morali ustvariti [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

To lahko storite tako, da greste v <a href="https://github.com/settings/personal-access-tokens" target="_blank">nastavitve osebnih dostopnih žetonov</a> v svojem GitHub računu.

Prosimo, upoštevajte [Pravilo najmanjših privilegijev](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) pri ustvarjanju vašega žetona. To pomeni, da naj žeton dobi le dovoljenja, ki jih potrebuje za zagon primerov kode v tem tečaju.

1. Izberite možnost `Fine-grained tokens` na levi strani zaslona tako, da preklopite na **Nastavitve razvijalca**

   ![Developer settings](../../../translated_images/sl/profile_developer_settings.410a859fe749c755.webp)

   Nato izberite `Generate new token`.

   ![Ustvari žeton](../../../translated_images/sl/fga_new_token.1c1a234afe202ab3.webp)

2. Vnesite opisno ime za svoj žeton, ki odraža njegov namen, da ga boste kasneje lažje prepoznali.

    🔐 Priporočena dolžina veljavnosti žetona

    Priporočena dolžina: 30 dni
    Za večjo varnost lahko izberete krajše obdobje—na primer 7 dni 🛡️
    To je odličen način, da si postavite osebni cilj in zaključite tečaj, medtem ko vam učno navdušenje ostaja visoko 🚀.

    ![Ime in potek žetona](../../../translated_images/sl/token-name-expiry-date.a095fb0de6386864.webp)

3. Omejite obseg žetona na vaš fork tega repozitorija.

    ![Omeji obseg na fork repozitorij](../../../translated_images/sl/token_repository_limit.924ade5e11d9d8bb.webp)

4. Omejite dovoljenja žetona: pod **Permissions** kliknite zavihek **Account**, in kliknite gumb "+ Add permissions". Pojavilo se bo spustno polje. Prosimo, poiščite **Models** in obkljukajte polje zanj.

    ![Dodaj dovoljenje Models](../../../translated_images/sl/add_models_permissions.c0c44ed8b40fc143.webp)

5. Pred generiranjem žetona preverite potrebna dovoljenja. ![Preveri dovoljenja](../../../translated_images/sl/verify_permissions.06bd9e43987a8b21.webp)

6. Pred generiranjem žetona se prepričajte, da ste pripravljeni žeton shraniti na varno mesto, kot je trezor upravitelja gesel, saj vam po ustvarjanju ne bo več prikazan. ![Shrani žeton varno](../../../translated_images/sl/store_token_securely.08ee2274c6ad6caf.webp)

Kopirajte nov žeton, ki ste ga pravkar ustvarili. Zdaj ga boste dodali v svojo datoteko `.env`, vključeno v tem tečaju.

### Korak 2: Ustvarite svojo datoteko `.env`

Za ustvarjanje datoteke `.env` zaženite naslednji ukaz v terminalu.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

To bo kopiralo primer datoteke in ustvarilo `.env` v vaši mapi, kjer izpolnite vrednosti za spremenljivke okolja.

Ko imate žeton v odložišču, odprite datoteko `.env` v svojem priljubljenem urejevalniku in prilepite žeton v polje `GITHUB_TOKEN`.

![Polje za GitHub žeton](../../../translated_images/sl/github_token_field.20491ed3224b5f4a.webp)

Zdaj bi morali biti sposobni zagnati primere kode iz tega tečaja.

## Nastavitev za primere, ki uporabljajo Microsoft Foundry in Azure AI Agent Service

### Korak 1: Pridobite konektor (endpoint) svojega Azure projekta


Sledite korakom za ustvarjanje huba in projekta v Azure AI Foundry, ki jih najdete tukaj: [Pregled virov huba](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Ko ustvarite projekt, boste morali pridobiti nabor za povezavo (connection string) za vaš projekt.

To lahko storite tako, da odprete stran **Pregled** vašega projekta v portalu Microsoft Foundry.

![Niz za povezavo projekta](../../../translated_images/sl/project-endpoint.8cf04c9975bbfbf1.webp)

### Korak 2: Ustvarite svojo datoteko `.env`

Za ustvarjanje datoteke `.env` zaženite naslednji ukaz v terminalu.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

To bo kopiralo primer datoteke in ustvarilo `.env` v vaši mapi, kjer izpolnite vrednosti za spremenljivke okolja.

Ko imate vrednosti kopirane, odprite datoteko `.env` v svojem priljubljenem urejevalniku in prilepite vrednost v polje `PROJECT_ENDPOINT`.

### Korak 3: Prijavite se v Azure

Kot varnostno najboljšo prakso bomo uporabili [avtentikacijo brez ključa](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) za prijavo v Azure OpenAI z Microsoft Entra ID.

Nato odprite terminal in za prijavo v svoj Azure račun zaženite `az login --use-device-code`.

Ko se prijavite, izberite svojo naročnino v terminalu.

## Dodatne spremenljivke okolja - Azure Search in Azure OpenAI 

Za lekcijo Agentic RAG - Lekcija 5 - so primeri, ki uporabljajo Azure Search in Azure OpenAI.

Če želite zagnati te primere, boste morali v datoteko `.env` dodati naslednje spremenljivke okolja:

### Stran Pregled (projekt)

- `AZURE_SUBSCRIPTION_ID` - Preverite **Podrobnosti projekta** na strani **Pregled** vašega projekta.

- `AZURE_AI_PROJECT_NAME` - Poglejte na vrh strani **Pregled** za vaš projekt.

- `AZURE_OPENAI_SERVICE` - To najdete na zavihku **Vključene zmogljivosti** za **Azure OpenAI Service** na strani **Pregled**.

### Center za upravljanje

- `AZURE_OPENAI_RESOURCE_GROUP` - Pojdite v **Lastnosti projekta** na strani **Pregled** v **Centru za upravljanje**.

- `GLOBAL_LLM_SERVICE` - Pod **Povezani viri** poiščite ime povezave **Azure AI Services**. Če ni na seznamu, preverite v **Azure portalu** pod svojo skupino virov za ime storitve AI Services.

### Stran Modeli + Končne točke

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Izberite svoj embedding model (npr. `text-embedding-ada-002`) in zabeležite **Ime razporeditve** iz podrobnosti modela.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Izberite svoj klepetalni model (npr. `gpt-4o-mini`) in zabeležite **Ime razporeditve** iz podrobnosti modela.

### Azure portal

- `AZURE_OPENAI_ENDPOINT` - Poiščite **Azure AI services**, kliknite nanjo, nato pojdite na **Upravljanje virov**, **Ključi in konektorji**, pomaknite se navzdol do "Azure OpenAI endpoints" ter kopirajte tistega, ki pravi "Language APIs".

- `AZURE_OPENAI_API_KEY` - Iz istega zaslona kopirajte KEY 1 ali KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Poiščite svoj vir **Azure AI Search**, kliknite nanj in si oglejte **Pregled**.

- `AZURE_SEARCH_API_KEY` - Nato pojdite na **Nastavitve** in potem **Ključi**, da kopirate primarni ali sekundarni skrbniški ključ.

### Zunanja spletna stran

- `AZURE_OPENAI_API_VERSION` - Obiščite stran [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) pod **Latest GA API release**.

### Nastavitev avtentikacije brez ključa

Namesto da v kodi trdo vnesete svoje poverilnice, bomo uporabili povezavo brez ključa z Azure OpenAI. Za to bomo uvozili `DefaultAzureCredential` in kasneje poklicali funkcijo `DefaultAzureCredential`, da pridobimo poverilnico.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Se zataknete?
Če imate kakršne koli težave pri zagonu te nastavitve, se pridružite naši <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord skupnosti Azure AI</a> ali <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">ustvarite poročilo o težavi</a>.

## Naslednja lekcija

Zdaj ste pripravljeni zagnati kodo za ta tečaj. Srečno pri učenju več o svetu AI agentov! 

[Uvod v AI agente in njihove primere uporabe](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Izjava o omejitvi odgovornosti:
Ta dokument je bil preveden z uporabo storitve za prevajanje z umetno inteligenco Co-op Translator (https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da avtomatski prevodi lahko vsebujejo napake ali netočnosti. Izvirni dokument v izvirnem jeziku velja za avtoritativni vir. Za kritične informacije priporočamo strokovni prevod, opravljen s strani človeškega prevajalca. Ne odgovarjamo za morebitne nesporazume ali napačne razlage, ki bi nastale zaradi uporabe tega prevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->