[![How to Design Good AI Agents](../../../translated_images/vi/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Nhấn vào hình trên để xem video bài học này)_

# Mẫu Thiết Kế Sử Dụng Công Cụ

Công cụ rất thú vị vì chúng cho phép các tác nhân AI có phạm vi khả năng rộng hơn. Thay vì tác nhân chỉ có một tập các hành động giới hạn mà nó có thể thực hiện, bằng cách thêm một công cụ, tác nhân giờ đây có thể thực hiện một loạt các hành động đa dạng. Trong chương này, chúng ta sẽ xem xét Mẫu Thiết Kế Sử Dụng Công Cụ, mô tả cách các tác nhân AI có thể sử dụng các công cụ cụ thể để đạt được mục tiêu của họ.

## Giới thiệu

Trong bài học này, chúng ta sẽ cố gắng trả lời các câu hỏi sau:

- Mẫu thiết kế sử dụng công cụ là gì?
- Nó có thể áp dụng vào các trường hợp sử dụng nào?
- Các thành phần/khối xây dựng cần thiết để triển khai mẫu thiết kế là gì?
- Các lưu ý đặc biệt khi sử dụng Mẫu Thiết Kế Sử Dụng Công Cụ để xây dựng các tác nhân AI đáng tin cậy là gì?

## Mục tiêu học tập

Sau khi hoàn thành bài học này, bạn sẽ có thể:

- Định nghĩa Mẫu Thiết Kế Sử Dụng Công Cụ và mục đích của nó.
- Xác định các trường hợp sử dụng mà Mẫu Thiết Kế Sử Dụng Công Cụ có thể áp dụng.
- Hiểu các yếu tố chính cần để triển khai mẫu thiết kế.
- Nhận biết các yếu tố cần lưu ý để đảm bảo sự đáng tin cậy ở các tác nhân AI sử dụng mẫu thiết kế này.

## Mẫu Thiết Kế Sử Dụng Công Cụ là gì?

**Mẫu Thiết Kế Sử Dụng Công Cụ** tập trung vào việc cung cấp cho các Mô Hình Ngôn Ngữ Lớn (LLMs) khả năng tương tác với các công cụ bên ngoài để đạt được các mục tiêu cụ thể. Công cụ là các đoạn mã có thể được tác nhân thực thi để thực hiện các hành động. Một công cụ có thể là một hàm đơn giản như máy tính, hoặc là một cuộc gọi API đến dịch vụ bên thứ ba như tra cứu giá cổ phiếu hoặc dự báo thời tiết. Trong ngữ cảnh các tác nhân AI, các công cụ được thiết kế để được thực thi bởi các tác nhân nhằm phản hồi các **cuộc gọi hàm do mô hình tạo ra**.

## Các trường hợp sử dụng mà nó có thể áp dụng là gì?

Các tác nhân AI có thể tận dụng công cụ để hoàn thành các nhiệm vụ phức tạp, truy xuất thông tin hoặc đưa ra quyết định. Mẫu thiết kế sử dụng công cụ thường được dùng trong các kịch bản yêu cầu tương tác động với các hệ thống bên ngoài, chẳng hạn như cơ sở dữ liệu, dịch vụ web hoặc trình thông dịch mã. Khả năng này hữu ích cho nhiều trường hợp khác nhau bao gồm:

- **Truy xuất Thông tin Động:** Các tác nhân có thể truy vấn API bên ngoài hoặc cơ sở dữ liệu để lấy dữ liệu cập nhật (ví dụ: truy vấn cơ sở dữ liệu SQLite để phân tích dữ liệu, lấy giá cổ phiếu hoặc thông tin thời tiết).
- **Thực thi và Thông dịch Mã:** Các tác nhân có thể thực thi mã hoặc script để giải quyết các bài toán toán học, tạo báo cáo hoặc thực hiện mô phỏng.
- **Tự động hóa Quy trình Làm việc:** Tự động hóa các quy trình lặp đi lặp lại hoặc đa bước bằng cách tích hợp các công cụ như bộ lập lịch tác vụ, dịch vụ email hoặc đường ống dữ liệu.
- **Hỗ trợ Khách hàng:** Các tác nhân có thể tương tác với hệ thống CRM, nền tảng quản lý vé hoặc cơ sở dữ liệu kiến thức để giải quyết các câu hỏi người dùng.
- **Tạo và Chỉnh sửa Nội dung:** Các tác nhân có thể sử dụng các công cụ như kiểm tra ngữ pháp, tóm tắt văn bản hoặc đánh giá an toàn nội dung để hỗ trợ các nhiệm vụ tạo nội dung.

## Các thành phần/khối xây dựng cần thiết để triển khai mẫu thiết kế sử dụng công cụ là gì?

Các khối xây dựng này cho phép tác nhân AI thực hiện nhiều loại nhiệm vụ đa dạng. Hãy xem xét các yếu tố chính cần để triển khai Mẫu Thiết Kế Sử Dụng Công Cụ:

- **Định nghĩa Hàm/Công cụ**: Các định nghĩa chi tiết về các công cụ có sẵn, bao gồm tên hàm, mục đích, tham số cần thiết và kết quả đầu ra dự kiến. Các định nghĩa này cho phép LLM hiểu được các công cụ sẵn có và cách xây dựng các yêu cầu hợp lệ.

- **Logic Thực thi Hàm:** Quy định cách và thời điểm các công cụ được gọi dựa trên ý định người dùng và ngữ cảnh cuộc trò chuyện. Điều này có thể bao gồm các mô-đun lập kế hoạch, cơ chế định tuyến, hoặc luồng điều kiện để quyết định việc sử dụng công cụ một cách động.

- **Hệ thống Xử lý Tin nhắn:** Các thành phần quản lý luồng trò chuyện giữa nhập liệu từ người dùng, phản hồi từ LLM, các cuộc gọi công cụ và đầu ra của công cụ.

- **Khung Tích hợp Công cụ:** Hạ tầng kết nối tác nhân với nhiều công cụ khác nhau, dù là các hàm đơn giản hay các dịch vụ phức tạp bên ngoài.

- **Xử lý Lỗi & Xác thực:** Các cơ chế để xử lý thất bại khi thực thi công cụ, xác thực tham số và quản lý các phản hồi không mong đợi.

- **Quản lý Trạng thái:** Theo dõi bối cảnh cuộc trò chuyện, các tương tác công cụ trước đó và dữ liệu tồn tại nhằm đảm bảo sự nhất quán qua các lượt tương tác.

Tiếp theo, hãy xem chi tiết về Gọi Hàm/Công cụ.

### Gọi Hàm/Công cụ

Gọi hàm là cách chủ yếu để cho phép các Mô Hình Ngôn Ngữ Lớn (LLMs) tương tác với công cụ. Bạn sẽ thường thấy từ 'Hàm' và 'Công cụ' được dùng thay thế cho nhau vì 'hàm' (khối mã có thể tái sử dụng) là 'công cụ' mà các tác nhân sử dụng để thực hiện nhiệm vụ. Để mã của một hàm được gọi, LLM phải so sánh yêu cầu của người dùng với mô tả hàm. Để làm điều này, một schema chứa mô tả của tất cả các hàm có sẵn được gửi tới LLM. LLM sau đó chọn hàm phù hợp nhất cho nhiệm vụ và trả về tên hàm cùng các tham số. Hàm được chọn sẽ được gọi, phản hồi của nó được gửi lại cho LLM, và LLM sử dụng thông tin đó để phản hồi yêu cầu người dùng.

Để các nhà phát triển triển khai gọi hàm cho tác nhân, bạn cần:

1. Một mô hình LLM hỗ trợ gọi hàm
2. Một schema chứa mô tả hàm
3. Mã cho từng hàm được mô tả

Hãy dùng ví dụ lấy thời gian hiện tại ở một thành phố để minh họa:

1. **Khởi tạo một LLM hỗ trợ gọi hàm:**

    Không phải tất cả các mô hình đều hỗ trợ gọi hàm, vì vậy điều quan trọng là kiểm tra rằng LLM bạn sử dụng có hỗ trợ hay không. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> hỗ trợ gọi hàm. Chúng ta có thể bắt đầu bằng việc khởi tạo client Azure OpenAI.

    ```python
    # Khởi tạo client Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Tạo Schema Hàm:**

    Tiếp theo chúng ta sẽ định nghĩa một schema JSON chứa tên hàm, mô tả về chức năng của hàm và tên cùng mô tả các tham số của hàm.
    Sau đó, ta sẽ gửi schema này tới client đã tạo trước đó, cùng với yêu cầu của người dùng để tìm thời gian ở San Francisco. Điều quan trọng cần lưu ý là **cuộc gọi công cụ** là cái được trả về, **không phải** kết quả cuối cùng của câu hỏi. Như đã đề cập, LLM trả về tên của hàm mà nó chọn cho nhiệm vụ, cùng các đối số sẽ được truyền cho hàm.

    ```python
    # Mô tả chức năng để mô hình đọc
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
  
    # Tin nhắn người dùng ban đầu
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Lần gọi API đầu tiên: Yêu cầu mô hình sử dụng hàm
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Xử lý phản hồi của mô hình
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Mã hàm cần thiết để thực hiện nhiệm vụ:**

    Bây giờ LLM đã chọn hàm nào cần được chạy, mã để thực hiện nhiệm vụ đó cần được triển khai và thực thi.
    Chúng ta có thể triển khai mã để lấy thời gian hiện tại bằng Python. Chúng ta cũng cần viết mã để trích xuất tên và các tham số từ response_message để lấy kết quả cuối cùng.

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
     # Xử lý các cuộc gọi hàm
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
  
      # Gọi API thứ hai: Lấy phản hồi cuối cùng từ mô hình
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

Gọi Hàm là trung tâm của hầu hết, nếu không muốn nói là tất cả thiết kế sử dụng công cụ cho tác nhân, tuy nhiên triển khai nó từ đầu đôi khi có thể khó khăn.
Như chúng ta đã học trong [Bài học 2](../../../02-explore-agentic-frameworks), các framework agentic cung cấp cho chúng ta các khối xây dựng sẵn để triển khai việc sử dụng công cụ.
 
## Ví dụ Sử dụng Công cụ với Các Framework Agentic

Dưới đây là một số ví dụ về cách bạn có thể triển khai Mẫu Thiết Kế Sử Dụng Công Cụ bằng các framework agentic khác nhau:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> là một framework AI mã nguồn mở dành cho các nhà phát triển .NET, Python và Java làm việc với Mô Hình Ngôn Ngữ Lớn (LLMs). Nó giúp đơn giản hóa quá trình gọi hàm bằng cách tự động mô tả các hàm và tham số của bạn cho mô hình thông qua quá trình gọi là <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">chuẩn hóa</a>. Nó cũng xử lý việc giao tiếp qua lại giữa mô hình và mã của bạn. Một lợi thế khác khi sử dụng framework agentic như Semantic Kernel là nó cho phép bạn truy cập các công cụ dựng sẵn như <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Tìm kiếm Tệp</a> và <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Trình Thông Dịch Mã</a>.

Sơ đồ sau minh họa quá trình gọi hàm với Semantic Kernel:

![function calling](../../../translated_images/vi/functioncalling-diagram.a84006fc287f6014.webp)

Trong Semantic Kernel các hàm/công cụ gọi là <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugin</a>. Chúng ta có thể chuyển hàm `get_current_time` đã thấy ở trên thành một plugin bằng cách biến nó thành một lớp chứa hàm đó. Chúng ta cũng có thể import trình trang trí `kernel_function`, nhận mô tả của hàm. Khi bạn tạo một kernel với GetCurrentTimePlugin, kernel sẽ tự động chuẩn hóa hàm và tham số, tạo schema để gửi đến LLM trong quá trình này.

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

# Tạo kernel
kernel = Kernel()

# Tạo plugin
get_current_time_plugin = GetCurrentTimePlugin(location)

# Thêm plugin vào kernel
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> là một framework agentic mới được thiết kế để giúp các nhà phát triển xây dựng, triển khai và mở rộng các tác nhân AI chất lượng cao, có thể mở rộng và an toàn mà không cần quản lý tài nguyên tính toán và lưu trữ nền tảng. Nó đặc biệt hữu ích cho các ứng dụng doanh nghiệp vì đây là một dịch vụ hoàn toàn được quản lý với bảo mật cấp doanh nghiệp.

So với phát triển trực tiếp bằng API LLM, Azure AI Agent Service có một số lợi thế, bao gồm:

- Gọi công cụ tự động – không cần phân tích cuộc gọi công cụ, gọi công cụ và xử lý phản hồi; tất cả đều được thực hiện phía máy chủ
- Quản lý dữ liệu an toàn – thay vì tự quản lý trạng thái hội thoại, bạn có thể dựa vào các `threads` để lưu trữ tất cả thông tin cần thiết
- Công cụ có sẵn – Các công cụ bạn có thể dùng để tương tác với nguồn dữ liệu, như Bing, Azure AI Search và Azure Functions.

Các công cụ có sẵn trong Azure AI Agent Service chia thành hai loại:

1. Công cụ Kiến thức:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Tích hợp với Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Tìm kiếm Tệp</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Công cụ Hành động:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Gọi Hàm</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Trình Thông Dịch Mã</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">Công cụ định nghĩa theo OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Dịch vụ Agent cho phép chúng ta sử dụng các công cụ này cùng nhau như một `bộ công cụ`. Nó cũng sử dụng `threads` để theo dõi lịch sử tin nhắn từ một cuộc hội thoại cụ thể.

Hãy tưởng tượng bạn là một đại diện bán hàng tại một công ty có tên Contoso. Bạn muốn phát triển một tác nhân hội thoại có thể trả lời các câu hỏi về dữ liệu bán hàng.

Hình ảnh sau minh họa cách bạn có thể sử dụng Azure AI Agent Service để phân tích dữ liệu bán hàng:

![Agentic Service In Action](../../../translated_images/vi/agent-service-in-action.34fb465c9a84659e.webp)

Để sử dụng bất kỳ công cụ nào với dịch vụ, chúng ta có thể tạo một client và định nghĩa một công cụ hoặc bộ công cụ. Để áp dụng thực tế, ta có thể sử dụng đoạn mã Python sau. LLM sẽ có thể xem xét bộ công cụ và quyết định sử dụng hàm do người dùng tạo, `fetch_sales_data_using_sqlite_query`, hoặc Code Interpreter dựng sẵn tùy theo yêu cầu người dùng.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # hàm fetch_sales_data_using_sqlite_query có thể được tìm thấy trong tệp fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Khởi tạo bộ công cụ
toolset = ToolSet()

# Khởi tạo agent gọi hàm với hàm fetch_sales_data_using_sqlite_query và thêm nó vào bộ công cụ
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Khởi tạo công cụ Code Interpreter và thêm nó vào bộ công cụ.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Những lưu ý đặc biệt khi sử dụng Mẫu Thiết Kế Sử Dụng Công Cụ để xây dựng các tác nhân AI đáng tin cậy là gì?

Một mối lo ngại phổ biến với SQL được sinh động bởi LLM là vấn đề bảo mật, đặc biệt là nguy cơ tấn công chèn SQL hoặc các hành động ác ý, chẳng hạn như xóa hoặc can thiệp vào cơ sở dữ liệu. Dù các quan ngại này là hợp lệ, chúng có thể được hạn chế hiệu quả bằng cách cấu hình đúng quyền truy cập cơ sở dữ liệu. Với hầu hết các cơ sở dữ liệu, điều này bao gồm việc cấu hình cơ sở dữ liệu ở chế độ chỉ đọc. Với các dịch vụ cơ sở dữ liệu như PostgreSQL hoặc Azure SQL, ứng dụng nên được cấp vai trò chỉ đọc (SELECT).

Chạy ứng dụng trong môi trường an toàn cũng giúp tăng cường bảo vệ. Trong các kịch bản doanh nghiệp, dữ liệu thường được trích xuất và chuyển đổi từ các hệ thống vận hành thành một cơ sở dữ liệu hoặc kho dữ liệu chỉ đọc với schema thân thiện với người dùng. Cách tiếp cận này đảm bảo dữ liệu được bảo mật, tối ưu hiệu suất và khả năng truy cập, đồng thời ứng dụng có quyền truy cập hạn chế và chỉ đọc.

## Mã mẫu
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Có Thêm Câu Hỏi về Việc Sử Dụng Mẫu Thiết Kế Công Cụ?

Tham gia [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) để gặp gỡ các học viên khác, tham dự giờ làm việc và nhận được câu trả lời cho các câu hỏi về tác nhân AI của bạn.

## Tài Nguyên Bổ Sung

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Hội Thảo Dịch Vụ Azure AI Agents</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Hội Thảo Đa Tác Nhân Contoso Creative Writer</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Hướng Dẫn Gọi Hàm Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Trình Diễn Mã Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Công Cụ Autogen</a>

## Bài Học Trước

[Hiểu Về Các Mẫu Thiết Kế Agentic](../03-agentic-design-patterns/README.md)

## Bài Học Tiếp Theo

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Tuyên bố từ chối trách nhiệm**:  
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI [Co-op Translator](https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo độ chính xác, xin lưu ý rằng bản dịch tự động có thể chứa lỗi hoặc sai sót. Tài liệu gốc bằng ngôn ngữ nguyên bản nên được coi là nguồn chính xác và đáng tin cậy nhất. Đối với các thông tin quan trọng, chúng tôi khuyến nghị sử dụng dịch vụ dịch thuật chuyên nghiệp bởi con người. Chúng tôi không chịu trách nhiệm về bất kỳ sự hiểu nhầm hoặc giải thích sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->