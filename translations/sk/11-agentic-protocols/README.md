# Používanie agentných protokolov (MCP, A2A a NLWeb)

[![Agentné protokoly](../../../translated_images/sk/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Kliknite na obrázok vyššie a pozrite si video tejto lekcie)_

Ako rastie používanie AI agentov, rastie aj potreba protokolov, ktoré zabezpečujú štandardizáciu, bezpečnosť a podporujú otvorené inovácie. V tejto lekcii sa budeme venovať 3 protokolom, ktoré sa snažia túto potrebu naplniť - Model Context Protocol (MCP), Agent to Agent (A2A) a Natural Language Web (NLWeb).

## Úvod

V tejto lekcii sa budeme venovať:

• Ako **MCP** umožňuje AI Agentom pristupovať k externým nástrojom a údajom na dokončenie úloh používateľa.

•  Ako **A2A** umožňuje komunikáciu a spoluprácu medzi rôznymi AI agentmi.

• Ako **NLWeb** prináša rozhrania v prirodzenom jazyku na akúkoľvek webovú stránku, čo umožňuje AI Agentom objavovať a interagovať s obsahom.

## Ciele učenia

• **Identifikovať** základný účel a prínosy MCP, A2A a NLWeb v kontexte AI agentov.

• **Vysvetliť** ako každý protokol uľahčuje komunikáciu a interakciu medzi LLM, nástrojmi a inými agentmi.

• **Rozpoznať** odlišné úlohy, ktoré každý protokol zohráva pri budovaní komplexných agentných systémov.

## Protokol kontextu modelu

The **Model Context Protocol (MCP)** is an open standard that provides standardized way for applications to provide context and tools to LLMs. This enables a "universal adaptor" to different data sources and tools that AI Agents can connect to in a consistent way.

Pozrime sa na komponenty MCP, výhody v porovnaní s priamym používaním API a príklad, ako by AI agenti mohli využiť MCP server.

### Hlavné komponenty MCP

MCP funguje na základe **klient-server architektúry** a hlavné komponenty sú:

• **Hostitelia** sú aplikácie s LLM (napríklad kódový editor ako VSCode), ktoré začínajú pripojenia k MCP Server.

• **Klienti** sú komponenty v hostiteľskej aplikácii, ktoré udržiavajú one-to-one spojenia so servermi.

• **Servery** sú ľahké programy, ktoré vystavujú konkrétne schopnosti.

V protokole sú zahrnuté tri základné primitíva, ktoré predstavujú schopnosti MCP Servera:

• **Tools**: Sú to samostatné akcie alebo funkcie, ktoré môže AI agent zavolať na vykonanie úlohy. Napríklad, služba počasia môže vystaviť nástroj "get weather", alebo e-commerce server môže vystaviť nástroj "purchase product". MCP servery v zozname svojich schopností oznamujú názov každého nástroja, popis a vstupno-výstupné schémy.

• **Resources**: Sú to len na čítanie dostupné položky údajov alebo dokumenty, ktoré môže MCP Server poskytnúť a klienti si ich môžu na požiadanie vyžiadať. Príklady zahŕňajú obsah súborov, záznamy v databáze alebo súbory protokolu. Resources môžu byť textové (ako kód alebo JSON) alebo binárne (ako obrázky alebo PDF).

• **Prompts**: Sú to preddefinované šablóny, ktoré poskytujú navrhované výzvy, umožňujúce zložitejšie pracovné toky.

### Výhody MCP

MCP ponúka významné výhody pre AI Agenty:

• **Dynamické zisťovanie nástrojov**: Agenti môžu dynamicky získať zoznam dostupných nástrojov zo servera spolu s popismi toho, čo robia. To kontrastuje s tradičnými API, ktoré často vyžadujú statické kódovanie integrácií, čo znamená, že každá zmena API si vyžaduje aktualizáciu kódu. MCP ponúka prístup "integrovať raz", čo vedie k väčšej prispôsobivosti.

• **Interoperabilita naprieč LLM**: MCP funguje s rôznymi LLM, čo poskytuje flexibilitu pri prepínaní základných modelov za účelom hodnotenia lepšieho výkonu.

• **Štandardizované zabezpečenie**: MCP zahŕňa štandardnú metódu autentifikácie, ktorá zlepšuje škálovateľnosť pri pridávaní prístupu k ďalším MCP serverom. Toto je jednoduchšie než spravovanie rôznych kľúčov a typov autentifikácie pre rôzne tradičné API.

### Príklad MCP

![Diagram MCP](../../../translated_images/sk/mcp-diagram.e4ca1cbd551444a1.webp)

Predstavte si, že používateľ chce rezervovať let pomocou AI asistenta poháňaného MCP.

1. **Pripojenie**: AI asistent (MCP klient) sa pripája k MCP serveru poskytovanému leteckou spoločnosťou.

2. **Zisťovanie nástrojov**: Klient sa spýta MCP servera leteckej spoločnosti: "What tools do you have available?" Server odpovie nástrojmi ako "search flights" a "book flights".

3. **Volanie nástroja**: Potom požiadate AI asistenta: "Please search for a flight from Portland to Honolulu." AI asistent pomocou svojho LLM identifikuje, že potrebuje zavolať nástroj "search flights" a odovzdá relevantné parametre (odlet, cieľ) MCP serveru.

4. **Vykonanie a odpoveď**: MCP server, fungujúci ako obal, vykoná skutočné volanie do interného rezervačného API leteckej spoločnosti. Následne obdrží informácie o letoch (napr. JSON dáta) a odošle ich späť AI asistentovi.

5. **Ďalšia interakcia**: AI asistent predstaví možnosti letov. Keď vyberiete let, asistent môže vyvolať nástroj "book flight" na tom istom MCP serveri a dokončiť rezerváciu.

## Agent-to-Agent Protocol (A2A)

Kým MCP sa zameriava na pripájanie LLM k nástrojom, **Agent-to-Agent (A2A) protocol** robí ďalej tým, že umožňuje komunikáciu a spoluprácu medzi rôznymi AI agentmi. A2A prepája AI agentov naprieč rôznymi organizáciami, prostrediami a technologickými zásobníkmi, aby spolu dokončili spoločnú úlohu.

Pozrieme sa na komponenty a výhody A2A spolu s príkladom, ako by sa dal použiť v našej cestovnej aplikácii.

### Hlavné komponenty A2A

A2A sa zameriava na umožnenie komunikácie medzi agentmi a ich spoluprácu pri dokončení podúlohy používateľa. Každá súčasť protokolu tomu prispieva:

#### Karta agenta

Podobne ako MCP server zdieľa zoznam nástrojov, Agent Card obsahuje:
- Meno agenta .
- A **popis všeobecných úloh** ktoré vykonáva.
- A **zoznam konkrétnych zručností** s popismi, ktoré pomáhajú ostatným agentom (alebo aj ľudským používateľom) pochopiť, kedy a prečo by chceli toho agenta zavolať.
- The **current Endpoint URL** of the agent
- The **version** and **capabilities** of the agent such as streaming responses and push notifications.

#### Agent Executor

Agent Executor je zodpovedný za **predávanie kontextu užívateľského chatu na vzdialeného agenta**, vzdialený agent to potrebuje, aby pochopil úlohu, ktorú treba dokončiť. V A2A serveri agent používa svoj vlastný Large Language Model (LLM) na parsovanie prichádzajúcich požiadaviek a vykonávanie úloh pomocou vlastných vnútorných nástrojov.

#### Artefakt

Keď vzdialený agent dokončí požadovanú úlohu, jeho pracovný výstup sa vytvorí ako artefakt. Artefakt **obsahuje výsledok práce agenta**, **popis toho, čo bolo dokončené**, a **textový kontext**, ktorý sa odošle cez protokol. Po odoslaní artefaktu sa spojenie s vzdialeným agentom uzavrie, kým nebude opäť potrebné.

#### Fronta udalostí

Táto súčasť sa používa na **spracovanie aktualizácií a odovzdávanie správ**. Je obzvlášť dôležitá v produkčnom prostredí pre agentné systémy, aby sa zabránilo uzavretiu spojenia medzi agentmi skôr, než bude úloha dokončená, najmä keď dokončenie úlohy môže trvať dlhší čas.

### Výhody A2A

• **Zlepšená spolupráca**: Umožňuje agentom od rôznych dodávateľov a platforiem interagovať, zdieľať kontext a spolupracovať, čo uľahčuje bezproblémovú automatizáciu naprieč tradične oddelenými systémami.

• **Flexibilita pri výbere modelu**: Každý A2A agent si môže zvoliť LLM, ktorý používa na obsluhu svojich požiadaviek, čo umožňuje optimalizované alebo doladené modely pre každého agenta, na rozdiel od jedného LLM pripojenia v niektorých MCP scenároch.

• **Vstavaná autentifikácia**: Autentifikácia je integrovaná priamo do A2A protokolu, čím poskytuje robustné bezpečnostné rámce pre interakcie agentov.

### Príklad A2A

![Diagram A2A](../../../translated_images/sk/A2A-Diagram.8666928d648acc26.webp)

Rozšírme náš scenár rezervácie ciest, tentokrát s použitím A2A.

1. **Požiadavka používateľa viacerým agentom**: Používateľ komunikuje s "Travel Agent" A2A klientom/agenta, napríklad slovami: "Prosím, zarezervuj celý výlet do Honolulu na budúci týždeň, vrátane letov, hotela a požičovne auta".

2. **Orchestrace Travel Agenta**: Travel Agent prijme túto zložitú požiadavku. Použije svoj LLM na rozmyslenie úlohy a zistí, že potrebuje komunikovať s inými špecializovanými agentmi.

3. **Medziagentná komunikácia**: Travel Agent potom použije A2A protokol na pripojenie k downstream agentom, ako sú "Airline Agent", "Hotel Agent" a "Car Rental Agent", ktoré vytvorili rôzne spoločnosti.

4. **Delegované vykonanie úloh**: Travel Agent pošle konkrétne úlohy týmto špecializovaným agentom (napr. "Find flights to Honolulu", "Book a hotel", "Rent a car"). Každý z týchto špecializovaných agentov, ktorý prevádzkuje vlastné LLM a využíva svoje nástroje (ktoré môžu byť sami MCP servery), vykoná svoju časť rezervácie.

5. **Konsolidovaná odpoveď**: Keď všetci downstream agenti dokončia svoje úlohy, Travel Agent skompletuje výsledky (detaily letov, potvrdenie hotela, rezerváciu auta) a pošle používateľovi komplexnú odpoveď vo forme chatu.

## Natural Language Web (NLWeb)

Webové stránky už dlho predstavujú primárny spôsob, ako majú používatelia prístup k informáciám a údajom na internete.

Pozrime sa na rôzne komponenty NLWeb, výhody NLWeb a príklad, ako náš NLWeb funguje pri pohľade na našu cestovnú aplikáciu.

### Komponenty NLWeb

- **NLWeb Application (Core Service Code)**: Systém, ktorý spracováva otázky v prirodzenom jazyku. Spája rôzne časti platformy, aby vytváral odpovede. Môžete ho považovať za **motor, ktorý poháňa funkcie v prirodzenom jazyku** webovej stránky.

- **NLWeb Protocol**: Toto je **základný súbor pravidiel pre interakciu v prirodzenom jazyku** s webovou stránkou. Vracia odpovede v JSON formáte (často používajúci Schema.org). Jeho účelom je vytvoriť jednoduchý základ pre „AI Web“, podobne ako HTML umožnil zdieľať dokumenty online.

- **MCP Server (Model Context Protocol Endpoint)**: Každé nastavenie NLWeb tiež funguje ako **MCP server**. To znamená, že môže **zdieľať nástroje (ako metódu „ask“) a údaje** s inými AI systémami. V praxi to umožňuje, aby obsah a schopnosti webovej stránky boli použiteľné AI agentmi, čím sa stránka stáva súčasťou širšieho „ekosystému agentov“.

- **Embedding Models**: Tieto modely sa používajú na **konverziu obsahu webovej stránky do číselných reprezentácií nazývaných vektory** (embeddings). Tieto vektory zachytávajú význam tak, aby ich počítače vedeli porovnávať a vyhľadávať. Ukladajú sa v špeciálnej databáze a používatelia si môžu zvoliť, ktorý embedding model chcú použiť.

- **Vector Database (Retrieval Mechanism)**: Táto databáza **ukladá embeddingy obsahu webovej stránky**. Keď niekto položí otázku, NLWeb kontroluje vektorovú databázu, aby rýchlo našiel najrelevantnejšie informácie. Poskytne rýchly zoznam možných odpovedí, zoradených podľa podobnosti. NLWeb pracuje s rôznymi systémami ukladania vektorov, ako sú Qdrant, Snowflake, Milvus, Azure AI Search a Elasticsearch.

### NLWeb na príklade

![NLWeb](../../../translated_images/sk/nlweb-diagram.c1e2390b310e5fe4.webp)

Zoberme si opäť našu stránku na rezerváciu ciest, tentokrát poháňanú NLWeb.

1. **Získavanie dát**: Existujúce produktové katalógy cestovnej stránky (napr. zoznamy letov, popisy hotelov, balíčky výletov) sú formátované pomocou Schema.org alebo načítané cez RSS feedy. Nástroje NLWeb tieto štruktúrované dáta ingestujú, vytvoria embeddingy a uložia ich do lokálnej alebo vzdialenej vektorovej databázy.

2. **Otázka v prirodzenom jazyku (človek)**: Používateľ navštívi web a namiesto prechádzania ponukami napíše do chatovacieho rozhrania: "Find me a family-friendly hotel in Honolulu with a pool for next week".

3. **Spracovanie NLWeb**: Aplikácia NLWeb prijme túto otázku. Posiela otázku LLM na pochopenie a súčasne vyhľadáva vektorovú databázu pre relevantné hotelové ponuky.

4. **Presné výsledky**: LLM pomáha interpretovať výsledky vyhľadávania z databázy, identifikovať najlepšie zhody na základe kritérií "family-friendly", "pool" a "Honolulu" a potom naformátovať odpoveď v prirodzenom jazyku. Kľúčové je, že odpoveď odkazuje na skutočné hotely z katalógu webovej stránky, čím sa zabraňuje vymýšľaniu informácií.

5. **Interakcia AI agenta**: Keďže NLWeb slúži ako MCP server, externý AI cestovný agent sa môže tiež pripojiť k inštancii NLWeb tejto webovej stránky. AI agent by potom mohol použiť metódu `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")`. Inštancia NLWeb by to spracovala, využila svoju databázu informácií o reštauráciách (ak je načítaná) a vrátila štruktúrovanú JSON odpoveď.

### Máte ďalšie otázky o MCP/A2A/NLWeb?

Pridajte sa na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kde sa môžete stretnúť s ostatnými študentmi, zúčastniť sa konzultácií a získať odpovede na svoje otázky o AI agentoch.

## Zdroje

- [MCP pre začiatočníkov](https://aka.ms/mcp-for-beginners)  
- [MCP Documentation](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb Repo](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel Guides](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vylúčenie zodpovednosti**:
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Hoci sa snažíme o presnosť, vezmite prosím na vedomie, že automatické preklady môžu obsahovať chyby alebo nepresnosti. Pôvodný dokument v jeho pôvodnom jazyku by sa mal považovať za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny ľudský preklad. Za žiadne nedorozumenia ani nesprávne výklady vzniknuté použitím tohto prekladu nenesieme zodpovednosť.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->