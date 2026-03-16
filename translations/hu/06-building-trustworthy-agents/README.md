[![Megbízható MI-ügynökök](../../../translated_images/hu/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Kattintson a fenti képre a tanóra videójának megtekintéséhez)_

# Megbízható MI-ügynökök építése

## Bevezetés

Ez az óra a következőket tárgyalja:

- Hogyan építsünk és telepítsünk biztonságos és hatékony MI-ügynököket
- Fontos biztonsági megfontolások MI-ügynökök fejlesztésekor.
- Hogyan őrizzük meg az adatok és a felhasználók magánéletét MI-ügynökök fejlesztése során.

## Tanulási célok

A lecke elvégzése után tudni fogja, hogyan:

- Azonosítani és mérsékelni a kockázatokat MI-ügynökök létrehozásakor.
- Biztonsági intézkedéseket bevezetni annak biztosítására, hogy az adatok és a hozzáférés megfelelően legyenek kezelve.
- Olyan MI-ügynököket létrehozni, amelyek megőrzik az adatvédelmet és minőségi felhasználói élményt nyújtanak.

## Biztonság

Először nézzük meg a biztonságos ügynöki alkalmazások építését. A biztonság azt jelenti, hogy a MI-ügynök a tervezett módon működik. Ügynöki alkalmazások fejlesztőjeként rendelkezünk módszerekkel és eszközökkel a biztonság maximalizálásához:

### Rendszerüzenet-keretrendszer felépítése

Ha valaha épített már MI-alkalmazást nagynyelvű modellek (LLM-ek) használatával, ismeri egy robusztus rendszerutasítás vagy rendszerüzenet megtervezésének fontosságát. Ezek az utasítások megállapítják a meta szabályokat, irányelveket és útmutatásokat arra vonatkozóan, hogyan lépjen kapcsolatba az LLM a felhasználóval és az adatokkal.

Az MI-ügynökök esetében a rendszerutasítás még fontosabb, mivel az ügynököknek rendkívül specifikus utasításokra lesz szükségük a számukra tervezett feladatok elvégzéséhez.

Skálázható rendszerüzenetek létrehozásához használhatunk egy rendszerüzenet-keretrendszert, amely egy vagy több ügynök felépítésére alkalmas az alkalmazásunkban:

![Rendszerüzenet-keretrendszer létrehozása](../../../translated_images/hu/system-message-framework.3a97368c92d11d68.webp)

#### 1. lépés: Meta rendszerüzenet létrehozása

A meta utasítást egy LLM fogja használni az általunk létrehozott ügynökök számára készülő rendszerutasítások generálására. Sablonként tervezzük meg, hogy hatékonyan tudjunk több ügynököt létrehozni szükség esetén.

Íme egy példa egy meta rendszerüzenetre, amelyet az LLM-nek adnánk:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### 2. lépés: Alapvető utasítás létrehozása

A következő lépés egy alapvető utasítás létrehozása az MI-ügynök leírására. Tartalmaznia kell az ügynök szerepét, azokat a feladatokat, amelyeket az ügynök elvégez, valamint az ügynök egyéb felelősségeit.

Íme egy példa:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### 3. lépés: Alap rendszerüzenet átadása az LLM-nek

Most optimalizálhatjuk ezt a rendszerüzenetet úgy, hogy a meta rendszerüzenetet rendszerüzenetként és az alap rendszerüzenetet átadjuk az LLM-nek.

Ez egy olyan rendszerüzenetet fog eredményezni, amely jobban alkalmas az MI-ügynökeink irányítására:

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

#### 4. lépés: Iterálás és fejlesztés

Ennek a rendszerüzenet-keretrendszernek az értéke abban rejlik, hogy könnyebbé teszi több ügynök rendszerüzeneteinek skálázását, valamint a rendszerüzenetek időbeli fejlesztését. Ritka, hogy az első próbálkozásra olyan rendszerüzenetet kapunk, amely a teljes felhasználási esetünkhöz tökéletesen megfelel. Ha képesek vagyunk apró módosításokat és javításokat végezni az alap rendszerüzeneten, és átfuttatni azt a rendszeren, akkor összehasonlíthatjuk és kiértékelhetjük az eredményeket.

## A fenyegetések megértése

A megbízható MI-ügynökök építéséhez fontos megérteni és mérsékelni az ügynökre irányuló kockázatokat és fenyegetéseket. Nézzük meg csak néhányat a különböző fenyegetések közül, és hogy hogyan lehet jobban tervezni és felkészülni rájuk.

![A fenyegetések megértése](../../../translated_images/hu/understanding-threats.89edeada8a97fc0f.webp)

### Feladat és utasítás

**Leírás:** A támadók megkísérlik megváltoztatni az MI-ügynök utasításait vagy céljait kérésekkel (prompting) vagy a bemenetek manipulálásával.

**Mérséklés**: Végezzen érvényesítési ellenőrzéseket és alkalmazzon bemeneti szűrőket, hogy észlelje a potenciálisan veszélyes kéréseket, mielőtt azokat az MI-ügynök feldolgozná. Mivel ezek a támadások általában gyakori interakciót igényelnek az ügynökkel, a beszélgetés fordulóinak számának korlátozása szintén módja ezeknek a támadásoknak a megelőzésére.

### Hozzáférés kritikus rendszerekhez

**Leírás**: Ha egy MI-ügynök hozzáfér az érzékeny adatokat tároló rendszerekhez és szolgáltatásokhoz, a támadók kompromittálhatják az ügynök és ezek a szolgáltatások közötti kommunikációt. Ezek lehetnek közvetlen támadások vagy közvetett próbálkozások, hogy az ügynökön keresztül információt szerezzenek ezekről a rendszerekről.

**Mérséklés**: Az MI-ügynökök csak szükség esetén kapjanak hozzáférést a rendszerekhez az ilyen típusú támadások megelőzése érdekében. Az ügynök és a rendszer közötti kommunikációnak szintén biztonságosnak kell lennie. Az autentikáció és a hozzáférés-vezérlés bevezetése további módja ezen információk védelmének.

### Erőforrás- és szolgáltatás-túlterhelés

**Leírás:** Az MI-ügynökök különböző eszközökhöz és szolgáltatásokhoz férhetnek hozzá a feladatok elvégzéséhez. A támadók kihasználhatják ezt a képességet azáltal, hogy az MI-ügynökön keresztül nagy mennyiségű kérést küldenek ezeknek a szolgáltatásoknak, ami rendszerszintű hibákhoz vagy magas költségekhez vezethet.

**Mérséklés:** Alkalmazzon irányelveket az MI-ügynök által egy szolgáltatásnak küldhető kérések számának korlátozására. A beszélgetés fordulóinak és az MI-ügynök felé küldött kérések számának korlátozása szintén módja ezen típusú támadások megelőzésének.

### Tudásbázis megmérgezése

**Leírás:** Ez a típusú támadás nem közvetlenül az MI-ügynökre irányul, hanem azokra a tudásbázisokra és egyéb szolgáltatásokra, amelyeket az MI-ügynök használni fog. Ez magában foglalhatja az adatok vagy információk sérülését, amelyeket az MI-ügynök egy feladat elvégzéséhez használna, és torz vagy nem szándékos válaszokat eredményez a felhasználó számára.

**Mérséklés:** Végezzen rendszeres ellenőrzést azokon az adatokon, amelyeket az MI-ügynök a munkafolyamataiban fog használni. Biztosítsa, hogy ezen adatokhoz való hozzáférés biztonságos legyen, és csak megbízható személyek által legyen módosítható az ilyen típusú támadás elkerülése érdekében.

### Láncolódó hibák

**Leírás:** Az MI-ügynökök különböző eszközökhöz és szolgáltatásokhoz férnek hozzá a feladatok elvégzéséhez. A támadók által okozott hibák más rendszerek meghibásodásához vezethetnek, amelyekhez az MI-ügynök csatlakozik, így a támadás szélesebb körűvé válik és nehezebb hibakeresni.

**Mérséklés**: Egy módszer ennek elkerülésére, ha az MI-ügynök korlátozott környezetben működik, például egy Docker-konténerben végzi a feladatokat, hogy megakadályozzuk a közvetlen rendszerellenes támadásokat. Visszaesési mechanizmusok és újrapróbálkozási logika létrehozása, amikor bizonyos rendszerek hibával válaszolnak, szintén módja a nagyobb rendszerszintű meghibásodások megelőzésének.

## Humán a hurokban

Egy másik hatékony módja a megbízható MI-ügynök rendszerek építésének a humán a hurokban (human-in-the-loop) használata. Ez egy olyan folyamatot hoz létre, ahol a felhasználók futás közben visszajelzést adhatnak az ügynököknek. A felhasználók lényegében ügynökként működnek egy többügynökös rendszerben, és jóváhagyással vagy a futó folyamat leállításával befolyásolhatják azt.

![Humán a hurokban](../../../translated_images/hu/human-in-the-loop.5f0068a678f62f4f.webp)

Íme egy kódrészlet az AutoGen használatával, amely bemutatja, hogyan valósítják meg ezt a koncepciót:

```python

# Hozza létre az ügynököket.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Használja az input() függvényt a felhasználó konzolbeli bevitelének megszerzéséhez.

# Hozza létre a leállítási feltételt, amely befejezi a beszélgetést, amikor a felhasználó azt mondja: "APPROVE".
termination = TextMentionTermination("APPROVE")

# Hozza létre a csapatot.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Futtassa a beszélgetést, és írja ki folyamatosan a konzolra.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Használja az asyncio.run(...)-t, amikor egy szkriptből futtatja.
await Console(stream)

```

## Következtetés

A megbízható MI-ügynökök építése gondos tervezést, robusztus biztonsági intézkedéseket és folyamatos iterációt igényel. Strukturált meta-prompt rendszer bevezetésével, a lehetséges fenyegetések megértésével és mérséklési stratégiák alkalmazásával a fejlesztők biztonságos és hatékony MI-ügynököket hozhatnak létre. Emellett a human-in-the-loop megközelítés beépítése biztosítja, hogy az MI-ügynökök összhangban maradjanak a felhasználói igényekkel, miközben minimalizálják a kockázatokat. Ahogy az MI tovább fejlődik, a biztonság, az adatvédelem és az etikai megfontolások proaktív szemlélete kulcsfontosságú lesz a bizalom és a megbízhatóság elősegítésében az MI-vezérelt rendszerekben.

### További kérdése van a megbízható MI-ügynökök építésével kapcsolatban?

Csatlakozzon a [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) közösségéhez, hogy találkozzon más tanulókkal, részt vegyen konzultációs órákon és választ kapjon az MI-ügynökökkel kapcsolatos kérdéseire.

## További források

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Felelős MI áttekintése</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Generatív MI modellek és MI-alkalmazások értékelése</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Biztonsági rendszerüzenetek</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Kockázatértékelési sablon</a>

## Előző lecke

[Agentic RAG](../05-agentic-rag/README.md)

## Következő lecke

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Felelősségkizárás:
Ezt a dokumentumot az AI-alapú fordítószolgáltatás, a Co-op Translator (https://github.com/Azure/co-op-translator) segítségével fordították. Bár törekszünk a pontosságra, kérjük, vegye figyelembe, hogy az automatikus fordítások hibákat vagy pontatlanságokat tartalmazhatnak. Az eredeti, anyanyelvű dokumentum tekintendő irányadónak. Fontos információk esetén profi, emberi fordítást javasolunk. Nem vállalunk felelősséget az e fordítás használatából eredő félreértésekért vagy helytelen értelmezésekért.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->