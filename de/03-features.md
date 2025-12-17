# Feature-Guide

Entdecke alle leistungsstarken Funktionen, die LiteStartup bietet, um dein Startup erfolgreich zu machen.

## Workmail - Business-E-Mail

LiteStartup enthält eine integrierte Business-E-Mail-Funktionalität, wodurch separate E-Mail-Dienste wie Google Workspace überflüssig werden.

### Was ist Workmail?

Workmail ist ein vollwertiger Business-E-Mail-Dienst, der direkt in LiteStartup integriert ist. Du kannst E-Mails über deine eigene Domain senden und empfangen – ohne zusätzliche Abos.

### Vorteile

- **Geld sparen**: 72–144 $ pro Jahr und Teammitglied (im Vergleich zu Google Workspace)
- **Eine Plattform**: E-Mail und Marketing an einem Ort
- **Professionelles Auftreten**: Nutze deine eigene Domain
- **Voll ausgestattet**: Weiterleitungen, Aliase, Auto-Responder

### Erste Schritte mit Workmail

1. Gehe zu **Settings** → **Workmail**
2. Füge deine Domain hinzu (z. B. `hello@yourdomain.com`)
3. Verifiziere DNS-Records
4. Erstelle E-Mail-Konten für Teammitglieder
5. Starte mit dem Senden und Empfangen von E-Mails

### E-Mail-Konten erstellen

```
1. Click "Add Email Account"
2. Enter username (e.g., "john")
3. Set password
4. Assign to team member
5. Click "Create"
```

Die E-Mail-Adresse lautet: `john@yourdomain.com`

### E-Mail-Weiterleitung

Richte automatische Weiterleitung ein:

```
1. Go to email account settings
2. Click "Forwarding"
3. Enter forwarding address
4. Confirm forwarding
5. Emails now forward automatically
```

### Auto-Responder

Richte automatische Antworten ein:

```
1. Go to email account settings
2. Click "Auto-Responder"
3. Enable auto-responder
4. Set message and date range
5. Save
```

## KI-Content-Assistent

Der KI-Content-Assistent von LiteStartup hilft dir, schneller bessere E-Mails zu schreiben.

### Funktionen

- **Betreffzeilen-Generierung**: KI schlägt optimierte Betreffzeilen vor
- **E-Mail-Text**: Generiere Inhalte für den E-Mail-Body
- **A/B-Testing**: Erstelle Varianten zum Testen
- **Tonfall-Anpassung**: Passe den Text an deine Brand Voice an
- **Optimierung**: Vorschläge zur Verbesserung der Öffnungsrate

### KI-Assistent verwenden

#### Betreffzeilen generieren

```
1. Click "AI Assistant" in email editor
2. Select "Generate Subject Lines"
3. Describe your email purpose
4. AI generates 5 variations
5. Click to use or regenerate
```

Beispiel:
- Input: "Welcome email for new users"
- KI-Vorschläge:
  - "Welcome! Get started in 3 minutes"
  - "You're in! Here's what's next"
  - "Welcome aboard - your journey starts now"

#### E-Mail-Text generieren

```
1. Click "AI Assistant"
2. Select "Generate Email Body"
3. Provide key points
4. Choose tone (professional, friendly, casual)
5. AI generates email content
6. Edit and customize as needed
```

#### A/B-Test-Varianten

```
1. Click "AI Assistant"
2. Select "Create A/B Variations"
3. AI generates alternative versions
4. Choose which to test
5. LiteStartup tracks performance
```

### KI-Schreibtipps

- ✓ Sei konkret, was dein Ziel ist
- ✓ Nenne deine Zielgruppe
- ✓ Gib den gewünschten Tonfall an
- ✓ Nenne die wichtigsten Informationen, die enthalten sein sollen
- ✓ Prüfe KI-Vorschläge und passe sie an

## Automatisierung & Workflows

Erstelle intelligente Workflows, die automatisch E-Mails basierend auf dem Verhalten deiner Nutzer versenden.

### Workflow-Typen

#### Welcome Series

Sende automatisch eine Serie von E-Mails an neue Abonnenten.

```
1. Go to Automation → Workflows
2. Click "Create Workflow"
3. Select "Welcome Series"
4. Add emails (1-5 emails)
5. Set delays between emails
6. Activate workflow
```

Beispiel Welcome Series:
- E-Mail 1: Welcome (immediate)
- E-Mail 2: Getting Started (1 day later)
- E-Mail 3: Feature Highlight (3 days later)
- E-Mail 4: Success Story (7 days later)

#### Re-engagement Campaign

Gewinne inaktive Abonnenten zurück.

```
1. Create workflow
2. Select "Re-engagement"
3. Set inactivity threshold (e.g., 30 days)
4. Add re-engagement emails
5. Set follow-up actions
6. Activate
```

#### Win-back Campaign

Sprich Kunden an, die in letzter Zeit nicht gekauft haben.

```
1. Create workflow
2. Select "Win-back"
3. Define inactive period
4. Create compelling offer
5. Set retry schedule
6. Activate
```

#### Abandoned Cart Recovery

Erinnere Kunden an Artikel, die im Warenkorb liegen geblieben sind.

```
1. Create workflow
2. Select "Abandoned Cart"
3. Set delay (e.g., 1 hour)
4. Customize email with product details
5. Add follow-up emails
6. Activate
```

### Workflow-Trigger

Workflows können ausgelöst werden durch:

- **Nutzeraktionen**: Signup, purchase, download
- **Zeitbasiert**: Specific date/time, anniversary
- **Verhalten**: Opens, clicks, inactivity
- **Custom**: API triggers, webhooks

### Workflow-Bedingungen

Füge Bedingungen hinzu, um den Ablauf des Workflows zu steuern:

```
IF user.plan == "pro" THEN send_email("pro_features")
IF user.location == "US" THEN send_email("us_offer")
IF user.opened_count > 5 THEN send_email("vip_offer")
```

### Workflow-Analytics

Überwache die Workflow-Performance:

- Gesendete E-Mails
- Zustellrate
- Öffnungsrate
- Klickrate
- Conversion-Rate
- Generierter Umsatz

## Subscription-Formulare

Baue deine Abonnentenliste mit eingebetteten Signup-Formularen auf.

### Subscription-Formular erstellen

```
1. Go to Forms → Create Form
2. Choose form type:
   - Simple signup
   - Double opt-in
   - Custom fields
3. Design form
4. Add fields (email, name, custom fields)
5. Set confirmation message
6. Get embed code
```

### Formular-Typen

#### Simple Signup

Ein einstufiges Formular für schnelle Registrierungen.

```html
<iframe src="https://forms.litestartup.com/simple/form_id"></iframe>
```

#### Double Opt-in

Zwei-Schritt-Bestätigung für Compliance.

```
1. User enters email
2. Confirmation email sent
3. User clicks confirmation link
4. Subscription confirmed
```

#### Custom Fields

Zusätzliche Informationen erfassen:

- Email (required)
- Name (optional)
- Company (optional)
- Plan Interest (dropdown)
- Budget (multiple choice)

### Formular-Anpassung

- **Farben**: An dein Branding anpassen
- **Text**: Eigene Labels und Nachrichten
- **Felder**: Felder hinzufügen/entfernen
- **Weiterleitung**: Weiterleitung nach der Registrierung
- **Webhook**: Daten an dein System senden

### Formulare einbetten

#### Auf der Website

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

#### Auf der Landingpage

```html
<!-- Embed directly -->
<iframe src="https://forms.litestartup.com/form_id" 
        width="100%" height="500"></iframe>
```

#### Popup-Formular

```javascript
LiteStartup.showPopup('form_id', {
  trigger: 'exit', // Show on exit intent
  delay: 5000,     // Show after 5 seconds
  frequency: 'once' // Show once per session
});
```

## Waitlist-Management

Baue vor dem Launch Spannung auf – mit Waitlist-Management.

### Waitlist erstellen

```
1. Go to Waitlist → Create Waitlist
2. Name your waitlist
3. Set launch date
4. Customize signup page
5. Generate signup link
6. Share with audience
```

### Waitlist-Features

- **Referral Tracking**: Nutzer steigen durch das Werben von Freunden im Ranking
- **Invite Codes**: Personalisierte Einladungscodes senden
- **Ranking**: Position des Nutzers auf der Waitlist anzeigen
- **Email Notifications**: Benachrichtigung bei Einladung
- **Analytics**: Signup-Quellen tracken

### Referral-Programm

Ermögliche Nutzern, durch Empfehlungen Early Access zu erhalten:

```
1. Enable referral in waitlist settings
2. Users get unique referral link
3. Each successful referral = 1 spot
4. Leaderboard shows top referrers
5. Send invites to top referrers first
```

### Einladungen senden

```
1. Go to Waitlist → Manage
2. Select users to invite
3. Generate invite codes
4. Send invite emails
5. Track acceptance
```

### Waitlist-Analytics

Überwache das Wachstum der Waitlist:

- Gesamtanzahl Registrierungen
- Registrierungen über Referrals
- Conversion-Rate
- Top-Referrer
- Signup-Quellen
- Geografische Verteilung

## E-Mail-Vorlagen

Erstelle und verwalte wiederverwendbare E-Mail-Vorlagen.

### Vorlagenbibliothek

Greife auf vorgefertigte Vorlagen zu:

- Welcome-E-Mails
- Promo-E-Mails
- Transaktionale E-Mails
- Newsletter-Vorlagen
- Event-Einladungen
- Passwort-Reset

### Eigene Vorlage erstellen

```
1. Go to Templates → Create
2. Choose layout
3. Add content blocks
4. Insert variables ({{name}}, {{company}})
5. Preview
6. Save template
```

### Vorlagen-Variablen

Nutze dynamische Variablen in Vorlagen:

```
Hello {{first_name}},

Welcome to {{company_name}}!

Your account: {{email}}
Plan: {{plan_type}}

Best regards,
The {{company_name}} Team
```

### Vorlagen testen

Teste Vorlagen vor dem Versand:

```
1. Click "Send Test"
2. Enter test email
3. Review email
4. Make adjustments
5. Send to list
```

## Kontaktmanagement

Organisiere und verwalte deine Abonnentenliste.

### Kontakte importieren

#### CSV-Import

```
1. Go to Contacts → Import
2. Upload CSV file
3. Map columns to fields
4. Review preview
5. Import
```

CSV-Format:
```
email,first_name,last_name,company,plan
john@example.com,John,Doe,Acme Inc,pro
jane@example.com,Jane,Smith,Tech Corp,free
```

#### API-Import

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

### Kontakte organisieren

#### Tags

Organisiere Kontakte mit Tags:

```
- "vip"
- "trial_user"
- "paying_customer"
- "inactive"
- "churned"
```

#### Segmente

Erstelle dynamische Segmente:

```
- Active users (opened email in last 30 days)
- High-value customers (spent > $1000)
- Trial users (signup < 14 days ago)
- Inactive (no activity > 60 days)
```

### Kontaktdaten

Speichere benutzerdefinierte Attribute:

```
- Unternehmen
- Jobtitel
- Branche
- Standort
- Plan-Typ
- Signup-Datum
- Letzter Kauf
- Lifetime Value
```

## Analysen & Reporting

Verfolge die E-Mail-Performance mit detaillierten Analysen.

### E-Mail-Metriken

- **Gesendet**: Gesamtzahl gesendeter E-Mails
- **Zugestellt**: Erfolgreich zugestellt
- **Bounced**: Hard-/Soft-Bounces
- **Geöffnet**: Eindeutige Opens
- **Geklickt**: Eindeutige Klicks
- **Abgemeldet**: Unsubscribe-Anfragen
- **Spam**: Spam-Beschwerden

### Kampagnen-Analytics

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

### Engagement-Tracking

Verfolge das Engagement einzelner Nutzer:

- E-Mail-Opens
- Link-Klicks
- Kaufhistorie
- Engagement-Score
- Datum der letzten Aktivität

### Individuelle Reports

Erstelle individuelle Reports:

```
1. Go to Reports → Create
2. Select metrics
3. Choose date range
4. Add filters
5. Generate report
6. Export as PDF/CSV
```

## Compliance & Zustellbarkeit

### DSGVO-Compliance

- ✓ Consent-Management
- ✓ Datenexport
- ✓ Recht auf Vergessenwerden
- ✓ Vorlagen für Datenschutzrichtlinien
- ✓ Audit-Logs

### CAN-SPAM-Compliance

- ✓ Klare Unsubscribe-Option
- ✓ Korrekte Absenderinformationen
- ✓ Ehrliche Betreffzeilen
- ✓ Physische Adresse erforderlich
- ✓ Unsubscribe innerhalb von 10 Tagen umgesetzt

### Zustellbarkeits-Features

- ✓ SPF/DKIM/DMARC-Setup
- ✓ Domain-Verifizierung
- ✓ Bounce-Management
- ✓ Spam-Testing
- ✓ Monitoring der IP-Reputation

## Integration

### Webhook-Events

Erhalte Benachrichtigungen in Echtzeit:

- E-Mail gesendet
- E-Mail zugestellt
- E-Mail geöffnet
- Link geklickt
- E-Mail gebounced
- Abgemeldet

### API-Integration

Integriere LiteStartup in deine Anwendung:

```php
// Send email via API
$response = $client->post('/emails/send', [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
]);
```

### Integrationen mit Drittanbietern

Verbinde dich mit beliebten Tools:

- Zapier
- Make (Integromat)
- IFTTT
- Slack
- Discord
- Benutzerdefinierte Webhooks

---

**Weiter:** Sieh dir die [Code Examples](/de/04-examples.md) oder [Pricing & Plans](/de/05-pricing.md) an!
