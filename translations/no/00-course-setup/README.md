# Course Setup

## Introduksjon

Denne leksjonen dekker hvordan du kjører kodeeksemplene i dette kurset.

## Bli med andre elever og få hjelp

Før du begynner å klone ditt repo, bli med i [AI Agents For Beginners Discord-kanalen](https://aka.ms/ai-agents/discord) for å få hjelp med oppsett, spørsmål om kurset, eller for å koble til andre elever.

## Klon eller Fork dette Repoet

For å starte, vennligst klon eller fork GitHub-repositoryet. Dette vil lage din egen versjon av kursmaterialet slik at du kan kjøre, teste og endre koden!

Dette kan gjøres ved å klikke på linken til <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fork repoet</a>.

Du skal nå ha din egen forkede versjon av dette kurset på følgende link:

![Forked Repo](../../../translated_images/no/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (anbefalt for workshop / Codespaces)

  >Det fullstendige repositoryet kan være stort (~3 GB) når du laster ned full historikk og alle filer. Hvis du kun deltar på workshoppen eller bare trenger noen få leksjonsmapper, unngår en shallow clone (eller en sparse clone) det meste av nedlastingen ved å kutte historikken og/eller hoppe over blobs.

#### Rask shallow clone – minimal historikk, alle filer

Bytt ut `<your-username>` i kommandoene nedenfor med din fork URL (eller upstream URL hvis du foretrekker det).

For å klone bare den siste commit-historikken (liten nedlasting):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

For å klone en spesifikk branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Delvis (sparse) clone – minimale blobs + kun valgte mapper

Dette bruker delvis kloning og sparse-checkout (krever Git 2.25+ og anbefales moderne Git med støtte for delvis kloning):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Gå inn i repo-mappen:

```bash|powershell
cd ai-agents-for-beginners
```

Spesifiser så hvilke mapper du vil ha (eksemplet nedenfor viser to mapper):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Etter å ha klonet og verifisert filene, hvis du kun trenger filene og ønsker å frigjøre plass (ingen git-historikk), slett repository metadata (💀irreversibelt – du mister all Git-funksjonalitet: ingen commits, pulls, pushes eller historikk-tilgang).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Bruke GitHub Codespaces (anbefalt for å unngå store lokale nedlastinger)

- Opprett en ny Codespace for dette repoet via [GitHub UI](https://github.com/codespaces).  

- I terminalen i den nylig opprettede codespacen, kjør en av shallow/sparse clone-kommandoene ovenfor for å hente kun de leksjonsmappene du trenger inn i Codespace-arbeidsområdet.
- Valgfritt: etter kloning i Codespaces, fjern .git for å frigjøre plass (se fjerningskommandoene ovenfor).
- Merk: Hvis du foretrekker å åpne repoet direkte i Codespaces (uten ekstra kloning), vær oppmerksom på at Codespaces vil bygge devcontainer-miljøet og kan fortsatt sette opp mer enn du trenger. Å klone en shallow kopi inne i en fersk Codespace gir deg mer kontroll over diskbruk.

#### Tips

- Bytt alltid ut clone-URL med din fork hvis du ønsker å redigere/commit.
- Hvis du senere trenger mer historikk eller filer, kan du hente dem eller justere sparse-checkout for å inkludere flere mapper.

## Kjøre Koden

Dette kurset tilbyr en serie Jupyter Notebooks som du kan bruke for å få praktisk erfaring med å bygge AI-agenter.

Kodeeksemplene bruker enten:

**Krever GitHub-konto – Gratis**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Merket som (semantic-kernel.ipynb)  
2) AutoGen Framework + GitHub Models Marketplace. Merket som (autogen.ipynb)

**Krever Azure-abonnement**:  
3) Azure AI Foundry + Azure AI Agent Service. Merket som (azureaiagent.ipynb)

Vi oppfordrer deg til å prøve alle tre typene eksempler for å se hva som fungerer best for deg.

Hvilket som helst alternativ du velger, avgjør hvilke oppsettssteg du må følge nedenfor:

## Krav

- Python 3.12+  
  - **MERK**: Hvis du ikke har Python3.12 installert, sørg for å installere det. Opprett deretter ditt virtuelle miljø ved å bruke python3.12 for å sikre at riktige versjoner installeres fra requirements.txt-filen.

    >Eksempel

    Opprett Python venv-mappe:

    ```bash|powershell
    python -m venv venv
    ```

    Aktiver deretter venv-miljø for:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: For eksempel-kodene som bruker .NET, sørg for å installere [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) eller nyere. Sjekk deretter installert .NET SDK-versjon:

    ```bash|powershell
    dotnet --list-sdks
    ```

- En GitHub-konto – for tilgang til GitHub Models Marketplace  
- Azure-abonnement – for tilgang til Microsoft Foundry  
- Microsoft Foundry-konto – for tilgang til Azure AI Agent Service  

Vi har inkludert en `requirements.txt`-fil i rotmappen av dette repositoryet med alle nødvendige Python-pakker for å kjøre kodeeksemplene.

Du kan installere dem ved å kjøre følgende kommando i terminalen i rotmappen:

```bash|powershell
pip install -r requirements.txt
```

Vi anbefaler å opprette et Python virtuelt miljø for å unngå konflikter og problemer.

## Sett opp VSCode

Sørg for at du bruker riktig versjon av Python i VSCode.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Oppsett for Eksempler som bruker GitHub Models

### Steg 1: Hent din GitHub Personal Access Token (PAT)

Dette kurset benytter GitHub Models Marketplace, som gir gratis tilgang til store språkmodeller (LLMs) som du vil bruke til å bygge AI-agenter.

For å bruke GitHub Models må du opprette en [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Dette kan gjøres ved å gå til dine <a href="https://github.com/settings/personal-access-tokens" target="_blank">Personal Access Tokens-innstillinger</a> i GitHub-kontoen din.

Vennligst følg [Prinsippet om minste privilegium](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) når du oppretter tokenen. Det betyr at du kun skal gi tokenen de tillatelsene som trengs for å kjøre kodeeksemplene i dette kurset.

1. Velg `Fine-grained tokens`-alternativet på venstre side av skjermen ved å gå til **Developer settings**

   ![Developer settings](../../../translated_images/no/profile_developer_settings.410a859fe749c755.webp)

   Velg deretter `Generate new token`.

   ![Generate Token](../../../translated_images/no/fga_new_token.1c1a234afe202ab3.webp)

2. Skriv inn et beskrivende navn for tokenet som gjenspeiler formålet, slik at det er lett å identifisere senere.

    🔐 Anbefalt varighet for token

    Anbefalt varighet: 30 dager  
    For en mer sikker holdning kan du velge kortere periode — for eksempel 7 dager 🛡️  
    Det er en fin måte å sette et personlig mål og fullføre kurset mens læringsmomentumet er høyt 🚀.

    ![Token Name and Expiration](../../../translated_images/no/token-name-expiry-date.a095fb0de6386864.webp)

3. Begrens tokenets omfang til din fork av dette repositoryet.

    ![Limit scope to fork repository](../../../translated_images/no/token_repository_limit.924ade5e11d9d8bb.webp)

4. Begrens tokenets tillatelser: Under **Permissions**, klikk på **Account**-fanen, og klikk "+ Add permissions"-knappen. En nedtrekksmeny dukker opp. Søk etter **Models** og huk av for det.

    ![Add Models Permission](../../../translated_images/no/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verifiser nødvendige tillatelser før du genererer tokenet. ![Verify Permissions](../../../translated_images/no/verify_permissions.06bd9e43987a8b21.webp)

6. Før du genererer tokenet, sørg for at du er klar til å lagre tokenet på et sikkert sted som i en passordbehandler, da det ikke vil vises igjen etter opprettelsen. ![Store Token Securely](../../../translated_images/no/store_token_securely.08ee2274c6ad6caf.webp)

Kopier ditt nye token som du nettopp har opprettet. Du skal nå legge dette inn i din `.env`-fil som følger med kurset.

### Steg 2: Opprett din `.env`-fil

For å lage `.env`-filen, kjør følgende kommando i terminalen.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dette kopierer eksempel-filen og oppretter en `.env` i katalogen din hvor du fyller inn verdiene for miljøvariablene.

Med token kopiert, åpne `.env`-filen i din favoritt teksteditor og lim inn token i `GITHUB_TOKEN`-feltet.

![GitHub Token Field](../../../translated_images/no/github_token_field.20491ed3224b5f4a.webp)

Du skal nå kunne kjøre kodeeksemplene i dette kurset.

## Oppsett for Eksempler som bruker Microsoft Foundry og Azure AI Agent Service

### Steg 1: Hent sluttpunktet for ditt Azure-prosjekt

Følg stegene for å opprette et hub og prosjekt i Azure AI Foundry her: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

Når du har opprettet prosjektet, må du hente tilkoblingsstrengen for prosjektet.

Dette gjøres ved å gå til **Oversikt**-siden for prosjektet i Microsoft Foundry-portalen.

![Project Connection String](../../../translated_images/no/project-endpoint.8cf04c9975bbfbf1.webp)

### Steg 2: Opprett din `.env`-fil

For å lage `.env`-filen, kjør følgende kommando i terminalen.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dette kopierer eksempel-filen og oppretter en `.env` i katalogen din hvor du fyller inn verdiene for miljøvariablene.

Med token kopiert, åpne `.env`-filen i din favoritt teksteditor og lim inn token i `PROJECT_ENDPOINT`-feltet.

### Steg 3: Logg inn på Azure

Som en sikkerhetsgod praksis skal vi bruke [nøkkelfri autentisering](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) for å autentisere mot Azure OpenAI med Microsoft Entra ID.

Åpne deretter en terminal og kjør `az login --use-device-code` for å logge på Azure-kontoen din.

Når du er logget inn, velg abonnement i terminalen.

## Ytterligere miljøvariabler – Azure Search og Azure OpenAI

For Agentic RAG-leksjonen – Leksjon 5 – finnes det eksempler som bruker Azure Search og Azure OpenAI.

Hvis du ønsker å kjøre disse eksemplene, må du legge til følgende miljøvariabler i din `.env`-fil:

### Oversiktsside (Prosjekt)

- `AZURE_SUBSCRIPTION_ID` – Sjekk **Prosjektdetaljer** på **Oversikt**-siden for prosjektet.

- `AZURE_AI_PROJECT_NAME` – Se øverst på **Oversikt**-siden for prosjektet.

- `AZURE_OPENAI_SERVICE` – Finn dette under **Included capabilities** fanen for **Azure OpenAI Service** på **Oversikt**-siden.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` – Gå til **Prosjektegenskaper** på **Oversikt**-siden i **Management Center**.

- `GLOBAL_LLM_SERVICE` – Under **Connected resources**, finn navnet på tilkoblingen for **Azure AI Services**. Hvis ikke oppført, sjekk i **Azure-portalen** under resource group for AI Services ressursnavn.

### Models + Endpoints-side

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` – Velg embedding-modellen (f.eks. `text-embedding-ada-002`) og notér **Deployment name** i modell-detaljene.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` – Velg chat-modellen (f.eks. `gpt-4o-mini`) og notér **Deployment name** i modell-detaljene.

### Azure-portalen

- `AZURE_OPENAI_ENDPOINT` – Finn **Azure AI services**, klikk på den, gå deretter til **Resource Management**, **Keys and Endpoint**, scroll ned til "Azure OpenAI endpoints" og kopier den som sier "Language APIs".

- `AZURE_OPENAI_API_KEY` – Fra samme side, kopier KEY 1 eller KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` – Finn din **Azure AI Search**-ressurs, klikk på den og se **Oversikt**.

- `AZURE_SEARCH_API_KEY` – Gå deretter til **Settings** og så **Keys** for å kopiere primær eller sekundær admin-nøkkel.

### Ekstern webside

- `AZURE_OPENAI_API_VERSION` – Besøk [API versjons livssyklus](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) siden under **Latest GA API release**.

### Sett opp nøkkelfri autentisering

I stedet for å hardkode legitimasjonene dine, bruker vi en nøkkelfri tilkobling med Azure OpenAI. Vi importerer `DefaultAzureCredential` og kaller senere `DefaultAzureCredential`-funksjonen for å hente legitimasjonen.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Sitter fast et sted?
Hvis du har noen problemer med å kjøre denne oppsettet, bli med i vår <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> eller <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">opprett en sak</a>.

## Neste leksjon

Du er nå klar til å kjøre koden for dette kurset. Lykke til med å lære mer om verdenen til AI-agenter!

[Introduksjon til AI-agenter og agentbrukstilfeller](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokumentet er oversatt ved hjelp av AI-oversettelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selv om vi streber etter nøyaktighet, vennligst vær oppmerksom på at automatiserte oversettelser kan inneholde feil eller unøyaktigheter. Det opprinnelige dokumentet på originalspråket bør betraktes som den autoritative kilden. For kritisk informasjon anbefales profesjonell menneskelig oversettelse. Vi er ikke ansvarlige for eventuelle misforståelser eller feiltolkninger som oppstår ved bruk av denne oversettelsen.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->