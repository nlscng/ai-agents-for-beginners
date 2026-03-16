[![Miten suunnitella hyviä AI-agentteja](../../../translated_images/fi/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Napsauta yllä olevaa kuvaa katsoaksesi tämän oppitunnin videon)_

# Työkalujen käyttö -suunnittelumalli

Työkalut ovat mielenkiintoisia, koska ne antavat AI-agenteille laajemman kyvykkyysalueen. Sen sijaan, että agentilla olisi rajallinen joukko toimintoja, joita se voi suorittaa, työkalun lisääminen mahdollistaa agentin suorittaa laajan valikoiman toimintoja. Tässä luvussa tarkastelemme Työkalujen käytön suunnittelumallia, joka kuvaa, miten AI-agentit voivat käyttää tiettyjä työkaluja saavuttaakseen tavoitteensa.

## Johdanto

Tässä oppitunnissa pyrimme vastaamaan seuraaviin kysymyksiin:

- Mikä on työkalujen käyttö -suunnittelumalli?
- Millaisiin käyttötapauksiin sitä voi soveltaa?
- Mitkä ovat suunnittelumallin toteuttamiseen tarvittavat osat/rakennuspalikat?
- Mitä erityisiä huomioita liittyy Työkalujen käytön suunnittelumallin käyttämiseen luotettavien AI-agenttien rakentamisessa?

## Oppimistavoitteet

Oppitunnin suorittamisen jälkeen pystyt:

- Määrittelemään Työkalujen käyttö -suunnittelumallin ja sen tarkoituksen.
- Tunnistamaan käyttötapaukset, joissa Työkalujen käyttö -suunnittelumalli soveltuu.
- Ymmärtämään suunnittelumallin avainosat, jotka tarvitaan sen toteuttamiseen.
- Huomaamaan luotettavuuden varmistamiseen liittyvät näkökohdat tämän suunnittelumallin mukaisissa AI-agenteissa.

## Mikä on Työkalujen käyttö -suunnittelumalli?

**Työkalujen käyttö -suunnittelumalli** keskittyy antamaan LLM-malleille kyvyn olla vuorovaikutuksessa ulkoisten työkalujen kanssa tiettyjen tavoitteiden saavuttamiseksi. Työkalut ovat koodia, jota agentti voi suorittaa toimiakseen. Työkalu voi olla yksinkertainen funktio, kuten laskin, tai kolmannen osapuolen palvelun API-kutsu, kuten osakekurssin haku tai sääennuste. AI-agenttien yhteydessä työkalut on suunniteltu suoritettavaksi agenttien vastauksena **mallin generoimiin funktiokutsuihin**.

## Millaisiin käyttötapauksiin sitä voi soveltaa?

AI-agentit voivat hyödyntää työkaluja suorittaakseen monimutkaisia tehtäviä, hakeakseen tietoa tai tehdäkseen päätöksiä. Työkalujen käyttö -suunnittelumallia käytetään usein tilanteissa, joissa tarvitaan dynaamista vuorovaikutusta ulkoisten järjestelmien kanssa, kuten tietokantojen, verkkopalveluiden tai kooditulkkien kanssa. Tämä kyky on hyödyllinen monissa käyttötapauksissa, mukaan lukien:

- **Dynaaminen tiedonhaku:** Agentit voivat kysyä ulkoisia API-rajapintoja tai tietokantoja saadakseen ajankohtaista dataa (esim. SQLite-tietokannasta kysely analyysia varten, osakekurssit tai sää).
- **Koodin suoritus ja tulkinta:** Agentit voivat suorittaa koodia tai skriptejä ratkaistakseen matemaattisia ongelmia, luodakseen raportteja tai suorittaakseen simulaatioita.
- **Työnkulkujen automaatio:** Toistuvien tai monivaiheisten työnkulkujen automatisointi integroimalla työkalut kuten tehtäväaikatauluttimet, sähköpostipalvelut tai dataputket.
- **Asiakastuki:** Agentit voivat olla vuorovaikutuksessa CRM-järjestelmien, tukipyyntöalustojen tai tietokantojen kanssa ratkaistakseen käyttäjän kyselyjä.
- **Sisällön luonti ja muokkaus:** Agentit voivat hyödyntää työkaluja kuten kieliopin tarkistajia, tekstin tiivistäjiä tai sisällön turvallisuusarvioijia auttaakseen sisällöntuotantotehtävissä.

## Mitkä ovat suunnittelumallin toteutukseen tarvittavat osat/rakennuspalikat?

Nämä rakennuspalikat mahdollistavat AI-agentin suorittaa monenlaisia tehtäviä. Tarkastellaan Työkalujen käyttö -suunnittelumallin toteutukseen tarvittavia keskeisiä osia:

- **Funktio/Työkaluskeemat**: Tarkat määritelmät käytettävissä olevista työkaluista, mukaan lukien funktion nimi, tarkoitus, vaaditut parametrit ja odotetut tuotokset. Näiden skeemojen avulla LLM ymmärtää, mitkä työkalut ovat käytettävissä ja miten kelvollisia pyyntöjä rakennetaan.

- **Funktion suorituslogiikka**: Ohjaa, miten ja milloin työkaluja kutsutaan käyttäjän aikomuksen ja keskustelukontekstin perusteella. Tämä voi sisältää suunnittelijamoduuleja, reititysmekanismeja tai ehtoja, jotka määrittävät työkalun käytön dynaamisesti.

- **Viestien käsittelyjärjestelmä**: Komponentit, jotka hallinnoivat keskustelun kulkua käyttäjän syötteiden, LLM-vastausten, työkalukutsujen ja työkalun tuottamien vastausten välillä.

- **Työkalujen integrointikehys**: Infrastruktuuri, joka yhdistää agentin erilaisiin työkaluihin, olivatpa ne yksinkertaisia funktioita tai monimutkaisia ulkoisia palveluja.

- **Virheiden käsittely ja validointi**: Mekanismit työkalun suorituksen virhetilanteiden käsittelyyn, parametrien validointiin ja odottamattomien vastausten hallintaan.

- **Tilanhallinta**: Seuraa keskustelukontekstia, aiempia työkalun käyttökertoja ja pysyviä tietoja, varmistaen johdonmukaisuuden monikertaisen keskustelun aikana.

Seuraavaksi tarkastelemme Funktio/Työkalukutsua tarkemmin.

### Funktio/Työkalukutsu

Funktiokutsu on ensisijainen tapa, jolla mahdollistamme suurten kielimallien (LLM) vuorovaikutuksen työkalujen kanssa. Usein näet 'Funktio' ja 'Työkalu' käytettävän vaihtokelpoisesti, koska 'funktiot' (uudelleenkäytettävät koodilohkot) ovat 'työkaluja', joita agentit käyttävät tehtävien suorittamiseen. Jotta funktion koodia voidaan kutsua, LLM:n täytyy verrata käyttäjän pyyntöä funktion kuvaukseen. Tätä varten LLM:lle lähetetään skeema, joka sisältää kaikkien käytettävissä olevien funktioiden kuvaukset. LLM valitsee sopivimman funktion tehtävään ja palauttaa sen nimen ja argumentit. Valittu funktio suoritetaan, sen vastaus lähetetään takaisin LLM:lle, joka käyttää tietoa vastatakseen käyttäjän pyyntöön.

Kehittäjien, jotka haluavat toteuttaa funktiokutsun agenteille, tarvitsee:

1. LLM-mallin, joka tukee funktiokutsuja
2. Skeeman, joka sisältää funktioiden kuvaukset
3. Koodin jokaiselle kuvatulle funktiolle

Käytetään esimerkkinä nykyisen ajan hakemista kaupungissa:

1. **Alusta LLM, joka tukee funktiokutsuja:**

    Kaikki mallit eivät tue funktiokutsuja, joten on tärkeää tarkistaa, että käyttämäsi LLM tukee tätä. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> tukee funktiokutsuja. Voimme aloittaa alustamalla Azure OpenAI -asiakkaan.

    ```python
    # Alusta Azure OpenAI -asiakas
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Luo funktioskeema**:

    Määrittelemme JSON-skeeman, joka sisältää funktion nimen, kuvauksen siitä, mitä funktio tekee, sekä funktioparametrien nimet ja kuvaukset.
    Tämä skeema annetaan aiemmin luodulle asiakkaalle yhdessä käyttäjän pyynnön kanssa, jossa pyydetään aika San Franciscossa. On tärkeää huomata, että **työkalukutsu** palautetaan, **ei** lopullinen vastaus kysymykseen. Kuten aiemmin mainittiin, LLM palauttaa valitun funktion nimen ja sille annettavat argumentit.

    ```python
    # Toimintokuvaus mallin luettavaksi
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
  
    # Alkuperäinen käyttäjän viesti
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Ensimmäinen API-kutsu: Pyydä mallia käyttämään toimintoa
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Käsittele mallin vastaus
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Funktiokoodi tehtävän suorittamiseksi**:

    Nyt kun LLM on valinnut, mikä funktio tulee suorittaa, vastaava koodi pitää toteuttaa ja suorittaa.
    Voimme toteuttaa koodin nykyisen ajan hakemiseksi Pythonissa. Meidän täytyy myös kirjoittaa koodi, joka poimii nimen ja argumentit response_message:stä lopputuloksen saamiseksi.

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
     # Käsittele funktiokutsut
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
  
      # Toinen API-kutsu: Hanki lopullinen vastaus mallilta
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

Funktiokutsu on useimpien, ellei kaikkien agenttityökalujen käyttöön liittyvien suunnittelumallien ytimessä, mutta sen toteuttaminen alusta asti voi joskus olla haasteellista.
Kuten opimme [Oppitunnissa 2](../../../02-explore-agentic-frameworks), agenttirungot tarjoavat valmiita rakennuspalikoita työkalujen käyttöön.

## Työkalujen käytön esimerkkejä agenttirunkojen kanssa

Seuraavassa on esimerkkejä, miten voit toteuttaa Työkalujen käyttö -suunnittelumallin eri agenttirunkoja käyttäen:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> on avoimen lähdekoodin AI-kehys .NET-, Python- ja Java-kehittäjille, jotka työskentelevät suurten kielimallien (LLM) kanssa. Se yksinkertaistaa funktiokutsujen käyttöä kuvaamalla automaattisesti funktiosi ja niiden parametrit mallille <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">sarjoittamisen</a> prosessin kautta. Se myös hoitaa mallin ja koodisi välisen viestinnän edestakaisin. Toinen etu agenttirungon, kuten Semantic Kernel, käytössä on se, että se antaa pääsyn valmiisiin työkaluihin, kuten <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> ja <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Seuraava kaavio kuvaa funktiokutsuprosessia Semantic Kernelissä:

![function calling](../../../translated_images/fi/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernelissä funktioita/työkaluja kutsutaan <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">liitännäisiksi (Plugins)</a>. Voimme muuttaa aiemmin nähdyn `get_current_time` -funktion liitännäiseksi tekemällä siitä luokan, joka sisältää funktion. Voimme myös tuoda `kernel_function`-koristelijan, joka ottaa vastaan funktion kuvauksen. Kun luot kernelin GetCurrentTimePluginilla, kernel sarjoittaa funktion ja sen parametrit automaattisesti, luoden skeeman LLM:lle lähetettäväksi.

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

# Luo ydin
kernel = Kernel()

# Luo laajennusosa
get_current_time_plugin = GetCurrentTimePlugin(location)

# Lisää laajennusosa ytimeen
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> on uudempi agenttirunko, joka on suunniteltu antamaan kehittäjille mahdollisuuden rakentaa, ottaa käyttöön ja skaalata turvallisesti korkealaatuisia ja laajennettavia AI-agentteja ilman tarvetta hallita taustalla olevia laskenta- ja tallennusresursseja. Se on erityisen hyödyllinen yrityssovelluksissa, koska se on täysin hallinnoitu palvelu, jossa on yritystason tietoturva.

Suoraan LLM-rajapinnan kehittämiseen verrattuna Azure AI Agent Service tarjoaa etuja, kuten:

- Automaattinen työkalujen kutsuminen – ei tarvitse jäsentää työkalukutsua, kutsua työkalua ja käsitellä vastausta; kaikki tapahtuu palvelinpuolella
- Turvallisesti hallinnoitu data – sen sijaan, että hallitset omaa keskustelutilaa, voit luottaa säikeisiin tallentamaan kaiken tarvitsemasi tiedon
- Valmiit työkalut – työkalut, joilla voit olla vuorovaikutuksessa tietolähteidesi kanssa, kuten Bing, Azure AI Search ja Azure Functions.

Azure AI Agent Servicen työkalut voidaan jakaa kahteen kategoriaan:

1. Tietotyökalut:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing Search -maadoitus</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Toimintatyökalut:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI-määritellyt työkalut</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agenttipalvelu antaa mahdollisuuden käyttää näitä työkaluja yhdessä `työkalupakkina`. Se käyttää myös `säikeitä`, jotka pitävät kirjaa tietyn keskustelun viestihistoriasta.

Kuvittele, että olet myyntiedustaja yrityksessä nimeltä Contoso. Haluat kehittää keskustelevaa agenttia, joka voi vastata kysymyksiin myyntidatastasi.

Seuraava kuva havainnollistaa, miten voisit käyttää Azure AI Agent Serviceä analysoidaksesi myyntidatasi:

![Agenttipalvelu toiminnassa](../../../translated_images/fi/agent-service-in-action.34fb465c9a84659e.webp)

Voit käyttää mitä tahansa näistä työkaluista palvelun kanssa luomalla asiakkaan ja määrittelemällä työkalun tai työkalupakin. Käytännössä voimme käyttää seuraavaa Python-koodia. LLM voi tarkastella työkalupakkia ja päättää käyttääkö se käyttäjän luomaa funktiota `fetch_sales_data_using_sqlite_query` vai valmista Code Interpreteria käyttäjän pyynnön mukaan.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query -funktio, joka löytyy tiedostosta fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Alusta työkalupakki
toolset = ToolSet()

# Alusta funktiokutsujen agentti fetch_sales_data_using_sqlite_query -funktiolla ja lisää se työkalupakkiin
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Alusta Koodin tulkki -työkalu ja lisää se työkalupakkiin.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Mitä erityisiä huomioita liittyy Työkalujen käyttö -suunnittelumallin käyttämiseen luotettavien AI-agenttien rakentamiseksi?

Yleinen huoli LLM:n dynaamisesti generoiman SQL:n osalta liittyy tietoturvaan, erityisesti SQL-injektion riskiin tai haitallisiin toimiin, kuten tietokannan poistamiseen tai muokkaamiseen. Vaikka nämä huolet ovat perusteltuja, ne voidaan tehokkaasti torjua konfiguroimalla tietokannan käyttöoikeudet oikein. Useimmissa tietokannoissa tämä tarkoittaa konfigurointia vain luku -tilaan. Tietokantapalveluissa kuten PostgreSQL tai Azure SQL sovellukselle määritellään vain lukuoikeudet (SELECT-rooli).

Sovelluksen ajaminen suojatussa ympäristössä vahvistaa suojaa entisestään. Yritysskenaarioissa data yleensä poimitaan ja muunnetaan operatiivisista järjestelmistä vain luku -tietokannaksi tai tietovarastoksi käyttäjäystävällisellä skeemalla. Tämä varmistaa, että data on turvallista, optimoitua suorituskyvyn ja saavutettavuuden kannalta, ja että sovelluksella on rajoitettu, vain luku -käyttöoikeus.

## Esimerkkikoodit
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Haluatko lisäkysymyksiä työkalujen käyttöön suunnittelumalleissa?

Liity [Microsoft Foundry Discordiin](https://aka.ms/ai-agents/discord) tapataksesi muita oppijoita, osallistuaksesi toimistotunteihin ja saadaksesi vastauksia AI-agenttien kysymyksiisi.

## Lisäresurssit

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service -työpaja</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Moni-agentti-työpaja</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Funktiokutsujen opas</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Koodin tulkki</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Työkalut</a>

## Edellinen Oppitunti

[Agentic Design Patternsin ymmärtäminen](../03-agentic-design-patterns/README.md)

## Seuraava Oppitunti

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastuuvapauslauseke**:  
Tämä asiakirja on käännetty käyttäen tekoälypohjaista käännöspalvelua [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, huomioithan, että automaattiset käännökset saattavat sisältää virheitä tai epätarkkuuksia. Alkuperäinen asiakirja sen alkuperäiskielellä on virallinen lähde. Tärkeissä asioissa suositellaan ammattilaisten tekemää ihmiskäännöstä. Emme ole vastuussa mahdollisista väärinkäsityksistä tai virhetulkinnasta, jotka johtuvat tämän käännöksen käytöstä.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->