# AGENTS.md

## Przegląd projektu

To repozytorium zawiera "AI Agents for Beginners" - kompleksowy kurs edukacyjny uczący wszystkiego, co potrzebne do budowy agentów AI. Kurs składa się z 15+ lekcji obejmujących podstawy, wzorce projektowe, frameworki oraz wdrożenie agentów AI do produkcji.

**Kluczowe technologie:**
- Python 3.12+
- Jupyter Notebooks do nauki interaktywnej
- AI Frameworki: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Services: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (dostępny bezpłatny poziom)

**Architektura:**
- Struktura oparta na lekcjach (katalogi 00-15+)
- Każda lekcja zawiera: dokumentację README, przykłady kodu (notatniki Jupyter) i obrazy
- Wsparcie wielojęzyczne poprzez zautomatyzowany system tłumaczeń
- Wiele opcji frameworków w każdej lekcji (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Polecenia konfiguracji

### Wymagania wstępne
- Python 3.12 lub nowszy
- Konto GitHub (dla GitHub Models - bezpłatny poziom)
- Subskrypcja Azure (opcjonalnie, dla usług Azure AI)

### Początkowa konfiguracja

1. **Clone or fork the repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # LUB
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Create and activate Python virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # W systemie Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # Edytuj plik .env, wpisując w nim swoje klucze API i endpointy
   ```

### Wymagane zmienne środowiskowe

For **GitHub Models (Free)**:
- `GITHUB_TOKEN` - Token dostępu osobistego z GitHub

For **Azure AI Services** (optional):
- `PROJECT_ENDPOINT` - Microsoft Foundry project endpoint
- `AZURE_OPENAI_API_KEY` - Azure OpenAI API key
- `AZURE_OPENAI_ENDPOINT` - Azure OpenAI endpoint URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Deployment name for chat model
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Deployment name for embeddings
- Additional Azure configuration as shown in `.env.example`

## Przepływ pracy deweloperskiej

### Uruchamianie notatników Jupyter

Każda lekcja zawiera wiele notatników Jupyter dla różnych frameworków:

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigate to a lesson directory** (e.g., `01-intro-to-ai-agents/code_samples/`)

3. **Open and run notebooks:**
   - `*-semantic-kernel.ipynb` - Korzystanie z frameworku Semantic Kernel
   - `*-autogen.ipynb` - Korzystanie z frameworku AutoGen
   - `*-python-agent-framework.ipynb` - Korzystanie z Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Korzystanie z Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Korzystanie z Azure AI Agent Service

### Praca z różnymi frameworkami

**Semantic Kernel + GitHub Models:**
- Bezpłatny poziom dostępny z kontem GitHub
- Dobry do nauki i eksperymentów
- File pattern: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Bezpłatny poziom dostępny z kontem GitHub
- Możliwości orkiestracji wieloagentowej
- File pattern: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Najnowszy framework od Microsoft
- Dostępny w Python i .NET
- File pattern: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Wymaga subskrypcji Azure
- Funkcje gotowe do użycia w produkcji
- File pattern: `*-azureaiagent.ipynb`

## Instrukcje testowania

To repozytorium edukacyjne z przykładowym kodem, a nie kod produkcyjny z testami automatycznymi. Aby zweryfikować swoją konfigurację i zmiany:

### Testowanie ręczne

1. **Test Python environment:**
   ```bash
   python --version  # Powinno być 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test notebook execution:**
   ```bash
   # Konwertuj notebook na skrypt i uruchom (importy testów)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verify environment variables:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Uruchamianie poszczególnych notatników

Otwórz notatniki w Jupyter i wykonuj komórki kolejno. Każdy notatnik jest samodzielny i zawiera:
- instrukcje importu
- ładowanie konfiguracji
- przykładowe implementacje agentów
- oczekiwane wyjścia w komórkach markdown

## Styl kodu

### Konwencje Pythona

- **Python Version**: 3.12+
- **Code Style**: Stosuj standardowe konwencje PEP 8 dla Pythona
- **Notebooks**: Używaj czytelnych komórek markdown do wyjaśnień koncepcji
- **Imports**: Grupuj importy: biblioteka standardowa, zewnętrzne, lokalne

### Konwencje notatników Jupyter

- Dołączaj opisowe komórki markdown przed komórkami z kodem
- Dodawaj przykłady wyników w notatnikach do referencji
- Używaj czytelnych nazw zmiennych odpowiadających koncepcjom lekcji
- Utrzymuj liniową kolejność wykonywania notatnika (komórka 1 → 2 → 3...)

### Organizacja plików

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

## Budowanie i wdrażanie

### Tworzenie dokumentacji

To repozytorium używa Markdown do dokumentacji:
- Pliki README.md w każdym folderze lekcji
- Główny README.md w katalogu głównym repozytorium
- Zautomatyzowany system tłumaczeń za pomocą GitHub Actions

### Potok CI/CD

Located in `.github/workflows/`:

1. **co-op-translator.yml** - Automatyczne tłumaczenie na 50+ języków
2. **welcome-issue.yml** - Wysyła powitanie twórcom nowych issue
3. **welcome-pr.yml** - Wysyła powitanie nowym kontrybutorom pull request

### Wdrażanie

To repozytorium edukacyjne - brak procesu wdrażania. Użytkownicy:
1. Fork lub sklonuj repozytorium
2. Uruchamiaj notatniki lokalnie lub w GitHub Codespaces
3. Ucz się, modyfikując i eksperymentując z przykładami

## Wytyczne dotyczące pull requestów

### Przed wysłaniem

1. **Test your changes:**
   - Uruchom w całości dotknięte notatniki
   - Sprawdź, że wszystkie komórki wykonują się bez błędów
   - Sprawdź, czy wyniki są odpowiednie

2. **Documentation updates:**
   - Zaktualizuj README.md jeśli dodajesz nowe koncepcje
   - Dodaj komentarze w notatnikach dla skomplikowanego kodu
   - Upewnij się, że komórki markdown wyjaśniają cel

3. **File changes:**
   - Unikaj commitowania plików `.env` (używaj `.env.example`)
   - Nie commituj katalogów `venv/` ani `__pycache__/`
   - Zachowaj outputy notatników gdy demonstrują koncepcje
   - Usuń pliki tymczasowe i notatniki kopii zapasowych (`*-backup.ipynb`)

### PR Title Format

Używaj opisowych tytułów:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Popraw literówkę w lesson-XX README`
- `[Update] Ulepsz przykład kodu w lesson-XX`
- `[Docs] Zaktualizuj instrukcje konfiguracji`

### Wymagane kontrole

- Notatniki powinny wykonywać się bez błędów
- Pliki README powinny być jasne i dokładne
- Stosuj istniejące wzorce kodu w repozytorium
- Zachowaj spójność z innymi lekcjami

## Dodatkowe uwagi

### Częste problemy

1. **Python version mismatch:**
   - Upewnij się, że używasz Pythona 3.12+
   - Niektóre pakiety mogą nie działać z starszymi wersjami
   - Użyj `python3 -m venv`, aby wprost określić wersję Pythona

2. **Environment variables:**
   - Zawsze twórz `.env` na podstawie `.env.example`
   - Nie commituj pliku `.env` (jest w `.gitignore`)
   - Token GitHub wymaga odpowiednich uprawnień

3. **Package conflicts:**
   - Użyj świeżego środowiska wirtualnego
   - Instaluj z `requirements.txt` zamiast pojedynczych pakietów
   - Niektóre notatniki mogą wymagać dodatkowych pakietów wymienionych w ich komórkach markdown

4. **Azure services:**
   - Usługi Azure AI wymagają aktywnej subskrypcji
   - Niektóre funkcje są specyficzne dla regionu
   - Ograniczenia bezpłatnego poziomu dotyczą GitHub Models

### Ścieżka nauki

Zalecana kolejność przechodzenia przez lekcje:
1. **00-course-setup** - Zacznij tutaj, aby skonfigurować środowisko
2. **01-intro-to-ai-agents** - Zrozum fundamenty agentów AI
3. **02-explore-agentic-frameworks** - Poznaj różne frameworki
4. **03-agentic-design-patterns** - Główne wzorce projektowe
5. Kontynuuj kolejno przez numerowane lekcje

### Wybór frameworku

Wybierz framework w zależności od swoich celów:
- **Learning/Prototyping**: Semantic Kernel + GitHub Models (bezpłatne)
- **Multi-agent systems**: AutoGen
- **Latest features**: Microsoft Agent Framework (MAF)
- **Production deployment**: Azure AI Agent Service

### Uzyskiwanie pomocy

- Dołącz do [Społeczności Microsoft Foundry na Discordzie](https://aka.ms/ai-agents/discord)
- Przejrzyj pliki README lekcji, aby uzyskać szczegółowe wskazówki
- Sprawdź główny [README.md](./README.md) w celu przeglądu kursu
- Odnieś się do [Konfiguracja kursu](./00-course-setup/README.md) po szczegółowe instrukcje konfiguracji

### Wkład

To otwarty projekt edukacyjny. Wkłady mile widziane:
- Ulepsz przykłady kodu
- Popraw literówki lub błędy
- Dodaj wyjaśniające komentarze
- Zaproponuj nowe tematy lekcji
- Przetłumacz na dodatkowe języki

Zobacz [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) dla aktualnych potrzeb.

## Kontekst specyficzny dla projektu

### Wsparcie wielojęzyczne

To repozytorium używa zautomatyzowanego systemu tłumaczeń:
- Wspierane 50+ języków
- Tłumaczenia w katalogach `/translations/<lang-code>/`
- Workflow GitHub Actions obsługuje aktualizacje tłumaczeń
- Pliki źródłowe są w języku angielskim w katalogu głównym repozytorium

### Struktura lekcji

Każda lekcja stosuje spójny wzorzec:
1. Miniatura wideo z linkiem
2. Zapisana treść lekcji (README.md)
3. Przykłady kodu w wielu frameworkach
4. Cele nauczania i wymagania wstępne
5. Dodatkowe powiązane zasoby edukacyjne

### Nazewnictwo przykładów kodu

Format: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Lekcja 4, Semantic Kernel
- `07-autogen.ipynb` - Lekcja 7, AutoGen
- `14-python-agent-framework.ipynb` - Lekcja 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lekcja 14, MAF .NET

### Specjalne katalogi

- `translated_images/` - Zlokalizowane obrazy dla tłumaczeń
- `images/` - Oryginalne obrazy dla treści w języku angielskim
- `.devcontainer/` - Konfiguracja kontenera deweloperskiego VS Code
- `.github/` - Workflowy i szablony GitHub Actions

### Zależności

Kluczowe pakiety z `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - framework AutoGen
- `semantic-kernel` - framework Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - usługi Azure AI
- `azure-search-documents` - integracja z Azure AI Search
- `chromadb` - baza wektorowa dla przykładów RAG
- `chainlit` - framework UI czatu
- `browser_use` - automatyzacja przeglądarki dla agentów
- `mcp[cli]` - wsparcie Model Context Protocol
- `mem0ai` - zarządzanie pamięcią dla agentów

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Zastrzeżenie:
Niniejszy dokument został przetłumaczony przy użyciu usługi tłumaczenia AI Co‑op Translator (https://github.com/Azure/co-op-translator). Chociaż dokładamy starań, by tłumaczenie było poprawne, prosimy pamiętać, że tłumaczenia automatyczne mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku źródłowym należy traktować jako wersję wiążącą. W przypadku informacji krytycznych zalecane jest skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z użycia tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->