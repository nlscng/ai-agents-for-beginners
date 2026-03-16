# AGENTS.md

## 專案概覽

此存放庫包含「初學者的 AI 代理人」 — 一門涵蓋建立 AI 代理人所需一切的完整教育課程。課程包含 15+ 堂課，涵蓋基礎、設計模式、框架及 AI 代理人之生產部署。

**關鍵技術：**
- Python 3.12+
- 用於互動學習的 Jupyter 筆記本
- AI 框架：Semantic Kernel、AutoGen、Microsoft Agent Framework (MAF)
- Azure AI 服務：Microsoft Foundry、Azure AI Agent Service
- GitHub 模型市場（提供免費等級）

**架構：**
- 以課程為基礎的結構（00-15+ 目錄）
- 每堂課包含：README 文件、程式碼範例（Jupyter 筆記本）及圖片
- 透過自動翻譯系統實現多語言支援
- 每堂課提供多個框架選項（Semantic Kernel、AutoGen、Azure AI Agent Service）

## 設置指令

### 前置需求
- Python 3.12 或以上版本
- GitHub 帳戶（使用 GitHub 模型 - 免費等級）
- Azure 訂閱（可選，使用 Azure AI 服務時）

### 初始設置

1. **複製或分支此存放庫：**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # 或者
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **建立並啟用 Python 虛擬環境：**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # 在 Windows 上：venv\Scripts\activate
   ```

3. **安裝相依套件：**
   ```bash
   pip install -r requirements.txt
   ```

4. **設定環境變數：**
   ```bash
   cp .env.example .env
   # 使用您的 API 金鑰和端點編輯 .env
   ```

### 必要的環境變數

針對 **GitHub 模型（免費）**：
- `GITHUB_TOKEN` - 來自 GitHub 的個人存取權杖

針對 **Azure AI 服務**（可選）：
- `PROJECT_ENDPOINT` - Microsoft Foundry 專案端點
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API 金鑰
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI 端點 URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - 聊天模型的部署名稱
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - 嵌入模型的部署名稱
- 其他 Azure 配置請參考 `.env.example`

## 開發工作流程

### 執行 Jupyter 筆記本

每堂課包含依不同框架拆分的多個 Jupyter 筆記本：

1. **啟動 Jupyter：**
   ```bash
   jupyter notebook
   ```

2. **進入指定課程目錄**（例如 `01-intro-to-ai-agents/code_samples/`）

3. **開啟並執行筆記本：**
   - `*-semantic-kernel.ipynb` - 使用 Semantic Kernel 框架
   - `*-autogen.ipynb` - 使用 AutoGen 框架
   - `*-python-agent-framework.ipynb` - 使用 Microsoft Agent Framework（Python）
   - `*-dotnet-agent-framework.ipynb` - 使用 Microsoft Agent Framework（.NET）
   - `*-azureaiagent.ipynb` - 使用 Azure AI Agent 服務

### 使用不同框架

**Semantic Kernel + GitHub 模型：**
- 免費等級需有 GitHub 帳戶
- 適合學習與實驗
- 檔案格式：`*-semantic-kernel*.ipynb`

**AutoGen + GitHub 模型：**
- 免費等級需有 GitHub 帳戶
- 支援多代理人協調
- 檔案格式：`*-autogen.ipynb`

**Microsoft Agent Framework (MAF)：**
- 微軟最新框架
- 支援 Python 及 .NET
- 檔案格式：`*-agent-framework.ipynb`

**Azure AI Agent Service：**
- 需要 Azure 訂閱
- 適合生產環境功能
- 檔案格式：`*-azureaiagent.ipynb`

## 測試說明

這是教育性質存放庫，包含示範程式碼而非自動化測試的生產程式碼。要驗證你的設置與變更：

### 手動測試

1. **測試 Python 環境：**
   ```bash
   python --version  # 應該是 3.12 以上
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **測試筆記本執行：**
   ```bash
   # 將筆記本轉換為腳本並執行（測試匯入）
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **確認環境變數：**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### 執行單一筆記本

在 Jupyter 中開啟並依序執行每個儲存格。每個筆記本均自成一體，包含：
- 匯入宣告
- 載入配置
- 範例代理人實作
- 以 markdown 儲存格展示預期輸出

## 程式碼風格

### Python 慣例

- **Python 版本**：3.12+
- **程式碼風格**：遵循 Python PEP 8 標準
- **筆記本**：使用清晰 markdown 儲存格說明概念
- **匯入**：分組標準庫、第三方、本地匯入

### Jupyter 筆記本慣例

- 在程式碼前添加具描述性的 markdown 儲存格
- 筆記本中加入輸出示例供參考
- 使用符合課程概念的明確變數名稱
- 執行順序保持線性（儲存格 1 → 2 → 3…）

### 檔案組織

```
<lesson-number>-<lesson-name>/
├── README.md                     # Lesson documentation
├── code_samples/
│   ├── <number>-semantic-kernel.ipynb
│   ├── <number>-autogen.ipynb
│   ├── <number>-python-agent-framework.ipynb
│   └── <number>-azureaiagent.ipynb
└── images/
    └── *.png
```

## 建置與部署

### 文件建置

此存放庫使用 Markdown 文件：
- 每堂課資料夾中的 README.md 檔案
- 存放庫根目錄的主要 README.md
- 透過 GitHub Actions 自動翻譯系統

### CI/CD 工作流程

位於 `.github/workflows/`：

1. **co-op-translator.yml** - 自動翻譯成 50+ 種語言
2. **welcome-issue.yml** - 歡迎新議題建立者
3. **welcome-pr.yml** - 歡迎新拉取請求貢獻者

### 部署

此為教育性質存放庫，無部署流程。使用者：
1. 分支或複製存放庫
2. 本地或 GitHub Codespaces 執行筆記本
3. 透過修改與實驗範例學習

## 拉取請求指引

### 提交前準備

1. **測試你的變更：**
   - 完整執行受影響的筆記本
   - 確認所有儲存格無錯誤
   - 驗證輸出是否正確

2. **文件更新：**
   - 新增概念時更新 README.md
   - 複雜程式碼加註筆記本註解
   - 確保 markdown 儲存格說明目的

3. **檔案更改：**
   - 避免提交 `.env` 檔案（使用 `.env.example`）
   - 不提交 `venv/` 或 `__pycache__/` 目錄
   - 筆記本示範概念時保留輸出
   - 移除暫存檔與備份筆記本（`*-backup.ipynb`）

### PR 標題格式

使用描述性標題：
- `[Lesson-XX] 新增 <概念> 範例`
- `[Fix] 修正 lesson-XX README 拼字錯誤`
- `[Update] 改善 lesson-XX 程式碼範例`
- `[Docs] 更新安裝指示`

### 必要檢查項目

- 筆記本能無誤執行
- README 文件清晰且準確
- 遵循現有程式碼模式
- 與其他課程保持一致性

## 附加說明

### 常見問題

1. **Python 版本不符：**
   - 請確保使用 Python 3.12+
   - 舊版本部分套件可能無法使用
   - 使用 `python3 -m venv` 指定 Python 版本

2. **環境變數：**
   - 務必從 `.env.example` 建立 `.env`
   - 不要提交 `.env` （已加入 `.gitignore`）
   - GitHub Token 需要適當權限

3. **套件衝突：**
   - 使用全新虛擬環境
   - 透過 `requirements.txt` 安裝套件，不逐個安裝
   - 部分筆記本在 markdown 中提及需安裝額外套件

4. **Azure 服務：**
   - 使用 Azure AI 服務需有有效訂閱
   - 部分功能區域限制
   - GitHub 模型免費等級有使用限制

### 學習路徑

推薦的課程進度：
1. **00-course-setup** - 從此開始環境設置
2. **01-intro-to-ai-agents** - 理解 AI 代理人基礎
3. **02-explore-agentic-frameworks** - 認識不同框架
4. **03-agentic-design-patterns** - 核心設計模式
5. 依序繼續參與編號課程

### 框架選擇

根據目標挑選框架：
- **學習／原型設計**：Semantic Kernel + GitHub 模型（免費）
- **多代理系統**：AutoGen
- **最新功能**：Microsoft Agent Framework (MAF)
- **生產部署**：Azure AI Agent Service

### 尋求協助

- 加入 [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- 閱讀各課程 README 文件尋找具體指引
- 查閱主 README.md 了解課程概覽
- 參考 [Course Setup](./00-course-setup/README.md) 進行詳細設置

### 貢獻方式

此為開放教育專案，歡迎貢獻：
- 改善程式碼範例
- 修正錯字或錯誤
- 新增說明註解
- 建議新課程主題
- 協助翻譯至更多語言

詳情請參考 [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) 的需求。

## 專案特定背景

### 多語言支援

本存放庫使用自動翻譯系統：
- 支援 50+ 種語言
- 翻譯位於 `/translations/<lang-code>/` 目錄
- 由 GitHub Actions 工作流程自動管理翻譯更新
- 原始檔案語言為英文，存放於根目錄

### 課程結構

每堂課遵循一致模式：
1. 影片縮圖含超連結
2. 課程書面內容 (README.md)
3. 多種框架的程式碼範例
4. 學習目標與先備知識
5. 附加學習資源連結

### 程式碼範例命名

格式：`<課程編號>-<框架名稱>.ipynb`
- `04-semantic-kernel.ipynb` - 第 4 課，Semantic Kernel
- `07-autogen.ipynb` - 第 7 課，AutoGen
- `14-python-agent-framework.ipynb` - 第 14 課，MAF Python
- `14-dotnet-agent-framework.ipynb` - 第 14 課，MAF .NET

### 特殊目錄

- `translated_images/` - 翻譯後對應的本地化圖片
- `images/` - 英文原生圖片
- `.devcontainer/` - VS Code 開發容器配置
- `.github/` - GitHub Actions 工作流程及模板

### 相依套件

`requirements.txt` 主要套件：
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen 框架
- `semantic-kernel` - Semantic Kernel 框架
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI 服務
- `azure-search-documents` - Azure AI 搜尋整合
- `chromadb` - 用於 RAG 範例的向量資料庫
- `chainlit` - 聊天 UI 框架
- `browser_use` - 瀏覽器自動化代理人
- `mcp[cli]` - 模型上下文協定支援
- `mem0ai` - 代理人記憶管理

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件係使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們力求準確，請注意自動翻譯可能包含錯誤或不精確之處。原始文件的母語版本應被視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們不對因使用本翻譯而產生的任何誤解或誤釋負責。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->