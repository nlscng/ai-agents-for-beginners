[![Дизайн-паттерн планирования](../../../translated_images/ru/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Нажмите на изображение выше, чтобы посмотреть видео этого урока)_

# Дизайн планирования

## Введение

В этом уроке будут рассмотрены:

* Определение ясной общей цели и разбиение сложной задачи на управляемые подзадачи.
* Использование структурированного вывода для более надежных и машинно-читаемых ответов.
* Применение событийно-управляемого подхода для обработки динамических задач и неожиданных входных данных.

## Цели обучения

По завершении урока вы поймете:

* Определять и задавать общую цель для AI-агента, убедившись, что он ясно понимает, чего нужно достичь.
* Декомпозировать сложную задачу на управляемые подзадачи и организовывать их в логическую последовательность.
* Оснастить агентов необходимыми инструментами (например, инструментами поиска или аналитики данных), решать, когда и как они используются, и справляться с возникающими неожиданными ситуациями.
* Оценивать результаты подзадач, измерять производительность и итеративно корректировать действия для улучшения итогового результата.

## Определение общей цели и разбиение задачи

![Определение целей и задач](../../../translated_images/ru/defining-goals-tasks.d70439e19e37c47a.webp)

Большинство реальных задач слишком сложны, чтобы решать их за один шаг. AI-агенту нужна краткая цель, которая будет направлять его планирование и действия. Например, рассмотрим цель:

    "Сгенерировать 3-дневный маршрут путешествия."

Хотя ее просто сформулировать, все равно требуется уточнение. Чем яснее цель, тем лучше агент (и любые человеческие сотрудники) сможет сосредоточиться на достижении правильного результата, например создании комплексного маршрута с вариантами перелетов, рекомендациями по отелям и предложениями по активностям.

### Декомпозиция задачи

Крупные или сложные задачи становятся более управляемыми, когда их разбивают на меньшие, ориентированные на цель подзадачи.
Для примера с маршрутом путешествия вы можете декомпозировать цель на:

* Бронирование авиабилетов
* Бронирование отеля
* Аренда автомобиля
* Персонализация

Каждую подзадачу затем можно поручить специализированным агентам или процессам. Один агент может специализироваться на поиске лучших предложений по авиабилетам, другой — на бронировании отелей и т. д. Координирующий или «финализирующий» агент затем может собрать эти результаты в единый связный маршрут для конечного пользователя.

Этот модульный подход также позволяет постепенно улучшать систему. Например, вы можете добавить специализированных агентов для рекомендаций по еде или предложений локальных активностей и со временем дорабатывать маршрут.

### Структурированный вывод

Большие языковые модели (LLMs) могут генерировать структурированный вывод (например, JSON), который проще для последующих агентов или сервисов парсить и обрабатывать. Это особенно полезно в многопользовательском (multi-agent) контексте, где мы можем выполнять эти задачи после получения результата планирования. Обзорную информацию смотрите в этой <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">публикации в блоге</a>.

Ниже приведен фрагмент Python, демонстрирующий простого агента планирования, декомпозирующего цель на подзадачи и генерирующего структурированный план:

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

# Модель подзадачи путешествия
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # мы хотим назначить задачу агенту

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Чтобы аутентифицироваться в модели, вам нужно сгенерировать персональный токен доступа (PAT) в настройках GitHub.
    # Создайте свой PAT, следуя инструкциям здесь: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Определите сообщение пользователя
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

# # Убедитесь, что содержимое ответа является допустимой JSON-строкой перед загрузкой
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Содержимое ответа не является допустимой JSON-строкой")

# # Выведите содержимое ответа после загрузки в формате JSON
# pprint(json.loads(response_content))

# Проверьте содержимое ответа с помощью модели MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Агент планирования с оркестрацией нескольких агентов

В этом примере Агент семантического маршрутизатора получает запрос пользователя (например, "Мне нужен план отеля для моей поездки.").

Затем планировщик:

* Получает план по отелю: Планировщик принимает сообщение пользователя и, основываясь на системном промпте (включая детали доступных агентов), генерирует структурированный план путешествия.
* Перечисляет агентов и их инструменты: Реестр агентов содержит список агентов (например, для перелетов, отелей, аренды автомобилей и активностей) вместе с функциями или инструментами, которые они предлагают.
* Маршрутизирует план к соответствующим агентам: В зависимости от количества подзадач планировщик либо отправляет сообщение напрямую выделенному агенту (для сценариев с одной задачей), либо координирует через менеджер группового чата для совместной работы нескольких агентов.
* Суммирует результат: Наконец, планировщик суммирует сгенерированный план для ясности.
Ниже приведен пример кода на Python, иллюстрирующий эти шаги:

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

# Модель подзадачи путешествия

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # мы хотим назначить задачу агенту

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Создайте клиента с проверкой типов переменных окружения

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Определите сообщение пользователя

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

# Убедитесь, что содержимое ответа является допустимой JSON-строкой перед загрузкой

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Выведите содержимое ответа после загрузки его как JSON

pprint(json.loads(response_content))
```

Что далее — это вывод из предыдущего кода, и вы затем можете использовать этот структурированный вывод, чтобы маршрутизировать к `assigned_agent` и суммировать план путешествия для конечного пользователя.

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

Пример ноутбука с предыдущим фрагментом кода доступен [здесь](07-autogen.ipynb).

### Итеративное планирование

Некоторым задачам требуется обмен информацией или перепланирование, когда результат одной подзадачи влияет на следующую. Например, если агент обнаруживает неожиданный формат данных при бронировании рейсов, ему может потребоваться адаптировать стратегию перед переходом к бронированию отелей.

Кроме того, обратная связь от пользователя (например, человек решает, что предпочитает более ранний рейс) может запустить частичное перепланирование. Такой динамический, итеративный подход обеспечивает соответствие итогового решения реальным ограничениям и меняющимся предпочтениям пользователя.

например, пример кода

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. то же, что и в предыдущем коде, и передать историю пользователя, текущий план
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
# .. перепланировать и отправить задачи соответствующим агентам
```

Для более всестороннего планирования ознакомьтесь с Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">статьей в блоге</a> о решении сложных задач.

## Резюме

В этой статье мы рассмотрели пример того, как можно создать планировщик, который может динамически выбирать определенных доступных агентов. Выходные данные Планировщика декомпозируют задачи и назначают агентов, чтобы они могли быть выполнены. Предполагается, что агенты имеют доступ к функциям/инструментам, необходимым для выполнения задачи. В дополнение к агентам вы можете включить другие паттерны, такие как рефлексия, суммаризатор и round robin чат для дальнейшей кастомизации.

## Дополнительные ресурсы

AutoGen Magentic One - Generalist multi-agent system для решения сложных задач, показавший впечатляющие результаты на нескольких сложных бенчмарках для агентных систем. Справка: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. В этой реализации оркестратор создает специализированный план задач и делегирует эти задачи доступным агентам. В дополнение к планированию оркестратор также использует механизм отслеживания для мониторинга прогресса задачи и перепланирования по мере необходимости.

### Есть вопросы о шаблоне проектирования планирования?

Присоединяйтесь к [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), чтобы встретиться с другими учащимися, посетить часы консультаций и получить ответы на вопросы по вашим AI-агентам.

## Предыдущий урок

[Создание надежных AI-агентов](../06-building-trustworthy-agents/README.md)

## Следующий урок

[Шаблон проектирования для нескольких агентов](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Отказ от ответственности**:
Этот документ был переведён с помощью сервиса машинного перевода [Co-op Translator](https://github.com/Azure/co-op-translator). Несмотря на наши усилия по обеспечению точности, пожалуйста, учитывайте, что автоматические переводы могут содержать ошибки или неточности. Исходный документ на языке оригинала следует считать авторитетным источником. Для критически важной информации рекомендуется профессиональный перевод человеком. Мы не несем ответственности за любые недоразумения или неправильные толкования, возникшие в результате использования этого перевода.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->