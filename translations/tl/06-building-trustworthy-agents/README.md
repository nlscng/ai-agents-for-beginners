[![Trustworthy AI Agents](../../../translated_images/tl/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(I-click ang larawan sa itaas upang panoorin ang video ng araling ito)_

# Pagbuo ng Mapagkakatiwalaang AI Agents

## Panimula

Tatalakayin sa araling ito:

- Paano bumuo at mag-deploy ng ligtas at epektibong AI Agents
- Mahahalagang konsiderasyon sa seguridad kapag nagde-develop ng AI Agents
- Paano mapanatili ang privacy ng data at gumagamit kapag nagde-develop ng AI Agents

## Mga Layuning Matutunan

Pagkatapos makumpleto ang araling ito, malalaman mo kung paano:

- Tukuyin at bawasan ang mga panganib kapag lumilikha ng AI Agents
- Magpatupad ng mga hakbang sa seguridad upang matiyak na maayos ang pamamahala ng data at access
- Gumawa ng AI Agents na nagpoprotekta sa privacy ng data at nagbibigay ng magandang karanasan sa gumagamit

## Kaligtasan

Unang titingnan natin ang pagbuo ng ligtas na mga aplikasyon ng agentic. Ang kaligtasan ay nangangahulugan na ang AI agent ay gumagana ayon sa disenyo. Bilang mga tagabuo ng mga agentic na aplikasyon, mayroon tayong mga pamamaraan at kagamitan upang mapalaki ang kaligtasan:

### Pagbuo ng System Message Framework

Kung nakabuo ka na ng AI application gamit ang Large Language Models (LLMs), alam mo ang kahalagahan ng pagdisenyo ng matibay na system prompt o system message. Ang mga prompt na ito ang nagtatakda ng mga meta na patakaran, mga tagubilin, at gabay kung paano makikipag-ugnayan ang LLM sa gumagamit at data.

Para sa AI Agents, mas mahalaga ang system prompt dahil kailangan nilang magkaroon ng napaka-especific na mga tagubilin para magawa ang mga gawain na idinisenyo para sa kanila.

Upang gumawa ng scalable na mga system prompt, maaari tayong gumamit ng system message framework para bumuo ng isa o higit pang mga agent sa ating aplikasyon:

![Building a System Message Framework](../../../translated_images/tl/system-message-framework.3a97368c92d11d68.webp)

#### Hakbang 1: Gumawa ng Meta System Message

Ang meta prompt ay gagamitin ng LLM upang lumikha ng mga system prompt para sa mga agent na gagawin natin. Dinisenyo natin ito bilang isang template upang maaari tayong gumawa ng maraming agent nang episyente kung kinakailangan.

Narito ang isang halimbawa ng meta system message na ibibigay natin sa LLM:

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### Hakbang 2: Gumawa ng basic prompt

Ang susunod na hakbang ay gumawa ng basic prompt upang ilarawan ang AI Agent. Dapat mong isama ang papel ng agent, ang mga gagawin nitong mga gawain, at anumang iba pang responsibilidad ng agent.

Narito ang isang halimbawa:

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### Hakbang 3: Ibigay ang Basic System Message sa LLM

Ngayon maaari nating i-optimize ang sistemang ito ng mensahe sa pamamagitan ng pagbibigay ng meta system message bilang system message kasama ng ating basic system message.

Gagawa ito ng isang system message na mas mahusay na dinisenyo para gabayan ang ating AI agents:

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

#### Hakbang 4: Paulit-ulit at Pagbutihin

Ang halaga ng system message framework na ito ay upang mapadali ang paggawa ng system messages mula sa maraming agent at pati na rin ang pagpapabuti ng iyong mga system message sa paglipas ng panahon. Bihira ang magkaroon ka ng system message na eksaktong gumagana sa unang pagkakataon para sa iyong buong kaso ng paggamit. Ang kakayahang gumawa ng maliliit na pagbabago at pagpapabuti sa pamamagitan ng pagbabago ng basic system message at pagpapatakbo nito sa system ay magpapahintulot sa iyo na ihambing at suriin ang mga resulta.

## Pag-unawa sa mga Banta

Upang makabuo ng mapagkakatiwalaang AI agents, mahalagang maunawaan at mabawasan ang mga panganib at banta sa iyong AI agent. Tingnan natin ang ilan lamang sa iba't ibang banta sa AI agents at kung paano ka makakapaghanda at makakapagplano para dito.

![Understanding Threats](../../../translated_images/tl/understanding-threats.89edeada8a97fc0f.webp)

### Gawain at Tagubilin

**Paglalarawan:** Sinusubukan ng mga umaatake na baguhin ang mga tagubilin o layunin ng AI agent sa pamamagitan ng prompting o pagmamanipula ng mga input.

**Bawasan**: Isagawa ang mga pagsusuri sa bisa at mga input filter upang tuklasin ang mga posibleng mapanganib na prompt bago ito iproseso ng AI Agent. Dahil ang mga atakeng ito ay karaniwang nangangailangan ng madalas na pakikisalamuha sa Agent, ang paglilimita sa bilang ng mga pag-ikot sa isang pag-uusap ay isa pang paraan upang maiwasan ang ganitong uri ng mga atake.

### Access sa Mga Kritikal na Sistema

**Paglalarawan**: Kung ang AI agent ay may access sa mga sistema at serbisyo na nag-iimbak ng sensitibong data, maaaring mapagsamantalahan ng mga umaatake ang komunikasyon sa pagitan ng agent at mga serbisyong ito. Maaari itong maging direktang mga atake o hindi direktang pagtatangka upang makakuha ng impormasyon tungkol sa mga sistemang ito sa pamamagitan ng agent.

**Bawasan**: Dapat mayroon lamang access ang AI agents sa mga sistema kung kinakailangan upang maiwasan ang ganitong uri ng mga atake. Dapat ding secure ang komunikasyon sa pagitan ng agent at sistema. Ang pagpapatupad ng authentication at access control ay isa pang paraan upang maprotektahan ang impormasyong ito.

### Sobra-sobrang Paggamit ng Mga Mapagkukunan at Serbisyo

**Paglalarawan:** Maaaring gumamit ang mga AI agents ng iba't ibang kasangkapan at serbisyo upang matapos ang mga gawain. Maaaring gamitin ito ng mga umaatake upang atakihin ang mga serbisyong ito sa pamamagitan ng pagpapadala ng mataas na dami ng mga kahilingan sa AI Agent, na maaaring magdulot ng pagkabigo ng sistema o mataas na gastos.

**Bawasan:** Magpatupad ng mga polisiya upang limitahan ang bilang ng mga kahilingan na maaari gawin ng isang AI agent sa isang serbisyo. Ang paglilimita sa bilang ng mga pag-ikot sa pag-uusap at mga kahilingan sa iyong AI agent ay isa pang paraan upang maiwasan ang ganitong uri ng mga atake.

### Pagkalason ng Knowledge Base

**Paglalarawan:** Ang ganitong uri ng pag-atake ay hindi direktang tumatarget sa AI agent kundi sa knowledge base at iba pang serbisyo na gagamitin ng AI agent. Maaaring kabilang dito ang pagsira ng data o impormasyon na gagamitin ng AI agent upang tapusin ang isang gawain, na maaaring magresulta sa bias o hindi inaasahang mga tugon sa gumagamit.

**Bawasan:** Isagawa ang regular na beripikasyon ng data na gagamitin ng AI agent sa mga workflow nito. Tiyakin na ang access sa data na ito ay secure at tanging mga pinagkakatiwalaang indibidwal lamang ang makakabago upang iwasan ang ganitong uri ng pag-atake.

### Sunod-sunod na Error

**Paglalarawan:** Nakakonekta ang AI agents sa iba't ibang kasangkapan at serbisyo upang matapos ang mga gawain. Ang mga error na sanhi ng mga umaatake ay maaaring magdulot ng kabiguan sa iba pang mga sistema na konektado sa AI agent, na nagpapalawak ng epekto ng atake at nagpapahirap sa pag-troubleshoot.

**Bawasan**: Isang paraan upang maiwasan ito ay ang pagpapaandar sa AI Agent sa isang limitadong kapaligiran, tulad ng paggawa ng mga gawain sa Docker container, upang maiwasan ang direktang pag-atake sa sistema. Ang paglikha ng mga fallback mechanism at retry logic kapag tumugon ang ilang sistema ng error ay isa pang paraan upang maiwasan ang mas malaking kabiguan ng sistema.

## Human-in-the-Loop

Isa pang epektibong paraan upang bumuo ng mapagkakatiwalaang mga sistema ng AI Agent ay ang paggamit ng Human-in-the-loop. Lumilikha ito ng daloy kung saan maaaring magbigay ng feedback ang mga gumagamit sa mga Agent habang tumatakbo ang proseso. Ang mga gumagamit ay epektibong kumikilos bilang mga agent sa isang multi-agent system at nagbibigay ng pag-apruba o pagtigil sa proseso.

![Human in The Loop](../../../translated_images/tl/human-in-the-loop.5f0068a678f62f4f.webp)

Narito ang isang snippet ng code gamit ang AutoGen upang ipakita kung paano ipinatutupad ang konseptong ito:

```python

# Gumawa ng mga ahente.
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # Gumamit ng input() para kumuha ng input ng user mula sa console.

# Gumawa ng kondisyon ng pagtigil na magtatapos sa pag-uusap kapag sinabi ng user na "APPROVE".
termination = TextMentionTermination("APPROVE")

# Gumawa ng koponan.
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# Patakbuhin ang pag-uusap at i-stream sa console.
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# Gumamit ng asyncio.run(...) kapag nagpapatakbo sa isang script.
await Console(stream)

```

## Konklusyon

Ang pagbuo ng mapagkakatiwalaang AI agents ay nangangailangan ng maingat na disenyo, matibay na mga hakbang sa seguridad, at tuloy-tuloy na pag-uulit. Sa pamamagitan ng pagsasagawa ng mga estrukturadong sistema ng meta prompting, pag-unawa sa mga potensyal na banta, at pagpapatupad ng mga estratehiya sa pag-iwas, maaaring gumawa ang mga developer ng AI agents na parehong ligtas at epektibo. Bukod dito, ang pagsasama ng human-in-the-loop na pamamaraan ay nagsisiguro na ang AI agents ay nananatiling nakaayon sa pangangailangan ng gumagamit habang pinapaliit ang mga panganib. Habang patuloy na umuunlad ang AI, ang pagpapanatili ng proaktibong pananaw sa seguridad, privacy, at mga etikal na konsiderasyon ay magiging susi upang mapalago ang tiwala at pagiging maaasahan sa mga AI-driven na sistema.

### May Karagdagang Mga Tanong tungkol sa Pagbuo ng Mapagkakatiwalaang AI Agents?

Sumali sa [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) upang makipagkita sa ibang mga nag-aaral, dumalo sa office hours at sagutin ang iyong mga tanong tungkol sa AI Agents.

## Karagdagang Mga Mapagkukunan

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">Pangkalahatang-ideya ng Responsible AI</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">Pagsusuri ng mga Generative AI Models at AI Applications</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">Mga System Message para sa Kaligtasan</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">Template para sa Risk Assessment</a>

## Nakaraang Aralin

[Agentic RAG](../05-agentic-rag/README.md)

## Susunod na Aralin

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Pagtatanging Paalala**:
Ang dokumentong ito ay isinalin gamit ang serbisyong AI na pagsasalin na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagama't nagsusumikap kaming maging tumpak, pakatandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga pagkakamali o di-katumpakan. Ang orihinal na dokumento sa wikang likas nito ang dapat ituring na pangunahing sanggunian. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasalin ng tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na nagmula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->