# AI agenti u proizvodnji: promatranje i evaluacija

[![AI Agents in Production](../../../translated_images/hr/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

Kako AI agenti prelaze iz eksperimentalnih prototipova u stvarne primjene, sposobnost razumijevanja njihovog ponašanja, praćenje njihove izvedbe i sustavna evaluacija njihovih izlaza postaju važni.

## Ciljevi učenja

Nakon dovršetka ove lekcije znat ćete kako/razumjeti:
- Osnovne koncepte promatranja i evaluacije agenata
- Tehnike za poboljšanje izvedbe, troškova i učinkovitosti agenata
- Što i kako sustavno evaluirati svoje AI agente
- Kako kontrolirati troškove pri uvođenju AI agenata u proizvodnju
- Kako instrumentirati agente izgrađene s AutoGen

Cilj je opremiti vas znanjem za pretvaranje vaših "crnih kutija" agenata u transparentne, upravljive i pouzdane sustave.

_**Napomena:** važno je implementirati AI agente koji su sigurni i pouzdani. Pogledajte i lekciju [Izgradnja pouzdanih AI agenata](./06-building-trustworthy-agents/README.md)._

## Tragači i segmenti

Alati za promatranje poput [Langfuse](https://langfuse.com/) ili [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) obično predstavljaju izvođenja agenata kao tragove i segmente.

- **Trag** predstavlja cjelovit zadatak agenta od početka do kraja (npr. obrada korisničkog upita).
- **Segmenti** su pojedinačni koraci unutar traga (npr. pozivanje jezičnog modela ili dohvat podataka).

![Trace tree in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Bez promatranja, AI agent može djelovati kao "crna kutija" - njegovo unutarnje stanje i razmišljanje su neprozirni, što otežava dijagnosticiranje problema ili optimizaciju izvedbe. S promatranjem, agenti postaju "staklene kutije", pružajući transparentnost koja je ključna za izgradnju povjerenja i osiguranje da rade kako je predviđeno.

## Zašto promatranje ima značaj u proizvodnim okruženjima

Prijenos AI agenata u proizvodna okruženja donosi nove izazove i zahtjeve. Promatranje više nije "lijepa za imati" nego kritična sposobnost:

*   **Otklanjanje pogrešaka i analiza uzroka:** Kad agent zakaže ili proizvede neočekivani rezultat, alati za promatranje pružaju tragove potrebne za točno lociranje izvora pogreške. To je posebno važno kod složenih agenata koji mogu uključivati više poziva na LLM, interakciju s alatima i uvjetnu logiku.
*   **Upravljanje kašnjenjem i troškovima:** AI agenti često ovise o LLM-ovima i drugim vanjskim API-jima koji se naplaćuju po tokenu ili pozivu. Promatranje omogućuje precizno praćenje tih poziva, pomažući identificirati operacije koje su pretjerano spore ili skupe. To omogućuje timovima optimizaciju upita, izbor učinkovitijih modela ili redizajn tijekova rada za kontrolu operativnih troškova i osiguranje dobrog korisničkog iskustva.
*   **Povjerenje, sigurnost i usklađenost:** U mnogim aplikacijama važno je osigurati da agenti djeluju sigurno i etički. Promatranje pruža zapis o akcijama i odlukama agenta. To se može koristiti za otkrivanje i sprječavanje problema poput unosa štetnih uputa, generiranja štetnog sadržaja ili neprimjerene obrade osobnih podataka (PII). Na primjer, možete pregledati tragove da biste razumjeli zašto je agent dao određeni odgovor ili upotrijebio određeni alat.
*   **Kontinuirani poboljšanja:** Podaci iz promatranja temelj su iterativnog razvojnog procesa. Praćenjem izvedbe agenata u stvarnom svijetu, timovi mogu identificirati područja za poboljšanje, prikupiti podatke za fino podešavanje modela i potvrditi utjecaj promjena. To stvara povratnu petlju u kojoj uvidi iz proizvodne evaluacije online informiraju offline eksperimentiranje i usavršavanje, dovodeći do postupno bolje izvedbe agenata.

## Ključni metrički pokazatelji za praćenje

Za praćenje i razumijevanje ponašanja agenata treba pratiti niz metrika i signala. Iako se specifične metrike mogu razlikovati ovisno o namjeni agenta, neke su univerzalno važne.

Ovdje su neke od najčešćih metrika koje alati za promatranje prate:

**Kašnjenje (Latency):** Koliko brzo agent odgovara? Dugo čekanje negativno utječe na korisničko iskustvo. Trebali biste mjeriti kašnjenje za zadatke i pojedinačne korake prateći izvođenje agenata. Na primjer, agent koji sve pozive modela obavi za 20 sekundi mogao bi se ubrzati korištenjem bržeg modela ili paralelnim izvođenjem poziva.

**Troškovi:** Koliki su troškovi po izvođenju agenta? AI agenti ovise o pozivima LLM-a koji se naplaćuju po tokenu ili o vanjskim API-jima. Često korištenje alata ili višestruki upiti mogu brzo povećati troškove. Na primjer, ako agent pet puta pozove LLM za neznatno poboljšanje kvalitete, morate procijeniti je li trošak opravdan ili možete smanjiti broj poziva ili koristiti jeftiniji model. Praćenje u stvarnom vremenu također može pomoći u otkrivanju neočekivanih skokova (npr. bugovi koji uzrokuju pretjerane petlje poziva API-ja).

**Pogreške zahtjeva:** Koliko je zahtjeva agent uspio obraditi? Ovo može uključivati pogreške API-ja ili neuspjele pozive alata. Da biste svog agenta učinili robusnijim u proizvodnji, možete postaviti rezervne opcije ili pokušaje ponovnog poziva. Npr. ako LLM pružatelj A nije dostupan, možete se prebaciti na LLM pružatelja B kao rezervu.

**Povratne informacije korisnika:** Implementiranjem direktnih korisničkih evaluacija dobivate vrijedne uvide. To može uključivati eksplicitne ocjene (👍za/👎protiv, ⭐1-5 zvjezdica) ili tekstualne komentare. Konzistentno negativne povratne informacije trebale bi vas upozoriti jer su znak da agent ne radi kako se očekuje.

**Implicitne povratne informacije korisnika:** Korisničko ponašanje pruža neizravne povratne informacije čak i bez eksplicitnih ocjena. To može uključivati trenutne preformulacije pitanja, ponovljene upite ili klikanje na gumb za ponovni pokušaj. Npr. ako vidite da korisnici više puta postavljaju isto pitanje, to je znak da agent ne radi kako se očekuje.

**Točnost:** Koliko često agent proizvodi točne ili poželjne rezultate? Definicije točnosti variraju (npr. rješenje problema, točnost dohvaćanja informacija, zadovoljstvo korisnika). Prvi je korak definirati što je uspjeh za vašeg agenta. Točnost možete pratiti preko automatiziranih provjera, rezultata evaluacije ili oznaka za završetak zadatka. Na primjer, označavanjem tragova kao "uspješno" ili "neuspješno".

**Automatizirane evaluacijske metrike:** Također možete postaviti automatizirane evaluacije. Na primjer, možete koristiti LLM za ocjenu izlaza agenta npr. je li koristan, točan ili nije. Postoji nekoliko open source biblioteka koje pomažu ocijeniti različite aspekte agenta. Npr. [RAGAS](https://docs.ragas.io/) za RAG agente ili [LLM Guard](https://llm-guard.com/) za otkrivanje štetnog jezika ili unosa štetnih uputa.

U praksi, kombinacija ovih metrika daje najbolju pokrivenost zdravstvenog stanja AI agenta. U ovom poglavlju [primjer bilježnice](./code_samples/10_autogen_evaluation.ipynb) pokazat ćemo vam kako ove metrike izgledaju u stvarnim primjerima, ali prvo ćemo naučiti kako izgleda tipični tijek evaluacije.

## Instrumentirajte svog agenta

Za prikupljanje podataka traga bit ćete u potrebi instrumentirati svoj kod. Cilj je instrumentirati kod agenta da emitira tragove i metrike koje može hvatati, obrađivati i vizualizirati platforma za promatranje.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) postao je industrijski standard za promatranje LLM-ova. Pruža skup API-ja, SDK-a i alata za generiranje, skupljanje i izvoz telemetrijskih podataka.

Postoji mnogo biblioteka za instrumentaciju koje omotavaju postojeće okvire za agente i olakšavaju izvoz OpenTelemetry segmenata u alat za promatranje. Ispod je primjer instrumentiranja AutoGen agenta s [OpenLit instrumentacijskom bibliotekom](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

Primjer bilježnice u ovom poglavlju ([example notebook](./code_samples/10_autogen_evaluation.ipynb)) pokazat će kako instrumentirati vaš AutoGen agent.

**Ručno kreiranje segmenata:** Iako instrumentacijske biblioteke pružaju dobru osnovu, često su potrebni detaljniji ili prilagođeni podaci. Možete ručno kreirati segmente za dodavanje prilagođene aplikacijske logike. Još važnije, mogu obogatiti automatski ili ručno stvarane segmente s prilagođenim atributima (poznatima i kao oznake ili metapodaci). Ti atributi mogu uključivati poslovno specifične podatke, međurezultate ili bilo koji kontekst koji može biti koristan za otklanjanje pogrešaka ili analizu, kao što su `user_id`, `session_id` ili `model_version`.

Primjer ručnog kreiranja tragova i segmenata s [Langfuse Python SDK-om](https://langfuse.com/docs/sdk/python/sdk-v3):

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Evaluacija agenta

Promatranje nam daje metrike, ali evaluacija je proces analize tih podataka (i izvođenja testova) za određivanje koliko dobro AI agent radi i kako se može poboljšati. Drugim riječima, kad imate te tragove i metrike, kako ih koristiti za ocjenu agenta i donošenje odluka?

Redovita evaluacija je važna jer AI agenti često nisu deterministički i mogu se mijenjati (kroz nadogradnje ili drift ponašanja modela) – bez evaluacije ne biste znali radi li vaš "pametni agent" dobar posao ili je nazadovao.

Postoje dvije kategorije evaluacija za AI agente: **online evaluacija** i **offline evaluacija**. Obje su vrijedne i nadopunjuju se. Obično počinjemo s offline evaluacijom, jer je to minimalni nužni korak prije uvođenja bilo kojeg agenta.

### Offline evaluacija

![Dataset items in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

To uključuje evaluaciju agenta u kontroliranom okruženju, tipično korištenjem testnih skupova podataka, a ne uživo korisničkih upita. Koristite kurirane skupove podataka gdje znate očekivani izlaz ili ispravno ponašanje, a zatim pokrećete svog agenta na njima.

Na primjer, ako ste napravili agenta za rješavanje matematičkih zadataka iz riječi, mogli biste imati [testni skup podataka](https://huggingface.co/datasets/gsm8k) od 100 problema s poznatim odgovorima. Offline evaluacija se često izvodi tijekom razvoja (i može biti dio CI/CD procesa) za provjeru poboljšanja ili zaštitu od regresija. Prednost je što je **ponovljivo i možete dobiti jasne metrike točnosti jer imate stvarne istinite podatke**. Također možete simulirati korisničke upite i mjeriti odgovore agenta prema idealnim odgovorima ili koristiti automatizirane metrike koje smo ranije opisali.

Glavni je izazov kod offline evaluacije osigurati da je vaš testni skup podataka sveobuhvatan i relevantan – agent može dobro raditi na fiksnom testnom skupu, ali se u proizvodnji suočiti s vrlo različitim upitima. Stoga trebate redovito ažurirati testne skupove novim rubnim slučajevima i primjerima koji odražavaju stvarne scenarije. Korisna je kombinacija manjeg "smoke test" skupa i većih evaluacijskih setova: manji setovi za brze provjere i veći za širu izvedbenu metriku.

### Online evaluacija

![Observability metrics overview](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Ovo označava evaluaciju agenta u živom, stvarnom okruženju, tj. tijekom stvarne upotrebe u proizvodnji. Online evaluacija uključuje praćenje izvedbe agenta na stvarnim korisničkim interakcijama i kontinuiranu analizu rezultata.

Na primjer, možete pratiti stope uspjeha, ocjene zadovoljstva korisnika ili druge metrike na živom prometu. Prednost online evaluacije je da **uhvati stvari koje ne biste mogli predvidjeti u laboratorijskom postavu** – možete uočiti drift modela tijekom vremena (ako učinkovitost agenta opada kako se obrasci ulaza mijenjaju) i uočiti neočekivane upite ili situacije koje nisu bile u vašim testnim podacima. Ona pruža stvarnu sliku o ponašanju agenta u prirodnom okruženju.

Online evaluacija često uključuje prikupljanje implicitnih i eksplicitnih povratnih informacija korisnika, kao što je ranije objašnjeno, te moguće provođenje shadow testova ili A/B testova (gdje nova verzija agenta radi paralelno kako bi se usporedila s starom). Izazov je što je teško dobiti pouzdane oznake ili ocjene za žive interakcije – možda se oslanjate na povratne informacije korisnika ili na izvedbene metrike (npr. je li korisnik kliknuo rezultat).

### Kombiniranje dvaju pristupa

Online i offline evaluacije nisu međusobno isključive; one su vrlo komplementarne. Uvidi iz online nadzora (npr. novi tipovi korisničkih upita na kojima agent loše radi) mogu se koristiti za nadopunu i poboljšanje offline testnih skupova. Suprotno, agenti koji dobro prolaze offline testove mogu se onda s većim povjerenjem implementirati i pratiti online.

Mnogi timovi zapravo usvajaju petlju:

_evaluacija offline -> implementacija -> nadzor online -> prikupljanje novih slučajeva neuspjeha -> dodavanje u offline skup -> fino podešavanje agenta -> ponavljanje_.

## Uobičajeni problemi

Prilikom uvođenja AI agenata u proizvodnju, možete naići na različite izazove. Evo nekoliko uobičajenih problema i mogućih rješenja:

| **Problem**    | **Moguće rješenje**   |
| ------------- | ------------------ |
| AI agent ne izvršava zadatke dosljedno | - Poboljšajte prompt dan AI agentu; budite jasni o ciljevima.<br>- Identificirajte gdje dijeljenje zadataka u podzadace koje obavljaju različiti agenti može pomoći. |
| AI agent zapada u kontinuirane petlje | - Osigurajte jasne uvjete zaustavljanja procesa da agent zna kada treba prekinuti.<br>- Za složene zadatke koji zahtijevaju rezoniranje i planiranje koristite veći model specijaliziran za te zadatke. |
| Pozivi alatu AI agenta ne funkcioniraju dobro | - Testirajte i validirajte izlaz alata izvan sustava agenta.<br>- Precizirajte definirane parametre, upite i imenovanje alata.  |
| Multi-agentni sustav ne radi dosljedno | - Poboljšajte upite danim svakom agentu kako bi bili specifični i različiti.<br>- Izgradite hijerarhijski sustav koristeći "routing" ili kontrolni agent za odabir ispravnog agenta. |

Mnogi od ovih problema mogu se učinkovitije identificirati s implementiranim promatranjem. Tragovi i metrike koje smo prethodno opisali pomažu precizno locirati problem u tijeku rada agenta, što otklanjanje pogrešaka i optimizaciju čini mnogo učinkovitijima.

## Upravljanje troškovima
Evo nekoliko strategija za upravljanje troškovima implementacije AI agenata u produkciju:

**Korištenje manjih modela:** Mali jezični modeli (SLM) mogu dobro funkcionirati u određenim agentnim slučajevima korištenja i značajno smanjiti troškove. Kao što je ranije spomenuto, izrada sustava za evaluaciju koji će odrediti i usporediti performanse u odnosu na veće modele najbolji je način da razumijete koliko će se SLM dobro pokazati za vaš slučaj korištenja. Razmislite o korištenju SLM-ova za jednostavnije zadatke poput klasifikacije namjere ili izdvajanja parametara, dok veće modele rezervirate za složeno zaključivanje.

**Korištenje rutera modela:** Slična strategija je korištenje raznolikosti modela i veličina. Možete koristiti LLM/SLM ili serverless funkciju za usmjeravanje zahtjeva temeljem složenosti prema modelima koji najbolje odgovaraju. Ovo će također pomoći u smanjenju troškova, a istovremeno osigurati performanse na pravim zadacima. Na primjer, jednostavne upite usmjerite na manje, brže modele, a skupe velike modele koristite samo za složene zadatke zaključivanja.

**Keširanje odgovora:** Identificiranje čestih zahtjeva i zadataka te pružanje odgovora prije nego što prođu kroz vaš agentni sustav dobar je način smanjenja volumena sličnih zahtjeva. Možete čak implementirati tijek rada za određivanje koliko je zahtjev sličan onima koje ste već keširali koristeći osnovnije AI modele. Ova strategija može značajno smanjiti troškove za često postavljana pitanja ili uobičajene radne tokove.

## Pogledajmo kako ovo funkcionira u praksi

U [primjernom bilježniku ovog odjeljka](./code_samples/10_autogen_evaluation.ipynb) vidjet ćemo primjere kako možemo koristiti alate za promatranje i procjenu našeg agenta.


### Imate li još pitanja o AI agentima u produkciji?

Pridružite se [Microsoft Foundry Discordu](https://aka.ms/ai-agents/discord) kako biste se upoznali s drugim polaznicima, sudjelovali na uredskim satima i dobili odgovore na vaša pitanja o AI agentima.

## Prethodna lekcija

[Metakognitivni obrazac dizajna](../09-metacognition/README.md)

## Sljedeća lekcija

[Agentni protokoli](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Odricanje od odgovornosti**:
Ovaj dokument je preveden pomoću AI servis za prijevod [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo postići točnost, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba se smatrati službenim i vjerodostojnim izvorom. Za važne informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakva nesporazuma ili pogrešne interpretacije koje proizlaze iz korištenja ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->