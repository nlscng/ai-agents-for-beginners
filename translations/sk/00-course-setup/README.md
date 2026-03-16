# Nastavenie kurzu

## Úvod

Táto lekcia pokryje, ako spustiť ukážky kódu z tohto kurzu.

## Pridajte sa k ostatným účastníkom a získajte pomoc

Predtým, než začnete klonovať svoj repozitár, pripojte sa k [kanálu Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord), aby ste získali pomoc pri nastavení, odpovede na otázky o kurze alebo sa spojili s ostatnými študentmi.

## Klonovanie alebo forkovanie tohto repozitára

Na začiatok, prosím, sklonujte alebo forknite GitHub repozitár. Tým si vytvoríte vlastnú verziu materiálov kurzu, aby ste mohli kód spúšťať, testovať a upravovať!

Toto môžete urobiť kliknutím na odkaz <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">vytvoriť fork repozitára</a>

Teraz by ste mali mať vlastnú forknutú verziu tohto kurzu na nasledujúcom odkaze:

![Forknutý repozitár](../../../translated_images/sk/forked-repo.33f27ca1901baa6a.webp)

### Povrchový klon (odporúčané pre workshop / Codespaces)

  > Celý repozitár môže byť veľký (~3 GB), ak si stiahnete celú históriu a všetky súbory. Ak sa zúčastňujete len workshopu alebo potrebujete len niekoľko priečinkov s lekciami, povrchový klon (alebo sparse klon) sa vyhne veľkej časti tohto sťahovania orezaním histórie a/alebo preskočením blobov.

#### Rýchly povrchový klon — minimálna história, všetky súbory

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

To clone only the latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Čiastočný (sparse) klon — minimálne bloby + iba vybrané priečinky

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

#### Používanie GitHub Codespaces (odporúčané, aby ste sa vyhli veľkým lokálnym stiahnutiam)

- Vytvorte nový Codespace pre tento repozitár cez [GitHub UI](https://github.com/codespaces).  

- V termináli novo vytvoreného Codespace spustite jeden z vyššie uvedených shallow/sparse klonovacích príkazov, aby ste do pracovného priestoru Codespace priniesli len priečinky s lekciami, ktoré potrebujete.
- Voliteľné: po klonovaní v Codespaces odstráňte .git, aby ste získali miesto (pozrite si príkazy na odstránenie vyššie).
- Poznámka: Ak uprednostňujete otvorenie repozitára priamo v Codespaces (bez ďalšieho klonovania), buďte si vedomí, že Codespaces zostaví devcontainer prostredie a môže stále zabezpečiť viac, než potrebujete. Klonovanie povrchovej kópie v novom Codespace vám dá väčšiu kontrolu nad využitím disku.

#### Tipy

- Vždy nahraďte URL klonu URL vášho forku, ak chcete upravovať/commitovať.
- Ak neskôr potrebujete viac histórie alebo súborov, môžete ich stiahnuť (fetch) alebo upraviť sparse-checkout, aby ste zahrnuli ďalšie priečinky.

## Spúšťanie kódu

Tento kurz ponúka sériu Jupyter notebookov, ktoré môžete spustiť, aby ste získali praktické skúsenosti s tvorbou AI agentov.

Ukážky kódu používajú buď:

**Vyžaduje účet GitHub - zadarmo**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Označené ako (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Označené ako (autogen.ipynb)

**Vyžaduje predplatné Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Označené ako (azureaiagent.ipynb)

Odporúčame vyskúšať všetky tri typy príkladov, aby ste zistili, ktorý vám najviac vyhovuje.

Ktorejkoľvek možnosti sa rozhodnete, určí to, ktoré kroky nastavenia musíte nasledovať nižšie:

## Požiadavky

- Python 3.12+
  - **NOTE**: If you don't have Python3.12 installed, ensure you install it.  Then create your venv using python3.12 to ensure the correct versions are installed from the requirements.txt file.
  
    >Príklad

    Vytvorte adresár pre Python venv:

    ```bash|powershell
    python -m venv venv
    ```

    Potom aktivujte venv pre:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: For the sample codes using .NET, ensure you install [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) or later. Then, check your installed .NET SDK version:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Účet GitHub - na prístup do GitHub Models Marketplace
- Predplatné Azure - na prístup k Microsoft Foundry
- Účet Microsoft Foundry - na prístup k Azure AI Agent Service

Do koreňa tohto repozitára sme priložili súbor `requirements.txt`, ktorý obsahuje všetky potrebné Python balíky na spustenie ukážok kódu.

Môžete ich nainštalovať spustením nasledujúceho príkazu v termináli v koreňovom adresári repozitára:

```bash|powershell
pip install -r requirements.txt
```

Odporúčame vytvoriť virtuálne prostredie Python, aby ste sa vyhli konfliktom a problémom.

## Nastavenie VSCode

Uistite sa, že vo VSCode používate správnu verziu Pythonu.

![obrázok](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Nastavenie pre ukážky používajúce GitHub Models 

### Krok 1: Získajte svoj GitHub Personal Access Token (PAT)

Tento kurz využíva GitHub Models Marketplace, ktorý poskytuje bezplatný prístup k veľkým jazykovým modelom (LLM), ktoré budete používať na tvorbu AI agentov.

Ak chcete používať GitHub Models, budete si musieť vytvoriť [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Toto môžete urobiť prechodom do <a href="https://github.com/settings/personal-access-tokens" target="_blank">Nastavenia osobných prístupových tokenov</a> vo vašom GitHub účte.

Prosím, riaďte sa zásadou [zásada najmenších privilégií](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) pri vytváraní tokenu. To znamená, že token by mal mať iba oprávnenia, ktoré potrebuje na spustenie ukážok kódu v tomto kurze.

1. Vyberte možnosť `Fine-grained tokens` na ľavej strane obrazovky prechodom do **Nastavenia vývojára**

   ![Nastavenia vývojára](../../../translated_images/sk/profile_developer_settings.410a859fe749c755.webp)

   Potom vyberte `Generate new token`.

   ![Vygenerovať token](../../../translated_images/sk/fga_new_token.1c1a234afe202ab3.webp)

2. Zadajte popisný názov tokenu, ktorý odráža jeho účel, aby ho bolo neskôr ľahké identifikovať.

    🔐 Odporúčaná dĺžka platnosti tokenu

    Odporúčaná doba: 30 dní
    Pre väčšie zabezpečenie môžete zvoliť kratšie obdobie — napr. 7 dní 🛡️
    Je to skvelý spôsob, ako si nastaviť osobný cieľ a dokončiť kurz, keď máte vysokú motiváciu učiť sa 🚀.

    ![Názov tokenu a expirácia](../../../translated_images/sk/token-name-expiry-date.a095fb0de6386864.webp)

3. Obmedzte rozsah tokenu na váš fork tohto repozitára.

    ![Obmedziť rozsah na fork repozitára](../../../translated_images/sk/token_repository_limit.924ade5e11d9d8bb.webp)

4. Obmedzte oprávnenia tokenu: pod **Permissions** kliknite na kartu **Account**, a kliknite na tlačidlo "+ Add permissions". Objaví sa rozbaľovacie menu. Vyhľadajte **Models** a zaškrtnite políčko pri ňom.

    ![Pridať oprávnenie Modely](../../../translated_images/sk/add_models_permissions.c0c44ed8b40fc143.webp)

5. Overte požadované oprávnenia pred vygenerovaním tokenu. ![Overiť oprávnenia](../../../translated_images/sk/verify_permissions.06bd9e43987a8b21.webp)

6. Pred vygenerovaním tokenu sa uistite, že ho budete môcť uložiť na bezpečné miesto, napríklad do správcu hesiel, pretože po vytvorení už nebude zobrazený. ![Uložiť token bezpečne](../../../translated_images/sk/store_token_securely.08ee2274c6ad6caf.webp)

Skopírujte nový token, ktorý ste práve vytvorili. Tento token teraz pridáte do súboru `.env` priloženého v tomto kurze.

### Krok 2: Vytvorte súbor `.env`

Na vytvorenie súboru `.env` spustite v termináli nasledujúci príkaz.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Tým sa skopíruje vzorový súbor a vytvorí sa `.env` vo vašom adresári, kde vyplníte hodnoty pre premenné prostredia.

Po skopírovaní tokenu otvorte súbor `.env` vo svojom obľúbenom textovom editore a vložte token do poľa `GITHUB_TOKEN`.

![Pole GitHub tokenu](../../../translated_images/sk/github_token_field.20491ed3224b5f4a.webp)

Teraz by ste mali byť schopní spustiť ukážky kódu z tohto kurzu.

## Nastavenie pre ukážky používajúce Microsoft Foundry a Azure AI Agent Service

### Krok 1: Získajte endpoint vášho Azure projektu


Postup vytvorenia hubu a projektu v Azure AI Foundry nájdete tu: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Keď vytvoríte projekt, budete potrebovať získať reťazec pripojenia pre váš projekt.

Toto urobíte na stránke **Prehľad** vášho projektu v portáli Microsoft Foundry.

![Reťazec pripojenia projektu](../../../translated_images/sk/project-endpoint.8cf04c9975bbfbf1.webp)

### Krok 2: Vytvorte súbor `.env`

Na vytvorenie súboru `.env` spustite v termináli nasledujúci príkaz.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Tým sa skopíruje vzorový súbor a vytvorí sa `.env` vo vašom adresári, kde vyplníte hodnoty pre premenné prostredia.

Po skopírovaní endpointu otvorte súbor `.env` vo svojom obľúbenom textovom editore a vložte endpoint do poľa `PROJECT_ENDPOINT`.

### Krok 3: Prihláste sa do Azure

Ako bezpečnostnú najlepšiu prax použijeme [overovanie bez kľúčov](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) na autentifikáciu do Azure OpenAI pomocou Microsoft Entra ID. 

Ďalej otvorte terminál a spustite `az login --use-device-code`, aby ste sa prihlásili do svojho Azure účtu.

Po prihlásení vyberte v termináli svoje predplatné.

## Ďalšie premenné prostredia - Azure Search a Azure OpenAI 

Pre lekciu Agentic RAG - Lekcia 5 - existujú príklady, ktoré používajú Azure Search a Azure OpenAI.

Ak chcete spustiť tieto ukážky, budete musieť pridať nasledujúce premenné prostredia do svojho súboru `.env`:

### Stránka prehľadu (projekt)

- `AZURE_SUBSCRIPTION_ID` - Skontrolujte **Podrobnosti projektu** na stránke **Prehľad** vášho projektu.

- `AZURE_AI_PROJECT_NAME` - Pozrite sa na vrch stránky **Prehľad** vášho projektu.

- `AZURE_OPENAI_SERVICE` - Nájdete to na karte **Zahrnuté funkcie** pre **Azure OpenAI Service** na stránke **Prehľad**.

### Centrum správy

- `AZURE_OPENAI_RESOURCE_GROUP` - Choďte do **Vlastnosti projektu** na stránke **Prehľad** v **Centre správy**.

- `GLOBAL_LLM_SERVICE` - V sekcii **Pripojené zdroje** nájdite názov pripojenia **Azure AI Services**. Ak nie je uvedené, skontrolujte na **Azure portáli** v rámci svojej skupiny prostriedkov názov zdroja AI Services.

### Stránka modelov + endpointov

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Vyberte svoj embedding model (napr. `text-embedding-ada-002`) a všimnite si **Názov nasadenia** v detailoch modelu.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Vyberte svoj chat model (napr. `gpt-4o-mini`) a všimnite si **Názov nasadenia** v detailoch modelu.

### Azure portál

- `AZURE_OPENAI_ENDPOINT` - Hľadajte **Služby Azure AI**, kliknite na ne, potom choďte do **Správa prostriedkov**, **Kľúče a endpoint**, posuňte sa nadol k "Azure OpenAI endpoints" a skopírujte ten, ktorý hovorí "Language APIs".

- `AZURE_OPENAI_API_KEY` - Z tej istej obrazovky skopírujte KEY 1 alebo KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Nájdite svoj zdroj **Azure AI Search**, kliknite naň a pozrite si **Prehľad**.

- `AZURE_SEARCH_API_KEY` - Potom choďte do **Nastavenia** a potom **Kľúče**, kde skopírujete primárny alebo sekundárny admin kľúč.

### Externá webová stránka

- `AZURE_OPENAI_API_VERSION` - Navštívte stránku [životný cyklus verzií API](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) v časti **Najnovšie všeobecne dostupné vydanie API**.

### Nastavenie autentifikácie bez kľúčov

Namiesto tvrdého zakódovania prihlasovacích údajov použijeme keyless spojenie s Azure OpenAI. Na to naimportujeme `DefaultAzureCredential` a neskôr zavoláme funkciu `DefaultAzureCredential`, aby sme získali overovacie údaje.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Uviazli ste niekde?
Ak máte nejaké problémy so spustením tohto nastavenia, pridajte sa na náš <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> alebo <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">nahláste problém</a>.

## Ďalšia lekcia

Teraz ste pripravení spustiť kód pre tento kurz. Prajeme veľa úspechov pri ďalšom spoznávaní sveta AI agentov! 

[Úvod do AI agentov a prípadov použitia](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vyhlásenie o vylúčení zodpovednosti**:
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Hoci sa usilujeme o presnosť, vezmite prosím na vedomie, že automatizované preklady môžu obsahovať chyby alebo nepresnosti. Pôvodný dokument v jeho originálnom jazyku by mal byť považovaný za autoritatívny zdroj. Pri kritických informáciách sa odporúča profesionálny ľudský preklad. Nepreberáme zodpovednosť za akékoľvek nedorozumenia alebo nesprávne výklady vzniknuté v dôsledku použitia tohto prekladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->