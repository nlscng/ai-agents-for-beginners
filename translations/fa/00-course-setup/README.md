# راه‌اندازی دوره

## معرفی

این درس نحوه اجرای نمونه‌های کد این دوره را پوشش می‌دهد.

## پیوستن به سایر فراگیران و دریافت کمک

قبل از اینکه مخزن خود را کلون کنید، به [کانال Discord «AI Agents For Beginners»](https://aka.ms/ai-agents/discord) بپیوندید تا در نصب، پرسش‌های مربوط به دوره یا ارتباط با سایر فراگیران کمک بگیرید.

## کلون یا فورک این مخزن

برای شروع، لطفاً مخزن GitHub را کلون یا فورک کنید. این کار نسخهٔ خودتان از محتوای دوره را ایجاد می‌کند تا بتوانید کد را اجرا، آزمایش و تغییر دهید!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">فورک کردن مخزن</a>

You should now have your own forked version of this course in the following link:

![مخزن فورک‌شده](../../../translated_images/fa/forked-repo.33f27ca1901baa6a.webp)

### کلون سطحی (توصیه‌شده برای کارگاه / Codespaces)

  > مخزن کامل می‌تواند هنگام دانلود تمام تاریخچه و همه فایل‌ها بزرگ باشد (~3 GB). اگر فقط در کارگاه شرکت می‌کنید یا فقط به چند پوشهٔ درس نیاز دارید، یک کلون سطحی (یا یک کلون پراکنده) با کوتاه‌کردن تاریخچه و/یا نادیده گرفتن بلاب‌ها از بیشتر این دانلود جلوگیری می‌کند.

#### کلون سطحی سریع — تاریخچهٔ حداقلی، همه فایل‌ها

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

To clone only the latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Partial (sparse) clone — بلاب‌های حداقلی + تنها پوشه‌های انتخاب‌شده

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
# زی‌اس‌اچ/باش
rm -rf .git
```

```powershell
# پاورشل
Remove-Item -Recurse -Force .git
```

#### استفاده از GitHub Codespaces (توصیه‌شده برای جلوگیری از دانلودهای بزرگ محلی)

- Create a new Codespace for this repo via the [رابط کاربری GitHub](https://github.com/codespaces).  

- In the terminal of the newly created codespace, run one of the shallow/sparse clone commands above to bring only the lesson folders you need into the Codespace workspace.
- Optional: after cloning inside Codespaces, remove `.git` to reclaim extra space (see removal commands above).
- Note: If you prefer to open the repo directly in Codespaces (without an extra clone), be aware Codespaces will construct the devcontainer environment and may still provision more than you need. Cloning a shallow copy inside a fresh Codespace gives you more control over disk usage.

#### نکات

- Always replace the clone URL with your fork if you want to edit/commit.
- If you later need more history or files, you can fetch them or adjust sparse-checkout to include additional folders.

## اجرای کد

This course offers a series of Jupyter Notebooks that you can run with to get hands-on experience building AI Agents.

The code samples use either:

**نیازمند حساب GitHub - رایگان**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. برچسب‌خورده به‌عنوان (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. برچسب‌خورده به‌عنوان (autogen.ipynb)

**نیازمند اشتراک Azure**:
3) Azure AI Foundry + Azure AI Agent Service. برچسب‌خورده به‌عنوان (azureaiagent.ipynb)

ما شما را تشویق می‌کنیم که هر سه نوع مثال را امتحان کنید تا ببینید کدام‌یک برای شما مناسب‌تر است.

Whichever option you choose, it will determine which setup steps you need to follow below:

## پیش‌نیازها

- Python 3.12+
  - **توجه**: If you don't have Python3.12 installed, ensure you install it.  Then create your venv using python3.12 to ensure the correct versions are installed from the requirements.txt file.
  
    >مثال

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

We have included a `requirements.txt` file in the root of this repository that contains all the required Python packages to run the code samples.

You can install them by running the following command in your terminal at the root of the repository:

```bash|powershell
pip install -r requirements.txt
```

We recommend creating a Python virtual environment to avoid any conflicts and issues.

## تنظیم VSCode

Make sure that you are using the right version of Python in VSCode.

![تصویر](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## تنظیم برای نمونه‌هایی که از GitHub Models استفاده می‌کنند 

### مرحله 1: دریافت توکن دسترسی شخصی GitHub (PAT)

این دوره از GitHub Models Marketplace بهره می‌برد و دسترسی رایگان به مدل‌های زبان بزرگ (LLMs) را فراهم می‌کند که از آن‌ها برای ساخت AI Agents استفاده خواهید کرد.

To use the GitHub Models, you will need to create a [توکن دسترسی شخصی GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

This can be done by going to your <a href="https://github.com/settings/personal-access-tokens" target="_blank">تنظیمات توکن‌های دسترسی شخصی</a> in your GitHub Account.

Please follow the [اصل کمترین امتیاز](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) when creating your token. This means you should only give the token the permissions it needs to run the code samples in this course.

1. Select the `Fine-grained tokens` option on the left side of your screen by traversing to the **تنظیمات توسعه‌دهنده**

   ![تنظیمات توسعه‌دهنده](../../../translated_images/fa/profile_developer_settings.410a859fe749c755.webp)

   سپس `Generate new token` را انتخاب کنید.

   ![ایجاد توکن](../../../translated_images/fa/fga_new_token.1c1a234afe202ab3.webp)

2. Enter a descriptive name for your token that reflects its purpose, making it easy to identify later.

    🔐 پیشنهاد مدت زمان توکن

    مدت زمان پیشنهادی: 30 روز
    برای امنیت بیشتر، می‌توانید مدت‌زمان کوتاه‌تری مانند 7 روز را انتخاب کنید 🛡️
    این یک روش عالی برای تعیین هدف شخصی و تکمیل دوره در حالی است که انگیزهٔ یادگیری شما بالا است 🚀.

    ![نام توکن و انقضاء](../../../translated_images/fa/token-name-expiry-date.a095fb0de6386864.webp)

3. Limit the token's scope to your fork of this repository.

    ![محدود کردن دامنه به مخزن فورک‌شده](../../../translated_images/fa/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restrict the token's permissions: Under **Permissions**, click **Account** tab, and click the "+ Add permissions" button. A dropdown will appear. Please search for **Models** and check the box for it.

    ![افزودن دسترسی Models](../../../translated_images/fa/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verify the permissions required before generating the token. ![بررسی دسترسی‌ها](../../../translated_images/fa/verify_permissions.06bd9e43987a8b21.webp)

6. Before generating the token, ensure you are ready to store the token in a secure place like a password manager vault, as it will not be shown again after you create it. ![ذخیرهٔ امن توکن](../../../translated_images/fa/store_token_securely.08ee2274c6ad6caf.webp)

Copy your new token that you have just created. You will now add this to your `.env` file included in this course.

### مرحله 2: ایجاد فایل `.env` شما

To create your `.env` file run the following command in your terminal.

```bash
# زد اس اچ/بش
cp .env.example .env
```

```powershell
# پاورشل
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `GITHUB_TOKEN` field.

![فیلد توکن GitHub](../../../translated_images/fa/github_token_field.20491ed3224b5f4a.webp)

You should now be able to run the code samples of this course.

## تنظیم برای نمونه‌هایی که از Microsoft Foundry و Azure AI Agent Service استفاده می‌کنند

### مرحله 1: بازیابی Endpoint پروژهٔ Azure شما


Follow the steps to creating a hub and project in Azure AI Foundry found here: [مرور منابع Hub](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you have created your project, you will need to retrieve the connection string for your project.

This can be done by going to the **Overview** page of your project in the Microsoft Foundry portal.

![رشتهٔ اتصال پروژه](../../../translated_images/fa/project-endpoint.8cf04c9975bbfbf1.webp)

### مرحله 2: ایجاد فایل `.env` شما

To create your `.env` file run the following command in your terminal.

```bash
# زی‌اِس‌اچ/بش
cp .env.example .env
```

```powershell
# پاورشل
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `PROJECT_ENDPOINT` field.

### مرحله 3: ورود به Azure

As a security best practice, we'll use [احراز هویت بدون کلید](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) to authenticate to Azure OpenAI with Microsoft Entra ID. 

Next, open a terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you've logged in, select your subscription in the terminal.

## متغیرهای محیطی اضافی - Azure Search و Azure OpenAI 

For the Agentic RAG Lesson - Lesson 5 - there are samples that use Azure Search and Azure OpenAI.

If you want to run these samples, you will need to add the following environment variables to your `.env` file:

### Overview Page (Project)

- `AZURE_SUBSCRIPTION_ID` - در **جزئیات پروژه** در صفحهٔ **Overview** پروژه‌تان بررسی کنید.

- `AZURE_AI_PROJECT_NAME` - در بالای صفحهٔ **Overview** پروژه‌تان نگاه کنید.

- `AZURE_OPENAI_SERVICE` - این مورد را در تب **Included capabilities** برای **Azure OpenAI Service** در صفحهٔ **Overview** بیابید.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - به **Project properties** در صفحهٔ **Overview** از **Management Center** بروید.

- `GLOBAL_LLM_SERVICE` - زیر **Connected resources**، نام اتصال **Azure AI Services** را پیدا کنید. اگر لیست نشده بود، در **Azure portal** در زیر resource group خود به‌دنبال نام منبع AI Services بگردید.

### Models + Endpoints Page

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - مدل embedding خود را انتخاب کنید (مثلاً `text-embedding-ada-002`) و **Deployment name** را از جزئیات مدل یادداشت کنید.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - مدل چت خود را انتخاب کنید (مثلاً `gpt-4o-mini`) و **Deployment name** را از جزئیات مدل یادداشت کنید.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - به دنبال **Azure AI services** بگردید، روی آن کلیک کنید، سپس به **Resource Management**، **Keys and Endpoint** بروید، به پایین اسکرول کنید تا "Azure OpenAI endpoints" را ببینید، و آن موردی را که می‌گوید "Language APIs" کپی کنید.

- `AZURE_OPENAI_API_KEY` - از همان صفحه، KEY 1 یا KEY 2 را کپی کنید.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - منبع **Azure AI Search** خود را پیدا کنید، روی آن کلیک کنید و **Overview** را ببینید.

- `AZURE_SEARCH_API_KEY` - سپس به **Settings** و سپس **Keys** بروید تا کلید ادمین اولیه یا ثانویه را کپی کنید.

### External Webpage

- `AZURE_OPENAI_API_VERSION` - صفحهٔ [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) را زیر بخش **Latest GA API release** بازدید کنید.

### راه‌اندازی احراز هویت بدون کلید

Rather than hardcode your credentials, we'll use a keyless connection with Azure OpenAI. To do so, we'll import `DefaultAzureCredential` and later call the `DefaultAzureCredential` function to get the credential.

```python
# پایتون
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## گیر کرده‌اید؟
اگر در اجرای این تنظیمات با مشکلی مواجه شدید، به <a href="https://discord.gg/kzRShWzttr" target="_blank">سرور Discord جامعه‌ی Azure AI</a> ما بپیوندید یا <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">یک issue ایجاد کنید</a>.

## درس بعدی

شما اکنون آماده‌اید تا کد این دوره را اجرا کنید. از یادگیری بیشتر دربارهٔ دنیای عامل‌های هوش مصنوعی لذت ببرید! 

[معرفی عامل‌های هوش مصنوعی و موارد استفاده‌ی آن‌ها](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
سلب مسئولیت:
این سند با استفاده از سرویس ترجمهٔ هوش مصنوعی Co-op Translator (https://github.com/Azure/co-op-translator) ترجمه شده است. هرچند ما در تلاش برای دقت هستیم، لطفاً توجه داشته باشید که ترجمه‌های خودکار ممکن است شامل اشتباهات یا نادرستی‌هایی باشند. نسخهٔ اصلی سند به زبان اصلی باید به‌عنوان منبع معتبر در نظر گرفته شود. برای اطلاعات مهم، ترجمهٔ حرفه‌ای و انسانی توصیه می‌شود. ما در قبال هرگونه سو‌تفاهم یا تفسیر نادرست ناشی از استفاده از این ترجمه مسئولیتی نداریم.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->