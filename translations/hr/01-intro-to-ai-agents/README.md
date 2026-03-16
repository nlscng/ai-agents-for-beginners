[![Uvod u AI agente](../../../translated_images/hr/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Kliknite na gornju sliku da pogledate video ovog sata)_


# Uvod u AI agente i primjenu agenata

Dobrodošli na tečaj "AI agenti za početnike"! Ovaj tečaj pruža osnovno znanje i primjere primjene za izradu AI agenata.

Pridružite se <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord zajednici</a> kako biste upoznali druge učenike i tvorce AI agenata te postavljali sva pitanja o ovom tečaju.

Za početak ovog tečaja, započinjemo s boljim razumijevanjem što su AI agenti i kako ih možemo koristiti u aplikacijama i radnim tokovima koje izrađujemo.

## Uvod

Ovaj sat obuhvaća:

- Što su AI agenti i koje su različite vrste agenata?
- Koji su najbolji slučajevi uporabe AI agenata i kako nam oni mogu pomoći?
- Koji su neki osnovni gradivni blokovi pri dizajniranju agentnih rješenja?

## Ciljevi učenja
Nakon dovršetka ovog sata, trebali biste moći:

- Razumjeti koncepte AI agenata i kako se razlikuju od drugih AI rješenja.
- Najučinkovitije primijeniti AI agente.
- Produktivno dizajnirati agentna rješenja za korisnike i klijente.

## Definiranje AI agenata i vrste AI agenata

### Što su AI agenti?

AI agenti su **sustavi** koji omogućuju **velikim jezičnim modelima (LLM-ovima)** da **izvršavaju radnje** proširujući njihove mogućnosti dajući LLM-ovima **pristup alatima** i **znanju**.

Razbijmo ovu definiciju na manje dijelove:

- **Sustav** - Važno je razmišljati o agentima ne samo kao o jednoj komponenti, već kao o sustavu mnogih komponenti. Na osnovnoj razini, komponente AI agenta su:
  - **Okolina** - Definirani prostor u kojem AI agent djeluje. Na primjer, ako imamo AI agenta za rezervaciju putovanja, okolina može biti sustav za rezervaciju putovanja koji AI agent koristi za dovršavanje zadataka.
  - **Senzori** - Okoline imaju informacije i pružaju povratne informacije. AI agenti koriste senzore za prikupljanje i tumačenje tih informacija o trenutačnom stanju okoline. U primjeru Agenta za rezervaciju putovanja, sustav za rezervaciju može pružiti informacije poput dostupnosti hotela ili cijena letova.
  - **Aktuatori** - Nakon što AI agent primi trenutačno stanje okoline, za trenutačni zadatak agent određuje koju radnju treba poduzeti kako bi promijenio okolinu. Za agenta za rezervaciju putovanja, to može biti rezervacija dostupne sobe za korisnika.

![Što su AI agenti?](../../../translated_images/hr/what-are-ai-agents.1ec8c4d548af601a.webp)

**Veliki jezični modeli** - Koncept agenata postojao je prije stvaranja LLM-ova. Prednost izrade AI agenata s LLM-ovima je njihova sposobnost interpretacije ljudskog jezika i podataka. Ta sposobnost omogućuje LLM-ovima interpretaciju informacija o okolini i definiranje plana za promjenu okoline.

**Izvršavanje radnji** - Izvan sustava AI agenata, LLM-ovi su ograničeni na situacije u kojima je radnja generiranje sadržaja ili informacija na temelju korisničkog upita. Unutar sustava AI agenata, LLM-ovi mogu izvršavati zadatke tumačeći korisnički zahtjev i koristeći alate dostupne u njihovoj okolini.

**Pristup alatima** - Koji alati su dostupni LLM-u definira 1) okolina u kojoj djeluje i 2) programer AI agenta. Za naš primjer agent za putovanja, alati agenta su ograničeni operacijama dostupnima u sustavu rezervacija, i/ili programer može ograničiti pristup alatu agenta samo na letove.

**Memorija+Znanje** - Memorija može biti kratkoročna u kontekstu razgovora između korisnika i agenta. Dugoročno, osim informacija koje pruža okolina, AI agenti mogu dohvatiti i znanje iz drugih sustava, servisa, alata pa čak i drugih agenata. U primjeru agenta za putovanja, to znanje može biti informacija o korisnikovim preferencijama putovanja pohranjena u bazi podataka klijenata.

### Različite vrste agenata

Sada kada imamo opću definiciju AI agenata, pogledajmo neke specifične vrste agenata i kako bi se primijenili na AI agenta za rezervaciju putovanja.

| **Vrsta agenta**             | **Opis**                                                                                                                           | **Primjer**                                                                                                                                                                                                                |
| -----------------------------| ---------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Jednostavni refleksni agenti** | Izvršavaju trenutne radnje na temelju unaprijed definiranih pravila.                                                             | Agent za putovanja interpretira kontekst e-pošte i prosljeđuje pritužbe o putovanju službi za korisnike.                                                                                                                   |
| **Modelom vođeni refleksni agenti** | Izvršavaju radnje na temelju modela svijeta i promjena tog modela.                                                               | Agent za putovanja daje prioritet rutama s značajnim promjenama cijena na temelju pristupa povijesnim podacima o cijenama.                                                                                                |
| **Agent s ciljem**            | Stvaraju planove za postizanje određenih ciljeva tumačeći cilj i određujući radnje za njegovo ostvarenje.                          | Agent za putovanja rezervira putovanje određujući potrebne aranžmane (automobil, javni prijevoz, letovi) s trenutačne lokacije do odredišta.                                                                              |
| **Agent s korisničkom vrijednošću** | Uzimaju u obzir preferencije i numerički uspoređuju kompromise kako bi odredili kako postići ciljeve.                               | Agent za putovanja maksimizira korisničku vrijednost balansiranjem između praktičnosti i cijene prilikom rezervacije putovanja.                                                                                            |
| **Učeći agenti**              | Poboljšavaju se tijekom vremena reagiranjem na povratne informacije i prilagođavanjem radnji.                                      | Agent za putovanja poboljšava se koristeći povratne informacije korisnika iz anketa nakon putovanja za prilagodbe u budućim rezervacijama.                                                                                |
| **Hijerarhijski agenti**      | Sastoje se od više agenata u slojevitom sustavu, pri čemu viši agenti razdvajaju zadatke u podzadatke za niže agente.             | Agent za putovanja otkazuje putovanje dijeleći zadatak na podzadatke (npr. otkazivanje pojedinačnih rezervacija) i niži agenti ih izvršavaju, izvještavajući višem agentu.                                                |
| **Sistemi s više agenata (MAS)** | Agenti dovršavaju zadatke neovisno, kooperativno ili konkurentno.                                                                | Kooperativno: Više agenata rezerviraju specifične usluge poput hotela, letova i zabave. Konkurentno: Više agenata upravljaju i natječu se za zajednički kalendar rezervacija hotela kako bi smjestili goste u hotel.       |

## Kada koristiti AI agente

U ranijem dijelu koristili smo primjer agenta za putovanja da objasnimo kako se različite vrste agenata mogu koristiti u različitim scenarijima rezervacije putovanja. Nastavit ćemo koristiti ovu aplikaciju kroz cijeli tečaj.

Pogledajmo vrste slučajeva uporabe za koje su AI agenti najbolji:

![Kada koristiti AI agente?](../../../translated_images/hr/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Problemi s otvorenim ishodom** - dopuštajući LLM-u da odredi potrebne korake za dovršetak zadatka jer se oni ne mogu uvijek hardkodirati u radni tok.
- **Višekorakni procesi** - zadaci koji zahtijevaju razinu složenosti u kojoj AI agent mora koristiti alate ili informacije kroz više koraka umjesto jednokratnog dohvaćanja.  
- **Poboljšanje tijekom vremena** - zadaci gdje se agent može poboljšati tijekom vremena primanjem povratnih informacija iz okoline ili od korisnika za pružanje bolje korisnosti.

Više o razmatranjima kod korištenja AI agenata pokriveno je u satu Izgradnja pouzdanih AI agenata.

## Osnove agentnih rješenja

### Razvoj agenata

Prvi korak u dizajniranju sustava AI agenta jest definirati alate, radnje i ponašanja. U ovom tečaju fokusiramo se na korištenje **Azure AI Agent Service** za definiranje naših agenata. Nudi značajke kao što su:

- Izbor otvorenih modela poput OpenAI, Mistral i Llama
- Korištenje licenciranih podataka kroz pružatelje poput Tripadvisor
- Korištenje standardiziranih OpenAPI 3.0 alata

### Agentni obrasci

Komunikacija s LLM-ovima odvija se putem upita (promptova). S obzirom na poluautonomnu prirodu AI agenata, nije uvijek moguće ili potrebno ručno ponovno slati upite LLM-u nakon promjene u okolini. Koristimo **agentne obrasce** koji nam omogućuju slanje upita LLM-u kroz više koraka na skalabilniji način.

Ovaj tečaj podijeljen je na neke od trenutno popularnih agentnih obrazaca.

### Agentni okviri

Agentni okviri omogućuju programerima implementaciju agentnih obrazaca putem koda. Ti okviri nude predloške, dodatke i alate za bolju suradnju AI agenata. Ove prednosti pružaju mogućnosti bolje vidljivosti i otklanjanja problema sa sustavima AI agenata.

U ovom tečaju istražit ćemo istraživački okvir AutoGen i produkcijski spreman okviri Agent iz Semantic Kernel.

## Primjeri koda

- Python: [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## Imate li još pitanja o AI agentima?

Pridružite se [Microsoft Foundry Discordu](https://aka.ms/ai-agents/discord) da upoznate druge učenike, sudjelujete u radnim satima i dobijete odgovore na pitanja o AI agentima.

## Prethodni sat

[Postavljanje tečaja](../00-course-setup/README.md)

## Sljedeći sat

[Istraživanje agentnih okvira](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Izjava o odricanju od odgovornosti**:
Ovaj dokument preveden je pomoću AI usluge za prevođenje [Co-op Translator](https://github.com/Azure/co-op-translator). Iako težimo točnosti, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za kritične informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakva nesporazuma ili pogrešna tumačenja koja proizađu iz korištenja ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->