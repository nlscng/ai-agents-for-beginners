[![良いAIエージェントの設計方法](../../../translated_images/ja/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(上の画像をクリックすると、このレッスンの動画をご覧いただけます)_

# ツール使用デザインパターン

ツールは、AIエージェントがより広範な能力を持つことを可能にするため、興味深いものです。エージェントが実行できるアクションが限られている代わりに、ツールを追加することでエージェントはいまや幅広いアクションを実行できます。この章では、AIエージェントが特定のツールを使って目標を達成する方法を説明するツール使用デザインパターンについて見ていきます。

## はじめに

このレッスンでは、以下の質問に答えようとしています：

- ツール使用デザインパターンとは何ですか？
- どのようなユースケースに適用できますか？
- デザインパターンを実装するために必要な要素／構成ブロックは何ですか？
- 信頼できるAIエージェントを構築する際、ツール使用デザインパターンを使用するときの特別な考慮事項は何ですか？

## 学習目標

このレッスンを修了した後、あなたは以下のことができるようになります：

- ツール使用デザインパターンとその目的を定義できる
- ツール使用デザインパターンが適用できるユースケースを特定できる
- デザインパターンを実装するために必要な主要な要素を理解できる
- このデザインパターンを使うAIエージェントの信頼性を確保するための考慮事項を認識できる

## ツール使用デザインパターンとは何ですか？

**ツール使用デザインパターン**は、LLMに外部ツールと連携して特定の目標を達成する能力を持たせることに重点を置いています。ツールは、エージェントがアクションを実行するために呼び出せるコードです。ツールは、計算機のような単純な関数であったり、株価照会や天気予報など第三者サービスへのAPI呼び出しであったりします。AIエージェントの文脈では、ツールは**モデル生成の関数呼び出し**に応じてエージェントが実行するために設計されています。

## どのようなユースケースに適用できますか？

AIエージェントはツールを活用して複雑なタスクを完了したり、情報を取得したり、意思決定を行ったりできます。ツール使用デザインパターンは、データベース、ウェブサービス、コードインタープリターなど外部システムと動的に連携する必要があるシナリオでよく利用されます。この能力は以下を含む様々なユースケースに役立ちます：

- **動的情報取得:** エージェントが外部APIやデータベースに問い合わせて最新のデータを取得（例：SQLiteデータベースからのデータ分析、株価や天気情報の取得）。
- **コード実行と解釈:** 数学的問題の解決、レポート作成、シミュレーションのためにコードやスクリプトを実行。
- **ワークフロー自動化:** タスクスケジューラ、メールサービス、データパイプラインなどのツールを統合し、繰り返しや多段階のワークフローを自動化。
- **カスタマーサポート:** CRMシステム、チケッティングプラットフォーム、ナレッジベースとやり取りしてユーザーの問い合わせを解決。
- **コンテンツ生成と編集:** 文法チェック、要約、コンテンツ安全評価などのツールを活用してコンテンツ作成を支援。

## ツール使用デザインパターンを実装するために必要な要素／構成ブロックは何ですか？

これらの構成ブロックにより、AIエージェントは幅広いタスクを実行できます。ツール使用デザインパターンを実装するために必要な主要な要素を見てみましょう：

- **関数／ツールスキーマ**：利用可能なツールの詳細定義（関数名、目的、必要なパラメーター、期待される出力）です。これによりLLMは、どのツールが利用可能でどのように有効なリクエストを構築するかを理解できます。

- **関数実行ロジック**：ユーザーの意図や会話コンテキストに基づき、ツールの呼び出し方法とタイミングを管理します。プランナーモジュール、ルーティング機構、条件付きフローなど、動的にツール利用を決定するものが含まれます。

- **メッセージ処理システム**：ユーザー入力、LLM応答、ツール呼び出し、ツール出力の会話フローを管理するコンポーネント。

- **ツール統合フレームワーク**：単純な関数や複雑な外部サービスのいずれであっても、エージェントとツールを接続するインフラストラクチャ。

- **エラー処理と検証**：ツールの実行失敗を処理し、パラメーターの検証や予期しない応答を管理する仕組み。

- **状態管理**：会話コンテキスト、過去のツールインタラクション、永続データを追跡し、複数ターンの対話で一貫性を保証。

次に、関数／ツール呼び出しについて詳細を見ていきましょう。

### 関数／ツール呼び出し

関数呼び出しは、LLM（大規模言語モデル）にツールと連携する方法を提供する主要な手段です。「関数」と「ツール」はしばしば同義で使われます。なぜなら、「関数」（再利用可能なコードのブロック）はエージェントがタスクを実行するための「ツール」だからです。関数のコードを呼び出すために、LLMはユーザーのリクエストを関数の説明と比較します。そのために、利用可能なすべての関数の説明を含むスキーマをLLMに送ります。LLMはタスクに最も適切な関数を選択し、その名前と引数を返します。選択された関数が呼び出され、その応答がLLMに戻され、LLMはそれを使ってユーザーのリクエストに応答します。

開発者がエージェントのために関数呼び出しを実装するには、以下が必要です：

1. 関数呼び出しをサポートするLLMモデル
2. 関数説明を含むスキーマ
3. 各関数の実装コード

都市の現在時刻を取得する例を使って説明します：

1. **関数呼び出しをサポートするLLMを初期化：**

    関数呼び出しをサポートするモデルを使用しているか確認することが重要です。 <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> は関数呼び出しをサポートしています。まずAzure OpenAIクライアントを初期化します。

    ```python
    # Azure OpenAI クライアントを初期化する
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **関数スキーマを作成：**

    次に、関数名、関数の説明、パラメーター名および説明を含むJSONスキーマを定義します。
    このスキーマを先ほど作成したクライアントに渡し、ユーザーの「サンフランシスコの時間を調べる」リクエストと共に送信します。重要なのは、**ツール呼び出し**が返されることであり、質問の最終回答ではありません。冒頭で述べたように、LLMはタスクのために選択した関数名とその引数を返します。

    ```python
    # モデルが読むための関数の説明
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # 初期ユーザーメッセージ
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # 最初のAPIコール：モデルに関数の使用を依頼
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # モデルの応答を処理する
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **タスクを実行する関数コード：**

    LLMがどの関数を実行するか選択したので、そのタスクを実行するコードを実装し呼び出す必要があります。
    Pythonで現在時刻を取得するコードを実装します。また、レスポンスメッセージから関数名と引数を抽出して最終結果を取得するコードも書きます。

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # 関数呼び出しを処理する
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # 2回目のAPI呼び出し：モデルから最終応答を取得する
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

関数呼び出しは、ほとんど（あるいはすべての）エージェントのツール使用デザインの中心です。しかし、ゼロから実装するのは時に困難な場合があります。
[レッスン2](../../../02-explore-agentic-frameworks)で学んだように、エージェントフレームワークはツール使用のための事前構築済み構成ブロックを提供しています。

## エージェントフレームワークを使ったツール使用の例

異なるエージェントフレームワークを使用してツール使用デザインパターンを実装する例をいくつか紹介します：

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> は、.NET、Python、Java開発者向けのオープンソースAIフレームワークで、大規模言語モデル（LLM）と連携します。関数の説明とパラメーターを自動的にモデルに伝える<a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">シリアライズ</a>を通じて関数呼び出しのプロセスを簡素化し、モデルとコード間のやりとりも扱います。また、Semantic Kernelのようなエージェントフレームワークを使うもう一つの利点は、<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">ファイル検索</a>や<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">コードインタープリター</a>などの事前構築済みツールにアクセスできることです。

以下の図はSemantic Kernelによる関数呼び出しのプロセスを示しています：

![function calling](../../../translated_images/ja/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernelでは関数／ツールは<a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">プラグイン</a>と呼ばれます。先ほどの`get_current_time`関数を、関数を含むクラスに変えてプラグインに変換できます。さらに`kernel_function`デコレーターをインポートして関数説明を渡します。GetCurrentTimePluginでカーネルを作成すると、カーネルは関数とパラメーターを自動的にシリアライズし、LLMに送信するスキーマを作成します。

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# カーネルを作成する
kernel = Kernel()

# プラグインを作成する
get_current_time_plugin = GetCurrentTimePlugin(location)

# プラグインをカーネルに追加する
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> は、開発者が基盤となる計算・ストレージリソースを管理せずに、高品質で拡張性のあるAIエージェントを安全に構築、デプロイ、スケールできるよう設計された新しいエージェントフレームワークです。特に企業向けアプリケーションに有用で、企業レベルのセキュリティを備えた完全マネージドサービスです。

LLM APIを直接使う場合と比べてAzure AI Agent Serviceが提供する利点には以下が含まれます：

- 自動ツール呼び出し — ツール呼び出しの解析、ツールの呼び出し、応答処理が不要になり、すべてサーバー側で行われる
- セキュアに管理されたデータ — 独自に会話状態を管理する代わりに、スレッドに情報をすべて格納可能
- 利用可能なツール群 — Bing、Azure AI Search、Azure Functionsなどのデータソースと連携するツールを利用可能

Azure AI Agent Serviceのツールは以下の2つのカテゴリに分かれます：

1. ナレッジツール：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing検索によるグラウンディング</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">ファイル検索</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. アクションツール：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">関数呼び出し</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">コードインタープリター</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI定義済みツール</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

エージェントサービスはこれらのツールを`toolset`としてまとめて使うことができます。また、特定の会話履歴を管理する`threads`も利用します。

あなたがContoso社の営業担当者で、販売データに関する質問に答えられる会話型エージェントを開発したいと想像してください。

次の画像は、Azure AI Agent Serviceで販売データを分析する方法の例を示しています：

![Agentic Service In Action](../../../translated_images/ja/agent-service-in-action.34fb465c9a84659e.webp)

これらのツールをサービスで使うには、クライアントを作成しツールやツールセットを定義します。実際の実装例を以下のPythonコードで示します。LLMはツールセットを見て、ユーザー作成の関数`fetch_sales_data_using_sqlite_query`を使うか、組み込みのコードインタープリターを使うか決定します。

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_functions.py ファイルにある fetch_sales_data_using_sqlite_query 関数。
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# ツールセットを初期化する
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query 関数で関数呼び出しエージェントを初期化し、ツールセットに追加する
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# コードインタープリター・ツールを初期化し、ツールセットに追加する。
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## 信頼できるAIエージェントを構築するためにツール使用デザインパターンにおける特別な考慮事項は何ですか？

LLMが動的に生成するSQLに関してよくある懸念はセキュリティで、特にSQLインジェクションやデータベースの破壊や改ざんといった悪意ある行為のリスクです。これらの懸念は適切なデータベースアクセス権限の設定によって効果的に軽減できます。ほとんどのデータベースでは、データベースを読み取り専用に設定することが関係します。PostgreSQLやAzure SQLのようなデータベースサービスの場合、アプリには読み取り専用（SELECT）ロールを割り当てるべきです。

アプリを安全な環境で実行することも保護を強化します。企業のシナリオでは、データは通常、運用システムから抽出・変換されて、読み取り専用のデータベースまたはデータウェアハウスにユーザーフレンドリーなスキーマで格納されます。このアプローチにより、データは安全で、性能とアクセス性が最適化され、アプリは制限された読み取り専用アクセス権しか持ちません。

## サンプルコード
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## ツールの使用デザインパターンについてさらに質問がありますか？

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)に参加して、他の学習者と交流したり、オフィスアワーに参加してAIエージェントに関する質問を解決しましょう。

## 追加リソース

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service ワークショップ</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer マルチエージェント ワークショップ</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel 関数呼び出しチュートリアル</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel コードインタープリター</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogenツール</a>

## 前のレッスン

[エージェントデザインパターンの理解](../03-agentic-design-patterns/README.md)

## 次のレッスン

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責事項**：  
本書類はAI翻訳サービス「Co-op Translator」（https://github.com/Azure/co-op-translator）を使用して翻訳されました。正確性を期しておりますが、自動翻訳には誤りや不正確な箇所が含まれる可能性があります。原文の言語による文書を正式な情報源としてご参考ください。重要な情報については、専門の人間による翻訳を推奨いたします。本翻訳の使用によって生じたいかなる誤解や解釈の相違についても、一切の責任を負いかねます。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->