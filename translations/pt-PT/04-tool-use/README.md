[![Como Projetar Bons Agentes de IA](../../../translated_images/pt-PT/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Clique na imagem acima para ver o vídeo desta aula)_

# Padrão de Utilização de Ferramentas

As ferramentas são interessantes porque permitem que agentes de IA tenham um conjunto mais vasto de capacidades. Em vez do agente ter um conjunto limitado de ações que pode executar, ao adicionar uma ferramenta, o agente pode agora executar uma ampla gama de ações. Neste capítulo, vamos analisar o Padrão de Utilização de Ferramentas, que descreve como agentes de IA podem usar ferramentas específicas para atingir os seus objetivos.

## Introdução

Nesta aula, procuramos responder às seguintes questões:

- O que é o padrão de utilização de ferramentas?
- Em que casos de uso pode ser aplicado?
- Quais são os elementos/blocos de construção necessários para implementar o padrão de utilização?
- Quais são as considerações especiais para usar o Padrão de Utilização de Ferramentas para construir agentes de IA fiáveis?

## Objetivos de Aprendizagem

Após completar esta aula, será capaz de:

- Definir o Padrão de Utilização de Ferramentas e o seu propósito.
- Identificar casos de uso onde o Padrão de Utilização de Ferramentas é aplicável.
- Compreender os elementos-chave necessários para implementar o padrão de design.
- Reconhecer considerações para garantir fiabilidade em agentes de IA que utilizam este padrão.

## O que é o Padrão de Utilização de Ferramentas?

O **Padrão de Utilização de Ferramentas** foca-se em dar aos LLMs a capacidade de interagir com ferramentas externas para alcançar objetivos específicos. As ferramentas são código que pode ser executado por um agente para realizar ações. Uma ferramenta pode ser uma função simples, como uma calculadora, ou uma chamada de API para um serviço externo, como consulta de preços de ações ou previsão meteorológica. No contexto dos agentes de IA, as ferramentas são concebidas para serem executadas por agentes em resposta a **chamadas de função geradas pelo modelo**.

## Em que casos de uso pode ser aplicado?

Os Agentes de IA podem recorrer a ferramentas para completar tarefas complexas, recuperar informação ou tomar decisões. O padrão de utilização de ferramentas é frequentemente utilizado em cenários que requerem interação dinâmica com sistemas externos, tais como bases de dados, serviços web ou interpretadores de código. Esta capacidade é útil para vários casos de uso, incluindo:

- **Recuperação Dinâmica de Informação:** Os agentes podem consultar APIs externas ou bases de dados para obter dados atualizados (por exemplo, consultar uma base de dados SQLite para análise de dados, obter preços de ações ou informação meteorológica).
- **Execução e Interpretação de Código:** Os agentes podem executar código ou scripts para resolver problemas matemáticos, gerar relatórios ou realizar simulações.
- **Automatização de Fluxos de Trabalho:** Automatizar fluxos de trabalho repetitivos ou em vários passos integrando ferramentas como agendadores de tarefas, serviços de e-mail ou pipelines de dados.
- **Apoio ao Cliente:** Os agentes podem interagir com sistemas CRM, plataformas de ticketing ou bases de conhecimento para resolver questões de utilizadores.
- **Geração e Edição de Conteúdo:** Os agentes podem recorrer a ferramentas como corretores gramaticais, resumidores de texto ou avaliadores de segurança de conteúdo para auxiliar em tarefas de criação de conteúdo.

## Quais são os elementos/blocos de construção necessários para implementar o padrão de utilização de ferramentas?

Estes blocos de construção permitem ao agente de IA realizar uma vasta gama de tarefas. Vamos ver os elementos-chave necessários para implementar o Padrão de Utilização de Ferramentas:

- **Esquemas de Função/Ferramenta**: Definições detalhadas das ferramentas disponíveis, incluindo nome da função, propósito, parâmetros necessários e outputs esperados. Estes esquemas permitem ao LLM entender que ferramentas estão disponíveis e como construir pedidos válidos.

- **Lógica de Execução de Funções**: Regula como e quando as ferramentas são invocadas com base na intenção do utilizador e no contexto da conversa. Isto pode incluir módulos de planeamento, mecanismos de encaminhamento ou fluxos condicionais que determinam o uso de ferramentas de forma dinâmica.

- **Sistema de Gestão de Mensagens**: Componentes que gerem o fluxo conversacional entre entradas do utilizador, respostas do LLM, chamadas de ferramenta e saídas das ferramentas.

- **Estrutura de Integração de Ferramentas**: Infraestrutura que liga o agente a várias ferramentas, quer sejam funções simples ou serviços externos complexos.

- **Tratamento de Erros e Validação**: Mecanismos para lidar com falhas na execução das ferramentas, validar parâmetros e gerir respostas inesperadas.

- **Gestão de Estado**: Acompanha o contexto da conversa, interações anteriores com ferramentas e dados persistentes para garantir consistência em interações multi-turno.

Next, let's look at Function/Tool Calling in more detail.
 
### Chamada de Função/Ferramenta

A chamada de função é a principal forma de permitir que Large Language Models (LLMs) interajam com ferramentas. Verá frequentemente 'Function' e 'Tool' usados de forma intercambiável porque 'functions' (blocos de código reutilizável) são as 'ferramentas' que os agentes utilizam para executar tarefas. Para que o código de uma função seja invocado, um LLM deve comparar o pedido do utilizador com a descrição das funções. Para o fazer, um esquema contendo as descrições de todas as funções disponíveis é enviado ao LLM. O LLM seleciona então a função mais apropriada para a tarefa e retorna o seu nome e argumentos. A função selecionada é invocada, a sua resposta é enviada de volta ao LLM, que usa a informação para responder ao pedido do utilizador.

Para os desenvolvedores implementarem chamadas de função para agentes, irá precisar de:

1. Um modelo LLM que suporte chamadas de função
2. Um esquema contendo descrições de funções
3. O código para cada função descrita

Vamos usar o exemplo de obter a hora atual numa cidade para ilustrar:

1. **Inicializar um LLM que suporte chamadas de função:**

    Nem todos os modelos suportam chamadas de função, por isso é importante verificar que o LLM que está a usar o faz.     <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> suporta chamadas de função. Podemos começar por iniciar o cliente Azure OpenAI. 

    ```python
    # Inicializar o cliente do Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Criar um Esquema de Função**:

    De seguida vamos definir um esquema JSON que contém o nome da função, descrição do que a função faz, e os nomes e descrições dos parâmetros da função.
    Vamos então pegar neste esquema e passá-lo ao cliente criado anteriormente, juntamente com o pedido do utilizador para encontrar a hora em São Francisco. O que é importante notar é que uma **chamada de ferramenta** é o que é retornado, **não** a resposta final à pergunta. Como mencionado anteriormente, o LLM retorna o nome da função que selecionou para a tarefa, e os argumentos que lhe serão passados.

    ```python
    # Descrição da função para o modelo ler
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
  
    # Mensagem inicial do utilizador
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Primeira chamada à API: Pedir ao modelo para usar a função
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Processar a resposta do modelo
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **O código da função necessário para executar a tarefa:**

    Agora que o LLM escolheu qual a função que precisa de ser executada, o código que realiza a tarefa precisa de ser implementado e executado.
    Podemos implementar o código para obter a hora atual em Python. Também será necessário escrever o código para extrair o nome e os argumentos da response_message para obter o resultado final.

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
     # Tratar chamadas de função
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
  
      # Segunda chamada à API: obter a resposta final do modelo
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

A Chamada de Função está no centro da maior parte, se não de todo, o design de utilização de ferramentas para agentes, no entanto implementá-la do zero pode por vezes ser desafiante.
Como aprendemos em [Lição 2](../../../02-explore-agentic-frameworks), os agentic frameworks fornecem-nos blocos de construção pré-construídos para implementar a utilização de ferramentas.
 
## Exemplos de Utilização de Ferramentas com Frameworks Agentic

Aqui estão alguns exemplos de como pode implementar o Padrão de Utilização de Ferramentas usando diferentes agentic frameworks:

### Semantic Kernel

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> é um framework de IA open-source para desenvolvedores .NET, Python e Java a trabalhar com Large Language Models (LLMs). Simplifica o processo de utilização de chamadas de função ao descrever automaticamente as suas funções e os seus parâmetros ao modelo através de um processo chamado <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">serialização</a>. Também gere a comunicação de ida e volta entre o modelo e o seu código. Outra vantagem de usar um agentic framework como o Semantic Kernel é que lhe permite aceder a ferramentas pré-construídas como <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">Pesquisa de Ficheiros</a> e <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Interpretador de Código</a>.

The following diagram illustrates the process of function calling with Semantic Kernel:

![chamada de função](../../../translated_images/pt-PT/functioncalling-diagram.a84006fc287f6014.webp)

In Semantic Kernel functions/tools are called <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. We can convert the `get_current_time` function we saw earlier into a plugin by turning it into a class with the function in it. We can also import the `kernel_function` decorator, which takes in the description of the function. When you then create a kernel with the GetCurrentTimePlugin, the kernel will automatically serialize the function and its parameters, creating the schema to send to the LLM in the process.

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

# Criar o núcleo
kernel = Kernel()

# Criar o plugin
get_current_time_plugin = GetCurrentTimePlugin(location)

# Adicionar o plugin ao núcleo
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> é um framework agentic mais recente que foi concebido para capacitar desenvolvedores a construir, implantar e escalar agentes de IA extensíveis e de alta qualidade de forma segura, sem necessidade de gerir os recursos subjacentes de computação e armazenamento. É particularmente útil para aplicações empresariais, uma vez que é um serviço totalmente gerido com segurança a nível empresarial.

When compared to developing with the LLM API directly, Azure AI Agent Service provides some advantages, including:

- Automatic tool calling – no need to parse a tool call, invoke the tool, and handle the response; all of this is now done server-side
- Securely managed data – instead of managing your own conversation state, you can rely on threads to store all the information you need
- Out-of-the-box tools – Tools that you can use to interact with your data sources, such as Bing, Azure AI Search, and Azure Functions.

As ferramentas disponíveis no Azure AI Agent Service podem ser divididas em duas categorias:

1. Knowledge Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Grounding with Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">File Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Action Tools:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Function Calling</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Code Interpreter</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI defined tools</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

The Agent Service allows us to be able to use these tools together as a `toolset`. It also utilizes `threads` which keep track of the history of messages from a particular conversation.

Imagine you are a sales agent at a company called Contoso. You want to develop a conversational agent that can answer questions about your sales data.

The following image illustrates how you could use Azure AI Agent Service to analyze your sales data:

![Serviço Agentic em Ação](../../../translated_images/pt-PT/agent-service-in-action.34fb465c9a84659e.webp)

To use any of these tools with the service we can create a client and define a tool or toolset. To implement this practically we can use the following Python code. The LLM will be able to look at the toolset and decide whether to use the user created function, `fetch_sales_data_using_sqlite_query`, or the pre-built Code Interpreter depending on the user request.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # função fetch_sales_data_using_sqlite_query que pode ser encontrada no ficheiro fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Inicializar conjunto de ferramentas
toolset = ToolSet()

# Inicializar um agente que chama funções com a função fetch_sales_data_using_sqlite_query e adicioná-lo ao conjunto de ferramentas
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Inicializar a ferramenta Code Interpreter e adicioná-la ao conjunto de ferramentas.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Quais são as considerações especiais para usar o Padrão de Utilização de Ferramentas para construir agentes de IA fiáveis?

Uma preocupação comum com SQL gerado dinamicamente por LLMs é a segurança, particularmente o risco de SQL injection ou ações maliciosas, como eliminar ou adulterar a base de dados. Embora essas preocupações sejam válidas, podem ser eficazmente mitigadas configurando corretamente as permissões de acesso à base de dados. Para a maioria das bases de dados, isto envolve configurar a base de dados como apenas leitura. Para serviços de base de dados como PostgreSQL ou Azure SQL, a aplicação deve receber uma função de apenas leitura (SELECT).

Executar a aplicação num ambiente seguro aumenta ainda mais a proteção. Em cenários empresariais, os dados são tipicamente extraídos e transformados a partir de sistemas operacionais para uma base de dados apenas leitura ou um data warehouse com um esquema amigável ao utilizador. Esta abordagem garante que os dados são seguros, otimizados para desempenho e acessibilidade, e que a aplicação tem acesso restrito e apenas leitura.

## Exemplos de Código
- Python: [Estrutura de Agentes](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Estrutura de Agentes](./code_samples/04-dotnet-agent-framework.md)

## Tem mais perguntas sobre os padrões de design de utilização de ferramentas?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para conhecer outros aprendentes, participar em horas de atendimento e obter respostas às suas questões sobre Agentes de IA.

## Recursos Adicionais

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Workshop do Azure AI Agents Service</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Workshop Multi-Agente Contoso Creative Writer</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Tutorial de Chamada de Funções do Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Interpretador de Código do Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Ferramentas Autogen</a>

## Lição Anterior

[Compreender os Padrões de Design Agêntico](../03-agentic-design-patterns/README.md)

## Próxima Lição

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Isenção de responsabilidade**:
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos por garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original, na sua língua de origem, deve ser considerado a fonte autoritativa. Para informações críticas, recomenda-se uma tradução profissional efetuada por um tradutor humano. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes da utilização desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->