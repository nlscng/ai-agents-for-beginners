[![דפוס תכנון](../../../translated_images/he/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(לחץ על התמונה למעלה כדי לצפות בסרטון של השיעור)_

# תכנון

## הקדמה

בשיעור זה נסקור

* הגדרת מטרה כללית ברורה וחלוקת משימה מורכבת למשימות ניתנות לניהול.
* ניצול פלט מובנה לתגובות אמינות יותר וקריאות למכונה.
* יישום גישה מבוססת-אירועים כדי לטפל במשימות דינמיות ובקלטים בלתי צפויים.

## מטרות למידה

בסיום השיעור, יהיה לך/לך הבנה לגבי:

* לזהות ולקבוע מטרה כללית לסוכן בינה מלאכותית, ולהבטיח שהוא יודע במפורש מה יש להשיג.
* לפרק משימה מורכבת לתתי-משימות ניתנות לניהול ולארגן אותן ברצף לוגי.
* לצייד סוכנים בכלים המתאימים (למשל, כלי חיפוש או כלי ניתוח נתונים), להחליט מתי וכיצד להשתמש בהם, ולנהל מצבים בלתי צפויים שעשויים להתעורר.
* להעריך את תוצאות תתי-המשימות, למדוד ביצועים ולחזור על פעולות כדי לשפר את הפלט הסופי.

## הגדרת המטרה הכוללת וחלוקת המשימה

![הגדרת מטרות ומשימות](../../../translated_images/he/defining-goals-tasks.d70439e19e37c47a.webp)

רוב המשימות בעולם האמיתי מורכבות מדי כדי לטפל בהן בצעד אחד. סוכן בינה מלאכותית זקוק למטרה תמציתית שתנחה את התכנון והפעולות שלו. לדוגמה, שקול את המטרה:

    "צור תוכנית נסיעה ל-3 ימים."

אמנם קל לומר זאת בפשטות, אך יש צורך לדייק. ככל שהמטרה ברורה יותר, כך הסוכן (וכולל העמיתים האנושיים) יוכלו להתמקד בהשגת התוצאה הנכונה, כמו יצירת מסלול מקיף הכולל אפשרויות טיסה, המלצות על מלונות והצעות לפעילויות.

### פירוק המשימה

משימות גדולות או מורכבות נהיות ניתנות לניהול יותר כשמפרקים אותן לתת-משימות ממוקדות מטרה.
בדוגמת מסלול הטיול, ניתן לפרק את המטרה ל:

* הזמנת טיסות
* הזמנת מלון
* השכרת רכב
* התאמה אישית

כל תת-משימה יכולה להיות מטופלת על ידי סוכנים או תהליכים ייעודיים. סוכן אחד עשוי להתמחות בחיפוש דילים לטיסות, אחר יתמקד בהזמנת מלונות, וכך הלאה. סוכן מתאם או "downstream" יכול לאסוף לאחר מכן את התוצאות הללו למסלול אחד ומקיף למשתמש הסופי.

גישה מודולרית זו מאפשרת גם שיפורים הדרגתיים. לדוגמה, ניתן להוסיף סוכנים מתמחים בהמלצות אוכל או בהצעות לפעילויות מקומיות ולדייק את המסלול לאורך הזמן.

### פלט מובנה

מודלים לשוניים גדולים (LLMs) יכולים ליצור פלט מובנה (למשל JSON) שקל יותר לפרסר ולעבד על ידי סוכנים או שירותים המורכבים לאחר מכן. הדבר שימושי במיוחד בהקשר רב-סוכני, שבו ניתן לפעול על המשימות לאחר קבלת פלט התכנון. עיין ב-<a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">פוסט בבלוג</a> לתמצית מהירה.

קטע ה-Python הבא מדגים סוכן תכנון פשוט המפרק מטרה לתת-משימות ויוצר תוכנית מובנית:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# מודל תת-משימה של נסיעה
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # אנחנו רוצים להקצות את המשימה לסוכן

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # כדי לאמת מול המודל תצטרך ליצור אסימון גישה אישי (PAT) בהגדרות GitHub שלך.
    # ליצירת אסימון ה-PAT שלך עקוב אחר ההוראות כאן: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# הגדר את הודעת המשתמש
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # ודא שתוכן התגובה הוא מחרוזת JSON חוקית לפני טעינתה
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("תוכן התגובה אינו מחרוזת JSON חוקית")

# # הדפס את תוכן התגובה לאחר טעינתו כ-JSON
# pprint(json.loads(response_content))

# אמת את תוכן התגובה באמצעות המודל MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### סוכן תכנון עם תזמור רב-סוכני

בדוגמה זו, סוכן ניתוב סמנטי מקבל בקשת משתמש (למשל, "אני צריך תוכנית מלון עבור הנסיעה שלי.").

המתכנן לאחר מכן:

* מקבל את תוכנית המלון: המתכנן לוקח את הודעת המשתמש ובהתבסס על פסקת מערכת (כולל פרטי סוכנים זמינים), מייצר תוכנית נסיעה מובנית.
* מפרט סוכנים וכלים שלהם: רישום הסוכנים מכיל רשימה של סוכנים (למשל, לטיסות, מלונות, השכרת רכב ופעילויות) יחד עם הפונקציות או הכלים שהם מציעים.
* מנתב את התוכנית לסוכנים המתאימים: בהתאם למספר תתי-המשימות, המתכנן או שולח את ההודעה ישירות לסוכן ייעודי (בסצנריונים של משימה אחת) או מתאם דרך מנהל צ'אט קבוצתי לשיתוף פעולה רב-סוכני.
* מסכם את התוצאה: לבסוף, המתכנן מסכם את התוכנית שנוצרה לשם בהירות.
דוגמת הקוד של Python להלן מראה שלבים אלו:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# מודל תת-משימה לטיול

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # אנו רוצים להקצות את המשימה לסוכן

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# צור את הלקוח עם משתני סביבה שעברו בדיקת טיפוסים

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# הגדר את הודעת המשתמש

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# וודא שתוכן התשובה הוא מחרוזת JSON תקינה לפני טעינתו

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# הדפס את תוכן התשובה לאחר טעינתו כ-JSON

pprint(json.loads(response_content))
```

מה שמוצג להלן הוא הפלט מהקוד הקודם ואתה יכול להשתמש בפלט המובנה הזה כדי לנתב לפי `assigned_agent` ולסכם את תוכנית הנסיעה למשתמש הסופי.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

דוגמה למחברת עם דוגמת הקוד הקודמת זמינה [כאן](07-autogen.ipynb).

### תכנון איטרטיבי

חלק מהמשימות דורשות חילופי דברים או תכנון מחדש, כאשר תוצאת תת-משימה אחת משפיעה על הבאה. לדוגמה, אם הסוכן מגלה פורמט נתונים בלתי צפוי בעת הזמנת טיסות, יתכן שיהיה עליו להתאים את האסטרטגיה שלו לפני המעבר להזמנת מלונות.

בנוסף, משוב משתמש (למשל, החלטה אנושית שהם מעדיפים טיסה מוקדמת יותר) יכול להפעיל תכנון חוזר חלקי. גישה דינמית ואיטרטיבית זו מבטיחה שהפתרון הסופי יתיישר עם מגבלות העולם האמיתי והעדפות המשתמש המשתנות.

למשל קוד

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. כמו בקוד הקודם, והעבר את היסטוריית המשתמש ואת התוכנית הנוכחית
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. תכנן מחדש ושלח את המשימות לסוכנים המתאימים
```

לתכנון מקיף יותר עיינו ב-Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">פוסט בבלוג</a> לפתרון משימות מורכבות.

## סיכום

במאמר זה הסתכלנו על דוגמה לאופן שבו ניתן ליצור מתכנן שבאופן דינמי בוחר את הסוכנים הזמינים המוגדרים. פלט המתכנן מפרק את המשימות ומקצה את הסוכנים כדי שניתן יהיה לבצע אותן. מניחים שלסוכנים יש גישה לפונקציות/כלים הנדרשים לביצוע המשימה. בנוסף לסוכנים ניתן לכלול דפוסים נוספים כמו רפלקציה, מסכם וסיבוב-שיחה (round robin chat) להתאמה נוספת.

## משאבים נוספים

AutoGen Magentic One - מערכת רב-סוכנית כללית (A Generalist multi-agent system) לפתרון משימות מורכבות שהשיגה תוצאות מרשימות במבחנים מאתגרים שונים של סוכנים. הפנייה: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. ביישום זה המנצח יוצר תוכנית ספציפית למשימה ומפנה את המשימות הללו לסוכנים הזמינים. בנוסף לתכנון, המנצח גם משתמש במנגנון מעקב כדי לפקח על התקדמות המשימה ולבצע תכנון מחדש לפי הצורך.

### יש לך עוד שאלות לגבי דפוס התכנון?

הצטרף ל-[Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) כדי לפגוש לומדים אחרים, להשתתף בשעות קבלה ולקבל תשובות לשאלות שלך על סוכני בינה מלאכותית.

## שיעור קודם

[בניית סוכני AI אמינים](../06-building-trustworthy-agents/README.md)

## שיעור הבא

[דפוס רב-סוכני](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
הצהרת אי-אחריות:
המסמך תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש לשים לב כי תרגומים אוטומטיים עלולים להכיל שגיאות או אי־דיוקים. על המסמך המקורי בשפתו המקורית להיחשב כמקור הסמכות. עבור מידע קריטי מומלץ להסתייע בתרגום מקצועי על ידי מתרגם אנושי. איננו אחראים לכל אי־הבנה או פרשנות שגויה הנובעת מהשימוש בתרגום זה.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->