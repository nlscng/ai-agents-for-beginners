# 課程設定

## 簡介

本課程將涵蓋如何運行本課程的代碼範例。

## 加入其他學習者並獲取幫助

在開始複製你的 repo 之前，請加入 [AI Agents For Beginners Discord 頻道](https://aka.ms/ai-agents/discord) 以獲取設置上的任何幫助、關於課程的任何問題，或與其他學習者交流。

## 複製或派生此 Repo

開始之前，請複製或派生此 GitHub 儲存庫。這會建立你自己的課程資料版本，讓你可以運行、測試和調整代碼！

可以點擊此連結 <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">派生此 repo</a> 來完成。

你現在應該擁有一個你自己的課程派生版本，位於以下連結：

![Forked Repo](../../../translated_images/zh-HK/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone（建議用於工作坊 / Codespaces）

  >完整的儲存庫可能很大（約3 GB）當你下載完整歷史紀錄和所有檔案時。如果你只是參加工作坊或只需要少數課程資料夾，淺層複製（或稀疏複製）透過截斷歷史或跳過 blob，可避免大部分下載。

#### 快速淺層複製 — 最小歷史，全部檔案

將以下命令中的 `<your-username>` 替換成你的派生 URL（或者如果你願意，使用上游 URL）。

只複製最新的提交歷史（小型下載）：

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

複製特定分支：

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### 部分（稀疏）複製 — 最小 blob + 只選定資料夾

這使用部分複製和 sparse-checkout（需 Git 2.25+，建議使用支持部分複製的現代 Git）：

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

進入儲存庫資料夾：

```bash|powershell
cd ai-agents-for-beginners
```

然後指定你想要的資料夾（下例顯示兩個資料夾）：

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

複製並驗證檔案後，如果你只需要檔案且想釋放空間（無 git 歷史），請刪除儲存庫元資料（💀不可逆 — 你會失去所有 Git 功能：無法提交、拉取、推送或存取歷史）。

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### 使用 GitHub Codespaces（建議避免大型本機下載）

- 透過 [GitHub UI](https://github.com/codespaces) 為此儲存庫建立新的 Codespace。

- 在新建立的 Codespace 終端機中，執行上述淺層/稀疏複製指令，將你需要的課程資料夾帶入 Codespace 工作區。
- 選用：在 Codespaces 內複製後，移除 .git 以回收額外空間（請參閱上方的移除指令）。
- 注意：如果你偏好直接在 Codespaces 開啟儲存庫（不另行複製），請注意 Codespaces 會建構 devcontainer 環境，可能依然會佔用比你需要更多的資源。在新 Codespace 中淺層複製給你更多控制磁碟使用量的彈性。

#### 小貼士

- 若計畫編輯/提交，請務必將複製的 URL 換成你的 fork。
- 以後需要更多歷史或檔案時，可以抓取它們或調整 sparse-checkout 包含額外資料夾。

## 運行代碼

本課程提供一系列 Jupyter 筆記本，你可以運行這些筆記本來實作 AI Agent 的建構。

代碼範例使用以下其中之一：

**需要 GitHub 帳戶 - 免費**：

1) Semantic Kernel Agent Framework + GitHub Models Marketplace。標示為 (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace。標示為 (autogen.ipynb)

**需要 Azure 訂閱**：
3) Azure AI Foundry + Azure AI Agent Service。標示為 (azureaiagent.ipynb)

我們鼓勵你嘗試所有三種類型的範例，看看哪個最適合你。

不管你選擇哪種選項，都會決定你需要遵循哪些設置步驟，詳見下文：

## 系統需求

- Python 3.12+
  - **注意**：如果你還未安裝 Python3.12，請先安裝。然後用 python3.12 建立虛擬環境，確保從 requirements.txt 安裝的版本正確無誤。
  
    >範例

    建立 Python venv 目錄：

    ```bash|powershell
    python -m venv venv
    ```

    然後啟動 venv 環境：

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+：對於使用 .NET 的範例代碼，請確保已安裝 [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) 或更新版本。接著檢查已安裝的 .NET SDK 版本：

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub 帳戶 - 以存取 GitHub Models Marketplace
- Azure 訂閱 - 以存取 Microsoft Foundry
- Microsoft Foundry 帳戶 - 以存取 Azure AI Agent Service

本儲存庫根目錄已包含 `requirements.txt`，裡面包含運行代碼範例所需的所有 Python 套件。

你可以在儲存庫根目錄的終端機中執行以下命令安裝：

```bash|powershell
pip install -r requirements.txt
```

建議建立 Python 虛擬環境，以避免任何衝突與問題。

## 設定 VSCode

請確認你在 VSCode 中使用正確版本的 Python。

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## 使用 GitHub Models 範例的設定

### 第 1 步：取得你的 GitHub 個人存取權杖 (PAT)

本課程使用 GitHub Models Marketplace，提供免費存取大型語言模型 (LLMs)，讓你用於構建 AI Agents。

要使用 GitHub Models，你需要建立一組[GitHub 個人存取權杖](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)。

你可以前往 GitHub 帳戶中的 <a href="https://github.com/settings/personal-access-tokens" target="_blank">個人存取權杖設定</a> 進行。

請依照[最小權限原則](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely)來建立權杖，意思是只賦予權杖運行課程代碼範例所需的權限。

1. 從左側選擇 `Fine-grained tokens` 選項，進入 **Developer settings**

   ![Developer settings](../../../translated_images/zh-HK/profile_developer_settings.410a859fe749c755.webp)

   接著選擇 `Generate new token`。

   ![Generate Token](../../../translated_images/zh-HK/fga_new_token.1c1a234afe202ab3.webp)

2. 輸入描述性名稱，反映此權杖用途，方便日後識別。

    🔐 權杖有效期限推薦

    建議有效期限：30 天
    為更安全起見，你可以選擇較短期限 — 例如 7 天 🛡️
    這是個很好的方式設定個人的目標，在學習熱情高昂時完成課程 🚀。

    ![Token Name and Expiration](../../../translated_images/zh-HK/token-name-expiry-date.a095fb0de6386864.webp)

3. 將權杖範圍限制為你 fork 的此儲存庫。

    ![Limit scope to fork repository](../../../translated_images/zh-HK/token_repository_limit.924ade5e11d9d8bb.webp)

4. 限制權杖權限：在 **Permissions** 中點選 **Account** 標籤，點 "+ Add permissions" 按鈕，會顯示下拉選單。請搜尋 **Models** 並勾選該選項。

    ![Add Models Permission](../../../translated_images/zh-HK/add_models_permissions.c0c44ed8b40fc143.webp)

5. 生成權杖前，確認所需權限。 ![Verify Permissions](../../../translated_images/zh-HK/verify_permissions.06bd9e43987a8b21.webp)

6. 生成權杖前，請準備妥善儲存權杖（例如密碼管理保險庫），因為生成後不會再次顯示。 ![Store Token Securely](../../../translated_images/zh-HK/store_token_securely.08ee2274c6ad6caf.webp)

複製你剛生成的權杖，接下來會將它填入本課程包含的 `.env` 檔案。

### 第 2 步：建立你的 `.env` 檔案

在終端機執行以下命令以建立 `.env` 檔案。

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

此命令會複製範例檔案並建立一個 `.env` 在你的目錄中，你可以在裡面填入環境變數的值。

將權杖複製後，以你喜歡的文字編輯器開啟 `.env`，貼上你的權杖至 `GITHUB_TOKEN` 欄位。

![GitHub Token Field](../../../translated_images/zh-HK/github_token_field.20491ed3224b5f4a.webp)

你現在就能執行本課程的代碼範例。

## 使用 Microsoft Foundry 和 Azure AI Agent Service 範例的設定

### 第 1 步：取得你的 Azure 專案端點


請依照 Azure AI Foundry 文件中說明，建立 hub 和 project，連結如下：[Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


建立專案後，你需要取得專案的連線字串。

可在 Microsoft Foundry 入口網站中，專案的 **Overview** 頁面找到。

![Project Connection String](../../../translated_images/zh-HK/project-endpoint.8cf04c9975bbfbf1.webp)

### 第 2 步：建立你的 `.env` 檔案

在終端機執行以下命令以建立 `.env` 檔案。

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

此命令會複製範例檔案並建立一個 `.env` 在你的目錄中，你可以填入環境變數的值。

將端點資訊複製後，以你喜歡的文字編輯器開啟 `.env`，貼上端點到 `PROJECT_ENDPOINT` 欄位。

### 第 3 步：登入 Azure

為安全考量，我們將使用[無憑證認證](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst)來使用 Microsoft Entra ID 認證 Azure OpenAI。

開啟終端機並執行 `az login --use-device-code` 登入你的 Azure 帳戶。

登入後，在終端機選擇你的訂閱。

## 額外環境變數 - Azure Search 與 Azure OpenAI 

在 Agentic RAG 課程 - 第5課中，有範例會使用 Azure Search 與 Azure OpenAI。

若你想運行這些範例，必須在 `.env` 檔案加入以下環境變數：

### 項目概覽頁面 (Project)

- `AZURE_SUBSCRIPTION_ID` - 查看專案 **Overview** 頁面的 **Project details**。

- `AZURE_AI_PROJECT_NAME` - 查看專案 **Overview** 頁面上方。

- `AZURE_OPENAI_SERVICE` - 在 **Overview** 頁面的 **Included capabilities** 標籤中找到 **Azure OpenAI Service**。

### 管理中心

- `AZURE_OPENAI_RESOURCE_GROUP` - 前往 **Management Center** 的 **Overview** 頁面中的 **Project properties**。

- `GLOBAL_LLM_SERVICE` - 在 **Connected resources** 中找到 **Azure AI Services** 連線名稱；若無列出，請在 Azure 入口網站內資源群組中尋找 AI Services 資源名稱。

### 模型與端點頁面

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - 選擇你的嵌入模型（例如 `text-embedding-ada-002`），並在模型詳細信息中找到 **Deployment name**。

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - 選擇你的聊天模型（例如 `gpt-4o-mini`），並在模型詳細信息中找到 **Deployment name**。

### Azure 入口網站

- `AZURE_OPENAI_ENDPOINT` - 找到 **Azure AI services**，點開後前往 **Resource Management** 的 **Keys and Endpoint**，向下滾動至 "Azure OpenAI endpoints"，複製標示為 "Language APIs" 的端點。

- `AZURE_OPENAI_API_KEY` - 同一畫面，複製 KEY 1 或 KEY 2。

- `AZURE_SEARCH_SERVICE_ENDPOINT` - 找到你的 **Azure AI Search** 資源，點進去看 **Overview**。

- `AZURE_SEARCH_API_KEY` - 接著前往 **Settings** 裡的 **Keys**，複製主要或次要管理金鑰。

### 外部網頁

- `AZURE_OPENAI_API_VERSION` - 請訪問[API 版本生命週期](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release)頁面，查看 **最新 GA API 發佈**。

### 設定無憑證認證

為避免將憑證寫死，我們會使用 Azure OpenAI 的無憑證連線。為此，我們會匯入 `DefaultAzureCredential`，之後呼叫該函式，以取得認證。

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## 卡關了嗎？
如果您在運行此設置時遇到任何問題，歡迎加入我們的 <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI 社區 Discord</a> 或 <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">創建問題回報</a>。

## 下一課程

您現在已準備好運行本課程的代碼。祝您在 AI 代理的世界中學習愉快！

[AI 代理及代理使用案例簡介](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件由 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 翻譯而成。儘管我們致力於翻譯準確，但請注意自動翻譯可能存在錯誤或不準確之處。原始文件的母語版本應視為權威來源。對於重要資訊，建議使用專業人工翻譯。本公司不承擔因使用本翻譯內容而產生的任何誤解或誤譯責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->