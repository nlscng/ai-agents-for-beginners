[![Panimula sa Mga Ahente ng AI](../../../translated_images/tl/lesson-1-thumbnail.d21b2c34b32d35bb.webp)](https://youtu.be/3zgm60bXmQk?si=QA4CW2-cmul5kk3D)

> _(I-click ang larawan sa itaas upang panoorin ang video ng araling ito)_


# Panimula sa Mga Ahente ng AI at Mga Kaso ng Paggamit

Maligayang pagdating sa kursong "Mga Ahente ng AI para sa mga Nagsisimula"! Ang kursong ito ay nagbibigay ng mga pangunahing kaalaman at mga halimbawang praktikal para sa pagbuo ng Mga Ahente ng AI.

Sumali sa <a href="https://discord.gg/kzRShWzttr" target="_blank">Komunidad ng Azure AI sa Discord</a> upang makilala ang ibang mga nag-aaral at mga Tagabuo ng Mga Ahente ng AI at magtanong tungkol sa kursong ito.

Upang simulan ang kursong ito, sisimulan natin sa pag-unawa nang mas mabuti kung ano ang Mga Ahente ng AI at kung paano natin sila magagamit sa mga aplikasyon at mga workflow na ating binubuo.

## Panimula

Saklaw ng araling ito:

- Ano ang Mga Ahente ng AI at ano ang iba't ibang uri ng mga ahente?
- Aling mga kaso ng paggamit ang pinakaangkop para sa Mga Ahente ng AI at paano nila tayo matutulungan?
- Ano ang ilan sa mga pangunahing bahagi kapag nagdidisenyo ng mga Agentic na Solusyon?

## Mga Layunin sa Pagkatuto
Pagkatapos makumpleto ang araling ito, dapat mong magawa ang mga sumusunod:

- Maunawaan ang mga konsepto ng Mga Ahente ng AI at kung paano sila naiiba mula sa ibang mga solusyon ng AI.
- Gamitin ang Mga Ahente ng AI nang pinakaepektibo.
- Disenyuhin ang mga Agentic na solusyon nang produktibo para sa parehong mga gumagamit at mga customer.

## Pagpapakahulugan sa Mga Ahente ng AI at Mga Uri ng Mga Ahente ng AI

### Ano ang Mga Ahente ng AI?

Ang Mga Ahente ng AI ay **mga sistema** na nagpapahintulot sa **Malalaking Modelong Pangwika(LLMs)** na **gumawa ng mga aksyon** sa pamamagitan ng pagpapalawak ng kanilang mga kakayahan sa pamamagitan ng pagbibigay sa LLMs ng **access sa mga tool** at **kaalaman**.

Hatiin natin ang depinisyon na ito sa mas maliliit na bahagi:

- **Sistema** - Mahalaga na isipin ang mga ahente hindi bilang isang solong bahagi lamang kundi bilang isang sistema ng maraming bahagi. Sa pangunahing antas, ang mga bahagi ng isang Ahente ng AI ay:
  - **Kapaligiran** - Ang tinukoy na espasyo kung saan gumagana ang Ahente ng AI. Halimbawa, kung mayroon tayong ahenteng AI para sa pagreserba ng paglalakbay, ang kapaligiran ay maaaring ang sistema ng pagreserba ng paglalakbay na ginagamit ng Ahente ng AI upang kumpletuhin ang mga gawain.
  - **Mga Sensor** - May impormasyon ang mga kapaligiran at nagbibigay ng feedback. Ginagamit ng mga Ahente ng AI ang mga sensor upang mangalap at mag-interpret ng impormasyong ito tungkol sa kasalukuyang estado ng kapaligiran. Sa halimbawa ng Ahente ng Pagreserba ng Paglalakbay, maaaring magbigay ang sistema ng pagreserba ng impormasyon tulad ng availability ng hotel o mga presyo ng flight.
  - **Mga Aktuwador** - Kapag natanggap ng Ahente ng AI ang kasalukuyang estado ng kapaligiran, para sa kasalukuyang gawain tinutukoy ng ahente kung anong aksyon ang gagawin upang baguhin ang kapaligiran. Para sa ahente ng pagreserba ng paglalakbay, maaaring ito ay magpareserba ng magagamit na kuwarto para sa gumagamit.

![Ano ang Mga Ahente ng AI?](../../../translated_images/tl/what-are-ai-agents.1ec8c4d548af601a.webp)

**Malalaking Modelong Pangwika** - Umiiral na ang konsepto ng mga ahente bago pa malikha ang LLMs. Ang bentahe ng pagbuo ng Mga Ahente ng AI gamit ang LLMs ay ang kanilang kakayahang mag-interpret ng wikang pantao at datos. Pinapahintulutan ng kakayahang ito ang LLMs na i-interpret ang impormasyon ng kapaligiran at magtukoy ng plano upang baguhin ang kapaligiran.

**Gumawa ng mga Aksyon** - Sa labas ng mga sistema ng Ahente ng AI, limitado ang LLMs sa mga sitwasyon kung saan ang aksyon ay ang paggawa ng nilalaman o impormasyon batay sa prompt ng gumagamit. Sa loob ng mga sistema ng Ahente ng AI, makakamit ng LLMs ang mga gawain sa pamamagitan ng pag-interpret ng kahilingan ng gumagamit at paggamit ng mga tool na magagamit sa kanilang kapaligiran.

**Pag-access sa Mga Tool** - Ang mga tool na naa-access ng LLM ay tinutukoy ng 1) ang kapaligirang kinatatakbuhan nito at 2) ang developer ng Ahente ng AI. Para sa halimbawa ng aming travel agent, limitado ang mga tool ng ahente ng mga operasyon na available sa sistema ng pagreserba, at/o maaaring limitahan ng developer ang pag-access ng ahente sa mga tool para sa mga flight.

**Memory+Kaalaman** - Ang memorya ay maaaring panandalian sa konteksto ng pag-uusap sa pagitan ng gumagamit at ng ahente. Pangmatagalan, bukod sa impormasyong ibinibigay ng kapaligiran, maaaring kumuha rin ang Mga Ahente ng AI ng kaalaman mula sa ibang mga sistema, serbisyo, tool, at maging mula sa ibang mga ahente. Sa halimbawa ng travel agent, ang kaalamang ito ay maaaring maging impormasyon tungkol sa mga kagustuhan sa paglalakbay ng gumagamit na matatagpuan sa isang customer database.

### Iba't ibang uri ng mga ahente

Ngayon na mayroon tayong pangkalahatang depinisyon ng Mga Ahente ng AI, tingnan natin ang ilang tiyak na uri ng ahente at kung paano ito iaaplay sa isang AI agent para sa pagreserba ng paglalakbay.

| **Uri ng Ahente**             | **Paglalarawan**                                                                                                                      | **Halimbawa**                                                                                                                                                                                                                 |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Simpleng Reflex na Ahente**      | Gumagawa ng agarang aksyon batay sa mga paunang itinakdang patakaran.                                                                 | Binibigyang-kahulugan ng ahente ng paglalakbay ang konteksto ng email at ipinapasa ang mga reklamo tungkol sa paglalakbay sa customer service.                                                                                   |
| **Model-Based Reflex na Ahente** | Gumagawa ng mga aksyon batay sa isang modelo ng mundo at mga pagbabago sa modelong iyon.                                              | Pinaprioritize ng ahente ng paglalakbay ang mga ruta na may makabuluhang pagbabago sa presyo batay sa pag-access sa makasaysayang datos ng pagpepresyo.                                                                                 |
| **Goal-Based na Ahente**         | Lumilikha ng mga plano upang maabot ang mga tiyak na layunin sa pamamagitan ng pag-interpret ng layunin at pagtukoy ng mga aksyon upang makamit ito. | Nagre-reserba ang ahente ng paglalakbay ng isang paglalakbay sa pamamagitan ng pagtukoy ng kinakailangang mga ayos sa paglalakbay (kotse, pampublikong transportasyon, mga flight) mula sa kasalukuyang lokasyon papunta sa destinasyon. |
| **Utility-Based na Ahente**      | Isinasaalang-alang ang mga kagustuhan at binabalanse ang mga tradeoff sa numerikal na paraan upang matukoy kung paano makakamit ang mga layunin.    | Pinapakinabangan ng ahente ng paglalakbay ang kapakinabangan sa pamamagitan ng pagbibigay-halaga sa kaginhawahan kumpara sa gastos kapag nagre-reserba ng paglalakbay.                                                              |
| **Mga Ahenteng Nag-aaral**           | Humuhusay sa paglipas ng panahon sa pamamagitan ng pagtugon sa feedback at pag-aayos ng mga aksyon ayon dito.                                                        | Humuhusay ang ahente ng paglalakbay sa pamamagitan ng paggamit ng feedback ng customer mula sa mga post-trip survey upang gumawa ng mga pagbabago sa mga susunod na booking.                                                      |
| **Hierarchical na Ahente**       | Naglalaman ng maraming ahente sa isang patong-patong na sistema, kung saan hinahati ng mga ahenteng nasa mas mataas na antas ang mga gawain sa mas maiikling subtasks para kumpletuhin ng mga ahente sa mas mababang antas. | Kinakansela ng ahente ng paglalakbay ang isang paglalakbay sa pamamagitan ng paghahati ng gawain sa mga subtasks (halimbawa, pagkansela ng mga partikular na booking) at pagpapatupad nito ng mga ahente sa mas mababang antas, na nag-uulat pabalik sa ahente sa mas mataas na antas. |
| **Multi-Agent Systems (MAS)** | Nagkukumpleto ang mga ahente ng mga gawain nang independiyente, alinman nang magkatuwang o may kompetisyon.                                                           | Kooperatiba: Maraming ahente ang nagre-reserba ng partikular na serbisyo sa paglalakbay tulad ng mga hotel, flight, at libangan. Kompetitibo: Maraming ahente ang nagmamanage at nakikipagkompetensya sa isang ibinahaging kalendaryo ng pagreserba ng hotel upang magpareserba ng mga customer sa hotel. |

## Kailan Gamitin ang Mga Ahente ng AI

Sa naunang seksyon, ginamit namin ang kaso ng paggamit ng Ahente ng Paglalakbay upang ipaliwanag kung paano magagamit ang iba't ibang uri ng mga ahente sa iba't ibang senaryo ng pagreserba ng paglalakbay. Patuloy nating gagamitin ang aplikasyon na ito sa buong kurso.

Tingnan natin ang mga uri ng kaso ng paggamit na pinakamainam para sa Mga Ahente ng AI:

![Kailan Gamitin ang Mga Ahente ng AI?](../../../translated_images/tl/when-to-use-ai-agents.54becb3bed74a479.webp)


- **Mga Problemang Bukas ang Saklaw** - pinapayagan ang LLM na tukuyin ang mga kinakailangang hakbang upang makumpleto ang isang gawain dahil hindi ito palaging maaaring i-hardcode sa isang workflow.
- **Mga Proseso na Maraming Hakbang** - mga gawain na nangangailangan ng antas ng kompleksidad kung saan kailangang gumamit ang Ahente ng AI ng mga tool o impormasyon sa maraming pag-ikot sa halip na isang beses na pagkuha.  
- **Pagpapabuti sa Paglipas ng Panahon** - mga gawain kung saan maaaring humusay ang ahente sa paglipas ng panahon sa pamamagitan ng pagtanggap ng feedback mula sa kapaligiran nito o mga gumagamit upang makapagbigay ng mas mataas na kapakinabangan.

Tinatalakay namin ang higit pang mga konsiderasyon sa paggamit ng Mga Ahente ng AI sa araling Pagbuo ng Maaasahang Mga Ahente ng AI.

## Mga Pangunahing Kaalaman ng Agentic na Solusyon

### Pagbuo ng Ahente

Ang unang hakbang sa pagdidisenyo ng isang sistema ng Ahente ng AI ay tukuyin ang mga tool, aksyon, at mga pag-uugali. Sa kursong ito, nakatuon kami sa paggamit ng **Azure AI Agent Service** upang tukuyin ang aming mga Ahente. Nag-aalok ito ng mga katangian tulad ng:

- Pagpili ng mga Bukas na Modelo tulad ng OpenAI, Mistral, at Llama
- Paggamit ng Lisensiyadong Data sa pamamagitan ng mga provider tulad ng Tripadvisor
- Paggamit ng standardized na OpenAPI 3.0 na mga tool

### Mga Pattern ng Agentic

Ang komunikasyon sa mga LLM ay sa pamamagitan ng prompts. Dahil sa semi-autonomous na katangian ng Mga Ahente ng AI, hindi palaging posible o kinakailangan na mano-manong i-reprompt ang LLM pagkatapos ng pagbabago sa kapaligiran. Gumagamit kami ng **Agentic Patterns** na nagpapahintulot sa amin na i-prompt ang LLM sa maraming hakbang sa mas masuskalang paraan.

Ang kursong ito ay nahahati sa ilang kasalukuyang sikat na Agentic na pattern.

### Mga Framework ng Agentic

Pinapayagan ng Mga Framework ng Agentic ang mga developer na i-implementa ang mga agentic na pattern sa pamamagitan ng code. Nag-aalok ang mga framework na ito ng mga template, plugin, at tool para sa mas mahusay na kolaborasyon ng Mga Ahente ng AI. Nagbibigay din ang mga benepisyo na ito ng mga kakayahan para sa mas mahusay na pagmamasid at paglutas ng problema ng mga sistema ng Mga Ahente ng AI.

Sa kursong ito, susuriin natin ang research-driven na AutoGen framework at ang production-ready na Agent framework mula sa Semantic Kernel.

## Mga Halimbawang Code

- Python: [Framework ng Ahente](./code_samples/01-python-agent-framework.ipynb)
- .NET: [Framework ng Ahente](./code_samples/01-dotnet-agent-framework.md)

## May Iba Ka Pang Mga Tanong tungkol sa Mga Ahente ng AI?

Sumali sa [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) upang makipagkita sa ibang mga nag-aaral, dumalo sa oras ng opisina at masagot ang iyong mga tanong tungkol sa Mga Ahente ng AI.

## Naunang Aralin

[Pag-setup ng Kurso](../00-course-setup/README.md)

## Susunod na Aralin

[Pagsusuri sa Mga Framework ng Agentic](../02-explore-agentic-frameworks/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Paunawa**:
Isinalin ang dokumentong ito gamit ang serbisyong pagsasalin na pinapagana ng AI na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagaman nagsusumikap kami para sa katumpakan, pakitandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga pagkakamali o hindi tumpak na impormasyon. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring na awtoritatibong sanggunian. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasaling‑tao. Hindi kami mananagot sa anumang hindi pagkakaunawaan o maling interpretasyon na magmumula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->