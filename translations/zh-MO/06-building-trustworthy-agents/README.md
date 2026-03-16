[![可靠的 AI 代理](../../../translated_images/zh-MO/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(點擊上方圖片觀看本課程影片)_

# 建立可靠的 AI 代理

## 介紹

本課程將涵蓋：

- 如何建立和部署安全且有效的 AI 代理
- 開發 AI 代理時的重要安全考量
- 開發 AI 代理時如何維護數據和用戶隱私

## 學習目標

完成本課程後，您將能夠：

- 識別和減輕創建 AI 代理時的風險
- 實施安全措施以確保數據和訪問權限得到妥善管理
- 創建維護數據隱私並提供優質用戶體驗的 AI 代理

## 安全性

我們先來看看如何建立安全的代理應用。安全意味著 AI 代理按設計執行。作為代理應用的開發者，我們有方法和工具來最大化安全：

### 建立系統訊息框架

如果您曾使用大型語言模型（LLM）建立 AI 應用，便知道設計健壯的系統提示或系統訊息有多重要。這些提示設定了元規則、指令和準則，規範 LLM 如何與用戶及數據互動。

對於 AI 代理來說，系統提示更為重要，因為 AI 代理需要非常具體的指示來完成我們為它們設計的任務。

為了建立可擴展的系統提示，我們可以使用系統訊息框架來構建一個或多個應用內代理：

![建立系統訊息框架](../../../translated_images/zh-MO/system-message-framework.3a97368c92d11d68.webp)

#### 步驟 1：建立元系統訊息

元提示將由 LLM 用來生成我們創建的代理的系統提示。我們將其設計為模板，以便在需要時能有效率地創建多個代理。

以下是我們會給 LLM 的元系統訊息範例：

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### 步驟 2：建立基本提示

下一步是建立描述 AI 代理的基本提示。您應該包含代理的角色、代理將完成的任務，以及代理的其他職責。

範例如下：

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### 步驟 3：向 LLM 提供基本系統訊息

現在我們可以優化這個系統訊息，方法是將元系統訊息作為系統訊息提供，再加上我們的基本系統訊息。

這將產生更適合指引我們 AI 代理的系統訊息：

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

#### 步驟 4：反覆修改與改進

這個系統訊息框架的價值在於能讓多個代理的系統訊息創建更易擴展，並隨時間改善您的系統訊息。您的系統訊息很少會在第一次就完全符合使用需求。能夠通過改變基本系統訊息並運行到系統中做小幅調整和改進，將幫助您比較和評估結果。

## 理解威脅

要建立可靠的 AI 代理，理解並降低對 AI 代理的風險和威脅非常重要。讓我們看看部分 AI 代理可能面對的不同威脅，以及您如何更好地規劃和防範。

![理解威脅](../../../translated_images/zh-MO/understanding-threats.89edeada8a97fc0f.webp)

### 任務與指令

**描述：** 攻擊者試圖通過提示或操控輸入來改變 AI 代理的指令或目標。

**減輕方法：** 執行驗證檢查和輸入過濾，以偵測可能危險的提示，防止其被 AI 代理處理。由於此類攻擊通常需要與代理頻繁互動，限制對話回合數也是防止此類攻擊的方法之一。

### 存取關鍵系統

**描述：** 若 AI 代理可存取存放敏感數據的系統及服務，攻擊者可能破壞代理與這些服務之間的通訊。這些攻擊可以是直接或間接嘗試從代理取得系統資訊。

**減輕方法：** AI 代理應僅在必要時獲得系統訪問權限以防止此類攻擊。代理與系統之間的通訊也應是安全的。實施驗證與存取控制是防護此資訊的另一種方式。

### 資源和服務過載

**描述：** AI 代理可存取多種工具和服務以完成任務。攻擊者可利用此能力透過 AI 代理發送大量請求來攻擊這些服務，可能導致系統故障或高額費用。

**減輕方法：** 實施政策以限制 AI 代理向服務發出請求的數量。限制對 AI 代理的對話回合數和請求量也是防止此類攻擊的方法。

### 知識庫中毒

**描述：** 此類攻擊不直接針對 AI 代理，而是針對 AI 代理將使用的知識庫及其他服務。這可能包括破壞代理用於完成任務的資料，導致對用戶產生偏頗或非預期的回應。

**減輕方法：** 定期驗證 AI 代理在工作流程中使用的資料。確保該資料的存取安全，並僅由信任的人員更動，避免此類攻擊。

### 累積性錯誤

**描述：** AI 代理存取各種工具和服務以完成任務。攻擊者引發的錯誤可能導致與代理連接的其他系統失效，使攻擊範圍擴大且難以排除故障。

**減輕方法：** 避免此情況一種方法是讓 AI 代理運行在有限環境中，例如在 Docker 容器內執行任務，以阻止直接系統攻擊。建立回退機制與重試邏輯，當某些系統回應錯誤時，也能防止更大範圍的系統故障。

## 人類在迴路中

另一種建立可靠 AI 代理系統的有效方式是使用「人類在迴路」(Human-in-the-loop) 方法。此流程讓用戶能在代理執行過程中提供反饋。用戶本質上在多代理系統中擔任代理身份，並可對執行程序給予批准或終止。

![人類在迴路中](../../../translated_images/zh-MO/human-in-the-loop.5f0068a678f62f4f.webp)

以下是使用 AutoGen 展示此概念實作的程式碼片段：

```python

# 建立代理。
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # 使用 input() 從主控台取得用戶輸入。

# 建立終止條件，當用戶說「APPROVE」時結束對話。
termination = TextMentionTermination("APPROVE")

# 建立團隊。
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# 執行對話並串流到主控台。
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# 在執行腳本時使用 asyncio.run(...)。
await Console(stream)

```

## 結論

建立可靠的 AI 代理需要謹慎設計、穩健的安全措施與持續迭代。透過實施結構化的元提示系統、了解潛在威脅並運用減緩策略，開發者能創造既安全又有效的 AI 代理。此外，結合人類在迴路的方法確保 AI 代理始終符合用戶需求，同時降低風險。隨著 AI 持續演進，持續在安全性、隱私及倫理方面採取主動態度，將是培養 AI 驅動系統信賴與可靠性的關鍵。

### 想了解更多關於建立可靠 AI 代理的問題嗎？

加入 [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) 與其他學習者互動，參加線上答疑時段，並解決您的 AI 代理相關問題。

## 其他資源

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">負責任的 AI 概述</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">生成式 AI 模型與 AI 應用評估</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">安全系統訊息</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">風險評估範本</a>

## 上一課

[Agentic RAG](../05-agentic-rag/README.md)

## 下一課

[規劃設計模式](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**免責聲明**：  
本文件係使用 AI 翻譯服務 [Co-op Translator](https://github.com/Azure/co-op-translator) 進行翻譯。雖然我哋致力於提供準確嘅翻譯，但請注意，自動翻譯可能存在錯誤或不準確之處。原始文件嘅母語版本應被視為唯一權威來源。對於重要資訊，建議採用專業人工翻譯。我哋不對因使用本翻譯而引起嘅任何誤解或曲解承擔責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->