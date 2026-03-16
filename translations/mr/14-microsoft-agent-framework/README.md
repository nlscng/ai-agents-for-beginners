# Microsoft Agent Framework चे अन्वेषण

![एजंट फ्रेमवर्क](../../../translated_images/mr/lesson-14-thumbnail.90df0065b9d234ee.webp)

### परिचय

This lesson will cover:

- Microsoft Agent Framework समजून घेणे: प्रमुख वैशिष्ट्ये आणि मूल्य  
- Microsoft Agent Framework च्या मुख्य संकल्पनांचा शोध
- MAF चे Semantic Kernel आणि AutoGen शी तुलना: स्थलांतर मार्गदर्शक

## शिक्षण उद्दिष्टे

हा धडा पूर्ण केल्यानंतर, आपण असे काय करायला शिकाल:

- Microsoft Agent Framework वापरून उत्पादनासाठी तयार AI एजंट कसे तयार करायचे
- Microsoft Agent Framework ची मुख्य वैशिष्ट्ये आपल्या एजंटिक वापराच्या प्रकरणांवर कशी लागू करायची
- विद्यमान एजंटिक फ्रेमवर्क्स आणि साधने कसे स्थलांतरित व एकत्रीकृत करायची  

## कोड नमुने 

Code samples for [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) can be found in this repository under `xx-python-agent-framework` and `xx-dotnet-agent-framework` files.

## Microsoft Agent Framework समजून घेणे

![फ्रेमवर्क परिचय](../../../translated_images/mr/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) हे Semantic Kernel आणि AutoGen मधील अनुभव व शिकण्यावर आधारलेले आहे. हे उत्पादन आणि संशोधन वातावरणात आढळणाऱ्या विविध एजंटिक वापरप्रकरणांची लवचिकता हाताळण्यासाठी सुविधा देते, ज्यात समाविष्ट आहे:

- **अनुक्रमिक एजंट ऑर्केस्ट्रेशन** अशा परिस्थितींमध्ये जेथे टप्प्याटप्प्याने वर्कफ्लोची आवश्यकता असते.
- **समानकालिक ऑर्केस्ट्रेशन** अशा परिस्थितींमध्ये जेथे एजंट्स एकाच वेळी कार्य पूर्ण करतात.
- **गट चॅट ऑर्केस्ट्रेशन** अशा परिस्थितींमध्ये जिथे एजंट्स एकाच कार्यावर सहकार्य करतात.
- **हँडऑफ ऑर्केस्ट्रेशन** अशा परिस्थितींमध्ये जिथे उपकार्ये पूर्ण होत असल्यावर एजंट्स एकमेकांना काम हस्तांतरित करतात.
- **मॅग्नेटिक ऑर्केस्ट्रेशन** अशा परिस्थितींमध्ये जिथे व्यवस्थापक एजंट कार्ययादी तयार करतो आणि बदलतो आणि उपएजंट्सचे समन्वय हाताळतो जेणेकरून कार्य पूर्ण होईल.

उत्पादनात AI एजंट्स वितरीत करण्यासाठी, MAF मध्ये खालील सुविधाही समाविष्ट आहेत:

- **निरिक्षणक्षमता (Observability)** OpenTelemetry चा वापर करून जिथे AI एजंटच्या प्रत्येक क्रियेत टुल कॉल, ऑर्केस्ट्रेशन पावले, तर्कप्रवाह आणि Microsoft Foundry डॅशबोर्डद्वारे कामगिरीचे निरीक्षण समाविष्ट आहे.
- **सुरक्षा** Microsoft Foundry वर नॅटिव्हली एजंट होस्ट करून, ज्यात भूमिका-आधारित प्रवेश, खाजगी डेटा हाताळणी आणि अंगभूत सामग्री सुरक्षा सारखी सुरक्षा नियंत्रणे आहेत.
- **टिकाऊपणा (Durability)** कारण एजंट थ्रेड आणि वर्कफ्लो मधील प्रक्रिया थांबवता, पुन्हा सुरू करता आणि त्रुटींपासून पुनर्प्राप्त करू शकतात, ज्यामुळे दीर्घकालीन प्रक्रियेची अनुमती मिळते.
- **नियंत्रण (Control)** मानव-इन-द-लूप वर्कफ्लोला समर्थन, जिथे कार्यांना मानवी मंजुरी आवश्यक म्हणून चिन्हित केले जाते.

Microsoft Agent Framework हा इंटरऑपरेबल असण्यावरही लक्ष केंद्रित करतो:

- **क्लाऊड-विशेष नाही** - एजंट कंटेनरमध्ये, ऑन-प्रिमाइसेस आणि विविध क्लाऊडवर चालू शकतात.
- **प्रदाता-विशेष नाही** - एजंट आपल्या पसंतीच्या SDK द्वारे तयार केले जाऊ शकतात ज्यात Azure OpenAI आणि OpenAI समाविष्ट आहे
- **ओपन स्टँडर्ड्सचे एकत्रीकरण** - एजंट-टू-एजंट (A2A) आणि Model Context Protocol (MCP) सारख्या प्रोटोकॉलचा वापर करून इतर एजंट्स आणि टूल्स शोधणे आणि वापरणे शक्य आहे.
- **प्लगइन्स आणि कनेक्टर्स** - Microsoft Fabric, SharePoint, Pinecone आणि Qdrant सारख्या डेटा आणि मेमरी सेवांशी कनेक्शन केले जाऊ शकतात.

आता पाहुया की हे वैशिष्ट्ये Microsoft Agent Framework च्या काही मूलभूत संकल्पनांवर कसे लागू होतात.

## Microsoft Agent Framework ची मुख्य संकल्पना

### एजंट्स

![एजंट घटक](../../../translated_images/mr/agent-components.410a06daf87b4fef.webp)

**एजंट तयार करणे**

एजंटची निर्मिती ही inference service (LLM Provider), AI एजंटने अनुसरावयाच्या सूचना आणि नियुक्त केलेले `name` हे परिभाषित करून केली जाते:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

वरील उदाहरण `Azure OpenAI` वापरत आहे परंतु एजंट विविध सेवांचा वापर करून तयार केले जाऊ शकतात ज्यात `Microsoft Foundry Agent Service` समाविष्ट आहे:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

किंवा A2A प्रोटोकॉल वापरून रिमोट एजंट्स:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**एजंट चालवणे**

एजंट्स `.run` किंवा `.run_stream` पद्धती वापरून चालवले जातात, सिरीअल उत्तरांसाठी किंवा स्ट्रीमिंग प्रतिसादांसाठी अनुक्रमे.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

प्रत्येक एजंट चालवणीयाला `max_tokens`, एजंट कॉल करू शकेल असे `tools`, आणि एजन्टसाठी वापरला जाणारा `model` सारखे पॅरामीटर्स सानुकूल करण्याचे पर्याय असू शकतात.

हे उपयुक्त आहे जिथे विशिष्ट मॉडेल्स किंवा टूल्स वापरुन वापरकर्त्याचे कार्य पूर्ण करणे आवश्यक असते.

**टूल्स**

टूल्स एजंट परिभाषित करताना दोन्ही ठिकाणी परिभाषित केले जाऊ शकतात:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# जेव्हा थेट ChatAgent तयार करताना

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

आणि एजंट चालवताना देखील:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # हे साधन फक्त या धावेसाठी प्रदान केले गेले आहे )
```

**एजंट थ्रेड्स**

एजंट थ्रेड्स मल्टी-टर्न संभाषणे हाताळण्यासाठी वापरल्या जातात. थ्रेड्स तयार करण्याचे दोन मार्ग आहेत:

- `get_new_thread()` वापरून जे थ्रेड कालांतराने जतन केले जाऊ शकते
- एजंट चालवताना स्वयंचलितरित्या थ्रेड तयार करणे आणि तो थ्रेड केवळ सध्याच्या रनदरम्यान टिकवणे.

थ्रेड तयार करण्यासाठी कोड असे दिसतो:

```python
# नवीन थ्रेड तयार करा.
thread = agent.get_new_thread() # एजंटला त्या थ्रेडसह चालवा.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

त्यानंतर आपण नंतर वापरण्यासाठी थ्रेड सिरीयलाइझ करू शकता:

```python
# नवीन थ्रेड तयार करा.
thread = agent.get_new_thread() 

# एजंटला थ्रेडसह चालवा.

response = await agent.run("Hello, how are you?", thread=thread) 

# साठवणीसाठी थ्रेडचे सीरिअलाइझ करा.

serialized_thread = await thread.serialize() 

# साठवणीतून लोड केल्यानंतर थ्रेडची स्थिती डीसीरिअलाइझ करा.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**एजंट मिडलवेयर**

एजंट्स टूल्स आणि LLMs सह परस्परसंवाद साधून वापरकर्त्याचे कार्य पूर्ण करतात. काही परिस्थितींमध्ये, या संवादांदरम्यान एखादी क्रिया चालवायची किंवा ट्रॅक करायची असते. एजंट मिडलवेयर आम्हाला हे करण्यास सक्षम करते:

*Function Middleware*

हे मिडलवेयर एजंट आणि ज्याला तो कॉल करणार त्या फंक्शन/टुल दरम्यान क्रिया चालवण्याची परवानगी देते. उदाहरणार्थ, फंक्शन कॉल वर लॉगिंग करायची गरज असेल तेव्हा हे वापरले जाऊ शकते.

खालील कोडमध्ये `next` हे परिभाषित करते की पुढचे मिडलवेयर कॉल व्हावे की प्रत्यक्ष फंक्शन कॉल व्हावे.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # पूर्व-प्रक्रिया: फंक्शनच्या अंमलबजावणीपूर्वी लॉग
    print(f"[Function] Calling {context.function.name}")

    # पुढील मिडलवेअर किंवा फंक्शनच्या अंमलबजावणीकडे पुढे जा
    await next(context)

    # पोस्ट-प्रक्रिया: फंक्शनच्या अंमलबजावणी नंतर लॉग
    print(f"[Function] {context.function.name} completed")
```

*Chat Middleware*

हे मिडलवेयर एजंट आणि LLM मधील विनंत्यांदरम्यान क्रिया चालवण्याची किंवा लॉग करण्याची परवानगी देते.

यामध्ये AI सेवेला पाठवल्या जाणाऱ्या `messages` सारखी महत्त्वाची माहिती असते.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # पूर्व-प्रक्रिया: एआय कॉल करण्यापूर्वी लॉग करा
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # पुढील मिडलवेअर किंवा एआय सेवेकडे पुढे जा
    await next(context)

    # पश्च-प्रक्रिया: एआय प्रतिसादानंतर लॉग करा
    print("[Chat] AI response received")

```

**एजंट मेमरी**

`Agentic Memory` धड्यात चर्चा केलेल्याप्रमाणे, मेमरी हे विविध संदर्भामध्ये एजंटला कार्य करण्यास सक्षम बनवण्याचा एक महत्त्वाचा घटक आहे. MAF मध्ये अनेक प्रकारच्या मेमरीचे समर्थन आहे:

*In-Memory Storage*

ही मेमरी अ‍ॅप्लिकेशन रनटाईम दरम्यान थ्रेड्समध्ये साठवले जाते.

```python
# नवीन थ्रेड तयार करा.
thread = agent.get_new_thread() # एजंट त्या थ्रेडसह चालवा.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Persistent Messages*

ही मेमरी वेगवेगळ्या सत्रांमध्ये संभाषण इतिहास साठवण्यासाठी वापरली जाते. हे `chat_message_store_factory` वापरून परिभाषित केले जाते :

```python
from agent_framework import ChatMessageStore

# सानुकूल संदेश संच तयार करा
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamic Memory*

ही मेमरी एजंट्स चालवण्याआधी संदर्भात जोडली जाते. या मेमरी बाह्य सेवांमध्ये जसे mem0 मध्ये साठवता येऊ शकतात:

```python
from agent_framework.mem0 import Mem0Provider

# उन्नत स्मृती क्षमतांसाठी Mem0 वापरणे
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**एजंट निरीक्षणक्षमता**

निरिक्षणक्षमता विश्वासार्ह आणि राखण्यायोग्य एजंटिक सिस्टम्स तयार करण्यासाठी महत्त्वाची आहे. MAF OpenTelemetry सह एकत्रित होते जेणेकरून ट्रेसिंग आणि मीटर्ससाठी चांगले निरिक्षण मिळू शकेल.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # काहीतरी करा
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### वर्कफ्लो

MAF पूर्वनिर्धारित पावले असलेले वर्कफ्लोज ऑफर करते जे एखादे कार्य पूर्ण करण्यासाठी असतात आणि त्यात AI एजंट हे त्या पावलांमधील घटक असतात.

वर्कफ्लोज नियंत्रण प्रवाह सुधारण्यासाठी वेगवेगळ्या घटकांनी बनलेले असतात. वर्कफ्लो मल्टी-एजंट ऑर्केस्ट्रेशन आणि वर्कफ्लो स्टेट जतन करण्यासाठी **चेकपॉइंटिंग** सक्षम करतात.

वर्कफ्लोचे मुख्य घटक आहेत:

**एक्झिक्युटर्स**

एक्झिक्युटर्स इनपुट संदेश प्राप्त करतात, त्यांचे नेमलेले कार्य पार पाडतात, आणि नंतर आउटपुट संदेश तयार करतात. हे वर्कफ्लोला मोठे कार्य पूर्ण करण्याच्या दिशेने पुढे नेतात. एक्झिक्युटर्स AI एजंट असू शकतात किंवा सानुकूल लॉजिक असू शकते.

**एज**

एज वर्कफ्लोमध्ये संदेशांच्या प्रवाहाचे परिभाषित करण्यासाठी वापरले जातात. हे प्रकारचे असू शकतात:

*Direct Edges* - एक्झिक्युटर्स दरम्यान साधे एक ते एक कनेक्शन्स:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Conditional Edges* - काही अटी पूर्ण झाल्यावर सक्रिय होतात. उदाहरणार्थ, जेव्हा हॉटेलाच्या खोल्या उपलब्ध नसतील तर एक्झिक्युटर इतर पर्याय सुचवू शकतो.

*Switch-case Edges* - परिभाषित अटींनुसार संदेशांना वेगवेगळ्या एक्झिक्युटर्सकडे मार्गदर्शित करतात. उदाहरणार्थ, जर प्रवाशाला प्राधान्य प्रवेश असेल तर त्यांची कामे दुसर्‍या वर्कफ्लोद्वारे हाताळली जाऊ शकतात.

*Fan-out Edges* - एकच संदेश अनेक लक्ष्यांकडे पाठवा.

*Fan-in Edges* - विविध एक्झिक्युटर्सकडून अनेक संदेश एकत्र करून एका लक्ष्यांकडे पाठवा.

**इवेंट्स**

वर्कफ्लोमध्ये चांगली निरीक्षणक्षमता प्रदान करण्यासाठी, MAF अंमलबजावणीसाठी अंगभूत इवेंट्स ऑफर करते ज्यात समाविष्ट आहेत:

- `WorkflowStartedEvent`  - वर्कफ्लोची अंमलबजावणी सुरू होते
- `WorkflowOutputEvent` - वर्कफ्लो आउटपुट तयार करते
- `WorkflowErrorEvent` - वर्कफ्लो त्रुटीला सामोरे जाते
- `ExecutorInvokeEvent`  - एक्झिक्युटर प्रक्रिया सुरू करतो
- `ExecutorCompleteEvent`  -  एक्झिक्युटर प्रक्रिया पूर्ण करतो
- `RequestInfoEvent` - विनंती जारी केली जाते

## इतर फ्रेमवर्कमधून स्थलांतर (Semantic Kernel आणि AutoGen)

### MAF आणि Semantic Kernel मधील फरक

**सरल केलेले एजंट निर्मिती**

Semantic Kernel प्रत्येक एजंटसाठी Kernel instance तयार करण्यावर अवलंबून असतो. MAF मध्ये मुख्य प्रदात्यांसाठी विस्तारांचा वापर करून एक साधा दृष्टिकोन आहे.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**एजंट थ्रेड तयार करणे**

Semantic Kernel मध्ये थ्रेड्स हाताने तयार करावे लागतात. MAF मध्ये, एजंटला थेट थ्रेड नियुक्त केला जातो.

```python
thread = agent.get_new_thread() # थ्रेडसह एजंट चालवा.
```

**टूल नोंदणी**

Semantic Kernel मध्ये, टूल्स Kernel कडे नोंदवली जातात आणि नंतर Kernel एजंटला passed केली जाते. MAF मध्ये, टूल्स एजंट तयार करताना थेट नोंदवली जातात.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF आणि AutoGen मधील फरक

**Teams विरुद्ध Workflows**

`Teams` हे AutoGen मधील इव्हेंट-ड्रिव्हन क्रियाकलापासाठी इव्हेंट संरचना आहेत. MAF `Workflows` वापरते जी डेटा ग्राफ-आधारित आर्किटेक्चरद्वारे एक्झिक्युटर्सकडे मार्गदर्शित करतात.

**टूल तयार करणे**

AutoGen मध्ये `FunctionTool` वापरून एजंट्स कॉल करण्यासाठी फंक्शन्स व्रॅप केले जातात. MAF मध्ये @ai_function वापरले जाते जे सारखे कार्य करते परंतु प्रत्येक फंक्शनसाठी स्कीमा स्वयंचलितपणे अनुमानित करते.

**एजंट वर्तन**

AutoGen मध्ये एजंट्स डिफॉल्टनुसार सिंगल-टर्न एजंट असतात जोपर्यंत `max_tool_iterations` हे काही अधिक निर्धारित केलेले नसते. MAF मध्ये `ChatAgent` डीफॉल्टनुसार मल्टी-टर्न असतो म्हणजे तो वापरकर्त्याचे कार्य पूर्ण होईपर्यंत टूल्स कॉल करत राहील.

## कोड नमुने 

Code samples for Microsoft Agent Framework can be found in this repository under `xx-python-agent-framework` and `xx-dotnet-agent-framework` files.

## Microsoft Agent Framework बाबत आणखी प्रश्न आहेत का?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet with other learners, attend office hours and get your AI Agents questions answered.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
अस्वीकरण:
हा दस्तऐवज AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून अनुवादित केला आहे. आम्ही अचूकतेसाठी प्रयत्नशील असलो तरी कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये चुका किंवा असमर्थतेची शक्यता असते. मूळ दस्तऐवज त्याच्या मूळ भाषेत अधिकृत स्रोत म्हणून विचारात घ्यावा. महत्वाच्या माहितीसाठी व्यावसायिक मानवी अनुवादाची शिफारस केली जाते. या अनुवादाच्या वापरामुळे उद्भवणाऱ्या कोणत्याही गैरसमजुती किंवा चुकीच्या अर्थलावण्यामुळे होणाऱ्या नुकसानीबद्दल आम्ही जबाबदार नाही.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->