[![Kako dizajnirati dobre AI agente](../../../translated_images/hr/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Kliknite gornju sliku za pregled videa ove lekcije)_

# Obrazac dizajna uporabe alata

Alati su zanimljivi jer omogućuju AI agentima širi spektar mogućnosti. Umjesto da agent ima ograničen skup radnji koje može izvršiti, dodavanjem alata agent sada može izvoditi širok raspon radnji. U ovom poglavlju razmotrit ćemo Obrazac dizajna uporabe alata, koji opisuje kako AI agenti mogu koristiti određene alate za postizanje svojih ciljeva.

## Uvod

U ovoj lekciji nastojimo odgovoriti na sljedeća pitanja:

- Što je obrazac dizajna uporabe alata?
- Za koje slučajeve upotrebe se može primijeniti?
- Koji su elementi/gradivni blokovi potrebni za implementaciju obrasca dizajna?
- Koje su posebne razmatranja pri korištenju Obrasca dizajna uporabe alata za izgradnju pouzdanih AI agenata?

## Ciljevi učenja

Nakon završetka ove lekcije moći ćete:

- Definirati Obrazac dizajna uporabe alata i njegovu svrhu.
- Prepoznati slučajeve upotrebe gdje je Obrazac dizajna uporabe alata primjenjiv.
- Razumjeti ključne elemente potrebne za implementaciju obrasca dizajna.
- Prepoznati razmatranja za osiguranje pouzdanosti AI agenata koji koriste ovaj obrazac dizajna.

## Što je Obrazac dizajna uporabe alata?

**Obrazac dizajna uporabe alata** usredotočuje se na davanje mogućnosti LLM-ovima da međusobno djeluju s vanjskim alatima kako bi postigli određene ciljeve. Alati su kod koji agent može izvršiti za izvođenje radnji. Alat može biti jednostavna funkcija poput kalkulatora, ili API poziv prema usluzi treće strane poput provjere cijene dionica ili vremenske prognoze. U kontekstu AI agenata, alati su dizajnirani da se izvode od strane agenata kao odgovor na **funkcijske pozive koje generira model**.

## Za koje slučajeve upotrebe se može primijeniti?

AI agenti mogu koristiti alate za dovršavanje složenih zadataka, dohvaćanje informacija ili donošenje odluka. Obrazac dizajna uporabe alata često se koristi u scenarijima koji zahtijevaju dinamičku interakciju s vanjskim sustavima, poput baza podataka, web-servisa ili tumača koda. Ova sposobnost korisna je za niz različitih slučajeva upotrebe, uključujući:

- **Dinamičko dohvaćanje informacija:** Agenti mogu upitavati vanjske API-je ili baze podataka kako bi dohvatili ažurirane podatke (npr. upitavanje SQLite baze podataka za analizu podataka, dohvaćanje cijena dionica ili vremenskih informacija).
- **Izvršavanje i tumačenje koda:** Agenti mogu izvršavati kod ili skripte za rješavanje matematičkih problema, generiranje izvještaja ili izvođenje simulacija.
- **Automatizacija radnih tokova:** Automatizacija ponavljajućih ili višestupanjskih radnih tokova integracijom alata poput raspoređivača zadataka, usluga e-pošte ili podatkovnih cjevovoda.
- **Podrška korisnicima:** Agenti mogu komunicirati s CRM sustavima, platformama za tikete ili bazi znanja kako bi riješili korisnička pitanja.
- **Generiranje i uređivanje sadržaja:** Agenti mogu koristiti alate poput provjere gramatike, sažimatelja teksta ili procjenitelja sigurnosti sadržaja kako bi pomogli u zadacima kreiranja sadržaja.

## Koji su elementi/gradivni blokovi potrebni za implementaciju obrasca dizajna uporabe alata?

Ovi gradivni blokovi omogućuju AI agentu izvođenje širokog raspona zadataka. Pogledajmo ključne elemente potrebne za implementaciju Obrasca dizajna uporabe alata:

- **Sheme funkcija/alata**: Detaljne definicije dostupnih alata, uključujući naziv funkcije, svrhu, potrebne parametre i očekivane izlaze. Ove sheme omogućuju LLM-u razumijevanje koji su alati dostupni i kako konstruirati valjane zahtjeve.

- **Logika izvršavanja funkcija**: Uređuje kako i kada se alati pozivaju na temelju korisnikove namjere i konteksta razgovora. To može uključivati module planera, mehanizme usmjeravanja ili uvjetne tokove koji dinamički određuju uporabu alata.

- **Sustav rukovanja porukama**: Komponente koje upravljaju razgovornim tokom između korisničkih unosa, LLM odgovora, poziva alata i izlaza alata.

- **Okvir za integraciju alata**: Infrastruktura koja povezuje agenta s raznim alatima, bilo da su to jednostavne funkcije ili složene vanjske usluge.

- **Rukovanje pogreškama i validacija**: Mehanizmi za rješavanje neuspjeha u izvršavanju alata, validaciju parametara i upravljanje neočekivanim odgovorima.

- **Upravljanje stanjem**: Prati kontekst razgovora, prethodne interakcije s alatima i trajne podatke kako bi se osigurala konzistentnost kroz višekratne okrete interakcije.

Sljedeće, pogledajmo Pozivanje funkcija/alata detaljnije.
 
### Pozivanje funkcija/alata

Pozivanje funkcija je primarni način na koji omogućujemo velikim jezičnim modelima (LLM-ovima) interakciju s alatima. Često ćete vidjeti da se 'Function' i 'Tool' koriste naizmjenično jer su 'functions' (blokovi ponovo upotrebljivog koda) 'alat' koje agenti koriste za obavljanje zadataka. Da bi se kod funkcije pozvao, LLM mora usporediti zahtjev korisnika s opisom funkcija. Za to se šalje shema koja sadrži opise svih dostupnih funkcija modelu. LLM zatim odabire najprikladniju funkciju za zadatak i vraća njezin naziv i argumente. Odabrana funkcija se poziva, njen odgovor se šalje natrag LLM-u, koji koristi te informacije za odgovor na korisnikov zahtjev.

Za programere koji žele implementirati pozivanje funkcija za agente, bit će vam potrebno:

1. An LLM model that supports function calling
2. A schema containing function descriptions
3. The code for each function described

Koristimo primjer dobivanja trenutnog vremena u gradu za ilustraciju:

1. **Inicijalizirajte LLM koji podržava pozivanje funkcija:**

    Nisu svi modeli podržavaju pozivanje funkcija, pa je važno provjeriti da model koji koristite to podržava.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> podržava pozivanje funkcija. Možemo početi inicijalizacijom Azure OpenAI klijenta. 

    ```python
    # Inicijalizirajte Azure OpenAI klijenta
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Kreirajte shemu funkcije**:

    Sljedeće ćemo definirati JSON shemu koja sadrži naziv funkcije, opis onoga što funkcija radi i nazive te opise parametara funkcije.
    Zatim ćemo ovu shemu proslijediti klijentu kreiranom prethodno, zajedno s korisnikovim zahtjevom da pronađe vrijeme u San Franciscu. Važno je napomenuti da je ono što se vraća **poziv alata**, **a ne** konačan odgovor na pitanje. Kao što je ranije spomenuto, LLM vraća naziv funkcije koju je odabrao za zadatak i argumente koji će joj biti proslijeđeni.

    ```python
    # Opis funkcije koji model treba pročitati
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
  
    # Početna korisnička poruka
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Prvi API poziv: Zatraži od modela da upotrijebi funkciju
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Obradi odgovor modela
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Kod funkcije potreban za izvršenje zadatka:**

    Sada kada je LLM odabrao koju funkciju treba pokrenuti, potrebno je implementirati i izvršiti kod koji obavlja zadatak.
    Kod za dobivanje trenutnog vremena možemo implementirati u Pythonu. Također ćemo trebati napisati kod za izdvajanje naziva i argumenata iz response_message kako bismo dobili konačan rezultat.

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
     # Rukovanje pozivima funkcija
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
  
      # Drugi API poziv: Dohvati konačni odgovor modela
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

Pozivanje funkcija je u središtu većine, ako ne i svih, dizajna upotrebe alata agenta, no implementacija od nule ponekad može biti izazovna.
Kao što smo naučili u [Lesson 2](../../../02-explore-agentic-frameworks) agentni okviri pružaju nam unaprijed izrađene gradivne blokove za implementaciju uporabe alata.
 
## Primjeri uporabe alata s agentnim okvirima

Evo nekoliko primjera kako možete implementirati Obrazac dizajna uporabe alata koristeći različite agentne okvire:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> je open-source AI okvir za .NET, Python i Java programere koji rade s velikim jezičnim modelima (LLM). Pojednostavljuje proces korištenja pozivanja funkcija automatskim opisivanjem vaših funkcija i njihovih parametara modelu kroz proces koji se zove <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serijaliziranje</a>. Također upravlja dvosmjernom komunikacijom između modela i vašeg koda. Još jedna prednost korištenja agentnog okvira poput Semantic Kernel je što vam omogućuje pristup unaprijed izgrađenim alatima poput <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> i <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Sljedeći dijagram ilustrira proces pozivanja funkcija sa Semantic Kernel:

![pozivanje funkcija](../../../translated_images/hr/functioncalling-diagram.a84006fc287f6014.webp)

U Semantic Kernel funkcije/alati nazivaju se <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. Možemo pretvoriti funkciju `get_current_time` koju smo vidjeli ranije u plugin tako što ćemo je staviti u klasu s tom funkcijom. Također možemo importati dekorator `kernel_function`, koji prima opis funkcije. Kada potom kreirate kernel s GetCurrentTimePlugin, kernel će automatski serijalizirati funkciju i njezine parametre, stvarajući shemu za slanje modelu u tom procesu.

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

# Stvorite jezgru
kernel = Kernel()

# Stvorite dodatak
get_current_time_plugin = GetCurrentTimePlugin(location)

# Dodajte dodatak u jezgru
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> je noviji agentni okvir osmišljen da omogući programerima sigurno izgradnju, implementaciju i skaliranje visokokvalitetnih i proširivih AI agenata bez potrebe za upravljanjem osnovnim računalnim i spremišnim resursima. Posebno je koristan za enterprise primjene budući da je potpuno upravljana usluga s enterprise razinom sigurnosti.

U usporedbi s razvojem izravno s LLM API-jem, Azure AI Agent Service pruža neke prednosti, uključujući:

- Automatsko pozivanje alata – nema potrebe za parsiranjem poziva alata, pozivanjem alata i rukovanjem odgovora; sve se to sada radi na strani poslužitelja
- Sigurno upravljanje podacima – umjesto upravljanja vlastitim stanjem razgovora, možete se osloniti na threads koji pohranjuju sve informacije koje su vam potrebne
- Alati spremni za korištenje – alati koje možete koristiti za interakciju s vašim izvorima podataka, poput Bing-a, Azure AI Search i Azure Functions.

Alati dostupni u Azure AI Agent Service mogu se podijeliti u dvije kategorije:

1. Knowledge Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Action Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service nam omogućuje korištenje ovih alata zajedno kao `toolset`. Također koristi `threads` koji prate povijest poruka iz određenog razgovora.

Zamislite da ste prodajni agent u tvrtki pod nazivom Contoso. Želite razviti razgovornog agenta koji može odgovarati na pitanja o vašim prodajnim podacima.

Sljedeća slika ilustrira kako biste mogli koristiti Azure AI Agent Service za analizu vaših prodajnih podataka:

![Agent Service u akciji](../../../translated_images/hr/agent-service-in-action.34fb465c9a84659e.webp)

Za korištenje bilo kojeg od ovih alata s uslugom možemo kreirati klijenta i definirati alat ili skup alata. Za praktičnu implementaciju možemo koristiti sljedeći Python kod. LLM će moći pogledati toolset i odlučiti hoće li koristiti funkciju kreiranu od strane korisnika, `fetch_sales_data_using_sqlite_query`, ili unaprijed izgrađeni Code Interpreter ovisno o korisnikovom zahtjevu.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # funkcija fetch_sales_data_using_sqlite_query koja se može naći u datoteci fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Inicijaliziraj skup alata
toolset = ToolSet()

# Inicijaliziraj agenta za pozivanje funkcija koristeći funkciju fetch_sales_data_using_sqlite_query i dodaj ga u skup alata
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Inicijaliziraj alat Code Interpreter i dodaj ga u skup alata
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Koja su posebna razmatranja pri korištenju Obrasca dizajna uporabe alata za izgradnju pouzdanih AI agenata?

Česta zabrinutost kod SQL-a koji dinamički generiraju LLM-ovi je sigurnost, posebno rizik od SQL injectiona ili zlonamjernih radnji, poput brisanja ili manipulacije bazom podataka. Iako su te zabrinutosti opravdane, mogu se učinkovito ublažiti pravilnom konfiguracijom dozvola pristupa bazi podataka. Za većinu baza podataka to uključuje konfiguriranje baze kao samo za čitanje. Za podatkovne usluge poput PostgreSQL-a ili Azure SQL-a, aplikaciji bi trebala biti dodijeljena uloga samo za čitanje (SELECT).

Pokretanje aplikacije u sigurnom okruženju dodatno pojačava zaštitu. U enterprise scenarijima, podaci se obično izvlače i transformiraju iz operativnih sustava u bazu podataka samo za čitanje ili skladište podataka s korisnički prilagođenom shemom. Taj pristup osigurava da su podaci sigurni, optimizirani za performanse i dostupnost te da aplikacija ima ograničen, samo za čitanje pristup.

## Primjeri koda
- Python: [Okvir za agente](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Okvir za agente](./code_samples/04-dotnet-agent-framework.md)

## Imate li još pitanja o uzorcima korištenja alata?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kako biste se upoznali s drugim polaznicima, prisustvovali konzultacijama i dobili odgovore na pitanja o AI agentima.

## Dodatni resursi

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Radionica Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer radionica s više agenata</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Vodič za pozivanje funkcija Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Interpreter koda Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen alati</a>

## Prethodna lekcija

[Razumijevanje agentičkih obrazaca dizajna](../03-agentic-design-patterns/README.md)

## Sljedeća lekcija

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Odricanje od odgovornosti:
Ovaj dokument preveden je pomoću AI prevoditeljskog servisa [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo osigurati točnost, imajte na umu da automatizirani prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati mjerodavnim izvorom. Za kritične informacije preporučujemo profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakve nesporazume ili pogrešna tumačenja koja proizlaze iz upotrebe ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->