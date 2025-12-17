# API 參考

LiteStartup REST API 的完整參考。所有請求都必須使用有效的 API 金鑰進行身分驗證。

## 基礎 URL

```
https://api.litestartup.com/client/v2
```

## 身分驗證

所有 API 請求都需要使用 Bearer Token 認證。

### Request Headers

```
Authorization: Bearer YOUR_API_KEY
```

### 驗證 API 金鑰

```bash
curl -X GET https://api.litestartup.com/client/v2/verify \
  -H "Authorization: Bearer sk_live_xxxxxxxxxxxxx"
```

## 回應格式

所有 API 回應皆以 JSON 格式回傳。

### 成功回應

```json
{
  "uuid": "xxxxxxxxxxxxx"
}
```

### 錯誤回應

```json
{
  "error": "Invalid API key"
}
```

## HTTP 狀態碼

| 代碼 | 意義 |
|------|---------|
| 200 | OK - 請求成功 |
| 201 | Created - 資源已建立 |
| 400 | Bad Request - 參數無效 |
| 401 | Unauthorized - API 金鑰無效或缺失 |
| 403 | Forbidden - 拒絕存取 |
| 404 | Not Found - 資源未找到 |
| 422 | Unprocessable Entity - 驗證失敗 |
| 429 | Too Many Requests - 超出速率限制 |
| 500 | Server Error - 內部伺服器錯誤 |

## 郵件 (Emails)

---
### 發送郵件

發送單封郵件或批次郵件。

**端點**: `POST /emails`

**Body 參數**

| 參數 | 類型 | 必填 | 說明 |
|------|------|------|------|
| to | string \| array | 是 | 收件人電子郵件地址 |
| from | string | 是 | 寄件人電子郵件地址 |
| subject | string | 是 | 郵件主旨 |
| html | string | 否 | HTML 郵件內容 |
| text | string | 否 | 純文字郵件內容 |
| replyTo | string | 否 | 回覆電子郵件地址 |
| cc | array | 否 | 副本收件人 |
| bcc | array | 否 | 密件副本收件人 |

**回應**

```json
{
  "messageId": "xxxxxxxxxxxxxxxx"
}
```

**範例**

```bash
curl -X POST https://api.litestartup.com/client/v2/emails \
     -H 'Authorization: Bearer sk_live_xxxxxxxxxxxxx' \
     -H 'Content-Type: application/json' \
     -d '{
  "to": "recipient@example.com",
  "from": "sender@yourdomain.com",
  "subject": "Welcome!",
  "html": "<h1>Hello</h1><p>Welcome to litestartup.</p>"
}'
```

### 取得已發送郵件狀態

取得已發送郵件的狀態與詳細資訊。

**端點**: `GET /emails/{email_id}`

**回應**

```json
{
  "success": true,
  "data": {
    "id": "email_1234567890",
    "to": "recipient@example.com",
    "from": "sender@yourdomain.com",
    "subject": "Welcome!",
    "status": "delivered",
    "created_at": "2024-01-15T10:00:00Z",
    "delivered_at": "2024-01-15T10:00:05Z",
    "opened_at": "2024-01-15T10:05:00Z",
    "clicked_at": "2024-01-15T10:06:00Z",
    "bounced": false,
    "spam_reported": false,
    "unsubscribed": false
  }
}
```

### 列出已發送郵件

取得已發送郵件清單，支援分頁與篩選。

**端點**: `GET /emails`

**查詢參數**

| 參數 | 類型 | 說明 |
|------|------|------|
| page | integer | 頁碼（預設：1） |
| limit | integer | 每頁筆數（預設：20，最大：100） |
| status | string | 依狀態篩選：queued, sent, delivered, bounced, failed |
| from | string | 依寄件人電子郵件篩選 |
| to | string | 依收件人電子郵件篩選 |
| tag | string | 依標籤篩選 |
| created_after | string | ISO 8601 時間戳記 |
| created_before | string | ISO 8601 時間戳記 |
| sort | string | 排序欄位：created_at, status |
| order | string | 排序順序：asc, desc |

**回應**

```json
{
  "success": true,
  "data": [
    {
      "id": "email_1234567890",
      "to": "recipient@example.com",
      "from": "sender@yourdomain.com",
      "subject": "Welcome!",
      "status": "delivered",
      "created_at": "2024-01-15T10:00:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 150,
    "pages": 8
  }
}
```

**範例**

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```


## 範本 (Templates)

---
### 建立範本

建立可重複使用的郵件範本。

**端點**: `POST /templates`

**請求 Body**

```json
{
  "name": "Welcome Email",
  "subject": "Welcome to {{company_name}}!",
  "html": "<h1>Hello {{name}}</h1><p>Welcome aboard!</p>",
  "text": "Hello {{name}}\n\nWelcome aboard!",
  "variables": ["name", "company_name"],
  "description": "Welcome email for new users"
}
```

**回應**

```json
{
  "success": true,
  "data": {
    "id": "tmpl_1234567890",
    "name": "Welcome Email",
    "created_at": "2024-01-15T10:00:00Z"
  }
}
```

### 取得範本

依 ID 取得範本。

**端點**: `GET /templates/{template_id}`

**回應**

```json
{
  "success": true,
  "data": {
    "id": "tmpl_1234567890",
    "name": "Welcome Email",
    "subject": "Welcome to {{company_name}}!",
    "html": "<h1>Hello {{name}}</h1>",
    "text": "Hello {{name}}",
    "variables": ["name", "company_name"],
    "created_at": "2024-01-15T10:00:00Z"
  }
}
```

### 列出範本

**端點**: `GET /templates`

**回應**

```json
{
  "success": true,
  "data": [
    {
      "id": "tmpl_1234567890",
      "name": "Welcome Email",
      "created_at": "2024-01-15T10:00:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 5
  }
}
```

### 更新範本

**端點**: `PUT /templates/{template_id}`

**請求 Body**

```json
{
  "name": "Welcome Email v2",
  "subject": "Welcome!",
  "html": "<h1>Hello {{name}}</h1>"
}
```

### 刪除範本

**端點**: `DELETE /templates/{template_id}`

**回應**

```json
{
  "success": true,
  "message": "Template deleted"
}
```

### 聯絡人 (Contacts)

#### 新增聯絡人

將聯絡人新增到您的訂閱名單。

**端點**: `POST /contacts`

**請求 Body**

```json
{
  "email": "user@example.com",
  "name": "John Doe",
  "attributes": {
    "company": "Acme Inc",
    "plan": "pro",
    "signup_date": "2024-01-15"
  },
  "tags": ["customer", "vip"],
  "subscribed": true
}
```

**回應**

```json
{
  "success": true,
  "data": {
    "id": "contact_1234567890",
    "email": "user@example.com",
    "name": "John Doe",
    "created_at": "2024-01-15T10:00:00Z"
  }
}
```

#### 取得聯絡人

**端點**: `GET /contacts/{contact_id}`

#### 列出聯絡人

**端點**: `GET /contacts`

**查詢參數**

| 參數 | 類型 | 說明 |
|------|------|------|
| page | integer | 頁碼 |
| limit | integer | 每頁筆數 |
| tag | string | 依標籤篩選 |
| subscribed | boolean | 依訂閱狀態篩選 |
| search | string | 依電子郵件或姓名搜尋 |

#### 更新聯絡人

**端點**: `PUT /contacts/{contact_id}`

#### 刪除聯絡人

**端點**: `DELETE /contacts/{contact_id}`

### 行銷活動 (Campaigns)

#### 建立行銷活動

**端點**: `POST /campaigns`

**請求 Body**

```json
{
  "name": "Q1 Newsletter",
  "subject": "January Newsletter",
  "html": "<h1>Newsletter</h1>",
  "text": "Newsletter",
  "from": "newsletter@yourdomain.com",
  "recipient_list": "all_subscribers",
  "scheduled_at": "2024-01-20T09:00:00Z"
}
```

#### 取得行銷活動

**端點**: `GET /campaigns/{campaign_id}`

#### 列出行銷活動

**端點**: `GET /campaigns`

#### 更新行銷活動

**端點**: `PUT /campaigns/{campaign_id}`

#### 發送行銷活動

**端點**: `POST /campaigns/{campaign_id}/send`

#### 取得行銷活動統計

**端點**: `GET /campaigns/{campaign_id}/stats`

**回應**

```json
{
  "success": true,
  "data": {
    "id": "campaign_1234567890",
    "name": "Q1 Newsletter",
    "sent": 1000,
    "delivered": 995,
    "bounced": 5,
    "opened": 450,
    "clicked": 120,
    "unsubscribed": 10,
    "spam_reported": 2,
    "open_rate": 45.2,
    "click_rate": 12.0
  }
}
```

### Webhooks

#### 建立 Webhook

訂閱郵件事件。

**端點**: `POST /webhooks`

**請求 Body**

```json
{
  "url": "https://yourdomain.com/webhooks/litestartup",
  "events": ["email.sent", "email.delivered", "email.opened", "email.clicked", "email.bounced"],
  "active": true
}
```

**事件**

- `email.sent` - 郵件已排隊發送
- `email.delivered` - 郵件已成功投遞
- `email.opened` - 郵件已被收件人打開
- `email.clicked` - 郵件中的連結已被點擊
- `email.bounced` - 郵件被退回
- `email.spam_reported` - 郵件被標記為垃圾郵件
- `email.unsubscribed` - 收件人已退訂

#### Webhook Payload

```json
{
  "event": "email.delivered",
  "timestamp": "2024-01-15T10:00:05Z",
  "data": {
    "email_id": "email_1234567890",
    "to": "recipient@example.com",
    "from": "sender@yourdomain.com",
    "subject": "Welcome!",
    "status": "delivered",
    "delivered_at": "2024-01-15T10:00:05Z"
  }
}
```

#### 列出 Webhooks

**端點**: `GET /webhooks`

#### 更新 Webhook

**端點**: `PUT /webhooks/{webhook_id}`

#### 刪除 Webhook

**端點**: `DELETE /webhooks/{webhook_id}`

## 速率限制 (Rate Limiting)

API 請求會依您的方案進行速率限制：

| 方案 | 請求/分鐘 | 請求/小時 |
|------|-----------------|---------------|
| 免費 | 60 | 1,000 |
| 專業 | 300 | 10,000 |

當觸發速率限制時，API 會回傳 429 狀態碼與 `Retry-After` Header。

```
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

## 錯誤代碼

| 代碼 | 消息 | 描述 |
|------|---------|-------------|
| INVALID_EMAIL | Invalid email address | 電子郵件格式無效 |
| INVALID_API_KEY | Invalid API key | API 金鑰遺失或無效 |
| DOMAIN_NOT_VERIFIED | Domain not verified | 寄件者網域未驗證 |
| RATE_LIMIT_EXCEEDED | Rate limit exceeded | 請求過多 |
| INVALID_TEMPLATE | Invalid template | 範本未找到或無效 |
| CONTACT_NOT_FOUND | Contact not found | 聯絡人 ID 未找到 |
| CAMPAIGN_NOT_FOUND | Campaign not found | 行銷活動 ID 未找到 |
| INSUFFICIENT_QUOTA | Insufficient quota | 超出每月郵件配額 |

## 最佳實務

### 安全

- ✓ 將 API 金鑰儲存在環境變數中
- ✓ 所有請求都使用 HTTPS
- ✓ 定期輪換 API 金鑰
- ✓ 切勿將 API 金鑰提交到版本控制

### 效能

- ✓ 可行時，於單一請求中批次發送多封郵件
- ✓ 重試時實作指數退避
- ✓ 在本機快取範本資料
- ✓ 大型結果集請使用分頁

### 可靠性

- ✓ 為所有請求實作錯誤處理
- ✓ 記錄所有 API 呼叫以便除錯
- ✓ 監控 Webhook 投遞
- ✓ 為關鍵操作實作冪等性

## 分頁

列表端點支援使用 `page` 與 `limit` 參數進行分頁。

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?page=2&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

回應包含分頁中繼資料：

```json
{
  "pagination": {
    "page": 2,
    "limit": 50,
    "total": 500,
    "pages": 10
  }
}
```

## 篩選與排序

列表端點支援篩選與排序：

```bash
# 依狀態篩選
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered" \
  -H "Authorization: Bearer YOUR_API_KEY"

# 依日期排序
curl -X GET "https://api.litestartup.com/client/v2/emails?sort=created_at&order=desc" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

**下一步：** 查看 [功能指南](/zh-tw/03-features.md) 或 [程式碼範例](/zh-tw/04-examples.md)！
