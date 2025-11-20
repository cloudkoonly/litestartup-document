# API 参考

LiteStartup REST API 的完整参考。所有请求都必须使用有效的 API 密钥进行身份验证。

## 基础 URL

```
https://api.litestartup.com/client/v2
```

## 身份验证

所有 API 请求都需要使用 Bearer 令牌认证。

### 请求头

```
Authorization: Bearer YOUR_API_KEY
```

### 验证 API 密钥

```bash
curl -X GET https://api.litestartup.com/client/v2/verify \
  -H "Authorization: Bearer sk_live_xxxxxxxxxxxxx"
```

## 响应格式

所有 API 响应均以 JSON 格式返回。

### 成功响应

```json
{
  "uuid": "xxxxxxxxxxxxx"
}
```

### 错误响应

```json
{
  "error": "Invalid API key"
}
```

## HTTP 状态码

| 代码 | 含义 |
|------|---------|
| 200 | OK - 请求成功 |
| 201 | Created - 资源已创建 |
| 400 | Bad Request - 参数无效 |
| 401 | Unauthorized - API 密钥无效或缺失 |
| 403 | Forbidden - 拒绝访问 |
| 404 | Not Found - 资源未找到 |
| 422 | Unprocessable Entity - 验证失败 |
| 429 | Too Many Requests - 超出速率限制 |
| 500 | Server Error - 内部服务器错误 |

## 邮件 (Emails)

---
### 发送邮件

发送单封邮件或批量邮件。

**端点**: `POST /emails`

**Body 参数**

| 参数 | 类型 | 必填 | 描述 |
|------|------|------|------|
| to | string \| array | 是 | 收件人邮箱地址 |
| from | string | 是 | 发件人邮箱地址 |
| subject | string | 是 | 邮件主题行 |
| html | string | 否 | HTML 邮件正文 |
| text | string | 否 | 纯文本邮件正文 |
| replyTo | string | 否 | 回复邮箱地址 |
| cc | array | 否 | 抄送收件人 |
| bcc | array | 否 | 密送收件人 |

**响应**

```json
{
  "messageId": "xxxxxxxxxxxxxxxx"
}
```

**示例**

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

### 获取已发送邮件状态

检索已发送邮件的状态和详细信息。

**端点**: `GET /emails/{email_id}`

**响应**

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

### 列出已发送邮件

检索已发送邮件的列表，支持分页和过滤。

**端点**: `GET /emails`

**查询参数**

| 参数 | 类型 | 描述 |
|------|------|------|
| page | integer | 页码 (默认: 1) |
| limit | integer | 每页结果数 (默认: 20, 最大: 100) |
| status | string | 按状态过滤: queued, sent, delivered, bounced, failed |
| from | string | 按发件人邮箱过滤 |
| to | string | 按收件人邮箱过滤 |
| tag | string | 按标签过滤 |
| created_after | string | ISO 8601 时间戳 |
| created_before | string | ISO 8601 时间戳 |
| sort | string | 排序字段: created_at, status |
| order | string | 排序顺序: asc, desc |

**响应**

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

**示例**

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```


## 模板 (Templates)

---
### 创建模板

创建一个可复用的邮件模板。

**端点**: `POST /templates`

**请求 Body**

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

**响应**

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

### 获取模板

通过 ID 检索模板。

**端点**: `GET /templates/{template_id}`

**响应**

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

### 列出模板

**端点**: `GET /templates`

**响应**

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

### 更新模板

**端点**: `PUT /templates/{template_id}`

**请求 Body**

```json
{
  "name": "Welcome Email v2",
  "subject": "Welcome!",
  "html": "<h1>Hello {{name}}</h1>"
}
```

### 删除模板

**端点**: `DELETE /templates/{template_id}`

**响应**

```json
{
  "success": true,
  "message": "Template deleted"
}
```

### 联系人 (Contacts)

#### 添加联系人

添加一个联系人到您的订阅列表。

**端点**: `POST /contacts`

**请求 Body**

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

**响应**

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

#### 获取联系人

**端点**: `GET /contacts/{contact_id}`

#### 列出联系人

**端点**: `GET /contacts`

**查询参数**

| 参数 | 类型 | 描述 |
|------|------|------|
| page | integer | 页码 |
| limit | integer | 每页结果数 |
| tag | string | 按标签过滤 |
| subscribed | boolean | 按订阅状态过滤 |
| search | string | 按邮箱或姓名搜索 |

#### 更新联系人

**端点**: `PUT /contacts/{contact_id}`

#### 删除联系人

**端点**: `DELETE /contacts/{contact_id}`

### 营销活动 (Campaigns)

#### 创建营销活动

**端点**: `POST /campaigns`

**请求 Body**

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

#### 获取营销活动

**端点**: `GET /campaigns/{campaign_id}`

#### 列出营销活动

**端点**: `GET /campaigns`

#### 更新营销活动

**端点**: `PUT /campaigns/{campaign_id}`

#### 发送营销活动

**端点**: `POST /campaigns/{campaign_id}/send`

#### 获取营销活动统计

**端点**: `GET /campaigns/{campaign_id}/stats`

**响应**

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

#### 创建 Webhook

订阅邮件事件。

**端点**: `POST /webhooks`

**请求 Body**

```json
{
  "url": "https://yourdomain.com/webhooks/litestartup",
  "events": ["email.sent", "email.delivered", "email.opened", "email.clicked", "email.bounced"],
  "active": true
}
```

**事件**

- `email.sent` - 邮件已排队发送
- `email.delivered` - 邮件已成功投递
- `email.opened` - 邮件已被收件人打开
- `email.clicked` - 邮件中的链接已被点击
- `email.bounced` - 邮件被退回
- `email.spam_reported` - 邮件被标记为垃圾邮件
- `email.unsubscribed` - 收件人已退订

#### Webhook 载荷

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

**端点**: `GET /webhooks`

#### 更新 Webhook

**端点**: `PUT /webhooks/{webhook_id}`

#### 删除 Webhook

**端点**: `DELETE /webhooks/{webhook_id}`

## 速率限制 (Rate Limiting)

API 请求根据您的计划进行速率限制：

| 计划 | 请求/分钟 | 请求/小时 |
|------|-----------------|---------------|
| 免费 | 60 | 1,000 |
| 专业 | 300 | 10,000 |

当受到速率限制时，API 返回 429 状态码和 `Retry-After` 头。

```
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

## 错误代码

| 代码 | 消息 | 描述 |
|------|---------|-------------|
| INVALID_EMAIL | Invalid email address | 邮箱格式无效 |
| INVALID_API_KEY | Invalid API key | API 密钥丢失或无效 |
| DOMAIN_NOT_VERIFIED | Domain not verified | 发件人域名未验证 |
| RATE_LIMIT_EXCEEDED | Rate limit exceeded | 请求过多 |
| INVALID_TEMPLATE | Invalid template | 模板未找到或无效 |
| CONTACT_NOT_FOUND | Contact not found | 联系人 ID 未找到 |
| CAMPAIGN_NOT_FOUND | Campaign not found | 营销活动 ID 未找到 |
| INSUFFICIENT_QUOTA | Insufficient quota | 超出每月邮件配额 |

## 最佳实践

### 安全

- ✓ 将 API 密钥存储在环境变量中
- ✓ 对所有请求使用 HTTPS
- ✓ 定期轮换 API 密钥
- ✓ 切勿将 API 密钥提交到版本控制

### 性能

- ✓ 可能的话，在单个请求中批量发送多封邮件
- ✓ 为重试实施指数退避
- ✓ 本地缓存模板数据
- ✓ 为大型结果集使用分页

### 可靠性

- ✓ 为所有请求实施错误处理
- ✓ 记录所有 API 调用以进行调试
- ✓ 监控 webhook 投递
- ✓ 为关键操作实施幂等性

## 分页

列表端点支持使用 `page` 和 `limit` 参数进行分页。

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?page=2&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

响应包含分页元数据：

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

## 过滤和排序

列表端点支持过滤和排序：

```bash
# 按状态过滤
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered" \
  -H "Authorization: Bearer YOUR_API_KEY"

# 按日期排序
curl -X GET "https://api.litestartup.com/client/v2/emails?sort=created_at&order=desc" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

**下一步：** 查看 [功能指南](03-features.md) 或 [代码示例](04-examples.md)！
