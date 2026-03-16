[![Prozkoumání rámců AI agentů](../../../translated_images/cs/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Klikněte na obrázek výše pro zhlédnutí videa této lekce)_

# Prozkoumejte rámce AI agentů

Rámce pro AI agenty jsou softwarové platformy navržené tak, aby zjednodušily vytváření, nasazení a správu AI agentů. Tyto rámce poskytují vývojářům předpřipravené komponenty, abstrakce a nástroje, které zefektivňují vývoj složitých AI systémů.

Tyto rámce pomáhají vývojářům soustředit se na jedinečné aspekty jejich aplikací tím, že poskytují standardizované přístupy k běžným výzvám ve vývoji AI agentů. Zvyšují škálovatelnost, dostupnost a efektivitu při budování AI systémů.

## Úvod 

Tato lekce se bude zabývat:

- Co jsou rámce AI agentů a čeho díky nim mohou vývojáři dosáhnout?
- Jak mohou týmy tyto rámce využít k rychlému prototypování, iteracím a zlepšování schopností svého agenta?
- Jaké jsou rozdíly mezi rámci a nástroji vytvořenými společností Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, a <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Mohu přímo integrovat nástroje ze stávajícího ekosystému Azure, nebo potřebuji samostatná řešení?
- Co je služba Azure AI Agents a jak mi pomáhá?

## Cíle učení

Cílem této lekce je pomoci vám pochopit:

- Úlohu rámců AI agentů ve vývoji umělé inteligence.
- Jak využít rámce AI agentů k vytváření inteligentních agentů.
- Klíčové schopnosti umožněné rámci AI agentů.
- Rozdíly mezi AutoGen, Semantic Kernel a Azure AI Agent Service.

## Co jsou rámce AI agentů a co díky nim mohou vývojáři dělat?

Tradiční AI rámce vám mohou pomoci integrovat AI do vašich aplikací a zlepšit je následujícími způsoby:

- **Personalizace**: AI může analyzovat chování a preference uživatelů, aby poskytla personalizovaná doporučení, obsah a zážitky.
Příklad: Streamovací služby jako Netflix používají AI k doporučování filmů a pořadů na základě sledovací historie, čímž zvyšují zapojení uživatelů a jejich spokojenost.
- **Automatizace a efektivita**: AI může automatizovat opakující se úkoly, optimalizovat pracovní postupy a zlepšovat provozní efektivitu.
Příklad: Aplikace zákaznické podpory používají chatboty poháněné AI k řešení běžných dotazů, čímž snižují dobu odezvy a uvolňují lidské agenty pro složitější problémy.
- **Vylepšená uživatelská zkušenost**: AI může zlepšit celkovou uživatelskou zkušenost tím, že poskytne inteligentní funkce jako rozpoznávání hlasu, zpracování přirozeného jazyka a prediktivní text.
Příklad: Virtuální asistenti jako Siri a Google Assistant používají AI k rozpoznávání a reagování na hlasové příkazy, což uživatelům usnadňuje interakci s jejich zařízeními.

### To všechno zní skvěle, že? Proč tedy potřebujeme rámec AI agentů?

Rámce pro AI agenty představují něco víc než jen AI rámce. Jsou navrženy tak, aby umožnily vytváření inteligentních agentů, kteří mohou interagovat s uživateli, jinými agenty a prostředím za účelem dosažení konkrétních cílů. Tihle agenti mohou vykazovat autonomní chování, činit rozhodnutí a přizpůsobovat se měnícím se podmínkám. Podívejme se na některé klíčové schopnosti, které rámce AI agentů umožňují:

- **Spolupráce a koordinace agentů**: Umožňují vytváření více AI agentů, kteří mohou spolupracovat, komunikovat a koordinovat se při řešení složitých úkolů.
- **Automatizace a řízení úkolů**: Poskytují mechanismy pro automatizaci vícestupňových pracovních postupů, delegování úkolů a dynamické řízení úkolů mezi agenty.
- **Kontextuální porozumění a adaptace**: Vybavují agenty schopností porozumět kontextu, přizpůsobit se měnícím se podmínkám a činit rozhodnutí na základě informací v reálném čase.

Stručně řečeno, agenti vám umožňují dělat víc, posunout automatizaci na vyšší úroveň a vytvářet inteligentnější systémy, které se dokážou přizpůsobit a učit se z prostředí.

## Jak rychle prototypovat, iterovat a zlepšovat schopnosti agenta?

Jedná se o rychle se vyvíjející oblast, ale existují některé společné prvky napříč většinou rámců AI agentů, které vám mohou pomoci rychle prototypovat a iterovat, konkrétně modulární komponenty, nástroje pro spolupráci a učení v reálném čase. Pojďme se na ně podívat podrobněji:

- **Používejte modulární komponenty**: AI SDK nabízejí předpřipravené komponenty, jako jsou AI a paměťové konektory, volání funkcí pomocí přirozeného jazyka nebo pluginů kódu, šablony promptů a další.
- **Využijte nástroje pro spolupráci**: Navrhujte agenty s konkrétními rolemi a úkoly, což jim umožní testovat a zdokonalovat společné pracovní postupy.
- **Učení v reálném čase**: Implementujte zpětnovazební smyčky, kde se agenti učí z interakcí a dynamicky upravují své chování.

### Používejte modulární komponenty

SDK jako Microsoft Semantic Kernel a LangChain nabízejí předpřipravené komponenty, jako jsou AI konektory, šablony promptů a správa paměti.

**Jak mohou týmy tyto nástroje použít**: Týmy mohou rychle sestavit tyto komponenty a vytvořit funkční prototyp bez nutnosti začínat od nuly, což umožňuje rychlé experimentování a iterace.

**Jak to funguje v praxi**: Můžete použít předpřipravený parser k extrahování informací z uživatelského vstupu, modul paměti k ukládání a načítání dat a generátor promptů k interakci s uživateli, to vše bez nutnosti budovat tyto komponenty od začátku.

**Ukázkový kód**. Pojďme se podívat na příklady, jak můžete použít předpřipravený AI konektor se Semantic Kernel Python a .Net, který používá automatické volání funkcí, aby model reagoval na uživatelský vstup:

``` python
# Příklad Semantic Kernel v Pythonu

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definujte objekt ChatHistory pro uchování kontextu konverzace
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definujte ukázkový plugin, který obsahuje funkci pro rezervaci cesty
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Vytvořte Kernel
kernel = Kernel()

# Přidejte ukázkový plugin do objektu Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definujte Azure OpenAI AI konektor
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Nastavte požadavky pro konfiguraci modelu s automatickým voláním funkcí
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Proveďte požadavek na model pro danou historii chatu a nastavení požadavku
    # Kernel obsahuje ukázku, kterou bude model vyžadovat k vyvolání
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
    # Příklad odpovědi AI modelu: `Váš let do New Yorku dne 1. ledna 2025 byl úspěšně rezervován. Šťastnou cestu! ✈️🗽`

    # Přidejte odpověď modelu do našeho kontextu historie chatu
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

Z tohoto příkladu můžete vidět, jak lze využít předpřipravený parser k extrahování klíčových informací z uživatelského vstupu, jako je odletové místo, destinace a datum žádosti o rezervaci letu. Tento modulární přístup vám umožňuje soustředit se na logiku na vyšší úrovni.

### Využijte nástroje pro spolupráci

Rámce jako CrewAI, Microsoft AutoGen a Semantic Kernel usnadňují vytváření více agentů, kteří mohou spolupracovat.

**Jak mohou týmy tyto nástroje použít**: Týmy mohou navrhovat agenty s konkrétními rolemi a úkoly, což jim umožní testovat a vylepšovat kolaborativní pracovní postupy a zlepšovat celkovou efektivitu systému.

**Jak to funguje v praxi**: Můžete vytvořit tým agentů, kde každý agent má specializovanou funkci, například získávání dat, analýzu nebo rozhodování. Tito agenti mohou komunikovat a sdílet informace, aby dosáhli společného cíle, například odpovědi na uživatelský dotaz nebo dokončení úkolu.

**Ukázkový kód (AutoGen)**:

```python
# vytváření agentů, poté vytvořte plán round robin, kde mohou spolupracovat, v tomto případě v pořadí

# Agent pro získávání dat
# Agent pro analýzu dat
# Agent pro rozhodování

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

# konverzace končí, když uživatel řekne "SCHVÁLIT"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Použijte asyncio.run(...), pokud spouštíte ve skriptu.
await Console(stream)
```

V předchozím kódu můžete vidět, jak vytvořit úkol, do kterého je zapojeno více agentů pracujících společně na analýze dat. Každý agent vykonává konkrétní funkci a úkol je proveden koordinací agentů, aby bylo dosaženo požadovaného výsledku. Vytvořením dedikovaných agentů se specializovanými rolemi můžete zlepšit efektivitu a výkon úkolů.

### Učení v reálném čase

Pokročilé rámce poskytují schopnosti pro pochopení kontextu v reálném čase a adaptaci.

**Jak mohou týmy tyto nástroje použít**: Týmy mohou implementovat zpětnovazební smyčky, kde se agenti učí z interakcí a dynamicky upravují své chování, což vede k průběžnému zlepšování a zdokonalování schopností.

**Jak to funguje v praxi**: Agenti mohou analyzovat zpětnou vazbu uživatelů, data z prostředí a výsledky úkolů, aby aktualizovali svou databázi znalostí, upravili algoritmy rozhodování a zlepšili výkon v čase. Tento iterativní proces učení umožňuje agentům přizpůsobit se měnícím se podmínkám a preferencím uživatelů a zvyšuje celkovou efektivitu systému.

## Jaké jsou rozdíly mezi rámci AutoGen, Semantic Kernel a Azure AI Agent Service?

Existuje mnoho způsobů, jak tyto rámce porovnat, ale podívejme se na některé klíčové rozdíly z hlediska jejich návrhu, schopností a cílových případů použití:

## AutoGen

AutoGen je open-source rámec vyvinutý laboratoří AI Frontiers Lab v Microsoft Research. Zaměřuje se na událostmi řízené distribuované *agentické* aplikace, umožňující více LLM a SLM, nástroje a pokročilé víceagentní návrhové vzory.

AutoGen je postaven kolem základního konceptu agentů, což jsou autonomní entity, které mohou vnímat své prostředí, činit rozhodnutí a provádět akce k dosažení konkrétních cílů. Agenti komunikují asynchronními zprávami, což jim umožňuje pracovat nezávisle a paralelně, čímž se zvyšuje škálovatelnost a rychlost odezvy systému.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenti jsou založeni na modelu aktorů</a>. Podle Wikipedie je aktor _základním stavebním prvkem souběžného výpočtu. V reakci na přijatou zprávu může aktor: provést lokální rozhodnutí, vytvořit více aktorů, odeslat další zprávy a určit, jak reagovat na další přijatou zprávu_.

**Případy použití**: Automatizace generování kódu, úlohy analýzy dat a vytváření vlastních agentů pro plánování a výzkumné funkce.

Zde jsou některé důležité klíčové koncepty AutoGen:

- **Agents**. Agent je softwarová entita, která:
  - **Komunikuje prostřednictvím zpráv**, tyto zprávy mohou být synchronní nebo asynchronní.
  - **Udržuje svůj vlastní stav**, který může být modifikován příchozími zprávami.
  - **Provádí akce** v reakci na přijaté zprávy nebo změny ve svém stavu. Tyto akce mohou upravovat stav agenta a mít vnější efekty, například aktualizaci záznamů zpráv, odesílání nových zpráv, vykonávání kódu nebo volání API.
    
  Zde máte krátký úryvek kódu, ve kterém vytvoříte vlastního agenta s chatovacími schopnostmi:

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
    
    V předchozím kódu byl vytvořen `MyAgent`, který dědí z `RoutedAgent`. Má obslužnou rutinu zpráv, která vypisuje obsah zprávy a poté odesílá odpověď pomocí delegáta `AssistantAgent`. Zvláště si všimněte, jak přiřazujeme do `self._delegate` instanci `AssistantAgent`, která je předpřipraveným agentem schopným zpracovávat chatová doplnění.


    Nyní nechme AutoGen vědět o tomto typu agenta a spusťme program:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Spustit zpracování zpráv na pozadí.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    V předchozím kódu jsou agenti registrováni v runtime a poté je agentovi odeslána zpráva, což má za následek následující výstup:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multi agents**. AutoGen podporuje vytváření více agentů, kteří mohou spolupracovat na dosažení složitých úkolů. Agenti mohou komunikovat, sdílet informace a koordinovat své akce pro efektivnější řešení problémů. Pro vytvoření multiagentního systému můžete definovat různé typy agentů se specializovanými funkcemi a rolemi, například získávání dat, analýzu, rozhodování a interakci s uživatelem. Podívejme se, jak takové vytvoření vypadá, abychom si to lépe představili:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Příklad deklarace Agenta
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Použití typu topic jako typu agenta.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="VAŠE_API_KLÍČ",
        ),
        ),
    )

    # ostatní deklarace zkráceny pro stručnost

    # Skupinový chat
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="VAŠE_API_KLÍČ",
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

    V předchozím kódu máme `GroupChatManager`, který je registrován v runtime. Tento manažer je zodpovědný za koordinaci interakcí mezi různými typy agentů, jako jsou autoři, ilustrátoři, editoři a uživatelé.

- **Agent Runtime**. Rámec poskytuje běhové prostředí, které umožňuje komunikaci mezi agenty, spravuje jejich identity a životní cykly a vynucuje bezpečnostní a soukromé hranice. To znamená, že můžete spouštět své agenty v zabezpečeném a kontrolovaném prostředí, což zajišťuje, že mohou bezpečně a efektivně komunikovat. Existují dvě runtime, které stojí za zmínku:
  - **Stand-alone runtime**. Toto je dobrá volba pro aplikace běžící v jednom procesu, kde jsou všichni agenti implementováni ve stejném programovacím jazyce a běží ve stejném procesu. Zde je ilustrace, jak to funguje:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Samostatné runtime</a>   
Aplikační zásobník

    *agenti komunikují prostřednictvím zpráv přes runtime a runtime spravuje životní cyklus agentů*

  - **Distributed agent runtime**, je vhodné pro víceprocesové aplikace, kde mohou být agenti implementováni v různých programovacích jazycích a běžet na různých strojích. Zde je ilustrace, jak to funguje:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distribuované runtime</a>

## Semantic Kernel + Agent Framework

Semantic Kernel je SDK pro orchestraci AI připravené pro podnikové použití. Skládá se z AI a paměťových konektorů spolu s Agent Frameworkem.

Nejprve pokryjme některé základní komponenty:

- **AI Connectors**: Jedná se o rozhraní s externími AI službami a datovými zdroji pro použití jak v Pythonu, tak v C#.

  ```python
  # Sémantické jádro Pythonu
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

    Zde máte jednoduchý příklad, jak vytvořit kernel a přidat službu pro doplňování chatu. Semantic Kernel vytváří připojení k externí AI službě, v tomto případě Azure OpenAI Chat Completion.

- **Plugins**: Tyto zapouzdřují funkce, které může aplikace použít. Existují hotové pluginy i vlastní, které si můžete vytvořit. S tím souvisí pojem "prompt functions". Místo poskytování přirozeného jazyka jako výzvy pro volání funkcí vysíláte modelu určité funkce. Na základě aktuálního kontextu chatu se model může rozhodnout zavolat jednu z těchto funkcí k dokončení požadavku nebo dotazu. Zde je příklad:

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

    Zde máte nejprve šablonu promptu `skPrompt`, která nechává místo pro uživatelský vstup, `$userInput`. Poté vytvoříte kernel funkci `SummarizeText` a importujete ji do kernelu s názvem pluginu `SemanticFunctions`. Všimněte si názvu funkce, která pomáhá Semantic Kernelu pochopit, co funkce dělá a kdy by měla být volána.

- **Native function**: Existují také nativní funkce, které může rámec volat přímo k provedení úkolu. Zde je příklad takové funkce, která získává obsah ze souboru:

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

- **Memory**:  Zjednodušuje a abstrahuje správu kontextu pro AI aplikace. Myšlenka paměti je taková, že jde o informace, které by model měl znát. Tyto informace můžete ukládat ve vektorovém úložišti, které může být v paměti jako databáze nebo ve formě vektorové databáze či podobně. Zde je příklad velmi zjednodušeného scénáře, kde jsou do paměti přidávány *fakty*:

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

    Tyto informace jsou pak uloženy do kolekce paměti `SummarizedAzureDocs`. Jedná se o velmi zjednodušený příklad, ale můžete vidět, jak můžete ukládat informace do paměti, aby je LLM mohl použít.

    Takže to jsou základy rámce Semantic Kernel, co je to s Agent Frameworkem?

    ## Azure AI Agent Service

    Služba Azure AI Agent je novější doplněk, představený na Microsoft Ignite 2024. Umožňuje vývoj a nasazení AI agentů s flexibilnějšími modely, jako je přímé volání open-source LLM jako Llama 3, Mistral a Cohere.

    Služba Azure AI Agent poskytuje silnější mechanismy podnikové bezpečnosti a metody ukládání dat, díky čemuž je vhodná pro podnikové aplikace. 

    Funguje „out-of-the-box“ s víceagentními orchestracemi jako AutoGen a Semantic Kernel.

    Tato služba je momentálně ve veřejné ukázce (Public Preview) a podporuje Python a C# pro vytváření agentů.

    Použitím Semantic Kernel Python můžeme vytvořit Azure AI Agenta s uživatelem definovaným pluginem:

    ```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definujte ukázkový plugin pro vzorek
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
        # Vytvořte definici agenta
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Vytvořte AzureAI agenta pomocí definovaného klienta a definice agenta
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Vytvořte vlákno pro držení konverzace
        # Pokud není poskytnuto žádné vlákno, bude nové vlákno
        # vytvořeno a vráceno s počáteční odpovědí
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
                # Vyvolejte agenta pro specifikované vlákno
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

    ### Základní koncepty

    Azure AI Agent Service má následující základní koncepty:

    - **Agent**. Azure AI Agent Service se integruje s Microsoft Foundry. V rámci AI Foundry funguje AI Agent jako „chytrá“ mikroslužba, kterou lze použít k odpovídání na otázky (RAG), provádění akcí nebo plné automatizaci pracovních postupů. Dosahuje toho kombinací síly generativních AI modelů s nástroji, které mu umožňují přistupovat k reálným datovým zdrojům a interagovat s nimi. Zde je příklad agenta:

        ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

        V tomto příkladu je agent vytvořen s modelem `gpt-4o-mini`, jménem `my-agent` a instrukcemi `You are helpful agent`. Agent je vybaven nástroji a zdroji k provádění úloh interpretace kódu.

    - **Vlákno a zprávy**. Vlákno je dalším důležitým konceptem. Představuje konverzaci nebo interakci mezi agentem a uživatelem. Vlákna lze použít ke sledování průběhu konverzace, ukládání kontextových informací a správě stavu interakce. Zde je příklad vlákna:

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

        V předchozím kódu je vytvořeno vlákno. Poté je do vlákna odeslána zpráva. Zavoláním `create_and_process_run` je agent požádán, aby na vláknu provedl práci. Nakonec jsou zprávy získány a zalogovány, abyste viděli odpověď agenta. Zprávy ukazují průběh konverzace mezi uživatelem a agentem. Je také důležité pochopit, že zprávy mohou být různých typů, jako text, obrázek nebo soubor; to znamená, že práce agenta mohla vést například k vytvoření obrázku nebo textové odpovědi. Jako vývojář pak můžete tyto informace dále zpracovat nebo je prezentovat uživateli.

    - **Integrace s jinými AI rámci**. Služba Azure AI Agent může spolupracovat s jinými rámci jako AutoGen a Semantic Kernel, což znamená, že část vaší aplikace můžete postavit v jednom z těchto rámců a například používat Agent service jako orchestrátor, nebo můžete vše postavit v Agent service.

    **Případy použití**: Azure AI Agent Service je navržena pro podnikové aplikace, které vyžadují bezpečné, škálovatelné a flexibilní nasazení AI agentů.

    ## Jaký je rozdíl mezi těmito rámci?

    Zdá se, že mezi těmito rámci existuje mnoho překryvů, ale existují některé klíčové rozdíly ve smyslu jejich návrhu, schopností a cílových případů použití:

    - **AutoGen**: Je to experimentální rámec zaměřený na špičkový výzkum v oblasti multi-agentních systémů. Je to nejlepší místo pro experimentování a prototypování sofistikovaných multi-agentních systémů.
    - **Semantic Kernel**: Je to do produkce připravená knihovna pro budování podnikových agentních aplikací. Zaměřuje se na událostmi řízené, distribuované agentní aplikace, umožňující více LLM a SLM, nástroje a návrhové vzory pro jednoho i více agentů.
    - **Azure AI Agent Service**: Je to platforma a služba nasazení v Azure Foundry pro agenty. Nabízí konektivitu k službám podporovaným Azure Foundry, jako Azure OpenAI, Azure AI Search, Bing Search a spouštění kódu.

    Stále si nejste jisti, který zvolit?

    ### Případy použití

    Pokusíme se vám pomoci tím, že projdeme některé běžné případy použití:

    > Otázka: Experimentuji, učím se a stavím proof-of-concept agentních aplikací a chci mít možnost rychle stavět a experimentovat
    >
    > Odpověď: AutoGen by byla dobrá volba pro tento scénář, protože se zaměřuje na událostmi řízené, distribuované agentní aplikace a podporuje pokročilé víceagentní návrhové vzory.

    > Otázka: Co dělá AutoGen lepší volbou než Semantic Kernel a Azure AI Agent Service pro tento případ použití?
    >
    > Odpověď: AutoGen je speciálně navržen pro událostmi řízené, distribuované agentní aplikace, díky čemuž je vhodný pro automatizaci generování kódu a úloh analýzy dat. Poskytuje potřebné nástroje a schopnosti pro efektivní budování složitých multi-agentních systémů.

    > Otázka: Zdá se, že by zde mohlo fungovat i Azure AI Agent Service, má nástroje pro generování kódu a další?
    >
    > Odpověď: Ano, Azure AI Agent Service je platformní služba pro agenty a přidává vestavěné schopnosti pro více modelů, Azure AI Search, Bing Search a Azure Functions. Umožňuje snadno stavět agenty v Foundry Portalu a nasazovat je ve velkém měřítku.

    > Otázka: Pořád jsem zmatený, dejte mi prosím jednu možnost
    >
    > Odpověď: Skvělou volbou je nejprve vytvořit svou aplikaci v Semantic Kernel a poté použít Azure AI Agent Service k nasazení vašeho agenta. Tento přístup vám umožní snadno perzistentně ukládat vaše agenty při využití síly budování multi-agentních systémů v Semantic Kernel. Navíc má Semantic Kernel konektor v AutoGen, což usnadňuje společné použití obou rámců.

    Shrňme klíčové rozdíly v tabulce:

    | Framework | Zaměření | Základní koncepty | Použití |
    | --- | --- | --- | --- |
    | AutoGen | Událostmi řízené, distribuované agentní aplikace | Agenti, Personas, Functions, Data | Generování kódu, úlohy analýzy dat |
    | Semantic Kernel | Porozumění a generování lidsky podobného textu | Agenti, modulární komponenty, spolupráce | Porozumění přirozenému jazyku, generování obsahu |
    | Azure AI Agent Service | Flexibilní modely, podniková bezpečnost, generování kódu, volání nástrojů | Modularita, spolupráce, orchestrace procesů | Bezpečné, škálovatelné a flexibilní nasazení AI agentů |

    Jaký je ideální případ použití pro každý z těchto rámců?

    ## Mohu přímo integrovat své stávající nástroje z Azure ekosystému, nebo potřebuji samostatná řešení?

    Odpověď zní ano, můžete své stávající nástroje z Azure ekosystému přímo integrovat zejména se Službou Azure AI Agent, protože byla navržena tak, aby bezproblémově fungovala s ostatními službami Azure. Můžete například integrovat Bing, Azure AI Search a Azure Functions. Existuje také hluboká integrace s Microsoft Foundry.

    Pro AutoGen a Semantic Kernel můžete také integrovat služby Azure, ale může být nutné volat tyto služby přímo z vašeho kódu. Dalším způsobem integrace je použití Azure SDK ke komunikaci se službami Azure z vašich agentů. Jak již bylo zmíněno, můžete také používat Azure AI Agent Service jako orchestrátor pro vaše agenty vytvořené v AutoGen nebo Semantic Kernel, což by poskytlo snadný přístup do Azure ekosystému.

    ## Ukázkové kódy

    - Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
    - .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

    ## Máte další otázky ohledně rámců AI agentů?

    Připojte se k [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), setkejte se s dalšími studenty, navštěvujte konzultační hodiny a nechte zodpovědět své otázky o AI agentech.

    ## Reference

    - <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Služba Azure AI Agent</a>
    - <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel a AutoGen</a>
    - <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Agentní rámec Semantic Kernel pro Python</a>
    - <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Agentní rámec Semantic Kernel pro .Net</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Služba Azure AI Agent</a>
    - <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Použití služby Azure AI Agent s AutoGen / Semantic Kernel k vytvoření řešení s více agenty</a>

    ## Předchozí lekce

    [Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

    ## Další lekce

    [Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vyloučení odpovědnosti**:
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). Ačkoliv usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho původním jazyce by měl být považován za rozhodující zdroj. Pro důležité informace se doporučuje profesionální lidský překlad. Za jakákoli nedorozumění nebo nesprávné výklady vyplývající z použití tohoto překladu neneseme odpovědnost.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->