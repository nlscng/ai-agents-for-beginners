[![ကောင်းမွန်သော AI ကိုယ်စားလှယ်များဒီဇိုင်းရေးဆွဲနည်း](../../../translated_images/my/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(ဤသင်ခန်းစာ၏ ဗီဒီယိုကို ကြည့်ရန် အပေါ်တွင်ရှိသည့်ပုံကို နှိပ်ပါ)_

# ကိရိယာသုံးခြင်း ဒီဇိုင်းပုံစံ

ကိရိယာများသည် စိတ်၀င်စားဖွယ်ကောင်းသည်၊ မည်သူ့ AI ကိုယ်စားလှယ်များအတွက် ကျယ်ပြန့်သော လုပ်ဆောင်နိုင်စွမ်းများရှိစေသည်။ ကိုယ်စားလှယ်သည် ပြုလုပ်နိုင်သော လှုပ်ရှားမှုအမျိုးအစားများ အကန့်အသတ်ရှိတာကိုခွဲထားပြီး၊ ကိရိယာတစ်ခု ထည့်သွင်းခြင်းဖြင့် ကိုယ်စားလှယ်သည် လုပ်ဆောင်နိုင်သည့် လှုပ်ရှားမှုများ အမျိုးမျိုး အသုံးပြုနိုင်ပါသည်။ ဤအခန်းတွင် ကျွန်ုပ်တို့သည် Tool Use Design Pattern ကို ကြည့်ရှုမည်ဖြစ်ပြီး AI ကိုယ်စားလှယ်များသည် သတ်မှတ်ထားသော ကိရိယာများကို မည်သို့ အသုံးပြုနိုင်ပြီး သူတို့ရည်မှန်းချက်များ ရရှိစေရန် အမျိုးအစားကို ဖော်ပြပေးပါမည်။

## နိဒါန်း

ဤသင်ခန်းစာတွင် ကျွန်ုပ်တို့ လေ့လာမည့် မေးခွန်းများမှာ -

- ကိရိယာသုံးခြင်း ဒီဇိုင်းပုံစံ란 무엇인가요?  
- အများဆုံး အသုံးချနိုင်သော ကိရိယာသုံးခြင်း များသည် မည်မျှသောကိစ္စများတွင် သုံးနိုင်ပါသလဲ?  
- ဒီဇိုင်းပုံစံကို အကောင်အထည်ဖော်ရန် လိုအပ်သည့်အချက်အလက်များ/အခြေခံဖွဲ့စည်းမှုများ ဆိုသည်မှာ မည်မျှလည်း?  
- ယုံကြည်စိတ်ချရသော AI ကိုယ်စားလှယ်များတည်ဆောက်ရာတွင် Tool Use Design Pattern ကို အသုံးပြုရာတွင် ထူးခြားသော အမြင်များဘာလည်းရှိသည်နည်း?  

## သင်ယူရန်ရည်ရွယ်ချက်များ

ဤသင်ခန်းစာပြီးဆုံးပြီးနောက် သင်သည် -

- Tool Use Design Pattern နှင့် ၎င်း၏ ရည်ရွယ်ချက်အကြောင်း ကို အတိအကျသိရှိနိုင်မည်၊  
- Tool Use Design Pattern ကို ဘယ်လို ကိစ္စများတွင် အသုံးပြုနိုင်မည်ဆိုတာ အတိအကျ ရွေးချယ်နိုင်မည်၊  
- ဒီဇိုင်းပုံစံ အကောင်အထည်ဖော်ရာ၌ လိုအပ်သည့် အရေးပါတဲ့ အချက်များကို နားလည်နိုင်မည်၊  
- ဒီဇိုင်းပုံစံကို အသုံးပြုပြီး AI ကိုယ်စားလှယ်များ ယုံကြည်စိတ်ချရရေး အတွက် လိုအပ်သည့် အချက်များအား သိရှိနိုင်မည် ဖြစ်သည်။

## ကိရိယာသုံးခြင်း ဒီဇိုင်းပုံစံ란 무엇인가요?

**Tool Use Design Pattern** သည် တစ်ခုထဲသော ရည်မှန်းချက်များကို အောင်မြင်ရန်အတွက် LLM များအား ပြင်ပကိရိယာများနှင့် အပြန်အလှန် ဆက်သွယ်နိုင်စွမ်းကို ပေးသောအခြေအနေကို ဦးတည်ပြောပါသည်။ ကိရိယာများဆိုသည်မှာ ကိုယ်စားလှယ်အား လုပ်ဆောင်နိုင်စေသော ကုဒ်များ ဖြစ်သည်။ ကိရိယာတစ်ခုမှာ ကိန်းဂဏန်းတွက်ချက်ခြင်း လို သာယာမာန်ပြုလုပ်နိုင်သည့် လုပ်ဆောင်ချက်တစ်ခု ဖြစ်နိုင်သလို၊ သုံးသူ သုံး API ခေါ်ယူမှုများမှတစ်ဆင့် စတော့ရှယ်ယာတန်ဖိုးရှာဖွေခြင်း သို့မဟုတ် မိုးလေဝသခန့်မှန်းခြေကဲ့သို့သော တတိယပါတီ ဝန်ဆောင်မှုဖြစ်နိုင်ပါသည်။ AI ကိုယ်စားလှယ်၏အခြေအနေတွင် ကိရိယာများကို မော်ဒယ်ဖြင့် ဖန်တီးထားသော function call များကို တုံ့ပြန်၍ ကိုယ်စားလှယ်က ကိုယ်တိုင် အကောင်အထည်ဖော်နိုင်ရန် ဖန်တီးထားသည်။

## ဘယ်အခြေအနေများတွင် အသုံးပြုနိုင်ပါသလဲ?

AI ကိုယ်စားလှယ်များသည် ကိရိယာများကို အသုံးပြု၍ တိုးတက်သော အလုပ်များ ပြီးမြောက်စေ၊ သတင်းအချက်အလက် ရယူစေ၊ ဆုံးဖြတ်ချက်များ ချနိုင်သည်။ Tool Use Design Pattern သည် databases၊ web services သို့မဟုတ် ကုဒ် ရှာဖွေသူများအား dynamic အပြန်အလှန်ဆက်ဆံမှု လိုအပ်သည့် အခြေအနေနှင့် မကြာခဏအသုံးပြုလေ့ရှိသည်။ ၎င်းသည် အောက်ပါ အခြေအနေများတွင် အသုံးဝင်ပါသည်-

- **Dynamic Information Retrieval:** ကိုယ်စားလှယ်များသည် ပြင်ပ API များ သို့မဟုတ် ဒေတာဘေ့စ်များမှ နောက်ဆုံးရ သတင်းအချက်အလက်များ ကိုမေးမြန်းနိုင်သည် (ဥပမာ - SQLite database ကို အသုံးပြုပြီး ဒေတာခွဲခြမ်းစိတ်ဖြာခြင်း၊ စတော့ရှယ်ယာတန်ဖိုး သို့မဟုတ် မိုးလေဝသ သတင်းရယူခြင်း)။
- **Code Execution and Interpretation:** ကိုယ်စားလှယ်များသည် ကုဒ်များ သို့မဟုတ် စာရိုက်ချက်များကို အကောင်အထည်ဖော်ပြီး သင်္ချာ ပြသနာများ ဖြေရှင်းခြင်း၊ အစီရင်ခံစာတင်ခြင်း သို့မဟုတ် မော်ကွန်းများ ပြုလုပ်နိုင်သည်။
- **Workflow Automation:** တခါတရံ လုပ်ဆောင်ရသော လုပ်ငန်းစဉ်များကို task scheduler များ၊ အီးမေးလ် ဝန်ဆောင်မှုများ သို့မဟုတ် ဒေတာ ပိုင်းလိုင်းများနှင့် ပွဲတော်ပွဲ။  
- **Customer Support:** ကိုယ်စားလှယ်များသည် CRM စနစ်များ၊ တင်ကေ့တင်က်များ၊ သို့မဟုတ် အသိပညာ ထုတ်ပြန်စုစည်းမှုများနှင့် ပူးပေါင်း၍ အသုံးပြုသူ မေးခွန်းများ ဖြေရှင်းနိုင်သည်။
- **Content Generation and Editing:** ကိုယ်စားလှယ်များသည် အစားထိုးစစ်သူများ၊ စာသားချုပ်ချပ်သူများ သို့မဟုတ် အကြောင်းအရာ လုံခြုံရေး စစ်ဆေးသူကိရိယာများကို အသုံးပြု၍ အကြောင်းအရာဖန်တီးခြင်းများ တွင် အကူအညီ ရနိုင်သည်။

## Tool Use Design Pattern ကို အကောင်အထည်ဖော်ရန် လိုအပ်သည့် အချက်အလက်/ဖွဲ့စည်းမှုများ

ဤဖွဲ့စည်းမှုများက AI ကိုယ်စားလှယ်အား အကြောင်းအရာများ ပြီးမြောက်စေပါသည်။ Tool Use Design Pattern ကို လုပ်ဆောင်ရန် အရေးပါတဲ့ အချက်များမှာ -

- **Function/Tool Schemas:** ရနိုင်သော ကိရိယာများ၏ အသေးစိတ်အဓိပ္ပါယ်များ၊ function မှာနာမည်၊ ရည်ရွယ်ချက်၊ လိုအပ်သည့် ပါရာမီတာများနှင့် မျှော်မှန်းထားသည့် ထွက်ရှိမှုများ ပါဝင်သည်။ ၎င်း schema များက LLM များအား ဘာကိရိယာများ ရနိုင်သည်နှင့် အတိအကျ မေးခွန်းတောင်းဆိုမှုများ ဖန်တီးနိုင်ရန်သိရှိစေပါသည်။

- **Function Execution Logic:** အသုံးပြုသူ ရည်ရွယ်ချက်နှင့် စကားပြောဆက်သွယ်မှု အခြေအနေအပေါ် မူတည်၍ ကိရိယာများကို မည်သို့၊ ဘယ်အချိန်တွင်ခေါ်ယူမည်ဆိုသည့် စည်းကမ်းများဖြစ်သည်။ ၎င်းမှာ planner modules၊ routing စက်မှုများ သို့မဟုတ် condition flows တို့ ပါဝင်နိုင်သည်။

- **Message Handling System:** အသုံးပြုသူဝင်ရောက်မှုများ၊ LLM အဖြေများ၊ ကိရိယာခေါ်ဆိုမှုများနှင့် ကိရိယာထွက်ရှိမှုများအကြား စကားပြောဆက်သွယ်မှု လှုပ်ရှားမှုကို စီမံကိန်းများ။

- **Tool Integration Framework:** ကိုယ်စားလှယ်အား ကိရိယာများနှင့် ချိတ်ဆက်ပေးသော သက်သေပြုတည်ဆောက်မှု၊ ရိုးရှင်းသော function များ သို့မဟုတ် ပြင်းထန်သော ပြင်ပဝန်ဆောင်မှုများကို ပေါင်းစည်းခြင်း။

- **Error Handling & Validation:** ကိရိယာများအကောင်အထည်ဖော်ခြင်းတွင် ကြုံတွေ့သော ဖြုတ်ဖျက်မှုများကို စီမံရန်၊ ပါရာမီတာများ စစ်ဆေးရန်နှင့် မမျှော်လင့်ထားသော တုံ့ပြန်မှုများကို စီမံခန့်ခွဲရန် နည်းလမ်းများ။

- **State Management:** စကားပြော အနေနှင့် ယခင်ကိရိယာ ဆက်သွယ်မှုများ၊ ပုံမှန်ထားသော ဒေတာများကို သိမ်းဆည်းပြီး multi-turn ဆက်သွယ်မှုများတွင် တစ်ပြိုင်နက်တည်း ဖြစ်နေစေရန်။

နောက်တစ်ဆင့်မှာ Function/Tool Calling ကို အသေးစိတ်ကြည့်ရှုပါမည်။

### Function/Tool Calling

Function calling သည် Large Language Models (LLMs) များအား ကိရိယာများနှင့် ဆက်သွယ်ရန် အဓိကနည်းလမ်းဖြစ်သည်။ ‘Function’ နှင့် ‘Tool’ ဟူသော အပိုင်းများကို မကြာခဏသုံးသည်မှာ ‘function’ များသည် တိုးတက်အသုံးပြုလိုက်သော ကုဒ်ပုဒ်များဖြစ်ပြီး၊ ‘tools’ များသည် ကိုယ်စားလှယ်များ ရှေ့ဆောင်ရန် အသုံးပြုသော ကိရိယာများဖြစ်ပါသည်။ function ရဲ့ ကုဒ်ကို ခေါ်ယူခြင်းအတွက် LLM သည် အသုံးပြုသူ တောင်းဆိုချက်ကို function အတိုင်းအတာနှင့် နှိုင်းယှဉ်ရမည်ဖြစ်သည်။ ယင်းအတွက် ရနိုင်သော function များ၏ အသေးစိတ်ဖော်ပြချက်များပါဝင်သည့် schema တစ်ခုတို့ကို LLM သို့ ပေးပို့သည်။ LLM သည် လိုအပ်သော function ကို ရွေးချယ်ပြီးနောက် ၎င်းနာမည်နှင့် argument များကို ပြန်လည်ပေးပို့သည်။ ရွေးချယ်ထားသော function ကို ခေါ်ယူပြီး ၎င်း၏ တုံ့ပြန်မှုကို LLM သို့ ပြန်လည်ပို့၍ အသုံးပြုသူ တောင်းဆိုမှုကို ဖြေပေးသည်။

Function calling ကို ကိုယ်စားလှယ်များအတွက် အကောင်အထည်ဖော်ရန် -

1. function calling ကို ထောက်ပံ့သော LLM model  
2. function အသေးစိတ်ဖော်ပြချက်များ ပါဝင်သည့် schema  
3. ဖော်ပြထားသော function အတွက် ကုဒ်များ  

မြို့တစ်မြို့၏ လက်ရှိအချိန် ရယူခြင်း အကြောင်း ဥပမာယူပါမည်-

1. **Function calling ထောက်ပံ့သော LLM ကို စတင်ဖန်တီးခြင်း-**

    function calling ကို ထောက်ပံ့သော မော်ဒယ်အားသာအသုံးပြုရမည်ဖြစ်ပြီး သင်သုံးအပ်သော LLM မှာ ထောက်ပံ့မှုရှိခြင်းကို စစ်ဆေးပါ။ <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> သည် function calling ကို ထောက်ပံ့ပါသည်။ Azure OpenAI client ကို စတင်ဖန်တီးနိုင်ပါပြီ။

    ```python
    # Azure OpenAI client ကို သတ်မှတ်ဆောင်ရွက်ပါ
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Function Schema တစ်ခု ဖန်တီးခြင်း-**

    function နာမည်၊ function အလုပ်လုပ်ပုံဖော်ပြချက်နှင့် ပါရာမီတာနာမည်များ၊ ဖော်ပြချက်များ ပါဝင်သည့် JSON schema ကို ဖန်တီးပါမည်။ schema ကို စီမံကိန်း client သို့ ယူပြီး အသုံးပြုသူ တောင်းဆိုချက်ဖြစ်သည့် San Francisco တွင်စောင့်ကြည့်ချိန် ရှာဖွေရန်နေရာတစ်ခုကနေ ပို့ပေးပါမည်။ မှတ်သားဖို့ လိုအပ်သည့် အချက်မှာ **tool call** တစ်ခုသာပြန်လာပြီး၊ စုံစမ်းမည့်မေးခွန်းအတွက် နောက်ဆုံး အဖြေ မဟုတ်ပါ။ LLM သည် အလုပ်စီမံရန် function နာမည်နှင့် argument များကိုသာ ပြန်ပေးအပ်သည်။

    ```python
    # မော်ဒယ်ဖတ်ရှုရန်အတွက် အလုပ်လုပ်ပုံဖော်ပြချက်
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
  
    # စတင်အသုံးပြုသူစာတိုက်
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # ပထမဆုံး API ခေါ်ဆိုချက်: မော်ဒယ်ကို function ကိုသုံးရန်မေးမြန်းပါ
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # မော်ဒယ်၏တုံ့ပြန်ချက်ကိုဆောင်ရွက်ပါ
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **အလုပ်ကို ဆောင်ရွက်မည့် function ကုဒ်-**

    LLM မှ ရွေးချယ်ထားသော function ကို ရှိပါက၊ ၎င်းကို အသုံးပြုရန် အမှန်တကယ် code ကိုရေးဆွဲပြီး အကောင်အထည်ဖော်သည်။  
    Python ဖြင့် လက်ရှိအချိန် ရယူရန် ကုဒ်ရေးရန် လိုအပ်သည်။ response_message ကနေ function နာမည်နှင့် argument များကို ထုတ်ယူဖို့ ကုဒ်ကိုလည်း ရေးရန်လိုပါသည်။

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
     # မှတ်တမ်းခေါ်ယူမှုများကို ကိုင်တွယ်ပါ
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
  
      # ဒုတိယ API ခေါ်ယူမှု: မော်ဒယ်မှ နောက်ဆုံးတုံ့ပြန်ချက်ကို ရယူပါ
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

Function Calling သည် most of agent tool use design ၏ ဗဟိုအချက်ဖြစ်ပါသည်၊ သို့သော် မူလကနေ တည်ဆောက်ရန် စိန်ခေါ်မှု ရှိတတ်သည်။  
[Lesson 2](../../../02-explore-agentic-frameworks) တွင် လေ့လာသည့်အတိုင်း agentic frameworks မှာ tool use ကို အကောင်အထည်ဖော်ရန် ကြိုတင်ဖွဲ့စည်းထားသော အပိုင်းများကို ပေးသည်။

## Agentic Frameworks နှင့် Tool Use ဥပမာများ

အောက်ပါ ဥပမာများမှာ လွယ်ကူစွာ Tool Use Design Pattern ကို agentic framework များ အသုံးပြုပြီး အကောင်အထည်ဖော် နည်းများဖြစ်သည်-

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> သည် .NET၊ Python နှင့် Java developer များအတွက် Large Language Models (LLMs) ဖြင့် လုပ်ငန်းဆောင်တာများကို အနေအထား ပေးသည့် open-source AI framework ဖြစ်သည်။ function calling ကို အလွယ်တကူ လုပ်ဆောင်နိုင်ရန် function များနှင့် ၎င်းတို့ရဲ့ ပါရာမီတာများကို <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializing</a> လုပ်ပေးခြင်းဖြင့် ဖော်ပြပေးပါသည်။ ထို့ပြင် model နှင့် ကိုယ်၏ code အကြား ဆက်သွယ်မှုကို ကိုင်တွယ်ပေးပါသည်။ Semantic Kernel ကို အသုံးပြုခြင်း၏နောက်ထပ် အကျိုးတရားမှာ <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> နှင့် <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a> ကဲ့သို့သော ကြိုတင်ဖန်တီးထားသော ကိရိယာများကိုလည်း အသုံးပြုနိုင်ခြင်း ဖြစ်သည်။

Semantic Kernel ဖြင့် function calling အဆင့်ဆင့်လုပ်ဆောင်မှုကို ပုံဆွဲထားသည်-

![function calling](../../../translated_images/my/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernel ခံတွင် functions/tools ကို <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a> ဟု ခေါ်သည်။ အောက်တွင် ရှင်းပြခဲ့သော `get_current_time` function ကို plugin အဖြစ် ပြောင်းလဲနိုင်ပြီး၊ class တစ်ခုအဖြစ် ဖော်ဆောင်နိုင်သည်။ function ၏ ဖော်ပြချက်ကိုယူသည့် `kernel_function` decorator ကိုလည်း import လုပ်နိုင်သည်။ GetCurrentTimePlugin ဖြင့် kernel တစ်ခုဖန်တီးပါက automatically function နှင့် ၎င်း၏ ပါရာမီတာများကို serialize ပြုလုပ်ကာ LLM သို့ schema တစ်ခု ပေးပို့သည်။

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

# ကန့်ရှင်ကို ဖန်တီးပါ
kernel = Kernel()

# ပလပ်ဂင်ကို ဖန်တီးပါ
get_current_time_plugin = GetCurrentTimePlugin(location)

# ပလပ်ဂင်ကို ကန့်ရှင်ထဲ ထည့်ပါ
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> သည် အသစ်ထွက် agentic framework ဖြစ်ပြီး developer များကို ၎င်းတို့၏ AI ကိုယ်စားလှယ်များကို ပြီးပြည့်စုံစွာ လုံခြုံစွာ တည်ဆောက်ခြင်း၊ deployment ဆောင်ရွက်ခြင်းနှင့် ရှယ်ထုတ်ရေး ဆောင်ရွက်ရန် အောက်ခံ သိုလှောင်မှုများမစိုးရိမ်ပဲ တာဝန် ထမ်းဆောင်နိုင်စေသည်။ လုပ်ငန်းအသုံးများအတွက် အထူးအသုံးဝင်သော managed service ဖြစ်ပြီး လုံခြုံရေး အဆင့်မြင့်သော နည်းလမ်းများ ပါ၀င်သည်။

LLM API ကို တိုက်ရိုက် အသုံးပြုခြင်းနှင့် နှိုင်းယှဥ်ပါက Azure AI Agent Service ၌ အောက်ပါ အားသာချက်များ ရှိသည် -

- ကိရိယာခေါ်ယူမှုကို အလိုအလျောက် လုပ်ဆောင်ခြင်း - tool call ကို ခွဲခြာရန်၊ tool ကို ခေါ်ရန်နှင့် တုံ့ပြန်မှုကို စီမံရန် မလိုအပ်တော့ပါ; ၎င်းအား အားလုံးသည် server-side မှ ဆောင်ရွက်ပါသည်  
- လုံခြုံစိတ်ချရသော ဒေတာ စီမံခန့်ခွဲမှု - ကိုယ်တိုင် conversation state ကို စီမံရှင်းလင်းရန်မလိုပဲ threads တွင် သတင်းအချက်အလက်အားလုံး သိမ်းဆည်းထားနိုင်သည့် တာဝန်ယူမှုရှိသည်  
- အထူး tools များ - သင်၏ ဒေတာရင်းမြစ်များနှင့် ဆက်သွယ်ရန် အသုံးပြုနိုင်သည့် Bing၊ Azure AI Search နှင့် Azure Functions ကဲ့သို့ tools များ ပါ၀င်သည်။

Azure AI Agent Service တွင် ရနိုင်သည့် ကိရိယာများကို နှစ်မျိုးခွဲ၍ ခွဲခြားနိုင်သည် -

1. Knowledge Tools:  
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing Search နှင့် Grounding</a>  
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>  
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>  

2. Action Tools:  
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>  
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>  
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI သတ်မှတ်ထားသော tools</a>  
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>  

Agent Service မှာ ကိရိယာများကို တစ်စုတည်း `toolset` အဖြစ် အသုံးပြုနိုင်စေသည်။ ၎င်းတွင် `threads` ကိုလည်း အသုံးပြုသည်။ ၎င်းသည် စကားပြောမှုဖြစ်စဉ်၏ အတိတ် သတင်းအချက်အလက်မှတ်တမ်းကို ထိန်းသိမ်းသည်။

Contoso ဟုခေါ်သော ကုမ္ပဏီတွင် ရောင်းအား ကိုယ်စားလှယ်တစ်ယောက်ဖြစ်ကြောင်း တွေးပါစို့။ သင်သည် သင်၏ ရောင်းအား ဒေတာများနှင့် ပတ်သတ်သော မေးခွန်းများကို ဖြေနိုင်သော စကားပြော AI ကိုယ်စားလှယ် တစ်ယောက် ဖန်တီးလိုသည်။

အောက်ပါပုံသည် Azure AI Agent Service ဖြင့် သင်၏ ရောင်းအားဒေတာကို ခွဲခြမ်းစိတ်ဖြာနည်းကို ဖော်ပြသည်-

![Agentic Service In Action](../../../translated_images/my/agent-service-in-action.34fb465c9a84659e.webp)

ဤ service နှင့် tool များကို အသုံးပြုရန် client တစ်ခုဖန်တီး၍ tool သို့မဟုတ် toolset ကို သတ်မှတ်ရမည်ဖြစ်သည်။ အသုံးပြုသူ၏ တောင်းဆိုချက်အပေါ်မူတည်၍ LLM မှ user ဖန်တီးထားသော function `fetch_sales_data_using_sqlite_query` သို့မဟုတ် ကြိုတင်တည်ဆောက်ထားသော Code Interpreter ကို အသုံးပြုမည် မရွေးဆုံးဖြတ်နိုင်ပါသည်။

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query ဖောင်ရှင်ကို fetch_sales_data_functions.py ဖိုင်တွင်တွေ့နိုင်သည်။
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# ကိရိယာစုစည်းမှု စတင်ခြင်း
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query ဖောင်ရှင်နှင့် function calling agent ကို စတင်ပြီး toolset တွင် ထည့်ခြင်း
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Code Interpreter tool ကို စတင်ပြီး toolset တွင် ထည့်ခြင်း။
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## ယုံကြည်စိတ်ချရသော AI ကိုယ်စားလှယ်များ တည်ဆောက်ရာတွင် Tool Use Design Pattern အသုံးပြုမှုအတွက် ထူးခြားစောင့်ကြည့်ရမည့် အချက်များ

LLM များမှ dynamic SQL ထွက်ရှိမှုတွင် လုံခြုံရေး စိုးရိမ်မှုတစ်ခုမှာ SQL injection သို့မဟုတ် database ကို ဖျက်ဆီးခြင်း၊ စိုးရိမ်ရသော လုပ်ဆောင်ချက်များ ဖြစ်ပေါ်နိုင်ခြင်း ဖြစ်သည်။ ဤစိုးရိမ်မှုများကို database access permission များကို မှန်ကန်စွာ ဖွင့်ထားခြင်းဖြင့် ထိရောက်စွာ ကာကွယ်နိုင်သည်။ ဒေတာဘေ့စ်များအတွက် များစွာသည် read-only အဖြစ်သတ်မှတ်ထားရပါသည်။ PostgreSQL သို့မဟုတ် Azure SQL ကဲ့သို့သော database ဝန်ဆောင်မှုများတွင် app အတွက် read-only (SELECT) role တစ်ခု ဖော်ပြထားရမည်ဖြစ်သည်။

app ကို လုံခြုံသော ပတ်ဝန်းကျင်တွင် လည်ပတ်ခြင်းသည် ကာကွယ်မှုကို ပိုမိုမြှင့်တင်ပေးသည်။ စီးပွားရေးလုပ်ငန်းအတွက် ဒေတာများသည် ယခင် စနစ်များမှ ရယူ၍ ဖော်ပြ ပြောင်းလဲပြီး read-only database သို့ ဒေတာရုံသို့ ပြောင်းလဲထားခြင်းဖြစ်သည်။ ၎င်းနည်းလမ်းသည် ဒေတာလုံခြုံမှုရှိစေပြီး လုပ်ဆောင်နိုင်မှုနှင့် ရရှိနိုင်မှုကို တိုးတက်စေပြီး app မှာ ဖတ်ချက်သာ ခွင့်ပြုသည့် environment ဖြစ်စေသည်။

## နမူနာကုဒ်များ
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## ကိရိယာအသုံးပြုဖို့ Design Patterns ကို နောက်ထပ်မေးစရာရှိလား?

အခြားသင်ယူနေသူတွေနဲ့တွေ့ဆုံဖို့၊ အလုပ်ချိန်တွေတက်ရောက်ဖို့၊ နဲ့သင့် AI Agents မေးခွန်းတွေကို ဖြေရှင်းပေးဖို့ [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) ကို ဝင်ရောက်ပါ။

## ထပ်ဆောင်းအရင်းအမြစ်များ

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## ယခင်သင်ခန်းစာ

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## နောက်တစ်ခန်းသင်ခန်းစာ

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**နောက်ခံအကြောင်း**  
ဒီစာတမ်းကို AI ဘာသာပြန်ဝန်ဆောင်မှုဖြစ်သည့် [Co-op Translator](https://github.com/Azure/co-op-translator) ဖြင့် ဘာသာပြန်ထားပါသည်။ ကျွန်ုပ်တို့သည် ချိုးညံမှုများကို လျော့ပါးစေဖို့ ကြိုးစားသော်လည်း၊ အလိုအလျောက် ပြန်ဆိုမှုများတွင် မှားယွင်းချက်များ သို့မဟုတ် မှန်ကန်မှုလွဲမှားမှုများ ပါဝင်နိုင်ကြောင်း ကျေးဇူးပြု၍ သိရှိပါရန်။ မူရင်းစာတမ်းကို မူလဘာသာဖြင့်သာ တရားဝင်အရင်းအမြစ်အဖြစ် သတ်မှတ်သင့်သည်။ အရေးကြီးသော အချက်အလက်များအတွက် လူပညာရှင်များအား စာလက်ခံပြန်ဆိုရန် အကြံပြုပါသည်။ ဤဘာသာပြန်မှု၏ အသုံးပြုမှုမှ ဖြစ်ပေါ်လာသော ဘယ်လို မသိမြင်မှုများ သို့မဟုတ် မှားယွင်း နားလည်မှုများအတွက် ကျွန်ုပ်တို့ တာဝန်မခံပါ။
<!-- CO-OP TRANSLATOR DISCLAIMER END -->