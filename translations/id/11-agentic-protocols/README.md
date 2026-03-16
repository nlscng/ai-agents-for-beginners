# Menggunakan Protokol Agenik (MCP, A2A dan NLWeb)

[![Protokol Agenik](../../../translated_images/id/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Klik gambar di atas untuk menonton video pelajaran ini)_

Seiring berkembangnya penggunaan agen AI, kebutuhan akan protokol yang menjamin standarisasi, keamanan, dan mendukung inovasi terbuka juga meningkat. Dalam pelajaran ini, kita akan membahas 3 protokol yang bertujuan memenuhi kebutuhan ini - Model Context Protocol (MCP), Agent to Agent (A2A) dan Natural Language Web (NLWeb).

## Pendahuluan

Dalam pelajaran ini, kita akan membahas:

• How **MCP** allows AI Agents to access external tools and data to complete user tasks.

•  How **A2A** enables communication and collaboration between different AI agents.

• How **NLWeb** brings natural language interfaces to any website enabling AI Agents to discover and interact with the content.

## Tujuan Pembelajaran

• **Mengidentifikasi** tujuan inti dan manfaat MCP, A2A, dan NLWeb dalam konteks agen AI.

• **Menjelaskan** bagaimana masing-masing protokol memfasilitasi komunikasi dan interaksi antara LLM, alat, dan agen lain.

• **Mengenali** peran berbeda yang dimainkan setiap protokol dalam membangun sistem agenik yang kompleks.

## Protokol Konteks Model

The **Protokol Konteks Model (MCP)** adalah standar terbuka yang menyediakan cara terstandarisasi bagi aplikasi untuk menyediakan konteks dan alat kepada LLM. Ini memungkinkan sebuah "adaptor universal" ke berbagai sumber data dan alat yang dapat dihubungkan Agen AI secara konsisten.

Mari kita lihat komponen MCP, manfaat dibandingkan penggunaan API langsung, dan contoh bagaimana agen AI mungkin menggunakan server MCP.

### Komponen Inti MCP

MCP beroperasi pada **arsitektur klien-server** dan komponen inti adalah:

• **Hosts** adalah aplikasi LLM (misalnya editor kode seperti VSCode) yang memulai koneksi ke Server MCP.

• **Clients** adalah komponen dalam aplikasi host yang menjaga koneksi satu-ke-satu dengan server.

• **Servers** adalah program ringan yang mengekspos kapabilitas tertentu.

Dalam protokol ini terdapat tiga primitif inti yang merupakan kapabilitas Server MCP:

• **Tools**: Ini adalah aksi atau fungsi diskret yang dapat dipanggil agen AI untuk melakukan suatu tindakan. Misalnya, layanan cuaca mungkin mengekspos alat "get weather", atau server e-commerce mungkin mengekspos alat "purchase product". Server MCP mengumumkan nama setiap alat, deskripsi, dan skema input/outputnya dalam daftar kapabilitas mereka.

• **Resources**: Ini adalah item data atau dokumen hanya-baca yang dapat disediakan oleh server MCP, dan klien dapat mengambilnya sesuai permintaan. Contohnya termasuk isi file, catatan basis data, atau file log. Resources bisa berupa teks (seperti kode atau JSON) atau biner (seperti gambar atau PDF).

• **Prompts**: Ini adalah template yang telah ditentukan sebelumnya yang menyediakan saran prompt, memungkinkan alur kerja yang lebih kompleks.

### Manfaat MCP

MCP menawarkan keuntungan signifikan bagi Agen AI:

• **Dynamic Tool Discovery**: Agen dapat secara dinamis menerima daftar alat yang tersedia dari server beserta deskripsi fungsi mereka. Ini berbeda dengan API tradisional, yang sering membutuhkan pengkodean statis untuk integrasi, sehingga setiap perubahan API memerlukan pembaruan kode. MCP menawarkan pendekatan "integrate once", yang menghasilkan kemampuan beradaptasi yang lebih besar.

• **Interoperability Across LLMs**: MCP bekerja lintas berbagai LLM, memberikan fleksibilitas untuk mengganti model inti untuk dievaluasi demi performa yang lebih baik.

• **Standardized Security**: MCP mencakup metode autentikasi standar, meningkatkan skalabilitas saat menambahkan akses ke server MCP tambahan. Ini lebih sederhana dibandingkan mengelola berbagai kunci dan jenis autentikasi untuk berbagai API tradisional.

### Contoh MCP

![Diagram MCP](../../../translated_images/id/mcp-diagram.e4ca1cbd551444a1.webp)

Bayangkan seorang pengguna ingin memesan penerbangan menggunakan asisten AI yang didukung oleh MCP.

1. **Koneksi**: Asisten AI (klien MCP) terhubung ke server MCP yang disediakan oleh maskapai.

2. **Penemuan Alat**: Klien menanyakan ke server MCP maskapai, "Alat apa saja yang tersedia?" Server merespons dengan alat seperti "search flights" dan "book flights".

3. **Pemanggilan Alat**: Kemudian Anda meminta asisten AI, "Tolong cari penerbangan dari Portland ke Honolulu." Asisten AI, menggunakan LLM-nya, mengidentifikasi bahwa ia perlu memanggil alat "search flights" dan mengirim parameter relevan (origin, destination) ke server MCP.

4. **Eksekusi dan Respon**: Server MCP, bertindak sebagai pembungkus, melakukan panggilan nyata ke API pemesanan internal maskapai. Kemudian menerima informasi penerbangan (misalnya data JSON) dan mengirimkannya kembali ke asisten AI.

5. **Interaksi Selanjutnya**: Asisten AI menyajikan opsi penerbangan. Setelah Anda memilih penerbangan, asisten mungkin memanggil alat "book flight" pada server MCP yang sama, menyelesaikan pemesanan.

## Protokol Agen-ke-Agen (A2A)

While MCP focuses on connecting LLMs to tools, the **Agent-to-Agent (A2A) protocol** takes it a step further by enabling communication and collaboration between different AI agents. A2A connects AI agents across different organizations, environments and tech stacks to complete a shared task.

Kita akan memeriksa komponen dan manfaat A2A, beserta contoh bagaimana hal ini dapat diterapkan dalam aplikasi perjalanan kita.

### Komponen Inti A2A

A2A berfokus pada memungkinkan komunikasi antar agen dan membuatnya bekerja sama untuk menyelesaikan subtugas pengguna. Setiap komponen protokol berkontribusi pada hal ini:

#### Kartu Agen

Serupa dengan bagaimana server MCP membagikan daftar alat, sebuah Kartu Agen memiliki:
- Nama Agen .
- A **deskripsi tugas umum** yang diselesaikannya.
- A **daftar keterampilan spesifik** dengan deskripsi untuk membantu agen lain (atau bahkan pengguna manusia) memahami kapan dan mengapa mereka ingin memanggil agen tersebut.
- The **current Endpoint URL** of the agent
- The **version** and **capabilities** of the agent such as streaming responses and push notifications.

#### Eksekutor Agen

Eksekutor Agen bertanggung jawab untuk **mengirimkan konteks obrolan pengguna ke agen jarak jauh**, agen jarak jauh membutuhkan ini untuk memahami tugas yang harus diselesaikan. Dalam server A2A, sebuah agen menggunakan Large Language Model (LLM) miliknya sendiri untuk mengurai permintaan yang masuk dan mengeksekusi tugas menggunakan alat internalnya sendiri.

#### Artefak

Saat agen jarak jauh menyelesaikan tugas yang diminta, produk kerjanya dibuat sebagai artefak. Sebuah artefak **memuat hasil kerja agen**, sebuah **deskripsi tentang apa yang diselesaikan**, dan **konteks teks** yang dikirim melalui protokol. Setelah artefak dikirim, koneksi dengan agen jarak jauh ditutup sampai diperlukan lagi.

#### Antrian Peristiwa

Komponen ini digunakan untuk **menangani pembaruan dan meneruskan pesan**. Ini sangat penting dalam produksi untuk sistem agenik agar mencegah koneksi antar agen tertutup sebelum tugas selesai, terutama ketika waktu penyelesaian tugas dapat memakan waktu lama.

### Manfaat A2A

• **Enhanced Collaboration**: Memungkinkan agen dari vendor dan platform berbeda untuk berinteraksi, berbagi konteks, dan bekerja sama, memfasilitasi otomatisasi mulus di seluruh sistem yang biasanya terpisah.

• **Model Selection Flexibility**: Setiap agen A2A dapat menentukan LLM yang digunakannya untuk melayani permintaan, memungkinkan model yang dioptimalkan atau disesuaikan per agen, berbeda dari satu koneksi LLM tunggal pada beberapa skenario MCP.

• **Built-in Authentication**: Autentikasi diintegrasikan langsung ke dalam protokol A2A, menyediakan kerangka keamanan yang kuat untuk interaksi agen.

### Contoh A2A

![Diagram A2A](../../../translated_images/id/A2A-Diagram.8666928d648acc26.webp)

Mari kita kembangkan skenario pemesanan perjalanan kita, tetapi kali ini menggunakan A2A.

1. **Permintaan Pengguna ke Multi-Agen**: Seorang pengguna berinteraksi dengan klien/agen A2A "Agen Perjalanan", misalnya dengan mengatakan, "Tolong pesan seluruh perjalanan ke Honolulu untuk minggu depan, termasuk penerbangan, hotel, dan mobil sewaan".

2. **Orkestrasi oleh Agen Perjalanan**: Agen Perjalanan menerima permintaan kompleks ini. Ia menggunakan LLM-nya untuk menganalisis tugas dan menentukan bahwa ia perlu berinteraksi dengan agen khusus lainnya.

3. **Komunikasi Antar-Agen**: Agen Perjalanan kemudian menggunakan protokol A2A untuk terhubung ke agen hilir, seperti "Agen Maskapai", "Agen Hotel", dan "Agen Penyewaan Mobil" yang dibuat oleh perusahaan berbeda.

4. **Pelaksanaan Tugas yang Didelegasikan**: Agen Perjalanan mengirimkan tugas spesifik ke agen-agennya yang khusus (misalnya, "Cari penerbangan ke Honolulu", "Pesan hotel", "Sewa mobil"). Masing-masing agen spesialis ini, menjalankan LLM mereka sendiri dan memanfaatkan alat internalnya (yang bisa saja berupa server MCP sendiri), melaksanakan bagian spesifik dari pemesanan.

5. **Respons Terkonsolidasi**: Setelah semua agen hilir menyelesaikan tugas mereka, Agen Perjalanan mengompilasi hasilnya (detail penerbangan, konfirmasi hotel, pemesanan sewa mobil) dan mengirimkan respons bergaya obrolan yang komprehensif kembali kepada pengguna.

## Natural Language Web (NLWeb)

Situs web sejak lama menjadi cara utama bagi pengguna untuk mengakses informasi dan data di seluruh internet.

Mari kita lihat komponen berbeda dari NLWeb, manfaat NLWeb dan contoh bagaimana NLWeb bekerja dengan melihat aplikasi perjalanan kita.

### Komponen NLWeb

- **NLWeb Application (Core Service Code)**: Sistem yang memproses pertanyaan berbahasa alami. Ia menghubungkan bagian-bagian platform untuk membuat respons. Anda dapat memikirkannya sebagai **mesin yang memberi tenaga pada fitur bahasa alami** sebuah situs web.

- **NLWeb Protocol**: Ini adalah **set aturan dasar untuk interaksi berbahasa alami** dengan sebuah situs web. Ia mengembalikan respons dalam format JSON (sering menggunakan Schema.org). Tujuannya adalah menciptakan fondasi sederhana untuk "AI Web," dengan cara yang sama seperti HTML memungkinkan berbagi dokumen secara online.

- **MCP Server (Model Context Protocol Endpoint)**: Setiap pengaturan NLWeb juga berfungsi sebagai **server MCP**. Ini berarti ia dapat **membagikan alat (seperti metode “ask”) dan data** dengan sistem AI lainnya. Dalam praktiknya, ini membuat konten dan kemampuan situs web dapat digunakan oleh agen AI, memungkinkan situs menjadi bagian dari ekosistem agen yang lebih luas.

- **Embedding Models**: Model-model ini digunakan untuk **mengonversi konten situs web menjadi representasi numerik yang disebut vektor** (embeddings). Vektor-vektor ini menangkap makna sedemikian rupa sehingga komputer dapat membandingkan dan mencari. Mereka disimpan dalam basis data khusus, dan pengguna dapat memilih model embedding yang ingin digunakan.

- **Vector Database (Retrieval Mechanism)**: Basis data ini **menyimpan embeddings dari konten situs web**. Ketika seseorang mengajukan pertanyaan, NLWeb memeriksa basis data vektor untuk dengan cepat menemukan informasi paling relevan. Ia memberikan daftar jawaban yang diperingkat berdasarkan kesamaan. NLWeb bekerja dengan berbagai sistem penyimpanan vektor seperti Qdrant, Snowflake, Milvus, Azure AI Search, dan Elasticsearch.

### Contoh NLWeb

![NLWeb](../../../translated_images/id/nlweb-diagram.c1e2390b310e5fe4.webp)

Pertimbangkan kembali situs web pemesanan perjalanan kita, tetapi kali ini, ia didukung oleh NLWeb.

1. **Data Ingestion**: Katalog produk situs perjalanan yang ada (mis., daftar penerbangan, deskripsi hotel, paket tur) diformat menggunakan Schema.org atau dimuat melalui feed RSS. Alat NLWeb mengambil data terstruktur ini, membuat embeddings, dan menyimpannya di basis data vektor lokal atau jarak jauh.

2. **Natural Language Query (Human)**: Seorang pengguna mengunjungi situs dan, alih-alih menavigasi menu, mengetik ke antarmuka obrolan: "Temukan hotel ramah keluarga di Honolulu dengan kolam renang untuk minggu depan".

3. **Pemrosesan NLWeb**: Aplikasi NLWeb menerima kueri ini. Ia mengirimkan kueri ke LLM untuk pemahaman dan secara bersamaan mencari basis data vektornya untuk daftar hotel relevan.

4. **Hasil Akurat**: LLM membantu menginterpretasikan hasil pencarian dari basis data, mengidentifikasi kecocokan terbaik berdasarkan kriteria "ramah keluarga," "kolam renang," dan "Honolulu," lalu memformat respons berbahasa alami. Yang penting, respons merujuk pada hotel nyata dari katalog situs, menghindari informasi yang dibuat-buat.

5. **Interaksi Agen AI**: Karena NLWeb berfungsi sebagai server MCP, agen perjalanan AI eksternal juga dapat terhubung ke instance NLWeb situs ini. Agen AI tersebut kemudian bisa menggunakan metode MCP `ask` untuk menanyakan langsung ke situs: `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")`. Instance NLWeb akan memproses ini, memanfaatkan basis data informasi restoran (jika dimuat), dan mengembalikan respons JSON terstruktur.

### Masih Punya Pertanyaan tentang MCP/A2A/NLWeb?

Bergabunglah dengan [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk bertemu pelajar lain, menghadiri jam kantor dan mendapatkan jawaban untuk pertanyaan Agen AI Anda.

## Sumber Daya

- [MCP untuk Pemula](https://aka.ms/mcp-for-beginners)  
- [Dokumentasi MCP](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Repo NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Panduan Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Penafian:
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berupaya mencapai ketepatan, harap diingat bahwa terjemahan otomatis dapat mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang sah. Untuk informasi yang bersifat krusial, disarankan menggunakan terjemahan profesional oleh penerjemah manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau salah tafsir yang timbul dari penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->