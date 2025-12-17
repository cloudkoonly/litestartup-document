# API リファレンス

LiteStartup REST API の完全なリファレンスです。すべてのリクエストは、有効な API key で認証する必要があります。

## Base URL

```
https://api.litestartup.com/client/v2
```

## 認証

すべての API リクエストは Bearer トークン認証が必要です。

### リクエストヘッダー

```
Authorization: Bearer YOUR_API_KEY
```

### API key の検証

```bash
curl -X GET https://api.litestartup.com/client/v2/verify \
  -H "Authorization: Bearer sk_live_xxxxxxxxxxxxx"
```

## レスポンス形式

すべての API レスポンスは JSON 形式で返されます。

### 成功時レスポンス

```json
{
  "uuid": "xxxxxxxxxxxxx"
}
```

### エラー時レスポンス

```json
{
  "error": "Invalid API key"
}
```

## HTTP ステータスコード

| コード | 意味 |
|------|---------|
| 200 | OK - リクエスト成功 |
| 201 | Created - リソース作成 |
| 400 | Bad Request - パラメータ不正 |
| 401 | Unauthorized - API key が不正または未指定 |
| 403 | Forbidden - アクセス拒否 |
| 404 | Not Found - リソースが見つからない |
| 422 | Unprocessable Entity - バリデーション失敗 |
| 429 | Too Many Requests - レート制限超過 |
| 500 | Server Error - サーバ内部エラー |

## Emails

---
### Send Email

単一のメール、または複数メール（バッチ）を送信します。

**Endpoint**: `POST /emails`

**Body Parameters**

| パラメータ          | 型 | 必須 | 説明 |
|--------------------|------|----------|-------------|
| to                 | string \| array | Yes | 宛先メールアドレス（複数可） |
| from               | string | Yes | 送信元メールアドレス |
| subject            | string | Yes | 件名 |
| html               | string | No | HTML 本文 |
| text               | string | No | テキスト本文 |
| replyTo            | string | No | Reply-to メールアドレス |
| cc                 | array | No | CC 宛先 |
| bcc                | array | No | BCC 宛先 |

**レスポンス**

```json
{
  "messageId": "xxxxxxxxxxxxxxxx"
}
```

**例**

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

### Get Sent Email Status

送信済みメールのステータスと詳細を取得します。

**Endpoint**: `GET /emails/{email_id}`

**レスポンス**

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

### List Sent Emails

送信済みメールの一覧を、ページネーションとフィルタリング付きで取得します。

**Endpoint**: `GET /emails`

**Query Parameters**

| パラメータ | 型 | 説明 |
|-----------|------|-------------|
| page | integer | ページ番号（default: 1） |
| limit | integer | 1ページあたり件数（default: 20, max: 100） |
| status | string | ステータスでフィルタ：queued, sent, delivered, bounced, failed |
| from | string | 送信元メールでフィルタ |
| to | string | 宛先メールでフィルタ |
| tag | string | タグでフィルタ |
| created_after | string | ISO 8601 timestamp |
| created_before | string | ISO 8601 timestamp |
| sort | string | ソート項目：created_at, status |
| order | string | ソート順：asc, desc |

**レスポンス**

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

**例**

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```


## テンプレート

---
### テンプレートを作成

再利用可能なメールテンプレートを作成します。

**Endpoint**: `POST /templates`

**リクエストボディ**

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

**レスポンス**

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

### テンプレートを取得

ID を指定してテンプレートを取得します。

**Endpoint**: `GET /templates/{template_id}`

**レスポンス**

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

### テンプレート一覧

**Endpoint**: `GET /templates`

**レスポンス**

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

### テンプレートを更新

**Endpoint**: `PUT /templates/{template_id}`

**リクエストボディ**

```json
{
  "name": "Welcome Email v2",
  "subject": "Welcome!",
  "html": "<h1>Hello {{name}}</h1>"
}
```

### テンプレートを削除

**Endpoint**: `DELETE /templates/{template_id}`

**レスポンス**

```json
{
  "success": true,
  "message": "Template deleted"
}
```

### 連絡先（Contacts）

#### 連絡先を追加

購読者リストに連絡先を追加します。

**Endpoint**: `POST /contacts`

**リクエストボディ**

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

**レスポンス**

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

#### 連絡先を取得

**Endpoint**: `GET /contacts/{contact_id}`

#### 連絡先一覧

**Endpoint**: `GET /contacts`

**クエリパラメータ**

| パラメータ | 型 | 説明 |
|-----------|------|-------------|
| page | integer | ページ番号 |
| limit | integer | 1ページあたり件数 |
| tag | string | タグでフィルタ |
| subscribed | boolean | 購読状態でフィルタ |
| search | string | メールアドレスまたは名前で検索 |

#### 連絡先を更新

**Endpoint**: `PUT /contacts/{contact_id}`

#### 連絡先を削除

**Endpoint**: `DELETE /contacts/{contact_id}`

### キャンペーン（Campaigns）

#### キャンペーンを作成

**Endpoint**: `POST /campaigns`

**リクエストボディ**

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

#### キャンペーンを取得

**Endpoint**: `GET /campaigns/{campaign_id}`

#### キャンペーン一覧

**Endpoint**: `GET /campaigns`

#### キャンペーンを更新

**Endpoint**: `PUT /campaigns/{campaign_id}`

#### キャンペーンを送信

**Endpoint**: `POST /campaigns/{campaign_id}/send`

#### キャンペーン統計を取得

**Endpoint**: `GET /campaigns/{campaign_id}/stats`

**レスポンス**

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

### Webhook

#### Webhook を作成

メールイベントを購読します。

**Endpoint**: `POST /webhooks`

**リクエストボディ**

```json
{
  "url": "https://yourdomain.com/webhooks/litestartup",
  "events": ["email.sent", "email.delivered", "email.opened", "email.clicked", "email.bounced"],
  "active": true
}
```

**イベント**

- `email.sent` - 送信のためにキューに入った
- `email.delivered` - 正常に配信された
- `email.opened` - 受信者に開封された
- `email.clicked` - メール内リンクがクリックされた
- `email.bounced` - バウンスした
- `email.spam_reported` - スパムとして報告された
- `email.unsubscribed` - 受信者が配信停止した

#### Webhook ペイロード

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

#### Webhook 一覧

**Endpoint**: `GET /webhooks`

#### Webhook を更新

**Endpoint**: `PUT /webhooks/{webhook_id}`

#### Webhook を削除

**Endpoint**: `DELETE /webhooks/{webhook_id}`

## レート制限（Rate Limiting）

API リクエストはプランに応じてレート制限されます：

| プラン | Requests/Minute | Requests/Hour |
|------|-----------------|---------------|
| Free | 60 | 1,000 |
| Pro | 300 | 10,000 |

レート制限に達すると、API は 429 ステータスコードと `Retry-After` ヘッダーを返します。

```
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

## エラーコード（Error Codes）

| コード | メッセージ | 説明 |
|------|---------|-------------|
| INVALID_EMAIL | Invalid email address | メール形式が不正 |
| INVALID_API_KEY | Invalid API key | API key が未指定または不正 |
| DOMAIN_NOT_VERIFIED | Domain not verified | 送信ドメインが未検証 |
| RATE_LIMIT_EXCEEDED | Rate limit exceeded | リクエスト過多 |
| INVALID_TEMPLATE | Invalid template | テンプレートが見つからない、または不正 |
| CONTACT_NOT_FOUND | Contact not found | 連絡先 ID が見つからない |
| CAMPAIGN_NOT_FOUND | Campaign not found | キャンペーン ID が見つからない |
| INSUFFICIENT_QUOTA | Insufficient quota | 月間メール枠を超過 |

## ベストプラクティス（Best Practices）

### セキュリティ

- ✓ API key は環境変数に保存する
- ✓ すべてのリクエストで HTTPS を使用する
- ✓ API key を定期的にローテーションする
- ✓ API key をバージョン管理にコミットしない

### パフォーマンス

- ✓ 可能なら 1 リクエストで複数メールをまとめて送信する
- ✓ リトライに指数バックオフを実装する
- ✓ テンプレートデータをローカルでキャッシュする
- ✓ 結果が多い場合はページネーションを使用する

### 信頼性

- ✓ すべてのリクエストでエラーハンドリングを実装する
- ✓ デバッグ用に API 呼び出しをログに残す
- ✓ Webhook 配信を監視する
- ✓ 重要な操作には冪等性（idempotency）を実装する

## ページネーション（Pagination）

一覧系エンドポイントは `page` と `limit` パラメータでページネーションをサポートします。

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?page=2&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

レスポンスにはページネーションのメタデータが含まれます：

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

## フィルタリングとソート（Filtering & Sorting）

一覧系エンドポイントはフィルタリングとソートをサポートします：

```bash
# Filter by status
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered" \
  -H "Authorization: Bearer YOUR_API_KEY"

# Sort by date
curl -X GET "https://api.litestartup.com/client/v2/emails?sort=created_at&order=desc" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

**次へ:** [Features Guide](/ja/03-features.md) または [Code Examples](/ja/04-examples.md) を確認してください。
