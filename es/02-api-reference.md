# Referencia de la API

Referencia completa de la API REST de LiteStartup. Todas las solicitudes deben autenticarse con una API key válida.

## URL base

```
https://api.litestartup.com/client/v2
```

## Autenticación

Todas las solicitudes a la API requieren autenticación mediante token Bearer.

### Cabecera de la solicitud

```
Authorization: Bearer YOUR_API_KEY
```

### Verificar API key

```bash
curl -X GET https://api.litestartup.com/client/v2/verify \
  -H "Authorization: Bearer sk_live_xxxxxxxxxxxxx"
```

## Formato de respuesta

Todas las respuestas de la API se devuelven en formato JSON.

### Respuesta exitosa

```json
{
  "uuid": "xxxxxxxxxxxxx"
}
```

### Respuesta de error

```json
{
  "error": "Invalid API key"
}
```

## Códigos de estado HTTP

| Código | Significado |
|------|---------|
| 200 | OK - Solicitud exitosa |
| 201 | Created - Recurso creado |
| 400 | Bad Request - Parámetros inválidos |
| 401 | Unauthorized - API key inválida o ausente |
| 403 | Forbidden - Acceso denegado |
| 404 | Not Found - Recurso no encontrado |
| 422 | Unprocessable Entity - Falló la validación |
| 429 | Too Many Requests - Se excedió el límite de tasa |
| 500 | Server Error - Error interno del servidor |

## Emails

---
### Enviar email

Envía un email individual o un lote de emails.

**Endpoint**: `POST /emails`

**Parámetros del body**

| Parámetro          | Tipo | Requerido | Descripción |
|--------------------|------|----------|-------------|
| to                 | string \| array | Sí | Dirección(es) de email del destinatario |
| from               | string | Sí | Dirección de email del remitente |
| subject            | string | Sí | Asunto del email |
| html               | string | No | Cuerpo HTML del email |
| text               | string | No | Cuerpo del email en texto plano |
| replyTo            | string | No | Dirección de email para responder |
| cc                 | array | No | Destinatarios en CC |
| bcc                | array | No | Destinatarios en BCC |

**Respuesta**

```json
{
  "messageId": "xxxxxxxxxxxxxxxx"
}
```

**Ejemplo**

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

### Obtener estado de un email enviado

Obtén el estado y los detalles de un email enviado.

**Endpoint**: `GET /emails/{email_id}`

**Respuesta**

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

### Listar emails enviados

Obtén una lista de emails enviados con paginación y filtros.

**Endpoint**: `GET /emails`

**Parámetros de query**

| Parámetro | Tipo | Descripción |
|-----------|------|-------------|
| page | integer | Número de página (por defecto: 1) |
| limit | integer | Resultados por página (por defecto: 20, máximo: 100) |
| status | string | Filtrar por estado: queued, sent, delivered, bounced, failed |
| from | string | Filtrar por email remitente |
| to | string | Filtrar por email destinatario |
| tag | string | Filtrar por tag |
| created_after | string | Timestamp ISO 8601 |
| created_before | string | Timestamp ISO 8601 |
| sort | string | Campo de orden: created_at, status |
| order | string | Orden: asc, desc |

**Respuesta**

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

**Ejemplo**

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```


## Plantillas

---
### Crear plantilla

Crea una plantilla de email reutilizable.

**Endpoint**: `POST /templates`

**Body de la solicitud**

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

**Respuesta**

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

### Obtener plantilla

Obtén una plantilla por ID.

**Endpoint**: `GET /templates/{template_id}`

**Respuesta**

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

### Listar plantillas

**Endpoint**: `GET /templates`

**Respuesta**

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

### Actualizar plantilla

**Endpoint**: `PUT /templates/{template_id}`

**Body de la solicitud**

```json
{
  "name": "Welcome Email v2",
  "subject": "Welcome!",
  "html": "<h1>Hello {{name}}</h1>"
}
```

### Eliminar plantilla

**Endpoint**: `DELETE /templates/{template_id}`

**Respuesta**

```json
{
  "success": true,
  "message": "Template deleted"
}
```

## Contactos

#### Añadir contacto

Añade un contacto a tu lista de suscriptores.

**Endpoint**: `POST /contacts`

**Body de la solicitud**

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

**Respuesta**

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

#### Obtener contacto

**Endpoint**: `GET /contacts/{contact_id}`

#### Listar contactos

**Endpoint**: `GET /contacts`

**Parámetros de query**

| Parámetro | Tipo | Descripción |
|-----------|------|-------------|
| page | integer | Número de página |
| limit | integer | Resultados por página |
| tag | string | Filtrar por tag |
| subscribed | boolean | Filtrar por estado de suscripción |
| search | string | Buscar por email o nombre |

#### Actualizar contacto

**Endpoint**: `PUT /contacts/{contact_id}`

#### Eliminar contacto

**Endpoint**: `DELETE /contacts/{contact_id}`

## Campañas

#### Crear campaña

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

#### Obtener campaña

**Endpoint**: `GET /campaigns/{campaign_id}`

#### Listar campañas

**Endpoint**: `GET /campaigns`

#### Actualizar campaña

**Endpoint**: `PUT /campaigns/{campaign_id}`

#### Enviar campaña

**Endpoint**: `POST /campaigns/{campaign_id}/send`

#### Obtener estadísticas de campaña

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

## Webhooks

#### Crear webhook

Suscríbete a eventos de email.

**Endpoint**: `POST /webhooks`

**Request Body**

```json
{
  "url": "https://yourdomain.com/webhooks/litestartup",
  "events": ["email.sent", "email.delivered", "email.opened", "email.clicked", "email.bounced"],
  "active": true
}
```

**Eventos**

- `email.sent` - Email encolado para envío
- `email.delivered` - Email entregado correctamente
- `email.opened` - Email abierto por el destinatario
- `email.clicked` - Enlace clicado en el email
- `email.bounced` - Email rebotado
- `email.spam_reported` - Email marcado como spam
- `email.unsubscribed` - El destinatario se dio de baja

#### Payload del webhook

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

#### Actualizar webhook

**Endpoint**: `PUT /webhooks/{webhook_id}`

#### Eliminar webhook

**Endpoint**: `DELETE /webhooks/{webhook_id}`

## Limitación de tasa

Las solicitudes a la API están limitadas por tasa según tu plan:

| Plan | Solicitudes/Minuto | Solicitudes/Hora |
|------|-----------------|---------------|
| Free | 60 | 1,000 |
| Pro | 300 | 10,000 |

Cuando se aplica la limitación, la API devuelve el código 429 junto con la cabecera `Retry-After`.

```
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

## Códigos de error

| Código | Mensaje | Descripción |
|------|---------|-------------|
| INVALID_EMAIL | Invalid email address | El formato del email no es válido |
| INVALID_API_KEY | Invalid API key | Falta la API key o es inválida |
| DOMAIN_NOT_VERIFIED | Domain not verified | El dominio remitente no está verificado |
| RATE_LIMIT_EXCEEDED | Rate limit exceeded | Demasiadas solicitudes |
| INVALID_TEMPLATE | Invalid template | La plantilla no existe o no es válida |
| CONTACT_NOT_FOUND | Contact not found | No se encontró el ID del contacto |
| CAMPAIGN_NOT_FOUND | Campaign not found | No se encontró el ID de la campaña |
| INSUFFICIENT_QUOTA | Insufficient quota | Se excedió la cuota mensual de emails |

## Buenas prácticas

### Seguridad

- ✓ Guarda las API keys en variables de entorno
- ✓ Usa HTTPS para todas las solicitudes
- ✓ Rota las API keys periódicamente
- ✓ Nunca subas API keys al control de versiones

### Rendimiento

- ✓ Envía varios emails en una sola solicitud cuando sea posible
- ✓ Implementa exponential backoff para reintentos
- ✓ Cachea localmente los datos de plantillas
- ✓ Usa paginación para conjuntos de resultados grandes

### Fiabilidad

- ✓ Implementa manejo de errores para todas las solicitudes
- ✓ Registra todas las llamadas a la API para depuración
- ✓ Monitoriza entregas de webhooks
- ✓ Implementa idempotencia en operaciones críticas

## Paginación

Los endpoints de listado soportan paginación mediante los parámetros `page` y `limit`.

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?page=2&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

La respuesta incluye metadatos de paginación:

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

## Filtrado y ordenación

Los endpoints de listado soportan filtrado y ordenación:

```bash
# Filter by status
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered" \
  -H "Authorization: Bearer YOUR_API_KEY"

# Sort by date
curl -X GET "https://api.litestartup.com/client/v2/emails?sort=created_at&order=desc" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

**Siguiente:** Revisa la [Guía de funcionalidades](/es/03-features.md) o los [Ejemplos de código](/es/04-examples.md)!
