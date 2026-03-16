# AI-agenter i produktion: Observabilitet & utvärdering

[![AI Agents in Production](../../../translated_images/sv/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

När AI-agenter går från experimentella prototyper till verkliga tillämpningar blir förmågan att förstå deras beteende, övervaka deras prestanda och systematiskt utvärdera deras utdata viktig.

## Lärandemål

Efter att ha slutfört den här lektionen kommer du att veta hur du/förstå:
- Kärnkoncept för agentobservabilitet och utvärdering
- Tekniker för att förbättra agenters prestanda, kostnader och effektivitet
- Vad och hur du systematiskt utvärderar dina AI-agenter
- Hur du kontrollerar kostnader vid driftsättning av AI-agenter i produktion
- Hur du instrumenterar agenter byggda med AutoGen

Målet är att ge dig kunskapen för att omvandla dina "svarta låda"-agenter till transparenta, hanterbara och pålitliga system.

_**Obs:** Det är viktigt att driftsätta AI-agenter som är säkra och pålitliga. Kolla också in lektionen [Bygga pålitliga AI-agenter](./06-building-trustworthy-agents/README.md)._

## Spår och spans

Observabilitetsverktyg som [Langfuse](https://langfuse.com/) eller [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) representerar vanligtvis agentkörningar som spår (traces) och spans.

- **Trace** representerar en komplett agentuppgift från start till slut (som att hantera en användarfråga).
- **Spans** är individuella steg inom spåret (som att anropa en språkmodell eller hämta data).

![Trace tree in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Utan observabilitet kan en AI-agent kännas som en "svart låda" - dess interna tillstånd och resonemang är ogenomskinliga, vilket gör det svårt att diagnostisera problem eller optimera prestanda. Med observabilitet blir agenter "glaslådor", vilket ger den transparens som är avgörande för att bygga förtroende och säkerställa att de fungerar som avsett. 

## Varför observabilitet är viktigt i produktionsmiljöer

Att överföra AI-agenter till produktionsmiljöer introducerar en ny uppsättning utmaningar och krav. Observabilitet är inte längre en "trevlig-att-ha"-funktion utan en kritisk kapabilitet:

*   **Felsökning och rotorsaksanalys**: När en agent misslyckas eller producerar ett oväntat resultat ger observabilitetsverktyg de spår som behövs för att lokalisera felkällan. Detta är särskilt viktigt i komplexa agenter som kan involvera flera LLM-anrop, verktygsinteraktioner och villkorlig logik.
*   **Latens- och kostnadshantering**: AI-agenter förlitar sig ofta på LLM:er och andra externa API:er som debiteras per token eller per anrop. Observabilitet möjliggör exakt spårning av dessa anrop, vilket hjälper till att identifiera operationer som är överdrivet långsamma eller dyra. Detta gör att team kan optimera prompts, välja mer effektiva modeller eller omforma arbetsflöden för att hantera driftkostnader och säkerställa en bra användarupplevelse.
*   **Förtroende, säkerhet och efterlevnad**: I många tillämpningar är det viktigt att säkerställa att agenter uppträder säkert och etiskt. Observabilitet ger en revisionskedja av agentens handlingar och beslut. Detta kan användas för att upptäcka och mildra problem som promptinjektion, generering av skadligt innehåll eller felhantering av personligt identifierbar information (PII). Till exempel kan du granska spår för att förstå varför en agent gav ett visst svar eller använde ett specifikt verktyg.
*   **Kontinuerliga förbättringsloopar**: Observabilitetsdata är grunden för en iterativ utvecklingsprocess. Genom att övervaka hur agenter presterar i verkligheten kan team identifiera förbättringsområden, samla data för finjustering av modeller och validera effekten av ändringar. Detta skapar en återkopplingsslinga där produktionsinsikter från onlineutvärdering informerar offline-experiment och förfining, vilket leder till successivt bättre agentprestanda.

## Viktiga mått att följa

För att övervaka och förstå agentbeteende bör en rad mått och signaler spåras. Medan de specifika måtten kan variera beroende på agentens syfte, är vissa universellt viktiga.

Här är några av de vanligaste måtten som observabilitetsverktyg övervakar:

**Latens:** Hur snabbt svarar agenten? Långa väntetider påverkar användarupplevelsen negativt. Du bör mäta latens för uppgifter och individuella steg genom att spåra agentkörningar. Till exempel kan en agent som tar 20 sekunder för alla modellanrop accelereras genom att använda en snabbare modell eller genom att köra modellanrop parallellt.

**Kostnader:** Vad kostar en agentkörning? AI-agenter förlitar sig på LLM-anrop som debiteras per token eller externa API:er. Frekvent verktygsanvändning eller flera prompts kan snabbt öka kostnaderna. Till exempel, om en agent anropar en LLM fem gånger för marginell kvalitetsförbättring måste du bedöma om kostnaden är motiverad eller om du kan minska antalet anrop eller använda en billigare modell. Realtidsövervakning kan också hjälpa till att identifiera oväntade toppar (t.ex. buggar som orsakar överdrivna API-loopar).

**Felkoder i förfrågningar:** Hur många förfrågningar misslyckades agenten med? Detta kan inkludera API-fel eller misslyckade verktygsanrop. För att göra din agent mer robust mot dessa i produktion kan du sedan ställa in fallback-mekanismer eller retries. T.ex. om LLM-leverantör A ligger nere, byter du till LLM-leverantör B som backup.

**Användarfeedback:** Implementering av direkt användarutvärdering ger värdefulla insikter. Detta kan inkludera explicita betyg (👍thumbs-up/👎down, ⭐1-5 stjärnor) eller textkommentarer. Konsekvent negativ feedback bör varna dig eftersom det är ett tecken på att agenten inte fungerar som förväntat. 

**Implicit användarfeedback:** Användarbeteenden ger indirekt feedback även utan explicita betyg. Detta kan inkludera omformulering av frågor direkt, upprepade förfrågningar eller att klicka på en försök-igen-knapp. T.ex. om du ser att användare upprepade gånger ställer samma fråga är det ett tecken på att agenten inte fungerar som förväntat.

**Noggrannhet:** Hur ofta producerar agenten korrekta eller önskvärda utdata? Definitioner av noggrannhet varierar (t.ex. problemlösningsriktighet, informationsåtervinningsnoggrannhet, användarnöjdhet). Det första steget är att definiera vad framgång betyder för din agent. Du kan spåra noggrannhet via automatiska kontroller, evalueringspoäng eller etiketter för slutförda uppgifter. Till exempel att markera spår som "succeeded" eller "failed". 

**Automatiserade utvärderingsmått:** Du kan också sätta upp automatiska utvärderingar. Till exempel kan du använda en LLM för att poängsätta agentens utdata, t.ex. om det är hjälpsamt, korrekt eller ej. Det finns också flera open source-bibliotek som hjälper dig att poängsätta olika aspekter av agenten. T.ex. [RAGAS](https://docs.ragas.io/) för RAG-agenter eller [LLM Guard](https://llm-guard.com/) för att upptäcka skadligt språk eller promptinjektion. 

I praktiken ger en kombination av dessa mått bästa täckning av en AI-agents hälsa. I detta kapitels [exempelanteckningsbok](./code_samples/10_autogen_evaluation.ipynb) visar vi hur dessa mått ser ut i verkliga exempel men först lär vi oss hur ett typiskt utvärderingsarbetsflöde ser ut.

## Instrumentera din agent

För att samla in spårningsdata behöver du instrumentera din kod. Målet är att instrumentera agentkoden för att emittera spår och mått som kan fångas, bearbetas och visualiseras av en observabilitetsplattform.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) har framkommit som en industristandard för LLM-observabilitet. Det tillhandahåller ett set med API:er, SDK:er och verktyg för att generera, samla in och exportera telemetridata. 

Det finns många instrumenteringsbibliotek som wrappar befintliga agentramverk och gör det enkelt att exportera OpenTelemetry-spans till ett observabilitetsverktyg. Nedan är ett exempel på hur man instrumenterar en AutoGen-agent med [OpenLit instrumenteringsbiblioteket](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

The [example notebook](./code_samples/10_autogen_evaluation.ipynb) in this chapter will demonstrate how to instrument your AutoGen agent.

**Manuell span-skapande:** Medan instrumenteringsbibliotek ger en bra bas finns det ofta fall där mer detaljerad eller anpassad information behövs. Du kan manuellt skapa spans för att lägga till anpassad applikationslogik. Viktigare är att de kan berika automatiskt eller manuellt skapade spans med anpassade attribut (även kända som tags eller metadata). Dessa attribut kan inkludera affärsspecifik data, mellanliggande beräkningar eller annan kontext som kan vara användbar för felsökning eller analys, såsom `user_id`, `session_id`, eller `model_version`.

Example on creating traces and spans manually with the [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3): 

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Agentutvärdering

Observabilitet ger oss mått, men utvärdering är processen att analysera dessa data (och utföra tester) för att avgöra hur väl en AI-agent presterar och hur den kan förbättras. Med andra ord, när du har de där spåren och måtten, hur använder du dem för att bedöma agenten och fatta beslut? 

Regelbunden utvärdering är viktigt eftersom AI-agenter ofta är icke-deterministiska och kan förändras (genom uppdateringar eller drift i modellbeteende) – utan utvärdering skulle du inte veta om din "smarta agent" faktiskt gör sitt jobb bra eller om den har regressat.

Det finns två kategorier av utvärderingar för AI-agenter: **online-utvärdering** och **offline-utvärdering**. Båda är värdefulla och kompletterar varandra. Vi börjar vanligtvis med offline-utvärdering, eftersom detta är det minsta nödvändiga steget innan man driftsätter en agent.

### Offline-utvärdering

![Dataset items in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

Detta innebär att utvärdera agenten i en kontrollerad miljö, vanligtvis med testdataset, inte live användarförfrågningar. Du använder kuraterade dataset där du vet vad den förväntade utgången eller korrekt beteende är, och kör sedan din agent på dessa. 

Till exempel, om du byggt en agent för matematiska textproblem kan du ha ett [testdataset](https://huggingface.co/datasets/gsm8k) på 100 problem med kända svar. Offline-utvärdering görs ofta under utveckling (och kan vara en del av CI/CD-pipelines) för att kontrollera förbättringar eller skydda mot regressioner. Fördelen är att det är **reproducerbart och du kan få tydliga noggrannhetsmått eftersom du har sanningen**. Du kan också simulera användarförfrågningar och mäta agentens svar mot ideala svar eller använda automatiska mått som beskrivits ovan. 

Den största utmaningen med offline-utvärdering är att säkerställa att ditt testdataset är omfattande och förblir relevant – agenten kan prestera väl på ett fast testset men möta mycket annorlunda frågor i produktion. Därför bör du hålla testseten uppdaterade med nya edge cases och exempel som speglar verkliga scenarier​. En mix av små "röktest"-fall och större utvärderingsset är användbar: små set för snabba kontroller och större för bredare prestandamått​.

### Online-utvärdering

![Observability metrics overview](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Detta hänvisar till att utvärdera agenten i en live, verklig miljö, dvs under faktisk användning i produktion. Online-utvärdering innebär att övervaka agentens prestanda på verkliga användarinteraktioner och kontinuerligt analysera resultat. 

Till exempel kan du spåra framgångsfrekvenser, användarnöjdhetspoäng eller andra mått på live-trafik. Fördelen med online-utvärdering är att det **fångar saker du kanske inte förutser i en laboratoriemiljö** – du kan observera modelldriftsförändring över tid (om agentens effektivitet försämras när inmatningsmönster skiftar) och fånga oväntade frågor eller situationer som inte fanns i ditt testdata​. Det ger en verklig bild av hur agenten uppträder i fält. 

Online-utvärdering involverar ofta insamling av implicit och explicit användarfeedback, som diskuterats, och eventuellt körning av skuggtester eller A/B-test (där en ny version av agenten körs parallellt för att jämföras med den gamla). Utmaningen är att det kan vara svårt att få tillförlitliga etiketter eller poäng för live-interaktioner – du kan behöva förlita dig på användarfeedback eller downstream-mått (som om användaren klickade på resultatet eller ej). 

### Att kombinera de två

Online- och offline-utvärderingar utesluter inte varandra; de är starkt komplementära. Insikter från online-övervakning (t.ex. nya typer av användarfrågor där agenten presterar dåligt) kan användas för att komplettera och förbättra offline-testdataset. Omvänt kan agenter som presterar väl i offline-tester sedan driftsättas mer förtroendefullt och övervakas online. 

Faktum är att många team antar en loop: 

_utvärdera offline -> distribuera -> övervaka online -> samla nya felfall -> lägg till i offline-datasetet -> förfina agenten -> upprepa_.

## Vanliga problem

När du driftsätter AI-agenter i produktion kan du stöta på olika utmaningar. Här är några vanliga problem och deras potentiella lösningar:

| **Problem**    | **Möjlig lösning**   |
| ------------- | ------------------ |
| AI Agent not performing tasks consistently | - Förfina prompten som ges till AI-agenten; var tydlig med målen.<br>- Identifiera var uppdelning av uppgifterna i deluppgifter och hantering av dessa av flera agenter kan hjälpa. |
| AI Agent running into continuous loops  | - Se till att du har tydliga stoppvillkor så att agenten vet när processen ska avbrytas.<br>- För komplexa uppgifter som kräver resonerande och planering, använd en större modell som är specialiserad för resoneringsuppgifter. |
| AI Agent tool calls are not performing well   | - Testa och validera verktygets output utanför agentsystemet.<br>- Förfina de definierade parametrarna, prompts och namngivningen av verktygen.  |
| Multi-Agent system not performing consistently | - Förfina prompts som ges till varje agent för att säkerställa att de är specifika och skilda från varandra.<br>- Bygg ett hierarkiskt system med en "routing" eller controller-agent för att avgöra vilken agent som är korrekt. |

Många av dessa problem kan identifieras mer effektivt med observabilitet på plats. De spår och mått vi diskuterade tidigare hjälper till att exakt lokalisera var i agentarbetsflödet problemen uppstår, vilket gör felsökning och optimering mycket mer effektivt.

## Hantera kostnader
Här är några strategier för att hantera kostnaderna för att driftsätta AI-agenter i produktion:

**Använda mindre modeller:** Små språkmodeller (SLMs) kan fungera bra i vissa agentlika användningsfall och kommer att minska kostnaderna avsevärt. Som nämnts tidigare är det bästa sättet att förstå hur bra en SLM kommer att prestera i ditt användningsfall att bygga ett utvärderingssystem för att bestämma och jämföra prestanda mot större modeller. Överväg att använda SLMs för enklare uppgifter som avsiktsklassificering eller parameterutvinning, samtidigt som du reserverar större modeller för komplexa resonemang.

**Använda en routermodell:** En liknande strategi är att använda en variation av modeller och storlekar. Du kan använda en LLM/SLM eller en serverlös funktion för att dirigera förfrågningar baserat på komplexitet till de modeller som passar bäst. Detta hjälper också till att minska kostnaderna samtidigt som det säkerställer prestanda för rätt uppgifter. Till exempel, dirigera enkla frågor till mindre, snabbare modeller, och använd endast dyra stora modeller för uppgifter som kräver komplexa resonemang.

**Cachelagring av svar:** Att identifiera vanliga förfrågningar och uppgifter och tillhandahålla svaren innan de går igenom ditt agentlika system är ett bra sätt att minska volymen av liknande förfrågningar. Du kan till och med implementera ett flöde för att identifiera hur lik en förfrågan är de cachelagrade förfrågningarna med hjälp av mer grundläggande AI-modeller. Denna strategi kan avsevärt minska kostnaderna för ofta ställda frågor eller vanliga arbetsflöden.

## Låt oss se hur detta fungerar i praktiken

I [exempelanteckningsboken i detta avsnitt](./code_samples/10_autogen_evaluation.ipynb) kommer vi att se exempel på hur vi kan använda verktyg för observabilitet för att övervaka och utvärdera vår agent.


### Har du fler frågor om AI-agenter i produktion?

Gå med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) för att träffa andra deltagare, delta i kontorstider och få dina frågor om AI-agenter besvarade.

## Föregående lektion

[Designmönster för metakognition](../09-metacognition/README.md)

## Nästa lektion

[Agentiska protokoll](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfriskrivning:
Detta dokument har översatts med hjälp av AI-översättningstjänsten Co-op Translator (https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet bör du vara medveten om att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på sitt originalspråk bör betraktas som den auktoritativa källan. För kritisk information rekommenderas en professionell mänsklig översättning. Vi ansvarar inte för eventuella missförstånd eller feltolkningar som uppstår vid användning av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->