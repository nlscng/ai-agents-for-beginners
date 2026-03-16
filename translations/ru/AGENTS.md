# AGENTS.md

## Обзор проекта

В этом репозитории находится "AI Agents for Beginners" — всесторонний образовательный курс, обучающий всему необходимому для создания AI-агентов. Курс состоит из 15+ уроков, охватывающих основы, шаблоны проектирования, фреймворки и развёртывание AI-агентов в продакшене.

**Ключевые технологии:**
- Python 3.12+
- Jupyter Notebooks для интерактивного обучения
- Фреймворки ИИ: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Сервисы Azure AI: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (доступен бесплатный тариф)

**Архитектура:**
- Структура, основанная на уроках (каталоги 00-15+)
- Каждый урок содержит: документацию README, примеры кода (Jupyter notebooks) и изображения
- Поддержка нескольких языков через автоматизированную систему перевода
- Несколько вариантов фреймворков для каждого урока (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Setup Commands

### Prerequisites
- Python 3.12 или выше
- Учётная запись GitHub (для GitHub Models - бесплатный уровень)
- Подписка Azure (необязательно, для сервисов Azure AI)

### Initial Setup

1. **Clone or fork the repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ИЛИ
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Create and activate Python virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # В Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # Отредактируйте .env, указав ваши API-ключи и конечные точки
   ```

### Required Environment Variables

For **GitHub Models (Free)**:
- `GITHUB_TOKEN` - Личный токен доступа из GitHub

For **Azure AI Services** (optional):
- `PROJECT_ENDPOINT` - Конечная точка проекта Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - Ключ API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL конечной точки Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Имя развёртывания для чат-модели
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Имя развёртывания для эмбеддингов
- Additional Azure configuration as shown in `.env.example`

## Development Workflow

### Running Jupyter Notebooks

Each lesson contains multiple Jupyter notebooks for different frameworks:

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigate to a lesson directory** (e.g., `01-intro-to-ai-agents/code_samples/`)

3. **Open and run notebooks:**
   - `*-semantic-kernel.ipynb` - Использование фреймворка Semantic Kernel
   - `*-autogen.ipynb` - Использование фреймворка AutoGen
   - `*-python-agent-framework.ipynb` - Использование Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Использование Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Использование Azure AI Agent Service

### Working with Different Frameworks

**Semantic Kernel + GitHub Models:**
- Free tier available with GitHub account
- Подходит для обучения и экспериментов
- File pattern: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Free tier available with GitHub account
- Возможности оркестрации нескольких агентов
- File pattern: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Последний фреймворк от Microsoft
- Доступен на Python и .NET
- File pattern: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Требует подписки Azure
- Функции, готовые к использованию в продакшене
- File pattern: `*-azureaiagent.ipynb`

## Testing Instructions

This is an educational repository with example code rather than production code with automated tests. To verify your setup and changes:

### Manual Testing

1. **Test Python environment:**
   ```bash
   python --version  # Должна быть версия 3.12 или выше.
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test notebook execution:**
   ```bash
   # Преобразовать ноутбук в скрипт и запустить (проверяет импорты)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verify environment variables:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Running Individual Notebooks

Open notebooks in Jupyter and execute cells sequentially. Each notebook is self-contained and includes:
- Операторы импорта
- Загрузку конфигурации
- Примеры реализаций агентов
- Ожидаемые результаты в markdown-ячейках

## Code Style

### Python Conventions

- **Python Version**: 3.12+
- **Code Style**: Следовать стандартным конвенциям PEP 8 для Python
- **Notebooks**: Использовать понятные markdown-ячейки для объяснения концепций
- **Imports**: Группировать по стандартной библиотеке, сторонним и локальным импортам

### Jupyter Notebook Conventions

- Включать описательные markdown-ячейки перед кодовыми ячейками
- Добавлять примеры вывода в ноутбуках для справки
- Использовать понятные имена переменных, соответствующие концепциям урока
- Сохранять линейный порядок выполнения ноутбука (cell 1 → 2 → 3...)

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

## Build and Deployment

### Building Documentation

This repository uses Markdown for documentation:
- Файлы README.md в каждой папке урока
- Главный README.md в корне репозитория
- Автоматизированная система перевода через GitHub Actions

### CI/CD Pipeline

Located in `.github/workflows/`:

1. **co-op-translator.yml** - Автоматический перевод на 50+ языков
2. **welcome-issue.yml** - Приветствует авторов новых issue
3. **welcome-pr.yml** - Приветствует авторов новых pull request

### Deployment

This is an educational repository - no deployment process. Users:
1. Сделайте fork или клонируйте репозиторий
2. Запускают ноутбуки локально или в GitHub Codespaces
3. Учитесь, изменяя и экспериментируя с примерами

## Pull Request Guidelines

### Before Submitting

1. **Test your changes:**
   - Запустите полностью затронутые ноутбуки
   - Убедитесь, что все ячейки выполняются без ошибок
   - Проверьте, что выводы корректны

2. **Documentation updates:**
   - Обновите README.md при добавлении новых концепций
   - Добавьте комментарии в ноутбуках для сложного кода
   - Убедитесь, что markdown-ячейки объясняют назначение

3. **File changes:**
   - Избегайте коммита файлов `.env` (используйте `.env.example`)
   - Не коммитьте каталоги `venv/` или `__pycache__/`
   - Сохраняйте выводы ноутбуков, когда они демонстрируют концепции
   - Удаляйте временные файлы и резервные ноутбуки (`*-backup.ipynb`)

### PR Title Format

Use descriptive titles:
- `[Lesson-XX] Добавить новый пример для <concept>`
- `[Fix] Исправить опечатку в lesson-XX README`
- `[Update] Улучшить пример кода в lesson-XX`
- `[Docs] Обновить инструкции по настройке`

### Required Checks

- Ноутбуки должны выполняться без ошибок
- Файлы README должны быть понятными и точными
- Следовать существующим шаблонам кода в репозитории
- Сохранять согласованность с другими уроками

## Additional Notes

### Common Gotchas

1. **Несоответствие версии Python:**
   - Убедитесь, что используется Python 3.12+
   - Некоторые пакеты могут не работать с более старыми версиями
   - Используйте `python3 -m venv`, чтобы явно указать версию Python

2. **Переменные окружения:**
   - Всегда создавайте `.env` из `.env.example`
   - Не коммитьте файл `.env` (он в `.gitignore`)
   - Токен GitHub требует надлежащих разрешений

3. **Конфликты пакетов:**
   - Используйте свежее виртуальное окружение
   - Устанавливайте из `requirements.txt`, а не по отдельным пакетам
   - Некоторые ноутбуки могут требовать дополнительные пакеты, указанные в их markdown-ячейках

4. **Сервисы Azure:**
   - Сервисы Azure AI требуют активной подписки
   - Некоторые функции специфичны для регионов
   - Ограничения бесплатного уровня применяются к GitHub Models

### Learning Path

Recommended progression through lessons:
1. **00-course-setup** - Начните здесь для настройки окружения
2. **01-intro-to-ai-agents** - Поймите основы AI-агентов
3. **02-explore-agentic-frameworks** - Узнайте о разных фреймворках
4. **03-agentic-design-patterns** - Основные шаблоны проектирования
5. Continue through numbered lessons sequentially

### Framework Selection

Choose framework based on your goals:
- **Learning/Prototyping**: Semantic Kernel + GitHub Models (free)
- **Multi-agent systems**: AutoGen
- **Latest features**: Microsoft Agent Framework (MAF)
- **Production deployment**: Azure AI Agent Service

### Getting Help

- Присоединяйтесь к [сообществу Microsoft Foundry в Discord](https://aka.ms/ai-agents/discord)
- Просмотрите файлы README уроков для конкретных указаний
- Проверьте главный [README.md](./README.md) для обзора курса
- Обратитесь к [Настройке курса](./00-course-setup/README.md) для подробных инструкций по настройке

### Contributing

Как внести вклад:
Это открытый образовательный проект. Вклады приветствуются:
- Улучшайте примеры кода
- Исправляйте опечатки или ошибки
- Добавляйте поясняющие комментарии
- Предлагайте новые темы для уроков
- Переводите на дополнительные языки

See [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) for current needs.

## Project-Specific Context

### Multi-Language Support

This repository uses an automated translation system:
- Поддерживается 50+ языков
- Переводы в каталогах `/translations/<lang-code>/`
- Рабочий процесс GitHub Actions обрабатывает обновления переводов
- Исходные файлы на английском в корне репозитория

### Lesson Structure

Each lesson follows a consistent pattern:
1. Миниатюра видео со ссылкой
2. Письменное содержание урока (README.md)
3. Примеры кода в нескольких фреймворках
4. Цели обучения и предварительные требования
5. Дополнительные обучающие ресурсы с ссылками

### Code Sample Naming

Format: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Урок 4, Semantic Kernel
- `07-autogen.ipynb` - Урок 7, AutoGen
- `14-python-agent-framework.ipynb` - Урок 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Урок 14, MAF .NET

### Special Directories

- `translated_images/` - Локализованные изображения для переводов
- `images/` - Оригинальные изображения для английского содержания
- `.devcontainer/` - Конфигурация контейнера разработки VS Code
- `.github/` - Рабочие процессы GitHub Actions и шаблоны

### Dependencies

Key packages from `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - Фреймворк AutoGen
- `semantic-kernel` - Фреймворк Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Сервисы Azure AI
- `azure-search-documents` - Интеграция с Azure AI Search
- `chromadb` - Векторная база данных для примеров RAG
- `chainlit` - Фреймворк интерфейса чата
- `browser_use` - Автоматизация браузера для агентов
- `mcp[cli]` - Поддержка Model Context Protocol
- `mem0ai` - Управление памятью для агентов

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Отказ от ответственности:
Этот документ был переведён с помощью сервиса машинного перевода на базе ИИ [Co-op Translator](https://github.com/Azure/co-op-translator). Мы стараемся обеспечивать точность, однако имейте в виду, что автоматические переводы могут содержать ошибки или неточности. Оригинальный документ на языке оригинала следует считать авторитетным источником. Для критически важной информации рекомендуется профессиональный перевод, выполненный человеком. Мы не несем ответственности за любые недоразумения или неверные толкования, возникшие в результате использования этого перевода.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->