[![நம்பகமான AI முகவர்கள்](../../../translated_images/ta/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(இந்த பாடம் காண வீடியோவைப் பார்க்க மேலே உள்ள படத்தை கிளிக் செய்யவும்)_

# நம்பகமான AI முகவர்களை உருவாக்குதல்

## அறிமுகம்

இந்த பாடத்தில் சேர்க்கப்படும் விஷயங்கள்:

- பாதுகாப்பான மற்றும் பயனுள்ள AI முகவர்களை எவ்வாறு உருவாக்கி பிரத்தியேகப்படுத்துவது
- AI முகவர்களை உருவாக்கும் போது முக்கியமான பாதுகாப்பு பரிசீலனைகள்.
- AI முகவர்களை உருவாக்கும் போது தரவு மற்றும் பயனர் தனியுரிமையை எவ்வாறு பராமரிப்பது.

## கற்றல் இலக்குகள்

இந்த பாடத்தை முடித்த பின், நீங்கள் அறிந்துகொள்ள இருப்பீர்கள்:

- AI முகவர்களை உருவாக்கும் போது ஆபத்துக்களை கண்டறிந்து குறைக்கும் விதம்.
- தரவையும் அணுகலைவும் முறையான முறையில் நிர்வகிக்க பாதுகாப்பு நடவடிக்கைகளை செயல்படுத்தல்.
- தரவு தனியுரிமையை பராமரிக்கும் மற்றும் உயர்தர பயனர் அனுபவத்தை வழங்கும் AI முகவர்களை உருவாக்குதல்.

## பாதுகாப்பு

முதலில், பாதுகாப்பான முகவரி செயலியங்களை உருவாக்குவோம். பாதுகாப்பு என்பது AI முகவர் திட்டமிடப்பட்டபடி செயல்படுவதை 의미ப் படுத்தும். முகவரி செயலிகளின் உருவாக்குநர்களாக நாம் பாதுகாப்பை அதிகரிக்க முறைமைகள் மற்றும் கருவிகள் வைத்துள்ளோம்:

### ஒரு அமைப்பு செய்தி கட்டமைப்பினை உருவாக்குதல்

நீங்கள் எப்போதாவது பெரிய மொழிப் மாதிரிகளை (LLMs) பயன்படுத்தி AI செயலியை உருவாக்கியிருந்தால், ஒரு வலுவான அமைப்பு ப்ராம்ட் அல்லது அமைப்பு செய்தியின் முக்கியத்துவத்தை அறிந்திருக்கிறீர்கள். இவ்வாறு ப்ராம்ட்கள் LLM பயனர் மற்றும் தரவுடன் எப்படி தொடர்பு கொள்வதற்கான மேட்டா விதிகள், கட்டளைகள் மற்றும் வழிகாட்டுதல்களை அமைக்கும்.

AI முகவர்களுக்கு, அமைப்பு ப்ராம்ட் இன்னும் முக்கியமாக இருக்கும், ஏனெனில் நாம் வடிவமைத்த பணிகளை AI முகவர்கள் மிகவும் குறிப்பிட்ட வழிகாட்டுதலுடன் நிறைவேற்ற வேண்டும்.

செயலியில் ஒரு அல்லது பல முகவர்களை உருவாக்க அமைப்பு ப்ராம்ட் கட்டமைப்பைப் பயன்படுத்தி பரிமாணமான அமைப்பு ப்ராம்ட்களை உருவாக்கலாம்:

![ஒரு அமைப்பு செய்தி கட்டமைப்பை உருவாக்குதல்](../../../translated_images/ta/system-message-framework.3a97368c92d11d68.webp)

#### படி 1: ஒரு மேட்டா அமைப்பு செய்தியை உருவாக்குதல்

மேட்டா ப்ராம்ட் LLM-ஐ பயன்படுத்தி நாங்கள் உருவாக்கும் முகவர்களுக்கு அமைப்பு ப்ராம்ட்களை உருவாக்கப் பயன்படுத்தப்படும். இது நாங்கள் பல முகவர்களை திறம்பட உருவாக்க ஒரு வார்ப்புருவாக வடிவமைக்கப்படுகிறது.

இது LLM-க்கு கொடுக்கும் ஒரு மேட்டா அமைப்பு செய்தி உதாரணம்:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### படி 2: அடிப்படை ப்ராம்ட்டை உருவாக்குதல்

அடுத்த படி AI முகவரியை விவரிக்க அடிப்படை ப்ராம்ட்டை உருவாக்குவதாகும். முகவரியின் பங்கை, அவர் முடிப்பதற்கான பணிகளையும் மற்றும் பிற பொறுப்புகளையும் சேர்க்கவேண்டும்.

இது ஒரு உதாரணம்:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### படி 3: அடிப்படை அமைப்பு செய்தியை LLM-க்கு வழங்குதல்

இப்போது இந்த அமைப்பு செய்தியை மேலமைப்பு அமைப்பு செய்தியாகவும், எங்கள் அடிப்படை அமைப்பு செய்தியாகவும் கொடுத்து அதிகரிக்கலாம்.

இது நம் AI முகவர்களை வழிநடத்த சிறந்த அமைப்பு செய்தியை உருவாக்கும்:

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

#### படி 4: மீண்டும் செய்யவும் மேம்படுத்தவும்

இந்த அமைப்பு செய்தி கட்டமைப்பின் முக்கியம் பல முகவரிகளுக்கு அமைப்பு செய்திகளை எளிதாக உருவாக்கவும், உங்கள் அமைப்பு செய்திகளை காலப்போக்கில் மேம்படுத்தவும் செயல் படுத்தும் திறன் ஆகும். உங்கள் முழு பயன்படுத்தும் வழக்குக்கு முதல் முறையில் சரியான அமைப்பு செய்தி உள்ளது என்பது அரிது. அடிப்படை அமைப்பு செய்தியை மாற்றி முயற்சி செய்து, முடிவுகளை ஒப்பீட்டு மதிப்பாய்வு செய்யும் வாய்ப்பு உண்டு.

## ஆபத்துக்களைப் புரிந்து கொள்ளுதல்

நம்பகமான AI முகவர்களை உருவாக்க, உங்கள் AI முகவருக்கான ஆபத்துக்கள் மற்றும் அபாயங்களை புரிந்து கொண்டு குறைக்குதல் முக்கியம். AI முகவர்களுக்கு உண்டான சில ஆபத்துக்களையும், அவற்றை எப்படி திட்டமிட்டு முன்னெடுக்கலாம் என்பதையும் பார்ப்போம்.

![ஆபத்துக்களைப் புரிந்து கொள்ளுதல்](../../../translated_images/ta/understanding-threats.89edeada8a97fc0f.webp)

### பணிகள் மற்றும் கட்டளைகள்

**விளக்கம்:** தாக்குநர்கள் AI முகவரின் கட்டளைகள் அல்லது குறிக்கோள்களை மாற்ற முயலுகிறார்கள், இது ப்ராம்டிங் அல்லது உள்ளீட்டுகளை மாற்றுவதன் மூலம் இருக்கும்.

**குறைப்பு**: AI முகவர் செயல்முறைக்கு முன் ஆபத்தான ப்ராம்ட்களை கண்டறிய செல்லுபடியான பரிசோதனைகள் மற்றும் உள்ளீட்டு வடிகட்டிகளைப் பயன்படுத்தவும். இந்த தாக்குதல்களுக்கு முகவருடன் அடிக்கடி தொடர்பு வேண்டியிருக்கும் என்பதால், உரையாடல் திருப்புகளின் எண்ணிக்கையை குறைப்பதுவும் பாதுகாப்பு வாயிலாக இருக்கும்.

### முக்கிய அமைப்புகளுக்கு அணுகல்

**விளக்கம்**: AI முகவர் முக்கிய தரவு சேமிப்பிடங்கள் மற்றும் சேவைகளுக்கு அணுகல் இருந்தால், தாக்குநர்கள் முகவருக்கிடையேயான தொடர்பை குற்றவடுத்தலாம். இது நேரடி தாக்குதலாக இருக்கலாம் அல்லது முகவரின் மூலம் அவற்றை பற்றிய தகவலைத் தேடும் முயற்சியாக இருக்கலாம்.

**குறைப்பு**: AI முகவர்களுக்கு தேவையானவை மட்டுமே அணுகலை வழங்க வேண்டும். முகவருக்கும் அமைப்புக்கும் இடையேயான தொடர்பு பாதுகாப்பானதாக இருக்க வேண்டும். அங்கீகாரம் மற்றும் அணுகல் கட்டுப்பாடுகளை நிறைவேற்றுவதும் பாதுகாப்புக்கு உதவும்.

### வளங்களும் சேவைகளும் அதிகபடியான சுமை ஏற்றல்

**விளக்கம்:** AI முகவர்கள் பணிகளை நிறைவேற்ற பல கருவிகள் மற்றும் சேவைகளை அணுக முடியும். தாக்குநர்கள் அதிக எண்ணிக்கையில் கோரிக்கைகளை அனுப்ப AI முகவரின் திறனைக் கண்காணித்து சேவைகளை தாக்க முடியும், இதனால் அமைப்பு தோல்விகள் அல்லது உயர்ந்த செலவுகள் ஏற்படக்கூடும்.

**குறைப்பு:** AI முகவர் ஒரு சேவைக்கு செய்யக்கூடிய கோரிக்கைகளின் எண்ணிக்கையை வரையறுக்கும் கொள்கைகளை செயல்படுத்தவும். உரையாடல் திருப்புகள் மற்றும் கோரிக்கைகளின் எண்ணிக்கையை கட்டுப்படுத்துவதும் இதே வகை தாக்குதல்களை தடுக்கும் வழியாகும்.

### அறிவுத் தரவுத்தொகுப்பு விஷம் சேர்க்கல்

**விளக்கம்:** இந்தத் தாக்குதல் நேரடியாக AI முகவரைக் குறிவைக்காது, ஆனால் பயனப்படும் அறிவுத் தரவுத்தொகுப்பையும் பிற சேவைகளையும் குறிவைக்கிறது. இதனால் AI முகவர் பணிகளை முடிக்க பயன்படுத்தும் தரவு அல்லது தகவலை கெடுப்பதோடு, பாகுபாடான அல்லது எதிர்பாராத பதில்களை உண்டாக்கும்.

**குறைப்பு:** AI முகவர் பணியில் பயன்படுத்தும் தரவுகளை முறையாக ஆய்வு செய்யவும். இந்த தரவுகளில் அணுக்கல் பாதுகாப்புடன் இருக்க வேண்டும் மற்றும் நம்பகமான நபர்களால் மட்டுமே மாற்றப்பட வேண்டும்.

### தொடர்ச்சியான பிழைகள்

**விளக்கம்:** AI முகவர்கள் பல சேவைகருவிகளுடன் தொடர்பு கொண்டிருப்பதால், தாக்குநர்களால் ஏற்படும் பிழைகள் தொடர்புடைய மற்ற அமைப்புகளின் தோல்விக்கு வழிவகுக்கும், இது தாக்குதலை பரவலாகவும் சிக்கலாகவும் ஆக்கும்.

**குறைப்பு**: ஒரு முறையாக, AI முகவர்க்கு கட்டுப்படுத்தப்பட்ட சூழலில் (என்கிறால் Docker கன்டெய்னரில்தான் பணிகளை செய்ய) செயல்பட வைக்க வேண்டும். மேலும் சில სისტემ்கள் பிழைத் தெரிவிக்கும் போதும், மறு முயற்சி மற்றும் பிழை மீட்பு வழிமுறைகளை உருவாக்கவும்.

## மனிதன்-இன்-தி-லூப்

நம்பகமான AI முகவர் அமைப்புகளை உருவாக்க மற்றொரு பயனுள்ள வழி மனிதன்-இன்-தி-லூப்பைப் பயன்படுத்துவதாகும். இது பயனர்கள் முகவர்களுக்கு ஓர் இயங்கும் போது கருத்துக்களை வழங்கும் ஓர் பணிவழியை உருவாக்குகிறது. பயனர்கள் பல முகவர் அமைப்பில் முகவர்கள் போன்று செயல்பட்டு, ஓரும் செயல்முறைக்கு அனுமதி அல்லது நிறுத்தலை வழங்குகிறார்கள்.

![மனிதன்-இன்-தி-லூப்](../../../translated_images/ta/human-in-the-loop.5f0068a678f62f4f.webp)

இந்தக் கருத்தைப் பதிவு செய்ய AutoGen ஐ பயன்படுத்திய ஒரு குறியீட்டு துண்டு இங்கே உள்ளது:

```python

# ஏஜென்ட்களை உருவாக்கவும்.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # console இலிருந்து பயனர் உள்ளீட்டை பெற input() ஐ பயன்படுத்தவும்.

# பயனர் "APPROVE" என்பதினால் உரையாடலை நிறுத்தும் முடிவு நிபந்தனையை உருவாக்கவும்.
termination = TextMentionTermination("APPROVE")

# குழுவை உருவாக்கவும்.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# உரையாடலை இயக்கி console க்கு ஸ்ட்ரீம் செய்யவும்.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# ஸ்கிரிப்டில் இயக்கும் போது asyncio.run(...) ஐ பயன்படுத்தவும்.
await Console(stream)

```

## முடிவு

நம்பகமான AI முகவர்களை உருவாக்குவது கவனமாக வடிவமைப்பு, வலுவான பாதுகாப்பு நடவடிக்கைகள், மற்றும் தொடர்ந்து மேம்படுத்துதலைத் தேவைப்படுத்தும். கட்டமைக்கப்பட்ட மேட்டா ப்ராம்டிங் அமைப்புகளை செயல்படுத்துவதும், சாத்தியமான ஆபத்துக்களை புரிந்துகொள்வதும், குறைப்புக் கொள்கைகளை பயன்படுத்துவதும், பாதுகாப்பான மற்றும் பயனுள்ள AI முகவர்களை உருவாக்க உதவும். கூடுதலாக, மனிதன்-இன்-தி-லூப் அணுகுமுறையை இணைப்பது AI முகவர்கள் பயனர் தேவைகளுடன் தழுவியிருக்கும் என்று உறுதிசெய்கிறது மேலும் ஆபத்துக்களை குறைக்கும். AI வளர்ச்சியுடன், பாதுகாப்பு, தனியுரிமை மற்றும் நெறிமுறை பரிசீலனைகளில் முன்னோடி நிலைப்பாட்டை பராமரிப்பது AI சார்ந்த அமைப்புகளில் நம்பிக்கை மற்றும் நம்பகத்தன்மையை வளர்க்க முக்கியம்.

### நம்பகமான AI முகவர்களை உருவாக்குவதில் கூடுதல் கேள்விகள் உள்ளதா?

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) இணைந்து மற்ற கற்றார்களுடன் சந்தித்து, அலுவலக நேரங்களில் கலந்துகொண்டு உங்கள் AI முகவர் கேள்விகளுக்கு பதில் பெறுங்கள்.

## கூடுதல் வளங்கள்

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">பொறுப்புடைய AI மேற்பார்வை</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">உருவாக்கும் AI மாதிரிகளின் மற்றும் AI செயலிகளின் மதிப்பீடு</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">பாதுகாப்பு அமைப்பு செய்திகள்</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">ஆபத்து மதிப்பீட்டு டெம்ப்ளேட்</a>

## முந்தைய பாடம்

[Agentic RAG](../05-agentic-rag/README.md)

## அடுத்த பாடம்

[திட்டமிடல் வடிவமைப்பு முறை](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**மறுப்பு**:
இந்த ஆவணம் AI மொழிபெயர்ப்பு சேவை [Co-op Translator](https://github.com/Azure/co-op-translator) பயன்படுத்தி மொழிபெயர்க்கப்பட்டுள்ளது. நாங்கள் துல்லியத்திற்காக முயற்சிக்கிறோம், இருப்பினும் தானியங்கி மொழிபெயர்ப்புகளில் பிழைகள் அல்லது துல்லியக்குறைவுகள் இருக்கக்கூடும் என்பதைக் கருத்தில் கொள்ளவும். உள்ளூர் மொழியில் உள்ள அசல் ஆவணம் அதிகாரப்பூர்வ ஆதாரமாக கருதப்பட வேண்டியது அவசியம். முக்கிய தகவல்களுக்கு, வீட்டு வல்லுநர் மனித மொழிபெயர்ப்பை பரிந்துரைக்கிறோம். இந்த மொழிபெயர்ப்பைப் பயன்படுத்துவதால் ஏற்படும் தவறான புரிதல்கள் அல்லது தவறான விளக்கங்களுக்கு நாங்கள் பொறுப்பானவர்கள் அல்ல.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->