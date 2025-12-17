# Erste Schritte mit LiteStartup

Starte mit LiteStartup in nur 5 Minuten. Dieser Guide führt dich durch die Registrierung, das Einrichten deines API-Keys und das Versenden deiner ersten E-Mail.

## Voraussetzungen

Bevor du startest, brauchst du:

- Eine gültige E-Mail-Adresse
- Einen Webbrowser
- Grundkenntnisse zu REST-APIs (für die Integration)
- Die Domain deiner Anwendung oder eine Testdomain

## Schritt 1: Kostenlos registrieren

### Konto erstellen

1. Besuche [LiteStartup.com](https://www.litestartup.com)
2. Klicke auf **Get Started / Sign Up**, um die Registrierungsseite zu öffnen
3. Oder gehe direkt zur Registrierungsseite: https://app.litestartup.com/signup?
4. Gib deine E-Mail-Adresse ein
5. Erstelle ein sicheres Passwort
6. Schließe den Registrierungsprozess ab

Du erhältst eine Bestätigungs-E-Mail. Klicke auf den Link, um dein Konto zu verifizieren.

### Was du bekommst

- **Free Plan**: 10.000 E-Mails pro Monat
- **Daily limit (Free)**: 350 E-Mails/Tag
- **Contacts (Free)**: 3.000 Kontakte
- **Domains (Free)**: 1 Domain
- **Data retention (Free)**: 30 Tage
- **Grundlegende Analysen**
- **AI Website Builder**: Erstelle Landingpages, Waitlist-Seiten, Newsletter und Blogs mit KI
- **Ticket & Live chat**: Verwalte Kundengespräche mit Tickets (per E-Mail) und einem Echtzeit-Live-Chat-Widget
- **AI Content Assistant**: KI generiert Marketing-E-Mails und A/B-Test-Varianten, um Schreiben und Iteration zu beschleunigen
- **AI Automation (Coming soon)**: Always-on-Automatisierung: Willkommens-, Follow-up- und Outreach-E-Mails – mit integriertem Lead-Capture und Growth-Workflows

Du kannst jederzeit upgraden. Pro bietet zusätzlich:

- **110.000 E-Mails pro Monat**
- **Kein tägliches Limit**
- **Unbegrenzte Kontakte**
- **Bis zu 10 Domains**
- **Längere Datenaufbewahrung (100 Tage)** und **Erweiterte Analysen**
- **Übertragung**: 0,20 $ pro 1.000 E-Mails nach Limit

## Schritt 2: API-Key einrichten

### API-Zugangsdaten erstellen

1. Melde dich in deinem LiteStartup-Dashboard an
2. Öffne den Bereich API-/Developer-Settings
3. Erstelle einen neuen API-Key
4. Gib dem Key einen aussagekräftigen Namen (z. B. "Production API Key")
5. Klicke auf **"Create"**

Dein API-Key wird nur einmal angezeigt. **Kopiere ihn sofort und speichere ihn sicher** – du kannst ihn später nicht erneut einsehen.

### API-Key sicher aufbewahren

**Wichtig**: Teile deinen API-Key niemals und committe ihn nicht in die Versionsverwaltung.

Speichere ihn als Umgebungsvariable:

```bash
# .env file
LITESTARTUP_API_KEY=sk_live_xxxxxxxxxxxxx
```

Oder in der Konfiguration deiner Anwendung:

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

## Schritt 3: Absender-E-Mail konfigurieren

### Absender-Domain hinzufügen

1. Füge in deinem Dashboard eine Absender-Domain hinzu (z. B. `yourdomain.com`)
2. Folge den DNS-Verifikationsschritten, die LiteStartup anzeigt
3. Nach der Verifizierung kannst du von Adressen dieser Domain senden (z. B. `hello@yourdomain.com`)

### Absender-E-Mail verifizieren

Zum Testen kannst du mit einer Domain starten, die du kontrollierst, oder eine Sandbox-/Testing-Option verwenden, die im Dashboard angeboten wird.

## Schritt 4: Erste E-Mail versenden

### Mit cURL

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

### Mit Node.js

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

### Mit Python

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

### Mit PHP

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

### Mit Ruby

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

### Mit Java (JDK 11+)

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

### Mit Go

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

### Mit Rust

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

### Mit .NET (C#)

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

### Mit C++ (libcurl)

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

## Schritt 5: Dashboard prüfen

### E-Mail-Status überwachen

1. Melde dich in deinem LiteStartup-Dashboard an
2. Gehe zum Bereich **Emails**
3. Du solltest deine gesendete E-Mail sehen, inklusive:
   - Zustellstatus
   - Open-Tracking (falls aktiviert)
   - Click-Tracking (falls aktiviert)
   - Zeitstempel

### E-Mail-Details ansehen

Klicke auf eine beliebige E-Mail, um Folgendes zu sehen:
- Empfängeradresse
- Betreffzeile
- Sendezeit
- Zustellstatus
- Open-/Click-Events
- Etwaige Fehler

## Häufige Probleme & Lösungen

### Fehler "Invalid API Key"

**Problem**: Du erhältst einen Authentifizierungsfehler.

**Lösung**:
- Prüfe, ob dein API-Key korrekt ist
- Prüfe, ob du das `Bearer`-Präfix verwendest: `Authorization: Bearer YOUR_KEY`
- Stelle sicher, dass der Key nicht abgelaufen ist
- Erstelle bei Bedarf einen neuen Key

### Fehler "Domain Not Verified"

**Problem**: Du kannst nicht von deiner Domain senden.

**Lösung**:
- Öffne in deinem Dashboard die Domain-Einstellungen
- Prüfe, ob deine Domain als verifiziert angezeigt wird
- Falls nicht, prüfe, ob die DNS-Records korrekt gesetzt wurden
- Warte 5–15 Minuten auf DNS-Propagation
- Nutze eine Sandbox-/Testing-Option, die im Dashboard angeboten wird

### Fehler "Rate Limit Exceeded"

**Problem**: Du hast zu viele E-Mails in zu kurzer Zeit gesendet.

**Lösung**:
- Warte ein paar Sekunden, bevor du weitere E-Mails sendest
- Upgrade auf einen höheren Plan für höhere Rate Limits
- Implementiere Exponential Backoff in deinem Code

### E-Mail nicht angekommen

**Problem**: Der Empfänger hat die E-Mail nicht erhalten.

**Lösung**:
- Prüfe, ob die E-Mail zugestellt wurde (Status = "delivered" im Dashboard)
- Bitte den Empfänger, den Spam-Ordner zu prüfen
- Stelle sicher, dass die Sender-Domain authentifiziert ist
- Prüfe, ob die Empfängeradresse korrekt ist
- Prüfe den Inhalt auf typische Spam-Trigger

## Nächste Schritte

Nachdem du deine erste E-Mail gesendet hast, schau dir Folgendes an:
1. **[API Reference](/de/02-api-reference.md)** - Alle verfügbaren Endpoints kennenlernen
2. **[Features Guide](/de/03-features.md)** - Erweiterte Features entdecken
3. **[Code Examples](/de/04-examples.md)** - Weitere Implementierungsbeispiele ansehen
4. **[Pricing & Plans](/de/05-pricing.md)** - Abrechnung und Upgrade-Optionen verstehen
 
 ## Bewährte Vorgehensweisen
 
 ### E-Mail-Inhalte
 
- ✓ Immer sowohl HTML- als auch Text-Versionen mitschicken
- ✓ Klare, aussagekräftige Betreffzeilen verwenden
- ✓ Für Marketing-E-Mails einen Unsubscribe-Link einbauen
- ✓ E-Mails testen, bevor du an große Listen sendest
- ✓ AI Content Assistant nutzen, um Betreffzeilen zu optimieren

 ### Integration
 
- ✓ API-Key in Umgebungsvariablen speichern
- ✓ Fehlerbehandlung und Retries implementieren
- ✓ E-Mail-Sende-Events fürs Debugging loggen
- ✓ Zustellraten und Bounce-Rates überwachen
- ✓ Event-Tracking-Optionen von LiteStartup nutzen (falls aktiviert)

 ### Sicherheit
 
- ✓ API-Keys niemals hardcoden
- ✓ API-Keys regelmäßig rotieren
- ✓ Für alle API-Calls HTTPS verwenden
- ✓ E-Mail-Adressen vor dem Senden validieren
- ✓ Auf deiner Seite Rate Limiting implementieren
 
 ## Fehlerbehebung
 
 ### Brauchst du Hilfe?
 
- Schau in die [API Reference](/de/02-api-reference.md) für detaillierte Dokumentation
- Sieh dir [Code Examples](/de/04-examples.md) für deine Programmiersprache an
- Sieh im [Features Guide](/de/03-features.md) nach, wenn du Hilfe zu bestimmten Features brauchst
- Kontaktiere den Support über dein Dashboard

## Offene Fragen (bitte bestätigen)

Damit dieser Guide zu 100% korrekt bleibt, bestätige bitte:

1. Wo genau im Dashboard erstellen Nutzer API-Keys (Menüpfad/Bezeichnung)?
2. Wie lautet der kanonische Setup-Flow für "Sender Domain" im Dashboard (Menüpfad/Bezeichnung)?
3. Gibt es einen offiziellen Sandbox-/Test-Absender (z. B. eine vorverifizierte Domain) für sofortiges Testen?
4. Wie sieht die API-Response für `POST /client/v2/emails` aus (z. B. `success`, eine `id`, etc.)?

---

**Bereit, mehr zu entdecken?** Schau dir die [API Reference](/de/02-api-reference.md) oder die [Code Examples](/de/04-examples.md) an!
