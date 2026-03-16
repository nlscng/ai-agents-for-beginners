# Explorando el Microsoft Agent Framework

![Agent Framework](../../../translated_images/es/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introducción

Esta lección cubrirá:

- Comprender Microsoft Agent Framework: Características clave y valor  
- Explorar los conceptos clave de Microsoft Agent Framework
- Comparar MAF con Semantic Kernel y AutoGen: Guía de migración

## Objetivos de aprendizaje

Después de completar esta lección, sabrás cómo:

- Construir agentes de IA listos para producción usando Microsoft Agent Framework
- Aplicar las funcionalidades principales de Microsoft Agent Framework a tus casos de uso agent-based
- Migrar e integrar frameworks y herramientas de agentes existentes  

## Ejemplos de código 

Los ejemplos de código para [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) se encuentran en este repositorio bajo los archivos `xx-python-agent-framework` y `xx-dotnet-agent-framework`.

## Comprendiendo Microsoft Agent Framework

![Framework Intro](../../../translated_images/es/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) se basa en la experiencia y aprendizajes de Semantic Kernel y AutoGen. Ofrece la flexibilidad para abordar la amplia variedad de casos de uso agent-based observados tanto en entornos de producción como de investigación, incluyendo:

- **Orquestación secuencial de agentes** en escenarios donde se necesitan flujos de trabajo paso a paso.
- **Orquestación concurrente** en escenarios donde los agentes deben completar tareas al mismo tiempo.
- **Orquestación de chat grupal** en escenarios donde los agentes pueden colaborar juntos en una tarea.
- **Orquestación de transferencia** en escenarios donde los agentes pasan la tarea uno al otro a medida que se completan las subtareas.
- **Orquestación magnética** en escenarios donde un agente administrador crea y modifica una lista de tareas y maneja la coordinación de subagentes para completar la tarea.

Para entregar agentes de IA en producción, MAF también incluye características para:

- **Observabilidad** a través del uso de OpenTelemetry, donde cada acción del agente de IA incluyendo invocación de herramientas, pasos de orquestación, flujos de razonamiento y monitoreo de rendimiento mediante paneles de Microsoft Foundry.
- **Seguridad** alojando agentes de forma nativa en Microsoft Foundry, que incluye controles de seguridad como acceso basado en roles, manejo de datos privados y seguridad de contenido incorporada.
- **Durabilidad** ya que los hilos y flujos de trabajo de agentes pueden pausarse, reanudarse y recuperarse de errores, permitiendo procesos de larga duración.
- **Control** con soporte para flujos de trabajo con intervención humana donde las tareas se marcan como requeridas de aprobación humana.

Microsoft Agent Framework también se enfoca en ser interoperable mediante:

- **Ser independiente de la nube** - Los agentes pueden ejecutarse en contenedores, en local y a través de múltiples nubes diferentes.
- **Ser independiente del proveedor** - Los agentes pueden crearse usando tu SDK preferido, incluyendo Azure OpenAI y OpenAI
- **Integrar estándares abiertos** - Los agentes pueden utilizar protocolos como Agent-to-Agent (A2A) y Model Context Protocol (MCP) para descubrir y usar otros agentes y herramientas.
- **Plugins y Conectores** - Se pueden establecer conexiones a servicios de datos y memoria como Microsoft Fabric, SharePoint, Pinecone y Qdrant.

Veamos cómo se aplican estas características a algunos de los conceptos centrales de Microsoft Agent Framework.

## Conceptos clave de Microsoft Agent Framework

### Agentes

![Agent Framework](../../../translated_images/es/agent-components.410a06daf87b4fef.webp)

**Creando agentes**

La creación de agentes se realiza definiendo el servicio de inferencia (proveedor LLM), un
conjunto de instrucciones para que el agente de IA siga y un `nombre` asignado:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Lo anterior usa `Azure OpenAI` pero los agentes pueden crearse utilizando una variedad de servicios incluyendo `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

APIs de OpenAI `Responses`, `ChatCompletion`

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

o agentes remotos usando el protocolo A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Ejecución de agentes**

Los agentes se ejecutan usando los métodos `.run` o `.run_stream` para respuestas sin streaming o con streaming respectivamente.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Cada ejecución de agente también puede tener opciones para personalizar parámetros como `max_tokens` usados por el agente, las `tools` que el agente puede llamar, e incluso el `modelo` usado para el agente.

Esto es útil en casos donde se requieren modelos o herramientas específicas para completar la tarea del usuario.

**Herramientas**

Las herramientas pueden definirse tanto al crear el agente:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Al crear un ChatAgent directamente

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

como al ejecutar el agente:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Herramienta proporcionada solo para esta ejecución )
```

**Hilos de agente**

Los hilos de agente se usan para manejar conversaciones de varios turnos. Los hilos pueden crearse de dos formas:

- Usando `get_new_thread()` que permite que el hilo se guarde a lo largo del tiempo
- Creando un hilo automáticamente cuando se ejecuta un agente y que sólo dura durante la ejecución actual.

Para crear un hilo, el código es así:

```python
# Crear un nuevo hilo.
thread = agent.get_new_thread() # Ejecutar el agente con el hilo.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Luego puedes serializar el hilo para almacenarlo para uso posterior:

```python
# Crear un nuevo hilo.
thread = agent.get_new_thread() 

# Ejecutar el agente con el hilo.

response = await agent.run("Hello, how are you?", thread=thread) 

# Serializar el hilo para almacenamiento.

serialized_thread = await thread.serialize() 

# Deserializar el estado del hilo después de cargar desde el almacenamiento.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware de agente**

Los agentes interactúan con herramientas y LLMs para completar las tareas del usuario. En ciertos escenarios, queremos ejecutar o rastrear entre estas interacciones. El middleware de agente nos permite hacer esto a través de:

*Middleware de función*

Este middleware nos permite ejecutar una acción entre el agente y una función/herramienta que llamará. Un ejemplo de uso podría ser para realizar algún registro (logging) de la llamada a la función.

En el código de abajo `next` define si se debe llamar al siguiente middleware o a la función real.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Preprocesamiento: Registrar antes de la ejecución de la función
    print(f"[Function] Calling {context.function.name}")

    # Continuar con el siguiente middleware o la ejecución de la función
    await next(context)

    # Posprocesamiento: Registrar después de la ejecución de la función
    print(f"[Function] {context.function.name} completed")
```

*Middleware de chat*

Este middleware permite ejecutar o registrar una acción entre el agente y las solicitudes entre el LLM.

Esto contiene información importante como los `messages` que se envían al servicio de IA.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Preprocesamiento: Registrando antes de la llamada de IA
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Continuar al siguiente middleware o servicio de IA
    await next(context)

    # Postprocesamiento: Registrar después de la respuesta de IA
    print("[Chat] AI response received")

```

**Memoria del agente**

Como se cubrió en la lección `Agentic Memory`, la memoria es un elemento importante para permitir que el agente opere sobre diferentes contextos. MAF ofrece varios tipos diferentes de memorias:

*Almacenamiento en memoria*

Esta es la memoria almacenada en hilos durante la ejecución de la aplicación.

```python
# Crear un nuevo hilo.
thread = agent.get_new_thread() # Ejecutar el agente con el hilo.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Mensajes persistentes*

Esta memoria se utiliza para almacenar el historial de conversación a través de diferentes sesiones. Se define usando `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Crear una tienda de mensajes personalizada
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Memoria dinámica*

Esta memoria se añade al contexto antes de ejecutar a los agentes. Estas memorias pueden almacenarse en servicios externos como mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Usando Mem0 para capacidades avanzadas de memoria
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

**Observabilidad del agente**

La observabilidad es importante para construir sistemas agent-based fiables y mantenibles. MAF se integra con OpenTelemetry para proveer trazas y métricas para mejor observabilidad.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # hacer algo
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Flujos de trabajo

MAF ofrece flujos de trabajo que son pasos predefinidos para completar una tarea e incluyen agentes de IA como componentes en esos pasos.

Los flujos de trabajo están compuestos por diferentes componentes que permiten un mejor control del flujo. Los flujos de trabajo también habilitan **orquestación multi-agente** y **checkpointing** para guardar estados del flujo de trabajo.

Los componentes centrales de un flujo de trabajo son:

**Ejecutores**

Los ejecutores reciben mensajes de entrada, realizan sus tareas asignadas y luego producen un mensaje de salida. Esto mueve el flujo hacia adelante para completar la tarea mayor. Los ejecutores pueden ser agentes de IA o lógica personalizada.

**Conexiones**

Las conexiones se utilizan para definir el flujo de mensajes en un flujo de trabajo. Estas pueden ser:

*Conexiones directas* - Conexiones simples uno a uno entre ejecutores:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Conexiones condicionales* - Se activan después de que se cumple cierta condición. Por ejemplo, cuando no hay habitaciones de hotel disponibles, un ejecutor puede sugerir otras opciones.

*Conexiones switch-case* - Dirigen mensajes a diferentes ejecutores basándose en condiciones definidas. Por ejemplo, si un cliente de viajes tiene acceso prioritario y sus tareas serán manejadas a través de otro flujo de trabajo.

*Conexiones fan-out* - Envían un mensaje a múltiples destinos.

*Conexiones fan-in* - Recogen múltiples mensajes de diferentes ejecutores y envían a un solo destino.

**Eventos**

Para proporcionar mejor observabilidad en los flujos de trabajo, MAF ofrece eventos incorporados para la ejecución, incluyendo:

- `WorkflowStartedEvent`  - Comienza la ejecución del flujo de trabajo
- `WorkflowOutputEvent` - El flujo de trabajo produce una salida
- `WorkflowErrorEvent` - El flujo de trabajo encuentra un error
- `ExecutorInvokeEvent`  - El ejecutor comienza el procesamiento
- `ExecutorCompleteEvent`  -  El ejecutor termina el procesamiento
- `RequestInfoEvent` - Se emite una solicitud

## Migrando desde otros frameworks (Semantic Kernel y AutoGen)

### Diferencias entre MAF y Semantic Kernel

**Creación simplificada de agentes**

Semantic Kernel requiere la creación de una instancia de Kernel para cada agente. MAF utiliza un enfoque simplificado usando extensiones para los principales proveedores.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Creación de hilos de agente**

Semantic Kernel requiere que los hilos se creen manualmente. En MAF, el hilo se asigna directamente al agente.

```python
thread = agent.get_new_thread() # Ejecutar el agente con el hilo.
```

**Registro de herramientas**

En Semantic Kernel, las herramientas se registran en el Kernel y luego se pasa el Kernel al agente. En MAF, las herramientas se registran directamente durante el proceso de creación del agente.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Diferencias entre MAF y AutoGen

**Equipos vs Flujo de trabajo**

`Teams` son la estructura de eventos para actividades basadas en eventos con agentes en AutoGen. MAF usa `Workflows` que enrutan datos a ejecutores mediante una arquitectura basada en gráficos.

**Creación de herramientas**

AutoGen usa `FunctionTool` para envolver funciones que los agentes pueden llamar. MAF usa @ai_function que opera de forma similar pero también infiere automáticamente los esquemas para cada función.

**Comportamiento del agente**

Los agentes son de turno único por defecto en AutoGen, a menos que se establezca `max_tool_iterations` a un valor mayor. En MAF, `ChatAgent` es de múltiples turnos por defecto, lo que significa que seguirá llamando herramientas hasta que se complete la tarea del usuario.

## Ejemplos de código 

Los ejemplos de código para Microsoft Agent Framework se pueden encontrar en este repositorio bajo los archivos `xx-python-agent-framework` y `xx-dotnet-agent-framework`.

## ¿Tienes más preguntas sobre Microsoft Agent Framework?

Únete al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para conocer a otros aprendices, asistir a horas de oficina y resolver tus preguntas sobre Agentes de IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso legal**:
Este documento ha sido traducido utilizando el servicio de traducción automática [Co-op Translator](https://github.com/Azure/co-op-translator). Aunque nos esforzamos por lograr precisión, tenga en cuenta que las traducciones automáticas pueden contener errores o inexactitudes. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por humanos. No nos hacemos responsables de ningún malentendido o interpretación errónea derivada del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->