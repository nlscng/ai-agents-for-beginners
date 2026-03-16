[![Trustworthy AI Agents](../../../translated_images/ja/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(上の画像をクリックするとこのレッスンのビデオを視聴できます)_

# 信頼できるAIエージェントの構築

## はじめに

このレッスンでは以下を扱います：

- 安全で効果的なAIエージェントの構築と展開方法
- AIエージェント開発時の重要なセキュリティ考慮点
- AIエージェント開発時のデータおよびユーザープライバシーの維持方法

## 学習目標

このレッスンを修了すると、以下ができるようになります：

- AIエージェント作成時のリスクの特定と軽減
- データとアクセスを適切に管理するためのセキュリティ対策の実装
- データプライバシーを保ちつつ質の高いユーザー体験を提供するAIエージェントの作成

## 安全性

まずは安全なエージェンティックアプリケーションの構築について見ていきましょう。安全性とは、AIエージェントが設計どおりに機能することを意味します。エージェンティックアプリケーションの開発者として、安全性を最大化するための方法とツールがあります。

### システムメッセージフレームワークの構築

もし大規模言語モデル（LLM）を使ってAIアプリケーションを構築したことがあれば、堅牢なシステムプロンプトやシステムメッセージの設計の重要性をご存じでしょう。これらのプロンプトは、LLMがユーザーやデータとどのように対話するかのメタルールや指示、ガイドラインを設定します。

AIエージェントにとっては、AIエージェントが設計したタスクを完遂するため、さらに具体的で詳細な指示が必要なため、システムプロンプトはもっと重要です。

拡張可能なシステムプロンプトを作成するために、アプリケーション内の一つまたは複数のエージェントを構築するためのシステムメッセージフレームワークを使うことができます：

![Building a System Message Framework](../../../translated_images/ja/system-message-framework.3a97368c92d11d68.webp)

#### ステップ1: メタシステムメッセージの作成

メタプロンプトは、LLMが作成するエージェント用のシステムプロンプトを生成するために使用されます。複数のエージェントを効率的に作成できるようにテンプレートとして設計します。

以下はLLMに与えるメタシステムメッセージの例です：

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### ステップ2: 基本プロンプトの作成

次のステップは、AIエージェントを説明する基本プロンプトを作成することです。エージェントの役割、エージェントが完了するタスク、その他の責任を含めるべきです。

例を示します：

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### ステップ3: LLMに基本システムメッセージを提供

今度は、メタシステムメッセージをシステムメッセージとして提供し、基本システムメッセージも一緒に渡すことでこのシステムメッセージを最適化できます。

これにより、AIエージェントを案内するのにより適したシステムメッセージが作成されます：

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### ステップ4: 反復と改善

このシステムメッセージフレームワークの価値は、複数のエージェントからシステムメッセージをスケーラブルに作成しやすくするとともに、時間をかけてシステムメッセージを改善できることです。最初から完全なユースケースに合うシステムメッセージができることは稀です。基本システムメッセージを変更してシステムで実行し、小さな調整や改善を行うことで、結果を比較・評価できます。

## 脅威の理解

信頼できるAIエージェントを構築するには、AIエージェントへのリスクや脅威を理解し、それを軽減することが重要です。AIエージェントに影響を及ぼす様々な脅威の一部について見て、どのようにより良く計画し準備できるかを考えましょう。

![Understanding Threats](../../../translated_images/ja/understanding-threats.89edeada8a97fc0f.webp)

### タスクと指示

**説明:** 攻撃者がプロンプトの操作や入力の改変によってAIエージェントの指示や目標を変更しようとする攻撃。

**軽減策:** AIエージェントが処理する前に潜在的に危険なプロンプトを検出するための検証チェックや入力フィルターを実行する。これらの攻撃は通常頻繁なエージェントとの対話を必要とするため、会話のターン数を制限することも防止策になる。

### 重要システムへのアクセス

**説明:** AIエージェントが機密データを保存しているシステムやサービスにアクセスできる場合、攻撃者がエージェントとこれらのサービス間の通信を乗っ取る可能性がある。これは直接攻撃やエージェントを介した間接的な情報収集の試みも含む。

**軽減策:** これらの攻撃を防ぐため、AIエージェントには必要な範囲でのみシステムへのアクセスを許可する。エージェントとシステム間の通信も安全にするべき。認証とアクセス制御の実装も情報保護手段の一つ。

### リソースとサービスの過負荷

**説明:** AIエージェントはタスクを完了するために様々なツールやサービスにアクセスできる。この能力を使い、攻撃者がエージェント経由で大量のリクエストを送信してサービスに攻撃をかけ、システム障害や高コストを引き起こす可能性がある。

**軽減策:** AIエージェントがサービスに送信できるリクエスト数を制限するポリシーを実装する。会話のターン数やエージェントへのリクエスト数を制限することも防止策となる。

### 知識ベースの汚染

**説明:** この種の攻撃はAIエージェント自体を直接狙うのではなく、エージェントが使用する知識ベースや他のサービスを狙う。データや情報を汚染することで、ユーザーへの応答に偏りや意図しない結果が生じる恐れがある。

**軽減策:** エージェントがワークフローで使用するデータを定期的に検証する。アクセスは安全に管理し、信頼できる人物のみが変更できるようにして、この攻撃を防ぐ。

### 連鎖的なエラー

**説明:** AIエージェントはタスク完了のため複数のツールやサービスを利用する。攻撃者によるエラーがこれらの接続されたシステムの障害を引き起こし、攻撃が拡大しトラブルシューティングが困難になる場合がある。

**軽減策:** これを避ける一つの方法として、たとえばDockerコンテナ内でタスクを実行するなど、限られた環境でAIエージェントを動作させて直接的なシステム攻撃を防ぐ手法がある。特定のシステムがエラー応答した際のフォールバック機構や再実行ロジックの作成も大規模なシステム障害を防ぐ方法である。

## ヒューマン・イン・ザ・ループ

信頼できるAIエージェントシステムを構築するもう一つの効果的な方法はヒューマン・イン・ザ・ループ方式の利用です。これは実行中にユーザーがエージェントにフィードバックを提供できるフローを作ります。ユーザーは多エージェントシステム内のエージェントの役割を果たし、実行プロセスの承認または終了を行います。

![Human in The Loop](../../../translated_images/ja/human-in-the-loop.5f0068a678f62f4f.webp)

以下はAutoGenを使ったこのコンセプトの実装例のコードスニペットです：

```python

# エージェントを作成します。
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # input() を使用してコンソールからユーザー入力を取得します。

# ユーザーが "APPROVE" と言ったときに会話を終了する終了条件を作成します。
termination = TextMentionTermination("APPROVE")

# チームを作成します。
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# 会話を実行し、コンソールにストリームします。
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# スクリプトで実行する際は asyncio.run(...) を使用します。
await Console(stream)

```

## まとめ

信頼できるAIエージェントを構築するには、綿密な設計、堅牢なセキュリティ対策、継続的な改善が必要です。体系的なメタプロンプトシステムの導入、潜在的な脅威の理解、軽減策の適用により、安全かつ効果的なAIエージェントを開発できます。さらにヒューマン・イン・ザ・ループ方式を取り入れることで、AIエージェントがユーザーのニーズと一致し、リスクを最小化することが可能です。AIが進化し続ける中で、セキュリティ、プライバシー、倫理的配慮に積極的に取り組むことが、AI駆動システムの信頼性と信頼を築く鍵となります。

### 信頼できるAIエージェントの構築についてさらに質問がありますか？

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) に参加して、他の学習者と交流し、オフィスアワーに参加してAIエージェントに関する質問に答えてもらいましょう。

## 追加リソース

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Responsible AI overview</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Evaluation of generative AI models and AI applications</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Safety system messages</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Risk Assessment Template</a>

## 前のレッスン

[Agentic RAG](../05-agentic-rag/README.md)

## 次のレッスン

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責事項**：  
本書類は、AI翻訳サービス「Co-op Translator」（https://github.com/Azure/co-op-translator）を使用して翻訳されました。正確性の向上に努めていますが、自動翻訳には誤りや不正確な箇所が含まれる可能性があります。原文の母国語版が正本として扱われるべきです。重要な情報については、専門の人間翻訳をご利用いただくことを推奨します。本翻訳の利用により生じたいかなる誤解や解釈の相違についても、当方は責任を負いません。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->