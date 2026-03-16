# Utilisation des Protocoles Agentiques (MCP, A2A et NLWeb)

[![Agentic Protocols](../../../translated_images/fr/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Cliquez sur l'image ci-dessus pour voir la vidéo de cette leçon)_

À mesure que l'utilisation des agents IA se développe, le besoin de protocoles garantissant la standardisation, la sécurité et favorisant l'innovation ouverte grandit également. Dans cette leçon, nous aborderons 3 protocoles visant à répondre à ce besoin - Model Context Protocol (MCP), Agent to Agent (A2A) et Natural Language Web (NLWeb).

## Introduction

Dans cette leçon, nous verrons :

• Comment **MCP** permet aux agents IA d'accéder à des outils et données externes pour accomplir les tâches des utilisateurs.

• Comment **A2A** facilite la communication et la collaboration entre différents agents IA.

• Comment **NLWeb** apporte une interface en langage naturel à tout site web, permettant aux agents IA de découvrir et d'interagir avec le contenu.

## Objectifs d'apprentissage

• **Identifier** le but principal et les avantages de MCP, A2A, et NLWeb dans le contexte des agents IA.

• **Expliquer** comment chaque protocole facilite la communication et l'interaction entre LLM, outils, et autres agents.

• **Reconnaître** les rôles distincts que chaque protocole joue dans la construction de systèmes agentiques complexes.

## Model Context Protocol

Le **Model Context Protocol (MCP)** est une norme ouverte qui offre un moyen standardisé aux applications de fournir contexte et outils aux LLMs. Cela permet un « adaptateur universel » aux différentes sources de données et outils auxquels les agents IA peuvent se connecter de manière cohérente.

Examinons les composants de MCP, les avantages comparés à l'utilisation directe d'API, et un exemple d’utilisation d’un serveur MCP par des agents IA.

### Composants essentiels de MCP

MCP fonctionne sur une **architecture client-serveur** et les composants principaux sont :

• **Hôtes** sont des applications LLM (par exemple un éditeur de code comme VSCode) qui démarrent les connexions vers un serveur MCP.

• **Clients** sont des composants au sein de l’application hôte qui maintiennent une connexion un-à-un avec les serveurs.

• **Serveurs** sont des programmes légers exposant des capacités spécifiques.

Le protocole inclut trois primitives de base qui représentent les capacités d’un serveur MCP :

• **Outils** : Ce sont des actions ou fonctions isolées qu'un agent IA peut appeler pour exécuter une tâche. Par exemple, un service météo pourrait exposer un outil « obtenir la météo », ou un serveur e-commerce un outil « acheter un produit ». Les serveurs MCP annoncent le nom, la description, et le schéma d’entrée/sortie de chaque outil dans leur liste de capacités.

• **Ressources** : Ce sont des éléments ou documents en lecture seule qu’un serveur MCP peut fournir, et que les clients peuvent récupérer à la demande. Exemples : contenu de fichiers, enregistrements de base de données, fichiers logs. Les ressources peuvent être du texte (comme du code ou JSON) ou du binaire (images, PDF).

• **Prompts** : Ce sont des modèles prédéfinis fournissant des suggestions de prompts pour permettre des flux de travail plus complexes.

### Avantages de MCP

MCP offre des avantages significatifs pour les agents IA :

• **Découverte dynamique des outils** : Les agents peuvent recevoir dynamiquement une liste des outils disponibles sur un serveur avec leurs descriptions. Cela contraste avec les API traditionnelles qui requièrent souvent un codage statique pour les intégrations, rendant nécessaires des mises à jour à chaque changement d’API. MCP propose une approche « intégrer une fois », offrant une meilleure adaptabilité.

• **Interopérabilité entre LLMs** : MCP fonctionne avec différents LLMs, offrant la flexibilité de changer de modèle principal pour une meilleure performance.

• **Sécurité standardisée** : MCP inclut une méthode d'authentification standard, améliorant la scalabilité lors de l’ajout d’accès à plusieurs serveurs MCP. C’est plus simple que de gérer des clés et authentifications différentes pour diverses API traditionnelles.

### Exemple MCP

![MCP Diagram](../../../translated_images/fr/mcp-diagram.e4ca1cbd551444a1.webp)

Imaginez qu’un utilisateur souhaite réserver un vol avec un assistant IA alimenté par MCP.

1. **Connexion** : L’assistant IA (client MCP) se connecte à un serveur MCP fourni par une compagnie aérienne.

2. **Découverte des outils** : Le client demande au serveur MCP de la compagnie : « Quels outils avez-vous disponibles ? » Le serveur répond avec des outils comme « rechercher des vols » et « réserver des vols ».

3. **Invocation d’outil** : Ensuite, vous demandez à l’assistant : « Veuillez rechercher un vol de Portland à Honolulu. » L’assistant IA, via son LLM, identifie qu’il doit appeler l’outil « rechercher des vols » et transmet les paramètres (origine, destination) au serveur MCP.

4. **Exécution et réponse** : Le serveur MCP, agissant comme un wrapper, effectue réellement l’appel à l’API interne de réservation de la compagnie aérienne. Il reçoit ensuite les informations du vol (par exemple en JSON) et les renvoie à l’assistant IA.

5. **Interaction supplémentaire** : L’assistant présente les options de vol. Une fois qu’un vol est choisi, l’assistant peut invoquer l’outil « réserver un vol » sur le même serveur MCP, finalisant la réservation.

## Protocole Agent-to-Agent (A2A)

Alors que MCP se concentre sur la connexion des LLM aux outils, le **protocole Agent-to-Agent (A2A)** va plus loin en permettant la communication et la collaboration entre différents agents IA. A2A connecte des agents IA issus de différentes organisations, environnements et stacks technologiques pour accomplir une tâche commune.

Nous examinerons les composants et avantages de l’A2A, ainsi qu’un exemple d’application dans notre scénario de voyage.

### Composants essentiels d’A2A

A2A vise à permettre la communication entre agents et leur travail collaboratif pour accomplir une sous-tâche utilisateur. Chaque composant contribue à cela :

#### Carte d’Agent

Comme un serveur MCP partage une liste d’outils, une Carte d’Agent contient :
- Le nom de l’agent.
- Une **description des tâches générales** qu’il accomplit.
- Une **liste de compétences spécifiques** avec descriptions pour aider d’autres agents (ou même des utilisateurs humains) à comprendre quand et pourquoi appeler cet agent.
- L’**URL de point de terminaison actuelle** de l’agent.
- La **version** et les **capacités** de l’agent, telles que réponses en streaming et notifications push.

#### Exécuteur d’Agent

L’Exécuteur d’Agent est responsable de **transmettre le contexte du chat utilisateur à l’agent distant**, nécessaire à l’agent pour comprendre la tâche à accomplir. Dans un serveur A2A, un agent utilise son propre Large Language Model (LLM) pour analyser les requêtes entrantes et exécuter les tâches en utilisant ses propres outils internes.

#### Artefact

Une fois qu’un agent distant a terminé la tâche demandée, son résultat est créé sous forme d’artefact. Un artefact **contient le résultat du travail de l’agent**, une **description de ce qui a été accompli**, et le **contexte texte** transmis via le protocole. Après envoi de l’artefact, la connexion avec l’agent distant est fermée jusqu’à ce qu’elle soit à nouveau nécessaire.

#### File d’événements

Ce composant sert à **gérer les mises à jour et transmettre les messages**. Il est particulièrement important en production pour les systèmes agentiques afin d’éviter que les connexions entre agents ne se ferment avant que la tâche soit terminée, surtout lorsque les temps d’exécution peuvent être longs.

### Avantages d’A2A

• **Collaboration améliorée** : Il permet aux agents de différents fournisseurs et plateformes d’interagir, partager le contexte, et collaborer pour automatiser de manière fluide des systèmes traditionnellement déconnectés.

• **Flexibilité de sélection de modèles** : Chaque agent A2A peut choisir le LLM utilisé pour traiter ses requêtes, permettant un usage de modèles optimisés ou fine-tunés par agent, contrairement à une connexion LLM unique dans certains scénarios MCP.

• **Authentification intégrée** : L’authentification est directement intégrée dans le protocole A2A, offrant un cadre de sécurité robuste pour les interactions entre agents.

### Exemple A2A

![A2A Diagram](../../../translated_images/fr/A2A-Diagram.8666928d648acc26.webp)

Développons notre scénario de réservation de voyage, mais cette fois via A2A.

1. **Requête utilisateur au Multi-Agent** : Un utilisateur interagit avec un client/agent A2A « Agent de voyage », par exemple en disant : « Réserve-moi un voyage complet à Honolulu la semaine prochaine, incluant vols, hôtel, et location de voiture ».

2. **Orchestration par l’Agent de Voyage** : L’agent de voyage reçoit cette demande complexe. Il utilise son LLM pour réfléchir à la tâche et déterminer qu’il doit interagir avec d’autres agents spécialisés.

3. **Communication inter-agent** : L’agent de voyage utilise ensuite le protocole A2A pour se connecter aux agents spécialisés en aval, comme un « agent compagnies aériennes », un « agent hôtel », et un « agent location de voitures », provenant de sociétés différentes.

4. **Exécution déléguée des tâches** : L’agent de voyage envoie des tâches spécifiques à ces agents spécialisés (ex : « Trouve des vols pour Honolulu », « Réserve un hôtel », « Loue une voiture »). Chacun, avec son propre LLM et ses outils (qui peuvent être eux-mêmes des serveurs MCP), réalise sa partie de la réservation.

5. **Réponse consolidée** : Une fois les agents terminant leurs tâches, l’agent de voyage compile les résultats (détails du vol, confirmation d’hôtel, réservation voiture) et renvoie une réponse complète en style chat à l’utilisateur.

## Natural Language Web (NLWeb)

Les sites web sont depuis longtemps le principal moyen d’accès des utilisateurs à l’information et aux données sur Internet.

Voyons les différents composants de NLWeb, ses avantages, et un exemple de fonctionnement avec notre application voyage.

### Composants de NLWeb

- **Application NLWeb (Code service principal)** : Le système qui traite les questions en langage naturel. Il relie les différentes parties de la plateforme pour créer des réponses. On peut le voir comme le **moteur qui alimente les fonctionnalités en langage naturel** d’un site web.

- **Protocole NLWeb** : Il constitue un **ensemble basique de règles pour l’interaction en langage naturel** avec un site web. Il retourne les réponses au format JSON (souvent avec Schema.org). Son but est de créer une base simple pour le « Web IA », comme HTML a permis le partage de documents en ligne.

- **Serveur MCP (point de terminaison Model Context Protocol)** : Chaque installation NLWeb fonctionne aussi comme un **serveur MCP**. Cela signifie qu’il peut **partager des outils (comme la méthode “ask”) et des données** avec d’autres systèmes IA. En pratique, cela rend le contenu et les capacités du site web utilisables par des agents IA, intégrant ainsi le site à l’écosystème plus large des agents.

- **Modèles d’Embedding** : Ces modèles sont utilisés pour **convertir le contenu du site web en représentations numériques appelées vecteurs (embeddings)**. Ces vecteurs capturent le sens d’une manière que les ordinateurs peuvent comparer et rechercher. Ils sont stockés dans une base de données spéciale, et les utilisateurs peuvent choisir le modèle d’embedding à utiliser.

- **Base de données vectorielle (mécanisme de recherche)** : Cette base **stocke les embeddings du contenu du site**. Lorsqu’une question est posée, NLWeb consulte la base pour trouver rapidement les informations les plus pertinentes. Elle donne une liste rapide de réponses possibles, classées par similarité. NLWeb fonctionne avec différents systèmes de stockage vectoriel comme Qdrant, Snowflake, Milvus, Azure AI Search et Elasticsearch.

### NLWeb en exemple

![NLWeb](../../../translated_images/fr/nlweb-diagram.c1e2390b310e5fe4.webp)

Considérons encore notre site de réservation voyage, mais cette fois alimenté par NLWeb.

1. **Ingestion de données** : Les catalogues de produits existants du site (ex : listes de vols, descriptions d’hôtels, forfaits touristiques) sont formatés avec Schema.org ou chargés via des flux RSS. Les outils de NLWeb ingèrent ces données structurées, créent des embeddings et les stockent dans une base vectorielle locale ou distante.

2. **Requête en langage naturel (humain)** : Un utilisateur visite le site et, au lieu de naviguer par menus, tape dans une interface de chat : « Trouve-moi un hôtel familial à Honolulu avec piscine pour la semaine prochaine ».

3. **Traitement NLWeb** : L’application NLWeb reçoit cette requête. Elle l’envoie à un LLM pour compréhension et simultanément recherche dans sa base vectorielle les offres d’hôtels pertinentes.

4. **Résultats précis** : Le LLM aide à interpréter les résultats de recherche de la base, identifie les meilleures correspondances selon les critères « familial », « piscine », et « Honolulu », puis formate une réponse en langue naturelle. Crucialement, la réponse fait référence à de véritables hôtels du catalogue, évitant toute information inventée.

5. **Interaction avec un agent IA** : Puisque NLWeb sert de serveur MCP, un agent IA externe pour les voyages pourrait aussi se connecter à cette instance NLWeb du site. L’agent IA pourrait alors utiliser la méthode `ask` du MCP pour interroger directement le site : `ask("Y a-t-il des restaurants végétaliens recommandés par l’hôtel dans la région de Honolulu ?")`. L’instance NLWeb traiterait cela, en utilisant sa base de données d’informations sur les restaurants (si chargée), et renverrait une réponse JSON structurée.

### Vous avez d’autres questions sur MCP/A2A/NLWeb ?

Rejoignez le [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pour rencontrer d’autres apprenants, participer aux heures de bureau et obtenir des réponses à vos questions sur les agents IA.

## Ressources

- [MCP pour débutants](https://aka.ms/mcp-for-beginners)  
- [Documentation MCP](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Répertoire NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Guides Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Avis de non-responsabilité** :  
Ce document a été traduit à l’aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue native doit être considéré comme la source faisant autorité. Pour les informations critiques, il est recommandé de faire appel à une traduction humaine professionnelle. Nous ne sommes pas responsables des malentendus ou des erreurs d’interprétation résultant de l’utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->