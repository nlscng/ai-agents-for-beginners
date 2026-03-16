[![Поуздани AI агенти](../../../translated_images/sr/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Кликните на горњу слику да бисте погледали видео о овој лекцији)_

# Прављење поузданих AI агената

## Увод

Ова лекција ће обрадити:

- Како изградити и имплементирати безбедне и ефикасне AI агенте
- Важне безбедносне аспекте приликом развоја AI агената.
- Како одржавати поверљивост података и корисника током развоја AI агената.

## Циљеви учења

Након завршетка ове лекције, знаћете како да:

- Идентификујете и ублажите ризике приликом креирања AI агената.
- Спроведете безбедносне мере како бисте осигурали правилно управљање подацима и приступом.
- Креирате AI агенте који одржавају поверљивост података и пружају квалитетно корисничко искуство.

## Безбедност

Прво да погледамо изградњу безбедних агенцијских апликација. Безбедност значи да AI агент функционише према предвиђеном. Као творци агенцијских апликација, имамо методе и алате за максимизирање безбедности:

### Изградња оквира системске поруке

Ако сте икада градили AI апликацију користећи Велике Језичке Моделе (LLMs), знате колико је важно дизајнирати робусну системску поруку или системски упит. Ови упити успостављају мета правила, инструкције и смернице за то како ће LLM комуницирати са корисником и подацима.

За AI агенте, системски упит је још важнији јер ће AI агенти требати веома специфичне инструкције да обаве задатке које смо за њих дизајнирали.

Да бисмо креирали скалабилне системске упите, можемо користити оквир системске поруке за изградњу једног или више агената у нашој апликацији:

![Изградња оквира системске поруке](../../../translated_images/sr/system-message-framework.3a97368c92d11d68.webp)

#### Корак 1: Креирајте мета системску поруку

Мета упит ће користити LLM за генерисање системских упита за агенте које креирамо. Дизајнирамо га као шаблон да бисмо ефикасно креирали више агената ако је потребно.

Ево примера мета системске поруке коју бисмо дали LLM-у:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Корак 2: Направите основни упит

Следећи корак је креирати основни упит који описује AI агента. Треба укључити улогу агента, задатке које ће агент обављати и све друге одговорности агента.

Ево примера:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Корак 3: Обезбедите Основну Системску Поруку LLM-у

Сада можемо оптимизовати ову системску поруку тако што ћемо обезбедити мета системску поруку као системску поруку и нашу основну системску поруку.

Ово ће произвести системску поруку боље дизајнирану за усмеравање наших AI агената:

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

#### Корак 4: Итерација и побољшање

Вредност овог оквира системске поруке је у могућности лакшег скалирања креирања системских порука од више агената као и побољшања ваших системских порука током времена. Ретко ћете имати системску поруку која функционише од првог пута за ваш целокупан случај употребе. Могућност да направите мале измене и побољшања мењајући основну системску поруку и покрећући је кроз систем омогућиће вам да упоредите и процените резултате.

## Разумевање претњи

Да бисте изградили поуздане AI агенте, важно је разумети и ублажити ризике и претње вашем AI агенту. Погледајмо само неке од различитих претњи AI агената и како боље планирати и припремити се за њих.

![Разумевање претњи](../../../translated_images/sr/understanding-threats.89edeada8a97fc0f.webp)

### Задатак и инструкциија

**Опис:** Нападачи покушавају да промене инструкције или циљеве AI агента преко упита или манипулације улазима.

**Ублажавање**: Извршавајте провере валидности и филтре улаза да бисте открили потенцијално опасне упите пре него што их AI агент обради. Пошто ови напади обично захтевају честу интеракцију са агентом, ограничавање броја корака у разговору је још један начин да се спрече ове врсте напада.

### Приступ критичним системима

**Опис**: Ако AI агент има приступ системима и услугама које чувају осетљиве податке, нападачи могу угрожавати комуникацију између агента и тих услуга. То могу бити директни напади или индиректни покушаји да се преко агента добију информације о тим системима.

**Ублажавање**: AI агенти треба да имају приступ системима само када је то потребно да би се спречили овакви напади. Комуникација између агента и система треба такође да буде безбедна. Имплементација аутентификације и контроле приступа је још један начин да се заштите овe информације.

### Преоптерећење ресурса и услуга

**Опис:** AI агенти могу приступити различитим алатима и услугама да би обавили задатке. Нападачи могу злоупотребити ову способност тако што шаљу велики број захтева преко AI агента, што може резултирати кваровима система или високим трошковима.

**Ублажавање:** Имплементирајте политике за ограничење броја захтева које AI агент може упутити одређеној услузи. Ограничење броја корака у разговору и захтева према вашем AI агенту је још један начин да се спрече ове врсте напада.

### Тровање базе знања

**Опис:** Овај тип напада не циља директно AI агента већ базу знања и друге услуге које ће AI агент користити. То може укључивати корупцију података или информација које ће AI агент користити да би обавио задатак, што може довести до пристрасних или непредвиђених одговора кориснику.

**Ублажавање:** Редовно вршите верификацију података које ће AI агент користити у својим радним процесима. Осигурајте да приступ овим подацима буде безбедан и да их мењају само поуздане особе како бисте избегли ову врсту напада.

### Каскадне грешке

**Опис:** AI агенти приступају различитим алатима и услугама да би обавили задатке. Грешке изазване нападима могу довести до кварова других система повезаних са AI агентом, чинећи напад распрострањенијим и тежим за решавање.

**Ублажавање**: Један од начина да се избегне ово је да AI агент ради у ограниченом окружењу, као што је извршавање задатака у Docker контејнеру, како би се спречили директни напади на систем. Градња резервних механизама и логике поновних покушаја када одређени системи одговоре са грешком је још један начин да се спрече већи кварови система.

## Човек у петљи

Још један ефикасан начин да се изградe поуздани AI агенцијски системи је коришћење човека у петљи. Ово ствара ток у којем корисници могу пружити повратне информације агентима током извршавања. Корисници у основи делују као агенти у мулти-агенцијском систему и пружају одобрење или прекид рада процеса.

![Човек у петљи](../../../translated_images/sr/human-in-the-loop.5f0068a678f62f4f.webp)

Ево фрагмента кода који користи AutoGen да прикаже како се овај концепт имплементира:

```python

# Креирај агенте.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Користи input() за унос података од корисника преко конзоле.

# Креирај услов за прекид који ће завршити разговор када корисник каже "APPROVE".
termination = TextMentionTermination("APPROVE")

# Креирај тим.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Покрени разговор и емитуј у конзолу.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Користи asyncio.run(...) када покрећеш у скрипти.
await Console(stream)

```

## Закључак

Прављење поузданих AI агената захтева пажљив дизајн, робусне безбедносне мере и континуирано унапређење. Имплементацијом структуираних мета система упита, разумевањем потенцијалних претњи и применом стратегија ублажавања, програмери могу креирати AI агенте који су и безбедни и ефикасни. Поред тога, укључивање приступа са човеком у петљи осигурава да AI агенти остају усклађени са потребама корисника уз минимизирање ризика. Како AI наставља да се развија, одржавање проактивног става према безбедности, приватности и етичким аспектима биће кључно за изградњу поверења и поузданости у системе вођене AI-ом.

### Имате још питања о прављењу поузданих AI агената?

Придружите се [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) за сусрет са другим ученицима, посећивање радног времена и добијање одговора на ваша питања о AI агентима.

## Додатни ресурси

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Преглед одговорне употребе AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Евалуација модела генеративног AI и AI апликација</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Системске поруке за безбедност</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Шаблон процене ризика</a>

## Претходна лекција

[Агенцијски RAG](../05-agentic-rag/README.md)

## Следећа лекција

[Образац за планирање](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ограничење одговорности**:  
Овај документ је преведен уз помоћ AI преводилачке услуге [Co-op Translator](https://github.com/Azure/co-op-translator). Иако се трудимо да превод буде прецизан, имајте у виду да аутоматизовани преводи могу садржати грешке или нетачности. Оригинални документ на његовом изворном језику треба сматрати ауторитетним извором. За критичне информације препоручује се професионални људски превод. Нисмо одговорни за било какве неспоразуме или погрешна тумачења која произилазе из употребе овог превода.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->