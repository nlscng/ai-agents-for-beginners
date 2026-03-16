# Explorando o Microsoft Agent Framework

![Agent Framework](../../../translated_images/pt-BR/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introdução

Esta lição abordará:

- Compreendendo o Microsoft Agent Framework: Recursos principais e valor  
- Explorando os conceitos-chave do Microsoft Agent Framework
- Comparando MAF com Semantic Kernel e AutoGen: Guia de migração

## Objetivos de Aprendizagem

Após concluir esta lição, você saberá como:

- Construir Agentes de IA Prontos para Produção usando o Microsoft Agent Framework
- Aplicar os recursos principais do Microsoft Agent Framework aos seus casos de uso agentic
- Migrar e integrar frameworks e ferramentas agentic existentes  

## Exemplos de Código 

Exemplos de código para [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) podem ser encontrados neste repositório nos arquivos `xx-python-agent-framework` e `xx-dotnet-agent-framework`.

## Compreendendo o Microsoft Agent Framework

![Framework Intro](../../../translated_images/pt-BR/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) se baseia na experiência e aprendizados do Semantic Kernel e AutoGen. Ele oferece a flexibilidade para atender à grande variedade de casos de uso agentic vistos em ambientes de produção e pesquisa, incluindo:

- **Orquestração sequencial de agentes** em cenários onde fluxos de trabalho passo a passo são necessários.
- **Orquestração concorrente** em cenários onde agentes precisam completar tarefas ao mesmo tempo.
- **Orquestração de chat em grupo** em cenários onde agentes podem colaborar juntos em uma tarefa.
- **Orquestração de transferência (handoff)** em cenários onde agentes passam a tarefa uns para os outros conforme as subtarefas são concluídas.
- **Orquestração magnética** em cenários onde um agente gerente cria e modifica uma lista de tarefas e gerencia a coordenação dos subagentes para completar a tarefa.

Para entregar Agentes de IA em Produção, o MAF também inclui recursos para:

- **Observabilidade** por meio do uso do OpenTelemetry, onde cada ação do Agente de IA, incluindo invocação de ferramenta, etapas de orquestração, fluxos de raciocínio e monitoramento de desempenho através dos dashboards do Microsoft Foundry.
- **Segurança** hospedando agentes nativamente no Microsoft Foundry, que inclui controles de segurança como acesso baseado em função, manipulação de dados privados e segurança de conteúdo embutida.
- **Durabilidade** pois threads e fluxos de trabalho de agentes podem pausar, retomar e recuperar de erros, permitindo processos de longa duração.
- **Controle** pois fluxos de trabalho com intervenção humana são suportados, onde tarefas são marcadas como requerendo aprovação humana.

O Microsoft Agent Framework também se foca em ser interoperável por meio de:

- **Ser agnóstico à nuvem** - Agentes podem rodar em containers, on-premises e em múltiplas nuvens diferentes.
- **Ser agnóstico ao provedor** - Agentes podem ser criados através do SDK preferido, incluindo Azure OpenAI e OpenAI.
- **Integração com padrões abertos** - Agentes podem utilizar protocolos como Agent-to-Agent (A2A) e Model Context Protocol (MCP) para descobrir e usar outros agentes e ferramentas.
- **Plugins e Conectores** - Conexões podem ser feitas com serviços de dados e memória como Microsoft Fabric, SharePoint, Pinecone e Qdrant.

Vamos ver como esses recursos são aplicados a alguns dos conceitos principais do Microsoft Agent Framework.

## Conceitos-Chave do Microsoft Agent Framework

### Agentes

![Agent Framework](../../../translated_images/pt-BR/agent-components.410a06daf87b4fef.webp)

**Criando Agentes**

A criação do agente é feita definindo o serviço de inferência (Provedor LLM), um conjunto de instruções para o Agente de IA seguir, e um `nome` atribuído:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

O acima está usando `Azure OpenAI`, mas agentes podem ser criados usando uma variedade de serviços, incluindo o `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

APIs OpenAI `Responses`, `ChatCompletion`

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

ou agentes remotos usando o protocolo A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Executando Agentes**

Agentes são executados usando os métodos `.run` ou `.run_stream` para respostas não transmissas ou por streaming.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Cada execução do agente também pode ter opções para personalizar parâmetros como `max_tokens` usado pelo agente, `tools` que o agente pode chamar, e até mesmo o próprio `model` usado para o agente.

Isso é útil em casos onde modelos ou ferramentas específicos são necessários para completar a tarefa do usuário.

**Ferramentas**

Ferramentas podem ser definidas tanto ao definir o agente:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Ao criar um ChatAgent diretamente

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

quanto ao executar o agente:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Ferramenta fornecida apenas para esta execução )
```

**Threads de Agente**

Threads de agente são usadas para lidar com conversas de múltiplas interações. Threads podem ser criadas por:

- Usar `get_new_thread()` que permite salvar a thread ao longo do tempo
- Criar uma thread automaticamente ao executar um agente, onde a thread dura apenas durante a execução atual.

Para criar uma thread, o código é assim:

```python
# Crie uma nova thread.
thread = agent.get_new_thread() # Execute o agente com a thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Você pode então serializar a thread para ser armazenada para uso posterior:

```python
# Crie uma nova thread.
thread = agent.get_new_thread() 

# Execute o agente com a thread.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serialize a thread para armazenamento.

serialized_thread = await thread.serialize() 

# Desserialize o estado da thread após carregar do armazenamento.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware do Agente**

Agentes interagem com ferramentas e LLMs para completar as tarefas dos usuários. Em certos cenários, queremos executar ou rastrear algo entre essas interações. Middleware do agente permite isso por meio de:

*Middleware de Função*

Esse middleware nos permite executar uma ação entre o agente e uma função/ferramenta que ele chamará. Um exemplo de uso é quando você quer fazer um registro (logging) na chamada da função.

No código abaixo, `next` define se o próximo middleware ou a função real deve ser chamada.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Pré-processamento: Registrar antes da execução da função
    print(f"[Function] Calling {context.function.name}")

    # Continuar para o próximo middleware ou execução da função
    await next(context)

    # Pós-processamento: Registrar após a execução da função
    print(f"[Function] {context.function.name} completed")
```

*Middleware de Chat*

Esse middleware permite executar ou registrar uma ação entre o agente e as requisições entre o LLM.

Isso contém informações importantes como as `messages` que estão sendo enviadas para o serviço de IA.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Pré-processamento: Registrar antes da chamada da IA
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Continuar para o próximo middleware ou serviço de IA
    await next(context)

    # Pós-processamento: Registrar após a resposta da IA
    print("[Chat] AI response received")

```

**Memória do Agente**

Como abordado na lição `Agentic Memory`, memória é um elemento importante para permitir que o agente opere sobre diferentes contextos. O MAF oferece vários tipos diferentes de memórias:

*Armazenamento em Memória*

Essa é a memória armazenada em threads durante o tempo de execução da aplicação.

```python
# Crie uma nova thread.
thread = agent.get_new_thread() # Execute o agente com a thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Mensagens Persistentes*

Essa memória é usada para armazenar histórico de conversas entre sessões diferentes. É definida usando o `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Criar um armazenamento de mensagens personalizado
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Memória Dinâmica*

Essa memória é adicionada ao contexto antes dos agentes serem executados. Essas memórias podem ser armazenadas em serviços externos como o mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Usando Mem0 para capacidades avançadas de memória
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**Observabilidade do Agente**

Observabilidade é importante para construir sistemas agentic confiáveis e fáceis de manter. MAF integra-se com OpenTelemetry para fornecer rastreamento e métricas para melhor observabilidade.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # fazer algo
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Fluxos de Trabalho

MAF oferece fluxos de trabalho que são passos pré-definidos para completar uma tarefa e incluem agentes de IA como componentes nesses passos.

Fluxos de trabalho são feitos de diferentes componentes que permitem melhor controle de fluxo. Fluxos de trabalho também permitem **orquestração multi-agente** e **checkpointing** para salvar estados do fluxo.

Os componentes principais de um fluxo de trabalho são:

**Executores**

Executores recebem mensagens de entrada, realizam suas tarefas atribuídas e então produzem uma mensagem de saída. Isso move o fluxo de trabalho adiante rumo à conclusão da tarefa maior. Executores podem ser agentes de IA ou lógica personalizada.

**Arestas**

Arestas são usadas para definir o fluxo de mensagens em um fluxo de trabalho. Essas podem ser:

*Arestas Diretas* - Conexões simples um-para-um entre executores:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Arestas Condicionais* - Ativadas após certa condição ser atingida. Por exemplo, quando quartos de hotel estão indisponíveis, um executor pode sugerir outras opções.

*Arestas switch-case* - Roteiam mensagens para diferentes executores baseados em condições definidas. Por exemplo, se um cliente de viagem tem acesso prioritário, suas tarefas serão tratadas por outro fluxo de trabalho.

*Arestas fan-out* - Enviam uma mensagem para múltiplos destinos.

*Arestas fan-in* - Coletam múltiplas mensagens de diferentes executores e enviam para um destino.

**Eventos**

Para fornecer melhor observabilidade nos fluxos de trabalho, o MAF oferece eventos embutidos para execução, incluindo:

- `WorkflowStartedEvent`  - Início da execução do fluxo de trabalho
- `WorkflowOutputEvent` - Fluxo de trabalho produz uma saída
- `WorkflowErrorEvent` - Fluxo de trabalho encontra um erro
- `ExecutorInvokeEvent`  - Executor começa o processamento
- `ExecutorCompleteEvent`  - Executor termina o processamento
- `RequestInfoEvent` - Uma requisição é emitida

## Migração de Outros Frameworks (Semantic Kernel e AutoGen)

### Diferenças entre MAF e Semantic Kernel

**Criação Simplificada de Agentes**

Semantic Kernel depende da criação de uma instância do Kernel para cada agente. MAF usa uma abordagem simplificada utilizando extensões para os principais provedores.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Criação de Thread do Agente**

Semantic Kernel requer que threads sejam criadas manualmente. No MAF, a thread é atribuída diretamente ao agente.

```python
thread = agent.get_new_thread() # Execute o agente com a thread.
```

**Registro de Ferramentas**

No Semantic Kernel, as ferramentas são registradas no Kernel e o Kernel é então passado para o agente. No MAF, as ferramentas são registradas diretamente durante o processo de criação do agente.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Diferenças entre MAF e AutoGen

**Teams vs Workflows**

`Teams` são a estrutura de eventos para atividade orientada a eventos com agentes no AutoGen. O MAF usa `Workflows` que roteiam dados para executores através de uma arquitetura baseada em grafo.

**Criação de Ferramentas**

AutoGen usa `FunctionTool` para encapsular funções para agentes chamarem. MAF usa @ai_function que opera de modo similar, mas também infere os esquemas automaticamente para cada função.

**Comportamento do Agente**

Agentes são agentes de turno único por padrão no AutoGen, a menos que `max_tool_iterations` seja definido para um valor maior. No MAF, o `ChatAgent` é multi-turno por padrão, o que significa que continuará chamando ferramentas até a tarefa do usuário ser concluída.

## Exemplos de Código 

Exemplos de código para Microsoft Agent Framework podem ser encontrados neste repositório nos arquivos `xx-python-agent-framework` e `xx-dotnet-agent-framework`.

## Tem Mais Perguntas Sobre o Microsoft Agent Framework?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar de horários de atendimento e tirar suas dúvidas sobre Agentes de IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução automática [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, por favor, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autoritativa. Para informações críticas, recomenda-se a tradução profissional realizada por humanos. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->