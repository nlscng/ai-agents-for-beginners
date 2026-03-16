[![כיצד לעצב סוכני בינה מלאכותית טובים](../../../translated_images/he/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(לחץ על התמונה למעלה לצפייה בווידאו של השיעור)_

# תבנית עיצוב לשימוש בכלים

כלים מעניינים כי הם מאפשרים לסוכני בינה מלאכותית יכולות רחבות יותר. במקום שהסוכן יוכל לבצע רק סט מוגבל של פעולות, על ידי הוספת כלי, הסוכן יכול כעת לבצע מגוון רחב של פעולות. בפרק זה נבחן את תבנית העיצוב לשימוש בכלים, המתארת כיצד סוכני בינה מלאכותית יכולים להשתמש בכלים ספציפיים כדי להשיג את מטרותיהם.

## מבוא

בשיעור זה ננסה לענות על השאלות הבאות:

- מהי תבנית העיצוב לשימוש בכלים?
- באילו מקרי שימוש ניתן להחיל אותה?
- מהן האבני בניין/הרכיבים הנדרשים ליישום תבנית העיצוב?
- אילו שיקולים מיוחדים קיימים בעת השימוש בתבנית העיצוב לשימוש בכלים על מנת לבנות סוכני בינה אמינים?

## מטרות למידה

לאחר השלמת שיעור זה, תוכל/י:

- להגדיר את תבנית העיצוב לשימוש בכלים ומטרתה.
- לזהות מקרי שימוש שבהם תבנית העיצוב לשימוש בכלים מתקיימת.
- להבין את המרכיבים המרכזיים הנדרשים ליישום תבנית העיצוב.
- לזהות שיקולים להבטחת אמינות בסוכני בינה שמשתמשים בתבנית עיצוב זו.

## מהי תבנית העיצוב לשימוש בכלים?

תבנית העיצוב לשימוש בכלים מתמקדת במתן היכולת למודלים לשפה גדולים (LLMs) באינטראקציה עם כלים חיצוניים כדי להשיג מטרות ספציפיות. כלים הם קוד שניתן להפעיל על ידי סוכן כדי לבצע פעולות. כלי יכול להיות פונקציה פשוטה כגון מחשבון, או קריאת API לשירות צד שלישי כמו בדיקת מחירי מניות או תחזית מזג אוויר. בהקשר של סוכני בינה מלאכותית, כלים מתוכננים כך שיהיו ניתנים להפעלה על ידי סוכנים בתגובה ל-**קריאות לפונקציות שנוצרו על ידי המודל**.

## באילו מקרים ניתן להחיל אותה?

סוכני בינה מלאכותית יכולים להיעזר בכלים כדי להשלים משימות מורכבות, לשלוף מידע או לקבל החלטות. תבנית העיצוב לשימוש בכלים משמשת לעיתים קרובות בתרחישים הדורשים אינטראקציה דינמית עם מערכות חיצוניות, כגון מאגרי נתונים, שירותי אינטרנט או מפרשי קוד. יכולת זו שימושית למגוון רחב של מקרי שימוש כולל:

- **שליפת מידע דינמית:** סוכנים יכולים לשאול APIs חיצוניים או מאגרי נתונים כדי לקבל נתונים מעודכנים (למשל, שאילתא למסד נתונים SQLite לניתוח נתונים, שליפת מחירי מניות או מידע על מזג אוויר).
- **הרצת קוד ופרשנות:** סוכנים יכולים להריץ קוד או סקריפטים כדי לפתור בעיות מתמטיות, ליצור דוחות או לבצע סימולציות.
- **אוטומציה של תהליכי עבודה:** אוטומציה של משימות חזרתיות או רב-שלביות על ידי אינטגרציה של כלים כמו מתזמני משימות, שירותי דוא״ל או צינורות נתונים.
- **שירות לקוחות:** סוכנים יכולים לאינטראקציה עם מערכות CRM, פלטפורמות כרטיסי תמיכה או מאגרי ידע כדי לפתור פניות משתמשים.
- **יצירה ועריכת תוכן:** סוכנים יכולים להיעזר בכלים כמו בודקי דקדוק, מסכמי טקסט או מעריכי בטיחות תוכן כדי לסייע במשימות יצירת תוכן.

## מהם המרכיבים/אבני הבניין הנדרשים ליישום תבנית העיצוב לשימוש בכלים?

אבני בניין אלה מאפשרות לסוכן הבינה המלאכותית לבצע מגוון רחב של מטלות. נבחן את המרכיבים המרכזיים הנדרשים ליישום תבנית העיצוב לשימוש בכלים:

- **סכימות פונקציה/כלי**: הגדרות מפורטות של הכלים הזמינים, כולל שם הפונקציה, המטרה, הפרמטרים הנדרשים והתוצרים הצפויים. סכימות אלה מאפשרות ל-LLM להבין אילו כלים זמינים וכיצד לבנות בקשות תקפות.

- **לוגיקת הרצת פונקציות**: מגדירה כיצד ומתי כלים מופעלים בהתבסס על כוונת המשתמש והקשר השיחה. זה יכול לכלול מודולי תכנון, מנגנוני ניתוב או זרימות מותנות שקובעות שימוש בכלים בצורה דינמית.

- **מערכת ניהול הודעות**: רכיבים שמנהלים את הזרימה השיחתית בין קלטי משתמש, תגובות LLM, קריאות לכלים ותשומות כלי.

- **מסגרת אינטגרציה לכלים**: תשתית שמחברת את הסוכן לכלים שונים, בין אם הם פונקציות פשוטות או שירותים חיצוניים מורכבים.

- **טיפול בשגיאות ואימות**: מנגנונים לטיפול בכשלונות בהרצת כלים, אימות פרמטרים וניהול תגובות בלתי צפויות.

- **ניהול מצב**: מעקב אחר הקשר השיחה, אינטראקציות קודמות עם כלים ונתונים מתמשכים כדי להבטיח עקביות לאורך אינטראקציות מרובות-סבבים.

Next, let's look at Function/Tool Calling in more detail.
 
### קריאה לפונקציות/כלים

קריאה לפונקציות היא הדרך העיקרית שאנו מאפשרים למודלים לשפה גדולים (LLMs) באינטראקציה עם כלים. לעיתים תראו את המונחים 'Function' ו-'Tool' משמשים לסירוגין כיוון ש'functions' (בלוקים של קוד שניתן לשימוש חוזר) הם ה'כלים' שסוכנים משתמשים בהם לביצוע משימות. כדי שקוד של פונקציה ייקרא, על ה-LLM להשוות את בקשת המשתמש לתיאור הפונקציות. לשם כך נשלחת למודל סכימה המכילה את תיאורי כל הפונקציות הזמינות. ה-LLM בוחר אז את הפונקציה המתאימה ביותר למשימה ומחזיר את שמה והארגומנטים שלה. הפונקציה שנבחרה מופעלת, התגובה שלה נשלחת חזרה ל-LLM, וה-LLM משתמש במידע כדי להגיב לבקשת המשתמש.

למפתחי תוכנה שמעוניינים ליישם קריאת פונקציות עבור סוכנים, תצטרכו:

1. An LLM model that supports function calling
2. A schema containing function descriptions
3. The code for each function described

נשתמש בדוגמה של קבלת הזמן הנוכחי בעיר כדי להמחיש:

1. **Initialize an LLM that supports function calling:**

    לא כל המודלים תומכים בקריאת פונקציות, לכן חשוב לבדוק שה-LLM שבו אתם משתמשים אכן תומך בכך.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> תומך בקריאת פונקציות. נוכל להתחיל על ידי יזום לקוח ה-Azure OpenAI. 

    ```python
    # אתחל את לקוח ה-Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Create a Function Schema**:

    לאחר מכן נגדיר סכימת JSON שמכילה את שם הפונקציה, תיאור מה שהפונקציה עושה, ושמות ותיאורים של פרמטרי הפונקציה.
    לאחר מכן נעביר סכימה זו אל הלקוח שנוצר קודם, יחד עם בקשת המשתמש למצוא את השעה בסן פרנסיסקו. מה שחשוב לציין הוא שהחזרת המודל תהיה **קריאת כלי**, **ולא** התשובה הסופית לשאלה. כפי שצויין לעיל, ה-LLM מחזיר את שם הפונקציה שהוא בחר למשימה ואת הארגומנטים שיועברו אליה.

    ```python
    # תיאור הפונקציה לקריאה על-ידי המודל
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
  
    # הודעת המשתמש ההתחלתית
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # קריאת ה-API הראשונה: בקש מהמודל להשתמש בפונקציה
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # עיבוד תגובת המודל
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **The function code required to carry out the task:**

    כעת שה-LLM בחר איזו פונקציה יש להריץ, יש לממש ולהריץ את הקוד שמבצע את המשימה.
    נוכל לממש את הקוד לקבלת השעה הנוכחית ב-Python. נצטרך גם לכתוב את הקוד לחילוץ השם והארגומנטים מתוך ה-response_message כדי לקבל את התוצאה הסופית.

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
     # טפל בקריאות לפונקציות
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
  
      # קריאה שנייה ל-API: קבל את התשובה הסופית מהמודל
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

Function Calling נמצא בלב רוב, אם לא כל, עיצוב השימוש בכלים עבור סוכנים, אך מימושו מאפס עלול להיות מאתגר לפעמים.
כפי שלמדנו ב-[שיעור 2](../../../02-explore-agentic-frameworks) מסגרות סוכנים (agentic frameworks) מספקות לנו אבני בניין מוכנות ליישום שימוש בכלים.
 
## דוגמאות לשימוש בכלים עם מסגרות סוכנים

להלן כמה דוגמאות לאופן שבו ניתן ליישם את תבנית העיצוב לשימוש בכלים באמצעות מסגרות סוכנים שונות:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> היא מסגרת AI קוד פתוח למפתחי .NET, Python ו-Java שעובדים עם מודלים לשפה גדולים (LLMs). היא מפשטת את תהליך השימוש בקריאת פונקציות על ידי תיאור אוטומטי של הפונקציות והפרמטרים שלהן למודל בתהליך שנקרא <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">סיריאליזציה</a>. היא גם מטפלת בתקשורת הלוך ושוב בין המודל לבין הקוד שלכם. יתרון נוסף בשימוש במסגרת סוכנים כמו Semantic Kernel הוא שהיא מאפשרת לכם גישה לכלים מוכנים מראש כמו <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">חיפוש קבצים</a> ו-<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">מפרש קוד</a>.

התמונה הבאה ממחישה את תהליך קריאת הפונקציות עם Semantic Kernel:

![קריאה לפונקציות](../../../translated_images/he/functioncalling-diagram.a84006fc287f6014.webp)

ב-Semantic Kernel פונקציות/כלים נקראים <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">תוספים</a>. נוכל להפוך את הפונקציה `get_current_time` שראינו קודם לתוסף על ידי הפיכתה למחלקה שמכילה את הפונקציה. כמו כן נוכל לייבא את הדקורטור `kernel_function`, שמקבל בתוכו את תיאור הפונקציה. כאשר תייצרו kernel עם ה-GetCurrentTimePlugin, ה-kernel יסיראילז את הפונקציה ואת הפרמטרים שלה בצורה אוטומטית, וייצור את הסכימה שתישלח ל-LLM בתהליך.

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

# צור את הליבה
kernel = Kernel()

# צור את התוסף
get_current_time_plugin = GetCurrentTimePlugin(location)

# הוסף את התוסף לליבה
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> היא מסגרת סוכנים חדשה שנועדה להעצים מפתחים לבנות, לפרוס ולמתג סוכני AI איכותיים, ניתנים להרחבה ובטוחים ללא צורך לניהול המשאבים הבסיסיים של חישוב ואחסון. היא שימושית במיוחד ליישומי ארגון מכיוון שהיא שירות מנוהל לחלוטין עם אבטחת ארגונית ברמה גבוהה.

בהשוואה לפיתוח ישיר דרך ממשק ה-LLM, Azure AI Agent Service מספקת כמה יתרונות, לרבות:

- קריאת כלים אוטומטית – אין צורך לנתח קריאת כלי, להפעיל את הכלי ולטפל בתשומה; כל אלה מטופלים כעת בצד השרת
- ניהול נתונים מאובטח – במקום לנהל את מצב השיחה בעצמכם, ניתן להסתמך על threads לאחסון כל המידע הנדרש
- כלים מוכנים לשימוש – כלים שניתן להשתמש בהם כדי לאינטראקציה עם מקורות הנתונים שלכם, כגון Bing, Azure AI Search ו-Azure Functions.

הכלים הזמינים ב-Azure AI Agent Service ניתנים לחלוקה לשתי קטגוריות:

1. כלים לידע:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">עיגון באמצעות חיפוש Bing</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">חיפוש קבצים</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. כלים לפעולה:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">קריאת פונקציות</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">מפרש קוד</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">כלים המוגדרים באמצעות OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

שירות הסוכנים מאפשר לנו להשתמש בכלים אלה יחד כ-`toolset`. הוא גם משתמש ב-`threads` שעוקבים אחרי היסטוריית ההודעות משיחה מסוימת.

דמיינו שאתם סוכן מכירות בחברה בשם Contoso. אתם רוצים לפתח סוכן שיח שיכול לענות על שאלות לגבי נתוני המכירות שלכם.

התמונה הבאה ממחישה כיצד ניתן להשתמש ב-Azure AI Agent Service לניתוח נתוני המכירות:

![שירות סוכני בפעולה](../../../translated_images/he/agent-service-in-action.34fb465c9a84659e.webp)

כדי להשתמש בכלים אלה עם השירות, נוכל ליצור לקוח ולהגדיר כלי או toolset. ליישום פרקטי נוכל להשתמש בקוד ה-Python הבא. ה-LLM יוכל לבחון את ה-toolset ולקבוע האם להשתמש בפונקציה שיצר המשתמש, `fetch_sales_data_using_sqlite_query`, או במפרש הקוד המוכן תלוי בבקשת המשתמש.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # הפונקציה fetch_sales_data_using_sqlite_query שנמצאת בקובץ fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# אתחול ערכת הכלים
toolset = ToolSet()

# אתחול סוכן הקריאה לפונקציות עם הפונקציה fetch_sales_data_using_sqlite_query והוספתו לערכת הכלים
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# אתחול כלי מפרש הקוד והוספתו לערכת הכלים.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## אילו שיקולים מיוחדים קיימים בעת שימוש בתבנית העיצוב לשימוש בכלים על מנת לבנות סוכני בינה אמינים?

חשש נפוץ עם SQL שנוצר דינמית על ידי LLMs הוא אבטחה, בפרט הסיכון של הזרקת SQL או פעולות זדוניות, כגון מחיקה או פגיעה במסד הנתונים. בעוד שחששות אלה תקפים, ניתן להקטין אותם באופן יעיל על ידי קביעת הרשאות גישה למסד הנתונים בצורה נכונה. עבור רוב מסדי הנתונים זה כולל קביעת הגישה כקריאה בלבד. עבור שירותי מסדי נתונים כמו PostgreSQL או Azure SQL, יש להקצות לאפליקציה תפקיד לקריאה בלבד (SELECT).

הרצת האפליקציה בסביבה מאובטחת מחזקת עוד יותר את ההגנה. בתרחישי ארגון, בדרך כלל מחלץ ומעבד נתונים ממערכות תפעוליות אל מסד נתונים לקריאה בלבד או למחסן נתונים (data warehouse) עם סכמה ידידותית למשתמש. גישה זו מבטיחה שהנתונים מאובטחים, מותאמים לביצועים ונגישים, וכי לאפליקציה יש גישה מוגבלת לקריאה בלבד.

## דוגמאות קוד
- Python: [מסגרת סוכנים](./code_samples/04-python-agent-framework.ipynb)
- .NET: [מסגרת סוכנים](./code_samples/04-dotnet-agent-framework.md)

## יש לכם עוד שאלות לגבי דפוסי העיצוב לשימוש בכלים?

הצטרפו ל-[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) כדי לפגוש לומדים אחרים, להשתתף בשעות קבלה ולקבל תשובות לשאלות שלכם על סוכני ה-AI.

## משאבים נוספים

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">סדנה ל-Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">סדנת רב-סוכנים של Contoso Creative Writer</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">מדריך לקריאה לפונקציות ב-Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">מפרש קוד של Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">כלי Autogen</a>

## השיעור הקודם

[הבנת דפוסי עיצוב סוכניים](../03-agentic-design-patterns/README.md)

## השיעור הבא

[RAG סוכני](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
הצהרת אי-אחריות:

מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש להביא בחשבון כי תרגומים אוטומטיים עלולים להכיל שגיאות או אי-דיוקים. יש להחשיב את המסמך המקורי בשפת המקור כמקור הסמכות. עבור מידע קריטי, מומלץ להיעזר בתרגום מקצועי שבוצע על ידי מתרגם אנושי. איננו נושאים באחריות עבור אי-הבנות או פרשנויות שגויות הנובעות משימוש בתרגום זה.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->