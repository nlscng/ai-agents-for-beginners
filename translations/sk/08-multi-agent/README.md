[![Dizajn s viacerými agentmi](../../../translated_images/sk/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Kliknite na obrázok vyššie pre zobrazenie videa tejto lekcie)_

# Dizajnové vzory s viacerými agentmi

Akonáhle začnete pracovať na projekte, ktorý zahŕňa viacerých agentov, budete musieť zvážiť dizajnový vzor s viacerými agentmi. Nie je však vždy okamžite jasné, kedy prejsť na viac agentov a aké sú výhody.

## Úvod

V tejto lekcii sa snažíme zodpovedať nasledujúce otázky:

- V akých scenároch je použitie viacerých agentov vhodné?
- Aké sú výhody použitia viacerých agentov oproti jednému agentovi vykonávajúcemu viac úloh?
- Aké sú stavebné prvky implementácie dizajnového vzoru s viacerými agentmi?
- Ako môžeme získať prehľad o tom, ako viacerí agenti navzájom spolupracujú?

## Ciele učenia

Po tejto lekcii by ste mali byť schopní:

- Identifikovať scenáre, kde je použitie viacerých agentov vhodné
- Rozpoznať výhody použitia viacerých agentov oproti jednému agentovi
- Pochopiť stavebné prvky implementácie dizajnového vzoru s viacerými agentmi

Aký je širší kontext?

*Viac agentov je dizajnový vzor, ktorý umožňuje viacerým agentom spolupracovať na dosiahnutí spoločného cieľa.*

Tento vzor sa široko používa v rôznych oblastiach, vrátane robotiky, autonómnych systémov a distribuovaných výpočtov.

## Scenáre, kde je použitie viacerých agentov vhodné

Ktoré scenáre sú teda dobrým prípadom použitia viacerých agentov? Odpoveď je, že existuje mnoho scenárov, kde použitie viacerých agentov prináša výhody, hlavne v nasledujúcich prípadoch:

- **Veľké pracovné zaťaženie**: Veľké pracovné zaťaženie sa môže rozdeliť na menšie úlohy a priradiť rôznym agentom, čo umožňuje paralelné spracovanie a rýchlejšie dokončenie. Príkladom je veľká úloha na spracovanie údajov.
- **Zložité úlohy**: Podobne ako pri veľkom pracovnom zaťažení, zložité úlohy sa môžu rozdeliť na menšie podúlohy a priradiť rôznym agentom, ktorí sa špecializujú na konkrétne aspekty úlohy. Dobrou ukážkou sú autonómne vozidlá, kde rôzni agenti riadia navigáciu, detekciu prekážok a komunikáciu s inými vozidlami.
- **Rôznorodá odbornosť**: Rôzni agenti môžu mať rôzne odborné znalosti, čo im umožňuje efektívnejšie riešiť rôzne aspekty úlohy než jeden agent. Príkladom je zdravotná starostlivosť, kde agenti spravujú diagnostiku, liečebné plány a monitorovanie pacientov.

## Výhody použitia viacerých agentov oproti jednému agentovi

Jednoagentový systém môže fungovať dobre pre jednoduché úlohy, no pri zložitejších úlohách môže použitie viacerých agentov priniesť niekoľko výhod:

- **Špecializácia**: Každý agent môže byť špecializovaný na konkrétnu úlohu. Nedostatok špecializácie v jednom agentovi znamená, že má agent na starosť všetko, ale môže byť zmätený pri riešení zložitej úlohy. Môže napríklad skončiť pri úlohe, na ktorú nie je najvhodnejší.
- **Škálovateľnosť**: Ľahšie je škálovať systémy pridaním ďalších agentov než preťažovaním jedného agenta.
- **Odolnosť voči chybám**: Ak jeden agent zlyhá, ostatní môžu pokračovať v činnosti, čo zabezpečuje spoľahlivosť systému.

Príkladom môže byť rezervácia výletu pre používateľa. Jednoagentový systém by musel riešiť všetky aspekty rezervácie, od hľadania letov, cez rezervovanie hotelov až po prenájom áut. Aby to zvládol, musel by mať agent nástroje na spracovanie všetkých týchto úloh. To by mohlo viesť ku komplikovanému a monolitickému systému, ktorý je ťažko udržiavateľný a škálovateľný. Multi-agentový systém by naopak mohol mať rôznych agentov špecializovaných na hľadanie letov, rezerváciu hotelov a prenájom áut. Takýto systém je modulárnejší, ľahšie sa udržiava a je škálovateľný.

Porovnajte to s cestovnou kanceláriou prevádzkovanou ako malý rodinný podnik oproti kancelárii fungujúcej ako franšíza. Rodinný podnik by mal jednoliateho agenta, ktorý rieši všetky aspekty rezervácie výletu, zatiaľ čo franšíza by mala rôznych agentov, ktorí spravujú rozdielne časti procesu rezervácie.

## Stavebné prvky implementácie dizajnového vzoru s viacerými agentmi

Predtým, než implementujete dizajnový vzor s viacerými agentmi, musíte pochopiť, z akých prvkov sa skladá.

Opäť si to konkretizujeme na príklade rezervácie výletu pre používateľa. Stavebné prvky by mohli obsahovať:

- **Komunikácia agentov**: Agent pre hľadanie letov, agent pre rezerváciu hotelov a agent pre prenájom áut musia komunikovať a zdieľať informácie o používateľových preferenciách a obmedzeniach. Musíte rozhodnúť o protokoloch a metódach tejto komunikácie. Konkrétne to znamená, že agent pre hľadanie letov musí komunikovať s agentom pre rezerváciu hotelov, aby bol hotel rezervovaný na rovnaké dátumy ako let. To znamená, že agenti si musia vymeniť informácie o dátumoch cesty používateľa, teda musíte určiť *ktorí agenti si informácie zdieľajú a ako si ich zdieľajú*.
- **Koordinačné mechanizmy**: Agenti musia koordinovať svoje činnosti, aby splnili preferencie a obmedzenia používateľa. Používateľ môže preferovať hotel blízko letiska, zatiaľ čo obmedzenie môže byť, že prenájom áut je možný len na letisku. To znamená, že agent pre rezerváciu hotelov musí koordinovať s agentom pre prenájom áut tak, aby boli splnené preferencie a obmedzenia používateľa. Musíte teda rozhodnúť *ako agenti koordinujú svoje činnosti*.
- **Architektúra agenta**: Agenti musia mať vnútornú štruktúru na rozhodovanie a učenie sa zo svojich interakcií s používateľom. To znamená, že agent pre hľadanie letov musí mať štruktúru na rozhodovanie, ktoré lety odporučiť. Musíte teda určiť *ako agenti robia rozhodnutia a učia sa z interakcií s používateľom*. Príklady, ako sa agent učí a zlepšuje, môžu byť napríklad použitie modelu strojového učenia na odporúčanie letov na základe predchádzajúcich preferencií používateľa.
- **Prehľad o interakciách viacerých agentov**: Musíte mať prehľad o tom, ako viacerí agenti spolupracujú. To znamená, že potrebujete nástroje a techniky na sledovanie aktivít a interakcií agentov. Môžu to byť nástroje na logovanie a monitorovanie, vizualizačné nástroje a metriky výkonu.
- **Vzory viacerých agentov**: Existujú rôzne vzory implementácie multi-agentových systémov, ako sú centralizovaná, decentralizovaná a hybridná architektúra. Musíte vybrať vzor, ktorý najlepšie sedí vášmu prípadu použitia.
- **Človek v slučke**: Vo väčšine prípadov bude človek v slučke a vy musíte inštruovať agentov, kedy majú požiadať o ľudský zásah. Môže to byť napríklad vtedy, keď používateľ požaduje konkrétny hotel alebo let, ktorý agenti neodporučili, alebo keď je potrebné potvrdenie pred rezerváciou letu či hotela.

## Prehľad o interakciách viacerých agentov

Je dôležité, aby ste mali prehľad o tom, ako viacerí agenti spolupracujú. Tento prehľad je nevyhnutný na ladenie, optimalizáciu a zabezpečenie efektívnosti celého systému. Na dosiahnutie tohto cieľa potrebujete nástroje a techniky na sledovanie aktivít a interakcií agentov. Môžu to byť nástroje na logovanie a monitorovanie, vizualizačné nástroje a metriky výkonu.

Napríklad v prípade rezervácie výletu by ste mohli mať panel, ktorý zobrazuje stav každého agenta, používateľove preferencie a obmedzenia a interakcie medzi agentmi. Tento panel by mohol zobrazovať dátumy cesty používateľa, lety odporúčané agentom pre lety, hotely odporúčané agentom pre hotely a autopožičovne odporúčané agentom pre prenájom áut. To by vám poskytlo jasný prehľad o tom, ako agenti navzájom spolupracujú a či sú splnené preferencie a obmedzenia používateľa.

Pozrime sa na jednotlivé aspekty podrobnejšie.

- **Nástroje na logovanie a monitorovanie**: Chcete, aby bol logovaný každý krok agenta. Záznam logu môže uložiť informácie o tom, ktorý agent vykonal akciu, akú akciu vykonal, kedy to bolo a ako dopadla. Tieto informácie možno použiť na ladenie, optimalizáciu a ďalšie účely.

- **Vizualizačné nástroje**: Vizualizačné nástroje vám môžu pomôcť vidieť interakcie medzi agentmi intuitívnejším spôsobom. Napríklad graf, ktorý zobrazuje tok informácií medzi agentmi, môže pomôcť identifikovať úzke miesta, neefektivity a ďalšie problémy v systéme.

- **Metriky výkonu**: Metriky výkonu vám pomôžu sledovať efektivitu multi-agentového systému. Môžete sledovať napríklad čas potrebný na dokončenie úlohy, počet dokončených úloh za jednotku času a presnosť odporúčaní agentov. Tieto informácie vám pomôžu identifikovať oblasti na zlepšenie a optimalizovať systém.

## Vzory viacerých agentov

Pozrime sa na konkrétne vzory, ktoré môžeme použiť na vytvorenie aplikácií s viacerými agentmi. Tu sú niektoré zaujímavé vzory, ktoré stojí za zváženie:

### Skupinový chat

Tento vzor je užitočný, keď chcete vytvoriť aplikáciu skupinového chatu, kde viacerí agenti môžu medzi sebou komunikovať. Typické prípady použitia zahŕňajú tímovú spoluprácu, zákaznícku podporu a sociálne siete.

V tomto vzore každý agent predstavuje používateľa v skupinovom chate a správy sa medzi agentmi vymieňajú pomocou spravodajského protokolu. Agenti môžu posielať správy do skupiny, prijímať správy zo skupiny a odpovedať na správy od iných agentov.

Tento vzor možno implementovať pomocou centralizovanej architektúry, kde sú všetky správy smerované cez centrálny server, alebo decentralizovanej architektúry, kde sa správy vymieňajú priamo.

![Skupinový chat](../../../translated_images/sk/multi-agent-group-chat.ec10f4cde556babd.webp)

### Odovzdanie úlohy

Tento vzor je užitočný, keď chcete vytvoriť aplikáciu, kde si viacerí agenti môžu predávať úlohy medzi sebou.

Typické prípady použitia zahŕňajú zákaznícku podporu, správu úloh a automatizáciu pracovných postupov.

V tomto vzore každý agent predstavuje úlohu alebo krok v pracovnom postupe a agenti si môžu úlohy odovzdať na základe vopred definovaných pravidiel.

![Odovzdanie](../../../translated_images/sk/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Spolupracujúce filtrovanie

Tento vzor je užitočný, keď chcete vytvoriť aplikáciu, kde viacerí agenti spolupracujú na tvorbe odporúčaní pre používateľov.

Prečo by ste chceli, aby viacerí agenti spolupracovali, je pretože každý agent môže mať inú odbornosť a prispievať do procesu odporúčania rôznymi spôsobmi.

Príkladom môže byť používateľ, ktorý chce odporúčanie na najlepší akciový titul na burze.

- **Odborník na priemysel**: Jeden agent môže byť odborníkom v konkrétnom odvetví.
- **Technická analýza**: Ďalší agent môže byť odborníkom na technickú analýzu.
- **Fundamentálna analýza**: Tretí agent môže byť odborníkom na fundamentálnu analýzu. Spoluprácou môžu títo agenti poskytnúť komplexnejšie odporúčanie používateľovi.

![Odporúčania](../../../translated_images/sk/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenár: Proces vrátenia peňazí

Zvážme scenár, kde zákazník sa snaží získať vrátenie peňazí za produkt. V tomto procese môže byť zapojených niekoľko agentov, ale rozdelíme ich na agentov špecifických pre tento proces a všeobecných agentov, ktorí môžu byť použiteľní aj v iných procesoch.

**Agenti špecifickí pre proces vrátenia peňazí**:

Nasledujú agenti, ktorí môžu byť zapojení do procesu vrátenia peňazí:

- **Agent zákazníka**: Tento agent reprezentuje zákazníka a je zodpovedný za iniciáciu procesu vrátenia peňazí.
- **Agent predajcu**: Tento agent reprezentuje predajcu a spracováva vrátenie peňazí.
- **Agent platby**: Tento agent reprezentuje platobný proces a zodpovedá za vrátenie platby zákazníkovi.
- **Agent vyriešenia**: Tento agent spravuje riešenie akýchkoľvek problémov vzniknutých počas procesu vrátenia.
- **Agent súladu**: Tento agent zabezpečuje, že proces vrátenia peňazí je v súlade s pravidlami a politikami.

**Všeobecní agenti**:

Títo agenti môžu byť použiteľní v iných častiach vášho podnikania.

- **Agent dopravy**: Tento agent reprezentuje proces dopravy a zabezpečuje vrátenie produktu predajcovi. Môže byť použitý nielen v procese vrátenia peňazí, ale aj na bežnú dopravu produktov.
- **Agent spätnej väzby**: Tento agent zodpovedá za zber spätnej väzby od zákazníka. Spätná väzba môže byť získavaná kedykoľvek, nielen počas procesu vrátenia.
- **Agent eskalácie**: Tento agent rieši eskalácie problémov na vyššiu úroveň podpory. Tento agent možno použiť pri akomkoľvek procese, kde je potrebné eskalovať problém.
- **Agent oznámení**: Tento agent zasiela oznámenia zákazníkovi v rôznych fázach procesu vrátenia.
- **Agent analytiky**: Analyzuje dáta súvisiace s procesom vrátenia peňazí.
- **Agent auditu**: Kontroluje, či je proces vrátenia správne vykonávaný.
- **Agent reportingu**: Generuje správy o procese vrátenia peňazí.
- **Agent znalostí**: Spravuje databázu znalostí súvisiacu s procesom vrátenia, môže mať znalosti aj o iných oblastiach vášho podnikania.
- **Agent bezpečnosti**: Zodpovedá za zabezpečenie procesu vrátenia.
- **Agent kvality**: Zabezpečuje kvalitu procesu vrátenia.

Už uvedených agentov je dosť veľa, či už pre špecifický proces vrátenia, alebo pre všeobecných agentov, ktorí môžu byť využití v iných oblastiach vášho podnikania. Dúfame, že vám to poskytne predstavu o tom, ako sa rozhodnúť, ktorých agentov použiť vo vašom multi-agentovom systéme.

## Zadanie

Navrhnite multi-agentový systém pre proces zákazníckej podpory. Identifikujte agentov zapojených v procese, ich úlohy a zodpovednosti, a ako navzájom interagujú. Zvážte agentov špecifických pre proces zákazníckej podpory aj všeobecných agentov použiteľných v iných častiach vášho podnikania.
> Premyslite si to, než si prečítate nasledujúce riešenie, možno budete potrebovať viac agentov, než si myslíte.

> TIP: Zamyslite sa nad jednotlivými fázami procesu zákazníckej podpory a tiež zvážte agentov potrebných pre akýkoľvek systém.

## Riešenie

[Riešenie](./solution/solution.md)

## Kontrolya poznatkov

Otázka: Kedy by ste mali zvážiť použitie viacerých agentov?

- [ ] A1: Keď máte malú pracovnú záťaž a jednoduchý úlohu.
- [ ] A2: Keď máte veľkú pracovnú záťaž.
- [ ] A3: Keď máte jednoduchý úlohu.

[Kvíz k riešeniu](./solution/solution-quiz.md)

## Zhrnutie

V tejto lekcii sme sa pozreli na návrhový vzor viacerých agentov, vrátane scenárov, kde sú viacero agentov použiteľní, výhod používania viacerých agentov oproti jednému agentovi, základných stavebných blokov implementácie návrhového vzoru viacerých agentov a ako mať prehľad o tom, ako spolu viacerí agenti interagujú.

### Máte viac otázok o návrhovom vzore viacerých agentov?

Pridajte sa na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kde sa môžete stretnúť s ďalšími študentmi, zúčastniť sa úradných hodín a zodpovedať si svoje otázky o AI agentoch.

## Ďalšie zdroje

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Návrhové vzory AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentické návrhové vzory</a>

## Predchádzajúca lekcia

[Plánovanie návrhu](../07-planning-design/README.md)

## Nasledujúca lekcia

[Metakognícia v AI agentoch](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Upozornenie**:  
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Aj keď sa snažíme o presnosť, majte prosím na pamäti, že automatizované preklady môžu obsahovať chyby alebo nepresnosti. Originálny dokument v jeho pôvodnom jazyku by mal byť považovaný za autoritatívny zdroj. Pre dôležité informácie sa odporúča profesionálny ľudský preklad. Nie sme zodpovední za akékoľvek nedorozumenia alebo nesprávne výklady vyplývajúce z použitia tohto prekladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->