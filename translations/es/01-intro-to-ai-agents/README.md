[![Intro to AI Agents](../../../translated_images/es/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Haz clic en la imagen de arriba para ver el video de esta lección)_


# Introducción a los Agentes de IA y Casos de Uso de Agentes

¡Bienvenido al curso "Agentes de IA para Principiantes"! Este curso ofrece conocimientos fundamentales y ejemplos aplicados para construir Agentes de IA.

Únete a la <a href="https://discord.gg/kzRShWzttr" target="_blank">Comunidad de Discord de Azure AI</a> para conocer a otros estudiantes y constructores de agentes de IA y preguntar cualquier duda que tengas sobre este curso.

Para comenzar este curso, iniciamos obteniendo una mejor comprensión de qué son los Agentes de IA y cómo podemos usarlos en las aplicaciones y flujos de trabajo que construimos.

## Introducción

Esta lección cubre:

- ¿Qué son los Agentes de IA y cuáles son los diferentes tipos de agentes?
- ¿Qué casos de uso son más adecuados para los Agentes de IA y cómo pueden ayudarnos?
- ¿Cuáles son algunos de los bloques de construcción básicos al diseñar soluciones agentivas?

## Objetivos de Aprendizaje
Después de completar esta lección, deberías ser capaz de:

- Entender los conceptos de Agentes de IA y cómo se diferencian de otras soluciones de IA.
- Aplicar Agentes de IA de la manera más eficiente.
- Diseñar soluciones agentivas de forma productiva tanto para usuarios como para clientes.

## Definiendo Agentes de IA y Tipos de Agentes de IA

### ¿Qué son los Agentes de IA?

Los Agentes de IA son **sistemas** que permiten a los **Modelos de Lenguaje a Gran Escala(LLMs)** **realizar acciones** ampliando sus capacidades al dar a los LLMs **acceso a herramientas** y **conocimiento**.

Desglosemos esta definición en partes más pequeñas:

- **Sistema** - Es importante pensar en los agentes no solo como un componente único sino como un sistema de muchos componentes. A nivel básico, los componentes de un Agente de IA son:
  - **Entorno** - El espacio definido donde opera el Agente de IA. Por ejemplo, si tuviéramos un agente de reservas de viaje, el entorno podría ser el sistema de reservas de viajes que el agente de IA utiliza para completar tareas.
  - **Sensores** - Los entornos tienen información y proporcionan retroalimentación. Los Agentes de IA usan sensores para recopilar e interpretar esta información sobre el estado actual del entorno. En el ejemplo del Agente de Reservas de Viaje, el sistema de reservas puede proporcionar información como la disponibilidad de hoteles o los precios de los vuelos.
  - **Actuadores** - Una vez que el Agente de IA recibe el estado actual del entorno, para la tarea actual el agente determina qué acción realizar para cambiar el entorno. Para el agente de reservas de viaje, podría ser reservar una habitación disponible para el usuario.

![¿Qué son los Agentes de IA?](../../../translated_images/es/what-are-ai-agents.1ec8c4d548af601a.webp)

**Modelos de Lenguaje a Gran Escala** - El concepto de agentes existía antes de la creación de los LLMs. La ventaja de construir Agentes de IA con LLMs es su capacidad para interpretar el lenguaje humano y los datos. Esta habilidad permite a los LLMs interpretar la información del entorno y definir un plan para cambiar el entorno.

**Realizar Acciones** - Fuera de los sistemas de Agentes de IA, los LLMs están limitados a situaciones donde la acción es generar contenido o información basándose en el prompt del usuario. Dentro de los sistemas de Agentes de IA, los LLMs pueden lograr tareas interpretando la solicitud del usuario y usando las herramientas disponibles en su entorno.

**Acceso a Herramientas** - Qué herramientas tiene acceso el LLM está definido por 1) el entorno en el que opera y 2) el desarrollador del Agente de IA. En nuestro ejemplo del agente de viajes, las herramientas del agente están limitadas por las operaciones disponibles en el sistema de reservas, y/o el desarrollador puede limitar el acceso del agente a herramientas relacionadas con vuelos.

**Memoria+Conocimiento** - La memoria puede ser a corto plazo en el contexto de la conversación entre el usuario y el agente. A largo plazo, fuera de la información proporcionada por el entorno, los Agentes de IA también pueden recuperar conocimiento de otros sistemas, servicios, herramientas e incluso otros agentes. En el ejemplo del agente de viajes, este conocimiento podría ser la información sobre las preferencias de viaje del usuario ubicada en una base de datos de clientes.

### Los diferentes tipos de agentes

Ahora que tenemos una definición general de Agentes de IA, veamos algunos tipos específicos de agentes y cómo se aplicarían a un agente de reservas de viaje.

| **Tipo de agente**                | **Descripción**                                                                                                                       | **Ejemplo**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Agentes de Reflejo Simples**      | Realizan acciones inmediatas basadas en reglas predefinidas.                                                                                  | El agente de viajes interpreta el contexto del correo electrónico y reenvía quejas de viaje al servicio de atención al cliente.                                                                                                                          |
| **Agentes de Reflejo Basados en Modelo** | Realizan acciones basadas en un modelo del mundo y cambios en ese modelo.                                                              | El agente de viajes prioriza rutas con cambios significativos de precio basándose en el acceso a datos históricos de precios.                                                                                                             |
| **Agentes Orientados a Objetivos**         | Crean planes para lograr objetivos específicos interpretando el objetivo y determinando acciones para alcanzarlo.                                  | El agente de viajes reserva un trayecto determinando los arreglos de viaje necesarios (coche, transporte público, vuelos) desde la ubicación actual hasta el destino.                                                                                |
| **Agentes Basados en Utilidad**      | Consideran preferencias y ponderan compensaciones numéricamente para determinar cómo lograr objetivos.                                               | El agente de viajes maximiza la utilidad sopesando conveniencia frente a costo al reservar el viaje.                                                                                                                                          |
| **Agentes de Aprendizaje**           | Mejoran con el tiempo respondiendo a la retroalimentación y ajustando las acciones en consecuencia.                                                        | El agente de viajes mejora usando la retroalimentación de los clientes de encuestas posteriores al viaje para hacer ajustes en futuras reservas.                                                                                                               |
| **Agentes Jerárquicos**       | Presentan múltiples agentes en un sistema por niveles, con agentes de nivel superior dividiendo tareas en subtareas para que agentes de nivel inferior las completen. | El agente de viajes cancela un viaje dividiendo la tarea en subtareas (por ejemplo, cancelar reservas específicas) y haciendo que agentes de nivel inferior las completen, informando de vuelta al agente de nivel superior.                                     |
| **Sistemas Multi-Agente (MAS)** | Los agentes completan tareas de forma independiente, ya sea de manera cooperativa o competitiva.                                                           | Cooperativo: Varios agentes reservan servicios de viaje específicos como hoteles, vuelos y entretenimiento. Competitivo: Varios agentes gestionan y compiten por un calendario de reservas hoteleras compartido para alojar a clientes en el hotel. |

## Cuándo usar Agentes de IA

En la sección anterior, usamos el caso de uso del Agente de Viajes para explicar cómo los diferentes tipos de agentes pueden usarse en distintos escenarios de reserva de viajes. Continuaremos usando esta aplicación a lo largo del curso.

Veamos los tipos de casos de uso para los que los Agentes de IA son más adecuados:

![¿Cuándo usar Agentes de IA?](../../../translated_images/es/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Problemas Abiertos** - permitir que el LLM determine los pasos necesarios para completar una tarea porque no siempre se puede codificar rigidamente en un flujo de trabajo.
- **Procesos de Múltiples Pasos** - tareas que requieren un nivel de complejidad en el que el Agente de IA necesita usar herramientas o información a lo largo de múltiples interacciones en lugar de una sola recuperación.  
- **Mejora con el Tiempo** - tareas donde el agente puede mejorar con el tiempo al recibir retroalimentación ya sea de su entorno o de los usuarios para proporcionar mayor utilidad.

Cubrimos más consideraciones sobre el uso de Agentes de IA en la lección Construyendo Agentes de IA Confiables.

## Fundamentos de Soluciones Agentivas

### Desarrollo de Agentes

El primer paso al diseñar un sistema de Agente de IA es definir las herramientas, acciones y comportamientos. En este curso, nos enfocamos en usar el **Azure AI Agent Service** para definir nuestros Agentes. Ofrece características como:

- Selección de modelos abiertos como OpenAI, Mistral y Llama
- Uso de datos licenciados a través de proveedores como Tripadvisor
- Uso de herramientas estándar OpenAPI 3.0

### Patrones Agentivos

La comunicación con los LLMs se realiza mediante prompts. Dada la naturaleza semiautónoma de los Agentes de IA, no siempre es posible o necesario volver a generar prompts manualmente al LLM después de un cambio en el entorno. Usamos **Patrones Agentivos** que nos permiten indicarle al LLM en múltiples pasos de una manera más escalable.

Este curso está dividido en algunos de los patrones agentivos más populares en la actualidad.

### Marcos Agentivos

Los marcos agentivos permiten a los desarrolladores implementar patrones agentivos mediante código. Estos frameworks ofrecen plantillas, complementos y herramientas para una mejor colaboración entre agentes. Estos beneficios proporcionan capacidades para una mejor observabilidad y resolución de problemas de los sistemas de Agentes de IA.

En este curso, exploraremos el framework basado en investigación AutoGen y el framework listo para producción Agent de Semantic Kernel.

## Ejemplos de Código

- Python: [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## ¿Tienes más preguntas sobre los Agentes de IA?

Únete al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para reunirte con otros estudiantes, asistir a horas de oficina y resolver tus preguntas sobre Agentes de IA.

## Lección Anterior

[Configuración del curso](../00-course-setup/README.md)

## Siguiente Lección

[Explorando marcos agentivos](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Descargo de responsabilidad:
Este documento ha sido traducido utilizando el servicio de traducción por IA Co-op Translator (https://github.com/Azure/co-op-translator). Aunque nos esforzamos por la precisión, tenga en cuenta que las traducciones automáticas pueden contener errores o imprecisiones. El documento original en su idioma debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por traductores humanos. No nos hacemos responsables de malentendidos o interpretaciones erróneas que puedan surgir del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->