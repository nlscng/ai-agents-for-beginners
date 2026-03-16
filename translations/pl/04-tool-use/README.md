[![Jak zaprojektować dobre agenty AI](../../../translated_images/pl/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Kliknij powyższy obraz, aby obejrzeć wideo z tej lekcji)_

# Wzorzec użycia narzędzi

Narzędzia są interesujące, ponieważ pozwalają agentom AI mieć szerszy zakres możliwości. Zamiast ograniczonego zestawu działań, które agent może wykonać, dodanie narzędzia umożliwia agentowi wykonywanie znacznie szerszego zakresu operacji. W tym rozdziale przyjrzymy się Wzorcu użycia narzędzi (Tool Use Design Pattern), który opisuje, jak agenci AI mogą używać konkretnych narzędzi do osiągania swoich celów.

## Wprowadzenie

W tej lekcji chcemy odpowiedzieć na następujące pytania:

- Czym jest wzorzec użycia narzędzi?
- Do jakich przypadków użycia można go zastosować?
- Jakie elementy/bloki budulcowe są potrzebne do wdrożenia wzorca?
- Jakie są specjalne rozważania związane z użyciem Wzorca użycia narzędzi przy budowie godnych zaufania agentów AI?

## Cele nauki

Po ukończeniu tej lekcji będziesz w stanie:

- Zdefiniować Wzorzec użycia narzędzi i jego cel.
- Zidentyfikować przypadki użycia, w których Wzorzec użycia narzędzi ma zastosowanie.
- Zrozumieć kluczowe elementy potrzebne do wdrożenia wzorca.
- Rozpoznać kwestie związane z zapewnieniem godności zaufania agentów AI wykorzystujących ten wzorzec.

## Czym jest Wzorzec użycia narzędzi?

Wzorzec użycia narzędzi koncentruje się na nadaniu LLM możliwości interakcji z zewnętrznymi narzędziami w celu osiągania konkretnych celów. Narzędzia to fragmenty kodu, które mogą być wykonywane przez agenta w celu wykonania działań. Narzędzie może być prostą funkcją, taką jak kalkulator, lub wywołaniem API do usługi zewnętrznej, takiej jak wyszukiwanie cen akcji czy prognoza pogody. W kontekście agentów AI, narzędzia są projektowane tak, aby mogły być wykonywane przez agentów w odpowiedzi na wywołania funkcji generowane przez model (model-generated function calls).

## Do jakich przypadków użycia można go zastosować?

Agenci AI mogą wykorzystywać narzędzia do realizacji złożonych zadań, pobierania informacji lub podejmowania decyzji. Wzorzec użycia narzędzi jest często stosowany w scenariuszach wymagających dynamicznej interakcji z zewnętrznymi systemami, takimi jak bazy danych, usługi sieciowe czy interpretery kodu. Ta zdolność jest przydatna w wielu różnych przypadkach użycia, w tym:

- Dynamiczne pobieranie informacji: Agenci mogą zapytaniać zewnętrzne API lub bazy danych, aby pobrać aktualne dane (np. zapytania do bazy SQLite w analizie danych, pobieranie cen akcji lub informacji o pogodzie).
- Wykonywanie i interpretacja kodu: Agenci mogą wykonywać kod lub skrypty, aby rozwiązywać problemy matematyczne, generować raporty lub przeprowadzać symulacje.
- Automatyzacja przepływów pracy: Automatyzacja powtarzalnych lub wieloetapowych przepływów pracy przez integrację narzędzi takich jak harmonogramy zadań, usługi e-mail czy potoki danych.
- Obsługa klienta: Agenci mogą integrować się z systemami CRM, platformami zgłoszeń lub bazami wiedzy, aby rozwiązywać zapytania użytkowników.
- Generowanie i edycja treści: Agenci mogą wykorzystywać narzędzia takie jak korektory gramatyczne, streszczacze tekstu czy oceniacze bezpieczeństwa treści, aby wspierać zadania związane z tworzeniem treści.

## Jakie elementy/bloki budulcowe są potrzebne do wdrożenia wzorca użycia narzędzi?

Te bloki budulcowe pozwalają agentowi AI wykonywać szeroki zakres zadań. Przyjrzyjmy się kluczowym elementom potrzebnym do wdrożenia Wzorca użycia narzędzi:

- Schematy funkcji/narzędzi: Szczegółowe definicje dostępnych narzędzi, w tym nazwa funkcji, cel, wymagane parametry i oczekiwane wyniki. Te schematy umożliwiają LLM zrozumienie, jakie narzędzia są dostępne i jak skonstruować poprawne żądania.

- Logika wykonywania funkcji: Reguluje, jak i kiedy narzędzia są wywoływane w oparciu o intencje użytkownika i kontekst rozmowy. Może to obejmować moduły planujące, mechanizmy routingu lub warunkowe przepływy, które dynamicznie decydują o użyciu narzędzi.

- System obsługi komunikatów: Komponenty zarządzające przepływem konwersacji między wejściami użytkownika, odpowiedziami LLM, wywołaniami narzędzi i wynikami narzędzi.

- Ramy integracji narzędzi: Infrastruktura łącząca agenta z różnymi narzędziami, zarówno prostymi funkcjami, jak i złożonymi usługami zewnętrznymi.

- Obsługa błędów i walidacja: Mechanizmy obsługi awarii w wykonaniu narzędzi, walidacji parametrów i zarządzania nieoczekiwanymi odpowiedziami.

- Zarządzanie stanem: Śledzi kontekst rozmowy, wcześniejsze interakcje z narzędziami i dane trwałe, aby zapewnić spójność w wieloetapowych interakcjach.

Następnie przyjrzyjmy się wywoływaniu funkcji/narzędzi bardziej szczegółowo.
 
### Wywoływanie funkcji/narzędzi

Wywoływanie funkcji jest podstawowym sposobem umożliwiającym Wielkim Modelom Językowym (LLMs) interakcję z narzędziami. Często zobaczysz, że 'Function' i 'Tool' są używane zamiennie, ponieważ 'funkcje' (bloki wielokrotnego użytku kodu) są 'narzędziami', których agenci używają do realizacji zadań. Aby kod funkcji został wywołany, LLM musi porównać żądanie użytkownika z opisami funkcji. W tym celu do modelu wysyłany jest schemat zawierający opisy wszystkich dostępnych funkcji. LLM następnie wybiera najbardziej odpowiednią funkcję do zadania i zwraca jej nazwę oraz argumenty. Wybrana funkcja jest wywoływana, jej odpowiedź jest wysyłana z powrotem do LLM, który wykorzystuje te informacje do udzielenia odpowiedzi na żądanie użytkownika.

Aby deweloperzy mogli zaimplementować wywoływanie funkcji dla agentów, będą potrzebować:

1. Modelu LLM, który obsługuje wywoływanie funkcji
2. Schematu zawierającego opisy funkcji
3. Kodu dla każdej opisanej funkcji

Użyjmy przykładu uzyskania aktualnego czasu w mieście, aby zilustrować:

1. Inicjalizacja LLM, który obsługuje wywoływanie funkcji:

    Nie wszystkie modele obsługują wywoływanie funkcji, więc ważne jest, aby sprawdzić, czy używany model to wspiera.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> obsługuje wywoływanie funkcji. Możemy zacząć od zainicjowania klienta Azure OpenAI. 

    ```python
    # Zainicjalizuj klienta Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. Utworzenie schematu funkcji:

    Następnie zdefiniujemy schemat JSON, który zawiera nazwę funkcji, opis tego, co funkcja robi, oraz nazwy i opisy parametrów funkcji.
    Następnie prześlemy ten schemat do wcześniej utworzonego klienta, wraz z żądaniem użytkownika, aby znaleźć czas w San Francisco. Ważne jest, aby zauważyć, że to, co jest zwracane, to **wywołanie narzędzia**, **a nie** końcowa odpowiedź na pytanie. Jak wspomniano wcześniej, LLM zwraca nazwę wybranej funkcji do zadania oraz argumenty, które zostaną jej przekazane.

    ```python
    # Opis funkcji do odczytania przez model
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # Wstępna wiadomość użytkownika
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Pierwsze wywołanie API: Poproś model, aby użył funkcji
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Przetwórz odpowiedź modelu
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. Kod funkcji potrzebny do wykonania zadania:

    Teraz, gdy LLM wybrał, która funkcja musi zostać uruchomiona, kod realizujący zadanie musi zostać zaimplementowany i wykonany.
    Możemy zaimplementować kod pobierający aktualny czas w Pythonie. Będziemy także musieli napisać kod, aby wyodrębnić nazwę i argumenty z response_message, aby uzyskać ostateczny wynik.

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # Obsłuż wywołania funkcji
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # Drugie wywołanie API: Pobierz ostateczną odpowiedź od modelu
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

Wywoływanie funkcji jest w centrum większości, jeśli nie wszystkich, rozwiązań projektowych użycia narzędzi przez agentów, jednak implementacja go od podstaw bywa czasami wyzwaniem.
Jak dowiedzieliśmy się w [Lekcji 2](../../../02-explore-agentic-frameworks) frameworki agentowe dostarczają nam gotowe bloki budulcowe do implementacji użycia narzędzi.
 
## Przykłady użycia narzędzi z frameworkami agentowymi

Oto kilka przykładów, jak można zaimplementować Wzorzec użycia narzędzi, korzystając z różnych frameworków agentowych:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> jest otwartoźródłowym frameworkiem AI dla deweloperów .NET, Python i Java pracujących z Wielkimi Modelami Językowymi (LLMs). Upraszcza proces używania wywołań funkcji, automatycznie opisując twoje funkcje i ich parametry modelowi poprzez proces zwany <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializowaniem</a>. Obsługuje również komunikację w obie strony między modelem a twoim kodem. Kolejną zaletą używania frameworka agentowego takiego jak Semantic Kernel jest to, że pozwala on na dostęp do gotowych narzędzi, takich jak <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> i <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Poniższy diagram ilustruje proces wywoływania funkcji z Semantic Kernel:

![wywoływanie funkcji](../../../translated_images/pl/functioncalling-diagram.a84006fc287f6014.webp)

W Semantic Kernel funkcje/narzędzia nazywane są <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. Możemy przekształcić funkcję `get_current_time`, którą widzieliśmy wcześniej, w plugin, zamieniając ją w klasę z tą funkcją wewnątrz. Możemy również zaimportować dekorator `kernel_function`, który przyjmuje opis funkcji. Kiedy utworzysz kernel z GetCurrentTimePlugin, kernel automatycznie zserializuje funkcję i jej parametry, tworząc w procesie schemat do wysłania do LLM.

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# Utwórz rdzeń
kernel = Kernel()

# Utwórz wtyczkę
get_current_time_plugin = GetCurrentTimePlugin(location)

# Dodaj wtyczkę do rdzenia
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> to nowszy framework agentowy zaprojektowany, aby umożliwić deweloperom bezpieczne budowanie, wdrażanie i skalowanie wysokiej jakości, rozszerzalnych agentów AI bez konieczności zarządzania zasobami obliczeniowymi i pamięcią masową. Jest szczególnie przydatny w zastosowaniach korporacyjnych, ponieważ jest to w pełni zarządzana usługa z ochroną klasy enterprise.

W porównaniu z opracowywaniem przy użyciu bezpośredniego API LLM, Azure AI Agent Service oferuje pewne zalety, w tym:

- Automatyczne wywoływanie narzędzi – brak potrzeby parsowania wywołania narzędzia, wywoływania narzędzia i obsługi odpowiedzi; wszystko to jest teraz wykonywane po stronie serwera
- Bezpiecznie zarządzane dane – zamiast zarządzać własnym stanem konwersacji, możesz polegać na threads, które przechowują wszystkie potrzebne informacje
- Gotowe narzędzia – narzędzia, które można wykorzystać do interakcji ze źródłami danych, takimi jak Bing, Azure AI Search i Azure Functions.

Narzędzia dostępne w Azure AI Agent Service można podzielić na dwie kategorie:

1. Narzędzia wiedzy:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Narzędzia akcji:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service pozwala używać tych narzędzi razem jako `toolset`. Wykorzystuje on również `threads`, które śledzą historię wiadomości z danej rozmowy.

Wyobraź sobie, że jesteś agentem sprzedaży w firmie o nazwie Contoso. Chcesz opracować agenta konwersacyjnego, który potrafi odpowiadać na pytania dotyczące twoich danych sprzedażowych.

Poniższy obraz ilustruje, jak możesz użyć Azure AI Agent Service do analizy danych sprzedażowych:

![Agentic Service In Action](../../../translated_images/pl/agent-service-in-action.34fb465c9a84659e.webp)

Aby użyć któregokolwiek z tych narzędzi z usługą, możemy utworzyć klienta i zdefiniować narzędzie lub zestaw narzędzi. Aby praktycznie to zaimplementować, możemy użyć następującego kodu w Pythonie. LLM będzie mógł spojrzeć na toolset i zdecydować, czy użyć funkcji stworzonej przez użytkownika `fetch_sales_data_using_sqlite_query`, czy wbudowanego Code Interpreter, w zależności od żądania użytkownika.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # funkcja fetch_sales_data_using_sqlite_query, którą można znaleźć w pliku fetch_sales_data_functions.py
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Zainicjalizuj zestaw narzędzi
toolset = ToolSet()

# Zainicjalizuj agenta, który wywołuje funkcję fetch_sales_data_using_sqlite_query, i dodaj go do zestawu narzędzi
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Zainicjalizuj narzędzie Code Interpreter i dodaj je do zestawu narzędzi
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Jakie są specjalne rozważania związane z użyciem Wzorca użycia narzędzi przy budowie godnych zaufania agentów AI?

Powszechne obawy dotyczące dynamicznie generowanego SQL przez LLM odnoszą się do bezpieczeństwa, szczególnie ryzyka wstrzyknięcia SQL (SQL injection) lub złośliwych działań, takich jak usuwanie czy manipulowanie bazą danych. Chociaż te obawy są uzasadnione, można je skutecznie złagodzić poprzez właściwą konfigurację uprawnień dostępu do bazy danych. W przypadku większości baz danych oznacza to skonfigurowanie bazy jako tylko do odczytu. Dla usług bazodanowych, takich jak PostgreSQL czy Azure SQL, aplikacji powinno się przypisać rolę tylko do odczytu (SELECT).

Uruchamianie aplikacji w bezpiecznym środowisku dodatkowo zwiększa ochronę. W scenariuszach korporacyjnych dane są zazwyczaj ekstraktowane i transformowane z systemów operacyjnych do bazy danych tylko do odczytu lub hurtowni danych o przyjaznym schemacie. Podejście to zapewnia, że dane są bezpieczne, zoptymalizowane pod kątem wydajności i dostępności oraz że aplikacja ma ograniczony dostęp tylko do odczytu.

## Przykładowe kody
- Python: [Framework agenta](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Framework agenta](./code_samples/04-dotnet-agent-framework.md)

## Masz więcej pytań dotyczących wzorców projektowych użycia narzędzi?

Dołącz do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), aby spotkać się z innymi uczestnikami, wziąć udział w godzinach konsultacji i uzyskać odpowiedzi na pytania dotyczące AI Agents.

## Dodatkowe zasoby

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Warsztat usługi Azure AI Agents</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Wieloagentowy warsztat Contoso Creative Writer</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Samouczek wywoływania funkcji w Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Interpreter kodu Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Narzędzia Autogen</a>

## Poprzednia lekcja

[Zrozumienie agentowych wzorców projektowych](../03-agentic-design-patterns/README.md)

## Następna lekcja

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Wyłączenie odpowiedzialności**:
Niniejszy dokument został przetłumaczony przy użyciu usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Chociaż dokładamy starań o poprawność, prosimy pamiętać, że tłumaczenia automatyczne mogą zawierać błędy lub nieścisłości. Oryginalny dokument w jego języku źródłowym powinien być uznawany za wersję wiążącą. W przypadku informacji o znaczeniu krytycznym zalecane jest skorzystanie z usług profesjonalnego tłumacza. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z korzystania z tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->