# Pamięć dla Agentów AI  
[![Agent Memory](../../../translated_images/pl/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Podczas omawiania unikalnych korzyści związanych z tworzeniem Agentów AI, głównie dyskutuje się o dwóch aspektach: zdolności do wywoływania narzędzi do realizacji zadań oraz zdolności do samodoskonalenia się. Pamięć stanowi fundament tworzenia agenta samodoskonalącego się, który może tworzyć lepsze doświadczenia dla naszych użytkowników.

W tej lekcji przyjrzymy się, czym jest pamięć dla Agentów AI oraz jak możemy nią zarządzać i wykorzystywać ją na korzyść naszych aplikacji.

## Wprowadzenie

Ta lekcja obejmie:

• **Zrozumienie pamięci Agenta AI**: Czym jest pamięć i dlaczego jest istotna dla agentów.

• **Implementacja i przechowywanie pamięci**: Praktyczne metody dodawania funkcji pamięci do twoich agentów AI, ze szczególnym uwzględnieniem pamięci krótkotrwałej i długotrwałej.

• **Uczynienie agentów AI samodoskonalącymi się**: Jak pamięć umożliwia agentom uczenie się na podstawie wcześniejszych interakcji i ulepszanie się z upływem czasu.

## Dostępne implementacje

Ta lekcja zawiera dwa wszechstronne poradniki-notatniki:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementuje pamięć przy użyciu Mem0 oraz Azure AI Search z frameworkiem Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementuje strukturalną pamięć z użyciem Cognee, automatycznie budując graf wiedzy oparty na embeddingach, wizualizując graf i inteligentne wyszukiwanie

## Cele nauki

Po ukończeniu tej lekcji będziesz potrafił:

• **Rozróżniać różne typy pamięci agenta AI**, w tym pamięć roboczą, krótkoterminową i długoterminową, a także specjalistyczne formy jak pamięć persona i epizodyczna.

• **Implementować i zarządzać pamięcią krótkoterminową i długoterminową dla agentów AI** przy użyciu frameworka Semantic Kernel, wykorzystując narzędzia takie jak Mem0, Cognee, pamięć typu Whiteboard oraz integrując z Azure AI Search.

• **Zrozumieć zasady stojące za samodoskonalącymi się agentami AI** oraz jak solidne systemy zarządzania pamięcią przyczyniają się do ciągłego uczenia się i adaptacji.

## Zrozumienie pamięci Agenta AI

W swojej istocie **pamięć dla agentów AI odnosi się do mechanizmów, które pozwalają im przechowywać i przypominać informacje**. Informacje te mogą zawierać konkretne szczegóły rozmowy, preferencje użytkownika, wcześniejsze działania lub nawet wyuczone wzorce.

Bez pamięci aplikacje AI często są bezstanowe, co oznacza, że każda interakcja zaczyna się od zera. Prowadzi to do powtarzalnego i frustrującego doświadczenia użytkownika, gdzie agent „zapomina” wcześniejszy kontekst lub preferencje.

### Dlaczego pamięć jest ważna?

Inteligencja agenta jest głęboko związana z jego zdolnością do przypominania i wykorzystywania informacji z przeszłości. Pamięć pozwala agentom być:

• **Refleksyjni**: Uczyć się na podstawie wcześniejszych działań i rezultatów.

• **Interakcyjni**: Utrzymywać kontekst w trakcie trwającej rozmowy.

• **Proaktywni i reaktywni**: Przewidywać potrzeby lub odpowiednio reagować na podstawie danych historycznych.

• **Autonomiczni**: Działać bardziej niezależnie, korzystając z przechowywanej wiedzy.

Celem implementacji pamięci jest uczynienie agentów bardziej **wiarygodnymi i efektywnymi**.

### Rodzaje pamięci

#### Pamięć robocza

Można ją porównać do kawałka kartki, z której agent korzysta podczas pojedynczego, trwającego zadania lub procesu myślowego. Zawiera natychmiastowe informacje potrzebne do wykonania następnego kroku.

Dla agentów AI, pamięć robocza często przechwytuje najistotniejsze informacje z rozmowy, nawet jeśli pełna jej historia jest długa lub przycięta. Skupia się na wydobyciu kluczowych elementów, takich jak wymagania, propozycje, decyzje i działania.

**Przykład pamięci roboczej**

W agencie do rezerwacji podróży pamięć robocza może przechwycić aktualne żądanie użytkownika, np. „Chcę zarezerwować wycieczkę do Paryża”. To konkretne wymaganie jest utrzymywane w kontekście agenta, aby ukierunkować bieżącą interakcję.

#### Pamięć krótkoterminowa

Ten typ pamięci przechowuje informacje przez czas trwania pojedynczej rozmowy lub sesji. To jest kontekst bieżącego czatu, pozwalający agentowi odwoływać się do wcześniejszych wypowiedzi w dialogu.

**Przykład pamięci krótkoterminowej**

Jeśli użytkownik zapyta „Ile kosztuje lot do Paryża?” a następnie zapyta „A co z zakwaterowaniem tam?”, pamięć krótkoterminowa zapewnia, że agent wie, iż „tam” odnosi się do „Paryża” w ramach tej samej rozmowy.

#### Pamięć długoterminowa

To informacje, które utrzymują się pomiędzy wieloma rozmowami lub sesjami. Pozwala agentom pamiętać preferencje użytkownika, wcześniejsze interakcje lub ogólną wiedzę przez dłuższy czas. Jest to ważne dla personalizacji.

**Przykład pamięci długoterminowej**

Pamięć długoterminowa może przechowywać fakt, że „Ben lubi narciarstwo i aktywności na świeżym powietrzu, pije kawę z widokiem na góry i unika zaawansowanych tras narciarskich z powodu dawnej kontuzji”. Te informacje, zdobyte z wcześniejszych interakcji, wpływają na rekomendacje podczas przyszłych sesji planowania podróży, czyniąc je bardzo spersonalizowanymi.

#### Pamięć persona

Ten specjalistyczny typ pamięci pomaga agentowi rozwijać spójną „osobowość” lub „personę”. Pozwala agentowi pamiętać szczegóły o sobie lub swojej roli, co sprawia, że interakcje są bardziej płynne i skupione.

**Przykład pamięci persona**

Jeśli agent podróży jest zaprojektowany jako „ekspert od planowania narciarskiego”, pamięć persona może wzmacniać tę rolę, wpływając na odpowiedzi zgodne z tonem i wiedzą eksperta.

#### Pamięć Workflow/Epizodyczna

Ta pamięć przechowuje sekwencję kroków, które agent wykonuje podczas złożonego zadania, włączając w to sukcesy i porażki. To jak pamiętanie konkretnych „epizodów” lub doświadczeń, aby z nich wyciągać naukę.

**Przykład pamięci epizodycznej**

Jeśli agent próbował zarezerwować określony lot, ale się to nie powiodło z powodu braku dostępności, pamięć epizodyczna może to zanotować, pozwalając agentowi spróbować alternatywnych lotów lub poinformować użytkownika o problemie w lepszy sposób podczas kolejnej próby.

#### Pamięć encji

Polega na wyodrębnianiu i zapamiętywaniu konkretnych encji (jak osoby, miejsca czy rzeczy) oraz zdarzeń z rozmów. Pozwala agentowi budować uporządkowane rozumienie kluczowych elementów omawianych w rozmowie.

**Przykład pamięci encji**

Z rozmowy o przeszłej podróży agent może wydobyć encje takie jak „Paryż”, „Wieża Eiffla” i „kolacja w restauracji Le Chat Noir”. W przyszłej interakcji agent może przypomnieć sobie „Le Chat Noir” i zaoferować dokonanie nowej rezerwacji.

#### Strukturalny RAG (Retrieval Augmented Generation)

Chociaż RAG to szersza technika, „Strukturalny RAG” jest wyróżniany jako potężna technologia pamięci. Wydobywa gęste, strukturalne informacje z różnych źródeł (rozmowy, e-maile, obrazy) i wykorzystuje je, by zwiększyć precyzję, przypominanie oraz szybkość odpowiedzi. W przeciwieństwie do klasycznego RAG, który opiera się wyłącznie na podobieństwie semantycznym, Strukturalny RAG korzysta z inherentnej struktury informacji.

**Przykład Strukturalnego RAG**

Zamiast tylko dopasowywać słowa kluczowe, Strukturalny RAG może przeanalizować szczegóły lotu (cel, data, godzina, linia lotnicza) z e-maila i zapisać je w uporządkowany sposób. Pozwala to na precyzyjne zapytania typu „Jaki lot zarezerwowałem do Paryża we wtorek?”

## Implementacja i przechowywanie pamięci

Implementacja pamięci dla agentów AI obejmuje systematyczny proces **zarządzania pamięcią**, który zawiera generowanie, przechowywanie, wyszukiwanie, integrowanie, aktualizowanie, a nawet „zapominanie” (czyli usuwanie) informacji. Wyszukiwanie jest szczególnie istotnym aspektem.

### Specjalistyczne narzędzia pamięciowe

#### Mem0

Jednym ze sposobów przechowywania i zarządzania pamięcią agenta jest użycie specjalistycznych narzędzi, takich jak Mem0. Mem0 działa jako warstwa pamięci trwałej, pozwalając agentom przypominać sobie istotne interakcje, przechowywać preferencje użytkownika i faktyczny kontekst oraz uczyć się na podstawie sukcesów i porażek z upływem czasu. Idea jest taka, że agenci bezstanowi zmieniają się w stanowych.

Działa to poprzez **dwufazowy proces pamięci: ekstrakcję i aktualizację**. Najpierw wiadomości dodane do wątku agenta są wysyłane do usługi Mem0, która wykorzystuje Duży Model Językowy (LLM) do zsumowania historii rozmowy i ekstrakcji nowych wspomnień. Następnie faza aktualizacji sterowana przez LLM decyduje, czy dodać, zmodyfikować lub usunąć te wspomnienia, zapisując je w hybrydowej bazie danych, która może zawierać bazy wektorowe, grafowe i klucz-wartość. System ten obsługuje też różne typy pamięci i może integrować pamięć grafową do zarządzania relacjami między encjami.

#### Cognee

Innym potężnym podejściem jest użycie **Cognee** — otwartoźródłowej semantycznej pamięci dla agentów AI, która przekształca dane ustrukturyzowane i nieustrukturyzowane w zapytalne grafy wiedzy oparte na embeddingach. Cognee oferuje **architekturę dual-store** łączącą wyszukiwanie wektorowe z relacjami grafowymi, pozwalając agentom rozumieć nie tylko podobieństwo informacji, lecz także wzajemne powiązania koncepcji.

Wyróżnia się w **hybrydowym wyszukiwaniu**, które łączy podobieństwo wektorowe, strukturę grafu oraz rozumowanie LLM — od prostego wyszukiwania fragmentów do zadawania pytań świadomych grafu. System utrzymuje **żywą pamięć**, która ewoluuje i rośnie, pozostając jednocześnie zapytalna jako jeden połączony graf, wspierając zarówno kontekst sesji krótkoterminowej, jak i pamięć trwałą długoterminową.

Poradnik-notatnik Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstruje budowę tej zunifikowanej warstwy pamięci, z praktycznymi przykładami wprowadzania różnorodnych źródeł danych, wizualizacji grafu wiedzy oraz zapytań z zastosowaniem różnych strategii wyszukiwania dostosowanych do konkretnych potrzeb agenta.

### Przechowywanie pamięci z RAG

Poza specjalistycznymi narzędziami pamięciowymi takimi jak mem0, możesz wykorzystać zaawansowane usługi wyszukiwania, takie jak **Azure AI Search, jako backend do przechowywania i wyszukiwania wspomnień**, zwłaszcza w przypadku strukturalnego RAG.

Pozwala to ugruntować odpowiedzi twojego agenta na własnych danych, zapewniając bardziej trafne i dokładne odpowiedzi. Azure AI Search może być używany do przechowywania pamięci użytkownika dotyczących podróży, katalogów produktów lub innej specjalistycznej wiedzy.

Azure AI Search wspiera funkcje takie jak **Strukturalny RAG**, który świetnie nadaje się do wydobywania i przywoływania gęstych, strukturalnych informacji z dużych zbiorów danych, takich jak historie rozmów, e-maile czy nawet obrazy. Zapewnia to „ponadludzką” precyzję i przypominanie w porównaniu do tradycyjnych metod cięcia tekstu i embeddingu.

## Uczynienie agentów AI samodoskonalącymi się

Typowym wzorcem dla agentów samodoskonalących się jest wprowadzenie **„agenta wiedzy”**. Ten oddzielny agent obserwuje główną rozmowę pomiędzy użytkownikiem a agentem podstawowym. Jego zadania to:

1. **Identyfikacja cennych informacji**: Określenie, czy jakaś część rozmowy jest warta zachowania jako wiedza ogólna lub konkretna preferencja użytkownika.

2. **Ekstrakcja i podsumowanie**: Wyodrębnienie istotnych nauk lub preferencji z rozmowy.

3. **Przechowywanie w bazie wiedzy**: Zapis tych informacji, często w bazie wektorowej, aby mogły być później wyszukane.

4. **Wzbogacanie przyszłych zapytań**: Gdy użytkownik inicjuje nowe zapytanie, agent wiedzy pobiera istotne przechowywane informacje i dołącza je do promptu użytkownika, dostarczając kluczowy kontekst agentowi podstawowemu (podobnie do RAG).

### Optymalizacje pamięci

• **Zarządzanie opóźnieniami**: Aby nie spowalniać interakcji użytkownika, na początku można użyć tańszego, szybszego modelu, który szybko oceni, czy informacja jest warta zapisania lub przywołania, a bardziej złożony proces ekstrakcji/wyszukiwania wywołać tylko wtedy, gdy jest to potrzebne.

• **Utrzymanie bazy wiedzy**: Dla rosnącej bazy wiedzy, rzadziej używane informacje mogą być przenoszone do „zimnego magazynu” celem obniżenia kosztów.

## Masz więcej pytań dotyczących pamięci agentów?

Dołącz do [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), aby spotkać innych uczących się, uczestniczyć w godzinach konsultacji i uzyskać odpowiedzi na pytania dotyczące Agentów AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Niniejszy dokument został przetłumaczony za pomocą usługi tłumaczeń AI [Co-op Translator](https://github.com/Azure/co-op-translator). Chociaż dążymy do dokładności, prosimy mieć na uwadze, że automatyczne tłumaczenia mogą zawierać błędy lub nieścisłości. Oryginalny dokument w języku źródłowym powinien być uznawany za autorytatywne źródło. W przypadku informacji o istotnym znaczeniu zaleca się skorzystanie z profesjonalnego tłumaczenia wykonanego przez człowieka. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z użycia tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->