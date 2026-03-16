[![Ejen AI Boleh Dipercayai](../../../translated_images/ms/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klik imej di atas untuk menonton video pelajaran ini)_

# Membina Ejen AI Boleh Dipercayai

## Pengenalan

Pelajaran ini akan merangkumi:

- Cara membina dan menerapkan Ejen AI yang selamat dan berkesan
- Pertimbangan keselamatan penting semasa membangunkan Ejen AI.
- Cara mengekalkan privasi data dan pengguna semasa membangunkan Ejen AI.

## Matlamat Pembelajaran

Selepas menyelesaikan pelajaran ini, anda akan mengetahui bagaimana untuk:

- Mengenal pasti dan mengurangkan risiko semasa mencipta Ejen AI.
- Melaksanakan langkah keselamatan untuk memastikan data dan akses diurus dengan betul.
- Mewujudkan Ejen AI yang mengekalkan privasi data dan menyediakan pengalaman pengguna yang berkualiti.

## Keselamatan

Mari kita mula dengan melihat bagaimana membina aplikasi ejen yang selamat. Keselamatan bermaksud ejen AI berfungsi sebagaimana yang direka. Sebagai pembina aplikasi ejen, kita mempunyai kaedah dan alat untuk memaksimumkan keselamatan:

### Membangunkan Rangka Kerja Mesej Sistem

Jika anda pernah membina aplikasi AI menggunakan Model Bahasa Besar (LLMs), anda tahu kepentingan mereka bentuk prompt sistem yang kukuh atau mesej sistem. Prompt ini menetapkan peraturan meta, arahan, dan garis panduan untuk bagaimana LLM akan berinteraksi dengan pengguna dan data.

Bagi Ejen AI, prompt sistem lebih penting kerana Ejen AI akan memerlukan arahan yang sangat khusus untuk menyelesaikan tugas yang telah kita reka untuk mereka.

Untuk mencipta prompt sistem yang boleh diskala, kita boleh menggunakan rangka kerja mesej sistem untuk membina satu atau lebih ejen dalam aplikasi kita:

![Membangunkan Rangka Kerja Mesej Sistem](../../../translated_images/ms/system-message-framework.3a97368c92d11d68.webp)

#### Langkah 1: Cipta Mesej Sistem Meta 

Meta prompt akan digunakan oleh LLM untuk menjana prompt sistem bagi ejen yang kita cipta. Kita mereka bentuknya sebagai templat supaya kita boleh dengan cekap mencipta pelbagai ejen jika perlu.

Berikut adalah contoh mesej sistem meta yang akan kita berikan kepada LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Langkah 2: Cipta prompt asas

Langkah seterusnya adalah mencipta prompt asas untuk menerangkan Ejen AI. Anda harus memasukkan peranan ejen, tugas yang ejen akan selesaikan, dan sebarang tanggungjawab lain ejen.

Berikut adalah contoh:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Langkah 3: Berikan Mesej Sistem Asas kepada LLM

Sekarang kita boleh mengoptimumkan mesej sistem ini dengan menyediakan mesej sistem meta sebagai mesej sistem dan mesej sistem asas kita.

Ini akan menghasilkan mesej sistem yang direka dengan lebih baik untuk membimbing ejen AI kita:

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

#### Langkah 4: Ulang dan Perbaiki

Nilai rangka kerja mesej sistem ini ialah kemampuannya untuk menskalakan penciptaan mesej sistem daripada pelbagai ejen dengan lebih mudah serta memperbaiki mesej sistem anda dari masa ke masa. Jarang sekali anda akan memiliki mesej sistem yang berfungsi pada percubaan pertama untuk kes penggunaan lengkap anda. Mampu membuat penyesuaian dan pembaikan kecil dengan menukar mesej sistem asas dan menjalankannya melalui sistem akan membolehkan anda membandingkan dan menilai hasilnya.

## Memahami Ancaman

Untuk membina ejen AI yang boleh dipercayai, adalah penting untuk memahami dan mengurangkan risiko dan ancaman kepada ejen AI anda. Mari kita lihat beberapa daripada pelbagai ancaman kepada ejen AI dan bagaimana anda boleh merancang dan bersedia dengan lebih baik untuknya.

![Memahami Ancaman](../../../translated_images/ms/understanding-threats.89edeada8a97fc0f.webp)

### Tugas dan Arahan

**Penerangan:** Penyerang cuba mengubah arahan atau matlamat ejen AI melalui prompting atau manipulasi input.

**Mitigasi**: Laksanakan pemeriksaan pengesahan dan penapis input untuk mengesan prompt yang berpotensi berbahaya sebelum ia diproses oleh Ejen AI. Oleh kerana serangan ini biasanya memerlukan interaksi yang kerap dengan Ejen, mengehadkan bilangan giliran dalam perbualan adalah satu lagi cara untuk mengelakkan jenis serangan ini.

### Akses kepada Sistem Kritikal

**Penerangan**: Jika ejen AI mempunyai akses kepada sistem dan perkhidmatan yang menyimpan data sensitif, penyerang boleh menjejaskan komunikasi antara ejen dan perkhidmatan ini. Ini boleh menjadi serangan langsung atau cubaan tidak langsung untuk mendapatkan maklumat tentang sistem ini melalui ejen.

**Mitigasi**: Ejen AI sepatutnya mempunyai akses kepada sistem berdasarkan keperluan sahaja untuk mencegah jenis serangan ini. Komunikasi antara ejen dan sistem juga harus selamat. Melaksanakan pengesahan dan kawalan akses adalah cara lain untuk melindungi maklumat ini.

### Bebanan Berlebihan pada Sumber dan Perkhidmatan

**Penerangan:** Ejen AI boleh mengakses pelbagai alat dan perkhidmatan untuk menyelesaikan tugas. Penyerang boleh memanfaatkan kemampuan ini untuk menyerang perkhidmatan ini dengan menghantar sejumlah besar permintaan melalui Ejen AI, yang mungkin mengakibatkan kegagalan sistem atau kos yang tinggi.

**Mitigasi:** Laksanakan polisi untuk menghadkan bilangan permintaan yang boleh dibuat oleh ejen AI kepada sesuatu perkhidmatan. Mengehadkan bilangan giliran perbualan dan permintaan kepada ejen AI anda adalah satu lagi cara untuk mencegah jenis serangan ini.

### Pencemaran Pangkalan Pengetahuan

**Penerangan:** Jenis serangan ini tidak mensasarkan ejen AI secara langsung tetapi mensasarkan pangkalan pengetahuan dan perkhidmatan lain yang akan digunakan oleh ejen AI. Ini boleh melibatkan pemusnahan data atau maklumat yang akan digunakan oleh ejen AI untuk menyelesaikan tugas, menyebabkan respons yang berat sebelah atau tidak dimaksudkan kepada pengguna.

**Mitigasi:** Lakukan pengesahan berkala terhadap data yang akan digunakan oleh ejen AI dalam aliran kerjanya. Pastikan akses kepada data ini selamat dan hanya diubah oleh individu yang dipercayai untuk mengelakkan jenis serangan ini.

### Ralat Berantai

**Penerangan:** Ejen AI mengakses pelbagai alat dan perkhidmatan untuk menyelesaikan tugas. Ralat yang disebabkan oleh penyerang boleh menyebabkan kegagalan sistem lain yang disambungkan kepada ejen AI, menyebabkan serangan menjadi lebih meluas dan lebih sukar untuk diselesaikan.

**Mitigasi**: Salah satu kaedah untuk mengelakkan ini adalah dengan membiarkan Ejen AI beroperasi dalam persekitaran terhad, seperti melaksanakan tugas dalam kontena Docker, untuk mengelakkan serangan sistem langsung. Mewujudkan mekanisme sandaran dan logik percubaan semula apabila sistem tertentu memberi respons dengan ralat adalah satu lagi cara untuk mencegah kegagalan sistem yang lebih besar.

## Manusia-dalam-Kitaran

Kaedah berkesan lain untuk membina sistem Ejen AI yang boleh dipercayai adalah dengan menggunakan Manusia-dalam-Kitaran. Ini mewujudkan aliran di mana pengguna dapat memberikan maklum balas kepada Ejen semasa proses berjalan. Pengguna pada dasarnya bertindak sebagai ejen dalam sistem berbilang-ejen dan dengan memberikan kelulusan atau penamatan proses yang sedang berjalan.

![Manusia dalam Kitaran](../../../translated_images/ms/human-in-the-loop.5f0068a678f62f4f.webp)

Berikut ialah contoh kod menggunakan AutoGen untuk menunjukkan bagaimana konsep ini dilaksanakan:

```python

# Cipta ejen.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Gunakan input() untuk mendapatkan input pengguna dari konsol.

# Buat syarat penamatan yang akan menamatkan perbualan apabila pengguna berkata "APPROVE".
termination = TextMentionTermination("APPROVE")

# Cipta pasukan.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Jalankan perbualan dan alirkan ke konsol.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Gunakan asyncio.run(...) apabila menjalankan dalam skrip.
await Console(stream)

```

## Kesimpulan

Membina ejen AI yang boleh dipercayai memerlukan reka bentuk yang teliti, langkah keselamatan yang mantap, dan iterasi berterusan. Dengan melaksanakan sistem meta-prompt yang berstruktur, memahami ancaman potensi, dan menerapkan strategi mitigasi, pembangun dapat mencipta ejen AI yang selamat dan berkesan. Selain itu, menggabungkan pendekatan manusia-dalam-kitaran memastikan ejen AI kekal selaras dengan keperluan pengguna sambil meminimumkan risiko. Seiring AI terus berkembang, mengekalkan sikap proaktif terhadap keselamatan, privasi, dan pertimbangan etika akan menjadi kunci bagi memupuk kepercayaan dan kebolehpercayaan dalam sistem yang digerakkan AI.

### Ada Soalan Lagi tentang Membina Ejen AI Boleh Dipercayai?

Sertai [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk berjumpa dengan pelajar lain, menghadiri waktu pejabat dan mendapatkan jawapan kepada soalan Ejen AI anda.

## Sumber Tambahan

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Tinjauan AI Bertanggungjawab</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Penilaian model AI generatif dan aplikasi AI</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Mesej sistem keselamatan</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Templat Penilaian Risiko</a>

## Pelajaran Sebelumnya

[Agentic RAG](../05-agentic-rag/README.md)

## Pelajaran Seterusnya

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Penafian:
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha memastikan ketepatan, sila ambil perhatian bahawa terjemahan automatik mungkin mengandungi ralat atau ketidaktepatan. Dokumen asal dalam bahasa asalnya hendaklah dianggap sebagai sumber yang sah. Untuk maklumat yang kritikal, penterjemahan profesional oleh penterjemah manusia adalah disyorkan. Kami tidak bertanggungjawab terhadap sebarang salah faham atau salah tafsiran yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->