[![Các tác nhân AI đáng tin cậy](../../../translated_images/vi/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Nhấp vào hình ảnh trên để xem video bài học này)_

# Xây Dựng Các Tác Nhân AI Đáng Tin Cậy

## Giới thiệu

Bài học này sẽ đề cập đến:

- Cách xây dựng và triển khai các tác nhân AI an toàn và hiệu quả
- Những cân nhắc quan trọng về bảo mật khi phát triển các tác nhân AI.
- Cách duy trì quyền riêng tư dữ liệu và người dùng khi phát triển các tác nhân AI.

## Mục tiêu học tập

Sau khi hoàn thành bài học này, bạn sẽ biết cách:

- Xác định và giảm thiểu rủi ro khi tạo các tác nhân AI.
- Thực hiện các biện pháp bảo mật để đảm bảo dữ liệu và quyền truy cập được quản lý đúng cách.
- Tạo các tác nhân AI duy trì quyền riêng tư dữ liệu và cung cấp trải nghiệm người dùng chất lượng.

## An toàn

Trước tiên, hãy xem xét việc xây dựng các ứng dụng tác nhân an toàn. An toàn có nghĩa là tác nhân AI hoạt động như được thiết kế. Với tư cách là người xây dựng các ứng dụng tác nhân, chúng ta có các phương pháp và công cụ để tối đa hóa sự an toàn:

### Xây dựng Khung Tin nhắn Hệ thống

Nếu bạn từng xây dựng ứng dụng AI sử dụng Mô hình Ngôn ngữ Lớn (LLMs), bạn sẽ biết tầm quan trọng của việc thiết kế lời nhắc hệ thống hoặc tin nhắn hệ thống mạnh mẽ. Những lời nhắc này thiết lập các quy tắc meta, hướng dẫn và chỉ dẫn về cách LLM sẽ tương tác với người dùng và dữ liệu.

Đối với các tác nhân AI, lời nhắc hệ thống còn quan trọng hơn vì các tác nhân AI sẽ cần các hướng dẫn rất cụ thể để hoàn thành các nhiệm vụ mà chúng ta đã thiết kế cho chúng.

Để tạo lời nhắc hệ thống có thể mở rộng, chúng ta có thể sử dụng khung tin nhắn hệ thống để xây dựng một hoặc nhiều tác nhân trong ứng dụng của mình:

![Xây dựng Khung Tin nhắn Hệ thống](../../../translated_images/vi/system-message-framework.3a97368c92d11d68.webp)

#### Bước 1: Tạo Tin nhắn Hệ thống Meta

Lời nhắc meta sẽ được sử dụng bởi LLM để tạo ra các lời nhắc hệ thống cho các tác nhân mà chúng ta tạo ra. Chúng ta thiết kế nó như một mẫu để có thể hiệu quả tạo nhiều tác nhân nếu cần.

Dưới đây là ví dụ về một tin nhắn hệ thống meta mà chúng tôi sẽ cung cấp cho LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Bước 2: Tạo lời nhắc cơ bản

Bước tiếp theo là tạo một lời nhắc cơ bản để mô tả Tác nhân AI. Bạn nên bao gồm vai trò của tác nhân, các nhiệm vụ tác nhân sẽ hoàn thành, và bất kỳ trách nhiệm nào khác của tác nhân.

Đây là một ví dụ:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Bước 3: Cung cấp Tin nhắn Hệ thống Cơ bản cho LLM

Bây giờ chúng ta có thể tối ưu hóa tin nhắn hệ thống này bằng cách cung cấp tin nhắn hệ thống meta làm tin nhắn hệ thống và tin nhắn hệ thống cơ bản của chúng ta.

Điều này sẽ tạo ra một tin nhắn hệ thống được thiết kế tốt hơn để hướng dẫn các tác nhân AI của chúng ta:

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

#### Bước 4: Lặp lại và Cải tiến

Giá trị của khung tin nhắn hệ thống này là khả năng mở rộng việc tạo tin nhắn hệ thống từ nhiều tác nhân dễ dàng hơn cũng như cải thiện tin nhắn hệ thống của bạn theo thời gian. Rất hiếm khi bạn sẽ có một tin nhắn hệ thống hoạt động ngay lần đầu cho toàn bộ trường hợp sử dụng của bạn. Việc có thể thực hiện những điều chỉnh nhỏ và cải tiến bằng cách thay đổi tin nhắn hệ thống cơ bản và chạy qua hệ thống sẽ cho phép bạn so sánh và đánh giá kết quả.

## Hiểu về Các Mối đe dọa

Để xây dựng các tác nhân AI đáng tin cậy, điều quan trọng là hiểu và giảm thiểu các rủi ro và mối đe dọa đối với tác nhân AI của bạn. Hãy xem xét một số mối đe dọa khác nhau đối với các tác nhân AI và cách bạn có thể lập kế hoạch và chuẩn bị tốt hơn cho chúng.

![Hiểu về Các Mối đe dọa](../../../translated_images/vi/understanding-threats.89edeada8a97fc0f.webp)

### Nhiệm vụ và Hướng dẫn

**Mô tả:** Kẻ tấn công cố gắng thay đổi các chỉ dẫn hoặc mục tiêu của tác nhân AI thông qua việc tạo lời nhắc hoặc thao túng đầu vào.

**Giảm thiểu**: Thực hiện các kiểm tra xác thực và bộ lọc đầu vào để phát hiện các lời nhắc có thể nguy hiểm trước khi chúng được xử lý bởi Tác nhân AI. Vì các cuộc tấn công này thường đòi hỏi tương tác thường xuyên với Tác nhân, hạn chế số lượt trong một cuộc trò chuyện là một cách khác để ngăn chặn các loại tấn công này.

### Truy cập vào Các Hệ thống Quan trọng

**Mô tả**: Nếu một tác nhân AI có quyền truy cập vào các hệ thống và dịch vụ lưu trữ dữ liệu nhạy cảm, kẻ tấn công có thể xâm phạm giao tiếp giữa tác nhân và các dịch vụ này. Đây có thể là các cuộc tấn công trực tiếp hoặc cố gắng gián tiếp để lấy thông tin về các hệ thống này thông qua tác nhân.

**Giảm thiểu**: Các tác nhân AI nên chỉ được cấp quyền truy cập vào các hệ thống khi thực sự cần thiết để ngăn chặn các loại tấn công này. Giao tiếp giữa tác nhân và hệ thống cũng nên được bảo mật. Việc thực hiện xác thực và kiểm soát truy cập là một cách khác để bảo vệ thông tin này.

### Quá tải Tài nguyên và Dịch vụ

**Mô tả:** Các tác nhân AI có thể truy cập nhiều công cụ và dịch vụ để hoàn thành các nhiệm vụ. Kẻ tấn công có thể lợi dụng khả năng này để tấn công các dịch vụ bằng cách gửi số lượng lớn yêu cầu qua Tác nhân AI, dẫn đến lỗi hệ thống hoặc chi phí cao.

**Giảm thiểu:** Thực hiện các chính sách giới hạn số yêu cầu mà một tác nhân AI có thể gửi đến một dịch vụ. Hạn chế số lượt trò chuyện và yêu cầu gửi tới tác nhân AI của bạn cũng là một cách để ngăn chặn các loại tấn công này.

### Đầu độc Cơ sở Tri thức

**Mô tả:** Loại tấn công này không nhắm trực tiếp vào tác nhân AI mà nhắm vào cơ sở tri thức và các dịch vụ mà tác nhân AI sẽ sử dụng. Điều này có thể liên quan đến việc làm hỏng dữ liệu hoặc thông tin mà tác nhân AI sẽ sử dụng để hoàn thành nhiệm vụ, dẫn đến phản hồi thiên lệch hoặc không mong muốn cho người dùng.

**Giảm thiểu:** Tiến hành kiểm tra định kỳ dữ liệu mà tác nhân AI sẽ sử dụng trong các quy trình làm việc của nó. Đảm bảo quyền truy cập vào dữ liệu này an toàn và chỉ được thay đổi bởi những người tin cậy để tránh loại tấn công này.

### Lỗi Chuỗi

**Mô tả:** Các tác nhân AI truy cập nhiều công cụ và dịch vụ để hoàn thành nhiệm vụ. Các lỗi do kẻ tấn công gây ra có thể dẫn đến sự cố của các hệ thống khác mà tác nhân AI kết nối, khiến cuộc tấn công lan rộng hơn và khó khắc phục hơn.

**Giảm thiểu**: Một phương pháp để tránh điều này là cho Tác nhân AI hoạt động trong môi trường giới hạn, chẳng hạn như thực hiện nhiệm vụ trong container Docker, để ngăn chặn tấn công hệ thống trực tiếp. Tạo các cơ chế dự phòng và logic thử lại khi một hệ thống trả về lỗi cũng là một cách để ngăn ngừa sự cố hệ thống lớn hơn.

## Con Người Trong Vòng Lặp

Một cách hiệu quả khác để xây dựng hệ thống Tác nhân AI đáng tin cậy là sử dụng Con Người trong vòng lặp. Điều này tạo ra luồng nơi người dùng có thể cung cấp phản hồi cho các Tác nhân trong quá trình chạy. Người dùng thực chất đóng vai trò như các tác nhân trong hệ thống đa tác nhân và duyệt chấp thuận hoặc chấm dứt quá trình đang chạy.

![Con Người Trong Vòng Lặp](../../../translated_images/vi/human-in-the-loop.5f0068a678f62f4f.webp)

Dưới đây là đoạn mã sử dụng AutoGen để minh họa cách khái niệm này được triển khai:

```python

# Tạo các tác nhân.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Sử dụng input() để nhận dữ liệu người dùng từ bảng điều khiển.

# Tạo điều kiện kết thúc sẽ dừng cuộc trò chuyện khi người dùng nói "APPROVE".
termination = TextMentionTermination("APPROVE")

# Tạo nhóm.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Chạy cuộc trò chuyện và phát trực tiếp lên bảng điều khiển.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Sử dụng asyncio.run(...) khi chạy trong một tập lệnh.
await Console(stream)

```

## Kết luận

Xây dựng các tác nhân AI đáng tin cậy đòi hỏi thiết kế cẩn thận, các biện pháp bảo mật vững chắc và sự lặp lại liên tục. Bằng cách thực hiện hệ thống lời nhắc meta có cấu trúc, hiểu các mối đe dọa tiềm ẩn và áp dụng các chiến lược giảm thiểu, nhà phát triển có thể tạo ra các tác nhân AI vừa an toàn vừa hiệu quả. Thêm vào đó, tích hợp phương pháp con người trong vòng lặp đảm bảo các tác nhân AI luôn phù hợp với nhu cầu người dùng đồng thời giảm thiểu rủi ro. Khi AI tiếp tục phát triển, duy trì sự chủ động về bảo mật, quyền riêng tư và các cân nhắc đạo đức sẽ là chìa khóa để xây dựng niềm tin và độ tin cậy trong các hệ thống vận hành bởi AI.

### Bạn còn câu hỏi nào về Xây Dựng Các Tác Nhân AI Đáng Tin Cậy không?

Tham gia [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) để gặp gỡ các học viên khác, tham dự giờ làm việc và nhận giải đáp câu hỏi về các Tác nhân AI của bạn.

## Tài nguyên bổ sung

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Tổng quan về AI có trách nhiệm</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Đánh giá các mô hình AI tạo sinh và ứng dụng AI</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Tin nhắn hệ thống về an toàn</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Mẫu Đánh giá Rủi ro</a>

## Bài học trước

[Agentic RAG](../05-agentic-rag/README.md)

## Bài học tiếp theo

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi nỗ lực để đảm bảo độ chính xác, xin lưu ý rằng bản dịch tự động có thể chứa lỗi hoặc không chính xác. Văn bản gốc bằng ngôn ngữ gốc của nó nên được coi là nguồn chính thức. Đối với các thông tin quan trọng, khuyến nghị sử dụng dịch vụ dịch thuật chuyên nghiệp do con người thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ hiểu lầm hay sai lệch nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->