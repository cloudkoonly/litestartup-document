# Introduction to LiteStartup

LiteStartup is a smart email marketing platform built specifically for startups. It combines the power of a business email service (workmail), AI-powered content generation, and reliable email delivery into one affordable, easy-to-use platform.

## What is LiteStartup?

LiteStartup is a SaaS (Software as a Service) email platform that helps startups:

- **Send marketing emails** with built-in AI content assistance
- **Manage business email** with workmail functionality (like Gmail)
- **Automate campaigns** with intelligent workflows
- **Build subscriber lists** with embedded signup forms
- **Manage waitlists** before product launch
- **Integrate easily** via REST API in minutes

Unlike traditional email marketing platforms that charge per contact, LiteStartup charges per email sent. This means you can import unlimited contacts and only pay for the emails you actually send.

## Key Features

### Workmail Like Gmail
The only email marketing platform with built-in business email. No need for separate Google Workspace subscriptions. Save $72-144 per year per team member.

### AI Content Assistant
Automatically generate subject lines, email copy, and A/B test variations. Write emails 10x faster with 10x better open rates. From idea to send in just 1 minute.

### Affordable Pricing
- **Free Plan**: 10,000 emails per month
- **Pro Plan**: 110,000 emails per month for $20/month
- **Pay-as-you-go**: $0.20 per 1,000 emails after your plan limit
- **No per-contact fees**: Import 100K contacts, only pay for emails sent

### Unlimited Contacts
Import and manage unlimited contacts. Pay only for emails sent, not for storing contacts. Full data ownership with CSV import/export.

### Enterprise Infrastructure
Built by AWS & Google Cloud engineers. 99.99% uptime with SOC2 & GDPR compliance. Startup prices with enterprise-grade reliability.

### Smart Automation
- **Waitlist Management**: Collect emails, send invite codes, convert waitlist to customers automatically
- **Subscription Forms**: Embeddable signup forms with double opt-in, embed anywhere in 30 seconds
- **AI Automation**: Smart workflows triggered by user behavior - welcome series, re-engagement, win-back campaigns

### Zero Vendor Lock-in
Use standard REST APIs. Switch providers anytime without code changes. Works with any programming language or framework.

## Who Should Use LiteStartup?

LiteStartup is ideal for:

- **Early-stage startups** building their first customer base
- **SaaS companies** needing reliable transactional email
- **Growth teams** running email marketing campaigns
- **Product teams** managing waitlists and early access
- **Developers** who want simple API integration without complexity
- **Businesses** looking for affordable email solutions without vendor lock-in

## How LiteStartup Works

### 1. Sign Up
Create a free account and get started immediately with 10,000 free emails per month.

### 2. Get API Credentials
Retrieve your API key from the dashboard in seconds.

### 3. Integrate
Use the simple REST API to send emails from your application. Works with any programming language.

### 4. Send Emails
Start sending transactional emails, marketing campaigns, or automated workflows.

### 5. Track & Optimize
Monitor delivery, opens, clicks, and use AI suggestions to improve performance.

## LiteStartup vs. Traditional Email Platforms

| Feature | LiteStartup | Traditional Platforms |
|---------|-------------|----------------------|
| Workmail (Business Email) | ✓ Included | ✗ Separate service |
| AI Content Assistant | ✓ Yes | ✗ No |
| Pricing Model | Per email sent | Per contact |
| Setup Time | 5 minutes | 30+ minutes |
| API Integration | ✓ Simple REST API | ✓ Complex SDKs |
| Vendor Lock-in | ✗ None | ✓ Yes |
| Free Tier | 10K emails/month | Limited |
| Uptime SLA | 99.99% | 99.9% |

## Getting Started

Ready to start sending emails? Here's what to do next:

1. **[Getting Started Guide](01-getting-started.md)** - Sign up and send your first email in 5 minutes
2. **[API Reference](02-api-reference.md)** - Complete API documentation and endpoints
3. **[Features Guide](03-features.md)** - Explore all features in detail
4. **[Code Examples](04-examples.md)** - Implementation examples in multiple languages
5. **[Pricing & Plans](05-pricing.md)** - Understand pricing and billing

## Quick Start Example

Send your first email in just a few lines of code:

```bash
curl -X POST https://api.litestartup.com/emails/send \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "to": "user@example.com",
    "from": "hello@yourdomain.com",
    "subject": "Welcome to LiteStartup!",
    "html": "<h1>Hello!</h1><p>Welcome to our platform.</p>",
    "text": "Hello! Welcome to our platform."
  }'
```

## Key Benefits

✓ **Save Money** - Pay only for emails sent, not per contact
✓ **Save Time** - AI generates content, setup takes 5 minutes
✓ **Enterprise Reliability** - 99.99% uptime, SOC2 & GDPR compliant
✓ **No Lock-in** - Standard REST API, switch anytime
✓ **Built for Startups** - Affordable pricing, startup-friendly features
✓ **Easy Integration** - Works with any language or framework

## Support & Resources

- **Documentation**: Complete guides and API reference
- **Code Examples**: Ready-to-use examples in multiple languages
- **API Status**: Real-time status of our infrastructure
- **Community**: Connect with other LiteStartup users

## Next Steps

- Get started with the [Getting Started Guide](01-getting-started.md)
- Explore the [API Reference](02-api-reference.md)
- Review [Code Examples](04-examples.md) for your programming language
- Check [Pricing & Plans](05-pricing.md) to find the right plan

---

**Ready to send your first email?** Start with the [Getting Started Guide](01-getting-started.md)!
