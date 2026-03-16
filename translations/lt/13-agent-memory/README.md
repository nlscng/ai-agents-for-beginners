# Atmintis AI agentams 
[![Agentų atmintis](../../../translated_images/lt/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Kalbant apie unikalią AI agentų kūrimo naudą, dažniausiai aptariami du dalykai: gebėjimas kviesti įrankius užduotims atlikti ir gebėjimas tobulėti laikui bėgant. Atmintis yra pagrindas kuriant savarankiškai tobulėjančius agentus, kurie gali sukurti geresnę patirtį mūsų vartotojams.

Šioje pamokoje pažvelgsime, kas yra atmintis AI agentams ir kaip galime ją valdyti bei naudoti mūsų programų naudai.

## Įvadas

Ši pamoka apims:

• **AI agentų atminties supratimas**: Kas yra atmintis ir kodėl ji yra būtina agentams.

• **Atminties įgyvendinimas ir saugojimas**: Praktiniai metodai, kaip pridėti atminties galimybes jūsų AI agentams, sutelkiant dėmesį į trumpalaikę ir ilgalaikę atmintį.

• **Suteikimas AI agentams gebėjimo tobulėti**: Kaip atmintis leidžia agentams mokytis iš ankstesnių sąveikų ir tobulėti laikui bėgant.

## Galimos įgyvendinimo parinktys

Ši pamoka apima du išsamius užrašų knygelių (notebook) vadovus:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Įgyvendina atmintį naudojant Mem0 ir Azure AI Search su Semantic Kernel karkasu

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Įgyvendina struktūrizuotą atmintį naudojant Cognee, automatiškai kuriant žinių grafą, paremtą embeddings, vizualizuojant grafą ir vykdant intelektualų atgavimo mechanizmą

## Mokymosi tikslai

Baigę šią pamoką, suprasite, kaip:

• **Atskirti įvairius AI agentų atminties tipus**, įskaitant darbinę, trumpalaikę ir ilgalaikę atmintį, taip pat specializuotas formas kaip persona ir epizodinė atmintis.

• **Įdiegti ir valdyti trumpalaikę bei ilgalaikę atmintį AI agentams** naudojant Semantic Kernel karkasą, pasitelkiant įrankius kaip Mem0, Cognee, Whiteboard atmintį ir integraciją su Azure AI Search.

• **Suprasti principus, leidžiančius AI agentams savarankiškai tobulėti** ir kaip tvirti atminties valdymo sprendimai prisideda prie nuolatinio mokymosi ir adaptacijos.

## AI agentų atminties supratimas

Iš esmės **AI agentų atmintis reiškia mechanizmus, leidžiančius jiems išlaikyti ir atsiminti informaciją**. Ši informacija gali būti specifinės detalės apie pokalbį, vartotojo pageidavimai, ankstesni veiksmai ar net išmokti modeliai.

Be atminties AI programos dažnai būna be valstybės (stateless), tai reiškia, kad kiekviena sąveika prasideda nuo nulio. Tai sukelia pasikartojančią ir erzinančią vartotojo patirtį, kur agentas "pamiršta" ankstesnį kontekstą ar nuostatas.

### Kodėl atmintis yra svarbi?

Agentų intelektas glaudžiai susijęs su jų gebėjimu prisiminti ir panaudoti ankstesnę informaciją. Atmintis leidžia agentams būti:

• **Refleksyviais**: Mokytis iš ankstesnių veiksmų ir rezultatų.

• **Interaktyviais**: Išlaikyti kontekstą vykstančioje pokalbio sekoje.

• **Proaktyviais ir reaguojančiais**: Numatyti poreikius arba tinkamai reaguoti remiantis istoriniais duomenimis.

• **Autonomiškais**: Veikti labiau savarankiškai remiantis saugoma informacija.

Atminties įgyvendinimo tikslas — padaryti agentus labiau **patikimus ir pajėgius**.

### Atminties tipai

#### Darbinė atmintis

Galvokite apie tai kaip apie tuo metu naudojamą užrašų lapelį, kurį agentas naudoja vienos, vykstančios užduoties ar mąstymo proceso metu. Ji laiko būtiną informaciją, reikalingą kitam žingsniui apskaičiuoti.

AI agentams darbinė atmintis dažnai fiksuoja svarbiausią informaciją iš pokalbio, net jei viso pokalbių istorija yra ilga arba sutrumpinta. Ji orientuojasi į raktinių elementų, tokių kaip reikalavimai, pasiūlymai, sprendimai ir veiksmai, išgavimą.

**Darbinės atminties pavyzdys**

Kelionių užsakymų agentui darbinė atmintis gali užfiksuoti vartotojo dabartinį prašymą, pvz., "Noriu užsakyti kelionę į Paryžių". Šis konkretus reikalavimas laikomas agento tiesioginiame kontekste, kad vadovautųsi dabartine sąveika.

#### Trumpalaikė atmintis

Šio tipo atmintis išlaiko informaciją vieno pokalbio ar sesijos metu. Tai yra dabartinio pokalbio kontekstas, leidžiantis agentui grįžti prie ankstesnių dialogo turų.

**Trumpalaikės atminties pavyzdys**

Jei vartotojas paklausia: "Kiek kainuotų skrydis į Paryžių?" ir vėliau klausia "O kaip dėl apgyvendinimo ten?", trumpalaikė atmintis užtikrina, kad agentas žino, jog "ten" reiškia "Paryžių" tame pačiame pokalbyje.

#### Ilgalaikė atmintis

Tai informacija, kuri išlieka per kelis pokalbius ar sesijas. Ji leidžia agentams prisiminti vartotojo pageidavimus, istorines sąveikas ar bendras žinias per ilgesnį laiką. Tai svarbu personalizavimui.

**Ilgalaikės atminties pavyzdys**

Ilgalaikė atmintis gali saugoti, kad "Benas mėgsta slidinėti ir lauko veiklas, mėgsta kavą su kalnų vaizdu ir nori vengti sudėtingų slidinėjimo trasų dėl ankstesnės traumos". Iš šių ankstesnių sąveikų išmokta informacija veikia rekomendacijas būsimo planavimo sesijose, darant jas itin suasmenintas.

#### Persona atmintis

Šis specializuotas atminties tipas padeda agentui formuoti nuoseklią "asmenybę" arba "personą". Ji leidžia agentui prisiminti detales apie save ar savo numatytą vaidmenį, todėl sąveikos tampa sklandesnės ir labiau orientuotos.

**Persona atminties pavyzdys**
Jei kelionių agentas yra sukurtas kaip "ekspertas slidinėjimo planuotojas", persona atmintis gali sustiprinti šį vaidmenį, paveikdama atsakymus taip, kad jie atitiktų eksperto toną ir žinias.

#### Darbo eigos / epizodinė atmintis

Ši atmintis saugo žingsnių seką, kurią agentas atlieka vykdydamas sudėtingą užduotį, įskaitant sėkmes ir nesėkmes. Tai kaip prisiminti konkrečius "epizodus" ar ankstesnes patirtis, kad būtų galima mokytis iš jų.

**Epizodinės atminties pavyzdys**

Jei agentas bandė užsakyti konkretų skrydį, bet tai nepavyko dėl nenumatomo prieinamumo trūkumo, epizodinė atmintis galėtų įrašyti šią nesėkmę, leidžiant agentui bandyti alternatyvius skrydžius arba informuoti vartotoją apie problemą labiau pagrįstai vykdant kitą bandymą.

#### Entitetų atmintis

Tai apima konkrečių entitetų (pvz., žmonių, vietų ar daiktų) ir įvykių išgavimą ir prisiminimą iš pokalbių. Tai leidžia agentui sukurti struktūrizuotą supratimą apie aptartus pagrindinius elementus.

**Entitetų atminties pavyzdys**

Iš pokalbio apie praeitą kelionę agentas gali išgauti "Paryžių", "Eifelio bokštą" ir "vakarienę restorane Le Chat Noir" kaip entitetus. Būsimoje sąveikoje agentas galėtų prisiminti "Le Chat Noir" ir pasiūlyti rezervaciją ten.

#### Struktūruotas RAG (Retrieval Augmented Generation)

Nors RAG yra platesnė technika, "Struktūruotas RAG" pabrėžiamas kaip galinga atminties technologija. Ji ištraukia tankią, struktūruotą informaciją iš įvairių šaltinių (pokalbių, el. laiškų, paveikslėlių) ir naudoja ją tikslumui, išgaudymui ir atsakymų greičiui pagerinti. Skirtingai nuo klasikinių RAG, kurie remiasi vien semantiniu panašumu, Struktūruotas RAG dirba su informacijos įgimta struktūra.

**Struktūruoto RAG pavyzdys**

Užuot tiesiog derinęs raktinius žodžius, Struktūruotas RAG galėtų išanalizuoti skrydžio detales (tikslas, data, laikas, oro linijos) iš el. laiško ir saugoti jas struktūrizuotu būdu. Tai leidžia tiksliai užklausoms, pavyzdžiui, "Kokį skrydį užsakiau į Paryžių antradienį?"

## Atminties įgyvendinimas ir saugojimas

Atminties įgyvendinimas AI agentams apima sistemingą procesą vadinamą **atminties valdymu**, kuris apima generavimą, saugojimą, gavimą, integravimą, atnaujinimą ir net "pamiršimą" (arba ištrynimą) informacijos. Išgavimas yra ypač svarbus aspektas.

### Specializuoti atminties įrankiai

#### Mem0

Viena iš galimybių saugoti ir valdyti agentų atmintį yra naudoti specializuotus įrankius, tokius kaip Mem0. Mem0 veikia kaip nuolatinio atminties sluoksnis, leidžiantis agentams prisiminti susijusias sąveikas, saugoti vartotojų nuostatas ir faktinį kontekstą bei mokytis iš sėkmių ir nesėkmių laikui bėgant. Idėja čia yra, kad bevalstės agentų modelis virsta būseną turinčiu.

Jis veikia per **dviejų fazių atminties procesą: išgavimą ir atnaujinimą**. Pirmiausia pranešimai, pridėti prie agento gijos, siunčiami į Mem0 tarnybą, kuri naudoja didelį kalbos modelį (LLM), kad suvestų pokalbių istoriją ir išgautų naujas atmintis. Vėliau LLM valdoma atnaujinimo fazė nustato, ar pridėti, pakeisti ar ištrinti šias atmintis, saugodama jas hibridinėje duomenų saugykloje, kuri gali apimti vektorių, grafų ir raktų-reikšmių duomenų bazes. Ši sistema taip pat palaiko įvairius atminties tipus ir gali įtraukti grafų atmintį santykiams tarp entitetų valdyti.

#### Cognee

Kitas galingas požiūris yra naudoti **Cognee**, atvirojo kodo semantinės atminties sistemą AI agentams, kuri transformuoja struktūrizuotus ir nestruktūrizuotus duomenis į užklausomus žinių grafus, paremtais embeddings. Cognee suteikia **dvikaupią saugyklos architektūrą**, derinančią vektorinį panašumo paiešką su grafų ryšiais, leidžiančią agentams suprasti ne tik tai, kas yra panašu, bet ir kaip sąvokos susijusios tarpusavyje.

Jis puikiai tinka **hibridiniam gavimui**, derinančiam vektorinį panašumą, grafų struktūrą ir LLM loginį svarstymą - nuo paprasto fragmentų paieškos iki grafų suvokiančių klausimų atsakymo. Sistema palaiko **gyvą atmintį**, kuri vystosi ir auga, išlikdama užklausoma kaip vienas sujungtas grafas, palaikantis tiek sesijos trumpalaikį kontekstą, tiek ilgalaikę nuolatinę atmintį.

Cognee užrašų knygelės vadovas ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstruoja, kaip sukurti šį sujungtą atminties sluoksnį, su praktiniais pavyzdžiais apie įvairių duomenų šaltinių įkėlimą, žinių grafo vizualizavimą ir užklausas su skirtingomis paieškos strategijomis, pritaikytomis konkretiems agentų poreikiams.

### Atminties saugojimas naudojant RAG

Beyond specialized memory tools like mem0 , you can leverage robust search services like **Azure AI Search as a backend for storing and retrieving memories**, especially for structured RAG.

This allows you to ground your agent's responses with your own data, ensuring more relevant and accurate answers. Azure AI Search can be used to store user-specific travel memories, product catalogs, or any other domain-specific knowledge.

Azure AI Search supports capabilities like **Structured RAG**, which excels at extracting and retrieving dense, structured information from large datasets like conversation histories, emails, or even images. This provides "superhuman precision and recall" compared to traditional text chunking and embedding approaches.

## Kaip AI agentai gali savarankiškai tobulėti

Dažnas modelis savarankiškai tobulėjantiems agentams apima atskiro "žinių agente" įvedimą. Šis atskiras agentas stebi pagrindinį pokalbį tarp vartotojo ir pagrindinio agento. Jo vaidmuo yra:

1. **Nustatyti vertingą informaciją**: Nuspręsti, ar kokia nors pokalbio dalis verta išsaugoti kaip bendros žinios ar konkretus vartotojo pageidavimas.

2. **Išgauti ir santraukinti**: Išskirti esminį mokymą ar pageidavimą iš pokalbio.

3. **Saugojimas žinių bazėje**: Išsaugoti šią išgautą informaciją, dažnai vektorinėje duomenų bazėje, kad vėliau būtų galima ją atgauti.

4. **Papildyti būsimus užklausimus**: Kai vartotojas inicijuoja naują užklausą, žinių agentas atgauna susijusią saugotą informaciją ir prideda ją prie vartotojo prašymo, pateikdamas pagrindiniam agentui svarbų kontekstą (panašiai kaip RAG).

### Atminties optimizavimai

• **Latencijos valdymas**: Norint išvengti vartotojo sąveikų sulėtėjimo, pradžioje galima naudoti pigesnį, greitesnį modelį, kuris greitai patikrina, ar informacija verta saugojimo ar paieškos, ir tik esant būtinybei įtraukti sudėtingesnį išgavimą/paiešką.

• **Žinių bazės priežiūra**: Augant žinių bazei, rečiau naudojama informacija gali būti perkelta į "šaltąją saugyklą", kad būtų valdoma kaina.

## Turite daugiau klausimų apie agentų atmintį?

Join the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) to meet with other learners, attend office hours and get your AI Agents questions answered.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Atsakomybės apribojimas**:
Šis dokumentas buvo išverstas naudojant dirbtinio intelekto vertimo paslaugą [Co-op Translator](https://github.com/Azure/co-op-translator). Nors stengiamės užtikrinti tikslumą, atkreipkite dėmesį, kad automatiniai vertimai gali turėti klaidų arba netikslumų. Originalus dokumentas jo gimtąja kalba turėtų būti laikomas autoritetingu šaltiniu. Dėl svarbios informacijos rekomenduojamas profesionalus, žmogaus atliktas vertimas. Mes neprisiimame atsakomybės už bet kokius nesusipratimus ar klaidingus aiškinimus, kilusius naudojant šį vertimą.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->