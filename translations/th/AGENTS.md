# AGENTS.md

## Project Overview

พื้นที่เก็บโค้ดนี้ประกอบด้วย "AI Agents for Beginners" - คอร์สการศึกษาครบวงจรที่สอนทุกอย่างที่จำเป็นในการสร้าง AI Agents คอร์สประกอบด้วยบทเรียนกว่า 15 บทที่ครอบคลุมพื้นฐาน รูปแบบการออกแบบ เฟรมเวิร์ก และการปรับใช้งานจริงของเอเจนต์ AI

**Key Technologies:**
- Python 3.12+
- Jupyter Notebooks สำหรับการเรียนเชิงโต้ตอบ
- AI Frameworks: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Services: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (free tier available)

**Architecture:**
- โครงสร้างแบบบทเรียน (ไดเรกทอรี 00-15+)
- แต่ละบทประกอบด้วย: เอกสาร README, ตัวอย่างโค้ด (Jupyter notebooks), และรูปภาพ
- รองรับหลายภาษาโดยระบบแปลอัตโนมัติ
- ตัวเลือกเฟรมเวิร์กหลายแบบต่อบท (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Setup Commands

### Prerequisites
- Python 3.12 หรือสูงกว่า
- บัญชี GitHub (สำหรับ GitHub Models - free tier)
- บัญชีสมาชิก Azure (ไม่บังคับ สำหรับบริการ Azure AI)

### Initial Setup

1. **Clone or fork the repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # หรือ
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Create and activate Python virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # บน Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # แก้ไขไฟล์ .env โดยใส่คีย์ API และจุดสิ้นสุด (endpoints) ของคุณ
   ```

### Required Environment Variables

For **GitHub Models (Free)**:
- `GITHUB_TOKEN` - โทเค็นการเข้าถึงส่วนบุคคลจาก GitHub

For **Azure AI Services** (optional):
- `PROJECT_ENDPOINT` - endpoint ของโครงการ Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - คีย์ API ของ Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL endpoint ของ Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - ชื่อ deployment สำหรับโมเดลแชท
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - ชื่อ deployment สำหรับ embeddings
- การกำหนดค่า Azure เพิ่มเติมตามที่แสดงใน `.env.example`

## Development Workflow

### Running Jupyter Notebooks

แต่ละบทจะมี Jupyter notebooks หลายไฟล์สำหรับเฟรมเวิร์กต่าง ๆ:

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigate to a lesson directory** (e.g., `01-intro-to-ai-agents/code_samples/`)

3. **Open and run notebooks:**
   - `*-semantic-kernel.ipynb` - ใช้เฟรมเวิร์ก Semantic Kernel
   - `*-autogen.ipynb` - ใช้เฟรมเวิร์ก AutoGen
   - `*-python-agent-framework.ipynb` - ใช้ Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - ใช้ Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - ใช้ Azure AI Agent Service

### Working with Different Frameworks

**Semantic Kernel + GitHub Models:**
- มีชั้นฟรีให้ใช้งานกับบัญชี GitHub
- เหมาะสำหรับการเรียนรู้และทดลอง
- รูปแบบไฟล์: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- มีชั้นฟรีให้ใช้งานกับบัญชี GitHub
- ความสามารถจัดการการทำงานแบบ multi-agent
- รูปแบบไฟล์: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- เฟรมเวิร์กล่าสุดจาก Microsoft
- ใช้ได้ทั้งใน Python และ .NET
- รูปแบบไฟล์: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- ต้องมีสมาชิก Azure
- ฟีเจอร์พร้อมใช้งานสำหรับการใช้งานจริงในผลิตภัณฑ์
- รูปแบบไฟล์: `*-azureaiagent.ipynb`

## Testing Instructions

นี่คือพื้นที่เก็บโค้ดเชิงการศึกษา มีตัวอย่างโค้ดมากกว่าการเป็นโค้ดสำหรับการผลิตที่มีการทดสอบอัตโนมัติ ในการยืนยันการตั้งค่าและการเปลี่ยนแปลงของคุณ:

### Manual Testing

1. **Test Python environment:**
   ```bash
   python --version  # ควรเป็น 3.12 ขึ้นไป
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test notebook execution:**
   ```bash
   # แปลงโน้ตบุ๊กเป็นสคริปต์และรัน (ทดสอบการนำเข้า)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verify environment variables:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Running Individual Notebooks

เปิดโน้ตบุ๊กใน Jupyter และรันเซลล์ตามลำดับ แต่ละโน้ตบุ๊กเป็นแบบ self-contained และรวมถึง:
- คำสั่ง import
- การโหลดการกำหนดค่า
- ตัวอย่างการใช้งานเอเจนต์
- ผลลัพธ์ที่คาดหวังในเซลล์ markdown

## Code Style

### Python Conventions

- **Python Version**: 3.12+
- **Code Style**: ปฏิบัติตามมาตรฐาน Python PEP 8
- **Notebooks**: ใช้เซลล์ markdown ที่ชัดเจนเพื่ออธิบายแนวคิด
- **Imports**: จัดกลุ่มตาม standard library, third-party, local imports

### Jupyter Notebook Conventions

- ใส่เซลล์ markdown อธิบายก่อนเซลล์โค้ด
- เพิ่มตัวอย่างผลลัพธ์ในโน้ตบุ๊กเพื่อเป็นข้อมูลอ้างอิง
- ใช้ชื่อตัวแปรที่ชัดเจนและสอดคล้องกับแนวคิดของบทเรียน
- รักษาลำดับการรันโน้ตบุ๊กให้เป็นเส้นตรง (cell 1 → 2 → 3...)

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

พื้นที่เก็บนี้ใช้ Markdown สำหรับเอกสาร:
- ไฟล์ README.md ในแต่ละโฟลเดอร์บทเรียน
- README.md หลักที่รูทของรีโพสิทอรี
- ระบบแปลภาษาอัตโนมัติผ่าน GitHub Actions

### CI/CD Pipeline

Located in `.github/workflows/`:

1. **co-op-translator.yml** - การแปลอัตโนมัติเป็นมากกว่า 50 ภาษา
2. **welcome-issue.yml** - ต้อนรับผู้สร้าง issue ใหม่
3. **welcome-pr.yml** - ต้อนรับผู้ร่วมส่ง pull request ใหม่

### Deployment

นี่คือรีโพสิทอรีเชิงการศึกษา - ไม่มีกระบวนการปรับใช้งาน ผู้ใช้:
1. Fork หรือ clone รีโพสิทอรี
2. รันโน้ตบุ๊กในเครื่องหรือใน GitHub Codespaces
3. เรียนรู้โดยการปรับแก้และทดลองกับตัวอย่าง

## Pull Request Guidelines

### Before Submitting

1. **Test your changes:**
   - รันโน้ตบุ๊กที่ได้รับผลกระทบให้ครบ
   - ยืนยันว่าเซลล์ทั้งหมดรันโดยไม่มีข้อผิดพลาด
   - ตรวจสอบว่าผลลัพธ์เป็นไปตามที่คาดหวัง

2. **Documentation updates:**
   - อัปเดต README.md หากเพิ่มแนวคิดใหม่
   - เพิ่มคอมเมนต์ในโน้ตบุ๊กสำหรับโค้ดที่ซับซ้อน
   - ตรวจสอบว่าเซลล์ markdown อธิบายจุดประสงค์อย่างชัดเจน

3. **File changes:**
   - หลีกเลี่ยงการคอมมิตไฟล์ `.env` (ใช้ `.env.example`)
   - อย่าคอมมิตไดเรกทอรี `venv/` หรือ `__pycache__/`
   - เก็บเอาต์พุตโน้ตบุ๊กไว้เมื่อมันแสดงแนวคิด
   - ลบไฟล์ชั่วคราวและโน้ตบุ๊กสำรอง (`*-backup.ipynb`)

### PR Title Format

Use descriptive titles:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Correct typo in lesson-XX README`
- `[Update] Improve code sample in lesson-XX`
- `[Docs] Update setup instructions`

### Required Checks

- โน้ตบุ๊กควรรันโดยไม่มีข้อผิดพลาด
- ไฟล์ README ควรชัดเจนและถูกต้อง
- ปฏิบัติตามรูปแบบโค้ดที่มีอยู่ในรีโพสิทอรี
- รักษาความสอดคล้องกับบทเรียนอื่น ๆ

## Additional Notes

### Common Gotchas

1. **Python version mismatch:**
   - ตรวจสอบให้แน่ใจว่าใช้ Python 3.12+
   - บางแพ็กเกจอาจไม่ทำงานกับเวอร์ชันเก่า
   - ใช้ `python3 -m venv` เพื่อระบุเวอร์ชัน Python อย่างชัดเจน

2. **Environment variables:**
   - สร้างไฟล์ `.env` จาก `.env.example` เสมอ
   - อย่าคอมมิตไฟล์ `.env` (มีใน `.gitignore`)
   - โทเค็น GitHub ต้องมีสิทธิที่เหมาะสม

3. **Package conflicts:**
   - ใช้ virtual environment ใหม่
   - ติดตั้งจาก `requirements.txt` แทนการติดตั้งทีละแพ็กเกจ
   - บางโน้ตบุ๊กอาจต้องการแพ็กเกจเพิ่มเติมที่ระบุไว้ในเซลล์ markdown ของพวกมัน

4. **Azure services:**
   - บริการ Azure AI ต้องมีการสมัครใช้งานที่ใช้งานอยู่
   - ฟีเจอร์บางอย่างจำกัดตามภูมิภาค
   - ข้อจำกัดของชั้นฟรีมีผลกับ GitHub Models

### Learning Path

แนวทางที่แนะนำในการเรียนบทเรียน:
1. **00-course-setup** - เริ่มที่นี่สำหรับการตั้งค่าสภาพแวดล้อม
2. **01-intro-to-ai-agents** - ทำความเข้าใจพื้นฐานของ AI agents
3. **02-explore-agentic-frameworks** - เรียนรู้เกี่ยวกับเฟรมเวิร์กต่าง ๆ
4. **03-agentic-design-patterns** - รูปแบบการออกแบบหลัก
5. ดำเนินการผ่านบทเรียนตามหมายเลขอย่างต่อเนื่อง

### Framework Selection

เลือกเฟรมเวิร์กตามเป้าหมายของคุณ:
- **Learning/Prototyping**: Semantic Kernel + GitHub Models (free)
- **Multi-agent systems**: AutoGen
- **Latest features**: Microsoft Agent Framework (MAF)
- **Production deployment**: Azure AI Agent Service

### Getting Help

- เข้าร่วม [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- ทบทวนไฟล์ README ของบทเรียนสำหรับคำแนะนำเฉพาะ
- ตรวจสอบไฟล์หลัก [README.md](./README.md) สำหรับภาพรวมของคอร์ส
- ดู [Course Setup](./00-course-setup/README.md) สำหรับคำแนะนำการตั้งค่าโดยละเอียด

### Contributing

นี่คือโครงการการศึกษาแบบเปิด ยินดีรับการมีส่วนร่วม:
- ปรับปรุงตัวอย่างโค้ด
- แก้ไขคำผิดหรือข้อผิดพลาด
- เพิ่มคอมเมนต์เพื่อชี้แจง
- เสนอหัวข้อบทเรียนใหม่
- แปลเป็นภาษาอื่นเพิ่มเติม

ดู [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) สำหรับความต้องการปัจจุบัน

## Project-Specific Context

### Multi-Language Support

รีโพสิทอรีนี้ใช้ระบบแปลอัตโนมัติ:
- รองรับมากกว่า 50 ภาษา
- การแปลเก็บไว้ในไดเรกทอรี `/translations/<lang-code>/`
- workflow ของ GitHub Actions จัดการการอัปเดตการแปล
- ไฟล์ต้นฉบับเป็นภาษาอังกฤษที่รูทของรีโพสิทอรี

### Lesson Structure

แต่ละบทเรียนปฏิบัติตามรูปแบบที่สม่ำเสมอ:
1. รูปย่อวิดีโอพร้อมลิงก์
2. เนื้อหาบทเรียนเป็นลายลักษณ์อักษร (README.md)
3. ตัวอย่างโค้ดในหลายเฟรมเวิร์ก
4. วัตถุประสงค์การเรียนรู้และข้อกำหนดเบื้องต้น
5. แหล่งเรียนรู้เพิ่มเติมที่มีลิงก์

### Code Sample Naming

รูปแบบ: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - บทเรียนที่ 4, Semantic Kernel
- `07-autogen.ipynb` - บทเรียนที่ 7, AutoGen
- `14-python-agent-framework.ipynb` - บทเรียนที่ 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - บทเรียนที่ 14, MAF .NET

### Special Directories

- `translated_images/` - รูปภาพที่แปลแล้วสำหรับการแปลภาษา
- `images/` - รูปภาพต้นฉบับสำหรับเนื้อหาอังกฤษ
- `.devcontainer/` - การกำหนดคอนเทนเนอร์พัฒนา VS Code
- `.github/` - GitHub Actions workflows และเทมเพลต

### Dependencies

แพ็กเกจหลักจาก `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - AutoGen framework
- `semantic-kernel` - Semantic Kernel framework
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - บริการ Azure AI
- `azure-search-documents` - การผสาน Azure AI Search
- `chromadb` - ฐานข้อมูลเวกเตอร์สำหรับตัวอย่าง RAG
- `chainlit` - เฟรมเวิร์ก UI สำหรับแชท
- `browser_use` - การทำ automation เบราว์เซอร์สำหรับเอเจนต์
- `mcp[cli]` - การสนับสนุน Model Context Protocol
- `mem0ai` - การจัดการหน่วยความจำสำหรับเอเจนต์

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
ข้อจำกัดความรับผิดชอบ:
เอกสารฉบับนี้ได้รับการแปลโดยใช้บริการแปลภาษาอัตโนมัติ Co-op Translator (https://github.com/Azure/co-op-translator) แม้ว่าเราจะพยายามให้มีความถูกต้อง โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่ถูกต้อง เอกสารต้นฉบับในภาษาต้นทางควรถูกถือว่าเป็นแหล่งข้อมูลที่มีความน่าเชื่อถือและเป็นหลัก สำหรับข้อมูลที่สำคัญ แนะนำให้ใช้บริการแปลโดยนักแปลมนุษย์มืออาชีพ เราจะไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่ผิดพลาดอันเกิดจากการใช้การแปลฉบับนี้
<!-- CO-OP TRANSLATOR DISCLAIMER END -->