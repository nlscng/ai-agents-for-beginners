[![วิธีออกแบบเอเจนต์ AI ที่ดี](../../../translated_images/th/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(คลิกที่รูปด้านบนเพื่อดูวิดีโอของบทเรียนนี้)_

# รูปแบบการออกแบบการใช้เครื่องมือ

เครื่องมือมีความน่าสนใจเพราะช่วยให้เอเจนต์ AI มีขอบเขตความสามารถที่กว้างขึ้น แทนที่จะให้เอเจนต์มีชุดการกระทำที่จำกัด การเพิ่มเครื่องมือเข้ามาจะช่วยให้เอเจนต์สามารถทำงานได้หลากหลายยิ่งขึ้น ในบทนี้ เราจะดูรูปแบบการออกแบบการใช้เครื่องมือ (Tool Use Design Pattern) ซึ่งอธิบายว่าทำไมเอเจนต์ AI จึงสามารถใช้เครื่องมือเฉพาะเพื่อให้บรรลุเป้าหมายได้อย่างไร

## บทนำ

ในบทเรียนนี้ เราต้องการตอบคำถามต่อไปนี้:

- รูปแบบการออกแบบการใช้เครื่องมือคืออะไร?
- มีกรณีการใช้งานใดบ้างที่สามารถนำไปใช้ได้?
- องค์ประกอบ/บล็อกพื้นฐานใดบ้างที่จำเป็นเพื่อการนำรูปแบบการออกแบบนี้ไปใช้?
- มีข้อพิจารณาพิเศษใดบ้างในการใช้รูปแบบการออกแบบการใช้เครื่องมือเพื่อสร้างเอเจนต์ AI ที่น่าเชื่อถือ?

## เป้าหมายการเรียนรู้

หลังจากเรียนจบบทเรียนนี้ คุณจะสามารถ:

- นิยามรูปแบบการออกแบบการใช้เครื่องมือและวัตถุประสงค์ของมัน
- ระบุกรณีการใช้งานที่รูปแบบการออกแบบการใช้เครื่องมือสามารถนำไปใช้ได้
- เข้าใจองค์ประกอบหลักที่จำเป็นเพื่อการนำรูปแบบการออกแบบนี้ไปใช้
- ตระหนักถึงข้อพิจารณาในการรับรองความน่าเชื่อถือของเอเจนต์ AI ที่ใช้รูปแบบการออกแบบนี้

## รูปแบบการออกแบบการใช้เครื่องมือคืออะไร?

รูปแบบการออกแบบการใช้เครื่องมือ (Tool Use Design Pattern) มุ่งเน้นที่การให้ LLMs สามารถโต้ตอบกับเครื่องมือภายนอกเพื่อบรรลุเป้าหมายเฉพาะ เครื่องมือคือโค้ดที่สามารถเรียกใช้โดยเอเจนต์เพื่อทำการกระทำ เครื่องมืออาจเป็นฟังก์ชันง่าย ๆ เช่น เครื่องคิดเลข หรือการเรียก API ไปยังบริการบุคคลที่สามเช่นการค้นหาราคาหุ้นหรือการพยากรณ์อากาศ ในบริบทของเอเจนต์ AI เครื่องมือถูกออกแบบให้เรียกใช้งานโดยเอเจนต์เพื่อตอบสนองต่อการเรียกฟังก์ชันที่สร้างโดยโมเดล (model-generated function calls)

## กรณีการใช้งานที่สามารถนำไปใช้ได้มีอะไรบ้าง?

เอเจนต์ AI สามารถใช้เครื่องมือเพื่อทำงานที่ซับซ้อน ดึงข้อมูล หรือช่วยในการตัดสินใจ รูปแบบการออกแบบการใช้เครื่องมือมักถูกใช้ในสถานการณ์ที่ต้องการการโต้ตอบแบบไดนามิกกับระบบภายนอก เช่น ฐานข้อมูล บริการเว็บ หรือโปรแกรมประมวลผลโค้ด ความสามารถนี้เป็นประโยชน์สำหรับกรณีการใช้งานต่าง ๆ เช่น:

- การดึงข้อมูลแบบไดนามิก: เอเจนต์สามารถเรียก API ภายนอกหรือฐานข้อมูลเพื่อนำข้อมูลที่เป็นปัจจุบัน (เช่น การสอบถามฐานข้อมูล SQLite เพื่อวิเคราะห์ข้อมูล, ดึงราคาหุ้น หรือข้อมูลสภาพอากาศ)
- การรันและตีความโค้ด: เอเจนต์สามารถรันโค้ดหรือสคริปต์เพื่อแก้ปัญหาทางคณิตศาสตร์ สร้างรายงาน หรือทำการจำลอง
- การอัตโนมัติของเวิร์กโฟลว์: การอัตโนมัติของงานที่ทำซ้ำหรือหลายขั้นตอนโดยการผสานรวมเครื่องมือ เช่น ตัวจัดตารางงาน บริการอีเมล หรือท่อข้อมูล
- ฝ่ายสนับสนุนลูกค้า: เอเจนต์สามารถโต้ตอบกับระบบ CRM แพลตฟอร์มตั๋ว หรือฐานความรู้เพื่อตอบคำถามของผู้ใช้
- การสร้างและแก้ไขเนื้อหา: เอเจนต์สามารถใช้เครื่องมืออย่างตัวตรวจไวยากรณ์ ตัวสรุปข้อความ หรือตัวประเมินความปลอดภัยของเนื้อหาเพื่อช่วยในการสร้างเนื้อหา

## องค์ประกอบ/บล็อกพื้นฐานที่จำเป็นเพื่อการนำรูปแบบการออกแบบการใช้เครื่องมือไปใช้คืออะไร?

บล็อกพื้นฐานเหล่านี้ช่วยให้เอเจนต์ AI สามารถทำงานหลากหลายได้ มาดูองค์ประกอบหลักที่จำเป็นเพื่อการนำ Tool Use Design Pattern ไปใช้:

- Function/Tool Schemas: คำจำกัดความโดยละเอียดของเครื่องมือที่ใช้งานได้ รวมถึงชื่อฟังก์ชัน วัตถุประสงค์ พารามิเตอร์ที่จำเป็น และผลลัพธ์ที่คาดหวัง Schema เหล่านี้ช่วยให้ LLM เข้าใจว่าเครื่องมือใดสามารถใช้ได้และวิธีสร้างคำขอที่ถูกต้อง

- Function Execution Logic: กำหนดวิธีและเวลาที่เครื่องมือถูกเรียกใช้งานตามเจตนาของผู้ใช้และบริบทการสนทนา อาจรวมถึงโมดูลวางแผน กลไกรูทติ้ง หรือลำดับเงื่อนไขที่กำหนดการใช้เครื่องมือแบบไดนามิก

- Message Handling System: ส่วนประกอบที่จัดการการไหลของการสนทนาระหว่างอินพุตผู้ใช้ การตอบของ LLM การเรียกเครื่องมือ และผลลัพธ์จากเครื่องมือ

- Tool Integration Framework: โครงสร้างพื้นฐานที่เชื่อมต่อเอเจนต์กับเครื่องมือต่าง ๆ ไม่ว่าจะเป็นฟังก์ชันง่าย ๆ หรือบริการภายนอกที่ซับซ้อน

- Error Handling & Validation: กลไกสำหรับจัดการความล้มเหลวในการเรียกใช้เครื่องมือ ตรวจสอบพารามิเตอร์ และจัดการการตอบสนองที่ไม่คาดคิด

- State Management: ติดตามบริบทการสนทนา การโต้ตอบกับเครื่องมือก่อนหน้า และข้อมูลถาวรเพื่อให้แน่ใจถึงความสอดคล้องในการโต้ตอบหลายรอบ

ต่อไป เรามาดู Function/Tool Calling โดยละเอียดมากขึ้น
 
### การเรียกใช้งานฟังก์ชัน/เครื่องมือ

การเรียกฟังก์ชันเป็นวิธีหลักที่เราเปิดโอกาสให้ Large Language Models (LLMs) โต้ตอบกับเครื่องมือ คุณจะเห็นคำว่า 'Function' และ 'Tool' ใช้สลับกันเพราะ 'functions' (บล็อกของโค้ดที่นำกลับมาใช้ได้) คือ 'tools' ที่เอเจนต์ใช้เพื่อทำงานต่าง ๆ เพื่อให้โค้ดของฟังก์ชันถูกเรียกใช้งาน LLM ต้องเปรียบเทียบคำขอของผู้ใช้กับคำอธิบายของฟังก์ชัน ในการทำเช่นนี้ จะส่ง schema ที่มีคำอธิบายของฟังก์ชันทั้งหมดที่มีให้กับ LLM จากนั้น LLM จะเลือกฟังก์ชันที่เหมาะสมที่สุดสำหรับงานและส่งคืนชื่อและอาร์กิวเมนต์ของมัน ฟังก์ชันที่ถูกเลือกจะถูกเรียกใช้งาน ผลลัพธ์ของมันจะถูกส่งกลับไปยัง LLM ซึ่งใช้ข้อมูลนั้นเพื่อตอบคำขอของผู้ใช้

สำหรับนักพัฒนาในการนำการเรียกฟังก์ชันสำหรับเอเจนต์ไปใช้ คุณจะต้องมี:

1. โมเดล LLM ที่รองรับการเรียกฟังก์ชัน
2. Schema ที่มีคำอธิบายฟังก์ชัน
3. โค้ดสำหรับแต่ละฟังก์ชันที่อธิบายไว้

ลองใช้ตัวอย่างการดึงเวลาปัจจุบันในเมืองมาเป็นภาพประกอบ:

1. **เริ่มต้น LLM ที่รองรับการเรียกฟังก์ชัน:**

    ไม่ใช่ทุกรุ่นที่จะรองรับการเรียกฟังก์ชัน ดังนั้นจึงสำคัญที่จะตรวจสอบว่า LLM ที่คุณใช้รองรับหรือไม่     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> รองรับการเรียกฟังก์ชัน เราสามารถเริ่มต้นโดยการสร้าง client ของ Azure OpenAI ได้

    ```python
    # เริ่มต้นไคลเอนต์ Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **สร้าง Function Schema**:

    ต่อไปเราจะกำหนด JSON schema ที่ประกอบด้วยชื่อฟังก์ชัน คำอธิบายของสิ่งที่ฟังก์ชันทำ และชื่อพร้อมคำอธิบายของพารามิเตอร์ของฟังก์ชัน
    จากนั้นเราจะนำ schema นี้และส่งไปยัง client ที่สร้างไว้ก่อนหน้านี้ พร้อมกับคำขอของผู้ใช้เพื่อค้นหาเวลาที่ซานฟรานซิสโก สิ่งที่สำคัญคือต้องสังเกตว่า **การเรียกเครื่องมือ** เป็นสิ่งที่ถูกส่งกลับมา **ไม่ใช่** คำตอบสุดท้ายตามคำถาม ตามที่กล่าวไว้ก่อนหน้านี้ LLM จะส่งคืนชื่อของฟังก์ชันที่มันเลือกสำหรับงาน และอาร์กิวเมนต์ที่จะถูกส่งให้มัน

    ```python
    # คำอธิบายฟังก์ชันสำหรับให้โมเดลอ่าน
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # ข้อความเริ่มต้นของผู้ใช้
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # การเรียก API ครั้งแรก: ขอให้โมเดลใช้ฟังก์ชัน
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # ประมวลผลการตอบกลับของโมเดล
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **โค้ดของฟังก์ชันที่จำเป็นเพื่อทำงาน:**

    ตอนนี้ที่ LLM ได้เลือกแล้วว่าฟังก์ชันใดจำเป็นต้องรัน โค้ดที่ทำงานนั้นต้องถูกเขียนและเรียกใช้งาน
    เราสามารถเขียนโค้ดเพื่อดึงเวลาปัจจุบันใน Python ได้ เราจะต้องเขียนโค้ดเพื่อสกัดชื่อและอาร์กิวเมนต์จาก response_message เพื่อให้ได้ผลลัพธ์สุดท้ายด้วย

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # จัดการการเรียกฟังก์ชัน
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # การเรียก API ครั้งที่สอง: รับคำตอบสุดท้ายจากโมเดล
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

การเรียกฟังก์ชันอยู่ที่แกนกลางของรูปแบบการใช้เครื่องมือของเอเจนต์ส่วนใหญ่ หากไม่ใช่ทั้งหมด อย่างไรก็ตามการนำมันมาปรับใช้จากศูนย์อาจท้าทายในบางครั้ง
ดังที่เราได้เรียนรู้ใน [Lesson 2](../../../02-explore-agentic-frameworks) เฟรมเวิร์กสำหรับเอเจนต์ (agentic frameworks) ให้บล็อกพื้นฐานที่สร้างไว้ล่วงหน้าแก่เราเพื่อนำการใช้เครื่องมือไปใช้ได้ง่ายขึ้น
 
## ตัวอย่างการใช้เครื่องมือด้วยเฟรมเวิร์กสำหรับเอเจนต์

ต่อไปนี้เป็นตัวอย่างบางส่วนของวิธีที่คุณสามารถนำ Tool Use Design Pattern ไปใช้โดยใช้เฟรมเวิร์กสำหรับเอเจนต์ต่าง ๆ:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> เป็นเฟรมเวิร์ก AI แบบโอเพ่นซอร์สสำหรับนักพัฒนา .NET, Python, และ Java ที่ทำงานกับ Large Language Models (LLMs) มันทำให้กระบวนการใช้การเรียกฟังก์ชันง่ายขึ้นโดยการอธิบายฟังก์ชันของคุณและพารามิเตอร์ของมันกับโมเดลโดยอัตโนมัติผ่านกระบวนการที่เรียกว่า <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializing</a> มันยังจัดการการสื่อสารไปมาระหว่างโมเดลและโค้ดของคุณ อีกหนึ่งข้อได้เปรียบของการใช้เฟรมเวิร์กสำหรับเอเจนต์อย่าง Semantic Kernel คือมันช่วยให้คุณเข้าถึงเครื่องมือที่สร้างไว้ล่วงหน้าได้ เช่น <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> และ <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>

แผนภาพต่อไปนี้แสดงกระบวนการของการเรียกฟังก์ชันด้วย Semantic Kernel:

![การเรียกฟังก์ชัน](../../../translated_images/th/functioncalling-diagram.a84006fc287f6014.webp)

ใน Semantic Kernel ฟังก์ชัน/เครื่องมือถูกเรียกว่า <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a> เราสามารถแปลงฟังก์ชัน `get_current_time` ที่เห็นก่อนหน้านี้ให้เป็น plugin โดยการเปลี่ยนมันเป็นคลาสที่มีฟังก์ชันนั้นอยู่ภายใน เราสามารถนำเข้า decorator `kernel_function` ซึ่งรับคำอธิบายของฟังก์ชัน เมื่อคุณสร้าง kernel พร้อมกับ GetCurrentTimePlugin นั้น kernel จะทำการ serialize ฟังก์ชันและพารามิเตอร์ของมันโดยอัตโนมัติเพื่อสร้าง schema ที่จะส่งไปยัง LLM ในกระบวนการ

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# สร้างเคอร์เนล
kernel = Kernel()

# สร้างปลั๊กอิน
get_current_time_plugin = GetCurrentTimePlugin(location)

# เพิ่มปลั๊กอินลงในเคอร์เนล
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> เป็นเฟรมเวิร์กสำหรับเอเจนต์รุ่นใหม่ที่ออกแบบมาเพื่อให้ผู้พัฒนาสามารถสร้าง ปรับใช้ และปรับขนาดเอเจนต์ AI คุณภาพสูงที่ขยายได้อย่างปลอดภัยโดยไม่ต้องจัดการทรัพยากรคอมพิวต์และพื้นที่เก็บข้อมูลเบื้องหลัง มันมีประโยชน์เป็นพิเศษสำหรับแอปพลิเคชันระดับองค์กรเนื่องจากเป็นบริการที่จัดการแบบเต็มรูปแบบพร้อมมาตรการความปลอดภัยระดับองค์กร

เมื่อเทียบกับการพัฒนาด้วย LLM API โดยตรง Azure AI Agent Service ให้ข้อได้เปรียบบางประการ รวมถึง:

- การเรียกเครื่องมือโดยอัตโนมัติ – ไม่จำเป็นต้องแยกวิเคราะห์การเรียกเครื่องมือ เรียกใช้งานเครื่องมือ และจัดการการตอบกลับ; ทั้งหมดนี้จะทำบนฝั่งเซิร์ฟเวอร์
- การจัดการข้อมูลอย่างปลอดภัย – แทนที่จะจัดการสถานะการสนทนาด้วยตัวเอง คุณสามารถพึ่งพา threads เพื่อเก็บข้อมูลที่คุณต้องการทั้งหมด
- เครื่องมือพร้อมใช้งานนอกกล่อง – เครื่องมือที่คุณสามารถใช้เพื่อโต้ตอบกับแหล่งข้อมูลของคุณ เช่น Bing, Azure AI Search, และ Azure Functions

เครื่องมือที่มีใน Azure AI Agent Service สามารถแบ่งออกเป็นสองหมวดหมู่:

1. Knowledge Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Action Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Agent Service ช่วยให้เราสามารถใช้เครื่องมือเหล่านี้ร่วมกันเป็น `toolset` ได้ นอกจากนี้ยังใช้ `threads` ซึ่งติดตามประวัติของข้อความจากการสนทนาแต่ละครั้ง

ลองนึกภาพว่าคุณเป็นพนักงานฝ่ายขายที่บริษัทชื่อ Contoso คุณต้องการพัฒนาเอเจนต์การสนทนาที่สามารถตอบคำถามเกี่ยวกับข้อมูลการขายของคุณได้

ภาพต่อไปนี้แสดงวิธีที่คุณอาจใช้ Azure AI Agent Service เพื่อวิเคราะห์ข้อมูลการขายของคุณ:

![Agentic Service In Action](../../../translated_images/th/agent-service-in-action.34fb465c9a84659e.webp)

ในการใช้เครื่องมือใด ๆ กับบริการนี้ เราสามารถสร้าง client และกำหนดเครื่องมือหรือชุดเครื่องมือ ในการนำไปปฏิบัติจริงเราสามารถใช้โค้ด Python ต่อไปนี้ LLM จะสามารถดูที่ toolset และตัดสินใจว่าจะใช้ฟังก์ชันที่ผู้ใช้สร้างขึ้น `fetch_sales_data_using_sqlite_query` หรือ Code Interpreter ที่สร้างไว้ล่วงหน้าขึ้นอยู่กับคำขอของผู้ใช้

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # ฟังก์ชัน fetch_sales_data_using_sqlite_query ซึ่งสามารถพบได้ในไฟล์ fetch_sales_data_functions.py
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# เริ่มต้นชุดเครื่องมือ
toolset = ToolSet()

# เริ่มต้นตัวแทนเรียกใช้ฟังก์ชันด้วยฟังก์ชัน fetch_sales_data_using_sqlite_query และเพิ่มลงในชุดเครื่องมือ
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# เริ่มต้นเครื่องมือ Code Interpreter และเพิ่มลงในชุดเครื่องมือ
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## ข้อพิจารณาพิเศษสำหรับการใช้รูปแบบการออกแบบการใช้เครื่องมือเพื่อสร้างเอเจนต์ AI ที่น่าเชื่อถือคืออะไร?

ข้อกังวลทั่วไปเกี่ยวกับ SQL ที่สร้างขึ้นแบบไดนามิกโดย LLM คือความปลอดภัย โดยเฉพาะความเสี่ยงของการโจมตีแบบ SQL injection หรือการกระทำที่เป็นอันตราย เช่น การลบหรือดัดแปลงฐานข้อมูล ในขณะที่ข้อกังวลเหล่านี้มีความถูกต้อง แต่สามารถลดความเสี่ยงได้อย่างมีประสิทธิภาพโดยการกำหนดสิทธิ์การเข้าถึงฐานข้อมูลอย่างเหมาะสม สำหรับฐานข้อมูลส่วนใหญ่สิ่งนี้เกี่ยวข้องกับการกำหนดฐานข้อมูลเป็นแบบอ่านอย่างเดียว สำหรับบริการฐานข้อมูลเช่น PostgreSQL หรือ Azure SQL แอปควรได้รับบทบาทแบบอ่านอย่างเดียว (SELECT)

การรันแอปในสภาพแวดล้อมที่ปลอดภัยยิ่งขึ้นจะช่วยเพิ่มการป้องกัน ในสถานการณ์ขององค์กร ข้อมูลมักถูกสกัดและแปลงจากระบบการปฏิบัติการไปยังฐานข้อมูลที่อ่านอย่างเดียวหรือคลังข้อมูลพร้อมสคีมาที่ใช้งานง่าย แนวทางนี้ช่วยให้แน่ใจว่าข้อมูลนั้นปลอดภัย ปรับให้เหมาะสมสำหรับประสิทธิภาพและการเข้าถึง และแอปมีการเข้าถึงแบบจำกัดเป็นแบบอ่านอย่างเดียว

## ตัวอย่างโค้ดตัวอย่าง
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## มีคำถามเพิ่มเติมเกี่ยวกับรูปแบบการออกแบบการใช้เครื่องมือไหม?

เข้าร่วม [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) เพื่อพบผู้เรียนคนอื่นๆ เข้าร่วมชั่วโมงให้คำปรึกษา และรับคำตอบสำหรับคำถามเกี่ยวกับ AI Agents ของคุณ

## แหล่งข้อมูลเพิ่มเติม

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">เวิร์กช็อป Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">เวิร์กช็อป Contoso Creative Writer แบบหลายเอเย่นต์</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">บทแนะนำการเรียกฟังก์ชันของ Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter ของ Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">เครื่องมือ Autogen</a>

## บทเรียนก่อนหน้า

[ทำความเข้าใจรูปแบบการออกแบบเชิงเอเย่นต์](../03-agentic-design-patterns/README.md)

## บทเรียนถัดไป

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
คำชี้แจง:
เอกสารฉบับนี้ได้รับการแปลโดยใช้บริการแปลด้วย AI Co-op Translator (https://github.com/Azure/co-op-translator) แม้เราจะพยายามให้การแปลถูกต้อง โปรดทราบว่าการแปลโดยอัตโนมัติอาจมีข้อผิดพลาดหรือความไม่แม่นยำ เอกสารต้นฉบับในภาษาต้นทางควรถือเป็นแหล่งข้อมูลที่เชื่อถือได้ สำหรับข้อมูลที่มีความสำคัญ ขอแนะนำให้ใช้การแปลโดยนักแปลมืออาชีพ เราไม่รับผิดชอบต่อความเข้าใจผิดหรือการตีความผิดที่เกิดจากการใช้การแปลฉบับนี้
<!-- CO-OP TRANSLATOR DISCLAIMER END -->