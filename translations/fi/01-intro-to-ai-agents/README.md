[![Johdatus tekoälyagentteihin](../../../translated_images/fi/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(Napsauta yllä olevaa kuvaa nähdäksesi tämän oppitunnin videon)_


# Johdatus tekoälyagentteihin ja agenttien käyttötapauksiin

Tervetuloa kurssille "Tekoälyagentit aloittelijoille"! Tämä kurssi tarjoaa perustietoa ja käytännön esimerkkejä tekoälyagenttien rakentamiseen.

Liity <a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI Discord -yhteisö</a> tapaamaan muita opiskelijoita ja tekoälyagenttien rakentajia sekä kysymään kurssiin liittyviä kysymyksiä.

Aloittaaksemme tämän kurssin tarkastelemme, mitä tekoälyagentit ovat ja miten voimme käyttää niitä sovelluksissa ja työnkuluissa, joita rakennamme.

## Johdanto

Tämä oppitunti käsittelee:

- Mitä tekoälyagentit ovat ja mitkä ovat eri agenttityypit?
- Mille käyttötapauksille tekoälyagentit sopivat parhaiten ja miten ne voivat auttaa meitä?
- Mitkä ovat perusrakenteet agenttisiin ratkaisuihin suunnittelussa?

## Oppimistavoitteet
Oppitunnin suorittamisen jälkeen sinun pitäisi pystyä:

- Ymmärtämään tekoälyagenttien käsitteet ja miten ne eroavat muista AI-ratkaisuista.
- Käyttämään tekoälyagentteja tehokkaimmin.
- Suunnittelemaan agenttiperustaisia ratkaisuja tuottavasti sekä käyttäjille että asiakkaille.

## Tekoälyagenttien määrittely ja agenttityypit

### Mitä ovat tekoälyagentit?

Tekoälyagentit ovat **järjestelmiä**, jotka mahdollistavat **suuret kielimallit (LLMs)** suorittamaan **toimintoja** laajentamalla niiden kyvykkyyksiä antamalla LLM:ille **pääsyn työkaluihin** ja **tietoon**.

Pilkotaan tätä määritelmää pienempiin osiin:

- **Järjestelmä** - On tärkeää ajatella agenteja ei vain yhtenä komponenttina, vaan monen komponentin järjestelmänä. Perustasolla tekoälyagentin komponentit ovat:
  - **Ympäristö** - Määritelty tila, jossa tekoälyagentti toimii. Esimerkiksi, jos meillä olisi matkavarauksen tekoälyagentti, ympäristö voisi olla varausjärjestelmä, jota agentti käyttää tehtävien suorittamiseen.
  - **Sensorit** - Ympäristöt sisältävät tietoa ja antavat palautetta. Tekoälyagentit käyttävät sensoreita kerätäkseen ja tulkitakseen tätä tietoa ympäristön nykytilasta. Matkavarauksen agentti esimerkiksi saa varausjärjestelmästä tietoa kuten hotellien saatavuudesta tai lentojen hinnoista.
  - **Actuators** - Kun tekoälyagentti vastaanottaa ympäristön nykytilan, se määrittää kulloisessakin tehtävässä, mitä toimintoa suoritetaan ympäristön muuttamiseksi. Matkavarauksen agentin tapauksessa se voisi olla käyttäjälle varattavan saatavilla olevan huoneen varaaminen.

![Mitä ovat tekoälyagentit?](../../../translated_images/fi/what-are-ai-agents.1ec8c4d548af601a.webp)

**Suuret kielimallit** - Agenttien käsite oli olemassa ennen LLM:ien syntyä. LLM:ien käyttö agenttien rakentamisessa tarjoaa etuna niiden kyvyn tulkita ihmiskieltä ja dataa. Tämä kyky mahdollistaa LLM:ien tulkitsemaan ympäristötietoa ja määrittelemään suunnitelman ympäristön muuttamiseksi.

**Toimintojen suorittaminen** - Muunlaisissa järjestelmissä LLM:ien toiminta rajoittuu sisällön tai tiedon tuottamiseen käyttäjän kehotteen perusteella. Agenttijärjestelmissä LLM:t voivat toteuttaa tehtäviä tulkitsemalla käyttäjän pyynnön ja käyttämällä ympäristössä saatavilla olevia työkaluja.

**Pääsy työkaluihin** - Mitä työkaluja LLM:illä on käytettävissään, määrittelevät 1) ympäristö, jossa se toimii, ja 2) tekoälyagentin kehittäjä. Matkavarauksen esimerkissä agentin työkalut rajoittuvat varausjärjestelmässä saatavilla oleviin toimintoihin, ja/tai kehittäjä voi rajoittaa agentin työkalupääsyä vaikkapa vain lentoihin.

**Muisti+Tieto** - Muisti voi olla lyhytaikaista keskustelun kontekstissa käyttäjän ja agentin välillä. Pitkäaikaisesti, ympäristön antaman tiedon ulkopuolella, tekoälyagentit voivat myös hakea tietoa muista järjestelmistä, palveluista, työkaluista ja jopa muilta agenteilta. Matkavarauksen esimerkissä tämä tieto voi olla käyttäjän matkustusehtoja koskevia tietoja asiakasrekisteristä.

### Eri agenttityypit

Nyt kun meillä on yleinen määritelmä tekoälyagenteista, katsotaan joitakin erityisiä agenttityyppejä ja miten niitä sovellettaisiin matkavarauksen tekoälyagenttiin.

| **Agenttityyppi**            | **Kuvaus**                                                                                                                            | **Esimerkki**                                                                                                                                                                                                                 |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Yksinkertaiset refleksiagentit**      | Suorittavat välittömiä toimintoja ennalta määriteltyjen sääntöjen perusteella.                                                       | Matka-agentti tulkitsee sähköpostin kontekstin ja ohjaa matkaklousitukset asiakaspalveluun.                                                                                                                                    |
| **Mallipohjaiset refleksiagentit** | Suorittavat toimintoja maailman mallin ja mallin muutosten perusteella.                                                              | Matka-agentti priorisoi reittejä, joilla on merkittäviä hintamuutoksia, perustuen pääsyyn historiallisiin hintatietoihin.                                                                                                     |
| **Tavoitepohjaiset agentit**         | Laativat suunnitelmia tiettyjen tavoitteiden saavuttamiseksi tulkitsemalla tavoitteen ja määrittämällä toimet sen saavuttamiseksi. | Matka-agentti varaa matkan määrittämällä tarvittavat matkajärjestelyt (auto, julkinen liikenne, lennot) nykyisestä sijainnista määränpäähän.                                                                                    |
| **Hyötyarvopohjaiset agentit**      | Ottavat huomioon mieltymykset ja punnitsevat kompromisseja numeerisesti tavoitteiden saavuttamiseksi.                               | Matka-agentti maksimoi hyötyä punnitsemalla mukavuuden versus kustannuksen varauksen tekemisessä.                                                                                                                             |
| **Oppivat agentit**           | Parantavat toimintaansa ajan myötä reagoimalla palautteeseen ja säätämällä toimintojaan sen mukaisesti.                               | Matka-agentti paranee käyttämällä asiakkaiden palautetta jälkikyselyistä tehdäkseen muutoksia tuleviin varauksiin.                                                                                                           |
| **Hierarkkiset agentit**       | Sisältävät useita agentteja kerrostetussa järjestelmässä, jossa korkeammat agentit jakavat tehtäviä ala-agenttien suorittamiksi.     | Matka-agentti peruuttaa matkan jakamalla tehtävän osatehtäviin (esimerkiksi tiettyjen varausten peruuttaminen) ja antamalla ala-agenttien suorittaa ne sekä raportoida takaisin korkeamman tason agentille.                       |
| **Moniagenttijärjestelmät (MAS)** | Agentit suorittavat tehtäviä itsenäisesti, joko yhteistyössä tai kilpaillen.                                                         | Yhteistyö: Useat agentit varaavat tiettyjä matkapalveluita, kuten hotelleja, lentoja ja viihdettä. Kilpailu: Useat agentit hallinnoivat ja kilpailevat jaetusta hotellivarauskalenterista pöytäkirjassa varatakseen asiakkaat hotelliin. |

## Milloin käyttää tekoälyagentteja

Aiempaan osioon käytimme matkavarauksen käyttötapausta selittääksemme, miten eri agenttityyppejä voidaan käyttää erilaisissa matkavarauksen tilanteissa. Jatkamme tämän sovelluksen käyttämistä koko kurssin ajan.

Katsotaan, millaisiin käyttötapauksiin tekoälyagentit soveltuvat parhaiten:

![Milloin käyttää tekoälyagentteja?](../../../translated_images/fi/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Avoimet ongelmat** - antaa LLM:in määrittää tarvittavat vaiheet tehtävän suorittamiseksi, koska kaikkia vaiheita ei voi aina kovakoodata työnkulkuun.
- **Monivaiheiset prosessit** - tehtävät, jotka vaativat riittävää monimutkaisuutta siten, että agentin täytyy käyttää työkaluja tai tietoa useiden kierrosten aikana yhden haun sijaan.  
- **Parantuminen ajan myötä** - tehtävät, joissa agentti voi parantua ajan myötä saamalla palautetta joko ympäristöstä tai käyttäjiltä tarjotakseen paremman hyödyn.

Käsittelemme lisää tekoälyagenttien käyttöön liittyviä huomioita oppitunnissa Rakentamalla luotettavia tekoälyagentteja.

## Agenttiperustaisten ratkaisujen perusteet

### Agentin kehittäminen

Ensimmäinen askel tekoälyagenttijärjestelmän suunnittelussa on määrittää työkalut, toiminnot ja käyttäytymiset. Tässä kurssissa keskitymme käyttämään Azure AI Agent Serviceä agenttiemme määrittelyyn. Se tarjoaa ominaisuuksia kuten:

- Avoimien mallien valinta, esimerkiksi OpenAI, Mistral ja Llama
- Lisensoidun datan käyttö palveluntarjoajien kautta, esimerkiksi Tripadvisor
- Standardoitujen OpenAPI 3.0 -työkalujen käyttö

### Agenttiperustaiset mallit

Viestintä LLM:ien kanssa tapahtuu kehotteiden avulla. Ottaen huomioon tekoälyagenttien puolittain itsenäisen luonteen, ei aina ole mahdollista tai tarpeen kehottaa LLM:ää uudelleen manuaalisesti ympäristön muuttuessa. Käytämme **agenttiperustaisia malleja**, jotka mahdollistavat LLM:ään kehotteiden antamisen useiden vaiheiden kautta skaalautuvammalla tavalla.

Tämä kurssi on jaettu joihinkin nykyisin suosittuihin agenttiperustaisiin malleihin.

### Agenttiperustaiset kehykset

Agenttiperustaiset kehykset antavat kehittäjille mahdollisuuden toteuttaa agenttiperustaisia malleja koodin avulla. Nämä kehykset tarjoavat malleja, laajennuksia ja työkaluja paremman agenttien yhteistyön tukemiseksi. Nämä edut tarjoavat paremmat mahdollisuudet agenttijärjestelmien havaittavuuteen ja vianmääritykseen.

Tässä kurssissa tutkimme tutkimuspohjaista AutoGen-kehystä ja tuotantovalmista Agent-kehystä Semantic Kerneliltä.

## Esimerkkikoodit

- Python: [Agenttikehys](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Agenttikehys](./code_samples/01-dotnet-agent-framework.md)

## Onko sinulla lisää kysymyksiä tekoälyagenteista?

Liity [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) tapaamaan muita opiskelijoita, osallistumaan office hour -tilaisuuksiin ja saadaksesi vastauksia tekoälyagentteja koskeviin kysymyksiisi.

## Edellinen oppitunti

[Kurssin asetukset](../00-course-setup/README.md)

## Seuraava oppitunti

[Agenttiperustaisten kehysten tutkiminen](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Vastuuvapauslauseke:
Tämä asiakirja on käännetty tekoälypohjaisella käännöspalvelulla [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, huomioithan, että automaattisissa käännöksissä voi esiintyä virheitä tai epätarkkuuksia. Alkuperäistä asiakirjaa sen alkuperäiskielellä tulee pitää ratkaisevana lähteenä. Kriittisten tietojen osalta suositellaan ammattikääntäjän tekemää käännöstä. Emme ole vastuussa tämän käännöksen käytöstä aiheutuvista väärinymmärryksistä tai virheellisistä tulkinnoista.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->