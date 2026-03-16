[![Többügynökös tervezés](../../../translated_images/hu/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Kattints a fenti képre a leckéhez tartozó videó megtekintéséhez)_

# Többügynökös tervezési minták

Amint elkezdesz dolgozni egy több ügynököt érintő projekten, meg kell fontolnod a többügynökös tervezési mintát. Azonban nem mindig egyértelmű, mikor érdemes áttérni több ügynökre és mik az előnyök.

## Bevezető

Ebben a leckében a következő kérdésekre keressük a választ:

- Milyen forgatókönyvekben alkalmazhatók a többügynökök?
- Milyen előnyei vannak a többügynökök használatának ahelyett, hogy egyetlen ügynök több feladatot végezne?
- Mik az építőkövei a többügynökös tervezési minta megvalósításának?
- Hogyan biztosítható a láthatóság arra vonatkozóan, hogy a több ügynök hogyan lép kölcsönhatásba egymással?

## Tanulási célok

Ezen lecke után képes leszel:

- Azonosítani azokat a helyzeteket, ahol a többügynökök alkalmazhatók
- Felismerni a többügynökök használatának előnyeit egyetlen ügynökhöz képest.
- Megérteni a többügynökös tervezési minta megvalósításának építőköveit.

Mi a nagyobb kép?

*A többügynökök egy tervezési minta, amely lehetővé teszi, hogy több ügynök együtt dolgozzon egy közös cél elérésén.* 

Ezt a mintát számos területen széles körben alkalmazzák, többek között a robotikában, autonóm rendszerekben és elosztott számítástechnikában.

## Forgatókönyvek, ahol a többügynökök alkalmazhatók

Mely forgatókönyvek esetén érdemes többügynökös megoldást alkalmazni? A válasz az, hogy sok olyan helyzet van, ahol több ügynök alkalmazása előnyös, különösen az alábbi esetekben:

- **Nagy munkaterhelés**: A nagy munkaterhelést kisebb feladatokra lehet bontani és különböző ügynökökhöz rendelni, ami párhuzamos feldolgozást és gyorsabb befejezést tesz lehetővé. Erre példa egy nagy adatfeldolgozási feladat.
- **Komplex feladatok**: A komplex feladatok, hasonlóan a nagy munkaterheléshez, kisebb alfeladatokra bonthatók, amelyeket különböző ügynökök végeznek, mindegyik egy adott aspektusra specializálódva. Jó példa erre az autonóm járművek esete, ahol külön ügynökök kezelik a navigációt, az akadályfelismerést és a kommunikációt a többi járművel.
- **Sokszínű szakértelem**: Különböző ügynökök különféle szakértelemmel rendelkezhetnek, így hatékonyabban tudják kezelni a feladat különböző aspektusait, mint egyetlen ügynök. Erre jó példa az egészségügy, ahol ügynökök kezelhetik a diagnosztikát, a kezelési terveket és a betegmegfigyelést.

## Többügynökök használatának előnyei egyetlen ügynökkel szemben

Egyetlen ügynök rendszere jól működhet egyszerű feladatoknál, de bonyolultabb feladatok esetén a több ügynök használata több előnnyel járhat:

- **Specializáció**: Minden ügynök egy adott feladatra specializálódhat. Az egyetlen ügynök specializáció hiánya azt jelenti, hogy van egy ügynököd, amely mindent meg tud csinálni, de összezavarodhat komplex feladatok esetén. Előfordulhat, hogy egy olyan feladatot végez el, amelyhez nem ő a legalkalmasabb.
- **Skálázhatóság**: A rendszer skálázása könnyebb több ügynök hozzáadásával, mint egyetlen ügynök túlterhelésével.
- **Hibatűrés**: Ha egy ügynök meghibásodik, a többi tovább működhet, biztosítva a rendszer megbízhatóságát.

Vegyünk egy példát: foglaljuk le egy felhasználó utazását. Egyetlen ügynöknek kellene kezelnie az utazásfoglalás minden aspektusát, a járatok keresésétől a hotelek és autóbérlések lefoglalásáig. Egyetlen ügynök megvalósításához az ügynöknek eszközökre lenne szüksége ezen feladatok kezeléséhez, ami összetett és monolitikus rendszert eredményezhet, amely nehezen karbantartható és skálázható. Egy többügynökös rendszer ezzel szemben különböző, járatkeresésre, hotelfoglalásra és autóbérlésre specializált ügynökökkel rendelkezhet. Ez modularitást, könnyebb karbantarthatóságot és skálázhatóságot eredményezne.

Hasonlítsuk ezt egy kis családi utazási irodaként működő ügynökséghez és egy franchise-ként működő utazási irodához. A kis családi iroda esetében egyetlen ügynök kezelné az utazásfoglalás minden aspektusát, míg a franchise esetében különböző ügynökök különböző aspektusokat intéznének.

## A többügynökös tervezési minta megvalósításának építőkövei

Mielőtt megvalósíthatod a többügynökös tervezési mintát, meg kell értened azokat az építőköveket, amelyek a mintát alkotják.

Tegyük ezt kézzelfoghatóbbá ismét az utazásfoglalás példáján keresztül. Ebben az esetben az építőkövek a következők lennének:

- **Ügynökök közötti kommunikáció**: A járatkereső, hotelfoglaló és autóbérlő ügynököknek kommunikálniuk és meg kell osztaniuk információkat a felhasználó preferenciáiról és korlátairól. El kell döntened a kommunikáció protokolljait és módszereit. Konkrétan ez azt jelenti, hogy a járatkereső ügynöknek kommunikálnia kell a hotelfoglaló ügynökkel, hogy a hotel ugyanazokra a dátumokra legyen lefoglalva, mint a járat. Ez azt jelenti, hogy az ügynököknek meg kell osztaniuk információt a felhasználó utazási dátumairól, tehát el kell döntened *mely ügynökök osztják meg az információt és hogyan*.
- **Koordinációs mechanizmusok**: Az ügynököknek koordinálniuk kell tevékenységüket annak biztosítása érdekében, hogy a felhasználó preferenciái és korlátai teljesüljenek. Egy felhasználói preferencia lehet például, hogy a felhasználó olyan hotelt szeretne, ami közel van a repülőtérhez, míg egy korlát lehet, hogy az autókölcsönzők csak a repülőtéren érhetők el. Ez azt jelenti, hogy a hotelfoglaló ügynöknek koordinálnia kell az autóbérlést intéző ügynökkel, hogy a felhasználó preferenciái és korlátai teljesüljenek. Ez azt jelenti, hogy el kell döntened *hogyan koordinálják az ügynökök a műveleteiket*.
- **Ügynök architektúra**: Az ügynököknek belső struktúrával kell rendelkezniük a döntéshozatalhoz és az interakciókból való tanuláshoz. Ez azt jelenti, hogy a járatkereső ügynöknek belső szerkezettel kell rendelkeznie ahhoz, hogy eldöntse, mely járatokat ajánlja a felhasználónak. Tehát el kell döntened *hogyan hoznak döntéseket az ügynökök és hogyan tanulnak a felhasználóval való interakcióikból*. Például az, hogy egy ügynök hogyan tanul és fejlődik, lehet, hogy a járatkereső ügynök egy gépi tanulási modellt használ a felhasználó korábbi preferenciái alapján történő járatajánláshoz.
- **Átláthatóság a többügynökös interakciókban**: Láthatósággal kell rendelkezned arra vonatkozóan, hogyan lépnek kölcsönhatásba egymással az ügynökök. Szükséged van eszközökre és technikákra az ügynöktevékenységek és interakciók nyomon követéséhez. Ez lehet naplózás és megfigyelési eszközök, vizualizációs eszközök és teljesítménymutatók formájában.
- **Többügynökös minták**: Különböző minták léteznek a többügynökös rendszerekhez, mint például a központosított, decentralizált és hibrid architektúrák. El kell döntened, melyik minta illik legjobban az esetedhez.
- **Ember a folyamatban**: A legtöbb esetben ember is részt vesz a folyamatban, és meg kell határoznod, hogy az ügynökök mikor kérjenek emberi beavatkozást. Ez lehet például akkor, ha a felhasználó egy konkrét hotelt vagy járatot kér, amit az ügynökök nem ajánlottak, vagy ha megerősítést kérnek a foglalás előtt.

## Átláthatóság a többügynökös interakciókban

Fontos, hogy láthatóságod legyen arra vonatkozóan, hogyan lépnek kölcsönhatásba egymással a különböző ügynökök. Ez az átláthatóság elengedhetetlen a hibakereséshez, optimalizáláshoz és a rendszer általános hatékonyságának biztosításához. Ennek eléréséhez eszközökre és technikákra van szükséged az ügynöktevékenységek és interakciók nyomon követéséhez. Ez lehet naplózás és megfigyelési eszközök, vizualizációs eszközök és teljesítménymutatók formájában.

Például egy felhasználó utazásának lefoglalása esetén lehet egy irányítópultod, amely megmutatja minden ügynök állapotát, a felhasználó preferenciáit és korlátait, valamint az ügynökök közötti interakciókat. Ez az irányítópult megmutathatja a felhasználó utazási dátumait, a járatügynök által ajánlott járatokat, a hoteldiget ajánló hotelügynök ajánlásait és az autóbérlő ügynök ajánlásait. Ez tiszta képet adna arról, hogyan lépnek kölcsönhatásba az ügynökök, és teljesülnek-e a felhasználó preferenciái és korlátai.

Nézzük meg részletesebben ezeket a szempontokat.

- **Naplózás és megfigyelési eszközök**: Szeretnéd, hogy minden ügynök minden végrehajtott műveletéről történjen naplózás. Egy naplóbejegyzés tárolhat információkat az ügynökről, amely végrehajtotta a műveletet, a végrehajtott műveletről, a művelet idejéről és a művelet eredményéről. Ezek az információk felhasználhatók hibakeresésre, optimalizálásra és egyéb célokra.
- **Vizualizációs eszközök**: A vizualizációs eszközök segíthetnek az ügynökök közötti interakciók intuitívabb megjelenítésében. Például lehet egy gráf, amely megmutatja az információ áramlását az ügynökök között. Ez segíthet azonosítani a torlódásokat, hatékonysági problémákat és egyéb rendszerszintű gondokat.
- **Teljesítménymutatók**: A teljesítménymutatók segíthetnek nyomon követni a többügynökös rendszer hatékonyságát. Például mérheted egy feladat elvégzéséhez szükséges időt, az egységnyi idő alatt teljesített feladatok számát és az ügynökök által adott ajánlások pontosságát. Ezek az adatok segíthetnek azonosítani a fejlesztendő területeket és optimalizálni a rendszert.

## Többügynökös minták

Merüljünk el néhány konkrét mintában, amelyeket többügynökös alkalmazások létrehozásához használhatunk. Íme néhány érdekes minta, amelyeket érdemes megfontolni:

### Csoportos csevegés

Ez a minta hasznos, amikor olyan csoportos csevegőalkalmazást szeretnél létrehozni, ahol több ügynök tud egymással kommunikálni. Tipikus felhasználási esetek erre a csapatmunka, ügyfélszolgálat és közösségi hálózatok.

Ebben a mintában minden ügynök egy felhasználót képvisel a csoportos csevegésben, és az üzeneteket üzenetküldő protokollon keresztül cserélik az ügynökök. Az ügynökök küldhetnek üzeneteket a csoportos csevegésnek, kaphatnak üzeneteket a csoporttól, és válaszolhatnak más ügynökök üzeneteire.

Ez a minta megvalósítható központosított architektúrával, ahol minden üzenet egy központi szerveren keresztül fut, vagy decentralizált architektúrával, ahol az üzenetek közvetlenül cserélődnek.

![Csoportos csevegés](../../../translated_images/hu/multi-agent-group-chat.ec10f4cde556babd.webp)

### Feladatátadás

Ez a minta akkor hasznos, amikor olyan alkalmazást szeretnél létrehozni, ahol több ügynök adhatja át egymásnak a feladatokat.

Tipikus felhasználási esetek erre az ügyfélszolgálat, feladatkezelés és munkafolyamat-automatizálás.

Ebben a mintában minden ügynök egy feladatot vagy munkafolyamat lépését képviseli, és az ügynökök előre meghatározott szabályok alapján adhatják át a feladatokat más ügynököknek.

![Feladatátadás](../../../translated_images/hu/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Kollaboratív szűrés

Ez a minta akkor hasznos, amikor olyan alkalmazást szeretnél létrehozni, ahol több ügynök együttműködve adhat ajánlásokat a felhasználóknak.

Azért érdemes több ügynököt bevonni az együttműködésbe, mert minden ügynök más szakértelemmel rendelkezhet, és különböző módon járulhat hozzá az ajánlási folyamathoz.

Vegyünk egy példát, ahol egy felhasználó azt kéri, ajánljuk meg, melyik részvényt érdemes megvenni a tőzsdén.

- **Iparági szakértő**:. Egy ügynök lehet egy adott iparág szakértője.
- **Technikai elemzés**: Egy másik ügynök lehet a technikai elemzés szakértője.
- **Fundamentális elemzés**: és egy harmadik ügynök lehet a fundamentális elemzés szakértője. Az együttműködés révén ezek az ügynökök átfogóbb ajánlást tudnak adni a felhasználónak.

![Ajánlás](../../../translated_images/hu/multi-agent-filtering.d959cb129dc9f608.webp)

## Forgatókönyv: Visszatérítési folyamat

Tekintsünk egy olyan forgatókönyvre, ahol egy ügyfél visszatérítést próbál kérni egy termékre; ebben a folyamatban több ügynök is részt vehet, de osszuk fel őket a visszatérítési folyamathoz specifikus ügynökökre és azokra az általános ügynökökre, amelyek más folyamatokban is használhatók.

**Visszatérítési folyamathoz kapcsolódó ügynökök**:

Az alábbiakban néhány ügynök, amelyek részt vehetnek a visszatérítési folyamatban:

- **Ügyfélügynök**: Ez az ügynök az ügyfelet képviseli és felelős a visszatérítési folyamat kezdeményezéséért.
- **Eladóügynök**: Ez az ügynök az eladót képviseli és felelős a visszatérítés feldolgozásáért.
- **Fizetési ügynök**: Ez az ügynök a fizetési folyamatot képviseli, és felelős az ügyfél kifizetésének visszatérítéséért.
- **Megoldási ügynök**: Ez az ügynök a problémamegoldási folyamatot képviseli, és felelős a visszatérítési folyamat során felmerülő problémák rendezéséért.
- **Megfelelőségi ügynök**: Ez az ügynök a megfelelőségi folyamatot képviseli, és felelős annak biztosításáért, hogy a visszatérítési folyamat megfeleljen a szabályozásoknak és irányelveknek.

**Általános ügynökök**:

Ezek az ügynökök más üzleti területeken is használhatók.

- **Szállítási ügynök**: Ez az ügynök a szállítási folyamatot képviseli és felelős a termék visszaküldéséért az eladóhoz. Ezt az ügynököt használhatod a visszatérítési folyamatban és általános termékszállításoknál is, például vásárlás esetén.
- **Visszajelzés ügynök**: Ez az ügynök a visszajelzési folyamatot képviseli és felelős az ügyféltől érkező visszajelzések gyűjtéséért. Visszajelzést bármikor lehet kérni, nem csak a visszatérítési folyamat során.
- **Eszkalációs ügynök**: Ez az ügynök az eszkalációs folyamatot képviseli és felelős a problémák magasabb szintű támogatáshoz történő továbbításáért. Ezt a típusú ügynököt bármely olyan folyamatnál használhatod, ahol szükség van ügyek eszkalálására.
- **Értesítési ügynök**: Ez az ügynök az értesítési folyamatot képviseli és felelős értesítések küldéséért az ügyfélnek a visszatérítési folyamat különböző szakaszaiban.
- **Analitikai ügynök**: Ez az ügynök az analitikai folyamatot képviseli és felelős a visszatérítési folyamathoz kapcsolódó adatok elemzéséért.
- **Audit ügynök**: Ez az ügynök az auditálási folyamatot képviseli és felelős a visszatérítési folyamat ellenőrzéséért, hogy az megfelelően történik-e.
- **Jelentéskészítő ügynök**: Ez az ügynök a jelentéskészítési folyamatot képviseli és felelős a visszatérítési folyamatról készített jelentések generálásáért.
- **Tudásügynök**: Ez az ügynök a tudáskezelési folyamatot képviseli és felelős a visszatérítési folyamathoz kapcsolódó tudásbázis karbantartásáért. Ez az ügynök ismeretekkel rendelkezhet mind a visszatérítésekről, mind az üzleted egyéb részeiről.
- **Biztonsági ügynök**: Ez az ügynök a biztonsági folyamatot képviseli és felelős a visszatérítési folyamat biztonságának biztosításáért.
- **Minőségügyi ügynök**: Ez az ügynök a minőségbiztosítási folyamatot képviseli és felelős a visszatérítési folyamat minőségének biztosításáért.

Korábban elég sok ügynököt soroltunk fel, mind a visszatérítési folyamathoz specifikusakat, mind az általános, más üzleti területeken is használható ügynököket. Remélhetőleg ez ad egy ötletet arról, hogyan dönthetsz arról, mely ügynököket érdemes használni a többügynökös rendszeredben.

## Feladat

Tervezz egy többügynökös rendszert egy ügyfélszolgálati folyamathoz. Azonosítsd a folyamatban részt vevő ügynököket, azok szerepét és felelősségét, valamint azt, hogyan lépnek kölcsönhatásba egymással. Vedd figyelembe mind az ügyfélszolgálati folyamathoz specifikus ügynököket, mind azokat az általános ügynököket, amelyeket az üzleted más részein is felhasználhatsz.
> Gondolkodj el rajta, mielőtt elolvasod a következő megoldást, lehet, hogy több ügynökre lesz szükséged, mint gondolnád.
>
> TIPP: Gondolj az ügyfélszolgálati folyamat különböző szakaszaira, és vedd figyelembe az adott rendszerhez szükséges ügynököket is.

## Solution

[Megoldás](./solution/solution.md)

## Knowledge checks

Kérdés: Mikor érdemes többügynökös megoldást alkalmazni?

- [ ] A1: Ha kis a munkaterhelés és egyszerű a feladat.
- [ ] A2: Ha nagy a munkaterhelés
- [ ] A3: Ha egyszerű a feladat.

[Megoldás kvíz](./solution/solution-quiz.md)

## Summary

Ebben a leckében áttekintettük a többügynökös tervezési mintát, beleértve azokat a helyzeteket, amikor a többügynökös megoldások alkalmazhatók, a többügynökös megközelítés előnyeit az egyetlen ügynökhöz képest, a többügynökös tervezési minta megvalósításának építőköveit, és azt, hogyan biztosíthatunk átláthatóságot arra vonatkozóan, hogyan lépnek kölcsönhatásba egymással az ügynökök.

### Van még kérdésed a többügynökös tervezési mintával kapcsolatban?

Csatlakozz a [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) közösséghez, hogy találkozz más tanulókkal, részt vehess fogadóórákon, és választ kapj az AI-ügynökökkel kapcsolatos kérdéseidre.

## Additional resources

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen tervezési minták</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentikus tervezési minták</a>


## Previous Lesson

[Tervezés és dizájn](../07-planning-design/README.md)

## Next Lesson

[Metakogníció az AI-ügynökökben](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Felelősségkizárás:
Ezt a dokumentumot az AI fordító szolgáltatás, a Co-op Translator (https://github.com/Azure/co-op-translator) segítségével fordítottuk. Bár igyekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti, anyanyelvű dokumentum tekintendő irányadónak. Fontos információk esetén professzionális, emberi fordítást javasolunk. Nem vállalunk felelősséget a fordítás használatából eredő félreértésekért vagy téves értelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->