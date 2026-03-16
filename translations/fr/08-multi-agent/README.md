[![Conception multi-agent](../../../translated_images/fr/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Cliquez sur l'image ci-dessus pour regarder la vidéo de cette leçon)_

# Patrons de conception multi-agent

Dès que vous commencez à travailler sur un projet impliquant plusieurs agents, vous devrez prendre en compte le patron de conception multi-agent. Cependant, il peut ne pas être immédiatement évident quand passer à plusieurs agents et quels sont les avantages.

## Introduction

Dans cette leçon, nous cherchons à répondre aux questions suivantes :

- Quels sont les scénarios dans lesquels les multi-agents sont applicables ?
- Quels sont les avantages d'utiliser plusieurs agents plutôt qu'un seul agent effectuant plusieurs tâches ?
- Quels sont les éléments constitutifs de la mise en œuvre du patron de conception multi-agent ?
- Comment avoir de la visibilité sur la façon dont les multiples agents interagissent entre eux ?

## Objectifs d'apprentissage

Après cette leçon, vous devriez être capable de :

- Identifier les scénarios où les multi-agents sont applicables
- Reconnaître les avantages d'utiliser plusieurs agents plutôt qu'un agent unique.
- Comprendre les éléments constitutifs de la mise en œuvre du patron de conception multi-agent.

Quel est le tableau d'ensemble ?

*Les multi-agents sont un patron de conception qui permet à plusieurs agents de travailler ensemble pour atteindre un objectif commun*.

Ce patron est largement utilisé dans divers domaines, notamment la robotique, les systèmes autonomes et l'informatique distribuée.

## Scénarios où les multi-agents sont applicables

Alors, quels scénarios sont de bons cas d'utilisation pour les multi-agents ? La réponse est qu'il existe de nombreux scénarios où l'emploi de plusieurs agents est bénéfique, en particulier dans les cas suivants :

- **Grandes charges de travail** : Les grandes charges de travail peuvent être divisées en tâches plus petites et attribuées à différents agents, permettant un traitement parallèle et une exécution plus rapide. Un exemple de ceci est dans le cas d'une importante tâche de traitement de données.
- **Tâches complexes** : Les tâches complexes, comme les grandes charges de travail, peuvent être décomposées en sous-tâches plus petites et attribuées à différents agents, chacun se spécialisant dans un aspect spécifique de la tâche. Un bon exemple est le cas des véhicules autonomes où différents agents gèrent la navigation, la détection d'obstacles et la communication avec les autres véhicules.
- **Expertise diversifiée** : Différents agents peuvent avoir des expertises variées, leur permettant de gérer différents aspects d'une tâche plus efficacement qu'un seul agent. Pour ce cas, un bon exemple est le domaine de la santé où des agents peuvent gérer le diagnostic, les plans de traitement et le suivi des patients.

## Avantages d'utiliser plusieurs agents plutôt qu'un agent unique

Un système à agent unique peut bien fonctionner pour des tâches simples, mais pour des tâches plus complexes, l'utilisation de plusieurs agents peut offrir plusieurs avantages :

- **Spécialisation** : Chaque agent peut être spécialisé pour une tâche spécifique. L'absence de spécialisation dans un agent unique signifie que vous avez un agent qui peut tout faire mais qui peut être confus face à une tâche complexe. Il peut par exemple finir par effectuer une tâche pour laquelle il n'est pas le mieux adapté.
- **Scalabilité** : Il est plus facile de faire évoluer les systèmes en ajoutant plus d'agents plutôt qu'en surchargeant un seul agent.
- **Tolérance aux pannes** : Si un agent échoue, d'autres peuvent continuer à fonctionner, garantissant la fiabilité du système.

Prenons un exemple, réservons un voyage pour un utilisateur. Un système à agent unique devrait gérer tous les aspects du processus de réservation, de la recherche de vols à la réservation d'hôtels et de voitures de location. Pour y parvenir avec un seul agent, celui-ci devrait disposer d'outils pour gérer toutes ces tâches. Cela pourrait conduire à un système complexe et monolithique, difficile à maintenir et à faire évoluer. Un système multi-agent, en revanche, pourrait avoir différents agents spécialisés dans la recherche de vols, la réservation d'hôtels et des voitures de location. Cela rendrait le système plus modulaire, plus facile à maintenir et évolutif.

Comparez cela à une agence de voyages tenue comme un petit commerce familial versus une agence de voyages exploitée en franchise. Le petit commerce familial aurait un seul agent gérant tous les aspects du processus de réservation, tandis que la franchise aurait différents agents gérant différents aspects du processus de réservation.

## Éléments constitutifs pour implémenter le patron de conception multi-agent

Avant de pouvoir implémenter le patron de conception multi-agent, vous devez comprendre les éléments constitutifs qui composent le patron.

Rendons cela plus concret en regardant à nouveau l'exemple de la réservation d'un voyage pour un utilisateur. Dans ce cas, les éléments constitutifs incluraient :

- **Communication entre agents** : Les agents chargés de trouver des vols, de réserver des hôtels et des voitures de location doivent communiquer et partager des informations sur les préférences et contraintes de l'utilisateur. Vous devez décider des protocoles et méthodes pour cette communication. Concrètement, cela signifie que l'agent chargé de trouver des vols doit communiquer avec l'agent chargé de réserver des hôtels pour s'assurer que l'hôtel est réservé pour les mêmes dates que le vol. Cela signifie que les agents doivent partager des informations sur les dates de voyage de l'utilisateur, ce qui implique que vous devez décider *quels agents partagent les informations et comment ils les partagent*.
- **Mécanismes de coordination** : Les agents doivent coordonner leurs actions pour s'assurer que les préférences et contraintes de l'utilisateur sont respectées. Une préférence utilisateur pourrait être qu'il souhaite un hôtel proche de l'aéroport tandis qu'une contrainte pourrait être que les voitures de location ne sont disponibles qu'à l'aéroport. Cela signifie que l'agent chargé de réserver les hôtels doit se coordonner avec l'agent chargé de réserver les voitures de location pour s'assurer que les préférences et contraintes de l'utilisateur sont respectées. Cela implique que vous devez décider *comment les agents coordonnent leurs actions*.
- **Architecture des agents** : Les agents doivent avoir une structure interne pour prendre des décisions et apprendre de leurs interactions avec l'utilisateur. Cela signifie que l'agent chargé de trouver les vols doit disposer d'une structure interne pour décider quels vols recommander à l'utilisateur. Cela implique que vous devez décider *comment les agents prennent des décisions et apprennent de leurs interactions avec l'utilisateur*. Des exemples de la façon dont un agent apprend et s'améliore pourraient être que l'agent chargé de trouver des vols pourrait utiliser un modèle d'apprentissage automatique pour recommander des vols à l'utilisateur en fonction de ses préférences passées.
- **Visibilité des interactions multi-agents** : Vous devez avoir de la visibilité sur la façon dont les multiples agents interagissent entre eux. Cela signifie que vous devez disposer d'outils et de techniques pour suivre les activités et interactions des agents. Cela pourrait prendre la forme d'outils de journalisation et de surveillance, d'outils de visualisation et de métriques de performance.
- **Patrons multi-agents** : Il existe différents patrons pour implémenter des systèmes multi-agents, tels que des architectures centralisées, décentralisées et hybrides. Vous devez choisir le patron qui convient le mieux à votre cas d'utilisation.
- **Humain dans la boucle** : Dans la plupart des cas, vous aurez un humain dans la boucle et vous devez indiquer aux agents quand demander une intervention humaine. Cela pourrait prendre la forme d'un utilisateur demandant un hôtel ou un vol spécifique que les agents n'ont pas recommandé ou demandant une confirmation avant de réserver un vol ou un hôtel.

## Visibilité sur les interactions entre agents

Il est important d'avoir de la visibilité sur la façon dont les multiples agents interagissent entre eux. Cette visibilité est essentielle pour le débogage, l'optimisation et pour garantir l'efficacité globale du système. Pour y parvenir, vous devez disposer d'outils et de techniques pour suivre les activités et interactions des agents. Cela pourrait se présenter sous la forme d'outils de journalisation et de surveillance, d'outils de visualisation et de métriques de performance.

Par exemple, dans le cas de la réservation d'un voyage pour un utilisateur, vous pourriez avoir un tableau de bord affichant l'état de chaque agent, les préférences et contraintes de l'utilisateur, et les interactions entre les agents. Ce tableau de bord pourrait montrer les dates de voyage de l'utilisateur, les vols recommandés par l'agent des vols, les hôtels recommandés par l'agent hôtelier, et les voitures de location recommandées par l'agent de location. Cela vous donnerait une vue claire de la façon dont les agents interagissent entre eux et si les préférences et contraintes de l'utilisateur sont respectées.

Examinons chacun de ces aspects plus en détail.

- **Outils de journalisation et de surveillance** : Vous voulez journaliser chaque action entreprise par un agent. Une entrée de journal pourrait stocker des informations sur l'agent ayant effectué l'action, l'action effectuée, l'heure de l'action et le résultat de l'action. Ces informations peuvent ensuite être utilisées pour le débogage, l'optimisation et plus encore.
- **Outils de visualisation** : Les outils de visualisation peuvent vous aider à voir les interactions entre les agents de manière plus intuitive. Par exemple, vous pourriez avoir un graphe montrant le flux d'informations entre les agents. Cela pourrait vous aider à identifier les goulots d'étranglement, les inefficacités et d'autres problèmes dans le système.
- **Métriques de performance** : Les métriques de performance peuvent vous aider à suivre l'efficacité du système multi-agent. Par exemple, vous pourriez suivre le temps nécessaire pour accomplir une tâche, le nombre de tâches terminées par unité de temps, et la précision des recommandations faites par les agents. Ces informations peuvent vous aider à identifier des axes d'amélioration et à optimiser le système.

## Modèles multi-agents

Plongeons dans quelques modèles concrets que nous pouvons utiliser pour créer des applications multi-agents. Voici quelques patrons intéressants à considérer :

### Chat de groupe

Ce patron est utile lorsque vous souhaitez créer une application de chat de groupe où plusieurs agents peuvent communiquer entre eux. Les cas d'utilisation typiques pour ce patron incluent la collaboration d'équipe, le support client et les réseaux sociaux.

Dans ce patron, chaque agent représente un utilisateur dans le chat de groupe, et les messages sont échangés entre agents en utilisant un protocole de messagerie. Les agents peuvent envoyer des messages au chat de groupe, recevoir des messages du chat de groupe et répondre aux messages des autres agents.

Ce patron peut être implémenté en utilisant une architecture centralisée où tous les messages sont routés via un serveur central, ou une architecture décentralisée où les messages sont échangés directement.

![Chat de groupe](../../../translated_images/fr/multi-agent-group-chat.ec10f4cde556babd.webp)

### Transfert

Ce patron est utile lorsque vous souhaitez créer une application où plusieurs agents peuvent se transférer des tâches entre eux.

Les cas d'utilisation typiques pour ce patron incluent le support client, la gestion des tâches et l'automatisation des flux de travail.

Dans ce patron, chaque agent représente une tâche ou une étape d'un flux de travail, et les agents peuvent transférer des tâches à d'autres agents en fonction de règles prédéfinies.

![Hand off](../../../translated_images/fr/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Filtrage collaboratif

Ce patron est utile lorsque vous souhaitez créer une application où plusieurs agents peuvent collaborer pour faire des recommandations aux utilisateurs.

La raison pour laquelle vous voudriez que plusieurs agents collaborent est que chaque agent peut avoir une expertise différente et peut contribuer au processus de recommandation de différentes manières.

Prenons un exemple où un utilisateur souhaite une recommandation sur la meilleure action à acheter sur le marché boursier.

- **Expert sectoriel**:. Un agent pourrait être un expert dans un secteur spécifique.
- **Analyse technique**: Un autre agent pourrait être un expert en analyse technique.
- **Analyse fondamentale**: et un autre agent pourrait être un expert en analyse fondamentale. En collaborant, ces agents peuvent fournir une recommandation plus complète à l'utilisateur.

![Recommandation](../../../translated_images/fr/multi-agent-filtering.d959cb129dc9f608.webp)

## Scénario : processus de remboursement

Considérez un scénario où un client tente d'obtenir un remboursement pour un produit, il peut y avoir plusieurs agents impliqués dans ce processus mais divisons-le entre des agents spécifiques à ce processus et des agents généraux pouvant être utilisés dans d'autres processus.

**Agents spécifiques au processus de remboursement**:

Voici quelques agents qui pourraient être impliqués dans le processus de remboursement :

- **Agent client**: Cet agent représente le client et est responsable d'initier le processus de remboursement.
- **Agent vendeur**: Cet agent représente le vendeur et est responsable du traitement du remboursement.
- **Agent de paiement**: Cet agent représente le processus de paiement et est responsable de rembourser le paiement du client.
- **Agent de résolution**: Cet agent représente le processus de résolution et est responsable de résoudre les problèmes qui surviennent pendant le processus de remboursement.
- **Agent conformité**: Cet agent représente le processus de conformité et est responsable de s'assurer que le processus de remboursement respecte les réglementations et les politiques.

**Agents généraux**:

Ces agents peuvent être utilisés par d'autres parties de votre entreprise.

- **Agent d'expédition**: Cet agent représente le processus d'expédition et est responsable du renvoi du produit au vendeur. Cet agent peut être utilisé à la fois pour le processus de remboursement et pour l'expédition générale d'un produit via un achat par exemple.
- **Agent de feedback**: Cet agent représente le processus de feedback et est responsable de collecter les retours du client. Les retours peuvent être recueillis à tout moment et pas seulement pendant le processus de remboursement.
- **Agent d'escalade**: Cet agent représente le processus d'escalade et est responsable d'escalader les problèmes vers un niveau de support supérieur. Vous pouvez utiliser ce type d'agent pour tout processus où vous devez escalader un problème.
- **Agent de notification**: Cet agent représente le processus de notification et est responsable d'envoyer des notifications au client à diverses étapes du processus de remboursement.
- **Agent d'analyse**: Cet agent représente le processus analytique et est responsable d'analyser les données liées au processus de remboursement.
- **Agent d'audit**: Cet agent représente le processus d'audit et est responsable d'auditer le processus de remboursement afin de s'assurer qu'il est correctement exécuté.
- **Agent de rapports**: Cet agent représente le processus de reporting et est responsable de générer des rapports sur le processus de remboursement.
- **Agent de connaissances**: Cet agent représente le processus de gestion des connaissances et est responsable de maintenir une base de connaissances d'informations liées au processus de remboursement. Cet agent pourrait être informé à la fois sur les remboursements et sur d'autres parties de votre entreprise.
- **Agent de sécurité**: Cet agent représente le processus de sécurité et est responsable d'assurer la sécurité du processus de remboursement.
- **Agent qualité**: Cet agent représente le processus qualité et est responsable d'assurer la qualité du processus de remboursement.

Il y a pas mal d'agents listés précédemment, tant pour le processus de remboursement spécifique que pour les agents généraux qui peuvent être utilisés dans d'autres parties de votre entreprise. J'espère que cela vous donne une idée de la façon dont vous pouvez décider quels agents utiliser dans votre système multi-agent.

## Exercice

Concevez un système multi-agent pour un processus de support client. Identifiez les agents impliqués dans le processus, leurs rôles et responsabilités, et comment ils interagissent entre eux. Prenez en compte à la fois les agents spécifiques au processus de support client et les agents généraux pouvant être utilisés dans d'autres parties de votre entreprise.
> Réfléchissez avant de lire la solution suivante, vous pourriez avoir besoin de plus d'agents que vous ne le pensez.
> 
> ASTUCE: Pensez aux différentes étapes du processus de support client et considérez également les agents nécessaires pour tout système.

## Solution

[Solution](./solution/solution.md)

## Knowledge checks

Question: Quand devriez-vous envisager d'utiliser des agents multiples?

- [ ] A1: Lorsque vous avez une charge de travail faible et une tâche simple.
- [ ] A2: Lorsque vous avez une charge de travail importante
- [ ] A3: Lorsque vous avez une tâche simple.

[Solution quiz](./solution/solution-quiz.md)

## Summary

Dans cette leçon, nous avons examiné le modèle de conception multi-agent, y compris les scénarios où les multi-agents sont applicables, les avantages d'utiliser plusieurs agents plutôt qu'un seul agent, les éléments constitutifs de la mise en œuvre du modèle de conception multi-agent, et comment avoir de la visibilité sur la façon dont les différents agents interagissent entre eux.

### Got More Questions about the Multi-Agent Design Pattern?

Join the [Discord de Microsoft Foundry](https://aka.ms/ai-agents/discord) to meet with other learners, attend office hours and get your AI Agents questions answered.

## Additional resources

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Modèles de conception AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Modèles de conception agentiques</a>


## Previous Lesson

[Conception de planification](../07-planning-design/README.md)

## Next Lesson

[Métacognition dans les agents IA](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Avis de non-responsabilité :
Ce document a été traduit à l'aide du service de traduction par IA Co-op Translator (https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d'assurer l'exactitude, veuillez noter que les traductions automatisées peuvent comporter des erreurs ou des inexactitudes. Le document original dans sa langue d'origine doit être considéré comme la source faisant foi. Pour les informations critiques, il est recommandé de recourir à une traduction professionnelle réalisée par un traducteur humain. Nous déclinons toute responsabilité pour tout malentendu ou mauvaise interprétation résultant de l'utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->