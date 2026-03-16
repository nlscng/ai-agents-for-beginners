[![কিভাবে ভালো AI এজেন্ট ডিজাইন করবেন](../../../translated_images/bn/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(এই পাঠের ভিডিও দেখতে উপরের ইমেজে ক্লিক করুন)_

# টুল ইউস ডিজাইন প্যাটার্ন

টুলগুলি দারুণ কারণ এগুলি AI এজেন্টদের বিস্তৃত কার্যাবলী সম্পাদনের সুযোগ দেয়। এজেন্টের সঞ্চালনযোগ্য কার্যগুলির সীমিত সেট থাকার পরিবর্তে, একটি টুল যুক্ত করার মাধ্যমে এজেন্ট এখন ব্যাপক পরিসরের কাজ করতে পারে। এই অধ্যায়ে আমরা টুল ইউস ডিজাইন প্যাটার্ন সম্পর্কে আলোচনা করব, যা বর্ণনা করে AI এজেন্টরা কীভাবে নির্দিষ্ট টুল ব্যবহার করে তাদের লক্ষ্য অর্জন করতে পারে।

## পরিচিতি

এই পাঠে আমরা নিম্নলিখিত প্রশ্নগুলোর উত্তর খুঁজব:

- টুল ইউস ডিজাইন প্যাটার্ন কী?
- কোন ব্যবহারের ক্ষেত্রে এটি প্রয়োগ করা যায়?
- ডিজাইন প্যাটার্ন বাস্তবায়নে প্রয়োজনীয় উপাদান/বিল্ডিং ব্লক কী কী?
- বিশ্বাসযোগ্য AI এজেন্ট তৈরিতে টুল ইউস ডিজাইন প্যাটার্ন ব্যবহার করার বিশেষ বিবেচনাগুলো কী কী?

## শেখার লক্ষ্য

এই পাঠ শেষ করার পর আপনি সক্ষম হবেন:

- টুল ইউস ডিজাইন প্যাটার্ন এবং এর উদ্দেশ্য ব্যাখ্যা করতে।
- কোন ব্যবহারের ক্ষেত্রে টুল ইউস ডিজাইন প্যাটার্ন প্রযোজ্য তা চিহ্নিত করতে।
- ডিজাইন প্যাটার্ন বাস্তবায়নের জন্য প্রয়োজনীয় মূল উপাদানগুলো বুঝতে।
- এই ডিজাইন প্যাটার্ন ব্যবহার করে AI এজেন্টের বিশ্বাসযোগ্যতা নিশ্চিত করার জন্য বিবেচনাগুলো চিনতে।

## টুল ইউস ডিজাইন প্যাটার্ন কী?

**টুল ইউস ডিজাইন প্যাটার্ন** বড় ভাষা মডেল (LLMs) কে নির্দিষ্ট লক্ষ্য অর্জনের জন্য বাহ্যিক টুলের সাথে ইন্টারঅ্যাক্ট করার ক্ষমতা প্রদান করে। টুল হচ্ছে এমন কোড যা একটি এজেন্টের মাধ্যমে চালানো যায় কিছু কাজ সম্পাদনের জন্য। একটি টুল একটি সহজ ফাংশন হতে পারে যেমন ক্যালকুলেটর, অথবা তৃতীয় পক্ষের সেবার API কল, যেমন স্টক মূল্য সন্ধান বা আবহাওয়ার পূর্বাভাস। AI এজেন্টদের প্রেক্ষাপটে, টুলগুলো **মডেল-উত্পাদিত ফাংশন কলের** উত্তরে এজেন্ট দ্বারা চালানোর জন্য ডিজাইন করা হয়।

## কোন ব্যবহারের ক্ষেত্রে এটি প্রয়োগ করা যায়?

AI এজেন্টরা জটিল কাজ সম্পন্ন করতে, তথ্য আহরণ করতে বা সিদ্ধান্ত নিতে টুল ব্যবহার করতে পারে। টুল ইউস ডিজাইন প্যাটার্ন সাধারণত এমন পরিস্থিতিতে ব্যবহৃত হয় যেখানে বাহ্যিক সিস্টেমের সাথে গতিশীল ইন্টারঅ্যাকশন প্রয়োজন, যেমন ডাটাবেস, ওয়েব সার্ভিস, বা কোড ইন্টারপ্রেটার। এটি বিভিন্ন ব্যবহারের ক্ষেত্রে উপকারী, যার মধ্যে রয়েছে:

- **গতিশীল তথ্য সংগ্রহ:** এজেন্টরা আপ-টু-ডেট ডেটা আনার জন্য বাহ্যিক API বা ডাটাবেসকে প্রশ্ন করতে পারে (যেমন, SQLite ডাটাবেস থেকে তথ্য বিশ্লেষণ, স্টক মূল্য বা আবহাওয়ার তথ্য সংগ্রহ)।
- **কোড কার্যকরকরণ ও ব্যাখ্যা:** এজেন্টরা গণিত সমস্যা সমাধান, রিপোর্ট তৈরি বা সিমুলেশন চালানোর জন্য কোড বা স্ক্রিপ্ট চালাতে পারে।
- **কর্মপ্রবাহ স্বয়ংক্রিয়করণ:** টাস্ক শিডিউলার, ইমেইল সার্ভিস বা ডেটা পাইপলাইন ইন্টিগ্রেট করে পুনরাবৃত্তিমূলক বা বহু-ধাপের কর্মপ্রবাহ স্বয়ংক্রিয় করা।
- **গ্রাহক সহায়তা:** এজেন্টরা CRM সিস্টেম, টিকিটিং প্ল্যাটফর্ম বা জ্ঞানভিত্তিক ক্ষেত্রের সাথে ইন্টারঅ্যাক্ট করে ব্যবহারকারীর প্রশ্নের উত্তর দিতে পারে।
- **কন্টেন্ট তৈরি ও সম্পাদনা:** এজেন্টরা ব্যাকরণ পরীক্ষক, টেক্সট সারাংশকারী বা কন্টেন্ট সেফটি মূল্যায়ক মত টুল ব্যবহার করে কন্টেন্ট তৈরিতে সহায়তা করতে পারে।

## টুল ইউস ডিজাইন প্যাটার্ন বাস্তবায়নের জন্য কোন উপাদান/বিল্ডিং ব্লক প্রয়োজন?

এই বিল্ডিং ব্লকসমূহ AI এজেন্টকে বিস্তৃত কাজ করতে সাহায্য করে। চলুন টুল ইউস ডিজাইন প্যাটার্ন বাস্তবায়নের জন্য প্রয়োজনীয় মূল উপাদানগুলো দেখি:

- **ফাংশন/টুল স্কিমা:** উপলব্ধ টুলগুলোর বিষদ সংজ্ঞা, যার মধ্যে ফাংশনের নাম, উদ্দেশ্য, প্রয়োজনীয় প্যারামিটার ও প্রত্যাশিত আউটপুট। এই স্কিমাগুলো LLM কে উপলব্ধ টুলের তথ্য দেয় এবং বৈধ অনুরোধ নির্মাণে সাহায্য করে।

- **ফাংশন কার্যকরকরণ লজিক:** ব্যবহারকারীর অভিপ্রায় ও কথোপকথনের প্রেক্ষাপট অনুযায়ী কখন ও কিভাবে টুলগুলো ডাকা হয় তা নিয়ন্ত্রণ করে। এতে পরিকল্পনাকারী মডিউল, রাউটিং ব্যবস্থা, অথবা শর্তাধীন প্রবাহ থাকতে পারে যা টুল ব্যবহার গতিশীলভাবে নির্ধারণ করে।

- **মেসেজ হ্যান্ডলিং সিস্টেম:** ব্যবহারকারীর ইনপুট, LLM প্রতিক্রিয়া, টুল কল এবং টুল আউটপুটের মধ্যে কথোপকথনের প্রবাহ নিয়ন্ত্রণ করে।

- **টুল ইন্টিগ্রেশন ফ্রেমওয়ার্ক:** সহজ ফাংশন হোক বা জটিল বাহ্যিক সার্ভিস, এজেন্টকে বিভিন্ন টুলের সাথে সংযুক্ত করে।

- **ত্রুটি পরিচালনা ও যাচাই:** টুল কার্যকরকরণে ত্রুটি সামলানো, প্যারামিটার যাচাইকরণ, এবং অপ্রত্যাশিত প্রতিক্রিয়া নিয়ন্ত্রণের প্রক্রিয়া।

- **স্থিতি ব্যবস্থাপনা:** কথোপকথনের প্রেক্ষাপট, পূর্ববর্তী টুল ইন্টারঅ্যাকশন ও অবিচল তথ্য ট্র্যাক করে বহু-বার্তা ইন্টারঅ্যাকশনে সঙ্গতি বজায় রাখে।

এরপর, ফাংশন/টুল কলিং আরও বিস্তারিতভাবে দেখি।

### ফাংশন/টুল কলিং

ফাংশন কলিং হল সেই মূল উপায় যার মাধ্যমে বড় ভাষা মডেলগুলো (LLMs) টুলের সাথে ইন্টারঅ্যাক্ট করতে সক্ষম হয়। প্রায়ই 'ফাংশন' এবং 'টুল' একে অপরের পরিবর্তে ব্যবহৃত হয় কারণ 'ফাংশন' (পুনরায় ব্যবহারযোগ্য কোড ব্লক) হল এজেন্টদের ব্যবহৃত 'টুল' কাজ সম্পাদনের জন্য। একটি ফাংশনের কোড কল করার জন্য, একটি LLM ব্যবহারকারীর অনুরোধ ফাংশনের বর্ণনার সাথে তুলনা করে। এজন্য একটি স্কিমা প্রয়োজন যা উপলব্ধ সকল ফাংশনের বর্ণনা রাখে এবং তা LLM কে পাঠানো হয়। LLM তখন কাজের জন্য সবচেয়ে উপযুক্ত ফাংশন নির্বাচন করে তার নাম ও আর্গুমেন্ট প্রদান করে। নির্বাচিত ফাংশনটি কল করা হয়, এর প্রতিক্রিয়া LLM এ ফেরত পাঠানো হয়, যা ব্যবহারকারীর অনুরোধকে সাড়া দিতে ব্যবহৃত হয়।

এজেন্টের জন্য ফাংশন কলিং বাস্তবায়নের জন্য দরকার:

1. ফাংশন কলিং সমর্থনকারী LLM মডেল
2. ফাংশন বর্ণনা যুক্ত স্কিমা
3. প্রতিটি বর্ণিত ফাংশনের কোড

চলুন একটি উদাহরণ দেখি: একটি শহরের বর্তমান সময় পাওয়া।

1. **ফাংশন কলিং সমর্থনকারী LLM ইনিশিয়ালাইজ করুন:**

    সব মডেল ফাংশন কলিং সমর্থন করে না, তাই ব্যবহৃত LLM এ এটি আছে কি না যাচাই করা জরুরি। <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> ফাংশন কলিং সমর্থন করে। আমরা Azure OpenAI ক্লায়েন্ট ইনিশিয়ালাইজ করে শুরু করব।

    ```python
    # Azure OpenAI ক্লায়েন্টটি ইনিশিয়ালাইজ করুন
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **একটি ফাংশন স্কিমা তৈরি করুন:**

    পরবর্তীতে আমরা একটি JSON স্কিমা নির্ধারণ করব, যাতে ফাংশনের নাম, ফাংশনটির কাজের বর্ণনা, এবং প্যারামিটারগুলোর নাম ও বর্ণনা থাকবে। তারপর আমরা এই স্কিমা ব্যবহার করে, পূর্বে তৈরি ক্লায়েন্টকে ব্যবহারকারীর 'San Francisco' সময় জানার অনুরোধ পাঠাব। লক্ষ্যণীয়, ফেরত আসা হল একটি **টুল কল**, **সর্বশেষ উত্তর নয়**। আগেই যেমন বলা হয়েছে, LLM কাজের জন্য নির্বাচিত ফাংশনের নাম এবং আর্গুমেন্ট দেয়।

    ```python
    # মডেল পড়ার জন্য ফাংশনের বর্ণনা
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # প্রাথমিক ব্যবহারকারীর বার্তা
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # প্রথম API কল: মডেলকে ফাংশনটি ব্যবহার করতে বলুন
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # মডেলের প্রতিক্রিয়া প্রক্রিয়া করুন
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **কাজ সম্পাদনের জন্য প্রয়োজনীয় ফাংশন কোড:**

    এখন LLM কোন ফাংশন চালাতে হবে তা বেছে নিয়েছে, সেই কাজটি সম্পাদনের কোড বাস্তবায়ন ও চালনা করতে হবে। 
    আমরা পাইথনের মাধ্যমে বর্তমান সময় পাওয়ার কোড লিখব। এছাড়াও response_message থেকে নাম ও আর্গুমেন্ট বের করার কোডও লিখতে হবে, যা চূড়ান্ত ফলাফল দিবে।

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # ফাংশন কলগুলি পরিচালনা করুন
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # দ্বিতীয় API কল: মডেল থেকে চূড়ান্ত প্রতিক্রিয়া পান
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

ফাংশন কলিং অধিকাংশ, নাও শুত্রে সব এজেন্ট টুল ইউস ডিজাইনের কেন্দ্রে থাকে, তবে শুরু থেকে এটি বাস্তবায়ন করা সময় সময় চ্যালেঞ্জিং হতে পারে। 
আমরা শিখেছি [Lesson 2](../../../02-explore-agentic-frameworks) থেকে যে এজেন্টিক ফ্রেমওয়ার্কগুলো পূর্বনির্মিত বিল্ডিং ব্লক সরবরাহ করে টুল ব্যবহার বাস্তবায়নে।

## এজেন্টিক ফ্রেমওয়ার্ক সহ টুল ইউস উদাহরণ

নিম্নে বিভিন্ন এজেন্টিক ফ্রেমওয়ার্ক ব্যবহার করে কিভাবে টুল ইউস ডিজাইন প্যাটার্ন বাস্তবায়ন করা যায় তার কিছু উদাহরণ:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> হল .NET, Python, এবং Java ডেভেলপারদের জন্য ওপেন-সোর্স AI ফ্রেমওয়ার্ক যারা LLM নিয়ে কাজ করে। এটি ফাংশন কলিং প্রক্রিয়া সহজ করে ফাংশন এবং তাদের প্যারামিটারগুলি মডেলের কাছে <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">সিরিয়ালাইজিং</a> মাধ্যমে বর্ণনা করে। এটি মডেল ও আপনার কোডের মধ্যে বার্তালাপ পরিচালনাও করে। Semantic Kernel এর মত এজেন্টিক ফ্রেমওয়ার্ক ব্যবহারের আরেকটি সুবিধা হলো পূর্বনির্মিত টুল ব্যবহার করতে পারা যেমন <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> ও <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>।

নিচের চিত্রে Semantic Kernel এর মাধ্যমে ফাংশন কলিং প্রক্রিয়া দেখানো হয়েছে:

![function calling](../../../translated_images/bn/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernel এ ফাংশন/টুলগুলোকে <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">প্লাগইনস</a> বলা হয়। আগে আমরা যা `get_current_time` ফাংশন দেখেছিলাম, তা একটি ক্লাসে রূপান্তর করে প্লাগইন হিসেবে তৈরি করা যায়। আমরা `kernel_function` ডেকোরেটরও ইমপোর্ট করতে পারি, যা ফাংশনের বর্ণনা নেয়। এরপর GetCurrentTimePlugin সহ একটি kernel তৈরি করলে, kernel স্বয়ংক্রিয়ভাবে ফাংশন ও তার প্যারামিটার সিরিয়ালাইজ করে এবং স্কিমা তৈরি করে যা LLM কে পাঠানো হয়।

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# কার্নেল তৈরি করুন
kernel = Kernel()

# প্লাগইন তৈরি করুন
get_current_time_plugin = GetCurrentTimePlugin(location)

# প্লাগইনটি কার্নেলের সাথে যোগ করুন
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> একটি নতুন এজেন্টিক ফ্রেমওয়ার্ক যা ডেভেলপারদের নিরাপদে উচ্চমানের, বিস্তৃত, এবং সম্প্রসারিত AI এজেন্ট তৈরি, প্রকাশ ও স্কেল করতে সক্ষম করে, যেখানে কম্পিউট ও স্টোরেজ সম্পদ ব্যবস্থাপনা করার দরকার হয় না। এটি বিশেষ করে এন্টারপ্রাইজ অ্যাপ্লিকেশনের জন্য উপযোগী কারণ এটি একটি পূর্ণ ম্যানেজড সার্ভিস এবং এন্টারপ্রাইজ গ্রেড সিকিউরিটি প্রদান করে।

LLM API সরাসরি ব্যবহারের তুলনায় Azure AI Agent Service কিছু সুবিধা দেয়, যেমন:

- স্বয়ংক্রিয় টুল কলিং – টুল কল পার্সিং, টুল কল করা, এবং প্রতিক্রিয়া হ্যান্ডলিংয়ের প্রয়োজন নেই; সবকিছু সার্ভার-সাইডে হয়
- নিরাপদে পরিচালিত ডেটা – নিজের কথোপকথন স্টেট পরিচালনার পরিবর্তে থ্রেডে সব তথ্য সংরক্ষণ করতে পারেন
- আগেই তৈরি টুলস – Bing, Azure AI Search, এবং Azure Functions এর মত ডেটা সোর্সের সাথে ইন্টারঅ্যাক্ট করার জন্য টুলপত্র রয়েছে।

Azure AI Agent Service এ উপলব্ধ টুলগুলো দুইটি শ্রেণীতে বিভক্ত:

1. জ্ঞানমূলক টুল:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing Search এর সাথে গ্রাউন্ডিং</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. অ্যাকশন টুল:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI সংজ্ঞায়িত টুলস</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service এইসব টুল একসাথে `toolset` হিসেবে ব্যবহার করার সুযোগ দেয়। এটি `threads` ব্যবহার করে, যা নির্দিষ্ট কথোপকথন থেকে মেসেজ ইতিহাস ট্র্যাক করে।

ধরুন আপনি Contoso নামের কোম্পানির সেলস এজেন্ট। আপনি এমন একটি কথোপকথন এজেন্ট তৈরি করতে চান যা আপনার সেলস ডেটা সম্পর্কে প্রশ্নের উত্তর দিতে পারে।

নিচের ছবি Azure AI Agent Service ব্যবহার করে কিভাবে সেলস ডেটা বিশ্লেষণ করা যায় দেখায়:

![Agentic Service In Action](../../../translated_images/bn/agent-service-in-action.34fb465c9a84659e.webp)

এই সার্ভিসের সাথে যেকোনো টুল ব্যবহার করতে আমরা ক্লায়েন্ট তৈরি করে একটি টুল বা টুলসেট ডিফাইন করব। বাস্তবায়নে নিচের পাইথন কোড ব্যবহার করতে পারি। LLM টুলসেট দেখে সিদ্ধান্ত নেবে ব্যবহারকারীর অনুরোধ অনুযায়ী `fetch_sales_data_using_sqlite_query` নামে ব্যবহারকারীর তৈরি ফাংশন ব্যবহার করবে বা পূর্বনির্মিত Code Interpreter।

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query ফাংশন যা একটি fetch_sales_data_functions.py ফাইলে পাওয়া যাবে।
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# টুলসেট ইনিশিয়ালাইজ করুন
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query ফাংশন সহ ফাংশন কলিং এজেন্ট ইনিশিয়ালাইজ করুন এবং এটিকে টুলসেটে যোগ করুন
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# কোড ইন্টারপ্রেটার টুল ইনিশিয়ালাইজ করুন এবং এটিকে টুলসেটে যোগ করুন।
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## বিশ্বাসযোগ্য AI এজেন্ট তৈরিতে টুল ইউস ডিজাইন প্যাটার্ন ব্যবহারে বিশেষ বিবেচনাগুলো কী কী?

LLM দ্বারা ডায়নামিক্যালি তৈরি SQL নিয়ে একটি সাধারণ উদ্বেগ হলো নিরাপত্তা, বিশেষ করে SQL ইনজেকশন কিংবা অপব ïধি, যেমন ডাটাবেস ড্রপ করা বা ছলনা করার সম্ভাবনা। যদিও এই উদ্বেগগুলো গুরুত্বপূর্ণ, সেগুলি কার্যকরভাবে হ্রাস করা যায় সঠিকভাবে ডাটাবেস অ্যাক্সেস অনুমতি কনফিগার করে। বেশিরভাগ ডাটাবেসের জন্য এটি রিড-ওনলি কনফিগারেশন প্রয়োজন। PostgreSQL বা Azure SQL মত ডাটাবেস সেবায় অ্যাপকে রিড-ওনলি (SELECT) রোল দেওয়া উচিত।

অ্যাপকে নিরাপদ পরিবেশে চালানো আরও সুরক্ষা বৃদ্ধি করে। এন্টারপ্রাইজ ক্ষেত্রে, ডেটা সাধারণত অপারেশনাল সিস্টেম থেকে আলাদা করে রিড-ওনলি ডাটাবেস বা ডেটা ওয়্যারহাউসে রূপান্তরিত হয় যা ব্যবহারকারী-বান্ধব স্কিমা থাকে। এই পদ্ধতি নিশ্চিত করে যে ডেটা নিরাপদ, কর্মক্ষম এবং প্রবেশযোগ্য, এবং অ্যাপের অ্যাক্সেস সীমাবদ্ধ রিড-ওনলি।

## নমুনা কোডসমূহ
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## টুল ব্যবহারের ডিজাইন প্যাটার্ন সম্পর্কে আরও প্রশ্ন আছে?

অন্য শিক্ষার্থীদের সাথে দেখা করার জন্য, অফিস আওয়ার এ যোগদানের জন্য এবং আপনার AI এজেন্ট সম্পর্কিত প্রশ্নের উত্তর পেতে [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)-এ যোগ দিন।

## অতিরিক্ত সম্পদ

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## পূর্ববর্তী পাঠ

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## পরবর্তী পাঠ

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**অস্বীকারোক্তি**:  
এই নথিটি AI অনুবাদ সেবার [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনূদিত হয়েছে। আমরা সঠিকতার জন্য যথাসাধ্য চেষ্টা করি, তবে দয়া করে মনে রাখবেন যে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা ভুল থাকতে পারে। মূল নথিটি তার নিজ ভাষায় কর্তৃত্বপূর্ণ উৎস হিসেবে বিবেচিত হওয়া উচিত। গুরুতর তথ্যের জন্য পেশাদার মানব অনুবাদের পরামর্শ দেওয়া হয়। এই অনুবাদ ব্যবহারের ফলে কোনো ভুল বোঝাবুঝি বা ব্যাখ্যার জন্য আমরা দায়ী নই।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->