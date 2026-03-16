# माइक्रोसॉफ्ट एजेंट फ्रेमवर्क का अन्वेषण

![Agent Framework](../../../translated_images/hi/lesson-14-thumbnail.90df0065b9d234ee.webp)

### परिचय

यह पाठ कवर करेगा:

- माइक्रोसॉफ्ट एजेंट फ्रेमवर्क को समझना: मुख्य विशेषताएं और मूल्य  
- माइक्रोसॉफ्ट एजेंट फ्रेमवर्क के मुख्य अवधारणाओं का अन्वेषण
- MAF की तुलना सेमांटिक कर्नेल और AutoGen से: माइग्रेशन गाइड

## सीखने के उद्देश्य

इस पाठ को पूरा करने के बाद, आप जानेंगे कि:

- माइक्रोसॉफ्ट एजेंट फ्रेमवर्क का उपयोग कर उत्पादन-तैयार AI एजेंट कैसे बनाएँ
- माइक्रोसॉफ्ट एजेंट फ्रेमवर्क की मुख्य विशेषताओं को अपने एजेंटिक उपयोग मामलों पर कैसे लागू करें
- मौजूदा एजेंटिक फ्रेमवर्क और टूल्स को माइग्रेट और इंटीग्रेट करें  

## कोड उदाहरण

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) के कोड उदाहरण इस रिपॉजिटरी में `xx-python-agent-framework` और `xx-dotnet-agent-framework` फ़ाइलों के अंतर्गत पाए जा सकते हैं।

## माइक्रोसॉफ्ट एजेंट फ्रेमवर्क को समझना

![Framework Intro](../../../translated_images/hi/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) सेमांटिक कर्नेल और AutoGen के अनुभव और सीख पर आधारित है। यह उत्पादन और अनुसंधान दोनों वातावरणों में देखे गए विभिन्न एजेंटिक उपयोग मामलों को संबोधित करने के लिए लचीलाता प्रदान करता है, जिनमें शामिल हैं:

- जहां चरण-दर-चरण कार्यप्रवाह की आवश्यकता हो, वहां **क्रमिक एजेंट ऑर्केस्ट्रेशन।**
- जहां एजेंटों को एक साथ कार्य पूरा करना हो, वहां **समानांतर ऑर्केस्ट्रेशन।**
- जहां एजेंट एक कार्य पर सहयोग कर सकते हैं, वहां **समूह चैट ऑर्केस्ट्रेशन।**
- जहां एजेंट उपकार्यों के पूरा होने के अनुसार कार्य एक दूसरे को सौंपते हैं, वहां **हैंडऑफ़ ऑर्केस्ट्रेशन।**
- जहां एक प्रबंधक एजेंट कार्य सूची बनाता और संशोधित करता है और उप-एजेंटों का समन्वय करता है, वहां **मैग्नेटिक ऑर्केस्ट्रेशन।**

उत्पादन में AI एजेंट्स प्रदान करने के लिए, MAF में निम्नलिखित विशेषताएं भी शामिल हैं:

- प्रत्येक AI एजेंट की हर क्रिया (जैसे टूल इनवोकेशन, ऑर्केस्ट्रेशन चरण, तर्क प्रवाह, और प्रदर्शन निगरानी) को Microsoft Foundry डैशबोर्ड के माध्यम से OpenTelemetry का उपयोग कर **अवलोकनीयता**।
- Microsoft Foundry पर एजेंट्स को मूल रूप से होस्ट करके **सुरक्षा**, जिसमें भूमिका-आधारित एक्सेस, निजी डेटा हैंडलिंग और अंतर्निहित सामग्री सुरक्षा शामिल हैं।
- एजेंट थ्रेड्स और वर्कफ़्लोज़ को रोकने, पुनः शुरू करने और त्रुटियों से पुनर्प्राप्त करने की क्षमता से लंबी चलने वाली प्रक्रियाओं के लिए **टिकाऊपन**।
- मानव अनुमोदन की आवश्यकता वाले कार्यों को चिह्नित करने वाले मानव संलिप्त वर्कफ़्लोज़ के लिए **नियंत्रण।**

माइक्रोसॉफ्ट एजेंट फ्रेमवर्क का इंटरोऑपरेबिलिटी पर भी ध्यान है, जैसे:

- **क्लाउड-निष्पक्ष** — एजेंट कंटेनरों, ऑन-प्रिमाइज़ और विभिन्न क्लाउड्स पर चल सकते हैं।
- **प्रदाता-निष्पक्ष** — एजेंट Azure OpenAI और OpenAI सहित अपने पसंदीदा SDK के माध्यम से बनाए जा सकते हैं।
- **ओपन स्टैंडर्ड एकीकरण** — एजेंट दूसरे एजेंटों और टूल्स का पता लगाने और उपयोग करने के लिए Agent-to-Agent (A2A) और Model Context Protocol (MCP) जैसे प्रोटोकॉल का उपयोग कर सकते हैं।
- **प्लगइन्स और कनेक्टर्स** — माइक्रोसॉफ्ट फैब्रिक, SharePoint, Pinecone और Qdrant जैसे डेटा और मेमोरी सेवाओं से कनेक्शन बनाए जा सकते हैं।

आइए देखें कि ये विशेषताएं माइक्रोसॉफ्ट एजेंट फ्रेमवर्क की कुछ मुख्य अवधारणाओं पर कैसे लागू होती हैं।

## माइक्रोसॉफ्ट एजेंट फ्रेमवर्क की मुख्य अवधारणाएँ

### एजेंट्स

![Agent Framework](../../../translated_images/hi/agent-components.410a06daf87b4fef.webp)

**एजेंट बनाना**

एजेंट बनाना इनफेरेंस सेवा (LLM प्रदाता), AI एजेंट के लिए अनुसरण करने के निर्देशों के सेट, और एक असाइन किया गया `name` परिभाषित करके किया जाता है:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```
  
ऊपर `Azure OpenAI` का उपयोग किया जा रहा है, लेकिन एजेंट विभिन्न सेवाओं से बनाए जा सकते हैं जिनमें `Microsoft Foundry Agent Service` शामिल है:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```
  
OpenAI के `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```
  
```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```
  
या A2A प्रोटोकॉल का उपयोग करके रिमोट एजेंट्स:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```
  
**एजेंट चलाना**

एजेंट को `.run` या `.run_stream` मेथड्स का उपयोग करके चलाया जाता है, जो गैर-स्ट्रीमिंग या स्ट्रीमिंग प्रतिक्रियाओं के लिए होते हैं।

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```
  
```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```
  
प्रत्येक एजेंट रन में `max_tokens`, उपयोग किए जाने वाले `tools`, और यहां तक कि एजेंट के लिए उपयोग किए जाने वाले `model` जैसे पैरामीटर कस्टमाइज़ करने के विकल्प भी हो सकते हैं।

यह उन मामलों में उपयोगी है जहां उपयोगकर्ता के कार्य को पूरा करने के लिए विशिष्ट मॉडल या टूल की आवश्यकता होती है।

**टूल्स**

टूल्स को एजेंट को परिभाषित करते समय भी परिभाषित किया जा सकता है:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# जब सीधे एक ChatAgent बनाया जा रहा हो

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```
  
और एजेंट चलाते समय भी:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # इस रन के लिए केवल प्रदान किया गया उपकरण )
```
  
**एजेंट थ्रेड्स**

एजेंट थ्रेड्स का उपयोग मल्टी-टर्न वार्तालाप को संभालने के लिए किया जाता है। थ्रेड्स को या तो निम्नलिखित से बनाया जा सकता है:

- `get_new_thread()` का उपयोग करके, जो समय के साथ थ्रेड को सहेजने में सक्षम बनाता है
- एजेंट चलाते समय एक थ्रेड स्वचालित रूप से बनाना, जो केवल वर्तमान रन के दौरान ही रहता है।

थ्रेड बनाने के लिए कोड इस प्रकार दिखता है:

```python
# एक नया थ्रेड बनाएं।
thread = agent.get_new_thread() # एजेंट को थ्रेड के साथ चलाएं।
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```
  
आप बाद में उपयोग के लिए थ्रेड को सीरियलाइज़ भी कर सकते हैं:

```python
# एक नया थ्रेड बनाएं।
thread = agent.get_new_thread() 

# थ्रेड के साथ एजेंट चलाएं।

response = await agent.run("Hello, how are you?", thread=thread) 

# संग्रहण के लिए थ्रेड को सीरियलाइज़ करें।

serialized_thread = await thread.serialize() 

# संग्रहण से लोड करने के बाद थ्रेड की स्थिति को डीसीरियलाइज़ करें।

resumed_thread = await agent.deserialize_thread(serialized_thread)
```
  
**एजेंट मिडलवेयर**

एजेंट उपयोगकर्ता के कार्यों को पूरा करने के लिए टूल्स और LLMs के साथ इंटरैक्ट करते हैं। कुछ परिदृश्यों में, हम इन अन्त:क्रियाओं के बीच कुछ निष्पादित या ट्रैक करना चाहते हैं। एजेंट मिडलवेयर हमें इसे निम्नलिखित के माध्यम से करने की अनुमति देता है:

*फंक्शन मिडलवेयर*

यह मिडलवेयर हमें एजेंट और जिस फंक्शन/टूल को वह कॉल करने वाला है, उसके बीच कोई क्रिया निष्पादित करने की अनुमति देता है। उदाहरण के लिए, आप फंक्शन कॉल पर कुछ लॉगिंग करना चाहते हैं।

नीचे कोड में `next` परिभाषित करता है कि अगला मिडलवेयर या असली फंक्शन कॉल किया जाना चाहिए।

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # पूर्व-संसाधन: फ़ंक्शन निष्पादन से पहले लॉग करें
    print(f"[Function] Calling {context.function.name}")

    # अगले मिडलवेयर या फ़ंक्शन निष्पादन पर जारी रखें
    await next(context)

    # पश्च-संसाधन: फ़ंक्शन निष्पादन के बाद लॉग करें
    print(f"[Function] {context.function.name} completed")
```
  
*चैट मिडलवेयर*

यह मिडलवेयर हमें एजेंट और LLM के बीच अनुरोधों के बीच कोई क्रिया निष्पादित या लॉग करने की अनुमति देता है।

इसमें महत्वपूर्ण जानकारी शामिल होती है जैसे AI सेवा को भेजे जा रहे `messages`।

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # पूर्व-प्रसंस्करण: AI कॉल से पहले लॉग
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # अगले मिडलवेयर या AI सेवा पर जारी रखें
    await next(context)

    # पोस्ट-प्रसंस्करण: AI प्रतिक्रिया के बाद लॉग
    print("[Chat] AI response received")

```
  
**एजेंट मेमोरी**

जैसा कि `Agentic Memory` पाठ में कवर किया गया है, मेमोरी एक महत्वपूर्ण तत्व है जो एजेंट को विभिन्न संदर्भों पर काम करने में सक्षम बनाती है। MAF कई प्रकार की मेमोरी प्रदान करता है:

*इन-मेमोरी स्टोरेज*

यह ऐप्लिकेशन रनटाइम के दौरान थ्रेड्स में संग्रहीत मेमोरी है।

```python
# एक नया थ्रेड बनाएं।
thread = agent.get_new_thread() # थ्रेड के साथ एजेंट चलाएं।
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```
  
*स्थायी संदेश*

यह मेमोरी विभिन्न सेशनों के बीच वार्तालाप इतिहास संग्रहीत करने के लिए उपयोग की जाती है। इसे `chat_message_store_factory` के माध्यम से परिभाषित किया जाता है:

```python
from agent_framework import ChatMessageStore

# एक कस्टम संदेश स्टोर बनाएं
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```
  
*डायनामिक मेमोरी*

यह मेमोरी एजेंट चलाने से पहले संदर्भ में जोड़ी जाती है। ये मेमोरी mem0 जैसी बाहरी सेवाओं में संग्रहीत हो सकती हैं:

```python
from agent_framework.mem0 import Mem0Provider

# उन्नत मेमोरी क्षमताओं के लिए Mem0 का उपयोग कर रहा है
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
  
**एजेंट अवलोकनीयता**

अवलोकनीयता विश्वसनीय और बनाए रखने योग्य एजेंटिक सिस्टम बनाने के लिए महत्वपूर्ण है। MAF बेहतर अवलोकनीयता के लिए OpenTelemetry के साथ एकीकृत होता है ताकि ट्रेसिंग और मीटर मुहैया कराए जा सकें।

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # कुछ करें
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```
  
### वर्कफ़्लोज़

MAF पूर्व-परिभाषित कदमों के साथ वर्कफ़्लोज़ प्रदान करता है जो कार्य पूरा करते हैं और उन चरणों में AI एजेंट को घटकों के रूप में शामिल करते हैं।

वर्कफ़्लोज़ विभिन्न घटकों से बने होते हैं जो बेहतर नियंत्रण प्रवाह की अनुमति देते हैं। वर्कफ़्लोज़ **मल्टी-एजेंट ऑर्केस्ट्रेशन** और वर्कफ़्लो स्थितियों को सहेजने के लिए **चेकपॉइंटिंग** को भी सक्षम करते हैं।

वर्कफ़्लो के मुख्य घटक हैं:

**निष्पादक (Executors)**

निष्पादक इनपुट संदेश प्राप्त करते हैं, अपने निर्दिष्ट कार्य करते हैं, और फिर आउटपुट संदेश उत्पन्न करते हैं। यह वर्कफ़्लो को बड़े कार्य की पूर्ति की ओर अग्रसर करता है। निष्पादक या तो AI एजेंट हो सकते हैं या कस्टम लॉजिक।

**एजेस (Edges)**

एजेस का उपयोग वर्कफ़्लो में संदेशों के प्रवाह को परिभाषित करने के लिए किया जाता है। ये हो सकते हैं:

*प्रत्यक्ष एजेस* - निष्पादकों के बीच सरल एक-से-एक कनेक्शन:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```
  
*सशर्त एजेस* - कुछ शर्त पूरी होने पर सक्रिय होते हैं। उदाहरण के लिए, जब होटल के कमरे उपलब्ध नहीं होते, तो कोई निष्पादक अन्य विकल्प सुझा सकता है।

*स्विच-केस एजेस* - परिभाषित शर्तों के आधार पर संदेशों को विभिन्न निष्पादकों पर रूट करते हैं। उदाहरण के लिए, यदि यात्रा ग्राहक को प्राथमिकता पहुँच है तो उनका कार्य किसी अन्य वर्कफ़्लो के माध्यम से हैंडल होगा।

*फैन-आउट एजेस* - एक संदेश को कई लक्ष्यों पर भेजना।

*फैन-इन एजेस* - अलग-अलग निष्पादकों से कई संदेश एकत्र करना और एक लक्ष्य को भेजना।

**ईवेंट्स**

वर्कफ़्लोज़ में बेहतर अवलोकनीयता प्रदान करने के लिए, MAF निष्पादन के लिए अंतर्निहित ईवेंट प्रदान करता है जिनमें शामिल हैं:

- `WorkflowStartedEvent`  - वर्कफ़्लो निष्पादन शुरू होता है
- `WorkflowOutputEvent` - वर्कफ़्लो आउटपुट उत्पन्न करता है
- `WorkflowErrorEvent` - वर्कफ़्लो में त्रुटि आती है
- `ExecutorInvokeEvent`  - निष्पादक प्रसंस्करण शुरू करता है
- `ExecutorCompleteEvent`  -  निष्पादक प्रसंस्करण समाप्त करता है
- `RequestInfoEvent` - एक अनुरोध जारी किया जाता है

## अन्य फ्रेमवर्क से माइग्रेशन (सेमांटिक कर्नेल और AutoGen)

### MAF और सेमांटिक कर्नेल के बीच अंतर

**सरल एजेंट निर्माण**

सेमांटिक कर्नेल हर एजेंट के लिए कर्नेल इंस्टेंस बनाने पर निर्भर करता है। MAF मुख्य प्रदाताओं के लिए एक्सटेंशन्स का उपयोग करके एक सरल दृष्टिकोण अपनाता है।

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```
  
**एजेंट थ्रेड निर्माण**

सेमांटिक कर्नेल में थ्रेड मैन्युअली बनाए जाते हैं। MAF में, एजेंट को सीधे एक थ्रेड असाइन किया जाता है।

```python
thread = agent.get_new_thread() # एजेंट को थ्रेड के साथ चलाएं।
```
  
**टूल पंजीकरण**

सेमांटिक कर्नेल में, टूल कर्नेल में पंजीकृत होते हैं और फिर कर्नेल एजेंट को दिया जाता है। MAF में, टूल एजेंट निर्माण प्रक्रिया के दौरान सीधे पंजीकृत होते हैं।

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```
  
### MAF और AutoGen के बीच अंतर

**टीम बनाम वर्कफ़्लोज़**

AutoGen में `Teams` एजेंट्स के साथ ईवेंट संचालित गतिविधि के लिए इवेंट संरचना हैं। MAF `Workflows` का उपयोग करता है जो डेटा को निष्पादकों तक ग्राफ आधारित वास्तुकला के माध्यम से मार्गदर्शित करता है।

**टूल निर्माण**

AutoGen एजेंट्स को कॉल करने के लिए `FunctionTool` का उपयोग करता है। MAF @ai_function का उपयोग करता है जो समान रूप से काम करता है लेकिन प्रत्येक फंक्शन के लिए स्कीमाओं का भी स्वतः अनुमान लगाता है।

**एजेंट व्यवहार**

AutoGen में एजेंट डिफ़ॉल्ट रूप से सिंगल-टर्न होते हैं जब तक कि `max_tool_iterations` उच्च सेट न हो। MAF में `ChatAgent` डिफ़ॉल्ट रूप से मल्टी-टर्न होता है, जिसका अर्थ है कि यह तब तक टूल कॉल करता रहेगा जब तक उपयोगकर्ता का कार्य पूरा नहीं हो जाता।

## कोड उदाहरण

माइक्रोसॉफ्ट एजेंट फ्रेमवर्क के कोड उदाहरण इस रिपॉजिटरी में `xx-python-agent-framework` और `xx-dotnet-agent-framework` फ़ाइलों के अंतर्गत पाए जा सकते हैं।

## माइक्रोसॉफ्ट एजेंट फ्रेमवर्क के बारे में आपके और प्रश्न हैं?

अन्य शिक्षार्थियों से मिलने, ऑफिस आवर अटेंड करने और अपने AI एजेंट्स के प्रश्नों के उत्तर पाने के लिए [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) जुड़ें।

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**अस्वीकरण**:  
यह दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनूदित किया गया है। यद्यपि हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवाद में त्रुटियाँ या असत्यताएँ हो सकती हैं। मूल भाषा में मूल दस्तावेज़ को अधिकारिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए पेशेवर मानव अनुवाद की सिफारिश की जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->