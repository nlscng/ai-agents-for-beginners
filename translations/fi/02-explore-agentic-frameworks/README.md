[![Tutustu tekoälyagenttikehyksiin](../../../translated_images/fi/lesson-2-thumbnail.c65f44c93b8558df.webp)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(Napsauta yllä olevaa kuvaa katsoaksesi tämän oppitunnin videon)_

# Tutustu tekoälyagenttikehyksiin

Tekoälyagenttikehykset ovat ohjelmistoalustoja, jotka on suunniteltu helpottamaan tekoälyagenttien luomista, käyttöönottoa ja hallintaa. Nämä kehykset tarjoavat kehittäjille valmiita komponentteja, abstraktioita ja työkaluja, jotka sujuvoittavat monimutkaisten tekoälyjärjestelmien kehitystä.

Nämä kehykset auttavat kehittäjiä keskittymään sovellustensa ainutlaatuisiin osa-alueisiin tarjoamalla standardisoituja lähestymistapoja yleisiin haasteisiin tekoälyagenttien kehityksessä. Ne parantavat skaalautuvuutta, saavutettavuutta ja tehokkuutta tekoälyjärjestelmien rakentamisessa.

## Johdanto

Tämä oppitunti kattaa:

- Mitä tekoälyagenttikehykset ovat ja mitä niiden avulla kehittäjät voivat saavuttaa?
- Miten tiimit voivat käyttää näitä prototyyppien nopeaan tekemiseen, iterointiin ja agentin ominaisuuksien parantamiseen?
- Mitkä ovat Microsoftin <a href="https://aka.ms/ai-agents/autogen" target="_blank">AutoGen</a>-, <a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">Semantic Kernel</a>- ja <a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">Azure AI Agent Service</a>-kehysten ja -työkalujen erot?
- Voinko integroida nykyiset Azure-ekosysteemini työkalut suoraan, vai tarvitsenko erillisiä ratkaisuja?
- Mikä on Azure AI Agents -palvelu ja miten se auttaa minua?

## Oppimistavoitteet

Tämän oppitunnin tavoitteena on auttaa sinua ymmärtämään:

- Tekoälyagenttikehysten rooli tekoälyn kehityksessä.
- Miten hyödyntää tekoälyagenttikehyksiä älykkäiden agenttien rakentamisessa.
- Keskeiset ominaisuudet, joita tekoälyagenttikehykset mahdollistavat.
- Erot AutoGenin, Semantic Kernelin ja Azure AI Agent Servicen välillä.

## Mitä tekoälyagenttikehykset ovat ja mitä niiden avulla kehittäjät voivat tehdä?

Perinteiset tekoälykehykset voivat auttaa sinua integroimaan tekoälyä sovelluksiisi ja parantamaan näitä sovelluksia seuraavilla tavoilla:

- **Personalisointi**: Tekoäly voi analysoida käyttäjän käyttäytymistä ja mieltymyksiä tarjotakseen räätälöityjä suosituksia, sisältöä ja käyttökokemuksia.
Esimerkki: Suoratoistopalvelut kuten Netflix käyttävät tekoälyä ehdottaakseen elokuvia ja sarjoja katseluhistorian perusteella, mikä lisää käyttäjien sitoutumista ja tyytyväisyyttä.
- **Automaatio ja tehokkuus**: Tekoäly voi automatisoida toistuvia tehtäviä, sujuvoittaa työnkulkuja ja parantaa toiminnan tehokkuutta.
Esimerkki: Asiakaspalvelusovellukset käyttävät tekoälypohjaisia chatbotteja hoitaakseen yleisiä kyselyjä, mikä lyhentää vastausaikoja ja vapauttaa ihmistyöntekijöitä monimutkaisempiin tehtäviin.
- **Parannettu käyttökokemus**: Tekoäly voi parantaa yleistä käyttökokemusta tarjoamalla älykkäitä ominaisuuksia, kuten puheentunnistusta, luonnollisen kielen käsittelyä ja ennustavaa tekstiä.
Esimerkki: Virtuaaliavustajat kuten Siri ja Google Assistant käyttävät tekoälyä ymmärtääkseen ja vastatakseen puheentunnistukseen, mikä helpottaa käyttäjien vuorovaikutusta laitteidensa kanssa.

### Kuulostaa hyvältä, mutta miksi tarvitsemme tekoälyagenttikehystä?

Tekoälyagenttikehykset edustavat enemmän kuin pelkkiä tekoälykehyksiä. Ne on suunniteltu mahdollistamaan älykkäiden agenttien luominen, jotka voivat olla vuorovaikutuksessa käyttäjien, muiden agenttien ja ympäristön kanssa saavuttaakseen tiettyjä tavoitteita. Nämä agentit voivat toimia itsenäisesti, tehdä päätöksiä ja sopeutua muuttuviin olosuhteisiin. Tarkastellaan joitakin keskeisiä ominaisuuksia, joita tekoälyagenttikehykset mahdollistavat:

- **Agenttien yhteistyö ja koordinointi**: Mahdollistavat useiden tekoälyagenttien luomisen, jotka voivat työskennellä yhdessä, kommunikoida ja koordinoitua ratkaistakseen monimutkaisia tehtäviä.
- **Tehtävien automaatio ja hallinta**: Tarjoavat mekanismeja monivaiheisten työnkulkujen automatisointiin, tehtävien delegointiin ja dynaamiseen tehtävien hallintaan agenttien kesken.
- **Kontekstuaalinen ymmärrys ja sopeutuminen**: Varustavat agentit kyvyllä ymmärtää kontekstia, sopeutua muuttuviin ympäristöihin ja tehdä päätöksiä reaaliaikaisen tiedon perusteella.

Yhteenvetona agentit antavat sinulle mahdollisuuden tehdä enemmän: viedä automaation seuraavalle tasolle ja luoda älykkäämpiä järjestelmiä, jotka voivat sopeutua ja oppia ympäristöstään.

## Miten prototyyppejä voi nopeasti rakentaa, iteröidä ja parantaa agentin ominaisuuksia?

Tämä ala kehittyy nopeasti, mutta useimmissa tekoälyagenttikehyksissä on joitakin yhteisiä tekijöitä, jotka auttavat sinua nopeasti prototyyppien tekemisessä ja iteroinnissa, nimittäin modulaariset komponentit, yhteistyötyökalut ja reaaliaikainen oppiminen. Sukelletaan näihin:

- **Käytä modulaarisia komponentteja**: AI SDK:t tarjoavat valmiita komponentteja, kuten tekoäly- ja muistikytkimiä, funktiokutsuja luonnollisella kielellä tai koodilaajennuksilla, kehotemalleja ja muuta.
- **Hyödynnä yhteistyötyökaluja**: Suunnittele agentteja tietyillä rooleilla ja tehtävillä, jolloin ne voivat testata ja hioa yhteistyötyönkulkuja.
- **Opiskele reaaliajassa**: Toteuta palautesilmukoita, joissa agentit oppivat vuorovaikutuksista ja säätävät käyttäytymistään dynaamisesti.

### Käytä modulaarisia komponentteja

SDK:t kuten Microsoft Semantic Kernel ja LangChain tarjoavat valmiita komponentteja, kuten AI-kytkimiä, kehotepohjia ja muistin hallintaa.

**Miten tiimit voivat käyttää näitä**: Tiimit voivat nopeasti koota nämä komponentit toimivaksi prototyypiksi ilman, että aloitetaan alusta, mikä mahdollistaa nopean kokeilun ja iteroinnin.

**Miten se toimii käytännössä**: Voit käyttää valmista jäsentä (parseria) poimiaksesi tietoa käyttäjän syötteestä, muistimoduulia tietojen tallentamiseen ja hakemiseen sekä kehotegeneraattoria vuorovaikutukseen käyttäjän kanssa — kaikki ilman, että sinun tarvitsee rakentaa näitä komponentteja alusta alkaen.

**Esimerkkikoodi**. Katsotaan esimerkkejä siitä, miten voit käyttää valmista AI-kytkintä Semantic Kernelin Python- ja .NET-versioissa, joka käyttää automaattista funktiokutsua mallin vastaamiseksi käyttäjän syötteeseen:

``` python
# Semantic Kernel Python -esimerkki

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Määrittele ChatHistory-olio pitämään keskustelun konteksti
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Määrittele esimerkkilaajennus, joka sisältää matkan varaustoiminnon
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Luo Kernel
kernel = Kernel()

# Lisää esimerkkilaajennus Kernel-olioon
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Määrittele Azure OpenAI AI -liitin
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Määrittele pyyntöasetukset mallin konfiguroimiseksi automaattisella toimintakutsulla
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Tee pyyntö mallille annetulla keskusteluhistorialla ja pyyntöasetuksilla
    # Kernel sisältää esimerkin, jonka malli pyytää suorittamaan
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # Esimerkki AI-mallin vastaus: `Lentosi New Yorkiin 1. tammikuuta 2025 on onnistuneesti varattu. Hyvää matkaa! ✈️🗽`

    # Lisää mallin vastaus keskusteluhistoriakontekstiimme
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel"); 
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```

Mitä tästä esimerkistä näet, on kuinka voit hyödyntää valmista jäsentä poimiaksesi keskeisiä tietoja käyttäjän syötteestä, kuten lähtö- ja kohdepaikan sekä päivämäärän lentovarauksen pyynnöstä. Tämä modulaarinen lähestymistapa antaa sinun keskittyä korkean tason logiikkaan.

### Hyödynnä yhteistyötyökaluja

Kehykset kuten CrewAI, Microsoft AutoGen ja Semantic Kernel helpottavat useiden agenttien luomista, jotka voivat työskennellä yhdessä.

**Miten tiimit voivat käyttää näitä**: Tiimit voivat suunnitella agentteja erityisillä rooleilla ja tehtävillä, jolloin ne voivat testata ja hioa yhteistyötyönkulkuja ja parantaa koko järjestelmän tehokkuutta.

**Miten se toimii käytännössä**: Voit luoda agenttitiimin, jossa jokaisella agentilla on erikoistunut tehtävä, kuten tiedonhaku, analyysi tai päätöksenteko. Nämä agentit voivat kommunikoida ja jakaa tietoa saavuttaakseen yhteisen tavoitteen, kuten vastaamalla käyttäjän kyselyyn tai suorittamalla tehtävän.

**Esimerkkikoodi (AutoGen)**:

```python
# luodaan agentteja, sitten luodaan pyörivä aikataulu, jossa he voivat työskennellä yhdessä, tässä tapauksessa järjestyksessä

# Tietojen hakemisen agentti
# Tietojen analysoinnin agentti
# Päätöksenteon agentti

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# keskustelu päättyy, kun käyttäjä sanoo "HYVÄKSY"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Käytä asyncio.run(...) ajettaessa skriptissä.
await Console(stream)
```

Mitä edellisessä koodissa näet, on kuinka voit luoda tehtävän, joka sisältää useiden agenttien yhteistyön datan analysoimiseksi. Jokainen agentti suorittaa tietyn toiminnon, ja tehtävä toteutetaan koordinoimalla agentteja halutun lopputuloksen saavuttamiseksi. Luomalla omistettuja agentteja erikoistuneilla rooleilla voit parantaa tehtävän tehokkuutta ja suorituskykyä.

### Opiskele reaaliajassa

Edistyneet kehykset tarjoavat kyvykkyyksiä reaaliaikaiseen kontekstin ymmärtämiseen ja sopeutumiseen.

**Miten tiimit voivat käyttää näitä**: Tiimit voivat toteuttaa palautesilmukoita, joissa agentit oppivat vuorovaikutuksista ja säätävät käyttäytymistään dynaamisesti, mikä johtaa jatkuvaan parantamiseen ja kyvykkyyksien hiomiseen.

**Miten se toimii käytännössä**: Agentit voivat analysoida käyttäjäpalautetta, ympäristötietoja ja tehtävien tuloksia päivittääkseen tietopohjaansa, säätääkseen päätöksentekoalgoritmejaan ja parantaakseen suorituskykyä ajan myötä. Tämä iteratiivinen oppimisprosessi mahdollistaa agenttien sopeutumisen muuttuviin olosuhteisiin ja käyttäjäpreferensseihin, mikä parantaa koko järjestelmän tehokkuutta.

## Mitkä ovat erot AutoGenin, Semantic Kernelin ja Azure AI Agent Servicen välillä?

Näitä kehyksiä voi verrata monin tavoin, mutta tarkastellaan joitakin keskeisiä eroja niiden suunnittelun, kyvykkyyksien ja kohdekäyttötapausten suhteen:

## AutoGen

AutoGen on Microsoft Researchin AI Frontiers Labin kehittämä avoimen lähdekoodin kehys. Se keskittyy tapahtumapohjaisiin, hajautettuihin agenttisovelluksiin, mahdollistaen useiden LLM:ien ja SLM:ien, työkalujen ja edistyneiden moniantiesuunnittelumallien käytön.

AutoGen rakentuu agenttien keskeisen käsitteen ympärille: agentit ovat itsenäisiä entiteettejä, jotka voivat havaita ympäristönsä, tehdä päätöksiä ja toimia saavuttaakseen tiettyjä tavoitteita. Agentit kommunikoivat asynkronisten viestien kautta, mikä antaa niille mahdollisuuden toimia itsenäisesti ja rinnakkain, parantaen järjestelmän skaalautuvuutta ja reagointikykyä.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">Agentit perustuvat näyttelijämalliin</a>. Wikipedian mukaan näyttelijä on _saman­aikaisten laskentojen perusyksikkö. Vastauksena vastaanottamaansa viestiin näyttelijä voi: tehdä paikallisia päätöksiä, luoda lisää näyttelijöitä, lähettää lisää viestejä ja päättää, miten vastata seuraavaan vastaanotettuun viestiin_.

**Käyttötapaukset**: Koodin automaatio, data-analyysitehtävät ja räätälöityjen agenttien rakentaminen suunnittelua ja tutkimusta varten.

Tässä on joitakin AutoGenin tärkeitä ydinkäsitteitä:

- **Agentit**. Agentti on ohjelmisto-entiteetti, joka:
  - **Kommunikoi viestien välityksellä**, nämä viestit voivat olla synkronisia tai asynkronisia.
  - **Ylläpitää omaa tilaansa**, jota saapuvat viestit voivat muuttaa.
  - **Suorittaa toimintoja** vastauksena vastaanotettuihin viesteihin tai tilan muutoksiin. Nämä toimet voivat muuttaa agentin tilaa ja tuottaa ulkoisia vaikutuksia, kuten päivittää viestilokeja, lähettää uusia viestejä, suorittaa koodia tai tehdä API-kutsuja.
    
  Tässä on lyhyt koodiesimerkki, jossa luot oman agenttisi chat-ominaisuuksilla:

    ```python
    from autogen_agentchat.agents import AssistantAgent
    from autogen_agentchat.messages import TextMessage
    from autogen_ext.models.openai import OpenAIChatCompletionClient


    class MyAgent(RoutedAgent):
        def __init__(self, name: str) -> None:
            super().__init__(name)
            model_client = OpenAIChatCompletionClient(model="gpt-4o")
            self._delegate = AssistantAgent(name, model_client=model_client)
    
        @message_handler
        async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
            print(f"{self.id.type} received message: {message.content}")
            response = await self._delegate.on_messages(
                [TextMessage(content=message.content, source="user")], ctx.cancellation_token
            )
            print(f"{self.id.type} responded: {response.chat_message.content}")
    ```
    
    Edellisessä koodissa `MyAgent` on luotu ja perii `RoutedAgent`-luokan. Sillä on viestinkäsittelijä, joka tulostaa viestin sisällön ja sitten lähettää vastauksen käyttäen `AssistantAgent`-delegaattia. Erityisesti huomaa, kuinka annamme `self._delegate`:lle instanssin `AssistantAgent`-luokasta, joka on valmiiksi rakennettu agentti, joka osaa käsitellä chat-vastauksia.


    Ilmoitetaan AutoGenille tästä agenttityypistä ja käynnistetään ohjelma seuraavaksi:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Aloita viestien käsittely taustalla.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```

    Edellisessä koodissa agentit rekisteröidään suoritusympäristöön ja sitten agentille lähetetään viesti, mikä johtaa seuraavaan tulostukseen:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```

- **Moni-agenttijärjestelmät**. AutoGen tukee useiden agenttien luomista, jotka voivat työskennellä yhdessä monimutkaisten tehtävien ratkaisemiseksi. Agentit voivat kommunikoida, jakaa tietoa ja koordinoida toimintojaan ongelmien tehokkaammaksi ratkaisemiseksi. Moni-agenttijärjestelmän luomiseksi voit määritellä erilaisia agenttityyppejä erikoistuneilla toiminnoilla ja rooleilla, kuten tiedonhaku, analyysi, päätöksenteko ja käyttäjävuorovaikutus. Katsotaan, miltä tällainen luominen näyttää, jotta saamme käsityksen siitä:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Esimerkki Agentin määrittelystä
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Käytetään topic-tyyppiä agentin tyypinä.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # muut määrittelyt lyhennetty tiiviyden vuoksi

    # Ryhmäkeskustelu
    group_chat_manager_type = await GroupChatManager.register(
    runtime,
    "group_chat_manager",
    lambda: GroupChatManager(
        participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        participant_descriptions=[
            writer_description, 
            illustrator_description, 
            editor_description, 
            user_description
        ],
        ),
    )
    ```

    Edellisessä koodissa meillä on `GroupChatManager`, joka on rekisteröity suoritusympäristöön. Tämä manager vastaa erilaisten agenttityyppien, kuten kirjoittajien, kuvittajien, toimittajien ja käyttäjien, välisen vuorovaikutuksen koordinoinnista.

- **Agenttien suoritusympäristö**. Kehys tarjoaa suoritusympäristön, joka mahdollistaa agenttien välisen viestinnän, hallinnoi niiden identiteettejä ja elinkaarta sekä valvoo turvallisuus- ja yksityisyysrajoja. Tämä tarkoittaa, että voit ajaa agenttejasi turvallisessa ja hallitussa ympäristössä, varmistaen, että ne voivat olla vuorovaikutuksessa turvallisesti ja tehokkaasti. On kaksi mielenkiintoista suoritusympäristöä:
  - **Erillinen suoritusympäristö**. Tämä on hyvä valinta yhden prosessin sovelluksille, joissa kaikki agentit on toteutettu samalla ohjelmointikielellä ja ajetaan samassa prosessissa. Tässä on kuvallinen esitys siitä, miten se toimii:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">Erillinen suoritusympäristö</a>   
Sovelluspino

    *agentit kommunikoivat viestien välityksellä suoritusympäristön kautta, ja suoritusympäristö hallinnoi agenttien elinkaarta*

  - **Jakautunut suoritusympäristö**, soveltuu moniprosessisovelluksiin, joissa agentit voidaan toteuttaa eri ohjelmointikielillä ja ajaa eri koneissa. Tässä on kuvallinen esitys siitä, miten se toimii:
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">Jakautunut suoritusympäristö</a>

## Semantic Kernel + Agent Framework

Semantic Kernel on yritystason AI-orchestration SDK. Se koostuu tekoäly- ja muistiyhteyksistä sekä Agent Frameworkista.

Käydään ensin läpi joitakin ydinosia:

- **AI-kytkimet**: Tämä on rajapinta ulkoisiin tekoälypalveluihin ja tietolähteisiin käytettäväksi sekä Pythonissa että C#:ssa.

  ```python
  # Semanttinen ydin Pythonissa
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```  

    ```csharp
    // Semantic Kernel C#
    using Microsoft.SemanticKernel;

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```

    Tässä on yksinkertainen esimerkki siitä, miten voit luoda kernelin ja lisätä chat-vastauspalvelun. Semantic Kernel luo yhteyden ulkoiseen tekoälypalveluun, tässä tapauksessa Azure OpenAI Chat Completioniin.

- **Laajennukset (Plugins)**: Nämä kapseloivat funktioita, joita sovellus voi käyttää. Saatavilla on sekä valmiita laajennuksia että omia, joita voit luoda. Liittyvä käsite on "prompt functions". Sen sijaan, että annetaan luonnollisen kielen vihjeitä funktion kutsumista varten, lähetät tietyt funktiot mallille. Nykyisen chat-kontekstin perusteella malli voi valita kutsua jotakin näistä funktioista täyttääkseen pyynnön tai kyselyn. Tässä esimerkki:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```

    Tässä sinulla on ensin mallikehote `skPrompt`, joka jättää tilaa käyttäjän syötteelle, `$userInput`. Sitten luot kernel-funktion `SummarizeText` ja tuot sen kernelin käyttöön plugin-nimellä `SemanticFunctions`. Huomaa funktion nimi, joka auttaa Semantic Kernelia ymmärtämään, mitä funktio tekee ja milloin sitä tulisi kutsua.

- **Natiivi funktio**: On myös natiivifunktioita, joita kehys voi kutsua suoraan tehtävän suorittamiseksi. Tässä esimerkki funktiosta, joka hakee sisällön tiedostosta:

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```

- **Muisti**: Abstrahoi ja yksinkertaistaa kontekstinhallintaa tekoälysovelluksissa. Ajatus muistista on, että tämä on jotain, jonka LLM:n pitäisi tietää. Voit tallentaa tämän tiedon vektorivarastoon, joka toimii muistissa pidettävänä tietokantana tai vektoripohjaisena tietokantana tai vastaavana. Tässä on esimerkki hyvin yksinkertaistetusta tilanteesta, jossa *faktat* lisätään muistiin:

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
    );
    
    string memoryCollectionName = "SummarizedAzureDocs";
    
    foreach (var fact in facts) {
        await memoryBuilder.SaveReferenceAsync(
            collection: memoryCollectionName,
            description: fact.Key.Split(";")[1].Trim(),
            text: fact.Value,
            externalId: fact.Key.Split(";")[2].Trim(),
            externalSourceName: "Azure Documentation"
        );
    }
    ```

    Nämä tosiasiat tallennetaan sitten muistokokoelmaan `SummarizedAzureDocs`. Tämä on hyvin yksinkertaistettu esimerkki, mutta siitä näet, miten voit tallentaa tietoa muistiin LLM:n käytettäväksi.

Joten siinä perusasiat Semantic Kernel -kehyksestä, entä Agent Framework?

## Azure AI Agent Service

Azure AI Agent Service on uudempi lisäys, joka esiteltiin Microsoft Ignite 2024 -tapahtumassa. Sen avulla voidaan kehittää ja ottaa käyttöön AI-agentteja joustavampien mallien kanssa, esimerkiksi kutsumalla suoraan avoimen lähdekoodin LLM-malleja kuten Llama 3, Mistral ja Cohere.

Azure AI Agent Service tarjoaa vankempia yritystason tietoturvamekanismeja ja tietojen tallennustapoja, mikä tekee siitä sopivan yrityssovelluksiin.

Se toimii valmiiksi yhteensopivana monen agentin orkestrointikehysten, kuten AutoGenin ja Semantic Kernelin, kanssa.

Palvelu on tällä hetkellä julkisessa esikatselussa (Public Preview) ja tukee Pythonia ja C#:ta agenttien rakentamiseen.

Käyttämällä Semantic Kernel Pythonia voimme luoda Azure AI Agentin käyttäjän määrittelemällä lisäosalla:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Määrittele esimerkkilisäosa esimerkkiä varten
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # Luo agenttimääritelmä
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Luo AzureAI-agentti käyttäen määriteltyä clientiä ja agenttimääritelmää
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Luo ketju pitämään keskustelu
        # Jos ketjua ei ole annettu, uusi ketju
        # luodaan ja palautetaan alkuperäisen vastauksen kanssa
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # Kutsu agenttia määritellylle ketjulle
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### Keskeiset käsitteet

Azure AI Agent Service sisältää seuraavat keskeiset käsitteet:

- **Agentti**. Azure AI Agent Service integroidaan Microsoft Foundryn kanssa. AI Foundryssa AI-agentti toimii "älykkäänä" mikropalveluna, jota voidaan käyttää kysymyksiin vastaamiseen (RAG), toimintojen suorittamiseen tai työnkulkujen täydelliseen automatisointiin. Se saavuttaa tämän yhdistämällä generatiivisten AI-mallien voiman työkaluihin, jotka antavat sille pääsyn ja mahdollisuuden olla vuorovaikutuksessa todellisten tietolähteiden kanssa. Tässä on esimerkki agentista:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    Tässä esimerkissä agentti luodaan mallilla `gpt-4o-mini`, nimellä `my-agent` ja ohjeilla `You are helpful agent`. Agentti varustetaan työkaluilla ja resursseilla koodin tulkintatehtävien suorittamiseksi.

- **Keskustelu ja viestit**. Keskustelu (thread) on toinen tärkeä käsite. Se edustaa keskustelua tai vuorovaikutusta agentin ja käyttäjän välillä. Keskusteluja voidaan käyttää keskustelun etenemisen seuraamiseen, kontekstin tallentamiseen ja vuorovaikutuksen tilan hallintaan. Tässä on esimerkki keskustelusta:

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    Edellisessä koodissa luodaan keskustelu. Tämän jälkeen keskustelulle lähetetään viesti. Kutsumalla `create_and_process_run` agenttia pyydetään tekemään työtä keskustelun parissa. Lopuksi viestit haetaan ja kirjataan nähdäksesi agentin vastauksen. Viestit osoittavat keskustelun etenemisen käyttäjän ja agentin välillä. On myös tärkeää ymmärtää, että viestit voivat olla eri tyyppejä, kuten tekstiä, kuvaa tai tiedostoa — eli agentin työ on saattanut tuottaa esimerkiksi kuvan tai tekstivastauksen. Kehittäjänä voit sitten käyttää tätä tietoa vastauksen edelleen käsittelemiseksi tai esittelemiseksi käyttäjälle.

- **Integroituu muihin AI-kehyksiin**. Azure AI Agent Service voi olla vuorovaikutuksessa muiden kehysten, kuten AutoGenin ja Semantic Kernelin, kanssa, mikä tarkoittaa, että voit rakentaa osan sovelluksestasi yhdessä näistä kehyksistä ja esimerkiksi käyttää Agent-palvelua orkestroijana tai voit rakentaa kaiken Agent-palvelussa.

**Käyttötapaukset**: Azure AI Agent Service on suunniteltu yrityssovelluksiin, jotka vaativat turvallista, skaalautuvaa ja joustavaa AI-agenttien käyttöönottoa.

## Mitä eroa näillä kehyksillä on?
 
Vaikuttaa siltä, että näiden kehysten välillä on paljon päällekkäisyyttä, mutta niiden suunnittelussa, ominaisuuksissa ja kohdekohteissa on joitain keskeisiä eroja:
 
- **AutoGen**: On kokeilukehys, joka keskittyy huipputason monen agentin järjestelmien tutkimukseen. Se on paras paikka kokeilla ja prototypoida kehittyneitä monen agentin järjestelmiä.
- **Semantic Kernel**: On tuotantovalmiiksi tarkoitettu agenttikirjasto yritystason agenttisovellusten rakentamiseen. Keskittyy tapahtumapohjaisiin, hajautettuihin agenttisovelluksiin, mahdollistaen useiden LLM- ja SLM-mallien, työkalujen sekä yksi- ja monikantaisten agenttimallien käytön.
- **Azure AI Agent Service**: On alusta ja käyttöönotto-palvelu Azure Foundryssa agentteja varten. Se tarjoaa yhteyksien rakentamisen Azuren tarjoamiin palveluihin, kuten Azure OpenAI, Azure AI Search, Bing Search ja koodin suoritusmahdollisuudet.
 
Etkö ole vielä varma, kumpaa valita?

### Käyttötapaukset
 
Käydään läpi muutamia yleisiä käyttötapauksia, jotka voivat auttaa sinua valinnassa:
 
> Q: Kokeilen, opiskelen ja rakennan proof-of-concept -agenttisovelluksia, ja haluan pystyä rakentamaan ja kokeilemaan nopeasti
>

>A: AutoGen olisi hyvä valinta tässä tilanteessa, koska se keskittyy tapahtumapohjaisiin, hajautettuihin agenttisovelluksiin ja tukee edistyneitä monen agentin suunnittelumalleja.

> Q: Mikä tekee AutoGenista paremman valinnan kuin Semantic Kernelin ja Azure AI Agent Service:n tässä käyttötapauksessa?
>
> A: AutoGen on erityisesti suunniteltu tapahtumapohjaisiin, hajautettuihin agenttisovelluksiin, mikä tekee siitä hyvin soveltuvan koodin generaation ja data-analyysin automatisointitehtäviin. Se tarjoaa tarvittavat työkalut ja ominaisuudet monimutkaisten monen agentin järjestelmien rakentamiseen tehokkaasti.

>Q: Vaikuttaa siltä, että Azure AI Agent Service voisi toimia myös tässä, sillä siinä on työkaluja koodin generointiin ja muuhun?

>
> A: Kyllä, Azure AI Agent Service on agenttipalvelu ja sisältää sisäänrakennettuja ominaisuuksia useille malleille, Azure AI Searchille, Bing-haulle ja Azure Functionsille. Sen avulla agenttien rakentaminen Foundry-portaalissa ja niiden käyttöönotto suuressa mittakaavassa on helppoa.
 
> Q: Olen edelleen hämmentynyt, anna minulle yksi vaihtoehto
>
> A: Erinomainen valinta on rakentaa sovelluksesi ensin Semantic Kernelilla ja käyttää sitten Azure AI Agent Serviceä agentin käyttöönottoon. Tämä lähestymistapa antaa sinun helposti säilyttää agenttisi samalla kun hyödynnät Semantic Kernelin kykyä rakentaa monen agentin järjestelmiä. Lisäksi Semantic Kernelilla on liitin AutoGeniin, mikä tekee molempien kehysten käytön yhdistelmän helpoksi.
 
Tiivistetään keskeiset erot taulukkoon:

| Framework | Fokus | Keskeiset käsitteet | Käyttötapaukset |
| --- | --- | --- | --- |
| AutoGen | Tapahtumapohjaiset, hajautetut agenttisovellukset | Agentit, Persoonat, Funktiot, Data | Koodin generointi, data-analyysitehtävät |
| Semantic Kernel | Ihmismäisen tekstin ymmärtäminen ja tuottaminen | Agentit, Modulaariset komponentit, Yhteistyö | Luonnollisen kielen ymmärtäminen, sisällön generointi |
| Azure AI Agent Service | Joustavat mallit, yritystason tietoturva, koodin generointi, työkalukutsut | Modulaarisuus, Yhteistyö, Prosessien orkestrointi | Turvallinen, skaalautuva ja joustava AI-agenttien käyttöönotto |

Mikä on ihanteellinen käyttötapaus kullekin näistä kehyksistä?

## Voinko integroida olemassa olevat Azure-ekosysteemin työkaluni suoraan, vai tarvitaanko erillisiä ratkaisuja?

Vastaus on kyllä: voit integroida olemassa olevat Azure-ekosysteemin työkalusi suoraan, erityisesti Azure AI Agent Servicen kanssa, koska se on rakennettu toimimaan saumattomasti muiden Azure-palveluiden kanssa. Voit esimerkiksi integroida Bingin, Azure AI Searchin ja Azure Functionsin. Lisäksi on syvä integraatio Microsoft Foundryn kanssa.

AutoGenin ja Semantic Kernelin kanssa voit myös integroida Azure-palveluihin, mutta se saattaa edellyttää, että kutsut Azure-palveluja koodistasi. Toinen tapa integroida on käyttää Azure SDK:ita agenttien kautta Azure-palveluihin kommunikointiin. Kuten aiemmin mainittiin, voit myös käyttää Azure AI Agent Serviceä orkestroijana AutoGenilla tai Semantic Kernelilla rakennettujen agenttien kohdalla, mikä antaa helpon pääsyn Azure-ekosysteemiin.

## Esimerkkikoodit

- Python: [Agent Framework](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/02-dotnet-agent-framework.md)

## Onko sinulla lisää kysymyksiä AI-agenttikehyksistä?

Liity [Microsoft Foundry Discordiin](https://aka.ms/ai-agents/discord) tapaa muita oppijoita, osallistu office hours -tilaisuuksiin ja saat vastauksia AI-agentteihin liittyviin kysymyksiisi.

## Lähteet

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel and AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">Using Azure AI Agent Service with AutoGen / Semantic Kernel to build a multi-agent's solution</a>

## Edellinen oppitunti

[Introduction to AI Agents and Agent Use Cases](../01-intro-to-ai-agents/README.md)

## Seuraava oppitunti

[Understanding Agentic Design Patterns](../03-agentic-design-patterns/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Vastuuvapauslauseke:
Tämä asiakirja on käännetty tekoälypohjaisella käännöspalvelulla [Co-op Translator](https://github.com/Azure/co-op-translator). Vaikka pyrimme tarkkuuteen, on huomioitava, että automaattikäännöksissä voi esiintyä virheitä tai epätarkkuuksia. Alkuperäinen asiakirja sen alkuperäisellä kielellä on pidettävä auktoritatiivisena lähteenä. Kriittisen tiedon osalta suositellaan ammattilaisen tekemää ihmiskäännöstä. Emme ole vastuussa tämän käännöksen käytöstä aiheutuvista mahdollisista väärinymmärryksistä tai virheellisistä tulkinnoista.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->