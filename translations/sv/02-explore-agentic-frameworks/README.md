[![Utforska AI-agentramverk](../../../translated_images/sv/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Klicka på bilden ovan för att se videon för denna lektion)_

# Utforska AI-agentramverk

AI-agentramverk är programvaruplattformar utformade för att förenkla skapandet, driftsättningen och hanteringen av AI-agenter. Dessa ramverk förser utvecklare med färdiga komponenter, abstraktioner och verktyg som effektiviserar utvecklingen av komplexa AI-system.

Dessa ramverk hjälper utvecklare att fokusera på de unika aspekterna av sina applikationer genom att erbjuda standardiserade tillvägagångssätt för vanliga utmaningar inom utveckling av AI-agenter. De förbättrar skalbarhet, tillgänglighet och effektivitet vid byggandet av AI-system.

## Introduktion 

Denna lektion kommer att behandla:

- Vad är AI Agent Frameworks och vad möjliggör de för utvecklare?
- Hur kan team använda dessa för att snabbt prototypla, iterera och förbättra sin agents kapabiliteter?
- Vad är skillnaderna mellan de ramverk och verktyg som skapats av Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, och <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Kan jag integrera mina befintliga verktyg i Azure-ekosystemet direkt, eller behöver jag fristående lösningar?
- Vad är Azure AI Agents service och hur hjälper detta mig?

## Lärandemål

Målen med denna lektion är att hjälpa dig att förstå:

- Rollen som AI-agentramverk har i AI-utveckling.
- Hur man använder AI-agentramverk för att bygga intelligenta agenter.
- Nyckelfunktioner som möjliggörs av AI-agentramverk.
- Skillnaderna mellan AutoGen, Semantic Kernel och Azure AI Agent Service.

## Vad är AI-agentramverk och vad möjliggör de för utvecklare?

Traditionella AI-ramverk kan hjälpa dig integrera AI i dina appar och göra dessa appar bättre på följande sätt:

- **Personalisering**: AI kan analysera användarbeteende och preferenser för att ge personliga rekommendationer, innehåll och upplevelser.
Example: Streamingtjänster som Netflix använder AI för att föreslå filmer och serier baserat på visningshistorik, vilket ökar användarengagemang och nöjdhet.
- **Automatisering och effektivitet**: AI kan automatisera repetitiva uppgifter, strömlinjeforma arbetsflöden och förbättra driftseffektiviteten.
Example: Kundserviceappar använder AI-drivna chattbottar för att hantera vanliga förfrågningar, vilket minskar svarstider och frigör mänskliga agenter för mer komplexa ärenden.
- **Förbättrad användarupplevelse**: AI kan förbättra den övergripande användarupplevelsen genom att erbjuda intelligenta funktioner såsom röstigenkänning, naturlig språkbehandling och prediktiv text.
Example: Virtuella assistenter som Siri och Google Assistant använder AI för att förstå och svara på röstkommandon, vilket gör det enklare för användare att interagera med sina enheter.

### Det låter ju bra, men varför behöver vi då AI-agentramverket?

AI-agentramverk representerar något mer än bara AI-ramverk. De är utformade för att möjliggöra skapandet av intelligenta agenter som kan interagera med användare, andra agenter och miljön för att uppnå specifika mål. Dessa agenter kan uppvisa autonomt beteende, fatta beslut och anpassa sig till förändrade förhållanden. Låt oss titta på några nyckelfunktioner som AI-agentramverk möjliggör:

- **Agent-samarbete och koordinering**: Möjliggör skapandet av flera AI-agenter som kan arbeta tillsammans, kommunicera och koordinera för att lösa komplexa uppgifter.
- **Automatisering och uppgiftshantering**: Erbjuder mekanismer för att automatisera flerstegade arbetsflöden, uppgiftsdelegering och dynamisk uppgiftshantering mellan agenter.
- **Kontextuell förståelse och anpassning**: Utrusta agenter med förmågan att förstå kontext, anpassa sig till förändrade miljöer och fatta beslut baserade på realtidsinformation.

Sammanfattningsvis tillåter agenter dig att göra mer, ta automatisering till nästa nivå och skapa mer intelligenta system som kan anpassa sig och lära av sin miljö.

## Hur man snabbt prototypar, itererar och förbättrar agentens förmågor?

Detta är ett snabbt föränderligt område, men det finns några saker som är vanliga för de flesta AI-agentramverk som kan hjälpa dig att snabbt prototypla och iterera, nämligen modulkomponenter, samarbetsverktyg och realtidsinlärning. Låt oss dyka in i dessa:

- **Använd modulära komponenter**: AI-SDK:er erbjuder färdiga komponenter såsom AI- och minneskopplingar, funktionsanrop via naturligt språk eller kod-plugins, promptmallar och mer.
- **Utnyttja samarbetsverktyg**: Designa agenter med specifika roller och uppgifter, vilket gör det möjligt för dem att testa och förfina kollaborativa arbetsflöden.
- **Lär i realtid**: Implementera feedbackloopar där agenter lär sig av interaktioner och justerar sitt beteende dynamiskt.

### Använd modulära komponenter

SDK:er som Microsoft Semantic Kernel och LangChain erbjuder färdiga komponenter såsom AI-kopplingar, promptmallar och minneshantering.

**Hur team kan använda dessa**: Team kan snabbt sätta ihop dessa komponenter för att skapa en fungerande prototyp utan att börja från början, vilket möjliggör snabb experimentering och iteration.

**Hur det fungerar i praktiken**: Du kan använda en förbyggd parser för att extrahera information från användarens inmatning, en minnesmodul för att lagra och hämta data, och en promptgenerator för att interagera med användare, allt utan att behöva bygga dessa komponenter från grunden.

**Exempelkod**. Låt oss titta på exempel på hur du kan använda en förbyggd AI-connector med Semantic Kernel Python och .Net som använder autoreglerat funktionsanrop för att få modellen att svara på användarinmatning:

``` python
# Semantic Kernel Python-exempel

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definiera ett ChatHistory-objekt för att hålla konversationens kontext
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definiera ett exempelplugin som innehåller funktionen för att boka resa
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Skapa kärnan
kernel = Kernel()

# Lägg till exempelpluginet i Kernel-objektet
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definiera Azure OpenAI AI-anslutningen
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definiera förfrågningsinställningarna för att konfigurera modellen med automatisk funktionsanrop
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Skicka förfrågan till modellen för den givna chattloggen och förfrågningsinställningarna
    # Kärnan innehåller exemplet som modellen kommer att begära att anropa
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
    # Exempel på AI-modellens svar: `Din flygning till New York den 1 januari 2025 har bokats framgångsrikt. Trevlig resa! ✈️🗽`

    # Lägg till modellens svar till vår chattloggskontext
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

Vad du kan se från detta exempel är hur du kan använda en förbyggd parser för att extrahera nyckelinformation från användarinmatning, såsom avreseort, destination och datum för en flygbokningsförfrågan. Detta modulära tillvägagångssätt låter dig fokusera på den övergripande logiken.

### Utnyttja samarbetsverktyg

Ramverk som CrewAI, Microsoft AutoGen och Semantic Kernel underlättar skapandet av flera agenter som kan arbeta tillsammans.

**Hur team kan använda dessa**: Team kan designa agenter med specifika roller och uppgifter, vilket gör det möjligt att testa och förfina kollaborativa arbetsflöden och förbättra systemets totala effektivitet.

**Hur det fungerar i praktiken**: Du kan skapa ett team av agenter där varje agent har en specialiserad funktion, såsom datainhämtning, analys eller beslutsfattande. Dessa agenter kan kommunicera och dela information för att uppnå ett gemensamt mål, såsom att besvara en användarfråga eller slutföra en uppgift.

**Exempelkod (AutoGen)**:

```python
# skapa agenter, sedan skapa ett round robin-schema där de kan arbeta tillsammans, i det här fallet i ordning

# Agent för datainhämtning
# Agent för dataanalys
# Agent för beslutsfattande

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

# konversationen avslutas när användaren säger "GODKÄNN"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Använd asyncio.run(...) när du kör i ett skript.
await Console(stream)
```

Vad du ser i den tidigare koden är hur du kan skapa en uppgift som involverar flera agenter som arbetar tillsammans för att analysera data. Varje agent utför en specifik funktion, och uppgiften exekveras genom att koordinera agenternas handlingar för att uppnå önskat resultat. Genom att skapa dedikerade agenter med specialiserade roller kan du förbättra uppgiftseffektiviteten och prestandan.

### Lär i realtid

Avancerade ramverk erbjuder kapabiliteter för kontextförståelse och anpassning i realtid.

**Hur team kan använda dessa**: Team kan implementera feedbackloopar där agenter lär sig av interaktioner och justerar sitt beteende dynamiskt, vilket leder till kontinuerlig förbättring och förfining av kapabiliteter.

**Hur det fungerar i praktiken**: Agenter kan analysera användarfeedback, miljödata och uppgiftsresultat för att uppdatera sin kunskapsbas, justera beslutsalgoritmer och förbättra prestandan över tid. Denna iterativa inlärningsprocess gör det möjligt för agenter att anpassa sig till förändrade förhållanden och användarpreferenser, vilket förbättrar systemets effektivitet.

## Vad är skillnaderna mellan ramverken AutoGen, Semantic Kernel och Azure AI Agent Service?

Det finns många sätt att jämföra dessa ramverk, men låt oss titta på några viktiga skillnader vad gäller deras design, kapabiliteter och målgruppsanvändningsfall:

## AutoGen

AutoGen är ett open-source-ramverk utvecklat av Microsoft Researchs AI Frontiers Lab. Det fokuserar på händelsestyrda, distribuerade *agentiska* applikationer, och möjliggör flera LLMs och SLMs, verktyg och avancerade mönster för multi-agentdesign.

AutoGen är byggt kring kärnkonceptet agenter, vilka är autonoma enheter som kan uppfatta sin omgivning, fatta beslut och vidta åtgärder för att nå specifika mål. Agenter kommunicerar via asynkrona meddelanden, vilket tillåter dem att arbeta självständigt och parallellt, vilket ökar systemets skalbarhet och responsivitet.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenter bygger på aktormodellen</a>. Enligt Wikipedia är en aktor _det grundläggande byggblocket för samtidig beräkning. Som svar på ett meddelande den tar emot kan en aktor: fatta lokala beslut, skapa fler aktorer, skicka fler meddelanden, och avgöra hur den ska svara på nästa mottagna meddelande_.

**Användningsfall**: Automatisering av kodgenerering, dataanalysuppgifter och att bygga anpassade agenter för planerings- och forskningsfunktioner.

Här är några viktiga kärnkoncept i AutoGen:

- **Agenter**. En agent är en mjukvaruenhet som:
  - **Kommunicerar via meddelanden**, dessa meddelanden kan vara synkrona eller asynkrona.
  - **Bibehåller sitt eget tillstånd**, som kan ändras av inkommande meddelanden.
  - **Utför åtgärder** som svar på mottagna meddelanden eller ändringar i sitt tillstånd. Dessa åtgärder kan ändra agentens tillstånd och ge externa effekter, såsom att uppdatera meddelandeloggar, skicka nya meddelanden, köra kod eller göra API-anrop.
    
  Här har du ett kort kodexempel där du skapar din egen agent med chattfunktionalitet:

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
    
    I den föregående koden har `MyAgent` skapats och ärver från `RoutedAgent`. Den har en meddelandehanterare som skriver ut innehållet i meddelandet och sedan skickar ett svar med hjälp av delegaten `AssistantAgent`. Notera särskilt hur vi tilldelar `self._delegate` en instans av `AssistantAgent` som är en färdig agent som kan hantera chattkompletteringar.


    Låt oss informera AutoGen om denna agenttyp och starta programmet härnäst:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Börja bearbeta meddelanden i bakgrunden.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    I den tidigare koden registreras agenterna i runtime-miljön och sedan skickas ett meddelande till agenten vilket resulterar i följande utdata:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Flera agenter**. AutoGen stödjer skapandet av flera agenter som kan arbeta tillsammans för att uppnå komplexa uppgifter. Agenter kan kommunicera, dela information och koordinera sina handlingar för att lösa problem mer effektivt. För att skapa ett multi-agent-system kan du definiera olika typer av agenter med specialiserade funktioner och roller, såsom datainhämtning, analys, beslutsfattande och användarinteraktion. Låt oss se hur en sådan skapelse ser ut så att vi får en känsla för det:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Exempel på att deklarera en Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Använder ämnestyp som agenttyp.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # återstående deklarationer förkortade för korthet

    # Gruppchatt
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

    I den tidigare koden har vi en `GroupChatManager` som är registrerad i runtime. Denna manager ansvarar för att koordinera interaktionerna mellan olika typer av agenter, såsom författare, illustratörer, redaktörer och användare.

- **Agentkörtid**. Ramverket tillhandahåller en runtime-miljö som möjliggör kommunikation mellan agenter, hanterar deras identiteter och livscykler samt upprätthåller säkerhets- och sekretessgränser. Detta innebär att du kan köra dina agenter i en säker och kontrollerad miljö, vilket försäkrar att de kan interagera säkert och effektivt. Det finns två körtider av intresse:
  - **Fristående körtid**. Detta är ett bra val för enprocessapplikationer där alla agenter implementeras i samma programmeringsspråk och körs i samma process. Här är en illustration av hur det fungerar:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Fristående körtid</a>   
Applikationsstack

    *agenter kommunicerar via meddelanden genom runtime, och runtime hanterar agenternas livscykel*

  - **Distribuerad agentkörtid**, är lämplig för multiprocessapplikationer där agenter kan vara implementerade i olika programmeringsspråk och köras på olika maskiner. Här är en illustration av hur det fungerar:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distribuerad körtid</a>

## Semantic Kernel + Agentramverk

Semantic Kernel är ett företagsredo AI-orkestrerings-SDK. Det består av AI- och minneskopplingar, tillsammans med ett agentramverk.

Låt oss först gå igenom några kärnkomponenter:

- **AI Connectors**: Detta är ett gränssnitt mot externa AI-tjänster och datakällor för användning i både Python och C#.

  ```python
  # Semantisk kärna Python
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

    Här har du ett enkelt exempel på hur du kan skapa en kernel och lägga till en chattkompletteringstjänst. Semantic Kernel skapar en anslutning till en extern AI-tjänst, i detta fall Azure OpenAI Chat Completion.

- **Plugins**: Dessa kapslar in funktioner som en applikation kan använda. Det finns både färdiga plugins och anpassade som du kan skapa. Ett relaterat koncept är "prompt-funktioner". Istället för att tillhandahålla naturliga språkledtrådar för funktionsanrop, sänder du ut vissa funktioner till modellen. Baserat på den aktuella chattkontexten kan modellen välja att anropa en av dessa funktioner för att slutföra en förfrågan eller fråga. Här är ett exempel:

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

    Här har du först en mallprompt `skPrompt` som lämnar utrymme för användaren att mata in text, `$userInput`. Sedan skapar du kernelfunktionen `SummarizeText` och importerar den därefter till kernel med plugin-namnet `SemanticFunctions`. Notera funktionsnamnet som hjälper Semantic Kernel att förstå vad funktionen gör och när den bör anropas.

- **Inbyggd funktion**: Det finns också inbyggda funktioner som ramverket kan anropa direkt för att utföra uppgiften. Här är ett exempel på en sådan funktion som hämtar innehållet från en fil:

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

- **Minne**:  Abstraherar och förenklar kontexthantering för AI-appar. Idén med minne är att detta är något som LLM:en bör känna till. Du kan lagra denna information i en vektorlager som i slutändan blir en minnesdatabas eller en vektordatabas eller liknande. Här är ett exempel på ett mycket förenklat scenario där *fakta* läggs till i minnet:

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

    Dessa fakta lagras sedan i minnessamlingen `SummarizedAzureDocs`. Detta är ett mycket förenklat exempel, men du kan se hur du kan lagra information i minnet för LLM att använda.

So that's the basics of the Semantic Kernel framework, what about the Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service är ett nyare tillskott, introducerat på Microsoft Ignite 2024. Det möjliggör utveckling och distribution av AI-agenter med mer flexibla modeller, såsom att direkt anropa öppna LLM-modeller som Llama 3, Mistral och Cohere.

Azure AI Agent Service erbjuder starkare säkerhetsmekanismer för företag och metoder för datalagring, vilket gör det lämpligt för företagsapplikationer. 

Det fungerar direkt (out-of-the-box) med multi-agent orkestreringsramverk som AutoGen och Semantic Kernel.

Denna tjänst är för närvarande i Public Preview och stödjer Python och C# för att bygga agenter.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definiera ett exempelplugin för exemplet
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
        # Skapa agentdefinition
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Skapa AzureAI Agent med den definierade klienten och agentdefinitionen
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Skapa en tråd för att hålla konversationen
        # Om ingen tråd tillhandahålls kommer en ny tråd att
        # skapas och returneras med det initiala svaret
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
                # Anropa agenten för den angivna tråden
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

### Kärnkoncept

Azure AI Agent Service har följande kärnkoncept:

- **Agent**. Azure AI Agent Service integreras med Microsoft Foundry. Inom AI Foundry fungerar en AI-agent som en "smart" mikrotjänst som kan användas för att besvara frågor (RAG), utföra åtgärder eller helt automatisera arbetsflöden. Detta uppnås genom att kombinera kraften i generativa AI-modeller med verktyg som låter den få åtkomst till och interagera med verkliga datakällor. Här är ett exempel på en agent:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    I det här exemplet skapas en agent med modellen `gpt-4o-mini`, ett namn `my-agent` och instruktionerna `You are helpful agent`. Agenten är utrustad med verktyg och resurser för att utföra kodtolkningsuppgifter.

- **Tråd och meddelanden**. Tråden är ett annat viktigt koncept. Den representerar en konversation eller interaktion mellan en agent och en användare. Trådar kan användas för att följa en konversations utveckling, lagra kontextinformation och hantera tillståndet i interaktionen. Här är ett exempel på en tråd:

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

    I den föregående koden skapas en tråd. Därefter skickas ett meddelande till tråden. Genom att anropa `create_and_process_run` blir agenten ombedd att utföra arbete på tråden. Slutligen hämtas meddelandena och loggas för att se agentens svar. Meddelandena visar konversationens förlopp mellan användaren och agenten. Det är också viktigt att förstå att meddelandena kan vara av olika typer, såsom text, bild eller fil — det vill säga att agentens arbete har resulterat i exempelvis en bild eller ett textsvar. Som utvecklare kan du sedan använda denna information för att bearbeta svaret vidare eller presentera det för användaren.

- **Integreras med andra AI-ramverk**. Azure AI Agent Service kan interagera med andra ramverk som AutoGen och Semantic Kernel, vilket innebär att du kan bygga en del av din app i ett av dessa ramverk och till exempel använda Agent-tjänsten som orkestrator, eller bygga allt i Agent-tjänsten.

**Användningsfall**: Azure AI Agent Service är utformat för företagsapplikationer som kräver säker, skalbar och flexibel distribution av AI-agenter.

## Vad är skillnaden mellan dessa ramverk?
 
Det kan verka som att det finns mycket överlappning mellan dessa ramverk, men det finns några viktiga skillnader när det gäller deras design, kapaciteter och vilka användningsfall de riktar sig mot:
 
- **AutoGen**: Är ett experimentellt ramverk inriktat på banbrytande forskning om multi-agent-system. Det är den bästa platsen för att experimentera och skapa prototyper av sofistikerade multi-agent-system.
- **Semantic Kernel**: Är ett produktionsklart agentbibliotek för att bygga företagsagentiska applikationer. Fokuserar på händelsestyrda, distribuerade agentapplikationer, vilket möjliggör flera LLMs och SLMs, verktyg samt designmönster för en- och flermedlemsagenter.
- **Azure AI Agent Service**: Är en plattform och distributionsservice i Azure Foundry för agenter. Den erbjuder bygg- och anslutningsmöjligheter till tjänster som stöds av Azure Foundry såsom Azure OpenAI, Azure AI Search, Bing Search och kodexekvering.
 
Still not sure which one to choose?

### Användningsfall
 
Let's see if we can help you by going through some common use cases:
 
> Q: I'm experimenting, learning and building proof-of-concept agent applications, and I want to be able to build and experiment quickly
>

>A: AutoGen would be a good choice for this scenario, as it focuses on event-driven, distributed agentic applications and supports advanced multi-agent design patterns.

> Q: What makes AutoGen a better choice than Semantic Kernel and Azure AI Agent Service for this use case?
>
> A: AutoGen is specifically designed for event-driven, distributed agentic applications, making it well-suited for automating code generation and data analysis tasks. It provides the necessary tools and capabilities to build complex multi-agent systems efficiently.

>Q: Sounds like Azure AI Agent Service could work here too, it has tools for code generation and more?

>
> A: Yes, Azure AI Agent Service is a platform service for agents and add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. It makes it easy to build your agents in the Foundry Portal and deploy them at scale.
 
> Q: I'm still confused just give me one option
>
> A: A great choice is to build your application in Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. This approach allows you to easily persist your agents while leveraging the power to build multi-agent systems in Semantic Kernel. Additionally, Semantic Kernel has a connector in AutoGen, making it easy to use both frameworks together.
 
Let's summarize the key differences in a table:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Händelsestyrda, distribuerade agentapplikationer | Agenter, Personas, Funktioner, Data | Kodgenerering, dataanalysuppgifter |
| Semantic Kernel | Förståelse och generering av människoliknande textinnehåll | Agenter, Modulära komponenter, Samarbete | Naturlig språkförståelse, innehållsgenerering |
| Azure AI Agent Service | Flexibla modeller, företagsäkerhet, kodgenerering, verktygsanrop | Modularitet, Samarbete, Processorkestrering | Säker, skalbar och flexibel distribution av AI-agenter |

What's the ideal use case for each of these frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

Svaret är ja — du kan integrera dina befintliga Azure-ekosystemverktyg direkt, särskilt med Azure AI Agent Service, eftersom den är byggd för att fungera sömlöst med andra Azure-tjänster. Du kan till exempel integrera Bing, Azure AI Search och Azure Functions. Det finns också djup integration med Microsoft Foundry.

För AutoGen och Semantic Kernel kan du också integrera med Azure-tjänster, men det kan kräva att du anropar Azure-tjänsterna från din kod. Ett annat sätt att integrera är att använda Azure SDK:er för att interagera med Azure-tjänster från dina agenter. Dessutom, som nämnts, kan du använda Azure AI Agent Service som en orkestrator för dina agenter byggda i AutoGen eller Semantic Kernel, vilket ger enkel tillgång till Azure-ekosystemet.

## Kodexempel

- Python: [Agentramverk](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agentramverk](./code_samples/02-dotnet-agent-framework.md)

## Har du fler frågor om AI-agentramverk?

Gå med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) för att träffa andra som lär sig, delta i kontorstider och få dina frågor om AI-agenter besvarade.

## Referenser

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agenttjänst</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel och AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent-ramverk</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent-ramverk</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent-tjänst</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Att använda Azure AI Agent Service med AutoGen / Semantic Kernel för att bygga en multi-agent-lösning</a>

## Föregående lektion

[Introduktion till AI-agenter och agentanvändningsfall](../01-intro-to-ai-agents/README.md)

## Nästa lektion

[Förstå agentiska designmönster](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfriskrivning:
Detta dokument har översatts med hjälp av AI-översättningstjänsten Co-op Translator (https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet, observera att automatiska översättningar kan innehålla fel eller felaktigheter. Det ursprungliga dokumentet på dess ursprungliga språk bör anses vara den auktoritativa källan. För viktig information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår till följd av användningen av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->