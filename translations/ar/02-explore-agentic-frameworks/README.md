[![استكشاف أطر عمل عوامل الذكاء الاصطناعي](../../../translated_images/ar/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(انقر على الصورة أعلاه لمشاهدة فيديو هذا الدرس)_

# استكشاف أطر عمل عوامل الذكاء الاصطناعي

أطر عمل عوامل الذكاء الاصطناعي هي منصات برمجية مصممة لتبسيط إنشاء ونشر وإدارة العوامل الذكية. تزود هذه الأطر المطورين بمكونات مُعدة مسبقًا وتجريدات وأدوات تُسهل تطوير أنظمة ذكاء اصطناعي معقدة.

تساعد هذه الأطر المطورين على التركيز على جوانب تطبيقاتهم الفريدة من خلال توفير نهج موحّد للتعامل مع التحديات الشائعة في تطوير عوامل الذكاء الاصطناعي. كما تعزز قابلية التوسع وسهولة الوصول والكفاءة في بناء أنظمة الذكاء الاصطناعي.

## مقدمة 

سيغطي هذا الدرس:

- ما هي أطر عمل عوامل الذكاء الاصطناعي وما الذي تمكّن المطورين من تحقيقه؟
- كيف يمكن للفرق استخدام هذه الأطر لبناء نماذج أولية بسرعة، والتكرار، وتحسين قدرات وكيلهم؟
- ما الفرق بين الأطر والأدوات التي أنشأتها Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, و <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>؟
- هل يمكنني دمج أدواتي الحالية في منظومة Azure مباشرةً، أم أحتاج إلى حلول مستقلة؟
- ما هي خدمة Azure AI Agents وكيف تساعدني؟

## أهداف التعلم

أهداف هذا الدرس هي مساعدتك على فهم:

- دور أطر عمل عوامل الذكاء الاصطناعي في تطوير الذكاء الاصطناعي.
- كيفية الاستفادة من أطر عمل عوامل الذكاء الاصطناعي لبناء وكلاء أذكياء.
- القدرات الرئيسية التي تمكّنها أطر عمل عوامل الذكاء الاصطناعي.
- الاختلافات بين AutoGen وSemantic Kernel وAzure AI Agent Service.

## ما هي أطر عمل عوامل الذكاء الاصطناعي وما الذي تمكّن المطورين من فعله؟

يمكن لأُطر الذكاء الاصطناعي التقليدية مساعدتك في دمج الذكاء الاصطناعي في تطبيقاتك وتحسين هذه التطبيقات بالطرق التالية:

- **التخصيص**: يمكن للذكاء الاصطناعي تحليل سلوك وتفضيلات المستخدمين لتقديم توصيات ومحتوى وتجارب مخصصة.
مثال: تستخدم خدمات البث مثل Netflix الذكاء الاصطناعي لاقتراح الأفلام والبرامج بناءً على تاريخ المشاهدة، مما يعزز تفاعل المستخدمين ورضاهم.
- **الأتمتة والكفاءة**: يمكن للذكاء الاصطناعي أتمتة المهام المتكررة، وتبسيط سير العمل، وتحسين الكفاءة التشغيلية.
مثال: تستخدم تطبيقات خدمة العملاء روبوتات محادثة مدفوعة بالذكاء الاصطناعي للتعامل مع الاستفسارات الشائعة، مما يقلل أوقات الاستجابة ويتيح للعمال البشر التعامل مع القضايا الأكثر تعقيدًا.
- **تحسين تجربة المستخدم**: يمكن للذكاء الاصطناعي تحسين تجربة المستخدم العامة من خلال توفير ميزات ذكية مثل التعرف على الصوت، ومعالجة اللغة الطبيعية، والنص التنبؤي.
مثال: تستخدم المساعدات الافتراضية مثل Siri وGoogle Assistant الذكاء الاصطناعي لفهم أوامر الصوت والرد عليها، مما يسهل على المستخدمين التفاعل مع أجهزتهم.

### كل هذا يبدو رائعًا، فلماذا نحتاج إلى إطار عمل لعوامل الذكاء الاصطناعي؟

تمثل أطر عمل عوامل الذكاء الاصطناعي شيئًا أكثر من مجرد أطر ذكاء اصطناعي. فهي مصممة لتمكين إنشاء وكلاء أذكياء يمكنهم التفاعل مع المستخدمين، ومع وكلاء آخرين، ومع البيئة لتحقيق أهداف محددة. يمكن لهذه العوامل أن تُظهر سلوكًا مستقلاً، وتتخذ قرارات، وتتكيّف مع الظروف المتغيرة. دعنا نلقي نظرة على بعض القدرات الرئيسية التي تمكّنها أطر عمل عوامل الذكاء الاصطناعي:

- **التعاون والتنسيق بين الوكلاء**: تمكّن إنشاء عدة وكلاء يمكنهم العمل معًا والتواصل والتنسيق لحل مهام معقدة.
- **أتمتة وإدارة المهام**: توفر آليات لأتمتة سير العمل متعدد الخطوات، وتفويض المهام، وإدارة المهام ديناميكيًا بين الوكلاء.
- **الفهم السياقي والتكيّف**: تزود الوكلاء بقدرة على فهم السياق، والتكيّف مع البيئات المتغيرة، واتخاذ قرارات بناءً على معلومات الوقت الحقيقي.

لذا باختصار، تُمكّنك العوامل من فعل المزيد، وتأخذ الأتمتة إلى مستوى أعلى، وتخلق أنظمة أذكى يمكنها التكيّف والتعلم من بيئتها.

## كيف تبني نموذجًا أوليًا بسرعة، وتُجري التكرارات، وتحسن قدرات الوكيل؟

هذا مجال سريع التطور، لكن هناك بعض الأمور المشتركة عبر معظم أُطر عمل عوامل الذكاء الاصطناعي التي يمكن أن تساعدك على بناء نماذج أولية بسرعة وإجراء تكرارات، وهي مكونات وحدوية، أدوات تعاونية، والتعلّم في الوقت الفعلي. لنغص في هذه النقاط:

- **استخدام مكونات معيارية**: توفر مجموعات تطوير البرمجيات مكونات مُعدة مسبقًا مثل موصلات الذكاء الاصطناعي والذاكرة، واستدعاء الدوال باستخدام اللغة الطبيعية أو مكونات إضافية للشفرة، وقوالب المطالبات، والمزيد.
- **الاستفادة من الأدوات التعاونية**: صمم وكلاء بأدوار ومهام محددة، مما يمكّنهم من اختبار وتحسين سير العمل التعاوني.
- **التعلم في الوقت الفعلي**: نفّذ حلقات تغذية راجعة حيث تتعلم الوكلاء من التفاعلات وتُعدّل سلوكها ديناميكيًا.

### استخدم مكونات معيارية

توفر مجموعات SDK مثل Microsoft Semantic Kernel وLangChain مكونات مُعدة مسبقًا مثل موصلات الذكاء الاصطناعي، وقوالب المطالبات، وإدارة الذاكرة.

**كيف يمكن للفرق استخدام هذه**: يمكن للفرق تجميع هذه المكونات بسرعة لإنشاء نموذج أولي وظيفي دون البدء من الصفر، مما يسمح بالتجريب السريع والتكرار.

**كيف يعمل ذلك عمليًا**: يمكنك استخدام محلل مُعد مسبقًا لاستخراج المعلومات من مدخلات المستخدم، ووحدة ذاكرة لتخزين واسترجاع البيانات، ومنشئ مطالبات للتفاعل مع المستخدمين، كل ذلك دون الحاجة لبناء هذه المكونات من البداية.

**مثال على الشيفرة**. لننظر إلى أمثلة حول كيفية استخدام موصل ذكاء اصطناعي مُعد مسبقًا مع Semantic Kernel لبناء Python و.Net الذي يستخدم استدعاء الدوال التلقائي لجعل النموذج يستجيب لمدخلات المستخدم:

``` python
# مثال على Semantic Kernel في بايثون

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# تعريف كائن ChatHistory للاحتفاظ بسياق المحادثة
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# تعريف ملحق تجريبي يحتوي على الدالة لحجز السفر
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# إنشاء النواة Kernel
kernel = Kernel()

# إضافة الملحق التجريبي إلى كائن النواة Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# تعريف موصل Azure OpenAI للذكاء الاصطناعي
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# تعريف إعدادات الطلب لتكوين النموذج مع استدعاء الدوال التلقائي
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # إرسال الطلب إلى النموذج باستخدام تاريخ المحادثة والإعدادات المحددة
    # النواة Kernel يحتوي على العينة التي سيطلب النموذج استدعاؤها
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
    # مثال على استجابة نموذج الذكاء الاصطناعي: `تم حجز رحلتك إلى نيويورك في 1 يناير 2025 بنجاح. رحلة آمنة! ✈️🗽`

    # إضافة استجابة النموذج إلى سياق تاريخ المحادثة الخاص بنا
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

ما يمكنك رؤيته من هذا المثال هو كيف يمكن الاستفادة من محلل مُعد مسبقًا لاستخراج معلومات رئيسية من مدخلات المستخدم، مثل موقع المغادرة والوجهة وتاريخ طلب حجز رحلة. يتيح لك هذا النهج المعياري التركيز على المنطق عالي المستوى.

### الاستفادة من الأدوات التعاونية

تسهل أُطر مثل CrewAI وMicrosoft AutoGen وSemantic Kernel إنشاء عدة وكلاء يمكنهم العمل معًا.

**كيف يمكن للفرق استخدام هذه**: يمكن للفرق تصميم وكلاء بأدوار ومهام محددة، مما يمكّنهم من اختبار وتحسين سير العمل التعاوني وتحسين كفاءة النظام بشكل عام.

**كيف يعمل ذلك عمليًا**: يمكنك إنشاء فريق من الوكلاء حيث يمتلك كل وكيل وظيفة متخصصة، مثل استرجاع البيانات، التحليل، أو اتخاذ القرار. يمكن لهذه الوكلاء التواصل ومشاركة المعلومات لتحقيق هدف مشترك، مثل الإجابة على استعلام مستخدم أو إكمال مهمة.

**مثال على الشيفرة (AutoGen)**:

```python
# إنشاء الوكلاء، ثم إنشاء جدول دوران حيث يمكنهم العمل معًا، في هذه الحالة بالترتيب

# وكيل استرجاع البيانات
# وكيل تحليل البيانات
# وكيل اتخاذ القرار

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

# تنتهي المحادثة عندما يقول المستخدم "موافقة"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# استخدم asyncio.run(...) عند التشغيل في سكريبت.
await Console(stream)
```

ما تراه في الشيفرة السابقة هو كيفية إنشاء مهمة تتضمن عدة وكلاء يعملون معًا لتحليل البيانات. يؤدي كل وكيل وظيفة محددة، وتُنفذ المهمة عن طريق تنسيق الوكلاء لتحقيق النتيجة المطلوبة. من خلال إنشاء وكلاء مكرّسين بأدوار متخصصة، يمكنك تحسين كفاءة وأداء المهام.

### التعلم في الوقت الفعلي

توفر الأُطر المتقدمة قدرات لفهم السياق في الوقت الفعلي والتكيّف.

**كيف يمكن للفرق استخدام هذه**: يمكن للفرق تنفيذ حلقات تغذية راجعة حيث تتعلم الوكلاء من التفاعلات وتُعدّل سلوكها ديناميكيًا، مما يؤدي إلى تحسين مستمر وتطوير للقدرات.

**كيف يعمل ذلك عمليًا**: يمكن للوكلاء تحليل ملاحظات المستخدم وبيانات البيئة ونتائج المهام لتحديث قاعدة معرفتهم، وضبط خوارزميات اتخاذ القرار، وتحسين الأداء مع مرور الوقت. تمكّن عملية التعلم هذه التكرارية الوكلاء من التكيّف مع الظروف المتغيرة وتفضيلات المستخدمين، مما يعزز فعالية النظام بشكل عام.

## ما الفرق بين الأطر AutoGen وSemantic Kernel وخدمة Azure AI Agent؟

هناك العديد من الطرق لمقارنة هذه الأُطر، لكن دعنا نلقي نظرة على بعض الاختلافات الرئيسية من حيث التصميم والقدرات وحالات الاستخدام المستهدفة:

## AutoGen

AutoGen هو إطار مفتوح المصدر طورته مختبرات بحوث الذكاء الاصطناعي في Microsoft Research's AI Frontiers Lab. يركز على تطبيقات *قائمة على الوكلاء* مدفوعة بالأحداث وموزعة، مما يمكّن عدة LLMs وSLMs وأدوات ونماذج تصميم متعددة الوكلاء متقدمة.

تم بناء AutoGen حول المفهوم الأساسي للوكلاء، وهم كيانات مستقلة يمكنها إدراك بيئتها، واتخاذ القرارات، واتخاذ إجراءات لتحقيق أهداف محددة. يتواصل الوكلاء عبر رسائل غير متزامنة أو متزامنة، مما يتيح لهم العمل بشكل مستقل وبالتوازي، مما يعزز قابلية التوسع واستجابة النظام.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">العوامل مبنية على نموذج الممثل</a>. وفقًا لويكيبيديا، الممثل هو _اللبنة الأساسية للحوسبة المتزامنة. استجابةً لرسالة يتلقاها، يمكن للممثل: اتخاذ قرارات محلية، إنشاء المزيد من الممثلين، إرسال المزيد من الرسائل، وتحديد كيفية الرد على الرسالة التالية المستلمة_.

**حالات الاستخدام**: أتمتة توليد الشيفرة، مهام تحليل البيانات، وبناء وكلاء مخصصين لوظائف التخطيط والبحث.

فيما يلي بعض المفاهيم الأساسية المهمة في AutoGen:

- **الوكلاء**. الوكيل هو كيان برمجي يقوم بـ:
  - **يتواصل عبر الرسائل**، يمكن أن تكون هذه الرسائل متزامنة أو غير متزامنة.
  - **يحافظ على حالته الخاصة**، والتي يمكن تعديلها بواسطة الرسائل الواردة.
  - **ينفذ إجراءات** استجابةً للرسائل المستلمة أو التغيّرات في حالته. قد تُعدّل هذه الإجراءات حالة الوكيل وتنتج تأثيرات خارجية، مثل تحديث سجلات الرسائل، إرسال رسائل جديدة، تنفيذ شيفرة، أو إجراء استدعاءات API.
    
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
    
    في الشيفرة السابقة، تم إنشاء `MyAgent` ويرث من `RoutedAgent`. لديه معالج رسائل يطبع محتوى الرسالة ثم يرسل ردًا باستخدام المندوب `AssistantAgent`. لاحظ بشكل خاص كيف نُعيّن إلى `self._delegate` مثيلاً من `AssistantAgent` وهو وكيل مُعد مسبقًا يمكنه التعامل مع استكمالات الدردشة.


    دعنا نُعلِم AutoGen بهذا النوع من الوكلاء ونطلق البرنامج بعد ذلك:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # ابدأ معالجة الرسائل في الخلفية.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    في الشيفرة السابقة يتم تسجيل الوكلاء مع وقت التشغيل ثم تُرسل رسالة إلى الوكيل مما يؤدي إلى الناتج التالي:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **أنظمة متعددة الوكلاء**. يدعم AutoGen إنشاء عدة وكلاء يمكنهم العمل معًا لتحقيق مهام معقدة. يمكن للوكلاء التواصل ومشاركة المعلومات وتنسيق أفعالهم لحل المشكلات بكفاءة أكبر. لإنشاء نظام متعدد الوكلاء، يمكنك تعريف أنواع مختلفة من الوكلاء بوظائف وأدوار متخصصة، مثل استرجاع البيانات، التحليل، اتخاذ القرار، والتفاعل مع المستخدم. لنرَ كيف يبدو مثل هذا الإنشاء لنفهمه:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # مثال على إعلان وكيل
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # استخدام نوع الموضوع كنوع الوكيل.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY"،
        ),
        ),
    )

    # تم اختصار الإعلانات المتبقية للاختصار

    # دردشة جماعية
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY"،
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

    في الشيفرة السابقة لدينا `GroupChatManager` مسجّل مع وقت التشغيل. هذا المدير مسؤول عن تنسيق التفاعلات بين أنواع مختلفة من الوكلاء، مثل الكتاب، والرسّامين، والمحررين، والمستخدمين.

- **وقت تشغيل الوكلاء**. يوفر الإطار بيئة وقت تشغيل، تمكّن التواصل بين الوكلاء، وتدير هوياتهم ودورات حياتهم، وتفرض حدود الأمان والخصوصية. هذا يعني أنه يمكنك تشغيل وكلائك في بيئة آمنة ومراقبة، مما يضمن قدرتهم على التفاعل بأمان وكفاءة. هناك وقتان للتشغيل ذو أهمية:
  - **وقت تشغيل مستقل**. هذا خيار جيد لتطبيقات العملية الواحدة حيث يتم تنفيذ جميع الوكلاء بنفس لغة البرمجة ويعملون في نفس العملية. إليك توضيحًا لكيفية عمله:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">وقت تشغيل مستقل</a>   
مكدس التطبيق

    *يتواصل الوكلاء عبر الرسائل من خلال وقت التشغيل، ويدير وقت التشغيل دورة حياة الوكلاء*

  - **وقت تشغيل موزع للوكلاء**، مناسب لتطبيقات متعددة العمليات حيث قد يتم تنفيذ الوكلاء بلغات برمجة مختلفة وعلى أجهزة مختلفة. إليك توضيحًا لكيفية عمله:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">وقت تشغيل موزع</a>

## Semantic Kernel + إطار عمل الوكلاء

Semantic Kernel هو SDK لتنسيق الذكاء الاصطناعي جاهز للمؤسسات. يتألف من موصلات ذكاء اصطناعي وذاكرة، إلى جانب إطار عمل للوكلاء.

دعنا نغطي أولًا بعض المكونات الأساسية:

- **موصلات الذكاء الاصطناعي**: هذا واجهة مع خدمات وموارد بيانات خارجية لاستخدامها في كل من Python وC#.

  ```python
  # نواة الدلالات بايثون
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

    هنا لديك مثال بسيط عن كيفية إنشاء kernel وإضافة خدمة استكمال الدردشة. ينشئ Semantic Kernel اتصالًا بخدمة ذكاء اصطناعي خارجية، في هذه الحالة، Azure OpenAI Chat Completion.

- **الإضافات (Plugins)**: تغلّف هذه الوظائف التي يمكن للتطبيق استخدامها. هناك إضافات جاهزة وإضافات مخصصة يمكنك إنشاؤها. مفهوم ذو علاقة هو "دوال المطالبة". بدلًا من تقديم تلميحات لغة طبيعية لاستدعاء الدوال، تقوم ببث بعض الدوال إلى النموذج. بناءً على سياق الدردشة الحالي، قد يختار النموذج استدعاء إحدى هذه الدوال لإكمال طلب أو استعلام. إليك مثالًا:

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

    هنا، لديك أولًا قالب مطالبة `skPrompt` يترك مكانًا للمستخدم لإدخال نص، `$userInput`. ثم تنشئ دالة kernel `SummarizeText` ثم تستوردها إلى kernel باسم الإضافة `SemanticFunctions`. لاحظ اسم الدالة الذي يساعد Semantic Kernel على فهم ما تفعله الدالة ومتى ينبغي استدعاؤها.

- **الدالة الأصلية**: هناك أيضًا دوال أصلية يمكن للإطار استدعاؤها مباشرة للقيام بالمهمة. إليك مثالاً على مثل هذه الدالة التي تسترجع المحتوى من ملف:

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

- **الذاكرة**: تُجرد وتبسط إدارة السياق لتطبيقات الذكاء الاصطناعي. الفكرة مع الذاكرة هي أن هذا شيء يجب أن يعرفه LLM. يمكنك تخزين هذه المعلومات في مخزن متجهات الذي ينتهي به المطاف بأن يكون قاعدة بيانات في الذاكرة أو قاعدة بيانات متجهات أو ما شابه. إليك مثالًا لسيناريو مبسّط جدًا حيث تُضاف *حقائق* إلى الذاكرة:

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

    تُخزّن هذه الحقائق بعد ذلك في مجموعة الذاكرة `SummarizedAzureDocs`. هذا مثال مبسّط جدًا، لكن يمكنك أن ترى كيف يمكنك تخزين المعلومات في الذاكرة لاستخدامها من قِبل نموذج اللغة الكبير.

إذًا هذه هي أساسيات إطار عمل Semantic Kernel، ماذا عن إطار عمل الوكلاء (Agent Framework)؟

## Azure AI Agent Service

تُعد خدمة Azure AI Agent Service إضافة أحدث، تم تقديمها في Microsoft Ignite 2024. تتيح تطوير ونشر وكلاء ذكاء اصطناعي بنماذج أكثر مرونة، مثل استدعاء نماذج LLM مفتوحة المصدر مباشرة مثل Llama 3 وMistral وCohere.

توفر خدمة Azure AI Agent Service آليات أمان للمؤسسات وطرق تخزين بيانات أقوى، مما يجعلها مناسبة لتطبيقات المؤسسات.

تعمل خارج الصندوق مع أطر تنسيق الوكلاء متعددة الوكلاء مثل AutoGen وSemantic Kernel.

هذه الخدمة متاحة حاليًا في المعاينة العامة وتدعم Python وC# لبناء الوكلاء.

باستخدام Semantic Kernel Python، يمكننا إنشاء وكيل Azure AI مع مكوّن إضافي مُعرّف من قبل المستخدم:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# تعريف إضافة نموذجية للنموذج
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
        # إنشاء تعريف الوكيل
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # إنشاء وكيل AzureAI باستخدام العميل وتعريف الوكيل المعرفة
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # إنشاء سلسلة للاحتفاظ بالمحادثة
        # إذا لم يتم توفير سلسلة، سيتم
        # إنشاء سلسلة جديدة وإرجاعها مع الاستجابة الأولية
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
                # استدعاء الوكيل للسلسلة المحددة
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

### المفاهيم الأساسية

تملك خدمة Azure AI Agent Service المفاهيم الأساسية التالية:

- **وكيل (Agent)**. تندمج خدمة Azure AI Agent Service مع Microsoft Foundry. داخل AI Foundry، يعمل الوكيل كخدمة مصغّرة "ذكية" يمكن استخدامها للإجابة على الأسئلة (RAG)، تنفيذ إجراءات، أو أتمتة سير العمل تمامًا. يحقق ذلك من خلال مزج قوة نماذج التوليد مع الأدوات التي تتيح له الوصول إلى مصادر بيانات العالم الحقيقي والتفاعل معها. إليك مثالًا على وكيل:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    في هذا المثال، يتم إنشاء وكيل بالموديل `gpt-4o-mini`، واسم `my-agent`، وتعليمات `You are helpful agent`. يُجهّز الوكيل بأدوات وموارد لأداء مهام تفسير الكود.

- **الخيط والرسائل (Thread and messages)**. الخيط مفهوم مهم آخر. يمثل المحادثة أو التفاعل بين الوكيل والمستخدم. يمكن استخدام الخيوط لتعقب تقدم المحادثة، تخزين معلومات السياق، وإدارة حالة التفاعل. إليك مثالًا على خيط:

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

    في الكود السابق، يتم إنشاء خيط. بعد ذلك، تُرسل رسالة إلى الخيط. عبر استدعاء `create_and_process_run`، يُطلب من الوكيل أداء عمل على الخيط. أخيرًا، تُجلب الرسائل وتُسجَّل لرؤية استجابة الوكيل. تشير الرسائل إلى تقدم المحادثة بين المستخدم والوكيل. من المهم أيضًا فهم أن الرسائل يمكن أن تكون من أنواع مختلفة مثل نص أو صورة أو ملف؛ أي أن عمل الوكلاء قد يؤدي، على سبيل المثال، إلى صورة أو استجابة نصية. كمطور، يمكنك بعد ذلك استخدام هذه المعلومات لمعالجة الاستجابة بشكل إضافي أو عرضها على المستخدم.

- **التكامل مع أُطر ذكاء اصطناعي أخرى**. يمكن لخدمة Azure AI Agent التفاعل مع أُطر أخرى مثل AutoGen وSemantic Kernel، مما يعني أنه يمكنك بناء جزء من تطبيقك في أحد هذه الأُطر واستخدام خدمة الوكيل كمُنَسِّق، أو يمكنك بناء كل شيء داخل خدمة الوكيل.

**حالات الاستخدام**: تم تصميم خدمة Azure AI Agent Service لتطبيقات المؤسسات التي تتطلب نشر وكلاء ذكاء اصطناعي آمن وقابل للتوسع ومرن.

## ما الفرق بين هذه الأُطر؟
 
قد يبدو أن هناك قدرًا كبيرًا من التداخل بين هذه الأُطر، لكن هناك بعض الاختلافات الرئيسية من حيث التصميم والقدرات وحالات الاستخدام المستهدفة:
 
- **AutoGen**: إطار تجريبي يركز على أبحاث الأنظمة متعددة الوكلاء المتقدمة. هو المكان الأفضل للتجربة ونمذجة الأنظمة متعددة الوكلاء المعقدة.
- **Semantic Kernel**: مكتبة جاهزة للإنتاج لبناء تطبيقات وكيلية للمؤسسات. يركز على التطبيقات الوكيلية الموزعة والمدفوعة بالأحداث، ويمكّن من استخدام عدة نماذج LLM وSLM، أدوات، ونماذج تصميم لوكيل واحد/متعدد.
- **Azure AI Agent Service**: منصة وخدمة نشر في Azure Foundry للوكلاء. يوفر بنية لبناء الاتصال بخدمات تدعمها Azure Found مثل Azure OpenAI وAzure AI Search وBing Search وتنفيذ الكود.
 
لا تزال غير متأكد أي واحد تختار؟

### حالات الاستخدام
 
دعنا نرى إن كان بإمكاننا مساعدتك من خلال استعراض بعض حالات الاستخدام الشائعة:
 
> س: أنا أجرب وأتعلم وأبني تطبيقات وكيلة إثبات الفكرة، وأريد أن أتمكن من البناء والتجريب بسرعة
>

>ج: سيكون AutoGen خيارًا جيدًا لهذا السيناريو، لأنه يركز على التطبيقات الوكيلية الموزعة والمدفوعة بالأحداث ويدعم أنماط تصميم متقدمة متعددة الوكلاء.

> س: ما الذي يجعل AutoGen خيارًا أفضل من Semantic Kernel وAzure AI Agent Service لهذا الاستخدام؟
>
> ج: صُمّم AutoGen خصيصًا للتطبيقات الوكيلية الموزعة والمدفوعة بالأحداث، مما يجعله مناسبًا لأتمتة توليد الشيفرة ومهام تحليل البيانات. يوفر الأدوات والقدرات اللازمة لبناء أنظمة متعددة الوكلاء المعقدة بكفاءة.

>س: يبدو أن خدمة Azure AI Agent Service قد تنجح هنا أيضًا، فلديها أدوات لتوليد الشيفرة والمزيد؟
>
> ج: نعم، تُعد خدمة Azure AI Agent Service خدمة منصة للوكلاء وتضيف قدرات مدمجة لدعم نماذج متعددة، Azure AI Search، Bing Search وAzure Functions. تجعل من السهل بناء وكلائك في بوابة Foundry ونشرهم على نطاق واسع.
 
> س: ما زلت محتارًا أعطني خيارًا واحدًا فقط
>
> ج: خيار رائع هو بناء تطبيقك في Semantic Kernel أولًا ثم استخدام Azure AI Agent Service لنشر وكيلك. تتيح هذه الطريقة الاحتفاظ بوكلائك بسهولة بينما تستفيد من القوة لبناء أنظمة متعددة الوكلاء في Semantic Kernel. بالإضافة إلى ذلك، لدى Semantic Kernel موصِل في AutoGen، مما يسهل استخدام الإطارين معًا.
 
لنلخّص الاختلافات الرئيسية في جدول:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | تطبيقات وكيلية موزعة مدفوعة بالأحداث | Agents, Personas, Functions, Data | توليد الشيفرة، مهام تحليل البيانات |
| Semantic Kernel | فهم وتوليد محتوى شبيه بالبشر | Agents, Modular Components, Collaboration | فهم اللغة الطبيعية، توليد المحتوى |
| Azure AI Agent Service | نماذج مرنة، أمان للمؤسسات، توليد الشيفرة، استدعاء الأدوات | Modularity, Collaboration, Process Orchestration | نشر وكلاء ذكاء اصطناعي آمنين وقابلين للتوسع ومرنين |

ما هي حالة الاستخدام المثالية لكل من هذه الأُطر؟

## هل يمكنني دمج أدوات منظومة Azure الحالية مباشرة، أم أحتاج حلولًا مستقلة؟

الإجابة نعم، يمكنك دمج أدوات منظومة Azure الحالية مباشرة مع خدمة Azure AI Agent Service بشكل خاص، لأن هذه الخدمة بُنيت لتعمل بسلاسة مع خدمات Azure الأخرى. يمكنك على سبيل المثال دمج Bing وAzure AI Search وAzure Functions. هناك أيضًا تكامل عميق مع Microsoft Foundry.

بالنسبة إلى AutoGen وSemantic Kernel، يمكنك أيضًا التكامل مع خدمات Azure، لكن قد يتطلب الأمر استدعاء خدمات Azure من كودك. طريقة أخرى للتكامل هي استخدام Azure SDKs للتفاعل مع خدمات Azure من وكلائك. بالإضافة إلى ذلك، كما ذُكر، يمكنك استخدام Azure AI Agent Service كمُنَسِّق لوكلائك المبنيين في AutoGen أو Semantic Kernel مما يمنح وصولًا سهلاً إلى منظومة Azure.

## أمثلة على الشيفرات

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## هل لديك المزيد من الأسئلة حول أُطر وكلاء الذكاء الاصطناعي؟

انضم إلى [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) للالتقاء بمتعلمين آخرين، حضور ساعات المكتب، والحصول على إجابات لأسئلتك حول وكلاء الذكاء الاصطناعي.

## المراجع

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">خدمة Azure Agent</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel وAutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">إطار وكلاء Semantic Kernel بلغة Python</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">إطار وكلاء Semantic Kernel بلغة .Net</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">خدمة Azure AI Agent</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">استخدام خدمة Azure AI Agent مع AutoGen / Semantic Kernel لبناء حل متعدد الوكلاء</a>

## الدرس السابق

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## الدرس التالي

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
إخلاء المسؤولية:
تمت ترجمة هذا المستند باستخدام خدمة الترجمة الآلية Co-op Translator (https://github.com/Azure/co-op-translator). بينما نسعى للحفاظ على الدقة، يُرجى العلم بأن الترجمات الآلية قد تحتوي على أخطاء أو عدم دقة. يجب اعتبار المستند الأصلي بلغته الأصلية المصدر المرجعي والموثوق. للمعلومات الحساسة أو الحرجة، يُنصح بالاستعانة بترجمة بشرية محترفة. لا نتحمل أي مسؤولية عن أي سوء فهم أو تفسير ناتج عن استخدام هذه الترجمة.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->