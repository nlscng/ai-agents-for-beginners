# 课程设置

## 介绍

本课将介绍如何运行本课程的代码示例。

## 加入其他学习者并获得帮助

在开始克隆你的仓库之前，请加入 [AI Agents 初学者 Discord 频道](https://aka.ms/ai-agents/discord) 获取任何设置方面的帮助、对课程的任何问题，或与其他学习者交流。

## 克隆或 Fork 此仓库

首先，请克隆或 Fork GitHub 仓库。这将创建课程资料的你自己的版本，以便你可以运行、测试和调整代码！

你可以通过点击链接来 <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">Fork 仓库</a>

你现在应该在下面的链接中拥有该课程的你自己的 Fork 版本：

![已 Fork 的仓库](../../../translated_images/zh-CN/forked-repo.33f27ca1901baa6a.webp)

### 浅克隆（建议用于研讨会 / Codespaces）

  > 当你下载完整历史和所有文件时，完整仓库可能很大（~3 GB）。如果你只参加研讨会或只需要少数课程文件夹，浅克隆（或稀疏克隆）通过截断历史和/或跳过 blob 来避免大部分下载。

#### 快速浅克隆 — 最小历史，所有文件

将下面命令中的 `<your-username>` 替换为你的 Fork URL（或如果你愿意，则替换为上游 URL）。

要仅克隆最近的提交历史（小下载）：

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

要克隆特定分支：

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### 部分（稀疏）克隆 — 最小 blob + 仅选定文件夹

这使用部分克隆和 sparse-checkout（需要 Git 2.25+ 且建议使用支持部分克隆的现代 Git）：

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

进入仓库文件夹：

```bash|powershell
cd ai-agents-for-beginners
```

然后指定你想要的文件夹（下面示例显示两个文件夹）：

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

在克隆并验证文件后，如果你只需要文件并希望释放空间（没有 git 历史），请删除仓库元数据（💀不可逆—你将失去所有 Git 功能：无法提交、拉取、推送或访问历史）。

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### 使用 GitHub Codespaces（建议以避免本地大规模下载）

- 通过 [GitHub UI](https://github.com/codespaces) 为此仓库创建一个新的 Codespace。  

- 在新创建的 Codespace 的终端中，运行上述浅克隆/稀疏克隆命令之一，将你需要的课程文件夹带入 Codespace 工作区。
- 可选：在 Codespaces 内克隆后，移除 .git 以回收额外空间（见上方的移除命令）。
- 注意：如果你更喜欢直接在 Codespaces 中打开仓库（无需额外克隆），请注意 Codespaces 会构建 devcontainer 环境，可能仍会配置超出你需要的内容。在新鲜的 Codespace 内克隆一个浅副本可以让你更好地控制磁盘使用情况。

#### 提示

- 如果你想编辑/提交，请始终将克隆 URL 替换为你的 Fork。
- 如果以后需要更多历史或文件，你可以获取它们或调整 sparse-checkout 以包含其他文件夹。

## 运行代码

本课程提供了一系列可以运行的 Jupyter Notebook，让你通过实践体验构建 AI Agent。

代码示例使用以下任一项：

**需要 GitHub 账号 - 免费：**

1) Semantic Kernel Agent Framework + GitHub Models Marketplace。 标注为 (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace。 标注为 (autogen.ipynb)

**需要 Azure 订阅：**
3) Azure AI Foundry + Azure AI Agent Service。 标注为 (azureaiagent.ipynb)

我们鼓励你尝试所有三种示例，以便找到最适合你的方案。

无论你选择哪种选项，它将决定下面你需要遵循的设置步骤：

## 要求

- Python 3.12+
  - **注意**：如果你没有安装 Python3.12，请确保安装它。然后使用 python3.12 创建你的 venv，以确保从 requirements.txt 文件中安装正确的版本。
  
    >示例

    创建 Python venv 目录：

    ```bash|powershell
    python -m venv venv
    ```

    然后激活 venv 环境以运行：

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+：对于使用 .NET 的示例代码，请确保安装 [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) 或更高版本。然后，检查你已安装的 .NET SDK 版本：

    ```bash|powershell
    dotnet --list-sdks
    ```

- 一个 GitHub 账号 - 用于访问 GitHub Models Marketplace
- Azure 订阅 - 用于访问 Microsoft Foundry
- Microsoft Foundry 账号 - 用于访问 Azure AI Agent Service

我们在此仓库根目录中包含了一个 `requirements.txt` 文件，其中包含运行代码示例所需的所有 Python 包。

你可以在仓库根目录的终端运行以下命令来安装它们：

```bash|powershell
pip install -r requirements.txt
```

我们建议创建一个 Python 虚拟环境以避免任何冲突和问题。

## 设置 VSCode

确保你在 VSCode 中使用的是正确版本的 Python。

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## 为使用 GitHub Models 的示例设置

### 第 1 步：检索你的 GitHub 个人访问令牌（PAT）

本课程利用 GitHub Models Marketplace，提供你将用于构建 AI Agent 的大型语言模型（LLM）的免费访问。

要使用 GitHub Models，你需要创建一个 [GitHub 个人访问令牌](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)。

你可以通过进入你的 GitHub 账号中的 <a href="https://github.com/settings/personal-access-tokens" target="_blank">个人访问令牌设置</a> 来完成此操作。

请在创建令牌时遵循 [最小权限原则](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely)。这意味着你应该仅授予令牌运行本课程代码示例所需的权限。

1. 在屏幕左侧的 **开发者设置** 中选择 `Fine-grained tokens` 选项

   ![开发者设置](../../../translated_images/zh-CN/profile_developer_settings.410a859fe749c755.webp)

   然后选择 `Generate new token`。

   ![生成令牌](../../../translated_images/zh-CN/fga_new_token.1c1a234afe202ab3.webp)

2. 输入一个描述性名称来反映令牌的用途，便于以后识别。

    🔐 令牌持续时间建议

    推荐持续时间：30 天
    为了更安全，你可以选择更短的周期——例如 7 天 🛡️
    这是在学习热情高涨时设定个人目标并完成课程的好方法 🚀。

    ![令牌名称和到期时间](../../../translated_images/zh-CN/token-name-expiry-date.a095fb0de6386864.webp)

3. 将令牌的作用域限制为你对此仓库的 Fork。

    ![将作用域限制为 fork 的仓库](../../../translated_images/zh-CN/token_repository_limit.924ade5e11d9d8bb.webp)

4. 限制令牌的权限：在 **Permissions** 下，点击 **Account** 选项卡，然后点击 “+ Add permissions” 按钮。将出现下拉菜单。请搜索 **Models** 并勾选其复选框。

    ![添加 Models 权限](../../../translated_images/zh-CN/add_models_permissions.c0c44ed8b40fc143.webp)

5. 在生成令牌之前，请核实所需权限。 ![核实权限](../../../translated_images/zh-CN/verify_permissions.06bd9e43987a8b21.webp)

6. 在生成令牌之前，确保你已准备好将令牌存储在像密码管理器保险库这样的安全位置，因为创建后将不会再次显示。 ![安全存储令牌](../../../translated_images/zh-CN/store_token_securely.08ee2274c6ad6caf.webp)

复制你刚创建的新令牌。现在你将把它添加到本课程包含的 `.env` 文件中。

### 第 2 步：创建你的 `.env` 文件

在终端中运行以下命令以创建你的 `.env` 文件。

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

这将复制示例文件并在你的目录中创建一个 `.env`，你可在其中填写环境变量的值。

复制令牌后，在你喜欢的文本编辑器中打开 `.env` 文件，并将令牌粘贴到 `GITHUB_TOKEN` 字段中。

![GitHub 令牌字段](../../../translated_images/zh-CN/github_token_field.20491ed3224b5f4a.webp)

现在你应该能够运行本课程的代码示例。

## 为使用 Microsoft Foundry 和 Azure AI Agent Service 的示例设置

### 第 1 步：检索你的 Azure 项目端点


请按照此处的步骤在 Azure AI Foundry 中创建 hub 和项目：[Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


创建项目后，你需要检索该项目的连接字符串。

可以通过转到 Microsoft Foundry 门户中项目的 **概览** 页面来完成此操作。

![项目连接字符串](../../../translated_images/zh-CN/project-endpoint.8cf04c9975bbfbf1.webp)

### 第 2 步：创建你的 `.env` 文件

在终端中运行以下命令以创建你的 `.env` 文件。

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

这将复制示例文件并在你的目录中创建一个 `.env`，你可在其中填写环境变量的值。

复制你的令牌后，在你喜欢的文本编辑器中打开 `.env` 文件，并将令牌粘贴到 `PROJECT_ENDPOINT` 字段中。

### 第 3 步：登录 Azure

作为安全最佳实践，我们将使用 [无密钥身份验证](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) 使用 Microsoft Entra ID 对 Azure OpenAI 进行身份验证。 

接下来，打开终端并运行 `az login --use-device-code` 以登录你的 Azure 账号。

登录后，在终端中选择你的订阅。

## 其他环境变量 - Azure Search 和 Azure OpenAI 

对于 Agentic RAG 课程 - 第 5 课 - 有些示例使用 Azure Search 和 Azure OpenAI。

如果你想运行这些示例，需要将以下环境变量添加到你的 `.env` 文件中：

### 概览页面（项目）

- `AZURE_SUBSCRIPTION_ID` - 在项目 **概览** 页面的 **项目详细信息** 中查看。

- `AZURE_AI_PROJECT_NAME` - 查看项目 **概览** 页面顶部的项目名称。

- `AZURE_OPENAI_SERVICE` - 在 **概览** 页面的 **Included capabilities** 选项卡中找到 **Azure OpenAI Service**。

### 管理中心

- `AZURE_OPENAI_RESOURCE_GROUP` - 转到 **管理中心** 的 **概览** 页面上的 **项目属性**。

- `GLOBAL_LLM_SERVICE` - 在 **已连接资源** 下，找到 **Azure AI Services** 的连接名称。如果未列出，请在 Azure 门户中查看你的资源组下的 AI Services 资源名称。

### 模型 + 端点 页面

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - 选择你的嵌入模型（例如 `text-embedding-ada-002`）并从模型详细信息中记下 **Deployment name**。

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - 选择你的聊天模型（例如 `gpt-4o-mini`）并从模型详细信息中记下 **Deployment name**。

### Azure 门户

- `AZURE_OPENAI_ENDPOINT` - 查找 **Azure AI services**，点击进入，然后转到 **Resource Management**、**Keys and Endpoint**，向下滚动到 “Azure OpenAI endpoints”，并复制标注为 “Language APIs” 的端点。

- `AZURE_OPENAI_API_KEY` - 在同一屏幕上，复制 KEY 1 或 KEY 2。

- `AZURE_SEARCH_SERVICE_ENDPOINT` - 找到你的 **Azure AI Search** 资源，点击它，并查看 **概览**。

- `AZURE_SEARCH_API_KEY` - 然后转到 **设置**，再转到 **Keys**，复制主或次管理员密钥。

### 外部网页

- `AZURE_OPENAI_API_VERSION` - 访问 [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) 页面下的 **Latest GA API release** 一节。

### 设置无密钥身份验证

我们将使用与 Azure OpenAI 的无密钥连接，而非硬编码凭据。为此，我们将导入 `DefaultAzureCredential`，并在稍后调用 `DefaultAzureCredential` 函数以获取凭据。

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## 卡在某处了吗?
如果在运行此设置时遇到任何问题，请加入我们的 <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI 社区 Discord</a> 或 <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">创建一个问题</a>。

## 下一课

你现在已经可以运行本课程的代码了。祝你在 AI 代理的世界中学习愉快并收获更多！

[AI 代理介绍与用例](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免责声明：
本文件已使用 AI 翻译服务 Co-op Translator（https://github.com/Azure/co-op-translator）进行翻译。尽管我们力求准确，但请注意，自动翻译可能包含错误或不准确之处。原始文档的原文应被视为权威来源。对于关键信息，建议采用专业人工翻译。我们不对因使用本翻译而产生的任何误解或错误解释承担责任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->