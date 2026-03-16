[![Pouzdani AI agenti](../../../translated_images/hr/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Kliknite gornju sliku da pogledate video ove lekcije)_

# Izgradnja pouzdanih AI agenata

## Uvod

Ova lekcija će obuhvatiti:

- Kako izgraditi i implementirati sigurne i učinkovite AI agente
- Važne sigurnosne razmatranja prilikom razvoja AI agenata.
- Kako održavati privatnost podataka i korisnika prilikom razvoja AI agenata.

## Ciljevi učenja

Nakon završetka ove lekcije, znat ćete kako:

- Identificirati i ublažiti rizike pri stvaranju AI agenata.
- Provesti sigurnosne mjere kako bi se osiguralo pravilno upravljanje podacima i pristupom.
- Stvoriti AI agente koji održavaju privatnost podataka i pružaju kvalitetno korisničko iskustvo.

## Sigurnost

Prvo pogledajmo izgradnju sigurnih agentskih aplikacija. Sigurnost znači da AI agent radi onako kako je zamišljen. Kao graditelji agentskih aplikacija, imamo metode i alate za maksimaliziranje sigurnosti:

### Izgradnja okvira za sistemske poruke

Ako ste ikada izgradili AI aplikaciju koristeći velike jezične modele (LLMs), znate koliko je važno dizajnirati robusni sistemski prompt ili sistemsku poruku. Ti promptovi uspostavljaju meta pravila, upute i smjernice za način na koji će se LLM odnositi prema korisniku i podacima.

Za AI agente, sistemski prompt je još važniji jer će AI agenti trebati vrlo specifične upute za izvršavanje zadataka koje smo za njih dizajnirali.

Za stvaranje skalabilnih sistemskih promptova možemo koristiti okvir za sistemske poruke za izgradnju jednog ili više agenata u našoj aplikaciji:

![Izgradnja okvira za sistemske poruke](../../../translated_images/hr/system-message-framework.3a97368c92d11d68.webp)

#### Korak 1: Stvorite meta sistemsku poruku 

Meta prompt će se koristiti od strane LLM-a za generiranje sistemskih promptova za agente koje stvorimo. Dizajniramo ga kao predložak kako bismo efikasno mogli stvoriti više agenata po potrebi.

Evo primjera meta sistemske poruke koju bismo dali LLM-u:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Korak 2: Stvorite osnovni prompt

Sljedeći korak je stvoriti osnovni prompt koji opisuje AI agenta. Trebali biste uključiti ulogu agenta, zadatke koje će agent izvršavati i sve ostale odgovornosti agenta.

Evo primjera:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Korak 3: Dostavite osnovnu sistemsku poruku LLM-u

Sada možemo optimizirati ovu sistemsku poruku tako da meta sistemsku poruku pružimo kao sistemsku poruku i našu osnovnu sistemsku poruku.

To će proizvesti sistemsku poruku koja je bolje dizajnirana za vođenje naših AI agenata:

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

#### Korak 4: Ponavljajte i poboljšavajte

Vrijednost ovog okvira za sistemske poruke je u mogućnosti da se lakše skalira stvaranje sistemskih poruka za više agenata kao i u poboljšavanju vaših sistemskih poruka tijekom vremena. Rijetko je da ćete imati sistemsku poruku koja radi prvi put za vaš cjelokupni slučaj upotrebe. Mogućnost da napravite male izmjene i poboljšanja mijenjanjem osnovne sistemske poruke i pokretanjem kroz sustav omogućit će vam usporedbu i evaluaciju rezultata.

## Razumijevanje prijetnji

Kako biste izgradili pouzdane AI agente, važno je razumjeti i ublažiti rizike i prijetnje prema vašem AI agentu. Pogledajmo samo neke od različitih prijetnji AI agentima i kako se možete bolje planirati i pripremiti za njih.

![Razumijevanje prijetnji](../../../translated_images/hr/understanding-threats.89edeada8a97fc0f.webp)

### Zadatak i upute

**Opis:** Napadači pokušavaju promijeniti upute ili ciljeve AI agenta putem promptanja ili manipuliranja ulazima.

**Ublažavanje**: Izvršite provjere valjanosti i filtre ulaza da biste otkrili potencijalno opasne promptove prije nego što ih AI agent obradi. Budući da ti napadi obično zahtijevaju učestalu interakciju s agentom, ograničavanje broja poteza u razgovoru je još jedan način da se spriječe ovakve vrste napada.

### Pristup kritičkim sustavima

**Opis**: Ako AI agent ima pristup sustavima i servisima koji pohranjuju osjetljive podatke, napadači mogu kompromitirati komunikaciju između agenta i tih servisa. To mogu biti izravni napadi ili indirektni pokušaji dobivanja informacija o tim sustavima kroz agenta.

**Ublažavanje**: AI agenti trebaju imati pristup sustavima samo po principu potrebe kako bi se spriječile ovakve vrste napada. Komunikacija između agenta i sustava također treba biti sigurna. Implementacija autentikacije i kontrole pristupa je još jedan način zaštite ovih informacija.

### Preopterećenje resursa i usluga

**Opis:** AI agenti mogu pristupiti različitim alatima i servisima kako bi izvršili zadatke. Napadači mogu iskoristiti tu sposobnost za napad na te servise slanjem velike količine zahtjeva preko AI agenta, što može rezultirati kvarovima sustava ili visokim troškovima.

**Ublažavanje:** Implementirajte politike za ograničavanje broja zahtjeva koje AI agent može slati servisu. Ograničavanje broja poteza u razgovoru i zahtjeva prema vašem AI agentu je još jedan način sprječavanja ovakvih vrsta napada.

### Trovanje baze znanja

**Opis:** Ova vrsta napada ne cilja izravno AI agenta već cilja bazu znanja i druge servise koje će AI agent koristiti. To može uključivati korumpiranje podataka ili informacija koje će AI agent koristiti za izvršavanje zadatka, što dovodi do pristranih ili neželjenih odgovora korisniku.

**Ublažavanje:** Redovito provjeravajte podatke koje će AI agent koristiti u svojim radnim tokovima. Osigurajte da je pristup tim podacima siguran i da ih mijenjaju samo pouzdane osobe kako biste izbjegli ovu vrstu napada.

### Kaskadne pogreške

**Opis:** AI agenti pristupaju raznim alatima i servisima za izvršavanje zadataka. Pogreške uzrokovane od strane napadača mogu dovesti do kvarova drugih sustava s kojima je AI agent povezan, čime napad postaje rašireniji i teže ga je otkloniti.

**Ublažavanje**: Jedna metoda za izbjegavanje toga je da AI agent radi u ograničenom okruženju, npr. izvršavanjem zadataka u Docker kontejneru, kako bi se spriječili izravni napadi na sustav. Izrada mehanizama za povratnu opciju i logike ponovnog pokušaja kad se neki sustavi jave s pogreškom je još jedan način sprječavanja većih kvarova sustava.

## Čovjek u petlji

Još jedan učinkovit način za izgradnju pouzdanih sustava AI agenata je korištenje koncepta 'čovjek u petlji'. Time se stvara tok u kojem korisnici mogu davati povratne informacije agentima tijekom izvršavanja. Korisnici u suštini djeluju kao agenti u sustavu s više agenata i svojim odobravanjem ili prekidom pokrenutog procesa utječu na izvršenje.

![Čovjek u petlji](../../../translated_images/hr/human-in-the-loop.5f0068a678f62f4f.webp)

Evo isječka koda koji koristi AutoGen kako bi pokazao kako se ovaj koncept implementira:

```python

# Kreirajte agente.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Koristite input() za dobivanje korisničkog unosa iz konzole.

# Kreirajte uvjet završetka koji će završiti razgovor kada korisnik kaže "APPROVE".
termination = TextMentionTermination("APPROVE")

# Kreirajte tim.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Pokrenite razgovor i streamajte u konzolu.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Koristite asyncio.run(...) kada se pokreće u skripti.
await Console(stream)

```

## Zaključak

Izgradnja pouzdanih AI agenata zahtijeva pažljiv dizajn, robusne sigurnosne mjere i kontinuiranu iteraciju. Implementacijom strukturiranih sustava meta promptanja, razumijevanjem potencijalnih prijetnji i primjenom strategija ublažavanja, programeri mogu stvoriti AI agente koji su i sigurni i učinkoviti. Dodatno, uključivanje pristupa 'čovjek u petlji' osigurava da AI agenti ostanu usklađeni s korisničkim potrebama uz minimiziranje rizika. Kako se AI nastavlja razvijati, održavanje proaktivnog stava prema sigurnosti, privatnosti i etičkim razmatranjima bit će ključno za njegovanje povjerenja i pouzdanosti u sustavima koje pokreće AI.

### Imate li više pitanja o izgradnji pouzdanih AI agenata?

Pridružite se [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kako biste se susreli s drugim učenicima, sudjelovali na radnim satima i dobili odgovore na pitanja o svojim AI agentima.

## Dodatni resursi

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Pregled odgovornog korištenja AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Evaluacija generativnih AI modela i AI aplikacija</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Sigurnosne sistemske poruke</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Predložak procjene rizika</a>

## Prethodna lekcija

[Agentic RAG](../05-agentic-rag/README.md)

## Sljedeća lekcija

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Odricanje od odgovornosti**:
Ovaj dokument je preveden pomoću AI usluge za prijevod [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo osigurati točnost, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za kritične informacije preporučuje se profesionalan prijevod koji obavi ljudski prevoditelj. Ne snosimo odgovornost za bilo kakve nesporazume ili pogrešne interpretacije koje proizlaze iz korištenja ovog prijevoda.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->