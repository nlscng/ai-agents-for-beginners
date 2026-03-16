# کورس سیٹ اپ

## تعارف

یہ سبق اس کورس کے کوڈ نمونوں کو چلانے کے طریقے کو کور کرے گا۔

## دوسرے سیکھنے والوں میں شامل ہوں اور مدد حاصل کریں

اپنا ریپو کلون کرنے سے پہلے، سیٹ اپ میں مدد، کورس کے بارے میں کوئی سوالات، یا دیگر سیکھنے والوں سے جڑنے کے لیے [AI Agents For Beginners Discord چینل](https://aka.ms/ai-agents/discord) میں شامل ہوں۔

## اس ریپو کو کلون کریں یا فورک کریں

شروع کرنے کے لیے، براہ کرم GitHub ریپوزیٹری کو کلون یا فورک کریں۔ اس سے آپ کے پاس کورس مواد کا اپنا ورژن ہوگا تاکہ آپ کوڈ کو چلا سکیں، ٹیسٹ کر سکیں، اور ایڈجسٹ کر سکیں!

یہ کام <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">ریپو فورک کرنے</a> کے لنک پر کلک کر کے کیا جا سکتا ہے۔

اب آپ کے پاس اس کورس کا اپنا فورک کیا ہوا ورژن درج ذیل لنک پر ہونا چاہیے:

![Forked Repo](../../../translated_images/ur/forked-repo.33f27ca1901baa6a.webp)

### شیلو کلون (ورکشاپ / Codespaces کے لیے تجویز کردہ)

  >پورا ریپوزیٹری مکمل ہسٹری اور تمام فائلیں ڈاؤن لوڈ کرنے پر بڑا (~3 GB) ہو سکتا ہے۔ اگر آپ صرف ورکشاپ میں شریک ہیں یا صرف چند سبق فولڈرز کی ضرورت ہے، تو ایک شیلو کلون (یا اسپارس کلون) زیادہ تر ڈاؤن لوڈ سے بچاتا ہے کیونکہ یہ ہسٹری کو مختصر کرتا ہے اور/یا بلبز کو چھوڑ دیتا ہے۔

#### تیز شیلو کلون — کم از کم ہسٹری، تمام فائلیں

نیچے دیے گئے کمانڈز میں `<your-username>` کو اپنے فورک یو آر ایل (یا اگر چاہیں تو اپ اسٹریم یو آر ایل) سے تبدیل کریں۔

صرف تازہ ترین کمیٹ ہسٹری کلون کرنے کے لیے (چھوٹا ڈاؤن لوڈ):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

کسی مخصوص برانچ کو کلون کرنے کے لیے:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### جزوی (اسپارس) کلون — کم از کم بلبز + صرف منتخب فولڈرز

یہ جزوی کلون اور اسپارس چیک آؤٹ استعمال کرتا ہے (Git 2.25+ درکار اور تجویز کردہ جدید Git کے ساتھ جزوی کلون کی حمایت):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

ریپو فولڈر میں جائیں:

```bash|powershell
cd ai-agents-for-beginners
```

پھر بتائیں کہ آپ کون سے فولڈرز چاہتے ہیں (نیچے مثال میں دو فولڈرز دکھائے گئے ہیں):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

کلون کرنے اور فائلیں چیک کرنے کے بعد، اگر آپ کو صرف فائلیں چاہیے اور جگہ خالی کرنی ہے (کوئی git ہسٹری نہیں)، تو براہ کرم ریپوزیٹری میٹاڈیٹا کو ڈیلیٹ کریں (💀 ناقابل واپسی — آپ تمام Git فنکشنلٹی کھو دیں گے: کوئی کمیٹس، پل، پوش، یا ہسٹری کی رسائی نہیں)۔

```bash
# زی ایس ایچ/بیash
rm -rf .git
```

```powershell
# پاور شیل
Remove-Item -Recurse -Force .git
```

#### GitHub Codespaces کا استعمال (لوکل بڑے ڈاؤن لوڈ سے بچنے کے لیے تجویز کردہ)

- اس ریپو کے لیے [GitHub UI](https://github.com/codespaces) کے ذریعے نیا Codespace بنائیں۔  

- نئے بنائے گئے Codespace کے ٹرمینل میں اوپر دی گئی شیلو/اسپارس کلون کمانڈز میں سے ایک چلائیں تاکہ آپ کو صرف مطلوبہ سبق فولڈرز Codespace ورک اسپیس میں مل جائیں۔
- اختیاری: Codespaces کے اندر کلون کرنے کے بعد، .git کو ہٹا کر اضافی جگہ واپس حاصل کریں (مندرجہ بالا ہٹانے کے کمانڈز دیکھیں)۔
- نوٹ: اگر آپ ریپو کو براہ راست Codespaces میں (اضافی کلون کے بغیر) کھولنا پسند کرتے ہیں، تو جان لیں کہ Codespaces devcontainer ماحول بنائے گا اور ہو سکتا ہے آپ کی ضرورت سے زیادہ وسائل فراہم کرے۔ تازہ Codespace میں شیلو کلون کرنے سے آپ کو ڈسک کے استعمال پر زیادہ کنٹرول ملتا ہے۔

#### تجاویز

- اگر آپ ترمیم/کمیٹ کرنا چاہتے ہیں تو کلون URL ہمیشہ اپنے فورک سے تبدیل کریں۔
- اگر بعد میں آپ کو زیادہ ہسٹری یا فائلز کی ضرورت ہو، تو آپ انہیں فیچ کر سکتے ہیں یا اسپارس چیک آؤٹ کو مزید فولڈرز شامل کرنے کے لیے ایڈجسٹ کر سکتے ہیں۔

## کوڈ چلانا

یہ کورس آپ کو Jupyter Notebooks کی ایک سیریز فراہم کرتا ہے جنہیں آپ چلائیں گے تاکہ AI Agents بنانے کا عملی تجربہ حاصل ہو۔

کوڈ نمونے درج ذیل استعمال کرتے ہیں:

**GitHub اکاؤنٹ ضروری ہے - مفت**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace۔ جسے (semantic-kernel.ipynb) کے طور پر لیبل کیا گیا ہے۔
2) AutoGen Framework + GitHub Models Marketplace۔ جسے (autogen.ipynb) کے طور پر لیبل کیا گیا ہے۔

**Azure سبسکشن ضروری ہے**:
3) Azure AI Foundry + Azure AI Agent Service۔ جسے (azureaiagent.ipynb) کے طور پر لیبل کیا گیا ہے۔

ہم آپ کی ترغیب دیتے ہیں کہ آپ ان تینوں طرح کی مثالوں کو آزمائیں تاکہ دیکھ سکیں کون سا آپ کے لیے بہترین کام کرتا ہے۔

جو بھی آپشن منتخب کریں، وہ نیچے آپ کو مطلوبہ سیٹ اپ مراحل کی تعین کرے گا:

## تقاضے

- Python 3.12+
  - **نوٹ**: اگر آپ کے پاس Python3.12 انسٹال نہیں ہے تو اسے یقینی بنائیں کہ آپ اسے انسٹال کریں۔ پھر اپنے venv کو python3.12 کے ساتھ بنائیں تاکہ requirements.txt فائل سے درست ورژنز انسٹال ہوں۔
  
    >مثال

    Python venv ڈائریکٹری بنائیں:

    ```bash|powershell
    python -m venv venv
    ```

    پھر venv ماحول کو فعال کریں:

    ```bash
    # زی ایس ایچ/باش
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: .NET استعمال کرنے والے نمونہ کوڈز کے لیے، یقینی بنائیں کہ آپ نے [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) یا اس سے زیادہ ورژن انسٹال کیا ہے۔ پھر اپنا انسٹال شدہ .NET SDK ورژن چیک کریں:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub اکاؤنٹ - GitHub Models Marketplace تک رسائی کے لیے
- Azure سبسکشن - Microsoft Foundry تک رسائی کے لیے
- Microsoft Foundry اکاؤنٹ - Azure AI Agent Service تک رسائی کے لیے

ہم نے اس ریپوزیٹری کی جڑ پر `requirements.txt` فائل شامل کی ہے جس میں تمام مطلوبہ Python پیکجز شامل ہیں تاکہ کوڈ نمونے چل سکیں۔

آپ اسے ریپوزیٹری کی جڑ میں اپنے ٹرمینل پر درج ذیل کمانڈ چلانے سے انسٹال کر سکتے ہیں:

```bash|powershell
pip install -r requirements.txt
```

ہم مشورہ دیتے ہیں کہ کسی بھی تصادم اور مسائل سے بچنے کے لیے Python ورچوئل ماحول بنائیں۔

## VSCode سیٹ اپ کریں

یقینی بنائیں کہ آپ VSCode میں درست Python ورژن استعمال کر رہے ہیں۔

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## GitHub Models استعمال کرنے والے نمونوں کے لیے سیٹ اپ

### مرحلہ 1: اپنا GitHub پرسنل ایکسیس ٹوکن (PAT) حاصل کریں

یہ کورس GitHub Models Marketplace استعمال کرتا ہے، جو آپ کو بڑے زبان ماڈلز (LLMs) تک مفت رسائی دیتا ہے جنہیں آپ AI Agents بنانے کے لیے استعمال کریں گے۔

GitHub Models استعمال کرنے کے لیے، آپ کو ایک [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) بنانا ہوگا۔

یہ آپ کے GitHub اکاؤنٹ میں <a href="https://github.com/settings/personal-access-tokens" target="_blank">Personal Access Tokens کی ترتیبات</a> پر جا کر کیا جاتا ہے۔

براہ کرم ٹوکن بناتے وقت [Principle of Least Privilege](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) کی پیروی کریں۔ اس کا مطلب ہے کہ آپ کو ٹوکن کو صرف وہی اجازتیں دینی چاہئیں جو اس کورس کے کوڈ نمونوں کو چلانے کے لیے ضروری ہوں۔

1. اپنی سکرین کے بائیں طرف `Fine-grained tokens` آپشن منتخب کریں، **Developer settings** پر جائیں۔

   ![Developer settings](../../../translated_images/ur/profile_developer_settings.410a859fe749c755.webp)

   پھر `Generate new token` منتخب کریں۔

   ![Generate Token](../../../translated_images/ur/fga_new_token.1c1a234afe202ab3.webp)

2. اپنے ٹوکن کے لیے ایک وضاحتی نام درج کریں جو اس کے مقصد کی عکاسی کرے تاکہ بعد میں اسے پہچاننا آسان ہو۔

    🔐 ٹوکن دورانیہ کی سفارش

    تجویز کردہ دورانیہ: 30 دن
    زیادہ محفوظ اختتام کے لیے، آپ کم مدت (مثلاً 7 دن) کا انتخاب کر سکتے ہیں 🛡️
    یہ ایک اچھا طریقہ ہے ذاتی ہدف مقرر کرنے اور کورس مکمل کرنے کے لیے جب آپ کا سیکھنے کا جذبہ بلند ہو 🚀۔

    ![Token Name and Expiration](../../../translated_images/ur/token-name-expiry-date.a095fb0de6386864.webp)

3. ٹوکن کا دائرہ کار صرف اس ریپو کے اپنے فورک تک محدود کریں۔

    ![Limit scope to fork repository](../../../translated_images/ur/token_repository_limit.924ade5e11d9d8bb.webp)

4. ٹوکن کی اجازتوں کو محدود کریں: **Permissions** میں، **Account** ٹیب پر کلک کریں، پھر "+ Add permissions" بٹن پر کلک کریں۔ ڈراپ ڈاؤن ظاہر ہوگا۔ براہ کرم **Models** تلاش کریں اور اس کے بندے کو چیک کریں۔

    ![Add Models Permission](../../../translated_images/ur/add_models_permissions.c0c44ed8b40fc143.webp)

5. ٹوکن بنانے سے پہلے مطلوبہ اجازتوں کی تصدیق کریں۔ ![Verify Permissions](../../../translated_images/ur/verify_permissions.06bd9e43987a8b21.webp)

6. ٹوکن بنانے سے پہلے، یقینی بنائیں کہ آپ اسے محفوظ جگہ مثلاً پاسورڈ مینیجر وولٹ میں ذخیرہ کرنے کے لیے تیار ہیں، کیونکہ یہ دوبارہ نہیں دکھایا جائے گا! ![Store Token Securely](../../../translated_images/ur/store_token_securely.08ee2274c6ad6caf.webp)

اب اپنا نیا بنایا ہوا ٹوکن کاپی کریں۔ آپ اسے اس کورس میں شامل `.env` فائل میں شامل کریں گے۔

### مرحلہ 2: اپنی `.env` فائل بنائیں

اپنے ٹرمینل میں درج ذیل کمانڈ چلائیں تاکہ اپنی `.env` فائل بنائیں۔

```bash
# زیڈ ایس ایچ / بی ایچ
cp .env.example .env
```

```powershell
# پاور شیل
Copy-Item .env.example .env
```

یہ مثال فائل کو کاپی کرے گا اور آپ کے فولڈر میں `.env` فائل بنائے گا جہاں آپ ماحول کی متغیرات کے لئے قدریں بھر سکیں گے۔

ٹوکن کاپی کرنے کے بعد، `.env` فائل کو اپنے پسندیدہ ٹیکسٹ ایڈیٹر میں کھولیں اور اپنا ٹوکن `GITHUB_TOKEN` فیلڈ میں چسپاں کریں۔

![GitHub Token Field](../../../translated_images/ur/github_token_field.20491ed3224b5f4a.webp)

اب آپ اس کورس کے کوڈ نمونے چلا سکیں گے۔

## Microsoft Foundry اور Azure AI Agent Service استعمال کرنے والے نمونوں کے لیے سیٹ اپ

### مرحلہ 1: اپنا Azure پروجیکٹ اینڈ پوائنٹ حاصل کریں

Azure AI Foundry میں ہب اور پروجیکٹ بنانے کے مراحل یہاں دیکھیں: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

ایک بار جب آپ اپنا پروجیکٹ بنا لیں، تو آپ کو اپنے پروجیکٹ کے کنکشن سٹرنگ کی ضرورت ہوگی۔

یہ کام Microsoft Foundry پورٹل میں اپنے پروجیکٹ کے **Overview** صفحے پر جا کر کیا جا سکتا ہے۔

![Project Connection String](../../../translated_images/ur/project-endpoint.8cf04c9975bbfbf1.webp)

### مرحلہ 2: اپنی `.env` فائل بنائیں

اپنے ٹرمینل میں درج ذیل کمانڈ چلائیں تاکہ اپنی `.env` فائل بنائیں۔

```bash
# زی ش/بش
cp .env.example .env
```

```powershell
# پاور شیل
Copy-Item .env.example .env
```

یہ مثال فائل کو کاپی کرے گا اور آپ کے فولڈر میں `.env` فائل بنائے گا جہاں آپ ماحول کی متغیرات کے لئے قدریں بھریں گے۔

ٹوکن کاپی کرنے کے بعد، اپنی پسندیدہ ٹیکسٹ ایڈیٹر میں `.env` فائل کھولیں اور اپنا ٹوکن `PROJECT_ENDPOINT` فیلڈ میں چسپاں کریں۔

### مرحلہ 3: Azure میں سائن ان کریں

سیکیورٹی کی بہترین مشق کے طور پر، ہم [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) استعمال کریں گے تاکہ Microsoft Entra ID کے ساتھ Azure OpenAI کی توثیق ہو سکے۔

اگلے مرحلے میں ٹرمینل کھولیں اور `az login --use-device-code` چلائیں تاکہ اپنے Azure اکاؤنٹ میں سائن ان ہو سکیں۔

سائن ان ہونے کے بعد، ٹرمینل میں اپنی سبسکپشن منتخب کریں۔

## اضافی ماحول کی متغیرات - Azure Search اور Azure OpenAI

Agentic RAG سبق - سبق 5 - میں ایسے نمونے ہیں جو Azure Search اور Azure OpenAI استعمال کرتے ہیں۔

اگر آپ یہ نمونے چلانا چاہتے ہیں، تو آپ کو اپنی `.env` فائل میں درج ذیل ماحول کی متغیرات شامل کرنی ہوں گی:

### اوورویو پیج (پروجیکٹ)

- `AZURE_SUBSCRIPTION_ID` - اپنے پروجیکٹ کے **Overview** صفحے پر **Project details** چیک کریں۔

- `AZURE_AI_PROJECT_NAME` - اپنے پروجیکٹ کے **Overview** صفحے کے اوپر دیکھیں۔

- `AZURE_OPENAI_SERVICE` - **Overview** صفحے کے **Included capabilities** ٹیب میں **Azure OpenAI Service** تلاش کریں۔

### مینجمنٹ سینٹر

- `AZURE_OPENAI_RESOURCE_GROUP` - مینجمنٹ سینٹر کے **Overview** صفحے میں **Project properties** دیکھیں۔

- `GLOBAL_LLM_SERVICE` - **Connected resources** کے تحت **Azure AI Services** کنکشن کا نام ڈھونڈیں۔ اگر نہیں ملے، تو اپنے ریسورس گروپ میں Azure پورٹل میں AI Services ریسورس کا نام چیک کریں۔

### ماڈلز + اینڈ پوائنٹس صفحہ

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - اپنے ایمبیڈنگ ماڈل منتخب کریں (مثلاً `text-embedding-ada-002`) اور ماڈل کی تفصیلات سے **Deployment name** نوٹ کریں۔

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - اپنے چیٹ ماڈل منتخب کریں (مثلاً `gpt-4o-mini`) اور ماڈل کی تفصیلات سے **Deployment name** نوٹ کریں۔

### Azure پورٹل

- `AZURE_OPENAI_ENDPOINT` - **Azure AI services** تلاش کریں، اس پر کلک کریں، پھر **Resource Management**, **Keys and Endpoint** میں جائیں، "Azure OpenAI endpoints" تک نیچے سکرول کریں، اور وہ کاپی کریں جو "Language APIs" کہلاتا ہے۔

- `AZURE_OPENAI_API_KEY` - اسی سکرین سے، کی 1 یا کی 2 کاپی کریں۔

- `AZURE_SEARCH_SERVICE_ENDPOINT` - اپنا **Azure AI Search** ریسورس تلاش کریں، اس پر کلک کریں، اور **Overview** دیکھیں۔

- `AZURE_SEARCH_API_KEY` - پھر **Settings** میں جائیں پھر **Keys** سے پرائمری یا سیکنڈری ایڈمن کی کاپی کریں۔

### بیرونی ویب صفحہ

- `AZURE_OPENAI_API_VERSION` - [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) صفحہ پر **Latest GA API release** کے تحت دیکھیں۔

### keyless authentication سیٹ اپ کریں

اپنے اسناد کو ہارڈ کوڈ کرنے کے بجائے، ہم Azure OpenAI کے ساتھ keyless connection استعمال کریں گے۔ ایسا کرنے کے لیے، ہم `DefaultAzureCredential` کو درآمد کریں گے اور بعد میں `DefaultAzureCredential` فنکشن کو کال کرکے اسناد حاصل کریں گے۔

```python
# پائتھن
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## کہیں پھنس گئے ہیں؟
اگر آپ کو اس سیٹ اپ کو چلانے میں کوئی مسئلہ ہو تو ہمارے <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> میں شامل ہوں یا <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">مسئلہ درج کریں</a>۔

## اگلا سبق

آپ اب اس کورس کے لیے کوڈ چلانے کے لیے تیار ہیں۔ AI ایجنٹس کی دنیا کے بارے میں مزید جاننے کے لیے خوش رہیں!

[AI ایجنٹس اور ایجنٹس کے استعمال کے کیسز کا تعارف](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**تنبیہ:**  
اس دستاویز کا ترجمہ AI ترجمہ سروس [Co-op Translator](https://github.com/Azure/co-op-translator) کے ذریعے کیا گیا ہے۔ اگرچہ ہم درستگی کے لیے کوشاں ہیں، براہ کرم یہ بات ذہن میں رکھیں کہ خودکار ترجمے میں غلطیاں یا اغلاط ہو سکتی ہیں۔ اصل دستاویز اپنی مادری زبان میں ہی معتبر ماخذ سمجھی جاتی ہے۔ اہم معلومات کے لیے پیشہ ور انسانی ترجمہ تجویز کیا جاتا ہے۔ اس ترجمے کے استعمال سے ہونے والی کسی بھی غلط فہمی یا غلط تشریح کے لیے ہم ذمہ دار نہیں ہیں۔
<!-- CO-OP TRANSLATOR DISCLAIMER END -->