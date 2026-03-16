[![Modèle de conception de planification](../../../translated_images/fr/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Cliquez sur l'image ci-dessus pour regarder la vidéo de cette leçon)_

# Conception de la planification

## Introduction

Cette leçon couvrira

* Définir un objectif global clair et décomposer une tâche complexe en tâches gérables.
* Exploiter des sorties structurées pour des réponses plus fiables et lisibles par machine.
* Appliquer une approche pilotée par les événements pour gérer des tâches dynamiques et des entrées inattendues.

## Objectifs d'apprentissage

Après avoir terminé cette leçon, vous comprendrez :

* Identifier et définir un objectif global pour un agent d'IA, en veillant à ce qu'il sache clairement ce qu'il doit accomplir.
* Décomposer une tâche complexe en sous-tâches gérables et les organiser dans une séquence logique.
* Fournir aux agents les bons outils (par exemple, outils de recherche ou d'analyse de données), décider quand et comment les utiliser, et gérer les situations imprévues qui surviennent.
* Évaluer les résultats des sous-tâches, mesurer les performances et itérer les actions pour améliorer le résultat final.

## Définir l'objectif global et décomposer une tâche

![Définir les objectifs et les tâches](../../../translated_images/fr/defining-goals-tasks.d70439e19e37c47a.webp)

La plupart des tâches du monde réel sont trop complexes pour être traitées en une seule étape. Un agent d'IA a besoin d'un objectif concis pour guider sa planification et ses actions. Par exemple, considérez l'objectif :

    "Générer un itinéraire de voyage de 3 jours."

Bien qu'il soit simple à énoncer, il nécessite tout de même un affinage. Plus l'objectif est clair, mieux l'agent (et tout collaborateur humain) peut se concentrer sur l'obtention du bon résultat, comme la création d'un itinéraire complet avec options de vol, recommandations d'hôtels et suggestions d'activités.

### Décomposition de la tâche

Les tâches vastes ou complexes deviennent plus gérables lorsqu'elles sont divisées en sous-tâches plus petites et orientées objectifs.
Pour l'exemple d'un itinéraire de voyage, vous pouvez décomposer l'objectif en :

* Réservation de vol
* Réservation d'hôtel
* Location de voiture
* Personnalisation

Chaque sous-tâche peut ensuite être traitée par des agents ou des processus dédiés. Un agent peut se spécialiser dans la recherche des meilleures offres de vol, un autre se concentrer sur les réservations d'hôtel, et ainsi de suite. Un agent de coordination ou “en aval” peut ensuite compiler ces résultats en un itinéraire cohérent pour l'utilisateur final.

Cette approche modulaire permet également des améliorations progressives. Par exemple, vous pourriez ajouter des agents spécialisés pour les recommandations alimentaires ou les suggestions d'activités locales et affiner l'itinéraire au fil du temps.

### Sortie structurée

Les modèles de langage (LLM) peuvent générer des sorties structurées (par ex. JSON) qui sont plus faciles à analyser et à traiter pour des agents ou services en aval. Ceci est particulièrement utile dans un contexte multi-agent, où nous pouvons exécuter ces tâches après réception de la sortie de planification. Consultez cet <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">article de blog</a> pour un aperçu rapide.

Le fragment Python suivant montre un simple agent de planification décomposant un objectif en sous-tâches et générant un plan structuré :

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Modèle de sous-tâche de voyage
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # Nous souhaitons attribuer la tâche à l'agent

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Pour vous authentifier auprès du modèle, vous devrez générer un jeton d'accès personnel (PAT) dans les paramètres de votre compte GitHub.
    # Créez votre jeton PAT en suivant les instructions ici: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Définir le message de l'utilisateur
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Assurez-vous que le contenu de la réponse est une chaîne JSON valide avant de la charger
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# if response_content is None:
#     raise ValueError("Le contenu de la réponse n'est pas une chaîne JSON valide")

# # Affichez le contenu de la réponse après l'avoir chargé en JSON
# pprint(json.loads(response_content))

# Validez le contenu de la réponse avec le modèle MathReasoning
# TravelPlan.model_validate(json.loads(response_content))
```

### Agent de planification avec orchestration multi-agent

Dans cet exemple, un agent de routage sémantique reçoit une requête utilisateur (p. ex., "J'ai besoin d'un plan d'hébergement pour mon voyage.").

Le planificateur procède ensuite comme suit :

* Reçoit le plan d'hébergement : Le planificateur prend le message de l'utilisateur et, sur la base d'un prompt système (incluant les détails des agents disponibles), génère un plan de voyage structuré.
* Liste les agents et leurs outils : le registre d'agents contient une liste d'agents (par ex. pour les vols, les hôtels, la location de voitures et les activités) ainsi que les fonctions ou outils qu'ils offrent.
* Achemine le plan vers les agents respectifs : en fonction du nombre de sous-tâches, le planificateur envoie soit le message directement à un agent dédié (pour les scénarios mono-tâche), soit coordonne via un gestionnaire de discussion de groupe pour une collaboration multi-agent.
* Résume le résultat : enfin, le planificateur résume le plan généré pour plus de clarté.
L'exemple de code Python suivant illustre ces étapes :

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Modèle de sous-tâche de voyage

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # nous voulons assigner la tâche à l'agent

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Créer le client avec des variables d'environnement vérifiées au niveau des types

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Définir le message de l'utilisateur

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# S'assurer que le contenu de la réponse est une chaîne JSON valide avant de la charger

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Afficher le contenu de la réponse après l'avoir chargé en JSON

pprint(json.loads(response_content))
```

Ce qui suit est la sortie du code précédent et vous pouvez ensuite utiliser cette sortie structurée pour acheminer vers `assigned_agent` et résumer le plan de voyage pour l'utilisateur final.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Un notebook d'exemple contenant le code précédent est disponible [ici](07-autogen.ipynb).

### Planification itérative

Certaines tâches nécessitent des allers-retours ou une re-planification, où le résultat d'une sous-tâche influence la suivante. Par exemple, si l'agent découvre un format de données inattendu lors de la réservation de vols, il pourrait devoir adapter sa stratégie avant de passer aux réservations d'hôtel.

De plus, les retours utilisateur (par ex. un humain décidant qu'il préfère un vol plus tôt) peuvent déclencher une re-planification partielle. Cette approche dynamique et itérative garantit que la solution finale s'aligne sur les contraintes du monde réel et les préférences évolutives des utilisateurs.

p. ex. : code d'exemple

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. identique au code précédent et transmettre l'historique de l'utilisateur, le plan actuel
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. réplanifier et envoyer les tâches aux agents respectifs
```

Pour une planification plus complète, consultez Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">article de blog</a> pour la résolution de tâches complexes.

## Résumé

Dans cet article, nous avons examiné un exemple de création d'un planificateur capable de sélectionner dynamiquement les agents disponibles définis. La sortie du planificateur décompose les tâches et assigne les agents afin qu'elles puissent être exécutées. On suppose que les agents ont accès aux fonctions/outils nécessaires pour accomplir la tâche. En plus des agents, vous pouvez inclure d'autres modèles comme la réflexion, le synthétiseur et le chat en round-robin pour personnaliser davantage.

## Ressources supplémentaires

AutoGen Magentic One - A Generalist multi-agent system for solving complex tasks and has achieved impressive results on multiple challenging agentic benchmarks. Référence : <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Dans cette implémentation, l'orchestrateur crée des plans spécifiques aux tâches et délègue ces tâches aux agents disponibles. En plus de la planification, l'orchestrateur emploie également un mécanisme de suivi pour surveiller la progression de la tâche et replanifier si nécessaire.

### Vous avez d'autres questions sur le modèle de conception de planification ?

Rejoignez le [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pour rencontrer d'autres apprenants, participer à des heures de permanence et obtenir des réponses à vos questions sur les agents d'IA.

## Leçon précédente

[Construire des agents d'IA dignes de confiance](../06-building-trustworthy-agents/README.md)

## Leçon suivante

[Modèle de conception multi-agent](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Clause de non-responsabilité :

Ce document a été traduit à l'aide du service de traduction par IA Co-op Translator (https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d'être précis, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d'origine doit être considéré comme la source faisant foi. Pour les informations critiques, il est recommandé d'avoir recours à une traduction professionnelle réalisée par un traducteur humain. Nous déclinons toute responsabilité en cas de malentendus ou d'interprétations erronées résultant de l'utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->