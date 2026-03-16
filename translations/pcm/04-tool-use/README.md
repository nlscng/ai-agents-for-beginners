[![How to Design Good AI Agents](../../../translated_images/pcm/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Click di image wey dey above to watch video for dis lesson)_

# Tool Use Design Pattern

Tools dey interesting because dem dey allow AI agents to get bigger range of things dem fit do. Instead make the agent get small set of actions wey e fit perform, if you add tool, the agent fit perform plenty actions now. For dis chapter, we go look the Tool Use Design Pattern, wey dey talk how AI agents fit use specific tools to achieve their goals.

## Introduction

For dis lesson, we wan answer these questions:

- Wetin be di tool use design pattern?
- Wetin be di use cases wey e fit apply for?
- Wetin be di elements/building blocks wey you need take implement di design pattern?
- Wetin be di special tins wey you go consider if you wan use Tool Use Design Pattern build AI agents wey people fit trust?

## Learning Goals

After you finish dis lesson, you go fit:

- Define di Tool Use Design Pattern and wetin e dey do.
- Identify use cases wey di Tool Use Design Pattern fit work for.
- Understand di important elements wey you need use implement di design pattern.
- Recognize tins wey you go consider to make sure say AI agents wey use dis design pattern dey trustworthy.

## Wetin be di Tool Use Design Pattern?

Di **Tool Use Design Pattern** dey focus on giving LLMs di ability to interact with outside tools to achieve particular goals. Tools na code wey agent fit run to perform actions. Tool fit be simple function like calculator, or e fit be API call to third-party service like check stock price or weather forecast. For AI agents matter, tools na to be run by agents when dem see **model-generated function calls**.

## Wetin be di use cases wey e fit apply for?

AI Agents fit use tools to complete hard tasks, find information, or take decisions. Di tool use design pattern dey mostly for situations wey need interaction with outside systems like databases, web services, or code interpreters. Dis ability dey useful for many different use cases like:

- **Dynamic Information Retrieval:** Agents fit ask outside APIs or databases to bring up-to-date data (e.g., ask SQLite database for data analysis, check stock prices or weather information).
- **Code Execution and Interpretation:** Agents fit run code or scripts to solve math problems, make reports, or do simulations.
- **Workflow Automation:** Automate repetitive or many-step workflows by joining tools like task schedulers, email services, or data pipelines.
- **Customer Support:** Agents fit interact with CRM systems, ticket platforms, or knowledge bases to solve user questions.
- **Content Generation and Editing:** Agents fit use tools like grammar checkers, text summarizers, or content safety checkers to help for content creation work.

## Wetin be di elements/building blocks wey you need take implement di tool use design pattern?

Dis building blocks go make AI agent fit perform many tasks. Make we look di key elements wey you need take implement di Tool Use Design Pattern:

- **Function/Tool Schemas**: Detailed definitions of available tools, including function name, purpose, required parameters, and expected outputs. These schemas enable the LLM to understand what tools are available and how to construct valid requests.

- **Function Execution Logic**: Governs how and when tools are invoked based on the user’s intent and conversation context. This may include planner modules, routing mechanisms, or conditional flows that determine tool usage dynamically.

- **Message Handling System**: Components wey dey manage di flow of conversation between user inputs, LLM responses, tool calls, and tool outputs.

- **Tool Integration Framework**: Infrastructure wey connect di agent to different tools, whether na simple functions or complex outside services.

- **Error Handling & Validation**: Mechanisms to handle tool failures, check parameters, and manage unexpected responses.

- **State Management**: Tracks conversation context, previous tool interactions, and persistent data to ensure consistency across multi-turn interactions.

Next, make we look Function/Tool Calling well well.

### Function/Tool Calling

Function calling na the main way wey we let Large Language Models (LLMs) interact with tools. You go often see 'Function' and 'Tool' used as if na di same because 'functions' (blocks of reusable code) na di 'tools' wey agents use do tasks. To run function code, LLM gats compare wetin user ask with di function description. To do dis, we send schema with descriptions of all di available functions to di LLM. Di LLM then choose di function wey best fit di task and return e name and arguments. Di chosen function go run, e answer go come back to LLM, wey go use am answer di user.

For developers to implement function calling for agents, you need:

1. LLM model wey support function calling
2. Schema wey get function descriptions
3. Code for each function described

Make we use example of getting current time for city show:

1. **Initialize LLM wey support function calling:**

    No all models support function calling, so e important to check say di LLM you dey use get am. <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> dey support function calling. We fit start by making Azure OpenAI client.

    ```python
    # Start di Azure OpenAI client
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Create Function Schema**:

    Next, we go define JSON schema wey get function name, description of wetin function dey do, and names plus descriptions of e parameters.
    We go pass dis schema to di client wey we make before, plus user request to find time for San Francisco. Di important thing to know be say di **tool call** na wetin go come out, **no be** final answer for di question. As we talk before, LLM go return di function name wey e choose for di task, along with di arguments wey e go pass run am.

    ```python
    # Function tori wey model go read
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
  
    # Di first message wey di user send
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Fes API call: Ask di model make e use di function
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Process di way di model respond
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Di function code wey e need to do di task:**

    Now say LLM don choose which function to run, di code to perform di task gats to be implemented and run.
    We fit write code to get current time for Python. We still go need write code wey go extract name and arguments from response_message to get di final result.

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
     # Handle function calls
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
  
      # Second API call: Make we get the last response from the model
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

Function Calling be di heart for most, if no be all, agent tool use design, but implementing am from scratch fit sometimes hard.
As we learn for [Lesson 2](../../../02-explore-agentic-frameworks), agentic frameworks dey provide pre-built building blocks to implement tool use.

## Tool Use Examples with Agentic Frameworks

Here be some examples how you fit implement Tool Use Design Pattern using different agentic frameworks:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> na open-source AI framework for .NET, Python, and Java developers wey dey work with Large Language Models (LLMs). E dey simplify how to use function calling by automatically describing your functions plus their parameters to di model through a process wey dem dey call <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serializing</a>. E also handle di back-and-forth communication between di model and your code. Another advantage of using agentic framework like Semantic Kernel na say e let you access pre-built tools like <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> and <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Dis diagram below dey show di process of function calling with Semantic Kernel:

![function calling](../../../translated_images/pcm/functioncalling-diagram.a84006fc287f6014.webp)

For Semantic Kernel functions/tools dem dey call <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. We fit turn di `get_current_time` function wey we see before into plugin by making am class with di function inside. We fit also import `kernel_function` decorator, wey dey carry description of di function. When you create kernel with GetCurrentTimePlugin, di kernel go automatically serialize di function and parameters, and make di schema to send to di LLM.

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

# Make di kernel
kernel = Kernel()

# Make di plugin
get_current_time_plugin = GetCurrentTimePlugin(location)

# Put di plugin inside di kernel
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> be newer agentic framework wey dey made to help developers build, deploy, and scale high-quality, and extensible AI agents without needing to manage di underlying compute and storage. E sabi well for enterprise applications because e be fully managed service wey get enterprise grade security.

When you compare am with developing direct with LLM API, Azure AI Agent Service get some better points, like:

- Automatic tool calling – no need to parse tool call, run di tool, and handle di response; all dis one na server-side work now
- Securely managed data – instead of you to manage your own conversation state, you fit depend on threads to store all di info wey you need
- Out-of-the-box tools – Tools wey you fit use take interact with your data sources, like Bing, Azure AI Search, and Azure Functions.

Tools wey dey available for Azure AI Agent Service fit divide into two:

1. Knowledge Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Action Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Di Agent Service make am possible to use all dis tools together as `toolset`. E also dey use `threads` to keep track of message history from one particular conversation.

Imagine say you be sales agent for company wey dem call Contoso. You want make you build conversational agent wey fit answer question about your sales data.

Dis image below dey show how you fit use Azure AI Agent Service analyze your sales data:

![Agentic Service In Action](../../../translated_images/pcm/agent-service-in-action.34fb465c9a84659e.webp)

To use any of dis tools with di service, we fit create client and define tool or toolset. To do am for real, we fit use dis Python code. LLM go fit look toolset and decide if e go use user created function, `fetch_sales_data_using_sqlite_query`, or pre-built Code Interpreter depend on wetin user ask.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query function wey you fit find inside fetch_sales_data_functions.py file.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Start toolset
toolset = ToolSet()

# Start function calling agent with the fetch_sales_data_using_sqlite_query function and add am to the toolset
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Start Code Interpreter tool and add am to the toolset.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Wetin be di special tins you go consider if you wan use Tool Use Design Pattern build AI agents wey people fit trust?

One common worry for SQL wey LLMs dey dynamically generate na security, especially di risk of SQL injection or bad actions like dropping or tampering with database. Even though dis worry dey correct, you fit protect well by setting database access permissions correct. For most databases, dis mean to configure di database as read-only. For database services like PostgreSQL or Azure SQL, the app suppose get read-only (SELECT) role.

To run di app for secure environment go even protect more. For enterprise level, data go usually extract and transform from operational systems into read-only database or data warehouse with user-friendly schema. Dis one dey ensure data dey secure, dey optimized for performance and access, and say di app get restricted read-only access.

## Sample Codes
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Get More Questions About How to Use Design Patterns for the Tool?

Come join [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) make you fit meet oda learners dem, enter office hours and get your AI Agents questions dem sabi answer for you.

## Additional Resources

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service Workshop</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer Multi-Agent Workshop</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel Function Calling Tutorial</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel Code Interpreter</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen Tools</a>

## Previous Lesson

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

## Next Lesson

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dis document dem translate am wit AI translation service wey dem call [Co-op Translator](https://github.com/Azure/co-op-translator). Even though we dey try make am correct, abeg sabi say automated translation fit get some mistakes or no too correct. Di original document wey e dey for e own language na di correct one you suppose trust. If na important matter, better make professional human translate am. We no go gree if person no understand or misinterpret anything wey come from this translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->