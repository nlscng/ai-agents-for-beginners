# Εξερεύνηση του Πλαισίου Microsoft Agent

![Agent Framework](../../../translated_images/el/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Εισαγωγή

Αυτό το μάθημα καλύπτει:

- Κατανόηση του Πλαισίου Microsoft Agent: Βασικά Χαρακτηριστικά και Αξία  
- Εξερεύνηση των Κύριων Εννοιών του Πλαισίου Microsoft Agent
- Σύγκριση του MAF με το Semantic Kernel και το AutoGen: Οδηγός Μεταφοράς

## Στόχοι Μάθησης

Μετά την ολοκλήρωση αυτού του μαθήματος, θα γνωρίζετε πώς να:

- Δημιουργείτε παραγωγικούς AI Agents χρησιμοποιώντας το Πλαίσιο Microsoft Agent
- Εφαρμόζετε τα βασικά χαρακτηριστικά του Πλαίσιου Microsoft Agent στα δικά σας περιπτώσεις χρήσης agent
- Μεταφέρετε και ενσωματώνετε υπάρχοντα agentic πλαίσια και εργαλεία  

## Δείγματα Κώδικα

Τα δείγματα κώδικα για το [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) βρίσκονται σε αυτό το αποθετήριο κάτω από τα αρχεία `xx-python-agent-framework` και `xx-dotnet-agent-framework`.

## Κατανόηση του Πλαισίου Microsoft Agent

![Framework Intro](../../../translated_images/el/framework-intro.077af16617cf130c.webp)

Το [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) βασίζεται στην εμπειρία και τις γνώσεις από το Semantic Kernel και το AutoGen. Προσφέρει ευελιξία για την αντιμετώπιση της ποικιλίας των περιπτώσεων χρήσης agentic που παρατηρούνται σε παραγωγικά και ερευνητικά περιβάλλοντα, συμπεριλαμβανομένων:

- **Αλληλουχία agent orchestration** σε σενάρια όπου απαιτούνται βήμα-βήμα ροές εργασίας.
- **Ταυτόχρονη ορχήστρωση** σε σενάρια όπου οι agents πρέπει να ολοκληρώσουν εργασίες ταυτόχρονα.
- **Ορχήστρωση ομαδικής συνομιλίας** σε σενάρια όπου οι agents συνεργάζονται σε μία εργασία.
- **Ανταλλαγή Ορχήστρωσης** σε σενάρια όπου οι agents μεταβιβάζουν την εργασία ο ένας στον άλλο καθώς ολοκληρώνονται τα υποέργα.
- **Μαγνητική Ορχήστρωση** σε σενάρια όπου ένας διαχειριστής agent δημιουργεί και τροποποιεί μια λίστα εργασιών και χειρίζεται το συντονισμό των υποagents για την ολοκλήρωση της εργασίας.

Για την παροχή των AI Agents σε παραγωγή, το MAF παρέχει επίσης δυνατότητες για:

- **Παρατηρησιμότητα** μέσω της χρήσης OpenTelemetry όπου κάθε ενέργεια του AI Agent συμπεριλαμβανομένων των κλήσεων εργαλείων, βημάτων ορχήστρωσης, ροών λογικής και παρακολούθησης απόδοσης γίνεται μέσα από τα dashboards του Microsoft Foundry.
- **Ασφάλεια** με τη φιλοξενία agents εγγενώς στο Microsoft Foundry που περιλαμβάνει ελέγχους ασφαλείας όπως πρόσβαση βάσει ρόλων, διαχείριση ιδιωτικών δεδομένων και ενσωματωμένη ασφάλεια περιεχομένου.
- **Ανθεκτικότητα** καθώς τα νήματα και οι ροές εργασίας των agents μπορούν να παύσουν, να συνεχιστούν και να ανακάμψουν από σφάλματα, επιτρέποντας μακροχρόνιες διαδικασίες.
- **Έλεγχος** καθώς υποστηρίζονται ροές εργασίας με ανθρώπινη συμμετοχή όπου οι εργασίες χαρακτηρίζονται ως απαιτούσες ανθρώπινη έγκριση.

Το Microsoft Agent Framework στοχεύει επίσης στην διαλειτουργικότητα μέσω:

- **Ανεξαρτησίας από το cloud** - Οι agents μπορούν να τρέχουν σε containers, τοπικά και σε πολλαπλά διαφορετικά σύννεφα.
- **Ανεξαρτησίας από παρόχους** - Οι agents μπορούν να δημιουργηθούν μέσω του προτιμώμενου SDK σας, συμπεριλαμβανομένων των Azure OpenAI και OpenAI.
- **Ενσωμάτωσης ανοικτών προτύπων** - Οι agents μπορούν να χρησιμοποιούν πρωτόκολλα όπως Agent-to-Agent (A2A) και Model Context Protocol (MCP) για να ανακαλύπτουν και να χρησιμοποιούν άλλους agents και εργαλεία.
- **Πρόσθετων και συνδετήρων** - Υπάρχουν συνδέσεις σε υπηρεσίες δεδομένων και μνήμης, όπως Microsoft Fabric, SharePoint, Pinecone και Qdrant.

Ας δούμε πώς εφαρμόζονται αυτά τα χαρακτηριστικά σε κάποιες βασικές έννοιες του Microsoft Agent Framework.

## Βασικές Έννοιες του Πλαισίου Microsoft Agent

### Agents

![Agent Framework](../../../translated_images/el/agent-components.410a06daf87b4fef.webp)

**Δημιουργία Agents**

Η δημιουργία agents γίνεται ορίζοντας την υπηρεσία συμπεράσματος (Πάροχος LLM), ένα σύνολο οδηγιών για να ακολουθήσει ο AI Agent, και ένα εκχωρημένο `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Το παραπάνω χρησιμοποιεί το `Azure OpenAI` αλλά οι agents μπορούν να δημιουργηθούν με ποικίλες υπηρεσίες, συμπεριλαμβανομένης της `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

ή απομακρυσμένοι agents που χρησιμοποιούν το πρωτόκολλο A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Εκτέλεση Agents**

Οι agents εκτελούνται χρησιμοποιώντας τις μεθόδους `.run` ή `.run_stream` για αποκρίσεις χωρίς ροή ή με ροή.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Κάθε εκτέλεση agent μπορεί επίσης να έχει επιλογές παραμετροποίησης, όπως `max_tokens` που χρησιμοποιεί ο agent, `tools` που ο agent μπορεί να καλέσει, και ακόμα και το ίδιο το `model` που χρησιμοποιείται για τον agent.

Αυτό είναι χρήσιμο σε περιπτώσεις όπου απαιτούνται συγκεκριμένα μοντέλα ή εργαλεία για την ολοκλήρωση της εργασίας του χρήστη.

**Εργαλεία**

Τα εργαλεία μπορούν να οριστούν τόσο κατά τον ορισμό του agent:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Όταν δημιουργείτε ένα ChatAgent απευθείας

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

όσο και κατά την εκτέλεση του agent:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Εργαλείο παρεχόμενο μόνο για αυτή την εκτέλεση )
```

**Νήματα Agent**

Τα νήματα Agent χρησιμοποιούνται για τη διαχείριση συνομιλιών πολλαπλών γύρων. Τα νήματα μπορούν να δημιουργηθούν είτε:

- Χρησιμοποιώντας `get_new_thread()` που επιτρέπει την αποθήκευση του νήματος με την πάροδο του χρόνου
- Δημιουργώντας ένα νήμα αυτόματα κατά την εκτέλεση ενός agent και διατηρώντας το νήμα μόνο κατά την τρέχουσα εκτέλεση.

Για να δημιουργήσετε ένα νήμα, ο κώδικας είναι:

```python
# Δημιουργήστε ένα νέο νήμα.
thread = agent.get_new_thread() # Εκτελέστε τον πράκτορα με το νήμα.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Μπορείτε επίσης να σειριοποιήσετε το νήμα για να αποθηκευτεί για μελλοντική χρήση:

```python
# Δημιουργήστε ένα νέο νήμα.
thread = agent.get_new_thread() 

# Εκτελέστε τον πράκτορα με το νήμα.

response = await agent.run("Hello, how are you?", thread=thread) 

# Σειριοποιήστε το νήμα για αποθήκευση.

serialized_thread = await thread.serialize() 

# Αποσειριοποιήστε την κατάσταση του νήματος μετά τη φόρτωση από την αποθήκευση.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware Agent**

Οι agents αλληλεπιδρούν με εργαλεία και LLMs για να ολοκληρώσουν τις εργασίες των χρηστών. Σε ορισμένα σενάρια, θέλουμε να εκτελούμε ή να παρακολουθούμε ενδιάμεσες αλληλεπιδράσεις. Το middleware agent μας επιτρέπει να το κάνουμε μέσω:

*Middleware Λειτουργίας*

Αυτό το middleware επιτρέπει την εκτέλεση μιας ενέργειας ανάμεσα στον agent και μια συνάρτηση/εργαλείο που καλείται. Ένα παράδειγμα χρήσης είναι η καταγραφή κλήσεων λειτουργιών.

Στον κώδικα παρακάτω, το `next` ορίζει αν θα κληθεί το επόμενο middleware ή η πραγματική συνάρτηση.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Προεπεξεργασία: Καταγραφή πριν από την εκτέλεση της συνάρτησης
    print(f"[Function] Calling {context.function.name}")

    # Συνέχεια στην επόμενη μεσολάβηση ή εκτέλεση συνάρτησης
    await next(context)

    # Μετα-επεξεργασία: Καταγραφή μετά την εκτέλεση της συνάρτησης
    print(f"[Function] {context.function.name} completed")
```

*Middleware Συνομιλίας*

Αυτό το middleware επιτρέπει την εκτέλεση ή καταγραφή μιας ενέργειας μεταξύ του agent και των αιτημάτων προς το LLM.

Περιλαμβάνει σημαντικές πληροφορίες, όπως τα `messages` που αποστέλλονται στην υπηρεσία AI.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Προεπεξεργασία: Καταγραφή πριν από την κλήση AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Συνέχεια στο επόμενο middleware ή υπηρεσία AI
    await next(context)

    # Μεταεπεξεργασία: Καταγραφή μετά την απάντηση AI
    print("[Chat] AI response received")

```

**Μνήμη Agent**

Όπως καλύφθηκε στο μάθημα `Agentic Memory`, η μνήμη είναι ένα σημαντικό στοιχείο για τη λειτουργία του agent σε διαφορετικά συμφραζόμενα. Το MAF προσφέρει διάφορους τύπους μνήμης:

*Αποθήκευση στη Μνήμη*

Αυτή είναι η μνήμη που αποθηκεύεται στα νήματα κατά τη διάρκεια του χρόνου εκτέλεσης της εφαρμογής.

```python
# Δημιουργήστε ένα νέο νήμα.
thread = agent.get_new_thread() # Εκτελέστε τον πράκτορα με το νήμα.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Επίμονες Εντολές*

Αυτή η μνήμη χρησιμοποιείται για την αποθήκευση ιστορικού συνομιλιών μεταξύ διαφορετικών συνεδριών. Ορίζεται μέσω της `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Δημιουργήστε μια προσαρμοσμένη αποθήκη μηνυμάτων
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Δυναμική Μνήμη*

Αυτή η μνήμη προστίθεται στο συμφραζόμενο πριν από την εκτέλεση των agents. Αυτές οι μνήμες μπορούν να αποθηκευτούν σε εξωτερικές υπηρεσίες όπως mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Χρήση του Mem0 για προχωρημένες δυνατότητες μνήμης
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**Παρατηρησιμότητα Agent**

Η παρατηρησιμότητα είναι σημαντική για την κατασκευή αξιόπιστων και διαχειρίσιμων συστημάτων agentic. Το MAF ενσωματώνεται με το OpenTelemetry για παροχή ιχνηλάτησης και μετρητών για καλύτερη παρατηρησιμότητα.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # κάνε κάτι
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Ροές Εργασίας

Το MAF προσφέρει ροές εργασίας που είναι προκαθορισμένα βήματα για την ολοκλήρωση μιας εργασίας και περιλαμβάνουν AI agents ως συνιστώσες αυτών των βημάτων.

Οι ροές εργασίας αποτελούνται από διάφορα εξαρτήματα που επιτρέπουν καλύτερο έλεγχο της ροής. Επιπλέον, οι ροές εργασίας επιτρέπουν **πολλαπλή ορχήστρωση agents** και **checkpointing** για την αποθήκευση καταστάσεων ροής εργασίας.

Τα βασικά στοιχεία μιας ροής εργασίας είναι:

**Εκτελεστές**

Οι εκτελεστές λαμβάνουν εισερχόμενα μηνύματα, εκτελούν τις ανατεθειμένες εργασίες, και παράγουν ένα εξερχόμενο μήνυμα. Αυτό προωθεί τη ροή εργασίας προς την ολοκλήρωση της μεγαλύτερης εργασίας. Οι εκτελεστές μπορεί να είναι είτε AI agents είτε προσαρμοσμένη λογική.

**Άκρες**

Οι άκρες χρησιμοποιούνται για να ορίσουν τη ροή μηνυμάτων σε μια ροή εργασίας. Αυτές μπορεί να είναι:

*Άμεσες Άκρες* - Απλές συνδέσεις ένα-προς-ένα μεταξύ εκτελεστών:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Υπό όρους Άκρες* - Ενεργοποιούνται μετά την ικανοποίηση συγκεκριμένης συνθήκης. Για παράδειγμα, όταν δεν υπάρχουν διαθέσιμα δωμάτια ξενοδοχείου, ένας εκτελεστής μπορεί να προτείνει άλλες επιλογές.

*Άκρες τύπου switch-case* - Δρομολογούν μηνύματα σε διαφορετικούς εκτελεστές βάσει ορισμένων συνθηκών. Για παράδειγμα, αν ο πελάτης ταξιδιού έχει προτεραιότητα, οι εργασίες του θα χειριστούν μέσω άλλης ροής εργασίας.

*Fan-out Άκρες* - Στέλνουν ένα μήνυμα σε πολλαπλούς στόχους.

*Fan-in Άκρες* - Συλλέγουν πολλαπλά μηνύματα από διάφορους εκτελεστές και τα στέλνουν σε έναν στόχο.

**Γεγονότα**

Για να παρέχει καλύτερη παρατηρησιμότητα στις ροές εργασίας, το MAF προσφέρει ενσωματωμένα γεγονότα για την εκτέλεση, όπως:

- `WorkflowStartedEvent` - Ξεκινά η εκτέλεση ροής εργασίας
- `WorkflowOutputEvent` - Η ροή εργασίας παράγει έξοδο
- `WorkflowErrorEvent` - Η ροή εργασίας αντιμετωπίζει σφάλμα
- `ExecutorInvokeEvent` - Ο εκτελεστής ξεκινά επεξεργασία
- `ExecutorCompleteEvent` - Ο εκτελεστής ολοκληρώνει την επεξεργασία
- `RequestInfoEvent` - Ένα αίτημα έχει εκδοθεί

## Μεταφορά από Άλλα Πλαίσια (Semantic Kernel και AutoGen)

### Διαφορές μεταξύ MAF και Semantic Kernel

**Απλοποιημένη Δημιουργία Agent**

Το Semantic Kernel βασίζεται στη δημιουργία ενός αντικειμένου Kernel για κάθε agent. Το MAF χρησιμοποιεί μια απλοποιημένη προσέγγιση με επεκτάσεις για τους κύριους παρόχους.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Δημιουργία Νημάτων Agent**

Το Semantic Kernel απαιτεί τη χειροκίνητη δημιουργία νημάτων. Στο MAF, ο agent αντιστοιχίζεται απευθείας σε ένα νήμα.

```python
thread = agent.get_new_thread() # Εκτελέστε τον πράκτορα με το νήμα.
```

**Εγγραφή Εργαλείων**

Στο Semantic Kernel, τα εργαλεία εγγράφονται στον Kernel και ο Kernel περνάει μετά στον agent. Στο MAF, τα εργαλεία καταχωρούνται απευθείας κατά τη δημιουργία του agent.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Διαφορές μεταξύ MAF και AutoGen

**Ομάδες έναντι Ροών Εργασίας**

Οι `Teams` είναι η δομή συμβάντων για τη συμβάντική δραστηριότητα με agents στο AutoGen. Το MAF χρησιμοποιεί `Workflows` που δρομολογούν δεδομένα προς τους εκτελεστές μέσω ενός γράφου.

**Δημιουργία Εργαλείων**

Το AutoGen χρησιμοποιεί το `FunctionTool` για να τυλίγει συναρτήσεις που μπορούν να καλέσουν οι agents. Το MAF χρησιμοποιεί το @ai_function που λειτουργεί παρόμοια αλλά επίσης υπολογίζει αυτόματα τα σχήματα για κάθε συνάρτηση.

**Συμπεριφορά Agent**

Οι agents στο AutoGen είναι κατά κανόνα μονόστροφα εκτός αν οριστεί `max_tool_iterations` σε υψηλότερη τιμή. Στο MAF, ο `ChatAgent` είναι από προεπιλογή πολύστροφος, πράγμα που σημαίνει ότι συνεχίζει να καλεί εργαλεία μέχρι να ολοκληρωθεί η εργασία του χρήστη.

## Δείγματα Κώδικα

Τα δείγματα κώδικα για το Microsoft Agent Framework βρίσκονται σε αυτό το αποθετήριο κάτω από τα αρχεία `xx-python-agent-framework` και `xx-dotnet-agent-framework`.

## Έχετε Περαιτέρω Ερωτήσεις για το Microsoft Agent Framework;

Ενταχθείτε στο [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) για να συναντήσετε άλλους μαθητές, να παρακολουθήσετε ώρες γραφείου και να λάβετε απαντήσεις στις ερωτήσεις σας για τους AI Agents.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Αποποίηση ευθυνών**:  
Αυτό το έγγραφο έχει μεταφραστεί χρησιμοποιώντας την υπηρεσία αυτόματης μετάφρασης AI [Co-op Translator](https://github.com/Azure/co-op-translator). Παρόλο που επιδιώκουμε ακρίβεια, παρακαλούμε να λάβετε υπόψη ότι οι αυτοματοποιημένες μεταφράσεις ενδέχεται να περιέχουν σφάλματα ή ανακρίβειες. Το πρωτότυπο έγγραφο στη μητρική του γλώσσα πρέπει να θεωρείται η επίσημη πηγή. Για κρίσιμες πληροφορίες, συνιστάται επαγγελματική ανθρώπινη μετάφραση. Δεν φέρουμε ευθύνη για τυχόν παρερμηνείες ή παρανοήσεις που προκύπτουν από τη χρήση αυτής της μετάφρασης.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->