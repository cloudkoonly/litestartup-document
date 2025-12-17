# API Reference

Riferimento completo per l’API REST di LiteStartup. Tutte le richieste devono essere autenticate con una API key valida.

## URL di base

```
https://api.litestartup.com/client/v2
```

## Autenticazione

Tutte le richieste API richiedono autenticazione tramite token Bearer.

### Header della richiesta

```
Authorization: Bearer YOUR_API_KEY
```

### Verifica API key

```bash
curl -X GET https://api.litestartup.com/client/v2/verify \
  -H "Authorization: Bearer sk_live_xxxxxxxxxxxxx"
```

## Formato della risposta

Tutte le risposte dell’API sono restituite in formato JSON.

### Risposta di successo

```json
{
  "uuid": "xxxxxxxxxxxxx"
}
```

### Risposta di errore

```json
{
  "error": "Invalid API key"
}
```

## Codici di stato HTTP

| Codice | Significato |
|------|---------|
| 200 | OK - Richiesta riuscita |
| 201 | Created - Risorsa creata |
| 400 | Bad Request - Parametri non validi |
| 401 | Unauthorized - API key non valida o mancante |
| 403 | Forbidden - Accesso negato |
| 404 | Not Found - Risorsa non trovata |
| 422 | Unprocessable Entity - Validazione fallita |
| 429 | Too Many Requests - Limite di richieste superato |
| 500 | Server Error - Errore interno del server |

## Emails

---
### Send Email

Invia una singola e-mail o un batch di e-mail.

**Endpoint**: `POST /emails`

**Parametri del body**

| Parametro          | Tipo | Obbligatorio | Descrizione |
|--------------------|------|----------|-------------|
| to                 | string \| array | Sì | Indirizzo/i e-mail del/dei destinatario/i |
| from               | string | Sì | Indirizzo e-mail del mittente |
| subject            | string | Sì | Oggetto dell’e-mail |
| html               | string | No | Corpo HTML dell’e-mail |
| text               | string | No | Corpo dell’e-mail in testo semplice |
| replyTo            | string | No | Indirizzo e-mail di risposta (reply-to) |
| cc                 | array | No | Destinatari in CC |
| bcc                | array | No | Destinatari in BCC |

**Risposta**

```json
{
  "messageId": "xxxxxxxxxxxxxxxx"
}
```

**Esempio**

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

Recupera lo stato e i dettagli di un’e-mail inviata.

**Endpoint**: `GET /emails/{email_id}`

**Risposta**

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

Recupera un elenco di e-mail inviate con paginazione e filtri.

**Endpoint**: `GET /emails`

**Parametri di query**

| Parametro | Tipo | Descrizione |
|-----------|------|-------------|
| page | integer | Numero pagina (default: 1) |
| limit | integer | Risultati per pagina (default: 20, max: 100) |
| status | string | Filtra per stato: queued, sent, delivered, bounced, failed |
| from | string | Filtra per e-mail mittente |
| to | string | Filtra per e-mail destinatario |
| tag | string | Filtra per tag |
| created_after | string | Timestamp ISO 8601 |
| created_before | string | Timestamp ISO 8601 |
| sort | string | Campo ordinamento: created_at, status |
| order | string | Direzione ordinamento: asc, desc |

**Risposta**

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

**Esempio**

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```


## Modelli

---
 ### Crea modello
 
 Crea un modello e-mail riutilizzabile.
 
 **Endpoint**: `POST /templates`

**Corpo della richiesta**

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

**Risposta**

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

### Ottieni modello
 
 Recupera un modello tramite ID.
 
 **Endpoint**: `GET /templates/{template_id}`
 
 **Risposta**
 
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

 ### Elenco modelli
 
 **Endpoint**: `GET /templates`
 
 **Risposta**
 
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

 ### Aggiorna modello
 
 **Endpoint**: `PUT /templates/{template_id}`
 
 **Corpo della richiesta**
 
 ```json
 {
   "name": "Welcome Email v2",
  "subject": "Welcome!",
  "html": "<h1>Hello {{name}}</h1>"
}
```

 ### Elimina modello
 
 **Endpoint**: `DELETE /templates/{template_id}`
 
 **Risposta**
 
 ```json
 {
   "success": true,
  "message": "Template deleted"
}
```

### Contatti

 #### Aggiungi contatto
 
 Aggiungi un contatto alla tua lista iscritti.
 
 **Endpoint**: `POST /contacts`
 
 **Corpo della richiesta**
 
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

**Risposta**

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

 #### Ottieni contatto
 
 **Endpoint**: `GET /contacts/{contact_id}`
 
 #### Elenco contatti
 
 **Endpoint**: `GET /contacts`
 
 **Parametri di query**
 
 | Parametro | Tipo | Descrizione |
 |-----------|------|-------------|
 | page | integer | Numero pagina |
 | limit | integer | Risultati per pagina |
 | tag | string | Filtra per tag |
 | subscribed | boolean | Filtra per stato di iscrizione |
 | search | string | Cerca per e-mail o nome |

 #### Aggiorna contatto
 
 **Endpoint**: `PUT /contacts/{contact_id}`
 
 #### Elimina contatto
 
 **Endpoint**: `DELETE /contacts/{contact_id}`

### Campagne

 #### Crea campagna
 
 **Endpoint**: `POST /campaigns`
 
 **Corpo della richiesta**
 
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

 #### Ottieni campagna
 
 **Endpoint**: `GET /campaigns/{campaign_id}`
 
 #### Elenco campagne
 
 **Endpoint**: `GET /campaigns`
 
 #### Aggiorna campagna
 
 **Endpoint**: `PUT /campaigns/{campaign_id}`
 
 #### Invia campagna
 
 **Endpoint**: `POST /campaigns/{campaign_id}/send`
 
 #### Statistiche campagna
 
 **Endpoint**: `GET /campaigns/{campaign_id}/stats`
 
 **Risposta**
 
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

 #### Crea webhook
 
 Iscriviti agli eventi e-mail.
 
 **Endpoint**: `POST /webhooks`
 
 **Corpo della richiesta**
 
 ```json
 {
   "url": "https://yourdomain.com/webhooks/litestartup",
  "events": ["email.sent", "email.delivered", "email.opened", "email.clicked", "email.bounced"],
  "active": true
}
```

 **Eventi**
 
 - `email.sent` - E-mail messa in coda per l’invio
 - `email.delivered` - E-mail consegnata con successo
 - `email.opened` - E-mail aperta dal destinatario
 - `email.clicked` - Link cliccato nell’e-mail
 - `email.bounced` - E-mail rimbalzata (bounce)
 - `email.spam_reported` - E-mail segnalata come spam
 - `email.unsubscribed` - Destinatario disiscritto

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

## Rate limiting

Le richieste API sono soggette a rate limit in base al tuo piano:

| Piano | Richieste/minuto | Richieste/ora |
|------|-----------------|---------------|
| Free | 60 | 1,000 |
| Pro | 300 | 10,000 |

Quando scatta il rate limit, l’API restituisce un codice 429 con header `Retry-After`.

```
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

## Codici di errore

| Code | Message | Description |
|------|---------|-------------|
| INVALID_EMAIL | Invalid email address | Il formato dell’e-mail non è valido |
| INVALID_API_KEY | Invalid API key | La API key è mancante o non valida |
| DOMAIN_NOT_VERIFIED | Domain not verified | Il dominio mittente non è verificato |
| RATE_LIMIT_EXCEEDED | Rate limit exceeded | Troppe richieste |
| INVALID_TEMPLATE | Invalid template | Template non trovato o non valido |
| CONTACT_NOT_FOUND | Contact not found | ID contatto non trovato |
| CAMPAIGN_NOT_FOUND | Campaign not found | ID campagna non trovato |
| INSUFFICIENT_QUOTA | Insufficient quota | Quota mensile e-mail superata |

## Best practice

### Sicurezza

- ✓ Salva le API key in variabili d’ambiente
- ✓ Usa HTTPS per tutte le richieste
- ✓ Ruota periodicamente le API key
- ✓ Non committare mai le API key nel controllo versione

### Prestazioni

- ✓ Raggruppa più e-mail in una singola richiesta quando possibile
- ✓ Implementa backoff esponenziale per i retry
- ✓ Metti in cache i dati dei template in locale
- ✓ Usa la paginazione per insiemi di risultati grandi

### Affidabilità

- ✓ Implementa gestione errori per tutte le richieste
- ✓ Fai log di tutte le chiamate API per il debug
- ✓ Monitora le consegne dei webhook
- ✓ Implementa idempotenza per le operazioni critiche

## Paginazione

Gli endpoint di elenco supportano la paginazione con i parametri `page` e `limit`.

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?page=2&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

La risposta include metadati di paginazione:

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

## Filtri e ordinamento

Gli endpoint di elenco supportano filtri e ordinamento:

```bash
# Filter by status
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered" \
  -H "Authorization: Bearer YOUR_API_KEY"

# Sort by date
curl -X GET "https://api.litestartup.com/client/v2/emails?sort=created_at&order=desc" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

**Successivo:** Consulta [Features Guide](/it/03-features.md) o [Code Examples](/it/04-examples.md)!
