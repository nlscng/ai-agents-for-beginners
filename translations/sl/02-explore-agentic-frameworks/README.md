[![Raziskovanje ogrodij AI agentov](../../../translated_images/sl/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Kliknite zgornjo sliko za ogled videoposnetka te lekcije)_

# Raziščite ogrodja AI agentov

Ogrodja AI agentov so programske platforme, zasnovane za poenostavitev ustvarjanja, uvajanja in upravljanja AI agentov. Ta ogrodja razvijalcem nudijo vnaprej izdelane komponente, abstrakcije in orodja, ki poenostavijo razvoj kompleksnih AI sistemov.

Ta ogrodja pomagajo razvijalcem, da se osredotočijo na unikatne vidike svojih aplikacij z zagotavljanjem standardiziranih pristopov k pogostim izzivom pri razvoju AI agentov. Izboljšujejo skalabilnost, dostopnost in učinkovitost pri gradnji AI sistemov.

## Uvod 

V tej lekciji bomo obravnavali:

- Kaj so ogrodja AI agentov in kaj razvijalcem omogočajo doseči?
- Kako lahko ekipe uporabijo ta ogrodja za hitro izdelavo prototipov, iteriranje in izboljšanje zmogljivosti svojih agentov?
- Kakšne so razlike med ogrodji in orodji, ki jih je ustvaril Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, in <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Ali lahko neposredno integriram obstoječa orodja iz Azure ekosistema ali potrebujem samostojne rešitve?
- Kaj je storitev Azure AI Agents in kako mi to pomaga?

## Cilji učenja

Cilji te lekcije so, da vam pomagajo razumeti:

- Vlogo ogrodij AI agentov pri razvoju AI.
- Kako izkoristiti ogrodja AI agentov za gradnjo inteligentnih agentov.
- Ključne zmogljivosti, ki jih omogočajo ogrodja AI agentov.
- Razlike med AutoGen, Semantic Kernel in Azure AI Agent Service.

## Kaj so ogrodja AI agentov in kaj razvijalcem omogočajo?

Tradicionalna ogrodja za AI vam lahko pomagajo integrirati AI v vaše aplikacije in izboljšati te aplikacije na naslednje načine:

- **Personalizacija**: AI lahko analizira vedenje in preference uporabnikov ter ponudi prilagojena priporočila, vsebine in izkušnje.
Primer: Pretakalne storitve, kot je Netflix, uporabljajo AI za predlaganje filmov in serij na podlagi zgodovine gledanja, s čimer povečajo angažiranost in zadovoljstvo uporabnikov.
- **Avtomatizacija in učinkovitost**: AI lahko avtomatizira ponavljajoča se opravila, poenostavi delovne procese in izboljša operativno učinkovitost.
Primer: Aplikacije za podporo strankam uporabljajo klepetalnike, podprte z AI, za obravnavo pogostih poizvedb, s čimer zmanjšajo odzivne čase in sprostijo človeške agente za bolj zapletene zadeve.
- **Izboljšana uporabniška izkušnja**: AI lahko izboljša splošno uporabniško izkušnjo z inteligentnimi funkcijami, kot so prepoznavanje govora, obdelava naravnega jezika in prediktivno besedilo.
Primer: Virtualni asistenti, kot sta Siri in Google Assistant, uporabljajo AI za razumevanje in odzivanje na glasovne ukaze, zaradi česar je lažje komunicirati z napravami.

### Vse to zveni odlično, ampak zakaj potrebujemo ogrodje AI agentov?

Ogrodja AI agentov predstavljajo več kot le AI ogrodja. Namenjena so omogočanju ustvarjanja inteligentnih agentov, ki lahko sodelujejo z uporabniki, drugimi agenti in okoljem za dosego določenih ciljev. Ti agenti lahko kažejo avtonomno vedenje, sprejemajo odločitve in se prilagajajo spreminjajočim se pogojem. Poglejmo nekaj ključnih zmogljivosti, ki jih omogočajo ogrodja AI agentov:

- **Sodelovanje in koordinacija agentov**: Omogočajo ustvarjanje več AI agentov, ki lahko delujejo skupaj, komunicirajo in se usklajujejo pri reševanju kompleksnih nalog.
- **Avtomatizacija in upravljanje nalog**: Nudijo mehanizme za avtomatizacijo večstopenjskih delovnih tokov, delegiranje nalog in dinamično upravljanje nalog med agenti.
- **Kontekstualno razumevanje in prilagajanje**: Opremljajo agente z zmožnostjo razumevanja konteksta, prilagajanja spreminjajočemu se okolju in sprejemanja odločitev na podlagi informacij v realnem času.

Torej povzemimo, agenti vam omogočajo več, dvignejo avtomatizacijo na naslednjo raven in ustvarijo bolj inteligentne sisteme, ki se lahko prilagajajo in učijo iz svojega okolja.

## Kako hitro izdelati prototip, iterirati in izboljšati zmogljivosti agenta?

To je hitro spreminjajoče se področje, vendar obstajajo nekatere skupne lastnosti večine ogrodij AI agentov, ki vam lahko pomagajo hitro izdelati prototipe in iterirati, in sicer modularne komponente, orodja za sodelovanje in učenje v realnem času. Poglobimo se v te teme:

- **Uporabite modularne komponente**: AI SDK-ji ponujajo vnaprej izdelane komponente, kot so AI in pomnilniški konektorji, klicanje funkcij z uporabo naravnega jezika ali vtičnikov za kodo, predloge pozivov in več.
- **Izkoristite orodja za sodelovanje**: Oblikujte agente z določenimi vlogami in nalogami, kar jim omogoča testiranje in izpopolnjevanje sodelovalnih delovnih tokov.
- **Učenje v realnem času**: Implementirajte povratne zanke, kjer se agenti učijo iz interakcij in dinamično prilagajajo svoje vedenje.

### Uporabite modularne komponente

SDK-ji, kot sta Microsoft Semantic Kernel in LangChain, ponujajo vnaprej izdelane komponente, kot so AI konektorji, predloge pozivov in upravljanje pomnilnika.

**Kako lahko ekipe to uporabijo**: Ekipe lahko hitro sestavijo te komponente, da ustvarijo funkcionalen prototip brez začetnega razvoja, kar omogoča hitro eksperimentiranje in iteriranje.

**Kako to deluje v praksi**: Lahko uporabite vnaprej izdelan parser za izvleček informacij iz uporabnikovega vnosa, modul pomnilnika za shranjevanje in pridobivanje podatkov ter generator pozivov za interakcijo z uporabniki, vse brez potrebe po gradnji teh komponent iz nič.

**Primer kode**. Oglejmo si primere, kako lahko uporabite vnaprej izdelan AI konektor s Semantic Kernel v Pythonu in .Net, ki uporablja samodejno klicanje funkcij, da model odgovori na uporabnikov vnos:

``` python
# Primer semantičnega jedra v Pythonu

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Določite objekt ChatHistory za shranjevanje konteksta pogovora
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Določite primer vtičnika, ki vsebuje funkcijo za rezervacijo potovanja
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Ustvarite jedro
kernel = Kernel()

# Dodajte primer vtičnika objektu jedra
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Določite povezovalnik AI Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Določite nastavitve zahteve za konfiguracijo modela z avtomatskim klicem funkcij
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Izvedite zahtevo modelu za dano zgodovino klepeta in nastavitve zahteve
    # Jedro vsebuje primer, ki ga bo model zahteval za izvedbo
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
    # Primer odgovora AI modela: `Vaš let do New Yorka 1. januarja 2025 je bil uspešno rezerviran. Srečno potovanje! ✈️🗽`

    # Dodajte odgovor modela v kontekst naše zgodovine klepeta
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

Iz tega primera lahko vidite, kako lahko izkoristite vnaprej izdelan parser za izvleček ključnih informacij iz uporabnikovega vnosa, kot so izvor, destinacija in datum zahteve za rezervacijo leta. Ta modularni pristop vam omogoča, da se osredotočite na logiko na visoki ravni.

### Izkoristite orodja za sodelovanje

Ogrodja, kot so CrewAI, Microsoft AutoGen in Semantic Kernel, olajšajo ustvarjanje več agentov, ki lahko delujejo skupaj.

**Kako lahko ekipe to uporabijo**: Ekipe lahko oblikujejo agente z določenimi vlogami in nalogami, kar jim omogoča testiranje in izpopolnjevanje sodelovalnih delovnih tokov ter izboljšanje splošne učinkovitosti sistema.

**Kako to deluje v praksi**: Lahko ustvarite ekipo agentov, kjer ima vsak agent specializirano funkcijo, na primer pridobivanje podatkov, analiza ali sprejemanje odločitev. Ti agenti lahko komunicirajo in delijo informacije, da dosežejo skupni cilj, na primer odgovorijo na uporabnikovo vprašanje ali dokončajo nalogo.

**Primer kode (AutoGen)**:

```python
# ustvarjanje agentov, nato ustvarite urnik round robin, kjer lahko sodelujejo, v tem primeru po vrsti

# Agent za pridobivanje podatkov
# Agent za analizo podatkov
# Agent za odločanje

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

# pogovor se konča, ko uporabnik reče "ODOBRI"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Uporabite asyncio.run(...), ko se izvaja v skripti.
await Console(stream)
```

Kar vidite v prejšnji kodi, je, kako lahko ustvarite nalogo, ki vključuje sodelovanje več agentov pri analizi podatkov. Vsak agent opravlja določeno funkcijo, naloga pa se izvede z usklajevanjem agentov za dosego želenega rezultata. Z ustvarjanjem namenskih agentov s specializiranimi vlogami lahko izboljšate učinkovitost in zmogljivost nalog.

### Učenje v realnem času

Napredna ogrodja zagotavljajo zmogljivosti za razumevanje konteksta in prilagajanje v realnem času.

**Kako lahko ekipe to uporabijo**: Ekipe lahko implementirajo povratne zanke, kjer se agenti učijo iz interakcij in dinamično prilagajajo svoje vedenje, kar vodi v stalno izboljševanje in izpopolnjevanje zmožnosti.

**Kako to deluje v praksi**: Agenti lahko analizirajo povratne informacije uporabnikov, podatke iz okolja in rezultate nalog, da posodobijo svojo bazo znanja, prilagodijo algoritme za sprejemanje odločitev in izboljšajo zmogljivost skozi čas. Ta iterativni proces učenja omogoča agentom, da se prilagajajo spreminjajočim se pogojem in uporabniškim preferencam ter izboljšajo splošno učinkovitost sistema.

## Kakšne so razlike med ogrodji AutoGen, Semantic Kernel in Azure AI Agent Service?

Obstaja veliko načinov primerjave teh ogrodij, poglejmo pa nekatere ključne razlike glede na njihovo zasnovo, zmogljivosti in ciljane primere uporabe:

## AutoGen

AutoGen je odprtokodno ogrodje, razvito v AI Frontiers Lab pri Microsoft Research. Osredotoča se na dogodkom vodene, distribuirane *agentne* aplikacije, ki omogočajo več LLM-jev in SLM-jev, orodij in napredne vzorce večagentnega oblikovanja.

AutoGen temelji na osnovnem konceptu agentov, ki so avtonomne entitete, ki zaznavajo svoje okolje, sprejemajo odločitve in izvajajo dejanja za dosego določenih ciljev. Agenti komunicirajo prek asinhronih sporočil, kar jim omogoča delovanje neodvisno in vzporedno, s čimer se poveča skalabilnost in odzivnost sistema.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenti temeljijo na modelu akterjev</a>. Po Wikipediji je akter _osnovna gradbena enota sočasnega računanja. V odzivu na prejeto sporočilo lahko akter: sprejme lokalne odločitve, ustvari več akterjev, pošlje več sporočil in določi, kako se odzvati na naslednje prejeto sporočilo_.

**Uporabni primeri**: avtomatizacija generiranja kode, naloge analize podatkov in gradnja prilagojenih agentov za načrtovanje in raziskovalne funkcije.

Tukaj so nekateri pomembni osnovni koncepti AutoGen:

- **Agenti**. Agent je programska entiteta, ki:
  - **Komunicira prek sporočil**, ta sporočila so lahko sinhrona ali asinhrona.
  - **Vzdržuje lastno stanje**, ki ga lahko spreminjajo dohodna sporočila.
  - **Izvaja dejanja** kot odziv na prejeta sporočila ali spremembe svojega stanja. Ta dejanja lahko spremenijo stanje agenta in povzročijo zunanje učinke, kot so posodabljanje dnevnikov sporočil, pošiljanje novih sporočil, izvajanje kode ali klici API-jev.
    
    Tu je kratka koda, v kateri ustvarite svojega agenta z zmogljivostmi klepeta:

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
    
    V prejšnji kodi je bil ustvarjen `MyAgent` in podeduje od `RoutedAgent`. Ima upravljalnik sporočil, ki izpiše vsebino sporočila in nato pošlje odgovor z uporabo delegata `AssistantAgent`. Posebej opazite, kako dodelimo `self._delegate` instanco `AssistantAgent`, ki je vnaprej izdelan agent, sposoben upravljati zaključke klepeta.


    Sporočimo AutoGenu ta tip agenta in nato zaženimo program:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Začni procesiranje sporočil v ozadju.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    V prejšnji kodi so agenti registrirani v runtime-u in nato je agentu poslan sporočilo, kar ima za rezultat naslednji izpis:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Več agentov**. AutoGen podpira ustvarjanje več agentov, ki lahko delujejo skupaj za dosego kompleksnih nalog. Agenti lahko komunicirajo, delijo informacije in usklajujejo svoja dejanja za učinkovitejše reševanje problemov. Za ustvarjanje sistema z več agenti lahko definirate različne tipe agentov z specializiranimi funkcijami in vlogami, kot so pridobivanje podatkov, analiza, sprejemanje odločitev in interakcija z uporabnikom. Poglejmo, kako takšno ustvarjanje izgleda, da dobimo občutek:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Primer deklaracije agenta
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Uporaba tipa teme kot tip agenta.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # preostale deklaracije skrajšane za jedrnatost

    # Skupinski klepet
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
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

    V prejšnji kodi imamo `GroupChatManager`, ki je registriran v runtime-u. Ta upravitelj je odgovoren za usklajevanje interakcij med različnimi tipi agentov, kot so pisci, ilustratorji, uredniki in uporabniki.

- **Runtime agentov**. Ogrodje zagotavlja runtime okolje, ki omogoča komunikacijo med agenti, upravlja njihove identitete in življenjske cikle ter zagotavlja varnostne in zasebnostne meje. To pomeni, da lahko svoje agente poganjate v varnem in nadzorovanem okolju, s čimer zagotovite, da lahko varno in učinkovito medsebojno delujejo. Obstajata dva runtima, ki jih je vredno omeniti:
  - **Samostojni runtime**. To je dobra izbira za aplikacije z enim procesom, kjer so vsi agenti implementirani v istem programskem jeziku in tečejo v istem procesu. Tukaj je ilustracija, kako deluje:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Samostojni runtime</a>   
Aplikacijski sklad

    *agenti komunicirajo prek sporočil prek runtime-a, in runtime upravlja življenjski cikel agentov*

  - **Distribuirani agentni runtime**, je primeren za aplikacije z več procesi, kjer so agenti lahko implementirani v različnih programskih jezikih in tečejo na različnih strojih. Tukaj je ilustracija, kako deluje:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distribuirani runtime</a>

## Semantic Kernel + Agent Framework

Semantic Kernel je podjetju primeren SDK za orkestracijo AI. Sestavljajo ga AI in pomnilniški konektorji ter ogrodje agentov.

Najprej obravnavajmo nekaj osnovnih komponent:

- **AI konektorji**: To je vmesnik do zunanjih AI storitev in virov podatkov za uporabo tako v Pythonu kot v C#.

  ```python
  # Semantično jedro Python
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

    Tu imate enostaven primer, kako lahko ustvarite kernel in dodate storitev za Chat Completion. Semantic Kernel vzpostavi povezavo z zunanjo AI storitvijo, v tem primeru Azure OpenAI Chat Completion.

- **Vtičniki**: Ti zapakirajo funkcije, ki jih aplikacija lahko uporablja. Obstajajo tako že pripravljeni vtičniki kot tudi lastni, ki jih lahko ustvarite. Soroden koncept so "prompt functions." Namesto da nudite naravne jezikovne namige za klic funkcij, oglašate določene funkcije modelu. Glede na trenutni kontekst klepeta se model lahko odloči poklicati eno izmed teh funkcij, da dokonča zahtevo ali poizvedbo. Tukaj je primer:

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

    Tu imate najprej predlogo poziva `skPrompt`, ki pusti prostor za vnos uporabnika, `$userInput`. Nato ustvarite kernel funkcijo `SummarizeText` in jo uvozite v kernel z imenom vtičnika `SemanticFunctions`. Upoštevajte ime funkcije, ki pomaga Semantic Kernelu razumeti, kaj funkcija počne in kdaj naj bo poklicana.

- **Nativne funkcije**: Obstajajo tudi nativne funkcije, ki jih ogrodje lahko neposredno pokliče za izvedbo naloge. Tukaj je primer take funkcije, ki pridobi vsebino iz datoteke:

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

- **Pomnilnik**: Apstraktira in poenostavlja upravljanje konteksta za AI aplikacije. Ideja s pomnilnikom je, da gre za informacije, ki bi jih LLM moral poznati. Te informacije lahko shranite v vektorsko bazo, ki je lahko v pomnilniku baza podatkov ali vektorska baza oziroma podobno. Tukaj je primer zelo poenostavljenega scenarija, kjer se *dejstva* dodajo v pomnilnik:

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

    Te dejstva se nato shranijo v zbirko pomnilnika `SummarizedAzureDocs`. To je zelo poenostavljen primer, vendar lahko vidite, kako lahko shranite informacije v pomnilnik, da jih LLM uporabi.

Torej to so osnove ogrodja Semantic Kernel, kaj pa Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service je bolj nedavna pridobitev, predstavljena na Microsoft Ignite 2024. Omogoča razvoj in uvajanje AI agentov z bolj prilagodljivimi modeli, kot je neposredno klicanje odprtokodnih LLM-jev, kot so Llama 3, Mistral in Cohere.

Azure AI Agent Service zagotavlja močnejše mehanizme varnosti za podjetja in metode shranjevanja podatkov, zaradi česar je primeren za poslovne aplikacije. 

Deluje iz škatle z okviri za orkestracijo več agentov, kot sta AutoGen in Semantic Kernel.

Ta storitev je trenutno v Public Preview in podpira Python in C# za gradnjo agentov.

Z uporabo Semantic Kernel Python lahko ustvarimo Azure AI Agenta z vtičnikom, ki ga določi uporabnik:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Določi vzorčni vtičnik za vzorec
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
        # Ustvari definicijo agenta
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Ustvari AzureAI agenta z uporabo definirane stranke in definicije agenta
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Ustvari nit za shranjevanje pogovora
        # Če ni podana nobena nit, bo ustvarjena nova nit
        # in vrnjena z začetnim odgovorom
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
                # Pokliči agenta za določeno nit
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

### Osnovni pojmi

Azure AI Agent Service ima naslednje osnovne koncepte:

- **Agent**. Azure AI Agent Service se integrira z Microsoft Foundry. Znotraj AI Foundry deluje AI agent kot "pameten" mikroservis, ki se lahko uporablja za odgovarjanje na vprašanja (RAG), izvajanje dejanj ali popolno avtomatizacijo delovnih tokov. To doseže s kombiniranjem moči generativnih AI modelov z orodji, ki mu omogočajo dostop do virov podatkov v realnem svetu in interakcijo z njimi. Tukaj je primer agenta:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    V tem primeru je agent ustvarjen z modelom `gpt-4o-mini`, imenom `my-agent` in navodili `You are helpful agent`. Agent je opremljen z orodji in viri za izvajanje nalog interpretacije kode.

- **Nit in sporočila**. Nit je še en pomemben koncept. Predstavlja pogovor ali interakcijo med agentom in uporabnikom. Niti se lahko uporabijo za sledenje napredka pogovora, shranjevanje kontekstnih informacij in upravljanje stanja interakcije. Tukaj je primer niti:

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

    V prejšnji kodi je ustvarjena nit. Nato se pošlje sporočilo v to nit. Z klicem `create_and_process_run` je agentu naročeno, naj opravi delo na niti. Na koncu se sporočila pridobijo in zabeležijo, da se vidi agentov odgovor. Sporočila kažejo napredek pogovora med uporabnikom in agentom. Pomembno je tudi razumeti, da so sporočila lahko različnih tipov, kot so besedilo, slika ali datoteka — to pomeni, da je agentovo delo na primer privedlo do slike ali besedilnega odgovora. Kot razvijalec lahko te informacije nato uporabite za nadaljnjo obdelavo odgovora ali njegovo prikazovanje uporabniku.

- **Povezovanje z drugimi AI okviri**. Storitev Azure AI Agent se lahko povezuje z drugimi ogrodji, kot sta AutoGen in Semantic Kernel, kar pomeni, da lahko del svoje aplikacije zgradite v enem izmed teh ogrodij in na primer uporabite to storitev kot orkestrator ali pa vse zgradite v njej.

**Primeri uporabe**: Azure AI Agent Service je zasnovana za poslovne aplikacije, ki zahtevajo varno, razširljivo in prilagodljivo uvajanje AI agentov.

## Kakšna je razlika med temi ogrodji?
 
Zdi se, da je med temi ogrodji veliko prekrivanja, vendar obstajajo ključne razlike glede na njihovo zasnovo, zmožnosti in ciljne primere uporabe:
 
- **AutoGen**: Je okvir za eksperimentiranje, osredotočen na najsodobnejše raziskave sistemov z več agenti. Je najboljše mesto za preizkušanje in prototipiranje zapletenih sistemov z več agenti.
- **Semantic Kernel**: Je knjižnica agentov pripravljena za produkcijo za gradnjo poslovnih agentskih aplikacij. Osredotoča se na dogodkovno vodene, distribuirane agentske aplikacije, omogoča uporabo več LLM-jev in SLM-jev, orodij ter oblikovalskih vzorcev za enega ali več agentov.
- **Azure AI Agent Service**: Je platforma in storitev za uvajanje v Azure Foundry za agente. Ponuja možnosti povezovanja s storitvami, ki jih podpira Azure Foundry, kot so Azure OpenAI, Azure AI Search, Bing Search in izvajanje kode.
 
Še vedno niste prepričani, katerega izbrati?

### Primeri uporabe
 
Poglejmo, ali vam lahko pomagamo s predstavitvijo nekaj pogostih primerov uporabe:
 
> Q: Eksperimentiram, se učim in ustvarjam proof-of-concept aplikacije agentov, ter želim hitro graditi in eksperimentirati
>
>
>A: AutoGen bi bila dobra izbira za ta scenarij, saj se osredotoča na dogodkovno vodene, distribuirane agentske aplikacije in podpira napredne oblikovalske vzorce za več agentov.

> Q: Kaj naredi AutoGen boljšo izbiro kot Semantic Kernel in Azure AI Agent Service za ta primer uporabe?
>
> A: AutoGen je posebej zasnovan za dogodkovno vodene, distribuirane agentske aplikacije, zaradi česar je dobro primeren za avtomatizacijo nalog generiranja kode in analize podatkov. Ponuja potrebna orodja in zmogljivosti za učinkovito gradnjo kompleksnih sistemov z več agenti.

>Q: Zdi se, da bi Azure AI Agent Service prav tako lahko deloval tukaj, saj ima orodja za generiranje kode in še več?

>
> A: Da, Azure AI Agent Service je platformna storitev za agente in dodaja vgrajene zmožnosti za več modelov, Azure AI Search, Bing Search in Azure Functions. Omogoča enostavno gradnjo agentov v Foundry portalu in njihovo uvajanje v obsegu.

> Q: Še vedno sem zmeden, dajte mi eno možnost
>
> A: Odlična izbira je, da najprej zgradite svojo aplikacijo v Semantic Kernel in nato uporabite Azure AI Agent Service za uvajanje vašega agenta. Ta pristop vam omogoča enostavno vzdrževanje agentov ob hkratnem izkoriščanju moči za gradnjo sistemov z več agenti v Semantic Kernel. Poleg tega ima Semantic Kernel konektor v AutoGen, kar olajša uporabo obeh ogrodij skupaj.
 
Povzemimo ključne razlike v tabeli:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Dogodkovno vodene, distribuirane agentske aplikacije | Agenti, persone, funkcije, podatki | Generiranje kode, naloge analize podatkov |
| Semantic Kernel | Razumevanje in generiranje besedila podobnega človeškemu | Agenti, modularne komponente, sodelovanje | Razumevanje naravnega jezika, ustvarjanje vsebin |
| Azure AI Agent Service | Prilagodljivi modeli, varnost za podjetja, generiranje kode, klicanje orodij | Modularnost, sodelovanje, orkestracija procesov | Varen, razširljiv in prilagodljiv način uvajanja AI agentov |

Kateri je idealen primer uporabe za vsak od teh ogrodij?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

Odgovor je da — lahko neposredno integrirate obstoječa orodja iz Azure ekosistema, še posebej z Azure AI Agent Service, saj je bila zgrajena za nemoteno delovanje z drugimi Azure storitvami. Na primer lahko integrirate Bing, Azure AI Search in Azure Functions. Obstaja tudi globoka integracija z Microsoft Foundry.

Za AutoGen in Semantic Kernel se lahko prav tako povežete z Azure storitvami, vendar boste morda morali klicati Azure storitve iz vaše kode. Druga možnost integracije je uporaba Azure SDK-jev za interakcijo z Azure storitvami iz vaših agentov. Poleg tega, kot je omenjeno, lahko uporabite Azure AI Agent Service kot orkestrator za agente, zgrajene v AutoGen ali Semantic Kernel, kar omogoča enostaven dostop do Azure ekosistema.

## Vzorčne kode

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), da spoznate druge učence, se udeležite uradnih ur in dobite odgovore na vprašanja o AI agentih.

## References

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Storitev Azure Agent</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel in AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel: Python ogrodje agentov</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel: .Net ogrodje agentov</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Storitev Azure AI Agent</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Uporaba Azure AI Agent Service z AutoGen / Semantic Kernel za izgradnjo rešitve z več agenti</a>

## Previous Lesson

[Uvod v AI agente in primere uporabe agentov](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Razumevanje agentskih oblikovalskih vzorcev](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Izjava o omejitvi odgovornosti:
Ta dokument je bil preveden z uporabo storitve za prevajanje z umetno inteligenco [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da avtomatizirani prevodi lahko vsebujejo napake ali netočnosti. Izvirni dokument v njegovem izvirnem jeziku naj velja za avtoritativni vir. Za kritične informacije priporočamo strokovni prevod, opravljen s strani človeka. Nismo odgovorni za morebitne nesporazume ali napačne razlage, ki izhajajo iz uporabe tega prevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->