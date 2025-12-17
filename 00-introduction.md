# Introduction to LiteStartup
 
 LiteStartup (positioned on the website as *Lite Email for Startups*) is an **AI-driven email service platform** for startups that brings together **Workmail (business email)**, **transactional email**, and **marketing email** in one product, with a simple REST API to integrate in minutes.
 
 ## What is LiteStartup?
 
 LiteStartup is a SaaS email platform for startups. In one sentence:
 
 - **An AI-driven email service model** that streamlines your email workflow (content, automation, and delivery)
 - **A unified stack for business email + transactional email + marketing email**, reducing vendor sprawl
 - **Developer-friendly integration** via standard RESTful APIs (no complex SDKs)
 
 Unlike traditional email marketing platforms that charge per contact, LiteStartup emphasizes **pay per email sent**, so you pay for what you send—not for storing contacts.
 
 ## What Makes Us Different
 
 ### Workmail Like Gmail
 The ONLY email marketing platform with business email like `support@yourcompany.com` in minutes.
 
 ### AI Content Assistant
 AI generates marketing emails and A/B test variations to speed up writing and iteration.
 
 ### Affordable
 Pay per email sent, not per contact.
 
 - **Pro**: $20/month for 110,000 emails/month
 - **Overage**: $0.20 per 1,000 emails after limit
 
 ### Enterprise Infrastructure
 Built by AWS & Google Cloud engineers. 99.9% uptime with SOC2 & GDPR compliance.
 
 ### Free Email Notifications
 Get a free email like `yourname@litestartup.net` for alerts, reports, and updates to your preferred inbox.
 
 ### AI Website Builder
 Chat with AI to create landing pages, waitlist pages, newsletters, and blogs. No coding needed.
 
 ### Ticket + Live Chat
 Manage customer conversations with tickets (via email) and a real-time live chat widget.
 
 ### AI Automation
 Always-on automation: welcome, follow-up, and outreach emails, with built-in lead capture and growth workflows.
 
 ## Who Should Use LiteStartup?
 
 LiteStartup is ideal for:
 
 - **Early-stage startups** building their first customer base
 - **SaaS products** that need transactional + marketing email in one place
 - **Growth teams** that want AI-assisted content and faster experiments
 - **Product teams** managing landing pages and waitlists
 - **Developers** who prefer simple REST APIs with minimal dependencies
 - **Teams avoiding vendor lock-in** who want the option to switch providers later
 
 ## How LiteStartup Works
 
 ### 1. Sign Up
 Create an account and start with the Free plan (10,000 emails/month).
 
 ### 2. Get API Credentials
 Retrieve your API key from the dashboard.
 
 ### 3. Integrate
 Send emails via RESTful API calls. Works with any language or framework.
 
 ### 4. Send Emails
 Send transactional emails, marketing campaigns, or automated workflows.
 
 ### 5. Track & Optimize
 Monitor basic analytics and iterate with AI-assisted improvements.
 
 ## LiteStartup vs. Traditional Email Platforms
 
 | Feature | LiteStartup | Traditional Platforms |
 |---|---|---|
 | Workmail (Business Email) | ✓ Included | ✗ Separate service |
 | AI Content Assistant | ✓ Yes | ✗ No |
 | Pricing Model | Per email sent | Per contact |
 | Setup Time | 5 minutes | 30+ minutes |
 | API Integration | ✓ Simple REST API | ✓ Complex SDKs |
 | Vendor Lock-in | ✗ None | ✓ Yes |
 | Free Tier | 10K emails/month | Limited |
 | Uptime (website) | 99.9% | 99.9% |
 
 ## Getting Started
 
 Ready to start sending emails? Here's what to do next:
 
 1. **[Getting Started Guide](01-getting-started.md)** - Sign up and send your first email in minutes
 2. **[API Reference](02-api-reference.md)** - Complete API documentation and endpoints
 3. **[Features Guide](03-features.md)** - Explore all features in detail
 4. **[Code Examples](04-examples.md)** - Implementation examples in multiple languages
 5. **[Pricing & Plans](05-pricing.md)** - Understand pricing and billing
 
 ## Quick Start Example
 
 Send your first email in just a few lines of code:

 ```bash
 curl -X POST https://api.litestartup.com/client/v2/emails \
   -H "Authorization: Bearer YOUR_API_KEY" \
   -H "Content-Type: application/json" \
   -d '{
     "to": "user@example.com",
     "from": "noreply@yourapp.com",
     "subject": "Welcome!",
     "html": "<h1>Hello</h1>"
   }'
 ```

 ## Key Benefits
 
 - **Lower cost** - Pay per email sent, not per contact
 - **Higher productivity** - AI content assistance and AI automation reduce manual work
 - **All-in-one toolkit** - Workmail + sending + landing pages/waitlists + ticket/live chat
 - **Fast integration** - REST API with no complex SDK dependencies
 - **Less lock-in** - Standard APIs make switching providers easier
 
 ## Support & Resources
 
 - **Documentation**: Complete guides and API reference
 - **Code Examples**: Ready-to-use examples in multiple languages
 - **Community**: Connect with other LiteStartup users
 
 ## Next Steps
 
 - Get started with the [Getting Started Guide](01-getting-started.md)
 - Explore the [API Reference](02-api-reference.md)
 - Review [Code Examples](04-examples.md) for your programming language
 - Check [Pricing & Plans](05-pricing.md) to find the right plan

---
 
 **Ready to send your first email?** Start with the [Getting Started Guide](01-getting-started.md).
