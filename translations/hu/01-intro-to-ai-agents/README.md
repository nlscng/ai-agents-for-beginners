[![Bevezetés az AI ügynökökhöz](../../../translated_images/hu/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(A fenti képre kattintva megtekintheti az óra videóját)_


# Bevezetés az AI ügynökökbe és ügynök-alapú felhasználási esetekbe

Üdvözlünk az „AI ügynökök kezdőknek” tanfolyamon! Ez a tanfolyam alapvető ismereteket és alkalmazási példákat kínál AI ügynökök építéséhez.

Csatlakozz az <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord közösséghez</a>, hogy találkozz más tanulókkal és AI Ügynök fejlesztőkkel, és feltehesd kérdéseidet ezzel a tanfolyammal kapcsolatban.

A tanfolyamot azzal kezdjük, hogy jobban megértjük, mik azok az AI ügynökök, és hogyan használhatjuk őket az általunk épített alkalmazásokban és munkafolyamatokban.

## Bevezetés

Ez az óra a következőket tárgyalja:

- Mik azok az AI ügynökök és milyen különböző típusai vannak az ügynököknek?
- Milyen felhasználási esetekhez a legalkalmasabbak az AI ügynökök, és hogyan segíthetnek nekünk?
- Mik az alapvető építőelemek ügynöki megoldások tervezésekor?

## Tanulási célok
Az óra elvégzése után képes leszel:

- Megérteni az AI ügynökök fogalmait és hogy miben különböznek más AI megoldásoktól.
- A leghatékonyabban alkalmazni az AI ügynököket.
- Produktívan tervezni ügynöki megoldásokat mind felhasználók, mind ügyfelek számára.

## Az AI ügynökök meghatározása és az AI ügynökök típusai

### Mik azok az AI ügynökök?

Az AI ügynökök olyan **rendszerek**, melyek lehetővé teszik a **nagy nyelvi modelleknek (LLM-eknek)**, hogy **műveleteket hajtsanak végre** azzal, hogy bővítik képességeiket eszközökhöz való **hozzáféréssel** és **tudással**.

Nézzük meg ezt a meghatározást kisebb részekre bontva:

- **Rendszer** – Fontos, hogy az ügynököket ne egyetlen komponensként, hanem több komponensből álló rendszerként tekintsük. Alapvető szinten az AI Ügynök komponensei:
  - **Környezet** – Az a meghatározott tér, ahol az AI Ügynök működik. Például ha egy utazási foglaló AI ügynökünk van, a környezet lehet maga az utazási foglaló rendszer, amelyet az ügynök a feladatok elvégzésére használ.
  - **Érzékelők** – A környezet információkat tartalmaz és visszajelzést ad. Az AI ügynök érzékelőket használ az aktuális környezeti állapot információinak összegyűjtésére és értelmezésére. Az utazási foglaló ügynök esetében az utazási rendszer például szolgáltathat adatokat a szállodák elérhetőségéről vagy a repülőjegy árakról.
  - **Beavatkozók** – Miután az AI ügynök megkapja az aktuális környezeti állapotot, az adott feladathoz meghatározza, milyen műveletet hajtson végre a környezet megváltoztatásához. Az utazási foglaló ügynök például lefoglalhat egy elérhető szobát a felhasználó számára.

![Mik azok az AI ügynökök?](../../../translated_images/hu/what-are-ai-agents.1ec8c4d548af601a.webp)

**Nagy nyelvi modellek** – Az ügynökök fogalma a LLM-ek létrejötte előtt is létezett. Az AI ügynökök LLM-ekkel történő létrehozásának előnye az emberi nyelv és adatértelmezési képességük. Ez a képesség lehetővé teszi a LLM-ek számára, hogy értelmezzék a környezeti információkat és tervezzék meg a környezet megváltoztatását.

**Műveletek végrehajtása** – Az AI ügynök rendszereken kívül a LLM-ek csak olyan helyzetekben képesek műveleteket végrehajtani, ahol a művelet tartalom vagy információ generálása a felhasználó által megadott prompt alapján. Az AI ügynök rendszerekben a LLM-ek feladatokat végeznek el a felhasználói kérés értelmezésével, és a környezetükben rendelkezésre álló eszközök használatával.

**Eszközökhöz való hozzáférés** – Az, hogy a LLM milyen eszközökhöz fér hozzá, két tényező határozza meg: 1) a környezet, ahol működik és 2) az AI ügynök fejlesztője. Utazási ügynök példánkban az ügynök eszközeit a foglalási rendszerben elérhető műveletek korlátozzák, illetve a fejlesztő szűkítheti az eszközhasználatot például csak repülőjegyekre.

**Memória + Tudás** – A memória lehet rövid távú, a felhasználó és az ügynök közötti beszélgetés kontextusában. Hosszú távon, a környezet által nyújtott információn túl, az AI ügynökök más rendszerekből, szolgáltatásokból, eszközökből és akár más ügynököktől is képesek tudást lekérni. Az utazási ügynök példájában ez lehet a felhasználó utazási preferenciáit tartalmazó ügyféladatbázis.

### Az ügynökök különböző típusai

Most, hogy van egy általános meghatározásunk az AI ügynökökről, nézzünk meg néhány speciális ügynök típust, és hogyan alkalmazhatók egy utazási foglaló AI ügynök esetében.

| **Ügynök típus**              | **Leírás**                                                                                                                          | **Példa**                                                                                                                                                                                                                   |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Egyszerű reflex ügynökök**  | Előre definiált szabályok alapján azonnali műveleteket hajtanak végre.                                                             | Az utazási ügynök értelmezi az e-mail kontextusát és továbbítja az utazási panaszokat az ügyfélszolgálathoz.                                                                                                                   |
| **Modellalapú reflex ügynökök** | A világmodell alapján, és annak változásaira reagálva hajtanak végre műveleteket.                                                 | Az utazási ügynök az előzményár-adatok alapján előnyben részesíti az olyan útvonalakat, ahol jelentős ármozgások történtek.                                                                                                  |
| **Cél-alapú ügynökök**        | Terveket készítenek egy adott cél elérésére, értelmezve a célt és meghatározva az eléréshez szükséges lépéseket.                     | Az utazási ügynök megtervezi az utazást az indulási helytől a célállomásig szükséges közlekedési módok (autó, tömegközlekedés, repülőjáratok) foglalásával.                                                                        |
| **Hasznosság-alapú ügynökök** | Preferenciákat mérlegelnek és numerikusan értékelik az alternatívákat a célok eléréséhez.                                           | Az utazási ügynök kényelmi és költségbeli szempontokat mérlegelve maximalizálja a hasznosságot az utazás foglalásakor.                                                                                                        |
| **Tanuló ügynökök**           | Visszacsatolás alapján folyamatosan javulnak és igazítják a műveleteket ennek megfelelően.                                          | Az utazási ügynök a felhasználói visszajelzések alapján utólagos felmérésekből tanul és módosítja a jövőbeni foglalásokat.                                                                                                   |
| **Hierarchikus ügynökök**    | Több ügynök tagozódik hierarchikus rendszerbe, a magasabb szintű ügynök feladatokat bont alfeladatokra, amelyeket alacsonyabb szintű ügynökök végeznek el. | Az utazási ügynök egy utat lemond úgy, hogy a feladatot több részfeladatra bontja (például egyes foglalások törlése), amelyeket alacsonyabb szintű ügynökök végeznek el, és visszajelzést adnak a felsőbb szintű ügynöknek.            |
| **Több-ügynökös rendszerek (MAS)** | Az ügynökök önállóan, vagy együttműködve, vagy versengve teljesítik a feladatokat.                                                 | Együttműködés: Több ügynök egyes utazási szolgáltatásokat (szállás, repülőjegy, program) foglal. Versengés: Több ügynök osztozik és verseng egy közös szállodai foglalási naptáron, hogy ügyfeleket helyezzen el a szállodában. |

## Mikor használjuk az AI ügynököket?

Korábban az utazási ügynök példán keresztül magyaráztuk meg, hogy hogyan alkalmazhatók a különböző ügynök típusok az utazásfoglalás eltérő szcenárióiban. A képzés során továbbra is ezt az alkalmazást fogjuk használni.

Nézzük meg azokat a felhasználási eseteket, amelyekhez az AI ügynökök a legalkalmasabbak:

![Mikor használjuk az AI ügynököket?](../../../translated_images/hu/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Nyitott problémák** – ahol a LLM határozza meg a szükséges lépéseket a feladat végrehajtásához, mert ezt nem lehet előre fixen beprogramozni a munkafolyamatba.
- **Többlépcsős folyamatok** – olyan feladatok, amelyek összetettségük miatt igénylik, hogy az AI ügynök több lépésen keresztül használjon eszközöket vagy információkat az egyszeri adatlekérés helyett.
- **Idővel történő javulás** – olyan feladatok, ahol az ügynök visszajelzések alapján tud fejlődni, akár a környezetéből, akár a felhasználóktól kapott visszacsatolással, hogy jobb hasznosságot biztosítson.

Az AI ügynökök használatának további szempontjait a Megbízható AI ügynökök építése leckében tárgyaljuk.

## Ügynöki megoldások alapjai

### Ügynök fejlesztés

Az AI ügynök rendszer tervezésének első lépése a használandó eszközök, műveletek és viselkedések meghatározása. Ebben a tanfolyamban az **Azure AI Agent Service** használatára fókuszálunk az ügynökök meghatározásához. Ez a szolgáltatás a következőket kínálja:

- Nyílt modellek kiválasztása, mint például OpenAI, Mistral, és Llama
- Licencelt adatok használata olyan szolgáltatóktól, mint a Tripadvisor
- Szabványosított OpenAPI 3.0 eszközök alkalmazása

### Ügynöki minták

A LLM-ekkel való kommunikáció promptokon keresztül történik. Az AI ügynökök félönálló jellege miatt nem mindig lehetséges vagy szükséges a LLM-et manuálisan újrapromptolni egy környezeti változás után. Olyan **ügynöki mintákat** használunk, amelyek lehetővé teszik a LLM több lépésen át tartó skálázható promptolását.

Ez a tanfolyam néhány jelenleg népszerű ügynöki mintára oszlik.

### Ügynöki keretrendszerek

Az ügynöki keretrendszerek lehetővé teszik a fejlesztők számára, hogy kódon keresztül valósítsák meg az ügynöki mintákat. Ezek a keretrendszerek sablonokat, bővítményeket és eszközöket kínálnak az AI ügynökök jobb együttműködéséhez. Ezek az előnyök jobb megfigyelhetőséget és hibakeresést biztosítanak az AI ügynök rendszerekhez.

Ebben a tanfolyamban megismerkedünk a kutatás-alapú AutoGen keretrendszerrel és a termelésre kész Agent keretrendszerrel a Semantic Kertből.

## Minta kódok

- Python: [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## Van még kérdése az AI ügynökökről?

Csatlakozz a [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) közösséghez, hogy találkozz más tanulókkal, részt vegyél konzultációkon, és választ kapj AI ügynök kérdéseidre.

## Előző óra

[Tanfolyam beállítása](../00-course-setup/README.md)

## Következő óra

[Az ügynöki keretrendszerek felfedezése](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Felelősség kizárása**:
Ez a dokumentum az AI fordító szolgáltatás, a [Co-op Translator](https://github.com/Azure/co-op-translator) segítségével készült. Bár igyekszünk pontos fordítást nyújtani, kérjük, vegye figyelembe, hogy az automatikus fordítások tartalmazhatnak hibákat vagy pontatlanságokat. Az eredeti dokumentum az anyanyelvén tekintendő hivatalos forrásnak. Kritikus információk esetén professzionális, emberi fordítást javaslunk. Nem vállalunk felelősséget az ebből a fordításból eredő félreértésekért vagy téves értelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->