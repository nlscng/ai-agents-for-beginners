# Usanidi wa Kozi

## Utangulizi

Somo hili litafunika jinsi ya kuendesha mifano ya msimbo ya kozi hii.

## Jiunge na Wanafunzi Wengine na Pata Msaada

Kabla ya kuanza ku-kloni repoh yako, jiunge na [AI Agents For Beginners Discord channel](https://aka.ms/ai-agents/discord) ili kupata msaada wa usanidi, kuuliza maswali kuhusu kozi, au kuwasiliana na wanafunzi wengine.

## Kloni au Forka repo hii

Ili kuanza, tafadhali kloni au forka Repositori ya GitHub. Hii itaunda toleo lako la nyenzo za kozi ili uweze kuendesha, kujaribu, na kubadilisha msimbo!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fork the repo</a>

You should now have your own forked version of this course in the following link:

![Repo Imeforkiwa](../../../translated_images/sw/forked-repo.33f27ca1901baa6a.webp)

### Kloni ya Ndogo (inapendekezwa kwa warsha / Codespaces)

  >Repositi nzima inaweza kuwa kubwa (~3 GB) unapopakua historia yote na faili zote. Ikiwa unahudhuria tu warsha au unahitaji folda chache za somo, kloni ya kina kidogo (au kloni sparse) hubaki bila sehemu kubwa ya upakuaji kwa kukata historia na/au kuepuka blobs.

#### Kloni ya haraka — historia ndogo, faili zote

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

To clone only the latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Kloni Sehemu (sparse) — blobs ndogo + folda zilizochaguliwa pekee

This uses partial clone and sparse-checkout (requires Git 2.25+ and recommended modern Git with partial clone support):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Traverse into the repo folder:

```bash|powershell
cd ai-agents-for-beginners
```

Then specify which folders you want (example below shows two folders):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

After cloning and verifying the files, if you only need files and want to free space (no git history), please delete the repository metadata (💀irreversible — you will lose all Git functionality: no commits, pulls, pushes, or history access).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Kutumia GitHub Codespaces (inapendekezwa ili kuepuka upakuaji mkubwa mahali pa kazi)

- Unda Codespace mpya kwa repo hii kupitia [GitHub UI](https://github.com/codespaces).  

- Kwenye terminal ya codespace iliyoundwa, endesha mojawapo ya amri za shallow/sparse clone hapo juu ili kuleta folda za somo unazohitaji kwenye nafasi ya Codespace workspace.
- Hiari: baada ya ku-cloni ndani ya Codespaces, ondoa .git ili kuurejesha nafasi zaidi (ona amri za kuondoa hapo juu).
- Kumbuka: Ikiwa unapendelea kufungua repo moja kwa moja ndani ya Codespaces (bila kloni ya ziada), fahamu Codespaces itaunda mazingira ya devcontainer na inaweza bado kutoa zaidi ya unachohitaji. Ku-cloni nakala isiyo nzito ndani ya Codespace safi kunakupa udhibiti zaidi juu ya matumizi ya diski.

#### Vidokezo

- Badilisha kila wakati URL ya kloni na fork yako ikiwa unataka kuhariri/commit.
- Ikiwa baadaye utahitaji historia zaidi au faili, unaweza kuzipata kwa fetch au kurekebisha sparse-checkout ili kujumuisha folda za ziada.

## Kuendesha Msimbo

Kozi hii inatoa mfululizo wa Jupyter Notebooks ambazo unaweza kuendesha ili kupata uzoefu wa vitendo wa kujenga AI Agents.

The code samples use either:

**Inahitaji Akaunti ya GitHub - Bila malipo**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Imewekwa alama kama (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Imetajwa kama (autogen.ipynb)

**Inahitaji Usajili wa Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Imetajwa kama (azureaiagent.ipynb)

Tunakuunga mkono ujaribu aina zote tatu za mifano ili kuona ni ipi inakufaa zaidi.

Chaguo lolote utakalochagua, litaamua hatua za usanidi unazohitaji kufuata hapa chini:

## Mahitaji

- Python 3.12+
  - **KUMBUKU**: Ikiwa huna Python3.12 imewekwa, hakikisha unaiweka.  Kisha unda venv yako ukitumia python3.12 kuhakikisha toleo sahihi zinawekwa kutoka kwa faili requirements.txt.
  
    >Mfano

    Create Python venv directory:

    ```bash|powershell
    python -m venv venv
    ```

    Then activate venv environment for:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Kwa mifano ya msimbo inayotumia .NET, hakikisha umeweka [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) au baadaye. Kisha, angalia toleo la .NET SDK ulioweka:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Akaunti ya GitHub - Kwa Upatikanaji wa GitHub Models Marketplace
- Usajili wa Azure - Kwa Upatikanaji wa Microsoft Foundry
- Akaunti ya Microsoft Foundry - Kwa Upatikanaji wa Azure AI Agent Service

Tumeweka faili `requirements.txt` katika mzizi wa repositori hii inayojumuisha vifurushi vyote vya Python vinavyohitajika kuendesha mifano ya msimbo.

Unaweza kuviweka kwa kuendesha amri ifuatayo katika terminal yako kwenye mzizi wa repositori:

```bash|powershell
pip install -r requirements.txt
```

Tunashauri kuunda mazingira ya kimazingira (virtual environment) ya Python ili kuepuka migongano na matatizo.

## Sanidi VSCode

Hakikisha unatumia toleo sahihi la Python katika VSCode.

![picha](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Sanidi kwa Mifano inayotumia GitHub Models 

### Hatua 1: Pata Tokeni Yako ya Ufikiaji wa Binafsi ya GitHub (PAT)

Kozi hii inatumia GitHub Models Marketplace, inayotoa upatikanaji wa bure kwa Large Language Models (LLMs) utakazotumia kujenga AI Agents.

Ili kutumia GitHub Models, utahitaji kuunda a [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

This can be done by going to your <a href="https://github.com/settings/personal-access-tokens" target="_blank">Personal Access Tokens settings</a> in your GitHub Account.

Tafadhali fuata the [Principle of Least Privilege](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) when creating your token. This means you should only give the token the permissions it needs to run the code samples in this course.

1. Chagua chaguo la `Fine-grained tokens` upande wa kushoto wa skrini yako kwa kwenda kwenye **Developer settings**

   ![Mipangilio ya Developer](../../../translated_images/sw/profile_developer_settings.410a859fe749c755.webp)

   Kisha chagua `Generate new token`.

   ![Tengeneza Tokeni](../../../translated_images/sw/fga_new_token.1c1a234afe202ab3.webp)

2. Weka jina lenye maelezo kwa tokeni yako linaloonyesha kusudi lake, ili liwe rahisi kutambua baadaye.

    🔐 Mapendekezo ya Muda wa Tokeni

    Muda uliopendekezwa: 30 days
    Kwa usalama zaidi, unaweza kuchagua kipindi kifupi—kama siku 7 🛡️
    Ni njia nzuri ya kuweka lengo la kibinafsi na kumaliza kozi wakati hamasa yako ya kujifunza iko juu 🚀.

    ![Jina la Tokeni na Kumalizika kwa Muda](../../../translated_images/sw/token-name-expiry-date.a095fb0de6386864.webp)

3. Punguza wigo wa tokeni kwa fork yako ya repositori hii.

    ![Punguza wigo kwa fork ya repositori](../../../translated_images/sw/token_repository_limit.924ade5e11d9d8bb.webp)

4. Punguza ruhusa za tokeni: Chini ya **Permissions**, bonyeza kichupo cha **Account**, na bonyeza kitufe cha "+ Add permissions". Menyu itajitokeza. Tafadhali tafuta **Models** na weka tiki kwenye kisanduku chake.

    ![Ongeza Ruhusa za Models](../../../translated_images/sw/add_models_permissions.c0c44ed8b40fc143.webp)

5. Thibitisha ruhusa zinazohitajika kabla ya kuunda tokeni. ![Thibitisha Ruhusa](../../../translated_images/sw/verify_permissions.06bd9e43987a8b21.webp)

6. Kabla ya kuunda tokeni, hakikisha uko tayari kuhifadhi tokeni kwenye mahali salama kama hifadhi ya wasimamizi wa nywila (password manager), kwani haitaonyeshwa tena baada ya kuunda. ![Hifadhi Tokeni Salama](../../../translated_images/sw/store_token_securely.08ee2274c6ad6caf.webp)

Nakili tokeni yako mpya uliyotengeneza. Sasa itaongeza kwenye faili yako `.env` iliyomo katika kozi hii.

### Hatua 2: Tengeneza Faili Yako `.env`

To create your `.env` file run the following command in your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Hii itakopa faili la mfano na kuunda `.env` katika saraka yako, ambapo utakamilisha thamani za vigezo vya mazingira.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `GITHUB_TOKEN` field.

![Uwanja wa Tokeni ya GitHub](../../../translated_images/sw/github_token_field.20491ed3224b5f4a.webp)

Sasa unapaswa kuwa na uwezo wa kuendesha mifano ya msimbo ya kozi hii.

## Sanidi kwa Mifano inayotumia Microsoft Foundry na Azure AI Agent Service

### Hatua 1: Pata Endpoint ya Mradi wako wa Azure


Follow the steps to creating a hub and project in Azure AI Foundry found here: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you have created your project, you will need to retrieve the connection string for your project.

Hii inaweza kufanywa kwa kwenda kwenye ukurasa wa **Overview** wa mradi wako katika bandari ya Microsoft Foundry.

![Connection String ya Mradi](../../../translated_images/sw/project-endpoint.8cf04c9975bbfbf1.webp)

### Hatua 2: Tengeneza Faili Yako `.env`

To create your `.env` file run the following command in your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Hii itakopa faili la mfano na kuunda `.env` katika saraka yako, ambapo utakamilisha thamani za vigezo vya mazingira.

Baada ya kunakili tokeni yako, fungua faili `.env` katika mhariri unaoupenda na weka tokeni yako kwenye uwanja `PROJECT_ENDPOINT`.

### Hatua 3: Ingia kwenye Azure

Kama njia bora ya usalama, tutatumia [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) kuji-authenticate kwa Azure OpenAI kwa kutumia Microsoft Entra ID. 

Next, open a terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you've logged in, select your subscription in the terminal.

## Vigezo vya Mazingira Zaidi - Azure Search na Azure OpenAI 

Kwa Somo la Agentic RAG - Somo la 5 - kuna mifano inayotumia Azure Search na Azure OpenAI.

Iki unataka kuendesha mifano hii, utahitaji kuongeza vigezo vya mazingira vifuatavyo kwenye faili yako `.env`:

### Ukurasa wa Muhtasari (Mradi)

- `AZURE_SUBSCRIPTION_ID` - Angalia **Project details** kwenye ukurasa wa **Overview** wa mradi wako.

- `AZURE_AI_PROJECT_NAME` - Angalia sehemu ya juu ya ukurasa wa **Overview** wa mradi wako.

- `AZURE_OPENAI_SERVICE` - Tafuta hii kwenye kichupo cha **Included capabilities** kwa **Azure OpenAI Service** kwenye ukurasa wa **Overview**.

### Kituo cha Usimamizi

- `AZURE_OPENAI_RESOURCE_GROUP` - Nenda kwenye **Project properties** kwenye ukurasa wa **Overview** wa **Management Center**.

- `GLOBAL_LLM_SERVICE` - Chini ya **Connected resources**, tafuta jina la muunganisho wa **Azure AI Services**. Ikiwa halijatolewa, angalia **Azure portal** chini ya resource group yako kwa jina la rasilimali ya AI Services.

### Ukurasa wa Models + Endpoints

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Chagua modeli yako ya embedding (mfano, `text-embedding-ada-002`) na kumbuka **Deployment name** kutoka kwa maelezo ya modeli.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Chagua modeli yako ya chat (mfano, `gpt-4o-mini`) na kumbuka **Deployment name** kutoka kwa maelezo ya modeli.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - Tafuta **Azure AI services**, ibonyeze, kisha nenda kwenye **Resource Management**, **Keys and Endpoint**, punguza hadi kwenye "Azure OpenAI endpoints", na nakili ile inayosema "Language APIs".

- `AZURE_OPENAI_API_KEY` - Kutoka kwenye skrini ile ile, nakili KEY 1 au KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Tafuta rasilimali yako ya **Azure AI Search**, ibonyeze, na ona **Overview**.

- `AZURE_SEARCH_API_KEY` - Kisha nenda **Settings** na kisha **Keys** ili kunakili ufunguo mkuu au wa pili wa admin.

### Tovuti ya Nje

- `AZURE_OPENAI_API_VERSION` - Tembelea the [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) page under **Latest GA API release**.

### Sanidi uthibitishaji bila funguo

Badala ya kuweka sifa zako (credentials) moja kwa moja ndani ya msimbo, tutatumia muunganisho unaofanya bila funguo (keyless) na Azure OpenAI. Kufanya hivyo, tutaingiza `DefaultAzureCredential` na baadaye kuita kazi ya `DefaultAzureCredential` ili kupata uthibitisho.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Umekwama Wapi?
Iwapo una matatizo yoyote kuendesha usanidi huu, jiunge kwenye <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord ya Jumuiya ya Azure AI</a> au <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">tengeneza suala</a>.

## Somo Ifuatayo

Sasa uko tayari kuendesha msimbo wa kozi hii. Furahia kujifunza zaidi kuhusu ulimwengu wa mawakala wa AI! 

[Utangulizi wa Mawakala wa AI na Matumizi ya Mawakala](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Tamko la kutokuwajibika:
Hati hii imetafsiriwa kwa kutumia huduma ya tafsiri ya AI [Co-op Translator](https://github.com/Azure/co-op-translator). Ingawa tunajitahidi kuhakikisha usahihi, tafadhali fahamu kwamba tafsiri za kiotomatiki zinaweza kuwa na makosa au ukosefu wa usahihi. Nakala ya awali ya hati hii katika lugha yake ya asili inapaswa kuchukuliwa kama chanzo chenye mamlaka. Kwa taarifa muhimu, inapendekezwa kutumia tafsiri ya kitaalamu iliyofanywa na mtafsiri wa binadamu. Hatutawajibika kwa maelewano mabaya au tafsiri zisizo sahihi zinazotokana na matumizi ya tafsiri hii.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->