# Kursinställning

## Introduktion

Denna lektion går igenom hur man kör kodexemplen i den här kursen.

## Gå med andra deltagare och få hjälp

Innan du börjar klona ditt repo, gå med i [Discord-kanalen för AI Agents For Beginners](https://aka.ms/ai-agents/discord) för att få hjälp med installationen, ställa frågor om kursen eller för att knyta kontakt med andra deltagare.

## Klona eller fork detta repo

För att börja, klona eller forka GitHub-repositoriet. Detta ger dig din egen version av kursmaterialet så att du kan köra, testa och justera koden!

Detta kan göras genom att klicka på länken till <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">forka repot</a>

Du bör nu ha din egen forkade version av den här kursen på följande länk:

![Forkat Repo](../../../translated_images/sv/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (rekommenderat för workshop / Codespaces)

  >Hela repositoriet kan vara stort (~3 GB) om du laddar ner hela historiken och alla filer. Om du bara deltar i workshopen eller bara behöver några lektion-mappar, undviker en shallow clone (eller en sparse clone) det mesta av nedladdningen genom att trunkera historiken och/eller hoppa över blobs.

#### Snabb shallow clone — minimal historik, alla filer

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

To clone only the latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Partial (sparse) clone — minimal blobs + only selected folders

This uses partial clone and sparse-checkout (requires Git 2.25+ and recommended modern Git with partial clone support):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Traverse into the repo folder:

```bash|powershell
cd ai-agents-for-beginners
```

Then specify which folders you want (example below shows two folders):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

After cloning and verifying the files, if you only need files and want to free space (no git history), please delete the repository metadata (💀irreversible — you will lose all Git functionality: no commits, pulls, pushes, or history access).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Använda GitHub Codespaces (rekommenderat för att undvika stora lokala nedladdningar)

- Skapa en ny Codespace för detta repo via [GitHub UI](https://github.com/codespaces).  

- I terminalen i den nyss skapade Codespace, kör ett av shallow/sparse clone-kommandona ovan för att bara ta in de lektionsmappar du behöver i Codespace-arbetsytan.
- Valfritt: efter att ha klonat inne i Codespaces, ta bort .git för att återfå extra utrymme (se borttagningskommandon ovan).
- Obs: Om du föredrar att öppna repot direkt i Codespaces (utan en extra clone), var medveten om att Codespaces kommer att konstruera devcontainer-miljön och kan fortfarande provisionera mer än du behöver. Att klona en shallow-kopia inne i en ny Codespace ger dig bättre kontroll över diskutrymmet.

#### Tips

- Byt alltid ut clone URL:en mot din fork om du vill redigera/commit:a.
- Om du senare behöver mer historik eller filer kan du fetch:a dem eller justera sparse-checkout för att inkludera ytterligare mappar.

## Köra koden

Denna kurs erbjuder en serie Jupyter Notebook-filer som du kan köra för att få praktisk erfarenhet av att bygga AI-agenter.

Kodexemplen använder antingen:

**Kräver GitHub-konto - Gratis**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Märkt som (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Märkt som (autogen.ipynb)

**Kräver Azure-prenumeration**:
3) Azure AI Foundry + Azure AI Agent Service. Märkt som (azureaiagent.ipynb)

Vi uppmuntrar dig att prova alla tre typer av exempel för att se vilken som passar dig bäst.

Vilket alternativ du än väljer kommer avgöra vilka installationssteg du behöver följa nedan:

## Krav

- Python 3.12+
  - **NOTE**: Om du inte har Python 3.12 installerat, se till att installera det. Skapa sedan ditt venv med python3.12 för att säkerställa att rätt versioner installeras från filen requirements.txt.
  
    >Exempel

    Create Python venv directory:

    ```bash|powershell
    python -m venv venv
    ```

    Aktivera sedan venv-miljön för:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: För exempel som använder .NET, se till att du installerar [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) eller senare. Kontrollera sedan din installerade .NET SDK-version:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Ett GitHub-konto - för åtkomst till GitHub Models Marketplace
- Azure-prenumeration - för åtkomst till Microsoft Foundry
- Microsoft Foundry-konto - för åtkomst till Azure AI Agent Service

Vi har inkluderat en `requirements.txt`-fil i roten av detta repo som innehåller alla nödvändiga Python-paket för att köra kodexemplen.

Du kan installera dem genom att köra följande kommando i din terminal i repositoryts rot:

```bash|powershell
pip install -r requirements.txt
```

Vi rekommenderar att skapa en Python-virtuell miljö för att undvika konflikter och problem.

## Konfigurera VSCode

Se till att du använder rätt Python-version i VSCode.

![bild](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Konfigurera för exempel som använder GitHub Models 

### Steg 1: Hämta din GitHub Personal Access Token (PAT)

Denna kurs använder GitHub Models Marketplace som ger gratis åtkomst till stora språkmodeller (LLMs) som du kommer att använda för att bygga AI-agenter.

För att använda GitHub Models måste du skapa en [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Detta kan göras genom att gå till dina <a href="https://github.com/settings/personal-access-tokens" target="_blank">Inställningar för personliga åtkomsttoken</a> i ditt GitHub-konto.

Följ [Principen om minsta privilegium](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) när du skapar din token. Det innebär att du endast bör ge token de behörigheter som behövs för att köra kodexemplen i denna kurs.

1. Välj alternativet `Fine-grained tokens` på vänstra sidan av din skärm genom att gå till **Developer settings**

   ![Utvecklarinställningar](../../../translated_images/sv/profile_developer_settings.410a859fe749c755.webp)

   Välj sedan `Generate new token`.

   ![Generera ny token](../../../translated_images/sv/fga_new_token.1c1a234afe202ab3.webp)

2. Ange ett beskrivande namn för din token som återspeglar dess syfte, så att det är lätt att identifiera senare.

    🔐 Rekommendation för token-varaktighet

    Rekommenderad varaktighet: 30 dagar
    För en säkrare inställning kan du välja en kortare period—till exempel 7 dagar 🛡️
    Det är ett bra sätt att sätta ett personligt mål och slutföra kursen medan din inlärningsmomentum är hög 🚀.

    ![Token-namn och utgångsdatum](../../../translated_images/sv/token-name-expiry-date.a095fb0de6386864.webp)

3. Begränsa tokenens omfattning till din fork av detta repository.

    ![Begränsa omfattningen till fork repository](../../../translated_images/sv/token_repository_limit.924ade5e11d9d8bb.webp)

4. Begränsa tokenens behörigheter: Under **Permissions**, klicka på fliken **Account**, och klicka på knappen "+ Add permissions". En rullgardinsmeny visas. Sök efter **Models** och markera kryssrutan för den.

    ![Lägg till Models-behörighet](../../../translated_images/sv/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verifiera de behörigheter som krävs innan du genererar token. ![Verifiera behörigheter](../../../translated_images/sv/verify_permissions.06bd9e43987a8b21.webp)

6. Innan du genererar token, se till att du är redo att lagra token på en säker plats som ett lösenordshanterarvalv, eftersom den inte visas igen efter att du skapat den. ![Spara token säkert](../../../translated_images/sv/store_token_securely.08ee2274c6ad6caf.webp)

Kopiera din nya token som du just skapat. Du kommer nu lägga till denna i din `.env`-fil som ingår i denna kurs.

### Steg 2: Skapa din `.env`-fil

För att skapa din `.env`-fil, kör följande kommando i din terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Detta kopierar exempel-filen och skapar en `.env` i din katalog där du fyller i värdena för miljövariablerna.

När du kopierat din token, öppna `.env`-filen i din favorittextredigerare och klistra in din token i fältet `GITHUB_TOKEN`.

![GitHub tokenfält](../../../translated_images/sv/github_token_field.20491ed3224b5f4a.webp)

Du bör nu kunna köra kodexemplen i denna kurs.

## Konfigurera för exempel som använder Microsoft Foundry och Azure AI Agent Service

### Steg 1: Hämta din Azure projektendpoint


Följ stegen för att skapa ett hubb och projekt i Azure AI Foundry som finns här: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


När du har skapat ditt projekt måste du hämta anslutningssträngen för ditt projekt.

Detta kan göras genom att gå till **Overview**-sidan för ditt projekt i Microsoft Foundry-portalen.

![Projekts anslutningssträng](../../../translated_images/sv/project-endpoint.8cf04c9975bbfbf1.webp)

### Steg 2: Skapa din `.env`-fil

För att skapa din `.env`-fil, kör följande kommando i din terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Detta kopierar exempel-filen och skapar en `.env` i din katalog där du fyller i värdena för miljövariablerna.

När du kopierat din token, öppna `.env`-filen i din favorittextredigerare och klistra in din token i fältet `PROJECT_ENDPOINT`.

### Steg 3: Logga in på Azure

Som en säkerhetsmässig best practice kommer vi att använda [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) för att autentisera mot Azure OpenAI med Microsoft Entra ID. 

Öppna sedan en terminal och kör `az login --use-device-code` för att logga in på ditt Azure-konto.

När du har loggat in, välj din prenumeration i terminalen.

## Ytterligare miljövariabler - Azure Search och Azure OpenAI 

För Agentic RAG-lektionen - Lektion 5 - finns exempel som använder Azure Search och Azure OpenAI.

Om du vill köra dessa exempel måste du lägga till följande miljövariabler i din `.env`-fil:

### Översiktssida (projekt)

- `AZURE_SUBSCRIPTION_ID` - Kontrollera **Project details** på **Overview**-sidan för ditt projekt.

- `AZURE_AI_PROJECT_NAME` - Titta längst upp på **Overview**-sidan för ditt projekt.

- `AZURE_OPENAI_SERVICE` - Hitta detta under fliken **Included capabilities** för **Azure OpenAI Service** på **Overview**-sidan.

### Management Center

- `AZURE_OPENAI_RESOURCE_GROUP` - Gå till **Project properties** på **Overview**-sidan i **Management Center**.

- `GLOBAL_LLM_SERVICE` - Under **Connected resources**, hitta anslutningsnamnet för **Azure AI Services**. Om det inte finns, kontrollera **Azure portal** under din resursgrupp för AI Services-resursens namn.

### Models + Endpoints Page

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Välj din embedding-modell (t.ex. `text-embedding-ada-002`) och notera **Deployment name** från modellens detaljer.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Välj din chattmodell (t.ex. `gpt-4o-mini`) och notera **Deployment name** från modellens detaljer.

### Azure-portalen

- `AZURE_OPENAI_ENDPOINT` - Leta efter **Azure AI services**, klicka på den, gå sedan till **Resource Management**, **Keys and Endpoint**, scrolla ner till "Azure OpenAI endpoints" och kopiera den som säger "Language APIs".

- `AZURE_OPENAI_API_KEY` - Från samma skärm, kopiera KEY 1 eller KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Hitta din **Azure AI Search**-resurs, klicka på den och se **Overview**.

- `AZURE_SEARCH_API_KEY` - Gå sedan till **Settings** och därefter **Keys** för att kopiera den primära eller sekundära adminnyckeln.

### Extern webbsida

- `AZURE_OPENAI_API_VERSION` - Besök sidan [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) under **Latest GA API release**.

### Ställ in keyless-autentisering

Istället för att hårdkoda dina uppgifter kommer vi att använda en keyless-anslutning med Azure OpenAI. För att göra detta importerar vi `DefaultAzureCredential` och anropar senare funktionen `DefaultAzureCredential` för att få credential.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Fastnat någonstans?
Om du har problem med att köra den här uppsättningen, hoppa in i vår <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> eller <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">skapa ett ärende</a>.

## Nästa lektion

Du är nu redo att köra koden för den här kursen. Lycka till med att lära dig mer om världen av AI-agenter! 

[Introduktion till AI-agenter och användningsfall](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfriskrivning**:
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Vi strävar efter noggrannhet, men var medveten om att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på sitt ursprungliga språk bör betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår till följd av användningen av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->