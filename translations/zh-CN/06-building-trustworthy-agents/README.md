[![可信赖的 AI 代理](../../../translated_images/zh-CN/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(点击上方图片查看本课视频)_

# 构建可信赖的 AI 代理

## 介绍

本课将涵盖：

- 如何构建和部署安全有效的 AI 代理
- 开发 AI 代理时的重要安全注意事项
- 开发 AI 代理时如何维护数据和用户隐私

## 学习目标

完成本课后，您将能够：

- 识别和减轻创建 AI 代理时的风险
- 实施安全措施，确保数据和访问得到妥善管理
- 创建维护数据隐私并提供优质用户体验的 AI 代理

## 安全

我们先来看看如何构建安全的代理应用。安全意味着 AI 代理按设计执行。作为代理应用的构建者，我们拥有最大化安全性的方法和工具：

### 构建系统消息框架

如果您曾使用大型语言模型（LLM）构建 AI 应用，就会知道设计强健的系统提示或系统消息的重要性。这些提示建立了元规则、指令和指南，指导 LLM 如何与用户和数据交互。

对于 AI 代理而言，系统提示更为重要，因为 AI 代理需要高度具体的指令来完成我们为其设计的任务。

为了创建可扩展的系统提示，我们可以使用系统消息框架来构建应用中的一个或多个代理：

![构建系统消息框架](../../../translated_images/zh-CN/system-message-framework.3a97368c92d11d68.webp)

#### 第 1 步：创建元系统消息

元提示将由 LLM 用于生成我们创建的代理的系统提示。我们将其设计成模板，以便在需要时高效创建多个代理。

以下是我们给 LLM 的一个元系统消息示例：

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### 第 2 步：创建基础提示

下一步是创建一个基础提示来描述 AI 代理。您应包括代理的角色、代理将完成的任务以及代理的其他职责。

示例：

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### 第 3 步：向 LLM 提供基础系统消息

现在我们可以通过提供元系统消息作为系统消息和我们的基础系统消息来优化此系统消息。

这将生成一个更适合指导我们 AI 代理的系统消息：

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

#### 第 4 步：迭代与改进

该系统消息框架的价值在于能够更轻松地扩展多个代理的系统消息创建，并随着时间推移改进系统消息。您的系统消息很少能第一次就完全满足用例需求。能够通过更改基础系统消息并让其通过系统进行处理，进行小幅调整和改进，将允许您比较和评估结果。

## 了解威胁

为了构建可信赖的 AI 代理，重要的是了解和减轻 AI 代理面临的风险和威胁。我们仅看一些针对 AI 代理的不同威胁，以及如何更好地进行规划和准备。

![了解威胁](../../../translated_images/zh-CN/understanding-threats.89edeada8a97fc0f.webp)

### 任务与指令

**描述:** 攻击者试图通过提示或操控输入更改 AI 代理的指令或目标。

**缓解措施:** 执行验证检查和输入过滤，以检测潜在危险提示，防止其被 AI 代理处理。由于此类攻击通常需要频繁与代理交互，限制对话轮数是预防这类攻击的另一种方式。

### 访问关键系统

**描述:** 如果 AI 代理可访问存储敏感数据的系统和服务，攻击者可通过代理与这些服务之间的通信进行攻击。这些攻击可能是直接的，也可能是通过代理尝试间接获取这些系统信息。

**缓解措施:** AI 代理应仅在必要时访问系统，以防止此类攻击。代理与系统之间的通信也应保证安全。实施身份验证和访问控制是保护此类信息的另一个方法。

### 资源和服务过载

**描述:** AI 代理访问不同工具和服务以完成任务。攻击者可能利用此能力通过 AI 代理发送大量请求攻击这些服务，可能导致系统故障或高昂费用。

**缓解措施:** 实施策略限制 AI 代理对服务的请求次数。限制与 AI 代理的对话轮数和请求次数是防止此类攻击的另一方式。

### 知识库投毒

**描述:** 此类攻击不是直接针对 AI 代理，而是针对 AI 代理将使用的知识库和其他服务。攻击可能通过破坏 AI 代理用于完成任务的数据或信息，导致向用户提供带偏见或非预期的响应。

**缓解措施:** 定期核查 AI 代理在工作流程中使用的数据。确保对此数据的访问安全，仅由可信人员更改，以避免此类攻击。

### 级联错误

**描述:** AI 代理访问各种工具和服务以完成任务。攻击者造成的错误可能导致 AI 代理连接的其他系统失败，使攻击范围扩大且更难排查。

**缓解措施:** 避免此类情况的一种方法是让 AI 代理在有限环境中运行，例如在 Docker 容器中执行任务，防止对系统的直接攻击。创建回退机制和在某些系统返回错误时的重试逻辑是防止更大系统故障的另一方式。

## 人类参与环节

构建可信赖的 AI 代理系统的另一有效方法是使用人类参与环节。这种方法创建了一个流程，用户可以在运行过程中向代理反馈。用户本质上作为多代理系统中的代理，提供对运行过程的批准或终止。

![人类参与环节](../../../translated_images/zh-CN/human-in-the-loop.5f0068a678f62f4f.webp)

以下是使用 AutoGen 展示此概念实现的代码片段：

```python

# 创建代理。
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # 使用 input() 从控制台获取用户输入。

# 创建终止条件，当用户说“APPROVE”时结束对话。
termination = TextMentionTermination("APPROVE")

# 创建团队。
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# 运行对话并将结果流式输出到控制台。
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# 在脚本中运行时使用 asyncio.run(...)。
await Console(stream)

```

## 结论

构建可信赖的 AI 代理需要细致的设计、强有力的安全措施和持续迭代。通过实施结构化的元提示系统、理解潜在威胁并应用缓解策略，开发者可创建安全有效的 AI 代理。此外，结合人类参与环节确保 AI 代理与用户需求保持一致，同时最大限度地降低风险。随着 AI 持续发展，保持在安全、隐私和伦理方面的积极态度，将是培养 AI 驱动系统可信赖性和可靠性的关键。

### 关于构建可信赖 AI 代理还有更多疑问？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，与其他学习者见面，参加答疑时间，获取您的 AI 代理问题解答。

## 额外资源

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">负责任的 AI 概述</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">生成式 AI 模型和 AI 应用评估</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">安全系统消息</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">风险评估模板</a>

## 上一课

[Agentic RAG](../05-agentic-rag/README.md)

## 下一课

[规划设计模式](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免责声明**：  
本文件使用 AI 翻译服务 [Co-op Translator](https://github.com/Azure/co-op-translator) 进行翻译。虽然我们努力确保翻译的准确性，但请注意自动翻译可能包含错误或不准确之处。该文件的原始语言版本应被视为权威版本。对于关键信息，建议采用专业人工翻译。我们不对因使用本翻译而产生的任何误解或误释承担责任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->