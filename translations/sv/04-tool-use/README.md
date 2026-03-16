[![How to Design Good AI Agents](../../../translated_images/sv/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Klicka på bilden ovan för att se videon av denna lektion)_

# Designmönster för verktygsanvändning

Verktyg är intressanta eftersom de ger AI-agenter en bredare uppsättning förmågor. Istället för att agenten har en begränsad uppsättning åtgärder den kan utföra, kan agenten genom att lägga till ett verktyg nu utföra en mängd olika åtgärder. I detta kapitel kommer vi att titta på designmönstret för verktygsanvändning, som beskriver hur AI-agenter kan använda specifika verktyg för att uppnå sina mål.

## Introduktion

I denna lektion försöker vi besvara följande frågor:

- Vad är designmönstret för verktygsanvändning?
- Vilka användningsfall kan det tillämpas på?
- Vilka element/byggstenar behövs för att implementera designmönstret?
- Vilka särskilda hänsynstaganden finns för att använda designmönstret för verktygsanvändning för att bygga pålitliga AI-agenter?

## Lärandemål

Efter att ha genomgått denna lektion kommer du att kunna:

- Definiera designmönstret för verktygsanvändning och dess syfte.
- Identifiera användningsfall där designmönstret för verktygsanvändning är tillämpligt.
- Förstå de viktigaste elementen som krävs för att implementera designmönstret.
- Känna igen hänsynstaganden för att säkerställa pålitlighet hos AI-agenter som använder detta designmönster.

## Vad är designmönstret för verktygsanvändning?

**Designmönstret för verktygsanvändning** fokuserar på att ge LLM:er förmågan att interagera med externa verktyg för att uppnå specifika mål. Verktyg är kod som kan köras av en agent för att utföra åtgärder. Ett verktyg kan vara en enkel funktion som en kalkylator, eller ett API-anrop till en tredjepartstjänst som aktiekursuppslagning eller väderprognos. I sammanhanget med AI-agenter är verktygen designade för att köras av agenter som svar på **modellgenererade funktionsanrop**.

## Vilka användningsfall kan det tillämpas på?

AI-agenter kan utnyttja verktyg för att slutföra komplexa uppgifter, hämta information eller fatta beslut. Designmönstret för verktygsanvändning används ofta i scenarier som kräver dynamisk interaktion med externa system, såsom databaser, webbtjänster eller kodtolkare. Denna förmåga är användbar för flera olika användningsfall inklusive:

- **Dynamisk informationshämtning:** Agenter kan fråga externa API:er eller databaser för att hämta uppdaterad data (t.ex. fråga en SQLite-databas för dataanalys, hämta aktiekurser eller väderinformation).
- **Kodexekvering och tolkning:** Agenter kan köra kod eller skript för att lösa matematiska problem, generera rapporter eller utföra simuleringar.
- **Automatisering av arbetsflöden:** Automatisering av repetitiva eller flerstegsarbetsflöden genom att integrera verktyg som uppgiftsschemaläggare, e-posttjänster eller datapipelines.
- **Kundsupport:** Agenter kan interagera med CRM-system, ärendehanteringsplattformar eller kunskapsbaser för att lösa användarfrågor.
- **Innehållsgenerering och redigering:** Agenter kan använda verktyg som grammatikkontroller, textsammanfattare eller innehållssäkerhetsutvärderare för att assistera med innehållsskapande uppgifter.

## Vilka element/byggstenar behövs för att implementera designmönstret för verktygsanvändning?

Dessa byggstenar låter AI-agenten utföra ett brett spektrum av uppgifter. Låt oss titta på de nyckelelement som behövs för att implementera designmönstret för verktygsanvändning:

- **Funktions-/verktygsscheman:** Detaljerade definitioner av tillgängliga verktyg, inklusive funktionsnamn, syfte, obligatoriska parametrar och förväntade output. Dessa scheman gör det möjligt för LLM att förstå vilka verktyg som finns tillgängliga och hur man konstruerar giltiga förfrågningar.

- **Logik för funktionskörning:** Styr hur och när verktyg anropas baserat på användarens avsikt och kontext i samtalet. Detta kan inkludera planeringsmoduler, ruttningsmekanismer eller villkorsstyrda flöden som dynamiskt bestämmer verktygsanvändning.

- **Meddelandeshanteringssystem:** Komponenter som hanterar samtalsflödet mellan användarinmatningar, LLM-svar, verktygsanrop och verktygsutdata.

- **Verktygsintegrationsramverk:** Infrastruktur som kopplar agenten till olika verktyg, vare sig de är enkla funktioner eller komplexa externa tjänster.

- **Felhanteirng och validering:** Mekanismer för att hantera fel vid verktygsexekvering, validera parametrar och hantera oväntade svar.

- **Tillståndshantering:** Spårar samtalskontext, tidigare verktygsinteraktioner och persistent data för att säkerställa konsistens över flera turer i interaktionen.

Nästa steg är att titta närmare på funktions-/verktygsanrop.

### Funktions-/verktygsanrop

Funktionsanrop är det primära sättet vi tillåter stora språkmodeller (LLM) att interagera med verktyg. Du ser ofta 'funktion' och 'verktyg' användas omväxlande eftersom 'funktioner' (block av återanvändbar kod) är de 'verktyg' som agenter använder för att utföra uppgifter. För att en funktionskod ska kunna anropas måste en LLM jämföra användarens förfrågan med funktionens beskrivning. För detta skickas ett schema innehållande beskrivningar av alla tillgängliga funktioner till LLM. LLM väljer sedan den mest lämpliga funktionen för uppgiften och returnerar dess namn och argument. Den valda funktionen anropas, dess svar skickas tillbaka till LLM som använder informationen för att svara på användarens förfrågan.

För att utvecklare ska kunna implementera funktionsanrop för agenter behöver du:

1. En LLM-modell som stödjer funktionsanrop
2. Ett schema innehållande funktionsbeskrivningar
3. Koden för varje beskriven funktion

Låt oss använda exemplet att få aktuell tid i en stad som illustration:

1. **Initiera en LLM som stödjer funktionsanrop:**

    Alla modeller stödjer inte funktionsanrop, så det är viktigt att kontrollera att den LLM du använder gör det. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> stödjer funktionsanrop. Vi kan börja med att initiera Azure OpenAI-klienten. 

    ```python
    # Initiera Azure OpenAI-klienten
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Skapa ett funktionsschema:**

    Nästa steg är att definiera ett JSON-schema som innehåller funktionsnamnet, en beskrivning av vad funktionen gör, och namnen samt beskrivningarna av funktionsparametrarna. 
    Vi skickar sedan detta schema till klienten som skapades tidigare, tillsammans med användarens förfrågan att ta reda på tiden i San Francisco. Det viktiga att notera är att ett **verktygsanrop** är vad som returneras, **inte** det slutliga svaret på frågan. Som nämnts ovan returnerar LLM namnet på den funktion den valde för uppgiften och dess argument.

    ```python
    # Funktionsbeskrivning för modellen att läsa
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
  
    # Initialt användarmeddelande
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Första API-anrop: Be modellen använda funktionen
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Bearbeta modellens svar
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Funktionskoden som krävs för att utföra uppgiften:**

    Nu när LLM har valt vilken funktion som ska köras behöver koden som utför uppgiften implementeras och exekveras.
    Vi kan implementera koden för att hämta aktuell tid i Python. Vi behöver också skriva koden för att extrahera namnet och argumenten från response_message för att få slutresultatet.

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
     # Hantera funktionsanrop
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
  
      # Andra API-anropet: Hämta det slutgiltiga svaret från modellen
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

Funktionsanrop är kärnan i de flesta, om inte alla, agenters designmönster för verktygsanvändning, men det kan ibland vara utmanande att implementera det från grunden.
Som vi lärde oss i [Lektion 2](../../../02-explore-agentic-frameworks) ger agentramverk oss förbyggda byggstenar för att implementera verktygsanvändning.
 
## Exempel på verktygsanvändning med agentramverk

Här är några exempel på hur du kan implementera designmönstret för verktygsanvändning med olika agentramverk:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> är ett open source AI-ramverk för .NET, Python och Java-utvecklare som arbetar med stora språkmodeller (LLM). Det förenklar processen att använda funktionsanrop genom att automatiskt beskriva dina funktioner och deras parametrar för modellen genom en process som kallas <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serialisering</a>. Det hanterar också kommunikationen fram och tillbaka mellan modellen och din kod. En annan fördel med att använda ett agentramverk som Semantic Kernel är att det låter dig komma åt förbyggda verktyg som <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Fil-sökning</a> och <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Kodtolkare</a>.

Följande diagram illustrerar processen för funktionsanrop med Semantic Kernel:

![function calling](../../../translated_images/sv/functioncalling-diagram.a84006fc287f6014.webp)

I Semantic Kernel kallas funktioner/verktyg för <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. Vi kan konvertera `get_current_time`-funktionen vi såg tidigare till en plugin genom att göra den till en klass med funktionen inuti. Vi kan också importera `kernel_function`-dekoratören, som tar emot beskrivningen av funktionen. När du sedan skapar en kernel med GetCurrentTimePlugin serialiserar kerneln automatiskt funktionen och dess parametrar, och skapar schemat som skickas till LLM i processen.

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

# Skapa kärnan
kernel = Kernel()

# Skapa pluginen
get_current_time_plugin = GetCurrentTimePlugin(location)

# Lägg till pluginen i kärnan
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> är ett nyare agentramverk som är utformat för att ge utvecklare möjlighet att säkert bygga, implementera och skala högkvalitativa och extensibla AI-agenter utan att behöva hantera de underliggande beräknings- och lagringsresurserna. Det är särskilt användbart för företagsapplikationer eftersom det är en helt hanterad tjänst med säkerhet i företagsklass.

Jämfört med utveckling direkt med LLM API erbjuder Azure AI Agent Service flera fördelar, inklusive:

- Automatiska verktygsanrop – ingen behov av att tolka ett verktygsanrop, anropa verktyget och hantera svaret; allt detta görs nu server-side
- Säker hantering av data – istället för att hantera ditt eget samtalstillstånd kan du förlita dig på trådar för att lagra all information du behöver
- Färdiga verktyg – Verktyg som du kan använda för att interagera med dina datakällor, såsom Bing, Azure AI Search och Azure Functions.

De verktyg som finns tillgängliga i Azure AI Agent Service kan delas in i två kategorier:

1. Kunskapsverktyg:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grundläggande sökning med Bing</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Fil-sökning</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Åtgärdsverktyg:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Funktionsanrop</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Kodtolkare</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI-definierade verktyg</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent-tjänsten gör det möjligt för oss att använda dessa verktyg tillsammans som en `toolset`. Den använder också `threads` som håller reda på historiken för meddelanden från ett särskilt samtal.

Föreställ dig att du är en försäljningsagent på ett företag som heter Contoso. Du vill utveckla en konversationsagent som kan svara på frågor om din försäljningsdata.

Följande bild illustrerar hur du kan använda Azure AI Agent Service för att analysera din försäljningsdata:

![Agentic Service In Action](../../../translated_images/sv/agent-service-in-action.34fb465c9a84659e.webp)

För att använda något av dessa verktyg med tjänsten kan vi skapa en klient och definiera antingen ett verktyg eller en verktygssamling. För att praktiskt implementera detta kan vi använda följande Python-kod. LLM kommer att kunna titta på verktygssamlingen och avgöra om den ska använda den användarskapade funktionen, `fetch_sales_data_using_sqlite_query`, eller den förbyggda Kodtolkaren beroende på användarens fråga.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query-funktion som finns i en fetch_sales_data_functions.py-fil.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Initiera verktygssats
toolset = ToolSet()

# Initiera funktionsanropsagent med fetch_sales_data_using_sqlite_query-funktionen och lägg till den i verktygssatsen
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Initiera Code Interpreter-verktyg och lägg till det i verktygssatsen.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Vilka särskilda hänsynstaganden finns för att använda designmönstret för verktygsanvändning för att bygga pålitliga AI-agenter?

En vanlig oro med SQL som genereras dynamiskt av LLM:er är säkerhet, särskilt risken för SQL-injektion eller skadliga åtgärder som att ta bort eller manipulera databasen. Medan dessa farhågor är giltiga kan de effektivt motverkas genom korrekt konfiguration av databasens åtkomstbehörigheter. För de flesta databaser innebär detta att konfigurera databasen som skrivskyddad. För databastjänster som PostgreSQL eller Azure SQL bör appen tilldelas en skrivskyddad (SELECT) roll.

Att köra appen i en säker miljö förstärker skyddet ytterligare. I företagsmiljöer extraheras och transformeras data vanligtvis från operativa system till en skrivskyddad databas eller datalager med ett användarvänligt schema. Detta tillvägagångssätt säkerställer att data är säkra, optimerade för prestanda och tillgänglighet, och att appen har begränsad, skrivskyddad åtkomst.

## Exempelkoder
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Har du fler frågor om verktygsanvändningsdesignmönster?

Gå med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) för att träffa andra inlärare, delta i kontorstider och få svar på dina frågor om AI-agenter.

## Ytterligare resurser

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## Föregående lektion

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## Nästa lektion

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfriskrivning**:
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Vi strävar efter noggrannhet, men var medveten om att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på dess originalspråk bör anses vara den auktoritativa källan. För viktig information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår genom användning av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->