[![如何设计优秀的 AI 代理](../../../translated_images/zh-CN/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(点击上方图片查看本课视频)_

# 工具使用设计模式

工具很有趣，因为它们允许 AI 代理拥有更广泛的能力范围。代理不仅限于执行一组有限的动作，通过增加工具，代理现在可以执行更广泛的动作。在本章中，我们将介绍工具使用设计模式，该模式描述了 AI 代理如何使用特定工具来实现其目标。

## 介绍

在本课中，我们将回答以下问题：

- 什么是工具使用设计模式？
- 它适用于哪些使用场景？
- 实现该设计模式需要哪些元素/构建块？
- 使用工具使用设计模式构建可信 AI 代理时有哪些特殊考虑？

## 学习目标

学完本课后，您将能够：

- 定义工具使用设计模式及其目的。
- 识别适用工具使用设计模式的使用场景。
- 理解实现该设计模式所需的关键元素。
- 认识使用该设计模式保证 AI 代理可信性的相关考虑。

## 什么是工具使用设计模式？

**工具使用设计模式** 专注于赋予大语言模型（LLM）与外部工具交互以实现特定目标的能力。工具是代理可以执行的代码，用以完成动作。工具既可以是诸如计算器这样简单的函数，也可以是调用第三方服务的 API，如股票价格查询或天气预报。在 AI 代理的上下文中，工具被设计成由代理响应**模型生成的函数调用**来执行。

## 它适用于哪些使用场景？

AI 代理可以利用工具完成复杂任务、检索信息或做出决策。工具使用设计模式常用于需要动态与外部系统交互的场景，比如数据库、网络服务或代码解释器。该能力适用于多种使用场景，包括：

- **动态信息检索：**代理可以查询外部 API 或数据库以获取最新数据（例如，查询 SQLite 数据库进行数据分析，获取股票价格或天气信息）。
- **代码执行与解释：**代理可以执行代码或脚本以解决数学问题、生成报告或进行模拟。
- **工作流自动化：**通过集成任务调度器、邮箱服务或数据管道等工具，自动化重复或多步骤的工作流程。
- **客户支持：**代理可以与客户关系管理系统（CRM）、工单平台或知识库交互以解决用户问题。
- **内容生成与编辑：**代理可以利用语法检查、文本摘要或内容安全评估等工具辅助内容创作任务。

## 实现工具使用设计模式需要哪些元素/构建块？

这些构建块使得 AI 代理能够执行多种任务。下面是实现工具使用设计模式所需的关键元素：

- **函数/工具模式定义**：对可用工具的详细定义，包括函数名、目的、必需参数和预期输出。这些模式使 LLM 能理解可用工具及如何构建有效请求。
- **函数执行逻辑**：根据用户意图和对话上下文决定何时以及如何调用工具。这可能包括规划模块、路由机制或动态决定工具使用的条件流程。
- **消息处理系统**：管理用户输入、LLM 响应、工具调用及工具输出之间的对话流。
- **工具集成框架**：连接代理与各类工具的基础设施，无论是简单函数还是复杂外部服务。
- **错误处理与验证**：处理工具执行失败、验证参数和应对意外响应的机制。
- **状态管理**：跟踪对话上下文、之前的工具交互及持久数据，确保多轮交互中的一致性。

接下来，我们详细介绍函数/工具调用。

### 函数/工具调用

函数调用是使大型语言模型（LLM）与工具交互的主要方式。通常你会看到“函数”和“工具”交替使用，因为“函数”（可复用代码块）就是代理用以完成任务的“工具”。为了调用函数代码，LLM 必须将用户请求与函数描述进行匹配。为此，会将包含所有可用函数描述的模式发送给 LLM，LLM 选择最合适的函数执行任务，并返回其名称和参数。所选函数随后被调用，其响应发送回 LLM，LLM 利用该信息回复用户请求。

开发者实现代理函数调用时需要：

1. 支持函数调用的 LLM 模型
2. 包含函数描述的模式
3. 每个函数的实现代码

以下以获取某城市当前时间的示例说明：

1. **初始化支持函数调用的 LLM：**

    并非所有模型都支持函数调用，确认所用 LLM 支持是重要步骤。<a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> 支持函数调用。我们可以先启动 Azure OpenAI 客户端。

    ```python
    # 初始化 Azure OpenAI 客户端
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **创建函数模式：**

    接下来定义一个 JSON 格式的模式，包含函数名、函数功能描述及参数名与描述。然后将该模式与用户请求（例如查询旧金山时间）一并传给先前创建的客户端。重要的是要注意，返回的是**工具调用**，而非问题的最终答案。正如前文所述，LLM 返回其选定的函数名和传递给函数的参数。

    ```python
    # 供模型读取的函数描述
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
  
    # 初始用户消息
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # 第一次API调用：请求模型使用该功能
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # 处理模型的响应
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **实现函数代码：**

    既然 LLM 选择了要执行的函数，接下来就需实现并执行完成任务的代码。我们用 Python 来实现获取当前时间的功能，同时需要编写代码从 response_message 中提取函数名和参数，以获取最终结果。

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
     # 处理函数调用
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
  
      # 第二次API调用：获取模型的最终响应
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

函数调用是大多数（如果不是全部）代理工具使用设计的核心，但从零实现可能具有挑战性。
正如我们在[第 2 课](../../../02-explore-agentic-frameworks)所学，agentic 框架为我们提供了预构建构建块来实现工具使用。

## 使用 Agentic 框架的工具使用示例

以下是使用不同 agentic 框架实现工具使用设计模式的示例：

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> 是面向 .NET、Python 和 Java 开发者的大语言模型（LLM）开源 AI 框架。它通过所谓的<a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">序列化</a>自动描述您的函数及其参数，从而简化了函数调用的使用过程。它还处理模型与代码之间的来回通信。使用比如 Semantic Kernel 这类 agentic 框架的另一个优势是，您可以访问预构建的工具，如<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">文件搜索</a>和<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">代码解释器</a>。

下图展示了 Semantic Kernel 中函数调用的流程：

![function calling](../../../translated_images/zh-CN/functioncalling-diagram.a84006fc287f6014.webp)

在 Semantic Kernel 中，函数/工具称为<a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">插件</a>。我们可以将前面看到的 `get_current_time` 函数转换成一个插件，将其封装成类及方法。我们还可以导入 `kernel_function` 装饰器，为函数添加描述。当用 GetCurrentTimePlugin 创建 kernel 时，kernel 会自动序列化函数及其参数，同时生成发送给 LLM 的模式。

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

# 创建内核
kernel = Kernel()

# 创建插件
get_current_time_plugin = GetCurrentTimePlugin(location)

# 将插件添加到内核
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> 是一款较新的 agentic 框架，旨在帮助开发者安全地构建、部署和扩展高质量、可扩展的 AI 代理，无需管理底层计算与存储资源。它对企业应用尤其有用，因为它是一个具有企业级安全性的完全托管服务。

与直接使用 LLM API 开发相比，Azure AI Agent Service 的优势包括：

- 自动调用工具 —— 无需解析工具调用、执行工具和处理响应；这些全部由服务器端完成
- 安全管理数据 —— 不必自己管理对话状态，可依赖线程跟踪所需信息
- 开箱即用的工具 —— 提供与数据源交互的工具，如 Bing、Azure AI Search 和 Azure Functions

Azure AI Agent Service 中可用的工具可分为两类：

1. 知识工具：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">结合 Bing 搜索进行基础检索</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">文件搜索</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI 搜索</a>

2. 动作工具：
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">函数调用</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">代码解释器</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI 定义的工具</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

代理服务允许我们将这些工具组合成一个 `工具集`。它还利用 `线程` 跟踪特定对话的消息历史。

假设您是 Contoso 公司的销售代理，想开发一个能够回答销售数据相关问题的对话代理。

下图展示了如何使用 Azure AI Agent Service 分析销售数据：

![Agentic Service In Action](../../../translated_images/zh-CN/agent-service-in-action.34fb465c9a84659e.webp)

要使用服务中的任意工具，我们可以创建客户端，并定义单个工具或工具集。以下 Python 代码展示了如何实践实现。LLM 能查看工具集，并根据用户请求决定调用用户创建的函数 `fetch_sales_data_using_sqlite_query` 还是预构建的代码解释器。

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query 函数，可以在 fetch_sales_data_functions.py 文件中找到。
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# 初始化工具集
toolset = ToolSet()

# 使用 fetch_sales_data_using_sqlite_query 函数初始化函数调用代理并将其添加到工具集
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# 初始化代码解释器工具并将其添加到工具集。
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## 使用工具使用设计模式构建可信 AI 代理的特殊考虑？

LLM 动态生成的 SQL 常见关注点是安全性，尤其是 SQL 注入风险或恶意操作（如删除或篡改数据库）。虽然这些担忧合理，但通过适当配置数据库访问权限可有效缓解。大多数数据库需配置为只读权限。对于 PostgreSQL 或 Azure SQL 等数据库服务，应用应被分配只读（SELECT）角色。

在安全环境中运行应用可以进一步增强保护。在企业场景中，数据通常会自运营系统中抽取并转换到只读数据库或数据仓库，采用用户友好模式。这种方式确保数据安全，优化性能和可访问性，并且应用拥有受限的只读访问权限。

## 示例代码
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## 对工具使用设计模式有更多疑问吗？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，与其他学习者交流，参加办公时间，并解答您的 AI 代理问题。

## 其他资源

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI 代理服务研讨会</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso 创意写作多代理研讨会</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">语义内核函数调用教程</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">语义内核代码解释器</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen 工具</a>

## 上一课

[理解代理设计模式](../03-agentic-design-patterns/README.md)

## 下一课

[代理 RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免责声明**：
本文件由人工智能翻译服务 [Co-op Translator](https://github.com/Azure/co-op-translator) 翻译完成。虽然我们力求准确，但请注意，自动翻译可能包含错误或不准确之处。原始语言的文档应被视为权威版本。对于重要信息，建议采用专业人工翻译。本公司不对因使用本翻译而产生的任何误解或误释承担责任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->