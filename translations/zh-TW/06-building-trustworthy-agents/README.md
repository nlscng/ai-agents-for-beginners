[![值得信賴的 AI 代理](../../../translated_images/zh-TW/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(點擊上方圖片以觀看本課程影片)_

# 建立值得信賴的 AI 代理

## 介紹

本課程將涵蓋：

- 如何建立與部署安全且有效的 AI 代理
- 開發 AI 代理時的重要安全考量
- 開發 AI 代理時如何維護資料與使用者隱私

## 學習目標

完成本課程後，您將能夠：

- 確認並減輕建立 AI 代理時的風險
- 實施安全措施以確保資料和存取權限妥善管理
- 創造在維護資料隱私同時提供優質使用者體驗的 AI 代理

## 安全性

讓我們先看看如何建立安全的代理應用程式。安全性代表 AI 代理按設計運作。作為代理應用的建構者，我們擁有方法與工具來最大化安全性：

### 建立系統訊息框架

如果您曾使用大型語言模型（LLMs）建立 AI 應用，您會了解設計堅固系統提示或系統訊息的重要性。這些提示建立了 LLM 如何與使用者及資料互動的元規則、指示與指南。

對 AI 代理而言，系統提示更為重要，因為 AI 代理需要非常具體的指令來完成我們設計的任務。

為了創建可擴展的系統提示，我們可以使用系統訊息框架來建立應用中的一個或多個代理：

![建立系統訊息框架](../../../translated_images/zh-TW/system-message-framework.3a97368c92d11d68.webp)

#### 步驟 1：建立元系統訊息

元提示將由 LLM 用來產生我們建立之代理的系統提示。我們將其設計為範本，以便在需要時能有效率地建立多個代理。

以下為我們會給予 LLM 的元系統訊息範例：

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### 步驟 2：建立基本提示

下一步是建立一個基本提示來描述 AI 代理。您應包含代理的角色、代理將完成的任務，以及代理的其他責任。

以下是一個範例：

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### 步驟 3：將基本系統訊息提供給 LLM

現在，我們可以透過提供元系統訊息作為系統訊息並加入我們的基本系統訊息來優化此系統訊息。

這將產生更適合引導我們 AI 代理的系統訊息：

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

#### 步驟 4：迭代與改進

此系統訊息框架的價值在於能輕鬆擴展多個代理的系統訊息創建，並隨時間改善您的系統訊息。首次即能符合完整使用案例的系統訊息較為罕見。透過更改基本系統訊息並執行系統，您可以進行微調和改進，並比較與評估結果。

## 理解威脅

要建立值得信賴的 AI 代理，理解並減輕針對您 AI 代理的風險與威脅至關重要。以下介紹部分針對 AI 代理的不同威脅，以及您如何更好地規劃和準備。

![理解威脅](../../../translated_images/zh-TW/understanding-threats.89edeada8a97fc0f.webp)

### 任務與指令

**描述：** 攻擊者嘗試透過提示或操作輸入來更改 AI 代理的指令或目標。

**緩解：** 執行驗證檢查與輸入過濾，及早偵測潛在危險提示，避免被 AI 代理處理。由於此類攻擊通常需頻繁與代理互動，限制對話輪數亦是防範此類攻擊的方法。

### 存取關鍵系統

**描述：** 若 AI 代理可存取儲存敏感資料的系統或服務，攻擊者可能入侵代理與這些服務之間的通訊。這可能是直接攻擊，或透過代理間接取得系統資訊。

**緩解：** AI 代理應僅在必要時存取系統以避免此類攻擊。代理與系統之間的通訊也需安全。實作驗證與存取控制是保護此資訊的另一方法。

### 資源與服務超載

**描述：** AI 代理可使用不同工具和服務以完成任務。攻擊者可利用此能力透過 AI 代理發送大量請求攻擊這些服務，造成系統故障或高額成本。

**緩解：** 制定政策限制 AI 代理向服務發送請求的數量。限制對話輪數與請求數也可防止此類攻擊。

### 知識庫中毒

**描述：** 此類攻擊不是直接針對 AI 代理，而是針對 AI 代理使用的知識庫或其他服務。攻擊可能破壞 AI 代理使用的資料或資訊，導致代理對使用者回答帶有偏見或非預期內容。

**緩解：** 定期驗證 AI 代理工作流程中使用的資料。確保對資料的存取安全，僅授權可信人員進行更動，以避免此類攻擊。

### 鏈式錯誤

**描述：** AI 代理會存取多種工具和服務完成任務。攻擊者引起的錯誤可能導致代理所連接的其他系統失敗，使攻擊擴散且難以排查。

**緩解：** 一種方法是讓 AI 代理運行於受限環境中，例如在 Docker 容器中執行任務，以避免直接攻擊系統。建立備援機制並在特定系統回傳錯誤時啟用重試邏輯，也是防止大型系統故障的方式。

## 人員介入流程

另一種建立值得信賴 AI 代理系統的有效方式是使用人員介入流程（Human-in-the-loop）。此流程讓使用者能在運行中提供回饋給代理。使用者實際上充當多代理系統中的代理人，透過批准或終止運行程序進行控制。

![人員介入流程](../../../translated_images/zh-TW/human-in-the-loop.5f0068a678f62f4f.webp)

以下是使用 AutoGen 實現此概念的程式碼片段：

```python

# 建立代理人。
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # 使用 input() 從控制台獲取用戶輸入。

# 建立終止條件，當用戶說「APPROVE」時結束對話。
termination = TextMentionTermination("APPROVE")

# 建立團隊。
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# 運行對話並串流到控制台。
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# 在腳本中運行時使用 asyncio.run(...)。
await Console(stream)

```

## 結論

建立值得信賴的 AI 代理需要謹慎設計、健全的安全措施和持續迭代。透過實施結構化的元提示系統、理解潛在威脅與採用緩解策略，開發者能創造既安全又有效的 AI 代理。此外，結合人員介入流程確保 AI 代理與使用者需求保持一致，同時將風險降至最低。隨著 AI 持續進步，積極維持安全性、隱私和倫理面的態度，將是培養 AI 系統信任與可靠性的關鍵。

### 對建立值得信賴 AI 代理還有更多疑問？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord)，與其他學習者交流，參加辦公時間並取得 AI 代理的疑問解答。

## 附加資源

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">負責任 AI 概覽</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">生成式 AI 模型與 AI 應用評估</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">安全系統訊息</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">風險評估範本</a>

## 前一課

[Agentic RAG](../05-agentic-rag/README.md)

## 下一課

[規劃設計範式](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我們努力追求準確性，但請注意自動翻譯可能包含錯誤或不準確之處。原始文件之母語版本應視為權威來源。對於重要資訊，建議使用專業人工翻譯。我們不對因使用本翻譯所產生的任何誤解或誤用承擔責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->