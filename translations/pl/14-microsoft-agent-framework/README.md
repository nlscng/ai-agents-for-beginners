# Poznawanie Microsoft Agent Framework

![Microsoft Agent Framework](../../../translated_images/pl/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Wprowadzenie

Ta lekcja obejmie:

- Zrozumienie Microsoft Agent Framework: Kluczowe funkcje i wartość  
- Przegląd kluczowych koncepcji Microsoft Agent Framework
- Porównanie MAF z Semantic Kernel i AutoGen: Przewodnik migracji

## Cele nauki

Po ukończeniu tej lekcji będziesz potrafił:

- Tworzyć gotowe do produkcji agentów AI przy użyciu Microsoft Agent Framework
- Zastosować podstawowe funkcje Microsoft Agent Framework w swoich przypadkach użycia agentów
- Migrować i integrować istniejące frameworki i narzędzia agentowe  

## Przykłady kodu

Przykłady kodu dla [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) można znaleźć w tym repozytorium w plikach `xx-python-agent-framework` i `xx-dotnet-agent-framework`.

## Zrozumienie Microsoft Agent Framework

![Wprowadzenie do frameworka](../../../translated_images/pl/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) opiera się na doświadczeniach i naukach z Semantic Kernel i AutoGen. Oferuje elastyczność umożliwiającą obsługę szerokiej gamy przypadków użycia agentów spotykanych zarówno w produkcji, jak i badaniach, w tym:

- **Sekwencyjna orkiestracja agentów** w scenariuszach wymagających krok po kroku przepływów pracy.
- **Równoległa orkiestracja** w scenariuszach, w których agenci muszą wykonywać zadania jednocześnie.
- **Orkiestracja rozmów grupowych** w scenariuszach, w których agenci mogą współpracować nad jednym zadaniem.
- **Orkiestracja przekazania** w scenariuszach, w których agenci przekazują zadanie sobie nawzajem, gdy podzadania są ukończone.
- **Orkiestracja magnetyczna** w scenariuszach, w których agent menedżer tworzy i modyfikuje listę zadań oraz koordynuje podagentów w celu wykonania zadania.

Aby dostarczać agentów AI w produkcji, MAF obejmuje również funkcje dla:

- **Obserwowalności** poprzez użycie OpenTelemetry, gdzie każda akcja agenta AI, w tym wywołanie narzędzia, kroki orkiestracji, przepływy rozumowania oraz monitorowanie wydajności są dostępne poprzez pulpity Microsoft Foundry.
- **Bezpieczeństwa** dzięki natywnemu hostowaniu agentów na Microsoft Foundry, które obejmuje kontrolę zabezpieczeń taką jak dostęp oparty na rolach, obsługa danych prywatnych i wbudowane bezpieczeństwo treści.
- **Trwałości** ponieważ wątki i przepływy pracy agentów mogą być wstrzymywane, wznawiane i odzyskiwane po błędach, co umożliwia dłużej trwające procesy.
- **Kontroli** poprzez wsparcie przepływów pracy z udziałem człowieka, gdzie zadania mogą być oznaczone jako wymagające zatwierdzenia przez człowieka.

Microsoft Agent Framework koncentruje się również na interoperacyjności poprzez:

- **Niezależność od chmury** - Agenci mogą działać w kontenerach, lokalnie oraz w różnych chmurach.
- **Niezależność od dostawcy** - Agenci mogą być tworzeni za pomocą preferowanego SDK, w tym Azure OpenAI i OpenAI
- **Integrację otwartych standardów** - Agenci mogą wykorzystywać protokoły takie jak Agent-to-Agent (A2A) i Model Context Protocol (MCP) do odkrywania i używania innych agentów oraz narzędzi.
- **Wtyczki i konektory** - Możliwe są połączenia do usług danych i pamięci, takich jak Microsoft Fabric, SharePoint, Pinecone i Qdrant.

Spójrzmy, jak te funkcje są stosowane w niektórych kluczowych koncepcjach Microsoft Agent Framework.

## Kluczowe koncepcje Microsoft Agent Framework

### Agenci

![Komponenty agenta](../../../translated_images/pl/agent-components.410a06daf87b4fef.webp)

**Tworzenie agentów**

Tworzenie agenta odbywa się poprzez zdefiniowanie usługi inferencyjnej (dostawcy LLM), zestawu instrukcji dla agenta AI do wykonania oraz przypisanego `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Powyżej użyto `Azure OpenAI`, ale agenci mogą być tworzeni za pomocą różnych usług, w tym `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

lub agentów zdalnych korzystających z protokołu A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Uruchamianie agentów**

Agenci są uruchamiani za pomocą metod `.run` lub `.run_stream` dla odpowiednio odpowiedzi nie-strumieniowych lub strumieniowych.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Każde uruchomienie agenta może również mieć opcje do dostosowania parametrów takich jak `max_tokens` używane przez agenta, `tools`, które agent może wywołać, a nawet sam `model` używany przez agenta.

Jest to przydatne w przypadkach, gdy do wykonania zadania użytkownika wymagane są konkretne modele lub narzędzia.

**Narzędzia**

Narzędzia mogą być definiowane zarówno przy definiowaniu agenta:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Tworząc ChatAgent bezpośrednio

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

jak i podczas uruchamiania agenta:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Narzędzie dostarczone tylko na to uruchomienie )
```

**Wątki agenta**

Wątki agenta służą do obsługi konwersacji wieloturnowych. Wątki można tworzyć poprzez:

- Użycie `get_new_thread()`, co umożliwia zapisanie wątku w czasie
- Tworzenie wątku automatycznie podczas uruchamiania agenta, gdzie wątek istnieje tylko podczas bieżącego uruchomienia.

Aby utworzyć wątek, kod wygląda następująco:

```python
# Utwórz nowy wątek.
thread = agent.get_new_thread() # Uruchom agenta z tym wątkiem.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Następnie możesz zserializować wątek, aby przechować go do późniejszego użycia:

```python
# Utwórz nowy wątek.
thread = agent.get_new_thread() 

# Uruchom agenta z wątkiem.

response = await agent.run("Hello, how are you?", thread=thread) 

# Zserializuj wątek do przechowywania.

serialized_thread = await thread.serialize() 

# Zdeserializuj stan wątku po wczytaniu z pamięci.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware agenta**

Agenci współdziałają z narzędziami i LLM, aby wykonać zadania użytkownika. W niektórych scenariuszach chcemy wykonywać lub śledzić działania między tymi interakcjami. Middleware agenta umożliwia nam to poprzez:

*Middleware funkcji*

To middleware pozwala na wykonanie akcji pomiędzy agentem a funkcją/narzędziem, które będzie wywoływane. Przykładem użycia jest chęć zalogowania wywołania funkcji.

W poniższym kodzie `next` określa, czy powinno być wywołane kolejne middleware, czy faktyczna funkcja.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Przetwarzanie wstępne: Zapisz w logu przed wykonaniem funkcji
    print(f"[Function] Calling {context.function.name}")

    # Kontynuuj do następnego middleware lub wykonania funkcji
    await next(context)

    # Przetwarzanie końcowe: Zapisz w logu po wykonaniu funkcji
    print(f"[Function] {context.function.name} completed")
```

*Middleware czatu*

To middleware pozwala na wykonanie lub zalogowanie akcji pomiędzy agentem a żądaniami wysyłanymi do LLM.

Zawiera to istotne informacje takie jak `messages`, które są wysyłane do usługi AI.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Wstępne przetwarzanie: Zaloguj przed wywołaniem AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Kontynuuj do kolejnego middleware lub usługi AI
    await next(context)

    # Końcowe przetwarzanie: Zaloguj po otrzymaniu odpowiedzi AI
    print("[Chat] AI response received")

```

**Pamięć agenta**

Jak omówiono w lekcji `Agentic Memory`, pamięć jest ważnym elementem pozwalającym agentowi działać w różnych kontekstach. MAF oferuje kilka różnych typów pamięci:

*Pamięć w pamięci*

Jest to pamięć przechowywana we wątkach podczas działania aplikacji.

```python
# Utwórz nowy wątek.
thread = agent.get_new_thread() # Uruchom agenta przy użyciu wątku.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Wiadomości trwałe*

Ta pamięć jest używana przy przechowywaniu historii konwersacji w różnych sesjach. Jest definiowana za pomocą `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Utwórz niestandardowy magazyn wiadomości
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Pamięć dynamiczna*

Ta pamięć jest dodawana do kontekstu przed uruchomieniem agentów. Pamięci te mogą być przechowywane w zewnętrznych usługach takich jak mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Korzystanie z Mem0 w celu uzyskania zaawansowanych możliwości pamięciowych
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**Obserwowalność agenta**

Obserwowalność jest istotna dla budowy niezawodnych i łatwych w utrzymaniu systemów agentowych. MAF integruje się z OpenTelemetry, aby zapewnić śledzenie i metryki dla lepszej obserwowalności.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # zrób coś
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Przepływy pracy

MAF oferuje przepływy pracy, które są zdefiniowanymi krokami do wykonania zadania i zawierają agentów AI jako komponenty w tych krokach.

Przepływy pracy składają się z różnych komponentów umożliwiających lepszą kontrolę przepływu. Przepływy pracy umożliwiają również **orkiestrację wieloagentową** i **tworzenie punktów kontrolnych** w celu zapisywania stanów przepływu pracy.

Podstawowe komponenty przepływu pracy to:

**Wykonawcy**

Wykonawcy otrzymują wiadomości wejściowe, wykonują przypisane zadania, a następnie generują wiadomość wyjściową. To przesuwa przepływ pracy naprzód w kierunku ukończenia większego zadania. Wykonawcy mogą być agentami AI lub niestandardową logiką.

**Krawędzie**

Krawędzie służą do definiowania przepływu wiadomości w przepływie pracy. Mogą to być:

*Krawędzie bezpośrednie* - Proste połączenia jeden-do-jednego między wykonawcami:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Krawędzie warunkowe* - Aktywowane po spełnieniu określonego warunku. Na przykład, gdy pokoje hotelowe są niedostępne, wykonawca może zasugerować inne opcje.

*Krawędzie typu switch-case* - Kierują wiadomości do różnych wykonawców na podstawie zdefiniowanych warunków. Na przykład, jeśli klient podróżniczy ma priorytetowy dostęp, jego zadania będą obsługiwane przez inny przepływ pracy.

*Krawędzie fan-out* - Wysyłają jedną wiadomość do wielu celów.

*Krawędzie fan-in* - Zbierają wiele wiadomości od różnych wykonawców i wysyłają je do jednego celu.

**Zdarzenia**

Aby zapewnić lepszą obserwowalność przepływów pracy, MAF oferuje wbudowane zdarzenia dla wykonania, w tym:

- `WorkflowStartedEvent`  - Rozpoczęcie wykonania przepływu pracy
- `WorkflowOutputEvent` - Przepływ pracy wygenerował wyjście
- `WorkflowErrorEvent` - Przepływ pracy napotkał błąd
- `ExecutorInvokeEvent`  - Wykonawca rozpoczyna przetwarzanie
- `ExecutorCompleteEvent`  -  Wykonawca kończy przetwarzanie
- `RequestInfoEvent` - Złożono żądanie

## Migracja z innych frameworków (Semantic Kernel i AutoGen)

### Różnice między MAF a Semantic Kernel

**Uproszczone tworzenie agentów**

Semantic Kernel polega na tworzeniu instancji Kernel dla każdego agenta. MAF stosuje uproszczone podejście, używając rozszerzeń dla głównych dostawców.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Tworzenie wątków agenta**

Semantic Kernel wymaga ręcznego tworzenia wątków. W MAF agent jest bezpośrednio przypisany do wątku.

```python
thread = agent.get_new_thread() # Uruchom agenta w wątku.
```

**Rejestracja narzędzi**

W Semantic Kernel narzędzia są rejestrowane w Kernel, a Kernel jest następnie przekazywany do agenta. W MAF narzędzia są rejestrowane bezpośrednio podczas procesu tworzenia agenta.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Różnice między MAF a AutoGen

**Teams vs Workflows**

`Teams` to struktura zdarzeń dla aktywności zdarzeniowych z agentami w AutoGen. MAF używa `Workflows`, które kierują dane do wykonawców poprzez architekturę opartą na grafie.

**Tworzenie narzędzi**

AutoGen używa `FunctionTool` do opakowywania funkcji wywoływanych przez agentów. MAF używa @ai_function, która działa podobnie, ale także automatycznie wnioskuje schematy dla każdej funkcji.

**Zachowanie agenta**

Agenci w AutoGen są domyślnie jednoetapowi (single-turn), chyba że `max_tool_iterations` jest ustawione na większą wartość. W MAF `ChatAgent` jest domyślnie wieloturnowy, co oznacza, że będzie wywoływać narzędzia aż do ukończenia zadania użytkownika.

## Przykłady kodu

Przykłady kodu dla Microsoft Agent Framework można znaleźć w tym repozytorium w plikach `xx-python-agent-framework` i `xx-dotnet-agent-framework`.

## Masz więcej pytań dotyczących Microsoft Agent Framework?

Dołącz do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) aby spotkać innych uczestników, wziąć udział w godzinach konsultacji i uzyskać odpowiedzi na pytania dotyczące twoich agentów AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Zastrzeżenie:
Niniejszy dokument został przetłumaczony przy użyciu usługi tłumaczeń AI [Co-op Translator](https://github.com/Azure/co-op-translator). Chociaż dążymy do zachowania dokładności, prosimy pamiętać, że tłumaczenia automatyczne mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku źródłowym należy traktować jako źródło wiążące. W przypadku informacji krytycznych zaleca się skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za żadne nieporozumienia ani błędne interpretacje wynikające z korzystania z tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->