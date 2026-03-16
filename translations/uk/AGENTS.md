# AGENTS.md

## Огляд проєкту

This repository contains "AI Agents for Beginners" - a comprehensive educational course teaching everything needed to build AI Agents. The course consists of 15+ lessons covering fundamentals, design patterns, frameworks, and production deployment of AI agents.

**Ключові технології:**
- Python 3.12+
- Jupyter Notebooks для інтерактивного навчання
- AI-фреймворки: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Служби Azure AI: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (доступний безкоштовний рівень)

**Архітектура:**
- Структура на основі уроків (каталоги 00-15+)
- Кожен урок містить: документацію README, приклади коду (Jupyter notebooks) та зображення
- Підтримка багатьох мов через автоматизовану систему перекладу
- Декілька варіантів фреймворків для кожного уроку (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Команди налаштування

### Передумови
- Python 3.12 або новіший
- GitHub account (for GitHub Models - free tier)
- Azure subscription (optional, for Azure AI services)

### Початкове налаштування

1. **Клонувати або форкнути репозиторій:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # АБО
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Створіть і активуйте віртуальне середовище Python:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # У Windows: venv\Scripts\activate
   ```

3. **Встановіть залежності:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Налаштуйте змінні середовища:**
   ```bash
   cp .env.example .env
   # Відредагуйте .env, додавши ваші ключі API та кінцеві точки
   ```

### Необхідні змінні середовища

Для **GitHub Models (Free)**:
- `GITHUB_TOKEN` - Персональний токен доступу з GitHub

Для **Azure AI Services** (опціонально):
- `PROJECT_ENDPOINT` - адреса кінцевої точки проєкту Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - ключ API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL кінцевої точки Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - ім'я розгортання для чат-моделі
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - ім'я розгортання для ембеддингів
- Додаткова конфігурація Azure, як показано в `.env.example`

## Робочий процес розробки

### Запуск Jupyter Notebooks

Кожен урок містить кілька Jupyter notebooks для різних фреймворків:

1. **Запустіть Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Перейдіть до каталогу уроку** (наприклад, `01-intro-to-ai-agents/code_samples/`)

3. **Відкрийте та запустіть ноутбуки:**
   - `*-semantic-kernel.ipynb` - Використання фреймворку Semantic Kernel
   - `*-autogen.ipynb` - Використання фреймворку AutoGen
   - `*-python-agent-framework.ipynb` - Використання Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Використання Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Використання Azure AI Agent Service

### Робота з різними фреймворками

**Semantic Kernel + GitHub Models:**
- Доступний безкоштовний рівень при наявності облікового запису GitHub
- Підходить для навчання та експериментів
- Шаблон файлу: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Доступний безкоштовний рівень при наявності облікового запису GitHub
- Можливості оркестрації кількох агентів
- Шаблон файлу: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Останній фреймворк від Microsoft
- Доступний для Python та .NET
- Шаблон файлу: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Потребує підписки Azure
- Функції, готові до використання у виробництві
- Шаблон файлу: `*-azureaiagent.ipynb`

## Інструкції з тестування

This is an educational repository with example code rather than production code with automated tests. To verify your setup and changes:

### Ручне тестування

1. **Перевірте середовище Python:**
   ```bash
   python --version  # Має бути 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Перевірте виконання ноутбуків:**
   ```bash
   # Перетворити ноутбук у скрипт і запустити (імпорти для тестів)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Перевірте змінні середовища:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Запуск окремих ноутбуків

Відкрийте ноутбуки в Jupyter і виконуйте клітинки послідовно. Кожен ноутбук є автономним і містить:
- Інструкції імпорту
- Завантаження конфігурації
- Приклади реалізацій агентів
- Очікувані результати в markdown-клітинках

## Стиль коду

### Конвенції Python

- **Версія Python**: 3.12+
- **Стиль коду**: Дотримуйтесь стандартних конвенцій Python PEP 8
- **Ноутбуки**: Використовуйте чіткі markdown-клітинки для пояснення концепцій
- **Імпорти**: Групуйте стандартну бібліотеку, сторонні та локальні імпорти

### Конвенції Jupyter Notebook

- Включайте описові markdown-клітинки перед кодовими клітинками
- Додавайте приклади виводу в ноутбуках для довідки
- Використовуйте зрозумілі імена змінних, що відповідають концепціям уроку
- Підтримуйте лінійний порядок виконання ноутбука (клітинка 1 → 2 → 3...)

### Організація файлів

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

## Збирання та розгортання

### Створення документації

У цьому репозиторії для документації використовується Markdown:
- README.md файли в кожній папці уроку
- Головний README.md у корені репозиторію
- Автоматизована система перекладу через GitHub Actions

### CI/CD конвеєр

Розташований у `.github/workflows/`:

1. **co-op-translator.yml** - Автоматичний переклад на 50+ мов
2. **welcome-issue.yml** - Привітання авторів нових issue
3. **welcome-pr.yml** - Привітання авторів нових pull request'ів

### Розгортання

This is an educational repository - no deployment process. Users:
1. Форкнути або клонувати репозиторій
2. Запускати ноутбуки локально або в GitHub Codespaces
3. Вчитися, змінюючи та експериментуючи з прикладами

## Керівництво щодо Pull Request'ів

### Перед надсиланням

1. **Перевірте свої зміни:**
   - Повністю виконайте змінені ноутбуки
   - Переконайтеся, що всі клітинки виконуються без помилок
   - Перевірте, що виводи є відповідними

2. **Оновлення документації:**
   - Оновіть README.md, якщо додаєте нові концепції
   - Додайте коментарі в ноутбуках для складного коду
   - Переконайтеся, що markdown-клітинки пояснюють призначення

3. **Зміни у файлах:**
   - Уникайте коміту файлів `.env` (користуйтеся `.env.example`)
   - Не додавайте в коміт директорії `venv/` або `__pycache__/`
   - Залишайте результати ноутбуків, коли вони демонструють концепції
   - Видаліть тимчасові файли та резервні ноутбуки (`*-backup.ipynb`)

### Формат назви PR

Використовуйте описові назви:
- `[Lesson-XX] Додати новий приклад для <concept>`
- `[Fix] Виправити опечатку в lesson-XX README`
- `[Update] Поліпшити приклад коду в lesson-XX`
- `[Docs] Оновити інструкції з налаштування`

### Обов'язкові перевірки

- Ноутбуки повинні виконуватися без помилок
- Файли README мають бути чіткими та точними
- Дотримуйтесь існуючих шаблонів коду в репозиторії
- Підтримуйте узгодженість з іншими уроками

## Додаткові нотатки

### Поширені помилки

1. **Невідповідність версії Python:**
   - Переконайтеся, що використовується Python 3.12+
   - Деякі пакети можуть не працювати з більш старими версіями
   - Використовуйте `python3 -m venv`, щоб явно вказати версію Python

2. **Змінні середовища:**
   - Завжди створюйте `.env` з `.env.example`
   - Не комітьте файл `.env` (він у `.gitignore`)
   - Токен GitHub потребує відповідних дозволів

3. **Конфлікти пакетів:**
   - Користуйтесь новим віртуальним середовищем
   - Встановлюйте з `requirements.txt`, а не по одному пакету
   - Деякі ноутбуки можуть вимагати додаткових пакетів, згаданих у їхніх markdown-клітинках

4. **Служби Azure:**
   - Служби Azure AI потребують активної підписки
   - Деякі функції залежать від регіону
   - Обмеження безкоштовного рівня застосовуються до GitHub Models

### Шлях навчання

Рекомендований порядок проходження уроків:
1. **00-course-setup** - Почніть тут для налаштування середовища
2. **01-intro-to-ai-agents** - Зрозуміти основи AI-агентів
3. **02-explore-agentic-frameworks** - Дізнатися про різні фреймворки
4. **03-agentic-design-patterns** - Основні шаблони проєктування
5. Продовжуйте послідовно проходити уроки за номерами

### Вибір фреймворку

Обирайте фреймворк залежно від ваших цілей:
- **Навчання/Прототипування**: Semantic Kernel + GitHub Models (безкоштовно)
- **Багатоагентні системи**: AutoGen
- **Останні можливості**: Microsoft Agent Framework (MAF)
- **Розгортання у виробництві**: Azure AI Agent Service

### Отримати допомогу

- Приєднуйтесь до [спільноти Microsoft Foundry у Discord](https://aka.ms/ai-agents/discord)
- Перегляньте README файли уроків для конкретних вказівок
- Перегляньте головний [README.md](./README.md) для огляду курсу
- Зверніться до [Налаштування курсу](./00-course-setup/README.md) для детальних інструкцій з налаштування

### Внесок

Це відкритий освітній проєкт. Внески вітаються:
- Поліпшити приклади коду
- Виправити опечатки або помилки
- Додати роз'яснювальні коментарі
- Запропонувати нові теми уроків
- Перекласти на додаткові мови

See [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) for current needs.

## Контекст проєкту

### Підтримка кількох мов

У цьому репозиторії використовується автоматизована система перекладу:
- Підтримується понад 50 мов
- Переклади у директоріях `/translations/<lang-code>/`
- Робочий процес GitHub Actions обробляє оновлення перекладів
- Початкові файли англійською у корені репозиторію

### Структура уроку

Кожен урок слідує єдиному шаблону:
1. Мініатюра відео з посиланням
2. Писемний вміст уроку (README.md)
3. Приклади коду в кількох фреймворках
4. Навчальні цілі та передумови
5. Додаткові навчальні ресурси із посиланнями

### Іменування прикладів коду

Формат: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Урок 4, Semantic Kernel
- `07-autogen.ipynb` - Урок 7, AutoGen
- `14-python-agent-framework.ipynb` - Урок 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Урок 14, MAF .NET

### Спеціальні директорії

- `translated_images/` - Локалізовані зображення для перекладів
- `images/` - Оригінальні зображення для англомовного вмісту
- `.devcontainer/` - Конфігурація контейнера розробки для VS Code
- `.github/` - GitHub Actions робочі процеси та шаблони

### Залежності

Ключові пакети з `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - фреймворк AutoGen
- `semantic-kernel` - фреймворк Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - служби Azure AI
- `azure-search-documents` - інтеграція Azure AI Search
- `chromadb` - Векторна база даних для прикладів RAG
- `chainlit` - фреймворк інтерфейсу чату
- `browser_use` - Автоматизація браузера для агентів
- `mcp[cli]` - підтримка Model Context Protocol
- `mem0ai` - Управління пам'яттю для агентів

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Відмова від відповідальності**:
Цей документ було перекладено за допомогою сервісу перекладу на основі штучного інтелекту [Co-op Translator](https://github.com/Azure/co-op-translator). Хоча ми прагнемо до точності, просимо врахувати, що автоматичні переклади можуть містити помилки або неточності. Оригінальний документ рідною мовою слід вважати авторитетним джерелом. Для критично важливої інформації рекомендується скористатися професійним перекладом, виконаним людиною. Ми не несемо відповідальності за будь-які непорозуміння або неправильні тлумачення, що виникли внаслідок використання цього перекладу.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->