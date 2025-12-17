# Guida alle funzionalità

Esplora tutte le potenti funzionalità che LiteStartup offre per aiutare la tua startup ad avere successo.

## Workmail - E-mail aziendale

LiteStartup include funzionalità di e-mail aziendale integrate, eliminando la necessità di servizi separati come Google Workspace.

### Che cos’è Workmail?

Workmail è un servizio di e-mail aziendale completo, integrato direttamente in LiteStartup. Invia e ricevi e-mail dal tuo dominio personalizzato senza abbonamenti aggiuntivi.

### Vantaggi

- **Risparmia**: $72-144 all’anno per membro del team (vs. Google Workspace)
- **Piattaforma unificata**: e-mail e marketing in un unico posto
- **Immagine professionale**: usa il tuo dominio personalizzato
- **Funzionalità complete**: inoltro, alias, risponditori automatici

### Iniziare con Workmail

1. Vai in **Settings** → **Workmail**
2. Aggiungi il tuo dominio (ad es. `hello@yourdomain.com`)
3. Verifica i record DNS
4. Crea gli account e-mail per i membri del team
5. Inizia a inviare e ricevere e-mail

### Crea account e-mail

```
1. Click "Add Email Account"
2. Enter username (e.g., "john")
3. Set password
4. Assign to team member
5. Click "Create"
```

L’indirizzo e-mail sarà: `john@yourdomain.com`

### Inoltro e-mail

Configura l’inoltro automatico:

```
1. Go to email account settings
2. Click "Forwarding"
3. Enter forwarding address
4. Confirm forwarding
5. Emails now forward automatically
```

### Risponditori automatici

Configura le risposte automatiche:

```
1. Go to email account settings
2. Click "Auto-Responder"
3. Enable auto-responder
4. Set message and date range
5. Save
```

## AI Content Assistant

L’AI Content Assistant di LiteStartup ti aiuta a scrivere e-mail migliori più velocemente.

### Funzionalità

- **Generazione oggetti**: l’IA suggerisce oggetti ottimizzati
- **Testo dell’e-mail**: genera contenuti per il corpo dell’e-mail
- **A/B testing**: crea varianti per i test
- **Regolazione del tono**: allinea il testo alla voce del tuo brand
- **Ottimizzazione**: suggerimenti per migliorare gli open rate

### Usare l’assistente IA

#### Generare oggetti

```
1. Click "AI Assistant" in email editor
2. Select "Generate Subject Lines"
3. Describe your email purpose
4. AI generates 5 variations
5. Click to use or regenerate
```

Esempio:
- Input: "Welcome email for new users"
- Suggerimenti IA:
  - "Welcome! Get started in 3 minutes"
  - "You're in! Here's what's next"
  - "Welcome aboard - your journey starts now"

#### Generare il testo dell’e-mail

```
1. Click "AI Assistant"
2. Select "Generate Email Body"
3. Provide key points
4. Choose tone (professional, friendly, casual)
5. AI generates email content
6. Edit and customize as needed
```

#### Varianti per test A/B

```
1. Click "AI Assistant"
2. Select "Create A/B Variations"
3. AI generates alternative versions
4. Choose which to test
5. LiteStartup tracks performance
```

### Consigli di scrittura con IA

- ✓ Sii specifico sul tuo obiettivo
- ✓ Indica il tuo pubblico target
- ✓ Specifica il tono desiderato
- ✓ Fornisci le informazioni chiave da includere
- ✓ Rivedi e personalizza i suggerimenti dell’IA

## Automazione e workflow

Crea workflow intelligenti che inviano automaticamente e-mail in base al comportamento degli utenti.

### Tipi di workflow

#### Serie di benvenuto

Invia automaticamente una serie di e-mail ai nuovi iscritti.

```
1. Go to Automation → Workflows
2. Click "Create Workflow"
3. Select "Welcome Series"
4. Add emails (1-5 emails)
5. Set delays between emails
6. Activate workflow
```

Esempio di serie di benvenuto:
- Email 1: Welcome (immediate)
- Email 2: Getting Started (1 day later)
- Email 3: Feature Highlight (3 days later)
- Email 4: Success Story (7 days later)

#### Campagna di riattivazione

Recupera gli iscritti inattivi.

```
1. Create workflow
2. Select "Re-engagement"
3. Set inactivity threshold (e.g., 30 days)
4. Add re-engagement emails
5. Set follow-up actions
6. Activate
```

#### Campagna win-back

Rivolgiti ai clienti che non acquistano da tempo.

```
1. Create workflow
2. Select "Win-back"
3. Define inactive period
4. Create compelling offer
5. Set retry schedule
6. Activate
```

#### Recupero carrello abbandonato

Ricorda ai clienti gli articoli lasciati nel carrello.

```
1. Create workflow
2. Select "Abandoned Cart"
3. Set delay (e.g., 1 hour)
4. Customize email with product details
5. Add follow-up emails
6. Activate
```

### Trigger dei workflow

I workflow possono essere attivati da:

- **Azioni utente**: signup, acquisto, download
- **Basati sul tempo**: data/ora specifica, anniversario
- **Comportamentali**: aperture, clic, inattività
- **Personalizzati**: trigger API, webhook

### Condizioni dei workflow

Aggiungi condizioni per controllare il flusso del workflow:

```
IF user.plan == "pro" THEN send_email("pro_features")
IF user.location == "US" THEN send_email("us_offer")
IF user.opened_count > 5 THEN send_email("vip_offer")
```

### Analytics dei workflow

Monitora le prestazioni del workflow:

- E-mail inviate
- Tasso di consegna
- Tasso di apertura
- Tasso di clic
- Tasso di conversione
- Ricavi generati

## Moduli di iscrizione

Costruisci la tua lista iscritti con moduli di registrazione incorporabili.

### Crea un modulo di iscrizione

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

### Tipi di modulo

#### Iscrizione semplice

Modulo a singolo passaggio per iscrizioni rapide.

```html
<iframe src="https://forms.litestartup.com/simple/form_id"></iframe>
```

#### Double opt-in

Conferma in due passaggi per la conformità.

```
1. User enters email
2. Confirmation email sent
3. User clicks confirmation link
4. Subscription confirmed
```

#### Campi personalizzati

Raccogli informazioni aggiuntive:

```
- Email (required)
- Name (optional)
- Company (optional)
- Plan Interest (dropdown)
- Budget (multiple choice)
```

### Personalizzazione del modulo

- **Colori**: in linea con il tuo brand
- **Testo**: etichette e messaggi personalizzati
- **Campi**: aggiungi/rimuovi campi
- **Redirect**: reindirizzamento dopo l’iscrizione
- **Webhook**: invia i dati al tuo sistema

### Incorporare i moduli

#### Sul sito

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

#### Su landing page

```html
<!-- Embed directly -->
<iframe src="https://forms.litestartup.com/form_id" 
        width="100%" height="500"></iframe>
```

#### Modulo popup

```javascript
LiteStartup.showPopup('form_id', {
  trigger: 'exit', // Show on exit intent
  delay: 5000,     // Show after 5 seconds
  frequency: 'once' // Show once per session
});
```

## Gestione della waitlist

Crea aspettativa prima del lancio con la gestione della waitlist.

### Crea una waitlist

```
1. Go to Waitlist → Create Waitlist
2. Name your waitlist
3. Set launch date
4. Customize signup page
5. Generate signup link
6. Share with audience
```

### Funzionalità della waitlist

- **Tracciamento referral**: gli utenti guadagnano posizioni invitando amici
- **Codici invito**: invia codici invito personalizzati
- **Ranking**: mostra la posizione dell’utente in waitlist
- **Notifiche e-mail**: avvisa quando l’utente viene invitato
- **Analytics**: traccia le sorgenti di iscrizione

### Programma referral

Permetti agli utenti di ottenere accesso anticipato invitando amici:

```
1. Enable referral in waitlist settings
2. Users get unique referral link
3. Each successful referral = 1 spot
4. Leaderboard shows top referrers
5. Send invites to top referrers first
```

### Invia inviti

```
1. Go to Waitlist → Manage
2. Select users to invite
3. Generate invite codes
4. Send invite emails
5. Track acceptance
```

### Analytics della waitlist

Monitora la crescita della waitlist:

- Iscrizioni totali
- Iscrizioni da referral
- Tasso di conversione
- Migliori referrer
- Sorgenti di iscrizione
- Distribuzione geografica

## Template e-mail

Crea e gestisci template e-mail riutilizzabili.

### Libreria template

Accedi a template predefiniti:

- E-mail di benvenuto
- E-mail promozionali
- E-mail transazionali
- Template newsletter
- Inviti a eventi
- Reset password

### Crea un template personalizzato

```
1. Go to Templates → Create
2. Choose layout
3. Add content blocks
4. Insert variables ({{name}}, {{company}})
5. Preview
6. Save template
```

### Variabili del template

Usa variabili dinamiche nei template:

```
Hello {{first_name}},

Welcome to {{company_name}}!

Your account: {{email}}
Plan: {{plan_type}}

Best regards,
The {{company_name}} Team
```

### Test dei template

Testa i template prima dell’invio:

```
1. Click "Send Test"
2. Enter test email
3. Review email
4. Make adjustments
5. Send to list
```

## Gestione contatti

Organizza e gestisci la tua lista iscritti.

### Importa contatti

#### Import CSV

```
1. Go to Contacts → Import
2. Upload CSV file
3. Map columns to fields
4. Review preview
5. Import
```

Formato CSV:
```
email,first_name,last_name,company,plan
john@example.com,John,Doe,Acme Inc,pro
jane@example.com,Jane,Smith,Tech Corp,free
```

#### Import via API

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

### Organizza i contatti

#### Tag

Organizza i contatti con i tag:

```
- "vip"
- "trial_user"
- "paying_customer"
- "inactive"
- "churned"
```

#### Segmenti

Crea segmenti dinamici:

```
- Active users (opened email in last 30 days)
- High-value customers (spent > $1000)
- Trial users (signup < 14 days ago)
- Inactive (no activity > 60 days)
```

### Dati del contatto

Memorizza attributi personalizzati:

```
- Company
- Job title
- Industry
- Location
- Plan type
- Signup date
- Last purchase
- Lifetime value
```

## Analytics e report

Monitora le prestazioni delle e-mail con analytics dettagliate.

### Metriche e-mail

- **Inviate (Sent)**: totale e-mail inviate
- **Consegnate (Delivered)**: consegnate con successo
- **Rimbalzate (Bounced)**: bounce hard/soft
- **Aperte (Opened)**: aperture uniche
- **Cliccate (Clicked)**: clic unici
- **Disiscritte (Unsubscribed)**: richieste di disiscrizione
- **Spam**: segnalazioni spam

### Analytics delle campagne

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

### Tracciamento dell’engagement

Traccia l’engagement del singolo utente:

- Aperture e-mail
- Clic sui link
- Storico acquisti
- Punteggio di engagement
- Data ultima attività

### Report personalizzati

Crea report personalizzati:

```
1. Go to Reports → Create
2. Select metrics
3. Choose date range
4. Add filters
5. Generate report
6. Export as PDF/CSV
```

## Conformità e deliverability

### Conformità GDPR

- ✓ Gestione del consenso
- ✓ Esportazione dei dati
- ✓ Diritto all’oblio
- ✓ Template di privacy policy
- ✓ Log di audit

### Conformità CAN-SPAM

- ✓ Opzione di disiscrizione chiara
- ✓ Informazioni mittente accurate
- ✓ Oggetti onesti
- ✓ Indirizzo fisico richiesto
- ✓ Disiscrizione rispettata entro 10 giorni

### Funzionalità di deliverability

- ✓ Configurazione SPF/DKIM/DMARC
- ✓ Verifica dominio
- ✓ Gestione bounce
- ✓ Test antispam
- ✓ Monitoraggio reputazione IP

## Integrazione

### Eventi webhook

Ricevi notifiche in tempo reale:

- E-mail inviata
- E-mail consegnata
- E-mail aperta
- Link cliccato
- E-mail rimbalzata (bounce)
- Disiscrizione

### Integrazione API

Integra con la tua applicazione:

```php
// Send email via API
$response = $client->post('/emails/send', [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
]);
```

### Integrazioni di terze parti

Connetti strumenti popolari:

- Zapier
- Make (Integromat)
- IFTTT
- Slack
- Discord
- Webhook personalizzati

---

**Successivo:** Consulta [Esempi di codice](/it/04-examples.md) o [Prezzi e piani](/it/05-pricing.md)!
