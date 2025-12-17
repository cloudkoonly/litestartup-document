# API-Referenz

Vollständige Referenz für die LiteStartup REST API. Alle Requests müssen mit einem gültigen API-Key authentifiziert werden.

## Base-URL

```
https://api.litestartup.com/client/v2
```

## Authentifizierung

Alle API-Requests erfordern eine Authentifizierung per Bearer-Token.

### Request-Header

```
Authorization: Bearer YOUR_API_KEY
```

### API-Key verifizieren

```bash
curl -X GET https://api.litestartup.com/client/v2/verify \
  -H "Authorization: Bearer sk_live_xxxxxxxxxxxxx"
```

## Response-Format

Alle API-Responses werden im JSON-Format zurückgegeben.

### Erfolgs-Response

```json
{
  "uuid": "xxxxxxxxxxxxx"
}
```

### Error-Response

```json
{
  "error": "Invalid API key"
}
```

## HTTP-Statuscodes

| Code | Bedeutung |
|------|---------|
| 200 | OK - Request erfolgreich |
| 201 | Created - Ressource erstellt |
| 400 | Bad Request - Ungültige Parameter |
| 401 | Unauthorized - API-Key fehlt oder ist ungültig |
| 403 | Forbidden - Zugriff verweigert |
| 404 | Not Found - Ressource nicht gefunden |
| 422 | Unprocessable Entity - Validierung fehlgeschlagen |
| 429 | Too Many Requests - Rate Limit überschritten |
| 500 | Server Error - Interner Serverfehler |

## E-Mails

---
### E-Mail senden

Sende eine einzelne E-Mail oder einen Batch von E-Mails.

**Endpoint**: `POST /emails`

**Anfrage-Parameter**

| Parameter          | Typ | Erforderlich | Beschreibung |
|--------------------|------|----------|-------------|
| to                 | string \| array | Ja | Empfänger-E-Mail-Adresse(n) |
| from               | string | Ja | Absender-E-Mail-Adresse |
| subject            | string | Ja | Betreffzeile |
| html               | string | Nein | HTML-Body |
| text               | string | Nein | Plain-Text-Body |
| replyTo            | string | Nein | Reply-to-E-Mail-Adresse |
| cc                 | array | Nein | CC-Empfänger |
| bcc                | array | Nein | BCC-Empfänger |

**Antwort**

```json
{
  "messageId": "xxxxxxxxxxxxxxxx"
}
```

**Beispiel**

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

### Status einer gesendeten E-Mail abrufen

Rufe den Status und die Details einer gesendeten E-Mail ab.

**Endpoint**: `GET /emails/{email_id}`

**Antwort**

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

### Gesendete E-Mails auflisten

Rufe eine Liste gesendeter E-Mails mit Pagination und Filtern ab.

**Endpoint**: `GET /emails`

**Abfrage-Parameter**

| Parameter | Typ | Beschreibung |
|-----------|------|-------------|
| page | integer | Seitennummer (Default: 1) |
| limit | integer | Ergebnisse pro Seite (Default: 20, max: 100) |
| status | string | Nach Status filtern: queued, sent, delivered, bounced, failed |
| from | string | Nach Absender-E-Mail filtern |
| to | string | Nach Empfänger-E-Mail filtern |
| tag | string | Nach Tag filtern |
| created_after | string | ISO 8601 Timestamp |
| created_before | string | ISO 8601 Timestamp |
| sort | string | Sortierfeld: created_at, status |
| order | string | Sortierreihenfolge: asc, desc |

**Antwort**

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

**Beispiel**

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```


## Vorlagen

---
### Vorlage erstellen

Erstelle eine wiederverwendbare E-Mail-Vorlage.

**Endpoint**: `POST /templates`

**Anfrage-Body**

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

**Antwort**

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

### Vorlage abrufen

Rufe eine Vorlage anhand der ID ab.

**Endpoint**: `GET /templates/{template_id}`

**Antwort**

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

### Vorlagen auflisten

**Endpoint**: `GET /templates`

**Antwort**

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

### Vorlage aktualisieren

**Endpoint**: `PUT /templates/{template_id}`

**Anfrage-Body**

```json
{
  "name": "Welcome Email v2",
  "subject": "Welcome!",
  "html": "<h1>Hello {{name}}</h1>"
}
```

### Vorlage löschen

**Endpoint**: `DELETE /templates/{template_id}`

**Antwort**

```json
{
  "success": true,
  "message": "Template deleted"
}
```

### Kontakte

#### Kontakt hinzufügen

Füge einen Kontakt zu deiner Abonnentenliste hinzu.

**Endpoint**: `POST /contacts`

**Anfrage-Body**

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

**Antwort**

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

#### Kontakt abrufen

**Endpoint**: `GET /contacts/{contact_id}`

#### Kontakte auflisten

**Endpoint**: `GET /contacts`

**Abfrage-Parameter**

| Parameter | Typ | Beschreibung |
|-----------|------|-------------|
| page | integer | Seitennummer |
| limit | integer | Ergebnisse pro Seite |
| tag | string | Nach Tag filtern |
| subscribed | boolean | Nach Abo-Status filtern |
| search | string | Suche nach E-Mail oder Name |

#### Kontakt aktualisieren

**Endpoint**: `PUT /contacts/{contact_id}`

#### Kontakt löschen

**Endpoint**: `DELETE /contacts/{contact_id}`

### Kampagnen

#### Kampagne erstellen

**Endpoint**: `POST /campaigns`

**Anfrage-Body**

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

#### Kampagne abrufen

**Endpoint**: `GET /campaigns/{campaign_id}`

#### Kampagnen auflisten

**Endpoint**: `GET /campaigns`

#### Kampagne aktualisieren

**Endpoint**: `PUT /campaigns/{campaign_id}`

#### Kampagne senden

**Endpoint**: `POST /campaigns/{campaign_id}/send`

#### Kampagnen-Statistiken abrufen

**Endpoint**: `GET /campaigns/{campaign_id}/stats`

**Antwort**

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

#### Webhook erstellen

Abonniere E-Mail-Events.

**Endpoint**: `POST /webhooks`

**Anfrage-Body**

```json
{
  "url": "https://yourdomain.com/webhooks/litestartup",
  "events": ["email.sent", "email.delivered", "email.opened", "email.clicked", "email.bounced"],
  "active": true
}
```

**Events**

- `email.sent` - E-Mail wurde zum Versand in die Queue gestellt
- `email.delivered` - E-Mail erfolgreich zugestellt
- `email.opened` - E-Mail wurde vom Empfänger geöffnet
- `email.clicked` - Link in der E-Mail wurde geklickt
- `email.bounced` - E-Mail ist gebounced
- `email.spam_reported` - E-Mail wurde als Spam markiert
- `email.unsubscribed` - Empfänger hat sich abgemeldet

#### Webhook-Payload

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

#### Webhooks auflisten

**Endpoint**: `GET /webhooks`

#### Webhook aktualisieren

**Endpoint**: `PUT /webhooks/{webhook_id}`

#### Webhook löschen

**Endpoint**: `DELETE /webhooks/{webhook_id}`

## Rate Limiting

API-Requests sind abhängig von deinem Plan rate-limitiert:

| Plan | Requests/Minute | Requests/Hour |
|------|-----------------|---------------|
| Free | 60 | 1,000 |
| Pro | 300 | 10,000 |

Wenn du rate-limitiert wirst, liefert die API den Statuscode 429 zusammen mit einem `Retry-After` Header.

```
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

## Fehlercodes

| Code | Meldung | Beschreibung |
|------|---------|-------------|
| INVALID_EMAIL | Ungültige E-Mail-Adresse | E-Mail-Format ist ungültig |
| INVALID_API_KEY | Ungültiger API-Key | API-Key fehlt oder ist ungültig |
| DOMAIN_NOT_VERIFIED | Domain nicht verifiziert | Absender-Domain ist nicht verifiziert |
| RATE_LIMIT_EXCEEDED | Rate Limit überschritten | Zu viele Requests |
| INVALID_TEMPLATE | Ungültige Vorlage | Vorlage nicht gefunden oder ungültig |
| CONTACT_NOT_FOUND | Kontakt nicht gefunden | Kontakt-ID nicht gefunden |
| CAMPAIGN_NOT_FOUND | Kampagne nicht gefunden | Kampagnen-ID nicht gefunden |
| INSUFFICIENT_QUOTA | Unzureichendes Kontingent | Monatliches E-Mail-Kontingent überschritten |

## Best Practices

### Sicherheit

- ✓ API-Keys in Umgebungsvariablen speichern
- ✓ Für alle Requests HTTPS verwenden
- ✓ API-Keys regelmäßig rotieren
- ✓ API-Keys niemals in die Versionsverwaltung committen

### Performance

- ✓ Wenn möglich mehrere E-Mails in einem Request bündeln
- ✓ Exponential Backoff für Retries implementieren
- ✓ Vorlagen-Daten lokal cachen
- ✓ Pagination bei großen Ergebnismengen verwenden

### Zuverlässigkeit

- ✓ Fehlerbehandlung für alle Requests implementieren
- ✓ Alle API-Calls fürs Debugging loggen
- ✓ Webhook-Zustellungen überwachen
- ✓ Idempotenz für kritische Operationen implementieren

## Pagination

List-Endpunkte unterstützen Pagination über die Parameter `page` und `limit`.

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?page=2&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

Die Response enthält Pagination-Metadaten:

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

## Filtern & Sortieren

List-Endpunkte unterstützen Filtern und Sortieren:

```bash
# Filter by status
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered" \
  -H "Authorization: Bearer YOUR_API_KEY"

# Sort by date
curl -X GET "https://api.litestartup.com/client/v2/emails?sort=created_at&order=desc" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

**Weiter:** Sieh dir den [Features Guide](/de/03-features.md) oder die [Code Examples](/de/04-examples.md) an!
