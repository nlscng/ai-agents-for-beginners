# Konfiguracja kursu

## Wprowadzenie

Ta lekcja pokaże, jak uruchomić przykłady kodu z tego kursu.

## Dołącz do innych uczących się i uzyskaj pomoc

Zanim zaczniesz klonować swoje repozytorium, dołącz do [kanału Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord), aby uzyskać pomoc przy konfiguracji, odpowiedzi na pytania dotyczące kursu lub aby połączyć się z innymi uczącymi się.

## Sklonuj lub rozwidlenie tego repozytorium

Aby zacząć, proszę sklonuj lub rozwidlnij repozytorium GitHub. To utworzy Twoją własną wersję materiałów kursu, dzięki czemu możesz uruchamiać, testować i modyfikować kod!

Można to zrobić klikając link <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fork the repo</a>

Powinieneś teraz mieć własną wersję rozwidloną tego kursu pod następującym linkiem:

![Forked Repo](../../../translated_images/pl/forked-repo.33f27ca1901baa6a.webp)

### Płytkie klonowanie (zalecane na warsztaty / Codespaces)

> Pełne repozytorium może być duże (~3 GB), jeśli pobierzesz całą historię i wszystkie pliki. Jeśli bierzesz udział tylko w warsztatach lub potrzebujesz tylko kilku folderów z lekcjami, płytkie klonowanie (lub klonowanie oszczędne) pozwala uniknąć większości tego pobierania przez skrócenie historii i/lub pominięcie blobów.

#### Szybkie płytkie klonowanie — minimalna historia, wszystkie pliki

Zastąp `<your-username>` poniższych poleceń adresem URL twojego fork (lub URL upstream jeśli wolisz).

Aby sklonować tylko najnowszą historię commitów (małe pobieranie):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Aby sklonować konkretną gałąź:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Częściowe (oszczędne) klonowanie — minimalne bloby + tylko wybrane foldery

Używa częściowego klonowania i sparse-checkout (wymaga Git 2.25+ i zalecany nowoczesny Git z obsługą częściowego klonowania):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Przejdź do folderu repozytorium:

```bash|powershell
cd ai-agents-for-beginners
```

Następnie określ, które foldery chcesz pobrać (poniższy przykład pokazuje dwa foldery):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Po sklonowaniu i weryfikacji plików, jeśli potrzebujesz tylko plików i chcesz zwolnić miejsce (bez historii git), usuń metadane repozytorium (💀nieodwracalne — utracisz całą funkcjonalność Git: brak commitów, pull, push czy dostępu do historii).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Użycie GitHub Codespaces (zalecane, aby uniknąć dużych lokalnych pobrań)

- Utwórz nowy Codespace dla tego repozytorium za pomocą [GitHub UI](https://github.com/codespaces).  

- W terminalu nowo utworzonego codespace, uruchom jedno z poleceń płytkiego/oszczędnego klonowania powyżej, aby przynieść tylko potrzebne foldery z lekcjami do przestrzeni roboczej Codespace.
- Opcjonalnie: po klonowaniu wewnątrz Codespaces, usuń .git, aby odzyskać dodatkowe miejsce (patrz polecenia usuwania powyżej).
- Uwaga: Jeśli chcesz otworzyć repozytorium bezpośrednio w Codespaces (bez dodatkowego klonowania), pamiętaj, że Codespaces zbuduje środowisko devcontainer i może przygotować więcej niż potrzebujesz. Klonowanie płytkiej kopii w świeżym Codespace daje większą kontrolę nad zużyciem dysku.

#### Wskazówki

- Zawsze zamieniaj URL klonowania na swój fork, jeśli chcesz edytować/commitować.
- Jeśli później będziesz potrzebować więcej historii lub plików, możesz je pobrać lub dostosować sparse-checkout, aby uwzględnić dodatkowe foldery.

## Uruchamianie kodu

Ten kurs oferuje serię notatników Jupyter, które możesz uruchamiać, by zdobyć praktyczne doświadczenie budując AI Agents.

Przykłady kodu używają:

**Wymaga konta GitHub - darmowe**:

1) Framework Semantic Kernel Agent + GitHub Models Marketplace. Oznaczone jako (semantic-kernel.ipynb)
2) Framework AutoGen + GitHub Models Marketplace. Oznaczone jako (autogen.ipynb)

**Wymaga subskrypcji Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Oznaczone jako (azureaiagent.ipynb)

Zachęcamy do wypróbowania wszystkich trzech typów przykładów, aby zobaczyć, który najlepiej Ci odpowiada.

Wybrana opcja określi, które kroki instalacji musisz wykonać poniżej:

## Wymagania

- Python 3.12+
  - **UWAGA**: Jeśli nie masz zainstalowanego Pythona 3.12, zainstaluj go. Następnie utwórz środowisko wirtualne (venv) używając python3.12, aby zapewnić instalację odpowiednich wersji z pliku requirements.txt.
  
    >Przykład

    Utwórz katalog wirtualnego środowiska Python:

    ```bash|powershell
    python -m venv venv
    ```

    Następnie aktywuj środowisko venv dla:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Dla przykładowych kodów w .NET, upewnij się, że masz zainstalowany [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) lub nowszy. Sprawdź wersję zainstalowanego SDK:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Konto GitHub - do dostępu do GitHub Models Marketplace
- Subskrypcja Azure - do dostępu do Microsoft Foundry
- Konto Microsoft Foundry - do dostępu do Azure AI Agent Service

W tym repozytorium znajduje się plik `requirements.txt` w katalogu głównym, zawierający wszystkie wymagane pakiety Python do uruchomienia przykładów kodu.

Możesz je zainstalować, uruchamiając następujące polecenie w terminalu w katalogu głównym repozytorium:

```bash|powershell
pip install -r requirements.txt
```

Zalecamy stworzenie wirtualnego środowiska Python, aby uniknąć konfliktów i problemów.

## Konfiguracja VSCode

Upewnij się, że używasz odpowiedniej wersji Pythona w VSCode.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Konfiguracja dla przykładów z GitHub Models

### Krok 1: Pobierz swój Token Dostępu Osobistego GitHub (PAT)

Ten kurs korzysta z GitHub Models Marketplace, oferując darmowy dostęp do dużych modeli językowych (LLM), które wykorzystasz do budowania AI Agents.

Aby korzystać z GitHub Models, musisz utworzyć [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Można to zrobić, przechodząc do <a href="https://github.com/settings/personal-access-tokens" target="_blank">ustawień tokenów dostępu osobistego</a> w swoim koncie GitHub.

Proszę, stosuj się do [zasady najmniejszych uprawnień](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) podczas tworzenia tokenu. Oznacza to, że powinieneś nadać tokenowi tylko te uprawnienia, które są niezbędne do uruchomienia przykładów kodu z tego kursu.

1. Wybierz opcję `Fine-grained tokens` po lewej stronie ekranu, przechodząc do **Developer settings**

   ![Developer settings](../../../translated_images/pl/profile_developer_settings.410a859fe749c755.webp)

   Następnie wybierz `Generate new token`.

   ![Generate Token](../../../translated_images/pl/fga_new_token.1c1a234afe202ab3.webp)

2. Wpisz opisową nazwę tokenu, która odzwierciedla jego przeznaczenie, aby łatwiej było go potem zidentyfikować.

    🔐 Zalecany czas ważności tokenu

    Zalecany czas: 30 dni  
    Dla większego bezpieczeństwa możesz wybrać krótszy okres — np. 7 dni 🛡️  
    To świetny sposób, by ustawić sobie cel osobisty i ukończyć kurs, gdy Twoja motywacja jest wysoka 🚀.

    ![Token Name and Expiration](../../../translated_images/pl/token-name-expiry-date.a095fb0de6386864.webp)

3. Ogranicz zakres tokenu do Twojego fork tego repozytorium.

    ![Limit scope to fork repository](../../../translated_images/pl/token_repository_limit.924ade5e11d9d8bb.webp)

4. Ogranicz uprawnienia tokenu: w sekcji **Permissions**, kliknij zakładkę **Account**, a następnie kliknij przycisk "+ Add permissions". Pojawi się menu rozwijane. Wyszukaj **Models** i zaznacz pole wyboru.

    ![Add Models Permission](../../../translated_images/pl/add_models_permissions.c0c44ed8b40fc143.webp)

5. Zweryfikuj wymagane uprawnienia przed wygenerowaniem tokenu. ![Verify Permissions](../../../translated_images/pl/verify_permissions.06bd9e43987a8b21.webp)

6. Przed wygenerowaniem tokenu upewnij się, że jesteś gotów przechować token w bezpiecznym miejscu, np. w menedżerze haseł, ponieważ nie będzie on wyświetlany ponownie po utworzeniu. ![Store Token Securely](../../../translated_images/pl/store_token_securely.08ee2274c6ad6caf.webp)

Skopiuj nowy token, który właśnie utworzyłeś. Teraz dodasz go do pliku `.env` dołączonego do tego kursu.

### Krok 2: Utwórz swój plik `.env`

Aby utworzyć plik `.env`, uruchom następujące polecenie w terminalu.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

To skopiuje plik przykładowy i utworzy `.env` w katalogu, w którym wypełnisz wartości zmiennych środowiskowych.

Po skopiowaniu tokenu otwórz plik `.env` w ulubionym edytorze tekstu i wklej token do pola `GITHUB_TOKEN`.

![GitHub Token Field](../../../translated_images/pl/github_token_field.20491ed3224b5f4a.webp)

Teraz powinieneś mieć możliwość uruchomienia przykładów kodu z tego kursu.

## Konfiguracja dla przykładów z Microsoft Foundry i Azure AI Agent Service

### Krok 1: Pobierz końcowy punkt (endpoint) projektu Azure

Postępuj zgodnie z instrukcjami tworzenia hubu i projektu w Azure AI Foundry opisanymi tutaj: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

Po utworzeniu projektu musisz pobrać łańcuch połączenia (connection string) swojego projektu.

Można to zrobić, przechodząc do strony **Overview** swojego projektu w portalu Microsoft Foundry.

![Project Connection String](../../../translated_images/pl/project-endpoint.8cf04c9975bbfbf1.webp)

### Krok 2: Utwórz swój plik `.env`

Aby utworzyć plik `.env`, uruchom następujące polecenie w terminalu.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

To skopiuje plik przykładowy i utworzy `.env` w katalogu, w którym wypełnisz wartości zmiennych środowiskowych.

Po skopiowaniu tokenu otwórz plik `.env` w ulubionym edytorze tekstu i wklej token do pola `PROJECT_ENDPOINT`.

### Krok 3: Zaloguj się do Azure

Jako najlepszą praktykę bezpieczeństwa użyjemy [uwierzytelniania bez klucza](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) do uwierzytelniania do Azure OpenAI za pomocą Microsoft Entra ID.

Następnie otwórz terminal i uruchom `az login --use-device-code`, aby zalogować się na swoje konto Azure.

Po zalogowaniu wybierz swoją subskrypcję w terminalu.

## Dodatkowe zmienne środowiskowe - Azure Search i Azure OpenAI

Dla lekcji Agentic RAG - Lekcja 5 - dostępne są przykłady korzystające z Azure Search i Azure OpenAI.

Jeśli chcesz uruchomić te przykłady, musisz dodać następujące zmienne środowiskowe do pliku `.env`:

### Strona Overview (Projekt)

- `AZURE_SUBSCRIPTION_ID` - Sprawdź **Szczegóły projektu** na stronie **Overview** swojego projektu.

- `AZURE_AI_PROJECT_NAME` - Spójrz na górę strony **Overview** swojego projektu.

- `AZURE_OPENAI_SERVICE` - Znajdziesz to w zakładce **Included capabilities** dla **Azure OpenAI Service** na stronie **Overview**.

### Centrum zarządzania

- `AZURE_OPENAI_RESOURCE_GROUP` - Przejdź do **Właściwości projektu** na stronie **Overview** w **Management Center**.

- `GLOBAL_LLM_SERVICE` - W sekcji **Connected resources** znajdź nazwę połączenia **Azure AI Services**. Jeśli nie jest wymieniona, sprawdź w **Azure portal** w grupie zasobów nazwę zasobu AI Services.

### Strona Modele + Punkty końcowe

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Wybierz swój model embedding (np. `text-embedding-ada-002`) i zapisz **Deployment name** z informacji o modelu.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Wybierz swój model czatu (np. `gpt-4o-mini`) i zapisz **Deployment name** z informacji o modelu.

### Portal Azure

- `AZURE_OPENAI_ENDPOINT` - Znajdź **Azure AI services**, kliknij, a potem przejdź do **Resource Management**, **Keys and Endpoint**, przewiń do "Azure OpenAI endpoints" i skopiuj ten, który mówi "Language APIs".

- `AZURE_OPENAI_API_KEY` - Z tego samego ekranu skopiuj KLUCZ 1 lub KLUCZ 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Znajdź swój zasób **Azure AI Search**, kliknij go i zobacz stronę **Overview**.

- `AZURE_SEARCH_API_KEY` - Następnie przejdź do **Settings**, a potem **Keys**, aby skopiować klucz administratora podstawowego lub zapasowego.

### Strona zewnętrzna

- `AZURE_OPENAI_API_VERSION` - Odwiedź stronę [życia wersji API](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) pod nagłówkiem **Latest GA API release**.

### Konfiguracja uwierzytelniania bezkluczowego

Zamiast twardo wpisywać swoje poświadczenia, użyjemy połączenia bezkluczowego z Azure OpenAI. W tym celu zaimportujemy `DefaultAzureCredential` i potem wywołamy funkcję `DefaultAzureCredential`, aby uzyskać poświadczenie.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Utknąłeś gdzieś?
Jeśli napotkasz jakiekolwiek problemy z uruchomieniem tego zestawu, dołącz do naszego <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> lub <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">zgłoś problem</a>.

## Następna lekcja

Jesteś teraz gotowy, aby uruchomić kod z tego kursu. Miłej nauki o świecie Agentów AI! 

[Wprowadzenie do Agentów AI i przypadków użycia agentów](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zastrzeżenie**:  
Dokument ten został przetłumaczony za pomocą usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mimo że dokładamy starań, aby tłumaczenie było jak najdokładniejsze, prosimy mieć na uwadze, że automatyczne tłumaczenia mogą zawierać błędy lub niedokładności. Oryginalny dokument w jego języku źródłowym należy uważać za wersję autorytatywną. W przypadku informacji o krytycznym znaczeniu zalecane jest skorzystanie z profesjonalnego, ludzkiego tłumaczenia. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z użycia tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->