# Korzystanie z Agentic Protocols (MCP, A2A i NLWeb)

[![Agentic Protocols](../../../translated_images/pl/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Kliknij powyższy obraz, aby obejrzeć film z tej lekcji)_

Wraz z rosnącym wykorzystaniem agentów AI rośnie też potrzeba protokołów, które zapewnią standaryzację, bezpieczeństwo i wspierają otwartą innowację. W tej lekcji omówimy 3 protokoły, które mają sprostać tym potrzebom - Model Context Protocol (MCP), Agent to Agent (A2A) oraz Natural Language Web (NLWeb).

## Wprowadzenie

W tej lekcji omówimy:

• Jak **MCP** pozwala agentom AI na dostęp do zewnętrznych narzędzi i danych, aby realizować zadania użytkownika.

• Jak **A2A** umożliwia komunikację i współpracę pomiędzy różnymi agentami AI.

• Jak **NLWeb** wprowadza interfejsy w języku naturalnym do dowolnej strony internetowej, umożliwiając agentom AI odkrywanie i interakcję z zawartością.

## Cele Nauki

• **Zidentyfikować** główny cel i korzyści MCP, A2A i NLWeb w kontekście agentów AI.

• **Wyjaśnić** jak każdy protokół ułatwia komunikację i interakcję pomiędzy LLM, narzędziami i innymi agentami.

• **Rozpoznać** różne role, jakie każdy protokół odgrywa w budowie złożonych systemów agentowych.

## Model Context Protocol

**Model Context Protocol (MCP)** to otwarty standard, który zapewnia ustandaryzowany sposób dostarczania kontekstu i narzędzi do LLM przez aplikacje. Umożliwia to stworzenie „uniwersalnego adaptera” do różnych źródeł danych i narzędzi, do których agenci AI mogą się łączyć w spójny sposób.

Przyjrzyjmy się komponentom MCP, korzyściom w porównaniu do bezpośredniego korzystania z API oraz przykładzie jak agenci AI mogą korzystać z serwera MCP.

### Główne komponenty MCP

MCP działa w oparciu o **architekturę klient-serwer**, a podstawowe składniki to:

• **Hosty** to aplikacje LLM (np. edytor kodu jak VSCode), które inicjują połączenia z serwerem MCP.

• **Klienci** to komponenty wewnątrz aplikacji hosta, utrzymujące połączenia jeden do jednego z serwerami.

• **Serwery** to lekkie programy udostępniające konkretne funkcjonalności.

W protokole zawarte są trzy podstawowe prymitywy będące zdolnościami serwera MCP:

• **Narzędzia**: To oddzielne akcje lub funkcje, które agent AI może wywołać, aby wykonać działanie. Na przykład serwis pogodowy może udostępniać narzędzie „pobierz pogodę”, a serwis e-commerce narzędzie „kup produkt”. Serwery MCP reklamują nazwę, opis i schemat wejścia/wyjścia każdego narzędzia w ich liście możliwości.

• **Zasoby**: To dane lub dokumenty tylko do odczytu, które serwer MCP może dostarczyć, a klienci mogą je pobierać na żądanie. Przykłady to zawartość plików, rekordy bazy danych lub pliki dziennika. Zasoby mogą być tekstowe (np. kod, JSON) lub binarne (np. obrazy, PDF-y).

• **Wzorce (Prompts)**: To predefiniowane szablony, które oferują sugerowane zapytania, pozwalając na bardziej złożone przepływy pracy.

### Korzyści MCP

MCP oferuje znaczące zalety dla agentów AI:

• **Dynamiczne Odkrywanie Narzędzi**: Agenci mogą dynamicznie otrzymać listę dostępnych narzędzi z serwera wraz z opisem ich działania. W przeciwieństwie do tradycyjnych API, które często wymagają statycznego kodowania integracji — każde API zmiana wymaga aktualizacji kodu. MCP oferuje podejście "zintegrować raz", co zapewnia większą elastyczność.

• **Interoperacyjność Między LLM**: MCP działa z różnymi LLM, zapewniając elastyczność zmiany modelu bazowego, by ocenić lepszą wydajność.

• **Standaryzowane Bezpieczeństwo**: MCP zawiera standardową metodę uwierzytelniania, co ułatwia skalowanie dostępu do kolejnych serwerów MCP. To prostsze niż zarządzanie różnymi kluczami i typami uwierzytelniania dla różnych tradycyjnych API.

### Przykład MCP

![MCP Diagram](../../../translated_images/pl/mcp-diagram.e4ca1cbd551444a1.webp)

Wyobraź sobie, że użytkownik chce zarezerwować lot za pomocą asystenta AI działającego na MCP.

1. **Połączenie**: Asystent AI (klient MCP) łączy się z serwerem MCP udostępnionym przez linię lotniczą.

2. **Odkrywanie Narzędzi**: Klient pyta serwer MCP linii lotniczej: „Jakie masz dostępne narzędzia?” Serwer odpowiada narzędziami takimi jak „wyszukaj loty” i „zarezerwuj lot”.

3. **Wywołanie Narzędzia**: Następnie prosisz asystenta AI: „Proszę, wyszukaj lot z Portland do Honolulu.” Asystent AI, korzystając ze swojego LLM, identyfikuje, że musi wywołać narzędzie „wyszukaj loty” i przekazuje odpowiednie parametry (miejsce startu, miejsce docelowe) do serwera MCP.

4. **Wykonanie i Odpowiedź**: Serwer MCP pełni rolę wrappera i wykonuje faktyczne wywołanie do wewnętrznego API rezerwacji linii lotniczej. Następnie otrzymuje informacje o lotach (np. dane JSON) i wysyła je z powrotem do asystenta AI.

5. **Dalsza Interakcja**: Asystent AI prezentuje opcje lotów. Gdy wybierzesz lot, asystent może wywołać narzędzie „zarezerwuj lot” na tym samym serwerze MCP, finalizując rezerwację.

## Protokół Agent-to-Agent (A2A)

Podczas gdy MCP skupia się na łączeniu LLM z narzędziami, **protokół Agent-to-Agent (A2A)** idzie o krok dalej, umożliwiając komunikację i współpracę między różnymi agentami AI. A2A łączy agentów AI z różnych organizacji, środowisk i stosów technologicznych, by wykonać wspólne zadanie.

Przeanalizujemy komponenty i korzyści A2A oraz przykład zastosowania w naszej aplikacji podróżniczej.

### Główne komponenty A2A

A2A koncentruje się na umożliwieniu komunikacji pomiędzy agentami i współpracy przy realizacji podzadań użytkownika. Każdy element protokołu się do tego przyczynia:

#### Agent Card

Podobnie jak serwer MCP udostępnia listę narzędzi, Agent Card zawiera:
- Nazwę Agenta.
- **opis ogólnych zadań**, które wykonuje.
- **listę specyficznych umiejętności** z opisami, które pomagają innym agentom (lub nawet ludziom) zrozumieć, kiedy i dlaczego warto wywołać danego agenta.
- **obecny URL Endpoint** agenta.
- **wersję** i **możliwości** agenta, takie jak streaming odpowiedzi i powiadomienia push.

#### Agent Executor

Agent Executor odpowiada za **przekazanie kontekstu rozmowy użytkownika do zdalnego agenta**, który tego potrzebuje, aby zrozumieć zadanie do wykonania. W serwerze A2A agent używa własnego Large Language Model (LLM) do analizowania przychodzących zapytań i realizacji zadań za pomocą swoich wewnętrznych narzędzi.

#### Artefakt

Gdy zdalny agent wykona żądane zadanie, jego rezultat jest utworzony jako artefakt. Artefakt zawiera **wynik pracy agenta**, **opis wykonanej czynności** oraz **kontekst tekstowy** przesyłany w protokole. Po wysłaniu artefaktu połączenie ze zdalnym agentem jest zamykane aż do ponownego wywołania.

#### Event Queue

Ten komponent służy do **obsługi aktualizacji i przekazywania wiadomości**. Jest szczególnie ważny w produkcji systemów agentowych, aby zapobiegać zamknięciu połączenia między agentami przed zakończeniem zadania, zwłaszcza gdy wykonanie może trwać dłużej.

### Korzyści A2A

• **Zwiększona Współpraca**: Umożliwia agentom z różnych dostawców i platform interakcję, współdzielenie kontekstu i pracę zespołową, ułatwiając automatyzację w systemach tradycyjnie rozłączonych.

• **Elastyczność Wyboru Modelu**: Każdy agent A2A może zdecydować, którego LLM używa do obsługi swoich zapytań, pozwalając na optymalizację lub dostosowanie modeli dla każdego agenta, w odróżnieniu od pojedynczego połączenia LLM w niektórych scenariuszach MCP.

• **Wbudowane Uwierzytelnianie**: Autoryzacja jest bezpośrednio zintegrowana z protokołem A2A, zapewniając solidne ramy bezpieczeństwa interakcji agentów.

### Przykład A2A

![A2A Diagram](../../../translated_images/pl/A2A-Diagram.8666928d648acc26.webp)

Rozwińmy nasz scenariusz rezerwacji podróży, tym razem korzystając z A2A.

1. **Złożone Zapytanie Użytkownika do Multi-Agenta**: Użytkownik kontaktuje się z klientem/agenta A2A „Agent Podróży”, mówiąc np.: „Proszę zarezerwuj całą podróż do Honolulu na przyszły tydzień, włączając bilety lotnicze, hotel i samochód do wynajęcia”.

2. **Orkiestracja przez Agenta Podróży**: Agent Podróży otrzymuje to złożone zapytanie. Używa swojego LLM, aby rozważyć zadanie i określić, że musi komunikować się z innymi wyspecjalizowanymi agentami.

3. **Komunikacja Między Agentami**: Agent Podróży wykorzystuje protokół A2A do połączenia się z agentami podrzędnymi, jak „Agent Linii Lotniczej”, „Agent Hotelowy” i „Agent Wynajmu Samochodów” tworzonymi przez różne firmy.

4. **Delegowanie Zadań**: Agent Podróży wysyła konkretne zadania do tych specjalistycznych agentów (np. „Znajdź loty do Honolulu”, „Zarezerwuj hotel”, „Wynajmij samochód”). Każdy z tych agentów, korzystając z własnych LLM i swoich narzędzi (które mogą być serwerami MCP), realizuje swoją część rezerwacji.

5. **Skompilowana Odpowiedź**: Gdy wszyscy agenci podrzędni zakończą zadania, Agent Podróży kompiluje wyniki (szczegóły lotów, potwierdzenie hotelu, rezerwację samochodu) i wysyła kompleksową odpowiedź w stylu czatu do użytkownika.

## Natural Language Web (NLWeb)

Strony internetowe od dawna są głównym sposobem dostępu użytkowników do informacji i danych w internecie.

Przyjrzyjmy się różnym komponentom NLWeb, korzyściom oraz przykładowemu działaniu naszej aplikacji podróżniczej z NLWeb.

### Komponenty NLWeb

- **Aplikacja NLWeb (Kod Usługi Głównej)**: System przetwarzający pytania w języku naturalnym. Łączy różne części platformy, aby tworzyć odpowiedzi. Można ją uważać za **silnik odpowiedzialny za funkcje języka naturalnego** na stronie internetowej.

- **Protokół NLWeb**: To **podstawowy zestaw reguł do interakcji w języku naturalnym** ze stroną internetową. Zwraca odpowiedzi w formacie JSON (często stosując Schema.org). Jego celem jest stworzenie prostych fundamentów dla „AI Web”, podobnie jak HTML umożliwił udostępnianie dokumentów online.

- **Serwer MCP (Endpoint Model Context Protocol)**: Każda konfiguracja NLWeb działa również jako **serwer MCP**. Oznacza to, że może **udostępniać narzędzia (np. metodę „ask”) oraz dane** innym systemom AI. W praktyce czyni to zawartość i możliwości strony użytecznymi dla agentów AI, umożliwiając, by strona stała się częścią szerszego „ekosystemu agentów”.

- **Modele Embeddingów**: Modele te służą do **przekształcania treści strony internetowej w reprezentacje numeryczne zwane wektorami (embeddingami)**. Wektory te oddają znaczenie w sposób, który komputery mogą porównywać i wyszukiwać. Są przechowywane w specjalnej bazie danych, a użytkownicy mogą wybrać, którego modelu embeddingów chcą używać.

- **Baza Wektorowa (Mechanizm Wyszukiwania)**: Ta baza przechowuje **embeddingi zawartości strony internetowej**. Gdy ktoś zada pytanie, NLWeb sprawdza bazę wektorową, by szybko znaleźć najbardziej istotne informacje. Dostarcza listę możliwych odpowiedzi, uporządkowaną według podobieństwa. NLWeb współpracuje z różnymi systemami przechowywania wektorów, takimi jak Qdrant, Snowflake, Milvus, Azure AI Search i Elasticsearch.

### NLWeb na przykładzie

![NLWeb](../../../translated_images/pl/nlweb-diagram.c1e2390b310e5fe4.webp)

Weźmy raz jeszcze naszą stronę do rezerwacji podróży, tym razem zasilaną przez NLWeb.

1. **Przetwarzanie danych**: Istniejące katalogi produktów strony (np. listy lotów, opisy hoteli, pakiety wycieczek) są formatowane za pomocą Schema.org lub ładowane przez kanały RSS. Narzędzia NLWeb pobierają te dane, tworzą embeddingi i przechowują je w lokalnej lub zdalnej bazie wektorowej.

2. **Zapytanie w języku naturalnym (człowiek)**: Użytkownik odwiedza stronę i zamiast przeglądać menu, wpisuje w interfejsie czatu: „Znajdź hotel przyjazny rodzinom w Honolulu z basenem na przyszły tydzień”.

3. **Przetwarzanie przez NLWeb**: Aplikacja NLWeb otrzymuje to zapytanie. Wysyła je do LLM do zrozumienia i równocześnie przeszukuje swoją bazę wektorową w poszukiwaniu odpowiednich hotelowych ofert.

4. **Precyzyjne wyniki**: LLM pomaga zinterpretować wyniki z bazy danych, identyfikując najlepsze dopasowania na podstawie kryteriów „przyjazny rodzinom”, „basen” i „Honolulu”, a następnie formatuje odpowiedź w języku naturalnym. Co ważne, odpowiedź odnosi się do faktycznych hoteli z katalogu strony, unikając wymyślonych informacji.

5. **Interakcja z agentem AI**: Ponieważ NLWeb działa jako serwer MCP, zewnętrzny agent AI podróży może też połączyć się z tym wystąpieniem NLWeb na stronie. Agent AI może użyć metody `ask` z MCP, aby zapytać stronę bezpośrednio: `ask("Czy w okolicy Honolulu są restauracje przyjazne weganom polecane przez hotel?")`. Instancja NLWeb przetworzy to, korzystając z swojej bazy danych restauracji (jeśli załadowana) i zwróci ustrukturyzowaną odpowiedź w formacie JSON.

### Masz więcej pytań o MCP/A2A/NLWeb?

Dołącz do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), aby spotkać innych uczących się, wziąć udział w godzinach konsultacji i uzyskać odpowiedzi na pytania dotyczące agentów AI.

## Zasoby

- [MCP dla początkujących](https://aka.ms/mcp-for-beginners)  
- [Dokumentacja MCP](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Repozytorium NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Przewodniki Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zastrzeżenie**:
Niniejszy dokument został przetłumaczony za pomocą usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Chociaż dokładamy starań, aby tłumaczenie było poprawne, prosimy mieć na uwadze, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w jego języku macierzystym należy uważać za źródło autorytatywne. W przypadku informacji krytycznych zalecane jest skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z korzystania z tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->