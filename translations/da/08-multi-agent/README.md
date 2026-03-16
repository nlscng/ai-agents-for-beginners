[![Multi-Agent Design](../../../translated_images/da/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Klik på billedet ovenfor for at se videoen af denne lektion)_

# Multi-agent designmønstre

Så snart du begynder at arbejde på et projekt, der involverer flere agenter, bliver du nødt til at overveje multi-agent designmønsteret. Det kan dog ikke være umiddelbart klart, hvornår man skal skifte til multi-agenter, og hvad fordelene er.

## Introduktion

I denne lektion ønsker vi at besvare følgende spørgsmål:

- Hvilke scenarier er multi-agenter anvendelige i?
- Hvad er fordelene ved at bruge multi-agenter frem for bare én enkelt agent, der udfører flere opgaver?
- Hvad er byggestenene for implementering af multi-agent designmønsteret?
- Hvordan får vi indsigt i, hvordan de flere agenter interagerer med hinanden?

## Læringsmål

Efter denne lektion bør du kunne:

- Identificere scenarier, hvor multi-agenter er anvendelige
- Genkende fordelene ved at bruge multi-agenter frem for en enkelt agent.
- Forstå byggestenene for implementering af multi-agent designmønsteret.

Hvad er det større billede?

*Multi-agenter er et designmønster, der gør det muligt for flere agenter at arbejde sammen for at opnå et fælles mål*.

Dette mønster anvendes bredt inden for forskellige felter, herunder robotteknologi, autonome systemer og distribueret databehandling.

## Scenarier hvor multi-agenter er anvendelige

Så hvilke scenarier er en god brugssag for at bruge multi-agenter? Svaret er, at der er mange scenarier, hvor indsættelsen af flere agenter er gavnlig, især i følgende tilfælde:

- **Store arbejdsbyrder**: Store arbejdsbyrder kan opdeles i mindre opgaver og tildeles forskellige agenter, hvilket tillader parallel behandling og hurtigere færdiggørelse. Et eksempel på dette er ved en stor databehandlingsopgave.
- **Komplekse opgaver**: Komplekse opgaver, ligesom store arbejdsbyrder, kan opdeles i mindre delopgaver og tildeles forskellige agenter, hvor hver specialiserer sig i en bestemt del af opgaven. Et godt eksempel på dette er autonome køretøjer, hvor forskellige agenter administrerer navigation, hindringsdetektion og kommunikation med andre køretøjer.
- **Mangfoldig ekspertise**: Forskellige agenter kan have forskellig ekspertise, hvilket gør dem i stand til at håndtere forskellige aspekter af en opgave mere effektivt end en enkelt agent. Et godt eksempel på dette er inden for sundhedssektoren, hvor agenter kan håndtere diagnostik, behandlingsplaner og patientovervågning.

## Fordele ved at bruge multi-agenter frem for en enkelt agent

Et enkelt agentsystem kan fungere godt for simple opgaver, men for mere komplekse opgaver kan brugen af flere agenter give flere fordele:

- **Specialisering**: Hver agent kan specialisere sig i en specifik opgave. Manglende specialisering i en enkelt agent betyder, at du har en agent, der kan gøre alt, men som kan blive forvirret over, hvad den skal gøre, når den står over for en kompleks opgave. Den kan for eksempel ende med at udføre en opgave, som den ikke er bedst egnet til.
- **Skalerbarhed**: Det er lettere at skalere systemer ved at tilføje flere agenter frem for at overbelaste én agent.
- **Fejltolerance**: Hvis én agent fejler, kan de øvrige fortsætte med at fungere, hvilket sikrer systemets pålidelighed.

Lad os tage et eksempel: lad os booke en rejse for en bruger. Et enkelt agentsystem skulle håndtere alle aspekter af rejsebookingsprocessen, fra at finde fly til at booke hoteller og lejebiler. For at opnå dette med en enkelt agent ville agenten skulle have værktøjer til at håndtere alle disse opgaver. Dette kunne føre til et komplekst og monolitisk system, der er svært at vedligeholde og skalere. Et multi-agent system derimod kunne have forskellige agenter specialiseret i at finde fly, booke hoteller og lejebiler. Dette ville gøre systemet mere modulært, lettere at vedligeholde og skalerbart.

Sammenlign dette med et rejsebureau drevet som en lille lokal forretning kontra et rejsebureau drevet som en franchise. Den lille butik ville have én enkelt agent, der håndterer alle aspekter af rejsebookingsprocessen, mens franchisen ville have forskellige agenter, der håndterer forskellige aspekter af rejsebookingsprocessen.

## Byggesten for implementering af multi-agent designmønsteret

Før du kan implementere multi-agent designmønsteret, skal du forstå byggestenene, der udgør mønsteret.

Lad os gøre dette mere konkret ved igen at kigge på eksemplet med at booke en rejse for en bruger. I dette tilfælde vil byggestenene inkludere:

- **Agentkommunikation**: Agenter til at finde fly, booke hoteller og lejebiler skal kommunikere og dele information om brugerens præferencer og begrænsninger. Du skal beslutte protokollerne og metoderne for denne kommunikation. Hvad det konkret betyder er, at agenten for at finde fly skal kommunikere med agenten for booking af hoteller for at sikre, at hotellet bookes til de samme datoer som flyet. Det betyder, at agenterne skal dele information om brugerens rejsedatoer, hvilket betyder, at du skal beslutte *hvilke agenter der deler info og hvordan de deler info*.
- **Koordinationsmekanismer**: Agenter skal koordinere deres handlinger for at sikre, at brugerens præferencer og begrænsninger bliver opfyldt. En brugerpræference kunne være, at de ønsker et hotel tæt på lufthavnen, mens en begrænsning kunne være, at lejebiler kun er tilgængelige i lufthavnen. Det betyder, at agenten for booking af hoteller skal koordinere med agenten for booking af lejebiler for at sikre, at brugerens præferencer og begrænsninger bliver opfyldt. Det betyder, at du skal beslutte *hvordan agenterne koordinerer deres handlinger*.
- **Agentarkitektur**: Agenter skal have den interne struktur for at træffe beslutninger og lære af deres interaktioner med brugeren. Det betyder, at agenten for at finde fly skal have den interne struktur for at træffe beslutninger om, hvilke fly der skal anbefales til brugeren. Det betyder, at du skal beslutte *hvordan agenterne træffer beslutninger og lærer af deres interaktioner med brugeren*. Eksempler på hvordan en agent lærer og forbedres kunne være, at agenten for at finde fly kunne bruge en maskinlæringsmodel til at anbefale fly til brugeren baseret på deres tidligere præferencer.
- **Synlighed i multi-agent interaktioner**: Du skal kunne se, hvordan de multiple agenter interagerer med hinanden. Det betyder, at du skal have værktøjer og teknikker til at spore agenters aktiviteter og interaktioner. Dette kunne være i form af logning og overvågningsværktøjer, visualiseringsværktøjer og præstationsmålinger.
- **Multi-agent mønstre**: Der findes forskellige mønstre til implementering af multi-agent systemer, såsom centraliserede, decentraliserede og hybride arkitekturer. Du skal vælge det mønster, der passer bedst til din brugssag.
- **Menneske i løkken**: I de fleste tilfælde vil du have et menneske i løkken, og du skal instruere agenterne om, hvornår de skal anmode om menneskelig indgriben. Dette kunne være i form af, at en bruger beder om et specifikt hotel eller fly, som agenterne ikke har anbefalet, eller at bede om bekræftelse før booking af et fly eller hotel.

## Synlighed i multi-agent interaktioner

Det er vigtigt, at du har synlighed i, hvordan de multiple agenter interagerer med hinanden. Denne synlighed er essentiel for fejlfinding, optimering og sikring af systemets overordnede effektivitet. For at opnå dette skal du have værktøjer og teknikker til at spore agenters aktiviteter og interaktioner. Dette kan være i form af logning og overvågningsværktøjer, visualiseringsværktøjer og præstationsmålinger.

For eksempel, i tilfælde af booking af en rejse for en bruger, kunne du have et dashboard, der viser status for hver agent, brugerens præferencer og begrænsninger samt interaktionerne mellem agenterne. Dette dashboard kunne vise brugerens rejsedatoer, de fly, der anbefales af flyagenten, de hoteller, der anbefales af hotelagenten, og de lejebiler, der anbefales af lejeagenten. Dette ville give dig et klart overblik over, hvordan agenterne interagerer med hinanden og om brugerens præferencer og begrænsninger bliver opfyldt.

Lad os se nærmere på hver af disse aspekter.

- **Logning og overvågningsværktøjer**: Du ønsker at få logget hver handling, som en agent foretager. En logpost kunne indeholde oplysninger om den agent, der udførte handlingen, den udførte handling, tidspunktet for handlingen og resultatet af handlingen. Disse oplysninger kan derefter bruges til fejlfinding, optimering og mere.

- **Visualiseringsværktøjer**: Visualiseringsværktøjer kan hjælpe dig med at se interaktionerne mellem agenter på en mere intuitiv måde. For eksempel kunne du have en graf, der viser informationsflowet mellem agenter. Dette kan hjælpe dig med at identificere flaskehalse, ineffektivitet og andre problemer i systemet.

- **Præstationsmålinger**: Præstationsmålinger kan hjælpe dig med at spore effektiviteten af multi-agent systemet. For eksempel kunne du måle den tid, det tager at fuldføre en opgave, antallet af opgaver fuldført per tid, og nøjagtigheden af anbefalingerne lavet af agenterne. Disse oplysninger kan hjælpe dig med at identificere forbedringsområder og optimere systemet.

## Multi-agent mønstre

Lad os dykke ned i nogle konkrete mønstre, vi kan bruge til at skabe multi-agent apps. Her er nogle interessante mønstre, der er værd at overveje:

### Gruppechat

Dette mønster er nyttigt, når du ønsker at skabe en gruppechat-applikation, hvor flere agenter kan kommunikere med hinanden. Typiske brugssituationer for dette mønster inkluderer teamsamarbejde, kundesupport og sociale netværk.

I dette mønster repræsenterer hver agent en bruger i gruppechatten, og beskeder udveksles mellem agenterne via en beskedprotokol. Agenterne kan sende beskeder til gruppechatten, modtage beskeder fra gruppechatten og svare på beskeder fra andre agenter.

Dette mønster kan implementeres ved hjælp af en centraliseret arkitektur, hvor alle beskeder rutes gennem en central server, eller en decentraliseret arkitektur, hvor beskeder udveksles direkte.

![Group chat](../../../translated_images/da/multi-agent-group-chat.ec10f4cde556babd.webp)

### Overdragelse

Dette mønster er nyttigt, når du ønsker at skabe en applikation, hvor flere agenter kan overdrage opgaver til hinanden.

Typiske brugssituationer for dette mønster inkluderer kundesupport, opgavestyring og workflow-automatisering.

I dette mønster repræsenterer hver agent en opgave eller et trin i en arbejdsgang, og agenter kan overdrage opgaver til andre agenter baseret på foruddefinerede regler.

![Hand off](../../../translated_images/da/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Kollektiv filtrering

Dette mønster er nyttigt, når du ønsker at skabe en applikation, hvor flere agenter kan samarbejde om at lave anbefalinger til brugere.

Hvorfor man vil have flere agenter til at samarbejde er, fordi hver agent kan have forskellig ekspertise og kan bidrage til anbefalingsprocessen på forskellige måder.

Lad os tage et eksempel, hvor en bruger ønsker en anbefaling om den bedste aktie at købe på aktiemarkedet.

- **Brancheekspert**: En agent kunne være ekspert i en specifik branche.
- **Teknisk analyse**: En anden agent kunne være ekspert i teknisk analyse.
- **Fundamental analyse**: Og en tredje agent kunne være ekspert i fundamental analyse. Ved at samarbejde kan disse agenter give en mere omfattende anbefaling til brugeren.

![Recommendation](../../../translated_images/da/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenario: Refusionsproces

Overvej et scenarie, hvor en kunde forsøger at få refusion for et produkt. Der kan være en del agenter involveret i denne proces, men lad os opdele det mellem agenter specifikke for denne proces og generelle agenter, der kan bruges i andre processer.

**Agenter specifikke for refusionsprocessen**:

Følgende er nogle agenter, der kunne være involveret i refusionsprocessen:

- **Kundeagent**: Denne agent repræsenterer kunden og er ansvarlig for at igangsætte refusionsprocessen.
- **Sælgeragent**: Denne agent repræsenterer sælgeren og er ansvarlig for at behandle refusionen.
- **Betalingsagent**: Denne agent repræsenterer betalingsprocessen og er ansvarlig for at refundere kundens betaling.
- **Løsningsagent**: Denne agent repræsenterer løsningsprocessen og er ansvarlig for at løse eventuelle problemer, der opstår under refusionsprocessen.
- **Overholdelsesagent**: Denne agent repræsenterer overholdelsesprocessen og sikrer, at refusionsprocessen følger regler og politikker.

**Generelle agenter**:

Disse agenter kan bruges af andre dele af din virksomhed.

- **Forsendelsesagent**: Denne agent repræsenterer forsendelsesprocessen og er ansvarlig for at sende produktet tilbage til sælgeren. Denne agent kan bruges både til refusionsprocessen og til generel forsendelse af et produkt via et køb for eksempel.
- **Feedbackagent**: Denne agent repræsenterer feedbackprocessen og er ansvarlig for at indsamle feedback fra kunden. Feedback kan gives når som helst og ikke kun under refusionsprocessen.
- **Optrapningsagent**: Denne agent repræsenterer optrapningsprocessen og er ansvarlig for at eskalere problemer til et højere supportniveau. Du kan bruge denne type agent i enhver proces, hvor der er behov for at eskalere et problem.
- **Notifikationsagent**: Denne agent repræsenterer notifikationsprocessen og er ansvarlig for at sende notifikationer til kunden på forskellige stadier af refusionsprocessen.
- **Analyseagent**: Denne agent repræsenterer analyseprocessen og er ansvarlig for at analysere data relateret til refusionsprocessen.
- **Revisionsagent**: Denne agent repræsenterer revisionsprocessen og er ansvarlig for at revidere refusionsprocessen for at sikre, at den udføres korrekt.
- **Rapporteringsagent**: Denne agent repræsenterer rapporteringsprocessen og er ansvarlig for at generere rapporter om refusionsprocessen.
- **Videnagent**: Denne agent repræsenterer vidensprocessen og er ansvarlig for at vedligeholde en vidensbase med information relateret til refusionsprocessen. Denne agent kunne være vidende om både refunderinger og andre dele af din virksomhed.
- **Sikkerhedsagent**: Denne agent repræsenterer sikkerhedsprocessen og er ansvarlig for at sikre, at refusionsprocessen er sikker.
- **Kvalitetsagent**: Denne agent repræsenterer kvalitetsprocessen og er ansvarlig for at sikre kvaliteten af refusionsprocessen.

Der er ret mange agenter listet ovenfor, både for den specifikke refusionsproces men også for de generelle agenter, der kan bruges i andre dele af din virksomhed. Forhåbentlig giver dette dig en idé om, hvordan du kan beslutte, hvilke agenter du vil bruge i dit multi-agent system.

## Opgave

Design et multi-agent system til en kundesupportproces. Identificer de agenter, der er involveret i processen, deres roller og ansvar, og hvordan de interagerer med hinanden. Overvej både agenter specifikke for kundesupportprocessen og generelle agenter, der kan bruges i andre dele af din virksomhed.
> Tænk dig om, før du læser den følgende løsning, du kan få brug for flere agenter, end du tror.

> TIP: Tænk på de forskellige faser i kundesupportprocessen, og overvej også agenter, der er nødvendige for ethvert system.

## Løsning

[Løsning](./solution/solution.md)

## Vidensprøver

Spørgsmål: Hvornår bør du overveje at bruge multi-agenter?

- [ ] A1: Når du har en lille arbejdsbyrde og en simpel opgave.
- [ ] A2: Når du har en stor arbejdsbyrde
- [ ] A3: Når du har en simpel opgave.

[Løsningsquiz](./solution/solution-quiz.md)

## Resumé

I denne lektion har vi kigget på multi-agent designmønsteret, herunder scenarier hvor multi-agenter er anvendelige, fordelene ved at bruge multi-agenter fremfor en enkelt agent, byggestenene til implementering af multi-agent designmønsteret, og hvordan man får indsigt i, hvordan de flere agenter interagerer med hinanden.

### Har du flere spørgsmål om Multi-Agent Designmønsteret?

Deltag i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for at mødes med andre lærende, deltage i kontortimer og få besvaret dine spørgsmål om AI-agenter.

## Yderligere ressourcer

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen designmønstre</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentiske designmønstre</a>

## Forrige lektion

[Planlægning af design](../07-planning-design/README.md)

## Næste lektion

[Metakognition i AI-agenter](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokument er oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, bedes du være opmærksom på, at automatiske oversættelser kan indeholde fejl eller unøjagtigheder. Det originale dokument på dets oprindelige sprog bør betragtes som den autoritative kilde. For kritisk information anbefales professionel menneskelig oversættelse. Vi påtager os intet ansvar for misforståelser eller fejltolkninger, der måtte opstå ved brug af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->