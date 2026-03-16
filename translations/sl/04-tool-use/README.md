[![Kako oblikovati dobre AI agente](../../../translated_images/sl/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Kliknite na zgornjo sliko za ogled videoposnetka te lekcije)_

# Vzorec oblikovanja uporabe orodij

Orodja so zanimiva, ker omogočajo AI agentom širši nabor zmožnosti. Namesto da ima agent omejen nabor dejanj, ki jih lahko izvede, lahko z dodajanjem orodja agent zdaj opravlja širok spekter dejanj. V tej poglavju si bomo ogledali vzorec oblikovanja uporabe orodij, ki opisuje, kako lahko AI agenti uporabljajo specifična orodja za doseganje svojih ciljev.

## Uvod

V tej lekciji želimo odgovoriti na naslednja vprašanja:

- Kaj je vzorec oblikovanja uporabe orodij?
- Za katere primere uporabe ga lahko uporabimo?
- Kateri elementi/gradniki so potrebni za implementacijo vzorca oblikovanja?
- Kakšni so posebni premisleki za uporabo vzorca oblikovanja uporabe orodij pri gradnji zaupanja vrednih AI agentov?

## Cilji učenja

Po zaključku te lekcije boste znali:

- Določiti vzorec oblikovanja uporabe orodij in njegov namen.
- Prepoznati primere uporabe, kjer je vzorec uporabnosti orodij uporaben.
- Razumeti ključne elemente, potrebne za implementacijo vzorca oblikovanja.
- Prepoznati premisleke za zagotavljanje zaupanja vrednih AI agentov z uporabo tega vzorca oblikovanja.

## Kaj je vzorec oblikovanja uporabe orodij?

**Vzorec oblikovanja uporabe orodij** daje LLM-jem sposobnost interakcije z zunanjimi orodji za doseganje specifičnih ciljev. Orodja so koda, ki jo agent lahko izvrši za opravljanje dejanj. Orodje je lahko preprosta funkcija, kot je kalkulator, ali klic API-ja do storitve tretje strani, kot je poizvedba cene delnic ali vremenska napoved. V kontekstu AI agentov so orodja zasnovana tako, da jih agenti izvajajo kot odziv na **klice funkcij, ki jih generira model**.

## Za katere primere uporabe ga lahko uporabimo?

AI agenti lahko uporabljajo orodja za dokončanje kompleksnih nalog, pridobivanje informacij ali sprejemanje odločitev. Vzorec oblikovanja uporabe orodij se pogosto uporablja v scenarijih, ki zahtevajo dinamično interakcijo z zunanjimi sistemi, kot so baze podatkov, spletne storitve ali interpretatorji kode. Ta zmožnost je uporabna za številne različne primere uporabe, vključno z:

- **Dinamično pridobivanje informacij:** Agenti lahko poizvedujejo zunanje API-je ali baze podatkov, da pridobijo posodobljene podatke (npr. poizvedba po SQLite bazi podatkov za analizo podatkov, pridobivanje cen delnic ali vremenskih informacij).
- **Zagon in interpretacija kode:** Agenti lahko izvajajo kodo ali skripte za reševanje matematičnih problemov, ustvarjanje poročil ali izvajanje simulacij.
- **Avtomatizacija delovnih tokov:** Avtomatizacija ponavljajočih se ali večstopenjskih delovnih tokov z vključevanjem orodij, kot so urniki opravil, email storitve ali podatkovni tokovi.
- **Podpora strankam:** Agenti lahko sodelujejo s CRM sistemi, platformami za izdajo tiketov ali bazami znanja za reševanje uporabniških poizvedb.
- **Ustvarjanje in urejanje vsebin:** Agenti lahko uporabljajo orodja, kot so preverjevalniki slovnice, povzemalniki besedil ali ocenjevalci varnosti vsebine, da pomagajo pri nalogah ustvarjanja vsebine.

## Kateri elementi/gradniki so potrebni za implementacijo vzorca uporabe orodij?

Ti gradniki omogočajo AI agentu izvajanje širokega nabora nalog. Oglejmo si ključne elemente, potrebne za implementacijo vzorca oblikovanja uporabe orodij:

- **Sheme funkcij/orodij**: Podrobne definicije razpoložljivih orodij, vključno z imenom funkcije, namenom, zahtevanimi parametri in pričakovanimi izhodi. Te sheme omogočajo LLM-ju razumevanje, katera orodja so na voljo in kako sestaviti veljavne zahteve.

- **Logika izvajanja funkcij**: Nadzira kako in kdaj se orodja kličejo glede na uporabnikovo namero in kontekst pogovora. Lahko vključuje module načrtovanja, mehanizme usmerjanja ali pogojne tokove, ki dinamično določajo uporabo orodij.

- **Sistem upravljanja sporočil**: Komponente, ki upravljajo potek pogovora med vhodnimi podatki uporabnika, odgovori LLM-ja, klici orodij in izhodi orodij.

- **Okvir za integracijo orodij**: Infrastruktura, ki povezuje agenta z različnimi orodji, bodisi preprostimi funkcijami ali zapletenimi zunanjimi storitvami.

- **Obravnava napak in preverjanje**: Mehanizmi za obravnavo napak pri izvajanju orodij, preverjanje parametrov in upravljanje nepričakovanih odzivov.

- **Upravljanje stanja**: Sledi kontekstu pogovora, prejšnjim interakcijam z orodji in trajnim podatkom, da zagotovi doslednost pri večkrožnih interakcijah.

Nato si poglejmo klic funkcij/orodij v več podrobnosti.

### Klic funkcij/orodij

Klic funkcij je glavni način, na katerega omogočimo Velikim jezikovnim modelom (LLM-jem) interakcijo z orodji. Pogosto boste videli, da se "funkcija" in "orodje" uporabljata izmenično, ker so 'funkcije' (bloki ponovno uporabne kode) dejansko 'orodja', ki jih agenti uporabljajo za opravljanje nalog. Da se lahko pokliče koda funkcije, mora LLM primerjati uporabnikovo zahtevo z opisom funkcije. Za to se pošlje shema z opisi vseh razpoložljivih funkcij LLM-ju. LLM nato izbere najbolj primerno funkcijo za nalogo in vrne njeno ime ter argumente. Izbrana funkcija se nato izvede, njen odgovor pa se pošlje nazaj LLM-ju, ki uporabi te informacije za odgovor na uporabnikovo zahtevo.

Za razvijalce, ki želijo implementirati klic funkcij za agente, boste potrebovali:

1. LLM model, ki podpira klic funkcij
2. Shemo z opisi funkcij
3. Kodo za vsako opisano funkcijo

Uporabimo primer, kako dobiti trenutni čas v mestu, da ilustriramo:

1. **Inicializirajte LLM, ki podpira klic funkcij:**

    Ne podpirajo vsi modeli klica funkcij, zato je pomembno preveriti, ali model, ki ga uporabljate, to omogoča. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> podpira klic funkcij. Lahko začnemo z inicializacijo Azure OpenAI odjemalca. 

    ```python
    # Inicializirajte Azure OpenAI odjemalca
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Ustvarite shemo funkcije:**

    Nato definiramo JSON shemo, ki vsebuje ime funkcije, opis česa funkcija počne in imena ter opise parametrov funkcije.
    To shemo nato posredujemo prej ustvarjenemu odjemalcu skupaj z uporabnikovo zahtevo po določitvi časa v San Franciscu. Pomembno je poudariti, da je rezultat **klic orodja**, **ne** končni odgovor na vprašanje. Kot je bilo omenjeno prej, LLM vrne ime funkcije, ki jo je izbral za nalogo, in argumente, ki ji bodo posredovani.

    ```python
    # Opis funkcije za branje modela
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
  
    # Začetno uporabniško sporočilo
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Prvi klic API: Prosite model, naj uporabi funkcijo
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Obdelajte odgovor modela
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Koda funkcije, potrebna za izvedbo naloge:**

    Ko je LLM izbral, katero funkcijo je treba zagnati, mora biti koda, ki opravi nalogo, implementirana in izvršena.
    Kodo za pridobivanje trenutnega časa lahko izvedemo v Pythonu. Prav tako bomo morali napisati kodo za izvlečenje imena funkcije in argumentov iz response_message, da dobimo končni rezultat.

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
     # Obravnava klice funkcij
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
  
      # Drugi klic API: Pridobite končni odgovor modela
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

Klic funkcije je v središču večine, če ne vseh oblik uporabe orodij agentov, vendar je njegova implementacija iz nič včasih zahtevna.
Kot smo se naučili v [Lekcija 2](../../../02-explore-agentic-frameworks) zagotavljajo agentni okviri vnaprej pripravljene gradnike za implementacijo uporabe orodij.

## Primeri uporabe orodij z agentnimi okviri

Tukaj je nekaj primerov, kako lahko implementirate vzorec oblikovanja uporabe orodij z uporabo različnih agentnih okvirjev:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> je odprtokodni AI okvir za razvijalce .NET, Python in Java, ki delajo z Velikimi jezikovnimi modeli (LLM). Poenostavlja postopek klica funkcij tako, da samodejno opisuje vaše funkcije in njihove parametre modelu s procesom, imenovanim <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializacija</a>. Prav tako upravlja komunikacijo med modelom in vašo kodo v obe smeri. Druga prednost uporabe agentnega okvirja, kot je Semantic Kernel, je, da omogoča dostop do vnaprej pripravljenih orodij, kot sta <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Iskanje datotek</a> in <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Interpretacija kode</a>.

Spodnji diagram ponazarja postopek klica funkcij s Semantic Kernel:

![function calling](../../../translated_images/sl/functioncalling-diagram.a84006fc287f6014.webp)

V Semantic Kernel se funkcije/orodja imenujejo <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Vtičniki</a>. Funkcijo `get_current_time`, ki smo jo videli prej, lahko pretvorimo v vtičnik tako, da jo naredimo razred s funkcijo znotraj. Prav tako lahko uvozimo dekorator `kernel_function`, ki sprejme opis funkcije. Ko nato ustvarite jedro s GetCurrentTimePlugin, jedro samodejno serializira funkcijo in njene parametre ter v procesu ustvari shemo za pošiljanje LLM-ju.

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

# Ustvari jedro
kernel = Kernel()

# Ustvari vtičnik
get_current_time_plugin = GetCurrentTimePlugin(location)

# Dodaj vtičnik v jedro
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> je novejši agentni okvir, zasnovan za omogočanje razvijalcem, da varno gradijo, uvajajo in skalirajo visokokakovostne in razširljive AI agente brez potrebe po upravljanju osnovnih računalniških in pomnilniških virov. Je še posebej uporaben za poslovne aplikacije, saj je popolnoma upravljana storitev s poslovno varnostjo.

V primerjavi z razvojem neposredno z LLM API-jem Azure AI Agent Service nudi naslednje prednosti:

- Avtomatski klic orodij – ni potrebe po razčlenitvi klica orodja, sprožitvi orodja in obravnavi odziva; vse to se zdaj izvaja na strežniški strani
- Varno upravljanje podatkov – namesto, da upravljate lastno stanje pogovora, lahko zaupate nitim, ki shranjujejo vse potrebne informacije
- Orodja, ki jih lahko takoj uporabljate – orodja za interakcijo z viri podatkov, kot so Bing, Azure AI Search in Azure Functions.

Orodja, na voljo v Azure AI Agent Service, lahko razdelimo v dve kategoriji:

1. Orodja za znanje:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Povezava z iskanjem Bing</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Iskanje datotek</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Orodja za ukrepanje:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Klic funkcij</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Interpretacija kode</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">Orodja, definirana z OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service nam omogoča, da ta orodja uporabljamo skupaj kot `orodjarski komplet`. Prav tako uporablja `nite`, ki sledijo zgodovini sporočil določene konverzacije.

Predstavljajte si, da ste prodajni agent v podjetju Contoso. Želite razviti pogovornega agenta, ki zna odgovarjati na vprašanja o vaših prodajnih podatkih.

Spodnja slika ponazarja, kako bi lahko uporabili Azure AI Agent Service za analizo vaših prodajnih podatkov:

![Agentic Service In Action](../../../translated_images/sl/agent-service-in-action.34fb465c9a84659e.webp)

Za uporabo teh orodij s storitvijo lahko ustvarimo odjemalca in definiramo orodje ali komplet orodij. Za praktično implementacijo lahko uporabimo naslednjo kodo v Pythonu. LLM bo lahko pogledal komplet orodij in se odločil, ali uporabiti funkcijo, ki jo je ustvaril uporabnik, `fetch_sales_data_using_sqlite_query`, ali pa vnaprej pripravljeno Interpretacijo kode, glede na uporabnikovo zahtevo.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # funkcija fetch_sales_data_using_sqlite_query, ki jo najdete v datoteki fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Inicializiraj orodjarno
toolset = ToolSet()

# Inicializiraj agenta za klic funkcij s funkcijo fetch_sales_data_using_sqlite_query in jo dodaj k orodjarni
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Inicializiraj orodje za interpretacijo kode in ga dodaj k orodjarni.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Kakšni so posebni premisleki pri uporabi vzorca oblikovanja uporabe orodij za gradnjo zaupanja vrednih AI agentov?

Pogosta skrb pri dinamično generiranem SQL-ju s strani LLM-jev je varnost, še posebej tveganje SQL injekcije ali zlonamernih dejanj, kot je brisanje ali spreminjanje baze podatkov. Čeprav so te skrbi upravičene, jih je mogoče učinkovito odpraviti z ustrezno konfiguracijo dovoljenj za dostop do baze podatkov. Pri večini baz podatkov to vključuje konfiguracijo baze kot samo za branje. Za baze podatkov, kot sta PostgreSQL ali Azure SQL, bi morale aplikaciji dodeliti vlogo samo za branje (SELECT).

Zagon aplikacije v varnem okolju še dodatno povečuje zaščito. V poslovnih scenarijih se podatki običajno izvlečejo in transformirajo iz operativnih sistemov v bazo samo za branje ali v skladišče podatkov z uporabniku prijazno shemo. Ta pristop zagotavlja, da so podatki varni, optimizirani za delovanje in dostopnost ter da ima aplikacija omejen, samo za branje, dostop.

## Vzorec kode
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Imate več vprašanj o uporabi vzorcev orodij v dizajnu?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kjer se lahko srečate z drugimi učenci, udeležite ur uradnih ur in dobite odgovore na vprašanja o AI agentih.

## Dodatni viri

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Delavnica Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Delavnica Contoso Creative Writer Multi-Agent</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Vodič za klic funkcij Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Interpreter kode</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Orodja</a>

## Prejšnja lekcija

[Razumevanje agentnih vzorcev dizajna](../03-agentic-design-patterns/README.md)

## Naslednja lekcija

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Omejitev odgovornosti**:
Ta dokument je bil preveden z uporabo AI prevajalske storitve [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, upoštevajte, da avtomatizirani prevodi lahko vsebujejo napake ali netočnosti. Izvorni dokument v izvirnem jeziku naj velja za avtoritativni vir. Za pomembne informacije priporočamo strokoven človeški prevod. Za morebitna nesporazume ali napačne interpretacije, ki izhajajo iz uporabe tega prevoda, ne odgovarjamo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->