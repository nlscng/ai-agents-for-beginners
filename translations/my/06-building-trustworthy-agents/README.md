[![ယုံကြည်စိတ်ချရသော AI အေးဂျင့်များ](../../../translated_images/my/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(ဓာတ်ပုံကို နှိပ်၍ဤသင်ခန်းစာ၏ ဗီဒီယိုကို ကြည့်ပါ)_

# ယုံကြည်စိတ်ချရသော AI အေးဂျင့်များ တည်ဆောက်ခြင်း

## နိဒါန်း

ဤသင်ခန်းစာတွင် ဖော်ပြမည့် အကြောင်းအရာများမှာ-

- ဘယ်လို လုံခြုံပြီး ထိရောက်သော AI အေးဂျင့်များကို တည်ဆောက်၊ ထုတ်လုပ်မည်နည်း။
- AI အေးဂျင့်များ ဖန်တီးရာတွင် အရေးကြီးသော လုံခြုံမှုအချက်များ။
- AI အေးဂျင့်များ ဖန်တီးရာတွင် ဒေတာနှင့် အသုံးပြုသူကိုယ်ရေး အချက်အလက် လုံခြုံမှု ထိန်းသိမ်းနည်း။

## သင်ယူရမည့် ရည်မှန်းချက်များ

ဤသင်ခန်းစာပြီးမြောက်ပြီးနောက်၊ သင်သိရှိနားလည်မည့်အချက်များ -

- AI အေးဂျင့်များ ဖန်တီးရာတွင် ဖြစ်ပေါ်နိုင်သည့် အန္တရာယ်နှင့် အန္တရာယ်များကို သတ်မှတ်ပြီး လျော့နည်းစေမည့်နည်းများ။
- ဒေတာနှင့် ဝင်ခွင့်များကို သေချာစွာ စီမံရန် လုံခြုံရေး အစီအစဉ်များကို အကောင်အထည်ဖော်ခြင်း။
- ဒေတာကိုယ်ရေးအချက်အလက် ကာကွယ်ပြီး အရည်အသွေးမြင့် အသုံးပြုသူ အတွေ့အကြုံ စေသော AI အေးဂျင့်များ ဖန်တီးခြင်း။

## လုံခြုံရေး

စလုံး အေးဂျင်တစ်ခုအောင် စိုးရိမ်မှုမရှိစေရန် ဂရုပြုစွာ တည်ဆောက်ခြင်းကို ကြည့်ကြရအောင်။ လုံခြုံခြင်းဆိုသည်မှာ AI အေးဂျင့်သည် ပုံသေရဲ့အတိုင်း လုပ်ဆောင်နိုင်ခြင်း ဖြစ်သည်။ အေးဂျင်ဆော့ဖ်၀ဲ တည်ဆောက်သူများအနေနဲ့ လုံခြုံမှု အမြင့်ဆုံးကို ရရှိစေရန် နည်းလမ်းများ၊ ကိရိယာများရှိသည်။

### စနစ်နှင့် သတိပေးစာ Framework တည်ဆောက်ခြင်း

သင် ကြီးမားသောဘာသာစကား မော်ဒယ်(LLMs) အသုံးပြု၍ AI လုပ်ငန်းစဉ် တည်ဆောက်ဖူးလျှင် စနစ် prompt သို့မဟုတ် စနစ်သတိပေးစာ ရေးဆွဲခြင်း အရေးကြီးမှတ်မိပါလိမ့်မယ်။ ၎င်းသည် မိမိကိုယ်တိုင်နှင့် ဒေတာနှင့် LLM ဆက်သွယ်ရေးအတွက် အခြေခံနညး္များ၊ ညွှန်ကြားချက်များ သတ်မှတ်ပေးသည်။

AI အေးဂျင့်များအတွက် စနစ် prompt သည် ပိုမိုအရေးကြီးသည်။ ကိစ္စအစုလိုက်အပြုံလိုက် ပြီးစီးရန် အတိအလင်း ညွှန်ကြားချက်များ လိုအပ်သည်။

မြှင့်တင်နိုင်သော စနစ် prompt များ ဖန်တီးရန် ကျွန်ုပ်တို့သည် application တစ်ခုအတွင်း တစ်ခု သို့မဟုတ် အများအပြား အေးဂျင့်များ တည်ဆောက်နိုင်သော စနစ်သတိပေးစာ ဖွဲ့စည်းတည်ဆောက်ခြင်းကို အသုံးပြုနိုင်သည်။

![စနစ်သတိပေးစာ Framework တည်ဆောက်ခြင်း](../../../translated_images/my/system-message-framework.3a97368c92d11d68.webp)

#### အဆင့် ၁။ Meta စနစ်သတိပေးစာ ဖန်တီးခြင်း

Meta prompt သည် LLM က စနစ် prompt များ ဖန်တီးရာတွင် အသုံးပြုမည်ဖြစ်သည်။ များစွာသော အေးဂျင့်များကို လွယ်ကူစွာ ဖန်တီးရန် အတတ်နိုင်ဆုံး template အဖြစ် ဒီဇိုင်းရေးဆွဲထားသည်။

LLM ထံတွင် ပေးပို့မည့် Meta စနစ်သတိပေးစာ ဥပမာက如下 -

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### အဆင့် ၂။ အခြေခံ prompt တစ်ခု ဖန်တီးခြင်း

နောက်တစ်ဆင့်မှာ AI အေးဂျင့်ကို ဖော်ပြရန် အခြေခံ prompt ရေးဆွဲခြင်းဖြစ်သည်။ အေးဂျင့်၏ တာဝန်၊ ဖျော်ဖြေရမည့် အလုပ်များနှင့် အခြားတာဝန်များ ပါဝင်ရန် လိုအပ်သည်။

ဥပမာ -

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### အဆင့် ၃။ အခြေခံ စနစ်သတိပေးစာကို LLM သို့ ပေးပို့ခြင်း

ယခု meta စနစ်သတိပေးစာနှင့် အခြေခံ စနစ်သတိပေးစာနှစ်သိပ်ပေးပြီး စနစ်သတိပေးစာကို အမြှင့်ဆုံးအဆင့်မှ ပြင်ဆင်မြှင့်တင်နိုင်သည်။

AI အေးဂျင့်များ ဦးဆောင်ရန် ပိုမိုကောင်းမွန်သော စနစ်သတိပေးစာ ထုတ်ပေးမည်ဖြစ်သည် -

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

#### အဆင့် ၄။ အဆက်အသွယ်ပြုပြင်အဆင်မြှင့်

ဤစနစ်သတိပေးစာ framework ၏ တန်ဖိုးမှာ စနစ်သတိပေးစာများကို အမျိုးမျိုးသော အေးဂျင့်များအတွက် ပိုမိုလွယ်ကူစွာ တိုးချဲ့ဖန်တီးခြင်းနှင့် ကောင်းမွန်လာစေရန် ကြိုးပမ်းနိုင်ခြင်း ဖြစ်သည်။ မူလအကြောင်းအခြေအနေဖြင့် သင့်လိုအပ်ချက်နှင့်ကိုက်ညီသည့် ကိုယ်တိုင်အဖော်ပြချက်ရှိသော စနစ်သတိပေးစာ ရရှိရေး အလွန်ရှားပါးသည်။ အခြေခံ စနစ်သတိပေးစာ အနည်းငယ်ပြောင်းလဲ၍ စနစ်မှ အသုံးပြု၍ ရလဒ်များကို နှိုင်းယှဉ် ကျယ်ပြန့်စွာ မည့်ဟာ ကောင်းသည်ဆိုတာ ဆုံးဖြတ်နိုင်သည်။

## အန္တရာယ်များကို နားလည်ခြင်း

ယုံကြည်စိတ်ချရသော AI အေးဂျင့်များ တည်ဆောက်ရန်အတွက် သင့် AI အေးဂျင့်အပေါ် ဖြစ်ပေါ်နိုင်သည့် အန္တရာယ်များနှင့် အန္တရာယ်များကို နားလည်ပြီး လျော့နည်းစေရန် မဖြစ်မနေ လိုအပ်သည်။ AI အေးဂျင့်ကို ကြုံတွေ့နိုင်သည့် အန္တရာယ်အချို့ကိုသာ ကြည့်ရှုကြကြပါစို့၊ နှင့် မည်သို့ကောင်းစွာ စီမံကျင့်သုံးနိုင်မည်နည်း။

![အန္တရာယ်များ နားလည်ခြင်း](../../../translated_images/my/understanding-threats.89edeada8a97fc0f.webp)

### တာဝန်နှင့် ညွှန်ကြားချက်

**ဖော်ပြချက်:** ခိုးယူသူများသည် AI အေးဂျင့်၏ ညွှန်ကြားချက် သို့မဟုတ် ရည်မှန်းချက်များကို prompt သို့မဟုတ် input မှတဆင့် ပြောင်းလဲရန် ကြိုးပမ်းသည်။

**လျော့နည်းစေမှု**: စစ်ဆေးခြင်းနှင့် input ဖန်တီးမှု စနစ်များ သုံး၍ အန္တရာယ်ရှိနိုင်သော prompt များကို AI အေးဂျင့်မှ စီမံမမီ သတိပေးစစ်ဆေးပါ။ ၎င်းတိုင်းသည် AI အေးဂျင့်နှင့် မကြာခဏ ဆက်သွယ်မှု လိုအပ်သောကြောင့် စကားပြောပွဲ ရာထူးများကို ကန့်သတ်ခြင်းက ဤအမျိုးအစား အတှကျကာကွယ်နိုင်သည်။

### အရေးကြီး စနစ်များ ဝင်ခွင့်

**ဖော်ပြချက်**: AI အေးဂျင့်သည် အချက်အလက်များ သိမ်းဆည်းထားသော စနစ်နှင့် ဝန်ဆောင်မှုများကို ဝင်ခွင့်ရှိပါက ခိုးယူသူများသည် အေးဂျင့်နှင့် ဤဝန်ဆောင်မှုများ အကြား ဆက်သွယ်မှုကို ဖောက်ပြန်နိုင်သည်။ ဤသည်များမှာ တိုက်ရိုက် ထိခိုက်မှု သို့မဟုတ် အပြောင်းအလဲမရှိဘဲ အချက်အလက်များ ရယူရန် ကြိုးပမ်းမှုများ ဖြစ်နိုင်သည်။

**လျော့နည်းစေမှု**: AI အေးဂျင့်များသည် ဖြတ်သန်းခွင့် လိုအပ်သည့်အခါမှသာ စနစ်များကို ဝင်ရောက်နိုင်ရန် ထိန်းချုပ်ထားသင့်သည်။ အေးဂျင့်နှင့် စနစ် အကြားဆက်သွယ်မှု လုံခြုံစေရန် authentication နှင့် access control များကို ပုံသေနည်းဖြင့် လုပ်ဆောင်သင့်သည်။

### သယံဇာတနှင့် ဝန်ဆောင်မှု များ ပြည့်နေမှု

**ဖော်ပြချက်:** AI အေးဂျင့်များက တာဝန်များ ပြီးမြောက်ရန် ကိရိယာများနှင့် ဝန်ဆောင်မှုအမျိုးမျိုးကို ဝင်ရောက်အသုံးပြုနိုင်သည်။ ခိုးယူသူများက အေးဂျင့်မှတဆင့် များပြားသော တောင်းဆိုမှုများ ပို့၍ ဝန်ဆောင်မှုများကို ရိုက်ခတ်နိုင်ပြီး စနစ် ပျက်ကွက်ခြင်း သို့မဟုတ် ကျယ်ပြန့်သော ကုန်ကျမှု ဖြစ်နိုင်သည်။

**လျော့နည်းစေမှု:** AI အေးဂျင့်တစ်ခုက ဝန်ဆောင်မှုတစ်ခုသို့ တောင်းဆိုခွင့်ရှိသော ကိန်းဂဏန်းကို ကန့်သတ်ရန် နည်းပညာ များ ကို တပ်ဆင်ပါ။ စကားပြောပွဲ ရာထူးများနှင့် တောင်းဆိုမှုမြောက်နှုန်းကို ကန့်သတ်ခြင်းကလည်း ဤအမျိုးအစား အတှကျကာကွယ်နိုင်သည်။

### အသိပညာ ရင်းမြစ် မပို့ဆိုး

**ဖော်ပြချက်:** ဤအမျိုးအစား ရိုက်ခတ်မှုသည် AI အေးဂျင့်ကို တိုက်ရိုက် ရိုက်ခတ်ခြင်း မဟုတ်ပေမဲ့ AI အေးဂျင့် အသုံးပြုမည့် အသိပညာရင်းမြစ်နှင့် အခြားဝန်ဆောင်မှုများကို ပစ်မှောက်သည်။ ၎င်းသည် ဒေတာဖျက်ဆီးခြင်း သို့မဟုတ် AI အေးဂျင့်မှ တာဝန်ပြည့်မီစေရန် အသုံးပြုမည့် အချက်အလက်များ အဆိပ်ထုတ်ခြင်း ဖြစ်နိုင်သည်၊ အသုံးပြုသူအပေါ် မမှန်ကန်ပေါ်လွင်သော၊ ကျပန်းသည့်ဖြေရှင်းချက်များ ဖြစ်စေသည်။

**လျော့နည်းစေမှု:** AI အေးဂျင့် Workflow တွင် အသုံးပြုမည့် ဒေတာများကို ပုံမှန်စစ်ဆေးပါ။ ဤဒေတာများကို လူတစ်ဦးချင်းစီသာ လုံခြုံစွာ ထိန်းချုပ်၍ ပြောင်းလဲခွင့်ရှိစေရန် သေချာစေရန် လုပ်ဆောင်ပါက ဤအမျိုးအစား အတှကျမဖြစ်စေရပါ။

### အဆင့်ဆက်အမှားများ

**ဖော်ပြချက်:** AI အေးဂျင့်များသည် ကိရိယာနှင့် ဝန်ဆောင်မှု အသီးသီးကို တာဝန်ဖြည့်ဆောင်ရာတွင် ဝင်ရောက်သည်။ ခိုးယူသူများ၏ အမှားများသည် AI အေးဂျင့် ဆက်နွယ်နေသော အခြားစနစ်များ ပျက်စီးခြင်း ဖြစ်စေပြီး အကာအကွယ် ကို ယူရန် အခက်အခဲများကို ဖြစ်စေသည်။

**လျော့နည်းစေမှု:** AI အေးဂျင့်ကို ကန့်သတ်ထားသော ပတ်ဝန်းကျင်တွင် လုပ်ဆောင်စေရန် နည်းလမ်းဖြစ်ပေါ်စေရန်၊ ဥပမာ၊ Docker container တွင် တာဝန်များ လုပ်ဆောင်စေရန် စနစ်တိုက်ရိုက် တိုက်ခိုက်မှု မဖြစ်စေပါ။ အချို့သော စနစ်များ အမှားဖြင့်တုံ့ပြန်မူ ရှိပါက fallback mechanism များ၊ ပြန်လည်ကြိုးစားမူများ ထည့်သွင်းထားခြင်းက သယံဇာတကျယ်ပြန့်သော စနစ်ပျက်ကွက်မှု မဖြစ်စေရန် ကာကွယ်နိုင်သည်။

## လူကို လုပ်ငန်းစဉ်တွင် ပါဝင်စေရန်

ယုံကြည်စိတ်ချရသော AI အေးဂျင့် စနစ် ဖန်တီးရာတွင် လူနှင့်အတူ လုပ်ငန်းစဉ် ပြုလုပ်ခြင်းသည် ထိရောက်သောနည်းလမ်းတစ်ခုဖြစ်သည်။ ဤသည်က အသုံးပြုသူများအနေနဲ့ အေးဂျင့်များ၏ လည်ပတ်မှုအတွင်း တုံ့ပြန်ချက်ပေးနိုင်စေသည်။ အသုံးပြုသူများသည် multi-agent စနစ်တွင် အေးဂျင့်တစ်ဦးအဖြစ် လုပ်ဆောင်ကာ လည်ပတ်နေသော လုပ်ငန်းစဉ်များကို ခွင့်ပြုခြင်း သို့မဟုတ် ရပ်ဆိုင်းခြင်း အစီအစဉ်များ ပေးနိုင်သည်။

![လူကို လုပ်ငန်းစဉ်တွင် ပါဝင်ခြင်း](../../../translated_images/my/human-in-the-loop.5f0068a678f62f4f.webp)

ဒီအယူအဆကို AutoGen အသုံးပြု၍ ထည့်သွင်းထားသည့် ကုတ်အပိုင်း -

```python

# အိုင်ဂျင့်များကိုဖန်တီးပါ။
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # console မှ user input ရယူရန် input() အသုံးပြုပါ။

# user မှ "APPROVE" ဟုပြောသောအခါ ပြောဆိုမှုကိုပြီးဆုံးစေမည့် သတ်မှတ်ချက်ကိုဖန်တီးပါ။
termination = TextMentionTermination("APPROVE")

# အဖွဲ့ကိုဖန်တီးပါ။
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# ပြောဆိုမှုကိုRunလုပ်ပြီး console သို့ stream ပြပါ။
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# script မှာ run လိုသောအခါ asyncio.run(...) ကိုအသုံးပြုပါ။
await Console(stream)

```

## အဆုံးသတ်

ယုံကြည်စိတ်ချရသော AI အေးဂျင့်များ တည်ဆောက်ရန် ဂရုပြု၍ ဒီဇိုင်းရေးဆွဲ၊ လုံခြုံရေးအတွက် ပဋိညာဉ်စနစ်များ ဖြည့်ဆည်းပြီး အဆက်အသွယ်တိုးတက်အောင်လုပ်ဆောင်ရမည်။ ဖွဲ့စည်းထားသည့် meta prompting စနစ်များ၊ ဖြစ်နိုင်သည့် အန္တရာယ်များ နားလည်ခြင်းနှင့် လျော့နည်းစေခြင်း များကို ကျင့်သုံးခြင်းအားဖြင့် လုံခြုံပြီး ထိရောက်သော AI အေးဂျင့်များ ဖန်တီးနိုင်မည်။ ထို့ပြင် လူကို လုပ်ငန်းစဉ်တွင် ပါဝင်စေခြင်းက AI အေးဂျင့်များ သုံးစွဲသူ၏ လိုအပ်ချက်များနှင့် ကိုက်ညီမှုရှိစေရန်နှင့် အန္တရာယ်များ လျော့နည်းစေရန် အရေးပါသည်။ AI နည်းပညာ တိုးတက်လာစဉ်တွင် လုံခြုံမှု၊ ကိုယ်ရေးကာကွယ်မှုနှင့် သမာသမားကျင့်ဝတ်များအပေါ် ပိုမိုဂရုစိုက်မှု ထိန်းသိမ်းခြင်းက AI မောင်းနှင်သော စနစ်များတွင် ယုံကြည်စိတ်ချရမှုနှင့် ယုံကြည်မှု တည်ဆောက်ရာတွင် အရေးပါသည်။

### ယုံကြည်စိတ်ချရသော AI အေးဂျင့်များ တည်ဆောက်ခြင်းအပေါ် ရှေးရွေး မေးခွန်းများရှိပါသလား?

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) တွင်၀င်ရောက်ပြီး သင်ယူသူများနှင့်တွေ့ဆုံ၊ အလုပ်ရုံးအချိန်များ တက်ရောက်ပြီး AI အေးဂျင့် မေးခွန်းများ ဖြေကြားပေးမှု ရယူပါ။

## နောက်ထပ် အရင်းအမြစ်များ

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">တာဝန်ယူမှုရှိသော AI ပြောကြားချက်အကျဉ်း</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">ဂျီနေရတစ် AI မော်ဒယ်များနှင့် AI အက်ပလီကေးရှင်းများ သုံးသပ်ခြင်း</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">လုံခြုံမှု စနစ်သတိပေးစာများ</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">အန္တရာယ် သုံးသပ်မှု ဖောင်တမ်း</a>

## ယခင် သင်ခန်းစာ

[Agentic RAG](../05-agentic-rag/README.md)

## နောက်တစ်ခု သင်ခန်းစာ

[အစီအစဉ်ဒီဇိုင်းပုံစံ](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**အရေးကြီးကြေညာချက်**  
ဤစာတမ်းကို AI ဘာသာပြန်ဝန်ဆောင်မှုဖြစ်သည့် [Co-op Translator](https://github.com/Azure/co-op-translator) အသုံးပြု၍ ဘာသာပြန်ထားပါသည်။ ကျွန်ုပ်တို့သည် မှန်ကန်မှုအတွက် ကြိုးပမ်းသော်လည်း စက်ယန္တရားဘာသာပြန်မှုများတွင် အမှားများ သို့မဟုတ် မှားယွင်းချက်များ ပါဝင်နိုင်သည်ကို သတိပြုပါ။ ပထမ ဗန်းဘာသာဖြင့် ရှိသော မူရင်းစာတမ်းကို ထိပ်တန်းအချုပ်အစိုးအရ အချက်အလက်ဖြစ်သည်ဟု သတ်မှတ်ပါ။ အရေးကြီးသောအချက်အလက်များအတွက် လူနည်းပြ သဘာဝဘာသာပြန်အကောင်းဆုံးဖြစ်သည်။ ဤဘာသာပြန်ချက်ကိုအသုံးပြုမှုမှ ဖြစ်ပေါ်နိုင်သည့် မသေချာမှုများ သို့မဟုတ် မှားယွင်းစိတ်ထားများအတွက် ကျွန်ုပ်တို့သည် တာဝန်မဲ့ပါ။
<!-- CO-OP TRANSLATOR DISCLAIMER END -->