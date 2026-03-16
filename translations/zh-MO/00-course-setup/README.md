# 課程設定

## 介紹

本課程會說明如何執行本課程的程式範例。

## 加入其他學習者並獲得協助

在開始複製你的儲存庫之前，請加入 [AI Agents For Beginners Discord channel](https://aka.ms/ai-agents/discord) 以取得任何設定上的協助、對課程的疑問，或與其他學習者交流。

## 複製或分叉此儲存庫

要開始，請複製或分叉 GitHub 儲存庫。這會建立你自己的課程教材版本，讓你可以執行、測試及調整程式！

這可透過點擊 <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">分叉此儲存庫</a> 的連結來完成

你現在應該會在以下連結有你自己分叉的課程版本：

![已分叉的儲存庫](../../../translated_images/zh-MO/forked-repo.33f27ca1901baa6a.webp)

### 淺層複製（建議用於工作坊 / Codespaces）

  >完整的儲存庫在下載完整歷史記錄與所有檔案時可能會很大（約 ~3 GB）。如果你只參加工作坊或只需要少數課程資料夾，淺層複製（或稀疏複製）可透過截斷歷史記錄及／或跳過 blobs 來避免大部分的下載。

#### 快速淺層複製 — 最少歷史，所有檔案

將 `<your-username>` 在下列指令中替換為你的 fork URL（或如果你偏好，上游（upstream）URL）。

若僅想複製最新的提交歷史（小量下載）：

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

若要複製特定分支：

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### 部分（稀疏）複製 — 最少 blobs + 只包含選定資料夾

此方法使用部分複製與 sparse-checkout（需要 Git 2.25+ 並建議使用支援 partial clone 的現代 Git）：

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

進入儲存庫資料夾：

```bash|powershell
cd ai-agents-for-beginners
```

然後指定你想要的資料夾（下例示範兩個資料夾）：

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

在複製並確認檔案後，如果你只需要檔案並想釋放空間（不保留 git 歷史），請刪除儲存庫的 metadata（💀不可逆 — 你將失去所有 Git 功能：無法提交、拉取、推送或存取歷史）。

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### 使用 GitHub Codespaces（建議以避免本機大型下載）

- 透過 [GitHub UI](https://github.com/codespaces) 為此儲存庫建立新的 Codespace。  

- 在新建立的 codespace 的終端機中，執行上面任一淺層／稀疏複製指令，僅將你所需的課程資料夾帶入 Codespace 工作區。
- 選用：在 Codespaces 中完成複製後，可移除 .git 以回收額外空間（參閱上方移除指令）。
- 注意：如果你偏好直接在 Codespaces 中開啟儲存庫（不另外複製），請留意 Codespaces 會構建 devcontainer 環境，並可能仍然配置超出你需求的內容。在新的 Codespace 內複製淺層副本，能讓你更能控制磁碟使用量。

#### 小提示

- 如果你想要編輯／提交，務必將複製 URL 換成你的 fork。
- 若你之後需要更多歷史或檔案，可以擷取它們或調整 sparse-checkout 以包含額外資料夾。

## 執行程式碼

本課程提供一系列 Jupyter Notebook，可讓你透過動手操作來建立 AI Agents。

程式範例會使用以下其中一種：

**Requires GitHub Account - Free**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace。標示為 (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace。標示為 (autogen.ipynb)

**Requires Azure Subscription**:
3) Azure AI Foundry + Azure AI Agent Service。標示為 (azureaiagent.ipynb)

我們鼓勵你嘗試這三種範例，以找出最適合你的方式。

無論你選擇哪一個選項，都會決定你接下來需要遵循哪些設定步驟：

## 需求

- Python 3.12+
  - **注意**：如果你尚未安裝 Python3.12，請務必安裝。接著使用 python3.12 建立你的 venv，以確保從 requirements.txt 檔案安裝到正確的版本。
  
    >範例

    建立 Python venv 目錄：

    ```bash|powershell
    python -m venv venv
    ```

    然後啟用 venv 環境：

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+：對於使用 .NET 的範例程式碼，請確保你安裝 [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) 或更新版本。然後，檢查你已安裝的 .NET SDK 版本：

    ```bash|powershell
    dotnet --list-sdks
    ```

- 一個 GitHub 帳戶 - 用於存取 GitHub Models Marketplace
- Azure 訂閱 - 用於存取 Microsoft Foundry
- Microsoft Foundry 帳戶 - 用於存取 Azure AI Agent Service

我們在本儲存庫根目錄內包含了一個 `requirements.txt` 檔案，其中列出所有執行程式範例所需的 Python 套件。

你可以在儲存庫根目錄的終端機中執行下列指令來安裝它們：

```bash|powershell
pip install -r requirements.txt
```

我們建議建立 Python 虛擬環境以避免衝突與問題。

## 設定 VSCode

請確保你在 VSCode 中使用正確的 Python 版本。

![圖像](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## 使用 GitHub Models 的範例設定

### 步驟 1：取得你的 GitHub 個人存取權杖 (PAT)

本課程使用 GitHub Models Marketplace，提供你用以建立 AI Agents 的大型語言模型（LLM）之免費存取。

要使用 GitHub Models，你需要建立一個 [GitHub 個人存取權杖](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)。

這可以透過前往你 GitHub 帳戶中的 <a href="https://github.com/settings/personal-access-tokens" target="_blank">Personal Access Tokens 設定</a> 完成。

建立你的存取權杖時，請遵循 [最小權限原則](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely)。這表示你只應賦予該權杖執行本課程程式範例所需的權限。

1. 在畫面左側選取 `Fine-grained tokens` 選項，前往 **Developer settings**

   ![開發人員設定](../../../translated_images/zh-MO/profile_developer_settings.410a859fe749c755.webp)

   然後選取 `Generate new token`。

   ![產生新令牌](../../../translated_images/zh-MO/fga_new_token.1c1a234afe202ab3.webp)

2. 為你的權杖輸入一個具描述性的名稱，反映其用途，方便日後識別。

    🔐 令牌有效期間建議

    建議期間：30 天
    為了更安全，你可以選擇較短的期間，例如 7 天 🛡️
    這是一個很好的方式來設定個人目標，並在學習動力高時完成課程 🚀。

    ![令牌名稱與到期](../../../translated_images/zh-MO/token-name-expiry-date.a095fb0de6386864.webp)

3. 將權杖的範圍限制到你對本儲存庫的 fork。

    ![將範圍限制為分叉儲存庫](../../../translated_images/zh-MO/token_repository_limit.924ade5e11d9d8bb.webp)

4. 限制權杖的權限：在 **Permissions** 下，點選 **Account** 分頁，然後點選 "+ Add permissions" 按鈕。會出現下拉選單。請搜尋 **Models** 並勾選它。

    ![新增 Models 權限](../../../translated_images/zh-MO/add_models_permissions.c0c44ed8b40fc143.webp)

5. 在產生權杖前，請再次確認所需權限。 ![驗證權限](../../../translated_images/zh-MO/verify_permissions.06bd9e43987a8b21.webp)

6. 在產生權杖之前，請確定你已準備好將權杖儲存在安全的地方，例如密碼管理工具的保險庫，因為建立後將不會再次顯示。 ![安全儲存令牌](../../../translated_images/zh-MO/store_token_securely.08ee2274c6ad6caf.webp)

複製你剛建立的新權杖。接著你會把它新增到本課程所含的 `.env` 檔案中。

### 步驟 2：建立你的 `.env` 檔案

在終端機中執行下列指令以建立 `.env` 檔案。

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

這會複製範例檔案並在你的目錄中建立 `.env`，然後你可以在其中填入環境變數的值。

複製權杖後，使用你喜愛的文字編輯器開啟 `.env` 檔案，並將權杖貼到 `GITHUB_TOKEN` 欄位。

![GitHub 令牌欄位](../../../translated_images/zh-MO/github_token_field.20491ed3224b5f4a.webp)

你現在應該可以執行本課程的程式範例了。

## 使用 Microsoft Foundry 與 Azure AI Agent Service 的範例設定

### 步驟 1：取得你的 Azure 專案端點


請遵循在 Azure AI Foundry 中建立 hub 與專案的步驟，詳見：[Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


建立專案後，你需要擷取該專案的連線字串。

這可以透過前往 Microsoft Foundry 入口網站中你專案的 **Overview** 頁面完成。

![專案連線字串](../../../translated_images/zh-MO/project-endpoint.8cf04c9975bbfbf1.webp)

### 步驟 2：建立你的 `.env` 檔案

在終端機中執行下列指令以建立 `.env` 檔案。

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

這會複製範例檔案並在你的目錄中建立 `.env`，然後你可以在其中填入環境變數的值。

複製完端點後，使用你喜愛的文字編輯器開啟 `.env` 檔案，並將其貼到 `PROJECT_ENDPOINT` 欄位。

### 步驟 3：登入 Azure

作為安全最佳實務，我們將使用 [無密鑰驗證](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) 透過 Microsoft Entra ID 來驗證 Azure OpenAI。 

接著，開啟終端機並執行 `az login --use-device-code` 以登入你的 Azure 帳戶。

登入後，在終端機中選擇你的訂閱。

## 額外的環境變數 - Azure Search 與 Azure OpenAI 

在 Agentic RAG 課程 - 第 5 課 - 有些範例會使用 Azure Search 與 Azure OpenAI。

如果你想執行這些範例，需將下列環境變數新增到你的 `.env` 檔案：

### Overview Page (Project)

- `AZURE_SUBSCRIPTION_ID` - 在專案的 **Overview** 頁面查看 **Project details**。

- `AZURE_AI_PROJECT_NAME` - 在專案 **Overview** 頁面頂端查看專案名稱。

- `AZURE_OPENAI_SERVICE` - 在 **Overview** 頁面的 **Included capabilities** 分頁中尋找 **Azure OpenAI Service**。

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - 前往 **Management Center** 的 **Overview** 頁面中的 **Project properties**。

- `GLOBAL_LLM_SERVICE` - 在 **Connected resources** 底下，找到 **Azure AI Services** 的連線名稱。如果未列出，請在 Azure 入口網站中於你的資源群組下檢查 AI Services 的資源名稱。

### Models + Endpoints Page

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - 選擇你的 embedding 模型（例如 `text-embedding-ada-002`），並在模型詳細資訊中注意 **Deployment name**。

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - 選擇你的 chat 模型（例如 `gpt-4o-mini`），並在模型詳細資訊中注意 **Deployment name**。

### Azure 入口網站

- `AZURE_OPENAI_ENDPOINT` - 尋找 **Azure AI services**，點選它，然後前往 **Resource Management**、**Keys and Endpoint**，向下滾動到 "Azure OpenAI endpoints"，並複製標示為 "Language APIs" 的那個端點。

- `AZURE_OPENAI_API_KEY` - 在同一畫面複製 KEY 1 或 KEY 2。

- `AZURE_SEARCH_SERVICE_ENDPOINT` - 找到你的 **Azure AI Search** 資源，點選它，並查看 **Overview**。

- `AZURE_SEARCH_API_KEY` - 接著前往 **Settings** 然後 **Keys**，複製主要或次要管理金鑰。

### 外部網頁

- `AZURE_OPENAI_API_VERSION` - 前往 [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) 頁面，在 **Latest GA API release** 下查看。

### 設定無密鑰驗證

我們將使用與 Azure OpenAI 的無密鑰連線，而不是將憑據硬編碼。為此，我們會匯入 `DefaultAzureCredential`，並稍後呼叫 `DefaultAzureCredential` 函式以取得憑證。

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## 卡住了嗎？
如果在執行此設定時遇到任何問題，歡迎加入我們的 <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI 社群 Discord</a> 或 <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">建立議題</a>。

## 下一課

你現在已準備好執行本課程的程式碼。祝你在 AI 代理人的世界中學習愉快！ 

[AI 代理人介紹與使用案例](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免責聲明：
本文件係使用 AI 翻譯服務 Co-op Translator（https://github.com/Azure/co-op-translator）進行翻譯。儘管我們力求準確，但自動翻譯可能含有錯誤或不準確之處。原始語言版本應被視為具權威性的來源。對於重要資訊，建議採用專業人工翻譯。我們不會就因使用本翻譯而產生的任何誤解或誤釋承擔任何責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->