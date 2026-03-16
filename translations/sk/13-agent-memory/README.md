# Pamäť pre AI agentov 
[![Pamäť agenta](../../../translated_images/sk/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Keď sa diskutuje o jedinečných výhodách vytvárania AI agentov, väčšinou sa hovoria dve veci: schopnosť volať nástroje na dokončenie úloh a schopnosť zlepšovať sa v čase. Pamäť je základom vytvárania samoučiacich sa agentov, ktorí dokážu vytvárať lepšie skúsenosti pre našich používateľov.

V tejto lekcii sa pozrieme na to, čo je pamäť pre AI agentov a ako ju môžeme spravovať a využívať v prospech našich aplikácií.

## Úvod

Táto lekcia pokryje:

• **Pochopenie pamäte AI agenta**: Čo je pamäť a prečo je pre agentov podstatná.

• **Implementácia a ukladanie pamäte**: Praktické metódy pridania schopností pamäte vašim AI agentom so zameraním na krátkodobú a dlhodobú pamäť.

• **Vytvorenie samoučiacich sa AI agentov**: Ako pamäť umožňuje agentom učiť sa z minulých interakcií a zlepšovať sa v priebehu času.

## Dostupné implementácie

Táto lekcia obsahuje dva komplexné notebookové tutoriály:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementuje pamäť pomocou Mem0 a Azure AI Search so Semantic Kernel frameworkom

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementuje štruktúrovanú pamäť pomocou Cognee, automaticky buduje graf znalostí založený na embeddingoch, vizualizuje graf a zabezpečuje inteligentné vyhľadávanie

## Ciele učenia

Po dokončení tejto lekcie budete vedieť:

• **Rozlíšiť medzi rôznymi typmi pamäte AI agenta**, vrátane pracovnej, krátkodobej a dlhodobej pamäte, ako aj špecializovaných foriem ako persona a episodická pamäť.

• **Implementovať a spravovať krátkodobú a dlhodobú pamäť pre AI agentov** pomocou Semantic Kernel frameworku, s využitím nástrojov ako Mem0, Cognee, Whiteboard memory a integráciou s Azure AI Search.

• **Pochopiť princípy fungovania samoučiacich sa AI agentov** a ako robustné systémy správy pamäte prispievajú k neustálemu učeniu a adaptácii.

## Pochopenie pamäte AI agenta

V jadre, **pamäť pre AI agentov odkazuje na mechanizmy, ktoré im umožňujú uchovávať a vyvolávať informácie**. Tieto informácie môžu byť konkrétne detaily o konverzácii, preferencie používateľa, minulé akcie alebo dokonca naučené vzory.

Bez pamäti sú AI aplikácie často bezstavové, čo znamená, že každá interakcia začína od nuly. To vedie k opakujúcemu sa a frustrujúcemu používateľskému zážitku, kde agent „zabúda“ predchádzajúci kontext alebo preferencie.

### Prečo je pamäť dôležitá?

Inteligencia agenta je hlboko spätá s jeho schopnosťou vyvolávať a využívať minulé informácie. Pamäť umožňuje agentom byť:

• **Reflexívni**: Učiť sa z minulých akcií a výsledkov.

• **Interaktívni**: Udržiavať kontext počas prebiehajúcej konverzácie.

• **Proaktívni a reaktívni**: Predvídať potreby alebo reagovať primerane na základe historických dát.

• **Autonómni**: Pôsobiť nezávislejšie čerpaním zo uložených poznatkov.

Cieľom implementácie pamäte je urobiť agentov viac **spoľahlivými a schopnými**.

### Typy pamäte

#### Pracovná pamäť

Predstavte si to ako kus papieru, ktorý agent používa počas jedinej, prebiehajúcej úlohy alebo myšlienkového procesu. Uchováva okamžité informácie potrebné na výpočet ďalšieho kroku.

Pre AI agentov pracovná pamäť často zachytáva najrelevantnejšie informácie z konverzácie, aj keď je celý chat dlhý alebo skrátený. Zameriava sa na extrakciu kľúčových prvkov ako požiadavky, návrhy, rozhodnutia a akcie.

**Príklad pracovnej pamäte**

V cestovnej rezervačnej službe by pracovná pamäť mohla zachytiť aktuálnu požiadavku používateľa, napríklad „Chcem si rezervovať výlet do Paríža“. Táto konkrétna požiadavka sa drží v bezprostrednom kontexte agenta, aby usmernila aktuálnu interakciu.

#### Krátkodobá pamäť

Tento typ pamäte uchováva informácie počas trvania jednej konverzácie alebo relácie. Je to kontext aktuálneho chatu, ktorý agentovi umožňuje odvolať sa na predchádzajúce výmeny v dialógu.

**Príklad krátkodobej pamäte**

Ak sa používateľ spýta: „Koľko by stál let do Paríža?“ a následne pokračuje: „A čo ubytovanie tam?“, krátkodobá pamäť zabezpečí, že agent vie, že „tam“ odkazuje na „Paríž“ v rámci tej istej konverzácie.

#### Dlhodobá pamäť

Ide o informácie, ktoré pretrvávajú naprieč viacerými konverzáciami alebo reláciami. Umožňuje agentom zapamätať si používateľské preferencie, historické interakcie alebo všeobecné znalosti počas dlhšieho obdobia. To je dôležité pre personalizáciu.

**Príklad dlhodobej pamäte**

Dlhodobá pamäť môže uložiť, že „Ben má rád lyžovanie a aktivity vonku, má rád kávu s výhľadom na hory a chce sa vyhnúť pokročilým zjazdovkám kvôli minulému zraneniu“. Táto informácia, získaná z predchádzajúcich interakcií, ovplyvňuje odporúčania pri budúcom plánovaní dovolenky, čím sú výrazne personalizované.

#### Persona pamäť

Tento špecializovaný typ pamäte pomáha agentovi rozvinúť konzistentnú „osobnosť“ alebo „perzónu“. Umožňuje agentovi pamätať si detaily o sebe alebo o svojej zamýšľanej roli, čím robí interakcie plynulejšími a zameranejšími.

**Príklad persona pamäte**
Ak je cestovný agent navrhnutý ako „expert na plánovanie lyžovačiek“, persona pamäť môže posilniť túto rolu a ovplyvniť jeho odpovede tak, aby zodpovedali tónu a znalostiam odborníka.

#### Workflow/Episodická pamäť

Táto pamäť uchováva sekvenciu krokov, ktoré agent podnikol počas komplexnej úlohy, vrátane úspechov a zlyhaní. Je to ako zapamätať si konkrétne „epizódy“ alebo minulé skúsenosti, aby sa z nich dalo poučiť.

**Príklad episodickej pamäte**

Ak sa agent pokúsil rezervovať konkrétny let, ale zlyhalo to kvôli nedostupnosti, episodická pamäť by mohla zaznamenať toto zlyhanie, čo umožní agentovi skúsiť alternatívne lety alebo informovať používateľa o probléme pri nasledujúcom pokuse s lepším kontextom.

#### Entity pamäť

To zahŕňa extrahovanie a zapamätanie si konkrétnych entít (ako ľudia, miesta alebo veci) a udalostí z konverzácií. Umožňuje agentovi vybudovať štruktúrované porozumenie kľúčových prvkov diskutovaných tém.

**Príklad entity pamäte**

Z konverzácie o minulom výlete môže agent extrahovať „Paríž“, „Eiffelova veža“ a „večera v reštaurácii Le Chat Noir“ ako entity. Pri budúcej interakcii by si agent mohol spomenúť na „Le Chat Noir“ a ponúknuť možnosť urobiť novú rezerváciu tam.

#### Štruktúrované RAG (Retrieval Augmented Generation)

Zatiaľ čo RAG je širšia technika, „Štruktúrované RAG“ je vyzdvihnuté ako silná technológia pamäte. Extrahuje husté, štruktúrované informácie z rôznych zdrojov (konverzácie, e-maily, obrázky) a používa ich na zvýšenie presnosti, vyhľadávania a rýchlosti odpovedí. Na rozdiel od klasického RAG, ktorý sa spolieha len na sémantickú podobnosť, Štruktúrované RAG pracuje s inherentnou štruktúrou informácií.

**Príklad štruktúrovaného RAG**

Namiesto len zhodovania kľúčových slov by Štruktúrované RAG mohlo parsovať detaily letu (destinácia, dátum, čas, letecká spoločnosť) z e-mailu a uložiť ich štruktúrovaným spôsobom. To umožňuje presné dotazy ako „Aký let som si rezervoval do Paríža v utorok?“

## Implementácia a ukladanie pamäte

Implementácia pamäte pre AI agentov zahŕňa systematický proces **správy pamäte**, ktorý zahŕňa generovanie, ukladanie, vyhľadávanie, integráciu, aktualizáciu a dokonca aj „zabúdanie“ (alebo mazanie) informácií. Vyhľadávanie je obzvlášť kľúčový aspekt.

### Špecializované nástroje pre pamäť

#### Mem0

Jedným zo spôsobov, ako ukladať a spravovať pamäť agenta, je použitie špecializovaných nástrojov ako Mem0. Mem0 funguje ako perzistentná vrstva pamäti, ktorá agentom umožňuje vyvolať relevantné interakcie, ukladať používateľské preferencie a faktický kontext a učiť sa z úspechov a zlyhaní v priebehu času. Myšlienka je, že bezstavoví agenti sa premienia na stavových.

Funguje cez **dvojfázový pipeline pamäti: extrakcia a aktualizácia**. Najprv sú správy pridané do vlákna agenta odoslané do služby Mem0, ktorá používa veľký jazykový model (LLM) na zhrnutie histórie konverzácie a extrakciu nových spomienok. Následne fáza aktualizácie riadená LLM určí, či tieto spomienky pridať, upraviť alebo vymazať, pričom ich uloží do hybridnej dátovej úložiska, ktoré môže zahŕňať vektorové, grafové a kľúč-hodnota databázy. Tento systém tiež podporuje rôzne typy pamäti a môže začleniť grafovú pamäť na správu vzťahov medzi entitami.

#### Cognee

Ďalším silným prístupom je použitie **Cognee**, open-source sémantickej pamäte pre AI agentov, ktorá transformuje štruktúrované aj neštruktúrované dáta do dotazovateľných grafov znalostí podporených embeddingami. Cognee poskytuje **architektúru s dual-store**, ktorá kombinuje vektorové vyhľadávanie podľa podobnosti s grafovými vzťahmi, čo agentom umožňuje rozumieť nielen tomu, ktoré informácie sú podobné, ale aj ako sú koncepty navzájom prepojené.

Vyniká v **hybridnom vyhľadávaní**, ktoré spája vektorovú podobnosť, štruktúru grafu a LLM uvažovanie - od surového vyhľadania kúskov až po otázky s ohľadom na graf. Systém udržiava **živú pamäť**, ktorá sa vyvíja a rastie a zároveň zostáva dotazovateľná ako jeden prepojený graf, podporujúc krátkodobý kontext relácie aj dlhodobú perzistentnú pamäť.

Notebookový tutoriál Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonštruje budovanie tejto zjednotenej vrstvy pamäti s praktickými príkladmi ingestovania rôznorodých zdrojov dát, vizualizácie grafu znalostí a dotazovania s rôznymi stratégiami vyhľadávania prispôsobenými konkrétnym potrebám agenta.

### Ukladanie pamäte pomocou RAG

Okrem špecializovaných nástrojov pre pamäť ako Mem0 , môžete využiť robustné vyhľadávacie služby ako **Azure AI Search ako backend na ukladanie a vyhľadávanie spomienok**, najmä pre štruktúrované RAG.

To vám umožní zakotviť odpovede agenta vo vašich vlastných dátach, čím zabezpečíte relevantnejšie a presnejšie odpovede. Azure AI Search môže byť použitý na ukladanie používateľsky špecifických cestovných spomienok, katalógov produktov alebo akýchkoľvek iných doménovo špecifických znalostí.

Azure AI Search podporuje schopnosti ako **Štruktúrované RAG**, ktoré vyniká v extrahovaní a vyhľadávaní hustých, štruktúrovaných informácií z veľkých datasetov ako história konverzácií, e-maily alebo dokonca obrázky. To poskytuje „nadľudskú presnosť a vyvolanie“ v porovnaní s tradičnými prístupmi delenia textu na kúsky a embeddingami.

## Vytváranie samoučiacich sa AI agentov

Bežný vzor pre samoučiacich sa agentov zahŕňa zavedenie **„knowledge agenta“**. Tento samostatný agent pozoruje hlavnú konverzáciu medzi používateľom a primárnym agentom. Jeho úlohou je:

1. **Identifikovať cenné informácie**: Určiť, či je časť konverzácie hodná uloženia ako všeobecné znalosti alebo špecifická používateľská preferencia.

2. **Extrahovať a zhrnúť**: Destilovať podstatné učenie alebo preferenciu z konverzácie.

3. **Uložiť do znalostnej databázy**: Trvale uložiť tieto extrahované informácie, často do vektorovej databázy, aby ich bolo možné neskôr vyhľadať.

4. **Obohacovať budúce dopyty**: Keď používateľ začne nový dopyt, knowledge agent načíta relevantné uložené informácie a pripojí ich k promptu používateľa, čím poskytne primárnemu agentovi kľúčový kontext (podobne ako RAG).

### Optimalizácie pre pamäť

• **Riadenie latencie**: Aby sa predišlo spomaleniu používateľských interakcií, môže sa najprv použiť lacnejší, rýchlejší model na rýchlu kontrolu, či sú informácie hodné uloženia alebo vyhľadania, pričom sa zložitejší proces extrakcie/vyhľadávania vykoná len v prípade potreby.

• **Údržba znalostnej databázy**: Pre rastúcu databázu znalostí možno menej často používané informácie presunúť do „studeného úložiska“, aby sa znížili náklady.

## Máte viac otázok o pamäti agentov?

Pridajte sa na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), aby ste sa stretli s inými študentmi, zúčastnili sa úradných hodín a získali odpovede na svoje otázky o AI agentoch.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vylúčenie zodpovednosti**:
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Hoci sa usilujeme o presnosť, vezmite prosím na vedomie, že automatické preklady môžu obsahovať chyby alebo nepresnosti. Pôvodný dokument v jeho originálnom jazyku by mal byť považovaný za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny ľudský preklad. Nezodpovedáme za akékoľvek nedorozumenia alebo nesprávne interpretácie vyplývajúce z použitia tohto prekladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->