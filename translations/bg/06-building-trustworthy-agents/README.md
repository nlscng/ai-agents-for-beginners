[![Достоверни AI агенти](../../../translated_images/bg/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Кликнете върху изображението по-горе, за да гледате видеото на този урок)_

# Изграждане на достоверни AI агенти

## Въведение

Този урок ще обхване:

- Как да изградим и внедрим безопасни и ефективни AI агенти
- Важни съображения за сигурността при разработката на AI агенти
- Как да поддържаме поверителността на данните и потребителите при разработка на AI агенти

## Учебни цели

След завършване на този урок ще можете да:

- Идентифицирате и намалявате рисковете при създаване на AI агенти
- Прилагате мерки за сигурност, за да се гарантира правилното управление на данните и достъпа
- Създавате AI агенти, които поддържат поверителността на данните и осигуряват качествен потребителски опит

## Безопасност

Нека първо разгледаме изграждането на безопасни агентни приложения. Безопасността означава, че AI агентът изпълнява задачите си както е проектиран. Като разработчици на агентни приложения, имаме методи и инструменти за максимизиране на безопасността:

### Изграждане на рамка за системни съобщения

Ако някога сте изграждали AI приложение с помощта на големи езикови модели (LLM), знаете колко е важно да се проектира стабилен системен prompt или системно съобщение. Тези prompts задават мета правилата, инструкциите и насоките за това как LLM ще взаимодейства с потребителя и с данните.

За AI агентите системният prompt е още по-важен, тъй като AI агентите ще се нуждаят от много конкретни инструкции за изпълнение на задачите, които сме им определили.

За да създадем мащабируеми системни prompts, можем да използваме рамка за системни съобщения за изграждане на един или повече агенти в нашето приложение:

![Изграждане на рамка за системни съобщения](../../../translated_images/bg/system-message-framework.3a97368c92d11d68.webp)

#### Стъпка 1: Създаване на мета системно съобщение

Мета prompt-а ще се използва от LLM, за да генерира системните prompts за агентите, които създаваме. Проектираме го като шаблон, за да можем ефективно да създаваме множество агенти при нужда.

Ето пример за мета системно съобщение, което бихме дали на LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Стъпка 2: Създаване на базов prompt

Следващата стъпка е да се създаде базов prompt, който описва AI агента. Трябва да включите ролята на агента, задачите, които ще изпълнява, и други отговорности на агента.

Ето пример:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Стъпка 3: Осигуряване на базово системно съобщение към LLM

Сега можем да оптимизираме това системно съобщение чрез предоставяне на мета системното съобщение като системно съобщение и нашето базово системно съобщение.

Това ще генерира системно съобщение, което е по-добре проектирано за насочване на нашите AI агенти:

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

#### Стъпка 4: Итерация и подобрение

Стойността на тази рамка за системни съобщения е да се улесни създаването на системни съобщения от множество агенти, както и подобряването им с течение на времето. Рядко ще имате системно съобщение, което работи перфектно от първия път за вашия пълен случай на употреба. Възможността за малки корекции и подобрения чрез промяна на базовото системно съобщение и провеждането му през системата ще ви позволи да сравнявате и оценявате резултатите.

## Разбиране на заплахите

За да изградите достоверни AI агенти, е важно да разберете и да намалите рисковете и заплахите за вашия AI агент. Нека разгледаме само някои от различните заплахи за AI агентите и как можете по-добре да планирате и подготвите защитата срещу тях.

![Разбиране на заплахите](../../../translated_images/bg/understanding-threats.89edeada8a97fc0f.webp)

### Задача и инструкция

**Описание:** Атакуващите се опитват да променят инструкциите или целите на AI агента чрез подсказване или манипулиране на входните данни.

**Облекчаване:** Изпълнявайте проверки за валидност и филтрирани входове, за да откривате потенциално опасни подсказки преди те да бъдат обработени от AI агента. Тъй като тези атаки обикновено изискват честа интеракция с агента, ограничаването на броя на ходовете в разговор е друг начин да се предотвратят такива атаки.

### Достъп до критични системи

**Описание:** Ако AI агентът има достъп до системи и услуги, които съхраняват чувствителни данни, атакуващите могат да компрометират комуникацията между агента и тези услуги. Това могат да бъдат директни атаки или косвени опити за получаване на информация за тези системи чрез агента.

**Облекчаване:** AI агентите трябва да имат достъп до системите само при необходимост, за да се предотвратят такива атаки. Комуникацията между агента и системата също трябва да бъде защитена. Прилагането на автентикация и контрол на достъпа е друг начин за защита на тази информация.

### Презареждане на ресурси и услуги

**Описание:** AI агентите могат да използват различни инструменти и услуги за изпълнение на задачи. Атакуващите могат да използват тази способност, за да нападнат тези услуги чрез изпращане на голям обем заявки чрез AI агента, което може да доведе до сривове на системата или високи разходи.

**Облекчаване:** Прилагайте политики за ограничаване на броя на заявките, които AI агент може да прави към услуга. Ограничаването на броя на ходовете в разговор и заявките към вашия AI агент е друг начин да се предотвратят такива атаки.

### Отравяне на база знания

**Описание:** Този вид атака не е насочена директно към AI агента, а към базата знания и други услуги, които AI агентът ще използва. Това може да включва повреждане на данните или информацията, които AI агентът ще използва за изпълнение на задачи, водещо до пристрастни или нежелани отговори към потребителя.

**Облекчаване:** Извършвайте редовна проверка на данните, които AI агентът ще използва в своите работни процеси. Осигурете, че достъпът до тези данни е защитен и се променя само от доверени лица, за да се избегне този тип атака.

### Последователни грешки

**Описание:** AI агентите използват различни инструменти и услуги за изпълнение на задачи. Грешките, предизвикани от атакуващи, могат да доведат до повреди в други системи, свързани с AI агента, което прави атаката по-широка и по-трудна за отстраняване.

**Облекчаване:** Един метод да се избегне това е AI агентът да оперира в ограничена среда, например чрез изпълнение на задачи в Docker контейнер, за да се предотвратят директни атаки върху системата. Създаването на механизми за резервен план и логика за повторение при грешки от определени системи е друг начин да се избегнат по-големи системни сривове.

## Човек в цикъла

Друг ефективен начин за изграждане на достоверни AI агентни системи е използването на „човек в цикъла“. Това създава поток, в който потребителите могат да предоставят обратна връзка на агентите по време на изпълнението. Потребителите ефективно действат като агенти в многоагентна система и чрез даване на одобрение или прекратяване на текущия процес.

![Човек в цикъла](../../../translated_images/bg/human-in-the-loop.5f0068a678f62f4f.webp)

Ето примерен код, използващ AutoGen, който показва как се прилага този концепт:

```python

# Създайте агентите.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Използвайте input() за получаване на вход от потребителя в конзолата.

# Създайте условие за прекратяване, което ще приключи разговора, когато потребителят каже "APPROVE".
termination = TextMentionTermination("APPROVE")

# Създайте екипа.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Стартирайте разговора и предавайте поточно към конзолата.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Използвайте asyncio.run(...), когато стартирате в скрипт.
await Console(stream)

```

## Заключение

Изграждането на достоверни AI агенти изисква внимателно проектиране, стабилни мерки за сигурност и непрекъсната итерация. Чрез прилагане на структурирани системи за мета подсказване, разбиране на потенциалните заплахи и прилагане на стратегии за намаляване на рисковете, разработчиците могат да създадат AI агенти, които са както безопасни, така и ефективни. Освен това, включването на подход „човек в цикъла“ гарантира, че AI агентите остават съобразени с нуждите на потребителите, като същевременно минимизират рисковете. С развитието на AI поддържането на проактивен подход към сигурността, поверителността и етичните съображения ще бъде ключово за изграждането на доверие и надеждност в AI базираните системи.

### Имате още въпроси относно изграждането на достоверни AI агенти?

Присъединете се към [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), за да се срещнете с други обучаващи се, да посетите консултативни часове и да получите отговори на вашите въпроси за AI агенти.

## Допълнителни ресурси

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Преглед на отговорно използване на AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Оценка на генеративни AI модели и AI приложения</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Системни съобщения за безопасност</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Шаблон за оценка на риска</a>

## Предишен урок

[Agentic RAG](../05-agentic-rag/README.md)

## Следващ урок

[Патърн за проектиране на планиране](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Отказ от отговорност**:
Този документ е преведен с помощта на AI преводаческа услуга [Co-op Translator](https://github.com/Azure/co-op-translator). Въпреки че се стремим към точност, моля, имайте предвид, че автоматизираните преводи могат да съдържат грешки или неточности. Оригиналният документ на неговия роден език трябва да се счита за авторитетен източник. За критична информация се препоръчва професионален човешки превод. Ние не носим отговорност за каквито и да е недоразумения или неправилни тълкувания, възникнали от използването на този превод.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->