# API Reference

Complete reference for the LiteStartup REST API. All requests must be authenticated with a valid API key.

## Base URL

```
https://api.litestartup.com
```

## Authentication

All API requests require authentication using Bearer token authentication.

### Request Header

```
Authorization: Bearer YOUR_API_KEY
```

### Example

```bash
curl -X GET https://api.litestartup.com/emails \
  -H "Authorization: Bearer sk_live_xxxxxxxxxxxxx"
```

## Response Format

All API responses are returned in JSON format.

### Success Response

```json
{
  "success": true,
  "data": {
    "id": "email_123",
    "to": "user@example.com",
    "status": "delivered"
  },
  "message": "Email sent successfully"
}
```

### Error Response

```json
{
  "success": false,
  "error": "Invalid email address",
  "code": "INVALID_EMAIL",
  "status": 400
}
```

## HTTP Status Codes

| Code | Meaning |
|------|---------|
| 200 | OK - Request successful |
| 201 | Created - Resource created |
| 400 | Bad Request - Invalid parameters |
| 401 | Unauthorized - Invalid or missing API key |
| 403 | Forbidden - Access denied |
| 404 | Not Found - Resource not found |
| 422 | Unprocessable Entity - Validation failed |
| 429 | Too Many Requests - Rate limit exceeded |
| 500 | Server Error - Internal server error |

## Endpoints

### Emails

#### Send Email

Send a single email or batch of emails.

**Endpoint**: `POST /emails/send`

**Request Body**

```json
{
  "to": "recipient@example.com",
  "from": "sender@yourdomain.com",
  "subject": "Welcome!",
  "html": "<h1>Hello</h1><p>Welcome to our service.</p>",
  "text": "Hello! Welcome to our service.",
  "reply_to": "support@yourdomain.com",
  "cc": ["cc@example.com"],
  "bcc": ["bcc@example.com"],
  "headers": {
    "X-Custom-Header": "value"
  },
  "tags": ["welcome", "onboarding"],
  "metadata": {
    "user_id": "123",
    "campaign": "welcome_series"
  },
  "template_id": "tmpl_123",
  "template_variables": {
    "name": "John",
    "activation_link": "https://example.com/activate"
  },
  "scheduled_at": "2024-01-15T10:30:00Z",
  "track_opens": true,
  "track_clicks": true
}
```

**Parameters**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| to | string \| array | Yes | Recipient email address(es) |
| from | string | Yes | Sender email address |
| subject | string | Yes | Email subject line |
| html | string | No | HTML email body |
| text | string | No | Plain text email body |
| reply_to | string | No | Reply-to email address |
| cc | array | No | CC recipients |
| bcc | array | No | BCC recipients |
| headers | object | No | Custom email headers |
| tags | array | No | Email tags for organization |
| metadata | object | No | Custom metadata |
| template_id | string | No | Email template ID |
| template_variables | object | No | Variables for template |
| scheduled_at | string | No | ISO 8601 timestamp for scheduling |
| track_opens | boolean | No | Enable open tracking (default: true) |
| track_clicks | boolean | No | Enable click tracking (default: true) |

**Response**

```json
{
  "success": true,
  "data": {
    "id": "email_1234567890",
    "to": "recipient@example.com",
    "from": "sender@yourdomain.com",
    "subject": "Welcome!",
    "status": "queued",
    "created_at": "2024-01-15T10:00:00Z",
    "scheduled_at": null
  }
}
```

**Example**

```bash
curl -X POST https://api.litestartup.com/emails/send \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "to": "user@example.com",
    "from": "hello@yourdomain.com",
    "subject": "Welcome!",
    "html": "<h1>Hello</h1>",
    "text": "Hello"
  }'
```

#### Get Email Status

Retrieve the status and details of a sent email.

**Endpoint**: `GET /emails/{email_id}`

**Response**

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

#### List Emails

Retrieve a list of sent emails with pagination and filtering.

**Endpoint**: `GET /emails`

**Query Parameters**

| Parameter | Type | Description |
|-----------|------|-------------|
| page | integer | Page number (default: 1) |
| limit | integer | Results per page (default: 20, max: 100) |
| status | string | Filter by status: queued, sent, delivered, bounced, failed |
| from | string | Filter by sender email |
| to | string | Filter by recipient email |
| tag | string | Filter by tag |
| created_after | string | ISO 8601 timestamp |
| created_before | string | ISO 8601 timestamp |
| sort | string | Sort field: created_at, status |
| order | string | Sort order: asc, desc |

**Response**

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

**Example**

```bash
curl -X GET "https://api.litestartup.com/emails?status=delivered&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### Templates

#### Create Template

Create a reusable email template.

**Endpoint**: `POST /templates`

**Request Body**

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

**Response**

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

#### Get Template

Retrieve a template by ID.

**Endpoint**: `GET /templates/{template_id}`

**Response**

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

#### List Templates

**Endpoint**: `GET /templates`

**Response**

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

#### Update Template

**Endpoint**: `PUT /templates/{template_id}`

**Request Body**

```json
{
  "name": "Welcome Email v2",
  "subject": "Welcome!",
  "html": "<h1>Hello {{name}}</h1>"
}
```

#### Delete Template

**Endpoint**: `DELETE /templates/{template_id}`

**Response**

```json
{
  "success": true,
  "message": "Template deleted"
}
```

### Contacts

#### Add Contact

Add a contact to your subscriber list.

**Endpoint**: `POST /contacts`

**Request Body**

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

**Response**

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

#### Get Contact

**Endpoint**: `GET /contacts/{contact_id}`

#### List Contacts

**Endpoint**: `GET /contacts`

**Query Parameters**

| Parameter | Type | Description |
|-----------|------|-------------|
| page | integer | Page number |
| limit | integer | Results per page |
| tag | string | Filter by tag |
| subscribed | boolean | Filter by subscription status |
| search | string | Search by email or name |

#### Update Contact

**Endpoint**: `PUT /contacts/{contact_id}`

#### Delete Contact

**Endpoint**: `DELETE /contacts/{contact_id}`

### Campaigns

#### Create Campaign

**Endpoint**: `POST /campaigns`

**Request Body**

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

#### Get Campaign

**Endpoint**: `GET /campaigns/{campaign_id}`

#### List Campaigns

**Endpoint**: `GET /campaigns`

#### Update Campaign

**Endpoint**: `PUT /campaigns/{campaign_id}`

#### Send Campaign

**Endpoint**: `POST /campaigns/{campaign_id}/send`

#### Get Campaign Stats

**Endpoint**: `GET /campaigns/{campaign_id}/stats`

**Response**

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

#### Create Webhook

Subscribe to email events.

**Endpoint**: `POST /webhooks`

**Request Body**

```json
{
  "url": "https://yourdomain.com/webhooks/litestartup",
  "events": ["email.sent", "email.delivered", "email.opened", "email.clicked", "email.bounced"],
  "active": true
}
```

**Events**

- `email.sent` - Email queued for sending
- `email.delivered` - Email successfully delivered
- `email.opened` - Email opened by recipient
- `email.clicked` - Link clicked in email
- `email.bounced` - Email bounced
- `email.spam_reported` - Email marked as spam
- `email.unsubscribed` - Recipient unsubscribed

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

#### List Webhooks

**Endpoint**: `GET /webhooks`

#### Update Webhook

**Endpoint**: `PUT /webhooks/{webhook_id}`

#### Delete Webhook

**Endpoint**: `DELETE /webhooks/{webhook_id}`

## Rate Limiting

API requests are rate limited based on your plan:

| Plan | Requests/Minute | Requests/Hour |
|------|-----------------|---------------|
| Free | 60 | 1,000 |
| Pro | 300 | 10,000 |

When rate limited, the API returns a 429 status code with a `Retry-After` header.

```
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

## Error Codes

| Code | Message | Description |
|------|---------|-------------|
| INVALID_EMAIL | Invalid email address | Email format is invalid |
| INVALID_API_KEY | Invalid API key | API key is missing or invalid |
| DOMAIN_NOT_VERIFIED | Domain not verified | Sender domain not verified |
| RATE_LIMIT_EXCEEDED | Rate limit exceeded | Too many requests |
| INVALID_TEMPLATE | Invalid template | Template not found or invalid |
| CONTACT_NOT_FOUND | Contact not found | Contact ID not found |
| CAMPAIGN_NOT_FOUND | Campaign not found | Campaign ID not found |
| INSUFFICIENT_QUOTA | Insufficient quota | Monthly email quota exceeded |

## Best Practices

### Security

- ✓ Store API keys in environment variables
- ✓ Use HTTPS for all requests
- ✓ Rotate API keys periodically
- ✓ Never commit API keys to version control

### Performance

- ✓ Batch multiple emails in a single request when possible
- ✓ Implement exponential backoff for retries
- ✓ Cache template data locally
- ✓ Use pagination for large result sets

### Reliability

- ✓ Implement error handling for all requests
- ✓ Log all API calls for debugging
- ✓ Monitor webhook deliveries
- ✓ Implement idempotency for critical operations

## Pagination

List endpoints support pagination with `page` and `limit` parameters.

```bash
curl -X GET "https://api.litestartup.com/emails?page=2&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

Response includes pagination metadata:

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

## Filtering & Sorting

List endpoints support filtering and sorting:

```bash
# Filter by status
curl -X GET "https://api.litestartup.com/emails?status=delivered" \
  -H "Authorization: Bearer YOUR_API_KEY"

# Sort by date
curl -X GET "https://api.litestartup.com/emails?sort=created_at&order=desc" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

**Next:** Check [Features Guide](03-features.md) or [Code Examples](04-examples.md)!
