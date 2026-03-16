[![Betrouwbare AI-Agenten](../../../translated_images/nl/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klik op de afbeelding hierboven om de video van deze les te bekijken)_

# Betrouwbare AI-Agenten bouwen

## Introductie

Deze les behandelt:

- Hoe veilige en effectieve AI-agenten te bouwen en implementeren
- Belangrijke beveiligingsoverwegingen bij het ontwikkelen van AI-agenten
- Hoe gegevens- en privacybescherming te waarborgen bij het ontwikkelen van AI-agenten

## Leerdoelen

Na het voltooien van deze les weet je hoe je:

- Risico’s kunt identificeren en beperken bij het creëren van AI-agenten
- Beveiligingsmaatregelen implementeert om ervoor te zorgen dat gegevens en toegang correct worden beheerd
- AI-agenten maakt die gegevensprivacy handhaven en een kwalitatieve gebruikerservaring bieden

## Veiligheid

Laten we eerst kijken naar het bouwen van veilige agentische toepassingen. Veiligheid betekent dat de AI-agent presteert zoals ontworpen. Als bouwers van agentische toepassingen hebben we methoden en tools om de veiligheid te maximaliseren:

### Een systeemberichtenframework bouwen

Als je ooit een AI-toepassing hebt gebouwd met Large Language Models (LLM’s), weet je hoe belangrijk het is om een robuuste systeemprompt of systeembericht te ontwerpen. Deze prompts stellen de meta regels, instructies en richtlijnen vast voor hoe het LLM met de gebruiker en data omgaat.

Voor AI-agenten is de systeemprompt nog belangrijker, omdat ze zeer specifieke instructies nodig hebben om de taken uit te voeren die we voor ze hebben ontworpen.

Om schaalbare systeemprompts te creëren, kunnen we een systeemberichtenframework gebruiken om een of meer agenten in onze applicatie te bouwen:

![Een systeemberichtenframework bouwen](../../../translated_images/nl/system-message-framework.3a97368c92d11d68.webp)

#### Stap 1: Maak een meta systeembericht

De meta prompt wordt door een LLM gebruikt om de systeemprompts voor de agenten die we maken te genereren. We ontwerpen het als een sjabloon, zodat we efficiënt meerdere agenten kunnen maken indien nodig.

Hier is een voorbeeld van een meta systeembericht dat we aan de LLM zouden geven:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Stap 2: Maak een basisprompt

De volgende stap is het maken van een basisprompt om de AI-agent te beschrijven. Je moet de rol van de agent, de taken die de agent zal uitvoeren en andere verantwoordelijkheden van de agent opnemen.

Hier is een voorbeeld:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Stap 3: Voorzie het basis systeembericht aan de LLM

Nu kunnen we dit systeembericht optimaliseren door het meta systeembericht als systeembericht te geven en ons basis systeembericht.

Dit zal een systeembericht opleveren dat beter is ontworpen om onze AI-agenten te begeleiden:

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

#### Stap 4: Itereren en verbeteren

De waarde van dit systeemberichtenframework is dat het makkelijker wordt om meerdere systeemberichten van verschillende agenten op te schalen en je systeemberichten in de loop der tijd te verbeteren. Het is zeldzaam dat je een systeembericht hebt dat de eerste keer werkt voor je volledige use case. Kleine aanpassingen en verbeteringen maken door het basis systeembericht te wijzigen en het door het systeem te laten lopen, stelt je in staat resultaten te vergelijken en evalueren.

## Inzicht in bedreigingen

Om betrouwbare AI-agenten te bouwen, is het belangrijk risico’s en bedreigingen voor je AI-agent te begrijpen en te beperken. Laten we kijken naar enkele verschillende bedreigingen voor AI-agenten en hoe je hier beter op kunt voorbereiden.

![Inzicht in bedreigingen](../../../translated_images/nl/understanding-threats.89edeada8a97fc0f.webp)

### Taak en instructie

**Beschrijving:** Aanvallers proberen de instructies of doelen van de AI-agent te wijzigen via prompting of manipulatie van inputs.

**Beperking:** Voer validatiecontroles en inputfilters uit om mogelijk gevaarlijke prompts te detecteren voordat ze door de AI-agent worden verwerkt. Omdat deze aanvallen meestal frequente interactie met de agent vereisen, is het beperken van het aantal beurten in een gesprek een andere manier om dit soort aanvallen te voorkomen.

### Toegang tot kritieke systemen

**Beschrijving:** Als een AI-agent toegang heeft tot systemen en diensten die gevoelige gegevens opslaan, kunnen aanvallers de communicatie tussen de agent en deze diensten compromitteren. Dit kan directe aanvallen zijn of indirecte pogingen om via de agent informatie over deze systemen te verkrijgen.

**Beperking:** AI-agenten dienen alleen toegang te hebben tot systemen op basis van noodzaak om dit soort aanvallen te voorkomen. Communicatie tussen de agent en het systeem moet ook veilig zijn. Authenticatie en toegangscontrole implementeren is een andere manier om deze informatie te beschermen.

### Overbelasting van bronnen en diensten

**Beschrijving:** AI-agenten kunnen verschillende tools en diensten benaderen om taken uit te voeren. Aanvallers kunnen deze mogelijkheid misbruiken om deze diensten aan te vallen door een groot aantal verzoeken via de AI-agent te sturen, wat kan leiden tot systeemstoringen of hoge kosten.

**Beperking:** Implementeer beleidsregels om het aantal verzoeken dat een AI-agent naar een dienst kan sturen te beperken. Het beperken van het aantal gespreksbeurten en verzoeken aan je AI-agent is een andere manier om dit soort aanvallen te voorkomen.

### Vergiftiging van de kennisbasis

**Beschrijving:** Dit type aanval richt zich niet direct op de AI-agent, maar op de kennisbasis en andere diensten die de AI-agent gebruikt. Dit kan betekenen dat de data of informatie die de AI-agent gebruikt om een taak uit te voeren, wordt gecorrumpeerd, wat leidt tot bevooroordeelde of ongewenste reacties aan de gebruiker.

**Beperking:** Voer regelmatig verificatie uit van de data die de AI-agent gebruikt in zijn workflows. Zorg ervoor dat de toegang tot deze data veilig is en alleen wordt gewijzigd door vertrouwde personen om dit type aanval te voorkomen.

### Cascaderende fouten

**Beschrijving:** AI-agenten gebruiken verschillende tools en diensten om taken uit te voeren. Fouten veroorzaakt door aanvallers kunnen leiden tot storingen in andere systemen waar de AI-agent mee verbonden is, waardoor de aanval zich verspreidt en moeilijker te verhelpen is.

**Beperking:** Een methode om dit te voorkomen is de AI-agent in een beperkte omgeving te laten opereren, bijvoorbeeld taken uitvoeren in een Docker-container, om directe systeemaanvallen te voorkomen. Het creëren van fallback-mechanismen en retry-logica wanneer systemen met een fout reageren, is een andere manier om grotere systeemstoringen te voorkomen.

## Mens in de lus

Een andere effectieve manier om betrouwbare AI-agent systemen te bouwen is het gebruik van een mens-in-de-lus. Dit creëert een flow waarbij gebruikers tijdens het proces feedback kunnen geven aan de agenten. Gebruikers fungeren als agenten binnen een multi-agent systeem en geven goedkeuring of beëindigen het lopende proces.

![Mens in de lus](../../../translated_images/nl/human-in-the-loop.5f0068a678f62f4f.webp)

Hier is een codevoorbeeld met AutoGen om te laten zien hoe dit concept wordt geïmplementeerd:

```python

# Maak de agenten aan.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Gebruik input() om gebruikersinvoer vanaf de console te krijgen.

# Maak de beëindigingsvoorwaarde die het gesprek zal beëindigen wanneer de gebruiker "APPROVE" zegt.
termination = TextMentionTermination("APPROVE")

# Maak het team aan.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Voer het gesprek uit en stroom naar de console.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Gebruik asyncio.run(...) bij het uitvoeren in een script.
await Console(stream)

```

## Conclusie

Het bouwen van betrouwbare AI-agenten vereist zorgvuldige ontwerpkeuzes, robuuste beveiligingsmaatregelen en continu itereren. Door gestructureerde meta prompt-systemen te implementeren, potentiële bedreigingen te begrijpen en mitigatiestrategieën toe te passen, kunnen ontwikkelaars AI-agenten maken die zowel veilig als effectief zijn. Daarnaast zorgt het integreren van een mens-in-de-lus aanpak ervoor dat AI-agenten in lijn blijven met de behoeften van gebruikers terwijl risico’s worden geminimaliseerd. Nu AI blijft evolueren, zal het behouden van een proactieve houding op het gebied van beveiliging, privacy en ethische overwegingen cruciaal zijn om vertrouwen en betrouwbaarheid in AI-gedreven systemen te bevorderen.

### Meer vragen over het bouwen van betrouwbare AI-agenten?

Word lid van de [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) om andere leerlingen te ontmoeten, deel te nemen aan kantooruren en je AI-agent vragen beantwoord te krijgen.

## Aanvullende bronnen

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Overzicht verantwoord gebruik van AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Evaluatie van generatieve AI-modellen en AI-toepassingen</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Veiligheidssysteemberichten</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Risicobeoordelingssjabloon</a>

## Vorige les

[Agentic RAG](../05-agentic-rag/README.md)

## Volgende les

[Planningsontwerppatroon](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dit document is vertaald met behulp van de AI-vertalingsdienst [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel wij streven naar nauwkeurigheid, dient u er rekening mee te houden dat geautomatiseerde vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het originele document in de oorspronkelijke taal geldt als de gezaghebbende bron. Voor kritische informatie wordt professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->