[![Úvod do AI agentů](../../../translated_images/cs/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Klikněte na obrázek výše pro zobrazení videa této lekce)_


# Úvod do AI agentů a případů použití

Vítejte v kurzu "AI Agents for Beginners"! Tento kurz poskytuje základní znalosti a praktické ukázky pro vytváření AI agentů.

Připojte se k <a href="https://discord.gg/kzRShWzttr" target="_blank">Komunitě Azure AI na Discordu</a>, kde se můžete setkat s ostatními studenty a tvůrci AI agentů a položit jakékoli otázky týkající se tohoto kurzu.

Abychom tento kurz zahájili, nejprve lépe pochopíme, co jsou AI agenti a jak je můžeme využít v aplikacích a pracovních postupech, které vytváříme.

## Úvod

Tato lekce pokrývá:

- Co jsou AI agenti a jaké jsou jejich různé typy?
- Pro jaké případy použití jsou AI agenti nejvhodnější a jak nám mohou pomoci?
- Jaké jsou některé základní stavební bloky při navrhování agentických řešení?

## Cíle učení
Po dokončení této lekce byste měli být schopni:

- Pochopit koncepty AI agentů a jak se liší od jiných AI řešení.
- Efektivně aplikovat AI agenty.
- Produktivně navrhovat agentická řešení pro uživatele i zákazníky.

## Definice AI agentů a typy AI agentů

### Co jsou AI agenti?

AI agenti jsou **systémy**, které umožňují **Velkým jazykovým modelům (LLMs)** **provádět akce** tím, že rozšiřují jejich schopnosti tím, že dávají LLM přístup k **nástrojům** a **znalostem**.

Rozeberme tuto definici na menší části:

- **Systém** - Je důležité nahlížet na agenty nejen jako na jednu komponentu, ale jako na systém mnoha komponent. Na základní úrovni jsou komponenty AI agenta:
  - **Prostředí** - Definovaný prostor, ve kterém AI agent operuje. Například, pokud máme AI agenta pro rezervaci cestování, prostředí může být rezervační systém, který agent používá k dokončení úkolů.
  - **Senzory** - Prostředí má informace a poskytuje zpětnou vazbu. AI agenti používají senzory k shromažďování a interpretaci těchto informací o aktuálním stavu prostředí. V příkladu cestovního agenta může rezervační systém poskytovat informace jako dostupnost hotelů nebo ceny letenek.
  - **Aktuátory** - Jakmile AI agent obdrží aktuální stav prostředí, pro aktuální úkol agent určí, jakou akci provést ke změně prostředí. U cestovního agenta to může být rezervace dostupného pokoje pro uživatele.

![Co jsou AI agenti?](../../../translated_images/cs/what-are-ai-agents.1ec8c4d548af601a.webp)

**Velké jazykové modely** - Koncept agentů existoval i před vznikem LLM. Výhodou vytváření AI agentů s LLM je jejich schopnost interpretovat lidský jazyk a data. Tato schopnost umožňuje LLM interpretovat informace o prostředí a definovat plán ke změně prostředí.

**Provádět akce** - Mimo systémy AI agentů jsou LLM omezeny na situace, kde je akce generování obsahu nebo informací na základě uživatelova promptu. V systémech AI agentů mohou LLM plnit úkoly tím, že interpretují žádost uživatele a používají nástroje dostupné ve svém prostředí.

**Přístup k nástrojům** - To, k jakým nástrojům má LLM přístup, je definováno 1) prostředím, ve kterém operuje, a 2) vývojářem AI agenta. V našem příkladu cestovního agenta jsou nástroje agenta omezeny operacemi dostupnými v rezervačním systému, a/nebo může vývojář omezit přístup agenta k nástrojům na lety.

**Paměť a znalosti** - Paměť může být krátkodobá v kontextu konverzace mezi uživatelem a agentem. Dlouhodobě, mimo informace poskytované prostředím, si AI agenti mohou také vyhledávat znalosti z jiných systémů, služeb, nástrojů a dokonce i od jiných agentů. V příkladu cestovního agenta by tyto znalosti mohly být informace o uživatelových preferencích cestování uložené v databázi zákazníků.

### Různé typy agentů

Now that we have a general definition of AI Agents, let us look at some specific agent types and how they would be applied to a travel booking AI agent.

| **Typ agenta**                | **Popis**                                                                                                                           | **Příklad**                                                                                                                                                                                                                     |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Jednoduchí reflexní agenti**      | Provádějí okamžité akce na základě předdefinovaných pravidel.                                                                         | Cestovní agent interpretuje kontext e-mailu a přeposílá stížnosti na cestování zákaznickému servisu.                                                                                                                             |
| **Modelově založení reflexní agenti** | Provádějí akce na základě modelu světa a změn v tomto modelu.                                                                        | Cestovní agent upřednostňuje trasy s významnými změnami cen na základě přístupu k historickým cenovým údajům.                                                                                                                 |
| **Agentí založení na cíli**         | Vytvářejí plány pro dosažení specifických cílů tím, že interpretují cíl a určují kroky k jeho dosažení.                              | Cestovní agent rezervuje cestu tím, že určí nezbytná cestovní opatření (auto, hromadná doprava, lety) z aktuální lokace do cíle.                                                                                                   |
| **Užitkově založení agenti**      | Zvažují preference a číselně vyhodnocují kompromisy, aby určily, jak dosáhnout cílů.                                                  | Cestovní agent maximalizuje užitek vyvážením pohodlí versus ceny při rezervaci cesty.                                                                                                                                          |
| **Učící se agenti**           | Zlepšují se v čase reagováním na zpětnou vazbu a přizpůsobováním svých akcí.                                                          | Cestovní agent se zlepšuje použitím zákaznické zpětné vazby z dotazníků po cestě pro úpravy budoucích rezervací.                                                                                                               |
| **Hierarchičtí agenti**       | Obsahují více agentů v hierarchickém systému, kde vyšší úrovně agentů rozdělují úkoly na dílčí úkoly pro nižší úrovně agentů.           | Cestovní agent zruší cestu tím, že rozdělí úkol na dílčí úkoly (například zrušení konkrétních rezervací) a nižší úrovně agentů je dokončí a ohlásí výsledky vyššímu agentovi.                                                      |
| **Systémy více agentů (MAS)** | Agenti dokončují úkoly nezávisle, buď kooperativně, nebo konkurenčně.                                                               | Kooperativní: Více agentů rezervuje specifické cestovní služby, jako jsou hotely, lety a zábava. Konkurenční: Více agentů spravuje a soupeří o sdílený kalendář rezervací hotelu, aby obsadili zákazníky v hotelu. |

## Kdy používat AI agenty

V předchozí části jsme použili případ použití cestovního agenta k vysvětlení, jak lze různé typy agentů použít v různých scénářích rezervace cestování. Tento příklad budeme používat i nadále v průběhu kurzu.

Podívejme se na typy případů použití, pro které jsou AI agenti nejvhodnější:

![Kdy používat AI agenty?](../../../translated_images/cs/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Problémy bez jasného řešení** - umožňují LLM určit potřebné kroky k dokončení úkolu, protože to nelze vždy pevně zakódovat do pracovního postupu.
- **Vícekrokové procesy** - úkoly, které vyžadují úroveň složitosti, při které agent potřebuje používat nástroje nebo informace během více kol namísto jednorázového vyhledání.  
- **Zlepšování v čase** - úkoly, kde se agent může v průběhu času zlepšovat tím, že dostává zpětnou vazbu ze svého prostředí nebo od uživatelů, aby poskytoval lepší užitek.

V lekci „Budování důvěryhodných AI agentů“ se věnujeme dalším úvahám o používání AI agentů.

## Základy agentických řešení

### Vývoj agentů

Prvním krokem při navrhování systému AI agenta je definovat nástroje, akce a chování. V tomto kurzu se zaměřujeme na použití **Azure AI Agent Service** pro definování našich agentů. Nabízí funkce jako:

- Výběr otevřených modelů, jako jsou OpenAI, Mistral a Llama
- Použití licencovaných dat prostřednictvím poskytovatelů, jako je Tripadvisor
- Použití standardizovaných nástrojů OpenAPI 3.0

### Agentické vzory

Komunikace s LLM probíhá prostřednictvím promptů. Vzhledem k polonezávislé povaze AI agentů není vždy možné nebo nutné ručně znovu zasílat prompt LLM po změně prostředí. Používáme **agentické vzory**, které nám umožňují promptovat LLM přes více kroků škálovatelnějším způsobem.

Tento kurz je rozdělen do některých z aktuálně populárních agentických vzorů.

### Agentické rámce

Agentické rámce umožňují vývojářům implementovat agentické vzory prostřednictvím kódu. Tyto rámce nabízejí šablony, pluginy a nástroje pro lepší spolupráci agentů. Tyto výhody poskytují možnosti pro lepší pozorovatelnost a odstraňování problémů v systémech AI agentů.

V tomto kurzu prozkoumáme výzkumně orientovaný rámec AutoGen a produkčně připravený Agent framework od Semantic Kernel.

## Ukázkové kódy

- Python: [Rámec agentů](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Rámec agentů](./code_samples/01-dotnet-agent-framework.md)

## Máte další dotazy ohledně AI agentů?

Připojte se k [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kde se můžete setkat s ostatními studenty, zúčastnit se konzultací a získat odpovědi na své otázky týkající se AI agentů.

## Předchozí lekce

[Nastavení kurzu](../00-course-setup/README.md)

## Další lekce

[Prozkoumání agentických rámců](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Zřeknutí se odpovědnosti**:
Tento dokument byl přeložen pomocí služby pro překlad založené na umělé inteligenci [Co-op Translator](https://github.com/Azure/co-op-translator). I když usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v originálním jazyce by měl být považován za závazný zdroj. Pro zásadní informace se doporučuje profesionální lidský překlad. Za jakékoli nedorozumění nebo nesprávné výklady vyplývající z použití tohoto překladu neneseme odpovědnost.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->