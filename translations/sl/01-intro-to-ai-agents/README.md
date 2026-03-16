[![Uvod v AI agente](../../../translated_images/sl/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Kliknite zgornjo sliko za ogled videa te lekcije)_


# Uvod v AI agente in primere uporabe agentov

Dobrodošli na tečaj "AI Agents for Beginners"! Ta tečaj ponuja temeljna znanja in praktične primere za gradnjo AI agentov.

Pridružite se <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord skupnosti</a>, da spoznate druge učeče se in razvijalce AI agentov ter postavite vsa vprašanja v zvezi s tem tečajem.

Za začetek tečaja bomo najprej bolje razumeli, kaj so AI agenti in kako jih lahko uporabimo v aplikacijah in potekih dela, ki jih gradimo.

## Uvod

Ta lekcija zajema:

- Kaj so AI agenti in katere so različne vrste agentov?
- Za katere primere uporabe so AI agenti najbolj primerni in kako nam lahko pomagajo?
- Kateri so nekateri osnovni gradniki pri oblikovanju agentskih rešitev?

## Cilji učenja
Po zaključku te lekcije boste lahko:

- Razumeli koncepte AI agentov in kako se razlikujejo od drugih AI rešitev.
- Najbolje uporabljali AI agente.
- Produktivno oblikovali agentske rešitve za uporabnike in stranke.

## Določanje AI agentov in vrste AI agentov

### Kaj so AI agenti?

AI agenti so **sistemi**, ki omogočajo **Veliki jezikovni modeli(LLMs)**, da **izvedejo dejanja**, s tem da razširijo njihove zmogljivosti z zagotavljanjem **dostopa do orodij** in **znanja**.

Razčlenimo to definicijo na manjše dele:

- **Okolje** - Opredeljeni prostor, v katerem deluje AI agent. Na primer, če bi imeli AI agenta za rezervacije potovanj, bi bilo okolje lahko sistem za rezervacijo potovanj, ki ga agent uporablja za dokončanje nalog.
- **Senzorji** - Okolja imajo informacije in zagotavljajo povratne informacije. AI agenti uporabljajo senzorje za zbiranje in interpretacijo teh informacij o trenutnem stanju okolja. V primeru agenta za rezervacije potovanj lahko sistem za rezervacije zagotovi informacije, kot so razpoložljivost hotelov ali cene letov.
- **Aktuatorji** - Ko AI agent prejme trenutni status okolja, za trenutno nalogo agent določi, katero dejanje izvesti za spremembo okolja. Pri agentu za rezervacije potovanj je to lahko rezervacija razpoložljive sobe za uporabnika.

![Kaj so AI agenti?](../../../translated_images/sl/what-are-ai-agents.1ec8c4d548af601a.webp)

**Veliki jezikovni modeli** - Koncept agentov je obstajal že pred nastankom LLM-jev. Prednost gradnje AI agentov z LLM-ji je njihova sposobnost interpretacije človeškega jezika in podatkov. Ta sposobnost omogoča LLM-jem interpretacijo informacij iz okolja in določitev načrta za spremembo okolja.

**Izvedba dejanj** - Izven sistemov AI agentov so LLM-ji omejeni na situacije, kjer je dejanje generiranje vsebine ali informacij na podlagi uporabnikovega poziva. Znotraj sistemov AI agentov lahko LLM-ji opravljajo naloge z interpretacijo uporabnikove zahteve in uporabo orodij, ki so na voljo v njihovem okolju.

**Dostop do orodij** - Katera orodja ima LLM na voljo, določata 1) okolje, v katerem deluje, in 2) razvijalec AI agenta. V našem primeru agenta za potovanja so orodja omejena z operacijami, ki so na voljo v sistemu za rezervacije, in/ali razvijalec lahko omeji dostop agenta do orodij na le lete.

**Spomin + Znanje** - Spomin je lahko kratkoročnega značaja v kontekstu pogovora med uporabnikom in agentom. Dolgoročno, izven informacij, ki jih zagotavlja okolje, lahko AI agenti pridobivajo znanje tudi iz drugih sistemov, storitev, orodij in celo drugih agentov. V primeru agenta za potovanja bi to znanje lahko bili podatki o uporabnikovih potovalnih preferencah, shranjeni v podatkovni zbirki strank.

### Različne vrste agentov

Zdaj, ko imamo splošno definicijo AI agentov, poglejmo nekaj specifičnih vrst agentov in kako bi jih uporabili pri agentu za rezervacije potovanj.

| **Vrsta agenta**                | **Opis**                                                                                                                       | **Primer**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Preprosti refleksni agenti**      | Izvajajo takojšnja dejanja na podlagi vnaprej določenih pravil.                                                                                  | Agent za potovanja interpretira kontekst e-pošte in posreduje pritožbe glede potovanj službi za pomoč strankam.                                                                                                                          |
| **Modelno osnovani refleksni agenti** | Izvajajo dejanja na podlagi modela sveta in sprememb tega modela.                                                              | Agent za potovanja daje prednost itinerarijem z znatnimi spremembami cen na podlagi dostopa do zgodovinskih podatkov o cenah.                                                                                                             |
| **Agenti, usmerjeni na cilje**         | Ustvarjajo načrte za dosego določenih ciljev z interpretacijo cilja in določanjem dejanj, ki vodijo do njega.                                  | Agent za potovanja rezervira potovanje tako, da določi potrebne prevozne uredbe (avto, javni prevoz, leti) od trenutne lokacije do cilja.                                                                                |
| **Agenti, usmerjeni k uporabnosti**      | Upoštevajo preference in numerično tehtajo kompromise, da določijo, kako doseči cilje.                                               | Agent za potovanja maksimizira uporabnost z tehtanjem priročnosti proti stroškom pri rezervaciji potovanja.                                                                                                                                          |
| **Učeči se agenti**           | S časom izboljšujejo svoje delovanje z odzivanjem na povratne informacije in ustreznim prilagajanjem dejanj.                                                        | Agent za potovanja se izboljšuje z uporabo povratnih informacij strank iz anket po potovanju za prilagoditve prihodnjih rezervacij.                                                                                                               |
| **Hierarhični agenti**       | Vključujejo več agentov v složeni sistem, pri čemer višje ravni agenti razdelijo naloge na podnaloge, ki jih dokončajo agenti nižjih ravni. | Agent za potovanja prekliče pot z razdelitvijo naloge na podnaloge (na primer preklic posameznih rezervacij) in dodelitvijo izvedbe agentom nižjih ravni, ki poročajo višjemu agentu.                                     |
| **Sistemi več agentov (MAS)** | Agenti opravljajo naloge neodvisno, bodisi sodelovalno ali tekmovalno.                                                           | Sodelovalno: več agentov rezervira posamezne storitve potovanja, kot so hoteli, leti in zabava. Tekmovalno: več agentov upravlja in tekmuje za skupni koledar rezervacij hotelov, da rezervirajo goste v hotel. |

## Kdaj uporabljati AI agente

V prejšnjem razdelku smo uporabili primer agenta za potovanja, da pojasnimo, kako se različne vrste agentov lahko uporabijo v različnih scenarijih rezervacij potovanj. Ta aplikacija nas bo spremljala skozi celoten tečaj.

Poglejmo vrste primerov uporabe, za katere so AI agenti najbolj primerni:

![Kdaj uporabljati AI agente?](../../../translated_images/sl/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Odprte naloge** - omogočanje, da LLM določi potrebne korake za dokončanje naloge, saj jih ni vedno mogoče vnaprej kodirati v potek dela.
- **Večstopenjski postopki** - naloge, ki zahtevajo stopnjo kompleksnosti, pri kateri mora AI agent uporabljati orodja ali informacije skozi več korakov namesto enkratnega pridobivanja.  
- **Izboljševanje skozi čas** - naloge, pri katerih se agent lahko sčasoma izboljša z zbiranjem povratnih informacij iz okolja ali od uporabnikov, da zagotovi boljšo uporabnost.

Več premislekov o uporabi AI agentov obravnavamo v lekciji Gradnja zaupanja vrednih AI agentov.

## Osnove agentnih rešitev

### Razvoj agentov

Prvi korak pri načrtovanju sistema AI agenta je določitev orodij, dejanj in vedenj. V tem tečaju se osredotočamo na uporabo **Azure AI Agent Service** za opredelitev naših agentov. Ponuja funkcije, kot so:

- Izbor odprtih modelov, kot so OpenAI, Mistral in Llama
- Uporaba licenciranih podatkov prek ponudnikov, kot je Tripadvisor
- Uporaba standardiziranih orodij OpenAPI 3.0

### Agentni vzorci

Komunikacija z LLM-ji poteka prek pozivov (prompts). Glede na polavtonomno naravo AI agentov ni vedno mogoče ali potrebno ročno znova spodbuditi LLM po spremembi v okolju. Uporabljamo **agentske vzorce**, ki nam omogočajo, da LLM spodbudimo skozi več korakov na bolj razširljiv način.

Ta tečaj je razdeljen na nekatere trenutno priljubljene agentske vzorce.

### Agentni okviri

Agentni okvirji razvijalcem omogočajo implementacijo agentskih vzorcev prek kode. Ti okviri ponujajo predloge, vtičnike in orodja za boljše sodelovanje AI agentov. Te prednosti nudijo boljšo opaznost in odpravljanje težav v sistemih AI agentov.

V tem tečaju bomo raziskali raziskovalno usmerjen okvir AutoGen in proizvodno pripravljen Agent framework iz Semantic Kernel.

## Primeri kode

- Python: [Agentni okvir](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agentni okvir](./code_samples/01-dotnet-agent-framework.md)

## Imate še vprašanja o AI agentih?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), da spoznate druge učeče se, se udeležite uradnih ur in dobite odgovore na vprašanja o AI agentih.

## Predhodna lekcija

[Nastavitev tečaja](../00-course-setup/README.md)

## Naslednja lekcija

[Raziskovanje agentnih okvirjev](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Izjava o omejitvi odgovornosti:
Ta dokument je bil preveden z uporabo storitve za prevajanje z umetno inteligenco [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da lahko avtomatski prevodi vsebujejo napake ali netočnosti. Izvirni dokument v izvirnem jeziku velja za avtoritativni vir. Za kritične informacije priporočamo strokoven človeški prevod. Ne prevzemamo odgovornosti za kakršnekoli nesporazume ali napačne interpretacije, ki izhajajo iz uporabe tega prevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->