[![कैसे डिजाइन करें अच्छे AI एजेंट](../../../translated_images/hi/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(इस पाठ का वीडियो देखने के लिए ऊपर छवि पर क्लिक करें)_

# टूल उपयोग डिज़ाइन पैटर्न

टूल्स दिलचस्प हैं क्योंकि वे AI एजेंट्स को अधिक व्यापक क्षमताओं की अनुमति देते हैं। एजेंट के पास केवल सीमित क्रियाओं का सेट होने के बजाय, टूल जोड़ने से एजेंट अब कई तरह की क्रियाएँ कर सकता है। इस अध्याय में, हम टूल उपयोग डिज़ाइन पैटर्न पर चर्चा करेंगे, जो बताता है कि AI एजेंट विशिष्ट टूल्स का उपयोग करके अपने लक्ष्यों को कैसे प्राप्त कर सकते हैं।

## परिचय

इस पाठ में, हम निम्नलिखित प्रश्नों के उत्तर खोजने का प्रयास करेंगे:

- टूल उपयोग डिज़ाइन पैटर्न क्या है?
- किन उपयोग मामलों में इसका प्रयोग किया जा सकता है?
- डिज़ाइन पैटर्न को लागू करने के लिए आवश्यक तत्व/निर्माण खंड क्या हैं?
- विश्वसनीय AI एजेंट बनाने के लिए टूल उपयोग डिज़ाइन पैटर्न का उपयोग करते समय क्या विशेष विचार करने चाहिए?

## सीखने के उद्देश्य

इस पाठ को पूरा करने के बाद, आप सक्षम होंगे:

- टूल उपयोग डिज़ाइन पैटर्न और उसके उद्देश्य को परिभाषित करना।
- उन उपयोग मामलों की पहचान करना जहाँ टूल उपयोग डिज़ाइन पैटर्न लागू हो सकता है।
- डिज़ाइन पैटर्न को लागू करने के लिए आवश्यक मुख्य तत्वों को समझना।
- इस डिज़ाइन पैटर्न का उपयोग करने वाले AI एजेंट्स में विश्वसनीयता सुनिश्चित करने के लिए विचारों को पहचानना।

## टूल उपयोग डिज़ाइन पैटर्न क्या है?

**टूल उपयोग डिज़ाइन पैटर्न** LLMs को बाहरी टूल्स के साथ इंटरैक्ट करने की क्षमता देता है ताकि विशिष्ट लक्ष्य पूरे किए जा सकें। टूल्स ऐसे कोड होते हैं जिन्हें एजेंट द्वारा क्रियान्वित किया जा सकता है। एक टूल एक सरल फ़ंक्शन हो सकता है जैसे कैलकुलेटर, या तीसरे पक्ष की सेवा के लिए API कॉल जैसे स्टॉक प्राइस लुकअप या मौसम पूर्वानुमान। AI एजेंट्स के संदर्भ में, टूल्स एजेंट द्वारा **मॉडल-जनित फ़ंक्शन कॉल्स** के जवाब में चलाने के लिए डिज़ाइन किए गए होते हैं।

## किन उपयोग मामलों में इसका प्रयोग किया जा सकता है?

AI एजेंट्स टूल्स का उपयोग जटिल कार्यों को पूरा करने, जानकारी प्राप्त करने, या निर्णय लेने के लिए कर सकते हैं। टूल उपयोग डिज़ाइन पैटर्न अक्सर उन परिदृश्यों में उपयोग होता है जहां बाहरी प्रणालियों, जैसे डेटाबेस, वेब सर्विसेज़, या कोड इंटरप्रेटर के साथ गतिशील इंटरैक्शन आवश्यक हो। इसकी उपयोगिता कई विभिन्न उपयोग मामलों में होती है, जैसे:

- **गतिशील सूचना पुनःप्राप्ति:** एजेंट बाहरी APIs या डेटाबेस से नवीनतम डेटा प्राप्त कर सकते हैं (जैसे SQLite डेटाबेस से डेटा विश्लेषण के लिए प्रश्न करना, स्टॉक कीमतें या मौसम जानकारी प्राप्त करना)।
- **कोड निष्पादन और व्याख्या:** एजेंट गणितीय समस्याओं को हल करने, रिपोर्ट बनाने, या सिमुलेशन करने के लिए कोड या स्क्रिप्ट चला सकते हैं।
- **कार्यप्रवाह स्वचालन:** टास्क शेड्यूलर्स, ईमेल सेवाएं, या डेटा पाइपलाइनों जैसे टूल्स को एकीकृत करके पुनरावृत्त या बहु-चरण प्रक्रियाओं का स्वचालन।
- **ग्राहक समर्थन:** एजेंट CRM सिस्टम, टिकटिंग प्लेटफॉर्म, या ज्ञान आधार से इंटरैक्ट कर उपयोगकर्ता प्रश्नों को हल कर सकते हैं।
- **सामग्री निर्माण और संपादन:** एजेंट ग्रामर चेकर, टेक्स्ट समरी, या कंटेंट सेफ्टी मूल्यांकन जैसे टूल्स का उपयोग सामग्री निर्माण कार्यों में सहायता के लिए कर सकते हैं।

## टूल उपयोग डिज़ाइन पैटर्न को लागू करने के लिए आवश्यक तत्व/निर्माण खंड क्या हैं?

ये निर्माण खंड AI एजेंट को विभिन्न कार्यों को करने में सक्षम बनाते हैं। टूल उपयोग डिज़ाइन पैटर्न लागू करने के लिए मुख्य तत्व निम्नलिखित हैं:

- **फ़ंक्शन/टूल स्कीमाज़:** उपलब्ध टूल्स की विस्तृत परिभाषाएँ, जिनमें फ़ंक्शन का नाम, उद्देश्य, आवश्यक पैरामीटर, और अपेक्षित आउटपुट शामिल हैं। ये स्कीमा LLM को यह समझने में मदद करते हैं कि कौन से टूल्स उपलब्ध हैं और वैध अनुरोध कैसे बनाएँ।

- **फ़ंक्शन निष्पादन तर्क:** निर्धारित करता है कि उपयोगकर्ता की इच्छा और संवाद के संदर्भ के आधार पर टूल्स कब और कैसे कॉल किए जाएं। इसमें योजना बनाने वाले मॉड्यूल, रूटिंग तंत्र, या सशर्त प्रवाह शामिल हो सकते हैं जो गतिशील रूप से टूल उपयोग को नियंत्रित करते हैं।

- **संदेश प्रबंधन प्रणाली:** उपयोगकर्ता इनपुट, LLM प्रतिक्रियाएं, टूल कॉल, और टूल आउटपुट के बीच वार्तालाप प्रवाह को प्रबंधित करने वाले घटक।

- **टूल एकीकरण फ्रेमवर्क:** वह अवसंरचना जो एजेंट को विभिन्न टूल्स से जोड़ती है, चाहे वे सरल फ़ंक्शन हों या जटिल बाहरी सेवाएं।

- **त्रुटि प्रबंधन और सत्यापन:** टूल निष्पादन में विफलताओं को संभालने, पैरामीटर वैधता जांचने, और अप्रत्याशित प्रतिक्रियाओं का प्रबंधन करने के लिए तंत्र।

- **स्थिति प्रबंधन:** संवाद संदर्भ, पिछले टूल इंटरैक्शन, और सतत डेटा को ट्रैक करता है ताकि बहु-चरण इंटरैक्शन में निरंतरता बनी रहे।

अब, आइए फ़ंक्शन/टूल कॉलिंग को और विस्तार में देखें।

### फ़ंक्शन/टूल कॉलिंग

फ़ंक्शन कॉलिंग वह मुख्य तरीका है जिससे हम LLMs को टूल्स के साथ इंटरैक्ट करने के लिए सक्षम बनाते हैं। अक्सर 'फ़ंक्शन' और 'टूल' को समानार्थी रूप में उपयोग किया जाता है क्योंकि 'फ़ंक्शंस' (पुन: उपयोग योग्य कोड ब्लॉक) वे 'टूल्स' हैं जिन्हें एजेंट कार्यों को पूरा करने के लिए उपयोग करते हैं। किसी फ़ंक्शन के कोड को कॉल करने के लिए, LLM को उपयोगकर्ता के अनुरोध की तुलना फ़ंक्शन के विवरण से करनी होती है। इसके लिए, उन सभी उपलब्ध फ़ंक्शंस के विवरणों वाला स्कीमा LLM को भेजा जाता है। LLM फिर कार्य के लिए सबसे उपयुक्त फ़ंक्शन का चयन करता है और उसका नाम तथा तर्क वापस करता है। चयनित फ़ंक्शन को कॉल किया जाता है, उसकी प्रतिक्रिया LLM को वापस भेजी जाती है, जो उस जानकारी का उपयोग उपयोगकर्ता के अनुरोध का उत्तर देने में करता है।

डेवलपर्स के लिए एजेंट्स के लिए फ़ंक्शन कॉलिंग लागू करने के लिए, आपको चाहिए:

1. ऐसा LLM मॉडल जो फ़ंक्शन कॉलिंग का समर्थन करता हो
2. फ़ंक्शन विवरणों वाला स्कीमा
3. प्रत्येक फ़ंक्शन के लिए कोड जो वर्णित है

शहर में वर्तमान समय प्राप्त करने के उदाहरण का उपयोग करते हैं:

1. **ऐसा LLM शुरू करें जो फ़ंक्शन कॉलिंग का समर्थन करता हो:**

    सभी मॉडल फ़ंक्शन कॉलिंग का समर्थन नहीं करते, इसलिए यह जांचना महत्वपूर्ण है कि आपका LLM ऐसा करता है। <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> फ़ंक्शन कॉलिंग का समर्थन करता है। हम Azure OpenAI क्लाइंट को इनिशिएट करना शुरू कर सकते हैं।

    ```python
    # Azure OpenAI क्लाइंट को प्रारंभ करें
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```
  
1. **फ़ंक्शन स्कीमा बनाएँ:**

    अगला कदम JSON स्कीमा परिभाषित करना है जिसमें फ़ंक्शन का नाम, क्या करता है इसका विवरण, और फ़ंक्शन पैरामीटर के नाम और विवरण शामिल हैं।
    फिर हम इस स्कीमा को पहले बनाए गए क्लाइंट को उपयोगकर्ता के अनुरोध के साथ पास करेंगे — जैसे कि सैन फ्रांसिस्को में समय पूछना। ध्यान देने योग्य बात है कि **टूल कॉल** वापस होता है, प्रश्न का अंतिम उत्तर **नहीं**। जैसा कि पहले कहा गया, LLM कार्य के लिए चुना हुआ फ़ंक्शन का नाम और इसे पास किए जाने वाले तर्क लौटाता है।

    ```python
    # मॉडल के पढ़ने के लिए फंक्शन विवरण
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
  
    # प्रारंभिक उपयोगकर्ता संदेश
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # पहला API कॉल: मॉडल से फ़ंक्शन का उपयोग करने को कहें
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # मॉडल की प्रतिक्रिया को संसाधित करें
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```
  
    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **कार्यान्वयन के लिए आवश्यक फ़ंक्शन कोड:**

    अब जब LLM ने चुना है कि कौन से फ़ंक्शन को चलाना है, उस कार्य को करने वाला कोड लागू और निष्पादित किया जाना चाहिए।
    हम पाइथन में वर्तमान समय प्राप्त करने का कोड लिख सकते हैं। साथ ही, अंतिम परिणाम प्राप्त करने के लिए response_message से नाम और तर्क निकालने का कोड भी लिखना होगा।

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
     # फ़ंक्शन कॉल्स को संभालें
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
  
      # दूसरा API कॉल: मॉडल से अंतिम प्रतिक्रिया प्राप्त करें
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
  
फ़ंक्शन कॉलिंग अधिकांश, यदि सभी नहीं, एजेंट टूल उपयोग डिज़ाइन का मूल है, हालांकि इसे स्क्रैच से लागू करना कभी-कभी चुनौतीपूर्ण हो सकता है। जैसा कि हमने [Lesson 2](../../../02-explore-agentic-frameworks) में सीखा, एजेंटिक फ्रेमवर्क हमें टूल उपयोग लागू करने के लिए पूर्व-निर्मित निर्माण खंड प्रदान करते हैं।

## एजेंटिक फ्रेमवर्क्स के साथ टूल उपयोग के उदाहरण

यहाँ कुछ उदाहरण दिए गए हैं कि आप विभिन्न एजेंटिक फ्रेमवर्क्स का उपयोग करते हुए टूल उपयोग डिज़ाइन पैटर्न को कैसे लागू कर सकते हैं:

### सेमांटिक कर्नेल

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">सेमांटिक कर्नेल</a> एक ओपन-सोर्स AI फ्रेमवर्क है जो .NET, पाइथन, और जावा डेवलपर्स के लिए LLMs के साथ काम करना आसान बनाता है। यह फ़ंक्शन कॉलिंग प्रक्रिया को सरल बनाता है क्योंकि यह आपकी फ़ंक्शंस और पैरामीटरों का वर्णन मॉडल को अपने आप करता है, जिसे <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">सीरियलाइजिंग</a> कहा जाता है। यह मॉडल और आपके कोड के बीच दो-तरफ़ा संचार भी संभालता है। सेमांटिक कर्नेल जैसे एजेंटिक फ्रेमवर्क का एक अन्य लाभ यह है कि यह पूर्व-निर्मित टूल्स जैसे <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">फ़ाइल सर्च</a> और <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">कोड इंटरप्रेटर</a> तक पहुँच प्रदान करता है।

निम्न आरेख सेमांटिक कर्नेल के साथ फ़ंक्शन कॉलिंग प्रक्रिया को दर्शाता है:

![function calling](../../../translated_images/hi/functioncalling-diagram.a84006fc287f6014.webp)

सेमांटिक कर्नेल में फ़ंक्शंस/टूल्स को <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">प्लगइन्स</a> कहा जाता है। हम पहले देखे गए `get_current_time` फ़ंक्शन को एक क्लास में बदलकर प्लगइन बना सकते हैं जिसमें वह फ़ंक्शन होगा। हम `kernel_function` डेकोरेटर को भी इम्पोर्ट कर सकते हैं, जो फ़ंक्शन का विवरण लेता है। जब आप GetCurrentTimePlugin के साथ कर्नेल बनाते हैं, तो कर्नेल स्वतः फ़ंक्शन और उसके पैरामीटरों को सीरियलाइज करेगा, जिससे LLM को भेजने के लिए स्कीमा बनाया जाएगा।

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

# कर्नेल बनाएं
kernel = Kernel()

# प्लगइन बनाएं
get_current_time_plugin = GetCurrentTimePlugin(location)

# प्लगइन को कर्नेल में जोड़ें
kernel.add_plugin(get_current_time_plugin)
```
  

### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> एक नया एजेंटिक फ्रेमवर्क है जिसे डेवलपर्स को सुरक्षित रूप से उच्च गुणवत्ता वाले और विस्तार योग्य AI एजेंट बनाने, तैनात करने, और स्केल करने के लिए बनाया गया है, जिसमें आधारभूत कंप्यूट और स्टोरेज संसाधनों का प्रबंधन आवश्यक नहीं है। यह विशेष रूप से एंटरप्राइज अनुप्रयोगों के लिए उपयोगी है क्योंकि यह एक पूर्ण-प्रबंधित सेवा है जिसमें एंटरप्राइज-ग्रेड सुरक्षा होती है।

जब सीधे LLM API के साथ विकास से तुलना की जाती है, तो Azure AI Agent Service के कुछ फायदे हैं, जिनमें शामिल हैं:

- स्वत: टूल कॉलिंग – टूल कॉल पार्स करने, टूल को चालू करने, और प्रतिक्रिया संभालने की कोई आवश्यकता नहीं; ये सब अब सर्वर-साइड होता है
- सुरक्षित डेटा प्रबंधन – अपनी बातचीत की स्थिति प्रबंधित करने के बजाय, आप थ्रेड्स पर भरोसा कर सकते हैं जो पूरी आवश्यक जानकारी संग्रहित करते हैं
- इंस्टेंट टूल्स – ऐसे टूल्स जिनसे आप अपने डेटा स्रोतों से इंटरैक्ट कर सकते हैं, जैसे Bing, Azure AI Search, और Azure Functions।

Azure AI Agent Service में उपलब्ध टूल्स को दो श्रेणियों में बांटा जा सकता है:

1. ज्ञान टूल्स:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing Search के साथ ग्राउंडिंग</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">फ़ाइल खोज</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. क्रिया टूल्स:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">फ़ंक्शन कॉलिंग</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">कोड इंटरप्रेटर</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI परिभाषित टूल्स</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure फ़ंक्शंस</a>

एजेंट सेवा हमें इन टूल्स को `toolset` के रूप में एक साथ उपयोग करने की अनुमति देती है। यह `threads` का उपयोग भी करता है जो एक विशिष्ट बातचीत के संदेशों का इतिहास रखता है।

कल्पना करें कि आप कंटोसो नामक कंपनी में एक सेल्स एजेंट हैं। आप एक संवादात्मक एजेंट विकसित करना चाहते हैं जो आपकी सेल्स डेटा के बारे में सवालों का जवाब दे सके।

निम्न छवि दिखाती है कि आप Azure AI Agent Service का उपयोग करके अपनी सेल्स डेटा का विश्लेषण कैसे कर सकते हैं:

![Agentic Service In Action](../../../translated_images/hi/agent-service-in-action.34fb465c9a84659e.webp)

सेवा के साथ इन टूल्स का उपयोग करने के लिए हम एक क्लाइंट बना सकते हैं और एक टूल या टूलसेट परिभाषित कर सकते हैं। इसे व्यावहारिक रूप में लागू करने के लिए नीचे पाइथन कोड दिया गया है। LLM टूलसेट को देखकर यह निर्णय ले सकेगा कि उपयोगकर्ता द्वारा बनाया गया फ़ंक्शन `fetch_sales_data_using_sqlite_query` या पूर्व-निर्मित कोड इंटरप्रेटर का उपयोग करना है।

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query फ़ंक्शन जिसे fetch_sales_data_functions.py फ़ाइल में पाया जा सकता है।
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# टूलसेट प्रारंभ करें
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query फ़ंक्शन के साथ फ़ंक्शन कॉलिंग एजेंट को प्रारंभ करें और इसे टूलसेट में जोड़ें
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# कोड इंटरप्रेटर टूल प्रारंभ करें और इसे टूलसेट में जोड़ें।
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```
  
## विश्वसनीय AI एजेंट बनाने के लिए टूल उपयोग डिज़ाइन पैटर्न के विशेष विचार क्या हैं?

LLMs द्वारा गतिशील रूप से उत्पन्न SQL के साथ एक सामान्य चिंता सुरक्षा है, विशेष रूप से SQL इंजेक्शन या दुर्भावनापूर्ण क्रियाओं का जोखिम, जैसे डेटाबेस को ड्रॉप करना या छेड़छाड़ करना। जबकि ये चिंताएं वैध हैं, इन्हें उचित डेटाबेस एक्सेस अनुमतियों के कॉन्फ़िगरेशन द्वारा प्रभावी ढंग से कम किया जा सकता है। अधिकांश डेटाबेस के लिए इसका मतलब है डेटाबेस को केवल-पढ़ने योग्य (read-only) बनाना। PostgreSQL या Azure SQL जैसे डेटाबेस सेवाओं के लिए, ऐप को केवल-पढ़ने (SELECT) भूमिका सौंपनी चाहिए।

ऐप को सुरक्षित वातावरण में चलाने से सुरक्षा और बढ़ जाती है। एंटरप्राइज परिदृश्यों में, डेटा सामान्यतः संचालन प्रणालियों से निकाला और रूपांतरित होकर एक केवल-पढ़े जाने योग्य डेटाबेस या डेटा वेयरहाउस में रखा जाता है जिसमें उपयोगकर्ता के लिए अनुकूल स्कीमा होता है। यह दृष्टिकोण डेटा को सुरक्षित, प्रदर्शन और पहुँच के लिए अनुकूलित रखता है और ऐप को प्रतिबंधित केवल-पढ़ने (read-only) पहुंच प्रदान करता है।

## नमूना कोड्स
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## टूल उपयोग डिज़ाइन पैटर्न के बारे में और प्रश्न?

अन्य शिक्षार्थियों से मिलने, कार्यालयीन घंटे में शामिल होने और अपने AI एजेंट्स से संबंधित प्रश्नों के उत्तर प्राप्त करने के लिए [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) में शामिल हों।

## अतिरिक्त संसाधन

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## पिछला पाठ

[एजेंटिक डिज़ाइन पैटर्न समझना](../03-agentic-design-patterns/README.md)

## अगला पाठ

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**अस्वीकरण**:  
यह दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियां या अशुद्धियां हो सकती हैं। मूल दस्तावेज़ को उसकी मातृभाषा में प्रामाणिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए पेशेवर मानव अनुवाद की सिफारिश की जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->