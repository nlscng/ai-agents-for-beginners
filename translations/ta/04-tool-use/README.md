[![How to Design Good AI Agents](../../../translated_images/ta/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(இந்த பாடத்தின் வீடியோவை பார்ப்பதற்கு மேல் உள்ள படத்தை கிளிக் செய்யவும்)_

# கருவி பயன்பாடு வடிவமைப்பு மாதிரி

கருவிகள் சுவாரசியமாக இருக்கின்றன, ஏனெனில் அவை AI முகவர்களுக்கு விரிவான திறன்களை பெற அனுமதிக்கின்றன. முகவருக்கு செய்யக்கூடிய செயற்பாடுகளின் வரம்பு குறைக்கப்பட்டிருப்பதற்குப் பதிலாக, ஒரு கருவியைச் சேர்ப்பதன் மூலம், முகவர் இப்போது பரவலான செயற்பாடுகளைச் செய்ய முடியும். இந்த அதிகாரத்தில், நாங்கள் கருவி பயன்பாடு வடிவமைப்புக் கோட்பாட்டை பார்ப்போம், இது AI முகவர்கள் தங்கள் இலக்குகளை அடைய குறிப்பிட்ட கருவிகளை எப்படி பயன்படுத்த முடியும் என்பதைக் கூறுகிறது.

## அறிமுகம்

இந்த பாடத்தில், நாங்கள் பின்வரும் கேள்விகளுக்கு பதில் காண முயற்சிக்கிறோம்:

- கருவி பயன்பாட்டு வடிவமைப்பு மாதிரி என்றால் என்ன?
- இது எந்த பயன்பாடுகளில் பயன்படுத்தப்பட முடியும்?
- வடிவமைப்பு மாதிரியை செயல்படுத்த தேவையான கூறுகள்/கட்டமைப்புக் கூறுகள் என்ன?
- நம்பிக்கையான AI முகவர்களை உருவாக்க கருவி பயன்பாடு வடிவமைப்பு மாதிரியுடன் தொடர்புடைய சிறப்பு கருதுகோள்கள் என்ன?

## கற்றல் நோக்கங்கள்

இந்த பாடத்தை முடித்த பிறகு, நீங்கள்:

- கருவி பயன்பாடு வடிவமைப்புக் கோட்பாட்டையும் அதன் நோக்கத்தையும் வரையறுக்க முடியும்.
- கருவி பயன்பாடு வடிவமைப்புக் கோட்பாடை பொருந்தக்கூடிய பயன்பாடுகளை அடையாளம் காண முடியும்.
- வடிவமைப்புக் கோட்பாட்டை செயல்படுத்த தேவையான முக்கிய கூறுகளை புரிந்துகொள்ள முடியும்.
- இந்த வடிவமைப்பைக் கொண்டு AI முகவர்களில் நம்பிக்கையை உறுதிப்படுத்துவதற்கான பரிசீலனைகள் என்ன என்பதைக் கவனிக்க முடியும்.

## கருவி பயன்பாடு வடிவமைப்பு மாதிரி என்பது என்ன?

**கருவி பயன்பாடு வடிவமைப்பு மாதிரி** போல் LLMகளுக்கு வெளிப்புற கருவிகளுடன் தொடர்பு கொண்டு குறிப்பிட்ட இலக்குகளை அடைய முடியுமாறு திறனை வழங்குகிறது. கருவிகள் என்பது முகவரி மூலம் செயல்படுத்தக்கூடிய குறியீடுகள் ஆகும். ஒரு கருவி கணக்கிடும் இயந்திரம் போன்ற எளிய செயல்பாடு அல்லது பங்கு-மூன்றாம் தரப்பு சேவைக்கு API அழைப்பு (பங்கு விலை கண்காணிப்பு அல்லது வானிலைக் கணிப்பு போன்ற) ஆக இருக்கலாம். AI முகவர்களின் சூழலில், கருவிகள் **மாதிரி உருவாக்கிய செயல்பாடு அழைப்புகளுக்கு** பதிலாக முகவர்களால் செயல்படுத்தப்பட도록 வடிவமைக்கப்பட்டுள்ளன.

## இது எந்த பயன்பாடுகளில் பயன்படுத்தப்பட முடியும்?

AI முகவர்கள் கருவிகளை பயன்படுத்தி சிக்கலான பணிகளை நிறைவேற்ற, தகவல்களை மீட்டெடுக்க, அல்லது முடிவெடுக்க முடியும். கருவி பயன்பாடு வடிவமைப்பு மாதிரி பொதுவாக தானியங்கி உறவு மற்றும் வெளிப்புற அமைப்புகளுடன், உட்பட தரவுத்தளங்கள், வலை சேவைகள் அல்லது குறியீட்டு மூல்யாக்கிகள் போன்றவற்றுடன் இயக்கம் தேவையான சூழல்களில் பயன்படுத்தப்படுகிறது. இதன் பயன்பாடுகள் பல்வேறு:

- **தனக்கேற்ற தகவல் மீட்டெடுப்பு:** முகவர்கள் வெளிப்புற APIகளோ அல்லது தரவுத்தளங்களோ மூலம் சமீபத்திய தரவைப் பெற முடியும் (எ.கா., SQLite தரவுத்தளத்தில் தரவு பகுப்பாய்வு, பங்கு விலை அல்லது வானிலை தகவல் பெற்று வருதல்).
- **குறியீட்டு செயல்பாடு மற்றும் மூல்யாக்கம்:** முகவர்கள் கணிதப் பிரச்சனைகளை தீர்க்க, அறிக்கைகள் உருவாக்க, அல்லது நுட்பப்படுத்தல் செய்ய குறியீடுகளை இயக்க முடியும்.
- **பணி தானியக்கம்:** பணி திட்டமிடுநர்கள், மின்னஞ்சல் சேவைகள், அல்லது தரவுப் குழாய்கள் போன்ற கருவிகளை ஒருங்கிணைக்கும்போது மறுபடியும் செய்ய வேண்டிய அல்லது பல படிகள் கொண்ட பணி.swftசொற்கள் தானியக்கமாக்குதல்.
- **வாடிக்கையாளர் ஆதரவு:** முகவர்கள் CRM அமைப்புகள், டிக்கெட் முகவர்கள் அல்லது அறிவுத் தளங்களுடன் தொடர்பு கொண்டு பயனர்களின் கேள்விகளை தீர்க்க முடியும்.
- **உள்ளடக்க உருவாக்கம் மற்றும் திருத்தம்:** இலக்கணச் சோதனையாளர், உரை சுருக்கியாளர், அல்லது உள்ளடக்க பாதுகாப்பு மதிப்பீட்டாளர் போன்ற கருவிகளை பயன்படுத்தி உள்ளடக்க உருவாக்க பணிகளுக்கு உதவலாம்.

## கருவி பயன்பாடு வடிவமைப்பு மாதிரியை செயல்படுத்த தேவையான கூறுகள்/கட்டமைப்புக் கூறுகள் என்ன?

இந்த கட்டமைப்புக் கூறுகள் AI முகவர்களுக்கு பரவலான பணிகளை செய்ய அனுமதிக்கின்றன. கருவி பயன்பாடு வடிவமைப்பு மாதிரியை செயல்படுத்த தேவையான முக்கிய கூறுக்களை பார்ப்போம்:

- **செயல்பாடு/கருவி வடிவமைப்புகள்**: கிடைக்கும் கருவிகளின் விரிவான வரைவுகள், இதில் செயல்பாட்டு பெயர், நோக்கம், தேவையான அளவை மற்றும் எதிர்பார்க்கப்படும் வெளியீடுகள் அடங்கும். இவ்வாறான வடிவமைப்புகள் LLM உருவாக்கப்பட்ட செயல்பாடுகள் என்னென்ன என்பதை புரிந்து கொள்ளவும் சரியான கோரிக்கைகளை உருவாக்கவும் உதவுகின்றன.

- **செயல்பாடு இயக்கல் தந்திரம்**: பயனர் நோக்கம் மற்றும் உரையாடல் சூழல் அடிப்படையில் கருவிகள் எப்போது எப்படி அழைக்கப்பட வேண்டும் என்பதற்கு வழிகாட்டும். இதில் திட்டமிடுபவர் மொடியூல்கள், வழித்திருப்பு முறைமைகள் அல்லது நிலையில் சார்ந்த ஓட்டங்கள் இருக்கலாம்.

- **செய்தி கையாளல் முறைமை**: பயனர் உள்ளீடுகள், LLM பதில்கள், கருவி அழைப்புகள் மற்றும் கருவி வெளியீடுகளுக்கு இடையேயான உரையாடல் ஓட்டத்தை நிர்வகிக்கும் கூறுகள்.

- **கருவி ஒருங்கிணைப்பு கட்டமைப்பு**: முகவருக்கு எளிய செயல்பாடுகளாக இருந்தாலும், சிக்கலான வெளிப்புற சேவைகளாக இருந்தாலும் பல்வேறு கருவிகளை இணைக்கும் அடித்தளம்.

- **பிழை கையாளல் மற்றும் சரிபார்**: கருவி இயக்கத்தில் தோல்விகளை கையாளுதல், அளவைகளை பரிசோதித்தல், எதிர்பாராத பதில்களை நிர்வகித்தல் போன்ற முறைகள்.

- **நிலை நிர்வாகம்**: உரையாடல் சூழலை, முந்தய கருவி தொடர்புகளை, மற்றும் நிலையான தரவுகளை பின்வரிசையில் பாதுகாத்தல்.

அடுத்ததாக, செயல்பாடு/கருவி அழைப்பினை விரிவாக பார்ப்போம்.

### செயல்பாடு/கருவி அழைப்பு

செயல்பாடு அழைப்பு என்பது LLMகளை கருவிகளுடன் தொடர்பு கொள்வதற்கு முதன்மையான வழியாகும். 'செயல்பாடு' மற்றும் 'கருவி' ஆகியவை பெரும்பாலும் பரஸ்பரம் பரிமாறிக்கொள்ளப்படுவதைக் காணலாம், காரணம் செயல்களில் (மறுபயன்படும் குறியீட்டு தொகுதிகள்) முகவர்கள் பணிகளைச் செய்ய கருவிகள் ஆகும். ஒரு செயல்பாட்டிற்கு கூட்டு குறியீடு இயங்க, LLM பயனரின் கோரிக்கையை செயல்பாடு விளக்கத்துடன் ஒப்பிட வேண்டும். இதற்காக கைமுறை செய்த செயல்பாடுகளுக்கு விளக்கங்கள் அடங்கிய ஒரு வடிவமைப்பு LLMக்கு அனுப்பப்படுகிறது. பிறகு LLM செயல் சொல்லுக்கான சரியான செயல்பாட்டைத் தேர்ந்தெடுத்து அதன் பெயர் மற்றும் அளவுருக்களை விடுப்பதாகும். தேர்ந்தெடுக்கப்பட்ட செயல்பாடு இயங்கப்படுகிறது, அதன் பதில் LLMக்கு அனுப்பப்படுகிறது, இது பயனர் கோரிக்கைக்கு பதிலளிக்க பயன்படுத்தப்படுகிறது.

செயல்பாடு அழைப்பை முகவர்களுக்காக செயல்படுத்த விரும்புவோர் தேவையானவை:

1. செயல்பாடு அழைப்பை ஆதரிக்கும் LLM மாதிரி
2. செயல்பாட்டின் விளக்கங்கள் உள்ள வடிவமைப்பு
3. ஒவ்வொரு செயல்பாட்டிற்கும் குறியீடு

நகரத்தில் தற்போதைய நேரம் பெறும் உதாரணத்தை எடுத்துக்காட்டுவோம்:

1. **செயல்பாடு அழைப்பை ஆதரிக்கும் LLM ஐ துவக்கவும்:**

    எல்லா மாதிரிகளும் செயல்பாடு அழைப்பை ஆதரிப்பதில்லை, உங்கள் LLM இது ஆதரிக்கிறதா என்பதைக் கவனிக்க வேண்டும். <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> செயல்பாடு அழைப்பை ஆதரிக்கிறது. நாம் Azure OpenAI கிளையண்டை தொடங்கலாம்.

    ```python
    # Azure OpenAI கிளையண்டை துவக்குங்கள்
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **செயல்பாட்டின் வடிவமைப்பை உருவாக்குதல்:**

    அடுத்ததாக, செயல்பாட்டின் பெயர், அதன் செயல்பாட்டின் விளக்கம் மற்றும் செயல்பாட்டு அளவுருக்களின் பெயர்கள் மற்றும் விளக்கங்கள் உள்ள JSON வடிவமைப்பை வரையறுக்க வேண்டும்.
    பிறகு இவ்வாறான வடிவமைப்பை முன் உருவாக்கப்பட்ட கிளையண்டிடம், பயனர் கோரிக்கையுடன் (சான் பிரான்சிஸ்கோவில் நேரம் பெறுதல்) அனுப்புவோம். முக்கியமாக கவனிக்க வேண்டியது ஒரு **கருவி அழைப்பு** தான் திரும்ப பெறப்படும், கேள்விக்கு இறுதி பதில் அல்ல. எப்படியெனில், முன்பு கூறியபடி, LLM வேலைக்கான செயல்பாட்டின்பெயர் மற்றும் அதற்கு அனுப்பப்படவேண்டிய அளவுருக்களை இழுத்தெடுக்கிறது.

    ```python
    # படிக்க மாதிரிக்கான செயல்பாட்டின் விளக்கம்
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
  
    # ஆரம்ப பயனர் செய்தி
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # முதல் API அழைப்பு: மாடலை செயல்பாட்டை பயன்படுத்த கேளுங்கள்
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # மாடல் பதிலை செயலாக்கவும்
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **பணியை நிறைவேற்ற தேவையான செயல்பாடு குறியீடு:**

    இப்போது LLM எந்த செயல்பாடு இயக்கப்பட வேண்டும் என்றதைத் தேர்ந்தெடுத்துள்ளது, அந்த செயல்பாட்டை நடாத்தும் குறியீடு செயல்படுத்தப்பட வேண்டும்.
    Python-ல் நகரத்தின் தற்போதைய நேரத்தை பெறக் குறியீட்டை எழுதலாம். எதிர்வினை செய்தியில் இருந்து பெயர் மற்றும் அளவுருக்களை எடுக்கக் குறியீடும் எழுத வேண்டும்.

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
     # செயல்பாடு அழைப்புகளை கையாளவும்
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
  
      # இரண்டாவது API அழைப்பு: மாதிரியில் இருந்து இறுதி பதிலைப் பெறுக
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

செயல்பாடு அழைப்பு என்பது பெரும்பாலான முகவர் கருவி பயன்பாடு வடிவமைப்பின் மையம் ஆகும், ஆனால் அதை புதியதாக செயல்படுத்துவது சிரமமாக இருக்கலாம்.
[Lesson 2](../../../02-explore-agentic-frameworks) இல் நாங்கள் கற்றது போல் முகவர் கட்டமைப்புகள் முன் தயார் கட்டமைப்புகளை வழங்கி கருவி பயன்பாட்டை செயல்படுத்த உதவுகின்றன.

## முகவர் கட்டமைப்புகளுடன் கருவி பயன்படுத்தும் உதாரணங்கள்

வिविध முகவர் கட்டமைப்புகளைப் பயன்படுத்தி கருவி பயன்பாடு வடிவமைப்பைப் பின்பற்றி செயல்படுத்த சில உதாரணங்கள்:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> என்பது .NET, Python, மற்றும் Java உருவாக்குநர்களுக்கான திறந்த மூல AI கட்டமைப்பாகும், LLMக்களுடன் வேலை செய்யும். இது செயல்பாட்டு அழைப்பை எளிதாக்குகிறது, உங்கள் செயல்பாடுகளையும் அதன் அளவுருக்களையும் மாதிரிக்கு சுவாசமாக <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">வரிசைப்படுத்துவதன்</a> மூலம் விளக்குகிறது. இது மாதிரி மற்றும் உங்கள் குறியீடு இடையேயான தொடர்பையும் கையாள்கிறது. Semantic Kernel போன்ற முகவர் கட்டமைப்பை பயன்படுத்துவதன் மேலும் ஒரு நன்மை, <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">கோப்பு தேடல்</a> மற்றும் <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">குறியீட்டு குறியீடு விளக்கி</a> போன்ற முன் தயாரிக்கப்பட்ட கருவிகளுக்கு அணுகலையும் வழங்குகிறது.

பின்வரும் வரைவியல் Semantic Kernel உடன் செயல்பாடு அழைப்பை விளக்குகிறது:

![function calling](../../../translated_images/ta/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernel இல் செயல்பாடுகள்/கருவிகள் <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">பிளகிண்கள்</a> என அழைக்கப்படுகின்றன. முன்பு பார்த்த `get_current_time` செயல்பாட்டை ஒரு கிளாஸ் ஆக மாற்றி பிளகிண் ஆக்கலாம். மேலும் செயல்பாட்டு விளக்கத்துடன் வர வரும் `kernel_function` அலங்கரிப்பாளரை இறக்குமதி செய்யலாம். இதன் மூலம் GetCurrentTimePlugin உடன் ஒரு கனெரல் உருவாக்கும்போது, கனெரல் தானாக செயல்பாட்டையும் அதன் அளவுருக்களையும் வரிசைப்படுத்தி, மாதிரிக்கு அனுப்ப தேவையான வடிவமைப்பை உருவாக்கும்.

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

# கர்னலை உருவாக்கவும்
kernel = Kernel()

# பிளகின் உருவாக்கவும்
get_current_time_plugin = GetCurrentTimePlugin(location)

# பிளகினை கர்னலில் சேர்க்கவும்
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> என்பது புதிய முகவர் கட்டமைப்பாக, மேற்பார்வை மற்றும் சேமிப்பக வளங்களை நிர்வகிக்காமல் பாதுகாப்பாக மேம்படுத்துவதற்காக உருவாக்குனர்களுக்கு உதவுகிறது. இது நிறுவன பயன்பாட்டுகளில் மிகவும் பயனுள்ளதாக உள்ளது, ஏனெனில் இது முழுவதும் நிர்வகிக்கப்படும் சேவையாகவும் நிறுவன தரம் பாதுகாப்புடன் கூடியதாகவும் உள்ளது.

இணையமை API உடன் நேரடியாக ஒப்பிடுகையில், Azure AI Agent Service சில நன்மைகள் வழங்குகிறது:

- தானாக கருவி அழைப்புகள் – கருவி அழைப்பை பகுத்தறிய, கருவியை அழைக்க, பதிலை கையாள தேவையில்லை; அனைத்தும் சேவையகம் பகுதியில் செய்யப்படும்
- பாதுகாப்பான தரவு நிர்வாகம் – உரையாடல் நிலையை நிர்வகிக்க பதில், தேவையான தகவல்களை சேமிப்பதற்கு திரெட்ஸ் பயன்படுத்த முடியும்
- பெட்டி வெளியே கருவிகள் – Bing, Azure AI Search, மற்றும் Azure Functions போன்ற தரவுத் தரவுகளுடன் தொடர்பு கொள்ளக் கூடிய கருவிகள்.

Azure AI Agent Service இல் கிடைக்கும் கருவிகள் இரண்டு வகைகளாகப் பிரிக்கப்படுகின்றன:

1. அறிவுத் கருவிகள்:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing தேடலுடன் அடித்தளக் கட்டமைப்பு</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">கோப்பு தேடல்</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI தேடல்</a>

2. செயல் கருவிகள்:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">செயல்பாடு அழைப்புகள்</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">குறியீடு விளக்கி</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI வரையறுக்கப்பட்ட கருவிகள்</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure செயல்பாடுகள்</a>

Agent Service இவை அனைத்தையும் `toolset` ஆகக் கூடிய பயன்படுத்த அனுமதிக்கிறது. மேலும் அது ஒரு உரையாடலின் செய்தி வரலாற்றை பின்வரிசையில் வைக்கும் `threads` ஐ பயன்படுத்துகிறது.

Contoso என்ற நிறுவனத்தில் நீங்கள் விற்பனை முகவராக இருக்கிறீர்கள் என்று கற்பனை செய்யுங்கள். உங்கள் விற்பனை தரவைப் பற்றிய கேள்விகளுக்கு பதிலளிக்கத்து உரையாடல் முகவரைக் கட்டமைக்க விரும்புகிறீர்கள்.

பின்வரும் படம் Azure AI Agent Service ஐப் பயன்படுத்தி உங்கள் விற்பனை தரவை எப்படி பகுப்பாய்வு செய்ய முடியும் என்பதைக் காட்டுகிறது:

![Agentic Service In Action](../../../translated_images/ta/agent-service-in-action.34fb465c9a84659e.webp)

சேவையுடன் இந்த கருவிகளைப் பயன்படுத்த எலக்ட் கிளையண்டை உருவாக்கவும், கருவி அல்லது கருவிமூட்டத்தை வரையறுக்கவும் முடியும். நடைமுறையில் இதை செயல்படுத்த பைதான் குறியீட்டை பயன்படுத்தலாம். பயனர் உருவாக்கிய செயல்பாடு `fetch_sales_data_using_sqlite_query` அல்லது முன் உருவாக்கப்பட்ட குறியீடு விளக்கி ஆகியவற்றை LLM கருவிமூட்டத்தை கற்றுக்கொண்ட பின்னர் தீர்மானிக்கும்.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query செயல்பாடு, fetch_sales_data_functions.py கோப்பில் காணப்படக்கூடியது.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# கருவி தொகுப்பை துவக்கம் செய்யவும்
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query செயல்பாட்டுடன் செயல்பாடு அழைக்கும் முகவரை துவங்கி அதை கருவி தொகுப்பில் சேர்க்கவும்
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# குறியீடு மொழிபெயர்ப்பாளர் கருவியினை துவங்கி அதை கருவி தொகுப்பில் சேர்க்கவும்.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## நம்பிக்கையான AI முகவர்களை உருவாக்க கருவி பயன்பாடு வடிவமைப்பின் சிறப்பு பரிசீலனைகள் என்ன?

LLMகள் சார்ந்த SQLல் உள்ள நெருங்கிய கவலை பாதுகாப்பு தொடர்புடையது, குறிப்பாக SQL அறைகுறி தாக்குதல் அல்லது தீய செயற்பாடுகள் (தரவுத்தளத்தை நீக்குதல் அல்லது மாற்றுதல் போன்ற). இந்த கவலைகள் உண்மையானவையாக இருந்தாலும், தரவுத்தள அணுகல் உரிமைகள் சரியாக கட்டமைக்கப்பட்டால் அவற்றைக் குறைக்கலாம். பெரும்பாலான தரவுத்தளங்களில் இதற்கு தரவுத்தளத்தை வாசிப்பதற்குரிய முறையில் அமைக்க வேண்டும். PostgreSQL அல்லது Azure SQL போன்ற தரவுத்தள சேவைகளுக்கு செயலி வாசிப்பதற்குரிய (SELECT) வேட்கை வழங்கப்பட வேண்டும்.

சேவையை பாதுகாப்பான சூழலில் இயக்குவதும் மேலதிக பாதுகாப்பை வழங்கும். நிறுவன சூழலில் தரவு இயங்குதளங்களிலிருந்து வாசிப்பதற்குரிய தரவுத்தளமாக அல்லது தரவு தளமாக மாற்றப்படுகிறது, இது பயன்பாட்டின் தரவு நன்றாக பாதுகாப்படையவும், தரவுகளை அணுக எளியது ஆகவும், செயலிக்கு கட்டுப்படுத்தப்பட்ட வாசிப்பதற்குரிய அணுகல் இருக்க உதவும்.

## எடுத்துக்காட்டு குறியீடுகள்
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## கருவி பயன்பாட்டுக்கான வடிவமைப்பு முறைகள் குறித்து மேலும் கேள்விகள் உள்ளதா?

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) இடத்தில் இணைந்து, மற்ற கற்றல் பயனாளர்களுடன் சந்தியுங்கள், அலுவலக நேரங்களில் கலந்துகொள்ளுங்கள் மற்றும் உங்கள் AI முகவர் தொடர்பான கேள்விகளுக்கு பதிலளிக்கவும்.

## கூடுதல் வளங்கள்

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI முகவர் சேவை வேலைப்பாட்டூரி</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer பன்முகவர் வேலைப்பாட்டூரி</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel செயல்முறை அழைப்பு பயிற்சி</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel குறியீடு புரிபொருள்</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen கருவிகள்</a>

## முந்தைய பாடம்

[Agentic Design Patterns பற்றி புரிதல்](../03-agentic-design-patterns/README.md)

## அடுத்த பாடம்

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**வெளியீட்டு அறிவிப்பு**:  
இந்த ஆவணம் AI மொழிபெயர்ப்பு சேவை [Co-op Translator](https://github.com/Azure/co-op-translator) பயன்படுத்தி மொழிபெயர்க்கப்பட்டுள்ளது. நாங்கள் துல்லியத்திற்காக முயற்சி செய்கிறோம் என்ற போதும், தானியங்கி மொழிபெயர்ப்புகளில் பிழைகள் அல்லது தவறுகள் இருக்கக்கூடியவை என்பதை கவனத்தில் கொள்ளவும். மொழிப்பெயர்ப்பு செய்யப்பட்ட ஆவணம் தவிர, அதன் சொந்த மொழியிலுள்ள அசலான ஆவணம் அதிகாரபூர்வமான மூலமாக கருதப்பட வேண்டும். முக்கியமான தகவல்களுக்கு, தொழில்முறை மனித மொழிபெயர்ப்பு பரிந்துரைக்கப்படுகிறது. இந்த மொழிபெயர்ப்பின் பயன்பாட்டால் ஏற்படும் தவறான புரிதல்கள் அல்லது தவறான விளக்கங்களுக்கு நாம் பொறுப்பேற்க மாட்டோம்.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->