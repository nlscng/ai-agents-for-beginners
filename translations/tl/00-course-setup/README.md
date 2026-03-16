# Course Setup

## Introduction

Tatalakayin ng araling ito kung paano patakbuhin ang mga code sample ng kursong ito.

## Join Other Learners and Get Help

Bago ka magsimulang i-clone ang iyong repo, sumali sa [AI Agents For Beginners Discord channel](https://aka.ms/ai-agents/discord) para makakuha ng tulong sa pag-setup, mga tanong tungkol sa kurso, o para makipag-ugnayan sa iba pang mga nag-aaral.

## Clone or Fork this Repo

Upang magsimula, i-clone o i-fork ang GitHub Repository. Gagawa ito ng sarili mong bersyon ng materyal ng kurso upang maaari mong patakbuhin, subukan, at baguhin ang code!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">i-fork ang repo</a>

You should now have your own forked version of this course in the following link:

![Naka-fork na Repo](../../../translated_images/tl/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (recommended for workshop / Codespaces)

  >Halimbawa

  Create Python venv directory:

  >The full repository can be large (~3 GB) when you download full history and all files. If you're only attending the workshop or only need a few lesson folders, a shallow clone (or a sparse clone) avoids most of that download by truncating history and/or skipping blobs.

#### Quick shallow clone — minimal history, all files

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

To clone only the latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Partial (sparse) clone — minimal blobs + only selected folders

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

#### Using GitHub Codespaces (recommended to avoid local large downloads)

- Create a new Codespace for this repo via the [GitHub UI](https://github.com/codespaces).  

- In the terminal of the newly created codespace, run one of the shallow/sparse clone commands above to bring only the lesson folders you need into the Codespace workspace.
- Optional: after cloning inside Codespaces, remove .git to reclaim extra space (see removal commands above).
- Note: If you prefer to open the repo directly in Codespaces (without an extra clone), be aware Codespaces will construct the devcontainer environment and may still provision more than you need. Cloning a shallow copy inside a fresh Codespace gives you more control over disk usage.

#### Tips

- Always replace the clone URL with your fork if you want to edit/commit.
- If you later need more history or files, you can fetch them or adjust sparse-checkout to include additional folders.

## Running the Code

This course offers a series of Jupyter Notebooks that you can run with to get hands-on experience building AI Agents.

The code samples use either:

**Requires GitHub Account - Free**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Labelled as (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Labeled as (autogen.ipynb)

**Requires Azure Subscription**:
3) Azure AI Foundry + Azure AI Agent Service. Labelled as (azureaiagent.ipynb)

Hinihikayat ka naming subukan ang lahat ng tatlong uri ng halimbawa upang makita kung alin ang pinakamainam para sa iyo.

Anuman ang piliin mo, iyon ang magtatakda kung aling mga setup na hakbang ang kailangan mong sundin sa ibaba:

## Requirements

- Python 3.12+
  - **TANDAAN**: Kung wala kang Python3.12 na naka-install, tiyaking i-install ito. Pagkatapos ay lumikha ng iyong venv gamit ang python3.12 upang matiyak na ang tamang mga bersyon ang mai-install mula sa requirements.txt file.
  
    >Halimbawa

    Gumawa ng direktoryo ng Python venv:

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

- .NET 10+: For the sample codes using .NET, ensure you install [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) or later. Then, check your installed .NET SDK version:

    ```bash|powershell
    dotnet --list-sdks
    ```

- A GitHub Account - For Access to the GitHub Models Marketplace
- Azure Subscription - For Access to Microsoft Foundry
- Microsoft Foundry Account - For Access to the Azure AI Agent Service

Isinama namin ang isang `requirements.txt` file sa ugat ng repositoryong ito na naglalaman ng lahat ng kinakailangang Python packages upang patakbuhin ang mga code sample.

Maaari mo silang i-install sa pamamagitan ng pagpapatakbo ng sumusunod na command sa iyong terminal sa ugat ng repositoryo:

```bash|powershell
pip install -r requirements.txt
```

Inirerekomenda naming gumawa ng Python virtual environment upang maiwasan ang anumang mga salungatan at isyu.

## Setup VSCode

Tiyaking ginagamit mo ang tamang bersyon ng Python sa VSCode.

![larawan](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Set Up for Samples using GitHub Models 

### Step 1: Retrieve Your GitHub Personal Access Token (PAT)

Kina-kailangan ng kursong ito ang GitHub Models Marketplace, na nagbibigay ng libreng access sa Large Language Models (LLMs) na gagamitin mo upang bumuo ng AI Agents.

Upang magamit ang GitHub Models, kailangan mong gumawa ng [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Magagawa ito sa pamamagitan ng pagpunta sa iyong <a href="https://github.com/settings/personal-access-tokens" target="_blank">Personal Access Tokens settings</a> sa iyong GitHub Account.

Pakitutukan ang [Prinsipyo ng Pinakamababang Pribilehiyo](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) kapag lumilikha ng iyong token. Ibig sabihin nito na dapat mo lamang bigyan ang token ng mga pahintulot na kailangan nito upang patakbuhin ang mga code sample sa kursong ito.

1. Piliin ang `Fine-grained tokens` option sa kaliwang bahagi ng iyong screen sa pamamagitan ng pagpunta sa **Developer settings**

   ![Mga setting ng Developer](../../../translated_images/tl/profile_developer_settings.410a859fe749c755.webp)

   Then select `Generate new token`.

   ![Gumawa ng Token](../../../translated_images/tl/fga_new_token.1c1a234afe202ab3.webp)

2. Ilagay ang isang malinaw na pangalan para sa iyong token na nagpapakita ng layunin nito, upang madali itong makilala sa hinaharap.

    🔐 Token Duration Recommendation

    Recommended duration: 30 days
    For a more secure posture, you can opt for a shorter period—such as 7 days 🛡️
    It’s a great way to set a personal target and complete the course while your learning momentum is high 🚀.

    ![Pangalan ng Token at Pag-expire](../../../translated_images/tl/token-name-expiry-date.a095fb0de6386864.webp)

3. Limitahan ang saklaw ng token sa iyong fork ng repositoryong ito.

    ![I-limit ang saklaw sa fork na repositoryo](../../../translated_images/tl/token_repository_limit.924ade5e11d9d8bb.webp)

4. Limitahan ang mga pahintulot ng token: Sa ilalim ng **Permissions**, i-click ang **Account** tab, at i-click ang "+ Add permissions" button. Lalabas ang isang dropdown. Mangyaring hanapin ang **Models** at i-check ang kahon para dito.

    ![Magdagdag ng Pahintulot ng Models](../../../translated_images/tl/add_models_permissions.c0c44ed8b40fc143.webp)

5. Suriin ang mga kinakailangang pahintulot bago gumawa ng token. ![I-verify ang mga Pahintulot](../../../translated_images/tl/verify_permissions.06bd9e43987a8b21.webp)

6. Bago gumawa ng token, tiyaking handa kang itago ang token sa isang ligtas na lugar tulad ng password manager vault, dahil hindi na ito ipapakita muli matapos mo itong likhain. ![Itago ang Token nang Ligtas](../../../translated_images/tl/store_token_securely.08ee2274c6ad6caf.webp)

Kopyahin ang bagong token na kakalikha mo lang. Idadagdag mo ito ngayon sa iyong `.env` file na kasama sa kursong ito.

### Step 2: Create Your `.env` File

Upang gumawa ng iyong `.env` file patakbuhin ang sumusunod na command sa iyong terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Ii-copy nito ang example file at gagawa ng `.env` sa iyong direktoryo kung saan pupunan mo ang mga halaga para sa mga environment variable.

Kapag nakopya mo na ang token, buksan ang `.env` file sa iyong paboritong text editor at i-paste ang iyong token sa `GITHUB_TOKEN` field.

![Patlang ng GitHub Token](../../../translated_images/tl/github_token_field.20491ed3224b5f4a.webp)

Dapat mo na ngayong magawang patakbuhin ang mga code sample ng kursong ito.

## Set Up for Samples using Microsoft Foundry and Azure AI Agent Service

### Step 1: Retrieve Your Azure Project Endpoint


Sundin ang mga hakbang sa paglikha ng hub at project sa Azure AI Foundry na makikita dito: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Kapag nagawa mo na ang iyong proyekto, kailangan mong kunin ang connection string para sa iyong proyekto.

Magagawa ito sa pamamagitan ng pagpunta sa **Overview** page ng iyong proyekto sa Microsoft Foundry portal.

![Project Connection String](../../../translated_images/tl/project-endpoint.8cf04c9975bbfbf1.webp)

### Step 2: Create Your `.env` File

Upang gumawa ng iyong `.env` file patakbuhin ang sumusunod na command sa iyong terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Ii-copy nito ang example file at gagawa ng `.env` sa iyong direktoryo kung saan pupunan mo ang mga halaga para sa mga environment variable.

Kapag nakopya mo na ang token, buksan ang `.env` file sa iyong paboritong text editor at i-paste ang iyong token sa `PROJECT_ENDPOINT` field.

### Step 3: Sign in to Azure

Bilang isang best practice sa seguridad, gagamit tayo ng [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) upang mag-authenticate sa Azure OpenAI gamit ang Microsoft Entra ID. 

Susunod, buksan ang terminal at patakbuhin ang `az login --use-device-code` upang mag-sign in sa iyong Azure account.

Kapag naka-log in ka na, piliin ang iyong subscription sa terminal.

## Additional Environment Variables - Azure Search and Azure OpenAI 

Para sa Agentic RAG Lesson - Lesson 5 - may mga sample na gumagamit ng Azure Search at Azure OpenAI.

Kung nais mong patakbuhin ang mga sample na ito, kailangan mong idagdag ang mga sumusunod na environment variables sa iyong `.env` file:

### Overview Page (Project)

- `AZURE_SUBSCRIPTION_ID` - Check **Project details** on the **Overview** page of your project.

- `AZURE_AI_PROJECT_NAME` - Look at the top of the **Overview** page for your project.

- `AZURE_OPENAI_SERVICE` - Find this in the **Included capabilities** tab for **Azure OpenAI Service** on the **Overview** page.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - Go to **Project properties** on the **Overview** page of the **Management Center**.

- `GLOBAL_LLM_SERVICE` - Under **Connected resources**, find the **Azure AI Services** connection name. If not listed, check the **Azure portal** under your resource group for the AI Services resource name.

### Models + Endpoints Page

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Select your embedding model (e.g., `text-embedding-ada-002`) and note the **Deployment name** from the model details.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Select your chat model (e.g., `gpt-4o-mini`) and note the **Deployment name** from the model details.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - Look for **Azure AI services**, click on it, then go to **Resource Management**, **Keys and Endpoint**, scroll down to the "Azure OpenAI endpoints", and copy the one that says "Language APIs".

- `AZURE_OPENAI_API_KEY` - From the same screen, copy KEY 1 or KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Find your **Azure AI Search** resource, click it, and see **Overview**.

- `AZURE_SEARCH_API_KEY` - Then go to **Settings** and then **Keys** to copy the primary or secondary admin key.

### External Webpage

- `AZURE_OPENAI_API_VERSION` - Visit the [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) page under **Latest GA API release**.

### Setup keyless authentication

Sa halip na i-hardcode ang iyong mga kredensyal, gagamit tayo ng keyless connection sa Azure OpenAI. Upang gawin ito, i-import natin ang `DefaultAzureCredential` at kalaunan tatawagin ang `DefaultAzureCredential` function upang makuha ang credential.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Stuck Somewhere?


Kung mayroon kang anumang problema sa pagpapatakbo ng pagsasaayos na ito, sumali sa aming <a href="https://discord.gg/kzRShWzttr" target="_blank">Komunidad ng Azure AI sa Discord</a> o <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">magbukas ng isyu</a>.

## Susunod na Aralin

Handa ka na ngayong patakbuhin ang code para sa kursong ito. Masayang matuto pa tungkol sa mundo ng mga AI Agent! 

[Panimula sa mga AI Agent at Mga Kaso ng Paggamit](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Paunawa:
Ang dokumentong ito ay isinalin gamit ang serbisyong AI na pagsasalin na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagaman nagsusumikap kami para sa katumpakan, pakitandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga pagkakamali o hindi tumpak na bahagi. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring na mapagkakatiwalaang pinagmulan. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasaling-pantao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na nagmumula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->