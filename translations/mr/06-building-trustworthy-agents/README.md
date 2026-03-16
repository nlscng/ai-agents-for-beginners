[![विश्वसनीय AI एजंट](../../../translated_images/mr/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(या धड्याचा व्हिडिओ पाहण्यासाठी वरील प्रतिमेवर क्लिक करा)_

# विश्वसनीय AI एजंट्स तयार करणे

## परिचय

हा धडा खालील गोष्टी समाविष्ट करेल:

- सुरक्षित आणि प्रभावी AI एजंट्स कसे तयार करावे आणि तैनात करावे
- AI एजंट्स विकसित करताना महत्त्वाच्या सुरक्षा बाबी
- AI एजंट्स विकसित करताना डेटा आणि वापरकर्त्यांच्या गोपनीयतेचे संरक्षण कसे राखावे

## शिकण्याची उद्दिष्टे

हा धडा पूर्ण केल्यावर, आपण हे करू शकाल:

- AI एजंट तयार करताना धोके ओळखणे आणि कमी करणे
- डेटा आणि प्रवेश योग्यरित्या व्यवस्थापित होण्यासाठी सुरक्षा उपाय अमलात आणणे
- डेटा गोपनीयता राखणारे आणि उत्तम वापरकर्ता अनुभव देणारे AI एजंट तयार करणे

## सुरक्षितता

सुरक्षित एजंटिक अनुप्रयोग तयार करण्याकडे प्रथम लक्ष देऊया. सुरक्षितता म्हणजे AI एजंट त्याप्रमाणेच काम करतो जे त्यासाठी डिझाइन केले आहे. एजंटिक अनुप्रयोगांचे निर्माते म्हणून, आम्ह्याकडे सुरक्षितता वाढवण्यासाठी पद्धती आणि साधने आहेत:

### सिस्टम संदेश फ्रेमवर्क तयार करणे

जर आपण कधीही लार्ज लँग्वेज मॉडेल्स (LLMs) वापरून AI अनुप्रयोग तयार केला असेल, तर आपल्याला मजबूत सिस्टम प्रॉम्प्ट किंवा सिस्टम संदेश डिझाइन करण्याचे महत्व माहित असेल. हे प्रॉम्प्ट LLM कसा वापरकर्त्याशी आणि डेटाशी संवाद करेल यासाठी मेटा नियम, सूचनांचे आणि मार्गदर्शक तत्त्वांचे स्थापन करतात.

AI एजंट्ससाठी, सिस्टम प्रॉम्प्ट आणखी महत्त्वाचा आहे कारण AI एजंट्सना आपण डिझाइन केलेले कार्य पूर्ण करण्यासाठी अत्यंत विशिष्ट सूचनांची आवश्यकता असेल.

स्केलेबल सिस्टम प्रॉम्प्ट तयार करण्यासाठी, आपण आपल्या अनुप्रयोगात एक किंवा अधिक एजंट तयार करण्यासाठी सिस्टम संदेश फ्रेमवर्क वापरू शकतो:

![सिस्टम संदेश फ्रेमवर्क तयार करणे](../../../translated_images/mr/system-message-framework.3a97368c92d11d68.webp)

#### पाऊल 1: एक मेटा सिस्टम संदेश तयार करा 

मेटा प्रॉम्प्टचा वापर LLM द्वारे आम्ही तयार करणार्‍या एजंटसाठी सिस्टम प्रॉम्प्ट जनरेट करण्यासाठी केला जाईल. आम्ही ते एक टेम्पलेट म्हणून डिझाइन करतो जेणेकरून आवश्यक असल्यास अनेक एजंट कार्यक्षमतेने तयार करता येतील.

येथे LLM ला देणार्‍या मेटा सिस्टम संदेशाचे एक उदाहरण आहे:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### पाऊल 2: एक मूलभूत प्रॉम्प्ट तयार करा

पुढील पाऊल म्हणजे AI एजंटचे वर्णन करण्यासाठी एक मूलभूत प्रॉम्प्ट तयार करणे. आपण एजंटची भूमिका, एजंट पूर्ण करणार्‍या कार्ये आणि एजंटची इतर जबाबदाऱ्या यांचा समावेश केला पाहिजे.

येथे एक उदाहरण आहे:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### पाऊल 3: मूलभूत सिस्टम संदेश LLM ला प्रदान करा

आता आपण मेटा सिस्टम संदेशाला सिस्टम संदेश म्हणून आणि आपला मूलभूत सिस्टम संदेश देऊन हा सिस्टम संदेश ऑप्टिमाइझ करू शकतो.

यामुळे आमच्या AI एजंट्सचे मार्गदर्शन करण्यासाठी अधिक चांगल्या प्रकारे डिझाइन केलेला एक सिस्टम संदेश तयार होईल:

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

#### पाऊल 4: पुनरावृत्ती करा आणि सुधारणा करा

या सिस्टम संदेश फ्रेमवर्कचे मूल्य म्हणजे अनेक एजंटसाठी सिस्टम संदेश तयार करणे सोपे करणे तसेच वेळेनुसार आपल्या सिस्टम संदेशात सुधारणा करणे. सामान्यतः प्रथम प्रयत्नात आपल्या संपूर्ण वापरप्रकरणासाठी कार्य करणारा सिस्टम संदेश मिळणे दुर्मिळ असते. मूलभूत सिस्टम संदेश बदलून आणि तो सिस्टममध्ये चालवून लहान बदल आणि सुधारणा करणे तुम्हाला निकालांची तुलना व मूल्यांकन करण्यास अनुमती देईल.

## धोक्यांचे समजून घेणे

विश्वसनीय AI एजंट तयार करण्यासाठी, आपल्या AI एजंटवर होणारे धोके व जोखमी समजून घेणे व त्यांना कमी करणे महत्त्वाचे आहे. चला AI एजंट्सवरील काही वेगवेगळ्या धोक्यांकडे व आपण त्यासाठी कसे उत्तम नियोजन व तयारी करू शकतो ते पाहूया.

![धोक्यांचे आकलन](../../../translated_images/mr/understanding-threats.89edeada8a97fc0f.webp)

### काम आणि सूचना

**वर्णन:** हल्लेखोर प्रॉम्प्टिंग किंवा इनपुट्समध्ये फेरफार करून AI एजंटच्या सूचनां किंवा उद्दिष्टांमध्ये बदल करण्याचा प्रयत्न करतात.

**कमीकरण**: AI एजंट प्रक्रियेत आणण्यापूर्वी संभाव्य धोकादायक प्रॉम्प्ट ओळखण्यासाठी प्रमाणीकरण तपासण्या आणि इनपुट फिल्टर्स चालवा. या हल्ल्यांना सामान्यतः एजंटशी वारंवार संवाद आवश्यक असतो, त्यामुळे संभाषणातील फेर्यांची संख्या मर्यादित करणे हा प्रकार प्रतिबंध करण्याचा आणखी एक मार्ग आहे.

### महत्त्वाच्या सिस्टम्सपर्यंत प्रवेश

**वर्णन**: जर AI एजंटला संवेदनशील डेटा साठवणाऱ्या सिस्टम्स आणि सेवांपर्यंत प्रवेश असेल, तर हल्लेखोर एजंट आणि या सेवांमधील संप्रेषणाला हल्ला करू शकतात. हे थेट हल्ले असू शकतात किंवा एजंटद्वारे या सिस्टम्सबद्दल माहिती मिळवण्याचे अप्रत्यक्ष प्रयत्न असू शकतात.

**कमीकरण**: या प्रकारच्या हल्ल्यांना प्रतिबंध करण्यासाठी AI एजंट्सना आवश्यकतेनुसारच प्रणालींमधील प्रवेश द्यावा. एजंट आणि सिस्टममधील संप्रेषण देखील सुरक्षित असावे. प्रमाणीकरण आणि प्रवेश नियंत्रण अंमलात आणणे हा या माहितीस संरक्षण करण्याचा आणखी एक मार्ग आहे.

### संसाधने आणि सेवा ओव्हरलोड होणे

**वर्णन:** AI एजंट्स कार्य पूर्ण करण्यासाठी विविध साधने आणि सेवा वापरू शकतात. हल्लेखोर हा क्षमता वापरून AI एजंटमार्फत उच्च प्रमाणात विनंत्या पाठवून या सेवांवर हल्ला करू शकतात, ज्यामुळे सिस्टम अयशस्वी होणे किंवा जास्त खर्च होऊ शकतो.

**कमीकरण:** AI एजंट एखाद्या सेवेवर किती विनंत्या करू शकतो याची संख्या मर्यादित करण्यासाठी धोरणे लागू करा. संभाषणातील फेर्यांची आणि आपल्या AI एजंटकडे येणाऱ्या विनंत्यांची संख्या मर्यादित करणे हा या प्रकारच्या हल्ल्यांना प्रतिबंध करण्याचा आणखी एक मार्ग आहे.

### ज्ञानाधार विषबाधा

**वर्णन:** हा प्रकारचा हल्ला थेट AI एजंटवर लक्ष केंद्रित करत नाही तर AI एजंट वापरणार्‍या ज्ञानाधार आणि इतर सेवांवर हल्ला करतो. यात डेटा किंवा माहिती दूषित करणे समाविष्ट असू शकते, ज्यामुळे वापरकर्त्यास प्रति पक्षपाती किंवा अनावश्यक प्रतिसाद मिळू शकतो.

**कमीकरण:** AI एजंट आपल्या वर्कफ्लोमध्ये वापरणार्‍या डेटाची नियमित तपासणी करा. या डेटावर प्रवेश सुरक्षित आहे आणि फक्त विश्वासार्ह व्यक्तींद्वारेच बदलला जातो याची खात्री करा जेणेकरून हा प्रकारचा हल्ला टाळता येईल.

### श्रृंखलाबद्ध चुका

**वर्णन:** AI एजंट्स कार्य पूर्ण करण्यासाठी विविध साधने आणि सेवांपर्यंत पोहोचतात. हल्लेखोरांमुळे झालेल्या चुका इतर प्रणालींच्या अयशस्वीतेकडे नेऊ शकतात ज्यामुळे हल्ला अधिक पसरलेला आणि निदान करण्यास अवघड होतो.

**कमीकरण**: याचे टाळण्याचे एक मार्ग म्हणजे AI एजंटला मर्यादित वातावरणात ऑपरेट करणे, उदा. Docker container मध्ये कार्ये पार पडावीत, ज्यामुळे थेट सिस्टम हल्ले टाळले जाऊ शकतात. काही सिस्टम त्रुटी सांगितल्यावर फॉलबॅक मेकॅनिझम आणि पुन्हा प्रयत्न करण्याचे लॉजिक तयार करणे ही मोठ्या प्रणाली अपयशांना प्रतिबंध करण्याची आणखी एक पद्धत आहे.

## मानवी-इन-द-लूप

विश्वसनीय AI एजंट प्रणाली तयार करण्याचा आणखी एक प्रभावी मार्ग म्हणजे मानवी-इन-द-लूप वापरणे. यामुळे एक असा प्रवाह तयार होतो जिथे वापरकर्ते रन दरम्यान एजंट्सना अभिप्राय देऊ शकतात. वापरकर्ते बहु-एजंट प्रणालीतील एजंटप्रमाणे वागतात आणि चालू प्रक्रियेची मंजुरी देणे किंवा थांबवणे यामुळे ते नियंत्रणात सहभाग घेतात.

![लूपमधील मानव](../../../translated_images/mr/human-in-the-loop.5f0068a678f62f4f.webp)

येथे AutoGen वापरून हा संकल्पना कशी अंमलात आणली जाते हे दाखवणारा एक कोड स्निपेट आहे:

```python

# एजंट तयार करा.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # कन्सोलमधून वापरकर्ता इनपुट घेण्यासाठी input() वापरा.

# वापरकर्ता "APPROVE" असे म्हणाल्यावर संभाषण संपवणारी समाप्तीची अट तयार करा.
termination = TextMentionTermination("APPROVE")

# टीम तयार करा.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# संभाषण चालवा आणि कन्सोलवर स्ट्रीम करा.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# स्क्रिप्टमध्ये चालवताना asyncio.run(...) वापरा.
await Console(stream)

```

## निष्कर्ष

विश्वसनीय AI एजंट तयार करण्यासाठी काळजीपूर्वक डिझाइन, मजबूत सुरक्षा उपाय आणि सतत पुनरावृत्ती आवश्यक असते. संरचित मेटा प्रॉम्प्टिंग सिस्टम्स अंमलात आणून, संभाव्य धोक्यांना समजून, आणि कमीकरण धोरणे लागू करून, विकसक सुरक्षित आणि प्रभावी AI एजंट तयार करू शकतात. तसेच, मानवी-इन-द-लूप पद्धत समाविष्ट केल्याने AI एजंट वापरकर्त्यांच्या गरजांशी सतत संरेखित राहतात आणि जोखमी कमी होतात. AI विकसित होत राहिल्यामुळे सुरक्षा, गोपनीयता आणि नैतिक बाबींवर अग्रगण्य दृष्टी ठेवणे AI-चालित प्रणालींमध्ये विश्वास आणि विश्वासार्हता वाढवण्यासाठी महत्त्वाचे ठरेल.

### विश्वसनीय AI एजंट्स तयार करण्याबद्दल आणखी प्रश्न आहेत का?

इतर शिक्षणार्थींसोबत भेटण्यासाठी, ऑफिस ऑवर्समध्ये सहभागी होण्यासाठी आणि तुमचे AI एजंट्स संदर्भातील प्रश्नांची उत्तरे मिळवण्यासाठी [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) मध्ये सामील व्हा.

## अतिरिक्त स्रोत

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">जबाबदार AI आढावा</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">जनरेटिव्ह AI मॉडेल्स आणि AI अनुप्रयोगांचे मूल्यांकन</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">सुरक्षा सिस्टम संदेश</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">जोखमीचे मूल्यांकन टेम्पलेट</a>

## मागील धडा

[Agentic RAG](../05-agentic-rag/README.md)

## पुढील धडा

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
अस्वीकरण:
हा दस्तऐवज AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून अनुवादित केला आहे. आम्ही अचूकतेसाठी प्रयत्न करतो, परंतु कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये चुका किंवा अचूकतेची कमतरता असू शकते. मूळ दस्तऐवज त्याच्या मूळ भाषेत अधिकृत स्रोत मानला जावा. महत्त्वाच्या माहितीसाठी व्यावसायिक मानवी अनुवाद करणे शिफारसीय आहे. या अनुवादाच्या वापरामुळे उद्भवणाऱ्या कोणत्याही गैरसमजुती किंवा चुकीच्या समजुतींबद्दल आम्ही जबाबदार नाही.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->