[![Pålitliga AI-agenter](../../../translated_images/sv/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klicka på bilden ovan för att se videon av denna lektion)_

# Bygga pålitliga AI-agenter

## Introduktion

Den här lektionen kommer att täcka:

- Hur man bygger och distribuerar säkra och effektiva AI-agenter
- Viktiga säkerhetsaspekter vid utveckling av AI-agenter.
- Hur man upprätthåller data- och användarintegritet vid utveckling av AI-agenter.

## Inlärningsmål

Efter att ha genomfört denna lektion kommer du att kunna:

- Identifiera och minska risker vid skapande av AI-agenter.
- Implementera säkerhetsåtgärder för att säkerställa korrekt hantering av data och åtkomst.
- Skapa AI-agenter som bibehåller dataintegritet och erbjuder en kvalitativ användarupplevelse.

## Säkerhet

Låt oss först titta på att bygga säkra agentbaserade applikationer. Säkerhet innebär att AI-agenten presterar som avsett. Som byggare av agentbaserade applikationer har vi metoder och verktyg för att maximera säkerheten:

### Bygga ett systemmeddelanderamverk

Om du någonsin byggt en AI-applikation med stora språkmodeller (LLM) vet du hur viktigt det är att designa en robust systemprompt eller systemmeddelande. Dessa prompts etablerar metaregler, instruktioner och riktlinjer för hur LLM ska interagera med användaren och data.

För AI-agenter är systemprompten ännu viktigare eftersom AI-agenterna behöver mycket specifika instruktioner för att slutföra de uppgifter vi designat för dem.

För att skapa skalbara systemprompter kan vi använda ett systemmeddelanderamverk för att bygga en eller flera agenter i vår applikation:

![Bygga ett systemmeddelanderamverk](../../../translated_images/sv/system-message-framework.3a97368c92d11d68.webp)

#### Steg 1: Skapa ett meta systemmeddelande

Meta-prompten kommer att användas av en LLM för att generera systemprompter för de agenter vi skapar. Vi designar den som en mall så att vi effektivt kan skapa flera agenter vid behov.

Här är ett exempel på ett meta systemmeddelande vi skulle ge till LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Steg 2: Skapa en grundläggande prompt

Nästa steg är att skapa en grundläggande prompt för att beskriva AI-agenten. Du bör inkludera agentens roll, de uppgifter agenten ska utföra och eventuella andra ansvarsområden för agenten.

Här är ett exempel:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Steg 3: Ge grundläggande systemmeddelande till LLM

Nu kan vi optimera detta systemmeddelande genom att tillhandahålla meta systemmeddelandet som systemmeddelande och vårt grundläggande systemmeddelande.

Detta kommer att producera ett systemmeddelande som är bättre utformat för att vägleda våra AI-agenter:

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

#### Steg 4: Iterera och förbättra

Värdet med detta systemmeddelanderamverk är att kunna skala skapandet av systemmeddelanden från flera agenter enklare samt förbättra dina systemmeddelanden över tid. Det är sällsynt att du får ett systemmeddelande som fungerar första gången för hela ditt användningsfall. Att kunna göra små justeringar och förbättringar genom att ändra det grundläggande systemmeddelandet och köra det genom systemet gör att du kan jämföra och utvärdera resultat.

## Förstå hot

För att skapa pålitliga AI-agenter är det viktigt att förstå och minska risker och hot mot din AI-agent. Låt oss titta på några av de olika hoten mot AI-agenter och hur du bättre kan planera för och förbereda dig för dem.

![Förstå hot](../../../translated_images/sv/understanding-threats.89edeada8a97fc0f.webp)

### Uppgift och instruktion

**Beskrivning:** Angripare försöker ändra instruktionerna eller målen för AI-agenten genom att ge prompts eller manipulera input.

**Motåtgärd:** Utför valideringskontroller och filtrering av input för att upptäcka potentiellt farliga prompts innan de behandlas av AI-agenten. Eftersom dessa attacker vanligtvis kräver frekvent interaktion med agenten är det ett annat sätt att begränsa antalet turer i en konversation för att förhindra dessa typer av attacker.

### Åtkomst till kritiska system

**Beskrivning:** Om en AI-agent har åtkomst till system och tjänster som lagrar känslig data kan angripare kompromettera kommunikationen mellan agenten och dessa tjänster. Dessa kan vara direkta attacker eller indirekta försök att få information om dessa system genom agenten.

**Motåtgärd:** AI-agenter ska ha åtkomst till system endast vid behov för att förhindra dessa typer av attacker. Kommunikation mellan agenten och systemet bör också vara säker. Att implementera autentisering och åtkomstkontroll är ett annat sätt att skydda denna information.

### Resurs- och tjänsteöverbelastning

**Beskrivning:** AI-agenter kan använda olika verktyg och tjänster för att utföra uppgifter. Angripare kan använda denna förmåga för att attackera dessa tjänster genom att skicka en hög volym av förfrågningar via AI-agenten, vilket kan resultera i systemfel eller höga kostnader.

**Motåtgärd:** Genomför policyer för att begränsa antalet förfrågningar en AI-agent kan göra till en tjänst. Att begränsa antalet konversationsomgångar och förfrågningar till din AI-agent är ett annat sätt att förhindra dessa typer av attacker.

### Förgiftning av kunskapsbas

**Beskrivning:** Denna typ av attack riktar sig inte direkt mot AI-agenten utan mot kunskapsbasen och andra tjänster som AI-agenten kommer använda. Detta kan innebära att data eller information som AI-agenten används för att slutföra en uppgift blir korrupt, vilket leder till partiska eller oavsiktliga svar till användaren.

**Motåtgärd:** Utför regelbunden verifiering av data som AI-agenten använder i sina arbetsflöden. Säkerställ att åtkomst till denna data är säker och endast ändras av betrodda personer för att undvika denna typ av attack.

### Kaskader av fel

**Beskrivning:** AI-agenter använder olika verktyg och tjänster för att slutföra uppgifter. Fel orsakade av angripare kan leda till att andra system som AI-agenten är kopplad till går sönder, vilket gör att attacken blir mer utbredd och svårare att felsöka.

**Motåtgärd:** En metod för att undvika detta är att låta AI-agenten arbeta i en begränsad miljö, till exempel att utföra uppgifter i en Docker-container, för att förhindra direkta systemattacker. Att skapa fallback-mekanismer och återförsökslogik när vissa system svarar med fel är ett annat sätt att förhindra större systemfel.

## Människa i loopen

Ett annat effektivt sätt att bygga pålitliga AI-agentssystem är att använda en människa i loopen. Detta skapar ett flöde där användare kan ge feedback till agenterna under körningen. Användarna fungerar i praktiken som agenter i ett multi-agent-system och genom att ge godkännande eller avbrytande av den pågående processen.

![Människa i loopen](../../../translated_images/sv/human-in-the-loop.5f0068a678f62f4f.webp)

Här är ett kodexempel som använder AutoGen för att visa hur detta koncept implementeras:

```python

# Skapa agenterna.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Använd input() för att få användarinmatning från konsolen.

# Skapa avslutningsvillkoret som kommer att avsluta konversationen när användaren säger "APPROVE".
termination = TextMentionTermination("APPROVE")

# Skapa teamet.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Kör konversationen och strömma till konsolen.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Använd asyncio.run(...) när du kör i ett skript.
await Console(stream)

```

## Slutsats

Att bygga pålitliga AI-agenter kräver noggrann design, robusta säkerhetsåtgärder och kontinuerlig iteration. Genom att implementera strukturerade meta-promptingsystem, förstå potentiella hot och tillämpa motåtgärdsstrategier kan utvecklare skapa AI-agenter som både är säkra och effektiva. Dessutom säkerställer en människa-i-loopen-ansats att AI-agenter förblir anpassade efter användarens behov samtidigt som riskerna minimeras. Eftersom AI fortsätter att utvecklas är det avgörande att upprätthålla ett proaktivt förhållningssätt till säkerhet, integritet och etiska överväganden för att främja förtroende och pålitlighet i AI-drivna system.

### Har du fler frågor om att bygga pålitliga AI-agenter?

Gå med i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) för att träffa andra elever, delta i öppna kontorstider och få svar på dina frågor om AI-agenter.

## Ytterligare resurser

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Ansvarsfull AI-översikt</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Utvärdering av generativa AI-modeller och AI-applikationer</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Säkerhetssystemmeddelanden</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Mall för riskbedömning</a>

## Föregående lektion

[Agentisk RAG](../05-agentic-rag/README.md)

## Nästa lektion

[Planeringsdesignmönster](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfriskrivning**:  
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet, bör du vara medveten om att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet på dess modersmål ska betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår från användningen av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->