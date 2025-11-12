# Features Guide

Explore all the powerful features LiteStartup offers to help your startup succeed.

## Workmail - Business Email

LiteStartup includes built-in business email functionality, eliminating the need for separate email services like Google Workspace.

### What is Workmail?

Workmail is a full-featured business email service integrated directly into LiteStartup. Send and receive emails from your custom domain without additional subscriptions.

### Benefits

- **Save Money**: $72-144 per year per team member (vs. Google Workspace)
- **Unified Platform**: Email and marketing in one place
- **Professional Image**: Use your custom domain
- **Full Features**: Forwarding, aliases, auto-responders

### Getting Started with Workmail

1. Go to **Settings** → **Workmail**
2. Add your domain (e.g., `hello@yourdomain.com`)
3. Verify DNS records
4. Create email accounts for team members
5. Start sending and receiving emails

### Create Email Accounts

```
1. Click "Add Email Account"
2. Enter username (e.g., "john")
3. Set password
4. Assign to team member
5. Click "Create"
```

Email address will be: `john@yourdomain.com`

### Email Forwarding

Set up automatic forwarding:

```
1. Go to email account settings
2. Click "Forwarding"
3. Enter forwarding address
4. Confirm forwarding
5. Emails now forward automatically
```

### Auto-Responders

Set up automatic replies:

```
1. Go to email account settings
2. Click "Auto-Responder"
3. Enable auto-responder
4. Set message and date range
5. Save
```

## AI Content Assistant

LiteStartup's AI Content Assistant helps you write better emails faster.

### Features

- **Subject Line Generation**: AI suggests optimized subject lines
- **Email Copy**: Generate email body content
- **A/B Testing**: Create variations for testing
- **Tone Adjustment**: Match your brand voice
- **Optimization**: Suggestions to improve open rates

### Using AI Assistant

#### Generate Subject Lines

```
1. Click "AI Assistant" in email editor
2. Select "Generate Subject Lines"
3. Describe your email purpose
4. AI generates 5 variations
5. Click to use or regenerate
```

Example:
- Input: "Welcome email for new users"
- AI Suggestions:
  - "Welcome! Get started in 3 minutes"
  - "You're in! Here's what's next"
  - "Welcome aboard - your journey starts now"

#### Generate Email Copy

```
1. Click "AI Assistant"
2. Select "Generate Email Body"
3. Provide key points
4. Choose tone (professional, friendly, casual)
5. AI generates email content
6. Edit and customize as needed
```

#### A/B Test Variations

```
1. Click "AI Assistant"
2. Select "Create A/B Variations"
3. AI generates alternative versions
4. Choose which to test
5. LiteStartup tracks performance
```

### AI Writing Tips

- ✓ Be specific about your goal
- ✓ Mention your target audience
- ✓ Specify desired tone
- ✓ Provide key information to include
- ✓ Review and customize AI suggestions

## Automation & Workflows

Create intelligent workflows that automatically send emails based on user behavior.

### Workflow Types

#### Welcome Series

Automatically send a series of emails to new subscribers.

```
1. Go to Automation → Workflows
2. Click "Create Workflow"
3. Select "Welcome Series"
4. Add emails (1-5 emails)
5. Set delays between emails
6. Activate workflow
```

Example Welcome Series:
- Email 1: Welcome (immediate)
- Email 2: Getting Started (1 day later)
- Email 3: Feature Highlight (3 days later)
- Email 4: Success Story (7 days later)

#### Re-engagement Campaign

Win back inactive subscribers.

```
1. Create workflow
2. Select "Re-engagement"
3. Set inactivity threshold (e.g., 30 days)
4. Add re-engagement emails
5. Set follow-up actions
6. Activate
```

#### Win-back Campaign

Target customers who haven't purchased recently.

```
1. Create workflow
2. Select "Win-back"
3. Define inactive period
4. Create compelling offer
5. Set retry schedule
6. Activate
```

#### Abandoned Cart Recovery

Remind customers about items left in cart.

```
1. Create workflow
2. Select "Abandoned Cart"
3. Set delay (e.g., 1 hour)
4. Customize email with product details
5. Add follow-up emails
6. Activate
```

### Workflow Triggers

Workflows can be triggered by:

- **User Actions**: Signup, purchase, download
- **Time-based**: Specific date/time, anniversary
- **Behavioral**: Opens, clicks, inactivity
- **Custom**: API triggers, webhooks

### Workflow Conditions

Add conditions to control workflow flow:

```
IF user.plan == "pro" THEN send_email("pro_features")
IF user.location == "US" THEN send_email("us_offer")
IF user.opened_count > 5 THEN send_email("vip_offer")
```

### Workflow Analytics

Monitor workflow performance:

- Emails sent
- Delivery rate
- Open rate
- Click rate
- Conversion rate
- Revenue generated

## Subscription Forms

Build your subscriber list with embedded signup forms.

### Create Subscription Form

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

### Form Types

#### Simple Signup

Single-step form for quick signups.

```html
<iframe src="https://forms.litestartup.com/simple/form_id"></iframe>
```

#### Double Opt-in

Two-step confirmation for compliance.

```
1. User enters email
2. Confirmation email sent
3. User clicks confirmation link
4. Subscription confirmed
```

#### Custom Fields

Collect additional information:

```
- Email (required)
- Name (optional)
- Company (optional)
- Plan Interest (dropdown)
- Budget (multiple choice)
```

### Form Customization

- **Colors**: Match your brand
- **Text**: Custom labels and messages
- **Fields**: Add/remove fields
- **Redirect**: Redirect after signup
- **Webhook**: Send data to your system

### Embed Forms

#### On Website

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

#### On Landing Page

```html
<!-- Embed directly -->
<iframe src="https://forms.litestartup.com/form_id" 
        width="100%" height="500"></iframe>
```

#### Popup Form

```javascript
LiteStartup.showPopup('form_id', {
  trigger: 'exit', // Show on exit intent
  delay: 5000,     // Show after 5 seconds
  frequency: 'once' // Show once per session
});
```

## Waitlist Management

Build hype before launch with waitlist management.

### Create Waitlist

```
1. Go to Waitlist → Create Waitlist
2. Name your waitlist
3. Set launch date
4. Customize signup page
5. Generate signup link
6. Share with audience
```

### Waitlist Features

- **Referral Tracking**: Users earn spots by referring friends
- **Invite Codes**: Send personalized invite codes
- **Ranking**: Show user's position on waitlist
- **Email Notifications**: Notify when invited
- **Analytics**: Track signup sources

### Referral Program

Enable users to earn early access by referring friends:

```
1. Enable referral in waitlist settings
2. Users get unique referral link
3. Each successful referral = 1 spot
4. Leaderboard shows top referrers
5. Send invites to top referrers first
```

### Send Invites

```
1. Go to Waitlist → Manage
2. Select users to invite
3. Generate invite codes
4. Send invite emails
5. Track acceptance
```

### Waitlist Analytics

Monitor waitlist growth:

- Total signups
- Referral signups
- Conversion rate
- Top referrers
- Signup sources
- Geographic distribution

## Email Templates

Create and manage reusable email templates.

### Template Library

Access pre-built templates:

- Welcome emails
- Promotional emails
- Transactional emails
- Newsletter templates
- Event invitations
- Password reset

### Create Custom Template

```
1. Go to Templates → Create
2. Choose layout
3. Add content blocks
4. Insert variables ({{name}}, {{company}})
5. Preview
6. Save template
```

### Template Variables

Use dynamic variables in templates:

```
Hello {{first_name}},

Welcome to {{company_name}}!

Your account: {{email}}
Plan: {{plan_type}}

Best regards,
The {{company_name}} Team
```

### Template Testing

Test templates before sending:

```
1. Click "Send Test"
2. Enter test email
3. Review email
4. Make adjustments
5. Send to list
```

## Contact Management

Organize and manage your subscriber list.

### Import Contacts

#### CSV Import

```
1. Go to Contacts → Import
2. Upload CSV file
3. Map columns to fields
4. Review preview
5. Import
```

CSV Format:
```
email,first_name,last_name,company,plan
john@example.com,John,Doe,Acme Inc,pro
jane@example.com,Jane,Smith,Tech Corp,free
```

#### API Import

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

### Organize Contacts

#### Tags

Organize contacts with tags:

```
- "vip"
- "trial_user"
- "paying_customer"
- "inactive"
- "churned"
```

#### Segments

Create dynamic segments:

```
- Active users (opened email in last 30 days)
- High-value customers (spent > $1000)
- Trial users (signup < 14 days ago)
- Inactive (no activity > 60 days)
```

### Contact Data

Store custom attributes:

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

## Analytics & Reporting

Track email performance with detailed analytics.

### Email Metrics

- **Sent**: Total emails sent
- **Delivered**: Successfully delivered
- **Bounced**: Hard/soft bounces
- **Opened**: Unique opens
- **Clicked**: Unique clicks
- **Unsubscribed**: Unsubscribe requests
- **Spam**: Spam complaints

### Campaign Analytics

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

### Engagement Tracking

Track individual user engagement:

- Email opens
- Link clicks
- Purchase history
- Engagement score
- Last activity date

### Custom Reports

Create custom reports:

```
1. Go to Reports → Create
2. Select metrics
3. Choose date range
4. Add filters
5. Generate report
6. Export as PDF/CSV
```

## Compliance & Deliverability

### GDPR Compliance

- ✓ Consent management
- ✓ Data export
- ✓ Right to be forgotten
- ✓ Privacy policy templates
- ✓ Audit logs

### CAN-SPAM Compliance

- ✓ Clear unsubscribe option
- ✓ Accurate sender information
- ✓ Honest subject lines
- ✓ Physical address required
- ✓ Unsubscribe honored within 10 days

### Deliverability Features

- ✓ SPF/DKIM/DMARC setup
- ✓ Domain verification
- ✓ Bounce management
- ✓ Spam testing
- ✓ IP reputation monitoring

## Integration

### Webhook Events

Receive real-time notifications:

- Email sent
- Email delivered
- Email opened
- Link clicked
- Email bounced
- Unsubscribed

### API Integration

Integrate with your application:

```php
// Send email via API
$response = $client->post('/emails/send', [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
]);
```

### Third-party Integrations

Connect with popular tools:

- Zapier
- Make (Integromat)
- IFTTT
- Slack
- Discord
- Custom webhooks

---

**Next:** Check [Code Examples](04-examples.md) or [Pricing & Plans](05-pricing.md)!
