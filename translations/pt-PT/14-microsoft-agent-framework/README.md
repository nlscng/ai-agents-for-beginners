# Explorando o Microsoft Agent Framework

![Estrutura de Agentes](../../../translated_images/pt-PT/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introdução

Esta lição irá cobrir:

- Compreender o Microsoft Agent Framework: Funcionalidades-chave e Valor  
- Explorar os Conceitos Principais do Microsoft Agent Framework
- Comparar MAF com Semantic Kernel e AutoGen: Guia de Migração

## Objetivos de Aprendizagem

Após completar esta lição, saberá como:

- Construir Agentes de IA prontos para produção usando o Microsoft Agent Framework
- Aplicar as funcionalidades principais do Microsoft Agent Framework aos seus casos de uso baseados em agentes
- Migrar e integrar frameworks e ferramentas existentes baseados em agentes  

## Exemplos de Código 

Exemplos de código para [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) podem ser encontrados neste repositório em `xx-python-agent-framework` e `xx-dotnet-agent-framework`.

## Compreender o Microsoft Agent Framework

![Introdução ao Framework](../../../translated_images/pt-PT/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) baseia-se na experiência e aprendizagens do Semantic Kernel e do AutoGen. Oferece a flexibilidade para abordar a grande variedade de casos de uso agenticos observados tanto em produção como em ambientes de investigação, incluindo:

- **Orquestração sequencial de agentes** em cenários onde são necessários fluxos de trabalho passo a passo.
- **Orquestração concorrente** em cenários onde os agentes precisam completar tarefas ao mesmo tempo.
- **Orquestração de chat em grupo** em cenários onde agentes podem colaborar entre si numa tarefa.
- **Orquestração de transferência** em cenários onde agentes transferem a tarefa entre si à medida que as subtarefas são concluídas.
- **Orquestração magnética** em cenários onde um agente gestor cria e modifica uma lista de tarefas e gere a coordenação dos subagentes para completar a tarefa.

Para entregar Agentes de IA em Produção, o MAF também inclui características para:

- **Observabilidade** através do uso do OpenTelemetry onde cada ação do Agente de IA, incluindo invocação de ferramentas, passos de orquestração, fluxos de raciocínio e monitorização de desempenho através dos painéis do Microsoft Foundry.
- **Segurança** ao alojar agentes nativamente no Microsoft Foundry, que inclui controlos de segurança como acesso baseado em funções, gestão de dados privados e segurança de conteúdo integrada.
- **Durabilidade** já que os threads e fluxos de agente podem pausar, retomar e recuperar de erros, o que permite processos de maior duração.
- **Control** sendo suportados fluxos de trabalho com intervenção humana onde tarefas são marcadas como requerendo aprovação humana.

O Microsoft Agent Framework também se foca na interoperabilidade através de:

- **Agnóstico quanto à nuvem** - Agentes podem correr em containers, on-prem e através de múltiplas nuvens diferentes.
- **Agnóstico quanto ao fornecedor** - Agentes podem ser criados através do seu SDK preferido incluindo Azure OpenAI e OpenAI
- **Integração de padrões abertos** - Agentes podem utilizar protocolos como Agent-to-Agent(A2A) e Model Context Protocol (MCP) para descobrir e utilizar outros agentes e ferramentas.
- **Plugins e conetores** - Podem ser estabelecidas ligações a serviços de dados e memória tais como Microsoft Fabric, SharePoint, Pinecone e Qdrant.

Vamos ver como estas funcionalidades são aplicadas a alguns dos conceitos principais do Microsoft Agent Framework.

## Conceitos Principais do Microsoft Agent Framework

### Agentes

![Estrutura de Agentes](../../../translated_images/pt-PT/agent-components.410a06daf87b4fef.webp)

**Criação de Agentes**

A criação de agentes é feita definindo o serviço de inferência (LLM Provider), um conjunto de instruções para o Agente de IA seguir, e um `name` atribuído:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Acima está a usar `Azure OpenAI` mas os agentes podem ser criados utilizando uma variedade de serviços incluindo `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

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

**Execução de Agentes**

Os agentes são executados usando os métodos `.run` ou `.run_stream` para respostas não-streaming ou streaming, respetivamente.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Cada execução de agente também pode ter opções para personalizar parâmetros tais como `max_tokens` usados pelo agente, `tools` que o agente pode chamar, e até mesmo o próprio `model` usado pelo agente.

Isto é útil em casos onde modelos ou ferramentas específicas são necessárias para completar a tarefa de um utilizador.

**Ferramentas**

As ferramentas podem ser definidas tanto ao definir o agente:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Ao criar um ChatAgent diretamente

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

como também ao executar o agente:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Ferramenta fornecida apenas para esta execução )
```

**Threads de Agente**

Os Threads de Agente são usados para gerir conversas multi-turno. Threads podem ser criados de duas maneiras:

- Usando `get_new_thread()` que permite que o thread seja salvo ao longo do tempo
- Criando um thread automaticamente ao executar um agente e tendo o thread apenas durante a execução atual.

Para criar um thread, o código é semelhante a isto:

```python
# Criar uma nova thread.
thread = agent.get_new_thread() # Executar o agente com a thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Pode então serializar o thread para ser armazenado para uso posterior:

```python
# Criar um novo thread.
thread = agent.get_new_thread() 

# Executar o agente com o thread.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serializar o thread para armazenamento.

serialized_thread = await thread.serialize() 

# Desserializar o estado do thread após o carregamento a partir do armazenamento.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware de Agente**

Os agentes interagem com ferramentas e LLMs para completar as tarefas dos utilizadores. Em certos cenários, queremos executar ou rastrear interações entre estes. O middleware de agente permite-nos fazer isto através de:

*Middleware de Função*

Este middleware permite-nos executar uma ação entre o agente e uma função/ferramenta que ele vai invocar. Um exemplo de quando isto seria usado é quando se pretende efetuar algum registo (logging) na chamada da função.

No código abaixo `next` define se o próximo middleware ou a função real deverá ser chamada.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Pré-processamento: Registar antes da execução da função
    print(f"[Function] Calling {context.function.name}")

    # Continuar para o próximo middleware ou execução da função
    await next(context)

    # Pós-processamento: Registar depois da execução da função
    print(f"[Function] {context.function.name} completed")
```

*Middleware de Chat*

Este middleware permite-nos executar ou registar uma ação entre o agente e os pedidos entre o LLM .

Isto contém informação importante tal como as `messages` que estão a ser enviadas para o serviço de IA.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Pré-processamento: Registo antes da chamada à IA
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Continuar para o middleware seguinte ou serviço de IA
    await next(context)

    # Pós-processamento: Registo após a resposta da IA
    print("[Chat] AI response received")

```

**Memória do Agente**

Conforme abordado na lição `Agentic Memory`, a memória é um elemento importante para permitir que o agente opere sobre diferentes contextos. O MAF oferece vários tipos diferentes de memórias:

*Armazenamento em memória*

Esta é a memória armazenada em threads durante o tempo de execução da aplicação.

```python
# Criar uma nova thread.
thread = agent.get_new_thread() # Executar o agente com a thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Mensagens persistentes*

Esta memória é utilizada quando se armazena o histórico de conversas através de diferentes sessões. É definida usando o `chat_message_store_factory` :

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

*Memória dinâmica*

Esta memória é adicionada ao contexto antes de os agentes serem executados. Estas memórias podem ser armazenadas em serviços externos tais como mem0:

```python
from agent_framework.mem0 import Mem0Provider

# A utilizar o Mem0 para funcionalidades avançadas de memória
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

A observabilidade é importante para construir sistemas agenticos fiáveis e fáceis de manter. O MAF integra-se com o OpenTelemetry para fornecer tracing e meters para melhor observabilidade.

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

O MAF oferece fluxos de trabalho que são passos pré-definidos para completar uma tarefa e incluem agentes de IA como componentes nesses passos.

Os fluxos de trabalho são compostos por diferentes componentes que permitem um melhor fluxo de controlo. Os fluxos de trabalho também permitem **orquestração multi-agente** e **checkpointing** para guardar estados do fluxo de trabalho.

Os componentes principais de um fluxo de trabalho são:

**Executores**

Os executores recebem mensagens de entrada, executam as suas tarefas atribuídas e depois produzem uma mensagem de saída. Isto move o fluxo de trabalho em direção à conclusão da tarefa maior. Os executores podem ser agentes de IA ou lógica personalizada.

**Arestas**

As arestas são usadas para definir o fluxo de mensagens num fluxo de trabalho. Estas podem ser:

*Arestas Diretas* - Ligações simples um-para-um entre executores:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Arestas Condicionais* - Ativadas quando uma certa condição é satisfeita. Por exemplo, quando quartos de hotel não estão disponíveis, um executor pode sugerir outras opções.

*Arestas switch-case* - Encaminham mensagens para diferentes executores com base em condições definidas. Por exemplo. se um cliente de viagens tiver acesso prioritário, as suas tarefas serão tratadas através de outro fluxo de trabalho.

*Arestas Fan-out* - Enviam uma mensagem para múltiplos destinos.

*Arestas Fan-in* - Reúnem múltiplas mensagens de diferentes executores e enviam para um destino.

**Eventos**

Para proporcionar melhor observabilidade nos fluxos de trabalho, o MAF oferece eventos integrados para a execução, incluindo:

- `WorkflowStartedEvent`  - A execução do fluxo de trabalho começa
- `WorkflowOutputEvent` - O fluxo de trabalho produz uma saída
- `WorkflowErrorEvent` - O fluxo de trabalho encontra um erro
- `ExecutorInvokeEvent`  - O executor inicia o processamento
- `ExecutorCompleteEvent`  -  O executor termina o processamento
- `RequestInfoEvent` - É emitido um pedido

## Migrar de Outros Frameworks (Semantic Kernel e AutoGen)

### Diferenças entre MAF e Semantic Kernel

**Criação de Agentes Simplificada**

O Semantic Kernel depende da criação de uma instância de Kernel para cada agente. O MAF tem uma abordagem simplificada ao usar extensões para os principais fornecedores.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Criação de Threads de Agente**

O Semantic Kernel exige que threads sejam criados manualmente. No MAF, o agente é diretamente atribuído a um thread.

```python
thread = agent.get_new_thread() # Execute o agente na thread.
```

**Registo de Ferramentas**

No Semantic Kernel, as ferramentas são registadas no Kernel e o Kernel é depois passado ao agente. No MAF, as ferramentas são registadas diretamente durante o processo de criação do agente.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Diferenças entre MAF e  AutoGen

**Teams vs Fluxos de Trabalho**

`Teams` são a estrutura de eventos para atividade orientada por eventos com agentes no AutoGen. O MAF usa `Workflows` que encaminham dados para executores através de uma arquitetura baseada em grafo.

**Criação de Ferramentas**

O AutoGen usa `FunctionTool` para envolver funções que os agentes podem chamar. O MAF usa @ai_function que opera de forma semelhante, mas também infere os esquemas automaticamente para cada função.

**Comportamento do Agente**

Os agentes são agentes de turno único por defeito no AutoGen, a menos que `max_tool_iterations` seja definido para um valor superior. No MAF, o `ChatAgent` é multi-turno por defeito, o que significa que continuará a chamar ferramentas até a tarefa do utilizador estar completa.

## Exemplos de Código 

Exemplos de código para Microsoft Agent Framework podem ser encontrados neste repositório em `xx-python-agent-framework` e `xx-dotnet-agent-framework`.

## Tem Mais Perguntas Sobre o Microsoft Agent Framework?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para conhecer outros aprendizes, assistir a horas de atendimento e obter respostas às suas perguntas sobre Agentes de IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso legal**:
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos por garantir a precisão, por favor tenha em atenção que traduções automáticas podem conter erros ou imprecisões. O documento original no seu idioma nativo deve ser considerado a fonte autoritativa. Para informações críticas, recomenda-se uma tradução profissional realizada por um tradutor humano. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes da utilização desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->