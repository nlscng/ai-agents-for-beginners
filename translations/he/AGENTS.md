# AGENTS.md

## סקירת הפרויקט

מאגר זה מכיל "סוכני AI למתחילים" - קורס חינוכי מקיף המלמד את כל הנדרש כדי לבנות סוכני בינה מלאכותית. הקורס מורכב מ-15+ שיעורים המכסים יסודות, דפוסי עיצוב, מסגרות, ופריסת ייצור של סוכנים.

**טכנולוגיות מרכזיות:**
- Python 3.12+
- Jupyter Notebooks ללמידה אינטראקטיבית
- מסגרות AI: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- שירותי Azure AI: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (שכבת חינם זמינה)

**ארכיטקטורה:**
- מבנה מבוסס שיעורים (תיקיות 00-15+)
- כל שיעור מכיל: תיעוד README, דוגמאות קוד (מחברות Jupyter), ותמונות
- תמיכה רב-שפתית באמצעות מערכת תרגום אוטומטית
- אפשרויות מסגרת מרובות לכל שיעור (Semantic Kernel, AutoGen, Azure AI Agent Service)

## פקודות התקנה

### דרישות מקדימות
- Python 3.12 או גרסה גבוהה יותר
- חשבון GitHub (עבור GitHub Models - שכבת חינם)
- מנוי Azure (אופציונלי, לשירותי Azure AI)

### הגדרה ראשונית

1. **Clone or fork the repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # או
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Create and activate Python virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # ב-Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # ערוך את קובץ .env והכנס בו את מפתחות ה-API ונקודות הקצה שלך
   ```

### משתני סביבה דרושים

For **GitHub Models (Free)**:
- `GITHUB_TOKEN` - אסימון גישה אישי מ-GitHub

For **Azure AI Services** (optional):
- `PROJECT_ENDPOINT` - Microsoft Foundry project endpoint
- `AZURE_OPENAI_API_KEY` - מפתח API של Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - כתובת Endpoint של Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - שם פריסת המודל לצ'אט
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - שם פריסת המודל ל-embeddings
- תצורות Azure נוספות כפי שמוצג ב-`.env.example`

## זרימת פיתוח

### הרצת Jupyter Notebooks

כל שיעור מכיל מספר מחברות Jupyter עבור מסגרות שונות:

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigate to a lesson directory** (e.g., `01-intro-to-ai-agents/code_samples/`)

3. **Open and run notebooks:**
   - `*-semantic-kernel.ipynb` - שימוש במסגרת Semantic Kernel
   - `*-autogen.ipynb` - שימוש במסגרת AutoGen
   - `*-python-agent-framework.ipynb` - שימוש ב-Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - שימוש ב-Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - שימוש ב-Azure AI Agent Service

### עבודה עם מסגרות שונות

**Semantic Kernel + GitHub Models:**
- שכבת חינם זמינה עם חשבון GitHub
- טוב ללמידה וניסויים
- תבנית קובץ: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- שכבת חינם זמינה עם חשבון GitHub
- יכולות אורקסטרציה מרובות-סוכנים
- תבנית קובץ: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- המסגרת העדכנית מבית Microsoft
- זמינה ב-Python וב-.NET
- תבנית קובץ: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- דורש מנוי Azure
- תכונות מוכנות לייצור
- תבנית קובץ: `*-azureaiagent.ipynb`

## הוראות בדיקה

זהו מאגר חינוכי עם קוד דוגמה ולא קוד ייצור עם בדיקות אוטומטיות. כדי לאמת את ההגדרה והשינויים שלך:

### בדיקות ידניות

1. **Test Python environment:**
   ```bash
   python --version  # חייב להיות 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test notebook execution:**
   ```bash
   # המר את המחברת לסקריפט והרץ (בודק את ייבוא המודולים)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verify environment variables:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### הרצת מחברות בודדות

פתח מחברות ב-Jupyter והריץ תאים ברצף. כל מחברת עצמאית וכוללת:
- הוראות ייבוא
- טעינת תצורה
- מימושי סוכנים לדוגמה
- תוצאות צפויות בתאי Markdown

## סגנון קוד

### הנחיות פייתון

- **Python Version**: 3.12+
- **Code Style**: עקוב אחר תקני PEP 8 של פייתון
- **Notebooks**: השתמש בתאי Markdown ברורים להסברת מושגים
- **Imports**: סדר לפי ספריית הסטנדרט, צד שלישי, וייבוא מקומי

### קונבנציות למחברות Jupyter

- כלול תאי Markdown מתארים לפני תאי קוד
- הוספת דוגמאות פלט במחברות כהפניות
- השתמש בשמות משתנים ברורים התואמים למושגי השיעור
- שמור על סדר הרצת המחברות ליניארי (תא 1 → 2 → 3...)

### File Organization

```
<lesson-number>-<lesson-name>/
├── README.md                     # Lesson documentation
├── code_samples/
│   ├── <number>-semantic-kernel.ipynb
│   ├── <number>-autogen.ipynb
│   ├── <number>-python-agent-framework.ipynb
│   └── <number>-azureaiagent.ipynb
└── images/
    └── *.png
```

## בנייה ופריסה

### בניית תיעוד

מאגר זה משתמש ב-Markdown לתיעוד:
- קבצי README.md בכל תיקיית שיעור
- README.md ראשי בשורש המאגר
- מערכת תרגום אוטומטית באמצעות GitHub Actions

### CI/CD Pipeline

ממוקם ב-`.github/workflows/`:

1. **co-op-translator.yml** - תרגום אוטומטי ל-50+ שפות
2. **welcome-issue.yml** - מברך יוצרי איטמים חדשים
3. **welcome-pr.yml** - מברך משתתפי Pull Request חדשים

### Deployment

זהו מאגר חינוכי - אין תהליך פריסה הגדרתי. המשתמשים:
1. Fork או clone של המאגר
2. הרצת המחברות מקומית או ב-GitHub Codespaces
3. למידה על ידי שינוי וניסוי בדוגמאות

## הנחיות לבקשות משיכה

### לפני שליחה

1. **Test your changes:**
   - הרץ את המחברות המושפעות במלואן
   - אשר שכל התאים רצים ללא שגיאות
   - בדוק שהתוצאות מתאימות

2. **Documentation updates:**
   - עדכן את README.md אם מוסיפים מושגים חדשים
   - הוסף הערות במחברות לקוד מורכב
   - ודא שתאי Markdown מסבירים את המטרה

3. **File changes:**
   - הימנע מהתחייבות קבצי `.env` (השתמש ב-`.env.example`)
   - אל תתחייב תיקיות `venv/` או `__pycache__/`
   - שמור פלט מחברות כאשר הם מראים מושגים
   - הסר קבצים זמניים וגיבויי מחברות (`*-backup.ipynb`)

### PR Title Format

Use descriptive titles:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Correct typo in lesson-XX README`
- `[Update] Improve code sample in lesson-XX`
- `[Docs] Update setup instructions`

### Required Checks

- מחברות צריכות להיאעדר ללא שגיאות
- קבצי README צריכים להיות ברורים ומדויקים
- עקוב אחרי דפוסי קוד קיימים במאגר
- שמור על אחידות עם שיעורים אחרים

## הערות נוספות

### בעיות נפוצות

1. **Python version mismatch:**
   - ודא שמשתמשים ב-Python 3.12+
   - חלק מהחבילות עשויות שלא לעבוד עם גרסאות ישנות יותר
   - השתמש ב-`python3 -m venv` כדי לציין במפורש את גרסת פייתון

2. **Environment variables:**
   - תמיד צור `.env` מתוך `.env.example`
   - אל תתחייב את קובץ `.env` (הוא ב-`.gitignore`)
   - אסימון GitHub זקוק להרשאות מתאימות

3. **Package conflicts:**
   - השתמש בסביבת venv חדשה
   - התקן מתוך `requirements.txt` במקום חבילות בודדות
   - חלק מהמחברות עשויות לדרוש חבילות נוספות שמפורטות בתאי Markdown שלהן

4. **Azure services:**
   - שירותי Azure AI דורשים מנוי פעיל
   - חלק מהתכונות תלויות באזור גיאוגרפי
   - הגבלות שכבת החינם חלות על GitHub Models

### מסלול הלימוד

המלצה להתקדמות דרך השיעורים:
1. **00-course-setup** - התחילו כאן להגדרת סביבה
2. **01-intro-to-ai-agents** - הבנת יסודות סוכני ה-AI
3. **02-explore-agentic-frameworks** - למידה על מסגרות שונות
4. **03-agentic-design-patterns** - דפוסי עיצוב מרכזיים
5. המשך דרך השיעורים המספריים ברצף

### בחירת מסגרת

בחר מסגרת בהתאם למטרותיך:
- **Learning/Prototyping**: Semantic Kernel + GitHub Models (חינם)
- **Multi-agent systems**: AutoGen
- **Latest features**: Microsoft Agent Framework (MAF)
- **Production deployment**: Azure AI Agent Service

### קבלת עזרה

- הצטרפו ל-[Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- עיינו בקבצי README של השיעורים לקבלת הנחיות ספציפיות
- בדקו את ה-[README.md](./README.md) הראשי עבור סקירת הקורס
- התייחסו ל-[Course Setup](./00-course-setup/README.md) להוראות התקנה מפורטות

### תרומות

זהו פרויקט חינוכי פתוח. תרומות מתקבלות בברכה:
- שיפור דוגמאות קוד
- תיקון שגיאות כתיב או טעויות
- הוספת הערות מבהירות
- הצעת נושאי שיעורים חדשים
- תרגום לשפות נוספות

See [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) for current needs.

## הקשר ספציפי לפרויקט

### תמיכה רב-שפתית

מאגר זה משתמש במערכת תרגום אוטומטית:
- תמיכה ב-50+ שפות
- תרגומים בתיקיות `/translations/<lang-code>/`
- workflow של GitHub Actions מטפל בעדכוני תרגום
- קבצי המקור באנגלית בשורש המאגר

### מבנה השיעור

כל שיעור עוקב אחרי תבנית עקבית:
1. תמונת ממוזערת וידאו עם קישור
2. תוכן השיעור הכתוב (README.md)
3. דוגמאות קוד במסגרות מרובות
4. מטרות למידה ודרישות מקדימות
5. משאבי למידה נוספים מקושרים

### ניסוח שם דוגמאות קוד

פורמט: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - שיעור 4, Semantic Kernel
- `07-autogen.ipynb` - שיעור 7, AutoGen
- `14-python-agent-framework.ipynb` - שיעור 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - שיעור 14, MAF .NET

### תיקיות מיוחדות

- `translated_images/` - תמונות מותאמות לשפות בתרגומים
- `images/` - תמונות מקוריות לתוכן האנגלי
- `.devcontainer/` - הגדרות מיכל פיתוח ל-VS Code
- `.github/` - workflows ו-template של GitHub Actions

### תלויות

חבילות מפתח מתוך `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - מסגרת AutoGen
- `semantic-kernel` - מסגרת Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - שירותי Azure AI
- `azure-search-documents` - אינטגרציה עם Azure AI Search
- `chromadb` - מסד וקטורי לדוגמאות RAG
- `chainlit` - מסגרת ממשק צ'אט
- `browser_use` - אוטומציה של דפדפן עבור סוכנים
- `mcp[cli]` - תמיכה ב-Model Context Protocol
- `mem0ai` - ניהול זיכרון עבור סוכנים

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
כתב ויתור:
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית Co-op Translator (https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש לשים לב כי תרגומים אוטומטיים עלולים להכיל שגיאות או אי־דיוקים. יש להתייחס לגרסה המקורית של המסמך בשפתו כמקור המוסמך. למידע קריטי מומלץ להיעזר בתרגום מקצועי על ידי מתרגם אנושי. איננו אחראים לכל אי־הבנה או לפרשנות שגויה הנובעת מהשימוש בתרגום זה.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->