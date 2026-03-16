# Microsoft Agent Framework ကို စူးစမ်းလေ့လာခြင်း

![Agent Framework](../../../translated_images/my/lesson-14-thumbnail.90df0065b9d234ee.webp)

### နိဒါန်း

ဒီသင်ခန်းစာတွင်ပါဝင်သောအကြောင်းအရာများမှာ -

- Microsoft Agent Framework ကိုနားလည်ခြင်း - အဓိက အင်္ဂါရပ်များနှင့် တန်ဖိုးများ  
- Microsoft Agent Framework ၏ အဓိက အယူအဆများကို စူးစမ်းလေ့လာခြင်း
- MAF နှင့် Semantic Kernel နှင့် AutoGen တို့ကို နှိုင်းယှဉ်ခြင်း - ပြောင်းရွှေ့ရန် လမ်းညွှန်ချက်

## သင်ယူရမည့် ရည်မှန်းချက်များ

ဒီသင်ခန်းစာပြီးမြောက်အပြီးတွင် သင်သည် -

- Microsoft Agent Framework အသုံးပြု၍ ထုတ်လုပ်မှု အဆင်သင့် AI Agent များ တည်ဆောက်နည်းကို သိရှိနိုင်မည်။
- Microsoft Agent Framework ၏ အဓိက အင်္ဂါရပ်များကို သင့် Agentic အသုံးပြုမှုကိစ္စများတွင် လျှောက်ထားနည်းကို သိရှိနိုင်မည်။
- ရှိပြီးသား Agentic framework များနှင့် ကိရိယာများကို ပြောင်းရွှေ့၍ ပေါင်းစည်းအသုံးပြုနည်းကို သိရှိနိုင်မည်။

## ကုဒ် နမူနာများ

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) အတွက် ကုဒ်နမူနာများကို ဤ repository ၏ `xx-python-agent-framework` နှင့် `xx-dotnet-agent-framework` ဖိုင်များအောက်တွင်တွေ့ရှိနိုင်သည်။

## Microsoft Agent Framework ကို နားလည်ခြင်း

![Framework Intro](../../../translated_images/my/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) သည် Semantic Kernel နှင့် AutoGen မှ အတွေ့အကြုံနှင့် သင်ယူမှုများအပေါ် ပေါ်ပြူလာပြီး တိုးချဲ့ထားသည်။ ထိုကဲ့သို့သော Agentic အသုံးပြုမှုများစွာကို ထိန်းသိမ်းနိုင်စေရန်အတွက် အလွန်ပြောင်းလွယ်ပြင်လွယ် ရည်ရွယ်ချက်ပါဝင်သည်။ ထိုတစ်ခုချင်းစီမှာ -

- အဆင့်လိုက် Agent အဆင့်မမြင့်ဖွဲ့စည်းမှု (Sequential Agent orchestration) - လုပ်ငန်းစဉ် ခြေလှမ်းလိုက် လုပ်ငန်းစဉ်များ ရှိသော နေရာများတွင်။
- တစ်ပြိုင်နက်တည်း လုပ်ငန်းများ ပြီးမြောက်စေရန် Agent များအပြိုင်အဆိုင် လုပ်ဆောင်ရန် လိုအပ်သော နေရာများတွင် Concurrent orchestration။
- Group chat orchestration - Agent များသည် အတူတကွ တစ်ခုတည်းသော လုပ်ငန်းကို ပူးပေါင်းဆောင်ရွက်နိုင်သော နေရာများတွင်။
- Handoff Orchestration - Subtask အပိုင်းများ ပြီးမြောက်သည့်အခါ Agent များသည် တစ်ဦးမှ တစ်ဦးသို့ လုပ်ငန်းကို လွှဲပြောင်းပေးသည့် အခြေအနေများတွင်။
- Magnetic Orchestration - မန်နေဂျာ Agent သည် လုပ်ငန်းစာရင်းတစ်ခုကို ဖန်တီး၊ ပြင်ဆင်ပြီး Subagent များကို စုပေါင်းညှိနှိုင်းကာ လုပ်ငန်းပြီးမြောက်အောင်လုပ်ဆောင်သည့် နေရာများတွင်။

ထုတ်လုပ်မှုတွင် AI Agent များ ပေးပို့ဖို့အတွက် MAF တွင် အောက်ပါ အင်္ဂါရပ်များပါဝင်သည် -

- OpenTelemetry အသုံးပြုခြင်းမှ Observability - AI Agent ၏ လုပ်ဆောင်ချက်များ၊ ကျယ်ပြန့်ပြီးတိကျသော tool ခေါ်ဆိုမှုများ၊ orchestration ခြေလှမ်းများ၊ ချဉ်းကပ်လမ်းကြောင်းများနှင့် Microsoft Foundry က ဒိုင်ရှ်ဘုတ် တွင် ကြည့်ရှုမှုဆိုင်ရာ စောင့်ကြည်မှုများ။
- Security - Microsoft Foundry တွင် တိုက်ရိုက် Agent များကို စီမံခြင်းဖြင့် အခန်းကဏ္ဍ အကောင့်ထိန်းချုပ်မှု၊ ကိုယ်ပိုင်ဒေတာ ကိုင်တွယ်မှုနှင့် အထောက်အထား ရှိသော မူဝါဒများပါဝင်။
- Durability - Agent thread များနှင့် workflow များအား ရပ်ဆိုင်း/ပြန်စတင်/အမှားကင်းကျော်ဖို့ အားပေးနိုင်ခြင်း၊ ရေရှည် လည်ပတ်မှုအတွက်။
- Control - လူ့လက်ထိန်းလှုပ်ရှားမှု ပါဝင်မှုကို ထောက်ပံ့ပေးပြီး လုပ်ငန်းများကို လူ့အတည်ပြုချက်လိုသည်ဟု မှတ်သားနိုင်ခြင်း။

Microsoft Agent Framework ၏ တခြား အထူးကောင်းမွန်ချက်များ

- Cloud-agnostic ဖြစ်ခြင်း - Agent များကို container များတွင်၊ on-premises တွင်၊ နှင့် cloud အမျိုးမျိုးတွင် လည်ပတ်နိုင်သည်။
- Provider-agnostic ဖြစ်ခြင်း - Azure OpenAI နှင့် OpenAI စတဲ့ သင့်အကြိုက် SDK များမှ ဖန်တီးနိုင်သည်။
- Open Standards ဗဟိုပြုခြင်း - Agent-to-Agent (A2A) နှင့် Model Context Protocol (MCP) စသည်ဖြင့် အခြား Agent များနှင့် ကိရိယာများ ရှာဖွေနိုင်သည်။
- Plugins နှင့် Connectors - Microsoft Fabric, SharePoint, Pinecone, Qdrant ကဲ့သို့ ဒေတာနှင့် စွမ်းရည် အထောက်အပံ့ဝန်ဆောင်မှုများနှင့် ချိတ်ဆက်မှု။

Microsoft Agent Framework ၏ အဓိက အယူအဆများကို အသုံးပြုရာတွင်၊ ၎င်း၏အင်္ဂါရပ်များအပေါ် မည်သို့ အသုံးပြုထားသည်ကို ကြည့်ကြရအောင်။

## Microsoft Agent Framework ၏ အဓိက အယူအဆများ

### Agents

![Agent Framework](../../../translated_images/my/agent-components.410a06daf87b4fef.webp)

**Agent များဖန်တီးခြင်း**

Agent ဖန်တီးခြင်းသည် inference service (LLM Provider) ကို သတ်မှတ်ခြင်း၊ AI Agent မလိုက်နာရမည့် အမိန့် များ စုစည်းခြင်း၊ နှင့် သတ်မှတ်ထားသော `name` တစ်ခု ချမှတ်ခြင်းဖြင့် ပြုလုပ်ပါသည်။

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

အထက်ပါ နမူနာတွင် `Azure OpenAI` ကို အသုံးပြုထားသော်လည်း `Microsoft Foundry Agent Service` ကဲ့သို့ ဝန်ဆောင်မှု များစွာဖြင့် Agent များ ဖန်တီးနိုင်သည်။

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI ၏ `Responses`၊ `ChatCompletion` API များ

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

သို့မဟုတ် A2A protocol ကိုသုံးပြီး အဝေးအကြောင်းကြား Agent များ ဖန်တီးနိုင်သည် -

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Agent များ လည်ပတ်ခြင်း**

Agent များသည် `.run` သို့မဟုတ် `.run_stream` နည်းလမ်းဖြင့်၊ စီးဆင်းမှုမရှိသော (non-streaming) သို့မဟုတ် စီးဆင်းမှုရှိသော (streaming) တုံ့ပြန်မှုများအတွက် လည်ပတ်သည်။

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Agent တစ်ခုချင်း run များတွင် `max_tokens` စသည်ဖြင့် Agent အသုံးပြုသော parameter များ၊ Agent က ခေါ်ယူနိုင်သော `tools` များ၊ နှင့် Agent အတွက် အသုံးပြုသော `model` ကို စိတ်ကြိုက်ပြင်ဆင်နိုင်သည်။

အားလုံး user ၏ လုပ်ငန်းကို ပြီးမြောက်စေရန် အထူးလိုသော model များ သို့မဟုတ် tool များ လိုအပ်ပါက အထူးအသုံးဝင်သည်။

**Tools**

Tools များကို Agent ဖန်တီးသည့်အချိန်၌ သတ်မှတ်နိုင်သည်။

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# ChatAgent ကို တိုက်ရိုက် ဖန်တီးသောအခါ

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

Agent ကို run ပြုလုပ်သည့်အချိန်တွင်လည်း သတ်မှတ်နိုင်သည်။

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # ဒီအပြေးအတွက်သာ ပေးထားသော ကိရိယာဖြစ်သည် )
```

**Agent Threads**

Agent Threads သည် မကြာခဏစကားဝိုင်းဆွေးနွေးမှု multi-turn ကို ကိုင်တွယ်ရန်အသုံးပြုသည်။ Thread များကို

- `get_new_thread()` ကို အသုံးပြု၍ အချိန်ကြာမြင့်စွာ သိမ်းဆည်းနိုင်သည်။
- Agent run ပြုလုပ်သည့်အချိန်တွင် ဖန်တီးလည်း ရပြီး ယခု run အတွင်းသာ Thread ရှိသေးသည်။

Thread ဖန်တီးရန်ကုဒ်ပုံစံမှာ -

```python
# လမ်းကြောင်းအသစ်တစ်ခု ဖန်တီးပါ။
thread = agent.get_new_thread() # လမ်းကြောင်းနှင့်အတူ အေးဂျင့်ကို ပြေးပါ။
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

ပြီးတော့ သိုလှောင်ရန် Thread ကို serialize ပြုလုပ်နိုင်သည်။

```python
# သစ်တစ်ခုသော thread ကို ဖန်တီးပါ။
thread = agent.get_new_thread() 

# Thread နှင့်အတူ agent ကို လုပ်ဆောင်ပါ။

response = await agent.run("Hello, how are you?", thread=thread) 

# သိုလှောင်မှုအတွက် thread ကို စီးရီးလိုက်ပုံသွင်းပါ။

serialized_thread = await thread.serialize() 

# သိုလှောင်နေရာမှ load ပြန်ပြီးနောက် thread အခြေအနေကို ပြန်လည် ခွဲထုတ်ပါ။

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent Middleware**

Agent များသည် user ၏လုပ်ငန်းများ ပြည့်စုံစွာ ဖော်ဆောင်ရန် tool များနှင့် LLM များနှင့် ဆက်ဆံပါသည်။ အချို့အခြေအနေများတွင် အကြားရေးဆက်ဆံမှုများကို လုပ်ဆောင်လိုသောအခါ Agent middleware သည် အောက်ပါ အလားအလာများရရှိစေသည် -

*Function Middleware*

Agent နှင့် function/tool ခေါ်ဆိုမှုအကြား လုပ်ဆောင်ချက်တစ်ခု ယူနိုင်ရန် middleware ဖြစ်သည်။ ဥပမာ အဲ့ဒါက function ခေါ်ဆိုမှုတွင် logging ကို လုပ်လိုသောအခါအသုံးဝင်နိုင်သည်။

ကုဒ်တွင် `next` သည် နောက်တစ် middleware သို့မဟုတ် function ကို ခေါ်ရန်ဖြစ်သည်။

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # ကြိုတင်လုပ်ဆောင်ခြင်း - လုပ်ဆောင်မှုစတင်မှုမတိုင်မှီ မှတ်တမ်းတင်ခြင်း
    print(f"[Function] Calling {context.function.name}")

    # နောက်ထပ် middleware သို့မဟုတ် လုပ်ဆောင်မှုဆက်လုပ်ရန် ဆက်လုပ်ခြင်း
    await next(context)

    # ပြီးဆုံးပြီးနောက် လုပ်ဆောင်မှုမှတ်တမ်းတင်ခြင်း
    print(f"[Function] {context.function.name} completed")
```

*Chat Middleware*

Agent နှင့် LLM တွေ့ဆုံမှုများအကြား လုပ်ဆောင်မှု သို့မဟုတ် logging လုပ်ရန် middleware ဖြစ်သည်။

AI ဝန်ဆောင်မှုသို့ ပေးပို့မည့် `messages` အကြောင်း အရေးကြီးသတင်းအချက်အလက်များပါဝင်သည်။

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # ကြိုတင်လုပ်ဆောင်ခြင်း: AI ခေါ်ဆိုမှုမပြုမီ မှတ်တမ်းတင်ခြင်း
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # နောက်ထပ် middleware သို့မဟုတ် AI ဝန်ဆောင်မှုသို့ ဆက်လက်လုပ်ဆောင်ရန်
    await next(context)

    # ပြီးဆုံးပြီးနောက်လုပ်ဆောင်ခြင်း: AI တုံ့ပြန်ချက်ရပြီးမှ မှတ်တမ်းတင်ခြင်း
    print("[Chat] AI response received")

```

**Agent Memory**

`Agentic Memory` သင်ခန်းစာတွင်ဖော်ပြသည့်အတိုင်း Memory သည် Agent ကို မတူညီသော Context များတွင် လည်ပတ်နိုင်စေရန် အရေးကြီးသည်။ MAF တွင် အမျိုးမျိုးသော Memory အမျိုးအစားများ ရှိသည် -

*In-Memory Storage*

ဤ memory သည် application runtime အတွင်း thread များ၏ အတွင်းရှိ သိုလှောင်မှုဖြစ်သည်။

```python
# အိုက်ကောအသစ်တစ်ခုဖန်တီးပါ။
thread = agent.get_new_thread() # အိုက်ကောနှင့်အတူအေးဂျင့်ကိုပြန်လည်ဆောင်ရွက်ပါ။
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Persistent Messages*

ဤ memory သည် မတူညီသော Sessions များမှ ကိစ္စရပ် သမိုင်းတမ်းများ သိမ်းဆည်းရာတွင် အသုံးပြုသည်။ `chat_message_store_factory` ဖြင့် သတ်မှတ်ထားသည် -

```python
from agent_framework import ChatMessageStore

# ကိုယ်ပိုင်စာသားသိုလှောင်ရာဆိုင်ကို တည်ဆောက်ပါ
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamic Memory*

ဤ memory ကို Agent များ run မတိုင်ခင် Context ထဲ သို့ ထည့်သွင်းသည်။ ဤ memory များကို mem0 ကဲ့သို့သော ပြင်ပဝန်ဆောင်မှုများတွင် သိမ်းဆည်းနိုင်သည် -

```python
from agent_framework.mem0 import Mem0Provider

# အဆင့်မြင့်မှတ်ဉာဏ်စွမ်းရည်များအတွက် Mem0 ကို အသုံးပြုခြင်း
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

**Agent Observability**

Observability သည် ယုံကြည်စိတ်ချမှုရှိသော၊ စောင့်ရှောက်မှု ရှိသော Agentic စနစ်များ တည်ဆောက်ရာတွင် အလွန်အရေးကြီးသည်။ MAF သည် OpenTelemetry နှင့် ပေါင်းစည်းကာ ကောင်းမွန်သော tracing နှင့် meter များ ထောက်ပံ့သည်။

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # အလုပ်တစ်ခုလုပ်ပါ
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Workflows

MAF သည် တစ်ခုတည်းသော လုပ်ငန်းအပိုင်းကို ပြီးမြောက်စေသော အဆင့်လိုက် ခြေလှမ်းများဖြင့် သတ်မှတ်ထားသော Workflows များ ပေးသည်။ AI Agent များကို အစိတ်အပိုင်းများအဖြစ် ထည့်သွင်းထားသည်။

Workflow များတွင် ဦးတည်ချက်ထိန်းချုပ်မှု အကောင်းဆုံး ဖွဲ့စည်းပုံများပါဝင်ပြီး, **Multi-agent orchestration** နှင့် **checkpointing** ကို ပြုလုပ်ကာ workflow အခြေအနေများ သိမ်းဆည်းပေးသည်။

Workflow ၏ အဓိက အစိတ်အပိုင်းများမှာ -

**Executors**

Executors သည် input messages များကို လက်ခံ၊ တာဝန်ပေးထားသောလုပ်ငန်းများ ပြုလုပ်ပြီး output message များ ထုတ်ပေးသည်။ ၎င်းက workflow ကို ရွေ့လျားစေပြီး လုပ်ငန်းကြီး ပြီးမြောက်အောင် ဆောင်ရွက်သည်။ Executors များသည် AI Agent သို့မဟုတ် စိတ်ကြိုက် Logic ဖြစ်နိုင်သည်။

**Edges**

Edges များသည် Workflow ထဲတွင် messages ၏ လည်ပတ်မှု လမ်းကြောင်းကို သတ်မှတ်ရာတွင် အသုံးပြုသည်။ ၎င်းက အမျိုးမျိုးရှိသည် -

*Direct Edges* - Executor နှစ်ခုကြား တစ်ချက်ချင်း ချိတ်ဆက်မှု -

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Conditional Edges* - သတ်မှတ်ထားသော မူဝါဒဖြင့် အသက်ဝင်သည်။ ဥပမာ - ဟိုတယ်အခန်း မရရှိနိုင်တော့ဘူးဆိုလျှင် မတူညီသောရွေးချယ်စရာများကို executor က စီစဉ်နိုင်သည်။

*Switch-case Edges* - သတ်မှတ်ထားသော မူဝါဒများအပေါ် အခြေခံကာ မက်ဆေ့ခ်ျများကို executor များသို့ လမ်းညွှန်သည်။ ဥပမာ - ခရီးသွားဖောက်သည်သည် ဦးစားပေးအောက်ခံဖြစ်လျှင် သူ၏လုပ်ငန်းများကို တခြား workflow ဖြင့်ဆောင်ရွက်ပေးသည်။

*Fan-out Edges* - တစ်ခုသော မက်ဆေ့ခ်ျကို လက်ခံသူများစွာသို့ ပေးပို့သည်။

*Fan-in Edges* - အမျိုးမျိုးသော Executor များမှ မက်ဆေ့ခ်ျများစုပေါင်းပြီး တစ်ခုသော လက်ခံသူသို့ ပေးပို့သည်။

**Events**

Workflow များ၏ observability ပိုမိုကောင်းမွန်စေရန် MAFသည် workflow ကိစ္စအတွက် အောက်ပါ built-in အဖြစ်သော events များ ပေးသည် -

- `WorkflowStartedEvent` - Workflow လည်ပတ်မှု စတင်သည်
- `WorkflowOutputEvent` - Workflow မှ output ထွက်လာသည်
- `WorkflowErrorEvent` - Workflow သည် အမှားတစ်ခု ကြုံတွေ့သည်
- `ExecutorInvokeEvent` - Executor သည် လုပ်ငန်းစတင်သည်
- `ExecutorCompleteEvent` - Executor သည် လုပ်ငန်းပြီးဆုံးသည်
- `RequestInfoEvent` - တောင်းဆိုမှု တစ်ခု ထုတ်လွှင့်သည်

## အခြား Framework များ (Semantic Kernel နှင့် AutoGen) မှ ပြောင်းရွှေ့ခြင်း

### MAF နှင့် Semantic Kernel ၏ ကွာခြားချက်များ

**Agent ဖန်တီးခြင်း လွယ်ကူခြင်း**

Semantic Kernel သည် Agent တစ်ခုစီအတွက် Kernel instance တစ်ခုဖန်တီးရန် လိုအပ်သည်။ MAF သည် အဓိက provider များအတွက် extension များ အသုံးပြုသည့် လွယ်ကူသောနည်းလမ်းဖြင့် ဖြေရှင်းသည်။

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Agent Thread ဖန်တီးခြင်း**

Semantic Kernel တွင် Thread များကို ကိုယ်တိုင် ဖန်တီးရသောနေရာ၊ MAF တွင် Agent ကို တိုက်ရိုက် Thread တစ်ခု ချမှတ်ပေးသည်။

```python
thread = agent.get_new_thread() # အေးဂျင့်ကို ထရက်နှင့်အတူ လည်ပတ်ပါ။
```

**Tool မှတ်ပုံတင်ခြင်း**

Semantic Kernel မှာ Tools များကို Kernel သို့မှတ်ပုံတင်ပြီး Kernel ကို Agent သို့ ပို့ပေးသည်။ MAF မှာ Tools များကို Agent ဖန်တီးသည့်အချိန်မှာ တိုက်ရိုက် မှတ်ပုံတင်သည်။

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF နှင့် AutoGen ၏ ကွာခြားချက်များ

**Teams နှင့် Workflows**

`Teams` သည် event ဒရိုင်ဗ်လုပ်ငန်းစဉ်များအတွက် AutoGen တွင် လုပ်ဆောင်ပုံစံဖြစ်သည်။ MAF သည် data များကို graph architecture အားဖြင့် executor များသို့ လမ်းညွှန်ပေးသော `Workflows` ကို အသုံးပြုသည်။

**Tool ဖန်တီးခြင်း**

AutoGen သည် `FunctionTool` ကို အသုံးပြုပြီး Agent များအတွက် function များကို ဝေါဟာရ ပုံသဏ္ဍာန်ချပေးသည်။ MAF သည် @ai_function ကို အသုံးပြုသည်။ ၎င်းသည် schema များကို အလိုအလျောက် ရွေးချယ်ပေးသည်။

**Agent လုပ်ဆောင်ပုံ**

AutoGen တွင် Agent များမှာ သာမာန်အားဖြင့် single-turn ဖြစ်သော်လည်း `max_tool_iterations` ကို မြင့်မားစေပါက မတူသည်။ MAF တွင် `ChatAgent` သည် multi-turn ဖြစ်ပြီး user ၏ လုပ်ငန်း ပြီးမြောက်သည်ထိ tool များ ကို ခေါ်ဆောင်ကြဉ်းနေသည်။

## ကုဒ်နမူနာများ

Microsoft Agent Framework အတွက် ကုဒ်နမူနာများကို ဤ repository ၏ `xx-python-agent-framework` နှင့် `xx-dotnet-agent-framework` ဖိုင်များအောက်တွင် တွေ့ရှိနိုင်သည်။

## Microsoft Agent Framework အကြောင်း ပိုမိုမေးမြန်းလိုပါက?

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) တွင် ဝင်ရောက်ပြီး ကျောင်းသားများနှင့် တွေ့ဆုံနိုင်၊ office hours များတက်ရောက်နိုင်ပြီး သင့်၏ AI Agent မေးခွန်းများကို ဖြေကြားပေးပါလိမ့်မည်။

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免责声明**:
အဆိုပါစာတမ်းကို AI ဘာသာပြန်စနစ် [Co-op Translator](https://github.com/Azure/co-op-translator) အသုံးပြုပြီး ဘာသာပြန်ထားပါသည်။ တိကျမှုအာမခံရန်ကြိုးစားပေမယ့် အလိုအလျောက်ဘာသာပြန်ထားမှုတွင် မှားယွင်းချက်များ သို့မဟုတ် မမှန်ကန်မှုများ ရှိနိုင်ကြောင်း အသိပေးလိုပါသည်။ မူလစာတမ်းကို မိသားစကားဖြင့်သာ ယုံကြည်စိတ်ချရသောအရင်းအမြစ်အဖြစ်ယူဆသင့်ပါသည်။ အရေးကြီးသည့်အချက်အလက်များအတွက် အသက်မဲ့လူသားဘာသာပြန်မှုကို အကြံပြုသည်။ ဤဘာသာပြန်မှု အသုံးပြုမှုကြောင့် ဖြစ်ပေါ်သော နားမလည်မှုများ သို့မဟုတ် မှားယွင်းဖွင့်ဆိုမှုများအတွက် ကျွန်ုပ်တို့သည် တာဝန်မေပေးပါ။
<!-- CO-OP TRANSLATOR DISCLAIMER END -->