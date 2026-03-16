# Memory para sa AI Agents 
[![Memorya ng Ahente](../../../translated_images/tl/lesson-13-thumbnail.959e3bc52d210c64.webp)](https://youtu.be/QrYbHesIxpw?si=qNYW6PL3fb3lTPMk)

Kapag pinag-uusapan ang mga natatanging benepisyo ng paglikha ng AI Agents, dalawang bagay ang karaniwang tinatalakay: ang kakayahang tumawag ng mga tool para kumpletuhin ang mga gawain at ang kakayahang mag-improve sa paglipas ng panahon. Ang memorya ang nasa pundasyon ng paglikha ng self-improving na agent na makakalikha ng mas magagandang karanasan para sa ating mga user.

Sa leksyong ito, titingnan natin kung ano ang memorya para sa AI Agents at kung paano natin ito pamamahalaan at gagamitin para sa kapakinabangan ng ating mga aplikasyon.

## Introduksyon

Sasaklawin ng leksyong ito:

• **Pag-unawa sa Memorya ng AI Agent**: Ano ang memorya at bakit ito mahalaga para sa mga agent.

• **Pagpapatupad at Pag-iimbak ng Memorya**: Praktikal na mga paraan para magdagdag ng kakayahan sa memorya sa iyong mga AI agent, na nakatuon sa short-term at long-term memory.

• **Paggawa ng Self-Improving na mga AI Agent**: Paano pinapagana ng memorya ang mga agent na matuto mula sa mga nakaraang interaksyon at mag-improve sa paglipas ng panahon.

## Available Implementations

Kasama sa leksyong ito ang dalawang komprehensibong notebook tutorial:

• **[13-agent-memory.ipynb](./13-agent-memory.ipynb)**: Nagpapatupad ng memory gamit ang Mem0 at Azure AI Search kasama ang Semantic Kernel framework

• **[13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)**: Nagpapatupad ng structured memory gamit ang Cognee, na awtomatikong bumubuo ng knowledge graph na suportado ng embeddings, binibigyang-buhay ang graph, at matalinong retrieval

## Mga Layunin sa Pagkatuto

Pagkatapos makumpleto ang leksyon na ito, malalaman mo kung paano:

• **Pag-iba-ibahin ang iba't ibang uri ng memorya ng AI agent**, kabilang ang working, short-term, at long-term memory, pati na rin ang mga espesyalisadong anyo tulad ng persona at episodic memory.

• **Magpatupad at mag-manage ng short-term at long-term memory para sa AI agents** gamit ang Semantic Kernel framework, na ginagamit ang mga tool tulad ng Mem0, Cognee, Whiteboard memory, at pag-integrate sa Azure AI Search.

• **Maunawaan ang mga prinsipyo sa likod ng self-improving na AI agents** at kung paano nakakatulong ang matibay na sistema ng pamamahala ng memorya sa tuloy-tuloy na pagkatuto at adaptasyon.

## Pag-unawa sa Memorya ng AI Agent

Sa pinakapuso, **ang memorya para sa AI agents ay tumutukoy sa mga mekanismong nagpapahintulot sa kanila na magtago at magbalik-tanaw ng impormasyon**. Ang impormasyong ito ay maaaring mga partikular na detalye tungkol sa isang pag-uusap, mga kagustuhan ng user, mga nagdaang aksyon, o kahit mga natutunang pattern.

Kung walang memorya, ang mga AI application ay kadalasang stateless, na nangangahulugang ang bawat interaksyon ay nagsisimula mula sa simula. Nagreresulta ito sa paulit-ulit at nakakainip na karanasan ng user kung saan ang agent ay "nakakalimot" ng naunang konteksto o mga kagustuhan.

### Bakit Mahalaga ang Memorya?

Ang katalinuhan ng isang agent ay malalim na naka-ugnay sa kakayahan nitong alalahanin at gamitin ang nakaraang impormasyon. Pinahihintulutan ng memorya ang mga agent na maging:

• **Reflective**: Natututo mula sa mga nagdaang aksyon at kinalabasan.

• **Interactive**: Pinananatili ang konteksto sa isang nagpapatuloy na pag-uusap.

• **Proactive at Reactive**: Ina-asahan ang mga pangangailangan o tumutugon nang angkop batay sa makasaysayang datos.

• **Autonomous**: Gumagana nang mas independyente sa pamamagitan ng pagkuha mula sa naka-imbak na kaalaman.

Ang layunin ng pagpapatupad ng memorya ay gawing mas **mapagkakatiwalaan at kakayahan** ang mga agent.

### Mga Uri ng Memorya

#### Working Memory

Isipin ito bilang isang piraso ng scratch paper na ginagamit ng agent sa loob ng isang solong, nagpapatuloy na gawain o proseso ng pag-iisip. Ito ay humahawak ng agarang impormasyon na kailangan upang kalkulahin ang susunod na hakbang.

Para sa mga AI agents, ang working memory ay kadalasang kumukuha ng pinaka-makabuluhang impormasyon mula sa isang pag-uusap, kahit na mahaba o na-truncate ang buong chat history. Nakatuon ito sa pagkuha ng mahahalagang elemento tulad ng mga requirement, proposal, desisyon, at aksyon.

**Halimbawa ng Working Memory**

Sa isang travel booking agent, maaaring mahuli ng working memory ang kasalukuyang kahilingan ng user, tulad ng "Gusto kong mag-book ng trip papuntang Paris". Ang partikular na requirement na ito ay hinahawakan sa agarang konteksto ng agent upang gabayan ang kasalukuyang interaksyon.

#### Short Term Memory

Ang uri ng memoryang ito ay nagtatago ng impormasyon para sa tagal ng isang pag-uusap o session. Ito ang konteksto ng kasalukuyang chat, na nagpapahintulot sa agent na tumukoy pabalik sa mga naunang turn sa dialogo.

**Halimbawa ng Short Term Memory**

Kung ang user ay nagtanong, "Magkano ang pamasahe ng flight papuntang Paris?" at pagkatapos ay sumunod na nagtanong ng "Paano naman ang accommodation doon?", tinitiyak ng short-term memory na alam ng agent na ang "doon" ay tumutukoy sa "Paris" sa loob ng parehong pag-uusap.

#### Long Term Memory

Ito ay impormasyon na nananatili sa paglipas ng maraming pag-uusap o session. Pinahihintulutan nito ang mga agent na maalala ang mga kagustuhan ng user, makasaysayang interaksyon, o pangkalahatang kaalaman sa mahabang panahon. Mahalaga ito para sa personalisasyon.

**Halimbawa ng Long Term Memory**

Maaaring mag-imbak ang long-term memory na "Mahilig si Ben sa skiing at outdoor activities, gusto ng kape na may tanawin ng bundok, at nais iwasan ang advanced ski slopes dahil sa dating pinsala". Ang impormasyong ito, na natutunan mula sa mga nakaraang interaksyon, ay nakakaapekto sa mga rekomendasyon sa mga susunod na travel planning sessions, na ginagawang lubos na personalized ang mga ito.

#### Persona Memory

Ang espesyalisadong uri ng memoryang ito ay tumutulong sa isang agent na magkaroon ng konsistenteng "personality" o "persona". Pinapayagan nito ang agent na maalala ang mga detalye tungkol sa sarili nito o sa inaasahang tungkulin, na ginagawang mas maayos at naka-pokus ang mga interaksyon.

**Halimbawa ng Persona Memory**
Kung ang travel agent ay dinisenyo upang maging isang "expert ski planner," maaaring patatagin ng persona memory ang tungkuling ito, na nakaapekto sa mga tugon nito upang tumugma sa tono at kaalaman ng isang eksperto.

#### Workflow/Episodic Memory

Itong memorya ay nag-iimbak ng pagkakasunod-sunod ng mga hakbang na ginawa ng agent sa isang komplikadong gawain, kabilang ang mga tagumpay at kabiguan. Parang pag-alala ng mga partikular na "episode" o nakaraang karanasan upang matuto mula rito.

**Halimbawa ng Episodic Memory**

Kung sinubukan ng agent na mag-book ng isang partikular na flight ngunit nabigo dahil sa kawalan ng availability, maaaring irekord ng episodic memory ang kabiguang ito, na nagbibigay-daan sa agent na subukan ang mga alternatibong flight o ipaalam sa user ang isyu nang mas may kaalaman sa isang susunod na pagtatangka.

#### Entity Memory

Kabilang dito ang pagkuha at pag-alala ng mga partikular na entidad (tulad ng tao, lugar, o bagay) at mga pangyayari mula sa mga pag-uusap. Pinapayagan nito ang agent na bumuo ng isang istrukturadong pag-unawa sa mga mahahalagang elemento na napag-usapan.

**Halimbawa ng Entity Memory**

Mula sa isang pag-uusap tungkol sa isang nakaraang biyahe, maaaring makuha ng agent ang "Paris," "Eiffel Tower," at "dinner sa Le Chat Noir restaurant" bilang mga entidad. Sa isang susunod na interaksyon, maaaring maalala ng agent ang "Le Chat Noir" at mag-alok na gumawa ng bagong reserbasyon doon.

#### Structured RAG (Retrieval Augmented Generation)

Habang ang RAG ay isang mas malawak na teknik, binibigyang-diin ang "Structured RAG" bilang isang makapangyarihang teknolohiya sa memorya. Kinukuha nito ang dense, istrukturadong impormasyon mula sa iba't ibang pinagkukunan (mga pag-uusap, email, imahe) at ginagamit ito upang pagandahin ang precision, recall, at bilis sa mga tugon. Hindi tulad ng klasikong RAG na umaasa lamang sa semantic similarity, ang Structured RAG ay gumagana kasama ng likas na istruktura ng impormasyon.

**Halimbawa ng Structured RAG**

Sa halip na simpleng tumugma ng mga keyword, maaaring i-parse ng Structured RAG ang mga detalye ng flight (destinasyon, petsa, oras, airline) mula sa isang email at iimbak ang mga ito sa isang istrukturadong paraan. Pinapahintulutan nito ang mga tumpak na query tulad ng "Anong flight ang na-book ko papuntang Paris noong Martes?"

## Pagpapatupad at Pag-iimbak ng Memorya

Ang pagpapatupad ng memorya para sa AI agents ay kinapapalooban ng isang sistematikong proseso ng **pamamahala ng memorya**, na kinabibilangan ng pag-generate, pag-iimbak, pag-retrieve, pag-integrate, pag-update, at kahit ang "pagkakalimot" (o pagtanggal) ng impormasyon. Ang retrieval ay isang partikular na kritikal na aspeto.

### Espesyal na Mga Tool para sa Memorya

#### Mem0

Isang paraan para mag-imbak at mag-manage ng memorya ng agent ay ang paggamit ng mga espesyal na tool tulad ng Mem0. Gumagana ang Mem0 bilang isang persistent memory layer, na nagpapahintulot sa mga agent na maalala ang mga kaugnay na interaksyon, mag-imbak ng mga kagustuhan ng user at factual context, at matuto mula sa mga tagumpay at kabiguan sa paglipas ng panahon. Ang ideya rito ay ang mga stateless na agent ay nagiging stateful.

Gumagana ito sa pamamagitan ng isang **two-phase memory pipeline: extraction at update**. Una, ang mga mensaheng idinagdag sa thread ng agent ay ipinapadala sa serbisyo ng Mem0, na gumagamit ng isang Large Language Model (LLM) upang ibuod ang kasaysayan ng pag-uusap at kunin ang mga bagong memorya. Kasunod nito, isang LLM-driven update phase ang tumutukoy kung magdadagdag, magbabago, o magtatanggal ng mga memoryang ito, iniimbak ang mga ito sa isang hybrid data store na maaaring magsama ng vector, graph, at key-value databases. Sinusuportahan din ng sistemang ito ang iba't ibang uri ng memorya at maaaring magsama ng graph memory para sa pamamahala ng mga relasyon sa pagitan ng mga entidad.

#### Cognee

Isa pang makapangyarihang paraan ay ang paggamit ng **Cognee**, isang open-source semantic memory para sa AI agents na nagbabago ng istrukturado at di-istrukturadong data sa queryable knowledge graphs na sinusuportahan ng embeddings. Nagbibigay ang Cognee ng isang **dual-store architecture** na pinagsasama ang vector similarity search at graph relationships, na nagpapahintulot sa mga agent na maunawaan hindi lamang kung anong impormasyon ang magkakatulad, kundi kung paano nauugnay ang mga konsepto sa isa't isa.

Magaling ito sa **hybrid retrieval** na pinaghalong vector similarity, graph structure, at LLM reasoning - mula raw chunk lookup hanggang graph-aware question answering. Pinananatili ng sistema ang **living memory** na umuunlad at lumalaki habang nananatiling queryable bilang isang konektadong graph, sumusuporta sa parehong short-term session context at long-term persistent memory.

Ipinapakita ng Cognee notebook tutorial ([13-agent-memory-cognee.ipynb](./13-agent-memory-cognee.ipynb)) ang pagbuo ng pinagsamang memory layer na ito, na may praktikal na mga halimbawa ng pag-ingest ng iba't ibang pinagkukunan ng data, pag-vizualisa ng knowledge graph, at pag-query gamit ang iba't ibang search strategies na nakaangkop sa partikular na pangangailangan ng agent.

### Pag-iimbak ng Memorya gamit ang RAG

Higit pa sa mga espesyal na tool sa memorya tulad ng mem0, maaari mong gamitin ang matatag na mga search service tulad ng **Azure AI Search bilang backend para sa pag-iimbak at pag-retrieve ng mga memorya**, lalo na para sa structured RAG.

Pinapahintulutan ka nitong gawing grounded ang mga tugon ng iyong agent gamit ang iyong sariling data, na tinitiyak ang mas may kaugnayan at mas tumpak na mga sagot. Maaaring gamitin ang Azure AI Search upang mag-imbak ng mga memoryang partikular sa user (hal., travel memories), product catalogs, o anumang iba pang domain-specific na kaalaman.

Sinusuportahan ng Azure AI Search ang mga kakayahan tulad ng **Structured RAG**, na mahusay sa pagkuha at pag-retrieve ng dense, istrukturadong impormasyon mula sa malalaking dataset tulad ng conversation histories, email, o kahit mga imahe. Nagbibigay ito ng "superhuman precision and recall" kumpara sa tradisyonal na text chunking at embedding approaches.

## Paggawa ng AI Agents na Self-Improve

Isang karaniwang pattern para sa self-improving agents ay ang pagpapakilala ng isang **"knowledge agent"**. Ang hiwalay na agent na ito ay nag-oobserba sa pangunahing pag-uusap sa pagitan ng user at ng pangunahing agent. Ang tungkulin nito ay:

1. **Tukuyin ang mahalagang impormasyon**: Alamin kung may anumang bahagi ng pag-uusap na karapat-dapat i-save bilang pangkalahatang kaalaman o isang partikular na kagustuhan ng user.

2. **I-extract at ibuod**: I-destill ang mahalagang natutunan o kagustuhan mula sa pag-uusap.

3. **I-imbak sa knowledge base**: I-persist ang na-extract na impormasyon, madalas sa isang vector database, upang ma-retrieve ito sa ibang pagkakataon.

4. **Palawakin ang mga susunod na query**: Kapag nagsimula ang user ng bagong query, kino-query ng knowledge agent ang mga naaangkop na naka-imbak na impormasyon at idinadagdag ito sa prompt ng user, nagbibigay ng mahalagang konteksto sa pangunahing agent (katulad ng RAG).

### Mga Optimizasyon para sa Memorya

• **Pamamahala ng Latency**: Upang maiwasan ang pagbagal ng interaksyon ng user, maaaring gumamit muna ng mas mura at mas mabilis na modelo para mabilis na i-check kung ang impormasyon ay mahalagang i-imbak o i-retrieve, at tatawagin lamang ang mas kumplikadong extraction/retrieval process kapag kinakailangan.

• **Pagpapanatili ng Knowledge Base**: Para sa lumalaking knowledge base, ang mga impormasyong hindi gaanong ginagamit ay maaaring ilipat sa "cold storage" upang pamahalaan ang gastos.

## May Karagdagang Mga Tanong Tungkol sa Agent Memory?

Sumali sa [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) upang makipagkita sa iba pang mga nag-aaral, dumalo sa office hours at masagot ang iyong mga tanong tungkol sa AI Agents.

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
Paunawa:
Ang dokumentong ito ay isinalin gamit ang serbisyo ng AI na pagsasalin na Co-op Translator (https://github.com/Azure/co-op-translator). Bagaman nagsusumikap kami para sa katumpakan, pakatandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga error o pagkakamali. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring na pinagmumulan ng awtoridad. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasalin ng isang human translator. Hindi kami mananagot sa anumang mga hindi pagkakaunawaan o maling interpretasyon na maaaring magmula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->