# Gebruik van agentische protocollen (MCP, A2A en NLWeb)

[![Agentische protocollen](../../../translated_images/nl/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Klik op de afbeelding hierboven om de video van deze les te bekijken)_

Naarmate het gebruik van AI-agenten toeneemt, groeit ook de behoefte aan protocollen die standaardisatie, beveiliging en open innovatie ondersteunen. In deze les behandelen we 3 protocollen die proberen aan deze behoefte te voldoen - Model Context Protocol (MCP), Agent to Agent (A2A) en Natural Language Web (NLWeb).

## Inleiding

In deze les behandelen we:

• Hoe **MCP** AI-agenten in staat stelt externe tools en gegevens te benaderen om gebruikers taken te laten voltooien.

•  Hoe **A2A** communicatie en samenwerking tussen verschillende AI-agenten mogelijk maakt.

• Hoe **NLWeb** natuurlijke-taalinterfaces naar elke website brengt, waardoor AI-agenten de inhoud kunnen ontdekken en ermee kunnen communiceren.

## Leerdoelen

• **Identificeer** het kerndoel en de voordelen van MCP, A2A en NLWeb in de context van AI-agenten.

• **Leg uit** hoe elk protocol communicatie en interactie tussen LLMs, tools en andere agenten faciliteert.

• **Herken** de onderscheidende rollen die elk protocol speelt bij het bouwen van complexe agentische systemen.

## Model Context Protocol

The **Model Context Protocol (MCP)** is an open standard that provides standardized way for applications to provide context and tools to LLMs. This enables a "universal adaptor" to different data sources and tools that AI Agents can connect to in a consistent way.

Laten we kijken naar de componenten van MCP, de voordelen vergeleken met direct API-gebruik, en een voorbeeld van hoe AI-agenten een MCP-server zouden kunnen gebruiken.

### Kerncomponenten van MCP

MCP opereert op een **client-serverarchitectuur** en de kerncomponenten zijn:

• **Hosts** zijn LLM-toepassingen (bijvoorbeeld een code-editor zoals VSCode) die de verbindingen naar een MCP-server starten.

• **Clients** zijn componenten binnen de hostapplicatie die één-op-één-verbindingen met servers onderhouden.

• **Servers** zijn lichtgewicht programma's die specifieke mogelijkheden blootstellen.

Opgenomen in het protocol zijn drie kernprimitieven die de mogelijkheden van een MCP-server vormen:

• **Tools**: Dit zijn afzonderlijke acties of functies die een AI-agent kan aanroepen om een handeling uit te voeren. Bijvoorbeeld, een weerservice kan een "get weather"-tool blootstellen, of een e-commerce server kan een "purchase product"-tool aanbieden. MCP-servers adverteren de naam, beschrijving en input/output-schema van elke tool in hun capabilities-lijst.

• **Resources**: Dit zijn alleen-lezen gegevensitems of documenten die een MCP-server kan bieden, en die clients op aanvraag kunnen ophalen. Voorbeelden zijn bestandsinhoud, databasegegevens of logbestanden. Resources kunnen tekst zijn (zoals code of JSON) of binair (zoals afbeeldingen of PDF's).

• **Prompts**: Dit zijn vooraf gedefinieerde sjablonen die voorgestelde prompts bieden, waardoor complexere workflows mogelijk worden.

### Voordelen van MCP

MCP biedt aanzienlijke voordelen voor AI-agenten:

• **Dynamic Tool Discovery**: Agenten kunnen dynamisch een lijst met beschikbare tools van een server ontvangen, samen met beschrijvingen van wat ze doen. Dit staat in contrast met traditionele API's, die vaak statische codering voor integraties vereisen, wat betekent dat elke API-wijziging code-updates nodig maakt. MCP biedt een "integreer-eenmaal"-benadering, wat leidt tot grotere aanpasbaarheid.

• **Interoperability Across LLMs**: MCP werkt met verschillende LLMs, wat flexibiliteit biedt om kernmodellen te wisselen om betere prestaties te evalueren.

• **Standardized Security**: MCP bevat een standaard authenticatiemethode, wat de schaalbaarheid verbetert bij het toevoegen van toegang tot extra MCP-servers. Dit is eenvoudiger dan het beheren van verschillende sleutels en authenticatietypes voor diverse traditionele API's.

### MCP Example

![MCP-diagram](../../../translated_images/nl/mcp-diagram.e4ca1cbd551444a1.webp)

Stel je voor dat een gebruiker een vlucht wil boeken met een AI-assistent die draait op MCP.

1. **Connection**: De AI-assistent (de MCP-client) maakt verbinding met een MCP-server geleverd door een luchtvaartmaatschappij.

2. **Tool Discovery**: De client vraagt aan de MCP-server van de luchtvaartmaatschappij: "Welke tools heeft u beschikbaar?" De server antwoordt met tools zoals "search flights" en "book flights".

3. **Tool Invocation**: Je vraagt de AI-assistent vervolgens: "Zoek alstublieft een vlucht van Portland naar Honolulu." De AI-assistent, met behulp van zijn LLM, identificeert dat hij de "search flights"-tool moet aanroepen en geeft de relevante parameters (vertrek, bestemming) door aan de MCP-server.

4. **Execution and Response**: De MCP-server, fungerend als een wrapper, maakt de daadwerkelijke oproep naar de interne boekings-API van de luchtvaartmaatschappij. Vervolgens ontvangt hij de vluchtinformatie (bijv. JSON-data) en stuurt deze terug naar de AI-assistent.

5. **Further Interaction**: De AI-assistent presenteert de vluchtopties. Zodra je een vlucht selecteert, kan de assistent mogelijk de "book flight"-tool aanroepen op dezelfde MCP-server, waarmee de boeking wordt voltooid.

## Agent-to-Agent Protocol (A2A)

While MCP focuses on connecting LLMs to tools, the **Agent-to-Agent (A2A) protocol** takes it a step further by enabling communication and collaboration between different AI agents.  A2A connects AI agents across different organizations, environments and tech stacks to complete a shared task.

We’ll examine the components and benefits of A2A, along with an example of how it could be applied in our travel application.

### A2A Core Components

A2A focuses on enabling communication between agents and having them work together to complete a subtask of user. Each component of the protocol contributes to this:

#### Agent Card

Similar to how an MCP server shares a list of tools, an Agent Card has:
- The Name of the Agent .
- A **description of the general tasks** it completes.
- A **list of specific skills** with descriptions to help other agents (or even human users) understand when and why they would want to call that agent.
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

![A2A-diagram](../../../translated_images/nl/A2A-Diagram.8666928d648acc26.webp)

Let's expand on our travel booking scenario, but this time using A2A.

1. **User Request to Multi-Agent**: A user interacts with a "Travel Agent" A2A client/agent, perhaps by saying, "Boek alsjeblieft een hele reis naar Honolulu voor volgende week, inclusief vluchten, een hotel en een huurauto".

2. **Orchestration by Travel Agent**: The Travel Agent receives this complex request. It uses its LLM to reason about the task and determine that it needs to interact with other specialized agents.

3. **Inter-Agent Communication**: The Travel Agent then uses the A2A protocol to connect to downstream agents, such as an "Airline Agent," a "Hotel Agent," and a "Car Rental Agent" that are created by different companies.

4. **Delegated Task Execution**: The Travel Agent sends specific tasks to these specialized agents (e.g., "Find flights to Honolulu," "Book a hotel," "Rent a car"). Each of these specialized agents, running their own LLMs and utilizing their own tools (which could be MCP servers themselves), performs its specific part of the booking.

5. **Consolidated Response**: Once all downstream agents complete their tasks, the Travel Agent compiles the results (flight details, hotel confirmation, car rental booking) and sends a comprehensive, chat-style response back to the user.

## Natural Language Web (NLWeb)

Websites have long been the primary way for users to access information and data across the internet.

Laten we kijken naar de verschillende componenten van NLWeb, de voordelen van NLWeb en een voorbeeld van hoe onze NLWeb werkt door naar onze reisapplicatie te kijken.

### Componenten van NLWeb

- **NLWeb Application (Core Service Code)**: Het systeem dat natuurlijke-taalvragen verwerkt. Het verbindt de verschillende delen van het platform om antwoorden te genereren. Je kunt het zien als de **motor die de natuurlijke-taalfuncties** van een website aandrijft.

- **NLWeb Protocol**: Dit is een **basisset regels voor natuurlijke-taalinteractie** met een website. Het stuurt antwoorden terug in JSON-formaat (vaak gebruikmakend van Schema.org). Het doel is om een eenvoudige basis te creëren voor het “AI Web,” op dezelfde manier waarop HTML het mogelijk maakte documenten online te delen.

- **MCP Server (Model Context Protocol Endpoint)**: Elke NLWeb-setup fungeert ook als een **MCP-server**. Dit betekent dat het **tools kan delen (zoals een “ask”-methode) en data** met andere AI-systemen. In de praktijk maakt dit de inhoud en mogelijkheden van de website bruikbaar voor AI-agenten, waardoor de site deel kan uitmaken van het bredere “agent ecosystem.”

- **Embedding Models**: Deze modellen worden gebruikt om **website-inhoud te converteren naar numerieke representaties die vectors worden genoemd** (embeddings). Deze vectors vangen betekenis op een manier waarop computers kunnen vergelijken en zoeken. Ze worden opgeslagen in een speciale database, en gebruikers kunnen kiezen welk embedmodel ze willen gebruiken.

- **Vector Database (Retrieval Mechanism)**: Deze database **slaat de embeddings van de website-inhoud op**. Wanneer iemand een vraag stelt, controleert NLWeb de vectordatabase om snel de meest relevante informatie te vinden. Het geeft een snelle lijst met mogelijke antwoorden, gerangschikt op overeenkomst. NLWeb werkt met verschillende vectoropslagsystemen zoals Qdrant, Snowflake, Milvus, Azure AI Search en Elasticsearch.

### NLWeb by Example

![NLWeb](../../../translated_images/nl/nlweb-diagram.c1e2390b310e5fe4.webp)

Consider our travel booking website again, but this time, it's powered by NLWeb.

1. **Data Ingestion**: The travel website's existing product catalogs (e.g., flight listings, hotel descriptions, tour packages) are formatted using Schema.org or loaded via RSS feeds. NLWeb's tools ingest this structured data, create embeddings, and store them in a local or remote vector database.

2. **Natural Language Query (Human)**: A user visits the website and, instead of navigating menus, types into a chat interface: "Zoek voor mij een gezinsvriendelijk hotel in Honolulu met een zwembad voor volgende week".

3. **NLWeb Processing**: The NLWeb application receives this query. It sends the query to an LLM for understanding and simultaneously searches its vector database for relevant hotel listings.

4. **Accurate Results**: The LLM helps to interpret the search results from the database, identify the best matches based on "gezinsvriendelijk," "zwembad," and "Honolulu" criteria, and then formats a natural language response. Crucially, the response refers to actual hotels from the website's catalog, avoiding made-up information.

5. **AI Agent Interaction**: Because NLWeb serves as an MCP server, an external AI travel agent could also connect to this website's NLWeb instance. The AI agent could then use the `ask` MCP method to query the website directly: `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")`. The NLWeb instance would process this, leveraging its database of restaurant information (if loaded), and return a structured JSON response.

### Nog meer vragen over MCP/A2A/NLWeb?

Sluit je aan bij de [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) om andere cursisten te ontmoeten, naar spreekuren te gaan en je vragen over AI-agenten beantwoord te krijgen.

## Bronnen

- [MCP for Beginners](https://aka.ms/mcp-for-beginners)  
- [MCP Documentation](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb Repo](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel Guides](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dit document is vertaald met behulp van de AI-vertaalservice [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel we streven naar nauwkeurigheid, houd er rekening mee dat geautomatiseerde vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het originele document in de oorspronkelijke taal dient als gezaghebbende bron te worden beschouwd. Voor cruciale informatie wordt een professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->