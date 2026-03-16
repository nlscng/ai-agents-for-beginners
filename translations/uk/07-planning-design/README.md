[![Патерн планування](../../../translated_images/uk/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Натисніть на зображення вище, щоб переглянути відео цього уроку)_

# Планування дизайну

## Вступ

Цей урок охоплює

* Визначення чіткої загальної мети та розбиття складного завдання на керовані підзадачі.
* Використання структурованого виводу для більш надійних і машинозчитуваних відповідей.
* Застосування подійно-орієнтованого підходу для обробки динамічних завдань і непередбачених вхідних даних.

## Цілі навчання

Після завершення цього уроку ви зрозумієте:

* Визначати та встановлювати загальну мету для AI-агента, забезпечуючи, щоб він чітко знав, що потрібно досягти.
* Розбивати складне завдання на керовані підзадачі та організовувати їх у логічну послідовність.
* Оснащувати агентів відповідними інструментами (наприклад, засобами пошуку або інструментами аналітики даних), вирішувати, коли і як їх використовувати, а також обробляти непередбачені ситуації.
* Оцінювати результати підзадач, вимірювати продуктивність і ітерувати дії для покращення остаточного результату.

## Визначення загальної мети та розбивка завдання

![Визначення цілей і завдань](../../../translated_images/uk/defining-goals-tasks.d70439e19e37c47a.webp)

Більшість реальних завдань занадто складні, щоб вирішити їх за один крок. AI-агенту потрібна коротка мета, яка спрямовуватиме його планування та дії. Наприклад, розглянемо мету:

    "Згенерувати 3-денний маршрут подорожі."

Хоча це просто сформулювати, вона все одно потребує уточнення. Чим ясніша мета, тим краще агент (та будь-які людські співпрацівники) може зосередитися на досягненні правильного результату, наприклад створенні повного маршруту з варіантами перельотів, рекомендаціями щодо готелів і пропозиціями активностей.

### Декомпозиція завдання

Великі або складні завдання стають більш керованими, коли їх розділити на менші, орієнтовані на мету підзадачі.
Для прикладу маршруту подорожі можна розбити мету на:

* Бронювання перельоту
* Бронювання готелю
* Оренда автомобіля
* Персоналізація

Кожною підзадачею потім можна займатися за допомогою спеціалізованих агентів або процесів. Один агент може спеціалізуватися на пошуку кращих пропозицій на перельоти, інший — зосереджуватися на бронюванні готелів і так далі. Координуючий або «низхідний» агент може звести ці результати в один цілісний маршрут для кінцевого користувача.

Такий модульний підхід також дозволяє поступові вдосконалення. Наприклад, ви можете додати спеціалізованих агентів для рекомендацій щодо їжі або пропозицій місцевих активностей і поступово вдосконалювати маршрут.

### Структурований вивід

Великі мовні моделі (LLMs) можуть генерувати структурований вивід (наприклад, JSON), який легше парсити та обробляти подальнім агентам або сервісам. Це особливо корисно в мультиагентному контексті, де ми можемо виконувати ці завдання після отримання плану. Зверніться до цієї <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">публікації в блозі</a> для короткого огляду.

Наведений нижче фрагмент Python демонструє простого агента планування, який розбиває мету на підзадачі та генерує структурований план:

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

# Модель підзадачі подорожі
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # ми хочемо призначити завдання агенту

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Щоб автентифікуватися в моделі, вам потрібно згенерувати персональний токен доступу (PAT) у налаштуваннях GitHub.
    # Створіть свій PAT, дотримуючись інструкцій тут: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Визначте повідомлення користувача
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

# # Переконайтеся, що вміст відповіді є дійсним JSON-рядком перед завантаженням
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Response content is not a valid JSON string")

# # Виведіть вміст відповіді після завантаження його як JSON
# pprint(json.loads(response_content))

# Перевірте вміст відповіді за допомогою моделі MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Агент планування з оркестрацією багатьох агентів

У цьому прикладі Semantic Router Agent отримує запит користувача (наприклад, "Мені потрібен план готелю для моєї поїздки.").

Планувальник потім:

* Отримує план готелю: планувальник бере повідомлення користувача і, на основі системного підказу (включаючи деталі доступних агентів), генерує структурований план подорожі.
* Перелічує агентів та їхні інструменти: реєстр агентів містить список агентів (наприклад, для перельотів, готелів, оренди авто та активностей) разом із функціями або інструментами, які вони пропонують.
* Маршрутизує план до відповідних агентів: залежно від кількості підзадач, планувальник або надсилає повідомлення безпосередньо до виділеного агента (для сценаріїв з одною задачею), або координує через менеджер групового чату для співпраці кількох агентів.
* Підсумовує результат: нарешті планувальник підсумовує згенерований план для ясності.
Наведений нижче приклад коду Python ілюструє ці кроки:

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

# Модель підзадачі подорожі

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # ми хочемо призначити завдання агенту

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Створіть клієнта, використовуючи змінні середовища з перевіркою типів

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Визначте повідомлення користувача

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

# Переконайтеся, що вміст відповіді є дійсним JSON-рядком перед його завантаженням

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Виведіть вміст відповіді після його завантаження як JSON

pprint(json.loads(response_content))
```

Нижче наведено вивід попереднього коду, і ви можете використати цей структурований вивід, щоб направити до `assigned_agent` та підсумувати план подорожі для кінцевого користувача.

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

Приклад ноутбука з попереднім кодом доступний [тут](07-autogen.ipynb).

### Ітеративне планування

Деякі завдання вимагають обміну інформацією або повторного планування, коли результат однієї підзадачі впливає на наступну. Наприклад, якщо агент виявляє непередбачений формат даних під час бронювання перельотів, йому може знадобитися адаптувати свою стратегію перед переходом до бронювання готелів.

Крім того, зворотний зв'язок від користувача (наприклад, коли людина вирішує, що віддає перевагу більш ранньому рейсу) може викликати часткове повторне планування. Такий динамічний, ітеративний підхід гарантує, що кінцеве рішення узгоджується з реальними обмеженнями та змінними уподобаннями користувача.

наприклад приклад коду

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. те саме, що й у попередньому коді, і передати історію користувача та поточний план
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
# .. перепланувати і надіслати завдання відповідним агентам
```

Для більш комплексного планування ознайомтеся з Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">публікацією в блозі</a> про розв'язання складних завдань.

## Підсумок

У цій статті ми розглянули приклад того, як можна створити планувальник, який може динамічно вибирати визначених доступних агентів. Вивід планувальника розбиває завдання і призначає агентів для їх виконання. Передбачається, що агенти мають доступ до функцій/інструментів, необхідних для виконання завдання. Окрім агентів, ви можете включити інші шаблони, такі як рефлексія, сумаризатор і круговий чат, щоб додатково налаштувати систему.

## Додаткові ресурси

AutoGen Magentic One - універсальна мультиагентна система для розв'язання складних завдань, яка досягла вражаючих результатів на кількох складних агентних бенчмарках. Посилання: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. У цій реалізації оркестратор створює специфічний план завдання та делегує ці завдання доступним агентам. Окрім планування оркестратор також використовує механізм відстеження для моніторингу прогресу завдання і за потреби виконує повторне планування.

### Є ще питання про патерн планування?

Долучіться до [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), щоб зустрітися з іншими учнями, відвідати години консультацій і отримати відповіді на свої запитання про AI-агентів.

## Попередній урок

[Створення надійних AI-агентів](../06-building-trustworthy-agents/README.md)

## Наступний урок

[Патерн мультиагентної системи](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Застереження**:
Цей документ було перекладено за допомогою сервісу машинного перекладу на базі штучного інтелекту [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, просимо врахувати, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ мовою оригіналу слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується скористатися послугами професійного перекладача. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->