[![বিশ্বস্ত AI এজেন্টসমূহ](../../../translated_images/bn/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(এই পাঠের ভিডিও দেখতে উপরের ছবিটি ক্লিক করুন)_

# বিশ্বস্ত AI এজেন্ট নির্মাণ

## পরিচিতি

এই পাঠে আলোচনা করা হবে:

- কীভাবে নিরাপদ এবং কার্যকর AI এজেন্ট তৈরি ও মোতায়েন করবেন
- AI এজেন্ট উন্নয়নের সময় গুরুত্বপূর্ণ নিরাপত্তা বিবেচ্য বিষয়সমূহ।
- AI এজেন্ট উন্নয়নের সময় কীভাবে তথ্য ও ব্যবহারকারীর গোপনীয়তা রক্ষা করবেন।

## শেখার লক্ষ্য

এই পাঠ শেষ করার পর, আপনি শিখতে পারবেন কীভাবে:

- AI এজেন্ট তৈরি করার সময় ঝুঁকি চিহ্নিত এবং কমাতে হয়।
- নিরাপত্তা ব্যবস্থা বাস্তবায়ন করে তথ্য ও প্রবেশাধিকার সঠিকভাবে পরিচালিত হয় তা নিশ্চিত করতে হয়।
- এমন AI এজেন্ট তৈরি করা যা তথ্য গোপনীয়তা বজায় রাখে ও মানসম্মত ব্যবহারকারী অভিজ্ঞতা প্রদান করে।

## নিরাপত্তা

প্রথমে আসুন নিরাপদ এজেন্টিক অ্যাপ্লিকেশন নির্মাণের কথা দেখি। নিরাপত্তা মানে AI এজেন্ট তার ডিজাইনের মতো কাজ করে। এজেন্টিক অ্যাপ্লিকেশন নির্মাতাদের জন্য নিরাপত্তা সর্বাধিক করার জন্য আমাদের রয়েছে পদ্ধতি এবং সরঞ্জাম:

### একটি সিস্টেম মেসেজ ফ্রেমওয়ার্ক তৈরি করা

আপনি যদি কখনও বৃহৎ ভাষা মডেল (LLM) ব্যবহার করে AI অ্যাপ্লিকেশন তৈরি করে থাকেন, তাহলে আপনি জানেন একটি শক্তিশালী সিস্টেম প্রম্পট বা সিস্টেম মেসেজ ডিজাইন করার গুরুত্ব। এই প্রম্পটগুলি মেটা নিয়ম, নির্দেশাবলী এবং গাইডলাইন স্থাপন করে কীভাবে LLM ব্যবহারকারী ও তথ্যের সাথে যোগাযোগ করবে।

AI এজেন্টদের জন্য, সিস্টেম প্রম্পট আরও বেশি গুরুত্বপূর্ণ কারণ AI এজেন্টদের আমাদের ডিজাইন করা কাজ সম্পন্ন করার জন্য খুব নির্দিষ্ট নির্দেশাবলী প্রয়োজন।

স্কেলেবল সিস্টেম প্রম্পট তৈরি করতে, আমরা একটি সিস্টেম মেসেজ ফ্রেমওয়ার্ক ব্যবহার করতে পারি যেটি আমাদের অ্যাপ্লিকেশনে এক বা একাধিক এজেন্ট তৈরি করতে সাহায্য করবে:

![Building a System Message Framework](../../../translated_images/bn/system-message-framework.3a97368c92d11d68.webp)

#### ধাপ ১: একটি মেটা সিস্টেম মেসেজ তৈরি করুন

মেটা প্রম্পটটি LLM ব্যবহার করে আমাদের তৈরি করা এজেন্টদের জন্য সিস্টেম প্রম্পট তৈরি করতে ব্যবহৃত হবে। আমরা এটি একটি টেমপ্লেট হিসেবে ডিজাইন করি যাতে প্রয়োজনে অনেক এজেন্ট দ্রুত তৈরি করা যায়।

এখানে একটি মেটা সিস্টেম মেসেজের উদাহরণ যা আমরা LLM কে দেব:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### ধাপ ২: একটি মৌলিক প্রম্পট তৈরি করুন

পরবর্তী ধাপ হল AI এজেন্টের বর্ণনা দেওয়ার জন্য একটি মৌলিক প্রম্পট তৈরি করা। এতে এজেন্টের ভূমিকা, এজেন্ট যে কাজগুলো সম্পন্ন করবে এবং এজেন্টের অন্যান্য দায়িত্ব অন্তর্ভুক্ত করা উচিত।

এখানে একটি উদাহরণ:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### ধাপ ৩: মৌলিক সিস্টেম মেসেজ LLM কে প্রদান করুন

এখন আমরা এই সিস্টেম মেসেজটিকে উন্নত করতে পারি মেটা সিস্টেম মেসেজ এবং আমাদের মৌলিক সিস্টেম মেসেজ প্রদান করে।

এটি একটি সিস্টেম মেসেজ তৈরি করবে যা আমাদের AI এজেন্টদের নির্দেশনার জন্য আরও ভালো ডিজাইন করা হয়েছে:

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

#### ধাপ ৪: পুনরাবৃত্তি এবং উন্নয়ন

এই সিস্টেম মেসেজ ফ্রেমওয়ার্কের মূল্য হলো একাধিক এজেন্টের সিস্টেম মেসেজ তৈরি করা সহজ করা এবং সময়ের সাথে আপনার সিস্টেম মেসেজ উন্নত করা। প্রথমবারেই আপনার সম্পূর্ণ ব্যবহারের জন্য কাজ করা একটি সিস্টেম মেসেজ পাওয়া বিরল। ছোটখাটো পরিবর্তন এবং উন্নতি করার মাধ্যমে মৌলিক সিস্টেম মেসেজ পরিবর্তন করে এটি সিস্টেমের মাধ্যমে চালিয়ে আপনি ফলাফল তুলনা এবং মূল্যায়ন করতে পারবেন।

## হুমকি বোঝা

বিশ্বস্ত AI এজেন্ট তৈরি করার জন্য, আপনার AI এজেন্টের ঝুঁকি ও হুমকি বোঝা এবং কমানো গুরুত্বপূর্ণ। আসুন AI এজেন্টের বিভিন্ন হুমকির মধ্যে কয়েকটি দেখি এবং কীভাবে আপনি এগুলোর জন্য ভালো পরিকল্পনা ও প্রস্তুতি নেবেন।

![Understanding Threats](../../../translated_images/bn/understanding-threats.89edeada8a97fc0f.webp)

### কাজ ও নির্দেশনা

**বর্ণনা:** আক্রমণকারীরা প্রম্পটিং বা ইনপুট ম্যানিপুলেশন মাধ্যমে AI এজেন্টের নির্দেশনা বা লক্ষ্য পরিবর্তন করার চেষ্টা করে।

**প্রতিরোধ:** AI এজেন্ট প্রক্রিয়াকরণের আগে সম্ভবত বিপজ্জনক প্রম্পট শনাক্তের জন্য যাচাইকরণ পরীক্ষা ও ইনপুট ফিল্টার ব্যবহার করুন। যেহেতু এই ধরনের আক্রমণ প্রায়ই এজেন্টের সাথে ঘন ঘন যোগাযোগ দাবি করে, কথোপকথনের পালা সংখ্যা সীমাবদ্ধ করাও এই ধরণের আক্রমণ প্রতিরোধের একটি উপায়।

### গুরুত্বপূর্ণ সিস্টেমে প্রবেশাধিকার

**বর্ণনা:** AI এজেন্ট যদি সংবেদনশীল তথ্য সংরক্ষণকারী সিস্টেম এবং পরিষেবায় প্রবেশাধিকার পেয়ে থাকে, আক্রমণকারীরা এজেন্ট ও এই পরিষেবাগুলোর মধ্যে যোগাযোগে কম্প্রোমাইজ করতে পারে। এটি সরাসরি আক্রমণ বা এজেন্টের মাধ্যমে এই সিস্টেম সম্পর্কে তথ্য অর্জনের অপ্রত্যক্ষ প্রচেষ্টা হতে পারে।

**প্রতিরোধ:** এই ধরনের আক্রমণ থেকে রক্ষা করতে AI এজেন্টদের শুধুমাত্র প্রয়োজনীয় সিস্টেমে প্রবেশাধিকার থাকা উচিত। এজেন্ট এবং সিস্টেমের মধ্যে যোগাযোগও নিরাপদ হওয়া উচিত। প্রমাণীকরণ এবং প্রবেশাধিকার নিয়ন্ত্রণ প্রয়োগ করাও তথ্য সুরক্ষার আরেকটি উপায়।

### সম্পদ ও পরিষেবা ওভারলোড

**বর্ণনা:** AI এজেন্ট বিভিন্ন টুল এবং পরিষেবা ব্যবহার করে কাজ শেষ করে। আক্রমণকারীরা এই ক্ষমতাটি ব্যবহার করে AI এজেন্টের মাধ্যমে উচ্চ পরিমাণ অনুরোধ পাঠিয়ে এই পরিষেবাগুলোর বিরুদ্ধে আক্রমণ করতে পারে, যা সিস্টেম ব্যর্থতা বা উচ্চ খরচ সৃষ্টির কারণ হতে পারে।

**প্রতিরোধ:** একটি AI এজেন্ট একটি পরিষেবায় পাঠাতে পারে এমন অনুরোধের সংখ্যা সীমাবদ্ধ করার নীতি বাস্তবায়ন করুন। কথোপকথনের পালা এবং আপনার AI এজেন্টে অনুরোধের সংখ্যা সীমাবদ্ধ করাও এই ধরনের আক্রমণ রোধের উপায়।

### জ্ঞানের ভান্ডার বিষাক্তকরণ

**বর্ণনা:** এই ধরণের আক্রমণ সরাসরি AI এজেন্টকে লক্ষ্য করে না, বরং AI এজেন্ট যে জ্ঞানের ভান্ডার এবং অন্যান্য পরিষেবা ব্যবহার করবে সেগুলোকে লক্ষ্য করে। এতে AI এজেন্টের কাজে ব্যবহৃত তথ্য বা ডেটা ক্ষতিগ্রস্ত হতে পারে, যার ফলে ব্যবহারকারীর প্রতি পক্ষপাতমূলক বা অনাকাঙ্ক্ষিত প্রতিক্রিয়া সৃষ্টি হতে পারে।

**প্রতিরোধ:** AI এজেন্টের কার্যপ্রবাহে ব্যবহৃত ডেটার নিয়মিত যাচাই করুন। এই ডেটার প্রবেশাধিকার নিরাপদ রাখুন এবং শুধুমাত্র বিশ্বাসযোগ্য ব্যক্তিরা পরিবর্তন করতে পারে তা নিশ্চিত করুন যাতে এই ধরনের আক্রমণ এড়ানো যায়।

### ধাপে ধাপে ভুল

**বর্ণনা:** AI এজেন্ট বিভিন্ন টুল এবং পরিষেবা ব্যবহার করে কাজ শেষ করে। আক্রমণকারীদের কারণে সৃষ্ট ভুলগুলি অন্য সিস্টেমগুলির ব্যর্থতার কারণ হতে পারে যা AI এজেন্টের সাথে সংযুক্ত থাকে, ফলে আক্রমণ আরও বিস্তৃত এবং সমাধান কঠিন হয়।

**প্রতিরোধ:** এড়ানোর একটি পদ্ধতি হলো AI এজেন্টকে সীমিত পরিবেশে পরিচালনা করা, যেমন ডকার কন্টেনারের মধ্যে কাজ করা, সরাসরি সিস্টেম আক্রমণ প্রতিরোধের জন্য। নির্দিষ্ট সিস্টেমগুলি ভুল সাড়া দিলে ফোলব্যাক ব্যবস্থা এবং পুনরায় চেষ্টা করার লজিক তৈরি করাও বড় সিস্টেম ব্যর্থতা প্রতিরোধের উপায়।

## হিউম্যান-ইন-দ্যা-লুপ

বিশ্বস্ত AI এজেন্ট সিস্টেম তৈরি করার আরেক কার্যকর উপায় হলো হিউম্যান-ইন-দ্যা-লুপ ব্যবহার। এটি এমন একটি প্রবাহ তৈরি করে যেখানে ব্যবহারকারীরা চলন্ত প্রক্রিয়ায় তাদের প্রতিক্রিয়া প্রদান করতে পারে। ব্যবহারকারীরা একটি মাল্টি-এজেন্ট সিস্টেমে এজেন্ট হিসেবে কাজ করে এবং চলমান প্রক্রিয়া অনুমোদন বা বন্ধ করতে পারে।

![Human in The Loop](../../../translated_images/bn/human-in-the-loop.5f0068a678f62f4f.webp)

এখানে AutoGen ব্যবহার করে এই ধারণাটি কীভাবে বাস্তবায়িত হয় তার একটি কোড স্নিপেট:

```python

# এজেন্ট গুলো তৈরি করুন।
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # কনসোল থেকে ব্যবহারকারীর ইনপুট পেতে input() ব্যবহার করুন।

# একটি সমাপ্তির শর্ত তৈরি করুন যা ব্যবহারকারী "APPROVE" বললে কথোপকথন শেষ করবে।
termination = TextMentionTermination("APPROVE")

# দল তৈরি করুন।
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# কথোপকথন চালান এবং কনসোলে স্ট্রিম করুন।
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# স্ক্রিপ্টে চালানোর সময় asyncio.run(...) ব্যবহার করুন।
await Console(stream)

```

## উপসংহার

বিশ্বস্ত AI এজেন্ট তৈরি করার জন্য সূক্ষ্ম ডিজাইন, শক্তিশালী নিরাপত্তা ব্যবস্থা এবং ধারাবাহিক পুনরাবৃত্তি প্রয়োজন। সংগঠিত মেটা প্রম্পটিং সিস্টেম বাস্তবায়ন, সম্ভাব্য হুমকি বোঝা এবং প্রতিরোধমূলক কৌশল প্রয়োগ করে, ডেভেলপাররা নিরাপদ ও কার্যকর AI এজেন্ট তৈরি করতে পারে। এছাড়াও, হিউম্যান-ইন-দ্যা-লুপ পদ্ধতি অন্তর্ভুক্ত করলে AI এজেন্ট ব্যবহারকারীর চাহিদার সঙ্গে সঙ্গতি বজায় রাখে এবং ঝুঁকি কমায়। AI আরও উন্নত হতে থাকায়, নিরাপত্তা, গোপনীয়তা এবং নৈতিক বিবেচনার বিষয়ে সক্রিয় মনোভাব বজায় রাখা AI চালিত সিস্টেমের বিশ্বস্ততা ও নির্ভরযোগ্যতা বৃদ্ধির মূল চাবিকাঠি হবে।

### বিশ্বস্ত AI এজেন্ট নির্মাণ সম্পর্কে আরও প্রশ্ন আছে?

অন্য শিক্ষার্থীদের সঙ্গে দেখা করতে, অফিসার সময়ে যোগ দিতে এবং আপনার AI এজেন্ট সম্পর্কিত প্রশ্নের উত্তর পেতে [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) এ যোগ দিন।

## অতিরিক্ত উৎস

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">দায়িত্বশীল AI ওভারভিউ</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">জেনারেটিভ AI মডেল ও AI অ্যাপ্লিকেশন মূল্যায়ন</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">নিরাপত্তা সিস্টেম মেসেজ</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">ঝুঁকি মূল্যায়ন টেমপ্লেট</a>

## আগের পাঠ

[Agentic RAG](../05-agentic-rag/README.md)

## পরের পাঠ

[পরিকল্পনা ডিজাইন প্যাটার্ন](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**দ্রষ্টব্য**:  
এই নথিটি AI অনুবাদ সেবা [Co-op Translator](https://github.com/Azure/co-op-translator) ব্যবহার করে অনূদিত হয়েছে। আমরা যথাসাধ্য সঠিকতার চেষ্টা করি, তবে স্বয়ংক্রিয় অনুবাদে ত্রুটি বা অসংগতি থাকতে পারে। প্রামাণিক উৎস হিসেবে মূল নথির নিজস্ব ভাষার সংস্করণকেই বিবেচনা করা উচিত। গুরুত্বপূর্ণ তথ্যের জন্য পেশাদার মানব অনুবাদ সুপারিশ করা হয়। এই অনুবাদের ব্যবহারে কোনও ভুলবোঝাবুঝি বা ভুল ব্যাখ্যার জন্য আমরা দায় স্বীকার করে না।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->