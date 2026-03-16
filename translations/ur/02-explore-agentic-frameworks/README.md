[![ای آئی ایجنٹ فریم ورکس کی تلاش](../../../translated_images/ur/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(اس سبق کی ویڈیو دیکھنے کے لیے اوپر دی گئی تصویر پر کلک کریں)_

# ای آئی ایجنٹ فریم ورکس کی تلاش

ای آئی ایجنٹ فریم ورکس سافٹ ویئر پلیٹ فارمز ہیں جو ای آئی ایجنٹس کی تخلیق، تعیناتی، اور انتظام کو آسان بنانے کے لیے ڈیزائن کیے گئے ہیں۔ یہ فریم ورکس ڈویلپرز کو پہلے سے بنے ہوئے اجزاء، ابسٹریکشنز، اور ٹولز فراہم کرتے ہیں جو پیچیدہ AI سسٹمز کی ترقی کو آسان بناتے ہیں۔

یہ فریم ورکس ڈویلپرز کو ان کی ایپلیکیشنز کے منفرد پہلوؤں پر توجہ مرکوز کرنے میں مدد دیتے ہیں کیونکہ یہ AI ایجنٹ کی ترقی میں عام چیلنجز کے لیے معیاری طریقے فراہم کرتے ہیں۔ یہ AI سسٹمز کی تعمیر میں توسیع پذیری، رسائی، اور کارکردگی کو بڑھاتے ہیں۔

## تعارف

اس سبق میں شامل ہیں:

- AI ایجنٹ فریم ورکس کیا ہیں اور یہ ڈویلپرز کو کیا حاصل کرنے کی اجازت دیتے ہیں؟
- ٹیمیں ان کا استعمال کرکے اپنے ایجنٹ کی صلاحیتوں کا تیزی سے پروٹوٹائپ، دوبارہ دور اور بہتری کیسے کر سکتی ہیں؟
- Microsoft کے بنائے گئے فریم ورکس اور ٹولز میں کیا فرق ہے: <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>، <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>، اور <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>؟
- کیا میں اپنے موجودہ Azure ایکوسسٹم کے ٹولز کو براہ راست انضمام کر سکتا ہوں، یا مجھے علیحدہ حل درکار ہیں؟
- Azure AI ایجنٹس سروس کیا ہے اور یہ میری کس طرح مدد کر رہی ہے؟

## سیکھنے کے مقاصد

اس سبق کے مقاصد یہ ہیں کہ آپ کو سمجھایا جائے:

- AI ایجنٹ فریم ورکس کا AI ترقی میں کردار۔
- ذہین ایجنٹس بنانے کے لیے AI ایجنٹ فریم ورکس کا فائدہ اٹھانا۔
- AI ایجنٹ فریم ورکس کی اہم صلاحیتیں۔
- AutoGen، Semantic Kernel، اور Azure AI Agent Service کے درمیان فرق۔

## AI ایجنٹ فریم ورکس کیا ہیں اور یہ ڈویلپرز کو کیا کرنے کی اجازت دیتے ہیں؟

روایتی AI فریم ورکس آپ کی ایپلیکیشنز میں AI کو ضم کرنے اور انہیں بہتر بنانے کے درج ذیل طریقوں میں مدد کر سکتے ہیں:

- **ذاتی نوعیت**: AI صارف کے رویے اور ترجیحات کا تجزیہ کر سکتا ہے تاکہ ذاتی نوعیت کی سفارشات، مواد، اور تجربات فراہم کیے جا سکیں۔
مثال: نیٹ فلکس جیسی اسٹریمنگ سروسز AI کا استعمال کرتی ہیں تاکہ صارفین کی دیکھنے کی تاریخ کی بنیاد پر فلمیں اور شوز تجویز کریں، جس سے صارف کی شمولیت اور اطمینان میں اضافہ ہوتا ہے۔
- **خودکار اور کارکردگی**: AI بار بار آنے والے کاموں کو خودکار بنا سکتا ہے، ورک فلو کو آسان بنا سکتا ہے، اور آپریشنل کارکردگی کو بہتر بنا سکتا ہے۔
مثال: کسٹمر سروس ایپس AI سے چلنے والے چیٹ بوٹس کا استعمال کرتی ہیں تاکہ عام سوالات کو ہینڈل کیا جا سکے، جواب کے اوقات کو کم کیا جائے اور انسانی ایجنٹس کو پیچیدہ مسائل کے لیے آزاد کیا جائے۔
- **بہتر صارف تجربہ**: AI مجموعی صارف تجربہ کو بہتر بنا سکتا ہے جیسے آواز کی شناخت، قدرتی زبان کی پروسیسنگ، اور پیشن گوئی ٹیکسٹ جیسی ذہین خصوصیات فراہم کر کے۔
مثال: وائس اسسٹنٹس جیسے سری اور گوگل اسسٹنٹ AI کا استعمال کرتے ہیں تاکہ آواز کے حکم کو سمجھیں اور جواب دیں، صارفین کے لیے اپنے آلات کے ساتھ تعامل آسان بنائیں۔

### یہ سب اچھا لگتا ہے، تو پھر AI ایجنٹ فریم ورک کی ضرورت کیوں ہے؟

AI ایجنٹ فریم ورکس محض AI فریم ورکس سے زیادہ کچھ ہیں۔ یہ ذہین ایجنٹس کے تخلیق کی سہولت فراہم کرتے ہیں جو صارفین، دیگر ایجنٹس، اور ماحول کے ساتھ خاص مقاصد کے حصول کے لیے تعامل کر سکتے ہیں۔ یہ ایجنٹس خود مختار مزاج دکھا سکتے ہیں، فیصلے کر سکتے ہیں، اور بدلتے ہوئے حالات کے مطابق ڈھل سکتے ہیں۔ آئیے AI ایجنٹ فریم ورکس کی کچھ اہم صلاحیتوں کو دیکھتے ہیں:

- **ایجنٹ تعاون اور ہم آہنگی**: متعدد AI ایجنٹس کی تخلیق کی اجازت دیتی ہے جو مل کر کام کر سکتے ہیں، رابطہ کر سکتے ہیں، اور پیچیدہ کاموں کو حل کرنے کے لیے ہم آہنگی کر سکتے ہیں۔
- **ٹاسک خودکاری اور انتظام**: ملٹی اسٹیپ ورک فلو، کام کی تفویض، اور ایجنٹس کے درمیان متحرک ٹاسک مینجمنٹ کے لیے میکانزم فراہم کرتے ہیں۔
- **متنی سمجھ اور انطباق**: ایجنٹس کو سیاق و سباق سمجھنے، بدلتے ہوئے ماحول کے مطابق ڈھلنے، اور حقیقی وقت کی معلومات کی بنیاد پر فیصلے کرنے کے قابل بناتے ہیں۔

خلاصہ یہ کہ، ایجنٹس آپ کو زیادہ کرنے کی اجازت دیتے ہیں، خودکاری کو اگلے درجے تک لے جاتے ہیں، اور زیادہ ذہین سسٹمز تخلیق کرتے ہیں جو اپنے ماحول سے سیکھتے اور ڈھلتے ہیں۔

## ایجنٹ کی صلاحیتوں کو تیزی سے پروٹوٹائپ، دوبارہ دور، اور بہتر کیسے کریں؟

یہ ایک تیزی سے بدلنے والا منظر نامہ ہے، لیکن زیادہ تر AI ایجنٹ فریم ورکس میں کچھ چیزیں مشترک ہوتی ہیں جنہیں آپ تیزی سے پروٹوٹائپ اور دورانے کے لیے استعمال کر سکتے ہیں، جیسے ماڈیول اجزاء، مشترکہ ٹولز، اور حقیقی وقت کی تعلیم۔ آئیے ان پر بات کرتے ہیں:

- **ماڈیولر اجزاء استعمال کریں**: AI SDKs پہلے سے بنے ہوئے اجزاء جیسے AI اور میموری کنیکٹرز، قدرتی زبان یا کوڈ پلگ انز کے ذریعے فنکشن کالنگ، پرامپٹ سانچے، وغیرہ فراہم کرتے ہیں۔
- **مشترکہ ٹولز سے فائدہ اٹھائیں**: ایجنٹس کو مخصوص کردار اور کام دے کر مشترکہ ورک فلو کو ٹیسٹ اور بہتر بنائیں۔
- **حقیقی وقت میں سیکھیں**: فیڈبیک لوپس نافذ کریں جہاں ایجنٹس بات چیت سے سیکھیں اور اپنا طرز عمل متحرک طریقے سے ایڈجسٹ کریں۔

### ماڈیولر اجزاء استعمال کریں

Microsoft Semantic Kernel اور LangChain جیسے SDKs پہلے سے بنے ہوئے اجزاء جیسے AI کنیکٹرز، پرامپٹ سانچے، اور میموری مینجمنٹ فراہم کرتے ہیں۔

**ٹیمیں ان کا کیسے استعمال کر سکتی ہیں**: ٹیمیں جلدی سے ان اجزاء کو جمع کر کے ایک فعال پروٹوٹائپ بنا سکتی ہیں بغیر صفر سے شروع کیے، جو تجربے اور آئی ڈیاز کا تیزی سے جائزہ لینے کی اجازت دیتا ہے۔

**عملی طور پر یہ کیسے کام کرتا ہے**: آپ صارف کی ان پٹ سے معلومات نکالنے کے لیے پہلے سے بنے ہوئے پارسر کا استعمال کر سکتے ہیں، ڈیٹا ذخیرہ کرنے اور بازیافت کے لیے میموری ماڈیول استعمال کر سکتے ہیں، اور صارف کے ساتھ بات چیت کے لیے پرامپٹ جنریٹر استعمال کر سکتے ہیں، وہ بھی بغیر اجزاء خود بنانے کی ضرورت کے۔

**مثال کوڈ**۔ آئیے دیکھتے ہیں کہ کس طرح Semantic Kernel Python اور .Net کے ساتھ پہلے سے بنے ہوئے AI کنیکٹر کو استعمال کرکے ماڈل سے صارف کی ان پٹ کا جواب حاصل کیا جا سکتا ہے:

``` python
# سیمانٹک کرنل پائتھن کی مثال

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# گفتگو کے سیاق و سباق رکھنے کے لیے ChatHistory آبجیکٹ کی تعریف کریں
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# سفر کی بکنگ کرنے والا فنکشن رکھنے والا ایک نمونہ پلگ ان متعین کریں
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# کرنل بنائیں
kernel = Kernel()

# نمونہ پلگ ان کو کرنل آبجیکٹ میں شامل کریں
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Azure OpenAI AI کنیکٹر کی تعریف کریں
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# ماڈل کو خودکار فنکشن کالنگ کے ساتھ کنفیگر کرنے کے لیے درخواست کی ترتیبات کی تعریف کریں
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # دی گئی چیٹ ہسٹری اور درخواست کی ترتیبات کے لیے ماڈل کو درخواست بھیجیں
    # کرنل میں وہ نمونہ شامل ہے جسے ماڈل عملدرآمد کے لیے درخواست کرے گا
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
    # مثال کے طور پر AI ماڈل کا جواب: `آپ کی 1 جنوری 2025 کو نیو یارک کے لیے پرواز کامیابی سے بک کر دی گئی ہے۔ محفوظ سفر! ✈️🗽`

    # ماڈل کے جواب کو ہماری چیٹ ہسٹری کے سیاق و سباق میں شامل کریں
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
  
اس مثال سے آپ دیکھ سکتے ہیں کہ کس طرح آپ پہلے سے بنے ہوئے پارسر کو صارف کی ان پٹ سے اہم معلومات، جیسے پرواز کی بکنگ کی ابتدا، منزل، اور تاریخ نکالنے کے لیے استعمال کر سکتے ہیں۔ یہ ماڈیولر طریقہ آپ کو اعلی سطح کی منطق پر توجہ مرکوز کرنے دیتا ہے۔

### مشترکہ ٹولز سے فائدہ اٹھائیں

CrewAI، Microsoft AutoGen، اور Semantic Kernel جیسے فریم ورکس متعدد ایجنٹس کی تخلیق کو آسان بناتے ہیں جو مل کر کام کر سکتے ہیں۔

**ٹیمیں ان کا کیسے استعمال کر سکتی ہیں**: ٹیمیں مخصوص کردار اور کام کے ساتھ ایجنٹس ڈیزائن کر سکتی ہیں تاکہ وہ مشترکہ ورک فلو کا تجربہ کریں اور اسے بہتر بنائیں، اور مجموعی نظام کی کارکردگی بڑھائیں۔

**عملی طور پر یہ کیسے کام کرتا ہے**: آپ ایک ایجنٹس کی ٹیم بنا سکتے ہیں جہاں ہر ایجنٹ کا مخصوص فنکشن ہو، جیسے ڈیٹا بازیافت، تجزیہ، یا فیصلہ سازی۔ یہ ایجنٹس بات چیت اور معلومات کا تبادلہ کر کے مشترکہ مقصد حاصل کر سکتے ہیں، مثلاً صارف کے سوال کا جواب دینا یا کوئی کام مکمل کرنا۔

**مثال کوڈ (AutoGen)**:

```python
# ایجنٹس بنائیں، پھر ایک راؤنڈ رابن شیڈول بنائیں جہاں وہ مل کر کام کر سکیں، اس صورت میں ترتیب کے مطابق

# ڈیٹا بازیافت ایجنٹ
# ڈیٹا تجزیہ ایجنٹ
# فیصلہ سازی ایجنٹ

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

# گفتگو تب ختم ہوتی ہے جب صارف "APPROVE" کہے
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# اسکرپٹ چلانے کے لیے asyncio.run(...) استعمال کریں۔
await Console(stream)
```
  
پچھلے کوڈ میں آپ دیکھ سکتے ہیں کہ کس طرح ایک ایسا کام بنایا جا سکتا ہے جس میں متعدد ایجنٹس مل کر ڈیٹا کا تجزیہ کرتے ہیں۔ ہر ایجنٹ ایک مخصوص فنکشن انجام دیتا ہے، اور کام ایجنٹس کے ہم آہنگ ہونے سے انجام پاتا ہے تاکہ مطلوبہ نتیجہ حاصل ہو۔ مخصوص کردار کے ساتھ مخصوص ایجنٹس بنا کر آپ کام کی کارکردگی اور کارگردگی کو بہتر بنا سکتے ہیں۔

### حقیقی وقت میں سیکھیں

جدید فریم ورکس حقیقی وقت کے سیاق و سباق کی سمجھ بوجھ اور انطباق کی صلاحیتیں فراہم کرتے ہیں۔

**ٹیمیں ان کا کیسے استعمال کر سکتی ہیں**: ٹیمیں فیڈبیک لوپس نافذ کر سکتی ہیں جہاں ایجنٹس بات چیت سے سیکھتے ہیں اور اپنا رویہ متحرک طور پر ایڈجسٹ کرتے ہیں، جس سے صلاحیتوں کی مسلسل بہتری اور نشونما ہوتی ہے۔

**عملی طور پر یہ کیسے کام کرتا ہے**: ایجنٹس صارف کے تاثرات، ماحول کی معلومات، اور کام کے نتائج کا تجزیہ کر کے اپنا نالج بیس اپ ڈیٹ کرتے ہیں، فیصلہ سازی کے الگورتھمز کو ایڈجسٹ کرتے ہیں، اور وقت کے ساتھ کارکردگی کو بہتر بناتے ہیں۔ یہ تدریجی سیکھنے کا عمل ایجنٹس کو بدلتے ہوئے حالات اور صارف کی ترجیحات کے مطابق ڈھالنے میں مدد دیتا ہے، جس سے مجموعی نظام کی تاثیر بڑھتی ہے۔

## AutoGen، Semantic Kernel اور Azure AI Agent Service فریم ورکس میں کیا فرق ہے؟

ان فریم ورکس کا موازنہ کرنے کے بہت سے طریقے ہیں، لیکن آئیے ان کی ڈیزائن، صلاحیتوں، اور ہدف استعمال کے معاملات کے حوالے سے کچھ اہم فرق دیکھتے ہیں:

## AutoGen

AutoGen ایک اوپن سورس فریم ورک ہے جو Microsoft Research کے AI Frontiers Lab نے تیار کیا ہے۔ یہ ایونٹ ڈرائیون، تقسیم شدہ *agentic* ایپلیکیشنز پر توجہ مرکوز کرتا ہے، متعدد LLMs اور SLMs، ٹولز، اور جدید کثیر ایجنٹ ڈیزائن پیٹرنز کو ممکن بناتا ہے۔

AutoGen ایجنٹس کے بنیادی تصور کے گرد بنایا گیا ہے، جو خودمختار ہستی ہیں جو اپنے ماحول کو محسوس کر سکتی ہیں، فیصلے کر سکتی ہیں، اور مخصوص مقاصد کے حصول کے لیے عمل کر سکتی ہیں۔ ایجنٹس غیر ہم وقت ساز پیغامات کے ذریعے رابطہ کرتے ہیں، جس سے وہ آزادانہ اور متوازی کام کر سکتے ہیں، نظام کی توسیع پذیری اور جواب دہی کو بڑھاتے ہیں۔

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">ایجنٹس اداکار ماڈل (actor model) پر مبنی ہیں</a>۔ ویکیپیڈیا کے مطابق، ایک اداکار _ہم عصر کمپیوٹیشن کی بنیادی اکائی ہے۔ ایک پیغام کے جواب میں جو اسے موصول ہوتا ہے، ایک اداکار: مقامی فیصلے کر سکتا ہے، مزید اداکار بنا سکتا ہے، مزید پیغامات بھیج سکتا ہے، اور اگلے موصول ہونے والے پیغام کا جواب دینے کا طریقہ طے کر سکتا ہے_۔

**استعمال کی مثالیں**: کوڈ جنریشن کا خودکار عمل، ڈیٹا تجزیہ کے کام، اور منصوبہ بندی اور تحقیق کے افعال کے لیے کسٹم ایجنٹس کی تخلیق۔

یہاں AutoGen کے کچھ اہم بنیادی تصورات ہیں:

- **ایجنٹس**۔ ایک ایجنٹ ایک سافٹ ویئر ہستی ہے جو:
  - **پیغامات کے ذریعے رابطہ کرتا ہے**، یہ پیغامات ہم وقت ساز یا غیر ہم وقت ساز ہو سکتے ہیں۔
  - **اپنی ریاست کو برقرار رکھتا ہے**، جسے آنے والے پیغامات سے تبدیل کیا جا سکتا ہے۔
  - **موصولہ پیغامات یا اپنی حالت میں تبدیلیوں کے جواب میں عمل انجام دیتا ہے**۔ یہ عمل ایجنٹ کی حالت کو تبدیل کر سکتے ہیں اور بیرونی اثرات پیدا کر سکتے ہیں، جیسے پیغام لاگز کو اپ ڈیٹ کرنا، نئے پیغامات بھیجنا، کوڈ چلانا، یا API کالز کرنا۔
    
  یہاں ایک چھوٹا کوڈ سنپٹ ہے جس میں آپ چیٹ صلاحیتوں کے ساتھ اپنا ایجنٹ بناتے ہیں:

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
  
    پچھلے کوڈ میں، `MyAgent` بنایا گیا ہے اور `RoutedAgent` سے وراثت میں لیا گیا ہے۔ اس کا ایک پیغام ہینڈلر ہے جو پیغام کے مواد کو پرنٹ کرتا ہے اور پھر `AssistantAgent` ڈیلگیٹ کا استعمال کرتے ہوئے جواب بھیجتا ہے۔ خاص طور پر غور کریں کہ ہم `self._delegate` کو `AssistantAgent` کی ایک مثال تفویض کرتے ہیں جو ایک پہلے سے بنایا گیا ایجنٹ ہے جو چیٹ تکمیل کو ہینڈل کر سکتا ہے۔

    آئیے AutoGen کو اس ایجنٹ قسم کے بارے میں بتائیں اور پروگرام شروع کریں:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # پس منظر میں پیغامات کی پروسیسنگ شروع کریں۔
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```
  
    پچھلے کوڈ میں ایجنٹس کو رن ٹائم کے ساتھ رجسٹر کیا گیا ہے اور پھر ایجنٹ کو پیغام بھیجا جاتا ہے جس سے مندرجہ ذیل نتائج حاصل ہوتے ہیں:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```
  
- **کئی ایجنٹس**۔ AutoGen متعدد ایجنٹس کی تخلیق کی حمایت کرتا ہے جو مل کر پیچیدہ کام انجام دے سکتے ہیں۔ ایجنٹس بات چیت کر سکتے ہیں، معلومات کا اشتراک کر سکتے ہیں، اور مسائل کو زیادہ مؤثر طریقے سے حل کرنے کے لیے اپنے عمل کو ہم آہنگ کر سکتے ہیں۔ متعدد ایجنٹ سسٹم بنانے کے لیے، آپ مختلف قسم کے ایجنٹس کو مخصوص فنکشنز اور کرداروں کے ساتھ تعریف کر سکتے ہیں، جیسے ڈیٹا بازیافت، تجزیہ، فیصلہ سازی، اور صارف کے تعامل۔ آئیے دیکھتے ہیں کہ ایسی تخلیق کیسی دکھتی ہے تاکہ ہمیں اس کا اندازہ ہو:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # ایجنٹ کا اعلان کرنے کی مثال
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # topic ٹائپ کو ایجنٹ کی قسم کے طور پر استعمال کرنا
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # باقی اعلانات کو اختصار کے لیے مختصر کیا گیا

    # گروپ چیٹ
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
  
    پچھلے کوڈ میں ہمارے پاس ایک `GroupChatManager` ہے جو رن ٹائم کے ساتھ رجسٹرڈ ہے۔ یہ مینیجر مختلف اقسام کے ایجنٹس جیسے مصنفین، مصوروں، ایڈیٹرز، اور صارفین کے درمیان تعاملات کو مربوط کرنے کا ذمہ دار ہے۔

- **ایجنٹ رن ٹائم**۔ فریم ورک ایک رن ٹائم ماحول فراہم کرتا ہے، جو ایجنٹس کے درمیان رابطہ کو ممکن بناتا ہے، ان کی شناخت اور زندگی کے چکر کا انتظام کرتا ہے، اور سیکیورٹی اور پرائیویسی کی حدود کو نافذ کرتا ہے۔ اس کا مطلب ہے کہ آپ اپنے ایجنٹس کو محفوظ اور کنٹرول شدہ ماحول میں چلا سکتے ہیں، یقینی بناتے ہوئے کہ وہ محفوظ اور مؤثر طریقے سے تعامل کر سکیں۔ دو دلچسپ رن ٹائم ہوتے ہیں:
  - **اسٹینڈ الون رن ٹائم**۔ یہ واحد عمل ایپلیکیشنز کے لیے اچھا انتخاب ہے جہاں تمام ایجنٹس ایک ہی پروگرامنگ زبان میں بنے ہوں اور ایک ہی عمل میں چل رہے ہوں۔ یہاں اس کے کام کرنے کا خاکہ ہے:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">اسٹینڈ الون رن ٹائم</a>  
ایپلیکیشن اسٹیک

    *ایجنٹس پیغامات کے ذریعے رن ٹائم سے بات چیت کرتے ہیں، اور رن ٹائم ایجنٹس کی زندگی کے چکر کا انتظام کرتا ہے*

  - **تقسیم شدہ ایجنٹ رن ٹائم**، یہ ملٹی پراسیس ایپلیکیشنز کے لیے موزوں ہے جہاں ایجنٹس مختلف پروگرامنگ زبانوں میں بنے ہوں اور مختلف مشینوں پر چل رہے ہوں۔ یہاں اس کے کام کرنے کا خاکہ ہے:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">تقسیم شدہ رن ٹائم</a>

## Semantic Kernel + ایجنٹ فریم ورک

Semantic Kernel ایک انٹرپرائز تیار شدہ AI آرکیسٹریشن SDK ہے۔ اس میں AI اور میموری کنیکٹرز کے ساتھ ساتھ ایک ایجنٹ فریم ورک شامل ہے۔

آئیے پہلے کچھ بنیادی اجزاء دیکھیں:

- **AI کنیکٹرز**: یہ Python اور C# دونوں میں استعمال کے لیے بیرونی AI خدمات اور ڈیٹا ذرائع کے ساتھ انٹرفیس ہے۔

  ```python
  # معنوی کرنل پائتھون
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
  
    یہاں آپ کے پاس ایک سادہ مثال ہے کہ کس طرح آپ ایک کرنل بنا سکتے ہیں اور چیٹ تکمیل سروس شامل کر سکتے ہیں۔ Semantic Kernel ایک بیرونی AI سروس، اس صورت میں Azure OpenAI چیٹ تکمیل، سے کنکشن بناتا ہے۔

- **پلگنز**: یہ ان فنکشنز کو لپیٹتے ہیں جنہیں ایک ایپلیکیشن استعمال کر سکتی ہے۔ تیار شدہ پلگنز بھی ہیں اور آپ اپنی مرضی کے مطابق بھی بنا سکتے ہیں۔ ایک متعلقہ تصور "prompt functions" ہے۔ فنکشن کال کے لیے قدرتی زبان کی ہدایات فراہم کرنے کے بجائے، آپ ماڈل کو مخصوص فنکشنز نشتر کرتے ہیں۔ موجودہ چیٹ سیاق و سباق کی بنیاد پر، ماڈل ان میں سے ایک فنکشن کو کال کر سکتا ہے تاکہ درخواست یا سوال مکمل کرے۔ یہاں ایک مثال ہے:

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
  
    یہاں، آپ کے پاس پہلے ایک ٹیمپلیٹ پرامپٹ `skPrompt` ہے جو صارف کو متن داخل کرنے کی جگہ دیتا ہے، `$userInput`۔ پھر آپ کرنل فنکشن `SummarizeText` بناتے ہیں اور اسے `SemanticFunctions` کے نام سے کرنل میں پلگ ان کے طور پر درآمد کرتے ہیں۔ فنکشن کے نام پر توجہ دیں جو Semantic Kernel کو سمجھنے میں مدد دیتا ہے کہ فنکشن کیا کرتا ہے اور کب کال ہونا چاہیے۔

- **نیٹیو فنکشن**: فریم ورک ایسے نیٹیو فنکشنز بھی کال کر سکتا ہے جو کام انجام دینے کے لیے براہ راست چلائے جاتے ہیں۔ یہاں ایک مثال ہے جو فائل سے مواد بازیافت کرتا ہے:

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
  
- **میموری**: AI ایپس کے لیے سیاق و سباق کی مینجمنٹ کو آسان اور مجرد بناتا ہے۔ میموری کا مقصد یہ ہے کہ یہ چیز LLM کو معلوم ہونی چاہیے۔ آپ یہ معلومات ویکٹر اسٹور میں رکھ سکتے ہیں جو ایک ان میموری ڈیٹا بیس، ویکٹر ڈیٹا بیس یا اس کے مشابہ ہو سکتا ہے۔ یہاں ایک بہت سادہ فرضیہ ہے جہاں *حقائق* میموری میں شامل کیے جاتے ہیں:

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
  

یہ حقائق پھر میموری کلیکشن `SummarizedAzureDocs` میں محفوظ کیے جاتے ہیں۔ یہ ایک بہت سادہ مثال ہے، لیکن آپ دیکھ سکتے ہیں کہ کس طرح آپ LLM کے استعمال کے لیے معلومات کو میموری میں ذخیرہ کر سکتے ہیں۔

تو یہ Semantic Kernel فریم ورک کی بنیادی باتیں تھیں، Agent Framework کے بارے میں کیا خیال ہے؟

## Azure AI Agent Service

Azure AI Agent Service ایک حالیہ اضافہ ہے، جو Microsoft Ignite 2024 میں متعارف کروایا گیا۔ یہ زیادہ لچکدار ماڈلز کے ساتھ AI ایجنٹس کی ترقی اور تعیناتی کی اجازت دیتا ہے، جیسا کہ لاما 3، Mistral، اور Cohere جیسے اوپن سورس LLMs کو براہ راست کال کرنا۔

Azure AI Agent Service مضبوط انٹرپرائز سیکیورٹی میکانزم اور ڈیٹا اسٹوریج طریقے مہیا کرتا ہے، جو اسے انٹرپرائز ایپلیکیشنز کے لیے موزوں بناتے ہیں۔

یہ آٹو جین اور Semantic Kernel جیسے کثیر ایجنٹ آرکسٹریشن فریم ورکس کے ساتھ باکس سے باہر کام کرتا ہے۔

یہ سروس اس وقت پبلک پریویو میں ہے اور ایجنٹس بنانے کے لیے Python اور C# کی حمایت کرتی ہے۔

Semantic Kernel Python کا استعمال کرتے ہوئے، ہم ایک Azure AI Agent بنا سکتے ہیں جس میں صارف کی جانب سے ڈیفائن کردہ پلگ ان ہو:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# نمونے کے لیے ایک پلگ ان متعین کریں
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
        # ایجنٹ کی تعریف بنائیں
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # متعین کردہ کلائنٹ اور ایجنٹ کی تعریف استعمال کرتے ہوئے AzureAI ایجنٹ بنائیں
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # گفتگو کو رکھنے کے لیے ایک تھریڈ بنائیں
        # اگر کوئی تھریڈ فراہم نہ کی جائے تو ایک نیا تھریڈ
        # ابتدائی جواب کے ساتھ بنایا جائے گا اور واپس کیا جائے گا
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
                # مخصوص تھریڈ کے لیے ایجنٹ کو کال کریں
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

### بنیادی تصورات

Azure AI Agent Service کے درج ذیل بنیادی تصورات ہیں:

- **ایجنٹ**۔ Azure AI Agent Service Microsoft Foundry کے ساتھ انضمام کرتا ہے۔ AI Foundry کے اندر، ایک AI ایجنٹ "سمارٹ" مائیکرو سروس کے طور پر کام کرتا ہے جسے سوالات کے جواب دینے (RAG)، اعمال انجام دینے، یا مکمل طور پر ورک فلو کو خودکار بنانے کے لیے استعمال کیا جا سکتا ہے۔ یہ یہ تخلیقی AI ماڈلز کی طاقت کو ان آلات کے ساتھ ملا کر حاصل کرتا ہے جو اسے حقیقی دنیا کے ڈیٹا ذرائع تک رسائی اور ان کے ساتھ تعامل کی اجازت دیتے ہیں۔ یہاں ایک ایجنٹ کی مثال ہے:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    اس مثال میں، ایک ایجنٹ ماڈل `gpt-4o-mini`، نام `my-agent`، اور ہدایات `You are helpful agent` کے ساتھ بنایا گیا ہے۔ ایجنٹ کو کوڈ کی تشریح کے کام انجام دینے کے لیے آلات اور وسائل سے لیس کیا گیا ہے۔

- **تھریڈ اور پیغامات**۔ تھریڈ ایک اور اہم تصور ہے۔ یہ ایجنٹ اور صارف کے درمیان ایک گفتگو یا تعامل کی نمائندگی کرتا ہے۔ تھریڈز کو گفتگو کی پیش رفت کو ٹریک کرنے، سیاق و سباق کی معلومات ذخیرہ کرنے، اور تعامل کی حالت کو منظم کرنے کے لیے استعمال کیا جا سکتا ہے۔ یہاں ایک تھریڈ کی مثال ہے:

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

    پچھلے کوڈ میں، ایک تھریڈ بنایا گیا۔ اس کے بعد، تھریڈ کو پیغام بھیجا گیا۔ `create_and_process_run` کو کال کر کے، ایجنٹ کو تھریڈ پر کام کرنے کے لیے کہا جاتا ہے۔ آخر میں، پیغامات حاصل کیے جاتے ہیں اور ایجنٹ کی پاسخ دیکھنے کے لیے لاگ کیے جاتے ہیں۔ یہ پیغامات صارف اور ایجنٹ کے درمیان گفتگو کی پیش رفت کو ظاہر کرتے ہیں۔ یہ سمجھنا بھی اہم ہے کہ پیغامات مختلف اقسام کے ہو سکتے ہیں، جیسے متن، تصویر، یا فائل، جو یہ بتاتا ہے کہ ایجنٹ کے کام کے نتیجے میں، مثلاً ایک تصویر یا متن کی شکل میں جواب آیا ہے۔ بطور ڈویلپر، آپ اس معلومات کو جوابی کارروائی کو مزید پراسیس کرنے یا صارف کو پیش کرنے کے لیے استعمال کر سکتے ہیں۔

- **دیگر AI فریم ورکس کے ساتھ انضمام**۔ Azure AI Agent سروس، AutoGen اور Semantic Kernel جیسے دیگر فریم ورکس کے ساتھ تعامل کر سکتی ہے، یعنی آپ اپنی ایپ کا کچھ حصہ ان میں سے کسی ایک فریم ورک میں بنا سکتے ہیں اور مثلاً ایجنٹ سروس کو آرکسٹریٹر کے طور پر استعمال کر سکتے ہیں یا آپ سب کچھ ایجنٹ سروس میں بھی بنا سکتے ہیں۔

**استعمال کے کیسز**: Azure AI Agent Service انٹرپرائز ایپلیکیشنز کے لیے ڈیزائن کی گئی ہے جنہیں محفوظ، اسکیل ایبل، اور لچکدار AI ایجنٹ تعیناتی کی ضرورت ہو۔

## ان فریم ورکس کے درمیان کیا فرق ہے؟

یہ بظاہر لگتا ہے کہ ان فریم ورکس کے درمیان بہت زیادہ اوورلیپ ہے، لیکن ان کے ڈیزائن، صلاحیتوں، اور ہدف استعمال کے کیسز کے لحاظ سے کچھ کلیدی فرق ہیں:

- **AutoGen**: تجرباتی فریم ورک ہے جو کثیر ایجنٹ سسٹمز پر جدید تحقیق پر مرکوز ہے۔ یہ ماہر اور پیچیدہ کثیر ایجنٹ سسٹمز کے تجربے اور پروٹو ٹائپ کے لیے بہترین جگہ ہے۔
- **Semantic Kernel**: پیداوار کے قابل ایجنٹ لائبریری ہے جو انٹرپرائز ایجنٹک ایپلیکیشنز بنانے کے لیے ہے۔ یہ ایونٹ پر مبنی، تقسیم شدہ ایجنٹک ایپلیکیشنز پر توجہ مرکوز کرتا ہے، مختلف LLMs اور SLMs، آلات، اور واحد/کثیر ایجنٹ ڈیزائن پیٹرنز کو قابل بناتا ہے۔
- **Azure AI Agent Service**: Azure Foundry میں ایجنٹس کے لیے ایک پلیٹ فارم اور تعیناتی سروس ہے۔ یہ Azure Found کی خدمات کے ساتھ کنیکٹیویٹی بنانے کی پیشکش کرتا ہے، جیسے Azure OpenAI، Azure AI Search، Bing Search اور کوڈ ایگزیکیوشن۔

اب بھی فیصلہ نہیں کر پائے کہ کون سا انتخاب کریں؟

### استعمال کے کیسز

چلیں کچھ عام استعمال کے کیسز پر چل کر دیکھتے ہیں کہ کیا ہم آپ کی مدد کر سکتے ہیں:

> سوال: میں تجربہ کر رہا ہوں، سیکھ رہا ہوں اور پروف آف کانسپٹ ایجنٹ ایپلیکیشنز بنا رہا ہوں، اور میں جلدی سے تعمیر اور تجربہ کرنا چاہتا ہوں۔
>

> جواب: اس منظرنامے کے لیے AutoGen ایک اچھا انتخاب ہوگا، کیونکہ یہ ایونٹ پر مبنی، تقسیم شدہ ایجنٹک ایپلیکیشنز پر توجہ دیتا ہے اور جدید کثیر ایجنٹ ڈیزائن پیٹرنز کی حمایت کرتا ہے۔

> سوال: اس استعمال کے کیس میں AutoGen، Semantic Kernel اور Azure AI Agent Service سے بہتر انتخاب کیوں ہے؟
>
> جواب: AutoGen خاص طور پر ایونٹ پر مبنی، تقسیم شدہ ایجنٹک ایپلیکیشنز کے لیے ڈیزائن کیا گیا ہے، جو کوڈ جنریشن اور ڈیٹا تجزیہ کے کاموں کو خودکار بنانے کے لیے موزوں ہے۔ یہ پیچیدہ کثیر ایجنٹ سسٹمز بنانے کے لیے ضروری آلات اور صلاحیتیں فراہم کرتا ہے۔

> سوال: لگتا ہے کہ Azure AI Agent Service یہاں بھی کام کر سکتا ہے، اس میں کوڈ جنریشن اور دیگر کے لیے آلات ہیں؟
>
> جواب: جی ہاں، Azure AI Agent Service ایجنٹس کے لیے ایک پلیٹ فارم سروس ہے اور متعدد ماڈلز، Azure AI سرچ، Bing سرچ اور Azure فنکشنز کے لیے بلٹ ان صلاحیتیں فراہم کرتی ہے۔ یہ آپ کو Foundry پورٹل میں اپنے ایجنٹس بنانے اور بڑے پیمانے پر تعینات کرنے میں آسانی دیتا ہے۔

> سوال: میں ابھی بھی الجھن میں ہوں، مجھے بس ایک آپشن دیں۔
>
> جواب: ایک بہترین انتخاب یہ ہے کہ آپ اپنی ایپلیکیشن پہلے Semantic Kernel میں بنائیں اور پھر Azure AI Agent Service کو اپنے ایجنٹ کی تعیناتی کے لیے استعمال کریں۔ اس طریقہ سے آپ اپنے ایجنٹس کو آسانی سے مستقل بنا سکتے ہیں اور ساتھ ہی Semantic Kernel میں کثیر ایجنٹ سسٹمز بنانے کی طاقت کا فائدہ اٹھا سکتے ہیں۔ اضافی طور پر، Semantic Kernel کا AutoGen میں ایک کنیکٹر بھی موجود ہے جو دونوں فریم ورکس کو آسانی سے ملانے کے قابل بناتا ہے۔

آئیے کلیدی فرق کو ایک جدول میں خلاصہ کرتے ہیں:

| فریم ورک | توجہ | بنیادی تصورات | استعمال کے کیسز |
| --- | --- | --- | --- |
| AutoGen | ایونٹ پر مبنی، تقسیم شدہ ایجنٹک ایپلیکیشنز | ایجنٹس، پرسناز، فنکشنز، ڈیٹا | کوڈ جنریشن، ڈیٹا تجزیہ کے کام |
| Semantic Kernel | انسانی طرز کے متن کو سمجھنا اور تخلیق کرنا | ایجنٹس، ماڈیولر کمپونینٹس، تعاون | فطری زبان کی سمجھ، مواد تخلیق |
| Azure AI Agent Service | لچکدار ماڈلز، انٹرپرائز سیکیورٹی، کوڈ جنریشن، ٹول کالنگ | ماڈیولیریٹی، تعاون، عمل کی آرکسٹریشن | محفوظ، اسکیل ایبل، اور لچکدار AI ایجنٹ تعیناتی |

ان فریم ورکس میں ہر ایک کے لیے مثالی استعمال کا کیس کیا ہے؟

## کیا میں اپنے موجودہ Azure ماحولیاتی نظام کے آلات کو براہ راست مربوط کر سکتا ہوں، یا مجھے الگ حل کی ضرورت ہے؟

جواب ہاں ہے، آپ اپنے موجودہ Azure ماحولیاتی نظام کے آلات کو خاص طور پر Azure AI Agent Service کے ساتھ براہ راست جوڑ سکتے ہیں، کیونکہ یہ دوسرے Azure سروسز کے ساتھ بلا رکاوٹ کام کرنے کے لیے بنایا گیا ہے۔ مثال کے طور پر، آپ Bing، Azure AI Search، اور Azure Functions کو مربوط کر سکتے ہیں۔ Microsoft Foundry کے ساتھ بھی گہرا انضمام موجود ہے۔

AutoGen اور Semantic Kernel کے لیے، آپ Azure سروسز کے ساتھ مربوط کر سکتے ہیں، لیکن اس کے لیے آپ کو اپنے کوڈ سے Azure سروسز کو کال کرنا پڑ سکتا ہے۔ ایک اور طریقہ یہ ہے کہ آپ Azure SDKs کا استعمال کرتے ہوئے اپنے ایجنٹس سے Azure سروسز کے ساتھ تعامل کریں۔ مزید برآں، جیسا کہ ذکر کیا گیا ہے، آپ Azure AI Agent Service کو AutoGen یا Semantic Kernel میں بنائے گئے اپنے ایجنٹس کے لیے آرکسٹریٹر کے طور پر استعمال کر سکتے ہیں جو Azure ماحولیاتی نظام تک آسان رسائی فراہم کرے گا۔

## نمونہ کوڈز

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## AI Agent Frameworks کے بارے میں مزید سوالات ہیں؟

[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) میں شامل ہوں تاکہ دوسرے سیکھنے والوں سے ملاقات کریں، آفس آورز میں شرکت کریں اور اپنے AI Agents کے سوالات کے جوابات حاصل کریں۔

## حوالہ جات

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel اور AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Azure AI Agent Service کو AutoGen / Semantic Kernel کے ساتھ استعمال کرتے ہوئے کثیر ایجنٹ حل بنانا</a>

## پچھلا سبق

[AI ایجنٹس اور ایجنٹ کے استعمال کے کیسز کا تعارف](../01-intro-to-ai-agents/README.md)

## اگلا سبق

[ایجنٹک ڈیزائن پیٹرنز کو سمجھنا](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**اعلانِ دستبرداری**:  
یہ دستاویز AI ترجمہ سروس [Co-op Translator](https://github.com/Azure/co-op-translator) استعمال کرتے ہوئے ترجمہ کی گئی ہے۔ اگرچہ ہم درستگی کے لیے کوشاں ہیں، براہ کرم اس بات سے آگاہ رہیں کہ خودکار ترجموں میں غلطیاں یا نقائص ہو سکتے ہیں۔ اصل دستاویز اپنی مادری زبان میں ہی معتبر ماخذ سمجھا جائے گا۔ اہم معلومات کے لیے پیشہ ور انسانی ترجمہ کرنا تجویز کیا جاتا ہے۔ اس ترجمے کے استعمال سے پیدا ہونے والے کسی بھی غلط فہم یا غلط تشریحات کے لیے ہم ذمہ دار نہیں ہیں۔
<!-- CO-OP TRANSLATOR DISCLAIMER END -->