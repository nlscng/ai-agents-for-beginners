# Postavljanje tečaja

## Uvod

Ova lekcija će pokriti kako pokrenuti primjere koda iz ovog tečaja.

## Pridružite se ostalim polaznicima i zatražite pomoć

Prije nego počnete klonirati svoj repozitorij, pridružite se [AI Agents For Beginners Discord kanalu](https://aka.ms/ai-agents/discord) kako biste dobili pomoć s postavljanjem, pitanja o tečaju ili se povezali s ostalim polaznicima.

## Klonirajte ili forknite ovaj repozitorij

Za početak, molimo klonirajte ili forknite GitHub repozitorij. To će vam omogućiti vlastitu verziju materijala tečaja kako biste mogli pokretati, testirati i podešavati kod!

To možete učiniti klikom na link <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fork repozitorija</a>

Sada biste trebali imati vlastitu forkanu verziju ovog tečaja na sljedećem linku:

![Forked Repo](../../../translated_images/hr/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (preporučeno za radionice / Codespaces)

  >Puni repozitorij može biti velik (~3 GB) ako preuzimate svu povijest i sve datoteke. Ako sudjelujete samo na radionici ili trebate samo nekoliko mapa s lekcijama, shallow clone (ili sparse clone) izbjegava većinu tog preuzimanja skraćivanjem povijesti i/ili preskakanjem blobova.

#### Brzi shallow clone — minimalna povijest, sve datoteke

Zamijenite `<your-username>` u naredbama ispod sa svojom URL-om forka (ili upstream URL-om ako preferirate).

Za kloniranje samo najnovije povijesti commita (malo preuzimanje):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Za kloniranje specifične grane:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Djelomični (sparse) clone — minimalni blobovi + samo određene mape

Koristi djelomični clone i sparse-checkout (zahtijeva Git 2.25+ i preporučeni moderni Git s podrškom za partial clone):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Uđite u mapu repozitorija:

```bash|powershell
cd ai-agents-for-beginners
```

Zatim specificirajte koje mape želite (primjer ispod prikazuje dvije mape):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Nakon kloniranja i provjere datoteka, ako su vam potrebne samo datoteke i želite osloboditi prostor (bez git povijesti), molimo obrišite repozitorijsku metapodatke (💀nepovratno — izgubiti ćete svu Git funkcionalnost: nema commitova, pullova, pushova ili pristupa povijesti).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Korištenje GitHub Codespaces (preporučeno da se izbjegnu velika lokalna preuzimanja)

- Kreirajte novi Codespace za ovaj repozitorij putem [GitHub UI](https://github.com/codespaces).  

- U terminalu novokreiranog Codespace-a pokrenite jednu od gore navedenih shallow/sparse clone naredbi da biste u Codespace workspace donijeli samo potrebne mape s lekcijama.
- Opcionalno: nakon kloniranja unutar Codespaces, uklonite .git za vraćanje dodatnog prostora (pogledajte naredbe za uklanjanje gore).
- Napomena: Ako preferirate otvoriti repozitorij direktno u Codespaces (bez dodatnog kloniranja), imajte na umu da Codespaces gradi devcontainer okruženje i može i dalje pripremiti više nego što vam treba. Kloniranje shallow kopije unutar svježeg Codespace-a daje vam veću kontrolu nad korištenjem diska.

#### Savjeti

- Uvijek zamijenite klon URL sa svojim fork-om ako želite uređivati/commitati.
- Ako kasnije trebate više povijesti ili datoteka, možete ih dohvatiti ili prilagoditi sparse-checkout za dodavanje dodatnih mapa.

## Pokretanje koda

Ovaj tečaj nudi niz Jupyter bilježnica koje možete pokrenuti za praktično iskustvo izgradnje AI agenata.

Primjeri koda koriste ili:

**Zahtijeva GitHub račun - Besplatno**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Označeno kao (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Označeno kao (autogen.ipynb)

**Zahtijeva Azure pretplatu**:
3) Azure AI Foundry + Azure AI Agent Service. Označeno kao (azureaiagent.ipynb)

Preporučujemo da isprobate sva tri tipa primjera kako biste vidjeli koji vam najbolje odgovara.

Koju god opciju odabrali, ona će odrediti koje korake postavljanja trebate slijediti u nastavku:

## Zahtjevi

- Python 3.12+
  - **NAPOMENA**: Ako nemate instaliran Python3.12, pobrinite se da ga instalirate. Zatim kreirajte svoj venv koristeći python3.12 kako biste osigurali instalaciju ispravnih verzija iz datoteke requirements.txt.
  
    >Primjer

    Kreirajte Python venv direktorij:

    ```bash|powershell
    python -m venv venv
    ```

    Zatim aktivirajte venv okruženje za:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Za primjere koda koji koriste .NET, pobrinite se da instalirate [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) ili noviji. Zatim provjerite svoju instaliranu verziju .NET SDK-a:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub račun - za pristup GitHub Models Marketplace-u
- Azure pretplatu - za pristup Microsoft Foundry
- Microsoft Foundry račun - za pristup Azure AI Agent Service-u

Uključili smo `requirements.txt` datoteku u korijenu ovog repozitorija koja sadrži sve potrebne Python pakete za pokretanje primjera koda.

Možete ih instalirati pokretanjem sljedeće naredbe u terminalu u korijenu repozitorija:

```bash|powershell
pip install -r requirements.txt
```

Preporučujemo kreiranje Python virtualnog okruženja kako biste izbjegli konflikte i probleme.

## Postavljanje VSCode

Provjerite koristite li ispravnu verziju Pythona u VSCode-u.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Postavljanje za primjere koji koriste GitHub Models

### Korak 1: Dohvatite svoj GitHub osobni pristupni token (PAT)

Ovaj tečaj koristi GitHub Models Marketplace, koji pruža besplatan pristup velikim jezičnim modelima (LLM-ovima) koje ćete koristiti za izgradnju AI agenata.

Za korištenje GitHub Models trebat ćete kreirati [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

To se radi odlaskom na <a href="https://github.com/settings/personal-access-tokens" target="_blank">Postavke osobnih pristupnih tokena</a> u svom GitHub računu.

Molimo slijedite [Načelo najmanjih privilegija](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) prilikom kreiranja tokena. To znači da tokenu trebate dati samo dozvole koje su potrebne za pokretanje primjera koda u ovom tečaju.

1. Odaberite opciju `Fine-grained tokens` na lijevoj strani zaslona tako da odete u **Developer settings**

   ![Developer settings](../../../translated_images/hr/profile_developer_settings.410a859fe749c755.webp)

   Zatim odaberite `Generate new token`.

   ![Generate Token](../../../translated_images/hr/fga_new_token.1c1a234afe202ab3.webp)

2. Unesite opisno ime za svoj token koje jasno označava njegovu svrhu, kako biste ga lako prepoznali kasnije.

    🔐 Preporuka trajanja tokena

    Preporučeno trajanje: 30 dana
    Za sigurniji pristup, možete odabrati kraći period — poput 7 dana 🛡️
    To je odličan način da postavite osobni cilj i završite tečaj dok vam je motivacija visoka 🚀.

    ![Token Name and Expiration](../../../translated_images/hr/token-name-expiry-date.a095fb0de6386864.webp)

3. Ograničite opseg tokena samo na vaš fork ovog repozitorija.

    ![Limit scope to fork repository](../../../translated_images/hr/token_repository_limit.924ade5e11d9d8bb.webp)

4. Ograničite dozvole tokena: Pod **Permissions**, kliknite na karticu **Account**, pa kliknite gumb "+ Add permissions". Pojavit će se padajući popis. Molimo potražite **Models** i označite tu opciju.

    ![Add Models Permission](../../../translated_images/hr/add_models_permissions.c0c44ed8b40fc143.webp)

5. Provjerite potrebne dozvole prije nego što generirate token. ![Verify Permissions](../../../translated_images/hr/verify_permissions.06bd9e43987a8b21.webp)

6. Prije generiranja tokena, pobrinite se da ste spremni pohraniti token na sigurno mjesto poput upravitelja lozinki, jer se neće ponovno prikazivati nakon kreiranja. ![Store Token Securely](../../../translated_images/hr/store_token_securely.08ee2274c6ad6caf.webp)

Kopirajte svoj novi token koji ste upravo kreirali. Sada ćete ga dodati u svoju `.env` datoteku uključenu u ovaj tečaj.

### Korak 2: Kreirajte svoju `.env` datoteku

Da biste kreirali `.env` datoteku, pokrenite sljedeću naredbu u terminalu.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Ovo će kopirati primjer datoteke i kreirati `.env` u vašem direktoriju gdje ćete ispuniti vrijednosti za varijable okruženja.

Nakon što ste kopirali token, otvorite `.env` datoteku u omiljenom uređivaču teksta i zalijepite token u polje `GITHUB_TOKEN`.

![GitHub Token Field](../../../translated_images/hr/github_token_field.20491ed3224b5f4a.webp)

Sada biste trebali moći pokrenuti primjere koda iz ovog tečaja.

## Postavljanje za primjere koji koriste Microsoft Foundry i Azure AI Agent Service

### Korak 1: Dohvatite svoj Azure projektni endpoint


Slijedite korake za kreiranje huba i projekta u Azure AI Foundry-u opisane ovdje: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Nakon što kreirate projekt, potrebno je dohvatiti connection string za vaš projekt.

To možete učiniti odlaskom na stranicu **Overview** vašeg projekta u Microsoft Foundry portalu.

![Project Connection String](../../../translated_images/hr/project-endpoint.8cf04c9975bbfbf1.webp)

### Korak 2: Kreirajte svoju `.env` datoteku

Da biste kreirali `.env` datoteku, pokrenite sljedeću naredbu u terminalu.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Ovo će kopirati primjer datoteke i kreirati `.env` u vašem direktoriju gdje ćete ispuniti vrijednosti za varijable okruženja.

Nakon što kopirate token, otvorite `.env` datoteku u omiljenom uređivaču teksta i zalijepite token u polje `PROJECT_ENDPOINT`.

### Korak 3: Prijavite se u Azure

Kao sigurnosnu dobru praksu, koristit ćemo [keyless autentifikaciju](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) za autentifikaciju u Azure OpenAI pomoću Microsoft Entra ID-ja.

Zatim otvorite terminal i pokrenite `az login --use-device-code` kako biste se prijavili u svoj Azure račun.

Nakon prijave odaberite svoju pretplatu u terminalu.

## Dodatne varijable okruženja - Azure Search i Azure OpenAI

Za lekciju Agentic RAG - Lekcija 5 - postoje primjeri koji koriste Azure Search i Azure OpenAI.

Ako želite pokrenuti te primjere, morat ćete dodati sljedeće varijable okruženja u svoju `.env` datoteku:

### Stranica Pregleda (Projekt)

- `AZURE_SUBSCRIPTION_ID` - Provjerite **Detalje projekta** na **Overview** stranici vašeg projekta.

- `AZURE_AI_PROJECT_NAME` - Pogledajte na vrhu **Overview** stranice za vaš projekt.

- `AZURE_OPENAI_SERVICE` - Pronađite ovo u kartici **Included capabilities** za **Azure OpenAI Service** na **Overview** stranici.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - Idite na **Project properties** na **Overview** stranici u **Management Center**.

- `GLOBAL_LLM_SERVICE` - Pod **Connected resources**, pronađite naziv veze **Azure AI Services**. Ako nije naveden, provjerite u **Azure portalu** unutar vaše grupe resursa naziv AI Services resursa.

### Stranica Modela + Endpointa

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Odaberite svoj embedding model (npr. `text-embedding-ada-002`) i zabilježite **Deployment name** iz detalja modela.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Odaberite svoj chat model (npr. `gpt-4o-mini`) i zabilježite **Deployment name** iz detalja modela.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - Potražite **Azure AI services**, kliknite na to, zatim idite na **Resource Management**, **Keys and Endpoint**, skrolajte do "Azure OpenAI endpoints", i kopirajte onaj koji kaže "Language APIs".

- `AZURE_OPENAI_API_KEY` - S iste stranice kopirajte KEY 1 ili KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Pronađite svoj **Azure AI Search** resurs, kliknite na njega i pogledajte **Overview**.

- `AZURE_SEARCH_API_KEY` - Zatim idite na **Settings** pa na **Keys** da kopirate primarni ili sekundarni administratorski ključ.

### Vanjska web stranica

- `AZURE_OPENAI_API_VERSION` - Posjetite [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) stranicu pod **Latest GA API release**.

### Postavljanje keyless autentifikacije

Umjesto da hardkodirate svoje vjerodajnice, koristit ćemo keyless vezu s Azure OpenAI. Da bismo to napravili, uvezit ćemo `DefaultAzureCredential` i kasnije pozvati funkciju `DefaultAzureCredential` kako bismo dobili vjerodajnicu.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Zapeli ste negdje?
Ako imate bilo kakvih problema s pokretanjem ove postavke, pridružite se našem <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> ili <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">kreirajte problem</a>.

## Sljedeći Lekcija

Sada ste spremni pokrenuti kod za ovaj tečaj. Sretno u učenju više o svijetu AI agenata!

[Uvod u AI agente i primjere uporabe agenata](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Izjava o odricanju odgovornosti**:
Ovaj dokument preveden je uz pomoć AI prevodilačke usluge [Co-op Translator](https://github.com/Azure/co-op-translator). Iako težimo točnosti, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za važne informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakve nesporazume ili kriva tumačenja koja proizlaze iz korištenja ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->