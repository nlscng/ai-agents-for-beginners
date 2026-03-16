[![Projekt wieloagentowy](../../../translated_images/pl/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Kliknij powyższy obraz, aby obejrzeć wideo z tej lekcji)_

# Wzorce projektowe dla systemów wieloagentowych

Jak tylko zaczniesz pracować nad projektem obejmującym wielu agentów, będziesz musiał rozważyć wzorzec projektowy wieloagentowy. Jednak może nie być od razu jasne, kiedy przejść do rozwiązań wieloagentowych i jakie są ich zalety.

## Wprowadzenie

W tej lekcji chcemy odpowiedzieć na następujące pytania:

- W jakich scenariuszach systemy wieloagentowe mają zastosowanie?
- Jakie są zalety używania systemów wieloagentowych w porównaniu z pojedynczym agentem wykonującym wiele zadań?
- Jakie są elementy składowe implementacji wzorca wieloagentowego?
- Jak uzyskać widoczność tego, jak wielokrotni agenci wchodzą ze sobą w interakcje?

## Cele nauki

Po tej lekcji będziesz w stanie:

- Zidentyfikować scenariusze, w których systemy wieloagentowe mają zastosowanie
- Rozpoznać zalety używania systemów wieloagentowych w porównaniu z pojedynczym agentem.
- Zrozumieć elementy składowe implementacji wzorca wieloagentowego.

Jaki jest szerszy kontekst?

*Systemy wieloagentowe to wzorzec projektowy, który pozwala wielu agentom współpracować, aby osiągnąć wspólny cel*.

Ten wzorzec jest szeroko stosowany w różnych dziedzinach, w tym w robotyce, systemach autonomicznych i przetwarzaniu rozproszonym.

## Scenariusze, w których systemy wieloagentowe mają zastosowanie

Zatem w jakich scenariuszach warto stosować systemy wieloagentowe? Odpowiedź jest taka, że istnieje wiele scenariuszy, w których zatrudnienie wielu agentów jest korzystne, zwłaszcza w następujących przypadkach:

- **Duże obciążenia**: Duże obciążenia można podzielić na mniejsze zadania i przydzielić różnym agentom, co umożliwia przetwarzanie równoległe i szybsze ukończenie. Przykładem może być duże zadanie przetwarzania danych.
- **Złożone zadania**: Złożone zadania, podobnie jak duże obciążenia, można rozbić na mniejsze podzadania i przydzielić różnym agentom, z których każdy specjalizuje się w określonym aspekcie zadania. Dobrym przykładem są pojazdy autonomiczne, gdzie różni agenci zarządzają nawigacją, wykrywaniem przeszkód i komunikacją z innymi pojazdami.
- **Różnorodne kompetencje**: Różni agenci mogą mieć zróżnicowane kompetencje, co pozwala im bardziej efektywnie zajmować się różnymi aspektami zadania niż pojedynczy agent. Przykładem może być opieka zdrowotna, gdzie agenci mogą zajmować się diagnostyką, planami leczenia i monitorowaniem pacjenta.

## Zalety stosowania systemów wieloagentowych w porównaniu z pojedynczym agentem

System z pojedynczym agentem może działać dobrze dla prostych zadań, ale dla bardziej złożonych zadań użycie wielu agentów może przynieść kilka korzyści:

- **Specjalizacja**: Każdy agent może być wyspecjalizowany w konkretnym zadaniu. Brak specjalizacji w pojedynczym agencie oznacza, że masz agenta, który potrafi wszystko, ale może się pogubić, gdy stanie przed złożonym zadaniem. Może na przykład końcowo wykonywać zadanie, do którego nie jest najlepiej przystosowany.
- **Skalowalność**: Łatwiej jest skalować systemy przez dodanie kolejnych agentów niż poprzez przeciążanie pojedynczego agenta.
- **Odporność na awarie**: Jeśli jeden agent zawiedzie, inni mogą dalej funkcjonować, co zapewnia niezawodność systemu.

Weźmy przykład: zarezerwujmy podróż dla użytkownika. System z jednym agentem musiałby obsłużyć wszystkie aspekty procesu rezerwacji podróży, od wyszukiwania lotów po rezerwację hoteli i samochodów. Aby osiągnąć to przy użyciu jednego agenta, agent musiałby mieć narzędzia do obsługi wszystkich tych zadań. Mogłoby to prowadzić do złożonego i monolitycznego systemu, który jest trudny w utrzymaniu i skalowaniu. System wieloagentowy, z drugiej strony, mógłby mieć różnych agentów wyspecjalizowanych w wyszukiwaniu lotów, rezerwowaniu hoteli i samochodów. To uczyniłoby system bardziej modułowym, łatwiejszym w utrzymaniu i skalowalnym.

Porównaj to do biura podróży prowadzonego jak małe, rodzinne biuro versus biura podróży działającego w modelu franczyzowym. W pierwszym przypadku jeden agent zajmowałby się wszystkimi aspektami procesu rezerwacji podróży, podczas gdy w modelu franczyzowym różni agenci zajmowaliby się różnymi aspektami procesu rezerwacji.

## Elementy składowe implementacji wzorca wieloagentowego

Zanim będziesz mógł zaimplementować wzorzec wieloagentowy, musisz zrozumieć elementy składowe, które tworzą ten wzorzec.

Uczyńmy to bardziej konkretnym, ponownie rozważając przykład rezerwacji podróży dla użytkownika. W tym przypadku elementy składowe obejmowałyby:

- **Komunikacja agentów**: Agenci wyszukujący loty, rezerwujący hotele i samochody muszą się komunikować i dzielić informacjami o preferencjach i ograniczeniach użytkownika. Musisz zdecydować o protokołach i metodach tej komunikacji. Co to oznacza w praktyce, to że agent wyszukujący loty musi komunikować się z agentem rezerwującym hotele, aby zapewnić, że hotel jest zarezerwowany na te same daty co lot. Oznacza to, że agenci muszą dzielić się informacjami o datach podróży użytkownika, co znaczy, że musisz zdecydować *które agenty udostępniają informacje i w jaki sposób je udostępniają*.
- **Mechanizmy koordynacji**: Agenci muszą koordynować swoje działania, aby zapewnić spełnienie preferencji i ograniczeń użytkownika. Preferencją użytkownika może być chęć posiadania hotelu blisko lotniska, podczas gdy ograniczeniem może być to, że samochody wynajmowane są tylko na lotnisku. To oznacza, że agent rezerwujący hotele musi koordynować się z agentem rezerwującym samochody, aby upewnić się, że preferencje i ograniczenia użytkownika są spełnione. Musisz zdecydować *jak agenty koordynują swoje działania*.
- **Architektura agenta**: Agenci muszą mieć wewnętrzną strukturę umożliwiającą podejmowanie decyzji i uczenie się na podstawie interakcji z użytkownikiem. To oznacza, że agent wyszukujący loty musi mieć strukturę wewnętrzną umożliwiającą podejmowanie decyzji o tym, które loty polecić użytkownikowi. Musisz zdecydować *jak agenty podejmują decyzje i uczą się na podstawie interakcji z użytkownikiem*. Przykłady sposobów, w jakie agent się uczy i poprawia, mogą obejmować użycie modelu uczenia maszynowego przez agenta wyszukującego loty do rekomendowania lotów użytkownikowi w oparciu o jego wcześniejsze preferencje.
- **Widoczność interakcji między agentami**: Musisz mieć widoczność tego, jak wiele agentów wchodzi ze sobą w interakcje. To oznacza, że potrzebujesz narzędzi i technik do śledzenia aktywności i interakcji agentów. Może to przyjmować formę narzędzi do logowania i monitorowania, narzędzi wizualizacyjnych i metryk wydajności.
- **Wzorce wieloagentowe**: Istnieją różne wzorce implementacji systemów wieloagentowych, takie jak architektury scentralizowane, zdecentralizowane i hybrydowe. Musisz zdecydować o wzorcu, który najlepiej pasuje do Twojego przypadku użycia.
- **Człowiek w pętli**: W większości przypadków w procesie uczestniczy człowiek i musisz wskazać agentom, kiedy mają prosić o interwencję człowieka. Może to przyjmować formę użytkownika proszącego o konkretny hotel lub lot, którego agenci nie polecili, lub prośby o potwierdzenie przed dokonaniem rezerwacji lotu czy hotelu.

## Widoczność interakcji między agentami

Ważne jest, aby mieć widoczność tego, jak wiele agentów wchodzi ze sobą w interakcje. Ta widoczność jest niezbędna do debugowania, optymalizacji i zapewnienia ogólnej skuteczności systemu. Aby to osiągnąć, potrzebujesz narzędzi i technik do śledzenia aktywności i interakcji agentów. Może to przyjmować formę narzędzi do logowania i monitorowania, narzędzi wizualizacyjnych i metryk wydajności.

Na przykład w przypadku rezerwacji podróży dla użytkownika możesz mieć pulpit nawigacyjny, który pokazuje status każdego agenta, preferencje i ograniczenia użytkownika oraz interakcje między agentami. Ten pulpit może pokazywać daty podróży użytkownika, loty rekomendowane przez agenta lotów, hotele rekomendowane przez agenta hotelowego oraz samochody rekomendowane przez agenta ds. wynajmu samochodów. Daje to jasny obraz tego, jak agenci współdziałają i czy preferencje oraz ograniczenia użytkownika są spełniane.

Przyjrzyjmy się każdemu z tych aspektów bardziej szczegółowo.

- **Narzędzia do logowania i monitorowania**: Chcesz rejestrować logi dla każdej akcji podjętej przez agenta. Wpis w logu mógłby przechowywać informacje o agencie, który wykonał akcję, wykonanej akcji, czasie jej wykonania oraz wyniku akcji. Te informacje mogą być następnie wykorzystane do debugowania, optymalizacji i innych działań.
- **Narzędzia wizualizacyjne**: Narzędzia wizualizacyjne mogą pomóc w zobaczeniu interakcji między agentami w bardziej intuicyjny sposób. Na przykład możesz mieć graf pokazujący przepływ informacji między agentami. Może to pomóc zidentyfikować wąskie gardła, nieefektywności i inne problemy w systemie.
- **Metryki wydajności**: Metryki wydajności mogą pomóc śledzić efektywność systemu wieloagentowego. Na przykład możesz śledzić czas potrzebny na wykonanie zadania, liczbę zadań wykonanych na jednostkę czasu oraz trafność rekomendacji dokonywanych przez agentów. Te informacje mogą pomóc zidentyfikować obszary do poprawy i zoptymalizować system.

## Wzorce wieloagentowe

Przyjrzyjmy się kilku konkretnym wzorcom, które można wykorzystać do tworzenia aplikacji wieloagentowych. Oto kilka interesujących wzorców wartych rozważenia:

### Czat grupowy

Ten wzorzec jest przydatny, gdy chcesz stworzyć aplikację czatu grupowego, w której wielu agentów może ze sobą komunikować. Typowe przypadki użycia tego wzorca obejmują współpracę zespołową, obsługę klienta i serwisy społecznościowe.

W tym wzorcu każdy agent reprezentuje użytkownika w czacie grupowym, a wiadomości są wymieniane między agentami za pomocą protokołu komunikacyjnego. Agenci mogą wysyłać wiadomości do czatu grupowego, otrzymywać wiadomości z czatu i odpowiadać na wiadomości od innych agentów.

Ten wzorzec można zaimplementować przy użyciu architektury scentralizowanej, gdzie wszystkie wiadomości są przekierowywane przez centralny serwer, lub architektury zdecentralizowanej, gdzie wiadomości są wymieniane bezpośrednio.

![Czat grupowy](../../../translated_images/pl/multi-agent-group-chat.ec10f4cde556babd.webp)

### Przekazanie zadań

Ten wzorzec jest przydatny, gdy chcesz stworzyć aplikację, w której wielu agentów może przekazywać sobie zadania.

Typowe przypadki użycia tego wzorca obejmują obsługę klienta, zarządzanie zadaniami i automatyzację przepływów pracy.

W tym wzorcu każdy agent reprezentuje zadanie lub krok w przepływie pracy, a agenci mogą przekazywać zadania innym agentom na podstawie zdefiniowanych reguł.

![Przekazanie](../../../translated_images/pl/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Filtrowanie kolaboracyjne

Ten wzorzec jest przydatny, gdy chcesz stworzyć aplikację, w której wielu agentów może współpracować przy tworzeniu rekomendacji dla użytkowników.

Powód, dla którego warto, aby wielu agentów współpracowało, polega na tym, że każdy agent może mieć inną wiedzę specjalistyczną i może przyczynić się do procesu rekomendacji na różne sposoby.

Weźmy przykład, gdzie użytkownik chce rekomendacji najlepszego akcji do kupienia na giełdzie.

- **Ekspert branżowy**:. Jeden agent mógłby być ekspertem w konkretnej branży.
- **Analiza techniczna**: Inny agent mógłby być ekspertem w analizie technicznej.
- **Analiza fundamentalna**: a kolejny agent mógłby być ekspertem w analizie fundamentalnej. Współpracując, ci agenci mogą dostarczyć użytkownikowi bardziej kompleksową rekomendację.

![Rekomendacja](../../../translated_images/pl/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenariusz: proces zwrotu

Rozważ scenariusz, w którym klient próbuje uzyskać zwrot za produkt — w tym procesie może uczestniczyć całkiem sporo agentów, ale podzielmy je na agentów specyficznych dla tego procesu oraz ogólnych agentów, którzy mogą być używani w innych procesach.

**Agenty specyficzne dla procesu zwrotu**:

Poniżej znajdują się niektóre agenty, które mogłyby być zaangażowane w proces zwrotu:

- **Agent klienta**: Ten agent reprezentuje klienta i jest odpowiedzialny za zainicjowanie procesu zwrotu.
- **Agent sprzedawcy**: Ten agent reprezentuje sprzedawcę i jest odpowiedzialny za przetwarzanie zwrotu.
- **Agent płatności**: Ten agent reprezentuje proces płatności i jest odpowiedzialny za zwrócenie płatności klientowi.
- **Agent ds. rozwiązywania problemów**: Ten agent reprezentuje proces rozwiązywania i jest odpowiedzialny za rozwiązywanie wszelkich problemów, które pojawią się podczas procesu zwrotu.
- **Agent ds. zgodności**: Ten agent reprezentuje proces zgodności i jest odpowiedzialny za zapewnienie, że proces zwrotu jest zgodny z przepisami i politykami.

**Agenty ogólne**:

Te agenty mogą być używane przez inne części Twojego biznesu.

- **Agent ds. wysyłki**: Ten agent reprezentuje proces wysyłki i jest odpowiedzialny za odesłanie produktu do sprzedawcy. Ten agent może być używany zarówno w procesie zwrotu, jak i do ogólnej wysyłki produktu przy zakupie.
- **Agent opinii**: Ten agent reprezentuje proces zbierania opinii i jest odpowiedzialny za zbieranie informacji zwrotnej od klienta. Opinie mogą być zbierane w dowolnym momencie, nie tylko podczas procesu zwrotu.
- **Agent eskalacji**: Ten agent reprezentuje proces eskalacji i jest odpowiedzialny za przekazywanie problemów na wyższy poziom wsparcia. Tego typu agenta możesz użyć w każdym procesie, gdzie potrzebna jest eskalacja problemu.
- **Agent powiadomień**: Ten agent reprezentuje proces powiadomień i jest odpowiedzialny za wysyłanie powiadomień do klienta na różnych etapach procesu zwrotu.
- **Agent analityczny**: Ten agent reprezentuje proces analityczny i jest odpowiedzialny za analizowanie danych związanych z procesem zwrotu.
- **Agent audytu**: Ten agent reprezentuje proces audytu i jest odpowiedzialny za audyt procesu zwrotu, aby upewnić się, że jest on przeprowadzany prawidłowo.
- **Agent raportowania**: Ten agent reprezentuje proces raportowania i jest odpowiedzialny za generowanie raportów dotyczących procesu zwrotu.
- **Agent wiedzy**: Ten agent reprezentuje proces zarządzania wiedzą i jest odpowiedzialny za utrzymywanie bazy wiedzy związanej z procesem zwrotu. Ten agent mógłby posiadać wiedzę zarówno o zwrotach, jak i o innych częściach Twojego biznesu.
- **Agent ds. bezpieczeństwa**: Ten agent reprezentuje proces bezpieczeństwa i jest odpowiedzialny za zapewnienie bezpieczeństwa procesu zwrotu.
- **Agent jakości**: Ten agent reprezentuje proces kontroli jakości i jest odpowiedzialny za zapewnienie jakości procesu zwrotu.

Wcześniej wymieniono dość dużo agentów, zarówno specyficznych dla procesu zwrotu, jak i ogólnych agentów, którzy mogą być wykorzystywani w innych częściach Twojego biznesu. Mamy nadzieję, że daje to wyobrażenie o tym, jak możesz zdecydować, których agentów użyć w swoim systemie wieloagentowym.

## Zadanie

Zaprojektuj system wieloagentowy dla procesu obsługi klienta. Zidentyfikuj agenty zaangażowane w proces, ich role i odpowiedzialności oraz sposób, w jaki wchodzą ze sobą w interakcje. Weź pod uwagę zarówno agenty specyficzne dla procesu obsługi klienta, jak i ogólnych agentów, którzy mogą być używani w innych częściach Twojego biznesu.
> Zastanów się, zanim przeczytasz poniższe rozwiązanie — może być potrzebnych więcej agentów, niż myślisz.
> WSKAZÓWKA: Pomyśl o różnych etapach procesu obsługi klienta, a także rozważ agentów potrzebnych dla każdego systemu.

## Rozwiązanie

[Rozwiązanie](./solution/solution.md)

## Sprawdzenie wiedzy

Pytanie: Kiedy należy rozważyć użycie multi-agentów?

- [ ] A1: Gdy masz małe obciążenie i proste zadanie.
- [ ] A2: Gdy masz duże obciążenie.
- [ ] A3: Gdy masz proste zadanie.

[Quiz rozwiązania](./solution/solution-quiz.md)

## Podsumowanie

W tej lekcji przyjrzeliśmy się wzorcowi projektowemu multi-agent, w tym scenariuszom, w których multi-agenci mają zastosowanie, zaletom korzystania z wielu agentów zamiast pojedynczego agenta, elementom składowym implementacji wzorca multi-agent oraz sposobom uzyskania wglądu w to, jak wielu agentów wchodzi ze sobą w interakcje.

### Masz więcej pytań dotyczących wzorca projektowego multi-agent?

Dołącz do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), aby spotkać się z innymi uczącymi się, uczestniczyć w dyżurach i uzyskać odpowiedzi na pytania dotyczące Twoich Agentów AI.

## Dodatkowe zasoby

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Wzorce projektowe AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Wzorce projektowe agentowe</a>


## Poprzednia lekcja

[Projektowanie planów](../07-planning-design/README.md)

## Następna lekcja

[Metapoznanie w agentach AI](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Zastrzeżenie:
Niniejszy dokument został przetłumaczony przy użyciu usługi tłumaczenia opartej na sztucznej inteligencji Co-op Translator (https://github.com/Azure/co-op-translator). Chociaż dokładamy starań, aby tłumaczenie było jak najbardziej rzetelne, należy pamiętać, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku źródłowym należy traktować jako wersję wiążącą. W przypadku informacji kluczowych zalecane jest skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z użycia tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->