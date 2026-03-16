# Kurs-Setup

## Einführung

Diese Lektion behandelt, wie Sie die Codebeispiele dieses Kurses ausführen.

## Treten Sie anderen Lernenden bei und holen Sie sich Hilfe

Bevor Sie mit dem Klonen Ihres Repos beginnen, treten Sie dem [Discord-Kanal „AI Agents For Beginners“](https://aka.ms/ai-agents/discord) bei, um Hilfe beim Setup zu erhalten, Fragen zum Kurs zu stellen oder sich mit anderen Lernenden zu vernetzen.

## Dieses Repo klonen oder forken

Um zu beginnen, klonen oder forken Sie bitte das GitHub-Repository. Dadurch erstellen Sie Ihre eigene Version des Kursmaterials, sodass Sie den Code ausführen, testen und anpassen können!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">das Repository forken</a>

Sie sollten jetzt Ihre eigene geforkte Version dieses Kurses unter folgendem Link haben:

![Geforktes Repository](../../../translated_images/de/forked-repo.33f27ca1901baa6a.webp)

### Flacher Clone (empfohlen für Workshop / Codespaces)

  >Das gesamte Repository kann groß sein (~3 GB), wenn Sie die komplette Historie und alle Dateien herunterladen. Wenn Sie nur am Workshop teilnehmen oder nur einige Lektionen benötigen, vermeidet ein flacher Clone (oder ein sparse clone) den größten Teil dieses Downloads, indem die Historie gekürzt und/oder Blobs übersprungen werden.

#### Schneller flacher Clone — minimale Historie, alle Dateien

Ersetzen Sie `<your-username>` in den folgenden Befehlen durch Ihre Fork-URL (oder die Upstream-URL, falls Sie diese bevorzugen).

Um nur die neueste Commit-Historie zu klonen (kleiner Download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Um einen bestimmten Branch zu klonen:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Partieller (sparse) Clone — minimale Blobs + nur ausgewählte Ordner

Dies verwendet partial clone und sparse-checkout (erfordert Git 2.25+ und ein empfohlenes modernes Git mit Unterstützung für partial clone):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Wechseln Sie in den Repo-Ordner:

```bash|powershell
cd ai-agents-for-beginners
```

Geben Sie dann an, welche Ordner Sie möchten (Beispiel unten zeigt zwei Ordner):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Nachdem Sie geklont und die Dateien überprüft haben: Wenn Sie nur die Dateien benötigen und Speicherplatz freigeben möchten (keine Git-Historie), löschen Sie bitte die Repository-Metadaten (💀 irreversibel — Sie verlieren alle Git-Funktionalitäten: keine Commits, Pulls, Pushes oder Zugriff auf die Historie).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Verwendung von GitHub Codespaces (empfohlen, um große lokale Downloads zu vermeiden)

- Erstellen Sie über die [GitHub UI](https://github.com/codespaces) einen neuen Codespace für dieses Repo.  

- Führen Sie im Terminal des neu erstellten Codespace einen der oben genannten flachen/sparse Clone-Befehle aus, um nur die benötigten Lektionen in den Codespace-Arbeitsbereich zu holen.
- Optional: Entfernen Sie nach dem Klonen innerhalb von Codespaces .git, um zusätzlichen Speicherplatz zurückzugewinnen (siehe die oben genannten Entfernen-Befehle).
- Hinweis: Wenn Sie das Repo direkt in Codespaces öffnen möchten (ohne einen zusätzlichen Klon), beachten Sie, dass Codespaces die devcontainer-Umgebung erstellt und möglicherweise mehr bereitstellt, als Sie benötigen. Das Klonen einer flachen Kopie innerhalb eines frischen Codespace gibt Ihnen mehr Kontrolle über die Speichernutzung.

#### Tipps

- Ersetzen Sie immer die Clone-URL durch Ihre Fork, wenn Sie bearbeiten/committen möchten.
- Wenn Sie später mehr Historie oder Dateien benötigen, können Sie diese abrufen oder sparse-checkout anpassen, um zusätzliche Ordner einzuschließen.

## Code ausführen

Dieser Kurs bietet eine Reihe von Jupyter-Notebooks, die Sie ausführen können, um praktische Erfahrungen beim Erstellen von KI-Agenten zu sammeln.

Die Codebeispiele verwenden eines der folgenden:

**Benötigt GitHub-Konto - Kostenlos**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Bezeichnet als (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Bezeichnet als (autogen.ipynb)

**Benötigt Azure-Abonnement**:
3) Azure AI Foundry + Azure AI Agent Service. Bezeichnet als (azureaiagent.ipynb)

Wir empfehlen Ihnen, alle drei Beispieltypen auszuprobieren, um herauszufinden, welcher am besten für Sie funktioniert.

Welche Option Sie auch wählen, sie bestimmt, welche Einrichtungsschritte Sie unten befolgen müssen:

## Voraussetzungen

- Python 3.12+
  - **HINWEIS**: Wenn Sie Python 3.12 nicht installiert haben, installieren Sie es bitte. Erstellen Sie dann Ihr venv mit python3.12, um sicherzustellen, dass die korrekten Versionen aus der Datei requirements.txt installiert werden.
  
    >Beispiel

    Create Python venv directory:

    ```bash|powershell
    python -m venv venv
    ```

    Aktivieren Sie dann die venv-Umgebung für:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Für die Beispielcodes, die .NET verwenden, installieren Sie das [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) oder neuer. Überprüfen Sie anschließend Ihre installierte .NET SDK-Version:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Ein GitHub-Konto - Für den Zugriff auf den GitHub Models Marketplace
- Azure-Abonnement - Für den Zugriff auf Microsoft Foundry
- Microsoft Foundry-Konto - Für den Zugriff auf den Azure AI Agent Service

Wir haben eine Datei `requirements.txt` im Root dieses Repositories hinzugefügt, die alle erforderlichen Python-Pakete enthält, um die Codebeispiele auszuführen.

Sie können diese installieren, indem Sie den folgenden Befehl im Terminal im Root des Repositories ausführen:

```bash|powershell
pip install -r requirements.txt
```

Wir empfehlen, eine Python-virtuelle Umgebung zu erstellen, um Konflikte und Probleme zu vermeiden.

## VSCode einrichten

Stellen Sie sicher, dass Sie in VSCode die richtige Python-Version verwenden.

![Bild](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Einrichtung für Beispiele mit GitHub Models 

### Schritt 1: Abrufen Ihres GitHub Personal Access Token (PAT)

Dieser Kurs nutzt den GitHub Models Marketplace, der kostenlosen Zugriff auf Large Language Models (LLMs) bietet, die Sie zum Erstellen von AI Agents verwenden werden.

Um die GitHub Models zu nutzen, müssen Sie ein [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) erstellen.

This can be done by going to your <a href="https://github.com/settings/personal-access-tokens" target="_blank">Einstellungen für Personal Access Tokens</a> in Ihrem GitHub-Konto.

Bitte befolgen Sie das [Prinzip der geringsten Privilegien](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely), wenn Sie Ihr Token erstellen. Das bedeutet, dass Sie dem Token nur die Berechtigungen geben sollten, die es benötigt, um die Codebeispiele in diesem Kurs auszuführen.

1. Wählen Sie die Option `Fine-grained tokens` auf der linken Seite Ihres Bildschirms, indem Sie zu den **Developer settings** navigieren

   ![Entwickler-Einstellungen](../../../translated_images/de/profile_developer_settings.410a859fe749c755.webp)

   Wählen Sie dann `Generate new token`.

   ![Token generieren](../../../translated_images/de/fga_new_token.1c1a234afe202ab3.webp)

2. Geben Sie einen beschreibenden Namen für Ihr Token ein, der seinen Zweck widerspiegelt und das spätere Identifizieren erleichtert.

    🔐 Empfehlung zur Token-Laufzeit

    Empfohlene Dauer: 30 Tage
    Für eine sicherere Vorgehensweise können Sie eine kürzere Periode wählen—z. B. 7 Tage 🛡️
    Das ist eine gute Möglichkeit, ein persönliches Ziel zu setzen und den Kurs zu beenden, solange Ihre Lernmotivation hoch ist 🚀.

    ![Token-Name und Ablaufdatum](../../../translated_images/de/token-name-expiry-date.a095fb0de6386864.webp)

3. Beschränken Sie den Geltungsbereich des Tokens auf Ihren Fork dieses Repositories.

    ![Geltungsbereich auf Fork beschränken](../../../translated_images/de/token_repository_limit.924ade5e11d9d8bb.webp)

4. Beschränken Sie die Berechtigungen des Tokens: Unter **Permissions** klicken Sie auf die Registerkarte **Account**, und klicken Sie auf die Schaltfläche "+ Add permissions". Ein Dropdown-Menü erscheint. Bitte suchen Sie nach **Models** und aktivieren Sie das Kontrollkästchen dafür.

    ![Models-Berechtigung hinzufügen](../../../translated_images/de/add_models_permissions.c0c44ed8b40fc143.webp)

5. Überprüfen Sie die erforderlichen Berechtigungen, bevor Sie das Token erstellen. ![Berechtigungen überprüfen](../../../translated_images/de/verify_permissions.06bd9e43987a8b21.webp)

6. Bevor Sie das Token erstellen, stellen Sie sicher, dass Sie es an einem sicheren Ort wie einem Passwort-Manager speichern können, da es nach der Erstellung nicht erneut angezeigt wird. ![Token sicher speichern](../../../translated_images/de/store_token_securely.08ee2274c6ad6caf.webp)

Kopieren Sie Ihr neu erstelltes Token. Fügen Sie es nun in die in diesem Kurs enthaltene Datei `.env` ein.

### Schritt 2: Erstellen Sie Ihre `.env`-Datei

Um Ihre `.env`-Datei zu erstellen, führen Sie den folgenden Befehl in Ihrem Terminal aus.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dies kopiert die Beispieldatei und erstellt eine `.env` in Ihrem Verzeichnis, in der Sie die Werte für die Umgebungsvariablen eintragen.

Öffnen Sie mit kopiertem Token die `.env`-Datei in Ihrem bevorzugten Texteditor und fügen Sie Ihr Token in das Feld `GITHUB_TOKEN` ein.

![GitHub Token Feld](../../../translated_images/de/github_token_field.20491ed3224b5f4a.webp)

Sie sollten nun in der Lage sein, die Codebeispiele dieses Kurses auszuführen.

## Einrichtung für Beispiele mit Microsoft Foundry und Azure AI Agent Service

### Schritt 1: Abrufen Ihres Azure-Projektendpunkts


Befolgen Sie die Schritte zur Erstellung eines Hubs und Projekts in Azure AI Foundry, die hier beschrieben sind: [Übersicht zu Hub-Ressourcen](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Nachdem Sie Ihr Projekt erstellt haben, müssen Sie die Verbindungszeichenfolge für Ihr Projekt abrufen.

Dies können Sie tun, indem Sie auf die **Overview**-Seite Ihres Projekts im Microsoft Foundry-Portal gehen.

![Projekt-Verbindungszeichenfolge](../../../translated_images/de/project-endpoint.8cf04c9975bbfbf1.webp)

### Schritt 2: Erstellen Sie Ihre `.env`-Datei

Um Ihre `.env`-Datei zu erstellen, führen Sie den folgenden Befehl in Ihrem Terminal aus.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dies kopiert die Beispieldatei und erstellt eine `.env` in Ihrem Verzeichnis, in der Sie die Werte für die Umgebungsvariablen eintragen.

Öffnen Sie mit kopiertem Token die `.env`-Datei in Ihrem bevorzugten Texteditor und fügen Sie Ihr Token in das Feld `PROJECT_ENDPOINT` ein.

### Schritt 3: Bei Azure anmelden

Als Best Practice für die Sicherheit verwenden wir [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst), um uns mit Microsoft Entra ID bei Azure OpenAI zu authentifizieren. 

Öffnen Sie als Nächstes ein Terminal und führen Sie `az login --use-device-code` aus, um sich bei Ihrem Azure-Konto anzumelden.

Nachdem Sie sich angemeldet haben, wählen Sie Ihr Abonnement im Terminal aus.

## Zusätzliche Umgebungsvariablen - Azure Search und Azure OpenAI 

Für die Agentic RAG-Lektion - Lektion 5 - gibt es Beispiele, die Azure Search und Azure OpenAI verwenden.

Wenn Sie diese Beispiele ausführen möchten, müssen Sie die folgenden Umgebungsvariablen zu Ihrer `.env`-Datei hinzufügen:

### Übersicht-Seite (Projekt)

- `AZURE_SUBSCRIPTION_ID` - Überprüfen Sie die **Project details** auf der **Overview**-Seite Ihres Projekts.

- `AZURE_AI_PROJECT_NAME` - Sehen Sie oben auf der **Overview**-Seite Ihres Projekts nach.

- `AZURE_OPENAI_SERVICE` - Finden Sie dies auf der **Included capabilities**-Registerkarte für **Azure OpenAI Service** auf der **Overview**-Seite.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - Gehen Sie zu **Project properties** auf der **Overview**-Seite des **Management Center**.

- `GLOBAL_LLM_SERVICE` - Unter **Connected resources** finden Sie den Verbindungsnamen **Azure AI Services**. Falls nicht aufgeführt, prüfen Sie das **Azure portal** in Ihrer Ressourcengruppe nach dem Namen der AI Services-Ressource.

### Models + Endpoints-Seite

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Wählen Sie Ihr Embedding-Modell (z. B. `text-embedding-ada-002`) und notieren Sie den **Deployment name** aus den Modelldetails.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Wählen Sie Ihr Chat-Modell (z. B. `gpt-4o-mini`) und notieren Sie den **Deployment name** aus den Modelldetails.

### Azure-Portal

- `AZURE_OPENAI_ENDPOINT` - Suchen Sie nach **Azure AI services**, klicken Sie darauf, gehen Sie dann zu **Resource Management**, **Keys and Endpoint**, scrollen Sie zu den "Azure OpenAI endpoints" und kopieren Sie diejenige, die als "Language APIs" bezeichnet ist.

- `AZURE_OPENAI_API_KEY` - Kopieren Sie auf derselben Seite KEY 1 oder KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Finden Sie Ihre **Azure AI Search**-Ressource, klicken Sie darauf und sehen Sie die **Overview**.

- `AZURE_SEARCH_API_KEY` - Gehen Sie dann zu **Settings** und anschließend zu **Keys**, um den primären oder sekundären Admin-Schlüssel zu kopieren.

### Externe Webseite

- `AZURE_OPENAI_API_VERSION` - Besuchen Sie die Seite [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) unter **Latest GA API release**.

### Keyless-Authentifizierung einrichten

Anstatt Ihre Anmeldeinformationen fest im Code zu hinterlegen, verwenden wir eine keyless-Verbindung mit Azure OpenAI. Dazu importieren wir `DefaultAzureCredential` und rufen später die Funktion `DefaultAzureCredential` auf, um die Anmeldeinformationen zu erhalten.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Festgefahren?
Wenn Sie Probleme bei der Ausführung dieses Setups haben, treten Sie unserem <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> bei oder <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">erstellen Sie ein Issue</a>.

## Nächste Lektion

Sie sind jetzt bereit, den Code für diesen Kurs auszuführen. Viel Spaß beim weiteren Kennenlernen der Welt der KI-Agenten! 

[Einführung in KI-Agenten und Anwendungsfälle](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Haftungsausschluss:
Dieses Dokument wurde mit dem KI-Übersetzungsdienst Co-op Translator (https://github.com/Azure/co-op-translator) übersetzt. Obwohl wir uns um Genauigkeit bemühen, beachten Sie bitte, dass automatisierte Übersetzungen Fehler oder Ungenauigkeiten enthalten können. Das Originaldokument in seiner Ausgangssprache ist als maßgebliche Quelle zu betrachten. Bei wichtigen Informationen wird eine professionelle menschliche Übersetzung empfohlen. Wir übernehmen keine Haftung für Missverständnisse oder Fehlinterpretationen, die sich aus der Verwendung dieser Übersetzung ergeben.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->