# Tác nhân AI trong Sản xuất: Khả năng quan sát & Đánh giá

[![Tác nhân AI trong Sản xuất](../../../translated_images/vi/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

Khi các tác nhân AI chuyển từ nguyên mẫu thí nghiệm sang ứng dụng thực tế, khả năng hiểu hành vi của chúng, giám sát hiệu suất và hệ thống hóa việc đánh giá đầu ra trở nên rất quan trọng.

## Mục tiêu học tập

Sau khi hoàn thành bài học này, bạn sẽ biết cách/hiểu:
- Các khái niệm cốt lõi về khả năng quan sát và đánh giá tác nhân
- Kỹ thuật cải thiện hiệu suất, chi phí và hiệu quả của các tác nhân
- Cái gì và cách nào để đánh giá các tác nhân AI một cách hệ thống
- Cách kiểm soát chi phí khi triển khai tác nhân AI vào sản xuất
- Cách chèn đo lường (instrument) cho các tác nhân xây dựng bằng AutoGen

Mục tiêu là trang bị cho bạn kiến thức để biến các tác nhân "hộp đen" thành các hệ thống minh bạch, dễ quản lý và đáng tin cậy.

_**Lưu ý:** Việc triển khai các Tác nhân AI an toàn và đáng tin cậy là rất quan trọng. Hãy xem thêm bài học [Building Trustworthy AI Agents](./06-building-trustworthy-agents/README.md)._

## Traces and Spans

Các công cụ quan sát như [Langfuse](https://langfuse.com/) hoặc [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) thường biểu diễn các lần chạy tác nhân dưới dạng traces và spans.

- **Trace** đại diện cho một nhiệm vụ tác nhân hoàn chỉnh từ đầu đến cuối (như xử lý một truy vấn của người dùng).
- **Spans** là các bước riêng lẻ trong trace (như gọi một mô hình ngôn ngữ hoặc truy xuất dữ liệu).

![Cây trace trong Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Nếu không có khả năng quan sát, một tác nhân AI có thể cảm thấy như một "hộp đen" - trạng thái nội bộ và lập luận bên trong của nó là mờ, làm cho việc chẩn đoán sự cố hoặc tối ưu hóa hiệu suất trở nên khó khăn. Với khả năng quan sát, các tác nhân trở thành "hộp kính", cung cấp sự minh bạch thiết yếu để xây dựng niềm tin và đảm bảo chúng hoạt động như mong đợi.

## Tại sao khả năng quan sát lại quan trọng trong môi trường sản xuất

Việc chuyển các tác nhân AI vào môi trường sản xuất đem theo một tập hợp thách thức và yêu cầu mới. Khả năng quan sát không còn là thứ "tốt để có" mà là một năng lực thiết yếu:

*   **Gỡ lỗi và Phân tích nguyên nhân gốc rễ:** Khi một tác nhân thất bại hoặc đưa ra đầu ra không mong đợi, các công cụ quan sát cung cấp các trace cần thiết để xác định nguồn gốc của lỗi. Điều này đặc biệt quan trọng trong các tác nhân phức tạp có thể bao gồm nhiều lần gọi LLM, tương tác công cụ và logic có điều kiện.
*   **Quản lý Độ trễ và Chi phí:** Các tác nhân AI thường phụ thuộc vào LLM và các API bên ngoài được tính phí theo token hoặc theo lần gọi. Khả năng quan sát cho phép theo dõi chính xác các cuộc gọi này, giúp xác định các hoạt động chậm hoặc tốn kém quá mức. Điều này cho phép các nhóm tối ưu hóa prompt, chọn mô hình hiệu quả hơn hoặc thiết kế lại luồng công việc để quản lý chi phí vận hành và đảm bảo trải nghiệm người dùng tốt.
*   **Niềm tin, An toàn và Tuân thủ:** Trong nhiều ứng dụng, việc đảm bảo tác nhân hành xử an toàn và có đạo đức là rất quan trọng. Khả năng quan sát cung cấp một đường dẫn kiểm toán các hành động và quyết định của tác nhân. Điều này có thể được dùng để phát hiện và giảm thiểu các vấn đề như prompt injection, tạo nội dung có hại, hoặc xử lý sai thông tin nhận dạng cá nhân (PII). Ví dụ, bạn có thể xem lại các trace để hiểu tại sao một tác nhân đưa ra phản hồi nhất định hoặc sử dụng một công cụ cụ thể.
*   **Vòng lặp Cải tiến Liên tục:** Dữ liệu quan sát là nền tảng của quy trình phát triển lặp lại. Bằng cách giám sát cách các tác nhân hoạt động trong thế giới thực, các nhóm có thể xác định điểm cần cải thiện, thu thập dữ liệu để tinh chỉnh mô hình, và xác thực tác động của các thay đổi. Điều này tạo ra một vòng phản hồi nơi các hiểu biết từ đánh giá trực tuyến chuyển thành thí nghiệm ngoại tuyến và hoàn thiện, dẫn đến hiệu suất tác nhân ngày càng tốt hơn.

## Các chỉ số chính cần theo dõi

Để theo dõi và hiểu hành vi của tác nhân, cần theo dõi một loạt chỉ số và tín hiệu. Mặc dù các chỉ số cụ thể có thể khác nhau tùy mục đích của tác nhân, một số là quan trọng phổ quát.

Dưới đây là một số chỉ số phổ biến mà các công cụ quan sát theo dõi:

**Độ trễ (Latency):** Tác nhân phản hồi nhanh như thế nào? Thời gian chờ lâu làm ảnh hưởng tiêu cực tới trải nghiệm người dùng. Bạn nên đo độ trễ cho các tác vụ và các bước riêng lẻ bằng cách trace các lần chạy tác nhân. Ví dụ, một tác nhân mất 20 giây cho tất cả các lần gọi mô hình có thể được tăng tốc bằng cách sử dụng mô hình nhanh hơn hoặc chạy các lần gọi mô hình song song.

**Chi phí:** Chi phí cho mỗi lần chạy tác nhân là bao nhiêu? Các tác nhân AI phụ thuộc vào các lần gọi LLM được tính phí theo token hoặc API bên ngoài. Việc sử dụng công cụ thường xuyên hoặc nhiều prompt có thể nhanh chóng làm tăng chi phí. Ví dụ, nếu một tác nhân gọi LLM năm lần để cải thiện chất lượng ít ỏi, bạn phải đánh giá xem chi phí có xứng đáng hay không hoặc liệu có thể giảm số lần gọi hoặc dùng mô hình rẻ hơn. Giám sát thời gian thực cũng có thể giúp phát hiện các đột biến bất ngờ (ví dụ: lỗi gây vòng lặp API quá mức).

**Lỗi Yêu cầu (Request Errors):** Có bao nhiêu yêu cầu mà tác nhân thất bại? Điều này có thể bao gồm lỗi API hoặc các cuộc gọi công cụ thất bại. Để làm cho tác nhân bền bỉ hơn trước những lỗi này trong môi trường sản xuất, bạn có thể thiết lập fallback hoặc thử lại. Ví dụ: nếu nhà cung cấp LLM A bị sập, bạn chuyển sang nhà cung cấp LLM B làm dự phòng.

**Phản hồi Người dùng:** Thực hiện đánh giá trực tiếp từ người dùng cung cấp cái nhìn quý giá. Điều này có thể bao gồm đánh giá rõ ràng (👍thích/👎không thích, ⭐1-5 sao) hoặc bình luận dạng văn bản. Phản hồi tiêu cực liên tục nên cảnh báo bạn vì đây là dấu hiệu rằng tác nhân không hoạt động như mong đợi.

**Phản hồi Người dùng Ngầm (Implicit User Feedback):** Hành vi người dùng cung cấp phản hồi gián tiếp ngay cả khi không có xếp hạng rõ ràng. Điều này có thể bao gồm việc sửa câu hỏi ngay lập tức, gửi lại truy vấn hoặc nhấp nút thử lại. Ví dụ: nếu bạn thấy người dùng lặp lại hỏi cùng một câu, đó là dấu hiệu tác nhân không hoạt động như mong đợi.

**Độ chính xác (Accuracy):** Tần suất tác nhân tạo ra đầu ra đúng hoặc mong muốn là bao nhiêu? Định nghĩa độ chính xác thay đổi (ví dụ: độ đúng trong giải quyết vấn đề, độ chính xác truy xuất thông tin, sự hài lòng của người dùng). Bước đầu tiên là xác định thành công trông như thế nào cho tác nhân của bạn. Bạn có thể theo dõi độ chính xác qua kiểm tra tự động, điểm đánh giá, hoặc nhãn hoàn thành tác vụ. Ví dụ, đánh dấu các trace là "succeeded" hoặc "failed".

**Các chỉ số Đánh giá Tự động:** Bạn cũng có thể thiết lập các đánh giá tự động. Ví dụ, bạn có thể dùng một LLM để chấm đầu ra của tác nhân, ví dụ xem nó có hữu ích, chính xác hay không. Cũng có một số thư viện mã nguồn mở giúp bạn chấm các khía cạnh khác nhau của tác nhân. Ví dụ [RAGAS](https://docs.ragas.io/) cho các tác nhân RAG hoặc [LLM Guard](https://llm-guard.com/) để phát hiện ngôn ngữ có hại hoặc prompt injection.

Trong thực tế, kết hợp các chỉ số này sẽ cung cấp bao phủ tốt nhất cho sức khỏe của một tác nhân AI. Trong [notebook ví dụ](./code_samples/10_autogen_evaluation.ipynb) của chương này, chúng tôi sẽ cho bạn thấy các chỉ số này trông như thế nào trong các ví dụ thực tế nhưng trước tiên, chúng ta sẽ tìm hiểu quy trình đánh giá điển hình trông như thế nào.

## Ghi nhận hoạt động cho Agent của bạn

Để thu thập dữ liệu tracing, bạn sẽ cần ghi nhận hoạt động trong mã của mình. Mục tiêu là chèn đo lường vào mã tác nhân để phát ra các trace và chỉ số có thể được nền tảng quan sát thu thập, xử lý và trực quan hóa.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) đã nổi lên như một tiêu chuẩn công nghiệp cho khả năng quan sát LLM. Nó cung cấp một tập các API, SDK và công cụ để sinh, thu thập và xuất dữ liệu telemety.

Có nhiều thư viện instrumentation bọc các framework tác nhân hiện có và làm cho việc xuất OpenTelemetry spans đến một công cụ quan sát trở nên dễ dàng. Dưới đây là một ví dụ về chèn instrumentation cho một tác nhân AutoGen với thư viện [OpenLit instrumentation library](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

Bản [notebook ví dụ](./code_samples/10_autogen_evaluation.ipynb) trong chương này sẽ minh họa cách chèn đo lường cho tác nhân AutoGen của bạn.

**Tạo Span Thủ công:** Trong khi các thư viện instrumentation cung cấp nền tảng tốt, thường có những trường hợp cần thông tin chi tiết hoặc tùy chỉnh hơn. Bạn có thể tạo span thủ công để thêm logic ứng dụng tuỳ chỉnh. Quan trọng hơn, bạn có thể làm giàu các span được tạo tự động hoặc thủ công bằng các thuộc tính tùy chỉnh (còn gọi là tag hoặc metadata). Những thuộc tính này có thể bao gồm dữ liệu đặc thù doanh nghiệp, các tính toán trung gian, hoặc bất kỳ ngữ cảnh nào hữu ích cho việc gỡ lỗi hoặc phân tích, chẳng hạn như `user_id`, `session_id`, hoặc `model_version`.

Ví dụ về việc tạo traces và spans thủ công với [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3):

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Đánh giá Agent

Khả năng quan sát cung cấp cho chúng ta các chỉ số, nhưng đánh giá là quá trình phân tích dữ liệu đó (và thực hiện các bài kiểm tra) để xác định mức độ một tác nhân AI đang hoạt động tốt và cách nó có thể được cải thiện. Nói cách khác, một khi bạn có những trace và chỉ số đó, bạn sử dụng chúng như thế nào để đánh giá tác nhân và đưa ra quyết định?

Việc đánh giá đều đặn là quan trọng vì các tác nhân AI thường không định trước và có thể tiến hóa (thông qua cập nhật hoặc trôi hành vi mô hình) – nếu không có đánh giá, bạn sẽ không biết liệu “tác nhân thông minh” của mình có thực sự làm tốt công việc hay không hoặc liệu nó có bị suy giảm.

Có hai loại đánh giá cho các tác nhân AI: **đánh giá trực tuyến** và **đánh giá ngoại tuyến**. Cả hai đều có giá trị và bổ trợ cho nhau. Chúng ta thường bắt đầu với đánh giá ngoại tuyến, vì đây là bước tối thiểu cần thiết trước khi triển khai bất kỳ tác nhân nào.

### Đánh giá ngoại tuyến

![Các mục dữ liệu trong Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

Điều này liên quan đến việc đánh giá tác nhân trong môi trường được kiểm soát, thường sử dụng các bộ dữ liệu kiểm thử, không phải truy vấn người dùng trực tiếp. Bạn sử dụng các bộ dữ liệu có tuyển chọn nơi bạn biết đầu ra mong đợi hoặc hành vi đúng, sau đó chạy tác nhân trên chúng.

Chẳng hạn, nếu bạn xây dựng một tác nhân giải bài toán đố toán, bạn có thể có một [bộ dữ liệu kiểm thử](https://huggingface.co/datasets/gsm8k) gồm 100 bài toán có đáp án biết trước. Đánh giá ngoại tuyến thường được thực hiện trong quá trình phát triển (và có thể là một phần của pipeline CI/CD) để kiểm tra cải tiến hoặc ngăn ngừa suy giảm. Lợi ích là nó **có thể lặp lại và bạn có thể có các chỉ số độ chính xác rõ ràng vì bạn có ground truth**. Bạn cũng có thể mô phỏng các truy vấn người dùng và đo phản hồi của tác nhân so với các đáp án lý tưởng hoặc sử dụng các chỉ số tự động như mô tả ở trên.

Thách thức chính với đánh giá ngoại tuyến là đảm bảo bộ dữ liệu kiểm thử của bạn toàn diện và luôn phù hợp – tác nhân có thể hoạt động tốt trên một bộ kiểm thử cố định nhưng gặp các truy vấn rất khác trong sản xuất. Do đó, bạn nên cập nhật bộ kiểm thử với các trường hợp biên và ví dụ mới phản ánh kịch bản thực tế. Một sự kết hợp giữa các trường hợp "kiểm tra nhanh" nhỏ và các bộ đánh giá lớn hơn là hữu ích: bộ nhỏ để kiểm tra nhanh và bộ lớn hơn để có các chỉ số hiệu suất rộng hơn.

### Đánh giá trực tuyến

![Tổng quan các chỉ số quan sát](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Điều này đề cập đến việc đánh giá tác nhân trong môi trường trực tiếp, thực tế, tức là trong quá trình sử dụng thực tế ở sản xuất. Đánh giá trực tuyến bao gồm giám sát hiệu suất của tác nhân trên tương tác người dùng thực và phân tích kết quả liên tục.

Ví dụ, bạn có thể theo dõi tỷ lệ thành công, điểm hài lòng của người dùng, hoặc các chỉ số khác trên lưu lượng trực tiếp. Ưu điểm của đánh giá trực tuyến là nó **bắt được những điều bạn có thể không lường trước trong phòng thí nghiệm** – bạn có thể quan sát trôi mô hình theo thời gian (nếu hiệu quả của tác nhân giảm khi mẫu đầu vào thay đổi) và phát hiện các truy vấn hoặc tình huống bất ngờ không có trong dữ liệu kiểm thử của bạn. Nó cung cấp một bức tranh thực sự về cách tác nhân hành xử ngoài đời thực.

Đánh giá trực tuyến thường bao gồm việc thu thập phản hồi người dùng ngầm và rõ ràng, như đã thảo luận, và có thể chạy thử nghiệm shadow hoặc A/B (nơi phiên bản mới của tác nhân chạy song song để so sánh với phiên bản cũ). Thách thức là có thể khó có được nhãn hoặc điểm số đáng tin cậy cho các tương tác trực tiếp – bạn có thể phải dựa vào phản hồi người dùng hoặc các chỉ số hạ nguồn (ví dụ người dùng có nhấp kết quả hay không).

### Kết hợp cả hai

Đánh giá trực tuyến và ngoại tuyến không loại trừ lẫn nhau; chúng bổ trợ rất tốt cho nhau. Những hiểu biết từ giám sát trực tuyến (ví dụ, các loại truy vấn người dùng mới mà tác nhân xử lý kém) có thể được dùng để bổ sung và cải thiện bộ dữ liệu kiểm thử ngoại tuyến. Ngược lại, các tác nhân hoạt động tốt trong kiểm thử ngoại tuyến có thể được triển khai và giám sát trực tuyến với độ tin cậy cao hơn.

Thực tế, nhiều nhóm áp dụng một vòng:

_đánh giá ngoại tuyến -> triển khai -> giám sát trực tuyến -> thu thập các trường hợp lỗi mới -> thêm vào bộ dữ liệu ngoại tuyến -> tinh chỉnh agent -> lặp lại_.

## Các vấn đề thường gặp

Khi bạn triển khai các tác nhân AI vào sản xuất, bạn có thể gặp nhiều thách thức khác nhau. Dưới đây là một số vấn đề phổ biến và các giải pháp khả thi:

| **Vấn đề**    | **Giải pháp tiềm năng**   |
| ------------- | ------------------ |
| Tác nhân AI không thực hiện nhiệm vụ một cách nhất quán | - Tinh chỉnh prompt đưa cho Tác nhân AI; làm rõ mục tiêu.<br>- Xác định nơi có thể chia nhiệm vụ thành các nhiệm vụ con và xử lý bởi nhiều tác nhân để cải thiện. |
| Tác nhân AI rơi vào vòng lặp liên tục  | - Đảm bảo bạn có các điều khoản và điều kiện kết thúc rõ ràng để Tác nhân biết khi nào cần dừng quy trình.<br>- Đối với các nhiệm vụ phức tạp cần suy luận và lập kế hoạch, sử dụng một mô hình lớn hơn chuyên về các nhiệm vụ suy luận. |
| Các cuộc gọi công cụ của Tác nhân không hoạt động tốt   | - Kiểm tra và xác thực đầu ra của công cụ bên ngoài hệ thống tác nhân.<br>- Tinh chỉnh các tham số đã định nghĩa, prompt, và cách đặt tên công cụ.  |
| Hệ thống đa tác nhân không hoạt động nhất quán | - Tinh chỉnh prompt được đưa cho từng tác nhân để đảm bảo chúng cụ thể và khác biệt.<br>- Xây dựng hệ thống phân cấp sử dụng một tác nhân "định tuyến" hoặc điều phối để xác định tác nhân đúng. |

Nhiều vấn đề này có thể được xác định hiệu quả hơn với khả năng quan sát. Các trace và chỉ số chúng ta đã thảo luận trước đó giúp chỉ ra chính xác vị trí trong luồng công việc của tác nhân nơi xảy ra vấn đề, làm cho việc gỡ lỗi và tối ưu hóa hiệu quả hơn nhiều.

## Quản lý chi phí
Dưới đây là một số chiến lược để quản lý chi phí khi triển khai các tác nhân AI vào môi trường sản xuất:

**Sử dụng Mô hình Nhỏ:** Mô hình Ngôn ngữ Nhỏ (SLMs) có thể hoạt động tốt trên một số trường hợp sử dụng liên quan đến tác nhân và sẽ giảm đáng kể chi phí. Như đã đề cập trước đó, xây dựng một hệ thống đánh giá để xác định và so sánh hiệu suất so với các mô hình lớn hơn là cách tốt nhất để hiểu được mức độ phù hợp của một SLM cho trường hợp sử dụng của bạn. Hãy cân nhắc sử dụng SLMs cho các tác vụ đơn giản hơn như phân loại ý định hoặc trích xuất tham số, đồng thời dành các mô hình lớn hơn cho những tác vụ suy luận phức tạp.

**Sử dụng Mô hình Định tuyến:** Một chiến lược tương tự là sử dụng đa dạng các mô hình và kích thước. Bạn có thể sử dụng một LLM/SLM hoặc hàm serverless để điều hướng các yêu cầu dựa trên độ phức tạp tới các mô hình phù hợp nhất. Điều này cũng sẽ giúp giảm chi phí đồng thời đảm bảo hiệu suất cho các nhiệm vụ phù hợp. Ví dụ, chuyển các truy vấn đơn giản đến các mô hình nhỏ hơn, nhanh hơn, và chỉ sử dụng các mô hình lớn, đắt tiền cho các nhiệm vụ suy luận phức tạp.

**Lưu trữ phản hồi (Caching Responses):** Xác định các yêu cầu và tác vụ phổ biến và cung cấp các phản hồi trước khi chúng đi qua hệ thống tác nhân của bạn là một cách tốt để giảm khối lượng các yêu cầu tương tự. Bạn thậm chí có thể triển khai một luồng để xác định độ tương đồng giữa một yêu cầu và các yêu cầu đã được lưu trong bộ nhớ đệm bằng cách sử dụng các mô hình AI cơ bản hơn. Chiến lược này có thể giảm đáng kể chi phí cho các câu hỏi thường gặp hoặc các luồng công việc phổ biến.

## Hãy xem cách điều này hoạt động trong thực tế

Trong [sổ tay ví dụ của phần này](./code_samples/10_autogen_evaluation.ipynb), chúng ta sẽ thấy các ví dụ về cách chúng ta có thể sử dụng các công cụ quan sát để giám sát và đánh giá tác nhân của mình.


### Còn thắc mắc gì về các tác nhân AI trong môi trường sản xuất?

Tham gia [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) để gặp gỡ những người học khác, tham dự giờ văn phòng và nhận câu trả lời cho các câu hỏi về tác nhân AI của bạn.

## Bài học trước

[Mẫu Thiết kế Siêu nhận thức](../09-metacognition/README.md)

## Bài học tiếp theo

[Giao thức tác nhân](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Miễn trừ trách nhiệm:
Văn bản này đã được dịch bằng dịch vụ dịch thuật AI Co-op Translator (https://github.com/Azure/co-op-translator). Mặc dù chúng tôi nỗ lực đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa sai sót hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ ban đầu nên được coi là nguồn có thẩm quyền. Đối với thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp do con người thực hiện. Chúng tôi không chịu trách nhiệm về bất kỳ hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->