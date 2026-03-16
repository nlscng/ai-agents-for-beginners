# Minne för AI‑agenter 
[![Agentminne](../../../translated_images/sv/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

När man diskuterar de unika fördelarna med att skapa AI‑agenter, tas två saker upp främst: möjligheten att anropa verktyg för att slutföra uppgifter och möjligheten att förbättras över tid. Minne ligger till grund för att skapa självförbättrande agenter som kan skapa bättre upplevelser för våra användare.

I den här lektionen kommer vi att titta på vad minne är för AI‑agenter och hur vi kan hantera det och använda det till fördel för våra applikationer.

## Introduction

Denna lektion täcker:

• **Understanding AI Agent Memory**: Vad minne är och varför det är viktigt för agenter.

• **Implementing and Storing Memory**: Praktiska metoder för att lägga till minneskapabiliteter i dina AI‑agenter, med fokus på korttids‑ och långtidsminne.

• **Making AI Agents Self‑Improving**: Hur minne möjliggör för agenter att lära av tidigare interaktioner och förbättras över tid.

## Available Implementations

Denna lektion inkluderar två omfattande notebook‑handledningar:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implements memory using Mem0 and Azure AI Search with Semantic Kernel framework

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implements structured memory using Cognee, automatically building knowledge graph backed by embeddings, visualizing graph, and intelligent retrieval

## Learning Goals

Efter att ha slutfört denna lektion kommer du att veta hur du kan:

• **Differentiate between various types of AI agent memory**, inklusive arbetsminne, korttidsminne och långtidsminne, samt specialiserade former som persona‑ och episodiskt minne.

• **Implement and manage short-term and long-term memory for AI agents** med hjälp av Semantic Kernel‑ramverket, och utnyttja verktyg som Mem0, Cognee, Whiteboard memory och integrera med Azure AI Search.

• **Understand the principles behind self-improving AI agents** och hur robusta system för minneshantering bidrar till kontinuerligt lärande och anpassning.

## Understanding AI Agent Memory

I grunden avser **minne för AI‑agenter de mekanismer som tillåter dem att behålla och återkalla information**. Denna information kan vara specifika detaljer om en konversation, användarpreferenser, tidigare handlingar eller till och med inlärda mönster.

Utan minne är AI‑applikationer ofta stateless, vilket betyder att varje interaktion börjar från början. Detta leder till en repetitiv och frustrerande användarupplevelse där agenten "glömmer" tidigare kontext eller preferenser.

### Why is Memory Important?

en agents intelligens är djupt kopplad till dess förmåga att återkalla och använda tidigare information. Minne gör att agenter kan vara:

• **Reflective**: Lära sig av tidigare handlingar och utfall.

• **Interactive**: Bibehålla kontext över en pågående konversation.

• **Proactive and Reactive**: Förutse behov eller reagera lämpligt baserat på historisk data.

• **Autonomous**: Operera mer självständigt genom att dra nytta av lagrad kunskap.

Målet med att implementera minne är att göra agenter mer **pålitliga och kapabla**.

### Types of Memory

#### Working Memory

Tänk på detta som ett skisspapper en agent använder under en enskild, pågående uppgift eller tankeprocess. Det håller omedelbar information som behövs för att beräkna nästa steg.

För AI‑agenter fångar arbetsminne ofta den mest relevanta informationen från en konversation, även om hela chathistoriken är lång eller trunkerad. Det fokuserar på att extrahera nyckelelement som krav, förslag, beslut och åtgärder.

**Working Memory Example**

I en resebokningsagent kan arbetsminnet fånga användarens aktuella förfrågan, till exempel "Jag vill boka en resa till Paris". Detta specifika krav hålls i agentens omedelbara kontext för att vägleda den pågående interaktionen.

#### Short Term Memory

Denna typ av minne behåller information under en enskild konversation eller session. Det är kontexten för den aktuella chatten, vilket gör att agenten kan hänvisa tillbaka till tidigare turer i dialogen.

**Short Term Memory Example**

Om en användare frågar, "Hur mycket skulle en flygning till Paris kosta?" och sedan följer upp med "Vad sägs om boende där?", säkerställer korttidsminnet att agenten vet att "där" avser "Paris" inom samma konversation.

#### Long Term Memory

Detta är information som består över flera konversationer eller sessioner. Det gör att agenter kan komma ihåg användarpreferenser, historiska interaktioner eller allmän kunskap över längre perioder. Detta är viktigt för personalisering.

**Long Term Memory Example**

Ett långtidsminne kan lagra att "Ben gillar skidåkning och friluftsliv, föredrar kaffe med utsikt över bergen, och vill undvika avancerade pisterna på grund av en tidigare skada". Denna information, inhämtad från tidigare interaktioner, påverkar rekommendationer i framtida reseplaneringssessioner och gör dem mycket mer personliga.

#### Persona Memory

Denna specialiserade minnestyp hjälper en agent att utveckla en konsekvent "personlighet" eller "persona". Den gör att agenten kan komma ihåg detaljer om sig själv eller sin avsedda roll, vilket gör interaktionerna mer flytande och fokuserade.

**Persona Memory Example**
Om reseagenten är designad för att vara en "expert på skidplanering", kan personaminne förstärka denna roll och påverka dess svar så att de stämmer överens med tonen och kunskapen hos en expert.

#### Workflow/Episodic Memory

Detta minne lagrar sekvensen av steg en agent tar under en komplex uppgift, inklusive framgångar och misslyckanden. Det liknar att minnas specifika "episoder" eller tidigare erfarenheter för att lära av dem.

**Episodic Memory Example**

Om agenten försökte boka en specifik flygning men det misslyckades på grund av att den inte var tillgänglig, kan episodiskt minne registrera detta misslyckande, vilket gör att agenten kan försöka alternativa flyg eller informera användaren om problemet på ett mer informerat sätt vid ett efterföljande försök.

#### Entity Memory

Detta innebär att extrahera och komma ihåg specifika entiteter (som personer, platser eller saker) och händelser från konversationer. Det gör att agenten kan bygga en strukturerad förståelse av nyckelelement som diskuterats.

**Entity Memory Example**

Från en konversation om en tidigare resa kan agenten extrahera "Paris", "Eiffeltornet" och "middag på Le Chat Noir‑restaurangen" som entiteter. Vid en framtida interaktion kan agenten komma ihåg "Le Chat Noir" och erbjuda att boka ett nytt bord där.

#### Structured RAG (Retrieval Augmented Generation)

Medan RAG är en bredare teknik, framhävs "Structured RAG" som en kraftfull minnesteknik. Den extraherar täta, strukturerade uppgifter från olika källor (konversationer, e‑post, bilder) och använder dem för att förbättra precision, återkallelse och hastighet i svaren. Till skillnad från klassisk RAG som enbart litar på semantisk likhet, arbetar Structured RAG med informationens inneboende struktur.

**Structured RAG Example**

Istället för att bara matcha nyckelord kan Structured RAG parsa flyguppgifter (destination, datum, tid, flygbolag) från ett e‑postmeddelande och lagra dem på ett strukturerat sätt. Detta möjliggör precisa frågor som "Vilket flyg bokade jag till Paris på tisdag?"

## Implementing and Storing Memory

Att implementera minne för AI‑agenter innebär en systematisk process för **minneshantering**, som inkluderar att generera, lagra, hämta, integrera, uppdatera och till och med "glömma" (eller radera) information. Hämtning är en särskilt avgörande aspekt.

### Specialized Memory Tools

#### Mem0

Ett sätt att lagra och hantera agentminne är att använda specialiserade verktyg som Mem0. Mem0 fungerar som ett persistenslager för minne, vilket tillåter agenter att återkalla relevanta interaktioner, lagra användarpreferenser och faktuell kontext, och lära av framgångar och misslyckanden över tid. Idén här är att stateless‑agenter blir stateful.

Det fungerar genom en **tvåfasig minnespipeline: extraktion och uppdatering**. Först skickas meddelanden som läggs till i en agents tråd till Mem0‑tjänsten, som använder en Large Language Model (LLM) för att sammanfatta konversationshistoriken och extrahera nya minnen. Därefter avgör en LLM‑driven uppdateringsfas om dessa minnen ska läggas till, modifieras eller raderas, och lagrar dem i en hybrid datalagring som kan inkludera vektor-, graf‑ och nyckel‑värde‑databaser. Detta system stöder även olika minnestyper och kan inkorporera grafminne för att hantera relationer mellan entiteter.

#### Cognee

Ett annat kraftfullt tillvägagångssätt är att använda **Cognee**, ett open‑source semantiskt minne för AI‑agenter som transformerar strukturerad och ostrukturerad data till sökbara kunskapsgrafer backade av embeddings. Cognee erbjuder en **dual‑store‑arkitektur** som kombinerar vektorsökning för likhet med grafrelationer, vilket gör det möjligt för agenter att förstå inte bara vad som är likt, utan hur koncept relaterar till varandra.

Det utmärker sig i **hybrid‑hämtning** som blandar vektorsimiläritet, grafstruktur och LLM‑resonemang – från rå chunk‑uppslagning till grafmedveten fråge‑svar. Systemet upprätthåller ett **levande minne** som utvecklas och växer samtidigt som det förblir sökbart som en sammanlänkad graf, och stöder både korttids sessionskontext och långtids beständigt minne.

Cognee‑notebook‑handledningen ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) visar hur man bygger detta enhetliga minneslager, med praktiska exempel på att ta in olika datakällor, visualisera kunskapsgrafen och fråga med olika sökstrategier anpassade till specifika agentbehov.

### Storing Memory with RAG

Utöver specialiserade minnesverktyg som mem0 kan du utnyttja robusta söktjänster som **Azure AI Search som backend för att lagra och hämta minnen**, särskilt för strukturerad RAG.

Detta gör att du kan förankra agentens svar i din egen data, vilket säkerställer mer relevanta och korrekta svar. Azure AI Search kan användas för att lagra användarspecifika reseminnen, produktkataloger eller annan domänspecifik kunskap.

Azure AI Search stöder kapaciteter som **Structured RAG**, vilket excellerar på att extrahera och hämta täta, strukturerade uppgifter från stora dataset som konversationshistorik, e‑post eller till och med bilder. Detta ger "övermänsklig precision och återkallelse" jämfört med traditionella text‑chunking‑ och embedding‑metoder.

## Making AI Agents Self-Improve

Ett vanligt mönster för självförbättrande agenter innebär att introducera en **"kunskapsagent"**. Denna separata agent observerar huvudkonversationen mellan användaren och den primära agenten. Dess roll är att:

1. **Identify valuable information**: Avgöra om någon del av konversationen är värd att spara som generell kunskap eller som en specifik användarpreferens.

2. **Extract and summarize**: Destillera den väsentliga lärdomen eller preferensen från konversationen.

3. **Store in a knowledge base**: Spara denna extraherade information, ofta i en vektorbas, så att den kan hämtas senare.

4. **Augment future queries**: När användaren initierar en ny förfrågan hämtar kunskapsagenten relevant sparad information och bifogar den till användarens prompt, vilket ger avgörande kontext till den primära agenten (liknar RAG).

### Optimizations for Memory

• **Latency Management**: För att undvika att sakta ner användarinteraktioner kan en billigare, snabbare modell användas initialt för att snabbt kontrollera om information är värd att lagra eller hämta, och endast anropa den mer komplexa extraktions-/hämtprocessen när det behövs.

• **Knowledge Base Maintenance**: För en växande kunskapsbas kan mindre frekvent använd information flyttas till "cold storage" för att hantera kostnader.

## Got More Questions About Agent Memory?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet with other learners, attend office hours and get your AI Agents questions answered.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Ansvarsfriskrivning:
Detta dokument har översatts med hjälp av AI-översättningstjänsten [Co-op Translator](https://github.com/Azure/co-op-translator). Även om vi strävar efter noggrannhet bör du vara medveten om att automatiska översättningar kan innehålla fel eller brister. Det ursprungliga dokumentet i sitt originalspråk ska betraktas som den auktoritativa källan. För kritisk information rekommenderas professionell mänsklig översättning. Vi ansvarar inte för några missförstånd eller feltolkningar som uppstår till följd av användningen av denna översättning.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->