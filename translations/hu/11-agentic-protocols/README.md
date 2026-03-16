# Ügynöki protokollok használata (MCP, A2A és NLWeb)

[![Agentic Protocols](../../../translated_images/hu/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Kattintson a fenti képre az óra videójának megtekintéséhez)_

Ahogy az AI ügynökök használata növekszik, úgy nő az olyan protokollok iránti igény is, amelyek biztosítják a szabványosítást, a biztonságot és támogatják a nyílt innovációt. Ebben az órában három protokollal foglalkozunk, amelyek ezt az igényt hivatottak kielégíteni - Model Context Protocol (MCP), Agent to Agent (A2A) és Natural Language Web (NLWeb).

## Bevezetés

Ebben az órában érintjük:

• Hogyan teszi lehetővé a **MCP**, hogy az AI ügynökök külső eszközökhöz és adatokhoz férjenek hozzá a felhasználói feladatok elvégzéséhez.

• Hogyan teszi lehetővé az **A2A** a kommunikációt és együttműködést különböző AI ügynökök között.

• Hogyan hozza el az **NLWeb** a természetes nyelvi felületeket bármely weboldalra, lehetővé téve az AI ügynökök számára a tartalom felfedezését és interakcióját.

## Tanulási célok

• **Azonosítani** az MCP, A2A és NLWeb központi célját és előnyeit az AI ügynökök kontextusában.

• **Megmagyarázni**, hogy az egyes protokollok hogyan könnyítik meg a kommunikációt és az interakciót a nagy nyelvi modellek (LLM-ek), eszközök és más ügynökök között.

• **Felcímkézni** az egyes protokollok konkrét szerepét a komplex ügynöki rendszerek felépítésében.

## Model Context Protocol

A **Model Context Protocol (MCP)** egy nyílt szabvány, amely szabványosított módot biztosít az alkalmazásoknak, hogy kontextust és eszközöket biztosítsanak az LLM-ek számára. Ez lehetővé tesz egy "univerzális adaptert" a különböző adatforrásokhoz és eszközökhöz, amelyeket az AI ügynökök következetes módon használhatnak.

Nézzük meg az MCP összetevőit, az előnyöket a közvetlen API használathoz képest, és egy példát arra, hogyan használhatják az AI ügynökök az MCP szervert.

### Az MCP alapvető összetevői

Az MCP egy **kliens-szerver architektúrán** alapul, és az alapvető összetevők:

• **Hostok**: Ezek LLM alkalmazások (például egy kódszerkesztő, mint a VSCode), amelyek elindítják a kapcsolatokat egy MCP szerverhez.

• **Kliens komponensek**: Ezek a host alkalmazáson belüli elemek, amelyek egy-egy kapcsolatot tartanak fenn a szerverekkel.

• **Szerverek**: Könnyűsúlyú programok, amelyek meghatározott képességeket kínálnak.

A protokoll három alapvető primitívet tartalmaz, amelyek egy MCP szerver képességei:

• **Eszközök**: Olyan diszkrét akciók vagy funkciók, amelyeket az AI ügynök hívhat meg egy adott művelet végrehajtásához. Például egy időjárás szolgáltatás kínálhat "időjárás lekérése" eszközt, vagy egy e-kereskedelmi szerver kitettséget nyújthat "termék vásárlása" eszközként. Az MCP szerverek minden eszköz nevét, leírását és input/output sémáját meghirdetik képességeik listáján.

• **Erőforrások**: Olyan olvasható adat elemek vagy dokumentumok, amelyeket egy MCP szerver biztosíthat, és amelyeket a kliensek igény szerint lekérhetnek. Példák: fájl tartalmak, adatbázis rekordok vagy naplófájlok. Az erőforrások lehetnek szövegesek (például kód vagy JSON) vagy binárisak (például képek vagy PDF-ek).

• **Kezdeményezők (Prompts)**: Előre definiált sablonok, amelyek javasolt kezdő szöveget biztosítanak, lehetővé téve összetettebb munkafolyamatokat.

### Az MCP előnyei

Az MCP jelentős előnyöket kínál az AI ügynökök számára:

• **Dinamikus eszköz felfedezés**: Az ügynökök dinamikusan kapnak listát az elérhető eszközökről és azok leírásáról. Ez ellentétben áll a hagyományos API-kkal, amelyek gyakran statikus kódolást igényelnek az integrációknál, így bármely API-változás kódfrissítést tesz szükségessé. Az MCP az "egyszer integrál" megközelítést kínálja, ami nagyobb alkalmazkodóképességet eredményez.

• **Közvetlen együttműködés különböző LLM-ek között**: Az MCP többféle LLM-mel is működik, így rugalmasságot biztosítva a jobb teljesítmény érdekében a modellcserére.

• **Szabványos biztonság**: Az MCP tartalmaz egy szabványos hitelesítési módszert, amely egyszerűbbé teszi az új MCP szerverek hozzáadását a hozzáférés bővítésekor. Ez egyszerűbb, mint több hagyományos API különböző kulcsainak és hitelesítési módjainak kezelése.

### MCP példa

![MCP Diagram](../../../translated_images/hu/mcp-diagram.e4ca1cbd551444a1.webp)

Képzeljük el, hogy egy felhasználó repülőjegy foglaláshoz AI asszisztenshez fordul, amely MCP-t használ.

1. **Kapcsolódás**: Az AI asszisztens (az MCP kliens) csatlakozik egy repülőjáratokat kínáló légitársaság MCP szerveréhez.

2. **Eszköz felfedezés**: A kliens azt kérdezi a légitársaság MCP szerverétől, "Milyen eszközeitek vannak?" A szerver válasza tartalmazza az olyan eszközöket, mint "járatok keresése" és "járatok foglalása".

3. **Eszköz meghívása**: Ezután a felhasználó megkéri az AI asszisztenst, hogy "Kérlek, keress járatot Portlandből Honolulu-ba." Az AI asszisztens LLM-jével felismeri, hogy meg kell hívnia a "járatok keresése" eszközt, és átadja a megfelelő paramétereket (indulási és érkezési hely) az MCP szervernek.

4. **Végrehajtás és válasz**: Az MCP szerver, mint "burkoló", ténylegesen meghívja a légitársaság belső foglalási API-ját. Ezután megkapja a járatinformációkat (pl. JSON adatokat) és visszaküldi az AI asszisztensnek.

5. **További interakció**: Az AI asszisztens megjeleníti a járat opciókat. Ha a felhasználó kiválaszt egy járatot, az asszisztens meghívhatja a "járat foglalása" eszközt ugyanazon MCP szerveren, ezzel befejezve a foglalást.

## Agent-to-Agent protokoll (A2A)

Míg az MCP az LLM-ek és az eszközök összekapcsolására koncentrál, az **Agent-to-Agent (A2A) protokoll** tovább lép azzal, hogy lehetővé teszi a kommunikációt és együttműködést különböző AI ügynökök között. Az A2A összeköti az AI ügynököket különböző szervezetek, környezetek és technológiai környezetek között egy közös feladat elvégzésére.

Megvizsgáljuk az A2A összetevőit és előnyeit, valamint egy példát arra, hogyan alkalmazható ez utazási alkalmazásunkban.

### Az A2A alapvető összetevői

Az A2A az ügynökök közötti kommunikáció lehetővé tételére és együttműködésére fókuszálva minden protokoll komponens ezt támogatja:

#### Agent Card

Hasonlóan ahhoz, hogy az MCP szerver megosztja az eszközök listáját, az Agent Card tartalmazza:  
- Az Ügynök nevét.  
- Általános feladatok **leírását**, amelyeket elvégez.  
- Egy **speciális képességek listáját** leírásokkal, hogy más ügynökök (vagy akár emberi felhasználók) megértsék, mikor és miért érdemes azt az ügynököt hívni.  
- Az ügynök **aktuális végpont URL-jét**.  
- Az ügynök **verzióját** és **képességeit**, mint például az adatfolyam válaszokat és a push értesítéseket.

#### Agent Executor

Az Agent Executor felelős a **felhasználói beszélgetés kontextusának átadásáért a távoli ügynöknek**, amelynek ehhez szüksége van, hogy megértse a végrehajtandó feladatot. Egy A2A szerveren az ügynök saját nagy nyelvi modelljét (LLM) használja a bejövő kérések elemzésére és a saját belső eszközeivel végzi el a feladatokat.

#### Artifact

Miután a távoli ügynök befejezi a kért feladatot, a munkája eredménye egy artifactként jön létre. Egy artifact **tartalmazza az ügynök munkájának eredményét**, egy leírást arról, mi készült el, és a protokollon keresztül továbbított szöveges kontextust. Az artifact elküldése után a távoli ügynökkel fenntartott kapcsolat lezárul, amíg ismét szükség nem lesz rá.

#### Event Queue

Ez az összetevő a **frissítések kezelésére és üzenetek továbbítására szolgál**. Különösen fontos a termelési ügynöki rendszerekben, hogy megakadályozza a kapcsolat lezárását a feladat befejezése előtt, különösen, ha a feladatok befejezése hosszabb időt vesz igénybe.

### Az A2A előnyei

• **Fokozott együttműködés**: Lehetővé teszi, hogy különböző szállítók és platformok ügynökei kommunikáljanak, megosszák a kontextust és együtt dolgozzanak, támogatva az automatizációt tradicionálisan különálló rendszerek között.

• **Rugalmasság a modellválasztásban**: Minden A2A ügynök eldöntheti, melyik LLM-et használja a kérések kiszolgálására, így optimalizált vagy finomhangolt modelleket alkalmazhat, ellentétben az MCP egyetlen LLM kapcsolódásával.

• **Beépített hitelesítés**: A hitelesítés közvetlenül az A2A protokoll része, erős biztonsági keretet adva az ügynöki interakciókhoz.

### A2A példa

![A2A Diagram](../../../translated_images/hu/A2A-Diagram.8666928d648acc26.webp)

Fejlesszük tovább utazási foglalási forgatókönyvünket, de most A2A-t használva.

1. **Felhasználói kérés többrésztvevős ügynökhöz**: Egy felhasználó egy "Travel Agent" A2A klienssel/ügynökkel kommunikál, például így: "Kérlek, foglalj le egy teljes utazást Honolulu-ba jövő hétre, beleértve a repülőjegyeket, szállodát és autóbérlést."

2. **Utazási ügynök összefogása**: Az utazási ügynök megkapja ezt a komplex kérést. LLM-jével átgondolja a feladatot és meghatározza, hogy más specializált ügynökökkel kell együttműködnie.

3. **Ügynökök közötti kommunikáció**: Az utazási ügynök az A2A protokollt használva kapcsolódik az alárendelt ügynökökhöz, például egy "Repülőtéri ügynök", egy "Szálloda ügynök" és egy "Autóbérlés ügynök", amelyek különböző cégek által készültek.

4. **Feladat delegálás**: Az utazási ügynök adott feladatokat küld ezeknek a specializált ügynököknek ("Keress járatokat Honolulu-ba", "Foglalj szállodát", "Bérelj autót"). Mindegyik ügynök a saját LLM-jét futtatja és a saját eszközeit (például MCP szervereket) használja a foglalás adott részének elvégzésére.

5. **Összesített válaszadás**: Miután az alárendelt ügynökök befejezték feladataikat, az utazási ügynök összefoglalja az eredményeket (járatinformációkat, szállodai visszaigazolást, autókölcsönzést) és egy csevegés-stílusú, átfogó válasz formájában elküldi a felhasználónak.

## Natural Language Web (NLWeb)

A weboldalak régóta elsődleges módját jelentik a felhasználók számára az információ és adatok elérésének az interneten.

Nézzük meg az NLWeb különböző összetevőit, előnyeit és egy példát arra, hogyan működik az NLWeb az utazási alkalmazásunk esetében.

### Az NLWeb összetevői

- **NLWeb alkalmazás (mag szolgáltatáskód)**: Az a rendszer, amely feldolgozza a természetes nyelvű kérdéseket. Kapcsolja a platform különböző részeit a válaszok létrehozására. Gondolhatunk rá úgy, mint egy **motorra, amely a weboldal természetes nyelvű funkcióit működteti**.

- **NLWeb protokoll**: Ez egy **alapvető szabálykészlet a természetes nyelvi interakcióhoz** egy weboldallal. Válaszokat JSON formátumban küld vissza (gyakran Schema.org használatával). Célja egy egyszerű alap megteremtése az „AI webhez”, ahogy a HTML tette lehetővé a dokumentumok online megosztását.

- **MCP szerver (Model Context Protocol végpont)**: Minden NLWeb telepítés MCP szerverként is működik. Ez azt jelenti, hogy képes **eszközöket (például egy “ask” metódust) és adatokat megosztani** más AI rendszerekkel. Gyakorlatban ez lehetővé teszi, hogy a weboldal tartalma és képességei AI ügynökök számára is használhatóak legyenek, így a webhely az “ügynök ökoszisztéma” részévé válhat.

- **Beágyazó modellek**: Ezek a modellek arra szolgálnak, hogy a weboldal tartalmát numerikus ábrázolássá (vektorokká, beágyazásokká) alakítsák át. Ezek a vektorok olyan jelentést rögzítenek, amelyet a számítógépek összehasonlíthatnak és kereshetnek benne. Ezeket egy speciális adatbázisban tárolják, és a felhasználók választhatják ki, mely beágyazó modellt szeretnék használni.

- **Vektor adatbázis (visszakereső mechanizmus)**: Ez az adatbázis tárolja a weboldal tartalmának beágyazásait. Amikor valaki kérdést tesz fel, az NLWeb ellenőrzi a vektor adatbázist, hogy gyorsan megtalálja a legrelevánsabb információkat. Egy gyors listát ad lehetséges válaszokról, amelyeket hasonlóság alapján rangsorol. Az NLWeb különböző vektor tároló rendszerekkel működik, mint például Qdrant, Snowflake, Milvus, Azure AI Search és Elasticsearch.

### Az NLWeb példán keresztül

![NLWeb](../../../translated_images/hu/nlweb-diagram.c1e2390b310e5fe4.webp)

Vegyük ismét az utazási foglalási weboldalunkat, de most NLWeb által működtetve.

1. **Adatfeldolgozás**: Az utazási weboldal meglévő termékkatalógusai (pl. járatlisták, szállodaleírások, túra csomagok) Schema.org segítségével vannak formázva vagy RSS feedeken keresztül betöltve. Az NLWeb eszközök felveszik ezeket a strukturált adatokat, beágyazásokat hoznak létre, majd egy helyi vagy távoli vektor adatbázisban tárolják.

2. **Természetes nyelvi lekérdezés (ember)**: Egy felhasználó ellátogat az oldalra, és menük böngészése helyett beír a chat felületbe egy kérést: „Keress nekem egy családbarát szállodát Honolulu-ban medencével a jövő hétre.”

3. **NLWeb feldolgozás**: Az NLWeb alkalmazás megkapja ezt a lekérdezést. Elküldi azt egy LLM-nek megértés céljából, miközben párhuzamosan keres a vektor adatbázisában releváns szállodai ajánlatokat.

4. **Pontos eredmények**: Az LLM segít az adatbázisból származó keresési eredmények értelmezésében, kiválasztja a legjobb találatokat a „családbarát”, „medence” és „Honolulu” kritériumok alapján, majd természetes nyelvű választ formáz. Fontos, hogy a válasz tényleges szállodákra hivatkozik az oldal katalógusából, elkerülve a kitalált információkat.

5. **AI ügynök interakció**: Mivel az NLWeb MCP szerverként is működik, egy külső AI utazási ügynök is kapcsolódhat a weboldal NLWeb példányához. Az AI ügynök így az `ask` MCP metódust használhatja a weboldal közvetlen lekérdezésére: `ask("Ajánlanak-e a szállodák vegánbarát éttermeket a Honolulu környékén?")`. Az NLWeb ezt feldolgozza, a szálloda információkat tartalmazó adatbázisra hivatkozva, és strukturált JSON választ ad vissza.

### Több kérdésed van az MCP/A2A/NLWeb-ről?

Csatlakozz a [Microsoft Foundry Discordhoz](https://aka.ms/ai-agents/discord), hogy más tanulókkal találkozz, részt vegyél konzultációkon és választ kapj AI ügynökkel kapcsolatos kérdéseidre.

## Források

- [MCP kezdőknek](https://aka.ms/mcp-for-beginners)  
- [MCP dokumentáció](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)  
- [NLWeb tárház](https://github.com/nlweb-ai/NLWeb)  
- [Semantic Kernel útmutatók](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Jogi nyilatkozat**:
Ez a dokumentum az AI fordító szolgáltatás, a [Co-op Translator](https://github.com/Azure/co-op-translator) segítségével készült. Bár az pontosságra törekszünk, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti dokumentum az anyanyelvén tekintendő hiteles forrásnak. Fontos információk esetén professzionális emberi fordítást javaslunk. Nem vállalunk felelősséget a fordítás használatából eredő félreértésekért vagy félrefordításokért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->