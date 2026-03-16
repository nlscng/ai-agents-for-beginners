[![Як проектувати хороших агентів ШІ](../../../translated_images/uk/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Клацніть зображення вище, щоб переглянути відео цього уроку)_

# Патерн використання інструментів

Інструменти цікаві тим, що вони дають агентам ШІ ширший спектр можливостей. Замість того, щоб агент мав обмежений набір дій, які він може виконувати, додавання інструмента дозволяє агенту виконувати набагато ширший діапазон дій. У цьому розділі ми розглянемо Патерн використання інструментів, який описує, як агенти ШІ можуть використовувати конкретні інструменти для досягнення своїх цілей.

## Вступ

У цьому уроці ми прагнемо відповісти на такі питання:

- Що таке патерн використання інструментів?
- У яких випадках його можна застосовувати?
- Які елементи/будівельні блоки потрібні для реалізації патерну?
- Які особливі міркування слід враховувати при використанні Патерну використання інструментів для побудови надійних агентів ШІ?

## Цілі навчання

Після завершення цього уроку ви зможете:

- Визначити Патерн використання інструментів та його призначення.
- Виявити випадки застосування, де Патерн використання інструментів є доречним.
- Зрозуміти ключові елементи, необхідні для реалізації патерну.
- Визнати міркування для забезпечення надійності агентів ШІ, що використовують цей патерн.

## Що таке Патерн використання інструментів?

Патерн використання інструментів зосереджений на наданні можливості великим мовним моделям (LLM) взаємодіяти з зовнішніми інструментами для досягнення конкретних цілей. Інструменти — це код, який агент може виконати для виконання дій. Інструментом може бути проста функція, така як калькулятор, або виклик API до стороннього сервісу, наприклад, перевірка ціни акцій або прогноз погоди. У контексті агентів ШІ інструменти розроблені для виконання агентами у відповідь на модель-згенеровані виклики функцій.

## Для яких випадків використання його можна застосувати?

Агенти ШІ можуть використовувати інструменти для виконання складних завдань, отримання інформації або прийняття рішень. Патерн використання інструментів часто застосовується в сценаріях, що вимагають динамічної взаємодії із зовнішніми системами, такими як бази даних, веб-сервіси або інтерпретатори коду. Ця здатність корисна для низки різних випадків використання, зокрема:

- **Динамічне отримання інформації:** Агенти можуть запитувати зовнішні API або бази даних, щоб отримати актуальні дані (наприклад, виконати запит до SQLite для аналізу даних, отримати ціну акцій або інформацію про погоду).
- **Виконання та інтерпретація коду:** Агенти можуть виконувати код або скрипти для вирішення математичних задач, генерації звітів або проведення симуляцій.
- **Автоматизація робочих процесів:** Автоматизація повторюваних або багатокрокових робочих процесів шляхом інтеграції інструментів, таких як планувальники завдань, служби електронної пошти або конвеєри даних.
- **Підтримка клієнтів:** Агенти можуть взаємодіяти зі CRM-системами, платформами для обробки запитів або базами знань для вирішення запитів користувачів.
- **Генерація та редагування контенту:** Агенти можуть використовувати інструменти, такі як перевірка граматики, скорочувачі тексту або оцінювачі безпеки контенту, щоб допомогти в завданнях створення контенту.

## Які елементи/будівельні блоки потрібні для реалізації патерну використання інструментів?

Ці будівельні блоки дозволяють агенту ШІ виконувати широкий спектр завдань. Розглянемо ключові елементи, необхідні для реалізації Патерну використання інструментів:

- **Схеми функцій/інструментів**: Детальні визначення доступних інструментів, включаючи назву функції, призначення, необхідні параметри та очікувані виходи. Ці схеми дозволяють LLM розуміти, які інструменти доступні і як сформувати дійсні запити.

- **Логіка виконання функцій**: Визначає, як і коли інструменти викликаються залежно від наміру користувача та контексту розмови. Це може включати модулі планування, механізми маршрутизації або умовні потоки, що динамічно визначають використання інструментів.

- **Система обробки повідомлень**: Компоненти, що керують потоками розмов між запитами користувача, відповідями LLM, викликами інструментів та їхніми результатами.

- **Фреймворк інтеграції інструментів**: Інфраструктура, яка підключає агента до різних інструментів, незалежно від того, чи це прості функції, чи складні зовнішні служби.

- **Обробка помилок та валідація**: Механізми для обробки збоїв при виконанні інструментів, перевірки параметрів і управління неочікуваними відповідями.

- **Управління станом**: Відстежує контекст розмови, попередні взаємодії з інструментами та постійні дані, щоб забезпечити узгодженість під час багатокрокових взаємодій.

Далі розглянемо Виклик функцій/інструментів детальніше.
 
### Виклик функцій/інструментів

Виклик функцій — це основний спосіб, яким ми надаємо Великим мовним моделям (LLM) можливість взаємодіяти з інструментами. Ви часто зустрічатимете терміни «Функція» та «Інструмент», що використовуються взаємозамінно, оскільки «функції» (блоки повторно використовуваного коду) — це ті «інструменти», які агенти використовують для виконання завдань. Для того щоб код функції було викликано, LLM має порівняти запит користувача з описом функцій. Для цього схема, що містить описи всіх доступних функцій, надсилається до LLM. LLM потім вибирає найбільш відповідну функцію для завдання і повертає її назву та аргументи. Обрану функцію викликають, її відповідь надсилають назад до LLM, який використовує цю інформацію, щоб відповісти на запит користувача.

Щоб розробники могли реалізувати виклик функцій для агентів, вам знадобиться:

1. Модель LLM, яка підтримує виклик функцій
2. Схема, що містить описи функцій
3. Код для кожної описаної функції

Використаємо приклад отримання поточного часу в місті для ілюстрації:

1. **Ініціалізуйте LLM, що підтримує виклик функцій:**

    Не всі моделі підтримують виклик функцій, тому важливо перевірити, чи підтримує це використовувана вами модель.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> підтримує виклик функцій. Ми можемо почати з ініціалізації клієнта Azure OpenAI. 

    ```python
    # Ініціалізувати клієнта Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Створіть схему функції**:

    Далі ми визначимо JSON-схему, яка містить назву функції, опис того, що робить функція, та назви й описи параметрів функції.
    Потім ми передамо цю схему клієнту, створеному раніше, разом із запитом користувача знайти час у Сан-Франциско. Важливо зазначити, що **інструментальний виклик** — це те, що повертається, **а не** остаточна відповідь на питання. Як уже зазначалося, LLM повертає назву функції, яку він обрав для завдання, та аргументи, які будуть передані їй.

    ```python
    # Опис функції для того, щоб модель могла її прочитати
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # Початкове повідомлення користувача
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Перший виклик API: Попросіть модель використати функцію
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Обробити відповідь моделі
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Код функції, необхідний для виконання завдання:**

    Тепер, коли LLM вибрала, яку функцію потрібно виконати, необхідно реалізувати та виконати код, що виконує завдання.
    Ми можемо реалізувати код для отримання поточного часу на Python. Також нам потрібно написати код для вилучення назви та аргументів з response_message, щоб отримати остаточний результат.

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # Обробка викликів функцій
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # Другий виклик API: Отримати остаточну відповідь від моделі
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

Виклик функцій є в основі більшості, якщо не всіх, реалізацій патерну використання інструментів для агентів, однак реалізувати його з нуля іноді може бути складно.
Як ми дізналися в [Уроці 2](../../../02-explore-agentic-frameworks), агентні фреймворки надають нам готові будівельні блоки для реалізації використання інструментів.
 
## Приклади використання інструментів з агентними фреймворками

Ось кілька прикладів того, як ви можете реалізувати Патерн використання інструментів, використовуючи різні агентні фреймворки:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> — це фреймворк з відкритим кодом для розробників на .NET, Python та Java, які працюють з Великими мовними моделями (LLM). Він спрощує процес використання виклику функцій, автоматично описуючи ваші функції та їхні параметри моделі через процес, який називається <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">серіалізацією</a>. Він також обробляє двосторонню комунікацію між моделлю та вашим кодом. Ще одна перевага використання агентного фреймворку, такого як Semantic Kernel, полягає в тому, що він дозволяє отримати доступ до готових інструментів, таких як <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> та <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Наступна діаграма ілюструє процес виклику функцій із Semantic Kernel:

![function calling](../../../translated_images/uk/functioncalling-diagram.a84006fc287f6014.webp)

У Semantic Kernel функції/інструменти називаються <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">плагінами</a>. Ми можемо перетворити функцію `get_current_time`, яку бачили раніше, на плагін, перетворивши її на клас із цією функцією всередині. Ми також можемо імпортувати декоратор `kernel_function`, який приймає опис функції. Коли ви потім створюєте kernel з GetCurrentTimePlugin, kernel автоматично сериалізує функцію та її параметри, створюючи схему для відправки до LLM у процесі.

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# Створити ядро
kernel = Kernel()

# Створити плагін
get_current_time_plugin = GetCurrentTimePlugin(location)

# Додати плагін до ядра
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> — це новіший агентний фреймворк, створений, щоб надати розробникам можливість безпечно створювати, розгортати та масштабувати високоякісні та розширювані агенти ШІ, не потребуючи керувати базовими ресурсами обчислення та зберігання. Він особливо корисний для корпоративних застосунків, оскільки є повністю керованим сервісом з рівнем безпеки на рівні підприємства.

У порівнянні з розробкою безпосередньо з API LLM, Azure AI Agent Service надає певні переваги, зокрема:

- Автоматичний виклик інструментів — нема потреби розбирати виклик інструмента, викликати інструмент і обробляти відповідь; усе це тепер виконується на серверній стороні
- Безпечно керовані дані — замість управління власним станом розмови, ви можете покладатися на threads для збереження всієї необхідної інформації
- Інструменти «з коробки» — інструменти, які ви можете використовувати для взаємодії з джерелами даних, такі як Bing, Azure AI Search та Azure Functions.

Інструменти, доступні в Azure AI Agent Service, можна поділити на дві категорії:

1. Інструменти знань:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Інструменти дій:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service дозволяє нам використовувати ці інструменти разом як `toolset`. Він також використовує `threads`, які відстежують історію повідомлень із певної розмови.

Уявіть, що ви торговий агент у компанії під назвою Contoso. Ви хочете розробити розмовного агента, який може відповідати на питання про ваші дані продажів.

Наступне зображення ілюструє, як ви могли б використовувати Azure AI Agent Service для аналізу ваших даних продажів:

![Agentic Service In Action](../../../translated_images/uk/agent-service-in-action.34fb465c9a84659e.webp)

Щоб використовувати будь-який із цих інструментів зі сервісом, ми можемо створити клієнта і визначити інструмент або набір інструментів. Для практичної реалізації ми можемо використати наведений нижче код на Python. LLM зможе переглянути toolset і вирішити, чи використовувати користувацьку функцію `fetch_sales_data_using_sqlite_query`, чи готовий Code Interpreter залежно від запиту користувача.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # функція fetch_sales_data_using_sqlite_query, яку можна знайти у файлі fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Ініціалізувати набір інструментів
toolset = ToolSet()

# Ініціалізувати агента для виклику функцій з функцією fetch_sales_data_using_sqlite_query та додати його до набору інструментів
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Ініціалізувати інструмент Code Interpreter та додати його до набору інструментів
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Які особливі міркування слід враховувати при використанні Патерну використання інструментів для побудови надійних агентів ШІ?

Загальною проблемою при динамічно згенерованому LLM SQL є безпека, зокрема ризик SQL-ін'єкцій або шкідливих дій, таких як видалення або пошкодження бази даних. Хоча ці занепокоєння є обґрунтованими, їх можна ефективно пом’якшити належною конфігурацією прав доступу до бази даних. Для більшості баз даних це передбачає налаштування бази даних у режимі лише для читання. Для сервісів баз даних на кшталт PostgreSQL або Azure SQL додатку слід призначити роль лише для читання (SELECT).

Запуск додатка в безпечному середовищі додатково підвищує захист. У корпоративних сценаріях дані зазвичай витягують і трансформують з оперативних систем у базу даних лише для читання або сховище даних зі зручною схемою. Такий підхід гарантує, що дані захищені, оптимізовані для продуктивності та доступності, і що додаток має обмежений доступ лише для читання.

## Приклади коду
- Python: [Фреймворк агента](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Фреймворк агента](./code_samples/04-dotnet-agent-framework.md)

## Маєте ще питання щодо шаблонів використання інструментів?

Приєднуйтесь до [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), щоб зустрітися з іншими учнями, відвідати години консультацій і отримати відповіді на свої питання щодо AI-агентів.

## Додаткові ресурси

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Воркшоп Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Мультиагентний воркшоп Contoso Creative Writer</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Підручник з виклику функцій у Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Інтерпретатор коду Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Інструменти Autogen</a>

## Попередній урок

[Розуміння агентних шаблонів проєктування](../03-agentic-design-patterns/README.md)

## Наступний урок

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Відмова від відповідальності:
Цей документ було перекладено за допомогою сервісу перекладу на базі ШІ Co-op Translator (https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, зверніть увагу, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ його рідною мовою слід вважати авторитетним джерелом. Для критичної інформації рекомендується скористатися послугами професійного перекладача. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->