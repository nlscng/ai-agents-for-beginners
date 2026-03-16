[![Εξερεύνηση Πλαισίων Πρακτόρων Τεχνητής Νοημοσύνης](../../../translated_images/el/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Κάντε κλικ στην εικόνα παραπάνω για να δείτε το βίντεο αυτού του μαθήματος)_

# Εξερευνήστε Πλαίσια Πρακτόρων Τεχνητής Νοημοσύνης

Τα πλαίσια πρακτόρων AI είναι πλατφόρμες λογισμικού σχεδιασμένες να απλοποιούν τη δημιουργία, την ανάπτυξη και τη διαχείριση πρακτόρων τεχνητής νοημοσύνης. Αυτά τα πλαίσια παρέχουν στους προγραμματιστές προκατασκευασμένα στοιχεία, αφαιρέσεις και εργαλεία που διευκολύνουν την ανάπτυξη σύνθετων συστημάτων AI.

Αυτά τα πλαίσια βοηθούν τους προγραμματιστές να επικεντρωθούν στις μοναδικές πτυχές των εφαρμογών τους παρέχοντας τυποποιημένες προσεγγίσεις σε κοινές προκλήσεις στην ανάπτυξη πρακτόρων AI. Ενισχύουν την κλιμάκωση, την προσβασιμότητα και την αποδοτικότητα στην κατασκευή συστημάτων AI.

## Εισαγωγή 

Αυτό το μάθημα θα καλύψει:

- Τι είναι τα Πλαίσια Πρακτόρων AI και τι επιτρέπουν στους προγραμματιστές να επιτύχουν;
- Πώς μπορούν οι ομάδες να τα χρησιμοποιήσουν για να πρωτοτυπήσουν γρήγορα, να επαναλάβουν και να βελτιώσουν τις δυνατότητες του πράκτορά τους;
- Ποιες είναι οι διαφορές ανάμεσα στα πλαίσια και τα εργαλεία που δημιουργήθηκαν από τη Microsoft <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>, και <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>;
- Μπορώ να ενσωματώσω απευθείας τα υπάρχοντα εργαλεία του οικοσυστήματος Azure μου, ή χρειάζομαι αυτόνομες λύσεις;
- Τι είναι η υπηρεσία Azure AI Agents και πώς με βοηθάει αυτό;

## Στόχοι μάθησης

Οι στόχοι αυτού του μαθήματος είναι να σας βοηθήσουν να κατανοήσετε:

- Το ρόλο των Πλαισίων Πρακτόρων AI στην ανάπτυξη AI.
- Πώς να αξιοποιήσετε τα Πλαίσια Πρακτόρων AI για να δημιουργήσετε έξυπνους πράκτορες.
- Κύριες δυνατότητες που ενεργοποιούνται από τα Πλαίσια Πρακτόρων AI.
- Τις διαφορές μεταξύ AutoGen, Semantic Kernel και Azure AI Agent Service.

## Τι είναι τα Πλαίσια Πρακτόρων AI και τι επιτρέπουν στους προγραμματιστές να κάνουν;

Τα παραδοσιακά Πλαίσια AI μπορούν να σας βοηθήσουν να ενσωματώσετε AI στις εφαρμογές σας και να τις βελτιώσετε με τους ακόλουθους τρόπους:

- **Προσωποποίηση**: Το AI μπορεί να αναλύει τη συμπεριφορά και τις προτιμήσεις των χρηστών για να παρέχει εξατομικευμένες προτάσεις, περιεχόμενο και εμπειρίες.
Παράδειγμα: Υπηρεσίες ροής όπως το Netflix χρησιμοποιούν AI για να προτείνουν ταινίες και σειρές με βάση το ιστορικό προβολών, ενισχύοντας την εμπλοκή και την ικανοποίηση των χρηστών.
- **Αυτοματοποίηση και Αποδοτικότητα**: Το AI μπορεί να αυτοματοποιεί επαναλαμβανόμενες εργασίες, να απλοποιεί ροές εργασίας και να βελτιώνει την επιχειρησιακή αποδοτικότητα.
Παράδειγμα: Εφαρμογές εξυπηρέτησης πελατών χρησιμοποιούν chatbot με δυνατότητες AI για να χειρίζονται συνήθεις ερωτήσεις, μειώνοντας τους χρόνους απόκρισης και απελευθερώνοντας ανθρώπινους πράκτορες για πιο πολύπλοκα ζητήματα.
- **Βελτιωμένη Εμπειρία Χρήστη**: Το AI μπορεί να βελτιώσει τη συνολική εμπειρία χρήστη παρέχοντας έξυπνες λειτουργίες όπως αναγνώριση φωνής, επεξεργασία φυσικής γλώσσας και προτεινόμενο κείμενο.
Παράδειγμα: Εικονικοί βοηθοί όπως η Siri και ο Google Assistant χρησιμοποιούν AI για να κατανοούν και να ανταποκρίνονται σε φωνητικές εντολές, διευκολύνοντας τους χρήστες να αλληλεπιδρούν με τις συσκευές τους.

### Αυτό ακούγεται υπέροχο, οπότε γιατί χρειαζόμαστε το Πλαίσιο Πρακτόρων AI;

Τα πλαίσια πρακτόρων AI αντιπροσωπεύουν κάτι περισσότερο από απλά πλαίσια AI. Είναι σχεδιασμένα να επιτρέπουν τη δημιουργία έξυπνων πρακτόρων που μπορούν να αλληλεπιδρούν με χρήστες, με άλλους πράκτορες και με το περιβάλλον για να πετύχουν συγκεκριμένους στόχους. Αυτοί οι πράκτορες μπορούν να εμφανίζουν αυτόνομη συμπεριφορά, να λαμβάνουν αποφάσεις και να προσαρμόζονται σε μεταβαλλόμενες συνθήκες. Ας δούμε μερικές βασικές δυνατότητες που ενεργοποιούνται από τα Πλαίσια Πρακτόρων AI:

- **Συνεργασία και Συντονισμός Πρακτόρων**: Επιτρέπουν τη δημιουργία πολλαπλών πρακτόρων AI που μπορούν να συνεργάζονται, να επικοινωνούν και να συντονίζονται για την επίλυση πολύπλοκων εργασιών.
- **Αυτοματοποίηση και Διαχείριση Εργασιών**: Παρέχουν μηχανισμούς για την αυτοματοποίηση ροών εργασίας πολλαπλών βημάτων, την ανάθεση εργασιών και τη δυναμική διαχείριση εργασιών μεταξύ πρακτόρων.
- **Περιεχόμενο Κατανόησης και Προσαρμογής**: Εφοδιάζουν τους πράκτορες με την ικανότητα να κατανοούν το πλαίσιο, να προσαρμόζονται σε μεταβαλλόμενα περιβάλλοντα και να λαμβάνουν αποφάσεις βάσει πληροφοριών σε πραγματικό χρόνο.

Συμπερασματικά, οι πράκτορες σας επιτρέπουν να κάνετε περισσότερα, να ανεβάσετε την αυτοματοποίηση σε επόμενο επίπεδο και να δημιουργήσετε πιο έξυπνα συστήματα που μπορούν να προσαρμόζονται και να μαθαίνουν από το περιβάλλον τους.

## Πώς να πρωτοτυπήσετε γρήγορα, να επαναλάβετε και να βελτιώσετε τις δυνατότητες του πράκτορα;

Αυτό είναι ένα τοπίο που εξελίσσεται γρήγορα, αλλά υπάρχουν ορισμένα πράγματα που είναι κοινά στα περισσότερα Πλαίσια Πρακτόρων AI και που μπορούν να σας βοηθήσουν να πρωτοτυπήσετε και να επαναλάβετε γρήγορα, δηλαδή μονάδες στοιχείων, εργαλεία συνεργασίας και μάθηση σε πραγματικό χρόνο. Ας εμβαθύνουμε σε αυτά:

- **Χρησιμοποιήστε Μονωμενικά Στοιχεία**: Τα SDK AI προσφέρουν προκατασκευασμένα στοιχεία όπως συνδέσεις AI και μνήμης, κλήσεις συναρτήσεων χρησιμοποιώντας φυσική γλώσσα ή πρόσθετα κώδικα, πρότυπα prompt και άλλα.
- **Αξιοποιήστε Εργαλεία Συνεργασίας**: Σχεδιάστε πράκτορες με συγκεκριμένους ρόλους και εργασίες, επιτρέποντάς τους να δοκιμάζουν και να βελτιώνουν συνεργατικές ροές εργασίας.
- **Μάθετε σε Πραγματικό Χρόνο**: Υλοποιήστε βρόχους ανατροφοδότησης όπου οι πράκτορες μαθαίνουν από τις αλληλεπιδράσεις και προσαρμόζουν τη συμπεριφορά τους δυναμικά.

### Χρησιμοποιήστε Μονωμενικά Στοιχεία

SDK όπως το Microsoft Semantic Kernel και το LangChain προσφέρουν προκατασκευασμένα στοιχεία όπως συνδέσεις AI, πρότυπα prompt και διαχείριση μνήμης.

**Πώς μπορούν οι ομάδες να τα χρησιμοποιήσουν**: Οι ομάδες μπορούν να συναρμολογήσουν γρήγορα αυτά τα στοιχεία για να δημιουργήσουν ένα λειτουργικό πρωτότυπο χωρίς να ξεκινήσουν από το μηδέν, επιτρέποντας γρήγορη πειραματική διαδικασία και επαναλήψεις.

**Πώς λειτουργεί στην πράξη**: Μπορείτε να χρησιμοποιήσετε έναν προκατασκευασμένο αναλυτή για να εξάγετε πληροφορίες από την είσοδο του χρήστη, ένα module μνήμης για να αποθηκεύετε και να ανακτάτε δεδομένα, και έναν γεννήτρια prompt για να αλληλεπιδράτε με τους χρήστες, όλα χωρίς να χρειάζεται να κατασκευάσετε αυτά τα στοιχεία από το μηδέν.

**Παράδειγμα κώδικα**. Ας δούμε παραδείγματα του πώς μπορείτε να χρησιμοποιήσετε έναν προκατασκευασμένο AI Connector με το Semantic Kernel σε Python και .Net που χρησιμοποιεί αυτόματη κλήση συναρτήσεων ώστε το μοντέλο να απαντά στην είσοδο του χρήστη:

``` python
# Παράδειγμα Semantic Kernel σε Python

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Ορισμός ενός αντικειμένου ChatHistory για την αποθήκευση του πλαισίου της συνομιλίας
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Ορισμός ενός δείγματος plugin που περιέχει τη συνάρτηση για κράτηση ταξιδιού
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Δημιουργία του Kernel
kernel = Kernel()

# Προσθήκη του δείγματος plugin στο αντικείμενο Kernel
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Ορισμός του AI Connector της Azure OpenAI
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Ορισμός των ρυθμίσεων του αιτήματος για διαμόρφωση του μοντέλου με αυτόματη κλήση λειτουργιών
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Αποστολή του αιτήματος στο μοντέλο για το δοσμένο ιστορικό συνομιλίας και τις ρυθμίσεις αιτήματος
    # Το Kernel περιέχει το δείγμα που το μοντέλο θα ζητήσει να εκτελέσει
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
    # Παράδειγμα απάντησης μοντέλου AI: `Η πτήση σας για τη Νέα Υόρκη στις 1 Ιανουαρίου 2025 έχει κρατηθεί με επιτυχία. Καλά ταξίδια! ✈️🗽`

    # Προσθήκη της απάντησης του μοντέλου στο πλαίσιο ιστορικού συνομιλίας μας
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

Αυτό που μπορείτε να δείτε από αυτό το παράδειγμα είναι πώς μπορείτε να αξιοποιήσετε έναν προκατασκευασμένο αναλυτή για να εξάγετε βασικές πληροφορίες από την είσοδο του χρήστη, όπως η προέλευση, ο προορισμός και η ημερομηνία ενός αιτήματος κράτησης πτήσης. Αυτή η μονωμενική προσέγγιση σας επιτρέπει να επικεντρωθείτε στη λογική υψηλού επιπέδου.

### Αξιοποιήστε Εργαλεία Συνεργασίας

Πλαίσια όπως το CrewAI, το Microsoft AutoGen και το Semantic Kernel διευκολύνουν τη δημιουργία πολλαπλών πρακτόρων που μπορούν να συνεργαστούν.

**Πώς μπορούν οι ομάδες να τα χρησιμοποιήσουν**: Οι ομάδες μπορούν να σχεδιάσουν πράκτορες με συγκεκριμένους ρόλους και εργασίες, επιτρέποντάς τους να δοκιμάζουν και να βελτιώνουν συνεργατικές ροές εργασίας και να βελτιώνουν τη συνολική αποδοτικότητα του συστήματος.

**Πώς λειτουργεί στην πράξη**: Μπορείτε να δημιουργήσετε μια ομάδα πρακτόρων όπου κάθε πράκτορας έχει μια εξειδικευμένη λειτουργία, όπως ανάκτηση δεδομένων, ανάλυση ή λήψη αποφάσεων. Αυτοί οι πράκτορες μπορούν να επικοινωνούν και να μοιράζονται πληροφορίες για να επιτύχουν έναν κοινό στόχο, όπως να απαντήσουν σε ένα ερώτημα χρήστη ή να ολοκληρώσουν μια εργασία.

**Παράδειγμα κώδικα (AutoGen)**:

```python
# δημιουργώντας πράκτορες, στη συνέχεια δημιουργήστε ένα χρονοδιάγραμμα ροτέισον όπου μπορούν να συνεργαστούν, σε αυτήν την περίπτωση με σειρά

# Πράκτορας Ανάκτησης Δεδομένων
# Πράκτορας Ανάλυσης Δεδομένων
# Πράκτορας Λήψης Αποφάσεων

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

# η συνομιλία τελειώνει όταν ο χρήστης πει "ΕΓΚΡΙΝΩ"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Χρησιμοποιήστε asyncio.run(...) κατά την εκτέλεση σε ένα σενάριο.
await Console(stream)
```

Αυτό που βλέπετε στον προηγούμενο κώδικα είναι πώς μπορείτε να δημιουργήσετε μια εργασία που περιλαμβάνει πολλαπλούς πράκτορες που συνεργάζονται για να αναλύσουν δεδομένα. Κάθε πράκτορας εκτελεί μια συγκεκριμένη λειτουργία, και η εργασία εκτελείται με το συντονισμό των πρακτόρων για να επιτευχθεί το επιθυμητό αποτέλεσμα. Δημιουργώντας αφιερωμένους πράκτορες με εξειδικευμένους ρόλους, μπορείτε να βελτιώσετε την αποδοτικότητα και την απόδοση των εργασιών.

### Μάθετε σε Πραγματικό Χρόνο

Προηγμένα πλαίσια παρέχουν δυνατότητες για κατανόηση του πλαισίου και προσαρμογή σε πραγματικό χρόνο.

**Πώς μπορούν οι ομάδες να τα χρησιμοποιήσουν**: Οι ομάδες μπορούν να εφαρμόσουν βρόχους ανατροφοδότησης όπου οι πράκτορες μαθαίνουν από τις αλληλεπιδράσεις και προσαρμόζουν τη συμπεριφορά τους δυναμικά, οδηγώντας σε συνεχή βελτίωση και τελειοποίηση των δυνατοτήτων.

**Πώς λειτουργεί στην πράξη**: Οι πράκτορες μπορούν να αναλύουν την ανατροφοδότηση των χρηστών, δεδομένα περιβάλλοντος και αποτελέσματα εργασιών για να ενημερώνουν τη βάση γνώσεων τους, να προσαρμόζουν αλγορίθμους λήψης αποφάσεων και να βελτιώνουν την απόδοση με την πάροδο του χρόνου. Αυτή η επαναληπτική διαδικασία μάθησης επιτρέπει στους πράκτορες να προσαρμόζονται σε μεταβαλλόμενες συνθήκες και προτιμήσεις χρηστών, ενισχύοντας τη συνολική αποτελεσματικότητα του συστήματος.

## Ποιες είναι οι διαφορές μεταξύ των πλαισίων AutoGen, Semantic Kernel και Azure AI Agent Service;

Υπάρχουν πολλοί τρόποι να συγκρίνουμε αυτά τα πλαίσια, αλλά ας δούμε μερικές βασικές διαφορές όσον αφορά το σχεδιασμό, τις δυνατότητες και τις στοχευμένες περιπτώσεις χρήσης:

## AutoGen

Το AutoGen είναι ένα ανοιχτού κώδικα πλαίσιο που αναπτύχθηκε από το AI Frontiers Lab της Microsoft Research. Επικεντρώνεται σε εφαρμογές «agentic» που βασίζονται σε γεγονότα και κατανεμημένες δομές, επιτρέποντας πολλαπλά LLMs και SLMs, εργαλεία και προχωρημένα μοτίβα σχεδίασης πολλαπλών πρακτόρων.

Το AutoGen είναι δομημένο γύρω από την κεντρική έννοια των πρακτόρων, οι οποίοι είναι αυτόνομες οντότητες που μπορούν να αντιλαμβάνονται το περιβάλλον τους, να λαμβάνουν αποφάσεις και να αναλαμβάνουν ενέργειες για να πετύχουν συγκεκριμένους στόχους. Οι πράκτορες επικοινωνούν μέσω ασύγχρονων μηνυμάτων, επιτρέποντάς τους να λειτουργούν ανεξάρτητα και παράλληλα, ενισχύοντας την κλιμάκωση και την ανταπόκριση του συστήματος.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Οι πράκτορες βασίζονται στο μοντέλο ηθοποιού</a>. Σύμφωνα με τη Wikipedia, ένας ηθοποιός είναι _η βασική δομική μονάδα του ταυτόχρονου υπολογισμού. Σε απάντηση σε ένα μήνυμα που λαμβάνει, ένας ηθοποιός μπορεί: να παίρνει τοπικές αποφάσεις, να δημιουργεί περισσότερους ηθοποιούς, να στέλνει περισσότερα μηνύματα, και να καθορίζει πώς θα ανταποκριθεί στο επόμενο μήνυμα που θα λάβει_.

**Περιπτώσεις Χρήσης**: Αυτοματοποίηση δημιουργίας κώδικα, εργασίες ανάλυσης δεδομένων και δημιουργία προσαρμοσμένων πρακτόρων για λειτουργίες σχεδιασμού και έρευνας.

Εδώ είναι μερικές σημαντικές βασικές έννοιες του AutoGen:

- **Πράκτορες**. Ένας πράκτορας είναι μια οντότητα λογισμικού που:
  - **Επικοινωνεί μέσω μηνυμάτων**, αυτά τα μηνύματα μπορούν να είναι σύγχρονα ή ασύγχρονα.
  - **Διατηρεί τη δική του κατάσταση**, η οποία μπορεί να τροποποιηθεί από εισερχόμενα μηνύματα.
  - **Εκτελεί ενέργειες** ως απάντηση σε ληφθέντα μηνύματα ή αλλαγές στην κατάστασή του. Αυτές οι ενέργειες μπορεί να τροποποιήσουν την κατάσταση του πράκτορα και να παράγουν εξωτερικά αποτελέσματα, όπως ενημέρωση αρχείων καταγραφής μηνυμάτων, αποστολή νέων μηνυμάτων, εκτέλεση κώδικα ή κλήσεις API.
    
  Εδώ έχετε ένα σύντομο απόσπασμα κώδικα στο οποίο δημιουργείτε τον δικό σας πράκτορα με δυνατότητες Συνομιλίας:

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
    
    Στον προηγούμενο κώδικα, `MyAgent` έχει δημιουργηθεί και κληρονομεί από `RoutedAgent`. Έχει έναν χειριστή μηνυμάτων που εκτυπώνει το περιεχόμενο του μηνύματος και στη συνέχεια στέλνει μια απάντηση χρησιμοποιώντας τον `AssistantAgent` αντιπρόσωπο. Σημειώστε ιδιαίτερα πώς αναθέτουμε σε `self._delegate` ένα στιγμιότυπο του `AssistantAgent` που είναι ένας προκατασκευασμένος πράκτορας ο οποίος μπορεί να χειριστεί συμπληρώσεις συνομιλίας.


    Ας ενημερώσουμε το AutoGen για αυτόν τον τύπο πράκτορα και ας ξεκινήσουμε το πρόγραμμα στη συνέχεια:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Ξεκινήστε την επεξεργασία μηνυμάτων στο παρασκήνιο.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Στον προηγούμενο κώδικα οι πράκτορες καταχωρούνται στο runtime και στη συνέχεια αποστέλλεται ένα μήνυμα στον πράκτορα με αποτέλεσμα την ακόλουθη έξοδο:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Πολλαπλοί πράκτορες**. Το AutoGen υποστηρίζει τη δημιουργία πολλαπλών πρακτόρων που μπορούν να συνεργαστούν για να επιτύχουν πολύπλοκες εργασίες. Οι πράκτορες μπορούν να επικοινωνούν, να μοιράζονται πληροφορίες και να συντονίζουν τις ενέργειές τους για να επιλύουν προβλήματα πιο αποτελεσματικά. Για να δημιουργήσετε ένα σύστημα πολλαπλών πρακτόρων, μπορείτε να ορίσετε διαφορετικά είδη πρακτόρων με εξειδικευμένες λειτουργίες και ρόλους, όπως ανάκτηση δεδομένων, ανάλυση, λήψη αποφάσεων και αλληλεπίδραση με τους χρήστες. Ας δούμε πώς μοιάζει μια τέτοια δημιουργία για να αποκτήσουμε μια αίσθηση:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Παράδειγμα δήλωσης ενός Πράκτορα
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Χρήση τύπου θέματος ως τύπου πράκτορα.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # υπολοίπες δηλώσεις συντομευμένες για συντομία

    # Ομαδική συνομιλία
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

    Στον προηγούμενο κώδικα έχουμε έναν `GroupChatManager` που είναι καταχωρημένος στο runtime. Αυτός ο διαχειριστής είναι υπεύθυνος για το συντονισμό των αλληλεπιδράσεων μεταξύ διαφορετικών τύπων πρακτόρων, όπως συγγραφείς, εικονογράφοι, επιμελητές και χρήστες.

- **Runtime Πρακτόρων**. Το πλαίσιο παρέχει ένα περιβάλλον runtime, επιτρέποντας την επικοινωνία μεταξύ πρακτόρων, διαχειρίζεται τις ταυτότητες και τον κύκλο ζωής τους, και επιβάλλει ορίων ασφάλειας και ιδιωτικότητας. Αυτό σημαίνει ότι μπορείτε να εκτελείτε τους πράκτορές σας σε ένα ασφαλές και ελεγχόμενο περιβάλλον, εξασφαλίζοντας ότι μπορούν να αλληλεπιδρούν με ασφάλεια και αποτελεσματικότητα. Υπάρχουν δύο runtimes ενδιαφέροντος:
  - **Stand-alone runtime**. Αυτή είναι μια καλή επιλογή για εφαρμογές μονοπρόσθεσης όπου όλοι οι πράκτορες υλοποιούνται στην ίδια γλώσσα προγραμματισμού και εκτελούνται στην ίδια διεργασία. Ακολουθεί μια απεικόνιση του πώς λειτουργεί:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Λειτουργία ανεξάρτητου χρόνου εκτέλεσης</a>   
Στοίβα εφαρμογής

    *οι πράκτορες επικοινωνούν μέσω μηνυμάτων μέσω του runtime, και το runtime διαχειρίζεται τον κύκλο ζωής των πρακτόρων*

  - **Distributed agent runtime**, είναι κατάλληλο για εφαρμογές πολλαπλών διεργασιών όπου οι πράκτορες μπορεί να υλοποιούνται σε διαφορετικές γλώσσες προγραμματισμού και να εκτελούνται σε διαφορετικές μηχανές. Ακολουθεί μια απεικόνιση του πώς λειτουργεί:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Διανεμημένο runtime</a>

## Semantic Kernel + Agent Framework

Το Semantic Kernel είναι ένα SDK Orchestration AI έτοιμο για επιχειρήσεις. Αποτελείται από συνδέσεις AI και μνήμης, μαζί με ένα Πλαίσιο Πρακτόρων.

Ας καλύψουμε πρώτα μερικά βασικά στοιχεία:

- **Συνδέσεις AI**: Αυτή είναι μια διεπαφή με εξωτερικές υπηρεσίες AI και πηγές δεδομένων για χρήση τόσο σε Python όσο και σε C#.

  ```python
  # Σημασιολογικός Πυρήνας Python
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

    Εδώ έχετε ένα απλό παράδειγμα του πώς μπορείτε να δημιουργήσετε έναν kernel και να προσθέσετε μια υπηρεσία συμπλήρωσης συνομιλίας. Το Semantic Kernel δημιουργεί μια σύνδεση με μια εξωτερική υπηρεσία AI, σε αυτή την περίπτωση, το Azure OpenAI Chat Completion.

- **Πρόσθετα (Plugins)**: Αυτά ενσωματώνουν λειτουργίες που μια εφαρμογή μπορεί να χρησιμοποιήσει. Υπάρχουν τόσο έτοιμα πρόσθετα όσο και προσαρμοσμένα που μπορείτε να δημιουργήσετε. Μια σχετική έννοια είναι οι "συναρτήσεις prompt." Αντί να παρέχετε φυσικές ενδείξεις για την κλήση μιας συνάρτησης, εκπέμπετε ορισμένες συναρτήσεις στο μοντέλο. Βάσει του τρέχοντος πλαισίου συνομιλίας, το μοντέλο μπορεί να επιλέξει να καλέσει μία από αυτές τις συναρτήσεις για να ολοκληρώσει ένα αίτημα ή ένα ερώτημα. Ακολουθεί ένα παράδειγμα:

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

    Εδώ, έχετε πρώτα ένα πρότυπο prompt `skPrompt` που αφήνει χώρο για τον χρήστη να εισάγει κείμενο, `$userInput`. Στη συνέχεια δημιουργείτε τη συνάρτηση kernel `SummarizeText` και στη συνέχεια την εισάγετε στον kernel με το όνομα πρόσθετου `SemanticFunctions`. Σημειώστε το όνομα της συνάρτησης που βοηθά το Semantic Kernel να καταλάβει τι κάνει η συνάρτηση και πότε θα πρέπει να κληθεί.

- **Νηπιακή συνάρτηση (Native function)**: Υπάρχουν επίσης native συναρτήσεις που το πλαίσιο μπορεί να καλέσει απευθείας για να εκτελέσει την εργασία. Ακολουθεί ένα παράδειγμα μιας τέτοιας συνάρτησης που ανακτά το περιεχόμενο από ένα αρχείο:

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

- **Μνήμη**:  Αφαιρεί και απλοποιεί τη διαχείριση του πλαισίου για εφαρμογές AI. Η ιδέα με τη μνήμη είναι ότι αυτό είναι κάτι που το LLM θα πρέπει να γνωρίζει. Μπορείτε να αποθηκεύσετε αυτές τις πληροφορίες σε ένα vector store που καταλήγει να είναι μια in-memory βάση δεδομένων ή μια βάσης δεδομένων διανυσμάτων ή κάτι παρόμοιο. Ακολουθεί ένα παράδειγμα ενός πολύ απλοποιημένου σεναρίου όπου προστίθενται *γεγονότα* στη μνήμη:

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

    Αυτά τα στοιχεία στη συνέχεια αποθηκεύονται στη συλλογή μνήμης `SummarizedAzureDocs`. Αυτό είναι ένα πολύ απλοποιημένο παράδειγμα, αλλά μπορείτε να δείτε πώς μπορείτε να αποθηκεύσετε πληροφορίες στη μνήμη για να τις χρησιμοποιήσει το LLM.

So that's the basics of the Semantic Kernel framework, what about the Agent Framework?

## Azure AI Agent Service

Το Azure AI Agent Service είναι μια πιο πρόσφατη προσθήκη, που παρουσιάστηκε στο Microsoft Ignite 2024. Επιτρέπει την ανάπτυξη και τη διάθεση πρακτόρων AI με πιο ευέλικτα μοντέλα, όπως η άμεση κλήση ανοιχτού κώδικα LLMs όπως Llama 3, Mistral και Cohere.

Η υπηρεσία Azure AI Agent Service παρέχει ισχυρότερους μηχανισμούς ασφάλειας για επιχειρήσεις και μεθόδους αποθήκευσης δεδομένων, καθιστώντας την κατάλληλη για επιχειρηματικές εφαρμογές. 

Λειτουργεί άμεσα με πλαίσια ορχήστρωσης πολλαπλών πρακτόρων όπως το AutoGen και το Semantic Kernel.

Αυτή η υπηρεσία βρίσκεται επί του παρόντος σε Public Preview και υποστηρίζει Python και C# για την κατασκευή πρακτόρων.

Using Semantic Kernel Python, we can create an Azure AI Agent with a user-defined plugin:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Ορίστε ένα δείγμα προσθέτου για το δείγμα
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
        # Δημιουργήστε ορισμό πράκτορα
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Δημιουργήστε τον πράκτορα AzureAI χρησιμοποιώντας τον ορισμένο πελάτη και τον ορισμό πράκτορα
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Δημιουργήστε ένα νήμα για να κρατήσει τη συνομιλία
        # Εάν δεν παρέχεται νήμα, θα δημιουργηθεί
        # νέο νήμα και θα επιστραφεί με την αρχική απάντηση
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
                # Καλείστε τον πράκτορα για το καθορισμένο νήμα
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

### Βασικές έννοιες

Η υπηρεσία Azure AI Agent Service έχει τις ακόλουθες βασικές έννοιες:

- **Πράκτορας (Agent)**. Η υπηρεσία Azure AI Agent Service ενσωματώνεται με το Microsoft Foundry. Στο AI Foundry, ένας AI πράκτορας λειτουργεί ως "έξυπνη" μικροϋπηρεσία που μπορεί να χρησιμοποιηθεί για να απαντά σε ερωτήσεις (RAG), να εκτελεί ενέργειες ή να αυτοματοποιεί πλήρως ροές εργασίας. Το πετυχαίνει συνδυάζοντας τη δύναμη των γενετικών μοντέλων AI με εργαλεία που του επιτρέπουν να έχει πρόσβαση και να αλληλεπιδρά με πραγματικές πηγές δεδομένων. Ακολουθεί ένα παράδειγμα πράκτορα:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Σε αυτό το παράδειγμα, δημιουργείται ένας πράκτορας με το μοντέλο `gpt-4o-mini`, το όνομα `my-agent` και τις οδηγίες `You are helpful agent`. Ο πράκτορας εξοπλίζεται με εργαλεία και πόρους για να εκτελεί εργασίες ερμηνείας κώδικα.

- **Θέμα (Thread) και μηνύματα**. Το thread είναι μια άλλη σημαντική έννοια. Αντιπροσωπεύει μια συνομιλία ή αλληλεπίδραση μεταξύ ενός πράκτορα και ενός χρήστη. Τα threads μπορούν να χρησιμοποιηθούν για να παρακολουθούν την πρόοδο μιας συνομιλίας, να αποθηκεύουν πληροφορίες συμφραζομένων και να διαχειρίζονται την κατάσταση της αλληλεπίδρασης. Ακολουθεί ένα παράδειγμα thread:

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

    Σε αυτόν τον κώδικα δημιουργείται ένα thread. Στη συνέχεια, ένα μήνυμα αποστέλλεται στο thread. Καλώντας `create_and_process_run`, ζητείται από τον πράκτορα να εκτελέσει εργασία στο thread. Τέλος, τα μηνύματα ανακτώνται και καταγράφονται για να δούμε την απάντηση του πράκτορα. Τα μηνύματα δείχνουν την πρόοδο της συνομιλίας μεταξύ του χρήστη και του πράκτορα. Είναι επίσης σημαντικό να κατανοήσουμε ότι τα μηνύματα μπορούν να είναι διαφορετικών τύπων, όπως κείμενο, εικόνα ή αρχείο — δηλαδή η εργασία του πράκτορα μπορεί να έχει ως αποτέλεσμα, για παράδειγμα, μια εικόνα ή μια κειμενική απάντηση. Ως προγραμματιστής, μπορείτε στη συνέχεια να χρησιμοποιήσετε αυτές τις πληροφορίες για να επεξεργαστείτε περαιτέρω την απάντηση ή να την παρουσιάσετε στον χρήστη.

- **Ενσωμάτωση με άλλα πλαίσια AI**. Η υπηρεσία Azure AI Agent Service μπορεί να αλληλεπιδρά με άλλα πλαίσια όπως το AutoGen και το Semantic Kernel, το οποίο σημαίνει ότι μπορείτε να κατασκευάσετε μέρος της εφαρμογής σας σε ένα από αυτά τα πλαίσια και, για παράδειγμα, να χρησιμοποιήσετε την υπηρεσία Agent ως ορχηστρωτή ή να δημιουργήσετε τα πάντα στην υπηρεσία Agent.

**Περιπτώσεις χρήσης**: Η υπηρεσία Azure AI Agent Service έχει σχεδιαστεί για επιχειρηματικές εφαρμογές που απαιτούν ασφαλή, κλιμακούμενη και ευέλικτη ανάπτυξη πρακτόρων AI.

## Ποια είναι η διαφορά μεταξύ αυτών των πλαισίων?
 
Φαίνεται ότι υπάρχει μεγάλη επικάλυψη μεταξύ αυτών των πλαισίων, αλλά υπάρχουν μερικές βασικές διαφορές όσον αφορά τον σχεδιασμό, τις δυνατότητες και τις στοχευμένες περιπτώσεις χρήσης:
 
- **AutoGen**: Είναι ένα πλαίσιο πειραματισμού επικεντρωμένο στην αιχμή της έρευνας για συστήματα πολλαπλών πρακτόρων. Είναι το καλύτερο μέρος για να πειραματιστείτε και να κατασκευάσετε πρωτότυπα σύνθετων συστημάτων πολλαπλών πρακτόρων.
- **Semantic Kernel**: Είναι μια έτοιμη για παραγωγή βιβλιοθήκη πρακτόρων για την κατασκευή επιχειρηματικών εφαρμογών με πρακτορική λογική. Εστιάζει σε εφαρμογές πρακτόρων που ενεργοποιούνται από γεγονότα και είναι κατανεμημένες, επιτρέποντας πολλαπλά LLMs και SLMs, εργαλεία, και μοτίβα σχεδίασης ενός ή πολλαπλών πρακτόρων.
- **Azure AI Agent Service**: Είναι μια πλατφόρμα και υπηρεσία διάθεσης στο Azure Foundry για πράκτορες. Προσφέρει σύνδεση με υπηρεσίες που υποστηρίζονται από το Azure Foundry όπως το Azure OpenAI, το Azure AI Search, το Bing Search και την εκτέλεση κώδικα.
 
Ακόμα δεν είστε σίγουροι ποιο να επιλέξετε;

### Περιπτώσεις χρήσης
 
Ας δούμε αν μπορούμε να σας βοηθήσουμε περνώντας από μερικές κοινές περιπτώσεις χρήσης:
 
> Q: Πειραματίζομαι, μαθαίνω και κατασκευάζω proof-of-concept εφαρμογές πρακτόρων, και θέλω να μπορώ να χτίζω και να πειραματίζομαι γρήγορα
>

>A: Το AutoGen θα ήταν μια καλή επιλογή για αυτό το σενάριο, καθώς επικεντρώνεται σε εφαρμογές πρακτόρων που ενεργοποιούνται από γεγονότα (event-driven), είναι κατανεμημένες και υποστηρίζει προηγμένα μοτίβα σχεδίασης πολλαπλών πρακτόρων.

> Q: Τι κάνει το AutoGen καλύτερη επιλογή από το Semantic Kernel και το Azure AI Agent Service για αυτήν την περίπτωση χρήσης;
>
> A: Το AutoGen έχει σχεδιαστεί ειδικά για εφαρμογές πρακτόρων που ενεργοποιούνται από γεγονότα και είναι κατανεμημένες, καθιστώντας το κατάλληλο για αυτοματοποίηση δημιουργίας κώδικα και εργασίες ανάλυσης δεδομένων. Παρέχει τα απαραίτητα εργαλεία και δυνατότητες για να κατασκευάσετε σύνθετα συστήματα πολλαπλών πρακτόρων αποτελεσματικά.

>Q: Ακούγεται σαν ότι η υπηρεσία Azure AI Agent Service θα μπορούσε επίσης να λειτουργήσει εδώ, έχει εργαλεία για δημιουργία κώδικα και άλλα;
>
> A: Ναι, η υπηρεσία Azure AI Agent Service είναι μια πλατφόρμα για πράκτορες και προσθέτει ενσωματωμένες δυνατότητες για πολλαπλά μοντέλα, Azure AI Search, Bing Search και Azure Functions. Διευκολύνει το χτίσιμο των πρακτόρων σας στο Foundry Portal και τη διάθεσή τους σε μεγάλη κλίμακα.
 
> Q: Είμαι ακόμα μπερδεμένος, δώστε μου απλώς μια επιλογή
>
> A: Μια εξαιρετική επιλογή είναι να χτίσετε πρώτα την εφαρμογή σας στο Semantic Kernel και στη συνέχεια να χρησιμοποιήσετε την υπηρεσία Azure AI Agent Service για να διαθέσετε τον πράκτορα. Αυτή η προσέγγιση σας επιτρέπει να διατηρείτε εύκολα τους πράκτορές σας ενώ αξιοποιείτε τη δύναμη για να χτίσετε συστήματα πολλαπλών πρακτόρων στο Semantic Kernel. Επιπλέον, το Semantic Kernel έχει ένα connector στο AutoGen, καθιστώντας εύκολη τη χρήση και των δύο πλαισίων μαζί.
 
Ας συνοψίσουμε τις βασικές διαφορές σε ένα πίνακα:

| Framework | Focus | Core Concepts | Use Cases |
| --- | --- | --- | --- |
| AutoGen | Εφαρμογές πρακτόρων ενεργοποιούμενες από γεγονότα, κατανεμημένες | Πράκτορες, Προσωπικότητες, Συναρτήσεις, Δεδομένα | Δημιουργία κώδικα, εργασίες ανάλυσης δεδομένων |
| Semantic Kernel | Κατανόηση και δημιουργία κειμένου που μοιάζει με ανθρώπινο | Πράκτορες, Μονάδες, Συνεργασία | Κατανόηση φυσικής γλώσσας, δημιουργία περιεχομένου |
| Azure AI Agent Service | Ευέλικτα μοντέλα, ασφάλεια για επιχειρήσεις, δημιουργία κώδικα, κλήση εργαλείων | Αρθρωτότητα, Συνεργασία, Ορχήστρωση διαδικασιών | Ασφαλής, κλιμακούμενη και ευέλικτη διάθεση πρακτόρων AI |

What's the ideal use case for each of these frameworks?

## Μπορώ να ενσωματώσω απευθείας τα υπάρχοντα εργαλεία του οικοσυστήματος Azure, ή χρειάζομαι ανεξάρτητες λύσεις?

Η απάντηση είναι ναι, μπορείτε να ενσωματώσετε απευθείας τα υπάρχοντα εργαλεία του οικοσυστήματος Azure ειδικά με την υπηρεσία Azure AI Agent Service, επειδή έχει σχεδιαστεί για να λειτουργεί απρόσκοπτα με άλλες υπηρεσίες Azure. Μπορείτε, για παράδειγμα, να ενσωματώσετε το Bing, το Azure AI Search και τις Azure Functions. Υπάρχει επίσης βαθιά ενσωμάτωση με το Microsoft Foundry.

Για το AutoGen και το Semantic Kernel, μπορείτε επίσης να ενσωματώσετε υπηρεσίες Azure, αλλά μπορεί να απαιτείται να κάνετε κλήσεις στις υπηρεσίες Azure από τον κώδικά σας. Ένας άλλος τρόπος να ενσωματωθείτε είναι να χρησιμοποιήσετε τα Azure SDKs για να αλληλεπιδράσετε με τις υπηρεσίες Azure από τους πράκτορές σας. Επιπλέον, όπως αναφέρθηκε, μπορείτε να χρησιμοποιήσετε την υπηρεσία Azure AI Agent Service ως ορχηστρωτή για τους πράκτορές σας που έχουν δημιουργηθεί στο AutoGen ή στο Semantic Kernel, κάτι που θα έδινε εύκολη πρόσβαση στο οικοσύστημα Azure.

## Παραδείγματα Κώδικα

- Python: [Πλαίσιο πρακτόρων](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Πλαίσιο πρακτόρων](./code_samples/02-dotnet-agent-framework.md)

## Έχετε κι άλλες ερωτήσεις σχετικά με τα πλαίσια πρακτόρων AI;

Συνδεθείτε στο [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) για να συναντήσετε άλλους εκπαιδευόμενους, να παρακολουθήσετε ώρες υποστήριξης και να λάβετε απαντήσεις στις ερωτήσεις σας για τους AI πράκτορες.

## Αναφορές

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Υπηρεσία Azure Agent</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel και AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Πλαίσιο Πρακτόρων Semantic Kernel για Python</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Πλαίσιο Πρακτόρων Semantic Kernel για .Net</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Υπηρεσία Azure AI Agent</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Χρήση της υπηρεσίας Azure AI Agent με AutoGen / Semantic Kernel για την κατασκευή λύσης πολλαπλών πρακτόρων</a>

## Προηγούμενο Μάθημα

[Εισαγωγή στους AI Πράκτορες και Περιπτώσεις Χρήσης](../01-intro-to-ai-agents/README.md)

## Επόμενο Μάθημα

[Κατανόηση των Σχεδιαστικών Μοτίβων Πρακτόρων](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Αποποίηση ευθυνών:
Αυτό το έγγραφο έχει μεταφραστεί χρησιμοποιώντας την υπηρεσία μετάφρασης με τεχνητή νοημοσύνη [Co-op Translator](https://github.com/Azure/co-op-translator). Παρά τις προσπάθειές μας για ακρίβεια, παρακαλούμε να λάβετε υπόψη ότι οι αυτοματοποιημένες μεταφράσεις ενδέχεται να περιέχουν σφάλματα ή ανακρίβειες. Το πρωτότυπο έγγραφο στη γλώσσα του πρέπει να θεωρείται η αξιόπιστη πηγή. Για κρίσιμες πληροφορίες συνιστάται επαγγελματική ανθρώπινη μετάφραση. Δεν φέρουμε ευθύνη για οποιεσδήποτε παρεξηγήσεις ή λανθασμένες ερμηνείες προκύψουν από τη χρήση αυτής της μετάφρασης.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->