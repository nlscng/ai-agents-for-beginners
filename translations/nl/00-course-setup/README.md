# Course Setup

## Introduction

Deze les behandelt hoe je de codevoorbeelden van deze cursus kunt uitvoeren.

## Join Other Learners and Get Help

Voordat je je repo kloont, sluit je aan bij het [AI Agents For Beginners Discord channel](https://aka.ms/ai-agents/discord) om hulp te krijgen bij de setup, vragen over de cursus, of om in contact te komen met andere cursisten.

## Clone or Fork this Repo

Om te beginnen, kloon of fork je de GitHub-repository. Dit maakt je eigen versie van het cursusmateriaal zodat je de code kunt uitvoeren, testen en aanpassen!

Dit kan gedaan worden door op de link te klikken om <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">een fork van de repo te maken</a>

Je zou nu je eigen geforkte versie van deze cursus in de volgende link moeten hebben:

![Geforkte repo](../../../translated_images/nl/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (aanbevolen voor workshop / Codespaces)

  >De volledige repository kan groot zijn (~3 GB) wanneer je de volledige geschiedenis en alle bestanden downloadt. Als je alleen de workshop bijwoont of slechts een paar lesmappen nodig hebt, voorkomt een shallow clone (of een sparse clone) dat je dat grootste deel van de download krijgt door de geschiedenis in te korten en/of blobs over te slaan.

#### Snelle shallow clone — minimale geschiedenis, alle bestanden

Vervang `<your-username>` in de onderstaande opdrachten door je fork URL (of de upstream URL als je dat prefereert).

Om alleen de laatste commitgeschiedenis te clonen (kleine download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Om een specifieke branch te clonen:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Gedeeltelijke (sparse) clone — minimale blobs + alleen geselecteerde mappen

Dit gebruikt partial clone en sparse-checkout (vereist Git 2.25+ en aanbevolen moderne Git met partial clone-ondersteuning):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Ga naar de repo-map:

```bash|powershell
cd ai-agents-for-beginners
```

Geef vervolgens op welke mappen je wilt (voorbeeld toont twee mappen):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Na het clonen en verifiëren van de bestanden, als je alleen de bestanden nodig hebt en ruimte wilt vrijmaken (geen git-geschiedenis), verwijder dan de repository-metadata (💀onomkeerbaar — je verliest alle Git-functionaliteit: geen commits, pulls, pushes of toegang tot geschiedenis).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Gebruik van GitHub Codespaces (aanbevolen om lokale grote downloads te voorkomen)

- Maak een nieuwe Codespace voor deze repo via de [GitHub UI](https://github.com/codespaces).  

- Voer in de terminal van de nieuw gemaakte Codespace een van de shallow/sparse clone-opdrachten hierboven uit om alleen de lesmappen die je nodig hebt in de Codespace-werkruimte te brengen.
- Optioneel: verwijder na het clonen binnen Codespaces .git om extra ruimte terug te winnen (zie verwijderopdrachten hierboven).
- Opmerking: Als je de voorkeur geeft aan het rechtstreeks openen van de repo in Codespaces (zonder een extra clone), wees je er dan van bewust dat Codespaces de devcontainer-omgeving zal opbouwen en mogelijk nog steeds meer zal provisionen dan je nodig hebt. Het clonen van een shallow kopie binnen een verse Codespace geeft je meer controle over schijfgebruik.

#### Tips

- Vervang altijd de clone-URL door je fork als je wilt bewerken/committen.
- Als je later meer geschiedenis of bestanden nodig hebt, kun je deze ophalen of sparse-checkout aanpassen om extra mappen op te nemen.

## Running the Code

Deze cursus biedt een reeks Jupyter Notebooks die je kunt uitvoeren om praktische ervaring op te doen met het bouwen van AI-agents.

De codevoorbeelden gebruiken ofwel:

**Requires GitHub Account - Free**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Gelabeld als (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Gelabeld als (autogen.ipynb)

**Requires Azure Subscription**:
3) Azure AI Foundry + Azure AI Agent Service. Gelabeld als (azureaiagent.ipynb)

We moedigen je aan om alle drie de typen voorbeelden uit te proberen om te zien welke het beste voor jou werkt.

Welke optie je ook kiest, dat bepaalt welke setupstappen je hieronder moet volgen:

## Requirements

- Python 3.12+
  - **NOTE**: Als je Python3.12 niet hebt geïnstalleerd, zorg dan dat je het installeert. Maak daarna je venv aan met python3.12 om ervoor te zorgen dat de juiste versies worden geïnstalleerd vanuit het requirements.txt-bestand.
  
    >Voorbeeld

    Maak een Python venv-map aan:

    ```bash|powershell
    python -m venv venv
    ```

    Activeer vervolgens de venv-omgeving voor:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Voor de voorbeeldcodes die .NET gebruiken, zorg dat je [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) of later installeert. Controleer daarna je geïnstalleerde .NET SDK-versie:

    ```bash|powershell
    dotnet --list-sdks
    ```

- A GitHub Account - For Access to the GitHub Models Marketplace
- Azure Subscription - For Access to Microsoft Foundry
- Microsoft Foundry Account - For Access to the Azure AI Agent Service

We hebben een `requirements.txt` bestand opgenomen in de root van deze repository dat alle vereiste Python-pakketten bevat om de codevoorbeelden uit te voeren.

Je kunt ze installeren door het volgende commando uit te voeren in je terminal in de root van de repository:

```bash|powershell
pip install -r requirements.txt
```

We raden aan om een Python virtual environment te creëren om conflicten en problemen te voorkomen.

## Setup VSCode

Zorg ervoor dat je de juiste versie van Python gebruikt in VSCode.

![afbeelding](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Set Up for Samples using GitHub Models 

### Step 1: Retrieve Your GitHub Personal Access Token (PAT)

Deze cursus maakt gebruik van de GitHub Models Marketplace, die gratis toegang biedt tot Large Language Models (LLMs) die je zult gebruiken om AI-agents te bouwen.

Om de GitHub Models te gebruiken, moet je een [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) aanmaken.

Dit kan gedaan worden door naar je <a href="https://github.com/settings/personal-access-tokens" target="_blank">Personal Access Tokens-instellingen</a> in je GitHub-account te gaan.

Volg alstublieft het [Principle of Least Privilege](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) bij het creëren van je token. Dit betekent dat je het token alleen de permissies moet geven die nodig zijn om de codevoorbeelden in deze cursus uit te voeren.

1. Selecteer de optie `Fine-grained tokens` aan de linkerkant van je scherm door naar de **Developer settings** te gaan

   ![Developer instellingen](../../../translated_images/nl/profile_developer_settings.410a859fe749c755.webp)

   Selecteer vervolgens `Generate new token`.

   ![Genereer Token](../../../translated_images/nl/fga_new_token.1c1a234afe202ab3.webp)

2. Voer een beschrijvende naam in voor je token die het doel weergeeft, zodat je het later gemakkelijk kunt herkennen.

    🔐 Aanbeveling voor tokenduur

    Aanbevolen duur: 30 dagen
    Voor een veiliger aanpak kun je kiezen voor een kortere periode — zoals 7 dagen 🛡️
    Het is een goede manier om een persoonlijke deadline te stellen en de cursus af te ronden terwijl je leermomentum hoog is 🚀.

    ![Tokennaam en vervaldatum](../../../translated_images/nl/token-name-expiry-date.a095fb0de6386864.webp)

3. Beperk de scope van het token tot je fork van deze repository.

    ![Scope beperken tot fork repository](../../../translated_images/nl/token_repository_limit.924ade5e11d9d8bb.webp)

4. Beperk de permissies van het token: Onder **Permissions**, klik op het **Account**-tabblad en klik op de knop "+ Add permissions". Er verschijnt een dropdown. Zoek naar **Models** en vink het vakje aan.

    ![Voeg Models-permissie toe](../../../translated_images/nl/add_models_permissions.c0c44ed8b40fc143.webp)

5. Controleer de vereiste permissies voordat je het token genereert. ![Controleer permissies](../../../translated_images/nl/verify_permissions.06bd9e43987a8b21.webp)

6. Zorg ervoor dat je het token op een veilige plaats hebt opgeslagen, zoals een wachtwoordmanager, voordat je het genereert, aangezien het niet opnieuw wordt getoond nadat je het hebt aangemaakt. ![Token veilig opslaan](../../../translated_images/nl/store_token_securely.08ee2274c6ad6caf.webp)

Kopieer je nieuwe token dat je zojuist hebt aangemaakt. Je zult dit nu toevoegen aan je `.env`-bestand dat bij deze cursus is inbegrepen.

### Step 2: Create Your `.env` File

Om je `.env`-bestand te maken, voer het volgende commando uit in je terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dit kopieert het voorbeeldbestand en maakt een `.env` in je map waarin je de waarden voor de omgevingsvariabelen invult.

Met je token gekopieerd, open je het `.env`-bestand in je favoriete teksteditor en plak je je token in het veld `GITHUB_TOKEN`.

![GitHub Token Field](../../../translated_images/nl/github_token_field.20491ed3224b5f4a.webp)

Je zou nu in staat moeten zijn om de codevoorbeelden van deze cursus uit te voeren.

## Set Up for Samples using Microsoft Foundry and Azure AI Agent Service

### Step 1: Retrieve Your Azure Project Endpoint


Volg de stappen om een hub en project te maken in Azure AI Foundry die hier worden beschreven: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Zodra je je project hebt aangemaakt, moet je de verbindingsreeks voor je project ophalen.

Dit kan gedaan worden door naar de **Overview**-pagina van je project te gaan in het Microsoft Foundry-portaal.

![Project Connection String](../../../translated_images/nl/project-endpoint.8cf04c9975bbfbf1.webp)

### Step 2: Create Your `.env` File

Om je `.env`-bestand te maken, voer het volgende commando uit in je terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dit kopieert het voorbeeldbestand en maakt een `.env` in je map waarin je de waarden voor de omgevingsvariabelen invult.

Met je token gekopieerd, open je het `.env`-bestand in je favoriete teksteditor en plak je je token in het veld `PROJECT_ENDPOINT`.

### Step 3: Sign in to Azure

Als best practice voor beveiliging gebruiken we [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) om te authenticeren bij Azure OpenAI met Microsoft Entra ID. 

Open vervolgens een terminal en voer `az login --use-device-code` uit om in te loggen op je Azure-account.

Zodra je bent ingelogd, selecteer je je subscription in de terminal.

## Additional Environment Variables - Azure Search and Azure OpenAI 

Voor de Agentic RAG-les - Les 5 - zijn er voorbeelden die Azure Search en Azure OpenAI gebruiken.

Als je deze voorbeelden wilt uitvoeren, moet je de volgende omgevingsvariabelen aan je `.env`-bestand toevoegen:

### Overview Page (Project)

- `AZURE_SUBSCRIPTION_ID` - Controleer **Project details** op de **Overview**-pagina van je project.

- `AZURE_AI_PROJECT_NAME` - Kijk bovenaan de **Overview**-pagina van je project.

- `AZURE_OPENAI_SERVICE` - Zoek dit in het **Included capabilities**-tabblad voor **Azure OpenAI Service** op de **Overview**-pagina.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - Ga naar **Project properties** op de **Overview**-pagina van het **Management Center**.

- `GLOBAL_LLM_SERVICE` - Onder **Connected resources** vind je de naam van de **Azure AI Services**-verbinding. Als deze niet wordt weergegeven, controleer dan de **Azure portal** onder je resourcegroep voor de naam van de AI Services-resource.

### Models + Endpoints Page

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Selecteer je embedding-model (bijv. `text-embedding-ada-002`) en noteer de **Deployment name** uit de modelgegevens.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Selecteer je chatmodel (bijv. `gpt-4o-mini`) en noteer de **Deployment name** uit de modelgegevens.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - Zoek naar **Azure AI services**, klik erop, ga vervolgens naar **Resource Management**, **Keys and Endpoint**, scrol naar beneden naar de "Azure OpenAI endpoints" en kopieer degene die "Language APIs" zegt.

- `AZURE_OPENAI_API_KEY` - Kopieer van hetzelfde scherm KEY 1 of KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Zoek je **Azure AI Search**-resource, klik erop en bekijk **Overview**.

- `AZURE_SEARCH_API_KEY` - Ga vervolgens naar **Settings** en dan **Keys** om de primaire of secundaire admin-sleutel te kopiëren.

### External Webpage

- `AZURE_OPENAI_API_VERSION` - Bezoek de [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) pagina onder **Latest GA API release**.

### Setup keyless authentication

In plaats van je referenties hardcoded toe te voegen, gebruiken we een keyless-verbinding met Azure OpenAI. Hiervoor importeren we `DefaultAzureCredential` en zullen we later de `DefaultAzureCredential`-functie aanroepen om de credential te verkrijgen.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Stuck Somewhere?
Als je problemen hebt met het uitvoeren van deze setup, kom naar onze <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> of <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">maak een issue aan</a>.

## Volgende les

Je bent nu klaar om de code voor deze cursus uit te voeren. Veel plezier met het verder ontdekken van de wereld van AI-agents! 

[Introductie tot AI-agents en gebruiksscenario's](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vrijwaring**:
Dit document is vertaald met behulp van de AI-vertalingsservice [Co-op Translator](https://github.com/Azure/co-op-translator). Hoewel we naar nauwkeurigheid streven, dient u er rekening mee te houden dat geautomatiseerde vertalingen fouten of onnauwkeurigheden kunnen bevatten. Het originele document in de oorspronkelijke taal moet als de gezaghebbende bron worden beschouwd. Voor cruciale informatie wordt een professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->