[![Dôveryhodní AI agenti](../../../translated_images/sk/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Kliknutím na obrázok vyššie si pozrite video z tejto lekcie)_

# Budovanie dôveryhodných AI agentov

## Úvod

V tejto lekcii sa dozviete:

- Ako vytvárať a nasadzovať bezpečných a efektívnych AI agentov
- Dôležité bezpečnostné opatrenia pri vývoji AI agentov
- Ako zachovať súkromie údajov a používateľov pri vývoji AI agentov

## Ciele učenia

Po skončení tejto lekcie budete vedieť:

- Identifikovať a zmierňovať riziká pri vytváraní AI agentov
- Implementovať bezpečnostné opatrenia na správu údajov a prístupu
- Vytvárať AI agentov, ktorí zachovávajú súkromie údajov a poskytujú kvalitný používateľský zážitok

## Bezpečnosť

Najprv sa pozrime na budovanie bezpečných agentných aplikácií. Bezpečnosť znamená, že AI agent funguje tak, ako je navrhnutý. Ako tvorcovia agentných aplikácií máme metódy a nástroje na maximalizáciu bezpečnosti:

### Budovanie rámca systémových správ

Ak ste už niekedy vytvárali AI aplikáciu využívajúcu veľké jazykové modely (LLM), viete, aká dôležitá je robustná systémová výzva alebo systémová správa. Tieto výzvy stanovujú metapravidlá, inštrukcie a pokyny, ako bude LLM komunikovať s používateľom a spracovávať údaje.

Pre AI agentov je systémová výzva ešte dôležitejšia, pretože AI agenti potrebujú veľmi špecifické inštrukcie na vykonanie úloh, ktoré sme pre nich navrhli.

Na vytvorenie škálovateľných systémových výziev môžeme použiť rámec systémových správ na vytvorenie jedného alebo viacerých agentov v našej aplikácii:

![Budovanie rámca systémových správ](../../../translated_images/sk/system-message-framework.3a97368c92d11d68.webp)

#### Krok 1: Vytvorte Meta systémovú správu

Meta výzva bude použitá LLM na generovanie systémových výziev pre agentov, ktorých vytvoríme. Navrhujeme ju ako šablónu, aby sme mohli efektívne vytvárať viacerých agentov podľa potreby.

Tu je príklad meta systémovej správy, ktorú by sme dali LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Krok 2: Vytvorte základnú výzvu

Ďalším krokom je vytvoriť základnú výzvu na opísanie AI agenta. Mali by ste zahrnúť rolu agenta, úlohy, ktoré agent bude vykonávať, a ďalšie zodpovednosti agenta.

Tu je príklad:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Krok 3: Poskytnite základnú systémovú správu LLM

Teraz môžeme optimalizovať túto systémovú správu tým, že poskytneme meta systémovú správu ako systémovú správu spolu s našou základnou systémovou správou.

To vytvorí systémovú správu, ktorá je lepšie navrhnutá na usmernenie našich AI agentov:

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

#### Krok 4: Iterujte a zlepšujte

Hodnota tohto rámca systémových správ spočíva v možnosti škálovať vytváranie systémových správ pre viacerých agentov jednoduchšie, ako aj v postupnom zlepšovaní systémových správ. Je zriedkavé, že systémová správa bude fungovať na prvý pokus pre váš kompletný prípad použitia. Schopnosť robiť malé úpravy a zlepšenia zmenou základnej systémovej správy a jej spustením cez systém vám umožní porovnávať a hodnotiť výsledky.

## Pochopenie hrozieb

Na vytvorenie dôveryhodných AI agentov je dôležité pochopiť a zmierniť riziká a hrozby, ktorým váš AI agent čelí. Pozrime sa na niektoré z rôznych hrozieb AI agentov a ako sa na ne lepšie pripraviť a plánovať.

![Pochopenie hrozieb](../../../translated_images/sk/understanding-threats.89edeada8a97fc0f.webp)

### Úloha a inštrukcia

**Popis:** Útočníci sa snažia zmeniť inštrukcie alebo ciele AI agenta prostredníctvom podnetov alebo manipulácie s vstupmi.

**Zmiernenie:** Vykonávajte overovacie kontroly a filtre vstupov na detekciu potenciálne nebezpečných podnetov pred ich spracovaním AI agentom. Keďže tieto útoky typicky vyžadujú častú interakciu s agentom, obmedzenie počtu ťahov v konverzácii je ďalším spôsobom, ako zabrániť týmto typom útokov.

### Prístup ku kritickým systémom

**Popis:** Ak má AI agent prístup k systémom a službám uchovávajúcim citlivé údaje, útočníci môžu ohroziť komunikáciu medzi agentom a týmito službami. Môžu to byť priame útoky alebo nepriame snahy získať informácie o týchto systémoch prostredníctvom agenta.

**Zmiernenie:** AI agenti by mali mať prístup k systémom len na nevyhnutný účel, aby sa zabránilo týmto typom útokov. Komunikácia medzi agentom a systémom by mala byť tiež zabezpečená. Implementácia autentifikácie a kontroly prístupu je ďalším spôsobom ochrany týchto informácií.

### Preťaženie zdrojov a služieb

**Popis:** AI agenti majú prístup k rôznym nástrojom a službám na vykonávanie úloh. Útočníci môžu využiť túto schopnosť na útok na tieto služby posielaním veľkého objemu požiadaviek cez AI agenta, čo môže viesť k zlyhaniu systému alebo vysokým nákladom.

**Zmiernenie:** Zavedenie pravidiel na obmedzenie počtu požiadaviek, ktoré môže AI agent zaslať službe. Obmedzenie počtu ťahov v konverzácii a požiadaviek na AI agenta je ďalším spôsobom, ako zabrániť týmto typom útokov.

### Otrava znalostnej databázy

**Popis:** Tento typ útoku nesmeruje priamo na AI agenta, ale na znalostnú databázu a ďalšie služby, ktoré AI agent použije. Môže ísť o poškodenie údajov alebo informácií, ktoré AI agent použije na dokončenie úlohy, čo vedie k zaujatým alebo nežiaducim odpovediam používateľovi.

**Zmiernenie:** Pravidelne overujte údaje, ktoré AI agent bude používať vo svojich pracovných postupoch. Zabezpečte, aby prístup k týmto údajom bol bezpečný a umožnený len dôveryhodným osobám, aby sa predišlo tomuto typu útoku.

### Reťazové chyby

**Popis:** AI agenti pristupujú k rôznym nástrojom a službám na vykonávanie úloh. Chyby spôsobené útočníkmi môžu viesť k zlyhaniam iných systémov, ku ktorým je AI agent pripojený, čo spôsobí, že útok bude rozšírenejší a ťažko riešiteľný.

**Zmiernenie:** Jednou z metód, ako sa vyhnúť týmto situáciám, je mať AI agenta v obmedzenom prostredí, napríklad vykonávanie úloh v Docker kontejnery, aby sa zabránilo priamym útokom na systém. Ďalším spôsobom je vytvorenie záložných mechanizmov a logiky opätovného pokusu, keď určité systémy reagujú chybou, čím sa predchádza väčším zlyhaniam systému.

## Ľudský zásah v procese

Ďalším efektívnym spôsobom, ako vytvoriť dôveryhodné AI agentné systémy, je používanie ľudského zásahu v procese (Human-in-the-loop). Tento prístup umožňuje používateľom poskytovať spätnú väzbu agentom počas behu procesu. Používatelia tak v podstate pôsobia ako agenti v multi-agentnom systéme a poskytujú schválenie alebo ukončenie prebiehajúceho procesu.

![Ľudský zásah v procese](../../../translated_images/sk/human-in-the-loop.5f0068a678f62f4f.webp)

Tu je ukážka kódu používajúca AutoGen, ktorá demonštruje implementáciu tohto konceptu:

```python

# Vytvorte agentov.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Použite input() na získanie vstupu od používateľa z konzoly.

# Vytvorte ukončovaciu podmienku, ktorá ukončí konverzáciu, keď používateľ povie "APPROVE".
termination = TextMentionTermination("APPROVE")

# Vytvorte tím.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Spustite konverzáciu a streamujte do konzoly.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Použite asyncio.run(...), keď spúšťate skript.
await Console(stream)

```

## Záver

Budovanie dôveryhodných AI agentov vyžaduje starostlivý dizajn, robustné bezpečnostné opatrenia a neustálu iteráciu. Implementáciou štruktúrovaných meta výziev, pochopením potenciálnych hrozieb a aplikáciou stratégií zmierňovania môžu vývojári vytvárať AI agentov, ktorí sú zároveň bezpeční aj efektívni. Okrem toho začlenenie prístupu s ľudským zásahom v procese zabezpečuje, že AI agenti zostanú v súlade s potrebami používateľov a zároveň minimalizujú riziká. Ako AI naďalej postupuje, udržiavanie proaktívneho postoja voči bezpečnosti, súkromiu a etickým otázkam bude kľúčom k budovaniu dôvery a spoľahlivosti v systémoch riadených AI.

### Máte ďalšie otázky o budovaní dôveryhodných AI agentov?

Pridajte sa na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), kde sa môžete stretnúť s ďalšími študentmi, zúčastniť sa konzultačných hodín a získať odpovede na vaše otázky o AI agentoch.

## Ďalšie zdroje

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Prehľad zodpovedného využívania AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Hodnotenie generatívnych AI modelov a AI aplikácií</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Bezpečnostné systémové správy</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Šablóna hodnotenia rizík</a>

## Predchádzajúca lekcia

[Agentný RAG](../05-agentic-rag/README.md)

## Nasledujúca lekcia

[Vzory plánovania](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Upozornenie**:  
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Hoci sa snažíme o presnosť, prosím, majte na pamäti, že automatické preklady môžu obsahovať chyby alebo nepresnosti. Originálny dokument v jeho pôvodnom jazyku by mal byť považovaný za autoritatívny zdroj. Pre kritické informácie sa odporúča profesionálny ľudský preklad. Za akékoľvek nedorozumenia alebo nesprávne výklady vyplývajúce z použitia tohto prekladu nenesieme zodpovednosť.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->