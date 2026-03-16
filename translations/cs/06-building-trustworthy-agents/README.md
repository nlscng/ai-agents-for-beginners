[![Důvěryhodní AI agenti](../../../translated_images/cs/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klikněte na obrázek výše pro zhlédnutí videa této lekce)_

# Vytváření důvěryhodných AI agentů

## Úvod

Tato lekce pokryje:

- Jak vytvořit a nasadit bezpečné a efektivní AI agenty
- Důležitá bezpečnostní opatření při vývoji AI agentů
- Jak zachovat soukromí dat a uživatelů při vývoji AI agentů

## Cíle učení

Po dokončení této lekce budete vědět, jak:

- Identifikovat a zmírňovat rizika při vytváření AI agentů
- Implementovat bezpečnostní opatření k zajištění správné správy dat a přístupu
- Vytvářet AI agenty, kteří zachovávají soukromí dat a poskytují kvalitní uživatelský zážitek

## Bezpečnost

Nejprve se podívejme na vytváření bezpečných agentních aplikací. Bezpečnost znamená, že AI agent funguje podle návrhu. Jako tvůrci agentních aplikací máme metody a nástroje, jak maximalizovat bezpečnost:

### Vytváření rámce systémových zpráv

Pokud jste někdy vytvářeli AI aplikaci pomocí modelů velkých jazyků (LLM), víte, jak důležité je navrhnout robustní systémový prompt nebo systémovou zprávu. Tyto prompty stanovují meta pravidla, instrukce a pokyny, jak bude LLM komunikovat s uživatelem a daty.

Pro AI agenty je systémový prompt ještě důležitější, protože AI agenti budou potřebovat velmi specifické instrukce k dokončení úkolů, které jsme jim určili.

Pro vytváření škálovatelných systémových promptů můžeme použít rámec systémových zpráv pro budování jednoho nebo více agentů v naší aplikaci:

![Vytváření rámce systémových zpráv](../../../translated_images/cs/system-message-framework.3a97368c92d11d68.webp)

#### Krok 1: Vytvoření meta systémové zprávy

Meta prompt bude použito LLM k generování systémových promptů pro agenty, které vytvoříme. Navrhujeme ho jako šablonu, abychom mohli efektivně vytvářet více agentů, pokud bude třeba.

Zde je příklad meta systémové zprávy, kterou bychom dali LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Krok 2: Vytvoření základního promptu

Dalším krokem je vytvořit základní prompt popisující AI agenta. Měli byste do něj zahrnout roli agenta, úkoly, které agent bude plnit, a další odpovědnosti agenta.

Zde je příklad:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Krok 3: Poskytnutí základní systémové zprávy LLM

Nyní můžeme tuto systémovou zprávu optimalizovat tak, že poskytneme meta systémovou zprávu jako systémovou zprávu a naši základní systémovou zprávu.

Výsledkem bude systémová zpráva lépe navržená k vedení našich AI agentů:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Krok 4: Opakování a zlepšování

Hodnota tohoto rámce systémových zpráv spočívá v tom, že umožňuje snadnější škálování vytváření systémových zpráv z více agentů a také zlepšování vašich systémových zpráv v průběhu času. Je vzácné, že budete mít systémovou zprávu, která funguje napoprvé pro celý váš případ použití. Možnost dělat malé úpravy a vylepšení změnou základní systémové zprávy a jejího zpracování systémem vám umožní porovnávat a hodnotit výsledky.

## Porozumění hrozbám

Pro vytváření důvěryhodných AI agentů je důležité porozumět rizikům a hrozbám pro vaše AI agenty a zmírnit je. Podívejme se na některé z různých hrozeb pro AI agenty a jak se na ně lépe připravit a plánovat.

![Porozumění hrozbám](../../../translated_images/cs/understanding-threats.89edeada8a97fc0f.webp)

### Úkol a instrukce

**Popis:** Útočníci se snaží změnit instrukce nebo cíle AI agenta prostřednictvím promptování nebo manipulace s vstupy.

**Zmírnění:** Proveďte validační kontroly a filtry vstupů, abyste odhalili potenciálně nebezpečné prompty, než je AI agent zpracuje. Protože tyto útoky obvykle vyžadují častou interakci s agentem, omezení počtu kroků v konverzaci je dalším způsobem, jak těmto útokům předcházet.

### Přístup ke kritickým systémům

**Popis:** Pokud má AI agent přístup k systémům a službám, které ukládají citlivá data, útočníci mohou kompromitovat komunikaci mezi agentem a těmito službami. Může jít o přímé útoky nebo nepřímé pokusy získat informace o těchto systémech přes agenta.

**Zmírnění:** AI agenti by měli mít přístup k systémům pouze v nezbytných případech, aby se takovým útokům zabránilo. Komunikace mezi agentem a systémem by měla být také zabezpečená. Implementace autentikace a kontroly přístupu je dalším způsobem, jak tato data ochránit.

### Přetížení zdrojů a služeb

**Popis:** AI agenti mohou používat různé nástroje a služby k plnění úkolů. Útočníci mohou tuto schopnost zneužít tím, že prostřednictvím AI agenta odešlou vysoký objem požadavků na služby, což může vést k selháním systémů nebo vysokým nákladům.

**Zmírnění:** Zavádějte pravidla omezující počet požadavků, které může AI agent na službu zaslat. Omezení počtu kroků konverzace a požadavků na AI agenta je dalším způsobem, jak těmto útokům zabránit.

### Otrava znalostní báze

**Popis:** Tento typ útoku není zaměřen přímo na AI agenta, ale na znalostní bázi a další služby, které AI agent používá. Může jít o poškození dat nebo informací, které AI agent použije k dokončení úkolu, což vede k zaujatým nebo nežádoucím odpovědím uživateli.

**Zmírnění:** Pravidelně ověřujte data, která AI agent používá ve svých pracovních postupech. Zajistěte, aby byl přístup k těmto datům bezpečný a měnili je pouze důvěryhodní jedinci, abyste předešli tomuto typu útoku.

### Kaskádové chyby

**Popis:** AI agenti přistupují k různým nástrojům a službám k plnění úkolů. Chyby způsobené útočníky mohou vést k selhání dalších systémů, ke kterým je AI agent připojen, což způsobí, že útok bude rozsáhlejší a obtížnější k řešení.

**Zmírnění:** Jeden způsob, jak tomu předejít, je provozovat AI agenta v omezeném prostředí, například vykonávat úkoly v Docker kontejneru, aby se zabránilo přímým útokům na systém. Vytvoření záložních mechanismů a logiky opakování pokusu při chybách systémů je dalším způsobem, jak zabránit větším selháním systému.

## Člověk v procesu (Human-in-the-Loop)

Dalším efektivním způsobem, jak vytvářet důvěryhodné systémy AI agentů, je použití konceptu člověka v procesu (Human-in-the-loop). Tento přístup vytváří tok, kde uživatelé mohou během běhu poskytovat agenty zpětnou vazbu. Uživatelé v podstatě fungují jako agenti v systému s více agenty a poskytují schválení nebo ukončení běžícího procesu.

![Člověk v procesu](../../../translated_images/cs/human-in-the-loop.5f0068a678f62f4f.webp)

Zde je ukázka kódu používající AutoGen, která ukazuje, jak je tento koncept implementován:

```python

# Vytvořte agenty.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Použijte input() pro získání vstupu od uživatele z konzole.

# Vytvořte ukončovací podmínku, která ukončí konverzaci, když uživatel řekne "APPROVE".
termination = TextMentionTermination("APPROVE")

# Vytvořte tým.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Spusťte konverzaci a přenášejte ji do konzole.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Při spouštění ve skriptu použijte asyncio.run(...).
await Console(stream)

```

## Závěr

Vytváření důvěryhodných AI agentů vyžaduje pečlivý návrh, robustní bezpečnostní opatření a kontinuální iterace. Implementací strukturovaných meta prompting systémů, porozuměním potenciálním hrozbám a aplikací zmírňujících strategií mohou vývojáři vytvořit AI agenty, kteří jsou bezpeční i efektivní. Navíc začlenění přístupu člověka v procesu zajišťuje, že AI agenti zůstanou v souladu s potřebami uživatelů a zároveň minimalizují rizika. Jak AI dále roste, udržování proaktivního přístupu k bezpečnosti, soukromí a etickým úvahám bude klíčové pro budování důvěry a spolehlivosti v AI řízených systémech.

### Máte více otázek o vytváření důvěryhodných AI agentů?

Připojte se k [Microsoft Foundry Discordu](https://aka.ms/ai-agents/discord), kde se setkáte s dalšími studenty, můžete navštěvovat konzultační hodiny a získat odpovědi na vaše otázky ohledně AI agentů.

## Další zdroje

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Přehled odpovědného používání AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Hodnocení generativních AI modelů a AI aplikací</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Bezpečnostní systémové zprávy</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Šablona posouzení rizik</a>

## Předchozí lekce

[Agentní RAG](../05-agentic-rag/README.md)

## Další lekce

[Designový vzor plánování](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Prohlášení o vyloučení odpovědnosti**:  
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). Přestože usilujeme o přesnost, mějte prosím na paměti, že automatické překlady mohou obsahovat chyby nebo nepřesnosti. Původní dokument v jeho mateřském jazyce by měl být považován za závazný zdroj. Pro důležité informace se doporučuje využít profesionální lidský překlad. Nepřebíráme žádnou odpovědnost za jakékoliv nedorozumění či nesprávné výklady vyplývající z použití tohoto překladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->