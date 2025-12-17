# 功能指南

探索 LiteStartup 提供的所有強大功能，協助您的新創團隊取得成功。

## Workmail - 企業信箱

LiteStartup 內建了企業信箱功能，無需再使用 Google Workspace 等獨立的郵件服務。

### 什麼是 Workmail？

Workmail 是一項直接整合到 LiteStartup 的全功能企業信箱服務。您可以直接使用自訂網域收發郵件，無需額外訂閱其他服務。

### 優勢

- **省錢**：每位團隊成員每年可節省 72-144 美元（相較於 Google Workspace）
- **統一平台**：郵件與行銷合而為一
- **專業形象**：使用您的自訂網域
- **功能齊全**：轉寄、別名、自動回覆

### 開始使用 Workmail

1. 前往 **Settings**（設定） → **Workmail**
2. 新增您的網域（例如，`hello@yourdomain.com`）
3. 驗證 DNS 紀錄
4. 為團隊成員建立信箱帳戶
5. 開始收發郵件

### 建立信箱帳戶

```
1. 點擊 "Add Email Account"（新增信箱帳戶）
2. 輸入使用者名稱（例如，"john"）
3. 設定密碼
4. 指派給團隊成員
5. 點擊 "Create"（建立）
```

信箱地址將會是：`john@yourdomain.com`

### 郵件轉寄

設定自動轉寄：

```
1. 前往信箱帳戶設定
2. 點擊 "Forwarding"（轉寄）
3. 輸入轉寄地址
4. 確認轉寄
5. 郵件將會自動轉寄
```

### 自動回覆

設定自動回覆：

```
1. 前往信箱帳戶設定
2. 點擊 "Auto-Responder"（自動回覆）
3. 啟用自動回覆
4. 設定訊息與日期範圍
5. 儲存
```

## AI 內容助手

LiteStartup 的 AI 內容助手可協助您更快寫出更好的郵件。

### 功能

- **生成主旨行**：AI 建議最佳化的主旨行
- **郵件內文**：生成郵件內文內容
- **A/B 測試**：建立用於測試的變體
- **語氣調整**：匹配您的品牌語調
- **最佳化**：提供提升開啟率的建議

### 使用 AI 助手

#### 生成主旨行

```
1. 在郵件編輯器中點擊 "AI Assistant"（AI 助手）
2. 選擇 "Generate Subject Lines"（生成主旨行）
3. 描述您的郵件目的
4. AI 生成 5 個變體
5. 點擊使用或重新生成
```

範例：
- 輸入："Welcome email for new users"（新用戶歡迎郵件）
- AI 建議：
  - "Welcome! Get started in 3 minutes"（歡迎！3 分鐘內開始使用）
  - "You're in! Here's what's next"（你已加入！接下來做什麼）
  - "Welcome aboard - your journey starts now"（歡迎加入 - 你的旅程現在開始）

#### 生成郵件內文

```
1. 點擊 "AI Assistant"
2. 選擇 "Generate Email Body"（生成郵件內文）
3. 提供關鍵重點
4. 選擇語氣（專業、友善、隨性）
5. AI 生成郵件內容
6. 視需要進行編輯與自訂
```

#### A/B 測試變體

```
1. 點擊 "AI Assistant"
2. 選擇 "Create A/B Variations"（建立 A/B 變體）
3. AI 生成替代版本
4. 選擇要測試的版本
5. LiteStartup 追蹤表現
```

### AI 寫作技巧

- ✓ 明確您的目標
- ✓ 提及您的目標受眾
- ✓ 指定期望的語氣
- ✓ 提供需要包含的關鍵資訊
- ✓ 檢視並自訂 AI 的建議

## 自動化與工作流

建立智慧工作流，根據使用者行為自動寄送郵件。

### 工作流類型

#### 歡迎系列

向新訂閱者自動寄送一系列郵件。

```
1. 前往 Automation（自動化） → Workflows（工作流）
2. 點擊 "Create Workflow"（建立工作流）
3. 選擇 "Welcome Series"（歡迎系列）
4. 新增郵件（1-5 封郵件）
5. 設定郵件之間的延遲
6. 啟用工作流
```

歡迎系列範例：
- 郵件 1：歡迎（立即寄送）
- 郵件 2：快速開始（1 天後）
- 郵件 3：功能亮點（3 天後）
- 郵件 4：成功案例（7 天後）

#### 重新互動行銷

喚回不活躍的訂閱者。

```
1. 建立工作流
2. 選擇 "Re-engagement"（重新互動）
3. 設定不活躍門檻（例如，30 天）
4. 新增重新互動郵件
5. 設定後續動作
6. 啟用
```

#### 喚回行銷

針對近期未購買的客戶。

```
1. 建立工作流
2. 選擇 "Win-back"（喚回）
3. 定義不活躍期間
4. 建立有吸引力的優惠
5. 設定重試計畫
6. 啟用
```

#### 棄購喚回

提醒客戶購物車中遺留的商品。

```
1. 建立工作流
2. 選擇 "Abandoned Cart"（棄購喚回）
3. 設定延遲（例如，1 小時）
4. 自訂包含產品詳情的郵件
5. 新增後續郵件
6. 啟用
```

### 工作流觸發器

工作流可以透過以下方式觸發：

- **使用者動作**：註冊、購買、下載
- **時間條件**：特定日期/時間、紀念日
- **行為**：開啟、點擊、不活躍
- **自訂**：API 觸發器、Webhooks

### 工作流條件

新增條件以控制工作流走向：

```
IF user.plan == "pro" THEN send_email("pro_features")
IF user.location == "US" THEN send_email("us_offer")
IF user.opened_count > 5 THEN send_email("vip_offer")
```

### 工作流分析

監控工作流表現：

- 寄送的郵件數
- 投遞率
- 開啟率
- 點擊率
- 轉換率
- 產生的收入

## 訂閱表單

使用可嵌入的註冊表單建立您的訂閱者名單。

### 建立訂閱表單

```
1. 前往 Forms（表單） → Create Form（建立表單）
2. 選擇表單類型：
   - 簡單註冊
   - 雙重確認 (Double opt-in)
   - 自訂欄位
3. 設計表單
4. 新增欄位（信箱、姓名、自訂欄位）
5. 設定確認訊息
6. 取得嵌入程式碼
```

### 表單類型

#### 簡單註冊

用於快速註冊的單步表單。

```html
<iframe src="https://forms.litestartup.com/simple/form_id"></iframe>
```

#### 雙重確認 (Double Opt-in)

用於合規的兩步確認。

```
1. 使用者輸入信箱
2. 寄送確認郵件
3. 使用者點擊確認連結
4. 訂閱完成確認
```

#### 自訂欄位

蒐集額外資訊：

```
- 信箱（必填）
- 姓名（選填）
- 公司（選填）
- 方案意向（下拉選單）
- 預算（多選）
```

### 表單自訂

- **顏色**：匹配您的品牌
- **文字**：自訂標籤與訊息
- **欄位**：新增/移除欄位
- **重新導向**：註冊後重新導向
- **Webhook**：將資料送到您的系統

### 嵌入表單

#### 在網站上

```html
<div id="litestartup-form"></div>
<script>
  LiteStartup.loadForm('form_id', {
    container: '#litestartup-form',
    onSuccess: function() {
      console.log('User subscribed!');
    }
  });
</script>
```

#### 在著陸頁上

```html
<!-- 直接嵌入 -->
<iframe src="https://forms.litestartup.com/form_id" 
         width="100%" height="500"></iframe>
```

#### 彈出式表單

```javascript
LiteStartup.showPopup('form_id', {
  trigger: 'exit', // 在離開意圖時顯示
  delay: 5000,     // 5 秒後顯示
  frequency: 'once' // 每個工作階段顯示一次
});
```

## 等候名單管理

在上線前透過等候名單管理建立熱度。

### 建立等候名單

```
1. 前往 Waitlist（等候名單） → Create Waitlist（建立等候名單）
2. 命名您的等候名單
3. 設定上線日期
4. 自訂註冊頁面
5. 產生註冊連結
6. 分享給受眾
```

### 等候名單功能

- **推薦追蹤**：使用者透過推薦朋友取得名次
- **邀請碼**：寄送個人化邀請碼
- **排名**：顯示使用者在等候名單中的位置
- **郵件通知**：受邀時通知
- **分析**：追蹤註冊來源

### 推薦計畫

允許使用者透過推薦朋友取得早期存取權限：

```
1. 在等候名單設定中啟用推薦
2. 使用者取得唯一的推薦連結
3. 每次成功推薦 = +1 個名次
4. 排行榜顯示頂級推薦人
5. 優先向頂級推薦人寄送邀請
```

### 寄送邀請

```
1. 前往 Waitlist（等候名單） → Manage（管理）
2. 選擇要邀請的使用者
3. 產生邀請碼
4. 寄送邀請郵件
5. 追蹤接受狀況
```

### 等候名單分析

監控等候名單成長：

- 總註冊數
- 推薦註冊數
- 轉換率
- 頂級推薦人
- 註冊來源
- 地理分布

## 郵件範本

建立並管理可重複使用的郵件範本。

### 範本庫

存取預先建立的範本：

- 歡迎郵件
- 促銷郵件
- 交易郵件
- 電子報範本
- 活動邀請
- 密碼重設

### 建立自訂範本

```
1. 前往 Templates（範本） → Create（建立）
2. 選擇版面配置
3. 新增內容區塊
4. 插入變數 ({{name}}, {{company}})
5. 預覽
6. 儲存範本
```

### 範本變數

在範本中使用動態變數：

```
Hello {{first_name}},

Welcome to {{company_name}}!

Your account: {{email}}
Plan: {{plan_type}}

Best regards,
The {{company_name}} Team
```

### 範本測試

在寄送前測試範本：

```
1. 點擊 "Send Test"（寄送測試）
2. 輸入測試信箱
3. 檢視郵件
4. 進行調整
5. 寄送給名單
```

## 聯絡人管理

組織並管理您的訂閱者名單。

### 匯入聯絡人

#### CSV 匯入

```
1. 前往 Contacts（聯絡人） → Import（匯入）
2. 上傳 CSV 檔案
3. 將欄位對應到欄位名稱
4. 檢視預覽
5. 匯入
```

CSV 格式：
```
email,first_name,last_name,company,plan
john@example.com,John,Doe,Acme Inc,pro
jane@example.com,Jane,Smith,Tech Corp,free
```

#### API 匯入

```php
$contacts = [
    ['email' => 'john@example.com', 'name' => 'John'],
    ['email' => 'jane@example.com', 'name' => 'Jane']
];

foreach ($contacts as $contact) {
    $response = $client->post('/contacts', [
        'email' => $contact['email'],
        'name' => $contact['name']
    ]);
}
```

### 組織聯絡人
#### 標籤 (Tags)

使用標籤組織聯絡人：

```
- "vip"
- "trial_user"（試用使用者）
- "paying_customer"（付費客戶）
- "inactive"（不活躍）
- "churned"（流失）
```

#### 分群 (Segments)

建立動態分群：

```
- 活躍使用者（過去 30 天內打開過郵件）
- 高價值客戶（消費 > $1000）
- 試用使用者（註冊 < 14 天前）
- 不活躍（無活動 > 60 天）
```

### 聯絡人資料

儲存自訂屬性：

```
- 公司
- 職位
- 行業
- 地點
- 計劃類型
- 註冊日期
- 最後購買
- 生命週期價值
```

## 分析與報告

使用詳細的分析追蹤郵件表現。

### 郵件指標

- **Sent**：寄送總數
- **Delivered**：成功投遞
- **Bounced**：硬/軟退信
- **Opened**：獨立開啟
- **Clicked**：獨立點擊
- **Unsubscribed**：退訂請求
- **Spam**：垃圾郵件投訴

### 行銷活動分析

```
Campaign: Q1 Newsletter
├── Sent: 10,000
├── Delivered: 9,950 (99.5%)
├── Bounced: 50 (0.5%)
├── Opened: 4,500 (45.2%)
├── Clicked: 1,200 (12.0%)
├── Unsubscribed: 50 (0.5%)
└── Conversion: 150 (1.5%)
```

### 參與度追蹤

追蹤單一使用者的參與度：

- 郵件開啟
- 連結點擊
- 購買歷史
- 參與度評分
- 最後活動日期

### 自訂報告

建立自訂報告：

```
1. 前往 Reports（報告） → Create（建立）
2. 選擇指標
3. 選擇日期範圍
4. 新增篩選條件
5. 產生報告
6. 匯出為 PDF/CSV
```

## 合規性與送達率

### GDPR 合規性

- ✓ 同意管理
- ✓ 資料匯出
- ✓ 被遺忘權
- ✓ 隱私權政策範本
- ✓ 稽核日誌

### CAN-SPAM 合規性

- ✓ 清楚的退訂選項
- ✓ 準確的寄件者資訊
- ✓ 誠實的主旨行
- ✓ 必須提供實體地址
- ✓ 10 天內處理退訂

### 送達率功能

- ✓ SPF/DKIM/DMARC 設定
- ✓ 網域驗證
- ✓ 退信管理
- ✓ 垃圾郵件測試
- ✓ IP 聲譽監控

## 整合

### Webhook 事件

接收即時通知：

- 郵件已寄送
- 郵件已投遞
- 郵件已開啟
- 連結已被點擊
- 郵件已退回
- 已退訂

### API 整合

與您的應用程式整合：

```php
// Send email via API
$response = $client->post('/emails/send', [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
]);
```

### 第三方整合

連接常用工具：

- Zapier
- Make (Integromat)
- IFTTT
- Slack
- Discord
- 自訂 Webhooks

---

**下一步：** 查看 [程式碼範例](/zh-tw/04-examples.md) 或 [價格方案](/zh-tw/05-pricing.md)！
