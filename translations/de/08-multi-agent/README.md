[![Multi-Agent Design](../../../translated_images/de/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Klicken Sie auf das Bild oben, um das Video zu dieser Lektion anzusehen)_

# Multi-Agenten-Designmuster

Sobald Sie an einem Projekt arbeiten, das mehrere Agenten umfasst, müssen Sie das Multi-Agenten-Designmuster berücksichtigen. Es ist jedoch möglicherweise nicht sofort klar, wann man auf Multi-Agenten umsteigen sollte und welche Vorteile dies hat.

## Einführung

In dieser Lektion möchten wir folgende Fragen beantworten:

- Für welche Szenarien sind Multi-Agenten geeignet?
- Welche Vorteile hat die Verwendung von Multi-Agenten gegenüber einem einzelnen Agenten, der mehrere Aufgaben übernimmt?
- Welche Bausteine gibt es für die Implementierung des Multi-Agenten-Designmusters?
- Wie erhalten wir Einblick darin, wie die mehreren Agenten miteinander interagieren?

## Lernziele

Nach dieser Lektion sollten Sie in der Lage sein:

- Szenarien zu identifizieren, in denen Multi-Agenten anwendbar sind
- Die Vorteile der Verwendung von Multi-Agenten gegenüber einem einzelnen Agenten zu erkennen.
- Die Bausteine für die Implementierung des Multi-Agenten-Designmusters zu verstehen.

Wie sieht das große Ganze aus?

*Multi-Agenten sind ein Designmuster, das es mehreren Agenten erlaubt, zusammenzuarbeiten, um ein gemeinsames Ziel zu erreichen*.

Dieses Muster wird in verschiedenen Bereichen eingesetzt, unter anderem in der Robotik, autonomen Systemen und verteiltem Rechnen.

## Szenarien, in denen Multi-Agenten anwendbar sind

Welche Szenarien sind also gut geeignet für den Einsatz von Multi-Agenten? Die Antwort ist, dass es viele Szenarien gibt, in denen der Einsatz mehrerer Agenten vorteilhaft ist, insbesondere in folgenden Fällen:

- **Große Arbeitslasten**: Große Arbeitslasten können in kleinere Aufgaben aufgeteilt und verschiedenen Agenten zugewiesen werden, wodurch parallele Verarbeitung und schnellere Fertigstellung möglich sind. Ein Beispiel hierfür ist eine große Datenverarbeitungsaufgabe.
- **Komplexe Aufgaben**: Komplexe Aufgaben können, wie große Arbeitslasten, in kleinere Teilaufgaben aufgeteilt werden, die jeweils verschiedenen Agenten zugewiesen werden, die sich auf einen bestimmten Aspekt der Aufgabe spezialisieren. Ein gutes Beispiel hierfür sind autonome Fahrzeuge, bei denen verschiedene Agenten Navigation, Hinderniserkennung und Kommunikation mit anderen Fahrzeugen übernehmen.
- **Verschiedene Fachkenntnisse**: Unterschiedliche Agenten können verschiedene Fachkenntnisse besitzen, sodass sie unterschiedliche Aspekte einer Aufgabe effektiver als ein einziger Agent bearbeiten können. Ein gutes Beispiel hierfür ist im Gesundheitswesen, wo Agenten Diagnosen, Behandlungspläne und Patientenüberwachung verwalten können.

## Vorteile der Verwendung von Multi-Agenten gegenüber einem einzelnen Agenten

Ein Ein-Agenten-System könnte bei einfachen Aufgaben gut funktionieren, aber bei komplexeren Aufgaben bietet die Verwendung mehrerer Agenten mehrere Vorteile:

- **Spezialisierung**: Jeder Agent kann auf eine bestimmte Aufgabe spezialisiert sein. Ein einzelner Agent ohne Spezialisierung kann alles tun, ist aber bei komplexen Aufgaben unter Umständen überfordert oder führt Aufgaben aus, für die er nicht optimal geeignet ist.
- **Skalierbarkeit**: Es ist einfacher, Systeme durch Hinzufügen weiterer Agenten zu skalieren, als einen einzelnen Agenten zu überlasten.
- **Fehlertoleranz**: Wenn ein Agent ausfällt, können andere weiterhin funktionieren, was die Zuverlässigkeit des Systems sicherstellt.

Nehmen wir ein Beispiel, wir buchen eine Reise für einen Nutzer. Ein Ein-Agenten-System müsste alle Aspekte des Buchungsprozesses abwickeln, von der Flugsuche bis zur Buchung von Hotels und Mietwagen. Um dies mit einem einzigen Agenten zu erreichen, müsste der Agent Werkzeuge für alle diese Aufgaben haben. Dies könnte zu einem komplexen und monolithischen System führen, das schwer zu warten und zu skalieren ist. Ein Multi-Agenten-System könnte dagegen unterschiedliche Agenten haben, die sich auf das Finden von Flügen, die Buchung von Hotels und Mietwagen spezialisieren. Das macht das System modularer, leichter wartbar und skalierbar.

Vergleichen Sie das mit einem Reisebüro, das als Familienbetrieb geführt wird, gegenüber einem Franchise-Reisebüro. Das Familienreisebüro hätte einen einzelnen Agenten, der alle Aspekte der Buchung übernimmt, während das Franchise verschiedene Agenten für unterschiedliche Aspekte des Buchungsprozesses einsetzt.

## Bausteine für die Implementierung des Multi-Agenten-Designmusters

Bevor Sie das Multi-Agenten-Designmuster implementieren können, müssen Sie die Bausteine verstehen, aus denen das Muster besteht.

Machen wir das anhand des Beispiels der Reisebuchung für einen Nutzer konkreter. Die Bausteine würden hier einschließen:

- **Agentenkommunikation**: Agenten für Flugsuche, Hotel- und Mietwagenbuchung müssen kommunizieren und Informationen über die Vorlieben und Einschränkungen des Nutzers austauschen. Sie müssen sich auf Protokolle und Methoden für diese Kommunikation einigen. Konkret bedeutet das, dass der Agent für Flugsuche mit dem Agenten für Hotelbuchung kommunizieren muss, damit das Hotel für die gleichen Daten wie der Flug gebucht wird. Die Agenten müssen also Informationen zum Reisedatum des Nutzers austauschen, was bedeutet, dass Sie festlegen müssen, *welche Agenten Informationen teilen und wie sie diese teilen*.
- **Koordinationsmechanismen**: Die Agenten müssen ihre Aktionen koordinieren, um sicherzustellen, dass die Präferenzen und Einschränkungen des Nutzers erfüllt werden. Eine Präferenz könnte sein, dass der Nutzer ein Hotel in Flughafennähe möchte, während eine Einschränkung sein könnte, dass Mietwagen nur am Flughafen verfügbar sind. Das bedeutet, dass der Agent für Hotelbuchung mit dem Agenten für Mietwagenbuchung koordinieren muss, um sicherzustellen, dass die Nutzerwünsche und -einschränkungen berücksichtigt werden. Sie müssen also entscheiden, *wie die Agenten ihre Aktionen koordinieren*.
- **Agentenarchitektur**: Agenten benötigen eine interne Struktur, um Entscheidungen zu treffen und aus ihren Interaktionen mit dem Nutzer zu lernen. Das bedeutet, dass der Agent für Flugsuche eine interne Struktur benötigt, um Entscheidungen darüber zu treffen, welche Flüge dem Nutzer empfohlen werden. Sie müssen also bestimmen, *wie die Agenten Entscheidungen treffen und aus der Interaktion mit dem Nutzer lernen*. Beispiele, wie ein Agent lernt und sich verbessert, könnten sein, dass der Agent für Flugsuche ein Machine-Learning-Modell nutzt, um Flüge basierend auf den bisherigen Präferenzen des Nutzers zu empfehlen.
- **Sichtbarkeit in Multi-Agenten-Interaktionen**: Sie müssen Einblick darin haben, wie die mehreren Agenten miteinander interagieren. Dazu benötigen Sie Werkzeuge und Techniken zur Verfolgung von Agentenaktivitäten und -interaktionen. Dies könnte in Form von Protokollierungs- und Überwachungstools, Visualisierungstools und Leistungskennzahlen erfolgen.
- **Multi-Agenten-Muster**: Es gibt verschiedene Muster zur Implementierung von Multi-Agenten-Systemen, wie zentralisierte, dezentralisierte und hybride Architekturen. Sie müssen das Muster wählen, das am besten zu Ihrem Anwendungsfall passt.
- **Mensch in der Schleife**: In den meisten Fällen ist ein Mensch in der Schleife, und Sie müssen die Agenten anweisen, wann sie menschliches Eingreifen anfordern sollen. Dies könnte beispielsweise dann der Fall sein, wenn ein Nutzer ein bestimmtes Hotel oder einen Flug anfordert, der von den Agenten nicht empfohlen wurde, oder wenn vor der Buchung eines Fluges oder Hotels eine Bestätigung eingeholt werden soll.

## Sichtbarkeit in Multi-Agenten-Interaktionen

Es ist wichtig, dass Sie Einblick darin haben, wie die verschiedenen Agenten miteinander interagieren. Diese Sichtbarkeit ist wesentlich für das Debugging, die Optimierung und die Sicherstellung der Effektivität des Gesamtsystems. Um dies zu erreichen, benötigen Sie Werkzeuge und Techniken, um Agentenaktivitäten und -interaktionen zu verfolgen. Dies kann in Form von Protokollierungs- und Überwachungswerkzeugen, Visualisierungstools und Leistungskennzahlen erfolgen.

Zum Beispiel könnten Sie im Fall der Reisebuchung für einen Nutzer ein Dashboard haben, das den Status jedes Agenten, die Präferenzen und Einschränkungen des Nutzers sowie die Interaktionen zwischen den Agenten anzeigt. Dieses Dashboard könnte die Reisedaten des Nutzers, die vom Flug-Agenten empfohlenen Flüge, die vom Hotel-Agenten empfohlenen Hotels und die vom Mietwagen-Agenten empfohlenen Fahrzeuge zeigen. So erhalten Sie eine klare Sicht darauf, wie die Agenten miteinander interagieren und ob die Wünsche und Einschränkungen des Nutzers erfüllt werden.

Schauen wir uns diese Aspekte etwas detaillierter an.

- **Protokollierungs- und Überwachungstools**: Sie sollten für jede Aktion, die ein Agent ausführt, Protokolle erstellen. Ein Protokolleintrag könnte Informationen über den ausführenden Agenten, die Aktion, die Uhrzeit der Aktion und das Ergebnis der Aktion speichern. Diese Informationen können für Debugging, Optimierung und weitere Zwecke genutzt werden.
- **Visualisierungstools**: Visualisierungstools können Ihnen helfen, die Interaktionen zwischen Agenten auf anschaulichere Weise zu sehen. Beispielsweise könnten Sie einen Graphen haben, der den Informationsfluss zwischen Agenten zeigt. Dies könnte helfen, Engpässe, Ineffizienzen und andere Probleme im System zu identifizieren.
- **Leistungskennzahlen**: Leistungskennzahlen helfen Ihnen dabei, die Effektivität des Multi-Agenten-Systems zu verfolgen. Beispielsweise könnten Sie die Zeit zur Erledigung einer Aufgabe, die Anzahl der Aufgaben pro Zeiteinheit und die Genauigkeit der Empfehlungen der Agenten messen. Diese Daten helfen Ihnen, Verbesserungsbereiche zu identifizieren und das System zu optimieren.

## Multi-Agenten-Muster

Tauchen wir nun in einige konkrete Muster ein, die wir verwenden können, um Multi-Agenten-Anwendungen zu erstellen. Hier sind einige interessante Muster, die es wert sind, betrachtet zu werden:

### Gruppenchat

Dieses Muster ist nützlich, wenn Sie eine Gruppenchat-Anwendung erstellen wollen, in der mehrere Agenten miteinander kommunizieren können. Typische Anwendungsfälle sind Teamzusammenarbeit, Kundenservice und soziale Netzwerke.

In diesem Muster repräsentiert jeder Agent einen Nutzer im Gruppenchat, und Nachrichten werden über ein Nachrichtenprotokoll zwischen den Agenten ausgetauscht. Die Agenten können Nachrichten an den Gruppenchat senden, Nachrichten vom Gruppenchat empfangen und auf Nachrichten anderer Agenten antworten.

Dieses Muster kann mit einer zentralisierten Architektur implementiert werden, bei der alle Nachrichten über einen zentralen Server geleitet werden, oder dezentral, bei dem Nachrichten direkt ausgetauscht werden.

![Group chat](../../../translated_images/de/multi-agent-group-chat.ec10f4cde556babd.webp)

### Weitergabe

Dieses Muster ist nützlich, wenn Sie eine Anwendung erstellen wollen, in der mehrere Agenten Aufgaben aneinander weitergeben können.

Typische Anwendungsfälle sind Kundenservice, Aufgabenverwaltung und Workflow-Automatisierung.

In diesem Muster repräsentiert jeder Agent eine Aufgabe oder einen Schritt in einem Workflow, und Agenten können Aufgaben basierend auf vordefinierten Regeln an andere Agenten übergeben.

![Hand off](../../../translated_images/de/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Kollaborative Filterung

Dieses Muster ist nützlich, wenn Sie eine Anwendung erstellen wollen, in der mehrere Agenten zusammenarbeiten, um Nutzern Empfehlungen zu geben.

Der Grund für die Zusammenarbeit mehrerer Agenten ist, dass jeder Agent unterschiedliche Expertise besitzt und den Empfehlungsprozess auf verschiedene Weise bereichern kann.

Nehmen wir das Beispiel, dass ein Nutzer eine Empfehlung für die beste Aktie für den Aktienmarkt möchte.

- **Branchenexperte**: Ein Agent könnte Experte in einer bestimmten Branche sein.
- **Technische Analyse**: Ein weiterer Agent könnte Experte in technischer Analyse sein.
- **Fundamentalanalyse**: Und ein anderer Agent könnte Experte in Fundamentalanalyse sein. Durch Zusammenarbeit können diese Agenten eine umfassendere Empfehlung für den Nutzer bereitstellen.

![Recommendation](../../../translated_images/de/multi-agent-filtering.d959cb129dc9f608.webp)

## Szenario: Rückerstattungsprozess

Betrachten Sie ein Szenario, in dem ein Kunde eine Rückerstattung für ein Produkt beantragt. Dabei können mehrere Agenten involviert sein, aber wir teilen sie auf in spezifische Agenten für diesen Prozess und allgemeine Agenten, die auch in anderen Prozessen verwendet werden können.

**Agenten spezifisch für den Rückerstattungsprozess**:

Folgende Agenten könnten im Rückerstattungsprozess beteiligt sein:

- **Kundenagent**: Dieser Agent repräsentiert den Kunden und ist verantwortlich für die Einleitung des Rückerstattungsprozesses.
- **Verkäuferagent**: Dieser Agent repräsentiert den Verkäufer und ist verantwortlich für die Abwicklung der Rückerstattung.
- **Zahlungsagent**: Dieser Agent repräsentiert den Zahlungsprozess und ist verantwortlich für die Rückzahlung des Kunden.
- **Lösungsagent**: Dieser Agent steht für den Lösungsprozess und ist verantwortlich für die Behebung von Problemen während des Rückerstattungsprozesses.
- **Compliance-Agent**: Dieser Agent stellt sicher, dass der Rückerstattungsprozess den Vorschriften und Richtlinien entspricht.

**Allgemeine Agenten**:

Diese Agenten können in anderen Teilen Ihres Unternehmens verwendet werden.

- **Versandagent**: Dieser Agent repräsentiert den Versandprozess und ist verantwortlich für den Rückversand des Produkts an den Verkäufer. Dieser Agent kann sowohl im Rückerstattungsprozess als auch beim allgemeinen Versand eines Produkts, etwa nach einem Kauf, eingesetzt werden.
- **Feedback-Agent**: Dieser Agent kümmert sich um das Sammeln von Rückmeldungen vom Kunden. Feedback kann jederzeit erfolgen, nicht nur während des Rückerstattungsprozesses.
- **Escalation-Agent**: Dieser Agent ist zuständig für die Eskalation von Problemen an eine höhere Supportebene. Diesen Agenten können Sie für jeden Prozess verwenden, bei dem eine Eskalation erforderlich ist.
- **Benachrichtigungsagent**: Dieser Agent ist für die Benachrichtigung des Kunden in verschiedenen Phasen des Rückerstattungsprozesses zuständig.
- **Analyse-Agent**: Dieser Agent analysiert Daten im Zusammenhang mit dem Rückerstattungsprozess.
- **Audit-Agent**: Dieser Agent überprüft den Rückerstattungsprozess, um dessen korrekte Durchführung sicherzustellen.
- **Reporting-Agent**: Dieser Agent erstellt Berichte zum Rückerstattungsprozess.
- **Wissensagent**: Dieser Agent verwaltet eine Wissensdatenbank mit Informationen zum Rückerstattungsprozess. Dieser Agent könnte sowohl hinsichtlich Rückerstattungen als auch anderer Geschäftsteile kundig sein.
- **Sicherheitsagent**: Dieser Agent sorgt für die Sicherheit im Rückerstattungsprozess.
- **Qualitätsagent**: Dieser Agent stellt die Qualität des Rückerstattungsprozesses sicher.

Es wurden vorher ziemlich viele Agenten genannt, sowohl für den spezifischen Rückerstattungsprozess als auch für allgemeine Agenten, die in anderen Unternehmensbereichen eingesetzt werden können. Hoffentlich gibt Ihnen das eine Vorstellung davon, wie Sie entscheiden können, welche Agenten Sie in Ihrem Multi-Agenten-System verwenden.

## Aufgabe

Entwerfen Sie ein Multi-Agenten-System für einen Kundenserviceprozess. Identifizieren Sie die im Prozess beteiligten Agenten, deren Rollen und Verantwortlichkeiten sowie ihre Interaktionen untereinander. Berücksichtigen Sie sowohl Agenten, die spezifisch für den Kundenserviceprozess sind, als auch allgemeine Agenten, die in anderen Teilen Ihres Unternehmens verwendet werden können.
> Denken Sie nach, bevor Sie die folgende Lösung lesen, Sie benötigen möglicherweise mehr Agenten, als Sie denken.

> TIPP: Denken Sie an die verschiedenen Phasen des Kundenserviceprozesses und berücksichtigen Sie auch die für jedes System benötigten Agenten.

## Lösung

[Lösung](./solution/solution.md)

## Wissensüberprüfungen

Frage: Wann sollten Sie die Verwendung von Multi-Agenten in Betracht ziehen?

- [ ] A1: Wenn Sie eine geringe Arbeitsbelastung und eine einfache Aufgabe haben.
- [ ] A2: Wenn Sie eine hohe Arbeitsbelastung haben.
- [ ] A3: Wenn Sie eine einfache Aufgabe haben.

[Lösung Quiz](./solution/solution-quiz.md)

## Zusammenfassung

In dieser Lektion haben wir uns das Multi-Agent Designmuster angesehen, einschließlich der Szenarien, in denen Multi-Agenten anwendbar sind, der Vorteile der Verwendung von Multi-Agenten gegenüber einem einzelnen Agenten, den Bausteinen zur Implementierung des Multi-Agent Designmusters und wie man die Sichtbarkeit darüber erhält, wie die mehreren Agenten miteinander interagieren.

### Haben Sie weitere Fragen zum Multi-Agent Designmuster?

Treten Sie dem [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) bei, um andere Lernende zu treffen, an Sprechstunden teilzunehmen und Ihre Fragen zu AI Agents beantwortet zu bekommen.

## Zusätzliche Ressourcen

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen Designmuster</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentic Designmuster</a>


## Vorherige Lektion

[Planungsdesign](../07-planning-design/README.md)

## Nächste Lektion

[Metakognition in AI Agents](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Haftungsausschluss**:  
Dieses Dokument wurde mithilfe des KI-Übersetzungsdienstes [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, bitten wir zu beachten, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in der jeweiligen Ausgangssprache gilt als maßgebliche Quelle. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die durch die Nutzung dieser Übersetzung entstehen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->