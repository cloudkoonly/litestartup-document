# Code Examples

Practical code examples for integrating LiteStartup into your application.

## PHP Examples

### Send Simple Email

```php
<?php
$apiKey = getenv('LITESTARTUP_API_KEY');
$url = 'https://api.litestartup.com/emails/send';

$data = [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1><p>Welcome to our service.</p>',
    'text' => 'Hello! Welcome to our service.'
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
    echo "Email sent: " . $result['data']['id'];
} else {
    echo "Error: " . $result['error'];
}
?>
```

### Send Email with Template

```php
<?php
$apiKey = getenv('LITESTARTUP_API_KEY');
$url = 'https://api.litestartup.com/emails/send';

$data = [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'template_id' => 'tmpl_welcome',
    'template_variables' => [
        'name' => 'John Doe',
        'company_name' => 'Acme Inc',
        'activation_link' => 'https://example.com/activate?token=abc123'
    ]
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
    echo "Email sent successfully";
}
?>
```

### Send Batch Emails

```php
<?php
$apiKey = getenv('LITESTARTUP_API_KEY');
$url = 'https://api.litestartup.com/emails/send';

$recipients = [
    'user1@example.com',
    'user2@example.com',
    'user3@example.com'
];

foreach ($recipients as $email) {
    $data = [
        'to' => $email,
        'from' => 'hello@yourdomain.com',
        'subject' => 'Special Offer!',
        'html' => '<h1>Special Offer</h1><p>Get 50% off today!</p>',
        'text' => 'Special Offer: Get 50% off today!'
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
        echo "Email sent to $email\n";
    }
}
?>
```

### Get Email Status

```php
<?php
$apiKey = getenv('LITESTARTUP_API_KEY');
$emailId = 'email_1234567890';
$url = 'https://api.litestartup.com/emails/' . $emailId;

$ch = curl_init($url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, [
    'Authorization: Bearer ' . $apiKey
]);

$response = curl_exec($ch);
$result = json_decode($response, true);

if ($result['success']) {
    $email = $result['data'];
    echo "Status: " . $email['status'] . "\n";
    echo "Delivered: " . $email['delivered_at'] . "\n";
    echo "Opened: " . $email['opened_at'] . "\n";
}
?>
```

## Python Examples

### Send Simple Email

```python
import requests
import os

api_key = os.getenv('LITESTARTUP_API_KEY')
url = 'https://api.litestartup.com/emails/send'

headers = {
    'Authorization': f'Bearer {api_key}',
    'Content-Type': 'application/json'
}

data = {
    'to': 'user@example.com',
    'from': 'hello@yourdomain.com',
    'subject': 'Welcome!',
    'html': '<h1>Hello</h1><p>Welcome to our service.</p>',
    'text': 'Hello! Welcome to our service.'
}

response = requests.post(url, headers=headers, json=data)
result = response.json()

if result['success']:
    print(f"Email sent: {result['data']['id']}")
else:
    print(f"Error: {result['error']}")
```

### Send Email with Tracking

```python
import requests
import os

api_key = os.getenv('LITESTARTUP_API_KEY')
url = 'https://api.litestartup.com/emails/send'

headers = {
    'Authorization': f'Bearer {api_key}',
    'Content-Type': 'application/json'
}

data = {
    'to': 'user@example.com',
    'from': 'hello@yourdomain.com',
    'subject': 'Check out our new features!',
    'html': '<h1>New Features</h1><p><a href="https://example.com/features">Learn more</a></p>',
    'text': 'Check out our new features',
    'track_opens': True,
    'track_clicks': True,
    'tags': ['announcement', 'features'],
    'metadata': {
        'user_id': '12345',
        'campaign': 'feature_announcement'
    }
}

response = requests.post(url, headers=headers, json=data)
result = response.json()

if result['success']:
    print(f"Email sent with tracking enabled")
```

### Scheduled Email

```python
import requests
import os
from datetime import datetime, timedelta

api_key = os.getenv('LITESTARTUP_API_KEY')
url = 'https://api.litestartup.com/emails/send'

# Schedule for 1 hour from now
scheduled_time = (datetime.utcnow() + timedelta(hours=1)).isoformat() + 'Z'

headers = {
    'Authorization': f'Bearer {api_key}',
    'Content-Type': 'application/json'
}

data = {
    'to': 'user@example.com',
    'from': 'hello@yourdomain.com',
    'subject': 'Scheduled Email',
    'html': '<h1>This email was scheduled!</h1>',
    'text': 'This email was scheduled!',
    'scheduled_at': scheduled_time
}

response = requests.post(url, headers=headers, json=data)
result = response.json()

if result['success']:
    print(f"Email scheduled for {scheduled_time}")
```

### List Emails with Filtering

```python
import requests
import os

api_key = os.getenv('LITESTARTUP_API_KEY')
url = 'https://api.litestartup.com/emails'

headers = {
    'Authorization': f'Bearer {api_key}'
}

params = {
    'status': 'delivered',
    'limit': 20,
    'page': 1,
    'sort': 'created_at',
    'order': 'desc'
}

response = requests.get(url, headers=headers, params=params)
result = response.json()

if result['success']:
    for email in result['data']:
        print(f"{email['to']} - {email['status']}")
    
    print(f"\nPage {result['pagination']['page']} of {result['pagination']['pages']}")
```

## Node.js Examples

### Send Simple Email

```javascript
const https = require('https');

const apiKey = process.env.LITESTARTUP_API_KEY;
const url = 'https://api.litestartup.com/emails/send';

const data = JSON.stringify({
  to: 'user@example.com',
  from: 'hello@yourdomain.com',
  subject: 'Welcome!',
  html: '<h1>Hello</h1><p>Welcome to our service.</p>',
  text: 'Hello! Welcome to our service.'
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
      console.log(`Email sent: ${result.data.id}`);
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

### Using Fetch API

```javascript
const apiKey = process.env.LITESTARTUP_API_KEY;

async function sendEmail() {
  const response = await fetch('https://api.litestartup.com/emails/send', {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${apiKey}`,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      to: 'user@example.com',
      from: 'hello@yourdomain.com',
      subject: 'Welcome!',
      html: '<h1>Hello</h1>',
      text: 'Hello'
    })
  });

  const result = await response.json();
  
  if (result.success) {
    console.log(`Email sent: ${result.data.id}`);
  } else {
    console.log(`Error: ${result.error}`);
  }
}

sendEmail();
```

### Using Axios

```javascript
const axios = require('axios');

const apiKey = process.env.LITESTARTUP_API_KEY;

async function sendEmail() {
  try {
    const response = await axios.post('https://api.litestartup.com/emails/send', {
      to: 'user@example.com',
      from: 'hello@yourdomain.com',
      subject: 'Welcome!',
      html: '<h1>Hello</h1>',
      text: 'Hello'
    }, {
      headers: {
        'Authorization': `Bearer ${apiKey}`,
        'Content-Type': 'application/json'
      }
    });

    console.log(`Email sent: ${response.data.data.id}`);
  } catch (error) {
    console.error(`Error: ${error.response.data.error}`);
  }
}

sendEmail();
```

## JavaScript (Browser)

### Send Email from Frontend

```javascript
async function sendEmail(to, subject, message) {
  const apiKey = 'YOUR_API_KEY'; // Use environment variable in production
  
  const response = await fetch('https://api.litestartup.com/emails/send', {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${apiKey}`,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      to: to,
      from: 'hello@yourdomain.com',
      subject: subject,
      html: `<p>${message}</p>`,
      text: message
    })
  });

  const result = await response.json();
  return result;
}

// Usage
sendEmail('user@example.com', 'Hello!', 'Welcome to our service')
  .then(result => {
    if (result.success) {
      console.log('Email sent successfully');
    }
  });
```

## Ruby Examples

### Send Simple Email

```ruby
require 'net/http'
require 'json'

api_key = ENV['LITESTARTUP_API_KEY']
url = URI('https://api.litestartup.com/emails/send')

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Post.new(url)
request['Authorization'] = "Bearer #{api_key}"
request['Content-Type'] = 'application/json'

data = {
  to: 'user@example.com',
  from: 'hello@yourdomain.com',
  subject: 'Welcome!',
  html: '<h1>Hello</h1>',
  text: 'Hello'
}

request.body = JSON.generate(data)

response = http.request(request)
result = JSON.parse(response.body)

if result['success']
  puts "Email sent: #{result['data']['id']}"
else
  puts "Error: #{result['error']}"
end
```

## Go Examples

### Send Simple Email

```go
package main

import (
    "bytes"
    "encoding/json"
    "fmt"
    "io/ioutil"
    "net/http"
    "os"
)

func main() {
    apiKey := os.Getenv("LITESTARTUP_API_KEY")
    url := "https://api.litestartup.com/emails/send"

    data := map[string]interface{}{
        "to":      "user@example.com",
        "from":    "hello@yourdomain.com",
        "subject": "Welcome!",
        "html":    "<h1>Hello</h1>",
        "text":    "Hello",
    }

    jsonData, _ := json.Marshal(data)

    req, _ := http.NewRequest("POST", url, bytes.NewBuffer(jsonData))
    req.Header.Set("Authorization", fmt.Sprintf("Bearer %s", apiKey))
    req.Header.Set("Content-Type", "application/json")

    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        panic(err)
    }
    defer resp.Body.Close()

    body, _ := ioutil.ReadAll(resp.Body)
    var result map[string]interface{}
    json.Unmarshal(body, &result)

    if result["success"].(bool) {
        fmt.Println("Email sent successfully")
    } else {
        fmt.Println("Error:", result["error"])
    }
}
```

## Webhook Integration

### Handle Webhook Events

```php
<?php
// Verify webhook signature
$payload = file_get_contents('php://input');
$signature = $_SERVER['HTTP_X_LITESTARTUP_SIGNATURE'] ?? '';
$secret = getenv('LITESTARTUP_WEBHOOK_SECRET');

$expectedSignature = hash_hmac('sha256', $payload, $secret);

if (!hash_equals($expectedSignature, $signature)) {
    http_response_code(401);
    exit('Unauthorized');
}

$event = json_decode($payload, true);

switch ($event['event']) {
    case 'email.delivered':
        handleDelivered($event['data']);
        break;
    case 'email.opened':
        handleOpened($event['data']);
        break;
    case 'email.clicked':
        handleClicked($event['data']);
        break;
    case 'email.bounced':
        handleBounced($event['data']);
        break;
}

function handleDelivered($data) {
    // Log delivery
    error_log("Email delivered to: " . $data['to']);
}

function handleOpened($data) {
    // Track open
    error_log("Email opened by: " . $data['to']);
}

function handleClicked($data) {
    // Track click
    error_log("Link clicked in email to: " . $data['to']);
}

function handleBounced($data) {
    // Handle bounce
    error_log("Email bounced: " . $data['to']);
}

http_response_code(200);
echo json_encode(['success' => true]);
?>
```

### Node.js Webhook Handler

```javascript
const express = require('express');
const crypto = require('crypto');

const app = express();
app.use(express.json());

const webhookSecret = process.env.LITESTARTUP_WEBHOOK_SECRET;

app.post('/webhooks/litestartup', (req, res) => {
  const signature = req.headers['x-litestartup-signature'];
  const payload = JSON.stringify(req.body);
  
  const expectedSignature = crypto
    .createHmac('sha256', webhookSecret)
    .update(payload)
    .digest('hex');
  
  if (signature !== expectedSignature) {
    return res.status(401).json({ error: 'Unauthorized' });
  }

  const event = req.body;

  switch (event.event) {
    case 'email.delivered':
      console.log(`Email delivered to ${event.data.to}`);
      break;
    case 'email.opened':
      console.log(`Email opened by ${event.data.to}`);
      break;
    case 'email.clicked':
      console.log(`Link clicked in email to ${event.data.to}`);
      break;
    case 'email.bounced':
      console.log(`Email bounced: ${event.data.to}`);
      break;
  }

  res.json({ success: true });
});

app.listen(3000, () => {
  console.log('Webhook server listening on port 3000');
});
```

## Error Handling

### PHP Error Handling

```php
<?php
function sendEmailWithErrorHandling($to, $subject, $message) {
    $apiKey = getenv('LITESTARTUP_API_KEY');
    $url = 'https://api.litestartup.com/emails/send';

    try {
        $data = [
            'to' => $to,
            'from' => 'hello@yourdomain.com',
            'subject' => $subject,
            'html' => $message,
            'text' => strip_tags($message)
        ];

        $ch = curl_init($url);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
        curl_setopt($ch, CURLOPT_TIMEOUT, 10);
        curl_setopt($ch, CURLOPT_HTTPHEADER, [
            'Authorization: Bearer ' . $apiKey,
            'Content-Type: application/json'
        ]);
        curl_setopt($ch, CURLOPT_POST, true);
        curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));

        $response = curl_exec($ch);
        $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
        curl_close($ch);

        if ($httpCode !== 200 && $httpCode !== 201) {
            throw new Exception("HTTP Error: $httpCode");
        }

        $result = json_decode($response, true);

        if (!$result['success']) {
            throw new Exception("API Error: " . $result['error']);
        }

        return $result['data'];
    } catch (Exception $e) {
        error_log("Email send failed: " . $e->getMessage());
        return false;
    }
}
?>
```

---

**Next:** Check [Pricing & Plans](05-pricing.md) or review [Features Guide](03-features.md)!
