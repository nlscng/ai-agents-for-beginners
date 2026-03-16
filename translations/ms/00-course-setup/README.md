# Persediaan Kursus

## Pengenalan

Pelajaran ini akan membincangkan cara menjalankan contoh kod bagi kursus ini.

## Sertai Pelajar Lain dan Dapatkan Bantuan

Sebelum anda mula menyalin repo anda, sertai [saluran Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord) untuk mendapatkan bantuan mengenai persediaan, sebarang soalan tentang kursus, atau untuk berhubung dengan pelajar lain.

## Salin atau Fork Repo ini

Untuk memulakan, sila salin atau fork Repositori GitHub. Ini akan menghasilkan versi sendiri bahan kursus supaya anda boleh menjalankan, menguji, dan mengubahsuai kod!

Ini boleh dilakukan dengan klik pautan <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">fork repo</a>

Anda kini sepatutnya mempunyai versi fork repo kursus ini pada pautan berikut:

![Forked Repo](../../../translated_images/ms/forked-repo.33f27ca1901baa6a.webp)

### Shallow Clone (disarankan untuk bengkel / Codespaces)

  >Repositori penuh boleh menjadi besar (~3 GB) apabila anda memuat turun sejarah penuh dan semua fail. Jika anda hanya menghadiri bengkel atau hanya memerlukan beberapa folder pelajaran, shallow clone (atau sparse clone) mengelakkan kebanyakan muat turun tersebut dengan memendekkan sejarah dan/atau mengelak blob.

#### Quick shallow clone — sejarah minimum, semua fail

Gantikan `<your-username>` dalam arahan di bawah dengan URL fork anda (atau URL upstream jika anda lebih suka).

Untuk menyalin hanya sejarah komit terkini (muat turun kecil):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Untuk clone cawangan tertentu:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Clone separa (sparse) — blob minimum + hanya folder terpilih

Ini menggunakan clone separa dan sparse-checkout (memerlukan Git 2.25+ dan disarankan Git moden dengan sokongan clone separa):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Masuk ke dalam folder repo:

```bash|powershell
cd ai-agents-for-beginners
```

Kemudian nyatakan folder yang anda ingin dapatkan (contoh di bawah menunjukkan dua folder):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Selepas menyalin dan mengesahkan fail, jika anda hanya perlukan fail dan mahu kosongkan ruang (tanpa sejarah git), sila padam metadata repositori (💀tidak boleh dipulihkan — anda akan kehilangan semua fungsi Git: tiada komit, tarik, tolak, atau akses sejarah).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Menggunakan GitHub Codespaces (disarankan untuk elak muat turun besar tempatan)

- Cipta Codespace baru untuk repo ini melalui [GitHub UI](https://github.com/codespaces).  

- Dalam terminal codespace yang baru dicipta, jalankan salah satu arahan shallow/sparse clone di atas untuk membawa hanya folder pelajaran yang anda perlukan ke dalam workspace Codespace.
- Pilihan: selepas menyalin dalam Codespaces, buang .git untuk mendapatkan semula ruang tambahan (lihat arahan buang di atas).
- Nota: Jika anda lebih suka buka repo terus dalam Codespaces (tanpa clone tambahan), berhati-hati kerana Codespaces akan membina persekitaran devcontainer dan mungkin masih sediakan lebih banyak daripada yang anda perlukan. Clone salinan shallow dalam Codespace baru memberi kawalan lebih baik ke atas penggunaan cakera.

#### Petua

- Sentiasa gantikan URL clone dengan fork anda jika mahu sunting/komit.
- Jika anda kemudian perlukan lebih sejarah atau fail, anda boleh fetch atau laraskan sparse-checkout untuk tambah folder tambahan.

## Menjalankan Kod

Kursus ini menawarkan siri Jupyter Notebooks yang boleh anda jalankan untuk mendapatkan pengalaman praktikal membina AI Agents.

Contoh kod menggunakan sama ada:

**Memerlukan Akaun GitHub - Percuma**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Ditandai sebagai (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Ditandai sebagai (autogen.ipynb)

**Memerlukan Langganan Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Ditandai sebagai (azureaiagent.ipynb)

Kami menggalakkan anda mencuba ketiga-tiga jenis contoh untuk melihat yang mana sesuai untuk anda.

Pilihan mana pun anda pilih, ia akan menentukan langkah persediaan yang perlu anda ikuti di bawah:

## Keperluan

- Python 3.12+
  - **NOTA**: Jika anda belum memasang Python3.12, pastikan anda memasangnya. Kemudian cipta venv menggunakan python3.12 untuk memastikan versi yang betul dipasang dari fail requirements.txt.
  
    >Contoh

    Cipta direktori Python venv:

    ```bash|powershell
    python -m venv venv
    ```

    Kemudian aktifkan persekitaran venv untuk:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Untuk contoh kod yang menggunakan .NET, pastikan anda memasang [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) atau lebih baru. Kemudian, semak versi .NET SDK yang anda pasang:

    ```bash|powershell
    dotnet --list-sdks
    ```

- Akaun GitHub - Untuk Akses GitHub Models Marketplace
- Langganan Azure - Untuk Akses Microsoft Foundry
- Akaun Microsoft Foundry - Untuk Akses Azure AI Agent Service

Kami sertakan fail `requirements.txt` dalam root repositori ini yang mengandungi semua pakej Python yang diperlukan untuk menjalankan contoh kod.

Anda boleh memasangnya dengan menjalankan arahan berikut dalam terminal pada root repositori:

```bash|powershell
pip install -r requirements.txt
```

Kami mengesyorkan mencipta persekitaran maya Python untuk mengelakkan sebarang konflik dan isu.

## Persediaan VSCode

Pastikan anda menggunakan versi Python yang betul dalam VSCode.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Persediaan untuk Contoh yang menggunakan GitHub Models 

### Langkah 1: Dapatkan Token Akses Peribadi GitHub (PAT) Anda

Kursus ini menggunakan GitHub Models Marketplace, menyediakan akses percuma kepada Model Bahasa Besar (LLMs) yang akan anda gunakan untuk membina AI Agents.

Untuk menggunakan GitHub Models, anda perlu mencipta [Token Akses Peribadi GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Ini boleh dilakukan dengan pergi ke <a href="https://github.com/settings/personal-access-tokens" target="_blank">tetapan Token Akses Peribadi</a> dalam Akaun GitHub anda.

Sila ikuti [Prinsip Keistimewaan Minimum](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) semasa mencipta token anda. Ini bermakna anda hanya perlu beri token kebenaran yang diperlukan untuk menjalankan contoh kod dalam kursus ini.

1. Pilih pilihan `Fine-grained tokens` di sebelah kiri skrin anda dengan pergi ke **Developer settings**

   ![Developer settings](../../../translated_images/ms/profile_developer_settings.410a859fe749c755.webp)

   Kemudian pilih `Generate new token`.

   ![Generate Token](../../../translated_images/ms/fga_new_token.1c1a234afe202ab3.webp)

2. Masukkan nama deskriptif untuk token anda yang mencerminkan tujuannya, supaya mudah dikenali kemudian.

    🔐 Cadangan Tempoh Token

    Tempoh disyorkan: 30 hari
    Untuk tahap keselamatan lebih tinggi, anda boleh pilih tempoh lebih singkat—seperti 7 hari 🛡️
    Ini cara yang bagus untuk menetapkan sasaran peribadi dan menamatkan kursus semasa momentum pembelajaran tinggi 🚀.

    ![Token Name and Expiration](../../../translated_images/ms/token-name-expiry-date.a095fb0de6386864.webp)

3. Hadkan skop token kepada fork repositori ini.

    ![Limit scope to fork repository](../../../translated_images/ms/token_repository_limit.924ade5e11d9d8bb.webp)

4. Hadkan kebenaran token: Di bawah **Permissions**, klik tab **Account**, dan klik butang "+ Add permissions". Satu dropdown akan muncul. Sila cari **Models** dan tandakan kotak untuknya.

    ![Add Models Permission](../../../translated_images/ms/add_models_permissions.c0c44ed8b40fc143.webp)

5. Sahkan kebenaran yang diperlukan sebelum menjana token. ![Verify Permissions](../../../translated_images/ms/verify_permissions.06bd9e43987a8b21.webp)

6. Sebelum menjana token, pastikan anda sedia menyimpan token itu di tempat selamat seperti pengurus kata laluan, kerana ia tidak akan ditunjukkan lagi selepas penciptaan. ![Store Token Securely](../../../translated_images/ms/store_token_securely.08ee2274c6ad6caf.webp)

Salin token baru yang anda baru sahaja cipta. Anda akan tambah ini ke fail `.env` yang disertakan dalam kursus ini.

### Langkah 2: Cipta Fail `.env` Anda

Untuk mencipta fail `.env` jalankan arahan berikut dalam terminal anda.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Ini akan menyalin fail contoh dan mencipta `.env` dalam direktori anda yang mana anda mengisi nilai bagi pemboleh ubah persekitaran.

Dengan token yang disalin, buka fail `.env` dalam penyunting teks kegemaran anda dan tampal token ke medan `GITHUB_TOKEN`.

![GitHub Token Field](../../../translated_images/ms/github_token_field.20491ed3224b5f4a.webp)

Anda kini sepatutnya dapat menjalankan contoh kod kursus ini.

## Persediaan untuk Contoh yang menggunakan Microsoft Foundry dan Azure AI Agent Service

### Langkah 1: Dapatkan Endpoint Projek Azure Anda


Ikuti langkah untuk mencipta hub dan projek di Azure AI Foundry yang boleh didapati di sini: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Setelah anda mencipta projek, anda perlu dapatkan string sambungan untuk projek anda.

Ini boleh dilakukan dengan pergi ke halaman **Overview** projek anda di portal Microsoft Foundry.

![Project Connection String](../../../translated_images/ms/project-endpoint.8cf04c9975bbfbf1.webp)

### Langkah 2: Cipta Fail `.env` Anda

Untuk mencipta fail `.env` jalankan arahan berikut dalam terminal anda.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Ini akan menyalin fail contoh dan mencipta `.env` dalam direktori anda yang mana anda mengisi nilai bagi pemboleh ubah persekitaran.

Dengan token yang disalin, buka fail `.env` dalam penyunting teks kegemaran anda dan tampal token ke medan `PROJECT_ENDPOINT`.

### Langkah 3: Log masuk ke Azure

Sebagai amalan keselamatan terbaik, kita akan menggunakan [pengesahan tanpa kunci](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) untuk mengesahkan ke Azure OpenAI dengan Microsoft Entra ID.

Seterusnya, buka terminal dan jalankan `az login --use-device-code` untuk log masuk ke akaun Azure anda.

Setelah log masuk, pilih langganan anda dalam terminal.

## Pemboleh Ubah Persekitaran Tambahan - Azure Search dan Azure OpenAI 

Untuk Pelajaran Agentic RAG - Pelajaran 5 - terdapat contoh yang menggunakan Azure Search dan Azure OpenAI.

Jika anda mahu jalankan contoh ini, anda perlu tambah pemboleh ubah persekitaran berikut ke fail `.env` anda:

### Halaman Gambaran Keseluruhan (Projek)

- `AZURE_SUBSCRIPTION_ID` - Semak **Project details** pada halaman **Overview** projek anda.

- `AZURE_AI_PROJECT_NAME` - Lihat di atas halaman **Overview** projek anda.

- `AZURE_OPENAI_SERVICE` - Cari ini di tab **Included capabilities** untuk **Azure OpenAI Service** pada halaman **Overview**.

### Pusat Pengurusan

- `AZURE_OPENAI_RESOURCE_GROUP` - Pergi ke **Project properties** pada halaman **Overview** di **Management Center**.

- `GLOBAL_LLM_SERVICE` - Di bawah **Connected resources**, cari nama sambungan **Azure AI Services**. Jika tidak disenaraikan, semak di **Azure portal** dalam kumpulan sumber anda untuk nama sumber AI Services.

### Halaman Model + Endpoint

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Pilih model embedding anda (contoh, `text-embedding-ada-002`) dan catat **Deployment name** dari butiran model.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Pilih model chat anda (contoh, `gpt-4o-mini`) dan catat **Deployment name** dari butiran model.

### Portal Azure

- `AZURE_OPENAI_ENDPOINT` - Cari **Azure AI services**, klik padanya, kemudian pergi ke **Resource Management**, **Keys and Endpoint**, tatal ke bawah ke "Azure OpenAI endpoints", dan salin yang bertulis "Language APIs".

- `AZURE_OPENAI_API_KEY` - Dari skrin yang sama, salin KEY 1 atau KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Cari sumber **Azure AI Search** anda, klik, dan lihat **Overview**.

- `AZURE_SEARCH_API_KEY` - Kemudian pergi ke **Settings** dan kemudian **Keys** untuk salin kunci pentadbir utama atau sekunder.

### Laman Web Luaran

- `AZURE_OPENAI_API_VERSION` - Lawati halaman [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) di bawah **Latest GA API release**.

### Persediaan pengesahan tanpa kunci

Daripada hardcode kelayakan anda, kita akan menggunakan sambungan tanpa kunci dengan Azure OpenAI. Untuk itu, kita akan import `DefaultAzureCredential` dan kemudian panggil fungsi `DefaultAzureCredential` untuk dapatkan kelayakan.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Tersangkut di Mana-mana?
Jika anda menghadapi sebarang masalah menjalankan persediaan ini, sertai <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Community Discord</a> kami atau <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">buat isu</a>.

## Pelajaran Seterusnya

Anda kini bersedia untuk menjalankan kod untuk kursus ini. Selamat belajar lebih lanjut mengenai dunia Ejen AI!

[Pengenalan kepada Ejen AI dan Kes Penggunaan Ejen](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk ketepatan, sila ambil perhatian bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidaktepatan. Dokumen asal dalam bahasa asalnya hendaklah dianggap sebagai sumber utama yang sah. Untuk maklumat penting, terjemahan profesional oleh manusia adalah disyorkan. Kami tidak bertanggungjawab terhadap sebarang salah faham atau salah tafsir yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->