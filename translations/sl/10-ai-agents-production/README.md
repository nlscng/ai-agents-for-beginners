# AI agenti v produkciji: Opazljivost in ocenjevanje

[![AI agenti v produkciji](../../../translated_images/sl/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

Ker AI agenti prehajajo iz eksperimentalnih prototipov v aplikacije v resničnem svetu, postaja pomembna sposobnost razumevanja njihovega vedenja, spremljanja zmogljivosti in sistematičnega ocenjevanja njihovih izhodov.

## Cilji učenja

Po končani lekciji boste znali/razumeli:
- Osnovne koncepte opazljivosti in ocenjevanja agentov
- Tehnike za izboljšanje zmogljivosti, stroškov in učinkovitosti agentov
- Kaj in kako sistematično ocenjevati vaše AI agente
- Kako nadzorovati stroške pri uvajanju AI agentov v produkcijo
- Kako instrumentirati agente zgrajene z AutoGen

Cilj je, da vas opremimo z znanjem, kako spremeniti vaše "črne skrinjice" agente v pregledne, obvladljive in zanesljive sisteme.

_**Opomba:** Pomembno je uvajati AI agente, ki so varni in zaupanja vredni. Oglejte si tudi lekcijo [Gradnja zaupanja vrednih AI agentov](./06-building-trustworthy-agents/README.md)._

## Sledi in spani

Orodja za opazljivost, kot sta [Langfuse](https://langfuse.com/) ali [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry), običajno predstavljajo izvedbe agentov kot sledi in spane.

- **Trace** predstavlja celotno nalogo agenta od začetka do konca (npr. obravnava uporabniške poizvedbe).
- **Spani** so posamezni koraki znotraj sledi (npr. klic jezikovnega modela ali pridobivanje podatkov).

![Drevo sledi v Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Brez opazljivosti se AI agent lahko zdi kot "črna skrinjica" — njegovo notranje stanje in sklepanje sta neprosojna, zaradi česar je težko diagnosticirati težave ali optimizirati delovanje. Z opazljivostjo agenti postanejo "steklene skrinjice", ki nudijo prosojnost, bistveno za gradnjo zaupanja in zagotavljanje delovanja po pričakovanjih.

## Zakaj je opazljivost pomembna v produkcijskih okoljih

Prehod AI agentov v produkcijska okolja prinaša nov nabor izzivov in zahtev. Opazljivost ni več "le lepo imeti", temveč ključna zmogljivost:

*   **Razhroščevanje in analiza izvornega vzroka**: Ko agent ne uspe ali poda nepričakovan izhod, orodja za opazljivost zagotavljajo sledi, potrebne za natančno lociranje vira napake. To je še posebej pomembno pri kompleksnih agentih, ki lahko vključujejo več klicev LLM, interakcije z orodji in pogojno logiko.
*   **Upravljanje zakasnitev in stroškov**: AI agenti pogosto temeljijo na LLM modelih in drugih zunanjih API-jih, za katere se zaračunava na token ali klic. Opazljivost omogoča natančno sledenje teh klicev in pomaga identificirati operacije, ki so pretirano počasne ali drage. To ekipam omogoča optimizacijo pozivov, izbiro bolj učinkovitih modelov ali prenovo potekov dela za obvladovanje operativnih stroškov in zagotavljanje dobre uporabniške izkušnje.
*   **Zaupanje, varnost in skladnost**: V mnogih aplikacijah je pomembno zagotavljanje varnega in etičnega vedenja agentov. Opazljivost nudi revizijsko sled dejanj in odločitev agenta. To lahko uporabite za zaznavanje in ublažitev težav, kot so injekcije pozivov, generiranje škodljive vsebine ali nepravilno ravnanje s osebno prepoznavnimi podatki (PII). Na primer, lahko pregledate sledi, da razumete, zakaj je agent podal določen odgovor ali uporabil določeno orodje.
*   **Zanke za neprekinjeno izboljševanje**: Podatki opazljivosti so temelj iterativnega razvojnega procesa. S spremljanjem, kako agenti delujejo v resničnem svetu, ekipe lahko identificirajo področja za izboljšave, zberejo podatke za fino nastavitev modelov in potrdijo vpliv sprememb. To ustvarja povratno zanko, kjer produkcijski vpogledi iz spletnega ocenjevanja informirajo offline eksperimentiranje in izpopolnjevanje, kar vodi k postopnemu izboljšanju zmogljivosti agentov.

## Ključni kazalniki za spremljanje

Za spremljanje in razumevanje vedenja agenta je treba spremljati vrsto kazalnikov in signalov. Specifični kazalniki se lahko razlikujejo glede na namen agenta, a nekateri so univerzalno pomembni.

Tukaj je nekaj najpogostejših kazalnikov, ki jih spremljajo orodja za opazljivost:

**Zakasnitev:** Kako hitro agent odgovori? Dolgi časi čakanja negativno vplivajo na uporabniško izkušnjo. Merite zakasnitev za naloge in posamezne korake z sledenjem izvedbam agenta. Na primer, agent, ki za vse klice modela porabi 20 sekund, bi lahko pohitrili z uporabo hitrejšega modela ali z vzporednim izvajanjem klicev modela.

**Stroški:** Koliko stane ena izvedba agenta? AI agenti se zanašajo na klice LLM, ki se zaračunavajo na token ali zunanje API-je. Pogosta uporaba orodij ali več pozivov lahko hitro poveča stroške. Na primer, če agent petkrat kliče LLM zaradi minimalnega izboljšanja kakovosti, morate oceniti, ali je strošek upravičen ali pa lahko zmanjšate število klicev ali uporabite cenejši model. Spremljanje v realnem času lahko tudi pomaga odkriti nepričakovane skoke (npr. napake, ki povzročajo pretirane API zanke).

**Napake zahtevkov:** Koliko zahtevkov je agent neuspel izvesti? To lahko vključuje API napake ali neuspešne klice orodij. Da bi agent naredili odpornejšega pred temi težavami v produkciji, lahko nastavite rezervne poti ali ponovitve. Npr. če ponudnik LLM A ne deluje, preklopite na ponudnika LLM B kot rezervnega.

**Povratne informacije uporabnikov:** Izvajanje neposrednih ocen uporabnikov zagotavlja dragocene vpoglede. To lahko vključuje eksplicitne ocene (👍thumbs-up/👎down, ⭐1-5 zvezdic) ali besedilne komentarje. Stalno negativno povratno informacijo naj vam prižge opozorilo, saj je to znak, da agent ne deluje po pričakovanjih. 

**Implicitne povratne informacije uporabnikov:** Vedenje uporabnikov nudi posredne povratne informacije tudi brez eksplicitnih ocen. To lahko vključuje takojšnje preoblikovanje vprašanja, ponavljene poizvedbe ali pritisk na gumb za ponovni poizkus. Npr. če opazite, da uporabniki večkrat zastavljajo isto vprašanje, je to znak, da agent ne deluje po pričakovanjih.

**Natančnost:** Kako pogosto agent ustvari pravilne ali zaželene izhode? Definicije natančnosti se razlikujejo (npr. pravilnost reševanja problemov, natančnost iskanja informacij, zadovoljstvo uporabnikov). Prvi korak je opredeliti, kako izgleda uspeh za vašega agenta. Natančnost lahko spremljate prek avtomatiziranih preverjanj, ocenjevalnih točk ali oznak dokončanja nalog. Na primer, označevanje sledi kot "uspešno" ali "neuspešno". 

**Samodejni evalvacijski kazalniki:** Prav tako lahko nastavite samodejne evaluacije. Na primer, lahko uporabite LLM za oceno izhoda agenta, npr. ali je koristen, natančen ali ne. Obstaja tudi več odprtokodnih knjižnic, ki pomagajo ocenjevati različne vidike agenta. Npr. [RAGAS](https://docs.ragas.io/) za RAG agente ali [LLM Guard](https://llm-guard.com/) za zaznavanje škodljivega jezika ali injekcij v pozive. 

V praksi kombinacija teh kazalnikov nudi najboljši vpogled v zdravje AI agenta. V tem poglavju v [primerovem zvezku](./code_samples/10_autogen_evaluation.ipynb) bomo prikazali, kako ti kazalniki izgledajo v resničnih primerih, a najprej se bomo naučili, kako tipičen potek ocenjevanja izgleda.

## Instrumentirajte svojega agenta

Za zbiranje podatkov o sledenju boste morali instrumentirati svojo kodo. Cilj je instrumentirati kodo agenta, da oddaja sledi in metrike, ki jih lahko zajame, obdela in vizualizira platforma za opazljivost.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) se je uveljavil kot industrijski standard za opazljivost LLM. Nudi nabor API-jev, SDK-jev in orodij za ustvarjanje, zbiranje in izvoz telemetričnih podatkov. 

Obstaja veliko knjižnic za instrumentiranje, ki ovijejo obstoječe ogrodje agentov in olajšajo izvoz OpenTelemetry spanov v orodje za opazljivost. Spodaj je primer instrumentiranja AutoGen agenta z [OpenLit instrumentation library](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

V tem poglavju bo [primer zvezka](./code_samples/10_autogen_evaluation.ipynb) prikazal, kako instrumentirati vaš AutoGen agent.

**Ročno ustvarjanje spanov:** Medtem ko knjižnice za instrumentiranje nudijo dobro osnovo, se pogosto pojavljajo primeri, kjer so potrebne bolj podrobne ali prilagojene informacije. Span-e lahko ročno ustvarite, da dodate prilagojeno aplikacijsko logiko. Še pomembneje, lahko obogatite samodejno ali ročno ustvarjene spane s prilagojenimi atributi (znanimi tudi kot oznake ali metapodatki). Ti atributi lahko vključujejo poslovno-specifične podatke, vmesne izračune ali katerikoli kontekst, ki je lahko uporaben za razhroščevanje ali analizo, kot so `user_id`, `session_id` ali `model_version`.

Primer ročnega ustvarjanja sledi in spanov z [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3): 

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Ocenjevanje agentov

Opazljivost nam daje metrike, vendar je ocenjevanje proces analiziranja teh podatkov (in izvajanja testov), da ugotovimo, kako dobro AI agent deluje in kako ga je mogoče izboljšati. Z drugimi besedami, ko imate te sledi in metrike, kako jih uporabite za presojanje agenta in sprejemanje odločitev? 

Redno ocenjevanje je pomembno, ker so AI agenti pogosto nedeterministični in se lahko spreminjajo (z nadgradnjami ali driftnim vedenjem modela) – brez ocenjevanja ne bi vedeli, ali vaš »pametni agent« dejansko opravlja svoje delo dobro ali pa je nazadoval.

Obstajata dve kategoriji ocenjevanj za AI agente: **online ocenjevanje** in **offline ocenjevanje**. Obe sta vredni in se dopolnjujeta. Običajno začnemo z offline ocenjevanjem, ker je to minimalni potreben korak pred uvajanjem katerega koli agenta.

### Offline ocenjevanje

![Elementi podatkovnega nabora v Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

To vključuje ocenjevanje agenta v nadzorovanem okolju, običajno z uporabo testnih podatkovnih nizov, ne z živimi uporabniškimi poizvedbami. Uporabite skrbno izbrane podatkovne nabore, kjer poznate pričakovani izhod ali pravilno vedenje, in nato zaženete agenta na teh podatkih. 

Na primer, če ste zgradili agenta za reševanje besedilnih matematičnih problemov, boste morda imeli [testni podatkovni niz](https://huggingface.co/datasets/gsm8k) s 100 problemi z znanimi odgovori. Offline ocenjevanje se pogosto izvaja med razvojem (in je lahko del CI/CD cevovodov), da preveri izboljšave ali zaščiti pred regresijami. Prednost je, da je **ponovljivo in lahko dobite jasne metrike natančnosti, saj imate referenčno resnico**. Prav tako lahko simulirate uporabniške poizvedbe in merite odzive agenta glede na idealne odgovore ali uporabite avtomatizirane metrike, kot je opisano zgoraj. 

Ključni izziv pri offline ocenjevanju je zagotavljanje, da je vaš testni podatkovni niz obsežen in ostane relevanten – agent je morda uspešen na fiksnem testnem naboru, vendar se lahko v produkciji sreča z zelo drugačnimi poizvedbami. Zato naj bodo testni nabori redno posodobljeni z novimi robnimi primeri in primeri, ki odražajo scenarije iz resničnega sveta. Mešanica majhnih "smoke test" primerov in večjih evalvacijskih nizov je uporabna: majhni nizi za hitre preglede in večji za obsežnejše metrike zmogljivosti.

### Online ocenjevanje 

![Pregled meril opazljivosti](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

To se nanaša na ocenjevanje agenta v živo, v resničnem okolju, tj. med dejansko uporabo v produkciji. Online ocenjevanje vključuje spremljanje zmogljivosti agenta pri resničnih uporabniških interakcijah in neprekinjeno analizo rezultatov. 

Na primer, morda spremljate stopnje uspeha, ocene zadovoljstva uporabnikov ali druge metrike na žičnem prometu. Prednost online ocenjevanja je, da **ujame stvari, ki jih morda v laboratoriju ne predvidevate** – lahko opazite drift modela skozi čas (če učinkovitost agenta upada, ko se vzorci vhodov spreminjajo) in ujamete nepričakovane poizvedbe ali situacije, ki niso bile v vaših testnih podatkih. Ponuja resnično sliko, kako agent deluje v divjini. 

Online ocenjevanje pogosto vključuje zbiranje implicitnih in eksplicitnih povratnih informacij uporabnikov, kot je bilo omenjeno, in morebiti izvajanje shadow testov ali A/B testov (kjer nova različica agenta teče vzporedno, da jo primerjate s staro). Izziv je, da je lahko težko pridobiti zanesljive oznake ali ocene za žive interakcije – pogosto se zanašate na povratne informacije uporabnikov ali metrika na bolj oddaljenih stopnjah (npr. ali je uporabnik kliknil rezultat).

### Združevanje obeh

Online in offline ocenjevanja nista izključujoča; sta zelo dopolnjujoča. Vpoglede iz spletnega spremljanja (npr. nove vrste uporabniških poizvedb, pri katerih agent deluje slabo) lahko uporabite za dopolnitev in izboljšanje offline testnih nizov. Obratno, agenti, ki se dobro obnesejo v offline testih, se nato lahko z več zaupanja uvedejo in spremljajo online. 

Dejansko mnoge ekipe sprejmejo zanko: 

_evaluate offline -> deploy -> monitor online -> collect new failure cases -> add to offline dataset -> refine agent -> repeat_.

## Pogoste težave

Ko uvajate AI agente v produkcijo, se lahko srečate z različnimi izzivi. Tukaj je nekaj pogostih težav in njihovih možnih rešitev:

| **Težava**    | **Možna rešitev**   |
| ------------- | ------------------ |
| AI Agent ne izvaja nalog dosledno | - Izboljšajte poziv, dan agentu; jasno določite cilje.<br>- Ugotovite, kje je smiselno razdeliti naloge na podnaloge in jih obravnavati z več agenti. |
| AI Agent se znajde v neskončnih zankah  | - Poskrbite za jasne pogoje za prekinitev, da agent ve, kdaj naj konča proces.<br>- Za kompleksne naloge, ki zahtevajo sklepanje in načrtovanje, uporabite večji model, specializiran za naloge sklepanja. |
| Klici orodij AI agenta ne delujejo dobro   | - Testirajte in potrdite izhod orodja zunaj sistema agenta.<br>- Izboljšajte definirane parametre, pozive in poimenovanje orodij.  |
| Sistem več agentov ne deluje dosledno | - Izboljšajte pozive, dane vsakemu agentu, da bodo specifični in različni med seboj.<br>- Zgradite hierarhični sistem z "usmerjevalnim" ali kontrolnim agentom, ki določi, kateri agent je pravi. |

Veliko teh težav je mogoče učinkoviteje odkriti z vzpostavljeno opazljivostjo. Sledi in metrike, o katerih smo govorili, pomagajo natančno določiti, kje v poteku dela agenta nastanejo problemi, kar olajša razhroščevanje in optimizacijo.

## Upravljanje stroškov
Tukaj je nekaj strategij za upravljanje stroškov uvajanja AI agentov v produkcijo:

**Using Smaller Models:** Majhni jezikovni modeli (SLMs) lahko dobro delujejo pri nekaterih agentskih primerih uporabe in bodo znatno znižali stroške. Kot je omenjeno prej, je najbolje zgraditi sistem za ocenjevanje, da določite in primerjate zmogljivost proti večjim modelom, saj je to najboljši način, da razumete, kako dobro bo SLM deloval v vašem primeru uporabe. Razmislite o uporabi SLM-jev za preprostejša opravila, kot so klasifikacija namena ali izvleček parametrov, medtem ko rezervirate večje modele za kompleksno razmišljanje.

**Using a Router Model:** Podobna strategija je uporaba različnih modelov in velikosti. Lahko uporabite LLM/SLM ali funkcijo brez strežnika za usmerjanje zahtev glede na kompleksnost do najbolj primernih modelov. To bo prav tako pomagalo znižati stroške, hkrati pa zagotoviti zmogljivost za pravilna opravila. Na primer, preproste poizvedbe usmerite na manjše, hitrejše modele in drage velike modele uporabite le za kompleksna razmišljanja.

**Caching Responses:** Prepoznavanje pogostih zahtev in opravil ter zagotavljanje odgovorov, preden gredo skozi vaš agentski sistem, je dober način za zmanjšanje obsega podobnih zahtev. Lahko celo uvedete potek, ki ugotavlja, kako podobna je zahteva vašim predpomnjenim zahtevam, z uporabo bolj osnovnih AI modelov. Ta strategija lahko znatno zmanjša stroške za pogosto zastavljena vprašanja ali običajne delovne tokove.

## Poglejmo, kako to deluje v praksi

V [primer zvezka tega razdelka](./code_samples/10_autogen_evaluation.ipynb) bomo videli primere, kako lahko uporabimo orodja za opazovanje za spremljanje in ocenjevanje našega agenta.


### Imate več vprašanj o AI agentih v produkciji?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), da se povežete z drugimi udeleženci, udeležite ur za vprašanja in dobite odgovore na vprašanja o AI agentih.

## Prejšnja lekcija

[Vzorec metakognicije](../09-metacognition/README.md)

## Naslednja lekcija

[Agentni protokoli](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Izjava o omejitvi odgovornosti:
Ta dokument je bil preveden z uporabo storitve za prevajanje z umetno inteligenco [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da avtomatizirani prevodi lahko vsebujejo napake ali netočnosti. Izvirni dokument v izvirnem jeziku velja za avtoritativni vir. Za kritične informacije priporočamo strokovni prevod, opravljen s strani usposobljenega prevajalca. Ne odgovarjamo za morebitne nesporazume ali napačne razlage, ki izhajajo iz uporabe tega prevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->