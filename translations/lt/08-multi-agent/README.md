[![Multi-agentų dizaino modeliai](../../../translated_images/lt/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Norėdami peržiūrėti pamokos vaizdo įrašą, spustelėkite aukščiau esantį paveikslėlį)_

# Multi-agentų dizaino modeliai

Vos pradėję dirbti su projektu, kuriame dalyvauja keli agentai, turėsite apsvarstyti multi-agentų dizaino modelį. Tačiau gali būti ne iš karto aišku, kada pereiti prie multi-agentų ir kokie yra pranašumai.

## Įvadas

Šioje pamokoje sieksime atsakyti į šiuos klausimus:

- Kokiose situacijose taikomi multi-agentai?
- Kokie yra multi-agentų naudojimo pranašumai, palyginti su vienu agentu, atliekant kelių užduočių?
- Kokie yra pagrindiniai multi-agentų dizaino modelio komponentai?
- Kaip galime matyti, kaip keli agentai sąveikauja tarpusavyje?

## Mokymosi tikslai

Šios pamokos pabaigoje turėtumėte sugebėti:

- Nustatyti situacijas, kuriose taikomi multi-agentai
- Atpažinti multi-agentų naudojimo pranašumus, palyginti su vienu agentu.
- Suprasti pagrindinius multi-agentų dizaino modelio komponentus.

Kokia yra didesnė prasmė?

*Multi-agentai yra dizaino modelis, leidžiantis keliems agentams bendradarbiauti siekiant bendro tikslo*.

Šis modelis plačiai naudojamas įvairiose srityse, įskaitant robotiką, autonomines sistemas ir paskirstytą skaičiavimą.

## Situacijos, kuriose taikomi multi-agentai

Kokios situacijos yra tinkamas multi-agentų taikymo pavyzdys? Atsakymas — daug situacijų, kai keli agentai yra naudingi, ypač šiais atvejais:

- **Didelis darbo krūvis**: dideles užduotis galima padalinti į mažesnes ir paskirti skirtingiems agentams, leidžiant lygiagrečiai apdoroti ir greičiau jas atlikti. Tokiu pavyzdžiu gali būti didelio duomenų apdorojimo užduotis.
- **Sudėtingos užduotys**: sudėtingas užduotis galima suskaidyti į mažesnes potaskes ir paskirti skirtingiems agentams, iš kurių kiekvienas specializuojasi specifinėje srityje. Geras pavyzdys yra autonominiai automobiliai, kur skirtingi agentai valdo navigaciją, kliūčių aptikimą ir komunikaciją su kitais automobiliais.
- **Įvairovė ekspertizėje**: skirtingi agentai gali turėti skirtingą ekspertizę, leidžiančią efektyviau spręsti įvairius užduoties aspektus, nei tai padarytų vienas agentas. Tokio atvejo pavyzdys yra sveikatos priežiūra, kur agentai valdo diagnostiką, gydymo planus ir paciento stebėjimą.

## Multi-agentų naudojimo pranašumai, palyginti su vienu agentu

Vienas agentas gali gerai susitvarkyti su paprastomis užduotimis, tačiau sudėtingesnėse užduotyse keli agentai suteikia kelių pranašumų:

- **Specializacija**: kiekvienas agentas gali būti specializuotas konkrečiai užduočiai. Vieno agento specializacijos stygius reiškia, kad agentas gali daryti viską, bet gali būti pasimetęs sudėtingoje užduotyje. Jis gali, pavyzdžiui, atlikti užduotį, kuriai nėra geriausiai tinkamas.
- **Mastelio keitimas**: lengviau plesti sistemas pridedant daugiau agentų nei apkraunant vieną agentą.
- **Gedimų tolerancija**: jei vienas agentas sugenda, kiti gali toliau veikti, užtikrindami sistemos patikimumą.

Pavyzdžiui, tarkime, kad užsakome kelionę vartotojui. Vieno agento sistema turėtų tvarkyti visus kelionės užsakymo aspektus – nuo skrydžių paieškos iki viešbučių ir automobilių nuomos rezervacijos. Norint tai padaryti vienam agentui, jam reikėtų turėti įrankius visoms šioms užduotims atlikti, kas gali lemti sudėtingą ir monolitinę sistemą, kurios priežiūra ir mastelio keitimas yra sunkūs. Multi-agentų sistema galėtų turėti skirtingus agentus, specializuotus skrydžių paieškai, viešbučių ir automobilių nuomai. Tai padarytų sistemą labiau moduline, lengviau prižiūrimą ir plečiamą.

Palyginkite kelionių biurą, valdomą šeimos verslo, su kelionių biuru, veikiančiu kaip franšizė. Šeimos verslas turėtų vieną agentą, tvarkantį visus kelionės užsakymo aspektus, o franšizė – skirtingus agentus, atsakingus už įvairius proceso etapus.

## Multi-agentų dizaino modelio komponentai

Prieš įgyvendindami multi-agentų dizaino modelį, turite suprasti jo pagrindinius komponentus.

Pavyzdžiui, vėl pažvelkime į kelionės užsakymo pavyzdį. Šiuo atveju komponentai būtų:

- **Agentų komunikacija**: agentai, ieškantys skrydžių, užsakantys viešbučius ir automobilius, turi komunikuoti ir dalintis informacija apie vartotojo pageidavimus ir apribojimus. Turite nuspręsti protokolus ir metodus šiai komunikacijai. Konkrečiai tai reiškia, kad skrydžių agentas turi komunikuoti su viešbučių agentu, kad užtikrintų, jog viešbutis rezervuojamas tais pačiais datomis kaip ir skrydis. Tai reiškia, kad agentai turi dalintis informacija apie kelionės datas, todėl turite nuspręsti *kokie agentai dalijasi informacija ir kaip tai vyksta*.
- **Koordinavimo mechanizmai**: agentai turi koordinuoti veiksmus, kad vartotojo pageidavimai ir apribojimai būtų įvykdyti. Vartotojo pageidavimas gali būti viešbutis netoli oro uosto, o apribojimas – kad automobilių nuoma yra tik oro uoste. Tai reiškia, kad viešbučių agentas turi koordinuotis su automobilių nuomos agentu, kad būtų atsižvelgta į vartotojo pageidavimus ir apribojimus. Todėl turite nuspręsti *kaip agentai koordinuoja savo veiksmus*.
- **Agentų architektūra**: agentai turi turėti vidinę struktūrą sprendimams priimti ir mokytis iš sąveikos su vartotoju. Tai reiškia, kad skrydžių agentas turi turėti vidinę struktūrą sprendimams, kuriuos skrydžius rekomenduoti. Turite nuspręsti *kaip agentai priima sprendimus ir mokosi iš sąveikos su vartotoju*. Pavyzdžiui, skrydžių agentas gali naudoti mašininio mokymosi modelį, kad rekomenduotų skrydžius pagal vartotojo ankstesnius pageidavimus.
- **Matomumas į multi-agentų sąveikas**: turite matyti, kaip keli agentai sąveikauja tarpusavyje. Tam reikia turėti priemones ir technikas agentų veiklos ir sąveikų sekimui. Tai gali būti žurnalavimo ir stebėjimo įrankiai, vizualizacijos priemonės ir našumo metrika.
- **Multi-agentų modeliai**: yra skirtingų modelių multi-agentų sistemų įgyvendinimui, pavyzdžiui, centralizuotos, decentralizuotos ir hibridinės architektūros. Turite nuspręsti, kuris modelis geriausiai atitinka jūsų naudojimo atvejį.
- **Žmogus cikle**: daugeliu atvejų žmogus yra procese ir turite nurodyti agentams, kada prašyti žmogaus įsikišimo. Tai gali būti, kai vartotojas prašo konkretaus viešbučio ar skrydžio, kurio agentai nesiūlė, arba patvirtinimo prieš užsakant skrydį ar viešbutį.

## Matomumas į multi-agentų sąveikas

Labai svarbu matyti, kaip keli agentai sąveikauja tarpusavyje. Šis matomumas būtinas derinimui, optimizavimui ir bendros sistemos efektyvumo užtikrinimui. Tam reikalingos priemonės ir technikos agentų veiklų bei sąveikų sekimui. Tai gali būti žurnalavimo ir stebėjimo įrankiai, vizualizacijos priemonės ir našumo metrika.

Pavyzdžiui, kelionės užsakymo atveju galite turėti informacijos suvestinę, rodančią kiekvieno agento būseną, vartotojo pageidavimus ir apribojimus bei agentų sąveikas. Šioje suvestinėje būtų rodoma vartotojo kelionės datos, skrydžius rekomenduojantis agentas, viešbučius rekomenduojantis agentas ir automobilių nuomą rekomenduojantis agentas. Tai suteiks aiškų vaizdą, kaip agentai sąveikauja ir ar vartotojo pageidavimai bei apribojimai tenkinami.

Pažvelkime į kiekvieną iš šių aspektų detaliau.

- **Žurnalavimo ir stebėjimo įrankiai**: norite žurnalizuoti kiekvieną agento veiksmą. Žurnalo įrašas gali saugoti informaciją apie agentą, atlikusį veiksmą, veiksmą, veiksmų atlikimo laiką ir rezultatus. Ši informacija gali būti naudojama derinimui, optimizavimui ir kitkam.
- **Vizualizacijos priemonės**: padeda aiškiau matyti agentų sąveikas. Pavyzdžiui, galėtumėte turėti grafiką, rodantį informacijos srautą tarp agentų. Tai padėtų identifikuoti sistemos užtrauktukus, neveiklumą ir kitus trūkumus.
- **Našumo metrika**: padeda stebėti multi-agentų sistemos efektyvumą. Pavyzdžiui, galite fiksuoti užduoties atlikimo laiką, užduočių skaičių per laiko vienetą ir agentų rekomendacijų tikslumą. Ši informacija padeda rasti tobulintinas sritis ir optimizuoti sistemą.

## Multi-agentų modeliai

Panagrinėkime konkrečius modelius, skirtus multi-agentų programoms kurti. Štai keletas įdomių modelių, vertų dėmesio:

### Grupinis pokalbis

Šis modelis praverčia, kai kuriate grupinio pokalbio programą, kurioje keli agentai gali bendrauti tarpusavyje. Tipiniai panaudojimo atvejai – komandos bendradarbiavimas, klientų aptarnavimas, socialiniai tinklai.

Šiame modelyje kiekvienas agentas atstovauja vartotojui grupinio pokalbio programoje, o žinutės keičiamos tarp agentų naudojant žinučių protokolą. Agentai gali siųsti žinutes grupėje, gauti žinutes iš grupės ir atsakyti kitiems agentams.

Modelį galima įgyvendinti naudojant centralizuotą architektūrą, kur visos žinutės keliauja per centrinį serverį, arba decentralizuotą architektūrą, kai žinutės keičiasi tiesiogiai.

![Grupinis pokalbis](../../../translated_images/lt/multi-agent-group-chat.ec10f4cde556babd.webp)

### Užduočių perdavimas

Šis modelis tinka, kai kuriate programą, kurioje keli agentai gali perduoti užduotis vieni kitiems.

Tipiniai panaudojimo atvejai – klientų aptarnavimas, užduočių valdymas, darbo srauto automatizavimas.

Šiame modelyje kiekvienas agentas atstovauja užduotį arba darbo srauto žingsnį, ir agentai gali perduoti užduotis kitiems agentams pagal nustatytas taisykles.

![Užduočių perdavimas](../../../translated_images/lt/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Bendradarbiaujantis filtravimas

Šis modelis naudingas, kai keli agentai gali bendradarbiauti rekomendacijų vartotojams teikimui.

Kodėl keli agentai turėtų bendradarbiauti? Kadangi kiekvienas agentas gali turėti skirtingą ekspertizę ir prisidėti prie rekomendacijų proceso skirtingais būdais.

Pavyzdžiui, vartotojas nori gauti rekomendaciją, kokią geriausią akciją pirkti rinkoje.

- **Pramonės ekspertas**: vienas agentas gali būti ekspertas konkrečioje pramonės šakoje.
- **Techninė analizė**: kitas agentas – techninės analizės specialistas.
- **Pagrindinė analizė**: dar vienas agentas – fundamentinės analizės specialistas. Bendradarbiaudami šie agentai gali pateikti išsamesnes rekomendacijas vartotojui.

![Rekomendacija](../../../translated_images/lt/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenarijus: Grąžinimo procesas

Apsvarstykite situaciją, kai klientas siekia gauti produkto grąžinimą. Procese gali dalyvauti nemažai agentų, tačiau padalinsime juos į procesui specifinius agentus ir bendruosius agentus, naudojamus kitose jūsų verslo srityse.

**Procesui specifiniai agentai**:

Šie agentai gali dalyvauti grąžinimo procese:

- **Kliento agentas**: atstovauja klientą ir pradeda grąžinimo procesą.
- **Pardavėjo agentas**: atstovauja pardavėją ir tvarko grąžinimą.
- **Mokėjimo agentas**: valdo mokėjimų procesą ir atsakingas už kliento pinigų grąžinimą.
- **Sprendimų agentas**: sprendžia iškilusias problemas grąžinimo procese.
- **Atitikties agentas**: užtikrina, kad grąžinimo procesas atitinka taisykles ir politiką.

**Bendrieji agentai**:

Šie agentai gali būti naudojami kitose jūsų verslo srityse.

- **Pristatymo agentas**: valdo produkto grąžinimo į pardavėją procesą. Šis agentas gali būti naudojamas tiek grąžinimo procese, tiek bendram produkto siuntimui, pavyzdžiui, pirkimo atveju.
- **Atsiliepimų agentas**: renka klientų atsiliepimus. Atsiliepimai gali būti renkami bet kada, ne tik grąžinimo metu.
- **Eskalacijos agentas**: eskaluoja problemas aukštesnio lygio pagalbai. Šio tipo agentą galite naudoti bet kuriame procese, kur reikalinga eskalacija.
- **Pranešimų agentas**: siunčia pranešimus klientui įvairiais grąžinimo proceso etapais.
- **Analitikos agentas**: analizuoja su grąžinimo procesu susijusius duomenis.
- **Auditavimo agentas**: atlieka grąžinimo proceso auditą, užtikrindamas teisingą vykdymą.
- **Ataskaitų agentas**: rengia grąžinimo proceso ataskaitas.
- **Žinių agentas**: palaiko žinių bazę apie grąžinimo procesą. Šis agentas gali būti išmanantis tiek grąžinimų, tiek kitų jūsų verslo sričių klausimais.
- **Saugumo agentas**: užtikrina grąžinimo proceso saugumą.
- **Kokybės agentas**: užtikrina grąžinimo proceso kokybę.

Prieš tai išvardyta nemažai agentų tiek konkrečiam grąžinimo procesui, tiek bendrieji agentai kitoms jūsų veiklos sritims. Tikimės, tai padės suprasti, kaip galite apsispręsti dėl agentų naudojimo savo multi-agentų sistemoje.

## Užduotis

Sukurkite multi-agentų sistemą klientų aptarnavimo procesui. Nustatykite procese dalyvaujančius agentus, jų vaidmenis ir atsakomybes bei kaip jie sąveikauja tarpusavyje. Įvertinkite tiek klientų aptarnavimo procesui specifinius agentus, tiek bendruosius agentus, kurie gali būti naudojami kitose jūsų verslo srityse.
> Pagalvokite prieš skaitydami šį sprendimą, galbūt jums reikės daugiau agentų nei manote.

> PATARIMAS: Pagalvokite apie skirtingus klientų aptarnavimo proceso etapus ir taip pat apsvarstykite agentus, reikalingus bet kuriai sistemai.

## Sprendimas

[Sprendimas](./solution/solution.md)

## Žinių patikrinimai

Klausimas: Kada reikėtų apsvarstyti daugiaagentinį naudojimą?

- [ ] A1: Kai turite mažą darbų kiekį ir paprastą užduotį.
- [ ] A2: Kai turite didelį darbų kiekį
- [ ] A3: Kai turite paprastą užduotį.

[Sprendimo testas](./solution/solution-quiz.md)

## Santrauka

Šioje pamokoje aptarėme daugiaagentinį dizaino šabloną, įskaitant scenarijus, kur daugiaagentinis šablonas yra tinkamas, daugiaagentinių agentų pranašumus prieš vieną agentą, daugiaagentinio dizaino šablono įgyvendinimo pagrindinius elementus ir kaip matyti, kaip keli agentai sąveikauja tarpusavyje.

### Turite daugiau klausimų apie daugiaagentinį dizaino šabloną?

Prisijunkite prie [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kad susitiktumėte su kitais besimokančiais, dalyvautumėte konsultacijose ir gautumėte atsakymus į savo AI agentų klausimus.

## Papildomi ištekliai

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen dizaino šablonai</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentiniai dizaino šablonai</a>


## Ankstesnė pamoka

[Planavimo dizainas](../07-planning-design/README.md)

## Kita pamoka

[Metakognicija AI agentuose](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors stengiamės užtikrinti tikslumą, atkreipkite dėmesį, kad automatizuoti vertimai gali turėti klaidų ar netikslumų. Originalus dokumentas gimtąja kalba turėtų būti laikomas autoritetingu šaltiniu. Dėl svarbios informacijos rekomenduojame kreiptis į profesionalų žmogaus vertėją. Mes neatsakome už bet kokius nesusipratimus ar neteisingas interpretacijas, kylančias dėl šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->