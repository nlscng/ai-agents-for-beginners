# Configuração do Curso

## Introdução

Esta lição cobrirá como executar os exemplos de código deste curso.

## Junte-se a Outros Aprendizes e Obtenha Ajuda

Antes de começar a clonar seu repositório, junte-se ao [canal do Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord) para obter ajuda com a configuração, tirar dúvidas sobre o curso ou se conectar com outros aprendizes.

## Clonar ou Fazer Fork deste Repositório

Para começar, por favor clone ou faça fork do repositório do GitHub. Isso criará sua própria versão do material do curso para que você possa executar, testar e ajustar o código!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fazer fork do repositório</a>

You should now have your own forked version of this course in the following link:

![Repositório Forkado](../../../translated_images/pt-BR/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (recomendado para workshop / Codespaces)

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

## Executando o Código

This course offers a series of Jupyter Notebooks that you can run with to get hands-on experience building AI Agents.

The code samples use either:

**Requires GitHub Account - Free**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Labelled as (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Labeled as (autogen.ipynb)

**Requires Azure Subscription**:
3) Azure AI Foundry + Azure AI Agent Service. Labelled as (azureaiagent.ipynb)

We encourage you to try out all three types of examples to see which one works best for you.

Whichever option you choose, it will determine which setup steps you need to follow below:

## Requisitos

- Python 3.12+
  - **NOTA**: Se você não tem o Python3.12 instalado, certifique-se de instalá-lo. Em seguida, crie seu venv usando python3.12 para garantir que as versões corretas sejam instaladas a partir do arquivo requirements.txt.
  
    >Exemplo

    Crie o diretório venv do Python:

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

We have included a `requirements.txt` file in the root of this repository that contains all the required Python packages to run the code samples.

You can install them by running the following command in your terminal at the root of the repository:

```bash|powershell
pip install -r requirements.txt
```

We recommend creating a Python virtual environment to avoid any conflicts and issues.

## Configurar o VSCode

Certifique-se de que está usando a versão correta do Python no VSCode.

![imagem](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Configuração para exemplos que usam GitHub Models 

### Etapa 1: Recupere seu Token de Acesso Pessoal do GitHub (PAT)

This course leverages the GitHub Models Marketplace, providing free access to Large Language Models (LLMs) that you will use to build AI Agents.

To use the GitHub Models, you will need to create a [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

This can be done by going to your <a href="https://github.com/settings/personal-access-tokens" target="_blank">Configurações de Personal Access Tokens</a> in your GitHub Account.

Please follow the [Principle of Least Privilege](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) when creating your token. This means you should only give the token the permissions it needs to run the code samples in this course.

1. Select the `Fine-grained tokens` option on the left side of your screen by traversing to the **Developer settings**

   ![Configurações do desenvolvedor](../../../translated_images/pt-BR/profile_developer_settings.410a859fe749c755.webp)

   Then select `Generate new token`.

   ![Gerar Token](../../../translated_images/pt-BR/fga_new_token.1c1a234afe202ab3.webp)

2. Enter a descriptive name for your token that reflects its purpose, making it easy to identify later.

    🔐 Token Duration Recommendation

    Recommended duration: 30 days
    For a more secure posture, you can opt for a shorter period—such as 7 days 🛡️
    It’s a great way to set a personal target and complete the course while your learning momentum is high 🚀.

    ![Nome do Token e Expiração](../../../translated_images/pt-BR/token-name-expiry-date.a095fb0de6386864.webp)

3. Limit the token's scope to your fork of this repository.

    ![Limitar escopo ao repositório forkado](../../../translated_images/pt-BR/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restrict the token's permissions: Under **Permissions**, click **Account** tab, and click the "+ Add permissions" button. A dropdown will appear. Please search for **Models** and check the box for it.

    ![Adicionar Permissão Models](../../../translated_images/pt-BR/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verify the permissions required before generating the token. ![Verificar Permissões](../../../translated_images/pt-BR/verify_permissions.06bd9e43987a8b21.webp)

6. Before generating the token, ensure you are ready to store the token in a secure place like a password manager vault, as it will not be shown again after you create it. ![Armazenar Token com Segurança](../../../translated_images/pt-BR/store_token_securely.08ee2274c6ad6caf.webp)

Copy your new token that you have just created. You will now add this to your `.env` file included in this course.

### Etapa 2: Crie seu arquivo `.env`

To create your `.env` file run the following command in your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `GITHUB_TOKEN` field.

![Campo do Token do GitHub](../../../translated_images/pt-BR/github_token_field.20491ed3224b5f4a.webp)

You should now be able to run the code samples of this course.

## Configuração para exemplos que usam Microsoft Foundry e Azure AI Agent Service

### Etapa 1: Recupere o Endpoint do seu Projeto Azure


Follow the steps to creating a hub and project in Azure AI Foundry found here: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you have created your project, you will need to retrieve the connection string for your project.

This can be done by going to the **Overview** page of your project in the Microsoft Foundry portal.

![String de Conexão do Projeto](../../../translated_images/pt-BR/project-endpoint.8cf04c9975bbfbf1.webp)

### Etapa 2: Crie seu arquivo `.env`

To create your `.env` file run the following command in your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `PROJECT_ENDPOINT` field.

### Etapa 3: Faça login no Azure

As a security best practice, we'll use [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) to authenticate to Azure OpenAI with Microsoft Entra ID. 

Next, open a terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you've logged in, select your subscription in the terminal.

## Variáveis de Ambiente Adicionais - Azure Search e Azure OpenAI 

For the Agentic RAG Lesson - Lesson 5 - there are samples that use Azure Search and Azure OpenAI.

If you want to run these samples, you will need to add the following environment variables to your `.env` file:

### Overview Page (Project)

- `AZURE_SUBSCRIPTION_ID` - Verifique **Project details** na página **Overview** do seu projeto.

- `AZURE_AI_PROJECT_NAME` - Olhe no topo da página **Overview** do seu projeto.

- `AZURE_OPENAI_SERVICE` - Encontre isso na aba **Included capabilities** para **Azure OpenAI Service** na página **Overview**.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - Vá para **Project properties** na página **Overview** do **Management Center**.

- `GLOBAL_LLM_SERVICE` - Em **Connected resources**, encontre o nome da conexão **Azure AI Services**. If not listed, check the **Azure portal** under your resource group for the AI Services resource name.

### Models + Endpoints Page

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Selecione seu embedding model (e.g., `text-embedding-ada-002`) e anote o **Deployment name** nos detalhes do modelo.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Selecione seu chat model (e.g., `gpt-4o-mini`) e anote o **Deployment name** nos detalhes do modelo.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - Look for **Azure AI services**, click on it, then go to **Resource Management**, **Keys and Endpoint**, scroll down to the "Azure OpenAI endpoints", and copy the one that says "Language APIs".

- `AZURE_OPENAI_API_KEY` - From the same screen, copy KEY 1 or KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Find your **Azure AI Search** resource, click it, and see **Overview**.

- `AZURE_SEARCH_API_KEY` - Then go to **Settings** and then **Keys** to copy the primary or secondary admin key.

### External Webpage

- `AZURE_OPENAI_API_VERSION` - Visit the [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) page under **Latest GA API release**.

### Setup keyless authentication

Rather than hardcode your credentials, we'll use a keyless connection with Azure OpenAI. To do so, we'll import `DefaultAzureCredential` and later call the `DefaultAzureCredential` function to get the credential.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Preso em Algum Lugar?
Se você tiver qualquer problema ao executar esta configuração, entre no nosso <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord da Comunidade Azure AI</a> ou <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">crie uma issue</a>.

## Próxima Lição

Você agora está pronto para executar o código deste curso. Bom aprendizado sobre o mundo dos Agentes de IA! 

[Introdução aos Agentes de IA e Casos de Uso de Agentes](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Isenção de responsabilidade**:
Este documento foi traduzido usando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para manter a precisão, esteja ciente de que traduções automatizadas podem conter erros ou imprecisões. A versão original do documento, em seu idioma nativo, deve ser considerada a fonte autoritativa. Para informações críticas, recomendamos tradução profissional feita por tradutores humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações equivocadas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->