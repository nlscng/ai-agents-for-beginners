[![Design multi-agent](../../../translated_images/ro/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Faceți clic pe imaginea de mai sus pentru a viziona videoclipul acestei lecții)_

# Multi-agent design patterns

De îndată ce începeți să lucrați la un proiect care implică mai mulți agenți, va trebui să luați în considerare modelul de design multi-agent. Cu toate acestea, s-ar putea să nu fie imediat clar când să treceți la multi-agenti și care sunt avantajele.

## Introducere

În această lecție, căutăm să răspundem la următoarele întrebări:

- Care sunt scenariile în care sistemele multi-agent sunt aplicabile?
- Care sunt avantajele utilizării sistemelor multi-agent față de un singur agent care face mai multe sarcini?
- Care sunt blocurile de construcție pentru implementarea modelului de design multi-agent?
- Cum avem vizibilitate asupra modului în care multiplele agenți interacționează între ei?

## Obiective de învățare

După această lecție, ar trebui să fiți capabil să:

- Identificați scenariile în care sistemele multi-agent sunt aplicabile
- Recunoașteți avantajele utilizării sistemelor multi-agent față de un agent singular.
- Înțelegeți blocurile de construcție pentru implementarea modelului de design multi-agent.

Care este imaginea de ansamblu?

*Sistemele multi-agent sunt un model de proiectare care permite mai multor agenți să lucreze împreună pentru a atinge un scop comun*.

Acest model este utilizat pe scară largă în diverse domenii, inclusiv robotică, sisteme autonome și calcul distribuit.

## Scenarii în care se aplică sistemele multi-agent

Deci, în ce scenarii este util să folosiți sisteme multi-agent? Răspunsul este că există multe scenarii în care utilizarea mai multor agenți este benefică, în special în următoarele cazuri:

- **Sarcini de lucru mari**: Sarcinile de lucru mari pot fi împărțite în sarcini mai mici și atribuite unor agenți diferiți, permițând procesarea paralelă și finalizarea mai rapidă. Un exemplu în acest sens este cazul unei sarcini mari de procesare a datelor.
- **Sarcini complexe**: Sarcinile complexe, la fel ca sarcinile de lucru mari, pot fi descompuse în subtasks mai mici și atribuite agenților diferiți, fiecare specializându-se într-un aspect specific al sarcinii. Un exemplu bun în acest sens este cazul vehiculelor autonome în care agenți diferiți gestionează navigația, detectarea obstacolelor și comunicarea cu alte vehicule.
- **Expertiză diversă**: Agenții diferiți pot avea expertize diverse, permițându-le să gestioneze diferite aspecte ale unei sarcini mai eficient decât un singur agent. Pentru acest caz, un exemplu bun este în domeniul sănătății, unde agenții pot gestiona diagnosticul, planurile de tratament și monitorizarea pacienților.

## Avantajele utilizării sistemelor multi-agent față de un agent singular

Un sistem cu un singur agent ar putea funcționa bine pentru sarcini simple, dar pentru sarcini mai complexe, utilizarea mai multor agenți poate oferi mai multe avantaje:

- **Specializare**: Fiecare agent poate fi specializat pentru o sarcină specifică. Lipsa specializării într-un singur agent înseamnă că aveți un agent care poate face totul, dar care s-ar putea confunda atunci când se confruntă cu o sarcină complexă. De exemplu, ar putea ajunge să facă o sarcină pentru care nu este cel mai potrivit.
- **Scalabilitate**: Este mai ușor să scalați sistemele prin adăugarea de agenți în loc să supraîncărcați un singur agent.
- **Toleranță la erori**: Dacă un agent eșuează, alții pot continua să funcționeze, asigurând fiabilitatea sistemului.

Să luăm un exemplu, să rezervăm o călătorie pentru un utilizator. Un sistem cu un singur agent ar trebui să gestioneze toate aspectele procesului de rezervare, de la găsirea zborurilor la rezervarea hotelurilor și a mașinilor de închiriat. Pentru a realiza acest lucru cu un singur agent, agentul ar trebui să aibă unelte pentru gestionarea tuturor acestor sarcini. Acest lucru ar putea conduce la un sistem complex și monolitic, dificil de întreținut și de scalat. Un sistem multi-agent, pe de altă parte, ar putea avea agenți diferiți specializați în găsirea zborurilor, rezervarea hotelurilor și a mașinilor de închiriat. Acest lucru ar face sistemul mai modular, mai ușor de întreținut și scalabil.

Comparați asta cu o agenție de turism condusă ca un mic magazin de familie versus o agenție de turism condusă ca o franciză. Magazinul de familie ar avea un singur agent care gestionează toate aspectele procesului de rezervare a călătoriei, în timp ce franciza ar avea agenți diferiți care gestionează diferite aspecte ale procesului de rezervare.

## Componentele de bază pentru implementarea modelului de design multi-agent

Înainte de a putea implementa modelul de design multi-agent, trebuie să înțelegeți blocurile de construcție care compun modelul.

Să facem acest lucru mai concret uitându-ne din nou la exemplul rezervării unei călătorii pentru un utilizator. În acest caz, blocurile de construcție ar include:

- **Comunicarea dintre agenți**: Agenții pentru găsirea zborurilor, rezervarea hotelurilor și a mașinilor de închiriat trebuie să comunice și să partajeze informații despre preferințele și constrângerile utilizatorului. Trebuie să decideți protocoalele și metodele pentru această comunicare. Ce înseamnă acest lucru concret este că agentul pentru găsirea zborurilor trebuie să comunice cu agentul pentru rezervarea hotelurilor pentru a se asigura că hotelul este rezervat pentru aceleași date ca zborul. Asta înseamnă că agenții trebuie să partajeze informații despre datele de călătorie ale utilizatorului, ceea ce înseamnă că trebuie să decideți *care agenți partajează informații și cum partajează informațiile*.
- **Mecanisme de coordonare**: Agenții trebuie să-și coordoneze acțiunile pentru a se asigura că preferințele și constrângerile utilizatorului sunt respectate. O preferință a utilizatorului ar putea fi că dorește un hotel aproape de aeroport, în timp ce o constrângere ar putea fi că mașinile de închiriat sunt disponibile doar la aeroport. Aceasta înseamnă că agentul pentru rezervarea hotelurilor trebuie să se coordoneze cu agentul pentru rezervarea mașinilor de închiriat pentru a se asigura că preferințele și constrângerile utilizatorului sunt îndeplinite. Aceasta înseamnă că trebuie să decideți *cum se coordonează agenții acțiunile lor*.
- **Arhitectura agenților**: Agenții trebuie să aibă structura internă pentru a lua decizii și a învăța din interacțiunile lor cu utilizatorul. Aceasta înseamnă că agentul pentru găsirea zborurilor trebuie să aibă structura internă pentru a lua decizii despre ce zboruri să recomande utilizatorului. Aceasta înseamnă că trebuie să decideți *cum iau agenții decizii și cum învață din interacțiunile cu utilizatorul*. Exemple de moduri în care un agent învață și se îmbunătățește ar putea fi că agentul pentru găsirea zborurilor ar putea folosi un model de învățare automată pentru a recomanda zboruri utilizatorului pe baza preferințelor anterioare.
- **Vizibilitatea în interacțiunile multi-agent**: Trebuie să aveți vizibilitate asupra modului în care multiplele agenți interacționează între ei. Aceasta înseamnă că trebuie să aveți instrumente și tehnici pentru urmărirea activităților și interacțiunilor agenților. Acest lucru ar putea fi sub forma instrumentelor de logare și monitorizare, instrumentelor de vizualizare și a metricilor de performanță.
- **Patternuri multi-agent**: Există diferite modele pentru implementarea sistemelor multi-agent, cum ar fi arhitecturile centralizate, descentralizate și hibride. Trebuie să decideți modelul care se potrivește cel mai bine cazului dumneavoastră de utilizare.
- **Omul în buclă**: În majoritatea cazurilor, veți avea un om în buclă și trebuie să instruiți agenții când să solicite intervenția umană. Acest lucru ar putea fi sub forma unui utilizator care cere un hotel sau un zbor specific pe care agenții nu l-au recomandat sau solicită confirmarea înainte de a rezerva un zbor sau un hotel.

## Vizibilitatea în interacțiunile multi-agent

Este important să aveți vizibilitate asupra modului în care multiplele agenți interacționează între ei. Această vizibilitate este esențială pentru depanare, optimizare și asigurarea eficacității generale a sistemului. Pentru a realiza acest lucru, trebuie să aveți instrumente și tehnici pentru urmărirea activităților și interacțiunilor agenților. Acest lucru ar putea fi sub forma instrumentelor de logare și monitorizare, instrumentelor de vizualizare și a metricilor de performanță.

De exemplu, în cazul rezervării unei călătorii pentru un utilizator, ați putea avea un tablou de bord care arată starea fiecărui agent, preferințele și constrângerile utilizatorului și interacțiunile dintre agenți. Acest tablou de bord ar putea arăta datele de călătorie ale utilizatorului, zborurile recomandate de agentul de zbor, hotelurile recomandate de agentul de hotel și mașinile de închiriat recomandate de agentul de închirieri auto. Acest lucru v-ar oferi o imagine clară despre cum interacționează agenții între ei și dacă preferințele și constrângerile utilizatorului sunt respectate.

Să analizăm fiecare dintre aceste aspecte mai în detaliu.

- **Instrumente de logare și monitorizare**: Doriți să aveți logare pentru fiecare acțiune întreprinsă de un agent. O înregistrare de log ar putea stoca informații despre agentul care a întreprins acțiunea, acțiunea realizată, momentul în care a fost realizată acțiunea și rezultatul acțiunii. Aceste informații pot fi apoi folosite pentru depanare, optimizare și altele.
- **Instrumente de vizualizare**: Instrumentele de vizualizare vă pot ajuta să vedeți interacțiunile dintre agenți într-un mod mai intuitiv. De exemplu, ați putea avea un grafic care arată fluxul de informații între agenți. Acest lucru v-ar putea ajuta să identificați blocaje, ineficiențe și alte probleme din sistem.
- **Metrici de performanță**: Metricile de performanță vă pot ajuta să urmăriți eficacitatea sistemului multi-agent. De exemplu, ați putea urmări timpul necesar pentru finalizarea unei sarcini, numărul de sarcini finalizate pe unitate de timp și acuratețea recomandărilor făcute de agenți. Aceste informații vă pot ajuta să identificați zone pentru îmbunătățire și să optimizați sistemul.

## Modele multi-agent

Să intrăm în câteva modele concrete pe care le putem folosi pentru a crea aplicații multi-agent. Iată câteva modele interesante care merită luate în considerare:

### Chat de grup

Acest model este util când doriți să creați o aplicație de chat de grup în care mai mulți agenți pot comunica între ei. Cazurile tipice de utilizare pentru acest model includ colaborarea în echipă, suportul pentru clienți și rețelele sociale.

În acest model, fiecare agent reprezintă un utilizator în chatul de grup, iar mesajele sunt schimbate între agenți folosind un protocol de mesagerie. Agenții pot trimite mesaje în chatul de grup, pot primi mesaje din chatul de grup și pot răspunde la mesajele altor agenți.

Acest model poate fi implementat folosind o arhitectură centralizată în care toate mesajele sunt direcționate printr-un server central, sau o arhitectură descentralizată în care mesajele sunt schimbate direct.

![Chat de grup](../../../translated_images/ro/multi-agent-group-chat.ec10f4cde556babd.webp)

### Predare

Acest model este util când doriți să creați o aplicație în care mai mulți agenți pot transmite sarcini între ei.

Cazurile tipice de utilizare pentru acest model includ suportul pentru clienți, managementul sarcinilor și automatizarea fluxului de lucru.

În acest model, fiecare agent reprezintă o sarcină sau un pas într-un flux de lucru, iar agenții pot transmite sarcini altor agenți pe baza unor reguli predefinite.

![Hand off](../../../translated_images/ro/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Filtrare colaborativă

Acest model este util când doriți să creați o aplicație în care mai mulți agenți pot colabora pentru a face recomandări utilizatorilor.

De ce ați dori ca mai mulți agenți să colaboreze? Pentru că fiecare agent poate avea expertiză diferită și poate contribui la procesul de recomandare în moduri diferite.

Să luăm un exemplu în care un utilizator dorește o recomandare despre cea mai bună acțiune în care să investească pe piața bursieră.

- **Expert din industrie**:. Un agent ar putea fi expert într-o industrie specifică.
- **Analiză tehnică**: Un alt agent ar putea fi expert în analiza tehnică.
- **Analiză fundamentală**: și un alt agent ar putea fi expert în analiza fundamentală. Prin colaborare, acești agenți pot oferi o recomandare mai cuprinzătoare utilizatorului.

![Recomandare](../../../translated_images/ro/multi-agent-filtering.d959cb129dc9f608.webp)

## Scenariu: Procesul de rambursare

Luați în considerare un scenariu în care un client încearcă să obțină rambursarea pentru un produs; pot fi implicați destul de mulți agenți în acest proces, dar să-i împărțim între agenți specifici acestui proces și agenți generali care pot fi folosiți în alte procese.

**Agenți specifici procesului de rambursare**:

Următorii sunt câțiva agenți care ar putea fi implicați în procesul de rambursare:

- **Agentul client**: Acest agent reprezintă clientul și este responsabil pentru inițierea procesului de rambursare.
- **Agentul vânzător**: Acest agent reprezintă vânzătorul și este responsabil pentru procesarea rambursării.
- **Agentul de plată**: Acest agent reprezintă procesul de plată și este responsabil pentru rambursarea plății clientului.
- **Agentul de rezolvare**: Acest agent reprezintă procesul de rezolvare și este responsabil pentru soluționarea oricăror probleme care apar în timpul procesului de rambursare.
- **Agentul de conformitate**: Acest agent reprezintă procesul de conformitate și este responsabil pentru asigurarea că procesul de rambursare respectă reglementările și politicile.

**Agenți generali**:

Acești agenți pot fi folosiți de alte părți ale afacerii dvs.

- **Agentul de expediere**: Acest agent reprezintă procesul de expediere și este responsabil pentru trimiterea produsului înapoi către vânzător. Acest agent poate fi folosit atât pentru procesul de rambursare, cât și pentru expedierea generală a unui produs printr-o achiziție, de exemplu.
- **Agentul de feedback**: Acest agent reprezintă procesul de colectare a feedback-ului și este responsabil pentru colectarea feedback-ului de la client. Feedbackul poate fi solicitat în orice moment, nu doar în timpul procesului de rambursare.
- **Agentul de escaladare**: Acest agent reprezintă procesul de escaladare și este responsabil pentru escaladarea problemelor către un nivel superior de suport. Puteți folosi acest tip de agent pentru orice proces în care trebuie să escaladați o problemă.
- **Agentul de notificare**: Acest agent reprezintă procesul de notificare și este responsabil pentru trimiterea notificărilor către client în diverse etape ale procesului de rambursare.
- **Agentul de analiză**: Acest agent reprezintă procesul de analiză și este responsabil pentru analizarea datelor legate de procesul de rambursare.
- **Agentul de audit**: Acest agent reprezintă procesul de audit și este responsabil pentru auditarea procesului de rambursare pentru a se asigura că se desfășoară corect.
- **Agentul de raportare**: Acest agent reprezintă procesul de raportare și este responsabil pentru generarea de rapoarte privind procesul de rambursare.
- **Agentul de cunoștințe**: Acest agent reprezintă procesul de gestionare a cunoștințelor și este responsabil pentru menținerea unei baze de cunoștințe legate de procesul de rambursare. Acest agent ar putea fi informat atât despre rambursări, cât și despre alte părți ale afacerii dvs.
- **Agentul de securitate**: Acest agent reprezintă procesul de securitate și este responsabil pentru asigurarea securității procesului de rambursare.
- **Agentul de calitate**: Acest agent reprezintă procesul de calitate și este responsabil pentru asigurarea calității procesului de rambursare.

Au fost enumerați destul de mulți agenți anterior, atât pentru procesul specific de rambursare, cât și pentru agenții generali care pot fi folosiți în alte părți ale afacerii dvs. Sperăm că acest lucru vă oferă o idee despre cum puteți decide ce agenți să utilizați în sistemul dvs. multi-agent.

## Temă

Proiectați un sistem multi-agent pentru un proces de suport pentru clienți. Identificați agenții implicați în proces, rolurile și responsabilitățile lor și modul în care interacționează între ei. Luați în considerare atât agenții specifici procesului de suport pentru clienți, cât și agenții generali care pot fi folosiți în alte părți ale afacerii dvs.
> Reflectează înainte de a citi soluția de mai jos; s-ar putea să ai nevoie de mai mulți agenți decât crezi.
>
> TIP: Gândește-te la diferitele etape ale procesului de suport pentru clienți și ia în considerare, de asemenea, agenții necesari pentru orice sistem.

## Soluție

[Soluție](./solution/solution.md)

## Verificări ale cunoștințelor

Întrebare: Când ar trebui să iei în considerare utilizarea mai multor agenți?

- [ ] A1: Când ai o încărcare de lucru mică și o sarcină simplă.
- [ ] A2: Când ai o încărcare de lucru mare
- [ ] A3: Când ai o sarcină simplă.

[Chestionar soluție](./solution/solution-quiz.md)

## Rezumat

În această lecție, am analizat modelul de proiectare multi-agent, incluzând scenariile în care se aplică agenții multipli, avantajele folosirii agenților multipli față de un agent singular, elementele de bază pentru implementarea modelului de proiectare multi-agent și modul de a avea vizibilitate asupra modului în care agenții multipli interacționează între ei.

### Ai mai multe întrebări despre modelul de proiectare multi-agent?

Alătură-te [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la ore de consultanță și a primi răspunsuri la întrebările tale despre agenții AI.

## Resurse suplimentare

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Tipare de proiectare AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Tipare de proiectare agentice</a>


## Lecția anterioară

[Design pentru planificare](../07-planning-design/README.md)

## Următoarea lecție

[Metacogniție în agenții AI](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Declinare de responsabilitate:
Acest document a fost tradus folosind serviciul de traducere AI Co-op Translator (https://github.com/Azure/co-op-translator). Deși ne străduim pentru acuratețe, vă rugăm să rețineți că traducerile automate pot conține erori sau inexactități. Documentul original, în limba sa nativă, trebuie considerat sursa autorizată. Pentru informații critice, se recomandă o traducere profesională realizată de un traducător uman. Nu ne asumăm responsabilitatea pentru niciun fel de neînțelegeri sau interpretări greșite care rezultă din utilizarea acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->