# Mémoire pour les agents IA  
[![Agent Memory](../../../translated_images/fr/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Lorsqu'on parle des avantages uniques de la création d'agents IA, deux éléments sont principalement abordés : la capacité d'appeler des outils pour accomplir des tâches et la capacité de s'améliorer avec le temps. La mémoire est à la base de la création d'un agent auto-améliorant qui peut offrir de meilleures expériences à nos utilisateurs.

Dans cette leçon, nous examinerons ce qu'est la mémoire pour les agents IA et comment nous pouvons la gérer et l'utiliser au bénéfice de nos applications.

## Introduction

Cette leçon couvrira :

• **Comprendre la mémoire des agents IA** : Qu'est-ce que la mémoire et pourquoi elle est essentielle pour les agents.

• **Implémenter et stocker la mémoire** : Méthodes pratiques pour ajouter des capacités de mémoire à vos agents IA, en mettant l’accent sur la mémoire à court terme et à long terme.

• **Rendre les agents IA auto-améliorables** : Comment la mémoire permet aux agents d’apprendre des interactions passées et s’améliorer au fil du temps.

## Implémentations disponibles

Cette leçon inclut deux tutoriels complets sous forme de notebooks :

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)** : Implémente la mémoire en utilisant Mem0 et Azure AI Search avec le framework Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)** : Implémente une mémoire structurée avec Cognee, construisant automatiquement un graphe de connaissances soutenu par des embeddings, visualisant le graphe et une récupération intelligente

## Objectifs d’apprentissage

Après avoir terminé cette leçon, vous saurez comment :

• **Différencier les différents types de mémoire des agents IA**, incluant la mémoire de travail, mémoire à court terme, mémoire à long terme ainsi que des formes spécialisées comme la mémoire de persona et la mémoire épisodique.

• **Implémenter et gérer la mémoire à court terme et à long terme pour les agents IA** en utilisant le framework Semantic Kernel, en exploitant des outils comme Mem0, Cognee, la mémoire Whiteboard et en intégrant Azure AI Search.

• **Comprendre les principes derrière les agents IA auto-améliorables** et comment les systèmes robustes de gestion de la mémoire favorisent un apprentissage et une adaptation continus.

## Comprendre la mémoire des agents IA

Au cœur, **la mémoire pour les agents IA désigne les mécanismes qui leur permettent de conserver et de rappeler des informations**. Ces informations peuvent être des détails spécifiques à une conversation, des préférences utilisateur, des actions passées ou même des schémas appris.

Sans mémoire, les applications IA sont souvent sans état, ce qui signifie que chaque interaction commence à zéro. Cela mène à une expérience utilisateur répétitive et frustrante où l’agent « oublie » le contexte ou les préférences précédentes.

### Pourquoi la mémoire est-elle importante ?

L’intelligence d’un agent est intimement liée à sa capacité à se rappeler et à utiliser les informations passées. La mémoire permet aux agents d’être :

• **Réfléchis** : Apprendre de leurs actions et résultats passés.

• **Interactifs** : Maintenir le contexte au cours d’une conversation en cours.

• **Proactifs et réactifs** : Anticiper les besoins ou répondre correctement en se basant sur les données historiques.

• **Autonomes** : Fonctionner plus indépendamment en puisant dans des connaissances stockées.

Le but de la mise en place de la mémoire est de rendre les agents plus **fiables et capables**.

### Types de mémoire

#### Mémoire de travail

Pensez-y comme un brouillon que l’agent utilise durant une tâche ou un processus de pensée en cours. Elle contient les informations immédiates nécessaires pour calculer l’étape suivante.

Pour les agents IA, la mémoire de travail capture souvent les informations les plus pertinentes d’une conversation, même si l’historique complet est long ou tronqué. Elle se concentre sur l’extraction d’éléments clés tels que les exigences, propositions, décisions et actions.

**Exemple de mémoire de travail**

Dans un agent de réservation de voyage, la mémoire de travail pourrait contenir la demande actuelle de l’utilisateur, comme « Je veux réserver un voyage à Paris ». Cette exigence spécifique est maintenue dans le contexte immédiat de l’agent pour guider l’interaction en cours.

#### Mémoire à court terme

Ce type de mémoire conserve les informations pendant une seule conversation ou session. C’est le contexte du chat en cours, permettant à l’agent de se référer aux tours précédents du dialogue.

**Exemple de mémoire à court terme**

Si un utilisateur demande « Combien coûte un vol pour Paris ? » et enchaîne avec « Et pour l’hébergement là-bas ? », la mémoire à court terme assure que l’agent sait que « là-bas » se réfère à « Paris » dans la même conversation.

#### Mémoire à long terme

Ce sont des informations qui persistent sur plusieurs conversations ou sessions. Elles permettent aux agents de se souvenir des préférences utilisateur, des interactions historiques ou des connaissances générales sur des périodes étendues. Ceci est important pour la personnalisation.

**Exemple de mémoire à long terme**

Une mémoire à long terme pourrait retenir que « Ben aime le ski et les activités en plein air, préfère son café avec vue sur la montagne, et souhaite éviter les pistes avancées à cause d’une blessure passée ». Ces informations, apprises lors d’interactions précédentes, influencent les recommandations lors de futures sessions de planification de voyage, les rendant très personnalisées.

#### Mémoire de persona

Ce type de mémoire spécialisé aide un agent à développer une « personnalité » ou un « persona » cohérents. Il permet à l’agent de retenir des détails sur lui-même ou son rôle prévu, rendant les interactions plus fluides et ciblées.

**Exemple de mémoire de persona**

Si l’agent de voyage est conçu pour être un « expert en planification de ski », la mémoire de persona pourrait renforcer ce rôle, influençant ses réponses pour correspondre au ton et aux connaissances d’un expert.

#### Mémoire de workflow/épisodique

Cette mémoire stocke la séquence d’étapes qu’un agent suit durant une tâche complexe, incluant succès et échecs. C’est comme se rappeler des « épisodes » ou expériences passées pour en tirer des leçons.

**Exemple de mémoire épisodique**

Si l’agent a tenté de réserver un vol spécifique mais a échoué en raison d’une indisponibilité, la mémoire épisodique pourrait enregistrer cet échec, permettant à l’agent d’essayer des alternatives ou d’informer l’utilisateur de façon plus informée lors d’une tentative ultérieure.

#### Mémoire d’entité

Cela implique l’extraction et la mémorisation d’entités spécifiques (personnes, lieux, objets) et d’événements issus des conversations. Cela permet à l’agent de construire une compréhension structurée des éléments clés évoqués.

**Exemple de mémoire d’entité**

D’une conversation sur un voyage passé, l’agent pourrait extraire « Paris », « Tour Eiffel » et « dîner au restaurant Le Chat Noir » comme entités. Lors d’une interaction future, l’agent pourrait se rappeler « Le Chat Noir » et proposer de faire une nouvelle réservation là-bas.

#### RAG structuré (Retrieval Augmented Generation)

Bien que le RAG soit une technique plus large, le « RAG structuré » est mis en avant comme une technologie mémoire puissante. Il extrait des informations denses et structurées de diverses sources (conversations, emails, images) et les utilise pour améliorer la précision, le rappel et la vitesse des réponses. Contrairement au RAG classique qui se base uniquement sur la similarité sémantique, le RAG structuré exploite la structure intrinsèque de l’information.

**Exemple de RAG structuré**

Plutôt que de simplement faire correspondre des mots-clés, le RAG structuré pourrait analyser les détails de vol (destination, date, heure, compagnie aérienne) à partir d’un email et les stocker de manière structurée. Cela permet des requêtes précises comme « Quel vol ai-je réservé pour Paris mardi ? »

## Implémenter et stocker la mémoire

Implémenter la mémoire pour les agents IA implique un processus systématique de **gestion de la mémoire**, qui comprend la génération, le stockage, la récupération, l’intégration, la mise à jour et même « l’oubli » (ou suppression) d’informations. La récupération est un aspect particulièrement crucial.

### Outils mémoire spécialisés

#### Mem0

Une façon de stocker et de gérer la mémoire d’un agent consiste à utiliser des outils spécialisés comme Mem0. Mem0 fonctionne comme une couche de mémoire persistante, permettant aux agents de rappeler les interactions pertinentes, stocker préférences utilisateur et contexte factuel, et apprendre de leurs succès et échecs au fil du temps. L’idée est que des agents sans état deviennent des agents ayant de l’état.

Cela fonctionne à travers un **pipeline mémoire en deux phases : extraction et mise à jour**. D’abord, les messages ajoutés à un fil de discussion d’agent sont envoyés au service Mem0, qui utilise un grand modèle de langage (LLM) pour résumer l’historique de conversation et extraire de nouveaux souvenirs. Ensuite, une phase de mise à jour pilotée par un LLM décide d’ajouter, modifier ou supprimer ces souvenirs, les stockant dans un magasin de données hybride pouvant inclure des bases vectorielles, graphiques et clé-valeur. Ce système supporte différents types de mémoire et peut incorporer une mémoire graphique pour gérer les relations entre entités.

#### Cognee

Une autre approche puissante consiste à utiliser **Cognee**, une mémoire sémantique open source pour agents IA qui transforme des données structurées et non structurées en graphes de connaissances interrogeables soutenus par des embeddings. Cognee fournit une **architecture à double magasin** combinant recherche par similarité vectorielle et relations graphiques, permettant aux agents de comprendre non seulement quelle information est similaire, mais aussi comment les concepts sont liés entre eux.

Il excelle dans la **récupération hybride** qui combine similarité vectorielle, structure graphique et raisonnement LLM – depuis la simple recherche de morceaux bruts jusqu’à la réponse à des questions conscientes du graphe. Le système maintient une **mémoire vivante** qui évolue et grandit tout en restant interrogeable en tant que graphe unique connecté, supportant à la fois le contexte de session à court terme et la mémoire persistante à long terme.

Le tutoriel du notebook Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) démontre la construction de cette couche mémoire unifiée, avec des exemples pratiques d’ingestion de sources de données diverses, visualisation du graphe de connaissance et interrogation avec différentes stratégies de recherche adaptées aux besoins spécifiques des agents.

### Stocker la mémoire avec RAG

Au-delà des outils mémoire spécialisés comme Mem0, vous pouvez exploiter des services de recherche puissants comme **Azure AI Search comme backend pour stocker et récupérer la mémoire**, surtout pour le RAG structuré.

Cela vous permet d’ancrer les réponses de votre agent à vos propres données, garantissant des réponses plus pertinentes et précises. Azure AI Search peut être utilisé pour stocker des mémoires de voyage spécifiques à un utilisateur, des catalogues produits ou toute autre connaissance métier.

Azure AI Search supporte des capacités comme le **RAG structuré**, qui excelle pour extraire et récupérer des informations denses et structurées à partir de larges ensembles de données comme des historiques de conversation, emails, voire images. Ceci fournit une « précision et un rappel surhumains » comparé aux approches classiques de découpage de texte et embeddings.

## Rendre les agents IA auto-améliorables

Un schéma courant pour les agents auto-améliorables implique l’introduction d’un **« agent de connaissance »**. Cet agent distinct observe la conversation principale entre l’utilisateur et l’agent principal. Son rôle est de :

1. **Identifier les informations précieuses** : Déterminer si une partie de la conversation mérite d’être conservée comme connaissance générale ou préférence spécifique.

2. **Extraire et résumer** : Distiller l’apprentissage essentiel ou la préférence de la conversation.

3. **Stocker dans une base de connaissances** : Conserver cette information extraite, souvent dans une base vectorielle, pour qu’elle soit récupérable ultérieurement.

4. **Augmenter les requêtes futures** : Lorsque l’utilisateur initie une nouvelle requête, l’agent de connaissance récupère les informations stockées pertinentes et les ajoute à l’invite utilisateur, fournissant un contexte crucial à l’agent principal (similaire au RAG).

### Optimisations pour la mémoire

• **Gestion de la latence** : Pour éviter de ralentir les interactions utilisateur, un modèle moins coûteux et plus rapide peut être utilisé initialement pour vérifier rapidement la valeur des informations à stocker ou récupérer, n’invoquant le processus d’extraction/récupération plus complexe que si nécessaire.

• **Maintenance de la base de connaissances** : Pour une base de connaissances en croissance, les informations moins fréquemment utilisées peuvent être déplacées en « stockage froid » pour gérer les coûts.

## Vous avez d’autres questions sur la mémoire des agents ?

Rejoignez le [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pour rencontrer d’autres apprenants, assister aux heures de bureau et obtenir des réponses à vos questions sur les agents IA.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Avertissement** :  
Ce document a été traduit à l’aide du service de traduction automatisée [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d’origine doit être considéré comme la source faisant foi. Pour toute information critique, une traduction professionnelle réalisée par un humain est recommandée. Nous déclinons toute responsabilité en cas de malentendus ou de mauvaises interprétations résultant de l’utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->