# สำรวจ Microsoft Agent Framework

![เฟรมเวิร์กของเอเจนต์](../../../translated_images/th/lesson-14-thumbnail.90df0065b9d234ee.webp)

### บทนำ

บทเรียนนี้จะครอบคลุม:

- การทำความเข้าใจ Microsoft Agent Framework: คุณสมบัติหลักและคุณค่า  
- สำรวจแนวคิดหลักของ Microsoft Agent Framework
- เปรียบเทียบ MAF กับ Semantic Kernel และ AutoGen: คู่มือการย้ายข้อมูล

## เป้าหมายการเรียนรู้

หลังจากทำบทเรียนนี้เสร็จ คุณจะสามารถ:

- สร้างเอเจนต์ AI ที่พร้อมใช้งานในผลิตภัณฑ์โดยใช้ Microsoft Agent Framework
- นำคุณสมบัติหลักของ Microsoft Agent Framework ไปใช้กับกรณีการใช้งานเชิงตัวแทน (agentic)
- ย้ายและรวมเฟรมเวิร์กและเครื่องมือเชิงตัวแทนที่มีอยู่  

## Code Samples 

ตัวอย่างโค้ดสำหรับ [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) สามารถพบได้ในรีโพซิทอรีนี้ภายใต้ไฟล์ `xx-python-agent-framework` และ `xx-dotnet-agent-framework`

## ทำความเข้าใจกับ Microsoft Agent Framework

![แนะนำเฟรมเวิร์ก](../../../translated_images/th/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) สร้างขึ้นบนประสบการณ์และบทเรียนจาก Semantic Kernel และ AutoGen โดยเสนอความยืดหยุ่นเพื่อจัดการกับหลากหลายกรณีการใช้งานเชิงตัวแทนที่พบได้ทั้งในการผลิตและงานวิจัย รวมถึง:

- **การออร์เคสตราแบบลำดับขั้น** ในสถานการณ์ที่ต้องการเวิร์กโฟลว์เป็นขั้นตอน
- **การออร์เคสตราแบบพร้อมกัน** ในสถานการณ์ที่เอเจนต์ต้องทำงานให้เสร็จพร้อมกัน
- **การออร์เคสตราในกลุ่มแชท** ในสถานการณ์ที่เอเจนต์สามารถทำงานร่วมกันบนงานเดียวกัน
- **การออร์เคสตราแบบส่งต่อ** ในสถานการณ์ที่เอเจนต์ส่งต่อหน้าที่ให้กันเมื่อซับทาสก์เสร็จสิ้น
- **การออร์เคสตราแบบแม่เหล็ก** ในสถานการณ์ที่เอเจนต์ผู้จัดการสร้างและแก้ไขรายการงานและจัดการการประสานงานของซับเอเจนต์เพื่อให้งานเสร็จสิ้น

เพื่อส่งมอบเอเจนต์ AI ในการใช้งานจริง MAF ยังรวมคุณสมบัติสำหรับ:

- **การสังเกตการณ์ (Observability)** ผ่านการใช้ OpenTelemetry ซึ่งทุกการกระทำของเอเจนต์ AI รวมถึงการเรียกใช้เครื่องมือ ขั้นตอนการออร์เคสตรา ลำดับเหตุผล และการตรวจวัดประสิทธิภาพผ่านแดชบอร์ดของ Microsoft Foundry
- **ความปลอดภัย** โดยการโฮสต์เอเจนต์แบบเนทีฟบน Microsoft Foundry ซึ่งรวมการควบคุมด้านความปลอดภัยเช่นการเข้าถึงตามบทบาท การจัดการข้อมูลส่วนตัว และการป้องกันเนื้อหาในตัว
- **ความทนทาน** เนื่องจากเธรดและเวิร์กโฟลว์ของเอเจนต์สามารถหยุดชั่วคราว ดำเนินต่อ และกู้คืนจากข้อผิดพลาดได้ ซึ่งเอื้อต่อกระบวนการที่ทำงานนานขึ้น
- **การควบคุม** เนื่องจากเวิร์กโฟลว์ที่มีมนุษย์อยู่ในลูปได้รับการสนับสนุนซึ่งงานจะถูกทำเครื่องหมายว่าเป็นงานที่ต้องได้รับการอนุมัติจากมนุษย์

Microsoft Agent Framework ยังมุ่งเน้นการทำงานร่วมกันได้โดย:

- **ไม่ขึ้นกับคลาวด์** - เอเจนต์สามารถรันในคอนเทนเนอร์ บน on-prem และข้ามหลายคลาวด์ต่าง ๆ
- **ไม่ขึ้นกับผู้ให้บริการ** - เอเจนต์สามารถสร้างผ่าน SDK ที่คุณชอบรวมถึง Azure OpenAI และ OpenAI
- **การรวมมาตรฐานเปิด** - เอเจนต์สามารถใช้โปรโตคอลเช่น Agent-to-Agent(A2A) และ Model Context Protocol (MCP) เพื่อค้นหาและใช้เอเจนต์และเครื่องมืออื่น ๆ
- **ปลั๊กอินและคอนเน็กเตอร์** - สามารถเชื่อมต่อกับบริการข้อมูลและหน่วยความจำเช่น Microsoft Fabric, SharePoint, Pinecone และ Qdrant

มาดูกันว่าแต่ละคุณสมบัติเหล่านี้ถูกนำไปใช้กับแนวคิดหลักของ Microsoft Agent Framework อย่างไร

## แนวคิดหลักของ Microsoft Agent Framework

### เอเจนต์

![เฟรมเวิร์กของเอเจนต์](../../../translated_images/th/agent-components.410a06daf87b4fef.webp)

**การสร้างเอเจนต์**

การสร้างเอเจนต์ทำโดยการกำหนดบริการอนุมาน (LLM Provider), ชุดคำสั่งสำหรับเอเจนต์ AI ให้ปฏิบัติตาม และการกำหนด `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

ข้างต้นใช้ `Azure OpenAI` แต่เอเจนต์สามารถสร้างโดยใช้บริการหลากหลายรวมถึง `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses` และ `ChatCompletion` API

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

หรือเอเจนต์ระยะไกลโดยใช้โปรโตคอล A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**การรันเอเจนต์**

เอเจนต์ถูกรันโดยใช้เมธอด `.run` หรือ `.run_stream` สำหรับการตอบแบบไม่สตรีมหรือแบบสตรีมตามลำดับ

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

แต่ละครั้งที่รันเอเจนต์ยังสามารถมีตัวเลือกเพื่อปรับแต่งพารามิเตอร์เช่น `max_tokens` ที่เอเจนต์ใช้, `tools` ที่เอเจนต์สามารถเรียกใช้ และแม้แต่ `model` ที่เอเจนต์ใช้เอง

สิ่งนี้มีประโยชน์ในกรณีที่ต้องการโมเดลหรือเครื่องมือเฉพาะในการทำงานให้เสร็จตามคำขอของผู้ใช้

**เครื่องมือ**

เครื่องมือสามารถกำหนดได้ทั้งเมื่อกำหนดเอเจนต์:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# เมื่อต้องสร้าง ChatAgent โดยตรง

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

และยังสามารถกำหนดได้เมื่อรันเอเจนต์:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # เครื่องมือนี้จัดเตรียมไว้สำหรับการรันครั้งนี้เท่านั้น )
```

**เธรดของเอเจนต์**

เธรดของเอเจนต์ถูกใช้เพื่อจัดการการสนทนาหลายตา (multi-turn) เธรดสามารถสร้างได้โดย:

- การใช้ `get_new_thread()` ซึ่งทำให้เธรดสามารถบันทึกไว้ใช้ในภายหลัง
- การสร้างเธรดอัตโนมัติเมื่อรันเอเจนต์และให้เธรดมีอายุเพียงระหว่างการรันปัจจุบัน

เพื่อสร้างเธรด โค้ดจะมีลักษณะดังนี้:

```python
# สร้างเธรดใหม่.
thread = agent.get_new_thread() # รันเอเจนต์ด้วยเธรดนั้น.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

จากนั้นคุณสามารถซีเรียลไลซ์เธรดเพื่อเก็บไว้ใช้งานในภายหลังได้:

```python
# สร้างเธรดใหม่.
thread = agent.get_new_thread() 

# เรียกใช้งานเอเจนต์ด้วยเธรด.

response = await agent.run("Hello, how are you?", thread=thread) 

# ซีเรียไลซ์เธรดเพื่อจัดเก็บ.

serialized_thread = await thread.serialize() 

# ดีซีเรียไลซ์สถานะของเธรดหลังจากโหลดจากที่จัดเก็บ.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**มิดเดิลแวร์ของเอเจนต์**

เอเจนต์โต้ตอบกับเครื่องมือและ LLM เพื่อทำงานให้ผู้ใช้สำเร็จ ในบางสถานการณ์ เราอาจต้องการดำเนินการหรือติดตามระหว่างการโต้ตอบเหล่านี้ มิดเดิลแวร์ของเอเจนต์ทำให้เราทำเช่นนี้ได้ผ่าน:

*Function Middleware*

มิดเดิลแวร์นี้ช่วยให้เราดำเนินการระหว่างเอเจนต์กับฟังก์ชัน/เครื่องมือที่มันจะเรียกใช้ ตัวอย่างการใช้งานคือเมื่อต้องการบันทึกการเรียกฟังก์ชัน

ในโค้ดด้านล่าง `next` กำหนดว่าควรเรียกมิดเดิลแวร์ถัดไปหรือฟังก์ชันจริง

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # การประมวลผลล่วงหน้า: บันทึกก่อนการเรียกใช้ฟังก์ชัน
    print(f"[Function] Calling {context.function.name}")

    # ดำเนินการต่อไปยังมิดเดิลแวร์ถัดไปหรือการเรียกใช้ฟังก์ชัน
    await next(context)

    # การประมวลผลภายหลัง: บันทึกหลังการเรียกใช้ฟังก์ชัน
    print(f"[Function] {context.function.name} completed")
```

*Chat Middleware*

มิดเดิลแวร์นี้ช่วยให้เราดำเนินการหรือบันทึกการกระทำระหว่างเอเจนต์กับคำขอที่ส่งไปยัง LLM

สิ่งนี้มีข้อมูลสำคัญเช่น `messages` ที่กำลังถูกส่งไปยังบริการ AI

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # การประมวลผลก่อน: บันทึกก่อนเรียกใช้งาน AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # ดำเนินการต่อไปยังมิดเดิลแวร์หรือบริการ AI ถัดไป
    await next(context)

    # การประมวลผลหลัง: บันทึกหลังการตอบกลับของ AI
    print("[Chat] AI response received")

```

**หน่วยความจำของเอเจนต์**

ตามที่กล่าวไว้ในบทเรียน `Agentic Memory` หน่วยความจำเป็นองค์ประกอบสำคัญที่ช่วยให้เอเจนต์ทำงานได้ในบริบทต่าง ๆ MAF มีหน่วยความจำหลายประเภทให้เลือก:

*In-Memory Storage*

หน่วยความจำนี้ถูกเก็บในเธรดระหว่างเวลาทำงานของแอปพลิเคชัน

```python
# สร้างเธรดใหม่.
thread = agent.get_new_thread() # รันตัวแทนโดยใช้เธรด.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Persistent Messages*

หน่วยความจำนี้ใช้เมื่อเก็บประวัติการสนทนาข้ามเซสชันต่าง ๆ ถูกกำหนดโดยใช้ `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# สร้างที่เก็บข้อความแบบกำหนดเอง
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamic Memory*

หน่วยความจำนี้จะถูกเพิ่มเข้าไปในบริบทก่อนที่เอเจนต์จะถูกรัน หน่วยความจำเหล่านี้สามารถเก็บไว้ในบริการภายนอกเช่น mem0:

```python
from agent_framework.mem0 import Mem0Provider

# ใช้ Mem0 เพื่อความสามารถด้านหน่วยความจำขั้นสูง
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

**การสังเกตการณ์ของเอเจนต์**

การสังเกตการณ์เป็นสิ่งสำคัญต่อการสร้างระบบเชิงตัวแทนที่น่าเชื่อถือและดูแลรักษาได้ MAF ผสานรวมกับ OpenTelemetry เพื่อให้การติดตาม (tracing) และมาตรวัดสำหรับการสังเกตการณ์ที่ดียิ่งขึ้น

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # ทำบางอย่าง
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### เวิร์กโฟลว์

MAF เสนอเวิร์กโฟลว์ที่เป็นขั้นตอนที่กำหนดไว้ล่วงหน้าเพื่อทำงานให้เสร็จและรวมเอเจนต์ AI เป็นส่วนประกอบในแต่ละขั้นตอน

เวิร์กโฟลว์ประกอบด้วยส่วนประกอบต่าง ๆ ที่ช่วยให้การควบคุมการไหลดีขึ้น เวิร์กโฟลว์ยังรองรับ **การออร์เคสตราแบบหลายเอเจนต์** และ **การเช็คพอยต์** เพื่อบันทึกสถานะของเวิร์กโฟลว์

ส่วนประกอบหลักของเวิร์กโฟลว์ได้แก่:

**ตัวดำเนินการ (Executors)**

ตัวดำเนินการรับข้อความนำเข้า ดำเนินงานตามที่ได้รับมอบหมาย แล้วสร้างข้อความเอาต์พุต ซึ่งช่วยให้เวิร์กโฟลว์ขยับไปข้างหน้าเพื่อนำไปสู่การทำงานที่ใหญ่ขึ้นให้เสร็จ ตัวดำเนินการสามารถเป็นเอเจนต์ AI หรือโลจิกที่กำหนดเอง

**ขอบเชื่อม (Edges)**

ขอบเชื่อมใช้เพื่อกำหนดการไหลของข้อความในเวิร์กโฟลว์ ซึ่งสามารถเป็นได้ดังนี้:

*ขอบเชื่อมแบบตรง (Direct Edges)* - การเชื่อมต่อตรงแบบหนึ่งต่อหนึ่งระหว่างตัวดำเนินการ:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*ขอบเชื่อมแบบมีเงื่อนไข (Conditional Edges)* - ทำงานเมื่อเงื่อนไขบางอย่างเป็นจริง ตัวอย่างเช่น เมื่อห้องพักโรงแรมไม่พร้อมใช้งาน ตัวดำเนินการอาจแนะนำตัวเลือกอื่น

*ขอบเชื่อมแบบสวิตช์-เคส (Switch-case Edges)* - นำข้อความไปยังตัวดำเนินการต่าง ๆ ตามเงื่อนไขที่กำหนด ตัวอย่างเช่น หากลูกค้าการเดินทางมีสิทธิ์เข้าถึงแบบพิเศษ งานของพวกเขาอาจถูกจัดการผ่านเวิร์กโฟลว์อื่น

*ขอบเชื่อมแบบกระจาย (Fan-out Edges)* - ส่งข้อความเดียวไปยังหลายเป้าหมาย

*ขอบเชื่อมแบบรวม (Fan-in Edges)* - รวบรวมข้อความหลายฉบับจากตัวดำเนินการต่าง ๆ แล้วส่งไปยังเป้าหมายหนึ่ง

**เหตุการณ์**

เพื่อให้การสังเกตการณ์เวิร์กโฟลว์ดียิ่งขึ้น MAF มีเหตุการณ์ในตัวสำหรับการดำเนินการรวมถึง:

- `WorkflowStartedEvent`  - การเริ่มต้นการดำเนินงานของเวิร์กโฟลว์
- `WorkflowOutputEvent` - เวิร์กโฟลว์สร้างเอาต์พุต
- `WorkflowErrorEvent` - เวิร์กโฟลว์พบข้อผิดพลาด
- `ExecutorInvokeEvent`  - ตัวดำเนินการเริ่มประมวลผล
- `ExecutorCompleteEvent`  -  ตัวดำเนินการเสร็จสิ้นการประมวลผล
- `RequestInfoEvent` - มีการออกคำขอ

## การย้ายจากเฟรมเวิร์กอื่น (Semantic Kernel และ AutoGen)

### ความแตกต่างระหว่าง MAF และ Semantic Kernel

**การสร้างเอเจนต์ที่เรียบง่ายขึ้น**

Semantic Kernel พึ่งพาการสร้างอินสแตนซ์ Kernel สำหรับแต่ละเอเจนต์ MAF ใช้วิธีที่เรียบง่ายขึ้นโดยใช้เอ็กซ์เทนชันสำหรับผู้ให้บริการหลัก

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**การสร้างเธรดของเอเจนต์**

Semantic Kernel ต้องให้สร้างเธรดด้วยตนเอง ใน MAF เอเจนต์จะถูกกำหนดเธรดโดยตรง

```python
thread = agent.get_new_thread() # รันเอเจนต์ด้วยเธรด
```

**การลงทะเบียนเครื่องมือ**

ใน Semantic Kernel เครื่องมือถูกลงทะเบียนกับ Kernel และ Kernel จะถูกส่งต่อไปยังเอเจนต์ ใน MAF เครื่องมือถูกลงทะเบียนโดยตรงในระหว่างกระบวนการสร้างเอเจนต์

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### ความแตกต่างระหว่าง MAF และ AutoGen

**Teams เทียบกับ Workflows**

`Teams` เป็นโครงสร้างเหตุการณ์สำหรับกิจกรรมขับเคลื่อนด้วยเหตุการณ์กับเอเจนต์ใน AutoGen ในขณะที่ MAF ใช้ `Workflows` ที่ส่งข้อมูลไปยังตัวดำเนินการผ่านสถาปัตยกรรมแบบกราฟ

**การสร้างเครื่องมือ**

AutoGen ใช้ `FunctionTool` เพื่อห่อหุ้มฟังก์ชันให้เอเจนต์เรียกใช้ MAF ใช้ @ai_function ซึ่งทำงานในลักษณะที่คล้ายกันแต่ยังสรุปสคีม่าโดยอัตโนมัติสำหรับแต่ละฟังก์ชัน

**พฤติกรรมของเอเจนต์**

เอเจนต์เป็นแบบรอบเดียวตามค่าเริ่มต้นใน AutoGen เว้นแต่จะตั้งค่า `max_tool_iterations` ให้สูงขึ้น ใน MAF `ChatAgent` เป็นแบบหลายรอบตามค่าเริ่มต้น หมายความว่าจะเรียกใช้เครื่องมือต่อเนื่องจนกว่างานของผู้ใช้จะเสร็จ

## Code Samples 

ตัวอย่างโค้ดสำหรับ Microsoft Agent Framework สามารถพบได้ในรีโพซิทอรีนี้ภายใต้ไฟล์ `xx-python-agent-framework` และ `xx-dotnet-agent-framework`

## มีคำถามเพิ่มเติมเกี่ยวกับ Microsoft Agent Framework หรือไม่?

เข้าร่วม [Discord ของ Microsoft Foundry](https://aka.ms/ai-agents/discord) เพื่อพบปะผู้เรียนคนอื่น ๆ เข้าร่วมชั่วโมงตอบคำถามและขอคำแนะนำเกี่ยวกับเอเจนต์ AI ของคุณ

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
ข้อจำกัดความรับผิดชอบ:
เอกสารฉบับนี้ถูกแปลโดยใช้บริการแปลด้วยปัญญาประดิษฐ์ [Co-op Translator](https://github.com/Azure/co-op-translator) แม้เราจะมุ่งมั่นเพื่อความถูกต้อง โปรดทราบว่าการแปลอัตโนมัติอาจมีข้อผิดพลาดหรือความคลาดเคลื่อนได้ เอกสารต้นฉบับในภาษาต้นฉบับควรถือเป็นแหล่งข้อมูลที่เป็นหลัก สำหรับข้อมูลที่สำคัญหรือมีผลกระทบสูง ขอแนะนำให้ใช้การแปลโดยนักแปลมืออาชีพ เราจะไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดใด ๆ ที่เกิดจากการใช้การแปลฉบับนี้
<!-- CO-OP TRANSLATOR DISCLAIMER END -->