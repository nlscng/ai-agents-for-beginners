[![Utforske AI Agent-rammeverk](../../../translated_images/no/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Klikk på bildet over for å se video av denne leksjonen)_

# Utforsk AI Agent-rammeverk

AI-agentrammeverk er programvareplattformer designet for å forenkle opprettelsen, distribusjonen og administrasjonen av AI-agenter. Disse rammeverkene gir utviklere forhåndsbygde komponenter, abstraksjoner og verktøy som effektiviserer utviklingen av komplekse AI-systemer.

Disse rammeverkene hjelper utviklere med å fokusere på de unike aspektene av deres applikasjoner ved å tilby standardiserte tilnærminger til vanlige utfordringer i utviklingen av AI-agenter. De forbedrer skalerbarhet, tilgjengelighet og effektivitet i bygging av AI-systemer.

## Introduksjon 

Denne leksjonen vil dekke:

- Hva er AI-agentrammeverk og hva gjør de mulig for utviklere å oppnå?
- Hvordan kan team bruke disse til å raskt prototype, iterere og forbedre agentens evner?
- Hva er forskjellene mellom rammeverkene og verktøyene laget av Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, og <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Kan jeg integrere mine eksisterende Azure-økosystemverktøy direkte, eller trenger jeg frittstående løsninger?
- Hva er Azure AI Agents-tjenesten og hvordan hjelper denne meg?

## Læringsmål

Målene for denne leksjonen er å hjelpe deg å forstå:

- Rollen til AI-agentrammeverk i AI-utvikling.
- Hvordan utnytte AI-agentrammeverk til å bygge intelligente agenter.
- Nøkkelfunksjoner muliggjort av AI-agentrammeverk.
- Forskjellene mellom AutoGen, Semantic Kernel og Azure AI Agent Service.

## Hva er AI-agentrammeverk og hva gjør de mulig for utviklere å gjøre?

Tradisjonelle AI-rammeverk kan hjelpe deg med å integrere AI i appene dine og gjøre disse appene bedre på følgende måter:

- **Personalisering**: AI kan analysere brukeradferd og preferanser for å gi personlige anbefalinger, innhold og opplevelser.
Eksempel: Strømmetjenester som Netflix bruker AI for å foreslå filmer og serier basert på seerhistorikk, noe som øker brukerengasjement og tilfredshet.
- **Automatisering og effektivitet**: AI kan automatisere repetitive oppgaver, effektivisere arbeidsflyt og forbedre operasjonell effektivitet.
Eksempel: Kundeserviceapper bruker AI-drevne chatboter for å håndtere vanlige henvendelser, noe som reduserer svartider og frigjør menneskelige agenter til mer komplekse saker.
- **Bedret brukeropplevelse**: AI kan forbedre totalopplevelsen ved å tilby intelligente funksjoner som stemmegjenkjenning, naturlig språkbehandling og prediktiv tekst.
Eksempel: Virtuelle assistenter som Siri og Google Assistant bruker AI for å forstå og svare på stemmekommandoer, noe som gjør det enklere for brukere å interagere med enhetene sine.

### Det høres jo flott ut, men hvorfor trenger vi AI-agentrammeverket?

AI-agentrammeverk representerer noe mer enn bare AI-rammeverk. De er designet for å muliggjøre opprettelsen av intelligente agenter som kan interagere med brukere, andre agenter og miljøet for å oppnå spesifikke mål. Disse agentene kan opptre autonomt, ta beslutninger og tilpasse seg endrende forhold. La oss se på noen viktige egenskaper muliggjort av AI-agentrammeverk:

- **Agent-samarbeid og koordinering**: Gjør det mulig å opprette flere AI-agenter som kan jobbe sammen, kommunisere og koordinere for å løse komplekse oppgaver.
- **Automatisering og oppgavehåndtering**: Tilbyr mekanismer for å automatisere flertrinns arbeidsflyter, oppgavefordeling og dynamisk oppgavehåndtering mellom agenter.
- **Kontextforståelse og tilpasning**: Utrust agentene med evne til å forstå kontekst, tilpasse seg skiftende miljøer og ta beslutninger basert på sanntidsinformasjon.

Kort oppsummert lar agenter deg gjøre mer, løfte automatiseringen til neste nivå, og skape mer intelligente systemer som kan tilpasse seg og lære av miljøet sitt.

## Hvordan raskt prototype, iterere og forbedre agentens evner?

Dette er et raskt skiftende landskap, men det finnes noen ting som er vanlige på tvers av de fleste AI-agentrammeverk og som kan hjelpe deg å raskt prototype og iterere, nemlig modulære komponenter, samarbeidende verktøy og sanntidslæring. La oss gå nærmere inn på disse:

- **Bruk modulære komponenter**: AI-SDK-er tilbyr forhåndsbygde komponenter som AI- og minnekontakter, funksjonskall ved bruk av naturlig språk eller kodeplugins, promptmaler og mer.
- **Dra nytte av samarbeidende verktøy**: Design agenter med spesifikke roller og oppgaver som gjør det mulig å teste og forbedre samarbeidsarbeidsflyter.
- **Lær i sanntid**: Implementer tilbakemeldingssløyfer hvor agenter lærer av interaksjoner og justerer atferden sin dynamisk.

### Bruk modulære komponenter

SDK-er som Microsoft Semantic Kernel og LangChain tilbyr forhåndsbygde komponenter som AI-kontakter, promptmaler og minnehåndtering.

**Hvordan team kan bruke disse**: Team kan raskt sette sammen disse komponentene for å lage en funksjonell prototype uten å starte fra bunnen av, noe som muliggjør rask eksperimentering og iterasjon.

**Hvordan det fungerer i praksis**: Du kan bruke en forhåndsbygget parser for å trekke ut informasjon fra brukerinput, en minnemodul for å lagre og hente data, og en promptgenerator for å interagere med brukere, alt uten å måtte bygge disse komponentene fra grunnen av.

**Eksempelkode**. La oss se på eksempler på hvordan du kan bruke en forhåndsbygd AI-kontakt med Semantic Kernel Python og .Net som bruker automatisk funksjonskall for å la modellen svare på brukerinput:

``` python
# Semantic Kernel Python-eksempel

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definer et ChatHistory-objekt for å holde samtalens kontekst
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definer et eksempelplugin som inneholder funksjonen for å bestille reise
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Opprett Kernel
kernel = Kernel()

# Legg til eksempelpluginet i Kernel-objektet
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definer Azure OpenAI AI-tilkoblingen
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definer forespørselsinnstillingene for å konfigurere modellen med automatisk funksjonsanrop
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Send forespørselen til modellen med gitt chathistorikk og forespørselsinnstillinger
    # Kernel inneholder eksemplet som modellen vil be om å kjøre
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
    # Eksempel på svar fra AI-modellen: `Din flyvning til New York den 1. januar 2025 har blitt bestilt. God tur! ✈️🗽`

    # Legg modellens svar til vår chathistorikk
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

Det du kan se fra dette eksempelet er hvordan du kan utnytte en forhåndsbygd parser til å trekke ut nøkkelinfo fra brukerinput, som avreisested, destinasjon og dato for en flybestillingsforespørsel. Denne modulære tilnærmingen lar deg fokusere på logikken på et overordnet nivå.

### Dra nytte av samarbeidende verktøy

Rammeverk som CrewAI, Microsoft AutoGen og Semantic Kernel legger til rette for opprettelse av flere agenter som kan jobbe sammen.

**Hvordan team kan bruke disse**: Team kan designe agenter med spesifikke roller og oppgaver, slik at de kan teste og forbedre samarbeidende arbeidsflyter og øke den totale systemeffektiviteten.

**Hvordan det fungerer i praksis**: Du kan opprette et team av agenter der hver agent har en spesialisert funksjon, som datainnhenting, analyse eller beslutningstaking. Disse agentene kan kommunisere og dele informasjon for å oppnå et felles mål, som å svare på en brukerspørsmål eller fullføre en oppgave.

**Eksempelkode (AutoGen)**:

```python
# opprett agenter, og opprett deretter en round-robin-plan hvor de kan samarbeide, i dette tilfellet i rekkefølge

# Agent for datainnhenting
# Agent for dataanalyse
# Agent for beslutningstaking

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

# samtalen avsluttes når brukeren sier "GODKJENN"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Bruk asyncio.run(...) når du kjører i et skript.
await Console(stream)
```

Det du ser i forrige kode er hvordan du kan opprette en oppgave som involverer flere agenter som jobber sammen for å analysere data. Hver agent utfører en bestemt funksjon, og oppgaven utføres ved å koordinere agentene for å oppnå ønsket resultat. Ved å lage dedikerte agenter med spesialiserte roller kan du forbedre oppgaveeffektivitet og ytelse.

### Lær i sanntid

Avanserte rammeverk tilbyr funksjoner for sanntids kontekstforståelse og tilpasning.

**Hvordan team kan bruke disse**: Team kan implementere tilbakemeldingssløyfer hvor agenter lærer av interaksjoner og dynamisk justerer sin atferd, noe som fører til kontinuerlig forbedring og finjustering av evnene.

**Hvordan det fungerer i praksis**: Agenter kan analysere brukerfeedback, miljødata og resultatene av oppgaver for å oppdatere sin kunnskapsbase, justere beslutningsalgoritmer og forbedre ytelsen over tid. Denne iterative læringsprosessen gjør det mulig for agentene å tilpasse seg skiftende forhold og brukerpreferanser, og øke den totale systemeffektiviteten.

## Hva er forskjellene mellom rammeverkene AutoGen, Semantic Kernel og Azure AI Agent Service?

Det finnes mange måter å sammenligne disse rammeverkene på, men la oss se på noen hovedforskjeller når det gjelder design, funksjonalitet og målrettede bruksområder:

## AutoGen

AutoGen er et open-source rammeverk utviklet av Microsoft Researchs AI Frontiers Lab. Det fokuserer på hendelsesstyrte, distribuerte *agentiske* applikasjoner, som muliggjør flere LLM-er og SLM-er, verktøy og avanserte designmønstre for flere agenter.

AutoGen er bygd rundt kjernebegrepet agenter, som er autonome enheter som kan oppfatte miljøet sitt, ta beslutninger og utføre handlinger for å oppnå spesifikke mål. Agenter kommuniserer via asynkrone meldinger, noe som gjør at de kan arbeide uavhengig og parallelt, forbedrer systemets skalerbarhet og responsivitet.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenter er basert på aktørmodellen</a>. Ifølge Wikipedia er en aktør _den grunnleggende byggesteinen i parallellberegning. Som svar på en melding den mottar kan en aktør: ta lokale beslutninger, opprette flere aktører, sende flere meldinger, og bestemme hvordan den skal svare på neste mottatte melding_.

**Bruksområder**: Automatisering av kodegenerering, dataanalysetjenester, og bygging av egne agenter for planlegging og forskningsfunksjoner.

Her er noen viktige kjernebegreper i AutoGen:

- **Agenter**. En agent er en programvarenhet som:
  - **Kommuniserer via meldinger**, disse meldingene kan være synkrone eller asynkrone.
  - **Opprettholder sin egen tilstand**, som kan endres av innkommende meldinger.
  - **Utfører handlinger** som svar på mottatte meldinger eller endringer i sin tilstand. Disse handlingene kan endre agentens tilstand og produsere eksterne effekter, som å oppdatere meldingslogger, sende nye meldinger, kjøre kode, eller gjøre API-kall.
    
  Her har du et kort kodesnutt der du lager din egen agent med chattefunksjoner:

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
    
    I forrige kode har `MyAgent` blitt opprettet og arver fra `RoutedAgent`. Den har en meldingsbehandler som skriver ut innholdet i meldingen og deretter sender et svar ved hjelp av delegaten `AssistantAgent`. Merk spesielt hvordan vi tildeler `self._delegate` en instans av `AssistantAgent` som er en forhåndsbygd agent som kan håndtere chat-kompletteringer.


    La oss informere AutoGen om denne agenttypen og starte programmet deretter:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Start behandling av meldinger i bakgrunnen.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    I forrige kode er agentene registrert i runtime og deretter sendes en melding til agenten, noe som resulterer i følgende utdata:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Flere agenter**. AutoGen støtter opprettelsen av flere agenter som kan samarbeide for å løse komplekse oppgaver. Agenter kan kommunisere, dele informasjon og koordinere sine handlinger for å løse problemer mer effektivt. For å lage et fleragent-system kan du definere forskjellige typer agenter med spesialiserte funksjoner og roller, som datainnhenting, analyse, beslutningstaking og brukerinteraksjon. La oss se hvordan en slik opprettelse ser ut for å få en følelse av det:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Eksempel på å erklære en agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Bruker topic-typen som agenttype.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # Resterende deklarasjoner forkortet av plasshensyn

    # Gruppechat
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

    I forrige kode har vi en `GroupChatManager` som er registrert i runtime. Denne manageren er ansvarlig for å koordinere samspillet mellom ulike typer agenter, som skribenter, illustratører, redaktører og brukere.

- **Agent Runtime**. Rammeverket tilbyr et runtime-miljø som muliggjør kommunikasjon mellom agenter, håndterer deres identiteter og livssykluser, og håndhever sikkerhets- og personverngrenser. Dette betyr at du kan kjøre agentene dine i et sikkert og kontrollert miljø, og sørge for at de kan interagere trygt og effektivt. Det finnes to runtime-miljøer av interesse:
  - **Frittstående runtime**. Dette er et godt valg for enkeltprosesser der alle agenter er implementert i samme programmeringsspråk og kjører i samme prosess. Her er en illustrasjon av hvordan det fungerer:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Frittstående runtime</a>   
Applikasjonsstack

    *agenter kommuniserer via meldinger gjennom runtime, og runtime håndterer agentenes livssyklus*

  - **Distribuert agent-runtime**, egnet for flerprosessapplikasjoner der agenter kan være implementert i forskjellige programmeringsspråk og kjøre på forskjellige maskiner. Her er en illustrasjon av hvordan det fungerer:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distribuert runtime</a>

## Semantic Kernel + Agent Framework

Semantic Kernel er et bedriftsklart AI-orchestrerings-SDK. Det består av AI- og minnekontakter, sammen med et agentrammeverk.

La oss først dekke noen kjernekomponenter:

- **AI-kontakter**: Dette er et grensesnitt mot eksterne AI-tjenester og datakilder for bruk i både Python og C#.

  ```python
  # Semantisk kjerne Python
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

    Her har du et enkelt eksempel på hvordan du kan opprette en kernel og legge til en chat completion-tjeneste. Semantic Kernel oppretter en forbindelse til en ekstern AI-tjeneste, i dette tilfelle Azure OpenAI Chat Completion.

- **Plugins**: Disse kapsler inn funksjoner som en applikasjon kan bruke. Det finnes både ferdige plugins og egendefinerte du kan lage selv. Et beslektet konsept er "prompt-funksjoner." I stedet for å gi naturlige språkoppfordringer for funksjonskall, kringkaster du visse funksjoner til modellen. Basert på den gjeldende chat-konteksten kan modellen velge å kalle en av disse funksjonene for å fullføre en forespørsel eller et spørsmål. Her er et eksempel:

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

    Her har du først en malprompt `skPrompt` som gir plass for brukerens input, `$userInput`. Deretter oppretter du kjernens funksjon `SummarizeText` og importerer den inn i kjernen med plugin-navnet `SemanticFunctions`. Merk navnet på funksjonen som hjelper Semantic Kernel med å forstå hva funksjonen gjør og når den skal kalles.

- **Native funksjon**: Det finnes også native funksjoner som rammeverket kan kalle direkte for å utføre oppgaven. Her er et eksempel på en slik funksjon som henter innhold fra en fil:

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

- **Minne**: Abstraherer og forenkler kontekststyring for AI-apper. Idéen med minne er at dette er noe LLM bør kjenne til. Du kan lagre denne informasjonen i en vektorbutikk som i praksis er en in-memory database, en vektordatabase eller lignende. Her er et eksempel på et veldig forenklet scenario der *fakta* legges til i minnet:

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

Disse faktaene blir deretter lagret i minnesamlingen `SummarizedAzureDocs`. Dette er et veldig forenklet eksempel, men du kan se hvordan du kan lagre informasjon i hukommelsen for at LLM skal bruke det.

Så det er det grunnleggende om Semantic Kernel-rammeverket, hva med Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service er en nyere tillegg, introdusert på Microsoft Ignite 2024. Det gjør det mulig å utvikle og distribuere AI-agenter med mer fleksible modeller, som å direkte kalle open source LLM-er som Llama 3, Mistral og Cohere.

Azure AI Agent Service gir sterkere sikkerhetsmekanismer for bedriftsbruk og metoder for datalagring, noe som gjør det egnet for bedriftsapplikasjoner.

Det fungerer rett ut av boksen med fleragentorchestrasjonsrammeverk som AutoGen og Semantic Kernel.

Denne tjenesten er for øyeblikket i offentlig forhåndsvisning og støtter Python og C# for bygging av agenter.

Ved å bruke Semantic Kernel Python kan vi lage en Azure AI Agent med et brukerdefinert plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definer en eksempel-plugin for eksempelet
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
        # Opprett agentdefinisjon
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Opprett AzureAI-agenten ved å bruke den definerte klienten og agentdefinisjonen
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Opprett en tråd for å holde samtalen
        # Hvis ingen tråd er oppgitt, vil en ny tråd bli
        # opprettet og returnert med den innledende responsen
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
                # Kall agenten for den angitte tråden
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

### Kjernen begreper

Azure AI Agent Service har følgende kjernebegreper:

- **Agent**. Azure AI Agent Service integreres med Microsoft Foundry. Innenfor AI Foundry fungerer en AI Agent som en "smart" mikrotjeneste som kan brukes til å svare på spørsmål (RAG), utføre handlinger eller fullstendig automatisere arbeidsflyter. Den oppnår dette ved å kombinere kraften til generative AI-modeller med verktøy som gjør det mulig å få tilgang til og samhandle med virkelige datakilder. Her er et eksempel på en agent:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    I dette eksemplet opprettes en agent med modellen `gpt-4o-mini`, et navn `my-agent` og instruksjoner `You are helpful agent`. Agenten er utstyrt med verktøy og ressurser for å utføre kodeinterpretasjonsoppgaver.

- **Tråd og meldinger**. Tråden er et annet viktig begrep. Den representerer en samtale eller interaksjon mellom en agent og en bruker. Tråder kan brukes til å spore fremdriften i en samtale, lagre kontekstinformasjon og administrere tilstanden til interaksjonen. Her er et eksempel på en tråd:

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

    I den forrige koden opprettes en tråd. Deretter sendes en melding til tråden. Ved å kalle `create_and_process_run` blir agenten bedt om å utføre arbeid på tråden. Til slutt hentes meldingene og logges for å se agentens respons. Meldingene indikerer fremdriften i samtalen mellom brukeren og agenten. Det er også viktig å forstå at meldingene kan være av forskjellige typer som tekst, bilde eller fil, det vil si at agentens arbeid har resultert i for eksempel et bilde eller en tekstrespons. Som utvikler kan du deretter bruke denne informasjonen til å viderebehandle responsen eller presentere den til brukeren.

- **Integreres med andre AI-rammeverk**. Azure AI Agent Service kan samhandle med andre rammeverk som AutoGen og Semantic Kernel, noe som betyr at du kan bygge deler av appen din i ett av disse rammeverkene og for eksempel bruke Agent-tjenesten som en orkestrator, eller du kan bygge alt i Agent-tjenesten.

**Bruksområder**: Azure AI Agent Service er designet for bedriftsapplikasjoner som krever sikker, skalerbar og fleksibel distribusjon av AI-agenter.

## Hva er forskjellen mellom disse rammeverkene?

Det høres ut som det er mye overlapp mellom disse rammeverkene, men det finnes noen viktige forskjeller når det gjelder deres design, funksjoner og målrettede bruksområder:

- **AutoGen**: Er et eksperimenteringsrammeverk som fokuserer på forskningsledende multi-agent-systemer. Det er det beste stedet å eksperimentere og prototype avanserte multi-agent-systemer.
- **Semantic Kernel**: Er et produksjonsklart agentbibliotek for bygging av agentapplikasjoner for bedrifter. Fokuserer på hendelsesdrevne, distribuerte agentapplikasjoner, som muliggjør flere LLM-er og SLM-er, verktøy og enkelt-/fleragent-designmønstre.
- **Azure AI Agent Service**: Er en plattform- og distribusjonstjeneste i Azure Foundry for agenter. Den tilbyr tilkoblingsbygging til tjenester støttet av Azure Foundry som Azure OpenAI, Azure AI Search, Bing Search og kodekjøring.

Er du fortsatt usikker på hvilken du skal velge?

### Bruksområder

La oss se om vi kan hjelpe deg ved å gå gjennom noen vanlige brukstilfeller:

> Q: Jeg eksperimenterer, lærer og bygger bevis-på-konsept agentapplikasjoner, og jeg ønsker å kunne bygge og eksperimentere raskt
>

> A: AutoGen vil være et godt valg for dette scenariet, siden det fokuserer på hendelsesdrevne, distribuerte agentapplikasjoner og støtter avanserte fleragent-designmønstre.

> Q: Hva gjør AutoGen til et bedre valg enn Semantic Kernel og Azure AI Agent Service for dette bruksområdet?
>
> A: AutoGen er spesifikt designet for hendelsesdrevne, distribuerte agentapplikasjoner, noe som gjør det godt egnet til å automatisere kodegenerering og dataanalyseoppgaver. Det gir nødvendige verktøy og funksjonalitet for å bygge komplekse multi-agent-systemer effektivt.

> Q: Det høres ut som Azure AI Agent Service også kan passe her, det har verktøy for kodegenerering og mer?

>
> A: Ja, Azure AI Agent Service er en plattformtjeneste for agenter og har innebygde muligheter for flere modeller, Azure AI Search, Bing Search og Azure Functions. Det gjør det enkelt å bygge agentene dine i Foundry-portalen og distribuere dem i stor skala.

> Q: Jeg er fortsatt forvirret, gi meg bare ett valg
>
> A: Et godt valg er å bygge applikasjonen din først i Semantic Kernel, og deretter bruke Azure AI Agent Service til å distribuere agenten din. Denne tilnærmingen lar deg enkelt vedvare agentene dine samtidig som du utnytter kraften til å bygge fler-agent-systemer i Semantic Kernel. I tillegg har Semantic Kernel en kobling i AutoGen, noe som gjør det enkelt å bruke begge rammeverkene sammen.

La oss oppsummere de viktigste forskjellene i en tabell:

| Framework | Fokus | Kjernen Begreper | Bruksområder |
| --- | --- | --- | --- |
| AutoGen | Hendelsesdrevne, distribuerte agentapplikasjoner | Agenter, Personas, Funksjoner, Data | Kodegenerering, dataanalyseoppgaver |
| Semantic Kernel | Forståelse og generering av menneskelignende tekstinnhold | Agenter, Modulære komponenter, Samarbeid | Naturlig språksforståelse, innholdsgenerering |
| Azure AI Agent Service | Fleksible modeller, bedriftsikkerhet, kodegenerering, verktøy-kall | Modularitet, samarbeid, prosessorchestrering | Sikker, skalerbar og fleksibel distribusjon av AI-agenter |

Hva er det ideelle bruksområdet for hvert av disse rammeverkene?

## Kan jeg integrere mine eksisterende Azure-økosystemverktøy direkte, eller trenger jeg frittstående løsninger?

Svaret er ja, du kan integrere dine eksisterende Azure-økosystemverktøy direkte med Azure AI Agent Service spesielt, dette fordi den er bygget for å fungere sømløst med andre Azure-tjenester. Du kan for eksempel integrere Bing, Azure AI Search og Azure Functions. Det er også dyp integrasjon med Microsoft Foundry.

For AutoGen og Semantic Kernel kan du også integrere med Azure-tjenester, men det kan kreve at du kaller Azure-tjenestene fra koden din. En annen måte å integrere på er å bruke Azure SDK-ene for å samhandle med Azure-tjenester fra agentene dine. I tillegg, som nevnt, kan du bruke Azure AI Agent Service som en orkestrator for agentene dine bygget i AutoGen eller Semantic Kernel, noe som gir enkel tilgang til Azure-økosystemet.

## Eksempel Kode

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Har du flere spørsmål om AI Agent Frameworks?

Bli med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for å møte andre lærende, delta på kontortimer og få svar på spørsmål om AI-agenter.

## Referanser

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel and AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## Forrige leksjon

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## Neste leksjon

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vennligst vær oppmerksom på at automatiske oversettelser kan inneholde feil eller unøyaktigheter. Originaldokumentet på dets opprinnelige språk bør betraktes som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->