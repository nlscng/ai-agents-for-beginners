[![Vertrauenswürdige KI-Agenten](../../../translated_images/de/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klicken Sie auf das Bild oben, um das Video zu dieser Lektion anzusehen)_

# Vertrauenswürdige KI-Agenten bauen

## Einführung

Diese Lektion behandelt:

- Wie man sichere und effektive KI-Agenten erstellt und einsetzt
- Wichtige Sicherheitsüberlegungen bei der Entwicklung von KI-Agenten
- Wie man Datenschutz und Benutzerprivatsphäre bei der Entwicklung von KI-Agenten wahrt

## Lernziele

Nach Abschluss dieser Lektion wissen Sie, wie Sie:

- Risiken bei der Erstellung von KI-Agenten erkennen und mindern
- Sicherheitsmaßnahmen implementieren, um sicherzustellen, dass Daten und Zugriffe richtig verwaltet werden
- KI-Agenten erstellen, die Datenschutz gewährleisten und eine hochwertige Benutzererfahrung bieten

## Sicherheit

Schauen wir uns zunächst den Aufbau sicherer agentischer Anwendungen an. Sicherheit bedeutet, dass der KI-Agent so funktioniert, wie er entworfen wurde. Als Entwickler agentischer Anwendungen verfügen wir über Methoden und Werkzeuge, um die Sicherheit zu maximieren:

### Aufbau eines Systemnachrichten-Frameworks

Wenn Sie schon einmal eine KI-Anwendung mit Large Language Models (LLMs) gebaut haben, kennen Sie die Wichtigkeit, einen robusten Systemprompt oder eine Systemnachricht zu gestalten. Diese Prompts legen die Meta-Regeln, Anweisungen und Leitlinien fest, wie das LLM mit dem Nutzer und den Daten interagiert.

Für KI-Agenten ist der Systemprompt noch wichtiger, da die KI-Agenten hochspezifische Anweisungen benötigen, um die Aufgaben zu erfüllen, die wir für sie entworfen haben.

Um skalierbare Systemprompts zu erzeugen, können wir ein Systemnachrichten-Framework verwenden, um einen oder mehrere Agenten in unserer Anwendung zu erstellen:

![Aufbau eines Systemnachrichten-Frameworks](../../../translated_images/de/system-message-framework.3a97368c92d11d68.webp)

#### Schritt 1: Erstellen einer Meta-Systemnachricht

Der Meta-Prompt wird von einem LLM verwendet, um die Systemprompts für die Agenten zu generieren, die wir erstellen. Wir gestalten ihn als Vorlage, damit wir bei Bedarf effizient mehrere Agenten erstellen können.

Hier ist ein Beispiel für eine Meta-Systemnachricht, die wir dem LLM geben würden:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Schritt 2: Erstellen eines Basis-Prompts

Der nächste Schritt ist das Erstellen eines Basis-Prompts, das den KI-Agenten beschreibt. Sie sollten die Rolle des Agenten, die Aufgaben, die er erledigen wird, und alle weiteren Verantwortlichkeiten des Agenten einschließen.

Hier ist ein Beispiel:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Schritt 3: Bereitstellen der Basis-Systemnachricht an das LLM

Nun können wir diese Systemnachricht optimieren, indem wir die Meta-Systemnachricht als Systemnachricht und unsere Basis-Systemnachricht bereitstellen.

Das erzeugt eine Systemnachricht, die besser gestaltet ist, um unsere KI-Agenten zu leiten:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Schritt 4: Iterieren und Verbessern

Der Wert dieses Systemnachrichten-Frameworks besteht darin, die Erstellung von Systemnachrichten mehrerer Agenten leichter skalieren und Ihre Systemnachrichten im Laufe der Zeit verbessern zu können. Es ist selten, dass eine Systemnachricht beim ersten Mal für Ihren kompletten Anwendungsfall funktioniert. Kleine Anpassungen und Verbesserungen durch Änderung der Basis-Systemnachricht und deren Durchlauf durch das System ermöglichen es Ihnen, Ergebnisse zu vergleichen und zu bewerten.

## Bedrohungen verstehen

Um vertrauenswürdige KI-Agenten zu bauen, ist es wichtig, die Risiken und Bedrohungen für Ihren KI-Agenten zu verstehen und zu mindern. Schauen wir uns einige der verschiedenen Bedrohungen für KI-Agenten an und wie Sie sich besser darauf vorbereiten können.

![Bedrohungen verstehen](../../../translated_images/de/understanding-threats.89edeada8a97fc0f.webp)

### Aufgaben und Anweisungen

**Beschreibung:** Angreifer versuchen, die Anweisungen oder Ziele des KI-Agenten durch Prompt-Manipulation oder Eingabemanipulation zu ändern.

**Minderung:** Führen Sie Validierungsprüfungen und Eingabefilter durch, um potenziell gefährliche Prompts zu erkennen, bevor sie vom KI-Agenten verarbeitet werden. Da diese Angriffe typischerweise häufige Interaktionen mit dem Agenten erfordern, ist das Begrenzen der Gesprächsrunden eine weitere Möglichkeit, solche Angriffe zu verhindern.

### Zugang zu kritischen Systemen

**Beschreibung:** Wenn ein KI-Agent Zugriff auf Systeme und Dienste hat, die sensible Daten speichern, können Angreifer die Kommunikation zwischen dem Agenten und diesen Diensten kompromittieren. Dies können direkte Angriffe oder indirekte Versuche sein, Informationen über diese Systeme durch den Agenten zu erhalten.

**Minderung:** KI-Agenten sollten nur bedarfsweise Zugriff auf Systeme haben, um diese Angriffsarten zu verhindern. Die Kommunikation zwischen Agent und System sollte zudem gesichert sein. Implementierung von Authentifizierung und Zugriffskontrolle ist eine weitere Möglichkeit, diese Informationen zu schützen.

### Überlastung von Ressourcen und Diensten

**Beschreibung:** KI-Agenten können verschiedene Werkzeuge und Dienste nutzen, um Aufgaben zu erledigen. Angreifer können diese Fähigkeit ausnutzen, um diese Dienste durch eine hohe Anzahl von Anfragen über den KI-Agenten anzugreifen, was zu Systemausfällen oder hohen Kosten führen kann.

**Minderung:** Implementieren Sie Richtlinien, die die Anzahl der Anfragen begrenzen, die ein KI-Agent an einen Dienst senden kann. Die Begrenzung der Gesprächsrunden und der Anfragen an Ihren KI-Agenten ist eine weitere Möglichkeit, solche Angriffe zu verhindern.

### Vergiftung der Wissensbasis

**Beschreibung:** Diese Art von Angriff richtet sich nicht direkt gegen den KI-Agenten, sondern gegen die Wissensbasis und andere Dienste, die der KI-Agent nutzt. Dies könnte die Korruption der Daten oder Informationen sein, die der KI-Agent verwendet, um eine Aufgabe zu erfüllen, was zu voreingenommenen oder unbeabsichtigten Antworten an den Nutzer führt.

**Minderung:** Führen Sie regelmäßige Überprüfungen der Daten durch, die der KI-Agent in seinen Workflows verwendet. Stellen Sie sicher, dass der Zugang zu diesen Daten sicher ist und nur von vertrauenswürdigen Personen geändert wird, um diese Art von Angriff zu vermeiden.

### Kaskadierende Fehler

**Beschreibung:** KI-Agenten greifen auf verschiedene Werkzeuge und Dienste zu, um Aufgaben zu erledigen. Fehler, die durch Angreifer verursacht werden, können zu Ausfällen anderer Systeme führen, die mit dem KI-Agenten verbunden sind, wodurch der Angriff sich weiter ausbreitet und schwerer zu beheben ist.

**Minderung:** Eine Methode, dies zu vermeiden, ist, den KI-Agenten in einer begrenzten Umgebung arbeiten zu lassen, wie z. B. in einem Docker-Container, um direkte Systemangriffe zu verhindern. Das Erstellen von Fallback-Mechanismen und Wiederholungslogik, wenn bestimmte Systeme mit einem Fehler antworten, ist eine weitere Möglichkeit, größere Systemausfälle zu verhindern.

## Mensch im Kreislauf

Ein weiterer effektiver Weg, vertrauenswürdige KI-Agentensysteme zu bauen, ist die Verwendung eines Mensch-im-Kreislauf. Dies schafft einen Ablauf, bei dem Nutzer während der Ausführung Feedback an die Agenten geben können. Nutzer agieren im Wesentlichen als Agenten in einem Multi-Agenten-System und geben Genehmigungen oder beenden den laufenden Prozess.

![Mensch im Kreislauf](../../../translated_images/de/human-in-the-loop.5f0068a678f62f4f.webp)

Hier ist ein Code-Snippet, das mit AutoGen zeigt, wie dieses Konzept implementiert wird:

```python

# Erstellen Sie die Agenten.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Verwenden Sie input(), um Benutzereingaben von der Konsole zu erhalten.

# Erstellen Sie die Abbruchbedingung, die das Gespräch beendet, wenn der Benutzer "APPROVE" sagt.
termination = TextMentionTermination("APPROVE")

# Erstellen Sie das Team.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Führen Sie das Gespräch aus und streamen Sie es in die Konsole.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Verwenden Sie asyncio.run(...), wenn Sie es in einem Skript ausführen.
await Console(stream)

```

## Fazit

Der Aufbau vertrauenswürdiger KI-Agenten erfordert sorgfältiges Design, robuste Sicherheitsmaßnahmen und kontinuierliche Iteration. Durch die Implementierung strukturierter Meta-Prompting-Systeme, das Verständnis potenzieller Bedrohungen und das Anwenden von Minderungsstrategien können Entwickler KI-Agenten schaffen, die sowohl sicher als auch effektiv sind. Zusätzlich stellt die Einbindung eines Mensch-im-Kreislauf-Ansatzes sicher, dass KI-Agenten auf die Bedürfnisse der Nutzer abgestimmt bleiben und Risiken minimiert werden. Da KI sich weiterentwickelt, wird eine proaktive Haltung zu Sicherheit, Privatsphäre und ethischen Überlegungen entscheidend sein, um Vertrauen und Zuverlässigkeit in KI-gesteuerte Systeme zu fördern.

### Haben Sie weitere Fragen zum Aufbau vertrauenswürdiger KI-Agenten?

Treten Sie dem [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) bei, um sich mit anderen Lernenden zu treffen, an Office Hours teilzunehmen und Ihre Fragen zu KI-Agenten beantwortet zu bekommen.

## Zusätzliche Ressourcen

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Überblick über verantwortungsvolle KI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Bewertung von generativen KI-Modellen und KI-Anwendungen</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Sicherheits-Systemnachrichten</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Vorlage für Risikoabschätzung</a>

## Vorherige Lektion

[Agentic RAG](../05-agentic-rag/README.md)

## Nächste Lektion

[Planungs-Designmuster](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Haftungsausschluss**:  
Dieses Dokument wurde mithilfe des KI-Übersetzungsdienstes [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir auf Genauigkeit achten, können automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten. Das Originaldokument in seiner Ursprungssprache gilt als maßgebliche Quelle. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die durch die Nutzung dieser Übersetzung entstehen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->