# Kursusopsætning

## Introduktion

Denne lektion forklarer, hvordan man kører kodeeksemplerne i dette kursus.

## Deltag med andre lærende og få hjælp

Før du begynder at klone dit repo, tilslut dig [AI Agents For Beginners Discord-kanal](https://aka.ms/ai-agents/discord) for at få hjælp til opsætning, stille spørgsmål om kurset eller forbinde dig med andre kursister.

## Klon eller fork dette repo

For at begynde skal du klone eller fork'e GitHub-repositoriet. Dette opretter din egen version af kursusmaterialet, så du kan køre, teste og tilpasse koden!

Dette kan gøres ved at klikke på linket til <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">opret en fork af repoet</a>

Du bør nu have din egen forkede version af dette kursus på følgende link:

![Forket repo](../../../translated_images/da/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (anbefales til workshop / Codespaces)

  >Hele repositoriet kan være stort (~3 GB), hvis du downloader hele historikken og alle filer. Hvis du kun deltager i workshoppen eller kun har brug for et par lektion-mapper, så undgår en shallow-klon (eller en sparse-klon) størstedelen af downloadet ved at afkorte historikken og/eller springe blobber over.

#### Hurtig shallow-klon — minimal historik, alle filer

Erstat `<your-username>` i kommandoerne nedenfor med din fork URL (eller upstream URL, hvis du foretrækker det).

For kun at klone den seneste commit-historik (lille download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

For at klone en specifik branche:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Delvis (sparse) klon — minimale blobs + kun udvalgte mapper

Dette bruger partial clone og sparse-checkout (kræver Git 2.25+ og anbefales at bruge en moderne Git med partial clone-understøttelse):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Gå ind i repomappen:

```bash|powershell
cd ai-agents-for-beginners
```

Angiv derefter hvilke mapper du ønsker (eksemplet nedenfor viser to mapper):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Efter kloning og verifikation af filerne, hvis du kun har brug for filerne og ønsker at frigøre plads (ingen git-historik), så slet venligst repository-metadaten (💀irreversibelt — du mister al Git-funktionalitet: ingen commits, pulls, pushes eller adgang til historik).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Brug af GitHub Codespaces (anbefales for at undgå store lokale downloads)

- Opret en ny Codespace for dette repo via [GitHub UI](https://github.com/codespaces).  

- I terminalen i den nyoprettede Codespace, kør en af shallow/sparse-clone-kommandoerne ovenfor for kun at hente de lektion-mapper, du har brug for ind i Codespace-workspacet.
- Valgfrit: efter kloning inde i Codespaces, fjern .git for at frigive ekstra plads (se sletningskommandoerne ovenfor).
- Bemærk: Hvis du foretrækker at åbne repoet direkte i Codespaces (uden en ekstra klon), så vær opmærksom på, at Codespaces vil bygge devcontainer-miljøet og stadig kan provisionere mere, end du har brug for. At klone en shallow-kopi inde i en frisk Codespace giver dig mere kontrol over diskforbruget.

#### Tips

- Erstat altid clone-URL'en med din fork, hvis du ønsker at redigere/committe.
- Hvis du senere får brug for mere historik eller flere filer, kan du hente dem eller justere sparse-checkout for at inkludere yderligere mapper.

## Kørsel af koden

Dette kursus tilbyder en række Jupyter-notebooks, som du kan køre for at få praktisk erfaring med at bygge AI-agenter.

Kodeeksemplerne bruger enten:

**Kræver GitHub-konto - Gratis**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Mærket som (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Mærket som (autogen.ipynb)

**Kræver Azure-abonnement**:
3) Azure AI Foundry + Azure AI Agent Service. Mærket som (azureaiagent.ipynb)

Vi opfordrer dig til at prøve alle tre typer eksempler for at finde ud af, hvilken der fungerer bedst for dig.

Uanset hvilken mulighed du vælger, vil det afgøre, hvilke opsætningstrin du skal følge nedenfor:

## Krav

- Python 3.12+
  - **BEMÆRK**: Hvis du ikke har Python3.12 installeret, skal du sørge for at installere det. Opret derefter dit venv ved hjælp af python3.12 for at sikre, at de korrekte versioner installeres fra requirements.txt-filen.
  
    >Eksempel

    Opret Python venv-mappe:

    ```bash|powershell
    python -m venv venv
    ```

    Aktivér derefter venv-miljøet for:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: For samplekoderne, der bruger .NET, skal du sikre, at du installerer [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) eller nyere. Tjek derefter din installerede .NET SDK-version:

    ```bash|powershell
    dotnet --list-sdks
    ```

- En GitHub-konto - For adgang til GitHub Models Marketplace
- Azure-abonnement - For adgang til Microsoft Foundry
- Microsoft Foundry-konto - For adgang til Azure AI Agent Service

Vi har inkluderet en `requirements.txt`-fil i roden af dette repository, som indeholder alle nødvendige Python-pakker for at køre kodeeksemplerne.

Du kan installere dem ved at køre følgende kommando i din terminal i roden af repositoriet:

```bash|powershell
pip install -r requirements.txt
```

Vi anbefaler at oprette et Python-virtuelt miljø for at undgå konflikter og problemer.

## Opsæt VSCode

Sørg for, at du bruger den rigtige version af Python i VSCode.

![billede](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Opsætning for eksempler, der bruger GitHub Models 

### Trin 1: Hent din GitHub Personal Access Token (PAT)

Dette kursus bruger GitHub Models Marketplace, som giver gratis adgang til store sprogmodeller (LLMs), som du vil bruge til at bygge AI-agenter.

For at bruge GitHub Models skal du oprette en [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Dette kan gøres ved at gå til dine <a href="https://github.com/settings/personal-access-tokens" target="_blank">Indstillinger for personlige adgangstokens</a> i din GitHub-konto.

Følg venligst [Principle of Least Privilege](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) når du opretter din token. Det betyder, at du kun bør give tokenen de tilladelser, den har brug for for at køre kodeeksemplerne i dette kursus.

1. Vælg `Fine-grained tokens`-muligheden i venstre side af din skærm ved at gå til **Udviklerindstillinger**

   ![Udviklerindstillinger](../../../translated_images/da/profile_developer_settings.410a859fe749c755.webp)

   Vælg derefter `Generer ny token`.

   ![Generer token](../../../translated_images/da/fga_new_token.1c1a234afe202ab3.webp)

2. Indtast et beskrivende navn for din token, der afspejler dens formål, så det er nemt at genkende senere.

    🔐 Anbefalet token-varighed

    Anbefalet varighed: 30 dage
    For en mere sikker tilgang kan du vælge en kortere periode — f.eks. 7 dage 🛡️
    Det er en god måde at sætte et personligt mål og gennemføre kurset, mens dit læringsmomentum er højt 🚀.

    ![Tokennavn og udløb](../../../translated_images/da/token-name-expiry-date.a095fb0de6386864.webp)

3. Begræns tokenens omfang til din fork af dette repository.

    ![Begræns omfang til fork af repositoryet](../../../translated_images/da/token_repository_limit.924ade5e11d9d8bb.webp)

4. Begræns tokenens tilladelser: Under **Permissions** klik på fanen **Account**, og klik på knappen "+ Add permissions". En dropdown vises. Søg efter **Models** og sæt flueben ved den.

    ![Tilføj Models-tilladelse](../../../translated_images/da/add_models_permissions.c0c44ed8b40fc143.webp)

5. Bekræft de nødvendige tilladelser, før du genererer tokenen. ![Bekræft tilladelser](../../../translated_images/da/verify_permissions.06bd9e43987a8b21.webp)

6. Inden du genererer tokenen, sørg for, at du er klar til at gemme tokenen et sikkert sted, f.eks. i en password manager, da den ikke vil blive vist igen efter oprettelsen. ![Gem token sikkert](../../../translated_images/da/store_token_securely.08ee2274c6ad6caf.webp)

Kopier din nye token, som du lige har oprettet. Du vil nu tilføje denne til din `.env`-fil, der er inkluderet i dette kursus.

### Trin 2: Opret din `.env`-fil

For at oprette din `.env`-fil skal du køre følgende kommando i din terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dette vil kopiere eksempel-filen og oprette en `.env` i din mappe, hvor du udfylder værdierne for miljøvariablerne.

Når du har kopieret din token, åbn `.env`-filen i din foretrukne teksteditor og indsæt din token i `GITHUB_TOKEN`-feltet.

![GitHub-tokenfelt](../../../translated_images/da/github_token_field.20491ed3224b5f4a.webp)

Du bør nu kunne køre kodeeksemplerne i dette kursus.

## Opsætning for eksempler, der bruger Microsoft Foundry og Azure AI Agent Service

### Trin 1: Hent dit Azure-projekt-endpoint


Følg trinnene til at oprette en hub og et projekt i Azure AI Foundry her: [Oversigt over hub-ressourcer](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Når du har oprettet dit projekt, skal du hente forbindelsesstrengen til dit projekt.

Dette kan gøres ved at gå til oversigtssiden for dit projekt i Microsoft Foundry-portalen.

![Projektforbindelsesstreng](../../../translated_images/da/project-endpoint.8cf04c9975bbfbf1.webp)

### Trin 2: Opret din `.env`-fil

For at oprette din `.env`-fil skal du køre følgende kommando i din terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Dette vil kopiere eksempel-filen og oprette en `.env` i din mappe, hvor du udfylder værdierne for miljøvariablerne.

Når du har kopieret din token, åbn `.env`-filen i din foretrukne teksteditor og indsæt din token i `PROJECT_ENDPOINT`-feltet.

### Trin 3: Log ind på Azure

Som en bedste praksis for sikkerhed vil vi bruge [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) til at autentificere mod Azure OpenAI med Microsoft Entra ID. 

Åbn herefter en terminal og kør `az login --use-device-code` for at logge ind på din Azure-konto.

Når du er logget ind, vælg dit abonnement i terminalen.

## Yderligere miljøvariabler - Azure Search og Azure OpenAI 

For Agentic RAG-lektionen - Lektion 5 - er der eksempler, der bruger Azure Search og Azure OpenAI.

Hvis du vil køre disse eksempler, skal du tilføje følgende miljøvariabler til din `.env`-fil:

### Oversigtsside (Projekt)

- `AZURE_SUBSCRIPTION_ID` - Tjek **Projektdetaljer** på **Oversigt**-siden for dit projekt.

- `AZURE_AI_PROJECT_NAME` - Se øverst på **Oversigt**-siden for dit projekt.

- `AZURE_OPENAI_SERVICE` - Find dette under fanen **Included capabilities** for **Azure OpenAI Service** på **Oversigt**-siden.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - Gå til **Project properties** på **Oversigt**-siden for **Management Center**.

- `GLOBAL_LLM_SERVICE` - Under **Connected resources** finder du navnet på forbindelsen **Azure AI Services**. Hvis det ikke er angivet, så tjek **Azure-portalen** under din resource group for navnet på AI Services-ressourcen.

### Models + Endpoints-side

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Vælg din embedding-model (f.eks. `text-embedding-ada-002`) og noter **Deployment name** fra modeloplysningerne.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Vælg din chat-model (f.eks. `gpt-4o-mini`) og noter **Deployment name** fra modeloplysningerne.

### Azure-portalen

- `AZURE_OPENAI_ENDPOINT` - Find **Azure AI services**, klik på det, gå til **Resource Management**, **Keys and Endpoint**, rul ned til "Azure OpenAI endpoints", og kopier den, der siger "Language APIs".

- `AZURE_OPENAI_API_KEY` - Fra samme skærm, kopier KEY 1 eller KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Find din **Azure AI Search**-ressource, klik på den, og se **Oversigt**.

- `AZURE_SEARCH_API_KEY` - Gå derefter til **Settings** og derefter **Keys** for at kopiere den primære eller sekundære admin-nøgle.

### Ekstern webside

- `AZURE_OPENAI_API_VERSION` - Besøg siden for [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) under **Latest GA API release**.

### Opsætning af nøglefri autentificering

I stedet for at hardcode dine legitimationsoplysninger, vil vi bruge en nøglefri forbindelse med Azure OpenAI. For at gøre det importerer vi `DefaultAzureCredential` og kalder senere `DefaultAzureCredential`-funktionen for at få legitimationsoplysningerne.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Står du fast et sted?
Hvis du har problemer med at køre denne opsætning, så hop ind i vores <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> eller <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">opret en issue</a>.

## Næste lektion

Du er nu klar til at køre koden til dette kursus. God fornøjelse med at lære mere om verdenen af AI-agenter! 

[Introduktion til AI-agenter og anvendelsestilfælde](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfraskrivelse:
Dette dokument er blevet oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi bestræber os på nøjagtighed, bedes du være opmærksom på, at automatiske oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets modersmål bør betragtes som den autoritative kilde. For kritisk information anbefales en professionel menneskelig oversættelse. Vi er ikke ansvarlige for eventuelle misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->