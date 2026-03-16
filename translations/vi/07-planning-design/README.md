[![Planning Design Pattern](../../../translated_images/vi/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Nhấp vào hình trên để xem video bài học này)_

# Lập Kế Hoạch Thiết Kế

## Giới thiệu

Bài học này sẽ đề cập đến

* Xác định một mục tiêu tổng thể rõ ràng và chia nhỏ một nhiệm vụ phức tạp thành các nhiệm vụ dễ quản lý.
* Tận dụng đầu ra có cấu trúc để có các phản hồi đáng tin cậy và dễ đọc máy hơn.
* Áp dụng phương pháp tiếp cận dựa trên sự kiện để xử lý các nhiệm vụ động và các đầu vào bất ngờ.

## Mục Tiêu Học Tập

Sau khi hoàn thành bài học này, bạn sẽ hiểu về:

* Xác định và đặt mục tiêu tổng thể cho một tác nhân AI, đảm bảo nó biết rõ điều gì cần đạt được.
* Phân rã một nhiệm vụ phức tạp thành các nhiệm vụ con có thể quản lý và sắp xếp chúng theo một trình tự logic.
* Trang bị cho các tác nhân các công cụ phù hợp (ví dụ: công cụ tìm kiếm hoặc công cụ phân tích dữ liệu), quyết định khi nào và cách sử dụng, đồng thời xử lý các tình huống bất ngờ phát sinh.
* Đánh giá kết quả của các nhiệm vụ con, đo lường hiệu suất và lặp lại các hành động để cải thiện đầu ra cuối cùng.

## Xác định Mục Tiêu Tổng Thể và Phân Chia Nhiệm Vụ

![Defining Goals and Tasks](../../../translated_images/vi/defining-goals-tasks.d70439e19e37c47a.webp)

Hầu hết các nhiệm vụ trong thế giới thực đều quá phức tạp để giải quyết trong một bước duy nhất. Một tác nhân AI cần một mục tiêu ngắn gọn để hướng dẫn việc lập kế hoạch và hành động của nó. Ví dụ, xem xét mục tiêu:

    "Tạo một lịch trình du lịch 3 ngày."

Mặc dù dễ nói, nó vẫn cần được tinh chỉnh. Mục tiêu càng rõ ràng thì tác nhân (và bất kỳ cộng tác viên con người nào) càng tập trung tốt hơn vào việc đạt được kết quả phù hợp, như tạo ra một lịch trình chi tiết với các tùy chọn bay, khuyến nghị khách sạn và gợi ý hoạt động.

### Phân Chia Nhiệm Vụ

Các nhiệm vụ lớn hoặc phức tạp trở nên dễ quản lý hơn khi được chia thành các nhiệm vụ con hướng đến mục tiêu.
Ví dụ lịch trình du lịch, bạn có thể phân chia mục tiêu thành:

* Đặt Vé Máy Bay
* Đặt Khách Sạn
* Thuê Xe
* Cá Nhân Hóa

Mỗi nhiệm vụ con sau đó có thể được xử lý bởi các tác nhân hoặc quy trình chuyên biệt. Một tác nhân có thể chuyên tìm kiếm các ưu đãi vé máy bay tốt nhất, tác nhân khác tập trung vào đặt khách sạn, v.v. Một tác nhân điều phối hoặc "hậu đoạn" có thể tổng hợp các kết quả này thành một lịch trình liền mạch cho người dùng cuối.

Cách tiếp cận mô-đun này cũng cho phép cải tiến dần dần. Ví dụ, bạn có thể thêm các tác nhân chuyên biệt cho Gợi Ý Ăn Uống hoặc Hoạt Động Địa Phương và dần hoàn thiện lịch trình theo thời gian.

### Đầu Ra Cấu Trúc

Mô Hình Ngôn Ngữ Lớn (LLMs) có thể tạo ra đầu ra có cấu trúc (ví dụ JSON) giúp các tác nhân hoặc dịch vụ phía sau dễ dàng phân tích và xử lý hơn. Điều này đặc biệt hữu ích trong bối cảnh đa tác nhân, nơi chúng ta có thể hành động dựa trên các nhiệm vụ sau khi nhận được đầu ra lập kế hoạch. Tham khảo bài <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogpost</a> này để có cái nhìn nhanh.

Đoạn mã Python sau minh họa một tác nhân lập kế hoạch đơn giản phân chia mục tiêu thành các nhiệm vụ con và tạo ra kế hoạch có cấu trúc:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Mô hình nhiệm vụ phụ du lịch
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # chúng ta muốn giao nhiệm vụ cho đại lý

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Để xác thực với mô hình, bạn cần tạo một token truy cập cá nhân (PAT) trong cài đặt GitHub của bạn.
    # Tạo token PAT của bạn bằng cách làm theo hướng dẫn tại đây: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Định nghĩa tin nhắn người dùng
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Đảm bảo nội dung phản hồi là một chuỗi JSON hợp lệ trước khi tải nó
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# nếu response_content là None:
#     raise ValueError("Nội dung phản hồi không phải là chuỗi JSON hợp lệ")

# # In nội dung phản hồi sau khi tải nó dưới dạng JSON
# pprint(json.loads(response_content))

# Xác thực nội dung phản hồi với mô hình MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Tác nhân Lập Kế Hoạch với Tổ Chức Đa Tác Nhân

Trong ví dụ này, một Tác Nhân Bộ Định Tuyến Ngữ Nghĩa nhận yêu cầu của người dùng (ví dụ, "Tôi cần một kế hoạch khách sạn cho chuyến đi của mình.").

Người lập kế hoạch sau đó:

* Nhận Kế Hoạch Khách Sạn: Người lập kế hoạch lấy tin nhắn của người dùng và dựa trên lời nhắc hệ thống (bao gồm chi tiết các tác nhân có sẵn), tạo ra một kế hoạch du lịch có cấu trúc.
* Liệt Kê Các Tác Nhân và Công Cụ của Họ: Đăng ký tác nhân chứa danh sách các tác nhân (ví dụ cho vé máy bay, khách sạn, thuê xe và hoạt động) cùng với các chức năng hoặc công cụ họ cung cấp.
* Định Tuyến Kế Hoạch Đến Các Tác Nhân Tương Ứng: Tùy theo số lượng nhiệm vụ con, người lập kế hoạch hoặc gửi tin nhắn trực tiếp đến tác nhân chuyên biệt (trong trường hợp nhiệm vụ đơn lẻ) hoặc phối hợp qua quản lý nhóm chat cho cộng tác đa tác nhân.
* Tóm Tắt Kết Quả: Cuối cùng, người lập kế hoạch tóm tắt kế hoạch được tạo để rõ ràng.
Mẫu mã Python sau minh họa các bước này:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Mô hình Nhiệm vụ con Du lịch

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # chúng tôi muốn giao nhiệm vụ cho đại lý

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Tạo khách hàng với biến môi trường đã kiểm tra kiểu

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Định nghĩa tin nhắn người dùng

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Đảm bảo nội dung phản hồi là chuỗi JSON hợp lệ trước khi tải nó

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# In nội dung phản hồi sau khi tải nó dưới dạng JSON

pprint(json.loads(response_content))
```

Phần tiếp theo là đầu ra từ mã trước đó và bạn sau đó có thể sử dụng đầu ra có cấu trúc này để định tuyến tới `assigned_agent` và tóm tắt kế hoạch du lịch cho người dùng cuối.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Một notebook ví dụ với mẫu mã trước đây có sẵn [ở đây](07-autogen.ipynb).

### Lập Kế Hoạch Lặp Đi Lặp Lại

Một số nhiệm vụ đòi hỏi trao đổi qua lại hoặc tái lập kế hoạch, trong đó kết quả của một nhiệm vụ con ảnh hưởng đến nhiệm vụ tiếp theo. Ví dụ, nếu tác nhân phát hiện định dạng dữ liệu bất ngờ khi đặt vé máy bay, nó có thể cần điều chỉnh chiến lược trước khi tiếp tục đặt khách sạn.

Thêm vào đó, phản hồi của người dùng (ví dụ như một người quyết định họ muốn chuyến bay sớm hơn) có thể kích hoạt việc lập kế hoạch lại một phần. Cách tiếp cận động và lặp đi lặp lại này đảm bảo rằng giải pháp cuối cùng phù hợp với các ràng buộc thực tế và sở thích người dùng đang phát triển.

ví dụ mã

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. giống như mã trước và truyền lịch sử người dùng, kế hoạch hiện tại
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. lập kế hoạch lại và gửi các nhiệm vụ đến các đại lý tương ứng
```

Để lập kế hoạch toàn diện hơn, hãy xem <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogpost Magnetic One</a> về giải quyết các nhiệm vụ phức tạp.

## Tóm Tắt

Trong bài viết này, chúng ta đã xem xét ví dụ về cách tạo ra một bộ lập kế hoạch có thể chọn động các tác nhân sẵn có được định nghĩa. Đầu ra của Bộ lập kế hoạch phân chia nhiệm vụ và giao cho các tác nhân để thực thi. Giả định các tác nhân có quyền truy cập vào các chức năng/công cụ cần thiết để thực hiện nhiệm vụ. Ngoài các tác nhân, bạn còn có thể bao gồm các mẫu khác như phản chiếu, tóm tắt và luân phiên trò chuyện để tùy chỉnh thêm.

## Tài Nguyên Bổ Sung

AutoGen Magentic One - Hệ thống đa tác nhân tổng quát để giải quyết các nhiệm vụ phức tạp và đã đạt kết quả ấn tượng trên nhiều tiêu chuẩn agentic thách thức. Tham khảo: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Trong cài đặt này, bộ điều phối tạo kế hoạch nhiệm vụ cụ thể và ủy thác các nhiệm vụ này cho các tác nhân sẵn có. Ngoài việc lập kế hoạch, bộ điều phối còn sử dụng cơ chế theo dõi để giám sát tiến trình nhiệm vụ và lập kế hoạch lại khi cần.

### Có Thêm Câu Hỏi về Mẫu Thiết Kế Lập Kế Hoạch?

Tham gia [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) để gặp gỡ những người học khác, tham dự giờ làm việc và được giải đáp các câu hỏi về Tác Nhân AI.

## Bài Học Trước

[Building Trustworthy AI Agents](../06-building-trustworthy-agents/README.md)

## Bài Học Tiếp Theo

[Multi-Agent Design Pattern](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Tuyên bố miễn trừ trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa lỗi hoặc không chính xác. Tài liệu gốc bằng ngôn ngữ nguyên bản nên được coi là nguồn tham khảo chính xác nhất. Đối với thông tin quan trọng, nên sử dụng dịch vụ dịch thuật chuyên nghiệp của con người. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu lầm hoặc diễn giải sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->