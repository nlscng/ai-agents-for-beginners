[![Introduktion till AI-agenter](../../../translated_images/sv/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Klicka på bilden ovan för att se videon till den här lektionen)_


# Introduktion till AI-agenter och agentanvändningsfall

Välkommen till kursen "AI-agenter för nybörjare"! Denna kurs ger grundläggande kunskap och praktiska exempel för att bygga AI-agenter.

Gå med i <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord-community</a> för att träffa andra deltagare och AI-agentbyggare och ställa eventuella frågor om den här kursen.

För att påbörja kursen börjar vi med att få en bättre förståelse för vad AI-agenter är och hur vi kan använda dem i de applikationer och arbetsflöden vi bygger.

## Introduktion

Denna lektion täcker:

- Vad är AI-agenter och vilka olika typer av agenter finns det?
- Vilka användningsfall passar bäst för AI-agenter och hur kan de hjälpa oss?
- Vilka är några av de grundläggande byggstenarna när man utformar agentiska lösningar?

## Lärandemål
Efter att ha slutfört denna lektion bör du kunna:

- Förstå konceptet AI-agenter och hur de skiljer sig från andra AI-lösningar.
- Tillämpa AI-agenter på ett så effektivt sätt som möjligt.
- Utforma agentiska lösningar produktivt för både användare och kunder.

## Definition av AI‑agenter och typer av AI‑agenter

### Vad är AI‑agenter?

AI‑agenter är **system** som möjliggör för **Large Language Models(LLMs)** att **utföra åtgärder** genom att utöka deras kapaciteter genom att ge LLM:er **åtkomst till verktyg** och **kunskap**.

Låt oss dela upp denna definition i mindre delar:

- **System** - Det är viktigt att se agenter inte bara som en enskild komponent utan som ett system av många komponenter. På grundläggande nivå är komponenterna i en AI‑agent:
  - **Environment** - Det definierade utrymmet där AI‑agenten verkar. Till exempel, om vi hade en reseboknings‑AI‑agent, skulle miljön kunna vara resebokningssystemet som AI‑agenten använder för att slutföra uppgifter.
  - **Sensors** - Miljöer har information och ger återkoppling. AI‑agenter använder sensorer för att samla in och tolka denna information om miljöns aktuella tillstånd. I exemplet med resebokningsagenten kan resebokningssystemet tillhandahålla information såsom hotellens tillgänglighet eller flygpriser.
  - **Actuators** - När AI‑agenten har fått miljöns aktuella tillstånd bestämmer agenten för den aktuella uppgiften vilken åtgärd som ska utföras för att förändra miljön. För resebokningsagenten kan det vara att boka ett tillgängligt rum åt användaren.

![Vad är AI‑agenter?](../../../translated_images/sv/what-are-ai-agents.1ec8c4d548af601a.webp)

**Large Language Models** - Konceptet med agenter fanns innan skapandet av LLMs. Fördelen med att bygga AI‑agenter med LLMs är deras förmåga att tolka mänskligt språk och data. Denna förmåga gör det möjligt för LLMs att tolka miljöinformation och definiera en plan för att förändra miljön.

**Perform Actions** - Utanför AI‑agentsystem är LLMs begränsade till situationer där handlingen är att generera innehåll eller information baserat på en användares uppmaning. Inom AI‑agentsystem kan LLMs utföra uppgifter genom att tolka användarens begäran och använda verktyg som finns tillgängliga i deras miljö.

**Access To Tools** - Vilka verktyg LLM:en har åtkomst till definieras av 1) den miljö den verkar i och 2) utvecklaren av AI‑agenten. I vårt exempel med reseagenten begränsas agentens verktyg av de operationer som finns tillgängliga i bokningssystemet, och/eller kan utvecklaren begränsa agentens verktygsåtkomst till flyg.

**Memory+Knowledge** - Minne kan vara kortsiktigt i kontexten av konversationen mellan användaren och agenten. På lång sikt, utöver informationen som tillhandahålls av miljön, kan AI‑agenter också hämta kunskap från andra system, tjänster, verktyg och till och med andra agenter. I reseagentexemplet kan denna kunskap vara information om användarens resepreferenser som finns i en kunddatabas.

### De olika typerna av agenter

Nu när vi har en allmän definition av AI‑agenter, låt oss titta på några specifika agenttyper och hur de skulle tillämpas på en reseboknings‑AI‑agent.

| **Agenttyp**                | **Beskrivning**                                                                                                                       | **Exempel**                                                                                                                                                                                                                   |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Enkla reflexagenter**     | Utför omedelbara åtgärder baserat på fördefinierade regler.                                                                             | Reseagent tolkar e-postens sammanhang och vidarebefordrar reseklagomål till kundtjänst.                                                                                                                                       |
| **Modellbaserade reflexagenter** | Utför åtgärder baserat på en modell av världen och förändringar i den modellen.                                                              | Reseagent prioriterar rutter med betydande prisförändringar baserat på tillgång till historisk prisdata.                                                                                                                     |
| **Målbaserade agenter**     | Skapar planer för att uppnå specifika mål genom att tolka målet och bestämma åtgärder för att nå det.                                  | Reseagent bokar en resa genom att bestämma nödvändiga researrangemang (bil, kollektivtrafik, flyg) från nuvarande plats till destinationen.                                                                                  |
| **Nyttebaserade agenter**   | Tar hänsyn till preferenser och väger avvägningar numeriskt för att avgöra hur mål ska uppnås.                                           | Reseagent maximerar nytta genom att väga bekvämlighet mot kostnad vid bokning.                                                                                                                                               |
| **Lärande agenter**         | Förbättras över tiden genom att svara på återkoppling och justera åtgärder därefter.                                                      | Reseagent förbättras genom att använda kundåterkoppling från enkäter efter resan för att göra justeringar i framtida bokningar.                                                                                              |
| **Hierarkiska agenter**     | Innehåller flera agenter i ett flernivåsystem, där högre nivåer delar upp uppgifter i deluppgifter för lägre nivåer att slutföra.        | Reseagent avbokar en resa genom att dela upp uppgiften i deluppgifter (t.ex. avbokning av specifika bokningar) och låta lägre nivåers agenter slutföra dem och rapportera tillbaka till den högre nivån.                         |
| **Fleragentsystem (MAS)**   | Agenter utför uppgifter oberoende, antingen kooperativt eller konkurrerande.                                                           | Kooperativt: Flera agenter bokar specifika resetjänster såsom hotell, flyg och underhållning. Konkurrerande: Flera agenter hanterar och konkurrerar om en gemensam hotellbokningskalender för att boka kunder till hotellet. |

## När man ska använda AI‑agenter

I det tidigare avsnittet använde vi användningsfallet reseagent för att förklara hur de olika agenttyperna kan användas i olika scenarier för resebokning. Vi kommer att fortsätta använda denna applikation genom hela kursen.

Låt oss titta på vilka typer av användningsfall som AI‑agenter lämpar sig bäst för:

![När ska man använda AI‑agenter?](../../../translated_images/sv/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Open-Ended Problems** - att låta LLM bestämma nödvändiga steg för att slutföra en uppgift eftersom det inte alltid går att hårdkoda i ett arbetsflöde.
- **Multi-Step Processes** - uppgifter som kräver en nivå av komplexitet där AI‑agenten behöver använda verktyg eller information över flera interaktioner istället för enkelhämtning.  
- **Improvement Over Time** - uppgifter där agenten kan förbättras över tid genom att få återkoppling från antingen sin miljö eller användare för att ge bättre nytta.

Vi går igenom fler överväganden kring användning av AI‑agenter i lektionen Bygga pålitliga AI‑agenter.

## Grundläggande om agentiska lösningar

### Agentutveckling

Det första steget i att utforma ett AI‑agentsystem är att definiera verktyg, åtgärder och beteenden. I den här kursen fokuserar vi på att använda **Azure AI Agent Service** för att definiera våra agenter. Den erbjuder funktioner som:

- Val av öppna modeller såsom OpenAI, Mistral och Llama
- Användning av licensierad data via leverantörer som Tripadvisor
- Användning av standardiserade OpenAPI 3.0-verktyg

### Agentiska mönster

Kommunikation med LLMs sker genom prompts. Givet AI‑agenternas semi‑autonoma natur är det inte alltid möjligt eller nödvändigt att manuellt ge LLM:en en ny prompt efter en förändring i miljön. Vi använder **Agentic Patterns** som tillåter oss att prompta LLM:en över flera steg på ett mer skalbart sätt.

Denna kurs är uppdelad i några av de för närvarande populära agentiska mönstren.

### Agentiska ramverk

Agentiska ramverk tillåter utvecklare att implementera agentiska mönster genom kod. Dessa ramverk erbjuder mallar, plugins och verktyg för bättre AI‑agent­samarbete. Dessa fördelar ger möjligheter till bättre observerbarhet och felsökning av AI‑agentsystem.

I denna kurs kommer vi att utforska det forskningsdrivna AutoGen‑ramverket och det produktionsredo Agent‑ramverket från Semantic Kernel.

## Kodexempel

- Python: [Agentramverk](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agentramverk](./code_samples/01-dotnet-agent-framework.md)

## Har du fler frågor om AI‑agenter?

Gå med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) för att träffa andra deltagare, delta i kontorstider och få svar på dina frågor om AI‑agenter.

## Föregående lektion

[Kursuppsättning](../00-course-setup/README.md)

## Nästa lektion

[Utforska agentiska ramverk](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfriskrivning:
Detta dokument har översatts med hjälp av AI-översättningstjänsten Co-op Translator (https://github.com/Azure/co-op-translator). Vi strävar efter noggrannhet, men var medveten om att automatiska översättningar kan innehålla fel eller brister. Originaldokumentet på dess ursprungsspråk bör betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår till följd av användningen av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->