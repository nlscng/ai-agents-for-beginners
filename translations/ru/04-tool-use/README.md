[![Как проектировать хороших агентов ИИ](../../../translated_images/ru/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Нажмите на изображение выше, чтобы посмотреть видео этого урока)_

# Паттерн использования инструментов

Инструменты интересны тем, что они позволяют агентам ИИ обладать более широким набором возможностей. Вместо того, чтобы агент имел ограниченный набор действий, которые он может выполнять, добавляя инструмент, агент теперь может выполнять широкий спектр действий. В этой главе мы рассмотрим паттерн использования инструментов, который описывает, как агенты ИИ могут использовать конкретные инструменты для достижения своих целей.

## Введение

В этом уроке мы постараемся ответить на следующие вопросы:

- Что такое паттерн использования инструментов?
- Для каких сценариев его можно применить?
- Какие элементы/строительные блоки необходимы для реализации паттерна?
- Какие специальные соображения существуют при использовании паттерна использования инструментов для создания заслуживающих доверия агентов ИИ?

## Цели обучения

После завершения этого урока вы сможете:

- Определить паттерн использования инструментов и его назначение.
- Определить случаи использования, где применим паттерн использования инструментов.
- Понять ключевые элементы, необходимые для реализации паттерна.
- Распознать аспекты обеспечения надежности агентов ИИ, использующих этот паттерн.

## Что такое паттерн использования инструментов?

Паттерн использования инструментов делает акцент на предоставлении LLM возможности взаимодействовать с внешними инструментами для достижения конкретных целей. Инструменты — это код, который агент может выполнить для выполнения действий. Инструментом может быть простая функция, такая как калькулятор, или вызов API к стороннему сервису, например, получение цены акций или прогноза погоды. В контексте агентов ИИ инструменты разработаны для выполнения агентами в ответ на **сгенерированные моделью вызовы функций**.

## Для каких сценариев его можно применить?

Агенты ИИ могут использовать инструменты для выполнения сложных задач, получения информации или принятия решений. Паттерн использования инструментов часто применяется в сценариях, требующих динамического взаимодействия с внешними системами, такими как базы данных, веб-сервисы или интерпретаторы кода. Эта возможность полезна для ряда различных случаев использования, включая:

- **Динамический сбор информации:** агенты могут запрашивать внешние API или базы данных, чтобы получить актуальные данные (например, запрос к базе данных SQLite для анализа данных, получение цен на акции или информации о погоде).
- **Выполнение и интерпретация кода:** агенты могут выполнять код или скрипты для решения математических задач, генерации отчетов или проведения симуляций.
- **Автоматизация рабочих процессов:** автоматизация повторяющихся или многошаговых процессов путем интеграции инструментов, таких как планировщики задач, службы электронной почты или конвейеры данных.
- **Поддержка клиентов:** агенты могут взаимодействовать с CRM-системами, платформами тикетов или базами знаний для разрешения пользовательских запросов.
- **Создание и редактирование контента:** агенты могут использовать инструменты, такие как проверка грамматики, суммаризация текста или оценщики безопасности контента, чтобы помогать в задачах создания контента.

## Какие элементы/строительные блоки необходимы для реализации паттерна использования инструментов?

Эти строительные блоки позволяют агенту ИИ выполнять широкий круг задач. Рассмотрим ключевые элементы, необходимые для реализации паттерна использования инструментов:

- **Схемы функций/инструментов:** подробные определения доступных инструментов, включая имя функции, назначение, обязательные параметры и ожидаемые результаты. Эти схемы позволяют LLM понять, какие инструменты доступны и как формировать корректные запросы.

- **Логика выполнения функций:** управляет тем, как и когда инструменты вызываются на основе намерений пользователя и контекста разговора. Это может включать модули планирования, механизмы маршрутизации или условные потоки, которые динамически определяют использование инструментов.

- **Система обработки сообщений:** компоненты, которые управляют разговорным потоком между вводом пользователя, ответами LLM, вызовами инструментов и результатами инструментов.

- **Фреймворк интеграции инструментов:** инфраструктура, которая подключает агента к различным инструментам, будь то простые функции или сложные внешние сервисы.

- **Обработка ошибок и валидация:** механизмы для обработки сбоев при выполнении инструментов, валидации параметров и управления неожиданными ответами.

- **Управление состоянием:** отслеживает контекст разговора, предыдущие взаимодействия с инструментами и постоянные данные, чтобы обеспечить согласованность в многошаговых взаимодействиях.

Далее рассмотрим вызов функций/инструментов более подробно.
 
### Вызов функций/инструментов

Вызов функций — это основной способ, с помощью которого мы даем возможность крупным языковым моделям (LLM) взаимодействовать с инструментами. Вы часто увидите, что «Function» и «Tool» используются взаимозаменяемо, потому что «functions» (блоки повторно используемого кода) — это «инструменты», которые агенты используют для выполнения задач. Чтобы код функции был вызван, LLM должен сопоставить запрос пользователя с описанием функций. Для этого схема, содержащая описания всех доступных функций, отправляется в LLM. Затем LLM выбирает наиболее подходящую функцию для задачи и возвращает ее имя и аргументы. Выбранная функция вызывается, ее ответ отправляется обратно в LLM, который использует полученную информацию для ответа на запрос пользователя.

Чтобы разработчики реализовали вызов функций для агентов, потребуется:

1. Модель LLM, которая поддерживает вызов функций
2. Схема, содержащая описания функций
3. Код для каждой описанной функции

Рассмотрим пример получения текущего времени в городе:

1. **Инициализировать LLM, который поддерживает вызов функций:**

    Не все модели поддерживают вызов функций, поэтому важно проверить, что используемая вами LLM это поддерживает.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> поддерживает вызов функций. Мы можем начать с инициализации клиента Azure OpenAI. 

    ```python
    # Инициализировать клиента Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Создать схему функции**:

    Далее мы определим JSON-схему, которая содержит имя функции, описание того, что функция делает, и имена и описания параметров функции.
    Затем мы передадим эту схему клиенту, созданному ранее, вместе с запросом пользователя о времени в Сан-Франциско. Важно отметить, что **возвращается вызов инструмента**, **а не** окончательный ответ на вопрос. Как упоминалось ранее, LLM возвращает имя функции, выбранной для задачи, и аргументы, которые будут ей переданы.

    ```python
    # Описание функции для чтения моделью
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
  
    # Исходное сообщение пользователя
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Первый вызов API: Попросить модель использовать функцию
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Обработать ответ модели
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Код функции, необходимый для выполнения задачи:**

    Теперь, когда LLM выбрала, какая функция должна быть запущена, необходимо реализовать и выполнить код, выполняющий задачу.
    Мы можем реализовать код для получения текущего времени на Python. Нам также потребуется написать код для извлечения имени и аргументов из response_message, чтобы получить окончательный результат.

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
     # Обрабатывать вызовы функций
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
  
      # Второй запрос к API: получить окончательный ответ от модели
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

Вызов функций лежит в основе большинства, если не всех, стратегий использования инструментов в дизайне агентов, однако реализация этого с нуля иногда может быть сложной.
Как мы узнали в [Lesson 2](../../../02-explore-agentic-frameworks) агентные фреймворки предоставляют нам готовые строительные блоки для реализации использования инструментов.
 
## Примеры использования инструментов с агентными фреймворками

Ниже приведены примеры того, как вы можете реализовать паттерн использования инструментов с помощью разных агентных фреймворков:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> — это фреймворк с открытым исходным кодом для разработчиков на .NET, Python и Java, работающих с крупными языковыми моделями (LLM). Он упрощает процесс использования вызова функций, автоматически описывая ваши функции и их параметры модели через процесс, называемый <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">сериализацией</a>. Он также обрабатывает двустороннюю коммуникацию между моделью и вашим кодом. Еще одним преимуществом использования агентного фреймворка, такого как Semantic Kernel, является то, что он позволяет получить доступ к готовым инструментам, таким как <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> и <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Следующая диаграмма иллюстрирует процесс вызова функций с Semantic Kernel:

![вызов функции](../../../translated_images/ru/functioncalling-diagram.a84006fc287f6014.webp)

В Semantic Kernel функции/инструменты называются <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. Мы можем преобразовать функцию `get_current_time`, которую видели ранее, в плагин, превратив её в класс с этой функцией внутри. Мы также можем импортировать декоратор `kernel_function`, который принимает описание функции. Когда вы затем создаете kernel с GetCurrentTimePlugin, kernel автоматически сериализует функцию и её параметры, создавая схему для отправки в LLM в процессе.

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

# Создать ядро
kernel = Kernel()

# Создать плагин
get_current_time_plugin = GetCurrentTimePlugin(location)

# Добавить плагин в ядро
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> — это более новый агентный фреймворк, разработанный для того, чтобы дать разработчикам возможность безопасно создавать, развертывать и масштабировать качественных и расширяемых агентов ИИ без необходимости управлять базовыми вычислительными и хранилищными ресурсами. Он особенно полезен для корпоративных приложений, поскольку является полностью управляемым сервисом с корпоративным уровнем безопасности.

По сравнению с разработкой с использованием LLM API напрямую, Azure AI Agent Service предоставляет некоторые преимущества, в том числе:

- Автоматический вызов инструментов — нет необходимости анализировать вызов инструмента, вызывать инструмент и обрабатывать ответ; все это теперь выполняется на стороне сервера
- Безопасно управляемые данные — вместо управления собственным состоянием разговора вы можете полагаться на threads для хранения всей необходимой информации
- Инструменты из коробки — инструменты, которые можно использовать для взаимодействия с вашими источниками данных, такие как Bing, Azure AI Search и Azure Functions.

Инструменты, доступные в Azure AI Agent Service, можно разделить на две категории:

1. Инструменты знаний:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Инструменты действий:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service позволяет нам использовать эти инструменты вместе как `toolset`. Он также использует `threads`, которые отслеживают историю сообщений конкретного разговора.

Представьте, что вы торговый представитель в компании под названием Contoso. Вы хотите разработать разговорного агента, который может отвечать на вопросы о ваших данных о продажах.

Следующее изображение иллюстрирует, как можно использовать Azure AI Agent Service для анализа данных о продажах:

![Agentic Service In Action](../../../translated_images/ru/agent-service-in-action.34fb465c9a84659e.webp)

Чтобы использовать любой из этих инструментов с сервисом, мы можем создать клиент и определить инструмент или набор инструментов. Для практической реализации мы можем использовать следующий код на Python. LLM сможет просмотреть toolset и решить, использовать ли пользовательскую функцию `fetch_sales_data_using_sqlite_query` или предустановленный Code Interpreter в зависимости от запроса пользователя.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # Функция fetch_sales_data_using_sqlite_query, которую можно найти в файле fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Инициализировать набор инструментов
toolset = ToolSet()

# Инициализировать агент вызова функций с функцией fetch_sales_data_using_sqlite_query и добавить его в набор инструментов
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Инициализировать инструмент Code Interpreter и добавить его в набор инструментов.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Какие специальные соображения существуют при использовании паттерна использования инструментов для создания заслуживающих доверия агентов ИИ?

Распространенная проблема с динамически генерируемым SQL от LLM — это безопасность, в частности риск SQL-инъекций или злонамеренных действий, таких как удаление или искажение базы данных. Хотя эти опасения обоснованы, их можно эффективно смягчить путем правильной настройки прав доступа к базе данных. Для большинства баз данных это включает настройку базы данных в режиме только для чтения. Для сервисов баз данных, таких как PostgreSQL или Azure SQL, приложению следует назначить роль только для чтения (SELECT).

Запуск приложения в безопасной среде дополнительно повышает защиту. В корпоративных сценариях данные обычно извлекают и преобразуют из операционных систем в базу данных или хранилище данных только для чтения с удобной схемой. Этот подход обеспечивает безопасность данных, оптимизацию производительности и доступности, а также ограниченный доступ приложения в режиме только для чтения.

## Примеры кода
- Python: [Фреймворк агентов](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Фреймворк агентов](./code_samples/04-dotnet-agent-framework.md)

## Есть ещё вопросы о шаблонах проектирования использования инструментов?

Присоединяйтесь к [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), чтобы встретиться с другими учащимися, посетить часы консультаций и получить ответы на ваши вопросы по AI Agents.

## Дополнительные ресурсы

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Мастерская Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Мастерская Contoso Creative Writer с несколькими агентами</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Учебник по вызову функций Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Интерпретатор кода Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Инструменты Autogen</a>

## Предыдущий урок

[Понимание агентных шаблонов проектирования](../03-agentic-design-patterns/README.md)

## Следующий урок

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Отказ от ответственности:
Этот документ был переведён с помощью сервиса автоматического перевода на базе ИИ [Co-op Translator](https://github.com/Azure/co-op-translator). Хотя мы стремимся к точности, имейте в виду, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его исходном языке следует считать авторитетным источником. Для критически важной информации рекомендуется воспользоваться услугами профессионального переводчика. Мы не несем ответственности за любые недоразумения или искажения смысла, возникшие в результате использования данного перевода.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->