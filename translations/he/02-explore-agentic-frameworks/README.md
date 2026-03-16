[![חקירת מסגרות סוכני AI](../../../translated_images/he/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(לחצו על התמונה למעלה לצפייה בווידאו של השיעור הזה)_

# חקור מסגרות סוכני AI

מסגרות סוכני AI הן פלטפורמות תוכנה שנועדו לפשט את יצירת, הפיתוח והניהול של סוכני AI. מסגרות אלו מספקות למפתחים רכיבים קיימים, הפשטות וכלים שמייעלים את הפיתוח של מערכות AI מורכבות.

מסגרות אלו מסייעות למפתחים למקד את תשומת הלב בהיבטים הייחודיים של היישומים שלהם על ידי מתן גישות סטנדרטיות לאתגרים נפוצים בפיתוח סוכני AI. הן משפרות את יכולת ההרחבה, הנגישות והיעילות בבניית מערכות AI.

## מבוא

השיעור הזה יכסה:

- מהן מסגרות סוכני AI ומה הן מאפשרות למפתחים להשיג?
- איך צוותים יכולים להשתמש בהן כדי להציג אב-טיפוס במהירות, לאפשר איטרציות ולשפר את יכולות הסוכן שלהם?
- מהם ההבדלים בין המסגרות והכלים שיצרה מיקרוסופט <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, ו-<a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- האם ניתן לשלב את הכלים הקיימים שלי באקו-סיסטם של Azure ישירות, או שדרושות פתרונות עצמאיים?
- מהי שירות Azure AI Agents ואיך זה עוזר לי?

## מטרות למידה

מטרות השיעור הן לסייע לך להבין:

- את התפקיד של מסגרות סוכני AI בפיתוח AI.
- איך לנצל מסגרות סוכני AI לבניית סוכנים אינטליגנטיים.
- יכולות מפתח שמאפשרות מסגרות סוכני AI.
- את ההבדלים בין AutoGen, Semantic Kernel, ו-Azure AI Agent Service.

## מהן מסגרות סוכני AI ומה הן מאפשרות למפתחים לעשות?

מסגרות AI מסורתיות יכולות לסייע לך לשלב AI באפליקציות שלך ולשפר את האפליקציות בדרכים הבאות:

- **התאמה אישית**: AI יכול לנתח התנהגות והעדפות משתמש כדי לספק המלצות, תוכן וחוויות מותאמות אישית.  
דוגמה: שירותי סטרימינג כמו Netflix משתמשים ב-AI כדי להציע סרטים ותוכניות בהתבסס על היסטוריית הצפייה, מה שמגביר את מעורבות המשתמשים והסיפוק שלהם.  
- **אוטומציה ויעילות**: AI יכול לאוטומט משימות חוזרות, לייעל תהליכים ולהגדיל את היעילות התפעולית.  
דוגמה: אפליקציות שירות לקוחות משתמשות בצ'אטבוטים המופעלים על ידי AI כדי לטפל בפניות נפוצות, להפחית זמני תגובה ולהשאיר סוכני אנוש למשימות מורכבות יותר.  
- **שיפור חוויית המשתמש**: AI יכול לשדרג את חוויית המשתמש הכוללת באמצעות תכונות אינטליגנטיות כמו זיהוי קולי, עיבוד שפה טבעית, וטקסט מנבא.  
דוגמה: עוזרים וירטואליים כמו סירי ועוזר גוגל משתמשים ב-AI כדי להבין ולהגיב לפקודות קוליות, מה שמקל על המשתמשים באינטראקציה עם המכשירים שלהם.

### הכל נשמע נהדר, אז למה אנו צריכים את מסגרת סוכני AI?

מסגרות סוכני AI מייצגות משהו מעבר למסגרות AI רגילות. הן מיועדות לאפשר יצירה של סוכנים אינטליגנטיים שיכולים לקיים אינטראקציה עם משתמשים, עם סוכנים אחרים ועם הסביבה כדי להשיג מטרות ספציפיות. סוכנים אלו יכולים להציג התנהגות אוטונומית, לקבל החלטות ולהסתגל לתנאים משתנים. בואו נבחן כמה יכולות מרכזיות שמאפשרות מסגרות סוכני AI:

- **שיתוף פעולה ותיאום בין סוכנים**: מאפשר יצירת מספר סוכני AI שיכולים לעבוד ביחד, לתקשר ולתאם כדי לפתור משימות מורכבות.  
- **אוטומציה וניהול משימות**: מספק מנגנונים לאוטומציה של תהליכי עבודה מרובי שלבים, האצלת משימות וניהול דינמי של משימות בין הסוכנים.  
- **הבנה והסתגלות הקשרית**: מצייד סוכנים ביכולת להבין הקשר, להסתגל לסביבות משתנות ולקבל החלטות בהתבסס על מידע בזמן אמת.

לסיכום, סוכנים מאפשרים לך לעשות יותר, לקחת אוטומציה לרמה הבאה, וליצור מערכות אינטליגנטיות שיכולות להסתגל וללמוד מהסביבה שלהן.

## איך להציג אב-טיפוס במהירות, לבצע איטרציה ולשפר את יכולות הסוכן?

זהו תחום שמתפתח במהירות, אבל יש כמה תכונות שמקובלות ברוב מסגרות סוכני AI שיכולות לסייע לך לאבטיפוס ולאיטרציה מהירה, כגון רכיבי מודולים, כלי שיתוף פעולה ולמידה בזמן אמת. בוא נדבר עליהם:

- **שימוש ברכיבי מודולים**: ערכות פיתוח AI מספקות רכיבים מוכנים מראש כמו מחברים ל-AI ולזיכרון, קריאת פונקציות באמצעות שפה טבעית או תוספים, תבניות הנעה, ועוד.  
- **ניצול כלי שיתוף פעולה**: עיצוב סוכנים עם תפקידים ומשימות ספציפיים, מה שמאפשר להם לבדוק ולחדד זרימות עבודה שיתופיות.  
- **למידה בזמן אמת**: יישום לולאות משוב שבהן סוכנים לומדים מהאינטראקציות ומותאמים את התנהגותם באופן דינמי.

### שימוש ברכיבי מודולים

SDKים כמו Microsoft Semantic Kernel ו-LangChain מציעים רכיבים מוכנים מראש כגון מחברים ל-AI, תבניות הנעה וניהול זיכרון.

**איך צוותים יכולים להשתמש בהם**: צוותים יכולים להרכיב מהר רכיבים אלו ליצירת אב-טיפוס פונקציונלי ללא התחלה מאפס, מה שמאפשר ניסוי ואיטרציה מהירים.

**איך זה עובד בפועל**: ניתן להשתמש באנלייזר מוכן מראש כדי לחלץ מידע מתוך קלט משתמש, מודול זיכרון לאחסון ושליפת נתונים, ומחולל הנעה לאינטראקציה עם משתמשים, הכל בלי לבנות רכיבים אלה מהתחלה.

**דוגמאות קוד**. בוא נראה דוגמאות לשימוש במחבר AI מוכן מראש עם Semantic Kernel ב-Python ו-.Net שמשתמש בקריאת פונקציות אוטומטית כדי שהמודל יגיב לקלט המשתמש:

``` python
# דוגמת Semantic Kernel בפייתון

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# הגדר אובייקט ChatHistory שיחזיק את ההקשר של השיחה
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# הגדר תוסף לדוגמה שמכיל פונקציה להזמנת נסיעה
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# צור את ה-Kernel
kernel = Kernel()

# הוסף את התוסף לדוגמה לאובייקט ה-Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# הגדר את מחבר Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# הגדר את הגדרות הבקשה כדי לקנפג את המודל לקריאה אוטומטית של פונקציות
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # בצע את הבקשה למודל עבור היסטוריית השיחה והגדרות הבקשה הנתונות
    # ה-Kernel מכיל את הדוגמה שהמודל יבקש להפעיל
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
    # דוגמת תגובת מודל ה-AI: `הטיסה שלך לניו יורק ב-1 בינואר 2025 הוזמנה בהצלחה. נסיעה נעימה! ✈️🗽`

    # הוסף את תגובת המודל להיסטוריית השיחה שלנו
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
  
מה שניתן לראות מדוגמה זו הוא איך ניתן לנצל אנלייזר מוכן מראש כדי להוציא מידע מרכזי מקלט המשתמש, כמו מקור, יעד ותאריך בקשת הזמנת טיסה. גישה מודולרית זו מאפשרת לך למקד את הלוגיקה ברמה גבוהה.

### ניצול כלי שיתוף פעולה

מסגרות כמו CrewAI, Microsoft AutoGen ו-Semantic Kernel מאפשרות יצירת מספר סוכנים שעובדים יחד.

**איך צוותים יכולים להשתמש בהם**: צוותים יכולים לתכנן סוכנים בעלי תפקידים ומשימות מוגדרות, מה שמאפשר להם לבדוק ולחדד זרימות עבודה שיתופיות ולשפר את היעילות הכוללת של המערכת.

**איך זה עובד בפועל**: ניתן ליצור צוות של סוכנים שכל אחד מהם מתמחה בתפקיד מיוחד, כמו שליפת נתונים, ניתוח או קבלת החלטות. סוכנים אלו יכולים לתקשר ולחלוק מידע כדי להשיג מטרה משותפת, כמו מענה לשאלה של משתמש או השלמת משימה.

**דוגמאות קוד (AutoGen)**:

```python
# יצירת סוכנים, ואז יצירת לוח זמנים סיבובי שבו הם יכולים לעבוד יחד, במקרה זה לפי הסדר

# סוכן אחזור נתונים
# סוכן ניתוח נתונים
# סוכן קבלת החלטות

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

# השיחה מסתיימת כאשר המשתמש אומר "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# השתמש ב-asyncio.run(...) בעת הרצה בסקריפט
await Console(stream)
```
  
מה שרואים בקוד שלמעלה הוא איך ליצור משימה שמערבת מספר סוכנים שעובדים יחד לניתוח נתונים. כל סוכן מבצע פונקציה מסוימת, והמשימה מתבצעת על ידי תיאום הפעולות בין הסוכנים להשגת התוצאה הרצויה. על ידי יצירת סוכנים ייעודיים בעלי תפקידים מיוחדים, ניתן לשפר את היעילות והביצועים של המשימה.

### למידה בזמן אמת

מסגרות מתקדמות מספקות יכולות להבנת הקשר בזמן אמת והסתגלות.

**איך צוותים יכולים להשתמש בהם**: ניתן ליישם לולאות משוב שבהן סוכנים לומדים מאינטראקציות ומותאמים את התנהגותם באופן דינמי, מה שמוביל לשיפור מתמיד ולטיוב היכולות.

**איך זה עובד בפועל**: סוכנים יכולים לנתח משוב משתמשים, נתוני סביבה ותוצאות משימות כדי לעדכן את מאגר הידע שלהם, לכוון אלגוריתמי קבלת החלטות ולשפר ביצועים לאורך זמן. תהליך למידה איטרטיבי זה מאפשר לסוכנים להסתגל לתנאים ולהעדפות משתנות, ומשפר את היעילות הכוללת של המערכת.

## מהם ההבדלים בין המסגרות AutoGen, Semantic Kernel ו-Azure AI Agent Service?

ישנן דרכים רבות להשוות בין המסגרות הללו, אך נבחן כמה הבדלים מרכזיים מבחינת עיצובן, יכולותיהן ומקרי השימוש המיועדים להן:

## AutoGen

AutoGen היא מסגרת קוד פתוח שפותחה על ידי מעבדת AI Frontiers של Microsoft Research. היא מתמקדת ביישומי סוכנים מבוזרים המונעים אירועים, ומאפשרת שימוש במספר LLMs ו-SLMs, כלים ותבניות עיצוב מתקדמות למערכות רב-סוכנים.

AutoGen בנויה סביב המושג המרכזי של סוכנים, שהם ישויות אוטונומיות שיכולות לתפוס את הסביבה שלהן, לקבל החלטות ולקחת פעולות להשגת מטרות ספציפיות. סוכנים מתקשרים דרך הודעות אסינכרוניות, מה שמאפשר להם לפעול באופן עצמאי וב-parallel, ומשפר את יכולת ההרחבה והתגובה של המערכת.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">סוכנים מבוססים על מודל השחקן</a>. לפי ויקיפדיה, שחקן הוא _היחידה הבסיסית של חישוב מקבילי. בתגובה להודעה שהוא מקבל, שחקן יכול: לקבל החלטות מקומיות, ליצור שחקנים נוספים, לשלוח הודעות נוספות, ולקבוע כיצד להגיב להודעה הבאה שיתקבל_.

**מקרי שימוש**: אוטומציה של יצירת קוד, משימות ניתוח נתונים, ובניית סוכנים מותאמים לפונקציות תכנון ומחקר.

הנה כמה מושגי יסוד חשובים ב-AutoGen:

- **סוכנים**. סוכן הוא ישות תוכנה שמבצעת:
  - **תקשורת באמצעות הודעות**, שהן יכולות להיות סינכרוניות או אסינכרוניות.  
  - **שומר על מצבו האישי**, שניתן לשנות על-ידי הודעות נכנסות.  
  - **מבצע פעולות** בתגובה להודעות שמתקבלות או לשינויים במצבו. פעולות אלו עשויות לשנות את מצבו של הסוכן וליצור השפעות חיצוניות, כגון עדכון רשומות הודעות, שליחת הודעות חדשות, ביצוע קוד, או ביצוע קריאות API.  
    
  כאן יש קטע קוד קצר שבו יוצרים סוכן עם יכולות שיחה:

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
    
    בקוד שלמעלה, `MyAgent` נוצר ויורש מ-`RoutedAgent`. יש לו מטפל הודעות שמדפיס את תוכן ההודעה ואז שולח תגובה באמצעות הנציג `AssistantAgent`. שימו לב במיוחד איך אנו משייכים ל-`self._delegate` מופע של `AssistantAgent` שהוא סוכן מוכן שיכול לטפל בהשלמות שיחה.

    עכשיו ניתן ל-AutoGen לדעת על סוג הסוכן הזה ולהפעיל את התוכנית:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # התחל לעבד הודעות ברקע.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    בקוד שלמעלה הסוכנים נרשמים בסביבת הריצה ואז נשלחת הודעה לסוכן שגורמת לפלט הבא:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **רב-סוכנים**. AutoGen תומך ביצירת מספר סוכנים שיכולים לעבוד יחד כדי להשיג משימות מורכבות. סוכנים יכולים לתקשר, לחלוק מידע ולתאם את פעולותיהם כדי לפתור בעיות ביעילות רבה יותר. ליצירת מערכת רב-סוכנים, ניתן להגדיר סוגים שונים של סוכנים עם פונקציות ותפקידים מיוחדים, כמו שליפת נתונים, ניתוח, קבלת החלטות ואינטראקציה עם משתמשים. בוא נראה איך נראית יצירה כזו כדי לקבל מושג:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # דוגמה להכרזת סוכן
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # שימוש בסוג topic כסוג הסוכן.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # ההכרזות הנותרות מקוצרות למען תמציתיות

    # צ'אט קבוצתי
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

    בקוד שלמעלה יש לנו `GroupChatManager` שנרשם לסביבת הריצה. מנהל זה אחראי לתיאום האינטראקציות בין סוגים שונים של סוכנים, כמו סופרים, מאיירים, עורכים ומשתמשים.

- **סביבת ריצה של סוכן**. המסגרת מספקת סביבת ריצה, שמאפשרת תקשורת בין סוכנים, מנהלת את זהויותיהם ומחזור חייהם, ואוכפת גבולות אבטחה ופרטיות. משמעות הדבר היא שתוכל להריץ את הסוכנים שלך בסביבה מאובטחת ומבוקרת, שמבטיחה שאפשר יהיה לקיים אינטראקציות בבטחה וביעילות. ישנן שתי סביבות ריצה מעניינות:  
  - **סביבת ריצה עצמאית**. זוהי בחירה טובה לאפליקציות חד-תהליכיות שבהן כל הסוכנים ממומשים באותה שפת תכנות ומורצים בתהליך אחד. להלן המחשה של אופן הפעולה:  
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">סביבת ריצה עצמאית</a>   
מערך יישומים

    *הסוכנים מתקשרים באמצעות הודעות דרך סביבת הריצה, וסביבת הריצה מנהלת את מחזור החיים של הסוכנים*

  - **סביבת ריצה מבוזרת**, מתאימה לאפליקציות מרובות תהליכים שבהן סוכנים יכולים להיות ממומשים בשפות תכנות שונות ולרוץ על מכונות שונות. להלן המחשה של אופן הפעולה:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">סביבת ריצה מבוזרת</a>

## Semantic Kernel + מסגרת סוכנים

Semantic Kernel היא SDK מוכנה לארגונים לאורקסטרציה של AI. היא כוללת מחברים ל-AI ולזיכרון, יחד עם מסגרת סוכנים.

נתחיל בכמה רכיבים מרכזיים:

- **מחברי AI**: ממשק עם שירותי AI חיצוניים ומקורות נתונים לשימוש הן ב-Python והן ב-C#.

  ```python
  # גרעין סמנטי פייתון
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
  
    כאן יש דוגמה פשוטה כיצד ליצור kernel ולהוסיף שירות השלמת שיחה. Semantic Kernel יוצר חיבור לשירות AI חיצוני, במקרה זה, Azure OpenAI Chat Completion.

- **תוספים**: אלה כוללים פונקציות שהאפליקציה יכולה להשתמש בהן. קיימים תוספים מוכנים וגם תוספים מותאמים שניתן ליצור. מושג קשור הוא "פונקציות הנעה". במקום לספק רמזים בשפה טבעית להפעלת פונקציות, אתה משדר פונקציות מסוימות למודל. בהתבסס על ההקשר הנוכחי של השיחה, המודל עשוי לבחור לקרוא לאחת מהפונקציות הללו כדי להשלים בקשה או שאלה. הנה דוגמה:

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
  
    כאן יש לך תבנית הנעה `skPrompt` שמשאירה מקום למשתמש להזין טקסט, `$userInput`. לאחר מכן יוצרים את פונקציית ה-kernel `SummarizeText` ומייבאים אותה ל-kernel עם שם התוסף `SemanticFunctions`. שים לב לשם הפונקציה שעוזר ל-Semantic Kernel להבין מה הפונקציה עושה ומתי יש להיקרא.

- **פונקציה מקורית**: קיימות גם פונקציות מקוריות שהמסגרת יכולה לקרוא אליהן ישירות כדי לבצע את המשימה. הנה דוגמה לפונקציה שמבצעת שליפה של תוכן מקובץ:

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
  
- **זיכרון**: מפשט ומפשט את ניהול ההקשר עבור אפליקציות AI. הרעיון עם הזיכרון הוא שזה משהו שה-LLM אמור לדעת עליו. ניתן לאחסן את המידע הזה במסגרת וקטורית המשמשת כמסד נתונים בזיכרון או כמאגר וקטורים דומה. הנה דוגמה לתרחיש מאוד פשוט שבו *עובדות* מתווספות לזיכרון:

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

העובדות הללו מאוחסנות לאחר מכן באוסף הזיכרון `SummarizedAzureDocs`. זהו דוגמה מפושטת מאוד, אך ניתן לראות כיצד ניתן לאחסן מידע בזיכרון לשימוש ה-LLM.

אז אלו היסודות של מסגרת Semantic Kernel, מה לגבי מסגרת ה-Agent?

## שירות Azure AI Agent

שירות Azure AI Agent הוא תוספת חדשה יותר, שהוצגה בכנס Microsoft Ignite 2024. הוא מאפשר פיתוח ופריסה של סוכני AI עם מודלים גמישים יותר, כמו קריאה ישירה ל-LLM קוד פתוח כגון Llama 3, Mistral ו-Cohere.

שירות Azure AI Agent מספק מנגנוני אבטחה מתקדמים ושיטות לאחסון נתונים, מה שהופך אותו מתאים ליישומים ארגוניים.

הוא פועל מיד עם מסגרות לארכיטקטורת רב-סוכנים כמו AutoGen ו-Semantic Kernel.

שירות זה נמצא כרגע במצב תצוגה מקדימה ציבורית ותומך בפייתון ו-C# לבניית סוכנים.

באמצעות Semantic Kernel ב-Python, נוכל ליצור Azure AI Agent עם תוסף שהוגדר על-ידי המשתמש:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# הגדר תוסף לדוגמה עבור הדוגמה
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
        # צור הגדרת סוכן
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # צור את סוכן AzureAI באמצעות הלקוח והגדרת הסוכן שהוגדרו
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # צור שרשור לאחסון השיחה
        # אם לא נמסר שרשור, ייווצר שרשור חדש
        # ויאוחזר עם התגובה הראשונית
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
                # הפעל את הסוכן עבור השרשור שצוין
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

### מושגי ליבה

שירות Azure AI Agent כולל את מושגי הליבה הבאים:

- **סוכן**. שירות Azure AI Agent משתלב עם Microsoft Foundry. בתוך AI Foundry, סוכן AI פועל כמיקרו-שירות "חכם" שניתן להשתמש בו כדי לענות על שאלות (RAG), לבצע פעולות או לאוטומט תהליכים לחלוטין. הוא משיג זאת על ידי שילוב כוחם של מודלי AI גנרטיביים עם כלים שמאפשרים לו לגשת למקורות נתונים אמיתיים ולהתקשר איתם. הנה דוגמה לסוכן:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    בדוגמה זו, נוצר סוכן עם הדגם `gpt-4o-mini`, שם `my-agent`, והוראות `You are helpful agent`. הסוכן מצויד בכלים ומשאבים לביצוע משימות פירוש קוד.

- **שרשור והודעות**. השרשור הוא מושג חשוב נוסף. הוא מייצג שיחה או אינטראקציה בין סוכן למשתמש. ניתן להשתמש בשרשורים למעקב אחר התקדמות שיחה, לאחסון מידע הקשר ולניהול המצב של האינטראקציה. הנה דוגמה לשרשור:

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

    בקוד הקודם, נוצר שרשור. לאחר מכן, נשלחת הודעה לשרשור. על ידי קריאה ל-`create_and_process_run`, הסוכן מתבקש לבצע עבודה על השרשור. לבסוף, ההודעות מאוחזרות ומתועדות לצורך צפייה בתגובת הסוכן. ההודעות מציינות את התקדמות השיחה בין המשתמש לסוכן. חשוב גם להבין כי ההודעות יכולות להיות מסוגים שונים כגון טקסט, תמונה או קובץ, כלומר עבודת הסוכנים הניבה לדוגמה תמונה או תגובת טקסט. כמפתח, ניתן להשתמש במידע זה לעיבוד נוסף של התגובה או להצגתה למשתמש.

- **משתלב עם מסגרות AI אחרות**. שירות Azure AI Agent יכול לתקשר עם מסגרות אחרות כמו AutoGen ו-Semantic Kernel, מה שאומר שניתן לבנות חלק מהאפליקציה באחת מהמסגרות האלה ולמשל להשתמש בשירות ה-Agent כאורקסטרטור או לבנות הכל בשירות ה-Agent.

**מקרי שימוש**: שירות Azure AI Agent מיועד ליישומים ארגוניים שדורשים פריסה מאובטחת, מדרגית וגמישה של סוכני AI.

## מה ההבדל בין המסגרות האלה?

נשמע שיש הרבה חפיפה בין המסגרות האלה, אבל יש כמה הבדלים מרכזיים מבחינת העיצוב, היכולות ומקרי השימוש המיועדים:

- **AutoGen**: היא מסגרת ניסיונית המתמקדת במחקר מתקדם על מערכות רב-סוכנים. זו המערכת הטובה ביותר לניסוי ופרוטוטייפ של מערכות רב-סוכנים מתוחכמות.
- **Semantic Kernel**: היא ספריית סוכנים מוכנה לייצור לבניית יישומים ארגוניים סוכניים. מתמקדת ביישומים סוכניים מבוססי אירועים, מבוזרים, המאפשרים שימוש בכמה LLM ו-SLM, כלים ודפוסי עיצוב לסוכנים בודדים ורבים.
- **שירות Azure AI Agent**: היא פלטפורמה ושירות פריסה ב-Azure Foundry לסוכנים. היא מציעה חיבור לשירותים הנתמכים על ידי Azure Foundry כמו Azure OpenAI, Azure AI Search, Bing Search וביצוע קוד.

עדיין לא בטוח מה לבחור?

### מקרי שימוש

בואו נראה אם נוכל לעזור על-ידי סקירת כמה מקרי שימוש נפוצים:

> ש: אני מתנסה, לומד ובונה יישומי הוכחה למושג (POC) לסוכנים, ואני רוצה להיות מסוגל לבנות ולנסות במהירות
>

> ת: AutoGen תהיה בחירה טובה לתרחיש זה, מכיוון שהיא מתמקדת ביישומים סוכניים מבוססי אירועים ומבוזרים ותומכת בדפוסי עיצוב מתקדמים למערכות רב-סוכנים.

> ש: מה הופך את AutoGen לבחירה טובה יותר מאשר Semantic Kernel ושירות Azure AI Agent למקרה שימוש זה?
>
> ת: AutoGen מיועדת במיוחד ליישומים סוכניים מבוססי אירועים ומבוזרים, מה שהופך אותה מתאימה לאוטומציה של יצירת קוד וניתוח נתונים. היא מספקת את הכלים והיכולות הדרושים לבניית מערכות רב-סוכנים מורכבות ביעילות.

> ש: נשמע ששירות Azure AI Agent יכול להתאים כאן גם כן, יש לו כלים ליצירת קוד ועוד?
>
> ת: כן, שירות Azure AI Agent הוא שירות פלטפורמה לסוכנים ומוסיף יכולות מובנות למודלים מרובים, Azure AI Search, Bing Search ו-Azure Functions. זה מאפשר לבנות בקלות את הסוכנים שלך בפורטל Foundry ולפרוס אותם בקנה מידה.

> ש: אני עדיין מתבלבל, תן לי אפשרות אחת בלבד
>
> ת: בחירה מצוינת היא לבנות את האפליקציה שלך תחילה ב-Semantic Kernel ואז להשתמש בשירות Azure AI Agent לפרוס את הסוכן שלך. גישה זו מאפשרת לך לשמר בקלות את הסוכנים שלך תוך ניצול הכוח לבניית מערכות רב-סוכנים ב-Semantic Kernel. בנוסף, ל-Semantic Kernel יש מחבר ב-AutoGen, מה שמקל על שימוש בשתי המסגרות יחד.

נסכם את ההבדלים המרכזיים בטבלה:

| מסגרת | מיקוד | מושגי ליבה | מקרי שימוש |
| --- | --- | --- | --- |
| AutoGen | יישומים סוכניים מבוססי אירועים ומבוזרים | סוכנים, פרסונות, פונקציות, נתונים | יצירת קוד, משימות ניתוח נתונים |
| Semantic Kernel | הבנה ויצירת טקסט בדומה לאנושי | סוכנים, רכיבים מודולריים, שיתוף פעולה | הבנת שפה טבעית, יצירת תוכן |
| שירות Azure AI Agent | מודלים גמישים, אבטחה ארגונית, יצירת קוד, קריאת כלים | מודולריות, שיתוף פעולה, אורקסטרציה של תהליכים | פריסה מאובטחת, מדרגית וגמישה של סוכנים |

מהו מקרה השימוש האידיאלי לכל אחת מהמסגרות הללו?

## האם אפשר לשלב את כלי האקוסיסטם הקיימים שלי ב-Azure ישירות, או שאני צריך פתרונות עצמאיים?

התשובה היא כן, ניתן לשלב את כלי האקוסיסטם הקיימים שלך ב-Azure ישירות עם שירות Azure AI Agent, במיוחד כי הוא תוכנן לעבוד בצורה חלקה עם שירותי Azure אחרים. לדוגמה, אפשר לשלב את Bing, Azure AI Search ו-Azure Functions. יש גם אינטגרציה עמוקה עם Microsoft Foundry.

עבור AutoGen ו-Semantic Kernel, ניתן גם כן לשלב עם שירותי Azure, אבל ייתכן שתצטרך לקרוא לשירותי Azure מתוך הקוד שלך. דרך נוספת לשלב היא להשתמש ב-SDKs של Azure לאינטראקציה עם שירותי Azure מהסוכנים שלך. בנוסף, כמו שצוין, אפשר להשתמש בשירות Azure AI Agent כאורקסטרטור לסוכנים שבנית ב-AutoGen או Semantic Kernel, מה שייתן גישה קלה לאקוסיסטם של Azure.

## דוגמאות קוד

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## יש לכם עוד שאלות על מסגרות סוכני AI?

הצטרפו ל-[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) כדי להיפגש עם לומדים אחרים, להשתתף בשעות משרד ולקבל מענה על שאלות בנוגע לסוכני AI.

## מקורות

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">שירות Azure Agent</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel ו-AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">מסגרת סוכנים Semantic Kernel ב-Python</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">מסגרת סוכנים Semantic Kernel ב-.Net</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">שירות Azure AI Agent</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">שימוש בשירות Azure AI Agent עם AutoGen / Semantic Kernel לבניית פתרון רב-סוכני</a>

## שיעור קודם

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## שיעור הבא

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**כתב ויתור**:  
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לשמור על דיוק, יש להתכוון כי תרגומים אוטומטיים עלולים להכיל שגיאות או אי־דיוקים. המסמך המקורי בשפת המקור צריך להיחשב למקור המהימן והסמכותי. למידע קריטי מומלץ להיעזר בתרגום מקצועי על ידי אדם. אנו לא נושאים באחריות לכל אי הבנות או פרשנויות שגויות הנובעות משימוש בתרגום זה.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->