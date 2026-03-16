[![Как да проектираме добри AI агенти](../../../translated_images/bg/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Кликнете върху изображението по-горе, за да гледате видеото на този урок)_

# Дизайнерски модел за използване на инструменти

Инструментите са интересни, защото позволяват на AI агентите да имат по-широк спектър от възможности. Вместо агентът да разполага с ограничен набор от действия, които може да изпълнява, чрез добавянето на инструмент, агентът вече може да изпълнява широк кръг действия. В тази глава ще разгледаме Дизайнерския модел за използване на инструменти, който описва как AI агентите могат да използват специфични инструменти, за да постигнат целите си.

## Въведение

В този урок ще се опитаме да отговорим на следните въпроси:

- Какво е дизайнерският модел за използване на инструменти?
- За какви случаи на употреба може да се прилага?
- Какви са елементите/строителните блокове, необходими за реализирането на модела?
- Какви са специалните съображения при използването на дизайнерския модел за използване на инструменти, за да се изградят надеждни AI агенти?

## Учебни цели

След завършване на този урок ще можете да:

- Дефинирате дизайнерския модел за използване на инструменти и неговата цел.
- Идентифицирате случаи на употреба, в които този модел е приложим.
- Разбирате ключовите елементи, необходими за изграждането на модела.
- Разпознавате съображения за осигуряване на надеждност при AI агенти, използващи този дизайнерски модел.

## Какво е дизайнерският модел за използване на инструменти?

**Дизайнерският модел за използване на инструменти** се фокусира върху даването на възможност на големите езикови модели (LLM) да взаимодействат с външни инструменти за постигане на конкретни цели. Инструментите са код, който може да бъде изпълнен от агент, за да извърши действия. Инструментът може да бъде проста функция, като калкулатор, или повикване на API към трета страна, например за търсене на цена на акция или прогноза за времето. В контекста на AI агентите, инструментите са проектирани да се изпълняват от агентите в отговор на **генерирани от модела повиквания на функции**.

## За какви случаи на употреба може да се прилага?

AI агентите могат да използват инструменти за изпълнение на сложни задачи, извличане на информация или вземане на решения. Дизайнерският модел за използване на инструменти често се прилага в сценарии, изискващи динамично взаимодействие с външни системи, като бази данни, уеб услуги или интерпретатори на код. Тази способност е полезна за редица различни случаи, включително:

- **Динамично извличане на информация:** Агентите могат да запитват външни API или бази данни за актуални данни (например, заявки към SQLite база за анализ на данни, получаване на цени на акции или информация за времето).
- **Изпълнение и интерпретиране на код:** Агентите могат да изпълняват код или скриптове за решаване на математически задачи, генериране на отчети или провеждане на симулации.
- **Автоматизация на работни процеси:** Автоматизиране на повтарящи се или многостъпкови работни процеси чрез интегриране на инструменти като планиращи задачи, имейл услуги или конвейери за данни.
- **Поддръжка на клиенти:** Агентите могат да взаимодействат с CRM системи, платформи за тикети или бази знания, за да решават запитвания на потребители.
- **Генериране и редакция на съдържание:** Агентите могат да използват инструменти като граматически проверяващи, обобщители на текст или оценители за безопасност на съдържанието, за да помагат при задачи за създаване на съдържание.

## Какви са елементите/строителните блокове, необходими за реализиране на дизайнерския модел за използване на инструменти?

Тези строителни блокове позволяват на AI агента да изпълнява широк набор от задачи. Нека разгледаме ключовите елементи, необходими за реализирането на Дизайнерския модел за използване на инструменти:

- **Схеми на функции/инструменти:** Подробни дефиниции на наличните инструменти, включително име на функцията, цел, необходими параметри и очаквани изходи. Тези схеми позволяват на LLM да разбере какви инструменти са налични и как да изгради валидни заявки.

- **Логика за изпълнение на функции:** Управлява кога и как се извикват инструментите в зависимост от намеренията на потребителя и контекста на разговора. Това може да включва модули за планиране, механизми за маршрутизиране или условни потоци, които динамично определят използването на инструменти.

- **Система за обработка на съобщения:** Компоненти, които управляват разговорния поток между входовете на потребителя, отговорите от LLM, повикванията към инструменти и изходите от тях.

- **Интеграционна рамка за инструменти:** Инфраструктура, която свързва агента с различни инструменти, независимо дали са прости функции или сложни външни услуги.

- **Обработка на грешки и валидация:** Механизми за справяне с неуспехи при изпълнение на инструменти, валидиране на параметрите и управление на неочаквани отговори.

- **Управление на състоянието:** Следи контекста на разговора, предходните взаимодействия с инструменти и постоянни данни, за да осигури последователност през многократни стъпки.

След това нека разгледаме по-подробно повикванията на функции/инструменти.
 
### Повикване на функции/инструменти

Повикването на функции е основният начин, по който позволяваме на големите езикови модели (LLM) да взаимодействат с инструменти. Често ще забележите, че 'Функция' и 'Инструмент' се използват взаимозаменяемо, тъй като 'функциите' (блокове многократно използваем код) са 'инструментите', които агентите използват за изпълнение на задачи. За да бъде извикан кодът на функция, LLM трябва да сравни заявката на потребителя с описанието на функциите. За целта се изпраща схема, съдържаща описанията на всички налични функции към LLM. След това LLM избира най-подходящата функция за задачата и връща нейното име и аргументи. Избраната функция се извиква, получената отговорна информация се връща обратно към LLM, който използва тази информация, за да отговори на заявката на потребителя.

За да реализирате повикване на функции за агенти, ще ви трябват:

1. Модел LLM, който поддържа повикване на функции
2. Схема, съдържаща описания на функциите
3. Кодът за всяка описана функция

Да използваме примера с получаване на текущото време в град, за да илюстрираме:

1. **Инициализирайте LLM, който поддържа повикване на функции:**

    Не всички модели поддържат повикване на функции, така че е важно да проверите дали използваният от вас LLM го прави. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> поддържа повикване на функции. Можем да започнем, като инициираме клиента на Azure OpenAI. 

    ```python
    # Инициализиране на клиента Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Създаване на схема на функция:**

    След това ще дефинираме JSON схема, която съдържа името на функцията, описание на това какво прави функцията и имената и описанията на параметрите на функцията.
    След това ще предадем тази схема на клиента, създаден по-рано, заедно със заявката на потребителя за установяване на времето в Сан Франциско. Важно е да се отбележи, че се връща **повикване на инструмент**, **а не** крайният отговор на въпроса. Както беше споменато по-рано, LLM връща името на функцията, избрана за задачата, и аргументите, които ще бъдат предадени на нея.

    ```python
    # Описание на функцията за модела да прочете
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
  
    # Първоначално съобщение от потребителя
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Първо API обаждане: Помолете модела да използва функцията
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Обработете отговора на модела
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Кодът на функцията, необходим за изпълнение на задачата:**

    След като LLM е избрал коя функция трябва да бъде изпълнена, трябва да се реализира и изпълни кодът, който извършва задачата.
    Можем да реализираме кода за получаване на текущото време на Python. Също така ще трябва да напишем код, който извлича името и аргументите от response_message, за да получим крайния резултат.

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
     # Обработване на извиквания на функции
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
  
      # Второ API повикване: Получаване на крайния отговор от модела
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

Повикването на функции е в основата на повечето, ако не и на всички дизайнерски модели за използване на инструменти от агенти, но реализирането му от нулата понякога може да бъде предизвикателно.
Както научихме в [Урок 2](../../../02-explore-agentic-frameworks), агентните рамки ни предоставят предварително изградени строителни блокове за реализиране на използването на инструменти.
 
## Примери за използване на инструменти с агентни рамки

Ето няколко примера как можете да реализирате Дизайнерския модел за използване на инструменти с различни агентни рамки:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> е отворен AI фреймуърк за разработчици на .NET, Python и Java, работещи с големи езикови модели (LLM). Той опростява процеса на използване на повикване на функции, като автоматично описва вашите функции и техните параметри на модела чрез процес, наречен <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">сериализация</a>. Освен това управлява двупосочната комуникация между модела и вашия код. Друга полза от използването на агентна рамка като Semantic Kernel е, че позволява достъп до предварително изградени инструменти като <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Търсене на файлове</a> и <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Интерпретатор на код</a>.

Следната диаграма илюстрира процеса на повикване на функции с Semantic Kernel:

![function calling](../../../translated_images/bg/functioncalling-diagram.a84006fc287f6014.webp)

В Semantic Kernel функциите/инструментите се наричат <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Плъгини</a>. Можем да превърнем функцията `get_current_time`, която видяхме по-рано, в плъгин, като я направим клас с функцията вътре. Също така можем да импортираме декоратора `kernel_function`, който приема описанието на функцията. Когато създадете kernel с GetCurrentTimePlugin, kernel автоматично сериализира функцията и нейните параметри, като създава схемата за изпращане към LLM в процеса.

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

# Създайте ядрото
kernel = Kernel()

# Създайте приставката
get_current_time_plugin = GetCurrentTimePlugin(location)

# Добавете приставката към ядрото
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> е по-нова агентна рамка, предназначена да даде възможност на разработчиците да изграждат, внедряват и мащабират сигурно висококачествени и разширяеми AI агенти без необходимост да управляват базовите изчислителни и съхранителни ресурси. Особено полезен е за корпоративни приложения, тъй като е напълно управлявана услуга с корпоративно ниво на сигурност.

В сравнение с директното разработване чрез LLM API, Azure AI Agent Service предлага някои предимства, включително:

- Автоматично повикване на инструменти – няма нужда да се парсира повикване на инструмент, да се извиква инструментът и да се обработва отговорът; всичко това се извършва вече на сървърна страна
- Сигурно управлявани данни – вместо да управлявате собственото си състояние на разговора, можете да разчитате на нишки (threads), които съхраняват цялата необходима информация
- Вградени инструменти – инструменти, които можете да използвате за взаимодействие с вашите източници на данни, като Bing, Azure AI Search и Azure Functions.

Инструментите, налични в Azure AI Agent Service, могат да се разделят на две категории:

1. Инструменти за знания:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Свързване с търсене Bing</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Търсене на файлове</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Инструменти за действия:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Повикване на функции</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Интерпретатор на код</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">Инструменти, дефинирани чрез OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service ни позволява да използваме тези инструменти заедно като `toolset`. Също така използва `нишки` (threads), които следят историята на съобщенията от даден разговор.

Представете си, че сте търговски агент в компания, наречена Contoso. Искате да разработите разговорен агент, който може да отговаря на въпроси относно вашите данни за продажбите.

Следното изображение илюстрира как можете да използвате Azure AI Agent Service, за да анализирате данните си за продажбите:

![Agentic Service In Action](../../../translated_images/bg/agent-service-in-action.34fb465c9a84659e.webp)

За да използваме някой от тези инструменти с услугата, можем да създадем клиент и да дефинираме инструмент или набор от инструменти. За практическа реализация можем да използваме следния Python код. LLM ще може да прегледа набора от инструменти и да реши дали да използва потребителски създадената функция `fetch_sales_data_using_sqlite_query`, или предварително изградения Code Interpreter в зависимост от заявката на потребителя.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # функция fetch_sales_data_using_sqlite_query, която може да бъде намерена във файла fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Инициализиране на набора от инструменти
toolset = ToolSet()

# Инициализиране на агент за извикване на функции с функцията fetch_sales_data_using_sqlite_query и добавянето ѝ към набора от инструменти
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Инициализиране на инструмент Code Interpreter и добавянето му към набора от инструменти.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Какви са специалните съображения при използването на дизайнерския модел за използване на инструменти, за да се изградят надеждни AI агенти?

Често срещана грижа при динамично генериран SQL от LLM е сигурността, особено рискът от SQL инжекции или злонамерени действия, като изтриване или манипулиране на базата данни. Докато тези опасения са валидни, те могат да бъдат ефективно неутрализирани чрез правилна конфигурация на разрешенията за достъп до базата данни. За повечето бази данни това включва конфигуриране на базата данни в режим само за четене. За бази данни като PostgreSQL или Azure SQL приложението трябва да бъде назначено със съответната роля само за четене (SELECT).

Изпълнението на приложението в сигурна среда допълнително засилва защитата. В корпоративните сценарии данните обикновено се извличат и трансформират от оперативните системи в база данни само за четене или хранилище на данни с потребителски ориентирана схема. Този подход гарантира, че данните са защитени, оптимизирани за производителност и достъпност, и че приложението има ограничен достъп само за четене.

## Примерни кодове
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Имате ли още въпроси относно използването на дизайн модели за инструменти?

Присъединете се към [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), за да се срещнете с други учащи, да посетите часове за консултации и да получите отговори на въпросите си за AI агенти.

## Допълнителни ресурси

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Работилница Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Работилница Contoso Creative Writer Multi-Agent</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Урок за повикване на функции в Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Интерпретатор на код в Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Инструменти Autogen</a>

## Предишен урок

[Разбиране на агентските дизайн модели](../03-agentic-design-patterns/README.md)

## Следващ урок

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Отказ от отговорност**:
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на съответния език трябва да се счита за официален източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за каквито и да е недоразумения или неправилни тълкувания, произтичащи от използването на този превод.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->