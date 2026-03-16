[![चांगले AI एजंट कसे डिझाइन करायचे](../../../translated_images/mr/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(वरील प्रतिमा क्लिक करा हा धडा असलेला व्हिडिओ पाहण्यासाठी)_

# टूल वापरण्याचा डिझाइन पॅटर्न

टुल्स (साधने) मनोरंजक आहेत कारण त्या AI एजंटना अधिक विस्तृत कार्यक्षमता देतात. एजंटकडे मर्यादित क्रियांची यादी असण्याऐवजी, टूल जोडल्याने एजंट आता विस्तृत श्रेणीतील क्रिया करू शकतो. या अध्यायात आपण टूल वापरण्याच्या डिझाइन पॅटर्नकडे पाहणार आहोत, जे स्पष्ट करते की AI एजंट आपल्या उद्दिष्टांची पूर्तता करण्यासाठी विशिष्ट साधनांचा कसा वापर करू शकतात.

## परिचय

या धड्यात, आपण खालील प्रश्नांची उत्तरे शोधणार आहोत:

- टूल वापरण्याचा डिझाइन पॅटर्न म्हणजे काय?
- कोणत्या उपयोगप्रकरणांवर हे लागू केले जाऊ शकते?
- डिझाइन पॅटर्न अंमलात आणण्यासाठी कोणती घटके/बिल्डिंग ब्लॉक्स आवश्यक आहेत?
- विश्वासार्ह AI एजंट तयार करण्यासाठी टूल वापरण्याच्या डिझाइन पॅटर्न वापरताना कोणत्या विशेष बाबी विचारात घ्याव्या?

## शिकण्याचे उद्दिष्ट

हा धडा पूर्ण केल्यानंतर आपण सक्षम असाल:

- टूल वापरण्याचा डिझाइन पॅटर्न आणि त्याचा उद्देश परिभाषित करण्यास.
- ज्या उपयोगप्रकरणांमध्ये टूल वापरण्याचा डिझाइन पॅटर्न लागू होतो ते ओळखण्यास.
- डिझाइन पॅटर्न अंमलात आणण्यासाठी आवश्यक मुख्य घटक समजून घेण्यास.
- या डिझाइन पॅटर्नचा वापर करणाऱ्या AI एजंटसाठी विश्वासार्हता सुनिश्चित करताना विचारात घेण्यासारख्या बाबी ओळखण्यास.

## टूल वापरण्याचा डिझाइन पॅटर्न म्हणजे काय?

टूल वापरण्याचा डिझाइन पॅटर्न मोठ्या भाषा मॉडेल्स (LLMs) ला बाह्य साधनांशी संवाद साधण्याची क्षमता देण्यावर केंद्रित आहे जेणेकरून विशिष्ट उद्दिष्टे पूर्ण करता येतील. टूल म्हणजे एजंटद्वारे कार्य करण्यासाठी चालवता येणारे कोड असते. एक टूल साधी फंक्शन असू शकते जसे की कॅल्क्युलेटर, किंवा तृतीय-पक्ष सेवेकडे केलेले API कॉल असू शकते जसे स्टॉक किंमत तपासणे किंवा हवामान अंदाज. AI एजंटच्या संदर्भात, टूल्सना डिझाइन केले जाते की ते एजंटद्वारे **मॉडेल-जनरेट केलेल्या फंक्शन कॉल्स** च्या प्रतिसादात चालवता येतील.

## कोणत्या उपयोगप्रकरणांवर ते लागू होते?

AI एजंट जटिल कार्ये पूर्ण करण्यासाठी, माहिती मिळवण्यासाठी किंवा निर्णय घेण्यासाठी टूल्सचा उपयोग करू शकतात. टूल वापरण्याचा डिझाइन पॅटर्न बहुधा अशा परिस्थितींमध्ये वापरला जातो जिथे बाह्य प्रणालींशी गतिशील परस्परसंवाद आवश्यक असतो, जसे डेटाबेस, वेब सेवा किंवा कोड इंटरप्रेटर. ही क्षमता अनेक वेगवेगळ्या उपयोगप्रकरणांसाठी उपयुक्त आहे ज्यात समावेश आहे:

- **गतिशील माहिती प्राप्ती:** एजंट्स बाह्य APIs किंवा डेटाबेस कडे क्वेरी करून अद्ययावत डेटा मिळवू शकतात (उदा., डेटा विश्लेषणासाठी SQLite डेटाबेस क्वेरी करणे, स्टॉक किंमती किंवा हवामानाची माहिती मिळवणे).
- **कोड अंमलबजावणी आणि व्याख्या:** एजंट्स गणिती समस्या सोडवण्यासाठी, अहवाल तयार करण्यासाठी किंवा सिम्युलेशन्स करण्यासाठी कोड किंवा स्क्रिप्ट चालवू शकतात.
- **वर्कफ्लो ऑटोमेशन:** टास्क शेड्युलर्स, ईमेल सेवा किंवा डेटा पाईपलाइन्ससारख्या टूल्स एकत्र करून पुनरावर्ती किंवा बहु-चरण वर्कफ्लो स्वयंचलित करणे.
- **ग्राहक समर्थन:** एजंट्स CRM प्रणाली, तिकीट प्रणाली किंवा ज्ञानाधारांशी संवाद साधून वापरकर्त्यांच्या चौकशा सोडवू शकतात.
- **सामग्री निर्मिती आणि संपादन:** व्याकरण तपासक, मजकूर सारांशक, किंवा सामग्री सुरक्षा मूल्यमापन करणारे टूल्स वापरून एजंट्स सामग्री निर्मिती कार्यात मदत करू शकतात.

## टूल वापरण्याच्या डिझाइन पॅटर्नची अंमलबजावणी करण्यासाठी कोणती घटके/बिल्डिंग ब्लॉक्स आवश्यक आहेत?

हे बिल्डिंग ब्लॉक्स AI एजंटला विस्तृत प्रकारची कामे पार पाडण्यास सक्षम करतात. चला टूल वापरण्याच्या डिझाइन पॅटर्नची अंमलबजावणी करण्यासाठी आवश्यक मुख्य घटक पाहू:

- **Function/Tool Schemas**: उपलब्ध साधनांची सविस्तर व्याख्या, ज्यात फंक्शनचे नाव, उद्देश, आवश्यक पॅरामीटर्स आणि अपेक्षित आउटपुट समाविष्ट असतात. या स्कीमामुळे LLM ला कळते की कोणती साधने उपलब्ध आहेत आणि वैध विनंत्या कशा तयार कराव्यात.

- **Function Execution Logic**: वापरकर्त्याच्या हेतू आणि संभाषणाच्या संदर्भानुसार टूल कधी आणि कसे कॉल करायचे हे नियंत्रित करते. यात प्लॅनर मॉड्यूल्स, राउटिंग मेकॅनिझम किंवा शर्तींवर आधारित प्रवाह समाविष्ट असू शकतात जे टूल वापर गतिशीलपणे ठरवतात.

- **Message Handling System**: वापरकर्त्याच्या इनपुट्स, LLM प्रतिसाद, टूल कॉल आणि टूल आउटपुट यांच्यातील संभाषण प्रवाह व्यवस्थापित करणारे घटक.

- **Tool Integration Framework**: एजंटला विविध टूल्सशी कनेक्ट करणारे पायाभूत ढाँचा, मग ते साधी फंक्शन्स असोत किंवा क्लिष्ट बाह्य सेवाच असोत.

- **Error Handling & Validation**: टूल अंमलबजावणीतील अयशस्वी गोष्टी हाताळण्यासाठी, पॅरामीटर्सची पडताळणी करण्यासाठी आणि अनपेक्षित प्रतिसाद व्यवस्थापित करण्यासाठी मेकॅनिझम.

- **State Management**: बहु-टर्न संवादामध्ये सुसंगतता सुनिश्चित करण्यासाठी संभाषण संदर्भ, मागील टूल इंटरॅक्शन्स आणि कायमस्वरूपी डेटा ट्रॅक करते.

आता, Function/Tool Calling बद्दल अधिक तपशिलात पाहूया.
 
### Function/Tool Calling

फंक्शन कॉलिंग हे मोठ्या भाषा मॉडेल्स (LLMs) ला टूल्सशी संवाद साधण्याच्या प्रमुख मार्गापैकी एक आहे. आपण बहुधा 'Function' आणि 'Tool' हे परस्पर वापरलेले पाहाल कारण 'functions' (पुन्हा वापरता येणाऱ्या कोडचे ब्लॉक्स) हेच एजंट्स कार्य करण्यासाठी वापरतील असे 'tools' असतात. एखाद्या फंक्शनचा कोड कॉल होण्यासाठी, LLM ला वापरकर्त्याच्या विनंतीची तुलना फंक्शन्सच्या वर्णनांशी करावी लागते. यासाठी उपलब्ध सर्व फंक्शन्सच्या वर्णनांचा आढावा करणारी एक स्कीमा LLM कडे पाठविली जाते. LLM नंतर कार्यासाठी सर्वात योग्य फंक्शन निवडते आणि त्याचे नाव आणि आर्ग्युमेंट्स परत करते. निवडलेले फंक्शन invoke केले जाते, त्याची प्रतिक्रिया LLM कडे परत पाठविली जाते, आणि LLM त्या माहितीनुसार वापरकर्त्याच्या विनंतीला उत्तर देते.

डेव्हलपर्सना एजंटसाठी फंक्शन कॉलिंग अंमलात आणण्यासाठी, आपल्याला आवश्यक आहे:

1. फंक्शन कॉलिंगला समर्थन करणारे एक LLM मॉडेल
2. फंक्शन वर्णन असलेली स्कीमा
3. प्रत्येक वर्णन केलेल्या फंक्शनसाठी कोड

चलो सॅन फ्रान्सिस्को मधील एखाद्या शहराचा चालू वेळ मिळवण्याच्या उदाहरणाचा वापर करूया:

1. **फंक्शन कॉलिंगला समर्थन करणारे LLM initialized करा:**

    सर्व मॉडेल्स फंक्शन कॉलिंगला समर्थन करीत नाहीत, त्यामुळे तुम्ही वापरत असलेले LLM हे समर्थन करते की नाही हे तपासणे महत्त्वाचे आहे.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> फंक्शन कॉलिंगसाठी समर्थन करते. आपण Azure OpenAI क्लायंट सुरू करून प्रारंभ करू शकतो. 

    ```python
    # Azure OpenAI क्लायंट प्रारंभ करा
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Function Schema तयार करा**:

    पुढे आपण JSON स्कीमा परिभाषित करू ज्यात फंक्शनचे नाव, फंक्शन काय करते याचे वर्णन, आणि फंक्शन पॅरामीटर्सची नावे व वर्णने असतील.
    नंतर आपण ही स्कीमा पूर्वी तयार केलेल्या क्लायंटला पास करू आणि वापरकर्त्याच्या विनंतीसह सॅन फ्रान्सिस्कोमधील वेळ जाणून घेण्यासाठी पाठवू. महत्त्वाचे म्हणजे लक्षात ठेवण्याची गोष्ट ही की **टूल कॉल** परत येतो, **प्रश्नाचे अंतिम उत्तर नाही**. पूर्वी म्हटल्याप्रमाणे, LLM कार्यासाठी निवडलेल्या फंक्शनचे नाव आणि त्यास दिल्या जाणार्‍या आर्ग्युमेंट्स परत करते.

    ```python
    # मॉडेल वाचण्यासाठी कार्याचे वर्णन
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
  
    # प्रारंभिक वापरकर्त्याचा संदेश
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # पहिला API कॉल: मॉडेलला फंक्शन वापरण्यास सांगा
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # मॉडेलच्या प्रतिसादाची प्रक्रिया करा
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **कार्यान्वित करण्यासाठी आवश्यक फंक्शन कोड:**

    आता जेव्हापासून LLM ने कोणते फंक्शन चालवावे हे निवडले आहे, ते कार्य पार पाडणारा कोड अंमलात आणावा आणि चालवावा लागेल.
    आपण Python मध्ये चालू वेळ मिळवण्यासाठी कोड अंमलात आणू शकतो. त्याशिवाय response_message मधून नाव व आर्ग्युमेंट्स काढून अंतिम निकाल मिळवण्यासाठी कोड लिहावे लागेल.

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
     # फंक्शन कॉल्स हाताळणे
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
  
      # दुसरा API कॉल: मॉडेलकडून अंतिम प्रतिसाद मिळवा
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

फंक्शन कॉलिंग हे बहुतेक, कदाचित सर्व एजंट टूल वापरण्याच्या डिझाइनचा हृदय आहे, परंतु ते शून्यापासून अंमलात आणणे कधी कधी आव्हानात्मक असू शकते.
जसे आपण [Lesson 2](../../../02-explore-agentic-frameworks) मध्ये शिकलो तेव्हा agentic फ्रेमवर्क्स आम्हाला टूल वापरण्याची अंमलबजावणी करण्यासाठी पूर्वनिर्मित बिल्डिंग ब्लॉक्स पुरवतात.
 
## एजेंटिक फ्रेमवर्क्ससह टूल वापरण्याची उदाहरणे

येथे विविध agentic फ्रेमवर्क्स वापरून टूल वापरण्याचा डिझाइन पॅटर्न कसा अंमलात आणता येईल याची काही उदाहरणे दिली आहेत:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> ही .NET, Python आणि Java विकसकांसाठी मोठ्या भाषा मॉडेल्स (LLMs) सोबत काम करण्यासाठी एक ओपन-सोर्स AI फ्रेमवर्क आहे. हे फंक्शन कॉलिंग वापरण्याची प्रक्रिया सुलभ करते कारण ते आपल्या फंक्शन्स आणि त्यांच्या पॅरामीटर्सचे वर्णन मॉडेलला आपोआप करते, ज्याला <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">सीरिअलायझिंग</a> म्हणतात. हे मॉडेल आणि आपल्या कोडमधील परस्परसंवादासह मागे-आणि-आगे संभाषण हाताळते. Semantic Kernel सारख्या agentic फ्रेमवर्कचा आणखी एक फायदा म्हणजे ते आपल्याला पूर्वनिर्मित साधनांसारख्या <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> आणि <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a> सारख्या टूल्समध्ये प्रवेश मिळवून देतो.

खालील आकृती Semantic Kernel सह फंक्शन कॉलिंगच्या प्रक्रियेचे स्पष्टीकरण करते:

![फंक्शन कॉलिंग](../../../translated_images/mr/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernel मध्ये फंक्शन्स/टूल्सना <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a> म्हटले जाते. आपण आधी पाहिलेल्या `get_current_time` फंक्शनला एक क्लासमध्ये रूपांतर करून प्लगइन बनवू शकतो. आपण `kernel_function` डेकोरेटर आयात करू शकतो, जो फंक्शनचे वर्णन स्वीकारतो. नंतर जेव्हा आपण GetCurrentTimePlugin सह kernel तयार करतो, तेव्हा kernel आपोआप फंक्शन आणि त्याच्या पॅरामीटर्सचे सीरिअलायझेशन करेल आणि LLM कडे पाठवण्यासाठी स्कीमा तयार करेल.

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

# कर्नेल तयार करा
kernel = Kernel()

# प्लगइन तयार करा
get_current_time_plugin = GetCurrentTimePlugin(location)

# कर्नेलमध्ये प्लगइन जोडा
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> ही एक नवीन agentic फ्रेमवर्क आहे जी विकसकांना सुरक्षितपणे उच्च-गुणवत्तेचे, विस्तारयोग्य AI एजंट तयार, तैनात आणि स्केल करण्यास सक्षम करण्यासाठी डिझाइन केलेली आहे, ज्यासाठी आधारभूत कंप्यूट आणि स्टोरेज संसाधने व्यवस्थापित करण्याची गरज नाही. हे एंटरप्राइझ अनुप्रयोगांसाठी विशेषतः उपयुक्त आहे कारण हे पूर्णपणे व्यवस्थापित सेवा असून एंटरप्राइझ दर्जाच्या सुरक्षिततेसह येते.

LLM API थेट विकसित करण्याच्या तुलनेत, Azure AI Agent Service काही फायदे देते, ज्यात समावेश आहे:

- Automatic tool calling – टूल कॉल पार्स करण्याची, टूल invoke करण्याची आणि प्रतिसाद हाताळण्याची गरज नाही; आता ही सर्व प्रक्रिया सर्व्हर-साइडवर केली जाते
- Securely managed data – आपल्या संभाषण स्थितीचे व्यवस्थापन करण्याऐवजी, आपल्याला आवश्यक सर्व माहिती साठवण्यासाठी आपण threads वर भरोसा करू शकता
- Out-of-the-box tools – Bing, Azure AI Search, आणि Azure Functions सारख्या आपल्या डेटा स्रोतांशी संवाद साधण्यासाठी वापरता येणारी साधने

Azure AI Agent Service मध्ये उपलब्ध टूल्स दोन वर्गात विभागता येतात:

1. Knowledge Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Action Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service आपल्याला या टूल्सना `toolset` म्हणून एकत्र वापरण्याची अनुमती देते. हे `threads` देखील वापरते जे विशिष्ट संभाषणाच्या संदेशांच्या इतिहासावर लक्ष ठेवतात.

कल्पना करा की आपण Contoso नावाच्या कंपनीत विक्री प्रतिनिधी आहात. आपण एक संभाषणात्मक एजंट विकसित करू इच्छिता जो आपल्या विक्री डेटाबद्दलची प्रश्ने उत्तरू शकेल.

खालील प्रतिमा दर्शवते की आपण Azure AI Agent Service चा वापर करून आपल्या विक्री डेटाचे विश्लेषण कसे करू शकता:

![एजेंटिक सेवा क्रियेत](../../../translated_images/mr/agent-service-in-action.34fb465c9a84659e.webp)

सेवा वापरून या टूल्सपैकी कोणतेही वापरण्यासाठी आपण क्लायंट तयार करू शकतो आणि टूल किंवा टूलसेट परिभाषित करू शकतो. हे प्रत्यक्षात अंमलात आणण्यासाठी आपण खालील Python कोड वापरू शकतो. LLM टूलसेट पहाळून ठरवेल की वापरकर्त्याद्वारे तयार केलेले फंक्शन `fetch_sales_data_using_sqlite_query` वापरायचे आहे की प्री-बिल्ट Code Interpreter वापरायचा हे वापरकर्त्याच्या विनंतीनुसार.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query फंक्शन जे fetch_sales_data_functions.py फाईलमध्ये आढळते.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# टूलसेट प्रारंभ करा
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query फंक्शनसह फंक्शन कॉल करणारा एजंट प्रारंभ करा आणि तो टूलसेटमध्ये जोडा
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Code Interpreter टूल प्रारंभ करा आणि ते टूलसेटमध्ये जोडा
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## टूल वापरण्याच्या डिझाइन पॅटर्नचा वापर करून विश्वासार्ह AI एजंट तयार करण्यासाठी कोणत्या विशेष बाबी विचारात घ्याव्यात?

LLMs द्वारा डायनॅमिकली निर्माण केलेल्या SQL शी संबंधित एक सामान्य चिंता सुरक्षा आहे, विशेषतः SQL इंजेक्शन किंवा डेटाबेस ड्रॉप करण्यासारख्या घातक क्रियांचे धोके. या चिंतांचा आधार असल्याने, योग्य प्रकारे डेटाबेस प्रवेश परवानग्या कॉन्फिगर करून त्यांचे प्रभावीपणे समाधान करता येऊ शकते. बहुतांश डेटाबेससाठी याचा अर्थ डेटाबेसला रीड-ओनली म्हणून कॉन्फिगर करणे आहे. PostgreSQL किंवा Azure SQL सारख्या डेटाबेस सेवांसाठी, अॅपला रीड-ओनली (SELECT) भूमिका देणे आवश्यक आहे.

अॅप सुरक्षित वातावरणात चालविल्यास संरक्षण अधिक वाढते. एंटरप्राइझ परिस्थितींमध्ये, डेटा सहसा ऑपरेशनल सिस्टममधून बाहेर काढला आणि रीड-ओनली डेटाबेस किंवा डेटा वेअरहाउसमध्ये रूपांतरित केला जातो ज्याचे स्कीमा वापरकर्ता-अनुकूल असते. हा दृष्टिकोन खात्री करतो की डेटा सुरक्षित आहे, कार्यक्षमता आणि प्रवेशयोग्यता यांसाठी ऑप्टिमाइझ केलेला आहे, आणि अॅपला मर्यादित, रीड-ओनली प्रवेश आहे.

## नमुना कोड
- Python: [एजंट फ्रेमवर्क](./code_samples/04-python-agent-framework.ipynb)
- .NET: [एजंट फ्रेमवर्क](./code_samples/04-dotnet-agent-framework.md)

## उपकरण वापर डिझाइन पॅटर्नबद्दल अजून प्रश्न आहेत का?

इतर शिकणाऱ्यांसोबत भेटण्यासाठी, ऑफिस तासांमध्ये सहभागी होण्यासाठी आणि आपल्या AI एजंट्ससंबंधी प्रश्नांची उत्तरे मिळवण्यासाठी [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) मध्ये सामील व्हा.

## अतिरिक्त संसाधने

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents सेवा कार्यशाळा</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer मल्टी-एजंट कार्यशाळा</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel फंक्शन कॉलिंग ट्यूटोरिअल</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel कोड इंटरप्रेटर</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen साधने</a>

## मागील धडा

[एजेंटिक डिझाइन पॅटर्न समजून घेणे](../03-agentic-design-patterns/README.md)

## पुढील धडा

[एजेंटिक RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
अस्वीकरण:
हे दस्तऐवज AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) वापरून अनुवादित केले गेले आहे. आम्ही अचूकतेसाठी प्रयत्न करतो, तरीही कृपया लक्षात घ्या की स्वयंचलित अनुवादांमध्ये त्रुटी किंवा अचूकतेची कमतरता असू शकते. मूळ भाषेतील दस्तऐवजाला अधिकृत स्रोत मानले पाहिजे. महत्त्वाच्या माहितीकरिता व्यावसायिक मानवी अनुवाद करण्याची शिफारस केली जाते. या अनुवादाच्या वापरामुळे उद्भवलेल्या कोणत्याही गैरसमजुतीं किंवा चुकीच्या अर्थबाह्यतेबद्दल आम्ही जबाबदार नाही.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->