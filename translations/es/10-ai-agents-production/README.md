# Agentes de IA en Producción: Observabilidad y Evaluación

[![Agentes de IA en Producción](../../../translated_images/es/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

A medida que los agentes de IA pasan de prototipos experimentales a aplicaciones del mundo real, la capacidad de comprender su comportamiento, supervisar su rendimiento y evaluar sistemáticamente sus salidas se vuelve importante.

## Objetivos de aprendizaje

Después de completar esta lección, sabrás cómo/entenderás:
- Conceptos clave de observabilidad y evaluación de agentes
- Técnicas para mejorar el rendimiento, los costos y la efectividad de los agentes
- Qué y cómo evaluar sistemáticamente tus agentes de IA
- Cómo controlar los costos al desplegar agentes de IA en producción
- Cómo instrumentar agentes creados con AutoGen

El objetivo es equiparte con el conocimiento para transformar tus agentes "caja negra" en sistemas transparentes, manejables y fiables.

_**Nota:** Es importante desplegar Agentes de IA que sean seguros y confiables. Consulta también la lección [Building Trustworthy AI Agents](./06-building-trustworthy-agents/README.md)._

## Trazas y spans

Las herramientas de observabilidad como [Langfuse](https://langfuse.com/) o [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) suelen representar las ejecuciones de agentes como trazas y spans.

- **Trace** representa una tarea completa del agente desde el inicio hasta el final (como manejar una consulta de usuario).
- **Spans** son pasos individuales dentro de la traza (como llamar a un modelo de lenguaje o recuperar datos).

![Árbol de trazas en Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Sin observabilidad, un agente de IA puede sentirse como una "caja negra": su estado interno y su razonamiento son opacos, lo que dificulta diagnosticar problemas u optimizar el rendimiento. Con observabilidad, los agentes se convierten en "cajas de cristal", ofreciendo transparencia que es vital para generar confianza y asegurar que operen según lo previsto. 

## Por qué la observabilidad importa en entornos de producción

La transición de agentes de IA a entornos de producción introduce un nuevo conjunto de desafíos y requisitos. La observabilidad deja de ser algo "agradable de tener" y se convierte en una capacidad crítica:

*   **Depuración y análisis de causa raíz**: Cuando un agente falla o produce una salida inesperada, las herramientas de observabilidad proporcionan las trazas necesarias para localizar la fuente del error. Esto es especialmente importante en agentes complejos que pueden implicar múltiples llamadas a LLM, interacciones con herramientas y lógica condicional.
*   **Gestión de latencia y costos**: Los agentes de IA a menudo dependen de LLMs y otras API externas que se facturan por token o por llamada. La observabilidad permite un seguimiento preciso de estas llamadas, ayudando a identificar operaciones que son excesivamente lentas o caras. Esto permite a los equipos optimizar prompts, seleccionar modelos más eficientes o rediseñar flujos de trabajo para gestionar los costos operativos y asegurar una buena experiencia de usuario.
*   **Confianza, seguridad y cumplimiento**: En muchas aplicaciones, es importante asegurar que los agentes se comporten de manera segura y ética. La observabilidad proporciona una pista de auditoría de las acciones y decisiones del agente. Esto puede usarse para detectar y mitigar problemas como la inyección de prompts, la generación de contenido dañino o el manejo inadecuado de información de identificación personal (PII). Por ejemplo, puedes revisar trazas para entender por qué un agente proporcionó cierta respuesta o usó una herramienta específica.
*   **Bucles de mejora continua**: Los datos de observabilidad son la base de un proceso de desarrollo iterativo. Al monitorizar cómo se desempeñan los agentes en el mundo real, los equipos pueden identificar áreas de mejora, recopilar datos para el ajuste fino de modelos y validar el impacto de los cambios. Esto crea un bucle de retroalimentación donde las ideas de producción obtenidas a partir de la evaluación en línea informan la experimentación y el refinamiento fuera de línea, llevando a un rendimiento progresivamente mejor del agente.

## Métricas clave para supervisar

Para monitorizar y comprender el comportamiento del agente, debe rastrearse una variedad de métricas y señales. Aunque las métricas específicas pueden variar según el propósito del agente, algunas son universalmente importantes.

Aquí están algunas de las métricas más comunes que las herramientas de observabilidad monitorizan:

**Latencia:** ¿Qué tan rápido responde el agente? Los tiempos de espera largos impactan negativamente la experiencia del usuario. Debes medir la latencia de las tareas y de pasos individuales trazando las ejecuciones del agente. Por ejemplo, un agente que tarda 20 segundos en todas las llamadas al modelo podría acelerarse usando un modelo más rápido o ejecutando las llamadas al modelo en paralelo.

**Costos:** ¿Cuál es el gasto por ejecución del agente? Los agentes de IA dependen de llamadas a LLM facturadas por token o de APIs externas. El uso frecuente de herramientas o múltiples prompts puede aumentar rápidamente los costos. Por ejemplo, si un agente llama a un LLM cinco veces por una mejora marginal de calidad, debes evaluar si el costo se justifica o si podrías reducir el número de llamadas o usar un modelo más barato. La monitorización en tiempo real también puede ayudar a identificar picos inesperados (por ejemplo, bugs que causan bucles excesivos de API).

**Errores de solicitudes:** ¿Cuántas solicitudes falló el agente? Esto puede incluir errores de API o llamadas a herramientas fallidas. Para hacer tu agente más robusto ante estos fallos en producción, puedes configurar alternativas o reintentos. Por ejemplo, si el proveedor de LLM A falla, cambias al proveedor de LLM B como respaldo.

**Retroalimentación del usuario:** Implementar evaluaciones directas de los usuarios proporciona información valiosa. Esto puede incluir valoraciones explícitas (👍pulgar arriba/👎pulgar abajo, ⭐1-5 estrellas) o comentarios textuales. La retroalimentación negativa consistente debe alertarte ya que es una señal de que el agente no está funcionando como se espera. 

**Retroalimentación implícita del usuario:** El comportamiento del usuario ofrece retroalimentación indirecta incluso sin valoraciones explícitas. Esto puede incluir reformulación inmediata de preguntas, consultas repetidas o hacer clic en un botón de reintento. Por ejemplo, si ves que los usuarios preguntan repetidamente lo mismo, es una señal de que el agente no está funcionando como se espera.

**Precisión:** ¿Con qué frecuencia produce el agente salidas correctas o deseables? Las definiciones de precisión varían (por ejemplo, corrección en la resolución de problemas, precisión en la recuperación de información, satisfacción del usuario). El primer paso es definir cómo se ve el éxito para tu agente. Puedes rastrear la precisión mediante comprobaciones automatizadas, puntuaciones de evaluación o etiquetas de finalización de tareas. Por ejemplo, marcar trazas como "succeeded" o "failed". 

**Métricas de evaluación automatizada:** También puedes configurar evaluaciones automáticas. Por ejemplo, puedes usar un LLM para puntuar la salida del agente, p. ej. si es útil, precisa o no. También existen varias bibliotecas de código abierto que te ayudan a puntuar diferentes aspectos del agente. Por ejemplo, [RAGAS](https://docs.ragas.io/) para agentes RAG o [LLM Guard](https://llm-guard.com/) para detectar lenguaje dañino o inyección de prompts. 

En la práctica, una combinación de estas métricas ofrece la mejor cobertura de la salud de un agente de IA. En el [notebook de ejemplo](./code_samples/10_autogen_evaluation.ipynb) de este capítulo, te mostraremos cómo se ven estas métricas en ejemplos reales, pero primero aprenderemos cómo es un flujo de evaluación típico.

## Instrumenta tu agente

Para recopilar datos de trazado, necesitarás instrumentar tu código. El objetivo es instrumentar el código del agente para emitir trazas y métricas que puedan ser capturadas, procesadas y visualizadas por una plataforma de observabilidad.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) se ha consolidado como un estándar de la industria para la observabilidad de LLM. Proporciona un conjunto de APIs, SDKs y herramientas para generar, recopilar y exportar datos de telemetría. 

Hay muchas bibliotecas de instrumentación que envuelven frameworks de agentes existentes y facilitan la exportación de spans de OpenTelemetry a una herramienta de observabilidad. A continuación hay un ejemplo de instrumentación de un agente AutoGen con la biblioteca de instrumentación [OpenLit](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

El [notebook de ejemplo](./code_samples/10_autogen_evaluation.ipynb) en este capítulo demostrará cómo instrumentar tu agente AutoGen.

**Creación manual de spans:** Mientras que las bibliotecas de instrumentación proporcionan una buena base, a menudo hay casos donde se necesita información más detallada o personalizada. Puedes crear spans manualmente para añadir lógica de aplicación personalizada. Más importante aún, pueden enriquecer spans creados automáticamente o manualmente con atributos personalizados (también conocidos como tags o metadata). Estos atributos pueden incluir datos específicos del negocio, cálculos intermedios o cualquier contexto que pueda ser útil para depuración o análisis, como `user_id`, `session_id` o `model_version`.

Ejemplo de creación manual de trazas y spans con el [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3): 

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Evaluación del agente

La observabilidad nos proporciona métricas, pero la evaluación es el proceso de analizar esos datos (y realizar pruebas) para determinar qué tan bien se desempeña un agente de IA y cómo se puede mejorar. En otras palabras, una vez que tienes esas trazas y métricas, ¿cómo las usas para juzgar al agente y tomar decisiones? 

La evaluación regular es importante porque los agentes de IA suelen ser no deterministas y pueden evolucionar (mediante actualizaciones o deriva del comportamiento del modelo): sin evaluación, no sabrías si tu "agente inteligente" realmente está haciendo bien su trabajo o si ha empeorado.

Hay dos categorías de evaluaciones para agentes de IA: **evaluación en línea** y **evaluación offline**. Ambas son valiosas y se complementan entre sí. Normalmente comenzamos con la evaluación offline, ya que es el paso mínimo necesario antes de desplegar cualquier agente.

### Evaluación offline

![Elementos del conjunto de datos en Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

Esto implica evaluar al agente en un entorno controlado, típicamente usando conjuntos de prueba, no consultas de usuarios en vivo. Utilizas conjuntos de datos curados donde sabes cuál es la salida esperada o el comportamiento correcto, y luego ejecutas tu agente sobre ellos. 

Por ejemplo, si construiste un agente para resolver problemas matemáticos de enunciado, podrías tener un [conjunto de prueba](https://huggingface.co/datasets/gsm8k) de 100 problemas con respuestas conocidas. La evaluación offline se realiza a menudo durante el desarrollo (y puede ser parte de pipelines de CI/CD) para comprobar mejoras o proteger contra regresiones. El beneficio es que es **repetible y puedes obtener métricas claras de precisión ya que tienes la verdad de referencia**. También podrías simular consultas de usuarios y medir las respuestas del agente frente a respuestas ideales o usar métricas automatizadas como se describió arriba. 

El desafío clave de la evaluación offline es asegurar que tu conjunto de pruebas sea exhaustivo y permanezca relevante: el agente puede funcionar bien en un conjunto de pruebas fijo pero encontrarse con consultas muy diferentes en producción. Por lo tanto, debes mantener los conjuntos de prueba actualizados con nuevos casos límite y ejemplos que reflejen escenarios del mundo real. Una mezcla de pequeños casos de "smoke test" y conjuntos de evaluación más grandes es útil: conjuntos pequeños para comprobaciones rápidas y más grandes para métricas de rendimiento más amplias.

### Evaluación en línea

![Resumen de métricas de observabilidad](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Esto se refiere a evaluar al agente en un entorno en vivo y del mundo real, es decir, durante el uso real en producción. La evaluación en línea implica monitorizar el rendimiento del agente en interacciones reales de usuarios y analizar los resultados de forma continua. 

Por ejemplo, podrías rastrear tasas de éxito, puntuaciones de satisfacción del usuario u otras métricas en tráfico en vivo. La ventaja de la evaluación en línea es que **captura cosas que podrías no anticipar en un entorno de laboratorio**: puedes observar la deriva del modelo a lo largo del tiempo (si la efectividad del agente se degrada a medida que cambian los patrones de entrada) y detectar consultas o situaciones inesperadas que no estaban en tus datos de prueba. Proporciona una imagen real de cómo se comporta el agente en el entorno real. 

La evaluación en línea a menudo implica recopilar retroalimentación implícita y explícita de los usuarios, como se discutió, y posiblemente ejecutar pruebas en sombras o pruebas A/B (donde una nueva versión del agente se ejecuta en paralelo para comparar con la antigua). El desafío es que puede ser complicado obtener etiquetas o puntuaciones fiables para interacciones en vivo: podrías depender de la retroalimentación del usuario o de métricas downstream (como si el usuario hizo clic en el resultado). 

### Combinando ambas

Las evaluaciones en línea y offline no son mutuamente excluyentes; se complementan mucho entre sí. Las ideas de la monitorización en línea (por ejemplo, nuevos tipos de consultas de usuarios donde el agente rinde mal) pueden usarse para aumentar y mejorar los conjuntos de prueba offline. A la inversa, los agentes que funcionan bien en pruebas offline pueden desplegarse con más confianza y monitorizarse en línea. 

De hecho, muchos equipos adoptan un bucle:

_evaluar offline -> desplegar -> monitorizar online -> recopilar nuevos casos de fallo -> añadir al conjunto de datos offline -> refinar el agente -> repetir_.

## Problemas comunes

Al desplegar agentes de IA en producción, puedes encontrar varios desafíos. Aquí hay algunos problemas comunes y sus posibles soluciones:

| **Issue**    | **Potential Solution**   |
| ------------- | ------------------ |
| AI Agent not performing tasks consistently | - Refina el prompt dado al Agente de IA; sé claro en los objetivos.<br>- Identifica dónde dividir las tareas en subtareas y manejarlo por múltiples agentes puede ayudar. |
| AI Agent running into continuous loops  | - Asegúrate de tener términos y condiciones de terminación claros para que el Agente sepa cuándo detener el proceso.<br>- Para tareas complejas que requieren razonamiento y planificación, usa un modelo más grande que esté especializado en tareas de razonamiento. |
| AI Agent tool calls are not performing well   | - Prueba y valida la salida de la herramienta fuera del sistema del agente.<br>- Refina los parámetros definidos, los prompts y la nomenclatura de las herramientas.  |
| Multi-Agent system not performing consistently | - Refina los prompts dados a cada agente para asegurarte de que sean específicos y distintos entre sí.<br>- Construye un sistema jerárquico usando un agente "enrutador" o controlador para determinar cuál agente es el correcto. |

Muchos de estos problemas pueden identificarse de forma más efectiva con la observabilidad en su lugar. Las trazas y métricas que discutimos anteriormente ayudan a localizar exactamente dónde en el flujo de trabajo del agente ocurren los problemas, haciendo que la depuración y la optimización sean mucho más eficientes.

## Gestión de costos
Aquí hay algunas estrategias para gestionar los costos de desplegar agentes de IA en producción:

**Usar modelos más pequeños:** Los Modelos de Lenguaje Pequeños (SLMs) pueden desempeñarse bien en ciertos casos de uso relacionados con agentes y reducirán significativamente los costos. Como se mencionó anteriormente, construir un sistema de evaluación para determinar y comparar el rendimiento frente a modelos más grandes es la mejor manera de entender qué tan bien se desempeñará un SLM en tu caso de uso. Considera usar SLMs para tareas más simples como clasificación de intenciones o extracción de parámetros, mientras reservas modelos más grandes para razonamientos complejos.

**Usar un modelo enrutador:** Una estrategia similar es usar una diversidad de modelos y tamaños. Puedes usar un LLM/SLM o una función sin servidor para enrutar las solicitudes según su complejidad hacia los modelos más adecuados. Esto también ayudará a reducir costos y a garantizar el rendimiento en las tareas correctas. Por ejemplo, enruta consultas simples a modelos más pequeños y rápidos, y utiliza modelos grandes y costosos solo para tareas de razonamiento complejo.

**Almacenamiento en caché de respuestas:** Identificar solicitudes y tareas comunes y proporcionar las respuestas antes de que pasen por tu sistema de agentes es una buena manera de reducir el volumen de solicitudes similares. Incluso puedes implementar un flujo para identificar cuán similar es una solicitud a tus solicitudes en caché usando modelos de IA más básicos. Esta estrategia puede reducir significativamente los costos para preguntas frecuentes o flujos de trabajo comunes.

## Veamos cómo funciona esto en la práctica

En el [cuaderno de ejemplo de esta sección](./code_samples/10_autogen_evaluation.ipynb), veremos ejemplos de cómo podemos usar herramientas de observabilidad para monitorizar y evaluar nuestro agente.


### ¿Tienes más preguntas sobre agentes de IA en producción?

Únete al [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para reunirte con otros estudiantes, asistir a horas de oficina y obtener respuestas a tus preguntas sobre agentes de IA.

## Lección anterior

[Patrón de diseño de metacognición](../09-metacognition/README.md)

## Siguiente lección

[Protocolos para agentes](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Descargo de responsabilidad:
Este documento ha sido traducido utilizando el servicio de traducción por IA [Co-op Translator](https://github.com/Azure/co-op-translator). Si bien nos esforzamos por la exactitud, tenga en cuenta que las traducciones automatizadas pueden contener errores o imprecisiones. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por un humano. No nos hacemos responsables de malentendidos o interpretaciones erróneas que puedan surgir del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->