# AGENTS.md

## Projektübersicht

Dieses Repository enthält "KI-Agenten für Einsteiger" – einen umfassenden Bildungskurs, der alles beibringt, was zum Erstellen von KI-Agenten erforderlich ist. Der Kurs besteht aus mehr als 15 Lektionen, die Grundlagen, Entwurfsmuster, Frameworks und den Produktionseinsatz von KI-Agenten abdecken.

**Schlüsseltechnologien:**
- Python 3.12+
- Jupyter Notebooks für interaktives Lernen
- KI-Frameworks: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure KI-Dienste: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (kostenlose Stufe verfügbar)

**Architektur:**
- Lektionenbasierte Struktur (Verzeichnisse 00-15+)
- Jede Lektion enthält: README-Dokumentation, Codebeispiele (Jupyter-Notebooks) und Bilder
- Mehrsprachige Unterstützung über automatisches Übersetzungssystem
- Mehrere Framework-Optionen pro Lektion (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Einrichtungsbefehle

### Voraussetzungen
- Python 3.12 oder höher
- GitHub-Konto (für GitHub Models – kostenlose Stufe)
- Azure-Abonnement (optional, für Azure KI-Dienste)

### Erste Einrichtung

1. **Repository klonen oder forken:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ODER
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Python-Virtual Environment erstellen und aktivieren:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Unter Windows: venv\Scripts\activate
   ```

3. **Abhängigkeiten installieren:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Umgebungsvariablen einrichten:**
   ```bash
   cp .env.example .env
   # Bearbeiten Sie .env mit Ihren API-Schlüsseln und Endpunkten
   ```

### Erforderliche Umgebungsvariablen

Für **GitHub Models (Kostenlos)**:
- `GITHUB_TOKEN` – Persönlicher Zugriffstoken von GitHub

Für **Azure KI-Dienste** (optional):
- `PROJECT_ENDPOINT` – Microsoft Foundry Projekt-Endpunkt
- `AZURE_OPENAI_API_KEY` – Azure OpenAI API-Schlüssel
- `AZURE_OPENAI_ENDPOINT` – Azure OpenAI Endpunkt-URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` – Deploy-Name für Chatmodell
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` – Deploy-Name für Embeddings
- Weitere Azure-Konfiguration wie in `.env.example` gezeigt

## Entwicklungsworkflow

### Jupyter Notebooks ausführen

Jede Lektion enthält mehrere Jupyter-Notebooks für verschiedene Frameworks:

1. **Jupyter starten:**
   ```bash
   jupyter notebook
   ```

2. **Zum Lektionenverzeichnis navigieren** (z.B. `01-intro-to-ai-agents/code_samples/`)

3. **Notebooks öffnen und ausführen:**
   - `*-semantic-kernel.ipynb` – Verwendung des Semantic Kernel Frameworks
   - `*-autogen.ipynb` – Verwendung des AutoGen Frameworks
   - `*-python-agent-framework.ipynb` – Verwendung des Microsoft Agent Frameworks (Python)
   - `*-dotnet-agent-framework.ipynb` – Verwendung des Microsoft Agent Frameworks (.NET)
   - `*-azureaiagent.ipynb` – Verwendung des Azure AI Agent Service

### Arbeiten mit verschiedenen Frameworks

**Semantic Kernel + GitHub Models:**
- Kostenlose Stufe mit GitHub-Konto verfügbar
- Gut zum Lernen und Experimentieren
- Dateimuster: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Kostenlose Stufe mit GitHub-Konto verfügbar
- Fähigkeiten zur Orchestrierung mehrerer Agenten
- Dateimuster: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Neuestes Framework von Microsoft
- Verfügbar für Python und .NET
- Dateimuster: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Erfordert Azure-Abonnement
- Produktionsreife Funktionen
- Dateimuster: `*-azureaiagent.ipynb`

## Testanweisungen

Dies ist ein Bildungs-Repository mit Beispielcode statt Produktionscode mit automatisierten Tests. Zur Überprüfung Ihrer Einrichtung und Änderungen:

### Manueller Test

1. **Python-Umgebung testen:**
   ```bash
   python --version  # Sollte 3.12+ sein
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Ausführung der Notebooks testen:**
   ```bash
   # Notizbuch in Skript umwandeln und ausführen (Tests importieren)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Umgebungsvariablen prüfen:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Einzelne Notebooks ausführen

Öffnen Sie Notebooks in Jupyter und führen Sie Zellen nacheinander aus. Jedes Notebook ist eigenständig und enthält:
- Importanweisungen
- Konfigurationsladevorgänge
- Beispielimplementierungen von Agenten
- Erwartete Ausgaben in Markdown-Zellen

## Code-Stil

### Python-Konventionen

- **Python-Version**: 3.12+
- **Code-Stil**: Folgen Sie den Standard-PEP 8-Konventionen für Python
- **Notebooks**: Verwenden Sie klare Markdown-Zellen zur Erklärung von Konzepten
- **Imports**: Gruppieren nach Standardbibliothek, Drittanbieter, lokale Importe

### Jupyter Notebook Konventionen

- Beschreibende Markdown-Zellen vor Codezellen einfügen
- Ausgabenbeispiele in Notebooks als Referenz hinzufügen
- Klare Variablennamen verwenden, die den Lektionsthemen entsprechen
- Die Ausführungsreihenfolge der Notebooks linear halten (Zelle 1 → 2 → 3 ...)

### Dateiorganisation

```
<lesson-number>-<lesson-name>/
├── README.md                     # Lesson documentation
├── code_samples/
│   ├── <number>-semantic-kernel.ipynb
│   ├── <number>-autogen.ipynb
│   ├── <number>-python-agent-framework.ipynb
│   └── <number>-azureaiagent.ipynb
└── images/
    └── *.png
```

## Erstellung und Bereitstellung

### Dokumentation erstellen

Dieses Repository verwendet Markdown für die Dokumentation:
- README.md Dateien in jedem Lektionenordner
- Haupt-README.md im Repository-Stamm
- Automatisches Übersetzungssystem über GitHub Actions

### CI/CD-Pipeline

Im Verzeichnis `.github/workflows/`:

1. **co-op-translator.yml** – Automatische Übersetzung in mehr als 50 Sprachen
2. **welcome-issue.yml** – Begrüßt neue Issue-Ersteller
3. **welcome-pr.yml** – Begrüßt neue Pull-Request-Beiträger

### Bereitstellung

Dies ist ein Bildungs-Repository – kein Bereitstellungsprozess. Nutzer:
1. Forken oder klonen das Repository
2. Führen Notebooks lokal oder in GitHub Codespaces aus
3. Lernen durch Ändern und Experimentieren mit Beispielen

## Richtlinien für Pull Requests

### Vor dem Einreichen

1. **Änderungen testen:**
   - Führen Sie alle betroffenen Notebooks vollständig aus
   - Stellen Sie sicher, dass alle Zellen ohne Fehler ausgeführt werden
   - Überprüfen Sie, ob die Ausgaben angemessen sind

2. **Dokumentationsupdates:**
   - README.md aktualisieren, wenn neue Konzepte hinzugefügt werden
   - Kommentare in Notebooks für komplexen Code ergänzen
   - Markdown-Zellen sollen den Zweck erläutern

3. **Dateiänderungen:**
   - `.env`-Dateien nicht einchecken (verwenden Sie `.env.example`)
   - Keine `venv/`- oder `__pycache__/`-Verzeichnisse committen
   - Notebook-Ausgaben beibehalten, wenn sie Konzepte verdeutlichen
   - Temporäre Dateien und Backup-Notebooks (`*-backup.ipynb`) entfernen

### PR-Titel-Format

Verwenden Sie beschreibende Titel:
- `[Lesson-XX] Neues Beispiel für <Konzept> hinzufügen`
- `[Fix] Tippfehler in lesson-XX README korrigieren`
- `[Update] Codebeispiel in lesson-XX verbessern`
- `[Docs] Setup-Anweisungen aktualisieren`

### Erforderliche Prüfungen

- Notebooks sollten fehlerfrei ausgeführt werden
- README-Dateien sollten klar und korrekt sein
- Bestehenden Code-Stil im Repository befolgen
- Konsistenz mit anderen Lektionen wahren

## Zusätzliche Hinweise

### Häufige Fehler

1. **Python-Versionskonflikte:**
   - Stellen Sie sicher, dass Python 3.12+ verwendet wird
   - Manche Pakete funktionieren nicht mit älteren Versionen
   - Verwenden Sie `python3 -m venv`, um die Python-Version explizit festzulegen

2. **Umgebungsvariablen:**
   - Erstellen Sie immer `.env` aus `.env.example`
   - Committen Sie `.env` nicht (ist in `.gitignore`)
   - GitHub-Token benötigt die entsprechenden Berechtigungen

3. **Paketkonflikte:**
   - Nutzen Sie eine frische virtuelle Umgebung
   - Installieren Sie aus `requirements.txt`, nicht einzelne Pakete
   - Einige Notebooks benötigen zusätzliche Pakete, die in ihren Markdown-Zellen erwähnt werden

4. **Azure-Dienste:**
   - Azure KI-Dienste erfordern ein aktives Abonnement
   - Manche Features sind regionsspezifisch
   - Kostenlose Stufe gilt für GitHub Models

### Lernpfad

Empfohlene Reihenfolge der Lektionen:
1. **00-course-setup** – Start hier für Einrichtung der Umgebung
2. **01-intro-to-ai-agents** – Grundlagen von KI-Agenten verstehen
3. **02-explore-agentic-frameworks** – Verschiedene Frameworks kennenlernen
4. **03-agentic-design-patterns** – Kern-Entwurfsmuster
5. Folgen Sie der nummerierten Reihenfolge der Lektionen

### Framework-Auswahl

Framework je nach Ziel wählen:
- **Lernen/Prototyping**: Semantic Kernel + GitHub Models (kostenlos)
- **Multi-Agenten-Systeme**: AutoGen
- **Neueste Features**: Microsoft Agent Framework (MAF)
- **Produktive Bereitstellung**: Azure AI Agent Service

### Unterstützung erhalten

- Treten Sie dem [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord) bei
- Lesen Sie die README-Dateien der Lektionen für spezifische Hinweise
- Überprüfen Sie die Haupt-README.md für Kursübersicht
- Folgen Sie den Anweisungen unter [Course Setup](./00-course-setup/README.md) für detaillierte Einrichtung

### Beiträge

Dies ist ein offenes Bildungsprojekt. Beiträge sind willkommen:
- Verbesserung von Codebeispielen
- Korrektur von Tippfehlern oder Fehlern
- Hinzufügen erläuternder Kommentare
- Vorschläge für neue Lektionsthemen
- Übersetzungen in weitere Sprachen

Siehe [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) für aktuelle Bedarfe.

## Projektspezifischer Kontext

### Mehrsprachige Unterstützung

Dieses Repository verwendet ein automatisiertes Übersetzungssystem:
- Mehr als 50 Sprachen unterstützt
- Übersetzungen in Verzeichnissen `/translations/<lang-code>/`
- GitHub Actions-Workflow aktualisiert Übersetzungen automatisch
- Quelldateien sind auf Englisch im Repository-Stamm

### Lektionenstruktur

Jede Lektion folgt einem konsistenten Muster:
1. Video-Vorschaubild mit Link
2. Schriftlicher Lektionstext (README.md)
3. Codebeispiele in mehreren Frameworks
4. Lernziele und Voraussetzungen
5. Zusätzliche Lernressourcen verlinkt

### Namensgebung der Codebeispiele

Format: `<Lektionsnummer>-<Framework-Name>.ipynb`
- `04-semantic-kernel.ipynb` – Lektion 4, Semantic Kernel
- `07-autogen.ipynb` – Lektion 7, AutoGen
- `14-python-agent-framework.ipynb` – Lektion 14, MAF Python
- `14-dotnet-agent-framework.ipynb` – Lektion 14, MAF .NET

### Spezielle Verzeichnisse

- `translated_images/` – Lokalisierte Bilder für Übersetzungen
- `images/` – Originalbilder für englischen Inhalt
- `.devcontainer/` – VS Code Entwicklungscontainer-Konfiguration
- `.github/` – GitHub Actions Workflows und Vorlagen

### Abhängigkeiten

Wichtige Pakete aus `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` – AutoGen Framework
- `semantic-kernel` – Semantic Kernel Framework
- `agent-framework` – Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` – Azure KI-Dienste
- `azure-search-documents` – Azure KI-Suche Integration
- `chromadb` – Vektordatenbank für RAG-Beispiele
- `chainlit` – Chat UI Framework
- `browser_use` – Browser-Automatisierung für Agenten
- `mcp[cli]` – Model Context Protocol Unterstützung
- `mem0ai` – Speichermanagement für Agenten

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Haftungsausschluss**:
Dieses Dokument wurde mithilfe des KI-Übersetzungsdienstes [Co-op Translator](https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir um Genauigkeit bemüht sind, können automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten. Das Originaldokument in seiner ursprünglichen Sprache gilt als verbindliche Quelle. Für wichtige Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die aus der Verwendung dieser Übersetzung entstehen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->