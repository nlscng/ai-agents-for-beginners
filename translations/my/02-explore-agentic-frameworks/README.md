[![AI Agent Frameworks ကို ရှာဖွေခြင်း](../../../translated_images/my/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(ဤသင်ခန်းစာ၏ ဗီဒီယိုကို ကြည့်ရန် အပေါ်တွင်ရှိသော ပုံကို ကလစ်ပါ)_ 

# AI Agent Frameworks ကို ရှာဖွေပါ

AI agent frameworks သည် AI agent များကို ဖန်တီးခြင်း၊ ဖြန့်ချိခြင်းနှင့် စီမံခန့်ခွဲခြင်းကို လွယ်ကူစေရန်ဒီဇိုင်းထုတ်ထားသည့် ဆော့ဖ်ဝဲ ပလက်ဖောင်းများဖြစ်သည်။ ဤ frameworks များသည် ဖွံ့ဖြိုးသူများကို အကြိုတည်ဆောက်ထားသည့် အစိတ်အပိုင်းများ၊ abstraction များနှင့် ကိရိယာများကို ပံ့ပိုးပေးကာ ရှုပ်ထွေးသော AI စနစ်များ၏ ဖွံ့ဖြိုးမှုကို လျင်မြန်စေရန် အကူအညီပေးပါသည်။

ဤ frameworks များက ဖွံ့ဖြိုးသူများကို သူတို့၏ လျှင်မြန်သောအသုံးပြုမှုများအပေါ် တွေးသည့် အထူးကျသော အချက်များတွင် အာရုံစိုက်နိုင်စေပြီး AI agent ဖွံ့ဖြိုးရေးဆိုင်ရာ ပုံမှန် စိန်ခေါ်မှုများအတွက် စံနှုန်းပြု သဘောတရားများကို ပေးဆောင်သည်။ ၎င်းတို့မှာ စီးပွားရေးချဲ့ထွင်နိုင်မှု၊ အသုံးပြုရလွယ်ကူမှုနှင့် ထိရောက်မှု တိုးမြှင့်ပေးပါသည်။

## နိဒါန်း 

ဤသင်ခန်းစာတွင် ဖော်ပြမည့်အချက်များမှာ -

- AI Agent Frameworks များသည် ဘာလဲ၊ ဖွံ့ဖြိုးသူများအား ဘာတွေစေချင်ရတာလဲ?
- အသင်းများသည် ၎င်းတို့ကို အမြန် prototype ဆွဲခြင်း၊ iteration ပြုလုပ်ခြင်းနှင့် agent ၏ အရည်အချင်းများကို တိုးတက်စေရေးအတွက် မည်သို့ အသုံးချနိုင်သနည်း?
- Microsoft က ဖန်တီးထားသည့် <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, နှင့် <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> တို့ရဲ့ frameworks နှင့် ကိရိယာများ ကြား အထူးကွဲပြားချက်များမှာ ဘာတွေလဲ?
- ကျွန်ုပ့်တက်ရှိသော Azure ပတ်ဝန်းကျင်ကိရိယာများကို တိုက်ရိုက် ပေါင်းစည်းနိုင်မလား၊ ဒါမှမဟုတ် သီးခြားဖြေရှင်းချက်များ လိုအပ်သလား?
- Azure AI Agents service သည် ဘာလဲ၊ ၎င်းက ကျွန်ုပ်ကို မည်သို့ အကူအညီပေးနေသလဲ?

## သင်ယူရန် ရည်မှန်းချက်များ

ဤ သင်ခန်းစာ၏ ရည်ရွယ်ချက်များမှာ သင်ကို နားလည်စေလိုသည့်အရာများမှာ -

- AI ဖွံ့ဖြိုးရေးတွင် AI Agent Frameworks ၏ တာဝန်
- အလွန်စွမ်းဆောင်နိုင်သော agent များတည်ဆောက်ရန် AI Agent Frameworks ကို မည်သို့ အသုံးချရမည်နည်း
- AI Agent Frameworks များမှ ဖွံ့ဖြိုးစေနိုင်သည့် အဓိက စွမ်းရည်များ
- AutoGen, Semantic Kernel နှင့် Azure AI Agent Service တို့အကြား ကွဲပြားချက်များ

## AI Agent Frameworks များ ဆိုတာ ဘာလဲ၊ ဖွံ့ဖြိုးသူများအား ဘာတွေ ပြုလုပ်ခွင့်ပေးသနည်း?

ရိုးရှင်းသော AI Frameworks များက သင့်စက်ရုပ်များနှင့် အက်ပလီကေးရှင်းများထဲသို့ AI ကို ပေါင်းစည်းပေးကာ အောက်ပါအတိုင်း အက်ပလီကေးရှင်းများကို ပိုမိုကောင်းမွန်စေပါသည် -

- **Personalization**: AI သည် အသုံးပြုသူ၏ အပြုအမူနှင့် အကြိုက်များကို ခွဲခြမ်း စိစစ်၍ ကိုယ်ပိုင်အကြံပြုချက်များ၊ အကြောင်းအရာများနှင့် အတွေ့အကြုံများကို ပေးနိုင်သည်။
  Example: Netflix ကဲ့သို့သော streaming ဝန်ဆောင်မှုများသည် ကြည့်ရှုမှတ်တမ်းအပေါ်မူတည်၍ ရုပ်ရှင်နှင့် ချန်နယ်များကို အကြံပြုရန် AI ကို အသုံးပြုသည်၊ အထိုက်အလျှော် အသုံးပြုသူ စိတ်ဝင်စားမှုနှင့် စိတ်ကျေနပ်မှုကို မြှင့်တင်ပေးသည်။
- **Automation and Efficiency**: AI သည် ထပ်တကြိမ်လုပ်ရသော လုပ်ငန်းများကို အလိုအလျောက် လုပ်ဆောင်ပေးခြင်း၊ လုပ်ငန်းစဉ်များကို တစ်ဆင့်ချင်းစီ လျှော့ချပေးခြင်းနှင့် စီမံခန့်ခွဲမှုထိရောက်မှုကို မြှင့်တင်ပေးနိုင်သည်။
  Example: Customer service အက်ပလီကေးရှင်းများတွင် AI ဖြင့် လုပ်ဆောင်သည့် chatbot များကို အသုံးပြု၍ မေးခွန်းများကို ကိုင်တွယ်ပေးပြီး တုံ့ပြန်ချိန်ကို လျှော့ချကာ လူသား အကျိုးပြု ဝန်ထမ်းများကို ပိုမိုရှုပ်ထွေးသော ဥပဒေ ဆိုင်ရာအလုပ်များအတွက် ထိန်းသိမ်းပေးနိုင်သည်။
- **Enhanced User Experience**: AI သည် အသံအသိအမှတ်ပြုခြင်း၊ သဘာဝဘာသာစကား ကိုင်တွယ်ခြင်းနှင့် ခန့်မှန်းရောက်ရှိစကားများကဲ့သို့ သိပ္ပံနည်း features များဖြင့် အသုံးပြုသူ အတွေ့အကြုံကို တိုးတက်စေသည်။
  Example: Siri နှင့် Google Assistant ကဲ့သို့သော virtual assistant များသည် အသံညွှန်ကြားချက်များကို နားလည်ပြီး တုံ့ပြန်ရန် AI ကို အသုံးပြုကာ အသုံးပြုသူများအနေဖြင့် စက်ပစ္စည်းများနှင့် ပိုမိုလွယ်ကူစွာ ဆက်ဆံနိုင်စေသည်။

### အားလုံးကောင်းမြင်နေပေမယ့်၊ ဒါဆို ဘာကြောင့် AI Agent Framework လိုအပ်သလဲ?

AI Agent frameworks များသည် ရိုးရိုး AI frameworks ထက် ပိုမိုကျယ်ပြန့်သော အရာတစ်ခုကို ကိုယ်စားပြုသည်။ ၎င်းတို့ကို အသုံးပြုကာ အသုံးပြုသူများ၊ အခြား agent များနှင့် ပတ်ဝန်းကျင်နှင့် အပြန်အလှန် ဆက်ဆံနိုင်သည့် အထူးသိပ္ပံဗေဒရှိ agent များကို ဖန်တီးရန် ရည်ရွယ်ထားသည်။ ၎င်း agent များသည် ကိုယ်ပိုင် အလိုအလျောက်ပြုမူမှု ပြသနိုင်ပြီး ဆုံးဖြတ်ချက်များချနိုင်ကာ ပြောင်းလဲနေသည့် အခြေအနေများနှင့် ကိုက်ညီ၍ ကိုက်ညီအောင် စိတ်ကြိုက် ပြောင်းလဲနိုင်သည်။ AI Agent Frameworks မှာ ပေးထားသည့် အဓိက စွမ်းရည်များကို အောက်တွင် ကြည့်ကြမည် -

- **Agent Collaboration and Coordination**: အများ agent များကို ဖန်တီးနိုင်ပြီး ၎င်းတို့သည် မျှဝေ ဆက်သွယ် ရပ်တည်သည့်အနေဖြင့် အတူတကွ အလုပ်လုပ်ကာ ရှုပ်ထွေးသော တာဝန်များကို ဖြေရှင်းနိုင်စေသည်။
- **Task Automation and Management**: အဆင့်မြင့် အလုပ်စဉ်များကို အလိုအလျှောက် လုပ်ဆောင်ခြင်း၊ တာဝန် ခွဲဝေခြင်းနှင့် agent များအကြား 动态 task စီမံခန့်ခွဲမှု များကို ပံ့ပိုးပေးသည်။
- **Contextual Understanding and Adaptation**: agent များကို စဉ်ဆက်မပြတ် သတင်းအချက်အလက်များနှင့်အညီ အခြေအနေကို နားလည်နိုင်စေပြီး ပြောင်းလဲနေသည့် ပတ်ဝန်းကျင်အဖြစ်အပျက်များနှင့် ကိုက်ညီ၍ ဆုံးဖြတ်ချက်ချနိုင်စေသည်။

အကျဉ်းချုံးပြောရရင် agent များက သင့်အား ပိုမိုများစွာလုပ်ဆောင်နိုင်စေပြီး automation ကို နောက်တန်းသို့ တိုးတက်စေကာ ပတ်ဝန်းကျင်မှ သင်ခန်းစာယူပြီး လေ့လာသင်ယူနိုင်သည့် ပိုမို စမတ်သော စနစ်များ ဖန်တီးနိုင်စေသည်။

## agent ၏ အရည်အချင်းများကို အမြန် prototype ဖန်တီးခြင်း၊ iteration ပြုလုပ်ခြင်းနှင့် တိုးတက်စေရန် မည်သို့လုပ်မည်နည်း?

ဤကွင်းစိုက်ကွာသည့် ပတ်ဝန်းကျင်သည် အလျင်အမြန်ပြောင်းလဲနေသော်လည်း အများအားဖြင့် AI Agent Frameworks များတွင် ရိုးရိုးတူလည်း ရှိသော အချက်များ ရှိပြီး ၎င်းတို့က သင့်အား အမြန် prototype ဆွဲခြင်းနှင့် iteration ပြုလုပ်ရာတွင် အကူအညီဖြစ်စေသည်။ အထူးသဖြင့် မော်ဂျူး အစိတ်အပိုင်းများ၊ ပူးပေါင်းဆောင်ရွက်နိုင်သော ကိရိယာများနှင့် အချိန်ပြည့် သင်ယူခြင်းတို့ ဖြစ်ကြသည်။ အချက်တချို့ကို ဖော်ပြပါမည်။

- **Use Modular Components**: AI SDK များသည် AI နှင့် Memory connectors, function calling ကို သဘာဝဘာသာဖြင့် သို့မဟုတ် code plugins ဖြင့် အသုံးပြုနိုင်ခြင်း၊ prompt templates အစရှိသည့် အကြိုတည်ဆောက်ထားသော အစိတ်အပိုင်းများကို ပေးသည်။
- **Leverage Collaborative Tools**: သတ်မှတ်ထားသော အခန်းကဏ္ဍများနှင့် တာဝန်များရှိသော agent များကို ဒီဇိုင်းဆွဲ၍ ပူးပေါင်းလုပ်ဆောင်မှု workflow များကို စမ်းသပ် တိုးတက်စေရန် ဖန်တီးနိုင်သည်။
- **Learn in Real-Time**: အပြန်အလှန်တုံ့ပြန်မှု လုပ်ငန်းစဉ်များကို အကောင်အထည်ဖော်ကာ agent များသည် အပြန်လှန် ဆက်ဆံမှုများမှ သင်ယူပြီး မိမိတို့၏ သဘောထားကို အချိန်နဲ့အမျှ ဖြင့် ပြန်လည်ထိန်းသိမ်းနိုင်သည်။

### မော်ဂျူး အစိတ်အပိုင်းများကို အသုံးပြုပါ

Microsoft Semantic Kernel နဲ့ LangChain ကဲ့သို့ SDK များသည် AI connectors, prompt templates, memory management ကဲ့သို့ အကြိုတည်ဆောက်ထားသော အစိတ်အပိုင်းများကို ပေးသည်။

**အဖွဲ့များက ၎င်းတို့ကို မည်သို့ အသုံးချနိုင်သနည်း**: အဖွဲ့များသည် အစိတ်အပိုင်းများကို အမှန်အတိုင်း ချိန်ဆ ု၍ လက်တွေ့အသုံးပြုနိုင်သော prototype ကို အမြန်တည်ဆောက်နိုင်ပြီး တုံ့ပြန်မှုစမ်းသပ်ခြင်းနှင့် iteration များကို လျင်မြန်စွာ ပြုလုပ်နိုင်သည်။

**လက်တွေ့တွင် မည်သို့ အလုပ်လုပ်သနည်း**: အသုံးပြုသူထံမှ အချက်အလက်ကို ခွဲထုတ်ရန် pre-built parser တစ်ခုကို အသုံးပြုနိုင်သည်၊ ဒေတာသိမ်းဆည်းရန် memory module တစ်ခုကို သုံးနိုင်ပြီး အသုံးပြုသူနှင့် အပြန်အလှန် ဆက်သွယ်ရန် prompt generator တစ်ခုကို ထည့်သွင်းနိုင်သည်၊  ဤအားလုံးကို အစအနေမစတင်ဘဲ အသစ်ကျောက်ထုကောက်ရန် မလိုပဲ အသုံးပြုနိုင်သည်။

**Example code**. Let's look at examples of how you can use a pre-built AI Connector with Semantic Kernel Python and .Net that uses auto-function calling to have the model respond to user input:

``` python
# Semantic Kernel Python နမူနာ

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# စကားပြောမှု၏ အကြောင်းအရာကို သိမ်းဆည်းရန် ChatHistory object ကို သတ်မှတ်ပါ
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# ခရီးသွားစာရင်းသွင်းရန် function ပါရှိသော နမူနာ plugin တစ်ခုကို သတ်မှတ်ပါ
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Kernel ကို တည်ဆောက်ပါ
kernel = Kernel()

# နမူနာ plugin ကို Kernel object ထဲထည့်ပါ
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Azure OpenAI AI Connector ကို သတ်မှတ်ပါ
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# auto-function calling ဖြင့် မော်ဒယ်ကို စီမံရန် request settings ကို သတ်မှတ်ပါ
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # ဖော်ပြထားသော chat history နှင့် request settings ဖြင့် မော်ဒယ်ဆီ သတင်းအချက်အလက် မေးမြန်းပါ
    # Kernel မှ မော်ဒယ်က တောင်းဆိုရန် နမူနာကို ပါဝင်သည်
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # အ例 AI မော်ဒယ် တုံ့ပြန်ချက်: `သင့်ရဲ့ ၂၀၂၅ ခုနှစ် ဇန်နဝါရီ ၁ ရက်နေ့တွင် New York သို့ သွားမည့် လေယာဉ် ခရီးကို အောင်မြင်စွာစာရင်းသွင်းပြီးပါပြီ။ ခရီးသွားရာမှာ သာယာမှုရှိပါစေ! ✈️🗽`

    # မော်ဒယ်၏ တုံ့ပြန်ချက်ကို ကျွန်ုပ်တို့၏ စကားပြောမှတ်တမ်းအကြောင်းအရာထဲသို့ ထည့်ပါ
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```

What you can see from this example is how you can leverage a pre-built parser to extract key information from user input, such as the origin, destination, and date of a flight booking request. This modular approach allows you to focus on the high-level logic.

### ပူးပေါင်းဆောင်ရွက်နိုင်သော ကိရိယာများကို အသုံးချပါ

CrewAI, Microsoft AutoGen, နှင့် Semantic Kernel ကဲ့သို့ frameworks များသည် အများ agent များကို ပူးပေါင်းလုပ်ဆောင်နိုင်ရန် အကူအညီပေးသည်။

**အဖွဲ့များက ၎င်းတို့ကို မည်သို့ အသုံးချနိုင်သနည်း**: အဖွဲ့များသည် သတ်မှတ်ထားသည့် အခန်းကဏ္ဍများနှင့် တာဝန်များရှိသော agent များကို ဒီဇိုင်းဆွဲနိုင်ပြီး ပူးပေါင်းလုပ်ဆောင်မှု workflow များကို စမ်းသပ်၊ ပြုပြင်၍ စနစ်၏ ထိရောက်မှုကို တိုးတက်စေနိုင်သည်။

**လက်တွေ့တွင် မည်သို့ အလုပ်လုပ်သနည်း**: သင်သည် တစ်ဦးချင်းစီမှာ data retrieval, analysis, သို့မဟုတ် decision-making ကဲ့သို့ အထူးပြု လုပ်ငန်းခွာများရှိသည့် agent များဖြင့် အဖွဲ့တစ်ဖွဲ့ကို ဖန်တီးနိုင်သည်။ ဤ agent များသည် ဆက်သွယ်များပြောဆိုကာ သတင်းအချက်အလက်မျှဝေ၍ အသင်းရည်မှန်းချက်တစ်ခုကို တက်နိုင်သည်၊ ဥပမာ အသုံးပြုသူမေးခွန်းကို ဖြေဆိုခြင်း သို့မဟုတ် တာဝန်တစ်ခုကို ပြီးမြောက်စေရန်။

**Example code (AutoGen)**:

```python
# အေးဂျင့်များကို ဖန်တီးပြီးနောက်၊ ၎င်းတို့အတူတကွ ကုသနိုင်ရန် round robin ကိရိယာ စီမံကိန်းကို ဖန်တီးပါ၊ ဒီအမှုတွင် နောက်တန်းလိုက်ဖြစ်ပါသည်။

# ဒေတာရယူမှုအေးဂျင့်
# ဒေတာခွဲခြမ်းစိတ်ဖြာမှုအေးဂျင့်
# ဆုံးဖြတ်ချက်ဖြစ်စဉ်အေးဂျင့်

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# အသုံးပြုသူက "APPROVE" ဟုဆိုသည်အထိ စကားပြောဆက်သွယ်မှု ပြီးဆုံးသည်။
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# script ထဲတွင် အသုံးပြုသောအခါ asyncio.run(...) ကို သုံးပါ။
await Console(stream)
```

What you see in the previous code is how you can create a task that involves multiple agents working together to analyze data. Each agent performs a specific function, and the task is executed by coordinating the agents to achieve the desired outcome. By creating dedicated agents with specialized roles, you can improve task efficiency and performance.

### အချိန်ကို အတူတကြီး သင်ယူပါ (Learn in Real-Time)

အဆင့်မြင့် frameworks များသည် အချိန်ပြည့် context နားလည်ခြင်းနှင့် ကိုက်ညီမှုများအတွက် စွမ်းရည်များကို ပေးသည်။

**အဖွဲ့များက ၎င်းတို့ကို မည်သို့ အသုံးချနိုင်သနည်း**: အဖွဲ့များသည် agent များအနေဖြင့် အပြန်အလှန်ကြားနာမှုပုံစံများကို အကောင်အထည်ဖော်ကာ ၎င်းတို့မှ သင်ယူပြီး ကိုယ်ပိုင် အပြုအမူများကို ဒိုင်နမစ်အတိုင်း ပြန်လည်ချိန်ညှိနိုင်စေရသည်၊ ၎င်းသည် စွမ်းရည်များကို ဆက်တိုက် တိုးတက်စေသည်။

**လက်တွေ့တွင် မည်သို့ အလုပ်လုပ်သနည်း**: agent များသည် အသုံးပြုသူတုံ့ပြန်မှုများ၊ ပတ်ဝန်းကျင်ဒေတာများနှင့် တာဝန်ရလဒ်များကို ခွဲခြမ်းသုံးသပ်ကာ ၎င်းတို့၏ သိပ္ပံအခြေခံများကို အပ်ဒိတ်လုပ်နိုင်သည်၊ ဆုံးဖြတ်ချက် algorithm များကို ပြောင်းလဲနိုင်သည်၊ နှင့် တစ်ချိန်ချိန်တွင် ဆောင်ရွက်မှုတိုးတက်စေရန် ဗဟုသုတအချက်အလက်များကို သိမ်းဆည်းနိုင်သည်။ ဤအဆင့်လိုက် သင်ယူမှုလုပ်ငန်းစဉ်သည် agent များအား ပြောင်းလဲနေသည့် အခြေအနေများနှင့် အသုံးပြုသူနှစ်သက်မှုများနှင့် ကိုက်ညီစေကာ စနစ်၏ ထိရောက်မှုကို မြှင့်တင်ပေးသည်။

## AutoGen, Semantic Kernel နှင့် Azure AI Agent Service တို့အကြား ကွဲပြားချက်များမှာ ဘာတွေလဲ?

ဤ frameworks များကို ယှဉ်ပြိုင်စိစစ်နိုင်သည့် နည်းလမ်းများစွာ ရှိသော်လည်း ၎င်းတို့၏ ဒီဇိုင်း၊ စွမ်းဆောင်ရည်များနှင့် ရည်မှန်းမှု ဖြစ်နိုင်ခြေများအရ အရေးပါတဲ့ ကွဲပြားချက်များကို အောက်တွင် ကြည့်ကြမည်။

## AutoGen

AutoGen သည် Microsoft Research ၏ AI Frontiers Lab မှ ဖွံ့ဖြိုးထားသည့် open-source framework ဖြစ်သည်။ ၎င်းသည် အဖြစ်အပျက် များမှ အသွင်ပြောင်းနိုင်သည့်၊ ဖြန့်ဝေထားသည့် *agentic* application များအား အဓိကထားပြီး LLMs နှင့် SLMs များ၊ ကိရိယာများနှင့် အဆင့်မြင့် multi-agent ဒီဇိုင်းပုံစံများကို ထောက်ပံ့ပေးသည်။

AutoGen သည် agent များ၏ အခြေခံစိတ်ကူးအပေါ် တည်ဆောက်ထားသည်။ agent သည် ၎င်း၏ ပတ်ဝန်းကျင်ကို မြင်မြင်သာသာ ခံယူနိုင်ပြီး ဆုံးဖြတ်ချက်ချနိုင်ကာ သတ်မှတ်ထားသည့် ရည်မှန်းချက်များကို မီတ္တူ ဆောင်ရွက်ရန် လုပ်ဆောင်နိုင်သော ကိုယ်ပိုင် အစိတ်အပိုင်းဖြစ်သည်။ agent များသည် asynchronous မက်ဆေ့ခ်ျများမှတစ်ဆင့် ဆက်သွယ်နိုင်ပြီး တစ်ချိန်တည်းတွင် လွတ်လပ်စွာနှင့် 병렬 စွာ အလုပ်လုပ်နိုင်သည်၊ ၎င်းသည် စနစ်၏ စီးပွားချဲ့ထွင်နိုင်မှုနှင့် တုံ့ပြန်နိုင်စွမ်းကို မြှင့်တင်ပေးသည်။

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agents သည် actor မော်ဒယ်ပေါ် အခြေခံသည်</a>။ Wikipedia အရ actor သည် _concurrent computation ၏ အခြေခံ တည်ဆောက်ပစ္စည်း ဖြစ်သည်။ ၎င်းက မက်ဆေ့ခ်ျတစ်ခုကို လက်ခံလာသောအခါ local ဆုံးဖြတ်ချက်များ ချနိုင်ပြီး၊ ပိုမိုသော actor များကို ဖန်တီးနိုင်ပြီး၊ ပိုမိုသော မက်ဆေ့ခ်ျများ ပို့လိုက်နိုင်ပြီး၊ လက်ခံမည့် နောက်တစ်ခု၏ မက်ဆေ့ခ်ျကို ဘယ်လို တုံ့ပြန်မည်ကို သတ်မှတ်နိုင်သည်_။

**Use Cases**: ကုဒ်ထုတ်လုပ်ခြင်းကို အလိုအလျှောက်လုပ်ဆောင်ခြင်း၊ ဒေတာ 分析 အလုပ်များနှင့် စီမံချက်များနှင့် သုတေသနလုပ်ငန်းများအတွက် custom agent များ ဖန်တီးခြင်းတို့ကို အထူးသင့်တော်သည်။

AutoGen ၏ အရေးပါတဲ့ အခြေခံ အယူအဆ အချို့မှာ -

- **Agents**. Agent သည် ဆော့ဖ်ဝဲ အရာဝတ္ထုတစ်ခုဖြစ်ပြီး -
  - **မက်ဆေ့ချျများမှတဆင့် ဆက်သွယ်တယ်**၊ ၎င်းမက်ဆေ့ခ်ျများသည် synchronous သို့မဟုတ် asynchronous ဖြစ်နိုင်သည်။
  - **၎င်း၏ ကိုယ်ပိုင် အခြေအနေကို ထိန်းသိမ်းတယ်**၊ ၎င်းကို လက်ရှိ လက်ခံလာသော မက်ဆေ့ချျများက ပြင်လဲနိုင်သည်။
  - **ရရှိလာသည့် မက်ဆေ့ချျများ သို့မဟုတ် အခြေအနေပြောင်းလဲမှုများကို တုံ့ပြန်ကာ လုပ်ဆောင်ချက်များ ဆောင်ရွက်တယ်**။ ဤ လုပ်ဆောင်ချက်များသည် agent ၏ အခြေအနေကို ပြောင်းလဲနိုင်ပြီး မက်ဆေ့ခ်ျ မှတ်တမ်းများကို အပ်ဒိတ်လုပ်ခြင်း၊ မက်ဆေ့ခ်ျအသစ်များ ပို့ခြင်း၊ ကုဒ်ကို အကောင်အထည်ဖော်ခြင်း သို့မဟုတ် API ခေါ်ဆိုချက်များ ပြုလုပ်ခြင်းကဲ့သို့ အပြင်ပေါက် ထိပ်ထားမြင်သာသည့် အကျိုးသက်ရောက်မှုများကို ဖြစ်နိုင်စေသည်။
    
  Here you have a short code snippet in which you create your own agent with Chat capabilities:

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
    
    In the previous code, `MyAgent` has been created and inherits from `RoutedAgent`. It has a message handler that prints the content of the message and then sends a response using the `AssistantAgent` delegate. Especially note how we assign to `self._delegate` an instance of `AssistantAgent` which is a pre-built agent that can handle chat completions.


    Let's let AutoGen know about this agent type and kick off the program next:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # အနောက်ခံမှာ စာတိုပို့ချက်များကို စတင်ဖြတ်သန်းနေသည်။
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    In the previous code the agents are registered with the runtime and then a message is sent to the agent resulting in the following output:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multi agents**. AutoGen သည် အများ agent များကို ဖန်တီးနိုင်ရန် ထောက်ပံ့ပေးသည်။ ၎င်းတို့သည် မက်ဆေ့ခ်ျများ ဆက်သွယ်ကာ သတင်းအချက်အလက်မျှဝေ၍ ၎င်းတို့၏ လှုပ်ရှားမှုများကို ကိုအော်တိုရှင်း ပြုလုပ်ကာ ရှုပ်ထွေးသော တာဝန်များကို ထိရောက်စွာ ဖြေရှင်းနိုင်စေသည်။ multi-agent system တစ်ခု ဖန်တီးရန်အတွက် သင်သည် data retrieval, analysis, decision-making နှင့် user interaction ကဲ့သို့ အရာဝတ္ထုအမျိုးအစားကွဲပြားသော agent များကို သတ်မှတ်နိုင်သည်။ ၎င်းနှင့် ဆင်တူ ဖန်တီးမှု တစ်ခုကို ကြည့်ပါ -

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Agent ကို ကြေညာသည့် နမူနာ
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # agent type အနေနဲ့ topic type ကို အသုံးပြုခြင်း။
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # ကျဉ်းမြောင်းအောင် ကျန်ရှိသော ကြေညာချက်များ

    # အုပ်စုစကားပြောခြင်း
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```

    In the previous code we have a `GroupChatManager` that is registered with the runtime. This manager is responsible for coordinating the interactions between different types of agents, such as writers, illustrators, editors, and users.

- **Agent Runtime**. Framework သည် runtime ပတ်ဝန်းကျင်တစ်ခုကို ပေးကာ agent များအကြား ဆက်သွယ်မှုကို ဆောင်ရွက်စေ၊ ၎င်းတို့၏ အထောက်အပံ့များနှင့် အသက်တာကာလများကို စီမံခန့်ခွဲပေးပြီး လုံခြုံရေးနှင့် ကိုယ်ရေးကိုယ်တာ အကန့်အသတ်များကို အကောင်အထည်ဖော်ပေးသည်။ ၎င်းက သင့် agent များကို လုံခြုံစိတ်ချစွာနှင့် ထိန်းချုပ်ထားသည့် ပတ်ဝန်းကျင်တစ်ခုတွင် လည်ပတ်နိုင်စေသည်။ စိတ်ဝင်စားစရာ runtime နှစ်မျိုး ရှိသည်။
  - **Stand-alone runtime**.  ဤသည်မှာ အားလုံးသော agents များကို တစ်ပရိုဆက်စ်တည်းတွင် တည်ဆောက်ထားသော ပရိုဂရမ်များအတွက် ကောင်းမွန်သည့် ရွေးချယ်မှုဖြစ်သည်။ ၎င်းသည် မည်သို့ လည်ပတ်သည်ကို အောက်တွင် ဥပမာ ဆွဲထားသည်။
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Stand-alone runtime</a>   
Application stack

    *agents communicate via messages through the runtime, and the runtime manages the lifecycle of agents*

  - **Distributed agent runtime**, is suitable for multi-process applications where agents may be implemented in different programming languages and running on different machines. Here's an illustration of how it works:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distributed runtime</a>

## Semantic Kernel + Agent Framework

Semantic Kernel သည် enterprise-ready AI Orchestration SDK တစ်ခုဖြစ်သည်။ ၎င်းတွင် AI နှင့် memory connectors များနှင့် အတူ Agent Framework တစ်ခုပါဝင်သည်။

Let's first cover some core components:

- **AI Connectors**: ၎င်းသည် Python နှင့် C# နှစ်မျိုးလုံးတွင် အသုံးပြုနိုင်သော အပြင်ဘက် AI ဝန်ဆောင်မှုများနှင့် ဒေတာ အရင်းအမြစ်များနှင့် ဆက်သွယ်ရန် အင်တာဖေ့စ်ဖြစ်သည်။

  ```python
  # Semantic Kernel Python
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  

    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```

    Here you have a simple example of how you can create a kernel and add a chat completion service. Semantic Kernel creates a connection to an external AI service, in this case, Azure OpenAI Chat Completion.

- **Plugins**: ၎င်းတို့သည် အက်ပလီကေးရှင်းတစ်ခုက အသုံးချနိုင်သည့် function များကို ထုပ်ပိုးထားသည်။ အသင့်အသုံးပြုနိုင်သော plugins များနှင့် သင်ပြုလုပ်နိုင်သော custom plugins များ ရှိသည်။ ဆက်စပ်သဘောတရားတစ်ခုမှာ "prompt functions" လည်း ဖြစ်သည်။ function ကိုဖိတ်ခေါ်ရန် သဘာဝဘာသာသက်ဝင်ချက်များ ပေးရန်အစား တချို့သော function များကို မော်ဒယ်ထံ ထုတ်ဖော်ပေးသည်။ လက်ရှိ chat context အပေါ် မူတည်၍ မော်ဒယ်သည် ဤ function များထဲမှ တစ်ခုကို ခေါ်ယူ၍ တောင်းဆိုချက် သို့မဟုတ် မေးခွန်းတစ်ခုကို ပြီးမြောက်စေသဖြင့် မဆိုရွေးချယ်နိုင်သည်။ ဥပမာအား လိုကြည့်ပါ။

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```

    Here, you first have a template prompt `skPrompt` that leaves room for the user to input text, `$userInput`. Then you create the kernel function `SummarizeText` and then import it into the kernel with the plugin name `SemanticFunctions`. Note the name of the function that helps Semantic Kernel understand what the function does and when it should be called.

- **Native function**: Framework သည် တိုက်ရိုက် ခေါ်ယူဆောင်ရွက်နိုင်သည့် native function များကိုလည်း ပါဝင်သည်။ ဖိုင်မှ အကြောင်းအရာကို ရယူသည့် အမျိုးအစား function တစ်ခု၏ ဥပမာက如下ဖြစ်သည်။

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```

- **Memory**: AI အက်ပလီကေးရှင်းများအတွက် context စီမံမှုကို abstraction လုပ်၍ လွယ်ကူစေသည်။ Memory သည် LLM သည် သိထားသင့်သည့် အချက်အလက်တစ်ခုဖြစ်သည်ဟု တွေးထားရသည်။ ဤသတင်းအချက်အလက်ကို vector store တစ်ခုတွင် သိမ်းဆည်းနိုင်ပြီး ၎င်းသည် in-memory database သို့မဟုတ် vector database သို့ အလားတူ အရာတစ်ခုဖြစ်နိုင်သည်။ အောက်တွင် *facts* များကို memory ထဲသို့ ထည့်သည့် အလွယ်တကူဖြစ်သော အခြေအနေ တစ်ခု၏ ဥပမာကို ဖော်ပြထားသည်။

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```

    ဤအချက်အလက်များကို ယင်းနောက် memory collection `SummarizedAzureDocs` တွင် သိမ်းဆည်းထားပါသည်။ ဤသည် သာမာန်အားဖြင့် ရိုးရှင်းသည့် ဥပမာတစ်ခု ဖြစ်သော်လည်း၊ LLM အတွက် အသုံးပြုရန် memory ထဲတွင် အချက်အလက်များကို မည်သို့ သိမ်းဆည်းနိုင်သည်ကို ကြည့်ရှုနိုင်ပါသည်။

    
So that's the basics of the Semantic Kernel framework, what about the Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service သည် နောက်ပိုင်းတွင် ထပ်မံ ထည့်သွင်းထားသည့် ဝန်ဆောင်မှုဖြစ်ပြီး Microsoft Ignite 2024 မှ မိတ်ဆက်လျက်ရှိသည်။ ၎င်းသည် Llama 3၊ Mistral၊ Cohere ကဲ့သို့ open-source LLM များကို တိုက်ရိုက်ခေါ်ယူနိုင်သလို ပိုမိုတိုးတက်သည့် မော်ဒယ်များဖြင့် AI agents များကို ဖန်တီး၍ deployment ပြုလုပ်နိုင်သည်။

Azure AI Agent Service သည် လုပ်ငန်းအဆင့်တွင် လုံခြုံရေးစနစ်များနှင့် ဒေတာသိမ်းဆည်းခြင်းနည်းလမ်းများကို အားကောင်းစေရန် ပံ့ပိုးပေးထားပြီး ကုမ္ပဏီအတွက် အသုံးပြုနိုင်သည်။

AutoGen နှင့် Semantic Kernel ကဲ့သို့ multi-agent orchestration frameworks များနှင့် အလုပ်လုပ်နိုင်စွမ်းကို ရရှိထားပါသည်။

ဤဝန်ဆောင်မှုသည် လက်ရှိ Public Preview အဆင့်တွင် ရှိပြီး agents ဖန်တီးရန် Python နှင့် C# ကို ထောက်ပံ့ပါသည်။

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# နမူနာအတွက် နမူနာပလပ်ဂင် ကို သတ်မှတ်ပါ
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # ကိုယ်စားလှယ် သတ်မှတ်ချက်ကို ဖန်တီးပါ
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # သတ်မှတ်ထားသော client နှင့် ကိုယ်စားလှယ်သတ်မှတ်ချက်ကို အသုံးပြု၍ AzureAI ကိုယ်စားလှယ်ကို ဖန်တီးပါ
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # စကားပွောရန် စက်ပစ္စည်းတစ်ခု ဖန်တီးပါ
        # စကားပွော စက်ပစ္စည်း မပေးပါက၊
        # အသစ်တစ်ခု ဖန်တီးပြီး မူလ ဖြေကြားချက်နှင့် ပြန်ပေးပါလိမ့်မည်
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # သတ်မှတ်ထားသော စကားပွော စက်ပစ္စည်းအတွက် ကိုယ်စားလှယ်ကို သက်ဝင်စေပါ
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### Core concepts

Azure AI Agent Service သည် အောက်ပါ အဓိက အယူအဆများကို ပါဝင်ထားသည်။

- **Agent**. Azure AI Agent Service သည် Microsoft Foundry နှင့် ပေါင်းစည်းထားသည်။ AI Foundry အတွင်းတွင် AI Agent သည် "smart" microservice တစ်ခုအဖြစ် အလုပ်လုပ်ပြီး မေးခွန်းများကို ဖြေဆိုခြင်း (RAG), လုပ်ဆောင်ချက်များ ဆောင်ရွက်ခြင်း သို့မဟုတ် workflow များကို အလိုအလျောက် ပြီးစီးစေနိုင်သည်။ ၎င်းသည် generative AI မော်ဒယ်များ၏ စွမ်းအားကို real-world data source များသို့ အကူအညီရရှိစေရန် tools များနှင့် ပေါင်းစည်း၍ အကောင်အထည်ဖော်သည်။ အောက်တွင် agent ဥပမာတစ်ခုကို ပြထားသည်။

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    In this example, an agent is created with the model `gpt-4o-mini`, a name `my-agent`, and instructions `You are helpful agent`. The agent is equipped with tools and resources to perform code interpretation tasks.

- **Thread and messages**. Thread သည် အရေးကြီးသော အယူအဆတစ်ခု ဖြစ်သည်။ ၎င်းသည် agent တစ်ဦးနှင့် user တစ်ဦးအကြား မေးမြန်းပြောဆိုမှု သို့မဟုတ် အပြန်အလှန် ဆက်ဆံမှုကို ကိုယ်စားပြုသည်။ Threads များကို စကားဝိုင်း၏ တိုးတက်မှုကို ချိတ်ဆက်ပြီး context သတင်းအချက်အလက်များ သိမ်းဆည်းရန်နှင့် ဆက်ဆံမှု၏ အခြေနေကို စီမံခန့်ခွဲရန် အသုံးပြုနိုင်သည်။ အောက်တွင် thread ဥပမာတစ်ခုကို ဖော်ပြထားသည်။

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    ဉပမာကုဒ်အရ thread တစ်ခု ဖန်တီးပြီးနောက် သို့သော် message တစ်ခုကို ထို thread သို့ ပို့လိုက်သည်။ `create_and_process_run` ကို ခေါ်သောအခါ agent ကို ထို thread တွင် လုပ်ဆောင်ရန် တောင်းဆိုထားသည်။ နောက်ဆုံးတွင် messages များကို ရယူ၍ agent ၏ တုံ့ပြန်မှုကို မှတ်တမ်းတင်ကြည့်ရှုပါသည်။ တင်သွင်းထားသော messages များက user နှင့် agent အကြား စကားဝိုင်း၏ တိုးတက်မှုကို ပြသသည်။ messages များသည် အမျိုးအစားမျိုးစုံ (text, image, file) ဖြစ်နိုင်သည်ကိုလည်း သိထားရမည်၊ ဥပမာ agent ၏ လုပ်ဆောင်မှုက image တစ်ပုံ သို့မဟုတ် text တုံ့ပြန်မှုတစ်ခု ဖြစ်နိုင်သည်။ ဖန်တီးသူအနေဖြင့် ၎င်းအချက်အလက်များကို ယခုတုံ့ပြန်မှုကို ထပ်မံ ပိုမိုလုပ်ဆောင်ရန် သို့မဟုတ် user ထံ မိတ်ဆက်ပေးရန် အသုံးပြုနိုင်သည်။

- **Integrates with other AI frameworks**. Azure AI Agent service သည် AutoGen၊ Semantic Kernel ကဲ့သို့သော အခြား framework များနှင့် ဆက်သွယ်နိုင်ပြီး ၎င်းဖြင့် သင်၏ app ၏ တစ်စိတ်တစ်ပိုင်းကို အဆိုပါ frameworks များတွင် တည်ဆောက်ပြီး Agent service ကို orchestrator အဖြစ် အသုံးပြုနိုင်သလို သေချာစွာ အားလုံးကို Agent service တွင် တည်ဆောက်နိုင်ပါသည်။

**Use Cases**: Azure AI Agent Service ကို လုံခြုံမှု၊ တိုးချဲ့နိုင်မှုနှင့် လိုက်လျောညီထွေ ပြောင်းလဲနိုင်မှု လိုအပ်သည့် ကုမ္ပဏီအပလီကေးရှင်းများအတွက် ဒီဇိုင်းဆွဲထားသည်။

## What's the difference between these frameworks?
 
ဤ frameworks များအကြား အချို့ ပြန်ရာအလွှာများ ရှိသော်လည်း ၎င်းတို့၏ ဒီဇိုင်း၊ စွမ်းနိုင်ရည်နှင့် ရည်ရွယ်ချက်အရ အဓိက ကွာခြားချက်များ ရှိသည်။
 
- **AutoGen**: အဓိကအားဖြင့် multi-agent systems ပေါ်တွင် အဆင့်မြင့် သုတေသနပြုခြင်းများအတွက် ဗျူဟာစမ်းသပ်မှု framework တစ်ခု ဖြစ်သည်။ ရှုပ်သည့် multi-agent systems များကို စမ်းသပ်ရန်နှင့် prototype ဖန်တီးရန် အကောင်းဆုံးနေရာဖြစ်သည်။
- **Semantic Kernel**: ကုမ္ပဏီအဆင့်တွင် အသုံးပြုနိုင်သော agent library တစ်ခုဖြစ်ပြီး agentic အပလီကေးရှင်းများကို တည်ဆောက်ရန် အသင့်နေသည်။ event-driven၊ distributed agentic applications များအပေါ် ဂရုပြုကာ အမျိုးမျိုးသော LLMs နှင့် SLMs၊ tools များနှင့် single/multi-agent ဒီဇိုင်းပုံစံများကို ကူညီပေးနိုင်သည်။
- **Azure AI Agent Service**: Agents အတွက် Azure Foundry အတွင်းရှိ platform နှင့် deployment ဝန်ဆောင်မှုဖြစ်သည်။ Azure OpenAI, Azure AI Search, Bing Search နှင့် code execution ကဲ့သို့ Azure Foundry မှ ပံ့ပိုးသော ဝန်ဆောင်မှုများနှင့် ချိတ်ဆက်နိုင်မှုများကို ဆောင်ရွက်ပေးသည်။
 
တစ်ခုကို ရွေးချယ်ရန် သေချာ မသိသေးပါသလား?

### Use Cases
 
အောက်တွင် ပုံမှန်ဖြစ်သော အသုံးအဆောင်အခြေအနေများတချို့ကို ကြည့်ကြပါစို့။
 
> Q: I'm experimenting, learning and building proof-of-concept agent applications, and I want to be able to build and experiment quickly
>
>A: AutoGen would be a good choice for this scenario, as it focuses on event-driven, distributed agentic applications and supports advanced multi-agent design patterns.

> Q: What makes AutoGen a better choice than Semantic Kernel and Azure AI Agent Service for this use case?
>
> A: AutoGen is specifically designed for event-driven, distributed agentic applications, making it well-suited for automating code generation and data analysis tasks. It provides the necessary tools and capabilities to build complex multi-agent systems efficiently.

>Q: Sounds like Azure AI Agent Service could work here too, it has tools for code generation and more?

>
> A: Yes, Azure AI Agent Service is a platform service for agents and add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. It makes it easy to build your agents in the Foundry Portal and deploy them at scale.
 
> Q: I'm still confused just give me one option
>
> A: A great choice is to build your application in Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. This approach allows you to easily persist your agents while leveraging the power to build multi-agent systems in Semantic Kernel. Additionally, Semantic Kernel has a connector in AutoGen, making it easy to use both frameworks together.
 
Let's summarize the key differences in a table:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Event-driven, distributed agentic applications | Agents, Personas, Functions, Data | Code generation, data analysis tasks |
| Semantic Kernel | Understanding and generating human-like text content | Agents, Modular Components, Collaboration | Natural language understanding, content generation |
| Azure AI Agent Service | Flexible models, enterprise security, Code generation, Tool calling | Modularity, Collaboration, Process Orchestration | Secure, scalable, and flexible AI agent deployment |

What's the ideal use case for each of these frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

အဖြေမှာ ဟုတ်ကဲ့ ဖြစ်ပြီး သင်၏ ရှိပြီးသား Azure ecosystem tools များကို အထူးသဖြင့် Azure AI Agent Service နှင့် တိုက်ရိုက်ချိတ်ဆက်နိုင်သည်။ ၎င်းသည် အခြား Azure ဝန်ဆောင်မှုများနှင့် ချိတ်ဆက်အလုပ်လုပ်နိုင်ရန် ရည်ရွယ်၍ ဖန်တီးထားသည်။ ဥပမာအားဖြင့် Bing၊ Azure AI Search နှင့် Azure Functions များကို ပေါင်းစည်းနိုင်သည်။ Microsoft Foundry နှင့်လည်း နက်ရှိုင်းစွာ ပေါင်းစည်းထားသည်။

AutoGen နှင့် Semantic Kernel အတွက်လည်း Azure ဝန်ဆောင်မှုများနှင့် ပေါင်းစည်းနိုင်ပါသည်၊ သို့သော် သင်၏ကုဒ်မှတဆင့် Azure ဝန်ဆောင်မှုများကို ခေါ်ယူရန် လိုအပ်နိုင်သည်။ ပေါင်းစည်းရန် တခြားနည်းလမ်းတစ်ခုမှာ Azure SDKs ကို အသုံးပြုပြီး agents မှတဆင့် Azure ဝန်ဆောင်မှုများနှင့် ဆက်သွယ်ခြင်းဖြစ်သည်။ ထို့အပြင်၊ အဆိုပါ Agent service ကို AutoGen သို့မဟုတ် Semantic Kernel ထဲတွင် တည်ဆောက်ထားသော သင့် agents များအတွက် orchestrator အဖြစ် အသုံးပြု၍ Azure ecosystem ထံ လွယ်ကူစွာ ဝင်ရောက်နိုင်စေပါသည်။

## Sample Codes

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet with other learners, attend office hours and get your AI Agents questions answered.

## References

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel and AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## Previous Lesson

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
သတိပေးချက်:
ဤစာတမ်းကို AI ဘာသာပြန်ဝန်ဆောင်မှု [Co-op Translator](https://github.com/Azure/co-op-translator) ဖြင့် ဘာသာပြန်ထားပါသည်။ ကျွန်ုပ်တို့သည် တိကျမှုအတွက် ကြိုးပမ်းပါသော်လည်း အလိုအလျှောက် ဘာသာပြန်ချက်များတွင် အမှားများ သို့မဟုတ် တိကျမှုနည်းပါးမှုများ ဖြစ်တတ်ကြောင်း သတိပြုပါ။ မူရင်းစာတမ်းကို မူရင်းဘာသာဖြင့်သာ တရားဝင် အရင်းအမြစ်အဖြစ်ယူဆရမည်ဖြစ်သည်။ အရေးကြီးသော အချက်အလက်များအတွက် လူအင်အားဖြင့် အတည်ပြုထားသော ပရော်ဖက်ရှင်နယ် ဘာသာပြန်ကို အကြံပြုပါသည်။ ဤဘာသာပြန်ချက်အသုံးပြုမှုကြောင့် ဖြစ်ပေါ်နိုင်သည့် နားမလည်မှုများ သို့မဟုတ် အဓိပ္ပါယ်မှားဖတ်ခြင်းများအတွက် ကျွန်ုပ်တို့သည် တာဝန်မရှိပါ။
<!-- CO-OP TRANSLATOR DISCLAIMER END -->