[![Padrão de Design de Planeamento](../../../translated_images/pt-PT/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Clique na imagem acima para ver o vídeo desta aula)_

# Design de Planeamento

## Introdução

Esta aula irá cobrir

* Definir um objetivo global claro e decompor uma tarefa complexa em tarefas geríveis.
* Aproveitar saídas estruturadas para respostas mais fiáveis e legíveis por máquina.
* Aplicar uma abordagem orientada a eventos para lidar com tarefas dinâmicas e entradas inesperadas.

## Objetivos de Aprendizagem

Após concluir esta aula, terá uma compreensão sobre:

* Identificar e definir um objetivo global para um agente de IA, garantindo que saiba claramente o que precisa ser alcançado.
* Decompor uma tarefa complexa em subtarefas geríveis e organizá-las numa sequência lógica.
* Equipar agentes com as ferramentas adequadas (por exemplo, ferramentas de pesquisa ou de análise de dados), decidir quando e como são usadas e lidar com situações inesperadas que surgem.
* Avaliar os resultados das subtarefas, medir o desempenho e iterar nas ações para melhorar o resultado final.

## Definindo o Objetivo Global e Dividindo uma Tarefa

![Definindo Objetivos e Tarefas](../../../translated_images/pt-PT/defining-goals-tasks.d70439e19e37c47a.webp)

A maioria das tarefas do mundo real é demasiado complexa para ser resolvida numa só etapa. Um agente de IA precisa de um objetivo conciso para orientar o seu planeamento e ações. Por exemplo, considere o objetivo:

    "Generate a 3-day travel itinerary."

Embora seja simples de enunciar, ainda necessita de refinamento. Quanto mais claro for o objetivo, melhor o agente (e quaisquer colaboradores humanos) poderão concentrar-se em alcançar o resultado certo, como criar um itinerário completo com opções de voos, recomendações de hotéis e sugestões de atividades.

### Decomposição de Tarefas

Tarefas grandes ou intrincadas tornam-se mais geríveis quando divididas em subtarefas mais pequenas, orientadas por objetivos.
Para o exemplo do itinerário de viagem, pode decompor o objetivo em:

* Reserva de Voos
* Reserva de Hotel
* Aluguer de Carro
* Personalização

Cada subtarefa pode então ser tratada por agentes ou processos dedicados. Um agente pode especializar-se em procurar as melhores ofertas de voos, outro concentra-se em reservas de hotéis, e assim por diante. Um agente coordenador ou “downstream” pode depois compilar estes resultados num único itinerário coeso para o utilizador final.

Esta abordagem modular também permite melhorias incrementais. Por exemplo, pode adicionar agentes especializados para Recomendações de Restaurantes ou Sugestões de Atividades Locais e refinar o itinerário ao longo do tempo.

### Saída Estruturada

Large Language Models (LLMs) podem gerar saídas estruturadas (por exemplo, JSON) que são mais fáceis de analisar e processar por agentes ou serviços a jusante. Isto é especialmente útil num contexto multi-agente, onde podemos executar estas tarefas após a recepção da saída de planeamento. Consulte este <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">artigo</a> para uma visão geral rápida.

O seguinte trecho de Python demonstra um agente de planeamento simples a decompor um objetivo em subtarefas e a gerar um plano estruturado:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Modelo de Subtarefa de Viagem
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # queremos atribuir a tarefa ao agente

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Para autenticar com o modelo, terá de gerar um token de acesso pessoal (PAT) nas definições da sua conta GitHub.
    # Crie o seu token PAT seguindo as instruções aqui: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Defina a mensagem do utilizador
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Assegure que o conteúdo da resposta é uma string JSON válida antes de a carregar
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("O conteúdo da resposta não é uma string JSON válida")

# # Imprimir o conteúdo da resposta depois de o carregar como JSON
# pprint(json.loads(response_content))

# Validar o conteúdo da resposta com o modelo MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Agente de Planeamento com Orquestração Multi-Agente

Neste exemplo, um Semantic Router Agent recebe um pedido do utilizador (por exemplo, "I need a hotel plan for my trip.").

O planeador então:

* Recebe o Plano de Hotel: O planeador toma a mensagem do utilizador e, com base num prompt de sistema (incluindo detalhes dos agentes disponíveis), gera um plano de viagem estruturado.
* Lista de Agentes e as suas Ferramentas: o registo de agentes contém uma lista de agentes (por exemplo, para voos, hotéis, aluguer de carros e atividades) juntamente com as funções ou ferramentas que oferecem.
* Encaminha o Plano para os Agentes Correspondentes: Dependendo do número de subtarefas, o planeador ou envia a mensagem diretamente para um agente dedicado (para cenários de tarefa única) ou coordena via um gestor de chat de grupo para colaboração multi-agente.
* Resume o Resultado: Finalmente, o planeador resume o plano gerado para maior clareza.
O seguinte exemplo de código Python ilustra estas etapas:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Modelo de Subtarefa de Viagem

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # queremos atribuir a tarefa ao agente

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Criar o cliente com variáveis de ambiente verificadas por tipo

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definir a mensagem do utilizador

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Garantir que o conteúdo da resposta é uma string JSON válida antes de a carregar

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Imprimir o conteúdo da resposta depois de o carregar como JSON

pprint(json.loads(response_content))
```

What follows is the output from the previous code and you can then use this structured output to route to `assigned_agent` and summarize the travel plan to the end user.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

An example notebook with the previous code sample is available [aqui](07-autogen.ipynb).

### Planeamento Iterativo

Algumas tarefas requerem ir e voltar ou replaneamento, onde o resultado de uma subtarefa influencia a seguinte. Por exemplo, se o agente descobrir um formato de dados inesperado enquanto reserva voos, pode precisar de adaptar a sua estratégia antes de prosseguir para as reservas de hotel.

Adicionalmente, o feedback do utilizador (por exemplo, um humano a decidir que prefere um voo mais cedo) pode desencadear um replaneamento parcial. Esta abordagem dinâmica e iterativa garante que a solução final se alinha com as restrições do mundo real e com as preferências do utilizador em evolução.

exemplo de código

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. igual ao código anterior e passar o histórico do utilizador e o plano atual
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. replanear e enviar as tarefas aos respetivos agentes
```

Para um planeamento mais abrangente consulte o Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">artigo do blog</a> para resolver tarefas complexas.

## Resumo

Neste artigo vimos um exemplo de como podemos criar um planeador que pode selecionar dinamicamente os agentes disponíveis definidos. A saída do Planeador decompõe as tarefas e atribui os agentes para que possam ser executadas. Parte-se do princípio que os agentes têm acesso às funções/ferramentas necessárias para realizar a tarefa. Para além dos agentes, pode incluir outros padrões como reflexão, sumarizador e chat round-robin para personalizar ainda mais.

## Recursos Adicionais

AutoGen Magentic One - A Generalist multi-agent system for solving complex tasks and has achieved impressive results on multiple challenging agentic benchmarks. Reference: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. In this implementation the orchestrator create task specific plan and delegates these tasks to the available agents. In addition to planning the orchestrator also employs a tracking mechanism to monitor the progress of the task and re-plans as required.

### Tem mais perguntas sobre o Padrão de Design de Planeamento?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para conhecer outros participantes, assistir a horas de atendimento e obter respostas às suas perguntas sobre Agentes de IA.

## Lição Anterior

[Construir Agentes de IA Confiáveis](../06-building-trustworthy-agents/README.md)

## Próxima Lição

[Padrão de Design Multi-Agente](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Isenção de responsabilidade**:
Este documento foi traduzido utilizando o serviço de tradução automática por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos por garantir a precisão, esteja ciente de que traduções automatizadas podem conter erros ou imprecisões. O documento original, no seu idioma nativo, deve ser considerado a fonte autoritativa. Para informação crítica, recomenda-se a tradução profissional por um tradutor humano. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações erradas decorrentes da utilização desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->