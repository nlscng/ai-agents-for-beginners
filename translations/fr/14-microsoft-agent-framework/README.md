# Exploration du Microsoft Agent Framework

![Framework d'agent](../../../translated_images/fr/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Introduction

Cette leçon couvrira :

- Comprendre Microsoft Agent Framework : fonctionnalités clés et valeur  
- Explorer les concepts clés de Microsoft Agent Framework
- Comparer MAF à Semantic Kernel et AutoGen : guide de migration

## Objectifs d'apprentissage

Après avoir terminé cette leçon, vous saurez comment :

- Construire des agents IA prêts pour la production en utilisant Microsoft Agent Framework
- Appliquer les fonctionnalités principales de Microsoft Agent Framework à vos cas d'utilisation agentiques
- Migrer et intégrer des frameworks et outils agentiques existants  

## Exemples de code 

Des exemples de code pour [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) se trouvent dans ce dépôt sous les fichiers `xx-python-agent-framework` et `xx-dotnet-agent-framework`.

## Comprendre Microsoft Agent Framework

![Framework Intro](../../../translated_images/fr/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) s'appuie sur l'expérience et les enseignements de Semantic Kernel et AutoGen. Il offre la flexibilité nécessaire pour répondre à la grande variété de cas d'utilisation agentiques observés en production et en recherche, notamment :

- **Orchestration d'agents séquentielle** dans des scénarios nécessitant des workflows étape par étape.
- **Orchestration concurrente** dans des scénarios où les agents doivent accomplir des tâches en même temps.
- **Orchestration de chat de groupe** dans des scénarios où les agents peuvent collaborer ensemble sur une même tâche.
- **Orchestration de transfert (Handoff)** dans des scénarios où les agents se transmettent la tâche au fur et à mesure que les sous-tâches sont complétées.
- **Orchestration magnétique** dans des scénarios où un agent gestionnaire crée et modifie une liste de tâches et gère la coordination des sous-agents pour accomplir la tâche.

Pour déployer des agents IA en production, MAF inclut également des fonctionnalités pour :

- **Observabilité** via l'utilisation d'OpenTelemetry où chaque action de l'agent IA, y compris l'invocation d'outils, les étapes d'orchestration, les flux de raisonnement et la surveillance des performances, est visible via les tableaux de bord Microsoft Foundry.
- **Sécurité** en hébergeant les agents nativement sur Microsoft Foundry, qui inclut des contrôles de sécurité tels que l'accès basé sur les rôles, la gestion des données privées et la sécurité intégrée du contenu.
- **Durabilité** car les threads et workflows d'agent peuvent être mis en pause, repris et récupérés après des erreurs, ce qui permet des processus de plus longue durée.
- **Contrôle** avec des workflows incluant un humain dans la boucle, où des tâches sont marquées comme nécessitant une approbation humaine.

Microsoft Agent Framework met également l'accent sur l'interopérabilité par :

- **Indépendance vis-à-vis du cloud** - Les agents peuvent s'exécuter dans des conteneurs, sur site et sur plusieurs clouds différents.
- **Indépendance vis-à-vis du fournisseur** - Les agents peuvent être créés via le SDK de votre choix, y compris Azure OpenAI et OpenAI
- **Intégration des standards ouverts** - Les agents peuvent utiliser des protocoles tels que Agent-to-Agent (A2A) et Model Context Protocol (MCP) pour découvrir et utiliser d'autres agents et outils.
- **Plugins et connecteurs** - Des connexions peuvent être établies vers des services de données et de mémoire tels que Microsoft Fabric, SharePoint, Pinecone et Qdrant.

Voyons comment ces fonctionnalités s'appliquent à certains des concepts clés de Microsoft Agent Framework.

## Concepts clés de Microsoft Agent Framework

### Agents

![Agent Framework](../../../translated_images/fr/agent-components.410a06daf87b4fef.webp)

**Création d'agents**

La création d'un agent se fait en définissant le service d'inférence (LLM Provider), un ensemble d'instructions que l'agent IA doit suivre, et un `name` attribué :

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

L'exemple ci‑dessus utilise `Azure OpenAI` mais des agents peuvent être créés en utilisant une variété de services, y compris `Microsoft Foundry Agent Service` :

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

ou des agents distants utilisant le protocole A2A :

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Exécution des agents**

Les agents s'exécutent à l'aide des méthodes `.run` ou `.run_stream` pour les réponses non-streaming ou streaming.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Chaque exécution d'agent peut également avoir des options pour personnaliser des paramètres tels que `max_tokens` utilisés par l'agent, les `tools` que l'agent peut appeler, et même le `model` lui-même utilisé pour l'agent.

Ceci est utile dans les cas où des modèles ou outils spécifiques sont nécessaires pour accomplir la tâche d'un utilisateur.

**Outils**

Les outils peuvent être définis à la fois lors de la définition de l'agent :

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Lors de la création directe d'un ChatAgent

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

et aussi lors de l'exécution de l'agent :

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Outil fourni uniquement pour cette exécution )
```

**Threads d'agent**

Les threads d'agent sont utilisés pour gérer les conversations à plusieurs tours. Les threads peuvent être créés soit en :

- Utilisant `get_new_thread()` qui permet au thread d'être sauvegardé au fil du temps
- Créant un thread automatiquement lors de l'exécution d'un agent et en ne faisant durer le thread que pendant l'exécution en cours.

Pour créer un thread, le code ressemble à ceci :

```python
# Créer un nouveau thread.
thread = agent.get_new_thread() # Exécuter l'agent avec le thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Vous pouvez ensuite sérialiser le thread pour le stocker et l'utiliser ultérieurement :

```python
# Créer un nouveau fil d'exécution.
thread = agent.get_new_thread() 

# Exécuter l'agent avec le fil d'exécution.

response = await agent.run("Hello, how are you?", thread=thread) 

# Sérialiser le fil d'exécution pour le stockage.

serialized_thread = await thread.serialize() 

# Désérialiser l'état du fil d'exécution après le chargement depuis le stockage.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware d'agent**

Les agents interagissent avec des outils et des LLM pour accomplir les tâches des utilisateurs. Dans certains scénarios, nous souhaitons exécuter ou suivre des actions entre ces interactions. Le middleware d'agent nous permet de le faire via :

*Middleware de fonction*

Ce middleware permet d'exécuter une action entre l'agent et une fonction/outils qu'il va appeler. Un exemple d'utilisation est lorsque vous souhaitez faire un enregistrement (logging) de l'appel de la fonction.

Dans le code ci‑dessous, `next` définit si le middleware suivant ou la fonction réelle doit être appelé.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Pré-traitement : journaliser avant l'exécution de la fonction
    print(f"[Function] Calling {context.function.name}")

    # Continuer vers le middleware suivant ou l'exécution de la fonction
    await next(context)

    # Post-traitement : journaliser après l'exécution de la fonction
    print(f"[Function] {context.function.name} completed")
```

*Middleware de chat*

Ce middleware nous permet d'exécuter ou d'enregistrer une action entre l'agent et les requêtes envoyées au LLM.

Il contient des informations importantes telles que les `messages` qui sont envoyés au service IA.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Pré-traitement : consigner avant l'appel à l'IA
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Continuer vers le middleware suivant ou le service d'IA
    await next(context)

    # Post-traitement : consigner après la réponse de l'IA
    print("[Chat] AI response received")

```

**Mémoire d'agent**

Comme vu dans la leçon `Agentic Memory`, la mémoire est un élément important pour permettre à l'agent de fonctionner sur différents contextes. MAF propose plusieurs types de mémoires :

*Stockage en mémoire (In-Memory Storage)*

Il s'agit de la mémoire stockée dans les threads pendant l'exécution de l'application.

```python
# Créer un nouveau fil d'exécution.
thread = agent.get_new_thread() # Exécuter l'agent avec le fil d'exécution.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Messages persistants*

Cette mémoire est utilisée pour stocker l'historique des conversations à travers différentes sessions. Elle est définie en utilisant le `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Créer un magasin de messages personnalisé
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Mémoire dynamique*

Cette mémoire est ajoutée au contexte avant l'exécution des agents. Ces mémoires peuvent être stockées dans des services externes tels que mem0 :

```python
from agent_framework.mem0 import Mem0Provider

# Utilisation de Mem0 pour des capacités mémoire avancées
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

**Observabilité des agents**

L'observabilité est importante pour construire des systèmes agentiques fiables et maintenables. MAF s'intègre avec OpenTelemetry pour fournir du tracing et des compteurs afin d'améliorer l'observabilité.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # faire quelque chose
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Flux de travail

MAF propose des workflows qui sont des étapes pré-définies pour accomplir une tâche et incluent des agents IA comme composants de ces étapes.

Les flux de travail sont composés de différents composants qui permettent un meilleur contrôle du flux. Les workflows permettent également l'**orchestration multi-agent** et le **checkpointing** pour sauvegarder les états du workflow.

Les composants principaux d'un workflow sont :

**Exécuteurs**

Les exécuteurs reçoivent des messages d'entrée, effectuent les tâches qui leur sont assignées, puis produisent un message de sortie. Cela fait avancer le workflow vers l'accomplissement de la tâche globale. Les exécuteurs peuvent être soit des agents IA soit de la logique personnalisée.

**Arêtes**

Les arêtes sont utilisées pour définir le flux des messages dans un workflow. Celles-ci peuvent être :

*Arêtes directes* - Connexions simples un-à-un entre exécuteurs :

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Arêtes conditionnelles* - Activées après qu'une certaine condition est remplie. Par exemple, lorsque des chambres d'hôtel sont indisponibles, un exécuteur peut suggérer d'autres options.

*Arêtes de type switch-case* - Acheminent les messages vers différents exécuteurs en fonction de conditions définies. Par exemple, si un client voyageur a un accès prioritaire, ses tâches seront traitées via un autre workflow.

*Arêtes de type fan-out* - Envoient un message vers plusieurs cibles.

*Arêtes de type fan-in* - Collectent plusieurs messages provenant de différents exécuteurs et les envoient vers une cible unique.

**Événements**

Pour offrir une meilleure observabilité des workflows, MAF propose des événements intégrés pour l'exécution, notamment :

- `WorkflowStartedEvent`  - Début de l'exécution du workflow
- `WorkflowOutputEvent` - Le workflow produit une sortie
- `WorkflowErrorEvent` - Le workflow rencontre une erreur
- `ExecutorInvokeEvent`  - L'exécuteur commence le traitement
- `ExecutorCompleteEvent`  -  L'exécuteur termine le traitement
- `RequestInfoEvent` - Une requête est émise

## Migration depuis d'autres frameworks (Semantic Kernel et AutoGen)

### Différences entre MAF et Semantic Kernel

**Création d'agents simplifiée**

Semantic Kernel repose sur la création d'une instance Kernel pour chaque agent. MAF adopte une approche simplifiée en utilisant des extensions pour les principaux fournisseurs.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Création de threads d'agent**

Semantic Kernel exige que les threads soient créés manuellement. Dans MAF, le thread est assigné directement à l'agent.

```python
thread = agent.get_new_thread() # Exécuter l'agent avec le fil d'exécution.
```

**Enregistrement des outils**

Dans Semantic Kernel, les outils sont enregistrés auprès du Kernel et le Kernel est ensuite passé à l'agent. Dans MAF, les outils sont enregistrés directement lors du processus de création de l'agent.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Différences entre MAF et AutoGen

**Teams vs Workflows**

`Teams` sont la structure d'événements pour l'activité pilotée par des événements avec des agents dans AutoGen. MAF utilise des `Workflows` qui acheminent les données vers des exécuteurs via une architecture basée sur un graphe.

**Création d'outils**

AutoGen utilise `FunctionTool` pour envelopper des fonctions que les agents peuvent appeler. MAF utilise @ai_function qui fonctionne de manière similaire mais infère également automatiquement les schémas pour chaque fonction.

**Comportement des agents**

Les agents sont par défaut à tour unique dans AutoGen à moins que `max_tool_iterations` ne soit défini sur une valeur supérieure. Dans MAF, le `ChatAgent` est multi-tours par défaut, ce qui signifie qu'il continuera à appeler des outils jusqu'à ce que la tâche de l'utilisateur soit terminée.

## Exemples de code 

Des exemples de code pour Microsoft Agent Framework se trouvent dans ce dépôt sous les fichiers `xx-python-agent-framework` et `xx-dotnet-agent-framework`.

## Vous avez d'autres questions sur Microsoft Agent Framework ?

Rejoignez le [Discord de Microsoft Foundry](https://aka.ms/ai-agents/discord) pour rencontrer d'autres apprenants, assister à des heures de permanence et obtenir des réponses à vos questions sur les agents IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Clause de non-responsabilité :**
Ce document a été traduit à l'aide du service de traduction automatique Co-op Translator (https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d'être précis, veuillez noter que les traductions automatisées peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d'origine doit être considéré comme la source faisant foi. Pour les informations critiques, il est recommandé de recourir à une traduction professionnelle effectuée par un traducteur humain. Nous ne sommes pas responsables des malentendus ou des interprétations erronées résultant de l'utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->