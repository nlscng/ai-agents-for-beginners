[![Надійні агенти ШІ](../../../translated_images/uk/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Натисніть на зображення вище, щоб переглянути відео цього уроку)_

# Створення надійних агентів ШІ

## Вступ

У цьому уроці розглядаються:

- Як створювати та розгортати безпечні й ефективні агенти ШІ
- Важливі питання безпеки під час розробки агентів ШІ
- Як забезпечити конфіденційність даних та користувачів під час розробки агентів ШІ

## Цілі навчання

Після завершення цього уроку ви знатимете, як:

- Виявляти та пом'якшувати ризики при створенні агентів ШІ
- Впроваджувати заходи безпеки для належного управління даними та доступом
- Створювати агентів ШІ, які забезпечують конфіденційність даних і якісний досвід користувача

## Безпека

Спочатку розглянемо створення безпечних агентних додатків. Безпека означає, що агент ШІ працює так, як задумано. Як розробники агентних додатків, ми маємо методи та інструменти для максимізації безпеки:

### Побудова каркасу системних повідомлень

Якщо ви коли-небудь створювали застосунок ШІ з використанням великих мовних моделей (LLMs), ви знаєте важливість розробки надійної системної підказки або системного повідомлення. Ці підказки встановлюють метаправила, інструкції та вказівки щодо того, як LLM взаємодіятиме з користувачем і даними.

Для агентів ШІ системна підказка ще важливіша, оскільки агентам ШІ потрібні дуже конкретні інструкції для виконання завдань, які ми для них спроектували.

Щоб створювати масштабовані системні підказки, ми можемо використовувати каркас системних повідомлень для побудови одного або кількох агентів у нашому застосунку:

![Створення рамки системних повідомлень](../../../translated_images/uk/system-message-framework.3a97368c92d11d68.webp)

#### Крок 1: Створіть мета-системне повідомлення

Мета-підказка буде використана LLM для генерації системних підказок для агентів, яких ми створюємо. Ми розробляємо її як шаблон, щоб ефективно створювати кілька агентів за потреби.

Ось приклад мета-системного повідомлення, яке ми б дали LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Крок 2: Створіть базову підказку

Наступний крок — створити базову підказку для опису агента ШІ. Ви повинні включити роль агента, завдання, які агент виконуватиме, та будь-які інші обов'язки агента.

Ось приклад:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Крок 3: Надання базового системного повідомлення LLM

Тепер ми можемо оптимізувати це системне повідомлення, надавши мета-системне повідомлення як системне повідомлення та нашу базову системну підказку.

Це призведе до системного повідомлення, яке краще спроєктоване для керування нашими агентами ШІ:

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

#### Крок 4: Повторюйте та вдосконалюйте

Цінність цього каркасу системних повідомлень полягає в можливості масштабу створення системних повідомлень для кількох агентів, а також у покращенні ваших системних повідомлень з часом. Рідко трапляється, що системне повідомлення працює з першого разу для повного випадку використання. Можливість вносити невеликі зміни та вдосконалення, змінюючи базову системну підказку та проганяючи її через систему, дозволить вам порівнювати й оцінювати результати.

## Розуміння загроз

Щоб створювати надійних агентів ШІ, важливо розуміти та пом'якшувати ризики й загрози для вашого агента ШІ. Розглянемо лише деякі з різних загроз агентам ШІ і як ви можете краще планувати та готуватися до них.

![Розуміння загроз](../../../translated_images/uk/understanding-threats.89edeada8a97fc0f.webp)

### Завдання та інструкції

**Опис:** Зловмисники намагаються змінити інструкції або цілі агента ШІ шляхом підказок або маніпуляцій вхідними даними.

**Заходи пом'якшення**: Виконуйте перевірки валідації та фільтри вхідних даних, щоб виявляти потенційно небезпечні підказки до того, як вони будуть оброблені агентом ШІ. Оскільки ці атаки зазвичай вимагають частої взаємодії з агентом, обмеження кількості ходів у розмові — ще один спосіб запобігти такого роду атакам.

### Доступ до критичних систем

**Опис**: Якщо агент ШІ має доступ до систем і сервісів, які зберігають конфіденційні дані, зловмисники можуть порушити комунікацію між агентом і цими сервісами. Це можуть бути як прямі атаки, так і непрямі спроби отримати інформацію про ці системи через агента.

**Заходи пом'якшення**: Агенти ШІ повинні мати доступ до систем на основі принципу необхідності, щоб запобігти такого роду атакам. Комунікація між агентом і системою також має бути захищеною. Впровадження автентифікації та контролю доступу — ще один спосіб захистити цю інформацію.

### Перевантаження ресурсів і сервісів

**Опис:** Агенти ШІ можуть отримувати доступ до різних інструментів і сервісів для виконання завдань. Зловмисники можуть використовувати цю можливість, щоб атакувати ці сервіси, надсилаючи великий обсяг запитів через агента ШІ, що може призвести до збоїв у системі або великих витрат.

**Заходи пом'якшення:** Впроваджуйте політики, які обмежують кількість запитів, які агент ШІ може направляти до сервісу. Обмеження кількості ходів у розмові та запитів до вашого агента ШІ — ще один спосіб запобігти такого роду атакам.

### Отруєння бази знань

**Опис:** Цей тип атаки не спрямований безпосередньо на агента ШІ, а на базу знань та інші сервіси, які агент ШІ використовує. Це може включати корупцію даних або інформації, яку агент ШІ використовуватиме для виконання завдання, що призведе до упереджених або небажаних відповідей користувачу.

**Заходи пом'якшення:** Регулярно перевіряйте дані, які агент ШІ використовуватиме у своїх робочих процесах. Переконайтеся, що доступ до цих даних захищений і змінюється лише довіреними особами, щоб уникнути цього типу атаки.

### Каскадні помилки

**Опис:** Агенти ШІ звертаються до різних інструментів і сервісів для виконання завдань. Помилки, спричинені зловмисниками, можуть призвести до збоїв інших систем, до яких підключений агент ШІ, що зробить атаку більш масштабною та складною для усунення.

**Заходи пом'якшення**: Один зі способів уникнути цього — змусити агента ШІ працювати в обмеженому середовищі, наприклад виконувати завдання в Docker-контейнері, щоб запобігти прямим атакам на систему. Створення механізмів відкату та логіки повторних спроб, коли певні системи відповідають із помилкою, — ще один спосіб запобігти масштабнішим збоям системи.

## Людина в циклі

Інший ефективний спосіб створення надійних систем агентів ШІ — це використання підходу "людина в циклі". Це створює процес, у якому користувачі можуть надавати відгук агентам під час їх виконання. Користувачі фактично діють як агенти в мультиагентній системі, надаючи підтвердження або зупинку виконуваного процесу.

![Людина в циклі](../../../translated_images/uk/human-in-the-loop.5f0068a678f62f4f.webp)

Ось фрагмент коду з використанням AutoGen, який показує, як реалізується ця концепція:

```python

# Створіть агентів.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Використовуйте input() для отримання введення користувача з консолі.

# Створіть умову завершення, яка припинить розмову, коли користувач скаже "APPROVE".
termination = TextMentionTermination("APPROVE")

# Створіть команду.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Запустіть розмову та виводьте її в консоль в потоковому режимі.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Використовуйте asyncio.run(...), коли запускаєте в скрипті.
await Console(stream)

```

## Висновок

Створення надійних агентів ШІ вимагає ретельного проєктування, надійних заходів безпеки та постійної ітерації. Впроваджуючи структуровані системи мета-підказок, розуміючи потенційні загрози та застосовуючи стратегії пом'якшення, розробники можуть створювати агенти ШІ, які є безпечними та ефективними. Додатково, інтеграція підходу "людина в циклі" забезпечує, що агенти ШІ залишаються узгодженими з потребами користувачів, одночасно мінімізуючи ризики. Оскільки ШІ продовжує розвиватися, підтримка проактивної позиції щодо безпеки, конфіденційності та етичних міркувань буде ключовою для формування довіри та надійності в системах на базі ШІ.

### Маєте ще запитання щодо створення надійних агентів ШІ?

Приєднуйтесь до [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) щоб зустрітися з іншими учнями, відвідати години консультацій і отримати відповіді на свої запитання щодо агентів ШІ.

## Додаткові ресурси

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Огляд відповідального використання ШІ</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Оцінка генеративних моделей ШІ та AI-застосунків</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Системні повідомлення безпеки</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Шаблон оцінки ризиків</a>

## Попередній урок

[Agentic RAG](../05-agentic-rag/README.md)

## Наступний урок

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Відмова від відповідальності**:
Цей документ було перекладено за допомогою сервісу перекладу на основі штучного інтелекту [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, зверніть увагу, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ в його вихідній мові слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується звертатися до професійного людського перекладу. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->