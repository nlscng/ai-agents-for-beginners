[![Πώς να Σχεδιάσετε Καλούς Πράκτορες Τεχνητής Νοημοσύνης](../../../translated_images/el/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(Κάντε κλικ στην παραπάνω εικόνα για να δείτε το βίντεο αυτού του μαθήματος)_

# Σχεδιαστικό Πρότυπο Χρήσης Εργαλείων

Τα εργαλεία είναι ενδιαφέροντα επειδή επιτρέπουν στους πράκτορες ΤΝ να έχουν ένα ευρύτερο φάσμα δυνατοτήτων. Αντί ο πράκτορας να έχει ένα περιορισμένο σύνολο ενεργειών που μπορεί να εκτελέσει, με την προσθήκη ενός εργαλείου, ο πράκτορας μπορεί πλέον να εκτελέσει μια ευρεία γκάμα ενεργειών. Σε αυτό το κεφάλαιο, θα εξετάσουμε το Σχεδιαστικό Πρότυπο Χρήσης Εργαλείων, που περιγράφει πώς οι πράκτορες ΤΝ μπορούν να χρησιμοποιούν συγκεκριμένα εργαλεία για να επιτύχουν τους στόχους τους.

## Εισαγωγή

Σε αυτό το μάθημα, επιδιώκουμε να απαντήσουμε στις ακόλουθες ερωτήσεις:

- Τι είναι το σχεδιαστικό πρότυπο χρήσης εργαλείων;
- Σε ποιες περιπτώσεις χρήσης μπορεί να εφαρμοστεί;
- Ποια είναι τα στοιχεία/δομικά τμήματα που χρειάζονται για την υλοποίηση του σχεδιαστικού προτύπου;
- Ποιες είναι οι ειδικές παρατηρήσεις για τη χρήση του Σχεδιαστικού Προτύπου Χρήσης Εργαλείων για την κατασκευή αξιόπιστων πρακτόρων ΤΝ;

## Στόχοι Μάθησης

Μετά την ολοκλήρωση αυτού του μαθήματος, θα είστε σε θέση να:

- Ορίσετε το Σχεδιαστικό Πρότυπο Χρήσης Εργαλείων και το σκοπό του.
- Αναγνωρίσετε περιπτώσεις χρήσης όπου το Σχεδιαστικό Πρότυπο Χρήσης Εργαλείων είναι εφαρμόσιμο.
- Κατανοήσετε τα βασικά στοιχεία που απαιτούνται για την υλοποίηση του σχεδιαστικού προτύπου.
- Αναγνωρίσετε παρατηρήσεις για την εξασφάλιση αξιοπιστίας στους πράκτορες ΤΝ που χρησιμοποιούν αυτό το σχεδιαστικό πρότυπο.

## Τι είναι το Σχεδιαστικό Πρότυπο Χρήσης Εργαλείων;

Το **Σχεδιαστικό Πρότυπο Χρήσης Εργαλείων** εστιάζει στη δυνατότητα των LLMs να αλληλεπιδρούν με εξωτερικά εργαλεία για την επίτευξη συγκεκριμένων στόχων. Τα εργαλεία είναι κώδικας που μπορεί να εκτελεστεί από έναν πράκτορα για να εκτελέσει ενέργειες. Ένα εργαλείο μπορεί να είναι μια απλή λειτουργία όπως ένας αριθμομηχανή, ή μια κλήση API σε υπηρεσία τρίτου μέρους όπως αναζήτηση τιμής μετοχής ή πρόγνωση καιρού. Στο πλαίσιο των πρακτόρων ΤΝ, τα εργαλεία σχεδιάζονται ώστε να εκτελούνται από πράκτορες σε απάντηση σε **κλήσεις λειτουργιών που παράγονται από το μοντέλο**.

## Σε ποιες περιπτώσεις χρήσης μπορεί να εφαρμοστεί;

Οι πράκτορες ΤΝ μπορούν να αξιοποιήσουν εργαλεία για να ολοκληρώσουν πολύπλοκες εργασίες, να αντλήσουν πληροφορίες ή να λάβουν αποφάσεις. Το σχεδιαστικό πρότυπο χρήσης εργαλείων χρησιμοποιείται συχνά σε σενάρια που απαιτούν δυναμική αλληλεπίδραση με εξωτερικά συστήματα, όπως βάσεις δεδομένων, web services ή διερμηνείς κώδικα. Αυτή η ικανότητα είναι χρήσιμη για πολλούς διαφορετικούς σκοπούς, συμπεριλαμβανομένων:

- **Δυναμική Ανάκτηση Πληροφοριών:** Οι πράκτορες μπορούν να ζητούν δεδομένα από εξωτερικά APIs ή βάσεις δεδομένων για να αντλήσουν ενημερωμένα δεδομένα (π.χ., ερωτήματα σε βάση SQLite για ανάλυση δεδομένων, ανάκτηση τιμών μετοχών ή πληροφοριών καιρού).
- **Εκτέλεση και Ερμηνεία Κώδικα:** Οι πράκτορες μπορούν να εκτελέσουν κώδικα ή σενάρια για επίλυση μαθηματικών προβλημάτων, παραγωγή αναφορών ή εκτέλεση προσομοιώσεων.
- **Αυτοματοποίηση Ροής Εργασίας:** Αυτοματισμός επαναλαμβανόμενων ή πολύ-βηματικών εργασιών ενσωματώνοντας εργαλεία όπως χρονοπρογραμματιστές εργασιών, υπηρεσίες email ή data pipelines.
- **Υποστήριξη Πελατών:** Οι πράκτορες μπορούν να αλληλεπιδρούν με συστήματα CRM, πλατφόρμες ticketing ή βάσεις γνώσεων για να επιλύουν ερωτήματα χρηστών.
- **Δημιουργία και Επεξεργασία Περιεχομένου:** Οι πράκτορες μπορούν να αξιοποιούν εργαλεία όπως έλεγχοι γραμματικής, συνοψιστές κειμένων ή αξιολογητές ασφάλειας περιεχομένου για να βοηθήσουν σε εργασίες δημιουργίας περιεχομένου.

## Ποια είναι τα στοιχεία/δομικά τμήματα που χρειάζονται για την υλοποίηση του σχεδιαστικού προτύπου χρήσης εργαλείων;

Αυτά τα δομικά τμήματα επιτρέπουν στον πράκτορα ΤΝ να εκτελεί ένα ευρύ φάσμα εργασιών. Ας δούμε τα βασικά στοιχεία που απαιτούνται για την υλοποίηση του Σχεδιαστικού Προτύπου Χρήσης Εργαλείων:

- **Σχήματα Λειτουργίας/Εργαλείου**: Αναλυτικοί ορισμοί των διαθέσιμων εργαλείων, περιλαμβανομένων ονόματος λειτουργίας, σκοπού, απαιτούμενων παραμέτρων και αναμενόμενων αποτελεσμάτων. Αυτά τα σχήματα επιτρέπουν στον LLM να κατανοεί ποια εργαλεία είναι διαθέσιμα και πώς να κατασκευάζει έγκυρα αιτήματα.

- **Λογική Εκτέλεσης Λειτουργίας**: Καθορίζει πώς και πότε καλούνται τα εργαλεία με βάση την πρόθεση του χρήστη και το πλαίσιο της συνομιλίας. Αυτό μπορεί να περιλαμβάνει μονάδες σχεδιασμού, μηχανισμούς δρομολόγησης ή ροές με συνθήκες που καθορίζουν δυναμικά τη χρήση εργαλείων.

- **Σύστημα Διαχείρισης Μηνυμάτων**: Συστατικά που διαχειρίζονται τη ροή της συνομιλίας μεταξύ εισόδων χρήστη, απαντήσεων LLM, κλήσεων εργαλείων και αποτελεσμάτων εργαλείων.

- **Πλαίσιο Ενσωμάτωσης Εργαλείων**: Υποδομή που συνδέει τον πράκτορα με διάφορα εργαλεία, είτε είναι απλές λειτουργίες είτε πολύπλοκες εξωτερικές υπηρεσίες.

- **Διαχείριση Σφαλμάτων & Επαλήθευση**: Μηχανισμοί για τη διαχείριση αποτυχιών εκτέλεσης εργαλείων, επικύρωσης παραμέτρων και διαχείρισης απροσδόκητων αποκρίσεων.

- **Διαχείριση Κατάστασης**: Παρακολουθεί το πλαίσιο της συνομιλίας, προηγούμενες αλληλεπιδράσεις με εργαλεία και επίμονα δεδομένα για να εξασφαλίσει συνέπεια σε πολλαπλές στροφές αλληλεπίδρασης.

Έπειτα, ας δούμε την Κλήση Λειτουργίας/Εργαλείου με περισσότερες λεπτομέρειες.
 
### Κλήση Λειτουργίας/Εργαλείου

Η κλήση λειτουργίας είναι ο κύριος τρόπος που επιτρέπουμε στα Μεγάλα Γλωσσικά Μοντέλα (LLMs) να αλληλεπιδρούν με εργαλεία. Συχνά θα δείτε τους όρους 'Λειτουργία' και 'Εργαλείο' να χρησιμοποιούνται εναλλακτικά επειδή οι 'λειτουργίες' (μπλοκ επαναχρησιμοποιήσιμου κώδικα) είναι τα 'εργαλεία' που οι πράκτορες χρησιμοποιούν για να εκτελέσουν εργασίες. Για να κληθεί ο κώδικας μιας λειτουργίας, ένα LLM πρέπει να συγκρίνει το αίτημα του χρήστη με την περιγραφή της λειτουργίας. Για αυτό στέλνουμε στο LLM ένα σχήμα που περιέχει τις περιγραφές όλων των διαθέσιμων λειτουργιών. Το LLM στη συνέχεια επιλέγει την πιο κατάλληλη λειτουργία για την εργασία και επιστρέφει το όνομά της και τα επιχειρήματά της. Η επιλεγμένη λειτουργία εκτελείται, η απάντησή της στέλνεται πίσω στο LLM, που χρησιμοποιεί την πληροφορία για να απαντήσει στο αίτημα του χρήστη.

Για να υλοποιήσουν οι προγραμματιστές την κλήση λειτουργίας για πράκτορες, θα χρειαστείτε:

1. Ένα μοντέλο LLM που υποστηρίζει κλήση λειτουργιών
2. Ένα σχήμα που περιέχει περιγραφές λειτουργιών
3. Τον κώδικα για κάθε περιγραφόμενη λειτουργία

Ας χρησιμοποιήσουμε το παράδειγμα της λήψης της τρέχουσας ώρας σε μια πόλη για να το απεικονίσουμε:

1. **Αρχικοποίηση ενός LLM που υποστηρίζει κλήση λειτουργίας:**

    Δεν υποστηρίζουν όλα τα μοντέλα κλήση λειτουργιών, οπότε είναι σημαντικό να ελέγξετε αν το LLM που χρησιμοποιείτε το υποστηρίζει. Το <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">Azure OpenAI</a> υποστηρίζει κλήση λειτουργιών. Μπορούμε να ξεκινήσουμε ξεκινώντας τον πελάτη Azure OpenAI. 

    ```python
    # Αρχικοποίηση του πελάτη Azure OpenAI
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **Δημιουργήστε ένα Σχήμα Λειτουργίας**:

    Στη συνέχεια θα ορίσουμε ένα JSON σχήμα που περιέχει το όνομα της λειτουργίας, περιγραφή του τι κάνει η λειτουργία και τα ονόματα και περιγραφές των παραμέτρων της λειτουργίας.
    Έπειτα θα περάσουμε αυτό το σχήμα στον πελάτη που δημιουργήσαμε προηγουμένως, μαζί με το αίτημα του χρήστη να βρει την ώρα στο Σαν Φρανσίσκο. Το σημαντικό που πρέπει να σημειωθεί είναι ότι αυτό που επιστρέφεται είναι μια **κλήση εργαλείου**, **όχι** η τελική απάντηση στο ερώτημα. Όπως αναφέρθηκε νωρίτερα, το LLM επιστρέφει το όνομα της λειτουργίας που επέλεξε για την εργασία και τα επιχειρήματα που θα περαστούν σε αυτή.

    ```python
    # Περιγραφή λειτουργίας για το μοντέλο να διαβάσει
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # Αρχικό μήνυμα χρήστη
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # Πρώτη κλήση API: Ζητήστε από το μοντέλο να χρησιμοποιήσει τη λειτουργία
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # Επεξεργασία της απάντησης του μοντέλου
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **Ο κώδικας της λειτουργίας που απαιτείται για την εκτέλεση της εργασίας:**

    Τώρα που το LLM έχει επιλέξει ποια λειτουργία πρέπει να εκτελεστεί, πρέπει να υλοποιηθεί και να εκτελεστεί ο κώδικας που εκτελεί την εργασία.
    Μπορούμε να υλοποιήσουμε τον κώδικα για να πάρουμε την τρέχουσα ώρα σε Python. Θα χρειαστεί επίσης να γράψουμε τον κώδικα για να εξάγουμε το όνομα και τα επιχειρήματα από το response_message για να πάρουμε το τελικό αποτέλεσμα.

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # Διαχείριση κλήσεων συναρτήσεων
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # Δεύτερη κλήση API: Λήψη της τελικής απόκρισης από το μοντέλο
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

Η κλήση λειτουργίας είναι στο επίκεντρο των περισσότερων, αν όχι όλων, σχεδιαστικών προτύπων χρήσης εργαλείων των πρακτόρων, ωστόσο η υλοποίησή της από την αρχή μπορεί μερικές φορές να είναι δύσκολη.
Όπως μάθαμε στο [Μάθημα 2](../../../02-explore-agentic-frameworks), τα πλαίσια πράκτορα (agentic frameworks) μας παρέχουν προ-κατασκευασμένα δομικά τμήματα για την υλοποίηση χρήσης εργαλείων.
 
## Παραδείγματα Χρήσης Εργαλείων με Πλαίσια Πράκτορα

Εδώ είναι μερικά παραδείγματα για το πώς μπορείτε να υλοποιήσετε το Σχεδιαστικό Πρότυπο Χρήσης Εργαλείων χρησιμοποιώντας διαφορετικά πλαίσια πράκτορα:

### Semantic Kernel

Το <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Semantic Kernel</a> είναι ένα ανοιχτού κώδικα πλαίσιο AI για προγραμματιστές .NET, Python και Java που εργάζονται με Μεγάλα Γλωσσικά Μοντέλα (LLMs). Απλοποιεί τη διαδικασία χρήσης κλήσης λειτουργίας περιγράφοντας αυτόματα τις λειτουργίες σας και τις παραμέτρους τους στο μοντέλο μέσω μιας διαδικασίας που ονομάζεται <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">σειριοποίηση</a>. Επίσης διαχειρίζεται την αμφίδρομη επικοινωνία μεταξύ του μοντέλου και του κώδικά σας. Ένα ακόμα πλεονέκτημα της χρήσης ενός agentic framework όπως το Semantic Kernel είναι ότι σας επιτρέπει να έχετε πρόσβαση σε προ-κατασκευασμένα εργαλεία όπως το <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">File Search</a> και τον <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Code Interpreter</a>.

Το παρακάτω διάγραμμα απεικονίζει τη διαδικασία κλήσης λειτουργίας με το Semantic Kernel:

![function calling](../../../translated_images/el/functioncalling-diagram.a84006fc287f6014.webp)

Στο Semantic Kernel οι λειτουργίες/εργαλεία ονομάζονται <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">Plugins</a>. Μπορούμε να μετατρέψουμε τη λειτουργία `get_current_time` που είδαμε νωρίτερα σε plugin μετατρέποντάς την σε κλάση που περιέχει τη λειτουργία. Μπορούμε επίσης να εισάγουμε τον διακοσμητή `kernel_function`, που δέχεται την περιγραφή της λειτουργίας. Όταν δημιουργήσετε έναν kernel με το GetCurrentTimePlugin, ο kernel θα σειριοποιήσει αυτόματα τη λειτουργία και τις παραμέτρους της, δημιουργώντας το σχήμα που θα σταλεί στο LLM στη διαδικασία.

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# Δημιουργήστε τον πυρήνα
kernel = Kernel()

# Δημιουργήστε το πρόσθετο
get_current_time_plugin = GetCurrentTimePlugin(location)

# Προσθέστε το πρόσθετο στον πυρήνα
kernel.add_plugin(get_current_time_plugin)
```
  
### Azure AI Agent Service

Το <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a> είναι ένα νεότερο πλαίσιο πράκτορα σχεδιασμένο να δίνει στους προγραμματιστές τη δυνατότητα να δημιουργούν, αναπτύσσουν και κλιμακώνουν με ασφάλεια, υψηλής ποιότητας και επεκτάσιμους πράκτορες ΤΝ χωρίς να χρειάζεται να διαχειρίζονται τους υποκείμενους πόρους υπολογισμού και αποθήκευσης. Είναι ιδιαίτερα χρήσιμο για επιχειρηματικές εφαρμογές μιας και είναι μια πλήρως διαχειριζόμενη υπηρεσία με επίπεδο ασφάλειας enterprise.

Σε σύγκριση με την ανάπτυξη με άμεσο API των LLM, το Azure AI Agent Service παρέχει κάποια πλεονεκτήματα, μεταξύ άλλων:

- Αυτόματη κλήση εργαλείων – δεν χρειάζεται να αναλύετε μια κλήση εργαλείου, να καλείτε το εργαλείο και να διαχειρίζεστε την απόκριση· όλα αυτά γίνονται πλέον στον server
- Ασφαλής διαχείριση δεδομένων – αντί να διαχειρίζεστε την κατάσταση της συνομιλίας, μπορείτε να βασιστείτε σε threads που αποθηκεύουν όλες τις πληροφορίες που χρειάζεστε
- Εργαλεία έτοιμα προς χρήση – εργαλεία που μπορείτε να χρησιμοποιήσετε για να αλληλεπιδράσετε με τις πηγές δεδομένων σας, όπως Bing, Azure AI Search και Azure Functions.

Τα εργαλεία που είναι διαθέσιμα στο Azure AI Agent Service μπορούν να χωριστούν σε δύο κατηγορίες:

1. Εργαλεία Γνώσης:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Υπόβαθρο με Bing Search</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">Αναζήτηση Αρχείων</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>

2. Εργαλεία Δράσης:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">Κλήση Λειτουργιών</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">Ερμηνευτής Κώδικα</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">Εργαλεία ορισμένα με OpenAPI</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>

Η υπηρεσία Agent επιτρέπει να χρησιμοποιούμε αυτά τα εργαλεία μαζί ως `toolset`. Επίσης, χρησιμοποιεί `threads` που παρακολουθούν το ιστορικό των μηνυμάτων μιας συγκεκριμένης συνομιλίας.

Φανταστείτε ότι είστε πωλητής σε μια εταιρεία που ονομάζεται Contoso. Θέλετε να αναπτύξετε έναν συνομιλητικό πράκτορα που να μπορεί να απαντά σε ερωτήσεις σχετικά με τα δεδομένα πωλήσεών σας.

Η ακόλουθη εικόνα απεικονίζει πώς θα μπορούσατε να χρησιμοποιήσετε το Azure AI Agent Service για να αναλύσετε τα δεδομένα πωλήσεών σας:

![Agentic Service In Action](../../../translated_images/el/agent-service-in-action.34fb465c9a84659e.webp)

Για να χρησιμοποιήσουμε οποιοδήποτε από αυτά τα εργαλεία με την υπηρεσία μπορούμε να δημιουργήσουμε έναν πελάτη και να ορίσουμε ένα εργαλείο ή set εργαλείων. Για να το υλοποιήσουμε πρακτικά, μπορούμε να χρησιμοποιήσουμε τον ακόλουθο κώδικα Python. Το LLM θα μπορεί να κοιτάξει το toolset και να αποφασίσει αν θα χρησιμοποιήσει τη συνάρτηση που δημιουργήσατε, `fetch_sales_data_using_sqlite_query`, ή τον προ-κατασκευασμένο Ερμηνευτή Κώδικα ανάλογα με το αίτημα του χρήστη.

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # συνάρτηση fetch_sales_data_using_sqlite_query που μπορεί να βρεθεί σε ένα αρχείο fetch_sales_data_functions.py.
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Αρχικοποίηση σετ εργαλείων
toolset = ToolSet()

# Αρχικοποίηση αντιπροσώπου κλήσης συνάρτησης με τη συνάρτηση fetch_sales_data_using_sqlite_query και προσθήκη της στο σετ εργαλείων
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# Αρχικοποίηση εργαλείου κώδικα διερμηνέα και προσθήκη του στο σετ εργαλείων.
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## Ποιες είναι οι ειδικές παρατηρήσεις για τη χρήση του Σχεδιαστικού Προτύπου Χρήσης Εργαλείων για την κατασκευή αξιόπιστων πρακτόρων ΤΝ;

Ένα κοινό πρόβλημα με το δυναμικά δημιουργημένο SQL από LLMs είναι η ασφάλεια, ιδίως ο κίνδυνος SQL injection ή κακόβουλων ενεργειών, όπως η διαγραφή ή η αλλοίωση της βάσης δεδομένων. Αν και αυτοί οι κίνδυνοι είναι πραγματικοί, μπορούν να αντιμετωπιστούν αποτελεσματικά με τη σωστή ρύθμιση των δικαιωμάτων πρόσβασης στη βάση δεδομένων. Για τις περισσότερες βάσεις δεδομένων αυτό περιλαμβάνει τη ρύθμιση της βάσης ως μόνο-ανάγνωσης. Για υπηρεσίες βάσεων δεδομένων όπως PostgreSQL ή Azure SQL, η εφαρμογή θα πρέπει να έχει έναν ρόλο μόνο-ανάγνωσης (SELECT).

Η εκτέλεση της εφαρμογής σε ένα ασφαλές περιβάλλον ενισχύει περαιτέρω την προστασία. Σε επιχειρηματικά σενάρια, τα δεδομένα συνήθως εξάγονται και μετασχηματίζονται από λειτουργικά συστήματα σε μια βάση δεδομένων ή αποθήκη δεδομένων μόνο-ανάγνωσης με ένα φιλικό προς τον χρήστη σχήμα. Αυτή η προσέγγιση διασφαλίζει ότι τα δεδομένα είναι ασφαλή, βελτιστοποιημένα για απόδοση και προσβασιμότητα, και ότι η εφαρμογή έχει περιορισμένη, μόνο-ανάγνωσης πρόσβαση.

## Παραδειγματικοί Κώδικες
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## Έχετε Περισσότερες Ερωτήσεις σχετικά με τα Σχέδια Σχεδίασης για τη Χρήση Εργαλείων;

Εγγραφείτε στο [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) για να συναντήσετε άλλους μαθητές, να παρακολουθήσετε ώρες γραφείου και να λάβετε απαντήσεις στις ερωτήσεις σας για τους Πράκτορες Τεχνητής Νοημοσύνης.

## Πρόσθετοι Πόροι

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Εργαστήριο Υπηρεσίας Πρακτόρων Azure AI</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Εργαστήριο Πολυπράκτορα Δημιουργικού Συγγραφέα Contoso</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Οδηγός Κλήσης Συναρτήσεων Semantic Kernel</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Ερμηνευτής Κώδικα Semantic Kernel</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Εργαλεία Autogen</a>

## Προηγούμενο Μάθημα

[Κατανόηση των Σχεδίων Σχεδίασης Πρακτόρων](../03-agentic-design-patterns/README.md)

## Επόμενο Μάθημα

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Αποποίηση ευθυνών**:  
Το παρόν έγγραφο έχει μεταφραστεί χρησιμοποιώντας την υπηρεσία αυτόματης μετάφρασης με τεχνητή νοημοσύνη [Co-op Translator](https://github.com/Azure/co-op-translator). Παρόλο που επιδιώκουμε την ακρίβεια, παρακαλούμε να έχετε υπόψη ότι οι αυτόματες μεταφράσεις ενδέχεται να περιέχουν λάθη ή ανακρίβειες. Το πρωτότυπο έγγραφο στη μητρική του γλώσσα πρέπει να θεωρείται ως η αξιόπιστη πηγή. Για σημαντικές πληροφορίες συνιστάται η επαγγελματική μετάφραση από ανθρώπους. Δεν φέρουμε ευθύνη για τυχόν παρανοήσεις ή λανθασμένες ερμηνείες που προκύπτουν από τη χρήση αυτής της μετάφρασης.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->