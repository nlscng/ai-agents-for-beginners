# Khám phá Microsoft Agent Framework

![Agent Framework](../../../translated_images/vi/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Giới thiệu

Bài học này sẽ bao gồm:

- Hiểu về Microsoft Agent Framework: Các tính năng chính và Giá trị  
- Khám phá các Khái niệm Chính của Microsoft Agent Framework
- So sánh MAF với Semantic Kernel và AutoGen: Hướng dẫn Di cư

## Mục tiêu học tập

Sau khi hoàn thành bài học này, bạn sẽ biết cách:

- Xây dựng các AI Agent sẵn sàng cho môi trường sản xuất sử dụng Microsoft Agent Framework
- Áp dụng các tính năng cốt lõi của Microsoft Agent Framework vào các trường hợp sử dụng Agentic của bạn
- Di cư và tích hợp các frameworks và công cụ Agentic hiện có  

## Các mẫu mã nguồn

Các mẫu mã nguồn cho [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) có thể tìm thấy trong kho lưu trữ này dưới các tệp `xx-python-agent-framework` và `xx-dotnet-agent-framework`.

## Hiểu về Microsoft Agent Framework

![Framework Intro](../../../translated_images/vi/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) được xây dựng dựa trên kinh nghiệm và bài học từ Semantic Kernel và AutoGen. Nó cung cấp sự linh hoạt để giải quyết nhiều loại trường hợp sử dụng agentic trong cả môi trường sản xuất và nghiên cứu bao gồm:

- **Điều phối Agent tuần tự** trong các kịch bản cần quy trình làm việc theo từng bước.
- **Điều phối đồng thời** trong các kịch bản các agent cần hoàn thành nhiệm vụ cùng lúc.
- **Điều phối trò chuyện nhóm** trong các kịch bản các agent có thể hợp tác với nhau để hoàn thành một nhiệm vụ.
- **Điều phối bàn giao** trong các kịch bản các agent chuyển giao công việc cho nhau khi các nhiệm vụ con được hoàn thành.
- **Điều phối từ tính** trong các kịch bản một agent quản lý tạo và chỉnh sửa danh sách nhiệm vụ và điều phối các subagent để hoàn thành nhiệm vụ.

Để cung cấp AI Agents trong môi trường sản xuất, MAF còn bao gồm các tính năng sau:

- **Quan sát** thông qua việc sử dụng OpenTelemetry nơi mọi hành động của AI Agent bao gồm gọi công cụ, các bước điều phối, luồng suy luận và giám sát hiệu năng thông qua bảng điều khiển Microsoft Foundry.
- **Bảo mật** bằng cách lưu trữ agents trực tiếp trên Microsoft Foundry bao gồm các kiểm soát bảo mật như quyền truy cập dựa trên vai trò, xử lý dữ liệu riêng tư và tính năng an toàn nội dung tích hợp.
- **Độ bền** khi luồng và workflow của Agent có thể tạm dừng, tiếp tục và phục hồi sau lỗi, cho phép các quy trình chạy lâu dài.
- **Kiểm soát** hỗ trợ quy trình làm việc có sự tham gia của con người, nơi nhiệm vụ được đánh dấu yêu cầu phê duyệt của con người.

Microsoft Agent Framework cũng tập trung vào khả năng tương tác bằng cách:

- **Không phụ thuộc đám mây** - Agents có thể chạy trong container, tại chỗ và trên nhiều đám mây khác nhau.
- **Không phụ thuộc nhà cung cấp** - Agents có thể được tạo qua SDK ưa thích của bạn bao gồm Azure OpenAI và OpenAI.
- **Tích hợp các tiêu chuẩn mở** - Agents có thể sử dụng các giao thức như Agent-to-Agent (A2A) và Model Context Protocol (MCP) để phát hiện và sử dụng các agent và công cụ khác.
- **Plugin và Bộ nối** - Kết nối có thể được thiết lập tới các dịch vụ dữ liệu và bộ nhớ như Microsoft Fabric, SharePoint, Pinecone và Qdrant.

Hãy xem cách các tính năng này được áp dụng vào một số khái niệm cốt lõi của Microsoft Agent Framework.

## Các Khái Niệm Chính của Microsoft Agent Framework

### Agents

![Agent Framework](../../../translated_images/vi/agent-components.410a06daf87b4fef.webp)

**Tạo Agents**

Tạo agent được thực hiện bằng cách định nghĩa dịch vụ suy luận (Nhà cung cấp LLM), một bộ hướng dẫn để AI Agent theo dõi, và gán một `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Trên đây sử dụng `Azure OpenAI` nhưng agent có thể được tạo bằng nhiều dịch vụ khác nhau bao gồm `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI API `Responses`, `ChatCompletion`

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

hoặc agent từ xa dùng giao thức A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Chạy Agents**

Agents được chạy bằng các phương thức `.run` hoặc `.run_stream` cho các phản hồi không theo luồng hoặc theo luồng tương ứng.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Mỗi lần chạy agent cũng có thể có các tùy chọn để tùy chỉnh tham số như `max_tokens` mà agent sử dụng, `tools` mà agent có thể gọi, và thậm chí `model` được sử dụng cho agent.

Điều này hữu ích trong các trường hợp cần mô hình hoặc công cụ cụ thể để hoàn thành công việc của người dùng.

**Công cụ**

Công cụ có thể được định nghĩa cả khi tạo agent:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Khi tạo một ChatAgent trực tiếp

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

và cũng khi chạy agent:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Công cụ chỉ được cung cấp cho lần chạy này )
```

**Luồng Agent**

Luồng Agent được sử dụng để xử lý các cuộc hội thoại nhiều lượt. Luồng có thể được tạo bằng cách:

- Sử dụng `get_new_thread()` cho phép luồng được lưu lại theo thời gian
- Tạo luồng tự động khi chạy agent và luồng chỉ tồn tại trong lần chạy hiện tại.

Để tạo một luồng, mã sẽ như sau:

```python
# Tạo một luồng mới.
thread = agent.get_new_thread() # Chạy tác nhân với luồng đó.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Bạn có thể tuần tự hóa luồng để lưu trữ sử dụng sau:

```python
# Tạo một luồng mới.
thread = agent.get_new_thread() 

# Chạy agent với luồng.

response = await agent.run("Hello, how are you?", thread=thread) 

# Tuần tự hóa luồng để lưu trữ.

serialized_thread = await thread.serialize() 

# Giải tuần tự hóa trạng thái luồng sau khi tải từ bộ nhớ.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent Middleware**

Agents tương tác với các công cụ và LLM để hoàn thành công việc của người dùng. Trong một số kịch bản, chúng ta muốn thực thi hoặc theo dõi các tương tác này. Middleware của agent cho phép chúng ta làm điều đó thông qua:

*Middleware chức năng*

Middleware này cho phép thực thi một hành động giữa agent và một hàm/công cụ mà nó sẽ gọi. Ví dụ khi muốn ghi lại log cuộc gọi hàm.

Trong mã dưới đây, `next` xác định có gọi middleware tiếp theo hoặc hàm thực tế hay không.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Tiền xử lý: Ghi nhật ký trước khi thực thi hàm
    print(f"[Function] Calling {context.function.name}")

    # Tiếp tục đến middleware hoặc thực thi hàm tiếp theo
    await next(context)

    # Hậu xử lý: Ghi nhật ký sau khi thực thi hàm
    print(f"[Function] {context.function.name} completed")
```

*Middleware trò chuyện*

Middleware này cho phép thực thi hoặc ghi lại một hành động giữa agent và các yêu cầu gửi tới LLM.

Nội dung bao gồm thông tin quan trọng như các `messages` được gửi đến dịch vụ AI.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Tiền xử lý: Ghi nhật ký trước khi gọi AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Tiếp tục đến middleware hoặc dịch vụ AI tiếp theo
    await next(context)

    # Hậu xử lý: Ghi nhật ký sau phản hồi của AI
    print("[Chat] AI response received")

```

**Bộ nhớ Agent**

Như đã đề cập trong bài học `Agentic Memory`, bộ nhớ là yếu tố quan trọng giúp agent hoạt động trên các ngữ cảnh khác nhau. MAF cung cấp nhiều loại bộ nhớ khác nhau:

*Bộ nhớ trong bộ nhớ tạm*

Đây là bộ nhớ được lưu trong các luồng trong thời gian chạy ứng dụng.

```python
# Tạo một luồng mới.
thread = agent.get_new_thread() # Chạy tác nhân với luồng đó.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Tin nhắn lưu trữ lâu dài*

Bộ nhớ này được dùng khi lưu lịch sử hội thoại qua các phiên khác nhau. Nó được định nghĩa qua `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Tạo một kho lưu trữ tin nhắn tùy chỉnh
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Bộ nhớ động*

Bộ nhớ này được thêm vào ngữ cảnh trước khi agent chạy. Các bộ nhớ này có thể được lưu trong dịch vụ bên ngoài như mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Sử dụng Mem0 cho các khả năng bộ nhớ nâng cao
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

**Quan sát Agent**

Quan sát là quan trọng để xây dựng các hệ thống agentic đáng tin cậy và dễ bảo trì. MAF tích hợp với OpenTelemetry để cung cấp truy vết và đo lường nhằm cải thiện khả năng quan sát.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # làm gì đó
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Workflows

MAF cung cấp workflows là các bước được định nghĩa sẵn để hoàn thành một công việc và bao gồm AI agents như là các thành phần trong các bước đó.

Workflows được tạo thành từ các thành phần khác nhau cho phép kiểm soát luồng tốt hơn. Workflows cũng cho phép **điều phối đa agent** và **điểm kiểm tra** để lưu trạng thái workflow.

Các thành phần cốt lõi của một workflow là:

**Executors**

Executors nhận thông điệp đầu vào, thực hiện các nhiệm vụ được giao, rồi tạo ra thông điệp đầu ra. Điều này đẩy workflow tiến về phía nhiệm vụ lớn hơn. Executors có thể là AI agent hoặc logic tùy chỉnh.

**Edges**

Edges được dùng để định nghĩa luồng thông điệp trong workflow. Có thể là:

*Direct Edges* - Kết nối một-một đơn giản giữa các executors:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Conditional Edges* - Kích hoạt sau khi điều kiện nhất định được thỏa mãn. Ví dụ, khi phòng khách sạn không còn chỗ, một executor có thể đề xuất các lựa chọn khác.

*Switch-case Edges* - Chuyển hướng thông điệp tới các executors khác nhau dựa trên điều kiện đã định nghĩa. Ví dụ nếu khách du lịch có quyền ưu tiên thì nhiệm vụ sẽ được xử lý qua workflow khác.

*Fan-out Edges* - Gửi một thông điệp tới nhiều đích.

*Fan-in Edges* - Thu thập nhiều thông điệp từ các executors khác nhau và gửi đến một đích.

**Events**

Để cải thiện khả năng quan sát trong workflows, MAF cung cấp các sự kiện tích hợp cho việc thực thi bao gồm:

- `WorkflowStartedEvent`  - Bắt đầu thực thi workflow
- `WorkflowOutputEvent` - Workflow tạo ra kết quả đầu ra
- `WorkflowErrorEvent` - Workflow gặp lỗi
- `ExecutorInvokeEvent`  - Executor bắt đầu xử lý
- `ExecutorCompleteEvent`  -  Executor hoàn thành xử lý
- `RequestInfoEvent` - Một yêu cầu được phát ra

## Di cư từ các Framework khác (Semantic Kernel và AutoGen)

### Sự khác biệt giữa MAF và Semantic Kernel

**Tạo Agent Đơn giản hóa**

Semantic Kernel yêu cầu tạo một instance Kernel cho mỗi agent. MAF dùng cách đơn giản hơn bằng cách sử dụng extension cho các nhà cung cấp chính.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Tạo Luồng Agent**

Semantic Kernel yêu cầu tạo luồng thủ công. Trong MAF, agent được trực tiếp gán một luồng.

```python
thread = agent.get_new_thread() # Chạy tác nhân với luồng.
```

**Đăng ký Công cụ**

Trong Semantic Kernel, công cụ được đăng ký vào Kernel rồi Kernel được truyền đến agent. Trong MAF, công cụ được đăng ký trực tiếp trong quá trình tạo agent.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Sự khác biệt giữa MAF và AutoGen

**Teams và Workflows**

`Teams` là cấu trúc sự kiện cho hoạt động dựa trên sự kiện với agents trong AutoGen. MAF dùng `Workflows` mà chuyển dữ liệu đến executors qua kiến trúc dạng đồ thị.

**Tạo Công cụ**

AutoGen dùng `FunctionTool` để đóng gói các hàm cho agent gọi. MAF dùng @ai_function hoạt động tương tự nhưng cũng tự động suy luận schema cho mỗi hàm.

**Hành vi Agent**

Agents trong AutoGen mặc định là single-turn trừ khi `max_tool_iterations` được đặt cao hơn. Trong MAF, `ChatAgent` mặc định là multi-turn có nghĩa là nó sẽ tiếp tục gọi các công cụ cho đến khi nhiệm vụ của người dùng hoàn thành.

## Các mẫu mã nguồn

Các mẫu mã nguồn cho Microsoft Agent Framework có thể tìm thấy trong kho lưu trữ này dưới các tệp `xx-python-agent-framework` và `xx-dotnet-agent-framework`.

## Còn câu hỏi nào về Microsoft Agent Framework?

Tham gia [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) để gặp gỡ các học viên khác, tham dự giờ làm việc và nhận câu trả lời cho các câu hỏi về AI Agents của bạn.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Tuyên bố miễn trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc thiếu sót. Tài liệu gốc bằng ngôn ngữ bản địa được coi là nguồn chính xác và đáng tin cậy nhất. Đối với các thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp do con người thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu lầm hoặc giải thích sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->