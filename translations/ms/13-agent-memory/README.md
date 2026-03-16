# Memori untuk Ejen AI  
[![Agent Memory](../../../translated_images/ms/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Apabila membincangkan manfaat unik mewujudkan Ejen AI, dua perkara yang sering dibincangkan: keupayaan untuk memanggil alat bagi menyiapkan tugasan dan keupayaan untuk memperbaiki diri dari masa ke masa. Memori adalah asas dalam mewujudkan ejen yang boleh memperbaiki diri sendiri yang dapat mencipta pengalaman yang lebih baik untuk pengguna kita.

Dalam pelajaran ini, kita akan melihat apa itu memori untuk Ejen AI dan bagaimana kita boleh menguruskannya serta menggunakannya untuk manfaat aplikasi kita.

## Pengenalan

Pelajaran ini akan merangkumi:

• **Memahami Memori Ejen AI**: Apa itu memori dan mengapa ia penting untuk ejen.

• **Melaksanakan dan Menyimpan Memori**: Kaedah praktikal untuk menambah kebolehan memori pada ejen AI anda, dengan fokus pada memori jangka pendek dan jangka panjang.

• **Menjadikan Ejen AI Memperbaiki Diri Sendiri**: Bagaimana memori membolehkan ejen belajar dari interaksi lalu dan memperbaiki diri dari masa ke masa.

## Pelaksanaan yang Tersedia

Pelajaran ini termasuk dua tutorial buku nota yang komprehensif:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Melaksanakan memori menggunakan Mem0 dan Azure AI Search dengan rangka kerja Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Melaksanakan memori berstruktur menggunakan Cognee, secara automatik membina graf pengetahuan yang disokong oleh embeddings, memvisualisasikan graf, dan pengambilan pintar

## Matlamat Pembelajaran

Selepas menyelesaikan pelajaran ini, anda akan tahu cara untuk:

• **Membezakan antara pelbagai jenis memori ejen AI**, termasuk memori kerja, jangka pendek, dan jangka panjang, serta bentuk khusus seperti memori persona dan episodik.

• **Melaksanakan dan mengurus memori jangka pendek dan jangka panjang untuk ejen AI** menggunakan rangka kerja Semantic Kernel, dengan menggunakan alat seperti Mem0, Cognee, memori Whiteboard, dan integrasi dengan Azure AI Search.

• **Memahami prinsip di sebalik ejen AI yang memperbaiki diri** dan bagaimana sistem pengurusan memori yang kukuh menyumbang kepada pembelajaran dan penyesuaian berterusan.

## Memahami Memori Ejen AI

Pada intinya, **memori untuk ejen AI merujuk kepada mekanisme yang membolehkan mereka menyimpan dan mengingat maklumat**. Maklumat ini boleh berupa butiran khusus tentang perbualan, keutamaan pengguna, tindakan lalu, atau corak yang dipelajari.

Tanpa memori, aplikasi AI sering kali tidak berkeadaan (stateless), bermakna setiap interaksi bermula dari kosong. Ini membawa kepada pengalaman pengguna yang berulang dan mengecewakan di mana ejen "lupa" konteks atau keutamaan sebelum ini.

### Mengapa Memori Penting?

Kecerdasan ejen sangat berkait rapat dengan keupayaannya untuk mengingat dan menggunakan maklumat lalu. Memori membolehkan ejen menjadi:

• **Reflektif**: Belajar dari tindakan dan hasil lalu.

• **Interaktif**: Mengekalkan konteks sepanjang perbualan yang sedang berjalan.

• **Proaktif dan Reaktif**: Meramalkan keperluan atau bertindak balas dengan tepat berdasarkan data sejarah.

• **Autonomi**: Beroperasi dengan lebih berdikari dengan menggunakan pengetahuan yang disimpan.

Matlamat melaksanakan memori adalah untuk menjadikan ejen lebih **boleh dipercayai dan berupaya**.

### Jenis Memori

#### Memori Kerja

Fikirkan ini sebagai sekeping kertas coretan yang digunakan oleh ejen semasa tugasan atau proses pemikiran yang sedang dijalankan. Ia menyimpan maklumat segera yang diperlukan untuk mengira langkah seterusnya.

Bagi ejen AI, memori kerja sering menangkap maklumat yang paling relevan dari perbualan, walaupun sejarah sembang penuh panjang atau terpotong. Ia memberi tumpuan kepada mengekstrak elemen utama seperti keperluan, cadangan, keputusan, dan tindakan.

**Contoh Memori Kerja**

Dalam ejen tempahan perjalanan, memori kerja mungkin menangkap permintaan pengguna semasa, seperti "Saya mahu menempah perjalanan ke Paris". Keperluan khusus ini disimpan dalam konteks segera ejen untuk membimbing interaksi semasa.

#### Memori Jangka Pendek

Jenis memori ini menyimpan maklumat untuk tempoh satu perbualan atau sesi. Ia adalah konteks sembang semasa, membolehkan ejen merujuk kembali kepada giliran-giliran sebelumnya dalam dialog.

**Contoh Memori Jangka Pendek**

Jika pengguna bertanya, "Berapa kos penerbangan ke Paris?" dan kemudian bertanya, "Bagaimana pula dengan penginapan di sana?", memori jangka pendek memastikan ejen tahu bahawa "di sana" merujuk kepada "Paris" dalam perbualan yang sama.

#### Memori Jangka Panjang

Ini adalah maklumat yang berterusan merentasi pelbagai perbualan atau sesi. Ia membolehkan ejen mengingati keutamaan pengguna, interaksi sejarah, atau pengetahuan umum dalam tempoh yang panjang. Ini penting untuk personalisasi.

**Contoh Memori Jangka Panjang**

Memori jangka panjang mungkin menyimpan bahawa "Ben suka bermain ski dan aktiviti luar, suka kopi dengan pemandangan gunung, dan mahu mengelakkan lereng ski lanjutan kerana kecederaan lalu". Maklumat ini, dipelajari dari interaksi sebelumnya, mempengaruhi cadangan dalam sesi perancangan perjalanan masa depan, menjadikannya sangat diperibadikan.

#### Memori Persona

Jenis memori khusus ini membantu ejen membangunkan "personaliti" atau "persona" yang konsisten. Ia membolehkan ejen mengingat butiran tentang dirinya atau peranan yang dimaksudkan, menjadikan interaksi lebih lancar dan fokus.

**Contoh Memori Persona**  
Jika ejen perjalanan direka untuk menjadi "perancang ski pakar," memori persona mungkin mengukuhkan peranan ini, mempengaruhi maklum balasnya agar selaras dengan tona dan pengetahuan seorang pakar.

#### Memori Aliran Kerja/Episodik

Memori ini menyimpan urutan langkah yang diambil ejen semasa tugasan kompleks, termasuk kejayaan dan kegagalan. Ia seperti mengingati "episod" tertentu atau pengalaman lalu untuk belajar daripadanya.

**Contoh Memori Episodik**

Jika ejen cuba menempah penerbangan tertentu tetapi gagal kerana tiada kekosongan, memori episodik boleh merekod kegagalan ini, membolehkan ejen cuba penerbangan alternatif atau memberitahu pengguna mengenai isu tersebut dengan lebih bermaklumat dalam cubaan seterusnya.

#### Memori Entiti

Ini melibatkan pengektrakan dan pengingatan entiti tertentu (seperti orang, tempat atau benda) dan peristiwa dari perbualan. Ia membolehkan ejen membina pemahaman berstruktur tentang elemen utama yang dibincangkan.

**Contoh Memori Entiti**

Daripada perbualan tentang perjalanan lalu, ejen mungkin mengekstrak "Paris," "Menara Eiffel," dan "makan malam di restoran Le Chat Noir" sebagai entiti. Dalam interaksi akan datang, ejen boleh mengingati "Le Chat Noir" dan menawarkan untuk membuat tempahan baru di sana.

#### Structured RAG (Retrieval Augmented Generation Berstruktur)

Walaupun RAG adalah teknik yang lebih luas, "Structured RAG" diketengahkan sebagai teknologi memori yang berkuasa. Ia mengekstrak maklumat padat dan berstruktur daripada pelbagai sumber (perbualan, emel, imej) dan menggunakannya untuk meningkatkan ketepatan, ingatan, dan kelajuan dalam maklum balas. Berbeza dengan RAG klasik yang hanya bergantung pada persamaan semantik, Structured RAG berfungsi dengan struktur maklumat secara asli.

**Contoh Structured RAG**

Daripada hanya memadankan kata kunci, Structured RAG boleh mengekstrak butiran penerbangan (destinasi, tarikh, masa, syarikat penerbangan) dari emel dan menyimpannya secara berstruktur. Ini membolehkan pertanyaan tepat seperti "Penerbangan apa yang saya tempah ke Paris pada hari Selasa?"

## Melaksanakan dan Menyimpan Memori

Melaksanakan memori untuk ejen AI melibatkan proses sistematik **pengurusan memori**, yang termasuk menjana, menyimpan, mengambil, mengintegrasi, mengemas kini, dan juga "melupakan" (atau memadam) maklumat. Pengambilan adalah aspek yang sangat penting.

### Alat Memori Khusus

#### Mem0

Salah satu cara untuk menyimpan dan mengurus memori ejen ialah menggunakan alat khusus seperti Mem0. Mem0 berfungsi sebagai lapisan memori berterusan yang membolehkan ejen mengingat interaksi relevan, menyimpan keutamaan pengguna dan konteks fakta, serta belajar dari kejayaan dan kegagalan dari masa ke masa. Idea di sini adalah ejen tanpa keadaan (stateless) bertukar menjadi ejen berkeadaan (stateful).

Ia berfungsi melalui **saluran memori dua fasa: pengekstrakan dan kemas kini**. Pertama, mesej yang ditambah dalam benang ejen dihantar ke perkhidmatan Mem0, yang menggunakan Model Bahasa Besar (LLM) untuk meringkaskan sejarah perbualan dan mengekstrak memori baru. Seterusnya, fasa kemas kini yang dikendalikan LLM menentukan sama ada untuk menambah, meminda, atau memadam memori tersebut, menyimpannya dalam stor data hibrid yang boleh merangkumi pangkalan data vektor, graf, dan nilai-kunci. Sistem ini juga menyokong pelbagai jenis memori dan boleh menggabungkan memori graf untuk mengurus hubungan antara entiti.

#### Cognee

Pendekatan berkuasa lain adalah menggunakan **Cognee**, memori semantik sumber terbuka untuk ejen AI yang mengubah data berstruktur dan tidak berstruktur menjadi graf pengetahuan yang boleh dipertanyakan dan disokong oleh embeddings. Cognee menyediakan **arsitektur penyimpanan berganda** yang menggabungkan pencarian persamaan vektor dengan hubungan graf, membolehkan ejen memahami bukan sahaja maklumat yang serupa tetapi bagaimana konsep berkait antara satu sama lain.

Ia cemerlang dalam **pengambilan hibrid** yang menggabungkan persamaan vektor, struktur graf, dan penaakulan LLM - dari pencarian serpihan mentah hingga menjawab soalan berasaskan graf. Sistem mengekalkan **memori hidup** yang berkembang dan terus ada sambil kekal boleh dipertanyakan sebagai satu graf bersambung, menyokong konteks sesi jangka pendek dan memori berterusan jangka panjang.

Tutorial buku nota Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) menunjukkan bagaimana membina lapisan memori bersepadu ini, dengan contoh praktikal penggunaan pelbagai sumber data, memvisualisasikan graf pengetahuan, dan melakukan pertanyaan dengan strategi carian berbeza yang disesuaikan untuk keperluan ejen tertentu.

### Menyimpan Memori dengan RAG

Selain alat memori khusus seperti mem0, anda boleh menggunakan perkhidmatan carian yang kukuh seperti **Azure AI Search sebagai backend untuk menyimpan dan mengambil memori**, terutamanya untuk Structured RAG.

Ini membolehkan anda mengasaskan maklum balas ejen dengan data sendiri, memastikan jawapan yang lebih relevan dan tepat. Azure AI Search boleh digunakan untuk menyimpan memori perjalanan khusus pengguna, katalog produk, atau mana-mana pengetahuan domain lain.

Azure AI Search menyokong kebolehan seperti **Structured RAG**, yang cemerlang dalam mengekstrak dan mengambil maklumat padat berstruktur dari set data besar seperti sejarah perbualan, emel, atau imej. Ini menyediakan "ketepatan dan ingatan supermanusia" berbanding pendekatan pemecahan teks tradisional dan embedding.

## Menjadikan Ejen AI Memperbaiki Diri Sendiri

Corak biasa untuk ejen yang memperbaiki diri adalah dengan memperkenalkan **"ejen pengetahuan"**. Ejen yang berasingan ini memerhati perbualan utama antara pengguna dan ejen utama. Peranannya adalah untuk:

1. **Kenal pasti maklumat bernilai**: Tentukan jika mana-mana bahagian perbualan berbaloi disimpan sebagai pengetahuan umum atau keutamaan pengguna tertentu.

2. **Ekstrak dan ringkaskan**: Menghuraikan pembelajaran atau keutamaan penting dari perbualan.

3. **Simpan dalam pangkalan pengetahuan**: Menyimpan maklumat yang diekstrak ini, sering dalam pangkalan data vektor, supaya ia boleh diambil kemudian.

4. **Tingkatkan pertanyaan masa depan**: Apabila pengguna memulakan pertanyaan baru, ejen pengetahuan mengambil maklumat yang disimpan berkaitan dan menambahkannya ke arahan pengguna, menyediakan konteks penting kepada ejen utama (serupa dengan RAG).

### Pengoptimuman untuk Memori

• **Pengurusan Latensi**: Untuk mengelakkan kelambatan interaksi pengguna, model yang lebih murah dan cepat boleh digunakan pada awalnya untuk cepat memeriksa jika maklumat bernilai untuk disimpan atau diambil, dan hanya memanggil proses ekstraksi/pengambilan yang lebih kompleks apabila perlu.

• **Penyelenggaraan Pangkalan Pengetahuan**: Untuk pangkalan pengetahuan yang berkembang, maklumat yang kurang digunakan boleh dipindahkan ke "penyimpanan sejuk" untuk mengurus kos.

## Ada Lagi Soalan Tentang Memori Ejen?

Sertai [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk berjumpa dengan pelajar lain, menghadiri waktu pejabat dan mendapatkan jawapan bagi soalan Ejen AI anda.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk ketepatan, sila ambil maklum bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidaktepatan. Dokumen asal dalam bahasa asalnya harus dianggap sebagai sumber yang sah. Untuk maklumat penting, terjemahan oleh penterjemah manusia profesional adalah disyorkan. Kami tidak bertanggungjawab atas sebarang salah faham atau salah tafsir yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->