[![Explorando Frameworks de Agentes de IA](../../../translated_images/pt-PT/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Clique na imagem acima para ver o vídeo desta lição)_

# Explore Frameworks de Agentes de IA

Os frameworks de agentes de IA são plataformas de software concebidas para simplificar a criação, implementação e gestão de agentes de IA. Estes frameworks fornecem aos desenvolvedores componentes pré-construídos, abstrações e ferramentas que agilizam o desenvolvimento de sistemas de IA complexos.

Estes frameworks ajudam os desenvolvedores a focar nos aspetos únicos das suas aplicações ao fornecer abordagens padronizadas para os desafios comuns no desenvolvimento de agentes de IA. Eles melhoram a escalabilidade, acessibilidade e eficiência na construção de sistemas de IA.

## Introdução 

Esta lição irá cobrir:

- O que são os Frameworks de Agentes de IA e o que permitem que os desenvolvedores consigam?
- Como as equipas podem usar estes para prototipar rapidamente, iterar e melhorar as capacidades dos seus agentes?
- Quais as diferenças entre os frameworks e ferramentas criadas pela Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, e <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Posso integrar as minhas ferramentas existentes do ecossistema Azure diretamente, ou preciso de soluções independentes?
- O que é o serviço Azure AI Agents e como este me está a ajudar?

## Objetivos de aprendizagem

Os objetivos desta lição são ajudá-lo a compreender:

- O papel dos Frameworks de Agentes de IA no desenvolvimento de IA.
- Como usar os Frameworks de Agentes de IA para construir agentes inteligentes.
- Capacidades-chave proporcionadas pelos Frameworks de Agentes de IA.
- As diferenças entre AutoGen, Semantic Kernel e Azure AI Agent Service.

## O que são Frameworks de Agentes de IA e o que permitem aos desenvolvedores fazer?

Os frameworks tradicionais de IA podem ajudá-lo a integrar IA nas suas aplicações e a melhorar estas apps das seguintes formas:

- **Personalização**: A IA pode analisar o comportamento e preferências do utilizador para fornecer recomendações, conteúdos e experiências personalizadas.
Exemplo: Serviços de streaming como a Netflix usam IA para sugerir filmes e programas com base no histórico de visualização, aumentando o envolvimento e satisfação do utilizador.
- **Automação e Eficiência**: A IA pode automatizar tarefas repetitivas, simplificar fluxos de trabalho e melhorar a eficiência operacional.
Exemplo: Aplicações de serviço ao cliente usam chatbots com IA para tratar inquéritos comuns, reduzindo tempos de resposta e libertando agentes humanos para questões mais complexas.
- **Melhoria da Experiência do Utilizador**: A IA pode melhorar a experiência geral do utilizador ao fornecer funcionalidades inteligentes como reconhecimento de voz, processamento de linguagem natural e texto preditivo.
Exemplo: Assistentes virtuais como Siri e Google Assistant usam IA para compreender e responder a comandos de voz, facilitando a interação dos utilizadores com os seus dispositivos.

### Tudo isto soa bem, certo? Então, por que precisamos do Framework de Agentes de IA?

Os frameworks de agentes de IA representam algo mais do que apenas frameworks de IA. São projetados para permitir a criação de agentes inteligentes que podem interagir com utilizadores, outros agentes e o ambiente para alcançar objetivos específicos. Estes agentes podem exibir comportamento autónomo, tomar decisões e adaptar-se a condições em mudança. Vamos ver algumas capacidades-chave proporcionadas pelos Frameworks de Agentes de IA:

- **Colaboração e Coordenação entre Agentes**: Permitem a criação de múltiplos agentes de IA que podem trabalhar em conjunto, comunicar e coordenar-se para resolver tarefas complexas.
- **Automação e Gestão de Tarefas**: Fornecem mecanismos para automatizar fluxos de trabalho multi-etapa, delegação de tarefas e gestão dinâmica de tarefas entre agentes.
- **Compreensão e Adaptação Contextual**: Equipam os agentes com a capacidade de entender o contexto, adaptar-se a ambientes em mudança e tomar decisões baseadas em informação em tempo real.

Em resumo, os agentes permitem-lhe fazer mais, levar a automação ao próximo nível, criar sistemas mais inteligentes que podem adaptar-se e aprender com o seu ambiente.

## Como prototipar rapidamente, iterar e melhorar as capacidades do agente?

Este é um campo em rápida evolução, mas existem algumas coisas comuns a maioria dos Frameworks de Agentes de IA que podem ajudá-lo a prototipar e iterar rapidamente, nomeadamente componentes modulares, ferramentas colaborativas e aprendizagem em tempo real. Vamos aprofundar estes pontos:

- **Use Componentes Modulares**: Os SDKs de IA oferecem componentes pré-construídos como conectores de IA e Memória, chamadas de função usando linguagem natural ou plugins de código, modelos de prompt e mais.
- **Aproveite Ferramentas Colaborativas**: Desenhe agentes com papéis e tarefas específicas, permitindo-lhes testar e refinar fluxos de trabalho colaborativos.
- **Aprenda em Tempo Real**: Implemente ciclos de feedback onde os agentes aprendem com as interações e ajustam o seu comportamento dinamicamente.

### Use Componentes Modulares

SDKs como Microsoft Semantic Kernel e LangChain oferecem componentes pré-construídos como conectores de IA, modelos de prompt e gestão de memória.

**Como as equipas podem usar estes**: As equipas podem montar rapidamente estes componentes para criar um protótipo funcional sem começar do zero, permitindo experimentação rápida e iteração.

**Como funciona na prática**: Pode usar um parser pré-construído para extrair informação da entrada do utilizador, um módulo de memória para armazenar e recuperar dados, e um gerador de prompt para interagir com os utilizadores, tudo sem ter de construir estes componentes do zero.

**Exemplo de código**. Vamos ver exemplos de como usar um Conector de IA pré-construído com Semantic Kernel Python e .Net que usa chamada automática de função para o modelo responder à entrada do utilizador:

``` python
# Exemplo em Python do Semantic Kernel

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definir um objeto ChatHistory para conter o contexto da conversa
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definir um plugin de exemplo que contém a função para reservar viagens
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Criar o Kernel
kernel = Kernel()

# Adicionar o plugin de exemplo ao objeto Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definir o conector de IA do Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definir as configurações de pedido para configurar o modelo com invocação automática de funções
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Fazer o pedido ao modelo com o histórico de conversa e as configurações de pedido fornecidas
    # O Kernel contém o exemplo que o modelo irá pedir para invocar
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
    # Example AI Model Response: `O seu voo para Nova Iorque no dia 1 de janeiro de 2025 foi reservado com sucesso. Boa viagem! ✈️🗽`

    # Adicionar a resposta do modelo ao contexto do nosso histórico de conversa
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

O que pode ver neste exemplo é como pode tirar proveito de um parser pré-construído para extrair informações-chave da entrada do utilizador, como a origem, destino e data de uma solicitação de reserva de voo. Esta abordagem modular permite-lhe focar na lógica de alto nível.

### Aproveite Ferramentas Colaborativas

Frameworks como CrewAI, Microsoft AutoGen, e Semantic Kernel facilitam a criação de múltiplos agentes que podem trabalhar em conjunto.

**Como as equipas podem usar estes**: As equipas podem desenhar agentes com papéis e tarefas específicas, permitindo-lhes testar e refinar fluxos de trabalho colaborativos e melhorar a eficiência geral do sistema.

**Como funciona na prática**: Pode criar uma equipa de agentes onde cada agente tem uma função especializada, como recuperação de dados, análise ou tomada de decisões. Estes agentes podem comunicar e partilhar informação para alcançar um objetivo comum, como responder a uma consulta do utilizador ou concluir uma tarefa.

**Exemplo de código (AutoGen)**:

```python
# criar agentes e depois criar um escalonamento round-robin onde possam trabalhar em conjunto, neste caso por ordem

# Agente de Recuperação de Dados
# Agente de Análise de Dados
# Agente de Tomada de Decisões

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

# a conversa termina quando o utilizador disser "APROVAR"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Use asyncio.run(...) ao executar um script.
await Console(stream)
```

O que vê no código anterior é como pode criar uma tarefa que envolve múltiplos agentes a trabalharem juntos para analisar dados. Cada agente realiza uma função específica, e a tarefa é executada coordenando os agentes para alcançar o resultado desejado. Ao criar agentes dedicados com papéis especializados, pode melhorar a eficiência e desempenho da tarefa.

### Aprenda em Tempo Real

Frameworks avançados proporcionam capacidades para compreensão de contexto em tempo real e adaptação.

**Como as equipas podem usar estes**: As equipas podem implementar ciclos de feedback onde os agentes aprendem das interações e ajustam o seu comportamento dinamicamente, levando a melhorias contínuas e refinamento das capacidades.

**Como funciona na prática**: Os agentes podem analisar o feedback dos utilizadores, dados ambientais e resultados das tarefas para atualizar a sua base de conhecimento, ajustar algoritmos de tomada de decisão e melhorar o desempenho ao longo do tempo. Este processo iterativo de aprendizagem permite que os agentes se adaptem a condições em mudança e preferências dos utilizadores, aumentando a eficácia geral do sistema.

## Quais são as diferenças entre os frameworks AutoGen, Semantic Kernel e Azure AI Agent Service?

Existem muitas formas de comparar estes frameworks, mas vamos olhar para algumas diferenças-chave em termos do seu design, capacidades e casos de uso-alvo:

## AutoGen

AutoGen é um framework open-source desenvolvido pelo AI Frontiers Lab da Microsoft Research. Foca-se em aplicações *agenticas* distribuídas e orientadas por eventos, permitindo múltiplos LLMs e SLMs, ferramentas, e padrões avançados de design multi-agente.

O AutoGen é construído em torno do conceito core de agentes, que são entidades autónomas que podem perceber o ambiente, tomar decisões e executar ações para alcançar objetivos específicos. Os agentes comunicam-se através de mensagens assíncronas, permitindo que trabalhem independentemente e em paralelo, melhorando a escalabilidade e responsividade do sistema.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Os agentes baseiam-se no modelo ator</a>. Segundo a Wikipédia, um ator é _a unidade básica da computação concorrente. Em resposta a uma mensagem que recebe, o ator pode: tomar decisões locais, criar mais atores, enviar mais mensagens e determinar como responder à próxima mensagem recebida_.

**Casos de uso**: Automação de geração de código, tarefas de análise de dados, e construção de agentes personalizados para funções de planeamento e investigação.

Aqui estão alguns conceitos-chave do AutoGen:

- **Agentes**. Um agente é uma entidade de software que:
  - **Comunica-se via mensagens**, estas mensagens podem ser síncronas ou assíncronas.
  - **Mantém o seu próprio estado**, que pode ser modificado por mensagens recebidas.
  - **Executa ações** em resposta a mensagens recebidas ou alterações no seu estado. Estas ações podem modificar o estado do agente e produzir efeitos externos, como atualizar registos de mensagens, enviar novas mensagens, executar código, ou fazer chamadas API.
    
  Aqui tem um curto excerto de código onde cria o seu próprio agente com capacidades de Chat:

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
    
    No código anterior, `MyAgent` foi criado e herda de `RoutedAgent`. Tem um manipulador de mensagens que imprime o conteúdo da mensagem e depois envia uma resposta usando o delegador `AssistantAgent`. Note especialmente como atribuímos a `self._delegate` uma instância de `AssistantAgent` que é um agente pré-construído que pode lidar com conclusões de chat.


    Vamos informar o AutoGen sobre este tipo de agente e arrancar o programa a seguir:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Iniciar o processamento de mensagens em segundo plano.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    No código anterior os agentes são registados no runtime e depois uma mensagem é enviada ao agente resultando na seguinte saída:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multi-agentes**. O AutoGen suporta a criação de múltiplos agentes que podem trabalhar em conjunto para realizar tarefas complexas. Os agentes podem comunicar, partilhar informação e coordenar as suas ações para resolver problemas de forma mais eficiente. Para criar um sistema multi-agente, pode definir diferentes tipos de agentes com funções e papéis especializados, como recuperação de dados, análise, tomada de decisões e interação com utilizadores. Vamos ver como se pareceria essa criação para termos uma noção:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Exemplo de declaração de um Agente
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # A utilizar o tipo topic como tipo de agente.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # declarações restantes encurtadas por brevidade

    # Chat de grupo
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

    No código anterior temos um `GroupChatManager` que está registado no runtime. Este gestor é responsável por coordenar as interações entre diferentes tipos de agentes, como escritores, ilustradores, editores e utilizadores.

- **Runtime de Agentes**. O framework fornece um ambiente runtime, permitindo comunicação entre agentes, gerindo as suas identidades e ciclos de vida, e impondo fronteiras de segurança e privacidade. Isto significa que pode executar os seus agentes num ambiente seguro e controlado, garantindo que podem interagir de forma segura e eficiente. Existem dois runtimes de interesse:
  - **Runtime autónomo**. É uma boa escolha para aplicações de processo único onde todos os agentes são implementados na mesma linguagem de programação e correm no mesmo processo. Aqui está uma ilustração de como funciona:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Runtime autónomo</a>   
Stack da aplicação

    *os agentes comunicam via mensagens através do runtime, e o runtime gere o ciclo de vida dos agentes*

  - **Runtime distribuído**, é adequado para aplicações multi-processo onde agentes podem ser implementados em diferentes linguagens de programação e executados em máquinas diferentes. Aqui está uma ilustração de como funciona:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Runtime distribuído</a>

## Semantic Kernel + Framework de Agentes

Semantic Kernel é um SDK de orquestração de IA pronto para empresa. Consiste em conectores de IA e memória, junto com um Framework de Agentes.

Vamos primeiro abordar alguns componentes fundamentais:

- **Conectores de IA**: Esta é uma interface com serviços de IA externos e fontes de dados para uso tanto em Python como em C#.

  ```python
  # Kernel semântico Python
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

    Aqui tem um exemplo simples de como pode criar um kernel e adicionar um serviço de conclusão de chat. O Semantic Kernel cria uma ligação a um serviço externo de IA, neste caso, Azure OpenAI Chat Completion.

- **Plugins**: Estes encapsulam funções que uma aplicação pode usar. Existem plugins prontos a usar e personalizados que pode criar. Um conceito relacionado é o de "funções prompt". Em vez de fornecer indicações em linguagem natural para invocação de funções, propaga certas funções para o modelo. Com base no contexto atual do chat, o modelo pode escolher invocar uma destas funções para completar um pedido ou consulta. Aqui está um exemplo:

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

    Aqui, tem primeiro um modelo prompt `skPrompt` que deixa espaço para o utilizador inserir texto, `$userInput`. Depois cria a função kernel `SummarizeText` e, em seguida, importa-a para o kernel com o nome do plugin `SemanticFunctions`. Note o nome da função que ajuda o Semantic Kernel a entender o que a função faz e quando deve ser chamada.

- **Função nativa**: Há também funções nativas que o framework pode chamar diretamente para executar a tarefa. Aqui está um exemplo de uma função a recuperar conteúdo de um ficheiro:

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

- **Memória**: Abstrai e simplifica a gestão do contexto para aplicações de IA. A ideia com memória é que isto é algo que o LLM deve saber. Pode armazenar esta informação numa store de vetores, que acaba por ser uma base de dados na memória, uma base de dados de vetores ou similar. Aqui está um exemplo de um cenário muito simplificado onde *factos* são adicionados à memória:

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

Estes factos são então armazenados na coleção de memória `SummarizedAzureDocs`. Este é um exemplo muito simplificado, mas pode ver como pode armazenar informação na memória para o LLM usar.

Então, estes são os básicos do framework Semantic Kernel, e o que dizer do Agent Framework?

## Azure AI Agent Service

O Azure AI Agent Service é uma adição mais recente, introduzida na Microsoft Ignite 2024. Permite o desenvolvimento e a implementação de agentes de IA com modelos mais flexíveis, como chamar diretamente LLMs open-source como Llama 3, Mistral e Cohere.

O Azure AI Agent Service fornece mecanismos de segurança empresarial mais robustos e métodos de armazenamento de dados, tornando-o adequado para aplicações empresariais.

Funciona imediatamente com frameworks de orquestração multi-agente como AutoGen e Semantic Kernel.

Este serviço está atualmente em Preview Público e suporta Python e C# para construir agentes.

Usando Semantic Kernel Python, podemos criar um Azure AI Agent com um plugin definido pelo utilizador:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Define um plugin de exemplo para a amostra
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
        # Criar definição do agente
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Criar o Agente AzureAI usando o cliente e a definição do agente definidos
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Criar um thread para conter a conversa
        # Se nenhum thread for fornecido, um novo thread será
        # criado e devolvido com a resposta inicial
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
                # Invocar o agente para o thread especificado
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

### Conceitos principais

O Azure AI Agent Service tem os seguintes conceitos principais:

- **Agent**. O Azure AI Agent Service integra-se com o Microsoft Foundry. Dentro do AI Foundry, um AI Agent atua como um microserviço "inteligente" que pode ser usado para responder a perguntas (RAG), executar ações ou automatizar fluxos de trabalho completamente. Isto é conseguido combinando o poder dos modelos de IA generativa com ferramentas que lhe permitem aceder e interagir com fontes de dados do mundo real. Aqui está um exemplo de um agente:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Neste exemplo, um agente é criado com o modelo `gpt-4o-mini`, o nome `my-agent` e as instruções `You are helpful agent`. O agente está equipado com ferramentas e recursos para executar tarefas de interpretação de código.

- **Thread e mensagens**. O thread é outro conceito importante. Representa uma conversa ou interação entre um agente e um utilizador. Os threads podem ser usados para acompanhar o progresso da conversa, armazenar informações de contexto e gerir o estado da interação. Aqui está um exemplo de um thread:

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

    No código anterior, é criado um thread. Depois, é enviada uma mensagem para o thread. Ao chamar `create_and_process_run`, o agente é solicitado a trabalhar no thread. Finalmente, as mensagens são recuperadas e registadas para ver a resposta do agente. As mensagens indicam o progresso da conversa entre o utilizador e o agente. Também é importante entender que as mensagens podem ser de diferentes tipos, como texto, imagem ou ficheiro, que é o resultado do trabalho do agente, por exemplo uma imagem ou uma resposta de texto. Como programador, pode usar esta informação para processar ainda mais a resposta ou apresentá-la ao utilizador.

- **Integra-se com outros frameworks de IA**. O Azure AI Agent Service pode interagir com outros frameworks como AutoGen e Semantic Kernel, o que significa que pode construir parte da sua aplicação num destes frameworks e, por exemplo, usar o Agent Service como orquestrador, ou pode construir tudo no Agent Service.

**Casos de Uso**: O Azure AI Agent Service é concebido para aplicações empresariais que requerem uma implementação de agentes de IA segura, escalável e flexível.

## Qual é a diferença entre estes frameworks?

Parece que há muita sobreposição entre estes frameworks, mas existem algumas diferenças principais em termos do seu design, capacidades e casos de uso alvo:

- **AutoGen**: É um framework de experimentação focado em investigação avançada em sistemas multi-agente. É o melhor local para experimentar e prototipar sistemas multi-agente sofisticados.
- **Semantic Kernel**: É uma biblioteca pronta para produção para construir aplicações empresariais agentic. Foca-se em aplicações agentic distribuídas e orientadas por eventos, permitindo múltiplos LLMs e SLMs, ferramentas, e padrões de design de agente único/múltiplo.
- **Azure AI Agent Service**: É uma plataforma e serviço de implementação no Azure Foundry para agentes. Oferece conectividade integrada com serviços suportados pela Azure Foundry, como Azure OpenAI, Azure AI Search, Bing Search e execução de código.

Ainda não tem a certeza de qual escolher?

### Casos de Uso

Vamos ver se o podemos ajudar percorrendo alguns casos de uso comuns:

> Q: Estou a experimentar, a aprender e a construir aplicações de agentes prova de conceito, e quero ser capaz de construir e experimentar rapidamente
>

> A: AutoGen seria uma boa escolha para este cenário, pois foca-se em aplicações agentic distribuídas e orientadas por eventos e suporta padrões avançados de design multi-agente.

> Q: O que torna o AutoGen uma escolha melhor do que o Semantic Kernel e o Azure AI Agent Service para este caso de uso?
>
> A: O AutoGen é especificamente desenhado para aplicações agentic distribuídas e orientadas por eventos, tornando-o adequado para automatizar tarefas de geração de código e análise de dados. Fornece as ferramentas e capacidades necessárias para construir sistemas multi-agente complexos de forma eficiente.

> Q: Parece que o Azure AI Agent Service também poderia funcionar aqui, tem ferramentas para geração de código e mais?

>
> A: Sim, o Azure AI Agent Service é um serviço de plataforma para agentes e inclui capacidades integradas para múltiplos modelos, Azure AI Search, Bing Search e Azure Functions. Facilita a construção dos seus agentes no Portal Foundry e a sua implementação em escala.

> Q: Ainda estou confuso, dê-me só uma opção
>
> A: Uma excelente escolha é construir a sua aplicação primeiro no Semantic Kernel e depois usar o Azure AI Agent Service para implementar o seu agente. Esta abordagem permite-lhe persistir facilmente os seus agentes enquanto aproveita o poder para construir sistemas multi-agente no Semantic Kernel. Além disso, o Semantic Kernel tem um conector no AutoGen, facilitando o uso de ambos os frameworks em conjunto.

Vamos resumir as diferenças principais numa tabela:

| Framework | Foco | Conceitos Principais | Casos de Uso |
| --- | --- | --- | --- |
| AutoGen | Aplicações agentic distribuídas e orientadas por eventos | Agentes, Personas, Funções, Dados | Geração de código, tarefas de análise de dados |
| Semantic Kernel | Compreensão e geração de conteúdo de texto semelhante ao humano | Agentes, Componentes Modulares, Colaboração | Compreensão de linguagem natural, geração de conteúdo |
| Azure AI Agent Service | Modelos flexíveis, segurança empresarial, geração de código, chamada de ferramentas | Modularidade, Colaboração, Orquestração de Processos | Implementação segura, escalável e flexível de agentes de IA |

Qual é o caso de uso ideal para cada um destes frameworks?

## Posso integrar as minhas ferramentas existentes do ecossistema Azure diretamente, ou preciso de soluções autónomas?

A resposta é sim, pode integrar as suas ferramentas existentes do ecossistema Azure diretamente com o Azure AI Agent Service, especialmente porque foi construído para funcionar perfeitamente com outros serviços Azure. Pode, por exemplo, integrar Bing, Azure AI Search e Azure Functions. Há também uma integração profunda com o Microsoft Foundry.

Para AutoGen e Semantic Kernel, também pode integrar com serviços Azure, mas pode ser necessário chamar os serviços Azure a partir do seu código. Outra forma de integrar é usar os SDKs Azure para interagir com serviços Azure a partir dos seus agentes. Além disso, como foi mencionado, pode usar o Azure AI Agent Service como orquestrador para os seus agentes construídos em AutoGen ou Semantic Kernel, o que dá acesso fácil ao ecossistema Azure.

## Exemplos de Código

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Tem Mais Perguntas sobre AI Agent Frameworks?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar em horas de atendimento e obter respostas às suas perguntas sobre AI Agents.

## Referências

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel and AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## Aula Anterior

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## Próxima Aula

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento foi traduzido utilizando o serviço de tradução automática [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, tenha em atenção que traduções automáticas podem conter erros ou imprecisões. O documento original na sua língua nativa deve ser considerado a fonte oficial. Para informações críticas, recomenda-se uma tradução profissional efetuada por seres humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações erradas resultantes da utilização desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->