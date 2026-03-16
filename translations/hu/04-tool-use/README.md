[![Hogyan tervezzünk jó AI ügynököket](../../../translated_images/hu/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Kattints a fent található képre a lecke videójának megtekintéséhez)_

# Tool Use Design Pattern

A eszközök érdekesek, mert lehetővé teszik az AI ügynökök számára, hogy szélesebb körű képességekkel rendelkezzenek. Ahelyett, hogy az ügynöknek egy korlátozott műveletkészlete lenne, egy eszköz hozzáadásával az ügynök immár sokféle műveletet tud végrehajtani. Ebben a fejezetben áttekintjük a Tool Use Design Patternet, amely leírja, hogyan használhatnak az AI ügynökök specifikus eszközöket céljaik eléréséhez.

## Bevezetés

Ebben a leckében a következő kérdésekre keresünk választ:

- Mi az a tool use design pattern?
- Milyen alkalmazási esetekre lehet alkalmazni?
- Milyen elemek/építőkövek szükségesek a design pattern megvalósításához?
- Milyen különleges megfontolások vannak a Tool Use Design Pattern használatakor bizalomra méltó AI ügynökök építéséhez?

## Tanulási célok

A lecke elvégzése után képes leszel:

- Meghatározni a Tool Use Design Patternet és annak célját.
- Azonosítani azokat az alkalmazási eseteket, ahol a Tool Use Design Pattern alkalmazható.
- Megérteni a design pattern megvalósításához szükséges kulcselemeket.
- Felismerni a megbízhatóság biztosítására vonatkozó megfontolásokat olyan AI ügynökök esetében, amelyek ezt a design patternet használják.

## Mi az a Tool Use Design Pattern?

A **Tool Use Design Pattern** arra fókuszál, hogy LLM-eknek képességet adjon külső eszközökkel való interakcióra, hogy konkrét célokat érjenek el. Az eszközök olyan kódok, amelyeket egy ügynök végrehajthat bizonyos műveletek elvégzésére. Egy eszköz lehet egy egyszerű függvény, például egy számológép, vagy egy harmadik fél szolgáltatására mutató API-hívás, például részvényár-keresés vagy időjárás-előrejelzés. Az AI ügynökök kontextusában az eszközöket úgy tervezik, hogy az ügynökök végrehajtsák őket **modell által generált függvényhívásokra** válaszul.

## Milyen alkalmazási esetekre alkalmazható?

Az AI ügynökök eszközöket vehetnek igénybe összetett feladatok elvégzéséhez, információk lekéréséhez vagy döntések meghozatalához. A tool use design pattern gyakran olyan forgatókönyvekben használatos, ahol dinamikus interakció szükséges külső rendszerekkel, például adatbázisokkal, webszolgáltatásokkal vagy kódértelmezőkkel. Ez a képesség számos különféle felhasználási esetben hasznos, többek között:

- **Dinamikus információlekérés:** Az ügynökök külső API-kat vagy adatbázisokat kérdezhetnek le naprakész adatokért (pl. egy SQLite adatbázis lekérdezése adatelemzéshez, részvényárak vagy időjárás lekérése).
- **Kódvégrehajtás és értelmezés:** Az ügynökök kódot vagy szkripteket futtathatnak matematikai problémák megoldására, jelentések generálására vagy szimulációk végrehajtására.
- **Munkafolyamat-automatizálás:** Ismétlődő vagy többlépéses munkafolyamatok automatizálása olyan eszközök integrálásával, mint feladatütemezők, e-mail szolgáltatások vagy adatcsatornák.
- **Ügyfélszolgálat:** Az ügynökök CRM rendszerekkel, jegykezelő platformokkal vagy tudásbázisokkal léphetnek kapcsolatba a felhasználói kérdések megoldásához.
- **Tartalomgenerálás és szerkesztés:** Az ügynökök olyan eszközöket használhatnak, mint nyelvtani ellenőrzők, szövegösszefoglalók vagy tartalombiztonsági értékelők a tartalomkészítés támogatásához.

## Milyen elemek/építőkövek szükségesek a tool use design pattern megvalósításához?

Ezek az építőkövek lehetővé teszik az AI ügynök számára, hogy széles körű feladatokat végezzen. Nézzük meg a Tool Use Design Pattern megvalósításához szükséges kulcselemeket:

- **Függvény/Eszköz séma:** Részletes meghatározások a rendelkezésre álló eszközökről, beleértve a függvény nevét, célját, szükséges paramétereket és várható kimeneteket. Ezek a sémák lehetővé teszik az LLM számára, hogy megértse, milyen eszközök állnak rendelkezésre és hogyan kell érvényes kéréseket összeállítani.

- **Függvényvégrehajtási logika:** Szabályozza, hogyan és mikor hívják meg az eszközöket a felhasználó szándéka és a beszélgetés kontextusa alapján. Ez magában foglalhat tervező modulokat, irányító mechanizmusokat vagy feltételes folyamatokat, amelyek dinamikusan határozzák meg az eszközhasználatot.

- **Üzenetkezelő rendszer:** Olyan komponensek, amelyek kezelik a felhasználói bemenetek, LLM-válaszok, eszközhívások és eszközkimenetek közötti beszélgetési folyamatot.

- **Eszközintegrációs keretrendszer:** Infrastruktúra, amely összekapcsolja az ügynököt különféle eszközökkel, legyenek azok egyszerű függvények vagy összetett külső szolgáltatások.

- **Hibakezelés és érvényesítés:** Mechanizmusok az eszközvégrehajtás sikertelenségeinek kezelésére, a paraméterek érvényesítésére és a váratlan válaszok kezelésére.

- **Állapotkezelés:** Követi a beszélgetés kontextusát, az előző eszközinterakciókat és a tartós adatokat, hogy többfordulós interakciók során következetességet biztosítson.

Ezután nézzük meg részletesebben a függvény-/eszközhívást.

### Function/Tool Calling

A függvényhívás az elsődleges módja annak, hogy nagy nyelvi modelleket (LLM-eket) képessé tegyünk eszközökkel való interakcióra. Gyakran látni fogod, hogy a 'Function' és a 'Tool' kifejezéseket felcserélve használják, mert a 'functions' (újrahasznosítható kódrészek) azok az 'eszközök', amelyeket az ügynökök feladatok végrehajtásához használnak. Ahhoz, hogy egy függvény kódját meghívják, az LLM-nek össze kell hasonlítania a felhasználó kérését a függvény leírásával. Ehhez egy sémát, amely tartalmazza az összes rendelkezésre álló függvény leírását, elküldünk az LLM-nek. Az LLM ezután kiválasztja a feladathoz legmegfelelőbb függvényt, és visszaadja annak nevét és argumentumait. A kiválasztott függvényt meghívják, a válasza visszaküldésre kerül az LLM-nek, amely az információt felhasználva válaszol a felhasználó kérésére.

Ahhoz, hogy a fejlesztők megvalósítsák a függvényhívást az ügynökök számára, szükséged lesz:

1. Egy olyan LLM modellre, amely támogatja a függvényhívást
2. Egy sémára, amely tartalmazza a függvények leírásait
3. A leírt függvényekhez tartozó kódra

Vegyük példának egy város aktuális idejének lekérését, hogy illusztráljuk:

1. **Indítsunk egy olyan LLM-et, amely támogatja a függvényhívást:**

    Nem minden modell támogatja a függvényhívást, ezért fontos ellenőrizni, hogy az általad használt LLM támogatja-e.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> támogatja a függvényhívást. Kezdhetjük azzal, hogy inicializáljuk az Azure OpenAI klienset. 

    ```python
    # Inicializálja az Azure OpenAI klienst
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Hozzunk létre egy függvénysémát**:

    Ezután definiálunk egy JSON sémát, amely tartalmazza a függvény nevét, leírását, hogy mit csinál a függvény, valamint a függvényparaméterek nevét és leírását.
    Ezt a sémát továbbadjuk a korábban létrehozott kliensnek, a felhasználó kérésével együtt, hogy megtaláljuk a San Francisco időpontját. Fontos megjegyezni, hogy egy **eszközhívás** az, ami visszatér, **nem** a kérdés végső válasza. Ahogy korábban említettük, az LLM visszaadja a feladat elvégzésére kiválasztott függvény nevét és az ahhoz átadandó argumentumokat.

    ```python
    # A modell számára olvasandó függvény leírása
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # Kezdeti felhasználói üzenet
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Első API-hívás: Kérje meg a modellt, hogy használja a függvényt
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Feldolgozza a modell válaszát
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **A feladat végrehajtásához szükséges függvénykód:**

    Most, hogy az LLM kiválasztotta, melyik függvényt kell futtatni, meg kell valósítani és végre kell hajtani a feladatot végző kódot.
    Pythonban megvalósíthatjuk a jelenlegi idő lekéréséhez szükséges kódot. Szükség lesz továbbá kódra, amely kinyeri a response_message-ből a nevet és az argumentumokat, hogy megkapjuk a végső eredményt.

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # Függvényhívások kezelése
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # Második API-hívás: A modell végső válaszának lekérése
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

A Function Calling a legtöbb, ha nem az összes ügynöki eszközhasználat központjában áll, azonban a nulláról történő megvalósítása néha kihívást jelenthet.
Ahogy a [Lesson 2](../../../02-explore-agentic-frameworks) leckében megtanultuk, az ügynöki keretrendszerek előre elkészített építőköveket biztosítanak az eszközhasználat megvalósításához.
 
## Eszközhasználat példái ügynöki keretrendszerekkel

Itt néhány példa arra, hogyan valósíthatod meg a Tool Use Design Patternet különböző ügynöki keretrendszerek használatával:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> egy nyílt forráskódú AI keretrendszer .NET, Python és Java fejlesztők számára, akik nagy nyelvi modellekkel (LLM-ekkel) dolgoznak. Megkönnyíti a függvényhívás használatát azáltal, hogy automatikusan leírja a függvényeidet és azok paramétereit a modell számára egy <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">szerializálás</a> nevű folyamaton keresztül. Kezeli továbbá a modell és a kód közötti oda-vissza kommunikációt. Egy másik előnye egy olyan ügynöki keretrendszer használatának, mint a Semantic Kernel, hogy hozzáférést biztosít előre elkészített eszközökhöz, például a <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> és a <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a> eszközökhöz.

A következő diagram szemlélteti a függvényhívás folyamatát a Semantic Kernel segítségével:

![függvényhívás](../../../translated_images/hu/functioncalling-diagram.a84006fc287f6014.webp)

A Semantic Kernelben a függvényeket/eszközöket <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">bővítményeknek (Plugins)</a> nevezzük. A korábban látott `get_current_time` függvényt átalakíthatjuk pluginné azáltal, hogy osztállyá alakítjuk, amely tartalmazza a függvényt. Importálhatjuk továbbá a `kernel_function` dekorátort, amely átveszi a függvény leírását. Amikor létrehozol egy kernelt a GetCurrentTimePlugin segítségével, a kernel automatikusan szerializálja a függvényt és annak paramétereit, ezzel létrehozva a sémát, amelyet az LLM-nek küldünk.

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# Hozd létre a kernelt
kernel = Kernel()

# Hozd létre a bővítményt
get_current_time_plugin = GetCurrentTimePlugin(location)

# Add hozzá a bővítményt a kernelhez
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> egy újabb ügynöki keretrendszer, amely lehetővé teszi a fejlesztők számára, hogy biztonságosan építsenek, telepítsenek és skálázzanak magas minőségű, kiterjeszthető AI ügynököket anélkül, hogy az alatta lévő számítási és tárolási erőforrásokat kellene kezelniük. Különösen vállalati alkalmazásokhoz hasznos, mivel teljesen felügyelt szolgáltatás vállalati szintű biztonsággal.

Az LLM API közvetlen használatával összehasonlítva az Azure AI Agent Service néhány előnyt nyújt, többek között:

- Automatikus eszközhívás – nincs szükség eszközhívás elemzésére, az eszköz meghívására és a válasz kezelésére; mindez most a szerveroldalon történik
- Biztonságosan kezelt adatok – a saját beszélgetési állapot kezelésére való helyett a threads-re támaszkodhatsz, amelyek az összes szükséges információt tárolják
- Kész eszközök – Olyan eszközök, amelyekkel adatforrásaidhoz kapcsolódhatsz, például a Bing, Azure AI Search és Azure Functions.

Az Azure AI Agent Service-ben elérhető eszközök két kategóriába sorolhatók:

1. Tudás eszközök:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing keresés alapozás</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Fájlkeresés</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Műveleti eszközök:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Függvényhívás (Function Calling)</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Kódértelmező (Code Interpreter)</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI által definiált eszközök</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Az Agent Service lehetővé teszi, hogy ezeket az eszközöket együtt, egy `toolset`-ként használd. Emellett `threads`-eket is használ, amelyek nyomon követik egy adott beszélgetés üzenettörténetét.

Képzeld el, hogy egy Contoso nevű cég értékesítési ügynöke vagy. Olyan beszélgető ügynököt szeretnél fejleszteni, amely képes válaszolni az értékesítési adataiddal kapcsolatos kérdésekre.

A következő kép azt szemlélteti, hogyan használhatnád az Azure AI Agent Service-et az értékesítési adatok elemzésére:

![Agenti szolgáltatás működés közben](../../../translated_images/hu/agent-service-in-action.34fb465c9a84659e.webp)

Bármelyik eszköz használatához a szolgáltatással létrehozhatunk egy klienset és definiálhatunk egy eszközt vagy eszközkészletet. Ennek gyakorlati megvalósításához a következő Python kódot használhatjuk. Az LLM meg tudja nézni az eszközkészletet és eldöntheti, hogy a felhasználó által létrehozott `fetch_sales_data_using_sqlite_query` függvényt használja-e, vagy a beépített Code Interpretort a felhasználói kérés függvényében.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # A fetch_sales_data_using_sqlite_query függvény, amely megtalálható a fetch_sales_data_functions.py fájlban.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Eszközkészlet inicializálása
toolset = ToolSet()

# Függvényhívó ügynök inicializálása a fetch_sales_data_using_sqlite_query függvénnyel és hozzáadása az eszközkészlethez
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# A Code Interpreter eszköz inicializálása és hozzáadása az eszközkészlethez.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Milyen különleges megfontolások vannak a Tool Use Design Pattern használatakor bizalomra méltó AI ügynökök építéséhez?

Az LLM-ek által dinamikusan generált SQL-lel kapcsolatban gyakori aggály a biztonság, különösen az SQL injection vagy rosszindulatú műveletek kockázata, például az adatbázis törlése vagy manipulálása. Bár ezek az aggodalmak jogosak, hatékonyan mérsékelhetők az adatbázis-hozzáférési jogosultságok megfelelő konfigurálásával. A legtöbb adatbázis esetében ez azt jelenti, hogy az adatbázist csak olvashatóként (read-only) konfiguráljuk. Olyan adatbázis-szolgáltatásoknál, mint a PostgreSQL vagy az Azure SQL, az alkalmazásnak olvasási jogosultságot (SELECT szerepkört) kell adni.

Az alkalmazás biztonságos környezetben való futtatása tovább növeli a védelmet. Vállalati forgatókönyvekben az adatok általában kinyerésre és átalakításra kerülnek az operatív rendszerekből egy csak olvasható adatbázisba vagy adattárházba, felhasználóbarát sémával. Ez a megközelítés biztosítja, hogy az adatok biztonságosak, teljesítmény és hozzáférhetőség szempontjából optimalizáltak legyenek, és hogy az alkalmazás korlátozott, csak olvasható hozzáféréssel rendelkezzen.

## Sample Codes
- Python: [Ügynök keretrendszer](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Ügynök keretrendszer](./code_samples/04-dotnet-agent-framework.md)

## További kérdéseid vannak az eszközhasználati tervezési mintákkal kapcsolatban?

Csatlakozz a [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), hogy találkozz más tanulókkal, részt vegyél fogadóórákon és választ kapj az AI ügynökökkel kapcsolatos kérdéseidre.

## További források

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service műhely</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer többügynökös workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel funkcióhívás oktatóanyag</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel kódértelmező</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen eszközök</a>

## Előző lecke

[Az ügynökszerű tervezési minták megértése](../03-agentic-design-patterns/README.md)

## Következő lecke

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Felelősségkizárás:
Ezt a dokumentumot a mesterséges intelligencián alapuló fordító szolgáltatás, a [Co-op Translator](https://github.com/Azure/co-op-translator) segítségével fordítottuk. Bár törekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatizált fordítások hibákat vagy pontatlanságokat tartalmazhatnak. A dokumentum eredeti, anyanyelvi változatát kell tekinteni a hiteles forrásnak. Kritikus fontosságú információk esetén szakmai, emberi fordítást javaslunk. Nem vállalunk felelősséget a fordítás használatából eredő félreértésekért vagy félreértelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->