[![विश्वसनीय एआई एजेंट्स](../../../translated_images/hi/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(इस पाठ का वीडियो देखने के लिए ऊपर की छवि पर क्लिक करें)_

# विश्वसनीय एआई एजेंट्स का निर्माण

## परिचय

इस पाठ में निम्नलिखित कवर किया जाएगा:

- सुरक्षित और प्रभावी एआई एजेंट्स कैसे बनाएं और तैनात करें
- एआई एजेंट्स विकसित करते समय महत्वपूर्ण सुरक्षा विचार
- एआई एजेंट्स विकसित करते समय डेटा और उपयोगकर्ता की गोपनीयता बनाए रखना

## सीखने के उद्देश्य

इस पाठ को पूरा करने के बाद, आप जानेंगे कि कैसे:

- एआई एजेंट्स बनाते समय जोखिमों की पहचान करें और उन्हें कम करें।
- डेटा और पहुंच को उचित प्रकार से प्रबंधित करने के लिए सुरक्षा उपाय लागू करें।
- ऐसे एआई एजेंट्स बनाएं जो डेटा गोपनीयता बनाए रखें और उच्च गुणवत्ता वाला उपयोगकर्ता अनुभव प्रदान करें।

## सुरक्षा

सबसे पहले आइए सुरक्षित एजेंटिक एप्लिकेशन बनाने को देखें। सुरक्षा का मतलब है कि एआई एजेंट जैसा डिजाइन किया गया है वैसा ही प्रदर्शन करता है। एजेंटिक एप्लिकेशन बनाने वालों के रूप में, हमारे पास सुरक्षा अधिकतम करने के लिए तरीके और उपकरण हैं:

### सिस्टम मैसेज फ्रेमवर्क बनाना

अगर आपने कभी बड़े भाषा मॉडल्स (LLMs) का उपयोग करके एआई एप्लिकेशन बनाया हो, तो आप जानते हैं कि एक मजबूत सिस्टम प्रॉम्प्ट या सिस्टम मैसेज डिजाइन करना कितना महत्वपूर्ण है। ये प्रॉम्प्ट्स वह नियम, निर्देश, और दिशानिर्देश स्थापित करते हैं जिनसे LLM उपयोगकर्ता और डेटा के साथ इंटरैक्ट करेगा।

एआई एजेंट्स के लिए, सिस्टम प्रॉम्प्ट और भी अधिक महत्वपूर्ण होता है क्योंकि एआई एजेंट्स को उन कार्यों को पूरा करने के लिए अत्यंत विशिष्ट निर्देश चाहिए होते हैं जिन्हें हमने उनके लिए डिजाइन किया है।

स्केलेबल सिस्टम प्रॉम्प्ट बनाने के लिए, हम अपने एप्लिकेशन में एक या अधिक एजेंट्स के निर्माण के लिए सिस्टम मैसेज फ्रेमवर्क का उपयोग कर सकते हैं:

![Building a System Message Framework](../../../translated_images/hi/system-message-framework.3a97368c92d11d68.webp)

#### कदम 1: एक मेटा सिस्टम मैसेज बनाएँ

मेटा प्रॉम्प्ट का उपयोग LLM द्वारा उन एजेंट्स के लिए सिस्टम प्रॉम्प्ट उत्पन्न करने के लिए किया जाएगा जिन्हें हम बनाएंगे। इसे एक टेम्प्लेट के रूप में डिजाइन किया जाता है ताकि जरूरत पड़ने पर हम कुशलतापूर्वक कई एजेंट्स बना सकें।

यहाँ एक उदाहरण है मेटा सिस्टम मैसेज का जो हम LLM को देंगे:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### कदम 2: एक मूल प्रॉम्प्ट बनाएँ

अगला कदम है एआई एजेंट का वर्णन करने के लिए एक मूल प्रॉम्प्ट बनाना। इसमें एजेंट की भूमिका, एजेंट द्वारा पूरे किए जाने वाले कार्य, और एजेंट की अन्य जिम्मेदारियां शामिल होनी चाहिए।

यहाँ एक उदाहरण है:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### कदम 3: LLM को मूल सिस्टम मैसेज प्रदान करें

अब हम इस सिस्टम मैसेज को इस प्रकार अनुकूलित कर सकते हैं कि मेटा सिस्टम मैसेज को सिस्टम मैसेज के रूप में और हमारा मूल सिस्टम मैसेज प्रदान किया जाए।

यह एक बेहतर डिज़ाइन किया हुआ सिस्टम मैसेज तैयार करेगा जो हमारे एआई एजेंट्स को मार्गदर्शन देने के लिए उपयुक्त होगा:

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

#### कदम 4: पुनरावृत्ति करें और सुधार करें

इस सिस्टम मैसेज फ्रेमवर्क का मूल्य इस में है कि आप कई एजेंट्स के लिए सिस्टम मैसेज बनाना आसान बना सकते हैं साथ ही समय के साथ अपने सिस्टम मैसेज में सुधार भी कर सकते हैं। यह दुर्लभ है कि आपकी पहली बार बनाई गई सिस्टम मैसेज पूरी तरह से आपके उपयोग के मामले के लिए काम करे। छोटे-मोटे बदलाव और सुधार करना संभव होना जरूरी है ताकि आप परिणामों की तुलना कर सकें और उनका मूल्यांकन कर सकें।

## खतरों को समझना

विश्वसनीय एआई एजेंट बनाने के लिए, आपके एआई एजेंट के लिए जोखिम और खतरे को समझना और उन्हें कम करना महत्वपूर्ण है। आइए एआई एजेंट्स के कुछ अलग-अलग खतरों को देखें और आप उनके लिए बेहतर योजना और तैयारी कैसे कर सकते हैं।

![Understanding Threats](../../../translated_images/hi/understanding-threats.89edeada8a97fc0f.webp)

### कार्य और निर्देश

**विवरण:** हमलावर एआई एजेंट के निर्देशों या लक्ष्यों को प्रॉम्प्टिंग या इनपुट्स को बदलकर बदलने का प्रयास करते हैं।

**रोकथाम:** संभावित खतरनाक प्रॉम्प्ट्स का पता लगाने के लिए सत्यापन जांच और इनपुट फिल्टर लागू करें इससे पहले कि उन्हें एआई एजेंट द्वारा संसाधित किया जाए। क्योंकि ये हमले आमतौर पर एजेंट के साथ बार-बार इंटरैक्शन की मांग करते हैं, वार्ता में टर्न्स की संख्या को सीमित करना इन प्रकार के हमलों को रोकने का एक और तरीका है।

### महत्वपूर्ण सिस्टम तक पहुंच

**विवरण:** यदि किसी एआई एजेंट को ऐसे सिस्टम और सेवाओं तक पहुंच है जो संवेदनशील डेटा संग्रहीत करते हैं, तो हमलावर एजेंट और इन सेवाओं के बीच संचार को समझौता कर सकते हैं। ये सीधे हमले हो सकते हैं या एजेंट के माध्यम से इन सिस्टमों के बारे में जानकारी प्राप्त करने के अप्रत्यक्ष प्रयास हो सकते हैं।

**रोकथाम:** इन प्रकार के हमलों को रोकने के लिए एआई एजेंट्स को सिस्टम तक केवल आवश्यकता के आधार पर पहुंच होनी चाहिए। एजेंट और सिस्टम के बीच संचार भी सुरक्षित होना चाहिए। प्रमाणीकरण और पहुंच नियंत्रण लागू करना इस जानकारी की सुरक्षा का एक और तरीका है।

### संसाधन और सेवा ओवरलोडिंग

**विवरण:** एआई एजेंट्स विभिन्न टूल और सेवाओं का उपयोग कार्यों को पूरा करने के लिए कर सकते हैं। हमलावर इस क्षमता का उपयोग इन सेवाओं पर हमले के लिए कर सकते हैं, जैसे कि एआई एजेंट के माध्यम से उच्च मात्रा में अनुरोध भेजना, जो सिस्टम विफलताओं या उच्च लागत का कारण बन सकता है।

**रोकथाम:** किसी सेवा पर एआई एजेंट द्वारा भेजे जाने वाले अनुरोधों की संख्या को सीमित करने के लिए नीतियां लागू करें। वार्ता के टर्न्स और एआई एजेंट को भेजे जाने वाले अनुरोधों की संख्या सीमित करना इन प्रकार के हमलों को रोकने का एक और तरीका है।

### ज्ञान आधार का विषाक्तकरण

**विवरण:** इस प्रकार का हमला सीधे एआई एजेंट को लक्षित नहीं करता बल्कि ज्ञान आधार और अन्य सेवाओं को लक्षित करता है जिनका उपयोग एआई एजेंट कार्य पूरा करने के लिए करेगा। इसमें डेटा या जानकारी को दूषित करना शामिल हो सकता है, जिससे एजेंट पूर्वाग्रही या अनइच्छित प्रतिक्रियाएं उपयोगकर्ता को प्रदान कर सकता है।

**रोकथाम:** एजेंट की वर्कफ़्लो में उपयोग किए जाने वाले डेटा का नियमित सत्यापन करें। सुनिश्चित करें कि इस डेटा तक पहुंच सुरक्षित हो और केवल विश्वसनीय लोगों द्वारा ही इसमें परिवर्तन किया जाए ताकि इस प्रकार के हमलों से बचा जा सके।

### परस्पर त्रुटियां (कास्केडिंग एरर्स)

**विवरण:** एआई एजेंट विभिन्न टूल और सेवाओं का उपयोग कार्य पूरा करने के लिए करते हैं। हमलावरों द्वारा उत्पन्न त्रुटियां उन अन्य सिस्टम्स की विफलताओं का कारण बन सकती हैं, जिनसे एजेंट जुड़ा होता है, जिससे हमला व्यापक हो जाता है और समस्या का निवारण कठिन हो जाता है।

**रोकथाम:** इसे रोकने का एक तरीका यह है कि एआई एजेंट को सीमित वातावरण में ऑपरेट करें, जैसे कि टास्क को डॉकर कंटेनर में करना, ताकि सीधे सिस्टम हमलों से बचा जा सके। जब कुछ सिस्टम त्रुटि प्रतिक्रिया देते हैं तो फॉलबैक तंत्र और पुनः प्रयास तर्क बनाना बड़ी प्रणाली की विफलताओं को रोकने का एक और तरीका है।

## ह्यूमन-इन-द-लूप

विश्वसनीय एआई एजेंट सिस्टम बनाने का एक और प्रभावी तरीका है ह्यूमन-इन-द-लूप का उपयोग करना। इससे ऐसा फ्लो बनता है जहाँ उपयोगकर्ता प्रोसेस के दौरान एजेंट्स को प्रतिक्रिया दे सकते हैं। उपयोगकर्ता मूलतः बहु-एजेंट सिस्टम में एजेंट के रूप में काम करते हैं और चल रहे प्रोसेस की स्वीकृति या समाप्ति प्रदान करते हैं।

![Human in The Loop](../../../translated_images/hi/human-in-the-loop.5f0068a678f62f4f.webp)

यहाँ AutoGen का उपयोग करते हुए एक कोड स्निपेट है जो दिखाता है कि यह विचार कैसे लागू किया गया है:

```python

# एजेंट बनाएं।
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # कंसोल से उपयोगकर्ता इनपुट प्राप्त करने के लिए input() का उपयोग करें।

# समाप्ति शर्त बनाएं जो बातचीत को तब समाप्त कर देगी जब उपयोगकर्ता "APPROVE" कहे।
termination = TextMentionTermination("APPROVE")

# टीम बनाएं।
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# बातचीत चलाएं और कंसोल पर स्ट्रीम करें।
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# स्क्रिप्ट चलाते समय asyncio.run(...) का उपयोग करें।
await Console(stream)

```

## निष्कर्ष

विश्वसनीय एआई एजेंट बनाने के लिए सावधानीपूर्वक डिजाइन, मजबूत सुरक्षा उपाय, और निरंतर पुनरावृत्ति आवश्यक है। संरचित मेटा प्रॉम्प्टिंग सिस्टम लागू करके, संभावित खतरों को समझकर, और रोकथाम रणनीतियों को अपनाकर, डेवलपर्स ऐसे एआई एजेंट्स बना सकते हैं जो सुरक्षित और प्रभावी दोनों हों। इसके अलावा, ह्यूमन-इन-द-लूप पद्धति शामिल करने से यह सुनिश्चित होता है कि एआई एजेंट उपयोगकर्ता की आवश्यकताओं के अनुरूप बने रहें और जोखिम न्यूनतम हो। जैसे-जैसे एआई विकसित होता रहेगा, सुरक्षा, गोपनीयता, और नैतिक विचारों पर सक्रिय दृष्टिकोण बनाए रखना एआई-संचालित सिस्टम में विश्वास और विश्वसनीयता बढ़ाने की कुंजी होगी।

### विश्वसनीय एआई एजेंट्स के निर्माण के बारे में और प्रश्न हैं?

अन्य शिक्षार्थियों से मिलने, ऑफिस ऑवर्स में भाग लेने, और अपने एआई एजेंट्स के प्रश्नों के उत्तर प्राप्त करने के लिए [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) में शामिल हों।

## अतिरिक्त संसाधन

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">जिम्मेदार एआई अवलोकन</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">सृजनात्मक एआई मॉडल और एआई एप्लिकेशन का मूल्यांकन</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">सुरक्षा सिस्टम संदेश</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">जोखिम आकलन टेम्पलेट</a>

## पिछला पाठ

[Agentic RAG](../05-agentic-rag/README.md)

## अगला पाठ

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**अस्वीकरण**:
यह दस्तावेज़ एआई अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनूदित किया गया है। हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवाद में त्रुटियाँ या अशुद्धियाँ हो सकती हैं। मूल दस्तावेज़ अपनी मूल भाषा में प्रामाणिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सलाह दी जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम उत्तरदायी नहीं हैं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->