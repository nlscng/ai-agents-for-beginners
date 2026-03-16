[![Agenți AI demni de încredere](../../../translated_images/ro/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Faceți clic pe imaginea de mai sus pentru a viziona videoclipul acestei lecții)_

# Construirea agenților AI de încredere

## Introducere

Această lecție va acoperi:

- Cum să construiești și să lansezi agenți AI siguri și eficienți
- Considerații importante de securitate la dezvoltarea agenților AI.
- Cum să menții confidențialitatea datelor și a utilizatorilor la dezvoltarea agenților AI.

## Obiective de învățare

După finalizarea acestei lecții, veți ști cum să:

- Identificați și să atenuați riscurile la crearea agenților AI.
- Implementați măsuri de securitate pentru a vă asigura că datele și accesul sunt gestionate corect.
- Creați agenți AI care mențin confidențialitatea datelor și oferă o experiență de utilizator de calitate.

## Siguranță

Să analizăm mai întâi construirea aplicațiilor agentice sigure. Siguranța înseamnă că agentul AI funcționează conform proiectului. Ca dezvoltatori ai aplicațiilor agentice, avem metode și instrumente pentru a maximiza siguranța:

### Construirea unui cadru de mesaje de sistem

Dacă ați construit vreodată o aplicație AI folosind modele mari de limbaj (LLM), știți importanța proiectării unui prompt sau mesaj de sistem robust. Aceste prompturi stabilesc regulile meta, instrucțiunile și ghidurile pentru modul în care LLM va interacționa cu utilizatorul și datele.

Pentru agenții AI, promptul de sistem este și mai important deoarece agenții AI vor avea nevoie de instrucțiuni foarte specifice pentru a îndeplini sarcinile pe care le-am proiectat pentru ei.

Pentru a crea prompturi de sistem scalabile, putem folosi un cadru de mesaje de sistem pentru a construi unul sau mai mulți agenți în aplicația noastră:

![Construirea unui cadru de mesaje de sistem](../../../translated_images/ro/system-message-framework.3a97368c92d11d68.webp)

#### Pasul 1: Creați un mesaj meta de sistem 

Promptul meta va fi folosit de un LLM pentru a genera prompturile de sistem pentru agenții pe care îi creăm. Îl proiectăm ca pe un șablon astfel încât să putem crea eficient mai mulți agenți, dacă este necesar.

Iată un exemplu de mesaj meta de sistem pe care l-am oferi LLM-ului:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Pasul 2: Creați un prompt de bază

Următorul pas este să creați un prompt de bază pentru a descrie Agentul AI. Ar trebui să includeți rolul agentului, sarcinile pe care agentul le va îndeplini și orice alte responsabilități ale agentului.

Iată un exemplu:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Pasul 3: Furnizați mesajul de sistem de bază către LLM

Acum putem optimiza acest mesaj de sistem furnizând mesajul meta de sistem ca mesaj de sistem și mesajul nostru de sistem de bază.

Acest lucru va produce un mesaj de sistem mai bine conceput pentru a ghida agenții AI:

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

#### Pasul 4: Iterați și îmbunătățiți

Valoarea acestui cadru de mesaje de sistem este de a putea scala crearea mesajelor de sistem pentru mai mulți agenți mai ușor, precum și de a vă îmbunătăți mesajele de sistem în timp. Este rar să aveți un mesaj de sistem care funcționează din prima pentru întregul dvs. caz de utilizare. Posibilitatea de a face mici ajustări și îmbunătățiri prin schimbarea mesajului de sistem de bază și rularea acestuia prin sistem vă va permite să comparați și să evaluați rezultatele.

## Înțelegerea amenințărilor

Pentru a construi agenți AI demni de încredere, este important să înțelegeți și să atenuați riscurile și amenințările la adresa agentului AI. Să analizăm doar unele dintre diferitele amenințări la adresa agenților AI și cum vă puteți planifica și pregăti mai bine pentru ele.

![Înțelegerea amenințărilor](../../../translated_images/ro/understanding-threats.89edeada8a97fc0f.webp)

### Sarcină și Instrucțiune

**Descriere:** Atacatorii încearcă să schimbe instrucțiunile sau obiectivele agentului AI prin prompting sau manipularea intrărilor.

**Atenuare**: Efectuați verificări de validare și filtre de intrare pentru a detecta prompturi potențial periculoase înainte ca acestea să fie procesate de agentul AI. Deoarece aceste atacuri necesită de obicei interacțiuni frecvente cu agentul, limitarea numărului de schimburi într-o conversație este o altă metodă de a preveni acest tip de atacuri.

### Acces la sisteme critice

**Descriere**: Dacă un agent AI are acces la sisteme și servicii care stochează date sensibile, atacatorii pot compromite comunicația dintre agent și aceste servicii. Acestea pot fi atacuri directe sau încercări indirecte de a obține informații despre aceste sisteme prin intermediul agentului.

**Atenuare**: Agenții AI ar trebui să aibă acces la sisteme doar pe bază de necesitate pentru a preveni acest tip de atacuri. Comunicarea dintre agent și sistem ar trebui, de asemenea, să fie securizată. Implementarea autentificării și a controlului accesului este o altă modalitate de a proteja aceste informații.

### Supraîncărcarea resurselor și serviciilor

**Descriere:** Agenții AI pot accesa diferite instrumente și servicii pentru a îndeplini sarcini. Atacatorii pot folosi această abilitate pentru a ataca aceste servicii prin trimiterea unui volum mare de cereri prin intermediul agentului AI, ceea ce poate duce la defecțiuni ale sistemului sau costuri ridicate.

**Atenuare:** Implementați politici pentru a limita numărul de cereri pe care un agent AI le poate face către un serviciu. Limitarea numărului de ture de conversație și a cererilor către agentul AI este o altă modalitate de a preveni aceste tipuri de atacuri.

### Otrăvirea bazei de cunoștințe

**Descriere:** Acest tip de atac nu vizează agentul AI direct, ci țintește baza de cunoștințe și alte servicii pe care agentul AI le va folosi. Acest lucru poate implica coruperea datelor sau informațiilor pe care agentul AI le va folosi pentru a îndeplini o sarcină, conducând la răspunsuri părtinitoare sau neintenționate pentru utilizator.

**Atenuare:** Efectuați verificări regulate ale datelor pe care agentul AI le va folosi în fluxurile sale de lucru. Asigurați-vă că accesul la aceste date este securizat și că pot fi modificate doar de persoane de încredere pentru a evita acest tip de atac.

### Erori în cascadă

**Descriere:** Agenții AI accesează diverse instrumente și servicii pentru a îndeplini sarcini. Erorile cauzate de atacatori pot duce la defecțiuni ale altor sisteme la care agentul AI este conectat, făcând atacul mai extins și mai greu de depistat.

**Atenuare**: O metodă de a evita acest lucru este ca Agentul AI să opereze într-un mediu limitat, cum ar fi executarea sarcinilor într-un container Docker, pentru a preveni atacurile directe asupra sistemului. Crearea de mecanisme de rezervă și logică de reîncercare atunci când anumite sisteme răspund cu o eroare este o altă modalitate de a preveni defecțiuni mai mari ale sistemului.

## Omul în buclă

O altă modalitate eficientă de a construi sisteme de agenți AI demni de încredere este utilizarea unui Om în buclă. Acest lucru creează un flux în care utilizatorii pot oferi feedback agenților în timpul rulării. Utilizatorii acționează practic ca agenți într-un sistem multi-agent și oferă aprobarea sau terminarea procesului în desfășurare.

![Omul în buclă](../../../translated_images/ro/human-in-the-loop.5f0068a678f62f4f.webp)

Iată un fragment de cod care folosește AutoGen pentru a arăta cum este implementat acest concept:

```python

# Creează agenții.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Folosește input() pentru a obține intrarea utilizatorului din consolă.

# Creează condiția de terminare care va încheia conversația când utilizatorul spune "APPROVE".
termination = TextMentionTermination("APPROVE")

# Creează echipa.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Rulează conversația și transmite în timp real către consolă.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Folosește asyncio.run(...) când rulezi într-un script.
await Console(stream)

```

## Concluzie

Construirea agenților AI demni de încredere necesită un design atent, măsuri robuste de securitate și iterație continuă. Prin implementarea unor sisteme structurate de meta-prompting, înțelegerea amenințărilor potențiale și aplicarea strategiilor de atenuare, dezvoltatorii pot crea agenți AI care sunt atât siguri, cât și eficienți. În plus, încorporarea unei abordări cu om în buclă asigură că agenții AI rămân aliniați cu nevoile utilizatorilor, minimizând în același timp riscurile. Pe măsură ce AI continuă să evolueze, menținerea unei poziții proactive în privința securității, confidențialității și considerațiilor etice va fi esențială pentru a încuraja încrederea și fiabilitatea în sistemele bazate pe AI.

### Aveți mai multe întrebări despre construirea agenților AI de încredere?

Alăturați-vă [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la ore de consultanță și a primi răspunsuri la întrebările dvs. despre agenții AI.

## Resurse suplimentare

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Prezentare generală Responsible AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Evaluarea modelelor AI generative și a aplicațiilor AI</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Mesaje de sistem pentru siguranță</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Șablon de evaluare a riscurilor</a>

## Lecția precedentă

[Agentic RAG](../05-agentic-rag/README.md)

## Următoarea lecție

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Declinare de responsabilitate**:
Acest document a fost tradus folosind serviciul de traducere automată bazat pe inteligență artificială [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original, în limba sa nativă, trebuie considerat sursa autoritară. Pentru informații critice, se recomandă o traducere profesională realizată de un traducător uman. Nu ne asumăm răspunderea pentru eventualele neînțelegeri sau interpretări eronate care pot apărea în urma utilizării acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->