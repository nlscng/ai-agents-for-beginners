[![Planning Design Pattern](../../../translated_images/id/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Klik gambar di atas untuk melihat video pelajaran ini)_

# Perencanaan Desain

## Pengantar

Pelajaran ini akan membahas

* Mendefinisikan tujuan keseluruhan yang jelas dan memecah tugas yang kompleks menjadi tugas-tugas yang dapat dikelola.
* Memanfaatkan output terstruktur untuk respons yang lebih andal dan dapat dibaca mesin.
* Menerapkan pendekatan berbasis acara untuk menangani tugas dinamis dan input tak terduga.

## Tujuan Pembelajaran

Setelah menyelesaikan pelajaran ini, Anda akan memahami tentang:

* Mengidentifikasi dan menetapkan tujuan keseluruhan untuk agen AI, memastikan ia mengetahui dengan jelas apa yang harus dicapai.
* Memecah tugas yang kompleks menjadi sub-tugas yang dapat dikelola dan mengaturnya dalam urutan logis.
* Melengkapi agen dengan alat yang tepat (misalnya, alat pencarian atau alat analitik data), memutuskan kapan dan bagaimana alat tersebut digunakan, serta menangani situasi tak terduga yang muncul.
* Mengevaluasi hasil sub-tugas, mengukur kinerja, dan mengulangi tindakan untuk meningkatkan output akhir.

## Mendefinisikan Tujuan Keseluruhan dan Memecah Tugas

![Defining Goals and Tasks](../../../translated_images/id/defining-goals-tasks.d70439e19e37c47a.webp)

Sebagian besar tugas di dunia nyata terlalu kompleks untuk ditangani dalam satu langkah. Agen AI membutuhkan tujuan ringkas untuk memandu perencanaan dan tindakannya. Misalnya, pertimbangkan tujuan:

    "Membuat itinerary perjalanan selama 3 hari."

Meskipun sederhana untuk dikemukakan, tetap perlu penyempurnaan. Semakin jelas tujuan, semakin baik agen (dan kolaborator manusia) dapat fokus untuk mencapai hasil yang tepat, seperti membuat itinerary yang komprehensif dengan pilihan penerbangan, rekomendasi hotel, dan saran aktivitas.

### Dekompisi Tugas

Tugas besar atau rumit menjadi lebih mudah dikelola ketika dibagi menjadi sub-tugas yang berorientasi pada tujuan.
Untuk contoh itinerary perjalanan, Anda dapat memecah tujuan menjadi:

* Pemesanan Penerbangan
* Pemesanan Hotel
* Penyewaan Mobil
* Personalisasi

Setiap sub-tugas kemudian dapat ditangani oleh agen atau proses yang khusus. Satu agen mungkin fokus mencari penawaran penerbangan terbaik, agen lain mengurusi pemesanan hotel, dan seterusnya. Agen koordinasi atau “hilir” kemudian menggabungkan hasil ini menjadi satu itinerary yang terpadu untuk pengguna akhir.

Pendekatan modular ini juga memungkinkan peningkatan secara bertahap. Misalnya, Anda bisa menambahkan agen khusus untuk Rekomendasi Makanan atau Saran Aktivitas Lokal dan menyempurnakan itinerary seiring waktu.

### Output Terstruktur

Model Bahasa Besar (LLM) dapat menghasilkan output terstruktur (misalnya JSON) yang lebih mudah untuk diproses dan diurai oleh agen atau layanan hilir. Ini sangat berguna dalam konteks multi-agen, di mana kita dapat melakukan tindakan atas tugas-tugas ini setelah output perencanaan diterima. Lihat <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogpost</a> ini untuk gambaran singkat.

Cuplikan kode Python berikut menunjukkan agen perencanaan sederhana yang memecah tujuan menjadi sub-tugas dan menghasilkan rencana terstruktur:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Model SubTugas Perjalanan
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # kita ingin menetapkan tugas kepada agen

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Untuk mengautentikasi dengan model Anda perlu membuat token akses pribadi (PAT) di pengaturan GitHub Anda.
    # Buat token PAT Anda dengan mengikuti petunjuk di sini: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definisikan pesan pengguna
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Pastikan konten respons adalah string JSON yang valid sebelum memuatnya
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Isi respons bukan string JSON yang valid")

# # Cetak konten respons setelah memuatnya sebagai JSON
# pprint(json.loads(response_content))

# Validasi konten respons dengan model MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Agen Perencanaan dengan Orkestrasi Multi-Agen

Dalam contoh ini, Agen Semantic Router menerima permintaan pengguna (misalnya, "Saya butuh rencana hotel untuk perjalanan saya.").

Perencana kemudian:

* Menerima Rencana Hotel: Perencana mengambil pesan pengguna dan, berdasarkan prompt sistem (termasuk detail agen yang tersedia), menghasilkan rencana perjalanan terstruktur.
* Mendaftar Agen dan Alat Mereka: Registri agen memuat daftar agen (misalnya untuk penerbangan, hotel, penyewaan mobil, dan aktivitas) beserta fungsi atau alat yang mereka tawarkan.
* Mengarahkan Rencana ke Agen Terkait: Tergantung pada jumlah sub-tugas, perencana mengirim pesan langsung ke agen yang khusus (untuk skenario tugas tunggal) atau mengoordinasikan melalui manajer grup chat untuk kolaborasi multi-agen.
* Merangkum Hasil: Akhirnya, perencana merangkum rencana yang dihasilkan untuk kejelasan.
Contoh kode Python berikut mengilustrasikan langkah-langkah ini:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Model SubTugas Perjalanan

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # kami ingin menetapkan tugas kepada agen

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Buat klien dengan variabel lingkungan yang diperiksa tipe datanya

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definisikan pesan pengguna

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Pastikan isi respons adalah string JSON yang valid sebelum memuatnya

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Cetak isi respons setelah memuatnya sebagai JSON

pprint(json.loads(response_content))
```

Berikut ini adalah keluaran dari kode sebelumnya dan Anda dapat menggunakan output terstruktur ini untuk mengarahkan ke `assigned_agent` dan merangkum rencana perjalanan kepada pengguna akhir.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Notebook contoh dengan cuplikan kode sebelumnya tersedia [di sini](07-autogen.ipynb).

### Perencanaan Iteratif

Beberapa tugas membutuhkan interaksi bolak-balik atau perencanaan ulang, di mana hasil dari satu sub-tugas mempengaruhi yang berikutnya. Misalnya, jika agen menemukan format data tak terduga saat memesan penerbangan, ia mungkin perlu menyesuaikan strateginya sebelum melanjutkan ke pemesanan hotel.

Selain itu, umpan balik pengguna (misalnya, keputusan manusia yang lebih memilih penerbangan lebih awal) dapat memicu perencanaan ulang sebagian. Pendekatan iteratif yang dinamis ini memastikan solusi akhir sesuai dengan keterbatasan dunia nyata dan preferensi pengguna yang berkembang.

misalnya kode contoh

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. sama seperti kode sebelumnya dan teruskan riwayat pengguna, rencana saat ini
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. rencanakan ulang dan kirim tugas kepada agen yang bersangkutan
```

Untuk perencanaan yang lebih komprehensif, lihat Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogpost</a> untuk menyelesaikan tugas kompleks.

## Ringkasan

Dalam artikel ini kita telah melihat contoh bagaimana kita dapat membuat perencana yang dapat secara dinamis memilih agen yang tersedia yang telah didefinisikan. Output dari Perencana memecah tugas dan menugaskan agen sehingga dapat dieksekusi. Diasumsikan agen memiliki akses ke fungsi/alat yang dibutuhkan untuk menjalankan tugas. Selain agen, Anda dapat memasukkan pola lain seperti refleksi, summarizer, dan round robin chat untuk kustomisasi lebih lanjut.

## Sumber Tambahan

AutoGen Magentic One - Sistem multi-agen generalis untuk menyelesaikan tugas kompleks dan telah mencapai hasil mengesankan pada berbagai benchmark agen yang menantang. Referensi: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Dalam implementasi ini orkestrator membuat rencana spesifik tugas dan mendelegasikan tugas tersebut ke agen yang tersedia. Selain perencanaan, orkestrator juga menggunakan mekanisme pelacakan untuk memantau kemajuan tugas dan melakukan perencanaan ulang sesuai kebutuhan.

### Ada Pertanyaan Lagi tentang Pola Perencanaan Desain?

Bergabunglah dengan [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk bertemu dengan pembelajar lain, menghadiri jam kantor, dan mendapatkan jawaban atas pertanyaan tentang Agen AI Anda.

## Pelajaran Sebelumnya

[Building Trustworthy AI Agents](../06-building-trustworthy-agents/README.md)

## Pelajaran Berikutnya

[Multi-Agent Design Pattern](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Penafian**:
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berupaya untuk akurasi, harap diingat bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang otoritatif. Untuk informasi penting, disarankan menggunakan terjemahan profesional oleh manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau interpretasi keliru yang timbul dari penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->