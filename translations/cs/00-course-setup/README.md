# Nastavení kurzu

## Úvod

Tato lekce pokryje, jak spouštět ukázky kódu tohoto kurzu.

## Připojte se k ostatním studentům a získejte pomoc

Než začnete klonovat své repo, připojte se k [Discord kanálu AI Agents For Beginners](https://aka.ms/ai-agents/discord), abyste získali pomoc s nastavením, mohli zodpovědět dotazy ohledně kurzu nebo se spojit s ostatními studenty.

## Klonování nebo vytvoření forku tohoto repozitáře

Pro začátek prosím klonujte nebo vytvořte fork GitHub repozitáře. Tím získáte vlastní verzi materiálů kurzu, abyste mohli kód spouštět, testovat a upravovat!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">vytvořit fork repozitáře</a>

Nyní byste měli mít vlastní fork tohoto kurzu na následujícím odkazu:

![Forkovaný repozitář](../../../translated_images/cs/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (doporučeno pro workshop / Codespaces)

  >Celý repozitář může být velký (~3 GB) když stáhnete celou historii a všechny soubory. Pokud se účastníte pouze workshopu nebo potřebujete jen několik složek lekcí, shallow clone (nebo sparse clone) se vyhne většině tohoto stahování tím, že ořízne historii a/nebo přeskočí bloby.

#### Rychlý shallow clone — minimální historie, všechny soubory

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

To clone only the latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Partial (sparse) clone — minimální bloby + pouze vybrané složky

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

#### Používání GitHub Codespaces (doporučeno k vyhnutí se velkým lokálním stažením)

- Vytvořte nový Codespace pro tento repozitář přes [uživatelské rozhraní GitHubu](https://github.com/codespaces).  

- V terminálu nově vytvořeného codespace spusťte jeden z výše uvedených shallow/sparse clone příkazů, aby se do pracovního prostoru Codespace načetly pouze potřebné složky lekcí.
- Volitelné: po klonování uvnitř Codespaces odstraňte .git pro uvolnění místa (viz příkazy pro odstranění výše).
- Poznámka: Pokud preferujete otevřít repozitář přímo v Codespaces (bez dalšího klonování), mějte na paměti, že Codespaces sestaví devcontainer prostředí a může stále zprovoznit více, než potřebujete. Klonování shallow kopie uvnitř nového Codespace vám dává větší kontrolu nad využitím disku.

#### Tipy

- Vždy nahraďte URL klonování URL vašeho forku, pokud chcete upravovat/commitovat.
- Pokud budete později potřebovat více historie nebo souborů, můžete je stáhnout (fetch) nebo upravit sparse-checkout, aby zahrnoval další složky.

## Spouštění kódu

Tento kurz nabízí řadu Jupyter Notebooků, které můžete spustit, abyste získali praktické zkušenosti s vytvářením AI agentů.

The code samples use either:

**Vyžaduje GitHub účet - Zdarma**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Označeno jako (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Označeno jako (autogen.ipynb)

**Vyžaduje předplatné Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Označeno jako (azureaiagent.ipynb)

Doporučujeme vyzkoušet všechny tři typy příkladů, abyste zjistili, který vám nejlépe vyhovuje.

Kteroukoli možnost si vyberete, určí, které kroky nastavení níže budete muset následovat:

## Požadavky

- Python 3.12+
  - **POZNÁMKA**: Pokud nemáte nainstalovaný Python 3.12, nainstalujte jej. Poté vytvořte své venv pomocí python3.12, aby se zajistilo nainstalování správných verzí z requirements.txt souboru.
  
    >Příklad

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

- A GitHub Account - For Access to the GitHub Models Marketplace
- Azure Subscription - For Access to Microsoft Foundry
- Microsoft Foundry Account - For Access to the Azure AI Agent Service

Do kořenového adresáře tohoto repozitáře jsme zahrnuli soubor `requirements.txt`, který obsahuje všechny požadované Python balíčky pro spuštění ukázek kódu.

Můžete je nainstalovat spuštěním následujícího příkazu v terminálu v kořenovém adresáři repozitáře:

```bash|powershell
pip install -r requirements.txt
```

Doporučujeme vytvořit Python virtuální prostředí, aby se zabránilo konfliktům a problémům.

## Nastavení VSCode

Ujistěte se, že ve VSCode používáte správnou verzi Pythonu.

![obrázek](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Nastavení pro ukázky používající GitHub Models 

### Krok 1: Získejte svůj GitHub Personal Access Token (PAT)

Tento kurz využívá GitHub Models Marketplace, který poskytuje bezplatný přístup k velkým jazykovým modelům (LLM), které budete používat k vytváření AI agentů.

Pro použití GitHub Models budete muset vytvořit [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

This can be done by going to your <a href="https://github.com/settings/personal-access-tokens" target="_blank">nastavení osobních přístupových tokenů</a> in your GitHub Account.

Dodržujte prosím [Principle of Least Privilege](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) při vytváření tokenu. To znamená, že token by měl mít pouze ta oprávnění, která potřebuje ke spuštění ukázek kódu v tomto kurzu.

1. Select the `Fine-grained tokens` option on the left side of your screen by traversing to the **Nastavení vývojáře**

   ![Nastavení vývojáře](../../../translated_images/cs/profile_developer_settings.410a859fe749c755.webp)

   Then select `Generate new token`.

   ![Vygenerovat token](../../../translated_images/cs/fga_new_token.1c1a234afe202ab3.webp)

2. Enter a descriptive name for your token that reflects its purpose, making it easy to identify later.

    🔐 Doporučená doba platnosti tokenu

    Doporučená doba: 30 dní
    Pro větší bezpečnost můžete zvolit kratší období—například 7 dní 🛡️
    Je to skvělý způsob, jak si nastavit osobní cíl a dokončit kurz, zatímco máte vysokou učební motivaci 🚀.

    ![Název tokenu a vypršení platnosti](../../../translated_images/cs/token-name-expiry-date.a095fb0de6386864.webp)

3. Limit the token's scope to your fork of this repository.

    ![Omezit rozsah na fork repozitáře](../../../translated_images/cs/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restrict the token's permissions: Under **Permissions**, click **Account** tab, and click the "+ Add permissions" button. A dropdown will appear. Please search for **Models** and check the box for it.

    ![Přidat oprávnění Models](../../../translated_images/cs/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verify the permissions required before generating the token. ![Ověřit oprávnění](../../../translated_images/cs/verify_permissions.06bd9e43987a8b21.webp)

6. Before generating the token, ensure you are ready to store the token in a secure place like a password manager vault, as it will not be shown again after you create it. ![Uložit token zabezpečeně](../../../translated_images/cs/store_token_securely.08ee2274c6ad6caf.webp)

Copy your new token that you have just created. You will now add this to your `.env` file included in this course.

### Krok 2: Vytvořte soubor `.env`

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

![Pole GitHub tokenu](../../../translated_images/cs/github_token_field.20491ed3224b5f4a.webp)

You should now be able to run the code samples of this course.

## Nastavení pro ukázky využívající Microsoft Foundry a Azure AI Agent Service

### Krok 1: Získejte koncový bod (endpoint) vašeho Azure projektu


Follow the steps to creating a hub and project in Azure AI Foundry found here: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you have created your project, you will need to retrieve the connection string for your project.

This can be done by going to the **Overview** page of your project in the Microsoft Foundry portal.

![Připojovací řetězec projektu](../../../translated_images/cs/project-endpoint.8cf04c9975bbfbf1.webp)

### Krok 2: Vytvořte soubor `.env`

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

Po zkopírování připojovacího řetězce otevřete `.env` ve svém oblíbeném textovém editoru a vložte ho do pole `PROJECT_ENDPOINT`.

### Krok 3: Přihlaste se do Azure

Jako osvědčený bezpečnostní postup použijeme [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) pro autentizaci do Azure OpenAI pomocí Microsoft Entra ID. 

Next, open a terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you've logged in, select your subscription in the terminal.

## Další proměnné prostředí - Azure Search a Azure OpenAI 

For the Agentic RAG Lesson - Lesson 5 - there are samples that use Azure Search and Azure OpenAI.

If you want to run these samples, you will need to add the following environment variables to your `.env` file:

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

### Nastavení keyless autentizace

Rather than hardcode your credentials, we'll use a keyless connection with Azure OpenAI. To do so, we'll import `DefaultAzureCredential` and later call the `DefaultAzureCredential` function to get the credential.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Zasekli jste se někde?
Pokud máte při spuštění tohoto nastavení nějaké potíže, připojte se na náš <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord komunity Azure AI</a> nebo <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">nahlaste problém</a>.

## Další lekce

Nyní jste připraveni spustit kód tohoto kurzu. Přejeme vám hodně zábavy při dalším objevování světa AI agentů! 

[Úvod do AI agentů a jejich případů použití](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Prohlášení o vyloučení odpovědnosti:
Tento dokument byl přeložen pomocí AI překladatelské služby Co-op Translator (https://github.com/Azure/co-op-translator). I když usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho mateřském jazyce by měl být považován za závazný zdroj. Pro důležité informace se doporučuje profesionální lidský překlad. Nejsme odpovědní za žádná nedorozumění nebo chybné výklady vyplývající z použití tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->