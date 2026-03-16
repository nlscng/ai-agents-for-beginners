# コースの設定

## 導入

このレッスンでは、本コースのコードサンプルを実行する方法を説明します。

## 他の学習者に参加してサポートを得る

リポジトリをクローンする前に、[AI Agents For Beginners Discord チャンネル](https://aka.ms/ai-agents/discord) に参加して、セットアップのサポートやコースに関する質問、他の学習者との交流を行ってください。

## このリポジトリをクローンまたはフォークする

まず、GitHub リポジトリをクローンまたはフォークしてください。これにより、コース教材の自分用のバージョンが作成され、コードを実行、テスト、調整できるようになります！

これは <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">リポジトリをフォークする</a> リンクをクリックすることで行えます

次のリンクに、あなた自身のフォークされたこのコースのバージョンが表示されているはずです:

![フォークしたリポジトリ](../../../translated_images/ja/forked-repo.33f27ca1901baa6a.webp)

### 浅いクローン（ワークショップ / Codespaces に推奨）

  >フルの履歴とすべてのファイルをダウンロードすると、リポジトリ全体は大きくなる場合があります（約3 GB）。ワークショップに参加するだけ、または必要なレッスンフォルダが数個だけの場合、浅いクローン（またはスパースクローン）は履歴を切り詰めたり blob をスキップしたりすることで、ほとんどのダウンロードを回避できます。

#### クイック浅いクローン — 最小限の履歴、すべてのファイル

以下のコマンド内の `<your-username>` を、あなたのフォークの URL（または必要に応じて上流の URL）に置き換えてください。

最新のコミット履歴のみをクローンする場合（ダウンロードが小さい）:

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

特定のブランチをクローンするには:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### 部分（スパース）クローン — 最小限の blob + 選択したフォルダのみ

これは部分クローンと sparse-checkout を使用します（Git 2.25+ が必要で、部分クローンをサポートする最新の Git を推奨します）:

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

リポジトリフォルダに移動します:

```bash|powershell
cd ai-agents-for-beginners
```

次に、必要なフォルダを指定します（以下の例は2つのフォルダを示しています）:

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

クローンしてファイルを確認した後、ファイルのみが必要でディスク領域を解放したい場合（git 履歴は不要）、リポジトリのメタデータを削除してください（💀取り消し不可 — すべての Git 機能を失います: コミット、プル、プッシュ、履歴へのアクセスはできなくなります）。

```bash
# zsh/bash
rm -rf .git
```

```powershell
# パワーシェル
Remove-Item -Recurse -Force .git
```

#### GitHub Codespaces の使用（ローカルでの大きなダウンロードを避けるために推奨）

- このリポジトリの新しい Codespace を [GitHub の UI](https://github.com/codespaces) から作成します。  

- 新しく作成した Codespace のターミナルで、上記の浅い/スパースクローンのコマンドのいずれかを実行して、必要なレッスンフォルダだけを Codespace ワークスペースに取り込みます。
- 任意: Codespaces 内でクローンした後、追加の空き容量を確保するために .git を削除します（上記の削除コマンドを参照）。
- 注意: クローンを追加で行わずにリポジトリを直接 Codespaces で開くことを好む場合でも、Codespaces は devcontainer 環境を構築し、必要以上のプロビジョニングが行われる可能性があります。新しい Codespace 内で浅いコピーをクローンすることで、ディスク使用量をより制御できます。

#### ヒント

- 編集/コミットしたい場合は、常にクローン URL を自分のフォークに置き換えてください。
- 後でさらに履歴やファイルが必要になった場合は、fetch するか、sparse-checkout を調整して追加のフォルダを含めることができます。

## コードの実行

このコースでは、AI エージェントを構築する実践的な経験を得るために実行できる一連の Jupyter Notebook を提供します。

コードサンプルは次のいずれかを使用します:

**GitHub アカウントが必要 - 無料**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace。ラベル: (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace。ラベル: (autogen.ipynb)

**Azure サブスクリプションが必要**:
3) Azure AI Foundry + Azure AI Agent Service。ラベル: (azureaiagent.ipynb)

すべてのタイプの例を試してみて、どれが自分に最適かを確認することをお勧めします。

どのオプションを選ぶかにより、以下で従う必要のあるセットアップ手順が決まります:

## 要件

- Python 3.12+
  - **注意**: Python 3.12 がインストールされていない場合は、必ずインストールしてください。その後、python3.12 を使って venv を作成し、requirements.txt ファイルから正しいバージョンがインストールされるようにしてください。
  
    >例

    Python の venv ディレクトリを作成:

    ```bash|powershell
    python -m venv venv
    ```

    次に、venv 環境を有効化します:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: .NET を使用するサンプルコードのために、[.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) 以降をインストールしていることを確認してください。その後、インストールされている .NET SDK のバージョンを確認します:

    ```bash|powershell
    dotnet --list-sdks
    ```

- GitHub アカウント - GitHub Models Marketplace へのアクセス用
- Azure サブスクリプション - Microsoft Foundry へのアクセス用
- Microsoft Foundry アカウント - Azure AI Agent Service へのアクセス用

このリポジトリのルートには、コードサンプルを実行するために必要なすべての Python パッケージを含む `requirements.txt` ファイルが含まれています。

リポジトリのルートでターミナルから次のコマンドを実行してインストールできます:

```bash|powershell
pip install -r requirements.txt
```

競合や問題を回避するために、Python 仮想環境の作成を推奨します。

## VSCode のセットアップ

VSCode で正しいバージョンの Python を使用していることを確認してください。

![画像](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## GitHub Models を使用するサンプルのセットアップ

### ステップ 1: GitHub Personal Access Token (PAT) を取得する

このコースでは GitHub Models Marketplace を活用し、AI エージェントを構築するために使用する大規模言語モデル（LLM）への無料アクセスを提供します。

GitHub Models を使用するには、[GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) を作成する必要があります。

これは GitHub アカウントの <a href="https://github.com/settings/personal-access-tokens" target="_blank">Personal Access Tokens 設定</a> で行えます。

トークンを作成する際は、[最小権限の原則](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) に従ってください。これは、トークンにこのコースのコードサンプルを実行するために必要な権限のみを付与することを意味します。

1. 画面左側の **開発者設定** に移動し、`Fine-grained tokens` オプションを選択します。

   ![開発者設定](../../../translated_images/ja/profile_developer_settings.410a859fe749c755.webp)

   次に `Generate new token` を選択します。

   ![トークンを生成](../../../translated_images/ja/fga_new_token.1c1a234afe202ab3.webp)

2. トークンの目的を反映した識別しやすい説明的な名前を入力します。

    🔐 トークン有効期限の推奨

    推奨期間: 30 日
    より安全にするために、7 日など短い期間を選択できます 🛡️
    学習の勢いが高いうちにコースを完了する目標を設定するのに良い方法です 🚀。

    ![トークン名と有効期限](../../../translated_images/ja/token-name-expiry-date.a095fb0de6386864.webp)

3. トークンのスコープをこのリポジトリのフォークに制限します。

    ![スコープをフォークリポジトリに制限](../../../translated_images/ja/token_repository_limit.924ade5e11d9d8bb.webp)

4. トークンの権限を制限します: **Permissions** の下で **Account** タブをクリックし、"+ Add permissions" ボタンをクリックします。ドロップダウンが表示されます。**Models** を検索して、そのチェックボックスをオンにしてください。

    ![モデルの権限を追加](../../../translated_images/ja/add_models_permissions.c0c44ed8b40fc143.webp)

5. トークンを生成する前に、必要な権限を確認してください。 ![権限を確認](../../../translated_images/ja/verify_permissions.06bd9e43987a8b21.webp)

6. トークンを生成する前に、パスワードマネージャのボールトなど安全な場所にトークンを保存する準備ができていることを確認してください。生成後は再表示されません。 ![トークンを安全に保存](../../../translated_images/ja/store_token_securely.08ee2274c6ad6caf.webp)

作成した新しいトークンをコピーしてください。これをこのコースに含まれている `.env` ファイルに追加します。

### ステップ 2: `.env` ファイルを作成する

`.env` ファイルを作成するには、ターミナルで次のコマンドを実行してください。

```bash
# zshまたはbash
cp .env.example .env
```

```powershell
# パワーシェル
Copy-Item .env.example .env
```

これにより example ファイルがコピーされ、ディレクトリに `.env` が作成され、環境変数の値を入力する場所が作成されます。

トークンをコピーしたら、お好みのテキストエディタで `.env` ファイルを開き、`GITHUB_TOKEN` フィールドにトークンを貼り付けます。

![GitHub トークン欄](../../../translated_images/ja/github_token_field.20491ed3224b5f4a.webp)

これで、このコースのコードサンプルを実行できるはずです。

## Microsoft Foundry と Azure AI Agent Service を使用するサンプルのセットアップ

### ステップ 1: Azure プロジェクトのエンドポイントを取得する

Azure AI Foundry でハブとプロジェクトを作成する手順は次を参照してください: [ハブリソースの概要](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

プロジェクトを作成したら、プロジェクトの接続文字列を取得する必要があります。

これは Microsoft Foundry ポータルのプロジェクトの **概要** ページで行えます。

![プロジェクト接続文字列](../../../translated_images/ja/project-endpoint.8cf04c9975bbfbf1.webp)

### ステップ 2: `.env` ファイルを作成する

`.env` ファイルを作成するには、ターミナルで次のコマンドを実行してください。

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# パワーシェル
Copy-Item .env.example .env
```

これにより example ファイルがコピーされ、ディレクトリに `.env` が作成され、環境変数の値を入力する場所が作成されます。

トークンをコピーしたら、お好みのテキストエディタで `.env` ファイルを開き、`PROJECT_ENDPOINT` フィールドにトークンを貼り付けます。

### ステップ 3: Azure にサインインする

セキュリティのベストプラクティスとして、Microsoft Entra ID を使用して Azure OpenAI に認証するために、[keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) を使用します。 

次に、ターミナルを開き `az login --use-device-code` を実行して Azure アカウントにサインインしてください。

ログインしたら、ターミナルでサブスクリプションを選択してください。

## 追加の環境変数 - Azure Search と Azure OpenAI

Agentic RAG レッスン（レッスン 5）では、Azure Search と Azure OpenAI を使用するサンプルがあります。

これらのサンプルを実行する場合は、以下の環境変数を `.env` ファイルに追加する必要があります:

### 概要ページ（プロジェクト）

- `AZURE_SUBSCRIPTION_ID` - プロジェクトの **概要** ページにある **プロジェクトの詳細** を確認してください。

- `AZURE_AI_PROJECT_NAME` - プロジェクトの **概要** ページ上部を確認してください。

- `AZURE_OPENAI_SERVICE` - **概要** ページの **Included capabilities** タブで **Azure OpenAI Service** を探してください。

### 管理センター

- `AZURE_OPENAI_RESOURCE_GROUP` - **Management Center** の **概要** ページにある **Project properties** に移動してください。

- `GLOBAL_LLM_SERVICE` - **Connected resources** の下で **Azure AI Services** の接続名を見つけてください。リストにない場合は、リソースグループ内の Azure ポータルで AI Services リソース名を確認してください。

### モデル + エンドポイントページ

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - 埋め込みモデル（例: `text-embedding-ada-002`）を選択し、モデルの詳細から **Deployment name** を確認してください。

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - チャットモデル（例: `gpt-4o-mini`）を選択し、モデルの詳細から **Deployment name** を確認してください。

### Azure ポータル

- `AZURE_OPENAI_ENDPOINT` - **Azure AI services** を探してクリックし、**Resource Management**、**Keys and Endpoint** に移動し、「Azure OpenAI endpoints」までスクロールして「Language APIs」と書かれているエンドポイントをコピーしてください。

- `AZURE_OPENAI_API_KEY` - 同じ画面から KEY 1 または KEY 2 をコピーしてください。

- `AZURE_SEARCH_SERVICE_ENDPOINT` - **Azure AI Search** リソースを見つけてクリックし、**概要** を確認してください。

- `AZURE_SEARCH_API_KEY` - 次に **Settings** → **Keys** に移動して、プライマリまたはセカンダリの管理キーをコピーしてください。

### 外部ウェブページ

- `AZURE_OPENAI_API_VERSION` - [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) ページの **Latest GA API release** を参照してください。

### キーなし認証のセットアップ

資格情報をハードコードする代わりに、Azure OpenAI ではキーなし接続を使用します。そのために `DefaultAzureCredential` をインポートし、後で `DefaultAzureCredential` 関数を呼び出して資格情報を取得します。

```python
# パイソン
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## どこかで詰まりましたか？
このセットアップの実行中に問題がある場合は、私たちの <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI コミュニティ Discord</a> に参加するか、<a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">Issue を作成する</a>。

## 次のレッスン

これでこのコースのコードを実行する準備が整いました。AI エージェントの世界についてさらに学ぶことを楽しんでください！ 

[AI エージェントの紹介とユースケース](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免責事項：
本書は AI 翻訳サービス「Co‑op Translator」（https://github.com/Azure/co-op-translator）を用いて翻訳されました。正確性の確保に努めていますが、自動翻訳には誤りや不正確な表現が含まれる可能性があります。原文（原言語で記載された文書）を権威ある出典として扱ってください。重要な情報については、専門の人間翻訳者による確認を推奨します。本翻訳の利用により生じた誤解や解釈の相違について、当方は一切の責任を負いません。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->