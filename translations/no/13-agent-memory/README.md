# Minne for AI-agenter 
[![Agent Memory](../../../translated_images/no/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Når man diskuterer de unike fordelene ved å lage AI-agenter, diskuteres hovedsakelig to ting: evnen til å kalle verktøy for å utføre oppgaver og evnen til å forbedre seg over tid. Minne ligger til grunn for å skape en selvforbedrende agent som kan skape bedre opplevelser for våre brukere.

I denne leksen skal vi se på hva minne er for AI-agenter og hvordan vi kan håndtere det og bruke det til fordel for våre applikasjoner.

## Introduksjon

Denne leksen vil dekke:

• **Forståelse av AI-agenters minne**: Hva minne er og hvorfor det er essensielt for agenter.

• **Implementering og lagring av minne**: Praktiske metoder for å legge til minnekapasiteter til dine AI-agenter, med fokus på korttids- og langsiktig minne.

• **Gjøre AI-agenter selvforbedrende**: Hvordan minne gjør det mulig for agenter å lære fra tidligere interaksjoner og forbedre seg over tid.

## Tilgjengelige implementeringer

Denne leksen inkluderer to omfattende notatboken veiledninger:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementerer minne ved bruk av Mem0 og Azure AI Search med Semantic Kernel-rammeverket

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementerer strukturert minne ved bruk av Cognee, som automatisk bygger en kunnskapsgraf støttet av embeddings, visualiserer grafen og intelligent henting

## Læringsmål

Etter å ha fullført denne leksen, vil du vite hvordan du kan:

• **Skille mellom ulike typer AI-agentminne**, inkludert arbeidsminne, korttidsminne og langtidsminne, samt spesialiserte former som persona- og episodisk minne.

• **Implementere og administrere korttids- og langtidsminne for AI-agenter** ved bruk av Semantic Kernel-rammeverket, og utnytte verktøy som Mem0, Cognee, Whiteboard-minne, og integrasjon med Azure AI Search.

• **Forstå prinsippene bak selvforbedrende AI-agenter** og hvordan robuste minnehåndteringssystemer bidrar til kontinuerlig læring og tilpasning.

## Forståelse av AI-agentminne

I sin kjerne refererer **minne for AI-agenter til mekanismene som lar dem beholde og hente informasjon**. Denne informasjonen kan være spesifikke detaljer om en samtale, brukerpreferanser, tidligere handlinger, eller til og med lærte mønstre.

Uten minne er AI-applikasjoner ofte statsløse, noe som betyr at hver interaksjon starter på nytt. Dette fører til en repeterende og frustrerende brukeropplevelse der agenten "glemmer" tidligere kontekst eller preferanser.

### Hvorfor er minne viktig?

En agents intelligens er dypt knyttet til dens evne til å hente frem og bruke tidligere informasjon. Minne gjør at agenter kan være:

• **Reflekterende**: Lære av tidligere handlinger og resultater.

• **Interaktive**: Opprettholde kontekst i en pågående samtale.

• **Proaktive og reaktive**: Forutse behov eller svare hensiktsmessig basert på historiske data.

• **Autonome**: Operere mer uavhengig ved å trekke på lagret kunnskap.

Målet med å implementere minne er å gjøre agenter mer **pålitelige og kapable**.

### Typer minne

#### Arbeidsminne

Tenk på dette som et arkagenten bruker under en enkelt, pågående oppgave eller tankerekke. Det holder umiddelbar informasjon som trengs for å beregne neste steg.

For AI-agenter fanger arbeidsminne ofte den mest relevante informasjonen fra en samtale, selv om hele chatthistorikken er lang eller trunkert. Det fokuserer på å trekke ut nøkkel elementer som krav, forslag, beslutninger og handlinger.

**Arbeidsminne-eksempel**

I en reisebestillingsagent kan arbeidsminne fange opp brukerens nåværende forespørsel, som "Jeg vil bestille en tur til Paris". Dette spesifikke kravet holdes i agentens umiddelbare kontekst for å styre den nåværende interaksjonen.

#### Korttidsminne

Denne typen minne beholder informasjon i løpet av en enkelt samtale eller økt. Det er konteksten for den nåværende chatten, som lar agenten referere tilbake til tidligere turer i dialogen.

**Korttidsminne-eksempel**

Hvis en bruker spør, "Hvor mye koster en flyreise til Paris?" og så følger opp med "Hva med overnatting der?", sikrer korttidsminne at agenten vet at "der" refererer til "Paris" innen samme samtale.

#### Langtidsminne

Dette er informasjon som vedvarer over flere samtaler eller økter. Det lar agenter huske brukerpreferanser, historiske interaksjoner eller generell kunnskap over lengre tid. Dette er viktig for personlig tilpasning.

**Langtidsminne-eksempel**

Et langtidsminne kan lagre at "Ben liker å stå på ski og utendørsaktiviteter, liker kaffe med utsikt mot fjellet, og ønsker å unngå avanserte skiløyper på grunn av en tidligere skade". Denne informasjonen, lært fra tidligere interaksjoner, påvirker anbefalinger i fremtidige reiseplanleggingsøkter og gjør dem svært personlige.

#### Persona-minne

Denne spesialiserte minnetypen hjelper en agent med å utvikle en konsekvent "personlighet" eller "persona". Det lar agenten huske detaljer om seg selv eller sin tiltenkte rolle, noe som gjør interaksjonene mer flytende og fokusert.

**Persona-minne-eksempel**

Hvis reiseagenten er designet for å være en "ekspert på skiplanlegging," kan persona-minne forsterke denne rollen og påvirke svarene slik at de samsvarer med en eksperts tone og kunnskap.

#### Workflow/Episodisk minne

Dette minnet lagrer rekkefølgen av trinn en agent tar under en kompleks oppgave, inkludert suksesser og feil. Det er som å huske spesifikke "episoder" eller tidligere erfaringer for å lære av dem.

**Episodisk minne-eksempel**

Hvis agenten forsøkte å bestille en spesifikk flyreise, men dette feilet på grunn av utilgjengelighet, kan episodisk minne registrere denne feilen, slik at agenten kan prøve alternative flyvninger eller informere brukeren mer informert om problemet ved neste forsøk.

#### Entity Memory

Dette innebærer å trekke ut og huske spesifikke enheter (som personer, steder eller ting) og hendelser fra samtaler. Det lar agenten bygge en strukturert forståelse av nøkkel elementer som diskuteres.

**Entity Memory-eksempel**

Fra en samtale om en tidligere tur kan agenten trekke ut "Paris," "Eiffeltårnet," og "middag på restauranten Le Chat Noir" som enheter. I en fremtidig interaksjon kan agenten huske "Le Chat Noir" og tilby å lage en ny reservasjon der.

#### Strukturert RAG (Retrieval Augmented Generation)

Mens RAG er en bredere teknikk, fremheves "Strukturert RAG" som en kraftfull minneteknologi. Den trekker ut tett, strukturert informasjon fra ulike kilder (samtaler, e-poster, bilder) og bruker det for å forbedre presisjon, tilbakehenting og hastighet i svar. I motsetning til klassisk RAG som kun baseres på semantisk likhet, arbeider Strukturert RAG med den iboende strukturen i informasjon.

**Strukturert RAG-eksempel**

I stedet for bare å matche søkeord kan Strukturert RAG analysere flydetaljer (destinasjon, dato, tid, flyselskap) fra en e-post og lagre dem på en strukturert måte. Dette tillater presise spørringer som "Hvilket fly bestilte jeg til Paris på tirsdag?"

## Implementering og lagring av minne

Å implementere minne for AI-agenter innebærer en systematisk prosess med **minnehåndtering**, som inkluderer generering, lagring, henting, integrering, oppdatering og til og med "glemming" (eller sletting) av informasjon. Henting er et særlig viktig aspekt.

### Spesialiserte minneverktøy

#### Mem0

En måte å lagre og administrere agentminne på er ved bruk av spesialiserte verktøy som Mem0. Mem0 fungerer som et vedvarende minnelag, som lar agenter hente relevante interaksjoner, lagre brukerpreferanser og faktuell kontekst, og lære av suksesser og feil over tid. Ideen her er at statsløse agenter blir til tilstandsfulle.

Det fungerer gjennom en **toveis minnebehandling: ekstraksjon og oppdatering**. Først sendes meldinger lagt til i en agents tråd til Mem0-tjenesten, som bruker en stor språkmodell (LLM) for å oppsummere samtalehistorikk og trekke ut nye minner. Deretter avgjør en LLM-drevet oppdateringsfase om minnene skal legges til, endres eller slettes, og lagrer dem i en hybrid databutikk som kan inkludere vektor-, graf- og nøkkel-verdi-databaser. Systemet støtter også ulike minnetyper og kan inkorporere grafminne for å administrere relasjoner mellom enheter.

#### Cognee

En annen kraftfull tilnærming er å bruke **Cognee**, et åpen kildekode semantisk minnesystem for AI-agenter som omformer strukturerte og ustrukturerte data til søkbare kunnskapsgrafer støttet av embeddings. Cognee tilbyr en **duallager-arkitektur** som kombinerer vektorlignende søk med grafrelasjoner, noe som gjør agenter i stand til å forstå ikke bare hva informasjon som er lik, men hvordan konsepter relaterer til hverandre.

Det utmerker seg i **hybrid henting** som blander vektorsimilaritet, grafstruktur og LLM-ressonnement – fra rå chunk-oppslag til graf-bevisst spørsmålssvar. Systemet opprettholder et **levende minne** som utvikler og vokser mens det forblir søkbart som en sammenkoblet graf, og støtter både korttidsøktkontekst og langtidsvedvarende minne.

Cognee-notatboken ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstrerer bygging av dette enhetlige minnelaget, med praktiske eksempler på å ta inn ulike datakilder, visualisere kunnskapsgrafen og søke med forskjellige søkestrategier tilpasset spesifikke agentbehov.

### Lagring av minne med RAG

Utover spesialiserte minneverktøy som Mem0, kan du benytte robuste søketjenester som **Azure AI Search som backend for lagring og henting av minner**, spesielt for strukturert RAG.

Dette lar deg forankre agentens svar med dine egne data, og sikrer mer relevante og nøyaktige svar. Azure AI Search kan brukes til å lagre brukerspesifikke reiseminner, produktkataloger eller annen domenespesifikk kunnskap.

Azure AI Search støtter funksjoner som **Strukturert RAG**, som utmerker seg i å trekke ut og hente tett, strukturert informasjon fra store datasett som samtalehistorikk, e-poster eller til og med bilder. Dette gir "overmenneskelig presisjon og tilbakehenting" sammenlignet med tradisjonelle metoder basert på tekstbiter og embedding.

## Gjøre AI-agenter selvforbedrende

Et vanlig mønster for selvforbedrende agenter innebærer å introdusere en **"kunnskapsagent"**. Denne separate agenten observerer hovedsamtalen mellom brukeren og den primære agenten. Dens rolle er å:

1. **Identifisere verdifull informasjon**: Bestemme om noen del av samtalen er verdt å lagre som generell kunnskap eller en spesifikk brukerpreferanse.

2. **Trekke ut og oppsummere**: Destillere den essensielle læringen eller preferansen fra samtalen.

3. **Lagre i en kunnskapsdatabase**: Bevare denne uttrukne informasjonen, ofte i en vektordatabasen, slik at den kan hentes frem senere.

4. **Forsterke fremtidige spørringer**: Når brukeren starter en ny forespørsel, henter kunnskapsagenten relevant lagret informasjon og legger den til i brukerens prompt, og gir avgjørende kontekst til hovedagenten (likt som RAG).

### Optimaliseringer for minne

• **Latenshåndtering**: For å unngå å senke brukerinteraksjoner kan en rimeligere, raskere modell brukes innledningsvis for raskt å sjekke om informasjon er verdt å lagre eller hente, og bare aktivere den mer komplekse ekstraksjons-/hentingsprosessen når det er nødvendig.

• **Vedlikehold av kunnskapsdatabase**: For en voksende kunnskapsbase kan mindre brukt informasjon flyttes til "kaldlagring" for å styre kostnader.

## Har du flere spørsmål om agentminne?

Bli med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for å møte andre lærende, delta på office hours og få dine AI-agent-spørsmål besvart.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Det originale dokumentet på dets opprinnelige språk skal betraktes som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som følge av bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->