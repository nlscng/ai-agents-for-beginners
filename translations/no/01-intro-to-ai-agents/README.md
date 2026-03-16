[![Intro to AI Agents](../../../translated_images/no/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Klikk på bildet over for å se video av denne leksjonen)_


# Introduksjon til AI-agenter og agentbrukstilfeller

Velkommen til kurset "AI-agenter for nybegynnere"! Dette kurset gir grunnleggende kunnskap og praktiske eksempler for å bygge AI-agenter.

Bli med i <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord-fellesskapet</a> for å treffe andre som lærer og bygger AI-agenter, og still spørsmål du måtte ha om dette kurset.

For å starte dette kurset begynner vi med å få en bedre forståelse av hva AI-agenter er og hvordan vi kan bruke dem i applikasjonene og arbeidsflytene vi bygger.

## Introduksjon

Denne leksjonen dekker:

- Hva er AI-agenter og hvilke forskjellige typer agenter finnes?
- Hvilke brukstilfeller passer best for AI-agenter, og hvordan kan de hjelpe oss?
- Hva er noen av de grunnleggende byggeklossene når man designer agentbaserte løsninger?

## Læringsmål
Etter å ha fullført denne leksjonen, skal du kunne:

- Forstå konseptene rundt AI-agenter og hvordan de skiller seg fra andre AI-løsninger.
- Bruke AI-agenter mest effektivt.
- Designe agentbaserte løsninger produktivt for både brukere og kunder.

## Definere AI-agenter og typer AI-agenter

### Hva er AI-agenter?

AI-agenter er **systemer** som gjør det mulig for **Store språkmodeller (LLMs)** å **utføre handlinger** ved å utvide deres evner ved å gi LLM-er **tilgang til verktøy** og **kunnskap**.

La oss dele denne definisjonen opp i mindre deler:

- **System** - Det er viktig å tenke på agenter ikke bare som en enkelt komponent, men som et system av mange komponenter. På grunnleggende nivå består en AI-agent av:
  - **Miljø** - Det definerte området hvor AI-agenten opererer. For eksempel, hvis vi hadde en reisebestillingsagent, kunne miljøet være reisebestillingssystemet som AI-agenten bruker for å fullføre oppgaver.
  - **Sensorer** - Miljøet har informasjon og gir tilbakemelding. AI-agenter bruker sensorer for å samle inn og tolke denne informasjonen om gjeldende tilstand i miljøet. I eksemplet med reisebestillingsagenten kan reisebestillingssystemet gi informasjon som hotelltilgjengelighet eller flypriser.
  - **Aktuatorer** - Når AI-agenten mottar gjeldende tilstand i miljøet, bestemmer agenten hva slags handling som skal utføres for å endre miljøet for oppgaven som utføres. For reisebestillingsagenten kan det være å booke et tilgjengelig rom for brukeren.

![What Are AI Agents?](../../../translated_images/no/what-are-ai-agents.1ec8c4d548af601a.webp)

**Store språkmodeller** - Konseptet med agenter eksisterte før skapelsen av LLM-er. Fordelen med å bygge AI-agenter med LLM-er er deres evne til å tolke menneskespråk og data. Denne evnen gjør at LLM-er kan tolke informasjon fra miljøet og definere en plan for å endre miljøet.

**Utføre handlinger** - Utenfor AI-agent systemer er LLM-er begrenset til situasjoner der handlingen er å generere innhold eller informasjon basert på en brukers prompt. Innenfor AI-agent systemer kan LLM-er utføre oppgaver ved å tolke brukerens forespørsel og bruke verktøy som er tilgjengelige i deres miljø.

**Tilgang til verktøy** - Hvilke verktøy LLM har tilgang til bestemmes av 1) miljøet det opererer i, og 2) utvikleren av AI-agenten. For vårt eksempel med reiseagenten er agentens verktøy begrenset til operasjonene som er tilgjengelige i bestillingssystemet, og/eller utvikleren kan begrense agentens tilgang til verktøy til flyreiser.

**Minne+Kunnskap** - Minne kan være korttidsminne i samtalekonteksten mellom bruker og agent. Langtidsminne, utenfor informasjonen gitt av miljøet, kan AI-agenter også hente kunnskap fra andre systemer, tjenester, verktøy og til og med andre agenter. I reiseagenteksemplet kan denne kunnskapen være informasjon om brukerens reisepreferanser lagret i en kundedatabase.

### De forskjellige typene agenter

Nå som vi har en generell definisjon av AI-agenter, la oss se på noen spesifikke agenttyper og hvordan de kan anvendes for en reisebestillings-AI-agent.

| **Agenttype**                 | **Beskrivelse**                                                                                                                       | **Eksempel**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Enkle refleksagenter**      | Utfører umiddelbare handlinger basert på forhåndsdefinerte regler.                                                                   | Reiseagent tolker innholdet i en e-post og videresender reiseklager til kundeservice.                                                                                                                         |
| **Modellbaserte refleksagenter** | Utfører handlinger basert på en modell av verden og endringer i denne modellen.                                                        | Reiseagent prioriterer ruter med betydelige prisendringer basert på tilgang til historiske prisdata.                                                                                                             |
| **Målbaserte agenter**        | Lager planer for å oppnå spesifikke mål ved å tolke målet og bestemme handlinger for å nå det.                                        | Reiseagent booker en reise ved å bestemme nødvendige reiseopplegg (bil, kollektivtransport, fly) fra nåværende sted til destinasjonen.                                                                                |
| **Nyttebaserte agenter**      | Tar hensyn til preferanser og veier opp avveininger numerisk for å bestemme hvordan mål oppnås.                                       | Reiseagent maksimerer nytte ved å veie bekvemmelighet opp mot kostnad når reisen bookes.                                                                                                                                          |
| **Lærende agenter**           | Forbedres over tid ved å respondere på tilbakemeldinger og justere handlinger deretter.                                              | Reiseagent forbedres ved å bruke kundetilbakemeldinger fra spørreundersøkelser etter tur for å gjøre justeringer i fremtidige bestillinger.                                                                                                               |
| **Hierarkiske agenter**       | Har flere agenter i et lagdelt system, hvor agenter på høyere nivå deler oppgaver inn i deloppgaver som agenter på lavere nivå skal fullføre. | Reiseagent kansellerer en tur ved å dele oppgaven i deloppgaver (for eksempel å kansellere spesifikke bestillinger) og la agenter på lavere nivå fullføre disse, og rapportere tilbake til agenten på høyere nivå.                                     |
| **Multi-agent systemer (MAS)** | Agenter utfører oppgaver uavhengig, enten samarbeidsvillig eller konkurransedyktig.                                                    | Samarbeidsvillig: Flere agenter booker spesifikke reisetjenester som hoteller, fly og underholdning. Konkurrerende: Flere agenter styrer og konkurrerer om en delt hotellbookingskalender for å booke kunder inn på hotellet. |

## Når skal man bruke AI-agenter

I tidligere seksjon brukte vi reiseagent-brukstilfellet for å forklare hvordan de forskjellige agenttypene kan brukes i ulike scenarioer for reisebestilling. Vi vil fortsette å bruke denne applikasjonen gjennom kurset.

La oss se på hvilke typer brukstilfeller AI-agenter er best egnet for:

![When to use AI Agents?](../../../translated_images/no/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Åpne problemer** - lar LLM bestemme nødvendige trinn for å fullføre en oppgave fordi det ikke alltid kan kodes hardt inn i en arbeidsflyt.
- **Flertrinnsprosesser** - oppgaver som krever et kompleksitetsnivå der AI-agenten må bruke verktøy eller informasjon over flere runder i stedet for å hente alt i ett skudd.  
- **Forbedring over tid** - oppgaver der agenten kan forbedres over tid ved å motta tilbakemeldinger fra enten miljøet eller brukere for å gi bedre nytte.

Vi dekker flere hensyn ved bruk av AI-agenter i leksjonen Bygge pålitelige AI-agenter.

## Grunnleggende om agentbaserte løsninger

### Agentutvikling

Det første steget i å designe et AI-agentsystem er å definere verktøy, handlinger og oppførsel. I dette kurset fokuserer vi på å bruke **Azure AI Agent Service** for å definere agentene våre. Den tilbyr funksjoner som:

- Valg av åpne modeller som OpenAI, Mistral og Llama
- Bruk av lisensiert data gjennom leverandører som Tripadvisor
- Bruk av standardiserte OpenAPI 3.0-verktøy

### Agentmønstre

Kommunikasjon med LLM-er skjer gjennom prompts. Gitt den semi-autonome naturen til AI-agenter, er det ikke alltid mulig eller nødvendig å manuelt prompt’e LLM på nytt etter en endring i miljøet. Vi bruker **agentmønstre** som gjør at vi kan prompt’e LLM over flere trinn på en mer skalerbar måte.

Dette kurset er delt inn i noen av de nåværende populære agentmønstrene.

### Agentrammeverk

Agentrammeverk gir utviklere mulighet til å implementere agentmønstre gjennom kode. Disse rammeverkene tilbyr maler, plugins og verktøy for bedre samarbeid mellom AI-agenter. Disse fordelene gir bedre muligheter for observasjon og feilsøking av AI-agent systemer.

I dette kurset vil vi utforske det forskningsbaserte AutoGen-rammeverket og det produksjonsklare Agent-rammeverket fra Semantic Kernel.

## Eksempelkoder

- Python: [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## Har du flere spørsmål om AI-agenter?

Bli med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for å møte andre som lærer, delta på kontortimer og få svar på dine spørsmål om AI-agenter.

## Forrige leksjon

[Course Setup](../00-course-setup/README.md)

## Neste leksjon

[Utforske agentrammeverk](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Det opprinnelige dokumentet på originalspråket skal anses som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->