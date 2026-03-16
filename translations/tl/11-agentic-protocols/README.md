# Paggamit ng Agentic Protocols (MCP, A2A at NLWeb)

[![Mga Agentic Protocols](../../../translated_images/tl/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(I-click ang larawan sa itaas upang panoorin ang video ng araling ito)_

Habang lumalago ang paggamit ng AI agents, lumalago rin ang pangangailangan para sa mga protocol na nagsisiguro ng standardisasyon, seguridad, at sumusuporta sa bukas na inobasyon. Sa araling ito, tatalakayin natin ang 3 protocol na tumutugon sa pangangailangang ito - Model Context Protocol (MCP), Agent to Agent (A2A) at Natural Language Web (NLWeb).

## Panimula

Sa araling ito, tatalakayin natin:

• Paano pinapayagan ng **MCP** ang mga AI Agents na ma-access ang mga external na tool at data upang makumpleto ang mga gawain ng user.

• Paano pinapahintulutan ng **A2A** ang komunikasyon at kolaborasyon sa pagitan ng iba't ibang AI agents.

• Paano dinadala ng **NLWeb** ang natural na wika bilang interface sa anumang website na nagpapahintulot sa mga AI Agents na tuklasin at makipag-ugnayan sa nilalaman.

## Mga Layunin sa Pagkatuto

• **Tukuyin** ang pangunahing layunin at mga benepisyo ng MCP, A2A, at NLWeb sa konteksto ng mga AI agents.

• **Ipaliwanag** kung paano pinapadali ng bawat protocol ang komunikasyon at interaksyon sa pagitan ng LLMs, mga tool, at ibang agents.

• **Kilalanin** ang magkakaibang papel na ginagampanan ng bawat protocol sa pagbuo ng mga kumplikadong agentic na sistema.

## Protokol ng Model Context

Ang **Model Context Protocol (MCP)** ay isang bukas na standard na nagbibigay ng isang standardisadong paraan para ang mga aplikasyon ay makapagbigay ng konteksto at mga tool sa mga LLM. Pinapayagan nito ang isang "unibersal na adaptor" sa iba't ibang pinagmumulan ng data at mga tool na maaaring ikonekta ng mga AI Agents sa isang pare-parehong paraan.

Tingnan natin ang mga komponent ng MCP, ang mga benepisyo kumpara sa direktang paggamit ng API, at isang halimbawa kung paano maaaring gamitin ng mga AI agent ang isang MCP server.

### Pangunahing Komponent ng MCP

Ang MCP ay gumagana sa isang **client-server architecture** at ang mga pangunahing komponent ay:

• **Hosts** ay mga aplikasyon ng LLM (halimbawa isang code editor tulad ng VSCode) na nagsisimula ng mga koneksyon sa isang MCP Server.

• **Clients** ay mga komponent sa loob ng host application na nagpapanatili ng one-to-one na koneksyon sa mga server.

• **Servers** ay mga magagaan na programa na nag-eekspos ng partikular na mga kakayahan.

Kasama sa protocol ang tatlong pangunahing primitive na siyang mga kakayahan ng isang MCP Server:

• **Tools**: Ito ay mga hiwalay na aksyon o function na maaaring tawagin ng isang AI agent upang magsagawa ng isang gawain. Halimbawa, ang isang weather service ay maaaring mag-eekspos ng isang "get weather" tool, o ang isang e-commerce server ay maaaring mag-eekspos ng isang "purchase product" tool. I-aanunsyo ng mga MCP server ang pangalan ng bawat tool, deskripsyon, at input/output schema sa kanilang listing ng mga kakayahan.

• **Resources**: Ito ay mga read-only na item ng data o dokumento na maaaring ibigay ng isang MCP server, at maaaring kunin ng mga client kapag kailangan. Mga halimbawa ay nilalaman ng file, talaan ng database, o mga log file. Ang Resources ay maaaring teksto (tulad ng code o JSON) o binary (tulad ng mga imahe o PDF).

• **Prompts**: Ito ay mga paunang définadong template na nagbibigay ng mga mungkahing prompt, na nagpapahintulot ng mas kumplikadong workflow.

### Mga Benepisyo ng MCP

Nag-aalok ang MCP ng mga makabuluhang bentahe para sa mga AI Agents:

• **Dynamic Tool Discovery**: Ang mga agent ay maaaring dynamic na makatanggap ng listahan ng mga magagamit na tool mula sa isang server kasama ang mga deskripsyon ng kanilang ginagawa. Ito ay kaiba sa tradisyonal na mga API, na madalas nangangailangan ng static na pag-cocode para sa mga integrasyon, na nangangahulugang ang anumang pagbabago sa API ay nangangailangan ng pag-update ng code. Nag-aalok ang MCP ng isang "integrate once" na paraan, na nagdudulot ng higit na kakayahang umangkop.

• **Interoperability Across LLMs**: Gumagana ang MCP sa iba't ibang LLMs, nagbibigay ng kakayahang magpalit ng core models para sa mas mahusay na performance.

• **Standardized Security**: Kasama sa MCP ang isang standard na paraan ng authentication, na nagpapabuti ng scalability kapag nagdadagdag ng access sa karagdagang MCP servers. Mas simple ito kaysa sa pamamahala ng iba't ibang keys at uri ng authentication para sa iba't ibang tradisyonal na API.

### Halimbawa ng MCP

![Diagram ng MCP](../../../translated_images/tl/mcp-diagram.e4ca1cbd551444a1.webp)

Isipin na nais ng isang user na mag-book ng flight gamit ang isang AI assistant na pinapagana ng MCP.

1. **Connection**: Ang AI assistant (ang MCP client) ay kumokonekta sa isang MCP server na ibinigay ng isang airline.

2. **Tool Discovery**: Tinanong ng client ang MCP server ng airline, "Anong mga tool ang mayroon kayo?" Sumagot ang server gamit ang mga tool tulad ng "maghanap ng mga flight" at "i-book ang flight".

3. **Tool Invocation**: Pagkatapos, sinabihan mo ang AI assistant, "Pakihanap ng flight mula Portland papuntang Honolulu." Kinilala ng AI assistant, gamit ang kanyang LLM, na kailangan nitong tawagin ang tool na "maghanap ng mga flight" at ipinapasa ang kaukulang mga parameter (origin, destination) sa MCP server.

4. **Execution and Response**: Ang MCP server, na kumikilos bilang wrapper, ay gumagawa ng aktwal na tawag sa internal booking API ng airline. Tinatanggap nito ang impormasyon ng flight (hal., JSON data) at isinusumite ito pabalik sa AI assistant.

5. **Further Interaction**: Ipinapakita ng AI assistant ang mga pagpipilian ng flight. Kapag pumili ka ng flight, maaaring i-invoke ng assistant ang tool na "i-book ang flight" sa parehong MCP server, na kumukumpleto sa booking.

## Protokol ng Agent-to-Agent (A2A)

Habang ang MCP ay nakatuon sa pagkonekta ng LLMs sa mga tool, ang **Agent-to-Agent (A2A) protocol** ay umuusbong pa sa pamamagitan ng pagpapahintulot ng komunikasyon at kolaborasyon sa pagitan ng iba't ibang AI agents. Kinokonekta ng A2A ang mga AI agents mula sa iba't ibang organisasyon, kapaligiran at tech stacks upang makumpleto ang isang pinag-isang gawain.

Susuriin natin ang mga komponent at benepisyo ng A2A, kasama ang isang halimbawa kung paano ito maaaring ilapat sa ating travel application.

### Pangunahing Komponent ng A2A

Nakatuon ang A2A sa pagpapahintulot ng komunikasyon sa pagitan ng mga agent at pagpapagawa sa kanila ng pagtutulungan upang makumpleto ang isang subtask para sa user. Ang bawat komponent ng protocol ay nag-aambag dito:

#### Agent Card

Katulad ng paraan ng pagbabahagi ng isang MCP server ng listahan ng mga tool, ang Agent Card ay may:
- Ang Pangalan ng Ahente .
- Isang **deskripsyon ng pangkalahatang mga gawain** na ginagawa nito.
- Isang **listahan ng mga partikular na kasanayan** na may mga deskripsyon upang tulungan ang ibang mga ahente (o kahit mga taong gumagamit) na maunawaan kung kailan at bakit nila nais tawagin ang ahente na iyon.
- Ang **kasalukuyang Endpoint URL** ng ahente
- Ang **bersyon** at **mga kakayahan** ng ahente tulad ng streaming responses at push notifications.

#### Agent Executor

Ang Agent Executor ay responsable para sa **pagpapasa ng konteksto ng usapan ng user sa remote na ahente**, kailangan ito ng remote na ahente upang maunawaan ang gawain na kailangang matapos. Sa isang A2A server, gumagamit ang isang ahente ng sarili nitong Large Language Model (LLM) upang i-parse ang papasok na mga kahilingan at isagawa ang mga gawain gamit ang sariling internal na mga tool.

#### Artifact

Kapag natapos na ng remote na ahente ang hinihinging gawain, ang kanyang produkto ng trabaho ay nililikha bilang isang artifact. Ang isang artifact ay **naglalaman ng resulta ng trabaho ng ahente**, isang **deskripsyon ng kung ano ang natapos**, at ang **text context** na ipinadala sa pamamagitan ng protocol. Pagkatapos maipadala ang artifact, isinasara ang koneksyon sa remote na ahente hanggang ito ay muling kailanganin.

#### Event Queue

Ang komponent na ito ay ginagamit para sa **paghawak ng mga update at pagpapasa ng mga mensahe**. Partikular itong mahalaga sa production para sa mga agentic na sistema upang maiwasang masara ang koneksyon sa pagitan ng mga ahente bago matapos ang isang gawain, lalo na kapag ang oras ng pagkumpleto ng gawain ay maaaring tumagal.

### Mga Benepisyo ng A2A

• **Pinalawak na Kolaborasyon**: Pinapayagan nito ang mga ahente mula sa iba't ibang vendor at platform na makipag-ugnayan, magbahagi ng konteksto, at magtulungan, na nagpapadali ng seamless automation sa pagitan ng karaniwang magkakahiwalay na mga sistema.

• **Kakayahang Pumili ng Modelo**: Ang bawat A2A agent ay maaaring magpasya kung aling LLM ang gagamitin nito para paglingkuran ang mga kahilingan, na nagpapahintulot ng optimized o fine-tuned na mga modelo para sa bawat ahente, hindi katulad ng isang solong LLM na koneksyon sa ilang MCP na senaryo.

• **Built-in na Authentication**: Ang authentication ay naka-integrate direkta sa A2A protocol, na nagbibigay ng matibay na security framework para sa interaksyon ng mga ahente.

### Halimbawa ng A2A

![Diagram ng A2A](../../../translated_images/tl/A2A-Diagram.8666928d648acc26.webp)

Palawakin natin ang aming scenario ng travel booking, ngunit sa pagkakataong ito gamit ang A2A.

1. **Request ng User sa Multi-Agent**: Nakikipag-ugnayan ang isang user sa isang "Ahente ng Paglalakbay" na A2A client/agent, marahil sa pagsasabi, "Pakibook ang buong biyahe papuntang Honolulu para sa susunod na linggo, kasama ang mga flights, hotel, at rental car".

2. **Orkestrasyon ng Ahente ng Paglalakbay**: Tinatanggap ng Ahente ng Paglalakbay ang kumplikadong kahilingang ito. Ginagamit nito ang kanyang LLM upang magmuni-muni tungkol sa gawain at matukoy na kailangan nitong makipag-ugnayan sa iba pang mga specialized na ahente.

3. **Inter-Agent Communication**: Pagkatapos, ginagamit ng Ahente ng Paglalakbay ang A2A protocol upang kumonekta sa downstream na mga ahente, tulad ng isang "Ahente ng Airline," isang "Ahente ng Hotel," at isang "Ahente ng Pagpapaupa ng Sasakyan" na nilikha ng iba't ibang kumpanya.

4. **Delegated Task Execution**: Ipinapadala ng Ahente ng Paglalakbay ang mga partikular na gawain sa mga specialized na ahenteng ito (hal., "Maghanap ng mga flight papuntang Honolulu," "Mag-book ng hotel," "Magpaupa ng sasakyan"). Bawat isa sa mga specialized na ahenteng ito, na nagpapatakbo ng kanilang sariling LLMs at gumagamit ng kanilang sariling mga tool (na maaari ring mga MCP servers), ay isinasagawa ang partikular nitong bahagi ng booking.

5. **Pinagsama-samang Tugon**: Kapag natapos na ng lahat ng downstream na ahente ang kanilang mga gawain, kinokompila ng Ahente ng Paglalakbay ang mga resulta (mga detalye ng flight, kumpirmasyon ng hotel, booking ng pagpapaupa ng sasakyan) at nagpapadala ng isang komprehensibo, chat-style na tugon pabalik sa user.

## Natural Language Web (NLWeb)

Matagal nang ang mga website ang pangunahing paraan para ma-access ng mga user ang impormasyon at data sa internet.

Tingnan natin ang iba't ibang komponent ng NLWeb, ang mga benepisyo ng NLWeb at isang halimbawa kung paano gumagana ang aming NLWeb sa pamamagitan ng pagtingin sa aming travel application.

### Mga Komponent ng NLWeb

- **NLWeb Application (Core Service Code)**: Ang sistema na nagpoproseso ng mga tanong sa natural na wika. Kinokonekta nito ang iba't ibang bahagi ng plataporma upang lumikha ng mga tugon. Maaari mo itong ituring bilang ang **engineng nagpapatakbo ng mga tampok ng natural na wika** ng isang website.

- **NLWeb Protocol**: Ito ay isang **pundamental na hanay ng mga patakaran para sa natural na wika na interaksyon** sa isang website. Nagbabalik ito ng mga tugon sa JSON format (madalas na gumagamit ng Schema.org). Layunin nito na lumikha ng isang simpleng pundasyon para sa "AI Web," katulad ng ginawa ng HTML para gawing posible ang pagbabahagi ng mga dokumento online.

- **MCP Server (Model Context Protocol Endpoint)**: Bawat NLWeb setup ay gumagana rin bilang isang **MCP server**. Ibig sabihin nito ay maaari itong **magbahagi ng mga tool (tulad ng isang “ask” method) at data** sa iba pang mga AI system. Sa praktika, ginagawa nitong magagamit ng mga AI agents ang nilalaman at kakayahan ng website, na nagpapahintulot sa site na maging bahagi ng mas malawak na "agent ecosystem."

- **Embedding Models**: Ang mga modelong ito ay ginagamit upang **i-convert ang nilalaman ng website sa mga numerical representation na tinatawag na vectors** (embeddings). Kinakatawan ng mga vector na ito ang kahulugan sa paraan na maaaring ikumpara at hanapin ng mga computer. Ito ay iniimbak sa isang espesyal na database, at maaaring pumili ang mga user kung aling embedding model ang nais nilang gamitin.

- **Vector Database (Retrieval Mechanism)**: Ang database na ito ay **nagtatago ng mga embeddings ng nilalaman ng website**. Kapag may nagtanong, sinusuri ng NLWeb ang vector database upang mabilis na hanapin ang pinaka-nauugnay na impormasyon. Nagbibigay ito ng mabilis na listahan ng mga posibleng sagot, niraranggo ayon sa pagkakatulad. Gumagana ang NLWeb sa iba't ibang vector storage systems tulad ng Qdrant, Snowflake, Milvus, Azure AI Search, at Elasticsearch.

### Halimbawa ng NLWeb

![NLWeb](../../../translated_images/tl/nlweb-diagram.c1e2390b310e5fe4.webp)

Isaalang-alang muli ang aming travel booking website, ngunit sa pagkakataong ito, pinapagana ng NLWeb.

1. **Data Ingestion**: Ang mga umiiral na product catalog ng travel website (hal., mga listahan ng flight, deskripsyon ng hotel, mga tour package) ay ini-format gamit ang Schema.org o niloload sa pamamagitan ng RSS feeds. Kinukuha ng mga tool ng NLWeb ang istrukturadong data na ito, lumilikha ng mga embeddings, at iniimbak ang mga ito sa lokal o remote na vector database.

2. **Natural Language Query (Human)**: Bumibisita ang isang user sa website at, sa halip na mag-navigate ng mga menu, nagta-type sa isang chat interface: "Find me a family-friendly hotel in Honolulu with a pool for next week".

3. **NLWeb Processing**: Tinatanggap ng NLWeb application ang query na ito. Ipinapadala nito ang query sa isang LLM para sa pag-unawa at kasabay nito hinahanap ang vector database para sa mga nauugnay na listahan ng hotel.

4. **Accurate Results**: Tinutulungan ng LLM na i-interpret ang mga resulta ng paghahanap mula sa database, tukuyin ang pinakamahusay na tugma base sa mga kriteriya na "family-friendly," "pool," at "Honolulu," at pagkatapos ay ifo-format ang isang tugon sa natural na wika. Mahalaga, tumutukoy ang tugon sa aktwal na mga hotel mula sa katalogo ng website, na iniiwasan ang anumang imbentong impormasyon.

5. **AI Agent Interaction**: Dahil nagsisilbi ang NLWeb bilang isang MCP server, maaaring kumonekta rin ang isang external na AI travel agent sa NLWeb instance ng website na ito. Maaari pagkatapos na gamitin ng AI agent ang `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")` MCP method upang direktang i-query ang website. Poproseso nito ang tanong, gagamitin ang database nito ng impormasyon ng mga restaurant (kung na-load), at magbabalik ng isang istrukturadong JSON na tugon.

### May Karagdagang Mga Tanong tungkol sa MCP/A2A/NLWeb?

Sumali sa [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) para makipagkita sa ibang mga nag-aaral, dumalo sa office hours at masagot ang iyong mga tanong tungkol sa AI Agents.

## Mga Sanggunian

- [MCP para sa mga Nagsisimula](https://aka.ms/mcp-for-beginners)  
- [Dokumentasyon ng MCP](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [Repo ng NLWeb](https://github.com/nlweb-ai/NLWeb)
- [Mga Gabay ng Semantic Kernel](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Paunawa**:
Ang dokumentong ito ay isinalin gamit ang serbisyong pagsasaling AI na Co-op Translator (https://github.com/Azure/co-op-translator). Bagaman nagsusumikap kami para sa katumpakan, pakitandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga pagkakamali o hindi tumpak na bahagi. Ang orihinal na dokumento sa likas nitong wika ang dapat ituring na awtoritatibong sanggunian. Para sa mahalagang impormasyon, inirerekomenda ang propesyonal na pagsasalin ng tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na nagmumula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->