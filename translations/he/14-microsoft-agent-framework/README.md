# חקר Microsoft Agent Framework

![מסגרת הסוכנים](../../../translated_images/he/lesson-14-thumbnail.90df0065b9d234ee.webp)

### הקדמה

השיעור הזה יעסוק ב:

- הבנת Microsoft Agent Framework: מאפיינים מרכזיים וערך  
- חקירת המושגים המרכזיים של Microsoft Agent Framework
- השוואת MAF ל‑Semantic Kernel ו‑AutoGen: מדריך הגירה

## מטרות למידה

בסיום שיעור זה תדעו כיצד:

- לבנות סוכני בינה מלאכותית מוכנים לפרודקשן באמצעות Microsoft Agent Framework
- להחיל את התכונות המרכזיות של Microsoft Agent Framework על מקרי השימוש הסוכניים שלכם
- להגר ולשלב מסגרות וכלים סוכניים קיימים  

## דוגמאות קוד 

דוגמאות קוד עבור [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) נמצאות במאגר זה תחת הקבצים `xx-python-agent-framework` ו־`xx-dotnet-agent-framework`.

## הבנת Microsoft Agent Framework

![מבוא למסגרת](../../../translated_images/he/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) מתבססת על הניסיון והלמידה מ‑Semantic Kernel ו‑AutoGen. היא מציעה גמישות להתמודד עם מגוון רחב של מקרי שימוש סוכניים הנצפים הן בסביבות פרודקשן והן במחקר, כולל:

- **תזמור סוכנים סדרתי** בתרחישים בהם נדרשים זרמי עבודה שלב אחר שלב.
- **תזמור מקבילי** בתרחישים שבהם סוכנים צריכים להשלים משימות בו־זמנית.
- **תזמור שיחת קבוצה** בתרחישים שבהם סוכנים יכולים לשתף פעולה יחד על משימה אחת.
- **תזמור העברת משימות (Handoff Orchestration)** בתרחישים שבהם סוכנים מעבירים זה לזה את המשימה כאשר תתי־המשימות הושלמו.
- **תזמור מגנטי** בתרחישים שבהם סוכן מנהל יוצר ומעדכן רשימת משימות ומטפל בתיאום בין תת‑הסוכנים להשלמת המשימה.

כדי לספק סוכני AI בפרודקשן, MAF כוללת גם תכונות עבור:

- **תצפית (Observability)** באמצעות שימוש ב‑OpenTelemetry, כאשר כל פעולה של סוכן ה‑AI כולל קריאת כלים, שלבי תזמור, תהליכי נימוק ומעקב ביצועים דרך לוחות הבקרה של Microsoft Foundry.
- **אבטחה** על ידי אירוח סוכנים באופן נייטיב ב‑Microsoft Foundry, הכולל בקרות אבטחה כגון גישה מבוססת תפקידים, טיפול בנתונים פרטיים ובטיחות תוכן מובנית.
- **עמידות** מכיוון ששרשורי סוכנים (Agent threads) וזרמי עבודה יכולים להשהות, להמשיך ולהתאושש מטעויות, מה שמאפשר תהליכים ארוכי‑טווח.
- **שליטה** שכן נתמכות זרימות עבודה עם אדם בלולאה, שבהן משימות מסומנות כדרושות אישור אנושי.

Microsoft Agent Framework גם מתמקדת ביכולת אינטרופרביליות על‑ידי:

- **א‑תלותית בענן (Being Cloud-agnostic)** - סוכנים יכולים לפעול במכולות, באופן מקומי (on‑prem) ועל פני עננים שונים.
- **א‑תלותית בספק (Being Provider-agnostic)** - ניתן ליצור סוכנים דרך ה‑SDK המועדף עליכם כולל Azure OpenAI ו‑OpenAI
- **שילוב סטנדרטים פתוחים** - סוכנים יכולים להשתמש בפרוטוקולים כגון Agent-to-Agent (A2A) ו‑Model Context Protocol (MCP) כדי לגלות ולהשתמש בסוכנים וכלים אחרים.
- **תוספים ומחברים** - ניתן לבצע חיבורים לשירותי נתונים וזיכרון כגון Microsoft Fabric, SharePoint, Pinecone ו‑Qdrant.

בואו נסתכל כיצד תכונות אלה מיושמות על חלק מהמושגים המרכזיים של Microsoft Agent Framework.

## המושגים המרכזיים של Microsoft Agent Framework

### סוכנים

![מסגרת הסוכנים](../../../translated_images/he/agent-components.410a06daf87b4fef.webp)

**יצירת סוכנים**

יצירת סוכן מתבצעת על ידי הגדרת שירות המסקנה (LLM Provider), קבוצת הוראות שעל סוכן ה‑AI לפעול לפיהן, ושם מוקצה `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

לעיל משתמשים ב־`Azure OpenAI` אך ניתן ליצור סוכנים באמצעות מגוון שירותים כולל `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

או סוכנים מרוחקים המשתמשים בפרוטוקול A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**הרצת סוכנים**

מפעילים סוכנים באמצעות המתודות .run או .run_stream לקבלת תגובות לא־סטרימינג או סטרימינג בהתאמה.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

לכל הרצת סוכן יכולים להיות גם אפשרויות להתאמת פרמטרים כגון `max_tokens` שבהם הסוכן משתמש, `tools` שהסוכן יכול לקרוא, ואפילו ה־`model` עצמו שבו משתמש הסוכן.

זה שימושי במקרים שבהם נדרשים מודלים או כלים ספציפיים להשלמת משימת המשתמש.

**כלים**

כלים ניתנים להגדרה הן בעת הגדרת הסוכן:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# בעת יצירת סוכן שיחה באופן ישיר

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

וגם בעת הרצת הסוכן:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # הכלי מסופק רק להרצה זו )
```

**שרשורי סוכן**

שרשורי סוכן משמשים לטיפול בשיחות מרובות סבבים. ניתן ליצור שרשורים באופן הבא:

- שימוש ב־`get_new_thread()` שמאפשר לשמור את השרשור לאורך זמן
- יצירת שרשור באופן אוטומטי בעת הרצת סוכן והגבלת השרשור לתקופת הריצה הנוכחית בלבד.

ליצירת שרשור, הקוד נראה כך:

```python
# צור שרשור חדש.
thread = agent.get_new_thread() # הפעל את הסוכן עם השרשור.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

ניתן לאחר מכן לסריאליז את השרשור כדי לאחסן אותו לשימוש מאוחר יותר:

```python
# צור שרשור חדש.
thread = agent.get_new_thread() 

# הרץ את הסוכן עם השרשור.

response = await agent.run("Hello, how are you?", thread=thread) 

# בצע סיריאליזציה של השרשור לאחסון.

serialized_thread = await thread.serialize() 

# שחזר את מצב השרשור לאחר טעינה מהאחסון.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**מתווך סוכן (Agent Middleware)**

סוכנים מתקשרים עם כלים ו‑LLMs כדי להשלים משימות של משתמשים. בתרחישים מסוימים אנו רוצים לבצע או לעקוב אחרי פעולות בין האינטראקציות הללו. מתווך הסוכן מאפשר לנו לעשות זאת באמצעות:

*מתווך פונקציה*

מתווך זה מאפשר לנו לבצע פעולה בין הסוכן לבין פונקציה/כלי שהוא יפעיל. דוגמה לשימוש תהיה אם נרצה לבצע רישום (logging) על קריאת הפונקציה.

בקוד שלמטה `next` מגדיר אם יש לקרוא למתווך הבא או לפונקציה עצמה.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # עיבוד מקדים: רישום לפני ביצוע הפונקציה
    print(f"[Function] Calling {context.function.name}")

    # המשך לשכבת התיווך הבאה או לביצוע הפונקציה
    await next(context)

    # עיבוד לאחר מעשה: רישום לאחר ביצוע הפונקציה
    print(f"[Function] {context.function.name} completed")
```

*מתווך שיחה*

מתווך זה מאפשר לנו לבצע או לרשום פעולה בין הסוכן לבין הבקשות המועברות ל‑LLM.

זה מכיל מידע חשוב כגון ה־`messages` שנשלחים לשירות ה‑AI.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # עיבוד מקדים: רישום לפני קריאה לבינה מלאכותית
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # המשך לשכבת התווך הבאה או לשירות בינה מלאכותית
    await next(context)

    # עיבוד לאחר מכן: רישום לאחר תגובת בינה מלאכותית
    print("[Chat] AI response received")

```

**זיכרון סוכן**

כפי שנדון בשיעור `Agentic Memory`, הזיכרון הוא מרכיב חשוב המאפשר לסוכן לפעול בהקשרים שונים. ל‑MAF יש מספר סוגי זיכרונות שונים:

*אחסון בזיכרון פנימי*

זהו הזיכרון השמור בשרשורים במהלך זמן ריצה של היישום.

```python
# צור חוט חדש.
thread = agent.get_new_thread() # הרץ את הסוכן עם החוט.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*הודעות מתמשכות*

זיכרון זה משמש לאחסון היסטוריית שיחות על פני סשנים שונים. הוא מוגדר באמצעות ה־`chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# צור מאגר הודעות מותאם
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*זיכרון דינמי*

זיכרון זה נוסף להקשר לפני הרצת הסוכנים. זיכרונות אלה יכולים להיות מאוחסנים בשירותים חיצוניים כגון mem0:

```python
from agent_framework.mem0 import Mem0Provider

# שימוש ב-Mem0 עבור יכולות זיכרון מתקדמות
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**תצפית של הסוכן**

תצפית חשובה לבניית מערכות סוכניות אמינות וניתנות לתחזוקה. ל‑MAF יש אינטגרציה עם OpenTelemetry לספק מעקב (tracing) ומדדים לשיפור התצפית.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # עשה משהו
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### זרמי עבודה

MAF מציעה זרמי עבודה שהם שלבים מוגדרים מראש להשלמת משימה וכוללים סוכני AI כרכיבים באותם שלבים.

זרמי עבודה מורכבים מרכיבים שונים שמאפשרים שליטה טובה יותר בזרימה. זרמי העבודה גם מאפשרים **תזמור רב‑סוכני** ו־**checkpointing** לשמירת מצבי זרימת עבודה.

הרכיבים המרכזיים של זרם עבודה הם:

**מבצעים (Executors)**

המבצעים מקבלים הודעות קלט, מבצעים את המשימות שהוקצבו להם, ולאחר מכן מייצרים הודעת פלט. זה מזיז את זרם העבודה קדימה לקראת השלמת המשימה הכוללת. מבצעים יכולים להיות סוכן AI או לוגיקה מותאמת.

**קצוות (Edges)**

הקצוות משמשים להגדרת זרימת ההודעות בזרם העבודה. אלה יכולים להיות:

*קצוות ישירים (Direct Edges)* - חיבורים פשוטים אחד‑לאחד בין מבצעים:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*קצוות מותנה (Conditional Edges)* - מופעלים לאחר שמתקיים תנאי מסוים. לדוגמה, כאשר חדרי מלון אינם זמינים, מבצע יכול להציע אפשרויות אחרות.

*קצוות של switch-case* - מנתבים הודעות למבצעים שונים על בסיס תנאים מוגדרים. לדוגמה, אם ללקוח נסיעות יש גישה בעדיפות והמשימות שלו יטופלו דרך זרם עבודה אחר.

*קצוות fan-out* - שולחים הודעה אחת למספר יעדים.

*קצוות fan-in* - אוספים מספר הודעות ממבצעים שונים ושולחים ליעד אחד.

**אירועים**

כדי לספק תצפית טובה יותר על זרמי עבודה, ל‑MAF יש אירועים מובנים עבור ביצוע, כולל:

- `WorkflowStartedEvent`  - ביצוע זרימת העבודה מתחיל
- `WorkflowOutputEvent` - זרם העבודה מייצר פלט
- `WorkflowErrorEvent` - זרם העבודה נתקל בשגיאה
- `ExecutorInvokeEvent`  - מבצע מתחיל לעבד
- `ExecutorCompleteEvent`  -  מבצע מסיים עיבוד
- `RequestInfoEvent` - נשלחה בקשה

## הגירה ממסגרות אחרות (Semantic Kernel ו‑AutoGen)

### הבדלים בין MAF ל‑Semantic Kernel

**יצירת סוכן מפושטת**

Semantic Kernel נסמך על יצירת מופע Kernel עבור כל סוכן. ל‑MAF יש גישה מפושטת שמשתמשת בהרחבות עבור הספקים הראשיים.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**יצירת שרשור סוכן**

Semantic Kernel דורש יצירת שרשורים באופן ידני. ב‑MAF, השרשור מוקצה ישירות לסוכן.

```python
thread = agent.get_new_thread() # הפעל את הסוכן באמצעות חוט ביצוע.
```

**רישום כלים**

ב‑Semantic Kernel, כלים נרשמים ל‑Kernel ואז ה‑Kernel מועבר לסוכן. ב‑MAF הכלים נרשמים ישירות במהלך תהליך יצירת הסוכן.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### הבדלים בין MAF ו‑AutoGen

**Teams מול Workflows**

`Teams` הן מבנה האירועים לפעילות מונעת אירועים עם סוכנים ב‑AutoGen. ל‑MAF יש `Workflows` שמנתבים נתונים למבצעים באמצעות ארכיטקטורת גרף.

**יצירת כלים**

AutoGen משתמש ב־`FunctionTool` לעטיפת פונקציות שהסוכנים יקראו. ב‑MAF משתמשים ב‑@ai_function שפועל באופן דומה אך גם גוזר את הסכימות אוטומטית לכל פונקציה.

**התנהגות סוכן**

ב‑AutoGen סוכנים הם חד‑סיבוביים כברירת מחדל אלא אם `max_tool_iterations` מוגדר לערך גבוה יותר. במסגרת MAF ה־`ChatAgent` רב‑סיבובי כברירת מחדל, כלומר הוא ימשיך לקרוא לכלים עד שמשימת המשתמש הושלמה.

## דוגמאות קוד 

דוגמאות קוד עבור Microsoft Agent Framework נמצאות במאגר זה תחת הקבצים `xx-python-agent-framework` ו־`xx-dotnet-agent-framework`.

## יש לכם עוד שאלות על Microsoft Agent Framework?

הצטרפו ל‑[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) כדי לפגוש לומדים אחרים, להשתתף בשעות ייעוץ (office hours) ולקבל תשובות לשאלות שלכם בנוגע לסוכני ה‑AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
כתב ויתור:
מסמך זה תורגם בעזרת שירות תרגום מבוסס בינה מלאכותית (Co-op Translator) https://github.com/Azure/co-op-translator. אמנם אנו שואפים לדייק, אך יש לדעת כי תרגומים אוטומטיים עלולים להכיל שגיאות או אי-דיוקים. יש להתייחס למסמך המקורי בשפתו כמקור הסמכות. לצורך מידע קריטי מומלץ להשתמש בתרגום מקצועי שנערך על ידי מתרגם אנושי. איננו אחראים לכל אי-הבנה או פרשנות שגויה הנובעים משימוש בתרגום זה.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->