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
2. Click a **Get Started / Sign Up** button to open the signup page
3. Or go directly to the signup page: https://app.litestartup.com/signup?
4. Enter your email address
5. Create a strong password
6. Complete the signup flow

You'll receive a confirmation email. Click the link to verify your account.

### What You Get

- **Free Plan**: 10,000 emails per month
- **Daily limit (Free)**: 350 emails/day
- **Contacts (Free)**: 3,000 contacts
- **Domains (Free)**: 1 domain
- **Data retention (Free)**: 30 days
- **Basic analytics**
- **AI Website Builder**: Create landing pages, waitlist pages, newsletters, and blogs with AI
- **Ticket & Live chat**: Manage customer conversations with tickets (via email) and a real-time live chat widget
- **AI Content Assistant**: AI generates marketing emails and A/B test variations to speed up writing and iteration
- **AI Automation (Coming soon)**: Always-on automation: welcome, follow-up, and outreach emails, with built-in lead capture and growth workflows

You can upgrade anytime. Pro adds:

- **110,000 emails/month**
- **No daily limit**
- **Unlimited contacts**
- **Up to 10 domains**
- **Longer data retention (100 days)** and **advanced analytics**
- **Overage**: $0.20 per 1,000 emails after limit

## Step 2: Set Up Your API Key

### Generate API Credentials

1. Log in to your LiteStartup dashboard
2. Open the API / Developer settings area
3. Create a new API key
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

1. In your dashboard, add a sender domain (e.g., `yourdomain.com`)
2. Follow the DNS verification steps shown by LiteStartup
3. Once verified, you can send from addresses on that domain (e.g., `hello@yourdomain.com`)

### Verify Your Sender Email

For testing, you can start with a domain you control, or use any sandbox/testing option shown in your dashboard.

## Step 4: Send Your First Email

### Using cURL

```bash
curl -X POST https://api.litestartup.com/client/v2/emails \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "to": "recipient@example.com",
    "from": "noreply@yourapp.com",
    "subject": "Welcome!",
    "html": "<h1>Hello</h1>"
  }'
```

### Using Node.js

```javascript
const https = require('https');

const apiKey = 'YOUR_API_KEY';
const url = 'https://api.litestartup.com/client/v2/emails';

const data = JSON.stringify({
  to: 'recipient@example.com',
  from: 'noreply@yourapp.com',
  subject: 'Welcome!',
  html: '<h1>Hello</h1>'
});

const options = {
  hostname: 'api.litestartup.com',
  path: '/client/v2/emails',
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
    if (res.statusCode >= 200 && res.statusCode < 300) {
      console.log('Request accepted.');
      return;
    }
    console.log(`Request failed (HTTP ${res.statusCode}): ${responseData}`);
  });
});

req.on('error', (error) => {
  console.error(error);
});

req.write(data);
req.end();
```

### Using Python

```python
import requests

api_key = 'YOUR_API_KEY'
url = 'https://api.litestartup.com/client/v2/emails'

headers = {
    'Authorization': f'Bearer {api_key}',
    'Content-Type': 'application/json'
}

data = {
    'to': 'recipient@example.com',
    'from': 'noreply@yourapp.com',
    'subject': 'Welcome!',
    'html': '<h1>Hello</h1>'
}

response = requests.post(url, headers=headers, json=data)
if 200 <= response.status_code < 300:
    print("Request accepted.")
else:
    print(f"Request failed (HTTP {response.status_code}): {response.text}")
```

### Using PHP

```php
<?php
$apiKey = 'YOUR_API_KEY';
$url = 'https://api.litestartup.com/client/v2/emails';

$data = [
    'to' => 'recipient@example.com',
    'from' => 'noreply@yourapp.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
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
$httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
curl_close($ch);

if ($httpCode >= 200 && $httpCode < 300) {
    echo "Request accepted.";
} else {
    echo "Request failed (HTTP $httpCode): $response";
}
?>
```

### Using Ruby

```ruby
require 'net/http'
require 'json'

api_key = 'YOUR_API_KEY'
uri = URI('https://api.litestartup.com/client/v2/emails')

req = Net::HTTP::Post.new(uri)
req['Authorization'] = "Bearer #{api_key}"
req['Content-Type'] = 'application/json'
req.body = {
  to: 'recipient@example.com',
  from: 'noreply@yourapp.com',
  subject: 'Welcome!',
  html: '<h1>Hello</h1>'
}.to_json

res = Net::HTTP.start(uri.host, uri.port, use_ssl: true) { |http| http.request(req) }

if res.code.to_i.between?(200, 299)
  puts 'Request accepted.'
else
  puts "Request failed (HTTP #{res.code}): #{res.body}"
end
```

### Using Java (JDK 11+)

```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;

public class LiteStartupSendEmail {
  public static void main(String[] args) throws Exception {
    String apiKey = "YOUR_API_KEY";
    String json = "{\"to\":\"recipient@example.com\",\"from\":\"noreply@yourapp.com\",\"subject\":\"Welcome!\",\"html\":\"<h1>Hello</h1>\"}";

    HttpRequest request = HttpRequest.newBuilder()
        .uri(URI.create("https://api.litestartup.com/client/v2/emails"))
        .header("Authorization", "Bearer " + apiKey)
        .header("Content-Type", "application/json")
        .POST(HttpRequest.BodyPublishers.ofString(json))
        .build();

    HttpClient client = HttpClient.newHttpClient();
    HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());

    int status = response.statusCode();
    if (status >= 200 && status < 300) {
      System.out.println("Request accepted.");
    } else {
      System.out.println("Request failed (HTTP " + status + "): " + response.body());
    }
  }
}
```

### Using Go

```go
package main

import (
  "bytes"
  "fmt"
  "io"
  "net/http"
)

func main() {
  apiKey := "YOUR_API_KEY"
  url := "https://api.litestartup.com/client/v2/emails"

  payload := []byte(`{"to":"recipient@example.com","from":"noreply@yourapp.com","subject":"Welcome!","html":"<h1>Hello</h1>"}`)
  req, err := http.NewRequest("POST", url, bytes.NewBuffer(payload))
  if err != nil {
    panic(err)
  }

  req.Header.Set("Authorization", "Bearer "+apiKey)
  req.Header.Set("Content-Type", "application/json")

  resp, err := http.DefaultClient.Do(req)
  if err != nil {
    panic(err)
  }
  defer resp.Body.Close()

  body, _ := io.ReadAll(resp.Body)
  if resp.StatusCode >= 200 && resp.StatusCode < 300 {
    fmt.Println("Request accepted.")
  } else {
    fmt.Printf("Request failed (HTTP %d): %s\n", resp.StatusCode, string(body))
  }
}
```

### Using Rust

```rust
// Requires: reqwest = { version = "0.11", features = ["json"] }, tokio = { version = "1", features = ["macros", "rt-multi-thread"] }

use reqwest::Client;
use serde_json::json;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    let api_key = "YOUR_API_KEY";

    let client = Client::new();
    let res = client
        .post("https://api.litestartup.com/client/v2/emails")
        .header("Authorization", format!("Bearer {}", api_key))
        .header("Content-Type", "application/json")
        .json(&json!({
            "to": "recipient@example.com",
            "from": "noreply@yourapp.com",
            "subject": "Welcome!",
            "html": "<h1>Hello</h1>"
        }))
        .send()
        .await?;

    let status = res.status();
    let body = res.text().await.unwrap_or_default();
    if status.is_success() {
        println!("Request accepted.");
    } else {
        println!("Request failed (HTTP {}): {}", status.as_u16(), body);
    }

    Ok(())
}
```

### Using .NET (C#)

```csharp
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;

public class Program
{
    public static async Task Main()
    {
        var apiKey = "YOUR_API_KEY";
        var url = "https://api.litestartup.com/client/v2/emails";

        using var client = new HttpClient();
        client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", apiKey);

        var json = "{\"to\":\"recipient@example.com\",\"from\":\"noreply@yourapp.com\",\"subject\":\"Welcome!\",\"html\":\"<h1>Hello</h1>\"}";
        using var content = new StringContent(json, Encoding.UTF8, "application/json");

        var response = await client.PostAsync(url, content);
        var body = await response.Content.ReadAsStringAsync();

        if (response.IsSuccessStatusCode)
        {
            Console.WriteLine("Request accepted.");
        }
        else
        {
            Console.WriteLine($"Request failed (HTTP {(int)response.StatusCode}): {body}");
        }
    }
}
```

### Using C++ (libcurl)

```cpp
// Requires libcurl

#include <curl/curl.h>
#include <iostream>

int main() {
  const char* apiKey = "YOUR_API_KEY";
  const char* url = "https://api.litestartup.com/client/v2/emails";

  const char* json = "{\"to\":\"recipient@example.com\",\"from\":\"noreply@yourapp.com\",\"subject\":\"Welcome!\",\"html\":\"<h1>Hello</h1>\"}";

  CURL* curl = curl_easy_init();
  if (!curl) return 1;

  struct curl_slist* headers = nullptr;
  headers = curl_slist_append(headers, "Content-Type: application/json");
  std::string auth = std::string("Authorization: Bearer ") + apiKey;
  headers = curl_slist_append(headers, auth.c_str());

  curl_easy_setopt(curl, CURLOPT_URL, url);
  curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
  curl_easy_setopt(curl, CURLOPT_POSTFIELDS, json);

  CURLcode res = curl_easy_perform(curl);
  long httpCode = 0;
  curl_easy_getinfo(curl, CURLINFO_RESPONSE_CODE, &httpCode);

  if (res == CURLE_OK && httpCode >= 200 && httpCode < 300) {
    std::cout << "Request accepted." << std::endl;
  } else {
    std::cout << "Request failed (HTTP " << httpCode << ")" << std::endl;
  }

  curl_slist_free_all(headers);
  curl_easy_cleanup(curl);
  return 0;
}
```

### Serverless: Cloudflare Workers

```javascript
export default {
  async fetch(request, env) {
    const res = await fetch('https://api.litestartup.com/client/v2/emails', {
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${env.LITESTARTUP_API_KEY}`,
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        to: 'recipient@example.com',
        from: 'noreply@yourapp.com',
        subject: 'Welcome!',
        html: '<h1>Hello</h1>'
      })
    });

    const body = await res.text();
    return new Response(body, { status: res.status });
  }
};
```

### Serverless: Vercel (API Route)

```javascript
export default async function handler(req, res) {
  const apiKey = process.env.LITESTARTUP_API_KEY;

  const r = await fetch('https://api.litestartup.com/client/v2/emails', {
    method: 'POST',
    headers: {
      Authorization: `Bearer ${apiKey}`,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      to: 'recipient@example.com',
      from: 'noreply@yourapp.com',
      subject: 'Welcome!',
      html: '<h1>Hello</h1>'
    })
  });

  const text = await r.text();
  res.status(r.status).send(text);
}
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
- Go to your domain settings in the dashboard
- Check if your domain shows as verified
- If not, verify the DNS records were added correctly
- Wait 5-15 minutes for DNS propagation
- Use any testing/sandbox option shown in your dashboard

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
- ✓ Use any event tracking option provided by LiteStartup (if enabled)

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

## Open Questions (Please Confirm)

To keep this guide 100% accurate, please confirm:

1. Where exactly in the dashboard do users create API keys (menu path/name)?
2. What is the canonical "sender domain" setup flow in the dashboard (menu path/name)?
3. Is there an official sandbox/test sender (like a pre-verified domain) for immediate testing?
4. What does the API response look like for `POST /client/v2/emails` (e.g., does it return `success`, an `id`, etc.)?

---

**Ready to explore more?** Check out the [API Reference](02-api-reference.md) or [Code Examples](04-examples.md)!
