[![Multi-Agent Design](../../../translated_images/pcm/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Click di picture wey dey above make you watch video of dis lesson)_

# Multi-agent design patterns

As soon as you start to work for project wey get multiple agents, you go need to think about di multi-agent design pattern. But e fit no clear sharp as when to change to multi-agents and wetin di benefits be.

## Introduction

For dis lesson, we dey find answer to dis kain questions:

- Wetin be di situations wey multi-agents fit wok for?
- Wetin be di benefits of to use multi-agents pass just one agent wey dey do multiple work?
- Wetin be di building blocks of how to do di multi-agent design pattern?
- How we sabi how di multiple agents dey interact with each oda?

## Learning Goals

After dis lesson, you suppose fit:

- Identify di scenarios wey multi-agents fit take work
- Know di benefits of to use multi-agents pass one single agent.
- Understand di building blocks to implement di multi-agent design pattern.

Wetin be di big picture?

*Multi agents na design pattern wey dey let multiple agents work together to achieve one common goal*.

Dis pattern dey use well well for many fields, including robotics, autonomous systems, and distributed computing.

## Scenarios Where Multi-Agents Are Applicable

So wetin be the scenarios wey good for to use multi-agents? Di answer be say many situations dey where e good to use multiple agents especially for these cases:

- **Large workloads**: Large workloads fit divide into small small tasks and give different agents, so that dem fit work parallel and finish quick. Example na big data processing work.
- **Complex tasks**: Complex tasks, like large workloads, fit break down into small subtasks and different agents fit handle their own part wey dem get skill for. Example na autonomous vehicles wey get different agents to manage navigation, obstacle detection and to talk with other vehicles.
- **Diverse expertise**: Different agents fit get different skills, so dem fit handle different parts of task better pass one agent. Example na healthcare wey agents fit manage diagnostics, treatment plans and patient monitoring.

## Advantages of Using Multi-Agents Over a Singular Agent

Single agent system fit work well for simple tasks, but for complex tasks, using multiple agents fit give plenty benefits:

- **Specialization**: Each agent fit specialize for one task. If one agent no get specialization, e mean say e fit get confused when task complex. E fit end up doing work wey e no sabi well.
- **Scalability**: E easy to scale system by adding more agents than to overload one agent.
- **Fault Tolerance**: If one agent fail, others fit still work, so system no go break down.

Make we use example, make we book trip for user. One single agent go need handle all aspects of booking trip, from finding flight to booking hotel and rental cars. To do all dis, e need tools to handle everything. Dis go make system complex and hard to maintain or scale. But multi-agent system fit get different agents for finding flights, booking hotels and rental cars. Dis go make system modular, easy to maintain and scale.

Compare am to travel bureau wey be small mom-and-pop shop versus travel bureau wey be franchise. Mom-and-pop shop get one single agent wey dey do all booking work, while franchise get different agents wey dey do different parts of booking.

## Building Blocks of Implementing the Multi-Agent Design Pattern

Before you fit implement multi-agent design pattern, you need understand di building blocks wey make up di pattern.

Make we make am clear with example of booking trip for user. Di building blocks go include:

- **Agent Communication**: Agents for finding flights, booking hotels and rental cars need talk and share info about user preferences and conditions. You suppose decide on di protocols and ways for dis communication. For example, flight agent need talk with hotel agent to ensure say hotel book for same dates with flight. So agents need share info about user travel dates, so you need decide *which agents dey share info and how dem dey share am*.
- **Coordination Mechanisms**: Agents need organize their actions to meet user preferences and conditions. For example, user fit want hotel near airport but rental cars only dey airport. So hotel agent need coordinate with rental car agent to satisfy user condition. You need decide *how agents dey coordinate their actions*.
- **Agent Architecture**: Agents need internal structure to make decisions and learn from interaction with user. For example, flight agent need make decisions about which flights to recommend. You need decide *how agents dey make decisions and dey learn from user interaction*. Example na flight agent fit use machine learning to recommend flights base on user past preferences.
- **Visibility into Multi-Agent Interactions**: You need sabi how multiple agents dey interact. You need tools and ways to track agent activities and interaction. E fit be logging and monitoring tools, visualization tools and performance metrics.
- **Multi-Agent Patterns**: Different patterns dey for making multi-agent system like centralized, decentralized and hybrid architectures. You need decide which pattern fit your use case best.
- **Human in the loop**: Most times, human go dey inside loop and you need tell agents when to ask human to help. E fit be when user ask for specific hotel or flight wey agents never recommend or when user wan confirm before booking flight or hotel.

## Visibility into Multi-Agent Interactions

E important make you get visibility on how multiple agents dey interact. Dis visibility important for debugging, optimizing and making sure system work well. To achieve dis, you need tools and ways for tracking agent activities and interactions. E fit be logging and monitoring tools, visualization tools, and performance metrics.

For example, for booking trip for user, you fit get dashboard wey show each agent status, user preferences and conditions, plus how agents dey interact. Dashboard fit show travel dates, flights wey flight agent recommend, hotels wey hotel agent recommend, and rental cars wey rental car agent recommend. Dis go give you clear view on how agents dey interact and whether user preference and conditions dey meet.

Make we look each part in detail.

- **Logging and Monitoring Tools**: You suppose get logging for each action agent perform. Log fit store info about di agent wey perform action, di action wey e do, time e do am, plus result of di action. Dis info fit dey use for debugging, optimizing and more.

- **Visualization Tools**: Visualization tools fit help you see how agents dey interact in easier way. For example, you fit get graph wey show information dey flow between agents. Dis fit help find bottlenecks, inefficiencies and other problems wey dey system.

- **Performance Metrics**: Performance metrics fit help you track how well multi-agent system dey work. For example, time to finish task, number of tasks finished per time unit, plus how correct agent recommendations be. Dis info fit help find areas to improve and optimize system.

## Multi-Agent Patterns

Make we look some concrete patterns wey we fit use to make multi-agent apps. Here be some patterns wey dey interesting to consider:

### Group chat

Dis pattern good when you want create group chat app wey multiple agents fit talk to each other. Common use cases na team collaboration, customer support and social networking.

For dis pattern, each agent represent user for group chat, and messages dey exchange between agents with messaging protocol. Agents fit send message to group chat, receive messages from group chat and respond to messages from other agents.

Dis pattern fit implement using centralized architecture where all messages go through one central server, or decentralized architecture where messages dey exchange directly.

![Group chat](../../../translated_images/pcm/multi-agent-group-chat.ec10f4cde556babd.webp)

### Hand-off

Dis pattern good when you want create app wey multiple agents fit hand off tasks to each other.

Common use cases na customer support, task management, and workflow automation.

For dis pattern, each agent represent task or step for workflow, and agents fit hand off tasks to other agents based on rules wey dem set.

![Hand off](../../../translated_images/pcm/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Collaborative filtering

Dis pattern good when you want create app wey multiple agents fit collaborate to recommend to users.

Why you go want make multiple agents collaborate be say each agent get different skill and fit add to recommendation process in different ways.

Make we use example where user want recommendation on best stock to buy for stock market.

- **Industry expert**: One agent fit be expert for one particular industry.
- **Technical analysis**: Another agent fit be expert for technical analysis.
- **Fundamental analysis**: Another agent fit be expert for fundamental analysis. If dem collaborate, agents fit give better recommendation to user.

![Recommendation](../../../translated_images/pcm/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenario: Refund process

Think of scenario where customer wan get refund for product, plenty agents fit dey for dis process but make we divide am between agents wey specific to dis refund process and general agents wey you fit use for other processes.

**Agents wey specific for refund process**:

Below na some agents wey fit dey for refund process:

- **Customer agent**: Dis agent represent customer and e dey responsible to start refund process.
- **Seller agent**: Dis agent represent seller and e dey responsible to process refund.
- **Payment agent**: Dis agent represent payment process and e dey responsible to refund customer payment.
- **Resolution agent**: Dis agent represent resolution process and e dey responsible to solve any wahala wey show for refund process.
- **Compliance agent**: Dis agent represent compliance process and e dey responsible to make sure refund process dey follow regulations and policies.

**General agents**:

Dis agents fit use for other business parts.

- **Shipping agent**: Dis agent represent shipping process and e dey responsible to send product back to seller. Dis agent fit use for refund process and for regular shipping of product after purchase.
- **Feedback agent**: Dis agent represent feedback process and e dey collect feedback from customer. Feedback fit happen anytime no be only during refund process.
- **Escalation agent**: Dis agent represent escalation process and e dey responsible to escalate issues to higher support level. You fit use dis type of agent for any process wey need escalation.
- **Notification agent**: Dis agent represent notification process and e dey responsible to send notifications to customer for different stages of refund process.
- **Analytics agent**: Dis agent represent analytics process and e dey responsible to analyze data wey relate to refund process.
- **Audit agent**: Dis agent represent audit process and e dey responsible to audit refund process to make sure say e dey do well.
- **Reporting agent**: Dis agent represent reporting process and e dey responsible to generate reports on refund process.
- **Knowledge agent**: Dis agent represent knowledge process and e dey responsible to keep knowledge base of info related to refund process. Dis agent fit sabi both refunds and other business areas.
- **Security agent**: Dis agent represent security process and e dey responsible to make sure refund process dey secure.
- **Quality agent**: Dis agent represent quality process and e dey responsible to make sure refund process get quality.

Plenty agents dey wey we list above both for specific refund process and general agents wey you fit use for other business parts. Hopefully, dis go give you idea on how to decide which agents you go use for your multi-agent system.

## Assignment

Design multi-agent system for customer support process. Identify agents wey dey involved, their roles and responsibilities, and how dem dey interact. Consider both agents wey specific to customer support process and general agents wey fit use for other business parts.
> Make you reason well before you read di solution wey dey below, e fit be say you go need more agents pass wetin you dey think.

> TIP: Reason di different stages of how customer support dey operate and also think about agents wey any system fit need.

## Solution

[Solution](./solution/solution.md)

## Knowledge checks

Question: When you suppose consider to use multi-agents?

- [ ] A1: When your workload small and task simple.
- [ ] A2: When your workload big
- [ ] A3: When your task simple.

[Solution quiz](./solution/solution-quiz.md)

## Summary

For dis lesson, we don look di multi-agent design pattern, including di times wey multi-agents fit work, di benefits of to use multi-agents pass only one agent, di things wey you go need to build di multi-agent design pattern, and how you fit dey see how many agents dey work together.

### Get more questions about the Multi-Agent Design Pattern?

Join di [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet other learners, join office hours and get your AI Agents questions answer.

## Additional resources

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen design patterns</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentic design patterns</a>


## Previous Lesson

[Planning Design](../07-planning-design/README.md)

## Next Lesson

[Metacognition in AI Agents](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Dis dokument don translate wit AI translation service [Co-op Translator](https://github.com/Azure/co-op-translator). Even though we dey try make am correct, abeg sabi say automated translation fit get some mistakes or wahala. Di original dokument wey dey im original language na di correct one you suppose trust. If na serious info, e better make professional human translator do am. We no go responsible for any misunderstanding or wrong interpretation wey fit happen because of dis translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->