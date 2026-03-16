[![Jak navrhnout dobré AI agenty](../../../translated_images/cs/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Klikněte na obrázek výše pro zobrazení videa této lekce)_

# Vzor návrhu používání nástrojů

Nástroje jsou zajímavé, protože umožňují AI agentům mít širší škálu schopností. Místo toho, aby agent měl omezenou sadu akcí, které může provádět, přidáním nástroje může agent nyní vykonávat širokou škálu akcí. V této kapitole se podíváme na vzor návrhu používání nástrojů, který popisuje, jak AI agenti mohou používat specifické nástroje k dosažení svých cílů.

## Úvod

V této lekci se snažíme odpovědět na následující otázky:

- Co je vzor návrhu používání nástrojů?
- Na jaké případy použití lze tento vzor aplikovat?
- Jaké prvky/stavební bloky jsou potřeba k implementaci tohoto vzoru?
- Jaká jsou speciální ohledání pro použití vzoru návrhu používání nástrojů k vytvoření důvěryhodných AI agentů?

## Cíle učení

Po dokončení této lekce budete schopni:

- Definovat vzor návrhu používání nástrojů a jeho účel.
- Identifikovat případy použití, kde je vzor návrhu používání nástrojů použitelný.
- Pochopit klíčové prvky potřebné k implementaci tohoto vzoru.
- Rozpoznat úvahy pro zajištění důvěryhodnosti AI agentů používajících tento vzor.

## Co je vzor návrhu používání nástrojů?

**Vzor návrhu používání nástrojů** se zaměřuje na umožnění LLMům interagovat s externími nástroji k dosažení specifických cílů. Nástroje jsou kód, který může agent spustit k vykonání akcí. Nástrojem může být jednoduchá funkce, například kalkulačka, nebo volání API na službu třetí strany, jako je vyhledání ceny akcií nebo předpověď počasí. V kontextu AI agentů jsou nástroje navrženy tak, aby byly spouštěny agenty jako odpověď na **modelem generované volání funkcí**.

## Na jaké případy použití lze vzor aplikovat?

AI agenti mohou využívat nástroje k dokončení složitých úkolů, získání informací nebo k rozhodování. Vzor používání nástrojů se často využívá v situacích, které vyžadují dynamickou interakci s externími systémy, jako jsou databáze, webové služby nebo interpretery kódu. Tato schopnost je užitečná pro mnoho různých případů použití, včetně:

- **Dynamické získávání informací:** Agenti mohou dotazovat externí API nebo databáze pro získání aktuálních dat (např. dotazování SQLite databáze pro analýzu dat, získání cen akcií nebo informací o počasí).
- **Spouštění a interpretace kódu:** Agenti mohou spouštět kód nebo skripty k řešení matematických problémů, generování zpráv nebo provádění simulací.
- **Automatizace pracovních postupů:** Automatizace opakujících se nebo více krokových pracovních postupů integrací nástrojů jako plánovače úkolů, e-mailových služeb nebo datových toků.
- **Zákaznická podpora:** Agenti mohou komunikovat s CRM systémy, ticketovacími platformami nebo znalostními bázemi k řešení dotazů uživatelů.
- **Tvorba a úprava obsahu:** Agenti mohou využívat nástroje jako kontroly gramatiky, shrnování textu nebo hodnocení bezpečnosti obsahu k podpoře tvorby obsahu.

## Jaké prvky/stavební bloky jsou potřeba k implementaci vzoru používání nástrojů?

Tyto stavební bloky umožňují AI agentovi vykonávat širokou škálu úkolů. Podívejme se na klíčové prvky potřebné k implementaci vzoru používání nástrojů:

- **Schémata funkcí/nástrojů**: Podrobné definice dostupných nástrojů, včetně názvu funkce, účelu, požadovaných parametrů a očekávaných výstupů. Tato schémata umožňují LLM pochopit, jaké nástroje jsou k dispozici a jak vytvořit platné požadavky.

- **Logika spouštění funkcí:** Řídí, jak a kdy jsou nástroje vyvolány na základě úmyslu uživatele a kontextu konverzace. Může zahrnovat moduly plánovače, mechanismy směrování nebo podmíněné toky určující dynamické využívání nástrojů.

- **Systém zpracování zpráv:** Komponenty, které spravují tok konverzace mezi uživatelskými vstupy, odpověďmi LLM, voláními nástrojů a výstupy nástrojů.

- **Rámec integrace nástrojů:** Infrastruktura, která propojuje agenta s různými nástroji, ať už jsou to jednoduché funkce nebo složité externí služby.

- **Řízení chyb a validace:** Mechanismy pro řešení selhání při vykonávání nástrojů, ověřování parametrů a správu neočekávaných odpovědí.

- **Správa stavu:** Sleduje konverzační kontext, předchozí interakce s nástroji a perzistentní data zajišťující konzistenci přes více kol interakcí.

Dále si podrobněji vysvětlíme volání funkcí/nástrojů.

### Volání funkcí/nástrojů

Volání funkcí je primární způsob, jak umožnit velkým jazykovým modelům (LLM) interakci s nástroji. Často uvidíte termíny „funkce“ a „nástroj“ používané zaměnitelně, protože „funkce“ (bloky znovupoužitelného kódu) jsou právě „nástroji“, které agenti používají k vykonávání úkolů. Aby bylo možné vyvolat kód funkce, musí LLM porovnat žádost uživatele s popisem funkcí. K tomu se LLM zasílá schéma obsahující popisy všech dostupných funkcí. LLM pak vybere nejvhodnější funkci pro úkol a vrátí její název a argumenty. Vybraná funkce je spuštěna, její odpověď se pošle zpět LLM, které použije informace k odpovědi uživateli.

Pro vývojáře, kteří chtějí implementovat volání funkcí pro agenty, je potřeba:

1. Model LLM, který podporuje volání funkcí
2. Schéma obsahující popisy funkcí
3. Kód pro každou popsanou funkci

Použijme příklad získání aktuálního času ve městě k ilustraci:

1. **Inicializujte LLM, které podporuje volání funkcí:**

    Ne všechny modely podporují volání funkcí, proto je důležité ověřit, zda vaše LLM tuto funkci má. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> podporuje volání funkcí. Můžeme začít vytvořením klienta Azure OpenAI. 

    ```python
    # Inicializujte klienta Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Vytvořte schéma funkce:**

    Dále definujeme JSON schéma, které obsahuje název funkce, popis toho, co funkce dělá, a názvy a popisy parametrů funkce.
    Toto schéma pak předáme dříve vytvořenému klientovi společně s uživatelskou žádostí o zjištění času v San Franciscu. Je důležité si uvědomit, že je vráceno **volání nástroje**, **nikoli** konečná odpověď na otázku. Jak již bylo zmíněno, LLM vrací název vybrané funkce a argumenty, které jí budou předány.

    ```python
    # Popis funkce pro model ke čtení
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
  
    # Počáteční zpráva uživatele
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # První volání API: Požádejte model, aby použil funkci
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Zpracovat odpověď modelu
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Kód funkce potřebný k vykonání úkolu:**

    Poté, co si LLM vybralo, kterou funkci spustit, je potřeba implementovat a spustit kód, který úkol vykoná.
    Kód pro získání aktuálního času můžeme napsat v Pythonu. Také budeme muset napsat kód pro extrakci názvu a argumentů z `response_message`, abychom dostali konečný výsledek.

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
     # Zpracovat volání funkcí
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
  
      # Druhý požadavek API: Získat konečnou odpověď od modelu
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

Volání funkcí je jádrem většiny, pokud ne všech, návrhů používání nástrojů agentů, ale jeho implementace od začátku může být někdy náročná.
Jak jsme se naučili v [Lekci 2](../../../02-explore-agentic-frameworks), agentní rámce nám poskytují předpřipravené stavební bloky pro implementaci používání nástrojů.
 
## Příklady používání nástrojů s agentními rámci

Zde jsou příklady, jak můžete implementovat vzor návrhu používání nástrojů za použití různých agentních rámců:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> je open-source AI rámec pro vývojáře .NET, Python a Java pracující s velkými jazykovými modely (LLM). Zjednodušuje proces volání funkcí tím, že automaticky popisuje vaše funkce a jejich parametry modelu pomocí procesu nazývaného <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializace</a>. Také se stará o komunikaci tam a zpět mezi modelem a vaším kódem. Další výhodou použití agentního rámce jako Semantic Kernel je, že vám umožňuje přistupovat k předpřipraveným nástrojům jako jsou <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Vyhledávání souborů</a> a <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Interpretr kódu</a>.

Následující diagram ilustruje proces volání funkcí s Semantic Kernel:

![function calling](../../../translated_images/cs/functioncalling-diagram.a84006fc287f6014.webp)

Ve Semantic Kernel jsou funkce/nástroje nazývány <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Pluginy</a>. Funkci `get_current_time`, kterou jsme viděli dříve, můžeme převést na plugin tím, že ji převedeme na třídu s touto funkcí uvnitř. Můžeme také importovat dekorátor `kernel_function`, který přijímá popis funkce. Když pak vytvoříte kernel s GetCurrentTimePlugin, kernel automaticky serializuje funkci a její parametry a při tom vytvoří schéma, které se posílá do LLM.

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

# Vytvořit jádro
kernel = Kernel()

# Vytvořit plugin
get_current_time_plugin = GetCurrentTimePlugin(location)

# Přidat plugin do jádra
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> je novější agentní rámec navržený tak, aby umožnil vývojářům bezpečně vytvářet, nasazovat a škálovat vysoce kvalitní a rozšiřitelné AI agenty, aniž by museli spravovat základní výpočetní a úložné zdroje. Je zvlášť užitečný pro podnikové aplikace, protože jde o plně spravovanou službu s bezpečností na podnikové úrovni.

Ve srovnání s vývojem přímo přes LLM API Azure AI Agent Service nabízí některé výhody, včetně:

- Automatické volání nástrojů – není potřeba analyzovat volání nástroje, vyvolávat nástroj a zpracovávat odpověď; to vše se nyní děje na straně serveru
- Bezpečně spravovaná data – místo správy vlastního stavu konverzace můžete spoléhat na vlákna, která uchovávají všechny potřebné informace
- Hotové nástroje – Nástroje, které můžete použít k interakci s vašimi zdroji dat, jako jsou Bing, Azure AI Search a Azure Functions.

Nástroje dostupné v Azure AI Agent Service lze rozdělit do dvou kategorií:

1. Nástroje pro znalosti:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Zakotvení pomocí Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Vyhledávání souborů</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Akční nástroje:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Volání funkcí</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Interpretr kódu</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">Nástroje definované OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service nám umožňuje používat tyto nástroje společně jako `sadu nástrojů`. Také využívá `vlákna`, která sledují historii zpráv z konkrétní konverzace.

Představte si, že jste prodejní agent ve společnosti Contoso. Chcete vyvinout konverzačního agenta, který dokáže odpovídat na otázky ohledně vašich prodejních dat.

Následující obrázek ilustruje, jak byste mohli použít Azure AI Agent Service pro analýzu vašich prodejních dat:

![Agentic Service In Action](../../../translated_images/cs/agent-service-in-action.34fb465c9a84659e.webp)

Pro použití kterékoli z těchto nástrojů se službou můžeme vytvořit klienta a definovat nástroj nebo sadu nástrojů. K praktické implementaci můžeme použít následující Python kód. LLM pak bude moci zvažovat sadu nástrojů a rozhodnout se, zda použije uživatelem vytvořenou funkci `fetch_sales_data_using_sqlite_query`, nebo předpřipravený Interpretr kódu v závislosti na uživatelské žádosti.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # funkce fetch_sales_data_using_sqlite_query, která se nachází v souboru fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Inicializovat sadu nástrojů
toolset = ToolSet()

# Inicializovat agenta pro volání funkcí s funkcí fetch_sales_data_using_sqlite_query a přidat ji do sady nástrojů
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Inicializovat nástroj Code Interpreter a přidat jej do sady nástrojů.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Jaká jsou speciální ohledání pro použití vzoru návrhu používání nástrojů k vytvoření důvěryhodných AI agentů?

Častou obavou při dynamicky generovaném SQL dotazem LLM je bezpečnost, zejména riziko SQL injekce nebo škodlivých akcí, jako je odstranění nebo manipulace s databází. I když jsou tyto obavy opodstatněné, dají se účinně zmírnit správnou konfigurací přístupových oprávnění k databázi. Pro většinu databází to znamená nastavení databáze jako pouze pro čtení. U databázových služeb jako PostgreSQL nebo Azure SQL by aplikace měla mít přidělenou roli pouze pro čtení (SELECT).

Provozování aplikace v zabezpečeném prostředí ještě více zvyšuje ochranu. V podnikovém prostředí jsou data obvykle extrahována a transformována z provozních systémů do databáze pouze pro čtení nebo datového skladu s přívětivým schématem. Tento přístup zajišťuje, že data jsou bezpečná, optimalizovaná pro výkon a přístupnost a že aplikace má omezený přístup pouze pro čtení.

## Ukázkové kódy
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Máte další otázky ohledně použití návrhových vzorů nástroje?

Připojte se k [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), abyste se setkali s dalšími studenty, zúčastnili se konzultačních hodin a dostali odpovědi na své otázky ohledně AI agentů.

## Další zdroje

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Workshop Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Workshop Contoso Creative Writer Multi-Agent</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Tutoriál pro volání funkcí Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Interpret kódu Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Nástroje</a>

## Předchozí lekce

[Porozumění návrhovým vzorům agentů](../03-agentic-design-patterns/README.md)

## Další lekce

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). I když usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho rodném jazyce by měl být považován za autoritativní zdroj. Pro důležité informace se doporučuje profesionální lidský překlad. Nejsme odpovědní za jakákoliv nedorozumění nebo chybné interpretace vzniklé použitím tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->