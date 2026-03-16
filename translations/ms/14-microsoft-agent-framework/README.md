# Menerokai Microsoft Agent Framework

![Rangka Kerja Ejen](../../../translated_images/ms/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Pengenalan

Pelajaran ini akan merangkumi:

- Memahami Microsoft Agent Framework: Ciri Utama dan Nilai  
- Meneroka Konsep Utama Microsoft Agent Framework
- Membandingkan MAF dengan Semantic Kernel dan AutoGen: Panduan Migrasi

## Matlamat Pembelajaran

Selepas menyelesaikan pelajaran ini, anda akan tahu bagaimana untuk:

- Membina Ejen AI Sedia untuk Pengeluaran menggunakan Microsoft Agent Framework
- Mengaplikasikan ciri teras Microsoft Agent Framework kepada Kes Penggunaan Ejen anda
- Memigrasi dan mengintegrasikan rangka kerja dan alat ejen sedia ada  

## Contoh Kod 

Contoh kod untuk [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) boleh didapati dalam repositori ini di bawah fail `xx-python-agent-framework` dan `xx-dotnet-agent-framework` fail.

## Memahami Microsoft Agent Framework

![Pengenalan Rangka Kerja](../../../translated_images/ms/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) membina di atas pengalaman dan pembelajaran dari Semantic Kernel dan AutoGen. Ia menawarkan fleksibiliti untuk menangani pelbagai kes penggunaan ejen yang dilihat dalam kedua-dua persekitaran pengeluaran dan penyelidikan termasuk:

- **Orkestrasi Ejen Bersiri** dalam senario di mana aliran kerja langkah demi langkah diperlukan.
- **Orkestrasi Serentak** dalam senario di mana ejen perlu menyelesaikan tugasan pada masa yang sama.
- **Orkestrasi sembang berkumpulan** dalam senario di mana ejen boleh bekerjasama pada satu tugasan.
- **Orkestrasi Serah Tugas** dalam senario di mana ejen menyerahkan tugasan antara satu sama lain apabila subtugas diselesaikan.
- **Orkestrasi Magnetik** dalam senario di mana ejen pengurus mencipta dan mengubah senarai tugasan serta mengendalikan koordinasi subejen untuk menyelesaikan tugasan.

Untuk menyampaikan Ejen AI dalam Pengeluaran, MAF juga menyertakan ciri untuk:

- **Observabiliti** melalui penggunaan OpenTelemetry di mana setiap tindakan Ejen AI termasuk pemanggilan alat, langkah orkestrasi, aliran penaakulan dan pemantauan prestasi melalui papan pemuka Microsoft Foundry.
- **Keselamatan** dengan mengehoskan ejen secara asli di Microsoft Foundry yang merangkumi kawalan keselamatan seperti akses berasaskan peranan, pengendalian data peribadi dan keselamatan kandungan terbina dalam.
- **Ketahanan** kerana thread ejen dan aliran kerja boleh berhenti sementara, disambung semula dan pulih daripada ralat yang membolehkan proses berjalan lebih lama.
- **Kawalan** kerana aliran kerja dengan campur tangan manusia disokong di mana tugasan ditandakan sebagai memerlukan kelulusan manusia.

Microsoft Agent Framework juga menumpukan kepada kebolehsinambungan dengan:

- **Bebas Awan** - Ejen boleh dijalankan dalam kontena, on-prem dan merentasi pelbagai awan yang berbeza.
- **Bebas Penyedia** - Ejen boleh dicipta melalui SDK pilihan anda termasuk Azure OpenAI dan OpenAI
- **Mengintegrasikan Piawaian Terbuka** - Ejen boleh menggunakan protokol seperti Agent-to-Agent(A2A) dan Model Context Protocol (MCP) untuk menemui dan menggunakan ejen serta alat lain.
- **Pemalam dan Penyambung** - Sambungan boleh dibuat ke perkhidmatan data dan memori seperti Microsoft Fabric, SharePoint, Pinecone dan Qdrant.

Mari lihat bagaimana ciri-ciri ini digunakan kepada beberapa konsep teras Microsoft Agent Framework.

## Konsep Utama Microsoft Agent Framework

### Ejen

![Rangka Kerja Ejen](../../../translated_images/ms/agent-components.410a06daf87b4fef.webp)

**Mencipta Ejen**

Pembentukan ejen dilakukan dengan mentakrifkan perkhidmatan inferens (LLM Provider), satu set arahan untuk Ejen AI ikuti, dan `name` yang ditetapkan:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Di atas menggunakan `Azure OpenAI` tetapi ejen boleh dicipta menggunakan pelbagai perkhidmatan termasuk `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

atau ejen jauh menggunakan protokol A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Menjalankan Ejen**

Ejen dijalankan menggunakan kaedah `.run` atau `.run_stream` untuk respons tanpa aliran atau dengan aliran.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Setiap larian ejen juga boleh mempunyai pilihan untuk menyesuaikan parameter seperti `max_tokens` yang digunakan oleh ejen, `tools` yang boleh dipanggil oleh ejen, dan malahan `model` itu sendiri yang digunakan untuk ejen.

Ini berguna dalam kes di mana model atau alat tertentu diperlukan untuk menyelesaikan tugasan pengguna.

**Alat**

Alat boleh ditakrifkan semasa mentakrif ejen:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Apabila membuat ChatAgent secara langsung

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

dan juga ketika menjalankan ejen:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Alat disediakan hanya untuk sesi ini )
```

**Thread Ejen**

Thread ejen digunakan untuk mengendalikan perbualan berbilang giliran. Thread boleh dicipta dengan sama ada:

- Menggunakan `get_new_thread()` yang membolehkan thread disimpan dari masa ke masa
- Mencipta thread secara automatik ketika menjalankan ejen dan hanya membuat thread kekal semasa larian semasa.

Untuk mencipta thread, kod kelihatan seperti ini:

```python
# Buat utas baru.
thread = agent.get_new_thread() # Jalankan ejen dengan utas tersebut.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Anda kemudian boleh menserialkan thread untuk disimpan bagi kegunaan kemudian:

```python
# Cipta utas baru.
thread = agent.get_new_thread() 

# Jalankan ejen dengan utas itu.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serialkan utas untuk penyimpanan.

serialized_thread = await thread.serialize() 

# Nyahserialkan keadaan utas selepas memuatkan dari storan.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware Ejen**

Ejen berinteraksi dengan alat dan LLM untuk menyelesaikan tugasan pengguna. Dalam sesetengah senario, kita mahu melaksanakan atau mengesan interaksi di antara ini. Middleware ejen membolehkan kita melakukan ini melalui:

*Middleware Fungsi*

Middleware ini membolehkan kita melaksanakan tindakan di antara ejen dan fungsi/alat yang akan dipanggilnya. Contoh bila ini digunakan adalah apabila anda mungkin mahu melakukan sedikit log pada panggilan fungsi.

Dalam kod di bawah `next` mentakrifkan sama ada middleware seterusnya atau fungsi sebenar harus dipanggil.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Pra-pemprosesan: Log sebelum pelaksanaan fungsi
    print(f"[Function] Calling {context.function.name}")

    # Teruskan ke middleware seterusnya atau pelaksanaan fungsi
    await next(context)

    # Pasca-pemprosesan: Log selepas pelaksanaan fungsi
    print(f"[Function] {context.function.name} completed")
```

*Middleware Sembang*

Middleware ini membolehkan kita melaksanakan atau merekod tindakan di antara ejen dan permintaan kepada LLM .

Ini mengandungi maklumat penting seperti `messages` yang dihantar ke perkhidmatan AI.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Pra-pemprosesan: Log sebelum panggilan AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Teruskan ke middleware seterusnya atau perkhidmatan AI
    await next(context)

    # Pasca-pemprosesan: Log selepas respons AI
    print("[Chat] AI response received")

```

**Memori Ejen**

Seperti yang dibincangkan dalam pelajaran `Agentic Memory`, memori adalah elemen penting untuk membolehkan ejen beroperasi dalam konteks berbeza. MAF menawarkan beberapa jenis memori yang berbeza:

*Penyimpanan Dalam Memori*

Ini adalah memori yang disimpan dalam thread semasa runtime aplikasi.

```python
# Buat utas baru.
thread = agent.get_new_thread() # Jalankan ejen dengan utas itu.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Mesej Kekal*

Memori ini digunakan apabila menyimpan sejarah perbualan merentasi sesi yang berbeza. Ia ditakrifkan menggunakan `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Cipta stor mesej tersuai
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Memori Dinamik*

Memori ini ditambah ke konteks sebelum ejen dijalankan. Memori ini boleh disimpan dalam perkhidmatan luaran seperti mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Menggunakan Mem0 untuk keupayaan memori lanjutan
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

**Observabiliti Ejen**

Observabiliti penting untuk membina sistem ejen yang boleh dipercayai dan mudah diselenggara. MAF berintegrasi dengan OpenTelemetry untuk menyediakan penjejakan dan meter bagi observabiliti yang lebih baik.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # lakukan sesuatu
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Aliran Kerja

MAF menawarkan aliran kerja yang merupakan langkah pratakrif untuk menyelesaikan tugas dan memasukkan ejen AI sebagai komponen dalam langkah tersebut.

Aliran kerja terdiri daripada komponen berbeza yang membolehkan aliran kawalan lebih baik. Aliran kerja juga membolehkan **orkestrasi berbilang ejen** dan **checkpointing** untuk menyimpan keadaan aliran kerja.

Komponen teras bagi aliran kerja ialah:

**Pelaksana**

Pelaksana menerima mesej input, melaksanakan tugas yang ditugaskan, dan kemudian menghasilkan mesej output. Ini menggerakkan aliran kerja ke hadapan menuju penyelesaian tugasan yang lebih besar. Pelaksana boleh menjadi ejen AI atau logik tersuai.

**Tepi**

Tepi digunakan untuk mentakrif aliran mesej dalam aliran kerja. Ini boleh menjadi:

*Tepi Langsung* - Sambungan satu-ke-satu ringkas antara pelaksana:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Tepi Bersyarat* - Diaktifkan selepas syarat tertentu dipenuhi. Contohnya, apabila bilik hotel tidak tersedia, seorang pelaksana boleh mencadangkan pilihan lain.

*Tepi suis-kes* - Menghala mesej kepada pelaksana berbeza berdasarkan syarat yang ditetapkan. Contohnya. jika pelanggan perjalanan mempunyai akses keutamaan dan tugasan mereka akan dikendalikan melalui aliran kerja lain.

*Tepi Fan-out* - Hantar satu mesej ke pelbagai sasaran.

*Tepi Fan-in* - Mengumpul pelbagai mesej dari pelaksana yang berbeza dan menghantar ke satu sasaran.

**Peristiwa**

Untuk menyediakan observabiliti yang lebih baik ke dalam aliran kerja, MAF menawarkan peristiwa terbina untuk pelaksanaan termasuk:

- `WorkflowStartedEvent`  - Pelaksanaan aliran kerja bermula
- `WorkflowOutputEvent` - Aliran kerja menghasilkan output
- `WorkflowErrorEvent` - Aliran kerja menghadapi ralat
- `ExecutorInvokeEvent`  - Pelaksana mula memproses
- `ExecutorCompleteEvent`  -  Pelaksana selesai memproses
- `RequestInfoEvent` - Satu permintaan dikeluarkan

## Migrasi Dari Rangka Kerja Lain (Semantic Kernel dan AutoGen)

### Perbezaan antara MAF dan Semantic Kernel

**Penciptaan Ejen yang Dipermudahkan**

Semantic Kernel bergantung pada penciptaan satu instans Kernel untuk setiap ejen. MAF menggunakan pendekatan yang dipermudahkan dengan menggunakan peluasan untuk penyedia utama.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Penciptaan Thread Ejen**

Semantic Kernel memerlukan thread dicipta secara manual. Dalam MAF, thread ditetapkan terus kepada ejen.

```python
thread = agent.get_new_thread() # Jalankan ejen dengan utas.
```

**Pendaftaran Alat**

Dalam Semantic Kernel, alat didaftarkan ke Kernel dan Kernel kemudian dipass ke ejen. Dalam MAF, alat didaftarkan secara langsung semasa proses penciptaan ejen.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Perbezaan antara MAF dan AutoGen

**Teams vs Aliran Kerja**

`Teams` adalah struktur peristiwa untuk aktiviti dipacu-peristiwa dengan ejen dalam AutoGen. MAF menggunakan `Workflows` yang menghala data kepada pelaksana melalui seni bina berasaskan graf.

**Penciptaan Alat**

AutoGen menggunakan `FunctionTool` untuk membalut fungsi agar ejen dapat memanggilnya. MAF menggunakan @ai_function yang beroperasi serupa tetapi juga menambahkan inferens skema secara automatik untuk setiap fungsi.

**Tingkah Laku Ejen**

Ejen adalah ejen giliran tunggal secara lalai dalam AutoGen kecuali `max_tool_iterations` ditetapkan kepada sesuatu yang lebih tinggi. Dalam MAF `ChatAgent` adalah berbilang giliran secara lalai bermakna ia akan terus memanggil alat sehingga tugasan pengguna selesai.

## Contoh Kod 

Contoh kod untuk Microsoft Agent Framework boleh didapati dalam repositori ini di bawah fail `xx-python-agent-framework` dan `xx-dotnet-agent-framework` fail.

## Ada Lagi Soalan Mengenai Microsoft Agent Framework?

Sertai [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk berjumpa dengan pelajar lain, menghadiri waktu pejabat dan mendapatkan jawapan untuk soalan Ejen AI anda.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk ketepatan, sila ambil perhatian bahawa terjemahan automatik mungkin mengandungi ralat atau ketidaktepatan. Dokumen asal dalam bahasa asalnya hendaklah dianggap sebagai sumber yang sah. Untuk maklumat penting, penterjemahan profesional oleh penterjemah manusia adalah disyorkan. Kami tidak bertanggungjawab ke atas sebarang salah faham atau salah tafsir yang timbul daripada penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->