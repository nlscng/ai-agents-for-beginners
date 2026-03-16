# Microsoft முகவர் கட்டமைப்பைக் கண்டறிதல்

![Agent Framework](../../../translated_images/ta/lesson-14-thumbnail.90df0065b9d234ee.webp)

### அறிமுகம்

இந்த பாடத்தில் கையாளப்படும் புள்ளிகள்:

- Microsoft முகவர் கட்டமைப்பை புரிந்துகொள்வது: முக்கிய அம்சங்கள் மற்றும் மதிப்பு  
- Microsoft முகவர் கட்டமைப்பின் முக்கிய கருத்துக்களை ஆராய்தல்
- MAF ஐ Semantic Kernel மற்றும் AutoGen உடன் ஒப்பிடுதல்: மாற்றம் வழிகாட்டி

## கற்றல் இலக்குகள்

இந்த பாடத்தை முடித்த பிறகு, நீங்கள் புரிந்துகொள்வீர்கள்:

- Microsoft முகவர் கட்டமைப்பைப் பயன்படுத்தி தயாரிப்பு தயார் செயற்கை நுண்ணறிவு முகவர்களை உருவாக்குவது
- Microsoft முகவர் கட்டமைப்பின் முக்கிய அம்சங்களை உங்கள் முகவர் பயன்பாட்டுக்கேற்றவாறு பயன் படுத்துவது
- உள்ளமைவு முகவர் கட்டமைப்புகள் மற்றும் கருவிகளை நகர்த்தி ஒருங்கிணைப்பது  

## குறியீட்டு எடுத்துக்காட்டுகள்

[Microsoft முகவர் கட்டமைப்பு (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) குறியீட்டு எடுத்துக்காட்டுகள் இந்த கோப்பு தொகுப்பில் `xx-python-agent-framework` மற்றும் `xx-dotnet-agent-framework` கோப்புகளின் கீழ் உள்ளன.

## Microsoft முகவர் கட்டமைப்பை புரிதல்

![Framework Intro](../../../translated_images/ta/framework-intro.077af16617cf130c.webp)

[Microsoft முகவர் கட்டமைப்பு (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) Semantic Kernel மற்றும் AutoGen இல் இருந்து கிடைத்த அனுபவமும் கற்றல்களும் அடிப்படையாகக் கொண்டு கட்டப்பட்டுள்ளது. இது உருவாக்கத்திலும் ஆராய்ச்சி சூழல்களிலும் காணப்படும் முகவர் பயன்பாடுகளின் பரவலான சிறப்பம்சங்களைத் தீர்க்க சவர்க்கமான சுதந்திரத்தைக் கொடுக்கிறது, இதில்:

- **தொடர்புடைய முகவர் ஒருங்கிணைப்பு** அடி-அடி பணிகள் தேவைப்படும் நிலைகளில்.
- **ஒரே நேரத்தில் ஒருங்கிணைப்பு** முகவர்கள் ஒரே நேரத்தில் பணிகளை முடிக்க வேண்டிய நிலைகளில்.
- **குழு அரட்டையொன்றின் ஒருங்கிணைப்பு** முகவர்கள் ஒரே பணிக்கு இணைந்து செயல்படக்கூடிய நிலைகளில்.
- **கையளிப்பு ஒருங்கிணைப்பு** துணைப் பணிகள் விரைவாக முடிந்தவுடன் முகவர்கள் ஒருவருக்கு மற்றொருவர் பணியை ஒப்படைக்கும் நிலைகளில்.
- **காந்த ஒருங்கிணைப்பு** மேலாளர் முகவர் பணியினை உருவாக்கி மாற்றி துணை முகவர்களின் ஒருங்கிணைப்பை கையாளும் நிலைகளில்.

தயாரிப்பில் AI முகவர்களை வழங்க, MAF இல் கீழ்க்கண்ட அம்சங்களும் உள்ளன:

- **காணுதலாக்கம் (Observability)** OpenTelemetry ஐ பயன்படுத்தி AI முகவர் செயல்பாடுகளை, கருவி அழைப்புகள், ஒருங்கிணைப்பு படிகள், பரிந்துரைகள் மற்றும் Microsoft Foundry டாஷ்போர்ட்களை நுழைந்து கண்காணிப்பு.
- **பாதுகாப்பு** Microsoft Foundry இல் உள்ளடக்கமாக முகவர்களை நடத்துதல், இதில் பங்கு அடிப்படையிலான அணுகல், தனிப்பட்ட தரவுகள் கையாளல் மற்றும் உள்ளமைவான உள்ளடக்க பாதுகாப்பு போன்றக் கட்டுப்பாடுகள் உள்ளன.
- **நிலைத்தன்மை** ஏஜென்ட் திரெட்கள் மற்றும் பணிமுறைகள் இடைவேளை கொள்வதும் மறுசுழற்சி செய்யவதும் தவறுகளை மீள்பெறும் வகையில் அமைக்கப்படுகிறது, இது நீண்ட காலமாக செயல்பட உதவுகிறது.
- **கட்டுப்பாடு** மனித உட்புகு பணிவழிச்செயல்களை ஆதரிக்கிறது, இதில் பணிகள் மனித அங்கீகாரத்தைச் சரிபார்க்கும் நிலையில் குறிக்கப்படுகிறது.

Microsoft முகவர் கட்டமைப்பு கீழ்க்கண்டவாறு ஒருங்கிணைப்பு சுதந்திரத்தை முன்னிட்டு உள்ளது:

- **கிளவுட் சாராததாக இருக்கிறது** - முகவர்கள் கண்டெயினர்கள், ஆன-பிரேமிஸ் மற்றும் பல்வேறு கிளவுட்களில் இயங்க முடியும்.
- **சேவையக சாயல் இல்லாமல் உள்ளது** - முகவர்கள் Azure OpenAI மற்றும் OpenAI உட்பட நீங்கள் விரும்பும் SDK மூலம் உருவாக்கப்படலாம்.
- **திறந்த தரநிலைகளுடன் ஒருங்கிணைப்பு** - முகவர்கள் முகவர்-முகவர் (A2A) மற்றும் மாதிரி காட்சி நெறிமுறை (MCP) போன்ற பாதைகள் மூலம் மற்ற முகவர்களையும் கருவிகளையும் கண்டுபிடித்து பயன்படுத்த முடியும்.
- **பிளகின்கள் மற்றும் இணைப்பிகள்** - Microsoft Fabric, SharePoint, Pinecone மற்றும் Qdrant போன்ற தரவு மற்றும் நினைவகம் சேவைகளுடன் கானெக்ஷன் செய்யலாம்.

இந்த அம்சங்கள் Microsoft முகவர் கட்டமைப்பின் சில முக்கிய கருத்துக்களில் எப்படி பயன்படுத்தப்படுகின்றன என்பதைக் காண்போம்.

## Microsoft முகவர் கட்டமைப்பின் முக்கிய கருத்துக்கள்

### முகவர்கள்

![Agent Framework](../../../translated_images/ta/agent-components.410a06daf87b4fef.webp)

**முகவர்களை உருவாக்குதல்**

முகவர் உருவாக்கம் என்பது inference சேவையை (LLM வழங்குநர்),  
AI முகவர் பின்பற்ற வேண்டிய பணிக்குறிப்புகளை மற்றும் அளிக்கப்பட்ட `பெயரை` வரையறுத்தல் ஆகும்:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

மேலே `Azure OpenAI` பயன்படுத்தியுள்ளோம், ஆனால் முகவர்கள் பின்வரும் சேவைகளை பயன்படுத்தியும் உருவாக்கலாம் `Microsoft Foundry Agent Service` உட்பட:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` API கள்

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

அல்லது A2A நெறிமுறையை பயன்படுத்தி தொலை முகவர்கள்:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**முகவர்களை இயக்கு**

முகவர்கள் `.run` அல்லது `.run_stream` முறைகளைக் கொண்டு விரைவிலோ அல்லது ஸ்ட்ரீமிங் பதில்களுக்கோ இயங்குவார்கள்.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

ஒவ்வொரு முகவர் இயக்கத்திலும் முகவர் பயன்படுத்தும் `max_tokens`, அழைக்கக் கூடிய `tools` மற்றும் கூடவே அந்த முகவருக்கு பயன்படுத்தப்படும் `model` போன்ற விருப்பங்களை தனிப்பயன்படுத்தலாம்.

இந்த வசதி குறிப்பிட்ட மாதிரிகள் அல்லது கருவிகள் பயனர்களின் பணிகளை முடிக்க தேவையான சூழலில் பயனுள்ளது.

**கருவிகள்**

கருவிகள் முகவர்களை வரையறுக்கும் போது:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# ChatAgent நேரடியாக உருவாக்கும் போது

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

அதன்பின் முகவர்களை இயக்கும் போதும் வரையறுக்கலாம்:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # இந்த ஓட்டத்திற்காக மட்டும் வழங்கப்பட்ட கருவி )
```

**முகவர் திரெட்கள்**

முகவர் திரெட்கள் பன்முறை உரையாடலை கையாள உதவும். திரெட்களை உருவாக்கும் வழிகள்:

- `get_new_thread()` பயன்படுத்தி திரெட்டை காலத்திற்குள் சேமிக்க முடியும்.
- முகவர்களை இயக்கும் போது திரெடை தானாக உருவாகி அந்த இயக்கத்தில் மட்டுமே நிலவும்.

திரெட்டை உருவாக்க குறியீடு இவ்வாறு இருக்கும்:

```python
# ஒரு புதிய திருமலை உருவாக்கவும்.
thread = agent.get_new_thread() # அந்த திருமலுடன் முகவரியை இயக்கவும்.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

பின்னர் திரெட்டை பின்னர் பயன்படுத்தும்போது சேமிக்க சீரியலைஸ் செய்யலாம்:

```python
# புதிய தாரத்தை உருவாக்குக.
thread = agent.get_new_thread() 

# தாரத்துடன் முகவரியை இயக்குக.

response = await agent.run("Hello, how are you?", thread=thread) 

# சேமிப்புக்காக தாரத்தை சீரமைக்கவும்.

serialized_thread = await thread.serialize() 

# சேமிப்பிலிருந்து ஏற்றிய பிறகு தாரத்தின் நிலையைக் குறியிடுக.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**முகவர் மிடில்வேர்**

முகவர்கள் கருவிகள் மற்றும் LLM களைச் சேர்ந்த செயல்பாடுகளை நிறைவேற்றும் போது, நாம் அவற்றுக்கிடையில் செயல்களை மேற்கொள்ள விரும்பும் போது. முகவர் மிடில்வேர் இதைச் செய்ய உதவுகிறது:

*செயல்பாடு மிடில்வேர்*

இந்த மிடில்வேர் முகவரும் அதன் அழைக்கும் செயல்பாடு / கருவியும் இடையில் செயல்பாடுகளை செய்துவிட்டுப் கண்காணிக்க உதவுகிறது. உதாரணமாக, ஒருநேரத்தில் செயல்பாடு அழைப்பில் பதிவு செய்யலாம்.

கீழ்காணும் குறியீட்டில் `next` அடுத்த மிடில்வேரை அல்லது உண்மையான செயல்பாட்டை அழைக்கத் தீர்மானிக்கிறது.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # முன்னணி செயலாக்கம்: செயல்பாடு நடப்பதற்கு முன் பதிவேடு
    print(f"[Function] Calling {context.function.name}")

    # அடுத்த மிடில்வேர் அல்லது செயல்பாடு செயல்படுத்த தொடரவும்
    await next(context)

    # பிந்தைய செயலாக்கம்: செயல்பாடு முடிந்தவுடன் பதிவேடு
    print(f"[Function] {context.function.name} completed")
```

*அரட்டை மிடில்வேர்*

இந்த மிடில்வேர் முகவர் மற்றும் LLM இடையேயான அரட்டை கோரிக்கைகளுக்கு இடையில் செயல்பாடுகளை பதிவு செய்யவும், செயல்படுத்தவும் உதவுகிறது.

இதில் AI சேவைக்கு அனுப்பப்படும் `messages` என்ன என்பதற்கான முக்கிய தகவல்கள் உள்ளன.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # முன்-செயலாக்கம்: AI அழைப்பிற்குள் பதிவு செய்யவும்
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # அடுத்த மிடில்வேர் அல்லது AI சேவைக்கு தொடரவும்
    await next(context)

    # பின்-செயலாக்கம்: AI பதிலுக்கு பிறகு பதிவு செய்யவும்
    print("[Chat] AI response received")

```

**முகவர் நினைவகம்**

`Agentic Memory` பாடத்தில் பேசப்பட்டபடி, நினைவகம் என்பது முகவரின் வித்தியாசமான சூழல்களில் செயல்பட உதவும் முக்கிய கூறு. MAF பலவிதமான நினைவகங்கள் வழங்குகிறது:

*நினைவக சேமிப்பு*

இது செயலியில் உள்ள திரெட்களில் சேமிக்கப்படும் நினைவகம்.

```python
# புதிய திரையில் உருவாக்கவும்.
thread = agent.get_new_thread() # அந்த திரையுடன் முகவரியை இயக்கவும்.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*நிலையான செய்திகள்*

பல்வேறு அமர்வுக்களுக்கு இடையேயான உரையாடல் வரலாறு சேமிக்க பயன்படும் நினைவகம். இது `chat_message_store_factory` மூலம் வரையறுக்கப்பட்டுள்ளது:

```python
from agent_framework import ChatMessageStore

# ஒரு தனிப்பயன் செய்தி சேமிப்பிடம் உருவாக்கவும்
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*இடையெனும் நினைவகம்*

முகவர்கள் இயங்குவதற்கு முன் சூழலில் சேர்க்கப்படும் நினைவகம். mem0 போன்ற வெளிப்புற சேவைகளில் சேமிக்க முடியும்:

```python
from agent_framework.mem0 import Mem0Provider

# முன்னேறிய நினைவக திறன்களுக்கு Mem0 ஐப் பயன்படுத்துதல்
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

**முகவர் காணுதலாக்கம்**

காணுதலாக்கம் என்பது நம்பகமான மற்றும் பராமரிக்கக்கூடிய முகவர் அமைப்புகளை உருவாக்க முக்கியம். MAF OpenTelemetry உடன் ஒருங்கிணைந்து சிறந்த கண்காணிப்புக்காக சரிவுகளை மற்றும் அளவுகோல்களை வழங்குகிறது.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # ஒரு செயல் செய்யவும்
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### பணிமுறை

MAF பணிமுறைகள் என்பது ஒரு பணியை முடிக்க முன்கூட்டியே வரையறுக்கப்பட்ட படிகள், அதில் AI முகவர்கள் அந்த படிகளில் கூறுகளாக உள்ளனர்.

பணிமுறைகள் கண்டிப்பான கட்டுப்பாடுகளை வழங்கும் பல கூறுக்களைக் கொண்டுள்ளன. பணிமுறைகள் **பல முகவர்களுக்கான ஒருங்கிணைப்பு** மற்றும் **நிலைவிடம் சேமிப்பு** மேற்கொள்ளலாம்.

பணிமுறையின் முக்கிய கூறுகள்:

**நிர்வாகிகள்**

நிர்வாகிகள் உள்ளீட்டு செய்திகளை பெற்று, அவற்றுக்கு பணிகளைச் செய்து, வெளியீட்டு செய்திகளை வெளியிடுகின்றனர். இது குழு பணியை முன்னேற்றும். நிர்வாகிகள் AI முகவர் அல்லது தனிப்பயன் தர்க்கம் இருக்கலாம்.

**நிழல்கள்**

நிழல்கள் என்பது பணிமுறையிலான செய்திகளின் ஓட்டத்தை வரையறுக்க பயன்படுத்தப்படுகிறது. இவை:

*நேரடி நிழல்கள்* - நிர்வாகிகளுக்கு இடையேயான எளிய ஒருமுறை இணைப்புகள்:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*நிபந்தனை நிழல்கள்* - சில நிபந்தனை பூரிக்கப்பட்டதும் செயல்படும். உதா: ஹோட்டல் அறைகள் கிடைக்கவில்லை என்றால், நிர்வாகி மற்ற விருப்பங்களை பரிந்துரைக்கும்.

*வெளியீடு-நுழைவு (Switch-case) நிழல்கள்* - நிபந்தனைகளின் அடிப்படையில் நிர்வாகிகளுக்கு செய்திகளை வழிநடத்தும். உதா: பயண வாடிக்கையாளர் முன்னுரிமை அணுகல் உள்ளதென்றால், அவர்களின் பணிகள் வேறு பணிமுறையின் வழியாக கையாளப்படும்.

*பகிர்-பதிக்கு (Fan-out) நிழல்கள்* - ஒரு செய்தியை பல இலக்க들에게 அனுப்பும்.

*சேகரி-இன (Fan-in) நிழல்கள்* - பல நிர்வாகிகளிடமிருந்தும் செய்திகளைச் கூடி ஒரு இலக்குக்கு அனுப்பும்.

**நிகழ்வுகள்**

பணிமுறைகளில் சிறந்த காணுதலாக்கத்துக்காக, MAF கட்டமைக்கப்பட்ட நிகழ்வுகளை வழங்குகிறது, இதில்:

- `WorkflowStartedEvent`  - பணிமுறை செயல்பாடு துவங்கியது
- `WorkflowOutputEvent` - பணிமுறை வெளியீடு தந்தது
- `WorkflowErrorEvent` - பணிமுறையில் பிழை ஏற்பட்டது
- `ExecutorInvokeEvent`  - நிர்வாகி செயல்படத் துவங்கியது
- `ExecutorCompleteEvent`  -  நிர்வாகி செயல்பாட்டை முடித்தது
- `RequestInfoEvent` - கோரிக்கை வெளியிடப்பட்டது

## பிற கட்டமைப்புகளிலிருந்து நகர்தல் (Semantic Kernel மற்றும் AutoGen)

### MAF மற்றும் Semantic Kernel இடையிலான வேறுபாடுகள்

**எளிமையாக்கப்பட்ட முகவர் உருவாக்கம்**

Semantic Kernel ஒவ்வொரு முகவருக்கும் Kernel இன்ஸ்டன்ஸ் உருவாக்கப் பொருந்தும். MAF முக்கிய வழங்குனர்களுக்கான நீட்சிகளைக் கொண்டு எளிமைப்படுத்திய அணுகுதலை பயன்படுத்துகிறது.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**முகவர் திரெட் உருவாக்கம்**

Semantic Kernel இல் திரெட்கள் கையால் உருவாக்கப்பட வேண்டும். MAF இல், முகவருக்கு நேரடியாக ஒரு திரெட் ஒதுக்கப்படுகிறது.

```python
thread = agent.get_new_thread() # தாவலைப் பயன்படுத்தி முகவரியை இயக்கவும்.
```

**கருவி பதிவு**

Semantic Kernel இல், கருவிகள் Kernel இற்கு பதிவு செய்யப்படுகிறார்கள், பின்னர் Kernel முகவருக்கு வழங்கப்படுகிறான். MAF இல், கருவிகள் முகவர் உருவாக்கும் நேரத்தில் நேரடியாக பதிவு செய்யப்படுகின்றன.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF மற்றும் AutoGen இடையிலான வேறுபாடுகள்

**குழுக்கள் vs பணிமுறைகள்**

`குழுக்கள்` AutoGen இல் நிகழ்வு இயக்கப்படும் செயலில் முகவர்களுடன் நடந்துகொள்ளும் நிகழ்வு கட்டமைப்பாகும். MAF `பணிமுறைகள்` என்ற கிராஃப் வழ்ந்த கட்டமைப்பில் நிர்வாகிகளுக்கு தரவு சென்று செயல்படும்.

**கருவி உருவாக்கம்**

AutoGen `FunctionTool` ஐ முகவர்கள் அழைக்கும் செயல்பாடுகளை ஊட்டமாகப் பயன்படுத்துகிறது. MAF @ai_function ஐப் பயன்படுத்து, இது ஒத்த செயல்பாடு கொண்டது மற்றும் ஒவ்வொரு செயல்பாட்டிற்கும் திட்டமிடல்களை தன்னிச்சையாக வரையறுக்கிறது.

**முகவர் நடத்தை**

AutoGen இல் முகவர்கள் இயல்பாக ஒன்று முறை செயற்படுவர்கள், அப்படியல்லெனில் `max_tool_iterations` அதிகமிட்டால். MAF இல் `ChatAgent` இயல்பாக பல முறை முகவர், அதாவது பயனர் பணிகள் முடிந்தவரை கருவிகளை அழைத்து நிறைவேற்றுகிறது.

## குறியீட்டு எடுத்துக்காட்டுகள்

Microsoft முகவர் கட்டமைப்புக்கான குறியீட்டு எடுத்துக்காட்டுகள் இந்த கோப்பு தொகுப்பில் `xx-python-agent-framework` மற்றும் `xx-dotnet-agent-framework` கோப்புகளின் கீழ் உள்ளன.

## Microsoft முகவர் கட்டமைப்பின் பற்றிய கூடுதல் கேள்விகள் உள்ளதா?

மற்ற கற்றுக்கொள்ளுவோருடன் சந்திக்க, அலுவலக நேரங்களில் கலந்துகொள்ள மற்றும் உங்கள் AI முகவர் தொடர்பான கேள்விகளுக்கு பதில் பெற [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) இல் சேரவும்.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**எச்சரிக்கை**:  
இந்த ஆவணம் AI மொழிபெயர்ப்பு சேவை [Co-op Translator](https://github.com/Azure/co-op-translator) மூலம் மொழிபெயர்க்கப்பட்டுள்ளது. துல்லியத்திற்காக நாம் முயலுகிறதாலும், தானியங்கி மொழிபெயர்ப்புகளில் தவறுகள் அல்லது தவறான புரிதல்கள் இருக்கலாம் என்பதற்கு கவனமாக இருங்கள். உள்ளடக்கத்தின் அசல் ஆவணம் அதன் சொந்த மொழியில் அதிகாரப்பூர்வ மூலமாக கருதப்பட வேண்டும். முக்கிய தகவல்களுக்கு, தொழில்முறை மனித மொழிபெயர்ப்பு பரிந்துரைக்கப்படுகிறது. இந்த மொழிபெயர்ப்பைப் பயன்படுத்தியதால் ஏற்படும் எந்த தவறான புரிதல் அல்லது தவறான விளக்கங்களுக்கும் நாங்கள் பொறுப்பு ஏற்கமாட்டோம்.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->