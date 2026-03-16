# Microsoft Agent Frameworkin tutkiminen

![Agent Framework](../../../translated_images/fi/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Johdanto

Tässä oppitunnissa käsitellään:

- Microsoft Agent Frameworkin ymmärtäminen: Keskeiset ominaisuudet ja arvo  
- Microsoft Agent Frameworkin keskeisten käsitteiden tutkiminen
- MAF:n vertaaminen Semantic Kernelin ja AutoGenin kanssa: Migraatio-opas

## Oppimistavoitteet

Oppitunnin suorittamisen jälkeen osaat:

- Rakentaa tuotantovalmiita tekoälyagentteja Microsoft Agent Frameworkin avulla
- Soveltaa Microsoft Agent Frameworkin ydintoimintoja agenttipohjaisiin käyttötapauksiisi
- Migroida ja integroida olemassa olevia agenttipohjaisia kehyksiä ja työkaluja

## Koodiesimerkit 

Microsoft Agent Frameworkin (MAF) koodiesimerkit löytyvät tästä repositoriosta tiedostojen `xx-python-agent-framework` ja `xx-dotnet-agent-framework` alta.

## Microsoft Agent Frameworkin ymmärtäminen

![Framework Intro](../../../translated_images/fi/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) rakentuu Semantic Kernelin ja AutoGenin kokemusten ja oppien päälle. Se tarjoaa joustavuutta monenlaisiin agenttipohjaisiin käyttötapauksiin, joita nähdään sekä tuotantoympäristöissä että tutkimuksessa, mukaan lukien:

- **Peräkkäinen agenttien orkestrointi** tilanteissa, joissa tarvitaan vaiheittaisia työnkulkuja.
- **Samanaikainen orkestrointi** tilanteissa, joissa agenttien tulee suorittaa tehtävät samaan aikaan.
- **Ryhmäkeskusteluorkestrointi** tilanteissa, joissa agentit tekevät yhteistyötä yhden tehtävän parissa.
- **Tehtävien siirtojen orkestrointi** tilanteissa, joissa agentit siirtävät tehtäviä toisilleen, kun osatehtävät valmistuvat.
- **Magneettinen orkestrointi** tilanteissa, joissa johtava agentti luo ja muokkaa tehtävälistaa ja koordinoi alagenttien toimintaa tehtävän suorittamiseksi.

Tuotantovalmiiden tekoälyagenttien toimittamiseksi MAF tarjoaa myös ominaisuuksia, kuten:

- **Havaittavuus** OpenTelemetryn avulla, jossa jokainen tekoälyagentin toiminto, mukaan lukien työkalukutsut, orkestrointivaiheet, päättelyvirrat ja suorituksen valvonta Microsoft Foundryn kojelautojen kautta, on seurattavissa.
- **Turvallisuus** isännöimällä agenteja natiivisti Microsoft Foundryssa, johon sisältyy turvallisuusohjauksia kuten roolipohjainen pääsy, yksityisen tiedon käsittely ja sisäänrakennettu sisällön turvallisuus.
- **Kestävyys** koska agenttilangat ja työnkulut voivat pysähtyä, jatkua ja toipua virheistä, mikä mahdollistaa pidempiaikaiset prosessit.
- **Hallinta** ihmisen osallistuminen työnkulkuun on tuettu, jolloin tehtävät voidaan merkitä vaativaksi ihmisen hyväksyntää.

Microsoft Agent Framework keskittyy myös yhteentoimivuuteen:

- **Pilvipalveluriippumattomuus** - Agentteja voi käyttää säiliöissä, paikallisissa ympäristöissä ja useissa pilvipalveluissa.
- **Tarjoajiriippumattomuus** - Agentteja voidaan luoda suosimallasi SDK:lla, mukaan lukien Azure OpenAI ja OpenAI.
- **Avoimien standardien hyödyntäminen** - Agentit voivat käyttää protokollia kuten Agent-to-Agent (A2A) ja Model Context Protocol (MCP) löytääkseen ja käyttäessään muita agenteja ja työkaluja.
- **Laajennukset ja liittimet** - Yhteydet voidaan tehdä datasäiliöihin ja muistiin kuten Microsoft Fabric, SharePoint, Pinecone ja Qdrant.

Tarkastellaan, miten nämä ominaisuudet liittyvät Microsoft Agent Frameworkin keskeisiin käsitteisiin.

## Microsoft Agent Frameworkin keskeiset käsitteet

### Agentit

![Agent Framework](../../../translated_images/fi/agent-components.410a06daf87b4fef.webp)

**Agenttien luominen**

Agentin luominen tapahtuu määrittelemällä päättelypalvelu (LLM Provider), joukko ohjeita tekoälyagentin noudatettavaksi ja määritelty `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Yllä käytetään `Azure OpenAI`:ta, mutta agentteja voidaan luoda monilla eri palveluilla, mukaan lukien `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI:n `Responses`, `ChatCompletion` API:t

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

tai etäagenttien kanssa käyttämällä A2A-protokollaa:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Agenttien suorittaminen**

Agenteja suoritetaan `.run` tai `.run_stream` -metodeilla, joko ei-suoratoistona tai suoratoistona vastauksia varten.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Jokaisella agentin suorituksella voi olla myös vaihtoehtoja, joilla voidaan mukauttaa parametreja, kuten agentin käyttämien `max_tokens` -arvoa, agentin kutsumia `tools`-työkaluja ja jopa agentin käyttämää `model`-mallia.

Tämä on hyödyllistä tilanteissa, joissa käyttäjän tehtävän suorittamiseen vaaditaan tiettyjä malleja tai työkaluja.

**Työkalut**

Työkaluja voidaan määritellä sekä agenttia luotaessa:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Kun luot ChatAgentin suoraan

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

että agenttia suoritettaessa:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Työkalu tarjottu vain tätä ajoa varten )
```

**Agenttilangat**

Agenttilankoja käytetään monikymmenkeskustelujen käsittelyyn. Langan voi luoda joko:

- Käyttämällä `get_new_thread()`, joka mahdollistaa langan tallentamisen ajan myötä
- Luomalla lankaa automaattisesti agenttia suoritettaessa, jolloin lanka kestää vain nykyisen suorituksen ajan.

Langan luomiseen koodi näyttää tältä:

```python
# Luo uusi säie.
thread = agent.get_new_thread() # Suorita agentti säikeen kanssa.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Voit sitten serialisoida langan, jotta se voidaan tallentaa myöhempää käyttöä varten:

```python
# Luo uusi säie.
thread = agent.get_new_thread() 

# Suorita agentti säikeellä.

response = await agent.run("Hello, how are you?", thread=thread) 

# Sarjoita säie tallennusta varten.

serialized_thread = await thread.serialize() 

# Purkaa säikeen tila latauksen jälkeen.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agenttien middleware**

Agentit toimivat työkalujen ja LLM:ien kanssa suorittaakseen käyttäjän tehtävät. Joissakin tilanteissa haluamme suorittaa tai seurata toimintoja näiden vuorovaikutusten välillä. Agenttien middleware mahdollistaa tämän seuraavasti:

*Funktiomiddleware*

Tämä middleware antaa mahdollisuuden suorittaa toiminto agentin ja funktion/työkalun välillä, jota agentti kutsuu. Esimerkki tämän käytöstä on lokituksen tekeminen funktiokutsusta.

Alla olevassa koodissa `next` määrittelee, kutsutaanko seuraava middleware tai varsinainen funktio.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Esikäsittely: Lokita ennen funktion suorittamista
    print(f"[Function] Calling {context.function.name}")

    # Jatka seuraavaan middlewareen tai funktion suorittamiseen
    await next(context)

    # Jälkikäsittely: Lokita funktion suorittamisen jälkeen
    print(f"[Function] {context.function.name} completed")
```

*Chat-middleware*

Tämä middleware mahdollistaa toiminnon suorittamisen tai lokituksen agentin ja LLM:n välisistä pyynnöistä.

Tähän sisältyy tärkeää tietoa, kuten AI-palveluun lähetettävät `messages`.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Esikäsittely: Kirjaa lokiin ennen tekoälykutsua
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Jatka seuraavaan middlewareen tai tekoälypalveluun
    await next(context)

    # Jälkikäsittely: Kirjaa lokiin tekoälyvastauksen jälkeen
    print("[Chat] AI response received")

```

**Agenttimuisti**

Kuten `Agentic Memory` -oppitunnissa käsiteltiin, muisti on tärkeä osa agentin toimintaa eri konteksteissa. MAF tarjoaa useita erilaisia muistityyppejä:

*Muisti sovelluksen suoritusajassa*

Tämä on muisti, jota tallennetaan langoissa sovelluksen käynnin aikana.

```python
# Luo uusi säie.
thread = agent.get_new_thread() # Suorita agentti säikeen kanssa.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Pysyvät viestit*

Tätä muistia käytetään keskusteluhistorian tallentamiseen eri istuntojen välillä. Se määritellään käyttäen `chat_message_store_factory` -asetusta:

```python
from agent_framework import ChatMessageStore

# Luo mukautettu viestivarasto
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynaaminen muisti*

Tämä muisti lisätään kontekstiin ennen agenttien suorittamista. Näitä muisteja voidaan tallentaa ulkoisissa palveluissa kuten mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Käytetään Mem0:aa edistyneisiin muistitoimintoihin
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a helpful assistant with memory.",
    context_providers=memory_provider
)

```

**Agenttien havaittavuus**

Havaittavuus on tärkeää luotettavien ja ylläpidettävien agenttipohjaisten järjestelmien rakentamisessa. MAF integroituu OpenTelemetryyn tarjoten jäljitystä ja mittareita paremman havaittavuuden saavuttamiseksi.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # tee jotain
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Työnkulut

MAF tarjoaa työnkulkuja, jotka ovat ennalta määriteltyjä vaiheita tehtävän suorittamiseksi ja sisältävät tekoälyagentteja osina näitä vaiheita.

Työnkulut koostuvat eri komponenteista, jotka parantavat ohjausvirtausta. Työnkulut mahdollistavat myös **moniagenttien orkestroinnin** ja **tarkistuspisteiden luomisen** työnkulun tilojen tallentamista varten.

Työnkulun ydinkomponentit ovat:

**Suorittajat**

Suorittajat vastaanottavat syöteviestejä, suorittavat määritellyt tehtävänsä ja tuottavat tulosviestin. Tämä vie työnkulkua eteenpäin kohti suuremman tehtävän valmistumista. Suorittaja voi olla joko tekoälyagentti tai mukautettu logiikka.

**Kaaret**

Kaaret määrittelevät viestien virtaamisen työnkulussa. Näitä voivat olla:

*Suorat kaaret* - Yksinkertaisia yksi-yhteen yhteyksiä suorittajien välillä:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Ehdolliset kaaret* - Aktivoituvat, kun tietty ehto täyttyy. Esimerkiksi hotellihuoneiden puuttuessa suorittaja voi ehdottaa vaihtoehtoja.

*Kytkinkaaret* - Reitittävät viestit eri suorittajille määriteltyjen ehtojen mukaan. Esim. jos matkailijalla on prioriteettikäyttöoikeus, hänen tehtävänsä hoidetaan toisen työnkulun kautta.

*Haarautuvat kaaret* - Lähettävät yhden viestin useille kohteille.

*Yhdistyvät kaaret* - Keräävät useita viestejä eri suorittajilta ja lähettävät yhdelle kohteelle.

**Tapahtumat**

Tarjotakseen paremman havaittavuuden työnkulkuihin, MAF tarjoaa sisäänrakennettuja tapahtumia suorituksen eri vaiheissa, kuten:

- `WorkflowStartedEvent`  - Työnkulun suoritus alkaa
- `WorkflowOutputEvent` - Työnkulku tuottaa tuloksen
- `WorkflowErrorEvent` - Työnkulku kohtaa virheen
- `ExecutorInvokeEvent`  - Suorittaja aloittaa käsittelyn
- `ExecutorCompleteEvent`  -  Suorittaja päättää käsittelyn
- `RequestInfoEvent` - Pyyntö lähetetty

## Migraatio muista kehyksistä (Semantic Kernel ja AutoGen)

### Erot MAF:n ja Semantic Kernelin välillä

**Yksinkertaistettu agentin luonti**

Semantic Kernel perustuu Kernel-instanssin luomiseen jokaista agenttia varten. MAF käyttää yksinkertaistettua lähestymistapaa, jossa käytetään laajennuksia pääpalveluntarjoajille.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Agenttilangan luonti**

Semantic Kernelissä langat pitää luoda manuaalisesti. MAF:ssa agentille määritellään suoraan lanka.

```python
thread = agent.get_new_thread() # Suorita agentti säikeellä.
```

**Työkalujen rekisteröinti**

Semantic Kernelissä työkalut rekisteröidään Kernelille ja Kernel välitetään sitten agentille. MAF:ssa työkalut rekisteröidään suoraan agentin luonnin yhteydessä.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Erot MAF:n ja AutoGenin välillä

**Teams vs Työnkulut**

AutoGenissa `Teams`-rakenne hallitsee tapahtumabohjattuja toimintoja agenttien kanssa. MAF käyttää `Workflows`-työnkulkuja, jotka reitittävät dataa suorittajille graafipohjaisen arkkitehtuurin kautta.

**Työkalujen luonti**

AutoGen käyttää `FunctionTool`-luokkaa, joka käärii funktiot agenttien kutsuttaviksi. MAF käyttää @ai_functionia, joka toimii samankaltaisesti, mutta arvaa myös kunkin funktion skeemat automaattisesti.

**Agentin käyttäytyminen**

AutoGenissa agentit ovat oletuksena yksivaiheisia, ellei `max_tool_iterations`-arvoa aseteta korkeammaksi. MAF:ssa `ChatAgent` on oletuksena moni-vaiheinen, eli se jatkaa työkalujen kutsumista, kunnes käyttäjän tehtävä on valmis.

## Koodiesimerkit 

Microsoft Agent Frameworkin koodiesimerkit löytyvät tästä repositoriosta tiedostojen `xx-python-agent-framework` ja `xx-dotnet-agent-framework` alta.

## Onko sinulla lisää kysymyksiä Microsoft Agent Frameworkista?

Liity [Microsoft Foundry Discordiin](https://aka.ms/ai-agents/discord) tavata muita oppijoita, osallistua toimistoaikoihin ja saada vastauksia tekoälyagenttien kysymyksiisi.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Vastuuvapauslauseke**:  
Tämä asiakirja on käännetty tekoälypohjaisella käännöspalvelulla [Co-op Translator](https://github.com/Azure/co-op-translator). Pyrimme tarkkuuteen, mutta automaattikäännöksiin voi sisältyä virheitä tai epätarkkuuksia. Alkuperäinen asiakirja sen alkuperäiskielellä tulee pitää ensisijaisena lähteenä. Tärkeissä asioissa suositellaan ammattilaisen tekemää ihmiskäännöstä. Emme ole vastuussa tämän käännöksen käytöstä aiheutuvista väärinymmärryksistä tai virhetulkinnoista.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->