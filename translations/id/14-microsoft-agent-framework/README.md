# Menjelajahi Microsoft Agent Framework

![Agent Framework](../../../translated_images/id/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Pendahuluan

Pelajaran ini akan membahas:

- Memahami Microsoft Agent Framework: Fitur Utama dan Nilai  
- Menjelajahi Konsep Kunci Microsoft Agent Framework
- Membandingkan MAF dengan Semantic Kernel dan AutoGen: Panduan Migrasi

## Tujuan Pembelajaran

Setelah menyelesaikan pelajaran ini, Anda akan mengetahui cara:

- Membangun AI Agent Siap Produksi menggunakan Microsoft Agent Framework
- Menerapkan fitur inti Microsoft Agent Framework pada Kasus Penggunaan Agen Anda
- Memigrasi dan mengintegrasikan framework dan alat Agentic yang sudah ada  

## Contoh Kode

Contoh kode untuk [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) dapat ditemukan di repositori ini di bawah file `xx-python-agent-framework` dan `xx-dotnet-agent-framework`.

## Memahami Microsoft Agent Framework

![Framework Intro](../../../translated_images/id/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) dibangun di atas pengalaman dan pembelajaran dari Semantic Kernel dan AutoGen. Ini menawarkan fleksibilitas untuk menangani berbagai macam kasus penggunaan agentic yang terlihat baik dalam lingkungan produksi maupun penelitian, termasuk:

- **Orkestrasi Agen Berurutan** dalam skenario di mana alur kerja langkah demi langkah dibutuhkan.
- **Orkestrasi Konkuren** dalam skenario di mana agen perlu menyelesaikan tugas secara bersamaan.
- **Orkestrasi Obrolan Grup** dalam skenario di mana agen dapat berkolaborasi bersama pada satu tugas.
- **Orkestrasi Penyerahan Tugas** dalam skenario di mana agen menyerahkan tugas satu sama lain saat subtugas selesai.
- **Orkestrasi Magnetik** dalam skenario di mana agen manajer membuat dan memodifikasi daftar tugas serta mengatur koordinasi subagen untuk menyelesaikan tugas.

Untuk menghadirkan AI Agent dalam Produksi, MAF juga menyertakan fitur untuk:

- **Observabilitas** melalui penggunaan OpenTelemetry di mana setiap aksi AI Agent termasuk pemanggilan alat, langkah orkestrasi, alur pemikiran, dan pemantauan kinerja melalui dashboard Microsoft Foundry.
- **Keamanan** dengan meng-host agen secara native di Microsoft Foundry yang mencakup kontrol keamanan seperti akses berbasis peran, penanganan data pribadi, dan keamanan konten bawaan.
- **Daya Tahan** karena thread dan alur kerja agen dapat dijeda, dilanjutkan, dan pulih dari kesalahan yang memungkinkan proses berjalan lebih lama.
- **Kontrol** karena alur kerja manusia dalam loop didukung di mana tugas ditandai sebagai memerlukan persetujuan manusia.

Microsoft Agent Framework juga fokus pada interoperabilitas dengan:

- **Bersifat Cloud-agnostic** - Agen dapat dijalankan di container, on-premise, dan di berbagai cloud berbeda.
- **Bersifat Provider-agnostic** - Agen dapat dibuat melalui SDK pilihan Anda termasuk Azure OpenAI dan OpenAI.
- **Mengintegrasikan Standar Terbuka** - Agen dapat memanfaatkan protokol seperti Agent-to-Agent (A2A) dan Model Context Protocol (MCP) untuk menemukan dan menggunakan agen serta alat lain.
- **Plugin dan Connector** - Koneksi dapat dilakukan ke layanan data dan memori seperti Microsoft Fabric, SharePoint, Pinecone, dan Qdrant.

Mari kita lihat bagaimana fitur-fitur ini diterapkan pada beberapa konsep inti Microsoft Agent Framework.

## Konsep Kunci Microsoft Agent Framework

### Agen

![Agent Framework](../../../translated_images/id/agent-components.410a06daf87b4fef.webp)

**Membuat Agen**

Pembuatan agen dilakukan dengan mendefinisikan layanan inferensi (Penyedia LLM),  
serangkaian instruksi yang harus diikuti AI Agent, dan `nama` yang ditetapkan:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Yang di atas menggunakan `Azure OpenAI` tetapi agen dapat dibuat menggunakan berbagai layanan termasuk `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

API `Responses`, `ChatCompletion` OpenAI

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

atau agen jarak jauh menggunakan protokol A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Menjalankan Agen**

Agen dijalankan menggunakan metode `.run` atau `.run_stream` untuk respons non-streaming atau streaming.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Setiap jalannya agen juga dapat memiliki opsi untuk menyesuaikan parameter seperti `max_tokens` yang digunakan agen, `tools` yang dapat dipanggil oleh agen, dan bahkan `model` yang digunakan untuk agen.

Ini berguna dalam kasus di mana model atau alat tertentu diperlukan untuk menyelesaikan tugas pengguna.

**Alat**

Alat dapat didefinisikan baik saat mendefinisikan agen:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Saat membuat ChatAgent secara langsung

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

dan juga saat menjalankan agen:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Alat disediakan hanya untuk pemakaian kali ini )
```

**Thread Agen**

Thread Agen digunakan untuk menangani percakapan multi-turn. Thread dapat dibuat dengan:

- Menggunakan `get_new_thread()` yang memungkinkan thread disimpan seiring waktu  
- Membuat thread secara otomatis saat menjalankan agen dan thread tersebut hanya bertahan selama jalannya saat ini.

Untuk membuat thread, kodenya seperti ini:

```python
# Buat thread baru.
thread = agent.get_new_thread() # Jalankan agen dengan thread tersebut.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Anda kemudian dapat menyerialisasi thread untuk disimpan guna penggunaan nanti:

```python
# Buat thread baru.
thread = agent.get_new_thread() 

# Jalankan agen dengan thread.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serialisasi thread untuk penyimpanan.

serialized_thread = await thread.serialize() 

# Deserialisasi status thread setelah memuat dari penyimpanan.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware Agen**

Agen berinteraksi dengan alat dan LLM untuk menyelesaikan tugas pengguna. Dalam skenario tertentu, kita ingin mengeksekusi atau melacak interaksi tersebut. Middleware agen memungkinkan kita melakukan ini melalui:

*Middleware Fungsi*

Middleware ini memungkinkan kita mengeksekusi aksi antara agen dan fungsi/alat yang akan dipanggilnya. Contohnya adalah ketika Anda ingin melakukan pencatatan pada pemanggilan fungsi.

Dalam kode di bawah, `next` menentukan apakah middleware berikutnya atau fungsi sebenarnya harus dipanggil.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Pra-pemrosesan: Log sebelum eksekusi fungsi
    print(f"[Function] Calling {context.function.name}")

    # Lanjutkan ke middleware berikutnya atau eksekusi fungsi
    await next(context)

    # Pasca-pemrosesan: Log setelah eksekusi fungsi
    print(f"[Function] {context.function.name} completed")
```

*Middleware Obrolan*

Middleware ini memungkinkan kita mengeksekusi atau mencatat aksi antara agen dan permintaan ke LLM.

Ini berisi informasi penting seperti `messages` yang dikirim ke layanan AI.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Pra-pemrosesan: Catat sebelum panggilan AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Lanjutkan ke middleware atau layanan AI berikutnya
    await next(context)

    # Pasca-pemrosesan: Catat setelah respons AI
    print("[Chat] AI response received")

```

**Memori Agen**

Seperti yang dibahas dalam pelajaran `Agentic Memory`, memori adalah elemen penting untuk memungkinkan agen beroperasi dalam berbagai konteks. MAF menawarkan beberapa jenis memori:

*Penyimpanan Dalam Memori*

Ini adalah memori yang disimpan dalam thread selama runtime aplikasi.

```python
# Buat sebuah thread baru.
thread = agent.get_new_thread() # Jalankan agen dengan thread tersebut.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Pesan Persisten*

Memori ini digunakan saat menyimpan riwayat percakapan antar sesi berbeda. Didefinisikan menggunakan `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Buat penyimpanan pesan khusus
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Memori Dinamis*

Memori ini ditambahkan ke konteks sebelum agen dijalankan. Memori ini dapat disimpan di layanan eksternal seperti mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Menggunakan Mem0 untuk kemampuan memori lanjutan
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**Observabilitas Agen**

Observabilitas penting untuk membangun sistem agentic yang andal dan dapat dipelihara. MAF terintegrasi dengan OpenTelemetry untuk menyediakan pelacakan dan pengukuran demi observabilitas yang lebih baik.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # melakukan sesuatu
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Alur Kerja

MAF menawarkan alur kerja yang merupakan langkah-langkah yang telah ditetapkan untuk menyelesaikan tugas dan mencakup AI agent sebagai komponen dalam langkah-langkah tersebut.

Alur kerja terdiri dari berbagai komponen yang memungkinkan aliran kontrol yang lebih baik. Alur kerja juga mendukung **orkestrasi multi-agen** dan **checkpointing** untuk menyimpan status alur kerja.

Komponen inti dari sebuah alur kerja adalah:

**Eksekutor**

Eksekutor menerima pesan input, melakukan tugas yang ditugaskan, dan kemudian menghasilkan pesan output. Ini melanjutkan alur kerja menuju penyelesaian tugas yang lebih besar. Eksekutor dapat berupa agen AI atau logika kustom.

**Edges**

Edges digunakan untuk mendefinisikan aliran pesan dalam alur kerja. Ini bisa berupa:

*Edges Langsung* - Koneksi satu-ke-satu sederhana antar eksekutor:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Edges Kondisional* - Diaktifkan setelah kondisi tertentu terpenuhi. Misalnya, ketika kamar hotel tidak tersedia, eksekutor dapat menyarankan opsi lain.

*Edges Switch-case* - Mengarahkan pesan ke eksekutor berbeda berdasarkan kondisi yang didefinisikan. Contohnya, jika pelanggan travel memiliki akses prioritas maka tugas mereka akan ditangani melalui alur kerja lain.

*Edges Fan-out* - Mengirim satu pesan ke beberapa target.

*Edges Fan-in* - Mengumpulkan beberapa pesan dari berbagai eksekutor dan mengirim ke satu target.

**Event**

Untuk menyediakan observabilitas yang lebih baik ke dalam alur kerja, MAF menawarkan event bawaan untuk pelaksanaan termasuk:

- `WorkflowStartedEvent` - Eksekusi alur kerja dimulai  
- `WorkflowOutputEvent` - Alur kerja menghasilkan output  
- `WorkflowErrorEvent` - Alur kerja mengalami kesalahan  
- `ExecutorInvokeEvent` - Eksekutor mulai memproses  
- `ExecutorCompleteEvent` - Eksekutor selesai memproses  
- `RequestInfoEvent` - Sebuah permintaan dikeluarkan

## Migrasi Dari Framework Lain (Semantic Kernel dan AutoGen)

### Perbedaan antara MAF dan Semantic Kernel

**Pembuatan Agen yang Disederhanakan**

Semantic Kernel bergantung pada pembuatan instance Kernel untuk setiap agen. MAF menggunakan pendekatan yang disederhanakan dengan menggunakan ekstensi untuk penyedia utama.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Pembuatan Thread Agen**

Semantic Kernel mengharuskan thread dibuat secara manual. Dalam MAF, thread langsung ditugaskan ke agen.

```python
thread = agent.get_new_thread() # Jalankan agen dengan thread.
```

**Registrasi Alat**

Dalam Semantic Kernel, alat didaftarkan ke Kernel kemudian Kernel diteruskan ke agen. Dalam MAF, alat didaftarkan langsung saat proses pembuatan agen.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Perbedaan antara MAF dan AutoGen

**Tim vs Alur Kerja**

`Teams` adalah struktur event untuk aktivitas berbasis event dengan agen di AutoGen. MAF menggunakan `Workflows` yang mengarahkan data ke eksekutor melalui arsitektur berbasis grafik.

**Pembuatan Alat**

AutoGen menggunakan `FunctionTool` untuk membungkus fungsi agar dapat dipanggil agen. MAF menggunakan @ai_function yang beroperasi serupa namun juga menginfer skema secara otomatis untuk setiap fungsi.

**Perilaku Agen**

Agen adalah agen single-turn secara default di AutoGen kecuali `max_tool_iterations` disetel lebih tinggi. Dalam MAF, `ChatAgent` adalah multi-turn secara default yang berarti ia akan terus memanggil alat sampai tugas pengguna selesai.

## Contoh Kode

Contoh kode untuk Microsoft Agent Framework dapat ditemukan di repositori ini di bawah file `xx-python-agent-framework` dan `xx-dotnet-agent-framework`.

## Punya Pertanyaan Lebih Lanjut Tentang Microsoft Agent Framework?

Bergabunglah dengan [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk bertemu dengan pelajar lain, menghadiri jam kantor, dan mendapatkan jawaban atas pertanyaan AI Agents Anda.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berupaya untuk memberikan terjemahan yang akurat, harap diingat bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang sah dan resmi. Untuk informasi penting, disarankan menggunakan jasa terjemahan profesional oleh penerjemah manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau salah tafsir yang timbul dari penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->