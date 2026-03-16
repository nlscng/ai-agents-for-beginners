[![可信賴的 AI 代理](../../../translated_images/zh-HK/lesson-6-thumbnail.a58ab36c099038d4.webp)](https://youtu.be/iZKkMEGBCUQ?si=Q-kEbcyHUMPoHp8L)

> _(按上方圖片以觀看本課程的影片)_

# 建立可信賴的 AI 代理

## 介紹

本課程將涵蓋：

- 如何構建及部署安全且有效的 AI 代理
- 在開發 AI 代理時的重要安全考量。
- 在開發 AI 代理時如何維護資料與用戶私隱。

## 學習目標

完成本課程後，你將會知道如何：

- 在建立 AI 代理時識別及減輕風險。
- 實施安全措施以確保資料與存取得到妥善管理。
- 建立能維護資料私隱並提供優質使用者體驗的 AI 代理。

## 安全

首先讓我們看看如何建立安全的代理應用。安全意味著 AI 代理按設計運作。作為代理應用的構建者，我們有方法和工具可以最大化安全性：

### 建立系統訊息框架

如果你曾使用大型語言模型 (LLMs) 構建 AI 應用，就會知道設計一個強健的系統提示或系統訊息的重要性。這些提示會建立元規則、指示和準則，說明 LLM 如何與使用者和資料互動。

對於 AI 代理來說，系統提示更為重要，因為 AI 代理需要高度具體的指示來完成我們為它們設計的任務。

為了建立可擴展的系統提示，我們可以使用系統訊息框架來為應用中建立一個或多個代理：

![建立系統訊息框架](../../../translated_images/zh-HK/system-message-framework.3a97368c92d11d68.webp)

#### 第一步：建立一個元系統訊息 

元提示將由 LLM 用來為我們建立的代理產生系統提示。我們把它設計成一個範本，以便在需要時有效地建立多個代理。

以下是我們會給 LLM 的一個元系統訊息範例：

```plaintext
You are an expert at creating AI agent assistants. 
You will be provided a company name, role, responsibilities and other
information that you will use to provide a system prompt for.
To create the system prompt, be descriptive as possible and provide a structure that a system using an LLM can better understand the role and responsibilities of the AI assistant. 
```

#### 第二步：建立一個基本提示

接下來的步驟是建立一個基本提示來描述 AI 代理。你應該包含代理的角色、代理將完成的任務，以及其他任何代理的職責。

以下是一個範例：

```plaintext
You are a travel agent for Contoso Travel that is great at booking flights for customers. To help customers you can perform the following tasks: lookup available flights, book flights, ask for preferences in seating and times for flights, cancel any previously booked flights and alert customers on any delays or cancellations of flights.  
```

#### 第三步：向 LLM 提供基本系統訊息

現在我們可以透過將元系統訊息作為系統訊息並結合我們的基本系統訊息來最佳化此系統訊息。

這將產生一個更適合引導我們 AI 代理的系統訊息：

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

#### 第四步：反覆改進

此系統訊息框架的價值在於能更容易地為多個代理擴展建立系統訊息，並隨時間改進你的系統訊息。很少會有一個系統訊息在第一次就能適用於完整的使用情境。能夠透過更改基本系統訊息並將其在系統中執行，進行小幅調整和改進，將允許你比較和評估結果。

## 理解威脅

要建立值得信賴的 AI 代理，理解並減輕對你的 AI 代理的風險與威脅十分重要。讓我們只看看其中一些對 AI 代理的不同威脅，以及你如何更好地計劃和準備它們。

![理解威脅](../../../translated_images/zh-HK/understanding-threats.89edeada8a97fc0f.webp)

### 任務與指示

**描述：** 攻擊者試圖透過提示或操縱輸入來改變 AI 代理的指示或目標。

**緩解：** 執行驗證檢查和輸入過濾，以在 AI 代理處理前偵測潛在危險的提示。由於這些攻擊通常需要與代理頻繁互動，限制對話回合數也是防止此類攻擊的一種方式。

### 存取關鍵系統

**描述：** 如果 AI 代理能存取儲存敏感資料的系統和服務，攻擊者可能會破壞代理與這些服務之間的通訊。這些可能是直接攻擊或透過代理間接嘗試獲取關於這些系統的資訊。

**緩解：** AI 代理應僅在必要時才存取系統，以防止此類攻擊。代理與系統之間的通訊也應該是安全的。實施驗證和存取控制是保護此資訊的另一種方法。

### 資源與服務過載

**描述：** AI 代理可以存取不同工具和服務以完成任務。攻擊者可能利用此能力透過 AI 代理發送大量請求來攻擊這些服務，可能導致系統故障或高額費用。

**緩解：** 實施政策以限制 AI 代理對某服務可發出請求的數量。限制對話回合數和對 AI 代理的請求數也是防止此類攻擊的另一種方式。

### 知識庫中毒

**描述：** 這類攻擊並非直接針對 AI 代理，而是針對 AI 代理將使用的知識庫和其他服務。這可能包括破壞 AI 代理用於完成任務的資料或資訊，導致對使用者產生偏頗或非預期的回應。

**緩解：** 定期驗證 AI 代理在其工作流程中使用的資料。確保對該資料的存取是安全的，且只有受信任的人員可以更改，以避免此類攻擊。

### 連鎖錯誤

**描述：** AI 代理存取各種工具和服務以完成任務。攻擊者造成的錯誤可能導致 AI 代理所連接的其他系統失效，使攻擊擴散並更難排查。

**緩解：** 避免這種情況的一個方法是讓 AI 代理在受限環境中運行，例如在 Docker 容器中執行任務，以防止對系統的直接攻擊。當某些系統回傳錯誤時，建立備援機制和重試邏輯也是防止較大範圍系統失效的方式。

## 人類參與流程

另一個建立值得信賴 AI 代理系統的有效方法是採用人類參與流程（Human-in-the-loop）。這建立了一個流程，讓使用者能在執行過程中向代理提供回饋。使用者在多代理系統中本質上扮演代理的角色，透過提供核准或終止執行程序。

![人類參與流程](../../../translated_images/zh-HK/human-in-the-loop.5f0068a678f62f4f.webp)

下面是一個使用 AutoGen 的程式片段，示範如何實作此概念：

```python

# 建立代理人。
model_client = OpenAIChatCompletionClient(model="gpt-4o-mini")
assistant = AssistantAgent("assistant", model_client=model_client)
user_proxy = UserProxyAgent("user_proxy", input_func=input)  # 使用 input() 從控制台獲取用戶輸入。

# 建立結束條件，當使用者輸入「APPROVE」時結束對話。
termination = TextMentionTermination("APPROVE")

# 建立團隊。
team = RoundRobinGroupChat([assistant, user_proxy], termination_condition=termination)

# 執行對話並將其串流到控制台。
stream = team.run_stream(task="Write a 4-line poem about the ocean.")
# 在腳本中執行時使用 asyncio.run(...)。
await Console(stream)

```

## 結論

建立值得信賴的 AI 代理需要謹慎的設計、穩健的安全措施和持續反覆改進。透過實施結構化的元提示系統、理解潛在威脅並採取緩解策略，開發者可以建立既安全又有效的 AI 代理。此外，納入人類參與流程可確保 AI 代理與使用者需求保持一致，同時將風險降至最低。隨著 AI 持續演進，對安全、隱私和倫理議題採取積極作為，將是促進 AI 驅動系統信任與可靠性的關鍵。

### 對建立值得信賴的 AI 代理有更多問題？

加入 the [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) 以與其他學習者交流、參加辦公時間並獲得 AI 代理問題的解答。

## 附加資源

- <a href="https://learn.microsoft.com/azure/ai-studio/responsible-use-of-ai-overview" target="_blank">負責任 AI 概述</a>
- <a href="https://learn.microsoft.com/azure/ai-studio/concepts/evaluation-approach-gen-ai" target="_blank">生成式 AI 模型與 AI 應用的評估</a>
- <a href="https://learn.microsoft.com/azure/ai-services/openai/concepts/system-message?context=%2Fazure%2Fai-studio%2Fcontext%2Fcontext&tabs=top-techniques" target="_blank">安全系統訊息</a>
- <a href="https://blogs.microsoft.com/wp-content/uploads/prod/sites/5/2022/06/Microsoft-RAI-Impact-Assessment-Template.pdf?culture=en-us&country=us" target="_blank">風險評估範本</a>

## Previous Lesson

[Agentic RAG](../05-agentic-rag/README.md)

## Next Lesson

[Planning Design Pattern](../07-planning-design/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
免責聲明：
本文件已使用 AI 翻譯服務 Co-op Translator（https://github.com/Azure/co-op-translator）進行翻譯。雖然我們力求準確，但請注意，自動翻譯可能包含錯誤或不準確之處。原文應被視為權威來源。對於重要資訊，建議使用專業人工翻譯。我們不對因使用本翻譯而引致的任何誤解或誤釋承擔任何責任。
<!-- CO-OP TRANSLATOR DISCLAIMER END -->