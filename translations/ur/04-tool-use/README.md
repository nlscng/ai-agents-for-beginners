[![اچھے AI ایجنٹس کیسے ڈیزائن کریں](../../../translated_images/ur/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(اوپر موجود تصویر پر کلک کریں تاکہ اس سبق کی ویڈیو دیکھی جا سکے)_

# ٹول استعمال ڈیزائن پیٹرن

ٹولز دلچسپ ہیں کیونکہ وہ AI ایجنٹس کو وسیع تر صلاحیتوں کا اختیار دیتے ہیں۔ ایک ایجنٹ کے پاس محدود اعمال کا سیٹ رکھنے کے بجائے، ایک ٹول شامل کرنے سے ایجنٹ اب مختلف قسم کے اعمال انجام دے سکتا ہے۔ اس باب میں، ہم ٹول استعمال ڈیزائن پیٹرن پر نظر ڈالیں گے، جو بیان کرتا ہے کہ AI ایجنٹس مخصوص ٹولز استعمال کرکے اپنے مقاصد کیسے حاصل کر سکتے ہیں۔

## تعارف

اس سبق میں ہم درج ذیل سوالات کے جواب تلاش کرنے کی کوشش کر رہے ہیں:

- ٹول استعمال ڈیزائن پیٹرن کیا ہے؟
- کن استعمال کے معاملات (use cases) پر اسے لاگو کیا جا سکتا ہے؟
- اس ڈیزائن پیٹرن کو نافذ کرنے کے لئے کن عناصر/بلڈنگ بلاکس کی ضرورت ہے؟
- قابلِ بھروسہ AI ایجنٹس بنانے کے لئے ٹول استعمال ڈیزائن پیٹرن استعمال کرتے ہوئے کن خصوصی امور پر غور کرنا چاہیے؟

## سیکھنے کے مقاصد

اس سبق کو مکمل کرنے کے بعد، آپ قابلِ عمل ہوں گے:

- ٹول استعمال ڈیزائن پیٹرن اور اس کے مقصد کی تعریف کرنا۔
- ایسے استعمال کے معاملات کی نشاندہی کرنا جہاں ٹول استعمال ڈیزائن پیٹرن قابلِ اطلاق ہو۔
- ڈیزائن پیٹرن کو نافذ کرنے کے لئے درکار اہم عناصر کو سمجھنا۔
- اس ڈیزائن پیٹرن استعمال کرنے والے AI ایجنٹس میں قابلِ بھروسگی برقرار رکھنے کے لیے غور کرنے والے امور کو پہچاننا۔

## ٹول استعمال ڈیزائن پیٹرن کیا ہے؟

**ٹول استعمال ڈیزائن پیٹرن** کا مرکزی مقصد LLMs کو بیرونی ٹولز کے ساتھ تعامل کرنے کی صلاحیت دینا ہے تاکہ مخصوص مقاصد حاصل کیے جا سکیں۔ ٹولز ایسے کوڈ ہیں جنہیں ایک ایجنٹ چلाकर اعمال انجام دے سکتا ہے۔ ایک ٹول ایک سادہ فنکشن ہو سکتا ہے جیسے کیلکولیٹر، یا کوئی تیسری پارٹی سروس کال جیسا کہ اسٹاک قیمت کی تلاش یا موسمیاتی پیشگوئی۔ AI ایجنٹس کے سیاق میں، ٹولز اس طرح ڈیزائن کیے جاتے ہیں کہ وہ **ماڈل کی طرف سے تیار کردہ فنکشن کالز** کے جواب میں ایجنٹس کے ذریعے چلائے جائیں۔

## کن استعمال کے معاملات پر اسے لاگو کیا جا سکتا ہے؟

AI ایجنٹس ٹولز کا فائدہ اٹھا کر پیچیدہ کام مکمل کر سکتے ہیں، معلومات حاصل کر سکتے ہیں، یا فیصلے کر سکتے ہیں۔ ٹول استعمال ڈیزائن پیٹرن اکثر ایسی صورتوں میں استعمال ہوتا ہے جہاں بیرونی نظاموں کے ساتھ متحرک تعامل درکار ہوتا ہے، جیسے ڈیٹا بیس، ویب سروسز، یا کوڈ انٹرپریٹرز۔ یہ صلاحیت مختلف استعمال کے معاملات کے لیے مفید ہے جن میں شامل ہیں:

- **متحرک معلومات بازیافت (Dynamic Information Retrieval):** ایجنٹس بیرونی APIs یا ڈیٹا بیسز سے تازہ ترین ڈیٹا حاصل کر سکتے ہیں (مثلاً، ڈیٹا تجزیہ کے لیے ایک SQLite ڈیٹا بیس سے سوال کرنا، اسٹاک کی قیمتیں یا موسم کی معلومات حاصل کرنا)۔
- **کوڈ کا نفاذ اور تفسیر (Code Execution and Interpretation):** ایجنٹس ریاضیاتی مسائل حل کرنے، رپورٹس تیار کرنے، یا سیمولیشنز کرنے کے لیے کوڈ یا اسکرپٹس چلا سکتے ہیں۔
- **ورک فلو خودکار کرنا (Workflow Automation):** ٹاسک شیڈولرز، ای میل سروسز، یا ڈیٹا پائپ لائنز جیسے ٹولز کو ضم کرکے بار بار یا کثیر مرحلہ ورک فلو کو خودکار بنانا۔
- **کسٹمر سپورٹ (Customer Support):** ایجنٹس CRM سسٹمز، ٹکٹنگ پلیٹ فارمز، یا نالج بیسس سے تعامل کر کے صارف کے سوالات کا حل فراہم کر سکتے ہیں۔
- **مواد کی تخلیق اور تدوین (Content Generation and Editing):** ایجنٹس گرائمر چیکرز، ٹیکسٹ سمریز، یا مواد کی حفاظت جانچنے والے ٹولز کا استعمال کر کے مواد سازی کے کاموں میں مدد کر سکتے ہیں۔

## ٹول استعمال ڈیزائن پیٹرن کو نافذ کرنے کے لئے کن عناصر/بلڈنگ بلاکس کی ضرورت ہے؟

یہ بلڈنگ بلاکس AI ایجنٹ کو مختلف قسم کے کام انجام دینے کی اجازت دیتے ہیں۔ آئیے ٹول استعمال ڈیزائن پیٹرن کو نافذ کرنے کے لئے درکار اہم عناصر پر نظر ڈالیں:

- **فنکشن/ٹول اسکیمائیں (Function/Tool Schemas):** دستیاب ٹولز کی تفصیلی تعریفیں، بشمول فنکشن کا نام، مقصد، درکار پیرا میٹرز، اور متوقع آؤٹ پٹس۔ یہ اسکیمائیں LLM کو سمجھنے کے قابل بناتی ہیں کہ کون سے ٹولز دستیاب ہیں اور درست درخواستیں کیسے بنائی جائیں۔
- **فنکشن نفاذ منطق (Function Execution Logic):** یہ طے کرتا ہے کہ صارف کی نیت اور گفتگو کے سیاق و سباق کی بنیاد پر ٹولز کب اور کیسے بلائے جائیں گے۔ اس میں پلانر ماڈیولز، روٹنگ میکنزمز، یا مشروط فلو شامل ہو سکتے ہیں جو متحرک طور پر ٹول کے استعمال کا فیصلہ کرتے ہیں۔
- **پیغام ہینڈلنگ سسٹم (Message Handling System):** وہ اجزاء جو صارف ان پٹس، LLM جوابات، ٹول کالز، اور ٹول آؤٹ پٹس کے درمیان بات چیت کے بہاؤ کو منظم کرتے ہیں۔
- **ٹول انٹیگریشن فریم ورک (Tool Integration Framework):** وہ انفراسٹرکچر جو ایجنٹ کو مختلف ٹولز سے جوڑتا ہے، چاہے وہ سادہ فنکشنز ہوں یا پیچیدہ بیرونی سروسز۔
- **خرابی ہینڈلنگ اور توثیق (Error Handling & Validation):** ٹول نفاذ میں ناکامیوں کو سنبھالنے، پیرا میٹرز کی توثیق کرنے، اور غیر متوقع جوابات کا انتظام کرنے کے طریقے۔
- **حالت کا انتظام (State Management):** گفتگو کے سیاق و سباق، پچھلے ٹول تعاملات، اور مستقل ڈیٹا کو ٹریک کرتا ہے تاکہ کثیر مورچے تعاملات میں ہم آہنگی برقرار رہے۔

اگلا، آئیے فنکشن/ٹول کالنگ کو مزید تفصیل سے دیکھیں۔
 
### فنکشن/ٹول کالنگ

فنکشن کالنگ وہ بنیادی طریقہ ہے جس کے ذریعے ہم Large Language Models (LLMs) کو ٹولز کے ساتھ تعامل کرنے کے قابل بناتے ہیں۔ آپ اکثر 'Function' اور 'Tool' کو باری باری دیکھیں گے کیونکہ 'functions' (قابلِ دوبارہ استعمال کوڈ بلاکس) وہ 'tools' ہیں جنہیں ایجنٹس کام انجام دینے کے لیے استعمال کرتے ہیں۔ کسی فنکشن کے کوڈ کو چلانے کے لیے، ایک LLM کو صارف کی درخواست کا موازنہ فنکشن کی تفصیل سے کرنا ہوگا۔ اس کے لیے دستیاب تمام فنکشنز کی تفصیلات پر مشتمل ایک اسکیمہ ماڈل کو بھیجی جاتی ہے۔ پھر LLM اس کام کے لیے سب سے مناسب فنکشن کا انتخاب کرتا ہے اور اس کا نام اور دلائل (arguments) واپس کرتا ہے۔ منتخب شدہ فنکشن کو چلایا جاتا ہے، اس کا جواب LLM کو بھیجا جاتا ہے، جو اس معلومات کو صارف کی درخواست کے جواب میں استعمال کرتا ہے۔

ڈیولپرز کے لیے ایجنٹس کے لیے فنکشن کالنگ نافذ کرنے کے لیے، آپ کو درکار ہوگا:

1. ایک LLM ماڈل جو فنکشن کالنگ کو سپورٹ کرے
2. فنکشن کی تفصیلات پر مشتمل ایک اسکیمہ
3. ہر بیان شدہ فنکشن کے لیے کوڈ

مثال کے طور پر کسی شہر میں موجودہ وقت حاصل کرنے کی مثال لیتے ہیں:

1. **ایسا LLM ابتدائیہ کریں جو فنکشن کالنگ کو سپورٹ کرے:**

    تمام ماڈلز فنکشن کالنگ کو سپورٹ نہیں کرتے، اس لیے یہ جانچنا ضروری ہے کہ آپ جو LLM استعمال کر رہے ہیں وہ یہ خصوصیت فراہم کرتا ہے۔     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> فنکشن کالنگ کو سپورٹ کرتا ہے۔ ہم Azure OpenAI کلائنٹ کو شروع کرکے آغاز کر سکتے ہیں۔ 

    ```python
    # Azure OpenAI کلائنٹ کو ابتدائی طور پر ترتیب دیں
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **فنکشن اسکیمہ بنائیں (Create a Function Schema):**

    اگلا قدم ایک JSON اسکیمہ کی تعریف کرنا ہے جو فنکشن کا نام، فنکشن کے کام کی وضاحت، اور فنکشن پیرا میٹرز کے نام اور وضاحتیں شامل کرے گا۔
    پھر ہم اس اسکیمہ کو پہلے بنائے گئے کلائنٹ کو بھیجیں گے، ساتھ ہی صارف کی وہ درخواست جو سان فرانسسکو میں وقت معلوم کرنے کے لیے ہے۔ اہم بات یہ ہے کہ **ٹول کال** وہ چیز ہے جو واپس آتی ہے، **نہ کہ** سوال کا حتمی جواب۔ جیسے پہلے ذکر کیا گیا، LLM اس کام کے لیے منتخب کردہ فنکشن کا نام اور اسے دیے جانے والے دلائل واپس کرتا ہے۔

    ```python
    # ماڈل کے پڑھنے کے لیے فنکشن کی تفصیل
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
  
    # ابتدائی صارف کا پیغام
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # پہلا API کال: ماڈل سے کہیں کہ فنکشن استعمال کرے
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # ماڈل کے جواب پر عمل کریں
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **وہ فنکشن کوڈ جو کام انجام دینے کے لیے درکار ہے:**

    اب جب کہ LLM نے انتخاب کر لیا ہے کہ کون سا فنکشن چلانا ہے، تو اس فنکشن کو انجام دینے والا کوڈ نافذ اور چلایا جانا چاہیے۔
    ہم Python میں موجودہ وقت حاصل کرنے کا کوڈ نافذ کر سکتے ہیں۔ ہمیں response_message سے نام اور دلائل نکالنے کے لیے بھی کوڈ لکھنے کی ضرورت ہوگی تاکہ حتمی نتیجہ حاصل کیا جا سکے۔

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
     # فنکشن کالز کو سنبھالیں
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
  
      # دوسری API کال: ماڈل سے حتمی جواب حاصل کریں
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

فنکشن کالنگ اکثر، اگر تمام ایجنٹ ٹول استعمال ڈیزائن کا مرکز نہ بھی ہو، تو اس کا دل ہوتی ہے، تاہم اسے شروع سے نافذ کرنا بعض اوقات مشکل ہو سکتا ہے۔
جیسا کہ ہم نے [سبق 2](../../../02-explore-agentic-frameworks) میں سیکھا، agentic فریم ورکس ہمیں ٹول استعمال کو نافذ کرنے کے لیے پہلے سے تیار شدہ بلڈنگ بلاکس فراہم کرتے ہیں۔
 
## ایجنٹک فریم ورکس کے ساتھ ٹول استعمال کی مثالیں

درج ذیل کچھ مثالیں ہیں کہ آپ مختلف agentic فریم ورکس استعمال کرتے ہوئے ٹول استعمال ڈیزائن پیٹرن کو کیسے نافذ کر سکتے ہیں:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> ایک اوپن سورس AI فریم ورک ہے جو .NET، Python، اور Java ڈیولپرز کے لیے LLMs کے ساتھ کام کرنے کو آسان بناتا ہے۔ یہ فنکشن کالنگ کے عمل کو آسان بناتا ہے کیونکہ یہ آپ کے فنکشنز اور ان کے پیرا میٹرز کو ماڈل کے لیے خود بخود بیان کرتا ہے اس عمل کے ذریعے جسے <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">سیریلائز کرنا</a> کہا جاتا ہے۔ یہ ماڈل اور آپ کے کوڈ کے درمیان پیچھے اور آگے کی رابطے کو بھی سنبھالتا ہے۔ Semantic Kernel جیسے agentic فریم ورک کے استعمال کا ایک اور فائدہ یہ ہے کہ یہ آپ کو پہلے سے بنے ہوئے ٹولز تک رسائی دیتا ہے جیسے <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">فائل سرچ</a> اور <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">کوڈ انٹرپرٹر</a>۔

مندرجہ ذیل خاکہ Semantic Kernel کے ساتھ فنکشن کالنگ کے عمل کی وضاحت کرتا ہے:

![فنکشن کالنگ](../../../translated_images/ur/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernel میں فنکشنز/ٹولز کو <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">پلگ انز</a> کہا جاتا ہے۔ ہم پہلے دیکھے گئے `get_current_time` فنکشن کو ایک پلگ ان میں تبدیل کر سکتے ہیں اسے ایک کلاس میں رکھنے سے جس میں وہ فنکشن شامل ہو۔ ہم `kernel_function` ڈیکوریٹر کو بھی امپورٹ کر سکتے ہیں، جو فنکشن کی وضاحت لیتا ہے۔ جب آپ پھر GetCurrentTimePlugin کے ساتھ ایک کرنل بناتے ہیں، تو کرنل خود بخود فنکشن اور اس کے پیرا میٹرز کو سیریلائز کرے گا، اور ماڈل کو بھیجنے کے لیے اسکیمہ تیار کرے گا۔

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

# کرنل بنائیں
kernel = Kernel()

# پلگ ان بنائیں
get_current_time_plugin = GetCurrentTimePlugin(location)

# پلگ ان کو کرنل میں شامل کریں
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> ایک جدید agentic فریم ورک ہے جو ڈیولپرز کو محفوظ طریقے سے اعلیٰ معیار، توسیع پذیری والے AI ایجنٹس بنانے، تعینات کرنے، اور اسکیل کرنے کے قابل بناتا ہے بغیر اس کے کہ انہیں نیچے موجود کمپیوٹ اور اسٹوریج وسائل کا انتظام کرنا پڑے۔ یہ خاص طور پر انٹرپرائز ایپلیکیشنز کے لیے مفید ہے کیونکہ یہ ایک مکمل طور پر منیجڈ سروس ہے جس میں انٹرپرائز گریڈ سیکیورٹی موجود ہے۔

براہِ راست LLM API کے ساتھ ڈیولپ کرنے کے مقابلے میں، Azure AI Agent Service کچھ فوائد فراہم کرتا ہے، جن میں شامل ہیں:

- خودکار ٹول کالنگ – اب ٹول کال کو پارس کرنے، ٹول کو بلاوا بھیجنے، اور جواب کو ہینڈل کرنے کی ضرورت نہیں؛ یہ سب سرور سائڈ پر ہو جاتا ہے
- محفوظ طریقے سے منظم ڈیٹا – اپنی گفتگو کی حالت کو خود انتظام کرنے کے بجائے، آپ `threads` پر انحصار کر سکتے ہیں تاکہ آپ کو درکار ساری معلومات محفوظ رہیں
- تیار شدہ ٹولز – ایسے ٹولز جو آپ کو آپ کے ڈیٹا سورسز کے ساتھ تعامل کرنے کے لیے دستیاب ہیں، جیسے Bing، Azure AI Search، اور Azure Functions۔

Azure AI Agent Service میں دستیاب ٹولز کو دو زمروں میں تقسیم کیا جا سکتا ہے:

1. نالج ٹولز (Knowledge Tools):
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing سرچ کے ساتھ گراؤنڈنگ</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">فائل سرچ</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. ایکشن ٹولز (Action Tools):
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">فنکشن کالنگ</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">کوڈ انٹرپرٹر</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI تعریف شدہ ٹولز</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service ہمیں ان ٹولز کو بطور `toolset` ایک ساتھ استعمال کرنے کی اجازت دیتا ہے۔ یہ `threads` کا بھی استعمال کرتا ہے جو کسی مخصوص گفتگو کے پیغامات کی تاریخ کو ٹریک رکھتے ہیں۔

فرض کریں آپ Contoso نامی کمپنی میں ایک سیلز ایجنٹ ہیں۔ آپ ایک گفتگو پر مبنی ایجنٹ تیار کرنا چاہتے ہیں جو آپ کے سیلز ڈیٹا کے بارے میں سوالات کا جواب دے سکے۔

ذیل میں تصویر دکھاتی ہے کہ آپ Azure AI Agent Service کو کس طرح استعمال کر سکتے ہیں تاکہ اپنے سیلز ڈیٹا کا تجزیہ کر سکیں:

![ایجنٹک سروس عمل میں](../../../translated_images/ur/agent-service-in-action.34fb465c9a84659e.webp)

ان ٹولز میں سے کسی کو بھی سروس کے ساتھ استعمال کرنے کے لیے ہم ایک کلائنٹ بنا سکتے ہیں اور ایک ٹول یا ٹول سیٹ کی تعریف کر سکتے ہیں۔ عملی نفاذ کے لیے ہم درج ذیل Python کوڈ استعمال کر سکتے ہیں۔ LLM ٹول سیٹ کو دیکھ کر فیصلہ کر سکے گا کہ آیا وہ صارف کی بنائی ہوئی فنکشن `fetch_sales_data_using_sqlite_query` استعمال کرے یا پہلے سے تیار کردہ کوڈ انٹرپرٹر، صارف کی درخواست کے مطابق۔

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query فنکشن جو fetch_sales_data_functions.py فائل میں پایا جا سکتا ہے۔
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# ٹول سیٹ کو شروع کریں
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query فنکشن کے ساتھ فنکشن کال کرنے والے ایجنٹ کو شروع کریں اور اسے ٹول سیٹ میں شامل کریں
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# کوڈ انٹرپریٹر ٹول کو شروع کریں اور اسے ٹول سیٹ میں شامل کریں۔
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## قابلِ بھروسہ AI ایجنٹس بنانے کے لیے ٹول استعمال ڈیزائن پیٹرن استعمال کرتے وقت خصوصی غور و خوض کیا ہیں؟

LLMs کی طرف سے متحرک طور پر تیار کردہ SQL کے بارے میں ایک عام تشویش سکیورٹی ہے، خاص طور پر SQL انجیکشن یا نقصان دہ اعمال کے خطرے کے سلسلے میں، جیسے ڈیٹا بیس ڈراپ کرنا یا اس میں چھیڑ چھاڑ کرنا۔ اگرچہ یہ خدشات بجا ہیں، مگر مناسب طریقے سے ڈیٹا بیس رسائی اجازتوں کو ترتیب دے کر ان کو مؤثر طریقے سے کم کیا جا سکتا ہے۔ زیادہ تر ڈیٹا بیسز کے لیے اس میں ڈیٹا بیس کو ریڈ اونلی کنفیگر کرنا شامل ہوتا ہے۔ PostgreSQL یا Azure SQL جیسی ڈیٹا بیس سروسز کے لیے، ایپ کو ایک ریڈ اونلی (SELECT) رول تفویض کیا جانا چاہیے۔

ایپ کو محفوظ ماحول میں چلانا تحفظ کو مزید بہتر بناتا ہے۔ انٹرپرائز منظرناموں میں، عام طور پر آپریشنل سسٹمز سے ڈیٹا نکالا اور تبدیل کر کے ایک ریڈ اونلی ڈیٹا بیس یا ڈیٹا ویئرہاؤس میں رکھا جاتا ہے جس کا اسکیمہ صارف دوست ہوتا ہے۔ اس طریقہ کار سے یہ یقینی بنتا ہے کہ ڈیٹا محفوظ ہے، کارکردگی اور دسترس کے لیے بہتر بنایا گیا ہے، اور ایپ کی رسائی محدود اور صرف ریڈ اونلی ہے۔

## نمونہ کوڈز
- پائتھن: [ایجنٹ فریم ورک](./code_samples/04-python-agent-framework.ipynb)
- .NET: [ایجنٹ فریم ورک](./code_samples/04-dotnet-agent-framework.md)

## کیا آپ کے پاس ٹول استعمال کرنے کے ڈیزائن پیٹرنز کے بارے میں مزید سوالات ہیں؟

دیگر سیکھنے والوں سے ملنے، آفس آورز میں شرکت کرنے، اور اپنے AI ایجنٹس کے سوالات کے جواب حاصل کرنے کے لیے [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) میں شامل ہوں۔

## اضافی وسائل

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents سروس ورکشاپ</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer ملٹی-ایجنٹ ورکشاپ</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel فنکشن کالنگ ٹیوٹوریل</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel کوڈ انٹرپریٹر</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen ٹولز</a>

## پچھلا سبق

[ایجنٹک ڈیزائن پیٹرنز کو سمجھنا](../03-agentic-design-patterns/README.md)

## اگلا سبق

[ایجنٹک RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
اعلانِ ذمہ داری:
یہ دستاویز مصنوعی ذہانت کی ترجمہ سروس Co-op Translator (https://github.com/Azure/co-op-translator) کے ذریعے ترجمہ کی گئی ہے۔ اگرچہ ہم درستگی کی بھرپور کوشش کرتے ہیں، براہِ کرم نوٹ کریں کہ خودکار ترجموں میں غلطیاں یا عدم مطابقتیں ہو سکتی ہیں۔ اصل دستاویز کو اس کی مادری زبان میں ہی معتبر ماخذ سمجھا جانا چاہیے۔ اہم معلومات کے لیے پیشہ ورانہ انسانی ترجمے کی سفارش کی جاتی ہے۔ اس ترجمے کے استعمال سے پیدا ہونے والی کسی بھی غلط فہمی یا غلط تعبیر کے لیے ہم ذمہ دار نہیں ہیں۔
<!-- CO-OP TRANSLATOR DISCLAIMER END -->