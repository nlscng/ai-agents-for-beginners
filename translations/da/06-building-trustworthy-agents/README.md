[![Pålidelige AI-agenter](../../../translated_images/da/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klik på billedet ovenfor for at se videoen af denne lektion)_

# Opbygning af pålidelige AI-agenter

## Introduktion

Denne lektion vil dække:

- Hvordan man bygger og implementerer sikre og effektive AI-agenter
- Vigtige sikkerhedsovervejelser ved udvikling af AI-agenter.
- Hvordan man opretholder data- og brugerprivathed ved udvikling af AI-agenter.

## Læringsmål

Efter at have gennemført denne lektion vil du vide, hvordan du:

- Identificerer og afbøder risici ved skabelse af AI-agenter.
- Implementerer sikkerhedsforanstaltninger for at sikre, at data og adgang håndteres korrekt.
- Skaber AI-agenter, der opretholder dataprivathed og leverer en kvalitetsbrugeroplevelse.

## Sikkerhed

Lad os først se på at bygge sikre agent-baserede applikationer. Sikkerhed betyder, at AI-agenten fungerer som designet. Som udviklere af agent-baserede applikationer har vi metoder og værktøjer til at maksimere sikkerheden:

### Opbygning af et systembesked-rammeværk

Hvis du nogensinde har bygget en AI-applikation med brug af store sprogmodeller (LLM'er), ved du, hvor vigtigt det er at designe et robust systemprompt eller systembesked. Disse prompts fastlægger de meta-regler, instruktioner og retningslinjer for, hvordan LLM'en vil interagere med brugeren og data.

For AI-agenter er systemprompten endnu vigtigere, da AI-agenterne vil have brug for meget specifikke instruktioner for at fuldføre de opgaver, vi har designet til dem.

For at skabe skalerbare systemprompter kan vi bruge et systembesked-rammeværk til at bygge en eller flere agenter i vores applikation:

![Opbygning af et systembesked-rammeværk](../../../translated_images/da/system-message-framework.3a97368c92d11d68.webp)

#### Trin 1: Opret en meta systembesked

Meta prompten vil blive brugt af en LLM til at generere systemprompter til de agenter, vi opretter. Vi designer den som en skabelon, så vi effektivt kan skabe flere agenter om nødvendigt.

Her er et eksempel på en meta systembesked, vi ville give til LLM’en:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Trin 2: Opret et grundlæggende prompt

Næste trin er at oprette et grundlæggende prompt for at beskrive AI-agenten. Du bør inkludere agentens rolle, de opgaver agenten skal udføre, og eventuelle andre ansvar, agenten har.

Her er et eksempel:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Trin 3: Giv grundlæggende systembesked til LLM

Nu kan vi optimere denne systembesked ved at give meta systembeskeden som systembesked sammen med vores grundlæggende systembesked.

Dette vil producere en systembesked, der er bedre designet til at styre vores AI-agenter:

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

#### Trin 4: Iterer og forbedr

Værdien af dette systembesked-rammeværk er at kunne skalere oprettelsen af systembeskeder for flere agenter lettere samt forbedre dine systembeskeder over tid. Det er sjældent, at du har en systembesked, der fungerer perfekt første gang for dit komplette brugsscenarie. At kunne foretage små justeringer og forbedringer ved at ændre den grundlæggende systembesked og køre den igennem systemet giver dig mulighed for at sammenligne og evaluere resultater.

## Forståelse af trusler

For at bygge pålidelige AI-agenter er det vigtigt at forstå og afbøde risici og trusler mod din AI-agent. Lad os se på nogle af de forskellige trusler mod AI-agenter og hvordan du kan planlægge og forberede dig bedre på dem.

![Forståelse af trusler](../../../translated_images/da/understanding-threats.89edeada8a97fc0f.webp)

### Opgave og instruktion

**Beskrivelse:** Angribere forsøger at ændre AI-agentens instruktioner eller mål gennem prompting eller manipulation af input.

**Afhjælpning**: Udfør valideringskontroller og inputfiltre for at opdage potentielt farlige prompts, før de behandles af AI-agenten. Da disse angreb typisk kræver hyppig interaktion med agenten, er begrænsning af antal udvekslinger i en samtale en anden måde at forhindre denne type angreb på.

### Adgang til kritiske systemer

**Beskrivelse**: Hvis en AI-agent har adgang til systemer og tjenester, der gemmer følsomme data, kan angribere kompromittere kommunikationen mellem agenten og disse tjenester. Det kan være direkte angreb eller indirekte forsøg på at skaffe information om disse systemer via agenten.

**Afhjælpning**: AI-agenter bør have adgang til systemer kun når nødvendigt for at forhindre denne type angreb. Kommunikationen mellem agenten og systemet skal også være sikker. Implementering af autentificering og adgangskontrol er en anden måde at beskytte disse oplysninger på.

### Overbelastning af ressourcer og tjenester

**Beskrivelse:** AI-agenter kan få adgang til forskellige værktøjer og tjenester for at fuldføre opgaver. Angribere kan udnytte denne evne til at angribe disse tjenester ved at sende et stort antal anmodninger via AI-agenten, hvilket kan resultere i systemfejl eller høje omkostninger.

**Afhjælpning:** Implementer politikker til at begrænse antallet af anmodninger, som en AI-agent kan sende til en tjeneste. Begrænsning af antal samtaleudvekslinger og anmodninger til din AI-agent er en anden måde at forhindre denne type angreb på.

### Forurening af vidensbase

**Beskrivelse:** Denne type angreb retter sig ikke direkte mod AI-agenten, men mod vidensbasen og andre tjenester, som AI-agenten vil bruge. Det kan involvere korruption af data eller oplysninger, som AI-agenten vil bruge til at fuldføre en opgave, hvilket fører til forudindtagede eller utilsigtede svar til brugeren.

**Afhjælpning:** Udfør regelmæssig verifikation af de data, som AI-agenten vil bruge i sine arbejdsgange. Sørg for, at adgangen til disse data er sikker og kun ændres af betroede personer for at undgå denne type angreb.

### Kaskaderende fejl

**Beskrivelse:** AI-agenter får adgang til forskellige værktøjer og tjenester for at fuldføre opgaver. Fejl forårsaget af angribere kan føre til fejl i andre systemer, som AI-agenten er tilknyttet, hvilket gør angrebet mere udbredt og sværere at fejlfinde.

**Afhjælpning**: En metode til at undgå dette er, at AI-agenten opererer i et begrænset miljø, såsom at udføre opgaver i en Docker-container, for at forhindre direkte systemangreb. At skabe fallback-mekanismer og retry-logik, når visse systemer svarer med en fejl, er en anden måde at forhindre større systemfejl på.

## Menneske-i-løkken

En anden effektiv måde at bygge pålidelige AI-Agent systemer på er ved at bruge et menneske-i-løkken. Dette skaber en strøm, hvor brugere kan give feedback til agenterne under kørslen. Brugerne fungerer i praksis som agenter i et multi-agent system ved at give godkendelse eller afbrydelse af den kørende proces.

![Menneske i løkken](../../../translated_images/da/human-in-the-loop.5f0068a678f62f4f.webp)

Her er et kodeeksempel, der bruger AutoGen til at vise, hvordan dette koncept implementeres:

```python

# Opret agenterne.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Brug input() til at få brugerinput fra konsollen.

# Opret afslutningsbetingelsen, som vil afslutte samtalen, når brugeren siger "GODKEND".
termination = TextMentionTermination("APPROVE")

# Opret teamet.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Kør samtalen og stream til konsollen.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Brug asyncio.run(...) når det køres i et script.
await Console(stream)

```

## Konklusion

At bygge pålidelige AI-agenter kræver omhyggeligt design, robuste sikkerhedsforanstaltninger og kontinuerlig iteration. Ved at implementere strukturerede meta-promptsystemer, forstå potentielle trusler og anvende afbødningsstrategier kan udviklere skabe AI-agenter, der både er sikre og effektive. Derudover sikrer en menneske-i-løkken tilgang, at AI-agenter forbliver tilpasset brugerens behov, samtidig med at risiciene minimeres. Efterhånden som AI udvikler sig, vil en proaktiv holdning til sikkerhed, privatliv og etiske overvejelser være nøglen til at fremme tillid og pålidelighed i AI-drevne systemer.

### Har du flere spørgsmål om opbygning af pålidelige AI-agenter?

Deltag i [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) for at møde andre elever, deltage i kontortimer og få svar på dine spørgsmål om AI-agenter.

## Yderligere ressourcer

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Overblik over ansvarlig AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Evaluering af generative AI-modeller og AI-applikationer</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Sikkerhedssystembeskeder</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Skabelon for risikovurdering</a>

## Forrige lektion

[Agentic RAG](../05-agentic-rag/README.md)

## Næste lektion

[Planlægningsdesignmønster](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Ansvarsfraskrivelse**:
Dette dokument er oversat ved hjælp af AI-oversættelsestjenesten [Co-op Translator](https://github.com/Azure/co-op-translator). Selvom vi stræber efter nøjagtighed, bedes du være opmærksom på, at automatiserede oversættelser kan indeholde fejl eller unøjagtigheder. Det oprindelige dokument på dets modersmål bør betragtes som den autoritative kilde. For kritisk information anbefales professionel menneskelig oversættelse. Vi påtager os ikke ansvar for eventuelle misforståelser eller fejltolkninger, der opstår som følge af brugen af denne oversættelse.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->