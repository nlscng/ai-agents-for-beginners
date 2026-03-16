# Memoria pentru Agenții AI 
[![Agent Memory](../../../translated_images/ro/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Când discutăm despre beneficiile unice ale creării Agenților AI, două aspecte sunt în principal abordate: capacitatea de a apela unelte pentru a finaliza sarcini și capacitatea de a se îmbunătăți în timp. Memoria stă la baza creării unui agent care se poate auto-îmbunătăți și care poate crea experiențe mai bune pentru utilizatorii noștri.

În această lecție, vom analiza ce este memoria pentru Agenții AI și cum o putem gestiona și folosi în beneficiul aplicațiilor noastre.

## Introducere

Această lecție va acoperi:

• **Înțelegerea Memoriei Agenților AI**: Ce este memoria și de ce este esențială pentru agenți.

• **Implementarea și Stocarea Memoriei**: Metode practice pentru adăugarea capacităților de memorie agenților AI, cu accent pe memoria pe termen scurt și lung.

• **Facerea Agenților AI Auto-Îmbunătățitori**: Cum permite memoria agenților să învețe din interacțiunile anterioare și să se îmbunătățească în timp.

## Implementări Disponibile

Această lecție include două tutoriale cu notebook-uri detaliate:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementează memoria folosind Mem0 și Azure AI Search cu framework-ul Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementează memoria structurată folosind Cognee, construind automat un grafic de cunoștințe susținut de embeddings, vizualizând graficul și realizând recuperarea inteligentă

## Obiective de Învățare

După finalizarea acestei lecții, vei ști cum să:

• **Diferențiezi între diferite tipuri de memorie ale agenților AI**, inclusiv memoria de lucru, memoria pe termen scurt și pe termen lung, precum și forme specializate precum memoria persona și episodică.

• **Implementezi și gestionezi memoria pe termen scurt și lung pentru agenții AI** folosind framework-ul Semantic Kernel, valorificând unelte precum Mem0, Cognee, Whiteboard memory și integrând cu Azure AI Search.

• **Înțelegi principiile din spatele agenților AI auto-îmbunătățitori** și cum sistemele robuste de gestionare a memoriei contribuie la învățarea și adaptarea continuă.

## Înțelegerea Memoriei Agenților AI

În esență, **memoria pentru agenții AI se referă la mecanismele care le permit să rețină și să reamintească informații**. Aceste informații pot fi detalii specifice despre o conversație, preferințe ale utilizatorului, acțiuni anterioare sau chiar tipare învățate.

Fără memorie, aplicațiile AI sunt adesea fără stare (stateless), ceea ce înseamnă că fiecare interacțiune începe de la zero. Acest lucru conduce la o experiență utilizator repetitivă și frustrantă, unde agentul "uită" contextul sau preferințele anterioare.

### De ce este Importantă Memoria?

Inteligența unui agent este adânc legată de capacitatea sa de a reaminti și utiliza informații din trecut. Memoria permite agenților să fie:

• **Reflectivi**: Să învețe din acțiunile și rezultatele anterioare.

• **Interactivi**: Să mențină contextul pe parcursul unei conversații continue.

• **Proactivi și Reactivi**: Să anticipeze nevoi sau să răspundă adecvat pe baza datelor istorice.

• **Autonomi**: Să funcționeze mai independent bazându-se pe cunoștințele stocate.

Scopul implementării memoriei este de a face agenții mai **de încredere și capabili**.

### Tipuri de Memorie

#### Memoria de Lucru

Gândește-te la aceasta ca la o bucată de hârtie pe care un agent o folosește în timpul unei singure sarcini sau procese de gândire în desfășurare. Ea păstrează informațiile imediate necesare pentru a calcula pasul următor.

Pentru agenții AI, memoria de lucru capturează adesea cele mai relevante informații dintr-o conversație, chiar dacă întregul istoric al discuției este lung sau trunchiat. Se concentrează pe extragerea elementelor cheie precum cerințe, propuneri, decizii și acțiuni.

**Exemplu Memorie de Lucru**

Într-un agent de rezervări de călătorie, memoria de lucru poate captura cererea curentă a utilizatorului, cum ar fi „Vreau să rezerv o excursie la Paris”. Această cerință specifică este menținută în contextul imediat al agentului pentru a ghida interacțiunea curentă.

#### Memoria pe Termen Scurt

Acest tip de memorie reține informații pe durata unei singure conversații sau sesiuni. Este contextul discuției curente, permițând agentului să se refere înapoi la ture anterioare din dialog.

**Exemplu Memorie pe Termen Scurt**

Dacă un utilizator întreabă „Cât ar costa un zbor spre Paris?” și apoi continuă cu „Dar cazarea acolo?”, memoria pe termen scurt asigură că agentul știe că „acolo” se referă la „Paris” în cadrul aceleiași conversații.

#### Memoria pe Termen Lung

Aceasta este informația care persistă pe parcursul mai multor conversații sau sesiuni. Permite agenților să-și amintească preferințele utilizatorului, interacțiunile istorice sau cunoștințe generale pe perioade extinse. Este importantă pentru personalizare.

**Exemplu Memorie pe Termen Lung**

O memorie pe termen lung ar putea stoca faptul că „Ben se bucură de schi și activități în aer liber, îi place cafeaua cu vedere la munte și dorește să evite pârtiile avansate din cauza unei accidentări anterioare”. Această informație, învățată din interacțiuni anterioare, influențează recomandările în sesiunile viitoare de planificare a călătoriilor, făcându-le foarte personalizate.

#### Memoria Persona

Acest tip specializat de memorie ajută un agent să dezvolte o „personalitate” sau „persona” consistentă. Permite agentului să-și reamintească detalii despre sine sau despre rolul său intenționat, făcând interacțiunile mai fluide și concentrate.

**Exemplu Memorie Persona**

Dacă agentul de călătorii este conceput să fie un „expert în planificarea schiului,” memoria persona ar putea consolida acest rol, influențând răspunsurile pentru a se alinia cu tonul și cunoștințele unui expert.

#### Memoria Workflow/Episodică

Această memorie stochează succesiunea pașilor pe care un agent îi urmează în timpul unei sarcini complexe, incluzând succese și eșecuri. Este ca și cum ar reține „episoade” specifice sau experiențe trecute pentru a învăța din ele.

**Exemplu Memorie Episodică**

Dacă agentul a încercat să rezerve un zbor specific, dar a eșuat din cauza indisponibilității, memoria episodică ar putea înregistra acest eșec, permițând agentului să încerce zboruri alternative sau să informeze utilizatorul despre problemă într-un mod mai bine informat la o încercare ulterioară.

#### Memoria Entității

Aceasta implică extragerea și reținerea unor entități specifice (precum persoane, locuri sau obiecte) și evenimente din conversații. Permite agentului să construiască o înțelegere structurată a elementelor principale discutate.

**Exemplu Memorie Entitate**

Dintr-o conversație despre o călătorie anterioară, agentul ar putea extrage „Paris”, „Turnul Eiffel” și „cina la restaurantul Le Chat Noir” ca entități. La o interacțiune viitoare, agentul ar putea reține „Le Chat Noir” și să ofere să facă o nouă rezervare acolo.

#### RAG Structurat (Retrieval Augmented Generation)

Deși RAG este o tehnică mai largă, „RAG Structurat” este evidențiat ca o tehnologie puternică de memorie. Aceasta extrage informații dense, structurate, din diverse surse (conversații, emailuri, imagini) și le folosește pentru a spori precizia, rechemarea și viteza răspunsurilor. Spre deosebire de RAG-ul clasic care se bazează exclusiv pe similaritatea semantică, RAG Structurat funcționează cu structura inerentă a informațiilor.

**Exemplu RAG Structurat**

În loc să se potrivească doar cuvinte-cheie, RAG Structurat ar putea analiza detaliile unui zbor (destinație, dată, oră, companie aeriană) dintr-un email și să le stocheze într-un mod structurat. Acest lucru permite interogări precise precum „Ce zbor am rezervat spre Paris marți?”

## Implementarea și Stocarea Memoriei

Implementarea memoriei pentru agenții AI implică un proces sistematic de **gestionare a memoriei**, care include generarea, stocarea, recuperarea, integrarea, actualizarea și chiar „uitarea” (sau ștergerea) informațiilor. Recuperarea este un aspect deosebit de crucial.

### Unelte Specializate pentru Memorie

#### Mem0

Un mod de a stoca și gestiona memoria agentului este folosind unelte specializate precum Mem0. Mem0 funcționează ca un strat persistent de memorie, permițând agenților să reamintească interacțiunile relevante, să stocheze preferințe ale utilizatorului și contexte factuale și să învețe din succese și eșecuri în timp. Ideea este că agenții fără stare devin agenți cu stare.

Funcționează printr-un **proces în două faze: extragere și actualizare**. Mai întâi, mesajele adăugate la firul unui agent sunt trimise către serviciul Mem0, care folosește un Model de Limbaj Mare (LLM) pentru a rezuma istoricul conversației și a extrage noi amintiri. Ulterior, o fază de actualizare condusă de LLM decide dacă să adauge, modifice sau șteargă aceste amintiri, stocându-le într-un depozit de date hibrid care poate include baze de date vectoriale, grafice și cheie-valoare. Acest sistem suportă, de asemenea, diverse tipuri de memorie și poate include memoria în graf pentru gestionarea relațiilor între entități.

#### Cognee

O altă abordare puternică este folosirea **Cognee**, o memorie semantică open-source pentru agenții AI care transformă date structurate și nestructurate în grafice de cunoștințe interogabile susținute de embeddings. Cognee oferă o **arhitectură dual-store** care combină căutarea după similaritate vectorială cu relațiile grafice, permițând agenților să înțeleagă nu doar ce informație este similară, ci și cum conceptele sunt legate între ele.

Excelentă pentru **recuperare hibridă** care combină similaritatea vectorială, structura grafică și raționamentul LLM — de la căutarea fragmentelor brute la răspunsuri la întrebări conștiente de graf. Sistemul menține o **memorie vie** care evoluează și crește, rămânând totodată interogabilă ca un graf conectat, suportând atât contextul de sesiune pe termen scurt, cât și memoria persistentă pe termen lung.

Tutorialul din notebook-ul Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstrează construirea acestui strat unificat de memorie, cu exemple practice de ingestie a unor surse diverse de date, vizualizarea graficului de cunoștințe și interogarea cu diferite strategii de căutare adaptate nevoilor specifice ale agentului.

### Stocarea Memoriei cu RAG

Dincolo de uneltele specializate de memorie precum Mem0, poți valorifica servicii robuste de căutare precum **Azure AI Search ca backend pentru stocarea și recuperarea amintirilor**, în special pentru RAG structurat.

Acest lucru îți permite să asiguri răspunsurile agentului cu propriile date, garantând răspunsuri mai relevante și precise. Azure AI Search poate fi folosit pentru a stoca amintirile de călătorie specifice utilizatorului, cataloage de produse sau orice altă cunoaștere specifică unui domeniu.

Azure AI Search suportă capabilități precum **RAG Structurat**, care excelează în extragerea și recuperarea informațiilor dense și structurate din seturi mari de date, precum istoricul conversațiilor, emailuri sau chiar imagini. Aceasta oferă „precizie și rechemare supra-umană” comparativ cu abordările tradiționale de fragmentare a textului și embeddings.

## Facerea Agenților AI să se Auto-Îmbunătățească

Un tipar comun pentru agenții auto-îmbunătățitori implică introducerea unui **„agent de cunoaștere”**. Acest agent separat observă conversația principală dintre utilizator și agentul principal. Rolul său este să:

1. **Identifice informații valoroase**: să determine dacă vreo parte a conversației merită salvată ca cunoaștere generală sau preferință specifică a utilizatorului.

2. **Extragă și rezume**: să distileze învățătura esențială sau preferința din conversație.

3. **Stocheze într-o bază de cunoștințe**: să păstreze aceste informații extrase, adesea într-o bază de date vectorială, pentru a putea fi recuperate ulterior.

4. **Completeze interogările viitoare**: când utilizatorul inițiază o nouă interogare, agentul de cunoaștere recuperează informațiile relevante stocate și le atașează promptului utilizatorului, oferind agentului principal context esențial (similar RAG).

### Optimizări pentru Memorie

• **Gestionarea Latenței**: Pentru a evita încetinirea interacțiunilor cu utilizatorul, poate fi folosit inițial un model mai ieftin și mai rapid care verifică rapid dacă o informație merită salvată sau recuperată, invocând doar procesul mai complex de extragere/recuperare când este necesar.

• **Mentenanța Bazei de Cunoștințe**: Pentru o bază de cunoștințe în creștere, informațiile folosite mai puțin frecvent pot fi mutate în „stocare rece” pentru a gestiona costurile.

## Ai Mai Multe Întrebări Despre Memoria Agenților?

Alătură-te [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la ore de consultații și a-ți primi răspunsurile la întrebările despre Agenții AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Declinare de responsabilitate**:
Acest document a fost tradus folosind serviciul de traducere AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim să asigurăm acuratețea, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original, în limba sa nativă, trebuie considerat sursa autoritară. Pentru informații critice, se recomandă traducerea profesională realizată de un specialist uman. Nu ne asumăm răspunderea pentru neînțelegeri sau interpretări eronate care pot apărea în urma utilizării acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->