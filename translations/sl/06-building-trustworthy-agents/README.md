[![Zanesljivi agenti AI](../../../translated_images/sl/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Kliknite na zgornjo sliko za ogled videoposnetka te lekcije)_

# Gradnja zanesljivih agentov AI

## Uvod

Ta lekcija bo obravnavala:

- Kako zgraditi in uvesti varne in učinkovite agente AI
- Pomembne varnostne premisleke pri razvoju agentov AI.
- Kako ohraniti zasebnost podatkov in uporabnikov pri razvoju agentov AI.

## Cilji učenja

Po končani tej lekciji boste vedeli, kako:

- Prepoznati in omiliti tveganja pri ustvarjanju agentov AI.
- Izvesti varnostne ukrepe za zagotovitev pravilnega upravljanja podatkov in dostopa.
- Ustvariti agente AI, ki ohranjajo zasebnost podatkov in zagotavljajo kakovostno uporabniško izkušnjo.

## Varnost

Najprej si oglejmo gradnjo varnih agentnih aplikacij. Varnost pomeni, da agent AI deluje, kot je bilo zasnovano. Kot graditelji agentnih aplikacij imamo metode in orodja za maksimalno varnost:

### Gradnja ogrodja za sistemska sporočila

Če ste že kdaj ustvarjali AI aplikacijo z uporabo velikih jezikovnih modelov (LLM), poznate pomen zasnove robustnega sistemskega poziva ali sistemskega sporočila. Ti pozivi vzpostavijo meta pravila, navodila in smernice za interakcijo LLM z uporabnikom in podatki.

Za agente AI je sistemski poziv še pomembnejši, saj bodo agenti AI potrebovali zelo specifična navodila za dokončanje nalog, ki smo jih zanje zasnovali.

Za ustvarjanje razširljivih sistemskih pozivov lahko uporabimo ogrodje sistemskega sporočila za gradnjo enega ali več agentov v naši aplikaciji:

![Gradnja ogrodja za sistemska sporočila](../../../translated_images/sl/system-message-framework.3a97368c92d11d68.webp)

#### Korak 1: Ustvarite meta sistemsko sporočilo

Meta poziv bo uporabil LLM za generiranje sistemskih pozivov za agente, ki jih ustvarjamo. Oblikujemo ga kot predlogo, da lahko učinkovito ustvarimo več agentov, če je potrebno.

Tukaj je primer meta sistemskega sporočila, ki bi ga dali LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Korak 2: Ustvarite osnovni poziv

Naslednji korak je, da ustvarite osnovni poziv za opis agenta AI. Vključiti morate vlogo agenta, naloge, ki jih bo agent opravil, in druge odgovornosti agenta.

Tukaj je primer:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Korak 3: Posredujte osnovno sistemsko sporočilo LLM

Zdaj lahko optimiziramo to sistemsko sporočilo tako, da posredujemo meta sistemsko sporočilo kot sistemsko sporočilo skupaj z našim osnovnim sistemskim sporočilom.

To bo ustvarilo sistemsko sporočilo, ki je bolje zasnovano za usmerjanje naših agentov AI:

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

#### Korak 4: Ponovite in izboljšajte

Vrednost tega ogrodja sistemskih sporočil je v tem, da lahko lažje razširjate ustvarjanje sistemskih sporočil za več agentov in hkrati izboljšujete svoja sistemska sporočila skozi čas. Redko se zgodi, da bo sistemsko sporočilo prvič delovalo za vaš celovit primer uporabe. Možnost majhnih popravkov in izboljšav z menjavo osnovnega sistemskega sporočila in njegovo obdelavo skozi sistem vam bo omogočila primerjavo in ocenjevanje rezultatov.

## Razumevanje groženj

Za gradnjo zanesljivih agentov AI je pomembno razumeti in omiliti tveganja in grožnje za vašega agenta AI. Oglejmo si le nekatere različne grožnje agentom AI in kako se nanje bolje pripraviti.

![Razumevanje groženj](../../../translated_images/sl/understanding-threats.89edeada8a97fc0f.webp)

### Naloge in navodila

**Opis:** Napadalci poskušajo spremeniti navodila ali cilje agenta AI preko pozivanja ali manipuliranja vhodnih podatkov.

**Omilitev:** Izvedite preverjanje veljavnosti in filtre za vhodne podatke, da zaznate potencialno nevarne pozive, preden jih agent AI obdela. Ker ti napadi tipično zahtevajo pogosto interakcijo z agentom, je omejitev števila krogov pogovora še en način za preprečevanje takšnih napadov.

### Dostop do kritičnih sistemov

**Opis:** Če ima agent AI dostop do sistemov in storitev, ki hranijo občutljive podatke, lahko napadalci ogrozijo komunikacijo med agentom in temi storitvami. To so lahko neposredni napadi ali poskusi za pridobitev informacij o teh sistemih preko agenta.

**Omilitev:** Agenti AI naj imajo dostop do sistemov samo, če je to nujno potrebno, da preprečimo tovrstne napade. Komunikacija med agentom in sistemom naj bo prav tako varna. Uvedba overjanja in nadzora dostopa je še en način za zaščito teh informacij.

### Preobremenitev virov in storitev

**Opis:** Agenti AI lahko dostopajo do različnih orodij in storitev za izvajanje nalog. Napadalci lahko to zmožnost zlorabijo tako, da pošiljajo velik obseg zahtev skozi agenta AI, kar lahko povzroči odpoved sistema ali visoke stroške.

**Omilitev:** Uvedite politike za omejitev števila zahtev, ki jih lahko agent AI pošlje storitvi. Omejitev števila krogov pogovora in zahtev agentu AI je še en način za preprečevanje tovrstnih napadov.

### Zastrupitev baze znanja

**Opis:** Ta vrsta napada ne cilja neposredno na agenta AI, ampak na bazo znanja in druge storitve, ki jih bo agent AI uporabljal. Lahko vključuje pokvarjanje podatkov ali informacij, ki jih bo agent uporabil za dokončanje naloge, kar vodi do pristranskih ali neželenih odgovorov uporabniku.

**Omilitev:** Redno preverjajte podatke, ki jih agent AI uporablja v svojih delovnih procesih. Poskrbite, da je dostop do teh podatkov varen in jih lahko spreminjajo samo zaupanja vredne osebe, da se izognete temu tipu napada.

### Vodeni zaporedni napaki

**Opis:** Agenti AI dostopajo do različnih orodij in storitev za izvedbo nalog. Napake, ki jih povzročijo napadalci, lahko povzročijo odpovedi drugih sistemov, s katerimi je agent povezan, zaradi česar se napad razširi in postane težje odpravljiv.

**Omilitev:** Ena metoda za izogibanje temu je, da agent AI deluje v omejenem okolju, na primer z izvajanjem nalog v Docker vsebniku, da se preprečijo neposredni napadi na sistem. Ustvarjanje rezervnih mehanizmov in logike ponovnega poskusa, ko določeni sistemi odgovorijo z napako, je še en način za preprečevanje večjih odpovedi sistema.

## Človek v zanki

Še en učinkovit način za gradnjo zanesljivih sistemov agentov AI je uporaba človeka v zanki. To ustvari potek, kjer lahko uporabniki med izvajanjem dajejo povratne informacije agentom. Uporabniki v bistvu delujejo kot agenti v sistemu z več agenti in tako odobravajo ali prekinejo tekoči proces.

![Človek v zanki](../../../translated_images/sl/human-in-the-loop.5f0068a678f62f4f.webp)

Tukaj je primer kode, ki uporablja AutoGen in prikazuje, kako je ta koncept izveden:

```python

# Ustvari agente.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Uporabi input() za pridobivanje vnosa uporabnika iz konzole.

# Ustvari pogoj za zaključek, ki bo končal pogovor, ko uporabnik reče "APPROVE".
termination = TextMentionTermination("APPROVE")

# Ustvari ekipo.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Zaženi pogovor in pretakaj v konzolo.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Uporabi asyncio.run(...), ko tečeš v skripti.
await Console(stream)

```

## Zaključek

Gradnja zanesljivih agentov AI zahteva skrbno zasnovo, robustne varnostne ukrepe in nenehno iteracijo. Z izvajanjem strukturiranih meta pozivnih sistemov, razumevanjem potencialnih groženj in uporabo strategij omilitve lahko razvijalci ustvarijo agente AI, ki so tako varni kot učinkoviti. Poleg tega vključitev človeka v zanki zagotavlja, da agenti AI ostanejo usklajeni z uporabniškimi potrebami ob hkratnem zmanjšanju tveganj. Ko se AI še naprej razvija, bo ohranjanje proaktivnega pristopa k varnosti, zasebnosti in etičnim vidikom ključnega pomena za spodbujanje zaupanja in zanesljivosti v sistemih, ki jih poganja AI.

### Imate več vprašanj o gradnji zanesljivih agentov AI?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) in se srečajte z drugimi učenci, udeležite uradnih ur in dobite odgovore na vprašanja o agentih AI.

## Dodatni viri

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Pregled odgovorne uporabe AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Evalvacija modelov generativne AI in AI aplikacij</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Varnostna sistemska sporočila</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Predloga ocene tveganja</a>

## Prejšnja lekcija

[Agentic RAG](../05-agentic-rag/README.md)

## Naslednja lekcija

[Oblikovni vzorec načrtovanja](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Omejitev odgovornosti**:
Ta dokument je bil preveden z uporabo storitve za strojno prevajanje [Co-op Translator](https://github.com/Azure/co-op-translator). Čeprav si prizadevamo za natančnost, vas opozarjamo, da lahko avtomatizirani prevodi vsebujejo napake ali netočnosti. Izvirni dokument v njegovem izvorni jeziku velja za verodostojen vir. Za kritične informacije priporočamo strokovni človeški prevod. Za morebitna nesporazume ali napačne razlage, ki izhajajo iz uporabe tega prevoda, ne odgovarjamo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->