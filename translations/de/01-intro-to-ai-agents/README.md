[![Einführung in KI-Agenten](../../../translated_images/de/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Klicken Sie auf das obige Bild, um das Video zu dieser Lektion anzusehen)_


# Einführung in KI-Agenten und Anwendungsfälle für Agenten

Willkommen zum Kurs "AI Agents for Beginners"! Dieser Kurs vermittelt grundlegendes Wissen und praxisnahe Beispiele zum Aufbau von KI-Agenten.

Treten Sie der <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord-Community</a> bei, um andere Lernende und Entwickler von KI-Agenten kennenzulernen und alle Fragen zu diesem Kurs zu stellen.

Um diesen Kurs zu beginnen, beginnen wir damit, ein besseres Verständnis dafür zu bekommen, was KI-Agenten sind und wie wir sie in den Anwendungen und Workflows einsetzen können, die wir erstellen.

## Introduction

Diese Lektion behandelt:

- Was sind KI-Agenten und welche verschiedenen Agententypen gibt es?
- Für welche Anwendungsfälle sind KI-Agenten am besten geeignet und wie können sie uns helfen?
- Was sind einige der grundlegenden Bausteine beim Entwurf agentischer Lösungen?

## Learning Goals
Nach Abschluss dieser Lektion sollten Sie in der Lage sein:

- Konzepte von KI-Agenten zu verstehen und wie sie sich von anderen KI-Lösungen unterscheiden.
- KI-Agenten effizient anzuwenden.
- Agentische Lösungen produktiv für sowohl Benutzer als auch Kunden zu entwerfen.

## Defining AI Agents and Types of AI Agents

### What are AI Agents?

KI-Agenten sind **Systeme**, die **Große Sprachmodelle(LLMs)** dazu befähigen, **Handlungen auszuführen**, indem sie ihre Fähigkeiten erweitern und den LLMs **Zugriff auf Werkzeuge** und **Wissen** gewähren.

Lassen Sie uns diese Definition in kleinere Teile zerlegen:

- **System** - Es ist wichtig, Agenten nicht nur als einzelne Komponente zu betrachten, sondern als ein System aus vielen Komponenten. Auf grundlegender Ebene sind die Komponenten eines KI-Agenten:
  - **Environment** - Der definierte Raum, in dem der KI-Agent arbeitet. Zum Beispiel könnte bei einem Reisebuchungs-KI-Agenten die Umgebung das Reisebuchungssystem sein, das der KI-Agent zur Erledigung von Aufgaben verwendet.
  - **Sensors** - Umgebungen enthalten Informationen und liefern Rückmeldungen. KI-Agenten verwenden Sensoren, um diese Informationen über den aktuellen Zustand der Umgebung zu sammeln und zu interpretieren. Im Beispiel des Reisebuchungs-Agenten kann das Buchungssystem Informationen wie Hotelverfügbarkeit oder Flugpreise bereitstellen.
  - **Actuators** - Sobald der KI-Agent den aktuellen Zustand der Umgebung erhalten hat, bestimmt der Agent für die aktuelle Aufgabe, welche Aktion ausgeführt werden soll, um die Umgebung zu verändern. Für den Reisebuchungs-Agenten könnte dies beispielsweise das Buchen eines verfügbaren Zimmers für den Benutzer sein.

![Was sind KI-Agenten?](../../../translated_images/de/what-are-ai-agents.1ec8c4d548af601a.webp)

**Große Sprachmodelle** - Das Konzept von Agenten existierte bereits vor der Entstehung von LLMs. Der Vorteil des Aufbaus von KI-Agenten mit LLMs liegt in deren Fähigkeit, menschliche Sprache und Daten zu interpretieren. Diese Fähigkeit ermöglicht es LLMs, Informationen aus der Umgebung zu interpretieren und einen Plan zu definieren, um die Umgebung zu verändern.

**Handlungen ausführen** - Außerhalb von KI-Agentensystemen sind LLMs auf Situationen beschränkt, in denen die Aktion darin besteht, Inhalte oder Informationen basierend auf einer Eingabe des Benutzers zu generieren. Innerhalb von KI-Agentensystemen können LLMs Aufgaben erfüllen, indem sie die Anfrage des Benutzers interpretieren und die ihnen in ihrer Umgebung zur Verfügung stehenden Werkzeuge nutzen.

**Zugriff auf Werkzeuge** - Welche Werkzeuge dem LLM zur Verfügung stehen, wird definiert durch 1) die Umgebung, in der es operiert, und 2) den Entwickler des KI-Agenten. In unserem Reiseagenten-Beispiel sind die Werkzeuge des Agenten durch die im Buchungssystem verfügbaren Operationen begrenzt, und/oder der Entwickler kann den Werkzeugzugriff des Agenten auf Flüge beschränken.

**Memory+Knowledge** - Speicher kann kurzfristig im Kontext der Konversation zwischen dem Benutzer und dem Agenten sein. Langfristig, außerhalb der Informationen, die die Umgebung bereitstellt, können KI-Agenten auch Wissen aus anderen Systemen, Diensten, Werkzeugen und sogar anderen Agenten abrufen. Im Reiseagenten-Beispiel könnten diese Kenntnisse Informationen über die Reisevorlieben des Nutzers sein, die in einer Kundendatenbank gespeichert sind.

### The different types of agents

Now that we have a general definition of AI Agents, let us look at some specific agent types and how they would be applied to a travel booking AI agent.

| **Agent Type**                | **Description**                                                                                                                       | **Example**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Simple Reflex Agents**      | Perform immediate actions based on predefined rules.                                                                                  | Travel agent interprets the context of the email and forwards travel complaints to customer service.                                                                                                                          |
| **Model-Based Reflex Agents** | Perform actions based on a model of the world and changes to that model.                                                              | Travel agent prioritizes routes with significant price changes based on access to historical pricing data.                                                                                                             |
| **Goal-Based Agents**         | Create plans to achieve specific goals by interpreting the goal and determining actions to reach it.                                  | Travel agent books a journey by determining necessary travel arrangements (car, public transit, flights) from the current location to the destination.                                                                                |
| **Utility-Based Agents**      | Consider preferences and weigh tradeoffs numerically to determine how to achieve goals.                                               | Travel agent maximizes utility by weighing convenience vs. cost when booking travel.                                                                                                                                          |
| **Learning Agents**           | Improve over time by responding to feedback and adjusting actions accordingly.                                                        | Travel agent improves by using customer feedback from post-trip surveys to make adjustments to future bookings.                                                                                                               |
| **Hierarchical Agents**       | Feature multiple agents in a tiered system, with higher-level agents breaking tasks into subtasks for lower-level agents to complete. | Travel agent cancels a trip by dividing the task into subtasks (for example, canceling specific bookings) and having lower-level agents complete them, reporting back to the higher-level agent.                                     |
| **Multi-Agent Systems (MAS)** | Agents complete tasks independently, either cooperatively or competitively.                                                           | Cooperative: Multiple agents book specific travel services such as hotels, flights, and entertainment. Competitive: Multiple agents manage and compete over a shared hotel booking calendar to book customers into the hotel. |

## When to Use AI Agents

In the earlier section, we used the Travel Agent use-case to explain how the different types of agents can be used in different scenarios of travel booking. We will continue to use this application throughout the course.

Let's look at the types of use cases that AI Agents are best used for:

![When to use AI Agents?](../../../translated_images/de/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Open-Ended Problems** - allowing the LLM to determine needed steps to complete a task because it can't always be hardcoded into a workflow.
- **Multi-Step Processes** - tasks that require a level of complexity in which the AI Agent needs to use tools or information over multiple turns instead of single shot retrieval.  
- **Improvement Over Time** - tasks where the agent can improve over time by receiving feedback from either its environment or users in order to provide better utility.

We cover more considerations of using AI Agents in the Building Trustworthy AI Agents lesson.

## Basics of Agentic Solutions

### Agent Development

The first step in designing an AI Agent system is to define the tools, actions, and behaviors. In this course, we focus on using the **Azure AI Agent Service** to define our Agents. It offers features like:

- Selection of Open Models such as OpenAI, Mistral, and Llama
- Use of Licensed Data through providers such as Tripadvisor
- Use of standardized OpenAPI 3.0 tools

### Agentic Patterns

Communication with LLMs is through prompts. Given the semi-autonomous nature of AI Agents, it isn't always possible or required to manually reprompt the LLM after a change in the environment. We use **Agentic Patterns** that allow us to prompt the LLM over multiple steps in a more scalable way.

This course is divided into some of the current popular Agentic patterns.

### Agentic Frameworks

Agentic Frameworks allow developers to implement agentic patterns through code. These frameworks offer templates, plugins, and tools for better AI Agent collaboration. These benefits provide abilities for better observability and troubleshooting of AI Agent systems.

In this course, we will explore the research-driven AutoGen framework and the production-ready Agent framework from Semantic Kernel.

## Sample Codes

- Python: [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## Got More Questions about AI Agents?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet with other learners, attend office hours and get your AI Agents questions answered.

## Previous Lesson

[Kurs-Setup](../00-course-setup/README.md)

## Next Lesson

[Erkundung agentischer Frameworks](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Haftungsausschluss:
Dieses Dokument wurde mit dem KI-Übersetzungsdienst Co-op Translator (https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, beachten Sie bitte, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in seiner Ausgangssprache ist als maßgebliche Quelle zu betrachten. Für kritische Informationen empfehlen wir eine professionelle, menschliche Übersetzung. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die aus der Verwendung dieser Übersetzung entstehen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->