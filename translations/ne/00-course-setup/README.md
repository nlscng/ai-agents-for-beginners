# कोर्स सेटअप

## परिचय

यो पाठले यस कोर्सका कोड नमूनाहरू कसरी चलाउने भनेर समेट्नेछ।

## अन्य सिक्नेहरूसँग जोडिनुहोस् र सहयोग प्राप्त गर्नुहोस्

रिपो क्लोन गर्नुभन्दा पहिले, सेटअपमा सहयोग, कोर्स सम्बन्धी कुनै प्रश्नहरू, वा अन्य सिक्नेहरूसँग जडान हुनको लागि [AI एजेन्टहरू प्रारम्भकर्ताका लागि Discord च्यानल](https://aka.ms/ai-agents/discord) मा सहभागी हुनुहोस्।

## यो रिपो क्लोन वा फोर्क गर्नुहोस्

सुरु गर्नको लागि, कृपया GitHub रिपोजिटरी क्लोन वा फोर्क गर्नुहोस्। यसले कोर्स सामग्रीको आफ्नो संस्करण बनाउँछ जसले गर्दा तपाईंले कोड चलाउन, परीक्षण गर्न, र परिमार्जन गर्न सक्नुहुन्छ!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">रिपो फोर्क गर्नुहोस्</a>

You should now have your own forked version of this course in the following link:

![फोर्क गरिएको रिपो](../../../translated_images/ne/forked-repo.33f27ca1901baa6a.webp)

### हल्का क्लोन (व्यावहारिक कार्यशाला / Codespaces का लागि सिफारिस गरिएको)

  > पूर्ण रिपोजिटरी पूरा इतिहास र सबै फाइलहरू डाउनलोड गर्दा ठूलो (~3 GB) हुनसक्छ। यदि तपाईं केवल कार्यशाला मा सहभागी हुनुहुन्छ वा केवल केही पाठ फोल्डरहरू चाहिएको छ भने, एक हल्का क्लोन (वा स्पार्स क्लोन) ले इतिहास छोट्याएर र/वा ब्लबहरू छोडेर त्यहाँको अधिकांश डाउनलोडबाट बचाउँछ।

#### द्रुत हल्का क्लोन — न्यूनतम इतिहास, सबै फाइलहरू

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

To clone only the latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### आंशिक (स्पार्स) क्लोन — न्यूनतम ब्लबहरू + मात्रै चयन गरिएका फोल्डरहरू

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
# पावरशेल
Remove-Item -Recurse -Force .git
```

#### GitHub Codespaces प्रयोग गर्दै (स्थानीय ठूलो डाउनलोडबाट बच्न सिफारिस गरिएको)

- यस रिपोको लागि [GitHub UI](https://github.com/codespaces) मार्फत नयाँ Codespace सिर्जना गर्नुहोस्।  

- नयाँ सिर्जना गरिएको codespace को टर्मिनलमा, केवल आवश्यक पाठ फोल्डरहरू Codespace कार्यक्षेत्रमा ल्याउन माथिका हल्का/स्पार्स क्लोन आदेशहरूमध्ये कुनै एक चलाउनुहोस्।
- वैकल्पिक: Codespaces भित्र क्लोन गरेपछि अतिरिक्त स्थान फिर्ता पाउन `.git` हटाउनुहोस् (माथि मेट्ने आदेशहरु हेर्नुहोस्)।
- नोट: यदि तपाईं अतिरिक्त क्लोन बिना सिधै Codespaces मा रिपो खोल्न मन पराउनुहुन्छ भने, ध्यान दिनुहोस् Codespaces ले devcontainer वातावरण निर्माण गर्नेछ र सम्भवतः तपाईंलाई चाहिने भन्दा बढी स्रोत provision गर्न सक्छ। नयाँ Codespace भित्र एक हल्का प्रतिलिपि क्लोन गर्दा डिस्क प्रयोगमा तपाईंलाई बढी नियन्त्रण मिल्छ।

#### सुझावहरू

- यदि तपाईं सम्पादन/कमिट गर्न चाहानुहुन्छ भने क्लोन URL सधैं आफ्नो फोर्कसँग प्रतिस्थापन गर्नुहोस्।
- यदि पछि तपाईंलाई थप इतिहास वा फाइलहरू आवश्यक परेमा, तपाईं तिनीहरू फेच गर्न सक्नुहुन्छ वा थप फोल्डरहरू समावेश गर्न sparse-checkout समायोजन गर्न सक्नुहुन्छ।

## कोड चलाउने तरिका

यस कोर्सले Jupyter Notebook हरूको श्रृंखला प्रदान गर्दछ जसलाई चलाएर तपाईं AI एजेन्टहरू निर्माण गर्ने व्यावहारिक अनुभव प्राप्त गर्न सक्नुहुन्छ।

The code samples use either:

**Requires GitHub Account - Free**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. (फाइल: semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. (फाइल: autogen.ipynb)

**Azure सदस्यता आवश्यक**:
3) Azure AI Foundry + Azure AI Agent Service. (फाइल: azureaiagent.ipynb)

We encourage you to try out all three types of examples to see which one works best for you.

Whichever option you choose, it will determine which setup steps you need to follow below:

## आवश्यकताहरू

- Python 3.12+
  - **NOTE**: यदि तपाईंले Python3.12 स्थापना गर्नुभएको छैन भने, कृपया यसलाई स्थापना गर्नुहोस्। त्यसपछि requirements.txt फाइलबाट सहि संस्करणहरू स्थापना हुन सुनिश्चित गर्न python3.12 प्रयोग गरी आफ्नो venv सिर्जना गर्नुहोस्।
  
    >उदाहरण

    Create Python venv directory:

    ```bash|powershell
    python -m venv venv
    ```

    त्यसपछि venv वातावरण सक्रिय गर्नुहोस्:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: .NET प्रयोग गर्ने नमूना कोडहरूको लागि, कृपया [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) वा पछि संस्करण स्थापना गर्नुहोस्। त्यसपछि, आफ्नो इन्स्टल गरिएको .NET SDK संस्करण जाँच गर्नुहोस्:

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

## VSCode सेटअप गर्नुहोस्

Make sure that you are using the right version of Python in VSCode.

![छवि](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## GitHub Models प्रयोग गर्ने नमूनाहरूको सेटअप

### चरण 1: आफ्नो GitHub Personal Access Token (PAT) प्राप्त गर्नुहोस्

यो कोर्सले GitHub Models Marketplace प्रयोग गर्दछ, जसले तपाईंले AI एजेन्टहरू निर्माण गर्न प्रयोग गर्ने ठूलो भाषा मोडेलहरू (LLMs) मा निःशुल्क पहुँच प्रदान गर्छ।

GitHub Models प्रयोग गर्न, तपाईंले [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) सिर्जना गर्न आवश्यक हुनेछ।

यसलाई तपाईंको GitHub खातामा रहेको <a href="https://github.com/settings/personal-access-tokens" target="_blank">Personal Access Tokens सेटिङहरू</a> मा गएर गर्न सकिन्छ।

कृपया टोकन बनाउँदा [न्यूनतम अधिकारको सिद्धान्त](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) पालना गर्नुहोस्। यसको अर्थ तपाइँले टोकनलाई केवल यस कोर्सका कोड नमूनाहरू चलाउन आवश्यक अधिकार मात्र दिनु पर्ने हुन्छ।

1. <strong>Developer settings</strong> मा गएर आफ्नो स्क्रिनको बाँया पट्टीमा रहेको `Fine-grained tokens` विकल्प चयन गर्नुहोस्।

   ![डेभलपर सेटिङ](../../../translated_images/ne/profile_developer_settings.410a859fe749c755.webp)

   त्यसपछि `Generate new token` चयन गर्नुहोस्।

   ![टोकन उत्पन्न गर्नुहोस्](../../../translated_images/ne/fga_new_token.1c1a234afe202ab3.webp)

2. Enter a descriptive name for your token that reflects its purpose, making it easy to identify later.

    🔐 Token Duration Recommendation

    Recommended duration: 30 days
    For a more secure posture, you can opt for a shorter period—such as 7 days 🛡️
    It’s a great way to set a personal target and complete the course while your learning momentum is high 🚀.

    ![Token Name and Expiration](../../../translated_images/ne/token-name-expiry-date.a095fb0de6386864.webp)

3. Limit the token's scope to your fork of this repository.

    ![Limit scope to fork repository](../../../translated_images/ne/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restrict the token's permissions: Under **Permissions**, click **Account** tab, and click the "+ Add permissions" button. A dropdown will appear. Please search for **Models** and check the box for it.

    ![Add Models Permission](../../../translated_images/ne/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verify the permissions required before generating the token. ![अनुमतिहरू जाँच गर्नुहोस्](../../../translated_images/ne/verify_permissions.06bd9e43987a8b21.webp)

6. Before generating the token, ensure you are ready to store the token in a secure place like a password manager vault, as it will not be shown again after you create it. ![टोकन सुरक्षित रूपमा भण्डारण गर्नुहोस्](../../../translated_images/ne/store_token_securely.08ee2274c6ad6caf.webp)

Copy your new token that you have just created. You will now add this to your `.env` file included in this course.

### चरण 2: आफ्नो `.env` फाइल सिर्जना गर्नुहोस्

To create your `.env` file run the following command in your terminal.

```bash
# zsh वा bash
cp .env.example .env
```

```powershell
# पावरशेल
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `GITHUB_TOKEN` field.

![GitHub टोकन फिल्ड](../../../translated_images/ne/github_token_field.20491ed3224b5f4a.webp)

You should now be able to run the code samples of this course.

## Microsoft Foundry र Azure AI Agent Service प्रयोग गर्ने नमूनाहरूको सेटअप

### चरण 1: आफ्नो Azure प्रोजेक्ट एंडपोइन्ट प्राप्त गर्नुहोस्


Azure AI Foundry मा हब र प्रोजेक्ट सिर्जना गर्ने चरणहरू यहाँ फेला पार्नुहोस्: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you have created your project, you will need to retrieve the connection string for your project.

This can be done by going to the **Overview** page of your project in the Microsoft Foundry portal.

![प्रोजेक्ट कनेक्सन स्ट्रिङ](../../../translated_images/ne/project-endpoint.8cf04c9975bbfbf1.webp)

### चरण 2: आफ्नो `.env` फाइल सिर्जना गर्नुहोस्

To create your `.env` file run the following command in your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# पावरशेल
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `PROJECT_ENDPOINT` field.

### चरण 3: Azure मा साइन इन गर्नुहोस्

सुरक्षा उत्तम अभ्यासको रूपमा, हामी Microsoft Entra ID मार्फत Azure OpenAI लाई प्रमाणीकृत गर्न [कुञ्जीविहीन प्रमाणीकरण](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) प्रयोग गर्नेछौं। 

Next, open a terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you've logged in, select your subscription in the terminal.

## थप वातावरण चरहरू - Azure Search र Azure OpenAI 

For the Agentic RAG Lesson - Lesson 5 - there are samples that use Azure Search and Azure OpenAI.

If you want to run these samples, you will need to add the following environment variables to your `.env` file:

### Overview Page (Project)

- `AZURE_SUBSCRIPTION_ID` - आफ्नो प्रोजेक्टको **Overview** पृष्ठमा रहेको **Project details** हेर्नुहोस्।

- `AZURE_AI_PROJECT_NAME` - आफ्नो प्रोजेक्टको **Overview** पृष्ठको शीर्षमा हेर्नुहोस्।

- `AZURE_OPENAI_SERVICE` - **Overview** पृष्ठमा रहेको **Included capabilities** ट्याबमा **Azure OpenAI Service** हेर्नुहोस्।

### व्यवस्थापन केन्द्र

- `AZURE_OPENAI_RESOURCE_GROUP` - **Management Center** को **Overview** पृष्ठमा रहेको **Project properties** मा जानुहोस्।

- `GLOBAL_LLM_SERVICE` - **Connected resources** अन्तर्गत, **Azure AI Services** कनेक्सन नाम खोज्नुहोस्। सूचीमा नभएमा, आफ्नो स्रोत समूह अन्तर्गत **Azure portal** मा AI Services स्रोत नाम जाँच गर्नुहोस्।

### Models + Endpoints पृष्ठ

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - आफ्नो embedding मोडेल (जस्तै, `text-embedding-ada-002`) चयन गर्नुहोस् र मोडेल विवरणबाट **Deployment name** नोट गर्नुहोस्।

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - आफ्नो chat मोडेल (जस्तै, `gpt-4o-mini`) चयन गर्नुहोस् र मोडेल विवरणबाट **Deployment name** नोट गर्नुहोस्।

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - **Azure AI services** खोज्नुहोस्, त्यसमा क्लिक गर्नुहोस्, त्यसपछि **Resource Management**, **Keys and Endpoint** मा जानुहोस्, "Azure OpenAI endpoints" सम्म स्क्रोल गर्नुहोस्, र "Language APIs" भनिएको एकलाई प्रतिलिपि गर्नुहोस्।

- `AZURE_OPENAI_API_KEY` - सोही स्क्रिनबाट KEY 1 वा KEY 2 प्रतिलिपि गर्नुहोस्।

- `AZURE_SEARCH_SERVICE_ENDPOINT` - आफ्नो **Azure AI Search** स्रोत खोज्नुहोस्, यसमा क्लिक गर्नुहोस्, र **Overview** हेर्नुहोस्।

- `AZURE_SEARCH_API_KEY` - त्यसपछि **Settings** मा जानुहोस् र **Keys** मा मुख्य वा गौण एडमिन की प्रतिलिपि गर्नुहोस्।

### बाह्य वेबपेज

- `AZURE_OPENAI_API_VERSION` - कृपया [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) पृष्ठको **Latest GA API release** भाग हेर्नुहोस्।

### कुञ्जीविहीन प्रमाणीकरण सेटअप गर्नुहोस्

Rather than hardcode your credentials, we'll use a keyless connection with Azure OpenAI. To do so, we'll import `DefaultAzureCredential` and later call the `DefaultAzureCredential` function to get the credential.

```python
# पाइथन
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## कतै अट्किनुभयो?
यदि तपाईंले यो सेटअप चलाउँदा कुनै समस्या भएमा, हाम्रो <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI समुदाय Discord</a> मा आउनुहोस् वा <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">इश्यू सिर्जना गर्नुहोस्</a>।

## अर्को पाठ

अब तपाईं यो कोर्सको कोड चलाउन तयार हुनुहुन्छ। AI एजेन्टहरूको संसारबारे थप सिक्न शुभकामना!

[AI एजेन्टहरू र एजेन्ट प्रयोगका केसहरूको परिचय](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
अस्वीकरण:
यो दस्तावेज AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) प्रयोग गरेर अनुवाद गरिएको हो। हामी सहीताको लागि प्रयास गर्छौं भने पनि, कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादमा त्रुटि वा अशुद्धता हुन सक्छ। मूल भाषामा रहेको दस्तावेजलाई आधिकारिक स्रोतको रूपमा मानिनु पर्छ। महत्वपुर्ण जानकारीका लागि पेशेवर मानवीय अनुवाद सिफारिस गरिन्छ। यो अनुवादको प्रयोगबाट उत्पन्न कुनै पनि गलतफहमी वा गलत व्याख्याका लागि हामी जिम्मेवार छैनौं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->