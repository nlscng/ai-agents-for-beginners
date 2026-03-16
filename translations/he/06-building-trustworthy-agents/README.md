[![סוכני בינה מלאכותית אמינים](../../../translated_images/he/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(לחצו על התמונה למעלה כדי לצפות בסרטון של השיעור הזה)_

# בניית סוכני בינה מלאכותית אמינים

## מבוא

בשיעור זה יוסברו:

- כיצד לבנות ולפרוס סוכני בינה מלאכותית בטוחים ויעילים
- שיקולי אבטחה חשובים בעת פיתוח סוכני בינה מלאכותית.
- כיצד לשמור על פרטיות המידע והמשתמש בעת פיתוח סוכני בינה מלאכותית.

## מטרות הלמידה

בסיום שיעור זה, תדעו כיצד:

- לזהות ולהפחית סיכונים בעת יצירת סוכני בינה מלאכותית.
- ליישם אמצעי אבטחה כדי להבטיח שהנתונים והגישה מנוהלים כראוי.
- ליצור סוכני בינה מלאכותית ששומרים על פרטיות הנתונים ומספקים חוויית משתמש איכותית.

## בטיחות

נתחיל בבחינה של בניית יישומים סוכניים בטוחים. בטיחות משמעותה שהסוכן מבצע את פעילותו כפי שתוכנן. כבוני יישומים סוכניים, יש לנו שיטות וכלים למקסם את הבטיחות:

### בניית מסגרת הודעת מערכת

אם יצרתם אי פעם יישום בינה מלאכותית המשתמש במודלי שפה גדולים (LLMs), אתם מבינים את החשיבות של עיצוב הנחיית מערכת או הודעת מערכת חזקה. הוראות אלה קובעות את הכללים המטא, ההנחיות וההוראות לאופן שבו ה-LLM יתקשר עם המשתמש והנתונים.

עבור סוכני בינה מלאכותית, הנחיית המערכת חשובה אף יותר, שכן הסוכנים יזדקקו להוראות מאוד מפורטות כדי להשלים את המשימות שעיצבנו עבורם.

כדי ליצור הנחיות מערכת הניתנות להרחבה, נוכל להשתמש במסגרת הודעת מערכת לבניית סוכן אחד או יותר ביישום שלנו:

![בניית מסגרת הודעת מערכת](../../../translated_images/he/system-message-framework.3a97368c92d11d68.webp)

#### שלב 1: צור הודעת מערכת מטא 

ה-meta prompt ישמש את ה-LLM ליצירת הנחיות מערכת עבור הסוכנים שניצור. אנו מעצבים אותו כתבנית כדי שנוכל ליצור ביעילות מספר סוכנים לפי הצורך.

הנה דוגמה להודעת מערכת מטא שניתן לתת ל-LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### שלב 2: צור הנחיה בסיסית

השלב הבא הוא ליצור הנחיה בסיסית לתיאור הסוכן. יש לכלול את תפקיד הסוכן, המשימות שהסוכן יבצע וכל אחריות נוספת של הסוכן.

הנה דוגמה:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### שלב 3: ספק הודעת מערכת בסיסית ל-LLM

כעת נוכל לשפר את הודעת המערכת הזו על ידי שימוש בהודעת המערכת המטא יחד עם הודעת המערכת הבסיסית שלנו.

זה יפיק הודעת מערכת שתוכננה טוב יותר להנחיית סוכני הבינה המלאכותית שלנו:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### שלב 4: חזור ושפר

הערך של מסגרת הודעות המערכת הזו הוא היכולת להרחיב את יצירת הודעות מערכת עבור מספר סוכנים בצורה קלה יותר, וכן לשפר את הודעות המערכת שלך לאורך זמן. נדיר שיהיה לך הודעת מערכת שעובדת מהפעם הראשונה עבור כל מקרה השימוש שלך. היכולת לבצע התאמות ושיפורים קטנים על ידי שינוי הודעת המערכת הבסיסית והפעלתה דרך המערכת תאפשר לך להשוות ולהעריך תוצאות.

## הבנת איומים

כדי לבנות סוכני בינה מלאכותית אמינים, חשוב להבין ולהפחית את הסיכונים והאיומים כלפי הסוכן. נבחן כאן רק חלק מהאיומים השונים כלפי סוכנים וכיצד ניתן לתכנן ולהתכונן אליהם בצורה טובה יותר.

![הבנת איומים](../../../translated_images/he/understanding-threats.89edeada8a97fc0f.webp)

### משימה והנחיה

**תיאור:** תוקפים מנסים לשנות את ההנחיות או את המטרות של הסוכן באמצעות פרומפטים או מניפולציה של קלטים.

**הפחתה**: בצע בדיקות אימות ומסנני קלט כדי לזהות פרומפטים שעלולים להיות מסוכנים לפני שיועברו לעיבוד על ידי הסוכן. מכיוון שתקיפות אלו בדרך כלל דורשות אינטראקציה תכופה עם הסוכן, הגבלת מספר ההחלפות בשיחה היא דרך נוספת למנוע סוגי תקיפות אלה.

### גישה למערכות קריטיות

**תיאור**: אם לסוכן יש גישה למערכות ושירותים המאחסנים נתונים רגישים, תוקפים יכולים לפגוע בתקשורת בין הסוכן לשירותים אלה. אלו עשויות להיות תקיפות ישירות או ניסיונות עקיפים להשיג מידע אודות מערכות אלו באמצעות הסוכן.

**הפחתה**: על סוכני הבינה המלאכותית לקבל גישה למערכות רק על בסיס צורך-חיוני כדי למנוע סוגי תקיפות אלה. התקשורת בין הסוכן למערכת גם צריכה להיות מאובטחת. יישום אימות ושליטת גישה הוא דרך נוספת להגן על מידע זה.

### עומס יתר על משאבים ושירותים

**תיאור:** סוכני בינה מלאכותית יכולים לגשת לכלים ושירותים שונים כדי לבצע משימות. תוקפים יכולים לנצל יכולת זו כדי לתקוף את השירותים על ידי שליחת נפח גבוה של בקשות דרך הסוכן, מה שעשוי לגרום לכשלי מערכת או לעלויות גבוהות.

**הפחתה:** יישם מדיניות להגבלת מספר הבקשות שסוכן יכול לבצע לשירות. הגבלת מספר ההחלפות בשיחה ומספר הבקשות אל הסוכן היא דרך נוספת למנוע סוגי תקיפות אלה.

### הרעלת בסיס הידע

**תיאור:** סוג תקיפה זה אינו תוקף במישרין את הסוכן אלא את בסיס הידע ושירותים אחרים שהסוכן ישתמש בהם. זה עלול לכלול זיהום של הנתונים או המידע שהסוכן ישתמש בו כדי להשלים משימה, מה שיוביל לתשובות מוטות או לא מכוונות למשתמש.

**הפחתה:** בצע אימות שוטף של הנתונים שהסוכן ישתמש בהם במסגרת זרימות העבודה שלו. ודא שניהול הגישה לנתונים אלה מאובטח וששינויים יתבצעו רק על ידי אנשים מהימנים כדי למנוע סוג תקיפה זה.

### שגיאות מצטברות

**תיאור:** סוכנים ניגשים לכלים ושירותים שונים כדי להשלים משימות. שגיאות הנגרמות על ידי תוקפים יכולות לגרום לכישלונות של מערכות נוספות שאליהן הסוכן מחובר, מה שהופך את התקיפה לנרחבת יותר וקשה יותר לאבחון.

**הפחתה**: שיטה אחת להימנע מכך היא לגרום לסוכן לפעול בסביבת מוגבלת, למשל ביצוע משימות בתוך מכולת Docker, כדי למנוע תקיפות ישירות על המערכת. יצירת מנגנוני גיבוי ולוגיקת ניסיון חוזר כאשר מערכות מסוימות מחזירות שגיאה היא דרך נוספת למנוע כשלי מערכת רחבים יותר.

## אדם בתהליך

דרך יעילה נוספת לבנות מערכות סוכנים אמינות היא שימוש באדם בתהליך. זה יוצר זרימה שבה משתמשים יכולים לספק משוב לסוכנים בזמן הריצה. המשתמשים למעשה פועלים כסוכנים במערכת רב-סוכנית ובהם הם מעניקים אישור או מפסיקים את התהליך הרץ.

![אדם בתהליך](../../../translated_images/he/human-in-the-loop.5f0068a678f62f4f.webp)

הנה קטע קוד המשתמש ב-AutoGen להראות כיצד מושג זה מיושם:

```python

# צור את הסוכנים.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # השתמש ב-input() כדי לקבל קלט מהמשתמש מהמסוף.

# צור את תנאי הסיום שיסיים את השיחה כאשר המשתמש אומר "APPROVE".
termination = TextMentionTermination("APPROVE")

# צור את הצוות.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# הרץ את השיחה וזרם את הפלט אל המסוף.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# השתמש ב-asyncio.run(...) כאשר מריצים בסקריפט.
await Console(stream)

```

## סיכום

בניית סוכני בינה מלאכותית אמינים דורשת עיצוב זהיר, אמצעי אבטחה חזקים ואיטרציה רציפה. באמצעות יישום מערכות הנחיה מטא מובנות, הבנת איומים פוטנציאליים ויישום אסטרטגיות הפחתה, מפתחים יכולים ליצור סוכנים שהם גם בטוחים וגם יעילים. בנוסף, שילוב גישת אדם בתהליך מבטיח שהסוכנים נשארים מיושרים לצרכי המשתמש תוך הפחתת סיכונים. ככל שהבינה המלאכותית ממשיכה להתפתח, שמירה על עמדה פרואקטיבית בנוגע לאבטחה, פרטיות ושיקולים אתיים תהיה המפתח לפיתוח אמון ואמינות במערכות המונעות על ידי בינה מלאכותית.

### יש לכם עוד שאלות לגבי בניית סוכני בינה מלאכותית אמינים?

הצטרפו ל-[Discord של Microsoft Foundry](https://aka.ms/ai-agents/discord) כדי להיפגש עם לומדים אחרים, להשתתף בשעות ייעוץ ולקבל תשובות לשאלות שלכם על סוכני הבינה המלאכותית.

## משאבים נוספים

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">סקירה על שימוש אחראי בבינה מלאכותית</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">הערכת מודלים גנרטיביים ויישומי בינה מלאכותית</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">הודעות מערכת לבטיחות</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">תבנית הערכת סיכונים</a>

## השיעור הקודם

[Agentic RAG](../05-agentic-rag/README.md)

## השיעור הבא

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
כתב ויתור:
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית Co-op Translator (https://github.com/Azure/co-op-translator). אף שאנו שואפים לדיוק, שימו לב שתרגומים אוטומטיים עלולים להכיל שגיאות או חוסר דיוקים. יש להתייחס למסמך המקורי בשפת המקור כאל המקור המוסמך. למידע קריטי, מומלץ לבצע תרגום מקצועי על ידי מתרגם אנושי. איננו אחראים לכל אי הבנה או פירוש שגוי הנובעים משימוש בתרגום זה.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->