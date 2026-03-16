# AGENTS.md

## 專案概述

此倉庫包含「初學者 AI 代理人」——一門全面的教育課程，涵蓋構建 AI 代理人所需的一切。課程包括 15+ 節課程，涵蓋基礎知識、設計模式、框架與 AI 代理人的生產部署。

**關鍵技術：**
- Python 3.12+
- 用於互動學習的 Jupyter 筆記本
- AI 框架：Semantic Kernel、AutoGen、Microsoft Agent Framework (MAF)
- Azure AI 服務：Microsoft Foundry、Azure AI Agent Service
- GitHub Models Marketplace（提供免費檔次）

**架構：**
- 以課程為基礎的結構（00-15+ 目錄）
- 每節課包含：README 文檔、程式碼範例（Jupyter 筆記本）、圖片
- 透過自動翻譯系統支援多語言
- 每節課提供多種框架選項（Semantic Kernel、AutoGen、Azure AI Agent Service）

## 安裝命令

### 前置條件
- Python 3.12 或更高版本
- GitHub 帳號（用於 GitHub Models - 免費檔次）
- Azure 訂閱（可選，用於 Azure AI 服務）

### 初始設置

1. **克隆或分叉倉庫：**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # 或者
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **建立並激活 Python 虛擬環境：**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # 在 Windows 上：venv\Scripts\activate
   ```

3. **安裝依賴項：**
   ```bash
   pip install -r requirements.txt
   ```

4. **設定環境變數：**
   ```bash
   cp .env.example .env
   # 用你的 API 密鑰和端點編輯 .env
   ```

### 必須的環境變數

對於 **GitHub Models（免費）**：
- `GITHUB_TOKEN` - GitHub 個人存取權杖

對於 **Azure AI 服務**（可選）：
- `PROJECT_ENDPOINT` - Microsoft Foundry 專案端點
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API 金鑰
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI 端點 URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - 聊天模型部署名稱
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - 嵌入部署名稱
- 如 `.env.example` 中所示的其他 Azure 設定

## 開發工作流程

### 運行 Jupyter 筆記本

每節課包含多個針對不同框架的 Jupyter 筆記本：

1. **啟動 Jupyter：**
   ```bash
   jupyter notebook
   ```

2. **導航至課程目錄**（例如，`01-intro-to-ai-agents/code_samples/`）

3. **打開並執行筆記本：**
   - `*-semantic-kernel.ipynb` - 使用 Semantic Kernel 框架
   - `*-autogen.ipynb` - 使用 AutoGen 框架
   - `*-python-agent-framework.ipynb` - 使用 Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - 使用 Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - 使用 Azure AI Agent Service

### 使用不同框架

**Semantic Kernel + GitHub Models：**
- 提供免費檔次，需要 GitHub 帳號
- 適合學習與實驗
- 檔案模式：`*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models：**
- 提供免費檔次，需要 GitHub 帳號
- 支援多代理調度能力
- 檔案模式：`*-autogen.ipynb`

**Microsoft Agent Framework (MAF)：**
- 微軟最新框架
- 提供 Python 與 .NET 版本
- 檔案模式：`*-agent-framework.ipynb`

**Azure AI Agent Service：**
- 需要 Azure 訂閱
- 生產級功能
- 檔案模式：`*-azureaiagent.ipynb`

## 測試說明

這是一個教育倉庫，包含範例程式碼而非具有自動化測試的生產代碼。用於驗證環境與變更：

### 手動測試

1. **測試 Python 環境：**
   ```bash
   python --version  # 應該係 3.12 或以上
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **測試筆記本執行：**
   ```bash
   # 將筆記本轉換為腳本並執行（測試匯入）
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **驗證環境變數：**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### 執行個別筆記本

在 Jupyter 中打開筆記本，按順序執行儲存格。每個筆記本均為自包含，含有：
- 匯入語句
- 讀取設定
- 代理人範例實現
- Markdown 儲存格中的預期輸出

## 程式碼風格

### Python 規範

- **Python 版本**：3.12+
- **程式碼風格**：遵守標準 Python PEP 8 規範
- **筆記本**：使用清晰的 markdown 儲存格解釋概念
- **匯入語句**：分組標準庫、第三方、當地匯入

### Jupyter 筆記本規範

- 在程式碼前包含描述性 markdown 儲存格
- 在筆記本中添加輸出範例供參考
- 使用符合課程概念的清晰變數名稱
- 保持筆記本執行順序線性（儲存格 1 → 2 → 3...）

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

### 建置文檔

此倉庫使用 Markdown 撰寫文檔：
- 每節課資料夾中的 README.md 檔案
- 倉庫根目錄的主 README.md
- 透過 GitHub Actions 的自動翻譯系統

### CI/CD 流程

位於 `.github/workflows/`：

1. **co-op-translator.yml** - 自動翻譯成 50+ 種語言
2. **welcome-issue.yml** - 歡迎新的議題創建者
3. **welcome-pr.yml** - 歡迎新的拉取請求貢獻者

### 部署

這是教育用倉庫，無部署流程。使用者可：
1. 分叉或克隆此倉庫
2. 本地或 GitHub Codespaces 中運行筆記本
3. 透過修改及實驗範例學習

## 拉取請求指南

### 提交前

1. **測試您的更改：**
   - 完整執行受影響的筆記本
   - 確認所有儲存格無錯誤
   - 檢查輸出是否適當

2. **文件更新：**
   - 若加入新概念請更新 README.md
   - 在筆記本中為複雜程式碼添加註解
   - 確保 markdown 儲存格解釋目的

3. **檔案變更：**
   - 避免提交 `.env` 檔案（請用 `.env.example`）
   - 不要提交 `venv/` 或 `__pycache__/` 目錄
   - 保留能展示概念的筆記本輸出
   - 移除臨時檔案與備份筆記本（`*-backup.ipynb`）

### PR 標題格式

使用描述性標題：
- `[Lesson-XX] 新增 <概念> 範例`
- `[Fix] 修正 lesson-XX README 拼寫`
- `[Update] 改善 lesson-XX 範例`
- `[Docs] 更新安裝指引`

### 必須檢查項目

- 筆記本能無錯誤執行
- README 檔案清晰且正確
- 遵守現有程式碼風格
- 與其他課程保持一致性

## 附加說明

### 常見陷阱

1. **Python 版本不符：**
   - 確保使用 Python 3.12+
   - 部分套件不支援舊版本
   - 使用 `python3 -m venv` 明確指定版本

2. **環境變數：**
   - 必須由 `.env.example` 創建 `.env`
   - 不要提交 `.env`（已列入 `.gitignore`）
   - GitHub Token 需要適當權限

3. **套件衝突：**
   - 使用全新虛擬環境安裝
   - 從 `requirements.txt` 安裝，而非單獨套件
   - 有些筆記本需要額外套件，見 markdown 說明

4. **Azure 服務：**
   - 需有效 Azure 訂閱
   - 部分功能地區限定
   - GitHub Models 免費檔次有相應限制

### 學習路徑

建議課程進度：
1. **00-course-setup** - 從環境配置開始
2. **01-intro-to-ai-agents** - 理解 AI 代理基礎
3. **02-explore-agentic-frameworks** - 認識不同框架
4. **03-agentic-design-patterns** - 核心設計模式
5. 按序繼續後續課程

### 框架選擇

依目標選擇框架：
- **學習/原型開發**：Semantic Kernel + GitHub Models（免費）
- **多代理系統**：AutoGen
- **最新功能**：Microsoft Agent Framework (MAF)
- **生產部署**：Azure AI Agent Service

### 尋求協助

- 加入[Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- 參考課程 README 文件獲取具體指導
- 查閱主 README.md 以瞭解課程總覽
- 詳見 [Course Setup](./00-course-setup/README.md) 了解詳盡安裝指引

### 貢獻指南

這是個開放教育專案，歡迎貢獻：
- 改善程式碼範例
- 修正拼寫或錯誤
- 添加說明性註解
- 建議新增課程主題
- 翻譯成其他語言

查看 [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) 了解目前需求。

## 專案特定內容

### 多語言支援

本倉庫使用自動翻譯系統：
- 支持 50+ 種語言
- 翻譯檔案位於 `/translations/<lang-code>/` 目錄
- GitHub Actions 工作流程負責更新翻譯
- 原始檔案以英文存於倉庫根目錄

### 課程結構

每節課遵循一致模式：
1. 含連結的影片縮圖
2. 書面課程內容 (README.md)
3. 多框架程式碼範例
4. 學習目標與先決條件
5. 連結額外學習資源

### 程式碼範例命名

格式：`<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - 第 4 課，Semantic Kernel
- `07-autogen.ipynb` - 第 7 課，AutoGen
- `14-python-agent-framework.ipynb` - 第 14 課，MAF Python
- `14-dotnet-agent-framework.ipynb` - 第 14 課，MAF .NET

### 特殊目錄

- `translated_images/` - 本地化圖片
- `images/` - 英文原圖
- `.devcontainer/` - VS Code 開發容器設定
- `.github/` - GitHub Actions 工作流程與模板

### 依賴套件

主要套件見 `requirements.txt`：
- `autogen-agentchat`、`autogen-core`、`autogen-ext` - AutoGen 框架
- `semantic-kernel` - Semantic Kernel 框架
- `agent-framework` - 微軟 Agent Framework
- `azure-ai-inference`、`azure-ai-projects` - Azure AI 服務
- `azure-search-documents` - Azure AI 搜索整合
- `chromadb` - 用於 RAG 範例的向量資料庫
- `chainlit` - 聊天 UI 框架
- `browser_use` - 代理人瀏覽器自動化
- `mcp[cli]` - 模型上下文協議支援
- `mem0ai` - 代理人記憶管理

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件係使用人工智能翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。儘管我們力求準確，請注意自動翻譯可能包含錯誤或不準確之處。原文文件的母語版本應視為權威來源。對於重要資訊，建議採用專業人工翻譯。我們對因使用本翻譯而引起的任何誤解或誤譯概不負責。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->