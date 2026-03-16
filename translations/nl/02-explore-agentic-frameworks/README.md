[![AI-agentframeworks verkennen](../../../translated_images/nl/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Klik op de afbeelding hierboven om de video van deze les te bekijken)_

# Explore AI Agent Frameworks

AI-agentframeworks zijn softwareplatforms die zijn ontworpen om het maken, implementeren en beheren van AI-agenten te vereenvoudigen. Deze frameworks bieden ontwikkelaars vooraf gebouwde componenten, abstracties en hulpmiddelen die de ontwikkeling van complexe AI-systemen stroomlijnen.

Deze frameworks helpen ontwikkelaars zich te concentreren op de unieke aspecten van hun toepassingen door gestandaardiseerde benaderingen te bieden voor veelvoorkomende uitdagingen in de ontwikkeling van AI-agenten. Ze bevorderen schaalbaarheid, toegankelijkheid en efficiëntie bij het bouwen van AI-systemen.

## Introduction 

This lesson will cover:

- What are AI Agent Frameworks and what do they enable developers to achieve?
- How can teams use these to quickly prototype, iterate, and improve their agent’s capabilities?
- What are the differences between the frameworks and tools created by Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, and <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?
- What is Azure AI Agents service and how is this helping me?

## Learning goals

The goals of this lesson are to help you understand:

- The role of AI Agent Frameworks in AI development.
- How to leverage AI Agent Frameworks to build intelligent agents.
- Key capabilities enabled by AI Agent Frameworks.
- The differences between AutoGen, Semantic Kernel, and Azure AI Agent Service.

## What are AI Agent Frameworks and what do they enable developers to do?

Traditional AI Frameworks can help you integrate AI into your apps and make these apps better in the following ways:

- **Personalization**: AI can analyze user behavior and preferences to provide personalized recommendations, content, and experiences.
Example: Streaming services like Netflix use AI to suggest movies and shows based on viewing history, enhancing user engagement and satisfaction.
- **Automation and Efficiency**: AI can automate repetitive tasks, streamline workflows, and improve operational efficiency.
Example: Customer service apps use AI-powered chatbots to handle common inquiries, reducing response times and freeing up human agents for more complex issues.
- **Enhanced User Experience**: AI can improve the overall user experience by providing intelligent features such as voice recognition, natural language processing, and predictive text.
Example: Virtual assistants like Siri and Google Assistant use AI to understand and respond to voice commands, making it easier for users to interact with their devices.

### That all sounds great right, so why do we need the AI Agent Framework?

AI Agent frameworks represent something more than just AI frameworks. They are designed to enable the creation of intelligent agents that can interact with users, other agents, and the environment to achieve specific goals. These agents can exhibit autonomous behavior, make decisions, and adapt to changing conditions. Let's look at some key capabilities enabled by AI Agent Frameworks:

- **Agent Collaboration and Coordination**: Enable the creation of multiple AI agents that can work together, communicate, and coordinate to solve complex tasks.
- **Task Automation and Management**: Provide mechanisms for automating multi-step workflows, task delegation, and dynamic task management among agents.
- **Contextual Understanding and Adaptation**: Equip agents with the ability to understand context, adapt to changing environments, and make decisions based on real-time information.

So in summary, agents allow you to do more, to take automation to the next level, to create more intelligent systems that can adapt and learn from their environment.

## How to quickly prototype, iterate, and improve the agent’s capabilities?

This is a fast-moving landscape, but there are some things that are common across most AI Agent Frameworks that can help you quickly prototype and iterate namely module components, collaborative tools, and real-time learning. Let's dive into these:

- **Use Modular Components**: AI SDKs offer pre-built components such as AI and Memory connectors, function calling using natural language or code plugins, prompt templates, and more.
- **Leverage Collaborative Tools**: Design agents with specific roles and tasks, enabling them to test and refine collaborative workflows.
- **Learn in Real-Time**: Implement feedback loops where agents learn from interactions and adjust their behavior dynamically.

### Use Modular Components

SDKs like Microsoft Semantic Kernel and LangChain offer pre-built components such as AI connectors, prompt templates, and memory management.

**How teams can use these**: Teams can quickly assemble these components to create a functional prototype without starting from scratch, allowing for rapid experimentation and iteration.

**How it works in practice**: You can use a pre-built parser to extract information from user input, a memory module to store and retrieve data, and a prompt generator to interact with users, all without having to build these components from scratch.

**Example code**. Let's look at examples of how you can use a pre-built AI Connector with Semantic Kernel Python and .Net that uses auto-function calling to have the model respond to user input:

``` python
# Semantic Kernel Python Voorbeeld

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definieer een ChatHistory-object om de context van het gesprek vast te leggen
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definieer een voorbeeldplugin die de functie bevat om reizen te boeken
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Maak de Kernel aan
kernel = Kernel()

# Voeg de voorbeeldplugin toe aan het Kernel-object
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definieer de Azure OpenAI AI Connector
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definieer de aanvraaginstellingen om het model te configureren met automatische functie-aanroep
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Doe het verzoek aan het model voor de gegeven chatgeschiedenis en aanvraaginstellingen
    # De Kernel bevat het voorbeeld dat het model zal verzoeken op te roepen
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
    # Voorbeeld AI Modelantwoord: `Uw vlucht naar New York op 1 januari 2025 is succesvol geboekt. Veilige reis! ✈️🗽`

    # Voeg het antwoord van het model toe aan onze chatgeschiedeniscontext
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

What you can see from this example is how you can leverage a pre-built parser to extract key information from user input, such as the origin, destination, and date of a flight booking request. This modular approach allows you to focus on the high-level logic.

### Leverage Collaborative Tools

Frameworks like CrewAI, Microsoft AutoGen, and Semantic Kernel facilitate the creation of multiple agents that can work together.

**How teams can use these**: Teams can design agents with specific roles and tasks, enabling them to test and refine collaborative workflows and improve overall system efficiency.

**How it works in practice**: You can create a team of agents where each agent has a specialized function, such as data retrieval, analysis, or decision-making. These agents can communicate and share information to achieve a common goal, such as answering a user query or completing a task.

**Example code (AutoGen)**:

```python
# agenten aanmaken, vervolgens een round robin schema maken waar ze samen kunnen werken, in dit geval op volgorde

# Gegevensophaalagent
# Gegevensanalyse-agent
# Besluitvormingsagent

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

# gesprek eindigt wanneer gebruiker "APPROVE" zegt
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Gebruik asyncio.run(...) bij het uitvoeren in een script.
await Console(stream)
```

What you see in the previous code is how you can create a task that involves multiple agents working together to analyze data. Each agent performs a specific function, and the task is executed by coordinating the agents to achieve the desired outcome. By creating dedicated agents with specialized roles, you can improve task efficiency and performance.

### Learn in Real-Time

Advanced frameworks provide capabilities for real-time context understanding and adaptation.

**How teams can use these**: Teams can implement feedback loops where agents learn from interactions and adjust their behavior dynamically, leading to continuous improvement and refinement of capabilities.

**How it works in practice**: Agents can analyze user feedback, environmental data, and task outcomes to update their knowledge base, adjust decision-making algorithms, and improve performance over time. This iterative learning process enables agents to adapt to changing conditions and user preferences, enhancing overall system effectiveness.

## What are the differences between the frameworks AutoGen, Semantic Kernel and Azure AI Agent Service?

There are many ways to compare these frameworks, but let's look at some key differences in terms of their design, capabilities, and target use cases:

## AutoGen

AutoGen is an open-source framework developed by Microsoft Research's AI Frontiers Lab. It focuses on event-driven, distributed *agentic* applications, enabling multiple LLMs and SLMs, tools, and advanced multi-agent design patterns.

AutoGen is built around the core concept of agents, which are autonomous entities that can perceive their environment, make decisions, and take actions to achieve specific goals. Agents communicate through asynchronous messages, allowing them to work independently and in parallel, enhancing system scalability and responsiveness.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agenten zijn gebaseerd op het actor-model</a>. According to Wikipedia, an actor is _het basiselement van gelijktijdige berekening. Als reactie op een bericht dat het ontvangt, kan een actor: lokale beslissingen nemen, meer actoren creëren, meer berichten sturen, en bepalen hoe te reageren op het volgende ontvangen bericht_.

**Use Cases**: Automating code generation, data analysis tasks, and building custom agents for planning and research functions.

Here are some important core concepts of AutoGen:

- **Agents**. An agent is a software entity that:
  - **Communicates via messages**, these messages can be synchronous or asynchronous.
  - **Maintains its own state**, which can be modified by incoming messages.
  - **Performs actions** in response to received messages or changes in its state. These actions may modify the agent’s state and produce external effects, such as updating message logs, sending new messages, executing code, or making API calls.
    
  Here you have a short code snippet in which you create your own agent with Chat capabilities:

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
    
    In the previous code, `MyAgent` has been created and inherits from `RoutedAgent`. It has a message handler that prints the content of the message and then sends a response using the `AssistantAgent` delegate. Especially note how we assign to `self._delegate` an instance of `AssistantAgent` which is a pre-built agent that can handle chat completions.


    Let's let AutoGen know about this agent type and kick off the program next:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Begin met het verwerken van berichten op de achtergrond.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    In the previous code the agents are registered with the runtime and then a message is sent to the agent resulting in the following output:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multi agents**. AutoGen supports the creation of multiple agents that can work together to achieve complex tasks. Agents can communicate, share information, and coordinate their actions to solve problems more efficiently. To create a multi-agent system, you can define different types of agents with specialized functions and roles, such as data retrieval, analysis, decision-making, and user interaction. Let's see how such a creation looks like so we get a sense of it:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Voorbeeld van het declareren van een Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Gebruik van het onderwerptype als het agenttype.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # Overige declaraties ingekort voor beknoptheid

    # Groepschat
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

    In the previous code we have a `GroupChatManager` that is registered with the runtime. This manager is responsible for coordinating the interactions between different types of agents, such as writers, illustrators, editors, and users.

- **Agent Runtime**. The framework provides a runtime environment, enabling communication between agents, manages their identities and lifecycles, and enforce security and privacy boundaries. This means that you can run your agents in a secure and controlled environment, ensuring that they can interact safely and efficiently. There are two runtimes of interest:
  - **Stand-alone runtime**. This is a good choice for single-process applications where all agents are implemented in the same programming language and run in the same process. Here's an illustration of how it works:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Stand-alone runtime</a>   
Application stack

    *agents communicate via messages through the runtime, and the runtime manages the lifecycle of agents*

  - **Distributed agent runtime**, is suitable for multi-process applications where agents may be implemented in different programming languages and running on different machines. Here's an illustration of how it works:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Distributed runtime</a>

## Semantic Kernel + Agent Framework

Semantic Kernel is an enterprise-ready AI Orchestration SDK. It consists of AI and memory connectors, along with an Agent Framework.

Let's first cover some core components:

- **AI Connectors**: This is an interface with external AI services and data sources for use in both Python and C#.

  ```python
  # Semantische Kernel Python
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

    Here you have a simple example of how you can create a kernel and add a chat completion service. Semantic Kernel creates a connection to an external AI service, in this case, Azure OpenAI Chat Completion.

- **Plugins**: These encapsulate functions that an application can use. There are both ready-made plugins and custom ones you can create. A related concept is "prompt functions." Instead of providing natural language cues for function invocation, you broadcast certain functions to the model. Based on the current chat context, the model may choose to call one of these functions to complete a request or query. Here's an example:

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

    Here, you first have a template prompt `skPrompt` that leaves room for the user to input text, `$userInput`. Then you create the kernel function `SummarizeText` and then import it into the kernel with the plugin name `SemanticFunctions`. Note the name of the function that helps Semantic Kernel understand what the function does and when it should be called.

- **Native function**: There's also native functions that the framework can call directly to carry out the task. Here's an example of such a function retrieving the content from a file:

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

- **Memory**:  Abstracts and simplifies context management for AI apps. The idea with memory is that this is something the LLM should know about. You can store this information in a vector store which ends up being an in-memory database or a vector database or similar. Here's an example of a very simplified scenario where *facts* are added to the memory:

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

    Deze feiten worden vervolgens opgeslagen in de geheugenverzameling `SummarizedAzureDocs`. Dit is een sterk vereenvoudigd voorbeeld, maar je kunt zien hoe je informatie kunt opslaan in het geheugen zodat de LLM deze kan gebruiken.

Dus dat is de basis van het Semantic Kernel-framework, maar hoe zit het met het Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service is een recentere toevoeging, geïntroduceerd tijdens Microsoft Ignite 2024. Het maakt de ontwikkeling en inzet van AI-agents mogelijk met flexibelere modellen, zoals het rechtstreeks aanroepen van open-source LLM's zoals Llama 3, Mistral en Cohere.

Azure AI Agent Service biedt sterkere beveiligingsmechanismen voor ondernemingen en methoden voor gegevensopslag, waardoor het geschikt is voor zakelijke toepassingen.

Het werkt direct uit de doos met multi-agent orkestratieframeworks zoals AutoGen en Semantic Kernel.

Deze service bevindt zich momenteel in de Public Preview en ondersteunt Python en C# voor het bouwen van agents.

Met Semantic Kernel Python kunnen we een Azure AI Agent maken met een door de gebruiker gedefinieerde plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definieer een voorbeeldplugin voor de sample
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
        # Maak agentdefinitie aan
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Maak de AzureAI Agent aan met de gedefinieerde client en agentdefinitie
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Maak een thread aan om het gesprek vast te houden
        # Als er geen thread wordt meegegeven, wordt er een nieuwe thread
        # gemaakt en geretourneerd met de initiële reactie
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
                # Roep de agent aan voor de opgegeven thread
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

### Kernconcepten

Azure AI Agent Service heeft de volgende kernconcepten:

- **Agent**. Azure AI Agent Service integreert met Microsoft Foundry. Binnen AI Foundry fungeert een AI Agent als een "slimme" microservice die gebruikt kan worden om vragen te beantwoorden (RAG), acties uit te voeren of workflows volledig te automatiseren. Dit bereikt het door de kracht van generatieve AI-modellen te combineren met tools die het mogelijk maken toegang te krijgen tot en te interageren met data uit de echte wereld. Hier is een voorbeeld van een agent:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    In dit voorbeeld wordt een agent aangemaakt met het model `gpt-4o-mini`, een naam `my-agent` en instructies `You are helpful agent`. De agent is uitgerust met tools en bronnen om taken voor code-interpretatie uit te voeren.

- **Thread and messages**. De thread is een ander belangrijk concept. Het vertegenwoordigt een gesprek of interactie tussen een agent en een gebruiker. Threads kunnen worden gebruikt om de voortgang van een gesprek bij te houden, contextinformatie op te slaan en de staat van de interactie te beheren. Hier is een voorbeeld van een thread:

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

    In de vorige code wordt een thread aangemaakt. Daarna wordt er een bericht naar de thread gestuurd. Door `create_and_process_run` aan te roepen, wordt de agent gevraagd werk op de thread uit te voeren. Ten slotte worden de berichten opgehaald en gelogd om de reactie van de agent te zien. De berichten geven de voortgang van het gesprek tussen de gebruiker en de agent aan. Het is ook belangrijk te begrijpen dat de berichten van verschillende typen kunnen zijn, zoals tekst, afbeelding of bestand; dat is het werk van de agent heeft bijvoorbeeld geresulteerd in een afbeelding of een tekstreactie. Als ontwikkelaar kun je deze informatie vervolgens gebruiken om de reactie verder te verwerken of aan de gebruiker te presenteren.

- **Integrates with other AI frameworks**. Azure AI Agent service kan interageren met andere frameworks zoals AutoGen en Semantic Kernel, wat betekent dat je een deel van je app in een van deze frameworks kunt bouwen en bijvoorbeeld de Agent service als orkestrator kunt gebruiken, of dat je alles in de Agent service kunt bouwen.

**Use Cases**: Azure AI Agent Service is ontworpen voor zakelijke toepassingen die veilige, schaalbare en flexibele inzet van AI-agents vereisen.

## What's the difference between these frameworks?
 
Het lijkt inderdaad alsof er veel overlap is tussen deze frameworks, maar er zijn enkele belangrijke verschillen in ontwerp, mogelijkheden en beoogde gebruiksscenario's:
 
- **AutoGen**: Is een experimenteerframework gericht op baanbrekend onderzoek naar multi-agent systemen. Het is de beste plek om te experimenteren en geavanceerde multi-agent systemen te prototypen.
- **Semantic Kernel**: Is een productie-klaar agentbibliotheek voor het bouwen van enterprise agentische applicaties. Richt zich op event-driven, gedistribueerde agentische applicaties, en maakt meerdere LLMs en SLMs, tools en single/multi-agent ontwerppatronen mogelijk.
- **Azure AI Agent Service**: Is een platform- en inzetservice in Azure Foundry voor agents. Het biedt bouwconnectiviteit naar services ondersteund door Azure Foundry zoals Azure OpenAI, Azure AI Search, Bing Search en code-executie.
 
Weet je nog steeds niet welke je moet kiezen?

### Gebruiksscenario's
 
Laten we eens kijken of we je kunnen helpen door enkele veelvoorkomende gebruiksscenario's te doorlopen:
 
> Q: Ik experimenteer, leer en bouw proof-of-concept agenttoepassingen, en ik wil snel kunnen bouwen en experimenteren
>

>A: AutoGen zou een goede keuze zijn voor dit scenario, aangezien het zich richt op event-driven, gedistribueerde agentische applicaties en geavanceerde multi-agent ontwerppatronen ondersteunt.

> Q: Wat maakt AutoGen een betere keuze dan Semantic Kernel en Azure AI Agent Service voor dit gebruiksscenario?
>
> A: AutoGen is specifiek ontworpen voor event-driven, gedistribueerde agentische applicaties, waardoor het goed geschikt is voor het automatiseren van codegeneratie en data-analysetaken. Het biedt de nodige tools en mogelijkheden om complexe multi-agent systemen efficiënt te bouwen.

>Q: Het klinkt alsof Azure AI Agent Service hier ook zou kunnen werken, het heeft tools voor codegeneratie en meer?
>
> A: Ja, Azure AI Agent Service is een platformdienst voor agents en voegt ingebouwde mogelijkheden toe voor meerdere modellen, Azure AI Search, Bing Search en Azure Functions. Het maakt het eenvoudig om je agents in de Foundry Portal te bouwen en op schaal te implementeren.
 
> Q: Ik ben nog steeds in de war, geef me gewoon één optie
>
> A: Een goede keuze is om je applicatie eerst in Semantic Kernel te bouwen en vervolgens Azure AI Agent Service te gebruiken om je agent te implementeren. Deze aanpak stelt je in staat je agents eenvoudig persistent op te slaan terwijl je gebruikmaakt van de kracht om multi-agent systemen in Semantic Kernel te bouwen. Daarnaast heeft Semantic Kernel een connector in AutoGen, waardoor het eenvoudig is om beide frameworks samen te gebruiken.
 
Laten we de belangrijkste verschillen samenvatten in een tabel:

| Framework | Focus | Kernconcepten | Gebruiksscenario's |
| --- | --- | --- | --- |
| AutoGen | Event-driven, gedistribueerde agentische applicaties | Agents, Personas, Functions, Data | Codegeneratie, data-analysetaken |
| Semantic Kernel | Begrip en generatie van mensachtige tekstinhoud | Agents, Modulaire componenten, Samenwerking | Natuurlijke taalbegrip, inhoudsgeneratie |
| Azure AI Agent Service | Flexibele modellen, enterprise-beveiliging, codegeneratie, tool-aanroepen | Modulariteit, Samenwerking, Procesorkestratie | Veilige, schaalbare en flexibele inzet van AI-agents |

Wat is het ideale gebruiksscenario voor elk van deze frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

Het antwoord is ja, je kunt je bestaande Azure-ecosysteemtools rechtstreeks integreren, vooral met Azure AI Agent Service, omdat het is gebouwd om naadloos samen te werken met andere Azure-services. Je kunt bijvoorbeeld Bing, Azure AI Search en Azure Functions integreren. Er is ook diepe integratie met Microsoft Foundry.

Voor AutoGen en Semantic Kernel kun je ook integreren met Azure-services, maar het kan vereisen dat je de Azure-services vanuit je code aanroept. Een andere manier om te integreren is door de Azure SDK's te gebruiken om vanuit je agents met Azure-services te communiceren. Daarnaast, zoals eerder genoemd, kun je Azure AI Agent Service gebruiken als orkestrator voor je agents die in AutoGen of Semantic Kernel zijn gebouwd, wat gemakkelijke toegang tot het Azure-ecosysteem biedt.

## Sample Codes

- Python: [Agent-framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent-framework](./code_samples/02-dotnet-agent-framework.md)

## Heb je meer vragen over AI Agent Frameworks?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) om andere learners te ontmoeten, deel te nemen aan office hours en je vragen over AI Agents beantwoord te krijgen.

## Referenties

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel en AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent-service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Azure AI Agent Service gebruiken met AutoGen / Semantic Kernel om een multi-agentoplossing te bouwen</a>

## Previous Lesson

[Inleiding tot AI-agents en gebruiksscenario's voor agents](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Agentische ontwerppatronen begrijpen](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Disclaimer:
Dit document is vertaald met behulp van de AI-vertalingsdienst Co-op Translator (https://github.com/Azure/co-op-translator). Hoewel we streven naar nauwkeurigheid, dient u er rekening mee te houden dat geautomatiseerde vertalingen fouten of onjuistheden kunnen bevatten. Het oorspronkelijke document in de originele taal moet als de gezaghebbende bron worden beschouwd. Voor kritieke informatie wordt een professionele menselijke vertaling aanbevolen. Wij zijn niet aansprakelijk voor eventuele misverstanden of verkeerde interpretaties die voortvloeien uit het gebruik van deze vertaling.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->