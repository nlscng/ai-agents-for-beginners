[![Trustworthy AI Agents](../../../translated_images/pa/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(ਇਸ ਪਾਠ ਦਾ ਵੀਡੀਓ ਦੇਖਣ ਲਈ ਉਪਰ ਦਿੱਤੀ ਤਸਵੀਰ 'ਤੇ ਕਲਿੱਕ ਕਰੋ)_

# ਭਰੋਸੇਯੋਗ AI ਏਜੰਟ ਬਣਾਉਣਾ

## ਤਾਰੁਫ਼

ਇਸ ਪਾਠ ਵਿੱਚ ਕਵਰ ਕੀਤਾ ਜਾਵੇਗਾ:

- ਸੁਰੱਖਿਅਤ ਅਤੇ ਪ੍ਰਭਾਵਸ਼ালী AI ਏਜੰਟ ਕਿਵੇਂ ਬਣਾਏ ਅਤੇ ਤਾਇਨਾਤ ਕੀਤੇ ਜਾਣ।
- AI ਏਜੰਟ ਵਿਕਸਿਤ ਕਰਦਿਆਂ ਮਹੱਤਵਪੂਰਨ ਸੁਰੱਖਿਆ ਵਿਚਾਰ।
- AI ਏਜੰਟ ਵਿਕਸਿਤ ਕਰਦਿਆਂ ਡਾਟਾ ਅਤੇ ਉਪਭੋਗਤਾ ਦੀ ਗੋਪਨੀਯਤਾ ਕਿਵੇਂ ਬਰਕਰਾਰ ਰਖੀ ਜਾਵੇ।

## ਸਿੱਖਣ ਦੇ ਲਕੜੀ

ਇਸ ਪਾਠ ਨੂੰ ਮੁਕੰਮਲ ਕਰਨ ਤੋਂ ਬਾਅਦ, ਤੁਸੀਂ ਜਾਣੋਗੇ ਕਿ:

- AI ਏਜੰਟ ਬਣਾਉਂਦੇ ਸਮੇਂ ਖ਼ਤਰੇ ਕਿਵੇਂ ਚਿਨ੍ਹਿਤ ਕਰੇ ਅਤੇ ਉਨ੍ਹਾਂ ਨੂੰ ਘਟਾਏ।
- ਇਹ ਸੁਨਿਸ਼ਚਿਤ ਕਰਨ ਲਈ ਸੁਰੱਖਿਆ ਉਪਾਅ ਕਿਵੇਂ ਲਾਗੂ ਕੀਤੇ ਜਾਣ ਕਿ ਡਾਟਾ ਅਤੇ ਪਹੁੰਚ ਸਹੀ ਢੰਗ ਨਾਲ ਪ੍ਰਬੰਧਿਤ ਹਨ।
- ਐਸੇ AI ਏਜੰਟ ਬਣਾਉ ਜੋ ਡਾਟਾ ਗੋਪਨੀਯਤਾ ਬਰਕਰਾਰ ਰੱਖਣ ਅਤੇ ਉੱਚ ਗੁਣਵੱਤਾ ਯੂਜ਼ਰ ਅਨੁਭਵ ਪ੍ਰਦਾਨ ਕਰਨ।

## ਸੁਰੱਖਿਆ

ਆਓ ਸਭ ਤੋਂ ਪਹਿਲਾਂ ਸੁਰੱਖਿਅਤ ਏਜੰਟਿਕ ਐਪਲੀਕੇਸ਼ਨਾਂ ਬਨਾਉਣ ਬਾਰੇ ਵੇਖੀਏ। ਸੁਰੱਖਿਆ ਦਾ ਮਤਲਬ ਹੈ ਕਿ AI ਏਜੰਟ ਡਿਜ਼ਾਇਨ ਅਨੁਸਾਰ ਕਾਰਗਰ ਹੈ। ਏਜੰਟਿਕ ਐਪਲੀਕੇਸ਼ਨਾਂ ਦੇ ਨਿਰਮਾਤਾ ਵਜੋਂ ਸਾਡੇ ਕੋਲ ਸੁਰੱਖਿਆ ਨੂੰ ਵੱਧ ਤੋਂ ਵੱਧ ਕਰਨ ਲਈ ਤਰੀਕੇ ਅਤੇ ਸੰਦ ਹਨ:

### ਸਿਸਟਮ ਮੈਸੇਜ ਫ੍ਰੇਮਵਰਕ ਤਿਆਰ ਕਰਨਾ

ਜੇ ਤੁਸੀਂ ਕਦੇ ਵੱਡੇ ਭਾਸ਼ਾ ਮਾਡਲ (LLMs) ਦੀ ਵਰਤੋਂ ਕਰਕੇ AI ਐਪਲੀਕੇਸ਼ਨ ਬਣਾਈ ਹੈ, ਤਾਂ ਤੁਸੀਂ ਜਾਣਦੇ ਹੋ ਕਿ ਮਜ਼ਬੂਤ ਸਿਸਟਮ ਪ੍ਰਾਂਪਟ ਜਾਂ ਸਿਸਟਮ ਮੈਸੇਜ ਡਿਜ਼ਾਇਨ ਕਰਨ ਦੀ ਮਹੱਤਤਾ ਕੀ ਹੈ। ਇਹ ਪ੍ਰਾਂਪਟ ਮੈਟਾ ਨਿਯਮ, ਹਦਾਇਤਾਂ ਅਤੇ ਦਿਸ਼ਾ-ਨਿਰਦੇਸ਼ ਤੈਅ ਕਰਦੇ ਹਨ ਕਿ LLM ਕਿਵੇਂ ਉਪਭੋਗਤਾ ਅਤੇ ਡਾਟਾ ਨਾਲ ਇੰਟਰਐਕਟ ਕਰੇਗਾ।

AI ਏਜੰਟਾਂ ਲਈ, ਸਿਸਟਮ ਪ੍ਰਾਂਪਟ ਹੋਰ ਵੀ ਜ਼ਿਆਦਾ ਮਹੱਤਵਪੂਰਨ ਹੈ ਕਿਉਂਕਿ AI ਏਜੰਟਾਂ ਨੂੰ ਅਜਿਹੀਆਂ ਵਿਸ਼ੇਸ਼ ਹਦਾਇਤਾਂ ਦੀ ਲੋੜ ਹੁੰਦੀ ਹੈ ਜੋ ਅਸੀਂ ਉਨ੍ਹਾਂ ਲਈ ਤੈਅ ਕੀਤੀਆਂ ਟਾਸਕਾਂ ਨੂੰ ਪੂਰਾ ਕਰਨ ਲਈ ਦਿੱਤੀਆਂ ਹਨ।

ਵੱਧ ਤੋਂ ਵੱਧ ਸਕੇਲਬਲ ਸਿਸਟਮ ਪ੍ਰਾਂਪਟ ਬਣਾਉਣ ਲਈ, ਅਸੀਂ ਆਪਣੇ ਐਪਲੀਕੇਸ਼ਨ ਵਿੱਚ ਇੱਕ ਜਾਂ ਵੱਧ ਏਜੰਟ ਬਨਾਉਣ ਲਈ ਸਿਸਟਮ ਮੈਸੇਜ ਫ੍ਰੇਮਵਰਕ ਦੀ ਵਰਤੋਂ ਕਰ ਸਕਦੇ ਹਾਂ:

![Building a System Message Framework](../../../translated_images/pa/system-message-framework.3a97368c92d11d68.webp)

#### ਕਦਮ 1: ਇਕ ਮੈਟਾ ਸਿਸਟਮ ਮੈਸੇਜ ਬਣਾਓ

ਮੈਟਾ ਪ੍ਰਾਂਪਟ LLM ਵੱਲੋਂ ਉਹ ਸਿਸਟਮ ਪ੍ਰਾਂਪਟ ਜਨਰੇਟ ਕਰਨ ਲਈ ਵਰਤਿਆ ਜਾਵੇਗਾ ਜੋ ਅਸੀਂ ਬਣਾਉਂਦੇ ਏਜੰਟਾਂ ਲਈ ਹੈ। ਅਸੀਂ ਇਸਨੂੰ ਇੱਕ ਟੈਮਪਲੇਟ ਵਜੋਂ ਤਿਆਰ ਕਰਦੇ ਹਾਂ ਤਾਂ ਜੋ ਜੇ ਲੋੜ ਹੋਵੇ ਤਾਂ ਅਸੀਂ ਅਸਾਨੀ ਨਾਲ ਕਈ ਏਜੰਟ ਬਣਾਉਣ ਵਿੱਚ ਸਮਰੱਥ ਹੋਈਏ।

ਇੱਥੇ ਇੱਕ ਮੈਟਾ ਸਿਸਟਮ ਮੈਸੇਜ ਦਾ ਉਦਾਹਰਨ ਹੈ ਜੋ ਅਸੀਂ LLM ਨੂੰ ਦੇਵਾਂਗੇ:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### ਕਦਮ 2: ਇੱਕ ਆਧਾਰਭੂਤ ਪ੍ਰਾਂਪਟ ਬਣਾਓ

ਅਗਲਾ ਕਦਮ ਇੱਕ ਆਧਾਰਭੂਤ ਪ੍ਰਾਂਪਟ ਬਣਾਉਣਾ ਹੈ ਜੋ AI ਏਜੰਟ ਦਾ ਵਰਣਨ ਕਰੇ। ਤੁਹਾਨੂੰ ਏਜੰਟ ਦਾ ਰੋਲ, ਉਸ ਦੇ ਕਰਨ ਵਾਲੇ ਕੰਮ ਅਤੇ ਹੋਰ ਜ਼ਿੰਮੇਵਾਰੀਆਂ ਸ਼ਾਮਲ ਕਰਨੀ ਚਾਹੀਦੀ ਹੈ।

ਇੱਥੇ ਇੱਕ ਉਦਾਹਰਨ ਹੈ:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### ਕਦਮ 3: ਆਧਾਰਭੂਤ ਸਿਸਟਮ ਮੈਸੇਜ ਨੂੰ LLM ਨੂੰ ਦਿਓ

ਹੁਣ ਅਸੀਂ ਇਸ ਸਿਸਟਮ ਮੈਸੇਜ ਨੂੰ ਉੱਤਮ ਬਣਾਉਣ ਲਈ ਮੈਟਾ ਸਿਸਟਮ ਮੈਸੇਜ ਅਤੇ ਸਾਡਾ ਆਧਾਰਭੂਤ ਸਿਸਟਮ ਮੈਸੇਜ ਦੋਹਾਂ ਨੂੰ ਸਿਸਟਮ ਮੈਸੇਜ ਵਜੋਂ ਦਿੰਦੇ ਹਾਂ।

ਇਹ ਇਕ ਐਸਾ ਸਿਸਟਮ ਮੈਸੇਜ ਤੈਅ ਕਰੇਗਾ ਜੋ ਸਾਡੇ AI ਏਜੰਟਾਂ ਦੀ ਮਦਦ ਕਰਨ ਲਈ ਬਿਹਤਰ ਹੋਵੇਗਾ:

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

#### ਕਦਮ 4: ਦੁਹਰਾਈ ਕਰੋ ਅਤੇ ਸੁਧਾਰ ਕਰੋ

ਇਸ ਸਿਸਟਮ ਮੈਸੇਜ ਫ੍ਰੇਮਵਰਕ ਦੀ ਕੀਮਤ ਇਹ ਹੈ ਕਿ ਇਹ ਵੱਖ-ਵੱਖ ਏਜੰਟਾਂ ਤੋਂ ਸਿਸਟਮ ਮੈਸੇਜ ਬਣਾਉਣ ਨੂੰ ਅਸਾਨ ਬਣਾਉਂਦਾ ਹੈ ਅਤੇ ਸਮੇਂ ਦੇ ਨਾਲ ਤੁਹਾਡੇ ਸਿਸਟਮ ਮੈਸੇਜਾਂ ਨੂੰ ਸੁਧਾਰਨ ਦਾ ਮੌਕਾ ਦਿੰਦਾ ਹੈ। ਕਮਿਊਨਲ ਵਾਰੀ, ਤੁਹਾਡੇ ਕੋਲ ਪਹਿਲੀ ਵਾਰਾਂ ਆਪਣੇ ਪੂਰੇ ਉਪਯੋਗ ਕੇਸ ਲਈ ਬਿਲਕੁਲ ਠੀਕ ਕੰਮ ਕਰਨ ਵਾਲਾ ਸਿਸਟਮ ਮੈਸੇਜ ਹੁੰਦਾ ਹੈ। ਛੋਟੇ ਬਦਲਾਅ ਕਰਨ ਅਤੇ ਆਧਾਰਭੂਤ ਸਿਸਟਮ ਮੈਸੇਜ ਨੂੰ ਬਦਲ ਕੇ ਬਿਹਤਰ ਨਤੀਜੇ ਪ੍ਰਾਪਤ ਕਰਨ ਦੇ ਯੋਗ ਹੋਣ ਨਾਲ ਤੁਸੀਂ ਨਤੀਜਿਆਂ ਦੀ ਤੁਲਨਾ ਅਤੇ ਮੂਲਾਂਕਣ ਕਰ ਸਕਦੇ ਹੋ।

## ਖਤਰੇ ਸਮਝਣਾ

ਭਰੋਸੇਯੋਗ AI ਏਜੰਟ ਬਣਾਉਣ ਲਈ, ਤੁਹਾਡੇ AI ਏਜੰਟ ਨੂੰ ਸਾਮਨਾ ਕਰਨ ਵਾਲੇ ਖਤਰਿਆਂ ਅਤੇ ਖਤਮ ਕਰਨ ਦੀ ਵਰਤੋਂ ਨੂੰ ਸਮਝਣਾ ਬਹੁਤ ਜਰੂਰੀ ਹੈ। ਆਓ ਸਿਰਫ ਕੁਝ ਖਤਰਿਆਂ ਨੂੰ ਵੇਖੀਏ ਜੋ AI ਏਜੰਟਾਂ ਨੂੰ ਜੂਝਦੇ ਹਨ ਅਤੇ ਤੁਸੀਂ ਉਹਨਾਂ ਲਈ ਬਿਹਤਰ ਤਰੀਕੇ ਨਾਲ ਯੋਜਨਾ ਬਣਾ ਸਕਦੇ ਹੋ।

![Understanding Threats](../../../translated_images/pa/understanding-threats.89edeada8a97fc0f.webp)

### ਟਾਸਕ ਅਤੇ ਹਦਾਇਤ

**ਵੇਰਵਾ:** ਹਮਲਾਵਰ AI ਏਜੰਟ ਦੀਆਂ ਹਦਾਇਤਾਂ ਜਾਂ ਲਕੜੀ-ਮਕਸਦ ਵਿਚ ਬਦਲਾਅ ਲਿਆਂਦੇ ਹਨ ਜਿਵੇਂ ਕਿ ਪ੍ਰਾਂਪਟਿੰਗ ਜਾਂ ਇਨਪੁਟਸ ਨੂੰ ਮਨੀਪੁਲੇਟ ਕਰਕੇ।

**ਘਟਾਓ:** ਸੁਰੱਖਿਅਤ ਪ੍ਰਾਂਪਟ ਦੀ ਪਛਾਣ ਕਰਨ ਅਤੇ ਪ੍ਰੋਸੈਸ ਤੋਂ ਪਹਿਲਾਂ ਖ਼ਤਰਨਾਕ ਪ੍ਰਾਂਪਟਾਂ ਦਾ ਪਤਾ ਲਗਾਉਣ ਲਈ ਵੈਧਤਾ ਜਾਂਚ ਅਤੇ ਇਨਪੁਟ ਫਿਲਟਰ ਚਲਾਓ। ਚੁਕਿ ਇਹ ਹਮਲੇ ਵਧੀਕ ਸੰਪਰਕ ਕਰਦੇ ਹਨ, ਸਮੱਗਰੀ ਦੀ ਗੱਲਬਾਤ ਦਾ ਸੱਤਾਸੱਤਰ ਸੀਮਾ ਕਰਨਾ ਵੀ ਇਨ੍ਹਾਂ ਹਮਲਿਆਂ ਨੂੰ ਰੋਕਣ ਦਾ ਤਰੀਕਾ ਹੈ।

### ਸੰਵੇਦਨਸ਼ੀਲ ਸਿਸਟਮਾਂ ਤੱਕ ਪਹੁੰਚ

**ਵੇਰਵਾ:** ਜੇ ਕੋਈ AI ਏਜੰਟ ਸੈਂਸਿਟਿਵ ਡਾਟਾ ਸਟੋਰ ਕਰਨ ਵਾਲੇ ਸਿਸਟਮਾਂ ਅਤੇ ਸੇਵਾਵਾਂ ਤੱਕ ਪਹੁੰਚ ਰੱਖਦਾ ਹੈ, ਤਾਂ ਹਮਲਾਵਰ ਉਸ ਏਜੰਟ ਅਤੇ ਸੰਬੰਧਿਤ ਸੇਵਾਵਾਂ ਵਿਚਕਾਰ ਸੰਚਾਰ ਨੂੰ ਭੰਗ ਕਰ ਸਕਦੇ ਹਨ। ਇਹ ਸਿੱਧੇ ਹਮਲੇ ਹੋ ਸਕਦੇ ਹਨ ਜਾਂ ਬੇਪਾਸੇ ਕੋਸ਼ਿਸ਼ਾਂ ਜੋ ਇਹ ਸਿਸਟਮ ਜਾਣਨ ਲਈ ਏਜੰਟ ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹਨ।

**ਘਟਾਓ:** AI ਏਜੰਟਾਂ ਨੂੰ ਝੂਠੇ ਹਮਲੇ ਰੋਕਣ ਲਈ ਸਿਰਫ਼ ਜ਼ਰੂਰਤ ਮੁਤਾਬਕ ਹੀ ਸਿਸਟਮ ਤੱਕ ਪਹੁੰਚ ਦੇਣੀ ਚਾਹੀਦੀ ਹੈ। ਏਜੰਟ ਅਤੇ ਸਿਸਟਮ ਵਿਚਕਾਰ ਸੰਚਾਰ ਨੂੰ ਸੁਰੱਖਿਅਤ ਬਣਾਉਣਾ ਚਾਹੀਦਾ ਹੈ। ਪ੍ਰਮਾਣਿਕਤਾ ਅਤੇ ਪਹੁੰਚ ਕੰਟਰੋਲ ਲਾਗੂ ਕਰਨਾ ਇਸ ਜਾਣਕਾਰੀ ਦੀ ਸੁਰੱਖਿਆ ਲਈ ਹੋਰ ਤਰੀਕਾ ਹੈ।

### ਸਰੋਤ ਅਤੇ ਸੇਵਾ ਡਾਲੋਡਿੰਗ

**ਵੇਰਵਾ:** AI ਏਜੰਟ ਟਾਸਕ ਪੂਰੇ ਕਰਨ ਲਈ ਵੱਖ-ਵੱਖ ਸੰਦਾਂ ਅਤੇ ਸੇਵਾਵਾਂ ਤੱਕ ਪਹੁੰਚ ਕਰਦੇ ਹਨ। ਹਮਲਾਵਰ AI ਏਜੰਟ ਰਾਹੀਂ ਜ਼ਿਆਦਾਤਰ ਬੇਨਤੀਆਂ ਭੇਜ ਕੇ ਇਹ ਸੇਵਾਵਾਂ 'ਤੇ ਹਮਲਾ ਕਰ ਸਕਦੇ ਹਨ, ਜਿਸ ਨਾਲ ਸਿਸਟਮ ਫੇਲ੍ਹ ਜਾਂ ਚੁੰਗੇ ਖਰਚੇ ਹੋ ਸਕਦੇ ਹਨ।

**ਘਟਾਓ:** ਨੀਤੀ ਬਣਾਈਏ ਜੋ AI ਏਜੰਟ ਦੇ ਵੱਲੋਂ ਸੇਵਾ ਨੂੰ ਕੀਤੀਆਂ ਬੇਨਤੀਆਂ ਦੀ ਗਿਣਤੀ ਸੀਮਤ ਕਰੇ। ਗੱਲਬਾਤ ਦੇ ਟਰਨ ਅਤੇ AI ਏਜੰਟ ਨੂੰ ਬੇਨਤੀਆਂ ਦੀ ਗਿਣਤੀ ਸੀਮਤ ਕਰਨਾ ਵੀ ਐਸੇ ਹਮਲਿਆਂ ਨੂੰ ਰੋਕਣ ਦਾ ਤਰੀਕਾ ਹੈ।

### ਗਿਆਨ ਆਧਾਰ ਜ਼ਹਿਰਲੋਪਣ

**ਵੇਰਵਾ:** ਇਹ ਸਿਰਫ਼ AI ਏਜੰਟ ਨੂੰ ਸਿੱਧਾ ਨਿਸ਼ਾਨਾ ਨਹੀਂ ਬਣਾ ਰਿਹਾ ਪਰ ਉਹ ਗਿਆਨ ਆਧਾਰ ਅਤੇ ਹੋਰ ਸੇਵਾਵਾਂ ਹਨ ਜੋ AI ਏਜੰਟ ਟਾਸਕ ਪੂਰੀ ਕਰਨ ਲਈ ਵਰਤੇਗਾ। ਇਹ ਡਾਟਾ ਜਾਂ ਜਾਣਕਾਰੀ ਨੂੰ ਖਰਾਬ ਕਰ ਸਕਦਾ ਹੈ ਜਿਸ ਨਾਲ ਉਪਭੋਗਤਾ ਨੂੰ ਪੱਖਪਾਤ ਜਾਂ ਅਣਚਾਹੇ ਜਵਾਬ ਮਿਲ ਸਕਦੇ ਹਨ।

**ਘਟਾਓ:** ਦਿੱਤੇ ਡਾਟੇ ਦੀ ਨਿਯਮਿਤ ਜਾਂਚ ਕਰੋ ਜਿਸਦਾ AI ਏਜੰਟ ਵਰਕਫਲੋਜ਼ ਵਿੱਚ ਇਸਤੇਮਾਲ ਕਰੇਗਾ। ਯਕੀਨੀ ਬਣਾਓ ਕਿ ਇਸ ਡਾਟੇ ਤੱਕ ਪਹੁੰਚ ਸੁਰੱਖਿਅਤ ਹੈ ਅਤੇ ਸਿਰਫ਼ ਭਰੋਸੇਯੋਗ ਵਿਅਕਤੀਆਂ ਦੁਆਰਾ ਬਦਲੀ ਜਾ ਸਕਦੀ ਹੈ ਤਾਂ ਜੋ ਐਸੇ ਹਮਲੇ ਤੋਂ ਬਚਾ ਜਾ ਸਕੇ।

### ਲੜੀਵਾਰ ਗਲਤੀਆਂ

**ਵੇਰਵਾ:** AI ਏਜੰਟ ਵੱਖ-ਵੱਖ ਸੰਦਾਂ ਅਤੇ ਸੇਵਾਵਾਂ ਤੱਕ ਪਹੁੰਚ ਰੱਖਦੇ ਹਨ ਟਾਸਕ ਪੂਰੇ ਕਰਨ ਲਈ। ਹਮਲਾਵਰਾਂ ਵਲੋਂ ਪੈਦਾ ਕੀਤੀਆਂ ਗਲਤੀਆਂ ਹੋਰ ਸਿਸਟਮਾਂ ਦੇ ਫੇਲੁਰੀ ਦਾ ਕਾਰਣ ਬਣ ਸਕਦੀਆਂ ਹਨ ਜੋ AI ਏਜੰਟ ਨਾਲ ਜੁੜੇ ਹਨ, ਜਿਸ ਨਾਲ ਹਮਲਾ ਮਹਿਲ ਤੋਂ ਵੱਧ ਫੈਲਦਾ ਹੈ ਅਤੇ ਸਮੱਸਿਆ ਦਾ ਹੱਲ ਕਰਨਾ ਮੁਸ਼ਕਿਲ ਹੋ ਜਾਂਦਾ ਹੈ।

**ਘਟਾਓ:** ਇੱਕ ਤਰੀਕਾ ਇਹ ਹੈ ਕਿ AI ਏਜੰਟ ਨੁਮਾਇੰਦਗੀ ਹੱਦਬੱਧ ਮਾਹੌਲ ਵਿੱਚ ਕੰਮ ਕਰੇ, ਜਿਵੇਂ ਕਿ Docker ਕੰਟੇਨਰ ਵਿੱਚ ਟਾਸਕ ਕਰਨਾ, ਤਾਂ ਜੋ ਸਿੱਧੇ ਸਿਸਟਮ ਹਮਲੇ ਤੋਂ ਬਚਿਆ ਜਾ ਸਕੇ। ਜਦੋਂ ਕੁਝ ਸਿਸਟਮ ਗਲਤੀ ਦੇ ਨਾਲ ਜਵਾਬ ਦਿੰਦੇ ਹਨ ਤਾਂ ਫਾਲਬੈਕ ਮਕੈਨਿਜ਼ਮ ਅਤੇ ਰੀਟ੍ਰਾਈ ਲ Logic Implement ਕਰਨਾ ਹੋਰ ਇੱਕ ਤਰੀਕਾ ਹੈ ਵੱਡੇ ਸਿਸਟਮੀਕ ਫੇਲਚਰਾਂ ਤੋਂ ਬਚਣ ਲਈ।

## ਮਨੁੱਖ-ਇਨ-ਦ-ਲੂਪ

ਭਰੋਸੇਯੋਗ AI ਏਜੰਟ ਸਿਸਟਮ ਨੂੰ ਬਣਾਉਣ ਦਾ ਇਕ ਹੋਰ ਪ੍ਰਭਾਵਸ਼ਾਲੀ ਤਰੀਕਾ ਮਨੁੱਖ-ਇਨ-ਦ-ਲੂਪ ਵਰਤਣਾ ਹੈ। ਇਹ ਇਕ ਐਸਾ ਪ੍ਰਵਾਹ ਬਣਾਉਂਦਾ ਹੈ ਜਿੱਥੇ ਵਰਤੋਂਕਾਰ ਚੱਲ ਰਹੇ ਪ੍ਰਕਿਰਿਆ ਦੌਰਾਨ ਏਜੰਟਾਂ ਨੂੰ ਫੀਡਬੈਕ ਦੇ ਸਕਦੇ ਹਨ। ਵਰਤੋਂਕਾਰ ਅਸਲ ਵਿੱਚ ਇੱਕ ਬਹੁ-ਏਜੰਟ ਸਿਸਟਮ ਵਿੱਚ ਏਜੰਟ ਵਜੋਂ ਕੰਮ ਕਰਦੇ ਹਨ ਅਤੇ ਚੱਲ ਰਹੇ ਪ੍ਰਕਿਰਿਆ ਨੂੰ ਮਨਜ਼ੂਰੀ ਜਾਂ ਬੰਦ ਕਰਨਗੇ।

![Human in The Loop](../../../translated_images/pa/human-in-the-loop.5f0068a678f62f4f.webp)

ਇਹ ਓਟੋਜਨ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਕੌਡ ਸਨਿੱਪੇਟ ਹੈ ਜੋ ਇਹ ਦਰਸਾਉਂਦਾ ਹੈ ਕਿ ਇਹ ਸਿਧਾਂਤ ਕਿਵੇਂ ਲਾਗੂ ਕੀਤਾ ਗਿਆ ਹੈ:

```python

# ਏਜੰਟ ਬਣਾਓ।
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # ਕੌਨਸੋਲ ਤੋਂ ਉਪਭੋਗਤਾ ਇਨਪੁਟ ਲੈਣ ਲਈ input() ਦਾ ਉਪਯੋਗ ਕਰੋ।

# ਸਮਾਪਤੀ ਸ਼ਰਤ ਬਣਾਓ ਜੋ ਗੱਲਬਾਤ ਨੂੰ ਖਤਮ ਕਰੇਗੀ ਜਦੋਂ ਉਪਭੋਗਤਾ "APPROVE" ਕਹਿੰਦਾ ਹੈ।
termination = TextMentionTermination("APPROVE")

# ਟੀਮ ਬਣਾਓ।
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# ਗੱਲਬਾਤ ਚਲਾਓ ਅਤੇ ਕੌਨਸੋਲ ‘ਤੇ ਦਿਖਾਓ।
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# ਸਕ੍ਰਿਪਟ ਵਿਚ ਚਲਾਉਣ ਸਮੇਂ asyncio.run(...) ਦਾ ਉਪਯੋਗ ਕਰੋ।
await Console(stream)

```

## ਨਤੀਜਾ

ਭਰੋਸੇਯੋਗ AI ਏਜੰਟ ਬਣਾਉਣ ਲਈ ਬਰੀਕੀ ਨਾਲ ਡਿਜ਼ਾਇਨ, ਮਜ਼ਬੂਤ ਸੁਰੱਖਿਆ ਉਪਾਅ ਅਤੇ ਲਗਾਤਾਰ ਸੁਧਾਰ ਦੀ ਲੋੜ ਹੈ। ਸੰਗਠਿਤ ਮੈਟਾ ਪ੍ਰਾਂਪਟਿੰਗ ਸਿਸਟਮਾਂ ਨੂੰ ਲਾਗੂ ਕਰਕੇ, ਸੰਭਾਵਿਤ ਖਤਰਿਆਂ ਨੂੰ ਸਮਝ ਕੇ ਅਤੇ ਘਟਾਓ ਰਣਨੀਤੀਆਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਵਿਕਾਸਕਾਰ ਐਸੇ AI ਏਜੰਟ ਬਣਾ ਸਕਦੇ ਹਨ ਜੋ ਸੁਰੱਖਿਅਤ ਅਤੇ ਪ੍ਰਭਾਵਸ਼ਾਲੀ ਦੋਹਾਂ ਹਨ। ਇਸਦੇ ਨਾਲ, ਮਨੁੱਖ-ਇਨ-ਦ-ਲੂਪ ਪਹੁੰਚ ਜੋੜਨ ਨਾਲ ਯਕੀਨੀ ਬਣਦਾ ਹੈ ਕਿ AI ਏਜੰਟ ਉਪਭੋਗਤਾ ਦੀਆਂ ਲੋੜਾਂ ਨਾਲ ਸਭੰਧਿਤ ਰਹਿੰਦੇ ਹਨ ਅਤੇ ਖਤਰਿਆਂ ਨੂੰ ਘਟਾ ਦਿੰਦੇ ਹਨ। ਜਿਵੇਂ AI ਵਿਕਸਤ ਹੁੰਦਾ ਰਹੇਗਾ, ਸੁਰੱਖਿਆ, ਗੋਪਨੀਯਤਾ ਅਤੇ ਨੈਤਿਕ ਪਹਿਲੂਆਂ 'ਤੇ ਪ੍ਰੋਐਕਟਿਵ ਟਿਕਾਊ ਕੰਮ ਕਰਨਾ AI-ਚਾਲਿਤ ਸਿਸਟਮਾਂ ਵਿੱਚ ਭਰੋਸਾ ਤੇ ਨਿਰਭਰਤਾ ਵਧਾਉਣ ਲਈ ਕੁੰਜੀ ਰਹੇਗਾ।

### ਭਰੋਸੇਯੋਗ AI ਏਜੰਟ ਸਿਰਜਨ ਬਾਰੇ ਹੋਰ ਸਵਾਲ?

ਦੂਜੇ ਸਿੱਖਣ ਵਾਲਿਆਂ ਨਾਲ ਮਿਲਣ ਲਈ, ਦਫਤਰ ਘੰਟਿਆਂ ਵਿੱਚ ਸ਼ਾਮਿਲ ਹੋਣ ਲਈ ਅਤੇ ਆਪਣੇ AI ਏਜੰਟਾਂ ਦੇ ਸਵਾਲਾਂ ਦੇ ਜਵਾਬ ਲਈ [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) ਵਿੱਚ ਜੁੜੋ।

## ਹੋਰ ਸਾਧਨ

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">ਜ਼ਿੰਮੇਵਾਰ AI ਦਾ ਜਾਇਜ਼ਾ</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">ਜਨਰੈਟਿਵ AI ਮਾਡਲਾਂ ਅਤੇ AI ਐਪਲੀਕੇਸ਼ਨਾਂ ਦਾ ਮੂਲਾਂਕਣ</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">ਸੁਰੱਖਿਆ ਸਿਸਟਮ ਸਨੇਹੇ</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">ਖਤਰੇ ਦਾ ਅਸੈਸਮੈਂਟ ਟੈਮਪਲੇਟ</a>

## ਪਿਛਲਾ ਪਾਠ

[Agentic RAG](../05-agentic-rag/README.md)

## ਅਗਲਾ ਪਾਠ

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**ਅਸੱਤੀਫਾ**:  
ਇਸ ਦਸਤਾਵੇਜ਼ ਦਾ ਅਨੁਵਾਦ AI ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦਕਿ ਅਸੀਂ ਸ਼ੁੱਧਤਾ ਲਈ ਪ੍ਰयਤਨਸ਼ੀਲ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਵਿੱਚ ਰੱਖੋ ਕਿ ਆਟੋਮੈਟਿਕ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਣਸੁੱਚਤੀਆਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼ ਇਸ ਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਅਧਿਕਾਰਿਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਜਰੂਰੀ ਜਾਣਕਾਰੀ ਲਈ, ਪ੍ਰੋਫੈਸ਼ਨਲ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਿਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਅਸੀਂ ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਹੋਣ ਵਾਲੀਆਂ ਕਿਸੇ ਵੀ ਗਲਤਫਹਿਮੀਆਂ ਜਾਂ ਭ੍ਰਮਾਂ ਲਈ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->