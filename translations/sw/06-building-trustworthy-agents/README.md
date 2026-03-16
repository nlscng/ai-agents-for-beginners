[![Wakala wa AI wa Kuaminika](../../../translated_images/sw/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Bonyeza picha hapo juu kuona video ya somo hili)_

# Kujenga Wakala wa AI wa Kuaminika

## Utangulizi

Somo hili litajumuisha:

- Jinsi ya kujenga na kupeleka Wakala wa AI salama na wenye ufanisi
- Mambo muhimu ya usalama wakati wa kuendeleza Wakala wa AI.
- Jinsi ya kudumisha faragha ya data na mtumiaji wakati wa kuendeleza Wakala wa AI.

## Malengo ya Kujifunza

Baada ya kumaliza somo hili, utajua jinsi ya:

- Kubaini na kupunguza hatari wakati wa kuunda Wakala wa AI.
- Kutekeleza hatua za usalama kuhakikisha kuwa data na upatikanaji vinadhibitiwa kwa usahihi.
- Kuunda Wakala wa AI wanaodumisha faragha ya data na kutoa uzoefu bora kwa mtumiaji.

## Usalama

Kwanza tuangalie kujenga programu za wakala salama. Usalama unamaanisha kuwa wakala wa AI anafanya kazi kama ilivyopangwa. Kama wajenzi wa programu za wakala, tuna mbinu na zana za kuongeza usalama:

### Kujenga Mfumo wa Ujumbe wa Mfumo

Ikiwa umewahi kujenga programu ya AI ukitumia Modeli Kubwa za Lugha (LLM), unajua umuhimu wa kubuni kauli ya mfumo thabiti au ujumbe wa mfumo. Kauli hizi huanzisha kanuni, maelekezo, na miongozo ya jinsi LLM itakavyoshirikiana na mtumiaji na data.

Kwa Wakala wa AI, kauli ya mfumo ni muhimu zaidi kwani Wakala wa AI watahitaji maelekezo maalum sana ili kukamilisha kazi tulizozibuni kwao.

Ili kuunda kauli za mfumo zinazoweza kupanuka, tunaweza kutumia mfumo wa ujumbe wa mfumo kwa ajili ya kujenga wakala mmoja au zaidi katika programu yetu:

![Kujenga Mfumo wa Ujumbe wa Mfumo](../../../translated_images/sw/system-message-framework.3a97368c92d11d68.webp)

#### Hatua 1: Tengeneza Ujumbe wa Meta wa Mfumo

Kauli ya meta itatumika na LLM kutengeneza kauli za mfumo kwa wakala tunaoanzisha. Tunaiunda kama kiolezo ili tuweze kuunda wakala wengi kwa ufanisi ikiwa zinazohitajika.

Hapa ni mfano wa ujumbe wa meta wa mfumo ambao tutampa LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Hatua 2: Tengeneza kauli ya msingi

Hatua inayofuata ni kuunda kauli ya msingi kuelezea Wakala wa AI. Unapaswa kujumuisha jukumu la wakala, kazi ambazo wakala atakamilisha, na majukumu mengine yoyote ya wakala.

Hapa ni mfano:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Hatua 3: Toa Ujumbe wa Mfumo wa Msingi kwa LLM

Sasa tunaweza kuboresha ujumbe huu wa mfumo kwa kutoa ujumbe wa meta wa mfumo kama ujumbe wa mfumo na ujumbe wetu wa mfumo wa msingi.

Hii itazalisha ujumbe wa mfumo uliobuniwa vyema kuongoza wakala wetu wa AI:

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

#### Hatua 4: Rudia na Boresha

Thamani ya mfumo huu wa ujumbe wa mfumo ni kuwezesha kukuza utengenezaji wa ujumbe wa mfumo kutoka kwa wakala wengi kwa urahisi pamoja na kuboresha ujumbe wako wa mfumo kadri ya wakati. Ni nadra kuwa na ujumbe wa mfumo unaofanya kazi mara ya kwanza kwa matumizi yako kamili. Kuwa na uwezo wa kufanya mabadiliko madogo na maboresho kwa kubadilisha ujumbe wa msingi wa mfumo na kuuharakisha kupitia mfumo kutakuwezesha kulinganisha na kuthamini matokeo.

## Kuelewa Vitisho

Ili kujenga wakala wa AI wa kuaminika, ni muhimu kuelewa na kupunguza hatari na vitisho vinavyomkabili wakala wako wa AI. Tuchukulie baadhi tu ya vitisho tofauti kwa wakala wa AI na jinsi unavyoweza kupanga na kujiandaa vyema kwazvo.

![Kuelewa Vitisho](../../../translated_images/sw/understanding-threats.89edeada8a97fc0f.webp)

### Kazi na Maelekezo

**Maelezo:** Wavamizi hujaribu kubadilisha maelekezo au malengo ya wakala wa AI kupitia uanzishaji au kudanganya pembejeo.

**Kupunguza Hatari**: Fanya ukaguzi wa uthibitisho na vichujio vya pembejeo kugundua maelekezo yenye hatari kabla hayajatambuliwa na Wakala wa AI. Kwa kuwa mashambulizi haya kwa kawaida yanahitaji mwingiliano wa mara kwa mara na Wakala, kupunguza idadi ya mizunguko katika mazungumzo ni njia nyingine ya kuzuia aina hizi za mashambulizi.

### Upatikanaji kwa Mifumo Muhimu

**Maelezo:** Ikiwa wakala wa AI ana upatikanaji kwa mifumo na huduma zinazohifadhi data nyeti, wavamizi wanaweza kuvuruga mawasiliano kati ya wakala na huduma hizi. Haya yanaweza kuwa mashambulizi ya moja kwa moja au jaribio la kupata taarifa kuhusu mifumo hii kupitia wakala.

**Kupunguza Hatari:** Wakala wa AI wanapaswa kuwa na upatikanaji wa mifumo kwa msingi wa haja tu ili kuzuia aina hizi za mashambulizi. Mawasiliano kati ya wakala na mfumo pia yanapaswa kuwa salama. Kutekeleza uthibitishaji na udhibiti wa upatikanaji ni njia nyingine ya kulinda taarifa hii.

### Kumbukumbu ya Rasilimali na Huduma Zaidi ya Kulevya

**Maelezo:** Wakala wa AI wanaweza kupata zana na huduma tofauti kukamilisha kazi. Wavamizi wanaweza kutumia uwezo huu kushambulia huduma hizi kwa kutuma maombi mengi kupitia Wakala wa AI, jambo ambalo linaweza kusababisha kushindwa kwa mifumo au gharama kubwa.

**Kupunguza Hatari:** Tekeleza sera za kupunguza idadi ya maombi ambayo wakala wa AI anaweza kutuma kwa huduma. Kupunguza idadi ya mizunguko ya mazungumzo na maombi kwa wakala wako wa AI ni njia nyingine ya kuzuia aina hizi za mashambulizi.

### Uchafuzi wa Msingi wa Maarifa

**Maelezo:** Aina hii ya shambulio hailengi wakala wa AI moja kwa moja bali inalenga msingi wa maarifa na huduma nyingine ambazo wakala wa AI atazitumia. Hii inaweza kujumuisha kuharibu data au taarifa ambazo wakala wa AI atazitumia kukamilisha kazi, na kusababisha majibu yenye upendeleo au yasiyokusudiwa kwa mtumiaji.

**Kupunguza Hatari:** Fanya uhakiki wa mara kwa mara wa data ambazo wakala wa AI atazitumia katika mizunguko yake ya kazi. Hakikisha upatikanaji wa data hii ni salama na unabadilishwa tu na watu wa kuaminika ili kuepuka aina hii ya mashambulio.

### Makosa Yanayotiririka

**Maelezo:** Wakala wa AI hupata zana na huduma mbalimbali kukamilisha kazi. Makosa yanayosababishwa na wavamizi yanaweza kusababisha kushindwa kwa mifumo mingine ambayo wakala wa AI ameunganishwa nayo, na kufanya shambulio kuwa pana zaidi na kuwa vigumu kufuatilia.

**Kupunguza Hatari:** Njia moja ya kuzuia hili ni kuwa Wakala wa AI afanye kazi katika mazingira yaliyodhibitiwa, kama kufanya kazi katika kontena la Docker, ili kuzuia mashambulio ya moja kwa moja kwa mfumo. Kuunda mifumo ya kurudi nyuma na mantiki ya kurudia wakati mifumo fulani inarudisha kosa ni njia nyingine ya kuzuia kushindwa mkubwa kwa mifumo.

## Mtu Katika Mzunguko

Njia nyingine yenye ufanisi ya kujenga mifumo ya Wakala wa AI wa kuaminika ni kutumia Mtu Katika Mzunguko. Hii huunda mtiririko ambapo watumiaji wanaweza kutoa maoni kwa Wakala wakati wa utekelezaji. Watumiaji kwa kimsingi hufanya kazi kama wakala katika mfumo wa wakala wengi na kwa kutoa idhini au kusitisha mchakato unaoendeshwa.

![Mtu Katika Mzunguko](../../../translated_images/sw/human-in-the-loop.5f0068a678f62f4f.webp)

Hapa kuna kifungu cha nambari kinachotumia AutoGen kuonyesha jinsi dhana hii inavyotekelezwa:

```python

# Unda mawakala.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Tumia input() kupata maingizo ya mtumiaji kutoka kwenye console.

# Unda hali ya kukomesha ambayo itamaliza mazungumzo wakati mtumiaji anasema "KUBALI".
termination = TextMentionTermination("APPROVE")

# Unda timu.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Endesha mazungumzo na uteleze kwenye console.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Tumia asyncio.run(...) unapokimbia katika script.
await Console(stream)

```

## Hitimisho

Kujenga wakala wa AI wa kuaminika kunahitaji muundo makini, hatua thabiti za usalama, na mazunguko ya kuendelea ya kuboresha. Kwa kutekeleza mifumo ya kuhimiza meta iliyopangwa kwa muundo, kuelewa vitisho vinavyowezekana, na kutumia mikakati ya kupunguza hatari, waendelezaji wanaweza kuunda wakala wa AI ambao ni salama na wenye ufanisi. Zaidi ya hayo, kuingiza njia ya mtu katika mzunguko huhakikisha kuwa wakala wa AI wanabaki sambamba na mahitaji ya watumiaji huku wakipunguza hatari. Kadri AI inavyoendelea, kudumisha msimamo wa kujiandaa mapema kwa usalama, faragha, na maadili kutakuwa muhimu kukuza kuaminika na uthabiti katika mifumo inayotegemea AI.

### Una Maswali Zaidi kuhusu Kujenga Wakala wa AI wa Kuaminika?

Jiunge na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kukutana na wanafunzi wengine, kuhudhuria saa za ofisi na kupata majibu ya maswali yako kuhusu Wakala wa AI.

## Rasilimali Zaidi

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Muhtasari wa AI Inayewajibika</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Tathmini ya mifano ya AI ya uumbaji na programu za AI</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Ujumbe wa mfumo wa usalama</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Kiolezo cha Tathmini ya Hatari</a>

## Somo la Awali

[Agentic RAG](../05-agentic-rag/README.md)

## Somo Linalofuata

[Mfumo wa Mchoro wa Mipango](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Tangazo la Hukumu**:  
Hati hii imetafsiriwa kwa kutumia huduma ya utafsiri wa AI [Co-op Translator](https://github.com/Azure/co-op-translator). Ingawa tunajitahidi kupata usahihi, tafadhali fahamu kuwa tafsiri za kiotomatiki zinaweza kuwa na makosa au kutotangamana kabisa. Hati asili katika lugha yake ya asili inapaswa kuzingatiwa kama chanzo cha mamlaka. Kwa taarifa muhimu, tafsiri ya kitaalamu ya binadamu inapendekezwa. Hatuna dhamana kwa maelezo yaliyokosewa au kutafsiriwa vibaya yanayotokana na matumizi ya tafsiri hii.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->