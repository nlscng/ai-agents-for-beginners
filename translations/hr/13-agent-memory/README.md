# Memorija za AI agente
[![Agent Memory](../../../translated_images/hr/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Kad se raspravlja o jedinstvenim prednostima stvaranja AI agenata, uglavnom se raspravlja o dvije stvari: mogućnosti pozivanja alata za izvršavanje zadataka i sposobnosti poboljšanja tijekom vremena. Memorija je temelj za stvaranje agenta koji sam sebe poboljšava i može stvarati bolje iskustvo za naše korisnike.

U ovoj lekciji pogledat ćemo što je memorija za AI agente i kako je možemo upravljati i koristiti u korist naših aplikacija.

## Uvod

Ova lekcija obuhvaća:

• **Razumijevanje memorije AI agenta**: Što je memorija i zašto je bitna za agente.

• **Implementacija i pohrana memorije**: Praktične metode dodavanja memorijskih sposobnosti vašim AI agentima, s fokusom na kratkotrajnu i dugotrajnu memoriju.

• **Kako učiniti AI agente samopoboljšavajućim**: Kako memorija omogućuje agentima učenje iz prošlih interakcija i poboljšanje kroz vrijeme.

## Dostupne implementacije

Ova lekcija uključuje dva opširna tutoriala u bilježnici:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementira memoriju koristeći Mem0 i Azure AI Search s Semantic Kernel okvirom

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementira strukturiranu memoriju koristeći Cognee, automatski gradi graf znanja potkrijepljen embeddingima, vizualizira graf i inteligentno dohvaćanje

## Ciljevi učenja

Nakon završetka ove lekcije znat ćete kako:

• **Razlikovati različite vrste memorije AI agenta**, uključujući radnu, kratkotrajnu i dugotrajnu memoriju, kao i specijalizirane oblike poput memorije persona i epizodne memorije.

• **Implementirati i upravljati kratkotrajnom i dugotrajnom memorijom za AI agente** koristeći Semantic Kernel okvir, koristeći alate poput Mem0, Cognee, Whiteboard memoriju i integraciju s Azure AI Search.

• **Razumjeti principe iza samopoboljšavajućih AI agenata** i kako robusni sustavi upravljanja memorijom pridonose kontinuiranom učenju i adaptaciji.

## Razumijevanje memorije AI agenta

U svojoj srži, **memorija za AI agente odnosi se na mehanizme koji im omogućuju zadržavanje i prisjećanje informacija**. Te informacije mogu biti specifični detalji o razgovoru, korisničke preferencije, prošli postupci ili čak naučeni obrasci.

Bez memorije, AI aplikacije često su bezstanja, što znači da svaka interakcija počinje ispočetka. To vodi do ponavljajućeg i frustrirajućeg korisničkog iskustva gdje agent "zaboravlja" prethodni kontekst ili preferencije.

### Zašto je memorija važna?

Inteligencija agenta duboko je povezana s njegovom sposobnošću prisjećanja i korištenja prošlih informacija. Memorija omogućuje agentima da budu:

• **Refleksivni**: Učeći iz prošlih postupaka i ishoda.

• **Interaktivni**: Održavajući kontekst tijekom tekućeg razgovora.

• **Proaktivni i reaktivni**: Predviđajući potrebe ili odgovarajući prikladno na temelju povijesnih podataka.

• **Autonomni**: Djelujući samostalnije oslanjajući se na pohranjeno znanje.

Cilj implementacije memorije je učiniti agente **pouzdanijima i sposobnijima**.

### Vrste memorije

#### Radna memorija

Razmislite o tome kao o papiriću na kojem agent piše tijekom jednog tekućeg zadatka ili misaonog procesa. Čuva neposredne informacije potrebne za izračun sljedećeg koraka.

Za AI agente, radna memorija često hvata najrelevantnije informacije iz razgovora, čak i ako je cijela povijest chata duga ili skraćena. Fokusira se na ispravljanje ključnih elemenata poput zahtjeva, prijedloga, odluka i akcija.

**Primjer radne memorije**

U agentu za rezervaciju putovanja, radna memorija može zadržati trenutni zahtjev korisnika, poput "Želim rezervirati putovanje u Pariz". Taj specifični zahtjev nalazi se u neposrednom kontekstu agenta kako bi usmjerio trenutnu interakciju.

#### Kratkotrajna memorija

Ova vrsta memorije zadržava informacije tijekom trajanja jednog razgovora ili sesije. To je kontekst trenutnog chata, omogućujući agentu da se vraća na prethodne dijelove dijaloga.

**Primjer kratkotrajne memorije**

Ako korisnik pita, "Koliko bi koštao let za Pariz?" a zatim dodaje, "A što je s smještajem tamo?", kratkotrajna memorija osigurava da agent zna da "tamo" u istoj konverzaciji znači "Pariz".

#### Dugotrajna memorija

To su informacije koje traju kroz više razgovora ili sesija. Omogućuje agentima da pamte korisničke preferencije, povijesne interakcije ili opće znanje kroz dulja razdoblja. To je važno za personalizaciju.

**Primjer dugotrajne memorije**

Dugotrajna memorija može pohraniti da "Ben voli skijanje i aktivnosti na otvorenom, voli kavu s pogledom na planinu i želi izbjeći zahtjevne skijaške staze zbog prošle ozljede". Te informacije, naučene iz prethodnih interakcija, utječu na preporuke u budućim planiranjima putovanja, čineći ih izrazito personaliziranima.

#### Memorija persona

Ova specijalizirana vrsta memorije pomaže agentu razviti dosljednu "ličnost" ili "personu". Omogućuje agentu da pamti detalje o sebi ili svojoj zamišljenoj ulozi, čineći interakcije fluidnijima i fokusiranijima.

**Primjer memorije persona**

Ako je agent za putovanja dizajniran kao "stručni planer skijanja", memorija persona može ojačati tu ulogu, utječući na njegove odgovore da budu prilagođeni tonu i znanju stručnjaka.

#### Radni tok / Epizodna memorija

Ova memorija pohranjuje niz koraka koje agent poduzima tijekom složenog zadatka, uključujući uspjehe i neuspjehe. To je poput pamćenja specifičnih "epizoda" ili prošlih iskustava radi učenja iz njih.

**Primjer epizodne memorije**

Ako je agent pokušao rezervirati određeni let, ali je to propalo zbog nedostupnosti, epizodna memorija može zabilježiti ovaj neuspjeh, što agentu omogućava da pokuša alternativne letove ili korisniku informira o problemu na informiraniji način pri sljedećem pokušaju.

#### Memorija entiteta

Ona uključuje izdvajanje i pamćenje specifičnih entiteta (poput ljudi, mjesta ili stvari) i događaja iz razgovora. Omogućuje agentu izgradnju strukturiranog razumijevanja ključnih elemenata o kojima se razgovaralo.

**Primjer memorije entiteta**

Iz razgovora o prošlom putovanju, agent može izdvojiti "Pariz", "Eiffelov toranj" i "večera u restoranu Le Chat Noir" kao entitete. U budućoj interakciji agent može prisjetiti "Le Chat Noir" i ponuditi novu rezervaciju tamo.

#### Strukturirani RAG (Retrieval Augmented Generation)

Iako je RAG šira tehnika, "Strukturirani RAG" ističe se kao moćna tehnologija memorije. Izvlači gusta, strukturirana znanja iz različitih izvora (razgovora, e-mailova, slika) i koristi ih za poboljšanje preciznosti, prizivanja i brzine odgovora. Za razliku od klasičnog RAG-a koji se oslanja samo na semantičku sličnost, Strukturirani RAG koristi ugrađenu strukturu informacija.

**Primjer strukturiranog RAG-a**

Umjesto samo podudaranja ključnih riječi, Strukturirani RAG može parsirati detalje leta (odredište, datum, vrijeme, zrakoplovna kompanija) iz e-maila i pohraniti ih strukturirano. To omogućuje precizne upite poput "Koji sam let rezervirao za Pariz u utorak?"

## Implementacija i pohrana memorije

Implementacija memorije za AI agente uključuje sustavni proces **upravljanja memorijom**, koji uključuje generiranje, pohranu, dohvat, integraciju, ažuriranje pa čak i "zaboravljanje" (ili brisanje) informacija. Dohvat je osobito važan aspekt.

### Specijalizirani alati za memoriju

#### Mem0

Jedan od načina pohrane i upravljanja memorijom agenta je korištenje specijaliziranih alata poput Mem0. Mem0 radi kao sloj trajne memorije, koji omogućuje agentima da se prisjete relevantnih interakcija, pohrane korisničke preferencije i činjenični kontekst, te uče iz uspjeha i neuspjeha tijekom vremena. Ideja je da bezstanja agenti postanu agensi sa stanjem.

Radi kroz **dvostupanjski memorijski proces: ekstrakciju i ažuriranje**. Prvo se poruke dodane u nit agenta šalju usluzi Mem0, koja koristi Veliki jezični model (LLM) za sažimanje povijesti razgovora i izdvajanje novih memorija. Zatim, faza ažuriranja koju vodi LLM odlučuje hoće li te memorije dodati, izmijeniti ili izbrisati, pohranjujući ih u hibridnu bazu podataka koja može uključivati vektorske, graf i ključ-vrijednost baze. Ovaj sustav također podržava razne vrste memorije i može uključiti graf-memoriju za upravljanje odnosima među entitetima.

#### Cognee

Drugi moćan pristup je korištenje **Cogneea**, open-source semantičke memorije za AI agente koja pretvara strukturirane i nestrukturirane podatke u upitljive grafove znanja potkrijepljene embeddingima. Cognee pruža **dvoslojnu arhitekturu** koja kombinira pretraživanje po vektorskoj sličnosti s grafovima odnosa, omogućujući agentima da razumiju ne samo što je informacija slična, nego i kako su koncepti međusobno povezani.

Izvrsno je za **hibridni dohvat** koji miješa vektorsku sličnost, graf strukturu i LLM rezoniranje – od pretraživanja sirovih dijelova do graf-ponašanog odgovaranja na pitanja. Sustav održava **živu memoriju** koja se razvija i raste, a ostaje dostupna za upite kao jedan povezani graf, podržavajući i kratkotrajni kontekst sesije i dugotrajnu trajnu memoriju.

Tutorial u bilježnici Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstrira izgradnju ovog ujedinjenog sloja memorije, s praktičnim primjerima upijanja raznovrsnih izvora podataka, vizualizacijom grafa znanja i upitima s različitim strategijama pretraživanja prilagođenima specifičnim potrebama agenata.

### Pohrana memorije s RAG-om

Osim specijaliziranih alata za pamćenje poput Mem0, možete iskoristiti robusne usluge pretraživanja kao što je **Azure AI Search kao pozadinu za pohranu i dohvat memorija**, osobito za strukturirani RAG.

To vam omogućuje da oslonite odgovore svog agenta na vlastite podatke, osiguravajući relevantnije i točnije odgovore. Azure AI Search može se koristiti za pohranu korisničkih memorija o putovanjima, katalozima proizvoda ili bilo kojem drugom specifičnom znanju iz domena.

Azure AI Search podržava mogućnosti poput **strukturiranog RAG-a**, koji izvrsno izdvaja i dohvaća guste, strukturirane informacije iz velikih skupova podataka poput povijesti razgovora, e-mailova ili čak slika. To pruža "nadzvukovitu preciznost i prizivanje" u usporedbi s tradicionalnim pristupima dijeljenju teksta i embeddinga.

## Kako učiniti AI agente samopoboljšavajućima

Čest obrazac za samopoboljšavajuće agente uključuje uvođenje **"agenta za znanje"**. Taj odvojeni agent promatra glavni razgovor između korisnika i glavnog agenta. Njegova uloga je:

1. **Identificirati vrijedne informacije**: Odrediti je li neki dio razgovora vrijedan pohranjivanja kao opće znanje ili specifična korisnička preferencija.

2. **Izvući i sažeti**: Izraditi bitno učenje ili preferenciju iz razgovora.

3. **Pohraniti u bazu znanja**: Sačuvati ove izdvojene informacije, često u vektorsku bazu podataka, kako bi ih kasnije mogli dohvatiti.

4. **Obogatiti buduće upite**: Kad korisnik pokrene novi upit, agent za znanje dohvaća relevantne pohranjene informacije i dodaje ih u korisnički upit, pružajući ključni kontekst glavnom agentu (slično RAG-u).

### Optimizacije za memoriju

• **Upravljanje latencijom**: Kako ne bi usporili korisničke interakcije, na početku se može koristiti jeftiniji, brži model za brzu provjeru je li informacija vrijedna za pohranu ili dohvat, a složeniji proces ekstrakcije/dohvata pokreće se samo kad je potrebno.

• **Održavanje baze znanja**: Za rastuću bazu znanja, informacije koje se rjeđe koriste mogu se premjestiti u "hladnu pohranu" radi upravljanja troškovima.

## Imate još pitanja o memoriji agenata?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kako biste se upoznali s drugim učenicima, sudjelovali u radnim satima i dobili odgovore na pitanja o AI agentima.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Napomena**:
Ovaj dokument je preveden pomoću AI prevoditeljske usluge [Co-op Translator](https://github.com/Azure/co-op-translator). Iako težimo točnosti, molimo imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati službenim izvorom. Za važne informacije preporučujemo profesionalni ljudski prijevod. Nismo odgovorni za bilo kakve nesporazume ili pogrešna tumačenja proizašla iz korištenja ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->