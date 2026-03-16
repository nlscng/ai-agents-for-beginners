# Impostazione del corso

## Introduzione

Questa lezione spiega come eseguire gli esempi di codice di questo corso.

## Unisciti ad altri studenti e ricevi aiuto

Prima di iniziare a clonare il tuo repository, unisciti al [Canale Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord) per ottenere aiuto con l'installazione, porre domande sul corso o connetterti con altri studenti.

## Clona o fai il fork di questo repository

Per iniziare, clona o fai il fork del repository GitHub. Questo creerà la tua versione del materiale del corso, così potrai eseguire, testare e modificare il codice!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fare il fork del repository</a>

You should now have your own forked version of this course in the following link:

![Repository forkato](../../../translated_images/it/forked-repo.33f27ca1901baa6a.webp)

### Clonazione superficiale (consigliata per workshop / Codespaces)

  >Il repository completo può essere grande (~3 GB) quando scarichi la cronologia completa e tutti i file. Se partecipi solo al workshop o ti servono solo alcune cartelle delle lezioni, una shallow clone (o una sparse clone) evita la maggior parte di quel download troncando la cronologia e/o saltando i blob.

#### Clonazione superficiale rapida — cronologia minima, tutti i file

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

Per clonare solo la cronologia dell'ultimo commit (scaricamento ridotto):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Per clonare un ramo specifico:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Clone parziale (sparse) — blob minimi + solo cartelle selezionate

Questo utilizza partial clone e sparse-checkout (richiede Git 2.25+ e si consiglia un Git moderno con supporto per partial clone):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Entra nella cartella del repository:

```bash|powershell
cd ai-agents-for-beginners
```

Quindi specifica quali cartelle vuoi (l'esempio sottostante mostra due cartelle):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Dopo aver clonato e verificato i file, se ti servono solo i file e vuoi liberare spazio (nessuna cronologia git), elimina i metadati del repository (💀irreversibile — perderai tutte le funzionalità di Git: nessun commit, pull, push o accesso alla cronologia).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Uso di GitHub Codespaces (consigliato per evitare grandi download locali)

- Crea un nuovo Codespace per questo repository tramite la [interfaccia di GitHub](https://github.com/codespaces).  

- Nel terminale del Codespace appena creato, esegui uno dei comandi di shallow/sparse clone sopra per portare solo le cartelle delle lezioni di cui hai bisogno nello spazio di lavoro del Codespace.
- Facoltativo: dopo il clone all'interno di Codespaces, rimuovi .git per recuperare spazio extra (vedi i comandi di rimozione sopra).
- Nota: se preferisci aprire il repository direttamente in Codespaces (senza un clone extra), tieni presente che Codespaces costruirà l'ambiente devcontainer e potrebbe ancora fornire più di quanto ti serve. Clonare una copia superficiale all'interno di un Codespace nuovo ti dà più controllo sull'utilizzo del disco.

#### Suggerimenti

- Sostituisci sempre l'URL di clone con il tuo fork se vuoi modificare/committare.
- Se in seguito avrai bisogno di più cronologia o file, puoi recuperarli o regolare sparse-checkout per includere cartelle aggiuntive.

## Esecuzione del codice

Questo corso offre una serie di notebook Jupyter che puoi eseguire per ottenere esperienza pratica nella creazione di agenti AI.

The code samples use either:

**Richiede account GitHub - Gratuito**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Etichettato come (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Etichettato come (autogen.ipynb)

**Richiede sottoscrizione Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Etichettato come (azureaiagent.ipynb)

Ti incoraggiamo a provare tutti e tre i tipi di esempi per vedere quale funziona meglio per te.

Qualunque opzione tu scelga, determinerà quali passaggi di configurazione dovrai seguire qui sotto:

## Requisiti

- Python 3.12+
  - **NOTA**: Se non hai Python3.12 installato, assicurati di installarlo.  Poi crea il tuo venv usando python3.12 per assicurarti che le versioni corrette siano installate dal file requirements.txt.
  
    >Esempio

    Crea la directory venv di Python:

    ```bash|powershell
    python -m venv venv
    ```

    Poi attiva l'ambiente venv per:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Per i codici di esempio che usano .NET, assicurati di installare [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) o successivo. Poi, verifica la versione del .NET SDK installato:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Un account GitHub - Per accedere al GitHub Models Marketplace
- Sottoscrizione Azure - Per accedere a Microsoft Foundry
- Account Microsoft Foundry - Per accedere all'Azure AI Agent Service

Abbiamo incluso un file `requirements.txt` nella radice di questo repository che contiene tutti i pacchetti Python richiesti per eseguire gli esempi di codice.

Puoi installarli eseguendo il seguente comando nel terminale nella radice del repository:

```bash|powershell
pip install -r requirements.txt
```

Raccomandiamo di creare un ambiente virtuale Python per evitare conflitti e problemi.

## Configura VSCode

Assicurati di utilizzare la versione corretta di Python in VSCode.

![immagine](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Configurazione per esempi che utilizzano GitHub Models 

### Passo 1: Recupera il tuo Personal Access Token (PAT) di GitHub

Questo corso sfrutta il GitHub Models Marketplace, fornendo accesso gratuito ai Large Language Models (LLM) che userai per costruire agenti AI.

Per usare i GitHub Models, devi creare un [Personal Access Token di GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

This can be done by going to your <a href="https://github.com/settings/personal-access-tokens" target="_blank">Impostazioni dei Personal Access Token</a> in your GitHub Account.

Per favore segui il [Principio del privilegio minimo](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) quando crei il token. Questo significa che dovresti dare al token solo le autorizzazioni di cui ha bisogno per eseguire gli esempi di codice in questo corso.

1. Seleziona l'opzione `Fine-grained tokens` sul lato sinistro dello schermo accedendo a **Impostazioni sviluppatore**

   ![Impostazioni sviluppatore](../../../translated_images/it/profile_developer_settings.410a859fe749c755.webp)

   Poi seleziona `Genera nuovo token`.

   ![Genera token](../../../translated_images/it/fga_new_token.1c1a234afe202ab3.webp)

2. Inserisci un nome descrittivo per il tuo token che rifletta il suo scopo, rendendolo facile da identificare in seguito.

    🔐 Raccomandazione durata del token

    Durata consigliata: 30 giorni
    Per una maggiore sicurezza, puoi optare per un periodo più breve—ad esempio 7 giorni 🛡️
    È un ottimo modo per fissare un obiettivo personale e completare il corso mentre il tuo slancio di apprendimento è alto 🚀.

    ![Nome token e scadenza](../../../translated_images/it/token-name-expiry-date.a095fb0de6386864.webp)

3. Limita l'ambito del token al tuo fork di questo repository.

    ![Limita ambito al fork del repository](../../../translated_images/it/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restringi le autorizzazioni del token: sotto **Autorizzazioni**, clicca sulla scheda **Account**, e clicca sul pulsante "+ Aggiungi autorizzazioni". Apparirà un menu a discesa. Cerca **Models** e seleziona la casella corrispondente.

    ![Aggiungi autorizzazione Models](../../../translated_images/it/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verifica le autorizzazioni richieste prima di generare il token. ![Verifica autorizzazioni](../../../translated_images/it/verify_permissions.06bd9e43987a8b21.webp)

6. Prima di generare il token, assicurati di essere pronto a conservare il token in un posto sicuro come un vault di un password manager, poiché non sarà mostrato di nuovo dopo la creazione. ![Archivia token in modo sicuro](../../../translated_images/it/store_token_securely.08ee2274c6ad6caf.webp)

Copia il nuovo token che hai appena creato. Ora lo aggiungerai al file `.env` incluso in questo corso.

### Passo 2: Crea il tuo file `.env`

Per creare il file `.env` esegui il seguente comando nel terminale.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Questo copierà il file di esempio e creerà un `.env` nella tua directory dove inserirai i valori delle variabili d'ambiente.

Con il token copiato, apri il file `.env` nel tuo editor di testo preferito e incolla il token nel campo `GITHUB_TOKEN`.

![Campo token GitHub](../../../translated_images/it/github_token_field.20491ed3224b5f4a.webp)

Ora dovresti essere in grado di eseguire gli esempi di codice di questo corso.

## Configurazione per esempi che utilizzano Microsoft Foundry e Azure AI Agent Service

### Passo 1: Recupera l'endpoint del tuo progetto Azure


Segui i passaggi per creare un hub e un progetto in Azure AI Foundry qui: [Panoramica delle risorse dell'hub](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Una volta creato il progetto, dovrai recuperare la stringa di connessione per il tuo progetto.

Questo può essere fatto andando alla pagina **Panoramica** del tuo progetto nel portale Microsoft Foundry.

![Stringa di connessione del progetto](../../../translated_images/it/project-endpoint.8cf04c9975bbfbf1.webp)

### Passo 2: Crea il tuo file `.env`

Per creare il file `.env` esegui il seguente comando nel terminale.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Questo copierà il file di esempio e creerà un `.env` nella tua directory dove inserirai i valori delle variabili d'ambiente.

Con la stringa copiata, apri il file `.env` nel tuo editor preferito e incolla la stringa nel campo `PROJECT_ENDPOINT`.

### Passo 3: Accedi ad Azure

Come best practice per la sicurezza, useremo l'[autenticazione senza chiave](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) per autenticare ad Azure OpenAI con Microsoft Entra ID. 

Poi, apri un terminale ed esegui `az login --use-device-code` per accedere al tuo account Azure.

Una volta effettuato l'accesso, seleziona la tua sottoscrizione nel terminale.

## Variabili d'ambiente aggiuntive - Azure Search e Azure OpenAI 

Per la lezione Agentic RAG - Lezione 5 - ci sono esempi che utilizzano Azure Search e Azure OpenAI.

Se vuoi eseguire questi esempi, dovrai aggiungere le seguenti variabili d'ambiente al tuo file `.env`:

### Pagina Panoramica (Progetto)

- `AZURE_SUBSCRIPTION_ID` - Controlla **Dettagli del progetto** nella pagina **Panoramica** del tuo progetto.

- `AZURE_AI_PROJECT_NAME` - Guarda in alto nella pagina **Panoramica** del tuo progetto.

- `AZURE_OPENAI_SERVICE` - Lo trovi nella scheda **Capacità incluse** per **Azure OpenAI Service** nella pagina **Panoramica**.

### Centro di gestione

- `AZURE_OPENAI_RESOURCE_GROUP` - Vai a **Proprietà del progetto** nella pagina **Panoramica** del **Centro di gestione**.

- `GLOBAL_LLM_SERVICE` - Sotto **Risorse connesse**, trova il nome della connessione **Azure AI Services**. Se non è elencato, controlla il **portale di Azure** nel tuo resource group per il nome della risorsa AI Services.

### Pagina Modelli + Endpoint

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Seleziona il tuo modello di embedding (es., `text-embedding-ada-002`) e annota il **Nome del deployment** dai dettagli del modello.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Seleziona il tuo modello chat (es., `gpt-4o-mini`) e annota il **Nome del deployment** dai dettagli del modello.

### Portale Azure

- `AZURE_OPENAI_ENDPOINT` - Cerca **Azure AI services**, cliccaci sopra, poi vai su **Resource Management**, **Keys and Endpoint**, scorri fino a "Azure OpenAI endpoints", e copia quello che dice "Language APIs".

- `AZURE_OPENAI_API_KEY` - Dalla stessa schermata, copia KEY 1 o KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Trova la tua risorsa **Azure AI Search**, cliccaci sopra e vai su **Panoramica**.

- `AZURE_SEARCH_API_KEY` - Poi vai su **Settings** e poi su **Keys** per copiare la chiave admin primaria o secondaria.

### Pagina esterna

- `AZURE_OPENAI_API_VERSION` - Visita la pagina [Ciclo di vita delle versioni API](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) sotto **Ultimo rilascio GA dell'API**.

### Configura l'autenticazione senza chiave

Invece di inserire le credenziali nel codice, useremo una connessione senza chiave con Azure OpenAI. Per farlo, importeremo `DefaultAzureCredential` e più avanti chiameremo la funzione `DefaultAzureCredential` per ottenere la credenziale.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Bloccato da qualche parte?
Se riscontri problemi nell'esecuzione di questa configurazione, unisciti al nostro <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord della community Azure AI</a> o <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">segnala un problema</a>.

## Lezione successiva

Ora sei pronto per eseguire il codice di questo corso. Buon apprendimento e buona esplorazione del mondo degli agenti AI! 

[Introduzione agli agenti AI e casi d'uso degli agenti](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Dichiarazione di non responsabilità:
Questo documento è stato tradotto utilizzando il servizio di traduzione automatica [Co-op Translator](https://github.com/Azure/co-op-translator). Sebbene ci impegniamo per garantire l'accuratezza, si prega di notare che le traduzioni automatiche possono contenere errori o imprecisioni. Il documento originale nella lingua di partenza deve essere considerato la fonte autorevole. Per informazioni critiche, si raccomanda una traduzione professionale eseguita da un traduttore umano. Non siamo responsabili per eventuali incomprensioni o interpretazioni errate derivanti dall'uso di questa traduzione.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->