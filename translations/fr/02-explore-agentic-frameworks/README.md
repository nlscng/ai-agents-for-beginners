[![Exploration des frameworks d'agents IA](../../../translated_images/fr/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Cliquez sur l'image ci-dessus pour voir la vidéo de cette leçon)_

# Explorer les frameworks d'agents IA

Les frameworks d'agents IA sont des plateformes logicielles conçues pour simplifier la création, le déploiement et la gestion des agents IA. Ces frameworks fournissent aux développeurs des composants préconstruits, des abstractions et des outils qui facilitent le développement de systèmes IA complexes.

Ces frameworks aident les développeurs à se concentrer sur les aspects uniques de leurs applications en offrant des approches standardisées aux défis courants du développement d'agents IA. Ils améliorent la scalabilité, l'accessibilité et l'efficacité dans la construction de systèmes IA.

## Introduction 

Cette leçon couvrira :

- Qu'est-ce que les frameworks d'agents IA et qu'autorisent-ils les développeurs à réaliser ?
- Comment les équipes peuvent-elles utiliser ces frameworks pour prototyper rapidement, itérer et améliorer les capacités de leur agent ?
- Quelles sont les différences entre les frameworks et outils créés par Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a> et <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a> ?
- Puis-je intégrer directement mes outils existants de l'écosystème Azure, ou ai-je besoin de solutions autonomes ?
- Qu'est-ce que le service Azure AI Agents et comment m'aide-t-il ?

## Objectifs d'apprentissage

Les objectifs de cette leçon sont de vous aider à comprendre :

- Le rôle des frameworks d'agents IA dans le développement IA.
- Comment tirer parti des frameworks d'agents IA pour construire des agents intelligents.
- Les capacités clés offertes par les frameworks d'agents IA.
- Les différences entre AutoGen, Semantic Kernel et Azure AI Agent Service.

## Qu'est-ce que les frameworks d'agents IA et qu'autorisent-ils les développeurs à faire ?

Les frameworks IA traditionnels peuvent vous aider à intégrer l'IA dans vos applications et à améliorer ces applications de la manière suivante :

- **Personnalisation** : L'IA peut analyser le comportement et les préférences des utilisateurs pour fournir des recommandations, du contenu et des expériences personnalisés.  
Exemple : Les services de streaming comme Netflix utilisent l'IA pour suggérer des films et des émissions basés sur l'historique de visionnage, améliorant ainsi l'engagement et la satisfaction des utilisateurs.  
- **Automatisation et efficacité** : L'IA peut automatiser les tâches répétitives, rationaliser les flux de travail et améliorer l'efficacité opérationnelle.  
Exemple : Les applications de service client utilisent des chatbots alimentés par l'IA pour gérer les demandes courantes, réduisant les temps de réponse et libérant les agents humains pour des problèmes plus complexes.  
- **Amélioration de l'expérience utilisateur** : L'IA peut améliorer l'expérience utilisateur globale en offrant des fonctionnalités intelligentes telles que la reconnaissance vocale, le traitement du langage naturel et la saisie prédictive.  
Exemple : Les assistants virtuels comme Siri et Google Assistant utilisent l'IA pour comprendre et répondre aux commandes vocales, facilitant ainsi l'interaction des utilisateurs avec leurs appareils.

### Tout cela semble génial, n'est-ce pas ? Alors pourquoi avons-nous besoin du framework d'agents IA ?

Les frameworks d'agents IA représentent quelque chose de plus que de simples frameworks IA. Ils sont conçus pour permettre la création d'agents intelligents capables d'interagir avec les utilisateurs, d'autres agents et l'environnement afin d'atteindre des objectifs spécifiques. Ces agents peuvent montrer un comportement autonome, prendre des décisions et s'adapter aux conditions changeantes. Regardons quelques capacités clés offertes par les frameworks d'agents IA :

- **Collaboration et coordination des agents** : Permettent la création de plusieurs agents IA qui peuvent travailler ensemble, communiquer et se coordonner pour résoudre des tâches complexes.  
- **Automatisation et gestion des tâches** : Fournissent des mécanismes pour automatiser des flux de travail à plusieurs étapes, la délégation de tâches et la gestion dynamique des tâches entre agents.  
- **Compréhension contextuelle et adaptation** : Équipent les agents de la capacité à comprendre le contexte, s'adapter à des environnements changeants et prendre des décisions basées sur des informations en temps réel.

En résumé, les agents vous permettent d'en faire plus, d'élever l'automatisation à un niveau supérieur, de créer des systèmes plus intelligents capables de s'adapter et d'apprendre de leur environnement.

## Comment prototyper rapidement, itérer et améliorer les capacités de l’agent ?

Ce domaine évolue rapidement, mais il existe des éléments communs à la plupart des frameworks d'agents IA qui peuvent vous aider à prototyper et itérer rapidement, notamment les composants modulaires, les outils collaboratifs et l'apprentissage en temps réel. Examinons-les :

- **Utiliser des composants modulaires** : Les SDK IA proposent des composants préconstruits tels que connecteurs AI et mémoire, appels de fonction via langage naturel ou plugins de code, modèles de prompt, et plus encore.  
- **Exploiter des outils collaboratifs** : Concevoir des agents avec des rôles et tâches spécifiques, leur permettant de tester et affiner des flux de travail collaboratifs.  
- **Apprendre en temps réel** : Mettre en place des boucles de rétroaction où les agents apprennent des interactions et ajustent leur comportement de façon dynamique.

### Utiliser des composants modulaires

Les SDK comme Microsoft Semantic Kernel et LangChain offrent des composants préconstruits tels que connecteurs AI, modèles de prompt et gestion de mémoire.

**Comment les équipes peuvent utiliser cela** : Elles peuvent assembler rapidement ces composants pour créer un prototype fonctionnel sans repartir de zéro, ce qui permet une expérimentation et itération rapides.

**Fonctionnement en pratique** : Vous pouvez utiliser un parseur préconstruit pour extraire des informations de la saisie utilisateur, un module mémoire pour stocker et récupérer des données, et un générateur de prompt pour interagir avec les utilisateurs, le tout sans avoir à construire ces composants vous-même.

**Exemple de code**. Voyons des exemples d'utilisation d'un connecteur AI préconstruit avec Semantic Kernel en Python et .Net qui utilise l’appel automatique de fonctions pour faire répondre le modèle à une saisie utilisateur :

``` python
# Exemple de Semantic Kernel en Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Définir un objet ChatHistory pour contenir le contexte de la conversation
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Définir un plugin d'exemple qui contient la fonction pour réserver un voyage
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Créer le Kernel
kernel = Kernel()

# Ajouter le plugin d'exemple à l'objet Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Définir le connecteur IA Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Définir les paramètres de requête pour configurer le modèle avec l'appel automatique de fonctions
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Envoyer la requête au modèle pour l'historique de chat et les paramètres de requête fournis
    # Le Kernel contient l'exemple que le modèle demandera d'invoquer
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # Exemple de réponse du modèle IA : `Votre vol pour New York le 1er janvier 2025 a été réservé avec succès. Bon voyage ! ✈️🗽`

    # Ajouter la réponse du modèle à l'historique de conversation
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```
  
Ce que vous voyez dans cet exemple est la manière dont vous pouvez exploiter un parseur préconstruit pour extraire des informations clés de la saisie utilisateur, telles que l'origine, la destination et la date d'une demande de réservation de vol. Cette approche modulaire vous permet de vous concentrer sur la logique de haut niveau.

### Exploiter des outils collaboratifs

Des frameworks comme CrewAI, Microsoft AutoGen et Semantic Kernel facilitent la création de plusieurs agents pouvant travailler ensemble.

**Comment les équipes peuvent utiliser cela** : Elles peuvent concevoir des agents avec des rôles et tâches spécifiques, leur permettant de tester et affiner des flux de travail collaboratifs et améliorer l'efficacité globale du système.

**Fonctionnement en pratique** : Vous pouvez créer une équipe d'agents où chaque agent a une fonction spécialisée, telle que récupération de données, analyse ou prise de décision. Ces agents peuvent communiquer et partager des informations pour atteindre un objectif commun, comme répondre à une requête utilisateur ou accomplir une tâche.

**Exemple de code (AutoGen)** :

```python
# créer des agents, puis établir un planning round-robin où ils peuvent travailler ensemble, dans ce cas dans l'ordre

# Agent de récupération de données
# Agent d'analyse des données
# Agent de prise de décision

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# La conversation se termine lorsque l'utilisateur dit "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Utilisez asyncio.run(...) lorsque vous l'exécutez dans un script.
await Console(stream)
```
  
Le code précédent montre comment créer une tâche impliquant plusieurs agents collaborant pour analyser des données. Chaque agent exécute une fonction spécifique, et la tâche est réalisée en coordonnant les agents pour atteindre le résultat souhaité. En créant des agents dédiés avec des rôles spécialisés, vous améliorez l'efficacité et la performance des tâches.

### Apprendre en temps réel

Les frameworks avancés offrent des capacités de compréhension contextuelle et d'adaptation en temps réel.

**Comment les équipes peuvent utiliser cela** : Elles peuvent mettre en place des boucles de rétroaction où les agents apprennent des interactions et ajustent leur comportement dynamiquement, conduisant à une amélioration continue et un raffinement des capacités.

**Fonctionnement en pratique** : Les agents peuvent analyser les retours utilisateurs, les données environnementales et les résultats des tâches pour mettre à jour leur base de connaissances, ajuster les algorithmes de prise de décision et améliorer les performances dans le temps. Ce processus d'apprentissage itératif permet aux agents de s'adapter aux conditions changeantes et aux préférences des utilisateurs, renforçant l'efficacité globale du système.

## Quelles sont les différences entre les frameworks AutoGen, Semantic Kernel et Azure AI Agent Service ?

Il existe plusieurs façons de comparer ces frameworks, examinons quelques différences clés en termes de conception, capacités et cas d'utilisation ciblés :

## AutoGen

AutoGen est un framework open source développé par Microsoft Research's AI Frontiers Lab. Il met l'accent sur les applications *agentiques* distribuées pilotées par événements, permettant l’intégration de plusieurs LLMs et SLMs, outils, ainsi que des modèles avancés de conception multi-agents.

AutoGen est construit autour du concept central d'agents, qui sont des entités autonomes capables de percevoir leur environnement, prendre des décisions et agir pour atteindre des objectifs spécifiques. Les agents communiquent via des messages asynchrones, ce qui leur permet de travailler de manière indépendante et parallèle, améliorant la scalabilité et la réactivité du système.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Les agents sont basés sur le modèle acteur</a>. Selon Wikipédia, un acteur est _le bloc de base du calcul concurrent. En réponse à un message reçu, un acteur peut : prendre des décisions locales, créer d’autres acteurs, envoyer davantage de messages et déterminer comment répondre au prochain message reçu_.

**Cas d’usage** : Automatisation de la génération de code, tâches d’analyse de données, et création d’agents personnalisés pour la planification et les fonctions de recherche.

Voici quelques concepts fondamentaux d’AutoGen :

- **Agents**. Un agent est une entité logicielle qui :
  - **Communique via des messages**, ces messages pouvant être synchrones ou asynchrones.  
  - **Maintient son propre état**, qui peut être modifié par les messages entrants.  
  - **Exécute des actions** en réponse aux messages reçus ou aux changements de son état. Ces actions peuvent modifier l’état de l’agent et produire des effets externes, tels que la mise à jour des journaux de messages, l’envoi de nouveaux messages, l’exécution de code ou l’appel d’API.  
    
  Voici un court extrait de code où vous créez votre propre agent avec des capacités de chat :

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
    
    Dans le code précédent, `MyAgent` est créé et hérite de `RoutedAgent`. Il a un gestionnaire de messages qui affiche le contenu du message puis envoie une réponse en utilisant le délégué `AssistantAgent`. Notez particulièrement comment nous attribuons à `self._delegate` une instance de `AssistantAgent` qui est un agent préconstruit capable de gérer des complétions de chat.

    Passons maintenant à la déclaration de ce type d’agent à AutoGen et lançons le programme :

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Démarrer le traitement des messages en arrière-plan.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Dans ce code, les agents sont enregistrés auprès de l’environnement d’exécution puis un message est envoyé à l’agent, résultant dans la sortie suivante :

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Multi-agents**. AutoGen prend en charge la création de plusieurs agents pouvant travailler ensemble pour accomplir des tâches complexes. Les agents peuvent communiquer, partager des informations et coordonner leurs actions pour résoudre les problèmes plus efficacement. Pour créer un système multi-agents, vous pouvez définir différents types d’agents avec des fonctions et rôles spécialisés, tels que récupération de données, analyse, prise de décision et interaction utilisateur. Voyons à quoi ressemble une telle création :

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Exemple de déclaration d'un Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Utilisation du type topic comme type d'agent.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # déclarations restantes raccourcies pour plus de concision

    # Discussion de groupe
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```

    Dans ce code, nous avons un `GroupChatManager` enregistré auprès de l’environnement d’exécution. Ce gestionnaire coordonne les interactions entre différents types d’agents, tels que rédacteurs, illustrateurs, éditeurs et utilisateurs.

- **Environnement d'exécution des agents**. Le framework fournit un environnement d’exécution, permettant la communication entre agents, gérant leurs identités et cycles de vie, et appliquant les règles de sécurité et de confidentialité. Cela signifie que vous pouvez exécuter vos agents dans un environnement sécurisé et contrôlé, garantissant qu’ils peuvent interagir de manière sûre et efficace. Il existe deux environnements d’exécution principaux :  
  - **Environnement autonome**. C’est un bon choix pour les applications monoprocessus où tous les agents sont implémentés dans le même langage de programmation et s’exécutent dans le même processus. Voici une illustration de son fonctionnement :  
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Environnement autonome</a>   
Pile applicative

    *les agents communiquent via des messages à travers l’environnement d’exécution, qui gère le cycle de vie des agents*

  - **Environnement d’exécution distribué**, adapté aux applications multiprocessus où les agents peuvent être implémentés dans différents langages et s’exécuter sur différentes machines. Voici une illustration de son fonctionnement :  
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Environnement distribué</a>

## Semantic Kernel + Agent Framework

Semantic Kernel est un SDK d’orchestration IA prêt pour l'entreprise. Il comprend des connecteurs AI et mémoire, ainsi qu’un framework d’agents.

Commençons par présenter quelques composants de base :

- **Connecteurs AI** : Interface avec des services IA externes et sources de données utilisable à la fois en Python et en C#.

  ```python
  # Noyau sémantique Python
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  

    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```

    Voici un exemple simple montrant comment créer un kernel et y ajouter un service de complétion de chat. Semantic Kernel établit une connexion avec un service IA externe, ici, Azure OpenAI Chat Completion.

- **Plugins** : Ils encapsulent des fonctions qu’une application peut utiliser. Il existe à la fois des plugins prêts à l’emploi et des personnalisés que vous pouvez créer. Un concept connexe est celui des "fonctions prompt". Au lieu de fournir des indices en langage naturel pour invoquer des fonctions, vous diffusez certaines fonctions au modèle. Selon le contexte actuel du chat, le modèle peut choisir d’appeler une de ces fonctions pour compléter une requête. Voici un exemple :

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```

    Ici, vous avez d’abord un modèle de prompt `skPrompt` qui laisse un espace pour que l’utilisateur saisisse du texte `$userInput`. Puis vous créez une fonction kernel `SummarizeText` que vous importez dans le kernel avec le nom de plugin `SemanticFunctions`. Notez le nom de la fonction qui aide Semantic Kernel à comprendre ce que la fonction fait et quand elle doit être appelée.

- **Fonctions natives** : Il y a aussi des fonctions natives que le framework peut appeler directement pour exécuter la tâche. Voici un exemple d’une telle fonction récupérant le contenu d’un fichier :

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```

- **Mémoire** : Abstrait et simplifie la gestion du contexte pour les applications IA. L’idée avec la mémoire est que c’est quelque chose que le LLM devrait connaître. Vous pouvez stocker cette information dans un magasin vectoriel, qui finit par être une base de données en mémoire, une base de données vectorielle ou autre similaire. Voici un exemple d’un scénario très simplifié où *des faits* sont ajoutés à la mémoire :

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```

Ces faits sont ensuite stockés dans la collection de mémoire `SummarizedAzureDocs`. Il s'agit d'un exemple très simplifié, mais vous pouvez voir comment vous pouvez stocker des informations dans la mémoire pour que le LLM puisse les utiliser.

Voici donc les bases du cadre Semantic Kernel, qu'en est-il du cadre Agent Framework ?

## Azure AI Agent Service

Azure AI Agent Service est une ajout plus récent, introduit lors de Microsoft Ignite 2024. Il permet le développement et le déploiement d'agents IA avec des modèles plus flexibles, comme l'appel direct de LLM open-source tels que Llama 3, Mistral et Cohere.

Azure AI Agent Service fournit des mécanismes de sécurité d’entreprise renforcés et des méthodes de stockage des données, le rendant adapté aux applications d’entreprise.

Il fonctionne immédiatement avec des cadres d'orchestration multi-agents comme AutoGen et Semantic Kernel.

Ce service est actuellement en aperçu public et supporte Python et C# pour la création d’agents.

Avec Semantic Kernel Python, nous pouvons créer un Azure AI Agent avec un plugin défini par l'utilisateur :

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Définir un plugin d'exemple pour l'exemple
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # Créer la définition de l'agent
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Créer l'agent AzureAI en utilisant le client défini et la définition de l'agent
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Créer un fil de discussion pour contenir la conversation
        # Si aucun fil n'est fourni, un nouveau fil sera
        # créé et renvoyé avec la réponse initiale
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # Invoquer l'agent pour le fil spécifié
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### Concepts clés

Azure AI Agent Service possède les concepts clés suivants :

- **Agent**. Azure AI Agent Service s'intègre à Microsoft Foundry. Au sein de AI Foundry, un Agent IA agit comme un microservice « intelligent » pouvant répondre à des questions (RAG), effectuer des actions ou automatiser complètement des flux de travail. Il réalise cela en combinant la puissance des modèles d'IA générative avec des outils lui permettant d'accéder et d'interagir avec des sources de données réelles. Voici un exemple d’agent :

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Dans cet exemple, un agent est créé avec le modèle `gpt-4o-mini`, un nom `my-agent` et les instructions `You are helpful agent`. L’agent est équipé d'outils et ressources pour réaliser des tâches d’interprétation de code.

- **Fil et messages**. Le fil est un autre concept important. Il représente une conversation ou interaction entre un agent et un utilisateur. Les fils peuvent être utilisés pour suivre la progression d'une conversation, stocker les informations contextuelles et gérer l'état de l’interaction. Voici un exemple de fil :

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    Dans le code précédent, un fil est créé. Par la suite, un message est envoyé au fil. En appelant `create_and_process_run`, on demande à l’agent d’effectuer un travail sur le fil. Enfin, les messages sont récupérés et enregistrés pour voir la réponse de l’agent. Les messages indiquent la progression de la conversation entre l’utilisateur et l’agent. Il est aussi important de comprendre que les messages peuvent être de différents types comme texte, image ou fichier, soit par exemple un travail de l’agent qui a généré une image ou une réponse textuelle. En tant que développeur, vous pouvez alors utiliser cette information pour traiter davantage la réponse ou la présenter à l’utilisateur.

- **S’intègre avec d’autres cadres IA**. Azure AI Agent Service peut interagir avec d'autres cadres comme AutoGen et Semantic Kernel, ce qui signifie que vous pouvez construire une partie de votre application dans l’un de ces cadres et par exemple utiliser le service Agent comme orchestrateur ou construire tout dans le service Agent.

**Cas d’utilisation** : Azure AI Agent Service est conçu pour des applications d’entreprise nécessitant une sécurité, une évolutivité et un déploiement flexible des agents IA.

## Quelle est la différence entre ces cadres ?

Il semble qu’il y ait beaucoup de chevauchements entre ces cadres, mais il existe des différences clés en termes de conception, capacités et cas d’usage cibles :

- **AutoGen** : est un cadre d’expérimentation axé sur la recherche de pointe sur les systèmes multi-agents. C’est le meilleur endroit pour expérimenter et prototyper des systèmes multi-agents sophistiqués.
- **Semantic Kernel** : est une bibliothèque prête pour la production pour construire des applications agentiques d’entreprise. Il se concentre sur les applications agentiques distribuées et pilotées par événements, permettant d’utiliser plusieurs LLM et SLM, outils, et des modèles de conception agent simple/multi-agent.
- **Azure AI Agent Service** : est une plateforme et un service de déploiement dans Azure Foundry pour les agents. Il offre une connectivité aux services supportés par Azure Foundry comme Azure OpenAI, Azure AI Search, Bing Search et l’exécution de code.

Toujours pas sûr de votre choix ?

### Cas d’utilisation

Voyons si nous pouvons vous aider en passant en revue quelques cas d’usage communs :

> Q : Je fais des expérimentations, j’apprends et je construis des applications agentes en preuve de concept, et je veux pouvoir construire et expérimenter rapidement
>

>A : AutoGen serait un bon choix pour ce scénario, car il se concentre sur des applications agentiques pilotées par événements, distribuées, et supporte des modèles de conception multi-agent avancés.

> Q : Qu’est-ce qui fait d’AutoGen un meilleur choix que Semantic Kernel et Azure AI Agent Service pour ce cas d’usage ?
>
> A : AutoGen est conçu spécifiquement pour des applications agentiques distribuées et pilotées par événements, ce qui le rend bien adapté à l’automatisation de tâches de génération de code et d’analyse de données. Il fournit les outils et capacités nécessaires pour construire efficacement des systèmes multi-agents complexes.

>Q : Il semble qu’Azure AI Agent Service pourrait aussi fonctionner ici, il a des outils pour la génération de code et plus encore ?

>
> A : Oui, Azure AI Agent Service est un service plateforme pour les agents et inclut des capacités intégrées pour plusieurs modèles, Azure AI Search, Bing Search et Azure Functions. Il facilite la construction de vos agents dans le portail Foundry et leur déploiement à grande échelle.

> Q : Je suis encore confus, donnez-moi juste une option
>
> A : Un excellent choix est de construire votre application d’abord dans Semantic Kernel puis d’utiliser Azure AI Agent Service pour déployer votre agent. Cette approche vous permet de persister facilement vos agents tout en tirant parti de la puissance pour construire des systèmes multi-agents dans Semantic Kernel. En outre, Semantic Kernel dispose d’un connecteur dans AutoGen, ce qui facilite l’utilisation des deux cadres ensemble.

Résumons les différences clés dans un tableau :

| Cadre | Focus | Concepts clés | Cas d’usage |
| --- | --- | --- | --- |
| AutoGen | Applications agentiques distribuées et pilotées par événements | Agents, Personas, Fonctions, Données | Génération de code, tâches d’analyse de données |
| Semantic Kernel | Compréhension et génération de contenu textuel humain | Agents, Composants modulaires, Collaboration | Compréhension du langage naturel, génération de contenu |
| Azure AI Agent Service | Modèles flexibles, sécurité d’entreprise, génération de code, appel d'outils | Modularité, Collaboration, Orchestration des processus | Déploiement d’agents IA sécurisé, évolutif et flexible |

Quel est le cas d’usage idéal pour chacun de ces cadres ?

## Puis-je intégrer directement mes outils existants de l'écosystème Azure, ou ai-je besoin de solutions autonomes ?

La réponse est oui, vous pouvez intégrer directement vos outils existants de l’écosystème Azure avec Azure AI Agent Service notamment, car il a été conçu pour fonctionner parfaitement avec d’autres services Azure. Vous pourriez par exemple intégrer Bing, Azure AI Search et Azure Functions. Il y a également une intégration poussée avec Microsoft Foundry.

Pour AutoGen et Semantic Kernel, vous pouvez aussi intégrer avec les services Azure, mais cela peut nécessiter d’appeler les services Azure depuis votre code. Une autre façon d’intégrer est d’utiliser les SDK Azure pour interagir avec les services Azure depuis vos agents. De plus, comme mentionné, vous pouvez utiliser Azure AI Agent Service comme orchestrateur pour vos agents construits dans AutoGen ou Semantic Kernel, ce qui permet un accès facile à l’écosystème Azure.

## Exemples de code

- Python : [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET : [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Vous avez d'autres questions sur les frameworks d’agents IA ?

Rejoignez le [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pour rencontrer d'autres apprenants, assister aux heures de bureau et obtenir des réponses à vos questions sur les agents IA.

## Références

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel et AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Utilisation d’Azure AI Agent Service avec AutoGen / Semantic Kernel pour construire une solution multi-agent</a>

## Leçon précédente

[Introduction aux agents IA et cas d’utilisation des agents](../01-intro-to-ai-agents/README.md)

## Leçon suivante

[Comprendre les modèles de conception agentique](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Avertissement** :  
Ce document a été traduit à l’aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d’origine doit être considéré comme la source faisant autorité. Pour les informations critiques, il est recommandé de recourir à une traduction professionnelle réalisée par un humain. Nous déclinons toute responsabilité en cas de malentendus ou d’interprétations erronées résultant de l’utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->