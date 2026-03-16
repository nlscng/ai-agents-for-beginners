[![Dizajn sustava s više agenata](../../../translated_images/hr/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Kliknite sliku iznad da pogledate video ove lekcije)_

# Obrasci dizajna za sustave s više agenata

Čim počnete raditi na projektu koji uključuje više agenata, morat ćete razmotriti obrazac dizajna za više agenata. Međutim, možda neće biti odmah jasno kada prijeći na sustav s više agenata i koje su prednosti.

## Uvod

U ovoj lekciji nastojimo odgovoriti na sljedeća pitanja:

- Na koje se scenarije primjenjuju sustavi s više agenata?
- Koje su prednosti korištenja sustava s više agenata u odnosu na jednog agenta koji obavlja više zadataka?
- Koji su gradivni elementi implementacije obrasca dizajna za više agenata?
- Kako imati uvid u to kako se agenti međusobno međusobno povezuju i komuniciraju?

## Ciljevi učenja

Nakon ove lekcije trebali biste moći:

- Prepoznati scenarije u kojima su sustavi s više agenata primjenjivi
- Uočiti prednosti korištenja sustava s više agenata u odnosu na jednog agenta
- Razumjeti gradivne elemente implementacije obrasca dizajna za više agenata

Koja je šira slika?

*Sustavi s više agenata su obrazac dizajna koji omogućuje da više agenata surađuje kako bi postigli zajednički cilj*.

Ovaj obrazac se široko koristi u raznim područjima, uključujući robotiku, autonomne sustave i distribuirano računarstvo.

## Scenariji u kojima su sustavi s više agenata primjenjivi

Koji su slučajevi dobar izbor za korištenje više agenata? Odgovor je da postoji mnogo scenarija u kojima je korisno koristiti više agenata, osobito u sljedećim slučajevima:

- **Velika opterećenja**: Velike radne količine mogu se podijeliti na manje zadatke i dodijeliti različitim agentima, što omogućuje paralelnu obradu i brže dovršenje. Primjer za to je veliki zadatak obrade podataka.
- **Kompleksni zadaci**: Kompleksne zadaće, poput velikih opterećenja, mogu se razbiti na manje podzadatke i dodijeliti različitim agentima, od kojih se svaki specijalizira za određeni aspekt zadatka. Dobar primjer za to su autonomna vozila gdje različiti agenti upravljaju navigacijom, otkrivanjem prepreka i komunikacijom s drugim vozilima.
- **Raznolika stručnost**: Različiti agenti mogu imati raznoliku stručnost, što im omogućuje da učinkovitije rješavaju različite aspekte zadatka nego jedan agent. U tom slučaju dobar primjer je zdravstvena zaštita gdje agenti mogu upravljati dijagnostikom, planovima liječenja i praćenjem pacijenata.

## Prednosti korištenja sustava s više agenata u odnosu na jednog agenta

Sustav s jednim agentom mogao bi dobro funkcionirati za jednostavne zadatke, ali za složenije zadatke korištenje više agenata može pružiti nekoliko prednosti:

- **Specijalizacija**: Svaki agent može biti specijaliziran za određeni zadatak. Nedostatak specijalizacije u jednom agentu znači da imate agenta koji može raditi sve, ali se može zbuniti što treba raditi kada se suoči sa složenim zadatkom. Na primjer, može na kraju obaviti zadatak za koji nije najbolje prikladan.
- **Skalabilnost**: Lakše je skalirati sustave dodavanjem više agenata nego preopterećivanjem jednog agenta.
- **Otpornost na greške**: Ako jedan agent zakaže, ostali mogu nastaviti s radom, osiguravajući pouzdanost sustava.

Uzmimo primjer — rezervirajmo putovanje za korisnika. Sustav s jednim agentom morao bi se baviti svim aspektima procesa rezervacije putovanja, od pronalaženja letova do rezervacije hotela i najma automobila. Da bi to postigao, jedan agent trebao bi imati alate za rukovanje svim tim zadacima. To bi moglo rezultirati složenim i monolitnim sustavom koji je teško održavati i skalirati. Sustav s više agenata, s druge strane, mogao bi imati različite agente specijalizirane za pronalaženje letova, rezervaciju hotela i najam automobila. To bi sustav učinilo modularnijim, lakšim za održavanje i skalabilnim.

Usporedite to s putničkom agencijom vođenom kao obiteljska agencija naspram franšize. Obiteljska agencija imala bi jednog agenta koji rješava sve aspekte procesa rezervacije putovanja, dok bi franšiza imala različite agente koji se bave različitim aspektima procesa rezervacije.

## Gradivni elementi implementacije obrasca dizajna za više agenata

Prije nego što možete implementirati obrazac dizajna za više agenata, morate razumjeti gradivne elemente koji čine taj obrazac.

Da bismo to učinili konkretnijim, ponovno pogledajmo primjer rezervacije putovanja za korisnika. U tom slučaju gradivni elementi uključivali bi:

- **Komunikacija agenata**: Agenti za pronalaženje letova, rezervaciju hotela i najam automobila trebaju komunicirati i dijeliti informacije o korisničkim preferencijama i ograničenjima. Trebate odlučiti o protokolima i metodama za tu komunikaciju. Konkretno, agent za pronalaženje letova mora komunicirati s agentom za rezervaciju hotela kako bi osigurao da je hotel rezerviran za iste datume kao i let. To znači da agenti trebaju dijeliti informacije o datumima putovanja korisnika, što znači da trebate odlučiti *koji agenti dijele informacije i kako ih dijele*.
- **Mehanizmi koordinacije**: Agenti trebaju koordinirati svoje akcije kako bi osigurali da su korisničke preferencije i ograničenja zadovoljena. Korisnička preferencija mogla bi biti da žele hotel blizu zračne luke, dok ograničenje može biti da su najamni automobili dostupni samo na zračnoj luci. To znači da agent za rezervaciju hotela treba koordinirati s agentom za rezervaciju najma automobila kako bi osigurao da su korisničke preferencije i ograničenja zadovoljena. To znači da trebate odlučiti *kako agenti koordiniraju svoje akcije*.
- **Arhitektura agenata**: Agenti trebaju imati unutarnju strukturu za donošenje odluka i učenje iz svojih interakcija s korisnikom. To znači da agent za pronalaženje letova treba imati unutarnju strukturu za donošenje odluka o tome koje letove preporučiti korisniku. To znači da trebate odlučiti *kako agenti donose odluke i uče iz svojih interakcija s korisnikom*. Primjeri kako agent uči i poboljšava se mogli bi biti da agent za pronalaženje letova koristi model strojnog učenja za preporučivanje letova korisniku na temelju njihovih prethodnih preferencija.
- **Vidljivost interakcija među agentima**: Trebate imati uvid u to kako se više agenata međusobno povezuje i komunicira. To znači da trebate imati alate i tehnike za praćenje aktivnosti i interakcija agenata. To može biti u obliku alata za evidentiranje i nadzor, alata za vizualizaciju i metrika izvedbe.
- **Obrasci za sustave s više agenata**: Postoje različiti obrasci za implementaciju sustava s više agenata, poput centraliziranih, decentraliziranih i hibridnih arhitektura. Trebate odlučiti o obrascu koji najbolje odgovara vašem slučaju korištenja.
- **Čovjek u petlji**: U većini slučajeva imat ćete čovjeka u petlji i trebate uputiti agente kada tražiti ljudsku intervenciju. To može biti u obliku korisnika koji traži određeni hotel ili let koji agenti nisu preporučili ili traženja potvrde prije rezervacije leta ili hotela.

## Vidljivost interakcija među agentima

Važno je imati uvid u to kako se više agenata međusobno povezuje i komunicira. Ta vidljivost je ključna za otklanjanje pogrešaka, optimizaciju i osiguravanje učinkovitosti sustava u cjelini. Da biste to postigli, trebate imati alate i tehnike za praćenje aktivnosti i interakcija agenata. To može biti u obliku alata za evidentiranje i nadzor, alata za vizualizaciju i metrika izvedbe.

Na primjer, u slučaju rezervacije putovanja za korisnika, mogli biste imati nadzornu ploču koja prikazuje status svakog agenta, korisničke preferencije i ograničenja te interakcije među agentima. Ta nadzorna ploča mogla bi prikazivati datume putovanja korisnika, letove koje je preporučio agent za letove, hotele koje je preporučio agent za hotele i najamne automobile koje je preporučio agent za najam automobila. To bi vam dalo jasan uvid u to kako agenti međusobno komuniciraju i zadovoljavaju li se korisničke preferencije i ograničenja.

Pogledajmo svaki od ovih aspekata detaljnije.

- **Alati za evidentiranje i nadzor**: Želite imati evidentiranje za svaku radnju koju agent poduzme. Unos u zapisnik mogao bi pohraniti informacije o agentu koji je poduzeo radnju, poduzetoj radnji, vremenu kada je radnja poduzeta i ishodu radnje. Te se informacije potom mogu koristiti za otklanjanje pogrešaka, optimizaciju i drugo.

- **Alati za vizualizaciju**: Alati za vizualizaciju mogu vam pomoći da intuitivnije vidite interakcije među agentima. Na primjer, mogli biste imati graf koji prikazuje tok informacija između agenata. To bi vam moglo pomoći identificirati uska grla, neučinkovitosti i druge probleme u sustavu.

- **Metrike učinka**: Metrike učinka mogu vam pomoći pratiti učinkovitost sustava s više agenata. Na primjer, mogli biste pratiti vrijeme potrebno za dovršetak zadatka, broj zadataka dovršenih po jedinici vremena i točnost preporuka koje daju agenti. Te informacije mogu vam pomoći identificirati područja za poboljšanje i optimizirati sustav.

## Obrasci sustava s više agenata

Zaronimo u neke konkretne obrasce koje možemo koristiti za izradu aplikacija s više agenata. Ovdje su neki zanimljivi obrasci koje vrijedi razmotriti:

### Grupni razgovor

Ovaj je obrazac koristan kada želite stvoriti aplikaciju za grupni razgovor u kojoj više agenata može međusobno komunicirati. Tipični slučajevi korištenja za ovaj obrazac uključuju timsku suradnju, korisničku podršku i društvene mreže.

U ovom obrascu svaki agent predstavlja korisnika u grupnom razgovoru, a poruke se razmjenjuju između agenata koristeći protokol za razmjenu poruka. Agenti mogu slati poruke u grupni razgovor, primati poruke iz grupnog razgovora i odgovarati na poruke od drugih agenata.

Ovaj se obrazac može implementirati koristeći centraliziranu arhitekturu u kojoj sve poruke prolaze kroz središnji poslužitelj, ili decentraliziranu arhitekturu u kojoj se poruke razmjenjuju izravno.

![Grupni razgovor](../../../translated_images/hr/multi-agent-group-chat.ec10f4cde556babd.webp)

### Predaja zadatka

Ovaj je obrazac koristan kada želite stvoriti aplikaciju u kojoj više agenata može prenositi zadatke jedni drugima.

Tipični slučajevi korištenja za ovaj obrazac uključuju korisničku podršku, upravljanje zadacima i automatizaciju radnih tokova.

U ovom obrascu svaki agent predstavlja zadatak ili korak u radnom toku, a agenti mogu predavati zadatke drugim agentima na temelju unaprijed definiranih pravila.

![Predaja zadatka](../../../translated_images/hr/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Suradničko filtriranje

Ovaj je obrazac koristan kada želite stvoriti aplikaciju u kojoj više agenata može surađivati pri davanju preporuka korisnicima.

Razlog zašto želite da više agenata surađuje jest taj što svaki agent može imati različitu stručnost i može pridonijeti procesu preporuka na različite načine.

Uzmimo primjer gdje korisnik želi preporuku za najbolju dionicu za kupnju na burzi.

- **Stručnjak za industriju**: Jedan agent mogao bi biti stručnjak za određenu industriju.
- **Tehnička analiza**: Drugi agent mogao bi biti stručnjak za tehničku analizu.
- **Fundamentalna analiza**: Još jedan agent mogao bi biti stručnjak za fundamentalnu analizu. Suradnjom ti agenti mogu korisniku pružiti sveobuhvatniju preporuku.

![Preporuka](../../../translated_images/hr/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenarij: Proces povrata novca

Razmotrite scenarij u kojem kupac pokušava dobiti povrat novca za proizvod; u tom procesu može biti uključeno prilično mnogo agenata, ali podijelimo ih između agenata specifičnih za ovaj proces i općih agenata koji se mogu koristiti u drugim procesima.

**Agenti specifični za proces povrata**:

Slijede neki agenti koji bi mogli biti uključeni u proces povrata:

- **Agent kupca**: Ovaj agent predstavlja kupca i odgovoran je za pokretanje procesa povrata.
- **Agent prodavača**: Ovaj agent predstavlja prodavača i odgovoran je za obradu povrata.
- **Agent za plaćanje**: Ovaj agent predstavlja proces plaćanja i odgovoran je za vraćanje kupčeve uplate.
- **Agent za rješavanje**: Ovaj agent predstavlja proces rješavanja problema i odgovoran je za rješavanje bilo kakvih problema koji se pojave tijekom procesa povrata.
- **Agent za usklađenost**: Ovaj agent predstavlja proces usklađenosti i odgovoran je za osiguravanje da je proces povrata u skladu s propisima i politikama.

**Opći agenti**:

Ove agente možete koristiti u drugim dijelovima vašeg poslovanja.

- **Agent dostave**: Ovaj agent predstavlja proces dostave i odgovoran je za slanje proizvoda natrag prodavaču. Ovaj agent može se koristiti i za proces povrata i za opću dostavu proizvoda prilikom kupnje, na primjer.
- **Agent za povratne informacije**: Ovaj agent predstavlja proces prikupljanja povratnih informacija i odgovoran je za prikupljanje povratnih informacija od kupca. Povratne informacije mogu se prikupljati u bilo kojem trenutku, a ne samo tijekom procesa povrata.
- **Agent za eskalaciju**: Ovaj agent predstavlja proces eskalacije i odgovoran je za eskalaciju problema na višu razinu podrške. Ovaj tip agenta možete koristiti za bilo koji proces u kojem trebate eskalirati problem.
- **Agent za obavijesti**: Ovaj agent predstavlja proces obavještavanja i odgovoran je za slanje obavijesti kupcu u različitim fazama procesa povrata.
- **Agent za analitiku**: Ovaj agent predstavlja proces analitike i odgovoran je za analiziranje podataka povezanih s procesom povrata.
- **Agent za reviziju**: Ovaj agent predstavlja proces revizije i odgovoran je za reviziju procesa povrata kako bi se osiguralo da se provodi ispravno.
- **Agent za izvještavanje**: Ovaj agent predstavlja proces izvještavanja i odgovoran je za generiranje izvještaja o procesu povrata.
- **Agent za znanje**: Ovaj agent predstavlja proces upravljanja znanjem i odgovoran je za održavanje baze znanja informacija povezanih s procesom povrata. Ovaj agent mogao bi imati znanje i o povratima i o drugim dijelovima vašeg poslovanja.
- **Agent sigurnosti**: Ovaj agent predstavlja proces sigurnosti i odgovoran je za osiguravanje sigurnosti procesa povrata.
- **Agent kvalitete**: Ovaj agent predstavlja proces osiguranja kvalitete i odgovoran je za osiguravanje kvalitete procesa povrata.

Ranije je navedeno prilično mnogo agenata, kako za specifični proces povrata, tako i općih agenata koji se mogu koristiti u drugim dijelovima vašeg poslovanja. Nadamo se da vam to daje ideju kako odlučiti koje agente koristiti u svom sustavu s više agenata.

## Zadatak

Dizajnirajte sustav s više agenata za proces korisničke podrške. Identificirajte agente uključene u proces, njihove uloge i odgovornosti te kako međusobno komuniciraju. Uzmite u obzir i agente specifične za proces korisničke podrške i opće agente koji se mogu koristiti u drugim dijelovima vašeg poslovanja.
> Razmislite prije nego pročitate sljedeće rješenje, možda će vam trebati više agenata nego što mislite.
> SAVJET: Razmislite o različitim fazama procesa korisničke podrške i također uzmite u obzir agente potrebne za bilo koji sustav.

## Rješenje

[Rješenje](./solution/solution.md)

## Provjere znanja

Question: When should you consider using multi-agents?

- [ ] A1: Kada imate mali opseg posla i jednostavan zadatak.
- [ ] A2: Kada imate veliki opseg posla
- [ ] A3: Kada imate jednostavan zadatak.

[Solution quiz](./solution/solution-quiz.md)

## Sažetak

U ovoj lekciji razmotrili smo obrazac dizajna s više agenata, uključujući scenarije u kojima su višestruki agenti primjenjivi, prednosti korištenja više agenata u odnosu na pojedinačnog agenta, gradivne blokove implementacije obrasca dizajna s više agenata te kako steći uvid u to kako više agenata međusobno djeluje.

### Imate li još pitanja o obrascu dizajna s više agenata?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kako biste se susreli s drugim polaznicima, sudjelovali na radnim satima i dobili odgovore na pitanja o AI agentima.

## Dodatni resursi

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Obrasci dizajna AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentni dizajnerski obrasci</a>


## Prethodna lekcija

[Planiranje dizajna](../07-planning-design/README.md)

## Sljedeća lekcija

[Metakognicija u AI agentima](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Odricanje odgovornosti:
Ovaj je dokument preveden pomoću AI usluge za prijevod [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo osigurati točnost, imajte na umu da automatizirani prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za važne informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakve nesporazume ili pogrešna tumačenja koja proizlaze iz korištenja ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->