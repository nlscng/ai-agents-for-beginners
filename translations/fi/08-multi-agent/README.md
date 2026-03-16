[![Moni-agenttinen suunnittelumalli](../../../translated_images/fi/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(Napsauta yllä olevaa kuvaa katsoaksesi tämän oppitunnin videon)_

# Moni-agenttiset suunnittelumallit

Heti kun alat työskennellä projektin parissa, joka sisältää useita agenteja, sinun on otettava huomioon moni-agenttinen suunnittelumalli. Kuitenkaan ei välttämättä ole heti selvää, milloin siirtyä moni-agentteihin ja mitkä ovat niiden edut.

## Johdanto

Tässä oppitunnissa pyrimme vastaamaan seuraaviin kysymyksiin:

- Missä tilanteissa moni-agentteja voidaan käyttää?
- Mitkä ovat moni-agenttien käyttämisen edut verrattuna siihen, että yksi ainoa agentti hoitaisi useita tehtäviä?
- Mitkä ovat moni-agenttisen suunnittelumallin toteutuksen rakennuspalikat?
- Miten voimme nähdä, miten useat agentit vuorovaikuttavat keskenään?

## Oppimistavoitteet

Tämän oppitunnin jälkeen sinun tulisi pystyä:

- Tunnistamaan tilanteet, joissa moni-agentteja voidaan käyttää
- Tunnistamaan moni-agenttien käytön edut verrattuna yksittäiseen agenttiin.
- Ymmärtämään moni-agenttisen suunnittelumallin toteutuksen rakennuspalikat.

Mikä on laajempi kokonaisuus?

*Moni-agentit ovat suunnittelumalli, joka mahdollistaa useiden agenttien työskentelyn yhdessä saavuttaakseen yhteisen tavoitteen*.

Tätä mallia käytetään laajalti eri aloilla, mukaan lukien robotiikka, autonomiset järjestelmät ja hajautettu laskenta.

## Tilanteet, joissa moni-agentteja voidaan käyttää

Missä tilanteissa moni-agenttien käyttö on hyvä vaihtoehto? Vastaus on, että monissa tilanteissa moni-agenttien käyttö on hyödyllistä, erityisesti seuraavissa tapauksissa:

- **Suuret työkuormat**: Suuret työkuormat voidaan jakaa pienempiin tehtäviin ja osoittaa erilaisille agenteille, mikä mahdollistaa rinnakkaisen käsittelyn ja nopeamman suorittamisen. Esimerkkinä tästä on suurten tietomäärien käsittely.
- **Monimutkaiset tehtävät**: Monimutkaiset tehtävät, kuten suuret työkuormat, voidaan pilkkoa pienempiin osatehtäviin ja osoittaa erilaisille agenteille, joista kukin erikoistuu tiettyyn osaan tehtävää. Hyvä esimerkki tästä on autonomiset ajoneuvot, joissa eri agentit hallitsevat navigointia, esteiden havaitsemista ja viestintää muiden ajoneuvojen kanssa.
- **Monipuolinen asiantuntemus**: Eri agenteilla voi olla erilainen asiantuntemus, jolloin ne voivat hoitaa tehtävän eri osa-alueita tehokkaammin kuin yksittäinen agentti. Tämän tyyppisenä esimerkkinä voidaan mainita terveydenhuolto, jossa agentit voivat hoitaa diagnostiikkaa, hoitosuunnitelmia ja potilaan seurantaa.

## Moni-agenttien käytön edut verrattuna yksittäiseen agenttiin

Yksittäinen agenttijärjestelmä voi toimia hyvin yksinkertaisissa tehtävissä, mutta monimutkaisemmissa tehtävissä moni-agenttien käyttäminen tarjoaa useita etuja:

- **Erikoistuminen**: Jokainen agentti voi erikoistua tiettyyn tehtävään. Yksittäisen agentin erikoistumattomuus tarkoittaa, että agentti voi tehdä kaikkea mutta voi olla hämmentynyt, mitä tehdä kohdatessaan monimutkaisen tehtävän. Se saattaa esimerkiksi päätyä tekemään tehtävän, johon se ei ole parhaimmillaan.
- **Laajennettavuus**: Järjestelmiä on helpompi laajentaa lisäämällä uusia agentteja kuin ylikuormittamalla yhtä agenttia.
- **Vikasietoisuus**: Jos yksi agentti epäonnistuu, muut voivat jatkaa toimintaansa, mikä takaa järjestelmän luotettavuuden.

Otetaan esimerkki: varataan käyttäjälle matka. Yksittäisen agenttijärjestelmän täytyisi hoitaa kaikki matkanvarauksen osat, lentojen etsimisestä hotellien ja vuokra-autojen varaamiseen. Tämän saavuttamiseksi yhdellä agentilla pitäisi olla työkalut kaikkien näiden tehtävien hoitamiseen. Tämä voi johtaa monimutkaiseen ja monoliittiseen järjestelmään, jota on vaikea ylläpitää ja laajentaa. Moni-agenttijärjestelmässä puolestaan voisi olla eri agentteja, jotka ovat erikoistuneet lentojen löytämiseen, hotellien ja vuokra-autojen varaamiseen. Tämä tekisi järjestelmästä modulaarisemman, helpommin ylläpidettävän ja laajennettavan.

Vertaa tätä matkatoimistoon, joka toimii pienenä perheyrityksenä verrattuna matkatoimistoon, joka toimii franchisingina. Perheyrityksessä yksi agentti hoitaisi kaikki matkanvarauksen vaiheet, kun taas franchisingissa eri agentit hoitaisivat matkanvarauksen eri osa-alueet.

## Moni-agenttisen suunnittelumallin toteutuksen rakennuspalikat

Ennen kuin voit toteuttaa moni-agenttisen suunnittelumallin, sinun on ymmärrettävä mallin rakennuspalikat.

Tehdään tämä konkreettisemmaksi katsomalla taas esimerkkiä käyttäjän matkan varaamisesta. Tässä tapauksessa rakennuspalikat voisivat sisältää:

- **Agenttien välinen kommunikointi**: Lentojen etsimisestä, hotellivarauksista ja vuokra-autoista vastaavien agenttien täytyy kommunikoida ja jakaa tietoa käyttäjän mieltymyksistä ja rajoitteista. Sinun täytyy päättää tämän kommunikoinnin protokollista ja tavoista. Konkreettisesti tämä tarkoittaa, että lentojen etsimisestä vastaavan agentin täytyy kommunikoida hotellin varaamisesta vastaavan agentin kanssa varmistaakseen, että hotelli on varattu samoille päiville kuin lento. Tämä tarkoittaa, että agenttien täytyy jakaa tietoa käyttäjän matkustusajoista, eli sinun täytyy päättää *mitkä agentit jakavat tietoa ja miten he jakavat tietoa*.
- **Koordinointimekanismit**: Agenttien täytyy koordinoida toimintaansa varmistaakseen, että käyttäjän mieltymykset ja rajoitteet täyttyvät. Käyttäjän mieltymys voi olla, että hotelli on lähellä lentokenttää, kun taas rajoite voi olla, että vuokra-autot ovat saatavilla vain lentokentällä. Tämä tarkoittaa, että hotellivarauksesta vastaavan agentin täytyy koordinoida toimintaansa vuokra-autojen varaamiseen liittyvän agentin kanssa, jotta käyttäjän mieltymykset ja rajoitteet täyttyvät. Sinun täytyy siis päättää *miten agentit koordinoivat toimintaansa*.
- **Agentin arkkitehtuuri**: Agenttien täytyy sisältää sisäinen rakenne päätöksenteolle ja oppimiselle käyttäjän kanssa tapahtuvan vuorovaikutuksen pohjalta. Tämä tarkoittaa, että lentojen etsimisestä vastaavalla agentilla täytyy olla sisäinen rakenne, joka mahdollistaa päätösten tekemisen siitä, mitä lentoja suositella käyttäjälle. Sinun täytyy siis päättää *miten agentit tekevät päätöksiä ja oppivat käyttäjän kanssa tapahtuvasta vuorovaikutuksesta*. Esimerkki siitä, miten agentti oppii ja parantaa toimintaansa, voisi olla, että lentojen etsimistä hoitava agentti voisi käyttää koneoppimismallia lentojen suosituksissa käyttäjän aikaisempien mieltymysten perusteella.
- **Näkyvyys moni-agenttisten vuorovaikutusten suhteen**: Sinun täytyy pystyä näkemään, miten useat agentit vuorovaikuttavat keskenään. Tämä tarkoittaa, että sinulla täytyy olla työkaluja ja tekniikoita agenttien toimintojen ja vuorovaikutusten seuraamiseen. Tämä voi olla esimerkiksi lokitus- ja valvontatyökalujen, visualisointityökalujen ja suorituskykymittareiden muodossa.
- **Moni-agenttiset mallit**: Moni-agenttijärjestelmiä voidaan toteuttaa eri malleilla, kuten keskitetyllä, hajautetulla ja hybridimallilla. Sinun tulee valita käyttötapaukseesi parhaiten sopiva malli.
- **Ihmisen osallistuminen**: Useimmissa tapauksissa järjestelmässä on mukana ihminen, ja sinun täytyy ohjeistaa agentteja, milloin pyytää ihmisen väliintuloa. Tämä voi esimerkiksi olla käyttäjän pyytämä tietty hotelli tai lento, jota agentit eivät ole suositelleet, tai varmistus ennen lennon tai hotellin varaamista.

## Näkyvyys moni-agenttisten vuorovaikutusten suhteen

On tärkeää, että sinulla on näkyvyys siihen, miten useat agentit vuorovaikuttavat keskenään. Tämä näkyvyys on välttämätöntä virheiden etsimisessä, optimoinnissa ja koko järjestelmän tehokkuuden varmistamisessa. Saavuttaaksesi tämän sinun täytyy olla käytössä työkaluja ja menetelmiä agenttien toimintojen ja vuorovaikutusten seuraamiseen. Tämä voi olla lokitus- ja valvontatyökaluja, visualisointityökaluja ja suorituskykymittareita.

Esimerkiksi käyttäjän matkan varaustilanteessa voitaisiin käyttää kojelautaa, joka näyttää kunkin agentin tilan, käyttäjän mieltymykset ja rajoitteet sekä agenttien väliset vuorovaikutukset. Tämä kojelauta voisi näyttää käyttäjän matkustusajat, lentojen suositukset lentojen etsintään erikoistuneelta agentilta, hotellien suositukset hotellivarauksista vastaavalta agentilta ja vuokra-autojen suositukset vuokra-autojen agentilta. Tämä antaisi selkeän näkymän siitä, miten agentit vuorovaikuttavat keskenään ja toteutuvatko käyttäjän mieltymykset ja rajoitteet.

Katsotaan kutakin näistä näkökulmista tarkemmin.

- **Lokitus- ja valvontatyökalut**: Haluat, että jokaisesta agentin suorittamasta toiminnosta tehdään lokimerkintä. Lokimerkintä voisi tallentaa tiedot agentista, joka toimenpiteen suoritti, tehdystä toiminnosta, toiminnan suoritusajankohdasta ja toiminnon tuloksesta. Tätä tietoa voidaan käyttää virheenkorjauksessa, optimoinnissa ja muussa.
- **Visualisointityökalut**: Visualisointityökalut auttavat sinua näkemään agenttien väliset vuorovaikutukset intuitiivisemmin. Esimerkiksi voitaisiin käyttää kaaviota, joka näyttää tiedon kulun agenttien välillä. Tämä voi auttaa tunnistamaan pullonkauloja, tehottomuuksia ja muita ongelmia järjestelmässä.
- **Suorituskykymittarit**: Suorituskykymittarit auttavat seuraamaan moni-agenttijärjestelmän tehokkuutta. Esimerkiksi voit mitata tehtävän suorittamiseen kulunutta aikaa, suoritetun tehtävien määrää aikayksikköä kohti ja agenttien tekemien suositusten tarkkuutta. Tämä tieto auttaa tunnistamaan parannuskohteita ja optimoimaan järjestelmää.

## Moni-agenttiset mallit

Tutustutaan konkreettisiin malleihin, joita voimme käyttää moni-agenttisissa sovelluksissa. Tässä muutamia kiinnostavia malleja, joita kannattaa harkita:

### Ryhmäkeskustelu

Tätä mallia käytetään, kun haluat luoda ryhmäkeskustelusovelluksen, jossa useat agentit voivat kommunikoida keskenään. Tyypillisiä käyttötapauksia ovat tiimityöskentely, asiakastuki ja sosiaalinen verkostoituminen.

Tässä mallissa kukin agentti edustaa käyttäjää ryhmäkeskustelussa, ja agenttien välillä vaihdetaan viestejä viestintäprotokollaa käyttäen. Agentit voivat lähettää viestejä ryhmäkeskusteluun, vastaanottaa viestejä ryhmäkeskustelusta ja vastata muiden agenttien viesteihin.

Mallin voi toteuttaa keskitetyllä arkkitehtuurilla, jossa kaikki viestit kulkevat keskuspalvelimen kautta, tai hajautetulla arkkitehtuurilla, jossa viestit vaihdetaan suoraan.

![Ryhmäkeskustelu](../../../translated_images/fi/multi-agent-group-chat.ec10f4cde556babd.webp)

### Tehtävän siirto

Tämä malli on hyödyllinen, kun haluat luoda sovelluksen, jossa useat agentit voivat siirtää tehtäviä toisilleen.

Tyypillisiä käyttötapauksia ovat asiakastuki, tehtävien hallinta ja työnkulkujen automatisointi.

Tässä mallissa jokainen agentti edustaa tehtävää tai vaihetta työnkulussa, ja agentit voivat siirtää tehtäviä toisille agenteille ennalta määriteltyjen sääntöjen perusteella.

![Tehtävän siirto](../../../translated_images/fi/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Yhteistyöhaku

Tämä malli on hyödyllinen, kun haluat luoda sovelluksen, jossa useat agentit voivat tehdä yhteistyötä käyttäjille suositusten tekemiseksi.

Miksi haluaisit, että useat agentit tekevät yhteistyötä? Koska jokaisella agentilla voi olla erilainen erikoisosaaminen, ja ne voivat osallistua suositusprosessiin eri tavoin.

Otetaan esimerkki, jossa käyttäjä haluaa suosituksen parhaasta osakkeesta ostettavaksi pörssissä.

- **Alan asiantuntija**: Yksi agentti voi olla asiantuntija tietyllä toimialalla.
- **Tekninen analyysi**: Toinen agentti voi olla teknisen analyysin asiantuntija.
- **Fundamenttianalyysi**: Ja kolmas agentti voi olla fundamenttianalyysin asiantuntija. Tekemällä yhteistyötä nämä agentit voivat tarjota käyttäjälle kattavamman suosituksen.

![Suositus](../../../translated_images/fi/multi-agent-filtering.d959cb129dc9f608.webp)

## Tilanne: Hyvitysprosessi

Kuvitellaan tilanne, jossa asiakas yrittää saada hyvityksen tuotteesta. Tässä prosessissa voi olla mukana useita agenteja, mutta jaetaan ne prosessikohtaisiin agenteihin ja yleisiin agenteihin, joita voidaan käyttää muissa prosesseissa.

**Hyvitysprosessiin liittyvät agentit**:

Seuraavat agentit voivat olla mukana hyvitysprosessissa:

- **Asiakasagentti**: Tämä agentti edustaa asiakasta ja vastaa hyvitysprosessin käynnistämisestä.
- **Myyjäagentti**: Tämä agentti edustaa myyjää ja vastaa hyvityksen käsittelystä.
- **Maksuagentti**: Tämä agentti edustaa maksuprosessia ja vastaa asiakkaan maksun hyvittämisestä.
- **Ratkaisuagentti**: Tämä agentti edustaa ratkaisuprosessia ja vastaa mahdollisten ongelmien ratkaisemisesta hyvitysprosessin aikana.
- **Sääntöjenmukaisuusagentti**: Tämä agentti edustaa sääntöjenmukaisuuden prosessia ja varmistaa, että hyvitysprosessi noudattaa sääntöjä ja käytäntöjä.

**Yleiset agentit**:

Näitä agentteja voidaan käyttää liiketoimintasi muissa osissa.

- **Toimitusagentti**: Tämä agentti edustaa toimitusprosessia ja vastaa tuotteen palauttamisesta myyjälle. Tätä agenttia voidaan käyttää sekä hyvitysprosessissa että tuotteen yleisessä toimituksessa esimerkiksi ostotapahtumassa.
- **Palautteenantaja-agentti**: Tämä agentti edustaa palautteenantoprosessia ja vastaa asiakkaan palautteen keräämisestä. Palautetta voidaan antaa milloin tahansa, ei vain hyvitysprosessin aikana.
- **Eskalaatioagentti**: Tämä agentti edustaa eskalaatioprosessia ja vastaa ongelmien siirtämisestä korkeammalle tukitasolle. Tätä agenttia voi käyttää missä tahansa prosessissa, jossa tarvitaan ongelman eskalointia.
- **Ilmoitusagentti**: Tämä agentti edustaa ilmoitusprosessia ja vastaa ilmoitusten lähettämisestä asiakkaalle eri hyvitysprosessin vaiheissa.
- **Analytiikka-agentti**: Tämä agentti edustaa analytiikkaprosessia ja vastaa hyvitysprosessiin liittyvien tietojen analysoinnista.
- **Auditointiagentti**: Tämä agentti edustaa auditointiprosessia ja vastaa hyvitysprosessin asianmukaisuuden tarkastamisesta.
- **Raportointiagentti**: Tämä agentti edustaa raportointiprosessia ja vastaa hyvitysprosessin raporttien tuottamisesta.
- **Tietämysagentti**: Tämä agentti edustaa tietämyspohjan ylläpitoa, sisältäen tietoja hyvitysprosessista. Tämä agentti voisi olla asiantunteva sekä hyvityksissä että muissa liiketoimintasi osa-alueissa.
- **Turvallisuusagentti**: Tämä agentti edustaa turvallisuusprosessia ja vastaa hyvitysprosessin turvallisuuden varmistamisesta.
- **Laatuagentti**: Tämä agentti edustaa laatuprosessia ja vastaa hyvitysprosessin laadun varmistamisesta.

Edellä on listattu melko monta agenttia sekä nimenomaan hyvitysprosessiin liittyen että yleisemmiksi agenteiksi, joita voidaan käyttää liiketoimintasi muissa osissa. Toivottavasti tämä antaa sinulle käsityksen siitä, miten voit päättää, mitä agenteja käyttää moni-agenttisessa järjestelmässäsi.

## Tehtävä

Suunnittele moni-agenttinen järjestelmä asiakastukiprosessille. Tunnista prosessiin liittyvät agentit, niiden roolit ja vastuut sekä miten ne vuorovaikuttavat keskenään. Ota huomioon sekä asiakastukiprosessiin liittyvät agentit että yleiset agentit, joita voidaan käyttää liiketoimintasi muissa osissa.
> Mieti hetki ennen kuin luet seuraavan ratkaisun, saatat tarvita enemmän agentteja kuin luulet.

> VINKKI: Mieti asiakastuen prosessin eri vaiheita ja ota huomioon myös järjestelmän tarvitsemat agentit.

## Ratkaisu

[Solution](./solution/solution.md)

## Tiedon tarkistukset

Kysymys: Milloin sinun tulisi harkita monen agentin käyttöä?

- [ ] A1: Kun sinulla on pieni työkuorma ja yksinkertainen tehtävä.
- [ ] A2: Kun sinulla on suuri työkuorma
- [ ] A3: Kun sinulla on yksinkertainen tehtävä.

[Solution quiz](./solution/solution-quiz.md)

## Yhteenveto

Tässä oppitunnissa olemme tarkastelleet monen agentin suunnittelumallia, mukaan lukien tilanteet, joissa monen agentin käyttö on tarkoituksenmukaista, monen agentin käytön etuja verrattuna yksittäiseen agenttiin, monen agentin suunnittelumallin toteuttamisen rakennuspalikoita ja miten saada näkyvyys siihen, miten useat agentit ovat vuorovaikutuksessa keskenään.

### Onko sinulla lisää kysymyksiä monen agentin suunnittelumallista?

Liity [Microsoft Foundry Discordiin](https://aka.ms/ai-agents/discord) tavata muita oppijoita, osallistua toimistoaikoihin ja saada vastauksia AI Agents -kysymyksiisi.

## Lisäresurssit

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen-suunnittelumallit</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agenttipohjaiset suunnittelumallit</a>


## Edellinen oppitunti

[Planning Design](../07-planning-design/README.md)

## Seuraava oppitunti

[Metakognitio AI-agenteissa](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastuuvapauslauseke**:
Tämä asiakirja on käännetty tekoälypohjaisella käännöspalvelulla [Co-op Translator](https://github.com/Azure/co-op-translator). Pyrimme tarkkuuteen, mutta ole hyvä ja huomioi, että automaattiset käännökset saattavat sisältää virheitä tai epätarkkuuksia. Alkuperäinen asiakirja sen omalla kielellä on virallinen lähde. Tärkeissä asioissa suositellaan ammattimaista ihmiskäännöstä. Emme ole vastuussa tämän käännöksen käytöstä mahdollisesti aiheutuvista väärinymmärryksistä tai tulkinnoista.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->