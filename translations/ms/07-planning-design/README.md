[![Corak Reka Bentuk Perancangan](../../../translated_images/ms/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Klik imej di atas untuk menonton video pelajaran ini)_

# Reka Bentuk Perancangan

## Pengenalan

Pelajaran ini akan merangkumi

* Menentukan matlamat keseluruhan yang jelas dan memecahkan tugasan yang kompleks kepada tugasan yang lebih mudah diurus.
* Memanfaatkan keluaran berstruktur untuk respons yang lebih boleh dipercayai dan boleh dibaca mesin.
* Menerapkan pendekatan berasaskan peristiwa untuk mengendalikan tugasan dinamik dan input yang tidak dijangka.

## Matlamat Pembelajaran

Selepas menyelesaikan pelajaran ini, anda akan memahami tentang:

* Mengenal pasti dan menetapkan matlamat keseluruhan untuk ejen AI, memastikan ia jelas mengetahui apa yang perlu dicapai.
* Menguraikan tugasan yang kompleks menjadi subtugas yang boleh diurus dan menyusunnya ke dalam urutan logik.
* Membekalkan ejen dengan alat yang sesuai (contohnya, alat carian atau alat analitik data), memutuskan bila dan bagaimana ia digunakan, dan mengendalikan situasi tidak dijangka yang timbul.
* Menilai hasil subtugas, mengukur prestasi, dan mengulangi tindakan untuk memperbaiki keluaran akhir.

## Menentukan Matlamat Keseluruhan dan Memecahkan Tugasan

![Menentukan Matlamat dan Tugasan](../../../translated_images/ms/defining-goals-tasks.d70439e19e37c47a.webp)

Kebanyakan tugasan dunia sebenar terlalu kompleks untuk ditangani dalam satu langkah. Ejen AI memerlukan objektif ringkas untuk membimbing perancangannya dan tindakannya. Sebagai contoh, pertimbangkan matlamat:

    "Generate a 3-day travel itinerary."

Walaupun mudah untuk dinyatakan, ia masih memerlukan penambahbaikan. Semakin jelas matlamat, semakin baik ejen (dan mana-mana kolaborator manusia) boleh memberi tumpuan untuk mencapai hasil yang betul, seperti mencipta itinerari menyeluruh dengan pilihan penerbangan, cadangan hotel, dan cadangan aktiviti.

### Penguraian Tugasan

Tugasan besar atau rumit menjadi lebih mudah diurus apabila dibahagikan kepada subtugas yang lebih kecil dan berorientasikan matlamat.
Untuk contoh itinerari perjalanan, anda boleh menguraikan matlamat kepada:

* Tempahan Penerbangan
* Tempahan Hotel
* Sewa Kereta
* Personalisasi

Setiap subtugas kemudian boleh ditangani oleh ejen atau proses khusus. Seorang ejen mungkin pakar dalam mencari tawaran penerbangan terbaik, satu lagi menumpukan pada tempahan hotel, dan sebagainya. Seorang ejen penyelaras atau “downstream” kemudian boleh menyusun hasil ini menjadi satu itinerari yang padu untuk pengguna akhir.

Pendekatan modular ini juga membenarkan peningkatan berperingkat. Sebagai contoh, anda boleh menambah ejen khusus untuk Cadangan Makanan atau Cadangan Aktiviti Tempatan dan memperhalusi itinerari dari masa ke masa.

### Keluaran berstruktur

Large Language Models (LLMs) boleh menjana keluaran berstruktur (contohnya JSON) yang lebih mudah untuk ejen atau perkhidmatan hiliran menguraikan dan proses. Ini amat berguna dalam konteks multi-ejen, di mana kita boleh melaksanakan tugasan ini selepas keluaran perancangan diterima. Rujuk <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">catatan blog</a> ini untuk gambaran ringkas.

Petikan Python berikut menunjukkan seorang ejen perancang mudah yang menguraikan matlamat kepada subtugas dan menjana pelan berstruktur:

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

# Model Subtugas Perjalanan
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # Kami ingin menetapkan tugasan kepada ejen

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Untuk mengesahkan dengan model anda perlu menjana token akses peribadi (PAT) dalam tetapan GitHub anda.
    # Buat token PAT anda dengan mengikuti arahan di sini: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Tentukan mesej pengguna
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

# # Pastikan kandungan respons adalah rentetan JSON yang sah sebelum memuatkannya
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Response content is not a valid JSON string")

# # Cetak kandungan respons selepas memuatkannya sebagai JSON
# pprint(json.loads(response_content))

# Sahkan kandungan respons dengan model MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Ejen Perancang dengan Orkestrasi Multi-Ejen

Dalam contoh ini, Semantic Router Agent menerima permintaan pengguna (contohnya, "I need a hotel plan for my trip.").

Perancang kemudian:

* Menerima Pelan Hotel: Perancang mengambil mesej pengguna dan, berdasarkan prompt sistem (termasuk butiran ejen yang tersedia), menjana pelan perjalanan yang berstruktur.
* Menyenaraikan Ejen dan Alat Mereka: Daftar ejen memegang senarai ejen (contohnya, untuk penerbangan, hotel, sewa kereta, dan aktiviti) bersama fungsi atau alat yang mereka tawarkan.
* Menghala Pelan kepada Ejen yang Berkaitan: Bergantung pada bilangan subtugas, perancang sama ada menghantar mesej secara langsung kepada ejen khusus (untuk senario tugasan tunggal) atau menyelaraskan melalui pengurus perbualan berkumpulan untuk kerjasama multi-ejen.
* Merumuskan Hasil: Akhirnya, perancang merumuskan pelan yang dijana untuk kejelasan.
Contoh kod Python berikut menggambarkan langkah-langkah ini:

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

# Model Subtugasan Perjalanan

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # kami ingin menetapkan tugasan kepada ejen

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Cipta klien dengan pembolehubah persekitaran yang diperiksa jenisnya

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Tentukan mesej pengguna

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

# Pastikan kandungan respons adalah rentetan JSON yang sah sebelum memuatkannya

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Cetak kandungan respons selepas memuatkannya sebagai JSON

pprint(json.loads(response_content))
```

Apa yang berikut adalah keluaran dari kod sebelumnya dan anda boleh menggunakan keluaran berstruktur ini untuk mengarahkan kepada `assigned_agent` dan merumuskan pelan perjalanan kepada pengguna akhir.

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

Contoh notebook dengan sampel kod di atas boleh didapati [di sini](07-autogen.ipynb).

### Perancangan Iteratif

Sesetengah tugasan memerlukan interaksi dua hala atau perancangan semula, di mana hasil satu subtugas mempengaruhi yang seterusnya. Sebagai contoh, jika ejen menemui format data yang tidak dijangka semasa menempah penerbangan, ia mungkin perlu menyesuaikan strateginya sebelum meneruskan kepada tempahan hotel.

Selain itu, maklum balas pengguna (contohnya seorang manusia memutuskan mereka lebih suka penerbangan yang lebih awal) boleh mencetuskan perancangan semula separa. Pendekatan dinamik dan iteratif ini memastikan penyelesaian akhir selari dengan kekangan dunia sebenar dan keutamaan pengguna yang berubah.

contoh kod

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. sama seperti kod sebelumnya dan teruskan sejarah pengguna, rancangan semasa
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
# .. rancang semula dan hantar tugas kepada ejen masing-masing
```

Untuk perancangan yang lebih menyeluruh, semak Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">catatan blog</a> untuk penyelesaian tugasan kompleks.

## Ringkasan

Dalam artikel ini kita telah melihat contoh bagaimana kita boleh mencipta perancang yang boleh memilih secara dinamik ejen yang tersedia yang ditakrifkan. Keluaran Perancang menguraikan tugasan dan menetapkan ejen supaya mereka boleh dilaksanakan. Diandaikan ejen mempunyai akses kepada fungsi/alat yang diperlukan untuk melaksanakan tugasan. Selain ejen, anda boleh memasukkan corak lain seperti refleksi, peringkas, dan sembang round-robin untuk terus menyesuaikan.

## Sumber Tambahan

AutoGen Magentic One - A Generalist multi-agent system for solving complex tasks and has achieved impressive results on multiple challenging agentic benchmarks. Reference: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Dalam pelaksanaan ini, orchestrator mencipta pelan khusus tugasan dan mendelegasikan tugasan-tugasan ini kepada ejen yang tersedia. Selain merancang, orchestrator juga menggunakan mekanisme penjejakan untuk memantau kemajuan tugasan dan merancang semula mengikut keperluan.

### Ada Lagi Soalan tentang Corak Reka Bentuk Perancangan?

Sertai [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) untuk berjumpa dengan pelajar lain, menghadiri waktu pejabat dan mendapatkan jawapan untuk soalan AI Agents anda.

## Pelajaran Sebelumnya

[Membina Ejen AI yang Boleh Dipercayai](../06-building-trustworthy-agents/README.md)

## Pelajaran Seterusnya

[Corak Reka Bentuk Multi-Ejen](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Penafian:
Dokumen ini telah diterjemahkan menggunakan perkhidmatan terjemahan AI Co-op Translator (https://github.com/Azure/co-op-translator). Walaupun kami berusaha untuk memastikan ketepatan, sila ambil perhatian bahawa terjemahan automatik mungkin mengandungi kesilapan atau ketidaktepatan. Dokumen asal dalam bahasa asalnya harus dianggap sebagai sumber rujukan yang sahih. Untuk maklumat yang kritikal, disarankan terjemahan profesional oleh penterjemah manusia. Kami tidak bertanggungjawab ke atas sebarang salah faham atau salah tafsiran yang timbul akibat penggunaan terjemahan ini.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->