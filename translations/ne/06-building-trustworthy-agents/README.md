[![विश्वसनीय AI एजेन्टहरू](../../../translated_images/ne/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(यस पठनको भिडियो हेर्न माथिको छवि क्लिक गर्नुहोस्)_

# विश्वसनीय AI एजेन्टहरू निर्माण गर्दै

## परिचय

यस पाठले समेट्नेछ:

- सुरक्षित र प्रभावकारी AI एजेन्टहरू कसरी निर्माण र तैनाथ गर्ने
- AI एजेन्टहरू विकास गर्दा महत्वपूर्ण सुरक्षा विचारहरू।
- AI एजेन्टहरू विकास गर्दा डेटा र प्रयोगकर्ता गोपनीयता कसरी कायम राख्ने।

## सिकाइ लक्ष्यहरू

यस पाठ पूरा गरेपछि, तपाईं जान्नेछ:

- AI एजेन्टहरू सिर्जना गर्दा जोखिमहरू कसरी पहिचान र कम गर्ने।
- डेटा र पहुँचलाई उचित रूपमा व्यवस्थापन गर्न सुरक्षा उपायहरू कसरी कार्यान्वयन गर्ने।
- डेटा गोपनीयता कायम राख्ने र गुणस्तरीय प्रयोगकर्ता अनुभव प्रदान गर्ने AI एजेन्टहरू कसरी बनाउने।

## सुरक्षा

पहिला हामी सुरक्षित एजेन्टिक अनुप्रयोगहरू निर्माण गर्ने कुरा हेरौं। सुरक्षा भनेको AI एजेन्टले डिजाइन अनुसार काम गर्नु हो। एजेन्टिक अनुप्रयोगहरूको निर्माताहरूको रूपमा, हामीसँग सुरक्षा अधिकतम गर्नका लागि विधिहरू र उपकरणहरू छन्:

### सिस्टम सन्देश फ्रेमवर्क बनाउँदा

यदि तपाईंले कहिले पनि ठूलो भाषा मोडेलहरू (LLMs) प्रयोग गरेर AI अनुप्रयोग बनाउनु भएको छ भने, तपाईंलाई बलियो सिस्टम प्राम्प्ट वा सिस्टम सन्देश डिजाइन गर्ने महत्त्व थाहा छ। यी प्राम्प्टहरूले LLM कसरी प्रयोगकर्ता र डेटा सँग अन्तरक्रिया गर्ने भनेर निर्धारित गर्ने नियम, निर्देशनहरू, र दिशानिर्देशहरू स्थापना गर्छन्।

AI एजेन्टहरूको लागि, सिस्टम प्राम्प्ट अझ पनि महत्वपूर्ण हुन्छ किनकि AI एजेन्टहरूले हाम्रा डिजाइन गरिएको कामहरू पूरा गर्न अत्यन्त निर्दिष्ट निर्देशनहरू चाहिन्छ।

स्केलेबल सिस्टम प्राम्प्टहरू बनाउनको लागि, हामी हाम्रो अनुप्रयोगमा एक वा बढी एजेन्टहरू निर्माण गर्न सिस्टम सन्देश फ्रेमवर्क प्रयोग गर्न सक्छौं:

![Building a System Message Framework](../../../translated_images/ne/system-message-framework.3a97368c92d11d68.webp)

#### चरण 1: मेटा सिस्टम सन्देश सिर्जना गर्नुहोस्

मेटा प्राम्प्ट LLM द्वारा प्रयोग गरिनेछ जसले हामीले सिर्जना गर्ने एजेन्टहरूको लागि सिस्टम प्राम्प्टहरू तयार पार्नेछ। हामी यसलाई टेम्प्लेटको रूपमा डिजाइन गर्छौं ताकि आवश्यक परे धेरै एजेन्टहरू सजिलै बनाइने होस्।

LLM लाई दिने मेटा सिस्टम सन्देशको उदाहरण यहाँ छ:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### चरण 2: आधारभूत प्राम्प्ट सिर्जना गर्नुहोस्

अर्को चरण AI एजेन्ट वर्णन गर्न आधारभूत प्राम्प्ट सिर्जना गर्ने हो। तपाईंले एजेन्टको भूमिका, एजेन्टले गर्ने कामहरू, र अन्य जिम्मेवारीहरू समावेश गर्नुपर्छ।

यहाँ एउटा उदाहरण छ:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### चरण 3: मूल सिस्टम सन्देश LLM लाई दिनुहोस्

अब हामी यस सिस्टम सन्देशलाई सुधार गर्न सक्छौं, मेटा सिस्टम सन्देशलाई सिस्टम सन्देशको रूपमा र हाम्रो आधारभूत सिस्टम सन्देशलाई प्रदान गरेर।

यसले AI एजेन्टहरूलाई मार्गदर्शन गर्ने राम्रो डिजाइन गरिएको सिस्टम सन्देश उत्पन्न गर्नेछ:

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

#### चरण 4: परिमार्जन र सुधार गर्नुहोस्

यस सिस्टम सन्देश फ्रेमवर्कको मूल्य भनेको धेरै एजेन्टहरूबाट सिस्टम सन्देश बनाउन सजिलो हुने र समयसँगै तपाईंका सिस्टम सन्देशहरू सुधार गर्ने क्षमता हो। तपाईंको पूरे प्रयोग केसका लागि पहिलो पटक काम गर्ने सिस्टम सन्देश हुनु दुर्लभ हुन्छ। आधारभूत सिस्टम सन्देश परिवर्तन गरी र प्रणाली मार्फत चलाएर साना सुधार र परिवर्तनहरू गर्नु, परिणामहरू तुलना र मूल्यांकन गर्न मद्दत गर्दछ।

## खतरा बुझ्नुपर्छ

विश्वसनीय AI एजेन्ट बनाउनका लागि, तपाईंको AI एजेन्टलाई हुने जोखिम र खतरा बुझ्नु र तिनलाई कम गर्नु महत्वपूर्ण छ। यहाँ AI एजेन्टहरूलाई हुने केही विभिन्न खतराहरू र तपाईंले तीका लागि कसरी राम्रो योजना र तयारी गर्न सक्नुहुन्छ भनी हेरौं।

![Understanding Threats](../../../translated_images/ne/understanding-threats.89edeada8a97fc0f.webp)

### कार्य र निर्देशन

**वर्णन:** आक्रमणकारीहरूले प्राम्प्टिङ वा इनपुटहरू हेरफेर गरेर AI एजेन्टका निर्देशन वा लक्ष्यहरू परिवर्तन गर्ने प्रयास गर्दछन्।

**कमजोरी हटाउने उपाय:** AI एजेन्टमार्फत प्रशोधन हुनु अघि सम्भावित खतरनाक प्राम्प्टहरूको पहिचान गर्न मान्यकरण जाँच र इनपुट फिल्टरहरू कार्यान्वयन गर्नुहोस्। यी आक्रमणहरू सामान्यतया एजेन्टसँग बारम्बार अन्तरक्रिया माग्ने भएकाले कुराकानीका पालो संख्यामा सीमा लगाउने अर्को उपाय हो।

### महत्वपूर्ण प्रणालीहरूमा पहुँच

**वर्णन:** यदि AI एजेन्टसँग संवेदनशील डेटा राख्ने प्रणाली र सेवाहरूमा पहुँच छ भने, आक्रमणकारीहरूले एजेन्ट र यी सेवाहरू बीचको सञ्चारमा समझौता गर्न सक्छन्। यी सिधा आक्रमण वा एजेन्टमार्फत ती प्रणालीहरूको बारेमा जानकारी हासिल गर्ने अप्रत्यक्ष प्रयास हुन सक्छ।

**कमजोरी हटाउने उपाय:** AI एजेन्टहरूलाई आवश्यकता अनुसार मात्र प्रणालीहरूमा पहुँच दिनुहोस्। एजेन्ट र प्रणालीबीचको सञ्चार पनि सुरक्षित हुनुपर्छ। प्रमाणीकरण र पहुँच नियन्त्रण कार्यान्वयन गर्नु अर्को तरिका हो।

### स्रोत र सेवा अधिभार

**वर्णन:** AI एजेन्टहरूले कार्य पूरा गर्न विभिन्न उपकरण र सेवाहरू पहुँच गर्न सक्छन्। आक्रमणकारीहरूले यो क्षमता प्रयोग गरी ती सेवाहरूमा धेरै अनुरोधहरू पठाएर प्रणाली विफलता वा उच्च लागत निम्त्याउन सक्छ।

**कमजोरी हटाउने उपाय:** AI एजेन्टले सेवा प्रदानकर्तालाई गर्ने अनुरोधहरूको संख्या सीमित गर्न नीतिहरू लागू गर्नुहोस्। संवादका पालो र अनुरोधहरू सीमित गर्नु अर्को उपाय हो।

### ज्ञान आधार विषाक्तता

**वर्णन:** यो आक्रमणले सिधै AI एजेन्टलाई लक्षित गर्दैन, बरु AI एजेन्टले प्रयोग गर्ने ज्ञान आधार र अन्य सेवाहरूमा लक्षित हुन्छ। यसमा एजेन्टले कार्य पूरा गर्न प्रयोग गर्ने डेटा वा जानकारीलाई भ्रष्ट पार्नु पर्न सक्छ, जसले पूर्वाग्रहपूर्ण वा अनइच्छित प्रतिक्रिया निम्त्याउँछ।

**कमजोरी हटाउने उपाय:** AI एजेन्टले प्रयोग गर्ने डेटा नियमित रूपमा जाँच गर्नुहोस्। यस डेटामा पहुँच सुरक्षित राख्नुहोस् र यो केवल विश्वसनीय व्यक्तिहरू द्वारा मात्र परिवर्तन गरियोस् ताकि यस्तो आक्रमण रोक्न सकियोस्।

### श्रेणीगत त्रुटिहरू

**वर्णन:** AI एजेन्टहरूले विभिन्न उपकरण र सेवाहरू पहुँच गर्छन्। आक्रमणकारीहरूले सिर्जना गरेको त्रुटिहरूले अन्य प्रणालीहरूमा पनि विफलता निम्त्याउन सक्छ, जसले आक्रमणलाई फैलाउछ र समाधान गर्न गाह्रो बनाउँछ।

**कमजोरी हटाउने उपाय:** AI एजेन्टले सीमित वातावरण (जस्तै Docker कन्टेनरमा कार्य गर्नु) मा कार्य गरेर प्रत्यक्ष प्रणाली आक्रमणबाट बच्न सकिन्छ। निश्चित प्रणालीले त्रुटि प्रतिक्रिया दिएमा फालब्याक प्रबन्ध र पुनः प्रयास गर्ने तर्क सिर्जना गर्नु राम्रो उपाय हो।

## मानव-इन-द-लूप

विश्वसनीय AI एजेन्ट प्रणालीहरू निर्माण गर्ने अर्को प्रभावकारी तरिका मानव-इन-द-लूप प्रयोग गर्नु हो। यसले यस्तो प्रवाह सिर्जना गर्छ जहाँ प्रयोगकर्ताहरूले चलिरहेको प्रक्रियामा एजेन्टहरूलाई प्रतिक्रिया दिन सक्दछन्। प्रयोगकर्ताहरू बहु-एजेन्ट प्रणालीमा एजेन्टको रूपमा कार्य गर्छन् र प्रक्रिया स्वीकृत वा समाप्त गर्नसक्छन्।

![Human in The Loop](../../../translated_images/ne/human-in-the-loop.5f0068a678f62f4f.webp)

यो अवधारणालाई कसरी लागू गरिएको छ भन्ने देखाउन AutoGen प्रयोग गर्ने कोड अंश यहाँ छ:

```python

# एजेन्टहरू सिर्जना गर्नुहोस्।
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # कन्सोलबाट प्रयोगकर्ताको इनपुट लिन input() प्रयोग गर्नुहोस्।

# टर्मिनेसन सर्त सिर्जना गर्नुहोस् जसले प्रयोगकर्ताले "APPROVE" भन्छ भने संवाद समाप्त गर्छ।
termination = TextMentionTermination("APPROVE")

# टोली सिर्जना गर्नुहोस्।
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# संवाद चलाउनुहोस् र कन्सोलमा स्ट्रिम गर्नुहोस्।
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# स्क्रिप्टमा चलाउँदा asyncio.run(...) प्रयोग गर्नुहोस्।
await Console(stream)

```

## निष्कर्ष

विश्वसनीय AI एजेन्टहरू निर्माण गर्न सावधानीपूर्वक डिजाइन, बलियो सुरक्षा उपायहरू, र निरन्तर सुधार आवश्यक छ। संरचित मेटा प्राम्प्टिङ प्रणालीहरू कार्यान्वयन गरी, सम्भावित खतरा बुझेर, र कम गर्ने रणनीतिहरू अपनाएर डेवलपर्सले सुरक्षित र प्रभावकारी AI एजेन्टहरू बनाउन सक्छन्। थप रूपमा, मानव-इन-द-लूप दृष्टिकोण समावेश गर्दा AI एजेन्टहरू प्रयोगकर्ताको आवश्यकतासँग मेल खाने र जोखिमहरूमाथि न्यूनतम बनाइन्छ। AI निरन्तर विकास हुँदै गएकोले सुरक्षा, गोपनीयता, र नैतिक विचारहरूमा सक्रिय दृष्टिकोण कायम राख्नु AI-प्रेरित प्रणालीमा विश्वास र भरोसा कायम राख्न महत्वपूर्ण हुनेछ।

### विश्वसनीय AI एजेन्टहरू बनाउने विषयमा थप प्रश्नहरू छन्?

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) मा सहभागी हुनुहोस्, अन्य सिक्नेमहरूलाई भेट्न, कार्यालय समयहरूमा सहभागी हुन र तपाईंका AI एजेन्ट सम्बन्धी प्रश्नहरूको उत्तर पाउन।

## अतिरिक्त स्रोतहरू

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">जिम्मेवार AI अवलोकन</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">सर्जनात्मक AI मोडेलहरू र AI अनुप्रयोगहरूको मूल्यांकन</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">सुरक्षा प्रणाली सन्देशहरू</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">जोखिम मूल्यांकन टेम्प्लेट</a>

## अघिल्लो पाठ

[Agentic RAG](../05-agentic-rag/README.md)

## अर्को पाठ

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**अस्वीकरण**:
यस दस्तावेजलाई AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) प्रयोग गरी अनुवाद गरिएको छ। हामी शुद्धतामा प्रयासरत छौं तापनि, कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादमा त्रुटिहरू वा अशुद्धिहरू हुनसक्छन्। मूल भाषा मा रहेको दस्तावेजलाई अधिकारिक स्रोतको रूपमा मानिनु पर्छ। महत्वपूर्ण जानकारीका लागि पेशेवर मानव अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न कुनै प्रकारको गलतफहमी वा गलत व्याख्याका लागि हामी जिम्मेवार छैनौं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->