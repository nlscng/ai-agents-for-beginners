[![Intro to AI Agents](../../../translated_images/et/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Klõpsa ülaloleval pildil, et vaadata selle õppetunni videot)_


# Sissejuhatus tehisintellekti agentidesse ja agendi kasutusjuhtudesse

Tere tulemast kursusele "Tehisintellekti Agendid Algajatele"! See kursus annab põhiteadmisi ja praktilisi näiteid tehisintellekti agentide ehitamiseks.

Liitu <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discordi kogukonnaga</a>, et kohtuda teiste õppijate ja tehisintellekti agentide loojatega ning esitada selle kursuse kohta küsimusi.

Kursuse alustamiseks saame parema ülevaate, mis on tehisintellekti agendid ja kuidas me saame neid kasutada rakendustes ning töövoogudes, mida loome.

## Sissejuhatus

Selles õppetunnis käsitleme:

- Mis on tehisintellekti agendid ja millised on erinevad agentide tüübid?
- Millised kasutusjuhud sobivad kõige paremini tehisintellekti agentidele ja kuidas nad meid aidata saavad?
- Millised on mõned põhilised ehituskivid agentlahenduste kavandamisel?

## Õpieesmärgid
Pärast selle õppetunni läbimist peaksid suutma:

- Mõista tehisintellekti agentide mõisteid ja kuidas need erinevad teistest tehisintellekti lahendustest.
- Kasutada tehisintellekti agente kõige tõhusamalt.
- Kavandada agentlahendusi produktiivselt nii kasutajatele kui ka klientidele.

## Tehisintellekti agentide määratlus ja agentide tüübid

### Mis on tehisintellekti agendid?

Tehisintellekti agendid on **süsteemid**, mis võimaldavad **suurtel keelemudelitel (LLM-idel)** **sooritada tegevusi**, laiendades nende võimekust, andes LLM-idele **juurdepääsu tööriistadele** ja **teadmistele**.

Hajutame selle definitsiooni väiksemateks osadeks:

- **Süsteem** – Oluline on mõelda agentidele mitte ainult kui üksikule komponendile, vaid kui paljude komponentide süsteemile. Põhitase, tehisintellekti agendi komponendid on:
  - **Keskkond** – Määratletud ruum, kus tehisintellekti agent tegutseb. Näiteks kui meil oleks reisibroneerimise tehisintellekti agent, siis keskkonnaks võiks olla reisibroneerimise süsteem, mida agent kasutab ülesannete täitmiseks.
  - **Sensorid** – Keskkonnad sisaldavad teavet ja annavad tagasisidet. Tehisintellekti agendid kasutavad sensoreid selle teabe kogumiseks ja tõlgendamiseks keskkonna praeguse seisundi kohta. Reisibroneerimise agendi näites võib süsteem anda infot nagu hotelli saadavus või lendude hinnad.
  - **Aktiivaatorid** – Kui agent saab keskkonna praeguse oleku, otsustab ta hetkeülesande jaoks, millist tegevust seadistada, et keskkonda muuta. Reisibroneerimise agendi puhul võib see olla saadava toa broneerimine kasutajale.

![What Are AI Agents?](../../../translated_images/et/what-are-ai-agents.1ec8c4d548af601a.webp)

**Suured Keelemudelid** – Agentide kontseptsioon eksisteeris juba enne LLM-ide loomist. AI agentide ehitamisel LLM-idega on eelis võimes tõlgendada inimkeelt ja andmeid. See võimaldab LLM-idel tõlgendada keskkonna teavet ja koostada plaani keskkonna muutmiseks.

**Tegevuste sooritamine** – Välja AI agentide süsteemidest on LLM-id piiratud olukordades, kus tegevus on kasutaja sisendi põhjal sisu või info genereerimine. AI agentide süsteemides suudavad LLM-id täita ülesandeid, tõlgendades kasutaja soovi ning kasutades keskkonnas kättesaadavaid tööriistu.

**Juurdepääs tööriistadele** – Millistele tööriistadele LLM-l on ligipääs, määrab 1) keskkond, kus ta tegutseb, ja 2) agendi arendaja. Reisiesindaja näites on agendi tööriistad piiratud broneerimissüsteemis saadaolevate toimingutega ja/või arendaja võib seada piiranguid agendi tööriistadele, näiteks lennupiletitele.

**Mälu + Teadmised** – Mälu võib olla lühiajaline, kasutaja ja agendi omavahelise vestluse kontekstis. Pikas perspektiivis, lisaks keskkonna poolt antud infole, saab AI agent ka teadmisi teiste süsteemide, teenuste, tööriistade ja isegi teiste agentide kaudu. Reisiesindaja näites võib see teadmine olla ülevaade kasutaja reiseerelistest eelistustest kliendi andmebaasis.

### Erinevad agenditüübid

Nüüd kui meil on üldine määratlus AI agentidele, vaatame mõne kindla agenditüübi näidet ja kuidas neid rakendatakse reisibroneerimise tehisintellekti agendi puhul.

| **Agendi tüüp**               | **Kirjeldus**                                                                                                                        | **Näide**                                                                                                                                                                                                                     |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Lihtsad refleksagentid**   | Sooritavad viivitamatult tegevusi eelnevalt määratletud reeglite põhjal.                                                             | Reisiesindaja tõlgendab e-kirja konteksti ja suunab reisikaebused klienditeenindusse.                                                                                                                                          |
| **Mudelpõhised refleksagentid** | Sooritavad tegevusi maailma mudeli ja selle muudatuste põhjal.                                                                      | Reisiesindaja eelistab marsruute, kus on olnud olulisi hinnamuutusi, tuginedes ajaloolistele hinnapõhjadele.                                                                                                                  |
| **Eesmärgipõhised agentid**  | Koostavad plaane kindlate eesmärkide saavutamiseks, tõlgendades eesmärki ja määrates tegevusi selle saavutamiseks.                   | Reisiesindaja broneerib reisi, kindlustades vajaliku transpordi (auto, ühistransport, lennud) praegusest kohast sihtkohta.                                                                                                       |
| **Kasulikkuspõhised agentid** | Võtavad arvesse eelistusi ja hindavad numbriliselt kompromisse eesmärkide saavutamiseks.                                            | Reisiesindaja maksimeerib kasulikkust, kaaludes mugavust ja hinda reisi broneerimisel.                                                                                                                                         |
| **Õppivad agentid**           | Paranevad aja jooksul vastavalt tagasisidele ja korrigeerivad tegevusi.                                                             | Reisiesindaja parandab teenust, kasutades kliendi tagasisidet pärast reisi, et kohandada tulevasi broneeringuid.                                                                                                               |
| **Hiearhilised agentid**      | Sisaldavad mitut agenti kihilise süsteemina, kus kõrgema taseme agent jagab ülesandeid alamagentidele, kes täidavad neid.          | Reisiesindaja tühistab reisi, jagades ülesande vajalike broneeringute tühistamiseks alamagentidele, kes teevad tööd ja annavad tagasisidet kõrgema taseme agendile.                                                               |
| **Mitmeagendi süsteemid (MAS)** | Agendid täidavad ülesandeid iseseisvalt, kas koostöö või võistlemise korras.                                                         | Koostöö: Mitmed agendid broneerivad erinevaid reisi teenuseid nagu hotellid, lennud ja meelelahutus. Võistlus: Mitmed agendid haldavad ja võistlevad ühise hotelli broneerimiskalendri üle, et kliente hotellis majutada.         |

## Millal kasutada tehisintellekti agente

Varasemas osas kasutasime reisiesindaja näidet, et selgitada, kuidas erinevat tüüpi agente saab rakendada erinevates reisibroneerimise stsenaariumites. Jätkame selle rakendusega kogu kursuse vältel.

Vaatleme kasutusjuhtude tüüpe, mille jaoks tehisintellekti agendid on kõige sobivamad:

![Millal kasutada AI agente?](../../../translated_images/et/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Avatud probleemid** – LLM määrab vajadusel toimingud ülesande lõpuleviimiseks, kuna neid pole võimalik alati töövoogu kodeerida.
- **Mitmeastmelised protsessid** – ülesanded, mis nõuavad keerukustaset, kus agent peab kasutama tööriistu või infot mitme sammuga, mitte ühe otsinguga.
- **Ajutine parenemine** – ülesanded, mille puhul agent saab aja jooksul parandada vastavalt keskkonna või kasutajate tagasisidele, et pakkuda paremat kasulikkust.

Täiendavaid kaalutlusi tehisintellekti agentide kasutamisel käsitleme usaldusväärsete AI agentide loomise õppetunnis.

## Agentilahenduste põhitõed

### Agendi arendus

Esimene samm AI agendi süsteemi kavandamisel on määratleda tööriistad, tegevused ja käitumismustrid. Selles kursuses keskendume **Azure AI Agent Service'i** kasutamisele agentide määratlemiseks. See pakub järgmisi võimalusi:

- Valik avatud mudeleid nagu OpenAI, Mistral ja Llama
- Litsentsitud andmete kasutamine teenusepakkujate kaudu nagu Tripadvisor
- Standardiseeritud OpenAPI 3.0 tööriistade kasutamine

### Agentmodellid

Suhtlus LLM-idega toimub promptide abil. Arvestades AI agentide poolautonoomset loomust, pole alati võimalik või vajalik LLM-i käsitsi uuesti promptida pärast keskkonna muutust. Kasutame **agentmustreid**, mis võimaldavad LLM-i sessioone mitme sammu jooksul sujuvamalt hallata.

See kursus jaguneb mõnede populaarsete agentmuste vahel.

### Agentraamistikud

Agentraamistikud võimaldavad arendajatel rakendada agentmustreid koodi kaudu. Need raamistikud pakuvad malle, pistikprogramme ja tööriistu parema koostöö jaoks AI agentide vahel. Need võimalused tagavad parema jälgitavuse ja vigade tuvastamise AI agentide süsteemides.

Selles kursuses uurime teadusuuringutel põhinevat AutoGen raamistikku ning tootmises valmisolekus Semantic Kernel'i Agent raamistikku.

## Näidiskoodid

- Python: [Agentraamistik](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agentraamistik](./code_samples/01-dotnet-agent-framework.md)

## On veel küsimusi AI agentide kohta?

Liitu [Microsoft Foundry Discordiga](https://aka.ms/ai-agents/discord), et kohtuda teiste õppijatega, osaleda virtuaalsetel kontoritundidel ja saada vastused AI agentide küsimustele.

## Eelmine õppetund

[Course Setup](../00-course-setup/README.md)

## Järgmine õppetund

[Exploring Agentic Frameworks](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastutusest loobumine**:
See dokument on tõlgitud kasutades tehisintellektil põhinevat tõlketeenust [Co-op Translator](https://github.com/Azure/co-op-translator). Kuigi püüdleme täpsuse poole, palun arvestage, et automatiseeritud tõlked võivad sisaldada vigu või ebatäpsusi. Algne dokument selle emakeeles peaks olema autoriteetne allikas. Tähtsa teabe puhul soovitatakse kasutada professionaalset inimtõlget. Me ei vastuta selle tõlke kasutamisest tekkida võivate arusaamatuste või valesti mõistmiste eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->