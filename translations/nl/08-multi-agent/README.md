[![Multi-Agent Design](../../../translated_images/nl/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Klik op de afbeelding hierboven om de video van deze les te bekijken)_

# Multi-agent ontwerppatronen

Zodra je begint te werken aan een project waarbij meerdere agents betrokken zijn, moet je rekening houden met het multi-agent ontwerppatroon. Het is echter misschien niet meteen duidelijk wanneer je moet overstappen op multi-agents en wat de voordelen zijn.

## Inleiding

In deze les willen we de volgende vragen beantwoorden:

- Voor welke scenario's zijn multi-agents toepasbaar?
- Wat zijn de voordelen van het gebruik van multi-agents ten opzichte van slechts één enkele agent die meerdere taken uitvoert?
- Wat zijn de bouwstenen voor het implementeren van het multi-agent ontwerppatroon?
- Hoe krijgen we inzicht in hoe de verschillende agents met elkaar omgaan?

## Leerdoelen

Na deze les zou je in staat moeten zijn om:

- Scenario's te identificeren waar multi-agents toepasbaar zijn
- De voordelen te herkennen van het gebruik van multi-agents in plaats van een enkele agent.
- De bouwstenen te begrijpen voor het implementeren van het multi-agent ontwerppatroon.

Wat is het grotere geheel?

*Multi agents zijn een ontwerppatroon dat meerdere agents toestaat samen te werken om een gemeenschappelijk doel te bereiken*.

Dit patroon wordt veel gebruikt in verschillende vakgebieden, waaronder robotica, autonome systemen en gedistribueerde computing.

## Scenario's Waar Multi-Agents Toepasbaar Zijn

Dus welke scenario's zijn een goede use case voor het gebruik van multi-agents? Het antwoord is dat er veel scenario's zijn waarbij het inzetten van meerdere agents voordelig is, vooral in de volgende gevallen:

- **Grote werklast**: Grote werklasten kunnen worden verdeeld in kleinere taken en toegewezen aan verschillende agents, wat parallelle verwerking en snellere voltooiing mogelijk maakt. Een voorbeeld hiervan is bij een grote dataverwerkingstaak.
- **Complexe taken**: Complexe taken, net als grote werklasten, kunnen worden opgesplitst in kleinere subtaken en toegewezen aan verschillende agents, die elk gespecialiseerd zijn in een specifiek aspect van de taak. Een goed voorbeeld hiervan is bij autonome voertuigen, waar verschillende agents navigatie, obstakeldetectie en communicatie met andere voertuigen beheren.
- **Diverse expertise**: Verschillende agents kunnen diverse expertise hebben, waardoor ze verschillende aspecten van een taak effectiever kunnen afhandelen dan één enkele agent. Voor dit geval is een goed voorbeeld in de gezondheidszorg, waar agents diagnosen, behandelplannen en patiëntmonitoring kunnen beheren.

## Voordelen van het Gebruik van Multi-Agents ten Opzichte van een Enkele Agent

Een enkel agentensysteem kan goed werken voor eenvoudige taken, maar voor complexere taken kan het gebruik van meerdere agents verschillende voordelen bieden:

- **Specialisatie**: Elke agent kan gespecialiseerd zijn in een specifieke taak. Het gebrek aan specialisatie in een enkele agent betekent dat je een agent hebt die alles kan doen, maar mogelijk in de war raakt over wat te doen bij een complexe taak. Het kan bijvoorbeeld een taak uitvoeren waarvoor het niet het beste geschikt is.
- **Schaalbaarheid**: Het is eenvoudiger om systemen te schalen door meer agents toe te voegen in plaats van één agent te overladen.
- **Fouttolerantie**: Als één agent faalt, kunnen anderen doorgaan met functioneren, wat de betrouwbaarheid van het systeem waarborgt.

Laten we een voorbeeld nemen, we boeken een reis voor een gebruiker. Een enkel agentensysteem zou alle aspecten van het reisboekingsproces moeten afhandelen, van het vinden van vluchten tot het boeken van hotels en huurauto's. Om dit met één enkele agent te bereiken, moet de agent hulpmiddelen hebben om al deze taken af te handelen. Dit kan leiden tot een complex en monolithisch systeem dat moeilijk te onderhouden en schalen is. Een multi-agent systeem daarentegen kan verschillende agents hebben die gespecialiseerd zijn in het vinden van vluchten, het boeken van hotels en huurauto's. Dit zou het systeem modulairder, gemakkelijker te onderhouden en schaalbaar maken.

Vergelijk dit met een reisbureau gerund als een familiebedrijf versus een reisbureau gerund als een franchise. Het familiebedrijf zou één agent hebben die alle aspecten van het reisboekingsproces afhandelt, terwijl de franchise verschillende agents zou hebben die verschillende aspecten van het reisboekingsproces afhandelen.

## Bouwstenen voor het Implementeren van het Multi-Agent Ontwerppatroon

Voordat je het multi-agent ontwerppatroon kunt implementeren, moet je de bouwstenen begrijpen die het patroon vormen.

Laten we dit concreter maken door opnieuw te kijken naar het voorbeeld van het boeken van een reis voor een gebruiker. In dit geval zouden de bouwstenen onder andere zijn:

- **Agentcommunicatie**: Agents voor het vinden van vluchten, het boeken van hotels en huurauto's moeten communiceren en informatie delen over de voorkeuren en beperkingen van de gebruiker. Je moet de protocollen en methoden voor deze communicatie bepalen. Concreet betekent dit dat de agent voor het vinden van vluchten moet communiceren met de agent voor het boeken van hotels om ervoor te zorgen dat het hotel wordt geboekt voor dezelfde data als de vlucht. Dat betekent dat de agents informatie moeten delen over de reisdata van de gebruiker, wat betekent dat je moet beslissen *welke agents info delen en hoe ze die info delen*.
- **Coördinatiemechanismen**: Agents moeten hun acties coördineren om ervoor te zorgen dat de voorkeuren en beperkingen van de gebruiker worden nageleefd. Een gebruikersvoorkeur kan zijn dat ze een hotel dicht bij het vliegveld willen, terwijl een beperking kan zijn dat huurauto's alleen beschikbaar zijn op het vliegveld. Dit betekent dat de agent voor het boeken van hotels moet coördineren met de agent voor het boeken van huurauto's om ervoor te zorgen dat de voorkeuren en beperkingen van de gebruiker worden nageleefd. Dit betekent dat je moet beslissen *hoe de agents hun acties coördineren*.
- **Agentarchitectuur**: Agents moeten de interne structuur hebben om beslissingen te nemen en te leren van hun interacties met de gebruiker. Dit betekent dat de agent voor het vinden van vluchten de interne structuur moet hebben om beslissingen te nemen over welke vluchten aan de gebruiker worden aanbevolen. Dit betekent dat je moet beslissen *hoe de agents beslissingen nemen en leren van hun interacties met de gebruiker*. Voorbeelden van hoe een agent leert en verbetert, kunnen zijn dat de agent voor het vinden van vluchten een machine learning-model gebruikt om vluchten aan de gebruiker aan te bevelen op basis van hun eerdere voorkeuren.
- **Inzicht in Multi-Agent Interacties**: Je moet inzicht hebben in hoe de verschillende agents met elkaar omgaan. Dit betekent dat je tools en technieken nodig hebt om de activiteiten en interacties van de agents te volgen. Dit kan in de vorm van logging- en monitoringtools, visualisatietools en prestatiemetingen.
- **Multi-Agent Patronen**: Er zijn verschillende patronen voor het implementeren van multi-agent systemen, zoals gecentraliseerde, gedecentraliseerde en hybride architecturen. Je moet het patroon kiezen dat het beste past bij jouw use case.
- **Mens in de lus**: In de meeste gevallen zal je een mens in de lus hebben en je moet de agents instrueren wanneer ze om menselijke tussenkomst moeten vragen. Dit kan in de vorm zijn van een gebruiker die vraagt om een specifiek hotel of vlucht die de agents niet hebben aanbevolen of om bevestiging voordat een vlucht of hotel wordt geboekt.

## Inzicht in Multi-Agent Interacties

Het is belangrijk dat je inzicht hebt in hoe de verschillende agents met elkaar omgaan. Dit inzicht is essentieel voor het debuggen, optimaliseren en waarborgen van de algehele effectiviteit van het systeem. Om dit te bereiken heb je tools en technieken nodig om de activiteiten en interacties van de agents te volgen. Dit kan in de vorm van logging- en monitoringtools, visualisatietools en prestatiestatistieken.

Bijvoorbeeld, in het geval van het boeken van een reis voor een gebruiker, kun je een dashboard hebben dat de status van elke agent toont, de voorkeuren en beperkingen van de gebruiker, en de interacties tussen agents. Dit dashboard kan de reisdata van de gebruiker tonen, de door de vluchtenagent aanbevolen vluchten, de door de hotelagent aanbevolen hotels, en de door de huurauto-agent aanbevolen huurauto's. Dit geeft je een duidelijk beeld van hoe de agents met elkaar omgaan en of de voorkeuren en beperkingen van de gebruiker worden nageleefd.

Laten we elk van deze aspecten wat uitgebreider bekijken.

- **Logging- en monitoringtools**: Je wilt voor elke actie die een agent uitvoert logging hebben. Een logboekitem kan informatie opslaan over de agent die de actie heeft uitgevoerd, de uitgevoerde actie, de tijd waarop de actie werd uitgevoerd en het resultaat van de actie. Deze informatie kan vervolgens worden gebruikt voor debuggen, optimaliseren en meer.
- **Visualisatietools**: Visualisatietools kunnen je helpen de interacties tussen agents op een meer intuïtieve manier te zien. Je zou bijvoorbeeld een grafiek kunnen hebben die de informatiestroom tussen agents toont. Dit kan helpen bij het identificeren van knelpunten, inefficiënties en andere problemen in het systeem.
- **Prestatiestatistieken**: Prestatiestatistieken kunnen je helpen de effectiviteit van het multi-agent systeem te volgen. Bijvoorbeeld, je zou de tijd kunnen volgen die nodig is om een taak te voltooien, het aantal taken dat per tijdseenheid is voltooid en de nauwkeurigheid van de aanbevelingen die door de agents worden gedaan. Deze informatie kan je helpen verbeterpunten te identificeren en het systeem te optimaliseren.

## Multi-Agent Patronen

Laten we enkele concrete patronen bekijken die we kunnen gebruiken om multi-agent apps te creëren. Hier zijn enkele interessante patronen die het overwegen waard zijn:

### Groepschat

Dit patroon is nuttig wanneer je een groepschatapplicatie wilt creëren waar meerdere agents met elkaar kunnen communiceren. Typische use cases voor dit patroon zijn teamcollaboratie, klantenondersteuning en sociale netwerken.

In dit patroon vertegenwoordigt elke agent een gebruiker in de groepschat en worden berichten uitgewisseld tussen agents met behulp van een berichtenprotocol. De agents kunnen berichten naar de groepschat sturen, berichten van de groepschat ontvangen en reageren op berichten van andere agents.

Dit patroon kan worden geïmplementeerd met een gecentraliseerde architectuur waarbij alle berichten via een centrale server worden geleid, of een gedecentraliseerde architectuur waarbij berichten rechtstreeks worden uitgewisseld.

![Group chat](../../../translated_images/nl/multi-agent-group-chat.ec10f4cde556babd.webp)

### Overdracht

Dit patroon is nuttig wanneer je een applicatie wilt creëren waarbij meerdere agents taken aan elkaar kunnen overdragen.

Typische use cases voor dit patroon zijn klantenondersteuning, taakbeheer en workflowautomatisering.

In dit patroon vertegenwoordigt elke agent een taak of een stap in een workflow, en kunnen agents taken overdragen aan andere agents op basis van vooraf gedefinieerde regels.

![Hand off](../../../translated_images/nl/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Samenwerkende filtering

Dit patroon is nuttig wanneer je een applicatie wilt creëren waarbij meerdere agents samenwerken om aanbevelingen te doen aan gebruikers.

De reden dat je meerdere agents wilt laten samenwerken is dat elke agent verschillende expertise kan hebben en op verschillende manieren kan bijdragen aan het aanbevelingsproces.

Laten we een voorbeeld nemen waarbij een gebruiker een aanbeveling wil over het beste aandeel om te kopen op de aandelenmarkt.

- **Industrie-expert**: Eén agent kan een expert zijn in een specifieke industrie.
- **Technische analyse**: Een andere agent kan een expert zijn in technische analyse.
- **Fundamentele analyse**: en een andere agent kan een expert zijn in fundamentele analyse. Door samen te werken, kunnen deze agents een meer complete aanbeveling doen aan de gebruiker.

![Recommendation](../../../translated_images/nl/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenario: Terugbetalingsproces

Overweeg een scenario waarin een klant een terugbetaling voor een product probeert te krijgen, er kunnen nogal wat agents betrokken zijn bij dit proces, maar laten we het verdelen tussen agents die specifiek voor dit proces zijn en algemene agents die in andere processen kunnen worden gebruikt.

**Agents specifiek voor het terugbetalingsproces**:

De volgende agents kunnen betrokken zijn bij het terugbetalingsproces:

- **Klantagent**: Deze agent vertegenwoordigt de klant en is verantwoordelijk voor het initiëren van het terugbetalingsproces.
- **Verkoper-agent**: Deze agent vertegenwoordigt de verkoper en is verantwoordelijk voor het verwerken van de terugbetaling.
- **Betaalagent**: Deze agent vertegenwoordigt het betaalproces en is verantwoordelijk voor het terugbetalen van de betaling van de klant.
- **Oplossingsagent**: Deze agent vertegenwoordigt het oplossingsproces en is verantwoordelijk voor het oplossen van eventuele problemen die tijdens het terugbetalingsproces ontstaan.
- **Compliance-agent**: Deze agent vertegenwoordigt het compliance-proces en is verantwoordelijk voor het waarborgen dat het terugbetalingsproces voldoet aan regelgeving en beleid.

**Algemene agents**:

Deze agents kunnen door andere delen van je bedrijf worden gebruikt.

- **Verzendagent**: Deze agent vertegenwoordigt het verzendproces en is verantwoordelijk voor het terugsturen van het product naar de verkoper. Deze agent kan zowel voor het terugbetalingsproces als voor het algemene verzenden van een product via een aankoop worden gebruikt.
- **Feedbackagent**: Deze agent vertegenwoordigt het feedbackproces en is verantwoordelijk voor het verzamelen van feedback van de klant. Feedback kan op elk moment worden gegeven en niet alleen tijdens het terugbetalingsproces.
- **Escalatie-agent**: Deze agent vertegenwoordigt het escalatieproces en is verantwoordelijk voor het escaleren van problemen naar een hoger niveau van ondersteuning. Dit type agent kan voor elk proces worden gebruikt waar je een probleem moet escaleren.
- **Notificatie-agent**: Deze agent vertegenwoordigt het notificatieproces en is verantwoordelijk voor het verzenden van meldingen aan de klant in verschillende fasen van het terugbetalingsproces.
- **Analytics-agent**: Deze agent vertegenwoordigt het analyseproces en is verantwoordelijk voor het analyseren van gegevens met betrekking tot het terugbetalingsproces.
- **Audit-agent**: Deze agent vertegenwoordigt het auditproces en is verantwoordelijk voor het auditen van het terugbetalingsproces om ervoor te zorgen dat het correct wordt uitgevoerd.
- **Rapportage-agent**: Deze agent vertegenwoordigt het rapportageproces en is verantwoordelijk voor het genereren van rapporten over het terugbetalingsproces.
- **Kennisagent**: Deze agent vertegenwoordigt het kennisproces en is verantwoordelijk voor het onderhouden van een kennisbasis met informatie over het terugbetalingsproces. Deze agent kan zowel kennis hebben over terugbetalingen als andere delen van je bedrijf.
- **Beveiligingsagent**: Deze agent vertegenwoordigt het beveiligingsproces en is verantwoordelijk voor het waarborgen van de beveiliging van het terugbetalingsproces.
- **Kwaliteitsagent**: Deze agent vertegenwoordigt het kwaliteitsproces en is verantwoordelijk voor het waarborgen van de kwaliteit van het terugbetalingsproces.

Er zijn nogal wat agents hierboven vermeld, zowel voor het specifieke terugbetalingsproces als voor de algemene agents die in andere delen van je bedrijf kunnen worden gebruikt. Hopelijk geeft dit je een idee hoe je kunt beslissen welke agents je gebruikt in je multi-agent systeem.

## Opdracht

Ontwerp een multi-agent systeem voor een klantenserviceproces. Identificeer de agents die betrokken zijn bij het proces, hun rollen en verantwoordelijkheden, en hoe ze met elkaar interageren. Overweeg zowel agents die specifiek zijn voor het klantenserviceproces als algemene agents die in andere delen van je bedrijf kunnen worden gebruikt.
> Denk er eens goed over na voordat je de volgende oplossing leest, je hebt misschien meer agenten nodig dan je denkt.

> TIP: Denk na over de verschillende fasen van het klantenondersteuningsproces en overweeg ook agenten die nodig zijn voor elk systeem.

## Oplossing

[Oplossing](./solution/solution.md)

## Kenniscontroles

Vraag: Wanneer moet je overwegen om meerdere agenten te gebruiken?

- [ ] A1: Wanneer je een kleine werklast en een eenvoudige taak hebt.
- [ ] A2: Wanneer je een grote werklast hebt
- [ ] A3: Wanneer je een eenvoudige taak hebt.

[Oplossingsquiz](./solution/solution-quiz.md)

## Samenvatting

In deze les hebben we gekeken naar het multi-agent ontwerp patroon, inclusief de scenario's waarin multi-agenten toepasbaar zijn, de voordelen van het gebruik van meerdere agenten ten opzichte van een enkele agent, de bouwstenen voor het implementeren van het multi-agent ontwerp patroon, en hoe je zicht kunt krijgen op hoe de meerdere agenten met elkaar samenwerken.

### Meer vragen over het Multi-Agent ontwerp patroon?

Sluit je aan bij de [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) om andere leerlingen te ontmoeten, deel te nemen aan spreekuren en je vragen over AI Agenten beantwoord te krijgen.

## Aanvullende bronnen

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen ontwerp patronen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentic ontwerp patronen</a>


## Vorige les

[Planning Ontwerp](../07-planning-design/README.md)

## Volgende les

[Metacognitie in AI Agenten](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Dit document is vertaald met behulp van de AI-vertalingsdienst [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel we streven naar nauwkeurigheid, dient u er rekening mee te houden dat automatische vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het originele document in de oorspronkelijke taal moet als de gezaghebbende bron worden beschouwd. Voor cruciale informatie wordt een professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortkomen uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->