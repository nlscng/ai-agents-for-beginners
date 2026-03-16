[![Planning Design Pattern](../../../translated_images/ja/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(上の画像をクリックするとこのレッスンの動画を視聴できます)_

# 計画デザイン

## はじめに

このレッスンでは以下について説明します：

* 明確な全体目標の設定と、複雑なタスクを管理しやすいタスクに分割する方法。
* 構造化された出力を活用して、より信頼性が高く機械可読な応答を得る方法。
* 動的なタスクや予期しない入力に対応するためのイベント駆動アプローチの適用。

## 学習目標

このレッスンを終えると、以下のことが理解できるようになります：

* AIエージェントの全体目標を特定し設定し、達成すべきことを明確に認識させる方法。
* 複雑なタスクを扱いやすいサブタスクに分解し、それらを論理的な順序で整理する方法。
* エージェントに適切なツール（例：検索ツールやデータ分析ツール）を装備させ、それらをいつどのように使用するかを決め、予期しない状況に対応する方法。
* サブタスクの成果を評価し、性能を測定し、最終的な出力を向上させるために行動を繰り返す方法。

## 全体目標の定義とタスクの分解

![Defining Goals and Tasks](../../../translated_images/ja/defining-goals-tasks.d70439e19e37c47a.webp)

ほとんどの実世界のタスクは一度のステップで解決できるほど単純ではありません。AIエージェントには、計画や行動を導く簡潔な目的が必要です。例えば、次の目標を考えてみましょう：

    「3日間の旅行プランを作成する」

これは簡単に述べられますが、まだ詳しく定義する必要があります。目標が明確であればあるほど、エージェント（および協力する人間も）は適切な成果、例えば、フライトオプション、ホテルの推奨、アクティビティの提案を含む包括的な旅行計画を作成することに集中できます。

### タスクの分解

大きなタスクや複雑なタスクは、小さく目的指向のサブタスクに分割すると扱いやすくなります。
旅行プランの例では、目標を次のように分解できます：

* フライト予約
* ホテル予約
* レンタカー
* パーソナライズ

それぞれのサブタスクは専門のエージェントやプロセスで対応できます。あるエージェントは最もお得なフライトを検索し、別のエージェントはホテル予約を担当するなどです。調整役や「下流」のエージェントがそれらの結果をまとめて、最終ユーザー向けの一貫した旅行プランを作成します。

このモジュール式アプローチにより、段階的な改良も可能です。例えば、食事の推薦や地元のアクティビティの提案を専門とするエージェントを追加し、旅行プランを時間をかけて改善していけます。

### 構造化出力

大規模言語モデル（LLM）は、下流のエージェントやサービスが解析・処理しやすい構造化された出力（たとえばJSON）を生成できます。これは特にマルチエージェントの文脈で有用で、計画結果を受け取った後にこれらのタスクを実行できます。詳しくはこの<a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">ブログ記事</a>をご参照ください。

以下のPythonコードは、目標をサブタスクに分解し構造化プランを生成するシンプルな計画エージェントの例です：

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# 旅行サブタスクモデル
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # タスクをエージェントに割り当てたい

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # モデルを認証するには、GitHub設定でパーソナルアクセストークン（PAT）を生成する必要があります。
    # こちらの手順に従ってPATトークンを作成してください: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# ユーザーメッセージを定義する
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # レスポンス内容が有効なJSON文字列であることを確認してから読み込む
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     ValueError("レスポンス内容が有効なJSON文字列ではありません") を発生させる

# # JSONとして読み込んだ後、レスポンス内容を表示する
# pprint(json.loads(response_content))

# MathReasoningモデルでレスポンス内容を検証する
# TravelPlan.model_validate(json.loads(response_content))
```

### マルチエージェントオーケストレーションを備えた計画エージェント

この例では、セマンティックルーターエージェントがユーザーのリクエスト（例：「旅行のためのホテルプランがほしい」）を受け取ります。

計画者は以下の役割を担います：

* ホテルプランの受け取り：ユーザーのメッセージを受け取り、利用可能なエージェント情報を含むシステムプロンプトを基に、構造化された旅行プランを生成します。
* エージェントとツールのリストアップ：エージェントレジストリにはフライト、ホテル、レンタカー、アクティビティなどのエージェントと、それぞれの提供する機能やツールのリストがあります。
* プランを担当エージェントへルーティング：サブタスク数に応じて、単一タスクの場合は直接専用エージェントにメッセージを送信し、マルチエージェントの場合はグループチャットマネージャを介して連携を取ります。
* 結果の概要作成：最終的に計画者は生成されたプランをわかりやすく要約します。

以下のPythonコードサンプルはこれらのステップを示しています：

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# 旅行サブタスクモデル

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # タスクをエージェントに割り当てたい

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# 型チェックされた環境変数でクライアントを作成する

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# ユーザーメッセージを定義する

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# 読み込む前にレスポンスの内容が有効なJSON文字列であることを確認する

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# JSONとして読み込んだ後にレスポンスの内容を出力する

pprint(json.loads(response_content))
```

以下は前述のコードからの出力例で、`assigned_agent` にルーティングして旅行プランを要約し、エンドユーザーに提示できます。

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

このコードサンプルを含むノートブックの例は[こちら](07-autogen.ipynb)で提供しています。

### 反復的計画

いくつかのタスクは、1つのサブタスクの結果が次のタスクに影響を与えるため、往復のやり取りや再計画が必要です。たとえば、フライト予約中に予期しないデータ形式が見つかった場合、ホテル予約に移る前に戦略を調整する必要があります。

また、ユーザーからのフィードバック（例：人間がより早いフライトを好むと決めた場合）が一部の再計画を引き起こすこともあります。このような動的で反復的なアプローチにより、最終的な解決策が実世界の制約や変化するユーザーの好みに適応します。

例：サンプルコード

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. 前のコードと同様にユーザーの履歴、現在のプランを引き継ぐ
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. 再計画を行い、タスクをそれぞれのエージェントに送信する
```

より包括的な計画を行う場合は、複雑なタスクを解決するためのMagnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">ブログ記事</a>もぜひご覧ください。

## まとめ

この記事では、利用可能なエージェントを動的に選択できる計画者の例を見てきました。計画者の出力はタスクを分解し、実行できるようエージェントに割り当てます。エージェントはタスクを実行するために必要な機能やツールにアクセスできると仮定します。エージェントに加え、反省（reflection）、要約（summarizer）、ラウンドロビンチャットなどのパターンを組み込んでさらにカスタマイズも可能です。

## 追加リソース

AutoGen Magentic One - 複雑なタスクを解決するための汎用マルチエージェントシステムで、複数の難しいエージェントベンチマークで素晴らしい成果を上げています。参考：https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one この実装ではオーケストレーターがタスク固有の計画を作成し、利用可能なエージェントにこれらのタスクを委任します。計画に加え、進捗を監視し必要に応じて再計画を行うトラッキング機能も備えています。

### 計画デザインパターンについてさらに質問がありますか？

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) に参加して、他の学習者と交流し、オフィスアワーに参加し、AIエージェントに関する質問に答えてもらいましょう。

## 前のレッスン

[信頼できるAIエージェントの構築](../06-building-trustworthy-agents/README.md)

## 次のレッスン

[マルチエージェントデザインパターン](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責事項**：  
本書類はAI翻訳サービス「Co-op Translator」（https://github.com/Azure/co-op-translator）を使用して翻訳されました。正確性を期しておりますが、自動翻訳には誤りや不正確な表現が含まれる可能性があることをご理解ください。原文はあくまで正式な参照資料としてください。重要な情報については、専門の人間による翻訳を推奨いたします。本翻訳の使用により生じた誤解や解釈の相違について、当方は一切責任を負いかねます。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->