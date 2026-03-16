# Настройване на курса

## Въведение

В този урок ще разгледаме как да стартирате примерите с код от този курс.

## Присъединете се към други обучаващи се и получете помощ

Преди да започнете да клонирате своето хранилище, присъединете се към [Discord канал за AI агенти за начинаещи](https://aka.ms/ai-agents/discord), за да получите помощ със настройката, да зададете въпроси за курса или да се свържете с други обучаващи се.

## Клониране или форкване на това хранилище

За да започнете, моля клонирайте или форквайте GitHub хранилището. Това ще създаде ваша собствена версия на материала от курса, така че да можете да стартирате, тествате и променяте кода!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">форкнете хранилището</a>

You should now have your own forked version of this course in the following link:

![Форкнато хранилище](../../../translated_images/bg/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (recommended for workshop / Codespaces)

  >Пълното хранилище може да бъде голямо (~3 GB) когато изтеглите цялата история и всички файлове. Ако присъствате само на работилницата или се нуждаете само от няколко папки с уроци, плитко клониране (или частично клониране) ще избегне повечето от това изтегляне чрез съкращаване на историята и/или пропускане на blob-ове.

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

- Create a new Codespace for this repo via the [потребителския интерфейс на GitHub](https://github.com/codespaces).  

- В терминала на новосъздадения codespace, изпълнете една от командите за плитко/частично клониране по-горе, за да внесете само папките с уроци, от които имате нужда в работното пространство на Codespace.
- По желание: след клониране вътре в Codespaces, премахнете .git, за да възстановите допълнително място (вижте командите за премахване по-горе).
- Забележка: Ако предпочитате да отворите хранилището директно в Codespaces (без допълнително клониране), имайте предвид, че Codespaces ще конструира devcontainer средата и все още може да предостави повече от необходимото. Клонирането на плитко копие вътре в нов Codespace ви дава повече контрол върху използването на диска.

#### Tips

- Always replace the clone URL with your fork if you want to edit/commit.
- If you later need more history or files, you can fetch them or adjust sparse-checkout to include additional folders.

## Стартиране на кода

This course offers a series of Jupyter Notebooks that you can run with to get hands-on experience building AI Agents.

The code samples use either:

**Изисква GitHub акаунт - безплатно**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Labelled as (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Labeled as (autogen.ipynb)

**Изисква Azure абонамент**:
3) Azure AI Foundry + Azure AI Agent Service. Labelled as (azureaiagent.ipynb)

We encourage you to try out all three types of examples to see which one works best for you.

Whichever option you choose, it will determine which setup steps you need to follow below:

## Изисквания

- Python 3.12+
  - **ЗАБЕЛЕЖКА**: Ако нямате инсталиран Python 3.12, уверете се, че го инсталирате.  След това създайте виртуална среда (venv) с python3.12, за да гарантирате, че правилните версии се инсталират от файла requirements.txt.
  
    >Пример

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

- .NET 10+: For the sample codes using .NET, ensure you install [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) or later. Then, check your installed .NET SDK version:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub акаунт - за достъп до GitHub Models Marketplace
- Azure абонамент - за достъп до Microsoft Foundry
- Microsoft Foundry акаунт - за достъп до Azure AI Agent Service

В корена на това хранилище сме включили файл `requirements.txt`, който съдържа всички необходими Python пакети за стартиране на примерите с код.

Можете да ги инсталирате, като изпълните следната команда в терминала си в корена на хранилището:

```bash|powershell
pip install -r requirements.txt
```

Препоръчваме да създадете Python виртуална среда, за да избегнете конфликти и проблеми.

## Настройка на VSCode

Уверете се, че използвате правилната версия на Python във VSCode.

![изображение](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Настройка за примерите, използващи GitHub Models 

### Стъпка 1: Получаване на вашия GitHub личен токен за достъп (PAT)

Този курс използва GitHub Models Marketplace, който осигурява безплатен достъп до големи езикови модели (LLMs), които ще използвате за изграждане на AI агенти.

To use the GitHub Models, you will need to create a [GitHub личен токен за достъп](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

This can be done by going to your <a href="https://github.com/settings/personal-access-tokens" target="_blank">настройките за лични токени за достъп</a> in your GitHub Account.

Please follow the [Принципа на най-малките привилегии](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) when creating your token. This means you should only give the token the permissions it needs to run the code samples in this course.

1. Select the `Fine-grained tokens` option on the left side of your screen by traversing to the **Настройки за разработчици**

   ![Настройки за разработчици](../../../translated_images/bg/profile_developer_settings.410a859fe749c755.webp)

   Then select `Generate new token`.

   ![Генериране на токен](../../../translated_images/bg/fga_new_token.1c1a234afe202ab3.webp)

2. Enter a descriptive name for your token that reflects its purpose, making it easy to identify later.

    🔐 Препоръчителна продължителност на токена

    Recommended duration: 30 days
    For a more secure posture, you can opt for a shorter period—such as 7 days 🛡️
    It’s a great way to set a personal target and complete the course while your learning momentum is high 🚀.

    ![Име на токена и срок на изтичане](../../../translated_images/bg/token-name-expiry-date.a095fb0de6386864.webp)

3. Limit the token's scope to your fork of this repository.

    ![Ограничете обхвата до форка на хранилището](../../../translated_images/bg/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restrict the token's permissions: Под **Разрешения**, кликнете върху раздела **Акаунт**, и натиснете бутона „+ Добави разрешения“. Ще се появи падащо меню. Моля потърсете **Models** и отметнете полето за него.

    ![Добавяне на разрешение Models](../../../translated_images/bg/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verify the permissions required before generating the token. ![Потвърдете разрешенията](../../../translated_images/bg/verify_permissions.06bd9e43987a8b21.webp)

6. Before generating the token, ensure you are ready to store the token in a secure place like a password manager vault, as it will not be shown again after you create it. ![Съхранете токена сигурно](../../../translated_images/bg/store_token_securely.08ee2274c6ad6caf.webp)

Copy your new token that you have just created. You will now add this to your `.env` file included in this course.

### Стъпка 2: Създайте вашия `.env` файл

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

![Поле за GitHub токен](../../../translated_images/bg/github_token_field.20491ed3224b5f4a.webp)

You should now be able to run the code samples of this course.

## Настройка за примерите, използващи Microsoft Foundry и Azure AI Agent Service

### Стъпка 1: Получаване на Endpoint на вашия Azure проект


Follow the steps to creating a hub and project in Azure AI Foundry found here: [Преглед на ресурсите на hub](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you have created your project, you will need to retrieve the connection string for your project.

This can be done by going to the **Overview** page of your project in the Microsoft Foundry portal.

![Низ за връзка на проекта](../../../translated_images/bg/project-endpoint.8cf04c9975bbfbf1.webp)

### Стъпка 2: Създайте вашия `.env` файл

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

### Стъпка 3: Влезте в Azure

Като добра практика за сигурност, ще използваме [автентикация без ключ](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) за удостоверяване към Azure OpenAI с Microsoft Entra ID. 

Next, open a terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you've logged in, select your subscription in the terminal.

## Допълнителни променливи на средата - Azure Search и Azure OpenAI 

For the Agentic RAG Lesson - Lesson 5 - there are samples that use Azure Search and Azure OpenAI.

If you want to run these samples, you will need to add the following environment variables to your `.env` file:

### Страница Overview (Проект)

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

### Външна уебстраница

- `AZURE_OPENAI_API_VERSION` - Visit the [Жизнен цикъл на версиите на API](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) page under **Latest GA API release**.

### Настройка на автентикация без ключ

Rather than hardcode your credentials, we'll use a keyless connection with Azure OpenAI. To do so, we'll import `DefaultAzureCredential` and later call the `DefaultAzureCredential` function to get the credential.

```python
# Пайтън
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Заклещени ли сте някъде?
Ако имате проблеми при стартиране на тази конфигурация, присъединете се към нашия <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> или <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">създайте issue</a>.

## Следващ урок

Сега сте готови да стартирате кода за този курс. Приятно учене и успех при опознаването на света на AI агентите! 

[Въведение в AI агентите и случаи на използване на агенти](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Отказ от отговорност:
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматичните преводи могат да съдържат грешки или неточности. Оригиналният документ на езика, на който е написан, трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за каквито и да е недоразумения или погрешни тълкувания, произтичащи от използването на този превод.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->