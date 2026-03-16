[![AIエージェントフレームワークを探る](../../../translated_images/ja/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(上の画像をクリックするとこのレッスンのビデオを表示します)_

# AIエージェントフレームワークを探る

AIエージェントフレームワークは、AIエージェントの作成、デプロイ、および管理を簡素化するために設計されたソフトウェアプラットフォームです。これらのフレームワークは、開発者に事前構築されたコンポーネント、抽象化、およびツールを提供し、複雑なAIシステムの開発を効率化します。

これらのフレームワークは、AIエージェント開発における共通の課題に対して標準化されたアプローチを提供することで、開発者がアプリケーションの固有部分に集中できるようにします。これにより、AIシステムのスケーラビリティ、アクセス性、および効率性が向上します。

## はじめに

このレッスンでは以下を扱います:

- AIエージェントフレームワークとは何か、開発者はそれによって何を達成できるか？
- チームはこれらを使ってどのように迅速にプロトタイプを作成し、反復し、エージェントの機能を改善できるか？
- Microsoft の <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>、<a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>、および <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> によって作成されたフレームワークやツールの違いは何か？
- 既存の Azure エコシステムのツールを直接統合できるのか、それともスタンドアロンのソリューションが必要か？
- Azure AI Agents サービスとは何か、そしてそれはどのように役立つのか？

## 学習目標

このレッスンの目標は以下を理解することです:

- AI開発におけるAIエージェントフレームワークの役割。
- インテリジェントエージェントを構築するためにAIエージェントフレームワークを活用する方法。
- AIエージェントフレームワークによって可能になる主な機能。
- AutoGen、Semantic Kernel、および Azure AI Agent Service の違い。

## AIエージェントフレームワークとは何か、開発者は何ができるようになるか？

従来のAIフレームワークは、アプリにAIを統合し、以下のようにこれらのアプリを向上させるのに役立ちます:

- **パーソナライゼーション**: AIはユーザーの行動や嗜好を分析して、パーソナライズされた推奨、コンテンツ、および体験を提供できます。
  例：Netflix のようなストリーミングサービスは、視聴履歴に基づいて映画や番組を推奨し、ユーザーのエンゲージメントと満足度を高めます。
- **自動化と効率化**: AIは反復作業を自動化し、ワークフローを合理化し、運用効率を改善できます。
  例：カスタマーサービスアプリは、AI搭載のチャットボットを使用して一般的な問い合わせに対応し、応答時間を短縮し、より複雑な問題に対して人間の担当者のリソースを確保します。
- **強化されたユーザー体験**: AIは音声認識、自然言語処理、予測入力などのインテリジェントな機能を提供することで、全体的なユーザー体験を向上させることができます。
  例：Siri や Google Assistant のような仮想アシスタントは、音声コマンドを理解して応答するためにAIを使用し、ユーザーがデバイスとやり取りするのを容易にします。

### それはすべて素晴らしいですね、ではなぜAIエージェントフレームワークが必要なのでしょうか？

AIエージェントフレームワークは単なるAIフレームワーク以上のものを表しています。これらは、ユーザー、他のエージェント、および環境と対話して特定の目標を達成できるインテリジェントなエージェントの作成を可能にするよう設計されています。これらのエージェントは自律的な振る舞いを示し、意思決定を行い、変化する条件に適応することができます。AIエージェントフレームワークによって可能になる主な機能を見てみましょう:

- **エージェントの協調とコーディネーション**: 複数のAIエージェントを作成し、協力し、通信し、複雑なタスクを解決するために調整することを可能にします。
- **タスクの自動化と管理**: マルチステップのワークフローの自動化、タスクの委任、およびエージェント間の動的タスク管理の仕組みを提供します。
- **文脈理解と適応**: エージェントに文脈を理解し、変化する環境に適応し、リアルタイムの情報に基づいて意思決定を行う能力を装備します。

要約すると、エージェントを使うことでより多くのことができ、自動化を次のレベルに引き上げ、環境から適応・学習できるよりインテリジェントなシステムを作成できます。

## どのようにして迅速にプロトタイプを作成し、反復し、エージェントの機能を改善するか？

この分野は急速に進化していますが、ほとんどのAIエージェントフレームワークに共通するいくつかの要素があり、迅速なプロトタイプ作成と反復に役立ちます。具体的にはモジュール化コンポーネント、協調ツール、およびリアルタイム学習です。これらを詳しく見ていきましょう:

- **モジュールコンポーネントを使用する**: AI SDK は AI およびメモリコネクタ、自然言語やコードプラグインを用いた関数呼び出し、プロンプトテンプレートなどの事前構築コンポーネントを提供します。
- **協調ツールを活用する**: 特定の役割とタスクを持つエージェントを設計し、協調ワークフローをテストおよび洗練することを可能にします。
- **リアルタイムで学習する**: エージェントが相互作用から学び、動的に振る舞いを調整するフィードバックループを実装します。

### モジュールコンポーネントを使用する

Microsoft Semantic Kernel や LangChain のような SDK は、AI コネクタ、プロンプトテンプレート、メモリ管理などの事前構築コンポーネントを提供します。

**チームがこれを使う方法**: チームはこれらのコンポーネントを迅速に組み合わせて、ゼロから構築することなく機能的なプロトタイプを作成し、迅速な実験と反復を可能にします。

**実践での動作**: 事前構築されたパーサーを使用してユーザー入力から情報を抽出し、データを保存・取得するメモリモジュールを使い、プロンプトジェネレータでユーザーとやり取りする、といったことをすべて一から構築する必要はありません。

**例のコード**. Semantic Kernel の Python と .Net で事前構築された AI コネクタを使用し、オート関数呼び出しを利用してモデルにユーザー入力に応答させる例を見てみましょう:

``` python
# セマンティックカーネル Python の例

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# 会話のコンテキストを保持する ChatHistory オブジェクトを定義する
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# 旅行予約の関数を含むサンプルプラグインを定義する
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# カーネルを作成する
kernel = Kernel()

# サンプルプラグインをカーネルオブジェクトに追加する
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Azure OpenAI AI コネクターを定義する
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# モデルを自動関数呼び出しで構成するリクエスト設定を定義する
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # 指定されたチャット履歴とリクエスト設定でモデルにリクエストを行う
    # カーネルはモデルが呼び出すサンプルを含んでいる
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # AIモデルの応答例: `2025年1月1日のニューヨークへのフライトが正常に予約されました。安全な旅を！✈️🗽`

    # モデルの応答をチャット履歴のコンテキストに追加する
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```

この例から分かるのは、事前構築されたパーサーを活用して、フライト予約リクエストの出発地、目的地、日付などの主要な情報をユーザー入力から抽出できる点です。このモジュール化されたアプローチにより、ハイレベルなロジックに集中できます。

### 協調ツールを活用する

CrewAI、Microsoft AutoGen、Semantic Kernel のようなフレームワークは、協力して動作できる複数のエージェントの作成を支援します。

**チームがこれを使う方法**: チームは特定の役割とタスクを持つエージェントを設計し、協調ワークフローをテストおよび洗練して全体のシステム効率を改善できます。

**実践での動作**: 各エージェントがデータ取得、分析、意思決定などの専門的な機能を持つエージェントチームを作成できます。これらのエージェントは通信して情報を共有し、ユーザーの問い合わせに答えたりタスクを完了したりするなどの共通の目標を達成します。

**例のコード (AutoGen)**:

```python
# エージェントを作成し、それからラウンドロビンスケジュールを作成して、今回は順番に一緒に作業できるようにします

# データ取得エージェント
# データ分析エージェント
# 意思決定エージェント

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# ユーザーが「APPROVE」と言うと会話が終了します
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# スクリプトで実行する場合は asyncio.run(...) を使用してください。
await Console(stream)
```

前のコードで分かるのは、複数のエージェントが協力してデータを分析するタスクをどのように作成できるかという点です。各エージェントは特定の機能を実行し、望ましい結果を達成するためにエージェント間の調整によってタスクが実行されます。専用の役割を持つエージェントを作成することで、タスクの効率とパフォーマンスを向上させることができます。

### リアルタイムで学習する

高度なフレームワークは、リアルタイムの文脈理解と適応の機能を提供します。

**チームがこれを使う方法**: チームは、エージェントがやり取りから学び、その振る舞いを動的に調整するフィードバックループを実装することで、継続的な改善と能力の洗練を行うことができます。

**実践での動作**: エージェントはユーザーフィードバック、環境データ、およびタスクの結果を分析して知識ベースを更新し、意思決定アルゴリズムを調整し、時間とともにパフォーマンスを向上させることができます。この反復学習プロセスにより、エージェントは変化する条件やユーザーの嗜好に適応し、システム全体の有効性を高めます。

## AutoGen、Semantic Kernel、Azure AI Agent Service の違いは何か？

これらのフレームワークを比較する方法は多数ありますが、設計、機能、およびターゲットユースケースの観点からいくつかの主要な違いを見てみましょう:

## AutoGen

AutoGen は Microsoft Research の AI Frontiers Lab によって開発されたオープンソースのフレームワークです。イベント駆動型の分散*エージェント的*アプリケーションに焦点を当てており、複数の LLM や SLM、ツール、および高度なマルチエージェント設計パターンを可能にします。

AutoGen は、環境を知覚し、意思決定を行い、特定の目標を達成するために行動を取る自律的な実体である「エージェント」というコア概念を中心に構築されています。エージェントは非同期メッセージを通じて通信し、それにより独立かつ並列に動作でき、システムのスケーラビリティと応答性を向上させます。

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">エージェントはアクターモデルに基づいています</a>。Wikipedia によると、アクターとは _並行計算の基本的な構成要素である。受け取ったメッセージに応答して、アクターはローカルな判断を下したり、さらにアクターを作成したり、より多くのメッセージを送信したり、次に受け取るメッセージへの応答方法を決定したりできます_。

**ユースケース**: コード生成の自動化、データ分析タスク、および計画・研究機能向けのカスタムエージェントの構築。

AutoGen の重要なコア概念をいくつか紹介します:

- **エージェント**。エージェントは以下を行うソフトウェア実体です:
  - **メッセージを介して通信する**。これらのメッセージは同期的または非同期的であり得ます。
  - **自身の状態を保持する**。この状態は受信したメッセージによって変更され得ます。
  - **受信したメッセージや状態の変化に応じてアクションを実行する**。これらのアクションはエージェントの状態を変更したり、メッセージログの更新、新しいメッセージの送信、コードの実行、API呼び出しなどの外部効果を生み出す場合があります。
    
  次に、チャット機能を持つ独自のエージェントを作成する短いコードスニペットがあります:

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
    
    前のコードでは、`MyAgent` が作成され `RoutedAgent` を継承しています。メッセージハンドラがメッセージの内容を出力し、その後 `AssistantAgent` デリゲートを使用して応答を送信します。特に、`self._delegate` に `AssistantAgent` のインスタンスを割り当てている点に注意してください。これはチャット補完を扱える事前構築のエージェントです。


    次に、AutoGen にこのエージェントタイプを知らせてプログラムを起動します:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # バックグラウンドでメッセージの処理を開始します。
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    前のコードではエージェントがランタイムに登録され、その後エージェントにメッセージが送られ、次のような出力が得られます:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **マルチエージェント**。AutoGen は複数のエージェントを作成して協力して複雑なタスクを達成することをサポートします。エージェントは通信し、情報を共有し、行動を調整して問題をより効率的に解決できます。マルチエージェントシステムを作成するには、データ取得、分析、意思決定、ユーザーとの対話などの専門機能や役割を持つ異なるタイプのエージェントを定義できます。どのようにそのような作成が見えるか、感覚をつかめるように見てみましょう:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # エージェントの宣言例
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # トピックタイプをエージェントタイプとして使用
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # 残りの宣言は簡潔にするため省略

    # グループチャット
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```

    前のコードでは、`GroupChatManager` がランタイムに登録されています。このマネージャは、ライター、イラストレーター、編集者、ユーザーなど、さまざまなタイプのエージェント間の相互作用を調整する役割を担っています。

- **エージェントランタイム**。フレームワークはランタイム環境を提供し、エージェント間の通信を可能にし、エージェントの識別子とライフサイクルを管理し、セキュリティとプライバシーの境界を強制します。これは、エージェントを安全かつ制御された環境で実行できることを意味します。関心のあるランタイムは二つあります:
  - **スタンドアロンランタイム**。これは、すべてのエージェントが同じプログラミング言語で実装され同じプロセスで実行される単一プロセスアプリケーションに適した選択です。動作のイラストは以下のとおりです:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">スタンドアロンランタイム</a>   
Application stack

    *エージェントはランタイムを通じてメッセージで通信し、ランタイムはエージェントのライフサイクルを管理します*

  - **分散エージェントランタイム**。これはエージェントが異なるプログラミング言語で実装され、異なるマシンで動作する可能性のあるマルチプロセスアプリケーションに適しています。動作のイラストは以下のとおりです:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">分散ランタイム</a>

## Semantic Kernel + Agent Framework

Semantic Kernel はエンタープライズ対応の AI オーケストレーション SDK です。これは AI およびメモリコネクタに加えて、エージェントフレームワークで構成されています。

まずいくつかのコアコンポーネントを説明します:

- **AI コネクタ**: これは Python と C# の両方で使用する外部 AI サービスやデータソースとのインターフェイスです。

  ```python
  # セマンティックカーネル Python
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  

    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```

    ここには、カーネルを作成してチャット補完サービスを追加する簡単な例があります。Semantic Kernel は外部 AI サービス、ここでは Azure OpenAI Chat Completion への接続を作成します。

- **プラグイン**: これらはアプリケーションが使用できる関数をカプセル化します。既成のプラグインとカスタムで作成できるプラグインの両方があります。関連する概念として「プロンプト関数」があります。自然言語による指示を提供する代わりに、特定の関数をモデルにブロードキャストします。現在のチャットコンテキストに基づき、モデルはこれらの関数のいずれかを呼び出してリクエストやクエリを完了することを選ぶ場合があります。例は次のとおりです:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```

    ここでは、まずユーザーがテキスト `$userInput` を入力する余地を残すテンプレートプロンプト `skPrompt` があります。次にカーネル関数 `SummarizeText` を作成し、それを `SemanticFunctions` というプラグイン名でカーネルにインポートします。Semantic Kernel が関数の目的や呼び出すべきタイミングを理解するのに役立つ関数名に注目してください。

- **ネイティブ関数**: フレームワークがタスクを実行するために直接呼び出せるネイティブ関数もあります。ファイルからコンテンツを取得するそのような関数の例を示します:

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```

- **メモリ**: AIアプリの文脈管理を抽象化し簡素化します。メモリの考え方は、LLM が知っておくべきものという点です。これらの情報をベクトルストアに保存することができ、これは結果的にインメモリデータベースやベクトルデータベースなどになります。以下は *事実* がメモリに追加される非常に単純化されたシナリオの例です:

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```

    これらの事実はその後メモリコレクション `SummarizedAzureDocs` に保存されます。これは非常に単純化した例ですが、LLM が使用するためにメモリに情報を保存する方法が分かります。

So that's the basics of the Semantic Kernel framework, what about the Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service is a more recent addition, introduced at Microsoft Ignite 2024. It allows for the development and deployment of AI agents with more flexible models, such as directly calling open-source LLMs like Llama 3, Mistral, and Cohere.

Azure AI Agent Service provides stronger enterprise security mechanisms and data storage methods, making it suitable for enterprise applications. 

It works out-of-the-box with multi-agent orchestration frameworks like AutoGen and Semantic Kernel.

This service is currently in Public Preview and supports Python and C# for building agents.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# サンプル用のサンプルプラグインを定義する
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # エージェント定義を作成する
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # 定義されたクライアントとエージェント定義を使ってAzureAIエージェントを作成する
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # 会話を保持するスレッドを作成する
        # スレッドが提供されない場合、新しいスレッドが
        # 作成され、初期応答とともに返される
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # 指定されたスレッドのためにエージェントを呼び出す
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### Core concepts

Azure AI Agent Service has the following core concepts:

- **Agent**. Azure AI Agent Service integrates with Microsoft Foundry. Within AI Foundry, an AI Agent acts as a "smart" microservice that can be used to answer questions (RAG), perform actions, or completely automate workflows. It achieves this by combining the power of generative AI models with tools that allow it to access and interact with real-world data sources. Here's an example of an agent:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    この例では、モデル `gpt-4o-mini`、名前 `my-agent`、指示 `You are helpful agent` でエージェントが作成されています。エージェントはコード解釈タスクを実行するためのツールとリソースを備えています。

- **Thread and messages**. スレッドは別の重要な概念です。これはエージェントとユーザー間の会話ややり取りを表します。スレッドは会話の進行を追跡し、コンテキスト情報を保存し、やり取りの状態を管理するために使用できます。以下はスレッドの例です:

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    前のコードでは、スレッドが作成され、その後スレッドにメッセージが送信されます。`create_and_process_run` を呼び出すことで、エージェントにスレッド上で作業するよう依頼します。最後に、メッセージを取得してログに記録し、エージェントの応答を確認します。メッセージはユーザーとエージェント間の会話の進行状況を示します。また、メッセージはテキスト、画像、ファイルなど異なるタイプになり得ることを理解することも重要です。つまり、エージェントの作業が例えば画像やテキストによる応答を生み出すことがあります。開発者として、その情報を用いて応答をさらに処理したり、ユーザーに提示したりできます。

- **Integrates with other AI frameworks**. Azure AI Agent service は AutoGen や Semantic Kernel のような他のフレームワークと連携できます。つまり、アプリの一部をこれらのフレームワークのいずれかで構築し、Agent service をオーケストレーターとして使用したり、Agent service ですべてを構築したりすることが可能です。

**Use Cases**: Azure AI Agent Service は、安全でスケーラブルかつ柔軟な AI エージェントのデプロイを必要とするエンタープライズ向けアプリケーションを対象としています。

## What's the difference between these frameworks?
 
It does sound like there is a lot of overlap between these frameworks, but there are some key differences in terms of their design, capabilities, and target use cases:
 
- **AutoGen**: マルチエージェントシステムに関する最先端の研究に焦点を当てた実験用フレームワークです。複雑なマルチエージェントシステムを実験・プロトタイプ化するのに最適です。
- **Semantic Kernel**: エンタープライズ向けのエージェントアプリケーションを構築するための本番対応のエージェントライブラリです。イベント駆動で分散型のエージェントアプリケーションに注力しており、複数のLLMやSLM、ツール、単一/複数エージェントの設計パターンを可能にします。
- **Azure AI Agent Service**: エージェント向けのプラットフォーム兼デプロイメントサービスで、Azure Foundry 上にあります。Azure OpenAI、Azure AI Search、Bing Search やコード実行など、Azure のサービスとの連携を提供します。
 
Still not sure which one to choose?

### Use Cases
 
Let's see if we can help you by going through some common use cases:
 
> Q: I'm experimenting, learning and building proof-of-concept agent applications, and I want to be able to build and experiment quickly
>
>
>A: AutoGen would be a good choice for this scenario, as it focuses on event-driven, distributed agentic applications and supports advanced multi-agent design patterns.

> Q: What makes AutoGen a better choice than Semantic Kernel and Azure AI Agent Service for this use case?
>
> A: AutoGen is specifically designed for event-driven, distributed agentic applications, making it well-suited for automating code generation and data analysis tasks. It provides the necessary tools and capabilities to build complex multi-agent systems efficiently.

>Q: Sounds like Azure AI Agent Service could work here too, it has tools for code generation and more?

>
> A: Yes, Azure AI Agent Service is a platform service for agents and add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. It makes it easy to build your agents in the Foundry Portal and deploy them at scale.
 
> Q: I'm still confused just give me one option
>
> A: A great choice is to build your application in Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. This approach allows you to easily persist your agents while leveraging the power to build multi-agent systems in Semantic Kernel. Additionally, Semantic Kernel has a connector in AutoGen, making it easy to use both frameworks together.
 
Let's summarize the key differences in a table:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | イベント駆動、分散型エージェントアプリケーション | エージェント、ペルソナ、関数、データ | コード生成、データ分析タスク |
| Semantic Kernel | 人間らしいテキストコンテンツの理解と生成 | エージェント、モジュールコンポーネント、コラボレーション | 自然言語理解、コンテンツ生成 |
| Azure AI Agent Service | 柔軟なモデル、エンタープライズセキュリティ、コード生成、ツール呼び出し | モジュール性、コラボレーション、プロセスオーケストレーション | 安全でスケーラブルかつ柔軟な AI エージェントのデプロイ |

What's the ideal use case for each of these frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

The answer is yes, you can integrate your existing Azure ecosystem tools directly with Azure AI Agent Service especially, this because it has been built to work seamlessly with other Azure services. You could for example integrate Bing, Azure AI Search, and Azure Functions. There's also deep integration with Microsoft Foundry.

For AutoGen and Semantic Kernel, you can also integrate with Azure services, but it may require you to call the Azure services from your code. Another way to integrate is to use the Azure SDKs to interact with Azure services from your agents. Additionally, like was mentioned, you can use Azure AI Agent Service as an orchestrator for your agents built in AutoGen or Semantic Kernel which would give easy access to the Azure ecosystem.

## Sample Codes

- Python: [エージェント フレームワーク](./code_samples/02-python-agent-framework.ipynb)
- .NET: [エージェント フレームワーク](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet with other learners, attend office hours and get your AI Agents questions answered.

## References

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel と AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python エージェントフレームワーク</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net エージェントフレームワーク</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent サービス</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">AutoGen / Semantic Kernel と Azure AI Agent Service を使用してマルチエージェントソリューションを構築する</a>

## Previous Lesson

[AI エージェントとユースケースの紹介](../01-intro-to-ai-agents/README.md)

## Next Lesson

[エージェント設計パターンの理解](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免責事項：
本書は AI 翻訳サービス「Co‑op Translator」（https://github.com/Azure/co-op-translator）を使用して翻訳されました。正確性に努めていますが、自動翻訳には誤りや不正確さが含まれる可能性があることをご承知おきください。原文（原言語での文書）が正式な情報源と見なされます。重要な情報については、専門の人間による翻訳を推奨します。本翻訳の利用により生じた誤解や解釈の相違について、当社は一切の責任を負いません。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->