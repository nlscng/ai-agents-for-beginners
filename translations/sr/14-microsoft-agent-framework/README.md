# Истраживање Microsoft Agent Framework-а

![Agent Framework](../../../translated_images/sr/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Увод

Овај час ће покрити:

- Разумевање Microsoft Agent Framework-а: Кључне Карактеристике и Вредност  
- Истраживање кључних појмова Microsoft Agent Framework-а
- Поређење MAF са Semantic Kernel и AutoGen: Водич за миграцију

## Циљеви учења

Након завршетка овог часа, знаћете како да:

- Креирате AI агенте спремне за продукцију користећи Microsoft Agent Framework
- Примeните основне карактеристике Microsoft Agent Framework-а у вашим агенцним случајевима
- Мигрирате и интегришете постојеће агенске оквире и алате  

## Примери кода

Примери кода за [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) могу се наћи у овом репозиторијуму у фајловима `xx-python-agent-framework` и `xx-dotnet-agent-framework`.

## Разумевање Microsoft Agent Framework-а

![Framework Intro](../../../translated_images/sr/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) се надовезује на искуство и сазнања из Semantic Kernel и AutoGen. Он нуди флексибилност за решавање широког спектра агенсних случајева који се виде и у продукцији и у истраживачким окружењима, укључујући:

- **Секвенцијалну оркестрацију агената** у сценаријима где су потребни корак-по-корак токови рада.
- **Паралелну оркестрацију** у сценаријима где агенти морају да заврше задатке истовремено.
- **Оркестрацију групног ћаскања** у сценаријима где агенти могу заједно сарађивати на једном задатку.
- **Оркестрацију предаје** у сценаријима где агенти предају задатак један другом како се подзадатци завршавају.
- **Магнетску оркестрацију** у сценаријима где менаџер агент креира и мења листу задатака и управља координацијом подагената да заврше задатак.

Да би испоручио AI агенте у продукцији, MAF такође укључује функције за:

- **Опсервабилност** кроз коришћење OpenTelemetry-а где свака акција AI агента, укључујући позив алата, кораке оркестрације, токове резоновања и праћење перформанси кроз Microsoft Foundry контролне табле.
- **Сигурност** хостованих агената нативно на Microsoft Foundry-у који укључује контролу приступа засновану на улогама, обраду приватних података и уграђену безбедност садржаја.
- **Издржљивост** јер се агенске теме и токови рада могу паузирати, наставити и опоравити од грешака, што омогућава дуже покретање процеса.
- **Контролу** јер су подржани токови рада са човеком у петљи где се задаци означавају као захтевајући људско одобрење.

Microsoft Agent Framework је такође фокусиран на интероперабилност кроз:

- **Бити независан од облака** - Агенти могу да раде у контејнерима, у локалном окружењу и преко више различитих облака.
- **Бити независан од провајдера** - Агенти могу бити креирани кроз ваш омиљени SDK укључујући Azure OpenAI и OpenAI.
- **Интеграцију отворених стандарда** - Агенти могу користити протоколе као што су Agent-to-Agent (A2A) и Model Context Protocol (MCP) за откривање и коришћење других агената и алата.
- **Плугине и конекторе** - Могуће су везе са сервисима за податке и меморију као што су Microsoft Fabric, SharePoint, Pinecone и Qdrant.

Погледајмо како се ове функције примењују на неке од основних појмова Microsoft Agent Framework-а.

## Кључни појмови Microsoft Agent Framework-а

### Агенти

![Agent Framework](../../../translated_images/sr/agent-components.410a06daf87b4fef.webp)

**Креирање агената**

Креирање агената се врши дефинисањем сервиса за инференцу (LLM провајдер), скупа упутстава која AI агент треба да следи и додељеног `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Горњи пример користи `Azure OpenAI`, али агенти могу бити креирани коришћењем разних сервиса укључујући `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` API-ји

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

или удаљени агенти користећи A2A протокол:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Покретање агената**

Агенти се покрећу коришћењем метода `.run` или `.run_stream` за одговарајуће нестриминг или стриминг одговоре.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Сваки позив агента такође може имати опције за прилагођавање параметара као што су `max_tokens` који агент користи, `tools` које агент може позивати, и чак сам `model` који се користи за агента.

Ово је корисно у случајевима када су за извршење корисничког задатка потребни одређени модели или алати.

**Алатке**

Алатке могу бити дефинисане приликом креирања агента:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Када се директно креира ChatAgent

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

и такође приликом покретања агента:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Алат обезбеђен само за овај покрет )
```

**Агентске теме**

Агентске теме се користе за руковање вишекратним разговорима. Теме могу бити креиране:

- Коришћењем `get_new_thread()` што омогућава да тема буде сачувана током времена
- Аутоматским креирањем теме приликом покретања агента која траје само током тренутног позива.

За креирање теме, код изгледа овако:

```python
# Креирај нови нит.
thread = agent.get_new_thread() # Покрени агента са нитима.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Онда тему можете сериализовати и сачувати за каснију употребу:

```python
# Направи нови тред.
thread = agent.get_new_thread() 

# Покрени агента са тредом.

response = await agent.run("Hello, how are you?", thread=thread) 

# Сериализуј тред за чување.

serialized_thread = await thread.serialize() 

# Десериализуј стање треда после учитавања из складишта.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent Middleware**

Агенти комуницирају са алатима и LLM-овима како би извршили корисничке задатке. У одређеним сценаријима желимо да извршимо или пратимо радње између ових интеракција. Agent middleware нам то омогућава кроз:

*Function Middleware*

Ова middleware компонента нам омогућава да извршимо акцију између агента и функције/алата које ће позивати. Пример употребе је када желите да радите евидентирање позива функције.

У следећем коду `next` одређује да ли се позива следећи middleware или стварна функција.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Предобрада: Логовање пре извршења функције
    print(f"[Function] Calling {context.function.name}")

    # Настави на следећи посреднички слој или извршење функције
    await next(context)

    # Постобрада: Логовање након извршења функције
    print(f"[Function] {context.function.name} completed")
```

*Chat Middleware*

Ова middleware компонента омогућава извршавање или евидентирање акција између агента и захтева према LLM-у.

Она садржи важне информације као што су `messages` који се шаљу AI сервису.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Предпроцесирање: Логовати пре позива АИ
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Настави на следећи посреднички софтвер или АИ сервис
    await next(context)

    # Постпроцесирање: Логовати након одговора АИ
    print("[Chat] AI response received")

```

**Agent Memory**

Као што је објашњено у лекцији `Agentic Memory`, меморија је важан елемент који омогућава агенту да функционише у различитим контекстима. MAF нуди неколико различитих типова меморија:

*Упамћена меморија у оквиру теме*

Ово је меморија која се чува у темама током извршавања апликације.

```python
# Креирај нови нит.
thread = agent.get_new_thread() # Покрени агента са нитю.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Постојана порука*

Ова меморија се користи за чување историје разговора кроз различите сесије. Дефинише се коришћењем `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Креирај прилагођену продавницу порука
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Динамичка меморија*

Ова меморија се додаје у контекст пре покретања агената. Могу се чувати у екстерним сервисима као што је mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Користећи Mem0 за напредне меморијске могућности
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

**Agent Observability**

Опсервабилност је важна за изградњу поузданих и одрживих агенсних система. MAF се интегрише са OpenTelemetry за пружање трагања и мера за бољу опсервабилност.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # уради нешто
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Токови рада

MAF нуди токове рада који су унапред дефинисани кораци за завршетак задатка и укључују AI агенте као компоненте тих корака.

Токови рада се састоје од различитих компоненти које омогућавају бољу контролу тока. Токови рада такође омогућавају **мулти-агентску оркестрацију** и **checkpointing** за чување стања тока рада.

Основне компоненте тока рада су:

**Извршиоци**

Извршиоци примају улазне поруке, обављају додељене задатке и затим производе излазну поруку. Ово помера ток рада напред ка завршетку већег задатка. Извршиоци могу бити AI агенти или прилагођена логика.

**Повезнице**

Повезнице се користе за дефинисање тока порука у току рада. Оне могу бити:

*Директне повезнице* - Једноставне везе један-на-један између извршилаца:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Условне повезнице* - Активирају се када одређени услов буде испуњен. На пример, када собе у хотелу нису доступне, извршилац може предложити друге опције.

*Прекидачке повезнице* - Усмеравају поруке ка различитим извршиоцима у зависности од дефинисаних услова. На пример, ако путник има приоритетан приступ, његови задаци ће бити обрађени другим током рада.

*Раздвајајуће повезнице* - Шаљу једну поруку на више циљева.

*Спајајуће повезнице* - Прикупљају више порука од различитих извршилаца и шаљу их једном циљу.

**Догађаји**

За бољу опсервабилност тока рада, MAF нуди уграђене догађаје током извршавања, укључујући:

- `WorkflowStartedEvent`  - Започињање извршавања тока рада
- `WorkflowOutputEvent` - Ток рада производи излаз
- `WorkflowErrorEvent` - Ток рада наилази на грешку
- `ExecutorInvokeEvent`  - Извршилац почиње обраду
- `ExecutorCompleteEvent`  -  Извршилац завршава обраду
- `RequestInfoEvent` - Подаци о послатом захтеву

## Миграција са других оквира (Semantic Kernel и AutoGen)

### Разлике између MAF и Semantic Kernel-а

**Поједностављено креирање агената**

Semantic Kernel тражи креирање Kernel инстанце за сваког агента. MAF користи поједностављени приступ кроз екстензије за главне провајдере.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Креирање агентских тема**

Semantic Kernel захтева ручно креирање тема. У MAF-у агенту се директно додељује тема.

```python
thread = agent.get_new_thread() # Покрените агента са нитима.
```

**Регистрација алатки**

У Semantic Kernel-у алатке се региструју у Kernel, а онда Kernel се прослеђује агенту. У MAF-у се алатке региструју директно током креирања агента.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Разлике између MAF и AutoGen

**Тимови у односу на токове рада**

`Teams` су структура догађаја за догађајно вођене активности са агентима у AutoGen. MAF користи `Workflows` који усмеравају податке ка извршиоцима кроз архитектуру засновану на графу.

**Креирање алатки**

AutoGen користи `FunctionTool` за омотавање функција које агенти могу позивати. MAF користи @ai_function који ради слично, али и аутоматски изводи шеме за сваку функцију.

**Понашање агената**

Агенти у AutoGen-у су по дефиницији једнократни осим ако `max_tool_iterations` није подешен на већу вредност. Унутар MAF `ChatAgent` је по дефаулту мултикратно позивајући алате док кориснички задатак није завршен.

## Примери кода

Примери кода за Microsoft Agent Framework могу се наћи у овом репозиторијуму у фајловима `xx-python-agent-framework` и `xx-dotnet-agent-framework`.

## Имате више питања о Microsoft Agent Framework-у?

Придружите се [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) да бисте упознали друге учеснике, присуствовали канцеларијским сатима и добили одговоре на питања о вашим AI агентима.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Изјава о одрицању одговорности**:
Овај документ је преведен помоћу АИ преводилачке услуге [Co-op Translator](https://github.com/Azure/co-op-translator). Иако тежимо тачности, имајте у виду да аутоматски преводи могу садржати грешке или нетачности. Првобитни документ на његовом оригиналном језику треба сматрати ауторитетним извором. За критичне информације препоручује се професионални људски превод. Нисмо одговорни за било каква неспоразума или погрешна тумачења која произилазе из коришћења овог превода.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->