# Brug af agentiske protokoller (MCP, A2A og NLWeb)

[![Agentprotokoller](../../../translated_images/da/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Klik på billedet ovenfor for at se videoen af denne lektion)_

Efterhånden som brugen af AI-agenter vokser, øges også behovet for protokoller, der sikrer standardisering, sikkerhed og understøtter åben innovation. I denne lektion dækker vi 3 protokoller, der søger at opfylde dette behov - Model Context Protocol (MCP), Agent to Agent (A2A) og Natural Language Web (NLWeb).

## Introduktion

I denne lektion vil vi gennemgå:

• Hvordan **MCP** giver AI-agenter adgang til eksterne værktøjer og data for at fuldføre brugeropgaver.

• Hvordan **A2A** muliggør kommunikation og samarbejde mellem forskellige AI-agenter.

• Hvordan **NLWeb** bringer naturlige sproggrænseflader til enhver hjemmeside, så AI-agenter kan finde og interagere med indholdet.

## Læringsmål

• **Identificere** det centrale formål og fordelene ved MCP, A2A og NLWeb i forbindelse med AI-agenter.

• **Forklare** hvordan hver protokol letter kommunikation og interaktion mellem LLM'er, værktøjer og andre agenter.

• **Genkende** de forskellige roller, hver protokol spiller i opbygningen af komplekse agentiske systemer.

## Model Context Protocol

Model Context Protocol (MCP) er en åben standard, der giver en standardiseret måde for applikationer at levere kontekst og værktøjer til LLM'er. Dette muliggør en "universel adapter" til forskellige datakilder og værktøjer, som AI-agenter kan forbindes til på en konsekvent måde.

Lad os se på komponenterne i MCP, fordelene sammenlignet med direkte API-brug, og et eksempel på, hvordan AI-agenter kunne bruge en MCP-server.

### MCPs kernekomponenter

MCP kører på en **client-server-arkitektur**, og kernekomponenterne er:

• **Hosts** er LLM-applikationer (for eksempel en kodeeditor som VSCode), der starter forbindelserne til en MCP-server.

• **Clients** er komponenter inden for host-applikationen, der opretholder én-til-én-forbindelser med servere.

• **Servers** er letvægtsprogrammer, der eksponerer specifikke kapaciteter.

Inde i protokollen findes tre kerneprimitiver, som er kapaciteterne for en MCP-server:

• **Tools**: Dette er diskrete handlinger eller funktioner, som en AI-agent kan kalde for at udføre en handling. For eksempel kunne en vejrtjeneste eksponere et "get weather"-værktøj, eller en e-handelsserver kunne eksponere et "purchase product"-værktøj. MCP-servere annoncerer hvert værktøjs navn, beskrivelse og input/output-skema i deres funktionalitetsoversigt.

• **Resources**: Dette er skrivebeskyttede dataelementer eller dokumenter, som en MCP-server kan levere, og klienter kan hente dem efter behov. Eksempler inkluderer filindhold, databaserecords eller logfiler. Resources kan være tekst (som kode eller JSON) eller binære (som billeder eller PDF'er).

• **Prompts**: Dette er foruddefinerede skabeloner, der giver foreslåede prompts og tillader mere komplekse arbejdsgange.

### Fordele ved MCP

MCP tilbyder betydelige fordele for AI-agenter:

• **Dynamisk værkdøgnsopdagelse**: Agenter kan dynamisk modtage en liste over tilgængelige værktøjer fra en server sammen med beskrivelser af, hvad de gør. Dette står i kontrast til traditionelle API'er, som ofte kræver statisk kodning for integrationer, hvilket betyder, at enhver API-ændring kræver kodeopdateringer. MCP tilbyder en "integrer én gang"-tilgang, hvilket fører til større tilpasningsevne.

• **Interoperabilitet på tværs af LLM'er**: MCP fungerer på tværs af forskellige LLM'er og giver fleksibilitet til at skifte kerne-modeller for at evaluere bedre ydeevne.

• **Standardiseret sikkerhed**: MCP inkluderer en standardgodkendelsesmetode, hvilket forbedrer skalerbarheden ved tilføjelse af adgang til yderligere MCP-servere. Dette er enklere end at håndtere forskellige nøgler og godkendelsestyper for forskellige traditionelle API'er.

### MCP-eksempel

![MCP-diagram](../../../translated_images/da/mcp-diagram.e4ca1cbd551444a1.webp)

Forestil dig, at en bruger vil booke en flyrejse ved hjælp af en AI-assistent drevet af MCP.

1. **Forbindelse**: AI-assistenten (MCP-klienten) opretter forbindelse til en MCP-server leveret af et flyselskab.

2. **Værktøjsopdagelse**: Klienten spørger flyselskabets MCP-server: "Hvilke værktøjer har I tilgængelige?" Serveren svarer med værktøjer som "search flights" og "book flights".

3. **Værktøjskald**: Du beder derefter AI-assistenten: "Søg venligst efter en flyvning fra Portland til Honolulu." AI-assistenten, ved hjælp af sin LLM, identificerer, at den skal kalde "search flights"-værktøjet og videregiver relevante parametre (afgangssted, destination) til MCP-serveren.

4. **Udførelse og svar**: MCP-serveren, som fungerer som en wrapper, foretager det faktiske kald til flyselskabets interne bookings-API. Den modtager derefter flyoplysningerne (f.eks. JSON-data) og sender dem tilbage til AI-assistenten.

5. **Yderligere interaktion**: AI-assistenten præsenterer flymulighederne. Når du vælger en flyvning, kan assistenten vælge at kalde "book flight"-værktøjet på den samme MCP-server og fuldføre bookingen.

## Agent-to-Agent Protocol (A2A)

Mens MCP fokuserer på at forbinde LLM'er til værktøjer, går **Agent-to-Agent (A2A)-protokollen** et skridt videre ved at muliggøre kommunikation og samarbejde mellem forskellige AI-agenter. A2A forbinder AI-agenter på tværs af forskellige organisationer, miljøer og teknologistakke for at fuldføre en fælles opgave.

Vi vil undersøge A2As komponenter og fordele samt et eksempel på, hvordan det kunne anvendes i vores rejseapplikation.

### A2As kernekomponenter

A2A fokuserer på at muliggøre kommunikation mellem agenter og få dem til at arbejde sammen om at fuldføre en underopgave for brugeren. Hver komponent i protokollen bidrager til dette:

#### Agent Card

Ligesom en MCP-server deler en liste over værktøjer, har et Agent Card:
- Agentens navn.
- En **beskrivelse af de generelle opgaver**, den udfører.
- En **liste over specifikke færdigheder** med beskrivelser for at hjælpe andre agenter (eller endda menneskelige brugere) med at forstå, hvornår og hvorfor de ville kalde den agent.
- Den **aktuelle Endpoint URL** for agenten
- **Versionen** og **kapaciteterne** af agenten, såsom streaming-responser og push-notifikationer.

#### Agent Executor

Agent Executor er ansvarlig for **at overføre konteksten af brugerchatten til den eksterne agent**; den eksterne agent har brug for dette for at forstå den opgave, der skal udføres. I en A2A-server bruger en agent sin egen Large Language Model (LLM) til at analysere indkommende forespørgsler og udføre opgaver ved hjælp af sine egne interne værktøjer.

#### Artifact

Når en ekstern agent har fuldført den anmodede opgave, oprettes dens arbejdsprodukt som et artifact. Et artifact **indeholder resultatet af agentens arbejde**, en **beskrivelse af hvad der blev udført**, og den **tekstkontekst**, der sendes gennem protokollen. Efter at artifactet er sendt, lukkes forbindelsen med den eksterne agent, indtil den igen er nødvendig.

#### Event Queue

Denne komponent bruges til **at håndtere opdateringer og videresende beskeder**. Den er særligt vigtig i produktion for agentiske systemer for at forhindre, at forbindelsen mellem agenter lukkes, før en opgave er fuldført, især når opgavekomplettering kan tage længere tid.

### Fordele ved A2A

• **Forbedret samarbejde**: Den gør det muligt for agenter fra forskellige leverandører og platforme at interagere, dele kontekst og arbejde sammen, hvilket muliggør sømløs automatisering på tværs af traditionelt adskilte systemer.

• **Fleksibilitet i modelvalg**: Hver A2A-agent kan selv beslutte, hvilken LLM den bruger til at håndtere sine forespørgsler, hvilket tillader optimerede eller fintunede modeller pr. agent, i modsætning til en enkelt LLM-forbindelse i nogle MCP-scenarier.

• **Indbygget godkendelse**: Godkendelse er integreret direkte i A2A-protokollen og giver en robust sikkerhedsramme for agentinteraktioner.

### A2A-eksempel

![A2A-diagram](../../../translated_images/da/A2A-Diagram.8666928d648acc26.webp)

Lad os udbygge vores rejsebookingsscenarie, men denne gang bruge A2A.

1. **Brugerforespørgsel til multi-agent**: En bruger interagerer med en "Travel Agent"-A2A-klient/agent, måske ved at sige: "Book venligst en hel tur til Honolulu i næste uge, inklusive fly, hotel og en lejebil".

2. **Orkestrering af Travel Agent**: Travel Agent modtager denne komplekse forespørgsel. Den bruger sin LLM til at ræsonnere om opgaven og afgøre, at den skal interagere med andre specialiserede agenter.

3. **Mellem-agent kommunikation**: Travel Agent bruger derefter A2A-protokollen til at oprette forbindelse til downstream-agenter, såsom en "Airline Agent", en "Hotel Agent" og en "Car Rental Agent", som er oprettet af forskellige virksomheder.

4. **Delegation af opgaveudførelse**: Travel Agent sender specifikke opgaver til disse specialiserede agenter (f.eks. "Find flights to Honolulu", "Book a hotel", "Rent a car"). Hver af disse specialiserede agenter, der kører deres egne LLM'er og bruger deres egne værktøjer (som kunne være MCP-servere i sig selv), udfører sin specifikke del af bookingen.

5. **Konsolideret svar**: Når alle downstream-agenter har fuldført deres opgaver, samler Travel Agent resultaterne (flyoplysninger, hotelbekræftelse, lejebilbooking) og sender et omfattende, chat-lignende svar tilbage til brugeren.

## Natural Language Web (NLWeb)

Websites har længe været den primære måde for brugere at få adgang til information og data på internettet.

Lad os se på de forskellige komponenter i NLWeb, fordelene ved NLWeb og et eksempel på, hvordan vores NLWeb virker ved at kigge på vores rejseapplikation.

### Komponenter i NLWeb

- **NLWeb-applikation (Core Service Code)**: Systemet, der behandler spørgsmål i naturligt sprog. Det forbinder de forskellige dele af platformen for at skabe svar. Du kan tænke på det som **motoren, der driver de naturlige sprogfunktioner** på en hjemmeside.

- **NLWeb-protokol**: Dette er et **grundlæggende sæt regler for naturlig sproginteraktion** med en hjemmeside. Den sender svar tilbage i JSON-format (ofte ved brug af Schema.org). Formålet er at skabe et simpelt grundlag for "AI-webben", på samme måde som HTML gjorde det muligt at dele dokumenter online.

- **MCP-server (Model Context Protocol Endpoint)**: Hver NLWeb-installation fungerer også som en **MCP-server**. Det betyder, at den kan **dele værktøjer (som en “ask”-metode) og data** med andre AI-systemer. I praksis gør dette hjemmesidens indhold og funktioner brugbare for AI-agenter, så sitet kan blive en del af det bredere "agent-økosystem".

- **Embedding-modeller**: Disse modeller bruges til at **konvertere hjemmesideindhold til numeriske repræsentationer kaldet vektorer** (embeddings). Disse vektorer fanger mening på en måde, som computere kan sammenligne og søge i. De gemmes i en særlig database, og brugere kan vælge, hvilken embedding-model de ønsker at bruge.

- **Vektordatabase (hentningsmekanisme)**: Denne database **gemmer embedding af hjemmesideindholdet**. Når nogen stiller et spørgsmål, tjekker NLWeb vektordatabasen for hurtigt at finde den mest relevante information. Den giver en hurtig liste over mulige svar, rangeret efter lighed. NLWeb fungerer med forskellige vektorlager-systemer såsom Qdrant, Snowflake, Milvus, Azure AI Search og Elasticsearch.

### NLWeb ved eksempel

![NLWeb](../../../translated_images/da/nlweb-diagram.c1e2390b310e5fe4.webp)

Overvej vores rejsebookingshjemmeside igen, men denne gang er den drevet af NLWeb.

1. **Dataindsamling**: Rejsesitetets eksisterende produktkataloger (f.eks. flylister, hotellbeskrivelser, ture) formateres ved hjælp af Schema.org eller indlæses via RSS-feeds. NLWebs værktøjer indtager disse strukturerede data, opretter embeddings og gemmer dem i en lokal eller fjern vektordatabase.

2. **Forespørgsel i naturligt sprog (menneske)**: En bruger besøger hjemmesiden og skriver i stedet for at navigere i menuer i et chatvindue: "Find mig et familievenligt hotel i Honolulu med pool til næste uge".

3. **NLWeb-behandling**: NLWeb-applikationen modtager denne forespørgsel. Den sender forespørgslen til en LLM for forståelse og søger samtidig i sin vektordatabase efter relevante hoteltilbud.

4. **Præcise resultater**: LLM'en hjælper med at fortolke søgeresultaterne fra databasen, identificere de bedste matches baseret på kriterierne "familievenligt", "pool" og "Honolulu", og formaterer derefter et svar i naturligt sprog. Vigtigt er, at svaret refererer til faktiske hoteller fra hjemmesidens katalog og undgår opfundne oplysninger.

5. **AI-agent-interaktion**: Fordi NLWeb fungerer som en MCP-server, kunne en ekstern AI-rejseagent også oprette forbindelse til denne hjemmesides NLWeb-instans. AI-agenten kunne så bruge `ask` MCP-metoden til at spørge hjemmesiden direkte: `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")`. NLWeb-instansen ville behandle dette ved at udnytte sin database med restaurantinformation (hvis indlæst) og returnere et struktureret JSON-svar.

### Har du flere spørgsmål om MCP/A2A/NLWeb?

Deltag i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for at møde andre studerende, deltage i office hours og få svar på dine spørgsmål om AI-agenter.

## Ressourcer

- [MCP for Beginners](https://aka.ms/mcp-for-beginners)  
- [MCP Documentation](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb Repo](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel Guides](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfraskrivelse:
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten Co-op Translator (https://github.com/Azure/co-op-translator). Selvom vi stræber efter nøjagtighed, skal du være opmærksom på, at automatiske oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på originalsproget bør betragtes som den autoritative kilde. For vigtig eller kritisk information anbefales en professionel menneskelig oversættelse. Vi kan ikke holdes ansvarlige for misforståelser eller fejltolkninger, som måtte opstå ved brug af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->