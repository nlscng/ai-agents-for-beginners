# Agents IA en Production : Observabilité et Évaluation

[![Agents IA en Production](../../../translated_images/fr/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

À mesure que les agents IA passent de prototypes expérimentaux à des applications réelles, la capacité à comprendre leur comportement, surveiller leurs performances et évaluer systématiquement leurs résultats devient importante.

## Objectifs d'apprentissage

Après avoir terminé cette leçon, vous saurez/comment comprendre :
- Les concepts clés de l'observabilité et de l'évaluation des agents
- Les techniques pour améliorer les performances, les coûts et l'efficacité des agents
- Ce qu'il faut évaluer et comment évaluer systématiquement vos agents IA
- Comment contrôler les coûts lors du déploiement des agents IA en production
- Comment instrumenter des agents construits avec AutoGen

L'objectif est de vous équiper avec les connaissances nécessaires pour transformer vos agents "boîte noire" en systèmes transparents, gérables et fiables.

_**Note :** Il est important de déployer des agents IA sûrs et dignes de confiance. Consultez également la leçon [Construire des Agents IA Dignes de Confiance](./06-building-trustworthy-agents/README.md)._

## Traces et Spans

Les outils d'observabilité tels que [Langfuse](https://langfuse.com/) ou [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) représentent généralement les exécutions d'agents sous forme de traces et de spans.

- **Trace** représente une tâche complète de l’agent du début à la fin (comme traiter une requête utilisateur).
- **Spans** sont les étapes individuelles au sein de la trace (comme l’appel à un modèle de langage ou la récupération de données).

![Arbre de trace dans Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Sans observabilité, un agent IA peut sembler être une "boîte noire" – son état interne et son raisonnement sont opaques, rendant difficile le diagnostic des problèmes ou l’optimisation des performances. Avec l'observabilité, les agents deviennent des "boîtes en verre", offrant une transparence vitale pour instaurer la confiance et assurer qu’ils fonctionnent comme prévu. 

## Pourquoi l’Observabilité est Importante en Environnements de Production

La transition des agents IA vers les environnements de production introduit de nouveaux défis et exigences. L'observabilité n’est plus un simple « plus » mais une capacité critique :

*   **Débogage et Analyse des Causes Racines** : Lorsqu’un agent échoue ou produit une sortie inattendue, les outils d’observabilité fournissent les traces nécessaires pour localiser la source de l’erreur. Ceci est particulièrement important dans les agents complexes pouvant impliquer plusieurs appels LLM, interactions avec des outils et logique conditionnelle.
*   **Gestion de la Latence et des Coûts** : Les agents IA s’appuient souvent sur des LLM et d’autres API externes facturés à la token ou à l’appel. L’observabilité permet de suivre précisément ces appels, aidant à identifier les opérations trop lentes ou coûteuses. Cela permet aux équipes d’optimiser les prompts, choisir des modèles plus efficaces ou repenser les workflows pour gérer les coûts opérationnels et garantir une bonne expérience utilisateur.
*   **Confiance, Sécurité et Conformité** : Dans de nombreuses applications, il est important de s’assurer que les agents se comportent de manière sûre et éthique. L’observabilité fournit une traçabilité des actions et décisions des agents. Cela peut être utilisé pour détecter et atténuer des problèmes comme l'injection de prompt, la génération de contenu nuisible ou la mauvaise gestion des informations personnellement identifiables (PII). Par exemple, vous pouvez revoir les traces pour comprendre pourquoi un agent a donné une certaine réponse ou utilisé un outil spécifique.
*   **Boucles d’Amélioration Continue** : Les données d’observabilité sont la base d’un processus de développement itératif. En surveillant la performance des agents dans le monde réel, les équipes peuvent identifier des axes d’amélioration, collecter des données pour affiner les modèles et valider l’impact des modifications. Cela crée une boucle de rétroaction où les insights de la production issus de l’évaluation en ligne alimentent l’expérimentation et le raffinement hors ligne, menant à une meilleure performance progressive des agents.

## Principaux Indicateurs à Suivre

Pour surveiller et comprendre le comportement des agents, une gamme de métriques et signaux doit être suivie. Bien que les métriques spécifiques puissent varier selon l’objectif de l’agent, certaines sont universellement importantes.

Voici quelques-unes des métriques les plus courantes surveillées par les outils d’observabilité :

**Latence :** À quelle vitesse l’agent répond-il ? Des temps d’attente longs impactent négativement l’expérience utilisateur. Vous devez mesurer la latence pour les tâches et les étapes individuelles en retraçant les exécutions de l’agent. Par exemple, un agent prenant 20 secondes pour tous les appels modèles pourrait être accéléré en utilisant un modèle plus rapide ou en exécutant les appels en parallèle.

**Coûts :** Quel est le coût par exécution d’agent ? Les agents IA s’appuient sur des appels LLM facturés par token ou des API externes. Une utilisation fréquente d’outils ou plusieurs prompts peuvent rapidement augmenter les coûts. Par exemple, si un agent appelle un LLM cinq fois pour une amélioration marginale de qualité, vous devez évaluer si le coût est justifié ou si vous pouvez réduire le nombre d’appels ou utiliser un modèle moins cher. La surveillance en temps réel peut aussi aider à identifier des pics inattendus (ex. bugs causant des boucles API excessives).

**Erreurs de Requête :** Combien de requêtes l’agent a-t-il échoué ? Cela peut inclure des erreurs d’API ou des appels d’outil échoués. Pour renforcer la robustesse de votre agent en production, vous pouvez ensuite configurer des solutions de secours ou des réessais. Par ex. si le fournisseur LLM A est indisponible, vous basculez vers le fournisseur B en secours.

**Retour Utilisateur :** Implémenter des évaluations directes utilisateurs fournit des informations précieuses. Cela peut inclure des évaluations explicites (👍pouce levé/👎pouce baissé, ⭐1-5 étoiles) ou des commentaires textuels. Un retour négatif constant doit vous alerter, signe que l’agent ne fonctionne pas comme attendu.

**Retour Utilisateur Implicite :** Les comportements utilisateurs fournissent un retour indirect même sans notes explicites. Cela peut inclure la reformulation immédiate d’une question, des requêtes répétées ou un clic sur un bouton de réessai. Par ex., si vous constatez que les utilisateurs posent à plusieurs reprises la même question, c’est un signe que l’agent ne fonctionne pas comme prévu.

**Précision :** À quelle fréquence l’agent produit-il des sorties correctes ou souhaitables ? Les définitions de précision varient (ex. exactitude de résolution de problèmes, précision de récupération d’informations, satisfaction utilisateur). La première étape est de définir ce que signifie la réussite pour votre agent. Vous pouvez suivre la précision via des contrôles automatisés, des scores d’évaluation ou des labels de complétion de tâche. Par exemple, marquer les traces comme « réussi » ou « échoué ».

**Métriques d’Évaluation Automatisées :** Vous pouvez aussi configurer des évaluations automatisées. Par exemple, vous pouvez utiliser un LLM pour évaluer la sortie de l’agent, par ex. si elle est utile, précise ou non. Il existe également plusieurs bibliothèques open source pour évaluer différents aspects de l’agent. Ex. [RAGAS](https://docs.ragas.io/) pour agents RAG ou [LLM Guard](https://llm-guard.com/) pour détecter un langage nuisible ou une injection de prompt.

Dans la pratique, une combinaison de ces métriques offre la meilleure couverture de la santé d’un agent IA. Dans ce [notebook d’exemple du chapitre](./code_samples/10_autogen_evaluation.ipynb), nous vous montrerons à quoi ces métriques ressemblent dans des exemples réels, mais d’abord, voyons à quoi ressemble un workflow typique d’évaluation.

## Instrumenter votre Agent

Pour collecter des données de traçage, vous devez instrumenter votre code. L’objectif est d’instrumenter le code de l’agent afin d’émettre des traces et métriques pouvant être capturées, traitées et visualisées par une plateforme d’observabilité.

**OpenTelemetry (OTel) :** [OpenTelemetry](https://opentelemetry.io/) s’est imposé comme un standard industriel pour l’observabilité LLM. Il fournit un ensemble d’API, SDK et outils pour générer, collecter et exporter des données télémétriques.

Il existe de nombreuses bibliothèques d’instrumentation qui enveloppent les frameworks d’agents existants et facilitent l’export de spans OpenTelemetry vers un outil d’observabilité. Voici un exemple d’instrumentation d’un agent AutoGen avec la [bibliothèque d’instrumentation OpenLit](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

Le [notebook d’exemple](./code_samples/10_autogen_evaluation.ipynb) de ce chapitre démontrera comment instrumenter votre agent AutoGen.

**Création Manuelle de Spans :** Bien que les bibliothèques d’instrumentation fournissent une bonne base, il y a parfois des cas où des informations plus détaillées ou personnalisées sont nécessaires. Vous pouvez créer des spans manuellement pour ajouter une logique applicative personnalisée. Plus important encore, ils peuvent enrichir les spans créés automatiquement ou manuellement avec des attributs personnalisés (aussi appelés tags ou métadonnées). Ces attributs peuvent inclure des données métier, des calculs intermédiaires ou tout contexte utile au débogage ou à l’analyse, tel que `user_id`, `session_id` ou `model_version`.

Exemple de création manuelle de traces et spans avec le [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3) :

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Évaluation de l’Agent

L’observabilité nous fournit des métriques, mais l’évaluation est le processus d’analyse de ces données (et de réalisation de tests) pour déterminer la performance d’un agent IA et les améliorations possibles. En d’autres termes, une fois que vous avez ces traces et métriques, comment les utiliser pour juger l’agent et prendre des décisions ?

L’évaluation régulière est importante car les agents IA sont souvent non déterministes et peuvent évoluer (via des mises à jour ou un dérive du comportement du modèle) – sans évaluation, vous ne sauriez pas si votre “agent intelligent” fait réellement bien son travail ou s’il a régressé.

Il existe deux catégories d’évaluations pour les agents IA : **évaluation en ligne** et **évaluation hors ligne**. Les deux sont précieuses et se complètent. Nous commençons généralement par l’évaluation hors ligne, qui est l’étape minimale nécessaire avant de déployer un agent.

### Évaluation Hors Ligne

![Éléments de dataset dans Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

Cela consiste à évaluer l’agent dans un contexte contrôlé, généralement en utilisant des jeux de données de test, et non des requêtes utilisateurs en direct. Vous utilisez des datasets sélectionnés où vous connaissez la sortie attendue ou le comportement correct, puis vous exécutez votre agent dessus.

Par exemple, si vous avez construit un agent de résolution de problèmes mathématiques, vous pourriez disposer d’un [dataset de test](https://huggingface.co/datasets/gsm8k) de 100 problèmes aux réponses connues. L’évaluation hors ligne se fait souvent lors du développement (et peut être intégrée dans des pipelines CI/CD) pour vérifier les améliorations ou prévenir les régressions. L’avantage est que c’est **répétable et vous pouvez obtenir des métriques précises de précision grâce à une vérité terrain**. Vous pouvez aussi simuler des requêtes utilisateurs et mesurer les réponses de l’agent face aux réponses idéales ou utiliser des métriques automatisées comme décrit plus haut.

Le principal défi avec l’évaluation hors ligne est de garantir que votre jeu de test est complet et reste pertinent – l’agent pourrait bien performer sur un jeu de test fixe, mais rencontrer des requêtes très différentes en production. Par conséquent, vous devez maintenir à jour les jeux de test avec de nouveaux cas limites et exemples reflétant les scénarios réels. Un mélange de petits cas « smoke test » et de larges jeux d’évaluation est utile : petits ensembles pour des contrôles rapides et plus grands pour des métriques plus globales.

### Évaluation en Ligne

![Vue d’ensemble des métriques d’observabilité](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Cela désigne l’évaluation de l’agent dans un environnement réel, en direct, c’est-à-dire lors de son usage en production. L’évaluation en ligne consiste à surveiller la performance de l’agent pendant les interactions utilisateurs réelles et à analyser continuellement les résultats.

Par exemple, vous pouvez suivre les taux de réussite, les scores de satisfaction utilisateur ou d’autres métriques sur le trafic live. L’avantage de l’évaluation en ligne est qu’elle **capte des phénomènes que vous ne pourriez pas anticiper en laboratoire** – vous pouvez observer la dérive du modèle au fil du temps (si l’efficacité de l’agent décline avec l’évolution des entrées) et détecter des requêtes ou situations inattendues qui n’étaient pas présentes dans vos données de test. Elle donne une image réelle du comportement de l’agent en conditions réelles.

L’évaluation en ligne implique souvent la collecte de retours utilisateurs implicites et explicites, comme discuté, et éventuellement la réalisation de tests en aveugle ou tests A/B (où une nouvelle version de l’agent tourne en parallèle pour comparaison avec l’ancienne). Le défi est d’obtenir des labels ou scores fiables pour les interactions en direct – vous pouvez vous appuyer sur le feedback utilisateur ou des métriques en aval (ex. l’utilisateur a-t-il cliqué sur le résultat).

### Combinaison des Deux

Les évaluations en ligne et hors ligne ne sont pas exclusives ; elles se complètent fortement. Les insights issus de la surveillance en ligne (ex. nouveaux types de requêtes où l’agent est faible) peuvent être utilisés pour enrichir et améliorer les datasets de test hors ligne. À l’inverse, les agents qui performent bien dans les tests hors ligne peuvent être déployés plus sereinement et suivis en ligne.

En fait, de nombreuses équipes adoptent une boucle :

_évaluer hors ligne -> déployer -> monitorer en ligne -> collecter de nouveaux cas d’échec -> ajouter au dataset hors ligne -> affiner l’agent -> répéter_.

## Problèmes Courants

Au fur et à mesure que vous déployez des agents IA en production, vous pouvez rencontrer divers défis. Voici quelques problèmes courants et leurs solutions potentielles :

| **Problème**    | **Solution Potentielle**   |
| ------------- | ------------------ |
| L’agent IA n’exécute pas les tâches de manière cohérente | - Affiner le prompt donné à l’agent IA ; être clair sur les objectifs.<br>- Identifier si diviser les tâches en sous-tâches et les gérer par plusieurs agents aide. |
| L’agent IA entre dans des boucles continues | - Assurez-vous d’avoir des conditions claires de terminaison pour que l’agent sache quand arrêter le processus.<br>- Pour les tâches complexes nécessitant raisonnement et planification, utilisez un modèle plus grand spécialisé dans le raisonnement. |
| Les appels aux outils de l’agent IA ne fonctionnent pas bien | - Tester et valider la sortie des outils en dehors du système agent.<br>- Affiner les paramètres définis, les prompts et le nommage des outils. |
| Le système multi-agent ne fonctionne pas de manière cohérente | - Affiner les prompts donnés à chaque agent pour qu’ils soient spécifiques et distincts.<br>- Construire un système hiérarchique utilisant un agent « routeur » ou contrôleur pour déterminer quel agent est le bon. |

Beaucoup de ces problèmes peuvent être identifiés plus efficacement grâce à l’observabilité. Les traces et métriques évoquées précédemment aident à localiser précisément où dans le workflow de l’agent les problèmes surviennent, rendant le débogage et l’optimisation beaucoup plus efficaces.

## Gestion des Coûts
Voici quelques stratégies pour gérer les coûts de déploiement des agents IA en production :

**Utiliser des modèles plus petits :** Les petits modèles de langage (SLM) peuvent bien fonctionner pour certains cas d'utilisation agentiques et réduiront considérablement les coûts. Comme mentionné précédemment, construire un système d'évaluation pour déterminer et comparer les performances par rapport aux modèles plus grands est la meilleure façon de comprendre comment un SLM fonctionnera sur votre cas d'utilisation. Envisagez d'utiliser des SLM pour des tâches plus simples comme la classification d'intention ou l'extraction de paramètres, tout en réservant les modèles plus grands pour un raisonnement complexe.

**Utiliser un modèle de routage :** Une stratégie similaire consiste à utiliser une diversité de modèles et de tailles. Vous pouvez utiliser un LLM/SLM ou une fonction serverless pour router les requêtes en fonction de leur complexité vers les modèles les mieux adaptés. Cela aidera également à réduire les coûts tout en garantissant la performance sur les bonnes tâches. Par exemple, router les requêtes simples vers des modèles plus petits et plus rapides, et n’utiliser les modèles coûteux et volumineux que pour les tâches de raisonnement complexes.

**Mise en cache des réponses :** Identifier les requêtes et tâches courantes et fournir les réponses avant qu’elles ne passent par votre système agentique est un excellent moyen de réduire le volume de requêtes similaires. Vous pouvez même implémenter un flux pour identifier à quel point une requête est similaire à vos requêtes en cache en utilisant des modèles d’IA plus basiques. Cette stratégie peut réduire significativement les coûts pour les questions fréquemment posées ou les flux de travail communs.

## Voyons comment cela fonctionne en pratique

Dans le [notebook exemple de cette section](./code_samples/10_autogen_evaluation.ipynb), nous verrons des exemples de l’utilisation des outils d’observabilité pour surveiller et évaluer notre agent.


### Vous avez d’autres questions sur les agents IA en production ?

Rejoignez le [Discord Microsoft Foundry](https://aka.ms/ai-agents/discord) pour rencontrer d’autres apprenants, assister aux heures de bureau et obtenir des réponses à vos questions sur les agents IA.

## Leçon précédente

[Metacognition Design Pattern](../09-metacognition/README.md)

## Prochaine leçon

[Agentic Protocols](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Avertissement** :  
Ce document a été traduit à l’aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d’origine doit être considéré comme la source faisant autorité. Pour les informations critiques, il est recommandé de faire appel à une traduction professionnelle réalisée par un humain. Nous déclinons toute responsabilité en cas de malentendus ou d’interprétations erronées résultant de l’utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->