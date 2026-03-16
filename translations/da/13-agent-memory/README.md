# Hukommelse for AI-agenter 
[![Hukommelse for AI-agenter](../../../translated_images/da/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Når man diskuterer de unikke fordele ved at skabe AI-agenter, er det især to ting, der ofte nævnes: evnen til at kalde værktøjer for at udføre opgaver og evnen til at forbedre sig over tid. Hukommelse er fundamentet for at skabe selvforbedrende agenter, der kan skabe bedre oplevelser for vores brugere.

I denne lektion ser vi på, hvad hukommelse er for AI-agenter, og hvordan vi kan administrere den og bruge den til fordel for vores applikationer.

## Introduktion

Denne lektion vil dække:

• **Forståelse af AI-agenthukommelse**: Hvad hukommelse er, og hvorfor det er vigtigt for agenter.

• **Implementering og lagring af hukommelse**: Praktiske metoder til at tilføje hukommelsesfunktioner til dine AI-agenter med fokus på korttids- og langtidshukommelse.

• **Gøre AI-agenter selvforbedrende**: Hvordan hukommelse gør det muligt for agenter at lære af tidligere interaktioner og forbedre sig over tid.

## Tilgængelige implementeringer

Denne lektion inkluderer to omfattende notebook-tutorials:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementerer hukommelse ved hjælp af Mem0 og Azure AI Search med Semantic Kernel-rammeværket

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementerer struktureret hukommelse ved hjælp af Cognee, der automatisk bygger en vidensgraf understøttet af embeddings, visualiserer grafen og intelligent opslag

## Læringsmål

Efter at have gennemført denne lektion vil du vide, hvordan du:

• **Skelner mellem forskellige typer AI-agenthukommelse**, herunder arbejdshukommelse, korttids- og langtidshukommelse samt specialiserede former som persona- og episodisk hukommelse.

• **Implementerer og administrerer korttids- og langtidshukommelse for AI-agenter** ved hjælp af Semantic Kernel-rammeværket, og udnytter værktøjer som Mem0, Cognee, Whiteboard-hukommelse samt integration med Azure AI Search.

• **Forstår principperne bag selvforbedrende AI-agenter** og hvordan robuste systemer til hukommelsesstyring bidrager til kontinuerlig læring og tilpasning.

## Forståelse af AI-agenthukommelse

I sin kerne refererer **hukommelse for AI-agenter til de mekanismer, der gør det muligt for dem at fastholde og genkalde information**. Denne information kan være specifikke detaljer om en samtale, brugerpræferencer, tidligere handlinger eller endda lærte mønstre.

Uden hukommelse er AI-applikationer ofte statsløse, hvilket betyder, at hver interaktion starter forfra. Dette fører til en gentagende og frustrerende brugeroplevelse, hvor agenten "glemmer" tidligere kontekst eller præferencer.

### Hvorfor er hukommelse vigtig?

en agents intelligens er dybt knyttet til dens evne til at genkalde og bruge tidligere information. Hukommelse gør agenter i stand til at være:

• **Reflekterende**: Lære af tidligere handlinger og resultater.

• **Interaktive**: Opretholde kontekst over en igangværende samtale.

• **Proaktive og reaktive**: Forudse behov eller reagere passende baseret på historiske data.

• **Autonome**: Operere mere selvstændigt ved at trække på lagret viden.

Målet med at implementere hukommelse er at gøre agenter mere **pålidelige og kompetente**.

### Typer af hukommelse

#### Arbejdshukommelse

Tænk på dette som en notesblok, en agent bruger under en enkelt, igangværende opgave eller tankeproces. Den holder den umiddelbare information, der er nødvendig for at beregne næste skridt.

For AI-agenter indfanger arbejdshukommelsen ofte den mest relevante information fra en samtale, selvom hele chat-historikken er lang eller trunkeret. Den fokuserer på at udtrække centrale elementer som krav, forslag, beslutninger og handlinger.

**Eksempel på arbejdshukommelse**

I en rejsebookingsagent kan arbejdshukommelsen fange brugerens aktuelle anmodning, såsom "Jeg vil gerne booke en rejse til Paris". Dette specifikke krav holdes i agentens umiddelbare kontekst for at guide den nuværende interaktion.

#### Korttidshukommelse

Denne type hukommelse fastholder information i løbet af en enkelt samtale eller session. Det er konteksten for den aktuelle chat og gør det muligt for agenten at referere tilbage til tidligere udvekslinger i dialogen.

**Eksempel på korttidshukommelse**

Hvis en bruger spørger, "Hvor meget ville en flyrejse til Paris koste?" og derefter følger op med "Hvad med overnatning der?", sikrer korttidshukommelse, at agenten ved, at "der" refererer til "Paris" i samme samtale.

#### Langtidshukommelse

Dette er information, der bevares på tværs af flere samtaler eller sessioner. Det gør det muligt for agenter at huske brugerpræferencer, historiske interaktioner eller generel viden over længere perioder. Dette er vigtigt for personalisering.

**Eksempel på langtidshukommelse**

En langtidshukommelse kan gemme, at "Ben nyder skiløb og udendørsaktiviteter, kan lide kaffe med udsigt over bjerge, og ønsker at undgå avancerede pister på grund af en tidligere skade". Denne information, lært fra tidligere interaktioner, påvirker anbefalinger i fremtidige rejseplanlægningssessioner og gør dem meget personlige.

#### Persona-hukommelse

Denne specialiserede hukommelsestype hjælper en agent med at udvikle en konsistent "personlighed" eller "persona". Den gør det muligt for agenten at huske detaljer om sig selv eller sin tiltænkte rolle, hvilket giver mere flydende og fokuserede interaktioner.

**Eksempel på persona-hukommelse**
Hvis rejseagenten er designet til at være en "ekspert i skirejser," kan persona-hukommelsen forstærke denne rolle og påvirke dens svar, så de stemmer overens med en eksperts tone og viden.

#### Workflow-/episodisk hukommelse

Denne hukommelse gemmer rækkefølgen af trin, en agent tager under en kompleks opgave, inklusive succeser og fejl. Det svarer til at huske specifikke "episoder" eller tidligere erfaringer for at lære af dem.

**Eksempel på episodisk hukommelse**

Hvis agenten forsøgte at booke en bestemt flyrejse, men det mislykkedes på grund af manglende tilgængelighed, kunne episodisk hukommelse registrere denne fejl, så agenten kan forsøge alternative fly eller informere brugeren om problemet mere oplyst ved et efterfølgende forsøg.

#### Entitetshukommelse

Dette involverer at udtrække og huske specifikke entiteter (som personer, steder eller ting) og begivenheder fra samtaler. Det gør det muligt for agenten at opbygge en struktureret forståelse af nøgleelementer, der er blevet diskuteret.

**Eksempel på entitetshukommelse**

Fra en samtale om en tidligere rejse kan agenten udtrække "Paris", "Eiffeltårnet" og "middag på Le Chat Noir-restaurant" som entiteter. I en fremtidig interaktion kunne agenten huske "Le Chat Noir" og tilbyde at lave en ny reservation der.

#### Struktureret RAG (Retrieval Augmented Generation)

Mens RAG er en bredere teknik, fremhæves "Struktureret RAG" som en kraftfuld hukommelsesteknologi. Den udtrækker tæt, struktureret information fra forskellige kilder (samtaler, e-mails, billeder) og bruger den til at forbedre præcision, recall og hastighed i svar. I modsætning til klassisk RAG, der udelukkende bygger på semantisk lighed, arbejder Struktureret RAG med den iboende struktur i informationen.

**Eksempel på Struktureret RAG**

I stedet for kun at matche nøgleord, kunne Struktureret RAG parse flydetaljer (destination, dato, tid, flyselskab) fra en e-mail og gemme dem struktureret. Dette muliggør præcise forespørgsler som "Hvilket fly bookede jeg til Paris på tirsdag?"

## Implementering og lagring af hukommelse

Implementering af hukommelse for AI-agenter involverer en systematisk proces for **hukommelsesstyring**, som inkluderer at generere, lagre, hente, integrere, opdatere og endda "glemme" (eller slette) information. Opslag er en særlig kritisk del.

### Specialiserede hukommelsesværktøjer

#### Mem0

En måde at gemme og styre agenthukommelse på er ved at bruge specialiserede værktøjer som Mem0. Mem0 fungerer som et persistenslag for hukommelse, der gør det muligt for agenter at genkalde relevante interaktioner, gemme brugerpræferencer og faktuel kontekst samt lære af succeser og fejl over tid. Idéen er her, at statsløse agenter bliver til tilstandsbevaret.

Det fungerer gennem en **tofases hukommelsespipeline: ekstraktion og opdatering**. Først sendes beskeder, der tilføjes en agents tråd, til Mem0-tjenesten, som bruger en stor sprogmodel (LLM) til at opsummere samtalehistorik og udtrække nye minder. Efterfølgende bestemmer en LLM-drevet opdateringsfase, om disse minder skal tilføjes, ændres eller slettes, og gemmer dem i en hybrid datalager, der kan inkludere vektor-, graf- og nøgle-værdi-databaser. Systemet understøtter også forskellige hukommelsestyper og kan inkorporere grafhukommelse til at styre relationer mellem entiteter.

#### Cognee

En anden kraftfuld tilgang er at bruge **Cognee**, en open source semantisk hukommelse for AI-agenter, der transformerar strukturerede og ustrukturerede data til forespørgselsbare vidensgrafer understøttet af embeddings. Cognee tilbyder en **dual-store-arkitektur**, der kombinerer vektorlignende søgning med grafrelationer, hvilket gør det muligt for agenter ikke blot at forstå, hvilke informationer der er ens, men hvordan begreber relaterer til hinanden.

Det udmærker sig i **hybridopslag**, der blander vektorligning, grafstruktur og LLM-resonering - fra rå chunk-opslag til graf-aware question answering. Systemet opretholder en **levende hukommelse**, der udvikler sig og vokser, mens den forbliver forespørgbar som én sammenhængende graf, og understøtter både korttids-sessionkontekst og langsigtet persistent hukommelse.

Cognee-notebook-tutorialen ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstrerer opbygningen af dette forenede hukommelseslag med praktiske eksempler på at ingestere forskellige datakilder, visualisere vidensgrafen og lave forespørgsler med forskellige søgestrategier skræddersyet til specifikke agentbehov.

### Lagring af hukommelse med RAG

Ud over specialiserede hukommelsesværktøjer som Mem0 kan du udnytte robuste søgetjenester som **Azure AI Search som backend til at gemme og hente minder**, især til struktureret RAG.

Dette giver dig mulighed for at forankre din agents svar i dine egne data, hvilket sikrer mere relevante og nøjagtige svar. Azure AI Search kan bruges til at gemme bruger-specifikke rejseminder, produktkataloger eller enhver anden domænespecifik viden.

Azure AI Search understøtter funktioner som **Struktureret RAG**, der excellerer i at udtrække og hente tæt, struktureret information fra store datasæt som samtalehistorikker, e-mails eller endda billeder. Dette giver "overmenneskelig præcision og recall" sammenlignet med traditionelle tekst-chunking- og embedding-tilgange.

## Gøre AI-agenter selvforbedrende

Et almindeligt mønster for selvforbedrende agenter involverer at introducere en **"vidensagent"**. Denne separate agent observerer hovedsamtalen mellem brugeren og den primære agent. Dens rolle er at:

1. **Identificere værdifuld information**: Bestemme, om en del af samtalen er værd at gemme som generel viden eller som en specifik brugerpræference.

2. **Udtrække og opsummere**: Destillere den væsentlige læring eller præference fra samtalen.

3. **Gemmes i en vidensdatabase**: Persistere denne udtrukne information, ofte i en vektordatabase, så den kan hentes senere.

4. **Forøge fremtidige forespørgsler**: Når brugeren initierer en ny forespørgsel, henter vidensagenten relevant lagret information og vedhæfter den til brugerens prompt, hvilket giver den primære agent afgørende kontekst (på samme måde som RAG).

### Optimeringer for hukommelse

• **Latensstyring**: For at undgå at sænke brugerinteraktioner kan en billigere, hurtigere model bruges indledningsvis til hurtigt at tjekke, om information er værd at gemme eller hente, og kun kalde den mere komplekse ekstraktions-/opslagsproces, når det er nødvendigt.

• **Vedligeholdelse af vidensbase**: For en voksende vidensbase kan mindre hyppigt brugt information flyttes til "cold storage" for at styre omkostninger.

## Har du flere spørgsmål om agenthukommelse?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for at møde andre lærende, deltage i åbent hus og få svar på dine spørgsmål om AI-agenter.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfraskrivelse:
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten Co-op Translator (https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, skal du være opmærksom på, at automatiske oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på sit oprindelige sprog bør betragtes som den autoritative kilde. For kritiske oplysninger anbefales en professionel menneskelig oversættelse. Vi er ikke ansvarlige for eventuelle misforståelser eller fejltolkninger, der måtte opstå som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->