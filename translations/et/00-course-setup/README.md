# Kursuse seadistamine

## Sissejuhatus

Selles õppetükis käsitletakse, kuidas käivitada selle kursuse koodinäiteid.

## Liitu teiste õppijatega ja saa abi

Enne oma repo kloonimist liitu [AI Agents For Beginners Discord kanaliga](https://aka.ms/ai-agents/discord), et saada abi seadistamisel, küsimuste korral kursuse kohta või et suhelda teiste õppijatega.

## Klooni või hargne see repo

Alustamiseks palun klooni või hargne GitHubi hoidla. See loob sinu versiooni kursuse materjalidest, et saad koodi käivitada, testida ja kohandada!

Seda saab teha klõpsates lingile <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">repo forkimiseks</a>

Sul peaks nüüd olema oma hargnenud versioon sellest kursusest järgmisel lingil:

![Forked Repo](../../../translated_images/et/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (soovitatav töötubade / Codespaces jaoks)

  > Täielik hoidla võib olla suur (~3 GB), kui laadid alla kogu ajaloo ja kõik failid. Kui osaled ainult töötoas või vajad vaid mõnda õppetüki kausta, siis võid kasutada shallow clone’i (või sparse clone’i), mis väldib enamikku allalaadimist, kärpides ajaloo ja/või vahele jättes binaarfailid.

#### Kiire shallow clone — minimaalne ajalugu, kõik failid

Asenda alltoodud käskudes `<your-username>` oma fork URL-i või upstream URL-iga, kui eelistad.

Ainult viimase commit ajaloo kloonimiseks (väike allalaadimine):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Kindla haru kloonimiseks:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Osaline (sparse) clone — minimaalne binaarfailide arv + ainult valitud kaustad

See kasutab osalist klooni ja sparse-checkout’i (nõuab Git 2.25+ ja soovitatakse kaasaegset Giti osalise klooni toega):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Liigu repo kausta:

```bash|powershell
cd ai-agents-for-beginners
```

Seejärel määra, milliseid kaustu soovid (alltoodud näites kaks kausta):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Pärast kloonimist ja failide kontrollimist, kui vajad ainult faile ja tahad vabaneda ruumist (ilma git ajaloota), siis palun kustuta hoidla metaandmed (💀tagasipöördumatu – kaotad kogu Git funktsionaalsuse: ei commit’e, pull’e, push’e ega ajaloole ligipääsu).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Kasutades GitHub Codespaces (soovitatav, et vältida suuri lokaalseid allalaadimisi)

- Loo uus Codespace selle repo jaoks GitHubi kasutajaliidese kaudu [GitHub UI](https://github.com/codespaces).  

- Uue Codespace terminalis kasuta üht eelpool nimetatud shallow/sparse clone käsku, et tuua vaid vajalikud õppetüki kaustad Codespace töökeskkonda.
- Valikuline: pärast kloonimist Codespaces eemalda .git, et vabastada lisaruumi (vaata eemaldamiskäske eelpool).
- Märkus: Kui eelistad avada hoidla otse Codespaces ilma lisakloonita, tuleb arvestada, et Codespaces loob devcontainer keskkonna ja võib ikka provisionida rohkem kui vajatakse. Shallow kloon värskes Codespaces annab parema kontrolli kettakasutuse üle.

#### Näpunäited

- Asenda klooni URL alati oma forkiga, kui soovid muudatusi teha või commit’ida.
- Kui hiljem vajad rohkem ajalooandmeid või faile, saad need tõmmata või kohandada sparse-checkout seadeid lisakaustade kaasamiseks.

## Koodi käivitamine

See kursus pakub sarja Jupyter Notebooks’i, mida saad käivitada, et omandada praktilisi kogemusi AI agentide loomisel.

Koodinäited kasutavad kas:

**Nõuab GitHubi kontot – Tasuta**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Märgistatud kui (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Märgistatud kui (autogen.ipynb)

**Nõuab Azure tellimust**:
3) Azure AI Foundry + Azure AI Agent Service. Märgistatud kui (azureaiagent.ipynb)

Soovitame sul proovida kõiki kolme tüüpi näiteid, et näha, milline sulle kõige paremini sobib.

Millise võimaluse valid, see määrab, milliseid seadistusetappe pead allpool järgima:

## Nõuded

- Python 3.12+
  - **MÄRKUS**: Kui sul pole Python 3.12 installitud, palun paigalda see. Seejärel loo oma virtuaalne keskkond python3.12 abil, et kindlustada õige versioonide install nõuete failist requirements.txt.
  
    >Näide

    Loo Python venv kaust:

    ```bash|powershell
    python -m venv venv
    ```

    Seejärel aktiveeri venv keskkond:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: .NET-ga näidiskoodide jaoks paigalda [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) või uuem versioon. Kontrolli oma installitud .NET SDK versiooni:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub konto - Juurdepääs GitHub Models Marketplace’ile
- Azure tellimus - Microsoft Foundry ligipääsuks
- Microsoft Foundry konto - Azure AI Agent Service ligipääsuks

Oleme lisanud selle hoidla juurkausta `requirements.txt` faili, mis sisaldab kõiki vajalikke Python pakette koodinäidete käivitamiseks.

Need paigaldad, kui jooksutad järgneva käsu terminalis hoidla juurkataloogis:

```bash|powershell
pip install -r requirements.txt
```

Soovitame luua Python virtuaalse keskkonna, et vältida konflikte ja tõrkeid.

## VSCode seadistamine

Veendu, et kasutad VSCode’is õiget Python versiooni.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## GitHub mudelitega näidiste seadistamine

### Samm 1: Hangi oma GitHubi isiklik juurdepääsu token (PAT)

See kursus kasutab GitHub Models Marketplace’i, mis pakub tasuta ligipääsu suurtele keelemudelitele (LLM), mida saad kasutada AI agentide ehitamiseks.

GitHub mudelite kasutamiseks pead looma [GitHub isikliku juurdepääsu tokeni](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Seda saad teha oma GitHub konto <a href="https://github.com/settings/personal-access-tokens" target="_blank">Isikliku juurdepääsu tokenite seadistustes</a>.

Palun järgi [vähemate õiguste põhimõtet](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) tokenit luues. See tähendab, et anna tokenile vaid õigused, mida on vaja selle kursuse koodinäidete käivitamiseks.

1. Vali ekraani vasakul servas **Developer settings** alt `Fine-grained tokens` valik.

   ![Developer settings](../../../translated_images/et/profile_developer_settings.410a859fe749c755.webp)

   Seejärel vali `Generate new token`.

   ![Generate Token](../../../translated_images/et/fga_new_token.1c1a234afe202ab3.webp)

2. Sisesta tokenile kirjeldav nimi, mis peegeldab selle eesmärki, et oleks hiljem lihtne tuvastada.

    🔐 Tokeni kestuse soovitus

    Soovitatav kestus: 30 päeva
    Kindlama turvalisuse tagamiseks võid valida lühema perioodi — näiteks 7 päeva 🛡️
    See on hea viis seatud eesmärk täita ja kursus lõpetada, kui õpingute hoog on kõrge 🚀.

    ![Token Name and Expiration](../../../translated_images/et/token-name-expiry-date.a095fb0de6386864.webp)

3. Piira tokeni ulatus ainult selle repo sinu hargnemisele.

    ![Limit scope to fork repository](../../../translated_images/et/token_repository_limit.924ade5e11d9d8bb.webp)

4. Piira tokeni õigusi: all **Permissions** klõpsa **Account** vahekaarti ja seejärel "+ Add permissions" nuppu. Ilmub rippmenüü. Otsi **Models** ja märgista see kastike.

    ![Add Models Permission](../../../translated_images/et/add_models_permissions.c0c44ed8b40fc143.webp)

5. Kontrolli vajalikke õigusi enne tokeni genereerimist. ![Verify Permissions](../../../translated_images/et/verify_permissions.06bd9e43987a8b21.webp)

6. Enne tokeni genereerimist kindlusta, et oled valmis tokeni ohutult salvestama näiteks paroolihalduri vault’i, sest seda ei näidata uuesti pärast loomist. ![Store Token Securely](../../../translated_images/et/store_token_securely.08ee2274c6ad6caf.webp)

Kopeeri just loodud token. Lisad selle nüüd kursuses kaasasolevasse `.env` faili.

### Samm 2: Loo oma `.env` fail

Loo `.env` fail käivitades terminalis järgmise käsu:

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

See kopeerib näidisdokumendi ja loob sinu kausta `.env` faili, kus täidad keskkonnamuutujate väärtused.

Tokeni kopeerimise järel ava `.env` fail oma eelistatud tekstiredaktoris ja kleebi token `GITHUB_TOKEN` lahtrisse.

![GitHub Token Field](../../../translated_images/et/github_token_field.20491ed3224b5f4a.webp)

Nüüd peaksid saama käivitada selle kursuse koodinäited.

## Microsoft Foundry ja Azure AI Agent Service näidiste seadistamine

### Samm 1: Hangi oma Azure projekti lõpp-punkt


Järgige juhiseid Azure AI Foundry keskust ja projekti loomisel aadressil: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Kui projekt on loodud, tuleb hankida ühenduse string oma projekti jaoks.

See saab tehtud, minnes Microsoft Foundry portaali projekti **Overview** lehele.

![Project Connection String](../../../translated_images/et/project-endpoint.8cf04c9975bbfbf1.webp)

### Samm 2: Loo oma `.env` fail

Loo `.env` fail käivitades terminalis järgmise käsu:

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

See kopeerib näidisin faili ja loob kataloogi `.env` faili, kus täidad keskkonnamuutujate väärtused.

Tokeni kopeerimise järel ava `.env` fail oma lemmik tekstiredaktoris ja kleebi token `PROJECT_ENDPOINT` lahtrisse.

### Samm 3: Logi sisse Azure'i

Turvalisuse parima tava kohaselt kasutame [võtmeta autentimist](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) Azure OpenAI autentimiseks Microsoft Entra ID-ga.

Järgmisena ava terminal ja käivita `az login --use-device-code`, et sisse logida oma Azure kontole.

Kui oled sisse logitud, vali terminalis oma tellimus.

## Täiendavad keskkonnamuutujad - Azure Search ja Azure OpenAI

Agentic RAG õppetüki — Õppetükk 5 — näidetes kasutatakse Azure Searchi ja Azure OpenAI’d.

Kui soovid neid näiteid käivitada, pead lisama järgmised keskkonnamuutujad oma `.env` faili:

### Ülevaade leht (Project)

- `AZURE_SUBSCRIPTION_ID` - Vaata projekti **Details** osa projekti **Overview** lehel.

- `AZURE_AI_PROJECT_NAME` - Vaata projekti **Overview** lehe ülaosast.

- `AZURE_OPENAI_SERVICE` - Leia see **Included capabilities** vahekaardilt **Azure OpenAI Service** all projekti lehel.

### Halduskeskus

- `AZURE_OPENAI_RESOURCE_GROUP` - Mine **Project properties** alla **Overview** lehel halduskeskuses.

- `GLOBAL_LLM_SERVICE` - **Connected resources** alt leia **Azure AI Services** ühenduse nimi. Kui pole nimekirjas, controleeri Azure portaalis oma ressursside grupist AI Services ressurssi.

### Mudelid + lõpp-punktid leht

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Vali oma embedding mudel (nt `text-embedding-ada-002`) ja märgi **Deployment name** mudeli detailides.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Vali oma chat muudel (nt `gpt-4o-mini`) ja märgi **Deployment name** mudeli detailides.

### Azure Portaal

- `AZURE_OPENAI_ENDPOINT` - Leia **Azure AI services** ja klõpsa sellel, seejärel mine **Resource Management**, **Keys and Endpoint**, kerides alla "Azure OpenAI endpoints" ning kopeeri see, mis kannab nimetust "Language APIs".

- `AZURE_OPENAI_API_KEY` - Samast ekraanilt kopeeri KEY 1 või KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Leia oma **Azure AI Search** ressurss, ava see ja vaata **Overview**.

- `AZURE_SEARCH_API_KEY` - Seejärel mine **Settings** ja **Keys**, et kopeerida peamine või teine admin võti.

### Väline veebileht

- `AZURE_OPENAI_API_VERSION` - Külasta lehte [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) punkti **Latest GA API release** all.

### Võtmeta autentimise seadistamine

Selle asemel, et kande oma mandaadid kõvakodeerida, kasutame võtmepõhist ühendust koos Azure OpenAI’ga. Selleks impordime `DefaultAzureCredential` ja hiljem kutsume funktsiooni `DefaultAzureCredential`, et saada mandaadid.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Jäid kuskile hätta?
Kui teil tekib selle seadistusega mingeid probleeme, liituge meie <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI kogukonna Discordiga</a> või <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">loodud probleemiga</a>.

## Järgmine õppetund

Olete nüüd valmis selle kursuse koodi jooksma. Head õppimist AI-agentide maailma kohta! 

[Intro AI-agentide ja agentide kasutusjuhtumitesse](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastutusest loobumine**:
See dokument on tõlgitud AI tõlketeenuse [Co-op Translator](https://github.com/Azure/co-op-translator) abil. Kuigi me püüdleme täpsuse poole, palun arvestage, et automaatsed tõlked võivad sisaldada vigu või ebatäpsusi. Originaaldokument selle emakeeles tuleb pidada autoriteetseks allikaks. Kriitilise teabe puhul soovitatakse kasutada professionaalset inimtõlget. Me ei vastuta selle tõlke kasutamisest tulenevate arusaamatuste ega valesti mõistmiste eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->