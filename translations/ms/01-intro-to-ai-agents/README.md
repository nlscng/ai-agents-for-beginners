[![Intro to AI Agents](../../../translated_images/ms/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Klik imej di atas untuk menonton video pelajaran ini)_


# Pengenalan kepada Ejen AI dan Kes Penggunaan Ejen

Selamat datang ke kursus "Ejen AI untuk Pemula"! Kursus ini menyediakan pengetahuan asas dan contoh aplikasi untuk membina Ejen AI.

Sertai <a href="https://discord.gg/kzRShWzttr" target="_blank">Komuniti Discord Azure AI</a> untuk bertemu pelajar lain dan Pembina Ejen AI serta ajukan apa-apa soalan yang anda ada mengenai kursus ini.

Untuk memulakan kursus ini, kita mulakan dengan mendapatkan pemahaman yang lebih baik tentang apa itu Ejen AI dan bagaimana kita boleh menggunakannya dalam aplikasi dan aliran kerja yang kita bina.

## Pengenalan

Pelajaran ini merangkumi:

- Apakah Ejen AI dan apakah jenis ejen yang berbeza?
- Apakah kes penggunaan terbaik untuk Ejen AI dan bagaimana mereka boleh membantu kita?
- Apakah blok binaan asas apabila mereka bentuk Penyelesaian Berasaskan Ejen?

## Matlamat Pembelajaran
Selepas menamatkan pelajaran ini, anda sepatutnya dapat:

- Memahami konsep Ejen AI dan bagaimana ia berbeza daripada penyelesaian AI lain.
- Mengaplikasikan Ejen AI dengan cara yang paling berkesan.
- Mereka bentuk penyelesaian Berasaskan Ejen dengan produktif untuk pengguna dan pelanggan.

## Mendefinisikan Ejen AI dan Jenis Ejen AI

### Apakah Ejen AI?

Ejen AI adalah **sistem** yang membolehkan **Model Bahasa Besar (LLM)** untuk **melaksanakan tindakan** dengan meluaskan kebolehan mereka dengan memberikan LLM **akses kepada alat** dan **pengetahuan**.

Mari kita pecahkan definisi ini kepada bahagian yang lebih kecil:

- **Sistem** - Penting untuk memikirkan ejen bukan hanya sebagai satu komponen tunggal tetapi sebagai sistem yang terdiri daripada banyak komponen. Pada tahap asas, komponen Ejen AI adalah:
  - **Persekitaran** - Ruang yang ditentukan di mana Ejen AI beroperasi. Sebagai contoh, jika kita mempunyai ejen tempahan perjalanan, persekitarannya boleh menjadi sistem tempahan pelancongan yang digunakan oleh Ejen AI untuk melengkapkan tugasan.
  - **Sensor** - Persekitaran mempunyai maklumat dan memberikan maklum balas. Ejen AI menggunakan sensor untuk mengumpul dan mentafsir maklumat ini tentang keadaan semasa persekitaran. Dalam contoh Ejen Tempahan Perjalanan, sistem tempahan perjalanan boleh memberikan maklumat seperti ketersediaan hotel atau harga penerbangan.
  - **Penggerak** - Setelah Ejen AI menerima keadaan semasa persekitaran, untuk tugasan semasa ejen menentukan tindakan apa yang perlu dilakukan untuk mengubah persekitaran. Untuk ejen tempahan perjalanan, ia mungkin untuk menempah bilik yang tersedia untuk pengguna.

![What Are AI Agents?](../../../translated_images/ms/what-are-ai-agents.1ec8c4d548af601a.webp)

**Model Bahasa Besar** - Konsep ejen telah wujud sebelum penciptaan LLM. Kelebihan membina Ejen AI dengan LLM adalah keupayaan mereka untuk mentafsir bahasa manusia dan data. Keupayaan ini membolehkan LLM mentafsir maklumat persekitaran dan menentukan rancangan untuk mengubah persekitaran.

**Melaksanakan Tindakan** - Di luar sistem Ejen AI, LLM terhad kepada situasi di mana tindakan adalah menjana kandungan atau maklumat berdasarkan arahan pengguna. Dalam sistem Ejen AI, LLM boleh menyelesaikan tugasan dengan mentafsir permintaan pengguna dan menggunakan alat yang tersedia dalam persekitaran mereka.

**Akses Kepada Alat** - Alat apa yang LLM boleh akses ditentukan oleh 1) persekitaran di mana ia beroperasi dan 2) pembangun Ejen AI. Untuk contoh ejen perjalanan kita, alat ejen terhad oleh operasi yang tersedia dalam sistem tempahan, dan/atau pembangun boleh mengehadkan akses alat ejen kepada penerbangan sahaja.

**Memori+Pengetahuan** - Memori boleh bersifat jangka pendek dalam konteks perbualan antara pengguna dan ejen. Jangka panjang, di luar maklumat yang disediakan oleh persekitaran, Ejen AI juga boleh mendapatkan pengetahuan dari sistem lain, perkhidmatan, alat, dan juga ejen lain. Dalam contoh ejen perjalanan, pengetahuan ini boleh jadi maklumat mengenai keutamaan perjalanan pengguna yang terletak di dalam pangkalan data pelanggan.

### Jenis-jenis ejen

Kini kita sudah ada definisi umum mengenai Ejen AI, mari kita lihat beberapa jenis ejen tertentu dan bagaimana mereka akan digunakan dalam ejen tempahan perjalanan.

| **Jenis Ejen**               | **Penerangan**                                                                                                                       | **Contoh**                                                                                                                                                                                                                   |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ejen Refleks Mudah**       | Melakukan tindakan segera berdasarkan peraturan yang telah ditetapkan.                                                             | Ejen perjalanan mentafsir konteks e-mel dan mengarahkan aduan perjalanan kepada khidmat pelanggan.                                                                                                                           |
| **Ejen Refleks Berasaskan Model** | Melakukan tindakan berdasarkan model tentang dunia dan perubahan pada model tersebut.                                               | Ejen perjalanan memberi keutamaan laluan dengan perubahan harga yang ketara berdasarkan akses kepada data harga sejarah.                                                                                                     |
| **Ejen Berasaskan Matlamat** | Membuat rancangan untuk mencapai matlamat tertentu dengan mentafsir matlamat dan menentukan tindakan untuk mencapainya.               | Ejen perjalanan menempah perjalanan dengan menentukan keperluan perjalanan (kereta, pengangkutan awam, penerbangan) dari lokasi semasa ke destinasi.                                                                        |
| **Ejen Berasaskan Utiliti**  | Mengambil kira keutamaan dan mengimbangi trade-off secara berangka untuk menentukan cara mencapai matlamat.                       | Ejen perjalanan memaksimumkan utiliti dengan menimbang kemudahan berbanding kos semasa menempah perjalanan.                                                                                                                  |
| **Ejen Pembelajaran**        | Membaiki prestasi dari masa ke masa dengan memberi maklum balas dan melaras tindakan sewajarnya.                                      | Ejen perjalanan memperbaiki dengan menggunakan maklum balas pelanggan dari tinjauan selepas perjalanan untuk membuat pelarasan pada tempahan akan datang.                                                                     |
| **Ejen Hierarki**            | Mempunyai pelbagai ejen dalam sistem berperingkat, dengan ejen peringkat tinggi membahagikan tugasan kepada sub-tugasan untuk ejen peringkat rendah selesaikan. | Ejen perjalanan membatalkan perjalanan dengan membahagikan tugasan kepada sub-tugasan (contoh: membatalkan tempahan tertentu) dan membenarkan ejen peringkat rendah menyelesaikannya, melaporkan kembali kepada ejen peringkat tinggi. |
| **Sistem Berbilang Ejen (MAS)** | Ejen melengkapkan tugasan secara berdikari, sama ada secara kerjasama atau bersaing.                                                   | Kerjasama: Pelbagai ejen menempah perkhidmatan perjalanan khusus seperti hotel, penerbangan, dan hiburan. Persaingan: Pelbagai ejen mengurus dan bersaing atas kalendar tempahan hotel yang sama untuk menempah pelanggan ke hotel. |

## Bila Menggunakan Ejen AI

Dalam seksyen sebelumnya, kita menggunakan kes penggunaan Ejen Perjalanan untuk menjelaskan bagaimana jenis-jenis ejen yang berlainan boleh digunakan dalam senario tempahan perjalanan yang berbeza. Kita akan terus menggunakan aplikasi ini sepanjang kursus.

Mari kita lihat jenis kes penggunaan yang paling sesuai untuk digunakan dengan Ejen AI:

![When to use AI Agents?](../../../translated_images/ms/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Masalah Terbuka** - membenarkan LLM menentukan langkah yang diperlukan untuk melengkapkan tugasan kerana ia tidak boleh sentiasa diprogramkan keras ke dalam aliran kerja.
- **Proses Berbilang Langkah** - tugasan yang memerlukan tahap kerumitan di mana Ejen AI perlu menggunakan alat atau maklumat dalam banyak giliran dan bukan cuma pengambilan sekali sahaja.  
- **Pembaikan Dari Masa ke Masa** - tugasan di mana ejen boleh memperbaiki dari masa ke masa dengan menerima maklum balas sama ada dari persekitarannya atau pengguna agar dapat memberikan utiliti yang lebih baik.

Kami membincangkan lebih banyak pertimbangan penggunaan Ejen AI dalam pelajaran Membangunkan Ejen AI yang Boleh Dipercayai.

## Asas Penyelesaian Berasaskan Ejen

### Pembangunan Ejen

Langkah pertama dalam mereka bentuk sistem Ejen AI adalah untuk mentakrif alat, tindakan, dan tingkah laku. Dalam kursus ini, kita memberi tumpuan kepada menggunakan **Perkhidmatan Ejen Azure AI** untuk mentakrif Ejen kita. Ia menawarkan ciri seperti:

- Pemilihan Model Terbuka seperti OpenAI, Mistral, dan Llama
- Penggunaan Data Berlesen melalui penyedia seperti Tripadvisor
- Penggunaan alat OpenAPI 3.0 yang distandardkan

### Corak Agentic

Komunikasi dengan LLM adalah melalui arahan. Memandangkan sifat separa autonomi Ejen AI, ia tidak selalu mungkin atau diperlukan untuk memberi arahan semula secara manual selepas perubahan dalam persekitaran. Kita menggunakan **Corak Agentic** yang membenarkan kita memberi arahan kepada LLM dalam banyak langkah dengan cara yang lebih boleh diskala.

Kursus ini dibahagikan kepada beberapa corak Agentic yang popular pada masa kini.

### Rangka Kerja Agentic

Rangka kerja Agentic membolehkan pembangun melaksanakan corak agentic melalui kod. Rangka kerja ini menawarkan templat, pemalam, dan alat untuk kolaborasi Ejen AI yang lebih baik. Manfaat ini menyediakan keupayaan untuk pemerhatian yang lebih baik dan penyelesaian masalah sistem Ejen AI.

Dalam kursus ini, kita akan meneroka rangka kerja AutoGen yang berasaskan penyelidikan dan rangka kerja ejen yang sedia untuk penghasilan dari Semantic Kernel.

## Contoh Kod

- Python: [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## Ada Lebih Banyak Soalan tentang Ejen AI?

Sertai [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk berjumpa dengan pelajar lain, menghadiri sesi waktu pejabat dan mendapatkan jawapan untuk soalan Ejen AI anda.

## Pelajaran Sebelumnya

[Course Setup](../00-course-setup/README.md)

## Pelajaran Seterusnya

[Menjelajah Rangka Kerja Agentic](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk ketepatan, sila ambil perhatian bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidakakuratan. Dokumen asal dalam bahasa asalnya harus dianggap sebagai sumber yang sah. Untuk maklumat penting, terjemahan profesional oleh manusia adalah disyorkan. Kami tidak bertanggungjawab atas sebarang salah faham atau interpretasi yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->