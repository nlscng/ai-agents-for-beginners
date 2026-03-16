[![Wzorzec projektowy planowania](../../../translated_images/pl/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Kliknij obraz powyżej, aby obejrzeć wideo tej lekcji)_

# Projektowanie planu

## Wprowadzenie

Ta lekcja omówi

* Określanie jasnego ogólnego celu i rozbijanie złożonego zadania na wykonalne podzadania.
* Wykorzystanie strukturyzowanego wyniku dla bardziej niezawodnych i maszynowo czytelnych odpowiedzi.
* Stosowanie podejścia opartego na zdarzeniach do obsługi dynamicznych zadań i nieoczekiwanych wejść.

## Cele nauki

Po ukończeniu tej lekcji będziesz rozumieć:

* Określić i ustawić ogólny cel dla agenta AI, zapewniając, że wyraźnie wie, co należy osiągnąć.
* Rozłożyć złożone zadanie na mniejsze podzadania i zorganizować je w logiczną sekwencję.
* Wyposażyć agentów we właściwe narzędzia (np. narzędzia wyszukiwania lub analizy danych), zdecydować kiedy i jak są używane oraz radzić sobie z nieoczekiwanymi sytuacjami, które się pojawiają.
* Ocenić wyniki podzadań, mierzyć wydajność i iterować działania w celu poprawy końcowego rezultatu.

## Określanie ogólnego celu i rozbijanie zadania

![Określanie celów i zadań](../../../translated_images/pl/defining-goals-tasks.d70439e19e37c47a.webp)

Większość zadań w rzeczywistym świecie jest zbyt skomplikowana, aby poradzić sobie z nią w jednym kroku. Agent AI potrzebuje zwięzłego celu, który pokieruje jego planowaniem i działaniami. Na przykład, rozważ cel:

    "Wygeneruj 3-dniowy plan podróży."

Chociaż jest to proste do sformułowania, nadal wymaga doprecyzowania. Im klarowniejszy cel, tym lepiej agent (i ewentualni współpracownicy) mogą skupić się na osiągnięciu właściwego rezultatu, takiego jak stworzenie kompleksowego planu z opcjami lotów, rekomendacjami hoteli i sugestiami aktywności.

### Dekompozycja zadań

Duże lub złożone zadania stają się bardziej zarządzalne, gdy są podzielone na mniejsze, zorientowane na cel podzadania.
Dla przykładu planu podróży można rozłożyć cel na:

* Rezerwacja lotów
* Rezerwacja hotelu
* Wynajem samochodu
* Personalizacja

Każde podzadanie może następnie być obsłużone przez wyspecjalizowanych agentów lub procesy. Jeden agent może specjalizować się w wyszukiwaniu najlepszych ofert lotów, inny koncentruje się na rezerwacjach hotelowych, i tak dalej. Agent koordynujący lub „downstream” może następnie skompilować te wyniki w jeden spójny plan dla użytkownika końcowego.

Takie modularne podejście pozwala również na stopniowe ulepszenia. Na przykład można dodać wyspecjalizowanych agentów odpowiadających za rekomendacje kulinarne lub sugestie lokalnych atrakcji i z czasem dopracowywać plan podróży.

### Strukturyzowany wynik

Large Language Models (LLMs) mogą generować strukturyzowany wynik (np. JSON), który jest łatwiejszy do parsowania i przetwarzania przez agentów lub usługi downstream. Jest to szczególnie przydatne w kontekście wieloagentowym, gdzie po otrzymaniu planu można wykonać kolejne zadania. Odniesienie do szybkiego przeglądu znajdziesz w tym <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">wpisie na blogu</a>.

Następujący fragment Pythona demonstruje prostego agenta planującego rozkładającego cel na podzadania i generującego strukturalny plan:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Model podzadania podróży
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # chcemy przypisać zadanie agentowi

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Aby uwierzytelnić się w modelu, musisz wygenerować osobisty token dostępu (PAT) w ustawieniach GitHub.
    # Utwórz swój token PAT, postępując zgodnie z instrukcjami tutaj: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Zdefiniuj wiadomość użytkownika
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Upewnij się, że zawartość odpowiedzi jest prawidłowym łańcuchem JSON przed jej załadowaniem
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Response content is not a valid JSON string")

# # Wyświetl zawartość odpowiedzi po załadowaniu jej jako JSON
# pprint(json.loads(response_content))

# Zwaliduj zawartość odpowiedzi przy użyciu modelu MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Agent planujący z orkiestracją wieloagentową

W tym przykładzie Agent Router Semantyczny otrzymuje żądanie użytkownika (np. "Potrzebuję planu hotelowego na moją podróż.").

Planner następnie:

* Otrzymuje Plan Hotelowy: Planner przyjmuje wiadomość użytkownika i, na podstawie promptu systemowego (w tym dostępnych szczegółów agentów), generuje strukturalny plan podróży.
* Wymienia Agentów i Ich Narzędzia: Rejestr agentów zawiera listę agentów (np. do lotów, hoteli, wynajmu samochodów i aktywności) wraz z funkcjami lub narzędziami, które oferują.
* Kieruje Plan do Odpowiednich Agentów: W zależności od liczby podzadań, planner albo wysyła wiadomość bezpośrednio do dedykowanego agenta (w scenariuszach jednego zadania), albo koordynuje poprzez menedżera czatu grupowego w przypadku współpracy wieloagentowej.
* Podsumowuje Wynik: Na koniec planner podsumowuje wygenerowany plan dla jasności.
Poniższy przykład kodu w Pythonie ilustruje te kroki:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Model podzadania podróży

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # chcemy przypisać zadanie agentowi

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Utwórz klienta z użyciem zmiennych środowiskowych sprawdzonych pod kątem typów

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Zdefiniuj wiadomość użytkownika

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Upewnij się, że zawartość odpowiedzi jest prawidłowym łańcuchem JSON przed jej załadowaniem

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Wypisz zawartość odpowiedzi po załadowaniu jej jako JSON

pprint(json.loads(response_content))
```

Co następuje, to wynik z poprzedniego kodu i możesz następnie użyć tego strukturyzowanego wyniku, aby skierować do `assigned_agent` i podsumować plan podróży dla użytkownika końcowego.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Przykładowy notebook z powyższym przykładem kodu jest dostępny [tutaj](07-autogen.ipynb).

### Planowanie iteracyjne

Niektóre zadania wymagają wymiany informacji tam i z powrotem lub ponownego planowania, gdzie wynik jednego podzadania wpływa na następne. Na przykład, jeśli agent odkryje nieoczekiwany format danych podczas rezerwacji lotów, może potrzebować dostosować swoją strategię przed przejściem do rezerwacji hoteli.

Dodatkowo, opinia użytkownika (np. gdy człowiek zdecyduje, że woli wcześniejszy lot) może wywołać częściowe ponowne zaplanowanie. Takie dynamiczne, iteracyjne podejście zapewnia, że końcowe rozwiązanie jest zgodne z ograniczeniami rzeczywistego świata i ewoluującymi preferencjami użytkownika.

np. przykładowy kod

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. tak samo jak poprzedni kod i przekaż historię użytkownika oraz bieżący plan
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. przeplanuj i wyślij zadania do odpowiednich agentów
```

Dla bardziej kompleksowego planowania sprawdź Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Wpis na blogu</a> dotyczący rozwiązywania złożonych zadań.

## Podsumowanie

W tym artykule przyjrzeliśmy się przykładowi, jak możemy stworzyć planner, który dynamicznie wybiera dostępnych zdefiniowanych agentów. Wynik Plannera dekomponuje zadania i przypisuje agentów, aby mogły zostać wykonane. Zakłada się, że agenci mają dostęp do funkcji/narzędzi wymaganych do realizacji zadania. Oprócz agentów można włączyć inne wzorce, takie jak refleksja, podsumowywacz i czat round robin, aby dodatkowo dostosować działanie.

## Dodatkowe zasoby

AutoGen Magentic One - A Generalist multi-agent system for solving complex tasks and has achieved impressive results on multiple challenging agentic benchmarks. Odniesienie: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. W tej implementacji orkiestrator tworzy specyficzny dla zadania plan i deleguje te zadania dostępnym agentom. Oprócz planowania orkiestrator stosuje również mechanizm śledzenia, aby monitorować postęp zadania i w razie potrzeby ponownie planować.

### Masz więcej pytań dotyczących wzorca projektowania planowania?

Dołącz do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), aby spotkać się z innymi uczącymi się, uczestniczyć w godzinach konsultacji i uzyskać odpowiedzi na pytania dotyczące Twoich agentów AI.

## Poprzednia lekcja

[Budowanie godnych zaufania agentów AI](../06-building-trustworthy-agents/README.md)

## Następna lekcja

[Wzorzec wieloagentowy](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zastrzeżenie**:
Niniejszy dokument został przetłumaczony przy użyciu usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Chociaż dążymy do dokładności, prosimy pamiętać, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku źródłowym należy uznać za źródło nadrzędne. W przypadku informacji o krytycznym znaczeniu zaleca się skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za żadne nieporozumienia lub błędne interpretacje wynikające z korzystania z tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->