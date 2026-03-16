# Korištenje agentnih protokola (MCP, A2A i NLWeb)

[![Agentic Protocols](../../../translated_images/hr/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Kliknite na gornju sliku za pregled videa ove lekcije)_

Kako raste korištenje AI agenata, raste i potreba za protokolima koji osiguravaju standardizaciju, sigurnost i podržavaju otvorenu inovaciju. U ovoj lekciji obradit ćemo 3 protokola koji žele zadovoljiti ovu potrebu - Model Context Protocol (MCP), Agent to Agent (A2A) i Natural Language Web (NLWeb).

## Uvod

U ovoj lekciji ćemo obrađivati:

• Kako **MCP** omogućuje AI agentima pristup vanjskim alatima i podacima za obavljanje korisničkih zadataka.

• Kako **A2A** omogućuje komunikaciju i suradnju između različitih AI agenata.

• Kako **NLWeb** donosi sučelja prirodnog jezika na bilo koju web stranicu omogućujući AI agentima da otkrivaju i komuniciraju s sadržajem.

## Ciljevi učenja

• **Prepoznati** osnovnu svrhu i prednosti MCP, A2A i NLWeb u kontekstu AI agenata.

• **Objasniti** kako svaki protokol olakšava komunikaciju i interakciju između LLM-ova, alata i drugih agenata.

• **Prepoznati** različite uloge koje svaki protokol ima u izgradnji složenih agentnih sustava.

## Model Context Protocol

**Model Context Protocol (MCP)** je otvoreni standard koji pruža standardizirani način za aplikacije da osiguraju kontekst i alate LLM-ovima. To omogućuje "univerzalni adapter" za različite izvore podataka i alate na koje se AI agenti mogu povezati na dosljedan način.

Pogledajmo komponente MCP-a, prednosti u odnosu na izravno korištenje API-ja, te primjer kako bi AI agenti mogli koristiti MCP server.

### Osnovne komponente MCP-a

MCP radi na **klijent-server arhitekturi** a osnovne komponente su:

• **Hostovi** su LLM aplikacije (na primjer uređivač koda poput VSCode) koje započinju veze prema MCP serveru.

• **Klijenti** su komponente unutar host aplikacije koje održavaju veze jedan-na-jedan sa serverima.

• **Serveri** su lagani programi koji izlažu specifične funkcionalnosti.

U protokolu su uključene tri osnovne primitivne funkcije koje su mogućnosti MCP servera:

• **Alati**: To su zasebne radnje ili funkcije koje AI agent može pozvati da izvrši neku radnju. Na primjer, vremenska služba može izložiti alat „dobavi vrijeme“, ili server e-trgovine može izložiti alat „kupi proizvod“. MCP serveri oglašavaju naziv alata, opis i ulazno/izlaznu shemu u svom popisu mogućnosti.

• **Resursi**: To su podaci samo za čitanje ili dokumenti koje MCP server može pružiti, a klijenti ih mogu dohvatiti po potrebi. Primjeri uključuju sadržaje datoteka, zapise iz baza podataka ili zapisnike. Resursi mogu biti tekstualni (kao kod ili JSON) ili binarni (kao slike ili PDF-ovi).

• **Promptovi**: To su unaprijed definirane predloške koji pružaju predložene upite, omogućujući složenije tijekove rada.

### Prednosti MCP-a

MCP nudi značajne prednosti za AI agente:

• **Dinamično otkrivanje alata**: Agenti mogu dinamički primiti popis dostupnih alata sa servera zajedno s opisima što ti alati rade. To je u kontrastu s tradicionalnim API-jima koji često zahtijevaju statično kodiranje za integracije, što znači da svaka promjena API-ja zahtijeva izmjenu koda. MCP nudi pristup "integriraj jednom", što vodi većoj prilagodljivosti.

• **Interoperabilnost između LLM-ova**: MCP radi preko različitih LLM-ova, pružajući fleksibilnost za promjenu temeljnih modela radi bolje izvedbe.

• **Standardizirana sigurnost**: MCP uključuje standardizirani način autentifikacije, što poboljšava skalabilnost kod dodavanja pristupa dodatnim MCP serverima. To je jednostavnije nego upravljanje različitim ključevima i tipovima autentifikacije za različite tradicionalne API-je.

### Primjer MCP-a

![MCP Diagram](../../../translated_images/hr/mcp-diagram.e4ca1cbd551444a1.webp)

Zamislite korisnika koji želi rezervirati let koristeći AI asistenta baziranog na MCP-u.

1. **Veza**: AI asistent (MCP klijent) se povezuje na MCP server koji pruža zrakoplovna kompanija.

2. **Otkrivanje alata**: Klijent pita MCP server zrakoplovne kompanije: „Koje alate imate dostupne?“ Server odgovara s alatima poput „traži letove“ i „rezerviraj letove“.

3. **Pozivanje alata**: Korisnik zatim traži od AI asistenta: „Molim te pretraži let od Portlanda do Honolulu-a.“ AI asistent, koristeći svoj LLM, identificira da treba pozvati alat „traži letove“ i prosljeđuje odgovarajuće parametre (polazište, odredište) MCP serveru.

4. **Izvršenje i odgovor**: MCP server, djelujući kao omotač, vrši stvarni poziv prema internom API-ju zrakoplovne kompanije. Zatim prima informacije o letu (npr. JSON podatke) i šalje ih nazad AI asistentu.

5. **Daljnja interakcija**: AI asistent prikazuje opcije leta. Kada korisnik odabere let, asistent može pozvati alat „rezerviraj let“ na istom MCP serveru, kompletirajući rezervaciju.

## Agent-to-Agent Protocol (A2A)

Dok se MCP fokusira na povezivanje LLM-ova s alatima, **Agent-to-Agent (A2A) protokol** ide korak dalje omogućujući komunikaciju i suradnju između različitih AI agenata. A2A povezuje AI agente preko različitih organizacija, okruženja i tehnoloških slojeva kako bi obavili zajednički zadatak.

Pregledat ćemo komponente i prednosti A2A, zajedno s primjerom primjene u našoj aplikaciji za putovanja.

### Osnovne komponente A2A

A2A je usmjeren na omogućavanje komunikacije između agenata i njihovo zajedničko obavljanje podzadatka korisnika. Svaka komponenta protokola doprinosi tome:

#### Agent Card

Slično kao što MCP server dijeli popis alata, Agent Card sadrži:
- Ime agenta.
- **Opis općih zadataka** koje agent izvršava.
- **Popis specifičnih vještina** s opisima koji pomažu drugim agentima (ili čak ljudskim korisnicima) razumjeti kada i zašto bi željeli pozvati tog agenta.
- **Trenutnu Endpoint URL** adresu agenta.
- **Verziju** i **mogućnosti** agenta, poput odgovora u streamingu i push obavijesti.

#### Agent Executor

Agent Executor je odgovoran za **prenošenje konteksta korisničkog chata udaljenom agentu**, koji treba te informacije da razumije zadatak koji treba izvršiti. U A2A serveru agent koristi svoj vlastiti Large Language Model (LLM) za analiziranje dolaznih zahtjeva i izvršavanje zadataka koristeći vlastite unutarnje alate.

#### Artifact

Kada udaljeni agent završi traženi zadatak, njegov je proizvod izrađen kao artefakt. Artefakt **sadrži rezultat rada agenta**, **opis onoga što je dovršeno** i **tekstualni kontekst** koji se šalje kroz protokol. Nakon slanja artefakta veza s udaljenim agentom se prekida dok nije ponovno potrebna.

#### Event Queue

Ova komponenta se koristi za **obradu ažuriranja i prijenos poruka**. Posebno je važna u produkciji agentnih sustava da se veza između agenata ne prekine prije završetka zadatka, osobito kad izvršenje zadatka može trajati dulje.

### Prednosti A2A

• **Poboljšana suradnja**: Omogućuje agentima iz različitih dobavljača i platformi da međusobno komuniciraju, dijele kontekst i surađuju, olakšavajući bešavnu automatizaciju preko tradicionalno nepovezanih sustava.

• **Fleksibilnost odabira modela**: Svaki A2A agent može odlučiti koji LLM koristi za obradu svojih zahtjeva, dopuštajući optimizirane ili fino podešene modele po agentu, za razliku od jedne LLM veze u nekim MCP scenarijima.

• **Ugrađena autentikacija**: Autentifikacija je integrirana izravno u A2A protokol, pružajući snažni sigurnosni okvir za interakcije agenata.

### Primjer A2A

![A2A Diagram](../../../translated_images/hr/A2A-Diagram.8666928d648acc26.webp)

Proširimo naš scenarij rezervacije putovanja, ali ovoga puta koristeći A2A.

1. **Korisnički zahtjev multi-agentu**: Korisnik komunicira s "Travel Agent" A2A klijentom/agentom, primjerice govoreći: "Molim rezerviraj cijelo putovanje za Honolulu sljedeći tjedan, uključujući letove, hotel i unajmljivanje auta".

2. **Orkestracija od strane Travel Agenta**: Travel Agent prima ovaj složeni zahtjev. Koristi svoj LLM za razmišljanje o zadatku i određivanje da treba komunicirati s drugim specijaliziranim agentima.

3. **Međusobna komunikacija agenata**: Travel Agent potom koristi A2A protokol da se poveže s nižim agentima, poput "Airline Agent", "Hotel Agent" i "Car Rental Agent" koje su napravile različite tvrtke.

4. **Delegirano izvršenje zadataka**: Travel Agent šalje specifične zadatke ovim specijaliziranim agentima (npr. "Pronađi letove za Honolulu", "Rezerviraj hotel", "Unajmi auto"). Svaki od tih specijaliziranih agenata, koristeći svoj vlastiti LLM i svoje alate (koji mogu biti i sami MCP serveri), izvršava svoj dio rezervacije.

5. **Konsolidirani odgovor**: Kada svi agenti izvrše svoje zadatke, Travel Agent sastavlja rezultate (detalji leta, potvrda hotela, rezervacija auta) i šalje opširan, chat-stil odgovor korisniku.

## Natural Language Web (NLWeb)

Web stranice su dugo vremena bile primarni način na koji korisnici pristupaju informacijama i podacima na internetu.

Pogledajmo različite komponente NLWeb-a, njegove prednosti i primjer kako NLWeb funkcionira na našoj aplikaciji za putovanja.

### Komponente NLWeb-a

- **NLWeb aplikacija (Core Service Code)**: Sustav koji obrađuje pitanja u prirodnom jeziku. Povezuje različite dijelove platforme za stvaranje odgovora. Možete ga zamisliti kao **motor koji pokreće značajke prirodnog jezika** na web stranici.

- **NLWeb protokol**: To je **osnovni skup pravila za interakciju prirodnim jezikom** s web stranicom. Vraća odgovore u JSON formatu (često koristeći Schema.org). Njegova svrha je stvoriti jednostavnu osnovu za "AI Web", na isti način na koji je HTML omogućio dijeljenje dokumenata online.

- **MCP server (Model Context Protocol Endpoint)**: Svaka NLWeb instalacija također radi kao **MCP server**. To znači da može **dijeliti alate (kao metodu „ask“) i podatke** s drugim AI sustavima. U praksi, to omogućuje da sadržaj i sposobnosti web stranice budu dostupni AI agentima, dopuštajući da stranica postane dio šire "agentne ekosustava".

- **Embedding modeli**: Ti modeli se koriste za **pretvaranje sadržaja web stranice u numeričke reprezentacije zvane vektori (embeddings)**. Ti vektori hvataju značenje na način koji računala mogu uspoređivati i pretraživati. Spremanjem u posebnu bazu podataka, korisnici mogu odabrati koji embedding model žele koristiti.

- **Vektorska baza podataka (mehanizam dohvaćanja)**: Ova baza podataka **spremi embeddinge sadržaja web stranica**. Kad netko postavi pitanje, NLWeb provjerava ovu bazu kako bi brzo pronašao najrelevantnije informacije. Daje brzi popis mogućih odgovora, rangiranih prema sličnosti. NLWeb radi s različitim sustavima za pohranu vektora poput Qdrant, Snowflake, Milvus, Azure AI Search i Elasticsearch.

### NLWeb na primjeru

![NLWeb](../../../translated_images/hr/nlweb-diagram.c1e2390b310e5fe4.webp)

Razmotrimo ponovno našu web stranicu za rezervaciju putovanja, ovoga puta pokretan NLWeb-om.

1. **Učitavanje podataka**: Postojeći katalog proizvoda na stranici za putovanja (npr. popisi letova, opisi hotela, ponude tura) su formatirani pomoću Schema.org ili učitani putem RSS feedova. NLWeb alati unose te strukturirane podatke, stvaraju embeddinge i spremaju ih u lokalnu ili udaljenu vektorsku bazu podataka.

2. **Upit u prirodnom jeziku (čovjek)**: Korisnik posjeti web i umjesto pregledavanja menija, upisuje u chat sučelje: „Pronađi mi hotel prijateljski prema obiteljima u Honoluluu s bazenom za sljedeći tjedan.“

3. **Obrada NLWeb-a**: NLWeb aplikacija primi ovaj upit. Šalje ga LLM-u za razumijevanje i istovremeno pretražuje svoju vektorsku bazu podataka za relevantne ponude hotela.

4. **Točni rezultati**: LLM pomaže interpretirati rezultate pretraživanja baze, identificira najbolje podudarnosti temeljem kriterija „prijateljski prema obiteljima“, „bazen“ i „Honolulu“, te zatim formira odgovor u prirodnom jeziku. Ključno, odgovor se odnosi na stvarne hotele iz kataloga web stranice, izbjegavajući izmišljene informacije.

5. **Interakcija AI agenta**: Budući da NLWeb radi kao MCP server, vanjski AI turistički agent također se može povezati na ovu NLWeb instancu web stranice. AI agent može koristiti `ask` MCP metodu za upit izravno web stranice: `ask("Ima li veganskih restorana u Honolulu području koje hotel preporučuje?")`. NLWeb će to obraditi, koristeći svoju bazu podataka o restoranima (ako je učitana) i vratiti strukturirani JSON odgovor.

### Imate li još pitanja o MCP/A2A/NLWeb?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) da upoznate druge polaznike, sudjelujete u radnim satima i dobijete odgovore na vaša pitanja o AI agentima.

## Resursi

- [MCP za početnike](https://aka.ms/mcp-for-beginners)  
- [MCP dokumentacija](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb repozitorij](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel vodiči](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Odricanje od odgovornosti**:
Ovaj je dokument preveden korištenjem AI prevoditeljskog servisa [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo postići točnost, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati službenim i autoritativnim izvorom. Za važne informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakva nesporazuma ili pogrešne interpretacije koje proizlaze iz korištenja ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->