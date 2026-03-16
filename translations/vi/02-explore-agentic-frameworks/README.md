[![Khám phá Khung Tác nhân AI](../../../translated_images/vi/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Nhấp vào hình ảnh ở trên để xem video của bài học này)_

# Khám phá các Khung Tác nhân AI

Khung tác nhân AI là các nền tảng phần mềm được thiết kế để đơn giản hóa việc tạo, triển khai và quản lý các tác nhân AI. Các khung này cung cấp cho nhà phát triển các thành phần, trừu tượng và công cụ đã được xây dựng sẵn giúp tinh giản việc phát triển các hệ thống AI phức tạp.

Những khung này giúp nhà phát triển tập trung vào các khía cạnh độc đáo của ứng dụng bằng cách cung cấp các phương pháp tiêu chuẩn hóa cho những thách thức phổ biến trong phát triển tác nhân AI. Chúng nâng cao khả năng mở rộng, tính tiếp cận và hiệu quả trong việc xây dựng hệ thống AI.

## Giới thiệu 

Bài học này sẽ bao gồm:

- Khung Tác nhân AI là gì và chúng cho phép nhà phát triển đạt được những gì?
- Các đội có thể sử dụng chúng như thế nào để nhanh chóng nguyên mẫu, lặp lại và cải thiện khả năng của tác nhân?
- Sự khác biệt giữa các khung và công cụ do Microsoft tạo ra <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, và <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> là gì?
- Tôi có thể tích hợp trực tiếp các công cụ trong hệ sinh thái Azure hiện có của mình, hay tôi cần các giải pháp độc lập?
- Dịch vụ Azure AI Agents là gì và điều này giúp tôi như thế nào?

## Mục tiêu học tập

Mục tiêu của bài học này là giúp bạn hiểu:

- Vai trò của các Khung Tác nhân AI trong phát triển AI.
- Cách tận dụng Khung Tác nhân AI để xây dựng các tác nhân thông minh.
- Các năng lực chính được kích hoạt bởi Khung Tác nhân AI.
- Sự khác biệt giữa AutoGen, Semantic Kernel và Azure AI Agent Service.

## Khung Tác nhân AI là gì và chúng cho phép nhà phát triển làm gì?

Các Khung AI truyền thống có thể giúp bạn tích hợp AI vào ứng dụng và làm cho các ứng dụng này tốt hơn theo các cách sau:

- **Cá nhân hóa**: AI có thể phân tích hành vi và sở thích người dùng để cung cấp đề xuất, nội dung và trải nghiệm được cá nhân hóa.
Ví dụ: Các dịch vụ phát trực tuyến như Netflix sử dụng AI để gợi ý phim và chương trình dựa trên lịch sử xem, tăng cường tương tác và sự hài lòng của người dùng.
- **Tự động hóa và Hiệu quả**: AI có thể tự động hóa các tác vụ lặp đi lặp lại, hợp lý hóa quy trình làm việc và cải thiện hiệu quả vận hành.
Ví dụ: Các ứng dụng dịch vụ khách hàng sử dụng chatbot hỗ trợ AI để xử lý các yêu cầu phổ biến, giảm thời gian phản hồi và giải phóng nhân viên con người cho những vấn đề phức tạp hơn.
- **Cải thiện Trải nghiệm Người dùng**: AI có thể nâng cao trải nghiệm tổng thể bằng cách cung cấp các tính năng thông minh như nhận dạng giọng nói, xử lý ngôn ngữ tự nhiên và gợi ý văn bản.
Ví dụ: Trợ lý ảo như Siri và Google Assistant sử dụng AI để hiểu và phản hồi lệnh thoại, giúp người dùng tương tác với thiết bị dễ dàng hơn.

### Nghe có vẻ hay đúng không, vậy tại sao chúng ta cần Khung Tác nhân AI?

Khung Tác nhân AI đại diện cho nhiều hơn chỉ là các khung AI thông thường. Chúng được thiết kế để cho phép tạo ra các tác nhân thông minh có thể tương tác với người dùng, các tác nhân khác và môi trường để đạt được các mục tiêu cụ thể. Những tác nhân này có thể thể hiện hành vi tự chủ, đưa ra quyết định và thích ứng với điều kiện thay đổi. Hãy xem một số năng lực chính mà Khung Tác nhân AI cung cấp:

- **Hợp tác và Phối hợp giữa các tác nhân**: Cho phép tạo nhiều tác nhân AI có thể làm việc cùng nhau, giao tiếp và phối hợp để giải quyết các nhiệm vụ phức tạp.
- **Tự động hóa và Quản lý tác vụ**: Cung cấp cơ chế để tự động hóa các quy trình đa bước, ủy quyền tác vụ và quản lý tác vụ động giữa các tác nhân.
- **Hiểu ngữ cảnh và Thích ứng**: Trang bị cho tác nhân khả năng hiểu ngữ cảnh, thích ứng với môi trường thay đổi và đưa ra quyết định dựa trên thông tin thời gian thực.

Tóm lại, các tác nhân cho phép bạn làm được nhiều hơn, đưa tự động hóa lên một tầm cao mới, tạo ra các hệ thống thông minh hơn có thể thích ứng và học hỏi từ môi trường của chúng.

## Làm thế nào để nhanh chóng nguyên mẫu, lặp lại và cải thiện khả năng của tác nhân?

Đây là một lĩnh vực phát triển nhanh, nhưng có một số yếu tố phổ biến trong hầu hết các Khung Tác nhân AI có thể giúp bạn nhanh chóng nguyên mẫu và lặp lại, cụ thể là các thành phần mô-đun, công cụ hợp tác và học tập thời gian thực. Hãy đi sâu vào các phần này:

- **Sử dụng các Thành phần Mô-đun**: Các SDK AI cung cấp các thành phần đã xây dựng sẵn như bộ ghép nối AI và bộ nhớ, gọi hàm tự động bằng ngôn ngữ tự nhiên hoặc plugin mã, mẫu prompt, và nhiều hơn nữa.
- **Tận dụng Công cụ Hợp tác**: Thiết kế các tác nhân với vai trò và nhiệm vụ cụ thể, cho phép họ thử nghiệm và tinh chỉnh các luồng công việc hợp tác.
- **Học trong Thời gian Thực**: Triển khai các vòng phản hồi nơi tác nhân học từ tương tác và điều chỉnh hành vi một cách động.

### Sử dụng các Thành phần Mô-đun

Các SDK như Microsoft Semantic Kernel và LangChain cung cấp các thành phần đã được xây dựng sẵn như bộ ghép nối AI, mẫu prompt và quản lý bộ nhớ.

**Các đội có thể sử dụng chúng như thế nào**: Các đội có thể nhanh chóng ghép các thành phần này lại để tạo một nguyên mẫu có chức năng mà không phải bắt đầu từ đầu, cho phép thử nghiệm và lặp lại nhanh.

**Cách vận hành trong thực tế**: Bạn có thể sử dụng một parser đã xây dựng sẵn để trích xuất thông tin từ đầu vào của người dùng, một mô-đun bộ nhớ để lưu trữ và truy xuất dữ liệu, và một trình tạo prompt để tương tác với người dùng, tất cả mà không phải xây dựng các thành phần này từ đầu.

**Ví dụ mã**. Hãy xem ví dụ về cách bạn có thể sử dụng một Bộ ghép nối AI đã tạo sẵn với Semantic Kernel Python và .Net, sử dụng gọi hàm tự động để mô hình phản hồi đầu vào người dùng:

``` python
# Ví dụ Semantic Kernel bằng Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Định nghĩa một đối tượng ChatHistory để giữ bối cảnh cuộc trò chuyện
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Định nghĩa một plugin mẫu chứa chức năng đặt chuyến đi
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Tạo Kernel
kernel = Kernel()

# Thêm plugin mẫu vào đối tượng Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Định nghĩa AI Connector của Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Định nghĩa các cài đặt yêu cầu để cấu hình mô hình với gọi hàm tự động
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Gửi yêu cầu đến mô hình với lịch sử trò chuyện và cài đặt yêu cầu đã cho
    # Kernel chứa mẫu mà mô hình sẽ yêu cầu gọi thực thi
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # Ví dụ phản hồi mô hình AI: `Chuyến bay của bạn đến New York vào ngày 1 tháng 1 năm 2025 đã được đặt thành công. Chúc bạn hành trình an toàn! ✈️🗽`

    # Thêm phản hồi của mô hình vào bối cảnh lịch sử trò chuyện của chúng ta
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```

Điều bạn thấy từ ví dụ này là cách bạn có thể tận dụng một parser đã xây dựng sẵn để trích xuất thông tin chính từ đầu vào người dùng, chẳng hạn như nơi khởi hành, điểm đến và ngày của yêu cầu đặt vé máy bay. Cách tiếp cận mô-đun này cho phép bạn tập trung vào logic ở mức cao hơn.

### Tận dụng Công cụ Hợp tác

Các khung như CrewAI, Microsoft AutoGen, và Semantic Kernel hỗ trợ việc tạo nhiều tác nhân có thể làm việc cùng nhau.

**Các đội có thể sử dụng chúng như thế nào**: Các đội có thể thiết kế các tác nhân với vai trò và nhiệm vụ cụ thể, cho phép họ thử nghiệm và tinh chỉnh các luồng công việc hợp tác và cải thiện hiệu quả tổng thể của hệ thống.

**Cách vận hành trong thực tế**: Bạn có thể tạo một nhóm tác nhân, nơi mỗi tác nhân có chức năng chuyên biệt, chẳng hạn như truy xuất dữ liệu, phân tích hoặc ra quyết định. Những tác nhân này có thể giao tiếp và chia sẻ thông tin để đạt được một mục tiêu chung, chẳng hạn như trả lời câu hỏi của người dùng hoặc hoàn thành một nhiệm vụ.

**Ví dụ mã (AutoGen)**:

```python
# tạo các tác nhân, sau đó tạo một lịch vòng tròn nơi họ có thể làm việc cùng nhau, trong trường hợp này là theo thứ tự

# Tác nhân Truy xuất Dữ liệu
# Tác nhân Phân tích Dữ liệu
# Tác nhân Ra Quyết định

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# cuộc trò chuyện kết thúc khi người dùng nói "PHÊ DUYỆT"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Sử dụng asyncio.run(...) khi chạy trong một script.
await Console(stream)
```

Trong mã trước, bạn thấy cách tạo một nhiệm vụ liên quan đến nhiều tác nhân cùng làm việc để phân tích dữ liệu. Mỗi tác nhân thực hiện một chức năng cụ thể, và nhiệm vụ được thực thi bằng cách phối hợp các tác nhân để đạt được kết quả mong muốn. Bằng cách tạo các tác nhân chuyên dụng với vai trò chuyên môn hóa, bạn có thể cải thiện hiệu quả và hiệu suất của nhiệm vụ.

### Học trong Thời gian Thực

Các khung tiên tiến cung cấp khả năng hiểu và thích ứng ngữ cảnh theo thời gian thực.

**Các đội có thể sử dụng chúng như thế nào**: Các đội có thể triển khai các vòng phản hồi nơi tác nhân học từ các tương tác và điều chỉnh hành vi một cách động, dẫn đến cải thiện liên tục và tinh chỉnh khả năng.

**Cách vận hành trong thực tế**: Tác nhân có thể phân tích phản hồi của người dùng, dữ liệu môi trường và kết quả nhiệm vụ để cập nhật cơ sở tri thức, điều chỉnh các thuật toán ra quyết định và cải thiện hiệu suất theo thời gian. Quá trình học lặp đi lặp lại này cho phép tác nhân thích ứng với điều kiện và sở thích người dùng thay đổi, nâng cao hiệu quả tổng thể của hệ thống.

## Sự khác biệt giữa các khung AutoGen, Semantic Kernel và Azure AI Agent Service là gì?

Có nhiều cách để so sánh các khung này, nhưng hãy xem một số khác biệt chính về thiết kế, khả năng và các trường hợp sử dụng mục tiêu:

## AutoGen

AutoGen là một khung mã nguồn mở do AI Frontiers Lab của Microsoft Research phát triển. Nó tập trung vào các ứng dụng *agentic* phân tán, hướng sự kiện, cho phép nhiều LLM và SLM, công cụ và các mô hình thiết kế đa tác nhân tiên tiến.

AutoGen được xây dựng xung quanh khái niệm cốt lõi là tác nhân, đó là các thực thể tự chủ có thể nhận biết môi trường của chúng, đưa ra quyết định và thực hiện hành động để đạt được các mục tiêu cụ thể. Các tác nhân giao tiếp thông qua các thông điệp không đồng bộ, cho phép chúng hoạt động độc lập và song song, nâng cao khả năng mở rộng và khả năng phản hồi của hệ thống.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Các tác nhân dựa trên mô hình actor</a>. Theo Wikipedia, một actor là _khối xây dựng cơ bản của tính toán đồng thời. Để đáp lại một thông điệp nó nhận được, một actor có thể: đưa ra quyết định cục bộ, tạo ra nhiều actor hơn, gửi thêm thông điệp, và xác định cách phản hồi thông điệp tiếp theo nhận được_.

**Các trường hợp sử dụng**: Tự động hóa tạo mã, các tác vụ phân tích dữ liệu và xây dựng tác nhân tùy chỉnh cho các chức năng lập kế hoạch và nghiên cứu.

Dưới đây là một số khái niệm cốt lõi quan trọng của AutoGen:

- **Tác nhân**. Một tác nhân là một thực thể phần mềm mà:
  - **Giao tiếp qua thông điệp**, những thông điệp này có thể đồng bộ hoặc không đồng bộ.
  - **Duy trì trạng thái riêng của nó**, trạng thái này có thể bị thay đổi bởi các thông điệp đến.
  - **Thực hiện hành động** để đáp lại các thông điệp nhận được hoặc các thay đổi trong trạng thái của nó. Những hành động này có thể sửa đổi trạng thái của tác nhân và tạo ra các hiệu ứng bên ngoài, chẳng hạn như cập nhật nhật ký thông điệp, gửi thông điệp mới, thực thi mã hoặc gọi API.
    
  Ở đây bạn có một đoạn mã ngắn trong đó bạn tạo tác nhân của riêng bạn với khả năng Chat:

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
    
    Trong mã trước, `MyAgent` đã được tạo và kế thừa từ `RoutedAgent`. Nó có một bộ xử lý thông điệp in nội dung của thông điệp và sau đó gửi một phản hồi sử dụng đại biểu `AssistantAgent`. Đặc biệt lưu ý cách chúng ta gán cho `self._delegate` một thể hiện của `AssistantAgent` là một tác nhân được xây dựng sẵn có thể xử lý hoàn thành chat.


    Hãy để AutoGen biết về kiểu tác nhân này và khởi động chương trình tiếp theo:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Bắt đầu xử lý tin nhắn trong nền.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Trong mã trước các tác nhân được đăng ký với runtime và sau đó một thông điệp được gửi đến tác nhân dẫn đến đầu ra sau:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Đa tác nhân**. AutoGen hỗ trợ việc tạo nhiều tác nhân có thể làm việc cùng nhau để đạt được các nhiệm vụ phức tạp. Các tác nhân có thể giao tiếp, chia sẻ thông tin và phối hợp hành động của họ để giải quyết vấn đề hiệu quả hơn. Để tạo một hệ thống đa tác nhân, bạn có thể định nghĩa các loại tác nhân khác nhau với các chức năng và vai trò chuyên biệt, chẳng hạn như truy xuất dữ liệu, phân tích, ra quyết định và tương tác với người dùng. Hãy xem cách tạo một hệ như vậy trông như thế nào để chúng ta có thể hiểu:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Ví dụ về khai báo một Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Sử dụng loại chủ đề làm loại agent.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # các khai báo còn lại được rút ngắn để ngắn gọn

    # Trò chuyện nhóm
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```

    Trong mã trước chúng ta có một `GroupChatManager` được đăng ký với runtime. Trình quản lý này chịu trách nhiệm phối hợp các tương tác giữa các loại tác nhân khác nhau, chẳng hạn như người viết, họa sĩ minh họa, biên tập viên và người dùng.

- **Runtime cho Tác nhân**. Khung cung cấp một môi trường runtime, cho phép giao tiếp giữa các tác nhân, quản lý danh tính và vòng đời của chúng, và thực thi các ranh giới bảo mật và quyền riêng tư. Điều này có nghĩa là bạn có thể chạy các tác nhân của mình trong một môi trường an toàn và được kiểm soát, đảm bảo rằng chúng có thể tương tác một cách an toàn và hiệu quả. Có hai runtime đáng chú ý:
  - **Runtime độc lập**. Đây là một lựa chọn tốt cho các ứng dụng một tiến trình nơi tất cả tác nhân được triển khai trong cùng một ngôn ngữ lập trình và chạy trong cùng một tiến trình. Đây là một minh họa về cách nó hoạt động:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Runtime độc lập</a>   
Application stack

    *các tác nhân giao tiếp qua các thông điệp thông qua runtime, và runtime quản lý vòng đời của các tác nhân*

  - **Runtime tác nhân phân tán**, phù hợp cho các ứng dụng đa tiến trình nơi các tác nhân có thể được triển khai bằng các ngôn ngữ lập trình khác nhau và chạy trên các máy khác nhau. Đây là một minh họa về cách nó hoạt động:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Runtime phân tán</a>

## Semantic Kernel + Khung Tác nhân

Semantic Kernel là một SDK Điều phối AI sẵn sàng cho doanh nghiệp. Nó bao gồm các bộ ghép nối AI và bộ nhớ, cùng với một Khung Tác nhân.

Trước tiên hãy đề cập một số thành phần cốt lõi:

- **Bộ ghép nối AI**: Đây là một giao diện với các dịch vụ AI bên ngoài và nguồn dữ liệu để sử dụng cả trong Python và C#.

  ```python
  # Semantic Kernel Python
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  

    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```

    Ở đây bạn có một ví dụ đơn giản về cách bạn có thể tạo một kernel và thêm một dịch vụ hoàn thành chat. Semantic Kernel tạo một kết nối tới một dịch vụ AI bên ngoài, trong trường hợp này là Azure OpenAI Chat Completion.

- **Plugin**: Chúng đóng gói các hàm mà một ứng dụng có thể sử dụng. Có cả plugin sẵn sàng và plugin tùy chỉnh mà bạn có thể tạo. Một khái niệm liên quan là "prompt functions." Thay vì cung cấp các gợi ý ngôn ngữ tự nhiên để gọi hàm, bạn phát sóng một số hàm nhất định tới mô hình. Dựa trên ngữ cảnh chat hiện tại, mô hình có thể chọn gọi một trong các hàm này để hoàn thành một yêu cầu hoặc truy vấn. Đây là một ví dụ:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```

    Ở đây, bạn đầu tiên có một mẫu prompt `skPrompt` để người dùng nhập văn bản, `$userInput`. Sau đó bạn tạo hàm kernel `SummarizeText` và sau đó nhập nó vào kernel với tên plugin `SemanticFunctions`. Lưu ý tên của hàm giúp Semantic Kernel hiểu hàm làm gì và khi nào nó nên được gọi.

- **Hàm gốc**: Cũng có các hàm gốc mà khung có thể gọi trực tiếp để thực hiện nhiệm vụ. Đây là một ví dụ về một hàm như vậy lấy nội dung từ một tệp:

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```

- **Bộ nhớ**: Trừu tượng hóa và đơn giản hóa quản lý ngữ cảnh cho các ứng dụng AI. Ý tưởng với bộ nhớ là đây là những điều mà LLM nên biết. Bạn có thể lưu trữ thông tin này trong một kho vector, vốn trở thành một cơ sở dữ liệu trong bộ nhớ hoặc một cơ sở dữ liệu vector hoặc tương tự. Đây là một ví dụ về một kịch bản rất đơn giản nơi *sự thật* được thêm vào bộ nhớ:

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```

    Những thông tin này sau đó được lưu trong bộ sưu tập bộ nhớ `SummarizedAzureDocs`. Đây là một ví dụ rất đơn giản, nhưng bạn có thể thấy cách bạn có thể lưu thông tin trong bộ nhớ để LLM sử dụng.

Vậy là cơ bản về framework Semantic Kernel, còn về Agent Framework thì sao?

## Dịch vụ Azure AI Agent

Azure AI Agent Service là một bổ sung gần đây, được giới thiệu tại Microsoft Ignite 2024. Nó cho phép phát triển và triển khai các agent AI với các mô hình linh hoạt hơn, chẳng hạn như gọi trực tiếp các LLM mã nguồn mở như Llama 3, Mistral và Cohere.

Azure AI Agent Service cung cấp các cơ chế bảo mật doanh nghiệp mạnh mẽ và phương thức lưu trữ dữ liệu, làm cho nó phù hợp cho các ứng dụng doanh nghiệp.

Nó hoạt động ngay lập tức với các framework điều phối đa-agent như AutoGen và Semantic Kernel.

Dịch vụ này hiện đang ở Public Preview và hỗ trợ Python và C# để xây dựng agent.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Định nghĩa một plugin mẫu cho ví dụ
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # Tạo định nghĩa tác nhân
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Tạo tác nhân AzureAI sử dụng client và định nghĩa tác nhân đã định nghĩa
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Tạo một luồng để giữ cuộc trò chuyện
        # Nếu không có luồng được cung cấp, một luồng mới sẽ được
        # tạo ra và trả về cùng với phản hồi ban đầu
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # Gọi tác nhân cho luồng được chỉ định
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### Các khái niệm cốt lõi

Azure AI Agent Service có các khái niệm cốt lõi sau:

- **Tác nhân**. Azure AI Agent Service tích hợp với Microsoft Foundry. Trong AI Foundry, một AI Agent đóng vai trò như một "microservice thông minh" có thể được dùng để trả lời câu hỏi (RAG), thực hiện hành động, hoặc tự động hóa hoàn toàn các quy trình công việc. Nó đạt được điều này bằng cách kết hợp sức mạnh của các mô hình sinh tạo với các công cụ cho phép truy cập và tương tác với các nguồn dữ liệu thực tế. Dưới đây là một ví dụ về một agent:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    In this example, an agent is created with the model `gpt-4o-mini`, a name `my-agent`, and instructions `You are helpful agent`. The agent is equipped with tools and resources to perform code interpretation tasks.

- **Chuỗi và tin nhắn**. Chuỗi là một khái niệm quan trọng khác. Nó đại diện cho một cuộc trò chuyện hoặc tương tác giữa agent và người dùng. Chuỗi có thể được dùng để theo dõi tiến trình của cuộc trò chuyện, lưu thông tin ngữ cảnh và quản lý trạng thái của tương tác. Dưới đây là một ví dụ về một chuỗi:

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    In the previous code, a thread is created. Thereafter, a message is sent to the thread. By calling `create_and_process_run`, the agent is asked to perform work on the thread. Finally, the messages are fetched and logged to see the agent's response. The messages indicate the progress of the conversation between the user and the agent. It's also important to understand that the messages can be of different types such as text, image, or file, that is the agents work has resulted in for example an image or a text response for example. As a developer, you can then use this information to further process the response or present it to the user.

- **Tích hợp với các framework AI khác**. Azure AI Agent service có thể tương tác với các framework khác như AutoGen và Semantic Kernel, điều này có nghĩa là bạn có thể xây dựng một phần ứng dụng của mình trong một trong các framework này và ví dụ sử dụng Agent service làm bộ điều phối hoặc bạn có thể xây dựng mọi thứ trong Agent service.

**Trường hợp sử dụng**: Azure AI Agent Service được thiết kế cho các ứng dụng doanh nghiệp cần triển khai agent AI an toàn, có khả năng mở rộng và linh hoạt.

## Sự khác biệt giữa các framework này là gì?
 
Có vẻ như có nhiều điểm chồng chéo giữa các framework này, nhưng có một số khác biệt then chốt về thiết kế, khả năng và mục tiêu sử dụng:
 
- **AutoGen**: Là một framework thử nghiệm tập trung vào nghiên cứu tiên phong về hệ thống đa-tác nhân. Đây là nơi tốt nhất để thử nghiệm và tạo nguyên mẫu các hệ thống đa-tác nhân phức tạp.
- **Semantic Kernel**: Là một thư viện agent sẵn sàng cho sản xuất để xây dựng các ứng dụng có tác nhân cho doanh nghiệp. Tập trung vào các ứng dụng tác nhân theo sự kiện, phân tán, cho phép nhiều LLM và SLM, công cụ, và các mẫu thiết kế đơn/đa-tác nhân.
- **Azure AI Agent Service**: Là một nền tảng và dịch vụ triển khai trong Azure Foundry dành cho các agent. Nó cung cấp kết nối tới các dịch vụ được hỗ trợ bởi Azure Foundry như Azure OpenAI, Azure AI Search, Bing Search và thực thi mã.
 
Vẫn chưa chắc chắn nên chọn cái nào?

### Trường hợp sử dụng
 
Hãy để chúng tôi giúp bạn bằng cách đi qua một vài trường hợp sử dụng phổ biến:
 
> Q: Tôi đang thử nghiệm, học và xây dựng các ứng dụng agent proof-of-concept, và tôi muốn có thể xây dựng và thử nghiệm nhanh chóng
>

>A: AutoGen sẽ là một lựa chọn tốt cho kịch bản này, vì nó tập trung vào các ứng dụng tác nhân phân tán theo hướng sự kiện và hỗ trợ các mẫu thiết kế đa-tác nhân nâng cao.

> Q: Điều gì làm AutoGen trở thành lựa chọn tốt hơn so với Semantic Kernel và Azure AI Agent Service cho trường hợp này?
>
> A: AutoGen được thiết kế đặc biệt cho các ứng dụng tác nhân phân tán theo hướng sự kiện, làm cho nó phù hợp để tự động hóa việc tạo mã và các tác vụ phân tích dữ liệu. Nó cung cấp các công cụ và khả năng cần thiết để xây dựng các hệ thống đa-tác nhân phức tạp một cách hiệu quả.

>Q: Nghe có vẻ Azure AI Agent Service cũng có thể làm được ở đây, nó có công cụ để tạo mã và nhiều thứ hơn?
 
>
> A: Đúng, Azure AI Agent Service là một dịch vụ nền tảng cho các agent và có các khả năng tích hợp sẵn cho nhiều mô hình, Azure AI Search, Bing Search và Azure Functions. Nó giúp bạn dễ dàng xây dựng agent trong Foundry Portal và triển khai ở quy mô.

> Q: Tôi vẫn bối rối, chỉ đưa cho tôi một lựa chọn thôi
>
> A: Một lựa chọn tuyệt vời là xây dựng ứng dụng của bạn trong Semantic Kernel trước, sau đó sử dụng Azure AI Agent Service để triển khai agent của bạn. Cách làm này cho phép bạn dễ dàng lưu trữ agent của mình đồng thời tận dụng sức mạnh để xây dựng hệ thống đa-tác nhân trong Semantic Kernel. Ngoài ra, Semantic Kernel có một connector trong AutoGen, giúp dễ dàng sử dụng cả hai framework cùng nhau.
 
Hãy tóm tắt những khác biệt chính trong một bảng:

| Framework | Mục tiêu | Khái niệm cốt lõi | Trường hợp sử dụng |
| --- | --- | --- | --- |
| AutoGen | Ứng dụng tác nhân phân tán, hướng sự kiện | Tác nhân, Nhân cách, Chức năng, Dữ liệu | Tạo mã, các tác vụ phân tích dữ liệu |
| Semantic Kernel | Hiểu và tạo nội dung văn bản giống con người | Tác nhân, Thành phần mô-đun, Hợp tác | Hiểu ngôn ngữ tự nhiên, tạo nội dung |
| Azure AI Agent Service | Mô hình linh hoạt, bảo mật doanh nghiệp, Tạo mã, Gọi công cụ | Tính mô-đun, Hợp tác, Điều phối quy trình | Triển khai agent AI an toàn, có khả năng mở rộng và linh hoạt |

What's the ideal use case for each of these frameworks?

## Tôi có thể tích hợp trực tiếp các công cụ trong hệ sinh thái Azure hiện có của mình, hay tôi cần các giải pháp độc lập?

Câu trả lời là có, bạn có thể tích hợp trực tiếp các công cụ trong hệ sinh thái Azure hiện có với Azure AI Agent Service đặc biệt, vì nó được xây dựng để làm việc liền mạch với các dịch vụ Azure khác. Ví dụ, bạn có thể tích hợp Bing, Azure AI Search và Azure Functions. Cũng có sự tích hợp sâu với Microsoft Foundry.

Đối với AutoGen và Semantic Kernel, bạn cũng có thể tích hợp với các dịch vụ Azure, nhưng có thể yêu cầu bạn phải gọi các dịch vụ Azure từ mã của mình. Một cách khác để tích hợp là sử dụng các SDK Azure để tương tác với dịch vụ Azure từ các agent của bạn. Ngoài ra, như đã đề cập, bạn có thể sử dụng Azure AI Agent Service làm bộ điều phối cho các agent được xây dựng trong AutoGen hoặc Semantic Kernel, điều này sẽ giúp truy cập hệ sinh thái Azure dễ dàng hơn.

## Mã mẫu

- Python: [Khung tác nhân](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Khung tác nhân](./code_samples/02-dotnet-agent-framework.md)

## Còn thắc mắc về các khung tác nhân AI?

Tham gia [Discord của Microsoft Foundry](https://aka.ms/ai-agents/discord) để gặp gỡ những người học khác, tham dự giờ hỗ trợ và nhận câu trả lời cho các câu hỏi về AI Agents của bạn.

## Tài liệu tham khảo

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Dịch vụ Azure Agent</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel và AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Khung tác nhân Semantic Kernel cho Python</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Khung tác nhân Semantic Kernel cho .Net</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Dịch vụ Azure AI Agent</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Sử dụng Azure AI Agent Service với AutoGen / Semantic Kernel để xây dựng giải pháp đa-tác nhân</a>

## Bài học trước

[Giới thiệu về Tác nhân AI và Trường hợp sử dụng](../01-intro-to-ai-agents/README.md)

## Bài học tiếp theo

[Hiểu các mẫu thiết kế agentic](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Miễn trừ trách nhiệm:
Tài liệu này đã được dịch bằng dịch vụ dịch thuật AI Co-op Translator (https://github.com/Azure/co-op-translator). Mặc dù chúng tôi cố gắng đảm bảo tính chính xác, xin lưu ý rằng các bản dịch tự động có thể chứa sai sót hoặc không chính xác. Văn bản gốc bằng ngôn ngữ ban đầu nên được coi là nguồn có thẩm quyền. Đối với các thông tin quan trọng, nên sử dụng bản dịch do chuyên gia/biên dịch viên chuyên nghiệp thực hiện. Chúng tôi không chịu trách nhiệm đối với bất kỳ sự hiểu lầm hoặc giải thích sai nào phát sinh từ việc sử dụng bản dịch này.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->