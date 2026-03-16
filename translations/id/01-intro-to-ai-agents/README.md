[![Pengantar Agen AI](../../../translated_images/id/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Klik gambar di atas untuk menonton video pelajaran ini)_


# Pengenalan Agen AI dan Studi Kasus Penggunaan Agen

Selamat datang di kursus "Agen AI untuk Pemula"! Kursus ini memberikan pengetahuan dasar dan contoh terapan untuk membangun Agen AI.

Bergabunglah dengan <a href="https://discord.gg/kzRShWzttr" target="_blank">Komunitas Discord Azure AI</a> untuk bertemu pelajar lain dan Pembuat Agen AI serta ajukan pertanyaan apa pun yang Anda miliki tentang kursus ini.

Untuk memulai kursus ini, kita mulai dengan memahami lebih baik apa itu Agen AI dan bagaimana kita dapat menggunakannya dalam aplikasi dan alur kerja yang kita bangun.

## Pengenalan

Pelajaran ini membahas:

- Apa itu Agen AI dan apa saja jenis-jenis agen?
- Kasus penggunaan apa yang paling cocok untuk Agen AI dan bagaimana mereka dapat membantu kita?
- Apa saja blok bangunan dasar saat merancang Solusi Agenik?

## Tujuan Pembelajaran
Setelah menyelesaikan pelajaran ini, Anda seharusnya dapat:

- Memahami konsep Agen AI dan bagaimana perbedaannya dengan solusi AI lainnya.
- Menerapkan Agen AI secara paling efisien.
- Mendesain solusi Agenik secara produktif untuk pengguna dan pelanggan.

## Mendefinisikan Agen AI dan Jenis-Jenis Agen AI

### Apa itu Agen AI?

Agen AI adalah **sistem** yang memungkinkan **Large Language Models(LLMs)** untuk **melakukan tindakan** dengan memperluas kemampuan mereka dengan memberikan LLM **akses ke alat** dan **pengetahuan**.

Mari uraikan definisi ini menjadi bagian yang lebih kecil:

- **Sistem** - Penting untuk memikirkan agen bukan hanya sebagai satu komponen tetapi sebagai sistem dari banyak komponen. Pada tingkat dasar, komponen Agen AI adalah:
  - **Lingkungan** - Ruang yang ditentukan di mana Agen AI beroperasi. Misalnya, jika kita memiliki Agen Pemesanan Perjalanan, lingkungan tersebut bisa berupa sistem pemesanan perjalanan yang digunakan Agen AI untuk menyelesaikan tugas.
  - **Sensor** - Lingkungan memiliki informasi dan memberikan umpan balik. Agen AI menggunakan sensor untuk mengumpulkan dan menginterpretasikan informasi ini tentang keadaan saat ini dari lingkungan. Dalam contoh Agen Pemesanan Perjalanan, sistem pemesanan perjalanan dapat memberikan informasi seperti ketersediaan hotel atau harga tiket pesawat.
  - **Aktuator** - Setelah Agen AI menerima keadaan saat ini dari lingkungan, untuk tugas saat ini agen menentukan tindakan apa yang harus dilakukan untuk mengubah lingkungan. Untuk agen pemesanan perjalanan, mungkin adalah memesan kamar yang tersedia untuk pengguna.

![Apa Itu Agen AI?](../../../translated_images/id/what-are-ai-agents.1ec8c4d548af601a.webp)

**Large Language Models** - Konsep agen sudah ada sebelum penciptaan LLMs. Keuntungan membangun Agen AI dengan LLMs adalah kemampuan mereka untuk menginterpretasikan bahasa manusia dan data. Kemampuan ini memungkinkan LLMs untuk menginterpretasikan informasi lingkungan dan mendefinisikan rencana untuk mengubah lingkungan.

**Melakukan Tindakan** - Di luar sistem Agen AI, LLMs terbatas pada situasi di mana tindakan adalah menghasilkan konten atau informasi berdasarkan prompt pengguna. Di dalam sistem Agen AI, LLMs dapat menyelesaikan tugas dengan menginterpretasikan permintaan pengguna dan menggunakan alat yang tersedia di lingkungan mereka.

**Akses ke Alat** - Alat apa yang dapat diakses oleh LLM ditentukan oleh 1) lingkungan tempatnya beroperasi dan 2) pengembang Agen AI. Untuk contoh agen perjalanan kami, alat agen dibatasi oleh operasi yang tersedia dalam sistem pemesanan, dan/atau pengembang dapat membatasi akses alat agen ke penerbangan.

**Memori+Pengetahuan** - Memori dapat bersifat jangka pendek dalam konteks percakapan antara pengguna dan agen. Dalam jangka panjang, di luar informasi yang disediakan oleh lingkungan, Agen AI juga dapat mengambil pengetahuan dari sistem lain, layanan, alat, dan bahkan agen lain. Dalam contoh agen perjalanan, pengetahuan ini bisa berupa informasi tentang preferensi perjalanan pengguna yang berada di basis data pelanggan.

### Jenis-Jenis Agen

Sekarang kita memiliki definisi umum tentang Agen AI, mari lihat beberapa jenis agen spesifik dan bagaimana mereka akan diterapkan pada agen pemesanan perjalanan.

| **Tipe Agen**                | **Deskripsi**                                                                                                                       | **Contoh**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Simple Reflex Agents**      | Melakukan tindakan segera berdasarkan aturan yang telah ditentukan.                                                                                  | Agen perjalanan menginterpretasikan konteks email dan meneruskan keluhan perjalanan ke layanan pelanggan.                                                                                                                          |
| **Model-Based Reflex Agents** | Melakukan tindakan berdasarkan model dunia dan perubahan pada model tersebut.                                                              | Agen perjalanan memprioritaskan rute dengan perubahan harga signifikan berdasarkan akses ke data harga historis.                                                                                                             |
| **Goal-Based Agents**         | Membuat rencana untuk mencapai tujuan tertentu dengan menginterpretasikan tujuan dan menentukan tindakan untuk mencapainya.                                  | Agen perjalanan memesan perjalanan dengan menentukan pengaturan perjalanan yang diperlukan (mobil, transportasi umum, penerbangan) dari lokasi saat ini ke tujuan.                                                                                |
| **Utility-Based Agents**      | Mempertimbangkan preferensi dan menimbang kompromi secara numerik untuk menentukan cara mencapai tujuan.                                               | Agen perjalanan memaksimalkan utilitas dengan menimbang kenyamanan vs. biaya saat memesan perjalanan.                                                                                                                                          |
| **Learning Agents**           | Meningkat dari waktu ke waktu dengan merespons umpan balik dan menyesuaikan tindakan sesuai.                                                        | Agen perjalanan meningkat dengan menggunakan umpan balik pelanggan dari survei pasca-perjalanan untuk melakukan penyesuaian terhadap pemesanan di masa depan.                                                                                                               |
| **Hierarchical Agents**       | Menampilkan beberapa agen dalam sistem bertingkat, dengan agen tingkat atas membagi tugas menjadi subtugas untuk agen tingkat bawah menyelesaikannya. | Agen perjalanan membatalkan perjalanan dengan membagi tugas menjadi subtugas (misalnya, membatalkan pemesanan tertentu) dan meminta agen tingkat bawah menyelesaikannya, melaporkan kembali ke agen tingkat atas.                                     |
| **Multi-Agent Systems (MAS)** | Agen menyelesaikan tugas secara independen, baik secara kooperatif maupun kompetitif.                                                           | Kooperatif: Beberapa agen memesan layanan perjalanan spesifik seperti hotel, penerbangan, dan hiburan. Kompetitif: Beberapa agen mengelola dan bersaing atas kalender pemesanan hotel bersama untuk memasukkan pelanggan ke hotel tersebut. |

## Kapan Menggunakan Agen AI

Di bagian sebelumnya, kami menggunakan kasus penggunaan Agen Perjalanan untuk menjelaskan bagaimana berbagai jenis agen dapat digunakan dalam skenario pemesanan perjalanan yang berbeda. Kita akan terus menggunakan aplikasi ini sepanjang kursus.

Mari lihat jenis-jenis kasus penggunaan yang paling cocok untuk Agen AI:

![Kapan Menggunakan Agen AI?](../../../translated_images/id/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Masalah Terbuka** - memungkinkan LLM menentukan langkah-langkah yang diperlukan untuk menyelesaikan tugas karena tidak selalu dapat dikodekan secara statis ke dalam alur kerja.
- **Proses Multi-Langkah** - tugas yang memerlukan tingkat kompleksitas di mana Agen AI perlu menggunakan alat atau informasi selama beberapa langkah alih-alih pengambilan sekali jalan.  
- **Peningkatan dari Waktu ke Waktu** - tugas di mana agen dapat meningkat dari waktu ke waktu dengan menerima umpan balik dari lingkungan atau pengguna untuk memberikan utilitas yang lebih baik.

Kami membahas lebih banyak pertimbangan penggunaan Agen AI dalam pelajaran Membangun Agen AI yang Dapat Dipercaya.

## Dasar-Dasar Solusi Agenik

### Pengembangan Agen

Langkah pertama dalam merancang sistem Agen AI adalah mendefinisikan alat, tindakan, dan perilaku. Dalam kursus ini, kita fokus pada penggunaan **Azure AI Agent Service** untuk mendefinisikan Agen kita. Layanan ini menawarkan fitur seperti:

- Pemilihan Model Terbuka seperti OpenAI, Mistral, dan Llama
- Penggunaan Data Berlisensi melalui penyedia seperti Tripadvisor
- Penggunaan alat OpenAPI 3.0 yang distandarisasi

### Pola Agenik

Komunikasi dengan LLM dilakukan melalui prompt. Mengingat sifat semi-otonom Agen AI, tidak selalu mungkin atau diperlukan untuk memprompt ulang LLM secara manual setelah perubahan di lingkungan. Kita menggunakan **Pola Agenik** yang memungkinkan kita memprompt LLM selama beberapa langkah dengan cara yang lebih dapat diskalakan.

Kursus ini dibagi menjadi beberapa pola Agenik populer saat ini.

### Kerangka Agenik

Kerangka Agenik memungkinkan pengembang mengimplementasikan pola agenik melalui kode. Kerangka ini menawarkan template, plugin, dan alat untuk kolaborasi Agen AI yang lebih baik. Manfaat ini memberikan kemampuan untuk observabilitas dan pemecahan masalah sistem Agen AI yang lebih baik.

Dalam kursus ini, kita akan mengeksplorasi kerangka AutoGen yang berbasis penelitian dan kerangka kerja Agent yang siap produksi dari Semantic Kernel.

## Contoh Kode

- Python: [Kerangka Agen](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Kerangka Agen](./code_samples/01-dotnet-agent-framework.md)

## Masih Punya Pertanyaan tentang Agen AI?

Bergabunglah dengan [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk bertemu pelajar lain, menghadiri jam kantor dan mendapatkan jawaban atas pertanyaan Anda tentang Agen AI.

## Pelajaran Sebelumnya

[Pengaturan Kursus](../00-course-setup/README.md)

## Pelajaran Berikutnya

[Menjelajahi Kerangka Agenik](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Penafian:
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI Co-op Translator (https://github.com/Azure/co-op-translator). Meskipun kami berupaya menjaga ketepatan, harap diperhatikan bahwa terjemahan otomatis dapat mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang otoritatif. Untuk informasi yang bersifat kritis, disarankan menggunakan jasa penerjemah profesional. Kami tidak bertanggung jawab atas kesalahpahaman atau salah tafsir yang timbul dari penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->