# Använda agentprotokoll (MCP, A2A och NLWeb)

[![Agentprotokoll](../../../translated_images/sv/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Klicka på bilden ovan för att se videon till denna lektion)_

När användningen av AI-agenter växer, ökar också behovet av protokoll som säkerställer standardisering, säkerhet och stöd för öppen innovation. I denna lektion går vi igenom 3 protokoll som syftar till att möta detta behov - Model Context Protocol (MCP), Agent to Agent (A2A) och Natural Language Web (NLWeb).

## Introduktion

I den här lektionen kommer vi att gå igenom:

• Hur **MCP** tillåter AI-agenter att få tillgång till externa verktyg och data för att slutföra användaruppgifter.

• Hur **A2A** möjliggör kommunikation och samarbete mellan olika AI-agenter.

• Hur **NLWeb** tar naturliga språkgränssnitt till vilken webbplats som helst och gör det möjligt för AI-agenter att upptäcka och interagera med innehållet.

## Lärandemål

• **Identifiera** kärnsyftet och fördelarna med MCP, A2A och NLWeb i samband med AI-agenter.

• **Förklara** hur varje protokoll underlättar kommunikation och interaktion mellan LLM:er, verktyg och andra agenter.

• **Känna igen** de olika roller som varje protokoll spelar vid uppbyggnaden av komplexa agentiska system.

## Modellkontextprotokoll

Det **Model Context Protocol (MCP)** är en öppen standard som tillhandahåller ett standardiserat sätt för applikationer att ge kontext och verktyg till LLMs. Detta möjliggör en "universell adapter" till olika datakällor och verktyg som AI-agenter kan ansluta till på ett konsekvent sätt.

Låt oss titta på komponenterna i MCP, fördelarna jämfört med direkt API-användning och ett exempel på hur AI-agenter kan använda en MCP-server.

### MCP kärnkomponenter

MCP fungerar med en **klient-serverarkitektur** och kärnkomponenterna är:

• **Hosts** är LLM-applikationer (till exempel en kodredigerare som VSCode) som initierar anslutningarna till en MCP-server.

• **Clients** är komponenter inom host-applikationen som upprätthåller en-till-en-anslutningar med servrar.

• **Servers** är lätta program som exponerar specifika funktioner.

Inkluderat i protokollet finns tre kärnprimitiver som är kapabiliteterna hos en MCP-server:

• **Tools**: Dessa är diskreta åtgärder eller funktioner som en AI-agent kan anropa för att utföra en handling. Till exempel kan en vädertjänst exponera ett "hämta väder"-verktyg, eller en e-handelsserver kan exponera ett "köp produkt"-verktyg. MCP-servrar annonserar varje verks namn, beskrivning och in-/utdata-schema i sin kapabilitetslista.

• **Resources**: Detta är skrivskyddade dataobjekt eller dokument som en MCP-server kan tillhandahålla, och klienter kan hämta dem vid behov. Exempel inkluderar filinnehåll, databasposter eller loggfiler. Resurser kan vara text (som kod eller JSON) eller binära (som bilder eller PDF:er).

• **Prompts**: Detta är fördefinierade mallar som ger föreslagna uppmaningar och möjliggör mer komplexa arbetsflöden.

### Fördelar med MCP

MCP erbjuder betydande fördelar för AI-agenter:

• **Dynamisk upptäckt av verktyg**: Agenter kan dynamiskt ta emot en lista över tillgängliga verktyg från en server tillsammans med beskrivningar av vad de gör. Detta står i kontrast till traditionella API:er, som ofta kräver statisk kodning för integrationer, vilket innebär att varje API-ändring kräver koduppdateringar. MCP erbjuder ett "integrera en gång"-angreppssätt, vilket leder till större anpassningsbarhet.

• **Interoperabilitet över olika LLMs**: MCP fungerar över olika LLM:er, vilket ger flexibilitet att byta kärnmodeller för att utvärdera bättre prestanda.

• **Standardiserad säkerhet**: MCP inkluderar en standardiserad autentiseringsmetod, vilket förbättrar skalbarheten när man lägger till åtkomst till ytterligare MCP-servrar. Detta är enklare än att hantera olika nycklar och autentiseringstyper för olika traditionella API:er.

### MCP-exempel

![MCP-diagram](../../../translated_images/sv/mcp-diagram.e4ca1cbd551444a1.webp)

Föreställ dig att en användare vill boka en flygresa med en AI-assistent som drivs av MCP.

1. **Anslutning**: AI-assistenten (MCP-klienten) ansluter till en MCP-server som tillhandahålls av ett flygbolag.

2. **Verktsupptäckt**: Klienten frågar flygbolagets MCP-server, "Vilka verktyg har ni tillgängliga?" Servern svarar med verktyg som "sök flyg" och "boka flyg".

3. **Verktsanrop**: Du ber sedan AI-assistenten, "Sök efter ett flyg från Portland till Honolulu." AI-assistenten, med hjälp av sin LLM, identifierar att den behöver anropa verktyget "sök flyg" och skickar relevanta parametrar (avgång, destination) till MCP-servern.

4. **Utförande och svar**: MCP-servern, som fungerar som en omslagare, gör det faktiska anropet till flygbolagets interna boknings-API. Den tar emot flyginformationen (t.ex. JSON-data) och skickar den tillbaka till AI-assistenten.

5. **Vidare interaktion**: AI-assistenten presenterar flygalternativen. När du väljer ett flyg kan assistenten anropa "boka flyg"-verktyget på samma MCP-server och slutföra bokningen.

## Agent-till-agent-protokoll (A2A)

Medan MCP fokuserar på att koppla LLM:er till verktyg tar **Agent-to-Agent (A2A) protocol** det ett steg längre genom att möjliggöra kommunikation och samarbete mellan olika AI-agenter. A2A kopplar AI-agenter över olika organisationer, miljöer och teknikstackar för att slutföra en gemensam uppgift.

Vi kommer att granska komponenterna och fördelarna med A2A, tillsammans med ett exempel på hur det kan tillämpas i vår reseapplikation.

### A2A kärnkomponenter

A2A fokuserar på att möjliggöra kommunikation mellan agenter och att låta dem arbeta tillsammans för att slutföra en deluppgift åt användaren. Varje komponent i protokollet bidrar till detta:

#### Agentkort

Liknande hur en MCP-server delar en lista över verktyg, har ett Agentkort:
- Agentens namn.
- En **beskrivning av de allmänna uppgifter** den utför.
- En **lista över specifika färdigheter** med beskrivningar för att hjälpa andra agenter (eller till och med mänskliga användare) att förstå när och varför de bör anropa den agenten.
- Den **aktuella slutpunkts-URL:en** för agenten
- **versionen** och **möjligheterna** hos agenten såsom strömmande svar och push-notifikationer.

#### Agentutförare

Agentutföraren ansvarar för att **skicka kontexten från användarchatten till den fjärrstyrda agenten**, den fjärrstyrda agenten behöver detta för att förstå uppgiften som ska utföras. I en A2A-server använder en agent sin egen stora språkmodell (LLM) för att analysera inkommande förfrågningar och utföra uppgifter med hjälp av sina egna interna verktyg.

#### Artefakt

När en fjärragent har slutfört den begärda uppgiften skapas dess resultat som ett artefakt. Ett artefakt **innehåller resultatet av agentens arbete**, en **beskrivning av vad som slutfördes**, och den **textkontext** som skickas genom protokollet. Efter att artefakten har skickats stängs anslutningen till den fjärrstyrda agenten tills den behövs igen.

#### Händelsekö

Denna komponent används för **hantering av uppdateringar och vidarebefordran av meddelanden**. Den är särskilt viktig i produktionsmiljö för agentiska system för att förhindra att anslutningen mellan agenter stängs innan en uppgift är slutförd, särskilt när uppgiftslöptider kan ta längre tid.

### Fördelar med A2A

• **Förbättrat samarbete**: Det gör det möjligt för agenter från olika leverantörer och plattformar att interagera, dela kontext och arbeta tillsammans, vilket underlättar sömlös automatisering över traditionellt frånkopplade system.

• **Flexibilitet i modellval**: Varje A2A-agent kan välja vilken LLM den använder för att hantera sina förfrågningar, vilket möjliggör optimerade eller finjusterade modeller per agent, till skillnad från en enda LLM-anslutning i vissa MCP-scenarier.

• **Inbyggd autentisering**: Autentisering är integrerat direkt i A2A-protokollet, vilket ger en robust säkerhetsram för agentinteraktioner.

### A2A-exempel

![A2A-diagram](../../../translated_images/sv/A2A-Diagram.8666928d648acc26.webp)

Låt oss bygga ut vårt scenario med resebokning, men denna gång med A2A.

1. **Användarförfrågan till multi-agent**: En användare interagerar med en "Reseagent"-A2A-klient/agent, kanske genom att säga, "Boka en hel resa till Honolulu nästa vecka, inklusive flyg, hotell och hyrbil."

2. **Orkestrering av reseagenten**: Reseagenten tar emot denna komplexa förfrågan. Den använder sin LLM för att resonera om uppgiften och avgöra att den behöver interagera med andra specialiserade agenter.

3. **Inter-agentkommunikation**: Reseagenten använder sedan A2A-protokollet för att ansluta till nedströmsagenter, såsom en "Flygbolagsagent", en "Hotellagent" och en "Biluthyrningsagent" som skapats av olika företag.

4. **Delegation av uppgifter**: Reseagenten skickar specifika uppgifter till dessa specialiserade agenter (t.ex. "Hitta flyg till Honolulu", "Boka ett hotell", "Hyr en bil"). Var och en av dessa specialiserade agenter, som kör sina egna LLM:er och använder sina egna verktyg (vilka i sig kan vara MCP-servrar), utför sin specifika del av bokningen.

5. **Konsoliderat svar**: När alla nedströmsagenter har slutfört sina uppgifter sammanställer reseagenten resultaten (flyguppgifter, hotellbekräftelse, biluthyrningsbokning) och skickar ett omfattande, chattliknande svar tillbaka till användaren.

## Natural Language Web (NLWeb)

Webbplatser har länge varit det huvudsakliga sättet för användare att få tillgång till information och data över internet.

Låt oss titta på de olika komponenterna i NLWeb, fördelarna med NLWeb och ett exempel på hur vår NLWeb fungerar genom att titta på vår reseapplikation.

### Komponenter i NLWeb

- **NLWeb Application (Core Service Code)**: Systemet som bearbetar frågor i naturligt språk. Det kopplar samman de olika delarna av plattformen för att skapa svar. Du kan tänka på det som motorn som driver webbplatsens funktioner för naturligt språk.

- **NLWeb Protocol**: Detta är en **grundläggande uppsättning regler för interaktion i naturligt språk** med en webbplats. Det skickar tillbaka svar i JSON-format (ofta med Schema.org). Dess syfte är att skapa en enkel grund för "AI-webben", på samma sätt som HTML gjorde det möjligt att dela dokument online.

- **MCP Server (Model Context Protocol Endpoint)**: Varje NLWeb-installation fungerar också som en **MCP-server**. Det innebär att den kan **dela verktyg (som en "ask"-metod) och data** med andra AI-system. I praktiken gör detta webbplatsens innehåll och funktioner användbara för AI-agenter och låter webbplatsen bli en del av det bredare "agentekosystemet."

- **Inbäddningsmodeller**: Dessa modeller används för att **omvandla webbplatsinnehåll till numeriska representationer kallade vektorer** (embeddings). Dessa vektorer fångar betydelse på ett sätt som datorer kan jämföra och söka i. De lagras i en särskild databas, och användare kan välja vilken inbäddningsmodell de vill använda.

- **Vektordatabas (hämtmekanism)**: Denna databas **lagrar inbäddningarna av webbplatsens innehåll**. När någon ställer en fråga kontrollerar NLWeb vektordatabasen för att snabbt hitta den mest relevanta informationen. Den ger en snabb lista över möjliga svar, rangordnade efter likhet. NLWeb fungerar med olika vektorlager som Qdrant, Snowflake, Milvus, Azure AI Search och Elasticsearch.

### NLWeb med exempel

![NLWeb](../../../translated_images/sv/nlweb-diagram.c1e2390b310e5fe4.webp)

Tänk på vår resebokningswebbplats igen, men denna gång drivs den av NLWeb.

1. **Datainmatning**: Resesajtens befintliga produktkataloger (t.ex. flyglistor, hotellbeskrivningar, paketresor) formateras med Schema.org eller laddas via RSS-flöden. NLWebs verktyg läser in denna strukturerade data, skapar inbäddningar och lagrar dem i en lokal eller fjärran vektordatabas.

2. **Fråga i naturligt språk (människa)**: En användare besöker webbplatsen och i stället för att navigera i menyer skriver denne i ett chattgränssnitt: "Hitta ett familjevänligt hotell i Honolulu med pool nästa vecka".

3. **NLWeb-bearbetning**: NLWeb-applikationen tar emot denna fråga. Den skickar frågan till en LLM för tolkning och söker samtidigt i sin vektordatabas efter relevanta hotellposter.

4. **Korrekt resultat**: LLM:en hjälper till att tolka sökresultaten från databasen, identifiera de bästa matchningarna baserat på kriterierna "familjevänligt", "pool" och "Honolulu", och formaterar sedan ett svar i naturligt språk. Avgörande är att svaret hänvisar till faktiska hotell från webbplatsens katalog och undviker påhittad information.

5. **Interaktion med AI-agent**: Eftersom NLWeb fungerar som en MCP-server kan en extern AI-reseagent också ansluta till webbplatsens NLWeb-instans. AI-agenten kan då använda `ask("Finns det några vegovänliga restauranger i Honolulu-området som rekommenderas av hotellet?")`. NLWeb-instansen skulle bearbeta detta, utnyttja sin databas med restauranginformation (om den är inläst) och returnera ett strukturerat JSON-svar.

### Fler frågor om MCP/A2A/NLWeb?

Gå med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) för att träffa andra lärande, delta i kontorstid och få dina frågor om AI-agenter besvarade.

## Resurser

- [MCP för nybörjare](https://aka.ms/mcp-for-beginners)  
- [MCP-dokumentation](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb-repo](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel-guider](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfriskrivning:
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Vi strävar efter noggrannhet, men observera att automatiska översättningar kan innehålla fel eller felaktigheter. Det ursprungliga dokumentet på sitt originalspråk bör betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår till följd av användning av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->