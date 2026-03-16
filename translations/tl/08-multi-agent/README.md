[![Multi-Agent Design](../../../translated_images/tl/lesson-8-thumbnail.278a3e4a59137d62.webp)](https://youtu.be/V6HpE9hZEx0?si=A7K44uMCqgvLQVCa)

> _(I-click ang larawan sa itaas upang mapanood ang video ng araling ito)_

# Mga pattern ng disenyo para sa multi-agent

Sa sandaling magsimula kang magtrabaho sa isang proyekto na may kinalaman sa maraming mga ahente, kakailanganin mong isaalang-alang ang pattern ng disenyo para sa multi-agent. Gayunpaman, maaaring hindi agad malinaw kung kailan lilipat sa multi-agents at kung ano ang mga benepisyo nito.

## Panimula

Sa araling ito, nais nating sagutin ang mga sumusunod na tanong:

- Ano-ano ang mga scenario kung saan naaangkop ang multi-agents?
- Ano ang mga benepisyo ng paggamit ng multi-agents kumpara sa iisang agent na gumagawa ng maraming gawain?
- Ano ang mga sangkap sa pagpapatupad ng multi-agent design pattern?
- Paano natin nakikita kung paano nakikipag-ugnayan ang maraming mga ahente sa isa't isa?

## Mga Layunin sa Pagkatuto

Pagkatapos ng araling ito, dapat mong magawa ang mga sumusunod:

- Tukuyin ang mga senaryong naaangkop ang multi-agents
- Kilalanin ang mga benepisyo ng paggamit ng multi-agents kaysa iisang agent.
- Unawain ang mga sangkap sa pagpapatupad ng multi-agent design pattern.

Ano ang mas malawak na larawan?

*Ang mga multi-agent ay isang pattern ng disenyo na nagpapahintulot sa maraming mga ahente na magtulungan upang makamit ang isang layunin*.

Malawak itong ginagamit sa iba't ibang larangan, kabilang ang robotics, autonomous systems, at distributed computing.

## Mga Senaryo Kung Saan Naaangkop ang Multi-Agents

Ano nga ba ang mga senaryo na magandang gamitin ang multi-agents? Ang sagot ay marami, lalo na sa mga sumusunod:

- **Malalaking gawain**: Ang malalaking gawain ay maaaring hatiin sa maliliit na tungkulin at italaga sa iba't ibang mga ahente, na nagpapahintulot sa sabayang pagproseso at mas mabilis na pagtapos. Halimbawa nito ay sa malawakang pagproseso ng datos.
- **Komplikadong gawain**: Tulad ng malalaking gawain, ang komplikadong gawain ay maaaring hatiin sa maliit na mga sub-tasks at italaga sa iba't ibang ahente na nag-specialize sa partikular na aspekto ng gawain. Isang halimbawa nito ay sa mga autonomous na sasakyan kung saan iba't ibang ahente ang namamahala sa navigasyon, pagtuklas ng hadlang, at komunikasyon sa ibang sasakyan.
- **Iba't ibang kadalubhasaan**: Ang iba't ibang ahente ay maaaring magkaroon ng ibat-ibang kadalubhasaan, kaya't mas epektibong hawakan nila ang iba’t ibang bahagi ng gawain kaysa iisang ahente lamang. Halimbawa dito ay sa healthcare kung saan ang mga ahente ay namamahala sa diagnostics, mga plano sa paggamot, at pagmamanman ng pasyente.

## Mga Benepisyo ng Paggamit ng Multi-Agents Kaysa Isang Ahente Lamang

Maaaring gumana ng maayos ang isang sistema ng ahente para sa mga simpleng gawain, ngunit para sa mas kumplikadong mga gawain, ang paggamit ng maraming ahente ay nagbibigay ng ilang mga benepisyo:

- **Espesyalisasyon**: Ang bawat ahente ay maaaring magspesyalis sa isang partikular na gawain. Ang kawalan ng espesyalisasyon sa isang ahente lamang ay nangangahulugang mayroon kang isang ahente na kayang gawin lahat ng bagay ngunit maaaring malito kung ano ang gagawin kapag naharap sa isang komplikadong gawain. Maaari nitong tapusin ang isang gawain na hindi naman ito ang mas angkop gawin.
- **Scalability**: Mas madali ang pagpapalawak ng sistema sa pamamagitan ng pagdaragdag ng mas maraming ahente kaysa pagbibigay ng labis na trabaho sa isang ahente lamang.
- **Fault Tolerance**: Kung may isang ahente na bumigo, ang iba ay maaaring magpatuloy sa kanilang gawain, na tinitiyak ang pagiging maaasahan ng sistema.

Halimbawa, mag-book tayo ng isang biyahe para sa isang user. Ang isang sistema ng ahente lang ay kailangang hawakan ang lahat ng aspeto ng proseso ng pag-book, mula sa paghahanap ng mga flight hanggang sa pag-book ng mga hotel at rental cars. Para magawa ito ng iisang ahente, kailangang may mga kagamitan ito para hawakan ang lahat ng mga gawain na ito. Maaari itong humantong sa isang komplikado at monolitikong sistema na mahirap panatilihin at palawakin. Sa kabilang banda, ang multi-agent system ay maaaring may iba't ibang ahente na espesyalista sa paghahanap ng mga flight, pag-book ng mga hotel, at rental cars. Ginagawang mas modular, mas madali panatilihin, at scalable ang sistema.

Ihambing ito sa isang travel bureau na pinapatakbo ng isang maliit na tindahan laban sa isang travel bureau na pinapatakbo bilang isang franchise. Ang maliit na tindahan ay may isang ahente na humahawak ng lahat ng aspeto ng proseso ng pag-book, habang ang franchise ay may iba't ibang mga ahente na humahawak ng bawat aspeto ng proseso ng pag-book.

## Mga Sangkap sa Pagpapatupad ng Multi-Agent Design Pattern

Bago mo maipatupad ang multi-agent design pattern, kailangan mong maunawaan ang mga sangkap na bumubuo sa pattern.

Gawin nating mas tiyak ito gamit muli ang halimbawa ng pag-book ng biyahe para sa isang user. Sa kasong ito, ang mga sangkap ay maaaring kabilang ang:

- **Komunikasyon ng Ahente**: Kailangan mag-komunikasyon ang mga ahente sa paghahanap ng flight, pag-book ng hotel, at rental cars at magbahagi ng impormasyon tungkol sa mga kagustuhan at limitasyon ng user. Kailangan mong magpasiya kung anong mga protocol at pamamaraan ang gagamitin para sa komunikasyong ito. Ibig sabihin nito, ang ahente para sa paghahanap ng flight ay kailangang makipag-ugnayan sa ahente para sa pag-book ng hotel upang matiyak na ang hotel ay naka-book para sa parehong mga petsa ng flight. Nangangahulugan ito na kailangang magbahagi ng impormasyon ang mga ahente tungkol sa mga petsa ng paglalakbay ng user, kaya kailangan mong magpasiya *kung alin sa mga ahente ang magbabahagi ng impormasyon at paano nila ito ibabahagi*.
- **Mga Mekanismo ng Koordinasyon**: Kailangan mag-coordinate ang mga ahente ng kanilang mga aksyon upang matiyak na natutugunan ang mga kagustuhan at limitasyon ng user. Halimbawa, maaaring gusto ng user ng hotel na malapit sa paliparan samantalang ang limitasyon ay na ang mga rental cars ay available lamang sa paliparan. Nangangahulugan ito na ang ahente sa pag-book ng hotel ay kailangang makipag-coordinate sa ahente sa pag-book ng rental cars upang matiyak na natutugunan ang mga kagustuhan at limitasyon ng user. Kailangan mong magpasiya *kung paano nagko-coordinate ang mga ahente ng kanilang mga aksyon*.
- **Arkitektura ng Ahente**: Kailangan magkaroon ng panloob na istruktura ang mga ahente upang makagawa ng desisyon at matuto mula sa kanilang mga interaksyon sa user. Nangangahulugan ito na ang ahente para sa paghahanap ng flight ay kailangang may istruktura upang magdesisyon kung aling mga flight ang ire-rekomenda sa user. Kailangan mong magpasiya *kung paano gumagawa ng desisyon at natututo ang mga ahente mula sa kanilang mga interaksyon sa user*. Halimbawa kung paano natututo at umuunlad ang isang ahente ay maaaring ang ahente sa flight ay gumamit ng machine learning model upang irekomenda ang mga flight batay sa mga nakaraang kagustuhan ng user.
- **Visibility sa Interaksyon ng Multi-Agent**: Kailangan mong makita kung paano nag-iinterak ang iba't ibang mga ahente. Nangangahulugan ito na kailangan mong magkaroon ng mga tool at teknik para sa pagsubaybay sa mga gawain at interaksyon ng mga ahente. Maaari itong tumukoy sa mga logging at monitoring tools, visualization tools, at performance metrics.
- **Mga Pattern sa Multi-Agent**: May iba't ibang pattern sa pagpapatupad ng multi-agent systems, tulad ng centralized, decentralized, at hybrid architectures. Kailangan mong magpasiya kung anong pattern ang pinaka-angkop sa iyong use case.
- **Tao sa Loop**: Sa karamihan ng mga kaso, may tao sa proseso at kailangan mong turuan ang mga ahente kung kailan hihingi ng interbensyon ng tao. Maaari itong nasa anyo ng user na humihiling para sa partikular na hotel o flight na hindi nirerekomenda ng mga ahente o humihingi ng kumpirmasyon bago mag-book ng flight o hotel.

## Visibility sa Interaksyon ng Multi-Agent

Mahalagang makita mo kung paano nagkaka-interak ang mga iba't ibang ahente. Mahalaga ito para sa pag-debug, pag-optimize, at pagtitiyak ng pagiging epektibo ng buong sistema. Upang magawa ito, kailangan mo ng mga tool at teknik para sa pagsubaybay ng mga aktibidad at interaksyon ng mga ahente. Maaari itong maging mga logging at monitoring tools, visualization tools, at performance metrics.

Halimbawa, sa kaso ng pag-book ng biyahe para sa isang user, maaari kang magkaroon ng dashboard na nagpapakita ng estado ng bawat ahente, mga kagustuhan at limitasyon ng user, at ang mga interaksyon sa pagitan ng mga ahente. Ang dashboard na ito ay maaaring magpakita ng mga petsa ng paglalakbay ng user, ang mga flight na nirerekomenda ng flight agent, mga hotel na nirerekomenda ng hotel agent, at mga rental car na nirerekomenda ng rental car agent. Bibigyan ka nito ng malinaw na pananaw kung paano nagkaka-interak ang mga ahente at kung natutugunan ba ang mga kagustuhan at limitasyon ng user.

Tingnan natin nang mas detalyado ang bawat aspeto.

- **Mga Logging at Monitoring Tools**: Gusto mong ma-log ang bawat aksyon na ginawa ng isang ahente. Ang isang log entry ay maaaring mag-imbak ng impormasyon tungkol sa ahenteng gumawa ng aksyon, ang aksyon na ginawa, ang oras ng pag-aksyon, at ang kinalabasan ng aksyon. Magagamit ang impormasyong ito para sa pag-debug, pag-optimize, at iba pa.

- **Mga Visualization Tools**: Makakatulong ang mga visualization tool na makita mo ang mga interaksyon sa pagitan ng mga ahente sa mas madaling intindihin na paraan. Halimbawa, maaari kang magkaroon ng graph na nagpapakita ng daloy ng impormasyon sa pagitan ng mga ahente. Makakatulong ito upang matukoy ang mga bottleneck, kakulangan ng kahusayan, at iba pang mga isyu sa sistema.

- **Performance Metrics**: Makakatulong ang mga performance metrics upang subaybayan ang kahusayan ng multi-agent system. Halimbawa, maaari mong subaybayan ang oras na ginugol para matapos ang isang gawain, dami ng mga gawain na natapos bawat yunit ng oras, at ang katumpakan ng mga rekomendasyon na ginawa ng mga ahente. Makakatulong ito upang tukuyin ang mga lugar na kailangang pagbutihin at mai-optimize ang sistema.

## Mga Pattern ng Multi-Agent

Tuklasin natin ang ilang mga konkretong pattern na maaari mong gamitin upang lumikha ng mga multi-agent apps. Narito ang ilang mga kawili-wiling pattern na dapat isaalang-alang:

### Group chat

Kapaki-pakinabang ang pattern na ito kapag nais mong lumikha ng group chat application kung saan maraming mga ahente ang maaaring makipag-usap sa isa't isa. Kadalasang gamit nito ang kolaborasyon sa team, customer support, at social networking.

Sa pattern na ito, bawat ahente ay kumakatawan sa isang user sa group chat, at nagpapalitan ng mga mensahe gamit ang isang protocol sa pagmemensahe. Maaari silang magpadala ng mga mensahe sa group chat, tumanggap ng mga mensahe mula sa group chat, at tumugon sa mga mensahe mula sa ibang mga ahente.

Maaaring ipatupad ang pattern na ito gamit ang centralized architecture kung saan ang lahat ng mensahe ay dumadaan sa isang central server, o decentralized architecture kung saan ang mga mensahe ay ipinagpapalit nang direkta.

![Group chat](../../../translated_images/tl/multi-agent-group-chat.ec10f4cde556babd.webp)

### Hand-off

Ang pattern na ito ay kapaki-pakinabang kapag nais mong lumikha ng aplikasyon kung saan maraming mga ahente ang maaaring magpalitan ng mga gawain sa isa't isa.

Kadalasang gamit nito ang customer support, task management, at workflow automation.

Sa pattern na ito, bawat ahente ay kumakatawan sa isang gawain o hakbang sa isang workflow, at maaaring ipasa ng mga ahente ang mga gawain sa ibang mga ahente base sa mga paunang itinakdang panuntunan.

![Hand off](../../../translated_images/tl/multi-agent-hand-off.4c5fb00ba6f8750a.webp)

### Collaborative filtering

Kapaki-pakinabang ang pattern na ito kapag nais mong lumikha ng aplikasyon kung saan maraming mga ahente ang nagtutulungan upang gumawa ng mga rekomendasyon sa mga user.

Bakit mo gustong maraming mga ahente ang mag-collaborate? Dahil bawat ahente ay maaaring may ibang kadalubhasaan at maaaring mag-ambag sa proseso ng rekomendasyon sa iba't ibang paraan.

Halimbawa, gusto ng user ng rekomendasyon para sa pinakamaigiing stock na bibilhin sa stock market.

- **Eksperto sa industriya**: Isang ahente ang maaaring eksperto sa isang partikular na industriya.
- **Teknikal na analisis**: Isa pang ahente ang maaaring eksperto sa teknikal na analisis.
- **Fundamental na analisis**: At isa pa ay maaaring eksperto sa fundamental na analisis. Sa pagtutulungan, makakapagbigay ang mga ahenteng ito ng mas komprehensibong rekomendasyon sa user.

![Recommendation](../../../translated_images/tl/multi-agent-filtering.d959cb129dc9f608.webp)

## Senaryo: Proseso ng Refund

Isaalang-alang ang senaryo kung saan ang isang customer ay nagtatangkang makakuha ng refund para sa isang produkto, maaaring maraming mga ahente ang kasangkot sa prosesong ito ngunit hatiin natin ito sa mga ahenteng espesipiko para sa prosesong ito at mga general agents na maaaring gamitin sa ibang mga proseso.

**Mga Ahente na Espesipiko sa Proseso ng Refund**:

Narito ang ilang mga ahente na maaaring kasangkot sa refund process:

- **Customer agent**: Kinakatawan nito ang customer at responsable sa pagsisimula ng proseso ng refund.
- **Seller agent**: Kinakatawan ang seller at responsable sa pagproseso ng refund.
- **Payment agent**: Kinakatawan ang proseso ng pagbabayad at responsable sa pag-refund ng bayad ng customer.
- **Resolution agent**: Kinakatawan ang proseso ng resolusyon at responsable sa paglutas ng anumang problema na lumitaw habang ginagawa ang refund.
- **Compliance agent**: Kinakatawan ang proseso ng pagsunod sa mga alituntunin at responsable sa pagtitiyak na ang proseso ng refund ay sumusunod sa mga regulasyon at patakaran.

**Mga General Agents**:

Maaaring gamitin ang mga ahenteng ito sa ibang bahagi ng iyong negosyo.

- **Shipping agent**: Kinakatawan ang proseso ng pagpapadala at responsable sa pagpapadala ng produkto pabalik sa seller. Magagamit ito para sa proseso ng refund at sa pangkalahatang pagpapadala ng produkto mula sa pagbili.
- **Feedback agent**: Kinakatawan ang proseso ng feedback at responsable sa pagkolekta ng puna mula sa customer. Maaaring mangyari ang feedback anumang oras, hindi lang sa proseso ng refund.
- **Escalation agent**: Kinakatawan ang proseso ng escalation at responsable sa pagpapasa ng mga isyu sa mas mataas na antas ng suporta. Maaari mo itong gamitin para sa anumang proseso na nangangailangan ng escalation.
- **Notification agent**: Kinakatawan ang proseso ng pagpapadala ng mga notipikasyon at responsable sa pagpapadala ng mga abiso sa customer sa iba't ibang yugto ng refund process.
- **Analytics agent**: Kinakatawan ang proseso ng pagsusuri ng datos na may kaugnayan sa refund process.
- **Audit agent**: Kinakatawan ang proseso ng audit at responsable sa pagtiyak na tama ang pagsasagawa ng proseso ng refund.
- **Reporting agent**: Kinakatawan ang proseso ng pag-uulat at responsable sa paggawa ng mga ulat tungkol sa proseso ng refund.
- **Knowledge agent**: Kinakatawan ang proseso ng kaalaman at responsable sa pagpapanatili ng kaalaman tungkol sa refund process. Maaari ding maging may kaalaman ito sa refunds at ibang bahagi ng iyong negosyo.
- **Security agent**: Kinakatawan ang proseso ng seguridad at responsable sa pagtitiyak ng kaligtasan ng proseso ng refund.
- **Quality agent**: Kinakatawan ang proseso ng kalidad at responsable sa pagtitiyak ng kalidad ng proseso ng refund.

Medyo marami ang mga ahenteng nabanggit para sa espesipikong proseso ng refund pati na rin sa mga pangkalahatang ahenteng maaaring gamitin sa ibang bahagi ng iyong negosyo. Sana'y nagbibigay ito ng ideya kung paano ka makakapagdesisyon kung aling mga ahente ang gagamitin sa iyong multi-agent system.

## Takdang-Aralin

Disenyo ng isang multi-agent system para sa proseso ng customer support. Tukuyin ang mga ahenteng kasangkot sa proseso, ang kanilang mga tungkulin at responsibilidad, at kung paano sila nakikipag-ugnayan sa isa't isa. Isaalang-alang ang parehong mga ahenteng espesipiko sa proseso ng customer support at mga general agents na maaaring gamitin sa ibang bahagi ng iyong negosyo.
> Mag-isip muna bago basahin ang sumusunod na solusyon, maaaring kailanganin mo ng mas maraming mga agent kaysa sa inaakala mo.

> TIP: Isipin ang iba't ibang yugto ng proseso ng customer support at isaalang-alang din ang mga agent na kailangan para sa anumang sistema.

## Solution

[Solution](./solution/solution.md)

## Knowledge checks

Question: Kailan mo dapat isaalang-alang ang paggamit ng multi-agents?

- [ ] A1: Kapag mayroon kang maliit na workload at simpleng gawain.
- [ ] A2: Kapag mayroon kang malaking workload
- [ ] A3: Kapag mayroon kang simpleng gawain.

[Solution quiz](./solution/solution-quiz.md)

## Summary

Sa leksyong ito, tiningnan natin ang multi-agent design pattern, kabilang ang mga sitwasyon kung saan ang multi-agents ay naaangkop, ang mga benepisyo ng paggamit ng multi-agents kumpara sa isang solong agent, ang mga pundasyon sa pagpapatupad ng multi-agent design pattern, at kung paano magkaroon ng visibility kung paano nakikipag-ugnayan ang iba't ibang agent sa isa't isa.

### May Karagdagang Mga Tanong Tungkol sa Multi-Agent Design Pattern?

Sumali sa [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) upang makipagkita sa ibang mga nag-aaral, dumalo sa office hours, at makakuha ng sagot sa iyong mga tanong tungkol sa AI Agents.

## Additional resources

- <a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/intro.html" target="_blank">AutoGen design patterns</a>
- <a href="https://www.analyticsvidhya.com/blog/2024/10/agentic-design-patterns/" target="_blank">Agentic design patterns</a>


## Previous Lesson

[Planning Design](../07-planning-design/README.md)

## Next Lesson

[Metacognition in AI Agents](../09-metacognition/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**Patalastas**:
Ang dokumentong ito ay isinalin gamit ang serbisyong AI na pagsasalin na [Co-op Translator](https://github.com/Azure/co-op-translator). Bagama't nagsusumikap kami para sa katumpakan, pakatandaan na ang mga awtomatikong pagsasalin ay maaaring maglaman ng mga kamalian o di-tumpak na impormasyon. Ang orihinal na dokumento sa orihinal nitong wika ang dapat ituring bilang pangunahing sanggunian. Para sa mahahalagang impormasyon, inirerekomenda ang propesyonal na pagsasalin ng tao. Hindi kami mananagot sa anumang hindi pagkakaintindihan o maling interpretasyon na maaaring magmula sa paggamit ng pagsasaling ito.
<!-- CO-OP TRANSLATOR DISCLAIMER END -->