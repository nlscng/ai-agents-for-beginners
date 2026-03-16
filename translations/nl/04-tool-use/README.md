[![Hoe ontwerp je goede AI-agenten](../../../translated_images/nl/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Klik op de afbeelding hierboven om de video van deze les te bekijken)_

# Tool Use Design Pattern

Tools zijn interessant omdat ze AI-agenten in staat stellen een breder scala aan mogelijkheden te hebben. In plaats van dat de agent een beperkte set acties kan uitvoeren, kan de agent met het toevoegen van een tool nu een breed scala aan acties uitvoeren. In dit hoofdstuk bekijken we het Tool Use Design Pattern, dat beschrijft hoe AI-agenten specifieke tools kunnen gebruiken om hun doelen te bereiken.

## Inleiding

In deze les willen we de volgende vragen beantwoorden:

- Wat is het tool use design pattern?
- Voor welke use cases kan het worden toegepast?
- Welke elementen/bouwstenen zijn nodig om het design pattern te implementeren?
- Welke speciale overwegingen zijn er bij het gebruiken van het Tool Use Design Pattern om betrouwbare AI-agenten te bouwen?

## Leerdoelen

Na het voltooien van deze les kun je:

- Het Tool Use Design Pattern definiëren en het doel ervan uitleggen.
- Use cases identificeren waar het Tool Use Design Pattern toepasbaar is.
- De belangrijkste elementen begrijpen die nodig zijn om het design pattern te implementeren.
- Overwegingen herkennen om betrouwbaarheid te waarborgen in AI-agenten die dit design pattern gebruiken.

## Wat is het Tool Use Design Pattern?

Het **Tool Use Design Pattern** richt zich op het geven van LLM's de mogelijkheid om te interageren met externe tools om specifieke doelen te bereiken. Tools zijn code die door een agent kan worden uitgevoerd om acties uit te voeren. Een tool kan een eenvoudige functie zijn, zoals een calculator, of een API-aanroep naar een externe dienst, zoals aandelenkoers opvragen of een weersvoorspelling. In de context van AI-agenten zijn tools ontworpen om te worden uitgevoerd door agenten als reactie op **door het model gegenereerde functie-aanroepen**.

## Voor welke use cases kan het worden toegepast?

AI-agenten kunnen tools gebruiken om complexe taken uit te voeren, informatie op te halen of beslissingen te nemen. Het tool use design pattern wordt vaak toegepast in situaties die dynamische interactie met externe systemen vereisen, zoals databases, webservices of code-interpreters. Deze mogelijkheid is nuttig voor verschillende use cases, waaronder:

- **Dynamische informatieopvraging:** Agenten kunnen externe API's of databases raadplegen om actuele gegevens op te halen (bijv. een SQLite-database raadplegen voor data-analyse, aandelenkoersen of weerinformatie ophalen).
- **Code-uitvoering en interpretatie:** Agenten kunnen code of scripts uitvoeren om wiskundige problemen op te lossen, rapporten te genereren of simulaties uit te voeren.
- **Workflow-automatisering:** Het automatiseren van repetitieve of meerstapsprocessen door tools te integreren zoals taakplanners, e-maildiensten of datapijplijnen.
- **Klantenservice:** Agenten kunnen interacteren met CRM-systemen, ticketplatforms of kennisbanken om gebruikersvragen op te lossen.
- **Contentcreatie en -bewerking:** Agenten kunnen tools gebruiken zoals grammatica-controleurs, tekstsamenvatters of contentveiligheidsbeoordelaars om te helpen bij contentcreatie.

## Welke elementen/bouwstenen zijn nodig voor het implementeren van het tool use design pattern?

Deze bouwstenen stellen de AI-agent in staat om een breed scala aan taken uit te voeren. Laten we de belangrijkste elementen bekijken die nodig zijn om het Tool Use Design Pattern te implementeren:

- **Functie/Tool-schemas**: Gedetailleerde definities van beschikbare tools, inclusief functienaam, doel, vereiste parameters en verwachte outputs. Deze schemas stellen de LLM in staat te begrijpen welke tools beschikbaar zijn en hoe geldige verzoeken te construeren.

- **Functie-uitvoeringslogica**: Regelt hoe en wanneer tools worden aangeroepen op basis van de intentie van de gebruiker en de context van het gesprek. Dit kan planner-modules, routeringsmechanismen of voorwaardelijke flows omvatten die het gebruik van tools dynamisch bepalen.

- **Berichtafhandelingssysteem**: Componenten die de gespreksstroom beheren tussen gebruikersinvoer, LLM-antwoorden, tool-aanroepen en tool-uitvoeringen.

- **Tool-integratieframework**: Infrastructuur die de agent verbindt met verschillende tools, of het nu eenvoudige functies of complexe externe diensten zijn.

- **Foutafhandeling & validatie**: Mechanismen om fouten bij tool-uitvoering af te handelen, parameters te valideren en onverwachte reacties te beheren.

- **Statusbeheer**: Houdt de gesprekcontext, eerdere tool-interacties en persistente data bij om consistentie te waarborgen over meerdere gespreksronden.

Laten we nu dieper ingaan op Functie/Tool-aanroepen.
 
### Functie/Tool-aanroepen

Functie-aanroepen zijn de primaire manier waarop we Large Language Models (LLM’s) in staat stellen te communiceren met tools. Je zult vaak zien dat 'Function' en 'Tool' door elkaar worden gebruikt omdat 'functies' (herbruikbare stukjes code) de 'tools' zijn die agenten gebruiken om taken uit te voeren. Om de code van een functie aan te roepen, moet een LLM het verzoek van de gebruiker vergelijken met de beschrijving van de functie. Hiervoor wordt een schema met de beschrijvingen van alle beschikbare functies naar de LLM gestuurd. De LLM selecteert dan de meest geschikte functie voor de taak en geeft de naam en argumenten terug. De geselecteerde functie wordt uitgevoerd, het antwoord wordt teruggestuurd naar de LLM, die deze informatie gebruikt om te reageren op het verzoek van de gebruiker.

Voor ontwikkelaars die functie-aanroepen voor agenten willen implementeren, heb je het volgende nodig:

1. Een LLM-model dat functie-aanroepen ondersteunt
2. Een schema met functieomschrijvingen
3. De code voor elke beschreven functie

Laten we het voorbeeld gebruiken van het opvragen van de huidige tijd in een stad om dit te illustreren:

1. **Initialiseer een LLM die functie-aanroepen ondersteunt:**

    Niet alle modellen ondersteunen functie-aanroepen, dus het is belangrijk na te gaan of de LLM die je gebruikt dat doet. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> ondersteunt functie-aanroepen. We kunnen beginnen met het initiëren van de Azure OpenAI-client.

    ```python
    # Initialiseer de Azure OpenAI-client
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Maak een Functie-schema aan**:

    Vervolgens definiëren we een JSON-schema dat de functienaam, een beschrijving van wat de functie doet, en de namen en omschrijvingen van de functieparameters bevat.
    Daarna geven we dit schema samen met het verzoek van de gebruiker door aan de eerder aangemaakte client, met het verzoek de tijd in San Francisco op te zoeken. Het is belangrijk op te merken dat wat wordt teruggegeven een **tool-aanroep** is, **niet** het definitieve antwoord op de vraag. Zoals eerder genoemd, retourneert de LLM de naam van de geselecteerde functie en de argumenten die aan deze functie worden doorgegeven.

    ```python
    # Functiebeschrijving voor het model om te lezen
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
  
    # Initiële gebruikersboodschap
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Eerste API-aanroep: Vraag het model de functie te gebruiken
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Verwerk de reactie van het model
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **De functiecode die nodig is om de taak uit te voeren:**

    Zodra de LLM heeft gekozen welke functie moet worden uitgevoerd, moet de code die de taak uitvoert worden geïmplementeerd en uitgevoerd.
    We kunnen de code implementeren om de huidige tijd in Python op te halen. We moeten ook de code schrijven om de naam en argumenten uit het response_message te extraheren om het uiteindelijke resultaat te krijgen.

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
     # Afhandelen van functieverzoeken
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
  
      # Tweede API-aanroep: Haal de definitieve reactie van het model op
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

Functie-aanroepen staan centraal in de meeste, zo niet alle, agent tool use designs, maar het kan soms uitdagend zijn om dit vanaf nul te implementeren.
Zoals we leerden in [Les 2](../../../02-explore-agentic-frameworks), bieden agentische frameworks voorgemaakte bouwstenen om toolgebruik te implementeren.
 
## Voorbeelden van Tool Use met Agentische Frameworks

Hier zijn enkele voorbeelden van hoe je het Tool Use Design Pattern kunt implementeren met verschillende agentische frameworks:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> is een open-source AI-framework voor .NET-, Python- en Java-ontwikkelaars die werken met Large Language Models (LLM’s). Het vereenvoudigt het gebruik van functie-aanroepen door automatisch je functies en parameters te beschrijven aan het model via een proces genaamd <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serialiseren</a>. Het regelt ook de heen-en-weer communicatie tussen het model en je code. Een ander voordeel van het gebruik van een agentisch framework zoals Semantic Kernel is dat je toegang krijgt tot vooraf gebouwde tools zoals <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Bestandszoeker</a> en <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

De volgende diagram illustreert het proces van functie-aanroepen met Semantic Kernel:

![functie-aanroepen](../../../translated_images/nl/functioncalling-diagram.a84006fc287f6014.webp)

In Semantic Kernel worden functies/tools <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a> genoemd. We kunnen de eerder genoemde `get_current_time` functie omzetten in een plugin door deze in een klasse te plaatsen met de functie erin. We kunnen ook de `kernel_function` decorator importeren, die de beschrijving van de functie aanneemt. Wanneer je dan een kernel maakt met de GetCurrentTimePlugin, zal de kernel automatisch de functie en parameters serialiseren en zo het schema creëren dat naar de LLM wordt gestuurd.

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

# Maak de kernel aan
kernel = Kernel()

# Maak de plugin aan
get_current_time_plugin = GetCurrentTimePlugin(location)

# Voeg de plugin toe aan de kernel
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> is een nieuwer agentisch framework dat is ontworpen om ontwikkelaars in staat te stellen veilig hoogwaardige en uitbreidbare AI-agenten te bouwen, deployen en schalen, zonder dat ze de onderliggende compute- en opslagresources hoeven te beheren. Het is met name handig voor bedrijfsapplicaties omdat het een volledig beheerde service is met veiligheidsmaatregelen op ondernemingsniveau.

In vergelijking met directe ontwikkeling met de LLM API biedt Azure AI Agent Service enkele voordelen, waaronder:

- Automatische tool-aanroepen – er is geen parsing van tool-aanroepen, uitvoeren van tools en afhandelen van antwoorden nodig; dit wordt nu server-side afgehandeld
- Veilig beheer van data – in plaats van zelf statusbeheer te doen, kun je vertrouwen op threads die alle benodigde informatie bewaren
- Direct beschikbare tools – tools die je kunt gebruiken om met je databronnen te interacteren, zoals Bing, Azure AI Search, en Azure Functions.

De tools beschikbaar in Azure AI Agent Service kunnen worden onderverdeeld in twee categorieën:

1. Kennis-tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Fundering met Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Bestandszoeker</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Actietools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Functie-aanroepen</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI-gedefinieerde tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

De Agent Service stelt ons in staat om deze tools samen te gebruiken als een `toolset`. Het maakt ook gebruik van `threads` die de geschiedenis van berichten uit een specifiek gesprek bijhouden.

Stel je voor dat je een sales agent bent bij een bedrijf genaamd Contoso. Je wilt een conversatie-agent ontwikkelen die vragen over je verkoopdata kan beantwoorden.

De volgende afbeelding illustreert hoe je Azure AI Agent Service kunt gebruiken om je verkoopdata te analyseren:

![Agentic Service in actie](../../../translated_images/nl/agent-service-in-action.34fb465c9a84659e.webp)

Om een van deze tools te gebruiken met de service kunnen we een client aanmaken en een tool of toolset definiëren. Om dit praktisch te implementeren kunnen we de volgende Python-code gebruiken. De LLM kan dan naar de toolset kijken en beslissen of de door de gebruiker gemaakte functie `fetch_sales_data_using_sqlite_query` of de vooraf gebouwde Code Interpreter moet worden gebruikt, afhankelijk van het verzoek van de gebruiker.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query functie die te vinden is in een fetch_sales_data_functions.py bestand.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Initialiseer toolset
toolset = ToolSet()

# Initialiseer function calling agent met de fetch_sales_data_using_sqlite_query functie en voeg deze toe aan de toolset
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Initialiseer Code Interpreter tool en voeg deze toe aan de toolset.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Welke speciale overwegingen zijn er bij het gebruik van het Tool Use Design Pattern voor het bouwen van betrouwbare AI-agenten?

Een veelvoorkomende zorg bij door LLM's dynamisch gegenereerde SQL is veiligheid, vooral het risico van SQL-injectie of kwaadaardige acties, zoals het verwijderen of manipuleren van de database. Hoewel deze zorgen terecht zijn, kunnen ze effectief worden verminderd door de database-toegangsrechten correct te configureren. Voor de meeste databases betekent dit dat de database als alleen-lezen wordt ingesteld. Voor databaseservices zoals PostgreSQL of Azure SQL moet de app een alleen-lezen (SELECT) rol toegewezen krijgen.

Het draaien van de applicatie in een veilige omgeving verhoogt de bescherming nog verder. In bedrijfsomgevingen wordt data meestal geëxtraheerd en getransformeerd van operationele systemen naar een alleen-lezen database of datawarehouse met een gebruikersvriendelijk schema. Deze aanpak zorgt ervoor dat de data beveiligd, geoptimaliseerd voor prestaties en toegankelijkheid is, en dat de app beperkte, alleen-lezen toegang heeft.

## Voorbeeldcodes
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Meer vragen over het gebruik van ontwerppatronen voor tools?

Sluit je aan bij de [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) om andere leerlingen te ontmoeten, deel te nemen aan inloopuren en antwoord te krijgen op je vragen over AI Agents.

## Aanvullende bronnen

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## Vorige les

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## Volgende les

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dit document is vertaald met behulp van de AI-vertalingsservice [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel wij streven naar nauwkeurigheid, kan het voorkomen dat geautomatiseerde vertalingen fouten of onnauwkeurigheden bevatten. Het oorspronkelijke document in de oorspronkelijke taal moet als de gezaghebbende bron worden beschouwd. Voor belangrijke informatie wordt professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->