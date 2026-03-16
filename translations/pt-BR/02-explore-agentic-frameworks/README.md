[![Explorando frameworks de agentes de IA](../../../translated_images/pt-BR/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Clique na imagem acima para assistir ao vídeo desta lição)_

# Explorar frameworks de agentes de IA

Frameworks de agentes de IA são plataformas de software projetadas para simplificar a criação, implantação e gerenciamento de agentes de IA. Esses frameworks fornecem aos desenvolvedores componentes, abstrações e ferramentas pré-construídas que agilizam o desenvolvimento de sistemas de IA complexos.

Esses frameworks ajudam os desenvolvedores a se concentrarem nos aspectos únicos de suas aplicações, oferecendo abordagens padronizadas para desafios comuns no desenvolvimento de agentes de IA. Eles aumentam a escalabilidade, acessibilidade e eficiência na construção de sistemas de IA.

## Introdução 

Esta lição cobrirá:

- O que são frameworks de agentes de IA e o que eles permitem que os desenvolvedores realizem?
- Como as equipes podem usar esses frameworks para prototipar rapidamente, iterar e melhorar as capacidades de seus agentes?
- Quais são as diferenças entre os frameworks e ferramentas criadas pela Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> e <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- Posso integrar minhas ferramentas existentes do ecossistema Azure diretamente ou preciso de soluções independentes?
- O que é o Azure AI Agent Service e como isso está me ajudando?

## Objetivos de aprendizagem

Os objetivos desta lição são ajudar você a entender:

- O papel dos frameworks de agentes de IA no desenvolvimento de IA.
- Como aproveitar frameworks de agentes de IA para construir agentes inteligentes.
- Capacidades principais habilitadas por frameworks de agentes de IA.
- As diferenças entre AutoGen, Semantic Kernel e Azure AI Agent Service.

## O que são frameworks de agentes de IA e o que eles permitem que os desenvolvedores façam?

Frameworks tradicionais de IA podem ajudar você a integrar IA em seus aplicativos e tornar esses apps melhores das seguintes maneiras:

- **Personalização**: A IA pode analisar o comportamento e as preferências do usuário para fornecer recomendações, conteúdo e experiências personalizadas.
Exemplo: Serviços de streaming como Netflix usam IA para sugerir filmes e séries com base no histórico de visualização, aumentando o engajamento e a satisfação do usuário.
- **Automação e Eficiência**: A IA pode automatizar tarefas repetitivas, otimizar fluxos de trabalho e melhorar a eficiência operacional.
Exemplo: Aplicativos de atendimento ao cliente usam chatbots com IA para lidar com consultas comuns, reduzindo os tempos de resposta e liberando agentes humanos para questões mais complexas.
- **Melhoria da Experiência do Usuário**: A IA pode aprimorar a experiência geral do usuário fornecendo recursos inteligentes como reconhecimento de voz, processamento de linguagem natural e texto preditivo.
Exemplo: Assistentes virtuais como Siri e Google Assistant usam IA para entender e responder a comandos de voz, facilitando a interação dos usuários com seus dispositivos.

### Tudo isso soa ótimo, certo? Então por que precisamos do Framework de Agentes de IA?

Frameworks de agentes de IA representam algo além dos frameworks tradicionais de IA. Eles são projetados para permitir a criação de agentes inteligentes que podem interagir com usuários, outros agentes e o ambiente para alcançar objetivos específicos. Esses agentes podem exibir comportamento autônomo, tomar decisões e se adaptar a condições em mudança. Vamos ver algumas capacidades-chave habilitadas pelos frameworks de agentes de IA:

- **Colaboração e Coordenação entre Agentes**: Possibilitam a criação de múltiplos agentes de IA que podem trabalhar juntos, comunicar-se e coordenar-se para resolver tarefas complexas.
- **Automação e Gestão de Tarefas**: Fornecem mecanismos para automatizar fluxos de trabalho de múltiplas etapas, delegação de tarefas e gestão dinâmica de tarefas entre agentes.
- **Compreensão Contextual e Adaptação**: Equipam os agentes com a habilidade de entender o contexto, adaptar-se a ambientes em mudança e tomar decisões baseadas em informações em tempo real.

Em resumo, agentes permitem que você faça mais: levar a automação a um novo nível e criar sistemas mais inteligentes que podem se adaptar e aprender com seu ambiente.

## Como prototipar rapidamente, iterar e melhorar as capacidades do agente?

Este é um cenário em rápida evolução, mas há algumas práticas comuns na maioria dos frameworks de agentes de IA que podem ajudar você a prototipar e iterar rapidamente, como componentes modulares, ferramentas colaborativas e aprendizado em tempo real. Vamos aprofundar nesses pontos:

- **Use Componentes Modulares**: SDKs de IA oferecem componentes pré-construídos, como conectores de IA e Memória, chamada de função usando linguagem natural ou plugins de código, templates de prompts e mais.
- **Aproveite Ferramentas Colaborativas**: Projete agentes com papéis e tarefas específicas, permitindo que testem e refinem fluxos de trabalho colaborativos.
- **Aprenda em Tempo Real**: Implemente loops de feedback onde os agentes aprendem com as interações e ajustam seu comportamento dinamicamente.

### Use Componentes Modulares

SDKs como Microsoft Semantic Kernel e LangChain oferecem componentes pré-construídos como conectores de IA, templates de prompt e gerenciamento de memória.

**Como as equipes podem usar isso**: As equipes podem montar rapidamente esses componentes para criar um protótipo funcional sem começar do zero, permitindo experimentação e iteração rápidas.

**Como funciona na prática**: Você pode usar um parser pré-construído para extrair informações da entrada do usuário, um módulo de memória para armazenar e recuperar dados e um gerador de prompts para interagir com os usuários, tudo sem precisar construir esses componentes do zero.

**Exemplo de código**. Vamos ver exemplos de como você pode usar um conector de IA pré-construído com Semantic Kernel em Python e .Net que usa auto-function calling para fazer o modelo responder à entrada do usuário:

``` python
# Exemplo de Semantic Kernel em Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Defina um objeto ChatHistory para manter o contexto da conversa
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Defina um plugin de exemplo que contém a função para reservar viagens
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Crie o Kernel
kernel = Kernel()

# Adicione o plugin de exemplo ao objeto Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Defina o Conector de IA Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Defina as configurações da solicitação para configurar o modelo com chamada automática de função
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Faça a solicitação ao modelo para o histórico de chat e configurações de solicitação fornecidos
    # O Kernel contém o exemplo que o modelo solicitará para invocar
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
    # Exemplo de resposta do modelo de IA: `Seu voo para Nova York em 1º de janeiro de 2025 foi reservado com sucesso. Boa viagem! ✈️🗽`

    # Adicione a resposta do modelo ao nosso contexto do histórico de chat
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

O que você pode ver a partir deste exemplo é como você pode aproveitar um parser pré-construído para extrair informações-chave da entrada do usuário, como origem, destino e data de uma solicitação de reserva de voo. Essa abordagem modular permite que você se concentre na lógica de alto nível.

### Aproveite Ferramentas Colaborativas

Frameworks como CrewAI, Microsoft AutoGen e Semantic Kernel facilitam a criação de múltiplos agentes que podem trabalhar juntos.

**Como as equipes podem usar isso**: As equipes podem projetar agentes com papéis e tarefas específicas, permitindo que testem e refinem fluxos de trabalho colaborativos e melhorem a eficiência geral do sistema.

**Como funciona na prática**: Você pode criar uma equipe de agentes onde cada agente tem uma função especializada, como recuperação de dados, análise ou tomada de decisão. Esses agentes podem se comunicar e compartilhar informações para alcançar um objetivo comum, como responder a uma consulta do usuário ou completar uma tarefa.

**Exemplo de código (AutoGen)**:

```python
# criando agentes, depois criando uma programação round robin onde eles podem trabalhar juntos, neste caso em ordem

# Agente de Recuperação de Dados
# Agente de Análise de Dados
# Agente de Tomada de Decisão

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

# a conversa termina quando o usuário diz "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Use asyncio.run(...) ao executar em um script.
await Console(stream)
```

O que você vê no código anterior é como você pode criar uma tarefa que envolve múltiplos agentes trabalhando juntos para analisar dados. Cada agente executa uma função específica, e a tarefa é realizada coordenando os agentes para alcançar o resultado desejado. Ao criar agentes dedicados com papéis especializados, você pode melhorar a eficiência e o desempenho das tarefas.

### Aprenda em Tempo Real

Frameworks avançados fornecem capacidades para compreensão de contexto em tempo real e adaptação.

**Como as equipes podem usar isso**: As equipes podem implementar loops de feedback onde os agentes aprendem com as interações e ajustam seu comportamento dinamicamente, levando a uma melhoria contínua e refinamento de capacidades.

**Como funciona na prática**: Os agentes podem analisar o feedback do usuário, dados do ambiente e resultados das tarefas para atualizar sua base de conhecimento, ajustar algoritmos de tomada de decisão e melhorar o desempenho ao longo do tempo. Esse processo iterativo de aprendizado permite que os agentes se adaptem a condições e preferências dos usuários em mudança, aumentando a eficácia geral do sistema.

## Quais são as diferenças entre os frameworks AutoGen, Semantic Kernel e Azure AI Agent Service?

Existem muitas maneiras de comparar esses frameworks, mas vamos ver algumas diferenças-chave em termos de design, capacidades e casos de uso alvo:

## AutoGen

AutoGen é um framework de código aberto desenvolvido pelo AI Frontiers Lab da Microsoft Research. Ele foca em aplicações *agentic* distribuídas e orientadas a eventos, permitindo múltiplos LLMs e SLMs, ferramentas e padrões avançados de design multi-agente.

AutoGen é construído em torno do conceito central de agentes, que são entidades autônomas que podem perceber seu ambiente, tomar decisões e realizar ações para alcançar objetivos específicos. Os agentes se comunicam por meio de mensagens assíncronas, permitindo que trabalhem de forma independente e em paralelo, aumentando a escalabilidade e a capacidade de resposta do sistema.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agentes são baseados no modelo de ator</a>. De acordo com a Wikipedia, um ator é _o bloco de construção básico da computação concorrente. Em resposta a uma mensagem que recebe, um ator pode: tomar decisões locais, criar mais atores, enviar mais mensagens e determinar como responder à próxima mensagem recebida_.

**Casos de uso**: Automatização de geração de código, tarefas de análise de dados e construção de agentes personalizados para funções de planejamento e pesquisa.

Aqui estão alguns conceitos centrais importantes do AutoGen:

- **Agentes**. Um agente é uma entidade de software que:
  - **Se comunica via mensagens**, essas mensagens podem ser síncronas ou assíncronas.
  - **Mantém seu próprio estado**, que pode ser modificado por mensagens recebidas.
  - **Executa ações** em resposta a mensagens recebidas ou mudanças em seu estado. Essas ações podem modificar o estado do agente e produzir efeitos externos, como atualizar logs de mensagens, enviar novas mensagens, executar código ou fazer chamadas de API.
    
  Aqui você tem um pequeno trecho de código no qual você cria seu próprio agente com capacidades de chat:

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
    
    No código anterior, `MyAgent` foi criado e herda de `RoutedAgent`. Ele possui um manipulador de mensagens que imprime o conteúdo da mensagem e então envia uma resposta usando o delegado `AssistantAgent`. Observe especialmente como atribuímos a `self._delegate` uma instância de `AssistantAgent`, que é um agente pré-construído capaz de lidar com completions de chat.


    Vamos informar ao AutoGen sobre esse tipo de agente e iniciar o programa a seguir:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Iniciar o processamento de mensagens em segundo plano.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    No código anterior os agentes são registrados no runtime e então uma mensagem é enviada ao agente resultando na seguinte saída:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Múltiplos agentes**. O AutoGen suporta a criação de múltiplos agentes que podem trabalhar juntos para atingir tarefas complexas. Os agentes podem se comunicar, compartilhar informações e coordenar suas ações para resolver problemas de forma mais eficiente. Para criar um sistema multi-agente, você pode definir diferentes tipos de agentes com funções e papéis especializados, como recuperação de dados, análise, tomada de decisão e interação com o usuário. Vamos ver como essa criação se parece para termos uma noção:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Exemplo de declaração de um Agente
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Usando o tipo de tópico como o tipo do agente.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="SUA_CHAVE_DE_API",
        ),
        ),
    )

    # declarações restantes abreviadas para brevidade

    # Chat em grupo
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="SUA_CHAVE_DE_API",
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

    No código anterior temos um `GroupChatManager` que é registrado no runtime. Esse gerente é responsável por coordenar as interações entre diferentes tipos de agentes, como redatores, ilustradores, editores e usuários.

- **Runtime de Agentes**. O framework fornece um ambiente de runtime, possibilitando a comunicação entre agentes, gerenciando suas identidades e ciclos de vida, e aplicando limites de segurança e privacidade. Isso significa que você pode executar seus agentes em um ambiente seguro e controlado, garantindo que eles possam interagir com segurança e eficiência. Existem dois runtimes de interesse:
  - **Runtime independente**. Esta é uma boa escolha para aplicações de processo único onde todos os agentes são implementados na mesma linguagem de programação e executados no mesmo processo. Aqui está uma ilustração de como funciona:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Runtime independente</a>   
Application stack

    *agentes se comunicam via mensagens através do runtime, e o runtime gerencia o ciclo de vida dos agentes*

  - **Runtime distribuído**, é adequado para aplicações multi-processo onde agentes podem ser implementados em diferentes linguagens de programação e executados em máquinas distintas. Aqui está uma ilustração de como funciona:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Runtime distribuído</a>

## Semantic Kernel + Agent Framework

Semantic Kernel é um SDK de orquestração de IA pronto para uso empresarial. Ele consiste em conectores de IA e memória, juntamente com um Agent Framework.

Vamos primeiro cobrir alguns componentes centrais:

- **Conectores de IA**: Esta é uma interface com serviços de IA externos e fontes de dados para uso tanto em Python quanto em C#.

  ```python
  # Kernel Semântico Python
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

    Aqui você tem um exemplo simples de como criar um kernel e adicionar um serviço de completions de chat. O Semantic Kernel cria uma conexão com um serviço de IA externo, neste caso, o Azure OpenAI Chat Completion.

- **Plugins**: Esses encapsulam funções que uma aplicação pode usar. Existem plugins prontos e também personalizados que você pode criar. Um conceito relacionado é o de "funções de prompt". Em vez de fornecer indícios em linguagem natural para invocar funções, você anuncia certas funções ao modelo. Com base no contexto atual do chat, o modelo pode escolher chamar uma dessas funções para completar uma solicitação ou consulta. Aqui está um exemplo:

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

    Aqui, você primeiro tem um template de prompt `skPrompt` que deixa espaço para o usuário inserir texto, `$userInput`. Em seguida você cria a função do kernel `SummarizeText` e então a importa para o kernel com o nome de plugin `SemanticFunctions`. Observe o nome da função que ajuda o Semantic Kernel a entender o que a função faz e quando ela deve ser chamada.

- **Função nativa**: Também há funções nativas que o framework pode chamar diretamente para realizar a tarefa. Aqui está um exemplo de tal função recuperando o conteúdo de um arquivo:

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

- **Memória**: Abstrai e simplifica o gerenciamento de contexto para aplicações de IA. A ideia com memória é que isso é algo que o LLM deveria saber. Você pode armazenar essa informação em um vector store que acaba se tornando um banco de dados em memória, ou um banco de dados vetorial ou similar. Aqui está um exemplo de um cenário muito simplificado onde *fatos* são adicionados à memória:

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

    Esses fatos são então armazenados na coleção de memória `SummarizedAzureDocs`. Este é um exemplo bem simplificado, mas você pode ver como pode armazenar informações na memória para o LLM usar.

So that's the basics of the Semantic Kernel framework, what about the Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service é uma adição mais recente, introduzida no Microsoft Ignite 2024. Ele permite o desenvolvimento e a implantação de agentes de IA com modelos mais flexíveis, como chamar diretamente LLMs de código aberto como Llama 3, Mistral e Cohere.

Azure AI Agent Service oferece mecanismos de segurança empresarial mais robustos e métodos de armazenamento de dados, tornando-o adequado para aplicações corporativas. 

Funciona pronto para uso com frameworks de orquestração multiagente como AutoGen e Semantic Kernel.

Esse serviço está atualmente em Public Preview e suporta Python e C# para a construção de agentes.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Define um plugin de exemplo para o exemplo
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
        # Criar definição de agente
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Criar o Agente AzureAI usando o cliente e a definição de agente definidos
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Criar um tópico para manter a conversa
        # Se nenhum tópico for fornecido, um novo tópico será
        # criado e retornado com a resposta inicial
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
                # Invocar o agente para o tópico especificado
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

Azure AI Agent Service possui os seguintes conceitos principais:

- **Agent**. O Azure AI Agent Service integra-se ao Microsoft Foundry. Dentro do AI Foundry, um agente de IA atua como um microsserviço "inteligente" que pode ser usado para responder a perguntas (RAG), executar ações, ou automatizar completamente fluxos de trabalho. Ele consegue isso combinando o poder de modelos generativos de IA com ferramentas que permitem acessar e interagir com fontes de dados do mundo real. Aqui está um exemplo de um agente:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Neste exemplo, um agente é criado com o modelo `gpt-4o-mini`, um nome `my-agent`, e instruções `You are helpful agent`. O agente está equipado com ferramentas e recursos para realizar tarefas de interpretação de código.

- **Thread and messages**. O thread é outro conceito importante. Ele representa uma conversa ou interação entre um agente e um usuário. Threads podem ser usados para acompanhar o progresso de uma conversa, armazenar informações de contexto e gerenciar o estado da interação. Aqui está um exemplo de um thread:

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

    No código anterior, um thread é criado. Em seguida, uma mensagem é enviada para o thread. Ao chamar `create_and_process_run`, o agente é solicitado a executar trabalho no thread. Por fim, as mensagens são buscadas e registradas para ver a resposta do agente. As mensagens indicam o progresso da conversa entre o usuário e o agente. Também é importante entender que as mensagens podem ser de diferentes tipos, como texto, imagem ou arquivo; ou seja, o trabalho do agente pode ter resultado, por exemplo, em uma imagem ou em uma resposta de texto. Como desenvolvedor, você pode então usar essas informações para processar a resposta ou apresentá-la ao usuário.

- **Integrates with other AI frameworks**. O Azure AI Agent Service pode interagir com outros frameworks como AutoGen e Semantic Kernel, o que significa que você pode construir parte do seu app em um desses frameworks e, por exemplo, usar o Agent service como um orquestrador, ou você pode construir tudo no Agent service.

**Use Cases**: O Azure AI Agent Service é projetado para aplicações empresariais que exigem implantação de agentes de IA segura, escalável e flexível.

## Qual é a diferença entre esses frameworks?
 
Parece que há muita sobreposição entre esses frameworks, mas existem diferenças importantes em termos de design, capacidades e casos de uso alvo:
 
- **AutoGen**: É um framework de experimentação focado em pesquisa de ponta em sistemas multiagente. É o melhor lugar para experimentar e prototipar sistemas multiagente sofisticados.
- **Semantic Kernel**: É uma biblioteca pronta para produção para construir aplicações agenticas empresariais. Foca em aplicações agenticas distribuídas e orientadas a eventos, permitindo múltiplos LLMs e SLMs, ferramentas e padrões de design de agente único/múltiplo.
- **Azure AI Agent Service**: É uma plataforma e serviço de implantação no Azure Foundry para agentes. Oferece conectividade a serviços suportados pelo Azure Found como Azure OpenAI, Azure AI Search, Bing Search e execução de código.
 
Ainda não tem certeza de qual escolher?

### Casos de Uso
 
Vamos ver se podemos ajudar você passando por alguns casos de uso comuns:
 
> Q: Estou experimentando, aprendendo e construindo aplicações de agente como prova de conceito, e quero conseguir desenvolver e experimentar rapidamente
>

>A: AutoGen seria uma boa escolha para este cenário, pois foca em aplicações agenticas distribuídas e orientadas a eventos e suporta padrões de design multiagente avançados.

> Q: O que torna o AutoGen uma escolha melhor do que o Semantic Kernel e o Azure AI Agent Service para este caso de uso?
>
> A: O AutoGen é especificamente projetado para aplicações agenticas distribuídas e orientadas a eventos, tornando-o bem adequado para automatizar geração de código e tarefas de análise de dados. Ele fornece as ferramentas e capacidades necessárias para construir sistemas multiagente complexos de forma eficiente.

>Q: Parece que o Azure AI Agent Service também poderia funcionar aqui, ele tem ferramentas para geração de código e mais?

>
> A: Sim, o Azure AI Agent Service é um serviço de plataforma para agentes e adiciona capacidades integradas para múltiplos modelos, Azure AI Search, Bing Search e Azure Functions. Facilita construir seus agentes no Foundry Portal e implantá-los em escala.
 
> Q: Ainda estou confuso, apenas me dê uma opção
>
> A: Uma ótima opção é construir sua aplicação primeiro no Semantic Kernel e então usar o Azure AI Agent Service para implantar seu agente. Essa abordagem permite persistir facilmente seus agentes enquanto aproveita o poder de construir sistemas multiagente no Semantic Kernel. Além disso, o Semantic Kernel tem um conector no AutoGen, facilitando o uso de ambos os frameworks juntos.
 
Vamos resumir as principais diferenças em uma tabela:

| Framework | Foco | Conceitos Principais | Casos de Uso |
| --- | --- | --- | --- |
| AutoGen | Aplicações agenticas distribuídas e orientadas a eventos | Agentes, Personas, Funções, Dados | Geração de código, tarefas de análise de dados |
| Semantic Kernel | Compreensão e geração de conteúdo textual semelhante ao humano | Agentes, Componentes Modulares, Colaboração | Compreensão de linguagem natural, geração de conteúdo |
| Azure AI Agent Service | Modelos flexíveis, segurança empresarial, geração de código, invocação de ferramentas | Modularidade, Colaboração, Orquestração de Processos | Implantação de agentes de IA segura, escalável e flexível |

What's the ideal use case for each of these frameworks?

## Posso integrar minhas ferramentas existentes do ecossistema Azure diretamente, ou preciso de soluções independentes?

A resposta é sim, você pode integrar suas ferramentas existentes do ecossistema Azure diretamente com o Azure AI Agent Service especialmente, isso porque ele foi construído para funcionar perfeitamente com outros serviços do Azure. Você pode, por exemplo, integrar o Bing, Azure AI Search e Azure Functions. Também há integração profunda com o Microsoft Foundry.

Para AutoGen e Semantic Kernel, você também pode integrar com serviços do Azure, mas pode ser necessário chamar os serviços do Azure a partir do seu código. Outra forma de integrar é usar os SDKs do Azure para interagir com os serviços do Azure a partir dos seus agentes. Além disso, como foi mencionado, você pode usar o Azure AI Agent Service como um orquestrador para seus agentes construídos em AutoGen ou Semantic Kernel, o que daria acesso fácil ao ecossistema Azure.

## Códigos de exemplo

- Python: [Framework de Agentes](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Framework de Agentes](./code_samples/02-dotnet-agent-framework.md)

## Tem mais perguntas sobre frameworks de agentes de IA?

Participe do [Discord do Microsoft Foundry](https://aka.ms/ai-agents/discord) para conhecer outros aprendizes, participar de office hours e obter respostas para suas perguntas sobre Agentes de IA.

## Referências

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel e AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Framework de Agentes do Semantic Kernel (Python)</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Framework de Agentes do Semantic Kernel (.Net)</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Serviço Azure AI Agent</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Usando o Azure AI Agent Service com AutoGen / Semantic Kernel para construir uma solução multiagente</a>

## Lição Anterior

[Introdução a Agentes de IA e Casos de Uso](../01-intro-to-ai-agents/README.md)

## Próxima Lição

[Entendendo Padrões de Design Agentic](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Isenção de responsabilidade:
Este documento foi traduzido usando o serviço de tradução por IA Co-op Translator (https://github.com/Azure/co-op-translator). Embora nos esforcemos pela precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original, em seu idioma nativo, deve ser considerado a fonte autorizada. Para informações críticas, recomenda-se tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações equivocadas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->