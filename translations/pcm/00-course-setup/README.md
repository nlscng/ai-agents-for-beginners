# How to Setup Di Course

## Introduction

Dis lesson go show how you fit run di code samples for dis course.

## Join Other Learners and Get Help

Before you begin to clone your repo, join di [AI Agents For Beginners Discord channel](https://aka.ms/ai-agents/discord) make you fit get help wit setup, ask questions about di course, or connect wit oda learners.

## Clone or Fork this Repo

To start, abeg clone or fork di GitHub Repository. Dis go give you your own copy of di course material make you fit run, test, and change di code!

You fit do am by clicking di link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fork the repo</a>

You suppose don get your own forked version of dis course for dis link:

![Repo wey you fork](../../../translated_images/pcm/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (recommended for workshop / Codespaces)

  >Di full repository fit big (~3 GB) if you download full history and all files. If na only workshop you dey attend or you only need small number of lesson folders, shallow clone (or sparse clone) go spare most of dat download by cutting history and/or skipping blobs.

#### Quick shallow clone — minimal history, all files

Replace `<your-username>` for di commands below with your fork URL (or di upstream URL if you prefer).

To clone only di latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Partial (sparse) clone — minimal blobs + only selected folders

Dis one dey use partial clone and sparse-checkout (you go need Git 2.25+ and modern Git wey support partial clone):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Traverse into di repo folder:

```bash|powershell
cd ai-agents-for-beginners
```

Then specify which folders you want (example below dey show two folders):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

After you don clone and check di files, if na only files you want and you wan free space (no git history), abeg delete di repository metadata (💀no reversible — you go lose all Git functionality: no commits, pulls, pushes, or history access).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Using GitHub Codespaces (recommended to avoid local large downloads)

- Create new Codespace for dis repo via di [GitHub UI](https://github.com/codespaces).  

- For di terminal of di new Codespace, run one of di shallow/sparse clone commands wey dey above to bring only di lesson folders wey you need enter di Codespace workspace.
- Optional: after you clone inside Codespaces, remove .git to get extra space back (see removal commands wey dey above).
- Note: If you prefer to open di repo direct for Codespaces (without extra clone), make you sabi say Codespaces go still build di devcontainer environment and fit still provision more than you need. Cloning small shallow copy inside fresh Codespace go give you more control for disk usage.

#### Tips

- Always change di clone URL to your fork if you want to edit/commit.
- If later you need more history or files, you fit fetch dem or adjust sparse-checkout to include extra folders.

## Running the Code

Dis course get serie of Jupyter Notebooks wey you fit run to get hands-on experience to build AI Agents.

Di code samples dey use either:

**Requires GitHub Account - Free**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Labelled as (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Labeled as (autogen.ipynb)

**Requires Azure Subscription**:
3) Azure AI Foundry + Azure AI Agent Service. Labelled as (azureaiagent.ipynb)

We dey encourage make you try out all three kind examples make you see which one dey work best for you.

Which ever option you choose, e go determine which setup steps you suppose follow below:

## Requirements

- Python 3.12+
  - **NOTE**: If you never get Python3.12 installed, make you install am. Then create your venv using python3.12 make e ensure correct versions dey installed from di requirements.txt file.
  
    >Example

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

- .NET 10+: For di sample codes wey dey use .NET, make sure say you install [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) or later. Then, check di .NET SDK version wey you don install:

    ```bash|powershell
    dotnet --list-sdks
    ```

- A GitHub Account - For Access to di GitHub Models Marketplace
- Azure Subscription - For Access to Microsoft Foundry
- Microsoft Foundry Account - For Access to di Azure AI Agent Service

We don include `requirements.txt` file for root of dis repository wey get all di Python packages wey you need run di code samples.

You fit install dem by running di command below for your terminal at di root of di repository:

```bash|powershell
pip install -r requirements.txt
```

We recommend say you create Python virtual environment make e avoid any conflicts and wahala.

## Setup VSCode

Make sure say you dey use di correct version of Python for VSCode.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Set Up for Samples using GitHub Models 

### Step 1: Retrieve Your GitHub Personal Access Token (PAT)

Dis course dey use di GitHub Models Marketplace, wey dey give free access to Large Language Models (LLMs) wey you go use to build AI Agents.

To use di GitHub Models, you go need create [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

You fit do am by going to your <a href="https://github.com/settings/personal-access-tokens" target="_blank">Personal Access Tokens settings</a> for your GitHub Account.

Abeg follow di [Principle of Least Privilege](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) when you dey create your token. This mean say give di token only di permissions wey e need make di code samples for dis course fit run.

1. Select di `Fine-grained tokens` option for di left side of your screen by going into di **Developer settings**

   ![Developer settings](../../../translated_images/pcm/profile_developer_settings.410a859fe749c755.webp)

   Then select `Generate new token`.

   ![Generate Token](../../../translated_images/pcm/fga_new_token.1c1a234afe202ab3.webp)

2. Put one descriptive name for your token wey go show wetin e dey do, make e easy to sabi later.

    🔐 Token Duration Recommendation

    Recommended duration: 30 days
    If you want more secure, you fit choose shorter time—like 7 days 🛡️
    Na good way to set personal target and finish di course while your learning momentum dey high 🚀.

    ![Token Name and Expiration](../../../translated_images/pcm/token-name-expiry-date.a095fb0de6386864.webp)

3. Limit di token scope to your fork of dis repository.

    ![Limit scope to fork repository](../../../translated_images/pcm/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restrict di token permissions: Under **Permissions**, click **Account** tab, then click di "+ Add permissions" button. Dropdown go show. Abeg search for **Models** and tick di box for am.

    ![Add Models Permission](../../../translated_images/pcm/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verify di permissions wey you need before you generate di token. ![Verify Permissions](../../../translated_images/pcm/verify_permissions.06bd9e43987a8b21.webp)

6. Before you generate di token, make sure say you ready to store di token for secure place like password manager vault, because dem no go show am again after you create am. ![Store Token Securely](../../../translated_images/pcm/store_token_securely.08ee2274c6ad6caf.webp)

Copy your new token wey you just create. You go add am to your `.env` file wey dey included for dis course.

### Step 2: Create Your `.env` File

To create your `.env` file run di command below for your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dis one go copy di example file and create `.env` for your directory where you go fill di values for di environment variables.

With your token wey you don copy, open di `.env` file for your text editor wey you like and paste your token inside di `GITHUB_TOKEN` field.

![GitHub Token Field](../../../translated_images/pcm/github_token_field.20491ed3224b5f4a.webp)

You suppose fit run di code samples for dis course now.

## Set Up for Samples using Microsoft Foundry and Azure AI Agent Service

### Step 1: Retrieve Your Azure Project Endpoint


Follow di steps to create hub and project for Azure AI Foundry wey dey here: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you don create your project, you go need to get di connection string for your project.

You fit do am by going to di **Overview** page of your project for di Microsoft Foundry portal.

![Project Connection String](../../../translated_images/pcm/project-endpoint.8cf04c9975bbfbf1.webp)

### Step 2: Create Your `.env` File

To create your `.env` file run di command below for your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dis one go copy di example file and create `.env` for your directory where you go fill di values for di environment variables.

With your token wey you don copy, open di `.env` file for your favourite text editor and paste your token inside di `PROJECT_ENDPOINT` field.

### Step 3: Sign in to Azure

As security best practice, we go use [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) to authenticate to Azure OpenAI with Microsoft Entra ID. 

Next, open terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you don log in, select your subscription for di terminal.

## Additional Environment Variables - Azure Search and Azure OpenAI 

For di Agentic RAG Lesson - Lesson 5 - some samples dey wey dey use Azure Search and Azure OpenAI.

If you want run these samples, you go need add di following environment variables to your `.env` file:

### Overview Page (Project)

- `AZURE_SUBSCRIPTION_ID` - Check **Project details** for di **Overview** page of your project.

- `AZURE_AI_PROJECT_NAME` - Look for di top of di **Overview** page for your project.

- `AZURE_OPENAI_SERVICE` - Find dis one for di **Included capabilities** tab for **Azure OpenAI Service** on di **Overview** page.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - Go to **Project properties** on di **Overview** page of di **Management Center**.

- `GLOBAL_LLM_SERVICE` - Under **Connected resources**, find di **Azure AI Services** connection name. If e no dey there, check di **Azure portal** under your resource group for di AI Services resource name.

### Models + Endpoints Page

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Select your embedding model (e.g., `text-embedding-ada-002`) and note di **Deployment name** from di model details.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Select your chat model (e.g., `gpt-4o-mini`) and note di **Deployment name** from di model details.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - Find **Azure AI services**, click am, then go to **Resource Management**, **Keys and Endpoint**, scroll down to di "Azure OpenAI endpoints", copy di one wey talk "Language APIs".

- `AZURE_OPENAI_API_KEY` - For di same screen, copy KEY 1 or KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Find your **Azure AI Search** resource, click am, then check **Overview**.

- `AZURE_SEARCH_API_KEY` - Then go to **Settings** and then **Keys** to copy di primary or secondary admin key.

### External Webpage

- `AZURE_OPENAI_API_VERSION` - Visit di [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) page under **Latest GA API release**.

### Setup keyless authentication

Instead of hardcoding your credentials, we go use keyless connection with Azure OpenAI. To do am, we go import `DefaultAzureCredential` and later call di `DefaultAzureCredential` function to get di credential.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Stuck Somewhere?
If you get any wahala running dis setup, waka join our <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> or <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">open one issue</a>.

## Next Leson

You don ready now to run the code for dis course. Enjoy learnin more about the world of AI Agents! 

[Intro to AI Agents and How Dem Dey Use Dem](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Disclaimer:
Na AI translation service (Co-op Translator - https://github.com/Azure/co-op-translator) translate this document. Even though we dey try make am correct, make you sabi say automated translations fit get mistakes or no too accurate. Make you treat the original document wey dey im own language as the official source. If na serious or important information, better make professional human translator check or translate am. We no dey responsible for any misunderstanding or wrong interpretation wey fit come from using this translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->