[![Kuidas kujundada häid tehisintellekti agente](../../../translated_images/et/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Klõpsa ülaloleval pildil, et vaadata selle õppetunni videot)_

# Tööriistade kasutamise disainimuster

Tööriistad on huvitavad, sest need võimaldavad tehisintellekti agentidel omada laiemat võimekust. Selle asemel, et agentil oleks piiratud hulk tegevusi, mida ta saab teha, võimaldab tööriista lisamine agendil nüüd sooritada palju erinevaid tegevusi. Selles peatükis vaatleme tööriistade kasutamise disainimustrit, mis kirjeldab, kuidas tehisintellekti agentid saavad kasutada konkreetseid tööriistu oma eesmärkide saavutamiseks.

## Sissejuhatus

Selles õppetunnis püüame vastata järgmistele küsimustele:

- Mis on tööriistade kasutamise disainimuster?
- Millistes kasutusjuhtudes seda saab rakendada?
- Millised elemendid/ehitusplokid on vajalikud disainimustri rakendamiseks?
- Millised on erilised kaalutlused tööriistade kasutamise disainimustri kasutamisel usaldusväärsete tehisintellekti agentide loomiseks?

## Õpieesmärgid

Pärast selle õppetunni lõpetamist suudate:

- Määratleda tööriistade kasutamise disainimustri ja selle eesmärgi.
- Tuvastada kasutusjuhtumeid, kus tööriistade kasutamise disainimuster on rakendatav.
- Mõista peamisi elemente, mis on vajalikud disainimustri rakendamiseks.
- Tunnustada kaalutlusi, mis tagavad selle disainimustri kasutavate tehisintellekti agentide usaldusväärsuse.

## Mis on tööriistade kasutamise disainimuster?

Tööriistade kasutamise disainimuster keskendub LLM-idele võime andmisele suhelda väliste tööriistadega konkreetsete eesmärkide saavutamiseks. Tööriistad on kood, mida agent saab käivitada, et sooritada toiminguid. Tööriist võib olla lihtne funktsioon, nagu kalkulaator, või kolmanda osapoole teenuse API-kõne, näiteks aktsiahindade päring või ilmaprognoos. Tehisintellekti agentide kontekstis on tööriistad disainitud nii, et neid käivitavad agendid vastusena mudeli genereeritud funktsioonikõnedele.

## Millistes kasutusjuhtudes seda saab rakendada?

Tehisintellekti agentid saavad tööriistu kasutada keerukate ülesannete täitmiseks, teabe hankimiseks või otsuste tegemiseks. Tööriistade kasutamise disainimustrit kasutatakse sageli stsenaariumites, mis nõuavad dünaamilist suhtlust väliste süsteemidega, nagu andmebaasid, veebiteenused või koodi interpreteerijad. See võime on kasulik mitmete erinevate kasutusjuhtude puhul, sealhulgas:

- **Dünaamiline teabe päring:** Agendid saavad pärida väliseid API-sid või andmebaase, et hankida ajakohastatud andmeid (nt SQLite andmebaasi pärimine andmeanalüüsiks, aktsiahindade või ilmainfo hankimine).
- **Koodi täitmine ja interpreteerimine:** Agendid saavad täita koodi või skripte matemaatiliste probleemide lahendamiseks, aruannete genereerimiseks või simulatsioonide läbiviimiseks.
- **Töövoo automatiseerimine:** Korduvate või mitmeastmeliste töövoogude automatiseerimine, integreerides tööriistu nagu ülesannete ajastajad, e-posti teenused või andmepipelines.
- **Klienditugi:** Agendid saavad suhelda CRM-süsteemide, piletihaldusplatvormide või teadmistebaasidega, et lahendada kasutajate päringuid.
- **Sisu loomine ja redigeerimine:** Agendid saavad kasutada tööriistu nagu grammatikakontrollijad, teksti kokkuvõtjad või sisu turvakontrolli hindajad, et aidata sisu loomise ülesannetes.

## Millised elemendid/ehitusplokid on vajalikud tööriistade kasutamise disainimustri rakendamiseks?

Need ehitusplokid võimaldavad tehisintellekti agendil täita laia valikut ülesandeid. Vaatame üle peamised elemendid, mis on vajalikud tööriistade kasutamise disainimustri rakendamiseks:

- **Funktsiooni/tööriista skeemid**: Saadavate tööriistade üksikasjalikud määratlused, mis sisaldavad funktsiooni nime, eesmärki, nõutavaid parameetreid ja eeldatavaid väljundeid. Need skeemid võimaldavad LLM-il mõista, millised tööriistad on saadaval ja kuidas koostada kehtivaid päringuid.

- **Funktsiooni täitmise loogika**: Reguleerib, kuidas ja millal tööriistu kutsutakse sõltuvalt kasutaja kavatsusest ja vestluse kontekstist. See võib hõlmata planeerijamooduleid, marsruutimismehhanisme või tingimuslikke vooge, mis määravad tööriistade dünaamilise kasutuse.

- **Sõnumite käsitlemise süsteem**: Komponendid, mis haldavad vestluse voogu kasutaja sisendite, LLM-i vastuste, tööriistakõnede ja tööriistaväljastuste vahel.

- **Tööriistade integreerimise raamistik**: Infrastruktuur, mis ühendab agendi erinevate tööriistadega, olgu need siis lihtsad funktsioonid või keerukad välisteenused.

- **Veakäsitlus ja valideerimine**: Mehhanismid tööriistade täitmise ebaõnnestumiste käsitlemiseks, parameetrite valideerimiseks ja ootamatute vastuste haldamiseks.

- **Oleku haldus**: Jälgib vestluse konteksti, varasemaid tööriistainteraktsioone ja püsivaid andmeid, et tagada järjepidevus mitme vooru interaktsioonide jooksul.

Järgmisena vaatame funktsioonide/tööriistade kutsumist üksikasjalikumalt.
 
### Funktsioonide/tööriistade kutsumine

Funktsioonide kutsumine on peamine viis, kuidas me võimaldame suurkeelemudelitel (LLM-idel) suhelda tööriistadega. Sageli kasutatakse termineid 'Funktsioon' ja 'Tööriist' vaheldumisi, sest 'funktsioonid' (taaskasutatava koodi plokid) on need 'tööriistad', mida agendid ülesannete täitmiseks kasutavad. Selleks, et funktsiooni kood saaks käivituda, peab LLM võrdlema kasutaja päringut funktsioonide kirjeldusega. Selleks saadetakse LLM-ile skeem, mis sisaldab kõigi saadaolevate funktsioonide kirjeldusi. LLM valib seejärel ülesande jaoks kõige sobivama funktsiooni ja tagastab selle nime ja argumendid. Valitud funktsioon käivitatakse, selle vastus saadetakse tagasi LLM-ile, mis kasutab neid andmeid, et vastata kasutaja päringule.

Arendajatel, kes soovivad agentidele funktsioonide kutsumist rakendada, on vaja:

1. LLM-mudelit, mis toetab funktsioonide kutsumist
2. Funktsioonikirjeldusi sisaldavat skeemi
3. Iga kirjeldatud funktsiooni koodi

Võtame näite hetkeaja saamiseks linnas, et illustreerida:

1. **Algatage LLM, mis toetab funktsioonide kutsumist:**

    Mitte kõik mudelid ei toeta funktsioonide kutsumist, seega on oluline kontrollida, kas LLM, mida kasutate, seda toetab.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> toetab funktsioonide kutsumist. Saame alustada Azure OpenAI kliendi initsialiseerimisest. 

    ```python
    # Initsialiseeri Azure OpenAI klient
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Looge funktsiooni skeem**:

    Järgmisena määratleme JSON-skeemi, mis sisaldab funktsiooni nime, kirjeldust funktsiooni eesmärgi kohta ning funktsiooni parameetrite nimesid ja kirjeldusi.
    Seejärel võtame selle skeemi ja anname selle varem loodud kliendile koos kasutaja päringuga, et leida aeg San Franciscos. Oluline on märgata, et tagastatav on **tööriistakõne**, **mitte** lõplik vastus küsimusele. Nagu eelnevalt mainitud, tagastab LLM valitud funktsiooni nime ja argumendid, mis sellele edastatakse.

    ```python
    # Funktsiooni kirjeldus, mida mudel loeb
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
  
    # Algne kasutaja sõnum
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Esimene API-kõne: Paluge mudelil funktsiooni kasutada
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Töötle mudeli vastust
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Funktsiooni kood ülesande täitmiseks:**

    Nüüd, kui LLM on valinud, millist funktsiooni tuleb käivitada, tuleb rakendada ja täita kood, mis ülesande ära teeb.
    Saame Pythonis rakendada koodi, mis hangib hetkeaja. Lisaks peame kirjutama koodi, et väljastusvastusest response_message välja võtta nimi ja argumendid, et saada lõplik tulemus.

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
     # Käsitle funktsioonikõnesid
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
  
      # Teine API-päring: saada mudeli lõplik vastus
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

Funktsioonide kutsumine on enamikus, kui mitte kõigis agentide tööriistakasutuse lahendustes keskne, kuid selle nullist rakendamine võib olla mõnikord keeruline.
Nagu õppisime [Õppetunnis 2](../../../02-explore-agentic-frameworks) pakuvad agentilised raamistikud meile eelnevalt valmistatud ehitusplokke tööriistakasutuse rakendamiseks.
 
## Tööriistade kasutamise näited agentiliste raamistikudega

Siin on mõned näited, kuidas saate tööriistade kasutamise disainimustrit rakendada erinevate agentiliste raamistikude abil:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> on avatud lähtekoodiga AI-raamistik .NET-, Python- ja Java-arendajatele, kes töötavad suurkeelemudelitega (LLM-id). See lihtsustab funktsioonikõne kasutamist, kirjeldades teie funktsioone ja nende parameetreid mudelile automaatselt protsessi kaudu, mida nimetatakse <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serialiseerimiseks</a>. See haldab ka mudeli ja teie koodi vahelist edasitagasi suhtlust. Teine eelis agentilise raamistikuga nagu Semantic Kernel kasutamisel on see, et see võimaldab pääseda eelnevalt valmistatud tööriistadele nagu <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> ja <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Järgnev diagramm illustreerib funktsioonikõne protsessi Semantic Kernelis:

![function calling](../../../translated_images/et/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernelis kutsutakse funktsioone/tööriistu <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">pluginiteks</a>. Saame teisendada varem näidatud `get_current_time` funktsiooni pluginaks, muutes selle klassiks, milles funktsioon asub. Samuti saame importida `kernel_function` dekoratoori, mis võtab vastu funktsiooni kirjelduse. Kui seejärel loote kerneli GetCurrentTimePluginiga, serialiseerib kernel automaatselt funktsiooni ja selle parameetrid, luues skeemi, mis saadetakse LLM-ile.

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

# Loo tuum
kernel = Kernel()

# Loo pistikprogramm
get_current_time_plugin = GetCurrentTimePlugin(location)

# Lisa pistikprogramm tuumasse
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> on uuem agentiline raamistik, mis on loodud selleks, et anda arendajatele võimalus turvaliselt ehitada, juurutada ja skaleerida kõrgekvaliteedilisi ning laiendatavaid tehisintellekti agente ilma, et peaks hallama aluseks olevat arvutus- ja salvestusressurssi. See on eriti kasulik ettevõtte rakenduste puhul, kuna tegu on täielikult hallatava teenusega ettevõtte tasemel turvafunktsioonidega.

Võrreldes arendamisega otse LLM API-ga pakub Azure AI Agent Service mõningaid eeliseid, sealhulgas:

- Automaatne tööriistakutsumine – pole vaja tööriistakõnet parsida, tööriista käivitada ja vastust käsitleda; kogu see toiming toimub nüüd serveripoolselt
- Turvaliselt hallatavad andmed – selle asemel, et hallata oma vestluste olekut, võite tugineda thread'idele, et salvestada kogu vajalikku teavet
- Valmis tööriistad – tööriistad, mida saate kasutada oma andmeallikatega suhtlemiseks, nagu Bing, Azure AI Search ja Azure Functions.

Azure AI Agent Service'is saadaval olevad tööriistad võib jagada kahte kategooriasse:

1. Teadmiste tööriistad:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Tegevustööriistad:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service võimaldab meil neid tööriistu kasutada koos kui `toolset`. See kasutab ka `threads`, mis hoiavad registrit konkreetse vestluse sõnumite ajaloost.

Kujutage ette, et olete müügiesindaja ettevõttes nimega Contoso. Soovite arendada vestlusagendi, mis suudab vastata küsimustele teie müügiandmete kohta.

Allolev pilt illustreerib, kuidas võiksite Azure AI Agent Service'i kasutada oma müügiandmete analüüsimiseks:

![Agentic Service In Action](../../../translated_images/et/agent-service-in-action.34fb465c9a84659e.webp)

Nende tööriistade kasutamiseks teenusega saame luua kliendi ja määratleda tööriista või tööriistakomplekti. Praktilise rakenduse jaoks võime kasutada järgmist Python-koodi. LLM suudab vaadata tööriistakomplekti ja otsustada, kas kasutada kasutaja loodud funktsiooni `fetch_sales_data_using_sqlite_query` või eelnevalt loodud Code Interpreterit, sõltuvalt kasutaja päringust.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query funktsioon, mida leiab failist fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Initsialiseeri tööriistakomplekt
toolset = ToolSet()

# Initsialiseeri funktsiooni kutsumise agent fetch_sales_data_using_sqlite_query funktsiooniga ja lisa see tööriistakomplekti
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Initsialiseeri Code Interpreter tööriist ja lisa see tööriistakomplekti
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Millised on erilised kaalutlused tööriistade kasutamise disainimustri rakendamisel usaldusväärsete tehisintellekti agentide loomiseks?

Üks levinud mure LLM-ide poolt dünaamiliselt genereeritud SQL-i puhul on turvalisus, eriti SQL-injektsiooni või pahatahtlike toimingute risk, nagu andmebaasi kustutamine või muutmine. Kuigi need mured on õigustatud, saab neid tõhusalt leevendada andmebaasi juurdepääsuõiguste nõuetekohase seadistamisega. Enamiku andmebaaside puhul tähendab see andmebaasi seadistamist ainult lugemisõigustega. Andmebaasiteenuste, nagu PostgreSQL või Azure SQL, puhul tuleks rakendusele määrata ainult lugemisõigusega (SELECT) roll.

Rakenduse käivitamine turvalises keskkonnas suurendab kaitset veelgi. Ettevõtte stsenaariumites eraldatakse andmed tavaliselt operatsioonisüsteemidest ja teisendatakse lugemisõigustega andmebaasiks või andmelattu kasutajasõbraliku skeemiga. See lähenemine tagab, et andmed on turvalised, optimeeritud jõudluse ja ligipääsetavuse jaoks ning et rakendusel on piiratud lugemisõigustega juurdepääs.

## Näidiskoodid
- Python: [Agendi raamistik](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agendi raamistik](./code_samples/04-dotnet-agent-framework.md)

## Kas sul on veel küsimusi tööriistade kasutamise disainimustrite kohta?

Liitu [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) et kohtuda teiste õppuritega, osaleda konsultatsioonidel ja saada vastuseid oma AI-agentide küsimustele.

## Täiendavad ressursid

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service töötuba</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer mitmeagendi töötuba</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel funktsioonikõnede õpetus</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel koodi tõlgendaja</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen tööriistad</a>

## Eelmine õppetund

[Agentsete disainimustrite mõistmine](../03-agentic-design-patterns/README.md)

## Järgmine õppetund

[Agentne RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastutusest loobumine**:
See dokument on tõlgitud tehisintellekti tõlketeenuse [Co-op Translator](https://github.com/Azure/co-op-translator) abil. Kuigi me püüame tagada täpsust, palun arvestage, et automaatsed tõlked võivad sisaldada vigu või ebatäpsusi. Algset dokumenti selle algkeeles tuleks pidada autoriteetseks allikaks. Olulise teabe puhul soovitatakse professionaalset inimtõlget. Me ei vastuta ühegi arusaamatuse ega valesti tõlgendamise eest, mis tuleneb selle tõlke kasutamisest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->