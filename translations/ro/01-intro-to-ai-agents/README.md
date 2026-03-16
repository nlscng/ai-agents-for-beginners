[![Intro to AI Agents](../../../translated_images/ro/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Faceți clic pe imaginea de mai sus pentru a viziona videoclipul acestei lecții)_


# Introducere în Agenții AI și Cazurile de Utilizare ale Agenților

Bine ați venit la cursul „Agenți AI pentru Începători”! Acest curs oferă cunoștințe fundamentale și exemple aplicate pentru construirea Agenților AI.

Alăturați-vă <a href="https://discord.gg/kzRShWzttr" target="_blank">Comunității Discord Azure AI</a> pentru a întâlni alți cursanți și constructori de Agenți AI și pentru a pune orice întrebări aveți despre acest curs.

Pentru a începe acest curs, începem prin a înțelege mai bine ce sunt Agenții AI și cum îi putem folosi în aplicațiile și fluxurile de lucru pe care le construim.

## Introducere

Această lecție acoperă:

- Ce sunt Agenții AI și care sunt diferitele tipuri de agenți?
- Care cazuri de utilizare sunt cele mai potrivite pentru Agenții AI și cum ne pot ajuta?
- Care sunt unele dintre elementele de bază în proiectarea soluțiilor agentice?

## Obiective de Învățare
După finalizarea acestei lecții, ar trebui să puteți:

- Înțelege conceptele de Agenți AI și cum diferă de alte soluții AI.
- Aplica Agenții AI în mod eficient.
- Proiecta soluții agentice productiv pentru utilizatori și clienți.

## Definirea Agenților AI și Tipurile de Agenți AI

### Ce sunt Agenții AI?

Agenții AI sunt **sisteme** care permit **Modelelor Mari de Limbaj (LLM-uri)** să **efectueze acțiuni** prin extinderea capabilităților lor, oferindu-le LLM-urilor **acces la instrumente** și **cunoștințe**.

Să descompunem această definiție în părți mai mici:

- **Sistem** - Este important să ne gândim la agenți nu doar ca la un singur component, ci ca la un sistem alcătuit din mai multe componente. La nivel de bază, componentele unui Agent AI sunt:
  - **Mediu** - Spațiul definit în care operează Agentul AI. De exemplu, dacă avem un agent AI pentru rezervări de călătorie, mediul ar putea fi sistemul de rezervări de călătorie pe care agentul AI îl folosește pentru a îndeplini sarcini.
  - **Senzori** - Mediile au informații și oferă feedback. Agenții AI folosesc senzori pentru a colecta și interpreta aceste informații despre starea curentă a mediului. În exemplul Agentului de Rezervări de Călătorie, sistemul de rezervări poate oferi informații precum disponibilitatea hotelurilor sau prețurile zborurilor.
  - **Actuatori** - Odată ce Agentul AI primește starea curentă a mediului, pentru sarcina curentă agentul determină ce acțiune să efectueze pentru a schimba mediul. Pentru agentul de rezervări de călătorie, aceasta ar putea fi rezervarea unei camere disponibile pentru utilizator.

![What Are AI Agents?](../../../translated_images/ro/what-are-ai-agents.1ec8c4d548af601a.webp)

**Modele Mari de Limbaj** - Conceptul de agenți a existat înainte de crearea LLM-urilor. Avantajul construirii Agenților AI cu LLM-uri este capacitatea lor de a interpreta limbajul uman și datele. Această abilitate le permite LLM-urilor să interpreteze informațiile mediului și să definească un plan pentru a schimba mediul.

**Efectuarea de Acțiuni** - În afara sistemelor de Agenți AI, LLM-urile sunt limitate la situații în care acțiunea este generarea de conținut sau informații bazate pe solicitarea unui utilizator. În cadrul sistemelor de Agenți AI, LLM-urile pot îndeplini sarcini interpretând cererea utilizatorului și folosind instrumente disponibile în mediul lor.

**Acces la Instrumente** - Ce instrumente are acces LLM-ul este definit de 1) mediul în care operează și 2) dezvoltatorul Agentului AI. Pentru exemplul agentului nostru de călătorie, instrumentele agentului sunt limitate de operațiunile disponibile în sistemul de rezervări și/sau dezvoltatorul poate limita accesul agentului la instrumente pentru zboruri.

**Memorie + Cunoștințe** - Memoria poate fi pe termen scurt, în contextul conversației dintre utilizator și agent. Pe termen lung, în afara informațiilor furnizate de mediu, Agenții AI pot de asemenea să recupereze cunoștințe din alte sisteme, servicii, instrumente și chiar alți agenți. În exemplul agentului de călătorie, aceste cunoștințe pot fi informații despre preferințele de călătorie ale utilizatorului stocate într-o bază de date a clienților.

### Diferitele tipuri de agenți

Acum că avem o definiție generală a Agenților AI, să analizăm câteva tipuri specifice de agenți și cum ar fi aplicați la un agent AI pentru rezervări de călătorie.

| **Tip Agent**                 | **Descriere**                                                                                                                       | **Exemplu**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Agenți Reflex Simpli**      | Execută acțiuni imediate pe baza unor reguli predefinite.                                                                             | Agentul de călătorie interpretează contextul unui email și redirecționează reclamațiile de călătorie către serviciul clienți.                                                                                                  |
| **Agenți Reflex Bazati pe Model** | Execută acțiuni pe baza unui model al lumii și a schimbărilor acestuia.                                                        | Agentul de călătorie prioritizează rute cu schimbări semnificative de preț bazate pe accesul la date istorice de prețuri.                                                                                                      |
| **Agenți Bazati pe Scop**     | Creează planuri pentru a atinge scopuri specifice interpretând scopul și determinând acțiunile pentru a-l atinge.                   | Agentul de călătorie rezervă o călătorie determinând aranjamentele necesare de călătorie (mașină, transport public, zboruri) de la locația curentă la destinație.                                                               |
| **Agenți Bazati pe Utilitate**| Ia în considerare preferințele și evaluează compromisurile numeric pentru a determina cum să atingă scopurile.                      | Agentul de călătorie maximizează utilitatea prin cântărirea confortului versus cost în rezervarea călătoriei.                                                                                                                  |
| **Agenți Învățători**         | Se îmbunătățesc în timp răspunzând la feedback și ajustând acțiunile în consecință.                                               | Agentul de călătorie se îmbunătățește folosind feedback-ul clienților din sondajele post-călătorie pentru a face ajustări la rezervările viitoare.                                                                             |
| **Agenți ierarhici**          | Au mai mulți agenți într-un sistem pe niveluri, agenții de nivel superior împart sarcinile în subtask-uri pentru agenții de nivel inferior. | Agentul de călătorie anulează o călătorie împărțind sarcina în subtask-uri (de exemplu, anularea rezervărilor specifice) și membrii agenți de nivel inferior le îndeplinesc, raportând înapoi la agentul de nivel superior.          |
| **Sisteme Multi-Agent (MAS)** | Agenții îndeplinesc sarcinile independent, fie cooperativ, fie competitiv.                                                          | Cooperativ: Mai mulți agenți rezervă servicii specifice de călătorie, cum ar fi hoteluri, zboruri și divertisment. Competitiv: Mai mulți agenți administrează și concurează pentru un calendar de rezervări hotelieră partajat.     |

## Când să folosești Agenți AI

În secțiunea anterioară, am folosit cazul de utilizare Agent de Călătorie pentru a explica cum pot fi utilizați diferitele tipuri de agenți în diverse scenarii de rezervare de călătorie. Vom continua să folosim această aplicație pe tot parcursul cursului.

Să analizăm tipurile de cazuri de utilizare pentru care Agenții AI sunt cei mai buni:

![When to use AI Agents?](../../../translated_images/ro/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Probleme Deschise** - permit LLM-ului să determine pașii necesari pentru a finaliza o sarcină deoarece nu poate fi întotdeauna codificat strict într-un flux de lucru.
- **Procese cu Mai mulți Pași** - sarcini care necesită un nivel de complexitate în care Agentul AI trebuie să utilizeze instrumente sau informații pe mai multe întoarceri în loc de o singură preluare.  
- **Îmbunătățire în Timp** - sarcini în care agentul poate să se îmbunătățească în timp prin primirea de feedback din mediul său sau de la utilizatori pentru a furniza o utilitate mai bună.

Acoperim mai multe considerații legate de utilizarea Agenților AI în lecția Construind Agenți AI de Încredere.

## Bazele Soluțiilor Agentice

### Dezvoltarea Agenților

Primul pas în proiectarea unui sistem de Agenți AI este definirea instrumentelor, acțiunilor și comportamentelor. În acest curs, ne concentrăm pe utilizarea **Azure AI Agent Service** pentru a defini agenții noștri. Oferă caracteristici precum:

- Selecția modelelor deschise precum OpenAI, Mistral și Llama
- Utilizarea datelor licențiate prin furnizori precum Tripadvisor
- Utilizarea instrumentelor standardizate OpenAPI 3.0

### Modele Agentice

Comunicarea cu LLM-urile se face prin prompturi. Având natura semi-autonomă a Agenților AI, nu este întotdeauna posibil sau necesar să reapelăm manual LLM-ul după o schimbare în mediu. Folosim **Modele Agentice** care ne permit să promptăm LLM-ul pe mai mulți pași într-un mod mai scalabil.

Acest curs este împărțit în unele dintre modelele agentice populare actuale.

### Framework-uri Agentice

Framework-urile agentice permit dezvoltatorilor să implementeze modelele agentice prin cod. Aceste framework-uri oferă șabloane, pluginuri și instrumente pentru o colaborare mai bună între Agenții AI. Aceste beneficii furnizează capacități pentru o mai bună observabilitate și depanare a sistemelor de Agenți AI.

În acest curs, vom explora framework-ul AutoGen bazat pe cercetare și framework-ul Agent gata pentru producție de la Semantic Kernel.

## Coduri Exemplu

- Python: [Agent Framework](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/01-dotnet-agent-framework.md)

## Aveți Mai Multe Întrebări despre Agenții AI?

Alăturați-vă [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) pentru a întâlni alți cursanți, a participa la orele de consultanță și a primi răspunsuri la întrebările despre Agenții AI.

## Lecția Anterioară

[Configurare Curs](../00-course-setup/README.md)

## Lecția Următoare

[Explorarea Framework-urilor Agentice](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:  
Acest document a fost tradus folosind serviciul de traducere AI [Co-op Translator](https://github.com/Azure/co-op-translator). Deși ne străduim să oferim o traducere cât mai exactă, vă rugăm să țineți cont că traducerile automate pot conține erori sau inexactități. Documentul original în limba sa nativă trebuie considerat sursa autorizată. Pentru informații critice, se recomandă traducerea profesională realizată de un specialist. Nu ne asumăm responsabilitatea pentru eventualele neînțelegeri sau interpretări greșite cauzate de utilizarea acestei traduceri.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->