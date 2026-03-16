# Sử dụng Các Giao thức Agentic (MCP, A2A và NLWeb)

[![Giao thức Agentic](../../../translated_images/vi/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Nhấp vào hình ảnh ở trên để xem video của bài học này)_

Khi việc sử dụng các đại lý AI tăng lên, nhu cầu về các giao thức đảm bảo tiêu chuẩn hóa, bảo mật và hỗ trợ đổi mới mở cũng tăng theo. Trong bài học này, chúng ta sẽ tìm hiểu 3 giao thức nhằm đáp ứng nhu cầu này - Model Context Protocol (MCP), Agent to Agent (A2A) và Natural Language Web (NLWeb).

## Giới thiệu

Trong bài học này, chúng ta sẽ đề cập đến:

• Cách **MCP** cho phép các Đại lý AI truy cập công cụ và dữ liệu bên ngoài để hoàn thành tác vụ của người dùng.

• Cách **A2A** cho phép giao tiếp và hợp tác giữa các đại lý AI khác nhau.

• Cách **NLWeb** mang giao diện ngôn ngữ tự nhiên đến bất kỳ trang web nào, cho phép các Đại lý AI khám phá và tương tác với nội dung.

## Mục tiêu học tập

• **Xác định** mục đích cốt lõi và lợi ích của MCP, A2A và NLWeb trong bối cảnh các đại lý AI.

• **Giải thích** cách mỗi giao thức tạo điều kiện cho giao tiếp và tương tác giữa LLM, công cụ và các đại lý khác.

• **Nhận biết** vai trò riêng biệt của mỗi giao thức trong việc xây dựng các hệ thống agentic phức tạp.

## Giao thức Ngữ cảnh Mô hình

Giao thức **Model Context Protocol (MCP)** là một tiêu chuẩn mở cung cấp một cách tiêu chuẩn hóa để ứng dụng cung cấp ngữ cảnh và công cụ cho các LLM. Điều này cho phép một "bộ điều hợp đa năng" tới các nguồn dữ liệu và công cụ khác nhau mà các Đại lý AI có thể kết nối theo một cách nhất quán.

Hãy xem các thành phần của MCP, lợi ích so với việc sử dụng API trực tiếp, và một ví dụ về cách các đại lý AI có thể sử dụng một máy chủ MCP.

### Thành phần cốt lõi của MCP

MCP hoạt động theo một **kiến trúc máy khách - máy chủ** và các thành phần cốt lõi là:

• **Hosts** là các ứng dụng LLM (ví dụ một trình soạn mã như VSCode) khởi tạo kết nối tới một Máy chủ MCP.

• **Clients** là các thành phần trong ứng dụng host duy trì các kết nối một-một với các máy chủ.

• **Servers** là các chương trình nhẹ cung cấp những khả năng cụ thể.

Trong giao thức có ba thành phần cơ bản là các khả năng của một Máy chủ MCP:

• **Tools**: Đây là các hành động hoặc chức năng rời rạc mà một đại lý AI có thể gọi để thực hiện một tác vụ. Ví dụ, một dịch vụ thời tiết có thể cung cấp một công cụ "lấy thời tiết", hoặc một máy chủ thương mại điện tử có thể cung cấp một công cụ "mua sản phẩm". Các máy chủ MCP quảng cáo tên, mô tả và sơ đồ đầu vào/đầu ra của từng công cụ trong danh sách khả năng của họ.

• **Resources**: Đây là các mục dữ liệu chỉ đọc hoặc tài liệu mà một máy chủ MCP có thể cung cấp, và client có thể truy xuất chúng theo yêu cầu. Ví dụ bao gồm nội dung tệp, bản ghi cơ sở dữ liệu, hoặc tệp nhật ký. Resources có thể là văn bản (như mã hoặc JSON) hoặc nhị phân (như hình ảnh hoặc PDF).

• **Prompts**: Đây là các mẫu được định nghĩa trước cung cấp các lệnh gợi ý, cho phép các luồng công việc phức tạp hơn.

### Lợi ích của MCP

MCP mang lại những lợi thế đáng kể cho các Đại lý AI:

• **Khám phá công cụ động**: Các đại lý có thể nhận danh sách công cụ có sẵn từ máy chủ một cách động cùng với mô tả về chức năng của chúng. Điều này trái ngược với các API truyền thống, vốn thường yêu cầu mã tĩnh để tích hợp, nghĩa là bất kỳ thay đổi API nào đều đòi hỏi cập nhật mã. MCP cung cấp cách tiếp cận "tích hợp một lần", dẫn đến khả năng thích ứng cao hơn.

• **Tương thích giữa các LLM**: MCP hoạt động trên nhiều LLM khác nhau, cung cấp sự linh hoạt để chuyển đổi mô hình lõi để đánh giá hiệu suất tốt hơn.

• **Bảo mật tiêu chuẩn hóa**: MCP bao gồm một phương thức xác thực tiêu chuẩn, cải thiện khả năng mở rộng khi thêm quyền truy cập vào các máy chủ MCP bổ sung. Điều này đơn giản hơn so với việc quản lý nhiều khóa và loại xác thực khác nhau cho các API truyền thống.

### Ví dụ về MCP

![Sơ đồ MCP](../../../translated_images/vi/mcp-diagram.e4ca1cbd551444a1.webp)

Hãy tưởng tượng một người dùng muốn đặt vé máy bay bằng trợ lý AI được hỗ trợ bởi MCP.

1. **Kết nối**: Trợ lý AI (client MCP) kết nối với một máy chủ MCP do hãng hàng không cung cấp.

2. **Khám phá công cụ**: Client hỏi máy chủ MCP của hãng hàng không, "Bạn có những công cụ nào?" Máy chủ trả lời với các công cụ như "tìm chuyến bay" và "đặt chuyến bay".

3. **Gọi công cụ**: Bạn sau đó yêu cầu trợ lý AI, "Vui lòng tìm chuyến bay từ Portland đến Honolulu." Trợ lý AI, sử dụng LLM của nó, xác định rằng cần gọi công cụ "tìm chuyến bay" và truyền các tham số liên quan (điểm khởi hành, điểm đến) tới máy chủ MCP.

4. **Thực thi và Phản hồi**: Máy chủ MCP, hoạt động như một lớp bọc, thực hiện cuộc gọi thực tế tới API đặt chỗ nội bộ của hãng hàng không. Sau đó nó nhận thông tin chuyến bay (ví dụ: dữ liệu JSON) và gửi trả lại cho trợ lý AI.

5. **Tương tác tiếp theo**: Trợ lý AI trình bày các tùy chọn chuyến bay. Khi bạn chọn một chuyến bay, trợ lý có thể gọi công cụ "đặt chuyến bay" trên cùng máy chủ MCP, hoàn tất việc đặt chỗ.

## Giao thức Agent-to-Agent (A2A)

Trong khi MCP tập trung vào việc kết nối LLM với công cụ, **Giao thức Agent-to-Agent (A2A)** tiến thêm một bước bằng cách cho phép giao tiếp và hợp tác giữa các đại lý AI khác nhau. A2A kết nối các đại lý AI giữa các tổ chức, môi trường và ngăn xếp công nghệ khác nhau để hoàn thành một nhiệm vụ chung.

Chúng ta sẽ xem xét các thành phần và lợi ích của A2A, cùng với một ví dụ về cách nó có thể được áp dụng trong ứng dụng du lịch của chúng ta.

### Thành phần cốt lõi của A2A

A2A tập trung vào việc cho phép giao tiếp giữa các đại lý và để họ làm việc cùng nhau nhằm hoàn thành một phần nhiệm vụ của người dùng. Mỗi thành phần của giao thức đóng góp vào điều này:

#### Thẻ Đại lý

Tương tự như cách một máy chủ MCP chia sẻ danh sách công cụ, một Thẻ Đại lý có:
- Tên của Đại lý.
- Một **mô tả về các nhiệm vụ tổng quát** mà nó thực hiện.
- Một **danh sách các kỹ năng cụ thể** với mô tả để giúp các đại lý khác (hoặc ngay cả người dùng) hiểu khi nào và vì sao họ muốn gọi đại lý đó.
- **URL Endpoint hiện tại** của đại lý
- **Phiên bản** và **khả năng** của đại lý như phản hồi dạng streaming và thông báo đẩy.

#### Trình thực thi Đại lý

Trình thực thi Đại lý chịu trách nhiệm **truyền ngữ cảnh của cuộc trò chuyện người dùng tới đại lý từ xa**, đại lý từ xa cần điều này để hiểu nhiệm vụ cần hoàn thành. Trong một máy chủ A2A, một đại lý sử dụng chính Large Language Model (LLM) của mình để phân tích các yêu cầu đến và thực hiện các nhiệm vụ bằng các công cụ nội bộ của nó.

#### Sản phẩm

Khi một đại lý từ xa hoàn thành nhiệm vụ được yêu cầu, sản phẩm công việc của nó được tạo thành một artifact. Một artifact **chứa kết quả công việc của đại lý**, một **mô tả những gì đã được hoàn thành**, và **ngữ cảnh văn bản** được gửi qua giao thức. Sau khi artifact được gửi, kết nối với đại lý từ xa được đóng cho đến khi cần lại.

#### Hàng đợi sự kiện

Thành phần này được sử dụng để **xử lý cập nhật và truyền tin nhắn**. Nó đặc biệt quan trọng trong môi trường sản xuất cho các hệ thống agentic để ngăn việc kết nối giữa các đại lý bị đóng trước khi nhiệm vụ hoàn thành, đặc biệt khi thời gian hoàn thành nhiệm vụ có thể kéo dài.

### Lợi ích của A2A

• **Hợp tác nâng cao**: Nó cho phép các đại lý từ các nhà cung cấp và nền tảng khác nhau tương tác, chia sẻ ngữ cảnh và làm việc cùng nhau, tạo điều kiện tự động hóa liền mạch giữa các hệ thống vốn trước đây bị ngắt kết nối.

• **Linh hoạt trong lựa chọn mô hình**: Mỗi đại lý A2A có thể quyết định sử dụng LLM nào để phục vụ các yêu cầu của mình, cho phép tối ưu hóa hoặc tinh chỉnh mô hình cho từng đại lý, khác với việc chỉ có một kết nối LLM trong một số kịch bản MCP.

• **Xác thực tích hợp sẵn**: Xác thực được tích hợp trực tiếp vào giao thức A2A, cung cấp một khung bảo mật vững chắc cho các tương tác giữa các đại lý.

### Ví dụ về A2A

![Sơ đồ A2A](../../../translated_images/vi/A2A-Diagram.8666928d648acc26.webp)

Hãy mở rộng kịch bản đặt du lịch của chúng ta, nhưng lần này sử dụng A2A.

1. **Yêu cầu người dùng tới hệ đa-đại lý**: Người dùng tương tác với một client/đại lý "Travel Agent" A2A, có thể bằng cách nói, "Hãy đặt toàn bộ chuyến đi tới Honolulu cho tuần tới, bao gồm vé máy bay, khách sạn và xe thuê."

2. **Điều phối bởi Đại lý Du lịch**: Đại lý Du lịch nhận yêu cầu phức tạp này. Nó sử dụng LLM của mình để suy luận về nhiệm vụ và xác định rằng nó cần tương tác với các đại lý chuyên môn hóa khác.

3. **Giao tiếp giữa các đại lý**: Đại lý Du lịch sau đó sử dụng giao thức A2A để kết nối với các đại lý hạ lưu, chẳng hạn như "Đại lý Hãng hàng không", "Đại lý Khách sạn" và "Đại lý Thuê xe" được tạo bởi các công ty khác nhau.

4. **Phân công thực hiện nhiệm vụ**: Đại lý Du lịch gửi các nhiệm vụ cụ thể cho các đại lý chuyên môn này (ví dụ, "Tìm chuyến bay đến Honolulu", "Đặt khách sạn", "Thuê xe"). Mỗi đại lý chuyên môn này, chạy LLM riêng và sử dụng các công cụ nội bộ của mình (có thể là các máy chủ MCP), thực hiện phần công việc riêng của mình cho việc đặt chỗ.

5. **Phản hồi tổng hợp**: Khi tất cả các đại lý hạ lưu hoàn thành nhiệm vụ, Đại lý Du lịch tổng hợp kết quả (chi tiết chuyến bay, xác nhận khách sạn, đặt xe) và gửi một phản hồi phong cách trò chuyện toàn diện trở lại cho người dùng.

## Web Ngôn ngữ Tự nhiên (NLWeb)

Các trang web từ lâu đã là cách chính để người dùng truy cập thông tin và dữ liệu trên Internet.

Hãy xem các thành phần khác nhau của NLWeb, lợi ích của NLWeb và một ví dụ về cách NLWeb của chúng ta hoạt động thông qua ứng dụng du lịch của chúng ta.

### Các thành phần của NLWeb

- **Ứng dụng NLWeb (Mã dịch vụ cốt lõi)**: Hệ thống xử lý các câu hỏi bằng ngôn ngữ tự nhiên. Nó kết nối các phần khác nhau của nền tảng để tạo phản hồi. Bạn có thể coi nó như **động cơ cung cấp các tính năng ngôn ngữ tự nhiên** cho một trang web.

- **Giao thức NLWeb**: Đây là một **tập hợp các quy tắc cơ bản cho tương tác ngôn ngữ tự nhiên** với một trang web. Nó trả về phản hồi ở định dạng JSON (thường sử dụng Schema.org). Mục đích của nó là tạo nền tảng đơn giản cho “AI Web”, tương tự như cách HTML làm cho việc chia sẻ tài liệu trực tuyến trở nên khả thi.

- **MCP Server (Endpoint của Model Context Protocol)**: Mỗi thiết lập NLWeb cũng hoạt động như một **máy chủ MCP**. Điều này có nghĩa là nó có thể **chia sẻ công cụ (như phương thức “ask”) và dữ liệu** với các hệ thống AI khác. Trong thực tế, điều này làm cho nội dung và khả năng của trang web có thể được các đại lý AI sử dụng, cho phép trang web trở thành một phần của “hệ sinh thái đại lý” rộng lớn hơn.

- **Mô hình nhúng (Embedding Models)**: Các mô hình này được dùng để **chuyển nội dung trang web thành các biểu diễn số gọi là vector** (embeddings). Những vector này nắm bắt ý nghĩa theo cách máy tính có thể so sánh và tìm kiếm. Chúng được lưu trữ trong một cơ sở dữ liệu đặc biệt, và người dùng có thể chọn mô hình embedding mà họ muốn sử dụng.

- **Cơ sở dữ liệu vector (Cơ chế truy xuất)**: Cơ sở dữ liệu này **lưu trữ các vector nhúng của nội dung trang web**. Khi ai đó đặt câu hỏi, NLWeb kiểm tra cơ sở dữ liệu vector để nhanh chóng tìm thông tin phù hợp nhất. Nó cung cấp một danh sách các câu trả lời tiềm năng được xếp hạng theo độ tương đồng. NLWeb làm việc với các hệ thống lưu trữ vector khác nhau như Qdrant, Snowflake, Milvus, Azure AI Search và Elasticsearch.

### Ví dụ về NLWeb

![NLWeb](../../../translated_images/vi/nlweb-diagram.c1e2390b310e5fe4.webp)

Xét lại trang web đặt du lịch của chúng ta, nhưng lần này nó được hỗ trợ bởi NLWeb.

1. **Nhập dữ liệu**: Các danh mục sản phẩm hiện có của trang web du lịch (ví dụ: danh sách chuyến bay, mô tả khách sạn, gói tour) được định dạng bằng Schema.org hoặc tải qua nguồn RSS. Công cụ của NLWeb nhập dữ liệu có cấu trúc này, tạo embeddings và lưu chúng vào cơ sở dữ liệu vector cục bộ hoặc từ xa.

2. **Truy vấn bằng ngôn ngữ tự nhiên (con người)**: Người dùng truy cập trang web và, thay vì duyệt menu, nhập vào giao diện trò chuyện: "Tìm cho tôi một khách sạn phù hợp cho gia đình ở Honolulu có hồ bơi cho tuần tới".

3. **Xử lý bởi NLWeb**: Ứng dụng NLWeb nhận truy vấn này. Nó gửi truy vấn tới một LLM để hiểu và đồng thời tìm kiếm cơ sở dữ liệu vector để tìm danh sách khách sạn liên quan.

4. **Kết quả chính xác**: LLM giúp diễn giải kết quả tìm kiếm từ cơ sở dữ liệu, xác định những kết quả phù hợp nhất dựa trên các tiêu chí "phù hợp cho gia đình", "có hồ bơi" và "Honolulu", rồi sau đó định dạng một phản hồi bằng ngôn ngữ tự nhiên. Quan trọng là phản hồi tham chiếu đến các khách sạn thực tế từ danh mục trang web, tránh thông tin bịa đặt.

5. **Tương tác với Đại lý AI**: Vì NLWeb hoạt động như một máy chủ MCP, một đại lý du lịch AI bên ngoài cũng có thể kết nối tới phiên bản NLWeb của trang web này. Đại lý AI sau đó có thể sử dụng phương thức `ask` của MCP để truy vấn trực tiếp trang web: `ask("Có nhà hàng thân thiện với người ăn chay ở khu vực Honolulu được khách sạn giới thiệu không?")`. Phiên bản NLWeb sẽ xử lý điều này, tận dụng cơ sở dữ liệu thông tin nhà hàng của nó (nếu đã được nạp), và trả về một phản hồi JSON có cấu trúc.

### Còn câu hỏi nào về MCP/A2A/NLWeb không?

Tham gia [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) để gặp những người học khác, tham dự giờ tư vấn và nhận câu trả lời cho các câu hỏi về Đại lý AI của bạn.

## Tài nguyên

- [MCP for Beginners](https://aka.ms/mcp-for-beginners)  
- [MCP Documentation](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb Repo](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel Guides](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Miễn trừ trách nhiệm:
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc sai sót. Văn bản gốc bằng ngôn ngữ gốc nên được coi là nguồn có thẩm quyền. Đối với các thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp do con người thực hiện. Chúng tôi không chịu trách nhiệm đối với bất kỳ sự hiểu nhầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->