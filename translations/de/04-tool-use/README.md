[![Wie man gute KI-Agenten entwirft](../../../translated_images/de/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Klicken Sie auf das obige Bild, um das Video zu dieser Lektion anzusehen)_

# Designmuster für Werkzeugnutzung

Werkzeuge sind interessant, weil sie KI-Agenten eine breitere Palette von Fähigkeiten ermöglichen. Anstatt dass der Agent nur eine begrenzte Anzahl von Aktionen ausführen kann, kann der Agent durch Hinzufügen eines Werkzeugs nun eine Vielzahl von Aktionen ausführen. In diesem Kapitel betrachten wir das Designmuster für Werkzeugnutzung, das beschreibt, wie KI-Agenten spezifische Werkzeuge verwenden können, um ihre Ziele zu erreichen.

## Einführung

In dieser Lektion möchten wir die folgenden Fragen beantworten:

- Was ist das Designmuster für Werkzeugnutzung?
- Für welche Anwendungsfälle kann es angewendet werden?
- Welche Elemente/Bausteine werden benötigt, um das Designmuster zu implementieren?
- Welche besonderen Überlegungen gibt es bei der Verwendung des Designmusters für Werkzeugnutzung, um vertrauenswürdige KI-Agenten zu bauen?

## Lernziele

Nach Abschluss dieser Lektion werden Sie in der Lage sein:

- Das Designmuster für Werkzeugnutzung und seinen Zweck zu definieren.
- Anwendungsfälle zu identifizieren, in denen das Designmuster für Werkzeugnutzung anwendbar ist.
- Die Schlüsselelemente zu verstehen, die benötigt werden, um das Designmuster zu implementieren.
- Überlegungen zu erkennen, um Vertrauenswürdigkeit bei KI-Agenten, die dieses Designmuster nutzen, sicherzustellen.

## Was ist das Designmuster für Werkzeugnutzung?

Das **Designmuster für Werkzeugnutzung** konzentriert sich darauf, LLMs die Fähigkeit zu geben, mit externen Werkzeugen zu interagieren, um bestimmte Ziele zu erreichen. Werkzeuge sind Code, der von einem Agenten ausgeführt werden kann, um Aktionen durchzuführen. Ein Werkzeug kann eine einfache Funktion wie ein Taschenrechner oder ein API-Aufruf zu einem Drittanbieterdienst wie Aktienkursabfrage oder Wettervorhersage sein. Im Kontext von KI-Agenten sind Werkzeuge so konzipiert, dass sie von Agenten als Reaktion auf **modellgenerierte Funktionsaufrufe** ausgeführt werden.

## Für welche Anwendungsfälle kann es angewendet werden?

KI-Agenten können Werkzeuge nutzen, um komplexe Aufgaben zu erledigen, Informationen abzurufen oder Entscheidungen zu treffen. Das Designmuster für Werkzeugnutzung wird häufig in Szenarien verwendet, die eine dynamische Interaktion mit externen Systemen erfordern, wie Datenbanken, Webservices oder Code-Interpreter. Diese Fähigkeit ist nützlich für verschiedene Anwendungsfälle, darunter:

- **Dynamische Informationsabfrage:** Agenten können externe APIs oder Datenbanken abfragen, um aktuelle Daten zu erhalten (z. B. Abfrage einer SQLite-Datenbank zur Datenanalyse, Abrufen von Aktienkursen oder Wetterinformationen).
- **Code-Ausführung und Interpretation:** Agenten können Code oder Skripte ausführen, um mathematische Probleme zu lösen, Berichte zu erstellen oder Simulationen durchzuführen.
- **Workflow-Automatisierung:** Automatisierung von wiederkehrenden oder mehrstufigen Arbeitsabläufen durch Integration von Werkzeugen wie Task-Schedulern, E-Mail-Diensten oder Daten-Pipelines.
- **Kundensupport:** Agenten können mit CRM-Systemen, Ticketplattformen oder Wissensdatenbanken interagieren, um Benutzeranfragen zu lösen.
- **Inhaltserstellung und -bearbeitung:** Agenten können Werkzeuge wie Grammatikprüfer, Textzusammenfasser oder Inhaltsicherheitsbewertungen nutzen, um bei der Inhaltserstellung zu helfen.

## Welche Elemente/Bausteine werden benötigt, um das Designmuster für Werkzeugnutzung zu implementieren?

Diese Bausteine ermöglichen es dem KI-Agenten, eine breite Palette von Aufgaben auszuführen. Werfen wir einen Blick auf die Schlüsselelemente, die zur Implementierung des Designmusters für Werkzeugnutzung benötigt werden:

- **Funktions-/Werkzeugschemata**: Detaillierte Definitionen der verfügbaren Werkzeuge, einschließlich Funktionsname, Zweck, erforderliche Parameter und erwartete Ausgaben. Diese Schemata ermöglichen es dem LLM zu verstehen, welche Werkzeuge verfügbar sind und wie gültige Anfragen formuliert werden.

- **Funktionsausführungslogik**: Steuert, wie und wann Werkzeuge basierend auf der Absicht des Benutzers und dem Gesprächskontext aufgerufen werden. Dies kann Planungsmodule, Routing-Mechanismen oder bedingte Abläufe umfassen, die die Werkzeugnutzung dynamisch bestimmen.

- **Nachrichtenverwaltungssystem**: Komponenten, die den Gesprächsfluss zwischen Benutzereingaben, LLM-Antworten, Werkzeugaufrufen und Werkzeugausgaben verwalten.

- **Werkzeugintegrations-Framework**: Infrastruktur, die den Agenten mit verschiedenen Werkzeugen verbindet, egal ob einfache Funktionen oder komplexe externe Dienste.

- **Fehlerbehandlung & Validierung**: Mechanismen zum Umgang mit Fehlern bei der Werkzeugausführung, zur Validierung von Parametern und zur Handhabung unerwarteter Antworten.

- **Statusverwaltung**: Verfolgt den Gesprächskontext, vorherige Werkzeuginteraktionen und persistente Daten, um Konsistenz über mehrstufige Interaktionen hinweg sicherzustellen.

Als nächstes betrachten wir Funktions-/Werkzeugaufrufe etwas genauer.

### Funktions-/Werkzeugaufrufe

Funktionsaufrufe sind der primäre Weg, um Large Language Models (LLMs) die Interaktion mit Werkzeugen zu ermöglichen. Man sieht oft, dass „Funktion“ und „Werkzeug“ synonym verwendet werden, weil „Funktionen“ (wiederverwendbare Codeblöcke) die „Werkzeuge“ sind, die Agenten verwenden, um Aufgaben auszuführen. Damit der Code einer Funktion aufgerufen werden kann, muss ein LLM die Benutzeranfrage mit der Funktionsbeschreibung abgleichen. Dazu wird ein Schema mit Beschreibungen aller verfügbaren Funktionen an das LLM gesendet. Das LLM wählt dann die passendste Funktion für die Aufgabe aus und gibt deren Namen und Argumente zurück. Die ausgewählte Funktion wird aufgerufen, die Antwort wird an das LLM zurückgesendet, das diese Informationen nutzt, um auf die Benutzeranfrage zu antworten.

Um Funktionsaufrufe für Agenten zu implementieren, benötigen Entwickler:

1. Ein LLM-Modell, das Funktionsaufrufe unterstützt
2. Ein Schema mit Funktionsbeschreibungen
3. Den Code für jede beschriebene Funktion

Um dies zu veranschaulichen, verwenden wir das Beispiel, die aktuelle Zeit in einer Stadt abzurufen:

1. **Initialisieren eines LLM, das Funktionsaufrufe unterstützt:**

    Nicht alle Modelle unterstützen Funktionsaufrufe, daher ist es wichtig zu prüfen, ob das von Ihnen verwendete LLM dies tut.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> unterstützt Funktionsaufrufe. Wir können beginnen, indem wir den Azure OpenAI-Client initialisieren.

    ```python
    # Initialisiere den Azure OpenAI-Client
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Erstellen eines Funktionsschemas:**

    Als Nächstes definieren wir ein JSON-Schema, das den Funktionsnamen, eine Beschreibung der Funktion sowie die Namen und Beschreibungen der Funktionsparameter enthält.
    Dieses Schema übergeben wir dann zusammen mit der Benutzeranfrage an den zuvor erstellten Client, um die Zeit in San Francisco zu ermitteln. Wichtig ist zu beachten, dass ein **Werkzeugaufruf** zurückgegeben wird, **nicht** die endgültige Antwort auf die Frage. Wie bereits erwähnt, gibt das LLM den Namen der Funktion zurück, die es für die Aufgabe ausgewählt hat, sowie die Argumente, die an sie übergeben werden.

    ```python
    # Funktionsbeschreibung zum Einlesen durch das Modell
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
  
    # Initiale Benutzeranfrage
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Erster API-Aufruf: Frage das Modell, die Funktion zu verwenden
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Verarbeite die Antwort des Modells
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Der Funktionscode zur Ausführung der Aufgabe:**

    Nun da das LLM entschieden hat, welche Funktion ausgeführt werden muss, muss der Code implementiert und ausgeführt werden, der die Aufgabe ausführt.
    Wir können den Code in Python schreiben, um die aktuelle Zeit zu erhalten. Wir müssen auch den Code schreiben, um den Namen und die Argumente aus der response_message zu extrahieren, um das endgültige Ergebnis zu erhalten.

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
     # Funktionenaufrufe behandeln
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
  
      # Zweiter API-Aufruf: Hole die endgültige Antwort vom Modell
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

Funktionsaufrufe stehen im Zentrum der meisten, wenn nicht aller Designmuster für den Werkzeuggebrauch bei Agenten, jedoch kann ihre Implementierung von Grund auf manchmal herausfordernd sein.
Wie wir in [Lektionen 2](../../../02-explore-agentic-frameworks) gelernt haben, stellen agentische Frameworks vorgefertigte Bausteine bereit, um Werkzeugnutzung umzusetzen.

## Beispiele für Werkzeugnutzung mit agentischen Frameworks

Hier sind einige Beispiele, wie Sie das Designmuster für Werkzeugnutzung mit verschiedenen agentischen Frameworks implementieren können:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> ist ein Open-Source-KI-Framework für .NET-, Python- und Java-Entwickler, die mit Large Language Models (LLMs) arbeiten. Es vereinfacht die Nutzung von Funktionsaufrufen, indem es Ihre Funktionen und deren Parameter automatisch über einen Prozess namens <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Serialisierung</a> beschreibt. Es übernimmt auch die Kommunikation zwischen dem Modell und Ihrem Code. Ein weiterer Vorteil eines agentischen Frameworks wie Semantic Kernel ist, dass es Ihnen den Zugriff auf vorgefertigte Werkzeuge wie <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Dateisuche</a> und <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a> ermöglicht.

Das folgende Diagramm illustriert den Prozess des Funktionsaufrufs mit Semantic Kernel:

![Funktionsaufrufe](../../../translated_images/de/functioncalling-diagram.a84006fc287f6014.webp)

In Semantic Kernel werden Funktionen/Werkzeuge <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a> genannt. Wir können die zuvor gezeigte Funktion `get_current_time` in ein Plugin umwandeln, indem wir sie in eine Klasse integrieren. Wir können auch den Decorator `kernel_function` importieren, der die Funktionsbeschreibung übernimmt. Wenn man dann einen Kernel mit dem GetCurrentTimePlugin erstellt, serialisiert der Kernel automatisch die Funktion und ihre Parameter und erstellt dabei das Schema, das an das LLM gesendet wird.

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

# Erstelle den Kernel
kernel = Kernel()

# Erstelle das Plugin
get_current_time_plugin = GetCurrentTimePlugin(location)

# Füge das Plugin zum Kernel hinzu
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> ist ein neueres agentisches Framework, das Entwicklern ermöglicht, hochwertige und erweiterbare KI-Agenten sicher zu erstellen, bereitzustellen und zu skalieren, ohne sich um die zugrundeliegenden Compute- und Speicherressourcen kümmern zu müssen. Es ist besonders nützlich für Unternehmensanwendungen, da es ein vollständig verwalteter Dienst mit Unternehmenssicherheitsstandard ist.

Im Vergleich zur direkten Entwicklung mit der LLM-API bietet der Azure AI Agent Service einige Vorteile, darunter:

- Automatischer Werkzeugaufruf – keine Notwendigkeit, einen Werkzeugaufruf zu parsen, das Werkzeug aufzurufen und die Antwort zu verarbeiten; all dies geschieht jetzt serverseitig
- Sicher verwaltete Daten – statt den eigenen Gesprächszustand zu verwalten, können Sie Threads nutzen, die alle notwendigen Informationen speichern
- Fertige Werkzeuge – Werkzeuge, mit denen Sie mit Ihren Datenquellen interagieren können, wie Bing, Azure AI Search und Azure Functions.

Die im Azure AI Agent Service verfügbaren Werkzeuge lassen sich in zwei Kategorien unterteilen:

1. Wissenswerkzeuge:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding mit Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Dateisuche</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Aktionswerkzeuge:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Funktionsaufrufe</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI-definierte Werkzeuge</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Der Agent Service ermöglicht es uns, diese Werkzeuge zusammen als `toolset` zu verwenden. Er nutzt außerdem `Threads`, die die Historie der Nachrichten eines bestimmten Gesprächstrackings speichern.

Stellen Sie sich vor, Sie sind Vertriebsmitarbeiter bei einem Unternehmen namens Contoso. Sie möchten einen Konversationsagenten entwickeln, der Fragen zu Ihren Vertriebsdaten beantworten kann.

Das folgende Bild zeigt, wie Sie Azure AI Agent Service verwenden könnten, um Ihre Vertriebsdaten zu analysieren:

![Agentic Service in Aktion](../../../translated_images/de/agent-service-in-action.34fb465c9a84659e.webp)

Um eines dieser Werkzeuge mit dem Dienst zu nutzen, können wir einen Client erstellen und ein Werkzeug oder Toolset definieren. Um dies praktisch umzusetzen, können wir den folgenden Python-Code verwenden. Das LLM kann das Toolset betrachten und entscheiden, ob es die benutzerdefinierte Funktion `fetch_sales_data_using_sqlite_query` oder den vorgefertigten Code Interpreter abhängig von der Benutzeranfrage verwendet.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query Funktion, die in einer Datei fetch_sales_data_functions.py zu finden ist.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Werkzeugset initialisieren
toolset = ToolSet()

# Funktion zur Agentenaufruf mit der fetch_sales_data_using_sqlite_query Funktion initialisieren und zum Werkzeugset hinzufügen
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Code Interpreter Werkzeug initialisieren und zum Werkzeugset hinzufügen.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Welche besonderen Überlegungen gibt es bei der Verwendung des Designmusters für Werkzeugnutzung, um vertrauenswürdige KI-Agenten zu bauen?

Ein häufiges Anliegen bei dynamisch durch LLM generiertem SQL ist die Sicherheit, insbesondere das Risiko von SQL-Injection oder böswilligen Aktionen wie dem Löschen oder Manipulieren der Datenbank. Obwohl diese Bedenken berechtigt sind, lassen sie sich durch eine ordnungsgemäße Konfiguration der Datenbankzugriffsberechtigungen effektiv mindern. Für die meisten Datenbanken bedeutet dies, die Datenbank als schreibgeschützt zu konfigurieren. Für Datenbankdienste wie PostgreSQL oder Azure SQL sollte der Anwendung eine schreibgeschützte (SELECT) Rolle zugewiesen werden.

Der Betrieb der Anwendung in einer sicheren Umgebung erhöht den Schutz zusätzlich. In Unternehmensszenarien werden Daten typischerweise extrahiert und von operativen Systemen in eine schreibgeschützte Datenbank oder ein Data Warehouse mit einer benutzerfreundlichen Schemaform transformiert. Dieses Vorgehen stellt sicher, dass die Daten sicher, für Leistung und Zugänglichkeit optimiert sind und dass die Anwendung einen eingeschränkten, schreibgeschützten Zugriff hat.

## Beispielcodes
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Haben Sie weitere Fragen zur Verwendung von Design Patterns im Tool?

Treten Sie dem [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) bei, um andere Lernende zu treffen, an Sprechstunden teilzunehmen und Antworten auf Ihre AI Agents Fragen zu erhalten.

## Zusätzliche Ressourcen

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## Vorherige Lektion

[Verstehen von agentenbasierten Designmustern](../03-agentic-design-patterns/README.md)

## Nächste Lektion

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Haftungsausschluss**:  
Dieses Dokument wurde mit dem KI-Übersetzungsdienst [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir bemüht sind, Genauigkeit zu gewährleisten, beachten Sie bitte, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in seiner Ausgangssprache gilt als maßgebliche Quelle. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die aus der Nutzung dieser Übersetzung entstehen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->