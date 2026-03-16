# Muisti tekoälyagenteille 
[![Agentin muisti](../../../translated_images/fi/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Kun keskustellaan tekoälyagenttien luomisen ainutlaatuisista eduista, kaksi asiaa nousevat päällimmäisinä esiin: kyky kutsua työkaluja tehtävien suorittamiseksi ja kyky parantua ajan myötä. Muisti on perustana itseään parantavien agenttien luomiselle, mikä voi tarjota parempia kokemuksia käyttäjillemme.

Tässä oppitunnissa tarkastelemme, mitä muisti tarkoittaa tekoälyagenteille ja kuinka voimme hallita ja hyödyntää sitä sovellustemme hyväksi.

## Johdanto

Tässä oppitunnissa käsitellään:

• **Tekoälyagenttien muistin ymmärtäminen**: Mitä muisti on ja miksi se on olennaista agenteille.

• **Muistin toteuttaminen ja tallentaminen**: Käytännön menetelmiä muistin lisäämiseksi tekoälyagenteille, painopisteenä lyhytaikainen ja pitkäaikainen muisti.

• **Tekoälyagenttien itseparantaminen**: Kuinka muisti mahdollistaa agenttien oppimisen aiemmista vuorovaikutuksista ja parantumisen ajan myötä.

## Saatavilla olevat toteutukset

Tämä oppitunti sisältää kaksi kattavaa muistikirjatutoriaalia:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Toteuttaa muistin käyttämällä Mem0:aa ja Azure AI Searchia Semantic Kernel -kehyksen kanssa

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Toteuttaa jäsennellyn muistin käyttämällä Cognee:tä, joka rakentaa automaattisesti upotuksiin perustuvan tietämysverkon, visualisoi verkon ja mahdollistaa älykkään noudon

## Oppimistavoitteet

Oppitunnin jälkeen osaat:

• **Erottaa eri tekoälyagenttimuistin tyypit**, mukaan lukien työmuisti, lyhytaikainen ja pitkäaikainen muisti sekä erikoistuneet muodot kuten persoonamuisti ja episodimuisti.

• **Toteuttaa ja hallita lyhytaikaista ja pitkäaikaista muistia tekoälyagenteille** käyttämällä Semantic Kernel -kehystä, hyödyntäen työkaluja kuten Mem0, Cognee, Whiteboard-muisti ja integroimalla Azure AI Searchin.

• **Ymmärtää itseään parantavien tekoälyagenttien periaatteet** ja kuinka vankka muistinhallintajärjestelmä edistää jatkuvaa oppimista ja sopeutumista.

## Tekoälyagenttien muistin ymmärtäminen

Ytimessä **muisti tekoälyagenteille tarkoittaa mekanismeja, jotka antavat niille mahdollisuuden säilyttää ja palauttaa tietoa**. Tämä tieto voi olla yksityiskohtia keskustelusta, käyttäjäasetuksista, menneistä toimista tai jopa opittuja malleja.

Ilman muistia tekoälysovellukset ovat usein tilattomia, mikä tarkoittaa, että jokainen vuorovaikutus alkaa alusta. Tämä johtaa toistuviin ja turhauttaviin käyttökokemuksiin, joissa agentti "unohtaa" aiemman kontekstin tai mieltymykset.

### Miksi muisti on tärkeää?

Agentin älykkyys on syvästi sidoksissa kykyynsä palauttaa ja hyödyntää aiempaa tietoa. Muisti antaa agenteille mahdollisuuden olla:

• **Reflektiivisiä**: Oppia menneistä toimista ja niiden tuloksista.

• **Vuorovaikutteisia**: Säilyttää kontekstin käynnissä olevan keskustelun aikana.

• **Ennakoivia ja reaktiivisia**: Ennakoida tarpeita tai vastata asianmukaisesti aiemman tiedon perusteella.

• **Autonomisia**: Toimia itsenäisemmin hyödyntämällä tallennettua tietämystä.

Muistin toteuttamisen tavoite on tehdä agenteista **luotettavampia ja kykenevämpiä**.

### Muistin tyypit

#### Työmuisti

Ajattele tätä kuin luonnospaperia, jota agentti käyttää yhden käynnissä olevan tehtävän tai ajatuksen aikana. Se pitää välittömän tiedon, joka tarvitaan seuraavan askeleen laskemiseen.

Tekoälyagenteille työmuisti usein tallentaa keskustelun kaikkein olennaisimmat tiedot, vaikka koko keskusteluhistoria olisi pitkä tai katkaistu. Se keskittyy tärkeiden elementtien erotteluun, kuten vaatimuksiin, ehdotuksiin, päätöksiin ja toimiin.

**Työmuistin esimerkki**

Matkavarauksia hoitavalla agentilla työmuisti voi tallentaa käyttäjän tämänhetkisen pyynnön, kuten "Haluan varata matkan Pariisiin". Tämä erityinen vaatimus pidetään agentin välittömässä kontekstissa ohjaamaan nykyistä vuorovaikutusta.

#### Lyhytaikainen muisti

Tämä muistin tyyppi säilyttää tietoa yhden keskustelun tai istunnon ajan. Se on nykyisen chatin konteksti, joka antaa agentin viitata takaisin aiempiin vuoropuhelukierroksiin.

**Lyhytaikaisen muistin esimerkki**

Jos käyttäjä kysyy "Kuinka paljon lento Pariisiin maksaisi?" ja seuraa kysymyksellä "Entä majoitus siellä?", lyhytaikainen muisti varmistaa, että agentti ymmärtää "siellä" viittaavan samaan keskusteluun liittyen "Parisiin".

#### Pitkäaikainen muisti

Tämä on tietoa, joka säilyy useiden keskustelujen tai istuntojen yli. Se antaa agenteille mahdollisuuden muistaa käyttäjäasetuksia, historiallisia vuorovaikutuksia tai yleistä tietoa pitkällä aikavälillä. Tämä on tärkeää personoinnissa.

**Pitkäaikaisen muistin esimerkki**

Pitkäaikainen muisti voisi tallentaa tiedon kuten "Ben nauttii laskettelusta ja ulkoilusta, pitää kahvista vuoristonäkymällä ja haluaa välttää vaativia rinteitä aiemman loukkaantumisen vuoksi". Tämä aiemmin opittu tieto vaikuttaa tuleviin suosituksiin matkasuunnittelussa, tehden niistä erittäin personoituja.

#### Persoonamuisti

Tämä erikoistunut muistityyppi auttaa agenttia kehittämään yhtenäisen "persoonallisuuden" tai roolin. Se antaa agentin muistaa yksityiskohtia itsestään tai tarkoitetusta roolistaan, tehden vuorovaikutuksista sujuvampia ja fokusoituneempia.

**Persoonamuistin esimerkki**
Jos matkatoimintoagentti on suunniteltu olemaan "asiantunteva laskettelusuunnittelija", persoonamuisti voi vahvistaa tätä roolia ja vaikuttaa vastauksiin vastaamaan asiantuntijan sävyä ja tietämystä.

#### Työnkulku/Episodimuisti

Tämä muisti tallentaa sarjan askeleita, joita agentti ottaa monimutkaisessa tehtävässä, mukaan lukien onnistumiset ja epäonnistumiset. Se on kuin tietyn "episodin" tai menneiden kokemusten muistaminen, josta voi oppia.

**Episodimuistin esimerkki**

Jos agentti yritti varata tietyn lennon mutta epäonnistui saatavuusongelman vuoksi, episodimuisti voisi kirjata tämän epäonnistumisen, jolloin agentti voi kokeilla vaihtoehtoisia lentoja tai tiedottaa käyttäjää ongelmasta tietoisemmalla tavalla myöhemmässä yrityksessä.

#### Entiteettimuisti

Tämä sisältää tiettyjen entiteettien (kuten ihmiset, paikat tai asiat) ja tapahtumien tunnistamisen ja muistamisen keskusteluista. Se antaa agentille mahdollisuuden rakentaa jäsennelty käsitys keskustelun keskeisistä elementeistä.

**Entiteettimuistin esimerkki**

Keskustelusta menneestä matkasta agentti voi erottaa entiteeteiksi "Pariisi", "Eiffel-torni" ja "illallinen Le Chat Noir -ravintolassa". Tulevassa vuorovaikutuksessa agentti voisi muistaa "Le Chat Noir" ja tarjoutua tekemään uusi varaus sinne.

#### Rakenteinen RAG (Retrieval Augmented Generation)

Vaikka RAG on laajempi tekniikka, "Rakenteinen RAG" korostetaan tehokkaana muistiteknologiana. Se erottaa tiivistä, jäsenneltyä tietoa eri lähteistä (keskustelut, sähköpostit, kuvat) ja käyttää sitä vastausten tarkkuuden, täydellisyyden ja nopeuden parantamiseen. Toisin kuin klassinen RAG, joka perustuu pelkästään semanttiseen samankaltaisuuteen, Rakenteinen RAG hyödyntää tiedon omaa rakennetta.

**Rakenteisen RAGin esimerkki**

Sen sijaan, että pelkästään osuttaisiin avainsanoihin, Rakenteinen RAG voisi jäsentää lentotiedot (määränpää, päivämäärä, aika, lentoyhtiö) sähköpostista ja tallentaa ne rakenteellisesti. Tämä mahdollistaa täsmällisiä kyselyjä kuten "Minkä lennon varasin Pariisiin tiistaina?"

## Muistin toteuttaminen ja tallentaminen

Muistin toteuttaminen tekoälyagenteille vaatii systemaattista prosessia eli **muistinhallintaa**, joka sisältää tiedon tuottamisen, tallentamisen, hakemisen, integroinnin, päivittämisen ja jopa "unohtamisen" (tai poistamisen). Noudon hallinta on erityisen keskeinen osa.

### Erikoistuneet muistityökalut

#### Mem0

Yksi tapa tallentaa ja hallita agentin muistia on käyttää erikoistuneita työkaluja kuten Mem0. Mem0 toimii pysyvänä muistikerroksena, jonka avulla agentit voivat palauttaa relevantteja vuorovaikutuksia, tallentaa käyttäjäasetuksia ja faktuaalista kontekstia sekä oppia onnistumisista ja epäonnistumisista ajan myötä. Ajatuksena on muuttaa tilattomia agenteja tilallisiksi.

Se toimii **kaksivaiheisen muistiputken kautta: uuttaminen ja päivitys**. Ensin agentin ketjuun lisätyt viestit lähetetään Mem0-palveluun, joka käyttää suurta kielimallia (LLM) keskusteluhistorian tiivistämiseen ja uusien muistojen uuttamiseen. Tämän jälkeen LLM-ohjattu päivitysvaihe päättää, lisätäänkö, muokataanko vai poistetaanko näitä muistoja, ja tallentaa ne hybriditietovarastoon, joka voi sisältää vektori-, graafi- ja avain-arvo-tietokantoja. Järjestelmä tukee myös erilaisia muistityyppejä ja voi sisältää graafimuistin entiteettien välisen suhdehallinnan varten.

#### Cognee

Toinen tehokas lähestymistapa on käyttää **Cognee**tä, avointa lähdekoodia olevaa semanttista muistia tekoälyagenteille, joka muuntaa jäsennellyn ja jäsentämättömän datan kyseltäviksi tietämysverkoiksi, joita tukevat upotukset. Cognee tarjoaa **kaksivarastorakenteen**, joka yhdistää vektoriperusteisen samankaltaisuushaun ja graafisuhteet, mahdollistaen agenteille ymmärtää paitsi mikä tieto on samankaltaista, myös miten käsitteet liittyvät toisiinsa.

Se loistaa **hybridinoudossa**, joka yhdistää vektorisamankaltaisuuden, graafirakenteen ja LLM-päättelyn - raakadatan hakemisesta graafitietoista kysymys-vastaus -toimintoihin. Järjestelmä ylläpitää **elävää muistia**, joka kehittyy ja kasvaa säilyen samalla kytkettynä yhtenäisenä tietämysverkona, tukeaen sekä lyhytaikaista istuntokontekstia että pitkäaikaista pysyvää muistia.

Cognee-muistikirjatutoriaali ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) demonstroi tämän yhtenäisen muistikerroksen rakentamista, käytännön esimerkein monipuolisten tietolähteiden ingestoimisesta, tietämysverkon visualisoinnista ja erilaisilla hakustrategioilla kyselyistä, jotka on räätälöity tiettyjen agenttitarpeiden mukaan.

### Muistin tallentaminen RAG:lla

Beyond specialized memory tools like mem0 , you can leverage robust search services like **Azure AI Search as a backend for storing and retrieving memories**, especially for structured RAG.

This allows you to ground your agent's responses with your own data, ensuring more relevant and accurate answers. Azure AI Search can be used to store user-specific travel memories, product catalogs, or any other domain-specific knowledge.

Azure AI Search supports capabilities like **Structured RAG**, which excels at extracting and retrieving dense, structured information from large datasets like conversation histories, emails, or even images. This provides "superhuman precision and recall" compared to traditional text chunking and embedding approaches.

## Tekoälyagenttien itseparantaminen

Yleinen malli itseään parantaville agenteille on erillisen **"tietoagentin"** käyttäminen. Tämä erillinen agentti tarkkailee pääkeskustelua käyttäjän ja ensisijaisen agentin välillä. Sen rooli on:

1. **Tunnistaa arvokas tieto**: Päätellä, onko jokin osa keskustelusta tallentamisen arvoista yleisenä tietona tai tiettynä käyttäjäasetuksena.

2. **Uuttaa ja tiivistää**: Tiivistää keskustelusta olennaisen oppimisen tai mieltymyksen.

3. **Tallentaa tietokantaan**: Säilöä tämä uutettu tieto tietämyskantaan, usein vektorikantaan, jotta se voidaan hakea myöhemmin.

4. **Täydentää tulevia kyselyjä**: Kun käyttäjä aloittaa uuden kyselyn, tietoagentti hakee relevantin tallennetun tiedon ja liittää sen käyttäjän kehotteeseen, tarjoten tärkeän kontekstin ensisijaiselle agentille (samankaltainen kuin RAG).

### Muistin optimoinnit

• **Viiveen hallinta**: Välttääksesi käyttäjävuorovaikutusten hidastumista, aluksi voidaan käyttää halvempaa ja nopeampaa mallia nopeasti tarkistamaan, onko tieto tallentamisen arvoista, ja kutsua monimutkaisempi uutto/hakulogiikka vain tarvittaessa.

• **Tietopohjan ylläpito**: Kasvavassa tietokannassa vähemmän käytetty tieto voidaan siirtää "kylmään varastoon" kustannusten hallitsemiseksi.

## Onko sinulla lisää kysymyksiä agenttimuistista?

Liity [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) -yhteisöön tavataksemme muita oppijoita, osallistuaksesi toimistoaikoihin ja saadaksesi vastauksia tekoälyagentteja koskeviin kysymyksiisi.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastuuvapauslauseke**:
Tämä asiakirja on käännetty käyttäen tekoälypohjaista käännöspalvelua [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, huomioithan, että automaattiset käännökset saattavat sisältää virheitä tai epätarkkuuksia. Alkuperäistä asiakirjaa sen alkuperäisellä kielellä tulisi pitää ensisijaisena ja auktoritatiivisena lähteenä. Tärkeän tiedon osalta suositellaan ammattimaista ihmiskäännöstä. Emme ole vastuussa tämän käännöksen käytöstä aiheutuvista väärinymmärryksistä tai virhetulkinnoista.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->