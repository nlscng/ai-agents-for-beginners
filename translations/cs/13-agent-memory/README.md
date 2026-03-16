# Paměť pro AI agenty 
[![Paměť agenta](../../../translated_images/cs/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Při diskusi o jedinečných výhodách vytváření AI agentů se obvykle zmiňují dvě hlavní věci: schopnost volat nástroje k dokončení úkolů a schopnost zlepšovat se v čase. Paměť je základem vytváření samo-zlepšujících se agentů, kteří mohou vytvářet lepší zážitky pro naše uživatele.

V této lekci se podíváme na to, co je paměť pro AI agenty a jak ji můžeme spravovat a využívat ve prospěch našich aplikací.

## Úvod

Tato lekce pokrývá:

• **Porozumění paměti AI agentů**: Co je paměť a proč je pro agenty nezbytná.

• **Implementace a ukládání paměti**: Praktické metody přidání schopností paměti do vašich AI agentů, se zaměřením na krátkodobou a dlouhodobou paměť.

• **Jak učinit AI agenty samovylepšujícími se**: Jak paměť umožňuje agentům učit se z minulých interakcí a zlepšovat se v čase.

## Dostupné implementace

Tato lekce obsahuje dva komplexní výukové notebooky:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Implementuje paměť pomocí Mem0 a Azure AI Search v rámci frameworku Semantic Kernel

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Implementuje strukturovanou paměť pomocí Cognee, automaticky buduje znalostní graf podporovaný embeddingy, vizualizuje graf a zajišťuje inteligentní vyhledávání

## Cíle učení

Po dokončení této lekce budete umět:

• **Rozlišovat mezi různými typy paměti AI agentů**, včetně pracovní, krátkodobé a dlouhodobé paměti, stejně jako specializované formy jako paměť osobnosti a epizodická paměť.

• **Implementovat a spravovat krátkodobou a dlouhodobou paměť pro AI agenty** pomocí frameworku Semantic Kernel, využívající nástroje jako Mem0, Cognee, Whiteboard memory a integraci s Azure AI Search.

• **Pochopit principy samovylepšujících se AI agentů** a jak robustní systémy správy paměti přispívají k neustálému učení a adaptaci.

## Porozumění paměti AI agentů

V jádru věci **paměť pro AI agenty odkazuje na mechanismy, které jim umožňují uchovávat a vybavovat si informace**. Tyto informace mohou být konkrétní detaily o konverzaci, uživatelské preference, minulé akce nebo dokonce naučené vzory.

Bez paměti jsou AI aplikace často bezstavové, což znamená, že každá interakce začíná od nuly. To vede k opakujícímu se a frustrujícímu uživatelskému zážitku, kdy agent „zapomíná“ předchozí kontext nebo preference.

### Proč je paměť důležitá?

inteligence agenta je hluboce svázána s jeho schopností vybavovat si a využívat minulé informace. Paměť umožňuje agentům být:

• **Reflexivní**: Učit se z minulých akcí a výsledků.

• **Interaktivní**: Udržovat kontext v průběhu probíhající konverzace.

• **Proaktivní a reaktivní**: Předvídat potřeby nebo reagovat vhodně na základě historických dat.

• **Autonomní**: Fungovat samostatněji čerpáním ze uložených znalostí.

Cílem implementace paměti je učinit agenty více **spolehlivými a schopnými**.

### Typy paměti

#### Pracovní paměť

Představte si to jako kousek papíru, který agent používá během jednoho probíhajícího úkolu nebo myšlenkového procesu. Obsahuje okamžité informace potřebné k výpočtu dalšího kroku.

U AI agentů pracovní paměť často zachycuje nejrelevantnější informace z konverzace, i když je celý chat dlouhý nebo oříznutý. Zaměřuje se na extrakci klíčových prvků jako požadavky, návrhy, rozhodnutí a akce.

**Příklad pracovní paměti**

U agenta pro rezervaci cest by pracovní paměť mohla zachytit aktuální požadavek uživatele, například „Chci si rezervovat cestu do Paříže“. Tento konkrétní požadavek je držen v bezprostředním kontextu agenta, aby řídil aktuální interakci.

#### Krátkodobá paměť

Tento typ paměti uchovává informace po dobu jedné konverzace nebo relace. Je to kontext aktuálního chatu, který umožňuje agentovi odkazovat na předchozí výměny v dialogu.

**Příklad krátkodobé paměti**

Pokud se uživatel zeptá: „Kolik by stál let do Paříže?“ a poté naváže otázkou „A co ubytování tam?“, krátkodobá paměť zajistí, že agent ví, že „tam“ odkazuje na „Paříž“ v rámci téže konverzace.

#### Dlouhodobá paměť

To jsou informace, které přetrvávají napříč více konverzacemi nebo relacemi. Umožňuje agentům pamatovat si uživatelské preference, historické interakce nebo obecné znalosti po dlouhou dobu. To je důležité pro personalizaci.

**Příklad dlouhodobé paměti**

Dlouhodobá paměť může uložit, že „Ben má rád lyžování a outdoorové aktivity, má rád kávu s výhledem na hory a chce se vyhnout pokročilým sjezdovkám kvůli dřívějšímu zranění“. Tyto informace, získané z předchozích interakcí, ovlivní doporučení v budoucích plánovacích relacích cest, čímž budou vysoce personalizovaná.

#### Paměť osobnosti

Tento specializovaný typ paměti pomáhá agentovi vyvinout konzistentní „osobnost“ nebo „personu“. Umožňuje agentovi pamatovat si detaily o sobě samém nebo o své zamýšlené roli, což činí interakce plynulejšími a více zaměřenými.

**Příklad paměti osobnosti**
Pokud je cestovní agent navržen jako „odborník na plánování lyžařských zájezdů“, paměť osobnosti může tuto roli posilovat a ovlivňovat jeho odpovědi tak, aby odpovídaly tónu a znalostem experta.

#### Workflow/Episodická paměť

Tato paměť ukládá posloupnost kroků, které agent provádí během složitého úkolu, včetně úspěchů a neúspěchů. Je to jako pamatovat si konkrétní „epizody“ nebo minulé zkušenosti, aby se z nich dalo poučit.

**Příklad epizodické paměti**

Pokud se agent pokusil rezervovat konkrétní let, ale rezervace selhala kvůli nedostupnosti, epizodická paměť by tento neúspěch zaznamenala, což agentovi umožní zkusit alternativní lety nebo informovat uživatele o problému informovanějším způsobem při následném pokusu.

#### Paměť entit

To zahrnuje extrakci a zapamatování konkrétních entit (jako lidé, místa nebo věci) a událostí z konverzací. Umožňuje agentovi budovat strukturované porozumění klíčovým prvkům, o nichž se diskutovalo.

**Příklad paměti entit**

Z konverzace o minulé cestě může agent extrahovat „Paříž“, „Eiffelova věž“ a „večeře v restauraci Le Chat Noir“ jako entity. Při budoucí interakci si agent může „Le Chat Noir“ vybavit a nabídnout, že tam zarezervuje stůl znovu.

#### Strukturovaný RAG (Retrieval Augmented Generation)

Zatímco RAG je širší technika, „Strukturovaný RAG“ je vyzdvihován jako výkonná technologie pro paměť. Extrahuje husté, strukturované informace z různých zdrojů (konverzace, e-maily, obrázky) a používá je ke zvýšení přesnosti, vybavitelnosti a rychlosti odpovědí. Na rozdíl od klasického RAG, který spoléhá výhradně na sémantickou podobnost, Strukturovaný RAG pracuje s vnitřní strukturou informací.

**Příklad Strukturovaného RAG**

Místo pouhého přiřazení klíčových slov by Strukturovaný RAG mohl z e-mailu parsovat detaily letu (destinace, datum, čas, letecká společnost) a uložit je strukturovaně. To umožňuje přesné dotazy jako „Jaký let jsem si rezervoval do Paříže na úterý?“

## Implementace a ukládání paměti

Implementace paměti pro AI agenty zahrnuje systematický proces **správy paměti**, který zahrnuje generování, ukládání, vyhledávání, integraci, aktualizaci a dokonce „zapomínání“ (nebo mazání) informací. Vyhledávání je obzvláště klíčové.

### Specializované nástroje pro paměť

#### Mem0

Jedním ze způsobů, jak ukládat a spravovat paměť agenta, je použití specializovaných nástrojů jako Mem0. Mem0 funguje jako perzistentní vrstva paměti, která agentům umožňuje vybavovat si relevantní interakce, ukládat uživatelské preference a faktický kontext a učit se z úspěchů a neúspěchů v průběhu času. Myšlenka je taková, že bezstavní agenti se promění ve stavové.

Funguje prostřednictvím **dvoufázového pipe-line procesu paměti: extrakce a aktualizace**. Nejprve jsou zprávy přidané do vlákna agenta odeslány do služby Mem0, která používá velký jazykový model (LLM) k shrnutí historie konverzace a extrakci nových vzpomínek. Následně fáze aktualizace řízená LLM určí, zda tyto vzpomínky přidat, upravit nebo odstranit, a uloží je do hybridního úložiště dat, které může zahrnovat vektorové, grafové a klíč-hodnota databáze. Tento systém také podporuje různé typy paměti a může začlenit grafovou paměť pro správu vztahů mezi entitami.

#### Cognee

Dalším silným přístupem je použití **Cognee**, open-source semantické paměti pro AI agenty, která transformuje strukturovaná i nestrukturovaná data do dotazovatelných znalostních grafů podporovaných embeddingy. Cognee poskytuje **architekturu s dvojím úložištěm** kombinující vektorové vyhledávání podle podobnosti s grafovými vztahy, což agentům umožňuje chápat nejen to, jaké informace jsou podobné, ale i jak jsou pojmy navzájem propojeny.

Vyniká v **hybridním vyhledávání**, které kombinuje vektorovou podobnost, strukturu grafu a LLM dedukci - od vyhledávání surových chunků až po dotazování s přihlédnutím ke grafu. Systém udržuje **žijící paměť**, která se vyvíjí a roste a zároveň zůstává dotazovatelná jako jeden propojený graf, podporující jak krátkodobý kontext relace, tak dlouhodobou perzistentní paměť.

Výukový notebook Cognee ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstruje budování této sjednocené vrstvy paměti, s praktickými příklady importu různorodých zdrojů dat, vizualizace znalostního grafu a dotazování s různými strategiemi vyhledávání přizpůsobenými specifickým potřebám agentů.

### Ukládání paměti pomocí RAG

Kromě specializovaných nástrojů pro paměť jako mem0 , můžete využít robustní vyhledávací služby jako **Azure AI Search jako backend pro ukládání a vyhledávání vzpomínek**, zejména pro strukturovaný RAG.

To vám umožní ukotvit odpovědi agenta ve vašich vlastních datech, čímž zajistíte relevantnější a přesnější odpovědi. Azure AI Search lze použít k ukládání uživatelem specifických cestovních vzpomínek, katalogů produktů nebo jakýchkoli jiných oborově specifických znalostí.

Azure AI Search podporuje schopnosti jako **Strukturovaný RAG**, který vyniká v extrakci a vyhledávání hustých, strukturovaných informací z velkých datasetů jako jsou historie konverzací, e-maily nebo dokonce obrázky. To poskytuje „nadlidskou přesnost a vybavitelnost“ ve srovnání s tradičními přístupy založenými na dělení textu na kusy a embeddingech.

## Jak učinit AI agenty samovylepšujícími se

Běžný vzor pro samovylepšující se agenty zahrnuje zavedení "agenta znalostí". Tento samostatný agent sleduje hlavní konverzaci mezi uživatelem a primárním agentem. Jeho role je:

1. **Identifikovat cenné informace**: Určit, zda je nějaká část konverzace vhodná k uložení jako obecná znalost nebo specifická uživatelská preference.

2. **Extrahovat a shrnout**: Destilovat podstatné učení nebo preferenci z konverzace.

3. **Uložit do báze znalostí**: Perzistovat tyto extrahované informace, často ve vektorové databázi, aby mohly být později vyhledány.

4. **Rozšířit budoucí dotazy**: Když uživatel zahájí nový dotaz, agent znalostí vyhledá relevantní uložené informace a připojí je k promptu uživatele, poskytující primárnímu agentovi klíčový kontext (podobně jako RAG).

### Optimalizace paměti

• **Řízení latence**: Aby se předešlo zpomalení uživatelských interakcí, může být nejprve použit levnější, rychlejší model pro rychlou kontrolu, zda je informace hodnotná k uložení nebo vyhledání, a složitější extrakční/vyhledávací proces se spouští jen když je to nutné.

• **Údržba báze znalostí**: Pro rostoucí bázi znalostí lze méně často používané informace přesunout do „studeného uložiště“, aby se snížily náklady.

## Máte další dotazy ohledně paměti agentů?

Připojte se k [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) a setkejte se s ostatními studenty, navštěvujte konzultační hodiny a získejte odpovědi na své otázky ohledně AI agentů.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Prohlášení o vyloučení odpovědnosti:
Tento dokument byl přeložen pomocí služby pro překlad pomocí umělé inteligence Co-op Translator (https://github.com/Azure/co-op-translator). I když se snažíme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v originálním jazyce by měl být považován za autoritativní zdroj. Pro zásadní informace se doporučuje profesionální lidský překlad. Za jakákoli nedorozumění nebo nesprávné výklady vyplývající z použití tohoto překladu neneseme odpovědnost.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->