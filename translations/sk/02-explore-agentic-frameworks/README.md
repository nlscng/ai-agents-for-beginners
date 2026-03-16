[![Preskúmanie rámcov AI agentov](../../../translated_images/sk/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Kliknite na obrázok vyššie pre zobrazenie videa tejto lekcie)_

# Preskúmajte rámce AI agentov

Rámce AI agentov sú softvérové platformy navrhnuté tak, aby zjednodušili vytváranie, nasadzovanie a správu AI agentov. Tieto rámce poskytujú vývojárom predpripravené komponenty, abstrakcie a nástroje, ktoré zefektívňujú vývoj komplexných AI systémov.

Tieto rámce pomáhajú vývojárom sústrediť sa na jedinečné aspekty ich aplikácií tým, že poskytujú štandardizované prístupy k bežným výzvam vo vývoji AI agentov. Zvyšujú škálovateľnosť, dostupnosť a efektívnosť pri budovaní AI systémov.

## Úvod

Táto lekcia pokryje:

- Čo sú rámce AI agentov a čo umožňujú vývojárom dosiahnuť?
- Ako môžu tímy tieto rámce využiť na rýchle prototypovanie, iteráciu a zlepšovanie schopností svojich agentov?
- Aké sú rozdiely medzi rámcami a nástrojmi vytvorenými spoločnosťou Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> a <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Môžem integrovať svoje existujúce nástroje v ekosystéme Azure priamo, alebo potrebujem samostatné riešenia?
- Čo je služba Azure AI Agents a ako mi pomáha?

## Ciele učenia

Ciele tejto lekcie sú pomôcť vám pochopiť:

- Úlohu rámcov AI agentov vo vývoji AI.
- Ako využiť rámce AI agentov na vytváranie inteligentných agentov.
- Kľúčové schopnosti, ktoré rámce AI agentov umožňujú.
- Rozdiely medzi AutoGen, Semantic Kernel a Azure AI Agent Service.

## Čo sú rámce AI agentov a čo umožňujú vývojárom robiť?

Tradičné AI rámce vám môžu pomôcť integrovať AI do vašich aplikácií a zlepšiť tieto aplikácie nasledujúcimi spôsobmi:

- **Personalizácia**: AI môže analyzovať správanie používateľov a ich preferencie, aby poskytla personalizované odporúčania, obsah a zážitky.
Príklad: Streamingové služby ako Netflix používajú AI na odporúčanie filmov a relácií na základe histórie sledovania, čím zvyšujú angažovanosť a spokojnosť používateľov.
- **Automatizácia a efektívnosť**: AI môže automatizovať opakujúce sa úlohy, zjednodušiť pracovné postupy a zlepšiť prevádzkovú efektívnosť.
Príklad: Aplikácie zákazníckej podpory používajú chatboty poháňané AI na riešenie bežných otázok, čo skracuje čas odozvy a uvoľňuje ľudských agentov pre zložitejšie problémy.
- **Vylepšený používateľský zážitok**: AI môže zlepšiť celkový používateľský zážitok poskytovaním inteligentných funkcií, ako je rozpoznávanie hlasu, spracovanie prirodzeného jazyka a prediktívny text.
Príklad: Virtuálni asistenti ako Siri a Google Assistant používajú AI na pochopenie a odpovedanie na hlasové príkazy, čo uľahčuje používateľom interakciu so svojimi zariadeniami.

### To všetko znie skvelo, však, tak prečo potrebujeme rámec AI agentov?

Rámce AI agentov predstavujú niečo viac než len AI rámce. Sú navrhnuté tak, aby umožnili vytváranie inteligentných agentov, ktorí môžu komunikovať s používateľmi, inými agentmi a prostredím s cieľom dosiahnuť konkrétne ciele. Títo agenti môžu vykazovať autonómne správanie, prijímať rozhodnutia a prispôsobovať sa meniacim sa podmienkam. Pozrime sa na niektoré kľúčové schopnosti, ktoré rámce AI agentov umožňujú:

- **Spolupráca a koordinácia agentov**: Umožňujú vytváranie viacerých AI agentov, ktorí môžu spolupracovať, komunikovať a koordinovať sa pri riešení komplexných úloh.
- **Automatizácia a riadenie úloh**: Poskytujú mechanizmy na automatizáciu viacstupňových pracovných postupov, delegovanie úloh a dynamické riadenie úloh medzi agentmi.
- **Kontextové porozumenie a adaptácia**: Vybavujú agentov schopnosťou rozumieť kontextu, prispôsobovať sa meniacim sa prostrediam a prijímať rozhodnutia na základe informácií v reálnom čase.

Celkovo agenti umožňujú robiť viac, posunúť automatizáciu na ďalšiu úroveň a vytvárať inteligentnejšie systémy, ktoré sa dokážu prispôsobiť a učiť sa zo svojho prostredia.

## Ako rýchlo prototypovať, iterovať a zlepšovať schopnosti agenta?

Toto je rýchlo sa meniacie prostredie, ale existujú určité prvky, ktoré sú spoločné pre väčšinu rámcov AI agentov a ktoré vám môžu pomôcť rýchlo prototypovať a iterovať, a to najmä modulárne komponenty, kolaboračné nástroje a učenie v reálnom čase. Pozrime sa na ne:

- **Používajte modulárne komponenty**: AI SDK ponúkajú predpripravené komponenty, ako sú AI a pamäťové konektory, volanie funkcií pomocou prirodzeného jazyka alebo pluginov s kódom, šablóny promptov a ďalšie.
- **Využívajte kolaboračné nástroje**: Navrhujte agentov so špecifickými rolami a úlohami, čo im umožní testovať a zdokonaľovať kolaboratívne pracovné postupy.
- **Učte sa v reálnom čase**: Implementujte spätné slučky, kde sa agenti učia z interakcií a dynamicky upravujú svoje správanie.

### Používajte modulárne komponenty

SDK ako Microsoft Semantic Kernel a LangChain ponúkajú predpripravené komponenty, ako sú AI konektory, šablóny promptov a správa pamäte.

**Ako môžu tímy tieto komponenty využiť**: Tímy môžu rýchlo zostaviť tieto komponenty, aby vytvorili funkčný prototyp bez nutnosti začínať od nuly, čo umožňuje rýchlé experimentovanie a iterovanie.

**Ako to funguje v praxi**: Môžete použiť predpripravený parser na extrahovanie informácií z používateľského vstupu, modul pamäte na ukladanie a získavanie údajov a generátor promptov na interakciu s používateľmi, to všetko bez potreby budovať tieto komponenty od začiatku.

**Príklad kódu**. Pozrime sa na príklady, ako môžete použiť predpripravený AI konektor so Semantic Kernel v Pythone a .Net, ktorý používa automatické volanie funkcií na to, aby model reagoval na vstup používateľa:

``` python
# Príklad Semantic Kernel v Pythone

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definujte objekt ChatHistory na uchovávanie kontextu konverzácie
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definujte ukážkový plugin, ktorý obsahuje funkciu na rezerváciu cesty
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Vytvorte Kernel
kernel = Kernel()

# Pridajte ukážkový plugin do objektu Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definujte AI konektor Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definujte nastavenia požiadavky na konfiguráciu modelu s automatickým volaním funkcie
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Vykonajte požiadavku na model pre danú históriu chatu a nastavenia požiadavky
    # Kernel obsahuje ukážku, ktorú bude model vyžadovať na spustenie
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
    # Príklad odpovede AI modelu: `Váš let do New Yorku na 1. januára 2025 bol úspešne rezervovaný. Šťastnú cestu! ✈️🗽`

    # Pridajte odpoveď modelu do nášho kontextu histórie chatu
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

Z tohto príkladu môžete vidieť, ako môžete využiť predpripravený parser na extrahovanie kľúčových informácií zo vstupu používateľa, ako sú miesto odletu, cieľ a dátum žiadosti o rezerváciu letu. Tento modulárny prístup vám umožňuje sústrediť sa na logiku na vyššej úrovni.

### Využívajte kolaboračné nástroje

Rámce ako CrewAI, Microsoft AutoGen a Semantic Kernel uľahčujú vytváranie viacerých agentov, ktorí môžu spolupracovať.

**Ako môžu tímy tieto využiť**: Tímy môžu navrhovať agentov so špecifickými rolami a úlohami, čo im umožní testovať a zdokonaliť kolaboratívne pracovné postupy a zlepšiť celkovú efektívnosť systému.

**Ako to funguje v praxi**: Môžete vytvoriť tím agentov, kde každý agent má špecializovanú funkciu, ako napríklad získavanie údajov, analýza alebo rozhodovanie. Títo agenti môžu komunikovať a zdieľať informácie, aby dosiahli spoločný cieľ, napríklad odpovedanie na dotaz používateľa alebo dokončenie úlohy.

**Príklad kódu (AutoGen)**:

```python
# vytváranie agentov, potom vytvorte rozvrh round robin, kde môžu pracovať spolu, v tomto prípade v poradí

# Agent na získavanie dát
# Agent na analýzu dát
# Agent na rozhodovanie

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

# konverzácia končí, keď používateľ povie "SCHVÁLIŤ"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Použite asyncio.run(...), keď spúšťate skript.
await Console(stream)
```

V predchádzajúcom kóde vidíte, ako môžete vytvoriť úlohu, ktorá zahŕňa viacerých agentov pracujúcich spolu na analýze údajov. Každý agent vykonáva konkrétnu funkciu a úloha je vykonaná koordináciou agentov s cieľom dosiahnuť požadovaný výsledok. Vytváraním dedikovaných agentov so špecializovanými rolami môžete zlepšiť efektívnosť a výkon úloh.

### Učte sa v reálnom čase

Pokročilé rámce poskytujú schopnosti pre porozumenie kontextu v reálnom čase a adaptáciu.

**Ako môžu tímy tieto využiť**: Tímy môžu implementovať spätné slučky, kde sa agenti učia z interakcií a dynamicky upravujú svoje správanie, čo vedie k neustálemu zlepšovaniu a zdokonaľovaniu schopností.

**Ako to funguje v praxi**: Agenti môžu analyzovať spätnú väzbu používateľov, environmentálne dáta a výsledky úloh, aby aktualizovali svoju databázu znalostí, upravili algoritmy rozhodovania a zlepšili výkon v priebehu času. Tento iteratívny proces učenia umožňuje agentom prispôsobiť sa meniacim sa podmienkam a preferenciám používateľov, čím sa zvyšuje celková účinnosť systému.

## Aké sú rozdiely medzi rámcami AutoGen, Semantic Kernel a Azure AI Agent Service?

Existuje mnoho spôsobov, ako tieto rámce porovnať, ale pozrime sa na niektoré kľúčové rozdiely z hľadiska ich dizajnu, schopností a cieľových prípadov použitia:

## AutoGen

AutoGen je open-source rámec vyvinutý laboratóriom AI Frontiers Lab v Microsoft Research. Zameriava sa na event-driven, distribuované *agentic* aplikácie, umožňujúce viacero LLM a SLM, nástroje a pokročilé vzory navrhovania viacerých agentov.

AutoGen je postavený okolo základného konceptu agentov, ktoré sú autonómnymi entitami schopnými vnímať svoje prostredie, prijímať rozhodnutia a vykonávať akcie na dosiahnutie konkrétnych cieľov. Agenti komunikujú asynchrónnymi správami, čo im umožňuje pracovať nezávisle a paralelne, čím sa zvyšuje škálovateľnosť a odozva systému.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenti sú založení na modeli aktéra</a>. Podľa Wikipédie je aktér _základným stavebným prvkom súbežného výpočtu. V reakcii na správu, ktorú prijme, môže aktér: robiť lokálne rozhodnutia, vytvárať ďalších aktérov, posielať ďalšie správy a rozhodnúť, ako reagovať na nasledujúcu prijatú správu_.

**Prípady použitia**: Automatizácia generovania kódu, úlohy analýzy údajov a vytváranie vlastných agentov pre plánovanie a výskumné funkcie.

Tu sú niektoré dôležité základné koncepty AutoGen:

- **Agenti**. Agent je softvérová entita, ktorá:
  - **Komunikuje prostredníctvom správ**, tieto správy môžu byť synchronné alebo asynchronné.
  - **Udržiava vlastný stav**, ktorý môže byť upravovaný prichádzajúcimi správami.
  - **Vykonáva akcie** v reakcii na prijaté správy alebo zmeny svojho stavu. Tieto akcie môžu upravovať stav agenta a vytvárať externé efekty, ako je aktualizácia záznamov správ, odosielanie nových správ, spúšťanie kódu alebo volanie API.
    
  Tu máte krátky ukážkový úryvok kódu, v ktorom vytvoríte vlastného agenta s chatovacími schopnosťami:

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
    
    V predchádzajúcom kóde bol vytvorený `MyAgent`, ktorý dedí od `RoutedAgent`. Má handler správ, ktorý vypíše obsah správy a potom odošle odpoveď pomocou delegáta `AssistantAgent`. Zvlášť si všimnite, ako priraďujeme do `self._delegate` inštanciu `AssistantAgent`, ktorá je predpripraveným agentom schopným spracovať chat completions.


    Informujme AutoGen o tomto type agenta a následne spustíme program:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Spustite spracovanie správ na pozadí.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    V predchádzajúcom kóde sú agenti zaregistrovaní v runtime a potom je agentovi odoslaná správa, čo má za následok nasledujúci výstup:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Viacerí agenti**. AutoGen podporuje vytváranie viacerých agentov, ktorí môžu spolupracovať na dosiahnutí komplexných úloh. Agenti môžu komunikovať, zdieľať informácie a koordinovať svoje akcie, aby efektívnejšie riešili problémy. Na vytvorenie systému s viacerými agentmi môžete definovať rôzne typy agentov so špecializovanými funkciami a rolami, ako je získavanie údajov, analýza, rozhodovanie a interakcia s používateľom. Pozrime sa, ako takáto tvorba vyzerá, aby sme si to vedeli lepšie predstaviť:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Príklad deklarácie Agenta
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Použitie typu topic ako typu agenta.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # zvyšné deklarácie skrátené pre stručnosť

    # Skupinový chat
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

    V predchádzajúcom kóde máme `GroupChatManager`, ktorý je zaregistrovaný v runtime. Tento manažér je zodpovedný za koordináciu interakcií medzi rôznymi typmi agentov, ako sú spisovatelia, ilustrátori, redaktori a používatelia.

- **Agent Runtime**. Rámec poskytuje runtime prostredie, umožňujúce komunikáciu medzi agentmi, spravuje ich identity a životné cykly a vynucuje bezpečnostné a súkromné hranice. To znamená, že môžete svoje agenti spúšťať v zabezpečenom a kontrolovanom prostredí, čo zaisťuje ich bezpečnú a efektívnu interakciu. Existujú dva runtime, ktoré sú predmetom záujmu:
  - **Samostatné runtime**. Toto je dobrá voľba pre aplikácie bežiace v jednom procese, kde sú všetci agenti implementovaní v rovnakom programovacom jazyku a bežia v tom istom procese. Tu je ilustrácia, ako to funguje:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Samostatné runtime</a>   
Aplikačný zásobník

    *agenti komunikujú prostredníctvom správ cez runtime a runtime spravuje životný cyklus agentov*

  - **Distribuovaný agent runtime**, je vhodný pre viacprocesové aplikácie, kde môžu byť agenti implementovaní v rôznych programovacích jazykoch a bežať na rôznych strojoch. Tu je ilustrácia, ako to funguje:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distribuované runtime</a>

## Semantic Kernel + Agent Framework

Semantic Kernel je enterprise-ready AI Orchestration SDK. Skladá sa z AI a pamäťových konektorov, spolu s Agent Frameworkom.

Najprv pokryjme niektoré základné komponenty:

- **AI konektory**: Ide o rozhranie k externým AI službám a zdrojom dát na použitie v Pythone aj C#.

  ```python
  # Semantické jadro Python
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

    Tu máte jednoduchý príklad toho, ako môžete vytvoriť kernel a pridať službu chat completions. Semantic Kernel vytvorí spojenie s externou AI službou, v tomto prípade Azure OpenAI Chat Completion.

- **Pluginy**: Tieto zapuzdrujú funkcie, ktoré môže aplikácia využívať. Existujú hotové pluginy aj vlastné, ktoré si môžete vytvoriť. Súvisiacim konceptom sú "prompt funkcie". Namiesto poskytovania prirodzených jazykových nápoved na vyvolanie funkcie, propagujete určité funkcie modelu. Na základe aktuálneho chatového kontextu sa model môže rozhodnúť zavolať jednu z týchto funkcií na dokončenie požiadavky alebo dotazu. Tu je príklad:

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

    Tu máte najprv šablónu promptu `skPrompt`, ktorá ponecháva priestor pre vstup používateľa, `$userInput`. Potom vytvoríte kernel funkciu `SummarizeText` a následne ju importujete do kernelu s názvom pluginu `SemanticFunctions`. Všimnite si názov funkcie, ktorý pomáha Semantic Kernelu pochopiť, čo funkcia robí a kedy by mala byť zavolaná.

- **Natívna funkcia**: Existujú aj natívne funkcie, ktoré môže rámec volať priamo na vykonanie úlohy. Tu je príklad takejto funkcie, ktorá získava obsah zo súboru:

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

- **Pamäť**: Abstrahuje a zjednodušuje správu kontextu pre AI aplikácie. Myšlienka pamäte je, že ide o informácie, ktoré by mal LLM vedieť. Tieto informácie môžete uložiť do vektorového úložiska, ktoré môže byť v pamäti, vektorová databáza alebo podobné riešenie. Tu je príklad veľmi zjednodušeného scenára, kde sa do pamäte pridávajú *fakty*:

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

    Tieto fakty sa potom ukladajú do kolekcie pamäte `SummarizedAzureDocs`. Toto je veľmi zjednodušený príklad, ale môžete vidieť, ako môžete ukladať informácie do pamäte, aby ich LLM mohol použiť.

Takže to sú základy rámca Semantic Kernel, čo potom Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service je novší prírastok, predstavený na Microsoft Ignite 2024. Umožňuje vývoj a nasadenie AI agentov s flexibilnejšími modelmi, ako priame volanie open-source LLM ako Llama 3, Mistral a Cohere.

Azure AI Agent Service poskytuje silnejšie mechanizmy podnikového zabezpečenia a metódy ukladania údajov, vďaka čomu je vhodná pre podnikové aplikácie. 

Funguje bez ďalšej konfigurácie s rámcami na orchestráciu viacerých agentov, ako sú AutoGen a Semantic Kernel.

Táto služba je momentálne v Public Preview a podporuje Python a C# na vytváranie agentov.

Pomocou Semantic Kernel Python môžeme vytvoriť Azure AI Agenta s používateľsky definovaným pluginom:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definujte ukážkový plugin pre ukážku
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
        # Vytvorte definíciu agenta
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Vytvorte AzureAI agenta pomocou definovaného klienta a definície agenta
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Vytvorte vlákno na uchovanie konverzácie
        # Ak nie je poskytnuté žiadne vlákno, bude vytvorené nové vlákno
        # a vrátené s počiatočnou odpoveďou
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
                # Vyvolajte agenta pre zadané vlákno
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

### Základné koncepty

Služba Azure AI Agent Service má nasledujúce základné koncepty:

- **Agent**. Služba Azure AI Agent Service sa integruje s Microsoft Foundry. Vnútri AI Foundry vystupuje AI Agent ako "inteligentná" mikroslužba, ktorú je možné použiť na zodpovedanie otázok (RAG), vykonávanie akcií alebo úplnú automatizáciu pracovných tokov. Dosahuje to kombinovaním sily generatívnych AI modelov s nástrojmi, ktoré mu umožňujú pristupovať k reálnym zdrojom dát a s nimi interagovať. Tu je príklad agenta:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    V tomto príklade je vytvorený agent s modelom `gpt-4o-mini`, menom `my-agent` a inštrukciami `You are helpful agent`. Agent je vybavený nástrojmi a zdrojmi na vykonávanie úloh interpretácie kódu.

- **Thread and messages**. Thread predstavuje ďalší dôležitý koncept. Reprezentuje konverzáciu alebo interakciu medzi agentom a používateľom. Thready môžu slúžiť na sledovanie priebehu konverzácie, ukladanie kontextových informácií a správu stavu interakcie. Tu je príklad thread-u:

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

    V predchádzajúcom kóde je vytvorený thread. Následne je do threadu odoslaná správa. Zavolaním `create_and_process_run` je agent požiadaný, aby vo threade vykonal prácu. Nakoniec sú správy načítané a zaznamenané, aby ste videli odpoveď agenta. Správy indikujú priebeh konverzácie medzi používateľom a agentom. Je tiež dôležité pochopiť, že správy môžu byť rôznych typov, ako sú text, obrázok alebo súbor — napríklad práca agenta môže viesť napríklad k obrázku alebo k textovej odpovedi. Ako vývojár potom môžete tieto informácie použiť na ďalšie spracovanie odpovede alebo jej zobrazenie používateľovi.

- **Integruje sa s inými AI rámcami**. Služba Azure AI Agent Service môže interagovať s inými rámcami ako AutoGen a Semantic Kernel, čo znamená, že môžete časť svojej aplikácie postaviť v jednom z týchto rámcov a napríklad použiť službu Agent ako orchestrátor, alebo môžete všetko zostaviť priamo v službe Agent.

**Príklady použitia**: Služba Azure AI Agent Service je navrhnutá pre podnikové aplikácie, ktoré vyžadujú bezpečné, škálovateľné a flexibilné nasadenie AI agentov.

## Čím sa tieto rámce líšia?
 
Znie to, že medzi týmito rámcami je veľa prekryvov, ale existujú kľúčové rozdiely z hľadiska ich dizajnu, schopností a cieľových prípadov použitia:
 
- **AutoGen**: Je experimentálny rámec zameraný na špičkový výskum v oblasti systémov viacerých agentov. Je to najvhodnejšie miesto na experimentovanie a prototypovanie sofistikovaných systémov viacerých agentov.
- **Semantic Kernel**: Je produkčne pripravená knižnica pre agentov na vytváranie podnikov ých agentných aplikácií. Zameriava sa na udalostne riadené, distribuované agentné aplikácie, umožňujúc viaceré LLM a SLM, nástroje a návrhové vzory pre jedného alebo viacerých agentov.
- **Azure AI Agent Service**: Je platforma a služba nasadenia v Azure Foundry pre agentov. Ponúka budovanie konektivity ku službám podporovaným v Azure Foundry, ako sú Azure OpenAI, Azure AI Search, Bing Search a vykonávanie kódu.
 
Stále si nie ste istí, ktorý zvoliť?

### Príklady použitia
 
Pozrime sa, či vám môžeme pomôcť prejsť niektoré bežné prípady použitia:
 
> Q: Experimentujem, učím sa a vytváram proof-of-concept agentné aplikácie, a chcem byť schopný rýchlo stavať a experimentovať
>
>
>A: AutoGen by bol dobrá voľba pre tento scenár, pretože sa zameriava na udalostne riadené, distribuované agentné aplikácie a podporuje pokročilé návrhové vzory pre viac agentov.

> Q: Čím je AutoGen lepšou voľbou než Semantic Kernel a Azure AI Agent Service pre tento prípad použitia?
>
> A: AutoGen je špeciálne navrhnutý pre udalostne riadené, distribuované agentné aplikácie, vďaka čomu je vhodný na automatizáciu generovania kódu a úloh analýzy dát. Poskytuje potrebné nástroje a schopnosti na efektívne budovanie zložitých systémov viacerých agentov.

>Q: Znie to, že Azure AI Agent Service by tu tiež mohla fungovať, má nástroje na generovanie kódu a viac?

>
> A: Áno, Azure AI Agent Service je platformová služba pre agentov a pridáva vstavané schopnosti pre viaceré modely, Azure AI Search, Bing Search a Azure Functions. Uľahčuje vytváranie agentov v portáli Foundry a ich nasadzovanie v mierke.
 
> Q: Stále som zmätený len mi dajte jednu možnosť
>
> A: Výbornou voľbou je najskôr vytvoriť aplikáciu v Semantic Kernel a potom použiť Azure AI Agent Service na nasadenie vášho agenta. Tento prístup vám umožní ľahko perzistovať vašich agentov pri využití sily pre budovanie systémov viacerých agentov v Semantic Kernel. Navyše má Semantic Kernel konektor v AutoGen, čo uľahčuje používanie oboch rámcov spolu.
 
Zhrňme kľúčové rozdiely v tabuľke:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Udalostne riadené, distribuované agentné aplikácie | Agenti, Persony, Funkcie, Dáta | Generovanie kódu, úlohy analýzy dát |
| Semantic Kernel | Pochopenie a generovanie textu podobného ľudskému | Agenti, Modulárne komponenty, Spolupráca | Porozumenie prirodzenému jazyku, generovanie obsahu |
| Azure AI Agent Service | Flexibilné modely, podnikové zabezpečenie, generovanie kódu, volanie nástrojov | Modularita, Spolupráca, Orchestrace procesov | Bezpečné, škálovateľné a flexibilné nasadenie AI agentov |

What's the ideal use case for each of these frameworks?

## Môžem integrovať moje existujúce nástroje ekosystému Azure priamo, alebo potrebujem samostatné riešenia?

Odpoveď je áno, môžete integrovať existujúce nástroje ekosystému Azure priamo, najmä so službou Azure AI Agent Service, pretože bola postavená tak, aby bezproblémovo spolupracovala s inými službami Azure. Môžete napríklad integrovať Bing, Azure AI Search a Azure Functions. Existuje tiež hlboká integrácia s Microsoft Foundry.

Pre AutoGen a Semantic Kernel môžete tiež integrovať služby Azure, ale môže to vyžadovať, aby ste služby Azure volali z vášho kódu. Ďalším spôsobom integrácie je používanie Azure SDK na interakciu so službami Azure z vašich agentov. Ako bolo spomenuté, môžete použiť Azure AI Agent Service ako orchestrátor pre agentov vytvorených v AutoGen alebo Semantic Kernel, čo by poskytlo ľahký prístup k ekosystému Azure.

## Ukážky kódu

- Python: [Rámec agentov](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Rámec agentov](./code_samples/02-dotnet-agent-framework.md)

## Máte ďalšie otázky o rámcoch AI agentov?

Pripojte sa k [Discord Microsoft Foundry](https://aka.ms/ai-agents/discord), aby ste sa stretli s ďalšími študentmi, zúčastnili sa konzultačných hodín a získali odpovede na svoje otázky o AI agentech.

## Referencie

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Služba Azure Agent</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel a AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Python rámec agentov Semantic Kernel</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Rámec agentov Semantic Kernel (.NET)</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Služba Azure AI Agent</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Použitie Azure AI Agent Service s AutoGen / Semantic Kernel na vytvorenie riešenia s viacerými agentmi</a>

## Predchádzajúca lekcia

[Úvod do AI agentov a prípadov použitia agentov](../01-intro-to-ai-agents/README.md)

## Ďalšia lekcia

[Pochopenie agentných návrhových vzorov](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Vylúčenie zodpovednosti:
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Hoci sa snažíme o presnosť, berte prosím na vedomie, že automatické preklady môžu obsahovať chyby alebo nepresnosti. Pôvodný dokument v jeho pôvodnom jazyku by sa mal považovať za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny ľudský preklad. Nie sme zodpovední za akékoľvek nedorozumenia alebo mylné výklady vyplývajúce z použitia tohto prekladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->