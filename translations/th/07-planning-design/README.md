[![รูปแบบการออกแบบการวางแผน](../../../translated_images/th/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(คลิกที่รูปภาพด้านบนเพื่อดูวิดีโอของบทเรียนนี้)_

# การวางแผนการออกแบบ

## บทนำ

บทเรียนนี้จะครอบคลุม

* การกำหนดเป้าหมายโดยรวมที่ชัดเจนและการแบ่งงานที่ซับซ้อนออกเป็นงานย่อยที่จัดการได้
* การใช้ผลลัพธ์ที่มีโครงสร้างเพื่อให้ได้การตอบกลับที่น่าเชื่อถือและอ่านโดยเครื่องได้ง่ายขึ้น
* การประยุกต์ใช้แนวทางขับเคลื่อนด้วยเหตุการณ์เพื่อจัดการงานที่เปลี่ยนแปลงได้และข้อมูลนำเข้าที่ไม่คาดคิด

## เป้าหมายการเรียนรู้

หลังจากเรียนบทเรียนนี้เสร็จสิ้น คุณจะเข้าใจเกี่ยวกับ:

* ระบุและตั้งเป้าหมายโดยรวมสำหรับเอเจนต์ AI เพื่อให้แน่ใจว่าเอเจนต์รู้ชัดเจนว่าจะต้องบรรลุอะไร
* แยกงานที่ซับซ้อนออกเป็นงานย่อยที่จัดการได้และจัดระเบียบเป็นลำดับตรรกะ
* จัดเตรียมเอเจนต์ด้วยเครื่องมือที่เหมาะสม (เช่น เครื่องมือค้นหาหรือเครื่องมือวิเคราะห์ข้อมูล) ตัดสินใจว่าเมื่อใดและอย่างไรที่จะใช้ และจัดการสถานการณ์ที่ไม่คาดคิดที่เกิดขึ้น
* ประเมินผลลัพธ์ของงานย่อย วัดประสิทธิภาพ และทำซ้ำการกระทำเพื่อปรับปรุงผลลัพธ์สุดท้าย

## การกำหนดเป้าหมายโดยรวมและการแบ่งงาน

![การกำหนดเป้าหมายและงาน](../../../translated_images/th/defining-goals-tasks.d70439e19e37c47a.webp)

งานในโลกจริงส่วนใหญ่มีความซับซ้อนเกินกว่าที่จะจัดการได้ในขั้นตอนเดียว เอเจนต์ AI ต้องการวัตถุประสงค์ที่กระชับเพื่อเป็นแนวทางในการวางแผนและการกระทำ ตัวอย่างเช่น ให้พิจารณาเป้าหมายว่า:

    "สร้างแผนการเดินทาง 3 วัน"

แม้ว่าจะเป็นข้อความที่ง่าย แต่ก็ยังต้องมีการปรับแต่ง เป้าหมายที่ชัดเจนยิ่งขึ้นจะทำให้เอเจนต์ (และผู้ร่วมงานมนุษย์) สามารถมุ่งเน้นไปที่ผลลัพธ์ที่ถูกต้องได้ดีขึ้น เช่น การสร้างแผนการเดินทางที่ครบถ้วนพร้อมตัวเลือกเที่ยวบิน คำแนะนำโรงแรม และข้อเสนอแนะกิจกรรม

### การแยกงานเป็นส่วนย่อย

งานขนาดใหญ่หรือซับซ้อนจะสามารถจัดการได้ดีขึ้นเมื่อตัดเป็นงานย่อยที่มีเป้าหมายชัดเจน สำหรับตัวอย่างแผนการเดินทาง คุณสามารถแบ่งเป้าหมายออกเป็น:

* การจองเที่ยวบิน
* การจองโรงแรม
* การเช่ารถ
* การปรับแต่งตามบุคคล

งานย่อยแต่ละอย่างสามารถจัดการโดยเอเจนต์หรือกระบวนการเฉพาะทางได้ เอเจนต์หนึ่งอาจเชี่ยวชาญด้านการค้นหาข้อเสนอเที่ยวบินที่ดีที่สุด อีกตัวหนึ่งมุ่งเน้นการจองโรงแรม และอื่น ๆ เอเจนต์ที่ประสานงานหรือเอเจนต์ "downstream" สามารถรวบรวมผลลัพธ์เหล่านี้เป็นแผนการเดินทางที่ครบถ้วนสำหรับผู้ใช้ปลายทาง

แนวทางแบบโมดูลาร์นี้ยังอนุญาตให้ปรับปรุงแบบเพิ่มขั้นได้ ตัวอย่างเช่น คุณสามารถเพิ่มเอเจนต์เฉพาะทางสำหรับคำแนะนำด้านอาหารหรือข้อเสนอแนะกิจกรรมท้องถิ่นและปรับปรุงแผนการเดินทางเมื่อเวลาผ่านไป

### ผลลัพธ์แบบมีโครงสร้าง

โมเดลภาษาใหญ่ (LLMs) สามารถสร้างผลลัพธ์ที่มีโครงสร้าง (เช่น JSON) ซึ่งง่ายสำหรับเอเจนต์หรือบริการ downstream ในการแยกวิเคราะห์และประมวลผล สิ่งนี้มีประโยชน์อย่างยิ่งในบริบทของมัลติเอเจนต์ ที่ซึ่งเราสามารถดำเนินการตามงานเหล่านี้หลังจากได้รับผลลัพธ์การวางแผน ดูภาพรวมได้อย่างรวดเร็วจาก <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">บล็อกโพสต์</a> นี้

ตัวอย่าง Python ต่อไปนี้แสดงเอเจนต์วางแผนง่าย ๆ ที่แยกเป้าหมายออกเป็นงานย่อยและสร้างแผนที่มีโครงสร้าง:

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

# โมเดลงานย่อยการเดินทาง
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # เราต้องการมอบหมายงานให้กับตัวแทน

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # เพื่อยืนยันตัวตนกับโมเดล คุณจะต้องสร้างโทเค็นการเข้าถึงส่วนบุคคล (PAT) ในการตั้งค่า GitHub ของคุณ.
    # สร้างโทเค็น PAT ของคุณโดยทำตามคำแนะนำที่นี่: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# กำหนดข้อความของผู้ใช้
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

# # ตรวจสอบให้แน่ใจว่าเนื้อหาการตอบกลับเป็นสตริง JSON ที่ถูกต้องก่อนโหลดมัน
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("เนื้อหาการตอบกลับไม่ใช่สตริง JSON ที่ถูกต้อง")

# # พิมพ์เนื้อหาการตอบกลับหลังจากโหลดเป็น JSON
# pprint(json.loads(response_content))

# ตรวจสอบความถูกต้องของเนื้อหาการตอบกลับด้วยโมเดล MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### เอเจนต์วางแผนพร้อมการประสานงานแบบมัลติเอเจนต์

ในตัวอย่างนี้ เอเจนต์ Semantic Router จะได้รับคำขอจากผู้ใช้ (เช่น "ฉันต้องการแผนโรงแรมสำหรับการเดินทางของฉัน")

จากนั้นผู้วางแผนจะ:

* รับแผนโรงแรม: ผู้วางแผนรับข้อความของผู้ใช้และจากคำสั่งระบบ (รวมถึงรายละเอียดของเอเจนต์ที่มีอยู่) จะสร้างแผนการเดินทางที่มีโครงสร้าง
* ระบุเอเจนต์และเครื่องมือของพวกมัน: ทะเบียนเอเจนต์เก็บรายการเอเจนต์ (เช่น สำหรับเที่ยวบิน โรงแรม การเช่ารถ และกิจกรรม) พร้อมกับฟังก์ชันหรือเครื่องมือที่พวกเขาให้บริการ
* เส้นทางแผนไปยังเอเจนต์ที่เกี่ยวข้อง: ขึ้นอยู่กับจำนวนงานย่อย ผู้วางแผนอาจส่งข้อความไปยังเอเจนต์เฉพาะทางโดยตรง (สำหรับสถานการณ์งานเดียว) หรือประสานงานผ่านผู้จัดการแชทกลุ่มสำหรับการทำงานร่วมกันแบบมัลติเอเจนต์
* สรุปผลลัพธ์: สุดท้าย ผู้วางแผนสรุปแผนที่สร้างเพื่อความชัดเจน
ตัวอย่างโค้ด Python ต่อไปนี้แสดงขั้นตอนเหล่านี้:

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

# โมเดลงานย่อยการเดินทาง

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # เราต้องการมอบหมายงานให้เอเจนต์

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# สร้างไคลเอนต์โดยใช้ตัวแปรแวดล้อมที่ตรวจสอบประเภทแล้ว

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# กำหนดข้อความของผู้ใช้

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

# ตรวจให้แน่ใจว่าเนื้อหาการตอบกลับเป็นสตริง JSON ที่ถูกต้องก่อนที่จะโหลด

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# พิมพ์เนื้อหาการตอบกลับหลังจากโหลดเป็น JSON แล้ว

pprint(json.loads(response_content))
```

ต่อไปนี้เป็นผลลัพธ์จากโค้ดก่อนหน้าและคุณสามารถใช้ผลลัพธ์ที่มีโครงสร้างนี้เพื่อนำทางไปยัง `assigned_agent` และสรุปแผนการเดินทางให้กับผู้ใช้ปลายทางได้

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

ตัวอย่างโน้ตบุ๊กที่มีตัวอย่างโค้ดก่อนหน้าพบได้ [ที่นี่](07-autogen.ipynb).

### การวางแผนแบบทำซ้ำ

บางงานต้องการการถกเถียงหรือการวางแผนใหม่ ซึ่งผลลัพธ์ของงานย่อยหนึ่งจะส่งผลต่อถัดไป ตัวอย่างเช่น หากเอเจนต์ค้นพบรูปแบบข้อมูลที่ไม่คาดคิดขณะจองเที่ยวบิน มันอาจต้องปรับกลยุทธ์ก่อนจะไปยังการจองโรงแรม

นอกจากนี้ คำติชมจากผู้ใช้ (เช่น ผู้ใช้ตัดสินใจว่าพวกเขาต้องการเที่ยวบินที่เร็วขึ้น) อาจกระตุ้นการวางแผนบางส่วนแบบใหม่ได้ แนวทางที่มีพลวัตและทำซ้ำนี้ช่วยให้แนวทางสุดท้ายสอดคล้องกับข้อจำกัดในโลกจริงและความชอบของผู้ใช้ที่เปลี่ยนแปลงไป

เช่น ตัวอย่างโค้ด

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. เหมือนกับโค้ดก่อนหน้าและส่งต่อประวัติผู้ใช้และแผนปัจจุบัน
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
# .. วางแผนใหม่และส่งงานไปยังตัวแทนที่เกี่ยวข้อง
```

สำหรับการวางแผนที่ครอบคลุมยิ่งขึ้น โปรดดู Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">บทความบล็อก</a> สำหรับการแก้ไขปัญหาที่ซับซ้อน

## สรุป

ในบทความนี้เราได้ดูตัวอย่างของการสร้างผู้วางแผนที่สามารถเลือกเอเจนต์ที่มีอยู่ได้อย่างไดนามิก ผลลัพธ์จากผู้วางแผนจะแยกงานออกเป็นส่วนย่อยและมอบหมายเอเจนต์เพื่อให้สามารถดำเนินการได้ โดยสมมติว่าเอเจนต์มีการเข้าถึงฟังก์ชัน/เครื่องมือที่จำเป็นในการปฏิบัติงาน นอกเหนือจากเอเจนต์แล้ว คุณยังสามารถรวมรูปแบบอื่น ๆ เช่น การสะท้อนความคิด (reflection), ตัวสรุป (summarizer) และการแชทแบบวนรอบ (round robin chat) เพื่อปรับแต่งเพิ่มเติม

## แหล่งข้อมูลเพิ่มเติม

AutoGen Magentic One - ระบบมัลติเอเจนต์แบบทั่วไปสำหรับแก้ปัญหางานที่ซับซ้อนและได้ผลลัพธ์ที่น่าประทับใจในแหล่งทดสอบหลายรายการ อ้างอิง: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. ในการใช้งานนี้ ตัวประสานงานจะสร้างแผนที่เฉพาะงานและมอบหมายงานเหล่านี้ให้กับเอเจนต์ที่มีอยู่ นอกเหนือจากการวางแผนแล้ว ตัวประสานงานยังนำกลไกการติดตามมาใช้เพื่อตรวจสอบความคืบหน้าของงานและวางแผนใหม่ตามที่จำเป็น

### มีคำถามเพิ่มเติมเกี่ยวกับรูปแบบการออกแบบการวางแผนไหม?

เข้าร่วม [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) เพื่อพบปะผู้เรียนคนอื่น ๆ เข้าร่วมชั่วโมงตอบคำถามและรับคำตอบสำหรับคำถามเกี่ยวกับ AI Agents ของคุณ

## บทเรียนก่อนหน้า

[การสร้างเอเยนต์ AI ที่น่าเชื่อถือ](../06-building-trustworthy-agents/README.md)

## บทเรียนถัดไป

[รูปแบบการออกแบบมัลติเอเจนต์](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
ข้อจำกัดความรับผิด:
เอกสารฉบับนี้ถูกแปลโดยใช้บริการแปลด้วยปัญญาประดิษฐ์ Co-op Translator (https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้การแปลมีความถูกต้อง โปรดทราบว่าการแปลโดยอัตโนมัติอาจมีข้อผิดพลาดหรือความคลาดเคลื่อน เอกสารต้นฉบับในภาษาต้นทางควรถูกยึดถือเป็นแหล่งข้อมูลหลัก สำหรับข้อมูลที่สำคัญ แนะนำให้ใช้บริการแปลโดยนักแปลมืออาชีพ เราจะไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่คลาดเคลื่อนอันเกิดจากการใช้การแปลฉบับนี้
<!-- CO-OP TRANSLATOR DISCLAIMER END -->