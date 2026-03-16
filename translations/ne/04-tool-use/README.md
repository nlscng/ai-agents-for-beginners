[![राम्रो AI एजेन्टहरु कसरी डिजाइन गर्ने](../../../translated_images/ne/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(यो पाठको भिडियो हेर्न माथिको तस्वीरमा क्लिक गर्नुहोस्)_

# उपकरण प्रयोग डिजाइन ढाँचा

उपकरणहरू रोचक हुन्छन् किनकि तिनीहरूले AI एजेन्टहरूलाई क्षमताहरूको विस्तृत दायरा राख्न अनुमति दिन्छ। एजेन्टसँग सीमित कार्यहरूको सेट हुने सट्टा, उपकरण थपेर, एजेन्टले अब कार्यहरूको व्यापक दायरा सम्पन्न गर्न सक्छ। यस अध्यायमा, हामी उपकरण प्रयोग डिजाइन ढाँचामा हेर्नेछौं, जुनले वर्णन गर्दछ कि AI एजेन्टहरूले कसरी विशिष्ट उपकरणहरू प्रयोग गरेर आफ्ना लक्ष्यहरू प्राप्त गर्न सक्छन्।

## परिचय

यस पाठमा, हामी निम्न प्रश्नहरूको उत्तर खोज्दैछौं:

- उपकरण प्रयोग डिजाइन ढांचा के हो?
- यसलाई लागू गर्न सकिने प्रयोग केसहरू के हुन्?
- डिजाइन ढांचा कार्यान्वयन गर्न आवश्यक तत्वहरू/निर्माण खण्डहरू के हुन्?
- भरोसायोग्य AI एजेन्टहरू निर्माण गर्न उपकरण प्रयोग डिजाइन ढाँचा प्रयोग गर्दा के विशेष विचारहरू हुन्छन्?

## सिकाइ लक्ष्यहरू

यस पाठ पूरा गरेपछि, तपाईं सक्षम हुनुहुनेछ:

- उपकरण प्रयोग डिजाइन ढाँचा र यसको उद्देश्य परिभाषित गर्न।
- उपकरण प्रयोग डिजाइन ढांचा लागू गर्न सकिने प्रयोग केसहरू पहिचान गर्न।
- डिजाइन ढाँचा कार्यान्वयन गर्न आवश्यक प्रमुख तत्वहरू बुझ्न।
- यस डिजाइन ढाँचा प्रयोग गरेर AI एजेन्टहरूमा भरोसायोग्यता सुनिश्चित गर्ने विचारहरू पहिचान गर्न।

## उपकरण प्रयोग डिजाइन ढाँचा के हो?

**उपकरण प्रयोग डिजाइन ढाँचा** ले LLMs लाई बाह्य उपकरणहरूसँग अन्तरक्रिया गर्ने क्षमता दिन केन्द्रित छ ताकि विशिष्ट लक्ष्यहरू प्राप्त गर्न सकियोस्। उपकरणहरू कोड हुन् जुन एजेन्टले कार्यहरू गर्नका लागि सञ्चालन गर्न सक्छ। उपकरण एउटा साधारण फ़ंक्शन हुन सक्छ जस्तै क्याल्कुलेटर, वा तेस्रो-पक्ष सेवाको API कल जस्तै स्टक मूल्य खोज वा मौसम पूर्वानुमान। AI एजेन्टहरूको सन्दर्भमा, उपकरणहरू मोडेल-उत्पन्न फ़ंक्शन कलहरूको प्रतिक्रिया स्वरूप एजेन्टले सञ्चालन गर्न डिजाइन गरिएका हुन्छन्।

## कुन प्रयोग केसहरूमा यसलाई लागू गर्न सकिन्छ?

AI एजेन्टहरू जटिल कार्यहरू पूरा गर्न, सूचना प्राप्त गर्न, वा निर्णय लिन उपकरणहरूको उपयोग गर्न सक्छन्। उपकरण प्रयोग डिजाइन ढाँचा प्रायः गतिशील अन्तरक्रिया आवश्यक पर्ने स्थिति, जस्तै डेटाबेस, वेब सेवाहरू, वा कोड व्याख्याकारहरूसँग सम्बन्धित हुन्छ। यो क्षमता विभिन्न प्रयोग केसहरूमा उपयोगी छ जसमा समावेश छन्:

- **गतिशील सूचना प्राप्ति:** एजेन्टहरूले बाह्य APIs वा डेटाबेसहरूलाई सोध्न सक्छन् ताजा डाटा ल्याउन (जस्तै, डेटा विश्लेषणका लागि SQLite डेटाबेस सोध्नु, स्टक मूल्य वा मौसम जानकारी ल्याउनु)।
- **कोड कार्यान्वयन र व्याख्या:** एजेन्टहरूले गणितीय समस्या समाधान गर्न, प्रतिवेदन सिर्जना गर्न, वा सिमुलेशन गर्न कोड वा स्क्रिप्टहरू चलाउन सक्छन्।
- **कार्यप्रवाह स्वचालन:** कार्य अनुसूचक, इमेल सेवा, वा डाटा पाइपलाइनजस्ता उपकरणहरू एकीकृत गरी पुनरावृत्ति वा बहु-चरण कार्यप्रवाहहरू स्वचालित बनाउनु।
- **ग्राहक सहायता:** एजेन्टहरूले CRM प्रणालीहरू, टिकटिङ प्लेटफर्महरू, वा ज्ञान आधारहरूसँग अन्तरक्रिया गरेर प्रयोगकर्ता प्रश्नहरू समाधान गर्न सक्छन्।
- **सामग्री सिर्जना र सम्पादन:** एजेन्टहरूले व्याकरण जाँचक, पाठ सारांशक, वा सामग्री सुरक्षा मुल्यांकनकर्ताजस्ता उपकरणहरूलाई सामग्री सिर्जना कार्यहरूमा सहायता पुर्याउन प्रयोग गर्न सक्छन्।

## उपकरण प्रयोग डिजाइन ढाँचा कार्यान्वयन गर्न आवश्यक तत्वहरू के छन्?

यी निर्माण खण्डहरूले AI एजेन्टलाई कार्यहरूको विस्तृत दायरा सम्पन्न गर्न अनुमति दिन्छन्। उपकरण प्रयोग डिजाइन ढाँचा लागू गर्न आवश्यक प्रमुख तत्वहरू यसप्रकार छन्:

- **फ़ंक्शन/उपकरण स्कीमा**: उपलब्ध उपकरणहरूको विस्तृत परिभाषा, जसमध्ये फ़ंक्शन नाम, उद्देश्य, आवश्यक प्यारामीटरहरू, र अपेक्षित आउटपुटहरू समावेश हुन्छ। यी स्कीमाले LLM लाई कुन उपकरणहरू उपलब्ध छन् र मान्य अनुरोध कसरी निर्माण गर्ने बुझ्न सक्षम बनाउँछन्।

- **फ़ंक्शन कार्यान्वयन तर्क**: प्रयोगकर्ताको आशय र संवाद सन्दर्भ अनुसार उपकरणहरू कहिले र कसरी बोलाइने निर्धारण गर्दछ। यसमा योजनाकार मोड्युलहरू, राउटिङ संयन्त्रहरू, वा सशर्त प्रवाहहरू समावेश हुन सक्छन् जुन उपकरण प्रयोग गतिशील रूपमा निर्धारण गर्छन्।

- **सन्देश ह्यान्डलिंग सिस्टम**: प्रयोगकर्ता इनपुट, LLM प्रतिक्रिया, उपकरण कॉलहरू, र उपकरण आउटपुटहरू बीचको संवाद प्रवाह व्यवस्थापन गर्ने कम्पोनेन्टहरू।

- **उपकरण एकीकरण फ्रेमवर्क**: एजेन्टलाई विभिन्न उपकरणहरूसँग जडान गर्ने पूर्वाधार, चाहे तिनीहरू साधारण फ़ंक्शनहरू हुन् या जटिल बाह्य सेवाहरू।

- **त्रुटि ह्यान्डलिंग र मान्यकरण**: उपकरण सञ्चालनमा विफलता सम्हाल्ने, प्यारामीटरहरू मान्य गर्ने, र अप्रत्याशित प्रतिक्रियाहरू व्यवस्थापन गर्ने संयन्त्रहरू।

- **अवस्था व्यवस्थापन**: बहु-चरण अन्तरक्रियाहरूमा निरन्तरता सुनिश्चित गर्न संवाद सन्दर्भ, पहिलेका उपकरण अन्तरक्रियाहरू, र दिर्घकालीन डेटा ट्र्याक गर्ने।

अब, Function/Tool Calling लाई विस्तारमा हेरौं।

### Function/Tool Calling

फ़ंक्शन कल LLMs लाई उपकरणहरूसँग अन्तरक्रिया गर्न मुख्य तरिका हो। तपाईंले प्रायः 'फ़ंक्शन' र 'उपकरण' साटासाट प्रयोग गरिँदै गरेको देख्नुहुनेछ किनकि 'फ़ंक्शन' (पुन: प्रयोग गर्न मिल्ने कोडका ब्लकहरू) नै एजेन्टहरूले कार्यहरू गर्न प्रयोग गर्ने 'उपकरण' हुन्। फ़ंक्शनको कोड कल गर्नका लागि, LLM ले प्रयोगकर्ताको अनुरोधलाई फ़ंक्शनको विवरणसँग तुलना गर्नुपर्छ। यसको लागि सबै उपलब्ध फ़ंक्शनहरूको विवरण भएको स्कीमा LLM लाई पठाइन्छ। LLM ले कार्यका लागि सबैभन्दा उपयुक्त फ़ंक्शन चयन गर्छ र त्यसको नाम र तर्कहरू फिर्ता गर्छ। चयन गरेको फ़ंक्शन कल गरिन्छ, त्यसको प्रतिक्रिया LLM लाई पठाइन्छ, जसले प्रयोगकर्ताको अनुरोधको जवाफ तयार पार्न त्यो जानकारी प्रयोग गर्छ।

एजेन्टहरूको लागि फ़ंक्शन कल कार्यान्वयन गर्न विकासकर्ता तलका चीजहरू चाहिन्छन्:

1. Function Calling समर्थन गर्ने LLM मोडल
2. फ़ंक्शन विवरणहरू समावेश गरिएको स्कीमा
3. प्रत्येक फ़ंक्शनको कार्यान्वयन कोड

साँच्चै समय हरेक शहरमा पत्ता लगाउने उदाहरण प्रयोग गरौं:

1. **Function Calling समर्थन गर्ने LLM सुरु गर्नुहोस्:**

    सबै मोडलहरूले Function Calling समर्थन गर्दैनन्, त्यसैले तपाईंले प्रयोग गरिरहेको LLM ले सम्मिलित गरेको छ कि छैन हेर्नु महत्त्वपूर्ण छ। <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> ले Function Calling समर्थन गर्दछ। हामी Azure OpenAI क्लाइन्ट सुरु गरेर सुरू गर्न सक्छौं।

    ```python
    # Azure OpenAI क्लाइन्ट सुरु गर्नुहोस्
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Function Schema तयार गर्नुहोस्:**

    अब हामी JSON स्कीमा परिभाषित गर्नेछौं जसमा फ़ंक्शन नाम, फ़ंक्शन के गर्छ भन्ने विवरण, र फ़ंक्शनका प्यारामीटरहरूको नाम र विवरण हुन्छ। 
    त्यसपछि हामी यो स्कीमालाई पहिले सिर्जना गरिएको क्लाइन्टमा प्रयोगकर्ताको अनुरोधसँगै पठाउनेछौं जसले सां फ्रान्सिस्कोको समय पत्ता लगाउने छ। महत्वका कुरा भनेको **tool call** फिर्ता हुन्छ, प्रश्नको अन्तिम जवाफ होइन। जस्तै पहिले भनिएको थियो, LLM ले कार्यका लागि चयन गरेको फ़ंक्शनको नाम र तर्कहरू फिर्ता गर्छ।

    ```python
    # मोडेलले पढ्नको लागि कार्य विवरण
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
  
    # प्रारम्भिक प्रयोगकर्ता सन्देश
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # पहिलो API आह्वान: मोडेललाई फंक्शन प्रयोग गर्न भनौं
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # मोडेलको प्रतिक्रिया प्रक्रिया गर्नुहोस्
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **कार्य सम्पन्न गर्न आवश्यक फ़ंक्शन कोड:**

    अब LLM ले कुन फ़ंक्शन चलाउनुपर्ने निर्धारण गरेपछि, त्यो कार्य सम्पन्न गर्ने कोड कार्यान्वयन र चलाउनु पर्छ।
    हामी पाइथनमा वर्तमान समय प्राप्त गर्ने कोड लेख्न सक्छौं। साथै अन्तिम नतिजा निकाल्न प्रतिक्रिया सन्देशबाट नाम र तर्क निकाल्ने कोड पनि लेख्न आवश्यक छ।

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
     # कार्य कलहरू ह्यान्डल गर्नुहोस्
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
  
      # दोस्रो API कल: मोडेलबाट अन्तिम प्रतिक्रिया प्राप्त गर्नुहोस्
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

Function Calling अधिकांश, यदि सबै होइन भने अगेन्ट उपकरण प्रयोग डिजाइनको मुटुमा हुन्छ, तर यसलाई स्क्र्याचबाट कार्यान्वयन गर्नु कहिलेकाहीं चुनौतीपूर्ण हुन सक्छ।
जस्तै [पाठ 2](../../../02-explore-agentic-frameworks) मा सिक्यौं, एजेन्टिक फ्रेमवर्कहरूले उपकरण प्रयोग कार्यान्वयन गर्न पूर्वनिर्मित निर्माण खण्डहरू उपलब्ध गराउँछन्।

## Agentic फ्रेमवर्कहरू संग उपकरण प्रयोगका उदाहरणहरू

यहाँ विभिन्न एजेन्टिक फ्रेमवर्कहरू प्रयोग गरेर उपकरण प्रयोग डिजाइन ढाँचा कसरी कार्यान्वयन गर्ने केही उदाहरणहरू छन्:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> एक खुला स्रोत AI फ्रेमवर्क हो जसले .NET, Python, र Java विकासकर्ताहरूलाई Large Language Models (LLMs) सँग काम गर्न सहायता पुर्याउँछ। यसले Function Calling प्रक्रिया सजिलो बनाउँछ, जसमा आफ्ना functions र तिनका प्यारामीटरहरूको विवरण मोडेललाई स्वचालित रूपमा <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">सिरीयलाइज</a> गर्ने प्रक्रिया मार्फत पठाउने काम गर्दछ। यसले मोडेल र तपाईंको कोडबीचको द्विपक्षीय संचार पनि व्यवस्थापन गर्दछ। Semantic Kernel जस्ता एजेन्टिक फ्रेमवर्क प्रयोग गर्दा अर्काे फाइदा भनेको हामीले <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> र <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a> जस्ता पूर्वनिर्मित उपकरणहरू पहुँच गर्न सकिन्छ।

तलको आरेखले Semantic Kernel मार्फत Function Calling प्रक्रिया देखाउँछ:

![function calling](../../../translated_images/ne/functioncalling-diagram.a84006fc287f6014.webp)

Semantic Kernel मा functions/उपकरणहरूलाई <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a> भनिन्छ। हामीले पहिले देखेको `get_current_time` फ़ंक्शनलाई Plugin मा रूपान्तरण गर्न सक्छौं जसमा त्यो फ़ंक्शन भएको एक क्लास बनाउने छौं। हामीले `kernel_function` डेकोरेटर आयात गर्न सक्छौं जसले फ़ंक्शनको विवरण लिन्छ। जब तपाईं GetCurrentTimePlugin संग kernel सिर्जना गर्नुहुन्छ, त्यो kernel स्वतः फ़ंक्शन र त्यसका प्यारामीटरहरू सिरीयलाइज गरेर LLM लाई पठाउन स्कीमा बनाउँछ।

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

# कर्नेल सिर्जना गर्नुहोस्
kernel = Kernel()

# प्लगइन सिर्जना गर्नुहोस्
get_current_time_plugin = GetCurrentTimePlugin(location)

# कर्नेलमा प्लगइन थप्नुहोस्
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> नयाँ एजेन्टिक फ्रेमवर्क हो जुन विकासकर्ताहरूलाई सुरक्षित रूपमा उच्च गुणस्तर र विस्तारयोग्य AI एजेन्टहरू निर्माण, डिप्लोय, र स्केल गर्न अनुमति दिन डिजाइन गरिएको हो, underlying compute र storage संसाधनहरू व्यवस्थापन नगरी। यो विशेष गरी enterprisew applications को लागि उपयोगी छ किनभने यो पूर्ण रूपमा प्रबन्धित सेवा हो र enterprise ग्रेड सुरक्षा प्रदान गर्दछ।

LLM API सँग सिधै विकास गर्ने तुलना गर्दा, Azure AI Agent Service ले केही फाइदाहरू दिन्छ:

- स्वचालित उपकरण कल – उपकरण कल पार्स गर्न, उपकरण डाका र प्रतिक्रिया सम्हाल्न आवश्यक छैन; यी सबै अब server-side मा हुन्छ।
- सुरक्षित रूपमा व्यवस्थापन गरिएका डेटा – आफ्नो संवाद अवस्था व्यवस्थापन गर्ने सट्टा, तपाईंले सबै आवश्यक जानकारी स्टोर गर्न थ्रेडहरूमा निर्भर गर्न सक्नुहुन्छ।
- आउट-अफ-द-बक्स उपकरणहरू – तपाईंको डाटा स्रोतहरू जस्तै Bing, Azure AI Search, र Azure Functions सँग अन्तरक्रिया गर्न प्रयोग गर्न सकिने उपकरणहरू।

Azure AI Agent Service मा उपलब्ध उपकरणहरू दुई वर्गमा विभाजन गर्न सकिन्छ:

1. ज्ञान उपकरणहरू:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing Search द्वारा ग्राउन्डिंग</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. कार्य उपकरणहरू:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI परिभाषित उपकरणहरू</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service ले यी उपकरणहरूलाई `toolset` को रूपमा सँगै प्रयोग गर्न अनुमति दिन्छ। यो `threads` को पनि उपयोग गर्छ जसले एउटा विशेष संवादको सन्देश इतिहास ट्र्याक गर्छ।

कल्पना गर्नुहोस् तपाईं Contoso नामको कम्पनीमा बिक्री एजेन्ट हुनुहुन्छ। तपाईं बिक्री डेटा सम्बन्धी प्रश्नहरूको उत्तर दिन सक्ने संवादात्मक एजेन्ट विकास गर्न चाहनुहुन्छ।

तलको छवि Azure AI Agent Service ले तपाईंको बिक्री डेटा विश्लेषण गर्न कसरी प्रयोग गर्न सकिन्छ देखाउँछ:

![Agentic Service In Action](../../../translated_images/ne/agent-service-in-action.34fb465c9a84659e.webp)

यी उपकरणहरूमध्ये कुनै पनि सेवा सँग प्रयोग गर्न हामी क्लाइन्ट बनाउने र एक उपकरण वा उपकरण समूह परिभाषित गर्नेछौं। व्यावहारिक रूपमा कार्यान्वयन गर्न हामी तलको पाइथन कोड प्रयोग गर्न सक्छौं। LLM ले उपकरण समूहलाई हेरेर प्रयोगकर्ताले सिर्जना गरेको फ़ंक्शन `fetch_sales_data_using_sqlite_query` वा पूर्वनिर्मित Code Interpreter प्रयोग गर्ने निर्णय गर्नेछ।

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query कार्य जसलाई fetch_sales_data_functions.py फाइलमा फेला पार्न सकिन्छ।
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# उपकरण सेट सुरू गर्नुहोस्
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query कार्यसँग function calling agent प्रारम्भ गर्नुहोस् र यसलाई उपकरण सेटमा थप्नुहोस्
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Code Interpreter उपकरण प्रारम्भ गर्नुहोस् र यसलाई उपकरण सेटमा थप्नुहोस्।
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## भरोसायोग्य AI एजेन्टहरू निर्माण गर्न उपकरण प्रयोग डिजाइन ढाँचा प्रयोग गर्दा विशेष विचारहरू के हुन्?

LLM द्वारा गतिशील रूपमा सिर्जना गरिएको SQL सँग सामान्य चिन्ता सुरक्षा सम्बन्धी हुन्छ, जुनमा SQL injection वा दुष्ट कार्यहरू (जस्तै डेटाबेस ड्रप गर्ने वा छेर्नेजस्ता) को जोखिम पनि पर्दछ। यस्ता चिन्ताहरू वास्तविक भए पनि, डेटाबेस पहुँच अनुमति उचित रूपमा कन्फिगर गरेर प्रभावकारी रूपमा कम गर्न सकिन्छ। अधिकांश डेटाबेसहरूको लागि यो डेटाबेसलाई read-only रूपमा कन्फिगर गर्ने हो। PostgreSQL वा Azure SQL जस्ता डेटाबेस सेवाहरूमा, एपलाई read-only (SELECT) भूमिका प्रदान गर्नु पर्छ।

एपलाई सुरक्षित वातावरणमा चलाउनु थप सुरक्षा प्रदान गर्दछ। उद्यम स्थितिहरूमा, डेटा सामान्यतया सञ्चालन प्रणालीहरूबाट निकालेर read-only डेटाबेस वा डाटा वेयरहाउसमा रूपान्तरण गरिन्छ जसमा प्रयोगकर्तामैत्री स्कीमा हुन्छ। यसले सुनिश्चित गर्छ कि डेटा सुरक्षित छ, प्रदर्शन र पहुँचका लागि अनुकूलित छ, र एपलाई सीमित, read-only पहुँच मात्र छ।

## नमूना कोडहरू
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## उपकरण प्रयोग डिजाइन ढाँचाहरू सम्बन्धी थप प्रश्नहरू छन्?

अरू सिक्नेहरूसँग भेट्न, अफिस आवरहरूमा सहभागी हुन र तपाईंका AI एजेन्ट सम्बन्धी प्रश्नहरूको उत्तर पाउन [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) मा सामेल हुनुहोस्।

## अतिरिक्त स्रोतहरू

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## अघिल्लो पाठ

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## अर्को पाठ

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**अस्वीकरण**:
यो कागजात AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) प्रयोग गरी अनुवाद गरिएको हो। हामी शुद्धताका लागि प्रयासरत छौं, तर कृपया ध्यान दिनुहोस् कि स्वचालित अनुवादमा त्रुटि वा अनुचितता हुन सक्छ। मूल कागजात यसको स्थानीय भाषामा नै आधिकारिक स्रोत मानिनु पर्छ। महत्वपूर्ण जानकारीका लागि व्यावसायिक मानवीय अनुवाद सिफारिस गरिन्छ। यस अनुवादको प्रयोगबाट उत्पन्न हुने कुनै पनि गलतफहमी वा व्याख्यामा हामी जिम्मेवार छैनौं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->