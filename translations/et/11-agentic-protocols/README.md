# Agentprotokollide kasutamine (MCP, A2A ja NLWeb)

[![Agentprotokollid](../../../translated_images/et/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(Klõpsake ülaloleval pildil, et vaadata selle tunni videot)_

AI agentide kasutamise kasvades suureneb ka vajadus protokollide järele, mis tagavad standardimise, turvalisuse ja toetavad avatud innovatsiooni. Selles õppetükis käsitleme kolme protokolli, mis püüavad seda vajadust täita – Model Context Protocol (MCP), Agent to Agent (A2A) ja Natural Language Web (NLWeb).

## Sissejuhatus

Selles tunnis käsitleme:

• Kuidas **MCP** lubab AI agentidel kasutada väliseid tööriistu ja andmeid kasutaja ülesannete täitmiseks.

• Kuidas **A2A** võimaldab erinevate AI agentide vahel suhtlust ja koostööd.

• Kuidas **NLWeb** toob loomuliku keele liidesed igale veebisaidile, võimaldades AI agentidel sisu avastada ja sellega suhelda.

## Õpieesmärgid

• **Tuua välja** MCP, A2A ja NLWeb põhieesmärk ja eelised AI agentide kontekstis.

• **Selgitada**, kuidas iga protokoll hõlbustab suhtlust ja interaktsiooni LLM-ide, tööriistade ja teiste agentide vahel.

• **Tunnustada** rollide erinevust, mida iga protokoll mängib keerukate agentide süsteemide ülesehitamisel.

## Model Context Protocol

**Model Context Protocol (MCP)** on avatud standard, mis pakub standardiseeritud viisi rakendustele pakkuda konteksti ja tööriistu LLM-idele. See võimaldab „universaalset adapterit“ eri andmeallikate ja tööriistade jaoks, millega AI agentidel on võimalik ühtlaselt ühenduda.

Vaatame MCP komponente, eeliseid otsese API kasutamise ees ja näidet, kuidas AI agentid võivad MCP serverit kasutada.

### MCP põhikomponendid

MCP töötab **kliendi-serveri arhitektuuril** ja põhikomponendid on:

• **Hostid** on LLM-rakendused (näiteks koodiredaktor nagu VSCode), mis alustavad ühendusi MCP serveriga.

• **Kliendid** on hostrakenduse sees olevad komponendid, mis hoiavad ühe-ühe-ühendusi serveritega.

• **Serverid** on kergekaalulised programmid, mis avavad kindlad võimekused.

Protokolli hulka kuulub kolm põhielementi, mis on MCP serveri võimed:

• **Tööriistad**: Need on eraldiseisvad tegevused või funktsioonid, mida AI agent saab kutsega käivitada. Näiteks võib ilmateenus pakkuda „ilma päringu“ tööriista või e-kaubanduse server „toote ostu“ tööriista. MCP serverid reklaamivad iga tööriista nime, kirjelduse ja sisend/väljundi skeemi oma võimekuste näidetes.

• **Ressursid**: Need on ainult lugemiseks mõeldud andmeüksused või dokumendid, mida MCP server saab pakkuda ning kliendid saavad neid päringu alusel kätte saada. Näideteks on failisisu, andmebaasisalvestised või logifailid. Ressursid võivad olla tekstina (näiteks kood või JSON) või binaarsed (näiteks pildid või PDFid).

• **Skriptid (Prompts)**: Need on eeldefineeritud mallid, mis pakuvad soovitatud käske keerukamate töövoogude jaoks.

### MCP eelised

MCP pakub AI agentidele märkimisväärseid eeliseid:

• **Dünaamiline tööriistade avastus**: Agendid saavad serverilt dünaamiliselt nimekirja saadaolevatest tööriistadest koos kirjeldustega toimingu kohta. See erineb traditsioonilistest API-dest, mis sageli nõuavad staatilist kodeerimist integratsioonide jaoks, mis tähendab, et iga API muutuse puhul on vaja koodi uuendada. MCP pakub „ühe korra integreerimise“ lähenemist, mis suurendab kohanemisvõimet.

• **Ühilduvus erinevate LLM-idega**: MCP töötab erinevate LLM-idega, võimaldades mudelite vahetust parema jõudluse saavutamiseks.

• **Standardiseeritud turvalisus**: MCP sisaldab standardset autentimismeetodit, mis parandab skaleeritavust MCP serverite juurde pääsu lisamisel. See on lihtsam kui erinevate võtmete ja autentimistüüpide haldamine traditsiooniliste API-de puhul.

### MCP näide

![MCP Diagramm](../../../translated_images/et/mcp-diagram.e4ca1cbd551444a1.webp)

Kujutlege, et kasutaja soovib AI assistendi abil lennupileti broneerida, kasutades MCP-d.

1. **Ühendamine**: AI assistent (MCP klient) ühendub lennufirma MCP serveriga.

2. **Tööriistade avastus**: Klient küsib lennufirma MCP serverilt: „Millised tööriistad teil olemas on?“ Server vastab tööriistadega nagu „otsi lende“ ja „broneeri lend“.

3. **Tööriista kutsumine**: Kasutaja ütleb AI assistendile: „Palun otsi lendu Portlandist Honolulu.“ AI assistent, kasutades oma LLM-i, määrab, et peab kutsuma tööriista „otsi lende“ ja edastab MCP serverile vajalikud parameetrid (lähtekoht, sihtkoht).

4. **Täideviimine ja vastus**: MCP server, toimides mähisena, teeb päris pöördumise lennufirma sisese broneerimis-API poole. Seejärel saab lennuinfo (nt JSON-andmed) ja saadab need AI assistendile tagasi.

5. **Edasine suhtlus**: AI assistent esitab lennuvalikud. Kui kasutaja valib lennu, võib assistent kutsuda sama MCP serveri tööriista „broneeri lend“ ning lõpetada broneeringu.

## Agentidevaheline protokoll (A2A)

Kui MCP keskendub LLM-ide ühendamisele tööriistadega, siis **Agent-to-Agent (A2A) protokoll** läheb sammu edasi, võimaldades erinevate AI agentide vahelist suhtlust ja koostööd. A2A ühendab AI agendid erinevates organisatsioonides, keskkondades ja tehnoloogiaplatformidel, et täita ühine ülesanne.

Vaatleme A2A komponente ja eeliseid ning näidet selle rakendamisest meie reisisüsteemis.

### A2A põhikomponendid

A2A keskendub agentide vahelise suhtluse võimaldamisele ja nende koostööle kasutaja alamülesande täitmisel. Protokolli iga komponent aitab sellel kaasa:

#### Agentkaart

Sarnaselt MCP serveri tööriistade nimekirjale sisaldab Agentkaart:

- Agendi nimi.

- **Üldise ülesande** kirjeldus, mida agent täidab.

- **Spetsiaalsete oskuste nimekiri** koos kirjeldustega, mis aitavad teistel agentidel (või isegi inimestel) mõista, millal ja miks antud agenti kutsuda.

- Agendi **praegune Endpoint URL**.

- Agendi **versioon** ja **võimekused** nagu voogedastusvastused ja push-teavitused.

#### Agent Executor

Agent Executor vastutab **kasutaja vestluskonteksti edastamise eest kaugagentile**; kaugagent vajab seda, et mõista, millist ülesannet tuleb täita. A2A serveris kasutab agent omaenda suure keelemudeli (LLM) abi sisenevate päringute analüüsiks ja ülesannete täitmiseks oma sisemiste tööriistade abil.

#### Artefakt

Kui kaugagent on taotluse täitnud, luuakse tulemuseks artefakt. Artefakt sisaldab **agendi töö tulemust**, **kirjeldust täidetud ülesandest** ja **teksti konteksti**, mis saadetakse protokolli kaudu. Pärast artefakti saatmist suletakse ühendus kaugagentiga kuni järgmise vajaduseni.

#### Sündmuste järjekord

Seda komponenti kasutatakse **uuenduste haldamiseks ja sõnumite edastamiseks**. See on tootmiskeskkonnas agentide vahel olulise tähtsusega, et ära hoida ühenduse sulgemist enne ülesande lõpetamist, eriti kui ülesannete täitmine võib võtta aega.

### A2A eelised

• **Tõhustatud koostöö**: Võimaldab erinevate tarnijate ja platvormide agentidel suhelda, jagada konteksti ja teha koostööd, võimaldades sujuvat automatiseerimist traditsiooniliselt eraldatud süsteemide vahel.

• **Mudelite valikuvabadus**: Iga A2A agent saab ise valida, millist LLM-i ta oma päringute teenindamiseks kasutab, võimaldades optimeeritud või peenhäälestatud mudeleid vastavalt agendile, erinevalt mõnest MCP stsenaariumist, kus on ühendus ühe LLM-iga.

• **Sisseehitatud autentimine**: Autentimine on A2A protokolli sisse ehitatud, pakkudes tugevat turvakeskkonda agentide vahelistele suhtlustele.

### A2A näide

![A2A Diagramm](../../../translated_images/et/A2A-Diagram.8666928d648acc26.webp)

Laiendame oma reisi broneerimise stsenaariumi, kasutades seekord A2A.

1. **Kasutaja päring mitme agendiga**: Kasutaja suhtleb „Reisiagent“ A2A kliendi/agendiga, öeldes näiteks: „Palun broneeri terve reis nädalaks Honolulu, sh lennud, hotell ja autorent“.

2. **Reisiagendi korraldus**: Reisiagent saab keerulise päringu. Ta kasutab oma LLM-i, et mõista ülesannet ja otsustab, et peab suhtlema teiste eriteadmistega agentidega.

3. **Agentide vaheline suhtlus**: Reisiagent kasutab A2A protokolli, et ühenduda teiste agentidega, näiteks „Lennufirma agent“, „Hotelli agent“ ja „Autorendi agent“, kes on loodud erinevate ettevõtete poolt.

4. **Ülesannete delegeerimine**: Reisiagent saadab konkreetseid ülesandeid neile spetsiifilistele agentidele (nt „Leia lennud Honolule“, „Broneeri hotell“, „Rendi auto“). Iga spetsiifiline agent kasutab oma LLM-i ja tööriistu (mis võivad olla ise MCP serverid), et täita oma osa broneeringust.

5. **Koondatud vastus**: Kui kõik allagentid on ülesanded lõpetanud, koondab Reisiagent tulemused (lennuandmed, hotelli kinnitus, autorendi broneering) ja saadab kasutajale tervikliku vestlusstiilis vastuse.

## Loomuliku keele veeb (NLWeb)

Veebisaidid on olnud pikka aega peamine viis kasutajatel interneti-infole ja andmetele ligi pääseda.

Vaatleme NLWeb erinevaid komponente, selle eeliseid ja näidet, kuidas meie NLWeb töötab, vaadates meie reisisüsteemi.

### NLWeb komponendid

- **NLWeb rakendus (põhiteenuse kood)**: Süsteem, mis töötleb loomuliku keele küsimusi. See ühendab platvormi erinevad osad, et luua vastuseid. Seda võib mõelda kui **mootor, mis jõustab veebisaidi loomuliku keele funktsionaalsust**.

- **NLWeb protokoll**: See on **lihtne reeglistik loomuliku keele interaktsiooniks** veebisaidiga. Vastuseks saadetakse JSON-formaadis andmeid (tihti kasutades Schema.org). Selle eesmärk on luua lihtne alus „AI veebile“ samamoodi nagu HTML võimaldas dokumente internetis jagada.

- **MCP server (Model Context Protocol lõpp-punkt)**: Iga NLWeb seadistus toimib ka **MCP serverina**. See tähendab, et see võib **jagada tööriistu (nt „küsi“ meetod) ja andmeid** teiste AI süsteemidega. Tegelikkuses teeb see veebisaidi sisu ja võimekused AI agentidele kasutatavaks, võimaldades saidil saada osaks laiemast „agendi ökosüsteemist“.

- **Embedding mudelid**: Need mudelid teisendavad veebisisu numbrilisteks esitusteks ehk vektoriteks (embeddingudeks). Need vektorid püüavad tähendust viisil, mida arvutid saavad võrrelda ja otsida. Need salvestatakse spetsiaalsesse andmebaasi ning kasutajad saavad valida kasutatava embedding-mudeli.

- **Vektorandmebaas (otsimismehhanism)**: See andmebaas salvestab veebisisu embeddinguid. Kui keegi esitab küsimuse, kontrollib NLWeb vektorandmebaasi, et kiiresti leida kõige asjakohasem info. See tagastab kiiresti võimalikud vastused, järjestatuna sarnasuse alusel. NLWeb töötab erinevate vektorite salvestussüsteemidega nagu Qdrant, Snowflake, Milvus, Azure AI Search ja Elasticsearch.

### NLWeb näide

![NLWeb](../../../translated_images/et/nlweb-diagram.c1e2390b310e5fe4.webp)

Võtame taas meie reisibroneerimise veebisaidi, millel seekord jookseb NLWeb.

1. **Andmete import**: Reisi veebisaidi olemasolevaid tootekatalooge (nt lendude nimekirjad, hotellide kirjeldused, reisipaketid) vormindatakse Schema.org vastavuses või laaditakse RSS-kanalite kaudu. NLWeb tööriistad võtavad selle struktureeritud andme, loovad embeddingud ja salvestavad need lokaalsesse või kaugvektorandmebaasi.

2. **Loomuliku keele päring (inimene)**: Kasutaja külastab veebisaiti ja selle asemel, et menüüsid sirvida, kirjutab jutuliidesesse: „Leia mulle peresõbralik hotell Honolulas, kus on järgmisel nädalal bassein“.

3. **NLWeb töötlemine**: NLWeb rakendus võtab küsimuse vastu. See saadab päringu LLM-ile mõistmiseks ja otsib samal ajal oma vektorandmebaasist relevantseid hotellikataloogi vastuseid.

4. **Täpsed tulemused**: LLM aitab tõlgendada andmebaasi otsingutulemusi, tuvastada parimad sobivad vastavalt kriteeriumitele „peresõbralik“, „bassein“ ja „Honolulu“ ning vormistab loomulikus keeles vastuse. Oluline on, et vastus viitab tegelikele veebisaidi hotellidele, vältides väljamõeldud infot.

5. **AI agendi interaktsioon**: Kuna NLWeb töötab MCP serverina, võib ka väline AI reisibüroo agent selle NLWebi võrguliidesele otse ühenduda. AI agent saab kasutada `ask` MCP meetodit, et veebisaidilt andmeid pärida: `ask("Kas hotell soovitab Honolulas taimetoitusõbralikke restorane?")`. NLWeb võttaks selle vastu, kasutades oma restoraniandmebaasi (kui see on laaditud), ja saadaks struktureeritud JSON vastuse.

### Kas Sul on rohkem küsimusi MCP/A2A/NLWeb kohta?

Liitu [Microsoft Foundry Discordiga](https://aka.ms/ai-agents/discord), et kohtuda teiste õppijatega, osaleda konsultatsioonitumepäevadel ja saada vastuseid oma AI agentidega seotud küsimustele.

## Ressursid

- [MCP alustamiseks](https://aka.ms/mcp-for-beginners)  
- [MCP dokumentatsioon](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb repositoorium](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel juhendid](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastutusest loobumine**:
See dokument on tõlgitud tehisintellekti tõlketeenuse [Co-op Translator](https://github.com/Azure/co-op-translator) abil. Kuigi me püüdleme täpsuse poole, palun arvestage, et automatiseeritud tõlgetes võib esineda vigu või ebatäpsusi. Originaaldokument selle algkeeles tuleb pidada usaldusväärseks allikaks. Olulise teabe puhul soovitatakse kasutada professionaalse inimese tehtud tõlget. Me ei vastuta selle tõlke kasutamisest tingitud arusaamatuste või väärintepreteerimiste eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->