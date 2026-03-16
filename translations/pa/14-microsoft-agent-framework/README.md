# ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਦਾ ਅਨੁਸੰਧਾਨ

![Agent Framework](../../../translated_images/pa/lesson-14-thumbnail.90df0065b9d234ee.webp)

### ਪਰੀਚਯ

ਇਸ ਪਾਠ ਵਿੱਚ ਸ਼ਾਮਲ ਹਨ:

- ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਦੀ ਸਮਝ: ਮੁੱਖ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਅਤੇ ਮੁੱਲ  
- ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਦੇ ਮੁੱਖ ਸੰਕਲਪਾਂ ਦੀ ਪੜਚੋਲ
- MAF ਨੂੰ Semantic Kernel ਅਤੇ AutoGen ਨਾਲ ਤੁਲਨਾ ਕਰਨਾ: ਮਾਈਗ੍ਰੇਸ਼ਨ ਗਾਈਡ

## ਸਿੱਖਣ ਦੇ ਲੱਛਣ

ਇਸ ਪਾਠ ਨੂੰ ਪੂਰਾ ਕਰਨ ਤੋਂ ਬਾਅਦ, ਤੁਸੀਂ ਜਾਣੋਂਗੇ ਕਿ ਕਿਵੇਂ:

- ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਪ੍ਰੋਡਕਸ਼ਨ ਤਿਆਰ AI ਏਜੰਟ ਬਣਾਏ ਜਾ ਸਕਦੇ ਹਨ
- ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਦੀਆਂ ਮੁੱਖ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਨੂੰ ਆਪਣੇ ਏਜੰਟਿਕ ਕੇਸਾਂ ਵਿੱਚ ਲਾਗੂ ਕੀਤਾ ਜਾ ਸਕਦਾ ਹੈ
- ਮੌਜੂਦਾ ਏਜੰਟਿਕ ਫਰੇਮਵਰਕ ਅਤੇ ਟੂਲਾਂ ਨੂੰ ਮਾਈਗ੍ਰੇਟ ਅਤੇ ਇੰਟੀਗਰੇਟ ਕੀਤਾ ਜਾ ਸਕਦਾ ਹੈ  

## ਕੋਡ ਨਮੂਨੇ

[ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) ਲਈ ਕੋਡ ਨਮੂਨੇ ਇਸ ਰਿਪੋਜ਼ਟਰੀ ਵਿਚ `xx-python-agent-framework` ਅਤੇ `xx-dotnet-agent-framework` ਫਾਇਲਾਂ ਹੇਠਾਂ ਮਿਲ ਸਕਦੇ ਹਨ।

## ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਦੀ ਸਮਝ

![Framework Intro](../../../translated_images/pa/framework-intro.077af16617cf130c.webp)

[ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok) Semantic Kernel ਅਤੇ AutoGen ਤੋਂ ਪ੍ਰਾਪਤ ਅਨੁਭਵ ਅਤੇ ਸਿੱਖਿਆ 'ਤੇ ਆਧਾਰਿਤ ਹੈ। ਇਹ ਪ੍ਰੋਡਕਸ਼ਨ ਅਤੇ ਖੋਜ ਵਾਤਾਵਰਣਾਂ ਵਿੱਚ ਵੇਖੇ ਗਏ ਵੱਖ-ਵੱਖ ਤਰ੍ਹਾਂ ਦੇ ਏਜੰਟਿਕ ਯੂਜ਼ ਕੇਸਾਂ ਨੂੰ ਸੰਬੋਧਨ ਦੇਣ ਲਈ ਲਚਕੀਲਾ ਹੈ, ਜਿਵੇਂ:

- ਐਸਸੀਕੁਐਂਸ਼ਲ ਏਜੰਟ ਆਰਕੇਸਟਰੈਸ਼ਨ ਉਹ ਸਥਿਤੀਆਂ ਜਿੱਥੇ ਕਦਮ-ਦਰ-ਕਦਮ ਵਰਕਫਲੋਜ਼ ਦੀ ਲੋੜ ਹੁੰਦੀ ਹੈ।
- ਸੰਕਲਿਤ ਆਰਕੇਸਟਰੈਸ਼ਨ ਉਹ ਸਥਿਤੀਆਂ ਜਿੱਥੇ ਏਜੰਟ ਇੱਕੋ ਸਮੇਂ ਕੰਮ ਪੂਰੇ ਕਰਨੇ ਹੁੰਦੇ ਹਨ।
- ਗਰੁੱਪ ਚੈਟ ਆਰਕੇਸਟਰੈਸ਼ਨ ਉਹ ਸਥਿਤੀਆਂ ਜਿੱਥੇ ਏਜੰਟ ਇੱਕ ਕੰਮ 'ਤੇ ਇਕੱਠੇ ਸਹਿਯੋਗ ਕਰ ਸਕਦੇ ਹਨ।
- ਹੈਂਡਆਫ ਆਰਕੇਸਟਰੈਸ਼ਨ ਉਹ ਸਥਿਤੀਆਂ ਜਿੱਥੇ ਏਜੰਟ ਇੱਕ-ਦੂਜੇ ਨੂੰ ਕੰਮ ਸੌਂਪਦੇ ਹਨ ਜਿਵੇਂ ਜ ਸੋਟਾਸਕ ਪੂਰੇ ਕੀਤੇ ਜਾਂਦੇ ਹਨ।
- ਮੈਗਨੇਟਿਕ ਆਰਕੇਸਟਰੈਸ਼ਨ ਉਹ ਸਥਿਤੀਆਂ ਜਿੱਥੇ ਮੈਨੇਜਰ ਏਜੰਟ ਕੰਮ ਦੀ ਸੂਚੀ ਬਣਾਉਂਦਾ ਅਤੇ ਸੋਧਦਾ ਹੈ ਅਤੇ ਸਬਏਜੰਟਸ ਦੀ ਸਹਿਯੋਜਨਾ ਕਰਦਾ ਹੈ ਤਾਂ ਜੋ ਕੰਮ ਪੂਰਾ ਕੀਤਾ ਜਾ ਸਕੇ।

ਪ੍ਰੋਡਕਸ਼ਨ ਵਿੱਚ AI ਏਜੰਟਸ ਪ੍ਰਦਾਨ ਕਰਨ ਲਈ, MAF ਵਿੱਚ ਹੇਠ ਲਿਖੀਆਂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਸ਼ਾਮਲ ਕੀਤੀਆਂ ਗਈਆਂ ਹਨ:

- OpenTelemetry ਰਾਹੀਂ **ਦੇਖਭਾਲਯੋਗਤਾ**, ਜਿੱਥੇ AI ਏਜੰਟ ਦੀ ਹਰ ਕ੍ਰਿਆ ਵਿੱਚ ਟੂਲ ਕਾਲ, ਆਰਕੇਸਟਰੈਸ਼ਨ ਕਦਮ, ਵਿਚਾਰ ਪ੍ਰਵਾਹ ਅਤੇ Microsoft Foundry ਡੈਸ਼ਬੋਰਡ ਦੁਆਰਾ ਪ੍ਰਦਰਸ਼ਨ ਨਿਗਰਾਨੀ ਸ਼ਾਮਲ ਹੈ।
- Microsoft Foundry 'ਤੇ ਨੈਟਿਵ ਤੌਰ 'ਤੇ ਏਜੰਟਸ ਹੋਸਟ ਕਰਕੇ **ਸੁਰੱਖਿਆ**, ਜਿਸ ਵਿੱਚ ਭੂਮਿਕਾ-ਆਧਾਰਿਤ ਪਹੁੰਚ, ਪ੍ਰਾਈਵੇਟ ਡੇਟਾ ਹੈਂਡਲਿੰਗ ਅਤੇ ਬਿਲਟ-ਇਨ ਸਮੱਗਰੀ ਸੁਰੱਖਿਆ ਜਿਹੇ ਨਿਯੰਤਰਣ ਹਨ।
- **ਟਕਸਾਲਪਣ** ਕਿਉਂਕਿ ਏਜੰਟ ਧਾਗੇ ਅਤੇ ਵਰਕਫਲੋਜ਼ ਰੁਕ ਸਕਦੇ ਹਨ, ਮੁੜ ਸ਼ੁਰੂ ਹੋ ਸਕਦੇ ਹਨ ਅਤੇ ਗਲਤੀਆਂ ਤੋਂ ਬਚ ਸਕਦੇ ਹਨ, ਜੋ ਲੰਬੇ ਸਮੇਂ ਚੱਲਣ ਵਾਲੇ ਪ੍ਰਕਿਰਿਆਵਾਂ ਦੀ ਸਹੂਲਤ ਦਿੰਦਾ ਹੈ।
- **ਕੰਟਰੋਲ** ਕਿਉਂਕਿ ਮਨੁੱਖੀ ਰੁਕਾਵਟ ਵਾਲੇ ਵਰਕਫਲੋਜ਼ ਦਾ ਸਮਰਥਨ ਕੀਤਾ ਜਾਂਦਾ ਹੈ ਜਿੱਥੇ ਕੰਮ ਮਨੁੱਖੀ ਮਨਜ਼ੂਰੀ ਦੀ ਲੋੜ ਵਾਲੇ ਵਜੋਂ ਨਿਸ਼ਾਨਿਤ ਕੀਤੇ ਜਾਂਦੇ ਹਨ।

ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਦੀ ਧਿਆਨ ਯੋਗ ਗੱਲ ਇਹ ਹੈ ਕਿ ਇਹ ਹਰ ਕਿਸਮ ਨਾਲ ਇੰਟਰਆਪਰੇਬਲ ਵਾਲਾ ਹੈ:

- **ਕਲਾਉਡ-ਅਗਨੋਸਟਿਕ** - ਏਜੰਟ ਕੰਟੇਨਰਾਂ ਵਿੱਚ, ਓਨ-ਪ੍ਰੇਮ ਅਤੇ ਵੱਖ ਵੱਖ ਕਲਾਉਡਾਂ ਵਿੱਚ ਚੱਲ ਸਕਦੇ ਹਨ।
- **ਪ੍ਰੋਵਾਈਡਰ-ਅਗਨੋਸਟਿਕ** - ਆਪਣੇ ਪਸੰਦੀਦਾ SDK ਨਾਲ ਏਜੰਟ ਬਣਾਏ ਜਾ ਸਕਦੇ ਹਨ ਜਿਵੇਂ Azure OpenAI ਅਤੇ OpenAI
- **ਖੁੱਲ੍ਹੇ ਮਿਆਰੀ ਪ੍ਰੋਟੋਕੋਲਾਂ ਨਾਲ ਸਮਰਥਨ** - ਏਜੰਟ Agent-to-Agent (A2A) ਅਤੇ Model Context Protocol (MCP) ਵਰਗੇ ਪ੍ਰੋਟੋਕੋਲਾਂ ਦੀ ਵਰਤੋਂ ਕਰ ਸਕਦੇ ਹਨ ਡੂਜਿਆਂ ਏਜੰਟਸ ਅਤੇ ਟੂਲਾਂ ਨੂੰ ਖੋਜਣ ਅਤੇ ਵਰਤਣ ਲਈ।
- **ਪਲੱਗਇਨ ਅਤੇ ਕਨੈਕਟਰ** - Microsoft Fabric, SharePoint, Pinecone ਅਤੇ Qdrant ਵਰਗੀਆਂ ਡਾਟਾ ਅਤੇ ਮੈਮੋਰੀ ਸਰਵਿਸਿਜ਼ ਨਾਲ ਕਨੈਕਸ਼ਨ ਬਣਾਏ ਜਾ ਸਕਦੇ ਹਨ।

ਚਲੋ ਵੇਖੀਏ ਕਿ ਇਹ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਦੇ ਕੁਝ ਮੁੱਖ ਸੰਕਲਪਾਂ ਨਾਲ ਕਿਵੇਂ ਲਾਗੂ ਕੀਤੀਆਂ ਜਾਂਦੀਆਂ ਹਨ।

## ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਦੇ ਮੁੱਖ ਸੰਕਲਪ

### ਏਜੰਟਸ

![Agent Framework](../../../translated_images/pa/agent-components.410a06daf87b4fef.webp)

**ਏਜੰਟ ਬਣਾਉਣਾ**

ਏਜੰਟ ਬਣਾਉਣਾ inference service (LLM ਪ੍ਰੋਵਾਈਡਰ), AI ਏਜੰਟ ਦੇ ਲਈ ਹਿਦਾਇਤਾਂ ਦਾ ਸੈੱਟ, ਅਤੇ ਨਿਰਧਾਰਤ `name` ਨੂੰ ਪਰिभਾਸ਼ਿਤ ਕਰਕੇ ਕੀਤਾ ਜਾਂਦਾ ਹੈ:

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at recommending trips to customers based on their preferences.", name="TripRecommender" )
```

ਉੱਪਰ ਦਿੱਤਾ ਕੋਡ `Azure OpenAI` ਦੀ ਵਰਤੋਂ ਕਰ ਰਿਹਾ ਹੈ ਪਰ ਏਜੰਟ ਵੱਖ-ਵੱਖ ਸਰਵਿਸਿਜ਼ ਜਿਵੇਂ `Microsoft Foundry Agent Service` ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਬਣਾਏ ਜਾ ਸਕਦੇ ਹਨ:

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

ਜਾਂ A2A ਪ੍ਰੋਟੋਕੋਲ ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹੋਏ ਰੀਮੋਟ ਏਜੰਟ:

```python
agent = A2AAgent( name=agent_card.name, description=agent_card.description, agent_card=agent_card, url="https://your-a2a-agent-host" )
```

**ਏਜੰਟ ਚਲਾਉਣਾ**

ਏਜੰਟ ਨੂੰ `.run` ਜਾਂ `.run_stream` ਮੈਥਡਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਚਲਾਇਆ ਜਾਂਦਾ ਹੈ ਜੇਕਰ ਨਾ-ਸਟ੍ਰੀਮਿੰਗ ਜਾਂ ਸਟ੍ਰੀਮਿੰਗ ਜਵਾਬ ਲਈ।

```python
result = await agent.run("What are good places to visit in Amsterdam?")
print(result.text)
```

```python
async for update in agent.run_stream("What are the good places to visit in Amsterdam?"):
    if update.text:
        print(update.text, end="", flush=True)

```

ਹਰ ਏਜੰਟ ਚਲਾਉਣ ਲਈ ਵਿਕਲਪ ਵੀ ਹੋ ਸਕਦੇ ਹਨ ਜਿਵੇਂ `max_tokens` ਜੋ ਏਜੰਟ ਦੁਆਰਾ ਵਰਤੇ ਜਾਂਦੇ ਹਨ, `tools` ਜੋ ਏਜੰਟ ਕਾਲ ਕਰ ਸਕਦਾ ਹੈ, ਅਤੇ ਇੱਥੋਂ ਤੱਕ ਕਿ `model` ਜੋ ਏਜੰਟ ਲਈ ਵਰਤਿਆ ਜਾਂਦਾ ਹੈ।

ਇਹ ਉਹਨਾਂ ਮਾਮਲਿਆਂ ਵਿੱਚ ਲਾਭਦਾਇਕ ਹੈ ਜਿੱਥੇ ਖਾਸ ਮਾਡਲ ਜਾਂ ਟੂਲਾਂ ਦੀ ਲੋੜ ਹੁੰਦੀ ਹੈ ਯੂਜ਼ਰ ਦਾ ਕੰਮ ਪੂਰਾ ਕਰਨ ਲਈ।

**ਟੂਲਜ਼**

ਟੂਲ ਐਜੰਟ ਬਣਾਉਂਦੇ ਸਮੇਂ ਪਰਿਭਾਸ਼ਿਤ ਕੀਤੇ ਜਾ ਸਕਦੇ ਹਨ:

```python
def get_attractions( location: Annotated[str, Field(description="The location to get the top tourist attractions for")], ) -> str: """Get the top tourist attractions for a given location.""" return f"The top attractions for {location} are." 


# ਜਦੋਂ ਸਿੱਧਾ ਇੱਕ ਚੈਟਏਜੰਟ ਬਣਾਇਆ ਜਾ ਰਿਹਾ ਹੈ

agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]

```

ਅਤੇ ਏਜੰਟ ਚਲਾਉਂਦੇ ਸਮੇਂ ਵੀ:

```python

result1 = await agent.run( "What's the best place to visit in Seattle?", tools=[get_attractions] # ਇਸ ਦੌੜ ਲਈ ਸਿਰਫ਼ ਉਪਲਬਧ ਟੂਲ )
```

**ਏਜੰਟ ਧਾਗੇ**

ਏਜੰਟ ਧਾਗੇ ਬਹੁ-ਟਰਨ ਗੱਲਬਾਤਾਂ ਨੂੰ ਸੰਭਾਲਣ ਲਈ ਵਰਤੇ ਜਾਂਦੇ ਹਨ। ਧਾਗੇ ਬਣਾਏ ਜਾ ਸਕਦੇ ਹਨ:

- `get_new_thread()` ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਜੋ ਕਿ ਧਾਗੇ ਨੂੰ ਸਮੇਂ ਦੇ ਨਾਲ ਸੰਭਾਲਣ ਦੀ ਸਹੂਲਤ ਦਿੰਦਾ ਹੈ
- ਏਜੰਟ ਨੂੰ ਚਲਾਉਂਦੇ ਸਮੇਂ ਆਟੋਮੈਟਿਕ ਧਾਗਾ ਬਣਾਉਣਾ ਜੋ ਕਿ ਸਿਰਫ ਇਸ ਚੱਲਾਣ ਲਈ ਹਾਲਤ ਰੱਖਦਾ ਹੈ।

ਧਾਗਾ ਬਣਾਉਣ ਲਈ ਕੋਡ ਇਸ ਤਰ੍ਹਾਂ ਹੁੰਦਾ ਹੈ:

```python
# ਇੱਕ ਨਵਾਂ ਧਾਗਾ ਬਣਾਓ।
thread = agent.get_new_thread() # ਧਾਗੇ ਨਾਲ ਏਜન્ટ ਚਲਾਓ।
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)

```

ਤੁਸੀਂ ਫਿਰ ਇਸ ਧਾਗੇ ਨੂੰ ਕਸੀਕ੍ਰਿਤ ਕਰਕੇ ਬਾਅਦ ਲਈ ਸਟੋਰ ਕਰ ਸਕਦੇ ਹੋ:

```python
# ਇੱਕ ਨਵ੍ਹਾ ਧਾਗਾ ਬਣਾਓ।
thread = agent.get_new_thread() 

# ਧਾਗੇ ਨਾਲ ਏਜੰਟ ਨੂੰ ਚਲਾਓ।

response = await agent.run("Hello, how are you?", thread=thread) 

# ਸਟੋਰੇਜ ਲਈ ਧਾਗੇ ਨੂੰ ਸੀਰੀਅਲਾਈਜ਼ ਕਰੋ।

serialized_thread = await thread.serialize() 

# ਸਟੋਰੇਜ ਤੋਂ ਲੋਡ ਕਰਨ ਤੋਂ ਬਾਅਦ ਧਾਗੇ ਦੀ ਸਥਿਤੀ ਨੂੰ ਡੀਸੀਰੀਅਲਾਈਜ਼ ਕਰੋ।

resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**ਏਜੰਟ ਮਿਡਲਵੇਅਰ**

ਏਜੰਟ ਯੂਜ਼ਰ ਦੇ ਕੰਮ ਪੂਰੇ ਕਰਨ ਲਈ ਟੂਲਾਂ ਅਤੇ LLMs ਨਾਲ ਗਤੀਵਿਧੀ ਕਰਦੇ ਹਨ। ਕੁਝ ਸਥਿਤੀਆਂ ਵਿੱਚ ਸਾਨੂੰ ਇਨ੍ਹਾਂ ਗਤੀਵਿਧੀਆਂ ਦੇ ਵਿਚਕਾਰ ਕੁਝ ਕਾਰਵਾਈ ਜਾਂ ਟ੍ਰੈਕਿੰਗ ਕਰਨੀ ਪੈਂਦੀ ਹੈ। ਏਜੰਟ ਮਿਡਲਵੇਅਰ ਸਾਨੂੰ ਇਹ ਕਿਰਿਆਵਾਂ ਕਰਨ ਦੀ ਆਗਿਆ ਦਿੰਦਾ ਹੈ:

*ਫੰਕਸ਼ਨ ਮਿਡਲਵੇਅਰ*

ਇਹ ਮਿਡਲਵੇਅਰ ਏਜੰਟ ਅਤੇ ਫੰਕਸ਼ਨ/ਟੂਲ ਜਿਸ ਨੂੰ ਇਹ ਕਾਲ ਕਰਨ ਜਾ ਰਿਹਾ ਹੈ, ਦੇ ਵਿਚਕਾਰ ਇੱਕ ਅਮਲ ਕਰਨ ਦੀ ਆਗਿਆ ਦਿੰਦਾ ਹੈ। ਉਦਾਹਰਨ ਵਜੋਂ, ਤੁਸੀਂ ਇਸਦਾ ਉਪਯੋਗ ਫੰਕਸ਼ਨ ਕਾਲ 'ਤੇ ਕੁਝ ਲੌਗਿੰਗ ਕਰਨ ਲਈ ਕਰ ਸਕਦੇ ਹੋ।

ਨਿਮਨ ਕੋਡ ਵਿੱਚ `next` ਇਹ ਨਿਰਧਾਰਤ ਕਰਦਾ ਹੈ ਕਿ ਅੱਗਲਾ ਮਿਡਲਵੇਅਰ ਕਾਲ ਹੋਵੇ ਜਾਂ ਅਸਲ ਫੰਕਸ਼ਨ।

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """Function middleware that logs function execution."""
    # ਪਹਿਲਾਂ ਪ੍ਰਕਿਰਿਆ: ਫੰਕਸ਼ਨ ਚਲਾਉਣ ਤੋਂ ਪਹਿਲਾਂ ਲੌਗ ਕਰੋ
    print(f"[Function] Calling {context.function.name}")

    # ਅਗਲੇ ਮਿਡਲਵੇਅਰ ਜਾਂ ਫੰਕਸ਼ਨ ਚਲਾਉਣ ਵੱਲ ਜਾਰੀ ਰੱਖੋ
    await next(context)

    # ਬਾਅਦ ਵਿੱਚ ਪ੍ਰਕਿਰਿਆ: ਫੰਕਸ਼ਨ ਚਲਾਉਣ ਤੋਂ ਬਾਅਦ ਲੌਗ ਕਰੋ
    print(f"[Function] {context.function.name} completed")
```

*ਚੈਟ ਮਿਡਲਵੇਅਰ*

ਇਹ ਮਿਡਲਵੇਅਰ ਏਜੰਟ ਅਤੇ LLM ਵਿਚਕਾਰ ਮੰਗਾਂ ਨੂੰ ਲੈ ਕੇ ਕਾਰਵਾਈ ਜਾਂ ਲੌਗਿੰਗ ਕਰਨ ਦੀ ਆਗਿਆ ਦਿੰਦਾ ਹੈ।

ਇਸ ਵਿੱਚ ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਹੁੰਦੀ ਹੈ ਜਿਵੇਂ ਕਿ AI ਸਰਵਿਸ ਨੂੰ ਭੇਜੇ ਗਏ `messages`।

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """Chat middleware that logs AI interactions."""
    # ਪ੍ਰੀ-ਪ੍ਰੋਸੈਸਿੰਗ: AI ਕਾਲ ਤੋਂ ਪਹਿਲਾਂ ਲੌਗ ਕਰੋ
    print(f"[Chat] Sending {len(context.messages)} messages to AI")

    # ਅਗਲੇ ਮਿਡਲਵੇਅਰ ਜਾਂ AI ਸਰਵਿਸ ਵੱਲ ਜਾਰੀ ਰੱਖੋ
    await next(context)

    # ਪੋਸਟ-ਪ੍ਰੋਸੈਸਿੰਗ: AI ਜਵਾਬ ਦੇ ਬਾਅਦ ਲੌਗ ਕਰੋ
    print("[Chat] AI response received")

```

**ਏਜੰਟ ਮੈਮੋਰੀ**

ਜਿਵੇਂ `Agentic Memory` ਪਾਠ ਵਿੱਚ ਕਵਰ ਕੀਤਾ ਗਿਆ ਹੈ, ਮੈਮੋਰੀ ਏਜੰਟ ਨੂੰ ਵੱਖ-ਵੱਖ ਸੰਦਰਭਾਂ ਵਿੱਚ ਕੰਮ ਕਰਨ ਯੋਗ ਬਣਾਉਂਦੀ ਹੈ। MAF ਵੱਖ-ਵੱਖ ਕਿਸਮ ਦੀਆਂ ਮੈਮੋਰੀਆਂ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ:

*ਇਨ-ਮੈਮੋਰੀ ਸਟੋਰੇਜ*

ਇਹ ਮੈਮੋਰੀ ਐਪਲੀਕੇਸ਼ਨ ਚਲਣ ਸਮੇਂ ਧਾਗਿਆਂ ਵਿੱਚ ਸਟੋਰ ਕੀਤੀ ਜਾਂਦੀ ਹੈ।

```python
# ਇੱਕ ਨਵੀਂ ਥ੍ਰੈਡ ਬਣਾਓ।
thread = agent.get_new_thread() # ਥ੍ਰੈਡ ਨਾਲ ਏਜੰਟ ਚਲਾਓ।
response = await agent.run("Hello, I am here to help you book travel. Where would you like to go?", thread=thread)
```

*ਪਰਸਿਸਟੈਂਟ ਮੈਸੇਜਜ਼*

ਇਹ ਮੈਮੋਰੀ ਵੱਖ-ਵੱਖ ਸੈਸ਼ਨਾਂ ਵਿੱਚ ਗੱਲਬਾਤ ਦੇ ਇਤਿਹਾਸ ਨੂੰ ਸਟੋਰ ਕਰਨ ਲਈ ਵਰਤੀ ਜਾਂਦੀ ਹੈ। ਇਹ `chat_message_store_factory` ਨਾਲ ਪਰਿਭਾਸ਼ਿਤ ਹੁੰਦੀ ਹੈ:

```python
from agent_framework import ChatMessageStore

# ਇੱਕ ਕਸਟਮ ਸੁਨੇਹਾ ਸਟੋਰ ਬਣਾਓ
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="You are a Travel assistant.",
    chat_message_store_factory=create_message_store
)

```

*ਡਾਇਨਾਮਿਕ ਮੈਮੋਰੀ*

ਇਹ ਮੈਮੋਰੀ ਏਜੰਟਸ ਚਲਾਉਣ ਤੋਂ ਪਹਿਲਾਂ ਸੰਦਰਭ ਵਿੱਚ ਜੋੜੀ ਜਾਂਦੀ ਹੈ। ਇਹ ਮੈਮੋਰੀਜ਼ ਬਾਹਰੀ ਸਰਵਿਸਿਜ਼ ਜਿਵੇਂ mem0 ਵਿੱਚ ਸਟੋਰ کیਤੀ ਜਾ سکتی ਹੈ:

```python
from agent_framework.mem0 import Mem0Provider

# ਅੱਗੇ ਵਧੀ ਹੋਈ ਮੈਮੋਰੀ ਖੂਬੀਆਂ ਲਈ Mem0 ਦੀ ਵਰਤੋਂ ਕਰਨਾ
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

**ਏਜੰਟ ਦੇਖਭਾਲਯੋਗਤਾ**

ਦ੍ਰਿਸ਼ਟੀ ਦੇ ਤੌਰ 'ਤੇ ਭਰੋਸੇਯੋਗ ਅਤੇ ਸੰਭਾਲਯੋਗ ਏਜੰਟਿਕ ਪ੍ਰਣਾਲੀਆਂ ਬਣਾਉਣ ਲਈ ਦੇਖਭਾਲਯੋਗਤਾ ਅਹੰਕਾਰਪੂਰਣ ਹੈ। MAF OpenTelemetry ਨਾਲ ਇੰਟੀਗਰੇਟ ਕਰਦਾ ਹੈ ਤਾਂ ਜੋ ਬਿਹਤਰ ਟਰੇਸਿੰਗ ਅਤੇ ਮੀਟਰ ਪ੍ਰਦਾਨ ਕੀਤੇ ਜਾ ਸਕਣ।

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()
with tracer.start_as_current_span("my_custom_span"):
    # ਕੁਝ ਕਰੋ
    pass
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### ਵਰਕਫਲੋਜ਼

MAF ਅਜੇਹੇ ਵਰਕਫਲੋਜ਼ ਦਿੰਦਾ ਹੈ ਜੋ ਇੱਕ ਕੰਮ ਪੂਰਾ ਕਰਨ ਲਈ ਪਹਿਲਾਂ ਤੋਂ ਪਰਿਭਾਸ਼ਿਤ ਕਦਮ ਹਨ ਅਤੇ ਇਸ ਵਿੱਚ AI ਏਜੰਟਸ ਨੂੰ ਕਦਮਾਂ ਦੀ ਇੱਕ ਘਟਕ ਵਜੋਂ ਸ਼ਾਮਿਲ ਕਰਦਾ ਹੈ।

ਵਰਕਫਲੋਜ਼ ਵੱਖ-ਵੱਖ ਭਾਗਾਂ ਤੋਂ ਬਣੇ ਹੁੰਦੇ ਹਨ ਜੋ ਬਿਹਤਰ ਕੰਟਰੋਲ ਫਲੋ ਦੀ ਆਗਿਆ ਦਿੰਦੇ ਹਨ। ਵਰਕਫਲੋਜ਼ **ਬਹੁ-ਏਜੰਟ ਆਰਕੇਸਟਰੈਸ਼ਨ** ਅਤੇ **ਚੈਕਪੌਇੰਟਿੰਗ** ਦਾ ਸਮਰਥਨ ਕਰਦਾ ਹੈ ਵਰਕਫਲੋ ਹਾਲਤਾਂ ਨੂੰ ਸੁਰੱਖਿਅਤ ਕਰਨ ਲਈ।

ਵਰਕਫਲੋਜ਼ ਦੇ ਮੁੱਖ ਭਾਗ ਹਨ:

**ਐਗਜ਼ਿਕਿਊਟਰ**

ਐਗਜ਼ਿਕਿਊਟਰ ਇਨਪੁੱਟ ਸੁਨੇਹੇ ਪ੍ਰਾਪਤ ਕਰਦੇ ਹਨ, ਆਪਣੇ ਨਿਰਧਾਰਿਤ ਕੰਮ ਕਰਦੇ ਹਨ, ਅਤੇ ਫਿਰ ਇੱਕ ਆઉਟਪੁੱਟ ਸੁਨੇਹਾ ਤਿਆਰ ਕਰਦੇ ਹਨ। ਇਹ ਵਰਕਫਲੋ ਨੂੰ ਵੱਡੇ ਕੰਮ ਦੀ ਪੂਰੀ ਹੁੰਦਾ ਵੱਲ ਅੱਗੇ ਵਧਾਉਂਦਾ ਹੈ। ਐਗਜ਼ਿਕਿਊਟਰ AI ਏਜੰਟ ਜਾਂ ਕਸਟਮ ਲਾਜਿਕ ਹੋ ਸਕਦੇ ਹਨ।

**ਐਜ**

ਐਜ ਵਰਕਫਲੋ ਵਿੱਚ ਸੁਨੇਹਿਆਂ ਦੇ ਪ੍ਰਵਾਹ ਨੂੰ ਪਰਿਭਾਸ਼ਿਤ ਕਰਨ ਲਈ ਵਰਤੇ ਜਾਂਦੇ ਹਨ। ਇਹ ਹੋ ਸਕਦੇ ਹਨ:

*ਸਿੱਧੇ ਐਜ* - ਐਗਜ਼ਿਕਿਊਟਰਾਂ ਵਿਚਕਾਰ ਸਧਾਰਨ ਇੱਕ-ਤੋਂ-ਇਕ ਕਨੈਕਸ਼ਨ:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*ਸ਼ਰਤਥ ਐਜ* - ਜਦੋਂ ਕੋਈ ਨਿਰਧਾਰਿਤ ਸ਼ਰਤ ਪੂਰੀ ਹੁੰਦੀ ਹੈ ਤਾਂ ਇਹ ਸક્રਿਆ ਹੋ ਜਾਂਦੇ ਹਨ। ਉਦਾਹਰਨ ਵਜੋਂ, ਜਦੋਂ ਹੋਟਲ ਕਮਰੇ ਉਪਲਬਧ ਨਹੀਂ ਹੁੰਦੇ ਤਾਂ ਐਗਜ਼ਿਕਿਊਟਰ ਹੋਰ ਵਿਕਲਪ ਸੁਝਾ ਸਕਦਾ ਹੈ।

*ਸਵਿੱਚ-ਕੇਸ ਐਜ* - ਨਿਰਧਾਰਿਤ ਸ਼ਰਤਾਂ ਦੇ ਆਧਾਰ 'ਤੇ ਸੁਨੇਹੇ ਵੱਖ-ਵੱਖ ਐਗਜ਼ਿਕਿਊਟਰਾਂ ਨੂੰ ਭੇਜਦੇ ਹਨ। ਉਦਾਹਰਨ ਵਜੋਂ, ਜੇ ਯਾਤਰੀ ਗਾਹਕ ਨੂੰ ਪ੍ਰਾਇਰਿਟੀ ਪਹੁੰਚ ਮਿਲਦੀ ਹੈ ਅਤੇ ਉਹਨਾਂ ਦੇ ਕੰਮ ਹੋਰ ਵਰਕਫਲੋ ਰਾਹੀਂ ਸੰਭਾਲੇ ਜਾਣਗੇ।

*ਫੈਨ-ਆਊਟ ਐਜ* - ਇੱਕ ਸੁਨੇਹਾ ਕਈ ਟਾਰਗਟਾਂ ਨੂੰ ਭੇਜਦਾ ਹੈ।

*ਫੈਨ-ਇਨ ਐਜ* - ਕਈ ਐਗਜ਼ਿਕਿਊਟਰਾਂ ਤੋਂ ਸੁਨੇਹੇ ਇਕੱਠੇ ਕਰਕੇ ਇੱਕ ਟਾਰਗਟ ਨੂੰ ਭੇਜਦਾ ਹੈ।

**ਈਵੈਂਟਸ**

ਵਰਕਫਲੋਜ਼ ਵਿੱਚ ਬਿਹਤਰ ਦੇਖਭਾਲਯੋਗਤਾ ਲਈ, MAF ਕਾਰਜਕਾਰੀ ਲਈ ਨਿਰਮਿਤ ਈਵੈਂਟ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ ਜਿਨ੍ਹਾਂ ਵਿੱਚ ਸ਼ਾਮਲ ਹਨ:

- `WorkflowStartedEvent`  - ਵਰਕਫਲੋਜ਼ ਕਾਰਜਕਾਰੀ ਸ਼ੁਰੂ ਹੁੰਦੀ ਹੈ
- `WorkflowOutputEvent` - ਵਰਕਫਲੋਜ਼ ਇੱਕ ਆਉਟਪੁੱਟ ਪੈਦਾ ਕਰਦਾ ਹੈ
- `WorkflowErrorEvent` - ਵਰਕਫਲੋਜ਼ ਵਿੱਚ ਗਲਤੀ ਆਉਂਦੀ ਹੈ
- `ExecutorInvokeEvent`  - ਐਗਜ਼ਿਕਿਊਟਰ ਕਾਰਜ ਪ੍ਰਾਰੰਭ ਕਰਦਾ ਹੈ
- `ExecutorCompleteEvent`  -  ਐਗਜ਼ਿਕਿਊਟਰ ਕਾਰਜ ਮੁਕੰਮਲ ਕਰਦਾ ਹੈ
- `RequestInfoEvent` - ਇੱਕ ਬੇਨਤੀ ਜਾਰੀ ਕੀਤੀ ਜਾਂਦੀ ਹੈ

## ਹੋਰ ਫਰੇਮਵਰਕ (Semantic Kernel ਅਤੇ AutoGen) ਤੋਂ ਮਾਈਗ੍ਰੇਸ਼ਨ

### MAF ਅਤੇ Semantic Kernel ਵਿਚਕਾਰ ਫਰਕ

**ਸਰਲਿਤ ਏਜੰਟ ਬਣਾਉਣਾ**

Semantic Kernel ਹਰ ਏਜੰਟ ਲਈ ਕੇਰਨਲ ਇੰਜਣ ਬਣਾਉਣ ਉੱਤੇ ਨਿਰਭਰ ਕਰਦਾ ਹੈ। MAF ਸਧਾਰਣ ਤਰੀਕੇ ਨਾਲ ਮੁੱਖ ਪ੍ਰੋਵਾਈਡਰਜ਼ ਲਈ ਐਕਸਟੈਂਸ਼ਨ ਦੀ ਵਰਤੋਂ ਕਰਦਾ ਹੈ।

```python
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent( instructions="You are good at reccomending trips to customers based on their preferences.", name="TripRecommender" )
```

**ਏਜੰਟ ਧਾਗਾ ਬਣਾਉਣਾ**

Semantic Kernel ਵਿੱਚ ਧਾਗੇ ਮੈਨੁਅਲੀ ਬਣਾਉਣੇ ਪੈਂਦੇ ਹਨ। MAF ਵਿੱਚ, ਏਜੰਟ ਨੂੰ ਸਿੱਧਾ ਧਾਗਾ ਦਿੱਤਾ ਜਾਂਦਾ ਹੈ।

```python
thread = agent.get_new_thread() # ਏਜੰਟ ਨੂੰ ਥ੍ਰੈੱਡ ਨਾਲ ਚਲਾਓ।
```

**ਟੂਲ ਰਜਿਸਟ੍ਰੇਸ਼ਨ**

Semantic Kernel ਵਿੱਚ ਟੂਲ ਕੇਰਨਲ ਨੂੰ ਰਜਿਸਟਰ ਕੀਤੇ ਜਾਂਦੇ ਹਨ ਅਤੇ ਫਿਰ ਕੇਰਨਲ ਨੂੰ ਏਜੰਟ ਲਈ ਦਿੱਤਾ ਜਾਂਦਾ ਹੈ। MAF ਵਿੱਚ, ਟੂਲ ਐਜੰਟ ਬਣਾਉਣ ਸਮੇਂ ਸਿੱਧਾ ਰਜਿਸਟਰ ਕੀਤੇ ਜਾਂਦੇ ਹਨ।

```python
agent = ChatAgent( chat_client=OpenAIChatClient(), instructions="You are a helpful assistant", tools=[get_attractions]
```

### MAF ਅਤੇ AutoGen ਵਿਚਕਾਰ ਫਰਕ

**ਟੀਮਾਂ ਬਨਾਮ ਵਰਕਫਲੋਜ਼**

`ਟੀਮਾਂ` AutoGen ਵਿੱਚਏਜੰਟਸ ਨਾਲ ਘਟਨਾ ਚਲਿਤ ਗਤੀਵਿਧੀ ਲਈ ਈਵੈਂਟ ਸਟਰਕਚਰ ਹਨ। MAF `ਵਰਕਫਲੋਜ਼` ਦੀ ਵਰਤੋਂ ਕਰਦਾ ਹੈ ਜੋ ਗ੍ਰਾਫ ਅਧਾਰਿਤ ਆਰਕੀਟੈਕਚਰ ਦੁਆਰਾ ਡਾਟਾ ਐਗਜ਼ਿਕਿਊਟਰਜ਼ ਤੱਕ ਰੂਟ ਕਰਦਾ ਹੈ।

**ਟੂਲ ਬਣਾਉਣਾ**

AutoGen `FunctionTool` ਦੀ ਵਰਤੋਂ ਕਰਦਾ ਹੈ ਤਾਂ ਜੋ ਫੰਕਸ਼ਨਜ਼ ਨੂੰ ਏਜੰਟਸ ਲਈ ਕਾਲ ਕਰਨ ਯੋਗ ਬਣਾਇਆ ਜਾ ਸਕੇ। MAF @ai_function ਦੀ ਵਰਤੋਂ ਕਰਦਾ ਹੈ ਜੋ ਇਸ ਤਰ੍ਹਾਂ ਹੀ ਕੰਮ ਕਰਦਾ ਹੈ ਪਰ ਹਰ ਫੰਕਸ਼ਨ ਲਈ ਆਟੋਮੈਟਿਕ схੀਮਾਂ ਦਾ ਅਨੁਮਾਨ ਲਗਾਉਂਦਾ ਹੈ।

**ਏਜੰਟ ਵਿਹਾਰ**

AutoGen ਵਿੱਚ ਏਜੰਟ ਮੂਲ ਰੂਪ ਵਿੱਚ ਸਿੰਗਲ-ਟਰਨ ਹਨ ਜਦ ਤੱਕ ਕਿ `max_tool_iterations` ਕਿਸੇ ਵੱਡੀ ਕਦਰ 'ਤੇ ਸੈੱਟ ਨਾ ਕੀਤਾ ਜਾਵੇ। MAF ਵਿੱਚ `ChatAgent` ਡਿਫੌਲਟ ਤੌਰ 'ਤੇ ਮਲਟੀ-ਟਰਨ ਹੈ, ਜਿਸਦਾ ਮਤਲਬ ਹੈ ਕਿ ਇਹ ਯੂਜ਼ਰ ਦੇ ਕੰਮ ਪੂਰਾ ਹੋਣ ਤੱਕ ਟੂਲ ਕਾਲ ਕਰਦਾ ਰਹੇਗਾ।

## ਕੋਡ ਨਮੂਨੇ

ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਲਈ ਕੋਡ ਨਮੂਨੇ ਇਸ ਰਿਪੋਜ਼ਟਰੀ ਵਿਚ `xx-python-agent-framework` ਅਤੇ `xx-dotnet-agent-framework` ਫਾਇਲਾਂ ਹੇਠਾਂ ਮਿਲਦੇ ਹਨ।

## ਮਾਈਕ੍ਰੋਸੌਫਟ ਏਜੰਟ ਫਰੇਮਵਰਕ ਬਾਰੇ ਹੋਰ ਸਵਾਲ?

ਹੋਰ ਸਿੱਖਣ ਵਾਲਿਆਂ ਨਾਲ ਮਿਲਣ, ਦਫਤਰ ਘੰਟੇ ਵਿੱਚ ਸ਼ਾਮਿਲ ਹੋਣ ਅਤੇ ਆਪਣੇ AI ਏਜੰਟ ਸਵਾਲਾਂ ਦੇ ਜਵਾਬ ਲੈਣ ਲਈ [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) ਵਿੱਚ ਸ਼ਾਮਿਲ ਹੋਵੋ।

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**ਅਸਵੀਕਾਰਿਆ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ AI ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਨਾਲ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀਅਤਾ ਲਈ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਵਿੱਚ ਰੱਖੋ ਕਿ ਆਟੋਮੈਟਿਕ ਅਨੁਵਾਦ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸਹੀਤੀਆਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼ ਜੋ ਇਸ ਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਹੈ, ਉਹ ਪ੍ਰਮਾਣਿਕ ਸਰੋਤ ਵਜੋਂ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਜਰੂਰੀ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਪੈਦਾਂ ਹੋਣ ਵਾਲੀਆਂ ਕਿਸੇ ਵੀ ਗਲਤਫਹਿਮੀਆਂ ਜਾਂ ਗਲਤ-ਵਿਆਖਿਆਵਾਂ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->