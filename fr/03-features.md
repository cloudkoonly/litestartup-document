# Guide des fonctionnalités

Découvrez toutes les fonctionnalités puissantes que LiteStartup propose pour aider votre startup à réussir.

## Workmail - E-mail professionnel

LiteStartup inclut une fonctionnalité d’e-mail professionnel intégrée, ce qui élimine le besoin de services e-mail séparés comme Google Workspace.

### Qu’est-ce que Workmail ?

Workmail est un service d’e-mail professionnel complet, intégré directement à LiteStartup. Envoyez et recevez des e-mails depuis votre domaine personnalisé sans abonnements supplémentaires.

### Avantages

- **Économisez** : 72–144 $ par an et par membre de l’équipe (vs. Google Workspace)
- **Plateforme unifiée** : e-mail et marketing au même endroit
- **Image professionnelle** : utilisez votre domaine personnalisé
- **Fonctionnalités complètes** : transferts, alias, réponses automatiques

### Bien démarrer avec Workmail

1. Allez dans **Settings** → **Workmail**
2. Ajoutez votre domaine (par ex. `hello@yourdomain.com`)
3. Vérifiez les enregistrements DNS
4. Créez des comptes e-mail pour les membres de l’équipe
5. Commencez à envoyer et recevoir des e-mails

### Créer des comptes e-mail

```
1. Click "Add Email Account"
2. Enter username (e.g., "john")
3. Set password
4. Assign to team member
5. Click "Create"
```

L’adresse e-mail sera : `john@yourdomain.com`

### Transfert d’e-mails

Configurer le transfert automatique :

```
1. Go to email account settings
2. Click "Forwarding"
3. Enter forwarding address
4. Confirm forwarding
5. Emails now forward automatically
```

### Répondeurs automatiques

Configurer des réponses automatiques :

```
1. Go to email account settings
2. Click "Auto-Responder"
3. Enable auto-responder
4. Set message and date range
5. Save
```

## AI Content Assistant

L’assistant de contenu IA de LiteStartup vous aide à écrire de meilleurs e-mails plus rapidement.

### Fonctionnalités

- **Génération d’objets** : l’IA suggère des objets optimisés
- **Rédaction** : génération du contenu du corps de l’e-mail
- **Tests A/B** : création de variations pour tester
- **Ajustement du ton** : alignement sur la voix de votre marque
- **Optimisation** : suggestions pour améliorer les taux d’ouverture

### Utiliser l’assistant IA

#### Générer des objets

```
1. Click "AI Assistant" in email editor
2. Select "Generate Subject Lines"
3. Describe your email purpose
4. AI generates 5 variations
5. Click to use or regenerate
```

Exemple :
- Input: "Welcome email for new users"
- AI Suggestions:
  - "Welcome! Get started in 3 minutes"
  - "You're in! Here's what's next"
  - "Welcome aboard - your journey starts now"

#### Générer le contenu de l’e-mail

```
1. Click "AI Assistant"
2. Select "Generate Email Body"
3. Provide key points
4. Choose tone (professional, friendly, casual)
5. AI generates email content
6. Edit and customize as needed
```

#### Variations de test A/B

```
1. Click "AI Assistant"
2. Select "Create A/B Variations"
3. AI generates alternative versions
4. Choose which to test
5. LiteStartup tracks performance
```

### Conseils de rédaction avec l’IA

- ✓ Soyez précis sur votre objectif
- ✓ Mentionnez votre audience cible
- ✓ Indiquez le ton souhaité
- ✓ Donnez les informations clés à inclure
- ✓ Relisez et personnalisez les suggestions de l’IA

## Automatisation & workflows

Créez des workflows intelligents qui envoient automatiquement des e-mails en fonction du comportement des utilisateurs.

### Types de workflows

#### Série de bienvenue

Envoyez automatiquement une série d’e-mails aux nouveaux abonnés.

```
1. Allez dans Automation → Workflows
2. Cliquez sur "Create Workflow"
3. Sélectionnez "Welcome Series"
4. Ajoutez des e-mails (1 à 5)
5. Définissez les délais entre les e-mails
6. Activez le workflow
```

Exemple de série de bienvenue :
- Email 1: Welcome (immediate)
- Email 2: Getting Started (1 day later)
- Email 3: Feature Highlight (3 days later)
- Email 4: Success Story (7 days later)

#### Campagne de ré-engagement

Réactivez les abonnés inactifs.

```
1. Créez un workflow
2. Sélectionnez "Re-engagement"
3. Définissez le seuil d’inactivité (par ex. 30 jours)
4. Ajoutez des e-mails de ré-engagement
5. Définissez les actions de suivi
6. Activez
```

#### Campagne de reconquête

Ciblez les clients qui n’ont pas acheté récemment.

```
1. Créez un workflow
2. Sélectionnez "Win-back"
3. Définissez la période d’inactivité
4. Créez une offre attractive
5. Définissez le calendrier de relance
6. Activez
```

#### Récupération de panier abandonné

Rappelez aux clients les articles laissés dans le panier.

```
1. Créez un workflow
2. Sélectionnez "Abandoned Cart"
3. Définissez le délai (par ex. 1 heure)
4. Personnalisez l’e-mail avec les détails du produit
5. Ajoutez des e-mails de relance
6. Activez
```

### Déclencheurs de workflow

Les workflows peuvent être déclenchés par :

- **Actions utilisateur** : inscription, achat, téléchargement
- **Basés sur le temps** : date/heure spécifique, anniversaire
- **Comportementaux** : ouvertures, clics, inactivité
- **Personnalisés** : déclencheurs via API, webhooks

### Conditions du workflow

Ajoutez des conditions pour contrôler le déroulement du workflow :

```
IF user.plan == "pro" THEN send_email("pro_features")
IF user.location == "US" THEN send_email("us_offer")
IF user.opened_count > 5 THEN send_email("vip_offer")
```

### Analyses des workflows

Suivez les performances des workflows :

- E-mails envoyés
- Taux de délivrabilité
- Taux d’ouverture
- Taux de clic
- Taux de conversion
- Revenu généré

## Formulaires d’inscription

Développez votre liste d’abonnés grâce à des formulaires d’inscription intégrables.

### Créer un formulaire d’inscription

```
1. Allez dans Forms → Create Form
2. Choisissez le type de formulaire :
   - Simple signup
   - Double opt-in
   - Custom fields
3. Concevez le formulaire
4. Ajoutez des champs (e-mail, nom, champs personnalisés)
5. Définissez le message de confirmation
6. Récupérez le code d’intégration
```

### Types de formulaires

#### Inscription simple

Formulaire en une étape pour des inscriptions rapides.

```html
<iframe src="https://forms.litestartup.com/simple/form_id"></iframe>
```

#### Double opt-in

Confirmation en deux étapes pour la conformité.

```
1. L’utilisateur saisit son e-mail
2. Un e-mail de confirmation est envoyé
3. L’utilisateur clique sur le lien de confirmation
4. L’inscription est confirmée
```

#### Champs personnalisés

Collectez des informations supplémentaires :

```
- Email (required)
- Name (optional)
- Company (optional)
- Plan Interest (dropdown)
- Budget (multiple choice)
```

### Personnalisation du formulaire

- **Couleurs** : assorties à votre marque
- **Texte** : libellés et messages personnalisés
- **Champs** : ajouter/supprimer des champs
- **Redirection** : rediriger après inscription
- **Webhook** : envoyer les données vers votre système

### Intégrer les formulaires

#### Sur un site web

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

#### Sur une landing page

```html
<!-- Embed directly -->
<iframe src="https://forms.litestartup.com/form_id" 
        width="100%" height="500"></iframe>
```

#### Formulaire pop-up

```javascript
LiteStartup.showPopup('form_id', {
  trigger: 'exit', // Show on exit intent
  delay: 5000,     // Show after 5 seconds
  frequency: 'once' // Show once per session
});
```

## Gestion de liste d’attente

Créez de l’engouement avant le lancement grâce à la gestion de liste d’attente.

### Créer une liste d’attente

```
1. Allez dans Waitlist → Create Waitlist
2. Nommez votre liste d’attente
3. Définissez la date de lancement
4. Personnalisez la page d’inscription
5. Générez le lien d’inscription
6. Partagez-le avec votre audience
```

### Fonctionnalités de la liste d’attente

- **Suivi des parrainages** : les utilisateurs gagnent des places en parrainant des amis
- **Codes d’invitation** : envoyez des codes personnalisés
- **Classement** : affiche la position de l’utilisateur dans la liste d’attente
- **Notifications e-mail** : notification lors de l’invitation
- **Analytics** : suivi des sources d’inscription

### Programme de parrainage

Permettez aux utilisateurs d’obtenir un accès anticipé en parrainant des amis :

```
1. Activez le parrainage dans les paramètres de la liste d’attente
2. Les utilisateurs obtiennent un lien de parrainage unique
3. Chaque parrainage validé = 1 place gagnée
4. Un classement affiche les meilleurs parrains
5. Envoyez d’abord des invitations aux meilleurs parrains
```

### Envoyer des invitations

```
1. Allez dans Waitlist → Manage
2. Sélectionnez les utilisateurs à inviter
3. Générez des codes d’invitation
4. Envoyez les e-mails d’invitation
5. Suivez les acceptations
```

### Analyses de la liste d’attente

Suivez la croissance de la liste d’attente :

- Inscriptions totales
- Inscriptions via parrainage
- Taux de conversion
- Meilleurs parrains
- Sources d’inscription
- Répartition géographique

## Templates d’e-mails

Créez et gérez des templates d’e-mails réutilisables.

### Bibliothèque de templates

Accédez à des templates pré-conçus :

- Welcome emails
- Promotional emails
- Transactional emails
- Newsletter templates
- Event invitations
- Password reset

### Créer un template personnalisé

```
1. Allez dans Templates → Create
2. Choisissez une mise en page
3. Ajoutez des blocs de contenu
4. Insérez des variables ({{name}}, {{company}})
5. Prévisualisez
6. Enregistrez le template
```

### Variables de template

Utilisez des variables dynamiques dans les templates :

```
Hello {{first_name}},

Welcome to {{company_name}}!

Your account: {{email}}
Plan: {{plan_type}}

Best regards,
The {{company_name}} Team
```

### Test du template

Testez les templates avant l’envoi :

```
1. Cliquez sur "Send Test"
2. Saisissez l’e-mail de test
3. Vérifiez l’e-mail
4. Ajustez si nécessaire
5. Envoyez à la liste
```

## Gestion des contacts

Organisez et gérez votre liste d’abonnés.

### Importer des contacts

#### Import CSV

```
1. Go to Contacts → Import
2. Upload CSV file
3. Map columns to fields
4. Review preview
5. Import
```

Format CSV :
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

### Organiser les contacts

#### Tags

Organisez les contacts avec des tags :

```
- "vip"
- "trial_user"
- "paying_customer"
- "inactive"
- "churned"
```

#### Segments

Créez des segments dynamiques :

```
- Active users (opened email in last 30 days)
- High-value customers (spent > $1000)
- Trial users (signup < 14 days ago)
- Inactive (no activity > 60 days)
```

### Données de contact

Stockez des attributs personnalisés :

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

## Analyses & reporting

Suivez la performance des e-mails grâce à des analyses détaillées.

### Indicateurs e-mail

- **Sent**: Total emails sent
- **Delivered**: Successfully delivered
- **Bounced**: Hard/soft bounces
- **Opened**: Unique opens
- **Clicked**: Unique clicks
- **Unsubscribed**: Unsubscribe requests
- **Spam**: Spam complaints

### Analyses des campagnes

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

### Suivi de l’engagement

Suivez l’engagement individuel des utilisateurs :

- Ouvertures d’e-mails
- Clics sur les liens
- Historique d’achat
- Score d’engagement
- Date de dernière activité

### Rapports personnalisés

Créez des rapports personnalisés :

```
1. Allez dans Reports → Create
2. Sélectionnez les indicateurs
3. Choisissez la plage de dates
4. Ajoutez des filtres
5. Générez le rapport
6. Exportez en PDF/CSV
```

## Conformité & délivrabilité

### Conformité GDPR

- ✓ Gestion du consentement
- ✓ Export des données
- ✓ Droit à l’oubli
- ✓ Templates de politique de confidentialité
- ✓ Journaux d’audit

### Conformité CAN-SPAM

- ✓ Option de désinscription claire
- ✓ Informations expéditeur exactes
- ✓ Objets honnêtes
- ✓ Adresse postale requise
- ✓ Désinscription effective sous 10 jours

### Fonctionnalités de délivrabilité

- ✓ Configuration SPF/DKIM/DMARC
- ✓ Vérification du domaine
- ✓ Gestion des bounces
- ✓ Tests anti-spam
- ✓ Suivi de la réputation IP

## Intégration

### Événements webhook

Recevez des notifications en temps réel :

- E-mail envoyé
- E-mail livré
- E-mail ouvert
- Lien cliqué
- E-mail en bounce
- Désabonnement

### Intégration API

Intégrez à votre application :

```php
// Send email via API
$response = $client->post('/emails/send', [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
]);
```

### Intégrations tierces

Connectez-vous à des outils populaires :

- Zapier
- Make (Integromat)
- IFTTT
- Slack
- Discord
- Webhooks personnalisés

---

**Suite :** Consultez les [Exemples de code](/fr/04-examples.md) ou [Tarifs & offres](/fr/05-pricing.md) !
