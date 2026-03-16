[![Intro to AI Agents](../../../translated_images/fr/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Cliquez sur l'image ci-dessus pour voir la vidéo de cette leçon)_


# Introduction aux Agents IA et Cas d'Utilisation des Agents

Bienvenue dans le cours "Agents IA pour Débutants" ! Ce cours fournit des connaissances fondamentales et des exemples pratiques pour créer des Agents IA.

Rejoignez la <a href="https://discord.gg/kzRShWzttr" target="_blank">Communauté Discord Azure AI</a> pour rencontrer d'autres apprenants et créateurs d'Agents IA, et poser toutes vos questions sur ce cours.

Pour commencer ce cours, nous commençons par mieux comprendre ce que sont les Agents IA et comment nous pouvons les utiliser dans les applications et workflows que nous construisons.

## Introduction

Cette leçon couvre :

- Qu'est-ce que les Agents IA et quels sont les différents types d'agents ?
- Quels cas d'utilisation sont les plus adaptés aux Agents IA et comment peuvent-ils nous aider ?
- Quels sont certains des blocs de construction de base lors de la conception de Solutions Agentiques ?

## Objectifs d’Apprentissage
Après avoir terminé cette leçon, vous devriez être capable de :

- Comprendre les concepts des Agents IA et comment ils diffèrent des autres solutions IA.
- Appliquer les Agents IA de façon optimale.
- Concevoir des solutions agentiques de manière productive pour les utilisateurs et les clients.

## Définition des Agents IA et Types d’Agents IA

### Qu’est-ce que les Agents IA ?

Les Agents IA sont des **systèmes** qui permettent aux **Modèles de Grand Langage (LLMs)** de **réaliser des actions** en étendant leurs capacités en donnant aux LLMs **l'accès à des outils** et à des **connaissances**.

Décomposons cette définition en parties plus petites :

- **Système** - Il est important de penser aux agents non pas comme un seul composant mais comme un système composé de plusieurs composants. Au niveau de base, les composants d’un Agent IA sont :
  - **Environnement** - L’espace défini où l’Agent IA opère. Par exemple, si nous avions un agent IA de réservation de voyages, l’environnement pourrait être le système de réservation de voyage que l’agent utilise pour accomplir des tâches.
  - **Capteurs** - Les environnements contiennent des informations et fournissent des retours. Les Agents IA utilisent des capteurs pour collecter et interpréter ces informations sur l'état actuel de l’environnement. Dans l'exemple de l'agent de réservation de voyage, le système de réservation peut fournir des informations telles que la disponibilité des hôtels ou les prix des vols.
  - **Actionneurs** - Une fois que l’Agent IA reçoit l’état actuel de l’environnement, pour la tâche en cours l’agent détermine quelle action effectuer pour changer l’environnement. Pour l’agent de réservation de voyage, cela pourrait être de réserver une chambre disponible pour l’utilisateur.

![What Are AI Agents?](../../../translated_images/fr/what-are-ai-agents.1ec8c4d548af601a.webp)

**Modèles de Grand Langage** - Le concept d’agents existait avant la création des LLMs. L’avantage de construire des Agents IA avec des LLMs est leur capacité à interpréter le langage humain et les données. Cette capacité permet aux LLMs d’interpréter les informations de l’environnement et de définir un plan pour changer l’environnement.

**Effectuer des Actions** - En dehors des systèmes d’Agents IA, les LLMs sont limités aux situations où l’action consiste à générer du contenu ou de l’information basée sur la demande d’un utilisateur. Dans les systèmes d’Agents IA, les LLMs peuvent accomplir des tâches en interprétant la demande de l’utilisateur et en utilisant les outils disponibles dans leur environnement.

**Accès aux Outils** - Les outils auxquels le LLM a accès sont définis par 1) l’environnement dans lequel il opère et 2) le développeur de l’Agent IA. Pour notre exemple d’agent de voyage, les outils de l’agent sont limités par les opérations disponibles dans le système de réservation, et/ou le développeur peut limiter l’accès aux outils de l’agent aux seuls vols.

**Mémoire+Connaissance** - La mémoire peut être à court terme dans le contexte de la conversation entre l’utilisateur et l’agent. À long terme, en dehors des informations fournies par l’environnement, les Agents IA peuvent également récupérer des connaissances provenant d’autres systèmes, services, outils, et même d’autres agents. Dans l’exemple de l’agent de voyage, ces connaissances pourraient être les informations sur les préférences de voyage de l’utilisateur situées dans une base de données client.

### Les différents types d’agents

Maintenant que nous avons une définition générale des Agents IA, examinons certains types spécifiques d’agents et comment ils seraient appliqués à un agent IA de réservation de voyage.

| **Type d’Agent**             | **Description**                                                                                                                      | **Exemple**                                                                                                                                                                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Agents Réflexes Simples**  | Effectuent des actions immédiates basées sur des règles prédéfinies.                                                               | L’agent de voyage interprète le contexte de l’email et transfère les plaintes de voyage au service client.                                                                                                                   |
| **Agents Réflexes Basés sur un Modèle** | Effectuent des actions basées sur un modèle du monde et ses changements.                                                           | L’agent de voyage priorise les itinéraires avec des changements de prix importants en se basant sur l’accès aux données de prix historiques.                                                                                  |
| **Agents Basés sur des Objectifs** | Créent des plans pour atteindre des objectifs spécifiques en interprétant l’objectif et en déterminant les actions à entreprendre. | L’agent de voyage réserve un trajet en déterminant les arrangements nécessaires (voiture, transports en commun, vols) depuis le lieu actuel jusqu’à la destination.                                                             |
| **Agents Basés sur l’Utilité** | Prennent en compte les préférences et pèsent numériquement les compromis pour déterminer comment atteindre les objectifs.          | L’agent de voyage maximise l’utilité en pesant la commodité par rapport au coût lors de la réservation du voyage.                                                                                                             |
| **Agents Apprenants**         | S’améliorent au fil du temps en répondant aux retours et en ajustant leurs actions en conséquence.                                 | L’agent de voyage s’améliore en utilisant les retours clients issus des enquêtes post-voyage pour ajuster les futures réservations.                                                                                           |
| **Agents Hiérarchiques**      | Composés de plusieurs agents en système à niveaux, où les agents de niveau supérieur décomposent les tâches en sous-tâches pour les agents de niveau inférieur. | L’agent de voyage annule un voyage en divisant la tâche en sous-tâches (par exemple, annuler des réservations spécifiques) et en laissant les agents de niveau inférieur les accomplir puis faire un retour à l’agent de niveau supérieur. |
| **Systèmes Multi-Agents (MAS)** | Les agents accomplissent des tâches indépendamment, soit de manière coopérative soit compétitive.                                   | Coopératif : Plusieurs agents réservent des services de voyage spécifiques tels que les hôtels, vols et divertissements. Compétitif : Plusieurs agents gèrent et se concurrencent sur un calendrier partagé de réservation d’hôtel pour réserver les clients dans l’hôtel.           |

## Quand utiliser les Agents IA

Dans la section précédente, nous avons utilisé le cas d’utilisation de l’agent de voyage pour expliquer comment les différents types d’agents peuvent être utilisés dans différents scénarios de réservation de voyage. Nous continuerons à utiliser cette application tout au long du cours.

Voyons les types de cas d’utilisation pour lesquels les Agents IA sont les plus adaptés :

![When to use AI Agents?](../../../translated_images/fr/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Problèmes Ouverts** - permettre au LLM de déterminer les étapes nécessaires pour accomplir une tâche parce que cela ne peut pas toujours être codé en dur dans un workflow.
- **Processus en Plusieurs Étapes** - tâches nécessitant un niveau de complexité où l’Agent IA doit utiliser des outils ou des informations sur plusieurs tours au lieu d’un simple rappel.
- **Amélioration dans le Temps** - tâches où l’agent peut s’améliorer au fil du temps en recevant des retours soit de son environnement, soit des utilisateurs afin de fournir une meilleure utilité.

Nous couvrons plus de considérations sur l’utilisation des Agents IA dans la leçon Construire des Agents IA de Confiance.

## Bases des Solutions Agentiques

### Développement d’Agent

La première étape pour concevoir un système d’Agent IA est de définir les outils, actions et comportements. Dans ce cours, nous nous concentrons sur l’utilisation du **Azure AI Agent Service** pour définir nos Agents. Il offre des fonctionnalités telles que :

- Sélection de modèles ouverts tels que OpenAI, Mistral et Llama
- Utilisation de données sous licence via des fournisseurs tels que Tripadvisor
- Utilisation d’outils standardisés OpenAPI 3.0

### Patterns Agentiques

La communication avec les LLMs se fait par des prompts. Étant donné la nature semi-autonome des Agents IA, il n’est pas toujours possible ni nécessaire de relancer manuellement le prompt du LLM après un changement dans l’environnement. Nous utilisons des **patterns agentiques** qui nous permettent de solliciter le LLM sur plusieurs étapes de façon plus évolutive.

Ce cours est divisé en certains des patterns agentiques populaires actuels.

### Frameworks Agentiques

Les Frameworks agentiques permettent aux développeurs d’implémenter des patterns agentiques via du code. Ces frameworks offrent des templates, plugins et outils pour une meilleure collaboration avec les Agents IA. Ces avantages fournissent des capacités pour une meilleure observabilité et un dépannage plus efficace des systèmes d’Agents IA.

Dans ce cours, nous allons explorer le framework AutoGen orienté recherche et le framework Agent prêt pour la production de Semantic Kernel.

## Exemples de Code

- Python : [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET : [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## Vous avez Plus de Questions sur les Agents IA ?

Rejoignez le [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pour rencontrer d’autres apprenants, participer aux heures de bureau et obtenir des réponses à vos questions sur les Agents IA.

## Leçon Précédente

[Configuration du cours](../00-course-setup/README.md)

## Leçon Suivante

[Exploration des Frameworks Agentiques](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Avertissement** :  
Ce document a été traduit à l’aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d’origine doit être considéré comme la source faisant foi. Pour toute information critique, il est recommandé de recourir à une traduction professionnelle réalisée par un humain. Nous ne saurions être tenus responsables de tout malentendu ou mauvaise interprétation résultant de l’utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->