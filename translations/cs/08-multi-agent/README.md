[![Multi-Agent Design](../../../translated_images/cs/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Klikněte na obrázek výše pro zhlédnutí videa této lekce)_

# Vzor návrhu vícenásobných agentů

Jakmile začnete pracovat na projektu, který zahrnuje více agentů, budete muset zvážit vzor návrhu vícenásobných agentů. Není však hned zřejmé, kdy přejít na více agentů a jaké jsou výhody.

## Úvod

V této lekci se snažíme odpovědět na následující otázky:

- Jaké jsou scénáře, kde jsou vícenásobní agenti použitelní?
- Jaké jsou výhody použití vícenásobných agentů oproti jednomu agentovi vykonávajícímu více úkolů?
- Jaké jsou stavební bloky implementace vzoru návrhu vícenásobných agentů?
- Jak získáme přehled o tom, jak si agenti vzájemně interagují?

## Cíle učení

Po této lekci byste měli být schopni:

- Identifikovat scénáře, kde jsou vícenásobní agenti použitelní
- Rozpoznat výhody použití vícenásobných agentů oproti jedinému agentovi.
- Pochopit stavební bloky implementace vzoru návrhu vícenásobných agentů.

Jaký je širší kontext?

*Vícenásobní agenti jsou vzor návrhu, který umožňuje více agentům spolupracovat za účelem dosažení společného cíle.*

Tento vzor je široce používán v různých oblastech, včetně robotiky, autonomních systémů a distribuovaného výpočtu.

## Scénáře, kde jsou vícenásobní agenti použitelní

Jaké scénáře jsou vhodné pro použití vícenásobných agentů? Odpověď je, že existuje mnoho situací, kdy je přínosné nasadit více agentů, zejména v následujících případech:

- **Velké pracovníky zátěže**: Velké pracovní úkoly lze rozdělit na menší úkoly a přiřadit je různým agentům, což umožňuje paralelní zpracování a rychlejší dokončení. Příkladem je rozsáhlé zpracování dat.
- **Složité úkoly**: Podobně jako u velkých zátěží lze složité úkoly rozdělit na menší dílčí úkoly a přiřadit je agentům specializovaným na konkrétní aspekt úkolu. Dobrou ukázkou jsou autonomní vozidla, kde různí agenti řeší navigaci, detekci překážek a komunikaci s ostatními vozidly.
- **Různorodá odborná znalost**: Různí agenti mohou mít různá odborná zaměření, což jim umožňuje efektivněji řešit různé aspekty úkolu než jeden agent. Příkladem v tomto případě je zdravotnictví, kde agenti mohou spravovat diagnostiku, léčebné plány a pacientské monitorování.

## Výhody použití vícenásobných agentů oproti jedinému agentovi

Systém s jedním agentem může fungovat dobře u jednoduchých úkolů, ale u složitějších úkolů může použití vícenásobných agentů přinést několik výhod:

- **Specializace**: Každý agent může být specializován na konkrétní úkol. Nedostatek specializace u jediného agenta znamená, že agent může dělat vše, ale může být zmatený, co dělat při složitém úkolu. Může například skončit tím, že vykoná úkol, na který není nejvhodnější.
- **Škálovatelnost**: Je snazší systém škálovat přidáním více agentů místo přetěžování jediného agenta.
- **Odolnost vůči chybám**: Pokud jeden agent selže, ostatní mohou pokračovat ve funkci, což zajišťuje spolehlivost systému.

Uveďme příklad, rezervujme cestu uživateli. Jednoagentový systém by musel řídit všechny aspekty procesu rezervace, od hledání letů přes rezervaci hotelů a pronájem aut. Aby jeden agent toto zvládl, musel by mít nástroje na řešení všech těchto úkolů, což by vedlo ke složitému a monolitickému systému obtížnému na údržbu a škálování. Víceagentový systém by naopak mohl mít různé agenty specializované na hledání letů, rezervaci hotelů a aut. To by učinilo systém modulárnějším, snáze udržovatelným a škálovatelným.

Porovnejme to s cestovní kanceláří provozovanou jako rodinným krámkem versus cestovní kanceláří fungující jako franšíza. Rodinný krámek by měl jednoho agenta, který řeší všechny aspekty rezervace, zatímco franšíza by měla různé agenty, každý řešící jiný aspekt rezervace.

## Stavební bloky implementace vzoru vícenásobných agentů

Než můžete vzor vícenásobných agentů implementovat, musíte porozumět stavebním blokům, které vzor tvoří.

Udělejme to konkrétnější opět na příkladu rezervace cesty uživateli. Stavební bloky by zahrnovaly:

- **Komunikace agentů**: Agenti na hledání letů, rezervaci hotelů a aut musí komunikovat a sdílet informace o preferencích a omezeních uživatele. Musíte rozhodnout o protokolech a metodách této komunikace. Konkrétně to znamená, že agent na hledání letů musí komunikovat s agentem na rezervaci hotelů, aby zajistil, že hotel je rezervován na stejné termíny jako let. To znamená, že agenti musí sdílet informace o cestovních datech uživatele, což vyžaduje rozhodnutí *které agenty sdílí informace a jak tyto informace sdílí*.
- **Koordinační mechanismy**: Agenti musí koordinovat své akce, aby byla splněna uživatelova přání a omezení. Uživatelská preference může být, že chce hotel blízko letiště, zatímco omezení může být, že auta k pronájmu jsou dostupná pouze na letišti. To znamená, že agent pro rezervaci hotelů musí koordinovat s agentem pro pronájem aut, aby byla splněna uživatelova očekávání. Potřebujete rozhodnout *jak si agenti koordinují své akce*.
- **Architektura agentů**: Agenti musí mít interní strukturu k rozhodování a učení se z interakcí s uživatelem. To znamená, že agent pro hledání letů musí mít vnitřní mechanismy rozhodování o tom, které lety doporučit. Potřebujete rozhodnout *jak agenti rozhodují a učí se z interakcí s uživatelem*. Příklady učení agenta mohou být, že agent na hledání letů může využívat model strojového učení k doporučování letů na základě minulých preferencí uživatele.
- **Přehled o interakcích vícenásobných agentů**: Musíte mít přehled o tom, jak agenti vzájemně interagují. To znamená, že potřebujete nástroje a techniky pro sledování aktivit a interakcí agentů. To může být ve formě nástrojů pro logování a monitorování, vizualizace a metrik výkonu.
- **Vzorové struktury vícenásobných agentů**: Existují různé vzory pro implementaci vícenásobných agentních systémů, jako jsou centralizované, decentralizované a hybridní architektury. Musíte si zvolit vzor, který nejlépe vyhovuje vašemu případu použití.
- **Člověk v procesu**: Většinou bude v procesu člověk, a musíte určit, kdy mají agenti požádat o lidský zásah. To může být ve formě uživatele, který požaduje konkrétní hotel nebo let, který agenti nedoporučili, nebo požádá o potvrzení před rezervací.

## Přehled o interakcích vícenásobných agentů

Je důležité mít přehled o tom, jak agenti spolu komunikují. Tento přehled je nezbytný pro ladění, optimalizaci a zajištění celkové efektivity systému. K tomu potřebujete nástroje a techniky pro sledování aktivit a interakcí agentů, například nástroje pro logování, monitorování, vizualizace a metriky výkonu.

Například u rezervace cesty uživateli byste mohli mít dashboard, který zobrazuje stav každého agenta, preference a omezení uživatele a interakce mezi agenty. Tento dashboard by mohl ukazovat cestovní data uživatele, lety doporučené agentem pro lety, hotely od agentů hotelů a auta od agentů na pronájem aut. To by vám dalo přehled, jak agenti spolupracují a zda jsou preference a omezení uživatele dodržena.

Podívejme se podrobněji na jednotlivé aspekty.

- **Nástroje pro logování a monitorování**: Chcete mít logování každé akce provedené agentem. Záznam v logu může obsahovat informace o agentovi, který akci vykonal, o akci samotné, čase provedení a výsledku akce. Tyto informace pak můžete využít k ladění, optimalizaci a dalším účelům.

- **Nástroje pro vizualizaci**: Vizualizace vám může pomoci vidět interakce agentů intuitivněji. Například můžete mít graf, který ukazuje tok informací mezi agenty. Tento graf vám pomůže identifikovat úzká místa, neefektivity a další problémy v systému.

- **Metriky výkonu**: Metriky výkonu pomáhají sledovat efektivitu systému vícenásobných agentů. Můžete sledovat například čas potřebný k dokončení úkolu, počet úkolů dokončených za jednotku času a přesnost doporučení od agentů. Tyto informace vám pomohou identifikovat oblasti pro zlepšení a optimalizaci systému.

## Vzorové struktury vícenásobných agentů

Pojďme se ponořit do konkrétních vzorů, které můžete využít pro vytváření aplikací s vícenásobnými agenty. Zde jsou některé zajímavé vzory, které stojí za zvážení:

### Skupinový chat

Tento vzor je užitečný, když chcete vytvořit skupinovou chatovací aplikaci, kde může více agentů spolu komunikovat. Typické použití zahrnuje týmovou spolupráci, zákaznickou podporu a sociální sítě.

V tomto vzoru každý agent reprezentuje uživatele ve skupinovém chatu a zprávy jsou mezi agenty vyměňovány pomocí zprávového protokolu. Agenti mohou posílat zprávy do skupiny, přijímat zprávy ze skupiny a reagovat na zprávy od ostatních agentů.

Tento vzor lze implementovat buď centralizovanou architekturou, kde všechny zprávy procházejí centrálním serverem, nebo decentralizovanou architekturou, kde si agenti zprávy vyměňují přímo.

![Group chat](../../../translated_images/cs/multi-agent-group-chat.ec10f4cde556babd.webp)

### Předání úkolu

Tento vzor je vhodný, když chcete vytvořit aplikaci, kde si agenti mohou předávat úkoly.

Typické použití zahrnuje zákaznickou podporu, správu úkolů a automatizaci pracovních toků.

V tomto vzoru každý agent reprezentuje úkol nebo krok v pracovním toku a agenti si mohou předávat úkoly na základě předem definovaných pravidel.

![Hand off](../../../translated_images/cs/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Spolupracující filtrování

Tento vzor je užitečný, když chcete vytvořit aplikaci, kde mohou agenti spolupracovat na poskytování doporučení uživatelům.

Proč byste chtěli, aby agenti spolupracovali? Protože každý agent může mít odlišné odborné znalosti a může do procesu doporučení přispět různými způsoby.

Uveďme příklad, kdy uživatel chce doporučení nejlepší akcie k nákupu na burze.

- **Odborník na odvětví**: Jeden agent může být odborníkem v určitém odvětví.
- **Technická analýza**: Další agent může být expertem na technickou analýzu.
- **Fundamentální analýza**: Jiný agent může být odborníkem na fundamentální analýzu. Spoluprací mohou tito agenti nabídnout uživateli komplexnější doporučení.

![Recommendation](../../../translated_images/cs/multi-agent-filtering.d959cb129dc9f608.webp)

## Scénář: Proces vrácení peněz

Uvažujme scénář, kdy zákazník žádá o vrácení peněz za produkt. Do tohoto procesu může být zapojeno mnoho agentů, ale rozdělíme je na agenty specifické pro tento proces a obecné agenty, které mohou být použity i v jiných procesech.

**Agenti specifickí pro proces vrácení peněz**:

Následující agenti mohou být zapojeni do procesu vrácení peněz:

- **Agent zákazníka**: Tento agent zastupuje zákazníka a je zodpovědný za zahájení procesu vrácení.
- **Agent prodejce**: Tento agent zastupuje prodejce a zajišťuje zpracování vrácení.
- **Agent platby**: Tento agent odpovídá za proces vrácení platby zákazníkovi.
- **Agent vyřešení**: Tento agent se stará o řešení případných problémů během procesu vrácení.
- **Agent souladu**: Tento agent zajišťuje, že proces vrácení odpovídá předpisům a politikám.

**Obecní agenti**:

Tyto agenty mohou využívat jiné části vašeho podnikání.

- **Agent dopravy**: Tento agent je zodpovědný za zaslání produktu zpět prodejci. Může být využit jak v procesu vrácení, tak při běžném zasílání produktů.
- **Agent zpětné vazby**: Tento agent sbírá zpětnou vazbu od zákazníků. Feedback můžete získávat kdykoli, nejen během procesu vrácení.
- **Agent eskalace**: Tento agent zajišťuje eskalaci problémů na vyšší úroveň podpory. Může být použit v jakémkoli procesu, kde je potřeba eskalovat problém.
- **Agent notifikací**: Tento agent posílá upozornění zákazníkovi v různých fázích procesu vrácení.
- **Agent analýzy**: Tento agent analyzuje data související s procesem vrácení.
- **Agent auditu**: Tento agent provádí audit procesu vrácení, aby bylo zajištěno jeho správné provádění.
- **Agent reportingu**: Tento agent generuje zprávy o průběhu vrácení.
- **Agent znalostí**: Tento agent spravuje databázi znalostí o procesu vrácení i dalších částech vašeho podnikání.
- **Agent zabezpečení**: Tento agent zajišťuje bezpečnost procesu vrácení.
- **Agent kvality**: Tento agent dohlíží na kvalitu procesu vrácení.

Výše uvedených agentů je poměrně mnoho, jak pro specifický proces vrácení, tak pro obecné agenty využitelné i jinde. Doufáme, že vám to dává představu, jak se rozhodnout, které agenty použít ve vašem víceagentním systému.

## Úkol

Navrhněte víceagentní systém pro proces zákaznické podpory. Identifikujte agenty zapojené do procesu, jejich role a odpovědnosti a jak spolu budou interagovat. Zvažte jak agenty specifické pro proces zákaznické podpory, tak obecné agenty, které lze využít i v dalších částech vašeho podnikání.
> Zamyslete se, než si přečtete následující řešení, možná budete potřebovat více agentů, než si myslíte.

> TIP: Zamyslete se nad různými fázemi procesu zákaznické podpory a také zvažte agenty potřebné pro jakýkoli systém.

## Řešení

[Řešení](./solution/solution.md)

## Kontroly znalostí

Otázka: Kdy byste měli zvážit použití multi-agentů?

- [ ] A1: Když máte malou pracovní zátěž a jednoduchý úkol.
- [ ] A2: Když máte velkou pracovní zátěž.
- [ ] A3: Když máte jednoduchý úkol.

[Kvíz řešení](./solution/solution-quiz.md)

## Shrnutí

V této lekci jsme se zabývali návrhovým vzorem multi-agent, včetně scénářů, kde jsou multi-agentní přístupy použitelné, výhod používání více agentů oproti jedinému agentovi, základními prvky implementace návrhového vzoru multi-agent a tím, jak mít přehled o tom, jak spolu jednotliví agenti vzájemně komunikují.

### Máte více otázek ohledně návrhového vzoru Multi-Agent?

Připojte se k [Microsoft Foundry Discordu](https://aka.ms/ai-agents/discord), kde se setkáte s dalšími studenty, můžete se zúčastnit hodin otevřených dveří a získat odpovědi na své otázky týkající se AI agentů.

## Další zdroje

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">Návrhové vzory AutoGen</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentní návrhové vzory</a>

## Předchozí lekce

[Plánování návrhu](../07-planning-design/README.md)

## Následující lekce

[Metakognice v AI Agentech](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Prohlášení o vyloučení odpovědnosti**:
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). Přestože usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho mateřském jazyce by měl být považován za závazný zdroj. Pro zásadní informace se doporučuje profesionální lidský překlad. Nezodpovídáme za jakékoli nedorozumění nebo mylné výklady vyplývající z použití tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->