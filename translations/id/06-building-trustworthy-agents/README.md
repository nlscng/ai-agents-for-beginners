[![Trustworthy AI Agents](../../../translated_images/id/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klik gambar di atas untuk menonton video pelajaran ini)_

# Membangun Agen AI yang Terpercaya

## Pendahuluan

Pelajaran ini akan membahas:

- Cara membangun dan menerapkan Agen AI yang aman dan efektif
- Pertimbangan keamanan penting saat mengembangkan Agen AI.
- Cara menjaga privasi data dan pengguna saat mengembangkan Agen AI.

## Tujuan Pembelajaran

Setelah menyelesaikan pelajaran ini, Anda akan tahu bagaimana:

- Mengidentifikasi dan mengurangi risiko saat membuat Agen AI.
- Menerapkan langkah-langkah keamanan untuk memastikan data dan akses dikelola dengan benar.
- Membuat Agen AI yang menjaga privasi data dan memberikan pengalaman pengguna yang berkualitas.

## Keamanan

Mari kita lihat terlebih dahulu bagaimana membangun aplikasi agen yang aman. Keamanan berarti agen AI melakukan tugas sesuai dengan yang dirancang. Sebagai pembangun aplikasi agen, kita memiliki metode dan alat untuk memaksimalkan keamanan:

### Membangun Kerangka Pesan Sistem

Jika Anda pernah membangun aplikasi AI menggunakan Large Language Models (LLM), Anda tahu pentingnya merancang prompt sistem atau pesan sistem yang kuat. Prompt ini menetapkan aturan meta, instruksi, dan pedoman bagaimana LLM akan berinteraksi dengan pengguna dan data.

Untuk Agen AI, prompt sistem ini bahkan lebih penting karena Agen AI memerlukan instruksi yang sangat spesifik untuk menyelesaikan tugas yang telah kami desain untuk mereka.

Untuk membuat prompt sistem yang dapat diskalakan, kita dapat menggunakan kerangka pesan sistem untuk membangun satu atau lebih agen dalam aplikasi kita:

![Building a System Message Framework](../../../translated_images/id/system-message-framework.3a97368c92d11d68.webp)

#### Langkah 1: Buat Pesan Sistem Meta

Meta prompt akan digunakan oleh LLM untuk menghasilkan prompt sistem untuk agen yang kita buat. Kami merancangnya sebagai template agar dapat dengan efisien membuat banyak agen jika diperlukan.

Berikut adalah contoh pesan sistem meta yang akan kami berikan kepada LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Langkah 2: Buat prompt dasar

Langkah berikutnya adalah membuat prompt dasar untuk mendeskripsikan Agen AI. Anda harus menyertakan peran agen, tugas yang akan diselesaikan oleh agen, dan tanggung jawab lain dari agen tersebut.

Berikut contohnya:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Langkah 3: Berikan Pesan Sistem Dasar ke LLM

Sekarang kita dapat mengoptimalkan pesan sistem ini dengan memberikan pesan sistem meta sebagai pesan sistem dan pesan sistem dasar kita.

Ini akan menghasilkan pesan sistem yang dirancang lebih baik untuk membimbing agen AI kita:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Langkah 4: Iterasi dan Perbaikan

Nilai dari kerangka pesan sistem ini adalah kemampuan untuk memudahkan skalabilitas pembuatan pesan sistem dari beberapa agen serta meningkatkan pesan sistem Anda seiring waktu. Jarang sekali Anda memiliki pesan sistem yang langsung bekerja untuk kasus penggunaan lengkap Anda pada percobaan pertama. Dengan mampu melakukan penyesuaian kecil dan perbaikan dengan mengubah pesan sistem dasar dan menjalankannya melalui sistem, Anda dapat membandingkan dan mengevaluasi hasilnya.

## Memahami Ancaman

Untuk membangun agen AI yang terpercaya, penting untuk memahami dan mengurangi risiko dan ancaman terhadap agen AI Anda. Mari kita lihat beberapa jenis ancaman terhadap agen AI dan bagaimana Anda bisa lebih baik merencanakan dan mempersiapkannya.

![Understanding Threats](../../../translated_images/id/understanding-threats.89edeada8a97fc0f.webp)

### Tugas dan Instruksi

**Deskripsi:** Penyerang mencoba mengubah instruksi atau tujuan agen AI melalui prompting atau manipulasi input.

**Mitigasi**: Lakukan pemeriksaan validasi dan filter input untuk mendeteksi prompt yang berpotensi berbahaya sebelum diproses oleh Agen AI. Karena serangan ini biasanya memerlukan interaksi sering dengan Agen, membatasi jumlah giliran dalam percakapan adalah cara lain untuk mencegah jenis serangan ini.

### Akses ke Sistem Penting

**Deskripsi**: Jika agen AI memiliki akses ke sistem dan layanan yang menyimpan data sensitif, penyerang dapat mengkompromikan komunikasi antara agen dan layanan tersebut. Ini bisa berupa serangan langsung atau upaya tidak langsung untuk memperoleh informasi tentang sistem tersebut melalui agen.

**Mitigasi**: Agen AI harus memiliki akses ke sistem hanya berdasarkan kebutuhan guna mencegah jenis serangan ini. Komunikasi antara agen dan sistem juga harus aman. Menerapkan otentikasi dan kontrol akses adalah cara lain untuk melindungi informasi ini.

### Pembebanan Berlebih pada Sumber Daya dan Layanan

**Deskripsi:** Agen AI dapat mengakses berbagai alat dan layanan untuk menyelesaikan tugas. Penyerang dapat menggunakan kemampuan ini untuk menyerang layanan tersebut dengan mengirimkan volume permintaan yang tinggi melalui Agen AI, yang dapat menyebabkan kegagalan sistem atau biaya tinggi.

**Mitigasi:** Terapkan kebijakan untuk membatasi jumlah permintaan yang dapat dilakukan agen AI ke sebuah layanan. Membatasi jumlah giliran percakapan dan permintaan ke agen AI Anda adalah cara lain untuk mencegah jenis serangan ini.

### Keracunan Basis Pengetahuan

**Deskripsi:** Jenis serangan ini tidak langsung menargetkan agen AI tetapi menargetkan basis pengetahuan dan layanan lain yang digunakan agen AI. Ini dapat melibatkan korupsi data atau informasi yang akan digunakan agen AI untuk menyelesaikan tugas, yang mengakibatkan respons bias atau tidak disengaja kepada pengguna.

**Mitigasi:** Lakukan verifikasi rutin terhadap data yang akan digunakan oleh agen AI dalam alur kerjanya. Pastikan akses ke data ini aman dan hanya diubah oleh individu terpercaya untuk menghindari jenis serangan ini.

### Kesalahan Berantai

**Deskripsi:** Agen AI mengakses berbagai alat dan layanan untuk menyelesaikan tugas. Kesalahan yang disebabkan oleh penyerang dapat menyebabkan kegagalan sistem lain yang terhubung dengan agen AI, sehingga serangan tersebut menjadi lebih meluas dan sulit untuk ditangani.

**Mitigasi**: Salah satu cara untuk menghindari ini adalah dengan menjalankan Agen AI dalam lingkungan terbatas, seperti melakukan tugas dalam kontainer Docker, untuk mencegah serangan sistem langsung. Membuat mekanisme cadangan dan logika pengulangan ketika sistem tertentu merespons dengan kesalahan adalah cara lain guna mencegah kegagalan sistem yang lebih besar.

## Human-in-the-Loop

Cara efektif lain untuk membangun sistem Agen AI yang terpercaya adalah menggunakan Human-in-the-loop. Ini menciptakan alur di mana pengguna dapat memberikan umpan balik kepada Agen selama proses berjalan. Pengguna pada dasarnya bertindak sebagai agen dalam sistem multi-agen dan memberikan persetujuan atau penghentian proses yang sedang berjalan.

![Human in The Loop](../../../translated_images/id/human-in-the-loop.5f0068a678f62f4f.webp)

Berikut cuplikan kode menggunakan AutoGen untuk menunjukkan bagaimana konsep ini diterapkan:

```python

# Buat agen.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Gunakan input() untuk mendapatkan masukan pengguna dari konsol.

# Buat kondisi terminasi yang akan mengakhiri percakapan ketika pengguna mengatakan "APPROVE".
termination = TextMentionTermination("APPROVE")

# Buat tim.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Jalankan percakapan dan alirkan ke konsol.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Gunakan asyncio.run(...) saat menjalankan dalam skrip.
await Console(stream)

```

## Kesimpulan

Membangun agen AI yang terpercaya memerlukan desain yang hati-hati, langkah-langkah keamanan yang kuat, dan iterasi berkelanjutan. Dengan menerapkan sistem meta prompting yang terstruktur, memahami ancaman potensial, dan menerapkan strategi mitigasi, pengembang dapat menciptakan agen AI yang aman dan efektif. Selain itu, mengintegrasikan pendekatan human-in-the-loop memastikan agen AI tetap selaras dengan kebutuhan pengguna sambil meminimalkan risiko. Seiring AI terus berkembang, mempertahankan sikap proaktif terhadap keamanan, privasi, dan pertimbangan etika akan menjadi kunci untuk membangun kepercayaan dan keandalan dalam sistem yang didorong oleh AI.

### Punya Pertanyaan Lebih Lanjut tentang Membangun Agen AI Terpercaya?

Bergabunglah dengan [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk bertemu dengan pembelajar lain, menghadiri jam kantor, dan mendapatkan jawaban atas pertanyaan Agen AI Anda.

## Sumber Daya Tambahan

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Ikhtisar AI Bertanggung Jawab</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Evaluasi model AI generatif dan aplikasi AI</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Pesan sistem keamanan</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Template Penilaian Risiko</a>

## Pelajaran Sebelumnya

[Agentic RAG](../05-agentic-rag/README.md)

## Pelajaran Selanjutnya

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berusaha untuk akurat, harap diingat bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang sahih. Untuk informasi penting, disarankan menggunakan jasa terjemahan profesional oleh manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau kesalahinterpretasian yang timbul dari penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->