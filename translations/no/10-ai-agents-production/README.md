# AI-agenter i produksjon: Observabilitet og evaluering

[![AI Agents in Production](../../../translated_images/no/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

Etter hvert som AI-agenter beveger seg fra eksperimentelle prototyper til virkelige applikasjoner, blir evnen til å forstå deres oppførsel, overvåke ytelsen og systematisk evaluere resultatene deres viktig.

## Læringsmål

Etter å ha fullført denne leksjonen vil du vite hvordan du kan/forstå:
- Kjernemekanismer for agentobservabilitet og evaluering
- Teknikker for å forbedre ytelse, kostnader og effektivitet for agenter
- Hva og hvordan du systematisk evaluerer AI-agentene dine
- Hvordan du kontrollerer kostnader når du distribuerer AI-agenter i produksjon
- Hvordan du instrumenterer agenter bygd med AutoGen

Målet er å gi deg kunnskapen til å forvandle dine "svarte bokser" til gjennomsiktige, håndterbare og pålitelige systemer.

_**Merk:** Det er viktig å distribuere AI-agenter som er trygge og pålitelige. Sjekk også ut leksjonen [Building Trustworthy AI Agents](./06-building-trustworthy-agents/README.md)._

## Traces og Spans

Observabilitetsverktøy som [Langfuse](https://langfuse.com/) eller [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) representerer vanligvis agentkjøringer som traces og spans.

- **Trace** representerer en komplett agentoppgave fra start til slutt (for eksempel håndtering av en brukerhenvendelse).
- **Spans** er individuelle steg innen trace (for eksempel et språkmodellkall eller datainnhenting).

![Trace tree in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Uten observabilitet kan en AI-agent føles som en "svart boks" – dens interne tilstand og resonnement er ugjennomsiktig, noe som gjør det vanskelig å feilsøke problemer eller optimalisere ytelsen. Med observabilitet blir agenter "glassbokser" som tilbyr gjennomsiktighet, noe som er avgjørende for å bygge tillit og sikre at de fungerer som forventet.

## Hvorfor observabilitet er viktig i produksjonsmiljøer

Overgangen til produksjon av AI-agenter introduserer nye utfordringer og krav. Observabilitet er ikke lenger en "hyggelig å ha"-funksjon, men en kritisk kapasitet:

*   **Feilsøking og rotårsaksanalyse**: Når en agent feiler eller gir uventet resultat, gir observabilitetsverktøyene traces som trengs for å spore opp feilkilden. Dette er spesielt viktig i komplekse agenter som kan innebære flere LLM-kall, verktøysinteraksjoner og betinget logikk.
*   **Latens- og kostnadshåndtering**: AI-agenter baserer seg ofte på LLM-er og andre eksterne API-er som faktureres per token eller kall. Observabilitet tillater nøyaktig sporing av disse kallene, slik at man kan identifisere operasjoner som er unødvendig treg eller kostbar. Dette gjør det mulig å optimalisere prompts, velge mer effektive modeller eller redesigne arbeidsflyter for å styre driftskostnader og sikre god brukeropplevelse.
*   **Tillit, sikkerhet og samsvar**: I mange applikasjoner er det viktig å sikre at agenter oppfører seg trygt og etisk. Observabilitet gir en revisjonsspor av agenthandlinger og beslutninger. Dette kan brukes til å oppdage og sette inn tiltak mot problemer som prompt-injeksjon, generering av skadelig innhold, eller feilbehandling av personlig identifiserbar informasjon (PII). For eksempel kan du gjennomgå traces for å forstå hvorfor en agent ga et bestemt svar eller brukte et bestemt verktøy.
*   **Kontinuerlige forbedringssykluser**: Observabilitetsdata er grunnlaget for en iterativ utviklingsprosess. Ved å overvåke hvordan agenter fungerer i den virkelige verden, kan team identifisere forbedringsområder, samle data for finjustering av modeller og validere effekten av endringer. Dette skaper en tilbakemeldingssløyfe hvor produksjonsinnsikter fra online evaluering informerer offline eksperimentering og forbedring, noe som fører til stadig bedre agentytelse.

## Viktige mål for sporing

For å overvåke og forstå agentoppførsel bør en rekke metrikker og signaler spores. Mens spesifikke metrikker kan variere basert på agentens formål, er noen universelt viktige.

Her er noen av de vanligste metrikker som observabilitetsverktøy overvåker:

**Latens:** Hvor raskt svarer agenten? Lange ventetider påvirker brukeropplevelsen negativt. Du bør måle latens for oppgaver og individuelle steg ved å spore agentkjøringer. For eksempel kan en agent som tar 20 sekunder for alle modellkall akselereres ved å bruke en raskere modell eller ved å kjøre modellkall parallelt.

**Kostnader:** Hva koster hver agentkjøring? AI-agenter baserer seg på LLM-kall fakturert per token eller eksterne API-er. Hyppig bruk av verktøy eller flere prompts kan raskt gi økte kostnader. For eksempel, hvis en agent kaller en LLM fem ganger for marginal kvalitetsforbedring, må du vurdere om kostnaden er berettiget eller om du kan redusere antall kall eller bruke en billigere modell. Sanntidsovervåking hjelper også med å oppdage uventede kostnadstopper (f.eks. feil som forårsaker overdrevne API-løkker).

**Feil i forespørsler:** Hvor mange forespørsler feilet agenten på? Dette kan inkludere API-feil eller mislykkede verktøyskall. For å gjøre agenten mer robust i produksjon kan du sette opp fallback-mekanismer eller automatiske retryer. For eksempel, hvis LLM-leverandør A er nede, bytter du til LLM-leverandør B som backup.

**Brukertilbakemeldinger:** Gjennomføring av direkte brukerevalueringer gir verdifulle innsikter. Dette kan inkludere eksplisitte vurderinger (👍tommel opp/👎tommel ned, ⭐1-5 stjerner) eller tekstlige kommentarer. Konsistent negativ tilbakemelding bør varsle deg, da det er et tegn på at agenten ikke fungerer som forventet.

**Implicit brukertilbakemelding:** Brukeratferd gir indirekte tilbakemeldinger uten eksplisitte vurderinger. Dette kan inkludere umiddelbar omformulering av spørsmål, gjentatte forespørsler eller klikk på en retry-knapp. For eksempel, hvis du ser at brukere gjentatte ganger spør samme spørsmål, er dette et tegn på at agenten ikke fungerer som forventet.

**Nøyaktighet:** Hvor ofte produserer agenten korrekte eller ønskede resultater? Definisjoner av nøyaktighet varierer (f.eks. korrekt problemløsning, nøyaktighet i informasjonssøk, brukertilfredshet). Det første steget er å definere hva suksess betyr for din agent. Du kan spore nøyaktighet gjennom automatiske kontroller, evalueringsscore eller merke oppgavefullføringer. For eksempel ved å merke traces som "lyktes" eller "feilet".

**Automatiserte evalueringsmetrikker:** Du kan også sette opp automatiserte evalueringer. For eksempel kan du bruke en LLM til å score agentens output, f.eks. om den er hjelpsom, nøyaktig eller ikke. Det finnes også flere open source-biblioteker som hjelper deg med å score ulike aspekter ved agenten, f.eks. [RAGAS](https://docs.ragas.io/) for RAG-agenter eller [LLM Guard](https://llm-guard.com/) for å oppdage skadelig språk eller prompt-injeksjon.

I praksis gir en kombinasjon av disse metrikker best dekning av en AI-agents helse. I dette kapitlets [eksempelnotatbok](./code_samples/10_autogen_evaluation.ipynb) vil vi vise hvordan disse metrikker ser ut i virkelige eksempler, men først lærer vi hvordan en typisk evalueringsarbeidsflyt ser ut.

## Instrumenter agenten din

For å samle inn tracing-data må du instrumentere koden din. Målet er å instrumentere agentkoden slik at den sender ut traces og metrikker som kan fanges opp, behandles og visualiseres av en observabilitetsplattform.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) har blitt en industristandard for LLM-observabilitet. Det gir sett med API-er, SDK-er og verktøy for å generere, samle og eksportere telemetridata.

Det finnes mange instrumenteringsbiblioteker som pakker inn eksisterende agentrammeverk og gjør det enkelt å eksportere OpenTelemetry-spans til et observabilitetsverktøy. Nedenfor er et eksempel på instrumentering av en AutoGen-agent med [OpenLit-instrumenteringsbiblioteket](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```


[Eksempelnotatboken](./code_samples/10_autogen_evaluation.ipynb) i dette kapitlet vil demonstrere hvordan du instrumenterer AutoGen-agenten din.

**Manuell opprettelse av Span:** Selv om instrumenteringsbiblioteker gir et godt utgangspunkt, er det ofte behov for mer detaljert eller tilpasset informasjon. Du kan opprette spans manuelt for å legge til skreddersydd applikasjonslogikk. Enda viktigere, de kan berikes med egendefinerte attributter (også kalt tags eller metadata). Disse attributtene kan inkludere forretningsspesifikke data, mellomregninger eller annen kontekst som kan være nyttig for feilsøking eller analyse, som for eksempel `user_id`, `session_id` eller `model_version`.

Eksempel på manuell opprettelse av traces og spans med [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3): 

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```


## Agent-evaluering

Observabilitet gir oss metrikker, men evaluering er prosessen med å analysere disse dataene (og utføre tester) for å avgjøre hvor godt en AI-agent presterer og hvordan den kan forbedres. Med andre ord, når du har de traces og metrikker, hvordan bruker du dem til å vurdere agenten og ta beslutninger?

Regelmessig evaluering er viktig fordi AI-agenter ofte er ikke-deterministiske og kan utvikle seg (gjennom oppdateringer eller endringer i modellens oppførsel) – uten evaluering ville du ikke vite om din "smarte agent" faktisk gjør jobben sin bra eller om den har fått tilbakegang.

Det finnes to kategorier av evaluering for AI-agenter: **online evaluering** og **offline evaluering**. Begge er verdifulle og utfyller hverandre. Vi starter vanligvis med offline evaluering, da dette er det minste nødvendige steget før distribusjon av en agent.

### Offline evaluering

![Dataset items in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

Dette innebærer evaluering av agenten i et kontrollert miljø, vanligvis ved å bruke testdatasett, ikke direkte brukerhenvendelser i sanntid. Du bruker kuraterte datasett hvor du vet hva den forventede outputen eller korrekte oppførselen er, og kjører agenten på disse.

For eksempel, hvis du laget en agent for tekstbaserte matteoppgaver, kan du ha et [testdatasett](https://huggingface.co/datasets/gsm8k) med 100 problemer med kjente svar. Offline evaluering utføres ofte under utvikling (og kan inngå i CI/CD-pipelines) for å sjekke forbedringer eller hindre regresjoner. Fordelen er at det er **repetitivt og gir klare nøyaktighetsmetrikker siden du har sannheten som grunnlag**. Du kan også simulere brukerhenvendelser og måle agentens svar mot ideelle svar eller bruke automatiske metrikker som beskrevet ovenfor.

Den viktigste utfordringen med offline evaluering er å sikre at testdatasettet er omfattende og fortsatt relevant – agenten kan prestere godt på et fast testsett, men møte svært ulike spørsmål i produksjon. Derfor bør du holde testsett oppdatert med nye tilfeller og eksempler som gjenspeiler virkelige scenarioer. En blanding av små "smøretstester" og større evalueringssett er nyttig: små sett for raske kontroller og større for bredere ytelsesmålinger.

### Online evaluering

![Observability metrics overview](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Dette refererer til evaluering av agenten i et levende, ekte miljø, altså under faktisk bruk i produksjon. Online evaluering inkluderer overvåking av agentens ytelse på ekte brukerinteraksjoner og kontinuerlig analyse av resultater.

For eksempel kan du spore suksessrater, brukertilfredshetspoeng eller andre metrikker på sanntidstrafikk. Fordelen med online evaluering er at den **fanger opp ting du kanskje ikke forutser i et laboratoriemiljø** – du kan observere modellendringer over tid (hvis agentens effektivitet forringes når inputmønstre skifter) og fange opp uventede spørsmål eller situasjoner som ikke var i testdataene dine. Den gir et ekte bilde av hvordan agenten oppfører seg ute i feltet.

Online evaluering innebærer ofte innsamling av implisitte og eksplisitte brukertilbakemeldinger, som nevnt, og muligens kjøring av shadow-tester eller A/B-tester (der en ny versjon kjører parallelt for å sammenligne med den gamle). Utfordringen er at det kan være vanskelig å få pålitelige etiketter eller poeng på live-interaksjoner – du kan være avhengig av brukertilbakemeldinger eller downstream-metrikker (som om brukeren klikket på resultatet).

### Kombinere de to

Online og offline evalueringer er ikke gjensidig utelukkende; de utfyller hverandre godt. Innsikter fra online overvåking (f.eks. nye typer brukerhenvendelser der agenten presterer dårlig) kan brukes til å forbedre offline testdatasett. Omvendt kan agenter som presterer godt på offline-tester også trygt distribueres og overvåkes online.

Mange team følger en syklus:

_evaluer offline -> deployer -> overvåk online -> samle nye feiltilfeller -> legg til i offline datasett -> forbedre agent -> gjenta_.

## Vanlige problemer

Når du distribuerer AI-agenter i produksjon, kan du møte ulike utfordringer. Her er noen vanlige problemer og mulige løsninger:

| **Problem**    | **Potensiell løsning**   |
| ------------- | ------------------ |
| AI-agent utfører ikke oppgaver konsekvent | - Forbedre prompten som gis til AI-agenten; vær tydelig på mål.<br>- Identifiser om oppdeling av oppgavene i deloppgaver som håndteres av flere agenter kan hjelpe. |
| AI-agent sitter fast i uendelige løkker | - Sikre klare avslutningsvilkår slik at agenten vet når prosessen skal stoppe.<br>- For komplekse oppgaver som krever resonnement og planlegging, bruk en større modell spesialisert for slike oppgaver. |
| AI-agentens verktøyskall fungerer dårlig | - Test og valider verktøyets output utenfor agentsystemet.<br>- Forbedre definerte parametere, prompts og navngivning av verktøy. |
| Multi-agent system utfører ikke konsekvent | - Forbedre prompts til hver agent for å sikre at de er spesifikke og forskjellige fra hverandre.<br>- Bygg et hierarkisk system med en "ruting"- eller kontrolleragent som bestemmer hvilken agent som er riktig. |

Mange av disse problemene kan identifiseres mer effektivt med observabilitet på plass. De traces og metrikker vi diskuterte tidligere hjelper deg nøyaktig å finne hvor i agentens arbeidsflyt problemene oppstår, noe som gjør feilsøking og optimalisering mye mer effektivt.

## Kostnadshåndtering
Her er noen strategier for å håndtere kostnadene ved å sette AI-agenter i produksjon:

**Bruke mindre modeller:** Små språkmodeller (SLM) kan fungere godt på visse agent-brukstilfeller og vil redusere kostnadene betydelig. Som nevnt tidligere er det beste måten å forstå hvor godt en SLM vil prestere på ditt brukstilfelle å bygge et evalueringssystem for å bestemme og sammenligne ytelse mot større modeller. Vurder å bruke SLM-er for enklere oppgaver som intensjonsklassifisering eller parameterekstraksjon, mens du reserverer større modeller til kompleks resonnement.

**Bruke en ruter-modell:** En lignende strategi er å bruke en variasjon av modeller og størrelser. Du kan bruke en LLM/SLM eller serverløs funksjon til å rute forespørsler basert på kompleksitet til de modellene som passer best. Dette vil også bidra til å redusere kostnadene samtidig som det sikrer ytelse på riktige oppgaver. For eksempel, rute enkle forespørsler til mindre, raskere modeller, og bare bruke dyre store modeller for komplekse resonnementsoppgaver.

**Caching av svar:** Å identifisere vanlige forespørsler og oppgaver og levere svarene før de går gjennom ditt agentiske system er en god måte å redusere volumet av like forespørsler på. Du kan til og med implementere en flyt for å identifisere hvor lik en forespørsel er til dine bufrede forespørsler ved hjelp av mer grunnleggende AI-modeller. Denne strategien kan betydelig redusere kostnadene for ofte stilte spørsmål eller vanlige arbeidsflyter.

## La oss se hvordan dette fungerer i praksis

I [eksempelskriptet til denne seksjonen](./code_samples/10_autogen_evaluation.ipynb) vil vi se eksempler på hvordan vi kan bruke observasjonsverktøy for å overvåke og evaluere agenten vår.

### Har du flere spørsmål om AI-agenter i produksjon?

Bli med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for å møte andre lærende, delta på kontortid og få svar på dine spørsmål om AI-agenter.

## Forrige leksjon

[Metakognitivt designmønster](../09-metacognition/README.md)

## Neste leksjon

[Agentiske protokoller](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi jobber for å oppnå nøyaktighet, vennligst vær oppmerksom på at automatiserte oversettelser kan inneholde feil eller unøyaktigheter. Det opprinnelige dokumentet på originalspråket skal anses som den autoritative kilden. For kritisk informasjon anbefales det å bruke profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for misforståelser eller feiltolkninger som oppstår som følge av bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->