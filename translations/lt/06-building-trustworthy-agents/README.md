[![Patikimi AI agentai](../../../translated_images/lt/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Spustelėkite aukščiau esančią nuotrauką, norėdami peržiūrėti šios pamokos vaizdo įrašą)_

# Patikimų AI agentų kūrimas

## Įvadas

Šioje pamokoje bus aptariama:

- Kaip kurti ir diegti saugius ir efektyvius AI agentus
- Svarbūs saugumo aspektai kuriant AI agentus.
- Kaip užtikrinti duomenų ir vartotojų privatumo apsaugą kuriant AI agentus.

## Mokymosi tikslai

Baigę šią pamoką, jūs žinosite, kaip:

- Nustatyti ir sumažinti rizikas kuriant AI agentus.
- Įgyvendinti saugumo priemones, kad duomenys ir prieiga būtų tinkamai valdomi.
- Kurti AI agentus, kurie užtikrina duomenų privatumą ir kokybišką vartotojo patirtį.

## Saugumas

Pirmiausia pažvelkime, kaip kurti saugias agentines programas. Sauga reiškia, kad AI agentas veikia pagal numatytą paskirtį. Kaip agentinių programų kūrėjai, turime metodus ir įrankius, leidžiančius maksimaliai padidinti saugumą:

### Sistemos pranešimų sistemos kūrimas

Jeigu kada nors kūrėte AI programą naudodami didelius kalbos modelius (LLM), jūs žinote, kaip svarbu sukurti tvirtą sistemos raginimą ar sistemos pranešimą. Šie raginimai nustato metareglus, instrukcijas ir gairės, kaip LLM bendrauja su vartotoju ir duomenimis.

AI agentams sistemos raginimas yra dar svarbesnis, nes AI agentams reikės itin specifinių instrukcijų, kad galėtų įvykdyti mums skirtas užduotis.

Norėdami sukurti keičiamus sistemos raginimus, galime naudoti sistemos pranešimų sistemą, skirtą sukurti vieną ar daugiau agentų mūsų programoje:

![Sistemos pranešimų sistemos kūrimas](../../../translated_images/lt/system-message-framework.3a97368c92d11d68.webp)

#### 1 žingsnis: Sukurkite metakomandos sistemos pranešimą

Meta raginimą naudos LLM, kad generuotų sistemos raginimus agentams, kuriuos kuriame. Jį projektuojame kaip šabloną, kad galėtume efektyviai kurti kelis agentus, jei prireiks.

Štai pavyzdys metakomandos sistemos pranešimo, kurį pateiktume LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### 2 žingsnis: Sukurkite pagrindinį raginimą

Kitas žingsnis – sukurti pagrindinį raginimą AI agentui apibūdinti. Reikia įtraukti agento vaidmenį, užduotis, kurias agentas atliks, ir kitas agento atsakomybes.

Štai pavyzdys:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### 3 žingsnis: Pateikite pagrindinį sistemos pranešimą LLM

Dabar galime optimizuoti šį sistemos pranešimą, pateikdami metakomandos sistemos pranešimą kaip sistemos pranešimą kartu su mūsų pagrindiniu sistemos pranešimu.

Šis procesas sukurs geriau suprojektuotą sistemos pranešimą, kuris geriau nukreips mūsų AI agentus:

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

#### 4 žingsnis: Iteruokite ir tobulinkite

Šios sistemos pranešimų sistemos vertė yra ta, kad galime lengviau kurti sistemos pranešimus keliems agentams ir laikui bėgant tobulinti pranešimus. Retai pasitaiko, kad iš karto turėtumėte tinkantį sistemos pranešimą visam jūsų atvejui. Gebėjimas daryti mažus pakeitimus ir tobulinimus keičiant pagrindinį sistemos pranešimą ir paleidžiant jį per sistemą leis jums palyginti ir įvertinti rezultatus.

## Grėsmių supratimas

Norint sukurti patikimus AI agentus, svarbu suprasti ir sumažinti rizikas bei grėsmes jūsų AI agentui. Pažvelkime į keletą skirtingų grėsmių AI agentams ir kaip geriau jas suplanuoti bei pasiruošti.

![Grėsmių supratimas](../../../translated_images/lt/understanding-threats.89edeada8a97fc0f.webp)

### Užduotis ir instrukcija

**Aprašymas:** Užpuolikai bando pakeisti AI agento instrukcijas ar tikslus naudodamiesi raginimu ar manipuliuodami įvestimis.

**Sumažinimas:** Atlikite patikrinimus ir įvesties filtrus, kad aptiktumėte potencialiai pavojingus raginimus prieš juos apdorojant AI agentui. Kadangi tokie išpuoliai dažnai reikalauja dažnos sąveikos su agentu, pokalbio apsukų ribojimas yra dar vienas būdas apsisaugoti nuo šių išpuolių.

### Prieiga prie kritinių sistemų

**Aprašymas:** Jei AI agentas turi prieigą prie sistemų ir paslaugų, kuriose saugomi jautrūs duomenys, užpuolikai gali pažeisti ryšį tarp agento ir šių paslaugų. Tai gali būti tiesioginiai išpuoliai arba netiesioginės pastangos gauti informaciją apie šias sistemas per agentą.

**Sumažinimas:** AI agentų prieiga prie sistemų turėtų būti suteikta tik esant poreikiui, kad būtų išvengta tokių išpuolių. Taip pat ryšys tarp agento ir sistemos turi būti saugus. Taikyti autentifikaciją ir prieigos kontrolę taip pat padeda apsaugoti šią informaciją.

### Ištekliai ir paslaugų perkrova

**Aprašymas:** AI agentai gali naudotis įvairiais įrankiais ir paslaugomis užduotims atlikti. Užpuolikai gali pasinaudoti šia galimybe užpulti šias paslaugas siųsdami daug užklausų per AI agentą, dėl ko gali kilti sistemos gedimai ar didelės išlaidos.

**Sumažinimas:** Įgyvendinkite politiką, ribojančią užklausų skaičių, kurias AI agentas gali siųsti paslaugai. Taip pat pokalbio apsukų ir užklausų ribojimas AI agentui yra dar vienas būdas išvengti tokių išpuolių.

### Žinių bazės užnuodijimas

**Aprašymas:** Šio tipo išpuolis nėra nukreiptas tiesiogiai į AI agentą, bet į žinių bazę ir kitas paslaugas, kurias AI agentas naudos. Tai gali apimti duomenų ar informacijos sugadinimą, kurią AI agentas panaudos užduočiai atlikti, dėl ko vartotojui gali būti pateikti šališki arba netikslūs atsakymai.

**Sumažinimas:** Atlikite reguliarią duomenų, kuriuos AI agentas naudos savo veiklos procese, patikrą. Užtikrinkite, kad prieiga prie šių duomenų būtų saugi ir juos galėtų keisti tik patikimi asmenys, kad būtų išvengta šio tipo išpuolių.

### Kaskadinis klaidų efektas

**Aprašymas:** AI agentai naudoja įvairius įrankius ir paslaugas užduotims atlikti. Užpuolėjų sukeltos klaidos gali sukelti gedimus kitose sistemose, prijungtose prie AI agento, dėl ko išpuolis išplinta ir jį sunkiau išspręsti.

**Sumažinimas:** Vienas būdas to išvengti – leisti AI agentui veikti ribotoje aplinkoje, pavyzdžiui, atlikti užduotis Docker konteineryje, kad būtų išvengta tiesioginių sistemos išpuolių. Taip pat sukurti atsarginio veikimo mechanizmus ir pakartotinio bandymo logiką, kai tam tikros sistemos grąžina klaidą, padeda išvengti didesnių sistemos gedimų.

## Žmogus valdyme

Kitas veiksmingas būdas kurti patikimas AI agentų sistemas yra naudoti žmogų valdyme (Human-in-the-loop). Tai sukuria procesą, kai vartotojai gali teikti atsiliepimus agentams vykdymo metu. Vartotojai iš esmės veikia kaip agentai daugiaagentėje sistemoje ir gali patvirtinti ar nutraukti vykdomą procesą.

![Žmogus grandinėje](../../../translated_images/lt/human-in-the-loop.5f0068a678f62f4f.webp)

Čia yra kodo fragmentas, naudojant AutoGen, kuris parodo, kaip įgyvendintas šis konceptas:

```python

# Sukurkite agentus.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Naudokite input() įvesti vartotojo duomenis iš konsolės.

# Sukurkite nutraukimo sąlygą, kuri užbaigs pokalbį, kai vartotojas sakys "PATVIRTINTI".
termination = TextMentionTermination("APPROVE")

# Sukurkite komandą.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Vykdykite pokalbį ir srautu parodykite konsolėje.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Naudokite asyncio.run(...), kai vykdote skriptą.
await Console(stream)

```

## Išvados

Kurti patikimus AI agentus reikalauja kruopštaus projektavimo, tvirtų saugumo priemonių ir nuolatinio tobulinimo. Įdiegę struktūrizuotus metaraginimo metodus, supratę galimas grėsmes ir taikydami rizikos mažinimo strategijas, kūrėjai gali sukurti saugius ir veiksmingus AI agentus. Be to, įtraukdami žmogaus valdymo metodą, užtikrinsite, kad AI agentai išliktų suderinti su vartotojų poreikiais ir sumažintų rizikas. Kadangi AI nuolat vystosi, proaktyvus požiūris į saugumą, privatumo ir etikos klausimus bus pagrindinis veiksnys užtikrinant pasitikėjimą ir patikimumą AI valdomose sistemose.

### Turite daugiau klausimų apie patikimų AI agentų kūrimą?

Prisijunkite prie [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kad susitiktumėte su kitais besimokančiais, dalyvautumėte konsultacijose ir gautumėte atsakymus į savo AI agentų klausimus.

## Papildomi ištekliai

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Atsakingas AI naudojimas – apžvalga</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Generatyvių AI modelių ir AI programų vertinimo metodai</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Saugumo sistemos pranešimai</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Rizikos vertinimo šablonas</a>

## Ankstesnė pamoka

[Agentinis RAG](../05-agentic-rag/README.md)

## Kitas pamoka

[Planavimo dizaino šablonas](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:  
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors stengiamės užtikrinti tikslumą, prašome atkreipti dėmesį, kad automatizuoti vertimai gali turėti klaidų ar netikslumų. Originalus dokumentas gimtąja kalba turėtų būti laikomas oficilia ir pagrindine informacijos versija. Dėl svarbios informacijos rekomenduojama kreiptis į profesionalius žmogaus vertėjus. Mes neatsakome už bet kokius nesusipratimus ar neteisingus aiškinimus, kylančius dėl šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->