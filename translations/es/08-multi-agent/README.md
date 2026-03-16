[![Multi-Agente Diseño](../../../translated_images/es/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Haz clic en la imagen de arriba para ver el video de esta lección)_

# Patrones de diseño multi-agente

Tan pronto como comiences a trabajar en un proyecto que involucre múltiples agentes, necesitarás considerar el patrón de diseño multi-agente. Sin embargo, puede que no sea inmediatamente claro cuándo cambiar a multi-agentes y cuáles son las ventajas.

## Introducción

En esta lección, buscamos responder las siguientes preguntas:

- ¿Cuáles son los escenarios donde los multi-agentes son aplicables?
- ¿Cuáles son las ventajas de usar multi-agentes en lugar de un solo agente haciendo múltiples tareas?
- ¿Cuáles son los componentes básicos para implementar el patrón de diseño multi-agente?
- ¿Cómo tenemos visibilidad de cómo los múltiples agentes están interactuando entre sí?

## Objetivos de aprendizaje

Después de esta lección, deberías ser capaz de:

- Identificar escenarios donde los multi-agentes son aplicables
- Reconocer las ventajas de usar multi-agentes sobre un agente singular.
- Comprender los componentes básicos para implementar el patrón de diseño multi-agente.

¿Cuál es el panorama general?

*Los multi-agentes son un patrón de diseño que permite que múltiples agentes trabajen juntos para lograr un objetivo común*.

Este patrón se usa ampliamente en varios campos, incluyendo robótica, sistemas autónomos e informática distribuida.

## Escenarios donde los multi-agentes son aplicables

Entonces, ¿qué escenarios son un buen caso de uso para usar multi-agentes? La respuesta es que hay muchos escenarios donde emplear múltiples agentes es beneficioso, especialmente en los siguientes casos:

- **Grandes cargas de trabajo**: Las grandes cargas de trabajo pueden dividirse en tareas más pequeñas y asignarse a diferentes agentes, permitiendo un procesamiento paralelo y una finalización más rápida. Un ejemplo de esto es el caso de una gran tarea de procesamiento de datos.
- **Tareas complejas**: Las tareas complejas, como las grandes cargas de trabajo, pueden dividirse en subtareas más pequeñas y asignarse a diferentes agentes, cada uno especializado en un aspecto específico de la tarea. Un buen ejemplo es en el caso de vehículos autónomos donde diferentes agentes manejan la navegación, detección de obstáculos y comunicación con otros vehículos.
- **Diversidad de experiencia**: Diferentes agentes pueden tener experiencia diversa, permitiéndoles manejar diferentes aspectos de una tarea de manera más efectiva que un solo agente. Para este caso, un buen ejemplo es en el ámbito de la salud donde los agentes pueden gestionar diagnósticos, planes de tratamiento y monitoreo de pacientes.

## Ventajas de usar multi-agentes sobre un agente singular

Un sistema con un solo agente podría funcionar bien para tareas simples, pero para tareas más complejas, usar múltiples agentes puede proporcionar varias ventajas:

- **Especialización**: Cada agente puede estar especializado para una tarea específica. La falta de especialización en un solo agente significa que tienes un agente que puede hacer de todo pero podría confundirse sobre qué hacer cuando se enfrenta a una tarea compleja. Por ejemplo, podría terminar haciendo una tarea para la que no está mejor capacitado.
- **Escalabilidad**: Es más fácil escalar sistemas agregando más agentes en lugar de sobrecargar a un solo agente.
- **Tolerancia a fallos**: Si un agente falla, otros pueden continuar funcionando, asegurando la confiabilidad del sistema.

Tomemos un ejemplo, vamos a reservar un viaje para un usuario. Un sistema de agente único tendría que manejar todos los aspectos del proceso de reserva del viaje, desde encontrar vuelos hasta reservar hoteles y autos de alquiler. Para lograr esto con un solo agente, el agente necesitaría tener herramientas para manejar todas estas tareas. Esto podría llevar a un sistema complejo y monolítico que es difícil de mantener y escalar. Un sistema multi-agente, por otro lado, podría tener diferentes agentes especializados en encontrar vuelos, reservar hoteles y autos de alquiler. Esto haría que el sistema sea más modular, más fácil de mantener y escalable.

Compáralo con una agencia de viajes administrada como una tienda familiar versus una agencia de viajes administrada como una franquicia. La tienda familiar tendría un solo agente manejando todos los aspectos del proceso de reserva del viaje, mientras que la franquicia tendría diferentes agentes manejando diferentes aspectos del proceso de reserva del viaje.

## Componentes básicos para implementar el patrón de diseño multi-agente

Antes de que puedas implementar el patrón de diseño multi-agente, necesitas entender los componentes que conforman el patrón.

Hagamos esto más concreto mirando nuevamente el ejemplo de reservar un viaje para un usuario. En este caso, los componentes incluirían:

- **Comunicación entre agentes**: Los agentes para encontrar vuelos, reservar hoteles y autos de alquiler necesitan comunicarse y compartir información sobre las preferencias y restricciones del usuario. Debes decidir los protocolos y métodos para esta comunicación. Esto significa concretamente que el agente para encontrar vuelos necesita comunicarse con el agente para reservar hoteles para asegurar que el hotel esté reservado para las mismas fechas que el vuelo. Eso quiere decir que los agentes necesitan compartir información sobre las fechas de viaje del usuario, lo que implica que debes decidir *qué agentes están compartiendo información y cómo la están compartiendo*.
- **Mecanismos de coordinación**: Los agentes necesitan coordinar sus acciones para asegurar que las preferencias y restricciones del usuario se cumplan. Una preferencia del usuario podría ser que quiera un hotel cerca del aeropuerto mientras que una restricción podría ser que los autos de alquiler solo estén disponibles en el aeropuerto. Esto significa que el agente para reservar hoteles necesita coordinarse con el agente para reservar autos de alquiler para asegurar que las preferencias y restricciones del usuario se cumplan. Esto significa que debes decidir *cómo los agentes están coordinando sus acciones*.
- **Arquitectura del agente**: Los agentes necesitan tener una estructura interna para tomar decisiones y aprender de sus interacciones con el usuario. Esto significa que el agente para encontrar vuelos necesita tener la estructura interna para tomar decisiones sobre qué vuelos recomendar al usuario. Esto implica que debes decidir *cómo los agentes toman decisiones y aprenden de sus interacciones con el usuario*. Ejemplos de cómo un agente aprende y mejora podrían ser que el agente para encontrar vuelos podría usar un modelo de aprendizaje automático para recomendar vuelos al usuario basado en sus preferencias pasadas.
- **Visibilidad en las interacciones multi-agente**: Necesitas tener visibilidad de cómo los múltiples agentes están interactuando entre sí. Esto significa que necesitas herramientas y técnicas para rastrear las actividades e interacciones de los agentes. Esto podría ser en forma de herramientas de registro y monitoreo, herramientas de visualización y métricas de desempeño.
- **Patrones multi-agente**: Existen diferentes patrones para implementar sistemas multi-agente, tales como arquitecturas centralizadas, descentralizadas e híbridas. Debes decidir el patrón que mejor se adapte a tu caso de uso.
- **Humano en el ciclo**: En la mayoría de los casos, tendrás un humano en el ciclo y necesitas instruir a los agentes cuándo solicitar intervención humana. Esto podría ser en forma de un usuario pidiendo un hotel o vuelo específico que los agentes no hayan recomendado o pidiendo confirmación antes de reservar un vuelo o hotel.

## Visibilidad en las interacciones multi-agente

Es importante que tengas visibilidad sobre cómo los múltiples agentes están interactuando entre sí. Esta visibilidad es esencial para depurar, optimizar y asegurar la efectividad general del sistema. Para lograr esto, necesitas herramientas y técnicas para rastrear las actividades e interacciones de los agentes. Esto podría ser en forma de herramientas de registro y monitoreo, herramientas de visualización y métricas de desempeño.

Por ejemplo, en el caso de reservar un viaje para un usuario, podrías tener un panel de control que muestre el estado de cada agente, las preferencias y restricciones del usuario, y las interacciones entre agentes. Este panel podría mostrar las fechas de viaje del usuario, los vuelos recomendados por el agente de vuelos, los hoteles recomendados por el agente de hoteles, y los autos de alquiler recomendados por el agente de autos de alquiler. Esto te daría una vista clara de cómo los agentes están interactuando entre sí y si las preferencias y restricciones del usuario se están cumpliendo.

Veamos cada uno de estos aspectos con más detalle.

- **Herramientas de registro y monitoreo**: Quieres que se realice el registro de cada acción tomada por un agente. Una entrada de registro podría almacenar información sobre el agente que tomó la acción, la acción tomada, el momento en que se tomó la acción, y el resultado de la acción. Esta información luego puede usarse para depurar, optimizar y más.

- **Herramientas de visualización**: Las herramientas de visualización pueden ayudarte a ver las interacciones entre los agentes de una manera más intuitiva. Por ejemplo, podrías tener un gráfico que muestre el flujo de información entre agentes. Esto podría ayudarte a identificar cuellos de botella, ineficiencias y otros problemas en el sistema.

- **Métricas de desempeño**: Las métricas de desempeño pueden ayudarte a rastrear la efectividad del sistema multi-agente. Por ejemplo, podrías rastrear el tiempo tomado para completar una tarea, el número de tareas completadas por unidad de tiempo y la precisión de las recomendaciones hechas por los agentes. Esta información puede ayudarte a identificar áreas de mejora y optimizar el sistema.

## Patrones multi-agente

Vamos a profundizar en algunos patrones concretos que podemos usar para crear aplicaciones multi-agente. Aquí hay algunos patrones interesantes que vale la pena considerar:

### Chat grupal

Este patrón es útil cuando quieres crear una aplicación de chat grupal donde múltiples agentes puedan comunicarse entre sí. Los casos típicos de uso para este patrón incluyen colaboración en equipo, soporte al cliente y redes sociales.

En este patrón, cada agente representa a un usuario en el chat grupal, y los mensajes se intercambian entre agentes usando un protocolo de mensajería. Los agentes pueden enviar mensajes al chat grupal, recibir mensajes del chat grupal y responder a mensajes de otros agentes.

Este patrón puede implementarse usando una arquitectura centralizada donde todos los mensajes se enrutan a través de un servidor central, o una arquitectura descentralizada donde los mensajes se intercambian directamente.

![Chat grupal](../../../translated_images/es/multi-agent-group-chat.ec10f4cde556babd.webp)

### Transferencia de tareas

Este patrón es útil cuando quieres crear una aplicación donde múltiples agentes puedan transferirse tareas entre sí.

Los casos típicos de uso para este patrón incluyen soporte al cliente, gestión de tareas y automatización de flujos de trabajo.

En este patrón, cada agente representa una tarea o un paso en un flujo de trabajo, y los agentes pueden transferir tareas a otros agentes basándose en reglas predefinidas.

![Transferencia de tareas](../../../translated_images/es/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Filtrado colaborativo

Este patrón es útil cuando quieres crear una aplicación donde múltiples agentes puedan colaborar para hacer recomendaciones a los usuarios.

La razón por la que querrías que múltiples agentes colaboren es porque cada agente puede tener experiencia diferente y puede contribuir al proceso de recomendación de distintas maneras.

Tomemos un ejemplo donde un usuario quiere una recomendación sobre la mejor acción para comprar en el mercado de valores.

- **Experto en industria**: Un agente podría ser un experto en una industria específica.
- **Análisis técnico**: Otro agente podría ser un experto en análisis técnico.
- **Análisis fundamental**: y otro agente podría ser un experto en análisis fundamental. Colaborando, estos agentes pueden ofrecer una recomendación más completa al usuario.

![Recomendación](../../../translated_images/es/multi-agent-filtering.d959cb129dc9f608.webp)

## Escenario: Proceso de reembolso

Considera un escenario donde un cliente está tratando de obtener un reembolso por un producto, puede haber bastantes agentes involucrados en este proceso pero dividámoslo entre agentes específicos para este proceso y agentes generales que pueden usarse en otros procesos.

**Agentes específicos para el proceso de reembolso**:

A continuación se listan algunos agentes que podrían estar involucrados en el proceso de reembolso:

- **Agente de cliente**: Este agente representa al cliente y es responsable de iniciar el proceso de reembolso.
- **Agente de vendedor**: Este agente representa al vendedor y es responsable de procesar el reembolso.
- **Agente de pagos**: Este agente representa el proceso de pago y es responsable de reembolsar el pago del cliente.
- **Agente de resolución**: Este agente representa el proceso de resolución y es responsable de resolver cualquier problema que surja durante el proceso de reembolso.
- **Agente de cumplimiento**: Este agente representa el proceso de cumplimiento y es responsable de asegurar que el proceso de reembolso cumpla con regulaciones y políticas.

**Agentes generales**:

Estos agentes pueden usarse en otras partes de tu negocio.

- **Agente de envíos**: Este agente representa el proceso de envío y es responsable de enviar el producto de vuelta al vendedor. Este agente puede usarse tanto para el proceso de reembolso como para el envío general de un producto por ejemplo.
- **Agente de retroalimentación**: Este agente representa el proceso de retroalimentación y es responsable de recopilar retroalimentación del cliente. La retroalimentación puede darse en cualquier momento y no solo durante el proceso de reembolso.
- **Agente de escalamiento**: Este agente representa el proceso de escalamiento y es responsable de escalar problemas a un nivel superior de soporte. Puedes usar este tipo de agente para cualquier proceso donde necesites escalar un problema.
- **Agente de notificaciones**: Este agente representa el proceso de notificaciones y es responsable de enviar notificaciones al cliente en varias etapas del proceso de reembolso.
- **Agente de análisis**: Este agente representa el proceso de análisis y es responsable de analizar datos relacionados con el proceso de reembolso.
- **Agente de auditoría**: Este agente representa el proceso de auditoría y es responsable de auditar el proceso de reembolso para asegurar que se está realizando correctamente.
- **Agente de reportes**: Este agente representa el proceso de reportes y es responsable de generar informes sobre el proceso de reembolso.
- **Agente de conocimiento**: Este agente representa el proceso de conocimiento y es responsable de mantener una base de conocimiento de información relacionada con el proceso de reembolso. Este agente podría tener conocimiento tanto sobre reembolsos como sobre otras partes de tu negocio.
- **Agente de seguridad**: Este agente representa el proceso de seguridad y es responsable de asegurar la seguridad del proceso de reembolso.
- **Agente de calidad**: Este agente representa el proceso de calidad y es responsable de asegurar la calidad del proceso de reembolso.

Hay bastantes agentes listados anteriormente tanto para el proceso específico de reembolso como para los agentes generales que pueden usarse en otras partes de tu negocio. Ojalá esto te dé una idea de cómo puedes decidir qué agentes usar en tu sistema multi-agente.

## Tarea

Diseña un sistema multi-agente para un proceso de soporte al cliente. Identifica los agentes involucrados en el proceso, sus roles y responsabilidades, y cómo interactúan entre sí. Considera tanto agentes específicos para el proceso de soporte al cliente como agentes generales que pueden usarse en otras partes de tu negocio.
> Piénsalo antes de leer la siguiente solución, es posible que necesites más agentes de los que crees.

> CONSEJO: Piensa en las diferentes etapas del proceso de atención al cliente y también considera los agentes necesarios para cualquier sistema.

## Solución

[Solución](./solution/solution.md)

## Comprobaciones de conocimiento

Pregunta: ¿Cuándo deberías considerar usar múltiples agentes?

- [ ] A1: Cuando tienes una carga de trabajo pequeña y una tarea sencilla.
- [ ] A2: Cuando tienes una gran carga de trabajo
- [ ] A3: Cuando tienes una tarea sencilla.

[Cuestionario de solución](./solution/solution-quiz.md)

## Resumen

En esta lección, hemos analizado el patrón de diseño de múltiples agentes, incluidos los escenarios en los que los múltiples agentes son aplicables, las ventajas de usar múltiples agentes en lugar de un solo agente, los componentes básicos para implementar el patrón de diseño de múltiples agentes y cómo tener visibilidad de cómo interactúan entre sí los múltiples agentes.

### ¿Tienes más preguntas sobre el patrón de diseño de múltiples agentes?

Únete al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para encontrarte con otros estudiantes, asistir a las horas de oficina y resolver tus dudas sobre Agentes de IA.

## Recursos adicionales

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Patrones de diseño AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Patrones de diseño agenticos</a>


## Lección anterior

[Planificación del diseño](../07-planning-design/README.md)

## Próxima lección

[Metacognición en Agentes de IA](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:
Este documento ha sido traducido utilizando el servicio de traducción automática [Co-op Translator](https://github.com/Azure/co-op-translator). Aunque nos esforzamos por la precisión, tenga en cuenta que las traducciones automatizadas pueden contener errores o inexactitudes. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda la traducción profesional realizada por un humano. No nos hacemos responsables de malentendidos o interpretaciones erróneas derivadas del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->