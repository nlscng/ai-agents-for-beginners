# Bruke Agentiske Protokoller (MCP, A2A og NLWeb)

[![Agentic Protocols](../../../translated_images/no/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Klikk på bildet over for å se video av denne leksjonen)_

Etter hvert som bruken av AI-agenter vokser, øker også behovet for protokoller som sikrer standardisering, sikkerhet og støtter åpen innovasjon. I denne leksjonen vil vi dekke 3 protokoller som søker å møte dette behovet - Model Context Protocol (MCP), Agent to Agent (A2A) og Natural Language Web (NLWeb).

## Introduksjon

I denne leksjonen vil vi dekke:

• Hvordan **MCP** gjør det mulig for AI-agenter å få tilgang til eksterne verktøy og data for å fullføre brukeroppgaver.

• Hvordan **A2A** muliggjør kommunikasjon og samarbeid mellom ulike AI-agenter.

• Hvordan **NLWeb** bringer naturlige språkgrensesnitt til enhver nettside, slik at AI-agenter kan oppdage og samhandle med innholdet.

## Læringsmål

• **Identifisere** hovedformålet og fordelene med MCP, A2A og NLWeb i konteksten av AI-agenter.

• **Forklare** hvordan hver protokoll legger til rette for kommunikasjon og samhandling mellom LLM-er, verktøy og andre agenter.

• **Gjenkjenne** de distinkte rollene hver protokoll spiller i å bygge komplekse agentiske systemer.

## Model Context Protocol

**Model Context Protocol (MCP)** er en åpen standard som gir en standardisert måte for applikasjoner å gi kontekst og verktøy til LLM-er. Dette muliggjør en "universell adapter" til forskjellige datakilder og verktøy som AI-agenter kan koble til på en konsistent måte.

La oss se på komponentene i MCP, fordelene sammenlignet med direkte API-bruk, og et eksempel på hvordan AI-agenter kan bruke en MCP-server.

### MCP Kjernekomponenter

MCP opererer på en **klient-tjener-arkitektur** og kjernekomponentene er:

• **Hosts** er LLM-applikasjoner (for eksempel en kodeeditor som VSCode) som starter tilkoblingene til en MCP-server.

• **Clients** er komponenter inne i vertsapplikasjonen som opprettholder én-til-én-tilkoblinger med servere.

• **Servers** er lettvektige programmer som eksponerer spesifikke funksjoner.

Inkludert i protokollen er tre kjerneprimitiver som er funksjonene til en MCP-server:

• **Tools**: Dette er diskrete handlinger eller funksjoner en AI-agent kan kalle for å utføre en handling. For eksempel kan en værtjeneste eksponere et "hent vær"-verktøy, eller en e-handelsserver kan eksponere et "kjøp produkt"-verktøy. MCP-servere annonserer hvert verktøys navn, beskrivelse og input/output-skjema i sin funksjonalitetsliste.

• **Resources**: Dette er skrivebeskyttede dataelementer eller dokumenter som en MCP-server kan tilby, og klienter kan hente dem på forespørsel. Eksempler inkluderer filinnhold, databaseposter eller loggfiler. Ressurser kan være tekst (som kode eller JSON) eller binær (som bilder eller PDF-er).

• **Prompts**: Dette er forhåndsdefinerte maler som tilbyr foreslåtte spørsmål, noe som tillater mer komplekse arbeidsflyter.

### Fordeler med MCP

MCP tilbyr betydelige fordeler for AI-agenter:

• **Dynamisk Verktøysoppdagelse**: Agenter kan dynamisk motta en liste over tilgjengelige verktøy fra en server sammen med beskrivelser av hva de gjør. Dette står i kontrast til tradisjonelle APIer som ofte krever statisk koding for integrasjoner, noe som betyr at alle API-endringer krever kodeoppdateringer. MCP tilbyr en "integrer én gang"-tilnærming, noe som fører til større tilpasningsevne.

• **Interoperabilitet på tvers av LLM-er**: MCP fungerer på tvers av ulike LLM-er, og gir fleksibilitet til å bytte kjerne-modeller for å evaluere bedre ytelse.

• **Standardisert Sikkerhet**: MCP inkluderer en standard autentiseringsmetode, noe som forbedrer skalerbarheten når man legger til tilgang til flere MCP-servere. Dette er enklere enn å håndtere forskjellige nøkler og autentiseringstyper for ulike tradisjonelle APIer.

### MCP Eksempel

![MCP Diagram](../../../translated_images/no/mcp-diagram.e4ca1cbd551444a1.webp)

Tenk deg at en bruker ønsker å bestille en flyreise ved hjelp av en AI-assistent drevet av MCP.

1. **Tilkobling**: AI-assistenten (MCP-klienten) kobler til en MCP-server levert av et flyselskap.

2. **Verktøyoppdagelse**: Klienten spør flyselskapets MCP-server, "Hvilke verktøy har dere tilgjengelig?" Serveren svarer med verktøy som "søk fly" og "bestill fly".

3. **Verktøyinnkalling**: Du ber så AI-assistenten om å "Vennligst søk etter en flyreise fra Portland til Honolulu." AI-assistenten, ved hjelp av sin LLM, identifiserer at den må kalle "søk fly"-verktøyet og sender relevante parametere (avreisested, destinasjon) til MCP-serveren.

4. **Utførelse og Respons**: MCP-serveren, som fungerer som en wrapper, utfører det faktiske kallet til flyselskapets interne booking-API. Deretter mottar den flyinformasjonen (f.eks. JSON-data) og sender den tilbake til AI-assistenten.

5. **Videre Interaksjon**: AI-assistenten presenterer flyalternativene. Når du velger en flyreise, kan assistenten kalle "bestill fly"-verktøyet på samme MCP-server og fullføre bestillingen.

## Agent-til-Agent Protokoll (A2A)

Mens MCP fokuserer på å koble LLM-er til verktøy, tar **Agent-to-Agent (A2A) protokollen** det ett skritt videre ved å muliggjøre kommunikasjon og samarbeid mellom ulike AI-agenter. A2A kobler AI-agenter på tvers av forskjellige organisasjoner, miljøer og teknologistabler for å fullføre en felles oppgave.

Vi vil undersøke komponentene og fordelene med A2A, sammen med et eksempel på hvordan det kan brukes i vår reiseapplikasjon.

### A2A Kjernekomponenter

A2A fokuserer på å muliggjøre kommunikasjon mellom agenter og la dem jobbe sammen for å fullføre en deloppgave for brukeren. Hver komponent i protokollen bidrar til dette:

#### Agentkort

På samme måte som en MCP-server deler en liste over verktøy, har et Agentkort:
- Navnet på agenten.
- En **beskrivelse av de generelle oppgavene** den utfører.
- En **liste over spesifikke ferdigheter** med beskrivelser som hjelper andre agenter (eller til og med menneskelige brukere) å forstå når og hvorfor de vil kalle på den agenten.
- Den **nåværende Endepunkt-URL** for agenten.
- **versjon** og **evner** til agenten som for eksempel strømming av svar og push-varslinger.

#### Agentutfører

Agentutføreren har ansvar for **å overføre konteksten av brukersamtalen til den eksterne agenten**, den eksterne agenten trenger dette for å forstå oppgaven som må utføres. I en A2A-server bruker en agent sin egen Large Language Model (LLM) for å tolke innkommende forespørsler og utføre oppgaver ved å bruke sine egne interne verktøy.

#### Artefakt

Når en ekstern agent har fullført den forespurte oppgaven, opprettes resultatet som et artefakt. Et artefakt **inneholder resultatet av agentens arbeid**, en **beskrivelse av hva som ble fullført**, og **tekstkonteksten** som sendes gjennom protokollen. Etter at artefaktet er sendt, lukkes tilkoblingen med den eksterne agenten til den trengs igjen.

#### Hendelseskø

Denne komponenten brukes for **å håndtere oppdateringer og sende meldinger**. Den er spesielt viktig i produksjon for agentiske systemer for å forhindre at forbindelsen mellom agenter lukkes før en oppgave er fullført, spesielt når oppgavefullførings-tiden kan være lang.

### Fordeler med A2A

• **Forbedret Samarbeid**: Det gjør det mulig for agenter fra forskjellige leverandører og plattformer å interagere, dele kontekst og jobbe sammen, noe som legger til rette for sømløs automatisering på tvers av tradisjonelt isolerte systemer.

• **Fleksibilitet i Modellvalg**: Hver A2A-agent kan bestemme hvilken LLM den bruker for å betjene sine forespørsler, noe som tillater optimaliserte eller finjusterte modeller per agent, i motsetning til en enkelt LLM-tilkobling i noen MCP-scenarier.

• **Innebygd Autentisering**: Autentisering er integrert direkte i A2A-protokollen, og gir et robust sikkerhetsrammeverk for agentinteraksjoner.

### A2A Eksempel

![A2A Diagram](../../../translated_images/no/A2A-Diagram.8666928d648acc26.webp)

La oss utvide vårt reisebestillingsscenario, men denne gangen bruker vi A2A.

1. **Brukerforespørsel til Multi-Agent**: En bruker interagerer med en "Reiseagent" som A2A-klient/agent, kanskje ved å si: "Vennligst bestill en hel tur til Honolulu neste uke, inkludert fly, hotell og leiebil".

2. **Orkestrering av Reiseagent**: Reiseagenten mottar denne komplekse forespørselen. Den bruker sin LLM til å resonere rundt oppgaven og avgjøre at den trenger å samhandle med andre spesialiserte agenter.

3. **Inter-Agent Kommunikasjon**: Reiseagenten bruker deretter A2A-protokollen for å koble til underordnede agenter, slik som en "Flyagent", en "Hotellagent" og en "Leiebilagent" som er opprettet av forskjellige selskaper.

4. **Delegering av Oppgaveutførelse**: Reiseagenten sender spesifikke oppgaver til disse spesialiserte agentene (f.eks. "Finn fly til Honolulu", "Bestill hotell", "Lei bil"). Hver av disse spesialiserte agentene, som kjører sine egne LLM-er og bruker sine egne verktøy (som kan være MCP-servere i seg selv), utfører sin spesifikke del av bestillingen.

5. **Konsolidert Respons**: Når alle underordnede agenter fullfører sine oppgaver, samler Reiseagenten resultatene (flydetaljer, hotellbekreftelse, leiebilbestilling) og sender et omfattende, chat-stil svar tilbake til brukeren.

## Natural Language Web (NLWeb)

Nettsteder har lenge vært den primære måten for brukere å få tilgang til informasjon og data på internett.

La oss se på de forskjellige komponentene i NLWeb, fordelene med NLWeb og et eksempel på hvordan vår NLWeb fungerer ved å se på vår reiseapplikasjon.

### Komponenter i NLWeb

- **NLWeb-applikasjon (kjernetjenestekode)**: Systemet som behandler spørsmål på naturlig språk. Det kobler sammen de forskjellige delene av plattformen for å lage svar. Du kan tenke på det som **motoren som driver de naturlige språkfunksjonene** på en nettside.

- **NLWeb-protokoll**: Dette er et **grunnleggende sett med regler for naturlig språk-interaksjon** med en nettside. Den sender tilbake svar i JSON-format (ofte ved hjelp av Schema.org). Hensikten er å skape et enkelt fundament for "AI-nettet", på samme måte som HTML gjorde det mulig å dele dokumenter på nettet.

- **MCP-server (Model Context Protocol-endepunkt)**: Hver NLWeb-oppsett fungerer også som en **MCP-server**. Dette betyr at den kan **dele verktøy (som en “ask”-metode) og data** med andre AI-systemer. I praksis gjør dette at nettstedets innhold og evner blir brukbart av AI-agenter, slik at nettstedet kan bli en del av det bredere "agentøkosystemet."

- **Innebygde modeller**: Disse modellene brukes til å **konvertere nettstedets innhold til numeriske representasjoner kalt vektorer** (embeddings). Disse vektorene fanger mening på en måte datamaskiner kan sammenligne og søke i. De lagres i en spesiell database, og brukere kan velge hvilken embedding-modell de vil bruke.

- **Vektordatabase (hentemekanisme)**: Denne databasen **lagrer embeddingene av nettstedets innhold**. Når noen stiller et spørsmål, søker NLWeb i vektordatabasen for raskt å finne den mest relevante informasjonen. Den gir en rask liste over mulige svar, rangert etter likhet. NLWeb fungerer med forskjellige vektorlager-systemer som Qdrant, Snowflake, Milvus, Azure AI Search og Elasticsearch.

### NLWeb ved Eksempel

![NLWeb](../../../translated_images/no/nlweb-diagram.c1e2390b310e5fe4.webp)

Tenk på vår reisebestillingsside igjen, men denne gangen drevet av NLWeb.

1. **Dataopptak**: Reisesidens eksisterende produktkataloger (f.eks. flylister, hotellbeskrivelser, turpakker) formateres ved hjelp av Schema.org eller lastes inn via RSS-feeds. NLWebs verktøy tar imot denne strukturerte dataen, lager embeddings og lagrer dem i en lokal eller ekstern vektordatabase.

2. **Spørsmål på naturlig språk (menneske)**: En bruker besøker nettsiden og i stedet for å navigere i menyer, skriver inn i en chat-grensesnitt: "Finn meg et familievennlig hotell i Honolulu med basseng for neste uke".

3. **NLWeb-behandling**: NLWeb-applikasjonen mottar dette spørsmålet. Den sender spørsmålet til en LLM for forståelse og søker samtidig i sin vektordatabase etter relevante hotell-lister.

4. **Nøyaktige resultater**: LLM hjelper med å tolke søkeresultatene fra databasen, identifisere de beste treffene basert på kriteriene "familievennlig", "basseng", og "Honolulu", og formaterer et naturlig språk-svar. Viktigst av alt, svaret viser til faktiske hoteller fra nettstedets katalog, og unngår oppdiktet informasjon.

5. **Interaksjon med AI-agent**: Fordi NLWeb fungerer som en MCP-server, kan en ekstern AI-reiseagent også koble til denne nettsidens NLWeb-instans. AI-agenten kan da bruke `ask` MCP-metoden for å spørre direkte til nettsiden: `ask("Er det noen veganske restauranter i Honolulu-området anbefalt av hotellet?")`. NLWeb-instansen ville behandle dette, utnytte sin database med restaurantinformasjon (hvis lastet inn), og returnere et strukturert JSON-svar.

### Har du flere spørsmål om MCP/A2A/NLWeb?

Bli med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for å møte andre lærende, delta på kontortimer og få svar på dine AI-agent-spørsmål.

## Ressurser

- [MCP for Nybegynnere](https://aka.ms/mcp-for-beginners)  
- [MCP Dokumentasjon](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb Repo](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel Guider](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi tilstreber nøyaktighet, vennligst vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Det opprinnelige dokumentet på dets opprinnelige språk skal anses som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som følge av bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->