# AGENTS.md

## 项目概述

本仓库包含“AI Agents 入门”——一门全面的教学课程，教授构建 AI 代理所需的一切。该课程包含 15 课以上，涵盖基础知识、设计模式、框架以及 AI 代理的生产部署。

**关键技术：**
- Python 3.12+
- 用于交互式学习的 Jupyter 笔记本
- AI 框架：Semantic Kernel、AutoGen、Microsoft Agent Framework (MAF)
- Azure AI 服务：Microsoft Foundry、Azure AI Agent Service
- GitHub 模型市场（提供免费套餐）

**架构：**
- 基于课程的结构（00-15+ 目录）
- 每课包含：README 文档、代码示例（Jupyter 笔记本）和图片
- 通过自动翻译系统支持多语言
- 每课提供多种框架选项（Semantic Kernel、AutoGen、Azure AI Agent Service）

## 安装命令

### 前置条件
- Python 3.12 或更高版本
- GitHub 账户（用于 GitHub 模型 - 免费套餐）
- Azure 订阅（可选，适用于 Azure AI 服务）

### 初始设置

1. **克隆或派生仓库：**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # 或者
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **创建并激活 Python 虚拟环境：**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # 在 Windows 上：venv\Scripts\activate
   ```

3. **安装依赖：**
   ```bash
   pip install -r requirements.txt
   ```

4. **设置环境变量：**
   ```bash
   cp .env.example .env
   # 使用您的 API 密钥和端点编辑 .env
   ```

### 必填环境变量

对于**GitHub 模型（免费）**：
- `GITHUB_TOKEN` - 来自 GitHub 的个人访问令牌

对于**Azure AI 服务**（可选）：
- `PROJECT_ENDPOINT` - Microsoft Foundry 项目端点
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API 密钥
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI 端点 URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - 聊天模型部署名称
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - 嵌入部署名称
- 以及 `.env.example` 中显示的其他 Azure 配置

## 开发工作流

### 运行 Jupyter 笔记本

每课包含多个针对不同框架的 Jupyter 笔记本：

1. **启动 Jupyter：**
   ```bash
   jupyter notebook
   ```

2. **导航至某课目录**（例如 `01-intro-to-ai-agents/code_samples/`）

3. **打开并运行笔记本：**
   - `*-semantic-kernel.ipynb` - 使用 Semantic Kernel 框架
   - `*-autogen.ipynb` - 使用 AutoGen 框架
   - `*-python-agent-framework.ipynb` - 使用 Microsoft Agent Framework（Python）
   - `*-dotnet-agent-framework.ipynb` - 使用 Microsoft Agent Framework（.NET）
   - `*-azureaiagent.ipynb` - 使用 Azure AI Agent Service

### 使用不同框架

**Semantic Kernel + GitHub 模型：**
- GitHub 账户免费套餐可用
- 适合学习与实验
- 文件模式：`*-semantic-kernel*.ipynb`

**AutoGen + GitHub 模型：**
- GitHub 账户免费套餐可用
- 支持多代理编排
- 文件模式：`*-autogen.ipynb`

**Microsoft Agent Framework (MAF)：**
- 微软最新框架
- Python 和 .NET 版本均有
- 文件模式：`*-agent-framework.ipynb`

**Azure AI Agent Service：**
- 需要 Azure 订阅
- 具备生产级功能
- 文件模式：`*-azureaiagent.ipynb`

## 测试说明

本仓库是教育用例代码库，示例代码非生产代码且无自动测试。验证安装和更改时：

### 手动测试

1. **测试 Python 环境：**
   ```bash
   python --version  # 应该是 3.12 及以上
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **测试笔记本执行：**
   ```bash
   # 将笔记本转换为脚本并运行（测试导入）
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **验证环境变量：**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### 运行单个笔记本

在 Jupyter 中打开笔记本，依次执行代码单元。每个笔记本自成体系，包含：
- 导入语句
- 配置加载
- 示例代理实现
- 期望输出（Markdown 单元格说明）

## 代码规范

### Python 规范

- **Python 版本**：3.12+
- **代码风格**：遵循 Python 官方 PEP 8 标准
- **笔记本**：使用清晰的 Markdown 单元格解释概念
- **导入语句**：按标准库、第三方、本地库分组

### Jupyter 笔记本规范

- 在代码单元前包含描述性 Markdown 单元
- 在笔记本中添加输出示例供参考
- 变量命名清晰，匹配课程概念
- 笔记本执行顺序保持线性（单元 1 → 2 → 3...）

### 文件组织

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

## 构建与部署

### 构建文档

本仓库文档使用 Markdown：
- 各课文件夹中的 README.md 文件
- 仓库根目录主 README.md
- 通过 GitHub Actions 自动翻译系统

### CI/CD 流水线

位于 `.github/workflows/`：

1. **co-op-translator.yml** - 自动翻译成 50+ 种语言
2. **welcome-issue.yml** -欢迎新问题创建者
3. **welcome-pr.yml** -欢迎新的 Pull Request 贡献者

### 部署

这是教育仓库，没有部署流程。用户：
1. Fork 或克隆仓库
2. 在本地或 GitHub Codespaces 中运行笔记本
3. 通过修改和实验示例进行学习

## Pull Request 指南

### 提交前准备

1. **测试修改：**
   - 完整运行所有受影响笔记本
   - 确保所有单元无错误执行
   - 检查输出是否合理

2. **文档更新：**
   - 若新增概念，更新 README.md
   - 笔记本内为复杂代码添加注释
   - 确保 Markdown 单元解释目的

3. **文件变更：**
   - 避免提交 `.env` 文件（使用 `.env.example`）
   - 不提交 `venv/` 或 `__pycache__/` 目录
   - 保留演示概念的笔记本输出
   - 删除临时文件和备份笔记本（`*-backup.ipynb`）

### PR 标题格式

采用描述性标题：
- `[Lesson-XX] 新增 <概念> 示例`
- `[Fix] 修正 lesson-XX README 拼写错误`
- `[Update] 优化 lesson-XX 代码示例`
- `[Docs] 更新安装说明`

### 必要检查

- 笔记本应能无错运行
- README 文件须清晰准确
- 遵循仓库既有代码模式
- 与其他课程保持一致性

## 其他说明

### 常见问题

1. **Python 版本不匹配：**
   - 确保使用 Python 3.12+
   - 部分包可能无法在旧版本下使用
   - 用 `python3 -m venv` 明确指定 Python 版本

2. **环境变量：**
   - 始终从 `.env.example` 创建 `.env` 文件
   - 不要提交 `.env` 文件（已列入 `.gitignore`）
   - GitHub 令牌需具备适当权限

3. **依赖冲突：**
   - 使用新的虚拟环境
   - 通过 `requirements.txt` 安装依赖，避免单独安装包
   - 某些笔记本可能需额外包，描述在 Markdown 里

4. **Azure 服务：**
   - Azure AI 服务需有效订阅
   - 部分功能受地区限制
   - GitHub 模型有免费额度限制

### 学习路径

推荐按顺序学习课程：
1. **00-course-setup** - 环境搭建入门
2. **01-intro-to-ai-agents** - AI 代理基础知识
3. **02-explore-agentic-frameworks** - 不同框架介绍
4. **03-agentic-design-patterns** - 核心设计模式
5. 依序学习后续编号课程

### 框架选择

依目标选择框架：
- **学习/原型**：Semantic Kernel + GitHub 模型（免费）
- **多代理系统**：AutoGen
- **最新特性**：Microsoft Agent Framework (MAF)
- **生产部署**：Azure AI Agent Service

### 获取帮助

- 加入 [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- 查看各课 README 文件获取具体指导
- 参阅主 [README.md](./README.md) 了解课程概况
- 查阅 [课程设置](./00-course-setup/README.md) 获取详细安装指南

### 贡献指南

这是一个开放的教育项目，欢迎贡献：
- 改进代码示例
- 修正拼写或错误
- 添加说明注释
- 建议新增课程主题
- 翻译成其他语言

详见 [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) 了解当前需求。

## 项目特定背景

### 多语言支持

本仓库采用自动翻译系统：
- 支持 50 多种语言
- 翻译文件位于 `/translations/<lang-code>/` 目录
- GitHub Actions 工作流处理翻译更新
- 源文件均为英文，位于仓库根目录

### 课程结构

每课遵循一致格式：
1. 视频缩略图带链接
2. 文字课程内容（README.md）
3. 多框架代码示例
4. 学习目标和前置知识
5. 额外学习资源链接

### 代码示例命名

格式为 `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - 第 4 课，Semantic Kernel
- `07-autogen.ipynb` - 第 7 课，AutoGen
- `14-python-agent-framework.ipynb` - 第 14 课，MAF Python 版
- `14-dotnet-agent-framework.ipynb` - 第 14 课，MAF .NET 版

### 特殊目录

- `translated_images/` - 翻译后的本地化图片
- `images/` - 英文原始图片
- `.devcontainer/` - VS Code 开发容器配置
- `.github/` - GitHub Actions 工作流和模板

### 依赖项

`requirements.txt` 主要包：
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen 框架
- `semantic-kernel` - Semantic Kernel 框架
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AI 服务
- `azure-search-documents` - Azure AI 搜索集成
- `chromadb` - 用于 RAG 示例的向量数据库
- `chainlit` - 聊天界面框架
- `browser_use` - 代理的浏览器自动化
- `mcp[cli]` - 模型上下文协议支持
- `mem0ai` - 代理内存管理

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免责声明**：  
本文件使用 AI 翻译服务 [Co-op Translator](https://github.com/Azure/co-op-translator) 进行翻译。尽管我们努力确保翻译的准确性，但请注意自动翻译可能存在错误或不准确之处。原始文件的母语版本应视为权威来源。对于关键信息，建议采用专业人工翻译。我们不对因使用本翻译而产生的任何误解或误读承担责任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->