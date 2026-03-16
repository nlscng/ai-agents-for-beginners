# AGENTS.md

## プロジェクト概要

このリポジトリは「初心者向けAIエージェント」— AIエージェントを構築するために必要なすべてを学べる包括的な教育コースを収録しています。コースは15以上のレッスンで構成され、基礎、設計パターン、フレームワーク、実運用展開までをカバーします。

**主要技術：**
- Python 3.12以上
- インタラクティブ学習用のJupyterノートブック
- AIフレームワーク：Semantic Kernel、AutoGen、Microsoft Agent Framework (MAF)
- Azure AIサービス：Microsoft Foundry、Azure AI Agent Service
- GitHub Models Marketplace（無料ティアあり）

**アーキテクチャ：**
- レッスン単位の構成（00-15+ ディレクトリ）
- 各レッスンには：READMEドキュメント、コードサンプル（Jupyterノートブック）、画像を含む
- 自動翻訳システムによる多言語対応
- 各レッスンに複数フレームワークオプションあり（Semantic Kernel、AutoGen、Azure AI Agent Service）

## セットアップコマンド

### 前提条件
- Python 3.12以上
- GitHubアカウント（GitHub Models利用時、無料ティア）
- Azureサブスクリプション（任意、Azure AIサービス用）

### 初期セットアップ

1. **リポジトリをクローンまたはフォーク：**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # または
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Python仮想環境を作成・有効化：**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Windowsでは: venv\Scripts\activate
   ```

3. **依存関係をインストール：**
   ```bash
   pip install -r requirements.txt
   ```

4. **環境変数を設定：**
   ```bash
   cp .env.example .env
   # APIキーとエンドポイントを含む.envファイルを編集してください
   ```

### 必須環境変数

**GitHub Models（無料版）用:**
- `GITHUB_TOKEN` - GitHubの個人アクセストークン

**Azure AIサービス用（任意）：**
- `PROJECT_ENDPOINT` - Microsoft Foundryプロジェクトエンドポイント
- `AZURE_OPENAI_API_KEY` - Azure OpenAI APIキー
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAIエンドポイントURL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - チャットモデルの展開名
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - 埋め込み用展開名
- その他、.env.example に示されたAzure設定

## 開発ワークフロー

### Jupyterノートブックの実行

各レッスンには複数のフレームワーク用ノートブックがあります：

1. **Jupyterを起動：**
   ```bash
   jupyter notebook
   ```

2. **レッスンのディレクトリに移動**（例：`01-intro-to-ai-agents/code_samples/`）

3. **ノートブックを開いて実行：**
   - `*-semantic-kernel.ipynb` - Semantic Kernelフレームワーク使用
   - `*-autogen.ipynb` - AutoGenフレームワーク使用
   - `*-python-agent-framework.ipynb` - Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Azure AI Agent Service使用

### フレームワーク別の作業方法

**Semantic Kernel + GitHub Models:**
- GitHubアカウントで無料利用可能
- 学習や試験に最適
- ファイルパターン：`*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- GitHubアカウントで無料利用可能
- マルチエージェントオーケストレーション対応
- ファイルパターン：`*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Microsoftの最新フレームワーク
- Pythonと.NET版あり
- ファイルパターン：`*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Azureサブスクリプション必要
- 実運用対応機能あり
- ファイルパターン：`*-azureaiagent.ipynb`

## テスト手順

このリポジトリは学習用のコードサンプル集であり、生産向けの自動テストはありません。セットアップと変更を検証するには：

### 手動テスト

1. **Python環境の動作確認：**
   ```bash
   python --version  # 3.12以上である必要があります
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **ノートブックの実行テスト：**
   ```bash
   # ノートブックをスクリプトに変換して実行する（テストのインポート）
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **環境変数の確認：**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### 個別ノートブックの実行

Jupyterでノートブックを開き、セルを順に実行してください。各ノートブックは自己完結型で以下を含みます：
- インポート文
- 設定読み込み
- エージェント実装例
- マークダウンセル内の期待される出力

## コードスタイル

### Pythonの規約

- **Pythonバージョン**: 3.12以上
- **コードスタイル**: 標準のPEP 8に準拠
- **ノートブック**: 概念説明には明確なマークダウンセルを使用
- **インポート**: 標準ライブラリ、サードパーティ、ローカルを分けてグループ化

### Jupyterノートブックの規約

- コードセル前に説明用のマークダウンセルを含める
- 出力例をノートブック内に記載
- 概念に合った明確な変数名を使う
- ノートブックの実行順序は直線的に（セル1 → 2 → 3…）

### ファイル構成

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

## ビルドとデプロイ

### ドキュメントのビルド

このリポジトリはMarkdownでドキュメントを管理：
- 各レッスンフォルダのREADME.mdファイル
- リポジトリルートのメインREADME.md
- GitHub Actionsによる自動翻訳システム

### CI/CDパイプライン

`.github/workflows/`に配置：

1. **co-op-translator.yml** - 50以上の言語への自動翻訳
2. **welcome-issue.yml** - 新規Issue作成者への挨拶
3. **welcome-pr.yml** - 新規プルリクエスト作成者への挨拶

### デプロイ

教育用リポジトリのため、展開プロセスはありません。ユーザーは：
1. フォークまたはクローン
2. ローカルもしくはGitHub Codespacesでノートブックを実行
3. 例を修正・試しながら学習

## プルリクエストガイドライン

### 提出前に

1. **変更をテスト：**
   - 関連ノートブックを最後まで実行
   - 全セルがエラーなく動作するか確認
   - 出力が期待通りかチェック

2. **ドキュメントの更新：**
   - 新概念追加時はREADME.mdを更新
   - 複雑なコードにコメントを追加
   - マークダウンセルで目的を明確に説明

3. **ファイル変更：**
   - `.env`ファイルはコミット禁止（`.env.example`を利用）
   - `venv/`や`__pycache__/`ディレクトリのコミット禁止
   - 概念説明に必要なノートブックの出力は保持
   - 一時ファイルやバックアップノートブック（`*-backup.ipynb`）は削除

### PRタイトルの書式

説明的なタイトルを使用：
- `[Lesson-XX] <概念> の新しい例を追加`
- `[Fix] lesson-XX READMEの誤字修正`
- `[Update] lesson-XXのコードサンプル改善`
- `[Docs] セットアップ手順の更新`

### 必須チェック

- ノートブックはエラーなく実行できること
- READMEはわかりやすく正確であること
- 既存のコードパターンに従うこと
- 他のレッスンとの整合性を保つこと

## 追加の注意事項

### よくある問題点

1. **Pythonバージョンの不一致：**
   - Python 3.12以上を必ず使用する
   - 旧バージョンでは一部パッケージが動かない場合がある
   - `python3 -m venv` で明示的にバージョン指定

2. **環境変数：**
   - いつも`.env.example`から`.env`を作成
   - `.env`はコミットしない（`.gitignore`に設定済み）
   - GitHubトークンには必要な権限を付与

3. **パッケージの競合：**
   - 新規の仮想環境を使うこと
   - 個別インストールではなく`requirements.txt`からまとめてインストール
   - ノートブックのマークダウンセルに追加パッケージの記載がある場合あり

4. **Azureサービス：**
   - Azure AIサービスの利用は有効なサブスクリプションが必要
   - 一部機能はリージョン限定の場合あり
   - GitHub Modelsは無料ティアの制限がある

### 学習の流れ

推奨順は以下の通り：
1. **00-course-setup** - 環境セットアップから開始
2. **01-intro-to-ai-agents** - AIエージェントの基礎を理解
3. **02-explore-agentic-frameworks** - フレームワークの種類を学ぶ
4. **03-agentic-design-patterns** - 主要設計パターンの習得
5. 番号順にレッスンを進める

### フレームワークの選択

目的別に選択：
- **学習・プロトタイプ**：Semantic Kernel + GitHub Models（無料）
- **マルチエージェント**：AutoGen
- **最新機能**：Microsoft Agent Framework (MAF)
- **本番展開**：Azure AI Agent Service

### ヘルプを得るには

- [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)に参加
- 各レッスンのREADMEで具体的なガイダンスを確認
- メインの[README.md](./README.md)でコース概要を見る
- 詳細セットアップは[00-course-setup/README.md](./00-course-setup/README.md)を参照

### 貢献について

オープンな教育プロジェクトです。貢献歓迎：
- コード例の改善
- 誤字脱字の修正
- コメント追加による明確化
- 新レッスンテーマの提案
- 追加言語への翻訳

現在の課題は[GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues)で確認可能。

## プロジェクト固有のコンテキスト

### 多言語対応

自動翻訳システムを利用：
- 50以上の言語をサポート
- `/translations/<lang-code>/` ディレクトリに翻訳ファイル
- GitHub Actionsで翻訳更新を管理
- ソースファイルは英語でリポジトリ直下に配置

### レッスン構成

すべてのレッスンは以下のパターンで構成：
1. 動画サムネイルとリンク
2. テキストベースのレッスンコンテンツ（README.md）
3. 複数フレームワークのコードサンプル
4. 学習目標と前提条件の記載
5. 追加学習リソースへのリンク

### コードサンプルの命名規則

形式：`<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - レッスン4、Semantic Kernel
- `07-autogen.ipynb` - レッスン7、AutoGen
- `14-python-agent-framework.ipynb` - レッスン14、MAF Python版
- `14-dotnet-agent-framework.ipynb` - レッスン14、MAF .NET版

### 特殊ディレクトリ

- `translated_images/` - 翻訳向けローカライズ画像
- `images/` - 英語コンテンツ用オリジナル画像
- `.devcontainer/` - VS Code開発コンテナ設定
- `.github/` - GitHub Actions関連ワークフローとテンプレート

### 依存関係

`requirements.txt`の主なパッケージ：
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGenフレームワーク
- `semantic-kernel` - Semantic Kernelフレームワーク
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Azure AIサービス
- `azure-search-documents` - Azure AI Search連携
- `chromadb` - RAG例のベクターデータベース
- `chainlit` - チャットUIフレームワーク
- `browser_use` - エージェント用ブラウザ自動化
- `mcp[cli]` - モデルコンテキストプロトコル対応
- `mem0ai` - エージェント用メモリ管理

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責事項**：  
本書類はAI翻訳サービス[Co-op Translator](https://github.com/Azure/co-op-translator)を使用して翻訳されました。正確性の向上に努めておりますが、自動翻訳には誤りや不正確な箇所が含まれる場合があります。原文（原言語版）が正式な情報源として優先されます。重要な情報については専門の人間による翻訳を推奨します。本翻訳の使用により生じたいかなる誤解や解釈の相違についても、一切の責任を負いかねますのでご了承ください。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->