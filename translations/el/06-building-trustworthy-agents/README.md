[![Agents Τεχνητής Νοημοσύνης Αξιόπιστοι](../../../translated_images/el/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Κάντε κλικ στην παραπάνω εικόνα για να δείτε το βίντεο αυτού του μαθήματος)_

# Δημιουργία Αξιόπιστων Agents Τεχνητής Νοημοσύνης

## Εισαγωγή

Αυτό το μάθημα θα καλύψει:

- Πώς να κατασκευάσετε και να αναπτύξετε ασφαλείς και αποτελεσματικούς Agents Τεχνητής Νοημοσύνης
- Σημαντικές παραμέτρους ασφάλειας κατά την ανάπτυξη Agents Τεχνητής Νοημοσύνης.
- Πώς να διατηρήσετε την ιδιωτικότητα των δεδομένων και των χρηστών κατά την ανάπτυξη Agents Τεχνητής Νοημοσύνης.

## Στόχοι Μάθησης

Μετά την ολοκλήρωση αυτού του μαθήματος, θα γνωρίζετε πώς να:

- Εντοπίζετε και να μετριάζετε κινδύνους κατά τη δημιουργία Agents Τεχνητής Νοημοσύνης.
- Εφαρμόζετε μέτρα ασφάλειας για να διασφαλίσετε ότι τα δεδομένα και η πρόσβαση διαχειρίζονται σωστά.
- Δημιουργείτε Agents Τεχνητής Νοημοσύνης που διατηρούν την ιδιωτικότητα των δεδομένων και προσφέρουν ποιοτική εμπειρία χρήστη.

## Ασφάλεια

Ας δούμε πρώτα πώς να χτίσουμε ασφαλείς εφαρμογές με agents. Ασφάλεια σημαίνει ότι ο agent ΤΝ λειτουργεί όπως έχει σχεδιαστεί. Ως κατασκευαστές εφαρμογών με agents, έχουμε μεθόδους και εργαλεία για τη μέγιστη ασφάλεια:

### Δημιουργία Πλαισίου Μηνυμάτων Συστήματος

Αν έχετε δημιουργήσει ποτέ εφαρμογή ΤΝ χρησιμοποιώντας Μεγάλα Μοντέλα Γλώσσας (LLMs), γνωρίζετε τη σημασία του σχεδιασμού ενός στιβαρού system prompt ή μηνύματος συστήματος. Αυτά τα prompts ορίζουν τους μετακανόνες, τις οδηγίες και κατευθυντήριες γραμμές για το πώς το LLM θα αλληλεπιδρά με τον χρήστη και τα δεδομένα.

Για τους Agents ΤΝ, το system prompt είναι ακόμη πιο σημαντικό καθώς οι agents θα χρειαστούν συγκεκριμένες οδηγίες για να ολοκληρώσουν τις εργασίες που έχουμε σχεδιάσει για αυτούς.

Για να δημιουργήσουμε κλιμακούμενα system prompts, μπορούμε να χρησιμοποιήσουμε ένα πλαίσιο μηνυμάτων συστήματος για να χτίσουμε έναν ή περισσότερους agents στην εφαρμογή μας:

![Building a System Message Framework](../../../translated_images/el/system-message-framework.3a97368c92d11d68.webp)

#### Βήμα 1: Δημιουργία ενός Μετα-Μηνύματος Συστήματος

Το meta prompt θα χρησιμοποιηθεί από ένα LLM για να παράγει τα system prompts για τους agents που δημιουργούμε. Το σχεδιάζουμε ως πρότυπο ώστε να μπορούμε αποτελεσματικά να δημιουργήσουμε πολλούς agents αν χρειαστεί.

Ορίστε ένα παράδειγμα μετα-μηνύματος συστήματος που θα δώσουμε στο LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Βήμα 2: Δημιουργία ενός βασικού prompt

Το επόμενο βήμα είναι να δημιουργήσετε ένα βασικό prompt για να περιγράψετε τον agent ΤΝ. Πρέπει να συμπεριλάβετε το ρόλο του agent, τις εργασίες που θα ολοκληρώσει και οποιεσδήποτε άλλες ευθύνες του agent.

Ορίστε ένα παράδειγμα:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Βήμα 3: Παροχή Βασικού Μηνύματος Συστήματος στο LLM

Τώρα μπορούμε να βελτιστοποιήσουμε αυτό το μήνυμα συστήματος παρέχοντας το μετα-μήνυμα συστήματος ως μήνυμα συστήματος καθώς και το βασικό μας μήνυμα συστήματος.

Αυτό θα παράγει ένα μήνυμα συστήματος που είναι καλύτερα σχεδιασμένο για να καθοδηγεί τους agents ΤΝ μας:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Βήμα 4: Επανάληψη και Βελτίωση

Η αξία αυτού του πλαισίου μηνυμάτων συστήματος είναι να μπορούμε να κλιμακώσουμε τη δημιουργία μηνυμάτων συστήματος από πολλούς agents πιο εύκολα καθώς και να βελτιώνουμε τα μηνύματά μας με το χρόνο. Είναι σπάνιο να έχετε ένα μήνυμα συστήματος που να λειτουργεί την πρώτη φορά για την πλήρη χρήση σας. Η δυνατότητα να κάνετε μικρές ρυθμίσεις και βελτιώσεις αλλάζοντας το βασικό μήνυμα συστήματος και να το εκτελείτε μέσα στο σύστημα θα σας επιτρέψει να συγκρίνετε και να αξιολογήσετε τα αποτελέσματα.

## Κατανόηση των Απειλών

Για να δημιουργήσετε αξιόπιστους agents ΤΝ, είναι σημαντικό να κατανοήσετε και να μετριάσετε τους κινδύνους και τις απειλές προς τον agent σας. Ας δούμε μόνο μερικές από τις διαφορετικές απειλές προς τους agents ΤΝ και πώς μπορείτε να σχεδιάσετε και να προετοιμαστείτε καλύτερα γι' αυτές.

![Understanding Threats](../../../translated_images/el/understanding-threats.89edeada8a97fc0f.webp)

### Εργασία και Οδηγίες

**Περιγραφή:** Επιτιθέμενοι προσπαθούν να αλλάξουν τις οδηγίες ή τους στόχους του agent ΤΝ μέσω prompting ή χειραγώγησης των εισροών.

**Μετριασμός**: Εκτελέστε ελέγχους επαλήθευσης και φίλτρα εισροών για να ανιχνεύσετε πιθανά επικίνδυνα prompts πριν αυτά επεξεργαστούν από τον agent ΤΝ. Καθώς αυτές οι επιθέσεις απαιτούν συχνή αλληλεπίδραση με τον agent, ο περιορισμός του αριθμού των γύρων σε μια συνομιλία αποτελεί έναν ακόμη τρόπο αποτροπής τέτοιων επιθέσεων.

### Πρόσβαση σε Κρίσιμα Συστήματα

**Περιγραφή:** Αν ένας agent ΤΝ έχει πρόσβαση σε συστήματα και υπηρεσίες που αποθηκεύουν ευαίσθητα δεδομένα, οι επιτιθέμενοι μπορούν να παραβιάσουν την επικοινωνία μεταξύ του agent και αυτών των υπηρεσιών. Οι επιθέσεις αυτές μπορεί να είναι άμεσες ή έμμεσες προσπάθειες για απόκτηση πληροφοριών σχετικά με αυτά τα συστήματα μέσω του agent.

**Μετριασμός:** Οι agents ΤΝ πρέπει να έχουν πρόσβαση σε συστήματα μόνο όταν είναι απολύτως απαραίτητο για να αποτραπούν τέτοιου είδους επιθέσεις. Η επικοινωνία μεταξύ agent και συστήματος πρέπει επίσης να είναι ασφαλής. Η εφαρμογή αυθεντικοποίησης και ελέγχου πρόσβασης είναι ένας ακόμα τρόπος προστασίας αυτών των πληροφοριών.

### Υπερφόρτωση Πόρων και Υπηρεσιών

**Περιγραφή:** Οι agents ΤΝ μπορούν να έχουν πρόσβαση σε διάφορα εργαλεία και υπηρεσίες για την ολοκλήρωση εργασιών. Οι επιτιθέμενοι μπορούν να εκμεταλλευτούν αυτή την ικανότητα στέλνοντας μεγάλο όγκο αιτημάτων μέσω του agent, προκαλώντας βλάβες συστήματος ή υψηλό κόστος.

**Μετριασμός:** Εφαρμόστε πολιτικές που περιορίζουν τον αριθμό των αιτημάτων που μπορεί να κάνει ένας agent ΤΝ σε μια υπηρεσία. Ο περιορισμός του αριθμού των γύρων συνομιλίας και των αιτημάτων προς τον agent είναι ένας άλλος τρόπος να αποτραπούν τέτοιου είδους επιθέσεις.

### Δηλητηρίαση Βάσης Γνώσεων

**Περιγραφή:** Αυτός ο τύπος επίθεσης δεν στοχεύει απευθείας τον agent ΤΝ, αλλά τη βάση γνώσης και άλλες υπηρεσίες που θα χρησιμοποιήσει ο agent. Αυτό μπορεί να περιλαμβάνει τη διαφθορά των δεδομένων ή πληροφοριών που χρησιμοποιεί ο agent για να ολοκληρώσει μια εργασία, οδηγώντας σε μεροληπτικές ή ανεπιθύμητες απαντήσεις προς τον χρήστη.

**Μετριασμός:** Εκτελέστε τακτικούς ελέγχους επαλήθευσης των δεδομένων που θα χρησιμοποιήσει ο agent ΤΝ στις διεργασίες του. Βεβαιωθείτε ότι η πρόσβαση σε αυτά τα δεδομένα είναι ασφαλής και τροποποιείται μόνο από αξιόπιστα άτομα για να αποφευχθεί αυτός ο τύπος επίθεσης.

### Αλυσιδωτά Σφάλματα

**Περιγραφή:** Οι agents ΤΝ προσπελαύνουν διάφορα εργαλεία και υπηρεσίες για να ολοκληρώσουν εργασίες. Σφάλματα που προκαλούνται από επιτιθέμενους μπορεί να οδηγήσουν σε αποτυχίες άλλων συστημάτων με τα οποία ο agent είναι συνδεδεμένος, κάνοντας την επίθεση πιο εκτεταμένη και δυσκολότερη στην αντιμετώπιση.

**Μετριασμός**: Μια μέθοδος αποφυγής είναι να λειτουργεί ο agent ΤΝ σε περιορισμένο περιβάλλον, όπως σε Docker container, για να αποτραπούν άμεσες επιθέσεις στο σύστημα. Η δημιουργία μηχανισμών επανόρθωσης και επαναδοκιμής όταν ορισμένα συστήματα ανταποκρίνονται με σφάλματα είναι ένας άλλος τρόπος αποτροπής μεγαλύτερων αποτυχιών στο σύστημα.

## Άνθρωπος στον Κύκλο

Ένας άλλος αποτελεσματικός τρόπος να δημιουργήσετε αξιόπιστα συστήματα Agents ΤΝ είναι η χρήση ανθρώπου στον κύκλο. Αυτό δημιουργεί μια ροή όπου οι χρήστες μπορούν να παρέχουν ανατροφοδότηση στους Agents κατά τη διάρκεια της εκτέλεσης. Οι χρήστες λειτουργούν ουσιαστικά ως agents σε ένα πολυ-agent σύστημα και παρέχουν έγκριση ή τερματισμό της διαδικασίας εκτέλεσης.

![Human in The Loop](../../../translated_images/el/human-in-the-loop.5f0068a678f62f4f.webp)

Εδώ είναι ένα απόσπασμα κώδικα που χρησιμοποιεί το AutoGen για να δείξει πώς υλοποιείται αυτή η έννοια:

```python

# Δημιουργήστε τους παράγοντες.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Χρησιμοποιήστε input() για να λάβετε είσοδο χρήστη από την κονσόλα.

# Δημιουργήστε την συνθήκη τερματισμού που θα σταματά τη συνομιλία όταν ο χρήστης πει "ΕΓΚΡΙΝΩ".
termination = TextMentionTermination("APPROVE")

# Δημιουργήστε την ομάδα.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Εκτελέστε τη συνομιλία και κάντε ροή στην κονσόλα.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Χρησιμοποιήστε asyncio.run(...) κατά την εκτέλεση σε σενάριο.
await Console(stream)

```

## Συμπέρασμα

Η δημιουργία αξιόπιστων agents ΤΝ απαιτεί προσεκτικό σχεδιασμό, στιβαρά μέτρα ασφαλείας και συνεχή βελτίωση. Με την υλοποίηση δομημένων συστημάτων μετα-προτροπής, την κατανόηση των πιθανών απειλών και την εφαρμογή στρατηγικών μετριασμού, οι προγραμματιστές μπορούν να δημιουργήσουν agents ΤΝ που είναι τόσο ασφαλείς όσο και αποτελεσματικοί. Επιπλέον, η ενσωμάτωση της προσέγγισης ανθρώπου στον κύκλο διασφαλίζει ότι οι agents παραμένουν ευθυγραμμισμένοι με τις ανάγκες των χρηστών ενώ ελαχιστοποιούνται οι κίνδυνοι. Καθώς η ΤΝ εξελίσσεται, η διατήρηση μιας προληπτικής στάσης σε θέματα ασφάλειας, ιδιωτικότητας και ηθικής θα είναι κλειδί για την καλλιέργεια εμπιστοσύνης και αξιοπιστίας σε συστήματα βασισμένα στην ΤΝ.

### Έχετε Περισσότερες Ερωτήσεις για τη Δημιουργία Αξιόπιστων Agents Τεχνητής Νοημοσύνης;

Εγγραφείτε στο [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) για να συναντήσετε άλλους μαθητές, να παρακολουθήσετε ώρες γραφείου και να λάβετε απαντήσεις στις ερωτήσεις σας σχετικά με τους Agents ΤΝ.

## Πρόσθετοι Πόροι

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Επισκόπηση Υπεύθυνης Τεχνητής Νοημοσύνης</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Αξιολόγηση γενετικών μοντέλων Τεχνητής Νοημοσύνης και εφαρμογών ΤΝ</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Ασφαλή μηνύματα συστήματος</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Πρότυπο Αξιολόγησης Κινδύνου</a>

## Προηγούμενο Μάθημα

[Agentic RAG](../05-agentic-rag/README.md)

## Επόμενο Μάθημα

[Σχέδιο Σχεδιασμού Προγράμματος](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Αποποίηση ευθυνών**:  
Αυτό το έγγραφο έχει μεταφραστεί χρησιμοποιώντας την υπηρεσία αυτόματης μετάφρασης [Co-op Translator](https://github.com/Azure/co-op-translator). Παρότι καταβάλλουμε προσπάθεια για ακρίβεια, παρακαλούμε λάβετε υπόψη ότι οι αυτοματοποιημένες μεταφράσεις ενδέχεται να περιέχουν λάθη ή ανακρίβειες. Το πρωτότυπο έγγραφο στη γλώσσα του θεωρείται η επίσημη πηγή. Για κρίσιμες πληροφορίες συνιστάται επαγγελματική ανθρώπινη μετάφραση. Δεν φέρουμε ευθύνη για τυχόν παρεξηγήσεις ή λανθασμένες ερμηνείες που προκύπτουν από τη χρήση αυτής της μετάφρασης.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->