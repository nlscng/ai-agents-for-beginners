[![Úvod do AI agentov](../../../translated_images/sk/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Kliknite na obrázok vyššie pre zobrazenie videa tejto lekcie)_


# Úvod do AI agentov a prípadov použitia agentov

Vitajte v kurze "AI agenti pre začiatočníkov"! Tento kurz poskytuje základné vedomosti a praktické ukážky na budovanie AI agentov.

Join the <a href="https://discord.gg/kzRShWzttr" target="_blank">Komunita Azure AI na Discorde</a> to meet other learners and AI Agent Builders and ask any questions you have about this course.

To start this course, we begin by getting a better understanding of what AI Agents are and how we can use them in the applications and workflows we build.

## Úvod

This lesson covers:

- Čo sú AI agenti a aké sú rôzne typy agentov?
- Pre aké prípady použitia sú AI agenti najvhodnejší a ako nám môžu pomôcť?
- Aké sú niektoré základné stavebné prvky pri navrhovaní agentických riešení?

## Ciele učenia
After completing this lesson, you should be able to:

- Pochopiť koncepty AI agentov a ako sa líšia od iných AI riešení.
- Efektívne aplikovať AI agentov.
- Navrhovať agentické riešenia produktívne pre používateľov aj zákazníkov.

## Definovanie AI agentov a typy AI agentov

### Čo sú AI agenti?

AI agenti sú **systémy**, ktoré umožňujú **veľkých jazykových modelov (LLMs)** **vykonávať akcie** tým, že rozširujú ich schopnosti poskytovaním **prístupu k nástrojom** a **vedomostiam**.

Let's break this definition into smaller parts:

- **System** - Je dôležité myslieť na agentov nie len ako na jeden komponent, ale ako na systém zložený z viacerých komponentov. Na základnej úrovni sú komponenty AI agenta:
  - **Environment** - Definovaný priestor, v ktorom AI agent funguje. Napríklad, ak by sme mali cestovného agenta na rezerváciu ciest, prostredie by mohlo byť rezervačný systém, ktorý agent používa na dokončenie úloh.
  - **Sensors** - Prostredia obsahujú informácie a poskytujú spätnú väzbu. AI agenti používajú senzory na zber a interpretáciu týchto informácií o aktuálnom stave prostredia. V príklade cestovného agenta môže rezervačný systém poskytovať informácie ako dostupnosť hotelov alebo ceny leteniek.
  - **Actuators** - Keď AI agent získa aktuálny stav prostredia, pre danú úlohu určí, akú akciu vykonať na zmenu prostredia. Pre cestovného agenta to môže byť rezervovanie dostupnej izby pre používateľa.

![Čo sú AI agenti?](../../../translated_images/sk/what-are-ai-agents.1ec8c4d548af601a.webp)

**Large Language Models** - Koncept agentov existoval ešte pred vytvorením LLM. Výhodou budovania AI agentov s LLM je ich schopnosť interpretovať ľudský jazyk a údaje. Táto schopnosť umožňuje LLM interpretovať informácie z prostredia a definovať plán na zmenu prostredia.

**Perform Actions** - Mimo systémov AI agentov sú LLM obmedzené na situácie, kde akcia spočíva v generovaní obsahu alebo informácií na základe výzvy používateľa. V rámci systémov AI agentov dokážu LLM vykonávať úlohy interpretáciou požiadavky používateľa a využívaním nástrojov dostupných v ich prostredí.

**Access To Tools** - Ktorým nástrojom má LLM prístup, je definované 1) prostredím, v ktorom operuje, a 2) vývojárom AI agenta. V našom príklade cestovného agenta sú nástroje agenta obmedzené operáciami dostupnými v rezervačnom systéme, a/alebo vývojár môže obmedziť prístup agenta len na lety.

**Memory+Knowledge** - Pamäť môže byť krátkodobá v kontexte rozhovoru medzi používateľom a agentom. Dlhodobo, okrem informácií poskytovaných prostredím, môžu AI agenti tiež získavať vedomosti z iných systémov, služieb, nástrojov a dokonca z iných agentov. V príklade cestovného agenta môžu tieto vedomosti obsahovať informácie o preferenciách používateľa týkajúce sa cestovania, uložené v databáze zákazníkov.

### Rôzne typy agentov

Now that we have a general definition of AI Agents, let us look at some specific agent types and how they would be applied to a travel booking AI agent.

| **Typ agenta**                | **Popis**                                                                                                                       | **Príklad**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Jednoduché reflexné agenty**      | Vykonávajú okamžité akcie na základe preddefinovaných pravidiel.                                                                                  | Cestovný agent interpretuje kontext e-mailu a preposiela sťažnosti týkajúce sa cestovania na zákaznícky servis.                                                                                                                          |
| **Modelovo založené reflexné agenty** | Vykonávajú akcie na základe modelu sveta a zmien v tom modeli.                                                              | Cestovný agent uprednostňuje trasy so značnými cenovými zmenami na základe prístupu k historickým údajom o cenách.                                                                                                             |
| **Agenti založení na cieľoch**         | Vytvárajú plány na dosiahnutie konkrétnych cieľov tým, že interpretujú cieľ a určujú kroky na jeho dosiahnutie.                                  | Cestovný agent zarezervuje cestu tým, že určí potrebné cestovné usporiadania (auto, verejná doprava, lety) z aktuálnej polohy do cieľa.                                                                                |
| **Agenti založení na užitočnosti**      | Zohľadňujú preferencie a číselne vážia kompromisy, aby rozhodli, ako dosiahnuť ciele.                                               | Cestovný agent maximalizuje užitočnosť vážením pohodlia verzus nákladov pri rezervácii cesty.                                                                                                                                          |
| **Učiace sa agenti**           | Zlepšujú sa v priebehu času reakciou na spätnú väzbu a prispôsobovaním svojich akcií.                                                        | Cestovný agent sa zlepšuje využitím spätnej väzby od zákazníkov z prieskumov po ceste na úpravy budúcich rezervácií.                                                                                                               |
| **Hierarchické agenty**       | Majú viacero agentov v vrstvenom systéme, kde vyššie úrovne rozdeľujú úlohy na podúlohy pre nízkoúrovňové agenti na dokončenie. | Cestovný agent zruší cestu rozdelením úlohy na podúlohy (napríklad zrušenie konkrétnych rezervácií) a nižšie úrovne agentov ich vykonajú a oznámia výsledok vyššiemu agentovi.                                     |
| **Systémy viacerých agentov (MAS)** | Agenti dokončujú úlohy nezávisle, buď kooperatívne alebo konkurenčne.                                                           | Kooperatívne: Viacero agentov zarezervuje konkrétne cestovné služby, ako sú hotely, lety a zábava. Konkurenčné: Viacero agentov spravuje a súťaží o zdieľaný kalendár rezervácií hotela, aby umiestnili zákazníkov do hotela. |

## Kedy používať AI agentov

In the earlier section, we used the Travel Agent use-case to explain how the different types of agents can be used in different scenarios of travel booking. We will continue to use this application throughout the course.

Pozrime sa na typy prípadov použitia, pre ktoré sú AI agenti najvhodnejší:

![Kedy používať AI agentov?](../../../translated_images/sk/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Open-Ended Problems** - umožniť LLM určiť potrebné kroky na dokončenie úlohy, pretože to nie je vždy možné alebo vhodné pevne zakódovať do pracovného postupu.
- **Multi-Step Processes** - úlohy, ktoré vyžadujú úroveň zložitosti, pri ktorej AI agent potrebuje používať nástroje alebo informácie počas viacerých krokov namiesto jednorazového načítania.  
- **Improvement Over Time** - úlohy, pri ktorých sa agent môže časom zlepšovať prijímaním spätnej väzby buď zo svojho prostredia alebo od používateľov, aby poskytoval lepšiu hodnotu.

We cover more considerations of using AI Agents in the Building Trustworthy AI Agents lesson.

## Basics of Agentic Solutions

### Agent Development

The first step in designing an AI Agent system is to define the tools, actions, and behaviors. In this course, we focus on using the **Azure AI Agent Service** to define our Agents. It offers features like:

- Výber otvorených modelov, ako sú OpenAI, Mistral a Llama
- Použitie licencovaných dát prostredníctvom poskytovateľov, ako je Tripadvisor
- Použitie štandardizovaných nástrojov OpenAPI 3.0

### Agentic Patterns

Communication with LLMs is through prompts. Given the semi-autonomous nature of AI Agents, it isn't always possible or required to manually reprompt the LLM after a change in the environment. We use **Agentic Patterns** that allow us to prompt the LLM over multiple steps in a more scalable way.

This course is divided into some of the current popular Agentic patterns.

### Agentic Frameworks

Agentic Frameworks allow developers to implement agentic patterns through code. These frameworks offer templates, plugins, and tools for better AI Agent collaboration. These benefits provide abilities for better observability and troubleshooting of AI Agent systems.

In this course, we will explore the research-driven AutoGen framework and the production-ready Agent framework from Semantic Kernel.

## Ukážkové kódy

- Python: [Rámec agentov](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Rámec agentov](./code_samples/01-dotnet-agent-framework.md)

## Máte ďalšie otázky o AI agentoch?

Pridajte sa na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet with other learners, attend office hours and get your AI Agents questions answered.

## Predchádzajúca lekcia

[Nastavenie kurzu](../00-course-setup/README.md)

## Nasledujúca lekcia

[Preskúmanie agentických rámcov](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vylúčenie zodpovednosti**:
Tento dokument bol preložený pomocou AI prekladateľskej služby [Co-op Translator](https://github.com/Azure/co-op-translator). Aj keď sa usilujeme o presnosť, berte prosím na vedomie, že automatické preklady môžu obsahovať chyby alebo nepresnosti. Originálny dokument v jeho pôvodnom jazyku by sa mal považovať za rozhodujúci zdroj. Pre kritické informácie odporúčame profesionálny preklad vykonaný človekom. Nie sme zodpovední za žiadne nedorozumenia alebo nesprávne výklady vyplývajúce z použitia tohto prekladu.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->