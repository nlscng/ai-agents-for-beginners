[![Exploring AI Agent Frameworks](../../../translated_images/es/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Haz clic en la imagen de arriba para ver el video de esta lección)_

# Explorar frameworks de agentes de IA

Los frameworks de agentes de IA son plataformas de software diseñadas para simplificar la creación, despliegue y gestión de agentes de IA. Estos frameworks proporcionan a los desarrolladores componentes preconstruidos, abstracciones y herramientas que agilizan el desarrollo de sistemas de IA complejos.

Estos frameworks ayudan a los desarrolladores a centrarse en los aspectos únicos de sus aplicaciones al proporcionar enfoques estandarizados para desafíos comunes en el desarrollo de agentes de IA. Mejoran la escalabilidad, accesibilidad y eficiencia en la construcción de sistemas de IA.

## Introducción 

Esta lección cubrirá:

- ¿Qué son los frameworks de agentes de IA y qué permiten lograr a los desarrolladores?
- ¿Cómo pueden los equipos usarlos para prototipar rápidamente, iterar y mejorar las capacidades de su agente?
- ¿Cuáles son las diferencias entre los frameworks y herramientas creados por Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, y <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>?
- ¿Puedo integrar mis herramientas existentes del ecosistema Azure directamente, o necesito soluciones independientes?
- ¿Qué es el servicio Azure AI Agents y cómo me está ayudando?

## Objetivos de aprendizaje

Los objetivos de esta lección son ayudarte a entender:

- El papel de los frameworks de agentes de IA en el desarrollo de IA.
- Cómo aprovechar los frameworks de agentes de IA para construir agentes inteligentes.
- Capacidades clave habilitadas por los frameworks de agentes de IA.
- Las diferencias entre AutoGen, Semantic Kernel y Azure AI Agent Service.

## ¿Qué son los frameworks de agentes de IA y qué permiten hacer a los desarrolladores?

Los frameworks tradicionales de IA pueden ayudarte a integrar IA en tus aplicaciones y mejorar estas aplicaciones de las siguientes maneras:

- **Personalización**: La IA puede analizar el comportamiento y las preferencias del usuario para ofrecer recomendaciones, contenido y experiencias personalizadas.
Ejemplo: Servicios de streaming como Netflix usan IA para sugerir películas y series basadas en el historial de visualización, mejorando el compromiso y la satisfacción del usuario.
- **Automatización y eficiencia**: La IA puede automatizar tareas repetitivas, agilizar flujos de trabajo y mejorar la eficiencia operativa.
Ejemplo: Aplicaciones de atención al cliente usan chatbots impulsados por IA para manejar consultas comunes, reduciendo los tiempos de respuesta y liberando a los agentes humanos para asuntos más complejos.
- **Mejora de la experiencia del usuario**: La IA puede mejorar la experiencia del usuario proporcionando funciones inteligentes como reconocimiento de voz, procesamiento de lenguaje natural y texto predictivo.
Ejemplo: Asistentes virtuales como Siri y Google Assistant usan IA para entender y responder a comandos de voz, facilitando la interacción de los usuarios con sus dispositivos.

### Todo eso suena genial, ¿entonces por qué necesitamos el framework de agentes de IA?

Los frameworks de agentes de IA representan algo más que simples frameworks de IA. Están diseñados para posibilitar la creación de agentes inteligentes que pueden interactuar con usuarios, otros agentes y el entorno para alcanzar objetivos específicos. Estos agentes pueden mostrar comportamiento autónomo, tomar decisiones y adaptarse a condiciones cambiantes. Veamos algunas capacidades clave habilitadas por los frameworks de agentes de IA:

- **Colaboración y coordinación entre agentes**: Permiten la creación de múltiples agentes de IA que pueden trabajar juntos, comunicarse y coordinarse para resolver tareas complejas.
- **Automatización y gestión de tareas**: Proporcionan mecanismos para automatizar flujos de trabajo de múltiples pasos, delegación de tareas y gestión dinámica de tareas entre agentes.
- **Comprensión contextual y adaptación**: Dotan a los agentes de la capacidad de entender el contexto, adaptarse a entornos cambiantes y tomar decisiones basadas en información en tiempo real.

En resumen, los agentes te permiten hacer más, llevar la automatización al siguiente nivel y crear sistemas más inteligentes que pueden adaptarse y aprender de su entorno.

## ¿Cómo prototipar rápidamente, iterar y mejorar las capacidades del agente?

Este es un panorama que avanza rápidamente, pero hay algunas cosas comunes en la mayoría de los frameworks de agentes de IA que pueden ayudarte a prototipar e iterar rápidamente, a saber: componentes modulares, herramientas colaborativas y aprendizaje en tiempo real. Vamos a profundizar en esto:

- **Usar componentes modulares**: Los SDKs de IA ofrecen componentes preconstruidos como conectores de IA y de memoria, llamadas a funciones usando lenguaje natural o plugins de código, plantillas de prompt y más.
- **Aprovechar herramientas colaborativas**: Diseñar agentes con roles y tareas específicas, permitiéndoles probar y refinar flujos de trabajo colaborativos.
- **Aprender en tiempo real**: Implementar bucles de retroalimentación donde los agentes aprenden de las interacciones y ajustan su comportamiento dinámicamente.

### Usar componentes modulares

SDKs como Microsoft Semantic Kernel y LangChain ofrecen componentes preconstruidos como conectores de IA, plantillas de prompt y gestión de memoria.

**Cómo pueden usar esto los equipos**: Los equipos pueden ensamblar rápidamente estos componentes para crear un prototipo funcional sin comenzar desde cero, lo que permite experimentación e iteración rápidas.

**Cómo funciona en la práctica**: Puedes usar un parser preconstruido para extraer información de la entrada del usuario, un módulo de memoria para almacenar y recuperar datos, y un generador de prompts para interactuar con los usuarios, todo sin tener que construir estos componentes desde cero.

**Código de ejemplo**. Veamos ejemplos de cómo puedes usar un conector de IA preconstruido con Semantic Kernel en Python y .Net que usa llamadas automáticas a funciones para que el modelo responda a la entrada del usuario:

``` python
# Ejemplo de Semantic Kernel en Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Definir un objeto ChatHistory para mantener el contexto de la conversación
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Definir un plugin de ejemplo que contiene la función para reservar viajes
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Crear el Kernel
kernel = Kernel()

# Añadir el plugin de ejemplo al objeto Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Definir el Conector AI de Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Definir la configuración de la solicitud para configurar el modelo con llamada automática a funciones
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Realizar la solicitud al modelo para el historial de chat y configuración de solicitud dados
    # El Kernel contiene el ejemplo que el modelo solicitará invocar
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
    # Ejemplo de Respuesta del Modelo AI: `Tu vuelo a Nueva York el 1 de enero de 2025 ha sido reservado con éxito. ¡Buen viaje! ✈️🗽`

    # Añadir la respuesta del modelo a nuestro contexto de historial de chat
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

Lo que puedes ver en este ejemplo es cómo puedes aprovechar un parser preconstruido para extraer información clave de la entrada del usuario, como el origen, el destino y la fecha de una solicitud de reserva de vuelo. Este enfoque modular te permite centrarte en la lógica de alto nivel.

### Aprovechar herramientas colaborativas

Frameworks como CrewAI, Microsoft AutoGen y Semantic Kernel facilitan la creación de múltiples agentes que pueden trabajar juntos.

**Cómo pueden usar esto los equipos**: Los equipos pueden diseñar agentes con roles y tareas específicas, permitiéndoles probar y refinar flujos de trabajo colaborativos y mejorar la eficiencia general del sistema.

**Cómo funciona en la práctica**: Puedes crear un equipo de agentes donde cada agente tiene una función especializada, como recuperación de datos, análisis o toma de decisiones. Estos agentes pueden comunicarse y compartir información para alcanzar un objetivo común, como responder a una consulta de un usuario o completar una tarea.

**Código de ejemplo (AutoGen)**:

```python
# creando agentes, luego crear un calendario de ronda robin donde puedan trabajar juntos, en este caso en orden

# Agente de Recuperación de Datos
# Agente de Análisis de Datos
# Agente de Toma de Decisiones

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

# la conversación termina cuando el usuario dice "APROBAR"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Use asyncio.run(...) al ejecutar en un script.
await Console(stream)
```

Lo que ves en el código anterior es cómo puedes crear una tarea que implica a múltiples agentes trabajando juntos para analizar datos. Cada agente realiza una función específica y la tarea se ejecuta coordinando a los agentes para alcanzar el resultado deseado. Al crear agentes dedicados con roles especializados, puedes mejorar la eficiencia y el rendimiento de las tareas.

### Aprender en tiempo real

Los frameworks avanzados ofrecen capacidades para la comprensión contextual y la adaptación en tiempo real.

**Cómo pueden usar esto los equipos**: Los equipos pueden implementar bucles de retroalimentación donde los agentes aprenden de las interacciones y ajustan su comportamiento dinámicamente, lo que conduce a una mejora continua y refinamiento de capacidades.

**Cómo funciona en la práctica**: Los agentes pueden analizar la retroalimentación de los usuarios, datos ambientales y resultados de tareas para actualizar su base de conocimientos, ajustar algoritmos de toma de decisiones y mejorar el rendimiento con el tiempo. Este proceso de aprendizaje iterativo permite que los agentes se adapten a condiciones cambiantes y a las preferencias de los usuarios, mejorando la efectividad general del sistema.

## ¿Cuáles son las diferencias entre los frameworks AutoGen, Semantic Kernel y Azure AI Agent Service?

Hay muchas formas de comparar estos frameworks, pero veamos algunas diferencias clave en términos de su diseño, capacidades y casos de uso objetivo:

## AutoGen

AutoGen es un framework de código abierto desarrollado por el AI Frontiers Lab de Microsoft Research. Se centra en aplicaciones *agentic* distribuidas y dirigidas por eventos, permitiendo múltiples LLMs y SLMs, herramientas y patrones avanzados de diseño multiagente.

AutoGen se construye alrededor del concepto central de agentes, que son entidades autónomas que pueden percibir su entorno, tomar decisiones y realizar acciones para lograr objetivos específicos. Los agentes se comunican a través de mensajes asincrónicos, lo que les permite trabajar de forma independiente y en paralelo, mejorando la escalabilidad y la capacidad de respuesta del sistema.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Los agentes se basan en el modelo actor</a>. Según Wikipedia, un actor es _la unidad básica de la computación concurrente. En respuesta a un mensaje que recibe, un actor puede: tomar decisiones locales, crear más actores, enviar más mensajes y determinar cómo responder al siguiente mensaje recibido_.

**Casos de uso**: Automatización de generación de código, tareas de análisis de datos y construcción de agentes personalizados para funciones de planificación e investigación.

Aquí hay algunos conceptos centrales importantes de AutoGen:

- **Agentes**. Un agente es una entidad de software que:
  - **Se comunica mediante mensajes**, estos mensajes pueden ser síncronos o asíncronos.
  - **Mantiene su propio estado**, que puede ser modificado por mensajes entrantes.
  - **Realiza acciones** en respuesta a mensajes recibidos o cambios en su estado. Estas acciones pueden modificar el estado del agente y producir efectos externos, como actualizar registros de mensajes, enviar nuevos mensajes, ejecutar código o realizar llamadas a APIs.
    
  Aquí tienes un breve fragmento de código en el que creas tu propio agente con capacidades de chat:

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
    
    En el código anterior, `MyAgent` ha sido creado y hereda de `RoutedAgent`. Tiene un manejador de mensajes que imprime el contenido del mensaje y luego envía una respuesta usando el delegado `AssistantAgent`. Nota especialmente cómo asignamos a `self._delegate` una instancia de `AssistantAgent`, que es un agente preconstruido que puede manejar completaciones de chat.


    Informemos a AutoGen sobre este tipo de agente y pongamos en marcha el programa a continuación:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Comenzar a procesar mensajes en segundo plano.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    En el código anterior los agentes se registran con el runtime y luego se envía un mensaje al agente dando como resultado la siguiente salida:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multiagentes**. AutoGen soporta la creación de múltiples agentes que pueden trabajar juntos para lograr tareas complejas. Los agentes pueden comunicarse, compartir información y coordinar sus acciones para resolver problemas de forma más eficiente. Para crear un sistema multiagente, puedes definir diferentes tipos de agentes con funciones y roles especializados, como recuperación de datos, análisis, toma de decisiones e interacción con el usuario. Veamos cómo se ve tal creación para hacernos una idea:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Ejemplo de declaración de un Agente
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Usando el tipo de tema como tipo de agente.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # declaraciones restantes abreviadas para mayor brevedad

    # Chat grupal
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

    En el código anterior tenemos un `GroupChatManager` que está registrado con el runtime. Este manager es responsable de coordinar las interacciones entre diferentes tipos de agentes, como escritores, ilustradores, editores y usuarios.

- **Runtime de agentes**. El framework proporciona un entorno de ejecución, permitiendo la comunicación entre agentes, gestiona sus identidades y ciclos de vida, y hace cumplir límites de seguridad y privacidad. Esto significa que puedes ejecutar tus agentes en un entorno seguro y controlado, asegurando que puedan interactuar de forma segura y eficiente. Hay dos runtimes de interés:
  - **Runtime independiente**. Esta es una buena opción para aplicaciones de un solo proceso donde todos los agentes están implementados en el mismo lenguaje de programación y se ejecutan en el mismo proceso. Aquí tienes una ilustración de cómo funciona:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Entorno de ejecución independiente</a>   
Application stack

    *agents communicate via messages through the runtime, and the runtime manages the lifecycle of agents*

  - **Runtime de agentes distribuido**, es adecuado para aplicaciones multiproceso donde los agentes pueden estar implementados en diferentes lenguajes de programación y ejecutarse en diferentes máquinas. Aquí tienes una ilustración de cómo funciona:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Entorno de ejecución distribuido</a>

## Semantic Kernel + Agent Framework

Semantic Kernel es un SDK de orquestación de IA listo para empresas. Consiste en conectores de IA y de memoria, junto con un Agent Framework.

Primero cubramos algunos componentes centrales:

- **Conectores de IA**: Esta es una interfaz con servicios de IA externos y fuentes de datos para usar tanto en Python como en C#.

  ```python
  # Núcleo Semántico Python
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

    Aquí tienes un ejemplo sencillo de cómo puedes crear un kernel y añadir un servicio de completado de chat. Semantic Kernel crea una conexión a un servicio de IA externo, en este caso, Azure OpenAI Chat Completion.

- **Plugins**: Estos encapsulan funciones que una aplicación puede usar. Hay plugins ya hechos y otros personalizados que puedes crear. Un concepto relacionado es el de "funciones de prompt". En lugar de proporcionar indicaciones en lenguaje natural para la invocación de funciones, transmites ciertas funciones al modelo. En función del contexto actual del chat, el modelo puede elegir llamar a una de estas funciones para completar una solicitud o consulta. Aquí tienes un ejemplo:

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

    Aquí, primero tienes un prompt plantilla `skPrompt` que deja espacio para que el usuario introduzca texto, `$userInput`. Luego creas la función del kernel `SummarizeText` y después la importas al kernel con el nombre de plugin `SemanticFunctions`. Observa el nombre de la función que ayuda a Semantic Kernel a entender qué hace la función y cuándo debe ser llamada.

- **Función nativa**: También existen funciones nativas que el framework puede llamar directamente para llevar a cabo la tarea. Aquí tienes un ejemplo de una función así que recupera el contenido de un archivo:

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

- **Memoria**:  Abstracta y simplifica la gestión del contexto para aplicaciones de IA. La idea con la memoria es que esto es algo que el LLM debería conocer. Puedes almacenar esta información en un vector store que termina siendo una base de datos en memoria o una base de datos vectorial o similar. Aquí tienes un ejemplo de un escenario muy simplificado donde se añaden *hechos* a la memoria:

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

    Estos hechos se almacenan luego en la colección de memoria `SummarizedAzureDocs`. Este es un ejemplo muy simplificado, pero puedes ver cómo puedes almacenar información en la memoria para que la LLM la use.

Así que esos son los conceptos básicos del framework Semantic Kernel, ¿y qué pasa con el Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service es una incorporación más reciente, introducida en Microsoft Ignite 2024. Permite el desarrollo y despliegue de agentes de IA con modelos más flexibles, como llamar directamente a LLMs de código abierto como Llama 3, Mistral y Cohere.

Azure AI Agent Service proporciona mecanismos de seguridad empresarial más robustos y métodos de almacenamiento de datos, lo que lo hace adecuado para aplicaciones empresariales. 

Funciona de forma inmediata con frameworks de orquestación multiagente como AutoGen y Semantic Kernel.

Este servicio está actualmente en Public Preview y admite Python y C# para la creación de agentes.

Usando Semantic Kernel Python, podemos crear un Azure AI Agent con un complemento definido por el usuario:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Definir un complemento de ejemplo para la muestra
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
        # Crear la definición del agente
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Crear el Agente AzureAI usando el cliente definido y la definición del agente
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Crear un hilo para mantener la conversación
        # Si no se proporciona un hilo, se creará uno nuevo
        # y se devolverá con la respuesta inicial
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
                # Invocar al agente para el hilo especificado
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

### Conceptos clave

Azure AI Agent Service tiene los siguientes conceptos clave:

- **Agent**. Azure AI Agent Service se integra con Microsoft Foundry. Dentro de AI Foundry, un AI Agent actúa como un microservicio "inteligente" que puede usarse para responder preguntas (RAG), realizar acciones o automatizar completamente flujos de trabajo. Lo logra combinando el poder de los modelos generativos de IA con herramientas que le permiten acceder e interactuar con fuentes de datos del mundo real. Aquí hay un ejemplo de un agente:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    En este ejemplo, se crea un agente con el modelo `gpt-4o-mini`, un nombre `my-agent`, y las instrucciones `You are helpful agent`. El agente está equipado con herramientas y recursos para realizar tareas de interpretación de código.

- **Thread and messages**. El hilo es otro concepto importante. Representa una conversación o interacción entre un agente y un usuario. Los hilos pueden usarse para rastrear el progreso de una conversación, almacenar información de contexto y gestionar el estado de la interacción. Aquí hay un ejemplo de un hilo:

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

    En el código anterior, se crea un hilo. Después, se envía un mensaje al hilo. Al llamar a `create_and_process_run`, se le pide al agente que realice trabajo en el hilo. Finalmente, los mensajes se obtienen y registran para ver la respuesta del agente. Los mensajes indican el progreso de la conversación entre el usuario y el agente. También es importante entender que los mensajes pueden ser de diferentes tipos como texto, imagen o archivo; es decir, el trabajo del agente ha resultado, por ejemplo, en una imagen o en una respuesta de texto. Como desarrollador, puedes usar esta información para procesar aún más la respuesta o presentarla al usuario.

- **Integrates with other AI frameworks**. Azure AI Agent service puede interactuar con otros frameworks como AutoGen y Semantic Kernel, lo que significa que puedes construir parte de tu aplicación en uno de estos frameworks y, por ejemplo, usar el Agent service como orquestador o puedes construir todo en el Agent service.

**Use Cases**: Azure AI Agent Service está diseñado para aplicaciones empresariales que requieren despliegue de agentes de IA seguro, escalable y flexible.

## ¿Cuál es la diferencia entre estos frameworks?
 
Parece que hay mucha superposición entre estos frameworks, pero hay algunas diferencias clave en términos de su diseño, capacidades y casos de uso objetivo:
 
- **AutoGen**: Es un framework de experimentación enfocado en la investigación de vanguardia sobre sistemas multiagente. Es el mejor lugar para experimentar y prototipar sistemas multiagente sofisticados.
- **Semantic Kernel**: Es una librería lista para producción para construir aplicaciones agenticas empresariales. Se centra en aplicaciones agenticas distribuidas y orientadas a eventos, permitiendo múltiples LLMs y SLMs, herramientas y patrones de diseño de agente único/múltiple.
- **Azure AI Agent Service**: Es una plataforma y servicio de despliegue en Azure Foundry para agentes. Ofrece conectividad a servicios soportados por Azure Found, como Azure OpenAI, Azure AI Search, Bing Search y ejecución de código.
 
¿Aún no estás seguro de cuál elegir?

### Casos de uso
 
Veamos si podemos ayudarte pasando por algunos casos de uso comunes:
 
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
 
Resumamos las diferencias clave en una tabla:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Aplicaciones multiagente distribuidas y orientadas a eventos | Agents, Personas, Functions, Data | Generación de código, tareas de análisis de datos |
| Semantic Kernel | Comprensión y generación de texto similar al humano | Agents, Modular Components, Collaboration | Comprensión del lenguaje natural, generación de contenido |
| Azure AI Agent Service | Modelos flexibles, seguridad empresarial, generación de código, invocación de herramientas | Modularity, Collaboration, Process Orchestration | Despliegue de agentes de IA seguro, escalable y flexible |

¿Cuál es el caso de uso ideal para cada uno de estos frameworks?

## ¿Puedo integrar directamente mis herramientas existentes del ecosistema Azure, o necesito soluciones independientes?

La respuesta es sí, puedes integrar tus herramientas existentes del ecosistema Azure directamente con Azure AI Agent Service especialmente, esto porque ha sido diseñado para funcionar sin problemas con otros servicios de Azure. Por ejemplo, podrías integrar Bing, Azure AI Search y Azure Functions. También hay una integración profunda con Microsoft Foundry.

Para AutoGen y Semantic Kernel, también puedes integrar con servicios de Azure, pero puede requerir que llames a los servicios de Azure desde tu código. Otra forma de integrar es usar los SDKs de Azure para interactuar con los servicios de Azure desde tus agentes. Además, como se mencionó, puedes usar Azure AI Agent Service como orquestador para tus agentes construidos en AutoGen o Semantic Kernel, lo que te daría un acceso sencillo al ecosistema Azure.

## Ejemplos de código

- Python: [Framework de Agentes](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Framework de Agentes](./code_samples/02-dotnet-agent-framework.md)

## ¿Tienes más preguntas sobre los frameworks de agentes de IA?

Únete al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrarte con otros estudiantes, asistir a horas de oficina y obtener respuestas a tus preguntas sobre AI Agents.

## Referencias

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel and AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## Previous Lesson

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## Next Lesson

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Descargo de responsabilidad:
Este documento ha sido traducido mediante el servicio de traducción por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Aunque nos esforzamos por la exactitud, tenga en cuenta que las traducciones automáticas pueden contener errores o inexactitudes. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por un traductor humano. No nos hacemos responsables de ningún malentendido o interpretación errónea que surja del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->