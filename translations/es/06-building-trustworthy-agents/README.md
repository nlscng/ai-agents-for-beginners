[![Agentes de IA confiables](../../../translated_images/es/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Haz clic en la imagen de arriba para ver el video de esta lección)_

# Construyendo agentes de IA confiables

## Introducción

Esta lección cubrirá:

- Cómo construir y desplegar agentes de IA seguros y efectivos
- Consideraciones importantes de seguridad al desarrollar agentes de IA.
- Cómo mantener la privacidad de los datos y de los usuarios al desarrollar agentes de IA.

## Objetivos de aprendizaje

Después de completar esta lección, sabrás cómo:

- Identificar y mitigar riesgos al crear agentes de IA.
- Implementar medidas de seguridad para asegurar que los datos y el acceso se gestionen adecuadamente.
- Crear agentes de IA que mantengan la privacidad de los datos y proporcionen una experiencia de usuario de calidad.

## Seguridad

Primero veamos cómo construir aplicaciones agenticas seguras. Seguridad significa que el agente de IA se comporta como se ha diseñado. Como constructores de aplicaciones agenticas, contamos con métodos y herramientas para maximizar la seguridad:

### Construyendo un marco de mensajes del sistema

Si alguna vez has construido una aplicación de IA usando Modelos de Lenguaje Grandes (LLMs), sabes la importancia de diseñar un prompt o mensaje del sistema robusto. Estos prompts establecen las meta reglas, instrucciones y directrices sobre cómo el LLM interactuará con el usuario y con los datos.

Para los agentes de IA, el prompt del sistema es incluso más importante, ya que los agentes necesitarán instrucciones altamente específicas para completar las tareas que hemos diseñado para ellos.

Para crear prompts de sistema escalables, podemos usar un marco de mensajes del sistema para construir uno o más agentes en nuestra aplicación:

![Construyendo un marco de mensajes del sistema](../../../translated_images/es/system-message-framework.3a97368c92d11d68.webp)

#### Paso 1: Crear un Meta Mensaje del Sistema

El meta prompt será usado por un LLM para generar los prompts del sistema para los agentes que creamos. Lo diseñamos como una plantilla para que podamos crear múltiples agentes de manera eficiente si es necesario.

Aquí hay un ejemplo de un meta mensaje del sistema que le daríamos al LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Paso 2: Crear un prompt básico

El siguiente paso es crear un prompt básico para describir al agente de IA. Debes incluir el rol del agente, las tareas que completará, y cualquier otra responsabilidad del agente.

Aquí hay un ejemplo:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Paso 3: Proporcionar el mensaje del sistema básico al LLM

Ahora podemos optimizar este mensaje de sistema proporcionando el meta mensaje del sistema como el mensaje del sistema y nuestro mensaje básico del sistema.

Esto producirá un mensaje del sistema mejor diseñado para guiar a nuestros agentes de IA:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Paso 4: Iterar y mejorar

El valor de este marco de mensajes del sistema es poder escalar la creación de mensajes de sistema para múltiples agentes más fácilmente, así como mejorar tus mensajes de sistema con el tiempo. Rara vez tendrás un mensaje de sistema que funcione a la perfección la primera vez para tu caso de uso completo. Poder hacer pequeños ajustes y mejoras cambiando el mensaje básico del sistema y procesándolo a través del sistema te permitirá comparar y evaluar resultados.

## Comprendiendo las amenazas

Para construir agentes de IA confiables, es importante entender y mitigar los riesgos y amenazas a tu agente de IA. Veamos solo algunas de las diferentes amenazas a los agentes de IA y cómo puedes planificar y prepararte mejor para ellas.

![Comprendiendo las amenazas](../../../translated_images/es/understanding-threats.89edeada8a97fc0f.webp)

### Tarea e instrucción

**Descripción:** Los atacantes intentan cambiar las instrucciones o metas del agente de IA mediante prompts o manipulando las entradas.

**Mitigación**: Ejecutar verificaciones de validación y filtros de entrada para detectar prompts potencialmente peligrosos antes de que sean procesados por el agente de IA. Dado que estos ataques requieren normalmente interacción frecuente con el agente, limitar el número de turnos en una conversación es otra forma de prevenir este tipo de ataques.

### Acceso a sistemas críticos

**Descripción:** Si un agente de IA tiene acceso a sistemas y servicios que almacenan datos sensibles, los atacantes pueden comprometer la comunicación entre el agente y estos servicios. Estos pueden ser ataques directos o intentos indirectos de obtener información sobre estos sistemas a través del agente.

**Mitigación:** Los agentes de IA deben tener acceso a sistemas sólo cuando sea necesario para prevenir este tipo de ataques. La comunicación entre el agente y el sistema también debe ser segura. Implementar autenticación y control de acceso es otra manera de proteger esta información.

### Sobrecarga de recursos y servicios

**Descripción:** Los agentes de IA pueden acceder a diferentes herramientas y servicios para completar tareas. Los atacantes pueden usar esta habilidad para atacar estos servicios enviando un alto volumen de solicitudes a través del agente de IA, lo cual puede resultar en fallas del sistema o altos costos.

**Mitigación:** Implementar políticas para limitar el número de solicitudes que un agente de IA puede hacer a un servicio. Limitar el número de turnos en la conversación y las solicitudes a tu agente de IA es otra manera de prevenir este tipo de ataques.

### Envenenamiento de base de conocimiento

**Descripción:** Este tipo de ataque no apunta directamente al agente de IA, sino a la base de conocimiento y otros servicios que el agente usará. Esto podría involucrar corromper los datos o información que el agente utilizará para completar una tarea, llevando a respuestas sesgadas o no deseadas para el usuario.

**Mitigación:** Realizar verificaciones regulares de los datos que el agente de IA usará en sus flujos de trabajo. Asegurar que el acceso a estos datos sea seguro y solo modificado por personas de confianza para evitar este tipo de ataque.

### Errores en cascada

**Descripción:** Los agentes de IA acceden a diversas herramientas y servicios para completar tareas. Los errores causados por atacantes pueden conducir a fallos de otros sistemas conectados al agente, haciendo que el ataque se vuelva más generalizado y más difícil de diagnosticar.

**Mitigación**: Un método para evitar esto es que el agente de IA opere en un entorno limitado, como ejecutar tareas en un contenedor Docker, para evitar ataques directos al sistema. Crear mecanismos de respaldo y lógica de reintentos cuando ciertos sistemas respondan con un error es otra forma de prevenir fallas mayores en el sistema.

## Humano en el ciclo

Otra forma efectiva de construir sistemas de agentes de IA confiables es usando un Humano en el ciclo. Esto crea un flujo donde los usuarios pueden proporcionar retroalimentación a los agentes durante la ejecución. Los usuarios esencialmente actúan como agentes en un sistema multiagente proporcionando aprobación o deteniendo el proceso en ejecución.

![Humano en el ciclo](../../../translated_images/es/human-in-the-loop.5f0068a678f62f4f.webp)

Aquí hay un fragmento de código usando AutoGen para mostrar cómo se implementa este concepto:

```python

# Crear los agentes.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Usar input() para obtener la entrada del usuario desde la consola.

# Crear la condición de terminación que finalizará la conversación cuando el usuario diga "APPROVE".
termination = TextMentionTermination("APPROVE")

# Crear el equipo.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Ejecutar la conversación y transmitirla a la consola.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Usar asyncio.run(...) al ejecutar en un script.
await Console(stream)

```

## Conclusión

Construir agentes de IA confiables requiere un diseño cuidadoso, medidas de seguridad robustas y una iteración continua. Al implementar sistemas estructurados de meta prompting, comprender las amenazas potenciales y aplicar estrategias de mitigación, los desarrolladores pueden crear agentes de IA que sean seguros y efectivos. Además, incorporar un enfoque de humano en el ciclo garantiza que los agentes de IA permanezcan alineados con las necesidades del usuario mientras se minimizan los riesgos. Conforme la IA continúa evolucionando, mantener una postura proactiva respecto a la seguridad, privacidad y consideraciones éticas será clave para fomentar la confianza y confiabilidad en los sistemas impulsados por IA.

### ¿Tienes más preguntas sobre cómo construir agentes de IA confiables?

Únete al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para conocer a otros aprendices, asistir a horas de oficina y obtener respuestas a tus preguntas sobre agentes de IA.

## Recursos adicionales

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Visión general de IA responsable</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Evaluación de modelos generativos de IA y aplicaciones de IA</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Mensajes del sistema de seguridad</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Plantilla de evaluación de riesgos</a>

## Lección anterior

[Agentic RAG](../05-agentic-rag/README.md)

## Próxima lección

[Patrón de diseño de planificación](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso legal**:
Este documento ha sido traducido utilizando el servicio de traducción automática [Co-op Translator](https://github.com/Azure/co-op-translator). Aunque nos esforzamos por la precisión, tenga en cuenta que las traducciones automáticas pueden contener errores o inexactitudes. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por humanos. No nos hacemos responsables de cualquier malentendido o interpretación errónea que surja del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->