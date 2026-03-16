# Дослідження Microsoft Agent Framework

![Agent Framework](../../../translated_images/uk/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Вступ

Цей урок охоплює:

- Розуміння Microsoft Agent Framework: ключові функції та цінність  
- Ознайомлення з ключовими концепціями Microsoft Agent Framework
- Порівняння MAF з Semantic Kernel та AutoGen: посібник з міграції

## Навчальні цілі

Після завершення цього уроку ви знатимете, як:

- Створювати AI-агентів, готових до продакшену, використовуючи Microsoft Agent Framework
- Застосовувати основні можливості Microsoft Agent Framework до ваших агентних сценаріїв використання
- Мігрувати та інтегрувати існуючі агентні фреймворки та інструменти  

## Приклади коду 

Приклади коду для [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) можна знайти в цьому репозиторії у файлах `xx-python-agent-framework` та `xx-dotnet-agent-framework`.

## Розуміння Microsoft Agent Framework

![Framework Intro](../../../translated_images/uk/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) базується на досвіді та висновках із Semantic Kernel і AutoGen. Він пропонує гнучкість для вирішення різних агентних сценаріїв використання, які зустрічаються як у продакшені, так і в дослідженнях, зокрема:

- **Послідовна оркестрація агентів** у сценаріях, де потрібні покрокові робочі процеси.
- **Паралельна оркестрація** у випадках, коли агенти повинні виконувати завдання одночасно.
- **Оркестрація групового чату** у сценаріях, де агенти можуть співпрацювати над одним завданням.
- **Оркестрація передачі** у сценаріях, де агенти передають завдання один одному в міру завершення підзавдань.
- **Магнітна оркестрація** у сценаріях, де агент-менеджер створює та змінює список завдань і координує роботу підагентів для виконання завдання.

Для доставки AI-агентів у продакшені MAF також включає можливості для:

- **Спостережуваності** через використання OpenTelemetry, де кожна дія AI-агента, включно з викликом інструментів, кроками оркестрації, потоками міркувань та моніторингом продуктивності відображається в інформаційних панелях Microsoft Foundry.
- **Безпеки** шляхом розміщення агентів нативно в Microsoft Foundry, що включає засоби контролю безпеки, такі як доступ на основі ролей, обробка приватних даних і вбудована безпека контенту.
- **Стійкості** оскільки потоки та робочі процеси агентів можуть призупинятися, відновлюватися та відновлювати роботу після помилок, що дозволяє запускати довші процеси.
- **Контролю** оскільки підтримуються робочі процеси з участю людини, де завдання позначаються як такі, що вимагають затвердження людиною.

Microsoft Agent Framework також орієнтований на взаємодію з іншими системами завдяки:

- **Незалежності від хмари** - агенти можуть запускатися в контейнерах, локально та в різних хмарах.
- **Незалежності від провайдера** - агенти можна створювати через улюблений SDK, включаючи Azure OpenAI та OpenAI
- **Інтеграції відкритих стандартів** - агенти можуть використовувати протоколи, такі як Agent-to-Agent (A2A) та Model Context Protocol (MCP), для виявлення та використання інших агентів і інструментів.
- **Плагінів і конекторів** - можливе підключення до сервісів даних і пам'яті, таких як Microsoft Fabric, SharePoint, Pinecone та Qdrant.

Давайте розглянемо, як ці функції застосовуються до деяких основних концепцій Microsoft Agent Framework.

## Ключові концепції Microsoft Agent Framework

### Агенти

![Agent Framework](../../../translated_images/uk/agent-components.410a06daf87b4fef.webp)

**Створення агентів**

Створення агента здійснюється шляхом визначення сервісу виведення (постачальника LLM), набору інструкцій для виконання AI-агентом та призначеного `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Вищенаведений приклад використовує `Azure OpenAI`, але агенти можуть створюватися за допомогою різних сервісів, включаючи `Microsoft Foundry Agent Service`:

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

або віддалені агенти, що використовують протокол A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Запуск агентів**

Агенти запускаються за допомогою методів `.run` або `.run_stream` для непотокових або потокових відповідей відповідно.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Кожен запуск агента також може мати параметри для налаштування таких опцій, як `max_tokens`, `tools`, які агент може викликати, і навіть сам `model`, що використовується агентом.

Це корисно у випадках, коли для виконання завдання користувача потрібні конкретні моделі або інструменти.

**Інструменти**

Інструменти можна визначати як під час створення агента:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# При створенні ChatAgent безпосередньо

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

так і під час запуску агента:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Інструмент надано лише для цього запуску )
```

**Потоки агента**

Потоки агента використовуються для обробки багатокрокових розмов. Потоки можна створити одним із таких способів:

- Використовуючи `get_new_thread()`, що дозволяє зберігати потік з часом
- Автоматично створюючи потік під час запуску агента, коли потік існує лише під час поточного запуску.

Щоб створити потік, код виглядає так:

```python
# Створіть новий потік.
thread = agent.get_new_thread() # Запустіть агента у цьому потоці.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Потім ви можете серіалізувати потік для зберігання і подальшого використання:

```python
# Створити новий потік.
thread = agent.get_new_thread() 

# Запустити агента в цьому потоці.

response = await agent.run("Hello, how are you?", thread=thread) 

# Серіалізувати потік для збереження.

serialized_thread = await thread.serialize() 

# Десеріалізувати стан потоку після завантаження зі сховища.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Проміжне програмне забезпечення агента**

Агенти взаємодіють з інструментами та LLM для виконання завдань користувачів. У певних сценаріях ми хочемо виконувати або відстежувати дії під час цих взаємодій. Проміжне програмне забезпечення агента дозволяє робити це через:

*Функціональне проміжне ПЗ*

Це проміжне ПЗ дозволяє виконати дію між агентом та функцією/інструментом, який він буде викликати. Приклад використання — коли потрібно зробити логування виклику функції.

У коді нижче `next` визначає, чи слід викликати наступне проміжне ПЗ або реальну функцію.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Попередня обробка: логування перед виконанням функції
    print(f"[Function] Calling {context.function.name}")

    # Продовжити до наступного проміжного обробника або виконання функції
    await next(context)

    # Пост-обробка: логування після виконання функції
    print(f"[Function] {context.function.name} completed")
```

*Чатове проміжне ПЗ*

Це проміжне ПЗ дозволяє виконувати або логувати дію між агентом та запитами до LLM.

Воно містить важливу інформацію, таку як `messages`, що надсилаються до AI-сервісу.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Попередня обробка: запис у журнал перед викликом ШІ
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Продовжити до наступного проміжного програмного забезпечення або сервісу ШІ
    await next(context)

    # Постобробка: запис у журнал після відповіді ШІ
    print("[Chat] AI response received")

```

**Пам'ять агента**

Як розглянуто в уроці `Agentic Memory`, пам'ять є важливим елементом для можливості агента працювати в різних контекстах. MAF пропонує декілька різних типів пам'яті:

*Зберігання в оперативній пам'яті*

Це пам'ять, що зберігається в потоках під час виконання додатка.

```python
# Створити новий потік.
thread = agent.get_new_thread() # Запустити агента у цьому потоці.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Постійні повідомлення*

Ця пам'ять використовується для збереження історії розмов між різними сесіями. Вона визначається за допомогою `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Створіть користувацьке сховище повідомлень
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Динамічна пам'ять*

Ця пам'ять додається до контексту перед запуском агентів. Такі пам'яті можуть зберігатися у зовнішніх сервісах, наприклад, mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Використання Mem0 для розширених можливостей пам'яті
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

**Спостережуваність агента**

Спостережуваність важлива для створення надійних і зручних у підтримці агентних систем. MAF інтегрується з OpenTelemetry для надання трасування та метрів для кращої спостережуваності.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # зробити щось
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Робочі процеси

MAF пропонує робочі процеси, які є попередньо визначеними кроками для виконання завдання і включають AI-агентів як компоненти цих кроків.

Робочі процеси складаються з різних компонентів, що дозволяють кращий контроль потоку. Робочі процеси також забезпечують **оркестрацію кількох агентів** та **контрольні точки (checkpointing)** для збереження станів робочого процесу.

Основні компоненти робочого процесу:

**Виконавці**

Виконавці отримують вхідні повідомлення, виконують призначені їм завдання, а потім генерують вихідне повідомлення. Це просуває робочий процес до завершення більшого завдання. Виконавцями можуть бути як AI-агенти, так і власна логіка.

**Зв'язки**

Зв'язки використовуються для визначення потоку повідомлень у робочому процесі. Вони можуть бути:

*Прямі зв'язки* - Просте з'єднання один-до-одного між виконавцями:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Умовні зв'язки* - Активуються після виконання певної умови. Наприклад, коли номери в готелях відсутні, виконавець може запропонувати інші варіанти.

*Перемикач-міст (switch-case) зв'язки* - Маршрутизують повідомлення до різних виконавців на основі визначених умов. Наприклад, якщо мандрівник має пріоритетний доступ, його завдання будуть оброблятися іншим робочим процесом.

*Розгалужувальні зв'язки (fan-out)* - Надсилають одне повідомлення до кількох цілей.

*Збиральні зв'язки (fan-in)* - Збирають кілька повідомлень від різних виконавців і надсилають їх до однієї цілі.

**Події**

Щоб забезпечити кращу спостережуваність робочих процесів, MAF пропонує вбудовані події виконання, зокрема:

- `WorkflowStartedEvent`  - Виконання робочого процесу починається
- `WorkflowOutputEvent` - Робочий процес створює вихід
- `WorkflowErrorEvent` - Робочий процес зазнає помилки
- `ExecutorInvokeEvent`  - Виконавець починає обробку
- `ExecutorCompleteEvent`  -  Виконавець завершує обробку
- `RequestInfoEvent` - Виконується запит

## Міграція з інших фреймворків (Semantic Kernel та AutoGen)

### Відмінності між MAF та Semantic Kernel

**Спрощене створення агентів**

Semantic Kernel покладається на створення екземпляра Kernel для кожного агента. MAF має спрощений підхід, використовуючи розширення для основних провайдерів.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Створення потоку агента**

У Semantic Kernel потоки потрібно створювати вручну. У MAF агенту безпосередньо призначається потік.

```python
thread = agent.get_new_thread() # Запустіть агента в потоці.
```

**Реєстрація інструментів**

У Semantic Kernel інструменти реєструються в Kernel, і Kernel потім передається агенту. У MAF інструменти реєструються безпосередньо під час створення агента.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Відмінності між MAF та AutoGen

**Teams vs Workflows**

`Teams` — це структура подій для подієво орієнтованої взаємодії з агентами в AutoGen. MAF використовує `Workflows`, які маршрутизують дані до виконавців через архітектуру на основі графа.

**Створення інструментів**

AutoGen використовує `FunctionTool` для обгортання функцій, які агенти можуть викликати. MAF використовує @ai_function, який працює подібно, але також автоматично виводить схеми для кожної функції.

**Поведінка агента**

Агенти за замовчуванням у AutoGen — це одноразові агенти (single-turn), якщо не встановлено `max_tool_iterations` на більше значення. У MAF `ChatAgent` за замовчуванням багатокроковий (multi-turn), тобто він буде продовжувати викликати інструменти, поки завдання користувача не буде виконано.

## Приклади коду 

Приклади коду для Microsoft Agent Framework можна знайти в цьому репозиторії у файлах `xx-python-agent-framework` та `xx-dotnet-agent-framework`.

## Маєте ще питання про Microsoft Agent Framework?

Приєднуйтесь до [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) щоб зустрітися з іншими учнями, відвідати офіс-години та отримати відповіді на свої питання про AI-агентів.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Відмова від відповідальності**:
Цей документ було перекладено за допомогою сервісу автоматичного перекладу на базі штучного інтелекту [Co-op Translator](https://github.com/Azure/co-op-translator). Хоч ми й прагнемо до точності, майте на увазі, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ його рідною мовою слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується професійний переклад, виконаний людиною. Ми не несемо відповідальності за будь-які непорозуміння чи неправильні тлумачення, що виникли внаслідок використання цього перекладу.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->