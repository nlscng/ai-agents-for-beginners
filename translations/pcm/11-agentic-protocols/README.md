# How dem dey use Agentic Protocols (MCP, A2A and NLWeb)

[![Agentic Protocols](../../../translated_images/pcm/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Tap di picture wey dey above to watch dis lesson video)_

As people dey use AI agents more, e dey important say protocols dey wey go make standardization, security, and open innovation easy. For dis lesson, we go cover 3 protocols wey dey try meet dis need - Model Context Protocol (MCP), Agent to Agent (A2A) and Natural Language Web (NLWeb).

## Introduction

For dis lesson, we go cover:

• How **MCP** dey allow AI Agents to access external tools and data to complete wetin user want.

• How **A2A** dey enable communication and collaboration between different AI agents.

• How **NLWeb** dey bring natural language interfaces go any website make AI Agents fit discover and interact with di content.

## Learning Goals

• **Identify** di main purpose and benefits of MCP, A2A, and NLWeb for AI agents.

• **Explain** how each protocol dey help communication and interaction between LLMs, tools, and other agents.

• **Recognize** di different roles wey each protocol dey play for building complex agentic systems.

## Model Context Protocol

Di **Model Context Protocol (MCP)** na open standard wey provide standardized way for applications to give context and tools to LLMs. Dis one dey enable universal adaptor to different data sources and tools wey AI Agents fit connect to in consistent way.

Make we look di parts of MCP, di benefits compared to direct API use, and example of how AI agents fit use MCP server.

### MCP Core Components

MCP dey work on **client-server architecture** and di main parts be:

• **Hosts** na LLM applications (for example code editor like VSCode) wey dey start di connections to MCP Server.

• **Clients** na components inside di host application wey dey maintain one-to-one connections with servers.

• **Servers** na lightweight programs wey dey expose specific capabilities.

For di protocol, three core primitives dey wey be di capabilities of MCP Server:

• **Tools**: Na discrete actions or functions wey AI agent fit call to perform action. For example, weather service fit expose "get weather" tool, or e-commerce server fit expose "purchase product" tool. MCP servers dey advertise each tool's name, description, and input/output schema for their capabilities listing.

• **Resources**: Na read-only data items or documents wey MCP server fit provide, and clients fit retrieve dem when dem need am. Examples be file contents, database records, or log files. Resources fit be text (like code or JSON) or binary (like images or PDFs).

• **Prompts**: Na predefined templates wey dey give suggested prompts, make e easy for more complex workflows.

### Benefits of MCP

MCP get important advantages for AI Agents:

• **Dynamic Tool Discovery**: Agents fit dynamically receive list of available tools from server plus description of wetin dem do. Dis one different from traditional APIs wey dey require static coding for integrations, so any API change mean you go update code. MCP give "integrate once" approach, make e easier to adapt.

• **Interoperability Across LLMs**: MCP fit work across different LLMs, so you fit switch core models to test for better performance.

• **Standardized Security**: MCP get standard authentication method, e dey make scaling to add more MCP servers easier. E simpler pass to manage different keys and auth types for many traditional APIs.

### MCP Example

![MCP Diagram](../../../translated_images/pcm/mcp-diagram.e4ca1cbd551444a1.webp)

Imagine say user wan book flight using AI assistant wey MCP dey power.

1. **Connection**: Di AI assistant (di MCP client) connect to MCP server wey airline provide.

2. **Tool Discovery**: Di client ask airline MCP server, "Which tools una get?" Di server go respond with tools like "search flights" and "book flights".

3. **Tool Invocation**: You go tell AI assistant, "Please search for a flight from Portland to Honolulu." Di AI assistant, using im LLM, go understand say e need call "search flights" tool and pass correct parameters (origin, destination) to MCP server.

4. **Execution and Response**: Di MCP server, wey dey act as wrapper, go make di actual call to airline internal booking API. E go receive flight information (e.g., JSON data) and send am back to di AI assistant.

5. **Further Interaction**: Di AI assistant go show di flight options. When you choose flight, di assistant fit call "book flight" tool on same MCP server to finish di booking.

## Agent-to-Agent Protocol (A2A)

While MCP dey focus on connecting LLMs to tools, di **Agent-to-Agent (A2A) protocol** dey take am further by enabling communication and collaboration between different AI agents. A2A connect AI agents from different organizations, environments and tech stacks to do shared task.

We go look di components and benefits of A2A, plus example of how e fit work for our travel app.

### A2A Core Components

A2A dey enable communication between agents make dem work together to finish part of user task. Each component for di protocol dey help do this:

#### Agent Card

Like how MCP server dey share tool list, Agent Card get:
- Di Name of di Agent.
- A **description of di general tasks** wey e dey do.
- A **list of specific skills** with descriptions to help other agents (or even human users) sabi when and why to call dat agent.
- Di **current Endpoint URL** of di agent
- Di **version** and **capabilities** like streaming responses and push notifications.

#### Agent Executor

Agent Executor dey responsible for **pass di context of di user chat to di remote agent**, cos remote agent need am to understand di task wey dem wan make e do. For A2A server, agent dey use im own Large Language Model (LLM) to parse incoming requests and run tasks with im own internal tools.

#### Artifact

When remote agent don finish di requested task, dem go create work product as artifact. Artifact **contain di result of di agent's work**, **description of wetin dem complete**, and di **text context** wey dem send through di protocol. After artifact don send, connection with remote agent close until dem need am again.

#### Event Queue

Dis component dey handle **updates and passing messages**. E important for production so agentic systems no go close connection before task don finish, especially wen task fit take long time.

### Benefits of A2A

• **Enhanced Collaboration**: E allow agents from different vendors and platforms to interact, share context, and work together, make automation smooth across systems wey normally no dey connect.

• **Model Selection Flexibility**: Each A2A agent fit choose which LLM e go use to handle requests, so dem fit use optimized or fine-tuned models per agent, no be like one LLM connection wey some MCP setups get.

• **Built-in Authentication**: Authentication dey built into A2A protocol, so e provide strong security framework for agent interactions.

### A2A Example

![A2A Diagram](../../../translated_images/pcm/A2A-Diagram.8666928d648acc26.webp)

Make we expand our travel booking scenario, but dis time with A2A.

1. **User Request to Multi-Agent**: User talk to "Travel Agent" A2A client/agent, fit talk say, "Please book an entire trip to Honolulu for next week, including flights, a hotel, and a rental car".

2. **Orchestration by Travel Agent**: Travel Agent receive dis complex request. E use im LLM to reason about di task and decide say e need to call other specialized agents.

3. **Inter-Agent Communication**: Travel Agent use A2A protocol connect to downstream agents, like "Airline Agent," "Hotel Agent," and "Car Rental Agent" wey different companies create.

4. **Delegated Task Execution**: Travel Agent send specific tasks to dem specialized agents (e.g., "Find flights to Honolulu," "Book a hotel," "Rent a car"). Each specialized agent run their own LLMs and use their own tools (dem fit be MCP servers themselves) to do their part of di booking.

5. **Consolidated Response**: When all downstream agents don finish, Travel Agent go compile results (flight details, hotel confirmation, car rental booking) and send complete chat-style response back to user.

## Natural Language Web (NLWeb)

Websites don long be main way wey people dey access information and data for internet.

Make we look di different parts of NLWeb, di benefits of NLWeb and example how our NLWeb dey work for our travel application.

### Components of NLWeb

- **NLWeb Application (Core Service Code)**: Di system wey dey process natural language questions. E connect di different parts of di platform to create responses. You fit think am as di **engine wey power di natural language features** of website.

- **NLWeb Protocol**: Na **basic set of rules for natural language interaction** with website. E dey send responses back in JSON format (often using Schema.org). Di purpose na to build simple foundation for the “AI Web,” same way HTML make e possible to share documents online.

- **MCP Server (Model Context Protocol Endpoint)**: Each NLWeb setup still dey work as **MCP server**. Mean say e fit **share tools (like an “ask” method) and data** with other AI systems. For practice, dis one make website content and abilities usable by AI agents, make site become part of wider “agent ecosystem.”

- **Embedding Models**: Dem models dey convert website content into numerical representations wey dem dey call vectors (embeddings). Dem vectors dey capture meaning so computer fit compare and search. Dem store am for special database, and users fit choose which embedding model dem wan use.

- **Vector Database (Retrieval Mechanism)**: Dis database **store di embeddings of website content**. When person ask question, NLWeb go check di vector database to quickly find di most relevant info. E go give fast list of possible answers, ranked by similarity. NLWeb fit work with different vector storage systems like Qdrant, Snowflake, Milvus, Azure AI Search, and Elasticsearch.

### NLWeb by Example

![NLWeb](../../../translated_images/pcm/nlweb-diagram.c1e2390b310e5fe4.webp)

Think about our travel booking website again, but now e dey powered by NLWeb.

1. **Data Ingestion**: Travel website existing product catalogs (e.g., flight listings, hotel descriptions, tour packages) dem format with Schema.org or dem load via RSS feeds. NLWeb tools go ingest dis structured data, create embeddings, and store dem for local or remote vector database.

2. **Natural Language Query (Human)**: User enter website and instead of dey navigate menu, e type for chat interface: "Find me a family-friendly hotel in Honolulu with a pool for next week".

3. **NLWeb Processing**: NLWeb application receive di query. E send di query to LLM to understand am and at di same time search im vector database for relevant hotel listings.

4. **Accurate Results**: Di LLM help interpret search results from di database, pick di best matches based on "family-friendly," "pool," and "Honolulu" criteria, then format natural language response. Important thing be say di response refer to real hotels from website catalog, so e no go invent info.

5. **AI Agent Interaction**: Because NLWeb fit serve as MCP server, external AI travel agent fit also connect to this NLWeb instance. Di AI agent fit then use di `ask` MCP method to query di website directly: `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")`. NLWeb instance go process dis, use im database of restaurant information (if dem load am), and return structured JSON response.

### Got More Questions about MCP/A2A/NLWeb?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet other learners, attend office hours and get your AI Agents questions answered.

## Resources

- [MCP for Beginners](https://aka.ms/mcp-for-beginners)  
- [MCP Documentation](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb Repo](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel Guides](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Abeg note:

Dis document na AI translation wey Co-op Translator (https://github.com/Azure/co-op-translator) do. Even though we dey try make am correct, make you sabi sey automated translations fit get mistakes or no too correct. Di original document for im original language na di correct authority. If na important matter, better make you use professional human translator. We no dey responsible for any misunderstanding or wrong interpretation wey fit arise from dis translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->