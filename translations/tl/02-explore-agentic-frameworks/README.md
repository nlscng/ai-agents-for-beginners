[![Paggalugad ng Mga Framework ng AI Agent](../../../translated_images/tl/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(I-click ang imahe sa itaas upang panoorin ang video ng leksyon na ito)_

# Tuklasin ang Mga Framework ng AI Agent

Ang mga AI agent framework ay mga software platform na idinisenyo upang pasimplehin ang paglikha, pag-deploy, at pamamahala ng mga AI agent. Ang mga framework na ito ay nagbibigay sa mga developer ng mga pre-built na komponent, abstraksiyon, at mga kasangkapan na nagpapadali sa pagbuo ng mga kumplikadong system ng AI.

Tinutulungan ng mga framework na ito ang mga developer na magpokus sa natatanging mga aspeto ng kanilang mga aplikasyon sa pamamagitan ng pagbibigay ng mga standardized na paraan sa mga karaniwang hamon sa pag-develop ng AI agent. Pinapahusay nila ang scalability, accessibility, at kahusayan sa pagbuo ng mga sistema ng AI.

## Panimula 

Tatalakayin ng leksyon na ito:

- Ano ang mga AI Agent Frameworks at ano ang pinapayagan nilang makamit ng mga developer?
- Paano magagamit ng mga koponan ang mga ito para mabilis na makapag-prototype, mag-iterate, at pagandahin ang kakayahan ng kanilang agent?
- Ano ang mga pagkakaiba sa pagitan ng mga framework at mga tool na ginawa ng Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, at <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Maaari ko bang i-integrate nang direkta ang aking umiiral na mga tool sa Azure ecosystem, o kailangan ko ba ng mga standalone na solusyon?
- Ano ang Azure AI Agents service at paano ito makakatulong sa akin?

## Mga Layunin ng Pagkatuto

Ang mga layunin ng leksyon na ito ay tulungan kang maunawaan ang mga sumusunod:

- Ang papel ng mga AI Agent Frameworks sa pag-develop ng AI.
- Paano samantalahin ang mga AI Agent Frameworks upang bumuo ng mga intelligent na agent.
- Mga pangunahing kakayahang pinapagana ng mga AI Agent Frameworks.
- Ang mga pagkakaiba sa pagitan ng AutoGen, Semantic Kernel, at Azure AI Agent Service.

## Ano ang mga AI Agent Frameworks at ano ang pinapayagan nilang gawin ng mga developer?

Makakatulong ang tradisyonal na mga AI Frameworks na i-integrate ang AI sa iyong mga app at gawing mas mahusay ang mga ito sa mga sumusunod na paraan:

- **Pagpapersonalisa**: Maaaring suriin ng AI ang pag-uugali at mga kagustuhan ng gumagamit upang magbigay ng mga personalized na rekomendasyon, nilalaman, at karanasan.
  Halimbawa: Gumagamit ang mga streaming service tulad ng Netflix ng AI upang magmungkahi ng mga pelikula at palabas batay sa kasaysayan ng panonood, na nagpapahusay ng pakikipag-ugnayan at kasiyahan ng gumagamit.
- **Awtomasyon at Kahusayan**: Maaaring i-automate ng AI ang mga paulit-ulit na gawain, pag-streamline ng mga workflow, at pagpapabuti ng operational na kahusayan.
  Halimbawa: Gumagamit ang mga customer service app ng AI-powered chatbots upang hawakan ang mga karaniwang inquiry, nagpapababa ng oras ng tugon at nagbibigay-laya sa mga human agent para sa mas kumplikadong isyu.
- **Pinahusay na Karanasan ng Gumagamit**: Maaaring pagandahin ng AI ang pangkalahatang karanasan ng gumagamit sa pamamagitan ng pagbibigay ng mga intelligent na tampok tulad ng voice recognition, natural language processing, at predictive text.
  Halimbawa: Gumagamit ang mga virtual assistant tulad ng Siri at Google Assistant ng AI upang maunawaan at tumugon sa mga voice command, ginagawa itong mas madali para sa mga gumagamit na makipag-ugnayan sa kanilang mga device.

### Ang lahat ng iyon ay maganda, kaya bakit kailangan natin ang AI Agent Framework?

Ang mga AI Agent framework ay higit pa sa mga simpleng AI framework. Dinisenyo ang mga ito upang payagan ang paglikha ng mga intelligent na agent na maaaring makipag-ugnayan sa mga gumagamit, ibang mga agent, at sa kapaligiran upang makamit ang tiyak na mga layunin. Maaaring magpakita ang mga agent ng autonomous na pag-uugali, gumawa ng mga desisyon, at mag-adapt sa mga nagbabagong kondisyon. Narito ang ilang pangunahing kakayahan na pinapagana ng mga AI Agent Frameworks:

- **Kolaborasyon at Koordinasyon ng mga Agent**: Pinapayagan ang paglikha ng maramihang AI agent na maaaring magtulungan, mag-communicate, at mag-coordinate upang malutas ang mga kumplikadong gawain.
- **Awtomasyon at Pamamahala ng Mga Gawain**: Nagbibigay ng mga mekanismo para sa pag-automate ng multi-step na mga workflow, delegasyon ng mga gawain, at dynamic na pamamahala ng gawain sa pagitan ng mga agent.
- **Kontextwal na Pag-unawa at Adaptasyon**: Nilalagyan ang mga agent ng kakayahang maunawaan ang konteksto, mag-adapt sa nagbabagong mga kapaligiran, at gumawa ng mga desisyon batay sa real-time na impormasyon.

Sa buod, pinapayagan ka ng mga agent na gumawa ng higit pa, itaas ang antas ng awtomasyon, at lumikha ng mas intelligent na mga sistema na maaaring mag-adapt at matuto mula sa kanilang kapaligiran.

## Paano mabilis na makapag-prototype, mag-iterate, at pagandahin ang kakayahan ng agent?

Mabilis ang pagbabago sa larangang ito, ngunit may ilang mga bagay na karaniwan sa karamihan ng mga AI Agent Frameworks na makakatulong sa iyo na mabilis na makapag-prototype at mag-iterate, tulad ng mga modular na komponent, mga kasangkapang kolaboratibo, at real-time na pagkatuto. Talakayin natin ang mga ito:

- **Gumamit ng Modular na mga Komponent**: Nag-aalok ang mga AI SDK ng mga pre-built na komponent tulad ng AI at Memory connectors, function calling gamit ang natural language o code plugins, mga prompt template, at iba pa.
- **Samantalahin ang mga Tool para sa Kolaborasyon**: Disenyuhin ang mga agent na may espesipikong mga tungkulin at gawain, na nagpapahintulot sa kanila na subukan at pinuhin ang mga collaborative workflow.
- **Matuto nang Real-time**: Magpatupad ng feedback loops kung saan natututo ang mga agent mula sa interaksyon at ina-adjust ang kanilang pag-uugali nang dinamiko.

### Gumamit ng Modular na mga Komponent

Nag-aalok ang mga SDK tulad ng Microsoft Semantic Kernel at LangChain ng mga pre-built na komponent tulad ng AI connectors, mga prompt template, at pamamahala ng memorya.

**Paano magagamit ng mga koponan ang mga ito**: Maaaring mabilis na buuin ng mga koponan ang mga komponent na ito upang gumawa ng mabibigay-panahong prototype nang hindi nagsisimula mula sa simula, na nagpapahintulot para sa mabilis na eksperimento at pag-iterate.

**Paano ito gumagana sa praksis**: Maaari kang gumamit ng pre-built na parser upang kunin ang impormasyon mula sa input ng gumagamit, isang memory module upang mag-imbak at kumuha ng data, at isang prompt generator upang makipag-ugnayan sa mga gumagamit, lahat nang hindi kailangang itayo ang mga komponent na ito mula sa simula.

**Halimbawa ng code**. Tingnan natin ang mga halimbawa kung paano mo magagamit ang isang pre-built AI Connector sa Semantic Kernel Python at .Net na gumagamit ng auto-function calling upang magpahayag ang model ng tugon sa input ng gumagamit:

``` python
# Halimbawa ng Semantic Kernel sa Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Tukuyin ang ChatHistory object upang hawakan ang konteksto ng pag-uusap
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Tukuyin ang isang halimbawa ng plugin na naglalaman ng function para mag-book ng biyahe
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Gumawa ng Kernel
kernel = Kernel()

# Idagdag ang halimbawa ng plugin sa Kernel object
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Tukuyin ang Azure OpenAI AI Connector
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Tukuyin ang mga setting ng request upang i-configure ang modelo na may auto-function calling
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Gawin ang request sa modelo para sa ibinigay na chat history at mga request settings
    # Naglalaman ang Kernel ng halimbawa na hihilingin ng modelo na i-invoke
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
    # Halimbawa ng Tugon ng AI Model: `Matagumpay na na-book ang iyong flight patungong New York sa Enero 1, 2025. Ingat sa biyahe! ✈️🗽`

    # Idagdag ang tugon ng modelo sa konteksto ng ating kasaysayan ng pag-uusap
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

Makikita mo mula sa halimbawang ito kung paano mo masasamantala ang isang pre-built na parser upang kunin ang mga pangunahing impormasyon mula sa input ng gumagamit, tulad ng pinagmulan, destinasyon, at petsa ng kahilingan sa pag-book ng flight. Pinapahintulutan ka ng modular na pamamaraan na ito na magpokus sa mataas-na-antas na lohika.

### Samantalahin ang mga Tool para sa Kolaborasyon

Ang mga framework tulad ng CrewAI, Microsoft AutoGen, at Semantic Kernel ay nagpapadali sa paglikha ng maramihang agent na maaaring magtulungan.

**Paano magagamit ng mga koponan ang mga ito**: Maaaring idisenyo ng mga koponan ang mga agent na may espesipikong mga tungkulin at gawain, na nagpapahintulot sa kanila na subukan at pinuhin ang mga collaborative workflow at pagbutihin ang pangkalahatang kahusayan ng sistema.

**Paano ito gumagana sa praksis**: Maaari kang lumikha ng isang koponan ng mga agent kung saan ang bawat agent ay may espesyal na tungkulin, tulad ng pagkuha ng data, pagsusuri, o paggawa ng desisyon. Maaaring mag-communicate at magbahagi ng impormasyon ang mga agent na ito upang makamit ang isang karaniwang layunin, tulad ng pagsagot sa isang query ng gumagamit o pagtapos ng isang gawain.

**Halimbawa ng code (AutoGen)**:

```python
# gumagawa ng mga ahente, pagkatapos gumawa ng isang round robin na iskedyul kung saan sila pwedeng magtrabaho nang magkakasama, sa kasong ito sunod-sunod

# Ahente sa Pagkuha ng Datos
# Ahente sa Pagsusuri ng Datos
# Ahente sa Paggawa ng Desisyon

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

# nagtatapos ang pag-uusap kapag sinabi ng user ang "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Gamitin ang asyncio.run(...) kapag nagpapatakbo sa isang script.
await Console(stream)
```

Makikita mo sa nakaraang code kung paano ka makalilikha ng isang gawain na kinabibilangan ng maraming agent na nagtutulungan upang suriin ang data. Ang bawat agent ay gumaganap ng isang partikular na tungkulin, at ang gawain ay isinasagawa sa pamamagitan ng pag-coordinate ng mga agent upang makamit ang ninanais na resulta. Sa pamamagitan ng paglikha ng dedikadong mga agent na may mga espesyal na tungkulin, maaari mong pagbutihin ang kahusayan at pagganap ng gawain.

### Matuto nang Real-time

Nagbibigay ang mga advanced na framework ng mga kakayahan para sa real-time na pag-unawa sa konteksto at adaptasyon.

**Paano magagamit ng mga koponan ang mga ito**: Maaaring magpatupad ang mga koponan ng mga feedback loop kung saan natututo ang mga agent mula sa interaksyon at ina-adjust ang kanilang pag-uugali nang dinamiko, na humahantong sa tuloy-tuloy na pagpapabuti at pagpipino ng mga kakayahan.

**Paano ito gumagana sa praksis**: Maaaring suriin ng mga agent ang feedback ng gumagamit, data ng kapaligiran, at mga kinalabasan ng gawain upang i-update ang kanilang knowledge base, i-adjust ang mga algorithm ng paggawa ng desisyon, at pagbutihin ang pagganap sa paglipas ng panahon. Pinapahintulutan ng prosesong ito ng iterative learning ang mga agent na mag-adapt sa nagbabagong kondisyon at mga kagustuhan ng gumagamit, na nagpapahusay ng pangkalahatang bisa ng sistema.

## Ano ang mga pagkakaiba sa pagitan ng mga framework AutoGen, Semantic Kernel at Azure AI Agent Service?

Maraming paraan upang ikumpara ang mga framework na ito, ngunit tingnan natin ang ilang pangunahing pagkakaiba sa mga tuntunin ng kanilang disenyo, kakayahan, at target na mga use case:

## AutoGen

Ang AutoGen ay isang open-source na framework na binuo ng Microsoft Research's AI Frontiers Lab. Nakatuon ito sa event-driven, distributed *agentic* applications, na nagpapahintulot ng maraming LLMs at SLMs, mga tool, at mga advanced na multi-agent design pattern.

Binuo ang AutoGen sa paligid ng pangunahing konsepto ng mga agent, na mga autonomous na entidad na maaaring maunawaan ang kanilang kapaligiran, gumawa ng mga desisyon, at gumawa ng mga aksyon upang makamit ang mga tiyak na layunin. Nagko-communicate ang mga agent sa pamamagitan ng asynchronous na mga mensahe, na nagpapahintulot sa kanila na gumana nang independiyente at paralel, pinapahusay ang scalability at responsiveness ng system.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Ang mga agent ay batay sa modelong actor</a>. Ayon sa Wikipedia, ang isang actor ay _ang pangunahing yunit ng magkakasabay na komputasyon. Bilang tugon sa isang mensaheng natatanggap nito, ang isang actor ay maaaring: gumawa ng lokal na mga desisyon, lumikha ng higit pang mga actor, magpadala ng karagdagang mga mensahe, at tukuyin kung paano tumugon sa susunod na mensahe na matatanggap_.

**Mga Use Case**: Pag-automate ng pagbuo ng code, mga gawain sa pagsusuri ng data, at pagbuo ng mga custom na agent para sa pagpaplano at mga function sa pananaliksik.

Narito ang ilang mahahalagang pangunahing konsepto ng AutoGen:

- **Mga Agent**. Ang isang agent ay isang software na entidad na:
  - **Nakikipag-ugnayan sa pamamagitan ng mga mensahe**, ang mga mensaheng ito ay maaaring synchronous o asynchronous.
  - **Nagpapanatili ng sarili nitong estado**, na maaaring mabago ng mga papasok na mensahe.
  - **Nagsasagawa ng mga aksyon** bilang tugon sa mga natanggap na mensahe o pagbabago sa estado nito. Ang mga aksyon na ito ay maaaring magbago ng estado ng agent at magdulot ng mga panlabas na epekto, tulad ng pag-update ng message logs, pagpapadala ng mga bagong mensahe, pagpapatupad ng code, o paggawa ng mga API call.
    
  Narito ang isang maikling snippet ng code kung saan lumilikha ka ng iyong sariling agent na may kakayahan sa Chat:

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
    
    Sa nakaraang code, ang `MyAgent` ay nilikha at nagmana mula sa `RoutedAgent`. Mayroon itong message handler na nagpi-print ng nilalaman ng mensahe at pagkatapos ay nagpapadala ng tugon gamit ang `AssistantAgent` delegate. Tandaan lalo na kung paano namin ina-assign sa `self._delegate` ang isang instance ng `AssistantAgent` na isang pre-built na agent na maaaring humawak ng chat completions.


    Paalamin natin ang AutoGen tungkol sa uri ng agent na ito at simulan ang programa kasunod nito:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Simulan ang pagproseso ng mga mensahe sa background.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Sa nakaraang code ang mga agent ay nakarehistro sa runtime at pagkatapos ay isang mensahe ang ipinadala sa agent na nagreresulta sa sumusunod na output:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Maramihang mga agent**. Sinusuportahan ng AutoGen ang paglikha ng maramihang agent na maaaring magtulungan upang makamit ang mga kumplikadong gawain. Maaaring mag-communicate ang mga agent, magbahagi ng impormasyon, at i-coordinate ang kanilang mga aksyon upang mas epektibong malutas ang mga problema. Upang lumikha ng isang multi-agent system, maaari mong tukuyin ang iba't ibang uri ng agent na may espesyal na mga function at tungkulin, tulad ng pagkuha ng data, pagsusuri, paggawa ng desisyon, at interaksyon sa gumagamit. Tingnan natin kung paano ganito ang magiging anyo ng paglikha upang magkaroon tayo ng ideya nito:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Halimbawa ng pagdedeklara ng Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Paggamit ng uri ng paksa bilang uri ng agent.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # pinaikli ang mga natitirang deklarasyon para sa kasimplehan

    # Pangkalahatang usapan
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

    Sa nakaraang code mayroon tayong `GroupChatManager` na nakarehistro sa runtime. Ang manager na ito ang responsable sa pag-coordinate ng mga interaksyon sa pagitan ng iba't ibang uri ng agent, tulad ng mga writer, illustrator, editor, at mga gumagamit.

- **Agent Runtime**. Nagbibigay ang framework ng isang runtime na kapaligiran, na nagpapahintulot ng komunikasyon sa pagitan ng mga agent, nagma-manage ng kanilang mga identidad at lifecycle, at nagpapatupad ng mga hangganan sa seguridad at privacy. Nangangahulugan ito na maaari mong patakbuhin ang iyong mga agent sa isang ligtas at kontroladong kapaligiran, tinitiyak na maaari silang makipag-ugnayan nang ligtas at mahusay. May dalawang runtime na dapat pansinin:
  - **Stand-alone na runtime**. Magandang pagpipilian ito para sa mga single-process na aplikasyon kung saan ang lahat ng agent ay na-implementa sa parehong programming language at tumatakbo sa parehong proseso. Narito ang isang ilustrasyon kung paano ito gumagana:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Stand-alone na runtime</a>   
Application stack

    *ang mga agent ay nakikipag-ugnayan sa pamamagitan ng mga mensahe sa runtime, at ang runtime ang nag-aasikaso ng lifecycle ng mga agent*

  - **Pinamahaging runtime para sa mga agent**, angkop ito para sa mga multi-process na aplikasyon kung saan ang mga agent ay maaaring na-implementa sa iba't ibang programming language at tumatakbo sa iba't ibang makina. Narito ang isang ilustrasyon kung paano ito gumagana:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Pinamahaging runtime</a>

## Semantic Kernel + Agent Framework

Ang Semantic Kernel ay isang enterprise-ready na AI Orchestration SDK. Binubuo ito ng mga AI at memory connectors, kasama ang isang Agent Framework.

Unahin nating talakayin ang ilang pangunahing komponent:

- **AI Connectors**: Ito ay isang interface sa mga external na AI service at mga pinagmumulan ng data para magamit sa parehong Python at C#.

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

    Narito ang isang simpleng halimbawa kung paano ka maaaring lumikha ng isang kernel at magdagdag ng isang chat completion service. Lumilikha ang Semantic Kernel ng koneksyon sa isang external na AI service, sa kasong ito, Azure OpenAI Chat Completion.

- **Plugins**: Ang mga ito ay naglalaman ng mga function na maaaring gamitin ng isang application. Mayroong parehong ready-made na plugins at mga custom na maaari mong likhain. Kaugnay na konsepto nito ang "prompt functions." Sa halip na magbigay ng mga natural language na pahiwatig para sa pag-invoke ng function, ini-broadcast mo ang mga tiyak na function sa model. Batay sa kasalukuyang konteksto ng chat, maaaring piliin ng model na tawagan ang isa sa mga function na ito upang kumpletuhin ang isang request o query. Narito ang isang halimbawa:

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

    Dito, mayroon ka munang template prompt `skPrompt` na nag-iiwan ng puwang para sa gumagamit na maglagay ng teksto, `$userInput`. Pagkatapos ay lumikha ka ng kernel function na `SummarizeText` at i-import ito sa kernel gamit ang plugin name na `SemanticFunctions`. Pansinin ang pangalan ng function na tumutulong sa Semantic Kernel na maunawaan kung ano ang ginagawa ng function at kung kailan ito dapat tawagin.

- **Native function**: Mayroon ding mga native na function na maaaring tawagin nang direkta ng framework upang isakatuparan ang gawain. Narito ang isang halimbawa ng isang function na kumukuha ng nilalaman mula sa isang file:

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

- **Memory**:  Nag-aabstract at nagpapasimple ng pamamahala ng konteksto para sa mga AI app. Ang ideya ng memory ay ito ay isang bagay na dapat malaman ng LLM. Maaari mong i-imbak ang impormasyong ito sa isang vector store na nagiging isang in-memory na database o isang vector database o katulad nito. Narito ang isang halimbawa ng isang napakasimpleng senaryo kung saan ang *mga katotohanan* ay idinadagdag sa memorya:

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

    Ang mga katotohanang ito ay pagkatapos ay iniimbak sa koleksyon ng memorya na `SummarizedAzureDocs`. Ito ay isang napakasimpleng halimbawa, pero makikita mo kung paano mo maiimbak ang impormasyon sa memorya para magamit ng LLM.

So that's the basics of the Semantic Kernel framework, what about the Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service ay isang mas kamakailang karagdagan, ipinakilala sa Microsoft Ignite 2024. Pinapayagan nito ang pag-develop at pag-deploy ng mga AI agent gamit ang mas flexible na mga modelo, tulad ng direktang pagtawag sa open-source LLMs tulad ng Llama 3, Mistral, at Cohere.

Azure AI Agent Service ay nagbibigay ng mas matibay na mekanismo ng seguridad para sa enterprise at mga paraan ng pag-iimbak ng datos, kaya angkop ito para sa mga enterprise na aplikasyon.

Ito ay gumagana nang out-of-the-box kasama ang multi-agent orchestration frameworks tulad ng AutoGen at Semantic Kernel.

Ang serbisyong ito ay kasalukuyang nasa Public Preview at sumusuporta sa Python at C# para sa paggawa ng mga agent.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Magdefine ng isang sample plugin para sa sample
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
        # Gumawa ng depinisyon ng ahente
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Gumawa ng AzureAI Agent gamit ang tinukoy na client at depinisyon ng ahente
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Gumawa ng isang thread para hawakan ang pag-uusap
        # Kung walang ibinigay na thread, isang bagong thread ang
        # gagawin at ibabalik kasama ang unang tugon
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
                # Tawagin ang ahente para sa tinukoy na thread
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

### Core concepts

Azure AI Agent Service ay may mga sumusunod na pangunahing konsepto:

- **Agent**. Azure AI Agent Service integrates with Microsoft Foundry. Within AI Foundry, an AI Agent acts as a "smart" microservice that can be used to answer questions (RAG), perform actions, or completely automate workflows. It achieves this by combining the power of generative AI models with tools that allow it to access and interact with real-world data sources. Here's an example of an agent:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Sa halimbawa na ito, ang isang agent ay ginawa gamit ang modelong `gpt-4o-mini`, isang pangalan na `my-agent`, at mga instruksiyon na `You are helpful agent`. Ang agent ay may mga tool at mga pinagkukunan upang magsagawa ng mga gawain ng interpretasyon ng code.

- **Thread and messages**. The thread is another important concept. It represents a conversation or interaction between an agent and a user. Threads can be used to track the progress of a conversation, store context information, and manage the state of the interaction. Here's an example of a thread:

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

    Sa naunang code, isang thread ang nilikha. Pagkatapos nito, isang mensahe ang ipinadala sa thread. Sa pagtawag ng `create_and_process_run`, hinihiling ang agent na gumawa ng trabaho sa thread. Sa wakas, kinukuha at nilolog ang mga mensahe upang makita ang tugon ng agent. Ipinapakita ng mga mensahe ang progreso ng pag-uusap sa pagitan ng user at ng agent. Mahalaga ring maunawaan na ang mga mensahe ay maaaring iba-iba ang uri tulad ng text, image, o file — ibig sabihin, ang trabaho ng agent ay maaaring nagresulta, halimbawa, sa isang imahe o isang tugon na teksto. Bilang isang developer, maaari mong gamitin ang impormasyong ito upang karagdagang iproseso ang tugon o ipakita ito sa user.

- **Integrates with other AI frameworks**. Azure AI Agent service can interact with other frameworks like AutoGen and Semantic Kernel, which means you can build part of your app in one of these frameworks and for example using the Agent service as an orchestrator or you can build everything in the Agent service.

**Use Cases**: Azure AI Agent Service ay idinisenyo para sa mga enterprise na aplikasyon na nangangailangan ng secure, scalable, at flexible na pag-deploy ng AI agent.

## What's the difference between these frameworks?
 
Mukhang maraming pag-ooverlap sa pagitan ng mga framework na ito, pero may ilang pangunahing pagkakaiba pagdating sa kanilang disenyo, kakayahan, at target na mga kaso ng paggamit:
 
- **AutoGen**: Isang experimentation framework na nakatuon sa nangungunang pananaliksik sa multi-agent systems. Ito ang pinakamainam na lugar para mag-eksperimento at mag-prototype ng masalimuot na multi-agent systems.
- **Semantic Kernel**: Isang production-ready na agent library para sa pagbuo ng enterprise agentic applications. Nakatuon ito sa event-driven, distributed agentic applications, na nagpapahintulot ng maraming LLMs at SLMs, mga tool, at single/multi-agent na design patterns.
- **Azure AI Agent Service**: Isang platform at deployment service sa Azure Foundry para sa mga agent. Nag-aalok ito ng konektividad sa mga serbisyo na sinusuportahan ng Azure Found tulad ng Azure OpenAI, Azure AI Search, Bing Search at code execution.
 
Still not sure which one to choose?

### Use Cases
 
Tingnan natin kung makakatulong kami sa pamamagitan ng pagtalakay sa ilang karaniwang kaso ng paggamit:
 
> Q: I'm experimenting, learning and building proof-of-concept agent applications, and I want to be able to build and experiment quickly
>

>A: AutoGen would be a good choice for this scenario, as it focuses on event-driven, distributed agentic applications and supports advanced multi-agent design patterns.

> Q: What makes AutoGen a better choice than Semantic Kernel and Azure AI Agent Service for this use case?
>
> A: AutoGen is specifically designed for event-driven, distributed agentic applications, making it well-suited for automating code generation and data analysis tasks. It provides the necessary tools and capabilities to build complex multi-agent systems efficiently.

>Q: Sounds like Azure AI Agent Service could work here too, it has tools for code generation and more?

>
> A: Yes, Azure AI Agent Service is a platform service for agents and add built-in capabilities for multiple models, Azure AI Search, Bing Search and Azure Functions. It makes it easy to build your agents in the Foundry Portal and deploy them at scale.
 
> Q: I'm still confused just give me one option
>
> A: A great choice is to build your application in Semantic Kernel first and then use Azure AI Agent Service to deploy your agent. This approach allows you to easily persist your agents while leveraging the power to build multi-agent systems in Semantic Kernel. Additionally, Semantic Kernel has a connector in AutoGen, making it easy to use both frameworks together.
 
I-summarize natin ang mga pangunahing pagkakaiba sa isang talahanayan:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Event-driven, distributed agentic applications | Agents, Personas, Functions, Data | Code generation, data analysis tasks |
| Semantic Kernel | Understanding and generating human-like text content | Agents, Modular Components, Collaboration | Natural language understanding, content generation |
| Azure AI Agent Service | Flexible models, enterprise security, Code generation, Tool calling | Modularity, Collaboration, Process Orchestration | Secure, scalable, and flexible AI agent deployment |

What's the ideal use case for each of these frameworks?

## Can I integrate my existing Azure ecosystem tools directly, or do I need standalone solutions?

Ang sagot ay oo, maaari mong i-integrate ang iyong umiiral na Azure ecosystem tools nang direkta sa Azure AI Agent Service lalo na, dahil ito ay ginawa upang gumana nang maayos kasama ang ibang Azure services. Maaari mong halimbawa i-integrate ang Bing, Azure AI Search, at Azure Functions. Mayroon ding malalim na integrasyon sa Microsoft Foundry.

Para sa AutoGen at Semantic Kernel, maaari mo ring i-integrate ang mga ito sa Azure services, ngunit maaaring kailanganin mong tawagin ang mga Azure services mula sa iyong code. Ang isa pang paraan ng integrasyon ay ang paggamit ng Azure SDKs upang makipag-ugnayan sa mga Azure services mula sa iyong mga agent. Bukod pa rito, tulad ng nabanggit, maaari mong gamitin ang Azure AI Agent Service bilang orchestrator para sa iyong mga agent na binuo sa AutoGen o Semantic Kernel na magbibigay ng madaling access sa Azure ecosystem.

## Sample Codes

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Got More Questions about AI Agent Frameworks?

Sumali sa [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) upang makipagkita sa ibang mga nag-aaral, dumalo sa office hours at masagot ang iyong mga tanong tungkol sa AI Agents.

## References

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Serbisyo ng Azure Agent</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel at AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Framework ng Semantic Kernel Python para sa Agent</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Framework ng Semantic Kernel .Net para sa Agent</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Serbisyo ng Azure AI Agent</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Paggamit ng Azure AI Agent Service kasama ang AutoGen / Semantic Kernel upang bumuo ng multi-agent na solusyon</a>

## Previous Lesson

[Panimula sa AI Agents at Mga Kaso ng Paggamit ng Agent](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Pag-unawa sa Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Paunawa:
Ang dokumentong ito ay isinalin gamit ang serbisyong pagsasalin ng AI na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagaman nagsusumikap kaming maging tumpak, pakitandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga pagkakamali o kamalian. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring na opisyal na pinagkukunan. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasalin ng tao. Hindi kami mananagot para sa anumang hindi pagkakaunawaan o maling interpretasyon na nagmumula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->