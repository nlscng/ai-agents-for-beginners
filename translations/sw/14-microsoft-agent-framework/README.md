# Kuchunguza Mfumo wa Wakala wa Microsoft

![Agent Framework](../../../translated_images/sw/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Utangulizi

Somo hili litashughulikia:

- Kuelewa Mfumo wa Wakala wa Microsoft: Vipengele Muhimu na Thamani  
- Kuchunguza Misingi Muhimu ya Mfumo wa Wakala wa Microsoft
- Kulinganisha MAF na Semantic Kernel na AutoGen: Mwongozo wa Kuhamia

## Malengo ya Kujifunza

Baada ya kumaliza somo hili, utajua jinsi ya:

- Kujenga Wakala wa AI Tayari Kutumika kwa uzalishaji ukitumia Mfumo wa Wakala wa Microsoft
- Kutumia vipengele vya msingi vya Mfumo wa Wakala wa Microsoft katika Matumizi Yako ya Wakala
- Kuhamia na kuunganisha mifumo na zana za wakala zilizopo  

## Sampuli za Msimbo 

Sampuli za msimbo kwa [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) zinaweza kupatikana katika hazina hii chini ya faili za `xx-python-agent-framework` na `xx-dotnet-agent-framework`.

## Kuelewa Mfumo wa Wakala wa Microsoft

![Framework Intro](../../../translated_images/sw/framework-intro.077af16617cf130c.webp)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) hujengea juu ya uzoefu na mafunzo kutoka Semantic Kernel na AutoGen. Inatoa unafuu wa kukabiliana na aina mbalimbali za matukio ya matumizi ya wakala yanayoonekana katika mazingira ya uzalishaji na utafiti ikijumuisha:

- **Mratibu wa Wakala wa Mfuatano** katika hali ambapo mchakato wa hatua kwa hatua unahitajika.
- **Mratibu wa Wakala wa Msimulizi Wakati Mmoja** katika hali ambapo mawakala wanahitaji kukamilisha kazi kwa wakati mmoja.
- **Mratibu wa Mazungumzo ya Kundi** katika hali ambapo mawakala wanaweza kushirikiana pamoja kwenye kazi moja.
- **Mratibu wa Kumkabidhi Mwingine** katika hali ambapo mawakala wanakabidhi kazi kwa mwingine wanapo maliza sehemu ndogo za kazi.
- **Mratibu wa Kivutio cha Sumaku** katika hali ambapo wakala msimamizi huunda na kubadilisha orodha ya kazi na kusimamia uratibu wa mawakala wengine ili kukamilisha kazi.

Ili kutoa Wakala wa AI katika Uzalishaji, MAF pia ina vipengele vya:

- **Uangalizi** kupitia matumizi ya OpenTelemetry ambapo kila hatua ya Wakala wa AI ikijumuisha kuitwa kwa zana, hatua za mratibu, mtiririko wa hoja na ufuatiliaji wa utendaji kupitia dashibodi za Microsoft Foundry.
- **Usalama** kwa kuendesha mawakala moja kwa moja kwenye Microsoft Foundry ambayo inajumuisha udhibiti wa usalama kama ufikiaji wa msingi wa majukumu, usimamizi wa data binafsi na usalama wa maudhui uliotengenezwa ndani.
- **Ubinadamu** kwani mriadha na michakato ya wakala inaweza kusimamishwa, kuendelea na kupona kutokana na makosa jambo linalowezesha michakato ya kugonga muda mrefu.
- **Udhibiti** kwani michakato ya mzunguko na wanadamu inasaidiwa ambapo kazi hupimwa kama zinahitaji idhini ya binadamu.

Mfumo wa Wakala wa Microsoft pia umejikita katika kuweza kuendana kwa:

- **Kuwa huru kwa Wingu** - Mawakala wanaweza kuendeshwa ndani ya kontena, kwa mteja mwenyewe na kwenye mawingu mbalimbali.
- **Kuwa huru kwa Mtoa Huduma** - Mawakala yanaweza kuundwa kwa kutumia SDK unayopendelea ikiwa ni pamoja na Azure OpenAI na OpenAI
- **Kuingiza Viwango Wazi** - Mawakala yanaweza kutumia itifaki kama Agent-to-Agent(A2A) na Model Context Protocol (MCP) kugundua na kutumia mawakala na zana nyingine.
- **Viambatisho na Vinuzi** - Muunganisho unaweza kufanywa na huduma za data na kumbukumbu kama Microsoft Fabric, SharePoint, Pinecone na Qdrant.

Tuchunguze jinsi vipengele hivi vinavyotumika katika baadhi ya dhana kuu za Mfumo wa Wakala wa Microsoft.

## Misingi Muhimu ya Mfumo wa Wakala wa Microsoft

### Mawakala

![Agent Framework](../../../translated_images/sw/agent-components.410a06daf87b4fef.webp)

**Kuumba Mawakala**

Uundaji wa wakala hufanywa kwa kufafanua huduma ya uainishaji (Mtoa LLM), seti ya maagizo kwa Wakala wa AI kufuata, na `jina` lililowekwa:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Hapo juu inatumia `Azure OpenAI` lakini mawakala yanaweza kuundwa kwa kutumia huduma mbalimbali ikiwa ni pamoja na `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

API za OpenAI `Responses`, `ChatCompletion`

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

au mawakala wa mbali kwa kutumia itifaki ya A2A:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Kuendesha Mawakala**

Mawakala huendeshwa kwa kutumia mbinu `.run` au `.run_stream` kwa jibu lisilotiririka au lenye mtiririko.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Kila utekelezaji wa wakala unaweza pia kuwa na chaguzi za kubinafsisha vigezo kama `max_tokens` kinachotumiwa na wakala, `tools` ambazo wakala anaweza kuita, na hata `model` yenyewe inayotumiwa na wakala.

Hii ni muhimu katika kesi ambapo mifano au zana maalum zinahitajika kukamilisha kazi ya mtumiaji.

**Zana**

Zana zinaweza kufafanuliwa wakati wa kuunda wakala:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Wakati wa kuunda ChatAgent moja kwa moja

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

na pia wakati wa kuendesha wakala:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Chombo kilichotolewa kwa ajili ya mtihani huu tu )
```

**Miadha ya Wakala**

Miadha ya wakala hutumika kushughulikia mazungumzo yenye vipindi vingi. Miacha inaweza kuundwa kwa:

- Kutumia `get_new_thread()` ambayo inaruhusu mfuatano kuokolewa kwa muda
- Kuunda mfuatano moja kwa moja wakati wa kuendesha wakala na mfuatano huu kukaa tu wakati wa utekelezaji wa sasa.

Kuuza mfuatano, msimbo ni kama hivi:

```python
# Unda thread mpya.
thread = agent.get_new_thread() # Endesha wakala na thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Kisha unaweza kusafirisha mfuatano kuhifadhiwa kwa matumizi ya baadaye:

```python
# Unda kipande kipya cha mfululizo.
thread = agent.get_new_thread() 

# Endesha wakala na kipande cha mfululizo.

response = await agent.run("Hello, how are you?", thread=thread) 

# Fanya serialization ya kipande cha mfululizo kwa ajili ya uhifadhi.

serialized_thread = await thread.serialize() 

# Fanya deserialization ya hali ya kipande cha mfululizo baada ya kupakia kutoka kwa uhifadhi.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Middleware ya Wakala**

Mawakala hufanya kazi na zana na LLMs kukamilisha majukumu ya mtumiaji. Katika baadhi ya hali, tunataka kutekeleza au kufuatilia kati ya mwingiliano huu. Middleware ya wakala inaturuhusu kufanya hivi kupitia:

*Middleware ya Kazi*

Middleware hii inaruhusu kutekeleza tendo kati ya wakala na kazi/zana atakayoitumia. Mfano wa wakati huu utatumika ni pale ambapo unaweza kutaka kufanya upatiliaji wa simu ya kazi.

Katika msimbo hapa chini `next` inafafanua kama middleware inayofuata au kazi halisi inapaswa kuitwa.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Kuhakiki awali: Andika kumbukumbu kabla ya utekelezaji wa kazi
    print(f"[Function] Calling {context.function.name}")

    # Endelea kwa sehemu inayofuata ya kati au utekelezaji wa kazi
    await next(context)

    # Kuhakiki baada: Andika kumbukumbu baada ya utekelezaji wa kazi
    print(f"[Function] {context.function.name} completed")
```

*Middleware ya Mazungumzo*

Middleware hii inaruhusu kutekeleza au kurekodi tendo kati ya wakala na maombi kati ya LLM.

Hii ina taarifa muhimu kama vile `messages` zinazotumwa kwa huduma ya AI.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Utangulizi: Andika kumbukumbu kabla ya simu ya AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Endelea kwenye middleware au huduma ya AI iliyofuata
    await next(context)

    # Uchakataji baadae: Andika kumbukumbu baada ya majibu ya AI
    print("[Chat] AI response received")

```

**Kumbukumbu ya Wakala**

Kama ilivyosomwa katika somo la `Kumbukumbu ya Wakala`, kumbukumbu ni kipengele muhimu kuwezesha wakala kufanya kazi kwenye muktadha tofauti. MAF hutoa aina kadhaa za kumbukumbu:

*Kumbukumbu ya Ndani ya Mfuatano*

Hii ni kumbukumbu iliyohifadhiwa katika miacha wakati wa utekelezaji wa programu.

```python
# Unda thread mpya.
thread = agent.get_new_thread() # Endesha wakala na thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Ujumbe wa Kudumu*

Kumbukumbu hii hutumiwa kuhifadhi historia ya mazungumzo kati ya vikao tofauti. Hufafanuliwa kwa kutumia `chat_message_store_factory`:

```python
from agent_framework import ChatMessageStore

# Unda duka la ujumbe la kawaida
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Kumbukumbu ya Kijumuishi*

Kumbukumbu hii inaongezwa katika muktadha kabla ya mawakala kuendeshwa. Kumbukumbu hizi zinaweza kuhifadhiwa katika huduma za nje kama mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Kutumia Mem0 kwa uwezo wa hali ya juu wa kumbukumbu
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

**Uangalifu wa Wakala**

Uangalifu ni muhimu kwa kujenga mifumo ya kuaminika na rahisi kudumisha. MAF inaunganisha na OpenTelemetry kutoa ufuatiliaji na vipimo vya uangalifu bora.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # fanya jambo mmoja
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Miaradi ya Kazi

MAF hutoa miaradi ya kazi ambayo ni hatua zilizowekwa za kumaliza kazi na zinajumuisha mawakala wa AI kama vipengele katika hatua hizo.

Miaradi ya kazi inaundwa na vipengele tofauti vinavyoruhusu mtiririko bora wa udhibiti. Miaradi pia inaruhusu **uratibu wa mawakala wengi** na **uhifadhi wa alama** kuhifadhi hali za mchakato wa kazi.

Vipengele vikuu vya mchakato ni:

**Watekelezaji**

Watekelezaji hupokea ujumbe wa kuingiza, kutekeleza kazi walizopangiwa, kisha kutoa ujumbe wa matokeo. Hii husogeza mchakato wa kazi mbele kuelekea kukamilisha kazi kubwa zaidi. Watekelezaji wanaweza kuwa wakala wa AI au mantiki maalum.

**Mikondo**

Mikondo hutumika kufafanua mtiririko wa ujumbe katika mchakato wa kazi. Hizi zinaweza kuwa:

*Mikondo ya Moja kwa Moja* - Muunganiko rahisi wa mtu moja kwa moja kati ya watekelezaji:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Mikondo ya Masharti* - Huitishwa baada ya sharti fulani kutimizwa. Kwa mfano, wakati vyumba vya hoteli havipatikani, mtekelezaji anaweza kupendekeza chaguzi nyingine.

*Mikondo ya Switch-case* - Huweka ujumbe kwa watekelezaji tofauti kwa kuzingatia masharti yaliyowekwa. Kwa mfano, mteja wa usafiri ana ufikiaji wa kipaumbele na kazi zao zitatatuliwa kupitia mchakato mwingine.

*Mikondo ya Fan-out* - Kutuma ujumbe mmoja kwa malengo mengi.

*Mikondo ya Fan-in* - Kukusanya ujumbe nyingi kutoka kwa watekelezaji tofauti na kutuma kwa lengo moja.

**Matukio**

Ili kutoa uangalizi bora katika mchakato wa kazi, MAF hutoa matukio ya ndani kwa ajili ya utekelezaji ikijumuisha:

- `WorkflowStartedEvent`  - Utekelezaji wa mchakato wa kazi unaanza
- `WorkflowOutputEvent` - Mchakato wa kazi hutoa matokeo
- `WorkflowErrorEvent` - Mchakato wa kazi unakutana na hitilafu
- `ExecutorInvokeEvent`  - Mtekelezaji anaanza kazi
- `ExecutorCompleteEvent`  -  Mtekelezaji anamaliza kazi
- `RequestInfoEvent` - Ombi limewasilishwa

## Kuhamia Kutoka kwa Mifumo Mingine (Semantic Kernel na AutoGen)

### Tofauti kati ya MAF na Semantic Kernel

**Kuumba Wakala kwa Rahisi**

Semantic Kernel hutegemea kuunda mfano wa Kernel kwa kila wakala. MAF ina njia rahisi zaidi kwa kutumia viendelezi kwa watoa huduma wakuu.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Uundaji wa Mfuatano wa Wakala**

Semantic Kernel inahitaji miacha kuundwa kwa mkono. Katika MAF, wakala huchukuliwa moja kwa moja mfuatano.

```python
thread = agent.get_new_thread() # Endesha wakala kwa kipande cha pande.
```

**Usajili wa Zana**

Katika Semantic Kernel, zana husajiliwa kwa Kernel kisha Kernel hutikishwa kwa wakala. Katika MAF, zana husajiliwa moja kwa moja wakati wa kuunda wakala.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Tofauti kati ya MAF na AutoGen

**Timu dhidi ya Miaradi ya Kazi**

`Timu` ni muundo wa matukio kwa shughuli zinazoendeshwa kwa matukio na mawakala katika AutoGen. MAF hutumia `Miaradi ya Kazi` inayotumia nakala za grafu kusambaza data kwa watekelezaji.

**Uumbaji wa Zana**

AutoGen hutumia `FunctionTool` kufunga kazi kwa mawakala kuitisha. MAF hutumia @ai_function ambayo hufanya kazi kwa njia sawa lakini pia hutabiri miundo kiotomatiki kwa kila kazi.

**Tabia ya Wakala**

Mawakala ni wakala wa mzunguko mmoja kwa chaguo-msingi katika AutoGen isipokuwa `max_tool_iterations` imewekwa juu. Ndani ya MAF `ChatAgent` ni wakala wa mzunguko mingi kwa chaguo-msingi, ikimaanisha anaendelea kuitisha zana mpaka kazi ya mtumiaji itakapokamilika.

## Sampuli za Msimbo 

Sampuli za msimbo kwa Mfumo wa Wakala wa Microsoft zinaweza kupatikana katika hazina hii chini ya faili za `xx-python-agent-framework` na `xx-dotnet-agent-framework`.

## Una Maswali Zaidi Kuhusu Mfumo wa Wakala wa Microsoft?

Jiunge na [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) kukutana na wanafunzi wengine, kuhudhuria saa za ofisi na kupata majibu ya maswali yako kuhusu Mawakala wa AI.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Kataa**:
Nyaraka hii imetafsiriwa kwa kutumia huduma ya tafsiri ya AI [Co-op Translator](https://github.com/Azure/co-op-translator). Ingawa tunajitahidi kwa usahihi, tafadhali fahamu kuwa tafsiri za kiotomatiki zinaweza kuwa na makosa au kasoro. Nyaraka asili katika lugha yake ya mzazi inapaswa kuzingatiwa kama chanzo cha mamlaka. Kwa taarifa muhimu, tafsiri ya kitaalamu na ya kibinadamu inapendekezwa. Hatubebeki wajibu wowote kwa kutoelewana au tafsiri potofu zinazotokana na matumizi ya tafsiri hii.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->