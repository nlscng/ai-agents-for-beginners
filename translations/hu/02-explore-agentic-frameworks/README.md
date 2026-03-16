[![AI Ügynökkeretek felfedezése](../../../translated_images/hu/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Kattints a fenti képre a tanóra videójának megtekintéséhez)_

# AI Ügynökkeretek felfedezése

Az AI ügynökkeretek olyan szoftverplatformok, amelyeket az AI ügynökök létrehozásának, telepítésének és kezelésének egyszerűsítésére terveztek. Ezek a keretek előre elkészített komponenseket, absztrakciókat és eszközöket biztosítanak a fejlesztők számára, amelyek meggyorsítják a bonyolult AI rendszerek fejlesztését.

Ezek a keretek segítik a fejlesztőket, hogy az alkalmazásaik egyedi aspektusaira összpontosítsanak azáltal, hogy szabványos megközelítéseket nyújtanak az AI ügynökfejlesztésben előforduló gyakori kihívásokra. Növelik az AI rendszerek építésének skálázhatóságát, elérhetőségét és hatékonyságát.

## Bevezetés 

Ez a tanóra a következőket fogja áttekinteni:

- Mik azok az AI ügynökkeretek és mit tesznek lehetővé a fejlesztők számára?
- Hogyan használhatják a csapatok ezeket ügynökeik képességeinek gyors prototípus készítésére, iterálására és fejlesztésére?
- Milyen különbségek vannak a Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> és <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> által létrehozott keretek és eszközök között?
- Közvetlenül integrálhatom meglévő Azure-ökoszisztéma eszközeimet, vagy különálló megoldásokra van szükségem?
- Mi az Azure AI Agents szolgáltatás, és hogyan segít nekem?

## Tanulási célok

Ennek a tanórának a céljai, hogy segítsenek megérteni:

- Az AI ügynökkeretek szerepét az AI fejlesztésben.
- Hogyan használhatók az AI ügynökkeretek intelligens ügynökök építéséhez.
- Az AI ügynökkeretek által biztosított kulcsfontosságú képességek.
- Az AutoGen, Semantic Kernel és Azure AI Agent Service közötti különbségeket.

## Mik azok az AI ügynökkeretek, és mit tesznek lehetővé a fejlesztők számára?

A hagyományos AI keretek segíthetnek az AI integrálásában az alkalmazásaidba, és az alábbi módokon tehetik jobbá ezeket az alkalmazásokat:

- **Személyre szabás**: Az AI elemezheti a felhasználói viselkedést és preferenciákat, hogy személyre szabott ajánlásokat, tartalmakat és élményeket nyújtson.
Példa: A Netflixhez hasonló streaming szolgáltatások AI segítségével javasolnak filmeket és műsorokat a megtekintési előzmények alapján, növelve a felhasználói elkötelezettséget és elégedettséget.
- **Automatizálás és hatékonyság**: Az AI automatizálhatja az ismétlődő feladatokat, egyszerűsítheti a munkafolyamatokat és javíthatja a működési hatékonyságot.
Példa: Az ügyfélszolgálati alkalmazások AI-alapú chatbotokat használnak a gyakori kérdések kezelésére, csökkentve a válaszidőt és felszabadítva az emberi munkatársakat bonyolultabb ügyekhez.
- **Fejlettebb felhasználói élmény**: Az AI javíthatja az általános felhasználói élményt intelligens funkciók nyújtásával, mint a hangfelismerés, természetes nyelvfeldolgozás és prediktív szöveg.
Példa: A Siri és a Google Assistant virtuális asszisztensek AI segítségével értik meg és válaszolják meg a hangutasításokat, megkönnyítve a felhasználók készülékeikkel történő interakcióját.

### Ez mind jól hangzik, de akkor miért van szükség az AI Ügynökkeretre?

Az AI ügynökkeretek többet jelentenek, mint egyszerű AI keretek. Olyan intelligens ügynökök létrehozását teszik lehetővé, amelyek képesek felhasználókkal, más ügynökökkel és a környezettel interakcióba lépni meghatározott célok elérése érdekében. Ezek az ügynökök autonóm viselkedést tanúsíthatnak, döntéseket hozhatnak, és alkalmazkodhatnak a változó körülményekhez. Nézzük meg az AI ügynökkeretek által nyújtott kulcsfontosságú képességeket:

- **Ügynökök közötti együttműködés és koordináció**: Több AI ügynök létrehozásának lehetősége, amelyek együtt dolgoznak, kommunikálnak és koordinálják feladataikat a komplex problémák megoldásához.
- **Feladat-automatizáció és menedzsment**: Többlépcsős munkafolyamatok automatizálásához, feladatdelegáláshoz és dinamikus feladatkezeléshez szükséges mechanizmusok biztosítása az ügynökök között.
- **Kontekstusértés és alkalmazkodás**: Az ügynökök képessé tétele a kontextus megértésére, a változó környezethez való alkalmazkodásra, és valós idejű információk alapján történő döntéshozatalra.

Összefoglalva tehát az ügynökök segítségével többre vagy képes: az automatizálást magasabb szintre emelheted, intelligensebb rendszereket hozhatsz létre, amelyek alkalmazkodni és tanulni tudnak a környezetükből.

## Hogyan lehet gyorsan prototípust készíteni, iterálni és fejleszteni az ügynök képességeit?

Ez egy gyorsan változó környezet, de van néhány általános elem a legtöbb AI ügynökkeretben, amelyek segítenek gyorsan prototípust készíteni és iterálni, ezek a moduláris komponensek, együttműködési eszközök és valós idejű tanulás. Nézzük meg ezeket:

- **Moduláris komponensek használata**: Az AI SDK-k előre elkészített komponenseket kínálnak, például AI és memória csatlakozókat, természetes nyelv vagy kód pluginek által hívható funkciókat, prompt sablonokat és még sok mást.
- **Együttműködési eszközök kihasználása**: Ügynökök tervezése konkrét szerepekkel és feladatokkal, lehetővé téve a csapatok számára, hogy teszteljék és finomítsák az együttműködési munkafolyamatokat.
- **Valós idejű tanulás**: Visszacsatolási hurkok implementálása, ahol az ügynökök a interakciókból tanulnak, és dinamikusan módosítják a viselkedésüket.

### Moduláris komponensek használata

Az SDK-k, mint a Microsoft Semantic Kernel és LangChain, előre elkészített komponenseket kínálnak, mint például AI csatlakozók, prompt sablonok és memória kezelés.

**Hogyan használhatják ezt a csapatok**: A csapatok gyorsan összerakhatják ezeket a komponenseket funkcionális prototípus készítéséhez anélkül, hogy a nulláról kezdenék, lehetővé téve a gyors kísérletezést és iterációt.

**Hogyan működik a gyakorlatban**: Használhatsz egy előre elkészített elemzőt a felhasználói bemenetből származó információk kinyerésére, egy memória modult az adatok tárolására és előkeresésére, valamint egy prompt generátort a felhasználókkal való interakcióhoz, mindezt anélkül, hogy ezeket a komponenseket kézzel kellene kidolgozni.

**Példa kód**. Nézzük meg, hogyan használhatod az előre elkészített AI csatlakozót a Semantic Kernel Python és .Net verziójában, amely automatikus függvényhívással válaszol a felhasználói bemenetekre:

``` python
# Semantic Kernel Python példa

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Hozzon létre egy ChatHistory objektumot a beszélgetés kontextusának tárolásához
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Hozzon létre egy mintaplugint, amely tartalmazza az utazás foglalására szolgáló függvényt
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Hozza létre a Kernel objektumot
kernel = Kernel()

# Adja hozzá a mintaplugint a Kernel objektumhoz
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Határozza meg az Azure OpenAI AI-kapcsolót
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Határozza meg a lekérés beállításait a modell automatikus függvényhívással történő konfigurálásához
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Küldje el a kérést a modellnek a megadott chat-előzmények és lekérési beállítások alapján
    # A Kernel tartalmazza a mintát, amelyet a modell meghívni fog
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # Példa AI modell válasz: `A 2025. január 1-jei New Yorkba tartó járatát sikeresen lefoglaltuk. Kellemes utazást! ✈️🗽`

    # Adja hozzá a modell válaszát a beszélgetés kontextusához
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```

Ebből a példából láthatod, hogyan használhatod az előre elkészített elemzőt a kulcsfontosságú információk, például az eredet, a célállomás és az időpont kinyerésére a repülőjegy foglalási kérelemből. Ez a moduláris megközelítés lehetővé teszi, hogy a magas szintű logikára koncentrálj.

### Együttműködési eszközök kihasználása

Olyan keretek, mint a CrewAI, a Microsoft AutoGen és a Semantic Kernel elősegítik több ügynök együttes munkáját.

**Hogyan használhatják ezt a csapatok**: A csapatok képesek ügynököket tervezni meghatározott szerepekkel és feladatokkal, lehetővé téve az együttműködési munkafolyamatok tesztelését és finomítását, valamint a rendszer hatékonyságának javítását.

**Hogyan működik a gyakorlatban**: Készíthetsz egy ügynökcsapatot, ahol minden ügynök speciális funkciót tölt be, például adatlekérés, elemzés vagy döntéshozatal. Ezek az ügynökök kommunikálhatnak és megoszthatják az információkat egy közös cél elérése érdekében, például egy felhasználói kérdés megválaszolásához vagy egy feladat elvégzéséhez.

**Példa kód (AutoGen)**:

```python
# agentek létrehozása, majd hozz létre egy körkörös (round-robin) ütemezést, ahol együtt dolgozhatnak, ebben az esetben sorrendben

# Adatlekérő ügynök
# Adatelemző ügynök
# Döntéshozó ügynök

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# a beszélgetés akkor ér véget, amikor a felhasználó azt mondja: "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Használd az asyncio.run(...) függvényt, amikor szkriptben futtatod.
await Console(stream)
```

Összesen, amit az előző kódból látsz, az egy feladat létrehozása, ami során több ügynök együttműködik az adatok elemzésében. Minden ügynök specifikus funkciót végez, és a feladat koordináltan, az ügynökök közös munkájával hajtódik végre a kívánt eredmény elérése érdekében. Speciális szerepköröket betöltő, dedikált ügynökök létrehozásával növelhető a feladat hatékonysága és teljesítménye.

### Valós idejű tanulás

Az előrehaladott keretek lehetőséget nyújtanak a valós idejű kontextusértésre és alkalmazkodásra.

**Hogyan használhatják ezt a csapatok**: Visszacsatolási hurkok bevezetése, ahol az ügynökök tanulnak az interakciókból, és dinamikusan módosítják viselkedésüket, ami folyamatos fejlődést és képességfejlesztést eredményez.

**Hogyan működik a gyakorlatban**: Az ügynökök elemzik a felhasználói visszajelzéseket, a környezeti adatokat és a feladat eredményét, frissítik tudásbázisukat, igazítják a döntéshozatali algoritmusokat, és idővel javítják a teljesítményt. Ez az iteratív tanulási folyamat lehetővé teszi az ügynökök számára, hogy alkalmazkodjanak a változó körülményekhez és a felhasználói preferenciákhoz, növelve a rendszer általános hatékonyságát.

## Milyen különbségek vannak az AutoGen, Semantic Kernel és Azure AI Agent Service keretek között?

Sokféleképpen lehet összehasonlítani ezeket a kereteket, de nézzünk néhány kulcsfontosságú különbséget a tervezésük, képességeik és célfelhasználási eseteik szempontjából:

## AutoGen

Az AutoGen a Microsoft Research AI Frontiers Lab által fejlesztett nyílt forráskódú keret. Eseményvezérelt, elosztott *ügynök* alkalmazásokra fókuszál, támogatva több LLM-et és SLM-et, eszközöket, valamint fejlett többügynökös tervezési mintákat.

Az AutoGen az ügynökök alapvető koncepciójára épül, amelyek autonóm entitások, képesek érzékelni környezetüket, döntéseket hozni és lépéseket tenni meghatározott célok elérése érdekében. Az ügynökök aszinkron üzenetekkel kommunikálnak, ami lehetővé teszi, hogy önállóan és párhuzamosan működjenek, növelve a rendszer skálázhatóságát és válaszkészségét.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Az ügynökök az actor modellre épülnek</a>. A Wikipédia szerint egy actor _a párhuzamos számítás alapvető építőköve. Az üzenet fogadására válaszul egy actor képes helyi döntésekre, több actor létrehozására, új üzenetek küldésére, valamint arra, hogy meghatározza, hogyan válaszoljon a következő fogadott üzenetre_.

**Felhasználási esetek**: Kódgenerálás automatizálása, adatfeldolgozási feladatok, valamint egyedi ügynökök létrehozása tervezési és kutatási funkciókhoz.

Az AutoGen néhány fontos alapvető koncepciója:

- **Ügynökök**. Egy ügynök egy szoftver entitás, amely:
  - **Üzeneteken keresztül kommunikál**, amelyek lehetnek szinkron vagy aszinkron jellegűek.
  - **Fenntartja saját állapotát**, amelyet a bejövő üzenetek módosíthatnak.
  - **Végrehajt tevékenységeket** a fogadott üzenetekre vagy állapotváltozásokra reagálva. Ezek a műveletek módosíthatják az ügynök állapotát és külső hatásokat eredményezhetnek, mint például üzenetnaplók frissítése, új üzenetek küldése, kód futtatása vagy API hívások.
    
  Íme egy rövid kódrészlet, amelyben saját Chat képességekkel rendelkező ügynököt hozol létre:

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
    
    Az előző kódban a `MyAgent` jött létre és az `RoutedAgent` osztályból származik. Tartalmaz egy üzenetkezelőt, amely kiírja az üzenet tartalmát, majd egy válasz küld az `AssistantAgent` delegált használatával. Különösen figyeld meg, hogyan rendeljük a `self._delegate` változóhoz az `AssistantAgent` példányát, ami egy előre elkészített ügynök, amely képes chat-kiegészítést kezelni.

    Ezután engedjük tudtára az AutoGen-nek ezt az ügynöktípust, és indítsuk el a programot:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Indítsa el az üzenetek feldolgozását a háttérben.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Az előző kódban az ügynökök regisztrálva vannak a futtatókörnyezettel, majd egy üzenet érkezik az ügynökhöz, amely az alábbi kimenetet eredményezi:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Több ügynök**. Az AutoGen lehetővé teszi több ügynök létrehozását, akik együttműködve oldanak meg összetett feladatokat. Az ügynökök kommunikálhatnak, megoszthatják az információt és összehangolhatják tevékenységüket a hatékonyabb problémamegoldás érdekében. Többügynökös rendszer létrehozásához definiálhatsz különböző típusú ügynököket specializált funkciókkal és szerepekkel, mint adatlekérés, elemzés, döntéshozatal és felhasználói interakció. Lássuk, hogyan néz ki egy ilyen rendszer létrehozása:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Példa egy ügynök deklarálására
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # A 'topic' típust használja ügynök típusaként.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="SAJÁT_API_KULCSOD",
        ),
        ),
    )

    # a további deklarációk rövidítve a tömörség kedvéért

    # Csoportos csevegés
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="SAJÁT_API_KULCSOD",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```

    Az előző kódban egy `GroupChatManager` van regisztrálva a futtatókörnyezettel. Ez a menedzser felelős az ügynökök közötti interakciók koordinálásáért különböző típusok között, mint írók, illusztrátorok, szerkesztők és felhasználók.

- **Ügynök futtatókörnyezet (Runtime)**. A keret biztosít egy futtatókörnyezetet, amely lehetővé teszi az ügynökök közötti kommunikációt, kezeli identitásukat és életciklusukat, valamint biztosítja a biztonsági és adatvédelmi határokat. Ez azt jelenti, hogy egy biztonságos és ellenőrzött környezetben futtathatod az ügynökeidet, garantálva, hogy biztonságosan és hatékonyan kommunikálnak. Két érdekes futtatókörnyezet létezik:
  - **Különálló futtatókörnyezet (stand-alone runtime)**. Ez jó választás egyszálú alkalmazásokhoz, ahol az összes ügynök ugyanabban a programozási nyelvben van megvalósítva és ugyanabban a folyamatban fut. Íme egy illusztráció, hogyan működik:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Különálló futtatókörnyezet</a>  
Alkalmazás stack

    *az ügynökök üzeneteken keresztül kommunikálnak a futtatókörnyezettel, amely kezeli az életciklusukat*

  - **Elosztott ügynök futtatókörnyezet**. Ez alkalmas többfolyamatú alkalmazásokhoz, ahol az ügynökök eltérő programozási nyelvekben valósulhatnak meg, és különböző gépeken futnak. Íme egy illusztráció, hogyan működik:

    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Elosztott futtatókörnyezet</a>

## Semantic Kernel + Ügynökkeret

A Semantic Kernel egy vállalati szintű AI Orchestration SDK. AI- és memória csatlakozókból, valamint egy Ügynökkeretből áll.

Először nézzünk meg néhány alapvető komponenst:

- **AI csatlakozók**: Ez egy interfész külső AI szolgáltatásokhoz és adatforrásokhoz, Pythonban és C#-ban egyaránt használható.

  ```python
  # Szemantikus Kernel Python
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  

    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```

    Itt egy egyszerű példa arra, hogyan hozhatsz létre egy kernelt és adhatsz hozzá chat befejezési szolgáltatást. A Semantic Kernel kapcsolatot létesít egy külső AI szolgáltatással, jelen esetben az Azure OpenAI Chat Completion szolgáltatással.

- **Pluginok**: Ezek olyan funkciókat csomagolnak be, amelyeket egy alkalmazás használhat. Vannak készen kapható pluginok és egyéni pluginok is, amelyeket készíthetsz. Egy kapcsolódó fogalom a "prompt funkciók". Ahelyett, hogy természetes nyelvi utasításokat adnál a függvényhíváshoz, bizonyos funkciókat közvetlenül „broadcastolsz” a modell felé. A jelenlegi chat kontextus alapján a modell eldöntheti, hogy hívjon-e az egyik ilyen funkciót egy kérés vagy lekérdezés teljesítéséhez. Íme egy példa:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```

    Itt először van egy sablon prompt, a `skPrompt`, amely teret hagy a felhasználó által bevitt szövegnek, `$userInput`. Ezután létrehozod a `SummarizeText` kernel funkciót, majd importálod a kernelbe a `SemanticFunctions` plugin névvel. Ügyelj a funkció nevére, amely segíti a Semantic Kernelt megérteni, mit csinál a funkció és mikor kell meghívni.

- **Natív funkció**: Vannak olyan natív funkciók is, amelyeket a keret közvetlenül hív meg a feladat végrehajtására. Íme egy példa ilyen funkcióra, amely fájl tartalmát olvassa be:

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```

- **Memória**: Absztrakciót és egyszerűsítést nyújt az AI alkalmazások kontextuskezeléséhez. A memória ötlete az, hogy ez egy olyan információ, amelyet a LLM-nek tudnia kell. Ezt tárolhatod vektortárolóban, ami lehet egy memóriában lévő adatbázis vagy vektoralapú adatbázis vagy hasonló. Íme egy nagyon egyszerűsített példa, ahol *tényeket* adunk a memóriához:

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```

    Ezeket a tényeket aztán elmentjük a `SummarizedAzureDocs` memória gyűjteménybe. Ez egy nagyon egyszerűsített példa, de látható, hogyan lehet információkat tárolni a memóriában az LLM használatára.

Szóval ez az Semantic Kernel keretrendszer alapja, mi a helyzet az Agent Framework-kel?

## Azure AI Agent Service

Az Azure AI Agent Service egy újabb kiegészítés, melyet a Microsoft Ignite 2024-en mutattak be. Lehetővé teszi AI ügynökök fejlesztését és telepítését rugalmasabb modellekkel, például közvetlenül nyílt forráskódú LLM-eket hívva, mint a Llama 3, Mistral és Cohere.

Az Azure AI Agent Service erősebb vállalati biztonsági mechanizmusokat és adattárolási módszereket kínál, így alkalmas vállalati alkalmazásokhoz.

Kész használatra működik többügynökös orkesztrációs keretrendszerekkel, mint az AutoGen és Semantic Kernel.

Ez a szolgáltatás jelenleg nyilvános előzetes verzióban érhető el, Python és C# támogatást nyújt ügynökök építéséhez.

A Semantic Kernel Python használatával létrehozhatunk egy Azure AI Agent-et felhasználó által definiált plugin segítségével:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Határozzon meg egy mintaplugint a példához
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # Hozzon létre egy ügynökdefiníciót
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Hozzon létre az AzureAI ügynököt a definiált kliens és az ügynökdefiníció felhasználásával
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Hozzon létre egy szálat a beszélgetés tárolásához
        # Ha nem adnak meg szálat, egy új szál
        # létrejön és a kezdeti válasszal együtt visszaadásra kerül
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # Hívja meg az ügynököt a megadott szálhoz
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### Alapvető fogalmak

Az Azure AI Agent Service rendelkezik a következő alapvető fogalmakkal:

- **Ügynök**. Az Azure AI Agent Service integrálódik a Microsoft Foundry-val. Az AI Foundry-n belül az AI ügynök "okos" mikroszolgáltatásként működik, amelyet kérdések megválaszolására (RAG), műveletek végrehajtására vagy munkafolyamatok teljes automatizálására lehet használni. Ezt úgy éri el, hogy ötvözi a generatív AI modellek erejét eszközökkel, melyek lehetővé teszik a valós adatokhoz való hozzáférést és azokkal való interakciót. Íme egy példa egy ügynökre:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Ebben a példában egy ügynök jön létre a `gpt-4o-mini` modellel, `my-agent` névvel és az utasítással: "You are helpful agent". Az ügynök fel van szerelve eszközökkel és erőforrásokkal kódértelmezési feladatok végrehajtásához.

- **Szalag (thread) és üzenetek**. A szalag egy másik fontos fogalom. Ez egy beszélgetést vagy interakciót képvisel egy ügynök és egy felhasználó között. A szalagok segítségével nyomon követhető a beszélgetés előrehaladása, tárolható a kontextus, és kezelhető az interakció állapota. Íme egy példa egy szalagra:

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    A korábbi kódban létrejön egy szalag. Ezután egy üzenetet küldenek a szalagra. A `create_and_process_run` hívással az ügynöktől kérik, hogy dolgozzon a szalagon. Végül az üzenetek lekérdezésre és naplózásra kerülnek, hogy lássuk az ügynök válaszát. Az üzenetek jelzik a beszélgetés előrehaladását a felhasználó és az ügynök között. Fontos megérteni, hogy az üzenetek különböző típusúak lehetnek, például szöveg, kép vagy fájl – azaz az ügynök munkája eredményezhet például képet vagy szöveges választ. Fejlesztőként ezt az információt felhasználhatja a válasz további feldolgozásához vagy megjelenítéséhez a felhasználónak.

- **Más AI keretrendszerekkel való integráció**. Az Azure AI Agent Service képes együttműködni más keretrendszerekkel, mint az AutoGen és a Semantic Kernel, ami azt jelenti, hogy az alkalmazás egy részét ezekben a keretrendszerekben is megépítheted, például az Agent Service-t használva orkesztrátorként, vagy az egészet az Agent Service-ben készítheted el.

**Használati esetek**: Az Azure AI Agent Service vállalati alkalmazások számára készült, ahol biztonságos, skálázható és rugalmas AI ügynökök telepítésére van szükség.

## Mi a különbség ezek között a keretrendszerek között?

Úgy tűnik sok átfedés van a keretrendszerek között, de vannak kulcsfontosságú különbségek a tervezésük, képességeik és célhasználataik tekintetében:

- **AutoGen**: Egy kísérleti keretrendszer, amely a többügynökös rendszerek élvonalbeli kutatására fókuszál. Ez a legjobb hely összetett többügynökös rendszerek kísérletezésére és prototípus készítésére.
- **Semantic Kernel**: Egy termelésre kész ügynökkönyvtár vállalati agentikus alkalmazások építéséhez. Az eseményvezérelt, elosztott agentikus alkalmazásokra fókuszál, támogat több LLM-et és SLM-et, eszközöket, valamint egy- és többügynökös tervezési mintákat.
- **Azure AI Agent Service**: Egy platform és telepítési szolgáltatás az Azure Foundry-ban az ügynökök számára. Kapcsolódást biztosít az Azure OpenAI, Azure AI Search, Bing Search és kódvégrehajtás szolgáltatásokhoz.

Még bizonytalan, melyiket válaszd?

### Használati esetek

Nézzük meg, tudunk-e segíteni néhány gyakori használati eset áttekintésével:

> K: Kísérletezek, tanulok és proof-of-concept agent-alkalmazásokat építek, és gyorsan akarok építkezni és kísérletezni.
>

>V: Az AutoGen jó választás lenne erre a helyzetre, mivel eseményvezérelt, elosztott agentikus alkalmazásokra fókuszál, és támogat fejlett többügynökös tervezési mintákat.

> K: Miért jobb választás az AutoGen, mint a Semantic Kernel vagy az Azure AI Agent Service ehhez az esethez?
>
> V: Az AutoGen kifejezetten eseményvezérelt, elosztott agentikus alkalmazásokra tervezték, így jól alkalmas kódgenerálási és adatfeldolgozási feladatok automatizálására. Megadja a szükséges eszközöket és képességeket a komplex többügynökös rendszerek hatékony felépítéséhez.

> K: Úgy tűnik, az Azure AI Agent Service is működhet itt, van eszközei kódgenerálásra és más feladatokra?
>
> V: Igen, az Azure AI Agent Service egy platform szolgáltatás ügynökök számára, beépített funkciókkal több modellhez, Azure AI Search, Bing Search és Azure Functions támogatással. Könnyű az ügynökeidet a Foundry Portálban építeni és nagy léptékben telepíteni.

> K: Még mindig zavarban vagyok, adj egyetlen opciót
>
> V: Remek választás, ha először a Semantic Kernel-ben építed az alkalmazásodat, majd az Azure AI Agent Service-el telepíted az ügynöködet. Ez a megközelítés lehetővé teszi, hogy könnyedén megőrizd ügynökeidet, miközben kihasználod a többügynökös rendszerek építésének erejét a Semantic Kernel-ben. Ráadásul a Semantic Kernel rendelkezik AutoGen kapcsolóval, így egyszerűen használhatod együtt mindkét keretrendszert.

Foglaljuk össze a főbb különbségeket egy táblázatban:

| Keretrendszer | Fókusz | Alapfogalmak | Használati esetek |
| --- | --- | --- | --- |
| AutoGen | Eseményvezérelt, elosztott agentikus alkalmazások | Ügynökök, személyiségek, funkciók, adatok | Kódgenerálás, adatelemzési feladatok |
| Semantic Kernel | Emberi nyelvhez hasonló szövegértés és generálás | Ügynökök, moduláris komponensek, együttműködés | Természetes nyelv feldolgozás, tartalom generálás |
| Azure AI Agent Service | Rugalmas modellek, vállalati biztonság, kódgenerálás, eszközök hívása | Modularitás, együttműködés, folyamat orkestráció | Biztonságos, skálázható és rugalmas AI ügynök telepítés |

Melyik a ideális használati eset mindegyik keretrendszerhez?

## Be tudom-e integrálni a meglévő Azure ökoszisztéma eszközeimet közvetlenül, vagy különálló megoldások kellenek?

A válasz igen, közvetlenül integrálhatod a meglévő Azure ökoszisztéma eszközeidet az Azure AI Agent Service-zel különösen, mivel azt kifejezetten az egyéb Azure szolgáltatásokkal való zökkenőmentes együttműködésre tervezték. Például integrálhatod a Bing, Azure AI Search és Azure Functions szolgáltatásokat. Van mély integráció a Microsoft Foundry-val is.

Az AutoGen és a Semantic Kernel esetében is integrálhatsz Azure szolgáltatásokat, de előfordulhat, hogy a kódból kell meghívni azokat. Egy másik lehetőség, hogy az Azure SDK-kat használod az Azure szolgáltatásokkal való interakcióra az ügynökeidből. Ráadásul, mint említettük, az Azure AI Agent Service-t használhatod orkesztrátorként az AutoGen-ben vagy Semantic Kernel-ben készült ügynökeidhez, így könnyen hozzáférhetsz az Azure ökoszisztémához.

## Minta kódok

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Több kérdésed van az AI Agent Framework-ökről?

Csatlakozz a [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) közösséghez más tanulókkal való találkozáshoz, hivatalos konzultációkhoz és AI Ügynök kérdések megválaszolásához.

## Hivatkozások

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel és AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Azure AI Agent Service használata AutoGen / Semantic Kernel-rel többugynökös megoldás építéséhez</a>

## Előző lecke

[Bevezetés az AI Ügynökökbe és az ügynök használati esetekbe](../01-intro-to-ai-agents/README.md)

## Következő lecke

[Agentikus Tervezési Minták megértése](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Nyilatkozat**:
Ez a dokumentum az AI fordító szolgáltatás, a [Co-op Translator](https://github.com/Azure/co-op-translator) használatával készült. Bár igyekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti dokumentum anyanyelvű változatát kell tekinteni a hivatalos forrásnak. Kritikus információk esetén ajánlott professzionális emberi fordítás igénybevétele. Nem vállalunk felelősséget a fordítás használatából eredő félreértésekért vagy félreértelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->