# Utilizarea Protocoalelor Agentice (MCP, A2A și NLWeb)

[![Protocoale Agentice](../../../translated_images/ro/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Faceți clic pe imaginea de mai sus pentru a viziona videoclipul acestei lecții)_

Pe măsură ce utilizarea agenților AI crește, crește și necesitatea protocoalelor care să asigure standardizarea, securitatea și să sprijine inovația deschisă. În această lecție, vom acoperi 3 protocoale care încearcă să satisfacă această nevoie - Model Context Protocol (MCP), Agent to Agent (A2A) și Natural Language Web (NLWeb).

## Introducere

În această lecție, vom acoperi:

• Cum **MCP** permite agenților AI să acceseze unelte și date externe pentru a îndeplini sarcini ale utilizatorului.

• Cum **A2A** facilitează comunicarea și colaborarea între diferiți agenți AI.

• Cum **NLWeb** aduce interfețe în limbaj natural pe orice site web, permițând agenților AI să descopere și să interacționeze cu conținutul.

## Obiective de Învățare

• **Identificați** scopul principal și beneficiile MCP, A2A și NLWeb în contextul agenților AI.

• **Explicați** modul în care fiecare protocol facilitează comunicarea și interacțiunea între LLM-uri, unelte și alți agenți.

• **Recunoașteți** rolurile distincte pe care fiecare protocol le joacă în construirea sistemelor complexe agentice.

## Model Context Protocol

**Model Context Protocol (MCP)** este un standard deschis care oferă o modalitate standardizată pentru aplicații de a furniza context și unelte către LLM-uri. Aceasta permite un „adaptor universal” către diferite surse de date și unelte la care agenții AI se pot conecta într-un mod consistent.

Să privim componentele MCP, beneficiile în comparație cu utilizarea directă a API-urilor și un exemplu despre cum agenții AI pot folosi un server MCP.

### Componente de Bază MCP

MCP funcționează pe o **arhitectură client-server** iar componentele de bază sunt:

• **Gazdele (Hosts)** sunt aplicații LLM (de exemplu un editor de cod precum VSCode) care inițiază conexiunile către un server MCP.

• **Clienții (Clients)** sunt componente în cadrul aplicației gazdă care mențin conexiuni unu-la-unu cu serverele.

• **Serverele (Servers)** sunt programe ușoare care expun capabilități specifice.

Protocolul include trei primitive de bază care sunt capabilitățile unui server MCP:

• **Unelte (Tools)**: Acestea sunt acțiuni discrete sau funcții pe care un agent AI le poate apela pentru a executa o acțiune. De exemplu, un serviciu de vreme ar putea expune o unealtă „obține vremea” sau un server de e-commerce ar putea expune o unealtă „cumpără produs”. Serverele MCP anunță pentru fiecare unealtă numele, descrierea și schema de intrare/ieșire în lista lor de capabilități.

• **Resurse (Resources)**: Acestea sunt elemente de date sau documente doar pentru citire pe care un server MCP le poate oferi, și pe care clienții le pot extrage la cerere. Exemple includ conținut de fișiere, înregistrări din baze de date sau fișiere jurnal. Resursele pot fi text (cum ar fi cod sau JSON) sau binare (cum ar fi imagini sau PDF-uri).

• **Prompturi (Prompts)**: Sunt șabloane predefinite care oferă prompturi sugerate, permițând fluxuri de lucru mai complexe.

### Beneficiile MCP

MCP oferă avantaje semnificative pentru agenții AI:

• **Descoperire Dinamică a Uneltelor**: Agenții pot primi dinamic o listă a uneltelor disponibile de la un server împreună cu descrierile celor ce fac. Acest lucru contrastează cu API-urile tradiționale, care de obicei necesită codare statică pentru integrări, ceea ce înseamnă că orice schimbare a API-ului necesită actualizări de cod. MCP oferă o abordare „integrează o dată”, conducând la o adaptabilitate mai mare.

• **Interoperabilitate între LLM-uri**: MCP funcționează cu diferite LLM-uri, oferind flexibilitatea de a schimba modelele principale pentru o performanță mai bună.

• **Securitate Standardizată**: MCP include o metodă standard de autentificare, îmbunătățind scalabilitatea când se adaugă acces la servere MCP suplimentare. Acest lucru este mai simplu decât gestionarea cheilor și tipurilor de autentificare diferite pentru diverse API-uri tradiționale.

### Exemplu MCP

![MCP Diagram](../../../translated_images/ro/mcp-diagram.e4ca1cbd551444a1.webp)

Imaginați-vă că un utilizator dorește să rezerve un zbor folosind un asistent AI alimentat de MCP.

1. **Conexiune**: Asistentul AI (clientul MCP) se conectează la un server MCP furnizat de o companie aeriană.

2. **Descoperirea Uneltelor**: Clientul întreabă serverul MCP al companiei aeriene: „Ce unelte aveți disponibile?” Serverul răspunde cu unelte precum „caută zboruri” și „rezervă zboruri”.

3. **Invocarea Unealtei**: Utilizatorul îi cere atunci asistentului AI: „Te rog caută un zbor de la Portland la Honolulu.” Asistentul AI, folosind LLM-ul său, identifică că trebuie să apeleze unealta „caută zboruri” și transmite parametrii relevanți (plecare, destinație) către serverul MCP.

4. **Executare și Răspuns**: Serverul MCP, funcționând ca un înveliș, face apelul efectiv la API-ul intern de rezervări al companiei aeriene. Apoi primește informațiile despre zbor (de exemplu date JSON) și le trimite înapoi către asistentul AI.

5. **Interacțiune Ulterioară**: Asistentul AI prezintă opțiunile de zbor. După ce selectați un zbor, asistentul poate invoca unealta „rezervă zbor” pe același server MCP, finalizând rezervarea.

## Protocolul Agent-la-Agent (A2A)

În timp ce MCP se concentrează pe conectarea LLM-urilor la unelte, **Agent-to-Agent (A2A)** face un pas mai departe permițând comunicarea și colaborarea între diferiți agenți AI. A2A conectează agenți AI din diferite organizații, medii și tehnologii pentru a îndeplini o sarcină comună.

Vom examina componentele și beneficiile A2A, împreună cu un exemplu despre cum ar putea fi aplicat în aplicația noastră de călătorii.

### Componente de Bază A2A

A2A se concentrează pe a permite comunicarea între agenți și cooperarea lor pentru a finaliza o sub-sarcină a utilizatorului. Fiecare componentă a protocolului contribuie la aceasta:

#### Agent Card

Similar cu modul în care un server MCP împărtășește o listă de unelte, un Agent Card conține:
- Numele agentului.
- O **descriere a sarcinilor generale** pe care le îndeplinește.
- O **listă de abilități specifice** cu descrieri pentru a ajuta alți agenți (sau chiar utilizatori umani) să înțeleagă când și de ce ar dori să apeleze acel agent.
- **URL-ul Endpoint-ului curent** al agentului
- **Versiunea** și **capabilitățile** agentului, cum ar fi răspunsuri în streaming și notificări push.

#### Agent Executor

Agent Executor este responsabil pentru **transmiterea contextului conversației utilizatorului către agentul la distanță**, agentul la distanță are nevoie de acest context pentru a înțelege sarcina ce trebuie îndeplinită. Într-un server A2A, agentul folosește propriul său Model de Limbaj (LLM) pentru a analiza cererile primite și a executa sarcini folosind uneltele interne.

#### Artifact

Odată ce agentul la distanță a finalizat sarcina solicitată, produsul muncii sale este creat sub forma unui artifact. Un artifact **conține rezultatul muncii agentului**, o **descriere a ceea ce a fost realizat** și **contextul text care este transmis prin protocol**. După ce artifact-ul este trimis, conexiunea cu agentul la distanță este închisă până când va fi din nou necesară.

#### Event Queue

Această componentă este folosită pentru **gestionarea actualizărilor și transmiterea mesajelor**. Este deosebit de importantă în producție pentru sistemele agentice pentru a preveni închiderea conexiunii între agenți înainte ca o sarcină să fie completă, mai ales când timpul de finalizare poate fi mai lung.

### Beneficiile A2A

• **Colaborare Îmbunătățită**: Permite agenților de la diferiți furnizori și platforme să interacționeze, să împărtășească context și să lucreze împreună, facilitând automatizarea fără întreruperi între sisteme tradițional separate.

• **Flexibilitate în Selectarea Modelului**: Fiecare agent A2A poate decide ce LLM utilizează pentru a gestiona cererile sale, permițând modele optimizate sau ajustate pentru fiecare agent, spre deosebire de o singură conexiune LLM în unele scenarii MCP.

• **Autentificare Integrată**: Autentificarea este integrată direct în protocolul A2A, oferind un cadru robust de securitate pentru interacțiunile agenților.

### Exemplu A2A

![A2A Diagram](../../../translated_images/ro/A2A-Diagram.8666928d648acc26.webp)

Să dezvoltăm scenariul nostru de rezervare călătorii, de data aceasta folosind A2A.

1. **Cererea Utilizatorului către Multi-Agent**: Un utilizator interacționează cu un client/agent A2A „Agent de Călătorii”, poate spunând: „Te rog rezervă o excursie completă la Honolulu săptămâna viitoare, inclusiv zboruri, hotel și mașină închiriată”.

2. **Orchestrare de către Agentul de Călătorii**: Agentul de Călătorii primește această cerere complexă. Folosește LLM-ul său pentru a analiza sarcina și pentru a determina că trebuie să interacționeze cu alți agenți specializați.

3. **Comunicare Inter-Agent**: Agentul de Călătorii folosește protocolul A2A pentru a se conecta cu agenți din aval, cum ar fi „Agentul Companiei Aeriene”, „Agentul Hotelului” și „Agentul de Închirieri Auto” create de companii diferite.

4. **Executarea Sarcinilor Delegated**: Agentul de Călătorii trimite sarcini specifice acestor agenți specializați (de ex., „Găsește zboruri către Honolulu”, „Rezervă un hotel”, „Închiriază o mașină”). Fiecare agent specializat, folosind propriul LLM și propriile unelte (care pot fi chiar servere MCP), execută partea sa specifică din rezervare.

5. **Răspuns Consolidat**: După ce toți agenții aval finalizează sarcinile, Agentul de Călătorii compilează rezultatele (detalii zbor, confirmare hotel, rezervare mașină) și trimite un răspuns complet, de tip chat, înapoi utilizatorului.

## Natural Language Web (NLWeb)

Site-urile web au fost mult timp modalitatea principală prin care utilizatorii accesează informații și date pe internet.

Să privim componentele diferite ale NLWeb, beneficiile acestuia și un exemplu de utilizare a NLWeb prin aplicația noastră de călătorii.

### Componentele NLWeb

- **Aplicația NLWeb (Codul Serviciului de Bază)**: Sistemul care procesează întrebările în limbaj natural. Leagă părțile diferite ale platformei pentru a crea răspunsuri. Poate fi considerat **motorul care alimentează funcțiile de limbaj natural** ale unui site web.

- **Protocolul NLWeb**: Un **set de reguli de bază pentru interacțiunea în limbaj natural** cu un site web. Trimite răspunsuri în format JSON (adesea folosind Schema.org). Scopul său este să creeze o fundație simplă pentru „Web-ul AI”, la fel cum HTML a făcut posibilă partajarea documentelor online.

- **Server MCP (Endpoint Protocol Model Context)**: Fiecare configurație NLWeb funcționează și ca un **server MCP**. Aceasta înseamnă că poate **partaja unelte (cum ar fi metoda „ask”) și date** cu alte sisteme AI. Practic, aceasta face conținutul și capabilitățile site-ului să fie utilizabile de către agenții AI, permițând site-ului să devină parte a ecosistemului mai larg „agent”.

- **Modele de Embedding**: Aceste modele sunt folosite pentru a **converti conținutul site-ului în reprezentări numerice numite vectori** (embedding-uri). Acești vectori capturează semnificația într-un mod pe care calculatoarele îl pot compara și căuta. Aceștia sunt stocați într-o bază de date specială, iar utilizatorii pot alege modelul embedding dorit.

- **Baza de date Vectorială (Mecanism de Recuperare)**: Această bază de date **stochează embedding-urile conținutului site-ului**. Când cineva pune o întrebare, NLWeb verifică baza de date vectorială pentru a găsi rapid cele mai relevante informații. Oferă o listă rapidă de posibile răspunsuri, ordonate după similaritate. NLWeb funcționează cu diferite sisteme de stocare vectorială cum ar fi Qdrant, Snowflake, Milvus, Azure AI Search și Elasticsearch.

### NLWeb prin Exemplu

![NLWeb](../../../translated_images/ro/nlweb-diagram.c1e2390b310e5fe4.webp)

Să considerăm din nou site-ul nostru de rezervări de călătorii, de data aceasta alimentat de NLWeb.

1. **Încărcarea Datelor**: Cataloagele de produse existente ale site-ului de călătorii (de ex., liste de zboruri, descrieri hoteluri, oferte de tururi) sunt formatate folosind Schema.org sau încărcate prin RSS feeds. Uneltele NLWeb preiau aceste date structurate, creează embedding-uri și le stochează într-o bază de date vectorială locală sau la distanță.

2. **Interogare în Limbaj Natural (Uman)**: Un utilizator vizitează site-ul și, în loc să navigheze prin meniuri, tastează într-o interfață de chat: „Găsește-mi un hotel prietenos cu familiile în Honolulu, cu piscină, pentru săptămâna viitoare”.

3. **Procesare NLWeb**: Aplicația NLWeb primește această întrebare. Trimite interogarea către un LLM pentru înțelegere și în același timp caută în baza sa de date vectorială liste relevante de hoteluri.

4. **Rezultate Precise**: LLM-ul ajută la interpretarea rezultatelor din baza de date, identifică cele mai bune potriviri bazate pe criteriile „prietenos cu familiile”, „piscină” și „Honolulu” și apoi formulează un răspuns în limbaj natural. Esențial, răspunsul face referire la hoteluri reale din catalogul site-ului, evitând informații inventate.

5. **Interacțiunea Agenților AI**: Deoarece NLWeb funcționează ca un server MCP, un agent AI extern de călătorii se poate conecta de asemenea la această instanță NLWeb a site-ului. Agentul AI ar putea folosi metoda MCP `ask` pentru a interoga direct site-ul: `ask("Există restaurante vegane recomandate de hotel în zona Honolulu?")`. Instanța NLWeb va procesa aceasta, folosind baza sa de date cu informații despre restaurante (dacă este încărcată), și va returna un răspuns JSON structurat.

### Aveți Mai Multe Întrebări despre MCP/A2A/NLWeb?

Alăturați-vă [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la sesiuni de birou și a primi răspunsuri la întrebările despre Agenții AI.

## Resurse

- [MCP pentru Începători](https://aka.ms/mcp-for-beginners)  
- [Documentația MCP](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Repo NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Ghiduri Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Declinare de responsabilitate**:  
Acest document a fost tradus utilizând serviciul de traducere AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original în limba sa nativă trebuie considerat sursa oficială. Pentru informații critice, se recomandă traducerea profesională realizată de un specialist uman. Nu ne asumăm responsabilitatea pentru neînțelegeri sau interpretări greșite care pot rezulta din utilizarea acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->