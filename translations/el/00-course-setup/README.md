# Ρύθμιση μαθήματος

## Εισαγωγή

Το μάθημα αυτό θα καλύψει πώς να εκτελείτε τα παραδείγματα κώδικα αυτού του μαθήματος.

## Ενταχθείτε σε άλλους μαθητές και λάβετε βοήθεια

Πριν ξεκινήσετε να κλωνοποιείτε το repo σας, ενταχθείτε στο [κανάλι Discord “AI Agents For Beginners”](https://aka.ms/ai-agents/discord) για να λάβετε βοήθεια με τη ρύθμιση, ερωτήσεις σχετικά με το μάθημα ή για να συνδεθείτε με άλλους μαθητές.

## Κλωνοποίηση ή Φόρκ αυτού του αποθετηρίου

Για να ξεκινήσετε, παρακαλούμε κλωνοποιήστε ή κάντε fork το GitHub αποθετήριο. Αυτό θα δημιουργήσει τη δική σας έκδοση του υλικού του μαθήματος ώστε να μπορείτε να εκτελείτε, να δοκιμάζετε και να τροποποιείτε τον κώδικα!

This can be done by clicking the link to <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">κάντε fork το αποθετήριο</a>

You should now have your own forked version of this course in the following link:

![Φορκαρισμένο αποθετήριο](../../../translated_images/el/forked-repo.33f27ca1901baa6a.webp)

### Επιφανειακή κλωνοποίηση (προτεινόμενη για εργαστήριο / Codespaces)

  >Το πλήρες αποθετήριο μπορεί να είναι μεγάλο (~3 GB) όταν κατεβάσετε ολόκληρο το ιστορικό και όλα τα αρχεία. Αν παρακολουθείτε μόνο το εργαστήριο ή χρειάζεστε μόνο μερικούς φακέλους μαθημάτων, μια επιφανειακή κλωνοποίηση (ή μια αραιή κλωνοποίηση) αποφεύγει το μεγαλύτερο μέρος αυτού του κατεβάσματος περιορίζοντας το ιστορικό και/ή παραλείποντας blobs.

#### Γρήγορη επιφανειακή κλωνοποίηση — ελάχιστο ιστορικό, όλα τα αρχεία

Replace `<your-username>` in the below commands with your fork URL (or the upstream URL if you prefer).

To clone only the latest commit history (small download):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

To clone a specific branch:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### Μερική (sparse) κλωνοποίηση — ελάχιστα blobs + μόνο επιλεγμένοι φάκελοι

This uses partial clone and sparse-checkout (requires Git 2.25+ and recommended modern Git with partial clone support):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

Traverse into the repo folder:

```bash|powershell
cd ai-agents-for-beginners
```

Then specify which folders you want (example below shows two folders):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

After cloning and verifying the files, if you only need files and want to free space (no git history), please delete the repository metadata (💀irreversible — you will lose all Git functionality: no commits, pulls, pushes, or history access).

```bash
# zsh/bash
rm -rf .git
```

```powershell
# PowerShell
Remove-Item -Recurse -Force .git
```

#### Χρήση GitHub Codespaces (συνιστάται για να αποφύγετε μεγάλες τοπικές λήψεις)

- Δημιουργήστε ένα νέο Codespace για αυτό το αποθετήριο μέσω του [GitHub UI](https://github.com/codespaces).  

- Στο τερματικό του πρόσφατα δημιουργημένου codespace, εκτελέστε μία από τις παραπάνω εντολές shallow/sparse clone για να φέρετε μόνο τους φακέλους μαθημάτων που χρειάζεστε στο workspace του Codespace.
- Προαιρετικό: αφού κλωνοποιήσετε μέσα στο Codespaces, καταργήστε το .git για να ανακτήσετε επιπλέον χώρο (βλ. εντολές αφαίρεσης παραπάνω).
- Σημείωση: Αν προτιμάτε να ανοίξετε το αποθετήριο απευθείας στα Codespaces (χωρίς επιπλέον κλωνοποίηση), να γνωρίζετε ότι τα Codespaces θα κατασκευάσουν το περιβάλλον devcontainer και μπορεί ακόμα να παρέχουν περισσότερα από όσα χρειάζεστε. Η κλωνοποίηση μιας επιφανειακής αντιγραφής μέσα σε ένα καινούργιο Codespace σας δίνει μεγαλύτερο έλεγχο στη χρήση δίσκου.

#### Συμβουλές

- Πάντα αντικαθιστάτε το URL κλωνοποίησης με το fork σας αν θέλετε να επεξεργαστείτε/κάνετε commit.
- Αν αργότερα χρειαστείτε περισσότερο ιστορικό ή αρχεία, μπορείτε να τα φέρετε (fetch) ή να προσαρμόσετε το sparse-checkout για να συμπεριλάβετε επιπλέον φακέλους.

## Εκτέλεση του Κώδικα

This course offers a series of Jupyter Notebooks that you can run with to get hands-on experience building AI Agents.

The code samples use either:

**Απαιτεί Λογαριασμό GitHub - Δωρεάν**:

1) Semantic Kernel Agent Framework + GitHub Models Marketplace. Επισημασμένο ως (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace. Επισημασμένο ως (autogen.ipynb)

**Απαιτεί Συνδρομή Azure**:
3) Azure AI Foundry + Azure AI Agent Service. Επισημασμένο ως (azureaiagent.ipynb)

We encourage you to try out all three types of examples to see which one works best for you.

Whichever option you choose, it will determine which setup steps you need to follow below:

## Απαιτήσεις

- Python 3.12+
  - **ΣΗΜΕΙΩΣΗ**: Αν δεν έχετε εγκατεστημένο Python3.12, βεβαιωθείτε ότι το εγκαθιστάτε. Στη συνέχεια δημιουργήστε το venv χρησιμοποιώντας python3.12 για να διασφαλίσετε ότι οι σωστές εκδόσεις εγκαθίστανται από το αρχείο requirements.txt.
  
    >Παράδειγμα

    Δημιουργία καταλόγου Python venv:

    ```bash|powershell
    python -m venv venv
    ```

    Στη συνέχεια ενεργοποιήστε το περιβάλλον venv για:

    ```bash
    # zsh/bash
    source venv/bin/activate
    ```
  
    ```dos
    # Command Prompt for Windows
    venv\Scripts\activate
    ```

- .NET 10+: Για τα δείγματα κώδικα που χρησιμοποιούν .NET, βεβαιωθείτε ότι έχετε εγκαταστήσει το [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) ή νεότερο. Στη συνέχεια, ελέγξτε την εγκατεστημένη έκδοση του .NET SDK:

    ```bash|powershell
    dotnet --list-sdks
    ```

- A GitHub Account - For Access to the GitHub Models Marketplace
- Azure Subscription - For Access to Microsoft Foundry
- Microsoft Foundry Account - For Access to the Azure AI Agent Service

Στη ρίζα αυτού του αποθετηρίου έχουμε συμπεριλάβει ένα αρχείο `requirements.txt` που περιέχει όλα τα απαιτούμενα πακέτα Python για να εκτελέσετε τα δείγματα κώδικα.

Μπορείτε να τα εγκαταστήσετε εκτελώντας την ακόλουθη εντολή στο τερματικό σας στη ρίζα του αποθετηρίου:

```bash|powershell
pip install -r requirements.txt
```

Συνιστούμε τη δημιουργία ενός εικονικού περιβάλλοντος Python για να αποφύγετε συγκρούσεις και προβλήματα.

## Ρύθμιση VSCode

Βεβαιωθείτε ότι χρησιμοποιείτε τη σωστή έκδοση Python στο VSCode.

![εικόνα](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## Ρύθμιση για δείγματα που χρησιμοποιούν GitHub Models 

### Βήμα 1: Λήψη του Προσωπικού Token Πρόσβασης GitHub (PAT)

Αυτό το μάθημα αξιοποιεί το GitHub Models Marketplace, προσφέροντας δωρεάν πρόσβαση σε Μεγάλα Γλωσσικά Μοντέλα (LLMs) που θα χρησιμοποιήσετε για να χτίσετε AI Agents.

Για να χρησιμοποιήσετε τα GitHub Models, θα χρειαστεί να δημιουργήσετε ένα [Προσωπικό Token Πρόσβασης GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

Αυτό μπορεί να γίνει πηγαίνοντας στις <a href="https://github.com/settings/personal-access-tokens" target="_blank">Ρυθμίσεις Προσωπικών Token Πρόσβασης</a> στον λογαριασμό GitHub σας.

Παρακαλώ ακολουθήστε την [Αρχή Ελαχιστοποίησης Δικαιωμάτων](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely) όταν δημιουργείτε το token. Αυτό σημαίνει ότι θα πρέπει να δώσετε στο token μόνο τα δικαιώματα που χρειάζεται για να εκτελέσει τα δείγματα κώδικα σε αυτό το μάθημα.

1. Επιλέξτε την επιλογή `Fine-grained tokens` στην αριστερή πλευρά της οθόνης σας πηγαίνοντας στις **Ρυθμίσεις προγραμματιστή**

   ![Ρυθμίσεις προγραμματιστή](../../../translated_images/el/profile_developer_settings.410a859fe749c755.webp)

   Στη συνέχεια επιλέξτε `Generate new token`.

   ![Generate Token](../../../translated_images/el/fga_new_token.1c1a234afe202ab3.webp)

2. Εισάγετε ένα περιγραφικό όνομα για το token που αντικατοπτρίζει τον σκοπό του, ώστε να είναι εύκολο να το αναγνωρίσετε αργότερα.

    🔐 Σύσταση διάρκειας token

    Συνιστώμενη διάρκεια: 30 ημέρες
    Για μεγαλύτερη ασφάλεια, μπορείτε να επιλέξετε μικρότερη περίοδο—όπως 7 ημέρες 🛡️
    Είναι ένας εξαιρετικός τρόπος να ορίσετε έναν προσωπικό στόχο και να ολοκληρώσετε το μάθημα ενώ η μαθησιακή σας δυναμική είναι υψηλή 🚀.

    ![Όνομα Token και Λήξη](../../../translated_images/el/token-name-expiry-date.a095fb0de6386864.webp)

3. Περιορίστε το πεδίο εφαρμογής του token στο fork αυτού του αποθετηρίου.

    ![Περιορίστε το πεδίο στο fork αποθετήριο](../../../translated_images/el/token_repository_limit.924ade5e11d9d8bb.webp)

4. Περιορίστε τα δικαιώματα του token: κάτω από τις **Permissions**, κάντε κλικ στην καρτέλα **Account**, και πατήστε το κουμπί "+ Add permissions". Θα εμφανιστεί ένα αναπτυσσόμενο μενού. Αναζητήστε το **Models** και τσεκάρετε το κουτάκι για αυτό.

    ![Προσθήκη Δικαιώματος Models](../../../translated_images/el/add_models_permissions.c0c44ed8b40fc143.webp)

5. Επαληθεύστε τα απαιτούμενα δικαιώματα πριν δημιουργήσετε το token. ![Επαλήθευση Δικαιωμάτων](../../../translated_images/el/verify_permissions.06bd9e43987a8b21.webp)

6. Πριν δημιουργήσετε το token, βεβαιωθείτε ότι είστε έτοιμοι να αποθηκεύσετε το token σε ασφαλές μέρος, όπως θησαυροφυλάκιο διαχειριστή κωδικών (password manager), καθώς δεν θα εμφανιστεί ξανά μετά τη δημιουργία του. ![Αποθήκευση Token με Ασφάλεια](../../../translated_images/el/store_token_securely.08ee2274c6ad6caf.webp)

Αντιγράψτε το νέο token που μόλις δημιουργήσατε. Τώρα θα το προσθέσετε στο αρχείο `.env` που περιλαμβάνεται σε αυτό το μάθημα.

### Βήμα 2: Δημιουργία του αρχείου `.env` σας

Για να δημιουργήσετε το αρχείο `.env`, εκτελέστε την ακόλουθη εντολή στο τερματικό σας.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# ΠάουερΣέλ
Copy-Item .env.example .env
```

Αυτό θα αντιγράψει το αρχείο παραδείγματος και θα δημιουργήσει ένα `.env` στον κατάλογό σας όπου θα συμπληρώσετε τις τιμές για τις μεταβλητές περιβάλλοντος.

Με το token αντιγραμμένο, ανοίξτε το αρχείο `.env` στον αγαπημένο σας επεξεργαστή κειμένου και επικολλήστε το token στο πεδίο `GITHUB_TOKEN`.

![Πεδίο Token GitHub](../../../translated_images/el/github_token_field.20491ed3224b5f4a.webp)

Τώρα θα πρέπει να μπορείτε να εκτελέσετε τα δείγματα κώδικα αυτού του μαθήματος.

## Ρύθμιση για δείγματα που χρησιμοποιούν Microsoft Foundry και Azure AI Agent Service

### Βήμα 1: Λήψη του Endpoint του έργου Azure σας


Ακολουθήστε τα βήματα για τη δημιουργία hub και έργου στο Azure AI Foundry που βρίσκονται εδώ: [Hub resources overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)


Αφού δημιουργήσετε το έργο σας, θα χρειαστεί να λάβετε τη συμβολοσειρά σύνδεσης (connection string) για το έργο σας.

Αυτό μπορεί να γίνει πηγαίνοντας στη σελίδα **Overview** του έργου σας στο portal του Microsoft Foundry.

![Συμβολοσειρά σύνδεσης έργου](../../../translated_images/el/project-endpoint.8cf04c9975bbfbf1.webp)

### Βήμα 2: Δημιουργία του αρχείου `.env` σας

Για να δημιουργήσετε το αρχείο `.env`, εκτελέστε την ακόλουθη εντολή στο τερματικό σας.

```bash
# zsh/bash
cp .env.example .env
```

```powershell
# PowerShell
Copy-Item .env.example .env
```

Αυτό θα αντιγράψει το αρχείο παραδείγματος και θα δημιουργήσει ένα `.env` στον κατάλογό σας όπου θα συμπληρώσετε τις τιμές για τις μεταβλητές περιβάλλοντος.

Με το token αντιγραμμένο, ανοίξτε το αρχείο `.env` στον αγαπημένο σας επεξεργαστή κειμένου και επικολλήστε το token στο πεδίο `PROJECT_ENDPOINT`.

### Βήμα 3: Σύνδεση στο Azure

Ως βέλτιστη πρακτική ασφαλείας, θα χρησιμοποιήσουμε [keyless authentication](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst) για να αυθεντικοποιηθούμε στο Azure OpenAI με Microsoft Entra ID. 

Στη συνέχεια, ανοίξτε ένα τερματικό και εκτελέστε `az login --use-device-code` για να συνδεθείτε στον λογαριασμό Azure σας.

Αφού συνδεθείτε, επιλέξτε τη συνδρομή σας στο τερματικό.

## Επιπλέον μεταβλητές περιβάλλοντος - Azure Search και Azure OpenAI 

Για το μάθημα Agentic RAG - Μάθημα 5 - υπάρχουν δείγματα που χρησιμοποιούν Azure Search και Azure OpenAI.

Αν θέλετε να εκτελέσετε αυτά τα δείγματα, θα χρειαστεί να προσθέσετε τις ακόλουθες μεταβλητές περιβάλλοντος στο αρχείο `.env` σας:

### Σελίδα επισκόπησης (Project)

- `AZURE_SUBSCRIPTION_ID` - Check **Project details** on the **Overview** page of your project.

- `AZURE_AI_PROJECT_NAME` - Look at the top of the **Overview** page for your project.

- `AZURE_OPENAI_SERVICE` - Find this in the **Included capabilities** tab for **Azure OpenAI Service** on the **Overview** page.

### Κέντρο Διαχείρισης

- `AZURE_OPENAI_RESOURCE_GROUP` - Go to **Project properties** on the **Overview** page of the **Management Center**.

- `GLOBAL_LLM_SERVICE` - Under **Connected resources**, find the **Azure AI Services** connection name. If not listed, check the **Azure portal** under your resource group for the AI Services resource name.

### Models + Endpoints Page

- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Select your embedding model (e.g., `text-embedding-ada-002`) and note the **Deployment name** from the model details.

- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Select your chat model (e.g., `gpt-4o-mini`) and note the **Deployment name** from the model details.

### Azure Portal

- `AZURE_OPENAI_ENDPOINT` - Look for **Azure AI services**, click on it, then go to **Resource Management**, **Keys and Endpoint**, scroll down to the "Azure OpenAI endpoints", and copy the one that says "Language APIs".

- `AZURE_OPENAI_API_KEY` - From the same screen, copy KEY 1 or KEY 2.

- `AZURE_SEARCH_SERVICE_ENDPOINT` - Find your **Azure AI Search** resource, click it, and see **Overview**.

- `AZURE_SEARCH_API_KEY` - Then go to **Settings** and then **Keys** to copy the primary or secondary admin key.

### Εξωτερική ιστοσελίδα

- `AZURE_OPENAI_API_VERSION` - Visit the [API version lifecycle](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) page under **Latest GA API release**.

### Ρύθμιση αυθεντικοποίησης χωρίς κλειδί

Rather than hardcode your credentials, we'll use a keyless connection with Azure OpenAI. To do so, we'll import `DefaultAzureCredential` and later call the `DefaultAzureCredential` function to get the credential.

```python
# Πάιθον
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## Κολλήσατε κάπου;
Αν έχετε οποιαδήποτε προβλήματα κατά την εκτέλεση αυτής της ρύθμισης, επισκεφθείτε το <a href="https://discord.gg/kzRShWzttr" target="_blank">Discord της Κοινότητας Azure AI</a> ή <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">δημιουργήστε ένα θέμα</a>.

## Επόμενο Μάθημα

Τώρα είστε έτοιμοι να εκτελέσετε τον κώδικα για αυτό το μάθημα. Καλή συνέχεια στην εκμάθηση περισσότερων για τον κόσμο των πρακτόρων τεχνητής νοημοσύνης! 

[Εισαγωγή στους Πράκτορες Τεχνητής Νοημοσύνης και Περιπτώσεις Χρήσης](../01-intro-to-ai-agents/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Αποποίηση ευθυνών:
Αυτό το έγγραφο έχει μεταφραστεί με χρήση υπηρεσίας αυτόματης μετάφρασης με τεχνητή νοημοσύνη Co-op Translator (https://github.com/Azure/co-op-translator). Παρότι επιδιώκουμε την ακρίβεια, παρακαλούμε να έχετε υπόψη ότι οι αυτοματοποιημένες μεταφράσεις ενδέχεται να περιέχουν σφάλματα ή ανακρίβειες. Το πρωτότυπο έγγραφο στη γλώσσα του πρέπει να θεωρείται η αυθεντική πηγή. Για κρίσιμες πληροφορίες συνιστάται επαγγελματική ανθρώπινη μετάφραση. Δεν φέρουμε ευθύνη για τυχόν παρεξηγήσεις ή λανθασμένες ερμηνείες που προκύπτουν από τη χρήση αυτής της μετάφρασης.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->