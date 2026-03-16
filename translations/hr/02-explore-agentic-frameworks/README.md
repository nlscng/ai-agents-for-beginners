[![Istraživanje AI Agent Frameworkova](../../../translated_images/hr/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Kliknite gornju sliku za pregled video lekcije)_

# Istražite AI Agent Frameworkove

AI agent frameworkovi su softverske platforme dizajnirane za pojednostavljenje stvaranja, implementacije i upravljanja AI agentima. Ovi frameworkovi pružaju programerima unaprijed izrađene komponente, apstrakcije i alate koji pojednostavljuju razvoj složenih AI sustava.

Ovi frameworkovi pomažu programerima da se fokusiraju na jedinstvene aspekte svojih aplikacija pružajući standardizirane pristupe uobičajenim izazovima u razvoju AI agenata. Oni povećavaju skalabilnost, dostupnost i učinkovitost u izgradnji AI sustava.

## Uvod

Ova lekcija će pokriti:

- Što su AI Agent Frameworkovi i što programerima omogućuju?
- Kako timovi mogu koristiti ove alate za brzo prototipiranje, iteraciju i poboljšanje sposobnosti svojih agenata?
- Koje su razlike između frameworkova i alata koje je stvorio Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> i <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Mogu li integrirati postojeće Azure ekosistemske alate izravno ili trebam samostalna rješenja?
- Što je Azure AI Agents usluga i kako mi pomaže?

## Ciljevi učenja

Ciljevi ove lekcije su da vam pomognu razumjeti:

- Ulogu AI Agent Frameworkova u razvoju AI-ja.
- Kako iskoristiti AI Agent Frameworkove za izgradnju inteligentnih agenata.
- Ključne sposobnosti koje omogućuju AI Agent Frameworkovi.
- Razlike između AutoGen, Semantic Kernel i Azure AI Agent Service.

## Što su AI Agent Frameworkovi i što programerima omogućuju?

Tradicionalni AI Frameworkovi mogu vam pomoći integrirati AI u vaše aplikacije i unaprijediti ih na sljedeće načine:

- **Personalizacija**: AI može analizirati ponašanje i preferencije korisnika kako bi pružio personalizirane preporuke, sadržaj i iskustva.  
Primjer: Streaming servisi poput Netflixa koriste AI za sugeriranje filmova i serija na temelju povijesti gledanja, povećavajući angažman i zadovoljstvo korisnika.
- **Automatizacija i učinkovitost**: AI može automatizirati ponavljajuće zadatke, pojednostaviti tijekove rada i poboljšati operativnu učinkovitost.  
Primjer: Aplikacije za korisničku podršku koriste AI chatbote za obradu uobičajenih upita, smanjujući vrijeme odgovora i oslobađajući ljudske agente za složenije slučajeve.
- **Poboljšano korisničko iskustvo**: AI može poboljšati ukupno korisničko iskustvo pružajući inteligentne značajke poput prepoznavanja glasa, obrade prirodnog jezika i prediktivnog teksta.  
Primjer: Virtualni asistenti poput Siri i Google Assistant koriste AI za razumijevanje i odgovaranje na glasovne naredbe, olakšavajući korisnicima interakciju s uređajima.

### Sve to zvuči odlično, ali zašto nam treba AI Agent Framework?

AI Agent frameworkovi predstavljaju nešto više od običnih AI frameworkova. Dizajnirani su za omogućavanje stvaranja inteligentnih agenata koji mogu komunicirati s korisnicima, drugim agentima i okolinom kako bi postigli specifične ciljeve. Ti agenti mogu pokazivati autonomno ponašanje, donositi odluke i prilagođavati se promjenjivim uvjetima. Pogledajmo neke ključne sposobnosti koje omogućuju AI Agent Frameworkovi:

- **Suradnja i koordinacija agenata**: Omogućuju stvaranje više AI agenata koji mogu raditi zajedno, komunicirati i koordinirati se za rješavanje složenih zadataka.
- **Automatizacija i upravljanje zadacima**: Pružaju mehanizme za automatizaciju višekorakih tijekova rada, delegiranje zadataka i dinamičko upravljanje među agentima.
- **Kontekstualno razumijevanje i prilagodba**: Opremaju agente sposobnošću razumijevanja konteksta, prilagodbe promjenjivim okruženjima i donošenja odluka na temelju informacija u stvarnom vremenu.

Ukratko, agenti vam omogućuju više - podižu automatizaciju na višu razinu, stvaraju inteligentnije sustave koji se mogu prilagoditi i učiti iz svoje okoline.

## Kako brzo prototipirati, iterirati i poboljšavati sposobnosti agenata?

Ovo je brzo promjenjivi krajolik, no postoje neke zajedničke stvari kod većine AI Agent Frameworkova koje vam pomažu brzo prototipirati i iterirati, a to su modularne komponente, alati za suradnju i učenje u stvarnom vremenu. Pogledajmo ih detaljnije:

- **Koristite modularne komponente**: AI SDK-ovi nude unaprijed izrađene komponente poput AI i memorijskih konektora, pozivanja funkcija prirodnim jezikom ili pomoću dodataka za kod, predložaka za promptove i još mnogo toga.
- **Iskoristite alate za suradnju**: Dizajnirajte agente s posebnim ulogama i zadacima, omogućujući im testiranje i dovršavanje suradničkih tijekova rada.
- **Učite u stvarnom vremenu**: Implementirajte povratne petlje u kojima agenti uče iz interakcija i dinamički prilagođavaju svoje ponašanje.

### Koristite modularne komponente

SDK-ovi poput Microsoft Semantic Kernel i LangChain nude unaprijed izrađene komponente poput AI konektora, predložaka za promptove i upravljanja memorijom.

**Kako timovi mogu koristiti ove komponente**: Timovi mogu brzo sastaviti ove komponente za stvaranje funkcionalnog prototipa bez počinjanja od nule, što omogućuje brze eksperimente i iteracije.

**Kako to funkcionira u praksi**: Možete koristiti unaprijed izrađeni parser za izdvajanje informacija iz korisničkog unosa, memorijski modul za pohranu i dohvat podataka te generator prompta za interakciju s korisnicima, sve bez potrebe za izgradnjom tih komponenti od početka.

**Primjer koda**. Pogledajmo primjere kako koristiti unaprijed izrađeni AI konektor s Semantic Kernel Python i .Net koji koristi automatsko pozivanje funkcija kako bi model odgovorio na korisnički unos:

``` python
# Primjer Semantic Kernela u Pythonu

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definirajte objekt ChatHistory za pohranu konteksta razgovora
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definirajte primjer dodatka koji sadrži funkciju za rezervaciju putovanja
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Stvorite Kernel
kernel = Kernel()

# Dodajte primjer dodatka u objekt Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definirajte Azure OpenAI AI konektor
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definirajte postavke zahtjeva za konfiguriranje modela s automatskim pozivanjem funkcija
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Pošaljite zahtjev modelu koristeći zadanu povijest razgovora i postavke zahtjeva
    # Kernel sadrži primjer koji će model zatražiti da pozove
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
    # Primjer odgovora AI modela: `Vaš let za New York 1. siječnja 2025. uspješno je rezerviran. Sretan put! ✈️🗽`

    # Dodajte odgovor modela u kontekst naše povijesti razgovora
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
  
Iz ovog primjera vidite kako iskoristiti unaprijed izrađeni parser za izdvajanje ključnih informacija iz korisničkog unosa, poput mjesta polaska, odredišta i datuma rezervacije leta. Ovaj modularni pristup omogućuje vam fokus na visokorazinsku logiku.

### Iskoristite alate za suradnju

Frameworkovi poput CrewAI, Microsoft AutoGen i Semantic Kernel olakšavaju stvaranje više agenata koji mogu raditi zajedno.

**Kako timovi mogu koristiti ove alate**: Timovi mogu dizajnirati agente s posebnim ulogama i zadacima, što im omogućuje testiranje i dorađivanje suradničkih tijekova rada te poboljšanje ukupne učinkovitosti sustava.

**Kako to funkcionira u praksi**: Možete kreirati tim agenata gdje svaki agent ima specijaliziranu funkciju, poput dohvaćanja podataka, analize ili donošenja odluka. Ti agenti mogu komunicirati i dijeliti informacije kako bi postigli zajednički cilj, poput odgovaranja na korisnički upit ili izvršavanja zadatka.

**Primjer koda (AutoGen)**:  

```python
# kreiranje agenata, zatim stvorite raspored round-robin gdje mogu surađivati, u ovom slučaju redom

# Agent za dohvat podataka
# Agent za analizu podataka
# Agent za donošenje odluka

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

# Razgovor završava kada korisnik kaže "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Koristite asyncio.run(...) pri pokretanju u skripti.
await Console(stream)
```
  
U prethodnom kodu vidite kako možete kreirati zadatak koji uključuje rad više agenata na analizi podataka. Svaki agent obavlja određenu funkciju, a zadatak se izvršava koordiniranjem agenata kako bi se postigao željeni rezultat. Stvaranjem posvećenih agenata sa specijaliziranim ulogama, možete poboljšati učinkovitost i izvedbu zadatka.

### Učite u stvarnom vremenu

Napredni frameworkovi pružaju mogućnosti za razumijevanje konteksta i prilagodbu u stvarnom vremenu.

**Kako timovi mogu koristiti ove mogućnosti**: Timovi mogu implementirati povratne petlje u kojima agenti uče iz interakcija i dinamički prilagođavaju svoje ponašanje, što dovodi do kontinuiranog poboljšanja i dorađivanja sposobnosti.

**Kako to funkcionira u praksi**: Agenti mogu analizirati povratne informacije korisnika, podatke o okolišu i rezultate zadataka kako bi ažurirali svoju bazu znanja, prilagodili algoritme donošenja odluka i s vremenom poboljšali izvedbu. Ovaj iterativni proces učenja omogućuje agentima prilagodbu promjenjivim uvjetima i korisničkim preferencijama, poboljšavajući ukupnu učinkovitost sustava.

## Koje su razlike između frameworkova AutoGen, Semantic Kernel i Azure AI Agent Service?

Postoji mnogo načina za usporedbu ovih frameworkova, no pogledajmo neke ključne razlike u smislu njihovog dizajna, sposobnosti i ciljanih slučajeva korištenja:

## AutoGen

AutoGen je open-source framework razvijen u Microsoft Research AI Frontiers Labu. Fokusira se na događajno vođene, distribuirane *agentske* aplikacije, omogućujući upotrebu više LLM-ova i SLM-ova, alata i naprednih višekratnih obrazaca dizajna agenata.

AutoGen je izgrađen oko osnovnog koncepta agenata, koji su autonomna entiteta koji mogu opažati svoju okolinu, donositi odluke i poduzimati radnje za postizanje specifičnih ciljeva. Agenti komuniciraju asinkronim porukama, što im omogućuje neovisni i paralelni rad, povećavajući skalabilnost i responzivnost sustava.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenti se zasnivaju na „actor modelu“</a>. Prema Wikipediji, actor je _osnovni građevni blok konkurentnog računarstva. Kao odgovor na primljenu poruku, actor može: donositi lokalne odluke, stvarati nove actore, slati dodatne poruke i odlučiti kako odgovoriti na sljedeću primljenu poruku_.

**Primjeri upotrebe**: Automatizacija generiranja koda, zadaci analize podataka i izgradnja prilagođenih agenata za planiranje i istraživačke funkcije.

Evo nekih važnih osnovnih koncepata AutoGen-a:

- **Agenti**. Agent je softverski entitet koji:
  - **Komunicira putem poruka**, koje mogu biti sinkrone ili asinkrone.
  - **Održava vlastito stanje**, koje se može mijenjati putem dolaznih poruka.
  - **Izvršava radnje** kao odgovor na primljene poruke ili promjene u svom stanju. Te radnje mogu mijenjati agentovo stanje i proizvoditi vanjske efekte, poput ažuriranja zapisnika poruka, slanja novih poruka, izvršavanja koda ili poziva API-ja.
    
  Evo kratkog isječka koda u kojem stvarate vlastiti agenta s chat mogućnostima:

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
    
    U prethodnom kodu `MyAgent` je kreiran i nasljeđuje `RoutedAgent`. Ima rukovatelj poruka koji ispisuje sadržaj poruke i zatim šalje odgovor koristeći delegat `AssistantAgent`. Posebno obratite pažnju na to kako dodjeljujemo `self._delegate` instanci `AssistantAgent`, što je unaprijed izrađeni agent koji može rukovati chat dovršetkom.


    Sad ćemo AutoGenu dati do znanja o ovom tipu agenta i pokrenuti program:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Započni obradu poruka u pozadini.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    U prethodnom kodu agenti su registrirani u runtime-u, a zatim je poslana poruka agentu koja rezultira sljedećim ispisom:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Višestruki agenti**. AutoGen podržava stvaranje više agenata koji mogu surađivati na složenim zadacima. Agenti mogu komunicirati, dijeliti informacije i koordinirati svoje radnje radi učinkovitijeg rješavanja problema. Za stvaranje višestrukog sustava agenata možete definirati različite tipove agenata sa specijaliziranim funkcijama i ulogama, poput dohvaćanja podataka, analize, donošenja odluka i interakcije s korisnicima. Pogledajmo kako takva kreacija izgleda:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Primjer deklariranja agenta
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Korištenje tipa topic kao tipa agenta.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # Preostale deklaracije skraćene radi sažetosti

    # Grupni razgovor
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

    U prethodnom kodu imamo `GroupChatManager` koji je registriran u runtime-u. Ovaj menadžer je odgovoran za koordinaciju interakcija između različitih tipova agenata, kao što su pisci, ilustratori, urednici i korisnici.

- **Agent Runtime**. Framework pruža runtime okruženje koje omogućuje komunikaciju između agenata, upravlja njihovim identitetima i životnim ciklusima te provodi sigurnosne i privatnosne granice. To znači da možete pokretati agente u sigurnom i kontroliranom okruženju, osiguravajući da oni mogu sigurno i učinkovito komunicirati. Postoje dva runtime-a od interesa:
  - **Samostalni runtime**. Dobar je izbor za jednoprocese aplikacije gdje su svi agenti implementirani u istom programskom jeziku i rade u istom procesu. Evo ilustracije kako to funkcionira:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Samostalni runtime</a>   
Sloj aplikacije

    *agenti komuniciraju putem poruka kroz runtime, a runtime upravlja životnim ciklusom agenata*

  - **Distribuirani agent runtime**, pogodan za višeporcesne aplikacije gdje agenti mogu biti implementirani u različitim programskim jezicima i raditi na različitim strojevima. Evo ilustracije kako to funkcionira:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distribuirani runtime</a>

## Semantic Kernel + Agent Framework

Semantic Kernel je SDK za orkestraciju AI-ja spreman za poslovnu upotrebu. Sastoji se od AI i memorijskih konektora, zajedno s Agent Frameworkom.

Prvo pokrijmo neke osnovne komponente:

- **AI konektori**: To je sučelje s vanjskim AI uslugama i izvorima podataka za korištenje u Pythonu i C#.

  ```python
  # Semantičko jezgro Python
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

    Ovdje imate jednostavan primjer stvaranja kernela i dodavanja usluge za chat dovršetak. Semantic Kernel uspostavlja vezu s vanjskom AI uslugom, u ovom slučaju Azure OpenAI Chat Completion.

- **Dodaci (Plugins)**: Oni enkapsuliraju funkcije koje aplikacija može koristiti. Postoje gotovi dodaci i prilagođeni koje možete sami stvoriti. Povezan koncept su „prompt funkcije“. Umjesto da nudite prirodno-jezične naznake za pozivanje funkcija, emitirate pojedine funkcije modelu. Na temelju trenutnog konteksta chata, model može odabrati pozivanje neke od tih funkcija za izvršenje zahtjeva ili upita. Evo primjera:

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

    Ovdje prvo imate predložak prompta `skPrompt` koji ostavlja prostor za unos teksta korisnika, `$userInput`. Zatim kreirate kernel funkciju `SummarizeText` i uvozite je u kernel s imenom dodatka `SemanticFunctions`. Obratite pažnju na ime funkcije koje pomaže Semantic Kernelu razumjeti što funkcija radi i kada bi se trebala pozvati.

- **Nativna funkcija**: Postoje i nativne funkcije koje framework može izravno pozvati za izvršavanje zadatka. Evo primjera takve funkcije koja dohvaća sadržaj iz datoteke:

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

- **Memorija**: Apstrahira i pojednostavljuje upravljanje kontekstom za AI aplikacije. Ideja memorije je da je to nešto što LLM treba znati. Možete pohraniti te informacije u vektorsku bazu podataka koja je ustvari baza podataka u memoriji, vektorska baza ili slično. Evo primjera vrlo pojednostavljenog scenarija gdje se *činjenice* dodaju u memoriju:

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

Ti se činjenice zatim pohranjuju u kolekciju memorije `SummarizedAzureDocs`. Ovo je vrlo pojednostavljeni primjer, ali možete vidjeti kako možete pohraniti informacije u memoriju za korištenje LLM-a.

Dakle, to su osnove Semantic Kernel okvira, a što je s Agent Frameworkom?

## Azure AI Agent Service

Azure AI Agent Service je noviji dodatak, predstavljen na Microsoft Ignite 2024. Omogućuje razvoj i implementaciju AI agenata s fleksibilnijim modelima, poput izravnog pozivanja open-source LLM-ova kao što su Llama 3, Mistral i Cohere.

Azure AI Agent Service pruža snažnije mehanizme sigurnosti za poduzeća i metode pohrane podataka, što ga čini prikladnim za poduzećne aplikacije.

Radi odmah s multi-agentnim orkestracijskim okvirima poput AutoGen i Semantic Kernel.

Ova usluga je trenutno u javnoj pretpregledu i podržava Python i C# za izradu agenata.

Koristeći Semantic Kernel Python, možemo stvoriti Azure AI Agent s korisnički definiranim dodatkom:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definirajte uzorak dodatka za primjer
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
        # Stvorite definiciju agenta
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Stvorite AzureAI agenta koristeći definirani klijent i definiciju agenta
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Stvorite nit za vođenje razgovora
        # Ako nit nije predana, nova će biti
        # stvorena i vraćena s početnim odgovorom
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
                # Pozovite agenta za navedenu nit
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

### Osnovni koncepti

Azure AI Agent Service ima sljedeće osnovne koncepte:

- **Agent**. Azure AI Agent Service integrira se s Microsoft Foundryjem. Unutar AI Foundryja, AI agent djeluje kao "pametna" mikroservis koja se može koristiti za odgovaranje na pitanja (RAG), izvršavanje radnji ili potpuno automatizirati radne tokove. To postiže kombiniranjem snage generativnih AI modela s alatima koji mu omogućuju pristup i interakciju s izvorima podataka iz stvarnog svijeta. Evo primjera agenta:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    U ovom primjeru, agent je kreiran s modelom `gpt-4o-mini`, imenom `my-agent` i uputama `You are helpful agent`. Agent je opremljen alatima i resursima za izvršavanje zadataka tumačenja koda.

- **Thread i poruke**. Thread (nit) je još jedan važan koncept. Predstavlja razgovor ili interakciju između agenta i korisnika. Threadovi se mogu koristiti za praćenje tijeka razgovora, pohranu kontekstualnih informacija i upravljanje stanjem interakcije. Evo primjera threada:

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

    U prethodnom kodu, nit je kreirana. Nakon toga, poruka je poslana niti. Pozivanjem `create_and_process_run`, agenta se traži da izvrši rad na niti. Na kraju se poruke dohvaćaju i zapisuju kako bi se vidio odgovor agenta. Poruke ukazuju na tijek razgovora između korisnika i agenta. Također je važno razumjeti da poruke mogu biti različitih vrsta poput teksta, slike ili datoteke, što znači da je rad agenta rezultirao, primjerice, slikom ili tekstualnim odgovorom. Kao programer, zatim možete koristiti ove informacije za daljnju obradu odgovora ili njegovo prikazivanje korisniku.

- **Integracija s drugim AI okvirima**. Azure AI Agent Service može komunicirati s drugim okvirima poput AutoGen i Semantic Kernel, što znači da možete izgraditi dio svoje aplikacije u jednom od tih okvira, a na primjer koristiti Agent Service kao orkestrator ili možete sve izgraditi u Agent Serviceu.

**Slučajevi upotrebe**: Azure AI Agent Service je dizajniran za poduzećne aplikacije koje zahtijevaju sigurnu, skalabilnu i fleksibilnu implementaciju AI agenata.

## Koja je razlika između ovih okvira?

Čini se da postoji mnogo preklapanja među ovim okvirima, ali postoje neke ključne razlike u smislu njihovog dizajna, sposobnosti i ciljanih slučajeva upotrebe:

- **AutoGen**: Eksperimentalni okvir usredotočen na najnovija istraživanja sustava s više agenata. Najbolje je mjesto za eksperimentiranje i prototipiziranje složenih multi-agentnih sustava.
- **Semantic Kernel**: Okvir spreman za proizvodnju za izgradnju poduzećnih agenata. Fokusira se na događajno vođene, distribuirane agentske aplikacije, omogućujući više LLM-ova i SLM-ova, alate i dizajnerske obrasce za jednog ili više agenata.
- **Azure AI Agent Service**: Platforma i usluga za implementaciju agenata u Azure Foundryju. Nudi mogućnosti povezivanja s uslugama podržanim u Azure Foundryju poput Azure OpenAI, Azure AI Search, Bing Search i izvršavanja koda.

Još uvijek niste sigurni koji odabrati?

### Slučajevi upotrebe

Pogledajmo možemo li vam pomoći prolaskom kroz neke uobičajene slučajeve:

> P: Eksperimentiram, učim i izrađujem dokazne agentne aplikacije i želim brzo izrađivati i eksperimentirati.

> O: AutoGen bi bio dobar izbor za ovaj scenarij jer se fokusira na događajno vođene, distribuirane agentske aplikacije i podržava napredne dizajnerske obrasce za više agenata.

> P: Što AutoGen čini boljim izborom od Semantic Kernela i Azure AI Agent Servicea za ovaj slučaj?
>
> O: AutoGen je posebno dizajniran za događajno vođene, distribuirane agentske aplikacije, što ga čini prikladnim za automatizaciju zadataka generiranja koda i analize podataka. Pruža potrebne alate i sposobnosti za učinkovitu izgradnju složenih multi-agentnih sustava.

> P: Zvuci kao da bi Azure AI Agent Service također mogao funkcionirati ovdje, ima alate za generiranje koda i još?
>
> O: Da, Azure AI Agent Service je platforma za agente i dodaje ugrađene mogućnosti za višestruke modele, Azure AI Search, Bing Search i Azure Functions. Omogućuje jednostavnu izgradnju agenata u Foundry portalu i njihovu implementaciju u velikom opsegu.

> P: Još sam zbunjen, dajte mi samo jednu opciju.
>
> O: Odličan izbor je prvo izgraditi aplikaciju u Semantic Kernelu, a zatim koristiti Azure AI Agent Service za implementaciju vašeg agenta. Ovaj pristup omogućuje vam jednostavno trajno pohranjivanje agenata uz iskoristivost moći izgradnje multi-agentnih sustava u Semantic Kernelu. Dodatno, Semantic Kernel ima konektor u AutoGenu, što olakšava korištenje oba okvira zajedno.

Sažmimo ključne razlike u tablici:

| Okvir | Fokus | Osnovni koncepti | Slučajevi upotrebe |
| --- | --- | --- | --- |
| AutoGen | Događajno vođene, distribuirane agentske aplikacije | Agenti, Osobnosti, Funkcije, Podaci | Generiranje koda, zadaci analize podataka |
| Semantic Kernel | Razumijevanje i generiranje teksta nalik ljudskom | Agenti, Modularne komponente, Suradnja | Razumijevanje prirodnog jezika, generiranje sadržaja |
| Azure AI Agent Service | Fleksibilni modeli, sigurnost za poduzeća, generiranje koda, pozivanje alata | Modularnost, Suradnja, Orkestracija procesa | Sigurna, skalabilna i fleksibilna implementacija AI agenata |

Koji je idealan slučaj za svaki od ovih okvira?

## Mogu li izravno integrirati svoje postojeće alate iz Azure ekosustava ili trebam samostalna rješenja?

Odgovor je da, možete izravno integrirati svoje postojeće Azure alate posebno s Azure AI Agent Service jer je izrađen da se besprijekorno povezuje s drugim Azure uslugama. Na primjer, možete integrirati Bing, Azure AI Search i Azure Functions. Postoji i duboka integracija s Microsoft Foundryjem.

Za AutoGen i Semantic Kernel također možete integrirati Azure usluge, ali može biti potrebno da pozivate Azure usluge iz svog koda. Drugi način integracije je korištenje Azure SDK-ova za interakciju s Azure uslugama iz vaših agenata. Dodatno, kao što je navedeno, možete koristiti Azure AI Agent Service kao orkestrator za svoje agente izgrađene u AutoGenu ili Semantic Kernelu, što bi omogućilo jednostavan pristup Azure ekosustavu.

## Primjeri koda

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Imate li više pitanja o AI Agent Frameworku?

Pridružite se [Microsoft Foundry Discordu](https://aka.ms/ai-agents/discord) kako biste upoznali druge učenike, sudjelovali na radnim satima i dobili odgovore na svoja pitanja o AI agentima.

## Reference

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel i AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Korištenje Azure AI Agent Service s AutoGen / Semantic Kernel za izgradnju multi-agentnog rješenja</a>

## Prethodna lekcija

[Uvod u AI agente i slučajeve upotrebe agenata](../01-intro-to-ai-agents/README.md)

## Sljedeća lekcija

[Razumijevanje agentskih dizajnerskih obrazaca](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Odricanje odgovornosti**:
Ovaj je dokument preveden pomoću AI usluge prevođenja [Co-op Translator](https://github.com/Azure/co-op-translator). Iako težimo točnosti, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati službenim izvorom. Za kritične informacije preporučuje se profesionalni ljudski prijevod. Nismo odgovorni za bilo kakva nesporazumevanja ili pogrešna tumačenja koja proizlaze iz korištenja ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->