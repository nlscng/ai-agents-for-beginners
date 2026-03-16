[![Trustworthy AI Agents](../../../translated_images/pcm/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(Klik di pikcha wey dey for on top make you fit watch dis lesson video)_

# How to Build Trustworthy AI Agents

## Introduction

Dis lesson go cover:

- How to build and deploy safe and effective AI Agents
- Important security considerations wen you dey develop AI Agents.
- How to keep data and user privacy safe wen you dey develop AI Agents.

## Learning Goals

After you finish dis lesson, you go sabi how to:

- Identify and stop dangers wen you dey create AI Agents.
- Put security measures make sure say data and access dey well managed.
- Create AI Agents wey go keep data privacy and give better user experience.

## Safety

Make we first check how to build safe agentic applications. Safety mean say di AI agent dey work as e suppose. As people wey dey build agentic applications, we get ways and tools to make safety better:

### How to Build System Message Framework

If you don ever build AI application with Large Language Models (LLMs), you know how e important to design strong system prompt or system message. These prompts na di meta rules, instructions, and guidelines wey dey tell how LLM go interact with user and data.

For AI Agents, system prompt dey even more important because AI Agents go need specific instructions to fit complete the tasks wey we don design for dem.

To create system prompts wey fit grow well, we fit use system message framework to build one or more agents inside our application:

![Building a System Message Framework](../../../translated_images/pcm/system-message-framework.3a97368c92d11d68.webp)

#### Step 1: Create Meta System Message 

Di meta prompt go make LLM generate system prompts for di agents wey we go create. We go design am as template so we fit quickly create many agents if we need.

Here na example of meta system message wey we fit give the LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Step 2: Create basic prompt

Next step na to create basic prompt wey go describe the AI Agent. You suppose put the role of agent, the tasks wey di agent go do, and other responsibilities of the agent.

Here na example:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Step 3: Provide Basic System Message to LLM

Now we fit optimize dis system message by giving the meta system message as system message and our basic system message together.

Dis one go produce system message wey better to guide our AI agents:

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

#### Step 4: Iterate and Improve

Di koko of dis system message framework na say e fit make system messages from many agents easily and as you dey improve your system messages over time. E no common say you go get system message wey go work well di first time for your full use case. To fit do small changes and improvements by changing di basic system message and run am again through the system go allow you compare and check results.

## Understanding Threats

To build trustworthy AI agents, e important to sabi and stop di risks and threats wey fit affect your AI agent. Make we look some of di different threats to AI agents and how you fit plan and prepare better for dem.

![Understanding Threats](../../../translated_images/pcm/understanding-threats.89edeada8a97fc0f.webp)

### Task and Instruction

**Description:** Attackers fit try change di instructions or goals of AI agent through prompting or manipulating inputs.

**Mitigation**: Make sure say you dey run validation checks and input filters to find dangerous prompts before AI Agent process them. Because dis kain attacks dey need frequent interaction with Agent, to limit number of turns for di conversation na another way to stop these attacks.

### Access to Critical Systems

**Description**: If AI agent get access to systems and services wey store sensitive data, attackers fit spoil communication between agent and those systems. These attacks fit be direct or indirect to gain info about systems through di agent.

**Mitigation**: AI agents suppose get access to systems only if dem need am to stop these attacks. Communication between agent and system suppose secure. To do authentication and control access na another way to protect dis info.

### Resource and Service Overloading

**Description:** AI agents fit use different tools and services to complete tasks. Attackers fit use this power to attack these services by sending plenty requests through AI Agent, wey fit cause system failure or high cost.

**Mitigation:** Put policies wey go limit amount of requests AI agent fit send to service. Limit number of conversation turns and requests go help prevent these attacks.

### Knowledge Base Poisoning

**Description:** Dis kain attack no dey target AI agent directly but e dey target knowledge base and other services wey AI agent go use. E fit mean to spoil data or info wey AI agent go use for task, wey fit cause biased or wrong answers to person wey dey use am.

**Mitigation:** Dey check data wey AI agent dey use often. Make sure say only trusted people get access to change this data to stop this kind attack.

### Cascading Errors

**Description:** AI agents dey use various tools and services to finish task. If attackers cause error, e fit affect other systems wey AI agent connect to, making di attack spread and e go hard to solve.

**Mitigation**: One way to stop na to make AI Agent dey work for limited environment like Docker container to avoid direct system attack. Also, to build fallback options and retry logic when certain system give error na way to avoid bigger system failure.

## Human-in-the-Loop

Another good way to build trustworthy AI Agent system na to use Human-in-the-loop. Dis one create flow where users fit give feedback to Agents while dem dey run. Users dey act like agents in multi-agent system by giving ok or stopping di running process.

![Human in The Loop](../../../translated_images/pcm/human-in-the-loop.5f0068a678f62f4f.webp)

Here na code snippet wey use AutoGen to show how dis idea dey work:

```python

# Make di agents dem.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Use input() to collect user talk from di console.

# Make di stop condition wey go end di conversation when di user talk "APPROVE".
termination = TextMentionTermination("APPROVE")

# Make di team.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Run di conversation and shine am for di console.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Use asyncio.run(...) when you dey run am for script.
await Console(stream)

```

## Conclusion

To build trustworthy AI agents, you need careful design, strong security measures, and continuous improve. By putting structured meta prompting systems, understanding threats, and applying better measures, developers fit create AI agents wey safe and effective. Plus, using human-in-the-loop approach go make sure AI agents dey align with user needs and reduce risks. As AI dey grow, to dey proactive about security, privacy, and ethics go key to build trust and reliability for AI-driven systems.

### You Get More Questions About Building Trustworthy AI Agents?

Join [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) make you fit meet other learners, attend office hours and get answers to your AI Agents questions.

## Additional Resources

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Responsible AI overview</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Evaluation of generative AI models and AI applications</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Safety system messages</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Risk Assessment Template</a>

## Previous Lesson

[Agentic RAG](../05-agentic-rag/README.md)

## Next Lesson

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Disclaimer**:
Dis document don translate wit AI translation service wey dem dey call [Co-op Translator](https://github.com/Azure/co-op-translator). Even though we dey try make e correct, abeg make you sabi say automated translation fit get some errors or wahala. Di original document wey e dey for im own language na di correct one wey you suppose trust. If na important information, e better make professional human translator do am. We no go responsible for any misunderstanding or wrong meaning wey fit show from dis translation.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->