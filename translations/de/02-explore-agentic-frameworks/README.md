[![Erkundung von KI-Agenten-Frameworks](../../../translated_images/de/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Klicken Sie auf das obige Bild, um das Video zu dieser Lektion anzusehen)_

# Erkundung von KI-Agenten-Frameworks

KI-Agenten-Frameworks sind Softwareplattformen, die entwickelt wurden, um die Erstellung, Bereitstellung und Verwaltung von KI-Agenten zu vereinfachen. Diese Frameworks bieten Entwicklern vorgefertigte Komponenten, Abstraktionen und Werkzeuge, die die Entwicklung komplexer KI-Systeme straffen.

Diese Frameworks helfen Entwicklern, sich auf die einzigartigen Aspekte ihrer Anwendungen zu konzentrieren, indem sie standardisierte Ansätze für häufige Herausforderungen in der Entwicklung von KI-Agenten bereitstellen. Sie verbessern Skalierbarkeit, Zugänglichkeit und Effizienz beim Aufbau von KI-Systemen.

## Einführung 

Diese Lektion behandelt:

- Was sind KI-Agenten-Frameworks und welche Möglichkeiten eröffnen sie Entwicklern?
- Wie können Teams diese nutzen, um schnell Prototypen zu erstellen, zu iterieren und die Fähigkeiten ihres Agenten zu verbessern?
- Was sind die Unterschiede zwischen den von Microsoft erstellten Frameworks und Tools <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> und <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Kann ich meine vorhandenen Azure-Ökosystem-Tools direkt integrieren, oder benötige ich eigenständige Lösungen?
- Was ist der Azure AI Agents-Dienst und wie hilft er mir?

## Lernziele

Ziel dieser Lektion ist es, Ihnen zu helfen, Folgendes zu verstehen:

- Die Rolle von KI-Agenten-Frameworks in der KI-Entwicklung.
- Wie man KI-Agenten-Frameworks nutzt, um intelligente Agenten zu bauen.
- Wichtige Fähigkeiten, die durch KI-Agenten-Frameworks ermöglicht werden.
- Die Unterschiede zwischen AutoGen, Semantic Kernel und Azure AI Agent Service.

## Was sind KI-Agenten-Frameworks und was ermöglichen sie Entwicklern?

Traditionelle KI-Frameworks können Ihnen dabei helfen, KI in Ihre Apps zu integrieren und diese Apps auf folgende Weise zu verbessern:

- **Personalisierung**: KI kann das Nutzerverhalten und Präferenzen analysieren, um personalisierte Empfehlungen, Inhalte und Erlebnisse bereitzustellen.
Beispiel: Streaming-Dienste wie Netflix verwenden KI, um Filme und Serien basierend auf der Wiedergabevergangenheit vorzuschlagen, wodurch die Benutzerbindung und -zufriedenheit erhöht wird.
- **Automatisierung und Effizienz**: KI kann repetitive Aufgaben automatisieren, Arbeitsabläufe straffen und die operative Effizienz verbessern.
Beispiel: Kundenservice-Apps nutzen KI-gesteuerte Chatbots, um häufige Anfragen zu bearbeiten, was die Antwortzeiten verkürzt und menschliche Agenten für komplexere Probleme entlastet.
- **Verbessertes Benutzererlebnis**: KI kann das gesamte Benutzererlebnis verbessern, indem sie intelligente Funktionen wie Spracherkennung, Verarbeitung natürlicher Sprache und prädiktiven Text bereitstellt.
Beispiel: Virtuelle Assistenten wie Siri und Google Assistant verwenden KI, um Sprachbefehle zu verstehen und darauf zu reagieren, wodurch die Interaktion der Benutzer mit ihren Geräten erleichtert wird.

### Das klingt alles großartig, also warum brauchen wir das KI-Agenten-Framework?

KI-Agenten-Frameworks repräsentieren mehr als nur normale KI-Frameworks. Sie sind darauf ausgelegt, die Erstellung intelligenter Agenten zu ermöglichen, die mit Benutzern, anderen Agenten und der Umgebung interagieren können, um bestimmte Ziele zu erreichen. Diese Agenten können autonomes Verhalten zeigen, Entscheidungen treffen und sich an veränderte Bedingungen anpassen. Schauen wir uns einige Schlüsselkompetenzen an, die durch KI-Agenten-Frameworks ermöglicht werden:

- **Zusammenarbeit und Koordination von Agenten**: Ermöglichen die Erstellung mehrerer KI-Agenten, die zusammenarbeiten, kommunizieren und koordinieren, um komplexe Aufgaben zu lösen.
- **Aufgabenautomatisierung und -verwaltung**: Bieten Mechanismen zur Automatisierung mehrstufiger Workflows, Aufgabenvergabe und dynamischen Aufgabenverwaltung zwischen Agenten.
- **Kontextuelles Verständnis und Anpassung**: Rüsten Agenten mit der Fähigkeit aus, Kontext zu verstehen, sich an veränderte Umgebungen anzupassen und Entscheidungen auf Basis von Echtzeitinformationen zu treffen.

Zusammenfassend ermöglichen Agenten mehr Handlungsspielraum, heben Automatisierung auf die nächste Stufe und schaffen intelligentere Systeme, die sich an ihre Umgebung anpassen und daraus lernen können.

## Wie kann man schnell Prototypen erstellen, iterieren und die Fähigkeiten des Agenten verbessern?

Dies ist ein schnelllebiges Feld, aber es gibt einige Dinge, die in den meisten KI-Agenten-Frameworks üblich sind und Ihnen helfen können, schnell Prototypen zu erstellen und zu iterieren, nämlich modulare Komponenten, kollaborative Werkzeuge und Echtzeit-Lernen. Schauen wir uns diese an:

- **Verwenden Sie modulare Komponenten**: KI-SDKs bieten vorgefertigte Komponenten wie AI- und Memory-Connectoren, Funktionsaufrufe mittels natürlicher Sprache oder Code-Plugins, Prompt-Vorlagen und mehr.
- **Nutzen Sie kollaborative Werkzeuge**: Entwerfen Sie Agenten mit spezifischen Rollen und Aufgaben, sodass sie kollaborative Workflows testen und verfeinern können.
- **Lernen in Echtzeit**: Implementieren Sie Feedback-Schleifen, in denen Agenten aus Interaktionen lernen und ihr Verhalten dynamisch anpassen.

### Verwenden Sie modulare Komponenten

SDKs wie Microsoft Semantic Kernel und LangChain bieten vorgefertigte Komponenten wie AI-Connectoren, Prompt-Vorlagen und Memory-Management.

**Wie Teams diese nutzen können**: Teams können diese Komponenten schnell zusammenstellen, um einen funktionalen Prototyp zu erstellen, ohne von Grund auf neu beginnen zu müssen, was schnelles Experimentieren und Iteration ermöglicht.

**Wie es in der Praxis funktioniert**: Sie können einen vorgefertigten Parser verwenden, um Informationen aus Benutzereingaben zu extrahieren, ein Memory-Modul, um Daten zu speichern und abzurufen, und einen Prompt-Generator, um mit Benutzern zu interagieren, alles ohne diese Komponenten selbst bauen zu müssen.

**Beispielcode**. Schauen wir uns Beispiele an, wie Sie einen vorgefertigten AI-Connector mit Semantic Kernel Python und .Net verwenden können, der auto-Funktionsaufrufe verwendet, damit das Modell auf Benutzereingaben reagiert:

``` python
# Semantic Kernel Python Beispiel

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definieren Sie ein ChatHistory-Objekt, um den Kontext der Unterhaltung zu speichern
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definieren Sie ein Beispiel-Plugin, das die Funktion zur Reisebuchung enthält
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Erstellen Sie den Kernel
kernel = Kernel()

# Fügen Sie das Beispiel-Plugin dem Kernel-Objekt hinzu
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definieren Sie den Azure OpenAI AI Connector
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definieren Sie die Anfrageeinstellungen, um das Modell mit automatischem Funktionsaufruf zu konfigurieren
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Senden Sie die Anfrage an das Modell für den gegebenen Chatverlauf und die Anfrageeinstellungen
    # Der Kernel enthält das Beispiel, das das Modell zur Ausführung anfordern wird
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # Beispiel-Antwort des KI-Modells: `Ihr Flug nach New York am 1. Januar 2025 wurde erfolgreich gebucht. Gute Reise! ✈️🗽`

    # Fügen Sie die Antwort des Modells unserem Chat-Kontext hinzu
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```

Was Sie aus diesem Beispiel sehen können, ist, wie Sie einen vorgefertigten Parser nutzen können, um Schlüsselinformationen aus Benutzereingaben zu extrahieren, wie zum Beispiel Abflugort, Ziel und Datum einer Flugbuchungsanfrage. Dieser modulare Ansatz ermöglicht es Ihnen, sich auf die Logik auf hoher Ebene zu konzentrieren.

### Nutzen Sie kollaborative Werkzeuge

Frameworks wie CrewAI, Microsoft AutoGen und Semantic Kernel erleichtern die Erstellung mehrerer Agenten, die zusammenarbeiten können.

**Wie Teams diese nutzen können**: Teams können Agenten mit spezifischen Rollen und Aufgaben entwerfen, wodurch sie kollaborative Workflows testen und verfeinern und die Gesamteffizienz des Systems verbessern können.

**Wie es in der Praxis funktioniert**: Sie können ein Team von Agenten erstellen, wobei jeder Agent eine spezialisierte Funktion hat, wie Datenabruf, Analyse oder Entscheidungsfindung. Diese Agenten können kommunizieren und Informationen teilen, um ein gemeinsames Ziel zu erreichen, wie z. B. die Beantwortung einer Benutzeranfrage oder das Abschließen einer Aufgabe.

**Beispielcode (AutoGen)**:

```python
# Erstellen von Agenten, dann einen Round-Robin-Plan erstellen, bei dem sie zusammenarbeiten können, in diesem Fall der Reihe nach

# Datenabruf-Agent
# Datenanalyse-Agent
# Entscheidungsfindungs-Agent

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# Das Gespräch endet, wenn der Benutzer "APPROVE" sagt
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Verwenden Sie asyncio.run(...), wenn Sie in einem Skript ausführen.
await Console(stream)
```

Was Sie im vorherigen Code sehen, ist, wie Sie eine Aufgabe erstellen können, die mehrere Agenten umfasst, die zusammenarbeiten, um Daten zu analysieren. Jeder Agent erfüllt eine spezifische Funktion, und die Aufgabe wird durch Koordination der Agenten ausgeführt, um das gewünschte Ergebnis zu erzielen. Durch die Erstellung dedizierter Agenten mit spezialisierten Rollen können Sie die Aufgabeneffizienz und Leistung verbessern.

### In Echtzeit lernen

Fortgeschrittene Frameworks bieten Fähigkeiten für kontextuelles Verständnis und Anpassung in Echtzeit.

**Wie Teams diese nutzen können**: Teams können Feedback-Schleifen implementieren, in denen Agenten aus Interaktionen lernen und ihr Verhalten dynamisch anpassen, was zu kontinuierlicher Verbesserung und Verfeinerung der Fähigkeiten führt.

**Wie es in der Praxis funktioniert**: Agenten können Benutzerfeedback, Umgebungsdaten und Aufgabenergebnisse analysieren, um ihr Wissensbasis zu aktualisieren, Entscheidungsalgorithmen anzupassen und die Leistung im Laufe der Zeit zu verbessern. Dieser iterative Lernprozess ermöglicht es Agenten, sich an veränderte Bedingungen und Benutzerpräferenzen anzupassen und die Gesamtwirksamkeit des Systems zu steigern.

## Was sind die Unterschiede zwischen den Frameworks AutoGen, Semantic Kernel und Azure AI Agent Service?

Es gibt viele Möglichkeiten, diese Frameworks zu vergleichen, aber sehen wir uns einige wichtige Unterschiede in Bezug auf Design, Fähigkeiten und Zielanwendungsfälle an:

## AutoGen

AutoGen ist ein Open-Source-Framework, das vom AI Frontiers Lab von Microsoft Research entwickelt wurde. Es konzentriert sich auf ereignisgesteuerte, verteilte *agentische* Anwendungen und ermöglicht den Einsatz mehrerer LLMs und SLMs, Tools und fortgeschrittener Multi-Agent-Designmuster.

AutoGen ist um das Kernkonzept der Agenten aufgebaut, bei dem es sich um autonome Entitäten handelt, die ihre Umgebung wahrnehmen, Entscheidungen treffen und Aktionen ausführen können, um bestimmte Ziele zu erreichen. Agenten kommunizieren über asynchrone Nachrichten, sodass sie unabhängig und parallel arbeiten können, was die Skalierbarkeit und Reaktionsfähigkeit des Systems erhöht.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenten basieren auf dem Actor-Modell</a>. Laut Wikipedia ist ein Actor _das grundlegende Bauelement der nebenläufigen Berechnung. Als Reaktion auf eine empfangene Nachricht kann ein Actor: lokale Entscheidungen treffen, weitere Actors erzeugen, weitere Nachrichten senden und bestimmen, wie auf die nächste empfangene Nachricht zu reagieren ist_.

**Anwendungsfälle**: Automatisierung der Codegenerierung, Datenanalyseaufgaben und der Aufbau kundenspezifischer Agenten für Planungs- und Forschungsfunktionen.

Hier sind einige wichtige Kernkonzepte von AutoGen:

- **Agenten**. Ein Agent ist eine Softwareentität, die:
  - **Kommuniziert über Nachrichten**, diese Nachrichten können synchron oder asynchron sein.
  - **Behält seinen eigenen Zustand bei**, der durch eingehende Nachrichten geändert werden kann.
  - **Führt Aktionen aus** als Reaktion auf erhaltene Nachrichten oder Zustandsänderungen. Diese Aktionen können den Zustand des Agenten ändern und externe Effekte erzeugen, wie z. B. Aktualisierung von Nachrichtenprotokollen, Senden neuer Nachrichten, Ausführen von Code oder Aufrufen von APIs.
    
  Hier haben Sie einen kurzen Codeausschnitt, in dem Sie Ihren eigenen Agenten mit Chat-Fähigkeiten erstellen:

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
    
    Im vorherigen Code wurde `MyAgent` erstellt und erbt von `RoutedAgent`. Es verfügt über einen Nachrichten-Handler, der den Inhalt der Nachricht ausgibt und dann eine Antwort mithilfe des Delegaten `AssistantAgent` sendet. Beachten Sie besonders, wie wir `self._delegate` eine Instanz von `AssistantAgent` zuweisen, wobei es sich um einen vorgefertigten Agenten handelt, der Chat-Completions verarbeiten kann.


    Lassen Sie AutoGen als Nächstes diesen Agententyp wissen und starten Sie das Programm:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Verarbeitung von Nachrichten im Hintergrund starten.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Im vorherigen Code werden die Agenten beim Runtime registriert und dann wird eine Nachricht an den Agenten gesendet, was zu folgender Ausgabe führt:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Mehrere Agenten**. AutoGen unterstützt die Erstellung mehrerer Agenten, die zusammenarbeiten können, um komplexe Aufgaben zu lösen. Agenten können kommunizieren, Informationen austauschen und ihre Aktionen koordinieren, um Probleme effizienter zu lösen. Um ein Multi-Agenten-System zu erstellen, können Sie verschiedene Typen von Agenten mit spezialisierten Funktionen und Rollen definieren, wie z. B. Datenabruf, Analyse, Entscheidungsfindung und Benutzerinteraktion. Schauen wir uns an, wie eine solche Erstellung aussieht, damit wir ein Gefühl dafür bekommen:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Beispiel für die Deklaration eines Agenten
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Verwendung des Thementyps als Agententyp.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # übrige Deklarationen aus Gründen der Kürze verkürzt

    # Gruppenchats
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```

    Im vorherigen Code haben wir einen `GroupChatManager`, der beim Runtime registriert ist. Dieser Manager ist für die Koordination der Interaktionen zwischen verschiedenen Agententypen verantwortlich, wie Autoren, Illustratoren, Editoren und Benutzern.

- **Agent-Laufzeit**. Das Framework stellt eine Laufzeitumgebung bereit, die die Kommunikation zwischen Agenten ermöglicht, ihre Identitäten und Lebenszyklen verwaltet und Sicherheits- sowie Datenschutzgrenzen durchsetzt. Das bedeutet, dass Sie Ihre Agenten in einer sicheren und kontrollierten Umgebung ausführen können, wodurch sichergestellt wird, dass sie sicher und effizient interagieren können. Es gibt zwei für Sie interessante Laufzeitumgebungen:
  - **Standalone-Laufzeit**. Dies ist eine gute Wahl für Single-Process-Anwendungen, bei denen alle Agenten in derselben Programmiersprache implementiert sind und im selben Prozess laufen. Hier eine Illustration, wie es funktioniert:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Standalone-Laufzeit</a>   
Application stack

    *Agenten kommunizieren über Nachrichten durch die Laufzeit, und die Laufzeit verwaltet den Lebenszyklus der Agenten*

  - **Verteilte Laufzeit**, ist geeignet für Multi-Process-Anwendungen, bei denen Agenten in verschiedenen Programmiersprachen implementiert sein und auf unterschiedlichen Rechnern laufen können. Hier eine Illustration, wie es funktioniert:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Verteilte Laufzeit</a>

## Semantic Kernel + Agent-Framework

Semantic Kernel ist ein unternehmensreifes AI-Orchestrierungs-SDK. Es besteht aus AI- und Memory-Connectoren sowie einem Agent-Framework.

Zuerst behandeln wir einige Kernkomponenten:

- **AI-Connectoren**: Dies ist eine Schnittstelle zu externen AI-Diensten und Datenquellen zur Verwendung sowohl in Python als auch in C#.

  ```python
  # Semantischer Kernel Python
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  

    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```

    Hier haben Sie ein einfaches Beispiel dafür, wie Sie einen Kernel erstellen und einen Chat-Completion-Dienst hinzufügen können. Semantic Kernel stellt eine Verbindung zu einem externen AI-Dienst her, in diesem Fall Azure OpenAI Chat Completion.

- **Plugins**: Diese kapseln Funktionen ein, die eine Anwendung nutzen kann. Es gibt sowohl fertige Plugins als auch benutzerdefinierte, die Sie erstellen können. Ein verwandtes Konzept sind "Prompt-Funktionen". Anstatt natürliche Sprachhinweise für Funktionsaufrufe bereitzustellen, senden Sie bestimmte Funktionen an das Modell. Basierend auf dem aktuellen Chat-Kontext kann das Modell entscheiden, eine dieser Funktionen aufzurufen, um eine Anfrage oder Abfrage zu vervollständigen. Hier ein Beispiel:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```

    Hier haben Sie zunächst eine Template-Prompt `skPrompt`, die Platz für die Benutzereingabe `$userInput` lässt. Dann erstellen Sie die Kernel-Funktion `SummarizeText` und importieren sie anschließend mit dem Plugin-Namen `SemanticFunctions` in den Kernel. Beachten Sie den Namen der Funktion, der Semantic Kernel dabei hilft zu verstehen, was die Funktion tut und wann sie aufgerufen werden sollte.

- **Native Funktion**: Es gibt auch native Funktionen, die das Framework direkt aufrufen kann, um die Aufgabe auszuführen. Hier ein Beispiel für eine solche Funktion, die den Inhalt einer Datei abruft:

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```

- **Memory**: Abstrahiert und vereinfacht das Kontextmanagement für KI-Apps. Die Idee hinter Memory ist, dass dies etwas ist, das das LLM wissen sollte. Sie können diese Informationen in einem Vektor-Store speichern, der letztlich eine In-Memory-Datenbank oder eine Vektor-Datenbank oder Ähnliches ist. Hier ein Beispiel für ein sehr vereinfachtes Szenario, in dem *Fakten* zum Memory hinzugefügt werden:

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```

    Diese Fakten werden dann in der Memory-Collection `SummarizedAzureDocs` gespeichert. Dies ist ein sehr vereinfachtes Beispiel, aber Sie können sehen, wie Sie Informationen im Memory speichern können, damit das LLM sie verwendet.

Also das sind die Grundlagen des Semantic Kernel Frameworks — wie sieht es mit dem Agent Framework aus?

## Azure AI Agent Service

Azure AI Agent Service ist eine neuere Ergänzung, eingeführt auf der Microsoft Ignite 2024. Es ermöglicht die Entwicklung und Bereitstellung von KI-Agenten mit flexibleren Modellen, wie z. B. dem direkten Aufrufen von Open-Source-LLMs wie Llama 3, Mistral und Cohere.

Azure AI Agent Service bietet stärkere unternehmensgerechte Sicherheitsmechanismen und Daten­speichermethoden, wodurch es sich für Unternehmensanwendungen eignet. 

Es funktioniert sofort einsatzbereit mit Multi-Agent-Orchestrierungs-Frameworks wie AutoGen und Semantic Kernel.

Dieser Dienst befindet sich derzeit in Public Preview und unterstützt Python und C# zum Erstellen von Agenten.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definieren Sie ein Beispiel-Plugin für das Beispiel
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # Agentendefinition erstellen
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Erstellen Sie den AzureAI-Agenten mit dem definierten Client und der Agentendefinition
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Erstellen Sie einen Thread, um das Gespräch zu führen
        # Wenn kein Thread angegeben ist, wird ein neuer Thread
        # erstellt und mit der Erstantwort zurückgegeben
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # Rufen Sie den Agenten für den angegebenen Thread auf
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### Kernkonzepte

Azure AI Agent Service hat die folgenden Kernkonzepte:

- **Agent**. Azure AI Agent Service integriert sich in Microsoft Foundry. Innerhalb von AI Foundry fungiert ein AI Agent als ein "intelligenter" Microservice, der verwendet werden kann, um Fragen zu beantworten (RAG), Aktionen auszuführen oder Workflows vollständig zu automatisieren. Dies erreicht er, indem er die Leistungsfähigkeit generativer KI-Modelle mit Tools kombiniert, die ihm den Zugriff auf und die Interaktion mit realen Datenquellen ermöglichen. Hier ist ein Beispiel für einen Agenten:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    In diesem Beispiel wird ein Agent mit dem Modell `gpt-4o-mini`, dem Namen `my-agent` und den Anweisungen `You are helpful agent` erstellt. Der Agent ist mit Tools und Ressourcen ausgestattet, um Aufgaben der Code-Interpretation durchzuführen.

- **Thread and messages**. Der Thread ist ein weiteres wichtiges Konzept. Er repräsentiert eine Konversation oder Interaktion zwischen einem Agenten und einem Benutzer. Threads können verwendet werden, um den Fortschritt einer Konversation zu verfolgen, Kontextinformationen zu speichern und den Zustand der Interaktion zu verwalten. Hier ist ein Beispiel für einen Thread:

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    Im vorherigen Code wird ein Thread erstellt. Danach wird eine Nachricht an den Thread gesendet. Durch den Aufruf von `create_and_process_run` wird der Agent aufgefordert, im Thread Arbeit zu leisten. Schließlich werden die Nachrichten abgerufen und protokolliert, um die Antwort des Agenten zu sehen. Die Nachrichten geben den Fortschritt der Konversation zwischen dem Benutzer und dem Agenten wieder. Es ist auch wichtig zu verstehen, dass die Nachrichten unterschiedliche Typen haben können, wie z. B. Text, Bild oder Datei, also dass die Arbeit des Agenten z. B. in einem Bild oder einer Textantwort resultiert. Als Entwickler können Sie diese Informationen dann weiterverarbeiten oder dem Benutzer präsentieren.

- **Integrates with other AI frameworks**. Der Azure AI Agent Service kann mit anderen Frameworks wie AutoGen und Semantic Kernel interagieren, was bedeutet, dass Sie einen Teil Ihrer App in einem dieser Frameworks erstellen und beispielsweise den Agent Service als Orchestrator verwenden können, oder Sie bauen alles im Agent Service auf.

**Use Cases**: Azure AI Agent Service ist für Unternehmensanwendungen konzipiert, die eine sichere, skalierbare und flexible Bereitstellung von KI-Agenten erfordern.

## What's the difference between these frameworks?
 
Es scheint zwar viel Überschneidung zwischen diesen Frameworks zu geben, aber es gibt einige wichtige Unterschiede in Bezug auf Design, Funktionalität und Zielanwendungen:
 
- **AutoGen**: Ist ein Experimentier-Framework, das sich auf Spitzenforschung zu Multi-Agent-Systemen konzentriert. Es ist der beste Ort, um ausgefeilte Multi-Agent-Systeme zu experimentieren und zu prototypisieren.
- **Semantic Kernel**: Ist eine produktionsreife Agenten-Bibliothek zum Erstellen unternehmensfähiger agentischer Anwendungen. Es fokussiert sich auf ereignisgesteuerte, verteilte agentische Anwendungen und ermöglicht mehrere LLMs und SLMs, Tools sowie Single-/Multi-Agent-Designmuster.
- **Azure AI Agent Service**: Ist eine Plattform- und Bereitstellungsdienstleistung in Azure Foundry für Agenten. Es bietet Konnektivität zu von Azure Found unterstützten Diensten wie Azure OpenAI, Azure AI Search, Bing Search und Code-Ausführung.
 
Noch unsicher, welche Wahl die richtige ist?

### Use Cases
 
Sehen wir uns an, ob wir Ihnen anhand einiger gängiger Anwendungsfälle helfen können:
 
> Q: I'm experimenting, learning and building proof-of-concept agent applications, and I want to be able to build and experiment quickly
>

>A: AutoGen would be a good choice for this scenario, as it focuses on event-driven, distributed agentic applications and supports advanced multi-agent design patterns.

> Q: What makes AutoGen a better choice than Semantic Kernel and Azure AI Agent Service for this use case?
>
> A: AutoGen is specifically designed for event-driven, distributed agentic applications, making it well-suited for automating code generation and data analysis tasks. It provides the necessary tools and capabilities to build complex multi-agent systems efficiently.

>Q: Sounds like Azure AI Agent Service could work here too, it has tools for code generation and more?

>
> A: Yes, Azure AI Agent Service is a platform service for agents and add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. It makes it easy to build your agents in the Foundry Portal and deploy them at scale.
 
> Q: I'm still confused just give me one option
>
> A: A great choice is to build your application in Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. This approach allows you to easily persist your agents while leveraging the power to build multi-agent systems in Semantic Kernel. Additionally, Semantic Kernel has a connector in AutoGen, making it easy to use both frameworks together.
 
Fassen wir die wichtigsten Unterschiede in einer Tabelle zusammen:

| Framework | Fokus | Kernkonzepte | Anwendungsfälle |
| --- | --- | --- | --- |
| AutoGen | Ereignisgesteuerte, verteilte agentische Anwendungen | Agents, Personas, Functions, Data | Code-Generierung, Datenanalyseaufgaben |
| Semantic Kernel | Verstehen und Erzeugen menschenähnlicher Textinhalte | Agents, Modular Components, Collaboration | Sprachverstehen, Inhaltserstellung |
| Azure AI Agent Service | Flexible Modelle, Unternehmenssicherheit, Code-Generierung, Tool-Aufrufe | Modularity, Collaboration, Process Orchestration | Sichere, skalierbare und flexible Bereitstellung von KI-Agenten |

Was ist der ideale Anwendungsfall für jedes dieser Frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

Die Antwort ist ja, Sie können Ihre vorhandenen Azure-Ecosystem-Tools direkt integrieren, insbesondere mit Azure AI Agent Service, da dieser so gebaut wurde, dass er nahtlos mit anderen Azure-Diensten zusammenarbeitet. Sie könnten zum Beispiel Bing, Azure AI Search und Azure Functions integrieren. Es gibt außerdem eine tiefe Integration mit Microsoft Foundry.

Für AutoGen und Semantic Kernel können Sie ebenfalls mit Azure-Diensten integrieren, aber es kann erforderlich sein, die Azure-Dienste aus Ihrem Code aufzurufen. Eine andere Möglichkeit zur Integration besteht darin, die Azure SDKs zu verwenden, um von Ihren Agenten aus mit Azure-Diensten zu interagieren. Zusätzlich, wie bereits erwähnt, können Sie Azure AI Agent Service als Orchestrator für Ihre in AutoGen oder Semantic Kernel erstellten Agenten verwenden, was den einfachen Zugriff auf das Azure-Ökosystem ermöglicht.

## Sample Codes

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Treten Sie dem [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) bei, um andere Lernende zu treffen, an Sprechstunden teilzunehmen und Antworten auf Ihre Fragen zu AI Agents zu erhalten.

## References

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel und AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Verwendung von Azure AI Agent Service mit AutoGen / Semantic Kernel zum Erstellen einer Multi-Agenten-Lösung</a>

## Previous Lesson

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Haftungsausschluss:
Dieses Dokument wurde mit dem KI-Übersetzungsdienst Co-op Translator (https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, beachten Sie bitte, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in seiner ursprünglichen Sprache ist als maßgebliche Quelle zu betrachten. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die aus der Verwendung dieser Übersetzung entstehen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->