[![Planning Design Pattern](../../../translated_images/sr/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Кликните на слику изнад да бисте погледали видео о овом лекцији)_

# Плански Дизајн

## Увод

Овај лекција ће обухватити

* Дефинисање јасног укупног циља и разбијање сложеног задатка на управљиве задатке.
* Коришћење структурисаног излаза за поузданије и машински читљиве одговоре.
* Примена приступа заснованог на догађајима за руковање динамичким задацима и неочекиваним улазима.

## Циљеви учења

Након завршетка ове лекције, имаћете разумевање о:

* Идентификовању и постављању укупног циља за AI агента, осигуравајући да јасно зна шта треба постићи.
* Распадању сложеног задатка на управљиве потзадатке и организовању у логичан низ.
* Опремању агената правим алатима (нпр. алати за претрагу или алати за аналитику података), одлучивању када и како се користе и руковању неочекиваним ситуацијама које се појаве.
* Евалуацији резултата потзадатака, мерењу учинка и итерисању акција ради побољшања коначног излаза.

## Дефинисање укупног циља и разбијање задатка

![Defining Goals and Tasks](../../../translated_images/sr/defining-goals-tasks.d70439e19e37c47a.webp)

Већина стварних задатака је превише сложена да се реши у једном кораку. AI агенту је потребан концизан циљ који ће усмеравати његово планирање и акције. На пример, размотримо циљ:

    "Направити тродневни план пута."

Иако је једноставан за изрицање, и даље је потребно прецизирање. Што је циљ јаснији, тим боље агент (и било који људски сарадници) могу да се фокусирају на постизање правог резултата, као што је креирање свеобухватног плана са опцијама за летове, препорукама за хотел и предлозима активности.

### Разлагање задатка

Велики или сложени задаци постају управљивији када се поделе на мање, циљано оријентисане потзадатке.
За пример плана пута, можете распоредити циљ на:

* Резервација лета
* Резервација хотела
* Изнајмљивање аутомобила
* Персонализација

Сваки потзадатак може затим обрађивати посебни агенти или процеси. Један агент може бити специјалиста за проналажење најбољих понуда летова, други се фокусира на резервације хотела, и тако даље. Координаторски или „потчињени“ агент може затим компајлирати ове резултате у кохерентан план за крајњег корисника.

Ова модуларна метода такође омогућава постепена унапређења. На пример, можете додати специјализоване агенте за препоруке хране или предлоге локалних активности и временом прецизирати план.

### Структурисани излаз

Велики језички модели (LLM) могу генератисати структурисани излаз (нпр. JSON) који је лакши за даље агенте или сервисе да анализирају и обраде. Ово је посебно корисно у мулти-агентском контексту, где можемо извршавати задатке након што је добијен план планирања. Погледајте овај <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">блог пост</a> за брз преглед.

Следећи Python исечак демонстрира једноставног планирача агента који разлаже циљ на потзадатке и генерише структурисани план:

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

# Модел за путни подзадаци
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # Желимо да доделимо задатак агенту

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Да бисте се аутентификовали са моделом, потребно је да генеришете лични приступни токен (PAT) у вашим GitHub подешавањима.
    # Креирајте свој PAT токен пратећи упутства овде: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Дефинишите поруку корисника
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

# # Осигурајте да је садржај одговора важећи JSON стринг пре него што га учитате
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# ако је response_content None:
#     баците ValueError("Садржај одговора није важећи JSON стринг")

# # Испишите садржај одговора након учитавања као JSON
# pprint(json.loads(response_content))

# Верификујте садржај одговора са MathReasoning моделом
# TravelPlan.model_validate(json.loads(response_content))
```

### Планирачки агент са мулти-агентском оркестрацијом

У овом примеру, Semantic Router Agent прима кориснички захтев (нпр. „Потребан ми је план хотела за моје путовање.“).

Планирач затим:

* Прима план хотела: Планирач узима поруку корисника и, на основу системског упуства (укључујући доступне детаље о агенту), генерише структурисани план путовања.
* Листује агенте и њихове алате: Регистар агената садржи листу агената (нпр. за лет, хотел, изнајмљивање аутомобила и активности) заједно са функцијама или алатима које нуде.
* Упућује план одговарајућим агентима: У зависности од броја потзадатака, планирач или шаље поруку директно посебном агенту (у случају једноструких сценарија) или координира преко менаџера групног ћаскања за мулти-агентску сарадњу.
* Сумира резултат: На крају, планирач прави резиме генерисаног плана ради јасноће.
Следећи Python пример кода илуструје ове кораке:

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

# Модел Подзадатка Путавања

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # Желимо да доделимо задатак агенту

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Креирајте клијента са типски провереним променљивим окружења

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Дефинишите поруку корисника

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

# Обезбедите да је садржај одговора важећи JSON низ пре учитавања

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Испишите садржај одговора након учитавања као JSON

pprint(json.loads(response_content))
```

Следи излаз из претходног кода и можете користити овај структурисани излаз за усмеравање ка `assigned_agent` и сажимање плана путовања за крајњег корисника.

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

Пример notebook-а са претходним примером кода доступан је [овде](07-autogen.ipynb).

### Итерирајуће планирање

Неки задаци захтевају напред-назад или поновно планирање, где резултат једног потзадатка утиче на следећи. На пример, ако агент открије неочекивани формат података приликом резервације летова, можда ће морати да адаптира своју стратегију пре него што пређе на резервације хотела.

Поред тога, повратна информација корисника (нпр. када човек одлучи да преферира ранији лет) може покренути делимично поновно планирање. Овај динамичан, итерирајући приступ осигурава да коначно решење одговара стварним ограничењима и развијајућим преференцама корисника.

нпр. пример кода

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. исто као претходни код и проследи корисничку историју, тренутни план
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
# .. поново испланирај и пошаљи задатке одговарајућим агентима
```

За комплетније планирање погледајте Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">блог пост</a> за решавање сложених задатака.

## Резиме

У овом чланку смо видели пример како можемо направити планирача који може динамично одабрати доступне дефинисане агенте. Излаз планирача разлаже задатке и додељује агенте тако да се могу извршити. Подржава се да агенти имају приступ функцијама/алатима потребним за извршење задатка. Поред агената, можете укључити и друге обрасце као што су рефлексија, сажимање и круг ћаскања за даљу прилагођеност.

## Додатни извори

AutoGen Magentic One - Генералистички мулти-агентски систем за решавање сложених задатака и постигао је импресивне резултате на више изазовних агенцијских тестова. Референца: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. У овој имплементацији оркестратор креира план специфичан за задатак и делегира те задатке доступним агентима. Поред планирања, оркестратор користи и механизам праћења напретка задатка и поновног планирања по потреби.

### Имате ли више питања о шаблону планирања?

Придружите се [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) да упознате друге учеснике, присуствујете офис сати и добијете одговоре на питања о AI агентима.

## Претходна лекција

[Изградња поверења у AI агенте](../06-building-trustworthy-agents/README.md)

## Следећа лекција

[Шаблон дизајна мулти-агента](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Одрицање одговорности**:
Овај документ је преведен помоћу AI услуге за превођење [Co-op Translator](https://github.com/Azure/co-op-translator). Иако се трудимо да буде прецизно, молимо вас да имате у виду да аутоматски преводи могу садржати грешке или нетачности. Оригинални документ на његовом изворном језику треба сматрати ауторитетом. За критичне информације препоручује се професионални људски превод. Не сносимо одговорност за било каква неспоразума или погрешна тумачења настала употребом овог превода.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->