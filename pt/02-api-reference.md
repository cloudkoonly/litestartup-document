# Referência da API

Referência completa da API REST do LiteStartup. Todas as requisições devem ser autenticadas com uma chave de API válida.

## URL base

```
https://api.litestartup.com/client/v2
```

## Autenticação

Todas as requisições de API exigem autenticação usando Bearer token.

### Cabeçalho da requisição

```
Authorization: Bearer YOUR_API_KEY
```

### Verificar chave de API

```bash
curl -X GET https://api.litestartup.com/client/v2/verify \
  -H "Authorization: Bearer sk_live_xxxxxxxxxxxxx"
```

## Formato de resposta

Todas as respostas da API são retornadas em formato JSON.

### Resposta de sucesso

```json
{
  "uuid": "xxxxxxxxxxxxx"
}
```

### Resposta de erro

```json
{
  "error": "Invalid API key"
}
```

## Códigos de status HTTP

| Código | Significado |
|------|---------|
| 200 | OK - Requisição bem-sucedida |
| 201 | Created - Recurso criado |
| 400 | Bad Request - Parâmetros inválidos |
| 401 | Unauthorized - Chave de API inválida ou ausente |
| 403 | Forbidden - Acesso negado |
| 404 | Not Found - Recurso não encontrado |
| 422 | Unprocessable Entity - Falha de validação |
| 429 | Too Many Requests - Rate limit excedido |
| 500 | Server Error - Erro interno do servidor |

## Emails

---
### Enviar e-mail

Envie um único e-mail ou um lote de e-mails.

**Endpoint**: `POST /emails`

**Parâmetros do corpo**

| Parâmetro          | Tipo | Obrigatório | Descrição |
|--------------------|------|----------|-------------|
| to                 | string \| array | Yes | Recipient email address(es) |
| from               | string | Yes | Sender email address |
| subject            | string | Yes | Email subject line |
| html               | string | No | HTML email body |
| text               | string | No | Plain text email body |
| replyTo            | string | No | Reply-to email address |
| cc                 | array | No | CC recipients |
| bcc                | array | No | BCC recipients |

**Resposta**

```json
{
  "messageId": "xxxxxxxxxxxxxxxx"
}
```

**Exemplo**

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

### Obter status do e-mail enviado

Recupere o status e os detalhes de um e-mail enviado.

**Endpoint**: `GET /emails/{email_id}`

**Resposta**

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

### Listar e-mails enviados

Recupere uma lista de e-mails enviados com paginação e filtros.

**Endpoint**: `GET /emails`

**Parâmetros de query**

| Parâmetro | Tipo | Descrição |
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

**Resposta**

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

**Exemplo**

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```


## Templates

---
### Criar template

Crie um template de e-mail reutilizável.

**Endpoint**: `POST /templates`

**Corpo da requisição**

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

**Resposta**

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

### Obter template

Recupere um template pelo ID.

**Endpoint**: `GET /templates/{template_id}`

**Resposta**

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

### Listar templates

**Endpoint**: `GET /templates`

**Resposta**

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

### Atualizar template

**Endpoint**: `PUT /templates/{template_id}`

**Corpo da requisição**

```json
{
  "name": "Welcome Email v2",
  "subject": "Welcome!",
  "html": "<h1>Hello {{name}}</h1>"
}
```

### Excluir template

**Endpoint**: `DELETE /templates/{template_id}`

**Resposta**

```json
{
  "success": true,
  "message": "Template deleted"
}
```

### Contatos

#### Adicionar contato

Adicione um contato à sua lista de assinantes.

**Endpoint**: `POST /contacts`

**Corpo da requisição**

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

**Resposta**

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

#### Obter contato

**Endpoint**: `GET /contacts/{contact_id}`

#### Listar contatos

**Endpoint**: `GET /contacts`

**Parâmetros de query**

| Parâmetro | Tipo | Descrição |
|-----------|------|-------------|
| page | integer | Page number |
| limit | integer | Results per page |
| tag | string | Filter by tag |
| subscribed | boolean | Filter by subscription status |
| search | string | Search by email or name |

#### Atualizar contato

**Endpoint**: `PUT /contacts/{contact_id}`

#### Excluir contato

**Endpoint**: `DELETE /contacts/{contact_id}`

### Campanhas

#### Criar campanha

**Endpoint**: `POST /campaigns`

**Corpo da requisição**

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

#### Obter campanha

**Endpoint**: `GET /campaigns/{campaign_id}`

#### Listar campanhas

**Endpoint**: `GET /campaigns`

#### Atualizar campanha

**Endpoint**: `PUT /campaigns/{campaign_id}`

#### Enviar campanha

**Endpoint**: `POST /campaigns/{campaign_id}/send`

#### Obter estatísticas da campanha

**Endpoint**: `GET /campaigns/{campaign_id}/stats`

**Resposta**

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

#### Criar webhook

Assine eventos de e-mail.

**Endpoint**: `POST /webhooks`

**Corpo da requisição**

```json
{
  "url": "https://yourdomain.com/webhooks/litestartup",
  "events": ["email.sent", "email.delivered", "email.opened", "email.clicked", "email.bounced"],
  "active": true
}
```

**Eventos**

- `email.sent` - E-mail enfileirado para envio
- `email.delivered` - E-mail entregue com sucesso
- `email.opened` - E-mail aberto pelo destinatário
- `email.clicked` - Link clicado no e-mail
- `email.bounced` - E-mail com bounce
- `email.spam_reported` - E-mail marcado como spam
- `email.unsubscribed` - Destinatário descadastrado

#### Payload do webhook

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

#### Listar webhooks

**Endpoint**: `GET /webhooks`

#### Atualizar webhook

**Endpoint**: `PUT /webhooks/{webhook_id}`

#### Excluir webhook

**Endpoint**: `DELETE /webhooks/{webhook_id}`

## Limitação de taxa

As requisições de API são limitadas por taxa (rate limited) de acordo com seu plano:

| Plan | Requests/Minute | Requests/Hour |
|------|-----------------|---------------|
| Free | 60 | 1,000 |
| Pro | 300 | 10,000 |

Quando há rate limiting, a API retorna o status 429 com o cabeçalho `Retry-After`.

```
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

## Códigos de erro

| Código | Mensagem | Descrição |
|------|---------|-------------|
| INVALID_EMAIL | Invalid email address | Email format is invalid |
| INVALID_API_KEY | Invalid API key | API key is missing or invalid |
| DOMAIN_NOT_VERIFIED | Domain not verified | Sender domain not verified |
| RATE_LIMIT_EXCEEDED | Rate limit exceeded | Too many requests |
| INVALID_TEMPLATE | Invalid template | Template not found or invalid |
| CONTACT_NOT_FOUND | Contact not found | Contact ID not found |
| CAMPAIGN_NOT_FOUND | Campaign not found | Campaign ID not found |
| INSUFFICIENT_QUOTA | Insufficient quota | Monthly email quota exceeded |

## Boas práticas

### Segurança

- ✓ Armazene chaves de API em variáveis de ambiente
- ✓ Use HTTPS em todas as requisições
- ✓ Faça rotação das chaves de API periodicamente
- ✓ Nunca faça commit de chaves de API no controle de versão

### Desempenho

- ✓ Agrupe (batch) vários e-mails em uma única requisição quando possível
- ✓ Implemente backoff exponencial para retries
- ✓ Faça cache dos dados de templates localmente
- ✓ Use paginação para grandes conjuntos de resultados

### Confiabilidade

- ✓ Implemente tratamento de erros para todas as requisições
- ✓ Registre (log) todas as chamadas de API para debug
- ✓ Monitore entregas de webhooks
- ✓ Implemente idempotência para operações críticas

## Paginação

Os endpoints de listagem suportam paginação com os parâmetros `page` e `limit`.

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?page=2&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

A resposta inclui metadados de paginação:

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

## Filtragem e ordenação

Os endpoints de listagem suportam filtragem e ordenação:

```bash
# Filter by status
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered" \
  -H "Authorization: Bearer YOUR_API_KEY"

# Sort by date
curl -X GET "https://api.litestartup.com/client/v2/emails?sort=created_at&order=desc" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

**Next:** Confira [Features Guide](/pt/03-features.md) ou [Code Examples](/pt/04-examples.md)!
