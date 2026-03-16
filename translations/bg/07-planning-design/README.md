[![Planning Design Pattern](../../../translated_images/bg/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Щракнете на изображението по-горе, за да гледате видеото на този урок)_

# Планиране на дизайн

## Въведение

Този урок ще обхване

* Дефиниране на ясен обща цел и разделяне на сложна задача на управляеми задачи.
* Използване на структурирани резултати за по-надеждни и машиночетими отговори.
* Прилагане на подход, основан на събития, за справяне с динамични задачи и непредвидени входни данни.

## Цели на обучението

След завършване на този урок ще имате разбиране за:

* Идентифициране и поставяне на обща цел за AI агент, гарантирайки, че той ясно знае какво трябва да бъде постигнато.
* Разделяне на сложна задача на управляеми подзадачи и организирането им в логическа последователност.
* Осигуряване на агентите с правилните инструменти (например, търсачески инструменти или инструменти за анализ на данни), решаване кога и как да бъдат използвани и справяне с непредвидени ситуации.
* Оценка на резултатите от подзадачите, измерване на представянето и итерации върху действията за подобряване на крайния изход.

## Дефиниране на общата цел и разделяне на задача

![Defining Goals and Tasks](../../../translated_images/bg/defining-goals-tasks.d70439e19e37c47a.webp)

Повечето реални задачи са твърде сложни, за да бъдат решени наведнъж. AI агентът се нуждае от кратка цел, която да ръководи неговото планиране и действия. Например, разгледайте целта:

    "Създаване на 3-дневен маршрут за пътуване."

Въпреки че е просто заявена, тя все още се нуждае от уточнение. Колкото по-ясна е целта, толкова по-добре агентът (и всеки човешки сътрудник) може да се съсредоточи върху постигането на правилния резултат, като създаване на цялостен маршрут с опции за полети, препоръки за хотели и предложения за активности.

### Разграждане на задача

Големи или сложни задачи стават по-управляеми, когато се разделят на по-малки, целенасочени подзадачи.
За примера с маршрута за пътуване, можете да разделите целта на:

* Резервация на полет
* Резервация на хотел
* Наемане на кола
* Персонализация

Всяка подзадача може да бъде решена от посветени агенти или процеси. Един агент може да се специализира в търсене на най-добрите оферти за полети, друг се фокусира върху резервациите за хотели и т.н. Координатор или „низходящ“ агент после може да компилира тези резултати в един цялостен маршрут за крайния потребител.

Този модулен подход позволява и стъпкови подобрения. Например, можете да добавите специализирани агенти за препоръки за храна или предложения за местни активности и да усъвършенствате маршрута с течение на времето.

### Структуриран изход

Големите езикови модели (LLMs) могат да генерират структуриран изход (например JSON), който е по-лесен за разбиране и обработка от низходящите агенти или услуги. Това е особено полезно в контекст на мулти-агентни системи, където можем да предприемем действия по задачите след получаване на планиращия изход. Вижте този <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">блог пост</a> за кратък преглед.

Следният Python фрагмент демонстрира прост планиращ агент, който разделя целта на подзадачи и генерира структуриран план:

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

# Модел за Подзадача Пътуване
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # искаме да възложим задачата на агента

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # За да се удостоверите с модела, трябва да генерирате личен токен за достъп (PAT) в настройките на GitHub.
    # Създайте вашия PAT токен, като следвате инструкциите тук: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Дефинирайте съобщението от потребителя
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

# # Уверете се, че съдържанието на отговора е валиден JSON низ преди да го заредите
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# ако response_content е None:
#     вдигнете ValueError("Съдържанието на отговора не е валиден JSON низ")

# # Отпечатайте съдържанието на отговора след зареждането му като JSON
# pprint(json.loads(response_content))

# Валидирайте съдържанието на отговора с модела MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Планиращ агент с мулти-агентна оркестрация

В този пример Semantic Router Agent получава потребителска заявка (например "Имам нужда от хотелски план за пътуването си.").

Планиращият агент:

* Получава План за хотел: Приема съобщението на потребителя и, базирано на системен prompt (включително наличните агенти), генерира структуриран план за пътуване.
* Изброява агенти и техните инструменти: Регистърът на агентите съдържа списък с агенти (например за полети, хотели, коли под наем и активности) заедно с функциите или инструментите, които предлагат.
* Насочва плана към съответните агенти: В зависимост от броя на подзадачите, планиращият или изпраща съобщението директно към посветен агент (за сценарии с една задача), или координира чрез мениджър на групов чат за мулти-агентно сътрудничество.
* Обобщава резултата: Накрая планиращият обобщава генерирания план за прозрачност.
Следният примерен Python код илюстрира тези стъпки:

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

# Модел за подзадача на пътуване

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # искаме да възложим задачата на агента

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Създайте клиента с типово проверени променливи на средата

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Дефинирайте съобщението на потребителя

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

# Уверете се, че съдържанието на отговора е валиден JSON низ преди да го заредите

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Отпечатайте съдържанието на отговора след зареждането му като JSON

pprint(json.loads(response_content))
```

Това, което следва, е изходът от горния код, който можете да използвате за насочване към `assigned_agent` и обобщаване на план за пътуване за крайния потребител.

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

Примерен бележник с предишния код е наличен [тук](07-autogen.ipynb).

### Итеративно планиране

Някои задачи изискват обратна връзка или повторно планиране, при което резултатът от една подзадача влияе на следващата. Например, ако агентът открие неочакван формат на данни при резервация на полети, може да се наложи да промени стратегията си преди да продължи с резервациите на хотели.

Освен това, обратната връзка от потребителя (например, ако човек реши, че предпочита по-ранен полет) може да задейства частично препланиране. Този динамичен, итеративен подход гарантира, че крайното решение съответства на реалните ограничения и променящите се предпочитания на потребителя.

например код

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. същото като предишния код и предава текущата история на потребителя, настоящия план
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
# .. пренасрочи и изпрати задачите на съответните агенти
```

За по-цялостно планиране разгледайте Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">блог пост</a> за решаване на сложни задачи.

## Резюме

В тази статия разгледахме пример как можем да създадем планиращ, който динамично избира наличните дефинирани агенти. Изходът на планиращия разбива задачите и разпределя агентите, така че да могат да бъдат изпълнени. Предполага се, че агентите имат достъп до функциите/инструментите, необходими за изпълнение на задачата. Освен агентите можете да включите и други модели като отражение, обобщаващ агент и ротационен чат, за да персонализирате допълнително.

## Допълнителни ресурси

AutoGen Magnetic One - универсална мулти-агентна система за решаване на сложни задачи, която е постигнала впечатляващи резултати в множество предизвикателни агентни бенчмаркове. Референция: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. В тази имплементация оркестраторът създава план, специфичен за задачата, и делегира задачите на наличните агенти. Освен планирането, оркестраторът използва механизъм за проследяване, за да наблюдава напредъка на задачата и при нужда препланира.

### Имате ли още въпроси за Патерна на планиране?

Присъединете се към [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), за да се срещнете с други обучаващи се, да посетите работни часове и да получите отговори на вашите въпроси за AI агенти.

## Предишен урок

[Създаване на надеждни AI агенти](../06-building-trustworthy-agents/README.md)

## Следващ урок

[Мулти-агентен дизайн патерн](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Отказ от отговорност**:  
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на неговия роден език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Не носим отговорност за никакви недоразумения или погрешни тълкувания, произтичащи от използването на този превод.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->