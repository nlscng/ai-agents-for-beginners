[![Ako navrhovať dobrých AI agentov](../../../translated_images/sk/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Kliknite na obrázok vyššie pre zobrazenie videa k tejto lekcii)_

# Dizajnový vzor používania nástrojov

Nástroje sú zaujímavé, pretože umožňujú AI agentom mať širší rozsah schopností. Namiesto toho, aby mal agent obmedzený súbor akcií, ktoré môže vykonať, pridaním nástroja môže agent vykonávať širokú škálu akcií. V tejto kapitole si pozrieme dizajnový vzor používania nástrojov, ktorý opisuje, ako môžu AI agenti používať konkrétne nástroje na dosiahnutie svojich cieľov.

## Úvod

V tejto lekcii sa snažíme odpovedať na nasledujúce otázky:

- Čo je dizajnový vzor používania nástrojov?
- Na aké použitia sa môže uplatniť?
- Aké sú prvky/stavebné bloky potrebné na implementáciu dizajnového vzoru?
- Aké sú špeciálne úvahy pri používaní dizajnového vzoru na vytváranie dôveryhodných AI agentov?

## Ciele učenia

Po absolvovaní tejto lekcie budete schopní:

- Definovať dizajnový vzor používania nástrojov a jeho účel.
- Identifikovať prípady použitia, kde je dizajnový vzor aplikovateľný.
- Pochopiť kľúčové prvky potrebné na implementáciu dizajnového vzoru.
- Rozpoznať úvahy na zabezpečenie dôveryhodnosti AI agentov používajúcich tento dizajnový vzor.

## Čo je dizajnový vzor používania nástrojov?

**Dizajnový vzor používania nástrojov** sa sústreďuje na to, aby veľké jazykové modely (LLM) mohli interagovať s externými nástrojmi na dosiahnutie konkrétnych cieľov. Nástroje sú kód, ktorý môže agent vykonať na vykonanie akcií. Nástroj môže byť jednoduchá funkcia, ako je kalkulačka, alebo API volanie na službu tretej strany, napríklad prehľad cien akcií alebo predpoveď počasia. V kontexte AI agentov sú nástroje navrhnuté tak, aby ich agenti spúšťali v reakcii na **funkčné volania generované modelom**.

## Na aké použitia sa môže uplatniť?

AI agenti môžu využiť nástroje na dokončenie zložitých úloh, získavanie informácií alebo prijímanie rozhodnutí. Dizajnový vzor používania nástrojov sa často využíva v situáciách, ktoré vyžadujú dynamickú interakciu s externými systémami, ako sú databázy, webové služby alebo interpretery kódu. Táto schopnosť je užitočná pre rôzne použitia vrátane:

- **Dynamické získavanie informácií:** Agenti môžu dotazovať externé API alebo databázy pre získanie aktuálnych dát (napríklad dotazovanie SQLite databázy pre analýzu dát, získavanie cien akcií alebo informácií o počasí).
- **Spúšťanie a interpretácia kódu:** Agenti môžu vykonávať kód alebo skripty na riešenie matematických problémov, generovanie správ alebo vykonávanie simulácií.
- **Automatizácia pracovných tokov:** Automatizácia opakujúcich sa alebo viacstupňových pracovných tokov integráciou nástrojov ako plánovače úloh, e-mailové služby alebo dátové pipeline.
- **Zákaznícka podpora:** Agenti môžu komunikovať so CRM systémami, ticketovacími platformami alebo databázami znalostí na riešenie používateľských dotazov.
- **Generovanie a úprava obsahu:** Agenti môžu využiť nástroje ako kontroly gramatiky, zhrnovače textu alebo hodnotiace nástroje bezpečnosti obsahu na pomoc s tvorbou obsahu.

## Aké sú prvky/stavebné bloky potrebné na implementáciu dizajnového vzoru používania nástrojov?

Tieto stavebné bloky umožňujú AI agentovi vykonávať širokú škálu úloh. Pozrime sa na kľúčové prvky potrebné na implementáciu dizajnového vzoru používania nástrojov:

- **Schémy funkcií/nástrojov:** Podrobné definície dostupných nástrojov, vrátane názvu funkcie, jej účelu, požadovaných parametrov a očakávaných výstupov. Tieto schémy umožňujú LLM pochopiť, aké nástroje sú k dispozícii a ako zostaviť platné požiadavky.

- **Logika vykonávania funkcií:** Riadí, ako a kedy sú nástroje vyvolané na základe zámeru používateľa a kontextu rozhovoru. Môže zahŕňať plánovacie moduly, mechanizmy smerovania alebo podmienené priechody, ktoré určujú používanie nástrojov dynamicky.

- **Systém spracovania správ:** Komponenty, ktoré riadia konverzačný tok medzi vstupmi používateľa, odpoveďami LLM, volaniami nástrojov a výstupmi nástrojov.

- **Rámec integrácie nástrojov:** Infrastruktúra, ktorá prepája agenta s rôznymi nástrojmi, či už ide o jednoduché funkcie alebo komplexné externé služby.

- **Riešenie chýb a validácia:** Mechanizmy na zvládanie zlyhaní pri vykonávaní nástrojov, overovanie parametrov a riadenie neočakávaných odpovedí.

- **Správa stavu:** Sleduje kontext rozhovoru, predchádzajúce interakcie s nástrojmi a perzistentné dáta na zabezpečenie konzistencie počas viackolových interakcií.

Ďalej si podrobnejšie pozrieme volanie funkcií/nástrojov.

### Volanie funkcií/nástrojov

Volanie funkcií je hlavným spôsobom, ako umožniť veľkým jazykovým modelom (LLMs) interagovať s nástrojmi. Často uvidíte, že „Funkcia“ a „Nástroj“ sa používajú zameniteľne, pretože „funkcie“ (bloky znovupoužiteľného kódu) sú tie „nástroje“, ktoré agenti používajú na vykonávanie úloh. Aby mohla byť vyvolaná funkcia, musí LLM porovnať požiadavku používateľa s popisom funkcie. Na to sa odošle schéma obsahujúca popisy všetkých dostupných funkcií modelu. LLM potom vyberie najvhodnejšiu funkciu pre danú úlohu a vráti jej názov a argumenty. Vybraná funkcia sa spustí, jej odpoveď sa pošle späť do LLM, ktorý použije tieto informácie na odpoveď na požiadavku používateľa.

Pre vývojárov na implementáciu volania funkcií pre agentov budete potrebovať:

1. Model LLM, ktorý podporuje volanie funkcií
2. Schému obsahujúcu popisy funkcií
3. Kód pre každú opísanú funkciu

Použime príklad získania aktuálneho času v meste na ilustráciu:

1. **Inicializujte LLM, ktorý podporuje volanie funkcií:**

    Nie všetky modely podporujú volanie funkcií, preto je dôležité overiť, či váš LLM túto podporu má. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> podporuje volanie funkcií. Môžeme začať inicializáciou klienta Azure OpenAI.

    ```python
    # Inicializujte klienta Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

2. **Vytvorte schému funkcie:**

    Ďalej definujeme JSON schému, ktorá obsahuje názov funkcie, popis toho, čo funkcia robí, a názvy a popisy jej parametrov.
    Túto schému potom pošleme klientovi, ktorý sme vytvorili, spolu s požiadavkou používateľa na zistenie času v San Franciscu. Dôležité je poznamenať, že sa vráti **volanie nástroja**, **nie** konečná odpoveď na otázku. Ako už bolo spomenuté, LLM vráti názov zvolenej funkcie pre úlohu a argumenty, ktoré sa jej predajú.

    ```python
    # Popis funkcie pre načítanie modelu
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
  
    # Počiatočná správa používateľa
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Prvý API hovor: Požiadajte model, aby použil funkciu
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Spracovať odpoveď modelu
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
3. **Kód funkcie potrebný na vykonanie úlohy:**

    Teraz, keď si LLM vybral, ktorá funkcia sa má spustiť, je potrebné implementovať a vykonať kód, ktorý úlohu spracuje.
    Môžeme implementovať kód na získanie aktuálneho času v Pythone. Tiež budeme potrebovať napísať kód na extrakciu názvu a argumentov zo response_message pre získanie konečného výsledku.

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
     # Spracovať volania funkcií
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
  
      # Druhé volanie API: Získať konečnú odpoveď od modelu
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

Volanie funkcií je jadrom väčšiny, ak nie všetkých, dizajnových vzorov používania nástrojov agentov, avšak jeho implementácia od základov môže byť niekedy náročná.
Ako sme sa naučili v [Lekcii 2](../../../02-explore-agentic-frameworks), agentické rámce nám poskytujú pripravené stavebné bloky na zavedenie používania nástrojov.
 
## Príklady používania nástrojov s agentickými rámcami

Tu sú niektoré príklady, ako môžete implementovať dizajnový vzor používania nástrojov s rôznymi agentickými rámcami:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> je open-source AI framework pre .NET, Python a Java vývojárov pracujúcich s veľkými jazykovými modelmi (LLM). Zjednodušuje proces používania volania funkcií tým, že automaticky popisuje vaše funkcie a ich parametre modelu prostredníctvom procesu zvaného <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializácia</a>. Tiež spravuje komunikáciu medzi modelom a vašim kódom. Ďalšou výhodou použitia agentického frameworku ako Semantic Kernel je, že umožňuje prístup k predpripraveným nástrojom, ako je <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> a <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Nasledujúci diagram znázorňuje proces volania funkcií v Semantic Kernel:

![volanie funkcií](../../../translated_images/sk/functioncalling-diagram.a84006fc287f6014.webp)

V Semantic Kernel sa funkcie/nástroje nazývajú <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Pluginy</a>. Môžeme previesť funkciu `get_current_time`, ktorú sme si ukázali skôr, na plugin tak, že ju zabalíme do triedy spolu s funkciou. Môžeme tiež naimportovať dekorátor `kernel_function`, ktorý prijíma popis funkcie. Keď následne vytvoríte kernel s GetCurrentTimePlugin, kernel automaticky serializuje funkciu a jej parametre a vytvorí schému na odoslanie modelu.

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

# Vytvorte jadro
kernel = Kernel()

# Vytvorte plugin
get_current_time_plugin = GetCurrentTimePlugin(location)

# Pridajte plugin do jadra
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> je novší agentický framework navrhnutý tak, aby umožnil vývojárom bezpečne vytvárať, nasadzovať a škálovať vysoko kvalitných a rozšíriteľných AI agentov bez potreby spravovať základné výpočtové zdroje a úložisko. Je obzvlášť užitočný pre podnikové aplikácie, keďže je plne spravovanou službou s bezpečnosťou na úrovni podnikov.

V porovnaní s priamym vývojom cez LLM API, Azure AI Agent Service poskytuje niekoľko výhod, vrátane:

- Automatické volanie nástrojov – nie je potrebné parsovať volanie nástroja, vyvolať nástroj a spracovať odpoveď; všetko sa rieši na strane servera
- Bezpečne spravované údaje – namiesto správy vlastného stavu konverzácie môžete spoľahnúť na vlákna (threads), ktoré ukladajú všetky potrebné informácie
- Predpripravené nástroje – nástroje, ktoré môžete používať na interakciu s vašimi zdrojmi dát, ako sú Bing, Azure AI Search a Azure Functions.

Nástroje dostupné v Azure AI Agent Service možno rozdeliť do dvoch kategórií:

1. Nástroje na prácu so znalosťami:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Práca s Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Nástroje akcií:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Volanie funkcií</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">Nástroje definované pomocou OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service nám umožňuje používať tieto nástroje spolu ako `toolset`. Tiež využíva `vlákna` (threads), ktoré sledujú históriu správ z konkrétnej konverzácie.

Predstavte si, že ste predajný agent v spoločnosti Contoso. Chcete vyvinúť konverzačného agenta, ktorý dokáže odpovedať na otázky týkajúce sa vašich predajných dát.

Nasledujúci obrázok znázorňuje, ako by ste mohli použiť Azure AI Agent Service na analýzu vašich predajných dát:

![Agentická služba v akcii](../../../translated_images/sk/agent-service-in-action.34fb465c9a84659e.webp)

Na používanie ktoréhokoľvek z týchto nástrojov so službou môžeme vytvoriť klienta a definovať nástroj alebo toolset. Prakticky môžeme použiť nasledujúci Python kód. LLM bude schopný na základe toolsetu rozhodnúť, či použije vlastnú funkciu vytvorenú používateľom `fetch_sales_data_using_sqlite_query`, alebo predpripravený Code Interpreter v závislosti od požiadavky používateľa.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # funkcia fetch_sales_data_using_sqlite_query, ktorá sa nachádza v súbore fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Inicializovať súpravu nástrojov
toolset = ToolSet()

# Inicializovať agenta volania funkcií s funkciou fetch_sales_data_using_sqlite_query a pridať ho do súpravy nástrojov
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Inicializovať nástroj Kódový interpret a pridať ho do súpravy nástrojov.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Aké sú špeciálne úvahy pri používaní dizajnového vzoru na vytváranie dôveryhodných AI agentov?

Bežnou obavou pri dynamicky generovanom SQL od LLM je bezpečnosť, najmä riziko SQL injection alebo škodlivých akcií, ako je odstránenie alebo manipulácia s databázou. Aj keď sú tieto obavy opodstatnené, dajú sa účinne zmierniť správnou konfiguráciou prístupových práv k databáze. Pre väčšinu databáz to zahŕňa nastavenie databázy ako iba na čítanie. Pre databázové služby ako PostgreSQL alebo Azure SQL by mala byť aplikácii priradená rola iba na čítanie (SELECT).

Spustenie aplikácie v bezpečnom prostredí ďalej zvyšuje ochranu. V podnikových scenároch sa údaje typicky extrahujú a transformujú z operačných systémov do databázy alebo dátového skladu len na čítanie s užívateľsky prívetivou schémou. Tento prístup zaručuje, že dáta sú zabezpečené, optimalizované pre výkon a prístupnosť, a že aplikácia má obmedzený prístup iba na čítanie.

## Vzorové kódy
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Máte viac otázok o návrhových vzoroch používania nástrojov?

Pridajte sa na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kde sa môžete stretnúť s ďalšími študentmi, zúčastniť sa konzultačných hodín a získať odpovede na svoje otázky o AI agentoch.

## Doplnkové zdroje

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Workshop Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Návod na volanie funkcií v Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Nástroje Autogen</a>

## Predchádzajúca lekcia

[Porozumenie agentným návrhovým vzorom](../03-agentic-design-patterns/README.md)

## Nasledujúca lekcia

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zrieknutie sa zodpovednosti**:
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Aj keď sa snažíme o presnosť, majte prosím na pamäti, že automatizované preklady môžu obsahovať chyby alebo nepresnosti. Originálny dokument v jeho pôvodnom jazyku by mal byť považovaný za autoritatívny zdroj. Pri dôležitých informáciách sa odporúča profesionálny ľudský preklad. Nezodpovedáme za akékoľvek nedorozumenia alebo nesprávne interpretácie vyplývajúce z použitia tohto prekladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->