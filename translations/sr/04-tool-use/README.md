[![Како дизајнирати добре AI агенте](../../../translated_images/sr/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Кликните на слику изнад да бисте погледали видео о овој лекцији)_

# Обрасци коришћења алата

Алатке су занимљиве јер омогућавају AI агентима шире могућности. Уместо да агент има ограничен скуп акција које може извршити, додавањем алатке он сада може извршити широк спектар радњи. У овом поглављу ћемо погледати Образац коришћења алата, који описује како AI агенти могу да користе специфичне алатке да би постигли своје циљеве.

## Увод

У овој лекцији желимо да одговоримо на следећа питања:

- Шта је образац коришћења алата?
- За које случајеве коришћења се може применити?
- Који су елементи/грађевински блокови потребни за имплементацију обрасца?
- Које су посебне мере за коришћење Обрасца коришћења алата за изградњу поузданих AI агената?

## Циљеви учења

Након завршетка ове лекције, моћи ћете да:

- Дефинишете Образац коришћења алата и његову сврху.
- Идентификујете случајеве коришћења где је Образац применљив.
- Разумете кључне елементе потребне за имплементацију обрасца.
- Препознате мере за обезбеђење поузданости AI агената који користе овај образац.

## Шта је Образац коришћења алата?

**Образац коришћења алата** фокусира се на пружање Large Language Models (LLM) могућности да интерагују са спољним алаткама ради постизања специфичних циљева. Алатке су код који агент може извршити да би обавио задатке. Алатка може бити једноставна функција као што је калкулатор, или позив API-ју треће стране као што су преглед цена акција или временска прогноза. У контексту AI агената, алатке су дизајниране да их агенти извршавају као одговор на **функцијске позиве генерисане моделом**.

## За које случајеве коришћења се може применити?

AI агенти могу користити алатке за завршетак сложених задатака, преузимање информација или доношење одлука. Образац коришћења алата често се примењује у сценаријима који захтевају динамичку интеракцију са спољним системима, као што су базе података, веб сервисе или интерпретатори кода. Ова способност је корисна у различитим случајевима укључујући:

- **Динамичко преузимање информација:** Агенти могу захтевати спољне API-је или базе података ради добијања актуелних података (нпр. упити у SQLite базу ради анализе података, преузимање цена акција или временских информација).
- **Извршавање и тумачење кода:** Агенти могу извршавати код или скрипте ради решавања математичких проблема, генерације извештаја или извођења симулација.
- **Аутоматизација радних токова:** Аутоматизација понављајућих или вишестепених радних токова интегрисањем алата као што су распоредивачи задатака, услуге е-поште или цевоводи за податке.
- **Корисничка подршка:** Агенти могу да интерагују са CRM системима, платформама за подршку или базама знања да реше корисничке упите.
- **Генерација и уређивање садржаја:** Агенти могу користити алате као што су проверавачи граматике, резимирање текста или процена безбедности садржаја да помогну у задацима креирања садржаја.

## Који су елементи/грађевински блокови потребни за имплементацију обрасца коришћења алата?

Ови грађевински блокови омогућавају AI агенту да обави широк спектар задатака. Погледајмо кључне елементе потребне за имплементацију Обрасца коришћења алата:

- **Шеме функција/алата**: Детаљни описи доступних алата, укључујући име функције, сврху, потребне параметре и очекиване излазне вредности. Ове шеме омогућавају LLM да разуме које су алатке доступне и како да конструише валидне захтеве.

- **Логика извршавања функција**: Прописује како и када се алатке позивају у зависности од намере корисника и контекста разговора. Ово може укључивати модуле планирања, механизме усмеравања или условне токове који динамички одређују употребу алата.

- **Систем управљања порукама**: Компоненте које управљају током разговора између уноса корисника, одговора LLM, позива алата и резултата алата.

- **Интеграциони оквир за алате**: Инфраструктура која повезује агента са различитим алаткама, било да су то једноставне функције или сложени спољни сервиси.

- **Обрада грешака и провера валидности**: Механизми за управљање неуспесима у извршењу алата, проверу параметара и обраду неочекиваних одговора.

- **Управљање стањем**: Праћење контекста разговора, претходних интеракција са алатима и упорних података како би се обезбедила конзистентност кроз вишекратно коришћење.

Следеће, погледајмо детаљније позивање функција/алата.

### Позивање функција/алата

Позивање функција је примарни начин на који омогућавамо Large Language Models (LLM) да интерагују са алатима. Често ће се "функција" и "алат" користити наизменично јер су "функције" (блокови поново употребљивог кода) ти "алати" које агенти користе за извршавање задатака. Да би се код функције позвао, LLM мора упоредити захтев корисника са описом функције. Да би то урадио, шаље се шема која садржи описе свих доступних функција LLM-у. LLM затим бира најприкладнију функцију за задатак и враћа њено име и аргументе. Изабрана функција се извршава, њен одговор се шаље назад LLM-у који користи те информације да одговори на кориснички захтев.

За програмере који желе да имплементирају позивање функција за агенте, потребно је:

1. LLM модел који подржава позивање функција
2. Шема која садржи описе функција
3. Код за сваку од описаних функција

Погледајмо пример добијања тренутног времена у граду као илустрацију:

1. **Иницијализујте LLM који подржава позивање функција:**

    Ни сви модели не подржавају позивање функција, па је важно проверити да ли модел који користите то ради. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> подржава позивање функција. Можемо започети иницијализацијом Azure OpenAI клијента. 

    ```python
    # Инициализујте Azure OpenAI клијента
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Креирајте шему функције**:

    Следеће ћемо дефинисати JSON шему која садржи име функције, опис шта функција ради и имена и описе параметара функције.
    Потом ћемо послати ову шему клијенту који смо раније направили заједно са корисничким захтевом да пронађе време у Сан Франциску. Важно је напоменути да се враћа **позив алата**, а **не** коначни одговор на питање. Као што је раније поменуто, LLM враћа име функције коју је изабрао за задатак и аргументе који ће јој бити прослеђени.

    ```python
    # Опис функције за читање модела
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
  
    # Почетна порука корисника
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Први позив API-ја: Замолити модел да користи функцију
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Обрадити одговор модела
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Код функције потребан за извршење задатка:**

    Сада када је LLM изабрао коју функцију треба покренути, код који обавља задатак мора бити имплементиран и извршен.
    Можемо имплементирати код за добијање тренутног времена у Python-у. Такође ћемо морати написати код за издвајање имена и аргумената из response_message да бисмо добили коначни резултат.

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
     # Обрада позива функција
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
  
      # Други позив API-ју: Добијање коначног одговора од модела
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

Позивање функција је у срцу већине, ако не и свих обрасца коришћења алата, међутим његова имплементација од нуле понекад може бити изазовна.
Као што смо научили у [Лекцији 2](../../../02-explore-agentic-frameworks) агенцијски оквири нам пружају унапред састављене грађевинске блокове за имплементацију коришћења алата.
 
## Примери коришћења алата са агенцијским оквирима

Ево неколико примера како можете имплементирати Образац коришћења алата користећи различите агенцијске оквире:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> је open-source AI оквир за .NET, Python и Java програмере који раде са Large Language Models (LLM). Поједностављује процес коришћења позивања функција аутоматским описивањем ваших функција и њихових параметара моделу кроз процес назван <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">серилизацијом</a>. Такође управља комуникацијом у оба смера између модела и вашег кода. Још једна предност коришћења агенцијског оквира као Semantic Kernel је што омогућава приступ унапред изграђеним алатима као што су <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Претрага фајлова</a> и <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Интерпретатор кода</a>.

Следећа шема илуструје процес позивања функција са Semantic Kernel:

![function calling](../../../translated_images/sr/functioncalling-diagram.a84006fc287f6014.webp)

У Semantic Kernel функције/алати се зову <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. Можемо претворити функцију `get_current_time` коју смо раније видели у plugin претварањем у класу са функцијом унутар. Такође можемо импортирати `kernel_function` декоратор који прихвата опис функције. Када онда креирате kernel са GetCurrentTimePlugin-ом, kernel аутоматски серилизује функцију и њене параметре, стварајући шему коју шаље LLM-у у том процесу.

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

# Креирај језгро
kernel = Kernel()

# Креирај додатак
get_current_time_plugin = GetCurrentTimePlugin(location)

# Додај додатак у језгро
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> је новији агенцијски оквир дизајниран да омогући програмерима сигурно креирање, постављање и скалирање квалитетних и проширивих AI агената без потребе за управљањем основним рачунарским и складишним ресурсима. Посебно је користан за корпоративне апликације јер је то потпуно управљана услуга са корпоративним нивоом безбедности.

У поређењу са директним развојем преко LLM API-ја, Azure AI Agent Service нуди неке предности, укључујући:

- Аутоматско позивање алата – нема потребе за парсирањем позива алата, извршавањем алата и обрадом одговора; све је то сада обављено на серверу
- Сигурно управљани подаци – уместо да сами управљате стањем разговора, можете се ослонити на thread-ове који чувају све потребне информације
- Алати који раде "одмах" – алатке за интеракцију са вашим изворима података, као што су Bing, Azure AI Search и Azure Functions.

Алатке доступне у Azure AI Agent Service могу се поделити у две категорије:

1. Алати за знање:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Повезивање са Bing претрагом</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Претрага фајлова</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Акциони алати:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Позивање функција</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Интерпретатор кода</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI дефинисани алати</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service нам омогућава коришћење ових алата заједно као `toolset`. Такође користи `thread` који прате историју порука из конкретног разговора.

Замислите да сте продајни агент у компанији Contoso. Желите да развијете конверзацијалног агента који може да одговара на питања о вашим подацима о продаји.

Следећа слика илуструје како можете користити Azure AI Agent Service за анализу ваших продајних података:

![Agentic Service In Action](../../../translated_images/sr/agent-service-in-action.34fb465c9a84659e.webp)

Да бисте користили било који од ових алата са сервисом, можете креирати клијента и дефинисати алат или скуп алата. За практичну имплементацију можемо користити следећи Python код. LLM ће моћи да погледа скуп алата и одлучи да ли ће користити функцију коју је креирао корисник, `fetch_sales_data_using_sqlite_query`, или унапред направљени интерпретатор кода у зависности од захтева корисника.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # функција fetch_sales_data_using_sqlite_query која се може пронаћи у фајлу fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Иницијализуј алатке
toolset = ToolSet()

# Иницијализуј агента за позивање функција са функцијом fetch_sales_data_using_sqlite_query и додај га алаткама
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Иницијализуј Code Interpreter алатку и додај је алаткама.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Које су посебне мере при коришћењу Обрасца коришћења алата ради изградње поузданих AI агената?

Често питање у вези са SQL упитима динамички генерисаним од стране LLM јесте безбедност, нарочито ризик од SQL инјекција или злонамерних акција, као што су брисање или мењање базе података. Иако су ове бриге валидне, могу се ефикасно ублажити правилним конфигурисањем приступних дозвола базе података. За већину база података то укључује конфигурисање базе као само за читање. За базне сервисе као PostgreSQL или Azure SQL, апликацији треба доделити улогу само за читање (SELECT).

Покретање апликације у сигурном окружењу додатно појачава заштиту. У корпоративним сценаријима, подаци се типично издвајају и трансформишу из оперативних система у базу или складиште података само за читање са кориснички пријатељском шемом. Овај приступ осигурава да су подаци безбедни, оптимизовани за перформансе и доступност, и да апликација има ограничен приступ само за читање.

## Пример кода
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Имате још питања о коришћењу образаца дизајна алата?

Придружите се [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) да упознате друге учеснике, присуствујете канцеларијским сатима и добијете одговоре на ваша питања о AI агентима.

## Додатни ресурси

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## Претходна лекција

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## Следећа лекција

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Одрицање одговорности**:
Овај документ је преведен користећи AI услугу за превођење [Co-op Translator](https://github.com/Azure/co-op-translator). Иако тежимо тачности, молимо вас да имате у виду да аутоматски преводи могу садржати грешке или нетачности. Изворни документ на његовом изворном језику треба сматрати ауторитетним извором. За критичне информације препоручује се професионални превод од стране човека. Нисмо одговорни за било каква неспоразума или погрешне тумачења која проистичу из коришћења овог превода.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->