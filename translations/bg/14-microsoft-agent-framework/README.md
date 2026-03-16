# Изследване на Microsoft Agent Framework

![Agent Framework](../../../translated_images/bg/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Въведение

Този урок ще покрие:

- Разбиране на Microsoft Agent Framework: Основни характеристики и стойност  
- Изследване на ключовите концепции на Microsoft Agent Framework
- Сравнение на MAF с Semantic Kernel и AutoGen: Ръководство за миграция

## Учебни цели

След завършване на този урок, ще знаете как да:

- Създавате продукционно готови AI агенти с помощта на Microsoft Agent Framework
- Прилагате основните функции на Microsoft Agent Framework към вашите агентни случаи на употреба
- Мигрирате и интегрирате съществуващи агентни рамки и инструменти  

## Примери с код  

Примери с код за [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) могат да бъдат намерени в това репозитори под файловете `xx-python-agent-framework` и `xx-dotnet-agent-framework`.

## Разбиране на Microsoft Agent Framework

![Framework Intro](../../../translated_images/bg/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) се основава на опита и наученото от Semantic Kernel и AutoGen. Той предлага гъвкавост да адресира широкото разнообразие от агентни случаи на употреба, срещани както в продукционна, така и в изследователска среда, включително:

- **Последователна агентна оркестрация** в сценарии, където са необходими стъпка по стъпка работни потоци.
- **Паралелна оркестрация** в сценарии, където агентите трябва да изпълняват задачи едновременно.
- **Оркестрация на групов чат** в сценарии, където агентите могат да си сътрудничат върху една задача.
- **Оркестрация на предаване** в сценарии, където агентите предават задачата един на друг с приключването на подзадачи.
- **Магнитна оркестрация** в сценарии, където агент-мениджър създава и модифицира списък със задачи и управлява координацията на подагенти за изпълнение на задачата.

За да предоставя AI агенти в продукция, MAF включва и функции за:

- **Наблюдаемост** чрез използване на OpenTelemetry, където всяко действие на AI агента, включително извикване на инструменти, стъпки на оркестрация, логически потоци и мониторинг на производителността през Microsoft Foundry табла.
- **Сигурност** чрез хостване на агентите директно на Microsoft Foundry, който включва контрол на достъпа на база роли, обработка на лични данни и вградена безопасност на съдържанието.
- **Издръжливост** тъй като нишките и работните потоци на агентите могат да се паузират, възобновяват и възстановяват след грешки, което позволява продължителни процеси.
- **Контрол** чрез поддръжка на работни потоци с човешко участие, където задачите се маркират като изискващи одобрение от човека.

Microsoft Agent Framework също така е насочен към съвместимост чрез:

- **Облак-независимост** – агенти могат да работят в контейнери, на локални сървъри и в различни облачни среди.
- **Доставчик-независимост** – агенти могат да се създават чрез предпочитания SDK, включително Azure OpenAI и OpenAI.
- **Интеграция на отворени стандарти** – агентите могат да използват протоколи като Agent-to-Agent (A2A) и Model Context Protocol (MCP) за откриване и използване на други агенти и инструменти.
- **Плъгини и конектори** – могат да се свързват с услуги за данни и памет като Microsoft Fabric, SharePoint, Pinecone и Qdrant.

Нека разгледаме как тези функции се прилагат към някои от ключовите концепции на Microsoft Agent Framework.

## Ключови концепции на Microsoft Agent Framework

### Агенти

![Agent Framework](../../../translated_images/bg/agent-components.410a06daf87b4fef.webp)

**Създаване на агенти**

Създаването на агент става чрез дефиниране на inference service (LLM доставчик), набор от инструкции, които AI агентът да следва, и задаване на `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

По-горе се използва `Azure OpenAI`, но агентите могат да се създават с различни услуги, включително `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` API

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

или отдалечени агенти, използващи A2A протокол:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Изпълнение на агенти**

Агентите се изпълняват с методите `.run` или `.run_stream` за отговори без стрийминг или със стрийминг.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Във всяко изпълнение на агент също могат да се задават опции за персонализиране на параметри като `max_tokens`, които агентът използва, `tools`, които агентът може да извиква, както и дори самия `model`, използван за агента.

Това е полезно в случаи, когато са необходими специфични модели или инструменти за изпълнение на задачата на потребителя.

**Инструменти**

Инструменти могат да се дефинират както при създаването на агента:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Когато създавате ChatAgent директно

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

така и при изпълнението на агента:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Инструмент, предоставен само за тази сесия )
```

**Нишки на агента**

Нишките на агента се използват за обработка на разговори с множество ходове. Нишки могат да се създават чрез:

- Използване на `get_new_thread()`, което позволява нишката да се запазва във времето
- Автоматично създаване на нишка при изпълнение на агент и тя да съществува само по време на текущото изпълнение

За създаване на нишка, кодът изглежда така:

```python
# Създайте нов поток.
thread = agent.get_new_thread() # Стартирайте агента с потока.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

След това можете да сериализирате нишката за съхранение и по-късна употреба:

```python
# Създайте нова нишка.
thread = agent.get_new_thread() 

# Стартирайте агента с нишката.

response = await agent.run("Hello, how are you?", thread=thread) 

# Сериализирайте нишката за съхранение.

serialized_thread = await thread.serialize() 

# Десериализирайте състоянието на нишката след зареждане от съхранението.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware на агента**

Агентите взаимодействат с инструменти и LLM, за да изпълняват задачите на потребителите. В някои случаи искаме да изпълним или проследим действие между тези взаимодействия. Middleware на агента ни позволява да правим това чрез:

*Function Middleware*

Това middleware ни позволява да извършим действие между агента и функция/инструмент, който ще извиква. Пример за използване е, ако желаете да направите логване на извикването на функцията.

В долния код `next` определя дали да се извика следващото middleware или директно функцията.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Предварителна обработка: Запис преди изпълнението на функцията
    print(f"[Function] Calling {context.function.name}")

    # Продължете към следващата междинна обработка или изпълнение на функция
    await next(context)

    # Последваща обработка: Запис след изпълнението на функцията
    print(f"[Function] {context.function.name} completed")
```

*Chat Middleware*

Това middleware позволява да изпълним действие или логване между агента и заявките към LLM.

Това съдържа важна информация като `messages`, които се изпращат към AI услугата.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Предварителна обработка: Лог преди повикване на AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Продължете към следващия междинен софтуер или AI услуга
    await next(context)

    # Следобработка: Лог след отговор от AI
    print("[Chat] AI response received")

```

**Памет на агента**

Както бе разгледано в урока `Agentic Memory`, паметта е важен елемент, който позволява на агента да работи с различен контекст. MAF предлага няколко типа памет:

*Съхранение в паметта*

Това е памет, съхранявана в нишките по време на изпълнението на приложението.

```python
# Създайте нов нишка.
thread = agent.get_new_thread() # Стартирайте агента с нишката.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Постоянни съобщения*

Тази памет се използва за съхранение на история на разговорите при различни сесии. Дефинира се чрез `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Създайте персонализирано хранилище за съобщения
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Динамична памет*

Тази памет се добавя в контекста преди стартиране на агентите. Тези памети могат да се съхраняват в външни услуги като mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Използване на Mem0 за разширени възможности за памет
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

**Наблюдаемост на агента**

Наблюдаемостта е важна за изграждането на надеждни и поддържани агентни системи. MAF се интегрира с OpenTelemetry, за да предостави проследяване и метри за по-добра наблюдаемост.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # направи нещо
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Работни потоци

MAF предлага работни потоци, които са предварително дефинирани стъпки за изпълнение на задача и включват AI агенти като компоненти в тези стъпки.

Работните потоци се състоят от различни компоненти, които позволяват по-добър контрол на потока. Те също така позволяват **оркестрация с множество агенти** и **checkpointing** за съхранение на състоянието на работния поток.

Основните компоненти на работен поток са:

**Изпълнители**

Изпълнителите получават входящи съобщения, изпълняват възложените им задачи и след това генерират изходящо съобщение. Това придвижва работния поток към завършване на по-голямата задача. Изпълнителите могат да бъдат AI агенти или персонализирана логика.

**Ръбове**

Ръбовете се използват за дефиниране на потока на съобщенията в един работен поток. Те могат да бъдат:

*Прости ръбове* - Простите връзки един към един между изпълнители:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Условни ръбове* - Активирани след изпълнение на определено условие. Например, когато няма налични хотелски стаи, изпълнител може да предложи други опции.

*Ръбове тип switch-case* - Насочват съобщенията към различни изпълнители въз основа на определени условия. Например, ако клиент за пътуване има приоритетен достъп, задачите му се обработват в друг работен поток.

*Ръбове fan-out* - Изпращат едно съобщение към множество цели.

*Ръбове fan-in* - Събират множество съобщения от различни изпълнители и ги изпращат към една цел.

**Събития**

За по-добра наблюдаемост в работните потоци, MAF предлага вградени събития за изпълнение, включително:

- `WorkflowStartedEvent`  - Започва изпълнение на работен поток
- `WorkflowOutputEvent` - Работният поток генерира изход
- `WorkflowErrorEvent` - Работният поток среща грешка
- `ExecutorInvokeEvent`  - Изпълнител започва обработка
- `ExecutorCompleteEvent`  -  Изпълнител завършва обработка
- `RequestInfoEvent` - Подава се заявка

## Миграция от други рамки (Semantic Kernel и AutoGen)

### Разлики между MAF и Semantic Kernel

**Оптимизирано създаване на агент**

Semantic Kernel изисква създаването на Kernel инстанция за всеки агент. MAF използва опростен подход чрез използване на разширения за основните доставчици.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Създаване на нишка на агент**

Semantic Kernel изисква нишките да се създават ръчно. В MAF нишка се задава директно на агента.

```python
thread = agent.get_new_thread() # Стартирайте агента с нишката.
```

**Регистрация на инструменти**

В Semantic Kernel, инструментите се регистрират в Kernel, който след това се подава на агента. В MAF, инструментите се регистрират директно по време на процеса на създаване на агента.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Разлики между MAF и AutoGen

**Екипи срещу Работни потоци**

`Teams` са структура за събития в AutoGen за управление на дейности с агенти чрез събития. MAF използва `Workflows`, които насочват данни към изпълнители чрез графова архитектура.

**Създаване на инструменти**

AutoGen използва `FunctionTool`, за да опакова функции за извикване от агенти. MAF използва @ai_function, който работи подобно, но също така автоматично извлича схемите за всяка функция.

**Поведение на агента**

Агентите са с единично обръщение по подразбиране в AutoGen, освен ако не е зададен `max_tool_iterations` на по-висока стойност. В MAF, `ChatAgent` е мулти-обръщение по подразбиране, което означава, че продължава да извиква инструменти докато задачата на потребителя не бъде завършена.

## Примери с код  

Примери с код за Microsoft Agent Framework могат да бъдат намерени в това репозитори под файловете `xx-python-agent-framework` и `xx-dotnet-agent-framework`.

## Имаш ли още въпроси за Microsoft Agent Framework?

Присъедини се към [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), за да се срещнеш с други учащи, да посетиш часове за въпроси и да получиш отговори на въпросите си за AI агенти.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Отказ от отговорност**:
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на неговия оригинален език трябва да се счита за авторитетен източник. За критична информация е препоръчително да се използва професионален човешки превод. Ние не носим отговорност за никакви недоразумения или неправилни тълкувания, произтичащи от използването на този превод.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->