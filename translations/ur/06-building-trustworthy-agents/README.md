[![قابلِ اعتماد AI ایجنٹس](../../../translated_images/ur/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(اوپر دی گئی تصویر پر کلک کریں تاکہ اس سبق کی ویڈیو دیکھی جا سکے)_

# قابلِ اعتماد AI ایجنٹس بنانا

## تعارف

اس سبق میں درج ذیل موضوعات شامل ہوں گے:

- محفوظ اور مؤثر AI ایجنٹس کیسے بنائے اور تعینات کیے جائیں
- AI ایجنٹس تیار کرتے وقت اہم سیکیورٹی پہلو
- AI ایجنٹس تیار کرتے وقت ڈیٹا اور صارف کی پرائیویسی کو برقرار رکھنے کے طریقے

## تعلیمی مقاصد

اس سبق کو مکمل کرنے کے بعد، آپ جان سکیں گے کہ کیسے:

- AI ایجنٹس بناتے وقت خطرات کی نشاندہی اور انھیں کم کیا جائے۔
- ڈیٹا اور رسائی کو مناسب طریقے سے منظم کرنے کے لیے سیکیورٹی اقدامات نافذ کیے جائیں۔
- ایسے AI ایجنٹس بنائے جائیں جو ڈیٹا کی پرائیویسی برقرار رکھیں اور صارف کو اعلیٰ معیار کا تجربہ فراہم کریں۔

## حفاظت

آئیے پہلے محفوظ ایجنٹک ایپلیکیشنز بنانے پر نظر ڈالتے ہیں۔ حفاظت کا مطلب ہے کہ AI ایجنٹ اپنی طے شدہ کارکردگی کے مطابق عمل کرے۔ ایجنٹک ایپلیکیشنز بنانے والوں کے طور پر، ہمارے پاس حفاظت کو زیادہ سے زیادہ کرنے کے لیے طریقے اور اوزار موجود ہیں:

### سسٹم میسج فریم ورک بنانا

اگر آپ نے کبھی بڑے زبان کے ماڈلز (LLMs) استعمال کرکے AI ایپلیکیشن بنائی ہے تو آپ جانتے ہیں کہ ایک مضبوط سسٹم پرامپٹ یا سسٹم میسج ڈیزائن کرنا کتنا اہم ہے۔ یہ پرامپٹس میٹا قواعد، ہدایات، اور رہنما اصول طے کرتے ہیں کہ LLM صارف اور ڈیٹا کے ساتھ کیسے تعامل کرے گا۔

AI ایجنٹس کے لیے سسٹم پرامپٹ اور بھی زیادہ اہم ہوتا ہے کیونکہ AI ایجنٹس کو ہمارے بنائے گئے مخصوص کاموں کو مکمل کرنے کے لیے بہت واضح ہدایات درکار ہوں گی۔

اسکیل ایبل سسٹم پرامپٹس بنانے کے لیے، ہم اپنے ایپلیکیشن میں ایک یا زیادہ ایجنٹس بنانے کے لیے سسٹم میسج فریم ورک استعمال کرسکتے ہیں:

![سسٹم میسج فریم ورک بنانا](../../../translated_images/ur/system-message-framework.3a97368c92d11d68.webp)

#### مرحلہ 1: ایک میٹا سسٹم میسج بنائیں

میٹا پرامپٹ کو LLM اس لیے استعمال کرے گا تاکہ ہمارے بنائے گئے ایجنٹس کے لیے سسٹم پرامپٹس تیار کرے۔ ہم اسے ایک ٹیمپلیٹ کے طور پر ڈیزائن کرتے ہیں تاکہ ضرورت پڑنے پر مؤثر طریقے سے متعدد ایجنٹس بنائے جا سکیں۔

یہاں ایک مثال ہے جو ہم LLM کو دے سکتے ہیں:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### مرحلہ 2: ایک بنیادی پرامپٹ بنائیں

اگلا قدم AI ایجنٹ کی وضاحت کے لیے ایک بنیادی پرامپٹ بنانا ہے۔ اس میں آپ کو ایجنٹ کا کردار، وہ کام جنہیں ایجنٹ پورا کرے گا، اور ایجنٹ کی کوئی دیگر ذمہ داریاں شامل کرنی چاہئیں۔

یہاں ایک مثال ہے:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### مرحلہ 3: بنیادی سسٹم میسج LLM کو فراہم کریں

اب ہم اس سسٹم میسج کو بہتر بنا سکتے ہیں، میٹا سسٹم میسج کو بطور سسٹم میسج فراہم کرکے اور ہمارا بنیادی سسٹم میسج شامل کرکے۔

یہ ایک ایسا سسٹم میسج تیار کرے گا جو ہمارے AI ایجنٹس کی رہنمائی کے لیے بہتر ڈیزائن کیا گیا ہوگا:

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

#### مرحلہ 4: تکرار کریں اور بہتر بنائیں

اس سسٹم میسج فریم ورک کی قدر یہ ہے کہ ایک سے زیادہ ایجنٹس کے لیے سسٹم میسجز بنانا آسان ہوجاتا ہے اور ساتھ ہی وقت کے ساتھ اپنے سسٹم میسجز کو بہتر بنایا جا سکتا ہے۔ عام طور پر آپ کا پہلا بنایا ہوا سسٹم میسج پوری صورتِ حال کے لیے پہلی بار مکمل طور پر کام نہیں کرے گا۔ بنیادی سسٹم میسج میں چھوٹے ترامیم کر کے اور اسے سسٹم کے ذریعے چلانے سے آپ نتائج کا موازنہ اور جائزہ لے سکتے ہیں۔

## خطرات کو سمجھنا

قابلِ اعتماد AI ایجنٹس بنانے کے لیے، یہ سمجھنا اور خطرات و دھمکیوں کو کم کرنا ضروری ہے جو آپ کے AI ایجنٹ کو متاثر کر سکتی ہیں۔ آئیے AI ایجنٹس کو لاحق کچھ مختلف خطرات اور ان کے لیے بہتر منصوبہ بندی اور تیاری کے بارے میں جانیں۔

![خطرات کو سمجھنا](../../../translated_images/ur/understanding-threats.89edeada8a97fc0f.webp)

### کام اور ہدایات

**تفصیل:** حملہ آور کوشش کرتے ہیں کہ پرامپٹنگ یا ان پٹس میں ہیر پھیر کرکے AI ایجنٹ کی ہدایات یا مقاصد بدل دیں۔

**تدارک**: نقصان دہ پرامپٹس کو AI ایجنٹ کے پروسیس ہونے سے پہلے معلوم کرنے کے لیے توثیقی چیکس اور ان پٹ فلٹرز نافذ کریں۔ چونکہ یہ حملے عام طور پر ایجنٹ کے ساتھ بار بار تعامل کے ذریعے ہوتے ہیں، لہٰذا گفتگو میں مرحلوں کی تعداد محدود کرنا بھی ان حملوں کو روکنے کا ایک طریقہ ہے۔

### اہم نظاموں تک رسائی

**Description**: اگر کسی AI ایجنٹ کو حساس ڈیٹا رکھنے والے نظاموں اور خدمات تک رسائی حاصل ہو تو حملہ آور ایجنٹ اور ان خدمات کے درمیان مواصلت کو متاثر کر سکتے ہیں۔ یہ براہِ راست حملے یا ایجنٹ کے ذریعے ان نظاموں کے بارے میں معلومات حاصل کرنے کی بالواسطہ کوششیں ہو سکتی ہیں۔

**Mitigation**: AI ایجنٹس کو ان نظاموں تک رسائی صرف ضرورت کے تحت دی جانی چاہیے تاکہ ان قسم کے حملوں سے بچا جا سکے۔ ایجنٹ اور سسٹم کے درمیان مواصلت بھی محفوظ ہونی چاہیے۔ اس معلومات کے تحفظ کے لیے توثیق اور رسائی کنٹرول نافذ کریں۔

### وسائل اور خدمات کا اوورلوڈ

**Description:** AI ایجنٹس مختلف ٹولز اور خدمات تک رسائی حاصل کر کے کام مکمل کرتے ہیں۔ حملہ آور اس صلاحیت کا فائدہ اٹھا کر AI ایجنٹ کے ذریعے ان خدمات پر بڑی تعداد میں درخواستیں بھیج کر حملہ کر سکتے ہیں، جس سے نظام ناکام ہو سکتا ہے یا بہت زیادہ لاگت آ سکتی ہے۔

**Mitigation:** ایسی پالیسیز نافذ کریں جو ایک AI ایجنٹ کی کسی سروس کو بھیجی جانے والی درخواستوں کی تعداد محدود کریں۔ گفتگو کے مرحلوں اور AI ایجنٹ کو بھیجی جانے والی درخواستوں کی تعداد محدود کرنا بھی ان حملوں کو روکنے کا ایک طریقہ ہے۔

### نالج بیس کو زہریلا کرنا

**Description:** اس قسم کا حملہ براہِ راست AI ایجنٹ کو نشانہ نہیں بناتا بلکہ اس نالج بیس اور دیگر خدمات کو ہدف بناتا ہے جو AI ایجنٹ اپنے کاموں کے لیے استعمال کرے گا۔ اس میں وہ ڈیٹا یا معلومات خراب کرنا شامل ہو سکتا ہے جو AI ایجنٹ کسی کام کو مکمل کرنے کے لیے استعمال کرتا ہے، جس کے نتیجے میں صارف کو متعصب یا غیر متوقع جوابات مل سکتے ہیں۔

**Mitigation:** AI ایجنٹ کے ورک فلو میں استعمال ہونے والے ڈیٹا کی باقاعدہ جانچ کریں۔ اس ڈیٹا تک رسائی محفوظ رکھیں اور اسے صرف قابلِ اعتماد افراد ہی تبدیل کریں تاکہ اس قسم کے حملوں سے بچا جا سکے۔

### زنجیروار غلطیاں

**Description:** AI ایجنٹس کام مکمل کرنے کے لیے مختلف ٹولز اور خدمات تک رسائی حاصل کرتے ہیں۔ حملہ آوروں کی وجہ سے پیدا ہونے والی غلطیاں دیگر نظاموں کی ناکامیوں کا سبب بن سکتی ہیں جن سے AI ایجنٹ منسلک ہوتا ہے، جس سے حملہ زیادہ وسیع اور حل کرنے میں مشکل ہو جاتا ہے۔

**Mitigation**: اس سے بچنے کا ایک طریقہ یہ ہے کہ AI ایجنٹ کو محدود ماحول میں چلایا جائے، جیسے Docker کنٹینر میں کام کرنا، تاکہ براہِ راست نظامی حملوں سے بچا جا سکے۔ جب مخصوص نظام غلطی کے ساتھ ردِ عمل دیں تو بیک اپ میکانزم اور دوبارہ کوشش کرنے کی منطق بنائیں تاکہ بڑے سسٹم فالٹس سے بچا جا سکے۔

## انسانی مداخلت

قابلِ اعتماد AI ایجنٹ سسٹمز بنانے کا ایک اور مؤثر طریقہ انسانی مداخلت (Human-in-the-Loop) کا استعمال ہے۔ اس سے ایک ایسا بہاؤ بنتا ہے جہاں صارفین رن کے دوران ایجنٹس کو فیڈ بیک دے سکتے ہیں۔ صارفین عملاً ایک کثیر-ایجنٹ سسٹم میں ایجنٹس کی طرح کام کرتے ہیں اور رننگ پراسیس کی منظوری یا ختم کرنے کے ذریعے دخل اندازی کرتے ہیں۔

![لوپ میں انسان](../../../translated_images/ur/human-in-the-loop.5f0068a678f62f4f.webp)

یہاں AutoGen استعمال کرتے ہوئے ایک کوڈ اسنیپٹ دیا گیا ہے تاکہ دکھایا جا سکے کہ یہ تصور کیسے نافذ کیا جاتا ہے:

```python

# ایجنٹس بنائیں۔
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # کنسول سے صارف کی ان پٹ حاصل کرنے کے لیے input() استعمال کریں۔

# اختتامی شرط بنائیں جو گفتگو ختم کر دے جب صارف "APPROVE" کہے۔
termination = TextMentionTermination("APPROVE")

# ٹیم بنائیں۔
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# گفتگو چلائیں اور اسے کنسول پر اسٹریم کریں۔
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# اسکرپٹ میں چلاتے وقت asyncio.run(...) استعمال کریں۔
await Console(stream)

```

## نتیجہ

قابلِ اعتماد AI ایجنٹس بنانے کے لیے احتیاط سے ڈیزائن، مضبوط سیکیورٹی اقدامات، اور مسلسل تکرار ضروری ہے۔ منظم میٹا پرامپٹنگ سسٹمز لاگو کرکے، ممکنہ خطرات کو سمجھ کر، اور تدارکی حکمتِ عملیاں اپناتے ہوئے، ڈویلپر ایسے AI ایجنٹس بنا سکتے ہیں جو محفوظ اور مؤثر دونوں ہوں۔ مزید برآں، انسانی مداخلت کو شامل کرنے سے یہ یقینی بنتا ہے کہ AI ایجنٹس صارفین کی ضروریات کے مطابق رہیں اور خطرات کم ہوں۔ جیسے جیسے AI ترقی کرتا رہے گا، سیکیورٹی، پرائیویسی، اور اخلاقی پہلوؤں پر پیش قدمی برقرار رکھنا AI پر مبنی سسٹمز میں بھروسہ اور اعتبار پیدا کرنے کی کلید ہوگا۔

### قابلِ اعتماد AI ایجنٹس بنانے کے بارے میں مزید سوالات ہیں؟

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) میں شامل ہوں تاکہ دوسرے سیکھنے والوں سے ملیں، آفس آورز میں شرکت کریں اور اپنے AI ایجنٹس سے متعلق سوالات کے جوابات حاصل کریں۔

## اضافی وسائل

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">ذمہ دار AI کا جائزہ</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">جنریٹو AI ماڈلز اور AI ایپلیکیشنز کا جائزہ</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">حفاظتی سسٹم میسجز</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">رسک اسیسمنٹ ٹیمپلیٹ</a>

## پچھلا سبق

[ایجنٹک RAG](../05-agentic-rag/README.md)

## اگلا سبق

[منصوبہ بندی ڈیزائن پیٹرن](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
بیانِ دستبرداری:
اس دستاویز کا ترجمہ AI ترجمہ سروس Co‑op Translator (https://github.com/Azure/co-op-translator) کے ذریعے کیا گیا ہے۔ اگرچہ ہم درستگی کے لیے کوشاں ہیں، براہِ کرم آگاہ رہیں کہ خودکار ترجموں میں غلطیاں یا نواقص ہو سکتے ہیں۔ اصل دستاویز کو اس کی مادری زبان میں معتبر ماخذ سمجھا جانا چاہیے۔ اہم اور حساس معلومات کے لیے پیشہ ور انسانی ترجمہ کی سفارش کی جاتی ہے۔ ہم اس ترجمے کے استعمال سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تعبیر کے لیے ذمہ دار نہیں ہوں گے۔
<!-- CO-OP TRANSLATOR DISCLAIMER END -->