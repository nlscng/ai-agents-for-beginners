[![Explorarea cadrelor pentru Agenți AI](../../../translated_images/ro/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Faceți clic pe imaginea de mai sus pentru a viziona videoclipul acestei lecții)_

# Explorarea cadrelor pentru Agenți AI

Cadramele pentru agenți AI sunt platforme software create pentru a simplifica crearea, implementarea și gestionarea agenților AI. Aceste cadre oferă dezvoltatorilor componente preconstruite, abstracții și unelte care optimizează dezvoltarea sistemelor AI complexe.

Aceste cadre ajută dezvoltatorii să se concentreze pe aspectele unice ale aplicațiilor lor, oferind abordări standardizate pentru provocările comune în dezvoltarea agenților AI. Ele îmbunătățesc scalabilitatea, accesibilitatea și eficiența în construirea sistemelor AI.

## Introducere

Această lecție va acoperi:

- Ce sunt cadrele pentru Agenți AI și ce permit dezvoltatorilor să realizeze?
- Cum pot echipele să folosească aceste cadre pentru a prototipa rapid, itera și îmbunătăți capacitățile agentului lor?
- Care sunt diferențele între cadrele și uneltele create de Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> și <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Pot integra direct uneltele mele existente din ecosistemul Azure sau am nevoie de soluții standalone?
- Ce este serviciul Azure AI Agents și cum mă ajută acesta?

## Obiectivele de învățare

Obiectivele acestei lecții sunt să te ajute să înțelegi:

- Rolul cadrelor pentru Agenți AI în dezvoltarea AI.
- Cum să valorifici cadrele pentru Agenți AI pentru a construi agenți inteligenți.
- Capacitățile cheie oferite de cadrele pentru Agenți AI.
- Diferențele dintre AutoGen, Semantic Kernel și Azure AI Agent Service.

## Ce sunt cadrele pentru Agenți AI și ce permit acestea dezvoltatorilor să facă?

Cadrele AI tradiționale te pot ajuta să integrezi AI în aplicațiile tale și să le faci mai bune în următoarele moduri:

- **Personalizare**: AI poate analiza comportamentul și preferințele utilizatorului pentru a oferi recomandări, conținut și experiențe personalizate.  
Exemplu: Serviciile de streaming precum Netflix folosesc AI pentru a sugera filme și emisiuni bazate pe istoricul de vizionare, sporind angajamentul și satisfacția utilizatorului.  
- **Automatizare și Eficiență**: AI poate automatiza sarcini repetitive, optimiza fluxurile de lucru și îmbunătăți eficiența operațională.  
Exemplu: Aplicațiile de servicii clienți folosesc chatboturi alimentate de AI pentru a gestiona cereri comune, reducând timpii de răspuns și eliberând agenții umani pentru probleme mai complexe.  
- **Experiență îmbunătățită pentru utilizator**: AI poate îmbunătăți experiența generală a utilizatorului oferind funcții inteligente, cum ar fi recunoaștere vocală, procesare a limbajului natural și text predictiv.  
Exemplu: Asistenții virtuali precum Siri și Google Assistant folosesc AI pentru a înțelege și a răspunde la comenzi vocale, facilitând interacțiunea utilizatorilor cu dispozitivele lor.

### Sună grozav, nu? Atunci de ce avem nevoie de cadrul pentru Agenți AI?

Cadrele pentru agenți AI reprezintă ceva mai mult decât cadrele AI obișnuite. Ele sunt concepute pentru a permite crearea de agenți inteligenți care pot interacționa cu utilizatorii, alți agenți și mediul înconjurător pentru a atinge scopuri specifice. Acești agenți pot manifesta comportament autonom, pot lua decizii și se pot adapta la condiții schimbătoare. Hai să vedem câteva capacități cheie furnizate de cadrele pentru Agenți AI:

- **Colaborare și coordonare între agenți**: Permite crearea mai multor agenți AI care pot lucra împreună, comunica și coordona pentru a rezolva sarcini complexe.  
- **Automatizarea și gestionarea sarcinilor**: Oferă mecanisme pentru automatizarea fluxurilor de lucru în mai mulți pași, delegarea sarcinilor și gestionarea dinamică a acestora între agenți.  
- **Înțelegere contextuală și adaptare**: Echiparea agenților cu abilitatea de a înțelege contextul, de a se adapta la medii în schimbare și de a lua decizii bazate pe informații în timp real.

Pe scurt, agenții îți permit să faci mai mult, să duci automatizarea la un alt nivel, să creezi sisteme mai inteligente care pot învăța și se pot adapta din mediul lor.

## Cum să prototipezi rapid, să iterezi și să îmbunătățești capacitățile agentului?

Acesta este un domeniu în mișcare rapidă, dar există câteva lucruri comune în cele mai multe cadre pentru Agenți AI care te pot ajuta să prototipezi rapid și să iterezi, în special componente modulare, unelte colaborative și învățare în timp real. Hai să explorăm acestea:

- **Folosește componente modulare**: SDK-urile AI oferă componente preconstruite, cum ar fi conectori AI și memorie, apelare de funcții folosind limbaj natural sau pluginuri de cod, șabloane de prompturi și altele.  
- **Valorifică uneltele colaborative**: Proiectează agenți cu roluri și sarcini specifice, permițând testarea și rafinarea fluxurilor de lucru colaborative.  
- **Învățare în timp real**: Implementează bucle de feedback în care agenții învață din interacțiuni și își ajustează comportamentul dinamic.

### Folosește componente modulare

SDK-uri precum Microsoft Semantic Kernel și LangChain oferă componente preconstruite, cum ar fi conectori AI, șabloane pentru prompturi și gestionare a memoriei.

**Cum pot folosi echipele acestea**: Echipele pot asambla rapid aceste componente pentru a crea un prototip funcțional fără a porni de la zero, facilitând experimentarea și iterarea rapidă.

**Cum funcționează în practică**: Poți folosi un parser preconstruit pentru a extrage informații din input-ul utilizatorului, un modul de memorie pentru a stoca și a recupera date și un generator de prompturi pentru a interacționa cu utilizatorii, toate acestea fără a fi nevoie să construiești aceste componente de la zero.

**Exemplu de cod**. Hai să vedem exemple despre cum poți folosi un conector AI preconstruit cu Semantic Kernel Python și .Net care utilizează apeluri automate de funcții pentru a obține răspunsuri ale modelului la input-ul utilizatorului:

``` python
# Exemplu Semantic Kernel în Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definează un obiect ChatHistory pentru a păstra contextul conversației
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definează un plugin de exemplu care conține funcția de rezervare a călătoriei
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Creează Kernel-ul
kernel = Kernel()

# Adaugă pluginul de exemplu la obiectul Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definează conectorul AI Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definează setările cererii pentru a configura modelul cu apelare automată a funcțiilor
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Trimite cererea către model folosind istoricul de chat dat și setările cererii
    # Kernel-ul conține exemplul pe care modelul îl va solicita pentru a-l invoca
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
    # Răspuns exemplu al modelului AI: `Zborul dumneavoastră către New York din 1 ianuarie 2025 a fost rezervat cu succes. Călătorie plăcută! ✈️🗽`

    # Adaugă răspunsul modelului în contextul istoricului nostru de chat
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
  
Ce poți observa din acest exemplu este cum poți valorifica un parser preconstruit pentru a extrage informații cheie din input-ul utilizatorului, cum ar fi originea, destinația și data unei cereri de rezervare de zbor. Această abordare modulară îți permite să te concentrezi pe logica de nivel înalt.

### Valorifică uneltele colaborative

Cadre precum CrewAI, Microsoft AutoGen și Semantic Kernel facilitează crearea mai multor agenți care pot lucra împreună.

**Cum pot folosi echipele acestea**: Echipele pot proiecta agenți cu roluri și sarcini specifice, permițând testarea și rafinarea fluxurilor de lucru colaborative și îmbunătățind eficiența generală a sistemului.

**Cum funcționează în practică**: Poți crea o echipă de agenți în care fiecare are o funcție specializată, cum ar fi colectarea datelor, analiza sau luarea deciziilor. Acești agenți pot comunica și împărtăși informații pentru a atinge un scop comun, cum ar fi răspunsul la o întrebare a utilizatorului sau finalizarea unei sarcini.

**Exemplu de cod (AutoGen)**:

```python
# creați agenți, apoi creați un program round-robin în care pot lucra împreună, în acest caz în ordine

# Agent de preluare a datelor
# Agent de analiză a datelor
# Agent de luare a deciziilor

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

# conversația se încheie când utilizatorul spune "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Folosiți asyncio.run(...) când rulați un script.
await Console(stream)
```
  
Ce vezi în codul anterior este cum poți crea o sarcină care implică mai mulți agenți ce lucrează împreună pentru a analiza date. Fiecare agent realizează o funcție specifică, iar sarcina este executată prin coordonarea agenților pentru a obține rezultatul dorit. Prin crearea de agenți dedicați cu roluri specializate, poți îmbunătăți eficiența și performanța sarcinii.

### Învață în timp real

Cadrele avansate oferă capabilități pentru înțelegerea contextuală în timp real și adaptare.

**Cum pot folosi echipele acestea**: Echipele pot implementa bucle de feedback în care agenții învață din interacțiuni și își ajustează comportamentul dinamic, conducând la o îmbunătățire continuă și rafinare a capacităților.

**Cum funcționează în practică**: Agenții pot analiza feedback-ul utilizatorilor, datele de mediu și rezultatele sarcinilor pentru a-și actualiza baza de cunoștințe, a regla algoritmii de luare a deciziilor și a îmbunătăți performanța în timp. Acest proces iterativ de învățare permite agenților să se adapteze la condiții și preferințe ale utilizatorilor în schimbare, sporind eficacitatea generală a sistemului.

## Care sunt diferențele dintre cadrele AutoGen, Semantic Kernel și Azure AI Agent Service?

Există multe moduri de a compara aceste cadre, dar hai să vedem câteva diferențe cheie în ceea ce privește designul, capabilitățile și cazurile lor țintă de utilizare:

## AutoGen

AutoGen este un cadru open-source dezvoltat de AI Frontiers Lab de la Microsoft Research. Se concentrează pe aplicații *agențiale* distribuite, bazate pe evenimente, care permit multiple LLM-uri și SLM-uri, instrumente și modele avansate multi-agent.

AutoGen este construit în jurul conceptului central de agenți, entități autonome care pot percepe mediul înconjurător, lua decizii și întreprinde acțiuni pentru a atinge scopuri specifice. Agenții comunică prin mesaje asincrone, permițându-le să lucreze independent și în paralel, sporind scalabilitatea și rapiditatea sistemului.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenții se bazează pe modelul actorului</a>. Conform Wikipedia, un actor este _elementul de bază al calculului concurent. Ca răspuns la un mesaj primit, un actor poate: lua decizii locale, crea alți actori, trimite mesaje suplimentare și determina cum să răspundă la următorul mesaj primit_.

**Cazuri de utilizare**: Automatizarea generării de cod, sarcini de analiză de date și construirea de agenți personalizați pentru planificare și funcții de cercetare.

Iată câteva concepte de bază importante ale AutoGen:

- **Agenți**. Un agent este o entitate software care:
  - **Comunică prin mesaje**, care pot fi sincron sau asincron.
  - **Își menține propriul stadiu**, ce poate fi modificat de mesajele primite.
  - **Întreprinde acțiuni** ca răspuns la mesajele primite sau la schimbările din stadiul său. Aceste acțiuni pot modifica stadiul agentului și pot produce efecte externe, cum ar fi actualizarea jurnalelor de mesaje, trimiterea de mesaje noi, executarea de cod sau apeluri API.

  Iată un fragment de cod scurt în care creezi propriul agent cu capabilități de chat:

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
  
În codul anterior, `MyAgent` a fost creat și moștenește de la `RoutedAgent`. Are un handler de mesaje care afișează conținutul mesajelor și apoi trimite un răspuns folosind delegatul `AssistantAgent`. Observă mai ales cum se atribuie pentru `self._delegate` o instanță a `AssistantAgent`, care este un agent preconstruit ce poate gestiona completări de chat.

    Să anunțăm AutoGen despre acest tip de agent și să pornim programul mai departe:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Începe procesarea mesajelor în fundal.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```
  
În codul anterior, agenții sunt înregistrați în runtime și apoi se trimite un mesaj către agent, rezultând următorul output:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```
  
- **Multi-agenti**. AutoGen susține crearea mai multor agenți care pot lucra împreună pentru a realiza sarcini complexe. Agenții pot comunica, împărtăși informații și coordona acțiunile pentru a rezolva probleme mai eficient. Pentru a crea un sistem multi-agent, poți defini diferite tipuri de agenți cu funcții și roluri specializate, cum ar fi colectarea datelor, analiza, luarea deciziilor și interacțiunea cu utilizatorul. Hai să vedem cum arată o astfel de creație ca să avem o idee:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Exemplu de declarare a unui Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Folosind tipul 'topic' ca tip al agentului.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # Celelalte declarații au fost prescurtate din motive de concizie

    # Chat de grup
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
  
În codul precedent avem un `GroupChatManager` înregistrat în runtime. Acest manager este responsabil de coordonarea interacțiunilor între diferite tipuri de agenți, cum ar fi scriitorii, ilustratorii, editorii și utilizatorii.

- **Runtime pentru agenți**. Cadrul oferă un mediu de rulare care permite comunicarea între agenți, gestionează identitățile și ciclurile lor de viață și impune limite de securitate și confidențialitate. Acest lucru înseamnă că poți rula agenții într-un mediu sigur și controlat, asigurând interacțiuni sigure și eficiente. Sunt două tipuri de runtime de interes:
  - **Runtime standalone**. Este o opțiune bună pentru aplicații cu un singur proces, unde toți agenții sunt implementați în același limbaj de programare și rulează în același proces. Iată o ilustrație a modului în care funcționează:  
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Runtime standalone</a>  
Pachetul aplicației

    *agenții comunică prin mesaje prin runtime, iar runtime gestionează ciclul de viață al agenților*

  - **Runtime distribuit pentru agenți**, potrivit pentru aplicații multi-proces unde agenții pot fi implementați în limbaje de programare diferite și rulează pe mașini diferite. Iată o ilustrație a modului în care funcționează:  
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Runtime distribuit</a>

## Semantic Kernel + Agent Framework

Semantic Kernel este un SDK pentru orchestrare AI pregătit pentru întreprinderi. Este compus din conectori AI și de memorie, împreună cu un Cadru pentru Agenți.

Să începem cu câteva componente de bază:

- **Conectori AI**: Aceasta este o interfață cu servicii AI externe și surse de date utilizabilă atât în Python, cât și în C#.

  ```python
  # Kernel semantic pentru Python
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
  
Aici ai un exemplu simplu despre cum poți crea un kernel și adăuga un serviciu de completare chat. Semantic Kernel creează o conexiune către un serviciu AI extern, în acest caz, Azure OpenAI Chat Completion.

- **Pluginuri**: Acestea încuadrează funcții pe care o aplicație le poate folosi. Există atât pluginuri gata făcute, cât și unele personalizate pe care le poți crea. Un concept asociat este „funcțiile prompt”. În loc să furnizezi indicații în limbaj natural pentru invocarea funcțiilor, transmiți anumite funcții către model. Bazat pe contextul curent al chat-ului, modelul poate alege să apeleze una dintre aceste funcții pentru a îndeplini o solicitare sau un query. Iată un exemplu:

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
  
Aici, mai întâi ai un șablon de prompt `skPrompt` care lasă loc utilizatorului să introducă textul, `$userInput`. Apoi creezi funcția kernel `SummarizeText` și o imporți în kernel cu numele pluginului `SemanticFunctions`. Observă numele funcției care ajută Semantic Kernel să înțeleagă ce face funcția și când ar trebui apelată.

- **Funcție nativă**: Există și funcții native pe care cadrul le poate apela direct pentru a executa sarcini. Iată un exemplu de astfel de funcție care extrage conținutul dintr-un fișier:

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
  
- **Memorie**: Abstractizează și simplifică gestionarea contextului pentru aplicațiile AI. Ideea cu memoria este că aceasta este ceva ce LLM ar trebui să știe. Poți stoca aceste informații într-un magazin vectorial care devine o bază de date în memorie, o bază de date vectorială sau similar. Iată un exemplu de scenariu foarte simplificat în care se adaugă *fapte* în memorie:

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

Aceste informații sunt apoi stocate în colecția de memorie `SummarizedAzureDocs`. Acesta este un exemplu foarte simplificat, dar puteți vedea cum puteți stoca informații în memorie pentru ca LLM să le folosească.

Deci, acestea sunt elementele de bază ale framework-ului Semantic Kernel, dar ce putem spune despre Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service este o adiție mai recentă, introdusă la Microsoft Ignite 2024. Permite dezvoltarea și implementarea de agenți AI cu modele mai flexibile, cum ar fi apelarea directă a LLM-urilor open-source precum Llama 3, Mistral și Cohere.

Azure AI Agent Service oferă mecanisme de securitate enterprise mai puternice și metode de stocare a datelor, făcându-l potrivit pentru aplicații enterprise.

Funcționează direct cu framework-uri de orchestrare multi-agent precum AutoGen și Semantic Kernel.

Acest serviciu este în prezent în Previzualizare Publică și suportă Python și C# pentru construirea agenților.

Folosind Semantic Kernel Python, putem crea un Azure AI Agent cu un plugin definit de utilizator:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definește un plugin de exemplu pentru exemplu
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
        # Creează definiția agentului
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Creează Agentul AzureAI folosind clientul și definiția agentului definite
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Creează un fir de discuție pentru a găzdui conversația
        # Dacă nu se furnizează niciun fir, un fir nou va fi
        # creat și returnat împreună cu răspunsul inițial
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
                # Invocă agentul pentru firul specificat
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

### Concepute de bază

Azure AI Agent Service are următoarele concepte de bază:

- **Agent**. Azure AI Agent Service se integrează cu Microsoft Foundry. În AI Foundry, un AI Agent acționează ca un microserviciu „inteligent” care poate fi folosit pentru a răspunde la întrebări (RAG), a efectua acțiuni sau a automatiza complet fluxurile de lucru. Realizează acest lucru combinând puterea modelelor AI generative cu instrumente care îi permit să acceseze și să interacționeze cu surse reale de date. Iată un exemplu de agent:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    În acest exemplu, un agent este creat cu modelul `gpt-4o-mini`, un nume `my-agent` și instrucțiuni „You are helpful agent”. Agentul este echipat cu instrumente și resurse pentru a efectua sarcini de interpretare a codului.

- **Thread și mesaje**. Thread-ul este un alt concept important. Reprezintă o conversație sau o interacțiune între un agent și un utilizator. Thread-urile pot fi folosite pentru a urmări progresul unei conversații, a stoca informații de context și a gestiona starea interacțiunii. Iată un exemplu de thread:

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

    În codul anterior, un thread este creat. Ulterior, un mesaj este trimis thread-ului. Prin apelarea funcției `create_and_process_run`, agentului i se cere să efectueze lucrări pe thread. În final, mesajele sunt preluate și înregistrate pentru a vedea răspunsul agentului. Mesajele indică progresul conversației dintre utilizator și agent. Este, de asemenea, important să înțelegem că mesajele pot fi de tipuri diferite, cum ar fi text, imagine sau fișier, ceea ce înseamnă că munca agentului a generat, de exemplu, o imagine sau un răspuns text. Ca dezvoltator, puteți folosi atunci aceste informații pentru a procesa mai departe răspunsul sau pentru a-l prezenta utilizatorului.

- **Se integrează cu alte framework-uri AI**. Azure AI Agent Service poate interacționa cu alte framework-uri, cum ar fi AutoGen și Semantic Kernel, ceea ce înseamnă că puteți construi o parte din aplicația dvs. într-unul dintre aceste framework-uri și, de exemplu, să folosiți serviciul Agent ca orchestrator sau să construiți totul în serviciul Agent.

**Cazuri de utilizare**: Azure AI Agent Service este proiectat pentru aplicații enterprise care necesită implementare securizată, scalabilă și flexibilă a agenților AI.

## Care este diferența dintre aceste framework-uri?

Se pare că există multe suprapuneri între aceste framework-uri, dar există diferențe cheie în ceea ce privește designul, capabilitățile și cazurile țintă de utilizare:

- **AutoGen**: Este un framework de experimentare axat pe cercetarea de ultimă generație în sisteme multi-agent. Este cel mai bun loc pentru a experimenta și prototipa sisteme multi-agent sofisticate.
- **Semantic Kernel**: Este o bibliotecă gata pentru producție pentru construirea de aplicații agentice enterprise. Se concentrează pe aplicații agentice distribuite, bazate pe evenimente, permițând utilizarea mai multor LLM-uri și SLM-uri, unelte și modele de design cu agenți unici sau multipli.
- **Azure AI Agent Service**: Este o platformă și un serviciu de implementare în Azure Foundry pentru agenți. Oferă conectivitate pentru servicii suportate de Azure Foundry, precum Azure OpenAI, Azure AI Search, Bing Search și execuția codului.

Încă nu sunteți sigur pe care să-l alegeți?

### Cazuri de utilizare

Să vedem dacă vă putem ajuta parcurgând câteva cazuri comune de utilizare:

> Întrebare: Experimentez, învăț și construiesc aplicații agentice proof-of-concept și doresc să pot construi și experimenta rapid
>

> Răspuns: AutoGen ar fi o alegere bună pentru acest scenariu, deoarece se concentrează pe aplicații agentice distribuite, bazate pe evenimente și suportă modele avansate de design multi-agent.

> Întrebare: Ce face ca AutoGen să fie o alegere mai bună decât Semantic Kernel și Azure AI Agent Service pentru acest caz de utilizare?
>
> Răspuns: AutoGen este proiectat special pentru aplicații agentice distribuite, bazate pe evenimente, ceea ce îl face potrivit pentru automatizarea sarcinilor de generare cod și analiză de date. Oferă instrumentele și capabilitățile necesare pentru a construi sisteme complexe multi-agent în mod eficient.

> Întrebare: Se pare că Azure AI Agent Service ar putea funcționa și el aici, are unelte pentru generare de cod și altele?

>
> Răspuns: Da, Azure AI Agent Service este un serviciu de platformă pentru agenți și adaugă capabilități încorporate pentru mai multe modele, Azure AI Search, Bing Search și Azure Functions. Facilitează construirea agenților în Foundry Portal și implementarea lor la scară.

> Întrebare: Încă sunt confuz, dă-mi te rog o singură opțiune
>
> Răspuns: O alegere excelentă este să-ți construiești aplicația în Semantic Kernel mai întâi și apoi să folosești Azure AI Agent Service pentru a-ți implementa agentul. Această abordare îți permite să persiști ușor agenții în timp ce valorifici puterea de a construi sisteme multi-agent în Semantic Kernel. În plus, Semantic Kernel are un conector în AutoGen, făcând ușoară utilizarea ambelor framework-uri împreună.

Să rezumăm principalele diferențe într-un tabel:

| Framework | Focus | Concepute de bază | Cazuri de utilizare |
| --- | --- | --- | --- |
| AutoGen | Aplicații agentice distribuite, bazate pe evenimente | Agenți, Personaje, Funcții, Date | Generare de cod, sarcini de analiză a datelor |
| Semantic Kernel | Înțelegerea și generarea de conținut textual asemănător omului | Agenți, Componente modulare, Colaborare | Înțelegerea limbajului natural, generare de conținut |
| Azure AI Agent Service | Modele flexibile, securitate enterprise, generare cod, apelare unelte | Modularitate, Colaborare, Orchestrarea proceselor | Implementare agenți AI securizată, scalabilă și flexibilă |

Care este cazul ideal de utilizare pentru fiecare dintre aceste framework-uri?

## Pot integra instrumentele mele existente din ecosistemul Azure direct, sau am nevoie de soluții independente?

Răspunsul este da, puteți integra instrumentele existente din ecosistemul Azure direct cu Azure AI Agent Service, mai ales pentru că a fost construit să funcționeze perfect cu alte servicii Azure. De exemplu, ați putea integra Bing, Azure AI Search și Azure Functions. Există, de asemenea, o integrare profundă cu Microsoft Foundry.

Pentru AutoGen și Semantic Kernel, puteți de asemenea să integrați cu serviciile Azure, dar este posibil să fie nevoie să apelați serviciile Azure din codul vostru. O altă modalitate de integrare este să folosiți SDK-urile Azure pentru a interacționa cu serviciile Azure din agenții voștri. În plus, așa cum s-a menționat, puteți folosi Azure AI Agent Service ca orchestrator pentru agenții construiți în AutoGen sau Semantic Kernel, ceea ce oferă acces facil la ecosistemul Azure.

## Coduri de exemplu

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Aveți mai multe întrebări despre AI Agent Frameworks?

Alăturați-vă [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la ore de asistență și a primi răspunsuri la întrebările despre AI Agents.

## Referințe

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel și AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## Lecția anterioară

[Introducere în agenții AI și cazuri de utilizare pentru agenți](../01-intro-to-ai-agents/README.md)

## Lecția următoare

[Înțelegerea modelelor de design agentice](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Declinare de responsabilitate**:  
Acest document a fost tradus folosind serviciul de traducere AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original, în limba sa nativă, trebuie considerat sursa autoritară. Pentru informații critice, se recomandă traducerea profesională realizată de un specialist uman. Nu ne asumăm răspunderea pentru eventualele neînțelegeri sau interpretări greșite care decurg din utilizarea acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->