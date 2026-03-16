# הגדרת הקורס

## مقدּמה

הלקסון הזה יכסה כיצד להפעיל את דוגמאות הקוד של הקורס הזה.

## הצטרף ללומדים אחרים וקבל עזרה

לפני שתתחיל לשכפל את הרפוזיטורי שלך, הצטרף ל-[ערוץ דיסקורד של AI Agents למתחילים](https://aka.ms/ai-agents/discord) כדי לקבל עזרה בהגדרה, לשאול שאלות לגבי הקורס, או כדי להתחבר עם לומדים אחרים.

## שכפל או פורק את הרפוזיטורי הזה

כדי להתחיל, אנא שכפל או פורק את רפוזיטורי ה-GitHub. זה ייצור גרסה משלך של חומר הקורס כך שתוכל להפעיל, לבדוק ולשנות את הקוד!

ניתן לעשות זאת בלחיצה על הקישור ל- <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">פורק את הרפוזיטורי</a>

כעת יש לך גרסה משלך של הפורק של הקורס בקישור הבא:

![Forked Repo](../../../translated_images/he/forked-repo.33f27ca1901baa6a.webp)

### שכפול שטחי (מומלץ לסדנאות / Codespaces)

  >הרפוזיטורי המלא יכול להיות גדול (~3 GB) כשאתה מוריד את כל ההיסטוריה וכל הקבצים. אם אתה משתתף רק בסדנה או צריך רק כמה תיקיות לקורס, שכפול שטחי (או שכפול דל) ימנע את רוב ההורדה על ידי קיצור ההיסטוריה ו/או דילוג על בלובים.

#### שכפול שטחי מהיר — היסטוריה מינימלית, כל הקבצים

החלף את `<your-username>` בפקודות מטה בכתובת ה-URL של הפורק שלך (או בכתובת ה-URL של האספקה אם תרצה).

כדי לשכפל רק את היסטוריית הקומיטים האחרונה (הורדה קטנה):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

כדי לשכפל ענף ספציפי:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### שכפול חלקי (דל) — מינימום בלובים + תיקיות נבחרות בלבד

זה משתמש בשכפול חלקי וב-sparse-checkout (דורש Git 2.25+ ומומלץ להשתמש ב-Git מודרני עם תמיכה בשכפול חלקי):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

גש לתיקיית הרפוזיטורי:

```bash|powershell
cd ai-agents-for-beginners
```

ואז ציין אילו תיקיות אתה רוצה (דוגמה למטה מציגה שתי תיקיות):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

לאחר השכפול ואימות הקבצים, אם אתה צריך רק את הקבצים ורוצה לפנות מקום (ללא היסטוריית git), אנא מחק את המידע המטאדאטה של הרפוזיטורי (💀בלתי הפיך — תאבד את כל פונקציונליות Git: אין קומיטים, משיכות, דחיפות או גישה להיסטוריה).

```bash
# זש/בש
rm -rf .git
```

```powershell
# פאוורשל
Remove-Item -Recurse -Force .git
```

#### שימוש ב-GitHub Codespaces (מומלץ להימנע מהורדות גדולות מקומיות)

- צור חיבור Codespace חדש לרפוזיטורי הזה דרך [ממשק GitHub](https://github.com/codespaces).  

- בטרמינל של ה-Codespace שנוצר הרץ אחת מהפקודות לשכפול השטחי/הדל למעלה כדי להביא רק את תיקיות השיעורים שאתה צריך לתוך סביבת העבודה של Codespace.
- אופציונלי: אחרי השכפול בתוך Codespaces, הסר את .git כדי לשחרר מקום נוסף (ראה פקודות הסרה למעלה).
- שים לב: אם אתה מעדיף לפתוח את הרפוזיטורי ישירות ב-Codespaces (בלי שכפול נוסף), שים לב ש-Codespaces ייבנה את סביבת devcontainer וייתכן שעדיין יספק יותר ממה שאתה צריך. שכפול שטחי בתוך Codespace חדש נותן לך שליטה טובה יותר על השימוש בדיסק.

#### טיפים

- תמיד החלף את כתובת השכפול לכתובת הפורק שלך אם אתה רוצה לערוך/לקמוט.
- אם בעתיד תצטרך יותר היסטוריה או קבצים, תוכל למשוך אותם או להתאים את sparse-checkout לכלול תיקיות נוספות.

## הפעלת הקוד

קורס זה מציע סדרת מחברות Jupyter שתוכל להריץ כדי לקבל ניסיון מעשי בבניית סוכני בינה מלאכותית.

דוגמאות הקוד משתמשות באחת מהאפשרויות הבאות:

**דורש חשבון GitHub - בחינם**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. מסומן כ-(semantic-kernel.ipynb)  
2) AutoGen Framework + GitHub Models Marketplace. מסומן כ-(autogen.ipynb)  

**דורש מנוי Azure**:  
3) Azure AI Foundry + Azure AI Agent Service. מסומן כ-(azureaiagent.ipynb)  

אנו מעודדים אותך לנסות את כל שלוש האופציות כדי לראות איזו מהן מתאימה לך ביותר.

כל אופציה שתבחר תקבע אילו צעדי הגדרה אתה צריך לפעול על פיהם למטה:

## דרישות

- Python 3.12+  
  - **הערה**: אם אין לך Python3.12 מותקן, ודא שאתה מתקין אותו. לאחר מכן צור את סביבת ה-venv שלך באמצעות python3.12 כדי להבטיח שהגרסאות הנכונות מותקנות מתוך קובץ requirements.txt.  
  
    >דוגמה  

    צור תיקיית venv ב-Python:

    ```bash|powershell
    python -m venv venv
    ```

    לאחר מכן הפעל את סביבת ה-venv עבור:

    ```bash
    # זש/באש
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: לקודים המשתמשים ב-.NET, וודא שאתה מתקין את [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) או גרסה מאוחרת יותר. לאחר מכן בדוק את גרסת .NET SDK המותקנת:

    ```bash|powershell
    dotnet --list-sdks
    ```

- חשבון GitHub - לגישה ל-GitHub Models Marketplace  
- מנוי Azure - לגישה ל-Microsoft Foundry  
- חשבון Microsoft Foundry - לגישה לשירות Azure AI Agent  

כלולנו קובץ `requirements.txt` בשורש הרפוזיטורי שמכיל את כל חבילת ה-Python הנדרשות כדי להריץ את דוגמאות הקוד.

אתה יכול להתקין אותן על ידי הרצת הפקודה הבאה בטרמינל שלך בתיקיית השורש של הרפוזיטורי:

```bash|powershell
pip install -r requirements.txt
```
  
אנו ממליצים ליצור סביבת Python וירטואלית כדי להימנע מכל התנגשויות ובעיות.

## הגדרת VSCode

וודא שאתה משתמש בגרסת ה-Python המתאימה ב-VSCode.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## הגדרת דוגמאות המשתמשות ב-GitHub Models

### שלב 1: קבל את אסימון הגישה האישית (PAT) שלך מ-GitHub

קורס זה מנצל את GitHub Models Marketplace, ומספק גישה חופשית למודלי שפה גדולים (LLMs) שתשתמש בהם לבניית סוכני בינה מלאכותית.

כדי להשתמש ב-GitHub Models, תצטרך ליצור [אסימון גישה אישי ל-GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

ניתן לעשות זאת על ידי כניסה ל<a href="https://github.com/settings/personal-access-tokens" target="_blank">הגדרות אסימוני הגישה האישיים</a> בחשבון ה-GitHub שלך.

אנא פעל לפי [עקרון ההרשאה המינימלית](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) בעת יצירת האסימון שלך. משמעות הדבר היא שעליך לתת לאסימון רק את ההרשאות שהוא זקוק להן כדי להפעיל את דוגמאות הקוד בקורס זה.

1. בחר באפשרות `Fine-grained tokens` בצד השמאלי של המסך על ידי ניווט ל**Developer settings**

   ![Developer settings](../../../translated_images/he/profile_developer_settings.410a859fe749c755.webp)

   לאחר מכן בחר `Generate new token`.

   ![Generate Token](../../../translated_images/he/fga_new_token.1c1a234afe202ab3.webp)

2. הזן שם תיאורי לאסימון שלך שמשקף את מטרתו, כדי שיהיה קל לזהות אותו מאוחר יותר.

    🔐 המלצת משך האסימון

    משך מומלץ: 30 ימים  
    למצב אבטחה חזק יותר, תוכל לבחור תקופה קצרה יותר — כגון 7 ימים 🛡️  
    זו דרך מצוינת להציב מטרה אישית ולהשלים את הקורס בזמן שהמומנטום הלמידתי שלך גבוה 🚀.

    ![Token Name and Expiration](../../../translated_images/he/token-name-expiry-date.a095fb0de6386864.webp)

3. הגבל את היקף האסימון לפורק שלך של הרפוזיטורי הזה.

    ![Limit scope to fork repository](../../../translated_images/he/token_repository_limit.924ade5e11d9d8bb.webp)

4. הגבל את הרשאות האסימון: תחת **Permissions**, לחץ על לשונית **Account**, ולאחר מכן לחץ על כפתור "+ Add permissions". ייפתח תפריט נפתח. אנא חפש **Models** וסמן את התיבה שלצדו.

    ![Add Models Permission](../../../translated_images/he/add_models_permissions.c0c44ed8b40fc143.webp)

5. אמת את ההרשאות הדרושות לפני יצירת האסימון. ![Verify Permissions](../../../translated_images/he/verify_permissions.06bd9e43987a8b21.webp)

6. לפני יצירת האסימון, וודא שאתה מוכן לשמור את האסימון במקום בטוח כמו מאגר סיסמאות, שכן הוא לא יוצג שוב לאחר יצירתו. ![Store Token Securely](../../../translated_images/he/store_token_securely.08ee2274c6ad6caf.webp)

העתק את האסימון החדש שיצרת. כעת תוסיף אותו לקובץ `.env` הכלול בקורס זה.

### שלב 2: צור את קובץ `.env` שלך

כדי ליצור את קובץ `.env` שלך, הרץ את הפקודה הבאה בטרמינל.

```bash
# זש/בש
cp .env.example .env
```

```powershell
# פאוורשל
Copy-Item .env.example .env
```

זה יעתיק את הקובץ לדוגמה ויצור `.env` בתיקייתך, שבו תמלא את הערכים של המשתני סביבה.

עם ההעתקה של האסימון שלך, פתח את קובץ `.env` בעורך הטקסט האהוב עליך והדבק את האסימון בשדה `GITHUB_TOKEN`.

![GitHub Token Field](../../../translated_images/he/github_token_field.20491ed3224b5f4a.webp)

כעת אמור להיות באפשרותך להריץ את דוגמאות הקוד של הקורס הזה.

## הגדרת דוגמאות המשתמשות ב-Microsoft Foundry וב-Azure AI Agent Service

### שלב 1: קבל את נקודת הקצה (Endpoint) של פרויקט ה-Azure שלך

עקוב אחרי הצעדים ליצירת Hub ופרויקט ב-Azure AI Foundry שנמצא כאן: [סקירת משאבי Hub](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

לאחר שיצרת את הפרויקט, תצטרך לקבל את מחרוזת החיבור לפרויקט שלך.

ניתן לעשות זאת על ידי כניסה לדף ה**Overview** של הפרויקט שלך בפורטל Microsoft Foundry.

![Project Connection String](../../../translated_images/he/project-endpoint.8cf04c9975bbfbf1.webp)

### שלב 2: צור את קובץ `.env` שלך

כדי ליצור את קובץ `.env` שלך, הרץ את הפקודה הבאה בטרמינל.

```bash
# זש/בש
cp .env.example .env
```

```powershell
# פאוורשל
Copy-Item .env.example .env
```

זה יעתיק את קובץ הדוגמה ויבנה `.env` בתיקייתך, שבו תמלא את ערכי משתני הסביבה.

עם ההעתקה של האסימון שלך, פתח את הקובץ `.env` בעורך הטקסט האהוב עליך והדבק את האסימון בשדה `PROJECT_ENDPOINT`.

### שלב 3: התחבר ל-Azure

כפרקטיקת אבטחה טובה, נשתמש ב-[אימות ללא מפתח](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) כדי לאמת קישור ל-Azure OpenAI עם Microsoft Entra ID.

לאחר מכן, פתח טרמינל והריץ `az login --use-device-code` כדי להתחבר לחשבון Azure שלך.

לאחר ההתחברות, בטרמינל בחר את המנוי שלך.

## משתני סביבה נוספים - Azure Search ו-Azure OpenAI

לשיעור Agentic RAG - שיעור 5 - יש דוגמאות שמשתמשות ב-Azure Search וב-Azure OpenAI.

אם תרצה להריץ דוגמאות אלה, תצטרך להוסיף את משתני הסביבה הבאים בקובץ `.env` שלך:

### דף סקירה (Project)

- `AZURE_SUBSCRIPTION_ID` - בדוק את **פרטי הפרויקט** בדף **Overview** של הפרויקט שלך.  
- `AZURE_AI_PROJECT_NAME` - בעיין בחלק העליון של דף **Overview** של הפרויקט שלך.  
- `AZURE_OPENAI_SERVICE` - מצא זאת בלשונית **כלולות היכולות** ל-**שירות Azure OpenAI** בדף **Overview**.

### מרכז ניהול

- `AZURE_OPENAI_RESOURCE_GROUP` - עבור ל**מאפייני הפרויקט** בדף **Overview** של **מרכז הניהול**.  
- `GLOBAL_LLM_SERVICE` - תחת **משאבים מחוברים**, מצא את שם החיבור של **Azure AI Services**. אם לא רשום, בדוק את ה-**פורטל Azure** תחת קבוצת המשאבים שלך עבור שם משאב שירותי AI.

### דף מודלים ונקודות קצה

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - בחר את מודל ההטמעה שלך (למשל, `text-embedding-ada-002`) ורשום את **שם הפריסה** מהפרטים של המודל.  
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - בחר את מודל הצ'אט שלך (למשל, `gpt-4o-mini`) ורשום את **שם הפריסה** מהפרטים של המודל.

### פורטל Azure

- `AZURE_OPENAI_ENDPOINT` - חפש **שירותי Azure AI**, לחץ עליו, עבור ל**ניהול משאבים**, **מפתחות ונקודת קצה**, גלול למטה אל "נקודות קצה של Azure OpenAI", והעתק את זו שכתוב עליה "שירותי שפה".  
- `AZURE_OPENAI_API_KEY` - מאותו המסך, העתק את KEY 1 או KEY 2.  
- `AZURE_SEARCH_SERVICE_ENDPOINT` - מצא את משאב **Azure AI Search** שלך, לחץ עליו וראה את ה**סקירה**.  
- `AZURE_SEARCH_API_KEY` - לאחר מכן עבור ל**הגדרות**, ואז ל**מפתחות** כדי להעתיק את המפתח הראשי או המשני.

### דף חיצוני

- `AZURE_OPENAI_API_VERSION` - בקר בדף [מחזור חיי גרסת API](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) תחת **הגרסה הרשמית העדכנית ביותר**.

### הגדרת אימות ללא מפתח

במקום לקודד את האישורים ישירות, נשתמש בקישור ללא מפתח עם Azure OpenAI. לשם כך, נייבא את `DefaultAzureCredential` ואחר כך נקרא לפונקציה `DefaultAzureCredential` כדי לקבל את האישורים.

```python
# פייתון
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## נתקעת איפשהו?
אם יש לך בעיות בהרצת ההגדרה הזו, הצטרף ל- <a href="https://discord.gg/kzRShWzttr" target="_blank">קהילת Azure AI ב-Discord</a> או <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">צור דו"ח בעיה</a>.

## השיעור הבא

אתה עכשיו מוכן להריץ את הקוד של הקורס הזה. בהצלחה בלמידה נוספת על עולם סוכני ה-AI!

[הקדמה לסוכני AI ומקרי השימוש שלהם](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**כתב ויתור**:  
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש לקחת בחשבון שתרגומים אוטומטיים עשויים להכיל טעויות או אי דיוקים. המסמך המקורי בשפתו המקורית נחשב למקור הסמכותי. למידע קריטי מומלץ להיעזר בתרגום מקצועי של בני אדם. אנו לא אחראים על הבנות שגויות או פרשנויות מוטעות הנובעות משימוש בתרגום זה.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->