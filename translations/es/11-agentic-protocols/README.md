# Uso de Protocolos Agentic (MCP, A2A y NLWeb)

[![Protocolos Agentic](../../../translated_images/es/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Haz clic en la imagen de arriba para ver el video de esta lección)_

A medida que crece el uso de agentes de IA, también lo hace la necesidad de protocolos que aseguren la estandarización, la seguridad y que apoyen la innovación abierta. En esta lección, cubriremos 3 protocolos que buscan satisfacer esta necesidad: Model Context Protocol (MCP), Agent to Agent (A2A) y Natural Language Web (NLWeb).

## Introducción

En esta lección, cubriremos:

• Cómo **MCP** permite que los agentes de IA accedan a herramientas y datos externos para completar las tareas del usuario.

• Cómo **A2A** habilita la comunicación y colaboración entre diferentes agentes de IA.

• Cómo **NLWeb** lleva interfaces de lenguaje natural a cualquier sitio web, permitiendo que los agentes de IA descubran e interactúen con el contenido.

## Objetivos de aprendizaje

• **Identificar** el propósito central y los beneficios de MCP, A2A y NLWeb en el contexto de agentes de IA.

• **Explicar** cómo cada protocolo facilita la comunicación e interacción entre LLMs, herramientas y otros agentes.

• **Reconocer** los roles distintos que desempeña cada protocolo en la construcción de sistemas agenticos complejos.

## Protocolo de Contexto de Modelo (MCP)

El **Model Context Protocol (MCP)** es un estándar abierto que proporciona una forma estandarizada para que las aplicaciones suministren contexto y herramientas a los LLMs. Esto habilita un "adaptador universal" a diferentes fuentes de datos y herramientas a las que los agentes de IA pueden conectarse de manera consistente.

Veamos los componentes de MCP, los beneficios en comparación con el uso directo de APIs y un ejemplo de cómo los agentes de IA podrían usar un servidor MCP.

### Componentes principales de MCP

MCP opera sobre una **arquitectura cliente-servidor** y los componentes principales son:

• **Hosts** son aplicaciones LLM (por ejemplo un editor de código como VSCode) que inician las conexiones a un servidor MCP.

• **Clients** son componentes dentro de la aplicación host que mantienen conexiones uno a uno con servidores.

• **Servers** son programas ligeros que exponen capacidades específicas.

En el protocolo se incluyen tres primitivas principales que constituyen las capacidades de un servidor MCP:

• **Tools**: Son acciones o funciones discretas que un agente de IA puede invocar para realizar una acción. Por ejemplo, un servicio meteorológico podría exponer una herramienta "get weather", o un servidor de comercio electrónico podría exponer una herramienta "purchase product". Los servidores MCP anuncian el nombre de cada herramienta, su descripción y el esquema de entrada/salida en su listado de capacidades.

• **Resources**: Son elementos de datos o documentos de solo lectura que un servidor MCP puede proporcionar, y que los clients pueden recuperar bajo demanda. Ejemplos incluyen contenidos de archivos, registros de bases de datos o archivos de registro. Las resources pueden ser texto (como código o JSON) o binarios (como imágenes o PDFs).

• **Prompts**: Son plantillas predefinidas que ofrecen sugerencias de prompts, permitiendo flujos de trabajo más complejos.

### Beneficios de MCP

MCP ofrece ventajas significativas para los agentes de IA:

• **Descubrimiento dinámico de herramientas**: Los agentes pueden recibir dinámicamente una lista de herramientas disponibles desde un servidor junto con descripciones de lo que hacen. Esto contrasta con las APIs tradicionales, que a menudo requieren codificación estática para integraciones, lo que significa que cualquier cambio en la API necesita actualizaciones de código. MCP ofrece un enfoque de "integrar una vez", conduciendo a una mayor adaptabilidad.

• **Interoperabilidad entre LLMs**: MCP funciona con diferentes LLMs, proporcionando flexibilidad para cambiar el modelo principal y evaluar un mejor rendimiento.

• **Seguridad estandarizada**: MCP incluye un método de autenticación estándar, mejorando la escalabilidad al añadir acceso a servidores MCP adicionales. Esto es más simple que gestionar diferentes claves y tipos de autenticación para varias APIs tradicionales.

### Ejemplo de MCP

![Diagrama MCP](../../../translated_images/es/mcp-diagram.e4ca1cbd551444a1.webp)

Imagina que un usuario desea reservar un vuelo usando un asistente de IA potenciado por MCP.

1. **Conexión**: El asistente de IA (el client MCP) se conecta a un servidor MCP proporcionado por una aerolínea.

2. **Descubrimiento de herramientas**: El client pregunta al servidor MCP de la aerolínea: "¿Qué herramientas tienen disponibles?" El servidor responde con herramientas como "search flights" y "book flights".

3. **Invocación de herramienta**: Luego le pides al asistente de IA: "Por favor busca un vuelo de Portland a Honolulu." El asistente de IA, usando su LLM, identifica que necesita llamar a la herramienta "search flights" y pasa los parámetros relevantes (origen, destino) al servidor MCP.

4. **Ejecución y respuesta**: El servidor MCP, actuando como envoltorio, realiza la llamada real a la API interna de reservas de la aerolínea. Luego recibe la información de vuelos (por ejemplo, datos JSON) y la envía de vuelta al asistente de IA.

5. **Interacción adicional**: El asistente de IA presenta las opciones de vuelo. Una vez que seleccionas un vuelo, el asistente podría invocar la herramienta "book flight" en el mismo servidor MCP, completando la reserva.

## Protocolo Agente-a-Agente (A2A)

Mientras que MCP se enfoca en conectar LLMs con herramientas, el **Agent-to-Agent (A2A) protocol** lleva esto un paso más allá al habilitar la comunicación y colaboración entre diferentes agentes de IA. A2A conecta agentes de IA a través de distintas organizaciones, entornos y pilas tecnológicas para completar una tarea compartida.

Examinaremos los componentes y beneficios de A2A, junto con un ejemplo de cómo podría aplicarse en nuestra aplicación de viajes.

### Componentes principales de A2A

A2A se centra en habilitar la comunicación entre agentes y en que trabajen juntos para completar una subtarea del usuario. Cada componente del protocolo contribuye a esto:

#### Tarjeta del agente

Similar a cómo un servidor MCP comparte una lista de herramientas, una Agent Card tiene:
- El nombre del agente .
- Una **descripción de las tareas generales** que realiza.
- Una **lista de habilidades específicas** con descripciones para ayudar a otros agentes (o incluso a usuarios humanos) a entender cuándo y por qué querrían invocar a ese agente.
- La **URL del Endpoint actual** del agente
- La **versión** y las **capacidades** del agente, como respuestas en streaming y notificaciones push.

#### Ejecutor del agente

El Agent Executor es responsable de **pasar el contexto del chat del usuario al agente remoto**, el agente remoto necesita esto para comprender la tarea que debe completarse. En un servidor A2A, un agente usa su propio Large Language Model (LLM) para analizar las solicitudes entrantes y ejecutar tareas usando sus propias herramientas internas.

#### Artefacto

Una vez que un agente remoto ha completado la tarea solicitada, su producto de trabajo se crea como un artefacto. Un artefacto **contiene el resultado del trabajo del agente**, una **descripción de lo que se completó** y el **contexto de texto** que se envía a través del protocolo. Después de que se envía el artefacto, la conexión con el agente remoto se cierra hasta que sea necesaria nuevamente.

#### Cola de eventos

Este componente se utiliza para **manejar actualizaciones y pasar mensajes**. Es particularmente importante en producción para sistemas agenticos, para evitar que la conexión entre agentes se cierre antes de que se complete una tarea, especialmente cuando los tiempos de finalización de tareas pueden ser más largos.

### Beneficios de A2A

• **Colaboración mejorada**: Permite que agentes de distintos proveedores y plataformas interactúen, compartan contexto y trabajen juntos, facilitando la automatización fluida a través de sistemas tradicionalmente desconectados.

• **Flexibilidad en la selección de modelos**: Cada agente A2A puede decidir qué LLM utiliza para atender sus solicitudes, permitiendo modelos optimizados o afinados por agente, a diferencia de una única conexión LLM en algunos escenarios MCP.

• **Autenticación integrada**: La autenticación está integrada directamente en el protocolo A2A, proporcionando un marco de seguridad robusto para las interacciones entre agentes.

### Ejemplo de A2A

![Diagrama A2A](../../../translated_images/es/A2A-Diagram.8666928d648acc26.webp)

Ampliemos nuestro escenario de reservas de viaje, pero esta vez usando A2A.

1. **Solicitud del usuario a un agente múltiple**: Un usuario interactúa con un "Agente de Viajes" cliente/agente A2A, quizás diciendo: "Por favor reserva un viaje completo a Honolulu para la próxima semana, incluyendo vuelos, hotel y coche de alquiler".

2. **Orquestación por el Agente de Viajes**: El Agente de Viajes recibe esta solicitud compleja. Usa su LLM para razonar sobre la tarea y determinar que necesita interactuar con otros agentes especializados.

3. **Comunicación entre agentes**: El Agente de Viajes usa el protocolo A2A para conectarse con agentes descendentes, como un "Agente de Aerolínea", un "Agente de Hotel" y un "Agente de Alquiler de Coches" creados por diferentes compañías.

4. **Ejecución delegada de tareas**: El Agente de Viajes envía tareas específicas a estos agentes especializados (por ejemplo, "Encuentra vuelos a Honolulu", "Reserva un hotel", "Alquila un coche"). Cada uno de estos agentes especializados, ejecutando sus propios LLMs y utilizando sus propias herramientas (que podrían ser servidores MCP), realiza su parte específica de la reserva.

5. **Respuesta consolidada**: Una vez que todos los agentes descendentes completan sus tareas, el Agente de Viajes compila los resultados (detalles de vuelo, confirmación de hotel, reserva de coche) y envía una respuesta completa, al estilo chat, al usuario.

## Web de Lenguaje Natural (NLWeb)

Los sitios web han sido durante mucho tiempo la principal forma para que los usuarios accedan a información y datos en internet.

Veamos los diferentes componentes de NLWeb, los beneficios de NLWeb y un ejemplo de cómo funciona nuestro NLWeb observando nuestra aplicación de viajes.

### Componentes de NLWeb

- **NLWeb Application (Core Service Code)**: El sistema que procesa preguntas en lenguaje natural. Conecta las diferentes partes de la plataforma para crear respuestas. Puedes pensar en él como el **motor que impulsa las funciones de lenguaje natural** de un sitio web.

- **NLWeb Protocol**: Este es un **conjunto básico de reglas para la interacción en lenguaje natural** con un sitio web. Devuelve respuestas en formato JSON (a menudo usando Schema.org). Su propósito es crear una base simple para la "Web de IA", de la misma manera que HTML hizo posible compartir documentos en línea.

- **MCP Server (Model Context Protocol Endpoint)**: Cada configuración de NLWeb también funciona como un **servidor MCP**. Esto significa que puede **compartir herramientas (como un método “ask”) y datos** con otros sistemas de IA. En la práctica, esto hace que el contenido y las capacidades del sitio web sean utilizables por agentes de IA, permitiendo que el sitio se convierta en parte del ecosistema más amplio de agentes.

- **Embedding Models**: Estos modelos se utilizan para **convertir el contenido del sitio web en representaciones numéricas llamadas vectores** (embeddings). Estos vectores capturan el significado de una forma que las computadoras pueden comparar y buscar. Se almacenan en una base de datos especial, y los usuarios pueden elegir qué modelo de embedding desean usar.

- **Vector Database (Retrieval Mechanism)**: Esta base de datos **almacena los embeddings del contenido del sitio web**. Cuando alguien hace una pregunta, NLWeb consulta la base de datos vectorial para encontrar rápidamente la información más relevante. Proporciona una lista rápida de posibles respuestas, ordenadas por similitud. NLWeb funciona con distintos sistemas de almacenamiento de vectores como Qdrant, Snowflake, Milvus, Azure AI Search y Elasticsearch.

### Ejemplo de NLWeb

![NLWeb](../../../translated_images/es/nlweb-diagram.c1e2390b310e5fe4.webp)

Considera nuevamente nuestro sitio web de reservas de viajes, pero esta vez, impulsado por NLWeb.

1. **Ingesta de datos**: Los catálogos de productos existentes del sitio de viajes (por ejemplo, listados de vuelos, descripciones de hoteles, paquetes turísticos) se formatean usando Schema.org o se cargan mediante feeds RSS. Las herramientas de NLWeb ingieren estos datos estructurados, crean embeddings y los almacenan en una base de datos vectorial local o remota.

2. **Consulta en lenguaje natural (humano)**: Un usuario visita el sitio y, en lugar de navegar menús, escribe en una interfaz de chat: "Encuéntrame un hotel familiar en Honolulu con piscina para la próxima semana".

3. **Procesamiento NLWeb**: La aplicación NLWeb recibe esta consulta. Envía la consulta a un LLM para su comprensión y, simultáneamente, busca en su base de datos vectorial los listados de hoteles relevantes.

4. **Resultados precisos**: El LLM ayuda a interpretar los resultados de búsqueda de la base de datos, identifica las mejores coincidencias en función de los criterios "familiar", "piscina" y "Honolulu", y luego formatea una respuesta en lenguaje natural. De manera crucial, la respuesta se refiere a hoteles reales del catálogo del sitio, evitando información inventada.

5. **Interacción con un agente de IA**: Debido a que NLWeb funciona como un servidor MCP, un agente de viajes de IA externo también podría conectarse a la instancia NLWeb de este sitio. El agente de IA podría entonces usar el método `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")`. La instancia NLWeb procesaría esto, aprovechando su base de datos de información de restaurantes (si está cargada), y devolvería una respuesta JSON estructurada.

### ¿Tienes más preguntas sobre MCP/A2A/NLWeb?

Únete al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrarte con otros aprendices, asistir a horas de oficina y obtener respuestas a tus preguntas sobre Agentes de IA.

## Recursos

- [MCP para Principiantes](https://aka.ms/mcp-for-beginners)  
- [Documentación de MCP](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Repositorio de NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Guías de Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Descargo de responsabilidad:
Este documento ha sido traducido mediante el servicio de traducción por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Aunque nos esforzamos por la exactitud, tenga en cuenta que las traducciones automáticas pueden contener errores o inexactitudes. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por un traductor humano. No nos hacemos responsables de malentendidos o interpretaciones erróneas que puedan derivarse del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->