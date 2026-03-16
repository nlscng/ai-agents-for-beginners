# Configuration du cours

## Introduction

Cette leçon expliquera comment exécuter les exemples de code de ce cours.

## Rejoignez d'autres apprenants et obtenez de l'aide

Avant de commencer à cloner votre dépôt, rejoignez le [canal Discord AI Agents For Beginners](https://aka.ms/ai-agents/discord) pour obtenir de l'aide sur la configuration, poser des questions sur le cours ou pour connecter avec d'autres apprenants.

## Cloner ou Forker ce dépôt

Pour commencer, veuillez cloner ou forker le dépôt GitHub. Cela vous permettra d'avoir votre propre version du matériel du cours afin que vous puissiez exécuter, tester et modifier le code !

Cela peut être fait en cliquant sur le lien pour <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">forker le dépôt</a>

Vous devriez maintenant avoir votre propre version forkée de ce cours au lien suivant :

![Forked Repo](../../../translated_images/fr/forked-repo.33f27ca1901baa6a.webp)

### Clonage superficiel (recommandé pour atelier / Codespaces)

  >Le dépôt complet peut être volumineux (~3 Go) lorsque vous téléchargez tout l'historique et tous les fichiers. Si vous assistez seulement à l'atelier ou si vous n'avez besoin que de quelques dossiers de leçons, un clonage superficiel (ou clonage sparse) évite la majorité de ce téléchargement en tronquant l'historique et/ou en sautant les blobs.

#### Clonage superficiel rapide — historique minimal, tous les fichiers

Remplacez `<your-username>` dans les commandes ci-dessous par l'URL de votre fork (ou l'URL upstream si vous préférez).

Pour cloner uniquement l'historique du dernier commit (téléchargement réduit) :

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

Pour cloner une branche spécifique :

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Clonage partiel (sparse) — blobs minimaux + uniquement dossiers sélectionnés

Cela utilise le clonage partiel et le sparse-checkout (nécessite Git 2.25+ et il est recommandé d'utiliser un Git moderne avec support du clonage partiel) :

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Naviguez dans le dossier du dépôt :

```bash|powershell
cd ai-agents-for-beginners
```

Puis spécifiez les dossiers que vous souhaitez (l'exemple ci-dessous montre deux dossiers) :

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

Après le clonage et la vérification des fichiers, si vous n'avez besoin que des fichiers et souhaitez libérer de l'espace (pas d'historique git), veuillez supprimer les métadonnées du dépôt (💀 irréversible — vous perdrez toute fonctionnalité Git : plus de commits, pulls, pushes ou accès à l'historique).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Utilisation de GitHub Codespaces (recommandé pour éviter les gros téléchargements locaux)

- Créez un nouveau Codespace pour ce dépôt via l'[interface GitHub](https://github.com/codespaces).  

- Dans le terminal du Codespace nouvellement créé, exécutez l'une des commandes de clonage superficiel/sparse ci-dessus pour importer uniquement les dossiers de leçons dont vous avez besoin dans l'espace de travail Codespace.
- Optionnel : après le clonage dans Codespaces, supprimez .git pour récupérer de l'espace supplémentaire (voir commandes de suppression ci-dessus).
- Note : Si vous préférez ouvrir directement le dépôt dans Codespaces (sans clonage supplémentaire), sachez que Codespaces construira l'environnement devcontainer et pourra toujours provisionner plus que nécessaire. Cloner une copie superficielle dans un Codespace neuf vous donne plus de contrôle sur l'utilisation du disque.

#### Conseils

- Remplacez toujours l'URL de clonage par celle de votre fork si vous souhaitez modifier/commiter.
- Si vous avez besoin ultérieurement de plus d'historique ou de fichiers, vous pouvez les récupérer ou ajuster le sparse-checkout pour inclure des dossiers supplémentaires.

## Exécution du code

Ce cours propose une série de notebooks Jupyter que vous pouvez exécuter pour acquérir une expérience pratique dans la construction d'agents IA.

Les exemples de code utilisent soit :

**Nécessite un compte GitHub - Gratuit** :

1) Framework Semantic Kernel Agent + GitHub Models Marketplace. Étiqueté comme (semantic-kernel.ipynb)
2) Framework AutoGen + GitHub Models Marketplace. Étiqueté comme (autogen.ipynb)

**Nécessite un abonnement Azure** :
3) Azure AI Foundry + Azure AI Agent Service. Étiqueté comme (azureaiagent.ipynb)

Nous vous encourageons à essayer les trois types d'exemples pour voir lequel vous convient le mieux.

Quelle que soit l'option choisie, elle déterminera les étapes de configuration à suivre ci-dessous :

## Prérequis

- Python 3.12+
  - **NOTE** : Si vous n'avez pas Python 3.12 installé, assurez-vous de l'installer. Créez ensuite votre environnement virtuel avec python3.12 pour garantir que les bonnes versions soient installées depuis le fichier requirements.txt.
  
    >Exemple

    Créer le répertoire d'environnement virtuel Python :

    ```bash|powershell
    python -m venv venv
    ```

    Puis activez l'environnement virtuel avec :

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+ : Pour les exemples utilisant .NET, assurez-vous d'installer le [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) ou une version ultérieure. Puis, vérifiez la version de votre SDK installé :

    ```bash|powershell
    dotnet --list-sdks
    ```

- Un compte GitHub - Pour accéder au GitHub Models Marketplace
- Un abonnement Azure - Pour accéder à Microsoft Foundry
- Un compte Microsoft Foundry - Pour accéder au Azure AI Agent Service

Un fichier `requirements.txt` est inclus à la racine de ce dépôt contenant tous les paquets Python nécessaires pour exécuter les exemples.

Vous pouvez les installer en exécutant la commande suivante dans votre terminal à la racine du dépôt :

```bash|powershell
pip install -r requirements.txt
```

Nous recommandons de créer un environnement virtuel Python pour éviter tout conflit et problème.

## Configuration de VSCode

Assurez-vous d'utiliser la bonne version de Python dans VSCode.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Configuration pour les exemples utilisant GitHub Models

### Étape 1 : Récupérez votre token d'accès personnel GitHub (PAT)

Ce cours utilise le GitHub Models Marketplace, offrant un accès gratuit à des modèles de langage large (LLMs) que vous utiliserez pour construire des agents IA.

Pour utiliser GitHub Models, vous devez créer un [token d'accès personnel GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Cela se fait en allant dans vos <a href="https://github.com/settings/personal-access-tokens" target="_blank">paramètres de tokens personnels</a> dans votre compte GitHub.

Veuillez suivre le [principe du moindre privilège](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) lors de la création de votre token. Cela signifie que vous devriez uniquement accorder au token les permissions nécessaires pour exécuter les exemples de code de ce cours.

1. Sélectionnez l'option `Fine-grained tokens` sur la gauche en allant dans les **Developer settings**

   ![Developer settings](../../../translated_images/fr/profile_developer_settings.410a859fe749c755.webp)

   Puis sélectionnez `Generate new token`.

   ![Generate Token](../../../translated_images/fr/fga_new_token.1c1a234afe202ab3.webp)

2. Entrez un nom descriptif pour votre token qui reflète son usage pour pouvoir l'identifier facilement plus tard.

    🔐 Recommandation durée du token

    Durée recommandée : 30 jours  
    Pour une posture plus sécurisée, optez pour une plus courte période — par exemple 7 jours 🛡️  
    C’est une excellente façon de se fixer un objectif personnel et de compléter le cours pendant que vous êtes motivé 🚀.

    ![Token Name and Expiration](../../../translated_images/fr/token-name-expiry-date.a095fb0de6386864.webp)

3. Limitez la portée du token à votre fork de ce dépôt.

    ![Limit scope to fork repository](../../../translated_images/fr/token_repository_limit.924ade5e11d9d8bb.webp)

4. Restreignez les permissions du token : Sous **Permissions**, cliquez sur l’onglet **Account**, puis cliquez sur le bouton "+ Add permissions". Un menu déroulant apparaîtra. Recherchez **Models** et cochez sa case.

    ![Add Models Permission](../../../translated_images/fr/add_models_permissions.c0c44ed8b40fc143.webp)

5. Vérifiez les permissions requises avant de générer le token. ![Verify Permissions](../../../translated_images/fr/verify_permissions.06bd9e43987a8b21.webp)

6. Avant de générer le token, assurez-vous d’être prêt à le stocker dans un endroit sécurisé comme un coffre-fort de gestionnaire de mots de passe, car il ne sera plus affiché après sa création. ![Store Token Securely](../../../translated_images/fr/store_token_securely.08ee2274c6ad6caf.webp)

Copiez votre nouveau token que vous venez de créer. Vous allez ensuite l’ajouter dans votre fichier `.env` inclus dans ce cours.

### Étape 2 : Créez votre fichier `.env`

Pour créer votre fichier `.env` exécutez la commande suivante dans votre terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Cela copiera le fichier d’exemple et créera un `.env` dans votre répertoire où vous pourrez remplir les valeurs des variables d’environnement.

Avec votre token copié, ouvrez le fichier `.env` dans votre éditeur de texte préféré et collez votre token dans le champ `GITHUB_TOKEN`.

![GitHub Token Field](../../../translated_images/fr/github_token_field.20491ed3224b5f4a.webp)

Vous devriez maintenant être en mesure d’exécuter les exemples de code de ce cours.

## Configuration pour les exemples utilisant Microsoft Foundry et Azure AI Agent Service

### Étape 1 : Récupérez le point de terminaison de votre projet Azure

Suivez les étapes pour créer un hub et un projet dans Azure AI Foundry ici : [Aperçu des ressources du hub](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)

Une fois votre projet créé, vous devrez récupérer la chaîne de connexion de votre projet.

Cela peut être fait en allant sur la page **Overview** de votre projet dans le portail Microsoft Foundry.

![Project Connection String](../../../translated_images/fr/project-endpoint.8cf04c9975bbfbf1.webp)

### Étape 2 : Créez votre fichier `.env`

Pour créer votre fichier `.env` exécutez la commande suivante dans votre terminal.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Cela copiera le fichier d’exemple et créera un `.env` dans votre répertoire où vous remplirez les valeurs des variables d’environnement.

Avec votre token copié, ouvrez le fichier `.env` dans votre éditeur de texte préféré et collez votre token dans le champ `PROJECT_ENDPOINT`.

### Étape 3 : Connectez-vous à Azure

Par mesure de sécurité, nous allons utiliser [l’authentification sans clé](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) pour s’authentifier auprès d’Azure OpenAI avec Microsoft Entra ID. 

Ensuite, ouvrez un terminal et exécutez `az login --use-device-code` pour vous connecter à votre compte Azure.

Une fois connecté, sélectionnez votre abonnement dans le terminal.

## Variables d’environnement supplémentaires - Azure Search et Azure OpenAI 

Pour la leçon Agentic RAG - Leçon 5 - il existe des exemples qui utilisent Azure Search et Azure OpenAI.

Si vous souhaitez exécuter ces exemples, vous devrez ajouter les variables d’environnement suivantes dans votre fichier `.env` :

### Page d’aperçu (Projet)

- `AZURE_SUBSCRIPTION_ID` - Consultez les **Détails du projet** sur la page **Overview** de votre projet.

- `AZURE_AI_PROJECT_NAME` - Regardez en haut de la page **Overview** pour le nom de votre projet.

- `AZURE_OPENAI_SERVICE` - Trouvez cette information dans l’onglet **Included capabilities** pour le service **Azure OpenAI** sur la page **Overview**.

### Centre de gestion

- `AZURE_OPENAI_RESOURCE_GROUP` - Allez dans **Project properties** sur la page **Overview** du **Management Center**.

- `GLOBAL_LLM_SERVICE` - Sous **Connected resources**, trouvez le nom de connexion **Azure AI Services**. Si non listé, vérifiez dans le portail Azure sous votre groupe de ressources pour le nom de la ressource AI Services.

### Page Modèles + Points de terminaison

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Sélectionnez votre modèle d’embedding (ex : `text-embedding-ada-002`) et notez le **Deployment name** depuis les détails du modèle.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Sélectionnez votre modèle de chat (ex : `gpt-4o-mini`) et notez le **Deployment name** depuis les détails du modèle.

### Portail Azure

- `AZURE_OPENAI_ENDPOINT` - Cherchez **Azure AI services**, cliquez dessus, puis allez dans **Resource Management**, **Keys and Endpoint**, faites défiler jusqu’aux points de terminaison Azure OpenAI et copiez celui qui indique "Language APIs".

- `AZURE_OPENAI_API_KEY` - Depuis le même écran, copiez la CLÉ 1 ou la CLÉ 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Trouvez votre ressource **Azure AI Search**, cliquez dessus et consultez l’**Overview**.

- `AZURE_SEARCH_API_KEY` - Ensuite, allez dans **Settings** puis **Keys** pour copier la clé admin primaire ou secondaire.

### Page web externe

- `AZURE_OPENAI_API_VERSION` - Visitez la page [Cycle de vie des versions API](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) sous **Latest GA API release**.

### Configurez l’authentification sans clé

Plutôt que d’écrire vos identifiants en dur, nous utiliserons une connexion sans clé avec Azure OpenAI. Pour cela, nous importerons `DefaultAzureCredential` et appellerons ensuite la fonction `DefaultAzureCredential` pour obtenir les informations d’identification.

```python
# Python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Bloqué quelque part ?
Si vous rencontrez des problèmes pour exécuter cette configuration, rejoignez notre <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord de la communauté Azure AI</a> ou <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">créez un ticket</a>.

## Leçon suivante

Vous êtes maintenant prêt à exécuter le code de ce cours. Bonne découverte du monde des agents IA !

[Introduction aux agents IA et cas d'utilisation des agents](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Avertissement** :  
Ce document a été traduit à l’aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforçons d’assurer l’exactitude, veuillez noter que les traductions automatiques peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue natale doit être considéré comme la source faisant foi. Pour les informations critiques, il est recommandé de faire appel à une traduction professionnelle réalisée par un humain. Nous déclinons toute responsabilité en cas de malentendus ou d’interprétations erronées résultant de l’utilisation de cette traduction.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->