[![Planning Design Pattern](../../../translated_images/fi/lesson-7-thumbnail.f7163ac557bea123.webp)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(Napsauta yllä olevaa kuvaa nähdäksesi tämän oppitunnin videon)_

# Suunnittelumalli

## Johdanto

Tässä oppitunnissa käsitellään

* Selkeän yleistavoitteen määrittäminen ja monimutkaisen tehtävän jakaminen hallittaviin tehtäviin.
* Jäsennellyn tulosteen hyödyntäminen luotettavampien ja koneellisesti luettavien vastausten saamiseksi.
* Tapahtumapohjaisen lähestymistavan soveltaminen dynaamisten tehtävien ja odottamattomien syötteiden käsittelemiseksi.

## Oppimistavoitteet

Kun olet suorittanut tämän oppitunnin, ymmärrät:

* Miten tunnistaa ja asettaa tekoälyagentille yleinen tavoite, varmistaen, että se tietää selkeästi, mitä tulee saavuttaa.
* Kuinka purkaa monimutkainen tehtävä hallittaviin alatavoitteisiin ja järjestää ne loogiseksi sarjaksi.
* Kuinka varustaa agentit oikeilla työkaluilla (esim. hakutyökalut tai data-analytiikkatyökalut), päättää milloin ja miten niitä käytetään sekä käsitellä odottamattomia tilanteita.
* Kuinka arvioida alatavoitteiden tuloksia, mitata suorituskykyä ja toistaa toimenpiteitä lopputuloksen parantamiseksi.

## Yleistavoitteen määrittäminen ja tehtävän jäsentäminen

![Defining Goals and Tasks](../../../translated_images/fi/defining-goals-tasks.d70439e19e37c47a.webp)

Useimmat todellisen maailman tehtävät ovat liian monimutkaisia hoidettavaksi yhdellä askeleella. Tekoälyagentilla tulee olla ytimekäs tavoite, joka ohjaa sen suunnittelua ja toimia. Esimerkiksi tavoite:

    "Luo 3 päivän matkasuunnitelma."

Vaikka se on yksinkertainen ilmaista, sitä tulee silti tarkentaa. Mitä selkeämpi tavoite on, sitä paremmin agentti (ja kaikki ihmistyöntekijät) voivat keskittyä saavuttamaan oikean lopputuloksen, kuten kattavan matkasuunnitelman laatimisen lentovaihtoehtoineen, hotellisuosituksineen ja aktiviteettiehdotuksineen.

### Tehtävän jäsentäminen

Suuret tai monimutkaiset tehtävät muuttuvat hallittaviksi jaoteltuina pienempiin, tavoitesuuntautuneisiin alatavoitteisiin.
Matkasuunnitelman tapauksessa tavoite voidaan jäsentää seuraaviin osiin:

* Lentovaraukset
* Hotellivaraukset
* Autonvuokraus
* Henkilökohtaistaminen

Jokainen alatavoite voidaan sitten ratkaista omistautuneiden agenttien tai prosessien toimesta. Yksi agentti saattaa erikoistua etsimään parhaat lentotarjoukset, toinen hotelli- ja niin edelleen. Koordinointia tai "alemman tason" agenttia voidaan käyttää näiden tulosten kokoamiseen yhdeksi yhtenäiseksi matkasuunnitelmaksi loppukäyttäjälle.

Tämä modulaarinen lähestymistapa mahdollistaa myös asteittaiset parannukset. Voit esimerkiksi lisätä erikoistuneita agenteja ruoka- tai paikallisten aktiviteettien suosituksiin ja tarkentaa suunnitelmaa ajan myötä.

### Jäsennelty tuloste

Laajat kielimallit (LLM) voivat tuottaa jäsenneltyä tulostetta (esim. JSON), jonka alemman tason agentit tai palvelut voivat helpommin jäsentää ja käsitellä. Tämä on erityisen hyödyllistä monen agentin ympäristössä, jossa voimme toimia tehtävien pohjalta heti suunnittelutuloksen saamisen jälkeen. Katso tästä <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">blogikirjoituksesta</a> nopea yleiskatsaus.

Seuraava Python-esimerkki havainnollistaa yksinkertaista suunnitteluagenttia, joka jäsentää tavoitteen alatavoitteisiin ja tuottaa jäsennellyn suunnitelman:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Matkustus alitehtävä malli
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # haluamme määrittää tehtävän agentille

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # Vahvistaaksesi mallin kanssa sinun täytyy luoda henkilökohtainen käyttöoikeustunnus (PAT) GitHub-asetuksissasi.
    # Luo PAT-tunnuksesi seuraamalla ohjeita täällä: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# Määrittele käyttäjän viesti
messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
                      Provide your response in JSON format with the following structure:
{'main_task': 'Plan a family trip from Singapore to Melbourne.',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': 'Book round-trip flights from Singapore to '
                               'Melbourne.'}
    Below are the available agents specialised in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(
        content="Create a travel plan for a family of 2 kids from Singapore to Melboune", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string" )

pprint(json.loads(response_content))

# # Varmista, että vastaussisältö on kelvollinen JSON-merkkijono ennen sen lataamista
# response_content: Optional[str] = response.content if isinstance(
#     response.content, str) else None
# jos response_content on None:
#     nosta ValueError("Vastaussisältö ei ole kelvollinen JSON-merkkijono")

# # Tulosta vastaussisältö sen lataamisen jälkeen JSON-muodossa
# pprint(json.loads(response_content))

# Vahvista vastaussisältö MathReasoning-mallilla
# TravelPlan.model_validate(json.loads(response_content))
```

### Suunnitteluagentti monen agentin orkestroinnilla

Tässä esimerkissä Semanttinen Reititin Agentti vastaanottaa käyttäjän pyynnön (esim. "Tarvitsen hotellisuunnitelman matkalleni.").

Suunnittelija suorittaa sitten:

* Vastaanottaa hotellisuunnitelman: Suunnittelija ottaa käyttäjän viestin ja järjestelmäkehotteen (sis. käytettävissä olevat agenttien tiedot) perusteella tuottaa jäsennellyn matkasuunnitelman.
* Listaa agentit ja niiden työkalut: Agenttirekisterissä on lista agenteista (esim. lento-, hotelli-, autonvuokraus- ja aktiviteettiagentit) sekä niiden tarjoamista toiminnoista tai työkaluista.
* Ohjaa suunnitelman vastaaville agenteille: Onko alatavoitteita yksi vai useampi, suunnittelija joko lähettää viestin suoraan omistautuneelle agentille (yksittäistehtävissä) tai koordinoi ryhmächatin kautta monen agentin yhteistyötä.
* Tiivistää lopputuloksen: Lopuksi suunnittelija kokoaa yhteen laaditun suunnitelman selkeyden vuoksi.
Seuraava Python-koodinäyte kuvastaa näitä vaiheita:

```python

from pydantic import BaseModel

from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# Matkasuorite malli

class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # haluamme määrittää tehtävän agentille

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# Luo asiakas tyyppitarkastetuilla ympäristömuuttujilla

client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# Määritä käyttäjän viesti

messages = [
    SystemMessage(content="""You are an planner agent.
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# Varmista, että vastauksen sisältö on kelvollinen JSON-merkkijono ennen lataamista

response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("Response content is not a valid JSON string")

# Tulosta vastauksen sisältö JSON:n lataamisen jälkeen

pprint(json.loads(response_content))
```

Edellä olevan koodin tulos on seuraava, ja voit käyttää tätä jäsenneltyä tulostetta ohjaten sitä `assigned_agent` -kohteelle ja tiivistää matkasuunnitelman loppukäyttäjälle.

```json
{
    "is_greeting": "False",
    "main_task": "Plan a family trip from Singapore to Melbourne.",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "Book round-trip flights from Singapore to Melbourne."
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "Find family-friendly hotels in Melbourne."
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "Arrange a car rental suitable for a family of four in Melbourne."
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "List family-friendly activities in Melbourne."
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "Provide information about Melbourne as a travel destination."
        }
    ]
}
```

Esimerkkimuistikirja edellisestä koodiesimerkistä on saatavilla [tästä](07-autogen.ipynb).

### Iteratiivinen suunnittelu

Jotkut tehtävät vaativat vuorovaikutteisuutta tai uudelleensuunnittelua, jossa yhden alatavoitteen lopputulos vaikuttaa seuraavaan. Esimerkiksi jos agentti kohdataan odottamattoman tietomuodon lentovarauksissa, sen täytyy ehkä mukauttaa strategiaansa ennen hotellivarauksia.

Lisäksi käyttäjän palaute (esim. ihmisen päätös haluta aikaisempi lento) voi käynnistää osittaisen uudelleensuunnittelun. Tämä dynaaminen, iteratiivinen lähestymistapa takaa, että lopullinen ratkaisu vastaa todellisia rajoitteita ja käyttäjän muuttuvia mieltymyksiä.

esim. koodiesimerkki

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
#.. sama kuin edellisessä koodissa ja välitä käyttäjän historia, nykyinen suunnitelma
messages = [
    SystemMessage(content="""You are a planner agent to optimize the
    Your job is to decide which agents to run based on the user's request.
    Below are the available agents specialized in different tasks:
    - FlightBooking: For booking flights and providing flight information
    - HotelBooking: For booking hotels and providing hotel information
    - CarRental: For booking cars and providing car rental information
    - ActivitiesBooking: For booking activities and providing activity information
    - DestinationInfo: For providing information about destinations
    - DefaultAgent: For handling general requests""", source="system"),
    UserMessage(content="Create a travel plan for a family of 2 kids from Singapore to Melbourne", source="user"),
    AssistantMessage(content=f"Previous travel plan - {TravelPlan}", source="assistant")
]
# .. suunnittele uudelleen ja lähetä tehtävät asianomaisille agenteille
```

Täydellisempään suunnitteluun kannattaa tutustua Magnetic One <a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">blogikirjoitukseen</a>, joka käsittelee monimutkaisten tehtävien ratkaisua.

## Yhteenveto

Tässä artikkelissa tarkastelimme esimerkkiä siitä, kuinka voimme luoda suunnittelijan, joka voi dynaamisesti valita määritellyt käytettävissä olevat agentit. Suunnittelijan tulos jäsentää tehtävät ja osoittaa agentit niin, että ne voidaan suorittaa. Oletetaan, että agenteilla on pääsy tehtävän suorittamiseen vaadittaviin toimintoihin/työkaluihin. Agenttien lisäksi voit mukaan ottaa muita malleja, kuten reflektoinnin, tiivistäjän ja round robin -chatin, lisäsäätöjen tekemiseksi.

## Lisäresurssit

AutoGen Magentic One - Yleistason monen agentin järjestelmä monimutkaisten tehtävien ratkaisuun ja joka on saavuttanut vaikuttavia tuloksia useilla haastavilla agenttisuorituksen vertailualueilla. Viite: <a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">autogen-magentic-one</a>. Tässä toteutuksessa orkestroija luo tehtäväkohtaisen suunnitelman ja delegoi nämä tehtävät käytettävissä oleville agenteille. Suunnittelun lisäksi orkestroija käyttää seurantamekanismia tehtävien etenemisen valvontaan ja tarvittaessa uudelleensuunnitteluun.

### Onko sinulla lisää kysymyksiä Suunnittelumallista?

Liity [Microsoft Foundry Discordiin](https://aka.ms/ai-agents/discord) tapaamaan muita oppijoita, osallistumaan toimistotunteihin ja saamaan vastauksia AI Agentteja koskeviin kysymyksiisi.

## Edellinen oppitunti

[Luotettavien AI Agenttien rakentaminen](../06-building-trustworthy-agents/README.md)

## Seuraava oppitunti

[Moni-agenttisuunnittelumalli](../08-multi-agent/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastuuvapauslauseke**:
Tämä asiakirja on käännetty tekoälypohjaisella käännöspalvelulla [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, otathan huomioon, että automaattikäännöksissä saattaa esiintyä virheitä tai epätarkkuuksia. Alkuperäistä asiakirjaa sen alkuperäiskielellä tulee pitää virallisena lähteenä. Tärkeissä tiedoissa suositellaan ammattimaista ihmiskäännöstä. Emme ole vastuussa tämän käännöksen käytöstä johtuvista väärinymmärryksistä tai tulkinnoista.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->