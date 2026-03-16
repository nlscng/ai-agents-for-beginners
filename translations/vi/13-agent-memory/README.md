# Bộ nhớ cho Tác nhân AI 
[![Bộ nhớ tác nhân](../../../translated_images/vi/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Khi thảo luận về những lợi ích độc đáo của việc tạo Tác nhân AI, thường nhắc đến hai điều chính: khả năng gọi công cụ để hoàn thành nhiệm vụ và khả năng cải thiện theo thời gian. Bộ nhớ là nền tảng của việc tạo tác nhân tự cải tiến có thể mang lại trải nghiệm tốt hơn cho người dùng của chúng ta.

Trong bài học này, chúng ta sẽ xem xét bộ nhớ là gì đối với Tác nhân AI và cách chúng ta có thể quản lý và sử dụng nó để mang lại lợi ích cho các ứng dụng của mình.

## Giới thiệu

Bài học này sẽ bao gồm:

• **Hiểu về Bộ nhớ của Tác nhân AI**: Bộ nhớ là gì và tại sao nó cần thiết cho các tác nhân.

• **Triển khai và Lưu trữ Bộ nhớ**: Các phương pháp thực tiễn để thêm khả năng bộ nhớ cho tác nhân AI của bạn, tập trung vào bộ nhớ ngắn hạn và dài hạn.

• **Làm cho Tác nhân AI Tự Cải thiện**: Cách bộ nhớ cho phép tác nhân học từ các tương tác trước và cải thiện theo thời gian.

## Các Triển khai Có sẵn

Bài học này bao gồm hai hướng dẫn notebook toàn diện:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Triển khai bộ nhớ bằng Mem0 và Azure AI Search với framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Triển khai bộ nhớ có cấu trúc bằng Cognee, tự động xây dựng biểu đồ tri thức dựa trên embeddings, trực quan hóa đồ thị và truy xuất thông minh

## Mục tiêu Học tập

Sau khi hoàn thành bài học này, bạn sẽ biết cách:

• **Phân biệt giữa các loại bộ nhớ của tác nhân AI khác nhau**, bao gồm bộ nhớ làm việc, ngắn hạn và dài hạn, cũng như các dạng chuyên biệt như persona và bộ nhớ theo tập.

• **Triển khai và quản lý bộ nhớ ngắn hạn và dài hạn cho tác nhân AI** sử dụng framework Semantic Kernel, tận dụng các công cụ như Mem0, Cognee, Whiteboard memory, và tích hợp với Azure AI Search.

• **Hiểu các nguyên tắc đằng sau tác nhân AI tự cải thiện** và cách hệ thống quản lý bộ nhớ mạnh mẽ góp phần vào việc học liên tục và thích nghi.

## Hiểu về Bộ nhớ của Tác nhân AI

Về cốt lõi, **bộ nhớ cho tác nhân AI đề cập đến các cơ chế cho phép chúng lưu giữ và hồi tưởng thông tin**. Thông tin này có thể là các chi tiết cụ thể về một cuộc hội thoại, sở thích người dùng, hành động trong quá khứ, hoặc thậm chí các mẫu đã học.

Không có bộ nhớ, các ứng dụng AI thường là vô trạng thái, nghĩa là mỗi tương tác bắt đầu lại từ đầu. Điều này dẫn đến trải nghiệm người dùng lặp lại và gây bực bội khi tác nhân "quên" ngữ cảnh hoặc sở thích trước đó.

### Tại sao Bộ nhớ Quan trọng?

trí tuệ của một tác nhân gắn chặt với khả năng hồi tưởng và sử dụng thông tin trong quá khứ. Bộ nhớ cho phép tác nhân trở nên:

• **Suy ngẫm**: Học từ các hành động và kết quả trước đó.

• **Tương tác**: Duy trì ngữ cảnh trong một cuộc hội thoại đang diễn ra.

• **Chủ động và Phản ứng**: Dự đoán nhu cầu hoặc phản ứng phù hợp dựa trên dữ liệu lịch sử.

• **Tự chủ**: Hoạt động độc lập hơn bằng cách dựa vào kiến thức đã lưu trữ.

Mục tiêu của việc triển khai bộ nhớ là làm cho tác nhân trở nên **đáng tin cậy và có năng lực** hơn.

### Các Loại Bộ nhớ

#### Bộ nhớ làm việc

Hãy coi đây như một mảnh giấy ghi tạm tác nhân dùng trong một nhiệm vụ hoặc quá trình tư duy đang diễn ra. Nó chứa thông tin ngay lập tức cần thiết để tính toán bước tiếp theo.

Đối với tác nhân AI, bộ nhớ làm việc thường lưu giữ thông tin liên quan nhất từ một cuộc trò chuyện, ngay cả khi lịch sử trò chuyện đầy đủ dài hoặc bị cắt bớt. Nó tập trung vào việc trích xuất các yếu tố chính như yêu cầu, đề xuất, quyết định và hành động.

**Ví dụ về Bộ nhớ làm việc**

Trong một tác nhân đặt vé du lịch, bộ nhớ làm việc có thể lưu yêu cầu hiện tại của người dùng, chẳng hạn như "Tôi muốn đặt một chuyến đi đến Paris". Yêu cầu cụ thể này được giữ trong ngữ cảnh ngay lập tức của tác nhân để hướng dẫn tương tác hiện tại.

#### Bộ nhớ ngắn hạn

Loại bộ nhớ này giữ thông tin trong suốt một cuộc trò chuyện hoặc phiên duy nhất. Đây là ngữ cảnh của cuộc trò chuyện hiện tại, cho phép tác nhân tham chiếu lại các lượt trước trong đối thoại.

**Ví dụ về Bộ nhớ ngắn hạn**

Nếu người dùng hỏi, "Bao nhiêu tiền cho một chuyến bay đến Paris?" và sau đó tiếp tục với "Còn chỗ nghỉ ở đó thì sao?", bộ nhớ ngắn hạn đảm bảo tác nhân biết "ở đó" ám chỉ "Paris" trong cùng cuộc trò chuyện.

#### Bộ nhớ dài hạn

Đây là thông tin tồn tại qua nhiều cuộc trò chuyện hoặc phiên. Nó cho phép tác nhân nhớ sở thích người dùng, tương tác lịch sử, hoặc kiến thức chung trong khoảng thời gian dài. Điều này quan trọng cho cá nhân hóa.

**Ví dụ về Bộ nhớ dài hạn**

Một bộ nhớ dài hạn có thể lưu rằng "Ben thích trượt tuyết và hoạt động ngoài trời, thích cà phê có view núi, và muốn tránh các dốc trượt tuyết nâng cao do một chấn thương trước đây". Thông tin này, học được từ các tương tác trước, ảnh hưởng đến các đề xuất trong các buổi lên kế hoạch du lịch trong tương lai, làm cho chúng rất cá nhân hóa.

#### Bộ nhớ Persona

Loại bộ nhớ chuyên biệt này giúp một tác nhân phát triển một "nhân cách" hoặc "persona" nhất quán. Nó cho phép tác nhân nhớ các chi tiết về bản thân hoặc vai trò dự định, làm cho các tương tác mượt mà và tập trung hơn.

**Ví dụ về Bộ nhớ Persona**
Nếu tác nhân du lịch được thiết kế để là một "chuyên gia lập kế hoạch trượt tuyết", bộ nhớ persona có thể củng cố vai trò này, ảnh hưởng đến phản hồi để phù hợp với giọng điệu và kiến thức của một chuyên gia.

#### Bộ nhớ Quy trình/Tập (Workflow/Episodic Memory)

Bộ nhớ này lưu trữ chuỗi các bước tác nhân thực hiện trong một nhiệm vụ phức tạp, bao gồm cả thành công và thất bại. Nó giống như nhớ các "tập" cụ thể hoặc trải nghiệm trong quá khứ để học hỏi từ chúng.

**Ví dụ về Bộ nhớ Tập**

Nếu tác nhân đã cố gắng đặt một chuyến bay cụ thể nhưng thất bại do không có chỗ, bộ nhớ tập có thể ghi lại thất bại này, cho phép tác nhân thử các chuyến bay thay thế hoặc thông báo cho người dùng về vấn đề đó một cách thông minh hơn trong lần cố gắng sau.

#### Bộ nhớ Thực thể

Điều này liên quan đến việc trích xuất và ghi nhớ các thực thể cụ thể (như người, địa điểm, hoặc vật) và các sự kiện từ cuộc trò chuyện. Nó cho phép tác nhân xây dựng một hiểu biết có cấu trúc về các yếu tố chính được thảo luận.

**Ví dụ về Bộ nhớ Thực thể**

Từ một cuộc trò chuyện về chuyến đi trước, tác nhân có thể trích xuất "Paris," "Eiffel Tower," và "dinner at Le Chat Noir restaurant" như các thực thể. Trong tương tác sau, tác nhân có thể nhớ "Le Chat Noir" và đề nghị đặt bàn mới ở đó.

#### Structured RAG (Retrieval Augmented Generation có Cấu trúc)

Trong khi RAG là một kỹ thuật rộng hơn, "Structured RAG" được nhấn mạnh như một công nghệ bộ nhớ mạnh mẽ. Nó trích xuất thông tin dày đặc, có cấu trúc từ nhiều nguồn khác nhau (cuộc trò chuyện, email, hình ảnh) và sử dụng chúng để nâng cao độ chính xác, khả năng hồi tưởng và tốc độ trong phản hồi. Không giống như RAG cổ điển chỉ dựa vào độ tương đồng ngữ nghĩa, Structured RAG làm việc với cấu trúc vốn có của thông tin.

**Ví dụ về Structured RAG**

Thay vì chỉ khớp từ khóa, Structured RAG có thể phân tích chi tiết chuyến bay (điểm đến, ngày, giờ, hãng bay) từ một email và lưu chúng theo cách có cấu trúc. Điều này cho phép truy vấn chính xác như "Tôi đã đặt chuyến bay nào đến Paris vào thứ Ba?"

## Triển khai và Lưu trữ Bộ nhớ

Triển khai bộ nhớ cho tác nhân AI bao gồm một quy trình có hệ thống của **quản lý bộ nhớ**, bao gồm tạo, lưu trữ, truy xuất, tích hợp, cập nhật, và thậm chí là "quên" (hoặc xóa) thông tin. Truy xuất là một khía cạnh đặc biệt quan trọng.

### Công cụ Bộ nhớ Chuyên dụng

#### Mem0

Một cách để lưu trữ và quản lý bộ nhớ tác nhân là sử dụng các công cụ chuyên dụng như Mem0. Mem0 hoạt động như một lớp bộ nhớ bền vững, cho phép tác nhân hồi tưởng các tương tác liên quan, lưu sở thích người dùng và ngữ cảnh thực tế, và học hỏi từ những thành công và thất bại theo thời gian. Ý tưởng ở đây là các tác nhân vô trạng trở thành có trạng thái.

Nó hoạt động thông qua **pipeline bộ nhớ hai giai đoạn: trích xuất và cập nhật**. Đầu tiên, các tin nhắn được thêm vào luồng của tác nhân được gửi đến dịch vụ Mem0, dịch vụ này sử dụng một Mô hình ngôn ngữ lớn (LLM) để tóm tắt lịch sử cuộc trò chuyện và trích xuất các ký ức mới. Sau đó, giai đoạn cập nhật do LLM điều khiển quyết định có nên thêm, sửa đổi hoặc xóa các ký ức này hay không, lưu chúng trong một kho dữ liệu lai có thể bao gồm cơ sở dữ liệu vector, đồ thị và key-value. Hệ thống này cũng hỗ trợ các loại bộ nhớ khác nhau và có thể tích hợp bộ nhớ đồ thị để quản lý mối quan hệ giữa các thực thể.

#### Cognee

Một phương pháp mạnh mẽ khác là sử dụng **Cognee**, một bộ nhớ ngữ nghĩa mã nguồn mở cho tác nhân AI biến dữ liệu có cấu trúc và không có cấu trúc thành các đồ thị tri thức có thể truy vấn được, được hỗ trợ bởi embeddings. Cognee cung cấp một **kiến trúc lưu trữ đôi** kết hợp tìm kiếm tương đồng vector với mối quan hệ đồ thị, cho phép tác nhân hiểu không chỉ thông tin nào là tương tự, mà còn là cách các khái niệm liên quan với nhau.

Nó xuất sắc ở **truy xuất lai** hòa trộn tương đồng vector, cấu trúc đồ thị, và lí giải của LLM - từ tra cứu đoạn thô đến trả lời câu hỏi nhận thức đồ thị. Hệ thống duy trì **bộ nhớ sống** phát triển và lớn dần trong khi vẫn có thể truy vấn như một đồ thị kết nối đơn, hỗ trợ cả ngữ cảnh phiên ngắn hạn và bộ nhớ lâu dài bền vững.

Notebook hướng dẫn Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) minh họa việc xây dựng lớp bộ nhớ hợp nhất này, với các ví dụ thực tế về nhập liệu từ nhiều nguồn dữ liệu khác nhau, trực quan hóa biểu đồ tri thức, và truy vấn với các chiến lược tìm kiếm khác nhau phục vụ nhu cầu cụ thể của tác nhân.

### Lưu trữ Bộ nhớ với RAG

Ngoài các công cụ bộ nhớ chuyên dụng như mem0 , bạn có thể tận dụng các dịch vụ tìm kiếm mạnh mẽ như **Azure AI Search làm backend để lưu trữ và truy xuất ký ức**, đặc biệt cho Structured RAG.

Điều này cho phép bạn định vị câu trả lời của tác nhân dựa trên dữ liệu của chính bạn, đảm bảo câu trả lời phù hợp và chính xác hơn. Azure AI Search có thể được sử dụng để lưu các ký ức du lịch cụ thể theo người dùng, danh mục sản phẩm, hoặc bất kỳ kiến thức chuyên môn nào khác.

Azure AI Search hỗ trợ các khả năng như **Structured RAG**, vốn xuất sắc trong việc trích xuất và truy xuất thông tin dày đặc, có cấu trúc từ các bộ dữ liệu lớn như lịch sử cuộc trò chuyện, email, hoặc thậm chí hình ảnh. Điều này cung cấp "độ chính xác và khả năng hồi tưởng siêu phàm" so với các phương pháp truyền thống phân đoạn văn bản và embedding.

## Làm cho Tác nhân AI Tự Cải thiện

Một mẫu phổ biến cho các tác nhân tự cải thiện bao gồm việc giới thiệu một **"tác nhân tri thức"**. Tác nhân tách biệt này quan sát cuộc trò chuyện chính giữa người dùng và tác nhân chính. Vai trò của nó là:

1. **Xác định thông tin có giá trị**: Quyết định phần nào của cuộc trò chuyện đáng được lưu như kiến thức chung hoặc sở thích cụ thể của người dùng.

2. **Trích xuất và tóm tắt**: Lấy cốt lõi học hỏi hoặc sở thích từ cuộc trò chuyện.

3. **Lưu vào cơ sở tri thức**: Lưu trữ thông tin trích xuất này, thường trong cơ sở dữ liệu vector, để có thể truy xuất sau này.

4. **Tăng cường truy vấn trong tương lai**: Khi người dùng khởi tạo truy vấn mới, tác nhân tri thức truy xuất thông tin đã lưu liên quan và thêm nó vào prompt của người dùng, cung cấp ngữ cảnh quan trọng cho tác nhân chính (tương tự như RAG).

### Tối ưu hóa cho Bộ nhớ

• **Quản lý Độ trễ**: Để tránh làm chậm tương tác người dùng, có thể sử dụng một mô hình rẻ hơn, nhanh hơn ban đầu để nhanh chóng kiểm tra xem thông tin có đáng lưu hay truy xuất hay không, chỉ gọi quá trình trích xuất/truy xuất phức tạp hơn khi cần.

• **Bảo trì Cơ sở tri thức**: Đối với cơ sở tri thức ngày càng lớn, thông tin ít được sử dụng hơn có thể được chuyển sang "lưu trữ lạnh" để quản lý chi phí.

## Còn Nhiều Câu hỏi về Bộ nhớ Tác nhân?

Tham gia [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) để gặp gỡ những người học khác, tham dự giờ làm việc và có câu hỏi về Tác nhân AI được trả lời.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Miễn trừ trách nhiệm:
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ gốc nên được coi là nguồn có thẩm quyền. Đối với thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp do con người thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ hiểu lầm hoặc giải thích sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->