# Erkundung des Microsoft Agent Framework

![Agent Framework](../../../translated_images/de/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Einführung

Diese Lektion behandelt:

- Verständnis des Microsoft Agent Framework: Hauptmerkmale und Nutzen  
- Erkundung der Schlüsselkonzepte des Microsoft Agent Framework
- Vergleich von MAF mit Semantic Kernel und AutoGen: Migrationsleitfaden

## Lernziele

Nach Abschluss dieser Lektion wissen Sie, wie Sie:

- Produktionsreife KI-Agenten mit dem Microsoft Agent Framework erstellen
- Die Kernfunktionen des Microsoft Agent Framework auf Ihre agentischen Anwendungsfälle anwenden
- Bestehende agentische Frameworks und Tools migrieren und integrieren  

## Code-Beispiele

Code-Beispiele für [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) finden Sie in diesem Repository unter den Dateien `xx-python-agent-framework` und `xx-dotnet-agent-framework`.

## Verständnis des Microsoft Agent Framework

![Framework Intro](../../../translated_images/de/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) baut auf den Erfahrungen und Erkenntnissen von Semantic Kernel und AutoGen auf. Es bietet die Flexibilität, die Vielzahl agentischer Anwendungsfälle abzudecken, die sowohl in Produktions- als auch in Forschungsumgebungen zu finden sind, darunter:

- **Sequenzielle Agenten-Orchestrierung** in Szenarien, in denen Schritt-für-Schritt-Arbeitsabläufe erforderlich sind.
- **Gleichzeitige Orchestrierung** in Szenarien, in denen Agenten Aufgaben gleichzeitig erledigen müssen.
- **Gruppenchat-Orchestrierung** in Szenarien, in denen Agenten gemeinsam an einer Aufgabe arbeiten können.
- **Übergabe-Orchestrierung** in Szenarien, in denen Agenten die Aufgabe aneinander übergeben, sobald Teilaufgaben abgeschlossen sind.
- **Magnetische Orchestrierung** in Szenarien, in denen ein Manager-Agent eine Aufgabenliste erstellt und verändert und die Koordination der Unteragenten zur Erledigung der Aufgabe übernimmt.

Um KI-Agenten in der Produktion bereitzustellen, enthält MAF außerdem Funktionen für:

- **Beobachtbarkeit** durch den Einsatz von OpenTelemetry, wobei jede Aktion des KI-Agenten einschließlich Werkzeugaufrufen, Orchestrierungsschritten, Argumentationsabläufen und Leistungsüberwachung über Microsoft Foundry Dashboards erfasst wird.
- **Sicherheit** durch native Ausführung der Agenten auf Microsoft Foundry, das Sicherheitskontrollen wie rollenbasierte Zugriffssteuerung, Handhabung privater Daten und integrierte Inhalts-Sicherheit beinhaltet.
- **Beständigkeit** da Agenten-Threads und Arbeitsabläufe pausieren, fortsetzen und Fehler wiederherstellen können, was längere Prozesse ermöglicht.
- **Kontrolle** da Workflows mit menschlicher Einbindung unterstützt werden, bei denen Aufgaben als zur menschlichen Genehmigung erforderlich markiert sind.

Das Microsoft Agent Framework legt zudem Wert auf Interoperabilität durch:

- **Cloud-Unabhängigkeit** – Agenten können in Containern, lokal (on-premises) und in verschiedenen Clouds ausgeführt werden.
- **Anbieter-Unabhängigkeit** – Agenten können mit dem bevorzugten SDK erstellt werden, einschließlich Azure OpenAI und OpenAI.
- **Integration offener Standards** – Agenten können Protokolle wie Agent-to-Agent (A2A) und Model Context Protocol (MCP) verwenden, um andere Agenten und Werkzeuge zu entdecken und zu nutzen.
- **Plugins und Connectoren** – Verbindungen zu Daten- und Speicher-Services wie Microsoft Fabric, SharePoint, Pinecone und Qdrant sind möglich.

Sehen wir uns an, wie diese Funktionen auf einige der Kernkonzepte des Microsoft Agent Framework angewendet werden.

## Schlüsselkonzepte des Microsoft Agent Framework

### Agenten

![Agent Framework](../../../translated_images/de/agent-components.410a06daf87b4fef.webp)

**Erstellen von Agenten**

Die Erstellung von Agenten erfolgt durch Definition des Inferenzdienstes (LLM-Anbieter), eine Reihe von Anweisungen, denen der KI-Agent folgen soll, und einen zugewiesenen `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Oben wird `Azure OpenAI` verwendet, aber Agenten können mit verschiedenen Diensten erstellt werden, einschließlich `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

oder entfernte Agenten unter Verwendung des A2A-Protokolls:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Ausführen von Agenten**

Agenten werden mit den Methoden `.run` oder `.run_stream` für nicht-streamende oder streamende Antworten ausgeführt.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Jeder Agentenlauf kann auch Optionen zur Anpassung von Parametern wie `max_tokens`, die vom Agenten verwendet werden, `tools`, die der Agent aufrufen kann, und sogar das `model`, das für den Agenten verwendet wird, enthalten.

Dies ist nützlich in Fällen, in denen bestimmte Modelle oder Werkzeuge für die Ausführung der Benutzeraufgabe erforderlich sind.

**Werkzeuge**

Werkzeuge können sowohl bei der Definition des Agenten festgelegt werden:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Beim direkten Erstellen eines ChatAgenten

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

als auch beim Ausführen des Agenten:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Werkzeug nur für diesen Lauf bereitgestellt )
```

**Agenten-Threads**

Agenten-Threads werden für Multi-Turn-Konversationen verwendet. Threads können entweder durch

- Verwendung von `get_new_thread()` erstellt werden, was ermöglicht, dass der Thread über die Zeit gespeichert wird
- automatisches Erstellen eines Threads beim Ausführen eines Agenten, der nur während der aktuellen Ausführung bestehen bleibt.

Der Code zur Erstellung eines Threads sieht so aus:

```python
# Erstelle einen neuen Thread.
thread = agent.get_new_thread() # Führe den Agenten mit dem Thread aus.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Danach kann der Thread serialisiert werden, um ihn später zu speichern:

```python
# Erstelle einen neuen Thread.
thread = agent.get_new_thread() 

# Führe den Agenten mit dem Thread aus.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serialisiere den Thread zur Speicherung.

serialized_thread = await thread.serialize() 

# Deserialisiere den Thread-Zustand nach dem Laden aus der Speicherung.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agenten-Middleware**

Agenten interagieren mit Werkzeugen und LLMs, um Benutzeraufgaben zu erfüllen. In bestimmten Szenarien möchten wir Aktionen ausführen oder zwischen diesen Interaktionen verfolgen. Agenten-Middleware ermöglicht dies durch:

*Funktions-Middleware*

Diese Middleware erlaubt es uns, eine Aktion zwischen dem Agenten und einer Funktion/einem Werkzeug, das aufgerufen wird, auszuführen. Ein Beispiel für deren Verwendung ist das Protokollieren eines Funktionsaufrufs.

Im untenstehenden Code definiert `next`, ob die nächste Middleware oder die eigentliche Funktion aufgerufen werden soll.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Vorverarbeitung: Protokoll vor der Funktionsausführung
    print(f"[Function] Calling {context.function.name}")

    # Weiter zum nächsten Middleware- oder Funktionsaufruf
    await next(context)

    # Nachverarbeitung: Protokoll nach der Funktionsausführung
    print(f"[Function] {context.function.name} completed")
```

*Chat-Middleware*

Diese Middleware erlaubt es, eine Aktion zwischen dem Agenten und den Anfragen an das LLM auszuführen oder zu protokollieren.

Sie enthält wichtige Informationen wie die `messages`, die an den KI-Dienst gesendet werden.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Vorverarbeitung: Protokoll vor dem KI-Aufruf
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Weiter zum nächsten Middleware oder KI-Dienst
    await next(context)

    # Nachverarbeitung: Protokoll nach KI-Antwort
    print("[Chat] AI response received")

```

**Agenten-Speicher**

Wie in der Lektion `Agentic Memory` behandelt, ist Speicher ein wichtiges Element, um den Agenten zu ermöglichen, über verschiedene Kontexte hinweg zu agieren. MAF bietet verschiedene Arten von Speicher:

*Im-Arbeitsspeicher*

Dies ist der während der Anwendungszeit gespeicherte Speicher in Threads.

```python
# Erstellen Sie einen neuen Thread.
thread = agent.get_new_thread() # Führen Sie den Agenten mit dem Thread aus.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Persistente Nachrichten*

Dieser Speicher wird verwendet, um den Gesprächsverlauf über verschiedene Sitzungen hinweg zu speichern. Er wird über die `chat_message_store_factory` definiert:

```python
from agent_framework import ChatMessageStore

# Erstellen Sie einen benutzerdefinierten Nachrichtenstore
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamischer Speicher*

Dieser Speicher wird dem Kontext hinzugefügt, bevor Agenten ausgeführt werden. Diese Speicher können in externen Diensten wie mem0 gespeichert werden:

```python
from agent_framework.mem0 import Mem0Provider

# Verwendung von Mem0 für erweiterte Speicherfunktionen
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**Agenten-Beobachtbarkeit**

Beobachtbarkeit ist wichtig, um zuverlässige und wartbare agentische Systeme zu bauen. MAF integriert sich mit OpenTelemetry, um Tracing und Metriken für eine bessere Beobachtbarkeit bereitzustellen.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # etwas tun
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Workflows

MAF bietet Workflows als vordefinierte Schritte zur Erledigung einer Aufgabe, die KI-Agenten als Komponenten in diesen Schritten enthalten.

Workflows bestehen aus verschiedenen Komponenten, die einen besseren Kontrollfluss ermöglichen. Workflows unterstützen außerdem **Multi-Agenten-Orchestrierung** und **Checkpointing**, um Workflow-Zustände zu speichern.

Die Kernkomponenten eines Workflows sind:

**Executoren**

Executoren erhalten Eingabenachrichten, führen ihre zugewiesenen Aufgaben aus und erzeugen eine Ausgabenachricht. Dies bringt den Workflow voran, um die größere Aufgabe zu erledigen. Executoren können KI-Agenten oder benutzerdefinierte Logik sein.

**Verbindungen (Edges)**

Verbindungen definieren den Nachrichtenfluss in einem Workflow. Diese können sein:

*Direkte Verbindungen* - Einfache Eins-zu-eins-Verbindungen zwischen Executoren:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Bedingte Verbindungen* - Werden aktiviert, nachdem eine bestimmte Bedingung erfüllt ist. Zum Beispiel kann ein Executor bei nicht verfügbaren Hotelzimmern andere Optionen vorschlagen.

*Switch-Case-Verbindungen* - Leiten Nachrichten basierend auf definierten Bedingungen an verschiedene Executoren weiter. Zum Beispiel wenn ein Reisekunde Prioritätszugang hat und seine Aufgaben durch einen anderen Workflow abgewickelt werden.

*Sternförmige Verbindungen (Fan-out)* - Sendet eine Nachricht an mehrere Ziele.

*Sternförmige Zusammenführungen (Fan-in)* - Sammelt mehrere Nachrichten von verschiedenen Executoren und sendet sie an ein Ziel.

**Ereignisse**

Um eine bessere Beobachtbarkeit von Workflows zu ermöglichen, bietet MAF integrierte Ereignisse für die Ausführung, darunter:

- `WorkflowStartedEvent`  - Workflow-Ausführung beginnt
- `WorkflowOutputEvent` - Workflow erzeugt eine Ausgabe
- `WorkflowErrorEvent` - Workflow stößt auf einen Fehler
- `ExecutorInvokeEvent`  - Executor beginnt mit der Verarbeitung
- `ExecutorCompleteEvent`  -  Executor beendet die Verarbeitung
- `RequestInfoEvent` - Eine Anforderung wird ausgegeben

## Migration von anderen Frameworks (Semantic Kernel und AutoGen)

### Unterschiede zwischen MAF und Semantic Kernel

**Vereinfachte Agentenerstellung**

Semantic Kernel erfordert die Erstellung einer Kernel-Instanz für jeden Agenten. MAF verwendet einen vereinfachten Ansatz durch Nutzung von Erweiterungen für die Hauptanbieter.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Erstellung von Agenten-Threads**

Im Semantic Kernel müssen Threads manuell erstellt werden. In MAF wird einem Agenten direkt ein Thread zugewiesen.

```python
thread = agent.get_new_thread() # Führen Sie den Agenten mit dem Thread aus.
```

**Werkzeug-Registrierung**

Im Semantic Kernel werden Werkzeuge beim Kernel registriert und dieser dann an den Agenten übergeben. In MAF werden Werkzeuge direkt während der Agentenerstellung registriert.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Unterschiede zwischen MAF und AutoGen

**Teams vs Workflows**

`Teams` sind die Event-Struktur für ereignisgesteuerte Aktivitäten mit Agenten in AutoGen. MAF verwendet `Workflows`, die Daten an Executoren über eine graphbasierte Architektur leiten.

**Werkzeugerstellung**

AutoGen verwendet `FunctionTool`, um Funktionen für Agenten aufzubereiten. MAF nutzt @ai_function, welches ähnlich funktioniert, aber auch automatisch die Schemata für jede Funktion ableitet.

**Agenten-Verhalten**

Agenten sind standardmäßig in AutoGen Single-Turn-Agenten, es sei denn `max_tool_iterations` wird auf einen höheren Wert gesetzt. Im MAF ist der `ChatAgent` standardmäßig Multi-Turn, was bedeutet, dass er Werkzeuge solange aufruft, bis die Benutzeraufgabe abgeschlossen ist.

## Code-Beispiele

Code-Beispiele für Microsoft Agent Framework finden Sie in diesem Repository unter den Dateien `xx-python-agent-framework` und `xx-dotnet-agent-framework`.

## Haben Sie weitere Fragen zum Microsoft Agent Framework?

Treten Sie dem [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) bei, um andere Lernende zu treffen, an Sprechstunden teilzunehmen und Ihre Fragen zu KI-Agenten beantwortet zu bekommen.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Haftungsausschluss**:  
Dieses Dokument wurde mit dem KI-Übersetzungsdienst [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, können automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten. Das Originaldokument in seiner Herkunftssprache ist als maßgebliche Quelle zu betrachten. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die aus der Verwendung dieser Übersetzung entstehen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->