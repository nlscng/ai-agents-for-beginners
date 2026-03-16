# AGENTS.md

## Gambaran Proyek

Repositori ini berisi "AI Agents untuk Pemula" - kursus edukasi komprehensif yang mengajarkan segala yang dibutuhkan untuk membangun AI Agents. Kursus ini terdiri dari lebih dari 15 pelajaran yang mencakup dasar-dasar, pola desain, framework, dan penerapan produksi dari AI agents.

**Teknologi Utama:**
- Python 3.12+
- Jupyter Notebooks untuk pembelajaran interaktif
- Framework AI: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Layanan Azure AI: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (tingkat gratis tersedia)

**Arsitektur:**
- Struktur berbasis pelajaran (direktori 00-15+)
- Setiap pelajaran berisi: dokumentasi README, contoh kode (notebook Jupyter), dan gambar
- Dukungan multi-bahasa melalui sistem terjemahan otomatis
- Beberapa opsi framework per pelajaran (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Perintah Setup

### Prasyarat
- Python 3.12 atau lebih tinggi
- Akun GitHub (untuk GitHub Models - tingkat gratis)
- Langganan Azure (opsional, untuk layanan Azure AI)

### Setup Awal

1. **Clone atau fork repositori:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # ATAU
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Buat dan aktifkan virtual environment Python:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Di Windows: venv\Scripts\activate
   ```

3. **Instal dependensi:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Atur variabel lingkungan:**
   ```bash
   cp .env.example .env
   # Edit .env dengan kunci API dan titik akhir Anda
   ```

### Variabel Lingkungan yang Diperlukan

Untuk **GitHub Models (Gratis)**:
- `GITHUB_TOKEN` - Token akses personal dari GitHub

Untuk **Layanan Azure AI** (opsional):
- `PROJECT_ENDPOINT` - Endpoint proyek Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - Kunci API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL endpoint Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Nama deployment model chat
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Nama deployment embeddings
- Konfigurasi Azure tambahan seperti yang ditunjukkan di `.env.example`

## Alur Kerja Pengembangan

### Menjalankan Jupyter Notebooks

Setiap pelajaran berisi beberapa notebook Jupyter untuk framework berbeda:

1. **Mulai Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Masuk ke direktori pelajaran** (misal, `01-intro-to-ai-agents/code_samples/`)

3. **Buka dan jalankan notebook:**
   - `*-semantic-kernel.ipynb` - Menggunakan framework Semantic Kernel
   - `*-autogen.ipynb` - Menggunakan framework AutoGen
   - `*-python-agent-framework.ipynb` - Menggunakan Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Menggunakan Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Menggunakan Azure AI Agent Service

### Bekerja dengan Berbagai Framework

**Semantic Kernel + GitHub Models:**
- Tingkat gratis tersedia dengan akun GitHub
- Baik untuk pembelajaran dan eksperimen
- Pola file: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Tingkat gratis tersedia dengan akun GitHub
- Kemampuan orkestrasi multi-agent
- Pola file: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Framework terbaru dari Microsoft
- Tersedia di Python dan .NET
- Pola file: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Membutuhkan langganan Azure
- Fitur siap produksi
- Pola file: `*-azureaiagent.ipynb`

## Instruksi Pengujian

Ini adalah repositori edukasi dengan contoh kode bukan kode produksi dengan pengujian otomatis. Untuk memverifikasi setup dan perubahan Anda:

### Pengujian Manual

1. **Uji lingkungan Python:**
   ```bash
   python --version  # Harus 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Uji eksekusi notebook:**
   ```bash
   # Konversi notebook ke skrip dan jalankan (mengujikan impor)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verifikasi variabel lingkungan:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Menjalankan Notebook Individu

Buka notebook di Jupyter dan jalankan sel secara berurutan. Setiap notebook bersifat mandiri dan mencakup:
- Pernyataan impor
- Pemuatan konfigurasi
- Implementasi contoh agent
- Output yang diharapkan dalam sel markdown

## Gaya Kode

### Konvensi Python

- **Versi Python**: 3.12+
- **Gaya Kode**: Ikuti konvensi standar Python PEP 8
- **Notebook**: Gunakan sel markdown yang jelas untuk menjelaskan konsep
- **Impor**: Kelompokkan berdasarkan pustaka standar, pihak ketiga, lokal

### Konvensi Jupyter Notebook

- Sertakan sel markdown deskriptif sebelum sel kode
- Tambahkan contoh output dalam notebook untuk referensi
- Gunakan nama variabel yang jelas dan sesuai konsep pelajaran
- Jaga urutan eksekusi notebook secara linear (sel 1 → 2 → 3…)

### Organisasi Berkas

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

## Build dan Deployment

### Membuat Dokumentasi

Repositori ini menggunakan Markdown untuk dokumentasi:
- Berkas README.md di setiap folder pelajaran
- README.md utama di root repositori
- Sistem terjemahan otomatis via GitHub Actions

### Pipeline CI/CD

Terletak di `.github/workflows/`:

1. **co-op-translator.yml** - Terjemahan otomatis ke 50+ bahasa
2. **welcome-issue.yml** - Menyambut pembuat issue baru
3. **welcome-pr.yml** - Menyambut kontributor pull request baru

### Deployment

Ini adalah repositori edukasi - tidak ada proses deployment. Pengguna:
1. Fork atau clone repositori
2. Jalankan notebook secara lokal atau di GitHub Codespaces
3. Belajar dengan memodifikasi dan bereksperimen dengan contoh

## Panduan Pull Request

### Sebelum Mengirim

1. **Uji perubahan Anda:**
   - Jalankan notebook yang terpengaruh secara lengkap
   - Pastikan semua sel berjalan tanpa error
   - Cek bahwa output sesuai

2. **Perubahan dokumentasi:**
   - Perbarui README.md jika menambah konsep baru
   - Tambahkan komentar di notebook untuk kode kompleks
   - Pastikan sel markdown menjelaskan maksud

3. **Perubahan berkas:**
   - Hindari commit berkas `.env` (gunakan `.env.example`)
   - Jangan commit direktori `venv/` atau `__pycache__/`
   - Pertahankan output notebook saat menunjukkan konsep
   - Hapus berkas sementara dan backup notebook (`*-backup.ipynb`)

### Format Judul PR

Gunakan judul deskriptif:
- `[Lesson-XX] Tambah contoh baru untuk <konsep>`
- `[Fix] Perbaiki typo di lesson-XX README`
- `[Update] Tingkatkan contoh kode di lesson-XX`
- `[Docs] Perbarui instruksi setup`

### Pemeriksaan yang Diperlukan

- Notebook harus berjalan tanpa error
- Berkas README harus jelas dan akurat
- Ikuti pola kode yang sudah ada di repositori
- Jaga konsistensi dengan pelajaran lain

## Catatan Tambahan

### Hal Umum yang Perlu Diperhatikan

1. **Versi Python tidak sesuai:**
   - Pastikan gunakan Python 3.12+
   - Beberapa paket mungkin tidak kompatibel dengan versi lama
   - Gunakan `python3 -m venv` untuk menentukan versi Python secara eksplisit

2. **Variabel lingkungan:**
   - Selalu buat `.env` dari `.env.example`
   - Jangan commit berkas `.env` (sudah ada di `.gitignore`)
   - Token GitHub memerlukan izin yang tepat

3. **Konflik paket:**
   - Gunakan virtual environment baru
   - Instal dari `requirements.txt` daripada paket individual
   - Beberapa notebook mungkin butuh paket tambahan yang disebutkan dalam sel markdown mereka

4. **Layanan Azure:**
   - Layanan Azure AI memerlukan langganan aktif
   - Beberapa fitur spesifik wilayah
   - Batasan tingkat gratis berlaku untuk GitHub Models

### Jalur Pembelajaran

Rekomendasi urutan pelajaran:
1. **00-course-setup** - Mulai di sini untuk setup lingkungan
2. **01-intro-to-ai-agents** - Pahami dasar agent AI
3. **02-explore-agentic-frameworks** - Pelajari berbagai framework
4. **03-agentic-design-patterns** - Pola desain inti
5. Lanjutkan pelajaran bernomor secara berurutan

### Pemilihan Framework

Pilih framework sesuai tujuan Anda:
- **Pembelajaran/Prototyping**: Semantic Kernel + GitHub Models (gratis)
- **Sistem multi-agent**: AutoGen
- **Fitur terbaru**: Microsoft Agent Framework (MAF)
- **Deployment produksi**: Azure AI Agent Service

### Mendapatkan Bantuan

- Bergabung dengan [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Tinjau berkas README pelajaran untuk panduan spesifik
- Cek [README.md](./README.md) utama untuk gambaran kursus
- Lihat [Course Setup](./00-course-setup/README.md) untuk instruksi setup rinci

### Kontribusi

Ini adalah proyek edukasi terbuka. Kontribusi disambut:
- Tingkatkan contoh kode
- Perbaiki typo atau kesalahan
- Tambahkan komentar penjelas
- Sarankan topik pelajaran baru
- Terjemahkan ke bahasa lain

Lihat [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) untuk kebutuhan saat ini.

## Konteks Khusus Proyek

### Dukungan Multi-Bahasa

Repositori ini menggunakan sistem terjemahan otomatis:
- Mendukung lebih dari 50 bahasa
- Terjemahan ada di direktori `/translations/<kode-bahasa>/`
- Workflow GitHub Actions menangani pembaruan terjemahan
- Berkas sumber dalam bahasa Inggris di root repositori

### Struktur Pelajaran

Setiap pelajaran mengikuti pola konsisten:
1. Thumbnail video dengan tautan
2. Konten pelajaran tertulis (README.md)
3. Contoh kode dalam beberapa framework
4. Tujuan pembelajaran dan prasyarat
5. Sumber belajar tambahan yang ditautkan

### Penamaan Contoh Kode

Format: `<nomor-pelajaran>-<nama-framework>.ipynb`
- `04-semantic-kernel.ipynb` - Pelajaran 4, Semantic Kernel
- `07-autogen.ipynb` - Pelajaran 7, AutoGen
- `14-python-agent-framework.ipynb` - Pelajaran 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Pelajaran 14, MAF .NET

### Direktori Khusus

- `translated_images/` - Gambar yang sudah dilokalisasi untuk terjemahan
- `images/` - Gambar asli untuk konten bahasa Inggris
- `.devcontainer/` - Konfigurasi container pengembangan VS Code
- `.github/` - Workflow dan template GitHub Actions

### Dependensi

Paket utama dari `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - framework AutoGen
- `semantic-kernel` - framework Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - layanan Azure AI
- `azure-search-documents` - integrasi Azure AI Search
- `chromadb` - basis data vektor untuk contoh RAG
- `chainlit` - framework UI chat
- `browser_use` - otomasi browser untuk agents
- `mcp[cli]` - dukungan Model Context Protocol
- `mem0ai` - manajemen memori untuk agents

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berupaya untuk keakuratan, harap diperhatikan bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidaktepatan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang berwenang. Untuk informasi penting, disarankan menggunakan terjemahan profesional oleh manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau penafsiran yang salah yang timbul dari penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->