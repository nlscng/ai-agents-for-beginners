[![Planning Design Pattern](../../../translated_images/es/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Haz clic en la imagen arriba para ver el video de esta lección)_

# Diseño de Planificación

## Introducción

Esta lección cubrirá

* Definir un objetivo general claro y descomponer una tarea compleja en tareas manejables.
* Aprovechar la salida estructurada para respuestas más confiables y legibles por máquinas.
* Aplicar un enfoque basado en eventos para manejar tareas dinámicas e inputs inesperados.

## Objetivos de Aprendizaje

Después de completar esta lección, tendrás una comprensión sobre:

* Identificar y establecer un objetivo general para un agente de IA, asegurando que sepa claramente qué debe lograrse.
* Descomponer una tarea compleja en subtareas manejables y organizarlas en una secuencia lógica.
* Equipar a los agentes con las herramientas adecuadas (por ejemplo, herramientas de búsqueda o de análisis de datos), decidir cuándo y cómo se usan, y manejar situaciones inesperadas que surjan.
* Evaluar los resultados de las subtareas, medir el rendimiento e iterar sobre las acciones para mejorar el resultado final.

## Definición del Objetivo General y Descomposición de una Tarea

![Defining Goals and Tasks](../../../translated_images/es/defining-goals-tasks.d70439e19e37c47a.webp)

La mayoría de las tareas del mundo real son demasiado complejas para abordarlas en un solo paso. Un agente de IA necesita un objetivo conciso para guiar su planificación y acciones. Por ejemplo, considere el objetivo:

    "Generar un itinerario de viaje de 3 días."

Aunque es simple de enunciar, aún necesita refinamiento. Cuanto más claro sea el objetivo, mejor podrá el agente (y cualquier colaborador humano) concentrarse en lograr el resultado correcto, como crear un itinerario completo con opciones de vuelos, recomendaciones de hoteles y sugerencias de actividades.

### Descomposición de Tareas

Las tareas grandes o intrincadas son más manejables cuando se dividen en subtareas orientadas a objetivos.
Para el ejemplo del itinerario de viaje, podrías descomponer el objetivo en:

* Reserva de vuelo
* Reserva de hotel
* Alquiler de coche
* Personalización

Cada subtarea puede ser abordada por agentes o procesos dedicados. Un agente podría especializarse en buscar las mejores ofertas de vuelo, otro en reservas de hotel, y así sucesivamente. Un agente coordinador o "aguas abajo" puede luego compilar estos resultados en un itinerario cohesivo para el usuario final.

Este enfoque modular también permite mejoras incrementales. Por ejemplo, podrías añadir agentes especializados para Recomendaciones de Comida o Sugerencias de Actividades Locales y refinar el itinerario con el tiempo.

### Salida Estructurada

Los Modelos de Lenguaje Grande (LLMs) pueden generar salida estructurada (por ejemplo JSON) que es más fácil para que agentes o servicios aguas abajo la analicen y procesen. Esto es especialmente útil en un contexto multiagente, donde podemos ejecutar estas tareas una vez que se recibe la salida de la planificación. Consulta este <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">artículo de blog</a> para una visión rápida.

El siguiente fragmento de Python demuestra un agente de planificación simple que descompone un objetivo en subtareas y genera un plan estructurado:

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

# Modelo de Subtarea de Viaje
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # queremos asignar la tarea al agente

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Para autenticarse con el modelo necesitará generar un token de acceso personal (PAT) en su configuración de GitHub.
    # Cree su token PAT siguiendo las instrucciones aquí: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Definir el mensaje del usuario
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

# # Asegurarse de que el contenido de la respuesta sea una cadena JSON válida antes de cargarlo
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# si response_content es None:
#     raise ValueError("El contenido de la respuesta no es una cadena JSON válida")

# # Imprimir el contenido de la respuesta después de cargarlo como JSON
# pprint(json.loads(response_content))

# Validar el contenido de la respuesta con el modelo MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Agente de Planificación con Orquestación Multiagente

En este ejemplo, un Agente Enrutador Semántico recibe una solicitud de usuario (por ejemplo, "Necesito un plan de hotel para mi viaje.").

El planificador entonces:

* Recibe el Plan de Hotel: El planificador toma el mensaje del usuario y, basado en un mensaje del sistema (incluyendo detalles de los agentes disponibles), genera un plan de viaje estructurado.
* Enumera Agentes y Sus Herramientas: El registro de agentes contiene una lista de agentes (por ejemplo, para vuelo, hotel, alquiler de coche y actividades) junto con las funciones o herramientas que ofrecen.
* Dirige el Plan a los Agentes Respectivos: Dependiendo del número de subtareas, el planificador envía el mensaje directamente a un agente dedicado (para escenarios de una sola tarea) o coordina mediante un administrador de chat grupal para colaboración multiagente.
* Resume el Resultado: Finalmente, el planificador resume el plan generado para mayor claridad.
El siguiente código Python ilustra estos pasos:

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

# Modelo de Subtarea de Viaje

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # queremos asignar la tarea al agente

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Crear el cliente con variables de entorno con tipo verificado

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Definir el mensaje del usuario

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

# Asegurarse de que el contenido de la respuesta sea una cadena JSON válida antes de cargarlo

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Imprimir el contenido de la respuesta después de cargarlo como JSON

pprint(json.loads(response_content))
```

A continuación se muestra la salida del código anterior y puedes usar esta salida estructurada para dirigirla al `assigned_agent` y resumir el plan de viaje al usuario final.

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

Un cuaderno de ejemplo con el código anterior está disponible [aquí](07-autogen.ipynb).

### Planificación Iterativa

Algunas tareas requieren ida y vuelta o re-planificación, donde el resultado de una subtarea influye en la siguiente. Por ejemplo, si el agente descubre un formato de datos inesperado al reservar vuelos, podría necesitar adaptar su estrategia antes de continuar con las reservas de hotel.

Además, la retroalimentación del usuario (ej. un humano que decide que prefiere un vuelo más temprano) puede desencadenar una re-planificación parcial. Este enfoque dinámico e iterativo asegura que la solución final se alinee con las restricciones del mundo real y las preferencias cambiantes del usuario.

ejemplo de código

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. igual que el código anterior y pasa el historial del usuario, el plan actual
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
# .. replanifica y envía las tareas a los agentes respectivos
```

Para una planificación más completa, consulta Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">artículo de blog</a> para resolver tareas complejas.

## Resumen

En este artículo vimos un ejemplo de cómo podemos crear un planificador que puede seleccionar dinámicamente los agentes disponibles definidos. La salida del Planificador descompone las tareas y asigna los agentes para que puedan ser ejecutadas. Se asume que los agentes tienen acceso a las funciones/herramientas necesarias para realizar la tarea. Además de los agentes, puedes incluir otros patrones como reflexión, resumen y chat round robin para personalizar aún más.

## Recursos Adicionales

AutoGen Magentic One - Un sistema multiagente generalista para resolver tareas complejas y que ha logrado resultados impresionantes en múltiples desafíantes benchmarks agenticos. Referencia: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. En esta implementación, el orquestador crea un plan específico para la tarea y delega estas tareas a los agentes disponibles. Además de planificar, el orquestador emplea un mecanismo de seguimiento para monitorear el progreso de la tarea y re-planifica según se requiera.

### ¿Tienes Más Preguntas sobre el Patrón de Diseño de Planificación?

Únete al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para conocer a otros aprendices, asistir a horas de oficina y resolver tus dudas sobre Agentes AI.

## Lección Anterior

[Construyendo agentes de IA confiables](../06-building-trustworthy-agents/README.md)

## Próxima Lección

[Patrón de diseño Multi-Agente](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso legal**:
Este documento ha sido traducido utilizando el servicio de traducción automática [Co-op Translator](https://github.com/Azure/co-op-translator). Aunque nos esforzamos por lograr precisión, tenga en cuenta que las traducciones automáticas pueden contener errores o inexactitudes. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por un humano. No nos responsabilizamos por malentendidos o interpretaciones erróneas derivadas del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->