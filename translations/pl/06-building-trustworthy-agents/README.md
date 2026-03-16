[![Godne zaufania agenty AI](../../../translated_images/pl/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Kliknij powyższy obraz, aby obejrzeć wideo z tej lekcji)_

# Budowanie godnych zaufania agentów AI

## Wprowadzenie

Ta lekcja obejmie:

- Jak budować i wdrażać bezpieczne oraz skuteczne agenty AI
- Ważne zagadnienia związane z bezpieczeństwem podczas tworzenia agentów AI
- Jak utrzymywać prywatność danych i użytkowników podczas tworzenia agentów AI

## Cele nauki

Po ukończeniu tej lekcji będziesz wiedzieć, jak:

- Identyfikować i łagodzić ryzyka przy tworzeniu agentów AI
- Wdrażać środki bezpieczeństwa zapewniające właściwe zarządzanie danymi i dostępem
- Tworzyć agentów AI, którzy zachowują prywatność danych i zapewniają wysoką jakość doświadczenia użytkownika

## Bezpieczeństwo

Najpierw przyjrzyjmy się budowaniu bezpiecznych aplikacji agentowych. Bezpieczeństwo oznacza, że agent AI działa zgodnie z założeniami. Jako twórcy aplikacji agentowych mamy metody i narzędzia, aby maksymalizować bezpieczeństwo:

### Budowanie ram komunikatów systemowych

Jeśli kiedykolwiek budowałeś aplikację AI używając dużych modeli językowych (LLM), wiesz, jak ważne jest zaprojektowanie solidnego system prompta lub komunikatu systemowego. Te promptu ustalają meta reguły, instrukcje i wytyczne dotyczące tego, jak LLM będzie się komunikować z użytkownikiem i danymi.

Dla agentów AI komunikat systemowy jest jeszcze ważniejszy, ponieważ agenty AI będą potrzebowały bardzo szczegółowych instrukcji, aby wykonać zaprojektowane dla nich zadania.

Aby tworzyć skalowalne komunikaty systemowe, możemy użyć ram komunikatu systemowego do tworzenia jednego lub więcej agentów w naszej aplikacji:

![Tworzenie ram komunikatów systemowych](../../../translated_images/pl/system-message-framework.3a97368c92d11d68.webp)

#### Krok 1: Utwórz meta komunikat systemowy

Meta prompt będzie używany przez LLM do generowania komunikatów systemowych dla agentów, których tworzymy. Projektujemy go jako szablon, aby móc efektywnie tworzyć wielu agentów w razie potrzeby.

Oto przykład meta komunikatu systemowego, który przekazalibyśmy LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Krok 2: Utwórz podstawowy prompt

Następnym krokiem jest stworzenie podstawowego prompta opisującego Agenta AI. Powinieneś uwzględnić rolę agenta, zadania, które agent będzie wykonywał, oraz inne obowiązki agenta.

Oto przykład:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Krok 3: Przekaż podstawowy komunikat systemowy do LLM

Teraz możemy zoptymalizować ten komunikat systemowy, podając meta komunikat systemowy jako komunikat systemowy oraz nasz podstawowy komunikat systemowy.

To wygeneruje komunikat systemowy, który będzie lepiej zaprojektowany do prowadzenia naszych agentów AI:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Krok 4: Iteruj i ulepszaj

Wartość tych ram komunikatów systemowych polega na tym, że umożliwiają one skalowanie tworzenia komunikatów systemowych dla wielu agentów oraz ulepszanie komunikatów systemowych w czasie. Rzadko zdarza się, że komunikat systemowy działa idealnie za pierwszym razem dla całego przypadku użycia. Możliwość wprowadzania drobnych poprawek przez zmianę podstawowego komunikatu systemowego i uruchamianie go przez system pozwoli ci porównać i ocenić wyniki.

## Zrozumienie zagrożeń

Aby zbudować godne zaufania agenty AI, ważne jest zrozumienie i łagodzenie ryzyk oraz zagrożeń dla twojego agenta AI. Przyjrzyjmy się niektórym z różnych zagrożeń dla agentów AI i temu, jak lepiej się na nie przygotować.

![Zrozumienie zagrożeń](../../../translated_images/pl/understanding-threats.89edeada8a97fc0f.webp)

### Zadanie i instrukcja

**Opis:** Atakujący próbują zmienić instrukcje lub cele agenta AI poprzez promptowanie lub manipulowanie wejściami.

**Łagodzenie**: Wykonuj kontrole walidacyjne i filtry wejściowe, aby wykrywać potencjalnie niebezpieczne promptu przed ich przetworzeniem przez agenta AI. Ponieważ tego typu ataki zwykle wymagają częstej interakcji z agentem, ograniczenie liczby tur w rozmowie jest kolejnym sposobem zapobiegania tego typu atakom.

### Dostęp do krytycznych systemów

**Opis**: Jeśli agent AI ma dostęp do systemów i usług przechowujących wrażliwe dane, atakujący mogą naruszyć komunikację między agentem a tymi usługami. Mogą to być ataki bezpośrednie lub pośrednie próby uzyskania informacji o tych systemach przez agenta.

**Łagodzenie**: Agenty AI powinny mieć dostęp do systemów tylko w razie potrzeby, aby zapobiec tego typu atakom. Komunikacja między agentem a systemem powinna być również zabezpieczona. Wdrożenie uwierzytelniania i kontroli dostępu to kolejny sposób ochrony tych informacji.

### Przeciążenie zasobów i usług

**Opis:** Agenty AI mogą uzyskiwać dostęp do różnych narzędzi i usług, aby wykonywać zadania. Atakujący mogą wykorzystać tę możliwość do atakowania tych usług, wysyłając dużą liczbę żądań przez agenta AI, co może prowadzić do awarii systemu lub wysokich kosztów.

**Łagodzenie:** Wdroż polityki ograniczające liczbę żądań, które agent AI może wysyłać do usługi. Ograniczenie liczby tur rozmowy i żądań do twojego agenta AI to kolejny sposób zapobiegania tego typu atakom.

### Zatrucie bazy wiedzy

**Opis:** Ten rodzaj ataku nie celuje bezpośrednio w agenta AI, lecz w bazę wiedzy i inne usługi, z których agent AI będzie korzystał. Może to polegać na uszkodzeniu danych lub informacji, których agent AI użyje do wykonania zadania, prowadząc do stronniczych lub niezamierzonych odpowiedzi dla użytkownika.

**Łagodzenie:** Regularnie weryfikuj dane, z których agent AI będzie korzystał w swoich przepływach pracy. Upewnij się, że dostęp do tych danych jest zabezpieczony i może być zmieniany tylko przez zaufane osoby, aby uniknąć tego typu ataku.

### Błędy kaskadowe

**Opis:** Agenty AI uzyskują dostęp do różnych narzędzi i usług w celu wykonywania zadań. Błędy spowodowane przez atakujących mogą prowadzić do awarii innych systemów, z którymi agent AI jest połączony, powodując, że atak staje się bardziej rozległy i trudniejszy do zdiagnozowania.

**Łagodzenie**: Jednym ze sposobów uniknięcia tego jest uruchamianie agenta AI w ograniczonym środowisku, na przykład wykonywanie zadań w kontenerze Docker, aby zapobiec bezpośrednim atakom na system. Tworzenie mechanizmów awaryjnych i logiki ponownych prób, gdy niektóre systemy odpowiadają błędem, to kolejny sposób zapobiegania większym awariom systemu.

## Człowiek w pętli

Innym skutecznym sposobem budowania godnych zaufania systemów agentowych jest użycie podejścia Człowiek w pętli. Tworzy to przepływ, w którym użytkownicy mogą przekazywać opinię agentom podczas działania. Użytkownicy w zasadzie działają jako agenci w systemie wieloagentowym, zatwierdzając lub przerywając procesy w trakcie działania.

![Człowiek w pętli](../../../translated_images/pl/human-in-the-loop.5f0068a678f62f4f.webp)

Poniżej znajduje się fragment kodu używający AutoGen, pokazujący, jak to pojęcie jest wdrażane:

```python

# Utwórz agentów.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Użyj input(), aby pobrać dane wejściowe od użytkownika z konsoli.

# Utwórz warunek zakończenia, który zakończy rozmowę, gdy użytkownik powie "APPROVE".
termination = TextMentionTermination("APPROVE")

# Utwórz zespół.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Uruchom rozmowę i strumieniuj ją do konsoli.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Użyj asyncio.run(...), gdy uruchamiasz skrypt.
await Console(stream)

```

## Podsumowanie

Budowanie godnych zaufania agentów AI wymaga starannego projektowania, solidnych środków bezpieczeństwa i ciągłej iteracji. Poprzez wdrożenie ustrukturyzowanych systemów meta promptów, zrozumienie potencjalnych zagrożeń i zastosowanie strategii łagodzenia, deweloperzy mogą tworzyć agentów AI, którzy są zarówno bezpieczni, jak i skuteczni. Dodatkowo włączenie podejścia człowieka w pętli zapewnia, że agenty AI pozostają zgodne z potrzebami użytkowników przy jednoczesnym minimalizowaniu ryzyka. W miarę jak AI będzie się rozwijać, utrzymanie proaktywnego podejścia do bezpieczeństwa, prywatności i kwestii etycznych będzie kluczowe dla budowania zaufania i niezawodności systemów napędzanych przez AI.

### Masz więcej pytań dotyczących budowania godnych zaufania agentów AI?

Dołącz do [Discord Microsoft Foundry](https://aka.ms/ai-agents/discord), aby spotkać innych uczących się, uczestniczyć w godzinach konsultacji i uzyskać odpowiedzi na pytania dotyczące twoich agentów AI.

## Dodatkowe zasoby

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Przegląd zasad odpowiedzialnego AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Ocena modeli generatywnej AI i aplikacji AI</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Komunikaty systemowe dotyczące bezpieczeństwa</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Szablon oceny ryzyka</a>

## Poprzednia lekcja

[Agentic RAG](../05-agentic-rag/README.md)

## Następna lekcja

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Zastrzeżenie:
Niniejszy dokument został przetłumaczony przy użyciu usługi tłumaczeń opartych na sztucznej inteligencji Co-op Translator (https://github.com/Azure/co-op-translator). Chociaż dążymy do dokładności, prosimy pamiętać, że tłumaczenia automatyczne mogą zawierać błędy lub niedokładności. Oryginalny dokument w języku źródłowym należy uznać za wersję wiążącą. W przypadku informacji istotnych zalecane jest skorzystanie z usług profesjonalnego tłumacza. Nie ponosimy odpowiedzialności za jakiekolwiek nieporozumienia lub błędne interpretacje wynikające z korzystania z tego tłumaczenia.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->