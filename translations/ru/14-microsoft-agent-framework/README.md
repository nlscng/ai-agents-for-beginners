# Изучение Microsoft Agent Framework

![Фреймворк агентов](../../../translated_images/ru/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Введение

В этом уроке будут рассмотрены:

- Понимание Microsoft Agent Framework: ключевые возможности и ценность  
- Изучение ключевых концепций Microsoft Agent Framework
- Сравнение MAF с Semantic Kernel и AutoGen: руководство по миграции

## Цели обучения

После завершения этого урока вы будете уметь:

- Создавать готовых к продакшну AI-агентов с помощью Microsoft Agent Framework
- Применять основные возможности Microsoft Agent Framework к вашим агентным сценариям
- Мигрировать и интегрировать существующие агентные фреймворки и инструменты  

## Примеры кода 

Примеры кода для [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) можно найти в этом репозитории в файлах `xx-python-agent-framework` и `xx-dotnet-agent-framework`.

## Понимание Microsoft Agent Framework

![Введение во фреймворк](../../../translated_images/ru/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) строится на опыте и выводах из Semantic Kernel и AutoGen. Он предлагает гибкость для решения широкого круга агентных сценариев, встречающихся как в продакшне, так и в исследовательской среде, включая:

- **Пошаговую оркестрацию агентов** в сценариях, где требуются пошаговые рабочие процессы.
- **Параллельную оркестрацию** в сценариях, где агенты должны выполнять задачи одновременно.
- **Оркестрацию группового чата** в сценариях, где агенты могут совместно работать над одной задачей.
- **Оркестрацию передачи (handoff)** в сценариях, где агенты передают задачу друг другу по мере завершения подзадач.
- **Магнитную оркестрацию** в сценариях, где менеджер-агент создает и изменяет список задач и координирует субагентов для выполнения задачи.

Для разворачивания AI-агентов в продакшне MAF также включает возможности для:

- **Наблюдаемости** через использование OpenTelemetry, где отслеживается каждое действие AI-агента, включая вызовы инструментов, шаги оркестрации, потоки рассуждений и мониторинг производительности через панели Microsoft Foundry.
- **Безопасности** за счет нативного размещения агентов на Microsoft Foundry, что включает средства управления безопасностью, такие как управление доступом на основе ролей, обработка приватных данных и встроенная безопасность контента.
- **Устойчивости** — потоки агентства и рабочие процессы могут приостанавливаться, возобновляться и восстанавливаться после ошибок, что позволяет поддерживать длительные процессы.
- **Контроля** — поддерживаются рабочие процессы с участием человека, где задачи помечаются как требующие одобрения человеком.

Microsoft Agent Framework также ориентирован на совместимость за счет:

- **Независимости от облака** — агенты могут запускаться в контейнерах, локально и в разных облаках.
- **Независимости от провайдера** — агенты можно создавать с помощью предпочитаемого SDK, включая Azure OpenAI и OpenAI
- **Интеграции открытых стандартов** — агенты могут использовать протоколы такие как Agent-to-Agent (A2A) и Model Context Protocol (MCP) для обнаружения и использования других агентов и инструментов.
- **Плагинов и коннекторов** — возможны подключения к сервисам данных и памяти, таким как Microsoft Fabric, SharePoint, Pinecone и Qdrant.

Давайте посмотрим, как эти возможности применяются к некоторым ключевым концепциям Microsoft Agent Framework.

## Ключевые концепции Microsoft Agent Framework

### Агенты

![Компоненты агента](../../../translated_images/ru/agent-components.410a06daf87b4fef.webp)

**Создание агентов**

Создание агента выполняется путем определения сервиса вывода (поставщик LLM), набора инструкций для AI-агента и присвоенного `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Выше используется `Azure OpenAI`, но агенты можно создавать с использованием различных сервисов, включая `Microsoft Foundry Agent Service`:

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

или удаленные агенты с использованием протокола A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Запуск агентов**

Агенты запускаются с помощью методов `.run` или `.run_stream` для нестриминговых или стриминговых ответов соответственно.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Каждый запуск агента также может иметь опции для настройки параметров, таких как `max_tokens`, `tools`, которыми агент может пользоваться, и даже сам `model`, используемый агентом.

Это полезно в случаях, когда для выполнения задачи пользователя требуются конкретные модели или инструменты.

**Инструменты**

Инструменты можно определять как при создании агента:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# При прямом создании ChatAgent

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

так и при запуске агента:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Инструмент предоставлен только для этого запуска )
```

**Потоки агента**

Потоки агента используются для обработки многотуровых разговоров. Потоки могут создаваться двумя способами:

- С помощью `get_new_thread()`, что позволяет сохранять поток со временем
- Автоматически при запуске агента, когда поток существует только в течение текущего запуска.

Чтобы создать поток, код выглядит так:

```python
# Создать новый поток.
thread = agent.get_new_thread() # Запустить агента в этом потоке.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Затем поток можно сериализовать для хранения и последующего использования:

```python
# Создать новый поток.
thread = agent.get_new_thread() 

# Запустить агента с этим потоком.

response = await agent.run("Hello, how are you?", thread=thread) 

# Сериализовать поток для хранения.

serialized_thread = await thread.serialize() 

# Десериализовать состояние потока после загрузки из хранилища.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Промежуточное ПО агента**

Агенты взаимодействуют с инструментами и LLM для выполнения задач пользователя. В некоторых сценариях мы хотим выполнять действия или отслеживать события между этими взаимодействиями. Промежуточное ПО агента позволяет делать это через:

*Функциональное промежуточное ПО*

Это промежуточное ПО позволяет выполнять действие между агентом и функцией/инструментом, который он собирается вызвать. Примером использования является логирование вызова функции.

В приведенном ниже коде `next` определяет, должен ли быть вызван следующий middleware или сама функция.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Предобработка: логирование перед выполнением функции
    print(f"[Function] Calling {context.function.name}")

    # Продолжить к следующему промежуточному обработчику или к выполнению функции
    await next(context)

    # Постобработка: логирование после выполнения функции
    print(f"[Function] {context.function.name} completed")
```

*Промежуточное ПО для чата*

Это промежуточное ПО позволяет выполнить или записать действие между агентом и запросами к LLM.

Оно содержит важную информацию, такую как `messages`, которые отправляются в AI-сервис.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Предобработка: логирование перед вызовом ИИ
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Продолжить к следующему промежуточному ПО или сервису ИИ
    await next(context)

    # Постобработка: логирование после ответа ИИ
    print("[Chat] AI response received")

```

**Память агента**

Как рассмотрено в уроке `Agentic Memory`, память является важным элементом, позволяющим агенту оперировать в разных контекстах. MAF предлагает несколько различных типов памяти:

*Память в оперативной памяти*

Это память, хранящаяся в потоках во время выполнения приложения.

```python
# Создать новый поток.
thread = agent.get_new_thread() # Запустить агента вместе с потоком.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Постоянные сообщения*

Эта память используется при сохранении истории разговоров между сессиями. Она определяется с помощью `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Создайте пользовательское хранилище сообщений
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Динамическая память*

Эта память добавляется в контекст перед запуском агентов. Такие памяти могут храниться во внешних сервисах, например mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Использование Mem0 для расширенных возможностей памяти
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

**Наблюдаемость агента**

Наблюдаемость важна для построения надежных и удобных в сопровождении агентных систем. MAF интегрируется с OpenTelemetry для предоставления трассировки и метрик для лучшей наблюдаемости.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # сделать что-нибудь
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Рабочие процессы

MAF предлагает рабочие процессы, которые представляют собой предопределенные шаги для выполнения задачи и включают AI-агентов в качестве компонентов на этих шагах.

Рабочие процессы состоят из различных компонентов, которые обеспечивают лучший контроль потока. Рабочие процессы также позволяют выполнять **оркестрацию нескольких агентов** и **создавать контрольные точки** для сохранения состояния workflow.

Основные компоненты рабочего процесса:

**Исполнители**

Исполнители получают входные сообщения, выполняют назначенные задачи и затем создают выходное сообщение. Это продвигает рабочий процесс к выполнению более крупной задачи. Исполнители могут быть как AI-агентами, так и пользовательской логикой.

**Ребра**

Ребра используются для определения потока сообщений в рабочем процессе. Это могут быть:

*Прямые ребра* - Простые одно-к-одному соединения между исполнителями:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Условные ребра* - Активируются после выполнения определенного условия. Например, когда номера в отеле недоступны, исполнитель может предложить другие варианты.

*Ребра switch-case* - Маршрутизируют сообщения к разным исполнителям на основе определенных условий. Например, если у клиента приоритетный доступ, его задачи будут обрабатываться в другом рабочем процессе.

*Разветвляющиеся ребра (Fan-out)* - Отправляют одно сообщение на несколько целей.

*Объединяющие ребра (Fan-in)* - Собирать несколько сообщений от разных исполнителей и отправлять их в одну цель.

**События**

Для обеспечения лучшей наблюдаемости рабочих процессов MAF предоставляет встроенные события для выполнения, включая:

- `WorkflowStartedEvent`  - Запуск выполнения рабочего процесса
- `WorkflowOutputEvent` - Рабочий процесс выпускает выход
- `WorkflowErrorEvent` - Рабочий процесс сталкивается с ошибкой
- `ExecutorInvokeEvent`  - Исполнитель начинает обработку
- `ExecutorCompleteEvent`  -  Исполнитель завершил обработку
- `RequestInfoEvent` - Отправлен запрос

## Миграция из других фреймворков (Semantic Kernel и AutoGen)

### Отличия между MAF и Semantic Kernel

**Упрощенное создание агентов**

Semantic Kernel требует создания экземпляра Kernel для каждого агента. MAF использует упрощенный подход с использованием расширений для основных провайдеров.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Создание потоков агента**

Semantic Kernel требует создания потоков вручную. В MAF агенту непосредственно присваивается поток.

```python
thread = agent.get_new_thread() # Запустите агента в потоке.
```

**Регистрация инструментов**

В Semantic Kernel инструменты регистрируются в Kernel, и затем Kernel передается агенту. В MAF инструменты регистрируются напрямую в процессе создания агента.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Отличия между MAF и AutoGen

**Teams vs Workflows**

`Teams` являются структурой событий для событийно-ориентированной активности с агентами в AutoGen. MAF использует `Workflows`, которые маршрутизируют данные к исполнителям через графовую архитектуру.

**Создание инструментов**

AutoGen использует `FunctionTool` для обертывания функций, которые агенты могут вызывать. MAF использует @ai_function, который работает аналогично, но также автоматически выводит схемы для каждой функции.

**Поведение агента**

В AutoGen агенты по умолчанию одношаговые (single-turn), если только `max_tool_iterations` не установлено на большее значение. В MAF `ChatAgent` по умолчанию многотуровый (multi-turn), что означает, что он будет продолжать вызывать инструменты до тех пор, пока задача пользователя не будет выполнена.

## Примеры кода 

Примеры кода для Microsoft Agent Framework можно найти в этом репозитории в файлах `xx-python-agent-framework` и `xx-dotnet-agent-framework`.

## Есть дополнительные вопросы о Microsoft Agent Framework?

Присоединяйтесь к [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), чтобы познакомиться с другими учащимися, посетить часы консультаций и получить ответы на свои вопросы по AI-агентам.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Отказ от ответственности**:
Этот документ был переведен с помощью сервиса перевода на основе ИИ [Co-op Translator](https://github.com/Azure/co-op-translator). Хотя мы стремимся к точности, просим учитывать, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его исходном языке следует считать авторитетным источником. Для критически важной информации рекомендуется обратиться к профессиональному переводу, выполненному человеком. Мы не несем ответственности за любые недоразумения или неправильные толкования, возникшие в результате использования этого перевода.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->