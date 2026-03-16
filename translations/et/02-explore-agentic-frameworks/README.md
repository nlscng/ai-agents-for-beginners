[![Tehisintellekti agendi raamistikud ülevaatamisel](../../../translated_images/et/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Klõpsake ülaloleval pildil, et vaadata selle õppetunni videot)_

# Tutvu tehisintellekti agendi raamistikuga

Tehisintellekti agendi raamistikud on tarkvaraplatvormid, mis on loodud lihtsustama tehisintellekti agentide loomist, juurutamist ja haldamist. Need raamistikud pakuvad arendajatele eelnevalt ehitatud komponente, abstraktsioone ja tööriistu, mis sujuvdavad keerukate tehisintellekti süsteemide arendamist.

Need raamistikud aitavad arendajatel keskenduda oma rakenduste unikaalsetele aspektidele, pakkudes standardiseeritud lähenemisi tehisintellekti agentide arendamisega seotud tavalistele väljakutsetele. Need suurendavad skaleeritavust, ligipääsetavust ja efektiivsust tehisintellekti süsteemide loomisel.

## Sissejuhatus

Selles õppetunnis käsitletakse:

- Mis on tehisintellekti agendi raamistikud ja mida need arendajatele võimaldavad saavutada?
- Kuidas saavad meeskonnad neid kasutada, et kiiresti prototüüpida, iteratsioonid teha ja parandada oma agendi võimeid?
- Millised on erinevused Microsofti <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kerneli</a> ja <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service’i</a> loodud raamistikute ja tööriistade vahel?
- Kas saan oma olemasolevaid Azure’i ökosüsteemi tööriistu otse integreerida või on vaja iseseisvaid lahendusi?
- Mis on Azure AI Agent Service ja kuidas see mind aitab?

## Õpieesmärgid

Selle õppetunni eesmärgiks on aidata sul mõista:

- Tehisintellekti agendi raamistikute rolli tehisintellekti arenduses.
- Kuidas kasutada tehisintellekti agendi raamistikke intelligentsete agentide loomiseks.
- Peamisi funktsioone, mida tehisintellekti agendi raamistikud võimaldavad.
- Erinevusi AutoGeni, Semantic Kernel’i ja Azure AI Agent Service’i vahel.

## Mis on tehisintellekti agendi raamistikud ja mida need arendajatele võimaldavad?

Traditsioonilised tehisintellekti raamistikud võivad aidata sul AI integreerida oma rakendustesse ja neid paremini muuta järgmistel viisidel:

- **Isikupärastamine**: AI saab analüüsida kasutaja käitumist ja eelistusi, et pakkuda isikupärastatud soovitusi, sisu ja kogemusi.
Näide: Voogedastusplatvormid nagu Netflix kasutavad tehisintellekti, et soovitada filme ja saateid vaatamisajaloo põhjal, suurendades kasutajate kaasatust ja rahulolu.
- **Automatiseerimine ja efektiivsus**: AI suudab automatiseerida korduvaid ülesandeid, sujuvamaks muuta töövooge ja parandada tegevuslikku efektiivsust.
Näide: Klienditeeninduse rakendused kasutavad AI-põhiseid vestlusroboteid tavapäraste päringute haldamiseks, vähendades reageerimisaegu ja vabastades inimagendid keerukamate probleemide lahendamiseks.
- **Parem kasutajakogemus**: AI võib parandada üldist kasutajakogemust, pakkudes intelligentsed funktsioonid nagu hääletuvastus, loomuliku keele töötlemine ja ennustav tekstisisestus.
Näide: Virtuaalsed assistendid nagu Siri ja Google Assistant kasutavad AI-t, et mõista ja täita häälkäsklusi, muutes seadmetega suhtlemise lihtsamaks.

### See kõik kõlab hästi, miks siis on vaja tehisintellekti agendi raamistikku?

Tehisintellekti agendi raamistikud tähistavad midagi enamat kui lihtsalt AI raamistikud. Need on loodud võimaldama intelligentsete agentide loomist, kes saavad suhelda kasutajate, teiste agentide ja keskkonnaga, et saavutada kindlaid eesmärke. Need agendid võivad näidata autonoomset käitumist, teha otsuseid ja kohaneda muutuvate tingimustega. Vaatame mõningaid peamisi funktsioone, mida tehisintellekti agendi raamistikud võimaldavad:

- **Agentide koostöö ja koordineerimine**: Võimaldavad luua mitu AI agenti, kes saavad üheskoos töötada, suhelda ja koordineerida keerukate ülesannete lahendamist.
- **Ülesannete automatiseerimine ja haldamine**: Pakuvad mehhanisme mitmeastmeliste töövoogude automatiseerimiseks, ülesannete delegeerimiseks ja dünaamiliseks ülesandehalduseks agentide vahel.
- **Kontekstipõhine mõistmine ja kohanemine**: Varustavad agente võimalusega mõista konteksti, kohaneda muutuvate keskkondadega ja teha otsuseid reaalajas saadud teabe põhjal.

Kokkuvõttes võimaldavad agendid sulle teha rohkem, viia automatiseerimine järgmisele tasemele ja luua targemaid süsteeme, mis saavad oma keskkonnast õppida ja kohaneda.

## Kuidas kiiresti prototüüpida, teha iteratsioone ja parandada agendi võimeid?

See valdkond areneb kiiresti, kuid enamikel tehisintellekti agendi raamistikudel on mõned ühised omadused, mis aitavad sul kiiresti prototüüpida ja iteratsioone teha — nimelt moodulikomponendid, koostööriistad ja reaalajaliselt õppimine. Sukeldume nendesse:

- **Kasuta moodulikomponente**: AI SDK-d pakuvad eelnevalt valmistatud komponente nagu AI ja mäluliidesed, funktsioonide kutsumine loomuliku keele või koodipluginatega, vihjetempliidid jms.
- **Kasu koostööriistadest**: Disaini agente konkreetsete rollide ja ülesannetega, võimaldades neil testida ja täiustada koostöövooge.
- **Õpi reaalajas**: Rakenda tagasisideahelad, kus agendid õpivad suhtlemisest ja kohandavad oma käitumist dünaamiliselt.

### Kasuta moodulikomponente

SDK-d nagu Microsoft Semantic Kernel ja LangChain pakuvad eelnevalt ehitatud komponente, näiteks AI-liidesi, vihjetempliide ja mäluhaldust.

**Kuidas meeskonnad saavad neid kasutada**: Meeskonnad saavad neid komponente kiiresti kokku panna funktsionaalse prototüübi loomiseks ilma algusest alustamata, võimaldades kiireid katsed ja iteratsioonid.

**Kuidas see praktikas töötab**: Sa võid kasutada eelset parserit, et ekstraheerida teavet kasutaja sisendist, mälumoodulit andmete salvestamiseks ja pärimiseks ning vihjetegijat kasutajatega suhtlemiseks, kõike seda ilma, et peaksid komponente nullist üles ehitama.

**Näide koodist**. Vaatame näiteid, kuidas kasutada eelnevalt ehitatud AI-liidest Semantic Kernel Pythonis ja .Netis, mis kasutab automaatset funktsioonikõnet, et mudelile kasutaja sisendile vastata:

``` python
# Semantic Kerneli Pythoni näide

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Määratle ChatHistory objekt, mis hoiab vestluse konteksti
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Määratle näidisplugin, mis sisaldab reisi broneerimise funktsiooni
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Loo Kernel
kernel = Kernel()

# Lisa näidisplugin Kerneli objektile
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Määratle Azure OpenAI AI-ühendus
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Määratle päringu seaded mudeli seadistamiseks automaatse funktsioonikutsumisega
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Esita mudelile päring antud vestluse ajaloo ja päringu seadistustega
    # Kernel sisaldab näidist, mille mudel palub käivitada
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
    # Näide AI mudeli vastusest: `Teie lend New Yorki 1. jaanuaril 2025 on edukalt broneeritud. Head reisi! ✈️🗽`

    # Lisa mudeli vastus meie vestluse ajalukku
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
  
Selle näite põhjal näed, kuidas kasutada eelnevalt ehitatud parserit võtmetähtsusega info, nagu lennukutse päritolu, sihtkoht ja kuupäev, kasutaja sisendist välja võtmise jaoks. See moodulik lähenemine võimaldab keskenduda kõrgemale äriloogikale.

### Kasuta koostööriistu

Raamistikud nagu CrewAI, Microsoft AutoGen ja Semantic Kernel hõlbustavad mitme agendi loomist, kes saavad üheskoos töötada.

**Kuidas meeskonnad neid saavad kasutada**: Meeskonnad saavad disainida agendid kindlate rollide ja ülesannetega, võimaldades neil testida ja täiustada koostöövooge ning parandada süsteemi üldist efektiivsust.

**Kuidas see praktikas töötab**: Sa võid luua agendimeeskonna, kus iga agent täidab spetsiifilist funktsiooni, näiteks andmete hankimist, analüüsi või otsustamist. Need agendid saavad suhelda ja jagada infot, et saavutada ühine eesmärk, näiteks vastata kasutaja päringule või lõpetada ülesanne.

**Näide koodist (AutoGen)**:

```python
# agentide loomine, seejärel luuakse round-robin-ajakava, kus nad saavad koos töötada, antud juhul järjekorras

# Andmete hankimise agent
# Andmeanalüüsi agent
# Otsuste tegemise agent

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

# vestlus lõpeb, kui kasutaja ütleb "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Kasutage asyncio.run(...), kui käivitate skripti.
await Console(stream)
```
  
Eelnevas koodis näed, kuidas luuakse ülesanne, mis nõuab mitme agendi koostööd andmete analüüsimiseks. Iga agent täidab spetsialiseeritud funktsiooni ja ülesanne viiakse läbi agentide koordineerimise abil soovitud tulemuse saavutamiseks. Spetsiaalsete rollidega agentide loomine aitab suurendada ülesande efektiivsust ja jõudlust.

### Õpi reaalajas

Arenenud raamistikud pakuvad võimalusi reaalajas konteksti mõistmiseks ja kohanemiseks.

**Kuidas meeskonnad neid saavad kasutada**: Meeskonnad saavad rakendada tagasisideahelaid, kus agendid õpivad vahejuhtumitest ja kohandavad oma käitumist dünaamiliselt, võimaldades pidevat täiustamist ja võimete lihvimist.

**Kuidas see praktikas töötab**: Agendid saavad analüüsida kasutajate tagasisidet, keskkonnadata ja ülesannete tulemusi, et värskendada oma teadmistebaasi, kohandada otsustusalgoritme ja parandada aja jooksul jõudlust. See iteratiivne õppimisprotsess võimaldab agentidel kohaneda muutuvate tingimustega ja kasutajate eelistustega, tõstes kogu süsteemi tõhusust.

## Millised on erinevused AutoGen'i, Semantic Kernel’i ja Azure AI Agent Service’i raamistikute vahel?

Nende raamistikute võrdlemiseks on palju võimalusi, kuid vaatame mõningaid olulisi erinevusi nende disaini, võimete ja sihtkasutuse järgi:

## AutoGen

AutoGen on Microsoft Researchi AI Frontiers labori loodud avatud lähtekoodiga raamistik. See keskendub sündmuspõhistele, hajutatud *agentsete* rakendustele, võimaldades mitu LLM-i ja SLM-i, tööriistu ning arenenud mitme-agendi disainimustreid.

AutoGen põhineb agentide põhimõttel, mis on autonoomsed üksused, kes saavad oma keskkonda tajuda, teha otsuseid ja tegutseda kindlate eesmärkide saavutamiseks. Agendid suhtlevad asünkroonsete sõnumite kaudu, võimaldades töötada iseseisvalt ja paralleelselt, parandades süsteemi skaleeritavust ja reageerimisvõimet.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agendid põhinevad näitlejamudelil (actor model)</a>. Vikipeedia järgi on näitleja _põhikomponent paralleelse arvutuse juures. Saadud sõnumile reageerides võib näitleja teha kohapealseid otsuseid, luua uusi näitlejaid, saata sõnumeid ja määrata, kuidas järgmist sõnumit vastu võtta_.

**Kasutusjuhtumid**: Koodi genereerimise automatiseerimine, andmeanalüüsi ülesanded ja kohandatud agentide loomine planeerimiseks ja uurimistööks.

Siin on mõned AutoGeni põhimõisted:

- **Agendid**. Agent on tarkvaraline üksus, kes:
  - **Suhtleb sõnumite kaudu**, mis võivad olla sünkroonsed või asünkroonsed.
  - **Hoidab oma olekut**, mida saab muuta saabuvate sõnumite põhjal.
  - **Teeb tegevusi** vastusena sõnumitele või oleku muutustele. Need tegevused võivad muuta agendi olekut ja avaldada välist mõju, näiteks uuendada sõnumilogisid, saata uusi sõnumeid, käivitada koodi või teha API-kõnesid.
    
  Järgnevalt on lühike koodinäide, kuidas luua oma agent vestlusvõimega:

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
  
    Eelnevas koodis on loodud `MyAgent`, mis pärineb `RoutedAgent` klassist. Sellel on sõnumihaldur, mis prindib sõnumi sisu ja saadab seejärel vastuse kasutades `AssistantAgent` delegaati. Pane tähele, kuidas `self._delegate` määratakse `AssistantAgent` instantsiks, mis on eelnevalt ehitatud agent, kes suudab vestlusi hallata.


    Anname AutoGenile teada sellest agentide tüübist ja alustame programmi:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Alusta sõnumite töötlemist taustal.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```
  
    Eelnevas koodis on agendid registreeritud runtime'is ja seejärel saadetakse agendile sõnum, mille tulemusena kuvatakse järgmine väljund:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```
  
- **Mitme agentsüsteem**. AutoGen toetab mitme agendi loomist, kes saavad koos keerukaid ülesandeid lahendada. Agendid saavad suhelda, jagada infot ja koordineerida tegevusi tõhusama probleemilahenduse nimel. Mitme-agendi süsteemi loomiseks saab defineerida erinevat tüüpi agente spetsiifiliste funktsioonide ja rollidega, nagu andmete hankimine, analüüs, otsustamine ja kasutajatega suhtlemine. Vaata, kuidas selline loomine välja näeb:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Näide agendi deklareerimisest
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Kasutab agendi tüübina 'topic'
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # ülejäänud deklaratsioonid on lühendatud lühiduse huvides

    # Rühmavestlus
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
  
    Eelnevas koodis on `GroupChatManager`, mis on registreeritud runtime'is. See juht vastutab erinevate tüüpi agentide, nagu kirjanike, illustraatorite, toimetajate ja kasutajate, omavahelise suhtluse koordineerimise eest.

- **Agendi jooksutuskeskkond**. Raamistik pakub jooksutuskeskkonda, mis võimaldab agenditel suhelda, haldab nende identiteeti ja elutsüklit ning tagab turvalisust ja privaatsust. On kaks huvipakkuvat jooksutuskeskkonda:
  - **Iseseisev jooksutuskeskkond**. Sobib üheprotsessiliste rakenduste jaoks, kus kõik agendid on kirjutatud samas programmeerimiskeeles ja töötavad samas protsessis. Siin on illustratsioon sellest, kuidas see toimib:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Iseseisev jooksutuskeskkond</a>  
Rakenduse virn

    *agendid suhtlevad sõnumite kaudu jooksutuskeskkonnas ja jooksutuskeskkond haldab agentide elutsüklit*

  - **Hajutatud agendi jooksutuskeskkond**, sobib mitme protsessiga rakendustele, kus agendid võivad olla implementeeritud erinevates keeltes ja töötada erinevatel masinatel. Siin on illustratsioon selle toimimisest:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Hajutatud jooksutuskeskkond</a>

## Semantic Kernel + Agendi raamistik

Semantic Kernel on ettevõtte jaoks valmis AI orkestreerimise SDK. See koosneb AI- ja mäluliidestest koos agendi raamistikuga.

Alustame mõningate põhikomponentide kirjeldusest:

- **AI-liidesed**: See on liides, mis võimaldab suhelda väliste AI-teenuste ja andmeallikatega nii Pythonis kui ka C#-s.

  ```python
  # Semantiline tuum Python
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
  
    siin on lihtne näide, kuidas luua kernel ja lisada vestluse lõpuleviimise teenus. Semantic Kernel loob ühenduse välise AI-teenusega, antud juhul Azure OpenAI vestluse lõpuleviimisega.

- **Pluginad**: Need kapseldavad funktsioone, mida rakendus saab kasutada. On olemas nii valmis pluginaid kui ka kohandatud omasid, mida saab ise luua. Seotud mõiste on "vihjefunktsioonid". Selle asemel, et pakkuda funktsiooni kutsumiseks loomuliku keele juhiseid, edastad mudelile teatud funktsioonid. Praeguse vestluse konteksti põhjal võib mudel valida ühe neist funktsioonidest päringu või taotluse täitmiseks. Näide:

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
  
    Siin on esmalt vihjepõhine mall `skPrompt`, mis jätab ruumi kasutaja sisendile `$userInput`. Seejärel loome kerneli funktsiooni `SummarizeText` ja impordime selle kerneli pluginana nimega `SemanticFunctions`. Pane tähele funktsiooni nime, see aitab Semantic Kernelil mõista, mida funktsioon teeb ja millal seda tuleks kutsuda.

- **Natiivfunktsioon**: Raamistikul on ka võimalus kutsuda natiivseid funktsioone, mis täidavad ülesandeid otse. Näiteks failisisu lugemine:

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
  
- **Mälu**: Abstraktiseerib ja lihtsustab konteksti haldust AI-rakendustes. Mälu mõte on, et LLM-il peaks olema teave konteksti kohta. Seda saab salvestada vektoripoodi, mis võib olla mälus töötav andmebaas või vektorandmebaas vms. Näiteks lihtsustatud stsenaarium, kus *faktid* lisatakse mällu:

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
  

Need faktid salvestatakse seejärel mälukogumikku `SummarizedAzureDocs`. See on väga lihtsustatud näide, kuid saate näha, kuidas teavet saab mällu salvestada, et LLM saaks seda kasutada.

Niisiis, need on Semantic Kernel raamistikud põhialused, aga mis saab Agent Frameworkist?

## Azure AI Agent Service

Azure AI Agent Service on hiljutisem lisand, mis tutvustati Microsoft Ignite 2024 ajal. See võimaldab arendada ja juurutada AI agente paindlikumate mudelitega, näiteks kutsudes otseselt avatud lähtekoodiga LLM-e nagu Llama 3, Mistral ja Cohere.

Azure AI Agent Service pakub tugevamaid ettevõtte turvamehhanisme ja andmete salvestamise meetodeid, muutes selle sobivaks ettevõtte rakendustele.

See töötab otsekohe koos mitme agendi orkestreerimisraamistikuga nagu AutoGen ja Semantic Kernel.

See teenus on praegu avalikus eelvaates ja toetab agendide loomist Pythonis ja C#-s.

Semantic Kernel Pythoniga saame luua Azure AI Agendi kasutaja määratud pluginaga:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Määratle näidisplugin näidise jaoks
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
        # Loo agendi määratlus
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Loo AzureAI agent, kasutades määratletud klienti ja agendi määratlust
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Loo lõim vestluse hoidmiseks
        # Kui lõime ei ole antud, uus lõim
        # luuakse ja tagastatakse esialgse vastusega
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
                # Käivita agent määratud lõime jaoks
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

### Põhikontseptsioonid

Azure AI Agent Service sisaldab järgmisi põhikontseptsioone:

- **Agent**. Azure AI Agent Service integreerub Microsoft Foundry-ga. AI Foundry sees tegutseb AI Agent kui "intelligentne" mikroteenus, mida saab kasutada küsimustele vastamiseks (RAG), toimingute tegemiseks või täiesti töövoogude automatiseerimiseks. See saavutatakse generatiivse tehisintellekti mudelite võimsuse kombineerimisega tööriistadega, mis võimaldavad pääseda ligi ja suhelda reaalmaailma andmeallikatega. Siin on näide agendist:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Selles näites luuakse agent mudeliga `gpt-4o-mini`, nimega `my-agent` ja juhistega `You are helpful agent`. Agent on varustatud tööriistade ja ressurssidega, et täita koodi tõlgendamise ülesandeid.

- **Lõim ja sõnumid**. Lõim on teine oluline kontseptsioon. See tähistab vestlust või suhtlust agendi ja kasutaja vahel. Lõime saab kasutada vestluse edenemise jälgimiseks, kontekstiinformatsiooni talletamiseks ja suhtluse oleku haldamiseks. Siin on näide lõimest:

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

    Eelnevas koodis luuakse lõim. Seejärel saadetakse lõimele sõnum. Kutsudes `create_and_process_run`, palutakse agendil lõime osas tööd teha. Lõpuks sõnumid tõmmatakse ja logitakse, et näha agendi vastust. Sõnumid näitavad vestluse edenemist kasutaja ja agendi vahel. Samuti on oluline mõista, et sõnumid võivad olla erinevat tüüpi, näiteks tekst, pilt või fail, see tähendab, et agendi töö on toonud näiteks välja pildi või tekstilise vastuse. Arendajana saate seda teavet kasutada vastuse edasiseks töötlemiseks või kasutajale esitamiseks.

- **Integreerub teiste AI raamistikudega**. Azure AI Agent Service saab suhelda teiste raamistikudega nagu AutoGen ja Semantic Kernel, mis tähendab, et saate oma rakenduse osa ehitada mõnes neist raamistikest ja näiteks kasutada Agent teenust orkestreerijana või luua kogu rakenduse Agent teenuses.

**Kasutus juhtumid**: Azure AI Agent Service on mõeldud ettevõtte rakendustele, mis vajavad turvalist, skaleeritavat ja paindlikku AI agendi juurutust.

## Mis vahe on nende raamistikude vahel?

Tundub, et nende raamistikude vahel on palju kattuvust, kuid on mõned olulised erinevused nende disaini, võimekuse ja sihtotstarbeliste kasutusjuhtude osas:

- **AutoGen**: On katse raamistik, mis keskendub uusimatele uuringutele mitme agendi süsteemide alal. See on parim koht keerukate mitme agendi süsteemide katsetamiseks ja prototüüpimiseks.
- **Semantic Kernel**: On tootmisvalmis agendi teek ettevõtte agendipõhiste rakenduste loomiseks. Keskendub sündmuspõhistele, hajutatud agentipõhistele rakendustele, võimaldades kasutada mitut LLM-i ja SLM-i, tööriistu ning üksi- ja mitme agendi disainimustreid.
- **Azure AI Agent Service**: On platvorm ja juurutusteenus Azure Foundry’s agentide jaoks. Pakub ühenduvust teenustega nagu Azure OpenAI, Azure AI Search, Bing Search ja koodi täitmine.

Kas ikka ei tea, kummat valida?

### Kasutamise juhud

Vaatame, kas saame aidata mõne levinud kasutusjuhtumi läbivaatamisega:

> K: Ma katsetan, õpin ja ehitan tõestuslikke agentide rakendusi ning soovin kiiresti ehitada ja katsetada
>

> V: AutoGen sobib selleks stsenaariumiks hästi, kuna see keskendub sündmuspõhistele, hajutatud agentipõhistele rakendustele ja toetab täiustatud mitme agendi disainimustreid.

> K: Miks on AutoGen parem valik kui Semantic Kernel ja Azure AI Agent Service selles kasutusjuhtumis?
>
> V: AutoGen on spetsiaalselt loodud sündmuspõhisteks, hajutatud agentipõhisteks rakendusteks, mis teeb selle ideaalseks koodi genereerimise ja andmete analüüsi automatiseerimiseks. See pakub vajalikke tööriistu ja võimeid keerukate mitme agendi süsteemide tõhusaks ehitamiseks.

> K: Tundub, et Azure AI Agent Service võiks siin ka toimida, tal on tööriistad koodi genereerimiseks ja rohkemgi?
>
> V: Jah, Azure AI Agent Service on platvormiteenus agentide jaoks ning lisab sisseehitatud võimekusi mitme mudeli, Azure AI Search, Bing Search ja Azure Functions jaoks. See muudab teie agentide lihtsaks loomise Foundry portaalis ning vähendab juurutustööd.

> K: Ma olen ikka veel segaduses, anna mulle lihtsalt üks valik.
>
> V: Hea valik on alustada oma rakenduse ehitamist Semantic Kernelis ja seejärel kasutada Azure AI Agent Service’i oma agendi juurutamiseks. See lähenemine võimaldab teil oma agente hõlpsasti säilitada, kasutades samal ajal Semantic Kernel võimsust mitme agendi süsteemide ehitamiseks. Lisaks on Semantic Kernelil AutoGenis ka ühendus, muutes mõlema raamistikuga koos töötamise lihtsaks.

Võtame võtmerõhud tabelisse kokku:

| Raamistik | Fookus | Põhikontseptsioonid | Kasutusjuhud |
| --- | --- | --- | --- |
| AutoGen | Sündmuspõhised, hajutatud agentipõhised rakendused | Agentid, Personaad, Funktsioonid, Andmed | Koodi genereerimine, andmete analüüsitööde automatiseerimine |
| Semantic Kernel | Inimlaadse teksti mõistmine ja genereerimine | Agentid, Moodulkomponendid, Koostöö | Loomuliku keele mõistmine, sisu genereerimine |
| Azure AI Agent Service | Paindlikud mudelid, ettevõtte turvalisus, koodi genereerimine, tööriistade kasutamine | Moodulaarne, Koostöö, Protsessi orkestreerimine | Turvaline, skaleeritav ja paindlik AI agendi juurutus |

Mis on ideaalne kasutusjuht igale neist raamistikest?

## Kas saan oma olemasolevaid Azure ökosüsteemi tööriistu otse integreerida või on vaja iseseisvaid lahendusi?

Vastus on jah, võite integreerida oma olemasolevaid Azure tööriistu otse eriti Azure AI Agent Service'iga, kuna see on loodud sujuvalt töötama koos teiste Azure teenustega. Näiteks saate integreerida Bing'i, Azure AI Search'i ja Azure Functionsiga. Samuti on süvaintegreerimine Microsoft Foundry-ga.

AutoGen ja Semantic Kernel puhul saate samuti Azure teenuseid kasutada, kuid see võib nõuda Azure teenuste kutsumist teie koodist. Teine võimalus integreerimiseks on kasutada Azure SDKsid, et suhelda Azure teenustega oma agentide kaudu. Lisaks võite, nagu mainitud, kasutada Azure AI Agent Service’i orkestreerijana agentidele, mis on loodud AutoGenis või Semantic Kernelis, mis annab lihtsa ligipääsu Azure ökosüsteemile.

## Koodinäited

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Kas Sul on veel küsimusi AI Agent Frameworkide kohta?

Liitu [Microsoft Foundry Discordiga](https://aka.ms/ai-agents/discord), et kohtuda teiste õppuritega, osaleda konsultatsioonides ja saada vastuseid oma AI agendi küsimustele.

## Viited

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel ja AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent teenus</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Kasutamine Azure AI Agent Service koos AutoGen / Semantic Kerneliga mitme agendi lahenduse ehitamiseks</a>

## Eelmine õppetund

[Intro AI Agentidele ja Agentide Kasutusjuhtumid](../01-intro-to-ai-agents/README.md)

## Järgmine õppetund

[Agentide disainimustrite mõistmine](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastutusest loobumine**:  
See dokument on tõlgitud tehisintellekti tõlketeenuse [Co-op Translator](https://github.com/Azure/co-op-translator) abil. Kuigi püüame tagada täpsust, palun arvestage, et automaatsed tõlked võivad sisaldada vigu või ebatäpsusi. Originaaldokument oma emakeeles tuleks pidada autoriteetseks allikaks. Kõrge tähtsusega teabe puhul soovitatakse kasutada professionaalset inimtõlget. Me ei vastuta selle tõlke kasutamisest tulenevate arusaamatuste või valesti mõistmiste eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->