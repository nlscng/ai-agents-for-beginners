[![Giới thiệu về tác nhân AI](../../../translated_images/vi/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Nhấp vào hình ảnh ở trên để xem video của bài học này)_


# Giới thiệu về Tác nhân AI và Các Trường hợp Sử dụng Tác nhân

Chào mừng bạn đến với khóa học "AI Agents for Beginners"! Khóa học này cung cấp kiến thức cơ bản và các ví dụ áp dụng để xây dựng Tác nhân AI.

Tham gia <a href="https://discord.gg/kzRShWzttr" target="_blank">Cộng đồng Azure AI trên Discord</a> để gặp gỡ những người học khác và các Nhà xây dựng Tác nhân AI, cũng như đặt bất kỳ câu hỏi nào bạn có về khóa học này.

Để bắt đầu khóa học này, chúng ta sẽ tìm hiểu rõ hơn Tác nhân AI là gì và cách chúng ta có thể sử dụng chúng trong các ứng dụng và quy trình làm việc mà chúng ta xây dựng.

## Giới thiệu

Bài học này bao gồm:

- Tác nhân AI là gì và có những loại tác nhân nào?
- Những trường hợp sử dụng nào phù hợp nhất với Tác nhân AI và chúng có thể giúp chúng ta như thế nào?
- Một số thành phần cơ bản khi thiết kế Giải pháp theo hướng tác nhân là gì?

## Mục tiêu học tập
Sau khi hoàn thành bài học này, bạn sẽ có thể:

- Hiểu các khái niệm về Tác nhân AI và cách chúng khác với các giải pháp AI khác.
- Áp dụng Tác nhân AI một cách hiệu quả nhất.
- Thiết kế các giải pháp theo hướng tác nhân một cách hiệu suất cho cả người dùng và khách hàng.

## Định nghĩa Tác nhân AI và Các loại Tác nhân AI

### Tác nhân AI là gì?

Tác nhân AI là **hệ thống** cho phép **Mô hình Ngôn ngữ Lớn (LLMs)** **thực hiện hành động** bằng cách mở rộng khả năng của chúng bằng cách cho LLMs **truy cập vào công cụ** và **kiến thức**.

Hãy phân tách định nghĩa này thành các phần nhỏ hơn:

- **Hệ thống** - Điều quan trọng là nghĩ về tác nhân không chỉ là một thành phần đơn lẻ mà là một hệ thống gồm nhiều thành phần. Ở mức cơ bản, các thành phần của một Tác nhân AI là:
  - **Môi trường** - Không gian được xác định nơi Tác nhân AI hoạt động. Ví dụ, nếu chúng ta có một tác nhân đặt vé du lịch, môi trường có thể là hệ thống đặt vé du lịch mà Tác nhân AI sử dụng để hoàn thành nhiệm vụ.
  - **Cảm biến** - Môi trường có thông tin và cung cấp phản hồi. Tác nhân AI sử dụng cảm biến để thu thập và diễn giải thông tin này về trạng thái hiện tại của môi trường. Trong ví dụ Tác nhân đặt vé du lịch, hệ thống đặt vé có thể cung cấp thông tin như tình trạng sẵn có của khách sạn hoặc giá vé máy bay.
  - **Bộ tác động** - Khi Tác nhân AI nhận được trạng thái hiện tại của môi trường, đối với nhiệm vụ hiện tại, tác nhân xác định hành động cần thực hiện để thay đổi môi trường. Đối với tác nhân đặt vé du lịch, đó có thể là đặt một phòng trống cho người dùng.

![Tác nhân AI là gì?](../../../translated_images/vi/what-are-ai-agents.1ec8c4d548af601a.webp)

**Mô hình Ngôn ngữ Lớn** - Khái niệm về tác nhân đã tồn tại trước khi xuất hiện các LLMs. Lợi thế của việc xây dựng Tác nhân AI với LLMs là khả năng diễn giải ngôn ngữ con người và dữ liệu của chúng. Khả năng này cho phép LLMs diễn giải thông tin môi trường và xác định một kế hoạch để thay đổi môi trường.

**Thực hiện hành động** - Bên ngoài hệ thống Tác nhân AI, LLMs bị giới hạn ở các tình huống mà hành động là tạo nội dung hoặc thông tin dựa trên lời nhắc của người dùng. Bên trong hệ thống Tác nhân AI, LLMs có thể hoàn thành các nhiệm vụ bằng cách diễn giải yêu cầu của người dùng và sử dụng các công cụ có sẵn trong môi trường của chúng.

**Truy cập công cụ** - Công cụ mà LLM có thể truy cập được xác định bởi 1) môi trường nó đang hoạt động và 2) nhà phát triển của Tác nhân AI. Trong ví dụ tác nhân du lịch của chúng ta, các công cụ của tác nhân bị giới hạn bởi những thao tác có sẵn trong hệ thống đặt vé, và/hoặc nhà phát triển có thể giới hạn quyền truy cập công cụ của tác nhân vào các chuyến bay.

**Bộ nhớ + Kiến thức** - Bộ nhớ có thể là ngắn hạn trong bối cảnh cuộc trò chuyện giữa người dùng và tác nhân. Về dài hạn, ngoài thông tin do môi trường cung cấp, Tác nhân AI cũng có thể truy xuất kiến thức từ các hệ thống, dịch vụ, công cụ khác và thậm chí từ các tác nhân khác. Trong ví dụ tác nhân du lịch, kiến thức này có thể là thông tin về sở thích du lịch của người dùng được lưu trong cơ sở dữ liệu khách hàng.

### Các loại tác nhân khác nhau

Bây giờ chúng ta đã có định nghĩa chung về Tác nhân AI, hãy xem một số loại tác nhân cụ thể và cách chúng sẽ được áp dụng cho tác nhân đặt vé du lịch.

| **Loại Tác nhân**                | **Mô tả**                                                                                                                       | **Ví dụ**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Tác nhân Phản xạ Đơn giản**      | Thực hiện hành động ngay lập tức dựa trên các quy tắc định trước.                                                                                  | Tác nhân du lịch diễn giải ngữ cảnh của email và chuyển các khiếu nại về chuyến đi tới bộ phận dịch vụ khách hàng.                                                                                                                          |
| **Tác nhân Phản xạ Dựa trên Mô hình** | Thực hiện hành động dựa trên một mô hình về thế giới và các thay đổi trong mô hình đó.                                                              | Tác nhân du lịch ưu tiên các tuyến đường có biến động giá đáng kể dựa trên quyền truy cập vào dữ liệu giá lịch sử.                                                                                                             |
| **Tác nhân Hướng tới Mục tiêu**         | Tạo kế hoạch để đạt được các mục tiêu cụ thể bằng cách diễn giải mục tiêu và xác định các hành động để đạt được nó.                                  | Tác nhân du lịch đặt một hành trình bằng cách xác định các sắp xếp cần thiết (xe hơi, phương tiện công cộng, chuyến bay) từ vị trí hiện tại đến điểm đến.                                                                                |
| **Tác nhân Dựa trên Tiện ích**      | Xem xét sở thích và cân nhắc đánh đổi theo số để xác định cách đạt được mục tiêu.                                               | Tác nhân du lịch tối đa hóa tiện ích bằng cách cân nhắc giữa tiện lợi và chi phí khi đặt chuyến đi.                                                                                                                                          |
| **Tác nhân Học hỏi**           | Cải thiện theo thời gian bằng cách phản hồi ý kiến và điều chỉnh hành động tương ứng.                                                        | Tác nhân du lịch cải thiện bằng cách sử dụng phản hồi của khách hàng từ các khảo sát sau chuyến đi để điều chỉnh các đặt chỗ trong tương lai.                                                                                                               |
| **Tác nhân Phân cấp**       | Có nhiều tác nhân trong một hệ thống phân tầng, trong đó các tác nhân cấp cao phân chia nhiệm vụ thành các nhiệm vụ con để các tác nhân cấp thấp hoàn thành. | Tác nhân du lịch hủy một chuyến đi bằng cách chia nhiệm vụ thành các nhiệm vụ con (ví dụ, hủy các đặt chỗ cụ thể) và để các tác nhân cấp thấp hoàn thành chúng, báo cáo lại cho tác nhân cấp cao.                                     |
| **Hệ thống Nhiều Tác nhân (MAS)** | Các tác nhân hoàn thành nhiệm vụ một cách độc lập, có thể hợp tác hoặc cạnh tranh.                                                           | Hợp tác: Nhiều tác nhân đặt các dịch vụ du lịch cụ thể như khách sạn, chuyến bay và giải trí. Cạnh tranh: Nhiều tác nhân quản lý và cạnh tranh trên một lịch đặt phòng khách sạn chung để đặt khách vào khách sạn. |

## Khi nào nên sử dụng Tác nhân AI

Trong phần trước, chúng ta đã sử dụng trường hợp sử dụng Tác nhân du lịch để giải thích cách các loại tác nhân khác nhau có thể được sử dụng trong các kịch bản đặt vé du lịch khác nhau. Chúng ta sẽ tiếp tục sử dụng ứng dụng này xuyên suốt khóa học.

Hãy xem các loại trường hợp sử dụng mà Tác nhân AI phù hợp nhất:

![Khi nào nên sử dụng Tác nhân AI?](../../../translated_images/vi/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Vấn đề Mở** - cho phép LLM xác định các bước cần thiết để hoàn thành một nhiệm vụ vì chúng không phải lúc nào cũng có thể được mã hóa cứng vào một quy trình.
- **Quy trình Nhiều Bước** - các nhiệm vụ yêu cầu một mức độ phức tạp trong đó Tác nhân AI cần sử dụng công cụ hoặc thông tin qua nhiều lượt thay vì chỉ truy xuất một lần.  
- **Cải thiện Qua Thời gian** - các nhiệm vụ trong đó tác nhân có thể cải thiện theo thời gian bằng cách nhận phản hồi từ môi trường hoặc người dùng để cung cấp tiện ích tốt hơn.

Chúng tôi đề cập nhiều hơn các cân nhắc khi sử dụng Tác nhân AI trong bài học Xây dựng Tác nhân AI Đáng tin cậy.

## Những điều cơ bản về Giải pháp theo hướng Tác nhân

### Phát triển Tác nhân

Bước đầu tiên trong thiết kế hệ thống Tác nhân AI là xác định các công cụ, hành động và hành vi. Trong khóa học này, chúng tôi tập trung vào việc sử dụng Azure AI Agent Service để định nghĩa Tác nhân. Dịch vụ này cung cấp các tính năng như:

- Lựa chọn các Mô hình mở như OpenAI, Mistral, và Llama
- Sử dụng Dữ liệu được cấp phép thông qua các nhà cung cấp như Tripadvisor
- Sử dụng các công cụ chuẩn hóa OpenAPI 3.0

### Các Mẫu theo hướng Tác nhân

Giao tiếp với LLMs thông qua các lời nhắc. Với tính bán tự chủ của Tác nhân AI, không phải lúc nào cũng có thể hoặc cần thiết phải gửi lại lời nhắc cho LLM sau khi có thay đổi trong môi trường. Chúng tôi sử dụng **Các Mẫu theo hướng Tác nhân** cho phép chúng ta nhắc LLM qua nhiều bước theo cách dễ mở rộng hơn.

Khóa học này được chia thành một số mẫu theo hướng tác nhân đang phổ biến hiện nay.

### Các Khung theo hướng Tác nhân

Các Khung theo hướng Tác nhân cho phép nhà phát triển triển khai các mẫu theo hướng tác nhân thông qua mã. Những khung này cung cấp các mẫu, plugin và công cụ để sự hợp tác giữa các Tác nhân AI được tốt hơn. Những lợi ích này cung cấp khả năng quan sát và khắc phục sự cố tốt hơn cho hệ thống Tác nhân AI.

Trong khóa học này, chúng ta sẽ khám phá khung nghiên cứu AutoGen và khung sẵn sàng cho sản xuất Agent từ Semantic Kernel.

## Mã mẫu

- Python: [Khung tác nhân](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Khung tác nhân](./code_samples/01-dotnet-agent-framework.md)

## Còn thắc mắc gì về Tác nhân AI?

Tham gia [Microsoft Foundry trên Discord](https://aka.ms/ai-agents/discord) để gặp gỡ những người học khác, tham dự giờ làm việc và nhận câu trả lời cho các câu hỏi về Tác nhân AI của bạn.

## Bài học trước

[Thiết lập Khóa học](../00-course-setup/README.md)

## Bài học tiếp theo

[Khám phá các Khung theo hướng Tác nhân](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Miễn trừ trách nhiệm:
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI Co-op Translator (https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc thông tin không chính xác. Tài liệu gốc bằng ngôn ngữ gốc nên được coi là nguồn có thẩm quyền. Đối với các thông tin quan trọng, khuyến nghị sử dụng bản dịch chuyên nghiệp do người dịch thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->