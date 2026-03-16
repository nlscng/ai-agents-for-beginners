[![How to Design Good AI Agents](../../../translated_images/tl/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(I-click ang larawan sa itaas upang panoorin ang video ng araling ito)_

# Pattern ng Disenyo sa Paggamit ng Tool

Kawili-wili ang mga tool dahil pinapayagan nila ang mga AI agent na magkaroon ng mas malawak na hanay ng kakayahan. Sa halip na ang agent ay may limitadong set ng mga aksyon na maaari nitong gawin, sa pamamagitan ng pagdagdag ng isang tool, maaari na ngayong magsagawa ang agent ng malawak na hanay ng mga aksyon. Sa kabanatang ito, titingnan natin ang Pattern ng Disenyo sa Paggamit ng Tool, na naglalarawan kung paano maaaring gumamit ang mga AI agent ng mga partikular na tool upang makamit ang kanilang mga layunin.

## Panimula

Sa araling ito, layunin nating sagutin ang mga sumusunod na tanong:

- Ano ang pattern ng disenyo sa paggamit ng tool?
- Ano ang mga kaso ng paggamit kung saan ito maaaring ilapat?
- Ano ang mga elemento/mga bloke ng pagbuo na kailangan upang maipatupad ang pattern ng disenyo?
- Ano ang mga espesyal na konsiderasyon sa paggamit ng Tool Use Design Pattern upang makabuo ng mga mapagkakatiwalaang AI agent?

## Mga Layunin sa Pagkatuto

Pagkatapos makumpleto ang araling ito, magagawa mong:

- Tukuyin ang Tool Use Design Pattern at ang layunin nito.
- Kilalanin ang mga kaso ng paggamit kung saan ang Tool Use Design Pattern ay naaangkop.
- Unawain ang mga pangunahing elemento na kailangan upang maipatupad ang pattern ng disenyo.
- Kilalanin ang mga konsiderasyon para sa pagtiyak ng pagiging mapagkakatiwalaan ng mga AI agent na gumagamit ng pattern ng disenyo na ito.

## Ano ang Tool Use Design Pattern?

Ang **Tool Use Design Pattern** ay nakatuon sa pagbibigay ng kakayahan sa mga LLM na makipag-ugnayan sa mga panlabas na tool upang makamit ang mga partikular na layunin. Ang mga tool ay code na maaaring ipatupad ng isang agent upang magsagawa ng mga aksyon. Ang isang tool ay maaaring isang simpleng function tulad ng calculator, o isang API call sa isang third-party na serbisyo tulad ng paghahanap ng presyo ng stock o forecast ng panahon. Sa konteksto ng mga AI agent, ang mga tool ay dinisenyo upang ipatupad ng mga agent bilang tugon sa **model-generated function calls**.

## Ano ang mga kaso ng paggamit kung saan ito maaaring ilapat?

Maaaring gamitin ng mga AI Agent ang mga tool upang tapusin ang mga kumplikadong gawain, kumuha ng impormasyon, o gumawa ng mga desisyon. Madalas gamitin ang pattern ng disenyo ng paggamit ng tool sa mga senaryo na nangangailangan ng dynamic na interaksyon sa mga panlabas na sistema, tulad ng mga database, web services, o code interpreters. Ang kakayahang ito ay kapaki-pakinabang para sa iba't ibang mga kaso ng paggamit kabilang ang:

- **Dynamic Information Retrieval:** Maaaring mag-query ang mga agent sa mga panlabas na API o database para kumuha ng pinakabagong data (halimbawa, pag-query sa isang SQLite database para sa pagsusuri ng data, pagkuha ng mga presyo ng stock o impormasyon sa panahon).
- **Code Execution and Interpretation:** Maaaring magpatupad ang mga agent ng code o script para lutasin ang mga matematikal na problema, gumawa ng mga ulat, o magsagawa ng mga simulasyon.
- **Workflow Automation:** Pag-automate ng mga paulit-ulit o multi-step na workflow sa pamamagitan ng pagsasama ng mga tool tulad ng task schedulers, email services, o data pipelines.
- **Customer Support:** Maaaring makipag-ugnayan ang mga agent sa mga CRM system, ticketing platform, o knowledge base para lutasin ang mga tanong ng user.
- **Content Generation and Editing:** Maaaring gamitin ng mga agent ang mga tool tulad ng grammar checkers, text summarizers, o content safety evaluators upang tumulong sa mga gawain sa paggawa ng nilalaman.

## Ano ang mga elemento/mga bloke ng pagbuo na kailangan upang maipatupad ang tool use design pattern?

Ang mga bloke ng pagbuo na ito ang nagpapahintulot sa AI agent na magsagawa ng malawak na hanay ng mga gawain. Tingnan natin ang mga pangunahing elemento na kailangan upang maipatupad ang Tool Use Design Pattern:

- **Function/Tool Schemas**: Detalyadong mga depinisyon ng mga available na tool, kabilang ang pangalan ng function, layunin, kinakailangang mga parameter, at inaasahang output. Pinapahintulutan ng mga schema na ito ang LLM na maunawaan kung anong mga tool ang available at kung paano bumuo ng balidong mga kahilingan.

- **Function Execution Logic**: Namamahala kung paano at kailan tinatawag ang mga tool batay sa intensyon ng user at konteksto ng pag-uusap. Maaaring kabilang dito ang mga planner module, routing mechanism, o mga kondisyonal na daloy na nagdedetermina ng dynamic na paggamit ng tool.

- **Message Handling System**: Mga bahagi na namamahala sa daloy ng pag-uusap sa pagitan ng mga input ng user, tugon ng LLM, tawag sa tool, at mga output ng tool.

- **Tool Integration Framework**: Impraestruktura na nag-uugnay sa agent sa iba't ibang mga tool, maging ito man ay simpleng mga function o komplikadong panlabas na serbisyo.

- **Error Handling & Validation**: Mga mekanismo upang hawakan ang mga pagkabigo sa pagpapatupad ng tool, i-validate ang mga parameter, at pamahalaan ang mga hindi inaasahang tugon.

- **State Management**: Sinusubaybayan ang konteksto ng pag-uusap, mga nakaraang interaksyon sa tool, at persistent na data upang matiyak ang konsistensiya sa maraming turn ng interaksyon.

Sunod, tingnan natin nang mas detalyado ang Function/Tool Calling.

### Function/Tool Calling

Ang function calling ang pangunahing paraan para bigyang-daan ang mga Large Language Models (LLMs) na makipag-ugnayan sa mga tool. Madalas mong makitang ginagamit na palitan ang 'Function' at 'Tool' dahil ang 'functions' (mga bloke ng reusable na code) ay ang 'tools' na ginagamit ng mga agent upang isagawa ang mga gawain. Para matawagan ang code ng isang function, kailangang ihambing ng LLM ang kahilingan ng user sa paglalarawan ng function. Upang magawa ito, ipinapadala sa LLM ang isang schema na naglalaman ng mga paglalarawan ng lahat ng available na mga function. Pinipili ng LLM ang pinakaangkop na function para sa gawain at ibinabalik ang pangalan nito pati na ang mga argumento. Tinatawag ang napiling function, ang tugon nito ay ipinapadala pabalik sa LLM, na ginagamit ang impormasyong iyon upang tumugon sa kahilingan ng user.

Para sa mga developer na nais magpatupad ng function calling para sa mga agent, kailangan ninyo ng:

1. Isang LLM model na sumusuporta sa function calling
2. Isang schema na naglalaman ng mga paglalarawan ng function
3. Ang code para sa bawat function na inilalarawan

Gamitin natin ang halimbawa ng pagkuha ng kasalukuyang oras sa isang lungsod upang ilarawan:

1. **I-initialize ang isang LLM na sumusuporta sa function calling:**

    Hindi lahat ng modelo ay sumusuporta sa function calling, kaya mahalagang tiyakin na ang LLM na ginagamit mo ay sumusuporta nito.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Sinusuportahan ng Azure OpenAI</a> ang function calling. Maaari tayong magsimula sa pamamagitan ng pag-initialize ng Azure OpenAI client.

    ```python
    # I-initialize ang Azure OpenAI client
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Gumawa ng Function Schema:**

    Susunod ay magtatakda tayo ng isang JSON schema na naglalaman ng pangalan ng function, paglalarawan ng ginagawa ng function, at ang mga pangalan at paglalarawan ng mga parameter ng function.
    Pagkatapos ay ipapasa natin ang schema na ito sa client na nilikha kanina, kasama ang kahilingan ng user upang hanapin ang oras sa San Francisco. Mahalaga na tandaan na ang bumabalik ay isang **tool call**, **hindi** ang panghuling sagot sa tanong. Tulad ng nabanggit kanina, ibinabalik ng LLM ang pangalan ng function na pinili nito para sa gawain, at ang mga argumento na ipapasa dito.

    ```python
    # Paglalarawan ng function para basahin ng modelo
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
  
    # Paunang mensahe ng gumagamit
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Unang tawag sa API: Hilingin sa modelo na gamitin ang function
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Proseso ng tugon ng modelo
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Ang code ng function na kailangan para isagawa ang gawain:**

    Ngayong napili na ng LLM kung aling function ang kailangang patakbuhin, kailangang ipatupad at isagawa ang code para sa gawain.
    Maaari nating ipatupad ang code upang makuha ang kasalukuyang oras sa Python. Kailangan din nating isulat ang code upang kunin ang pangalan at mga argumento mula sa response_message upang makuha ang panghuling resulta.

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
     # Pangasiwaan ang mga tawag sa function
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
  
      # Ikalawang tawag sa API: Kunin ang panghuling sagot mula sa modelo
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

Ang Function Calling ay nasa puso ng karamihan, kung hindi man lahat, ng agent tool use design, subalit ang pag-implementa nito mula sa simula ay maaaring minsang maging hamon.
Tulad ng natutunan natin sa [Lesson 2](../../../02-explore-agentic-frameworks), nagbibigay ang mga agentic framework ng mga pre-built na bloke ng pagbuo upang maipatupad ang tool use.
 
## Mga Halimbawa ng Tool Use gamit ang Agentic Frameworks

Narito ang ilang mga halimbawa kung paano mo maipapatupad ang Tool Use Design Pattern gamit ang iba't ibang agentic framework:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> ay isang open-source AI framework para sa mga .NET, Python, at Java developer na nagtatrabaho gamit ang Large Language Models (LLMs). Pinapadali nito ang proseso ng paggamit ng function calling sa pamamagitan ng awtomatikong paglalarawan ng iyong mga function at kanilang mga parametera sa modelo sa pamamagitan ng isang proseso na tinatawag na <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializing</a>. Pinamamahalaan din nito ang palitan ng komunikasyon sa pagitan ng modelo at ng iyong code. Isa pang pakinabang ng paggamit ng agentic framework tulad ng Semantic Kernel, ay pinahihintulutan kang ma-access ang mga pre-built na tool tulad ng <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> at <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Ipinapakita ng sumusunod na diagram ang proseso ng function calling gamit ang Semantic Kernel:

![function calling](../../../translated_images/tl/functioncalling-diagram.a84006fc287f6014.webp)

Sa Semantic Kernel ang mga function/tool ay tinatawag na <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. Maaari nating gawing plugin ang `get_current_time` function na nakita natin kanina sa pamamagitan ng paggawa nito bilang isang klase na may function sa loob nito. Maaari din nating i-import ang `kernel_function` decorator, na tumatanggap ng paglalarawan ng function. Kapag nilikha mo ang kernel kasama ang GetCurrentTimePlugin, awtomatikong suserialisa ng kernel ang function at ang mga parameter nito, na lumilikha ng schema upang ipadala sa LLM sa proseso.

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

# Gumawa ng kernel
kernel = Kernel()

# Gumawa ng plugin
get_current_time_plugin = GetCurrentTimePlugin(location)

# Idagdag ang plugin sa kernel
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> ay isang mas bagong agentic framework na dinisenyo upang bigyang kapangyarihan ang mga developer na ligtas na bumuo, mag-deploy, at mag-scale ng mataas na kalidad at extensible na AI agent nang hindi na kailangang pamahalaan ang underlying na compute at storage resources. Partikular itong kapaki-pakinabang para sa mga enterprise application dahil ito ay isang fully managed service na may enterprise grade na seguridad.

Kung ikukumpara sa direktang pag-develop gamit ang LLM API, may mga sumusunod na pakinabang ang Azure AI Agent Service, kabilang ang:

- Awtomatikong pagtawag ng tool – hindi na kailangan pang i-parse ang isang tool call, tawagan ang tool, at hawakan ang tugon; lahat ng ito ay ginagawa na sa server-side
- Ligtas na pinamamahalaang data – sa halip na pamahalaan ang sarili mong estado ng pag-uusap, maaari kang umasa sa threads upang itago ang lahat ng impormasyong kailangan mo
- Mga tool na handa nang gamitin – Mga tool na maaari mong gamitin upang makipag-ugnayan sa iyong mga pinagmumulan ng data, tulad ng Bing, Azure AI Search, at Azure Functions.

Ang mga tool na available sa Azure AI Agent Service ay nahahati sa dalawang kategorya:

1. Mga Knowledge Tool:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding gamit ang Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Mga Action Tool:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">Mga tool na nilalarawan ng OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Pinapayagan tayo ng Agent Service na magamit ang mga tool na ito nang sabay bilang isang `toolset`. Ginagamit din nito ang `threads` na nagtatala ng kasaysayan ng mga mensahe mula sa partikular na pag-uusap.

Isipin mo na ikaw ay isang sales agent sa isang kumpanya na tinatawag na Contoso. Nais mong bumuo ng isang conversational agent na kayang sumagot sa mga tanong tungkol sa iyong sales data.

Ipinapakita ng sumusunod na imahe kung paano mo magagamit ang Azure AI Agent Service upang suriin ang iyong sales data:

![Agentic Service In Action](../../../translated_images/tl/agent-service-in-action.34fb465c9a84659e.webp)

Para magamit ang alinman sa mga tool na ito sa serbisyo, maaari tayong gumawa ng client at magtakda ng isang tool o toolset. Para sa praktikal na implementasyon, maaari nating gamitin ang sumusunod na Python code. Magagawa ng LLM na tingnan ang toolset at magdesisyon kung gagamitin ang sariling function ng user, `fetch_sales_data_using_sqlite_query`, o ang pre-built Code Interpreter depende sa kahilingan ng user.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query function na matatagpuan sa isang fetch_sales_data_functions.py na file.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# I-initialize ang toolset
toolset = ToolSet()

# I-initialize ang function calling agent gamit ang fetch_sales_data_using_sqlite_query function at idagdag ito sa toolset
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# I-initialize ang Code Interpreter tool at idagdag ito sa toolset.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Ano ang mga espesyal na konsiderasyon sa paggamit ng Tool Use Design Pattern upang makabuo ng mga mapagkakatiwalaang AI agent?

Isang pangkaraniwang alalahanin sa SQL na dinamiko na nilikha ng mga LLM ay seguridad, partikular ang panganib ng SQL injection o mga malisyosong gawain, tulad ng pag-drop o pagtangkang pakialaman ang database. Bagamat may bisa ang mga alalahaning ito, maaari itong lubos na mabawasan sa pamamagitan ng wastong pagsasaayos ng mga pahintulot sa pag-access ng database. Para sa karamihan ng mga database, kasama dito ang pagsasaayos ng database bilang read-only. Para sa mga database service tulad ng PostgreSQL o Azure SQL, dapat bigyan ang app ng read-only (SELECT) na tungkulin.

Ang pagpapatakbo ng app sa isang secure na kapaligiran ay lalo pang nagpapahusay sa proteksyon. Sa mga enterprise scenario, karaniwang kinukuha at binabago ang data mula sa mga operational na sistema papunta sa isang read-only na database o data warehouse na may user-friendly na schema. Tinitiyak ng pamamaraang ito na ligtas ang data, optimized para sa performance at accessibility, at may limitadong read-only access ang app.

## Sample Codes
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## May Karagdagang Mga Tanong Tungkol sa Tool Use Design Patterns?

Sumali sa [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) upang makipagkita sa iba pang mga nag-aaral, dumalo sa office hours, at masagot ang iyong mga tanong tungkol sa AI Agents.

## Karagdagang Mga Mapagkukunan

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## Nakaraang Aralin

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## Susunod na Aralin

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Paalala**:  
Ang dokumentong ito ay isinalin gamit ang AI translation service na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagamat nagsusumikap kami na maging tumpak, mangyaring tandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga pagkakamali o di-tumpak na impormasyon. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring na pangunahing sanggunian. Para sa mga importanteng impormasyon, inirerekomenda ang propesyonal na salin ng tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na maaaring magmula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->