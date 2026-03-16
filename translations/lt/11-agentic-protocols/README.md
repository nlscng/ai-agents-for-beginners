# Naudojant agentinius protokolus (MCP, A2A ir NLWeb)

[![Agentiniai protokolai](../../../translated_images/lt/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Spustelėkite aukščiau esančią nuotrauką, norėdami peržiūrėti šios pamokos vaizdo įrašą)_

Kadangi AI agentų naudojimas auga, didėja ir poreikis protokolams, užtikrinantiems standartizaciją, saugumą ir atviros inovacijos palaikymą. Šioje pamokoje apžvelgsime 3 protokolus, siekiančius tenkinti šiuos poreikius – Model Context Protocol (MCP), Agent to Agent (A2A) ir Natural Language Web (NLWeb).

## Įvadas

Šioje pamokoje aptarsime:

• Kaip **MCP** leidžia AI agentams pasiekti išorinius įrankius ir duomenis užduotims atlikti.

• Kaip **A2A** įgalina komunikaciją ir bendradarbiavimą tarp skirtingų AI agentų.

• Kaip **NLWeb** atneša natūralios kalbos sąsajas į bet kurią svetainę, leidžiant AI agentams atrasti ir sąveikauti su turiniu.

## Mokymosi tikslai

• **Nustatyti** pagrindinį MCP, A2A ir NLWeb tikslą bei privalumus AI agentų kontekste.

• **Paaiškinti**, kaip kiekvienas protokolas palengvina komunikaciją ir sąveiką tarp LLM, įrankių ir kitų agentų.

• **Atpažinti** skirtingas roles, kurias kiekvienas protokolas atlieka statant sudėtingas agentines sistemas.

## Model Context Protocol

Model Context Protocol (MCP) yra atviras standartas, suteikiantis standartizuotą būdą programoms perduoti kontekstą ir įrankius LLM. Tai leidžia turėti „universalią jungtį“ prie skirtingų duomenų šaltinių ir įrankių, prie kurių AI agentai gali prisijungti nuosekliai.

Peržiūrėkime MCP komponentus, privalumus, palyginti su tiesioginiu API naudojimu, ir pavyzdį, kaip AI agentai gali naudoti MCP serverį.

### MCP pagrindiniai komponentai

MCP veikia pagal **klientų‑serverių architektūrą**, o pagrindiniai komponentai yra:

• **Hosts** yra LLM programos (pavyzdžiui, kodo redaktorius VSCode), kurios inicijuoja ryšius su MCP serveriu.

• **Clients** yra komponentai pačioje host programoje, palaikantys vienas‑vienam ryšius su serveriais.

• **Servers** yra lengvos programos, kurios atveria konkrečias galimybes.

Protokole įtraukti trys pagrindiniai primityvai — tai MCP serverio galimybės:

• **Tools**: Tai atskiros veiksmų arba funkcijų, kurias AI agentas gali iškvieti atlikti veiksmą, pavyzdžiai. Pavyzdžiui, orų tarnyba gali atverti „get weather“ įrankį, arba e. prekybos serveris gali atverti „purchase product“ įrankį. MCP serveriai savo galimybių sąraše skelbia kiekvieno įrankio pavadinimą, aprašymą ir įvesties/išvesties schemą.

• **Resources**: Tai tik skaitymui skirti duomenų elementai arba dokumentai, kuriuos MCP serveris gali pateikti, ir kuriuos klientai gali gauti pagal poreikį. Pavyzdžiai: failų turinys, duomenų bazių įrašai ar žurnalo failai. Resources gali būti tekstiniai (pvz., kodas ar JSON) arba dvejetainiai (pvz., vaizdai ar PDF).

• **Prompts**: Išankstiniai šablonai, suteikiantys siūlomus užklausų pavyzdžius ir leidžiantys kurti sudėtingesnius darbo eigos scenarijus.

### MCP privalumai

MCP suteikia reikšmingų privalumų AI agentams:

• **Dinaminis įrankių atradimas**: Agentai gali dinamiškai gauti sąrašą galimų įrankių iš serverio kartu su aprašymais, ką jie atlieka. Tai skiriasi nuo tradicinių API, kurios dažnai reikalauja statinio kodavimo integracijoms, o bet koks API pasikeitimas reiškia kodo atnaujinimus. MCP siūlo „integruoti vieną kartą“ požiūrį, kuris suteikia didesnį prisitaikymą.

• **Suderinamumas tarp skirtingų LLM**: MCP veikia su skirtingais LLM, suteikdamas lankstumą keisti pagrindinius modelius, kad būtų galima įvertinti geresnį našumą.

• **Standartizuotas saugumas**: MCP apima standartinį autentifikavimo metodą, pagerinantį mastelį pridedant prieigą prie papildomų MCP serverių. Tai paprasčiau nei valdyti skirtingus raktus ir autentifikavimo tipus įvairioms tradicinėms API.

### MCP pavyzdys

![MCP diagrama](../../../translated_images/lt/mcp-diagram.e4ca1cbd551444a1.webp)

Įsivaizduokite, kad vartotojas nori užsakyti skrydį naudodamas MCP palaikomą AI asistentą.

1. **Connection**: AI asistentas (MCP klientas) prisijungia prie aviakompanijos suteikto MCP serverio.

2. **Tool Discovery**: Klientas paklausia aviakompanijos MCP serverio: „Kokius įrankius turite?“ Serveris atsako su įrankiais, tokiais kaip „search flights“ ir „book flights“.

3. **Tool Invocation**: Tuomet prašote AI asistento: „Prašau surasti skrydį iš Portland į Honolulu.“ AI asistentas, naudodamas savo LLM, nustato, kad reikia iškviesti įrankį „search flights“ ir perduoda MCP serveriui atitinkamus parametrus (kilmės, paskirties vieta).

4. **Execution and Response**: MCP serveris, veikiantis kaip apvalkalas, atlieka faktinį skambutį į aviakompanijos vidinį užsakymų API. Jis gauna skrydžių informaciją (pvz., JSON duomenis) ir grąžina ją AI asistentui.

5. **Further Interaction**: AI asistentas pateikia skrydžių parinktis. Kai pasirinksite skrydį, asistentas gali iškviesti tą patį MCP serverį su įrankiu „book flight“, užbaigdamas užsakymą.

## Agent-to-Agent Protocol (A2A)

Nors MCP orientuojasi į LLM ir įrankių sujungimą, **Agent-to-Agent (A2A) protokolas** žengia žingsnį toliau, įgalindamas komunikaciją ir bendradarbiavimą tarp skirtingų AI agentų. A2A jungia AI agentus per skirtingas organizacijas, aplinkas ir technologines struktūras, kad būtų įvykdytas bendras uždavinys.

Išnagrinėsime A2A komponentus ir privalumus, kartu pateikdami pavyzdį, kaip tai galėtų būti taikoma mūsų kelionių programėlėje.

### A2A pagrindiniai komponentai

A2A orientuotas į agentų tarpusavio komunikacijos užtikrinimą ir jų bendrą darbą vykdant vartotojo dalinę užduotį. Kiekvienas protokolo komponentas prisideda prie to:

#### Agento kortelė

Panašiai kaip MCP serveris dalinasi įrankių sąrašu, Agento kortelė turi:
- Agento pavadinimas .
- **bendrųjų užduočių aprašymą**, kurias jis atlieka.
- **konkrečių įgūdžių sąrašą** su aprašymais, padedančiais kitiems agentams (ar net žmonėms) suprasti, kada ir kodėl verta iškviesti tą agentą.
- **dabartinį Endpoint URL** agento
- **versiją** ir **galimybes**, pvz., srautinius atsakymus ir stumiamuosius pranešimus.

#### Agento vykdytojas

Agento vykdytojas atsakingas už **vartotojo pokalbio konteksto perdavimą nuotoliniam agentui**, nes nuotoliniam agentui reikia šio konteksto, kad suprastų, kokia užduotis turi būti atlikta. A2A serveryje agentas naudoja savo LLM, kad išanalizuotų gaunamas užklausas ir įvykdytų užduotis naudodamas savo vidinius įrankius.

#### Artefaktas

Kai nuotolinis agentas įvykdo prašytą užduotį, jo darbo rezultatas sukuriamas kaip artefaktas. Artefakte **yra agente atlikto darbo rezultatas**, **aprašymas, kas buvo atlikta**, ir **tekstinis kontekstas**, kuris siunčiamas per protokolą. Po artefakto išsiuntimo ryšys su nuotoliniu agentu uždaromas iki tol, kol jis vėl prireiks.

#### Įvykių eilė

Šis komponentas naudojamas **atnaujinimams tvarkyti ir žinutėms perduoti**. Tai ypač svarbu gamybiniams agentiniams sprendimams, kad būtų išvengta ryšio uždarymo tarp agentų prieš užduoties pabaigą, ypač kai užduotys gali užtrukti ilgiau.

### A2A privalumai

• **Pagerintas bendradarbiavimas**: Leidžia skirtingų tiekėjų ir platformų agentams bendrauti, dalytis kontekstu ir dirbti kartu, palengvindamas sklandžią automatizaciją tarp tradiciškai atskirtų sistemų.

• **Lankstus modelių pasirinkimas**: Kiekvienas A2A agentas gali nuspręsti, kurį LLM naudoti savo užklausų aptarnavimui, leidžiant optimizuotus ar pritaikytus modelius kiekvienam agentui, skirtingai nei vienas LLM ryšys kai kuriuose MCP scenarijuose.

• **Integruotas autentifikavimas**: Autentifikavimas yra tiesiogiai integruotas į A2A protokolą, suteikiant tvirtą saugumo pagrindą agentų sąveikoms.

### A2A pavyzdys

![A2A diagrama](../../../translated_images/lt/A2A-Diagram.8666928d648acc26.webp)

Išplėsime mūsų kelionių užsakymo scenarijų, bet šįkart naudodami A2A.

1. **User Request to Multi-Agent**: Vartotojas bendrauja su „Travel Agent“ A2A klientu/agentu, pavyzdžiui, sakydamas: „Prašau užsakyti visą kelionę į Honolulu kitai savaitei, įskaitant skrydžius, viešbutį ir nuomos automobilį“.

2. **Orchestration by Travel Agent**: Travel Agent gauna šį sudėtingą prašymą. Jis naudoja savo LLM, kad apmąstytų užduotį ir nustatytų, jog reikia sąveikauti su kitais specializuotais agentais.

3. **Inter-Agent Communication**: Travel Agent tada naudoja A2A protokolą, kad prisijungtų prie žemyninių agentų, pvz., „Airline Agent“, „Hotel Agent“ ir „Car Rental Agent“, kuriuos sukūrė skirtingos įmonės.

4. **Delegated Task Execution**: Travel Agent siunčia konkrečias užduotis šiems specializuotiems agentams (pvz., „Find flights to Honolulu“, „Book a hotel“, „Rent a car“). Kiekvienas iš šių specializuotų agentų, naudodamas savo LLM ir savo įrankius (kurie patys gali būti MCP serveriai), atlieka savo užduoties dalį.

5. **Consolidated Response**: Kai visi žemyniniai agentai užbaigia savo užduotis, Travel Agent sujungia rezultatus (skrydžių duomenis, viešbučio patvirtinimą, nuomos automobilio užsakymą) ir pateikia vartotojui išsamų, pokalbio stiliaus atsakymą.

## Natural Language Web (NLWeb)

Svetainės jau seniai yra pagrindinis būdas vartotojams prieiti prie informacijos ir duomenų internete.

Pažiūrėkime į skirtingus NLWeb komponentus, NLWeb privalumus ir pavyzdį, kaip mūsų NLWeb veikia žvelgiant iš kelionių programėlės pusės.

### NLWeb komponentai

- **NLWeb Application (Core Service Code)**: Sistema, kuri apdoroja natūralios kalbos klausimus. Ji sujungia skirtingas platformos dalis, kad sukurtų atsakymus. Galite ją manyti kaip **variklį, kuris maitina natūralios kalbos funkcijas** svetainėje.

- **NLWeb Protocol**: Tai **pagrindinių taisyklių rinkinys natūralios kalbos sąveikai** su svetaine. Jis grąžina atsakymus JSON formatu (dažnai naudojant Schema.org). Jo paskirtis – sukurti paprastą pagrindą „AI internetui“, taip kaip HTML leido bendrinti dokumentus internete.

- **MCP Server (Model Context Protocol Endpoint)**: Kiekviena NLWeb konfigūracija taip pat veikia kaip **MCP serveris**. Tai reiškia, kad ji gali **dalytis įrankiais (pvz., „ask“ metodu) ir duomenimis** su kitomis AI sistemomis. Praktikoje tai leidžia svetainės turinį ir galimybes padaryti prieinamas AI agentams, paversdama svetainę platesnės „agentų ekosistemos“ dalimi.

- **Embedding Models**: Šie modeliai naudojami **svetainės turinį paversti skaitmeninėmis reprezentacijomis, vadinamomis vektoriais** (embeddings). Šie vektoriai fiksuoja reikšmę taip, kad kompiuteriai galėtų juos palyginti ir ieškoti. Jie saugomi specialioje duomenų bazėje, ir vartotojai gali pasirinkti, kurį embedding modelį naudoti.

- **Vector Database (Retrieval Mechanism)**: Ši duomenų bazė **saugo svetainės turinio embedding’us**. Kai kas nors užduoda klausimą, NLWeb patikrina vektorinę duomenų bazę, kad greitai rastų aktualiausią informaciją. Ji pateikia greitą galimų atsakymų sąrašą, išrikiuotą pagal panašumą. NLWeb veikia su įvairiomis vektorių saugyklomis, tokiomis kaip Qdrant, Snowflake, Milvus, Azure AI Search ir Elasticsearch.

### NLWeb pavyzdys

![NLWeb](../../../translated_images/lt/nlweb-diagram.c1e2390b310e5fe4.webp)

Apsvarstykime vėl mūsų kelionių užsakymo svetainę, bet šįkart ji veikia su NLWeb.

1. **Data Ingestion**: Kelionių svetainės esami produktų katalogai (pvz., skrydžių sąrašai, viešbučių aprašymai, kelionių paketai) yra suformatuojami naudojant Schema.org arba įkelti per RSS. NLWeb įrankiai importuoja šiuos struktūruotus duomenis, sukuria embedding’us ir saugo juos vietinėje arba nuotolinėje vektorinėje duomenų bazėje.

2. **Natural Language Query (Human)**: Vartotojas apsilanko svetainėje ir, vietoje naršymo meniu, įveda pokalbio sąsajoje: „Rask šeimoms tinkamą viešbutį Honolulu su baseinu kitai savaitei“.

3. **NLWeb Processing**: NLWeb programa gauna šią užklausą. Ji siunčia užklausą į LLM supratimui ir tuo pačiu metu ieško savo vektorinėje duomenų bazėje atitinkančių viešbučių sąrašų.

4. **Accurate Results**: LLM padeda interpretuoti paieškos rezultatus iš duomenų bazės, identifikuoti geriausius atitikmenis pagal kriterijus „šeimai tinkamas“, „baseinas“ ir „Honolulu“, ir tada suformatuoti natūralios kalbos atsakymą. Svarbu, kad atsakymas nurodo tikrus viešbučius iš svetainės katalogo, vengiant išgalvotos informacijos.

5. **AI Agent Interaction**: Kadangi NLWeb veikia kaip MCP serveris, išorinis AI kelionių agentas taip pat galėtų prisijungti prie šios svetainės NLWeb instancijos. AI agentas galėtų naudoti `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")`. NLWeb instancija apdorotų tai, pasinaudodama savo restoranų informacijos duomenų baze (jei ji įkelta), ir grąžintų struktūruotą JSON atsakymą.

### Dar turite klausimų apie MCP/A2A/NLWeb?

Prisijunkite prie [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord), susitikite su kitais besimokančiais, dalyvaukite konsultacijų valandose ir gaukite atsakymus į savo AI agentų klausimus.

## Ištekliai

- [MCP pradedantiesiems](https://aka.ms/mcp-for-beginners)  
- [MCP dokumentacija](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb repozitorija](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel vadovai](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors siekiame tikslumo, prašome atkreipti dėmesį, kad automatizuoti vertimai gali turėti klaidų arba netikslumų. Originalus dokumentas jo gimtąja kalba turėtų būti laikomas autoritetingu šaltiniu. Esant kritinei informacijai, rekomenduojama pasitelkti profesionalų vertėją. Mes neatsakome už jokius nesusipratimus ar neteisingas interpretacijas, kilusias dėl šio vertimo naudojimo.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->