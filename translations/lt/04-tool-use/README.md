[![Kaip sukurti gerus DI agentus](../../../translated_images/lt/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Spustelėkite aukščiau esantį paveikslėlį, kad peržiūrėtumėte šios pamokos vaizdo įrašą)_

# Įrankių naudojimo dizaino šablonas

Įrankiai yra įdomūs, nes jie leidžia DI agentams turėti platesnį veiksmų spektrą. Vietoj to, kad agentas turėtų ribotą veiksmų skaičių, pridėjus įrankį agentas dabar gali atlikti daug įvairių veiksmų. Šiame skyriuje apžvelgsime Įrankių naudojimo dizaino šabloną, kuris aprašo, kaip DI agentai gali naudoti specifinius įrankius norėdami pasiekti savo tikslus.

## Įvadas

Šioje pamokoje sieksime atsakyti į šiuos klausimus:

- Kas yra įrankių naudojimo dizaino šablonas?
- Kokiais atvejais jis gali būti taikomas?
- Kokie elementai/statybiniai blokai reikalingi šablonui įgyvendinti?
- Kokie yra ypatingi aspektai naudojant Įrankių naudojimo dizaino šabloną kuriant patikimus DI agentus?

## Mokymosi tikslai

Baigę šią pamoką galėsite:

- Apibrėžti Įrankių naudojimo dizaino šabloną ir jo paskirtį.
- Nustatyti atvejus, kuriose taikomas Įrankių naudojimo dizaino šablonas.
- Suprasti pagrindinius elementus, reikalingus šablonui įgyvendinti.
- Atpažinti svarbias aplinkybes patikimumo užtikrinimui DI agentų naudojamuose įrankių šablonuose.

## Kas yra Įrankių naudojimo dizaino šablonas?

**Įrankių naudojimo dizaino šablonas** skirta suteikti LLM galimybę sąveikauti su išoriniais įrankiais siekiant konkrečių tikslų. Įrankiai yra kodas, kurį agentas gali vykdyti atlikdamas veiksmus. Įrankis gali būti paprasta funkcija, pavyzdžiui, skaičiuotuvas, arba API kvietimas į trečiosios šalies paslaugą, tokią kaip akcijų kainų paieška ar orų prognozė. DI agentų kontekste įrankiai yra sukurti taip, kad būtų vykdomi agentų reaguojant į **modelio sugeneruotus funkcijų kvietimus**.

## Kokiais atvejais jis gali būti taikomas?

DI agentai gali naudoti įrankius atlikdami sudėtingas užduotis, gaudami informaciją arba priimdami sprendimus. Įrankių naudojimo dizaino šablonas dažnai taikomas situacijose, kur reikalinga dinamiška sąveika su išorinėmis sistemomis, tokiomis kaip duomenų bazės, interneto paslaugos ar kodo interpretatoriai. Ši galimybė naudinga daugeliui skirtingų atvejų, įskaitant:

- **Dinaminis informacijos gavimas:** Agentai gali užklausti išorinių API ar duomenų bazių, norėdami gauti atnaujintus duomenis (pvz., užklausos SQLite duomenų bazėje duomenų analizei, akcijų kainų ar orų informacija).
- **Kodo vykdymas ir interpretavimas:** Agentai gali vykdyti kodą ar scenarijus, spręsti matematines problemas, generuoti ataskaitas ar atlikti simuliacijas.
- **Darbo eigos automatizavimas:** Automatinis pasikartojančių arba kelių žingsnių darbo eigų vykdymas integruojant įrankius, tokius kaip užduočių planuotojai, el. pašto paslaugos ar duomenų srautai.
- **Klientų aptarnavimas:** Agentai gali sąveikauti su CRM sistemomis, bilietų platformomis ar žinių bazėmis, spręsdami naudotojų užklausas.
- **Turinio kūrimas ir redagavimas:** Agentai gali naudoti kalbos taisytuvus, teksto santraukas ar turinio saugos vertintojus, siekdami padėti kuriant turinį.

## Kokie elementai/statybiniai blokai reikalingi įrankių naudojimo dizaino šablonui įgyvendinti?

Šie statybiniai blokai leidžia DI agentui atlikti platų užduočių spektrą. Pažvelkime į pagrindinius elementus, reikalingus Įrankių naudojimo dizaino šablonui įgyvendinti:

- **Funkcijų/įrankių schemos**: Išsamūs turimų įrankių aprašymai, įskaitant funkcijos pavadinimą, paskirtį, reikalingus parametrus ir numatomus išėjimus. Šios schemos leidžia LLM suprasti, kokie įrankiai yra prieinami ir kaip suformuoti galiojančius užklausas.

- **Funkcijų vykdymo logika**: Nustato, kaip ir kada kviečiami įrankiai, atsižvelgiant į vartotojo ketinimus ir pokalbio kontekstą. Tai gali apimti planavimo modulius, maršrutizavimo mechanizmus ar sąlyginį srautą, kuris dinamiškai nusprendžia apie įrankių naudojimą.

- **Žinučių valdymo sistema**: Komponentai, valdantys pokalbio eigą tarp vartotojo įrašų, LLM atsakymų, įrankių kvietimų ir jų rezultatų.

- **Įrankių integracijos sistema**: Infrastruktūra, jungianti agentą su įvairiais įrankiais, nesvarbu ar tai paprastos funkcijos, ar sudėtingos išorinės paslaugos.

- **Klaidų valdymas ir patikrinimas**: Mechanizmai, tvarkantys įrankių vykdymo klaidas, tikrinantys parametrus ir valdantys netikėtus atsakymus.

- **Būsenos valdymas**: Stebi pokalbio kontekstą, ankstesnius įrankių panaudojimus ir išliekamuosius duomenis, užtikrinant nuoseklumą kelių turų sąveikose.

Toliau pažvelkime į funkcijų/įrankių kvietimą išsamiau.
 
### Funkcijų/įrankių kvietimas

Funkcijų kvietimas yra pagrindinis būdas, kuriuo leidžiame Didelėms kalbos modeliams (LLM) sąveikauti su įrankiais. Dažnai matysite, kad 'funkcija' ir 'įrankis' vartojami kaip sinonimai, nes 'funkcijos' (pernaudojamo kodo blokai) yra 'įrankiai', kuriuos agentai naudoja užduotims atlikti. Kad funkcijos kodas būtų iškviestas, LLM turi palyginti vartotojo užklausą su funkcijos aprašymu. Tam yra siunčiama schema, kurioje yra visų prieinamų funkcijų aprašymai. LLM pasirinkdamas tinkamą funkciją užduočiai grąžina jos pavadinimą ir argumentus. Pasirinkta funkcija iškviečiama, jos atsakymas siunčiamas atgal LLM, kuris naudoja šią informaciją atsakydamas vartotojui.

Kūrėjams norintiems įgyvendinti funkcijų kvietimą agentams reikės:

1. LLM modelio, palaikančio funkcijų kvietimą
2. Schemos su funkcijų aprašymais
3. Kodo kiekvienai funkcijai, aprašytai schemoje

Pažiūrėkime pavyzdį, kaip gauti dabartinį laiką miesto atžvilgiu:

1. **Inicijuokite LLM, palaikantį funkcijų kvietimą:**

    Ne visi modeliai palaiko funkcijų kvietimą, tad svarbu patikrinti, ar naudojamas LLM tai palaiko. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> palaiko funkcijų kvietimą. Galime pradėti inicijuodami Azure OpenAI klientą. 

    ```python
    # Inicializuokite Azure OpenAI klientą
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

2. **Sukurkite funkcijos schemą**:

    Toliau apibrėšime JSON schemą, kurioje bus funkcijos pavadinimas, aprašymas, ką funkcija atlieka, ir funkcijos parametrų pavadinimai su aprašymais.
    Tada šią schemą perduosime anksčiau sukurtam klientui kartu su vartotojo užklausa apie laiką San Franciske. Svarbu pažymėti, kad grąžinama yra **įrankio kvietimas**, **ne** galutinis atsakymas į klausimą. Kaip minėta anksčiau, LLM grąžina funkcijos, kurią pasirinko užduočiai, pavadinimą ir argumentus, kurie bus perduoti funkcijai.

    ```python
    # Funkcijos aprašymas modeliui skaityti
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
  
    # Pradinis vartotojo pranešimas
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Pirmas API kvietimas: Paprašykite modelio naudoti funkciją
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Apdorokite modelio atsakymą
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
3. **Funkcijos kodas, reikalingas užduočiai atlikti:**

    Kadangi LLM pasirinko, kuri funkcija turi būti vykdoma, reikia įgyvendinti ir vykdyti kodą, kuris įvykdys užduotį.
    Galime įgyvendinti kodą dabartiniam laikui gauti Python kalba. Taip pat reikės parašyti kodą, kuris iš atsakymo žinutės išskirs funkcijos pavadinimą ir argumentus, kad gautume galutinį rezultatą.

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
     # Tvarkyti funkcijos iškvietimus
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
  
      # Antras API kvietimas: Gauti galutinį modelio atsakymą
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

Funkcijų kvietimas yra pagrindas daugumai, jei ne visiems agentų įrankių naudojimo dizaino sprendimams, tačiau įgyvendinti jį nuo nulio kartais gali būti sudėtinga.
Kaip išmokome iš [Pamokos 2](../../../02-explore-agentic-frameworks), agentiniams karkasams suteikiamos iš anksto paruošti statybiniai blokai įrankių naudojimui įgyvendinti.
 
## Įrankių naudojimo pavyzdžiai su agentiniais karkasais

Štai keletas pavyzdžių, kaip galite įgyvendinti Įrankių naudojimo dizaino šabloną naudodami skirtingus agentinius karkasus:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> yra atviro kodo DI karkasas .NET, Python ir Java kūrėjams, dirbantiems su Dideliais kalbos modeliais (LLM). Jis supaprastina funkcijų kvietimo naudojimą automatiškai aprašydamas jūsų funkcijas ir jų parametrus modeliui per procesą, vadinamą <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializavimu</a>. Taip pat jis valdo abipusį ryšį tarp modelio ir jūsų kodo. Kitas Semantic Kernel pranašumas yra tas, kad jis leidžia naudotis iš anksto paruoštais įrankiais, tokiais kaip <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Failų paieška</a> ir <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Kodo interpretatorius</a>.

Toliau pateiktame schemoje apžvelgiama funkcijų kvietimo eiga su Semantic Kernel:

![function calling](../../../translated_images/lt/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernel funkcijos/įrankiai vadinami <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugin‘ais</a>. Galime ankstesnę `get_current_time` funkciją paversti plugin'u, sukurdami ją kaip klasę su funkcija viduje. Taip pat galime importuoti `kernel_function` dekoratorių, kuriam perduodamas funkcijos aprašymas. Kai sukuriame kernelį su GetCurrentTimePlugin, kernelis automatiškai serializuoja funkciją ir jos parametrus, kurdamas schemą, kuri siunčiama LLM.

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

# Create the kernel
kernel = Kernel()

# Create the plugin
get_current_time_plugin = GetCurrentTimePlugin(location)

# Add the plugin to the kernel
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> yra naujesnis agentinis karkasas, sukurtas tam, kad padėtų kūrėjams saugiai kurti, diegti ir mastuoti kokybiškus bei išplečiamus DI agentus, nereikalaujant valdyti žemiau esančių skaičiavimo ir saugojimo išteklių. Tai ypač naudinga verslo programoms, nes tai visiškai valdomas servis, turintis verslo lygio saugumą.

Palyginti su tiesioginiu LLM API naudojimu, Azure AI Agent Service suteikia kai kurių privalumų, įskaitant:

- Automatinis įrankių kvietimas – nereikia analizuoti įrankio kvietimo, iškviesti įrankio ir tvarkyti atsakymo; visa tai atliekama serverio pusėje
- Saugus duomenų valdymas – vietoj savo pokalbio būsenos valdymo galite pasikliauti threads, saugančiais jums reikalingą informaciją
- Iš karto paruošti įrankiai – įrankiai, skirti sąveikai su jūsų duomenų šaltiniais, tokiais kaip Bing, Azure AI Search ir Azure Functions.

Azure AI Agent Service įrankius galima suskirstyti į dvi kategorijas:

1. Žinių įrankiai:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Žinioms pagrįsti su Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Failų paieška</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Veiksmų įrankiai:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Funkcijų kvietimas</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Kodo interpretatorius</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI apibrėžti įrankiai</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service leidžia naudoti šiuos įrankius kartu kaip `toolset`. Taip pat naudojamos `threads`, kurios seka konkretaus pokalbio žinučių istoriją.

Įsivaizduokite, kad dirbate pardavimų agentu įmonėje Contoso. Norite sukurti pokalbių agentą, galintį atsakyti į klausimus apie jūsų pardavimų duomenis.

Toliau pateiktas vaizdas iliustruoja, kaip galėtumėte naudoti Azure AI Agent Service analizuojant pardavimų duomenis:

![Agentic Service In Action](../../../translated_images/lt/agent-service-in-action.34fb465c9a84659e.webp)

Norėdami naudoti bet kurį iš šių įrankių su paslauga, galime sukurti klientą ir apibrėžti įrankį arba įrankių rinkinį. Praktiniam įgyvendinimui galime naudoti šį Python kodą. LLM galės peržiūrėti įrankių rinkinį ir nuspręsti, ar naudoti vartotojo sukurtą funkciją `fetch_sales_data_using_sqlite_query`, ar iš anksto paruoštą Kodo interpretatorių, priklausomai nuo vartotojo užklausos.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query funkcija, kurią galima rasti faile fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Inicializuoti įrankių rinkinį
toolset = ToolSet()

# Inicializuoti funkcijų kvietimo agentą su fetch_sales_data_using_sqlite_query funkcija ir pridėti jį prie įrankių rinkinio
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Inicializuoti Kodo interpretatoriaus įrankį ir pridėti jį prie įrankių rinkinio.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Kokios yra ypatingos aplinkybės naudojant Įrankių naudojimo dizaino šabloną kuriant patikimus DI agentus?

Dažna problema su dinamiškai LLM sugeneruotu SQL yra saugumas, ypač SQL injekcijos ar kenkėjiškų veiksmų, tokių kaip duomenų bazės trynimas ar klastojimas, rizika. Nors šios problemos yra pagrįstos, jas galima veiksmingai suvaldyti tinkamai konfigūruojant duomenų bazės prieigos teises. Daugeliui duomenų bazių tai reiškia duomenų bazės konfigūravimą tik skaitymui. Duomenų bazių paslaugoms, tokioms kaip PostgreSQL ar Azure SQL, programai turėtų būti suteikta tik skaitymo (SELECT) rolė.

Programos vykdymas saugioje aplinkoje dar labiau sustiprina apsaugą. Verslo scenarijuose duomenys paprastai yra išgaunami ir transformuojami iš operacinių sistemų į tik skaitymui skirtą duomenų bazę ar duomenų sandėlį su naudotojui draugiška schema. Šis požiūris užtikrina, kad duomenys būtų saugūs, optimizuoti našumui ir prieinamumui, o programa turėtų ribotą, tik skaitymui skirtą prieigą.

## Pavyzdiniai kodai
- Python: [Agentų sistema](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agentų sistema](./code_samples/04-dotnet-agent-framework.md)

## Turite daugiau klausimų apie įrankių naudojimo dizaino šablonus?

Prisijunkite prie [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), susipažinkite su kitais besimokančiais, dalyvaukite konsultacijose ir gaukite atsakymus į savo AI agentų klausimus.

## Papildomi resursai

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI agentų paslaugų dirbtuvės</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso kūrybinio rašytojo multi-agentų dirbtuvės</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel funkcijų kvietimo vadovas</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel kodo interpretatorius</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen įrankiai</a>

## Ankstesnė pamoka

[Agentinių dizaino šablonų supratimas](../03-agentic-design-patterns/README.md)

## Sekanti pamoka

[Agentinis RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:  
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors siekiame tikslumo, prašome atkreipti dėmesį, kad automatiniai vertimai gali turėti klaidų ar netikslumų. Originalus dokumentas gimtąja kalba turėtų būti laikomas autoritetingu šaltiniu. Kritinei informacijai rekomenduojame naudoti profesionalų žmogaus vertimą. Mes neatsakome už bet kokius nesusipratimus ar neteisingą interpretaciją, kylančius dėl šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->