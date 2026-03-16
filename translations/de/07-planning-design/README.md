[![Planungs-Designmuster](../../../translated_images/de/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Klicken Sie auf das obige Bild, um das Video zu dieser Lektion anzusehen)_

# Planungs-Design

## Einführung

Diese Lektion behandelt

* Das Definieren eines klaren Gesamtziels und das Aufteilen einer komplexen Aufgabe in überschaubare Teilaufgaben.
* Die Nutzung von strukturiertem Output für zuverlässigere und maschinenlesbare Antworten.
* Die Anwendung eines ereignisgesteuerten Ansatzes zur Handhabung dynamischer Aufgaben und unerwarteter Eingaben.

## Lernziele

Nach Abschluss dieser Lektion werden Sie ein Verständnis dafür haben:

* Ein Gesamtziel für einen KI-Agenten zu identifizieren und festzulegen, sodass er klar weiß, was erreicht werden soll.
* Eine komplexe Aufgabe in überschaubare Teilaufgaben zu zerlegen und diese in einer logischen Reihenfolge zu organisieren.
* Agenten mit den richtigen Werkzeugen auszustatten (z. B. Suchwerkzeuge oder Datenanalysetools), zu entscheiden, wann und wie diese eingesetzt werden, und unerwartete Situationen zu bewältigen.
* Die Ergebnisse von Teilaufgaben zu bewerten, die Leistung zu messen und Aktionen zu iterieren, um das Endergebnis zu verbessern.

## Das Gesamtziel definieren und eine Aufgabe aufteilen

![Ziele und Aufgaben definieren](../../../translated_images/de/defining-goals-tasks.d70439e19e37c47a.webp)

Die meisten realen Aufgaben sind zu komplex, um sie in einem einzigen Schritt zu bewältigen. Ein KI-Agent benötigt eine prägnante Zielsetzung, die seine Planung und Aktionen lenkt. Zum Beispiel das Ziel:

    „Erstelle einen 3-Tages-Reiseplan.“

So einfach es formuliert ist, benötigt es dennoch eine Verfeinerung. Je klarer das Ziel, desto besser kann der Agent (und jeder menschliche Mitarbeiter) sich darauf konzentrieren, das richtige Ergebnis zu erzielen, wie z. B. einen umfassenden Reiseplan mit Flugoptionen, Hotel-Empfehlungen und Aktivitätsvorschlägen zu erstellen.

### Aufteilung der Aufgabe

Große oder komplexe Aufgaben werden überschaubarer, wenn sie in kleinere, zielgerichtete Teilaufgaben aufgeteilt werden.
Für das Beispiel Reiseplan könnte man das Ziel in folgende Teilaufgaben gliedern:

* Flugbuchung
* Hotelbuchung
* Mietwagen
* Personalisierung

Jede Teilaufgabe kann dann von spezialisierten Agenten oder Prozessen bearbeitet werden. Ein Agent könnte sich auf die Suche nach den besten Flugangeboten spezialisieren, ein anderer auf Hotelbuchungen usw. Ein koordinierender oder „nachgelagerter“ Agent kann diese Ergebnisse dann zu einem zusammenhängenden Reiseplan für den Endnutzer zusammenfügen.

Dieser modulare Ansatz ermöglicht zudem schrittweise Erweiterungen. Beispielsweise könnten spezialisierte Agenten für Restaurantempfehlungen oder lokale Aktivitätsvorschläge hinzugefügt und der Reiseplan im Laufe der Zeit verfeinert werden.

### Strukturierter Output

Large Language Models (LLMs) können strukturierten Output (z. B. JSON) erzeugen, der für nachgelagerte Agenten oder Dienste leichter zu interpretieren und zu verarbeiten ist. Dies ist besonders nützlich in einem Multi-Agenten-Kontext, wo wir Aufgaben nach Erhalt der Planungs-Ergebnisse ausführen können. Siehe dazu diesen <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">Blogbeitrag</a> für eine kurze Übersicht.

Der folgende Python-Code zeigt einen einfachen Planungs-Agenten, der ein Ziel in Teilaufgaben zerlegt und einen strukturierten Plan erzeugt:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Travel SubTask Modell
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # Wir wollen die Aufgabe dem Agenten zuweisen

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Um sich mit dem Modell zu authentifizieren, müssen Sie in Ihren GitHub-Einstellungen ein persönliches Zugriffstoken (PAT) generieren.
    # Erstellen Sie Ihr PAT-Token, indem Sie den Anweisungen hier folgen: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definiere die Benutzernachricht
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Stellen Sie sicher, dass der Antwortinhalt eine gültige JSON-Zeichenfolge ist, bevor Sie ihn laden
# response_content: Optional[str] = response.content, falls isinstance(
#     response.content, str) sonst None
# falls response_content None ist:
#     ValueError auslösen("Antwortinhalt ist keine gültige JSON-Zeichenfolge")

# # Drucke den Antwortinhalt nach dem Laden als JSON
# pprint(json.loads(response_content))

# Überprüfe den Antwortinhalt mit dem MathReasoning-Modell
# TravelPlan.model_validate(json.loads(response_content))
```

### Planungs-Agent mit Multi-Agenten-Orchestrierung

In diesem Beispiel erhält ein Semantic Router Agent eine Benutzeranfrage (z. B. „Ich brauche einen Hotelplan für meine Reise.“).

Der Planer:

* Empfängt den Hotelplan: Der Planer nimmt die Nachricht des Benutzers und generiert basierend auf einem System-Prompt (inklusive verfügbarer Agenten-Details) einen strukturierten Reiseplan.
* Listet Agenten und ihre Werkzeuge auf: Das Agenten-Verzeichnis enthält eine Liste von Agenten (z. B. für Flug, Hotel, Mietwagen und Aktivitäten) samt deren Funktionen oder Werkzeugen.
* Leitet den Plan an die jeweiligen Agenten weiter: Je nach Anzahl der Teilaufgaben schickt der Planer die Nachricht entweder direkt an einen dedizierten Agenten (bei Einzeltask-Szenarien) oder koordiniert über einen Gruppen-Chat-Manager für die Multi-Agenten-Zusammenarbeit.
* Fasst das Ergebnis zusammen: Abschließend fasst der Planer den generierten Plan zur besseren Übersicht zusammen.
Der folgende Python-Code veranschaulicht diese Schritte:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Reise-Unteraufgabenmodell

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # Wir möchten die Aufgabe dem Agenten zuweisen

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Erstellen Sie den Client mit typgeprüften Umgebungsvariablen

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definieren Sie die Benutzernachricht

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Stellen Sie sicher, dass der Antwortinhalt eine gültige JSON-Zeichenfolge ist, bevor Sie ihn laden

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Drucken Sie den Antwortinhalt nach dem Laden als JSON aus

pprint(json.loads(response_content))
```

Das Folgende ist die Ausgabe des vorherigen Codes, und Sie können diesen strukturierten Output verwenden, um ihn an `assigned_agent` weiterzuleiten und den Reiseplan für den Endnutzer zusammenzufassen.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Ein Beispiel-Notebook mit dem vorherigen Codebeispiel ist [hier](07-autogen.ipynb) verfügbar.

### Iterative Planung

Manche Aufgaben erfordern ein Hin und Her oder eine Neuplanung, bei der das Ergebnis einer Teilaufgabe die nächste beeinflusst. Wenn der Agent beispielsweise beim Buchen von Flügen ein unerwartetes Datenformat entdeckt, muss er seine Strategie möglicherweise anpassen, bevor er mit der Hotelbuchung fortfährt.

Außerdem kann Benutzerfeedback (z. B. ein Mensch entscheidet, dass er einen früheren Flug bevorzugt) eine Teilneuplannung auslösen. Dieser dynamische, iterative Ansatz stellt sicher, dass die endgültige Lösung mit den realen Rahmenbedingungen und sich ändernden Nutzerpräferenzen übereinstimmt.

Beispielcode:

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. gleich wie im vorherigen Code und übergebe die Benutzerhistorie, aktuellen Plan
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. neu planen und die Aufgaben an die jeweiligen Agenten senden
```

Für eine umfassendere Planung sehen Sie sich Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogpost</a> zum Lösen komplexer Aufgaben an.

## Zusammenfassung

In diesem Artikel haben wir ein Beispiel betrachtet, wie wir einen Planer erstellen können, der dynamisch die verfügbaren definierten Agenten auswählt. Der Output des Planers zerlegt die Aufgaben und weist die Agenten zu, damit diese ausgeführt werden können. Es wird angenommen, dass die Agenten Zugriff auf die erforderlichen Funktionen/Werkzeuge haben, um die Aufgabe zu erfüllen. Zusätzlich zu den Agenten können Sie weitere Muster wie Reflection, Summarizer und Round-Robin-Chat einbinden, um die Funktionalität weiter anzupassen.

## Zusätzliche Ressourcen

AutoGen Magentic One – Ein generalistisches Multi-Agenten-System zur Lösung komplexer Aufgaben mit beeindruckenden Ergebnissen bei mehreren herausfordernden Agenten-Benchmarks. Referenz: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. In dieser Implementierung erstellt der Orchestrator aufgabenspezifische Pläne und delegiert diese an die verfügbaren Agenten. Zusätzlich zur Planung setzt der Orchestrator auch einen Tracking-Mechanismus ein, um den Fortschritt der Aufgabe zu überwachen und bei Bedarf Neuplanungen vorzunehmen.

### Haben Sie weitere Fragen zum Planungs-Designmuster?

Treten Sie dem [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) bei, um andere Lernende zu treffen, an Sprechstunden teilzunehmen und Ihre Fragen zu AI Agents beantwortet zu bekommen.

## Vorherige Lektion

[Vertrauenswürdige KI-Agenten bauen](../06-building-trustworthy-agents/README.md)

## Nächste Lektion

[Multi-Agenten-Designmuster](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Haftungsausschluss**:  
Dieses Dokument wurde mit dem KI-Übersetzungsdienst [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, weisen wir darauf hin, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in seiner Ursprungssprache ist als maßgebliche Quelle zu betrachten. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die durch die Nutzung dieser Übersetzung entstehen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->