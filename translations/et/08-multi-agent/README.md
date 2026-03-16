[![Mitmeagendi disain](../../../translated_images/et/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Klõpsa ülaloleval pildil, et vaadata selle õppetunni videot)_

# Mitmeagendi disainimustrid

Niipea kui hakkate töötama projektiga, mis hõlmab mitut agenti, peate kaaluma mitmeagendi disainimustrit. Kuid võib-olla ei ole kohe selge, millal üle minna mitme agenti kasutamisele ja millised on eelised.

## Sissejuhatus

Selles õppetükis püüame vastata järgmistele küsimustele:

- Millistes stsenaariumites on mitmeagendid rakendatavad?
- Millised on mitme agenti kasutamise eelised võrreldes üheainsa agendiga, kes teeb mitu ülesannet?
- Millised on mitmeagendi disainimustri rakendamise ehituskivid?
- Kuidas meil on ülevaade sellest, kuidas mitmed agendid omavahel suhtlevad?

## Õpieesmärgid

Pärast seda õppetundi peaksid suutma:

- Tuvastada stsenaariumid, kus mitmeagendid on rakendatavad
- Tunnustada mitme agenti kasutamise eeliseid võrreldes üheainsa agendiga
- Mõista mitmeagendi disainimustri rakendamise ehituskive

Mis on suurem pilt?

*Mitmeagendid on disainimuster, mis võimaldab mitmel agendil töötada koos ühise eesmärgi saavutamiseks.*

See muster on laialdaselt kasutusel erinevates valdkondades, sealhulgas robootikas, autonoomsetes süsteemides ja hajutatud arvutustehnoloogias.

## Stsenaariumid, kus mitmeagendid on rakendatavad

Millised stsenaariumid on head mitmeagendi kasutamiseks? Vastus on, et on palju olukordi, kus mitme agendi rakendamine on kasulik, eriti järgmistes juhtudel:

- **Suur koormus**: Suuri töömahtusid saab jagada väiksemateks ülesanneteks ja määrata erinevatele agentidele, võimaldades paralleelprotsessimist ja kiiremat lõpetamist. Näide sellest on suur andmetöötlustöö.
- **Komplekssed ülesanded**: Kompleksseid ülesandeid, nagu suured töömahud, saab jagada väiksemateks alaufunktsioonideks ja määrata erinevatele agentidele, kellest igaüks spetsialiseerub konkreetsele aspektile. Hea näide on autonoomsed sõidukid, kus erinevad agendid haldavad navigeerimist, takistuste tuvastamist ja suhtlust teiste sõidukitega.
- **Mitmekesine ekspertiis**: Erinevatel agentidel võib olla mitmekesine ekspertiis, mis võimaldab neil käsitleda erinevaid ülesande aspekte tõhusamalt kui üks agent. Hea näide on tervishoid, kus agendid võivad hallata diagnostikat, raviplaane ja patsiendi jälgimist.

## Mitme agenti kasutamise eelised võrreldes üheainsa agendiga

Ühe agendi süsteem võib toimida hästi lihtsate ülesannete puhul, kuid keerukamate ülesannete puhul võib mitme agendi kasutamine anda mitmeid eeliseid:

- **Spetsialiseerumine**: Iga agent võib olla spetsialiseerunud konkreetsele ülesandele. Ühe agendi spetsialiseerumise puudumine tähendab, et teil on agent, kes suudab kõike teha, kuid võib keeruka ülesande korral segadusse sattuda. Ta võib näiteks lõpuks teha ülesannet, milleks ta pole kõige paremini sobiv.
- **Skaalautuvus**: Süsteeme on lihtsam skaleerida, lisades rohkem agente, kui koormata ühte agenti üle.
- **Tõrketaluvus**: Kui üks agent ebaõnnestub, võivad teised jätkata toimimist, tagades süsteemi usaldusväärsuse.

Võtame näiteks: broneerime kasutajale reisi. Ühe agendi süsteem peaks tegelema kõigi reisi broneerimise aspektidega, alates lendude leidmisest kuni hotellide ja autorentide broneerimiseni. Ühe agendi jaoks saavutamiseks peaks agentil olema tööriistad kõigi nende ülesannete haldamiseks. See võib viia keeruka ja monoliitse süsteemini, mida on raske hooldada ja skaleerida. Mitmeagendi süsteem võiks seevastu omada erinevaid agente, kes on spetsialiseerunud lendude leidmisele, hotellide broneerimisele ja autorentidele. See muudaks süsteemi modulaarsemaks, lihtsamini hooldatavaks ja skaleeritavaks.

Võrrelge seda pereettevõttena juhitava reisibürooga versus frantsiisina juhitava reisibürooga. Pereettevõttes tegeleb kogu broneerimisprotsessiga üks agent, samas kui frantsiisis on erinevad agendid, kes tegelevad erinevate broneerimisprotsessi osadega.

## Mitmeagendi disainimustri rakendamise ehituskivid

Enne kui saate mitmeagendi disainimustri rakendada, peate mõistma mustri moodustavaid ehituskive.

Teeme selle konkreetsemaks, uurides taas kasutaja reisi broneerimise näidet. Sel juhul hõlmaksid ehituskivid:

- **Agentide kommunikatsioon**: Lendude leidmise agent, hotellide broneerimise agent ja autorentide agent peavad suhtlema ja jagama teavet kasutaja eelistuste ja piirangute kohta. Peate otsustama selle suhtluse protokollide ja meetodite üle. Konkreetselt tähendab see, et lendude leidmise agent peab suhtlema hotellide broneerimise agendiga, et tagada hotell broneeritakse samadel kuupäevadel kui lend. See tähendab, et agentidel peab olema jagatud info kasutaja reisi kuupäevade kohta; peate otsustama *millised agendid infot jagavad ja kuidas nad infot jagavad*.
- **Koordineerimismehhanismid**: Agendid peavad koordineerima oma tegevusi, et tagada kasutaja eelistuste ja piirangute täitmine. Kasutaja eelistus võib olla näiteks hotell lennujaama lähedal, samas kui piirang võib olla, et autorendid on saadaval ainult lennujaamas. See tähendab, et hotellide broneerimise agent peab koordineerima autorendi agendiga, et tagada kasutaja eelistuste ja piirangute täitmine. See tähendab, et peate otsustama *kuidas agendid oma tegevusi koordineerivad*.
- **Agendi arhitektuur**: Agentidel peab olema sisemine struktuur, et teha otsuseid ja õppida oma suhtlustest kasutajaga. See tähendab, et lendude leidmise agendil peab olema sisemine struktuur, et otsustada, milliseid lende kasutajale soovitada. See tähendab, et peate otsustama *kuidas agendid otsuseid teevad ja õppivad oma suhtlustest kasutajaga*. Näited sellest, kuidas agent õpib ja paraneb, võivad olla näiteks see, et lendude leidmise agent kasutab masinõppemudelit lendude soovitamiseks kasutaja varasemate eelistuste põhjal.
- **Ülevaade mitmeagendilisest suhtlusest**: Teil peab olema ülevaade sellest, kuidas mitmed agendid omavahel suhtlevad. See tähendab, et teil peavad olema tööriistad ja tehnikad agentide tegevuste ja suhtluste jälgimiseks. See võib olla logimise ja jälgimise tööriistade, visualiseerimistööriistade ja jõudlusmõõdikute kujul.
- **Mitmeagendi mustrid**: Mitmeagendiliste süsteemide rakendamiseks on erinevaid mustreid, näiteks tsentraliseeritud, detsentraliseeritud ja hübriidse arhitektuuriga lahendused. Te peate otsustama mustri, mis kõige paremini sobib teie kasutusjuhule.
- **Inimene tsüklis**: Enamasti on protsessis inimene ja peate juhendama agente, millal küsida inimsekkumist. See võib väljenduda näiteks kasutajasõnumina, kus kasutaja soovib kindlat hotelli või lendu, mida agendid ei ole soovitanud, või kui küsitakse kinnitust enne lennu või hotelli broneerimist.

## Ülevaade mitmeagendilisest suhtlusest

Oluline on, et teil oleks ülevaade sellest, kuidas mitmed agendid omavahel suhtlevad. See ülevaade on hädavajalik silumiseks, optimeerimiseks ja kogu süsteemi toimivuse tagamiseks. Selle saavutamiseks peavad teil olema tööriistad ja tehnikad agentide tegevuste ja suhtluste jälgimiseks. See võib väljenduda logimise ja jälgimise tööriistade, visualiseerimistööriistade ja jõudlusmõõdikute kujul.

Näiteks kasutaja reisi broneerimise puhul võite omada juhtpaneeli, mis näitab iga agendi olekut, kasutaja eelistusi ja piiranguid ning agentidevahelisi suhtlusi. See juhtpaneel võib näidata kasutaja reisi kuupäevi, lendude soovitusi lendude agendi poolt, hotelle, mida soovitab hotellide agent, ja autorente, mida soovitab autorendi agent. See annab selge ülevaate sellest, kuidas agendid omavahel suhtlevad ja kas kasutaja eelistused ja piirangud on täidetud.

Vaatame neid aspekte üksikasjalikumalt.

- **Logimine ja jälgimistööriistad**: Soovite, et iga agendi tehtud tegevus oleks logitud. Logikirje võib salvestada teavet, milline agent tegevuse tegi, millise tegevuse võttis, millal see tegevus toimus ja tegevuse tulemuse. Seda teavet saab seejärel kasutada vigade otsimiseks, optimeerimiseks ja muuks.
- **Visualiseerimistööriistad**: Visualiseerimistööriistad aitavad näha agentidevahelisi suhtlusi intuitiivsemal viisil. Näiteks võite omada graafikut, mis näitab infovoogu agentide vahel. See võib aidata tuvastada kitsaskohti, ebatõhususi ja muid süsteemi probleeme.
- **Tulemusmõõdikud**: Tulemusmõõdikud aitavad jälgida mitmeagendilise süsteemi tõhusust. Näiteks võite jälgida ülesande täitmiseks kuluvat aega, täidetud ülesannete arvu ajaühikus ja agentide poolt tehtud soovituste täpsust. See teave aitab tuvastada parandamisvõimalusi ja optimeerida süsteemi.

## Mitmeagendi mustrid

Sukeldume mõnede konkreetsete mustrite juurde, mida saab kasutada mitmeagendiliste rakenduste loomiseks. Siin on mõned huvitavad mustrid, mida tasub kaaluda:

### Rühmavestlus

See muster on kasulik, kui soovite luua rühmavestluse rakenduse, kus mitu agenti saavad omavahel suhelda. Tüüpilised kasutusjuhud sisaldavad meeskonnatööd, kliendituge ja sotsiaalset võrgustumist.

Selles mustris esindab iga agent ühte kasutajat rühmavestluses ning sõnumeid vahetatakse agentide vahel sõnumivahetuse protokolli kaudu. Agendid saavad saata sõnumeid rühmavestlusesse, vastu võtta rühmavestlusest sõnumeid ja vastata teiste agentide sõnumitele.

Seda mustrit saab rakendada tsentraliseeritud arhitektuuri abil, kus kõik sõnumid suunatakse läbi keskserveri, või detsentraliseeritud arhitektuuri abil, kus sõnumeid vahetatakse otse.

![Rühmavestlus](../../../translated_images/et/multi-agent-group-chat.ec10f4cde556babd.webp)

### Üleandmine

See muster on kasulik, kui soovite luua rakenduse, kus mitu agenti saavad omavahel ülesandeid üle anda.

Tüüpilised kasutusjuhud hõlmavad kliendituge, ülesannete haldust ja töövoo automatiseerimist.

Selles mustris esindab iga agent ülesannet või töövoo sammu ning agendid saavad määratud reeglite alusel ülesandeid teistele agentidele üle anda.

![Tööde üleandmine](../../../translated_images/et/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Koostööpõhine filtreerimine

See muster on kasulik, kui soovite luua rakenduse, kus mitu agenti saavad teha koostööd, et pakkuda kasutajatele soovitusi.

Miks soovite, et mitu agenti teeksid koostööd? Sest iga agent võib omada erinevat ekspertiisi ja anda soovitusprotsessi erineva panuse.

Võtame näiteks olukorra, kus kasutaja soovib soovitust parimaaktsia ostmiseks aktsiaturul.

- **Tööstuse ekspert**: Üks agent võib olla konkreetse tööstusharu ekspert.
- **Tehniline analüüs**: Teine agent võib olla tehnilise analüüsi ekspert.
- **Fundamentaalne analüüs**: Ja kolmas agent võib olla fundamentaalse analüüsi ekspert. Koostöös saavad need agendid pakkuda kasutajale põhjalikumat soovitust.

![Soovitus](../../../translated_images/et/multi-agent-filtering.d959cb129dc9f608.webp)

## Stsenaarium: tagasimakse protsess

Kujutage ette stsenaariumi, kus klient üritab saada toote eest tagasimakset. Selle protsessi puhul võib olla kaasatud üsna mitu agenti, kuid jagame need protsessispetsiifilisteks agentideks ja üldisteks agentideks, keda saab kasutada ka teistes protsessides.

**Protsessispetsiifilised agentid tagasimakse jaoks**:

Järgnevad on mõned agendid, kes võivad olla kaasatud tagasimakse protsessi:

- **Kliendiagent**: See agent esindab klienti ja vastutab tagasimakse protsessi algatamise eest.
- **Müüjaagent**: See agent esindab müüjat ja vastutab tagasimakse töötlemise eest.
- **Makseagent**: See agent esindab makseprotsessi ja vastutab kliendi makse tagastamise eest.
- **Lahendusagent**: See agent esindab lahenduse protsessi ja vastutab kõigi tagasimakse protsessi käigus tekkinud probleemide lahendamise eest.
- **Vastavusagent**: See agent esindab vastavuse protsessi ja vastutab selle eest, et tagasimakse protsess vastaks eeskirjadele ja poliitikatele.

**Üldised agendid**:

Neid agente saab kasutada teie äri teiste osade poolt.

- **Saatmisagent**: See agent esindab saatmisprotsessi ja vastutab toote tagastamise saatmise eest müüjale. Seda agenti saab kasutada nii tagasimakse protsessis kui ka üldises toote saatmises näiteks ostu puhul.
- **Tagasisideagent**: See agent esindab tagasiside protsessi ja vastutab kliendilt tagasiside kogumise eest. Tagasisidet võidakse koguda igal ajal, mitte ainult tagasimakse protsessi ajal.
- **Eskalatsiooniagent**: See agent esindab eskalatsiooni protsessi ja vastutab probleemide eskaleerimise eest kõrgemale tugitasemele. Seda tüüpi agenti saab kasutada mis tahes protsessi puhul, kus on vaja teemat eskaleerida.
- **Teavituseagent**: See agent esindab teavituse protsessi ja vastutab kliendi teavitamise eest tagasimakse protsessi eri etappides.
- **Analüüsiagent**: See agent esindab analüüsi protsessi ja vastutab tagasimakse protsessiga seotud andmete analüüsimise eest.
- **Auditagent**: See agent esindab auditi protsessi ja vastutab tagasimakse protsessi auditeerimise eest, et tagada selle korrektne teostamine.
- **Aruandlusagent**: See agent esindab aruandluse protsessi ja vastutab raportite genereerimise eest tagasimakse protsessi kohta.
- **Teadmisteagent**: See agent esindab teadmiste protsessi ja vastutab tagasimakse protsessiga seotud teabe teadmistebaasi hooldamise eest. See agent võib omada teadmisi nii tagasimaksetest kui ka muudest teie äri valdkondadest.
- **Turbeagent**: See agent esindab turbe protsessi ja vastutab tagasimakse protsessi turvalisuse tagamise eest.
- **Kvaliteediagent**: See agent esindab kvaliteedi protsessi ja vastutab tagasimakse protsessi kvaliteedi tagamise eest.

Nimetatud agentide hulk on üsna suur nii spetsiifiliste tagasimakse agentide kui ka üldiste agentide osas, keda saab kasutada teie äri teistes osades. Loodetavasti annab see teile ülevaate, kuidas otsustada, milliseid agente kasutada oma mitmeagendilises süsteemis.

## Ülesanne

Kavandage mitmeagendiline süsteem klienditoe protsessi jaoks. Tuvastage protsessis osalevad agendid, nende rollid ja vastutusvaldkonnad ning kuidas nad omavahel suhtlevad. Arvestage nii klienditoega seotud spetsiifilisi agente kui ka üldisi agente, keda saab kasutada teie ettevõtte teiste osade jaoks.
> Mõtle enne, kui loed järgmist lahendust — sul võib vaja minna rohkem agente, kui arvad.
> Vihje: Mõtle klienditoe protsessi erinevatele etappidele ja ka sellele, milliseid agente iga süsteem vajab.

## Lahendus

[Lahendus](./solution/solution.md)

## Teadmiskontrollid

Question: Millal peaksid kaaluma mitmeagendi kasutamist?

- [ ] A1: Kui sul on väike töökoormus ja lihtne ülesanne.
- [ ] A2: Kui sul on suur töökoormus
- [ ] A3: Kui sul on lihtne ülesanne.

[Lahenduse viktoriin](./solution/solution-quiz.md)

## Kokkuvõte

Selles õppetükis käsitlesime mitmeagendi disainimustrit — sealhulgas olukordi, kus mitmeagendiline lähenemine on kohane, mitmeagendi kasutamise eeliseid võrreldes üheainsa agendiga, mitmeagendi disainimustri rakendamise ehitusplokke ning seda, kuidas saada ülevaadet, kuidas mitmed agendid omavahel suhtlevad.

### Kas sul on veel küsimusi mitmeagendi disainimustri kohta?

Liitu [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) et kohtuda teiste õppuritega, osaleda konsultatsioonitundides ja saada vastused oma AI agentide küsimustele.

## Täiendavad ressursid

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen disainimustrid</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentikesksed disainimustrid</a>


## Eelmine õppetund

[Planeerimise disain](../07-planning-design/README.md)

## Järgmine õppetund

[Metakognitsioon tehisintellekti agentides](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Lahtiütlus**:
See dokument on tõlgitud tehisintellekti tõlke-teenuse [Co-op Translator](https://github.com/Azure/co-op-translator) abil. Kuigi püüame tagada täpsust, palun arvestage, et automatiseeritud tõlked võivad sisaldada vigu või ebatäpsusi. Originaaldokumenti selle emakeeles tuleks pidada autoriteetseks allikaks. Olulise teabe puhul soovitatakse kasutada professionaalset inimtõlget. Me ei vastuta ühegi arusaamatuse või valesti tõlgendamise eest, mis võib tuleneda selle tõlke kasutamisest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->