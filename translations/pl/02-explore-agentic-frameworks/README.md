[![Eksploracja frameworków agentów AI](../../../translated_images/pl/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Kliknij powyższy obraz, aby obejrzeć wideo z tej lekcji)_

# Eksploracja frameworków agentów AI

Frameworki agentów AI to platformy programowe zaprojektowane, aby uprościć tworzenie, wdrażanie i zarządzanie agentami AI. Te frameworki dostarczają deweloperom gotowe komponenty, abstrakcje i narzędzia, które usprawniają rozwój złożonych systemów AI.

Frameworki te pomagają deweloperom skupić się na unikalnych aspektach ich aplikacji, oferując standaryzowane podejścia do powszechnych wyzwań w rozwoju agentów AI. Zwiększają skalowalność, dostępność i efektywność budowania systemów AI.

## Wprowadzenie

Ta lekcja obejmie:

- Czym są frameworki agentów AI i co umożliwiają deweloperom osiągnąć?
- Jak zespoły mogą szybko prototypować, iterować i ulepszać możliwości swoich agentów?
- Jakie są różnice między frameworkami i narzędziami stworzonymi przez Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> oraz <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Czy mogę bezpośrednio integrować moje istniejące narzędzia z ekosystemu Azure, czy potrzebuję rozwiązań samodzielnych?
- Czym jest usługa Azure AI Agents i jak mi pomaga?

## Cele nauki

Celem tej lekcji jest pomoc w zrozumieniu:

- Roli frameworków agentów AI w rozwoju AI.
- Jak wykorzystać frameworki agentów AI do budowy inteligentnych agentów.
- Kluczowych możliwości oferowanych przez frameworki agentów AI.
- Różnic między AutoGen, Semantic Kernel i Azure AI Agent Service.

## Czym są frameworki agentów AI i co umożliwiają deweloperom?

Tradycyjne frameworki AI mogą pomóc zintegrować AI w twoich aplikacjach i uczynić je lepszymi poprzez:

- **Personalizację**: AI może analizować zachowania i preferencje użytkowników, aby dostarczać spersonalizowane rekomendacje, treści i doświadczenia.
Przykład: Serwisy streamingowe takie jak Netflix wykorzystują AI, aby sugerować filmy i programy na podstawie historii oglądania, zwiększając zaangażowanie i zadowolenie użytkowników.
- **Automatyzację i efektywność**: AI może automatyzować powtarzalne zadania, usprawniać przebiegi pracy i poprawiać efektywność operacyjną.
Przykład: Aplikacje obsługi klienta używają chatbotów napędzanych AI do obsługi typowych zapytań, skracając czas reakcji i odciążając pracowników do bardziej złożonych problemów.
- **Ulepszone doświadczenie użytkownika**: AI może poprawić ogólne doświadczenie użytkownika, zapewniając inteligentne funkcje takie jak rozpoznawanie mowy, przetwarzanie języka naturalnego oraz tekst predykcyjny.
Przykład: Asystenci wirtualni tacy jak Siri i Google Assistant używają AI do rozumienia i odpowiadania na polecenia głosowe, ułatwiając interakcję użytkowników z urządzeniami.

### Wszystko to brzmi świetnie, prawda? To po co nam framework agentów AI?

Frameworki agentów AI to coś więcej niż zwykłe frameworki AI. Są zaprojektowane, aby umożliwić tworzenie inteligentnych agentów, którzy mogą wchodzić w interakcje z użytkownikami, innymi agentami i środowiskiem, aby osiągać określone cele. Ci agenci mogą wykazywać autonomiczne zachowania, podejmować decyzje i dostosowywać się do zmieniających się warunków. Spójrzmy na niektóre kluczowe możliwości zapewniane przez frameworki agentów AI:

- **Współpraca i koordynacja agentów**: Umożliwiają tworzenie wielu agentów AI, którzy mogą razem pracować, komunikować się i koordynować, aby rozwiązywać złożone zadania.
- **Automatyzacja i zarządzanie zadaniami**: Zapewniają mechanizmy automatyzacji wieloetapowych procesów, delegowania zadań i dynamicznego zarządzania zadaniami wśród agentów.
- **Kontekstowe rozumienie i adaptacja**: Wyposażają agentów w zdolność rozumienia kontekstu, dostosowywania się do zmieniającego się środowiska oraz podejmowania decyzji w oparciu o informacje w czasie rzeczywistym.

Podsumowując, agenci pozwalają na więcej, przenosząc automatyzację na wyższy poziom, tworząc inteligentniejsze systemy, które potrafią się uczyć i dostosowywać do środowiska.

## Jak szybko prototypować, iterować i ulepszać możliwości agenta?

To szybko zmieniająca się dziedzina, ale istnieją pewne elementy wspólne dla większości frameworków agentów AI, które pomogą szybko prototypować i iterować, mianowicie modułowe komponenty, narzędzia do współpracy oraz naukę w czasie rzeczywistym. Przyjrzyjmy się im:

- **Używaj modułowych komponentów**: SDK AI oferują gotowe komponenty takie jak konektory AI i pamięci, wywoływanie funkcji za pomocą języka naturalnego lub wtyczek kodu, szablony promptów i inne.
- **Wykorzystuj narzędzia do współpracy**: Projektuj agentów z konkretnymi rolami i zadaniami, umożliwiając im testowanie i udoskonalanie wspólnych przebiegów pracy.
- **Ucz się w czasie rzeczywistym**: Wdrażaj pętle zwrotne, gdzie agenci uczą się na podstawie interakcji i dynamicznie dostosowują swoje zachowanie.

### Używaj modułowych komponentów

SDK takie jak Microsoft Semantic Kernel i LangChain oferują gotowe komponenty, takie jak konektory AI, szablony promptów i zarządzanie pamięcią.

**Jak zespoły mogą z nich korzystać**: Zespoły mogą szybko łączyć te komponenty, aby stworzyć funkcjonalny prototyp bez rozpoczynania od zera, co pozwala na szybkie eksperymentowanie i iterację.

**Jak to działa w praktyce**: Możesz użyć gotowego parsera do wyciągania informacji z danych wejściowych użytkownika, modułu pamięci do przechowywania i odzyskiwania danych oraz generatora promptów do interakcji z użytkownikami, wszystko bez konieczności budowania tych komponentów od podstaw.

**Przykład kodu**. Spójrzmy na przykłady, jak użyć gotowego konektora AI z Semantic Kernel w Python i .Net, który korzysta z automatycznego wywoływania funkcji, by model odpowiadał na dane wejściowe użytkownika:

``` python
# Przykład Semantic Kernel w Pythonie

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Zdefiniuj obiekt ChatHistory, aby przechowywał kontekst rozmowy
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Zdefiniuj przykładową wtyczkę, która zawiera funkcję rezerwacji podróży
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Utwórz Kernel
kernel = Kernel()

# Dodaj przykładową wtyczkę do obiektu Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Zdefiniuj konektor AI dla Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Zdefiniuj ustawienia żądania, aby skonfigurować model do automatycznego wywoływania funkcji
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Wyślij żądanie do modelu dla podanej historii czatu i ustawień żądania
    # Kernel zawiera przykład, który model poprosi o wywołanie
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
    # `Twój lot do Nowego Jorku na 1 stycznia 2025 został pomyślnie zarezerwowany. Bezpiecznej podróży! ✈️🗽`

    # Dodaj odpowiedź modelu do kontekstu historii czatu
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

Z tego przykładu widzimy, jak wykorzystać gotowy parser do wyciągania kluczowych informacji z wprowadzenia użytkownika, takich jak miejsce początkowe, cel i data rezerwacji lotu. Takie modułowe podejście pozwala skupić się na logice na wyższym poziomie.

### Wykorzystuj narzędzia do współpracy

Frameworki takie jak CrewAI, Microsoft AutoGen i Semantic Kernel ułatwiają tworzenie wielu agentów, którzy mogą współpracować.

**Jak zespoły mogą z nich korzystać**: Zespoły mogą projektować agentów z określonymi rolami i zadaniami, co umożliwia testowanie i udoskonalanie wspólnych przebiegów pracy oraz poprawę efektywności całego systemu.

**Jak to działa w praktyce**: Możesz stworzyć zespół agentów, gdzie każdy ma specjalizowaną funkcję, na przykład pozyskiwanie danych, analizę lub podejmowanie decyzji. Agenci mogą się komunikować i dzielić informacjami, aby osiągnąć wspólny cel, taki jak odpowiedź na zapytanie użytkownika lub wykonanie zadania.

**Przykład kodu (AutoGen)**:

```python
# tworzenie agentów, następnie utworzenie harmonogramu round-robin, w którym mogą współpracować, w tym przypadku w kolejności

# Agent pobierania danych
# Agent analizy danych
# Agent podejmowania decyzji

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

# konwersacja kończy się, gdy użytkownik powie "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Użyj asyncio.run(...), gdy uruchamiasz w skrypcie.
await Console(stream)
```

W poprzednim kodzie widać, jak można stworzyć zadanie obejmujące współpracę wielu agentów analizujących dane. Każdy agent wykonuje określoną funkcję, a zadanie jest realizowane poprzez koordynację agentów, aby osiągnąć oczekiwany rezultat. Tworzenie dedykowanych agentów ze specjalistycznymi rolami poprawia efektywność i wydajność zadań.

### Ucz się w czasie rzeczywistym

Zaawansowane frameworki oferują zdolności do rozumienia kontekstu i adaptacji w czasie rzeczywistym.

**Jak zespoły mogą z nich korzystać**: Zespoły mogą wdrażać pętle zwrotne, w których agenci uczą się na podstawie interakcji i dynamicznie dostosowują swoje zachowanie, co prowadzi do ciągłej poprawy i udoskonalania możliwości.

**Jak to działa w praktyce**: Agenci analizują opinie użytkowników, dane środowiskowe oraz wyniki zadań, aby aktualizować swoją bazę wiedzy, dostosowywać algorytmy podejmowania decyzji i poprawiać wydajność w czasie. Ten iteracyjny proces uczenia pozwala agentom reagować na zmieniające się warunki i preferencje użytkowników, podnosząc ogólną skuteczność systemu.

## Jakie są różnice między frameworkami AutoGen, Semantic Kernel i Azure AI Agent Service?

Istnieje wiele sposobów porównania tych frameworków, ale spójrzmy na niektóre kluczowe różnice pod kątem ich konstrukcji, możliwości oraz docelowych zastosowań:

## AutoGen

AutoGen to otwartoźródłowy framework opracowany przez Microsoft Research AI Frontiers Lab. Koncentruje się na zdarzeniowych, rozproszonych aplikacjach *agentowych*, umożliwiając wykorzystanie wielu modeli LLM i SLM, narzędzi oraz zaawansowanych wzorców projektowych wieloagentowych.

AutoGen opiera się na kluczowej koncepcji agentów, którzy są autonomicznymi jednostkami zdolnymi do postrzegania środowiska, podejmowania decyzji i działania celem osiągnięcia konkretnych celów. Agenci komunikują się asynchronicznie, co pozwala im pracować niezależnie i równolegle, zwiększając skalowalność i efektywność systemu.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenci opierają się na modelu aktora</a>. Z Wikipedii: aktor to _podstawowy blok budulcowy współbieżnych obliczeń. W odpowiedzi na otrzymaną wiadomość aktor może: podejmować lokalne decyzje, tworzyć kolejnych aktorów, wysyłać kolejne wiadomości i decydować, jak zareagować na następną otrzymaną wiadomość_.

**Przypadki użycia**: Automatyzacja generowania kodu, zadania analizy danych oraz tworzenie niestandardowych agentów do planowania i funkcji badawczych.

Oto niektóre ważne podstawowe koncepcje AutoGen:

- **Agenci**. Agent to oprogramowanie, które:
  - **Komunikuje się poprzez wiadomości**, które mogą być synchroniczne lub asynchroniczne.
  - **Utrzymuje własny stan**, który może być modyfikowany przez przychodzące wiadomości.
  - **Wykonuje działania** w odpowiedzi na otrzymane wiadomości lub zmiany stanu. Działania te mogą modyfikować stan agenta i wywoływać efekty zewnętrzne, takie jak aktualizowanie logów wiadomości, wysyłanie nowych wiadomości, wykonywanie kodu lub wywoływanie API.
    
  Poniżej krótki fragment kodu, w którym tworzysz własnego agenta z funkcjami czatu:

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
    
    W poprzednim kodzie `MyAgent` został utworzony i dziedziczy po `RoutedAgent`. Ma handler wiadomości, który wypisuje zawartość wiadomości, a następnie wysyła odpowiedź używając delegata `AssistantAgent`. Szczególnie zwróć uwagę, jak przypisujemy do `self._delegate` instancję `AssistantAgent`, który jest gotowym agentem obsługującym uzupełnienia czatu.


    Teraz poinformujmy AutoGen o tego typu agencie i uruchommy program:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Rozpocznij przetwarzanie wiadomości w tle.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    W poprzednim kodzie agenci są rejestrowani w środowisku wykonawczym, a następnie wysłana jest wiadomość do agenta, co skutkuje następującym wynikiem:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Wieloagentowość**. AutoGen wspiera tworzenie wielu agentów, którzy mogą współpracować, aby realizować złożone zadania. Agenci mogą komunikować się, dzielić informacjami i koordynować swoje działania w celu efektywniejszego rozwiązywania problemów. Aby stworzyć system wieloagentowy, możesz definiować różne typy agentów z wyspecjalizowanymi funkcjami i rolami, takimi jak pozyskiwanie danych, analiza, podejmowanie decyzji czy interakcja z użytkownikiem. Zobaczmy, jak wygląda takie tworzenie:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Przykład deklaracji agenta
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Użycie typu topic jako typu agenta.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # pozostałe deklaracje skrócone dla zwięzłości

    # Czat grupowy
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

    W poprzednim kodzie mamy `GroupChatManager` zarejestrowanego w środowisku wykonawczym. Manager ten odpowiada za koordynację interakcji między różnymi typami agentów, takimi jak pisarze, ilustratorzy, redaktorzy i użytkownicy.

- **Środowisko wykonawcze agentów**. Framework zapewnia środowisko wykonawcze, które umożliwia komunikację między agentami, zarządza ich tożsamościami oraz cyklem życia i egzekwuje granice bezpieczeństwa i prywatności. Dzięki temu możesz uruchamiać agentów w bezpiecznym i kontrolowanym środowisku, zapewniając, że mogą bezpiecznie i efektywnie wchodzić w interakcję. Istnieją dwa środowiska wykonawcze:
  - **Samodzielne środowisko wykonawcze**. To dobra opcja dla aplikacji jednowątkowych, gdzie wszyscy agenci są zaimplementowani w tym samym języku programowania i działają w tym samym procesie. Oto ilustracja działania:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Samodzielne środowisko wykonawcze</a>   
Stos aplikacji

    *agenci komunikują się poprzez wiadomości przez środowisko wykonawcze, które zarządza ich cyklem życia*

  - **Rozproszone środowisko wykonawcze**, nadaje się do aplikacji wieloprocesowych, w których agenci mogą być zaimplementowani w różnych językach programowania i działać na różnych maszynach. Oto ilustracja działania:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Rozproszone środowisko wykonawcze</a>

## Semantic Kernel + Framework Agentów

Semantic Kernel to biznesowy SDK do orkiestracji AI. Składa się z konektorów AI i pamięci oraz Frameworka Agentów.

Najpierw omówmy podstawowe komponenty:

- **Konektory AI**: To interfejs do zewnętrznych usług AI i źródeł danych, używany zarówno w Pythonie, jak i C#.

  ```python
  # Semantyczne jądro — Python
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

    Poniżej prosty przykład, jak możesz stworzyć kernel i dodać usługę uzupełniania czatu. Semantic Kernel tworzy połączenie z zewnętrzną usługą AI, w tym przypadku Azure OpenAI Chat Completion.

- **Wtyczki (Plugins)**: Zawierają funkcje, które aplikacja może wykorzystywać. Są gotowe wtyczki oraz te, które możesz stworzyć samodzielnie. Pokrewną koncepcją są "funkcje promptów" — zamiast dostarczać naturalne wskazówki do wywołania funkcji, publikujesz pewne funkcje dla modelu. Na podstawie aktualnego kontekstu czatu model może wybrać wywołanie jednej z tych funkcji, by zrealizować zapytanie. Oto przykład:

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

    Najpierw masz szablon prompta `skPrompt`, który pozostawia miejsce na wpisanie tekstu przez użytkownika, `$userInput`. Następnie tworzysz funkcję kernela `SummarizeText` i importujesz ją do kernela pod nazwą wtyczki `SemanticFunctions`. Zwróć uwagę na nazwę funkcji, która pomaga Semantic Kernel zrozumieć, co funkcja robi i kiedy powinna zostać wywołana.

- **Funkcje natywne**: Framework może także wywoływać bezpośrednio natywne funkcje realizujące zadanie. Oto przykład takiej funkcji pobierającej zawartość z pliku:

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

- **Pamięć**: Abstrahuje i upraszcza zarządzanie kontekstem dla aplikacji AI. Idea pamięci polega na tym, że LLM powinien mieć o niej wiedzę. Możesz przechowywać te informacje w bazie wektorowej, która staje się bazą danych w pamięci, bazą wektorową lub podobną. Oto przykład uproszczonego scenariusza, gdzie *fakty* są dodawane do pamięci:

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

Te fakty są następnie przechowywane w kolekcji pamięci `SummarizedAzureDocs`. To bardzo uproszczony przykład, ale widać, jak można przechowywać informacje w pamięci, aby LLM mógł ich używać.

To podstawy frameworka Semantic Kernel, a co z Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service to nowszy dodatek, wprowadzony na Microsoft Ignite 2024. Umożliwia rozwijanie i wdrażanie agentów AI z bardziej elastycznymi modelami, takimi jak bezpośrednie wywoływanie otwartych modeli LLM np. Llama 3, Mistral i Cohere.

Azure AI Agent Service zapewnia silniejsze mechanizmy bezpieczeństwa korporacyjnego i metody przechowywania danych, co czyni go odpowiednim do zastosowań przedsiębiorstw.

Działa od razu z ramami orkiestracji wieloagentowej takimi jak AutoGen i Semantic Kernel.

Usługa jest obecnie w wersji Public Preview i wspiera Python oraz C# do budowy agentów.

Za pomocą Semantic Kernel Python możemy stworzyć Azure AI Agenta z wtyczką zdefiniowaną przez użytkownika:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Zdefiniuj przykładowy plugin dla przykładu
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
        # Utwórz definicję agenta
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Utwórz agenta AzureAI używając zdefiniowanego klienta i definicji agenta
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Utwórz wątek, który będzie przechowywał rozmowę
        # Jeśli nie zostanie podany żaden wątek, nowy wątek zostanie
        # utworzony i zwrócony wraz z początkową odpowiedzią
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
                # Wywołaj agenta dla określonego wątku
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

### Podstawowe koncepcje

Azure AI Agent Service ma następujące podstawowe koncepcje:

- **Agent**. Azure AI Agent Service integruje się z Microsoft Foundry. W ramach AI Foundry agent AI działa jak "inteligentna" mikrousługa, która może być używana do odpowiadania na pytania (RAG), wykonywania działań lub całkowitej automatyzacji przepływów pracy. Osiąga to dzięki połączeniu mocy generatywnych modeli AI z narzędziami pozwalającymi mu na dostęp i interakcję z rzeczywistymi źródłami danych. Oto przykład agenta:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    W tym przykładzie agent jest tworzony z modelem `gpt-4o-mini`, nazwą `my-agent` oraz instrukcjami `You are helpful agent`. Agent jest wyposażony w narzędzia i zasoby do wykonywania zadań interpretacji kodu.

- **Wątek i wiadomości**. Wątek to kolejna ważna koncepcja. Reprezentuje rozmowę lub interakcję między agentem a użytkownikiem. Wątki można używać do śledzenia postępu rozmowy, przechowywania informacji kontekstowych oraz zarządzania stanem interakcji. Oto przykład wątku:

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

    W powyższym kodzie tworzony jest wątek. Następnie wysyłana jest wiadomość do wątku. Wywołując `create_and_process_run`, agentowi zleca się wykonanie pracy na wątku. Na koniec pobierane są i zapisywane wiadomości, by zobaczyć odpowiedź agenta. Wiadomości wskazują postęp rozmowy między użytkownikiem a agentem. Istotne jest też to, że wiadomości mogą mieć różne typy, np. tekst, obraz lub plik — wynikiem pracy agenta może być na przykład obraz lub odpowiedź tekstowa. Jako deweloper możesz potem użyć tych informacji do dalszego przetwarzania odpowiedzi lub przedstawienia jej użytkownikowi.

- **Integracja z innymi frameworkami AI**. Azure AI Agent Service może współdziałać z innymi frameworkami, takimi jak AutoGen i Semantic Kernel, co oznacza, że możesz budować część swojej aplikacji w jednym z tych frameworków i np. używać Agent Service jako orkiestratora albo budować wszystko w Agent Service.

**Przypadki użycia**: Azure AI Agent Service jest stworzony dla zastosowań korporacyjnych wymagających bezpiecznego, skalowalnego i elastycznego wdrażania agentów AI.

## Jaka jest różnica między tymi frameworkami?

Brzmi, jakby było wiele nakładających się funkcji między tymi frameworkami, ale istnieją kluczowe różnice pod względem ich projektu, możliwości i docelowych zastosowań:

- **AutoGen**: To framework eksperymentalny skoncentrowany na badaniach wiodących w dziedzinie systemów wieloagentowych. To najlepsze miejsce do eksperymentowania i prototypowania zaawansowanych systemów wieloagentowych.
- **Semantic Kernel**: To gotowa do produkcji biblioteka agentów do budowy korporacyjnych aplikacji agentowych. Skupia się na zdarzeniowych, rozproszonych aplikacjach agentowych, umożliwiając użycie wielu LLM i SLM, narzędzi oraz wzorców projektowych jedno-/wieloagentowych.
- **Azure AI Agent Service**: To platforma i usługa wdrożeniowa w Azure Foundry dla agentów. Oferuje łączenie z usługami wspieranymi przez Azure Foundry, takimi jak Azure OpenAI, Azure AI Search, Bing Search i wykonywanie kodu.

Wciąż nie wiesz, który wybrać?

### Przypadki użycia

Sprawdźmy, czy możemy pomóc, przechodząc przez kilka typowych przypadków użycia:

> Q: Eksperymentuję, uczę się i buduję aplikacje proof-of-concept z agentami i chcę móc szybko budować i eksperymentować
>

>A: AutoGen będzie dobrym wyborem w tym scenariuszu, ponieważ skupia się na zdarzeniowych, rozproszonych aplikacjach agentowych i wspiera zaawansowane wzorce projektowe wieloagentowe.

> Q: Co sprawia, że AutoGen jest lepszym wyborem niż Semantic Kernel i Azure AI Agent Service dla tego przypadku użycia?
>
> A: AutoGen jest specjalnie zaprojektowany dla zdarzeniowych, rozproszonych aplikacji agentowych, co sprawia, że doskonale nadaje się do automatyzacji generacji kodu i analizy danych. Zapewnia niezbędne narzędzia i możliwości do efektywnego budowania złożonych systemów wieloagentowych.

>Q: Brzmi, jakby Azure AI Agent Service też mógł się tu sprawdzić, ma narzędzia do generowania kodu i inne?

>
> A: Tak, Azure AI Agent Service to platformowa usługa dla agentów z wbudowanymi możliwościami dla wielu modeli, Azure AI Search, Bing Search oraz Azure Functions. Ułatwia tworzenie agentów w Foundry Portal i wdrażanie ich na dużą skalę.
 
> Q: Nadal jestem zdezorientowany, podaj mi jedną opcję
>
> A: Dobrym wyborem jest najpierw zbudowanie aplikacji w Semantic Kernel, a następnie użycie Azure AI Agent Service do wdrożenia agenta. Takie podejście pozwala łatwo utrzymywać agentów, jednocześnie korzystając z mocy budowania systemów wieloagentowych w Semantic Kernel. Dodatkowo Semantic Kernel ma konektor w AutoGen, co ułatwia jednoczesne użycie obu frameworków.
 
Podsumujmy kluczowe różnice w tabeli:

| Framework | Skupienie | Podstawowe Koncepcje | Przypadki Użycia |
| --- | --- | --- | --- |
| AutoGen | Zdarzeniowe, rozproszone aplikacje agentowe | Agenci, Persony, Funkcje, Dane | Generowanie kodu, zadania analizy danych |
| Semantic Kernel | Rozumienie i generowanie tekstu podobnego do ludzkiego | Agenci, Komponenty Modularne, Współpraca | Rozumienie języka naturalnego, generowanie treści |
| Azure AI Agent Service | Elastyczne modele, bezpieczeństwo korporacyjne, generowanie kodu, wywoływanie narzędzi | Modularność, Współpraca, Orkiestracja Procesów | Bezpieczne, skalowalne i elastyczne wdrażanie agentów AI |

Jaki jest idealny przypadek użycia dla każdego z tych frameworków?

## Czy mogę bezpośrednio integrować moje istniejące narzędzia ekosystemu Azure, czy potrzebuję rozwiązań autonomicznych?

Odpowiedź brzmi: tak, możesz bezpośrednio integrować swoje istniejące narzędzia ekosystemu Azure szczególnie z Azure AI Agent Service, ponieważ został on stworzony do płynnej współpracy z innymi usługami Azure. Możesz na przykład zintegrować Bing, Azure AI Search i Azure Functions. Istnieje też głęboka integracja z Microsoft Foundry.

W przypadku AutoGen i Semantic Kernel również możesz integrować się z usługami Azure, ale może to wymagać wywoływania tych usług z poziomu twojego kodu. Innym sposobem integracji jest używanie SDK Azure do interakcji z usługami Azure z poziomu twoich agentów. Dodatkowo, jak wspomniano, możesz używać Azure AI Agent Service jako orkiestratora dla agentów zbudowanych w AutoGen lub Semantic Kernel, co zapewni łatwy dostęp do ekosystemu Azure.

## Przykładowe kody

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Masz więcej pytań o AI Agent Frameworks?

Dołącz do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), żeby spotkać innych uczących się, uczestniczyć w godzinach konsultacji i uzyskać odpowiedzi na swoje pytania dotyczące AI Agentów.

## Referencje

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel i AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Użycie Azure AI Agent Service z AutoGen / Semantic Kernel do budowy rozwiązania wieloagentowego</a>

## Poprzednia Lekcja

[Wprowadzenie do AI Agentów i przypadków użycia Agentów](../01-intro-to-ai-agents/README.md)

## Następna Lekcja

[Zrozumienie wzorców projektowych agentowych](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zastrzeżenie**:  
Ten dokument został przetłumaczony przy użyciu automatycznej usługi tłumaczeniowej AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mimo że dokładamy starań, aby tłumaczenie było jak najbardziej precyzyjne, prosimy mieć na uwadze, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku macierzystym należy traktować jako źródło nadrzędne. W przypadku informacji o krytycznym znaczeniu zalecane jest skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z korzystania z tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->