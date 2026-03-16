# Agenți AI în Producție: Observabilitate și Evaluare

[![Agenți AI în Producție](../../../translated_images/ro/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

Pe măsură ce agenții AI trec de la prototipuri experimentale la aplicații reale, devine importantă capacitatea de a înțelege comportamentul lor, de a monitoriza performanța și de a evalua sistematic rezultatele.

## Obiectivele învățării

După finalizarea acestei lecții, vei ști cum să/vei înțelege:
- Conceptele de bază ale observabilității și evaluării agenților
- Tehnici pentru îmbunătățirea performanței, costurilor și eficienței agenților
- Ce și cum să evaluezi sistematic agenții tăi AI
- Cum să controlezi costurile la implementarea agenților AI în producție
- Cum să instrumentezi agenți construiți cu AutoGen

Scopul este să te echipezi cu cunoștințele necesare pentru a transforma agenții „cutie neagră” în sisteme transparente, gestionabile și de încredere.

_**Notă:** Este important să implementezi agenți AI care sunt siguri și demni de încredere. Verifică și lecția [Construirea Agenților AI Demni de Încredere](./06-building-trustworthy-agents/README.md)._

## Urmăriri și Pași

Unelte de observabilitate precum [Langfuse](https://langfuse.com/) sau [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) reprezintă de obicei execuțiile agenților ca urmăriri și pași.

- **Urmărire** reprezintă o sarcină completă a agentului de la început până la sfârșit (de exemplu, procesarea unei interogări a utilizatorului).
- **Pașii** sunt etape individuale din urmărire (de exemplu, apelarea unui model de limbaj sau recuperarea datelor).

![Trace tree in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Fără observabilitate, un agent AI poate părea o „cutie neagră” – starea și raționamentul intern sunt opace, ceea ce face dificilă diagnosticarea problemelor sau optimizarea performanței. Cu observabilitate, agenții devin „cutii de sticlă”, oferind transparență esențială pentru a construi încredere și a asigura funcționarea conform intențiilor.

## De ce este importantă observabilitatea în mediile de producție

Trecerea agenților AI în mediile de producție introduce o nouă serie de provocări și cerințe. Observabilitatea nu mai este un „nice-to-have”, ci o capacitate critică:

*   **Depanare și Analiză a Cauzei Rădăcină**: Când un agent eșuează sau produce un rezultat neașteptat, uneltele de observabilitate furnizează urmăriri necesare pentru identificarea sursei erorii. Acest lucru este esențial în agenți complexi care pot implica mai multe apeluri la modele LLM, interacțiuni cu unelte și logică condiționată.
*   **Gestionarea latenței și costurilor**: Agenții AI se bazează adesea pe LLM-uri și alte API-uri externe care sunt taxate per token sau per apel. Observabilitatea permite urmărirea precisă a acestor apeluri, ajutând la identificarea operațiunilor excesiv de lente sau scumpe. Acest lucru permite echipelor să optimizeze solicitările, să selecteze modele mai eficiente sau să redeseneze fluxurile de lucru pentru a gestiona costurile operaționale și a asigura o experiență utilizator bună.
*   **Încredere, Siguranță și Conformitate**: În multe aplicații, este important să se asigure că agenții se comportă sigur și etic. Observabilitatea oferă un traseu de audit al acțiunilor și deciziilor agentului. Acesta poate fi utilizat pentru a detecta și atenua probleme precum injecția de comenzi (prompt injection), generarea de conținut dăunător sau gestionarea greșită a informațiilor personale identificabile (PII). De exemplu, poți revizui urmăriri pentru a înțelege de ce un agent a oferit un anumit răspuns sau a folosit un anumit instrument.
*   **Buclă continuă de îmbunătățire**: Datele de observabilitate sunt fundația unui proces iterativ de dezvoltare. Prin monitorizarea performanței agenților în lumea reală, echipele pot identifica domenii de îmbunătățire, pot colecta date pentru optimizarea modelelor și valida impactul schimbărilor. Aceasta creează o buclă de feedback în care informațiile din producție obținute din evaluarea online alimentează experimentarea și rafinarea offline, conducând la performanțe din ce în ce mai bune ale agentului.

## Metrici cheie de urmărit

Pentru a monitoriza și înțelege comportamentul agentului, trebuie urmărită o varietate de metrici și semnale. Deși metricile specifice pot varia în funcție de scopul agentului, unele sunt universal importante.

Iată câteva dintre cele mai comune metrici monitorizate de uneltele de observabilitate:

**Latența:** Cât de rapid răspunde agentul? Timpurile lungi de așteptare afectează negativ experiența utilizatorului. Trebuie să măsori latența pentru sarcini și pași individuali urmărind execuțiile agentului. De exemplu, un agent care ia 20 de secunde pentru toate apelurile la model poate fi accelerat folosind un model mai rapid sau apelând modelele în paralel.

**Costuri:** Care este costul per execuție a agentului? Agenții AI se bazează pe apeluri LLM facturate per token sau API-uri externe. Utilizarea frecventă a uneltelor sau multiple solicitări pot crește rapid costurile. De exemplu, dacă un agent apelează un LLM de cinci ori pentru o îmbunătățire marginală a calității, trebuie să evaluezi dacă costul este justificat sau dacă poți reduce numărul de apeluri ori folosi un model mai ieftin. Monitorizarea în timp real poate ajuta și la identificarea creșterilor neașteptate (ex. bug-uri care provoacă bucle excesive cu API-ul).

**Erori la cereri:** Câte cereri au eșuat? Acest lucru poate include erori API sau apeluri eșuate ale uneltelor. Pentru a face agentul mai robust în producție, poți seta apoi mecanisme de fallback sau reîncercări. De ex., dacă furnizorul LLM A cade, treci automat la furnizorul LLM B ca rezervă.

**Feedback Utilizator:** Implementarea evaluărilor directe ale utilizatorilor oferă informații valoroase. Aceasta poate include evaluări explicite (👍like/👎dislike, ⭐1-5 stele) sau comentarii textuale. Feedback-ul negativ constant ar trebui să te alerteze, fiind un semn că agentul nu funcționează conform așteptărilor.

**Feedback implicit al utilizatorului:** Comportamentul utilizatorilor oferă feedback indirect chiar și fără evaluări explicite. Acesta poate include reformularea imediată a întrebărilor, întrebări repetate sau apăsarea butonului de retry. De ex., dacă observi că utilizatorii repetă aceeași întrebare, este un semn că agentul nu funcționează corespunzător.

**Acuratețe:** Cât de frecvent produce agentul rezultate corecte sau dorite? Definițiile acurateții variază (ex. corectitudinea rezolvării problemelor, acuratețea recuperării informațiilor, satisfacția utilizatorului). Primul pas este să definești ce înseamnă succes pentru agentul tău. Poți monitoriza acuratețea prin verificări automate, scoruri de evaluare sau etichete de finalizare a sarcinii. De exemplu, marcarea urmăririlor ca „reușite” sau „eșuate”.

**Metrici automate de evaluare:** Poți seta și evaluări automate. De exemplu, poți folosi un LLM pentru a acorda un scor ieșirii agentului, de exemplu dacă este utilă, corectă sau nu. Există și mai multe biblioteci open source care te ajută să evaluezi diferite aspecte ale agentului. De ex. [RAGAS](https://docs.ragas.io/) pentru agenți RAG sau [LLM Guard](https://llm-guard.com/) pentru detectarea limbajului dăunător sau injecția de prompturi.

În practică, o combinație dintre aceste metrici oferă cea mai completă imagine a stării de sănătate a unui agent AI. În [notebook-ul exemplu](./code_samples/10_autogen_evaluation.ipynb) din acest capitol, îți vom arăta cum arată aceste metrici în exemple reale, dar mai întâi vom învăța cum arată un flux tipic de evaluare.

## Instrumentează-ți Agentul

Pentru a colecta date de urmărire, trebuie să instrumentezi codul. Scopul este de a instrumenta codul agentului astfel încât să emită urmăriri și metrici care pot fi capturate, procesate și vizualizate de o platformă de observabilitate.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) a devenit un standard industrial pentru observabilitatea LLM-urilor. Oferă un set de API-uri, SDK-uri și unelte pentru generarea, colectarea și exportarea datelor de telemetrie.

Există multe biblioteci de instrumentare care învelesc cadrul existent de agenți și facilitează exportul de pași OpenTelemetry către un instrument de observabilitate. Mai jos este un exemplu de instrumentare a unui agent AutoGen cu biblioteca de instrumentare [OpenLit](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

[Notebook-ul exemplu](./code_samples/10_autogen_evaluation.ipynb) din acest capitol va demonstra cum să instrumentezi agentul tău AutoGen.

**Creare manuală de pași:** Deși bibliotecile de instrumentare oferă o bază bună, deseori sunt cazuri când se dorește informație mai detaliată sau personalizată. Poți crea manual pași pentru a adăuga logică personalizată aplicației. Mai important, aceștia pot îmbogăți pașii creați automat sau manual cu atribute personalizate (cunoscute și ca taguri sau metadata). Aceste atribute pot include date specifice business-ului, calcule intermediare sau orice context util pentru depanare sau analiză, precum `user_id`, `session_id` sau `model_version`.

Exemplu de creare manuală a urmăririlor și pașilor cu [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3):

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Evaluarea Agentului

Observabilitatea ne oferă metrici, dar evaluarea este procesul de analizare a acelor date (și efectuarea de teste) pentru a determina cât de bine performează un agent AI și cum poate fi îmbunătățit. Cu alte cuvinte, după ce ai acele urmăriri și metrici, cum le folosești pentru a judeca agentul și a lua decizii?

Evaluarea regulată este importantă deoarece agenții AI sunt adesea nedeterministici și pot evolua (prin actualizări sau schimbarea comportamentului modelului) – fără evaluare, nu ai ști dacă „agentul inteligent” își face bine treaba sau dacă a regresat.

Există două categorii de evaluări pentru agenții AI: **evaluare online** și **evaluare offline**. Ambele sunt valoroase și se completează reciproc. De obicei începem cu evaluarea offline, deoarece este pasul minim necesar înainte de a implementa un agent.

### Evaluarea Offline

![Dataset items in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

Aceasta implică evaluarea agentului într-un mediu controlat, de obicei folosind seturi de date de test, nu interogări live ale utilizatorilor. Folosești seturi de date curate unde știi care este rezultatul așteptat sau comportamentul corect și rulezi apoi agentul pe acestea.

De exemplu, dacă ai construit un agent pentru rezolvarea problemelor de matematică, ai putea avea un [set de date de test](https://huggingface.co/datasets/gsm8k) cu 100 de probleme cu răspunsuri cunoscute. Evaluarea offline se face adesea în timpul dezvoltării (și poate face parte din pipeline-uri CI/CD) pentru a verifica îmbunătățirile sau a preveni regresiile. Avantajul este că este **repetabilă și poți obține metrici clare de acuratețe deoarece ai adevărul de referință**. Poți de asemenea simula interacțiuni ale utilizatorilor și măsura răspunsurile agentului față de răspunsuri ideale sau folosi metrici automate cum am descris mai sus.

Provocarea cheie a evaluării offline este să te asiguri că setul tău de test este cuprinzător și rămâne relevant – agentul poate performa bine pe un set fix de test, dar să întâlnească interogări foarte diferite în producție. Prin urmare, trebuie să păstrezi seturile de test actualizate cu cazuri marginale și exemple care reflectă scenarii din lumea reală. Un amestec de cazuri mici „smoke test” și seturi de evaluare mai extinse este util: seturi mici pentru verificări rapide și seturi mari pentru metrici mai largi de performanță.

### Evaluarea Online

![Observability metrics overview](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

Aceasta se referă la evaluarea agentului într-un mediu live, real, adică în timpul utilizării reale în producție. Evaluarea online implică monitorizarea performanței agentului pe interacțiunile reale ale utilizatorilor și analizarea continuă a rezultatelor.

De exemplu, poți urmări ratele de succes, scorurile de satisfacție ale utilizatorilor sau alte metrici pe traficul live. Avantajul evaluării online este că **prinde lucruri pe care nu le-ai anticipa într-un mediu de laborator** – poți observa deriva modelului în timp (dacă eficiența agentului scade pe măsură ce pattern-urile de input se schimbă) și poți detecta interogări sau situații neașteptate care nu au fost în datele tale de testare. Oferă o imagine reală a modului în care agentul se comportă în mediu real.

Evaluarea online implică adesea colectarea de feedback implicit și explicit al utilizatorilor, după cum s-a discutat, și posibil rularea de teste în umbră sau teste A/B (unde o nouă versiune a agentului rulează în paralel pentru a fi comparată cu cea veche). Provocarea este că poate fi dificil să obții etichete sau scoruri fiabile pentru interacțiunile live – te poți baza pe feedback-ul utilizatorilor sau pe metrici downstream (ex. dacă utilizatorul a dat click pe rezultat).

### Combinarea celor două

Evaluările online și offline nu se exclud reciproc; sunt foarte complementare. Insight-urile din monitorizarea online (de ex. tipuri noi de interogări unde agentul performează slab) pot fi folosite pentru a completa și îmbunătăți seturile de test offline. Invers, agenții care performează bine în testele offline pot fi apoi implementați mai încrezător și monitorizați online.

De fapt, multe echipe adopta o buclă:

_evaluează offline -> implementează -> monitorizează online -> colectează cazuri noi de eșecuri -> adaugă în setul offline -> rafinează agentul -> repetă_.

## Probleme Comune

Pe măsură ce implementezi agenți AI în producție, este posibil să întâmpini diverse provocări. Iată câteva probleme comune și soluțiile potențiale:

| **Problemă**    | **Soluție Potențială**   |
| ------------- | ------------------ |
| Agentul AI nu execută sarcinile în mod consistent | - Ajustează promptul dat agentului AI; fii clar în obiective.<br>- Identifică dacă împărțirea sarcinilor pe subtask-uri și gestionarea acestora de mai mulți agenți poate ajuta. |
| Agentul AI intră în bucle continue  | - Asigură-te că există termeni și condiții clare de terminare, ca agentul să știe când să oprească procesul.<br>- Pentru sarcini complexe ce necesită raționament și planificare, folosește un model mai mare specializat pentru aceste tipuri de sarcini. |
| Apelurile la unelte ale agentului AI nu performează bine   | - Testează și validează rezultatul uneltei în afara sistemului agentului.<br>- Ajustează parametrii, prompturile și denumirile uneltelor. |
| Sistem Multi-Agent nu performează consistent | - Ajustează prompturile date fiecărui agent pentru a fi specifice și distincte.<br>- Construiește un sistem ierarhic folosind un agent „ruter” sau controller pentru a decide care agent este cel potrivit. |

Multe dintre aceste probleme pot fi identificate mai eficient cu observabilitate activă. Urmăririle și metricile discutate anterior ajută să localizezi exact unde în fluxul agentului apar problemele, făcând depanarea și optimizarea mult mai eficiente.

## Gestionarea Costurilor
Iată câteva strategii pentru a gestiona costurile implementării agenților AI în producție:

**Folosirea modelelor mai mici:** Modelele de limbaj mici (SLM) pot performa bine în anumite cazuri de utilizare agentică și vor reduce costurile semnificativ. După cum am menționat mai devreme, construirea unui sistem de evaluare pentru a determina și compara performanța față de modelele mai mari este cea mai bună metodă de a înțelege cât de bine va performa un SLM pe cazul tău de utilizare. Ia în considerare utilizarea SLM-urilor pentru sarcini mai simple, cum ar fi clasificarea intenției sau extragerea parametrilor, în timp ce modelele mai mari le rezervi pentru raționamente complexe.

**Folosirea unui model router:** O strategie similară este utilizarea diversității de modele și dimensiuni. Poți folosi un LLM/SLM sau o funcție serverless pentru a direcționa cererile în funcție de complexitate către modelele cele mai potrivite. Acest lucru va ajuta, de asemenea, la reducerea costurilor, asigurând în același timp performanța pentru sarcinile potrivite. De exemplu, direcționează întrebările simple către modele mai mici și mai rapide și folosește modelele mari și costisitoare doar pentru sarcini de raționament complex.

**Stocarea în cache a răspunsurilor:** Identificarea cererilor și sarcinilor comune și oferirea răspunsurilor înainte ca acestea să treacă prin sistemul tău agentic este o metodă bună de a reduce volumul cererilor similare. Poți chiar implementa un flux pentru a identifica cât de asemănătoare este o cerere cu cele din cache folosind modele AI mai simple. Această strategie poate reduce considerabil costurile pentru întrebările frecvente sau fluxurile de lucru comune.

## Să vedem cum funcționează aceasta în practică

În [notebook-ul exemplu al acestei secțiuni](./code_samples/10_autogen_evaluation.ipynb), vom vedea exemple despre cum putem folosi instrumentele de observabilitate pentru a monitoriza și evalua agentul nostru.

### Ai întrebări despre agenții AI în producție?

Alătură-te [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la sesiuni de consultanță și a primi răspunsuri la întrebările tale despre agenții AI.

## Lecția anterioară

[Modelul de proiectare Metacognition](../09-metacognition/README.md)

## Lecția următoare

[Protocoale agentice](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Declinare de responsabilitate**:  
Acest document a fost tradus folosind serviciul de traducere automată AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original în limba sa nativă trebuie considerat sursa autorizată. Pentru informații critice, se recomandă traducerea profesională realizată de un traducător uman. Nu ne asumăm responsabilitatea pentru eventuale neînțelegeri sau interpretări greșite care pot apărea în urma utilizării acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->