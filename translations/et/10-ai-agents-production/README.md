# AI-agentide tootmine: jälgitavus ja hindamine

[![AI-agentide tootmine](../../../translated_images/et/lesson-10-thumbnail.2b79a30773db093e.webp)](https://youtu.be/l4TP6IyJxmQ?si=reGOyeqjxFevyDq9)

Kui AI-agentid liiguvad eksperimenteerimisprototüüpide staadiumist reaalse maailma rakendusteni, muutub oluliseks nende käitumise mõistmine, jõudluse jälgimine ja väljundite süsteemne hindamine.

## Õpieesmärgid

Pärast selle tunni läbimist oskad/saad aru:
- Agendi jälgitavuse ja hindamise põhimõistetest
- Tehnikatest, kuidas parandada agentide jõudlust, kulusid ja tõhusust
- Mida ja kuidas oma AI-agente süsteemselt hinnata
- Kuidas kulusid kontrollida AI-agentide tootmisse juurutamisel
- Kuidas instrumeneerida AutoGeniga ehitatud agente

Eesmärk on anda sulle teadmised, kuidas muuta sinu "must kast" agentidest läbipaistvad, hallatavad ja usaldusväärsed süsteemid.

_**Märkus:** On oluline juurutada AI-agente, kes on turvalised ja usaldusväärsed. Vaata ka õppetundi [Usaldusväärsete AI-agentide loomine](./06-building-trustworthy-agents/README.md)._

## Jäljed ja kestad

Jälgitavustööriistad nagu [Langfuse](https://langfuse.com/) või [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry) kujutavad tavaliselt agendi käivitusi jälgedena ja kestadena.

- **Jälg (trace)** tähistab täielikku agendi ülesannet algusest lõpuni (näiteks kasutaja päringu töötlemine).
- **Kestad (spans)** on üksikud sammud jäljes (näiteks keelemudeli kutsumine või andmete pärimine).

![Jälgede puu Langfuses](https://langfuse.com/images/cookbook/example-autogen-evaluation/trace-tree.png)

Ilma jälgitavuseta võib AI-agent tunduda kui "must kast" – selle sisemine olek ja mõtlemine on hämarad, mis teeb probleemide diagnoosimise ja jõudluse optimeerimise raskeks. Jälgitavusega muutuvad agentide "klaaskastideks", pakkudes läbipaistvust, mis on usalduse loomisel ja selle kindlustamisel, et nad töötavad kavandatult, hädavajalik.

## Miks jälgitavus tootmiskeskkondades oluline on

AI-agentide ületoomine tootmiskeskkondadesse seab esile uued väljakutsed ja nõuded. Jälgitavus ei ole enam lihtsalt hea lisavõimalus, vaid kriitiline võimekus:

*   **Tõrkeotsing ja algpõhjuse analüüs:** Kui agent ebaõnnestub või toodab ootamatut väljundit, annavad jälgitavustööriistad vajalikud jäljed vea algpõhjuse täpsustamiseks. See on eriti oluline keerulistes agentides, mis võivad sisaldada mitmeid LLM-päringuid, tööriistade interaktsioone ja tingimusloogikat.
*   **Latentsus ja kulude haldamine:** AI-agentid toetuvad sageli LLM-idele ja teistele välistele API-dele, mille eest arveldatakse tokenite või päringute alusel. Jälgitavus võimaldab täpselt jälgida neid päringuid, aidates tuvastada liiga aeglasi või kulukaid operatsioone. See võimaldab meeskondadel optimeerida päringuid, valida efektiivsemaid mudeleid või ümber kujundada töövooge kulude kontrollimiseks ja hea kasutajakogemuse tagamiseks.
*   **Usaldus, turvalisus ja nõuetele vastavus:** Paljudes rakendustes on oluline tagada, et agent käituks turvaliselt ja eetiliselt. Jälgitavus annab auditeerimistee agendi tegevustest ja otsustest. Seda saab kasutada selliste probleemide avastamiseks ja leevendamiseks nagu sisendi süstimine (prompt injection), kahjuliku sisu genereerimine või isikuandmete väärkohtlemine. Näiteks saad jälgi üle vaadata, et mõista, miks agent andis teatud vastuse või kasutas spetsiifilist tööriista.
*   **Jätkuvad parendustsüklid:** Jälgatavuse andmed on iteratiivse arendusprotsessi alus. Jälgides, kuidas agent maailmas toimib, saab meeskond tuvastada parenduskohti, koguda andmeid mudelite täpsustamiseks ja valideerida muudatuste mõju. See loob tagasisideloo, kus tootmiskeskkonna teadmised veebihindamisest suunavad offline katsetusi ja täiendamist, mis viib järjest parema agentide jõudluseni.

## Olulised mõõdikud jälgimiseks

Agentide käitumise jälgimiseks ja mõistmiseks tuleks jälgida mitmesuguseid mõõdikuid ja signaale. Kuigi spetsiifilised mõõdikud võivad erineda sõltuvalt agendi eesmärgist, on mõned universaalselt olulised.

Siin on mõned kõige levinumad mõõdikud, mida jälgitavustööriistad kontrollivad:

**Latentsus:** Kui kiiresti agent vastab? Pikk ooteaeg halvendab kasutajakogemust. Sa peaksid mõõtma latentsust ülesannete ja üksikute sammude lõikes, pidades silmas agendi käivitusi. Näiteks agent, kes kulutab kõigile mudeli päringutele 20 sekundit, võiks kiirendada, kasutades kiirust mudelit või tehes mudelipäringuid paralleelselt.

**Kulud:** Mis on kulu ühe agendi käivituse kohta? AI-agentid tuginevad tihti LLM-päringutele, mis arveldatakse tokenite või väliste API-de põhjal. Tihe tööriistade kasutamine või mitmed sisendid võivad kulusid kiiresti tõsta. Näiteks, kui agent kutsub LLM-i viis korda vähese kvaliteeditõusu nimel, tuleb hinnata, kas kulu on õigustatud või saaks päringute arvu vähendada või odavamat mudelit kasutada. Reaalajas jälgimine aitab ka tuvastada ootamatuid hüppeid (nt vead, mis põhjustavad liigseid API-kordusi).

**Päringute vead:** Mitu päringut agent ebaõnnestus? See võib hõlmata API vigu või tööriistade ebaõnnestunud väljakutseid. Selleks, et muuta agent tootmises vastupidavamaks, saad seada tagavaramehhanisme või katsetada taaskäivitust. Näiteks, kui LLM-teenus A ei tööta, siis lülitud LLM-teenusele B varundusena.

**Kasutajate tagasiside:** Otse kasutaja hinnangute kogumine annab väärtuslikke teadmisi. See võib olla selged hinnangud (👍heaks/👎halb, ⭐1-5 tärni) või tekstilised kommentaarid. Püsiv negatiivne tagasiside peaks sind hoiatama, sest see näitab, et agent ei tööta ootuspäraselt.

**Kaudne kasutajate tagasiside:** Kasutajate käitumine annab kaudset tagasisidet ilma selgete hinnanguteta. See võib olla küsimuste ümber sõnastamine kohe, korduvad päringud või taaskäivituse nupule vajutamine. Näiteks, kui näed, et kasutajad küsivad korduvalt sama küsimust, on see märk, et agent ei tööta ootuspäraselt.

**Täpneus:** Kui sageli toodab agent korrektseid või soovitud tulemusi? Täpsuse määratlused võivad erineda (nt probleemide lahendamise õigsus, andmete täpsus, kasutaja rahulolu). Esimene samm on määratleda, milline edukas tulemus sinu agendi puhul välja näeb. Sa saad jälgida täpsust automaatkontrollide, hindamisskooride või ülesannete täitmise siltide kaudu. Näiteks märgistades jäljed "õnnestunud" või "ebaõnnestunud".

**Automatiseeritud hindamismõõdikud:** Sa võid kasutada ka automaatseid hindamisi. Näiteks saad LLM-i kasutada agendi väljundi hindamiseks, kas see on abistav, täpne või mitte. On ka mitmeid avatud lähtekoodiga raamatukogusid, mis aitavad hinnata agendi erinevaid aspekte. Nt [RAGAS](https://docs.ragas.io/) RAG-agentidele või [LLM Guard](https://llm-guard.com/) kahjuliku keele või sisendi süstimiste avastamiseks.

Praktikas annab nende mõõdikute kombinatsioon parima ülevaate AI-agendi seisundist. Käesolevas peatükis [näidismärkmikus](./code_samples/10_autogen_evaluation.ipynb) näitame, kuidas need mõõdikud reaalses näites välja näevad, kuid kõigepealt õpime, milline näeb välja tüüpiline hindamistoiming.

## Instrumeneeri oma agent

Jälgimisandmete kogumiseks on vaja instrumeneerida oma kood. Eesmärk on instrumeneerida agendi kood nii, et ta väljastaks jälgi ja mõõdikuid, mida saab jälgitavuse platvorm püüda, töödelda ja visualiseerida.

**OpenTelemetry (OTel):** [OpenTelemetry](https://opentelemetry.io/) on kujunenud tööstusharu standardiks LLM-jälgitavuse jaoks. See pakub API-sid, SDK-sid ja tööriistu telemeetria andmete genereerimiseks, kogumiseks ja eksportimiseks.

On palju instrumendiraamatukogusid, mis mähivad olemasolevaid agendi raamistikke ja muudavad OpenTelemetry kestade eksportimise jälgitavustööriistale lihtsaks. Allolev näide demonstreerib AutoGen agendi instrumendiks tegemist kasutades [OpenLit instrumendiraamatukogu](https://github.com/openlit/openlit):

```python
import openlit

openlit.init(tracer = langfuse._otel_tracer, disable_batch = True)
```

Selles peatükis olev [näidismärkmik](./code_samples/10_autogen_evaluation.ipynb) näitab, kuidas oma AutoGen agent instrumeneerida.

**Kestade käsitsi loomine:** Kuigi instrumendiraamatukogud annavad hea põhja, on olukordi, kus on vaja täpsemat või kohandatud infot. Sa saad käsitsi luua kestasid, et lisada kohandatud rakendusloogikat. Kõige olulisem on, et saab rikastada automaatselt või käsitsi loodud kestasid kohandatud atribuutidega (tuntud ka kui sildid või metaandmed). Need atribuudid võivad sisaldada äri-spetsiifilisi andmeid, vahepealseid arvutusi või konteksti, mis võib olla kasulik silumiseks või analüüsiks, näiteks `user_id`, `session_id` või `model_version`.

Näide jälgede ja kestade käsitsi loomisest kasutades [Langfuse Python SDK-d](https://langfuse.com/docs/sdk/python/sdk-v3):

```python
from langfuse import get_client
 
langfuse = get_client()
 
span = langfuse.start_span(name="my-span")
 
span.end()
```

## Agendi hindamine

Jälgitavus annab meile mõõdikud, aga hindamine on see protsess, kus analüüsitakse neid andmeid (ja sooritatakse teste), et määrata, kui hästi AI-agent töötab ja kuidas seda saab parandada. Teisisõnu, kui sul on need jäljed ja mõõdikud olemas, kuidas sa neid kasutad, et hinnata agenti ja teha otsuseid?

Regulaarne hindamine on oluline, sest AI-agentid on tihti mitte-determineerivad ja võivad aja jooksul areneda (uuenduste või mudeli käitumise kõikumise kaudu) – ilma hindamiseta sa ei teaks, kas sinu "tark agent" tõesti täidab hästi oma ülesannet või on ta taandunud.

AI-agentide hindamisi on kahte kategooriasse: **veebihindamine (online evaluation)** ja **offline hindamine**. Mõlemad on väärtuslikud ja täiendavad teineteist. Tavaliselt alustame offline hindamisest, sest see on minimaalne samm enne ükskõik millise agendi juurutamist.

### Offline hindamine

![Andmekogumi üksused Langfuses](https://langfuse.com/images/cookbook/example-autogen-evaluation/example-dataset.png)

See tähendab agendi hindamist kontrollitud keskkonnas, tavaliselt testandmekogumitega, mitte otsekasutaja päringutega. Sa kasutad kureeritud andmekogumeid, kus tead, milline on oodatav väljund või õige käitumine, ja käivitad oma agendi nende peal.

Näiteks kui oled loonud matemaatika sõnaprobleemide agendi, võib sul olla [testandmekogu](https://huggingface.co/datasets/gsm8k) 100 probleemiga, mille vastused on teada. Offline hindamist tehakse sageli arendamise ajal (ja see võib olla osa CI/CD töövoogudest), et kontrollida parendusi või kaitsta tagasiminekute eest. Eelis on see, et see on **korduv ja annab selged täpsuse mõõdikud, kuna on olemas tõeandmed**. Sa võid ka simuleerida kasutajapäringuid ja mõõta agendi vastuseid ideaalkommentaaride vastu või kasutada automaatseid mõõdikuid nagu eespool kirjeldatud.

Offline hindamise peamine väljakutse on tagada, et sinu testandmekogu on põhjalik ja ajakohane – agent võib hästi sooritada fikseeritud testkogul, kuid tootmises võib kokku puutuda hoopis erinevate päringutega. Seetõttu peaks testkogusid regulaarselt uuendama uutest piirsituatsioonidest ja reaalsete stsenaariumite näidetest. Kasulik on kasutada nii väikeseid "suitsuteste" kui ka suuremaid hindamiskogumeid: väikseid kiireteks kontrollideks ja suuremaid laiemate jõudlusmõõdikute jaoks.

### Veebihindamine (online evaluation)

![Jälgitavuse mõõdikute ülevaade](https://langfuse.com/images/cookbook/example-autogen-evaluation/dashboard.png)

See tähendab agendi hindamist elavas, reaalajas keskkonnas, st tegeliku kasutamise ajal tootmises. Veebihindamine hõlmab agendi jõudluse jälgimist päris kasutajate interaktsioonidel ja tulemuste pidevat analüüsi.

Näiteks võid jälgida õnnestumiste määra, kasutajate rahulolu skoori või teisi mõõdikuid reaalajas liiklusel. Veebihindamise eelis on see, et see **püüab kinni asju, mida sa laboris oodata ei pruugi** – sa saad jälgida mudelite käitumise muutusi aja jooksul (kui agendi tõhusus halveneb, kuna sisendi mustrid muutuvad) ja tabada ootamatuid päringuid või olukordi, mis testandmekogus polnud. See annab tõelise pildi sellest, kuidas agent looduses käitub.

Veebihindamine sisaldab sageli kaudse ja otsese kasutajate tagasiside kogumist, nagu mainitud, ning võib-olla varjuteste või A/B-teste (kus uus agent käivitub paralleelselt vana vastu võrdlemiseks). Väljakutse on, et reaalajas interaktsioonide jaoks võib olla keeruline saada usaldusväärseid silte või skoorisid – võid tugineda kasutajate tagasisidele või edasistele mõõdikutele (kas kasutaja klikkis tulemusele).

### Kahe meetodi kombineerimine

Veebihindamine ja offline hindamine ei välista teineteist; need täiendavad suurepäraselt üksteist. Veebijälgimise teadmisi (nt uued kasutajapäringute tüübid, millele agent halvasti vastab) saab kasutada offline testandmekogude täiustamiseks ja parandamiseks. Vastupidiselt saab offline testides hästi sooritanud agente siis kindlamalt juurutada ja reaalajas jälgida.

Tegelikult kasutavad paljud meeskonnad järgmist tsüklit:

_offline hindamine -> juurutamine -> veebijälgimine -> uute ebaõnnestumiste kogumine -> lisamine offline andmestikku -> agendi täiendamine -> kordamine_.

## Levinud probleemid

AI-agentide tootmisse viimisel võid kokku puutuda erinevate väljakutsetega. Siin on mõned tüüpilised probleemid ja võimalikud lahendused:

| **Probleem**    | **Võimalik lahendus**   |
| ------------- | ------------------ |
| AI-agent ei täida ülesandeid järjepidevalt | - Täiusta agendile antud sisendit; ole eesmärkides konkreetne.<br>- Määra, kus saab ülesandeid jaotada alamülesanneteks ja las need täidavad mitmed agentid. |
| AI-agent jääb lõpututesse tsüklitesse  | - Veendu, et on selged protsessi lõpetamise tingimused, et agent teaks, millal protsess lõpetada.<br>- Keeruliste ülesannete puhul, mis nõuavad mõtlemist ja planeerimist, kasuta suuremat ja spetsialiseeritud mudelit. |
| AI-agendi tööriistade väljakutsed ei täida hästi oma ülesandeid | - Testi ja valideeri tööriistade väljundit väljaspool agenti.<br>- Täiusta tööriistadele antud parameetreid, sisendeid ja nimetusi.  |
| Mitmeagendi süsteem ei tööta järjepidevalt | - Täiusta igale agendile antud sisendeid, et need oleksid spetsiifilised ja omavahel erinevad.<br>- Ehita hierarhiline süsteem, kasutades "liigutaja" või kontroller-agent, mis otsustab, milline agent on õige. |

Paljusid neist probleemidest saab tõhusamalt tuvastada jälgitavusega. Eespool arutletud jäljed ja mõõdikud aitavad täpselt paikneda, kus agendi töövoos probleemid tekivad, muutes silumise ja optimeerimise tõhusamaks.

## Kulude juhtimine
Siin on mõned strateegiad AI-agendi tootmisse juurutamise kulude haldamiseks:

**Väiksemate mudelite kasutamine:** Väikesed keelemudelid (SLM-id) võivad teatud agentidega seotud kasutusjuhtudel hästi toimida ning vähendavad oluliselt kulusid. Nagu eelnevalt mainitud, on parim viis hinnata ja võrrelda suuremate mudelitega nende toimivust ehitada hindamissüsteem, mis aitab mõista, kui hästi SLM teie kasutusjuhtumil toimib. Mõelge SLM-ide kasutamisele lihtsamate ülesannete puhul, nagu kavatsuse klassifitseerimine või parameetrite eraldamine, samal ajal kui keerulisema mõtlemise jaoks kasutatakse suuremaid mudeleid.

**Marsruutimudeli kasutamine:** Sarnane strateegia on kasutada mitmekesisust mudelite ja suuruste osas. Võite kasutada LLM-i/SLM-i või serverivaba funktsiooni, et marsruutida päringud keerukuse põhjal sobivaimatele mudelitele. See aitab samuti kulusid vähendada ja tagab soorituse õigete ülesannete puhul. Näiteks suunake lihtsad päringud väiksemate ja kiiremate mudelite poole ning kasutage kulukaid suuri mudeleid vaid keerukate ratsionaalsete ülesannete jaoks.

**Vastuste vahemällu salvestamine:** Üldiste päringute ja ülesannete tuvastamine ning nende vastuste ette pakkumine enne, kui nad agent-süsteemi läbivad, on hea viis vähendada sarnaste päringute hulka. Võite isegi rakendada voogu, mis määrab, kui sarnane päring on teie vahemällu salvestatud päringutele, kasutades selleks lihtsamaid AI-mudeleid. See strateegia võib oluliselt vähendada kulusid sagedaste küsimuste või tavapäraste tööprotsesside puhul.

## Vaatame, kuidas see praktikas toimib

Selles [sektsiooni näitenootebigis](./code_samples/10_autogen_evaluation.ipynb) näeme näiteid, kuidas saame kasutada jälgimisvahendeid, et meie agenti jälgida ja hinnata.


### Kas sul on veel küsimusi AI agentide tootmises?

Liitu [Microsoft Foundry Discordiga](https://aka.ms/ai-agents/discord), et kohtuda teiste õppuritega, osaleda tööaegadel ja saada vastused AI Agentide küsimustele.

## Eelmine õppetükk

[Metakognitsiooni disainimuster](../09-metacognition/README.md)

## Järgmine õppetükk

[Agent-seadustikud](../11-agentic-protocols/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastutusest loobumine**:
See dokument on tõlgitud kasutades tehisintellektil põhinevat tõlketeenust [Co-op Translator](https://github.com/Azure/co-op-translator). Kuigi püüame täpsust, palun arvestage, et automaatsel tõlkel võivad esineda vead või ebatäpsused. Originaaldokument oma emakeeles tuleks pidada autoriteetseks allikaks. Olulise teabe puhul soovitame kasutada professionaalset inimtõlget. Me ei vastuta selle tõlke kasutamisest tulenevate arusaamatuste ega valesti mõistmiste eest.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->