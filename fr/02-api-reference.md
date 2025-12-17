# Référence API

Référence complète de l’API REST LiteStartup. Toutes les requêtes doivent être authentifiées avec une clé API valide.

## URL de base

```
https://api.litestartup.com/client/v2
```

## Authentification

Toutes les requêtes API nécessitent une authentification via un token Bearer.

### En-tête de requête

```
Authorization: Bearer YOUR_API_KEY
```

### Vérifier la clé API

```bash
curl -X GET https://api.litestartup.com/client/v2/verify \
  -H "Authorization: Bearer sk_live_xxxxxxxxxxxxx"
```

## Format de réponse

Toutes les réponses de l’API sont renvoyées au format JSON.

### Réponse de succès

```json
{
  "uuid": "xxxxxxxxxxxxx"
}
```

### Réponse d’erreur

```json
{
  "error": "Invalid API key"
}
```

## Codes d’état HTTP

| Code | Signification |
|------|---------|
| 200 | OK - Requête réussie |
| 201 | Created - Ressource créée |
| 400 | Bad Request - Paramètres invalides |
| 401 | Unauthorized - Clé API invalide ou manquante |
| 403 | Forbidden - Accès refusé |
| 404 | Not Found - Ressource introuvable |
| 422 | Unprocessable Entity - Validation échouée |
| 429 | Too Many Requests - Limite de débit dépassée |
| 500 | Server Error - Erreur interne du serveur |

## Emails

---
### Envoyer un e-mail

Envoyer un e-mail unique ou un lot d’e-mails.

**Endpoint**: `POST /emails`

**Paramètres du body**

| Paramètre          | Type | Requis | Description |
|--------------------|------|----------|-------------|
| to                 | string \| array | Oui | Adresse(s) e-mail du/des destinataire(s) |
| from               | string | Oui | Adresse e-mail de l’expéditeur |
| subject            | string | Oui | Objet de l’e-mail |
| html               | string | Non | Corps HTML de l’e-mail |
| text               | string | Non | Corps texte (plain text) de l’e-mail |
| replyTo            | string | Non | Adresse e-mail de réponse (reply-to) |
| cc                 | array | Non | Destinataires en copie (CC) |
| bcc                | array | Non | Destinataires en copie cachée (BCC) |

**Réponse**

```json
{
  "messageId": "xxxxxxxxxxxxxxxx"
}
```

**Exemple**

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

### Obtenir le statut d’un e-mail envoyé

Récupérer le statut et les détails d’un e-mail envoyé.

**Endpoint**: `GET /emails/{email_id}`

**Réponse**

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

### Lister les e-mails envoyés

Récupérer une liste d’e-mails envoyés avec pagination et filtres.

**Endpoint**: `GET /emails`

**Paramètres de requête (query)**

| Paramètre | Type | Description |
|-----------|------|-------------|
| page | integer | Numéro de page (par défaut : 1) |
| limit | integer | Résultats par page (par défaut : 20, max : 100) |
| status | string | Filtrer par statut : queued, sent, delivered, bounced, failed |
| from | string | Filtrer par e-mail expéditeur |
| to | string | Filtrer par e-mail destinataire |
| tag | string | Filtrer par tag |
| created_after | string | Horodatage ISO 8601 |
| created_before | string | Horodatage ISO 8601 |
| sort | string | Champ de tri : created_at, status |
| order | string | Ordre de tri : asc, desc |

**Réponse**

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

**Exemple**

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered&limit=10" \
  -H "Authorization: Bearer YOUR_API_KEY"
```


## Templates

---
### Créer un template

Créer un template d’e-mail réutilisable.

**Endpoint**: `POST /templates`

**Body de requête**

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

**Réponse**

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

### Obtenir un template

Récupérer un template par ID.

**Endpoint**: `GET /templates/{template_id}`

**Réponse**

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

### Lister les templates

**Endpoint**: `GET /templates`

**Réponse**

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

### Mettre à jour un template

**Endpoint**: `PUT /templates/{template_id}`

**Body de requête**

```json
{
  "name": "Welcome Email v2",
  "subject": "Welcome!",
  "html": "<h1>Hello {{name}}</h1>"
}
```

### Supprimer un template

**Endpoint**: `DELETE /templates/{template_id}`

**Réponse**

```json
{
  "success": true,
  "message": "Template deleted"
}
```

### Contacts

#### Ajouter un contact

Ajouter un contact à votre liste d’abonnés.

**Endpoint**: `POST /contacts`

**Body de requête**

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

**Réponse**

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

#### Obtenir un contact

**Endpoint**: `GET /contacts/{contact_id}`

#### Lister les contacts

**Endpoint**: `GET /contacts`

**Paramètres de requête (query)**

| Paramètre | Type | Description |
|-----------|------|-------------|
| page | integer | Numéro de page |
| limit | integer | Résultats par page |
| tag | string | Filtrer par tag |
| subscribed | boolean | Filtrer par statut d’abonnement |
| search | string | Rechercher par e-mail ou nom |

#### Mettre à jour un contact

**Endpoint**: `PUT /contacts/{contact_id}`

#### Supprimer un contact

**Endpoint**: `DELETE /contacts/{contact_id}`

### Campagnes

#### Créer une campagne

**Endpoint**: `POST /campaigns`

**Body de requête**

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

#### Obtenir une campagne

**Endpoint**: `GET /campaigns/{campaign_id}`

#### Lister les campagnes

**Endpoint**: `GET /campaigns`

#### Mettre à jour une campagne

**Endpoint**: `PUT /campaigns/{campaign_id}`

#### Envoyer une campagne

**Endpoint**: `POST /campaigns/{campaign_id}/send`

#### Obtenir les statistiques d’une campagne

**Endpoint**: `GET /campaigns/{campaign_id}/stats`

**Réponse**

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

#### Créer un webhook

S’abonner aux événements e-mail.

**Endpoint**: `POST /webhooks`

**Body de requête**

```json
{
  "url": "https://yourdomain.com/webhooks/litestartup",
  "events": ["email.sent", "email.delivered", "email.opened", "email.clicked", "email.bounced"],
  "active": true
}
```

**Événements**

- `email.sent` - E-mail mis en file d’attente pour l’envoi
- `email.delivered` - E-mail livré avec succès
- `email.opened` - E-mail ouvert par le destinataire
- `email.clicked` - Lien cliqué dans l’e-mail
- `email.bounced` - E-mail en bounce
- `email.spam_reported` - E-mail marqué comme spam
- `email.unsubscribed` - Destinataire désabonné

#### Payload du webhook

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

#### Lister les webhooks

**Endpoint**: `GET /webhooks`

#### Mettre à jour un webhook

**Endpoint**: `PUT /webhooks/{webhook_id}`

#### Supprimer un webhook

**Endpoint**: `DELETE /webhooks/{webhook_id}`

## Limitation de débit

Les requêtes API sont limitées en débit selon votre plan :

| Plan | Requêtes/minute | Requêtes/heure |
|------|-----------------|---------------|
| Free | 60 | 1,000 |
| Pro | 300 | 10,000 |

En cas de limitation, l’API renvoie un code d’état 429 avec un en-tête `Retry-After`.

```
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

## Codes d’erreur

| Code | Message | Description |
|------|---------|-------------|
| INVALID_EMAIL | Invalid email address | Le format de l’e-mail est invalide |
| INVALID_API_KEY | Invalid API key | La clé API est manquante ou invalide |
| DOMAIN_NOT_VERIFIED | Domain not verified | Le domaine d’expéditeur n’est pas vérifié |
| RATE_LIMIT_EXCEEDED | Rate limit exceeded | Trop de requêtes |
| INVALID_TEMPLATE | Invalid template | Template introuvable ou invalide |
| CONTACT_NOT_FOUND | Contact not found | ID de contact introuvable |
| CAMPAIGN_NOT_FOUND | Campaign not found | ID de campagne introuvable |
| INSUFFICIENT_QUOTA | Insufficient quota | Quota mensuel d’e-mails dépassé |

## Bonnes pratiques

### Security

- ✓ Stockez les clés API dans des variables d’environnement
- ✓ Utilisez HTTPS pour toutes les requêtes
- ✓ Faites tourner les clés API périodiquement
- ✓ Ne commitez jamais les clés API dans un dépôt

### Performance

- ✓ Regroupez plusieurs e-mails dans une seule requête quand c’est possible
- ✓ Implémentez un backoff exponentiel pour les retries
- ✓ Mettez en cache les données de templates localement
- ✓ Utilisez la pagination pour les gros ensembles de résultats

### Reliability

- ✓ Implémentez la gestion d’erreurs pour toutes les requêtes
- ✓ Journalisez tous les appels API pour le debug
- ✓ Surveillez les livraisons de webhooks
- ✓ Implémentez l’idempotence pour les opérations critiques

## Pagination

Les endpoints de liste supportent la pagination via les paramètres `page` et `limit`.

```bash
curl -X GET "https://api.litestartup.com/client/v2/emails?page=2&limit=50" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

La réponse inclut des métadonnées de pagination :

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

## Filtrage et tri

Les endpoints de liste supportent le filtrage et le tri :

```bash
# Filter by status
curl -X GET "https://api.litestartup.com/client/v2/emails?status=delivered" \
  -H "Authorization: Bearer YOUR_API_KEY"

# Sort by date
curl -X GET "https://api.litestartup.com/client/v2/emails?sort=created_at&order=desc" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

---

**Suite :** Consultez le [Guide des fonctionnalités](/fr/03-features.md) ou les [Exemples de code](/fr/04-examples.md) !
