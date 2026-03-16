# Používání Agentic Protocols (MCP, A2A and NLWeb)

[![Agentní protokoly](../../../translated_images/cs/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Klikněte na obrázek výše pro zhlédnutí videa této lekce)_

S rostoucím využíváním AI agentů roste i potřeba protokolů, které zajistí standardizaci, bezpečnost a podporu otevřené inovace. V této lekci pokryjeme 3 protokoly, které usilují o splnění této potřeby - Model Context Protocol (MCP), Agent to Agent (A2A) a Natural Language Web (NLWeb).

## Introduction

In this lesson, we will cover:

• How **MCP** allows AI Agents to access external tools and data to complete user tasks.

•  How **A2A** enables communication and collaboration between different AI agents.

• How **NLWeb** brings natural language interfaces to any website enabling AI Agents to discover and interact with the content.

## Learning Goals

• **Identify** the core purpose and benefits of MCP, A2A, and NLWeb in the context of AI agents.

• **Explain** how each protocol facilitates communication and interaction between LLMs, tools, and other agents.

• **Recognize** the distinct roles each protocol plays in building complex agentic systems.

## Model Context Protocol

The **Model Context Protocol (MCP)** is an open standard that provides standardized way for applications to provide context and tools to LLMs. This enables a "universal adaptor" to different data sources and tools that AI Agents can connect to in a consistent way.

Let’s look at the components of MCP, the benefits compared to direct API usage, and an example of how AI agents might use an MCP server.

### MCP Core Components

MCP operates on a **client-server architecture** and the core components are:

• **Hosts** are LLM applications (for example a code editor like VSCode) that start the connections to an MCP Server.

• **Clients** are components within the host application that maintain one-to-one connections with servers.

• **Servers** are lightweight programs that expose specific capabilities.

Included in the protocol are three core primitives which are the capabilities of an MCP Server:

• **Tools**: These are discrete actions or functions an AI agent can call to perform an action. For example, a weather service might expose a "get weather" tool, or an e-commerce server might expose a "purchase product" tool. MCP servers advertise each tool's name, description, and input/output schema in their capabilities listing.

• **Resources**: These are read-only data items or documents that an MCP server can provide, and clients can retrieve them on demand. Examples include file contents, database records, or log files. Resources can be text (like code or JSON) or binary (like images or PDFs).

• **Prompts**: These are predefined templates that provide suggested prompts, allowing for more complex workflows.

### Benefits of MCP

MCP offers significant advantages for AI Agents:

• **Dynamic Tool Discovery**: Agents can dynamically receive a list of available tools from a server along with descriptions of what they do. This contrasts with traditional APIs, which often require static coding for integrations, meaning any API change necessitates code updates. MCP offers an "integrate once" approach, leading to greater adaptability.

• **Interoperability Across LLMs**: MCP works across different LLMs, providing flexibility to switch core models to evaluate for better performance.

• **Standardized Security**: MCP includes a standard authentication method, improving scalability when adding access to additional MCP servers. This is simpler than managing different keys and authentication types for various traditional APIs.

### MCP Example

![Diagram MCP](../../../translated_images/cs/mcp-diagram.e4ca1cbd551444a1.webp)

Imagine a user wants to book a flight using an AI assistant powered by MCP.

1. **Connection**: The AI assistant (the MCP client) connects to an MCP server provided by an airline.

2. **Tool Discovery**: The client asks the airline's MCP server, "What tools do you have available?" The server responds with tools like "search flights" and "book flights".

3. **Tool Invocation**: You then ask the AI assistant, "Please search for a flight from Portland to Honolulu." The AI assistant, using its LLM, identifies that it needs to call the "search flights" tool and passes the relevant parameters (origin, destination) to the MCP server.

4. **Execution and Response**: The MCP server, acting as a wrapper, makes the actual call to the airline's internal booking API. It then receives the flight information (e.g., JSON data) and sends it back to the AI assistant.

5. **Further Interaction**: The AI assistant presents the flight options. Once you select a flight, the assistant might invoke the "book flight" tool on the same MCP server, completing the booking.

## Agent-to-Agent Protocol (A2A)

While MCP focuses on connecting LLMs to tools, the **Agent-to-Agent (A2A) protocol** takes it a step further by enabling communication and collaboration between different AI agents.  A2A connects AI agents across different organizations, environments and tech stacks to complete a shared task.

We’ll examine the components and benefits of A2A, along with an example of how it could be applied in our travel application.

### A2A Core Components

A2A focuses on enabling communication between agents and having them work together to complete a subtask of user. Each component of the protocol contributes to this:

#### Agent Card

Similar to how an MCP server shares a list of tools, an Agent Card has:
- Jméno agenta .
- A **popis obecných úkolů** které plní.
- A **seznam konkrétních dovedností** s popisy, které pomáhají ostatním agentům (nebo i lidským uživatelům) pochopit, kdy a proč by daného agenta volali.
- The **current Endpoint URL** of the agent
- The **version** and **capabilities** of the agent such as streaming responses and push notifications.

#### Agent Executor

The Agent Executor is responsible for **passing the context of the user chat to the remote agent**, the remote agent needs this to understand the task that needs to be completed. In an A2A server, an agent uses its own Large Language Model (LLM) to parse incoming requests and execute tasks using its own internal tools.

#### Artifact

Once a remote agent has completed the requested task, its work product is created as an artifact.  An artifact **contains the result of the agent's work**, a **description of what was completed**, and the **text context** that is sent through the protocol. After the artifact is sent, the connection with the remote agent is closed until it is needed again.

#### Event Queue

This component is used for **handling updates and passing messages**. It is particularly important in production for agentic systems to prevent the connection between agents from being closed before a task is completed, especially when task completion times can take a longer time.

### Benefits of A2A

• **Enhanced Collaboration**: It enables agents from different vendors and platforms to interact, share context, and work together, facilitating seamless automation across traditionally disconnected systems.

• **Model Selection Flexibility**: Each A2A agent can decide which LLM it uses to service its requests, allowing for optimized or fine-tuned models per agent, unlike a single LLM connection in some MCP scenarios.

• **Built-in Authentication**: Authentication is integrated directly into the A2A protocol, providing a robust security framework for agent interactions.

### A2A Example

![Diagram A2A](../../../translated_images/cs/A2A-Diagram.8666928d648acc26.webp)

Let's expand on our travel booking scenario, but this time using A2A.

1. **User Request to Multi-Agent**: A user interacts with a "Travel Agent" A2A client/agent, perhaps by saying, "Please book an entire trip to Honolulu for next week, including flights, a hotel, and a rental car".

2. **Orchestration by Travel Agent**: The Travel Agent receives this complex request. It uses its LLM to reason about the task and determine that it needs to interact with other specialized agents.

3. **Inter-Agent Communication**: The Travel Agent then uses the A2A protocol to connect to downstream agents, such as an "Airline Agent," a "Hotel Agent," and a "Car Rental Agent" that are created by different companies.

4. **Delegated Task Execution**: The Travel Agent sends specific tasks to these specialized agents (e.g., "Find flights to Honolulu," "Book a hotel," "Rent a car"). Each of these specialized agents, running their own LLMs and utilizing their own tools (which could be MCP servers themselves), performs its specific part of the booking.

5. **Consolidated Response**: Once all downstream agents complete their tasks, the Travel Agent compiles the results (flight details, hotel confirmation, car rental booking) and sends a comprehensive, chat-style response back to the user.

## Natural Language Web (NLWeb)

Websites have long been the primary way for users to access information and data across the internet.

Let us look at the different components of NLWeb, the benefits of NLWeb and an example how our NLWeb works by looking at our travel application.

### Components of NLWeb

- **NLWeb Application (Core Service Code)**: Systém, který zpracovává otázky v přirozeném jazyce. Spojuje různé části platformy, aby vytvářel odpovědi. Můžete si ho představit jako **motor, který pohání funkce přirozeného jazyka** webu.

- **NLWeb Protocol**: Toto je **základní sada pravidel pro interakci v přirozeném jazyce** s webovou stránkou. Vrací odpovědi ve formátu JSON (často se používá Schema.org). Jeho účelem je vytvořit jednoduchý základ pro „AI Web“, podobně jako HTML umožnilo sdílení dokumentů online.

- **MCP Server (Model Context Protocol Endpoint)**: Každé NLWeb nasazení funguje také jako **MCP server**. To znamená, že může **sdílet nástroje (jako metodu „ask“) a data** s jinými AI systémy. V praxi to umožňuje, aby se obsah a schopnosti webu staly použitelnými pro AI agenty a web se stal součástí širší „ekosystému agentů“.

- **Embedding Models**: Tyto modely se používají k **převedení obsahu webu do číselných reprezentací nazývaných vektory** (embeddings). Tyto vektory zachycují význam tak, aby je počítače mohly porovnávat a vyhledávat. Ukládají se do speciální databáze a uživatelé si mohou vybrat, který embedding model chtějí použít.

- **Vector Database (Retrieval Mechanism)**: Tato databáze **ukládá embeddingy obsahu webu**. Když někdo položí otázku, NLWeb prohledá vektorovou databázi, aby rychle našel nejrelevantnější informace. Vrací rychlý seznam možných odpovědí, seřazených podle podobnosti. NLWeb funguje s různými systémy pro ukládání vektorů, jako jsou Qdrant, Snowflake, Milvus, Azure AI Search a Elasticsearch.

### NLWeb by Example

![NLWeb](../../../translated_images/cs/nlweb-diagram.c1e2390b310e5fe4.webp)

Consider our travel booking website again, but this time, it's powered by NLWeb.

1. **Data Ingestion**: The travel website's existing product catalogs (e.g., flight listings, hotel descriptions, tour packages) are formatted using Schema.org or loaded via RSS feeds. NLWeb's tools ingest this structured data, create embeddings, and store them in a local or remote vector database.

2. **Natural Language Query (Human)**: A user visits the website and, instead of navigating menus, types into a chat interface: "Find me a family-friendly hotel in Honolulu with a pool for next week".

3. **NLWeb Processing**: The NLWeb application receives this query. It sends the query to an LLM for understanding and simultaneously searches its vector database for relevant hotel listings.

4. **Accurate Results**: The LLM helps to interpret the search results from the database, identify the best matches based on "family-friendly," "pool," and "Honolulu" criteria, and then formats a natural language response. Crucially, the response refers to actual hotels from the website's catalog, avoiding made-up information.

5. **AI Agent Interaction**: Because NLWeb serves as an MCP server, an external AI travel agent could also connect to this website's NLWeb instance. The AI agent could then use the `ask("Doporučuje hotel nějaké veganské restaurace v oblasti Honolulu?")` MCP method to query the website directly. The NLWeb instance would process this, leveraging its database of restaurant information (if loaded), and return a structured JSON response.

### Got More Questions about MCP/A2A/NLWeb?

Připojte se k [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) a setkejte se s ostatními studenty, navštivte office hours a nechte si zodpovědět své otázky ohledně AI agentů.

## Resources

- [MCP pro začátečníky](https://aka.ms/mcp-for-beginners)  
- [MCP Documentation](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Repo NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Průvodce Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Prohlášení o vyloučení odpovědnosti:
Tento dokument byl přeložen pomocí služby pro překlad založené na umělé inteligenci [Co-op Translator](https://github.com/Azure/co-op-translator). Ačkoli usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho originálním jazyce by měl být považován za autoritativní zdroj. Pro zásadní informace se doporučuje využít profesionální lidský překlad. Nejsme odpovědní za žádná nedorozumění nebo chybné výklady vyplývající z použití tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->