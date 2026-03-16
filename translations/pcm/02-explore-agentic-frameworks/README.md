[![Explorin AI Agent Frameworks](../../../translated_images/pcm/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Tap di picture up top make you watch di video for dis lesson)_

# Make we explore AI Agent Frameworks

AI agent frameworks na software platforms wey dem design to make e easy to create, deploy, and manage AI agents. Dem frameworks dey give developers pre-built components, abstractions, and tools wey dey streamline how to build complex AI systems.

Dem frameworks dey help developers focus for di unique parts of dia applications by providing standard ways to handle common wahala wey dey for AI agent development. Dem dey boost scalability, accessibility, and efficiency when you dey build AI systems.

## Intro 

This lesson go cover:

- Wetin be AI Agent Frameworks and wetin dem fit make developers achieve?
- How teams fit use dem to quickly prototype, iterate, and improve dia agent capabilities?
- How dem frameworks and tools wey Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, and <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> take different?
- I fit integrate my existing Azure ecosystem tools direct, or I need standalone solutions?
- Wetin be Azure AI Agents service and how e dey help me?

## Learning goals

Di goals of dis lesson na to help you understand:

- Di role of AI Agent Frameworks for AI development.
- How to use AI Agent Frameworks build intelligent agents.
- Key capabilities wey AI Agent Frameworks dey enable.
- Di differences between AutoGen, Semantic Kernel, and Azure AI Agent Service.

## Wetin be AI Agent Frameworks and wetin dem make developers fit do?

Traditional AI Frameworks fit help you put AI inside your apps and make dem better for these ways:

- **Personalization**: AI fit analyze user behaviour and preferences to give personalized recommendations, content, and experiences.
Example: Streaming services like Netflix dey use AI to suggest movies and shows based on wetin person don watch before, make user engagement and satisfaction increase.
- **Automation and Efficiency**: AI fit automate repetitive tasks, streamline workflows, and improve operational efficiency.
Example: Customer service apps dey use AI-powered chatbots to handle common inquiries, reduce response times and free human agents for more complex mata.
- **Enhanced User Experience**: AI fit improve di overall user experience by giving intelligent features like voice recognition, natural language processing, and predictive text.
Example: Virtual assistants like Siri and Google Assistant dey use AI to understand and respond to voice commands, make am easier for users to interact with dia devices.

### E sweet no be so, why we still need AI Agent Framework?

AI Agent frameworks na more pass normal AI frameworks. Dem dem design make e possible to create intelligent agents wey fit interact with users, other agents, and di environment to achieve specific goals. These agents fit show autonomous behavior, make decisions, and adapt to changing conditions. Make we look some key capabilities wey AI Agent Frameworks dey enable:

- **Agent Collaboration and Coordination**: Make you fit create many AI agents wey fit work together, communicate, and coordinate to solve complex tasks.
- **Task Automation and Management**: Provide ways to automate multi-step workflows, task delegation, and dynamic task management among agents.
- **Contextual Understanding and Adaptation**: Give agents ability to understand context, adapt to changing environments, and make decisions based on real-time information.

So in short, agents dey allow you do more, carry automation go next level, and create smarter systems wey fit adapt and learn from dia environment.

## How to quickly prototype, iterate, and improve the agent’s capabilities?

This space dey move fast, but some things common for most AI Agent Frameworks fit help you quickly prototype and iterate—things like modular components, collaborative tools, and real-time learning. Make we break dem down:

- **Use Modular Components**: AI SDKs dey offer pre-built components like AI and Memory connectors, function calling using natural language or code plugins, prompt templates, and more.
- **Leverage Collaborative Tools**: Design agents get specific roles and tasks, make dem fit test and refine collaborative workflows.
- **Learn in Real-Time**: Put feedback loops wey agents go learn from interactions and change dia behaviour dynamically.

### Use Modular Components

SDKs like Microsoft Semantic Kernel and LangChain dey give pre-built components like AI connectors, prompt templates, and memory management.

**How teams fit use these**: Teams fit quickly put together these components to make a workable prototype without starting from scratch, so dem fit do rapid experimentation and iteration.

**How e dey work for practice**: You fit use a pre-built parser to extract information from user input, a memory module to store and retrieve data, and a prompt generator to interact with users, all without to build these components from beginning.

**Example code**. Make we look examples how you fit use pre-built AI Connector with Semantic Kernel Python and .Net wey dey use auto-function calling make model respond to user input:

``` python
# Semantic Kernel Python Example

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Define one ChatHistory object wey go hold di talk talk context
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Define one sample plugin wey get di function to book travel
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Create di Kernel
kernel = Kernel()

# Add di sample plugin to di Kernel object
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Define di Azure OpenAI AI Connector
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Define di request settings wey go configure di model wit auto-function calling
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Make di request to di model for di given chat history and request settings
    # Di Kernel get di sample wey di model go request to invoke
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
    # Example AI Model Response: `Your flight to New York on January 1, 2025, don successfully book. Safe travels! ✈️🗽`

    # Add di model response to our chat history context
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

Wetin you fit see from dis example na how you fit use pre-built parser to extract key information from user input, like origin, destination, and date of a flight booking request. Dis modular approach make you fit focus on di high-level logic.

### Leverage Collaborative Tools

Frameworks like CrewAI, Microsoft AutoGen, and Semantic Kernel dey make am easy to create multiple agents wey fit work together.

**How teams fit use these**: Teams fit design agents with specific roles and tasks, make dem test and refine collaborative workflows and improve overall system efficiency.

**How e dey work for practice**: You fit create team of agents where each agent get specialized function, like data retrieval, analysis, or decision-making. These agents fit communicate and share information to achieve one goal, like answer user query or finish a task.

**Example code (AutoGen)**:

```python
# de create agents, den create one round robin schedule wey dem fit work together, for dis case na in order

# Data Retrieval Agent
# Data Analysis Agent
# Decision Making Agent

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

# conversation go finish when user talk "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Use asyncio.run(...) wen you dey run for script.
await Console(stream)
```

Wetin you see for di code before na how you fit create task wey involve multiple agents wey dey work together to analyze data. Each agent dey perform specific function, and di task dey execute by coordinating agents to get di wanted result. By creating dedicated agents with specialized roles, you fit improve task efficiency and performance.

### Learn in Real-Time

Advanced frameworks dey provide capabilities for real-time context understanding and adaptation.

**How teams fit use these**: Teams fit implement feedback loops wey agents go learn from interactions and adjust dia behaviour dynamically, leading to continuous improvement and refinement of capabilities.

**How e dey work for practice**: Agents fit analyze user feedback, environmental data, and task outcomes to update dia knowledge base, adjust decision-making algorithms, and improve performance over time. Dis iterative learning process make agents fit adapt to changing conditions and user preferences, and so improve overall system effectiveness.

## Wetin be di differences between AutoGen, Semantic Kernel and Azure AI Agent Service?

Plenty ways dey to compare these frameworks, but make we look some key differences for design, capabilities, and target use cases:

## AutoGen

AutoGen na open-source framework wey Microsoft Research's AI Frontiers Lab develop. E focus on event-driven, distributed *agentic* applications, make multiple LLMs and SLMs, tools, and advanced multi-agent design patterns possible.

AutoGen build around di core idea of agents, wey be autonomous entities wey fit perceive dia environment, make decisions, and take actions to reach specific goals. Agents dey communicate through asynchronous messages, make dem fit work independently and in parallel, wey dey improve system scalability and responsiveness.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agents dem base for di actor model</a>. According to Wikipedia, an actor na _di basic building block of concurrent computation. In response to a message e receive, an actor fit: make local decisions, create more actors, send more messages, and decide how e go respond to di next message wey e receive_.

**Use Cases**: Automating code generation, data analysis tasks, and building custom agents for planning and research functions.

Here some important core concepts of AutoGen:

- **Agents**. An agent na software entity wey:
  - **Communicates via messages**, these messages fit be synchronous or asynchronous.
  - **Maintains its own state**, wey fit change by incoming messages.
  - **Performs actions** in response to received messages or changes for im state. These actions fit change di agent’s state and produce external effects, like updating message logs, sending new messages, executing code, or making API calls.
    
  Here you get small code snippet wey show how you fit create your own agent with Chat capabilities:

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
    
    For di previous code, `MyAgent` don create and e inherit from `RoutedAgent`. E get message handler wey dey print di content of di message and then send response using di `AssistantAgent` delegate. Especially notice how we assign to `self._delegate` one instance of `AssistantAgent` wey be pre-built agent wey fit handle chat completions.


    Make we tell AutoGen about dis agent type and start di program next:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Begin to process message dem for background.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    For di previous code agents register with di runtime and then message send go the agent wey produce di following output:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multi agents**. AutoGen dey support creation of many agents wey fit work together to solve complex tasks. Agents fit communicate, share information, and coordinate dia actions to solve problems more efficiently. To create multi-agent system, you fit define different types of agents with specialized functions and roles, like data retrieval, analysis, decision-making, and user interaction. Make we see how such creation fit be so we go get sense of am:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Example of to declare Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Using topic kain as di agent kain.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # di oda declaration dem don short for make am easy

    # Group chat
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

    For di previous code we get `GroupChatManager` wey register with di runtime. Dis manager na di one wey coordinate di interactions between different types of agents, like writers, illustrators, editors, and users.

- **Agent Runtime**. Di framework dey provide runtime environment, wey enable communication between agents, manage dia identities and lifecycles, and enforce security and privacy boundaries. E mean say you fit run agents for secure and controlled environment, make sure dem fit interact safely and efficiently. Two runtimes dey important:
  - **Stand-alone runtime**. Na good choice for single-process applications where all agents write for same programming language and run for same process. Here an illustration how e dey work:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Stand-alone runtime</a>   
Application stack

    *agents dey communicate via messages through di runtime, and di runtime dey manage di lifecycle of agents*

  - **Distributed agent runtime**, good for multi-process applications where agents fit be implemented for different programming languages and run on different machines. Here one illustration how e dey work:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distributed runtime</a>

## Semantic Kernel + Agent Framework

Semantic Kernel na enterprise-ready AI Orchestration SDK. E get AI and memory connectors, together with an Agent Framework.

Make we first cover some core components:

- **AI Connectors**: Na di interface wey connect external AI services and data sources for use for both Python and C#.

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

    Here you get simple example how you fit create kernel and add chat completion service. Semantic Kernel dey create connection to external AI service, for this case, Azure OpenAI Chat Completion.

- **Plugins**: Dem dey encapsulate functions wey application fit use. Both ready-made plugins dey and custom ones you fit create. Related concept na "prompt functions." Instead of to give natural language cues for function invocation, you broadcast certain functions to di model. Based on di current chat context, di model fit choose to call one of these functions to finish request or query. Here example:

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

    Here, you first get template prompt `skPrompt` wey leave room for user to input text, `$userInput`. Then you create kernel function `SummarizeText` and import am into kernel with plugin name `SemanticFunctions`. Note di name of di function wey help Semantic Kernel know wetin di function dey do and wen e suppose call am.

- **Native function**: E still get native functions wey di framework fit call direct to carry out task. Here example of such function wey dey retrieve content from file:

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

- **Memory**:  E abstract and simplify context management for AI apps. Idea with memory na say dis na wetin di LLM suppose know. You fit store dis information for vector store wey fit be in-memory database or vector database or something like that. Here example of very simplified scenario where *facts* dey add to memory:

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

    Dees facts den dey store for di memory collection `SummarizedAzureDocs`. Na very simplified example dis, but you fit see how you fit store information for di memory make the LLM fit use am.

So na di basics of the Semantic Kernel framework, wetin about the Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service na more recent addition wey dem introduce for Microsoft Ignite 2024. E dey allow development and deployment of AI agents wey get more flexible models, like to call open-source LLMs direct like Llama 3, Mistral, and Cohere.

Azure AI Agent Service dey provide stronger enterprise security mechanisms and data storage methods, so e make am suitable for enterprise applications. 

E dey work out-of-the-box with multi-agent orchestration frameworks like AutoGen and Semantic Kernel.

This service dey currently for Public Preview and e support Python and C# for building agents.

Using Semantic Kernel Python, we fit create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Define one sample plugin for di sample
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
        # Make agent definition
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Make di AzureAI Agent use di defined client and agent definition
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Make one thread to keep di conversation
        # If no thread dey, one new thread go
        # dey made and return wit di first response
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
                # Call di agent for di thread wey dem specify
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

### Di main concepts

Azure AI Agent Service get di following core concepts:

- **Agent**. Azure AI Agent Service dey integrate with Microsoft Foundry. Inside AI Foundry, an AI Agent dey act as a "smart" microservice wey fit be used to answer questions (RAG), perform actions, or completely automate workflows. E dey do dis by joining di power of generative AI models with tools wey allow am to access and interact with real-world data sources. Here na example of an agent:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    For dis example, dem create agent with model `gpt-4o-mini`, name `my-agent`, and instructions `You are helpful agent`. The agent get tools and resources to do code interpretation tasks.

- **Thread and messages**. Thread na another important concept. E represent conversation or interaction between an agent and a user. Threads fit dey used to track di progress of conversation, store context information, and manage di state of di interaction. Here na example of a thread:

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

    For di previous code, dem create thread. Afterwards, dem send message to di thread. By calling `create_and_process_run`, dem ask di agent to perform work on di thread. Finally, dem fetch and log di messages to see di agent response. Di messages show di progress of di conversation between di user and di agent. E still important to sabi say di messages fit be of different types like text, image, or file — for example di agent work fit produce an image or a text response. As developer, you fit use dis information to further process di response or present am to di user.

- **Integrates with other AI frameworks**. Azure AI Agent service fit interact with other frameworks like AutoGen and Semantic Kernel, wey mean say you fit build part of your app for one of these frameworks and for example use di Agent service as an orchestrator, or you fit build everything inside di Agent service.

**Use Cases**: Azure AI Agent Service design for enterprise applications wey need secure, scalable, and flexible AI agent deployment.

## Wetin be the difference between these frameworks?
 
E fit sound like plenty overlap dey between these frameworks, but get some key differences for their design, capabilities, and target use cases:
 
- **AutoGen**: Na experimentation framework wey dey focus on leading-edge research on multi-agent systems. E be the best place to experiment and prototype sophisticated multi-agent systems.
- **Semantic Kernel**: Na production-ready agent library for building enterprise agentic applications. E focus on event-driven, distributed agentic applications, enabling multiple LLMs and SLMs, tools, and single/multi-agent design patterns.
- **Azure AI Agent Service**: Na platform and deployment service for Azure Foundry wey dey for agents. E offer connectivity to services wey Azure Foundry support like Azure OpenAI, Azure AI Search, Bing Search and code execution.
 
Still no sure which one to choose?

### Use Cases
 
Make we see if we fit help you by going through some common use cases:
 
> Q: I dey experiment, dey learn and dey build proof-of-concept agent applications, and I want make I fit build and experiment quick-quick
>

>A: AutoGen go be good choice for dis scenario, because e dey focus on event-driven, distributed agentic applications and e support advanced multi-agent design patterns.

> Q: Wetin make AutoGen better choice pass Semantic Kernel and Azure AI Agent Service for dis use case?
>
> A: AutoGen specially design for event-driven, distributed agentic applications, so e well-suited for automating code generation and data analysis tasks. E provide di necessary tools and capabilities to build complex multi-agent systems efficiently.

>Q: E dey sound like Azure AI Agent Service fit also work here, e get tools for code generation and more?

>
> A: Yes, Azure AI Agent Service na platform service for agents and e add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. E make am easy to build your agents for the Foundry Portal and deploy dem at scale.
 
> Q: I still confused, just give me one option
>
> A: Good choice be to build your application for Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. Dis approach allow you to easily persist your agents while you dey leverage di power to build multi-agent systems inside Semantic Kernel. Additionally, Semantic Kernel get connector for AutoGen, which make am easy to use both frameworks together.
 
Make we summarize di key differences for a table:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Event-driven, distributed agentic applications | Agents, Personas, Functions, Data | Code generation, data analysis tasks |
| Semantic Kernel | Understanding and generating human-like text content | Agents, Modular Components, Collaboration | Natural language understanding, content generation |
| Azure AI Agent Service | Flexible models, enterprise security, Code generation, Tool calling | Modularity, Collaboration, Process Orchestration | Secure, scalable, and flexible AI agent deployment |

Wetin be di ideal use case for each of these frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

Di answer na yes — you fit integrate your existing Azure ecosystem tools directly, especially with Azure AI Agent Service, because dem build am to work seamlessly with other Azure services. You fit, for example, integrate Bing, Azure AI Search, and Azure Functions. Dem still get deep integration with Microsoft Foundry.

For AutoGen and Semantic Kernel, you fit also integrate with Azure services, but e fit require say you call the Azure services from your code. Another way na to use di Azure SDKs to interact with Azure services from your agents. Additionally, like we mention before, you fit use Azure AI Agent Service as orchestrator for your agents wey you build inside AutoGen or Semantic Kernel, wey go give easy access to di Azure ecosystem.

## Sample Codes

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Join di [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) make you fit meet other learners, attend office hours and get your AI Agents questions answered.

## References

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel and AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## Previous Lesson

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Disclaimer:
Di document don translate by AI translation service [Co-op Translator] (https://github.com/Azure/co-op-translator). We dey try make am correct, but abeg note say automated translations fit get errors or inaccuracies. Di original document for im native language suppose be di authoritative source. If na important information, better make professional human translator check am. We no dey liable for any misunderstandings or misinterpretations wey fit come from the use of this translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->