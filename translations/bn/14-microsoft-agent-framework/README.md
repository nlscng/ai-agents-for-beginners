# মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্ক অনুসন্ধান

![Agent Framework](../../../translated_images/bn/lesson-14-thumbnail.90df0065b9d234ee.webp)

### পরিচিতি

এই পাঠে আলোচনা করা হবে:

- মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্ক বোঝা: প্রধান বৈশিষ্ট্য এবং মূল্য  
- মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্কের মূল ধারণাগুলো অনুসন্ধান করা
- MAF বনাম Semantic Kernel এবং AutoGen তুলনা: মাইগ্রেশন গাইড

## শেখার লক্ষ্য

এই পাঠ সম্পূর্ণ করার পর, আপনি জানবেন কীভাবে:

- মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্ক ব্যবহার করে প্রোডাকশন প্রস্তুত AI এজেন্ট তৈরি করবেন
- মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্কের মূল বৈশিষ্ট্যগুলো আপনার এজেন্টিক ইউজ কেসে প্রয়োগ করবেন
- বিদ্যমান এজেন্টিক ফ্রেমওয়ার্ক এবং টুলস মাইগ্রেট ও ইন্টিগ্রেট করবেন  

## কোড নমুনা

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok)-এর জন্য কোড নমুনা এই রিপোজিটরির `xx-python-agent-framework` এবং `xx-dotnet-agent-framework` ফাইলের মধ্যে পাওয়া যাবে।

## মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্ক বোঝা

![Framework Intro](../../../translated_images/bn/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) Semantic Kernel এবং AutoGen থেকে প্রাপ্ত অভিজ্ঞতা এবং শেখার উপর ভিত্তি করে তৈরি। এটি বিভিন্ন প্রোডাকশন এবং গবেষণা পরিবেশে দেখা এজেন্টিক ইউজ কেসগুলো মোকাবেলা করার জন্য নমনীয়তা প্রদান করে, যার মধ্যে রয়েছে:

- **ক্রমবর্ধমান এজেন্ট অর্কেস্ট্রেশন** যেখানে ধাপে ধাপে ওয়ার্কফ্লো প্রয়োজন হয়।
- **সমান্তরাল অর্কেস্ট্রেশন** যেখানে এজেন্টদের একই সময়ে কাজগুলো সম্পন্ন করতে হয়।
- **গ্রুপ চ্যাট অর্কেস্ট্রেশন** যেখানে একযোগে এজেন্টরা একটি কাজ নিয়ে সহযোগিতা করে।
- **হ্যান্ডঅফ অর্কেস্ট্রেশন** যেখানে এজেন্টরা সাবটাস্ক সম্পন্ন হওয়ার পর কাজ পরস্পরের মাঝে হস্তান্তর করে।
- **ম্যাগনেটিক অর্কেস্ট্রেশন** যেখানে একটি ম্যানেজার এজেন্ট কাজের তালিকা তৈরি, পরিবর্তন করে এবং সাবএজেন্টদের সমন্বয় করে কাজ শেষ করে।

প্রোডাকশনে AI এজেন্ট সরবরাহের জন্য, MAF এর মধ্যে রয়েছে:

- **অবজারভেবিলিটি** OpenTelemetry ব্যবহার করে যেখানে AI এজেন্টের প্রতিটি কাজ যেমন টুল আহ্বান, অর্কেস্ট্রেশন ধাপ, রিজনিং ফ্লো এবং পারফরম্যান্স মনিটরিং মাইক্রোসফট ফাউন্ড্রি ড্যাশবোর্ডের মাধ্যমে দেখা যায়।
- **নিরাপত্তা** মাইক্রোসফট ফাউন্ড্রির নেটিভ হোস্টিংয়ের মাধ্যমে, যেখানে রোল-বেস্ট অ্যাক্সেস, প্রাইভেট ডেটা হ্যান্ডলিং এবং বিল্ট-ইন কন্টেন্ট সেফটি রয়েছে।
- **টেকসইপনা** কারণ Agent থ্রেড এবং ওয়ার্কফ্লো পজ, রিসিউম ও এরর থেকে রিকভার করতে পারে যা দীর্ঘমেয়াদি প্রসেস সক্ষম করে।
- **নিয়ন্ত্রণ** কারণ মানব সমর্থিত ওয়ার্কফ্লো সমর্থিত যেখানে কাজগুলো মানব অনুমোদন দাবী করে চিহ্নিত হয়।

মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্ক ইন্টারঅপারেবল হওয়ার উপরও গুরুত্ব আরোপ করে যেমন:

- **ক্লাউড-নিরপেক্ষ** - এজেন্টগুলি কন্টেইনার, অন-প্রিম এবং বিভিন্ন ক্লাউডে চালানো যেতে পারে।
- **প্রোভাইডার-নিরপেক্ষ** - এজেন্ট আপনার পছন্দের SDK যেমন Azure OpenAI এবং OpenAI দিয়ে তৈরি করা যায়।
- **ওপেন স্ট্যান্ডার্ড ইন্টিগ্রেশন** - Agent-to-Agent (A2A) এবং Model Context Protocol (MCP) মতো প্রোটোকল ব্যবহার করে অন্য এজেন্ট ও টুল সন্ধান ও ব্যবহার করতে পারে।
- **প্লাগইন ও কানেক্টর** - মাইক্রোসফট ফ্যাব্রিক, শেয়ারপয়েন্ট, পাইনকোন এবং Qdrant এর মতো ডাটা ও মেমোরি সার্ভিসের সাথে কানেকশন করা যায়।

চলুন দেখে নিই কীভাবে এই বৈশিষ্ট্যগুলো মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্কের কিছু মূল ধারণায় প্রয়োগ করা হয়।

## মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্কের মূল ধারণাগুলো

### এজেন্টস

![Agent Framework](../../../translated_images/bn/agent-components.410a06daf87b4fef.webp)

**এজেন্ট তৈরি করা**

এজেন্ট তৈরি হয় ইনফারেন্স সার্ভিস (LLM প্রোভাইডার), AI এজেন্টের জন্য নির্দেশাবলী সেট, এবং একটি নির্ধারিত `name` দিয়ে:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

উপরে `Azure OpenAI` ব্যবহার করা হয়েছে তবে বিভিন্ন সার্ভিস ব্যবহার করে এজেন্ট তৈরি করা যায় যেমন `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` অ্যাপিআই

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

অথবা দূরবর্তী এজেন্টরা A2A প্রোটোকল ব্যবহার করে:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**এজেন্ট চালানো**

`.run` অথবা `.run_stream` মেথড ব্যবহার করে এজেন্ট চালানো হয়, যা নন-স্ট্রিমিং বা স্ট্রিমিং রেসপন্সের জন্য ব্যবহৃত হয়।

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

প্রতিটি এজেন্ট রান কাস্টমাইজ করার জন্য বিকল্প থাকতে পারে যেমন এজেন্টের `max_tokens`, কল করতে পারা `tools`, এমনকি ব্যবহারকৃত `model`।

এটি দরকারী যখন নির্দিষ্ট মডেল বা টুল ব্যবহার করে ইউজারের কাজ সম্পন্ন করতে হয়।

**টুলস**

টুল সংজ্ঞায়িত করা যায় এজেন্ট তৈরির সময়:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# সরাসরি একটি ChatAgent তৈরি করার সময়

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

এবং এজেন্ট চালানোর সময়ও:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # শুধুমাত্র এই রানটির জন্য প্রদানকৃত টুল )
```

**এজেন্ট থ্রেডস**

এজেন্ট থ্রেডগুলো মাল্টি-টার্ন কথোপকথন পরিচালনা করে। থ্রেড তৈরি করা যায়:

- `get_new_thread()` ব্যবহার করে যা সময়ের সাথে থ্রেড সংরক্ষণ করে
- অথবা এজেন্ট চালানোর সময় স্বয়ংক্রিয়ভাবে থ্রেড তৈরি হয় যা কেবল বর্তমান রান চলাকালীন থাকে।

থ্রেড তৈরি করার উদাহরণ:

```python
# একটি নতুন থ্রেড তৈরি করুন।
thread = agent.get_new_thread() # থ্রেডের সাথে এজেন্ট চালান।
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

পরে থ্রেড সিরিয়ালাইজ করে সংরক্ষণ করা যায়:

```python
# একটি নতুন থ্রেড তৈরি করুন।
thread = agent.get_new_thread() 

# থ্রেডের সাথে এজেন্ট চালান।

response = await agent.run("Hello, how are you?", thread=thread) 

# সংরক্ষণের জন্য থ্রেড সিরিয়ালাইজ করুন।

serialized_thread = await thread.serialize() 

# সংরক্ষণের পরে থ্রেডের স্টেট ডেসিরিয়ালাইজ করুন।

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**এজেন্ট মিডলওয়্যার**

এজেন্ট টুল ও LLM এর সাথে ইন্টারঅ্যাক্ট করে ইউজারের কাজ সম্পন্ন করে। কিছু পরিস্থিতিতে আমরা চাই এদের মাঝে কিছু কার্য সম্পাদন বা ট্র্যাক করতে। এজেন্ট মিডলওয়্যার দ্বারা এটি সম্ভব:

*ফাংশন মিডলওয়্যার*

এটি এজেন্ট এবং একটি ফাংশন/টুলের মধ্যে একটি অ্যাকশন এক্সিকিউট করতে দেয়, যেমন ফাংশন কলের লগিং করা।

নিম্নলিখিত কোডে `next` নির্দেশ করে পরবর্তী মিডলওয়্যার বা আসল ফাংশন কল হবে কিনা।

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # প্রি-প্রসেসিং: ফাংশন কার্যন্বয়ের পূর্বে লগ করুন
    print(f"[Function] Calling {context.function.name}")

    # পরবর্তী মিডলওয়্যার বা ফাংশন কার্যন্বয়ে চলুন
    await next(context)

    # পোস্ট-প্রসেসিং: ফাংশন কার্যন্বয়ের পর লগ করুন
    print(f"[Function] {context.function.name} completed")
```

*চ্যাট মিডলওয়্যার*

এটি এজেন্ট এবং LLM এর মধ্যে রিকোয়েস্টের মাঝে একটি অ্যাকশন বা লগ এক্সিকিউট করতে দেয়।

এর মধ্যে গুরুত্বপূর্ণ তথ্য নিয়ে থাকে যেমন AI সার্ভিসে পাঠানো `messages`।

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # প্রিপ্রসেসিং: AI কলের আগে লগ করুন
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # পরবর্তী মিডলওয়্যার বা AI সার্ভিসে যান
    await next(context)

    # পোস্ট-প্রসেসিং: AI প্রতিক্রিয়ার পরে লগ করুন
    print("[Chat] AI response received")

```

**এজেন্ট মেমোরি**

`Agentic Memory` পাঠে আলোচনা করা হয়েছে, মেমোরি এজেন্টকে বিভিন্ন প্রসঙ্গে কাজ করার সুযোগ দেয়। MAF বিভিন্ন ধরনের মেমোরি অফার করে:

*ইন-মেমোরি স্টোরেজ*

অ্যাপ্লিকেশন রানটাইমে থ্রেডে সংরক্ষিত মেমোরি।

```python
# একটি নতুন থ্রেড তৈরি করুন।
thread = agent.get_new_thread() # থ্রেডের সাথে এজেন্ট চালান।
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*পার্সিস্টেন্ট মেসেজ*

এর মাধ্যমে বিভিন্ন সেশনের কথোপকথন ইতিহাস সংরক্ষণ হয়। এটি `chat_message_store_factory` দিয়ে সংজ্ঞায়িত:

```python
from agent_framework import ChatMessageStore

# একটি কাস্টম মেসেজ স্টোর তৈরি করুন
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*ডাইনামিক মেমোরি*

এটি এজেন্ট চলার আগে প্রসঙ্গে যোগ করা হয়। এই মেমোরি বহিঃস্থ সার্ভিস যেমন mem0-তে সংরক্ষণ করা যেতে পারে:

```python
from agent_framework.mem0 import Mem0Provider

# উন্নত মেমোরি ক্ষমতার জন্য Mem0 ব্যবহৃত হচ্ছে
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

**এজেন্ট অবজারভেবিলিটি**

বিশ্বস্ত ও রক্ষণাবেক্ষণযোগ্য এজেন্টিক সিস্টেম গঠনের জন্য অবজারভেবিলিটি গুরুত্বপূর্ণ। MAF OpenTelemetry-র সঙ্গে ইন্টিগ্রেট করে ট্রেসিং এবং মিটার প্রোভাইড করে।

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # কিছু করা
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### ওয়ার্কফ্লো

MAF ওয়ার্কফ্লো অফার করে যা পূর্বনির্ধারিত ধাপসমূহের মাধ্যমে কাজ সম্পন্ন করে এবং AI এজেন্টকে ঐ ধাপের উপাদান হিসেবে অন্তর্ভুক্ত করে।

ওয়ার্কফ্লো বিভিন্ন উপাদান দিয়ে গঠিত যা উন্নত কন্ট্রোল ফ্লো সম্ভব করে। ওয়ার্কফ্লো **মাল্টি-এজেন্ট অর্কেস্ট্রেশন** এবং **চেকপয়েন্টিং** সমর্থন করে যা ওয়ার্কফ্লো স্টেট সংরক্ষণ করে।

ওয়ার্কফ্লোর মূল উপাদান হল:

**এক্সিকিউটরস**

এক্সিকিউটর ইনপুট মেসেজ গ্রহণ করে, নির্ধারিত কাজ সম্পন্ন করে এবং আউটপুট মেসেজ তৈরি করে। এটি বড় কাজের দিকে ওয়ার্কফ্লোকে এগিয়ে নিয়ে যায়। এক্সিকিউটর AI এজেন্ট বা কাস্টম লজিক হতে পারে।

**এজেস**

এজেস মেসেজের প্রবাহ নির্ধারণ করে। এগুলো হতে পারে:

*ডাইরেক্ট এজেস* - এক্সিকিউটরের মধ্যে সরল এক-থেকে-এক সংযোগ:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*কন্ডিশনাল এজেস* - নির্দিষ্ট শর্ত পূরণের পর সক্রিয় হয়। যেমন, যদি হোটেল রুম না থাকে, এক্সিকিউটর অন্য অপশন প্রস্তাব করতে পারে।

*সুইচ-কেস এজেস* - শর্তানুযায়ী মেসেজ রুট করে বিভিন্ন এক্সিকিউটরে পাঠায়। যেমন, ভ্রমণ গ্রাহক প্রাধিকার পেলে তাদের কাজ অন্য ওয়ার্কফ্লো দ্বারা পরিচালিত হয়।

*ফ্যান-আউট এজেস* - একটি মেসেজ একাধিক টার্গেটে পাঠায়।

*ফ্যান-ইন এজেস* - একাধিক এক্সিকিউটরের মেসেজ সংগ্রহ করে একটিতে পাঠায়।

**ইভেন্টস**

ওয়ার্কফ্লো উন্নত অবজারভেবিলিটির জন্য MAF বাস্তবায়িত ইভেন্ট দেয়:

- `WorkflowStartedEvent` - ওয়ার্কফ্লো শুরু
- `WorkflowOutputEvent` - ওয়ার্কফ্লো আউটপুট তৈরি করে
- `WorkflowErrorEvent` - ওয়ার্কফ্লো ত্রুটি পায়
- `ExecutorInvokeEvent` - এক্সিকিউটর কাজ শুরু করে
- `ExecutorCompleteEvent` - এক্সিকিউটর কাজ শেষ করে
- `RequestInfoEvent` - একটি রিকোয়েস্ট ইস্যু হয়

## অন্যান্য ফ্রেমওয়ার্ক থেকে মাইগ্রেট (Semantic Kernel এবং AutoGen)

### MAF এবং Semantic Kernel এর মধ্যে পার্থক্য

**সহজকৃত এজেন্ট তৈরি**

Semantic Kernel প্রতি এজেন্টে কের্নেল ইনস্ট্যান্স তৈরি করে। MAF সহজ পদ্ধতি গ্রহণ করেছে মেইন প্রোভাইডারের জন্য এক্সটেনশন ব্যবহার করে।

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**এজেন্ট থ্রেড তৈরি**

Semantic Kernel থ্রেড ম্যানুয়ালি তৈরি করতে হয়। MAF এজেন্টের সাথে সরাসরি থ্রেড বরাদ্দ করে।

```python
thread = agent.get_new_thread() # এজেন্টটি থ্রেডের সাথে চালান।
```

**টুল রেজিস্ট্রেশন**

Semantic Kernel-এ টুলগুলো কের্নেলে রেজিস্টার করা হয় এবং তারপর কের্নেল এজেন্টের কাছে যায়। MAF-এ টুল সরাসরি এজেন্ট তৈরি করার সময় রেজিস্টার হয়।

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF এবং AutoGen এর মধ্যে পার্থক্য

**টিম বনাম ওয়ার্কফ্লো**

`Teams` হচ্ছে AutoGen এর ইভেন্ট ভিত্তিক এজেন্ট কার্যক্রমের কাঠামো। MAF ব্যবহার করে `Workflows` যা গ্রাফ ভিত্তিক আর্কিটেকচারের মাধ্যমে এক্সিকিউটরের কাছে ডেটা রুট করে।

**টুল তৈরি**

AutoGen ব্যবহার করে `FunctionTool` যা ফাংশনগুলোকে এজেন্টের জন্য প্রেরণযোগ্য করে। MAF ব্যবহার করে @ai_function যা অনুরূপ কাজ করে এবং প্রতিটি ফাংশনের স্কিমাও স্বয়ংক্রিয়ভাবে বের করে।

**এজেন্ট আচরণ**

AutoGen-এ ডিফল্টভাবে এজেন্টরা সিঙ্গেল-টার্ন, তবে `max_tool_iterations` বাড়ালে তা মাল্টি-টার্ন হয়। MAF-এ `ChatAgent` ডিফল্ট মাল্টি-টার্ন যা ইউজারের কাজ শেষ না হওয়া পর্যন্ত টুল কল চালিয়ে যায়।

## কোড নমুনা

মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্কের জন্য কোড নমুনা এই রিপোজিটরির `xx-python-agent-framework` এবং `xx-dotnet-agent-framework` ফাইলের মধ্যে দেখা যাবে।

## মাইক্রোসফট এজেন্ট ফ্রেমওয়ার্ক সম্পর্কে আরও প্রশ্ন?

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)-এ যোগ দিন অন্যান্য শিক্ষার্থীদের সাথে মিশতে, অফিস আওয়ারস-এ অংশ নিতে এবং আপনার AI এজেন্ট সম্পর্কিত প্রশ্নের উত্তর পেতে।

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**অস্বীকৃতি**:  
এই নথিটি AI অনুবাদ সেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনূদিত হয়েছে। আমরা যথাসাধ্য সঠিকতা নিশ্চিত করার চেষ্টা করি, তবে অনুগ্রহ করে সচেতন থাকুন যে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা অননুমোদিত তথ্য থাকতে পারে। মূল নথিটি এর স্বকীয় ভাষায় সংশ্লিষ্ট কর্তৃপক্ষের কাছ থেকে বিবেচিত হওয়া উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদের পরামর্শ দেওয়া হয়। এই অনুবাদের ব্যবহার থেকে সৃষ্ট কোনো ভুলবোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায়িত্বশীল নয়।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->