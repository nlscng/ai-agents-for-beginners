[![Wprowadzenie do Agentów AI](../../../translated_images/pl/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Kliknij powyższy obraz, aby obejrzeć film z tej lekcji)_


# Wprowadzenie do Agentów AI i Przypadków Użycia Agentów

Witamy na kursie "Agenci AI dla Początkujących"! Kurs ten dostarcza podstawową wiedzę i przykłady zastosowań do budowy Agentów AI.

Dołącz do <a href="https://discord.gg/kzRShWzttr" target="_blank">Społeczności Azure AI na Discordzie</a>, aby poznać innych uczących się i twórców Agentów AI oraz zadać wszelkie pytania dotyczące tego kursu.

Aby rozpocząć ten kurs, zaczynamy od lepszego zrozumienia, czym są Agenci AI i jak możemy ich używać w aplikacjach i przepływach pracy, które tworzymy.

## Wprowadzenie

Ta lekcja obejmuje:

- Czym są Agenci AI i jakie są różne typy agentów?
- Do jakich zastosowań najlepiej nadają się Agenci AI i jak mogą nam pomóc?
- Jakie są podstawowe elementy konstrukcyjne przy projektowaniu rozwiązań Agentycznych?

## Cele Nauki
Po ukończeniu tej lekcji powinieneś być w stanie:

- Zrozumieć koncepcje Agentów AI i czym różnią się od innych rozwiązań AI.
- Wydajnie stosować Agentów AI.
- Projektować produktywnie rozwiązania agentyczne zarówno dla użytkowników, jak i klientów.

## Definicja Agentów AI i Typy Agentów AI

### Czym są Agenci AI?

Agenci AI to **systemy**, które umożliwiają **dużym modelom językowym (LLM)** **wykonywanie działań**, rozszerzając ich możliwości poprzez udostępnianie LLM **dostępu do narzędzi** i **wiedzy**.

Rozbijmy tę definicję na mniejsze części:

- **System** - ważne jest, aby myśleć o agentach nie tylko jako o pojedynczym komponencie, ale jako o systemie wielu komponentów. Na podstawowym poziomie, komponenty Agenta AI to:
  - **Środowisko** - zdefiniowana przestrzeń, w której działa Agent AI. Na przykład, jeśli mamy agenta do rezerwacji podróży, środowiskiem może być system rezerwacji podróży, z którego agent korzysta do realizacji zadań.
  - **Czujniki** - środowisko posiada informacje i zapewnia informacje zwrotne. Agenci AI używają czujników do zbierania i interpretacji tych informacji o aktualnym stanie środowiska. W przykładzie Agenta Rezerwacji Podróży, system rezerwacji może dostarczać informacje takie jak dostępność hoteli czy ceny lotów.
  - **Wykonawcy działań (aktuatory)** - gdy Agent AI otrzyma aktualny stan środowiska, określa, jaką akcję podjąć, aby zmienić środowisko dla aktualnego zadania. Dla agenta rezerwacji podróży może to być zarezerwowanie dostępnego pokoju dla użytkownika.

![Czym są Agenci AI?](../../../translated_images/pl/what-are-ai-agents.1ec8c4d548af601a.webp)

**Duże Modele Językowe** - koncepcja agentów istniała przed stworzeniem LLM. Zaletą budowania Agentów AI z użyciem LLM jest ich zdolność do interpretacji języka ludzkiego i danych. Ta zdolność pozwala LLM interpretować informacje środowiskowe i definiować plan zmiany środowiska.

**Wykonywanie Działań** - poza systemami Agentów AI, LLM są ograniczone do sytuacji, gdzie działanie polega na generowaniu treści lub informacji na podstawie zapytania użytkownika. W systemach Agentów AI, LLM mogą realizować zadania przez interpretację żądania użytkownika i użycie dostępnych narzędzi w ich środowisku.

**Dostęp Do Narzędzi** - narzędzia, do których LLM ma dostęp, są definiowane przez 1) środowisko, w którym działa, oraz 2) dewelopera Agenta AI. W naszym przykładzie agenta podróży, narzędzia agenta są ograniczone przez operacje dostępne w systemie rezerwacji, a deweloper może ograniczyć dostęp narzędzi do lotów.

**Pamięć+Wiedza** - pamięć może mieć charakter krótkoterminowy w kontekście rozmowy między użytkownikiem a agentem. Długoterminowo, poza informacjami dostarczonymi przez środowisko, Agenci AI mogą również pobierać wiedzę z innych systemów, usług, narzędzi, a nawet innych agentów. W przykładzie agenta podróży, ta wiedza mogłaby obejmować informacje o preferencjach podróżnych użytkownika znajdujące się w bazie danych klientów.

### Różne typy agentów

Teraz, gdy mamy ogólną definicję Agentów AI, spójrzmy na niektóre specyficzne typy agentów i jak można je zastosować w agencie rezerwującym podróże.

| **Typ Agenta**                 | **Opis**                                                                                                                           | **Przykład**                                                                                                                                                                                                                    |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Proste Agenty Refleksyjne** | Wykonują natychmiastowe działania na podstawie zdefiniowanych reguł.                                                              | Agent podróży interpretuje kontekst e-maila i przekazuje skargi dotyczące podróży do obsługi klienta.                                                                                                                          |
| **Agenty Refleksyjne Oparte na Modelu** | Wykonują działania na podstawie modelu świata i zmian w tym modelu.                                                      | Agent podróży priorytetyzuje trasy z istotnymi zmianami cen na podstawie dostępu do danych historycznych cen.                                                                                                                  |
| **Agenty Oparte na Celach**    | Tworzą plany do osiągnięcia określonych celów, interpretując cel i ustalając działania do jego realizacji.                      | Agent podróży rezerwuje podróż, ustalając niezbędne ustalenia podróżne (samochód, transport publiczny, loty) od aktualnej lokalizacji do celu.                                                                                   |
| **Agenty Oparte na Użyteczności** | Rozważają preferencje i wagę kompromisów liczbowo, aby określić, jak osiągnąć cele.                                       | Agent podróży maksymalizuje użyteczność, rozważając wygodę versus koszt podczas rezerwacji podróży.                                                                                                                            |
| **Agenty Uczące się**          | Ulepszają się z czasem, reagując na informacje zwrotne i odpowiednio dostosowując działania.                                      | Agent podróży poprawia się, korzystając z opinii klientów z ankiet po podróży, aby dokonać korekt przyszłych rezerwacji.                                                                                                       |
| **Agenty Hierarchiczne**       | Zawierają wiele agentów w systemie warstwowym, gdzie agenty wyższego poziomu dzielą zadania na podzadania dla agentów niższego poziomu. | Agent podróży anuluje podróż, dzieląc zadanie na podzadania (np. anulowanie konkretnych rezerwacji) i zlecając ich wykonanie agentom niższego poziomu, którzy raportują do agenta wyższego poziomu.                              |
| **Systemy Wieloagentowe (MAS)**| Agenty wykonują zadania niezależnie, współpracując lub konkurując.                                                                | Współpraca: Wielu agentów rezerwuje konkretne usługi podróżne, takie jak hotele, loty i rozrywka. Konkurencja: Wielu agentów zarządza i konkuruje o wspólny kalendarz rezerwacji hotelu, obsługując klientów hotelu.            |

## Kiedy używać Agentów AI

W wcześniejszej części użyliśmy przypadku Agenta Podróży, aby wyjaśnić, jak różne typy agentów mogą być stosowane w różnych scenariuszach rezerwacji podróży. Kontynuujemy używanie tej aplikacji przez cały kurs.

Spójrzmy na typy zastosowań, do których Agenci AI nadają się najlepiej:

![Kiedy używać Agentów AI?](../../../translated_images/pl/when-to-use-ai-agents.54becb3bed74a479.webp)

- **Problemy Otwarte** - pozwalające LLM określać potrzebne kroki do wykonania zadania, ponieważ nie zawsze mogą być one na stałe zakodowane w przepływie pracy.
- **Procesy Wieloetapowe** - zadania wymagające poziomu złożoności, w których Agent AI musi używać narzędzi lub informacji przez wiele etapów zamiast jednorazowego pobierania.
- **Poprawa Z Upływem Czasu** - zadania, w których agent może się ulepszać, otrzymując informacje zwrotne ze środowiska lub od użytkowników, aby zapewnić lepszą użyteczność.

Więcej rozważań na temat używania Agentów AI omówimy w lekcji Budowanie Godnych Zaufania Agentów AI.

## Podstawy Rozwiązań Agentycznych

### Tworzenie Agentów

Pierwszym krokiem w projektowaniu systemu Agenta AI jest zdefiniowanie narzędzi, działań i zachowań. W tym kursie skupiamy się na użyciu **Azure AI Agent Service** do definiowania naszych Agentów. Oferuje on funkcje takie jak:

- Wybór modeli otwartych, takich jak OpenAI, Mistral i Llama
- Korzystanie z licencjonowanych danych dostarczanych przez dostawców, takich jak Tripadvisor
- Korzystanie ze standardowych narzędzi OpenAPI 3.0

### Wzorce Agentyczne

Komunikacja z LLM odbywa się poprzez zapytania (prompt). Ze względu na półautonomiczną naturę Agentów AI, nie zawsze jest możliwe lub konieczne ręczne ponowne wysyłanie zapytania do LLM po zmianie w środowisku. Używamy **wzorców agentycznych**, które pozwalają na zadawanie zapytań LLM wieloetapowo w sposób bardziej skalowalny.

Ten kurs jest podzielony na niektóre z aktualnie popularnych wzorców agentycznych.

### Frameworki Agentyczne

Frameworki Agentyczne umożliwiają deweloperom implementację wzorców agentycznych za pomocą kodu. Frameworki te oferują szablony, wtyczki i narzędzia do lepszej współpracy Agentów AI. Korzyści te zapewniają możliwości lepszej obserwowalności i diagnozowania systemów Agentów AI.

W tym kursie zbadamy oparte na badaniach frameworki AutoGen oraz produkcyjnie gotowy framework Agent od Semantic Kernel.

## Przykładowe Kody

- Python: [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## Masz Więcej Pytań o Agentach AI?

Dołącz do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), aby spotkać innych uczących się, uczestniczyć w godzinach konsultacji i uzyskać odpowiedzi na swoje pytania o Agentach AI.

## Poprzednia Lekcja

[Konfiguracja Kursu](../00-course-setup/README.md)

## Następna Lekcja

[Eksploracja Frameworków Agentycznych](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zastrzeżenie**:
Niniejszy dokument został przetłumaczony za pomocą usługi tłumaczenia AI [Co-op Translator](https://github.com/Azure/co-op-translator). Chociaż dokładamy starań, aby tłumaczenie było jak najbardziej precyzyjne, prosimy mieć na uwadze, że automatyczne tłumaczenia mogą zawierać błędy lub niedokładności. Oryginalny dokument w jego rodzimym języku powinien być uznawany za źródło wiarygodne i autorytatywne. W przypadku informacji o kluczowym znaczeniu zalecane jest skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z korzystania z tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->