[![Padrão de Design de Planejamento](../../../translated_images/pt-BR/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Clique na imagem acima para assistir ao vídeo desta lição)_

# Design de Planejamento

## Introdução

Esta lição abordará

* Definir uma meta geral clara e dividir uma tarefa complexa em tarefas gerenciáveis.
* Aproveitar a saída estruturada para respostas mais confiáveis e legíveis por máquina.
* Aplicar uma abordagem orientada a eventos para lidar com tarefas dinâmicas e entradas inesperadas.

## Objetivos de Aprendizagem

Após concluir esta lição, você terá uma compreensão sobre:

* Identificar e definir uma meta geral para um agente de IA, garantindo que ele saiba claramente o que precisa ser alcançado.
* Decompor uma tarefa complexa em subtarefas gerenciáveis e organizá-las em uma sequência lógica.
* Equipar agentes com as ferramentas certas (por exemplo, ferramentas de busca ou ferramentas de análise de dados), decidir quando e como são usadas, e lidar com situações inesperadas que surgem.
* Avaliar os resultados das subtarefas, medir o desempenho e iterar nas ações para melhorar o resultado final.

## Definindo a Meta Geral e Dividindo uma Tarefa

![Definindo Metas e Tarefas](../../../translated_images/pt-BR/defining-goals-tasks.d70439e19e37c47a.webp)

A maioria das tarefas do mundo real é complexa demais para ser realizada em uma única etapa. Um agente de IA precisa de um objetivo conciso para guiar seu planejamento e ações. Por exemplo, considere a meta:

    "Gerar um roteiro de viagem de 3 dias."

Embora seja simples de declarar, ainda precisa de refinamento. Quanto mais clara a meta, melhor o agente (e quaisquer colaboradores humanos) podem se concentrar em alcançar o resultado correto, como criar um roteiro abrangente com opções de voos, recomendações de hotéis e sugestões de atividades.

### Decomposição da Tarefa

Tarefas grandes ou complexas tornam-se mais gerenciáveis quando divididas em subtarefas menores e orientadas por objetivos.  
Para o exemplo do roteiro de viagem, você pode decompor a meta em:

* Reserva de voo
* Reserva de hotel
* Aluguel de carro
* Personalização

Cada subtarefa pode então ser tratada por agentes ou processos dedicados. Um agente pode se especializar em buscar as melhores ofertas de voo, outro foca nas reservas de hotel, e assim por diante. Um agente coordenador ou “downstream” pode então compilar esses resultados em um roteiro coeso para o usuário final.

Essa abordagem modular também permite melhorias incrementais. Por exemplo, você pode adicionar agentes especializados para Recomendações de Comida ou Sugestões de Atividades Locais e refinar o roteiro com o tempo.

### Saída Estruturada

Modelos de Linguagem Grandes (LLMs) podem gerar saída estruturada (por exemplo, JSON) que é mais fácil para agentes ou serviços downstream analisarem e processarem. Isso é especialmente útil em um contexto multiagente, onde podemos executar essas tarefas após receber a saída do planejamento. Consulte este <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">post no blog</a> para uma visão rápida.

O snippet de Python a seguir demonstra um agente de planejamento simples decompondo uma meta em subtarefas e gerando um plano estruturado:

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
    # Para autenticar com o modelo, você precisará gerar um token de acesso pessoal (PAT) nas configurações do seu GitHub.
    # Crie seu token PAT seguindo as instruções aqui: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Defina a mensagem do usuário
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

# # Certifique-se de que o conteúdo da resposta seja uma string JSON válida antes de carregá-la
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("O conteúdo da resposta não é uma string JSON válida")

# # Imprima o conteúdo da resposta após carregá-lo como JSON
# pprint(json.loads(response_content))

# Valide o conteúdo da resposta com o modelo MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Agente de Planejamento com Orquestração Multiagente

Neste exemplo, um Agente Roteador Semântico recebe uma solicitação do usuário (por exemplo, "Preciso de um plano de hotel para minha viagem.").

O planejador então:

* Recebe o Plano de Hotel: O planejador pega a mensagem do usuário e, baseado em um prompt do sistema (incluindo detalhes dos agentes disponíveis), gera um plano de viagem estruturado.
* Lista Agentes e Suas Ferramentas: O registro de agentes mantém uma lista de agentes (por exemplo, para voo, hotel, aluguel de carro e atividades) juntamente com as funções ou ferramentas que eles oferecem.
* Encaminha o Plano para os Agentes Respectivos: Dependendo do número de subtarefas, o planejador envia a mensagem diretamente para um agente dedicado (para cenários de tarefa única) ou coordena via um gerenciador de chat em grupo para colaboração multiagente.
* Resume o Resultado: Finalmente, o planejador resume o plano gerado para maior clareza.

O seguinte código Python ilustra essas etapas:

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

# Modelo de SubTarefa de Viagem

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

# Crie o cliente com variáveis de ambiente com tipo verificado

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Defina a mensagem do usuário

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

# Garanta que o conteúdo da resposta seja uma string JSON válida antes de carregá-lo

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Imprima o conteúdo da resposta após carregá-lo como JSON

pprint(json.loads(response_content))
```

O que segue é a saída do código anterior e você pode então usar essa saída estruturada para encaminhar para o `assigned_agent` e resumir o plano de viagem para o usuário final.

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

Um notebook de exemplo com o código anterior está disponível [aqui](07-autogen.ipynb).

### Planejamento Iterativo

Algumas tarefas exigem um vai-e-volta ou replanejamento, onde o resultado de uma subtarefa influencia a próxima. Por exemplo, se o agente descobrir um formato de dados inesperado ao reservar voos, ele pode precisar adaptar sua estratégia antes de prosseguir para as reservas de hotel.

Além disso, o feedback do usuário (por exemplo, um humano decidindo que prefere um voo mais cedo) pode disparar um replanejamento parcial. Essa abordagem dinâmica e iterativa garante que a solução final esteja alinhada com as restrições do mundo real e as preferências do usuário em evolução.

exemplo de código

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. mesmo que o código anterior e passar o histórico do usuário, plano atual
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
# .. replanejar e enviar as tarefas para os respectivos agentes
```

Para um planejamento mais abrangente, confira o Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">Blogpost</a> para resolver tarefas complexas.

## Resumo

Neste artigo, vimos um exemplo de como podemos criar um planejador que pode selecionar dinamicamente os agentes disponíveis definidos. A saída do Planejador decompõe as tarefas e atribui os agentes para que elas possam ser executadas. Assume-se que os agentes tenham acesso às funções/ferramentas necessárias para realizar a tarefa. Além dos agentes, você pode incluir outros padrões como reflexão, resumidor e chat round robin para personalizar ainda mais.

## Recursos Adicionais

AutoGen Magnetic One - Um sistema multiagente generalista para resolver tarefas complexas que alcançou resultados impressionantes em múltiplos benchmarks desafiadores. Referência: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Nesta implementação, o orquestrador cria um plano de tarefa específico e delega essas tarefas aos agentes disponíveis. Além do planejamento, o orquestrador também emprega um mecanismo de rastreamento para monitorar o progresso da tarefa e replaneja conforme necessário.

### Tem Mais Perguntas sobre o Padrão de Design de Planejamento?

Junte-se ao [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrar outros aprendizes, participar de horários de atendimento e tirar suas dúvidas sobre Agentes de IA.

## Lição Anterior

[Construindo Agentes de IA Confiáveis](../06-building-trustworthy-agents/README.md)

## Próxima Lição

[Padrão de Design Multi-Agente](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:  
Este documento foi traduzido utilizando o serviço de tradução por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Embora nos esforcemos para garantir a precisão, esteja ciente de que traduções automáticas podem conter erros ou imprecisões. O documento original em seu idioma nativo deve ser considerado a fonte autorizada. Para informações críticas, recomenda-se a tradução profissional humana. Não nos responsabilizamos por quaisquer mal-entendidos ou interpretações incorretas decorrentes do uso desta tradução.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->