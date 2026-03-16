# Geheugen voor AI-agenten 
[![Agentgeheugen](../../../translated_images/nl/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

When discussing the unique benefits of creating AI Agents, two things are mainly discussed: the ability to call tools to complete tasks and the ability to improve over time. Memory is at the foundation of creating self-improving agent that can create better experiences for our users.

In this lesson, we will look at what memory is for AI Agents and how we can manage it and use it for the benefit of our applications.

## Introductie

This lesson will cover:

• **Geheugen van AI-agenten begrijpen**: Wat geheugen is en waarom het essentieel is voor agenten.

• **Implementeren en opslaan van geheugen**: Praktische methoden om geheugenmogelijkheden toe te voegen aan je AI-agenten, met de nadruk op kortetermijn- en langetermijngeheugen.

• **AI-agenten zelfverbeterend maken**: Hoe geheugen agenten in staat stelt te leren van eerdere interacties en in de loop van de tijd te verbeteren.

## Beschikbare implementaties

This lesson includes two comprehensive notebook tutorials:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementeert geheugen met behulp van Mem0 en Azure AI Search binnen het Semantic Kernel-framework

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementeert gestructureerd geheugen met Cognee, bouwt automatisch een kennisgrafiek gebaseerd op embeddings, visualiseert de grafiek en biedt intelligente opvraging

## Leerdoelen

After completing this lesson, you will know how to:

• **Onderscheid maken tussen verschillende typen geheugen van AI-agenten**, inclusief werkgeheugen, kortetermijn- en langetermijngeheugen, evenals gespecialiseerde vormen zoals persona- en episodisch geheugen.

• **Implementeren en beheren van kortetermijn- en langetermijngeheugen voor AI-agenten** met behulp van het Semantic Kernel-framework, gebruikmakend van tools zoals Mem0, Cognee, Whiteboard memory, en integratie met Azure AI Search.

• **Begrijpen van de principes achter zelfverbeterende AI-agenten** en hoe robuuste systemen voor geheugenbeheer bijdragen aan continu leren en aanpassing.

## Het geheugen van AI-agenten begrijpen

In de kern, **verwijst geheugen voor AI-agenten naar de mechanismen die hen in staat stellen informatie te bewaren en op te roepen**. Deze informatie kan specifieke details zijn over een gesprek, gebruikersvoorkeuren, eerdere acties of zelfs aangeleerde patronen.

Zonder geheugen zijn AI-toepassingen vaak stateless, wat betekent dat elke interactie vanaf nul begint. Dit leidt tot een repetitieve en frustrerende gebruikerservaring waarbij de agent "vergeet" wat er eerder is besproken of wat de voorkeuren waren.

### Waarom is geheugen belangrijk?

De intelligentie van een agent is nauw verbonden met zijn vermogen om eerdere informatie te herinneren en te gebruiken. Geheugen stelt agenten in staat om:

• **Reflectief**: Leren van eerdere acties en uitkomsten.

• **Interactief**: Context behouden tijdens een lopend gesprek.

• **Proactief en reactief**: Behoeften anticiperen of passend reageren op basis van historische gegevens.

• **Autonoom**: Zelfstandiger functioneren door te putten uit opgeslagen kennis.

Het doel van het implementeren van geheugen is agenten meer **betrouwbaar en bekwaam** te maken.

### Soorten geheugen

#### Werkgeheugen

Zie dit als een kladpapiertje dat een agent gebruikt tijdens een enkele, lopende taak of denkproces. Het bevat directe informatie die nodig is om de volgende stap te berekenen.

Voor AI-agenten vangt werkgeheugen vaak de meest relevante informatie uit een gesprek op, zelfs als de volledige chatgeschiedenis lang is of wordt afgekapt. Het richt zich op het extraheren van sleutelelementen zoals vereisten, voorstellen, beslissingen en acties.

**Voorbeeld Werkgeheugen**

In een reisboekingsagent kan het werkgeheugen het huidige verzoek van de gebruiker vastleggen, zoals "I want to book a trip to Paris". Deze specifieke vereiste wordt in de onmiddellijke context van de agent gehouden om de huidige interactie te sturen.

#### Kortetermijngeheugen

Dit type geheugen bewaart informatie voor de duur van één gesprek of sessie. Het is de context van de huidige chat, waardoor de agent kan terugverwijzen naar vorige beurten in de dialoog.

**Voorbeeld Kortetermijngeheugen**

Als een gebruiker vraagt: "How much would a flight to Paris cost?" en vervolgens doorgaat met "What about accommodation there?", zorgt het kortetermijngeheugen ervoor dat de agent weet dat "there" verwijst naar "Paris" binnen hetzelfde gesprek.

#### Langetermijngeheugen

Dit is informatie die voortduurt over meerdere gesprekken of sessies. Het stelt agenten in staat gebruikersvoorkeuren, historische interacties of algemene kennis over langere periodes te onthouden. Dit is belangrijk voor personalisatie.

**Voorbeeld Langetermijngeheugen**

Een langetermijngeheugen kan opslaan dat "Ben enjoys skiing and outdoor activities, likes coffee with a mountain view, and wants to avoid advanced ski slopes due to a past injury". Deze informatie, geleerd uit eerdere interacties, beïnvloedt aanbevelingen in toekomstige reisplanningssessies en maakt ze zeer gepersonaliseerd.

#### Persona-geheugen

Dit gespecialiseerde geheugentype helpt een agent een consistente "persoonlijkheid" of "persona" te ontwikkelen. Het stelt de agent in staat details over zichzelf of zijn bedoelde rol te onthouden, waardoor interacties vloeiender en gerichter worden.

**Voorbeeld Persona-geheugen**
Als de reisagent is ontworpen als een "expert ski planner," kan persona-geheugen deze rol versterken en de reacties van de agent afstemmen op de toon en kennis van een expert.

#### Workflow/episodisch geheugen

Dit geheugen slaat de volgorde van stappen op die een agent neemt tijdens een complexe taak, inclusief successen en mislukkingen. Het is alsof specifieke "episodes" of ervaringen worden onthouden om ervan te leren.

**Voorbeeld Episodisch geheugen**

Als de agent heeft geprobeerd een specifieke vlucht te boeken maar dat mislukte door onbeschikbaarheid, kan het episodisch geheugen deze mislukking registreren, waardoor de agent alternatieve vluchten kan proberen of de gebruiker bij een volgende poging beter kan informeren over het probleem.

#### Entiteitengeheugen

Dit omvat het extraheren en onthouden van specifieke entiteiten (zoals personen, plaatsen of dingen) en gebeurtenissen uit gesprekken. Het stelt de agent in staat een gestructureerd begrip op te bouwen van belangrijke besproken elementen.

**Voorbeeld Entiteitengeheugen**

Uit een gesprek over een eerdere reis kan de agent "Paris," "Eiffel Tower," en "dinner at Le Chat Noir restaurant" extraheren als entiteiten. In een toekomstige interactie kan de agent "Le Chat Noir" herinneren en aanbieden daar een nieuwe reservering te maken.

#### Gestructureerde RAG (Retrieval Augmented Generation)

Hoewel RAG een bredere techniek is, wordt "Gestructureerde RAG" benadrukt als een krachtige geheugenstechnologie. Het extraheert dicht, gestructureerd informatie uit verschillende bronnen (gesprekken, e-mails, afbeeldingen) en gebruikt deze om precisie, recall en snelheid in antwoorden te verbeteren. In tegenstelling tot klassieke RAG die alleen op semantische gelijkenis vertrouwt, werkt Gestructureerde RAG met de inherente structuur van informatie.

**Voorbeeld Gestructureerde RAG**

In plaats van alleen trefwoorden te matchen, kan Gestructureerde RAG vluchtgegevens (bestemming, datum, tijd, luchtvaartmaatschappij) uit een e-mail parsen en deze opslaan op een gestructureerde manier. Dit maakt precieze zoekopdrachten mogelijk zoals "What flight did I book to Paris on Tuesday?"

## Implementatie en opslag van geheugen

Het implementeren van geheugen voor AI-agenten omvat een systematisch proces van **geheugenbeheer**, dat het genereren, opslaan, ophalen, integreren, bijwerken en zelfs "vergeten" (of verwijderen) van informatie omvat. Ophalen is een bijzonder cruciaal aspect.

### Gespecialiseerde geheugenhulpmiddelen

#### Mem0

Een manier om agentgeheugen op te slaan en te beheren is het gebruik van gespecialiseerde tools zoals Mem0. Mem0 werkt als een persistent geheugenniveau, waardoor agenten relevante interacties kunnen herinneren, gebruikersvoorkeuren en feitelijke context kunnen opslaan en kunnen leren van successen en mislukkingen in de loop van de tijd. Het idee hier is dat stateless agenten veranderen in stateful agenten.

Het werkt via een **tweepasig geheugenpipeline: extractie en update**. Eerst worden berichten die aan de thread van een agent worden toegevoegd naar de Mem0-service gestuurd, die een Large Language Model (LLM) gebruikt om de gesprekshistorie samen te vatten en nieuwe herinneringen te extraheren. Vervolgens bepaalt een LLM-gestuurde updatefase of deze herinneringen moeten worden toegevoegd, gewijzigd of verwijderd, en slaat ze ze op in een hybride datastore die vector-, graf- en key-value-databases kan omvatten. Dit systeem ondersteunt ook verschillende geheugentypes en kan grafgeheugen opnemen voor het beheren van relaties tussen entiteiten.

#### Cognee

Een andere krachtige benadering is het gebruik van **Cognee**, een open-source semantisch geheugen voor AI-agenten dat gestructureerde en ongestructureerde data transformeert in doorzoekbare kennisgrafieken die worden ondersteund door embeddings. Cognee biedt een **dual-store architectuur** die vector-zoekopdrachten combineert met grafrelaties, waardoor agenten niet alleen begrijpen welke informatie vergelijkbaar is, maar ook hoe concepten zich tot elkaar verhouden.

Het blinkt uit in **hybride opvraging** die vectorvergelijking, grafstructuur en LLM-redenering combineert - van ruwe chunk-opzoeking tot graf-bewuste vraagbeantwoording. Het systeem onderhoudt **levend geheugen** dat evolueert en groeit terwijl het als één verbonden graf doorzoekbaar blijft, en ondersteunt zowel kortetermijnsessiecontext als langetermijn persistent geheugen.

The Cognee notebook tutorial ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstrates building this unified memory layer, with practical examples of ingesting diverse data sources, visualizing the knowledge graph, and querying with different search strategies tailored to specific agent needs.

### Geheugen opslaan met RAG

Beyond specialized memory tools like mem0 , you can leverage robust search services like **Azure AI Search as a backend for storing and retrieving memories**, especially for structured RAG.

This allows you to ground your agent's responses with your own data, ensuring more relevant and accurate answers. Azure AI Search can be used to store user-specific travel memories, product catalogs, or any other domain-specific knowledge.

Azure AI Search supports capabilities like **Structured RAG**, which excels at extracting and retrieving dense, structured information from large datasets like conversation histories, emails, or even images. This provides "superhuman precision and recall" compared to traditional text chunking and embedding approaches.

## AI-agenten zelfverbeterend maken

A common pattern for self-improving agents involves introducing a **"kennisagent"**. This separate agent observes the main conversation between the user and the primary agent. Its role is to:

1. Identify valuable information: Determine if any part of the conversation is worth saving as general knowledge or a specific user preference.

2. Extract and summarize: Distill the essential learning or preference from the conversation.

3. Store in a knowledge base: Persist this extracted information, often in a vector database, so it can be retrieved later.

4. Augment future queries: When the user initiates a new query, the knowledge agent retrieves relevant stored information and appends it to the user's prompt, providing crucial context to the primary agent (similar to RAG).

### Optimalisaties voor geheugen

• **Latentiebeheer**: Om te voorkomen dat gebruikersinteracties vertragen, kan aanvankelijk een goedkoper, sneller model worden gebruikt om snel te controleren of informatie waardevol is om op te slaan of op te halen, en alleen het complexere extractie-/ophaalproces aanroepen wanneer dat nodig is.

• **Onderhoud van de kennisbasis**: Voor een groeiende kennisbasis kan minder vaak gebruikte informatie naar "cold storage" worden verplaatst om kosten te beheren.

## Nog meer vragen over agentgeheugen?

Sluit je aan bij de [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) om andere leerlingen te ontmoeten, spreekuren bij te wonen en antwoorden op je vragen over AI-agenten te krijgen.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Disclaimer:
Dit document is vertaald met behulp van de AI-vertalingsdienst Co-op Translator (https://github.com/Azure/co-op-translator). Hoewel we naar nauwkeurigheid streven, dient u er rekening mee te houden dat geautomatiseerde vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het originele document in de oorspronkelijke taal dient als gezaghebbende bron te worden beschouwd. Voor kritieke informatie wordt een professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor enige misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->