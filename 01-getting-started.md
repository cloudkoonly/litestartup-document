# Getting Started with LiteStartup

Get up and running with LiteStartup in just 5 minutes. This guide walks you through signing up, setting up your API key, and sending your first email.

## Prerequisites

Before you begin, you'll need:

- A valid email address
- A web browser
- Basic knowledge of REST APIs (for integration)
- Your application's domain or a test domain

## Step 1: Sign Up for Free

### Create Your Account

1. Visit [LiteStartup.com](https://www.litestartup.com)
2. Click **"Start Free Today"** button
3. Enter your email address
4. Create a strong password
5. Click **"Sign Up"**

You'll receive a confirmation email. Click the link to verify your account.

### What You Get

- **Free Plan**: 10,000 emails per month
- **Full API Access**: All features available
- **No Credit Card Required**: Start completely free
- **Upgrade Anytime**: Scale up as you grow

## Step 2: Set Up Your API Key

### Generate API Credentials

1. Log in to your LiteStartup dashboard
2. Navigate to **Settings** → **API Keys**
3. Click **"Generate New API Key"**
4. Give your key a descriptive name (e.g., "Production API Key")
5. Click **"Create"**

Your API key will be displayed once. **Copy it immediately and store it securely** - you won't be able to see it again.

### Secure Your API Key

**Important**: Never share your API key or commit it to version control.

Store it as an environment variable:

```bash
# .env file
LITESTARTUP_API_KEY=sk_live_xxxxxxxxxxxxx
```

Or in your application configuration:

```php
$apiKey = getenv('LITESTARTUP_API_KEY');
```

```python
import os
api_key = os.getenv('LITESTARTUP_API_KEY')
```

```javascript
const apiKey = process.env.LITESTARTUP_API_KEY;
```

## Step 3: Configure Your Sender Email

### Add a Sender Domain

1. Go to **Settings** → **Domains**
2. Click **"Add Domain"**
3. Enter your domain (e.g., `hello@yourdomain.com`)
4. Follow the DNS verification steps:
   - Add the provided DNS records to your domain
   - Wait for verification (usually 5-15 minutes)
5. Once verified, you can send from this domain

### Verify Your Sender Email

For testing, you can use:

```
test@litestartup.com
```

This is a test domain that works immediately without DNS verification.

## Step 4: Send Your First Email

### Using cURL

```bash
curl -X POST https://api.litestartup.com/emails/send \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "to": "recipient@example.com",
    "from": "hello@yourdomain.com",
    "subject": "Welcome to LiteStartup!",
    "html": "<h1>Hello!</h1><p>Your first email with LiteStartup.</p>",
    "text": "Hello! Your first email with LiteStartup."
  }'
```

### Using PHP

```php
<?php
$apiKey = 'YOUR_API_KEY';
$url = 'https://api.litestartup.com/emails/send';

$data = [
    'to' => 'recipient@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome to LiteStartup!',
    'html' => '<h1>Hello!</h1><p>Your first email with LiteStartup.</p>',
    'text' => 'Hello! Your first email with LiteStartup.'
];

$ch = curl_init($url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, [
    'Authorization: Bearer ' . $apiKey,
    'Content-Type: application/json'
]);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));

$response = curl_exec($ch);
$result = json_decode($response, true);

if ($result['success']) {
    echo "Email sent successfully!";
} else {
    echo "Error: " . $result['error'];
}
?>
```

### Using Python

```python
import requests
import json

api_key = 'YOUR_API_KEY'
url = 'https://api.litestartup.com/emails/send'

headers = {
    'Authorization': f'Bearer {api_key}',
    'Content-Type': 'application/json'
}

data = {
    'to': 'recipient@example.com',
    'from': 'hello@yourdomain.com',
    'subject': 'Welcome to LiteStartup!',
    'html': '<h1>Hello!</h1><p>Your first email with LiteStartup.</p>',
    'text': 'Hello! Your first email with LiteStartup.'
}

response = requests.post(url, headers=headers, json=data)
result = response.json()

if result['success']:
    print("Email sent successfully!")
else:
    print(f"Error: {result['error']}")
```

### Using Node.js

```javascript
const https = require('https');

const apiKey = 'YOUR_API_KEY';
const url = 'https://api.litestartup.com/emails/send';

const data = JSON.stringify({
  to: 'recipient@example.com',
  from: 'hello@yourdomain.com',
  subject: 'Welcome to LiteStartup!',
  html: '<h1>Hello!</h1><p>Your first email with LiteStartup.</p>',
  text: 'Hello! Your first email with LiteStartup.'
});

const options = {
  hostname: 'api.litestartup.com',
  path: '/emails/send',
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${apiKey}`,
    'Content-Type': 'application/json',
    'Content-Length': data.length
  }
};

const req = https.request(options, (res) => {
  let responseData = '';
  
  res.on('data', (chunk) => {
    responseData += chunk;
  });
  
  res.on('end', () => {
    const result = JSON.parse(responseData);
    if (result.success) {
      console.log('Email sent successfully!');
    } else {
      console.log(`Error: ${result.error}`);
    }
  });
});

req.on('error', (error) => {
  console.error(error);
});

req.write(data);
req.end();
```

## Step 5: Check Your Dashboard

### Monitor Email Status

1. Log in to your LiteStartup dashboard
2. Go to **Emails** section
3. You should see your sent email with:
   - Delivery status
   - Open tracking (if enabled)
   - Click tracking (if enabled)
   - Timestamp

### View Email Details

Click on any email to see:
- Recipient address
- Subject line
- Send time
- Delivery status
- Open/click events
- Any errors

## Common Issues & Solutions

### "Invalid API Key" Error

**Problem**: You're getting an authentication error.

**Solution**:
- Verify your API key is correct
- Check that you're using `Bearer` prefix: `Authorization: Bearer YOUR_KEY`
- Ensure the key hasn't expired
- Generate a new key if needed

### "Domain Not Verified" Error

**Problem**: You can't send from your domain.

**Solution**:
- Go to **Settings** → **Domains**
- Check if your domain shows as "Verified"
- If not, verify the DNS records were added correctly
- Wait 5-15 minutes for DNS propagation
- Use `test@litestartup.com` for testing

### "Rate Limit Exceeded" Error

**Problem**: You've sent too many emails too quickly.

**Solution**:
- Wait a few seconds before sending more emails
- Upgrade to a higher plan for higher rate limits
- Implement exponential backoff in your code

### Email Not Received

**Problem**: The recipient didn't receive the email.

**Solution**:
- Check the email was delivered (status = "delivered" in dashboard)
- Ask recipient to check spam folder
- Verify sender domain is authenticated
- Check recipient email address is correct
- Review email content for spam triggers

## Next Steps

Now that you've sent your first email, explore:

1. **[API Reference](02-api-reference.md)** - Learn all available endpoints
2. **[Features Guide](03-features.md)** - Explore advanced features
3. **[Code Examples](04-examples.md)** - See more implementation examples
4. **[Pricing & Plans](05-pricing.md)** - Understand billing and upgrade options

## Best Practices

### Email Content

- ✓ Always include both HTML and text versions
- ✓ Use clear, descriptive subject lines
- ✓ Include an unsubscribe link for marketing emails
- ✓ Test emails before sending to large lists
- ✓ Use AI Content Assistant to optimize subject lines

### Integration

- ✓ Store API key in environment variables
- ✓ Implement error handling and retries
- ✓ Log email send events for debugging
- ✓ Monitor delivery rates and bounce rates
- ✓ Use webhooks to track email events

### Security

- ✓ Never hardcode API keys
- ✓ Rotate API keys periodically
- ✓ Use HTTPS for all API calls
- ✓ Validate email addresses before sending
- ✓ Implement rate limiting on your end

## Troubleshooting

### Need Help?

- Check the [API Reference](02-api-reference.md) for detailed documentation
- Review [Code Examples](04-examples.md) for your programming language
- See [Features Guide](03-features.md) for feature-specific help
- Contact support through your dashboard

---

**Ready to explore more?** Check out the [API Reference](02-api-reference.md) or [Code Examples](04-examples.md)!
