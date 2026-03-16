# Mälu tehisintellekti agentidele 
[![Agent Memory](../../../translated_images/et/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Tehisintellekti agentide loomise ainulaadsetest eelistest rääkides käsitletakse peamiselt kahte asja: tööriistade kasutamise võime ülesannete täitmiseks ja aja jooksul paranemise võime. Mälu on enesetäiendava agendi loomise alus, mis suudab meie kasutajatele pakkuda paremaid kogemusi.

Selles õppetükis vaatleme, mis on mälu tehisintellekti agentide jaoks ja kuidas me saame seda hallata ning kasutada oma rakenduste kasuks.

## Sissejuhatus

Selles õppetükis käsitleme:

• **Tehisintellekti agendi mälu mõistmine**: Mis on mälu ja miks see agentidele oluline on.

• **Mälu rakendamine ja salvestamine**: Praktilised meetodid mälu võimaluste lisamiseks oma tehisintellekti agentidele, keskendudes lühiajalisele ja pikaajalisele mälule.

• **Tehisintellekti agentide enesetäiendamine**: Kuidas mälu võimaldab agentidel õppida varasematest suhtlustest ja aja jooksul areneda.

## Saadaval olevad rakendused

Selles õppetükis on kaks põhjalikku märkmikuõpetust:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Mälu rakendamine Mem0 ja Azure AI Search abil Semantic Kernel raamistikuga

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Struktureeritud mälu rakendamine Cognee abil, mis automaatselt ehitab teadmistegraafi, mida toetavad manused, visualiseerib graafi ja võimaldab intelligentselt otsida

## Õpieesmärgid

Pärast selle õppetüki läbimist oskad:

• **Erinevaid tehisintellekti agendi mälu tüüpe eristada**, sealhulgas töö- ehk töömälusid, lühiajalist ja pikaajalist mälu ning spetsialiseeritud vorme nagu persooni- ja episoodiline mälu.

• **Rakendada ja hallata lühiajalist ja pikaajalist mälu tehisintellekti agentidele** kasutades Semantic Kernel raamistikku, kasutades selliseid tööriistu nagu Mem0, Cognee, Whiteboard mälu ning integreerides Azure AI Search teenustega.

• **Mõista enesetäiendavate tehisintellekti agentide põhimõtteid** ja kuidas usaldusväärsed mäluhaldusmehhanismid aitavad kaasa pidevale õppimisele ja kohanemisele.

## Tehisintellekti agendi mälu mõistmine

Põhimõtteliselt viitab **mälu tehisintellekti agentide puhul mehhanismidele, mis võimaldavad neil säilitada ja meenutada teavet**. See teave võib olla üksikasjalik vestluse kohta, kasutaja eelistusi, varasemaid tegevusi või isegi õpitud mustreid.

Ilma mäluta on tehisintellekti rakendused sageli olekuta, mis tähendab, et iga suhtlus algab nullist. See viib korduva ja frustreeriva kasutajakogemuseni, kus agent "unustab" varasema konteksti või eelistused.

### Miks mälu on oluline?

Agendi intelligentsus on sügavalt seotud tema võimega meenutada ja kasutada varasemat teavet. Mälu võimaldab agentidel olla:

• **Mõtisklev**: Õppimine varasematest tegevustest ja tulemustest.

• **Interaktiivne**: Konteksti hoidmine kestva vestluse jooksul.

• **Proaktiivne ja reageeriv**: Vajaduste ennetamine või asjakohane reageerimine ajalooliste andmete põhjal.

• **Autonoomne**: Tegutsemine iseseisvalt, kasutades salvestatud teadmisi.

Mälu rakendamise eesmärk on muuta agendid **usaldusväärsemaks ja võimekamaks**.

### Mälu tüübid

#### Töömälud

Näiteks töömäluna võib mõelda paberilehe tükki, mida agent kasutab ühe jooksva ülesande või mõttekäigu ajal. See hoiab kohest teavet, mis on vajalik järgmise sammu arvutamiseks.

Tehisintellekti agentide puhul talletab töömälud sageli vestluse kõige asjakohasemat teavet, isegi kui kogu vestluslugu on pikk või lühendatud. See keskendub peamiste elementide nagu nõuded, ettepanekud, otsused ja tegevused eraldamisele.

**Töömälu näide**

Reisibroneerimise agendi puhul võib töömälud salvestada kasutaja praeguse taotluse, näiteks "Ma tahan broneerida reisi Pariisi". See konkreetne nõue hoitakse agendi vahetus kontekstis, et juhtida praegust suhtlust.

#### Lühiajaline mälu

See mälu tüüp säilitab teavet ühe vestluse või sessiooni jooksul. See on praeguse vestluse kontekst, mis võimaldab agendil viidata vestluse varasematele sammuile.

**Lühiajalise mälu näide**

Kui kasutaja küsib "Kui palju maksab lend Pariisi?" ja seejärel jätkab "Ent kuidas on majutusega seal?", tagab lühiajaline mälu, et agent teab, et "seal" viitab "Pariisi" samas vestluses.

#### Pikaajaline mälu

See on teave, mis püsib mitmete vestluste või sessioonide vahel. See võimaldab agentidel meeles pidada kasutaja eelistusi, ajaloolisi suhtlusi või üldisi teadmisi pikema aja vältel. See on oluline personaliseerimiseks.

**Pikaajalise mälu näide**

Pikaajaline mälu võib hoida meeles, et "Ben naudib suusatamist ja vabas õhus tegevusi, meeldib kohv mägivaatega ja soovib vältida keerukaid suusaradu vigastuse tõttu". See varasemast suhtlusest õpitud info mõjutab soovitusi tulevastes reisiplaneerimise sessioonides, muutes need väga isikupäraseks.

#### Persona mälu

See spetsialiseeritud mälu tüüp aitab agendil välja töötada järjepideva "isiksuse" või "persona". See võimaldab agendil mäletada üksikasju enda või ettenähtud rolli kohta, muutes suhtluse sujuvamaks ja sihipärasemaks.

**Persona mälu näide**

Kui reisibüroo agent on loodud olema "ekpert suusaplaanija", võib persona mälu seda rolli tugevdada ning mõjutada tema vastuseid nii, et need vastaksid eksperdi toonile ja teadmistele.

#### Töövoo/Episoodiline mälu

See mälu salvestab sammude jada, mida agent teeb keeruka ülesande täitmisel, sealhulgas õnnestumised ja ebaõnnestumised. See on nagu meenutada konkreetseid "episoodseid" või varasemaid kogemusi, et neist õppida.

**Episoodilise mälu näide**

Kui agent üritas broneerida konkreetse lennu, kuid see ebaõnnestus saadavuse puudumise tõttu, võib episoodiline mälu salvestada selle ebaõnnestumise, võimaldades agendil proovida alternatiivseid lende või teavitada kasutajat probleemist teadlikumal viisil järgmise katse ajal.

#### Objektimälu

See hõlmab konkreetsete objektide (nagu inimesed, kohad või esemed) ja sündmuste tuvastamist ja salvestamist vestlustest. See võimaldab agendil luua struktureeritud arusaama arutatavatest võtmeelementidest.

**Objektimälu näide**

Varasema reisi vestlusest võib agent eraldada asjad nagu "Pariis", "Eiffeli torn" ja "õhtusöök restoranis Le Chat Noir" objektidena. Järgnevas suhtluses võib agent meenutada "Le Chat Noir'i" ja pakkuda seal uut broneeringut teha.

#### Struktureeritud RAG (Retrieval Augmented Generation)

Kuigi RAG on laiem tehnika, on "Struktureeritud RAG" esile toodud kui võimas mälu tehnoloogia. See eraldab tihedat, struktureeritud teavet erinevatest allikatest (vestlused, e-kirjad, pildid) ja kasutab seda täpsuse, meenutuse ja vastuse kiiruse parandamiseks. Erinevalt klassikalisest RAG-ist, mis tugineb ainult semantilisele sarnasusele, töötab Struktureeritud RAG teabe loomuliku struktuuriga.

**Struktureeritud RAG näide**

Võrreldes märksõnade kokkusattumisega võiks Struktureeritud RAG parsida lennuandmed (sihtkoht, kuupäev, kellaaeg, lennufirma) e-kirjast ja salvestada need struktureeritud kujul. See võimaldab täpseid päringuid nagu "Millise lennu ma broneerisin Pariisi teisipäeval?"

## Mälu rakendamine ja salvestamine

Mälu rakendamine tehisintellekti agentidele hõlmab süsteemset protsessi nimega **mäluhaldus**, mis koosneb teabe genereerimisest, salvestamisest, pärimisest, integreerimisest, uuendamisest ja isegi unustamisest (või kustutamisest). Pärimine on eriti tähtis.

### Spetsialiseeritud mälu tööriistad

#### Mem0

Üks viis agentide mälu salvestamiseks ja haldamiseks on kasutada spetsiaalseid tööriistu nagu Mem0. Mem0 toimib püsiva mälukihtina, võimaldades agentidel meenutada asjakohaseid suhtlusi, salvestada kasutaja eelistusi ja faktilist konteksti ning õppida aja jooksul õnnestumistest ja ebaõnnestumistest. Idee on muuta olekutud agendid olekuga agendiks.

See töötab läbi **kahefaasilise mälu torujuhtme: eraldamine ja uuendamine**. Esiteks saadetakse agenti vestlusesse lisatud sõnumid Mem0 teenusele, mis kasutab suurt keelemudelit (LLM) vestluse ajaloo kokkuvõtmiseks ja uute mälestuste eraldamiseks. Seejärel määrab LLM-põhine uuendamisfaas, kas neid mälestusi lisada, muuta või kustutada, salvestades need hübriidandmebaasi, mis võib sisaldada vektor-, graafi- ja võtme-väärtuse andmebaase. See süsteem toetab ka erinevaid mälu tüüpe ja võib lisada graafimälu, mis haldab objektidevahelisi suhteid.

#### Cognee

Teine võimas lähenemine on kasutada **Cogneet**, mis on avatud lähtekoodiga semantiline mälu tehisintellekti agentidele, muutes struktureeritud ja struktureerimata andmed päringuteks sobivateks teadmiste graafideks, mida toetavad manused. Cognee pakub **kahepoodilist arhitektuuri**, mis ühendab vektorisarnasuse otsingu graafisuhetega, võimaldades agentidel mõista mitte ainult seda, milline teave on sarnane, vaid ka kuidas mõisted omavahel seotud on.

See paistab silma **hübriidse päringu** poolest, mis ühendab vektorisarnasuse, graafi struktuuri ja LLM põhjendamise – alates toorest tükipõhisest otsingust kuni graafiteadliku küsimuste vastamiseni. Süsteem hoiab **elavat mälu**, mis areneb ja kasvab, olles samal ajal päringutega kättesaadav kui üks ühendatud graaf, toetades nii lühiajalist sessiooni konteksti kui ka pikaajalist püsivat mälu.

Cognee märkmikuõpetus ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstreerib selle ühtse mälu kihi loomist, praktiliste näidetega erinevate andmeallikate sisselugemisest, teadmiste graafi visualiseerimisest ja päringutest eri otsingustrateegiatega, mis on kohandatud agentide konkreetsetele vajadustele.

### Mälu salvestamine RAG abil

Lisaks spetsialiseeritud mälu tööriistadele nagu mem0 , saate kasutada tugevaid otsinguteenuseid nagu **Azure AI Search mälu salvestamiseks ja pärimiseks**, eriti struktureeritud RAG jaoks.

See võimaldab teil oma agendi vastuseid siduda oma andmetega, tagades asjakohasemad ja täpsemad vastused. Azure AI Search saab kasutada kasutajapõhiste reisimälestuste, toodete kataloogide või muu valdkonnapõhise teadmiste salvestamiseks.

Azure AI Search toetab selliseid võimalusi nagu **Struktureeritud RAG**, mis on väga tõhus tiheda ja struktureeritud teabe eraldamisel ja pärimisel suurtest andmekogudest nagu vestluse ajalugu, e-kirjad või isegi pildid. See tagab traditsioonilistest tekstitükkide ja manuste lähenemistest "üliinimliku täpsuse ja meenutuse".

## Tehisintellekti agentide enesetäiustamine

Enesetäiendavate agentide tavaline mustritähendab **"teadmiste agendi"** kasutuselevõttu. See eraldi agent jälgib põhivestlust kasutaja ja peamise agendi vahel. Selle roll on:

1. **Tu vastada väärtuslikule teabele**: Määrata, kas mõni vestluse osa väärib salvestamist üldise teadmise või konkreetse kasutaja eelistusena.

2. **Eraldada ja kokku võtta**: Kranstsuda vestluse olulisem õppimine või eelistus.

3. **Salvestada teadmistebaasi**: Säilitada see eraldatud teave, sageli vektoriandmebaasis, et seda hiljem saaks pärida.

4. **Täiendada tulevasi päringuid**: Kui kasutaja alustab uut päringut, otsib teadmisteagent vajaliku salvestatud info ja lisab selle kasutaja käsule, pakkudes olulist konteksti põhieagendile (sarnaselt RAG-ile).

### Mälu optimeerimine

• **Latentsuse haldamine**: Kasutaja suhtluse kiiruse säilitamiseks võib alguses kasutada odavamat ja kiiremat mudelit, et kiiresti hinnata, kas teave on väärt salvestamist või pärimist, kutsudes keerukama eraldamis-/pärimisprotsessi esile ainult vajaduse korral.

• **Teadmistebaasi hooldus**: Kasvava teadmistebaasi puhul võib vähe kasutatud teabe viia "külma hoiustamise" alla, et kulusid hallata.

## Täiendavad küsimused agendi mälu kohta?

Liitu [Microsoft Foundry Discordiga](https://aka.ms/ai-agents/discord), et kohtuda teiste õppuritega, osaleda konsultatsioonitundides ja saada vastused oma tehisintellekti agentide küsimustele.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Austusavaldus**:
See dokument on tõlgitud tehisintellekti tõlketeenuse [Co-op Translator](https://github.com/Azure/co-op-translator) abil. Kuigi püüame täpsust, tuleb arvestada, et automaatsed tõlked võivad sisaldada vigu või ebatäpsusi. Algne dokument selle emakeeles tuleks pidada autoriteetseks allikaks. Kriitilise teabe puhul soovitatakse kasutada professionaalset inimtõlget. Me ei ole vastutavad selle tõlke kasutamisest tingitud arusaamatuste või valesti mõistmiste eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->