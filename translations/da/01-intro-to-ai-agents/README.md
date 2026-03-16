[![Introduktion til AI-agenter](../../../translated_images/da/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Klik på billedet ovenfor for at se videoen til denne lektion)_


# Introduktion til AI-agenter og anvendelsestilfælde

Velkommen til kurset "AI-agenter for begyndere"! Dette kursus giver grundlæggende viden og anvendte eksempler til opbygning af AI-agenter.

Deltag i <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord-fællesskab</a> for at møde andre kursister og AI-agentbyggere og stille spørgsmål om dette kursus.

For at starte dette kursus begynder vi med at få en bedre forståelse af, hvad AI-agenter er, og hvordan vi kan bruge dem i de applikationer og arbejdsgange, vi bygger.

## Introduktion

Denne lektion dækker:

- Hvad er AI-agenter, og hvilke forskellige typer agenter findes der?
- Hvilke anvendelsestilfælde er bedst for AI-agenter, og hvordan kan de hjælpe os?
- Hvad er nogle af de grundlæggende byggesten, når man designer agentiske løsninger?

## Læringsmål
Efter at have gennemført denne lektion, bør du kunne:

- Forstå begreberne omkring AI-agenter og hvordan de adskiller sig fra andre AI-løsninger.
- Anvende AI-agenter mest effektivt.
- Designe agentiske løsninger produktivt for både brugere og kunder.

## Definition af AI-agenter og typer af AI-agenter

### Hvad er AI-agenter?

AI-agenter er **systemer**, der gør det muligt for **Store sprogmodeller(LLMs)** at **udføre handlinger** ved at udvide deres kapaciteter ved at give LLMs **adgang til værktøjer** og **viden**.

Lad os opdele denne definition i mindre dele:

- **System** - Det er vigtigt at tænke på agenter ikke blot som en enkelt komponent, men som et system af mange komponenter. På det basale niveau er komponenterne i en AI-agent:
  - **Miljø** - Det definerede rum, hvor AI-agenten opererer. For eksempel, hvis vi havde en rejsebookings-AI-agent, kunne miljøet være rejsebookingssystemet, som AI-agenten bruger til at fuldføre opgaver.
  - **Sensorer** - Miljøer har information og giver feedback. AI-agenter bruger sensorere til at indsamle og fortolke disse oplysninger om den aktuelle tilstand i miljøet. I rejsebookings-agent-eksemplet kan rejsebookingssystemet give oplysninger såsom hoteltilgængelighed eller flypriser.
  - **Aktuatorer** - Når AI-agenten modtager den aktuelle tilstand af miljøet, bestemmer agenten for den aktuelle opgave, hvilken handling der skal udføres for at ændre miljøet. For rejsebookingsagenten kan det være at booke et tilgængeligt værelse for brugeren.

![Hvad er AI-agenter?](../../../translated_images/da/what-are-ai-agents.1ec8c4d548af601a.webp)

**Store sprogmodeller** - Konceptet agenter eksisterede før skabelsen af LLMs. Fordelen ved at bygge AI-agenter med LLMs er deres evne til at fortolke menneskesprog og data. Denne evne gør det muligt for LLMs at fortolke miljømæssige oplysninger og definere en plan for at ændre miljøet.

**Udføre handlinger** - Uden for AI-agent-systemer er LLMs begrænset til situationer, hvor handlingen er at generere indhold eller information baseret på en brugers prompt. Inde i AI-agent-systemer kan LLMs opnå opgaver ved at fortolke brugerens anmodning og bruge værktøjer, der er tilgængelige i deres miljø.

**Adgang til værktøjer** - Hvilke værktøjer LLM har adgang til defineres af 1) det miljø, det opererer i, og 2) udvikleren af AI-agenten. I vores rejseagent-eksempel er agentens værktøjer begrænset af de operationer, der er tilgængelige i bookingsystemet, og/eller udvikleren kan begrænse agentens værktøjsadgang til fly.

**Hukommelse+Viden** - Hukommelse kan være kortvarig i konteksten af samtalen mellem brugeren og agenten. Langsigtet, uden for de oplysninger, der leveres af miljøet, kan AI-agenter også hente viden fra andre systemer, tjenester, værktøjer og endda andre agenter. I rejseagent-eksemplet kunne denne viden være oplysninger om brugerens rejsepræferencer, der findes i en kundedatabase.

### De forskellige typer af agenter

Nu hvor vi har en generel definition af AI-agenter, lad os se på nogle specifikke agenttyper og hvordan de ville blive anvendt på en rejsebookings-AI-agent.

| **Agenttype**                | **Beskrivelse**                                                                                                                       | **Eksempel**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Enkle refleksagenter**      | Udfører øjeblikkelige handlinger baseret på foruddefinerede regler.                                                                   | Rejseagenten fortolker konteksten i e-mailen og videresender rejseklager til kundeservice.                                                                                                                                    |
| **Model-baserede refleksagenter** | Udfører handlinger baseret på en model af verdenen og ændringer af den model.                                                          | Rejseagenten prioriterer ruter med væsentlige prisændringer baseret på adgang til historiske prisdata.                                                                                                                     |
| **Målbaserede agenter**       | Opretter planer for at nå specifikke mål ved at fortolke målet og bestemme handlinger for at nå det.                                  | Rejseagenten booker en rejse ved at bestemme nødvendige rejsearrangementer (bil, offentlig transport, fly) fra den aktuelle placering til destinationen.                                                                     |
| **Nyttebaserede agenter**     | Tager hensyn til præferencer og vægter kompromiser numerisk for at bestemme, hvordan mål kan opnås.                                   | Rejseagenten maksimerer nytten ved at afveje bekvemmelighed mod pris ved booking af rejser.                                                                                                                                   |
| **Lærende agenter**           | Forbedrer sig over tid ved at reagere på feedback og justere handlinger i overensstemmelse hermed.                                     | Rejseagenten forbedrer sig ved at bruge kundefeedback fra spørgeskemaer efter rejsen til at foretage justeringer af fremtidige bookinger.                                                                                   |
| **Hierarkiske agenter**       | Indeholder flere agenter i et lagdelt system, hvor højere-niveau agenter opdeler opgaver i underopgaver, som lavere-niveau agenter udfører. | Rejseagenten annullerer en rejse ved at opdele opgaven i underopgaver (for eksempel annullering af specifikke reservationer) og få lavere-niveau agenter til at fuldføre dem og rapportere tilbage til den højere-niveau agent. |
| **Multi-agent systemer (MAS)** | Agenter udfører opgaver uafhængigt, enten samarbejdende eller konkurrerende.                                                          | Samarbejdende: Flere agenter booker specifikke rejsetjenester såsom hoteller, fly og underholdning. Konkurrerende: Flere agenter administrerer og konkurrerer om en delt hotelbookingskalender for at booke kunder ind på hotellet. |

## Hvornår skal man bruge AI-agenter

I det tidligere afsnit brugte vi rejseagent-anvendelsestilfældet til at forklare, hvordan de forskellige typer agenter kan bruges i forskellige scenarier inden for rejsebooking. Vi vil fortsætte med at bruge denne applikation gennem hele kurset.

Lad os se på de typer anvendelsestilfælde, som AI-agenter er bedst anvendt til:

![Hvornår skal man bruge AI-agenter?](../../../translated_images/da/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Åbne problemer** - give LLM mulighed for at bestemme de nødvendige trin for at løse en opgave, fordi det ikke altid kan blive hårdkodet i en arbejdsgang.
- **Flertrinsprocesser** - opgaver, der kræver et kompleksitetsniveau, hvor AI-agenten skal bruge værktøjer eller information over flere omgange i stedet for enkeltforespørgsler.  
- **Forbedring over tid** - opgaver, hvor agenten kan forbedre sig over tid ved at modtage feedback fra enten sit miljø eller brugere for at levere bedre nytte.

Vi behandler flere overvejelser ved brug af AI-agenter i lektionen om opbygning af pålidelige AI-agenter.

## Grundlæggende om agentiske løsninger

### Agentudvikling

Det første skridt i at designe et AI-agent-system er at definere værktøjerne, handlingerne og adfærd. I dette kursus fokuserer vi på at bruge **Azure AI Agent Service** til at definere vores agenter. Den tilbyder funktioner som:

- Valg af åbne modeller såsom OpenAI, Mistral og Llama
- Brug af licenserede data gennem leverandører såsom Tripadvisor
- Brug af standardiserede OpenAPI 3.0-værktøjer

### Agentiske mønstre

Kommunikation med LLMs foregår gennem prompts. Givet den semi-autonome natur af AI-agenter er det ikke altid muligt eller nødvendigt at manuelt gen-prompt LLM efter en ændring i miljøet. Vi bruger **agentiske mønstre**, der tillader os at prompt'e LLM over flere trin på en mere skalerbar måde.

Dette kursus er opdelt i nogle af de aktuelt populære agentiske mønstre.

### Agentiske frameworks

Agentiske frameworks tillader udviklere at implementere agentiske mønstre gennem kode. Disse frameworks tilbyder skabeloner, plugins og værktøjer til bedre samarbejde mellem AI-agenter. Disse fordele giver muligheder for bedre observerbarhed og fejlfinding af AI-agent-systemer.

I dette kursus vil vi udforske det forskningsdrevne AutoGen-framework og det produktionsklare Agent-framework fra Semantic Kernel.

## Eksempelkoder

- Python: [Agent-ramme](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent-ramme](./code_samples/01-dotnet-agent-framework.md)

## Har du flere spørgsmål om AI-agenter?

Deltag i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for at møde andre kursister, deltage i kontortimer og få besvaret dine spørgsmål om AI-agenter.

## Forrige lektion

[Kursusopsætning](../00-course-setup/README.md)

## Næste lektion

[Udforskning af agentiske frameworks](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfraskrivelse:
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, bedes du være opmærksom på, at automatiske oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på originalsproget bør betragtes som den autoritative kilde. For kritisk information anbefales en professionel menneskelig oversættelse. Vi påtager os intet ansvar for misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->