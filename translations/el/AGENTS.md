# AGENTS.md

## Επισκόπηση έργου

Αυτό το αποθετήριο περιέχει "AI Agents για Αρχάριους" - ένα πλήρες εκπαιδευτικό μάθημα που διδάσκει τα πάντα για την κατασκευή AI Agents. Το μάθημα αποτελείται από περισσότερα από 15 μαθήματα που καλύπτουν τα θεμελιώδη, πρότυπα σχεδίασης, πλαίσια εργασίας και ανάπτυξη παραγωγής AI agents.

**Κύριες Τεχνολογίες:**
- Python 3.12+
- Jupyter Notebooks για διαδραστική μάθηση
- AI Πλαίσια Εργασίας: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Υπηρεσίες Azure AI: Microsoft Foundry, Azure AI Agent Service
- GitHub Models Marketplace (διαθέσιμο δωρεάν επίπεδο)

**Αρχιτεκτονική:**
- Δομή βάσει μαθημάτων (κατάλογοι 00-15+)
- Κάθε μάθημα περιλαμβάνει: τεκμηρίωση README, δείγματα κώδικα (Jupyter notebooks) και εικόνες
- Υποστήριξη πολλαπλών γλωσσών μέσω αυτόματου συστήματος μετάφρασης
- Πολλαπλές επιλογές πλαισίων ανά μάθημα (Semantic Kernel, AutoGen, Azure AI Agent Service)

## Εντολές Εγκατάστασης

### Προαπαιτούμενα
- Python 3.12 ή νεότερη
- Λογαριασμός GitHub (για GitHub Models - δωρεάν επίπεδο)
- Συνδρομή Azure (προαιρετικό, για υπηρεσίες Azure AI)

### Αρχική Ρύθμιση

1. **Κλωνοποιήστε ή κάντε fork το αποθετήριο:**
   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # Ή
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```

2. **Δημιουργήστε και ενεργοποιήστε εικονικό περιβάλλον Python:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Στα Windows: venv\Scripts\activate
   ```

3. **Εγκαταστήστε τις εξαρτήσεις:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Ορίστε τις μεταβλητές περιβάλλοντος:**
   ```bash
   cp .env.example .env
   # Επεξεργαστείτε το .env με τα κλειδιά API και τα endpoints σας
   ```

### Απαιτούμενες Μεταβλητές Περιβάλλοντος

Για **GitHub Models (Δωρεάν)**:
- `GITHUB_TOKEN` - Προσωπικό access token από το GitHub

Για **Υπηρεσίες Azure AI** (προαιρετικό):
- `PROJECT_ENDPOINT` - Endpoint έργου Microsoft Foundry
- `AZURE_OPENAI_API_KEY` - Κλειδί API Azure OpenAI
- `AZURE_OPENAI_ENDPOINT` - URL endpoint Azure OpenAI
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` - Όνομα ανάπτυξης για chat model
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` - Όνομα ανάπτυξης για embeddings
- Επιπλέον ρυθμίσεις Azure όπως στο `.env.example`

## Ροή Ανάπτυξης

### Εκτέλεση Jupyter Notebooks

Κάθε μάθημα περιλαμβάνει πολλαπλά Jupyter notebooks για διαφορετικά πλαίσια:

1. **Εκκινήστε Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Πλοηγηθείτε σε φάκελο μαθήματος** (π.χ., `01-intro-to-ai-agents/code_samples/`)

3. **Ανοίξτε και εκτελέστε τα notebooks:**
   - `*-semantic-kernel.ipynb` - Χρήση πλαισίου Semantic Kernel
   - `*-autogen.ipynb` - Χρήση πλαισίου AutoGen
   - `*-python-agent-framework.ipynb` - Χρήση Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` - Χρήση Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` - Χρήση Azure AI Agent Service

### Εργασία με Διάφορα Πλαίσια Εργασίας

**Semantic Kernel + GitHub Models:**
- Διαθέσιμο δωρεάν επίπεδο με λογαριασμό GitHub
- Κατάλληλο για μάθηση και πειραματισμό
- Μοτίβο αρχείων: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**
- Διαθέσιμο δωρεάν επίπεδο με λογαριασμό GitHub
- Δυνατότητες πολυ-πράκτορα ορχήστρωσης
- Μοτίβο αρχείων: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**
- Πιο πρόσφατο πλαίσιο από τη Microsoft
- Διαθέσιμο σε Python και .NET
- Μοτίβο αρχείων: `*-agent-framework.ipynb`

**Azure AI Agent Service:**
- Απαιτεί συνδρομή Azure
- Χαρακτηριστικά κατάλληλα για παραγωγή
- Μοτίβο αρχείων: `*-azureaiagent.ipynb`

## Οδηγίες Δοκιμών

Αυτό είναι ένα εκπαιδευτικό αποθετήριο με παραδείγματα κώδικα και όχι κώδικα παραγωγής με αυτοματοποιημένες δοκιμές. Για να επαληθεύσετε τη ρύθμισή σας και τις αλλαγές:

### Χειροκίνητη Δοκιμή

1. **Δοκιμάστε το περιβάλλον Python:**
   ```bash
   python --version  # Θα πρέπει να είναι 3.12+
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```

2. **Δοκιμάστε την εκτέλεση notebook:**
   ```bash
   # Μετατροπή τετραδίου σε σενάριο και εκτέλεση (δοκιμές εισαγωγών)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```

3. **Επαληθεύστε τις μεταβλητές περιβάλλοντος:**
   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN missing')"
   ```

### Εκτέλεση Ατομικών Notebooks

Ανοίξτε notebooks σε Jupyter και εκτελέστε τα κελιά διαδοχικά. Κάθε notebook είναι αυτόνομο και περιλαμβάνει:
- Δηλώσεις εισαγωγής
- Φόρτωση ρυθμίσεων
- Υλοποιήσεις ενδεικτικών πρακτόρων
- Αναμενόμενα αποτελέσματα σε markdown κελιά

## Στυλ Κώδικα

### Συμβάσεις Python

- **Έκδοση Python**: 3.12+
- **Στυλ Κώδικα**: Ακολουθείστε τις τυπικές συμβάσεις PEP 8 της Python
- **Notebooks**: Χρησιμοποιήστε σαφή markdown κελιά για επεξηγήσεις
- **Imports**: Ομαδοποιήστε κατά πρότυπη βιβλιοθήκη, τρίτους, τοπικές εισαγωγές

### Συμβάσεις Jupyter Notebook

- Περιλάβετε περιγραφικά markdown κελιά πριν από τα κελιά κώδικα
- Προσθέστε παραδείγματα εξόδου στα notebooks για αναφορά
- Χρησιμοποιήστε σαφή ονόματα μεταβλητών που ταιριάζουν με τις έννοιες του μαθήματος
- Διατηρήστε γραμμική σειρά εκτέλεσης notebook (κελί 1 → 2 → 3...)

### Οργάνωση Αρχείων

```
<lesson-number>-<lesson-name>/
├── README.md                     # Lesson documentation
├── code_samples/
│   ├── <number>-semantic-kernel.ipynb
│   ├── <number>-autogen.ipynb
│   ├── <number>-python-agent-framework.ipynb
│   └── <number>-azureaiagent.ipynb
└── images/
    └── *.png
```

## Κατασκευή και Ανάπτυξη

### Δημιουργία Τεκμηρίωσης

Αυτό το αποθετήριο χρησιμοποιεί Markdown για την τεκμηρίωση:
- Αρχεία README.md σε κάθε φάκελο μαθήματος
- Κύριο README.md στη ρίζα του αποθετηρίου
- Αυτόματο σύστημα μετάφρασης με GitHub Actions

### CI/CD Pipeline

Βρίσκεται στο `.github/workflows/`:

1. **co-op-translator.yml** - Αυτόματη μετάφραση σε περισσότερες από 50 γλώσσες
2. **welcome-issue.yml** - Υποδοχή νέων δημιουργών ζητημάτων (issues)
3. **welcome-pr.yml** - Υποδοχή νέων συμβολών Pull Request

### Ανάπτυξη

Πρόκειται για εκπαιδευτικό αποθετήριο - χωρίς διαδικασία ανάπτυξης. Οι χρήστες:
1. Κάνουν fork ή κλωνοποιούν το αποθετήριο
2. Τρέχουν notebooks τοπικά ή σε GitHub Codespaces
3. Μαθαίνουν τροποποιώντας και πειραματιζόμενοι με παραδείγματα

## Οδηγίες Pull Request

### Πριν την Υποβολή

1. **Δοκιμάστε τις αλλαγές σας:**
   - Τρέξτε πλήρως τα επηρεαζόμενα notebooks
   - Επαληθεύστε ότι όλα τα κελιά εκτελούνται χωρίς σφάλματα
   - Ελέγξτε ότι οι έξοδοι είναι κατάλληλες

2. **Ενημερώσεις τεκμηρίωσης:**
   - Ενημερώστε το README.md αν προσθέτετε νέες έννοιες
   - Προσθέστε σχόλια στα notebooks για πολύπλοκο κώδικα
   - Εξασφαλίστε ότι τα markdown κελιά εξηγούν το σκοπό

3. **Αλλαγές σε αρχεία:**
   - Αποφύγετε το commit αρχείων `.env` (χρησιμοποιήστε `.env.example`)
   - Μην κάνετε commit φακέλους `venv/` ή `__pycache__/`
   - Κρατήστε τις εξόδους notebook όταν δείχνουν έννοιες
   - Αφαιρέστε προσωρινά αρχεία και backup notebooks (`*-backup.ipynb`)

### Μορφή Τίτλου PR

Χρησιμοποιήστε περιγραφικούς τίτλους:
- `[Lesson-XX] Προσθήκη νέου παραδείγματος για <έννοια>`
- `[Fix] Διόρθωση ορθογραφικού λάθους στο README του lesson-XX`
- `[Update] Βελτίωση δείγματος κώδικα στο lesson-XX`
- `[Docs] Ενημέρωση οδηγιών εγκατάστασης`

### Απαιτούμενοι Έλεγχοι

- Τα notebooks πρέπει να εκτελούνται χωρίς σφάλματα
- Τα αρχεία README να είναι σαφή και ακριβή
- Ακολουθείστε τα υπάρχοντα πρότυπα κώδικα στο αποθετήριο
- Διατηρήστε συνέπεια με τα υπόλοιπα μαθήματα

## Επιπλέον Σημειώσεις

### Συχνά Προβλήματα

1. **Αντιστοίχιση έκδοσης Python:**
   - Βεβαιωθείτε ότι χρησιμοποιείται Python 3.12+
   - Ορισμένα πακέτα μπορεί να μη λειτουργούν με παλαιότερες εκδόσεις
   - Χρησιμοποιήστε `python3 -m venv` για ρητή καθορισμένη έκδοση Python

2. **Μεταβλητές περιβάλλοντος:**
   - Πάντα δημιουργείτε `.env` από `.env.example`
   - Μην κάνετε commit το αρχείο `.env` (είναι στο `.gitignore`)
   - Το GitHub token χρειάζεται κατάλληλα δικαιώματα

3. **Σύγκρουση πακέτων:**
   - Χρησιμοποιήστε φρέσκο εικονικό περιβάλλον
   - Εγκαταστήστε από `requirements.txt` αντί μεμονωμένων πακέτων
   - Ορισμένα notebooks μπορεί να απαιτούν επιπλέον πακέτα που αναφέρονται στα markdown κελιά τους

4. **Υπηρεσίες Azure:**
   - Οι υπηρεσίες Azure AI απαιτούν ενεργή συνδρομή
   - Μερικά χαρακτηριστικά περιορίζονται ανά περιοχή
   - Οι περιορισμοί δωρεάν επιπέδου ισχύουν για τα GitHub Models

### Διαδρομή Μάθησης

Συνιστώμενη σειρά μαθημάτων:
1. **00-course-setup** - Ξεκινήστε εδώ για τη ρύθμιση περιβάλλοντος
2. **01-intro-to-ai-agents** - Κατανόηση των θεμελίων AI πρακτόρων
3. **02-explore-agentic-frameworks** - Μάθετε για διαφορετικά πλαίσια εργασίας
4. **03-agentic-design-patterns** - Βασικά πρότυπα σχεδίασης
5. Συνεχίστε τα μαθήματα με αύξοντα αριθμό διαδοχικά

### Επιλογή Πλαισίου Εργασίας

Επιλέξτε πλαίσιο ανάλογα με τους στόχους σας:
- **Μάθηση/Πρωτοτυπία**: Semantic Kernel + GitHub Models (δωρεάν)
- **Πολυ-πρακτορικά συστήματα**: AutoGen
- **Πρόσφατα χαρακτηριστικά**: Microsoft Agent Framework (MAF)
- **Ανάπτυξη παραγωγής**: Azure AI Agent Service

### Λήψη Βοήθειας

- Συμμετέχετε στο [Microsoft Foundry Community Discord](https://aka.ms/ai-agents/discord)
- Ανατρέξτε στα README των μαθημάτων για συγκεκριμένες οδηγίες
- Δείτε το κύριο [README.md](./README.md) για επισκόπηση μαθήματος
- Ανατρέξτε στο [Course Setup](./00-course-setup/README.md) για λεπτομερές οδηγό εγκατάστασης

### Συμμετοχή

Αυτό είναι ένα ανοιχτό εκπαιδευτικό έργο. Καλώς δεχόμενες οι συνεισφορές:
- Βελτίωση των παραδειγμάτων κώδικα
- Διόρθωση λαθών ή ορθογραφικών
- Προσθήκη σχολίων για διευκρίνιση
- Πρόταση νέων θεμάτων για μαθήματα
- Μετάφραση σε επιπλέον γλώσσες

Δείτε τα [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues) για τρέχουσες ανάγκες.

## Συγκεκριμένο Πλαίσιο Έργου

### Υποστήριξη Πολλών Γλωσσών

Αυτό το αποθετήριο χρησιμοποιεί αυτόματο σύστημα μετάφρασης:
- Υποστήριξη σε περισσότερες από 50 γλώσσες
- Μεταφράσεις στους καταλόγους `/translations/<lang-code>/`
- Το GitHub Actions workflow διαχειρίζεται ενημερώσεις μετάφρασης
- Τα αρχεία πηγής είναι στα Αγγλικά στη ρίζα του αποθετηρίου

### Δομή Μαθήματος

Κάθε μάθημα ακολουθεί ένα σταθερό μοτίβο:
1. Μικρογραφία βίντεο με σύνδεσμο
2. Γραπτό περιεχόμενο μαθήματος (README.md)
3. Δείγματα κώδικα σε πολλαπλά πλαίσια
4. Μαθησιακοί στόχοι και προαπαιτούμενα
5. Επιπλέον εκπαιδευτικοί πόροι με συνδέσμους

### Ονομασία Δειγμάτων Κώδικα

Μορφή: `<αριθμός-μαθήματος>-<όνομα-πλαισίου>.ipynb`
- `04-semantic-kernel.ipynb` - Μάθημα 4, Semantic Kernel
- `07-autogen.ipynb` - Μάθημα 7, AutoGen
- `14-python-agent-framework.ipynb` - Μάθημα 14, MAF Python
- `14-dotnet-agent-framework.ipynb` - Μάθημα 14, MAF .NET

### Ειδικοί Φάκελοι

- `translated_images/` - Τοπικοποιημένες εικόνες για μεταφράσεις
- `images/` - Αρχικές εικόνες για το αγγλικό περιεχόμενο
- `.devcontainer/` - Ρυθμίσεις container ανάπτυξης VS Code
- `.github/` - GitHub Actions workflows και πρότυπα

### Εξαρτήσεις

Κύρια πακέτα από `requirements.txt`:
- `autogen-agentchat`, `autogen-core`, `autogen-ext` - πλαίσιο AutoGen
- `semantic-kernel` - πλαίσιο Semantic Kernel
- `agent-framework` - Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` - υπηρεσίες Azure AI
- `azure-search-documents` - ενσωμάτωση Azure AI Search
- `chromadb` - Βάση δεδομένων διανυσμάτων για παραδείγματα RAG
- `chainlit` - Πλαίσιο UI για chat
- `browser_use` - Αυτοματισμός browser για πράκτορες
- `mcp[cli]` - Υποστήριξη Model Context Protocol
- `mem0ai` - Διαχείριση μνήμης για πράκτορες

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Αποποίηση Ευθύνης**:
Αυτό το έγγραφο έχει μεταφραστεί χρησιμοποιώντας την υπηρεσία μετάφρασης με τεχνητή νοημοσύνη [Co-op Translator](https://github.com/Azure/co-op-translator). Παρόλο που επιδιώκουμε την ακρίβεια, παρακαλούμε να γνωρίζετε ότι οι αυτοματοποιημένες μεταφράσεις μπορεί να περιέχουν σφάλματα ή ανακρίβειες. Το πρωτότυπο έγγραφο στη γλώσσα του θεωρείται η επίσημη και αρμόδια πηγή. Για κρίσιμες πληροφορίες συνιστάται η επαγγελματική ανθρώπινη μετάφραση. Δεν φέρουμε ευθύνη για οποιεσδήποτε παρεξηγήσεις ή λανθασμένες ερμηνείες που προκύπτουν από τη χρήση αυτής της μετάφρασης.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->