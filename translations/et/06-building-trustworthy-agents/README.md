[![Usaldusväärsed tehisintellekti agendid](../../../translated_images/et/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klõpsake ülaloleval pildil, et vaadata selle õppetunni videot)_

# Usaldusväärsete tehisintellekti agentide loomine

## Sissejuhatus

Selles õppetükis käsitletakse:

- Kuidas ehitada ja juurutada turvalisi ning tõhusaid tehisintellekti agente
- Olulisi turvaküsimusi tehisintellekti agentide arendamisel
- Kuidas säilitada andmete ja kasutajate privaatsust tehisintellekti agentide arendamisel

## Õpieesmärgid

Pärast selle õppetüki läbimist oskate:

- Tuvastada ja leevendada riske tehisintellekti agentide loomisel
- Rakendada turvameetmeid, et tagada andmete ja juurdepääsu nõuetekohane haldamine
- Luua tehisintellekti agente, kes säilitavad andmete privaatsuse ja pakuvad kvaliteetset kasutajakogemust

## Turvalisus

Vaatleme esmalt agentipõhiste turvaliste rakenduste loomist. Turvalisus tähendab, et tehisintellekti agent toimib vastavalt ette nähtule. Agentipõhiste rakenduste ehitajatena on meil meetodid ja tööriistad, et maksimeerida turvalisust:

### Süsteemisõnumiraamistiku loomine

Kui olete kunagi ehitanud tehisintellekti rakendust, kasutades Suuri Keelemudeleid (LLMs), teate, kui oluline on tugeva süsteemipäringu või süsteemisõnumi kujundamine. Need päringud määratlevad meta-reeglid, juhised ja suunised selle kohta, kuidas LLM suhtleb kasutaja ja andmetega.

Tehisintellekti agentide puhul on süsteemipäring veelgi olulisem, kuna agentidel on vaja väga spetsiifilisi juhiseid, et täita meie jaoks kavandatud ülesandeid.

Skaalautuvate süsteemipäringute loomiseks võime kasutada süsteemisõnumiraamistikku ühe või mitme agendi ehitamiseks meie rakenduses:

![Süsteemisõnumiraamistiku loomine](../../../translated_images/et/system-message-framework.3a97368c92d11d68.webp)

#### Samm 1: Loo meta-süsteemisõnum 

Meta-päringut kasutab LLM süsteemisõnumite genereerimiseks agentidele, keda me loome. Kavandame selle mallina, et saaksime vajaduse korral tõhusalt luua mitut agenti.

Siin on näide meta-süsteemisõnumist, mille me LLM-ile annaksime:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Samm 2: Loo põhiprompt

Järgmine samm on luua põhiprompt, mis kirjeldab tehisintellekti agenti. Peaksite kaasama agendi rolli, ülesanded, mida agent täidab, ja kõik muud agendi vastutusalad.

Siin on näide:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Samm 3: Esita põhisüsteemisõnum LLM-ile

Nüüd saame seda süsteemisõnumit optimeerida, esitades meta-süsteemisõnumi süsteemisõnumina ja meie põhisüsteemisõnumi.

See genereerib süsteemisõnumi, mis on paremini kavandatud meie tehisintellekti agentide juhendamiseks:

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

#### Samm 4: Itereeri ja paranda

Selle süsteemisõnumiraamistiku väärtus seisneb võimaluses skaleerida mitme agendi süsteemisõnumite loomist ning oma süsteemisõnumeid aja jooksul parandada. Harva juhtub, et teil on esimesel katsel süsteemisõnum, mis sobib täielikult teie kasutusjuhtumile. Võimalus teha väikseid näpukaid ja parendusi, muutes põhisüsteemisõnumit ja lastes selle läbi süsteemi, võimaldab teil võrrelda ja hinnata tulemusi.

## Ohtude mõistmine

Usaldusväärsete tehisintellekti agentide loomiseks on oluline mõista ja leevendada agentidele suunatud riske ja ohte. Vaatame mõningaid erinevaid ohte tehisintellekti agentide suhtes ja kuidas nendeks paremini planeerida ja valmistuda.

![Ohtude mõistmine](../../../translated_images/et/understanding-threats.89edeada8a97fc0f.webp)

### Ülesanne ja juhised

**Kirjeldus:** Ründajad püüavad muuta agendi juhiseid või eesmärke läbi päringute või sisendite manipuleerimise.

**Leevendamine**: Tehke valideerimiskontrolle ja sisendifiltreid, et tuvastada potentsiaalselt ohtlikud päringud enne, kui neid agent töötleb. Kuna need rünnakud nõuavad tavaliselt sagedast suhtlust agendiga, on vestluse käikude arvu piiramine veel üks viis nende rünnakute tõkestamiseks.

### Juurdepääs kriitilistele süsteemidele

**Kirjeldus**: Kui tehisintellekti agentil on juurdepääs süsteemidele ja teenustele, mis hoiavad tundlikke andmeid, võivad ründajad ohustada kommunikatsiooni agenti ja nende teenuste vahel. Need võivad olla otsesed rünnakud või kaudsed katsed saada teavet nende süsteemide kohta läbi agendi.

**Leevendamine**: Agentidel peaks olema juurdepääs süsteemidele ainult siis, kui see on vajalik, et vältida selliseid rünnakuid. Kommunikatsioon agendi ja süsteemi vahel peaks samuti olema turvaline. Autentimise ja juurdepääsukontrolli rakendamine on teine viis selle teabe kaitsmiseks.

### Ressursside ja teenuste ülekoormus

**Kirjeldus:** Tehisintellekti agentidel võib olla juurdepääs erinevatele tööriistadele ja teenustele ülesannete täitmiseks. Ründajad saavad seda võimet ära kasutada, saates agendi kaudu teenustele suure hulga päringuid, mis võib põhjustada süsteemirikkeid või suuri kulusid.

**Leevendamine:** Rakendage poliitikad, mis piiravad, kui palju päringuid agent võib teenusele teha. Vestluse käikude ja päringute arvu piiramine teie agendi suhtes on veel üks viis nende rünnakute tõkestamiseks.

### Teadmistebaasi mürgitamine

**Kirjeldus:** See tüüpi rünnak ei sihi agenti otseselt, vaid teadmistebaasi ja muid teenuseid, mida agent kasutab. See võib hõlmata andmete või informatsiooni korruptsiooni, mida agent kasutab ülesande täitmiseks, põhjustades kallutatud või soovimatuid vastuseid kasutajale.

**Leevendamine:** Kontrollige regulaarselt andmeid, mida agent oma töövoogudes kasutab. Tagage andmetele turvaline juurdepääs ja lubade muutmine ainult usaldusväärsete isikute poolt, et vältida sellist rünnakut.

### Kaskaadvead

**Kirjeldus:** Agentid kasutavad ülesannete täitmiseks erinevaid tööriistu ja teenuseid. Ründajate põhjustatud vead võivad viia teiste süsteemide riketeni, millega agent on ühendatud, muutes rünnaku laiemaks ja raskemini tõrgetuvaks.

**Leevendamine**: Üks meetod selle vältimiseks on lasta agendil töötada piiratud keskkonnas, näiteks teha ülesandeid Docker-konteineris, et vältida otseseid rünnakuid süsteemile. Ka alternatiivsete mehhanismide ja taaskäivituse loogika loomine, kui teatud süsteemid vastavad veaga, on teine viis suuremate süsteemirikete ärahoidmiseks.

## Inimene silmuses

Veel üks tõhus viis usaldusväärsete tehisintellekti agendisüsteemide loomiseks on inimesega silmuses (human-in-the-loop) kasutamine. See loob voogu, kus kasutajad saavad jooksvalt anda agentidele tagasisidet. Kasutajad toimivad sisuliselt agentidena mitme-agendi süsteemis ja annavad heakskiitu või lõpetavad jooksva protsessi.

![Inimene silmuses](../../../translated_images/et/human-in-the-loop.5f0068a678f62f4f.webp)

Siin on AutoGen-i kasutav koodilõik, mis näitab, kuidas seda kontseptsiooni rakendatakse:

```python

# Loo agendid.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Kasuta input() kasutaja sisendi saamiseks konsoolist.

# Loo lõpetamistingimus, mis lõpetab vestluse, kui kasutaja ütleb "APPROVE".
termination = TextMentionTermination("APPROVE")

# Loo meeskond.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Käivita vestlus ja voogesta see konsooli.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Kasuta asyncio.run(...), kui käivitad skripti.
await Console(stream)

```

## Kokkuvõte

Usaldusväärsete tehisintellekti agentide loomine nõuab hoolikat kujundust, tugevaid turvameetmeid ja pidevat iteratsiooni. Struktureeritud meta-päringute süsteemide rakendamise, võimalike ohtude mõistmise ja leevendusstrateegiate kasutuselevõtuga saavad arendajad luua agente, kes on nii turvalised kui ka tõhusad. Lisaks tagab inimese silmuses lähenemine, et agentid jäävad kooskõlla kasutajate vajadustega, vähendades samal ajal riske. Kuna tehisintellekt jätkab arenemist, on proaktiivne hoiak turvalisuse, privaatsuse ja eetiliste kaalutluste osas võtmetähtsusega usalduse ja usaldusväärsuse edendamisel tehisintellektil põhinevates süsteemides.

### Kas teil on veel küsimusi usaldusväärsete tehisintellekti agentide loomise kohta?

Liituge [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kogukonnaga, et kohtuda teiste õppuritega, osaleda konsultatsioonidel ja saada vastuseid oma AI-agentide küsimustele.

## Lisamaterjalid

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Vastutustundliku tehisintellekti ülevaade</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Generatiivsete AI mudelite ja AI-rakenduste hindamine</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Turvalisuse süsteemisõnumid</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Riskihindamise mall</a>

## Eelmine õppetund

[Agentne RAG](../05-agentic-rag/README.md)

## Järgmine õppetund

[Planeerimise disainimuster](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Vastutusest loobumine:

See dokument on tõlgitud tehisintellekti tõlketeenuse Co-op Translator (https://github.com/Azure/co-op-translator) abil. Kuigi püüame tagada täpsust, tuleb arvestada, et automaatsed tõlked võivad sisaldada vigu või ebatäpsusi. Originaaldokument selle emakeeles tuleks pidada autoriteetseks allikaks. Olulise teabe puhul on soovitatav kasutada professionaalset inimtõlget. Me ei vastuta selle tõlke kasutamisest tulenevate arusaamatuste või valesti tõlgendamise eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->