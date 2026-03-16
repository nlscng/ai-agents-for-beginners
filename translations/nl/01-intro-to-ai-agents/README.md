[![Introductie tot AI-agenten](../../../translated_images/nl/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Klik op de bovenstaande afbeelding om de video van deze les te bekijken)_


# Introductie tot AI-agenten en gebruiksscenario's

Welkom bij de "AI Agents for Beginners" cursus! Deze cursus biedt fundamentele kennis en praktijkvoorbeelden voor het bouwen van AI-agenten.

Sluit je aan bij de <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord-community</a> om andere cursisten en AI-agentbouwers te ontmoeten en vragen te stellen over deze cursus.

Om met deze cursus te beginnen, beginnen we met een beter begrip van wat AI-agenten zijn en hoe we ze kunnen gebruiken in de toepassingen en workflows die we bouwen.

## Introductie

Deze les behandelt:

- Wat zijn AI-agenten en wat zijn de verschillende typen agenten?
- Voor welke gebruiksscenario's zijn AI-agenten het meest geschikt en hoe kunnen ze ons helpen?
- Wat zijn enkele van de basisbouwstenen bij het ontwerpen van agentische oplossingen?

## Leerdoelen
Na het voltooien van deze les zou je in staat moeten zijn om:

- AI-agentconcepten te begrijpen en hoe ze verschillen van andere AI-oplossingen.
- AI-agenten zo efficiënt mogelijk toe te passen.
- Agentische oplossingen productief te ontwerpen voor zowel gebruikers als klanten.

## Definitie van AI-agenten en typen AI-agenten

### Wat zijn AI-agenten?

AI-agenten zijn **systemen** die **grote taalmodellen (LLMs)** in staat stellen **acties uit te voeren** door hun mogelijkheden uit te breiden door LLMs **toegang tot tools** en **kennis** te geven.

Laten we deze definitie opdelen in kleinere onderdelen:

- **Systeem** - Het is belangrijk om agenten niet alleen als één component te zien, maar als een systeem van vele componenten. Op basisniveau zijn de componenten van een AI-agent:
  - **Environment** - De gedefinieerde ruimte waarin de AI-agent opereert. Bijvoorbeeld, als we een reisboekings-AI-agent zouden hebben, kan de omgeving het reisboekingssysteem zijn dat de AI-agent gebruikt om taken te voltooien.
  - **Sensors** - Omgevingen bevatten informatie en geven feedback. AI-agenten gebruiken sensoren om deze informatie over de huidige staat van de omgeving te verzamelen en te interpreteren. In het voorbeeld van de reisboekingsagent kan het reisboekingssysteem informatie geven zoals hotelbeschikbaarheid of vluchtprijzen.
  - **Actuators** - Zodra de AI-agent de huidige staat van de omgeving ontvangt, bepaalt de agent voor de huidige taak welke actie moet worden uitgevoerd om de omgeving te veranderen. Voor de reisboekingsagent kan dit bijvoorbeeld het boeken van een beschikbare kamer voor de gebruiker zijn.

![Wat zijn AI-agenten?](../../../translated_images/nl/what-are-ai-agents.1ec8c4d548af601a.webp)

**Grote taalmodellen** - Het concept van agenten bestond al vóór de creatie van LLMs. Het voordeel van het bouwen van AI-agenten met LLMs is hun vermogen om menselijke taal en data te interpreteren. Dit vermogen stelt LLMs in staat om omgevingsinformatie te interpreteren en een plan te definiëren om de omgeving te veranderen.

**Acties uitvoeren** - Buiten AI-agentsystemen zijn LLMs beperkt tot situaties waarin de actie het genereren van inhoud of informatie is op basis van een gebruikersprompt. Binnen AI-agentsystemen kunnen LLMs taken uitvoeren door het verzoek van de gebruiker te interpreteren en tools te gebruiken die beschikbaar zijn in hun omgeving.

**Toegang tot tools** - Welke tools het LLM kan gebruiken, wordt bepaald door 1) de omgeving waarin het opereert en 2) de ontwikkelaar van de AI-agent. Voor ons reisagentvoorbeeld worden de tools van de agent beperkt door de bewerkingen die beschikbaar zijn in het boekingssysteem, en/of kan de ontwikkelaar de tooltoegang van de agent beperken tot vluchten.

**Geheugen+Kennis** - Geheugen kan kortetermijn zijn in de context van het gesprek tussen de gebruiker en de agent. Op de lange termijn, buiten de informatie die door de omgeving wordt geleverd, kunnen AI-agenten ook kennis ophalen uit andere systemen, services, tools en zelfs andere agenten. In het voorbeeld van de reisagent kan deze kennis bijvoorbeeld de informatie over de reisvoorkeuren van de gebruiker zijn, opgeslagen in een klantendatabase.

### De verschillende typen agenten

Nu we een algemene definitie van AI-agenten hebben, laten we enkele specifieke agenttypen bekijken en hoe ze toegepast zouden worden op een reisboekings-AI-agent.

| **Agenttype**                | **Beschrijving**                                                                                                                       | **Voorbeeld**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Eenvoudige reflexagenten**      | Voeren onmiddellijke acties uit op basis van vooraf gedefinieerde regels.                                                                                  | De reisagent interpreteert de context van de e-mail en stuurt reisklachten door naar de klantenservice.                                                                                                                          |
| **Modelgebaseerde reflexagenten** | Voeren acties uit op basis van een wereldmodel en wijzigingen in dat model.                                                              | De reisagent geeft prioriteit aan routes met significante prijswijzigingen op basis van toegang tot historische prijsgegevens.                                                                                                             |
| **Doelgerichte agenten**         | Maken plannen om specifieke doelen te bereiken door het doel te interpreteren en acties te bepalen om dat te bereiken.                                  | De reisagent boekt een reis door de noodzakelijke reisarrangementen (auto, openbaar vervoer, vluchten) te bepalen van de huidige locatie naar de bestemming.                                                                                |
| **Nut-gebaseerde agenten**      | Houden rekening met voorkeuren en wegen afwegingen numeriek om te bepalen hoe doelen te bereiken.                                               | De reisagent maximaliseert nut door gemak versus kosten af te wegen bij het boeken van reizen.                                                                                                                                          |
| **Leeragenten**           | Verbeteren zich in de loop van de tijd door te reageren op feedback en acties dienovereenkomstig aan te passen.                                                        | De reisagent verbetert door klantfeedback uit enquêtes na de reis te gebruiken om aanpassingen te doen aan toekomstige boekingen.                                                                                                               |
| **Hiërarchische agenten**       | Bestaan uit meerdere agenten in een gelaagd systeem, waarbij agenten op hoger niveau taken opdelen in subtaken voor agenten op lager niveau om te voltooien. | De reisagent annuleert een reis door de taak op te delen in subtaken (bijvoorbeeld specifieke boekingen annuleren) en agenten op lager niveau deze uit te laten voeren, die terugrapporteren aan de agent op hoger niveau.                                     |
| **Multi-agentensystemen (MAS)** | Agenten voltooien taken onafhankelijk, hetzij coöperatief of competitief.                                                           | Coöperatief: Meerdere agenten boeken specifieke reisdiensten zoals hotels, vluchten en entertainment. Competitief: Meerdere agenten beheren en concurreren over een gedeelde hotelboekingskalender om klanten in het hotel te plaatsen. |

## Wanneer AI-agenten te gebruiken

In de vorige sectie gebruikten we het reisagentvoorbeeld om uit te leggen hoe de verschillende typen agenten in verschillende scenario's van reisboekingen kunnen worden gebruikt. We zullen deze toepassing in de hele cursus blijven gebruiken.

Laten we kijken naar de soorten gebruiksscenario's waarbij AI-agenten het meest geschikt zijn:

![Wanneer AI-agenten te gebruiken?](../../../translated_images/nl/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Open-eindige problemen** - het LLM toestaan de benodigde stappen te bepalen om een taak te voltooien omdat dit niet altijd hardcoded in een workflow kan worden.
- **Meertrapsprocessen** - taken die een niveau van complexiteit vereisen waarbij de AI-agent tools of informatie over meerdere beurten moet gebruiken in plaats van éénmalige ophalen.  
- **Verbetering in de loop van de tijd** - taken waarbij de agent in de loop van de tijd kan verbeteren door feedback te ontvangen van zijn omgeving of gebruikers om zo betere bruikbaarheid te bieden.

We behandelen meer overwegingen bij het gebruik van AI-agenten in de les Building Trustworthy AI Agents.

## Basisprincipes van agentische oplossingen

### Agentontwikkeling

De eerste stap bij het ontwerpen van een AI-agentensysteem is het definiëren van de tools, acties en gedragingen. In deze cursus richten we ons op het gebruik van de **Azure AI Agent Service** om onze agenten te definiëren. Het biedt functies zoals:

- Selectie van open modellen zoals OpenAI, Mistral en Llama
- Gebruik van gelicentieerde data via providers zoals Tripadvisor
- Gebruik van gestandaardiseerde OpenAPI 3.0-tools

### Agentische patronen

Communicatie met LLMs gebeurt via prompts. Gegeven de semi-autonome aard van AI-agenten is het niet altijd mogelijk of vereist om het LLM handmatig opnieuw te prompten na een wijziging in de omgeving. We gebruiken **agentische patronen** die ons in staat stellen om het LLM over meerdere stappen op een meer schaalbare manier te prompten.

Deze cursus is verdeeld in enkele van de momenteel populaire agentische patronen.

### Agentische frameworks

Agentische frameworks stellen ontwikkelaars in staat om agentische patronen via code te implementeren. Deze frameworks bieden sjablonen, plugins en tools voor betere samenwerking tussen agenten. Deze voordelen zorgen voor betere observeerbaarheid en probleemoplossing van AI-agentensystemen.

In deze cursus verkennen we het onderzoeksgerichte AutoGen-framework en het productieklare Agent-framework van Semantic Kernel.

## Voorbeeldcode

- Python: [Agent-framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent-framework](./code_samples/01-dotnet-agent-framework.md)

## Nog vragen over AI-agenten?

Sluit je aan bij de [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) om andere cursisten te ontmoeten, kantooruren bij te wonen en je vragen over AI-agenten beantwoord te krijgen.

## Vorige les

[Course Setup](../00-course-setup/README.md)

## Volgende les

[Verkennen van agentische frameworks](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dit document is vertaald met behulp van de AI-vertalingsdienst [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel we streven naar nauwkeurigheid, dient u zich ervan bewust te zijn dat geautomatiseerde vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het originele document in de oorspronkelijke taal moet als de gezaghebbende bron worden beschouwd. Voor kritieke informatie wordt een professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->