# 使用 Agentic 協定（MCP、A2A 與 NLWeb）

[![Agentic 協定](../../../translated_images/zh-TW/lesson-11-thumbnail.b6c742949cf1ce2a.webp)](https://youtu.be/X-Dh9R3Opn8)

> _(點擊上方圖片以觀看本課程的影片)_

隨著 AI 代理人的使用增加，對於可確保標準化、安全性並支援開放創新的協定需求也相應增加。在本課程中，我們將介紹三個旨在滿足此需求的協定 — 模型上下文協定（Model Context Protocol，MCP）、代理人對代理人（Agent-to-Agent，A2A）與自然語言網路（Natural Language Web，NLWeb）。

## 簡介

在本課程中，我們將涵蓋：

• **MCP** 如何允許 AI 代理人存取外部工具與資料，以完成使用者任務。

• **A2A** 如何使不同的 AI 代理人之間能夠溝通與協作。

• **NLWeb** 如何為任何網站帶來自然語言介面，使 AI 代理人能發現並與內容互動。

## 學習目標

• **識別** MCP、A2A 和 NLWeb 在 AI 代理人情境中的核心目的與好處。

• **解釋** 每個協定如何促進 LLM、工具與其他代理人之間的溝通與互動。

• **辨認** 每個協定在建構複雜代理系統時所扮演的不同角色。

## 模型上下文協定

**Model Context Protocol (MCP)** 是一個開放標準，提供應用程式向 LLM 提供上下文與工具的標準化方式。這使得 AI 代理人能以一致的方式連接到不同資料來源與工具，成為一個「通用轉接器」。讓我們看看 MCP 的組成部分、與直接使用 API 相比的優勢，以及 AI 代理人可能如何使用 MCP 伺服器的範例。

### MCP 核心組件

MCP 採用一個 **client-server 架構**，其核心組件為：

• **Hosts** 是啟動與 MCP Server 連線的 LLM 應用程式（例如像 VSCode 這類的程式編輯器）。

• **Clients** 是主機應用程式中的元件，與伺服器維持一對一的連線。

• **Servers** 是公開特定能力的輕量程式。

協定中包含三個核心原語，這些就是 MCP 伺服器的能力：

• **Tools**：這些是 AI 代理人可以呼叫以執行動作的離散操作或函數。例如，天氣服務可能公開一個 "get weather" 工具，或電子商務伺服器可能公開一個 "purchase product" 工具。MCP 伺服器在其能力清單中會宣告每個工具的名稱、描述，以及輸入/輸出架構。

• **Resources**：這些是 MCP 伺服器可以提供的唯讀資料項或文件，客戶端可以按需取得。範例包括檔案內容、資料庫記錄或日誌檔。Resources 可以是文字（像程式碼或 JSON）或二進位檔（像圖像或 PDF）。

• **Prompts**：這些是預先定義的範本，提供建議的提示，允許更複雜的工作流程。

### MCP 的優點

MCP 為 AI 代理人提供重要優勢：

• **動態工具發現**：代理人可以動態接收伺服器提供的可用工具清單，以及這些工具的功能描述。這與傳統 API 不同，傳統 API 通常需要為整合撰寫靜態程式碼，意味著任何 API 變更都需要更新程式碼。MCP 提供「一次整合」的方法，帶來更高的適應性。

• **跨 LLM 的互通性**：MCP 能在不同 LLM 之間運作，提供彈性以切換核心模型來評估較佳效能。

• **標準化的安全性**：MCP 包含標準的驗證方法，當新增對其他 MCP 伺服器的存取時，可提升可擴充性。這比為各種傳統 API 管理不同密鑰與驗證類型更為簡單。

### MCP 範例

![MCP 圖表](../../../translated_images/zh-TW/mcp-diagram.e4ca1cbd551444a1.webp)

想像一個使用者想用由 MCP 驅動的 AI 助手訂飛機票。

1. **Connection**: AI 助手（MCP client）連接到航空公司提供的 MCP server。

2. **Tool Discovery**: 客戶端詢問航空公司的 MCP 伺服器，「你有哪些可用的工具？」伺服器回應像是 "search flights" 和 "book flights" 等工具。

3. **Tool Invocation**: 你接著請 AI 助手：「請搜尋一張從 Portland 到 Honolulu 的航班。」AI 助手使用其 LLM 判斷需要呼叫 "search flights" 工具，並將相關參數（出發地、目的地）傳給 MCP 伺服器。

4. **Execution and Response**: MCP 伺服器作為包裝器，實際呼叫航空公司的內部訂票 API，然後接收航班資訊（例如 JSON 資料）並回傳給 AI 助手。

5. **Further Interaction**: AI 助手呈現航班選項。當你選擇航班後，助理可能會在同一 MCP 伺服器上調用 "book flight" 工具來完成訂票。

## 代理人對代理人協定 (A2A)

當 MCP 專注於連接 LLM 到工具時，**Agent-to-Agent (A2A)** 協定更進一步，使不同的 AI 代理人之間能夠溝通與協作。A2A 將來自不同組織、環境與技術堆疊的 AI 代理人連接起來，以完成共同任務。

我們將檢視 A2A 的組件與優勢，並以我們的旅遊應用為例說明其應用方式。

### A2A 核心組件

A2A 著重於啟用代理人之間的溝通，並使他們協同完成使用者的子任務。協定的每個組件都為此做出貢獻：

#### Agent Card

類似於 MCP 伺服器分享工具清單的方式，Agent Card 包含：
- The Name of the Agent .
- 一個 **描述其所完成的一般任務** 的說明。
- 一個 **具體技能清單** 與描述，以幫助其他代理人（或甚至人類使用者）理解何時以及為何會想要呼叫該代理人。
- 代理人的 **當前 Endpoint URL**
- 代理人的 **版本** 及 **能力**（例如串流回應與推播通知）。

#### Agent Executor

Agent Executor 負責 **將使用者對話的上下文傳遞給遠端代理人**，遠端代理人需要這些資訊來理解需要完成的任務。在 A2A 伺服器中，代理人會使用其自己的大型語言模型（LLM）來解析進來的請求，並使用其內部工具執行任務。

#### Artifact

當遠端代理人完成所請求的任務後，其工作產出會建立為一個 artifact。artifact **包含代理人工作的結果**、**完成事項的描述**，以及透過協定傳遞的**文字上下文**。在 artifact 傳送後，與遠端代理人的連線會關閉，直到再次需要時才會重新建立。

#### Event Queue

此元件用於 **處理更新與傳遞訊息**。在生產環境中特別重要，用以防止代理人之間的連線在任務完成前被關閉，尤其是當任務完成可能需要較長時間時。

### A2A 的優點

• **增強的協作**：它使來自不同供應商與平台的代理人能互動、分享上下文並共同工作，促進跨越傳統互不相連系統的無縫自動化。

• **模型選擇彈性**：每個 A2A 代理人可以決定使用哪個 LLM 來處理其請求，允許各代理人使用最佳化或微調的模型，不像某些 MCP 情境下僅有單一 LLM 連線。

• **內建驗證**：驗證直接整合在 A2A 協定中，為代理人互動提供強健的安全框架。

### A2A 範例

![A2A 圖表](../../../translated_images/zh-TW/A2A-Diagram.8666928d648acc26.webp)

讓我們擴展之前的旅遊訂票情境，但這次使用 A2A。

1. **User Request to Multi-Agent**: 使用者與一個「旅遊代理人」A2A 客戶端/代理人互動，例如說：「請幫我預訂下週前往 Honolulu 的整個行程，包括航班、飯店與租車」。

2. **Orchestration by Travel Agent**: 旅遊代理人接收此複雜請求。它使用其 LLM 推理任務並判斷需要與其他專門代理人互動。

3. **Inter-Agent Communication**: 旅遊代理人接著使用 A2A 協定連接到下游代理人，例如由不同公司建立的「航空公司代理人」、「飯店代理人」與「租車代理人」。

4. **Delegated Task Execution**: 旅遊代理人將具體任務委派給這些專門代理人（例如「搜尋飛往 Honolulu 的航班」、「訂飯店」、「租車」）。每個專門代理人皆運行自己的 LLM 並使用其內部工具（這些工具本身也可能是 MCP 伺服器），以完成其特定的預訂任務。

5. **Consolidated Response**: 一旦所有下游代理人完成任務，旅遊代理人會整合結果（航班細節、飯店確認、租車預訂），並以聊天式的綜合回應發送給使用者。

## 自然語言網路（NLWeb）

網站長久以來一直是使用者存取互聯網資訊與資料的主要方式。

讓我們看看 NLWeb 的不同組件、NLWeb 的好處，以及透過我們的旅遊應用示範 NLWeb 如何運作的範例。

### NLWeb 的組件

- **NLWeb 應用程式（核心服務程式碼）**：處理自然語言問題的系統。它連接平台的不同部分以產生回應。你可以把它視為驅動網站自然語言功能的 **引擎**。

- **NLWeb 協定**：這是一套用於與網站進行自然語言互動的基本規則。它以 JSON 格式（通常使用 Schema.org）回傳回應。其目的是為「AI 網路」建立一個簡單的基礎，就像 HTML 讓線上分享文件成為可能一樣。

- **MCP Server（Model Context Protocol 端點）**：每個 NLWeb 設定也能作為 MCP 伺服器。這表示它可以與其他 AI 系統分享工具（像是一個「ask」方法）與資料。實務上，這使得網站的內容與能力可以被 AI 代理人使用，讓網站成為更廣泛「代理人生態系」的一部分。

- **嵌入模型**：這些模型用來將網站內容轉換成稱為向量（embeddings）的數值表示。這些向量以可供電腦比較與搜尋的方式捕捉語意。它們儲存在專用資料庫中，使用者可以選擇想使用的嵌入模型。

- **向量資料庫（檢索機制）**：該資料庫儲存網站內容的嵌入。當有人提出問題時，NLWeb 會檢查向量資料庫以快速找到最相關的資訊，並依相似度排序提供一組可能的答案。NLWeb 支援不同的向量儲存系統，如 Qdrant、Snowflake、Milvus、Azure AI Search 與 Elasticsearch。

### NLWeb 範例

![NLWeb 圖表](../../../translated_images/zh-TW/nlweb-diagram.c1e2390b310e5fe4.webp)

再以我們的旅遊訂票網站為例，但這次由 NLWeb 提供支援。

1. **Data Ingestion**: 旅遊網站現有的產品目錄（例如航班清單、飯店描述、旅遊套裝）會以 Schema.org 格式化或透過 RSS 載入。NLWeb 的工具會攝取這些結構化資料、建立嵌入，並將它們儲存在本地或遠端的向量資料庫中。

2. **Natural Language Query (Human)**: 使用者造訪網站，並非透過瀏覽選單，而是在聊天介面輸入：「幫我找下週在 Honolulu、有游泳池且適合親子的飯店」。

3. **NLWeb Processing**: NLWeb 應用程式接收此查詢。它會將查詢送往 LLM 以理解，同時在向量資料庫中搜尋相關的飯店清單。

4. **Accurate Results**: LLM 協助解讀資料庫的搜尋結果，根據「適合親子」、「有游泳池」和「Honolulu」等條件識別最佳匹配，然後格式化為自然語言回應。關鍵在於，回應參照網站目錄中的實際飯店，避免虛構資訊。

5. **AI Agent Interaction**: 因為 NLWeb 同時作為 MCP 伺服器，外部的 AI 旅遊代理人也可以連接到該網站的 NLWeb 實例。AI 代理人可以使用 `ask("Are there any vegan-friendly restaurants in the Honolulu area recommended by the hotel?")` 這個 MCP 方法直接查詢網站。NLWeb 實例會處理該查詢，若已載入餐廳資訊資料庫，將利用其資料並回傳結構化的 JSON 回應。

### 對 MCP/A2A/NLWeb 有更多問題嗎？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) 與其他學習者交流，參加辦公時間並獲得關於 AI 代理人的問題解答。

## 資源

- [MCP 初學者指南](https://aka.ms/mcp-for-beginners)  
- [MCP 文件](https://github.com/microsoft/semantic-kernel/tree/main/python/semantic-kernel/semantic_kernel/connectors/mcp)
- [NLWeb 儲存庫](https://github.com/nlweb-ai/NLWeb)
- [Semantic Kernel 指南](https://learn.microsoft.com/semantic-kernel/)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免責聲明：
本文件係使用 AI 翻譯服務 Co-op Translator（https://github.com/Azure/co-op-translator）所翻譯。雖然我們力求準確，但請留意自動翻譯可能含有錯誤或不精確之處。原始語言的文件應視為具權威性的來源。對於重要資訊，建議採用專業人工翻譯。我們不對因使用本翻譯而產生的任何誤解或錯誤詮釋承擔任何責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->