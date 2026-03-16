# AGENTS.md

## Resumen del Proyecto

Este repositorio contiene "Agentes de IA para Principiantes" - un curso educativo integral que enseña todo lo necesario para construir Agentes de IA. El curso consta de más de 15 lecciones que cubren fundamentos, patrones de diseño, frameworks y despliegue en producción de agentes de IA.

**Tecnologías Clave:**
- Python 3.12+
- Jupyter Notebooks para aprendizaje interactivo
- Frameworks de IA: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Servicios de Azure AI: Microsoft Foundry, Azure AI Agent Service
- Mercado de modelos de GitHub (nivel gratuito disponible)

**Arquitectura:**
- Estructura basada en lecciones (directorios 00-15+)
- Cada lección contiene: documentación README, ejemplos de código (Jupyter notebooks) e imágenes
- Soporte multilingüe mediante sistema de traducción automatizado
- Varias opciones de framework por lección (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Comandos de Configuración

### Requisitos Previos
- Python 3.12 o superior
- Cuenta de GitHub (para Modelos de GitHub - nivel gratuito)
- Suscripción de Azure (opcional, para servicios AI de Azure)

### Configuración Inicial

1. **Clona o haz fork del repositorio:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # O
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Crea y activa un entorno virtual de Python:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   ```

3. **Instala las dependencias:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configura las variables de entorno:**
   ```bash
   cp .env.example .env
   # Edita el archivo .env con tus claves API y endpoints
   ```

### Variables de Entorno Requeridas

Para **Modelos de GitHub (Gratis)**:
- `GITHUB_TOKEN` - Token de acceso personal de GitHub

Para **Servicios AI de Azure** (opcional):
- `PROJECT_ENDPOINT` - Endpoint del proyecto en Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - Clave API de Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL endpoint de Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Nombre del despliegue para el modelo de chat
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Nombre del despliegue para embeddings
- Configuración adicional de Azure como se muestra en `.env.example`

## Flujo de Trabajo para Desarrollo

### Ejecución de Jupyter Notebooks

Cada lección contiene múltiples notebooks de Jupyter para diferentes frameworks:

1. **Inicia Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navega a un directorio de lección** (ej. `01-intro-to-ai-agents/code_samples/`)

3. **Abre y ejecuta notebooks:**
   - `*-semantic-kernel.ipynb` - Usando el framework Semantic Kernel
   - `*-autogen.ipynb` - Usando el framework AutoGen
   - `*-python-agent-framework.ipynb` - Usando Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Usando Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Usando Azure AI Agent Service

### Trabajo con Diferentes Frameworks

**Semantic Kernel + Modelos GitHub:**
- Nivel gratuito disponible con cuenta de GitHub
- Bueno para aprendizaje y experimentación
- Patrón de archivos: `*-semantic-kernel*.ipynb`

**AutoGen + Modelos GitHub:**
- Nivel gratuito disponible con cuenta de GitHub
- Capacidades de orquestación multiagente
- Patrón de archivos: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Último framework de Microsoft
- Disponible en Python y .NET
- Patrón de archivos: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Requiere suscripción Azure
- Funcionalidades listas para producción
- Patrón de archivos: `*-azureaiagent.ipynb`

## Instrucciones para Pruebas

Este es un repositorio educativo con código de ejemplo en lugar de código de producción con pruebas automatizadas. Para verificar tu configuración y cambios:

### Pruebas Manuales

1. **Prueba el entorno Python:**
   ```bash
   python --version  # Debe ser 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Prueba la ejecución de notebooks:**
   ```bash
   # Convertir el cuaderno a script y ejecutar (prueba las importaciones)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Verifica las variables de entorno:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Ejecución Individual de Notebooks

Abre notebooks en Jupyter y ejecuta las celdas secuencialmente. Cada notebook es autónomo e incluye:
- Importaciones
- Carga de configuración
- Implementaciones de agentes de ejemplo
- Resultados esperados en celdas markdown

## Estilo de Código

### Convenciones para Python

- **Versión Python**: 3.12+
- **Estilo de Código**: Sigue las convenciones estándar PEP 8 de Python
- **Notebooks**: Usa celdas markdown claras para explicar conceptos
- **Imports**: Agrupa por biblioteca estándar, terceros, locales

### Convenciones para Jupyter Notebook

- Incluye celdas markdown descriptivas antes del código
- Añade ejemplos de salida en notebooks para referencia
- Usa nombres de variables claros que coincidan con los conceptos de la lección
- Mantén el orden de ejecución de notebooks lineal (celda 1 → 2 → 3...)

### Organización de Archivos

```
<lesson-number>-<lesson-name>/
├── README.md                     # Lesson documentation
├── code_samples/
│   ├── <number>-semantic-kernel.ipynb
│   ├── <number>-autogen.ipynb
│   ├── <number>-python-agent-framework.ipynb
│   └── <number>-azureaiagent.ipynb
└── images/
    └── *.png
```

## Construcción y Despliegue

### Construcción de Documentación

Este repositorio usa Markdown para documentación:
- Archivos README.md en cada carpeta de lección
- README.md principal en la raíz del repositorio
- Sistema de traducción automatizado mediante GitHub Actions

### Pipeline CI/CD

Ubicado en `.github/workflows/`:

1. **co-op-translator.yml** - Traducción automática a más de 50 idiomas
2. **welcome-issue.yml** - Da la bienvenida a los creadores de issues nuevos
3. **welcome-pr.yml** - Da la bienvenida a los colaboradores de pull requests nuevos

### Despliegue

Este es un repositorio educativo - sin proceso de despliegue. Los usuarios:
1. Hacen fork o clonan el repositorio
2. Ejecutan los notebooks localmente o en GitHub Codespaces
3. Aprenden modificando y experimentando con ejemplos

## Guía para Pull Requests

### Antes de Enviar

1. **Prueba tus cambios:**
   - Ejecuta completamente los notebooks afectados
   - Verifica que todas las celdas se ejecuten sin errores
   - Confirma que las salidas sean adecuadas

2. **Actualizaciones de documentación:**
   - Actualiza README.md si agregas nuevos conceptos
   - Agrega comentarios en notebooks para código complejo
   - Asegúrate que las celdas markdown expliquen el propósito

3. **Cambios en archivos:**
   - Evita subir archivos `.env` (usa `.env.example`)
   - No subas directorios `venv/` ni `__pycache__/`
   - Conserva las salidas de notebooks cuando demuestran conceptos
   - Elimina archivos temporales y notebooks de respaldo (`*-backup.ipynb`)

### Formato del Título para PR

Usa títulos descriptivos:
- `[Lesson-XX] Añadir nuevo ejemplo para <concepto>`
- `[Fix] Corregir error tipográfico en README de la lección-XX`
- `[Update] Mejorar ejemplo de código en la lección-XX`
- `[Docs] Actualizar instrucciones de configuración`

### Verificaciones Requeridas

- Los notebooks deben ejecutarse sin errores
- Los archivos README deben ser claros y precisos
- Sigue los patrones de código existentes en el repositorio
- Mantén coherencia con otras lecciones

## Notas Adicionales

### Problemas Comunes

1. **Desajuste de versión de Python:**
   - Asegura usar Python 3.12+
   - Algunos paquetes pueden no funcionar con versiones anteriores
   - Usa `python3 -m venv` para especificar explícitamente la versión

2. **Variables de entorno:**
   - Siempre crea `.env` a partir de `.env.example`
   - No subas el archivo `.env` (está en `.gitignore`)
   - El token de GitHub necesita permisos adecuados

3. **Conflictos de paquetes:**
   - Usa un entorno virtual limpio
   - Instala desde `requirements.txt` en lugar de paquetes individuales
   - Algunos notebooks pueden requerir paquetes adicionales mencionados en sus celdas markdown

4. **Servicios de Azure:**
   - Los servicios de Azure AI requieren suscripción activa
   - Algunas funcionalidades son específicas para ciertas regiones
   - Aplican limitaciones del nivel gratuito para Modelos GitHub

### Ruta de Aprendizaje

Progresión recomendada a través de las lecciones:
1. **00-course-setup** - Comienza aquí para la configuración del entorno
2. **01-intro-to-ai-agents** - Comprende los fundamentos de agentes IA
3. **02-explore-agentic-frameworks** - Aprende sobre diferentes frameworks
4. **03-agentic-design-patterns** - Patrones de diseño fundamentales
5. Continúa secuencialmente con las lecciones numeradas

### Selección de Framework

Elige el framework según tus objetivos:
- **Aprendizaje/Prototipado**: Semantic Kernel + Modelos GitHub (gratis)
- **Sistemas multi-agente**: AutoGen
- **Características más recientes**: Microsoft Agent Framework (MAF)
- **Despliegue en producción**: Azure AI Agent Service

### Obtener Ayuda

- Únete al [Discord de la Comunidad Microsoft Foundry](https://aka.ms/ai-agents/discord)
- Revisa los archivos README de las lecciones para guía específica
- Consulta el [README.md principal](./README.md) para resumen del curso
- Consulta [Configuración del Curso](./00-course-setup/README.md) para instrucciones detalladas

### Contribuir

Este es un proyecto educativo abierto. Se aceptan contribuciones:
- Mejorar ejemplos de código
- Corregir errores tipográficos o de código
- Añadir comentarios aclaratorios
- Sugerir nuevos temas para lecciones
- Traducir a idiomas adicionales

Consulta [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) para necesidades actuales.

## Contexto Específico del Proyecto

### Soporte Multilingüe

Este repositorio usa un sistema de traducción automatizado:
- Más de 50 idiomas soportados
- Traducciones en directorios `/translations/<lang-code>/`
- El flujo de trabajo de GitHub Actions maneja las actualizaciones de traducción
- Los archivos fuente están en inglés en la raíz del repositorio

### Estructura de la Lección

Cada lección sigue un patrón consistente:
1. Miniatura de video con enlace
2. Contenido escrito de la lección (README.md)
3. Ejemplos de código en múltiples frameworks
4. Objetivos de aprendizaje y prerequisitos
5. Recursos adicionales de aprendizaje enlazados

### Nomenclatura de Ejemplos de Código

Formato: `<lesson-number>-<framework-name>.ipynb`
- `04-semantic-kernel.ipynb` - Lección 4, Semantic Kernel
- `07-autogen.ipynb` - Lección 7, AutoGen
- `14-python-agent-framework.ipynb` - Lección 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Lección 14, MAF .NET

### Directorios Especiales

- `translated_images/` - Imágenes localizadas para traducciones
- `images/` - Imágenes originales para contenido en inglés
- `.devcontainer/` - Configuración del contenedor de desarrollo para VS Code
- `.github/` - Flujos y plantillas de acciones de GitHub

### Dependencias

Paquetes clave desde `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - Framework AutoGen
- `semantic-kernel` - Framework Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - Servicios Azure AI
- `azure-search-documents` - Integración Azure AI Search
- `chromadb` - Base de datos vectorial para ejemplos RAG
- `chainlit` - Framework para interfaz de chat
- `browser_use` - Automatización de navegador para agentes
- `mcp[cli]` - Soporte para Model Context Protocol
- `mem0ai` - Gestión de memoria para agentes

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Aviso Legal**:  
Este documento ha sido traducido utilizando el servicio de traducción automática [Co-op Translator](https://github.com/Azure/co-op-translator). Aunque nos esforzamos por la precisión, tenga en cuenta que las traducciones automatizadas pueden contener errores o inexactitudes. El documento original en su idioma nativo debe considerarse la fuente autorizada. Para información crítica, se recomienda una traducción profesional realizada por humanos. No nos hacemos responsables por malentendidos o interpretaciones erróneas derivadas del uso de esta traducción.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->