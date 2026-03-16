# Memori for AI Agents 
[![Agent Memori](../../../translated_images/pcm/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

When we dey talk about di special beta wey dey come from building AI Agents, two main tins dey: di ability to call tools to finish task dem and di ability to dey improve with time. Memori na di foundation wey make self-improving agent fit create better experience for our users.

For dis lesson, we go look wetin memori mean for AI Agents and how we fit manage am and use am for di betterment of our applications.

## Introduction

This lesson go cover:

• **Understanding AI Agent Memory**: Wetin memori be and why e important for agents.

• **Implementing and Storing Memory**: Practical ways to add memori capability to your AI agents, we go focus for short-term and long-term memori.

• **Making AI Agents Self-Improving**: How memori dey allow agents learn from past interactions and improve as time dey go.

## Available Implementations

This lesson get two full notebook tutorials:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implements memory using Mem0 and Azure AI Search with Semantic Kernel framework

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implements structured memory using Cognee, automatically building knowledge graph backed by embeddings, visualizing graph, and intelligent retrieval

## Learning Goals

After you finish this lesson, you go sabi how to:

• **Differentiate between various types of AI agent memory**, including working, short-term, and long-term memori, plus special forms like persona and episodic memori.

• **Implement and manage short-term and long-term memori for AI agents** using the Semantic Kernel framework, make use of tools like Mem0, Cognee, Whiteboard memory, and join am with Azure AI Search.

• **Understand the principles behind self-improving AI agents** and how solid memori management systems dey help continuous learning and adaptation.

## Understanding AI Agent Memory

For inside, **memori for AI agents mean di mechanisms wey make dem fit keep and recall information**. Dis information fit be specific details about one conversation, user preferences, past actions, or even patterns wey dem don learn.

Without memori, AI apps dey stateless, meaning every interaction start from zero. Dis one dey cause repetitive and frustrating user experience where di agent go dey "forget" previous context or preferences.

### Why is Memory Important?

Agent intelligence strong based on how e fit recall and use past information. Memori make agents fit:

• **Reflective**: Learn from past actions and outcomes.

• **Interactive**: Keep context across wetin dey go on for conversation.

• **Proactive and Reactive**: Anticipate needs or respond correct based on historical data.

• **Autonomous**: Work more independent by using stored knowledge.

Di goal for adding memori na to make agents more **reliable and capable**.

### Types of Memory

#### Working Memory

Think am like scratch paper wey agent dey use for one single ongoing task or thought process. E hold immediate information wey agent need to compute di next step.

For AI agents, working memori dey capture di most relevant info from one conversation, even if di full chat history long or don truncate. E dey focus on key elements like requirements, proposals, decisions, and actions.

**Working Memory Example**

For a travel booking agent, working memori fit hold di user's current request, like "I want to book a trip to Paris". Dis specific requirement dey for di agent immediate context to guide di current interaction.

#### Short Term Memory

Dis kind memori dey keep information for di duration of one conversation or session. Na di context of di current chat, e allow di agent refer back to earlier turns for di dialogue.

**Short Term Memory Example**

If user ask, "How much would a flight to Paris cost?" and later ask, "What about accommodation there?", short-term memori make sure di agent sabi say "there" mean "Paris" inside di same conversation.

#### Long Term Memory

Dis na information wey dey persist across many conversations or sessions. E allow agents remember user preferences, historical interactions, or general knowledge for long time. Na dis one dey important for personalization.

**Long Term Memory Example**

Long-term memori fit store say "Ben enjoys skiing and outdoor activities, likes coffee with a mountain view, and wants to avoid advanced ski slopes due to a past injury". Dis info, wey dem learn from earlier interactions, go influence recommendations for future travel planning, make dem very personalized.

#### Persona Memory

Dis special memori help agent get consistent "personality" or "persona". E allow agent remember details about itself or di role wey e suppose play, make interactions flow better and stay focused.

**Persona Memory Example**
If di travel agent design as "expert ski planner," persona memori go reinforce dat role, make answers follow expert tone and knowledge.

#### Workflow/Episodic Memory

Dis memori dey store di sequence of steps agent take during one complex task, including successes and failures. E be like remembering specific "episodes" or past experience to learn from dem.

**Episodic Memory Example**

If agent try book one flight but e fail because e no available, episodic memori fit record dis failure, so next time agent fit try alternative flights or tell user the issue for later attempt with better context.

#### Entity Memory

Dis one dey involve to extract and remember specific entities (people, places, or things) and events from conversations. E let agent build structured understanding of key elements wey dem talk about.

**Entity Memory Example**

From one conversation about past trip, agent fit extract "Paris," "Eiffel Tower," and "dinner at Le Chat Noir restaurant" as entities. For future interaction, agent fit recall "Le Chat Noir" and offer to make new reservation there.

#### Structured RAG (Retrieval Augmented Generation)

Even though RAG na broad technique, "Structured RAG" dey show as powerful memori technology. E dey extract dense, structured info from different sources (conversations, emails, images) and use am to improve precision, recall, and speed for responses. No be like classic RAG wey only rely on semantic similarity; Structured RAG dey work with di inherent structure of information.

**Structured RAG Example**

Instead of just matching keywords, Structured RAG fit parse flight details (destination, date, time, airline) from one email and store dem in structured way. Dis one allow precise queries like "What flight did I book to Paris on Tuesday?"

## Implementing and Storing Memory

To implement memori for AI agents, you go follow systematic process of **memory management**, wey include generating, storing, retrieving, integrating, updating, and even "forgetting" (or deleting) information. Retrieval na one especially important part.

### Specialized Memory Tools

#### Mem0

One way to store and manage agent memori na to use specialized tools like Mem0. Mem0 dey serve as persistent memori layer, make agents fit recall relevant interactions, store user preferences and factual context, and learn from successes and failures over time. Di idea na to turn stateless agents into stateful ones.

E dey work through **two-phase memory pipeline: extraction and update**. First, messages wey add to agent's thread go send go Mem0 service, wey go use LLM to summarize conversation history and extract new memories. After dat, LLM-driven update phase go decide whether to add, modify, or delete these memories, and dem go store am inside hybrid data store wey fit include vector, graph, and key-value databases. Dis system fit also support different memori types and fit include graph memory for managing relationships between entities.

#### Cognee

Another strong approach na to use **Cognee**, open-source semantic memori for AI agents wey dey transform structured and unstructured data into queryable knowledge graphs backed by embeddings. Cognee get **dual-store architecture** wey combine vector similarity search with graph relationships, make agents fit understand not just wetin similar but how concepts relate to each other.

E clear for **hybrid retrieval** wey blend vector similarity, graph structure, and LLM reasoning - from raw chunk lookup to graph-aware question answering. Di system maintain **living memory** wey dey evolve and grow while e still dey queryable as one connected graph, supporting both short-term session context and long-term persistent memori.

Di Cognee notebook tutorial ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) show how to build this unified memori layer, with practical examples of ingesting different data sources, visualizing the knowledge graph, and querying with different search strategies wey fit di agent needs.

### Storing Memory with RAG

Besides specialized memory tools like mem0 , you fit use strong search services like **Azure AI Search as a backend for storing and retrieving memories**, especially for structured RAG.

Dis one let you ground your agent's responses with your own data, make answers more relevant and accurate. Azure AI Search fit store user-specific travel memories, product catalogs, or any other domain-specific knowledge.

Azure AI Search get features like **Structured RAG**, wey sabi extract and retrieve dense, structured info from big datasets like conversation histories, emails, or even images. Dis one fit give "superhuman precision and recall" compared to traditional text chunking and embedding ways.

## Making AI Agents Self-Improve

Common pattern for self-improving agents na to introduce one **"knowledge agent"**. Dis separate agent dey observe di main conversation between di user and di primary agent. Di role na to:

1. **Identify valuable information**: Decide if any part of di conversation worth to save as general knowledge or specific user preference.

2. **Extract and summarize**: Distill di important learning or preference from di conversation.

3. **Store in a knowledge base**: Save this extracted info, often for vector database, so e fit retrieve am later.

4. **Augment future queries**: When user start new query, di knowledge agent go retrieve relevant stored info and append am to di user's prompt, give important context to di primary agent (like RAG).

### Optimizations for Memory

• **Latency Management**: To avoid slow down user interactions, you fit use one cheaper, faster model first to quickly check if info worth to store or retrieve, and only call di more complex extraction/retrieval process when necessary.

• **Knowledge Base Maintenance**: For large knowledge base, less-used info fit move go "cold storage" to manage cost.

## Got More Questions About Agent Memory?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet other learners, attend office hours and get your AI Agents questions answered.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Disclaimer:
Dis document don translate wit AI translation service Co-op Translator (https://github.com/Azure/co-op-translator). Even though we dey try make am correct, abeg sabi say automatic translations fit get errors or wrong parts. The original document for im own language suppose be the official source. If na important information, e better make professional human translator check am. We no dey liable for any misunderstanding or wrong interpretation wey fit come from use of this translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->