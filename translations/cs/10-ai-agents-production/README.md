# AI agenti v produkci: pozorovatelnost a hodnocení

[![AI agenti v produkci](../../../translated_images/cs/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

Jak se AI agenti přesouvají z experimentálních prototypů do reálných aplikací, schopnost porozumět jejich chování, sledovat jejich výkon a systematicky hodnotit jejich výstupy se stává důležitou.

## Cíle učení

Po dokončení této lekce budete umět/porozumíte:
- Základním konceptům pozorovatelnosti a hodnocení agentů
- Technikám pro zlepšení výkonu, nákladů a efektivity agentů
- Co a jak systematicky hodnotit u vašich AI agentů
- Jak kontrolovat náklady při nasazování AI agentů do produkce
- Jak instrumentovat agenty postavené s AutoGen

Cílem je vybavit vás znalostmi, které přemění vaše „černé skříňky“ agentů na transparentní, spravovatelné a spolehlivé systémy.

_**Poznámka:** Je důležité nasazovat AI agenty, kteří jsou bezpeční a důvěryhodní. Podívejte se také na lekci [Budování důvěryhodných AI agentů](./06-building-trustworthy-agents/README.md)._

## Sledy a úseky

Nástroje pro pozorovatelnost, jako je [Langfuse](https://langfuse.com/) nebo [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry), obvykle reprezentují běhy agenta jako sledy a úseky.

- **Sled** představuje kompletní úkol agenta od začátku do konce (např. zpracování uživatelského dotazu).
- **Úseky** jsou jednotlivé kroky uvnitř sledu (např. volání jazykového modelu nebo získávání dat).

![Trace tree in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Bez pozorovatelnosti může AI agent působit jako „černá skříňka“ – jeho vnitřní stav a uvažování jsou neprůhledné, což ztěžuje diagnostiku problémů nebo optimalizaci výkonu. S pozorovatelností se agenti stávají „skleněnými skříňkami“, které nabízejí transparentnost nezbytnou pro budování důvěry a zajištění, že fungují podle očekávání.

## Proč je pozorovatelnost důležitá v produkčním prostředí

Přechod AI agentů do produkčního prostředí přináší novou sadu výzev a požadavků. Pozorovatelnost už není jen „příjemným doplňkem“, ale kritickou schopností:

*   **Ladění a analýza kořenové příčiny:** Když agent selže nebo vygeneruje neočekávaný výstup, nástroje pro pozorovatelnost poskytují sledy potřebné k určení zdroje chyby. To je obzvlášť důležité u složitých agentů, které mohou zahrnovat více volání LLM, interakcí s nástroji a podmíněné logiky.
*   **Řízení latence a nákladů:** AI agenti často spoléhají na LLM a jiné externí API, které jsou účtovány za token nebo za volání. Pozorovatelnost umožňuje přesné sledování těchto volání a pomáhá identifikovat operace, které jsou nadměrně pomalé nebo drahé. To umožňuje týmům optimalizovat promptování, vybrat efektivnější modely nebo přepracovat pracovní postupy tak, aby lépe řídily provozní náklady a zajistily dobrý uživatelský zážitek.
*   **Důvěra, bezpečnost a shoda:** V mnoha aplikacích je důležité zajistit, aby se agenti chovali bezpečně a eticky. Pozorovatelnost poskytuje auditní stopu akcí a rozhodnutí agenta. To lze využít k detekci a zmírnění problémů, jako je prompt injection, generování škodlivého obsahu nebo nesprávné nakládání s osobně identifikovatelnými údaji (PII). Například můžete zkontrolovat sledy, abyste pochopili, proč agent poskytl určitou odpověď nebo použil konkrétní nástroj.
*   **Cykly kontinuálního zlepšování:** Data z pozorovatelnosti jsou základem iterativního vývojového procesu. Monitorováním toho, jak si agenti vedou v reálném světě, mohou týmy identifikovat oblasti pro zlepšení, sbírat data pro doladění modelů a ověřovat dopad změn. To vytváří zpětnou vazbu, kde produkční poznatky z online hodnocení informují offline experimentování a zdokonalování, což vede k postupně lepším výkonům agentů.

## Klíčové metriky ke sledování

Pro sledování a porozumění chování agenta by měla být sledována řada metrik a signálů. Konkrétní metriky se mohou lišit podle účelu agenta, ale některé jsou univerzálně důležité.

Zde jsou některé z nejběžnějších metrik, které sledují nástroje pro pozorovatelnost:

**Latency:** Jak rychle agent odpovídá? Dlouhé čekání negativně ovlivňuje uživatelský zážitek. Latenci byste měli měřit pro úkoly a jednotlivé kroky sledováním běhů agenta. Například agent, který potřebuje 20 sekund na všechna volání modelu, by mohl být urychlen použitím rychlejšího modelu nebo paralelním prováděním volání modelů.

**Costs:** Jaké jsou náklady na jeden běh agenta? AI agenti spoléhají na volání LLM účtovaná za token nebo externí API. Časté používání nástrojů nebo více promptů může rychle zvýšit náklady. Například pokud agent volá LLM pětkrát za marginální zlepšení kvality, musíte zvážit, zda je to oprávněné, nebo zda můžete snížit počet volání nebo použít levnější model. Monitorování v reálném čase také může pomoci identifikovat neočekávané špičky (např. chyby způsobující nadměrné smyčky API).

**Request Errors:** Kolik požadavků agent nezpracoval? To může zahrnovat chyby API nebo neúspěšná volání nástrojů. Aby byl váš agent v produkci robustnější vůči těmto situacím, můžete nastavit fallbacky nebo opakování. Např. pokud LLM poskytovatel A padne, přepněte na LLM poskytovatele B jako zálohu.

**User Feedback:** Implementace přímého uživatelského hodnocení poskytuje cenné poznatky. To může zahrnovat explicitní hodnocení (👍palec nahoru/👎dolů, ⭐1-5 hvězdiček) nebo textové komentáře. Konzistentně negativní zpětná vazba by vás měla varovat, protože je to znamení, že agent nefunguje podle očekávání.

**Implicit User Feedback:** Chování uživatelů poskytuje nepřímou zpětnou vazbu i bez explicitních hodnocení. To může zahrnovat okamžité přeformulování dotazu, opakované dotazy nebo klikání na tlačítko „znovu“. Např. pokud vidíte, že uživatelé opakovaně pokládají stejnou otázku, je to známka toho, že agent nefunguje podle očekávání.

**Accuracy:** Jak často agent generuje správné nebo žádoucí výstupy? Definice přesnosti se liší (např. správnost řešení úloh, přesnost vyhledávání informací, spokojenost uživatele). Prvním krokem je definovat, jak vypadá úspěch pro vašeho agenta. Přesnost můžete sledovat pomocí automatických kontrol, hodnotících skóre nebo štítků dokončení úkolů. Například označování sledů jako „succeeded“ nebo „failed“.

**Automated Evaluation Metrics:** Můžete také nastavit automatizované evaluace. Například můžete použít LLM k ohodnocení výstupu agenta, např. zda je užitečný, přesný či nikoli. Existuje také několik open source knihoven, které vám pomohou skórovat různé aspekty agenta. Např. [RAGAS](https://docs.ragas.io/) pro RAG agenty nebo [LLM Guard](https://llm-guard.com/) k detekci škodlivého jazyka nebo prompt injection.

V praxi dává kombinace těchto metrik nejlepší pokrytí "zdraví" AI agenta. V tomto kapitole v [ukázkovém notebooku](./code_samples/10_autogen_evaluation.ipynb) vám ukážeme, jak tyto metriky vypadají v reálných příkladech, ale nejprve se naučíme, jak typický evaluační workflow vypadá.

## Instrumentujte svého agenta

K získávání dat o sledování budete muset instrumentovat svůj kód. Cílem je instrumentovat kód agenta tak, aby emitoval sledy a metriky, které může zachytit, zpracovat a vizualizovat platforma pro pozorovatelnost.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) se stal průmyslovým standardem pro pozorovatelnost LLM. Poskytuje sadu API, SDK a nástrojů pro generování, sběr a export telemetrických dat.

Existuje mnoho instrumentačních knihoven, které obalují existující frameworky agentů a usnadňují export OpenTelemetry úseků do nástroje pro pozorovatelnost. Níže je příklad instrumentace AutoGen agenta pomocí knihovny [OpenLit instrumentation](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

Ukázkový [notebook](./code_samples/10_autogen_evaluation.ipynb) v této kapitole předvede, jak instrumentovat vašeho AutoGen agenta.

**Ruční vytváření úseků:** I když instrumentační knihovny poskytují dobré výchozí nastavení, často nastanou případy, kdy jsou potřeba podrobnější nebo vlastní informace. Můžete ručně vytvářet úseky pro přidání vlastní aplikační logiky. Co je důležitější, mohou obohatit automaticky nebo ručně vytvořené úseky o vlastní atributy (také známé jako tagy nebo metadata). Tyto atributy mohou zahrnovat obchodně specifická data, mezilehlé výpočty nebo jakýkoli kontext, který může být užitečný pro ladění nebo analýzu, jako jsou `user_id`, `session_id` nebo `model_version`.

Příklad ručního vytváření sledů a úseků s [Langfuse Python SDK](https://langfuse.com/docs/sdk/python/sdk-v3):

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Hodnocení agentů

Pozorovatelnost nám dává metriky, ale hodnocení je proces analýzy těchto dat (a provádění testů) za účelem zjištění, jak dobře AI agent funguje a jak ho lze zlepšit. Jinými slovy, až budete mít sledy a metriky, jak je použijete k posouzení agenta a k rozhodování?

Pravidelné hodnocení je důležité, protože AI agenti jsou často nedeterminističtí a mohou se vyvíjet (prostřednictvím aktualizací nebo driftu chování modelu) – bez hodnocení byste nevěděli, zda váš „chytrý agent“ skutečně odvádí dobrou práci nebo zda regresoval.

Existují dvě kategorie hodnocení AI agentů: **online hodnocení** a **offline hodnocení**. Obě jsou cenné a vzájemně se doplňují. Obvykle začínáme offline hodnocením, protože to je minimální nutný krok před nasazením jakéhokoli agenta.

### Offline hodnocení

![Dataset items in Langfuse](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

To zahrnuje hodnocení agenta v kontrolovaném prostředí, typicky s použitím testovacích datasetů, nikoli živých uživatelských dotazů. Používáte kurátované datové sady, kde znáte očekávaný výstup nebo správné chování, a pak spustíte svého agenta na těchto datech.

Například pokud jste vytvořili agenta na slovní matematické úlohy, můžete mít [testovací dataset](https://huggingface.co/datasets/gsm8k) 100 problémů se známými odpověďmi. Offline hodnocení se často provádí během vývoje (a může být součástí CI/CD pipeline) ke kontrole zlepšení nebo ochraně proti regresím. Výhodou je, že je to **opakovatelný proces a můžete získat jasné metriky přesnosti, protože máte ground truth**. Můžete také simulovat uživatelské dotazy a měřit odpovědi agenta vůči ideálním odpovědím nebo použít automatizované metriky, jak bylo popsáno výše.

Klíčovou výzvou offline eval je zajistit, aby byl váš testovací dataset komplexní a zůstal relevantní – agent může na fixním testovacím souboru podávat dobrý výkon, ale v produkci může narážet na velmi odlišné dotazy. Proto byste měli udržovat testovací sady aktualizované o nové okrajové případy a příklady, které odrážejí reálné scénáře​. Kombinace malých „smoke testů“ a větších evaluačních sad je užitečná: malé sady pro rychlé kontroly a větší pro širší metriky výkonu​.

### Online hodnocení

![Observability metrics overview](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

To se týká hodnocení agenta v živém, reálném prostředí, tj. během skutečného nasazení v produkci. Online hodnocení zahrnuje monitorování výkonu agenta na reálných uživatelských interakcích a průběžnou analýzu výsledků.

Například můžete sledovat míry úspěšnosti, skóre spokojenosti uživatelů nebo jiné metriky na živém provozu. Výhodou online hodnocení je, že **zachycuje věci, které byste v laboratorním prostředí nemuseli předvídat** – můžete pozorovat drift modelu v čase (pokud účinnost agenta klesá se změnou vzorců vstupů) a zachytit neočekávané dotazy nebo situace, které nebyly v testovacích datech​. Poskytuje skutečný obrázek toho, jak se agent chová v reálném světě.

Online hodnocení často zahrnuje sběr implicitní a explicitní uživatelské zpětné vazby, jak bylo popsáno, a případně provádění shadow testů nebo A/B testů (kde nová verze agenta běží paralelně pro porovnání se starou). Výzvou je, že může být obtížné získat spolehlivé štítky nebo skóre pro živé interakce – možná se budete spoléhat na uživatelskou zpětnou vazbu nebo metriky downstream (např. zda uživatel klikl na výsledek).

### Kombinace obou

Online a offline hodnocení se nevylučují; jsou vysoce doplňující. Poznatky z online monitorování (např. nové typy uživatelských dotazů, kde agent podává slabý výkon) lze využít k rozšíření a vylepšení offline testovacích datasetů. Naopak agenti, kteří si vedou dobře v offline testech, mohou být s větší důvěrou nasazeni a monitorováni online.

Ve skutečnosti mnoho týmů přijímá smyčku:

_evaluate offline -> deploy -> monitor online -> collect new failure cases -> add to offline dataset -> refine agent -> repeat_.

## Běžné problémy

Při nasazování AI agentů do produkce se můžete setkat s různými výzvami. Zde jsou některé běžné problémy a jejich možná řešení:

| **Issue**    | **Potential Solution**   |
| ------------- | ------------------ |
| AI Agent not performing tasks consistently | - Upřesněte prompt, který je dán AI agentovi; buďte jasní v cílech.<br>- Identifikujte, kde může rozdělení úkolů na podúkoly a jejich zpracování více agenty pomoci. |
| AI Agent running into continuous loops  | - Zajistěte, abyste měli jasné podmínky ukončení, aby agent věděl, kdy zastavit proces.<br>- Pro složité úkoly vyžadující uvažování a plánování použijte větší model specializovaný na řešení úloh. |
| AI Agent tool calls are not performing well   | - Otestujte a ověřte výstup nástroje mimo systém agenta.<br>- Zjemněte definované parametry, prompty a pojmenování nástrojů.  |
| Multi-Agent system not performing consistently | - Upřesněte prompty předávané jednotlivým agentům, aby byly konkrétní a navzájem odlišné.<br>- Postavte hierarchický systém s „routing“ nebo kontrolním agentem, který určí, který agent je ten správný. |

Mnoho z těchto problémů lze efektivněji identifikovat s nasazenou pozorovatelností. Sledy a metriky, o kterých jsme mluvili výše, pomáhají přesně určit, kde v pracovním toku agenta k problémům dochází, což značně zrychluje ladění a optimalizaci.

## Řízení nákladů
Zde je několik strategií, jak řídit náklady na nasazení AI agentů do produkce:

**Using Smaller Models:** Malé jazykové modely (SLMs) mohou v určitých agentních případech fungovat dobře a výrazně sníží náklady. Jak bylo zmíněno dříve, nejlepší způsob, jak pochopit, jak dobře se SLM osvědčí pro váš případ použití, je vybudovat evaluační systém k určení a porovnání výkonu vůči větším modelům. Zvažte použití SLMs pro jednodušší úkoly, jako je klasifikace záměru nebo extrakce parametrů, a větší modely ponechte pro složité odvozování.

**Using a Router Model:** Podobnou strategií je používat rozmanitost modelů a velikostí. Můžete použít LLM/SLM nebo serverless funkci k směrování požadavků podle složitosti na nejvhodnější modely. To také pomůže snížit náklady a zároveň zajistí výkon u správných úkolů. Například směrujte jednoduché dotazy na menší, rychlejší modely a drahé velké modely používejte pouze pro složité odvozovací úlohy.

**Caching Responses:** Identifikace běžných požadavků a úkolů a poskytování odpovědí dříve, než projdou vaším agentním systémem, je dobrý způsob, jak snížit objem podobných požadavků. Můžete dokonce implementovat tok, který pomocí jednodušších AI modelů určí, jak podobný je požadavek vašim uloženým (cached) požadavkům. Tato strategie může výrazně snížit náklady u často kladených dotazů nebo běžných pracovních postupů.

## Podívejme se, jak to funguje v praxi

V [example notebook of this section](./code_samples/10_autogen_evaluation.ipynb) uvidíme příklady toho, jak můžeme použít nástroje pro observabilitu k monitorování a vyhodnocování našeho agenta.


### Máte další otázky týkající se AI agentů v produkci?

Připojte se k [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), setkejte se s ostatními studenty, zúčastněte se konzultačních hodin a získejte odpovědi na své otázky o AI agentech.

## Předchozí lekce

[Návrhový vzor metakognice](../09-metacognition/README.md)

## Další lekce

[Agentické protokoly](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Prohlášení o vyloučení odpovědnosti:
Tento dokument byl přeložen pomocí AI překladatelské služby Co-op Translator (https://github.com/Azure/co-op-translator). I když usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho mateřském jazyce by měl být považován za autoritativní zdroj. Pro zásadní informace se doporučuje profesionální lidský překlad. Nejsme odpovědní za jakékoliv nedorozumění nebo nesprávné výklady vzniklé v důsledku použití tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->