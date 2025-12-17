# LiteStartup 簡介
 
 LiteStartup（官網定位：*Lite Email for Startups*）是一套面向創業團隊的 **AI 驅動郵件服務平台**，把 *Workmail（企業信箱）*、*Transactional Email（交易郵件）*、*Marketing Email（行銷郵件）* 等能力整合在同一個產品裡，並提供可直接呼叫的 REST API，幫助你用更低成本、更少設定完成郵件發送與成長觸達。
 
 ## LiteStartup 是什麼？
 
 LiteStartup 是一款 SaaS 郵件平台，核心定義可以概括為：
 
 - **用 AI 改造郵件工作流程的郵件服務模型**：從內容生成到自動化觸達，盡可能減少人工操作
 - **同時涵蓋「企業信箱 + 行銷郵件 + 交易郵件」**：減少多供應商拼裝
 - **面向開發者的簡單整合**：無需複雜 SDK，透過標準 RESTful API 快速接入
 
 與傳統按聯絡人計費的郵件平台不同，LiteStartup 主打 **按實際發送量計費（pay per email sent）**，而不是按聯絡人數量收費。
 
 ## 核心特性（What Makes Us Different）
 
 ### Workmail Like Gmail（企業信箱）
 可在幾分鐘內開通類似 `support@yourcompany.com` 的企業信箱能力，減少額外採購與設定成本。
 
 ### AI Content Assistant（AI 內容助手）
 AI 生成行銷郵件內容，並提供 A/B 測試變體；從想法到發送可以更快完成。
 
 ### Affordable（按發送計費，更輕量）
 - **按郵件發送量計費**：不是按聯絡人計費
 - **超額費用**：$0.20 / 1,000 emails（超過方案額度後）
 - **範例方案**：Pro 為 $20/月，包含 110,000 emails/月
 
 ### Enterprise Infrastructure（企業級基礎設施）
 官網描述為由 AWS 與 Google Cloud 工程師建構，提供較高可用與合規能力（SOC2 & GDPR）。
 
 ### Free Email Notifications（免費通知郵箱）
 提供類似 `yourname@litestartup.net` 的通知郵箱，用於警示、報表、更新等，減少通知系統建置成本。
 
 ### AI Website Builder（AI 建站／落地頁）
 透過與 AI 對話快速生成高轉化落地頁／Waitlist 頁／Newsletter／Blog 等，無需寫程式。
 
 ### Ticket + Live Chat（工單與線上客服）
 - Ticket：用郵件高效管理客戶工單
 - Live Chat：網站即時聊天元件，提升線索轉化
 
 ### AI Automation（AI 自動化成長）
 AI 自動發送歡迎、跟進與外呼郵件，並結合線索捕獲等能力，形成「常開」的成長自動化。
 
 ## 誰適合使用 LiteStartup？
 
 LiteStartup 更適合以下族群／團隊：
 
 - **早期創業團隊**：需要快速搭建企業信箱、行銷觸達與通知郵件
 - **SaaS 產品**：同時需要交易郵件與行銷郵件，並希望用統一平台管理
 - **成長／行銷團隊**：希望用 AI 提升郵件內容產出效率與實驗速度
 - **產品團隊**：需要 Waitlist、落地頁、早期存取邀請等能力
 - **開發者**：偏好標準 REST API、輕量接入、減少 SDK 依賴
 - **希望避免供應商鎖定的團隊**：更易遷移與替換郵件服務
 
 ## LiteStartup 如何運作
 
 ### 1. 註冊
 建立帳戶即可開始使用（免費方案包含每月 10,000 emails）。
 
 ### 2. 取得 API 憑證
 在控制台取得 API Key。
 
 ### 3. 整合
 透過 RESTful API 呼叫發送郵件，適用於任何語言／框架。
 
 ### 4. 發送郵件
 發送交易郵件、行銷郵件或觸發自動化工作流程。
 
 ### 5. 追蹤與優化
 查看基礎分析資料，並結合 AI 能力持續迭代郵件內容與轉化表現。
 
 ## LiteStartup vs 傳統郵件平台
 
 |特性|LiteStartup|傳統郵件平台|
 |------|------------|--------------|
 |Workmail（企業信箱）|✓ Included|✗ Separate service|
 |AI Content Assistant|✓ Yes|✗ No|
 |計費模型|Per email sent|Per contact|
 |接入／設定|5 minutes|30+ minutes|
 |API 整合|✓ Simple REST API|✓ Complex SDKs|
 |供應商鎖定|✗ None|✓ Yes|
 |免費額度|10K emails/month|Limited|
 |可用性（官網描述）|99.9%|99.9%|
 
 ## 開始使用
 
 準備開始發送郵件？你可以從下面幾步開始：
 
 1. **[快速入門指南](/zh-tw/01-getting-started.md)** - 註冊並在 5 分鐘內發送你的第一封郵件
 2. **[API 文件](/zh-tw/02-api-reference.md)** - 完整的 API 文件與端點
 3. **[功能指南](/zh-tw/03-features.md)** - 詳細探索所有功能
 4. **[程式碼範例](/zh-tw/04-examples.md)** - 多種語言的實作範例
 5. **[定價與方案](/zh-tw/05-pricing.md)** - 了解定價與計費
 
 ## 快速呼叫範例
 
 用幾行程式碼發送你的第一封郵件：
 
 ```bash
 curl -X POST https://api.litestartup.com/client/v2/emails \
   -H "Authorization: Bearer YOUR_API_KEY" \
   -H "Content-Type: application/json" \
   -d '{
     "to": "user@example.com",
     "from": "noreply@yourapp.com",
     "subject": "Welcome!",
     "html": "<h1>Hello</h1>"
   }'
 ```
 
 ## 關鍵價值
 
 - **成本更可控**：按郵件發送量計費，而不是按聯絡人計費
 - **生產力更高**：AI 內容助手與 AI 自動化減少人工操作
 - **一體化工具**：Workmail + 郵件發送 + 落地頁／Waitlist + Ticket／Live Chat
 - **輕量整合**：REST API，無複雜 SDK 與依賴
 - **更少鎖定**：標準 API 設計，遷移與替換成本更低
 
 ## 支援與資源
 
 - **文件**：完整的指南與 API 參考
 
 - **程式碼範例**：多種語言的即用型範例
 
 - **社群**：與其他 LiteStartup 使用者交流
 
 ## 下一步
 
 - 閱讀[入門指南](/zh-tw/01-getting-started.md)
 
 - 瀏覽[API 參考](/zh-tw/02-api-reference.md)
 
 - 查看[程式碼範例](/zh-tw/04-examples.md)，找到適合你程式語言的範例
 
 - 查看[定價與方案](/zh-tw/05-pricing.md)，選擇合適的方案
---
 
 **準備發送你的第一封郵件？** 從 [快速入門指南](/zh-tw/01-getting-started.md) 開始。
