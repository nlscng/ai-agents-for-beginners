[![เอเจนต์ AI ที่น่าเชื่อถือ](../../../translated_images/th/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(คลิกที่รูปด้านบนเพื่อดูวิดีโอของบทเรียนนี้)_

# การสร้างเอเจนต์ AI ที่น่าเชื่อถือ

## บทนำ

บทเรียนนี้จะครอบคลุม:

- วิธีการสร้างและปรับใช้เอเจนต์ AI ที่ปลอดภัยและมีประสิทธิภาพ
- ข้อควรพิจารณาด้านความปลอดภัยที่สำคัญเมื่อพัฒนาเอเจนต์ AI
- วิธีการรักษาข้อมูลและความเป็นส่วนตัวของผู้ใช้เมื่อพัฒนาเอเจนต์ AI

## เป้าหมายการเรียนรู้

หลังจากเรียนจบบทเรียนนี้ คุณจะทราบวิธี:

- ระบุและลดความเสี่ยงเมื่อสร้างเอเจนต์ AI
- นำมาตรการด้านความปลอดภัยไปใช้เพื่อให้แน่ใจว่าการจัดการข้อมูลและการเข้าถึงเป็นไปอย่างเหมาะสม
- สร้างเอเจนต์ AI ที่รักษาความเป็นส่วนตัวของข้อมูลและมอบประสบการณ์ผู้ใช้ที่มีคุณภาพ

## ความปลอดภัย

ก่อนอื่นมาดูการสร้างแอปพลิเคชันแบบตัวแทนที่ปลอดภัยกันก่อน ความปลอดภัยหมายถึงว่าเอเจนต์ AI ทำงานตามที่ออกแบบไว้ ในฐานะผู้พัฒนาแอปพลิเคชันเชิงเอเจนต์ เรามีวิธีการและเครื่องมือเพื่อเพิ่มความปลอดภัยให้มากที่สุด:

### การสร้างกรอบข้อความระบบ

หากคุณเคยสร้างแอปพลิเคชัน AI โดยใช้โมเดลภาษาขนาดใหญ่ (LLMs) คุณจะรู้ว่าการออกแบบพรอมต์ระบบหรือข้อความระบบที่แข็งแกร่งนั้นสำคัญเพียงใด ข้อความเหล่านี้กำหนดกฎเมตา คำสั่ง และแนวทางสำหรับวิธีที่ LLM จะโต้ตอบกับผู้ใช้และข้อมูล

สำหรับเอเจนต์ AI พรอมต์ระบบมีความสำคัญยิ่งขึ้นเพราะเอเจนต์จะต้องการคำสั่งที่เฉพาะเจาะจงสูงเพื่อทำงานที่เรากำหนดให้แล้วเสร็จ

เพื่อสร้างพรอมต์ระบบที่สามารถขยายขนาดได้ เราสามารถใช้กรอบข้อความระบบเพื่อสร้างเอเจนต์หนึ่งตัวหรือหลายตัวในแอปพลิเคชันของเราได้:

![การสร้างกรอบข้อความระบบ](../../../translated_images/th/system-message-framework.3a97368c92d11d68.webp)

#### ขั้นตอนที่ 1: สร้างข้อความระบบเมตา 

พรอมต์เมตาจะถูกใช้โดย LLM เพื่อสร้างพรอมต์ระบบสำหรับเอเจนต์ที่เราสร้าง เราออกแบบมันเป็นเทมเพลตเพื่อให้สามารถสร้างเอเจนต์หลายตัวได้อย่างมีประสิทธิภาพหากจำเป็น

นี่คือตัวอย่างของข้อความระบบเมตาที่เราจะให้กับ LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### ขั้นตอนที่ 2: สร้างพรอมต์พื้นฐาน

ขั้นตอนต่อไปคือการสร้างพรอมต์พื้นฐานเพื่ออธิบายเอเจนต์ AI คุณควรรวมบทบาทของเอเจนต์ งานที่เอเจนต์จะทำให้เสร็จ และความรับผิดชอบอื่น ๆ ของเอเจนต์

นี่คือตัวอย่าง:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### ขั้นตอนที่ 3: ส่งข้อความระบบพื้นฐานให้ LLM

ตอนนี้เราสามารถปรับแต่งข้อความระบบนี้ได้โดยการให้ข้อความระบบเมตาเป็นข้อความระบบและรวมกับข้อความระบบพื้นฐานของเรา

วิธีนี้จะสร้างข้อความระบบที่ออกแบบมาให้ดียิ่งขึ้นสำหรับการชี้นำเอเจนต์ AI ของเรา:

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

#### ขั้นตอนที่ 4: ทำซ้ำและปรับปรุง

คุณค่าของกรอบข้อความระบบนี้คือความสามารถในการขยายการสร้างข้อความระบบจากหลายเอเจนต์ได้ง่ายขึ้น รวมทั้งปรับปรุงข้อความระบบของคุณเมื่อเวลาผ่านไป แทบจะไม่เคยมีข้อความระบบที่ทำงานได้สมบูรณ์ตั้งแต่ครั้งแรกสำหรับกรณีการใช้งานทั้งหมด การสามารถปรับแต่งเล็กน้อยและปรับปรุงโดยการเปลี่ยนข้อความระบบพื้นฐานแล้วรันผ่านกรอบระบบจะช่วยให้คุณเปรียบเทียบและประเมินผลลัพธ์ได้

## การทำความเข้าใจภัยคุกคาม

เพื่อสร้างเอเจนต์ AI ที่น่าเชื่อถือ จำเป็นต้องเข้าใจและลดความเสี่ยงและภัยคุกคามต่อเอเจนต์ของคุณ มาดูบางประเภทของภัยคุกคามต่อเอเจนต์ AI และวิธีการวางแผนเตรียมรับมือกับพวกมันกัน

![การทำความเข้าใจภัยคุกคาม](../../../translated_images/th/understanding-threats.89edeada8a97fc0f.webp)

### งานและคำสั่ง

**คำอธิบาย:** ผู้โจมตีพยายามเปลี่ยนคำสั่งหรือเป้าหมายของเอเจนต์ AI ผ่านการพรอมต์หรือการจัดการอินพุต

**การลดความเสี่ยง:** ดำเนินการตรวจสอบการยืนยันและตัวกรองอินพุตเพื่อค้นหาพรอมต์ที่อาจเป็นอันตรายก่อนที่จะถูกประมวลผลโดยเอเจนต์ AI เนื่องจากการโจมตีประเภทนี้มักต้องการการโต้ตอบบ่อยครั้งกับเอเจนต์ การจำกัดจำนวนรอบในการสนทนาก็เป็นอีกวิธีหนึ่งที่จะป้องกันการโจมตีประเภทนี้

### การเข้าถึงระบบสำคัญ

**คำอธิบาย:** หากเอเจนต์ AI มีการเข้าถึงระบบและบริการที่เก็บข้อมูลที่ละเอียดอ่อน ผู้โจมตีอาจเจาะช่องทางการสื่อสารระหว่างเอเจนต์กับบริการเหล่านี้ ซึ่งสามารถเป็นการโจมตีโดยตรงหรือความพยายามโดยอ้อมเพื่อให้ได้ข้อมูลเกี่ยวกับระบบเหล่านี้ผ่านเอเจนต์

**การลดความเสี่ยง:** เอเจนต์ AI ควรมีสิทธิ์เข้าถึงระบบแบบจำเป็นเท่านั้นเพื่อลดการโจมตีประเภทนี้ การสื่อสารระหว่างเอเจนต์กับระบบควรปลอดภัย การนำการพิสูจน์ตัวตนและการควบคุมการเข้าถึงไปใช้อีกทางหนึ่งจะช่วยปกป้องข้อมูลนี้ได้

### การโอเวอร์โหลดทรัพยากรและบริการ

**คำอธิบาย:** เอเจนต์ AI สามารถเข้าถึงเครื่องมือและบริการต่าง ๆ เพื่อทำงานให้เสร็จ ผู้โจมตีอาจใช้ความสามารถนี้โจมตีบริการเหล่านี้โดยส่งคำขอจำนวนมากผ่านเอเจนต์ AI ซึ่งอาจทำให้ระบบล้มเหลวหรือเกิดค่าใช้จ่ายสูง

**การลดความเสี่ยง:** นำนโยบายจำกัดจำนวนคำขอที่เอเจนต์ AI สามารถส่งไปยังบริการต่าง ๆ การจำกัดจำนวนรอบสนทนาและคำขอต่อเอเจนต์ AI ของคุณเป็นอีกวิธีหนึ่งในการป้องกันการโจมตีประเภทนี้

### การปนเปื้อนฐานความรู้

**คำอธิบาย:** การโจมตีประเภทนี้ไม่ได้มุ่งเป้าไปที่เอเจนต์ AI โดยตรง แต่เป็นการโจมตีฐานความรู้และบริการอื่น ๆ ที่เอเจนต์ AI จะใช้ ซึ่งอาจรวมถึงการทำให้ข้อมูลที่เอเจนต์จะใช้ในการทำงานเสียหาย นำไปสู่การตอบกลับที่มีอคติหรือไม่เป็นไปตามที่คาดหวัง

**การลดความเสี่ยง:** ทำการตรวจสอบความถูกต้องของข้อมูลที่เอเจนต์ AI จะใช้ในเวิร์กโฟลว์อย่างสม่ำเสมอ ตรวจสอบให้แน่ใจว่าการเข้าถึงข้อมูลนี้ปลอดภัยและมีการเปลี่ยนแปลงโดยบุคคลที่เชื่อถือได้เท่านั้น เพื่อหลีกเลี่ยงการโจมตีประเภทนี้

### ข้อผิดพลาดที่ลุกลาม

**คำอธิบาย:** เอเจนต์ AI เข้าถึงเครื่องมือและบริการต่าง ๆ เพื่อทำงาน ข้อผิดพลาดที่เกิดจากผู้โจมตีอาจนำไปสู่ความล้มเหลวของระบบอื่น ๆ ที่เอเจนต์เชื่อมต่ออยู่ ทำให้การโจมตีแพร่หลายมากขึ้นและยากต่อการแก้ไขปัญหา

**การลดความเสี่ยง:** หนึ่งในวิธีป้องกันคือให้เอเจนต์ AI ทำงานในสภาพแวดล้อมที่จำกัด เช่น การทำงานภายใน Docker container เพื่อป้องกันการโจมตีระบบโดยตรง การสร้างกลไกสำรองและตรรกะการลองใหม่เมื่อระบบบางส่วนตอบกลับด้วยข้อผิดพลาดเป็นอีกวิธีหนึ่งที่จะป้องกันความล้มเหลวของระบบในวงกว้าง

## มนุษย์ในวงจร

อีกวิธีที่มีประสิทธิภาพในการสร้างระบบเอเจนต์ AI ที่น่าเชื่อถือคือการใช้แนวทางมนุษย์ในวงจร (Human-in-the-loop) วิธีนี้สร้างกระบวนการที่ให้ผู้ใช้สามารถให้ข้อเสนอแนะแก่เอเจนต์ระหว่างการทำงาน ผู้ใช้โดยพื้นฐานจะทำหน้าที่เป็นเอเจนต์ในระบบหลายเอเจนต์ โดยให้การอนุมัติหรือยุติกระบวนการที่กำลังรันอยู่

![มนุษย์ในวงจร](../../../translated_images/th/human-in-the-loop.5f0068a678f62f4f.webp)

นี่คือตัวอย่างโค้ดที่ใช้ AutoGen เพื่อแสดงวิธีการนำแนวคิดนี้ไปใช้:

```python

# สร้างเอเจนต์
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # ใช้ input() เพื่อรับข้อมูลจากผู้ใช้จากคอนโซล

# สร้างเงื่อนไขการสิ้นสุดที่จะจบการสนทนาเมื่อผู้ใช้พิมพ์ว่า "APPROVE"
termination = TextMentionTermination("APPROVE")

# สร้างทีม
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# รันการสนทนาและสตรีมไปยังคอนโซล
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# ใช้ asyncio.run(...) เมื่อรันในสคริปต์
await Console(stream)

```

## สรุป

การสร้างเอเจนต์ AI ที่น่าเชื่อถือจำเป็นต้องมีการออกแบบที่รอบคอบ มาตรการด้านความปลอดภัยที่แข็งแกร่ง และการปรับปรุงอย่างต่อเนื่อง โดยการนำระบบเมตาพรอมต์แบบมีโครงสร้างไปใช้ การเข้าใจภัยคุกคามที่อาจเกิดขึ้น และการใช้กลยุทธ์การลดความเสี่ยง นักพัฒนาสามารถสร้างเอเจนต์ AI ที่ปลอดภัยและมีประสิทธิภาพได้ นอกจากนี้ การผนวกแนวทางมนุษย์ในวงจรยังช่วยให้เอเจนต์ AI ยังคงสอดคล้องกับความต้องการของผู้ใช้ในขณะที่ลดความเสี่ยง ในขณะที่ AI ยังคงพัฒนา การรักษาท่าทีเชิงรุกในด้านความปลอดภัย ความเป็นส่วนตัว และข้อพิจารณาทางจริยธรรมจะเป็นกุญแจสำคัญในการสร้างความไว้วางใจและความเชื่อถือได้ในระบบที่ขับเคลื่อนด้วย AI

### มีคำถามเพิ่มเติมเกี่ยวกับการสร้างเอเจนต์ AI ที่น่าเชื่อถือหรือไม่?

เข้าร่วม [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) เพื่อพบกับผู้เรียนคนอื่น ๆ เข้าร่วมชั่วโมงตอบคำถาม และรับคำตอบสำหรับคำถามเกี่ยวกับเอเจนต์ AI ของคุณ

## แหล่งข้อมูลเพิ่มเติม

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">ภาพรวมการใช้ AI อย่างรับผิดชอบ</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">การประเมินโมเดล AI เชิงกำเนิดและแอปพลิเคชัน AI</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">ข้อความระบบด้านความปลอดภัย</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">เทมเพลตการประเมินความเสี่ยง</a>

## บทเรียนก่อนหน้า

[Agentic RAG](../05-agentic-rag/README.md)

## บทเรียนถัดไป

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**ข้อจำกัดความรับผิดชอบ**:
เอกสารฉบับนี้ถูกแปลโดยใช้บริการแปลภาษาด้วยปัญญาประดิษฐ์ [Co-op Translator](https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้การแปลถูกต้อง โปรดทราบว่าการแปลโดยอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่แม่นยำ เอกสารต้นฉบับในภาษาต้นฉบับควรถือเป็นแหล่งข้อมูลที่เป็นหลักและเชื่อถือได้ สำหรับข้อมูลที่มีความสำคัญ แนะนำให้ใช้บริการแปลโดยมนุษย์ผู้เชี่ยวชาญ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความที่ผิดพลาดอันเกิดจากการใช้การแปลฉบับนี้
<!-- CO-OP TRANSLATOR DISCLAIMER END -->