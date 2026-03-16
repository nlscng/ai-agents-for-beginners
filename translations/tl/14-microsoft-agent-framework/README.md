# Pagsusuri sa Microsoft Agent Framework

![Agent Framework](../../../translated_images/tl/lesson-14-thumbnail.90df0065b9d234ee.webp)

### Panimula

Saklaw ng araling ito:

- Pag-unawa sa Microsoft Agent Framework: Mga Pangunahing Katangian at Halaga  
- Pagsusuri sa Mga Pangunahing Konsepto ng Microsoft Agent Framework
- Paghahambing ng MAF sa Semantic Kernel at AutoGen: Gabay sa Paglilipat

## Mga Layunin sa Pagkatuto

Pagkatapos makumpleto ang araling ito, malalaman mo kung paano:

- Gumawa ng Production Ready AI Agents gamit ang Microsoft Agent Framework
- I-apply ang mga pangunahing katangian ng Microsoft Agent Framework sa iyong mga Agentic Use Cases
- Maglilipat at mag-integrate ng mga umiiral na Agentic frameworks at tools  

## Mga Halimbawang Code 

Makikita ang mga halimbawang code para sa [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) sa repositoryong ito sa ilalim ng `xx-python-agent-framework` at `xx-dotnet-agent-framework` na mga file.

## Pag-unawa sa Microsoft Agent Framework

![Framework Intro](../../../translated_images/tl/framework-intro.077af16617cf130c.webp)

Ang [Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) ay itinatayo sa karanasan at mga aral mula sa Semantic Kernel at AutoGen. Nag-aalok ito ng kakayahang tugunan ang malawak na sari-saring agentic use cases na nakikita sa parehong produksyon at mga kapaligiran ng pananaliksik kabilang ang:

- **Pagsunod-sunod na Agent orchestration** sa mga senaryo kung saan kinakailangan ang step-by-step workflows.
- **Sabayang orchestration** sa mga senaryo kung saan kailangang tapusin ng mga agents ang mga gawain nang sabay-sabay.
- **Group chat orchestration** sa mga senaryo kung saan maaaring magtulungan ang mga agents sa isang gawain.
- **Handoff Orchestration** sa mga senaryo kung saan ipinapasa ng mga agents ang gawain sa isa’t isa habang natatapos ang mga subtasks.
- **Magnetic Orchestration** sa mga senaryo kung saan ang isang manager agent ay lumilikha at nagbabago ng listahan ng gawain at humahawak sa koordinasyon ng mga subagents upang matapos ang gawain.

Upang makapaghatid ng AI Agents sa Produksyon, mayroong mga tampok ang MAF para sa:

- **Observability** sa pamamagitan ng paggamit ng OpenTelemetry kung saan bawat aksyon ng AI Agent kabilang ang tool invocation, mga hakbang ng orchestration, reasoning flows, at performance monitoring sa pamamagitan ng mga Microsoft Foundry dashboard.
- **Seguridad** sa pamamagitan ng pag-host ng mga agents nang native sa Microsoft Foundry na may mga kontrol sa seguridad tulad ng role-based access, private data handling, at built-in content safety.
- **Katatagan** dahil ang mga thread at workflows ng Agent ay maaaring mag-pause, mag-resume, at mag-recover mula sa mga error na nagbibigay-daan sa mas mahabang proseso.
- **Kontrol** dahil sinusuportahan ang human in the loop workflows kung saan minamarkahan bilang nangangailangan ng human approval ang mga gawain.

Nakatuon din ang Microsoft Agent Framework sa pagiging interoperable sa pamamagitan ng:

- **Hindi naka-depende sa Cloud** - Maaaring tumakbo ang mga agents sa mga containers, on-prem, at sa iba't ibang mga cloud.
- **Hindi naka-depende sa Provider** - Maaaring malikha ang mga agents gamit ang iyong nais na SDK kabilang ang Azure OpenAI at OpenAI
- **Pagsasama ng Open Standards** - Maaaring gumamit ang mga agents ng mga protocol tulad ng Agent-to-Agent (A2A) at Model Context Protocol (MCP) upang matuklasan at magamit ang ibang agents at tools.
- **Plugins at Connectors** - Maaaring makipag-ugnayan sa mga data at memory services gaya ng Microsoft Fabric, SharePoint, Pinecone, at Qdrant.

Tingnan natin kung paano inaaplay ang mga tampok na ito sa ilan sa mga pangunahing konsepto ng Microsoft Agent Framework.

## Pangunahing Konsepto ng Microsoft Agent Framework

### Mga Agent

![Agent Framework](../../../translated_images/tl/agent-components.410a06daf87b4fef.webp)

**Paglikha ng Mga Agent**

Ang paglikha ng agent ay ginagawa sa pamamagitan ng pagtatakda ng inference service (LLM Provider), isang
set ng mga tagubilin na susundin ng AI Agent, at isang itinalagang `name`:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

Gumagamit ang nasa itaas ng `Azure OpenAI` pero maaaring malikha ang mga agent gamit ang iba't ibang serbisyo kabilang ang `Microsoft Foundry Agent Service`:

```python
AzureAIAgentClient(async_credential=credential).create_agent( name="HelperAgent", instructions="You are a helpful assistant." ) as agent
```

OpenAI `Responses`, `ChatCompletion` APIs

```python
agent = OpenAIResponsesClient().create_agent( name="WeatherBot", instructions="You are a helpful weather assistant.", )
```

```python
agent = OpenAIChatClient().create_agent( name="HelpfulAssistant", instructions="You are a helpful assistant.", )
```

o mga remote agents gamit ang A2A protocol:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**Pagpapatakbo ng Mga Agent**

Pinapatakbo ang mga agents gamit ang `.run` o `.run_stream` na mga pamamaraan para sa non-streaming o streaming na mga tugon.

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

Maaaring magkaroon ng mga option ang bawat pagpapatakbo ng agent para i-customize ang mga parameter tulad ng `max_tokens` na ginagamit ng agent, `tools` na maaaring tawagan ng agent, at maging ang `model` mismo na ginagamit para sa agent.

Kapaki-pakinabang ito sa mga kaso kung saan kinakailangan ang tiyak na mga modelo o tool para matapos ang gawain ng gumagamit.

**Mga Tools**

Maaaring idefine ang mga tool kapwa sa pagtukoy sa agent:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# Kapag direktang lumilikha ng isang ChatAgent

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

at kapag pinapatakbo ang agent:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # Kasangkapang ibinigay para lamang sa pagtakbo na ito )
```

**Agent Threads**

Ginagamit ang Agent Threads para hawakan ang multi-turn conversations. Maaaring malikha ang mga thread sa pamamagitan ng:

- Paggamit ng `get_new_thread()` na nagbibigay-daan sa thread na mai-save sa paglipas ng panahon
- Awtomatikong paggawa ng thread kapag pinapatakbo ang agent at tumatagal lamang ang thread sa kasalukuyang pagpapatakbo.

Ganito ang hitsura ng code para gumawa ng thread:

```python
# Gumawa ng bagong thread.
thread = agent.get_new_thread() # Patakbuhin ang agent gamit ang thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

Maaari mong i-serialize ang thread para itago para sa paggamit sa hinaharap:

```python
# Gumawa ng bagong thread.
thread = agent.get_new_thread() 

# Patakbuhin ang ahente gamit ang thread.

response = await agent.run("Hello, how are you?", thread=thread) 

# I-serialize ang thread para sa pag-iimbak.

serialized_thread = await thread.serialize() 

# I-deserialize ang estado ng thread pagkatapos mag-load mula sa imbakan.

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**Agent Middleware**

Nakikipag-ugnayan ang mga agent sa mga tool at LLM upang matapos ang mga gawain ng gumagamit. Sa ilang mga senaryo, nais nating magpatupad o mag-track sa pagitan ng mga pakikipag-ugnayang ito. Pinapahintulutan tayo ng agent middleware na gawin ito sa pamamagitan ng:

*Function Middleware*

Pinapayagan tayo ng middleware na ito na magpatupad ng aksyon sa pagitan ng agent at isang function/tool na tatawagin nito. Halimbawa kung kailan ito gagamitin ay kapag nais mong mag-log ng function call.

Sa code sa ibaba, tinutukoy ng `next` kung ang susunod na middleware o ang aktwal na function ang tatawagin.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # Pre-processing: Mag-log bago ang pagpapatupad ng function
    print(f"[Function] Calling {context.function.name}")

    # Magpatuloy sa susunod na middleware o pagpapatupad ng function
    await next(context)

    # Post-processing: Mag-log matapos ang pagpapatupad ng function
    print(f"[Function] {context.function.name} completed")
```

*Chat Middleware*

Pinapayagan tayo ng middleware na ito na magpatupad o mag-log ng aksyon sa pagitan ng agent at ng mga request papunta sa LLM.

Naglalaman ito ng mahalagang impormasyon tulad ng `messages` na ipinapadala sa AI service.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # Pre-proseso: Mag-log bago ang tawag sa AI
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # Magpatuloy sa susunod na middleware o serbisyo ng AI
    await next(context)

    # Post-proseso: Mag-log pagkatapos ng tugon ng AI
    print("[Chat] AI response received")

```

**Agent Memory**

Tulad ng tinalakay sa `Agentic Memory` na leksyon, mahalaga ang memorya upang payagan ang agent na mag-operate sa iba't ibang mga konteksto. Nag-aalok ang MAF ng ilang uri ng memorya:

*In-Memory Storage*

Ito ay ang memorya na iniimbak sa mga thread habang tumatakbo ang aplikasyon.

```python
# Lumikha ng bagong thread.
thread = agent.get_new_thread() # Patakbuhin ang ahente gamit ang thread.
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*Persistent Messages*

Ang memoryang ito ay ginagamit sa pag-iimbak ng kasaysayan ng pag-uusap sa iba't ibang sesyon. Ito ay tinutukoy gamit ang `chat_message_store_factory` :

```python
from agent_framework import ChatMessageStore

# Gumawa ng pasadyang tindahan ng mensahe
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*Dynamic Memory*

Idinadagdag ang memoryang ito sa konteksto bago patakbuhin ang mga agents. Maaaring iimbak ang mga memoryang ito sa mga external services tulad ng mem0:

```python
from agent_framework.mem0 import Mem0Provider

# Paggamit ng Mem0 para sa mga advanced na kakayahan sa memorya
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

**Agent Observability**

Mahalaga ang observability sa pagtayo ng mga maaasahan at madaling panatilihing agentic system. Nag-iintegrate ang MAF sa OpenTelemetry upang magbigay ng tracing at meters para sa mas mahusay na observability.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # gumawa ng isang bagay
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### Mga Workflows

Nag-aalok ang MAF ng mga workflows na pre-defined na mga hakbang upang matapos ang isang gawain at kinabibilangan ng AI agents bilang mga bahagi sa mga hakbang na iyon.

Binubuo ang mga workflow ng iba't ibang mga bahagi na nagpapahintulot ng mas mahusay na daloy ng kontrol. Pinapayagan din ng mga workflow ang **multi-agent orchestration** at **checkpointing** upang mai-save ang mga estado ng workflow.

Ang mga pangunahing bahagi ng isang workflow ay:

**Executors**

Tumanggap ang executors ng input messages, isinasagawa ang kanilang itinalagang mga gawain, at pagkatapos ay nagpo-produce ng output message. Inihahatid nito ang workflow patawid sa pagtatapos ng mas malaking gawain. Maaaring AI agent o custom logic ang mga executors.

**Edges**

Ginagamit ang edges upang tukuyin ang daloy ng mga mensahe sa isang workflow. Maaari itong maging:

*Direct Edges* - Simpleng one-to-one connection sa pagitan ng mga executors:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*Conditional Edges* - Naka-activate kapag natugunan ang isang kondisyon. Halimbawa, kapag hindi available ang mga hotel rooms, maaaring magmungkahi ang executor ng iba pang opsyon.

*Switch-case Edges* - Nag-u-route ng mga mensahe sa iba't ibang executors batay sa mga itinakdang kondisyon. Halimbawa, kung ang customer sa travel ay may priority access, hahawakan ang kanilang mga gawain sa pamamagitan ng ibang workflow.

*Fan-out Edges* - Nagpapadala ng isang mensahe sa maraming target.

*Fan-in Edges* - Nangongolekta ng maraming mensahe mula sa iba't ibang executors at nagpapadala sa isang target.

**Events**

Upang magbigay ng mas mahusay na observability sa mga workflows, nag-aalok ang MAF ng built-in na mga event para sa pagpapatupad kabilang ang:

- `WorkflowStartedEvent`  - Nagsisimula ang pagpapatakbo ng workflow
- `WorkflowOutputEvent` - Nagbibigay ng output ang workflow
- `WorkflowErrorEvent` - Nakaranas ng error ang workflow
- `ExecutorInvokeEvent`  - Nagsimula ang executor sa pagproseso
- `ExecutorCompleteEvent`  - Natapos ng executor ang pagproseso
- `RequestInfoEvent` - Na-issue ang isang request

## Paglilipat Mula sa Ibang Frameworks (Semantic Kernel at AutoGen)

### Mga Pagkakaiba sa pagitan ng MAF at Semantic Kernel

**Pinadaling Paglikha ng Agent**

Nangangailangan ang Semantic Kernel ng paglikha ng Kernel instance para sa bawat agent. Gumagamit ang MAF ng pinasimpleng paraan sa pamamagitan ng paggamit ng extensions para sa mga pangunahing provider.

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**Paglikha ng Agent Thread**

Kinakailangan ng Semantic Kernel na manu-manong malikha ang mga thread. Sa MAF, direktang itinalaga sa agent ang thread.

```python
thread = agent.get_new_thread() # Patakbuhin ang ahente gamit ang thread.
```

**Pagre-register ng Tool**

Sa Semantic Kernel, nirerehistro ang mga tool sa Kernel at inililipat ang Kernel sa agent. Sa MAF, direktang nirerehistro ang mga tools habang nililikha ang agent.

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### Mga Pagkakaiba sa pagitan ng MAF at AutoGen

**Teams kumpara sa Workflows**

Ang `Teams` ay ang estruktura ng event para sa event driven na aktibidad kasama ang mga agent sa AutoGen. Gumagamit ang MAF ng `Workflows` na nag-u-route ng data sa mga executors sa pamamagitan ng arkitekturang graph based.

**Paglikha ng Tool**

Gumagamit ang AutoGen ng `FunctionTool` para balutin ang mga function na tatawagin ng mga agent. Gumagamit ang MAF ng @ai_function na gumagana nang katulad ngunit awtomatikong tinutukoy ang mga schema para sa bawat function.

**Pag-uugali ng Agent**

Ang mga agent sa AutoGen ay single-turn agent bilang default maliban kung itinakda ang `max_tool_iterations` sa mas mataas na halaga. Sa MAF, ang `ChatAgent` ay multi-turn bilang default ibig sabihin ay patuloy itong tatawag ng mga tools hanggang matapos ang gawain ng gumagamit.

## Mga Halimbawang Code 

Makikita ang mga halimbawang code para sa Microsoft Agent Framework sa repositoryong ito sa ilalim ng `xx-python-agent-framework` at `xx-dotnet-agent-framework` na mga file.

## May Karagdagang Mga Tanong Tungkol sa Microsoft Agent Framework?

Sumali sa [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) upang makipagkita sa ibang mga nag-aaral, dumalo sa mga office hours, at makakuha ng sagot sa iyong mga tanong tungkol sa AI Agents.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Paunawa**:
Ang dokumentong ito ay isinalin gamit ang AI translation service na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagama't nagsusumikap kaming maging tumpak, pakatandaan na ang mga awtomatikong salin ay maaaring maglaman ng mga pagkakamali o maling interpretasyon. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring na pangunahing sanggunian. Para sa mga mahalagang impormasyon, inirerekomenda ang propesyonal na pagsasaling tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling pagkaintindi na dulot ng paggamit ng salin na ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->