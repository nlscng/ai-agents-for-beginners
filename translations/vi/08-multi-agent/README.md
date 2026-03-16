[![Multi-Agent Design](../../../translated_images/vi/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Nhấp vào hình ảnh trên để xem video của bài học này)_

# Các mẫu thiết kế đa tác nhân

Ngay khi bạn bắt đầu làm việc trên một dự án liên quan đến nhiều tác nhân, bạn sẽ cần xem xét mẫu thiết kế đa tác nhân. Tuy nhiên, có thể chưa rõ ràng ngay khi nào nên chuyển sang đa tác nhân và những lợi ích của nó là gì.

## Giới thiệu

Trong bài học này, chúng ta sẽ tìm câu trả lời cho các câu hỏi sau:

- Những kịch bản nào áp dụng được đa tác nhân?
- Lợi ích của việc sử dụng đa tác nhân so với chỉ một tác nhân đơn làm nhiều nhiệm vụ là gì?
- Các khối xây dựng để triển khai mẫu thiết kế đa tác nhân là gì?
- Làm thế nào để chúng ta có thể quan sát được cách các tác nhân tương tác với nhau?

## Mục tiêu học tập

Sau bài học này, bạn sẽ có thể:

- Xác định các kịch bản áp dụng được đa tác nhân
- Nhận biết lợi ích của việc sử dụng đa tác nhân so với tác nhân đơn lẻ
- Hiểu được các khối xây dựng để triển khai mẫu thiết kế đa tác nhân

Bức tranh lớn hơn là gì?

*Đa tác nhân là một mẫu thiết kế cho phép nhiều tác nhân làm việc cùng nhau để đạt được một mục tiêu chung*.

Mẫu này được sử dụng rộng rãi trong nhiều lĩnh vực, bao gồm robot, hệ thống tự động và điện toán phân tán.

## Các kịch bản áp dụng đa tác nhân

Vậy những kịch bản nào là trường hợp sử dụng tốt cho đa tác nhân? Câu trả lời là có rất nhiều kịch bản mà việc sử dụng nhiều tác nhân mang lại lợi ích, đặc biệt trong các trường hợp sau:

- **Khối lượng công việc lớn**: Khối lượng công việc lớn có thể được chia thành các nhiệm vụ nhỏ hơn và phân bổ cho các tác nhân khác nhau, cho phép xử lý đồng thời và hoàn thành nhanh hơn. Ví dụ là một nhiệm vụ xử lý dữ liệu lớn.
- **Nhiệm vụ phức tạp**: Các nhiệm vụ phức tạp, giống như khối lượng công việc lớn, có thể được chia thành các nhiệm vụ con nhỏ hơn và gán cho các tác nhân khác nhau, mỗi tác nhân chuyên về một khía cạnh cụ thể của nhiệm vụ. Ví dụ điển hình là các xe tự hành, nơi các tác nhân khác nhau quản lý khả năng điều hướng, phát hiện chướng ngại vật, và giao tiếp với các xe khác.
- **Chuyên môn đa dạng**: Các tác nhân khác nhau có thể có chuyên môn đa dạng, cho phép họ xử lý các khía cạnh của nhiệm vụ hiệu quả hơn so với một tác nhân đơn. Ví dụ trong lĩnh vực chăm sóc sức khỏe, các tác nhân có thể quản lý chuẩn đoán, kế hoạch điều trị, và theo dõi bệnh nhân.

## Lợi thế của việc sử dụng đa tác nhân so với chỉ một tác nhân duy nhất

Hệ thống một tác nhân có thể hoạt động tốt cho các nhiệm vụ đơn giản, nhưng với các nhiệm vụ phức tạp hơn, sử dụng nhiều tác nhân sẽ mang lại một số lợi ích:

- **Chuyên môn hóa**: Mỗi tác nhân có thể được chuyên môn hóa cho một nhiệm vụ cụ thể. Thiếu chuyên môn hóa trong một tác nhân duy nhất có nghĩa là tác nhân đó có thể làm tất cả mọi việc nhưng có thể bị nhầm lẫn khi phải xử lý các nhiệm vụ phức tạp. Ví dụ, nó có thể xử lý một nhiệm vụ mà nó không phù hợp nhất.
- **Tính mở rộng**: Dễ dàng mở rộng hệ thống bằng cách thêm nhiều tác nhân hơn thay vì quá tải một tác nhân duy nhất.
- **Khả năng chịu lỗi**: Nếu một tác nhân bị lỗi, các tác nhân khác vẫn tiếp tục hoạt động, đảm bảo độ tin cậy của hệ thống.

Hãy lấy ví dụ, hãy đặt một chuyến đi cho người dùng. Một hệ thống tác nhân đơn sẽ phải xử lý tất cả các khía cạnh của quá trình đặt chuyến đi, từ tìm chuyến bay đến đặt khách sạn và thuê xe. Để đạt được điều này với một tác nhân duy nhất, tác nhân đó phải có các công cụ xử lý tất cả các nhiệm vụ. Điều này có thể dẫn đến một hệ thống phức tạp, một thể thống nhất, khó bảo trì và mở rộng. Trong khi đó, một hệ thống đa tác nhân có thể có các tác nhân chuyên môn hóa trong việc tìm chuyến bay, đặt khách sạn, và thuê xe. Điều này làm cho hệ thống mô-đun hơn, dễ bảo trì và có khả năng mở rộng.

So sánh điều này với một văn phòng du lịch nhỏ do gia đình vận hành so với một văn phòng du lịch theo mô hình nhượng quyền. Văn phòng nhỏ gia đình sẽ có một tác nhân duy nhất xử lý tất cả các khía cạnh của việc đặt chuyến đi, trong khi nhượng quyền sẽ có các tác nhân khác nhau xử lý các khía cạnh khác nhau của quá trình.

## Các khối xây dựng để triển khai mẫu thiết kế đa tác nhân

Trước khi bạn có thể triển khai mẫu thiết kế đa tác nhân, bạn cần hiểu các thành phần cấu tạo nên mẫu.

Hãy làm điều này cụ thể hơn bằng cách xem xét ví dụ đặt chuyến đi cho người dùng. Trong trường hợp này, các khối xây dựng bao gồm:

- **Giao tiếp giữa các tác nhân**: Các tác nhân tìm chuyến bay, đặt khách sạn và thuê xe cần giao tiếp và chia sẻ thông tin về sở thích và ràng buộc của người dùng. Bạn cần quyết định các giao thức và phương pháp cho việc giao tiếp này. Cụ thể là tác nhân tìm chuyến bay cần giao tiếp với tác nhân đặt khách sạn để đảm bảo khách sạn được đặt cùng ngày với chuyến bay. Điều đó có nghĩa là các tác nhân cần chia sẻ thông tin về ngày đi du lịch của người dùng, tức là bạn cần quyết định *những tác nhân nào chia sẻ thông tin và cách họ chia sẻ*.
- **Cơ chế phối hợp**: Các tác nhân cần phối hợp hành động để đảm bảo sở thích và ràng buộc của người dùng được đáp ứng. Ví dụ, sở thích của người dùng có thể là muốn khách sạn gần sân bay trong khi một ràng buộc là xe thuê chỉ có sẵn tại sân bay. Điều này nghĩa là tác nhân đặt khách sạn cần phối hợp với tác nhân thuê xe để đảm bảo các sở thích và ràng buộc của người dùng được đáp ứng. Bạn cần quyết định *cách các tác nhân phối hợp hành động*.
- **Kiến trúc tác nhân**: Các tác nhân cần có cấu trúc nội bộ để ra quyết định và học hỏi từ tương tác với người dùng. Ví dụ, tác nhân tìm chuyến bay cần có cấu trúc nội bộ để quyết định các chuyến bay nên đề xuất cho người dùng. Bạn cần quyết định *cách các tác nhân đưa ra quyết định và học hỏi từ tương tác với người dùng*. Ví dụ về cách tác nhân học và cải thiện có thể là tác nhân tìm chuyến bay sử dụng mô hình học máy để đề xuất chuyến bay dựa trên sở thích trước đó của người dùng.
- **Khả năng quan sát tương tác đa tác nhân**: Bạn cần có khả năng quan sát cách các tác nhân tương tác với nhau. Điều này có nghĩa bạn cần các công cụ và kỹ thuật để theo dõi hoạt động và tương tác của các tác nhân. Điều này có thể ở dạng công cụ ghi nhật ký và giám sát, công cụ trực quan hóa và các chỉ số hiệu suất.
- **Mẫu đa tác nhân**: Có các mẫu khác nhau để triển khai hệ thống đa tác nhân, như kiến trúc tập trung, phân tán và lai. Bạn cần quyết định mẫu phù hợp nhất với trường hợp sử dụng của bạn.
- **Con người trong vòng quay**: Trong hầu hết các trường hợp, bạn sẽ có một con người trong vòng quay và bạn cần chỉ dẫn các tác nhân khi nào phải yêu cầu can thiệp của con người. Điều này có thể ở dạng người dùng yêu cầu một khách sạn hay chuyến bay cụ thể mà các tác nhân chưa đề xuất hoặc yêu cầu xác nhận trước khi đặt chuyến bay hoặc khách sạn.

## Khả năng quan sát tương tác đa tác nhân

Việc bạn có thể quan sát cách các tác nhân tương tác rất quan trọng. Khả năng này cần thiết để gỡ lỗi, tối ưu hóa và đảm bảo hiệu quả tổng thể của hệ thống. Để làm được điều đó, bạn cần có các công cụ và kỹ thuật để theo dõi hoạt động và tương tác của các tác nhân. Ví dụ là công cụ ghi nhật ký và giám sát, công cụ trực quan và các chỉ số hiệu suất.

Ví dụ, trong trường hợp đặt chuyến đi cho người dùng, bạn có thể có một bảng điều khiển hiển thị trạng thái của từng tác nhân, sở thích và ràng buộc của người dùng, cũng như tương tác giữa các tác nhân. Bảng này có thể hiển thị ngày đi du lịch của người dùng, các chuyến bay được tác nhân chuyến bay đề xuất, khách sạn được tác nhân khách sạn đề xuất, và các xe thuê do tác nhân thuê xe đề xuất. Điều này sẽ cho bạn cái nhìn rõ ràng về cách các tác nhân tương tác với nhau và liệu các sở thích và ràng buộc của người dùng có được đáp ứng hay không.

Chúng ta cùng xem xét chi tiết từng khía cạnh này.

- **Công cụ ghi nhật ký và giám sát**: Bạn muốn ghi lại nhật ký cho mỗi hành động mà tác nhân thực hiện. Một mục ghi nhật ký có thể lưu trữ thông tin về tác nhân thực hiện hành động, hành động đã thực hiện, thời gian thực hiện và kết quả của hành động đó. Thông tin này có thể dùng để gỡ lỗi, tối ưu hóa và hơn thế nữa.

- **Công cụ trực quan hóa**: Công cụ trực quan giúp bạn nhìn thấy các tương tác giữa các tác nhân một cách trực quan hơn. Ví dụ, bạn có thể có một đồ thị hiển thị luồng thông tin giữa các tác nhân. Điều này giúp bạn nhận diện các điểm nghẽn, sự kém hiệu quả và các vấn đề khác trong hệ thống.

- **Chỉ số hiệu suất**: Các chỉ số hiệu suất giúp bạn theo dõi hiệu quả của hệ thống đa tác nhân. Ví dụ, bạn có thể theo dõi thời gian hoàn thành một nhiệm vụ, số nhiệm vụ hoàn thành trong một đơn vị thời gian, và độ chính xác của các đề xuất do các tác nhân đưa ra. Thông tin này giúp bạn xác định các điểm cần cải thiện và tối ưu hóa hệ thống.

## Mẫu đa tác nhân

Hãy đi sâu vào một số mẫu cụ thể mà bạn có thể sử dụng để tạo ứng dụng đa tác nhân. Dưới đây là một số mẫu thú vị đáng xem xét:

### Trò chuyện nhóm

Mẫu này hữu ích khi bạn muốn tạo một ứng dụng trò chuyện nhóm nơi nhiều tác nhân có thể giao tiếp với nhau. Các trường hợp sử dụng điển hình của mẫu này bao gồm hợp tác nhóm, hỗ trợ khách hàng, và mạng xã hội.

Trong mẫu này, mỗi tác nhân đại diện cho một người dùng trong nhóm chat, và các tin nhắn được trao đổi giữa các tác nhân bằng một giao thức nhắn tin. Các tác nhân có thể gửi tin nhắn đến nhóm chat, nhận tin nhắn từ nhóm chat, và phản hồi tin nhắn từ các tác nhân khác.

Mẫu này có thể được triển khai bằng kiến trúc tập trung, nơi tất cả các tin nhắn được chuyển qua một máy chủ trung tâm, hoặc kiến trúc phân tán, nơi các tin nhắn được trao đổi trực tiếp.

![Group chat](../../../translated_images/vi/multi-agent-group-chat.ec10f4cde556babd.webp)

### Chuyển giao (Hand-off)

Mẫu này hữu ích khi bạn muốn tạo một ứng dụng nơi nhiều tác nhân có thể chuyển giao nhiệm vụ cho nhau.

Các trường hợp sử dụng điển hình bao gồm hỗ trợ khách hàng, quản lý nhiệm vụ, và tự động hóa quy trình làm việc.

Trong mẫu này, mỗi tác nhân đại diện cho một nhiệm vụ hoặc một bước trong quy trình, và các tác nhân có thể chuyển giao nhiệm vụ cho tác nhân khác dựa trên các quy tắc đã định sẵn.

![Hand off](../../../translated_images/vi/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Lọc cộng tác

Mẫu này hữu ích khi bạn muốn tạo một ứng dụng nơi nhiều tác nhân hợp tác để đưa ra đề xuất cho người dùng.

Lý do bạn muốn nhiều tác nhân hợp tác là bởi vì mỗi tác nhân có thể có chuyên môn khác nhau và đóng góp vào quá trình đề xuất theo những cách khác nhau.

Hãy lấy ví dụ người dùng muốn được đề xuất cổ phiếu tốt nhất để mua trên thị trường chứng khoán.

- **Chuyên gia ngành**: Một tác nhân có thể là chuyên gia trong một ngành cụ thể.
- **Phân tích kỹ thuật**: Một tác nhân khác có thể là chuyên gia phân tích kỹ thuật.
- **Phân tích cơ bản**: Và một tác nhân khác có thể là chuyên gia phân tích cơ bản. Bằng việc hợp tác, các tác nhân này có thể cung cấp một đề xuất toàn diện hơn cho người dùng.

![Recommendation](../../../translated_images/vi/multi-agent-filtering.d959cb129dc9f608.webp)

## Kịch bản: Quy trình hoàn tiền

Xem xét một kịch bản khách hàng muốn lấy lại tiền cho một sản phẩm, có thể có khá nhiều tác nhân liên quan trong quy trình này, nhưng chúng ta sẽ chia thành tác nhân cụ thể cho quy trình này và các tác nhân chung có thể dùng trong các quy trình khác.

**Các tác nhân cụ thể cho quy trình hoàn tiền**:

Dưới đây là một số tác nhân có thể tham gia vào quy trình hoàn tiền:

- **Tác nhân khách hàng**: Đại diện cho khách hàng và chịu trách nhiệm khởi xướng quy trình hoàn tiền.
- **Tác nhân người bán**: Đại diện cho người bán và chịu trách nhiệm xử lý việc hoàn tiền.
- **Tác nhân thanh toán**: Đại diện cho quy trình thanh toán và chịu trách nhiệm hoàn tiền cho khách hàng.
- **Tác nhân giải quyết**: Đại diện cho quy trình giải quyết và chịu trách nhiệm xử lý các vấn đề phát sinh trong quy trình hoàn tiền.
- **Tác nhân tuân thủ**: Đại diện cho quy trình tuân thủ và chịu trách nhiệm đảm bảo quy trình hoàn tiền phù hợp với các quy định và chính sách.

**Các tác nhân chung**:

Những tác nhân này có thể được sử dụng bởi các phần khác trong doanh nghiệp của bạn.

- **Tác nhân vận chuyển**: Đại diện cho quy trình vận chuyển và chịu trách nhiệm vận chuyển sản phẩm trả lại người bán. Tác nhân này có thể dùng cả cho quy trình hoàn tiền và vận chuyển chung khi mua hàng.
- **Tác nhân phản hồi**: Đại diện cho quy trình thu thập phản hồi từ khách hàng. Phản hồi có thể được lấy bất cứ lúc nào chứ không chỉ trong quy trình hoàn tiền.
- **Tác nhân tăng cấp**: Đại diện cho quy trình tăng cấp và chịu trách nhiệm đưa các vấn đề lên cấp hỗ trợ cao hơn. Bạn có thể dùng loại tác nhân này cho bất kỳ quy trình nào cần tăng cấp vấn đề.
- **Tác nhân thông báo**: Đại diện cho quy trình thông báo và chịu trách nhiệm gửi thông báo đến khách hàng ở các giai đoạn khác nhau của quy trình hoàn tiền.
- **Tác nhân phân tích**: Đại diện cho quy trình phân tích dữ liệu liên quan đến quy trình hoàn tiền.
- **Tác nhân kiểm toán**: Đại diện cho quy trình kiểm toán và chịu trách nhiệm kiểm tra quy trình hoàn tiền để đảm bảo được thực hiện đúng.
- **Tác nhân báo cáo**: Đại diện cho quy trình báo cáo và chịu trách nhiệm tạo báo cáo về quy trình hoàn tiền.
- **Tác nhân kiến thức**: Đại diện cho quy trình quản lý kiến thức và chịu trách nhiệm duy trì cơ sở dữ liệu thông tin liên quan đến quy trình hoàn tiền. Tác nhân này có thể có kiến thức về cả hoàn tiền và các phần khác trong doanh nghiệp của bạn.
- **Tác nhân an ninh**: Đại diện cho quy trình bảo mật và chịu trách nhiệm đảm bảo an toàn cho quy trình hoàn tiền.
- **Tác nhân chất lượng**: Đại diện cho quy trình quản lý chất lượng và chịu trách nhiệm đảm bảo chất lượng của quy trình hoàn tiền.

Có khá nhiều tác nhân được liệt kê ở trên cả cho quy trình hoàn tiền cụ thể và các tác nhân chung có thể được dùng ở các phần khác của doanh nghiệp bạn. Hy vọng điều này giúp bạn hình dung cách quyết định các tác nhân sử dụng trong hệ thống đa tác nhân của bạn.

## Bài tập

Thiết kế một hệ thống đa tác nhân cho quy trình hỗ trợ khách hàng. Xác định các tác nhân tham gia trong quy trình, vai trò và trách nhiệm của họ, cũng như cách họ tương tác với nhau. Xem xét cả các tác nhân cụ thể cho quy trình hỗ trợ khách hàng và các tác nhân chung có thể dùng trong các phần khác của doanh nghiệp bạn.
> Hãy suy nghĩ trước khi bạn đọc giải pháp sau, bạn có thể cần nhiều tác nhân hơn bạn nghĩ.

> TIP: Hãy nghĩ về các giai đoạn khác nhau của quy trình hỗ trợ khách hàng và cũng cân nhắc các tác nhân cần thiết cho bất kỳ hệ thống nào.

## Solution

[Solution](./solution/solution.md)

## Knowledge checks

Question: Khi nào bạn nên xem xét sử dụng đa tác nhân?

- [ ] A1: Khi bạn có khối lượng công việc nhỏ và nhiệm vụ đơn giản.
- [ ] A2: Khi bạn có khối lượng công việc lớn
- [ ] A3: Khi bạn có nhiệm vụ đơn giản.

[Solution quiz](./solution/solution-quiz.md)

## Summary

Trong bài học này, chúng ta đã xem xét mô hình thiết kế đa tác nhân, bao gồm các kịch bản áp dụng đa tác nhân, những lợi ích của việc sử dụng đa tác nhân so với một tác nhân duy nhất, các thành phần xây dựng để triển khai mô hình thiết kế đa tác nhân, và cách để có thể quan sát được cách các tác nhân đa tương tác với nhau.

### Có Thêm Câu Hỏi về Mô Hình Thiết Kế Đa Tác Nhân?

Tham gia [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) để gặp gỡ những người học khác, tham dự các giờ làm việc và nhận được câu trả lời cho các câu hỏi về Tác nhân AI của bạn.

## Additional resources

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Mô hình thiết kế AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Mô hình thiết kế Agentic</a>


## Previous Lesson

[Planning Design](../07-planning-design/README.md)

## Next Lesson

[Metacognition in AI Agents](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Tuyên bố từ chối trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi nỗ lực đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ nguyên bản nên được coi là nguồn đáng tin cậy nhất. Đối với các thông tin quan trọng, khuyến nghị sử dụng dịch thuật chuyên nghiệp bởi con người. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu nhầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->