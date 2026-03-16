[![Desain Multi-Agen](../../../translated_images/id/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Klik gambar di atas untuk melihat video pelajaran ini)_

# Pola desain multi-agen

Begitu Anda mulai mengerjakan proyek yang melibatkan banyak agen, Anda harus mempertimbangkan pola desain multi-agen. Namun, mungkin tidak langsung jelas kapan harus beralih ke multi-agen dan apa keuntungannya.

## Pendahuluan

Dalam pelajaran ini, kita akan mencari jawaban untuk pertanyaan berikut:

- Apa saja skenario di mana multi-agen dapat diterapkan?
- Apa keuntungan menggunakan multi-agen dibanding hanya satu agen tunggal yang melakukan banyak tugas?
- Apa saja blok bangunan untuk mengimplementasikan pola desain multi-agen?
- Bagaimana kita dapat melihat bagaimana beberapa agen berinteraksi satu sama lain?

## Tujuan Pembelajaran

Setelah pelajaran ini, Anda harus bisa:

- Mengidentifikasi skenario di mana multi-agen bisa diterapkan
- Mengenali keuntungan menggunakan multi-agen dibanding satu agen tunggal.
- Memahami blok bangunan dalam mengimplementasikan pola desain multi-agen.

Apa gambaran yang lebih besar?

*Multi-agen adalah pola desain yang memungkinkan beberapa agen bekerja sama mencapai tujuan bersama*.

Pola ini banyak digunakan di berbagai bidang, termasuk robotika, sistem otonom, dan komputasi terdistribusi.

## Skenario di Mana Multi-Agen Dapat Diterapkan

Jadi, skenario apa yang merupakan kasus penggunaan bagus untuk memakai multi-agen? Jawabannya adalah ada banyak skenario di mana penggunaan banyak agen bermanfaat terutama dalam kasus berikut:

- **Beban kerja besar**: Beban kerja besar dapat dibagi menjadi tugas-tugas lebih kecil dan dialokasikan ke agen berbeda, memungkinkan pemrosesan paralel dan penyelesaian lebih cepat. Contoh ini adalah pada tugas pemrosesan data besar.
- **Tugas kompleks**: Tugas kompleks, seperti beban kerja besar, dapat dipecah menjadi subtugas lebih kecil dan dialokasikan ke agen berbeda, masing-masing berspesialisasi pada aspek tertentu dari tugas. Contoh bagus adalah pada kendaraan otonom di mana agen berbeda menangani navigasi, deteksi rintangan, dan komunikasi dengan kendaraan lain.
- **Keahlian beragam**: Agen berbeda dapat memiliki keahlian beragam, memungkinkan mereka menangani aspek berbeda dari tugas lebih efektif dibandingkan satu agen tunggal. Contoh dalam bidang kesehatan di mana agen mengelola diagnostik, rencana perawatan, dan pemantauan pasien.

## Keuntungan Menggunakan Multi-Agen Dibanding Agen Tunggal

Sistem agen tunggal bisa bekerja baik untuk tugas sederhana, tetapi untuk tugas lebih kompleks, menggunakan banyak agen dapat memberikan beberapa keuntungan:

- **Spesialisasi**: Setiap agen dapat berspesialisasi untuk tugas tertentu. Kurangnya spesialisasi dalam satu agen berarti agen itu bisa melakukan semua hal tapi mungkin bingung apa yang harus dilakukan saat menghadapi tugas kompleks. Misalnya, agen itu mungkin akhirnya melakukan tugas yang sebenarnya bukan keahliannya.
- **Skalabilitas**: Lebih mudah untuk menskalakan sistem dengan menambah agen daripada membebani satu agen tunggal.
- **Toleransi Kesalahan**: Jika satu agen gagal, agen lain dapat terus berfungsi, memastikan keandalan sistem.

Mari kita ambil contoh, kita memesan perjalanan untuk pengguna. Sistem agen tunggal harus menangani semua aspek proses pemesanan perjalanan, mulai dari mencari penerbangan hingga memesan hotel dan mobil sewaan. Untuk mencapainya dengan agen tunggal, agen tersebut perlu memiliki alat untuk menangani semua tugas ini. Ini bisa menjadikan sistem kompleks dan monolitik yang sulit dipelihara dan diskalakan. Sistem multi-agen, di sisi lain, bisa punya agen berbeda yang berspesialisasi dalam mencari penerbangan, memesan hotel, dan mobil sewaan. Ini membuat sistem lebih modular, mudah dipelihara, dan skalabel.

Bandingkan dengan biro perjalanan yang dijalankan sebagai toko keluarga versus biro perjalanan yang dijalankan sebagai waralaba. Toko keluarga hanya punya satu agen yang menangani semua aspek pemesanan perjalanan, sementara waralaba punya agen berbeda yang menangani aspek berbeda dari proses tersebut.

## Blok Bangunan dalam Mengimplementasikan Pola Desain Multi-Agen

Sebelum Anda dapat mengimplementasikan pola desain multi-agen, Anda harus memahami blok bangunan yang membentuk pola tersebut.

Mari kita perjelas dengan kembali melihat contoh pemesanan perjalanan untuk pengguna. Dalam hal ini, blok bangunan termasuk:

- **Komunikasi Agen**: Agen untuk mencari penerbangan, memesan hotel, dan mobil sewaan perlu berkomunikasi dan berbagi informasi tentang preferensi dan batasan pengguna. Anda perlu memutuskan protokol dan metode untuk komunikasi ini. Artinya secara konkret agen pencari penerbangan perlu berkomunikasi dengan agen pemesan hotel untuk memastikan hotel dipesan untuk tanggal yang sama dengan penerbangan. Itu berarti agen harus berbagi info tanggal perjalanan pengguna, sehingga Anda perlu menentukan *agen mana yang berbagi info dan bagaimana mereka berbagi info*.
- **Mekanisme Koordinasi**: Agen perlu mengoordinasikan tindakan mereka untuk memastikan preferensi dan batasan pengguna terpenuhi. Contohnya, preferensi pengguna bisa ingin hotel dekat bandara sedangkan batasannya mobil sewaan hanya tersedia di bandara. Ini berarti agen pemesan hotel harus berkoordinasi dengan agen pemesan mobil untuk memastikan preferensi dan batasan pengguna terpenuhi. Ini berarti Anda perlu menentukan *bagaimana agen mengoordinasikan tindakan mereka*.
- **Arsitektur Agen**: Agen perlu memiliki struktur internal untuk mengambil keputusan dan belajar dari interaksinya dengan pengguna. Ini berarti agen pencari penerbangan perlu memiliki struktur internal untuk memutuskan penerbangan mana yang direkomendasikan kepada pengguna. Ini berarti Anda perlu menentukan *bagaimana agen membuat keputusan dan belajar dari interaksi dengan pengguna*. Contohnya bagaimana agen belajar dan berkembang bisa menggunakan model pembelajaran mesin untuk merekomendasikan penerbangan berdasarkan preferensi pengguna sebelumnya.
- **Visibilitas Interaksi Multi-Agen**: Anda harus memiliki visibilitas tentang bagaimana beberapa agen berinteraksi satu sama lain. Ini berarti Anda perlu memiliki alat dan teknik untuk melacak aktivitas dan interaksi agen. Ini bisa berupa alat log dan monitoring, alat visualisasi, dan metrik performa.
- **Pola Multi-Agen**: Ada pola berbeda untuk mengimplementasikan sistem multi-agen, seperti arsitektur terpusat, terdesentralisasi, dan hibrida. Anda perlu menentukan pola yang paling sesuai dengan kasus penggunaan Anda.
- **Manusia dalam loop**: Dalam kebanyakan kasus, Anda akan melibatkan manusia dalam loop dan Anda perlu menginstruksikan agen kapan harus meminta intervensi manusia. Ini bisa berupa pengguna meminta hotel atau penerbangan spesifik yang tidak direkomendasikan oleh agen atau meminta konfirmasi sebelum memesan penerbangan atau hotel.

## Visibilitas Interaksi Multi-Agen

Penting untuk memiliki visibilitas tentang bagaimana beberapa agen saling berinteraksi. Visibilitas ini penting untuk debugging, optimisasi, dan memastikan efektivitas sistem secara keseluruhan. Untuk mencapainya, Anda perlu alat dan teknik melacak aktivitas dan interaksi agen. Ini bisa berupa alat logging dan monitoring, alat visualisasi, dan metrik performa.

Misalnya, dalam kasus pemesanan perjalanan untuk pengguna, Anda bisa memiliki dashboard yang menunjukkan status masing-masing agen, preferensi dan batasan pengguna, serta interaksi antar agen. Dashboard ini bisa menampilkan tanggal perjalanan pengguna, penerbangan yang direkomendasikan oleh agen penerbangan, hotel yang direkomendasikan oleh agen hotel, dan mobil sewaan yang direkomendasikan oleh agen mobil sewaan. Ini memberi Anda gambaran jelas tentang bagaimana agen berinteraksi satu sama lain dan apakah preferensi serta batasan pengguna terpenuhi.

Mari kita lihat masing-masing aspek ini lebih detail.

- **Alat Logging dan Monitoring**: Anda ingin mencatat setiap tindakan yang diambil agen. Entri log bisa menyimpan informasi tentang agen yang mengambil tindakan, tindakan yang dilakukan, waktu tindakan tersebut, dan hasil dari tindakan itu. Informasi ini bisa digunakan untuk debugging, optimisasi, dan lainnya.

- **Alat Visualisasi**: Alat visualisasi dapat membantu Anda melihat interaksi antar agen dengan cara yang lebih intuitif. Misalnya, Anda bisa memiliki grafik yang menunjukkan aliran informasi antar agen. Ini membantu mengidentifikasi kemacetan, ketidakefisienan, dan isu lain dalam sistem.

- **Metrik Performa**: Metrik performa membantu Anda melacak efektivitas sistem multi-agen. Misalnya, Anda bisa melacak waktu yang dibutuhkan untuk menyelesaikan tugas, jumlah tugas yang diselesaikan per satuan waktu, dan akurasi rekomendasi yang dibuat agen. Informasi ini membantu mengidentifikasi area yang perlu perbaikan dan mengoptimalkan sistem.

## Pola Multi-Agen

Mari kita selami beberapa pola konkret yang bisa kita gunakan untuk membuat aplikasi multi-agen. Berikut beberapa pola menarik yang patut dipertimbangkan:

### Obrolan grup

Pola ini berguna saat Anda ingin membuat aplikasi obrolan grup di mana beberapa agen bisa saling berkomunikasi. Kasus penggunaan khas untuk pola ini termasuk kolaborasi tim, dukungan pelanggan, dan jaringan sosial.

Dalam pola ini, setiap agen mewakili seorang pengguna di obrolan grup, dan pesan dipertukarkan antar agen menggunakan protokol pesan. Agen dapat mengirim pesan ke obrolan grup, menerima pesan dari obrolan grup, dan merespons pesan dari agen lain.

Pola ini dapat diimplementasikan menggunakan arsitektur terpusat di mana semua pesan dialirkan melalui server pusat, atau arsitektur terdesentralisasi di mana pesan dipertukarkan langsung.

![Obrolan grup](../../../translated_images/id/multi-agent-group-chat.ec10f4cde556babd.webp)

### Penyerahan tugas

Pola ini berguna saat Anda ingin membuat aplikasi di mana beberapa agen bisa menyerahkan tugas ke agen lain.

Kasus penggunaan khas pola ini termasuk dukungan pelanggan, manajemen tugas, dan otomatisasi alur kerja.

Dalam pola ini, setiap agen mewakili sebuah tugas atau langkah dalam alur kerja, dan agen dapat menyerahkan tugas kepada agen lain berdasarkan aturan yang telah ditentukan.

![Penyerahan tugas](../../../translated_images/id/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Penyaringan kolaboratif

Pola ini berguna saat Anda ingin membuat aplikasi di mana beberapa agen dapat berkolaborasi untuk memberikan rekomendasi kepada pengguna.

Mengapa Anda ingin beberapa agen berkolaborasi adalah karena setiap agen bisa memiliki keahlian berbeda dan dapat berkontribusi ke proses rekomendasi dengan cara berbeda.

Mari kita ambil contoh di mana pengguna menginginkan rekomendasi saham terbaik untuk dibeli di pasar saham.

- **Ahli industri**: Satu agen bisa menjadi ahli dalam industri tertentu.
- **Analisis teknikal**: Agen lain bisa menjadi ahli dalam analisis teknikal.
- **Analisis fundamental**: Dan agen lain bisa ahli analisis fundamental. Dengan berkolaborasi, agen-agen ini dapat memberikan rekomendasi yang lebih komprehensif kepada pengguna.

![Rekomendasi](../../../translated_images/id/multi-agent-filtering.d959cb129dc9f608.webp)

## Skenario: Proses pengembalian dana

Pertimbangkan skenario di mana pelanggan mencoba mendapatkan pengembalian dana untuk sebuah produk, ada cukup banyak agen yang terlibat dalam proses ini tapi mari kita bagi antara agen khusus untuk proses ini dan agen umum yang bisa digunakan dalam proses lain.

**Agen khusus untuk proses pengembalian dana**:

Berikut beberapa agen yang bisa terlibat dalam proses pengembalian dana:

- **Agen pelanggan**: Agen ini mewakili pelanggan dan bertanggung jawab memulai proses pengembalian dana.
- **Agen penjual**: Agen ini mewakili penjual dan bertanggung jawab memproses pengembalian dana.
- **Agen pembayaran**: Agen ini mewakili proses pembayaran dan bertanggung jawab mengembalikan pembayaran ke pelanggan.
- **Agen resolusi**: Agen ini mewakili proses resolusi dan bertanggung jawab menyelesaikan masalah yang muncul selama proses pengembalian dana.
- **Agen kepatuhan**: Agen ini mewakili proses kepatuhan dan bertanggung jawab memastikan proses pengembalian dana sesuai dengan regulasi dan kebijakan.

**Agen umum**:

Agen-agen ini bisa digunakan di bagian lain bisnis Anda.

- **Agen pengiriman**: Agen ini mewakili proses pengiriman dan bertanggung jawab mengirimkan produk kembali ke penjual. Agen ini bisa digunakan baik untuk proses pengembalian dana maupun untuk pengiriman produk secara umum melalui pembelian misalnya.
- **Agen umpan balik**: Agen ini mewakili proses pengumpulan umpan balik dan bertanggung jawab mengumpulkan umpan balik dari pelanggan. Umpan balik bisa diberikan kapan saja, tidak hanya saat proses pengembalian dana.
- **Agen eskalasi**: Agen ini mewakili proses eskalasi dan bertanggung jawab mengeskalasi masalah ke tingkat dukungan yang lebih tinggi. Anda bisa menggunakan agen jenis ini untuk proses apapun yang memerlukan eskalasi masalah.
- **Agen notifikasi**: Agen ini mewakili proses pemberitahuan dan bertanggung jawab mengirim notifikasi ke pelanggan di berbagai tahap proses pengembalian dana.
- **Agen analitik**: Agen ini mewakili proses analitik dan bertanggung jawab menganalisis data terkait proses pengembalian dana.
- **Agen audit**: Agen ini mewakili proses audit dan bertanggung jawab mengaudit proses pengembalian dana untuk memastikan pelaksanaannya benar.
- **Agen pelaporan**: Agen ini mewakili proses pelaporan dan bertanggung jawab membuat laporan mengenai proses pengembalian dana.
- **Agen pengetahuan**: Agen ini mewakili proses pengetahuan dan bertanggung jawab memelihara basis pengetahuan informasi terkait proses pengembalian dana. Agen ini bisa memiliki pengetahuan tentang pengembalian dana dan bagian lain bisnis Anda.
- **Agen keamanan**: Agen ini mewakili proses keamanan dan bertanggung jawab menjaga keamanan proses pengembalian dana.
- **Agen kualitas**: Agen ini mewakili proses kualitas dan bertanggung jawab memastikan kualitas proses pengembalian dana.

Ada cukup banyak agen yang tercantum sebelumnya, baik untuk proses pengembalian dana khusus maupun untuk agen umum yang bisa digunakan di bagian lain bisnis Anda. Semoga ini memberi Anda gambaran tentang bagaimana Anda dapat memutuskan agen mana yang digunakan dalam sistem multi-agen Anda.

## Tugas

Rancang sistem multi-agen untuk proses dukungan pelanggan. Identifikasi agen yang terlibat dalam proses, peran dan tanggung jawabnya, dan bagaimana mereka berinteraksi satu sama lain. Pertimbangkan baik agen khusus untuk proses dukungan pelanggan maupun agen umum yang dapat digunakan di bagian lain bisnis Anda.
> Pikirkan terlebih dahulu sebelum Anda membaca solusi berikut, Anda mungkin memerlukan lebih banyak agen daripada yang Anda kira.

> TIP: Pikirkan tentang berbagai tahap dari proses dukungan pelanggan dan juga pertimbangkan agen yang dibutuhkan untuk sistem apa pun.

## Solusi

[Solusi](./solution/solution.md)

## Pemeriksaan Pengetahuan

Pertanyaan: Kapan Anda harus mempertimbangkan menggunakan multi-agen?

- [ ] A1: Ketika Anda memiliki beban kerja kecil dan tugas yang sederhana.
- [ ] A2: Ketika Anda memiliki beban kerja besar
- [ ] A3: Ketika Anda memiliki tugas yang sederhana.

[Solusi kuis](./solution/solution-quiz.md)

## Ringkasan

Dalam pelajaran ini, kami telah membahas pola desain multi-agen, termasuk skenario di mana multi-agen berlaku, keuntungan menggunakan multi-agen dibandingkan agen tunggal, blok bangunan dalam mengimplementasikan pola desain multi-agen, dan bagaimana memiliki visibilitas tentang bagaimana beberapa agen berinteraksi satu sama lain.

### Punya Lebih Banyak Pertanyaan tentang Pola Desain Multi-Agen?

Bergabunglah dengan [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk bertemu dengan pembelajar lain, menghadiri jam kantor, dan mendapatkan jawaban untuk pertanyaan Anda tentang AI Agents.

## Sumber daya tambahan

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Pola desain AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Pola desain Agentic</a>


## Pelajaran Sebelumnya

[Perencanaan Desain](../07-planning-design/README.md)

## Pelajaran Berikutnya

[Metakognisi dalam AI Agents](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berusaha untuk keakuratan, harap diperhatikan bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang sahih. Untuk informasi yang penting, disarankan menggunakan terjemahan profesional oleh manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau penafsiran yang salah yang timbul dari penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->