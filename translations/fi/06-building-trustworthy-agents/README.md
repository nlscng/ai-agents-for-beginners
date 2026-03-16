[![Luotettavat tekoälyagentit](../../../translated_images/fi/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klikkaa yllä olevaa kuvaa katsoaksesi tämän oppitunnin videon)_

# Luotettavien tekoälyagenttien rakentaminen

## Johdanto

Tässä oppitunnissa käsitellään:

- Kuinka rakentaa ja ottaa käyttöön turvallisia ja tehokkaita tekoälyagentteja
- Tärkeitä turvallisuusnäkökohtia tekoälyagenttien kehittämisessä.
- Kuinka ylläpitää tietojen ja käyttäjän yksityisyyttä tekoälyagentteja kehittäessä.

## Oppimistavoitteet

Tämän oppitunnin suorittamisen jälkeen osaat:

- Tunnistaa ja vähentää riskejä tekoälyagentteja luodessa.
- Toteuttaa suojaustoimenpiteitä, jotta tiedot ja käyttöoikeudet hoidetaan asianmukaisesti.
- Luoda tekoälyagentteja, jotka ylläpitävät tietosuojaa ja tarjoavat laadukkaan käyttäjäkokemuksen.

## Turvallisuus

Katsotaan ensin, miten rakennetaan turvallisia agenttipohjaisia sovelluksia. Turvallisuus tarkoittaa, että tekoälyagentti toimii suunnitellulla tavalla. Agenttisovellusten rakentajina meillä on menetelmiä ja työkaluja turvallisuuden maksimoimiseksi:

### System-viestikehyksen rakentaminen

Jos olet joskus rakentanut tekoälysovelluksen käyttäen suuria kielimalleja (LLM), tiedät vahvan system-kehotteen tai system-viestin suunnittelun tärkeyden. Nämä kehotteet asettavat metatalot, ohjeet ja ohjeistukset siitä, miten LLM toimii käyttäjän ja datan kanssa.

Tekoälyagenttien kohdalla system-kehote on vieläkin tärkeämpi, sillä tekoälyagenttien on saatava hyvin tarkat ohjeet suorittaakseen meille suunnitellut tehtävät.

Skaalautuvien system-kehotteiden luomiseksi voimme käyttää system-viestikehystä yhden tai useamman agentin rakentamiseen sovelluksessamme:

![System-viestikehyksen rakentaminen](../../../translated_images/fi/system-message-framework.3a97368c92d11d68.webp)

#### Vaihe 1: Luo meta system-viesti 

Metakehotea käyttää LLM system-kehotteiden luomiseen luomillemme agenteille. Suunnittelemme sen malliksi, jotta voimme tehokkaasti luoda useita agenteja tarvittaessa.

Tässä on esimerkki metajärjestelmäviestistä, jonka antaisimme LLM:lle:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Vaihe 2: Luo peruskehotus

Seuraavaksi luodaan peruskehotus kuvaamaan tekoälyagenttia. Siihen tulisi sisällyttää agentin rooli, agentin suorittamat tehtävät ja muut agentin vastuut.

Tässä esimerkki:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Vaihe 3: Anna perus system-viesti LLM:lle

Nyt voimme optimoida tätä system-viestiä antamalla metajärjestelmäviestin system-viestinä sekä perus system-viestin.

Tämä tuottaa paremmin suunnitellun system-viestin, joka ohjaa tekoälyagenttejamme:

```markdown
**Company Name:** Contoso Travel  
**Role:** Travel Agent Assistant

**Objective:**  
You are an AI-powered travel agent assistant for Contoso Travel, specializing in booking flights and providing exceptional customer service. Your main goal is to assist customers in finding, booking, and managing their flights, all while ensuring that their preferences and needs are met efficiently.

**Key Responsibilities:**

1. **Flight Lookup:**
    
    - Assist customers in searching for available flights based on their specified destination, dates, and any other relevant preferences.
    - Provide a list of options, including flight times, airlines, layovers, and pricing.
2. **Flight Booking:**
    
    - Facilitate the booking of flights for customers, ensuring that all details are correctly entered into the system.
    - Confirm bookings and provide customers with their itinerary, including confirmation numbers and any other pertinent information.
3. **Customer Preference Inquiry:**
    
    - Actively ask customers for their preferences regarding seating (e.g., aisle, window, extra legroom) and preferred times for flights (e.g., morning, afternoon, evening).
    - Record these preferences for future reference and tailor suggestions accordingly.
4. **Flight Cancellation:**
    
    - Assist customers in canceling previously booked flights if needed, following company policies and procedures.
    - Notify customers of any necessary refunds or additional steps that may be required for cancellations.
5. **Flight Monitoring:**
    
    - Monitor the status of booked flights and alert customers in real-time about any delays, cancellations, or changes to their flight schedule.
    - Provide updates through preferred communication channels (e.g., email, SMS) as needed.

**Tone and Style:**

- Maintain a friendly, professional, and approachable demeanor in all interactions with customers.
- Ensure that all communication is clear, informative, and tailored to the customer's specific needs and inquiries.

**User Interaction Instructions:**

- Respond to customer queries promptly and accurately.
- Use a conversational style while ensuring professionalism.
- Prioritize customer satisfaction by being attentive, empathetic, and proactive in all assistance provided.

**Additional Notes:**

- Stay updated on any changes to airline policies, travel restrictions, and other relevant information that could impact flight bookings and customer experience.
- Use clear and concise language to explain options and processes, avoiding jargon where possible for better customer understanding.

This AI assistant is designed to streamline the flight booking process for customers of Contoso Travel, ensuring that all their travel needs are met efficiently and effectively.

```

#### Vaihe 4: Toista ja paranna

Tämän system-viestikehyksen arvo on kyky skaalata useiden agenttien system-viestien luomista helposti sekä parantaa system-viestejä ajan myötä. On harvinaista, että saat täydellisen system-viestin ensimmäisellä yrittämällä täyttämään käyttötapauksen. Mahdollisuus tehdä pieniä säätöjä ja parannuksia muuttamalla perus system-viestiä ja suorittamalla se järjestelmään antaa mahdollisuuden vertailla ja arvioida tuloksia.

## Uhkien ymmärtäminen

Luotettavien tekoälyagenttien rakentamiseksi on tärkeää ymmärtää ja lieventää riskejä ja uhkia, joita tekoälyagentillesi voi kohdistua. Tarkastellaan joitakin erilaisia uhkia tekoälyagenteille ja miten niihin voi valmistautua paremmin.

![Uhkien ymmärtäminen](../../../translated_images/fi/understanding-threats.89edeada8a97fc0f.webp)

### Tehtävä ja ohjeistus

**Kuvaus:** Hyökkääjät yrittävät muuttaa tekoälyagentin ohjeita tai tavoitteita kehotteilla tai syötteiden manipuloinnilla.

**Vähentäminen**: Suorita vahvistustarkastuksia ja syötesuodattimia havaitaksesi mahdollisesti vaaralliset kehotteet ennen kuin tekoälyagentti käsittelee ne. Koska nämä hyökkäykset vaativat tyypillisesti toistuvaa vuorovaikutusta agentin kanssa, keskustelun kierrosten rajoittaminen on toinen tapa estää tällaiset hyökkäykset.

### Pääsy kriittisiin järjestelmiin

**Kuvaus**: Jos tekoälyagentilla on pääsy järjestelmiin ja palveluihin, jotka tallentavat arkaluonteista tietoa, hyökkääjät voivat vaarantaa viestinnän agentin ja näiden palveluiden välillä. Nämä voivat olla suoria hyökkäyksiä tai epäsuoria yrityksiä saada tietoa näistä järjestelmistä agentin kautta.

**Vähentäminen**: AI-agenteilla tulisi olla pääsy järjestelmiin vain tarpeen mukaan tämän tyyppisten hyökkäysten estämiseksi. Agentin ja järjestelmän välinen viestintä tulisi myös suojata. Todennuksen ja pääsynvalvonnan käyttöönotto on toinen tapa suojata tätä tietoa.

### Resurssien ja palveluiden kuormittaminen

**Kuvaus:** Tekoälyagentit voivat käyttää erilaisia työkaluja ja palveluita tehtävien suorittamiseen. Hyökkääjät voivat käyttää tätä kykyä hyökätäkseen näihin palveluihin lähettämällä suuren määrän pyyntöjä tekoälyagentin kautta, mikä voi johtaa järjestelmävirheisiin tai suuriin kustannuksiin.

**Vähentäminen:** Ota käyttöön käytännöt, joilla rajoitetaan tekoälyagentin tekemien pyyntöjen määrää palvelulle. Keskustelun kierrosten ja pyyntöjen määrän rajoittaminen tekoälyagentillesi on toinen tapa estää tämän tyyppisiä hyökkäyksiä.

### Tietopohjan myrkyttäminen

**Kuvaus:** Tämä hyökkäys ei kohdistu suoraan tekoälyagenttiin, vaan tietopohjaan ja muihin palveluihin, joita tekoälyagentti käyttää. Se voi tarkoittaa datan tai tiedon korruptiota, jota tekoälyagentti käyttää suorittaakseen tehtävän, mikä johtaa puolueellisiin tai ei-toivottuihin vastauksiin käyttäjälle.

**Vähentäminen:** Suorita säännöllisiä tarkistuksia datalle, jota tekoälyagentti käyttää työnkuluissaan. Varmista, että pääsy tähän dataan on suojattu ja että vain luotetut henkilöt voivat muuttaa sitä tämän tyyppisen hyökkäyksen välttämiseksi.

### Ketjureaktiovirheet

**Kuvaus:** Tekoälyagentit käyttävät erilaisia työkaluja ja palveluita tehtävien suorittamiseen. Hyökkääjien aiheuttamat virheet voivat johtaa muiden agenttiin kytkettyjen järjestelmien vioittumiseen, jolloin hyökkäys leviää laajemmaksi ja vaikeammaksi paikallistaa.

**Vähentäminen**: Yksi keino välttää tämä on, että tekoälyagentti toimii rajatussa ympäristössä, kuten suorittamalla tehtäviä Docker-kontissa, estäen suorat järjestelmähyökkäykset. Palautemekanismien ja uudelleenyrityksen luominen, kun tietyt järjestelmät vastaavat virheellä, on myös tapa estää laajempia järjestelmävikoj.

## Ihminen silmukassa

Toinen tehokas tapa rakentaa luotettavia tekoälyagenttijärjestelmiä on käyttää ihmistä silmukassa. Tämä luo vuon, jossa käyttäjät voivat antaa palautetta agenteille niiden toimiessa. Käyttäjät toimivat ikään kuin agenteina moniagenttisessa järjestelmässä, hyväksyen tai keskeyttäen käynnissä olevan prosessin.

![Ihminen silmukassa](../../../translated_images/fi/human-in-the-loop.5f0068a678f62f4f.webp)

Tässä on koodiesimerkki, joka käyttää AutoGenia ja näyttää, miten tämä käsite toteutetaan:

```python

# Luo agentit.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Käytä input()-funktiota saadaksesi käyttäjän syöte konsolista.

# Luo lopetusehto, joka päättää keskustelun, kun käyttäjä sanoo "APPROVE".
termination = TextMentionTermination("APPROVE")

# Luo tiimi.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Suorita keskustelu ja lähetä tulokset konsoliin.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Käytä asyncio.run(...), kun suoritat skriptissä.
await Console(stream)

```

## Yhteenveto

Luotettavien tekoälyagenttien rakentaminen vaatii huolellista suunnittelua, vankkoja turvallisuustoimia ja jatkuvaa kehitystä. Rakentamalla rakenteellisia metakehotejärjestelmiä, ymmärtämällä mahdolliset uhat ja soveltamalla lievennysstrategioita, kehittäjät voivat luoda tekoälyagentteja, jotka ovat sekä turvallisia että tehokkaita. Lisäksi ihmisen mukanaolo prosessissa varmistaa, että tekoälyagentit pysyvät käyttäjien tarpeiden mukaisina ja riskit minimoidaan. Tekoälyn kehittyessä turvallisuuden, yksityisyyden ja eettisten näkökohtien ennakoiva huomioiminen on avain luottamuksen ja luotettavuuden rakentamiseen tekoälypohjaisissa järjestelmissä.

### Onko sinulla lisää kysymyksiä luotettavien tekoälyagenttien rakentamisesta?

Liity [Microsoft Foundry Discord -yhteisöön](https://aka.ms/ai-agents/discord) tavata muita oppijoita, osallistua toimistoaikoihin ja saada vastauksia tekoälyagenttikysymyksiisi.

## Lisäresurssit

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Vastuullisen tekoälyn yleiskatsaus</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Generatiivisten tekoälymallien ja tekoälysovellusten arviointi</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Turvallisuusjärjestelmäviestit</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Riskinarviointimalli</a>

## Edellinen oppitunti

[Agenttikäyttöinen RAG](../05-agentic-rag/README.md)

## Seuraava oppitunti

[Suunnittelumalli](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastuuvapauslauseke**:
Tämä asiakirja on käännetty tekoälykäännöspalvelulla [Co-op Translator](https://github.com/Azure/co-op-translator). Pyrimme tarkkuuteen, mutta huomioithan, että automaattikäännöksissä saattaa esiintyä virheitä tai epätarkkuuksia. Alkuperäinen asiakirja sen alkuperäisellä kielellä on katsottava viralliseksi lähteeksi. Tärkeissä asioissa suositellaan ammattimaista ihmiskäännöstä. Emme ole vastuussa tämän käännöksen käytöstä aiheutuvista väärinymmärryksistä tai virhetulkinnoista.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->