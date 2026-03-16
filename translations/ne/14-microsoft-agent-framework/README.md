# Microsoft Agent Framework को अन्वेषण

![Agent Framework](../../../translated_images/ne/lesson-14-thumbnail.90df0065b9d234ee.webp)

### परिचय

यस पाठले समेट्नेछ:

- Microsoft Agent Framework बुझ्ने: मुख्य विशेषताहरू र मान  
- Microsoft Agent Framework का मुख्य अवधारणाहरूको अन्वेषण
- MAF लाई Semantic Kernel र AutoGen सँग तुलना: माइग्रेशन गाइड

## सिकाइ लक्ष्यहरू

यो पाठ पूरा गरेपछि, तपाईं जान्न सक्नुहुनेछ:

- Microsoft Agent Framework प्रयोग गरी उत्पादन प्रयोग गर्न योग्य AI एजेन्टहरू बनाउन
- Microsoft Agent Framework का कोर विशेषताहरूलाई तपाईंको Agentic प्रयोग केसहरूमा लागू गर्न
- अवस्थित Agentic फ्रेमवर्कहरू र उपकरणहरू माइग्रेट र एकीकरण गर्न  

## कोड नमूनाहरू

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) का कोड नमूनाहरू यस रिपोजिटरीमा `xx-python-agent-framework` र `xx-dotnet-agent-framework` फाइलहरू अन्तर्गत पाउन सकिन्छ।

## Microsoft Agent Framework बुझ्ने

![Framework Intro](../../../translated_images/ne/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) Semantic Kernel र AutoGen बाट प्राप्त अनुभव र सिकाइहरू माथि निर्माण गरिएको छ। यसले उत्पादन र अनुसन्धान वातावरणहरूमा देखिएका विभिन्न प्रकारका agentic प्रयोग केसहरूलाई सम्बोधन गर्ने लचीलोपन प्रदान गर्दछ जसमा:

- **क्रमसंगत एजेन्ट अनुशासन** जहाँ चरण-दर-चरण कार्यप्रवाह आवश्यक हुन्छ।
- **समवर्ती अनुशासन** जहाँ एजेन्टहरूले एउटै समयमा कार्य पूरा गर्नुपर्छ।
- **समूह च्याट अनुशासन** जहाँ एजेन्टहरूले एकै कार्यमा सँगै सहकार्य गर्न सक्छन्।
- **ह्यान्डअफ अनुशासन** जहाँ एजेन्टहरूले एकअर्कालाई उपकार्यहरू पूरा भएपछि कार्य हस्तान्तरण गर्छन्।
- **म्याग्नेटिक अनुशासन** जहाँ प्रबन्धक एजेन्टले कार्य सूची सिर्जना र परिमार्जन गर्छ र उपएजेन्टहरूको समन्वय सम्हाल्छ कार्य पूरा गर्न।

AI एजेन्टहरू उत्पादनमा उपलब्ध गराउन, MAF ले निम्न सुविधाहरू पनि समावेश गरेको छ:

- **अवलोकनक्षमता** OpenTelemetry को प्रयोग मार्फत जहाँ AI एजेन्टको हरेक क्रिया जस्तै उपकरण बोलाउने, अनुशासनका चरणहरू, तर्क प्रवाहहरू र Microsoft Foundry ड्यासबोर्डहरू मार्फत प्रदर्शन अनुगमन गरिएको हुन्छ।
- **सुरक्षा** Microsoft Foundry मा नेटिभ रूपमा एजेन्टहरू होस्ट गरेर जसमा भूमिका-आधारित पहुँच, निजी डेटा ह्यान्डलिंग, र बिल्ट-इन सामग्री सुरक्षा जस्ता सुरक्षा नियन्त्रणहरू समावेश छन्।
- **टिकाउपन** किनभने एजेन्ट थ्रेडहरू र कार्य प्रवाहहरू रोक्न, पुन: सुरु गर्न र त्रुटिहरूबाट पुनः प्राप्त गर्न सकिन्छ जसले लामो समयसम्म चल्ने प्रक्रियाहरू सक्षम बनाउँछ।
- **नियन्त्रण** किनभने मानवीय अनुमोदन आवश्यक पर्ने कार्यहरू चिन्ह लगाउँदै मानवीय इन-लूप कार्यप्रवाहहरू समर्थन गरिन्छ।

Microsoft Agent Framework ले अन्तरसञ्चालनीयताको लागि पनि जोड दिन्छ:

- **क्लाउड-एग्नोस्टिक हुने** - एजेन्टहरू कन्टेनरहरूमा, अन-प्रिम र विभिन्न क्लाउडहरूमा चलाउन सकिन्छ।
- **प्रदाता-एग्नोस्टिक हुने** - एजेन्टहरू तपाईंको रोजाइको SDK मार्फत सिर्जना गर्न सकिन्छ जसमा Azure OpenAI र OpenAI समावेश छन्।
- **खुला मानकहरू एकीकरण गर्ने** - एजेन्टहरू Agent-to-Agent (A2A) र Model Context Protocol (MCP) जस्ता प्रोटोकलहरू प्रयोग गरेर अन्य एजेन्टहरू र उपकरणहरू पत्ता लगाउन र प्रयोग गर्न सक्छन्।
- **प्लगइनहरू र कनेक्टर्स** - Microsoft Fabric, SharePoint, Pinecone र Qdrant जस्ता डेटा र मेमोरी सेवाहरूमा जडान गर्न सकिन्छ।

अब हेरौं यी सुविधाहरू Microsoft Agent Framework का केही मुख्य अवधारणाहरूमा कसरी लागू गरिन्छ।

## Microsoft Agent Framework का मुख्य अवधारणाहरू

### एजेन्टहरू

![Agent Framework](../../../translated_images/ne/agent-components.410a06daf87b4fef.webp)

**एजेन्ट सिर्जना**

एजेन्ट सिर्जना LLM प्रदायकको रुपमा इन्फरेन्स सेवा परिभाषित गरेर, AI एजेन्टले पालना गर्नुपर्ने निर्देशनहरूको सेट र एक `name` तोक्दै गरिन्छ:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

माथिको उदाहरणमा `Azure OpenAI` प्रयोग गरिएको छ तर एजेन्टहरू विभिन्न सेवाहरू जस्तै `Microsoft Foundry Agent Service` मार्फत पनि सिर्जना गर्न सकिन्छ:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI का `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

वा A2A प्रोटोकल प्रयोग गरेर रिमोट एजेन्टहरू:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**एजेन्ट चलाउने**

एजेन्टहरू `.run` वा `.run_stream` विधिहरू प्रयोग गरी नन-स्ट्रीमिङ वा स्ट्रीमिङ जवाफका लागि चलाइन्छन्।

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

हरेक एजेन्ट चलाउन विकल्पहरू पनि हुन्छन् जुन जस्तै एजेन्टले प्रयोग गर्ने `max_tokens`, एजेन्टले बोलाउन सक्ने `tools`, र एजेन्टका लागि प्रयोग भएको `model` पनि फरक पार्न सकिन्छ।

यो उपयोगी हुन्छ जहाँ प्रयोगकर्ताको कार्य पूरा गर्न विशिष्ट मोडेल वा उपकरणहरू आवश्यक हुन्छन्।

**उपकरणहरू**

उपकरणहरू एजेन्ट परिभाषा गर्दा:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# सिधै ChatAgent बनाउँदा

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

र एजेन्ट चलाउँदा पनि परिभाषित गर्न सकिन्छ:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # यस रनको लागि मात्र प्रदान गरिएको उपकरण )
```

**एजेन्ट थ्रेडहरू**

एजेन्ट थ्रेडहरू बहु-पटक संवादहरू सम्हाल्न प्रयोग गरिन्छ। थ्रेडहरू यसरी सिर्जना गर्न सकिन्छ:

- `get_new_thread()` प्रयोग गरेर जसले थ्रेडलाई समयक्रममा बचत गर्न योग्य बनाउँछ
- एजेन्ट चलाउँदा स्वतः थ्रेड सिर्जना गर्ने र त्यो थ्रेड अहिलेको चलाइ अवधिभर मात्र रहने।

थ्रेड सिर्जना गर्न कोड यस प्रकार छ:

```python
# नयाँ थ्रेड सिर्जना गर्नुहोस्।
thread = agent.get_new_thread() # थ्रेडसँग एजेन्ट चलाउनुहोस्।
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

पछि थ्रेडलाई पछि प्रयोगको लागि सिरीयलाईज गर्न सकिन्छ:

```python
# नयाँ थ्रेड सिर्जना गर्नुहोस्।
thread = agent.get_new_thread() 

# थ्रेडसहित एजेन्ट चलाउनुहोस्।

response = await agent.run("Hello, how are you?", thread=thread) 

# संग्रहणको लागि थ्रेडलाई सिरियलाइज गर्नुहोस्।

serialized_thread = await thread.serialize() 

# संग्रहणबाट लोड गरेपछि थ्रेड अवस्था डीसिरियलाइज गर्नुहोस्।

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**एजेन्ट मिडलवेयर**

एजेन्टहरूले उपकरण र LLMसंग अन्तर्क्रिया गरेर प्रयोगकर्ताका कार्यहरू पूरा गर्छन्। केही परिस्थितिमा हामी यी अन्तर्क्रियाहरूको बीचमा केहि कार्य गर्न वा ट्र्याक गर्न चाहन्छौं। एजेन्ट मिडलवेयरले यसलाई यसरी अनुमति दिन्छ:

*फंक्शन मिडलवेयर*

यो मिडलवेयरले एजेन्ट र एक फंक्शन/उपकरण बीच कार्य सम्पादन गर्न अनुमति दिन्छ जुन बोलाउनु पर्ने हुन्छ। उदाहरणका लागि, फंक्शन कलमा लगिङ गर्न चाहिंदा प्रयोग गरिन्छ।

माथिको कोडमा `next` ले अर्को मिडलवेयर वा वास्तविक फंक्शन कल गर्नु पर्ने हो कि भनेर निर्धारण गर्छ।

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # पूर्व-संस्करण: कार्यक्षमता सञ्चालन हुनु अघि लग इन गर्नुहोस्
    print(f"[Function] Calling {context.function.name}")

    # अर्को मिडलवेयर वा कार्यक्षमता सञ्चालन तर्फ अगाडि बढ्नुहोस्
    await next(context)

    # पश्च-संस्करण: कार्यक्षमता सञ्चालन पछि लग इन गर्नुहोस्
    print(f"[Function] {context.function.name} completed")
```

*च्याट मिडलवेयर*

यो मिडलवेयरले एजेन्ट र LLM बिचका अनुरोधहरूबीच कार्यहरू सम्पादन वा लग गर्न अनुमति दिन्छ।

यसमा AI सेवामा पठाइएका `messages` जस्ता महत्वपूर्ण जानकारीहरू हुन्छन्।

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # पूर्व-प्रक्रमण: AI कलअघि लग
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # अर्को मिडलवेयर वा AI सेवा तर्फ जारी राख्नुहोस्
    await next(context)

    # पश्च-प्रक्रमण: AI प्रतिक्रिया पछाडि लग
    print("[Chat] AI response received")

```

**एजेन्ट मेमोरी**

`Agentic Memory` पाठमा चर्चा गरे अनुसार, मेमोरी एजेन्टलाई विभिन्न सन्दर्भहरूमा सञ्चालन गर्न महत्त्वपूर्ण हो। MAF ले विभिन्न प्रकारका मेमोरीहरू प्रस्ताव गरेको छ:

*इन-मेमोरी स्टोरेज*

यो मेमोरी अप्लिकेशन रनटाइमको क्रममा थ्रेडहरूमा भण्डारण हुन्छ।

```python
# नयाँ थ्रेड सिर्जना गर्नुहोस्।
thread = agent.get_new_thread() # त्या थ्रेडसँग एजेण्ट चलाउनुहोस्।
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*स्थायी सन्देशहरू*

यो मेमोरी विभिन्न सत्रहरूमा संवाद इतिहास भण्डारण गर्न प्रयोग हुन्छ। यसलाई `chat_message_store_factory` को प्रयोगले परिभाषित गरिन्छ:

```python
from agent_framework import ChatMessageStore

# एउटा अनुकूल सन्देश भण्डारण सिर्जना गर्नुहोस्
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*डायनामिक मेमोरी*

यो मेमोरी एजेन्टहरू चलाउनु अघि सन्दर्भमा थपिन्छ। यी मेमोरीहरू बाह्य सेवाहरू जस्तै mem0 मा भण्डारण गर्न सकिन्छ:

```python
from agent_framework.mem0 import Mem0Provider

# उन्नत मेमोरी क्षमताहरूको लागि Mem0 प्रयोग गर्दै
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

**एजेन्ट अवलोकनक्षमता**

अवलोकनक्षमता विश्वसनीय र कायम रहने एजेन्ट प्रणालीहरू निर्माण गर्न महत्त्वपूर्ण छ। MAF ले OpenTelemetry सँग एकीकृत भएर ट्रेसिङ र मीटरहरू प्रदान गर्दछ जुन अवलोकनक्षमता सुधार गर्छ।

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # केहि गर्नुहोस्
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### कार्यप्रवाहहरू

MAF ले पूर्वनिर्धारित चरणहरू समावेश गर्ने कार्यप्रवाहहरू प्रदान गर्दछ जसले कार्य पूरा गर्न AI एजेन्टहरूलाई कम्पोनेन्टको रूपमा समेट्छ।

कार्यप्रवाहहरू विभिन्न कम्पोनेन्टहरू मिलेर बनेका छन् जसले नियन्त्रण प्रवाहलाई सुधार्छ। कार्यप्रवाहहरूले **बहु-एजेन्ट अनुशासन** र **चेकपोइन्टिंग** पनि सक्षम पार्छ जसले कार्यप्रवाह अवस्थाहरू बचत गर्न मद्दत गर्छ।

कार्यप्रवाहका मुख्य कम्पोनेन्टहरू:

**एग्जिक्युटरहरू**

एग्जिक्युटरहरूले इनपुट सन्देशहरू प्राप्त गर्छन्, तोकिएका कार्यहरू गर्छन् र आउटपुट सन्देश उत्पादन गर्छन्। यसले कार्यप्रवाहलाई ठूलो कार्यको पूर्णतर्फ अगाडि बढाउँछ। एग्जिक्युटरहरू AI एजेन्ट वा कस्टम लॉजिक हुन सक्छन्।

**एजहरू**

एजहरू कार्यप्रवाहमा सन्देशहरूको प्रवाह परिभाषित गर्न प्रयोग गरिन्छ। यी हुन सक्छन्:

*प्रत्यक्ष एजहरू* - एग्जिक्युटरहरूबीच सधैं एक-देखि-एक जडानहरू:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*सशर्त एजहरू* - कुनै सर्त पूरा भएपछि सक्रिय हुने। उदाहरणका लागि, होटल कोठाहरू उपलब्ध नभएमा, एग्जिक्युटरले अन्य विकल्पहरू सुझाउन सक्छ।

*स्विच-केस एजहरू* - सर्तहरू अनुसार सन्देशहरू विभिन्न एग्जिक्युटरहरूमा पठाउने। उदाहरणका लागि, यात्रा ग्राहकलाई प्राथमिकता पहुँच भएमा र तिनका कार्यहरू अर्को कार्यप्रवाहबाट सम्हालिने।

*फ्यान-आउट एजहरू* - एउटै सन्देशलाई बहु लक्षितहरूमा पठाउने।

*फ्यान-इन एजहरू* - विभिन्न एग्जिक्युटरहरूबाट बहु सन्देशहरू सङ्कलन गरेर एउटा लक्ष्यमा पठाउने।

**घटनाहरू**

कार्यप्रवाहहरूको राम्रो अवलोकनक्षमताका लागि, MAF ले कार्यसम्पादनका लागि बिल्ट-इन घटनाहरू उपलब्ध गराउँछ जसमा समावेश छन्:

- `WorkflowStartedEvent` - कार्यप्रवाहको सञ्चालन सुरु हुन्छ
- `WorkflowOutputEvent` - कार्यप्रवाहले आउटपुट उत्पादन गर्छ
- `WorkflowErrorEvent` - कार्यप्रवाहले त्रुटि सामना गर्छ
- `ExecutorInvokeEvent` - एग्जिक्युटरले प्रक्रिया सुरु गर्छ
- `ExecutorCompleteEvent` - एग्जिक्युटरले प्रक्रिया समाप्त गर्छ
- `RequestInfoEvent` - अनुरोध जारी गरिएको छ

## अन्य फ्रेमवर्कहरूबाट माइग्रेट गर्दै (Semantic Kernel र AutoGen)

### MAF र Semantic Kernel बीच भिन्नताहरू

**सरल एजेन्ट सिर्जना**

Semantic Kernel हरेक एजेन्टका लागि Kernel instance सिर्जना गर्नमा निर्भर हुन्छ। MAF ले मुख्य प्रदायकहरूको लागि एक्सटेन्सनहरू प्रयोग गरेर सरल तरिका अपनाएको छ।

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**एजेन्ट थ्रेड सिर्जना**

Semantic Kernel मा थ्रेडहरू म्यानुअली सिर्जना गर्नुपर्छ। MAF मा, एजेन्टलाई सिधै थ्रेड प्रदान गरिन्छ।

```python
thread = agent.get_new_thread() # एजेन्टलाई थ्रेडसहित चलाउनुहोस्।
```

**उपकरण दर्ता**

Semantic Kernel मा उपकरणहरू Kernel लाई दर्ता गरिन्छ र त्यसपछि Kernel एजेन्टमा पठाइन्छ। MAF मा, उपकरणहरू एजेन्ट सिर्जनाको समयमा सिधै दर्ता गरिन्छ।

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF र AutoGen बीच भिन्नताहरू

**Teams बनाम Workflows**

`Teams` AutoGen मा एजेन्टहरूसँग घटना-चालित गतिविधिका लागि घटना संरचना हो। MAF ले `Workflows` प्रयोग गर्छ जुन ग्राफ-आधारित संरचनाबाट डेटा एग्जिक्युटरहरूमा मार्गनिर्देशन गर्छ।

**उपकरण सिर्जना**

AutoGen ले `FunctionTool` प्रयोग गरेर एजेन्टहरूले बोलाउने फंक्शनहरूलाई र्याप गर्छ। MAF ले @ai_function प्रयोग गर्छ जुन समान रूपमा काम गर्छ र प्रत्येक फंक्शनका स्किमाहरू स्वतः अनुमान लगाउँछ।

**एजेन्ट व्यवहार**

AutoGen मा एजेन्टहरू डिफल्ट रूपमा एकल-पटक एजेन्टहरू हुन्छन् जबसम्म `max_tool_iterations` बढाइएको हुँदैन। MAF भित्र `ChatAgent` डिफल्ट रूपमा बहु-पटक हो जसको अर्थ यो हो कि प्रयोगकर्ताको कार्य पूरा नभएसम्म उपकरणहरू बोलाइरहन सक्छ।

## कोड नमूनाहरू

Microsoft Agent Framework का कोड नमूनाहरू यस रिपोजिटरीका `xx-python-agent-framework` र `xx-dotnet-agent-framework` फाइलहरूमा पाउन सकिन्छ।

## Microsoft Agent Framework सम्बन्धी थप प्रश्नहरू छ?

अन्य सिक्नेहरूसँग भेट्न, अफिस आवर्समा सहभागी हुन र तपाईंका AI एजेन्टका प्रश्नहरूको जवाफ पाउन [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) मा सहभागी हुनुहोस्।

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**अस्वीकरण**:
यस दस्तावेजलाई AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) प्रयोग गरी अनुवाद गरिएको हो। हामी सटीकताको प्रयास गर्दैछौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादहरूमा त्रुटि वा असंगतिहरू हुन सक्छन्। मूल दस्तावेजलाई यसको मातृभाषामा अधिकारिक स्रोत मानिनुपर्छ। महत्वपूर्ण जानकारीहरूको लागि, व्यावसायिक मानव अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट हुने कुनै पनि गलतफहमी वा गलत व्याख्याहरूको लागि हामी जिम्मेवार हुनेछैनौं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->