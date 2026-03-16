[![Надежные агенты ИИ](../../../translated_images/ru/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Нажмите на изображение выше, чтобы посмотреть видео этого урока)_

# Создание надежных агентов ИИ

## Введение

В этом уроке будут рассмотрены:

- Как создавать и разворачивать безопасных и эффективных агентов ИИ
- Важные соображения по безопасности при разработке агентов ИИ.
- Как сохранять конфиденциальность данных и пользователей при разработке агентов ИИ.

## Цели обучения

После завершения этого урока вы будете знать, как:

- Выявлять и уменьшать риски при создании агентов ИИ.
- Реализовывать меры безопасности, чтобы гарантировать надлежащее управление данными и доступом.
- Создавать агентов ИИ, которые обеспечивают конфиденциальность данных и качественный пользовательский опыт.

## Безопасность

Сначала рассмотрим создание безопасных агентных приложений. Безопасность означает, что AI-агент работает в соответствии с задумкой. Как разработчики агентных приложений, у нас есть методы и инструменты для максимизации безопасности:

### Создание структуры системных сообщений

Если вы когда-либо создавали приложение ИИ с использованием Large Language Models (LLMs), вы знаете важность разработки надежного системного запроса или системного сообщения. Эти подсказки устанавливают метаправила, инструкции и руководящие принципы для того, как LLM будет взаимодействовать с пользователем и данными.

Для агентов ИИ системный запрос еще важнее, поскольку агентам ИИ требуются очень специфические инструкции для выполнения задач, которые мы для них спланировали.

Чтобы создавать масштабируемые системные подсказки, мы можем использовать структуру системных сообщений для построения одного или нескольких агентов в нашем приложении:

![Создание структуры системных сообщений](../../../translated_images/ru/system-message-framework.3a97368c92d11d68.webp)

#### Шаг 1: Создайте мета-системное сообщение 

Мета-подсказка будет использоваться LLM для генерации системных подсказок для создаваемых нами агентов. Мы разрабатываем ее как шаблон, чтобы эффективно создавать несколько агентов при необходимости.

Вот пример мета-системного сообщения, которое мы могли бы дать LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Шаг 2: Создайте базовый запрос

Следующим шагом является создание базового запроса для описания агента ИИ. Вам следует указать роль агента, задачи, которые агент будет выполнять, и любые другие обязанности агента.

Вот пример:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Шаг 3: Передайте базовое системное сообщение LLM

Теперь мы можем оптимизировать это системное сообщение, предоставив мета-системное сообщение в качестве системного сообщения и наше базовое системное сообщение.

Это создаст системное сообщение, которое лучше подходит для руководства нашими агентами ИИ:

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

#### Шаг 4: Итерация и улучшение

Ценность этой структуры системных сообщений заключается в возможности масштабировать создание системных сообщений для нескольких агентов, а также в улучшении ваших системных сообщений со временем. Редко бывает так, что системное сообщение работает идеально с первого раза для всего вашего сценария использования. Возможность вносить небольшие изменения и улучшения, меняя базовое системное сообщение и прогоняя его через систему, позволит вам сравнивать и оценивать результаты.

## Понимание угроз

Чтобы строить надежных агентов ИИ, важно понимать и смягчать риски и угрозы для вашего агента ИИ. Давайте рассмотрим лишь некоторые из различных угроз для агентов ИИ и как вы можете лучше планировать и готовиться к ним.

![Понимание угроз](../../../translated_images/ru/understanding-threats.89edeada8a97fc0f.webp)

### Задачи и инструкции

**Описание:** Злоумышленники пытаются изменить инструкции или цели агента ИИ через подсказки или манипуляцию вводом.

**Смягчение:** Выполняйте проверки валидации и фильтры ввода, чтобы обнаруживать потенциально опасные подсказки до того, как они будут обработаны агентом ИИ. Поскольку эти атаки обычно требуют частого взаимодействия с агентом, ограничение числа ходов в разговоре — еще один способ предотвратить подобные атаки.

### Доступ к критическим системам

**Описание:** Если агент ИИ имеет доступ к системам и сервисам, которые хранят конфиденциальные данные, злоумышленники могут скомпрометировать коммуникацию между агентом и этими сервисами. Это могут быть прямые атаки или косвенные попытки получить информацию об этих системах через агента.

**Смягчение:** Агенты ИИ должны иметь доступ к системам только по необходимости, чтобы предотвратить такие атаки. Коммуникация между агентом и системой также должна быть защищена. Реализация аутентификации и контроля доступа — еще один способ защитить эту информацию.

### Перегрузка ресурсов и сервисов

**Описание:** Агенты ИИ могут обращаться к различным инструментам и сервисам для выполнения задач. Злоумышленники могут воспользоваться этой возможностью, чтобы атаковать эти сервисы, отправляя через агента ИИ большой объем запросов, что может привести к сбоям системы или высоким затратам.

**Смягчение:** Внедрите политики, ограничивающие число запросов, которые агент ИИ может отправлять в сервис. Ограничение числа ходов в разговоре и запросов к вашему агенту ИИ — еще один способ предотвратить такие атаки.

### Отравление базы знаний

**Описание:** Этот тип атаки не нацелен непосредственно на агента ИИ, но нацеливается на базу знаний и другие сервисы, которые агент ИИ будет использовать. Это может включать повреждение данных или информации, которую агент ИИ будет использовать для выполнения задачи, что приведет к предвзятым или непреднамеренным ответам пользователю.

**Смягчение:** Проводите регулярную проверку данных, которые агент ИИ будет использовать в своих рабочих процессах. Убедитесь, что доступ к этим данным защищен и изменения в них вносят только доверенные лица, чтобы избежать такого типа атак.

### Каскадные ошибки

**Описание:** Агенты ИИ обращаются к различным инструментам и сервисам для выполнения задач. Ошибки, вызванные злоумышленниками, могут привести к сбоям других систем, к которым подключен агент ИИ, что делает атаку более масштабной и сложной для устранения.

**Смягчение:** Один из методов избежать этого — заставить агента ИИ работать в ограниченной среде, например, выполнять задачи в контейнере Docker, чтобы предотвратить прямые системные атаки. Создание механизмов резервного копирования и логики повторных попыток при получении ошибок от определенных систем — еще один способ предотвратить крупные сбои системы.

## Человек в цикле

Еще один эффективный способ построить надежные системы агентов ИИ — использование подхода "человек в цикле". Это создает поток, в котором пользователи могут предоставлять обратную связь агентам во время выполнения. Пользователи фактически действуют как агенты в мультиагентной системе, предоставляя подтверждение или прекращение выполняемого процесса.

![Человек в цикле](../../../translated_images/ru/human-in-the-loop.5f0068a678f62f4f.webp)

Вот фрагмент кода с использованием AutoGen, показывающий, как реализуется эта концепция:

```python

# Создайте агентов.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Используйте input() для получения ввода пользователя с консоли.

# Создайте условие завершения, которое завершит разговор, когда пользователь скажет "APPROVE".
termination = TextMentionTermination("APPROVE")

# Создайте команду.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Запустите разговор и выводите его в консоль.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Используйте asyncio.run(...), когда запускаете скрипт.
await Console(stream)

```

## Заключение

Создание надежных агентов ИИ требует тщательного проектирования, надежных мер безопасности и постоянной итерации. Внедряя структурированные системы мета-подсказок, понимая потенциальные угрозы и применяя стратегии их смягчения, разработчики могут создавать агентов ИИ, которые одновременно безопасны и эффективны. Кроме того, включение подхода "человек в цикле" обеспечивает соответствие агентов ИИ потребностям пользователей при минимизации рисков. По мере развития ИИ проактивная позиция в отношении безопасности, конфиденциальности и этических соображений будет ключевой для формирования доверия и надежности систем на основе ИИ.

### Есть ли у вас дополнительные вопросы о создании надежных агентов ИИ?

Присоединяйтесь к [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), чтобы встретиться с другими учениками, посетить часы консультаций и получить ответы на ваши вопросы по агентам ИИ.

## Дополнительные ресурсы

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Обзор ответственного использования ИИ</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Оценка генеративных моделей ИИ и AI-приложений</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Системные сообщения для безопасности</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Шаблон оценки рисков</a>

## Предыдущий урок

[Agentic RAG](../05-agentic-rag/README.md)

## Следующий урок

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Отказ от ответственности:
Этот документ был переведён с помощью сервиса машинного перевода на базе ИИ Co‑op Translator (https://github.com/Azure/co-op-translator). Хотя мы стремимся к точности, имейте в виду, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на его исходном языке следует считать авторитетным источником. Для критически важной информации рекомендуется профессиональный перевод, выполненный человеком. Мы не несем ответственности за любые недоразумения или искажения смысла, возникшие в результате использования этого перевода.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->