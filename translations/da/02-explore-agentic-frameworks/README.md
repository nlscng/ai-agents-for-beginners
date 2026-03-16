[![Udforsk AI-agentrammer](../../../translated_images/da/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Klik på billedet ovenfor for at se videoen til denne lektion)_

# Udforsk AI-agentrammer

AI-agentrammer er softwareplatforme designet til at forenkle oprettelsen, udrulningen og styringen af AI-agenter. Disse rammer giver udviklere forudbyggede komponenter, abstraktioner og værktøjer, der effektiviserer udviklingen af komplekse AI-systemer.

Disse rammer hjælper udviklere med at fokusere på de unikke aspekter af deres applikationer ved at tilbyde standardiserede tilgange til almindelige udfordringer i udvikling af AI-agenter. De forbedrer skalerbarhed, tilgængelighed og effektivitet i opbygningen af AI-systemer.

## Introduktion 

Denne lektion vil dække:

- Hvad er AI-agentrammer, og hvad gør de muligt for udviklere at opnå?
- Hvordan kan teams bruge dem til hurtigt at prototype, iterere og forbedre deres agents evner?
- Hvad er forskellene mellem de rammer og værktøjer, som Microsoft har skabt: <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, og <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Kan jeg integrere mine eksisterende Azure-økosystemværktøjer direkte, eller har jeg brug for selvstændige løsninger?
- Hvad er Azure AI Agents-tjenesten, og hvordan hjælper den mig?

## Læringsmål

Målsætningen med denne lektion er at hjælpe dig med at forstå:

- Rollen for AI-agentrammer i AI-udvikling.
- Hvordan man udnytter AI-agentrammer til at bygge intelligente agenter.
- Centrale kapabiliteter, som AI-agentrammer muliggør.
- Forskellene mellem AutoGen, Semantic Kernel og Azure AI Agent Service.

## Hvad er AI Agent Frameworks og hvad gør de det muligt for udviklere at gøre?

Traditionelle AI-rammer kan hjælpe dig med at integrere AI i dine apps og gøre disse apps bedre på følgende måder:

- **Personalisering**: AI kan analysere brugeradfærd og præferencer for at give personlige anbefalinger, indhold og oplevelser.
Example: Streamingtjenester som Netflix bruger AI til at foreslå film og shows baseret på seerhistorik, hvilket øger brugerengagement og tilfredshed.
- **Automatisering og effektivitet**: AI kan automatisere gentagne opgaver, strømline arbejdsprocesser og forbedre operationel effektivitet.
Example: Kundeserviceapps bruger AI-drevne chatbots til at håndtere almindelige henvendelser, hvilket reducerer svartider og frigør menneskelige agenter til mere komplekse problemer.
- **Forbedret brugeroplevelse**: AI kan forbedre den samlede brugeroplevelse ved at levere intelligente funktioner som stemmegenkendelse, naturlig sprogbehandling og forudsigende tekst.
Example: Virtuelle assistenter som Siri og Google Assistant bruger AI til at forstå og svare på talekommandoer, hvilket gør det lettere for brugere at interagere med deres enheder.

### Det lyder jo godt, så hvorfor har vi brug for AI-agentrammen?

AI-agentrammer repræsenterer noget mere end blot AI-rammer. De er designet til at muliggøre oprettelsen af intelligente agenter, der kan interagere med brugere, andre agenter og miljøet for at opnå specifikke mål. Disse agenter kan udvise autonom adfærd, træffe beslutninger og tilpasse sig ændrede forhold. Lad os se på nogle nøglekapabiliteter, som AI-agentrammer muliggør:

- **Agent-samarbejde og koordinering**: Muliggør oprettelsen af flere AI-agenter, der kan arbejde sammen, kommunikere og koordinere for at løse komplekse opgaver.
- **Opgaveautomatisering og -styring**: Tilbyder mekanismer til automatisering af flertrinsarbejdsgange, opgavedeling og dynamisk opgavestyring blandt agenter.
- **Kontekstforståelse og tilpasning**: Udstyrer agenter med evnen til at forstå kontekst, tilpasse sig ændrede miljøer og træffe beslutninger baseret på realtidsinformation.

Sammenfattende giver agenter dig mulighed for at gøre mere, tage automatisering til næste niveau og skabe mere intelligente systemer, der kan tilpasse sig og lære af deres miljø.

## Hvordan hurtigt prototype, iterere og forbedre agentens evner?

Dette er et hastigt skiftende landskab, men der er nogle ting, der er fælles for de fleste AI-agentrammer, som kan hjælpe dig med hurtigt at prototype og iterere, nemlig modulære komponenter, samarbejdsværktøjer og læring i realtid. Lad os dykke ned i disse:

- **Brug modulære komponenter**: AI-SDK'er tilbyder forudbyggede komponenter såsom AI- og hukommelsesforbindelser, funktionskald ved brug af naturligt sprog eller kode-plugins, prompt-skabeloner og mere.
- **Udnyt samarbejdsværktøjer**: Design agenter med specifikke roller og opgaver, så de kan teste og forfine samarbejdsarbejdsgange.
- **Lær i realtid**: Implementer feedbackloops, hvor agenter lærer af interaktioner og justerer deres adfærd dynamisk.

### Brug modulære komponenter

SDK'er som Microsoft Semantic Kernel og LangChain tilbyder forudbyggede komponenter såsom AI-forbindelser, prompt-skabeloner og hukommelsesstyring.

**Hvordan teams kan bruge disse**: Teams kan hurtigt samle disse komponenter for at skabe en funktionel prototype uden at starte fra bunden, hvilket muliggør hurtig eksperimentering og iteration.

**Hvordan det fungerer i praksis**: Du kan bruge en forudbygget parser til at udtrække oplysninger fra brugerinput, en hukommelsesmodul til at gemme og hente data og en prompt-generator til at interagere med brugere, alt sammen uden at skulle bygge disse komponenter fra bunden.

**Eksempelkode**. Lad os se på eksempler på, hvordan du kan bruge en forudbygget AI-Connector med Semantic Kernel Python og .Net, der bruger auto-function calling for at få modellen til at svare på brugerinput:

``` python
# Semantic Kernel Python eksempel

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definér et ChatHistory-objekt til at holde samtalens kontekst
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definér en prøveplugin, som indeholder funktionen til at booke rejse
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Opret Kernel
kernel = Kernel()

# Tilføj prøveplugin til Kernel-objektet
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definér Azure OpenAI AI Connector
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definér forespørgselsindstillingerne for at konfigurere modellen med automatisk funktionskald
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Foretag forespørgslen til modellen for den givne samtalehistorik og forespørgselsindstillinger
    # Kernel indeholder prøven, som modellen vil anmode om at udføre
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
    # Eksempel på AI-modelsvar: `Din flyvning til New York den 1. januar 2025 er blevet booket succesfuldt. God rejse! ✈️🗽`

    # Tilføj modellens svar til vores samtalehistoriens kontekst
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

Hvad du kan se fra dette eksempel er, hvordan du kan udnytte en forudbygget parser til at udtrække nøgleoplysninger fra brugerinput, såsom afgangssted, destination og dato for en flybestillingsforespørgsel. Denne modulære tilgang giver dig mulighed for at fokusere på det overordnede logiske niveau.

### Udnyt samarbejdsværktøjer

Rammer som CrewAI, Microsoft AutoGen og Semantic Kernel faciliterer oprettelsen af flere agenter, der kan arbejde sammen.

**Hvordan teams kan bruge disse**: Teams kan designe agenter med specifikke roller og opgaver, hvilket gør det muligt for dem at teste og forfine samarbejdsarbejdsgange og forbedre den samlede systemeffektivitet.

**Hvordan det fungerer i praksis**: Du kan skabe et team af agenter, hvor hver agent har en specialiseret funktion, såsom dataudtræk, analyse eller beslutningstagning. Disse agenter kan kommunikere og dele information for at nå et fælles mål, såsom at besvare en brugerforespørgsel eller fuldføre en opgave.

**Eksempelkode (AutoGen)**:

```python
# opretter agenter, derefter opret en round robin-plan, hvor de kan arbejde sammen, i dette tilfælde i rækkefølge

# Dataindhentningsagent
# Dataanalyseagent
# Beslutningstagingsagent

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

# samtalen afsluttes, når brugeren siger "GODKEND"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Brug asyncio.run(...) når det kører i et script.
await Console(stream)
```

Det, du ser i den tidligere kode, er, hvordan du kan oprette en opgave, der involverer flere agenter, som arbejder sammen om at analysere data. Hver agent udfører en specifik funktion, og opgaven eksekveres ved at koordinere agenternes handlinger for at opnå det ønskede resultat. Ved at skabe dedikerede agenter med specialiserede roller kan du forbedre opgavetilgængelighed og ydeevne.

### Læring i realtid

Avancerede rammer tilbyder kapabiliteter for kontekstforståelse og tilpasning i realtid.

**Hvordan teams kan bruge disse**: Teams kan implementere feedbackloops, hvor agenter lærer af interaktioner og justerer deres adfærd dynamisk, hvilket fører til løbende forbedring og forfining af kapabiliteter.

**Hvordan det fungerer i praksis**: Agenter kan analysere brugerfeedback, miljødata og opgaveudfald for at opdatere deres videnbase, justere beslutningsalgoritmer og forbedre præstationen over tid. Denne iterative læringsproces muliggør, at agenter kan tilpasse sig ændrede forhold og brugerpræferencer, hvilket forbedrer systemets samlede effektivitet.

## Hvad er forskellene mellem rammerne AutoGen, Semantic Kernel og Azure AI Agent Service?

Der er mange måder at sammenligne disse rammer på, men lad os se på nogle nøgleforskelle med hensyn til deres design, kapabiliteter og målrettede brugstilfælde:

## AutoGen

AutoGen er en open-source-ramme udviklet af Microsoft Researchs AI Frontiers Lab. Den fokuserer på begivenhedsdrevne, distribuerede *agentiske* applikationer og muliggør flere LLMs og SLMs, værktøjer og avancerede multi-agent designmønstre.

AutoGen er bygget omkring kernekonceptet agenter, som er autonome enheder, der kan opfatte deres miljø, træffe beslutninger og udføre handlinger for at opnå specifikke mål. Agenter kommunikerer gennem asynkrone beskeder, hvilket gør det muligt for dem at arbejde uafhængigt og parallelt og dermed forbedre systemets skalerbarhed og reaktionsevne.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenter er baseret på aktørmodellen</a>. Ifølge Wikipedia er en aktør _den grundlæggende byggesten i samtidig beregning. Som svar på en besked, den modtager, kan en aktør: træffe lokale beslutninger, skabe flere aktører, sende flere beskeder og bestemme, hvordan den skal svare på den næste besked, den modtager_.

**Use Cases**: Automatisering af kodegenerering, dataanalysetasks og opbygning af tilpassede agenter til planlægnings- og forskningsfunktioner.

Her er nogle vigtige kernebegreber i AutoGen:

- **Agenter**. En agent er en softwareentitet, der:
  - **Kommunikerer via beskeder**, disse beskeder kan være synkrone eller asynkrone.
  - **Opretholder sin egen tilstand**, som kan ændres af indkommende beskeder.
  - **Udfører handlinger** som reaktion på modtagne beskeder eller ændringer i sin tilstand. Disse handlinger kan ændre agentens tilstand og skabe eksterne effekter, såsom opdatering af beskedlogs, afsendelse af nye beskeder, udførelse af kode eller kald til API'er.
    
  Her har du et kort kodeudsnit, hvor du opretter din egen agent med chatfunktioner:

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
    
    I den foregående kode er `MyAgent` blevet oprettet og arver fra `RoutedAgent`. Den har en beskedhåndterer, der udskriver indholdet af beskeden og derefter sender et svar ved hjælp af `AssistantAgent`-delegeringen. Bemærk især, hvordan vi tildeler til `self._delegate` en instans af `AssistantAgent`, som er en forudbygget agent, der kan håndtere chat-completions.


    Lad os informere AutoGen om denne agenttype og starte programmet næste:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Start behandlingen af beskeder i baggrunden.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    I den foregående kode registreres agenterne hos runtime, og der sendes derefter en besked til agenten, hvilket resulterer i følgende output:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Fleragenter**. AutoGen understøtter oprettelsen af flere agenter, der kan arbejde sammen for at opnå komplekse opgaver. Agenter kan kommunikere, dele information og koordinere deres handlinger for at løse problemer mere effektivt. For at skabe et fleragentsystem kan du definere forskellige typer agenter med specialiserede funktioner og roller, såsom dataudtræk, analyse, beslutningstagning og brugerinteraktion. Lad os se, hvordan en sådan oprettelse ser ud, så vi får en fornemmelse af det:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Eksempel på deklaration af en Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Brug af emnetype som agenttype.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="DIN_API_NØGLE",
        ),
        ),
    )

    # resterende deklarationer forkortet for overskuelighed

    # Gruppechat
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="DIN_API_NØGLE",
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

    I den foregående kode har vi en `GroupChatManager`, der er registreret hos runtime. Denne manager er ansvarlig for at koordinere interaktionerne mellem forskellige typer agenter, såsom forfattere, illustratører, redaktører og brugere.

- **Agent Runtime**. Rammen tilbyder et runtime-miljø, der muliggør kommunikation mellem agenter, håndterer deres identiteter og livscyklusser samt håndhæver sikkerheds- og privatlivsgrænser. Det betyder, at du kan køre dine agenter i et sikkert og kontrolleret miljø og sikre, at de kan interagere sikkert og effektivt. Der er to runtimes af interesse:
  - **Enkeltstående runtime**. Dette er et godt valg for enkeltproces-applikationer, hvor alle agenter implementeres i samme programmeringssprog og kører i samme proces. Her er en illustration af, hvordan det fungerer:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Enkeltstående runtime</a>   
Applikationsstak

    *agenter kommunikerer via beskeder gennem runtime, og runtime håndterer agenternes livscyklus*

  - **Distribueret runtime**, er velegnet til multiprocess-applikationer, hvor agenter kan være implementeret i forskellige programmeringssprog og køre på forskellige maskiner. Her er en illustration af, hvordan det fungerer:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distribueret runtime</a>

## Semantic Kernel + Agent-ramme

Semantic Kernel er et virksomhedsklart AI-orkestrerings-SDK. Det består af AI- og hukommelsesforbindelser samt en Agent-ramme.

Lad os først gennemgå nogle kernekomponenter:

- **AI Connectors**: Dette er en grænseflade til eksterne AI-tjenester og datakilder til brug i både Python og C#.

  ```python
  # Semantisk Kernel Python
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

    Her har du et simpelt eksempel på, hvordan du kan oprette et kernel og tilføje en chat completion-tjeneste. Semantic Kernel opretter en forbindelse til en ekstern AI-tjeneste, i dette tilfælde Azure OpenAI Chat Completion.

- **Plugins**: Disse indkapsler funktioner, som en applikation kan bruge. Der findes både færdiglavede plugins og brugerdefinerede, som du kan oprette. Et beslægtet koncept er "prompt-funktioner". I stedet for at give naturlige sprogledetråde for funktionskald, broadcastes visse funktioner til modellen. Baseret på den aktuelle chatkontekst kan modellen vælge at kalde en af disse funktioner for at fuldføre en anmodning eller forespørgsel. Her er et eksempel:

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

    Her har du først en skabelonprompt `skPrompt`, der giver plads til, at brugeren kan indtaste tekst, `$userInput`. Derefter opretter du kernelfunktionen `SummarizeText` og importerer den derefter i kernel med plugin-navnet `SemanticFunctions`. Bemærk navnet på funktionen, som hjælper Semantic Kernel med at forstå, hvad funktionen gør, og hvornår den skal kaldes.

- **Native function**: Der er også native funktioner, som rammen kan kalde direkte for at udføre opgaven. Her er et eksempel på en sådan funktion, der henter indholdet fra en fil:

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

- **Memory**: Abstraherer og forenkler kontekststyring for AI-apps. Idéen med hukommelse er, at dette er noget, LLM'en bør kende til. Du kan gemme disse oplysninger i et vektorlager, som ender med at være en in-memory database eller en vektordatabase eller lignende. Her er et eksempel på et meget forenklet scenarie, hvor *fakta* tilføjes til hukommelsen:

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

    Disse fakta gemmes derefter i hukommelsessamlingen `SummarizedAzureDocs`. Dette er et meget forenklet eksempel, men du kan se, hvordan du kan gemme information i hukommelsen, så LLM'en kan bruge den.

Så det var det grundlæggende i Semantic Kernel-rammeværket — hvad med Agent Framework?

## Azure AI Agent-tjeneste

Azure AI Agent Service er en nyere tilføjelse, introduceret ved Microsoft Ignite 2024. Den gør det muligt at udvikle og udrulle AI-agenter med mere fleksible modeller, såsom direkte kald til open-source LLM'er som Llama 3, Mistral og Cohere.

Azure AI Agent Service tilbyder stærkere virksomhedssikkerhedsmekanismer og metoder til datalagring, hvilket gør den velegnet til virksomhedsapplikationer. 

Den fungerer direkte med multi-agent orkestreringsrammeværk som AutoGen og Semantic Kernel.

Denne tjeneste er i øjeblikket i Public Preview og understøtter Python og C# til at bygge agenter.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definer et eksempel plugin til eksemplet
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
        # Opret agentdefinition
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Opret AzureAI-agenten ved hjælp af den definerede klient og agentdefinition
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Opret en tråd til at holde samtalen
        # Hvis ingen tråd er angivet, vil en ny tråd
        # blive oprettet og returneret med det indledende svar
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
                # Kald agenten for den angivne tråd
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

### Kernebegreber

Azure AI Agent Service har følgende kernebegreber:

- **Agent**. Azure AI Agent Service integrerer med Microsoft Foundry. Inden for AI Foundry fungerer en AI Agent som en "smart" mikrotjeneste, der kan bruges til at besvare spørgsmål (RAG), udføre handlinger eller fuldstændigt automatisere workflows. Det opnås ved at kombinere kraften fra generative AI-modeller med værktøjer, der giver den adgang til og mulighed for at interagere med real-world datakilder. Her er et eksempel på en agent:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    I dette eksempel oprettes en agent med modellen `gpt-4o-mini`, navnet `my-agent` og instruktionerne `You are helpful agent`. Agenten er udstyret med værktøjer og ressourcer til at udføre kodefortolkningsopgaver.

- **Thread and messages**. Tråden er et andet vigtigt koncept. Den repræsenterer en samtale eller interaktion mellem en agent og en bruger. Tråde kan bruges til at spore fremskridt i en samtale, gemme kontekstinformation og styre tilstanden i interaktionen. Her er et eksempel på en tråd:

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

    I den tidligere kode oprettes en tråd. Derefter sendes en besked til tråden. Ved at kalde `create_and_process_run` bliver agenten bedt om at udføre arbejde på tråden. Endelig hentes og logges beskederne for at se agentens svar. Beskederne angiver fremskridtene i samtalen mellem brugeren og agenten. Det er også vigtigt at forstå, at beskederne kan være af forskellige typer som tekst, billede eller fil — det vil sige, at agentens arbejde for eksempel har resulteret i et billede eller et tekstsvar. Som udvikler kan du derefter bruge disse oplysninger til yderligere at bearbejde svaret eller præsentere det for brugeren.

- **Integrates with other AI frameworks**. Azure AI Agent-tjenesten kan interagere med andre rammeværk som AutoGen og Semantic Kernel, hvilket betyder, at du kan bygge dele af din app i et af disse rammeværk og for eksempel bruge Agent-tjenesten som orkestrator, eller du kan bygge det hele i Agent-tjenesten.

**Use Cases**: Azure AI Agent Service er designet til virksomhedsapplikationer, der kræver sikker, skalerbar og fleksibel udrulning af AI-agenter.

## Hvad er forskellen mellem disse rammeværk?
 
Det lyder som om, der er meget overlap mellem disse rammeværk, men der er nogle nøgleforskelle med hensyn til deres design, kapaciteter og målrettede anvendelsestilfælde:
 
- **AutoGen**: Er et eksperimenteringsrammeværk med fokus på banebrydende forskning i multi-agent systemer. Det er det bedste sted at eksperimentere og prototype sofistikerede multi-agent systemer.
- **Semantic Kernel**: Er et produktionsklart agentbibliotek til at bygge agentiske virksomhedsapplikationer. Fokuserer på begivenhedsdrevne, distribuerede agentapplikationer, hvilket muliggør brug af flere LLM'er og SLM'er, værktøjer samt single-/multi-agent designmønstre.
- **Azure AI Agent Service**: Er en platform- og udrulningstjeneste i Azure Foundry for agenter. Den tilbyder opbygning og forbindelser til services understøttet af Azure Foundry såsom Azure OpenAI, Azure AI Search, Bing Search og kodeeksekvering.
 
Er du stadig i tvivl om, hvilken du skal vælge?

### Anvendelsestilfælde
 
Lad os se, om vi kan hjælpe dig ved at gennemgå nogle almindelige anvendelsestilfælde:
 
> Q: I'm experimenting, learning and building proof-of-concept agent applications, and I want to be able to build and experiment quickly
>
> A: AutoGen would be a good choice for this scenario, as it focuses on event-driven, distributed agentic applications and supports advanced multi-agent design patterns.
>
> Q: What makes AutoGen a better choice than Semantic Kernel and Azure AI Agent Service for this use case?
>
> A: AutoGen is specifically designed for event-driven, distributed agentic applications, making it well-suited for automating code generation and data analysis tasks. It provides the necessary tools and capabilities to build complex multi-agent systems efficiently.
>
> Q: Sounds like Azure AI Agent Service could work here too, it has tools for code generation and more?
>
> A: Yes, Azure AI Agent Service is a platform service for agents and add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. It makes it easy to build your agents in the Foundry Portal and deploy them at scale.
>
> Q: I'm still confused just give me one option
>
> A: A great choice is to build your application in Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. This approach allows you to easily persist your agents while leveraging the power to build multi-agent systems in Semantic Kernel. Additionally, Semantic Kernel has a connector in AutoGen, making it easy to use both frameworks together.
 
Lad os opsummere de vigtigste forskelle i en tabel:

| Framework | Fokus | Kernekoncepter | Anvendelsestilfælde |
| --- | --- | --- | --- |
| AutoGen | Begivenhedsdrevne, distribuerede agentapplikationer | Agents, Personas, Functions, Data | Kodegenerering, dataanalyseopgaver |
| Semantic Kernel | Forståelse og generering af menneskelignende tekstindhold | Agents, Modular Components, Collaboration | Naturlig sprogforståelse, indholdsgenerering |
| Azure AI Agent Service | Fleksible modeller, virksomhedssikkerhed, kodegenerering, kald til værktøjer | Modularity, Collaboration, Process Orchestration | Sikker, skalerbar og fleksibel udrulning af AI-agenter |

Hvad er det ideelle anvendelsestilfælde for hver af disse rammeværk?

## Kan jeg integrere mine eksisterende Azure-økosystemværktøjer direkte, eller har jeg brug for separate løsninger?

Svaret er ja — du kan integrere dine eksisterende Azure-økosystemværktøjer direkte med især Azure AI Agent Service, fordi den er bygget til at fungere problemfrit med andre Azure-tjenester. Du kan for eksempel integrere Bing, Azure AI Search og Azure Functions. Der er også dyb integration med Microsoft Foundry.

For AutoGen og Semantic Kernel kan du også integrere med Azure-tjenester, men det kan kræve, at du kalder Azure-tjenesterne fra din kode. En anden måde at integrere på er at bruge Azure SDK'erne til at interagere med Azure-tjenester fra dine agenter. Derudover, som nævnt, kan du bruge Azure AI Agent Service som orkestrator for dine agenter bygget i AutoGen eller Semantic Kernel, hvilket giver nem adgang til Azure-økosystemet.

## Eksempelkoder

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Har du flere spørgsmål om AI-agentrammer?

Deltag i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for at møde andre lærende, deltage i kontortimer og få svar på dine spørgsmål om AI-agenter.

## Referencer

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent-tjeneste</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel og AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent-ramme</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent-ramme</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent-tjeneste</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Brug af Azure AI Agent Service med AutoGen / Semantic Kernel til at bygge en multi-agent-løsning</a>

## Forrige lektion

[Introduktion til AI-agenter og agentbrugstilfælde](../01-intro-to-ai-agents/README.md)

## Næste lektion

[Forståelse af agentiske designmønstre](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfraskrivelse:
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, bedes du være opmærksom på, at automatiske oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets oprindelige sprog bør betragtes som den autoritative kilde. For kritisk information anbefales en professionel menneskelig oversættelse. Vi er ikke ansvarlige for misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->