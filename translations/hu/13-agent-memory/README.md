# Memória az AI Ügynökök számára  
[![Agent Memory](../../../translated_images/hu/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Az AI Ügynökök egyedi előnyeinek megvitatásakor főként két dolgot említenek: az eszközök meghívásának képességét a feladatok elvégzéséhez és az idővel történő fejlődés képességét. A memória az alapja annak, hogy önfejlesztő ügynököket hozzunk létre, amelyek jobb élményeket képesek nyújtani felhasználóink számára.

Ebben a leckében megvizsgáljuk, hogy mi a memória az AI Ügynökök számára, és hogyan kezelhetjük és használhatjuk azt alkalmazásaink javára.

## Bevezetés

Ez a lecke a következőket tartalmazza:

• **AI Ügynök Memória megértése**: Mi az a memória, és miért elengedhetetlen az ügynökök számára.

• **Memória megvalósítása és tárolása**: Gyakorlati módszerek a memória képességek hozzáadására AI ügynökeidhez, különös tekintettel a rövid távú és hosszú távú memóriára.

• **Az AI Ügynökök önfejlesztése**: Hogyan teszi lehetővé a memória, hogy az ügynökök tanuljanak a múltbeli interakciókból és idővel fejlődjenek.

## Elérhető Megvalósítások

Ez a lecke két átfogó jegyzetfüzetes oktatóanyagot tartalmaz:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Mem0 és Azure AI Search használatával valósítja meg a memóriát a Semantic Kernel keretrendszerrel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Strukturált memóriát valósít meg Cognee segítségével, automatikusan épít tudásgráfot beágyazásokkal, vizualizálja a gráfot és intelligens lekérdezést kínál

## Tanulási Célok

A lecke elvégzése után tudni fogod, hogyan:

• **Megkülönböztesd az AI ügynök memóriájának különböző típusait**, beleértve a munka-, rövid távú és hosszú távú memóriát, valamint a speciális formákat, mint a persona és epizodikus memória.

• **Megvalósítsd és kezeld a rövid távú és hosszú távú memóriát AI ügynökök számára** a Semantic Kernel keretrendszer segítségével, kihasználva olyan eszközöket, mint a Mem0, Cognee, Whiteboard memória és integrálva az Azure AI Search szolgáltatást.

• **Megértsd az önfejlesztő AI ügynökökkel kapcsolatos alapelveket**, és azt, hogy a robosztus memória-kezelési rendszerek hogyan járulnak hozzá a folyamatos tanuláshoz és alkalmazkodáshoz.

## Az AI Ügynök Memória Megértése

Lényegében az **AI ügynökök memóriája az a mechanizmus, amely lehetővé teszi számukra, hogy megtartsák és előhívják az információkat**. Ezek az információk lehetnek specifikus részletek egy beszélgetésről, felhasználói preferenciák, korábbi műveletek vagy akár tanult minták.

Memória nélkül az AI alkalmazások gyakran állapot nélküli (stateless), ami azt jelenti, hogy minden interakció újrakezdődik. Ez ismétlődő és frusztráló felhasználói élményhez vezet, ahol az ügynök "elfelejti" az előző kontextust vagy preferenciákat.

### Miért fontos a memória?

Egy ügynök intelligenciája mélyen kötődik ahhoz, hogy mennyire képes előhívni és felhasználni a múltbeli információkat. A memória lehetővé teszi az ügynökök számára, hogy:

• **Reflektívak legyenek**: Tanuljanak a múltbeli cselekvésekből és eredményekből.

• **Interaktívak legyenek**: Fenntartsák a kontextust a folyamatban lévő beszélgetés során.

• **Proaktívak és reaktívak legyenek**: Megjósolják a szükségleteket vagy megfelelően reagálnak a történelmi adatok alapján.

• **Autonómak legyenek**: Önállóbban működjenek a tárolt tudásra támaszkodva.

A memória megvalósításának célja, hogy az ügynökök megbízhatóbbak és ügyesebbek legyenek.

### Memória típusok

#### Munka memória

Gondolj erre úgy, mint egy vázlatpapírra, amit az ügynök egyetlen, folyamatban lévő feladat vagy gondolatmenet során használ. Tartalmazza az azonnali információkat, amelyek szükségesek a következő lépés kiszámításához.

AI ügynökök esetén a munka memória gyakran rögzíti a beszélgetés legrelevánsabb információit, akkor is, ha a teljes csevegési előzmény hosszú vagy rövidített. Arra fókuszál, hogy kulcselemeket – mint követelmények, javaslatok, döntések és műveletek – emeljen ki.

**Munka memória példa**

Egy utazási foglalást végző ügynöknél a munka memória rögzítheti a felhasználó aktuális kérését, például "Szeretnék egy utat foglalni Párizsba". Ez a konkrét követelmény vesz részt az ügynök azonnali kontextusában a jelenlegi interakció irányítására.

#### Rövid távú memória

Ez a memória típus megtartja az információkat egyetlen beszélgetés vagy munkamenet idejére. Ez a jelenlegi csevegés kontextusa, amely lehetővé teszi, hogy az ügynök visszautaljon a párbeszéd korábbi fordulataira.

**Rövid távú memória példa**

Ha egy felhasználó megkérdezi: "Mennyibe kerül egy repülőjegy Párizsba?" majd utána rákérdez: "És a szállás ott?", a rövid távú memória biztosítja, hogy az ügynök tudja, hogy a "ott" Párizsra vonatkozik ugyanabban a beszélgetésben.

#### Hosszú távú memória

Ez az információ több beszélgetés vagy munkamenet során is fennmarad. Lehetővé teszi az ügynökök számára, hogy megjegyezzék a felhasználói preferenciákat, történelmi interakciókat vagy általános tudást hosszabb időn át. Ez fontos a személyre szabás szempontjából.

**Hosszú távú memória példa**

A hosszú távú memória eltárolhatja, hogy "Ben szeret síelni és szabadtéri tevékenységeket, élvezi a kávét hegyi kilátással, és el akarja kerülni a nehéz sípályákat egy korábbi sérülés miatt". Ez az információ korábbi interakciókból származik, és befolyásolja a jövőbeni utazástervezési üléseket, így rendkívül személyre szabottá téve azokat.

#### Persona memória

Ez a specializált memória segíti az ügynököt abban, hogy következetes "személyiséget" vagy "persona"-t alakítson ki. Lehetővé teszi, hogy az ügynök megjegyezzen magáról, vagy a tervezett szerepéről részleteket, így az interakciók folyékonyabbak és fókuszáltabbak lesznek.

**Persona memória példa**

Ha az utazási ügynök „szakértő sítervezőként” van kialakítva, a persona memória megerősítheti ezt a szerepet, befolyásolva a válaszokat, hogy azok összhangban legyenek egy szakértő hangjával és tudásával.

#### Munkafolyamat/epizodikus memória

Ez a memória az ügynök által összetett feladat során megtett lépések sorozatát tárolja, beleértve a sikereket és kudarcokat is. Mintha megjegyezné a specifikus "epizódokat" vagy korábbi tapasztalatokat, hogy tanulhasson belőlük.

**Epizodikus memória példa**

Ha az ügynök megpróbált lefoglalni egy adott járatot, de az nem volt elérhető, az epizodikus memória rögzítheti ezt a kudarcot, így az ügynök alternatív járatokat próbálhat meg vagy tájékoztathatja a felhasználót a problémáról tájékozottabb módon egy következő próbálkozás során.

#### Entitás memória

Ez magában foglalja konkrét entitások (például személyek, helyek vagy tárgyak) és események kinyerését és megjegyzését a beszélgetésekből. Lehetővé teszi az ügynök számára, hogy strukturált megértést építsen a kulcselemekről.

**Entitás memória példa**

Egy múltbeli utazásról szóló beszélgetésből az ügynök kinyerheti azokat az entitásokat, hogy "Párizs", "Eiffel-torony" és "vacsora a Le Chat Noir étteremben". Egy jövőbeli interakcióban az ügynök felidézheti a "Le Chat Noir"-t és felajánlhat új foglalást ott.

#### Strukturált RAG (Retrieval Augmented Generation)

Míg a RAG egy tágabb technika, addig a "Strukturált RAG" kiemelkedik, mint egy erőteljes memória technológia. Ez sűrű, strukturált információkat nyer ki különböző forrásokból (beszélgetések, e-mailek, képek), és használja azok pontosságának, előhívási képességének és sebességének növelésére a válaszokban. A klasszikus RAG-dal ellentétben, amely csupán szemorntikus hasonlóságra épül, a Strukturált RAG az információ bennszülött struktúrájával dolgozik.

**Strukturált RAG példa**

Ahelyett, hogy csak kulcsszavakat egyeztetne, a Strukturált RAG képes lehet egy e-mailből a repülőjárat adatait (célállomás, dátum, időpont, légitársaság) strukturált módon kinyerni és tárolni. Ez lehetővé teszi pontos lekérdezéseket, például: "Melyik járatot foglaltam Párizsba kedden?"

## Memória Megvalósítása és Tárolása

AI ügynökök memóriájának megvalósítása egy rendszeres folyamat, amely magában foglalja a **memória kezelést**, ideértve az információk generálását, tárolását, előhívását, integrálását, frissítését és akár "elfelejtését" (vagy törlését). Az előhívás különösen fontos szerepet tölt be.

### Specializált memória eszközök

#### Mem0

Az egyik módja az ügynök memória tárolásának és kezelésének a Mem0 használata. A Mem0 egy tartós memória rétegként működik, amely lehetővé teszi, hogy az ügynökök előhívják a releváns interakciókat, eltárolják a felhasználói preferenciákat és tényszerű kontextust, valamint idővel tanuljanak a sikerekből és kudarcokból. Az ötlet az, hogy az állapot nélküli ügynökök állapottal rendelkezővé váljanak.

Ez egy **kétfázisú memória-pipeline-on: kinyerés és frissítés** keresztül működik. Először az ügynök szálához hozzáadott üzeneteket a Mem0 szolgáltatásnak küldik, amely egy nagynyelvű modellt (LLM) használ a beszélgetési előzmények összefoglalására és új emlékek kinyerésére. Ezt követően egy LLM vezérelt frissítési fázis dönti el, hogy hozzáadja, módosítja vagy törli-e ezeket a memóriákat, melyeket egy hibrid adatbázisban tárolnak, amely magában foglalhat vektoros, gráf- és kulcs-érték adatbázisokat is. Ez a rendszer támogat különböző memória típusokat és beépíthet gráf memóriát az entitások közötti kapcsolatok kezelésére.

#### Cognee

Egy másik hatékony megközelítés a **Cognee** használata, amely egy nyílt forráskódú szemantikai memória az AI ügynökök számára, mely strukturált és strukturálatlan adatokat alakít át kérdezhető tudásgráfokká beágyazások támogatásával. A Cognee egy **kettős tároló architektúrát** kínál, amely ötvözi a vektorhasenlőségi keresést a gráfkapcsolatokkal, lehetővé téve az ügynökök számára, hogy ne csak azt értsék meg, milyen információk hasonlóak, hanem azt is, hogy a fogalmak hogyan kapcsolódnak egymáshoz.

Kitűnő a **hibrid előhívásban**, amely ötvözi a vektorhasenlőséget, a gráfstruktúrát és a LLM-alapú érvelést – a nyers darabkák keresésétől a gráfhoz kötött kérdés-válaszolásig. A rendszer fenntart egy **élő memóriát**, amely fejlődik és növekszik, miközben egy összekapcsolt gráfként kérdezhető marad, támogatva a rövid távú munkamenet kontextust és a hosszú távú tartós memóriát is.

A Cognee jegyzetfüzetes oktatóanyag ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) bemutatja ennek az egységes memória rétegnek az építését, gyakorlati példákkal a különféle adatforrások bevitelére, a tudásgráf vizualizálására, és a lekérdezésre különböző keresési stratégiákkal, testre szabva az ügynök specifikus igényeihez.

### Memória tárolása RAG-gal

A specializált memóriaeszközökön túl, mint a Mem0, használhatsz megbízható keresési szolgáltatásokat, például az **Azure AI Search-t mint háttérrendszert a memóriák tárolására és előhívására**, különösen a strukturált RAG esetében.

Ez lehetővé teszi, hogy az ügynök válaszait a saját adatbázisodhoz kösd, így relevánsabb és pontosabb válaszok születnek. Az Azure AI Search használható egyedi felhasználói utazási emlékek, termékkatalógusok vagy bármilyen más domain-specifikus tudás tárolására.

Az Azure AI Search támogatja a **Strukturált RAG képességeket**, amelyek kiválóak sűrű, strukturált információk kinyerésére és előhívására nagy adatállományokból, például beszélgetési előzményekből, e-mailekből vagy akár képekből. Ez „emberfeletti pontosságot és találati arányt” biztosít az hagyományos szövegtördelésen és beágyazásokon alapuló megközelítésekkel szemben.

## Az AI Ügynökök Önfejlesztése

Az önfejlesztő ügynökökre jellemző minta egy **„tudásügynök”** bevezetése. Ez a különálló ügynök figyeli a fő beszélgetést a felhasználó és az elsődleges ügynök között. Feladata:

1. **Értékes információ azonosítása**: Megállapítani, hogy van-e a beszélgetésben olyan rész, amit érdemes általános tudásként vagy specifikus felhasználói preferenciaként elmenteni.

2. **Kinyerés és összefoglalás**: Kivonatolni a beszélgetésből a lényegi tanulást vagy preferenciát.

3. **Tárolás egy tudásbázisban**: Eltárolni ezt az információt, gyakran egy vektoradatbázisban, hogy később előhívható legyen.

4. **Jövőbeli lekérdezések támogatása**: Amikor a felhasználó új lekérdezést indít, a tudásügynök előhívja a releváns tárolt információkat és hozzáfűzi a felhasználói kérést, biztosítva a fontos kontextust az elsődleges ügynök számára (hasonlóan a RAG-hoz).

### Memória optimalizálások

• **Késleltetés kezelése**: Az interakciók lassulásának elkerülése érdekében eleinte egy olcsóbb, gyorsabb modellt lehet használni arra, hogy gyorsan ellenőrizze, érdemes-e tárolni vagy előhívni az információt, és csak szükség esetén hívja meg a bonyolultabb kinyerési/előhívási folyamatot.

• **Tudásbázis karbantartása**: Egy növekvő tudásbázis esetén a ritkábban használt információkat áthelyezhetik „hideg tárolóba” a költségek kezelése érdekében.

## Még több kérdésed van az ügynök memóriájáról?

Csatlakozz a [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) közösséghez, hogy találkozhass más tanulókkal, részt vehess az ügyfélfogadási órákon, és választ kapj AI Ügynökökkel kapcsolatos kérdéseidre.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Jogi nyilatkozat**:  
Ezt a dokumentumot az AI fordító szolgáltatás [Co-op Translator](https://github.com/Azure/co-op-translator) segítségével fordítottuk le. Habár igyekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatikus fordítások tartalmazhatnak hibákat vagy pontatlanságokat. A dokumentum eredeti, anyanyelvi változata tekintendő hivatalos forrásnak. Kritikus információk esetén szakmai, emberi fordítást javasolt igénybe venni. Nem vállalunk felelősséget a fordítás használatából eredő félreértésekért vagy téves értelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->