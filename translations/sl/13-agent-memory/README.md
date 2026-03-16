# Pomnilnik za AI agente 
[![Pomnilnik agenta](../../../translated_images/sl/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Pri razpravi o edinstvenih prednostih ustvarjanja AI agentov se običajno omenjata dve zadevi: sposobnost klicanja orodij za izvedbo nalog in sposobnost izboljševanja skozi čas. Pomnilnik je temelj za ustvarjanje agenta, ki se lahko sam izboljšuje in lahko ustvari boljše izkušnje za naše uporabnike.

V tej lekciji bomo pogledali, kaj je pomnilnik za AI agente in kako ga lahko upravljamo ter uporabljamo v korist naših aplikacij.

## Uvod

Ta lekcija bo obravnavala:

• **Razumevanje pomnilnika AI agentov**: Kaj je pomnilnik in zakaj je pomemben za agente.

• **Implementacija in shranjevanje pomnilnika**: Praktične metode za dodajanje zmožnosti pomnilnika vašim AI agentom, s poudarkom na kratkoročnem in dolgoročnem pomnilniku.

• **Omogočanje samopopolnjevanja AI agentov**: Kako pomnilnik omogoča agentom učenje iz preteklih interakcij in izboljševanje skozi čas.

## Razpoložljive implementacije

Ta lekcija vključuje dva obsežna vodiča v zvezku:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementira pomnilnik z uporabo Mem0 in Azure AI Search z okvirjem Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementira strukturiran pomnilnik z uporabo Cognee, samodejno gradi graf znanja, podprt z embeddings, vizualizira graf in omogoča inteligentno priklicavanje

## Cilji učenja

Po zaključku te lekcije boste znali:

• **Razlikovati med različnimi vrstami pomnilnika AI agentov**, vključno z delovnim, kratkoročnim in dolgoročnim pomnilnikom, pa tudi specializiranimi oblikami, kot sta osebnostni in epizodični pomnilnik.

• **Implementirati in upravljati kratkoročni in dolgoročni pomnilnik za AI agente** z uporabo okvirja Semantic Kernel, z izkoriščanjem orodij, kot so Mem0, Cognee, Whiteboard memory, in integracijo z Azure AI Search.

• **Razumeti principe samopopolnjevanja AI agentov** in kako robustni sistemi upravljanja pomnilnika prispevajo k neprekinjenemu učenju in prilagajanju.

## Razumevanje pomnilnika AI agentov

V svoji jedru **pomnilnik za AI agente označuje mehanizme, ki jim omogočajo, da hranijo in prikličejo informacije**. Te informacije so lahko specifični podatki o pogovoru, uporabniške preference, pretekla dejanja ali celo naučeni vzorci.

Brez pomnilnika so AI aplikacije pogosto brezstanjne, kar pomeni, da vsaka interakcija začne znova. To vodi v ponavljajočo se in frustrirajočo uporabniško izkušnjo, kjer agent "pozabi" prejšnji kontekst ali preference.

### Zakaj je pomnilnik pomemben?

Inteligenca agenta je tesno povezana z njegovo sposobnostjo priklica in uporabe preteklih informacij. Pomnilnik omogoča, da so agenti:

• **Refleksivni**: Učenje iz preteklih dejanj in izidov.

• **Interaktivni**: Ohranjanje konteksta med tekočim pogovorom.

• **Proaktivni in odzivni**: Predvidevanje potreb ali ustrezno odzivanje na podlagi zgodovinskih podatkov.

• **Avtonomni**: Delovanje bolj samostojno z izkoriščanjem shranjenega znanja.

Cilj implementacije pomnilnika je narediti agente bolj **zanesljive in sposobne**.

### Vrste pomnilnika

#### Delovni pomnilnik

To lahko razumete kot list papirja, ki ga agent uporablja med eno tekočo nalogo ali miselnim procesom. Vsebuje neposredne informacije, potrebne za izračun naslednjega koraka.

Za AI agente delovni pomnilnik pogosto zajame najbolj pomembne informacije iz pogovora, tudi če je celotna zgodovina klepeta dolga ali skrajšana. Osredotoča se na izvleček ključnih elementov, kot so zahteve, predlogi, odločitve in dejanja.

**Primer delovnega pomnilnika**

V agentu za rezervacijo potovanj lahko delovni pomnilnik zajame trenutno zahtevo uporabnika, na primer "Želim rezervirati potovanje v Pariz". Ta specifična zahteva je shranjena v trenutnem kontekstu agenta, da vodi trenutno interakcijo.

#### Kratkoročni pomnilnik

Ta tip pomnilnika ohranja informacije za trajanje enega pogovora ali seje. Je kontekst trenutnega klepeta, ki agentu omogoča, da se sklicuje na prejšnje poteze v dialogu.

**Primer kratkoročnega pomnilnika**

Če uporabnik vpraša: "Koliko bi stal let v Pariz?" in nato doda "Kaj pa nastanitev tam?", kratkoročni pomnilnik zagotovi, da agent ve, da "tam" znotraj istega pogovora pomeni "Pariz".

#### Dolgoročni pomnilnik

To so informacije, ki trajajo čez več pogovorov ali sej. Agentom omogoča, da si zapomnijo uporabniške preference, zgodovinske interakcije ali splošno znanje skozi daljša obdobja. To je pomembno za personalizacijo.

**Primer dolgoročnega pomnilnika**

Dolgoročni pomnilnik lahko shrani, da "Ben uživa v smučanju in zunanjih aktivnostih, ima rad kavo z razgledom na gore in se želi izogibati zahtevnim smučarskim progama zaradi pretekle poškodbe". Te informacije, pridobljene iz prejšnjih interakcij, vplivajo na priporočila v prihodnjih načrtih potovanj in jih naredijo zelo personalizirane.

#### Osebnostni pomnilnik

Ta specializirana vrsta pomnilnika pomaga agentu razviti dosledno "osebnost" ali "persono". Agentu omogoča, da si zapomni podrobnosti o sebi ali svoji predvideni vlogi, kar naredi interakcije bolj tekoče in osredotočene.

**Primer osebnostnega pomnilnika**
Če je potovalni agent zasnovan kot "strokovnjak za smučanje", lahko osebnostni pomnilnik utrdi to vlogo in vpliva na njegove odgovore, da se ujemajo s tonom in znanjem strokovnjaka.

#### Pomnilnik delovnega toka/epizodični pomnilnik

Ta pomnilnik hrani zaporedje korakov, ki jih je agent sprejel med kompleksno nalogo, vključno s uspehi in napakami. Je kot spomin na specifične "epizode" ali pretekle izkušnje, iz katerih se lahko uči.

**Primer epizodičnega pomnilnika**

Če je agent poskušal rezervirati določen let, vendar je to spodletelo zaradi nedosegljivosti, lahko epizodični pomnilnik zabeleži ta neuspeh, kar agentu omogoči, da poskusi z alternativnimi leti ali uporabnika obvesti o težavi bolj informirano pri naslednjem poskusu.

#### Pomnilnik entitet

To vključuje izvlečenje in zapomnitev specifičnih entitet (kot so osebe, kraji ali stvari) in dogodkov iz pogovorov. Agentu omogoča, da zgradi strukturirano razumevanje ključnih elementov, o katerih je bilo govora.

**Primer pomnilnika entitet**

Iz pogovora o preteklem potovanju lahko agent izlušči "Pariz", "Eifflov stolp" in "večerjo v restavraciji Le Chat Noir" kot entitete. Pri prihodnji interakciji bi se agent lahko spomnil "Le Chat Noir" in ponudil, da tam rezervira novo mizo.

#### Strukturiran RAG (Retrieval Augmented Generation)

Medtem ko je RAG širša tehnika, je "Strukturiran RAG" poudarjen kot zmogljiva tehnologija pomnilnika. Izvleče goste, strukturirane informacije iz različnih virov (pogovori, e-pošta, slike) in jih uporablja za izboljšanje natančnosti, priklica in hitrosti v odzivih. V nasprotju s klasičnim RAG, ki se opira izključno na semantično podobnost, Strukturiran RAG deluje z inherentno strukturo informacij.

**Primer strukturiranega RAG**

Namesto da bi le ujemal ključne besede, bi Strukturiran RAG lahko razčlenil podrobnosti leta (destinacija, datum, ura, letalska družba) iz e-pošte in jih shranil na strukturiran način. To omogoča natančna poizvedovanja, kot je "Kateri let sem rezerviral v Pariz v torek?"

## Implementacija in shranjevanje pomnilnika

Implementacija pomnilnika za AI agente vključuje sistematičen proces upravljanja pomnilnika, ki zajema ustvarjanje, shranjevanje, pridobivanje, integracijo, posodabljanje in celo "pozabljanje" (ali brisanje) informacij. Pridobivanje je še posebej ključno.

### Specializirana orodja za pomnilnik

#### Mem0

Eden od načinov za shranjevanje in upravljanje pomnilnika agenta je uporaba specializiranih orodij, kot je Mem0. Mem0 deluje kot trajna plast pomnilnika, kar agentom omogoča priklic relevantnih interakcij, shranjevanje uporabniških preferenc in faktografskega konteksta ter učenje iz uspehov in neuspehov skozi čas. Ideja je, da se brezstanjni agenti spremenijo v stanovanjske.

Deluje preko **dvostopenjskega pomnilniškega kanala: ekstrakcija in posodobitev**. Najprej se sporočila, dodana v nit agenta, pošljejo storitvi Mem0, ki uporablja velik jezikovni model (LLM) za povzemanje zgodovine pogovorov in izvleček novih spominov. Nato faza posodobitve, ki jo vodi LLM, določi, ali dodati, spremeniti ali izbrisati te spomine ter jih shrani v hibridno podatkovno skladišče, ki lahko vključuje vektorsko, grafično in ključ-vrednost bazo podatkov. Ta sistem podpira tudi različne tipe pomnilnika in lahko vključuje grafični pomnilnik za upravljanje odnosov med entitetami.

#### Cognee

Drugi zmogljiv pristop je uporaba **Cognee**, odprtokodnega semantičnega pomnilnika za AI agente, ki transformira strukturirane in nestrukturirane podatke v poizvedljiv graf znanja, podprt z embeddings. Cognee zagotavlja **dvoskladiščno arhitekturo**, ki združuje vektorsko iskanje po podobnosti z grafičnimi odnosi, kar agentom omogoča razumevanje ne le katere informacije so podobne, temveč kako so koncepti povezani.

Izstopa pri **hibridnem priklicu**, ki združuje vektorsko podobnost, grafično strukturo in razmišljanje LLM - od neposrednega iskanja kosov do vprašanj, ki zavedajo grafa. Sistem vzdržuje **živi pomnilnik**, ki se razvija in raste ter ostaja poizvedljiv kot en povezan graf, podpira tako kratkoročni kontekst seje kot dolgoročni trajni pomnilnik.

Vodič v zvezku Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) prikazuje gradnjo te združene plasti pomnilnika, z praktičnimi primeri vnosa različnih virov podatkov, vizualizacijo grafa znanja in poizvedovanjem z različnimi strategijami iskanja, prilagojenimi specifičnim potrebam agenta.

### Shranjevanje pomnilnika z RAG

Poleg specializiranih orodij za pomnilnik, kot je mem0, lahko za shranjevanje in priklic spominov izkoristite robustne iskalne storitve, kot je **Azure AI Search**, zlasti za strukturiran RAG.

To vam omogoča, da zasidrate odgovore agenta v lastnih podatkih in s tem zagotovite bolj relevantne in natančne odgovore. Azure AI Search se lahko uporablja za shranjevanje uporabniško specifičnih spominov o potovanjih, katalogov izdelkov ali katerokoli drugo domeno specifičnega znanja.

Azure AI Search podpira zmogljivosti, kot je **Strukturiran RAG**, ki uspeva pri izvleku in priklicu gostih, strukturiranih informacij iz velikih podatkovnih nizov, kot so zgodovine pogovorov, e-pošta ali celo slike. To zagotavlja "nadčloveško natančnost in priklic" v primerjavi s tradicionalnim razbijanjem besedila na kose in vdelavami.

## Omogočanje samopopolnjevanja AI agentov

Pogosta shema za samopopolnjujoče agente vključuje uvajanje "agenta za znanje". Ta ločeni agent opazuje glavni pogovor med uporabnikom in primarnim agentom. Njegova vloga je:

1. **Prepoznati dragocene informacije**: Določiti, ali je kateri koli del pogovora vreden shranitve kot splošno znanje ali specifična uporabniška preferenca.

2. **Izvleči in povzeti**: Destilirati bistveno učno vsebino ali preference iz pogovora.

3. **Shranjevati v podatkovno bazo znanja**: Ohranjati te izvlečene informacije, pogosto v vektorski bazi podatkov, da jih je mogoče kasneje priklicati.

4. **Ojačati prihodnje poizvedbe**: Ko uporabnik začne novo poizvedbo, agent za znanje prikliče relevantne shranjene informacije in jih priloži uporabnikovemu pozivu, kar primarnemu agentu zagotovi ključen kontekst (podobno kot RAG).

### Optimizacije za pomnilnik

• **Upravljanje latence**: Da se izognemo upočasnitvi uporabniških interakcij, se lahko sprva uporabi cenejši, hitrejši model za hitro preverjanje, ali je informacija vredna shranjevanja ali priklica, in šele po potrebi sproži bolj zapleten proces ekstrakcije/priklica.

• **Vzdrževanje baze znanja**: Za rastočo bazo znanja se manj pogosto uporabljene informacije lahko premaknejo v "hladno skladišče" za obvladovanje stroškov.

## Imate več vprašanj o pomnilniku agentov?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), srečajte se z drugimi učenci, udeležite se ur za vprašanja in dobite odgovore na svoja vprašanja o AI agentih.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Izjava o omejitvi odgovornosti**:
Dokument je bil preveden s pomočjo storitve za prevajanje z umetno inteligenco [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da lahko avtomatizirani prevodi vsebujejo napake ali netočnosti. Izvirni dokument v njegovem izvorni jeziku velja za avtoritativni vir. Za kritične informacije priporočamo strokovni človeški prevod. Ne odgovarjamo za morebitne nesporazume ali napačne razlage, ki izhajajo iz uporabe tega prevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->