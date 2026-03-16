[![How to Design Good AI Agents](../../../translated_images/da/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Klik på billedet ovenfor for at se video af denne lektion)_

# Tool Use Design Pattern

Værktøjer er interessante, fordi de giver AI-agenter mulighed for at have en bredere rækkevidde af kapaciteter. I stedet for at agenten har et begrænset sæt af handlinger, den kan udføre, kan agenten ved at tilføje et værktøj nu udføre et bredt udvalg af handlinger. I dette kapitel vil vi se på Tool Use Design Pattern, som beskriver, hvordan AI-agenter kan bruge specifikke værktøjer for at nå deres mål.

## Introduktion

I denne lektion vil vi forsøge at besvare følgende spørgsmål:

- Hvad er tool use design pattern?
- Hvilke anvendelsestilfælde kan det anvendes på?
- Hvilke elementer/byggeblokke er nødvendige for at implementere designmønsteret?
- Hvilke særlige overvejelser findes der ved brug af Tool Use Design Pattern til at bygge troværdige AI-agenter?

## Læringsmål

Efter at have gennemført denne lektion vil du kunne:

- Definere Tool Use Design Pattern og dets formål.
- Identificere anvendelsestilfælde hvor Tool Use Design Pattern er anvendeligt.
- Forstå nøgleelementerne der er nødvendige for at implementere designmønsteret.
- Genkende overvejelser for at sikre troværdighed i AI-agenter, der bruger dette designmønster.

## Hvad er Tool Use Design Pattern?

**Tool Use Design Pattern** fokuserer på at give LLM'er mulighed for at interagere med eksterne værktøjer for at opnå specifikke mål. Værktøjer er kode, som kan eksekveres af en agent for at udføre handlinger. Et værktøj kan være en simpel funktion såsom en regnemaskine eller et API-kald til en tredjepartstjeneste såsom aktiekursopslag eller vejrudsigter. I konteksten af AI-agenter er værktøjer designet til at blive udført af agenter som svar på **modelgenererede funktionskald**.

## Hvilke anvendelsestilfælde kan det anvendes på?

AI-agenter kan benytte værktøjer til at fuldføre komplekse opgaver, hente information eller træffe beslutninger. Tool use design pattern bruges ofte i scenarier, der kræver dynamisk interaktion med eksterne systemer som databaser, webservices eller kodefortolkere. Denne evne er nyttig i en række forskellige anvendelsestilfælde herunder:

- **Dynamisk informationshentning:** Agenter kan forespørge eksterne API'er eller databaser for at hente opdaterede data (f.eks. forespørgsel til en SQLite database til dataanalyse, hente aktiekurser eller vejrinformation).
- **Kodeeksekvering og fortolkning:** Agenter kan eksekvere kode eller scripts for at løse matematiske problemer, generere rapporter eller foretage simuleringer.
- **Automatisering af arbejdsprocesser:** Automatisering af gentagne eller flertrins arbejdsprocesser ved at integrere værktøjer som opgavestyring, e-mail-tjenester eller datapipelines.
- **Kundesupport:** Agenter kan interagere med CRM-systemer, ticketplatforme eller vidensbaser for at løse brugerhenvendelser.
- **Indholdsskabelse og redigering:** Agenter kan bruge værktøjer som grammatikkontrol, tekstopsummering eller vurdering af indholdssikkerhed til at assistere ved indholdsskabelse.

## Hvilke elementer/byggeblokke er nødvendige for at implementere tool use design pattern?

Disse byggeblokke gør det muligt for AI-agenten at udføre et bredt udvalg af opgaver. Lad os se på nøgleelementerne der er nødvendige for at implementere Tool Use Design Pattern:

- **Funktions-/Værktøjsskemaer**: Detaljerede definitioner af tilgængelige værktøjer, herunder funktionsnavn, formål, nødvendige parametre og forventede output. Disse skemaer gør det muligt for LLM at forstå, hvilke værktøjer der er tilgængelige og hvordan man konstruerer gyldige anmodninger.

- **Funktionsudførelseslogik**: Styrer hvordan og hvornår værktøjer kaldes baseret på brugerens hensigt og samtalekontekst. Dette kan inkludere planlægningsmoduler, routingmekanismer eller betingede flows, der dynamisk bestemmer brugen af værktøjer.

- **Beskedhåndteringssystem**: Komponenter, der håndterer samtaleforløbet mellem brugerinput, LLM-svar, værktøjskald og værktøjsrespons.

- **Værktøjsintegrationsrammeværk**: Infrastruktur, der forbinder agenten til forskellige værktøjer, hvad enten det er simple funktioner eller komplekse eksterne services.

- **Fejlhåndtering & Validering**: Mekanismer til at håndtere fejl ved værktøjsudførelse, validere parametre og håndtere uventede svar.

- **Statusstyring**: Sporer samtalekontekst, tidligere værktøjsinteraktioner og vedvarende data for at sikre konsistens på tværs af multi-turn interaktioner.

Lad os nu se nærmere på Funktions-/Værktøjskald.

### Funktions-/Værktøjskald

Funktionskald er den primære måde, hvorpå vi giver Store Sprogsmodeller (LLM'er) mulighed for at interagere med værktøjer. Man vil ofte se 'Function' og 'Tool' brugt om hinanden, fordi 'funktioner' (genanvendelige kodeblokke) er de 'værktøjer', agenter bruger til at udføre opgaver. For at en funktionskode kan blive kaldt, skal en LLM sammenligne brugerens forespørgsel med funktionens beskrivelse. Til dette sendes et skema, der indeholder beskrivelser af alle tilgængelige funktioner, til LLM'en. LLM'en vælger derefter den mest passende funktion til opgaven og returnerer dens navn og argumenter. Den valgte funktion udføres, og dens svar sendes tilbage til LLM'en, som bruger informationen til at besvare brugerens forespørgsel.

For udviklere der ønsker at implementere funktionskald for agenter, har I brug for:

1. En LLM-model, der understøtter funktionskald
2. Et skema med funktionsbeskrivelser
3. Koden til hver beskrevet funktion

Lad os bruge eksemplet med at få aktuelt tidspunkt i en by til at illustrere:

1. **Initialiser en LLM, der understøtter funktionskald:**

    Ikke alle modeller understøtter funktionskald, så det er vigtigt at kontrollere, at den LLM, du bruger, gør det. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> understøtter funktionskald. Vi kan starte med at initialisere Azure OpenAI klienten. 

    ```python
    # Initialiser Azure OpenAI-klienten
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Opret et Funktionsskema**:

    Dernæst vil vi definere et JSON-skema, der indeholder funktionsnavn, beskrivelse af hvad funktionen gør, og navne samt beskrivelser af funktionsparametre.
    Vi sender dette skema til den oprettede klient sammen med brugerens forespørgsel om at finde tidspunktet i San Francisco. Det vigtige at bemærke er, at det, der returneres, er et **værktøjskald**, **ikke** det endelige svar på spørgsmålet. Som tidligere nævnt returnerer LLM navnet på den funktion, den har valgt til opgaven, og de argumenter, der skal sendes ind.

    ```python
    # Funktionsbeskrivelse for modellen at læse
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
  
    # Initial brugerbesked
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Første API-kald: Bed modellen om at bruge funktionen
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Behandl modellens svar
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Den nødvendige funktionskode til at udføre opgaven:**

    Nu hvor LLM har valgt, hvilken funktion der skal køres, skal koden, der udfører opgaven, implementeres og eksekveres.
    Vi kan implementere koden til at hente den aktuelle tid i Python. Vi skal også skrive koden til at udtrække navn og argumenter fra response_message for at få det endelige resultat.

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
     # Håndter funktionskald
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
  
      # Andet API-kald: Få det endelige svar fra modellen
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

Funktionskald er kernen i det meste, hvis ikke al tool use design, men det kan til tider være udfordrende at implementere dette fra bunden.
Som vi lærte i [Lektion 2](../../../02-explore-agentic-frameworks) giver agentiske frameworks os forbyggede byggeblokke til at implementere tool use.

## Eksempler på Tool Use med Agentiske Frameworks

Her er nogle eksempler på, hvordan du kan implementere Tool Use Design Pattern ved hjælp af forskellige agentiske frameworks:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> er et open source AI-framework til .NET, Python og Java-udviklere, der arbejder med Store Sprogsmodeller (LLM'er). Det forenkler processen med at bruge funktionskald ved automatisk at beskrive dine funktioner og deres parametre til modellen gennem en proces kaldet <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serialisering</a>. Det håndterer også kommunikationen frem og tilbage mellem modellen og din kode. En anden fordel ved at bruge et agentisk framework som Semantic Kernel er, at det giver adgang til færdigbyggede værktøjer som <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> og <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Følgende diagram illustrerer processen med funktionskald med Semantic Kernel:

![function calling](../../../translated_images/da/functioncalling-diagram.a84006fc287f6014.webp)

I Semantic Kernel kaldes funktioner/værktøjer <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. Vi kan konvertere den `get_current_time`-funktion, vi så tidligere, til et plugin ved at gøre den til en klasse med funktionen indeni. Vi kan også importere `kernel_function` dekoratoren, som tager beskrivelsen af funktionen. Når du så opretter en kernel med GetCurrentTimePlugin, vil kernelen automatisk serialisere funktionen og dens parametre og skabe skemaet til at sende til LLM'en i processen.

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

# Opret kernen
kernel = Kernel()

# Opret plugin'et
get_current_time_plugin = GetCurrentTimePlugin(location)

# Tilføj plugin'et til kernen
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> er et nyere agentisk framework, designet til at give udviklere mulighed for sikkert at bygge, implementere og skalere AI-agenter af høj kvalitet og med udvidelsesmuligheder uden at skulle håndtere de underliggende compute- og lagringsressourcer. Det er særligt nyttigt til virksomhedsapplikationer, da det er en fuldt administreret service med sikkerhed i virksomhedsklasse.

Sammenlignet med at udvikle direkte med LLM API, tilbyder Azure AI Agent Service nogle fordele, herunder:

- Automatisk værktøjskald – ikke brug for at parse et værktøjskald, kalde værktøjet og håndtere svaret; alt dette foregår nu server-side
- Sikkert håndterede data – i stedet for selv at styre samtalestatus kan man stole på threads, som gemmer al nødvendig information
- Out-of-the-box værktøjer – Værktøjer du kan bruge til at interagere med dine datakilder, såsom Bing, Azure AI Search og Azure Functions.

De værktøjer, der er tilgængelige i Azure AI Agent Service, kan opdeles i to kategorier:

1. Videnværktøjer:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding med Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Aktionsværktøjer:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI-definerede værktøjer</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agentservicen giver os mulighed for at bruge disse værktøjer sammen som et `toolset`. Det benytter også `threads`, som holder styr på beskedhistorikken i en bestemt samtale.

Forestil dig, at du er en salgsagent hos en virksomhed kaldet Contoso. Du ønsker at udvikle en samtaleagent, der kan besvare spørgsmål om dine salgsdata.

Følgende billede illustrerer, hvordan du kan bruge Azure AI Agent Service til at analysere dine salgsdata:

![Agentic Service In Action](../../../translated_images/da/agent-service-in-action.34fb465c9a84659e.webp)

For at bruge nogen af disse værktøjer med servicen kan vi oprette en klient og definere et værktøj eller værktøjssæt. For at implementere dette praktisk kan vi bruge følgende Python-kode. LLM'en vil kunne se på værktøjssættet og afgøre, om den skal bruge den brugeroprettede funktion `fetch_sales_data_using_sqlite_query` eller den forbyggede Code Interpreter afhængigt af brugerens forespørgsel.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query-funktion, som findes i en fil ved navn fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Initialiser værktøjssæt
toolset = ToolSet()

# Initialiser funktionskaldsagent med fetch_sales_data_using_sqlite_query-funktionen og tilføj den til værktøjssættet
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Initialiser Code Interpreter-værktøj og tilføj det til værktøjssættet.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Hvilke særlige overvejelser findes ved brug af Tool Use Design Pattern til at bygge troværdige AI-agenter?

En almindelig bekymring ved SQL dynamisk genereret af LLM'er er sikkerhed, især risikoen for SQL injection eller ondsindede handlinger som at slette eller manipulere databasen. Selvom disse bekymringer er valide, kan de effektivt afbødes ved korrekt konfiguration af databaseadgangstilladelser. For de fleste databaser betyder dette at konfigurere databasen som read-only. For databaseservices som PostgreSQL eller Azure SQL bør appen tildeles en read-only (SELECT) rolle.

At køre appen i et sikkert miljø øger beskyttelsen yderligere. I virksomhedsscenarier udtrækkes og transformeres data typisk fra operationelle systemer til en read-only database eller datalager med et brugervenligt skema. Denne tilgang sikrer, at data er sikre, optimeret til ydeevne og tilgængelighed, og at appen kun har begrænset, læseadgang.

## Eksempelkoder
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Har du flere spørgsmål om værktøjsbrugsdesignmønstre?

Deltag i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for at møde andre lærende, deltage i kontortimer og få besvaret dine spørgsmål om AI-agenter.

## Yderligere ressourcer

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## Forrige lektion

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## Næste lektion

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, bedes du være opmærksom på, at automatiserede oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets modersmål bør betragtes som den autoritative kilde. For kritisk information anbefales professionel menneskelig oversættelse. Vi påtager os intet ansvar for eventuelle misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->