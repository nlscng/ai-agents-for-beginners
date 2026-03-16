# AGENTS.md

## Project Overview

This repository mengandungi "AI Agents for Beginners" - satu kursus pendidikan komprehensif yang mengajar segala yang diperlukan untuk membina AI Agents. Kursus ini terdiri daripada 15+ pelajaran yang merangkumi asas, corak reka bentuk, rangka kerja, dan penyebaran pengeluaran agen AI.

**Key Technologies:**
- Python 3.12+
- Jupyter Notebooks untuk pembelajaran interaktif
- AI Frameworks: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI Services: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (lapisan percuma tersedia)

**Architecture:**
- Struktur berasaskan pelajaran (direktori 00-15+)
- Setiap pelajaran mengandungi: dokumentasi README, sampel kod (Jupyter notebooks), dan imej
- Sokongan berbilang bahasa melalui sistem penterjemahan automatik
- Berbilang pilihan rangka kerja bagi setiap pelajaran (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Setup Commands

### Prerequisites
- Python 3.12 atau lebih tinggi
- Akaun GitHub (untuk GitHub Models - lapisan percuma)
- Langganan Azure (opsional, untuk perkhidmatan Azure AI)

### Initial Setup

1. **Clone or fork the repository:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ATAU
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Create and activate Python virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Pada Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables:**
   ```bash
   cp .env.example .env
   # Sunting .env dengan kunci API dan titik hujung anda
   ```

### Required Environment Variables

For **GitHub Models (Free)**:
- `GITHUB_TOKEN` - Token capaian peribadi dari GitHub

For **Azure AI Services** (opsional):
- `PROJECT_ENDPOINT` - Microsoft Foundry project endpoint
- `AZURE_OPENAI_API_KEY` - Kunci API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL endpoint Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Nama deployment untuk model chat
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Nama deployment untuk embeddings
- Konfigurasi Azure tambahan seperti yang ditunjukkan dalam `.env.example`

## Development Workflow

### Running Jupyter Notebooks

Setiap pelajaran mengandungi pelbagai Jupyter notebooks untuk rangka kerja yang berbeza:

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigate to a lesson directory** (contoh, `01-intro-to-ai-agents/code_samples/`)

3. **Open and run notebooks:**
   - `*-semantic-kernel.ipynb` - Menggunakan rangka kerja Semantic Kernel
   - `*-autogen.ipynb` - Menggunakan rangka kerja AutoGen
   - `*-python-agent-framework.ipynb` - Menggunakan Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Menggunakan Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Menggunakan Azure AI Agent Service

### Working with Different Frameworks

**Semantic Kernel + GitHub Models:**
- Lapisan percuma tersedia dengan akaun GitHub
- Sesuai untuk pembelajaran dan eksperimen
- Corak fail: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Lapisan percuma tersedia dengan akaun GitHub
- Keupayaan orkestrasi pelbagai ejen
- Corak fail: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Rangka kerja terkini dari Microsoft
- Tersedia dalam Python dan .NET
- Corak fail: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Memerlukan langganan Azure
- Ciri sedia untuk pengeluaran
- Corak fail: `*-azureaiagent.ipynb`

## Testing Instructions

Ini adalah repositori pendidikan dengan contoh kod dan bukannya kod pengeluaran dengan ujian automatik. Untuk mengesahkan setup dan perubahan anda:

### Manual Testing

1. **Test Python environment:**
   ```bash
   python --version  # Mesti 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Test notebook execution:**
   ```bash
   # Tukar notebook kepada skrip dan jalankan (menguji import)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verify environment variables:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Running Individual Notebooks

Buka notebook dalam Jupyter dan laksanakan sel secara berurutan. Setiap notebook berdiri sendiri dan termasuk:
- Pernyataan import
- Pemuat konfigurasi
- Implementasi contoh agen
- Output yang dijangka dalam sel markdown

## Code Style

### Python Conventions

- **Python Version**: 3.12+
- **Code Style**: Ikut konvensi Python PEP 8 standard
- **Notebooks**: Gunakan sel markdown yang jelas untuk menerangkan konsep
- **Imports**: Kumpulkan mengikut standard library, pihak ketiga, import tempatan

### Jupyter Notebook Conventions

- Sertakan sel markdown yang deskriptif sebelum sel kod
- Tambah contoh output dalam notebook untuk rujukan
- Gunakan nama pembolehubah yang jelas yang sepadan dengan konsep pelajaran
- Pastikan susunan pelaksanaan notebook linear (sel 1 → 2 → 3...)

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

Repositori ini menggunakan Markdown untuk dokumentasi:
- Fail README.md dalam setiap folder pelajaran
- README.md utama di akar repositori
- Sistem penterjemahan automatik melalui GitHub Actions

### CI/CD Pipeline

Terletak di `.github/workflows/`:

1. **co-op-translator.yml** - Penterjemahan automatik ke 50+ bahasa
2. **welcome-issue.yml** - Menyambut pencipta isu baru
3. **welcome-pr.yml** - Menyambut penyumbang pull request baru

### Deployment

Ini adalah repositori pendidikan - tiada proses penyebaran. Pengguna:
1. Fork atau clone repositori
2. Jalankan notebook secara tempatan atau dalam GitHub Codespaces
3. Belajar dengan mengubah dan mencuba contoh

## Pull Request Guidelines

### Before Submitting

1. **Test your changes:**
   - Jalankan notebook yang terjejas sepenuhnya
   - Sahkan semua sel dilaksanakan tanpa ralat
   - Periksa bahawa output adalah sesuai

2. **Documentation updates:**
   - Kemas kini README.md jika menambah konsep baru
   - Tambah komen dalam notebook untuk kod yang kompleks
   - Pastikan sel markdown menerangkan tujuan

3. **File changes:**
   - Elakkan mengkomit fail `.env` (guna `.env.example`)
   - Jangan komit direktori `venv/` atau `__pycache__/`
   - Simpan output notebook apabila ia menunjukkan konsep
   - Keluarkan fail sementara dan notebook sandaran (`*-backup.ipynb`)

### PR Title Format

Gunakan tajuk yang deskriptif:
- `[Lesson-XX] Add new example for <concept>`
- `[Fix] Correct typo in lesson-XX README`
- `[Update] Improve code sample in lesson-XX`
- `[Docs] Update setup instructions`

### Required Checks

- Notebook harus dilaksanakan tanpa ralat
- Fail README mesti jelas dan tepat
- Ikuti corak kod sedia ada dalam repositori
- Kekalkan konsistensi dengan pelajaran lain

## Additional Notes

### Common Gotchas

1. **Python version mismatch:**
   - Pastikan Python 3.12+ digunakan
   - Sesetengah pakej mungkin tidak berfungsi dengan versi lebih lama
   - Gunakan `python3 -m venv` untuk menentukan versi Python dengan jelas

2. **Environment variables:**
   - Sentiasa cipta `.env` dari `.env.example`
   - Jangan komit fail `.env` (ia disenaraikan dalam `.gitignore`)
   - Token GitHub memerlukan kebenaran yang sesuai

3. **Package conflicts:**
   - Gunakan virtual environment baru
   - Pasang dari `requirements.txt` daripada pakej individu
   - Sesetengah notebook mungkin memerlukan pakej tambahan yang dinyatakan dalam sel markdown mereka

4. **Azure services:**
   - Perkhidmatan Azure AI memerlukan langganan aktif
   - Sesetengah ciri adalah khusus kepada rantau
   - Had lapisan percuma terpakai kepada GitHub Models

### Learning Path

Cadangan susunan pelajaran:
1. **00-course-setup** - Mula di sini untuk setup persekitaran
2. **01-intro-to-ai-agents** - Fahami asas agen AI
3. **02-explore-agentic-frameworks** - Pelajari tentang pelbagai rangka kerja
4. **03-agentic-design-patterns** - Corak reka bentuk teras
5. Teruskan melalui pelajaran bernombor secara berurutan

### Framework Selection

Pilih rangka kerja berdasarkan matlamat anda:
- **Learning/Prototyping**: Semantic Kernel + GitHub Models (percuma)
- **Multi-agent systems**: AutoGen
- **Latest features**: Microsoft Agent Framework (MAF)
- **Production deployment**: Azure AI Agent Service

### Getting Help

- Sertai the [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Semak fail README pelajaran untuk panduan khusus
- Periksa [README.md](./README.md) utama untuk gambaran kursus
- Rujuk [Course Setup](./00-course-setup/README.md) untuk arahan setup terperinci

### Contributing

Ini adalah projek pendidikan terbuka. Sumbangan dialu-alukan:
- Perbaiki contoh kod
- Betulkan salah ejaan atau ralat
- Tambah komen yang menerangkan
- Cadangkan topik pelajaran baharu
- Terjemahkan ke bahasa tambahan

Lihat [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) untuk keperluan semasa.

## Project-Specific Context

### Multi-Language Support

Repositori ini menggunakan sistem penterjemahan automatik:
- 50+ bahasa disokong
- Terjemahan di dalam direktori `/translations/<lang-code>/`
- Aliran kerja GitHub Actions mengurus kemas kini terjemahan
- Fail sumber adalah dalam Bahasa Inggeris di akar repositori

### Lesson Structure

Setiap pelajaran mengikuti corak yang konsisten:
1. Thumbnail video dengan pautan
2. Kandungan pelajaran bertulis (README.md)
3. Sampel kod dalam pelbagai rangka kerja
4. Objektif pembelajaran dan prasyarat
5. Sumber pembelajaran tambahan yang dipautkan

### Code Sample Naming

Format: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Pelajaran 4, Semantic Kernel
- `07-autogen.ipynb` - Pelajaran 7, AutoGen
- `14-python-agent-framework.ipynb` - Pelajaran 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Pelajaran 14, MAF .NET

### Special Directories

- `translated_images/` - Imej yang dilokalkan untuk terjemahan
- `images/` - Imej asal untuk kandungan Bahasa Inggeris
- `.devcontainer/` - Konfigurasi kontena pembangunan VS Code
- `.github/` - Aliran kerja GitHub Actions dan templat

### Dependencies

Pakej utama dari `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - Rangka kerja AutoGen
- `semantic-kernel` - Rangka kerja Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Perkhidmatan Azure AI
- `azure-search-documents` - Integrasi Azure AI Search
- `chromadb` - Pangkalan data vektor untuk contoh RAG
- `chainlit` - Rangka UI chat
- `browser_use` - Automasi pelayar untuk agen
- `mcp[cli]` - Sokongan Model Context Protocol
- `mem0ai` - Pengurusan memori untuk agen

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Penafian:
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha mencapai ketepatan, sila ambil perhatian bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidaktepatan. Dokumen asal dalam bahasa asalnya harus dianggap sebagai sumber rujukan yang sahih. Untuk maklumat kritikal, terjemahan profesional oleh penterjemah manusia adalah disyorkan. Kami tidak bertanggungjawab terhadap sebarang salah faham atau salah tafsiran yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->