[![Reka Bentuk Berbilang Ejen](../../../translated_images/ms/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Klik imej di atas untuk menonton video bagi pelajaran ini)_

# Corak reka bentuk multi-ejen

Sebaik sahaja anda mula bekerja pada projek yang melibatkan berbilang ejen, anda perlu mempertimbangkan corak reka bentuk berbilang ejen. Walau bagaimanapun, mungkin tidak jelas bila untuk beralih kepada berbilang ejen dan apakah kelebihannya.

## Pengenalan

Dalam pelajaran ini, kami ingin menjawab soalan-soalan berikut:

- Apakah senario di mana berbilang ejen boleh digunakan?
- Apakah kelebihan menggunakan berbilang ejen berbanding hanya satu ejen tunggal yang melakukan pelbagai tugas?
- Apakah blok binaan untuk melaksanakan corak reka bentuk berbilang ejen?
- Bagaimana kita mendapat keterlihatan tentang bagaimana berbilang ejen berinteraksi antara satu sama lain?

## Matlamat Pembelajaran

Selepas pelajaran ini, anda sepatutnya dapat:

- Mengenal pasti senario di mana berbilang ejen sesuai digunakan
- Mengenali kelebihan menggunakan berbilang ejen berbanding ejen tunggal.
- Memahami blok binaan untuk melaksanakan corak reka bentuk berbilang ejen.

Apakah gambaran yang lebih besar?

*Berbilang ejen adalah corak reka bentuk yang membenarkan beberapa ejen bekerjasama untuk mencapai matlamat bersama*.

Corak ini digunakan secara meluas dalam pelbagai bidang, termasuk robotik, sistem autonomi, dan pengkomputeran teragih.

## Senario Di Mana Berbilang Ejen Sesuai Digunakan

Jadi apakah senario yang menjadi kes penggunaan yang baik untuk menggunakan berbilang ejen? Jawapannya ialah terdapat banyak senario di mana menggunakan beberapa ejen adalah bermanfaat terutamanya dalam kes-kes berikut:

- **Beban kerja besar**: Beban kerja besar boleh dibahagikan kepada tugas-tugas yang lebih kecil dan diberikan kepada ejen-ejen yang berbeza, membolehkan pemprosesan selari dan penyelesaian yang lebih cepat. Contoh bagi ini adalah dalam kes tugas pemprosesan data yang besar.
- **Tugas kompleks**: Tugas kompleks, seperti beban kerja besar, boleh dipecahkan kepada subtugas yang lebih kecil dan diberikan kepada ejen-ejen yang berbeza, setiap satu mengkhusus dalam aspek tertentu tugas tersebut. Contoh yang baik bagi ini adalah dalam kes kenderaan autonomi di mana ejen-ejen yang berbeza mengurus navigasi, pengesanan halangan, dan komunikasi dengan kenderaan lain.
- **Kepakaran yang pelbagai**: Ejen-ejen yang berbeza boleh mempunyai kepakaran yang pelbagai, membolehkan mereka menangani aspek-aspek berbeza sesuatu tugas dengan lebih berkesan daripada satu ejen sahaja. Untuk kes ini, contoh yang baik adalah dalam penjagaan kesihatan di mana ejen boleh mengurus diagnostik, pelan rawatan, dan pemantauan pesakit.

## Kelebihan Menggunakan Berbilang Ejen Berbanding Ejen Tunggal

Satu sistem ejen tunggal boleh berfungsi dengan baik untuk tugas-tugas mudah, tetapi untuk tugas yang lebih kompleks, menggunakan berbilang ejen boleh memberikan beberapa kelebihan:

- **Pengkhususan**: Setiap ejen boleh dikhususkan untuk tugas tertentu. Kekurangan pengkhususan dalam satu ejen bermakna anda mempunyai ejen yang boleh melakukan segala-galanya tetapi mungkin keliru tentang apa yang perlu dilakukan apabila berdepan dengan tugas yang kompleks. Contohnya, ia mungkin akhirnya melakukan tugas yang bukanlah yang paling sesuai untuknya.
- **Kebolehskoalan**: Lebih mudah untuk menskalakan sistem dengan menambah lebih banyak ejen daripada membebankan satu ejen tunggal.
- **Toleransi Kegagalan**: Jika satu ejen gagal, ejen-ejen lain boleh terus berfungsi, memastikan kebolehpercayaan sistem.

Mari ambil contoh, mari kita tempah perjalanan untuk seorang pengguna. Satu sistem ejen tunggal perlu mengendalikan semua aspek proses tempahan perjalanan, dari mencari penerbangan hingga menempah hotel dan kereta sewa. Untuk mencapai ini dengan satu ejen, ejen tersebut perlu mempunyai alat untuk mengendalikan semua tugas ini. Ini boleh membawa kepada sistem yang kompleks dan monolitik yang sukar untuk diselenggara dan diskalakan. Sistem berbilang ejen, sebaliknya, boleh mempunyai ejen-ejen yang berbeza yang mengkhusus dalam mencari penerbangan, menempah hotel, dan kereta sewa. Ini akan menjadikan sistem lebih bermodul, lebih mudah diselenggara, dan boleh diskalakan.

Bandingkan ini dengan sebuah biro pelancongan yang dikendalikan sebagai kedai kecil keluarga berbanding biro pelancongan yang dikendalikan sebagai francais. Kedai kecil keluarga akan mempunyai satu ejen yang mengendalikan semua aspek proses tempahan perjalanan, manakala francais akan mempunyai ejen-ejen yang berbeza mengendalikan aspek-aspek berbeza proses tempahan perjalanan.

## Blok Binaan untuk Melaksanakan Corak Reka Bentuk Berbilang Ejen

Sebelum anda dapat melaksanakan corak reka bentuk berbilang ejen, anda perlu memahami blok binaan yang membentuk corak tersebut.

Mari kita jadikan ini lebih konkrit dengan sekali lagi melihat contoh menempah perjalanan untuk seorang pengguna. Dalam kes ini, blok binaan akan termasuk:

- **Komunikasi Ejen**: Ejen untuk mencari penerbangan, menempah hotel, dan kereta sewa perlu berkomunikasi dan berkongsi maklumat tentang keutamaan dan kekangan pengguna. Anda perlu memutuskan protokol dan kaedah untuk komunikasi ini. Apa yang dimaksudkan secara konkrit ialah ejen untuk mencari penerbangan perlu berkomunikasi dengan ejen untuk menempah hotel untuk memastikan hotel ditempah untuk tarikh yang sama seperti penerbangan. Itu bermakna ejen-ejen perlu berkongsi maklumat tentang tarikh perjalanan pengguna, bermakna anda perlu memutuskan *ejen mana yang berkongsi maklumat dan bagaimana mereka berkongsi maklumat*.
- **Mekanisme Penyelaras**: Ejen perlu menyelaraskan tindakan mereka untuk memastikan keutamaan dan kekangan pengguna dipenuhi. Satu keutamaan pengguna boleh jadi bahawa mereka mahu hotel yang dekat dengan lapangan terbang manakala satu kekangan boleh jadi bahawa kereta sewa hanya tersedia di lapangan terbang. Ini bermakna ejen untuk menempah hotel perlu menyelaraskan dengan ejen untuk menempah kereta sewa untuk memastikan keutamaan dan kekangan pengguna dipenuhi. Ini bermakna anda perlu memutuskan *bagaimana ejen-ejen menyelaraskan tindakan mereka*.
- **Seni Bina Ejen**: Ejen perlu mempunyai struktur dalaman untuk membuat keputusan dan belajar daripada interaksi mereka dengan pengguna. Ini bermakna ejen untuk mencari penerbangan perlu mempunyai struktur dalaman untuk membuat keputusan tentang penerbangan mana yang hendak disyorkan kepada pengguna. Ini bermakna anda perlu memutuskan *bagaimana ejen-ejen membuat keputusan dan belajar daripada interaksi mereka dengan pengguna*. Contoh bagaimana ejen belajar dan memperbaiki boleh jadi ejen untuk mencari penerbangan boleh menggunakan model pembelajaran mesin untuk mencadangkan penerbangan kepada pengguna berdasarkan keutamaan lalu mereka.
- **Keterlihatan dalam Interaksi Berbilang Ejen**: Anda perlu mempunyai keterlihatan tentang bagaimana berbilang ejen berinteraksi antara satu sama lain. Ini bermakna anda perlu mempunyai alat dan teknik untuk menjejak aktiviti dan interaksi ejen. Ini boleh dalam bentuk alat pencatatan dan pemantauan, alat visualisasi, dan metrik prestasi.
- **Corak Berbilang Ejen**: Terdapat corak-corak yang berbeza untuk melaksanakan sistem berbilang ejen, seperti seni bina berpusat, terdesentralisasi, dan hibrid. Anda perlu memutuskan corak yang paling sesuai dengan kes penggunaan anda.
- **Campur tangan manusia**: Dalam kebanyakan kes, anda akan mempunyai campur tangan manusia dan anda perlu mengarahkan ejen bila untuk meminta intervensi manusia. Ini boleh dalam bentuk pengguna meminta hotel atau penerbangan tertentu yang ejen tidak cadangkan atau meminta pengesahan sebelum menempah penerbangan atau hotel.

## Keterlihatan dalam Interaksi Berbilang Ejen

Adalah penting bahawa anda mempunyai keterlihatan tentang bagaimana berbilang ejen berinteraksi antara satu sama lain. Keterlihatan ini penting untuk pengesanan ralat, pengoptimuman, dan memastikan keberkesanan keseluruhan sistem. Untuk mencapai ini, anda perlu mempunyai alat dan teknik untuk menjejak aktiviti dan interaksi ejen. Ini boleh dalam bentuk alat pencatatan dan pemantauan, alat visualisasi, dan metrik prestasi.

Contohnya, dalam kes menempah perjalanan untuk seorang pengguna, anda boleh mempunyai papan pemuka yang menunjukkan status setiap ejen, keutamaan dan kekangan pengguna, dan interaksi antara ejen-ejen. Papan pemuka ini boleh menunjukkan tarikh perjalanan pengguna, penerbangan yang dicadangkan oleh ejen penerbangan, hotel yang dicadangkan oleh ejen hotel, dan kereta sewa yang dicadangkan oleh ejen kereta sewa. Ini akan memberi anda pandangan yang jelas tentang bagaimana ejen-ejen berinteraksi antara satu sama lain dan sama ada keutamaan dan kekangan pengguna dipenuhi.

Mari lihat setiap aspek ini dengan lebih terperinci.

- **Alat Pencatatan dan Pemantauan**: Anda mahu pencatatan dilakukan untuk setiap tindakan yang diambil oleh ejen. Satu entri log boleh menyimpan maklumat tentang ejen yang mengambil tindakan, tindakan yang diambil, masa tindakan diambil, dan hasil tindakan. Maklumat ini kemudian boleh digunakan untuk pengesanan ralat, pengoptimuman dan lain-lain.
- **Alat Visualisasi**: Alat visualisasi boleh membantu anda melihat interaksi antara ejen dengan cara yang lebih intuitif. Contohnya, anda boleh mempunyai graf yang menunjukkan aliran maklumat antara ejen-ejen. Ini boleh membantu anda mengenal pasti kesesakan, ketidakcekapan, dan isu-isu lain dalam sistem.
- **Metrik Prestasi**: Metrik prestasi boleh membantu anda menjejak keberkesanan sistem berbilang ejen. Contohnya, anda boleh menjejak masa yang diambil untuk menyelesaikan suatu tugas, bilangan tugas yang diselesaikan setiap unit masa, dan ketepatan cadangan yang dibuat oleh ejen-ejen. Maklumat ini boleh membantu anda mengenal pasti bidang untuk penambahbaikan dan mengoptimumkan sistem.

## Corak Berbilang Ejen

Mari kita mendalami beberapa corak konkrit yang boleh kita gunakan untuk mencipta aplikasi berbilang ejen. Berikut adalah beberapa corak menarik yang patut dipertimbangkan:

### Sembang kumpulan

Corak ini berguna apabila anda ingin mencipta aplikasi sembang kumpulan di mana berbilang ejen boleh berkomunikasi antara satu sama lain. Kes penggunaan tipikal untuk corak ini termasuk kerjasama pasukan, sokongan pelanggan, dan rangkaian sosial.

Dalam corak ini, setiap ejen mewakili seorang pengguna dalam sembang kumpulan, dan mesej ditukar antara ejen menggunakan protokol pemesejan. Ejen boleh menghantar mesej ke sembang kumpulan, menerima mesej dari sembang kumpulan, dan membalas mesej daripada ejen lain.

Corak ini boleh dilaksanakan menggunakan seni bina berpusat di mana semua mesej dirute melalui pelayan pusat, atau seni bina terdesentralisasi di mana mesej ditukar secara terus.

![Sembang kumpulan](../../../translated_images/ms/multi-agent-group-chat.ec10f4cde556babd.webp)

### Serah tugas

Corak ini berguna apabila anda ingin mencipta aplikasi di mana berbilang ejen boleh menyerahkan tugas antara satu sama lain.

Kes penggunaan tipikal untuk corak ini termasuk sokongan pelanggan, pengurusan tugas, dan automasi aliran kerja.

Dalam corak ini, setiap ejen mewakili satu tugas atau satu langkah dalam aliran kerja, dan ejen boleh menyerahkan tugas kepada ejen lain berdasarkan peraturan yang telah ditetapkan.

![Serah tugas](../../../translated_images/ms/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Penapisan kolaboratif

Corak ini berguna apabila anda ingin mencipta aplikasi di mana berbilang ejen boleh bekerjasama untuk membuat cadangan kepada pengguna.

Mengapa anda mahu berbilang ejen bekerjasama adalah kerana setiap ejen boleh mempunyai kepakaran yang berbeza dan boleh menyumbang kepada proses cadangan dengan cara yang berbeza.

Mari ambil contoh di mana seorang pengguna mahu cadangan tentang saham terbaik untuk dibeli di pasaran saham.

- **Pakar industri**:. Satu ejen boleh menjadi pakar dalam industri tertentu.
- **Analisis teknikal**: Satu lagi ejen boleh menjadi pakar dalam analisis teknikal.
- **Analisis asas**: dan satu lagi ejen boleh menjadi pakar dalam analisis asas. Dengan bekerjasama, ejen-ejen ini boleh memberikan cadangan yang lebih komprehensif kepada pengguna.

![Cadangan](../../../translated_images/ms/multi-agent-filtering.d959cb129dc9f608.webp)

## Senario: Proses bayaran balik

Pertimbangkan satu senario di mana seorang pelanggan cuba mendapatkan bayaran balik untuk sebuah produk, mungkin terdapat beberapa ejen yang terlibat dalam proses ini tetapi mari kita bahagikan antara ejen-ejen khusus untuk proses ini dan ejen-ejen umum yang boleh digunakan dalam proses lain.

**Ejen khusus untuk proses bayaran balik**:

Berikut adalah beberapa ejen yang boleh terlibat dalam proses bayaran balik:

- **Ejen pelanggan**: Ejen ini mewakili pelanggan dan bertanggungjawab untuk memulakan proses bayaran balik.
- **Ejen penjual**: Ejen ini mewakili penjual dan bertanggungjawab untuk memproses bayaran balik.
- **Ejen pembayaran**: Ejen ini mewakili proses pembayaran dan bertanggungjawab untuk memulangkan bayaran kepada pelanggan.
- **Ejen penyelesaian**: Ejen ini mewakili proses penyelesaian dan bertanggungjawab untuk menyelesaikan sebarang isu yang timbul semasa proses bayaran balik.
- **Ejen pematuhan**: Ejen ini mewakili proses pematuhan dan bertanggungjawab untuk memastikan proses bayaran balik mematuhi peraturan dan polisi.

**Ejen umum**:

Ejen-ejen ini boleh digunakan oleh bahagian lain dalam perniagaan anda.

- **Ejen penghantaran**: Ejen ini mewakili proses penghantaran dan bertanggungjawab untuk menghantar produk kembali kepada penjual. Ejen ini boleh digunakan sama ada untuk proses bayaran balik dan juga untuk penghantaran umum produk melalui pembelian contohnya.
- **Ejen maklum balas**: Ejen ini mewakili proses maklum balas dan bertanggungjawab untuk mengumpul maklum balas daripada pelanggan. Maklum balas boleh diperoleh pada bila-bila masa dan bukan hanya semasa proses bayaran balik.
- **Ejen pengeskalasian**: Ejen ini mewakili proses pengeskalasian dan bertanggungjawab untuk meningkatkan isu ke tahap sokongan yang lebih tinggi. Anda boleh menggunakan jenis ejen ini untuk mana-mana proses di mana anda perlu mengeskalasi isu.
- **Ejen pemberitahuan**: Ejen ini mewakili proses pemberitahuan dan bertanggungjawab untuk menghantar pemberitahuan kepada pelanggan pada pelbagai peringkat proses bayaran balik.
- **Ejen analitik**: Ejen ini mewakili proses analitik dan bertanggungjawab untuk menganalisis data berkaitan proses bayaran balik.
- **Ejen audit**: Ejen ini mewakili proses audit dan bertanggungjawab untuk mengaudit proses bayaran balik untuk memastikan ia dijalankan dengan betul.
- **Ejen pelaporan**: Ejen ini mewakili proses pelaporan dan bertanggungjawab untuk menghasilkan laporan mengenai proses bayaran balik.
- **Ejen pengetahuan**: Ejen ini mewakili proses pengetahuan dan bertanggungjawab untuk menyelenggara pangkalan pengetahuan maklumat berkaitan proses bayaran balik. Ejen ini boleh mahir dalam kedua-dua hal berkenaan bayaran balik dan bahagian lain perniagaan anda.
- **Ejen keselamatan**: Ejen ini mewakili proses keselamatan dan bertanggungjawab untuk memastikan keselamatan proses bayaran balik.
- **Ejen kualiti**: Ejen ini mewakili proses kualiti dan bertanggungjawab untuk memastikan kualiti proses bayaran balik.

Terdapat banyak ejen disenaraikan sebelum ini baik untuk proses bayaran balik yang khusus tetapi juga untuk ejen umum yang boleh digunakan dalam bahagian lain perniagaan anda. Diharapkan ini memberi anda gambaran tentang bagaimana anda boleh membuat keputusan tentang ejen mana yang hendak digunakan dalam sistem berbilang ejen anda.

## Tugasan

Reka bentuk sistem berbilang ejen untuk proses sokongan pelanggan. Kenal pasti ejen-ejen yang terlibat dalam proses, peranan dan tanggungjawab mereka, dan bagaimana mereka berinteraksi antara satu sama lain. Pertimbangkan kedua-dua ejen yang khusus untuk proses sokongan pelanggan dan ejen umum yang boleh digunakan dalam bahagian lain perniagaan anda.
> Fikir sejenak sebelum anda membaca penyelesaian berikut; anda mungkin memerlukan lebih banyak ejen daripada yang anda sangka.
> PETUA: Fikirkan tentang peringkat berbeza dalam proses sokongan pelanggan dan pertimbangkan juga ejen yang diperlukan untuk mana-mana sistem.

## Solution

[Penyelesaian](./solution/solution.md)

## Knowledge checks

Question: Bilakah anda harus mempertimbangkan menggunakan berbilang ejen?

- [ ] A1: Apabila anda mempunyai beban kerja yang kecil dan tugas yang mudah.
- [ ] A2: Apabila anda mempunyai beban kerja yang besar
- [ ] A3: Apabila anda mempunyai tugas yang mudah.

[Kuiz penyelesaian](./solution/solution-quiz.md)

## Summary

Dalam pelajaran ini, kita telah melihat corak reka bentuk berbilang ejen, termasuk senario di mana berbilang ejen sesuai, kelebihan menggunakan berbilang ejen berbanding ejen tunggal, blok binaan untuk melaksanakan corak reka bentuk berbilang ejen, dan bagaimana memperoleh kebolehlihatan terhadap bagaimana pelbagai ejen berinteraksi antara satu sama lain.

### Ada lagi soalan tentang Corak Reka Bentuk Berbilang Ejen?

Sertai the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk bertemu dengan pelajar lain, menghadiri waktu pejabat dan mendapatkan jawapan kepada soalan Ejen AI anda.

## Additional resources

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Corak reka bentuk AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Corak reka bentuk agentik</a>


## Previous Lesson

[Perancangan Reka Bentuk](../07-planning-design/README.md)

## Next Lesson

[Metakognisi dalam Ejen AI](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Penafian:
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha mencapai ketepatan, sila ambil maklum bahawa terjemahan automatik mungkin mengandungi ralat atau ketidaktepatan. Dokumen asal dalam bahasa asalnya hendaklah dianggap sebagai sumber yang muktamad. Untuk maklumat yang kritikal, disyorkan mendapatkan terjemahan profesional oleh penterjemah manusia. Kami tidak akan bertanggungjawab ke atas sebarang salah faham atau salah tafsir yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->