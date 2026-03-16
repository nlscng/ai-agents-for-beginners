# Menggunakan Protokol Agentic (MCP, A2A dan NLWeb)

[![Agentic Protocols](../../../translated_images/ms/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Klik imej di atas untuk menonton video pelajaran ini)_

Dengan pertumbuhan penggunaan agen AI, begitu juga keperluan untuk protokol yang memastikan piawaian, keselamatan, dan menyokong inovasi terbuka. Dalam pelajaran ini, kita akan membincangkan 3 protokol yang bertujuan memenuhi keperluan ini - Model Context Protocol (MCP), Agent to Agent (A2A) dan Natural Language Web (NLWeb).

## Pengenalan

Dalam pelajaran ini, kita akan membincangkan:

• Bagaimana **MCP** membolehkan Agen AI mengakses alat dan data luaran untuk menyelesaikan tugasan pengguna.

• Bagaimana **A2A** membolehkan komunikasi dan kerjasama antara agen AI yang berbeza.

• Bagaimana **NLWeb** membawa antara muka bahasa semula jadi ke mana-mana laman web yang membolehkan Agen AI menemui dan berinteraksi dengan kandungan tersebut.

## Matlamat Pembelajaran

• **Kenal pasti** tujuan utama dan faedah MCP, A2A, dan NLWeb dalam konteks agen AI.

• **Jelaskan** bagaimana setiap protokol memudahkan komunikasi dan interaksi antara LLM, alat, dan agen lain.

• **Kenali** peranan berbeza yang dimainkan oleh setiap protokol dalam membina sistem agentik yang kompleks.

## Model Context Protocol

**Model Context Protocol (MCP)** adalah piawaian terbuka yang menyediakan cara piawai untuk aplikasi memberikan konteks dan alat kepada LLM. Ini membolehkan "penyesuai universal" kepada pelbagai sumber data dan alat yang boleh disambungkan oleh Agen AI secara konsisten.

Mari lihat komponen MCP, faedah berbanding penggunaan API secara langsung, dan contoh bagaimana agen AI mungkin menggunakan server MCP.

### Komponen Teras MCP

MCP beroperasi pada **senibina klien-server** dan komponen terasnya adalah:

• **Hosts** ialah aplikasi LLM (contohnya penyunting kod seperti VSCode) yang memulakan sambungan ke Server MCP.

• **Clients** ialah komponen dalam aplikasi host yang mengekalkan sambungan satu-ke-satu dengan server.

• **Servers** ialah program ringan yang mendedahkan keupayaan tertentu.

Termasuk dalam protokol adalah tiga primitif teras iaitu keupayaan Server MCP:

• **Tools**: Ini adalah tindakan atau fungsi diskret yang boleh dipanggil oleh agen AI untuk melakukan sesuatu tindakan. Contohnya, perkhidmatan cuaca mungkin mendedahkan alat "dapatkan cuaca", atau server e-dagang mungkin mendedahkan alat "beli produk". Server MCP mengiklankan nama alat, penerangan, dan skema input/output dalam senarai keupayaannya.

• **Resources**: Ini adalah item data atau dokumen bacaan sahaja yang boleh disediakan oleh server MCP, dan klien boleh mengambilnya mengikut permintaan. Contohnya termasuk kandungan fail, rekod pangkalan data, atau fail log. Resources boleh berupa teks (seperti kod atau JSON) atau binari (seperti imej atau PDF).

• **Prompts**: Ini adalah templat yang telah ditetapkan yang menyediakan cadangan prompt, membenarkan aliran kerja yang lebih kompleks.

### Faedah MCP

MCP menawarkan kelebihan ketara untuk Agen AI:

• **Penemuan Alat Dinamik**: Agen boleh menerima senarai alat yang tersedia dari server bersama penerangan tentang fungsi setiap alat. Ini berbeza dengan API tradisional yang sering memerlukan pengekodan statik untuk integrasi, jadi apa-apa perubahan API memerlukan kemas kini kod. MCP menawarkan pendekatan "integrasi sekali", membawa kepada kebolehsuaian yang lebih tinggi.

• **Kesalingoperasian Merentas LLM**: MCP berfungsi merentas pelbagai LLM, memberikan fleksibiliti untuk menukar model teras bagi penilaian prestasi yang lebih baik.

• **Keselamatan Berpiawaian**: MCP termasuk kaedah pengesahan standard, meningkatkan kebolehsisan apabila menambah akses ke lebih banyak server MCP. Ini lebih mudah berbanding menguruskan kunci dan jenis pengesahan berbeza untuk pelbagai API tradisional.

### Contoh MCP

![MCP Diagram](../../../translated_images/ms/mcp-diagram.e4ca1cbd551444a1.webp)

Bayangkan seorang pengguna ingin menempah penerbangan menggunakan pembantu AI yang dikuasakan oleh MCP.

1. **Sambungan**: Pembantu AI (klien MCP) menyambung ke server MCP yang disediakan oleh syarikat penerbangan.

2. **Penemuan Alat**: Klien bertanya kepada server MCP syarikat penerbangan, "Apakah alat yang anda ada?" Server menjawab dengan alat seperti "carian penerbangan" dan "tempah penerbangan".

3. **Pemanggilan Alat**: Anda kemudiannya meminta pembantu AI, "Sila cari penerbangan dari Portland ke Honolulu." Pembantu AI, menggunakan LLMnya, mengenal pasti bahawa ia perlu memanggil alat "carian penerbangan" dan menghantar parameter berkaitan (asal, destinasi) kepada server MCP.

4. **Pelaksanaan dan Respons**: Server MCP, bertindak sebagai pembalut, membuat panggilan sebenar ke API tempahan dalaman syarikat penerbangan. Kemudian ia menerima maklumat penerbangan (contohnya data JSON) dan menghantarnya balik kepada pembantu AI.

5. **Interaksi Lanjutan**: Pembantu AI membentangkan pilihan penerbangan. Setelah anda memilih penerbangan, pembantu itu mungkin memanggil alat "tempah penerbangan" pada server MCP yang sama, melengkapkan tempahan.

## Protokol Agent-to-Agent (A2A)

Manakala MCP menumpukan pada menyambungkan LLM ke alat, **protokol Agent-to-Agent (A2A)** mengambil satu langkah lagi dengan membolehkan komunikasi dan kerjasama antara agen AI berlainan. A2A menyambungkan agen AI merentas organisasi, persekitaran dan sistem teknologi yang berbeza untuk menyelesaikan tugasan yang dikongsi.

Kita akan meneliti komponen dan faedah A2A, bersama contoh bagaimana ia boleh digunakan dalam aplikasi perjalanan kita.

### Komponen Teras A2A

A2A menumpukan pada membolehkan komunikasi antara agen dan membolehkan mereka bekerjasama menyelesaikan sub-tugasan pengguna. Setiap komponen protokol menyumbang kepada ini:

#### Kad Agen

Serupa dengan cara server MCP berkongsi senarai alat, Kad Agen mempunyai:
- Nama Agen.
- **penerangan tugasan umum** yang dilaksanakan.
- **senarai kemahiran spesifik** dengan penerangan untuk membantu agen lain (atau pengguna manusia) memahami bila dan mengapa mereka ingin memanggil agen tersebut.
- **URL Endpoint semasa** agen.
- **versi** dan **keupayaan** agen seperti respons penstriman dan notifikasi tolak.

#### Pelaksana Agen

Pelaksana Agen bertanggungjawab untuk **menghantar konteks perbualan pengguna kepada agen jauh**, agen jauh memerlukannya untuk memahami tugasan yang perlu diselesaikan. Dalam server A2A, agen menggunakan Model Bahasa Besar (LLM) sendiri untuk memproses permintaan masuk dan melaksanakan tugasan menggunakan alat dalaman sendiri.

#### Artifak

Setelah agen jauh menyelesaikan tugasan yang diminta, produk kerjanya diwujudkan sebagai artifak. Artifak **mengandungi hasil kerja agen**, **penerangan tentang apa yang diselesaikan**, dan **konteks teks** yang dihantar melalui protokol. Selepas artifak dihantar, sambungan dengan agen jauh ditutup sehingga diperlukan lagi.

#### Antrian Acara

Komponen ini digunakan untuk **mengendalikan kemas kini dan menghantar mesej**. Ia penting dalam produksi bagi sistem agentik untuk mengelakkan sambungan antara agen ditutup sebelum tugasan selesai, terutama apabila masa penyelesaian tugasan boleh memakan masa lebih lama.

### Faedah A2A

• **Kerjasama Dipertingkatkan**: Ia membolehkan agen dari vendor dan platform berbeza berinteraksi, berkongsi konteks, dan bekerjasama, memudahkan automasi lancar merentas sistem yang biasanya tidak bersambung.

• **Fleksibiliti Pemilihan Model**: Setiap agen A2A boleh menentukan LLM mana yang digunakannya untuk memenuhi permintaan, membolehkan model yang dioptimum atau disesuaikan mengikut agen, berbeza dengan sambungan LLM tunggal dalam sesetengah senario MCP.

• **Pengautentikan Terbina Dalam**: Pengautentikan disepadukan terus ke dalam protokol A2A, menyediakan rangka kerja keselamatan yang kukuh untuk interaksi agen.

### Contoh A2A

![A2A Diagram](../../../translated_images/ms/A2A-Diagram.8666928d648acc26.webp)

Mari kita kembangkan senario tempahan perjalanan kita, kali ini menggunakan A2A.

1. **Permintaan Pengguna ke Agen Pelbagai**: Pengguna berinteraksi dengan klien/agen A2A "Ejen Perjalanan", mungkin dengan berkata, "Sila tempah satu perjalanan penuh ke Honolulu minggu depan, termasuk penerbangan, hotel, dan kereta sewa".

2. **Pengurusan oleh Ejen Perjalanan**: Ejen Perjalanan menerima permintaan kompleks ini. Ia menggunakan LLMnya untuk menilai tugasan dan menentukan ia perlu berinteraksi dengan agen khusus lain.

3. **Komunikasi Antara Agen**: Ejen Perjalanan menggunakan protokol A2A untuk menyambung ke agen hiliran, seperti "Agen Syarikat Penerbangan," "Agen Hotel," dan "Agen Kereta Sewa" yang dibuat oleh syarikat berlainan.

4. **Pelaksanaan Tugasan Bertugas**: Ejen Perjalanan menghantar tugasan khusus kepada agen khusus ini (contoh, "Cari penerbangan ke Honolulu," "Tempah hotel," "Sewa kereta"). Setiap agen khusus ini, menjalankan LLM sendiri dan menggunakan alatnya (yang mungkin server MCP itu sendiri), melaksanakan sebahagian tempahan tersebut.

5. **Respons Konsolidasi**: Setelah semua agen hiliran menyelesaikan tugasan mereka, Ejen Perjalanan menggabungkan keputusan (butiran penerbangan, pengesahan hotel, tempahan kereta sewa) dan menghantar respons gaya sembang yang lengkap kepada pengguna.

## Natural Language Web (NLWeb)

Laman web telah lama menjadi cara utama bagi pengguna mengakses maklumat dan data di seluruh internet.

Mari kita lihat komponen berbeza NLWeb, faedah NLWeb dan contoh bagaimana NLWeb berfungsi dengan melihat aplikasi perjalanan kita.

### Komponen NLWeb

- **Aplikasi NLWeb (Kod Perkhidmatan Teras)**: Sistem yang memproses soalan dalam bahasa semula jadi. Ia menghubungkan bahagian berbeza platform untuk menghasilkan respons. Anda boleh anggap ia sebagai **enjin yang menggerakkan ciri bahasa semula jadi** sebuah laman web.

- **Protokol NLWeb**: Ini adalah **set peraturan asas untuk interaksi bahasa semula jadi** dengan laman web. Ia menghantar balik respons dalam format JSON (selalunya menggunakan Schema.org). Tujuannya adalah mewujudkan asas mudah untuk “Web AI,” sama seperti HTML membolehkan perkongsian dokumen dalam talian.

- **Server MCP (Titik Akhir Model Context Protocol)**: Setiap konfigurasi NLWeb juga berfungsi sebagai **server MCP**. Ini bermaksud ia boleh **kongsi alat (seperti kaedah “ask”) dan data** dengan sistem AI lain. Dalam praktik, ini menjadikan kandungan dan kebolehan laman web boleh digunakan oleh agen AI, membenarkan laman itu menjadi sebahagian daripada “ekosistem agen” yang lebih luas.

- **Model Embedding**: Model ini digunakan untuk **menukar kandungan laman web menjadi representasi angka yang dipanggil vektor** (embedding). Vektor ini menangkap makna secara cara yang boleh dibandingkan dan dicari oleh komputer. Ia disimpan dalam pangkalan data khas, dan pengguna boleh memilih model embedding yang mahu digunakan.

- **Pangkalan Data Vektor (Mekanisme Pengambilan)**: Pangkalan data ini **menyimpan embedding kandungan laman web**. Apabila seseorang bertanya soalan, NLWeb memeriksa pangkalan data vektor untuk mencari maklumat paling relevan dengan cepat. Ia memberikan senarai pantas jawapan yang mungkin, yang disusun menurut kesamaan. NLWeb berfungsi dengan pelbagai sistem penyimpanan vektor seperti Qdrant, Snowflake, Milvus, Azure AI Search, dan Elasticsearch.

### Contoh NLWeb

![NLWeb](../../../translated_images/ms/nlweb-diagram.c1e2390b310e5fe4.webp)

Pertimbangkan laman web tempahan perjalanan kita sekali lagi, kali ini dikuasakan oleh NLWeb.

1. **Pengambilan Data**: Katalog produk laman web perjalanan sedia ada (contohnya, senarai penerbangan, penerangan hotel, pakej lawatan) diformat menggunakan Schema.org atau dimuat melalui suapan RSS. Alat NLWeb menyerap data berstruktur ini, mencipta embedding, dan menyimpannya dalam pangkalan data vektor tempatan atau jauh.

2. **Pertanyaan Bahasa Semula Jadi (Manusia)**: Pengguna melawat laman web dan, sebagai ganti melayar menu, menaip ke dalam antara muka sembang: "Cari saya hotel mesra keluarga di Honolulu dengan kolam renang untuk minggu depan".

3. **Pemprosesan NLWeb**: Aplikasi NLWeb menerima pertanyaan ini. Ia menghantar pertanyaan kepada LLM untuk kefahaman dan serentak membuat carian dalam pangkalan data vektornya untuk senarai hotel yang relevan.

4. **Keputusan Tepat**: LLM membantu mentafsir keputusan carian dari pangkalan data, mengenal pasti padanan terbaik berdasarkan kriteria "mesra keluarga," "kolam renang," dan "Honolulu," dan kemudian memformat respons dalam bahasa semula jadi. Penting untuk diperhatikan, respons merujuk kepada hotel sebenar dari katalog laman web, mengelakkan maklumat yang direka-reka.

5. **Interaksi Agen AI**: Oleh kerana NLWeb berfungsi sebagai server MCP, agen AI perjalanan luaran juga boleh bersambung ke instans NLWeb laman web ini. Agen AI tersebut kemudian boleh menggunakan kaedah `ask` MCP untuk bertanya terus ke laman: `ask("Adakah terdapat restoran mesra vegan di kawasan Honolulu yang disyorkan oleh hotel?")`. Instans NLWeb akan memproses ini, menggunakan pangkalan data maklumat restoran (jika dimuatkan), dan mengembalikan respons JSON berstruktur.

### Ada Lagi Soalan tentang MCP/A2A/NLWeb?

Sertai [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk berjumpa dengan pelajar lain, menghadiri waktu pejabat dan mendapatkan jawapan bagi soalan AI Agen anda.

## Sumber

- [MCP untuk Pemula](https://aka.ms/mcp-for-beginners)  
- [Dokumentasi MCP](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Repositori NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Panduan Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk ketepatan, sila ambil maklum bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidaktepatan. Dokumen asal dalam bahasa asalnya harus dianggap sebagai sumber rujukan yang sah. Untuk maklumat penting, terjemahan profesional oleh manusia adalah disyorkan. Kami tidak bertanggungjawab atas sebarang salah faham atau salah tafsir yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->