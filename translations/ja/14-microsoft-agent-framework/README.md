# Microsoft Agent Frameworkの探究

![Agent Framework](../../../translated_images/ja/lesson-14-thumbnail.90df0065b9d234ee.webp)

### はじめに

このレッスンの内容：

- Microsoft Agent Frameworkの理解：主な特徴と価値  
- Microsoft Agent Frameworkの主要な概念の探求
- MAFとSemantic KernelおよびAutoGenの比較：移行ガイド

## 学習目標

このレッスンを修了すると、以下がわかるようになります：

- Microsoft Agent Frameworkを使って本番対応のAIエージェントを構築する方法
- Microsoft Agent Frameworkのコア機能をエージェント利用ケースに適用する方法
- 既存のエージェントフレームワークやツールの移行および統合方法  

## コードサンプル

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) のコードサンプルはこのリポジトリ内の `xx-python-agent-framework` および `xx-dotnet-agent-framework` ファイルにあります。

## Microsoft Agent Frameworkの理解

![Framework Intro](../../../translated_images/ja/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) は、Semantic KernelおよびAutoGenの経験と知見を基に構築されています。生産環境と研究環境の両方で見られる様々なエージェント利用ケースに対応する柔軟性を提供しています：

- **逐次的エージェントオーケストレーション**：ステップバイステップのワークフローが必要なシナリオ。
- **並行オーケストレーション**：複数のエージェントが同時にタスクを完了する必要があるシナリオ。
- **グループチャットオーケストレーション**：エージェント同士が一つのタスクに協力して取り組むシナリオ。
- **ハンドオフオーケストレーション**：サブタスクが完了するごとにエージェントがタスクを引き継ぐシナリオ。
- **マグネティックオーケストレーション**：マネージャーエージェントがタスクリストを作成・修正し、サブエージェントの調整を行うシナリオ。

本番環境でAIエージェントを提供するため、MAFには以下の機能も含まれています：

- **オブザーバビリティ**：OpenTelemetryを使用し、ツール呼び出し、オーケストレーションステップ、推論フロー、Microsoft Foundryのダッシュボードでのパフォーマンス監視など、AIエージェントのあらゆるアクションの可観測性を提供。
- **セキュリティ**：Microsoft Foundry上でエージェントをネイティブにホスティングし、役割ベースアクセス制御、プライベートデータ処理、組み込みのコンテンツ安全対策を含むセキュリティ管理を実現。
- **耐久性**：エージェントスレッドやワークフローは一時停止、再開、エラーからの回復が可能で、長時間稼働プロセスをサポート。
- **制御**：ヒューマンインザループワークフローをサポートし、人間の承認が必要なタスクのマーク付けが可能。

また、Microsoft Agent Frameworkは相互運用性に焦点を当てています：

- **クラウド非依存** - エージェントはコンテナ、オンプレミス、複数の異なるクラウド上で動作可能。
- **プロバイダー非依存** - 好みのSDK（Azure OpenAIやOpenAIなど）を通じてエージェントを作成可能。
- **オープン標準の統合** - Agent-to-Agent(A2A)、Model Context Protocol(MCP)などのプロトコルを利用し、他のエージェントやツールの検出・利用が可能。
- **プラグインとコネクター** - Microsoft Fabric、SharePoint、Pinecone、Qdrantなどのデータ・メモリーサービスに接続可能。

これらの機能がMicrosoft Agent Frameworkの核となるコンセプトにどのように適用されているか見ていきましょう。

## Microsoft Agent Frameworkの主要概念

### エージェント

![Agent Framework](../../../translated_images/ja/agent-components.410a06daf87b4fef.webp)

**エージェントの作成**

エージェント作成は推論サービス（LLMプロバイダー）、AIエージェントが従う命令セット、そして割り当てられた `name` を定義して行います：

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

上記は `Azure OpenAI` を使用していますが、`Microsoft Foundry Agent Service` など様々なサービスでエージェント作成が可能です：

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAIの `Responses`、`ChatCompletion` API

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

あるいはA2Aプロトコルを用いたリモートエージェント：

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**エージェントの実行**

エージェントはストリーミング応答の有無に応じて、`.run` または `.run_stream` メソッドで実行します。

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

各エージェント実行時には、エージェントが使用する `max_tokens` や呼び出せる `tools`、さらには使用する `model` などパラメーターをカスタマイズするオプションがあります。

これはユーザーのタスク完了に特定のモデルやツールが必要な場合に有用です。

**ツール**

ツールはエージェント定義時にも：

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# ChatAgent を直接作成する場合

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

エージェント実行時にも定義可能です：

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # この実行のためだけに提供されたツール )
```

**エージェントスレッド**

エージェントスレッドは多ターン会話を扱うために使用します。スレッドは以下のいずれかで作成可能です：

- 時間を超えてスレッドを保存可能にする `get_new_thread()` を利用
- エージェント実行時に自動的にスレッドを作成し、実行中のみ有効なスレッドにする

スレッド作成コード例：

```python
# 新しいスレッドを作成します。
thread = agent.get_new_thread() # スレッドでエージェントを実行します。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

後で使用するためにスレッドをシリアライズして保存もできます：

```python
# 新しいスレッドを作成します。
thread = agent.get_new_thread() 

# スレッドでエージェントを実行します。

response = await agent.run("Hello, how are you?", thread=thread) 

# ストレージ用にスレッドをシリアライズします。

serialized_thread = await thread.serialize() 

# ストレージから読み込んだ後、スレッドの状態をデシリアライズします。

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**エージェントミドルウェア**

エージェントはツールやLLMと連携してユーザーのタスクを完了します。特定のシナリオではこれらのやり取りの途中で処理を実行したり追跡したいことがあります。エージェントミドルウェアはこれを以下で可能にします：

*関数ミドルウェア*

関数やツールを呼び出す際のエージェントとの間で処理を入れることができます。例えば関数呼び出し時にログ記録を行う用途で使われます。

下記のコードの `next` は、次のミドルウェアか実際の関数を呼び出すかを定義しています。

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # 前処理：関数実行前のログ
    print(f"[Function] Calling {context.function.name}")

    # 次のミドルウェアまたは関数の実行に進む
    await next(context)

    # 後処理：関数実行後のログ
    print(f"[Function] {context.function.name} completed")
```

*チャットミドルウェア*

エージェントとLLM間のリクエストのやり取り中に処理やログ記録を行うミドルウェアです。

AIサービスに送信される `messages` などの重要な情報が含まれます。

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # 前処理：AI呼び出し前のログ
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # 次のミドルウェアまたはAIサービスへ続行
    await next(context)

    # 後処理：AI応答後のログ
    print("[Chat] AI response received")

```

**エージェントメモリー**

「Agentic Memory」レッスンで説明した通り、メモリーはエージェントが異なるコンテクストで動作するための重要な要素です。MAFは以下の複数種類のメモリーを提供しています：

*インメモリストレージ*

アプリケーション実行中のスレッド内に格納されるメモリーです。

```python
# 新しいスレッドを作成します。
thread = agent.get_new_thread() # スレッドでエージェントを実行します。
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*永続メッセージ*

異なるセッション間で会話履歴を保存するためのメモリーです。`chat_message_store_factory` により定義します：

```python
from agent_framework import ChatMessageStore

# カスタムメッセージストアを作成する
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*動的メモリー*

エージェント実行前のコンテキストに追加されるメモリーです。mem0のような外部サービスで格納可能です：

```python
from agent_framework.mem0 import Mem0Provider

# 高度なメモリ機能のためにMem0を使用する
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**エージェントのオブザーバビリティ**

信頼性が高く保守可能なエージェントシステムを構築するにはオブザーバビリティが重要です。MAFはOpenTelemetryと統合し、トレーシングとメトリクスを提供します。

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # 何かをする
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### ワークフロー

MAFはタスクを完了するためのあらかじめ定義されたステップを持つワークフローを提供し、そのステップにAIエージェントをコンポーネントとして組み込めます。

ワークフローは制御フローを強化するための様々なコンポーネントから成り立ち、**マルチエージェントオーケストレーション**と**チェックポイント機能**により状態保存が可能です。

ワークフローの主要コンポーネントは：

**エグゼキューター**

エグゼキューターは入力メッセージを受け取り、割り当てられた処理を実行し、出力メッセージを生成します。これによりワークフローを大きなタスク完了に向けて進めます。エグゼキューターはAIエージェントかカスタムロジックのいずれかです。

**エッジ**

エッジはワークフロー内のメッセージの流れを定義します。具体的には：

*直接エッジ* - エグゼキューター間の単純な一対一接続：

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*条件付きエッジ* - 特定の条件が満たされた後にアクティブになります。例えばホテルの部屋が利用不可の場合、他の選択肢を提案するエグゼキューターを起動。

*スイッチケースエッジ* - 条件に基づき異なるエグゼキューターにメッセージをルーティング。例えば、優先アクセス権を持つ旅行客は別のワークフローでタスク処理される。

*ファンアウトエッジ* - 一つのメッセージを複数のターゲットに送信。

*ファンインエッジ* - 複数のエグゼキューターからのメッセージを集約し、一つのターゲットに送信。

**イベント**

ワークフローの可視化向上のため、MAFは実行中のイベントを内蔵しています：

- `WorkflowStartedEvent`  - ワークフロー実行開始
- `WorkflowOutputEvent` - ワークフローによる出力生成
- `WorkflowErrorEvent` - ワークフロー障害発生
- `ExecutorInvokeEvent`  - エグゼキューター処理開始
- `ExecutorCompleteEvent`  -  エグゼキューター処理完了
- `RequestInfoEvent` - リクエスト発行

## 他のフレームワーク（Semantic KernelおよびAutoGen）からの移行

### MAFとSemantic Kernelの違い

**簡易化されたエージェント作成**

Semantic Kernelはエージェント毎にKernelインスタンスの作成が必要でした。MAFは主要プロバイダー向けの拡張機能を使い、より簡素なアプローチを取っています。

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**エージェントスレッドの作成**

Semantic Kernelはスレッドを手動で作成する必要がありますが、MAFではエージェントに直接スレッドが割り当てられます。

```python
thread = agent.get_new_thread() # スレッドでエージェントを実行します。
```

**ツール登録**

Semantic KernelではツールはKernelに登録され、そのKernelをエージェントに渡します。MAFではツールはエージェント作成時に直接登録します。

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAFとAutoGenの違い

**Teams vs Workflows**

`Teams` はAutoGenにおけるイベントドリブンアクティビティの構造です。一方MAFはグラフベースのアーキテクチャでエグゼキューターへデータをルーティングする `Workflows` を使います。

**ツール作成**

AutoGenはエージェントが呼び出す関数をラップするために `FunctionTool` を使用します。MAFは @ai_function を使い、それに加え関数ごとにスキーマを自動推論します。

**エージェントの振る舞い**

AutoGenのエージェントはデフォルトでシングルターンですが、`max_tool_iterations` を高く設定した場合のみマルチターンとなります。MAFの `ChatAgent` はデフォルトでマルチターンで動作し、ユーザーのタスク完了までツール呼び出しを繰り返します。

## コードサンプル

Microsoft Agent Frameworkのコードサンプルはこのリポジトリ内の `xx-python-agent-framework` および `xx-dotnet-agent-framework` ファイルにあります。

## Microsoft Agent Frameworkについてさらに質問がありますか？

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) に参加して、他の学習者と交流したり、オフィスアワーに参加してAIエージェントに関する質問をしましょう。

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責事項**：  
本書類はAI翻訳サービス「Co-op Translator」（https://github.com/Azure/co-op-translator）を使用して翻訳されました。正確性を期しておりますが、自動翻訳には誤りや不正確な部分が含まれる可能性があります。原文が権威ある正式な情報源として扱われるべきです。重要な情報については、専門の人間による翻訳を推奨いたします。本翻訳の使用によって生じたいかなる誤解や解釈の相違についても、当方は一切責任を負いかねます。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->