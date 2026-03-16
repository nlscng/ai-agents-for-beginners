[![Multi-agentni oblikovni vzorci](../../../translated_images/sl/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Kliknite zgornjo sliko za ogled videa te lekcije)_

# Vzorci oblikovanja za večagentne sisteme

Ko začnete delati na projektu, ki vključuje več agentov, morate upoštevati vzorec oblikovanja za večagentne sisteme. Vendar pa morda ni takoj jasno, kdaj preiti na več agentov in kakšne so prednosti.

## Uvod

V tej lekciji želimo odgovoriti na naslednja vprašanja:

- Kateri so scenariji, kjer je uporaba več agentov smiselna?
- Kakšne so prednosti uporabe več agentov v primerjavi z enim samim agentom, ki opravlja več nalog?
- Kateri so gradniki za implementacijo vzorca oblikovanja za večagentne sisteme?
- Kako vidimo, kako medsebojno sodelujejo več agentov?

## Cilji učenja

Po tej lekciji boste lahko:

- Prepoznali scenarije, kjer je uporaba več agentov smiselna
- Prepoznali prednosti uporabe več agentov v primerjavi z enim samim agentom
- Razumeli gradnike za implementacijo vzorca oblikovanja za večagentne sisteme

Kakšna je širša slika?

*Več agentov je vzorec oblikovanja, ki omogoča sodelovanje več agentov za dosego skupnega cilja*.

Ta vzorec se široko uporablja na različnih področjih, vključno z robotiko, avtonomnimi sistemi in distribuiranim računalništvom.

## Scenariji, kjer je uporaba več agentov smiselna

Kateri scenariji so torej dober primer za uporabo več agentov? Odgovor je, da obstaja veliko scenarijev, kjer je uporaba več agentov koristna, še posebej v naslednjih primerih:

- **Velika delovna obremenitev**: Velike delovne obremenitve se lahko razdelijo na manjše naloge in dodelijo različnim agentom, kar omogoča vzporedno obdelavo in hitrejše dokončanje. Primer tega je obdelava velikih podatkov.
- **Zapletene naloge**: Zapletene naloge, podobno kot velike delovne obremenitve, je mogoče razdeliti na manjše podnaloge in dodeliti različnim agentom, ki se specializirajo za določen vidik naloge. Dober primer tega so avtonomna vozila, kjer različni agenti upravljajo navigacijo, zaznavanje ovir in komunikacijo z drugimi vozili.
- **Raznolike strokovne kompetence**: Različni agenti imajo lahko raznolike strokovne kompetence, kar jim omogoča učinkovitejše upravljanje različnih vidikov naloge kot en sam agent. Dober primer tega je zdravstvena oskrba, kjer lahko agenti upravljajo diagnostiko, načrte zdravljenja in spremljanje pacientov.

## Prednosti uporabe več agentov v primerjavi z enim samim agentom

Sistem z enim samim agentom bi lahko dobro deloval za enostavne naloge, vendar pa lahko uporaba več agentov pri bolj zapletenih nalogah prinese številne prednosti:

- **Specializacija**: Vsak agent se lahko specializira za določeno nalogo. Pomanjkanje specializacije v enem agentu pomeni, da imate agenta, ki zna vse, vendar se lahko zmede, kaj narediti pri zapleteni nalogi. Na primer, lahko se zgodi, da agent opravi nalogo, za katero ni najbolje usposobljen.
- **Razširljivost**: Lažje je razširiti sistem z dodajanjem novih agentov kot pa preobremenjevati en sam agent.
- **Odpornost na napake**: Če eden od agentov odpove, lahko drugi še vedno delujejo, kar zagotavlja zanesljivost sistema.

Vzemimo primer: rezervacija potovanja za uporabnika. Sistem z enim agentom bi moral upravljati vse vidike rezervacije potovanja, od iskanja letov do rezervacije hotelov in najema avtomobilov. Za dosego tega z enim agentom bi morali imeti orodja za vse te naloge. To bi lahko vodilo do zapletenega in monolitnega sistema, ki je težaven za vzdrževanje in razširjanje. Sistem z več agenti pa lahko vključuje različne agente, specializirane za iskanje letov, rezervacijo hotelov in najem avtomobilov. Tako je sistem bolj modularen, lažji za vzdrževanje in razširljiv.

Primerjajmo to z manjšo potovalno agencijo (mama in oče) v primerjavi s potovalno agencijo kot franšizo. Mama in oče bi imela enega samega agenta, ki skrbi za vse vidike rezervacije, medtem ko bi franšiza imela različne agente za različne vidike rezervacije.

## Gradniki za implementacijo vzorca oblikovanja za večagentne sisteme

Preden lahko implementirate vzorec oblikovanja za večagentne sisteme, morate razumeti gradnike, ki sestavljajo ta vzorec.

Naredimo to bolj konkretno z zgledom rezervacije potovanja za uporabnika. V tem primeru gradniki vključujejo:

- **Komunikacija med agenti**: Agenti za iskanje letov, rezervacijo hotelov in najem avtomobilov morajo komunicirati in deliti informacije o uporabnikovih željah in omejitvah. Potrebno je odločiti o protokolih in metodah za to komunikacijo. Konkretno to pomeni, da agent za iskanje letov komunicira z agentom za rezervacijo hotelov, da se zagotovi, da je hotel rezerviran za iste datume kot let. To pomeni, da morajo agenti deliti informacije o uporabnikovih datumih potovanja, kar pomeni, da morate določiti *kateri agenti delijo informacije in kako jih delijo*.
- **Mehanizmi usklajevanja**: Agenti morajo usklajevati svoja dejanja, da zagotovijo izpolnitev uporabnikovih želja in omejitev. Uporabnikova želja je lahko na primer hotel blizu letališča, medtem ko je omejitev, da so avtomobili za najem na voljo samo na letališču. To pomeni, da mora agent za rezervacijo hotelov usklajevati svoja dejanja z agentom za najem avtomobilov, da se zagotovi izpolnitev uporabnikovih želja in omejitev. To pomeni, da morate določiti *kako agenti usklajujejo svoja dejanja*.
- **Arhitektura agentov**: Agenti morajo imeti notranjo strukturo za sprejemanje odločitev in učenje iz interakcij z uporabnikom. To pomeni, da mora agent za iskanje letov imeti notranjo strukturo za odločanje, katere lete priporočiti uporabniku. To pomeni, da morate določiti *kako agenti sprejemajo odločitve in se učijo iz interakcij z uporabnikom*. Primeri učenja in izboljševanja agenta so, da agent za iskanje letov lahko uporablja strojno učenje za priporočanje letov glede na pretekle želje uporabnika.
- **Preglednost večagentnih interakcij**: Potrebno je zagotoviti preglednost, kako medsebojno sodelujejo različni agenti. To pomeni, da potrebujete orodja in tehnike za sledenje aktivnostim in interakcijam agentov. To so lahko orodja za beleženje in spremljanje, vizualizacijska orodja in merila uspešnosti.
- **Vzorci za večagentne sisteme**: Obstajajo različni vzorci za implementacijo večagentnih sistemov, kot so centralizirana, decentralizirana in hibridna arhitektura. Potrebno je izbrati vzorec, ki najbolj ustreza vašemu primeru uporabe.
- **Človek v zanki**: V večini primerov bo v zanki prisoten človek, zato morate agentom določiti, kdaj prositi za človeško intervencijo. To je lahko, ko uporabnik zahteva določen hotel ali let, ki ga agenti niso priporočili, ali ko je potrebna potrdita pred rezervacijo leta ali hotela.

## Preglednost večagentnih interakcij

Pomembno je, da imate preglednost, kako medsebojno sodelujejo različni agenti. Ta preglednost je ključna za odpravljanje napak, optimizacijo in zagotavljanje učinkovitosti sistema kot celote. Za dosego tega potrebujete orodja in tehnike za sledenje aktivnostim in interakcijam agentov. To je lahko v obliki orodij za beleženje in spremljanje, vizualizacije in meril uspešnosti.

Na primer, pri rezervaciji potovanja za uporabnika bi lahko imeli nadzorno ploščo, ki prikazuje stanje posameznega agenta, uporabnikove želje in omejitve ter interakcije med agenti. Ta nadzorna plošča bi lahko prikazovala datume potovanja uporabnika, lete, ki jih priporoča agent za lete, hotele, ki jih priporoča agent za hotele, in avtomobile za najem, ki jih priporoča agent za najem avtomobilov. Tako bi imeli jasen pregled nad medsebojnim delovanjem agentov in ali so uporabnikove želje in omejitve upoštevane.

Poglejmo te vidike podrobneje.

- **Orodja za beleženje in spremljanje**: Želite imeti beleženje za vsako dejanje, ki ga opravi agent. Zapisi v dnevniku lahko vsebujejo informacije o agentu, ki je izvedel dejanje, opravljenem dejanju, času izvajanja in izidu. Te informacije se uporabljajo za odpravljanje napak, optimizacijo in drugo.
- **Vizualizacijska orodja**: Vizualizacijska orodja pomagajo videti interakcije med agenti na bolj intuitiven način. Na primer, lahko imate graf, ki prikazuje pretok informacij med agenti. To lahko pomaga pri identifikaciji ozkih grl, neučinkovitosti in drugih težav v sistemu.
- **Merila uspešnosti**: Merila uspešnosti pomagajo spremljati učinkovitost večagentnega sistema. Na primer, lahko spremljate čas, potreben za izvedbo naloge, število opravljenih nalog na časovno enoto in točnost priporočil, ki jih agenti podajajo. Te informacije vam pomagajo odkriti področja za izboljšave in optimizirati sistem.

## Vzorci za večagentne sisteme

Oglejmo si nekaj konkretnih vzorcev, ki jih lahko uporabimo za ustvarjanje večagentnih aplikacij. Tukaj je nekaj zanimivih vzorcev, ki jih je vredno upoštevati:

### Skupinski klepet

Ta vzorec je uporaben, ko želite ustvariti aplikacijo za skupinski klepet, kjer lahko več agentov komunicira med seboj. Tipični primeri uporabe so timsko sodelovanje, podpora strankam in družbena omrežja.

V tem vzorcu vsak agent predstavlja uporabnika v skupinskem klepetu, sporočila pa se izmenjujejo med agenti prek protokola za sporočila. Agenti lahko pošiljajo sporočila skupinskemu klepetu, prejemajo sporočila iz klepeta in odgovarjajo na sporočila drugih agentov.

Ta vzorec se lahko implementira z centralizirano arhitekturo, kjer se vsa sporočila usmerjajo prek centralnega strežnika, ali decentralizirano arhitekturo, kjer se sporočila izmenjujejo neposredno.

![Skupinski klepet](../../../translated_images/sl/multi-agent-group-chat.ec10f4cde556babd.webp)

### Predaja nalog

Ta vzorec je uporaben, ko želite ustvariti aplikacijo, kjer lahko več agentov izmenjuje naloge med seboj.

Tipični primeri uporabe vključujejo podporo strankam, upravljanje nalog in avtomatizacijo potekov dela.

V tem vzorcu vsak agent predstavlja nalogo ali korak v poteku dela, agenti pa naloge posredujejo drugim agentom na podlagi vnaprej določenih pravil.

![Predaja nalog](../../../translated_images/sl/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Sodelovalno filtriranje

Ta vzorec je uporaben, ko želite ustvariti aplikacijo, kjer lahko več agentov sodeluje pri dajanju priporočil uporabnikom.

Zakaj bi želeli, da sodeluje več agentov? Ker lahko vsak agent ima različne strokovne kompetence in prispeva k procesu priporočanja na različne načine.

Vzemimo primer, ko uporabnik želi priporočilo o najboljšem delnicah za nakup na borzi.

- **Strokovnjak za industrijo**: En agent je lahko strokovnjak za določeno industrijo.
- **Tehnična analiza**: Drug agent je lahko strokovnjak za tehnično analizo.
- **Temeljna analiza**: Tretji agent je lahko strokovnjak za temeljno analizo. S sodelovanjem lahko ti agenti zagotovijo bolj celovito priporočilo uporabniku.

![Priporočilo](../../../translated_images/sl/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenarij: Postopek vračila

Predstavljajte si scenarij, kjer kupec želi dobiti vračilo za izdelek. Ta proces lahko zajema več agentov, vendar jih bomo razdelili na agente, specifične za ta proces, in splošne agente, ki se lahko uporabljajo tudi v drugih procesih.

**Agenti specifični za postopek vračila**:

Naslednji agenti bi lahko sodelovali v postopku vračila:

- **Agent za stranke**: Predstavlja kupca in je odgovoren za začetek postopka vračila.
- **Agent prodajalca**: Predstavlja prodajalca in je odgovoren za obdelavo vračila.
- **Agent za plačila**: Predstavlja plačilni proces in skrbi za vračilo plačila kupcu.
- **Agent za reševanje**: Predstavlja proces reševanja težav in je odgovoren za reševanje morebitnih težav med postopkom vračila.
- **Agent za skladnost**: Predstavlja proces skladnosti in zagotavlja, da potek vračila ustreza predpisom in pravilnikom.

**Splošni agenti**:

Ti agenti se lahko uporabljajo v drugih delih vašega poslovanja.

- **Agent za dostavo**: Predstavlja proces dostave in je odgovoren za vračilo izdelka prodajalcu. Ta agent se lahko uporablja tako za postopek vračila kot za splošno dostavo izdelkov, na primer ob nakupu.
- **Agent za povratne informacije**: Predstavlja proces zbiranja povratnih informacij od strank. Povratne informacije lahko zbirate kadarkoli, ne le med postopkom vračila.
- **Agent za eskalacijo**: Predstavlja proces eskalacije in skrbi za prenos težav na višjo podporno raven. Ta vrsta agenta se lahko uporablja za vsak proces, kjer je potrebna eskalacija problema.
- **Agent za obveščanje**: Predstavlja proces obveščanja in je odgovoren za pošiljanje obvestil kupcu v različnih fazah postopka vračila.
- **Agent za analizo**: Predstavlja proces analize in je odgovoren za analizo podatkov, povezanih s postopkom vračila.
- **Agent za revizijo**: Predstavlja proces revizije in zagotavlja, da je postopek vračila pravilno izveden.
- **Agent za poročanje**: Predstavlja proces poročanja in je odgovoren za pripravo poročil o postopku vračila.
- **Agent za znanje**: Predstavlja proces upravljanja znanja in vzdržuje bazo znanja o postopku vračila. Ta agent ima lahko znanje tako o vračilih kot o drugih poslovnih področjih.
- **Agent za varnost**: Predstavlja proces varnosti in zagotavlja varnost postopka vračila.
- **Agent za kakovost**: Predstavlja proces zagotavljanja kakovosti in skrbi za kakovost postopka vračila.

Naštetih je kar nekaj agentov, tako specifičnih za postopek vračila kot tudi splošnih agentov, ki jih lahko uporabite v drugih delih vašega poslovanja. Upamo, da vam to daje idejo, kako se odločiti, katere agente uporabiti v vašem večagentnem sistemu.

## Naloga

Oblikujte večagentni sistem za proces podpore strankam. Prepoznajte agente v procesu, njihove vloge in odgovornosti ter kako med seboj sodelujejo. Upoštevajte tako agente specifične za proces podpore kot tudi splošne agente, ki jih lahko uporabite v drugih delih vašega poslovanja.
> Premislite, preden preberete naslednjo rešitev, morda boste potrebovali več agentov, kot mislite.

> NAMIG: Razmislite o različnih fazah procesa podpore strankam in prav tako upoštevajte agente, potrebne za kateri koli sistem.

## Rešitev

[Rešitev](./solution/solution.md)

## Preverjanje znanja

Vprašanje: Kdaj bi morali razmisliti o uporabi več agentov?

- [ ] A1: Ko imate malo dela in enostavno nalogo.
- [ ] A2: Ko imate veliko dela
- [ ] A3: Ko imate enostavno nalogo.

[Rešitveni kviz](./solution/solution-quiz.md)

## Povzetek

V tej lekciji smo si ogledali vzorec večagentnega načrtovanja, vključno s scenariji, kjer so večagenti primerni, prednosti uporabe več agentov pred enim samim agentom, gradnike za implementacijo večagentnega vzorca ter kako imeti pregled nad tem, kako medsebojno delujejo več agenti.

### Imate več vprašanj o večagentnem vzorcu načrtovanja?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), da se srečate z drugimi udeleženci, obiščete svetovalne ure in dobite odgovore na vprašanja o AI agentih.

## Dodatni viri

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Vzorce načrtovanja AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentni vzorci načrtovanja</a>


## Prejšnja lekcija

[Načrtovanje oblikovanja](../07-planning-design/README.md)

## Naslednja lekcija

[Metakognicija v AI agentih](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Omejitev odgovornosti**:
Ta dokument je bil preveden z uporabo AI prevajalske storitve [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da avtomatizirani prevodi lahko vsebujejo napake ali netočnosti. Izvirni dokument v njegovem izvirnem jeziku velja za uradni vir. Za ključne informacije priporočamo strokovni človeški prevod. Za morebitna nesporazuma ali napačne interpretacije, ki izhajajo iz uporabe tega prevoda, ne prevzemamo nobene odgovornosti.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->