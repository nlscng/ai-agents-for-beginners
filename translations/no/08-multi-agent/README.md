[![Multi-agent designmønstre](../../../translated_images/no/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Klikk bildet ovenfor for å se video av denne leksjonen)_

# Multi-agent designmønstre

Så snart du begynner å jobbe på et prosjekt som involverer flere agenter, må du vurdere designmønsteret for flere agenter. Det er imidlertid ikke alltid umiddelbart klart når man bør bytte til flere agenter og hva fordelene er.

## Innledning

I denne leksjonen prøver vi å svare på følgende spørsmål:

- Hvilke scenarier er aktuelle for bruk av flere agenter?
- Hva er fordelene ved å bruke flere agenter framfor én enkelt agent som utfører flere oppgaver?
- Hva er byggesteinene for å implementere designmønsteret for flere agenter?
- Hvordan får vi innsyn i hvordan de flere agentene samhandler med hverandre?

## Læringsmål

Etter denne leksjonen skal du kunne:

- Identifisere scenarier hvor flere agenter er aktuelle
- Gjenkjenne fordelene ved å bruke flere agenter framfor én enkelt agent.
- Forstå byggesteinene for å implementere designmønsteret for flere agenter.

Hva er det store bildet?

*Flere agenter er et designmønster som gjør det mulig for flere agenter å arbeide sammen for å oppnå et felles mål*.

Dette mønsteret brukes mye innen ulike felt, inkludert robotikk, autonome systemer og distribuert databehandling.

## Scenarier hvor flere agenter er aktuelle

Så hvilke scenarier er et godt brukstilfelle for å bruke flere agenter? Svaret er at det finnes mange scenarier hvor det er fordelaktig å benytte flere agenter, spesielt i følgende tilfeller:

- **Store arbeidsmengder**: Store arbeidsmengder kan deles opp i mindre oppgaver og tildeles ulike agenter, noe som tillater parallell behandling og raskere gjennomføring. Et eksempel på dette er ved behandling av store datamengder.
- **Komplekse oppgaver**: Komplekse oppgaver, som store arbeidsmengder, kan brytes ned i mindre deloppgaver og tildeles ulike agenter, hvor hver spesialiserer seg på en bestemt del av oppgaven. Et godt eksempel er autonome kjøretøy hvor forskjellige agenter håndterer navigasjon, hindringsdeteksjon og kommunikasjon med andre kjøretøy.
- **Ulike ekspertiser**: Ulike agenter kan ha ulik ekspertise, som gjør at de kan håndtere forskjellige aspekter av en oppgave mer effektivt enn en enkelt agent. Et godt eksempel på dette er innen helsesektoren, hvor agenter kan håndtere diagnostikk, behandlingsplaner og pasientovervåkning.

## Fordeler ved å bruke flere agenter framfor én agent

Et enkelt agentsystem kan fungere godt for enkle oppgaver, men for mer komplekse oppgaver kan bruk av flere agenter gi flere fordeler:

- **Spesialisering**: Hver agent kan være spesialisert for en bestemt oppgave. Mangel på spesialisering i en enkelt agent betyr at du har en agent som kan gjøre alt, men som kan bli forvirret over hva den skal gjøre når den står overfor en kompleks oppgave. Den kan for eksempel ende opp med å utføre en oppgave den ikke egner seg best for.
- **Skalerbarhet**: Det er enklere å skalere systemer ved å legge til flere agenter i stedet for å overbelaste en enkelt agent.
- **Feiltoleranse**: Hvis en agent feiler, kan andre fortsette å fungere, noe som sikrer systemets pålitelighet.

La oss ta et eksempel: la oss bestille en reise for en bruker. Et enkelt agentsystem måtte håndtere alle aspekter av reisebestillingsprosessen, fra å finne fly til å bestille hoteller og leiebiler. For å få dette til med én enkelt agent, måtte agenten ha verktøy for å håndtere alle disse oppgavene. Dette kan føre til et komplekst og monolitisk system som er vanskelig å vedlikeholde og skalere. Et multi-agent-system, derimot, kan ha ulike agenter spesialisert på å finne fly, bestille hoteller og leiebiler. Dette vil gjøre systemet mer modulært, enklere å vedlikeholde og skalerbart.

Sammenlign dette med et reisebyrå drevet som en liten familiedrevet butikk versus et reisebyrå drevet som en franchise. Den lille familien ville ha en enkelt agent som håndterer alle aspekter av reisebestillingsprosessen, mens franchisen ville ha forskjellige agenter som håndterer ulike aspekter av prosessen.

## Byggesteiner for å implementere designmønsteret for flere agenter

Før du kan implementere designmønsteret for flere agenter, må du forstå byggesteinene som utgjør mønsteret.

La oss konkretisere dette ved igjen å se på eksemplet med å bestille en reise for en bruker. I dette tilfellet vil byggesteinene inkludere:

- **Agentkommunikasjon**: Agenter for å finne fly, bestille hoteller og leiebiler må kommunisere og dele informasjon om brukerens preferanser og begrensninger. Du må bestemme protokollene og metodene for denne kommunikasjonen. Konkret betyr dette at agenten som finner fly må kommunisere med agenten som bestiller hotell for å sikre at hotellet er booket for de samme datoene som flyet. Det betyr at agentene må dele informasjon om brukerens reisedatoer, hvilket betyr at du må bestemme *hvilke agenter som deler informasjon og hvordan de deler informasjon*.
- **Koordineringsmekanismer**: Agenter må koordinere handlingene sine for å sikre at brukerens preferanser og begrensninger blir møtt. En brukerprefereanse kan være at de ønsker et hotell nær flyplassen, mens en begrensning kan være at leiebiler kun er tilgjengelige på flyplassen. Dette betyr at agenten som bestiller hotell må koordinere med agenten som bestiller leiebil for å sikre at brukerens preferanser og begrensninger blir møtt. Dette betyr at du må bestemme *hvordan agentene koordinerer handlingene sine*.
- **Agentarkitektur**: Agenter må ha en intern struktur for å ta avgjørelser og lære av sine interaksjoner med brukeren. Dette betyr at agenten som finner fly må ha en intern struktur for å ta beslutninger om hvilke fly som skal anbefales til brukeren. Dette betyr at du må bestemme *hvordan agentene tar beslutninger og lærer fra sine interaksjoner med brukeren*. Eksempler på hvordan en agent lærer og forbedrer seg kan være at agenten som finner fly kan bruke en maskinlæringsmodell for å anbefale fly til brukeren basert på tidligere preferanser.
- **Innsyn i interaksjoner mellom flere agenter**: Du må ha innsyn i hvordan de flere agentene samhandler med hverandre. Dette betyr at du må ha verktøy og teknikker for å spore agentaktiviteter og interaksjoner. Dette kan være i form av logging- og overvåkingsverktøy, visualiseringsverktøy og ytelsesmetrikker.
- **Mønstre for flere agenter**: Det finnes ulike mønstre for å implementere multi-agent-systemer, som sentraliserte, desentraliserte og hybride arkitekturer. Du må bestemme hvilket mønster som passer best for ditt brukstilfelle.
- **Mennesket i løkken**: I de fleste tilfeller vil du ha et menneske i løkken, og du må instruere agentene om når de skal be om menneskelig inngripen. Dette kan være i form av at en bruker ber om et bestemt hotell eller fly som agentene ikke har anbefalt, eller ber om bekreftelse før booking av fly eller hotell.

## Innsyn i interaksjoner mellom flere agenter

Det er viktig at du har innsyn i hvordan de flere agentene samhandler med hverandre. Dette innsynet er avgjørende for feilsøking, optimalisering og for å sikre den overordnede effektiviteten i systemet. For å oppnå dette må du ha verktøy og teknikker for å spore agentaktiviteter og interaksjoner. Dette kan være i form av logging- og overvåkingsverktøy, visualiseringsverktøy og ytelsesmetrikker.

For eksempel, i tilfelle bestilling av en reise for en bruker, kan du ha et dashbord som viser statusen til hver agent, brukerens preferanser og begrensninger, og interaksjonene mellom agentene. Dette dashbordet kan vise brukerens reisedatoer, flyene som er anbefalt av flåtageenten, hotellene som er anbefalt av hotellagenten, og leiebilene som er anbefalt av leiebilagenten. Dette vil gi deg en klar oversikt over hvordan agentene samhandler med hverandre og om brukerens preferanser og begrensninger blir møtt.

La oss se nærmere på hver av disse aspektene.

- **Logging- og overvåkingsverktøy**: Du bør ha logging for hver handling som tas av en agent. En loggoppføring kan lagre informasjon om agenten som tok handlingen, handlingen som ble tatt, tidspunktet handlingen ble tatt, og utfallet av handlingen. Denne informasjonen kan deretter brukes til feilsøking, optimalisering og mer.

- **Visualiseringsverktøy**: Visualiseringsverktøy kan hjelpe deg å se interaksjonene mellom agenter på en mer intuitiv måte. For eksempel kan du ha en graf som viser informasjonsflyten mellom agenter. Dette kan hjelpe deg med å identifisere flaskehalser, ineffektivitet og andre problemer i systemet.

- **Ytelsesmetrikker**: Ytelsesmetrikker kan hjelpe deg å spore hvor effektivt multi-agent-systemet er. For eksempel kan du spore tiden det tar å fullføre en oppgave, antall oppgaver fullført per tidsenhet, og nøyaktigheten til anbefalingene agentene gir. Denne informasjonen kan hjelpe deg med å identifisere forbedringsområder og optimalisere systemet.

## Mønstre for multi-agent-systemer

La oss dykke ned i noen konkrete mønstre vi kan bruke for å lage multi-agent-apper. Her er noen interessante mønstre verdt å vurdere:

### Gruppechat

Dette mønsteret er nyttig når du vil lage en gruppechat-applikasjon hvor flere agenter kan kommunisere med hverandre. Typiske brukstilfeller for dette mønsteret inkluderer teamsamarbeid, kundestøtte og sosiale nettverk.

I dette mønsteret representerer hver agent en bruker i gruppechatten, og meldinger utveksles mellom agenter ved hjelp av en meldingsprotokoll. Agentene kan sende meldinger til gruppechatten, motta meldinger fra gruppechatten, og svare på meldinger fra andre agenter.

Dette mønsteret kan implementeres ved hjelp av en sentralisert arkitektur hvor alle meldinger rutes gjennom en sentral server, eller en desentralisert arkitektur hvor meldinger utveksles direkte.

![Gruppechat](../../../translated_images/no/multi-agent-group-chat.ec10f4cde556babd.webp)

### Overlevering

Dette mønsteret er nyttig når du vil lage en applikasjon hvor flere agenter kan overlevere oppgaver til hverandre.

Typiske brukstilfeller for dette mønsteret inkluderer kundestøtte, oppgavehåndtering og arbeidsflytautomatisering.

I dette mønsteret representerer hver agent en oppgave eller et steg i en arbeidsflyt, og agenter kan overlevere oppgaver til andre agenter basert på forhåndsdefinerte regler.

![Hand off](../../../translated_images/no/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Kollaborativ filtrering

Dette mønsteret er nyttig når du vil lage en applikasjon hvor flere agenter kan samarbeide for å gi anbefalinger til brukere.

Hvorfor du vil at flere agenter skal samarbeide er fordi hver agent kan ha ulik ekspertise og kan bidra til anbefalingsprosessen på forskjellige måter.

La oss ta et eksempel hvor en bruker ønsker en anbefaling på den beste aksjen å kjøpe på aksjemarkedet.

- **Bransjeekspert**: En agent kan være ekspert innen en spesifikk bransje.
- **Teknisk analyse**: En annen agent kan være ekspert på teknisk analyse.
- **Fundamental analyse**: Og en annen agent kan være ekspert på fundamental analyse. Ved å samarbeide kan disse agentene gi en mer omfattende anbefaling til brukeren.

![Anbefaling](../../../translated_images/no/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenario: Refusjonsprosess

Vurder et scenario hvor en kunde forsøker å få refusjon for et produkt; det kan være ganske mange agenter involvert i denne prosessen, men la oss dele det opp mellom agenter spesifikke for denne prosessen og generelle agenter som kan brukes i andre prosesser.

**Agenter spesifikke for refusjonsprosessen**:

Følgende er noen agenter som kan være involvert i refusjonsprosessen:

- **Kundeagent**: Denne agenten representerer kunden og er ansvarlig for å initiere refusjonsprosessen.
- **Selgeragent**: Denne agenten representerer selgeren og er ansvarlig for å behandle refusjonen.
- **Betalingsagent**: Denne agenten representerer betalingsprosessen og er ansvarlig for å refundere kundens betaling.
- **Løsningsagent**: Denne agenten representerer løsningsprosessen og er ansvarlig for å løse eventuelle problemer som oppstår under refusjonsprosessen.
- **Samsvarsagent**: Denne agenten representerer samsvarsprosessen og er ansvarlig for å sikre at refusjonsprosessen overholder regelverk og retningslinjer.

**Generelle agenter**:

Disse agentene kan brukes av andre deler av virksomheten din.

- **Fraktagent**: Denne agenten representerer fraktprosessen og er ansvarlig for å sende produktet tilbake til selgeren. Denne agenten kan brukes både i refusjonsprosessen og til generell frakt av et produkt ved et kjøp, for eksempel.
- **Tilbakemeldingsagent**: Denne agenten representerer tilbakemeldingsprosessen og er ansvarlig for å samle inn tilbakemeldinger fra kunden. Tilbakemeldinger kan innhentes til enhver tid og ikke bare under refusjonsprosessen.
- **Eskaleringsagent**: Denne agenten representerer eskaleringsprosessen og er ansvarlig for å eskalere problemer til et høyere støttenivå. Du kan bruke denne typen agent for enhver prosess hvor du trenger å eskalere et problem.
- **Varslingsagent**: Denne agenten representerer varslingsprosessen og er ansvarlig for å sende varsler til kunden på ulike stadier av refusjonsprosessen.
- **Analyseagent**: Denne agenten representerer analyseprosessen og er ansvarlig for å analysere data knyttet til refusjonsprosessen.
- **Revisjonsagent**: Denne agenten representerer revisjonsprosessen og er ansvarlig for å revidere refusjonsprosessen for å sikre at den blir gjennomført korrekt.
- **Rapporteringsagent**: Denne agenten representerer rapporteringsprosessen og er ansvarlig for å generere rapporter om refusjonsprosessen.
- **Kunnskapsagent**: Denne agenten representerer kunnskapsprosessen og er ansvarlig for å vedlikeholde en kunnskapsbase med informasjon knyttet til refusjonsprosessen. Denne agenten kan være kunnskapsrik både om refusjoner og andre deler av virksomheten din.
- **Sikkerhetsagent**: Denne agenten representerer sikkerhetsprosessen og er ansvarlig for å sikre sikkerheten i refusjonsprosessen.
- **Kvalitetsagent**: Denne agenten representerer kvalitetsprosessen og er ansvarlig for å sikre kvaliteten på refusjonsprosessen.

Det er ganske mange agenter listet opp tidligere, både for den spesifikke refusjonsprosessen og for de generelle agentene som kan brukes i andre deler av virksomheten din. Forhåpentligvis gir dette deg en idé om hvordan du kan bestemme hvilke agenter du skal bruke i ditt multi-agent-system.

## Oppgave

Design et multi-agent-system for en kundestøtteprosess. Identifiser agentene som er involvert i prosessen, deres roller og ansvar, og hvordan de samhandler med hverandre. Vurder både agenter som er spesifikke for kundestøtteprosessen og generelle agenter som kan brukes i andre deler av virksomheten din.
> Tenk deg om før du leser følgende løsning, du kan trenge flere agenter enn du tror.

> TIPS: Tenk på de ulike fasene i kundestøtteprosessen og vurder også hvilke agenter som trengs for ethvert system.

## Løsning

[Løsning](./solution/solution.md)

## Kunnskapssjekker

Spørsmål: Når bør du vurdere å bruke multi-agenter?

- [ ] A1: Når du har liten arbeidsmengde og en enkel oppgave.
- [ ] A2: Når du har stor arbeidsmengde
- [ ] A3: Når du har en enkel oppgave.

[Løsningsquiz](./solution/solution-quiz.md)

## Sammendrag

I denne leksjonen har vi sett på multi-agent designmønsteret, inkludert scenarier hvor multi-agenter er aktuelle, fordelene ved å bruke flere agenter framfor en enkelt agent, byggesteinene for å implementere multi-agent designmønsteret, og hvordan få innsikt i hvordan de ulike agentene samhandler med hverandre.

### Har du flere spørsmål om designmønsteret for multi-agenter?

Bli med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for å møte andre deltakere, delta på kontortid og få svar på spørsmål om AI-agenter.

## Tilleggsressurser

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen designmønstre</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentiske designmønstre</a>


## Forrige leksjon

[Planleggingsdesign](../07-planning-design/README.md)

## Neste leksjon

[Metakognisjon i AI-agenter](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfraskrivelse:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Originaldokumentet på det opprinnelige språket bør anses som den autoritative kilden. For kritisk informasjon anbefales profesjonell, menneskelig oversettelse. Vi er ikke ansvarlige for misforståelser eller feiltolkninger som oppstår som følge av bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->