# Pengaturan Kursus

## Pendahuluan

Pelajaran ini akan membahas cara menjalankan contoh kode dari kursus ini.

## Bergabung dengan Pembelajar Lain dan Dapatkan Bantuan

Sebelum Anda mulai mengkloning repo Anda, bergabunglah dengan [saluran Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord) untuk mendapatkan bantuan dengan pengaturan, pertanyaan tentang kursus, atau untuk terhubung dengan pembelajar lain.

## Kloning atau Fork repositori ini

Untuk memulai, silakan kloning atau fork Repositori GitHub. Ini akan membuat versi Anda sendiri dari materi kursus sehingga Anda dapat menjalankan, menguji, dan mengubah kode!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fork repositori</a>

You should now have your own forked version of this course in the following link:

![Repositori yang di-fork](../../../translated_images/id/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (disarankan untuk workshop / Codespaces)

  >Repositori penuh bisa berukuran besar (~3 GB) jika Anda mengunduh seluruh riwayat dan semua file. Jika Anda hanya mengikuti workshop atau hanya membutuhkan beberapa folder pelajaran, a shallow clone (atau a sparse clone) menghindari sebagian besar unduhan tersebut dengan memotong riwayat dan/atau melewatkan blob.

#### Quick shallow clone — riwayat minimal, semua file

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

To clone only the latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Partial (sparse) clone — blob minimal + hanya folder terpilih

This uses partial clone and sparse-checkout (requires Git 2.25+ and recommended modern Git with partial clone support):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Traverse into the repo folder:

```bash|powershell
cd ai-agents-for-beginners
```

Then specify which folders you want (example below shows two folders):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

After cloning and verifying the files, if you only need files and want to free space (no git history), please delete the repository metadata (💀tidak dapat dikembalikan — Anda akan kehilangan semua fungsi Git: tidak ada commits, pulls, pushes, atau akses riwayat).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Menggunakan GitHub Codespaces (disarankan untuk menghindari unduhan lokal yang besar)

- Buat Codespace baru untuk repo ini melalui [GitHub UI](https://github.com/codespaces).  

- Di terminal dari codespace yang baru dibuat, jalankan salah satu perintah shallow/sparse clone di atas untuk membawa hanya folder pelajaran yang Anda butuhkan ke workspace Codespace.
- Opsional: setelah mengkloning di dalam Codespaces, hapus .git untuk mengembalikan ruang ekstra (lihat perintah penghapusan di atas).
- Catatan: Jika Anda lebih memilih membuka repo langsung di Codespaces (tanpa kloning tambahan), perhatikan Codespaces akan membangun lingkungan devcontainer dan mungkin masih menyediakan lebih banyak dari yang Anda butuhkan. Mengkloning salinan shallow di dalam Codespace baru memberi Anda kontrol lebih atas penggunaan disk.

#### Tips

- Selalu ganti URL kloning dengan fork Anda jika Anda ingin mengedit/commit.
- Jika Anda kemudian membutuhkan lebih banyak riwayat atau file, Anda dapat mengambilnya atau menyesuaikan sparse-checkout untuk memasukkan folder tambahan.

## Menjalankan Kode

Kursus ini menawarkan serangkaian Jupyter Notebook yang dapat Anda jalankan untuk mendapatkan pengalaman praktis membangun AI Agents.

The code samples use either:

**Memerlukan Akun GitHub - Gratis**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Dilabeli sebagai (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Dilabeli sebagai (autogen.ipynb)

**Memerlukan Langganan Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Dilabeli sebagai (azureaiagent.ipynb)

Kami mendorong Anda untuk mencoba ketiga jenis contoh tersebut untuk melihat mana yang paling cocok untuk Anda.

Pilihan mana pun yang Anda pilih, itu akan menentukan langkah pengaturan mana yang perlu Anda ikuti di bawah ini:

## Persyaratan

- Python 3.12+
  - **CATATAN**: Jika Anda belum menginstal Python3.12, pastikan Anda menginstalnya.  Kemudian buat venv Anda menggunakan python3.12 untuk memastikan versi yang benar diinstal dari file requirements.txt.
  
    >Contoh

    Buat direktori venv Python:

    ```bash|powershell
    python -m venv venv
    ```

    Kemudian aktifkan lingkungan venv untuk:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Untuk contoh kode yang menggunakan .NET, pastikan Anda menginstal [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) atau lebih baru. Kemudian, periksa versi .NET SDK yang terpasang:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Akun GitHub - Untuk Akses ke GitHub Models Marketplace
- Langganan Azure - Untuk Akses ke Microsoft Foundry
- Akun Microsoft Foundry - Untuk Akses ke Azure AI Agent Service

Kami telah menyertakan file `requirements.txt` di root repositori ini yang berisi semua paket Python yang diperlukan untuk menjalankan contoh kode.

Anda dapat menginstalnya dengan menjalankan perintah berikut di terminal Anda pada root repositori:

```bash|powershell
pip install -r requirements.txt
```

Kami menyarankan membuat lingkungan virtual Python untuk menghindari konflik dan masalah.

## Mengatur VSCode

Pastikan Anda menggunakan versi Python yang benar di VSCode.

![gambar](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Pengaturan untuk Contoh yang Menggunakan GitHub Models 

### Langkah 1: Ambil GitHub Personal Access Token (PAT) Anda

Kursus ini memanfaatkan GitHub Models Marketplace, menyediakan akses gratis ke Large Language Models (LLMs) yang akan Anda gunakan untuk membangun AI Agents.

Untuk menggunakan GitHub Models, Anda perlu membuat sebuah [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Ini dapat dilakukan dengan membuka <a href="https://github.com/settings/personal-access-tokens" target="_blank">pengaturan Personal Access Tokens</a> di Akun GitHub Anda.

Harap ikuti prinsip [Prinsip Hak Istimewa Minimum](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) saat membuat token Anda. Ini berarti Anda hanya harus memberikan token izin yang diperlukan untuk menjalankan contoh kode dalam kursus ini.

1. Select the `Fine-grained tokens` option on the left side of your screen by traversing to the **Developer settings**

   ![Pengaturan Pengembang](../../../translated_images/id/profile_developer_settings.410a859fe749c755.webp)

   Then select `Generate new token`.

   ![Hasilkan Token](../../../translated_images/id/fga_new_token.1c1a234afe202ab3.webp)

2. Enter a descriptive name for your token that reflects its purpose, making it easy to identify later.

    🔐 Rekomendasi Durasi Token

    Durasi yang direkomendasikan: 30 days
    Untuk postur keamanan yang lebih baik, Anda dapat memilih periode yang lebih pendek—seperti 7 days 🛡️
    Ini adalah cara yang bagus untuk menetapkan target pribadi dan menyelesaikan kursus saat momentum belajar Anda tinggi 🚀.

    ![Nama Token dan Kedaluwarsa](../../../translated_images/id/token-name-expiry-date.a095fb0de6386864.webp)

3. Limit the token's scope to your fork of this repository.

    ![Batasi cakupan ke repositori fork](../../../translated_images/id/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restrict the token's permissions: Under **Permissions**, click **Account** tab, and click the "+ Add permissions" button. A dropdown will appear. Please search for **Models** and check the box for it.

    ![Tambah Izin Models](../../../translated_images/id/add_models_permissions.c0c44ed8b40fc143.webp)

5. Verify the permissions required before generating the token. ![Verifikasi Izin](../../../translated_images/id/verify_permissions.06bd9e43987a8b21.webp)

6. Before generating the token, ensure you are ready to store the token in a secure place like a password manager vault, as it will not be shown again after you create it. ![Simpan Token dengan Aman](../../../translated_images/id/store_token_securely.08ee2274c6ad6caf.webp)

Copy your new token that you have just created. You will now add this to your `.env` file included in this course.

### Langkah 2: Buat File `.env` Anda

To create your `.env` file run the following command in your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `GITHUB_TOKEN` field.

![Kolom Token GitHub](../../../translated_images/id/github_token_field.20491ed3224b5f4a.webp)

You should now be able to run the code samples of this course.

## Pengaturan untuk Contoh yang Menggunakan Microsoft Foundry dan Azure AI Agent Service

### Langkah 1: Ambil Endpoint Proyek Azure Anda


Follow the steps to creating a hub and project in Azure AI Foundry found here: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Once you have created your project, you will need to retrieve the connection string for your project.

This can be done by going to the **Overview** page of your project in the Microsoft Foundry portal.

![String Koneksi Proyek](../../../translated_images/id/project-endpoint.8cf04c9975bbfbf1.webp)

### Langkah 2: Buat File `.env` Anda

To create your `.env` file run the following command in your terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

This will copy the example file and create a `.env` in your directory and where you fill in the values for the environment variables.

With your token copied, open the `.env` file in your favorite text editor and paste your token into the `PROJECT_ENDPOINT` field.

### Langkah 3: Masuk ke Azure

As a security best practice, we'll use [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) to authenticate to Azure OpenAI with Microsoft Entra ID. 

Next, open a terminal and run `az login --use-device-code` to sign in to your Azure account.

Once you've logged in, select your subscription in the terminal.

## Variabel Lingkungan Tambahan - Azure Search dan Azure OpenAI 

For the Agentic RAG Lesson - Lesson 5 - there are samples that use Azure Search and Azure OpenAI.

If you want to run these samples, you will need to add the following environment variables to your `.env` file:

### Halaman Overview (Proyek)

- `AZURE_SUBSCRIPTION_ID` - Periksa **Project details** pada halaman **Overview** proyek Anda.

- `AZURE_AI_PROJECT_NAME` - Lihat di bagian atas halaman **Overview** proyek Anda.

- `AZURE_OPENAI_SERVICE` - Temukan ini di tab **Included capabilities** untuk **Azure OpenAI Service** pada halaman **Overview**.

### Pusat Manajemen

- `AZURE_OPENAI_RESOURCE_GROUP` - Buka **Project properties** pada halaman **Overview** dari **Management Center**.

- `GLOBAL_LLM_SERVICE` - Di bawah **Connected resources**, temukan nama koneksi **Azure AI Services**. Jika tidak tercantum, periksa **Azure portal** di bawah grup sumber daya Anda untuk nama resource AI Services.

### Halaman Models + Endpoints

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Pilih model embedding Anda (mis., `text-embedding-ada-002`) dan catat **Deployment name** dari detail model.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Pilih model chat Anda (mis., `gpt-4o-mini`) dan catat **Deployment name** dari detail model.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - Cari **Azure AI services**, klik itu, lalu buka **Resource Management**, **Keys and Endpoint**, gulir ke bawah ke "Azure OpenAI endpoints", dan salin yang bertuliskan "Language APIs".

- `AZURE_OPENAI_API_KEY` - Dari layar yang sama, salin KEY 1 atau KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Temukan resource **Azure AI Search** Anda, klik itu, dan lihat **Overview**.

- `AZURE_SEARCH_API_KEY` - Lalu buka **Settings** dan kemudian **Keys** untuk menyalin kunci admin primer atau sekunder.

### Halaman Eksternal

- `AZURE_OPENAI_API_VERSION` - Kunjungi halaman [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) di bawah **Latest GA API release**.

### Menyiapkan autentikasi tanpa kunci

Rather than hardcode your credentials, we'll use a keyless connection with Azure OpenAI. To do so, we'll import `DefaultAzureCredential` and later call the `DefaultAzureCredential` function to get the credential.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Terjebak di Suatu Tempat?
Jika Anda mengalami masalah menjalankan pengaturan ini, bergabunglah ke <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord Komunitas Azure AI</a> atau <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">buat sebuah issue</a>.

## Pelajaran Selanjutnya

Anda sekarang siap menjalankan kode untuk kursus ini. Selamat belajar lebih banyak tentang dunia Agen AI! 

[Pengantar Agen AI dan Kasus Penggunaan Agen](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berupaya mencapai akurasi, harap diperhatikan bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang berwenang. Untuk informasi yang bersifat kritis, disarankan menggunakan terjemahan profesional oleh penerjemah manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau salah tafsir yang timbul dari penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->