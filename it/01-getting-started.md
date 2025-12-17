# Inizia con LiteStartup

Configura LiteStartup e parti in soli 5 minuti. Questa guida ti accompagna nella registrazione, nella configurazione della tua API key e nell’invio della tua prima e-mail.

## Prerequisiti

Prima di iniziare, ti serviranno:

- Un indirizzo e-mail valido
- Un browser web
- Conoscenze di base delle API REST (per l’integrazione)
- Il dominio della tua applicazione o un dominio di test

## Step 1: Registrati gratuitamente

### Crea il tuo account

1. Visita [LiteStartup.com](https://www.litestartup.com)
2. Clicca su un pulsante **Get Started / Sign Up** per aprire la pagina di registrazione
3. Oppure vai direttamente alla pagina di registrazione: https://app.litestartup.com/signup?
4. Inserisci il tuo indirizzo e-mail
5. Crea una password robusta
6. Completa il flusso di registrazione

Riceverai un’e-mail di conferma. Clicca sul link per verificare il tuo account.

### Cosa ottieni

- **Piano gratuito**: 10.000 e-mail al mese
- **Limite giornaliero (gratuito)**: 350 e-mail/giorno
- **Contatti (gratuito)**: 3.000 contatti
- **Domini (gratuito)**: 1 dominio
- **Conservazione dei dati (gratuito)**: 30 giorni
- **Analisi di base**
- **AI Website Builder**: Crea landing page, pagine di attesa, newsletter e blog con AI
- **Ticket & Live chat**: Gestisci le conversazioni con i clienti con ticket (via e-mail) e un widget di live chat in tempo reale
- **AI Content Assistant**: AI genera e-mail di marketing e variazioni di test A/B per velocizzare la scrittura e l’iterazione
- **AI Automation (Prossimamente)**: Automazione sempre attiva: e-mail di benvenuto, follow-up e outreach, con lead capture e flussi di crescita integrati

Puoi effettuare l’upgrade in qualsiasi momento. Il piano Pro aggiunge:

- **110.000 e-mail/mese**
- **Nessun limite giornaliero**
- **Contatti illimitati**
- **Fino a 10 domini**
- **Conservazione dei dati più lunga (100 giorni)** e **analisi avanzate**
- **Sovrapprezzo**: 0,20 $ per 1.000 e-mail dopo il limite

## Step 2: Configura la tua API key

### Genera le credenziali API

1. Accedi alla dashboard di LiteStartup
2. Apri l’area impostazioni API / Developer
3. Crea una nuova API key
4. Dai alla chiave un nome descrittivo (ad es. "Production API Key")
5. Clicca **"Create"**

La tua API key verrà mostrata una sola volta. **Copiala subito e conservala in modo sicuro**: non potrai visualizzarla di nuovo.

### Metti in sicurezza la tua API key

**Importante**: non condividere mai la tua API key e non committarla nel controllo versione.

Salvala come variabile d’ambiente:

```bash
# .env file
LITESTARTUP_API_KEY=sk_live_xxxxxxxxxxxxx
```

Oppure nella configurazione della tua applicazione:

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

## Step 3: Configura l’e-mail mittente

### Aggiungi un dominio mittente

1. Nella dashboard, aggiungi un dominio mittente (ad es. `yourdomain.com`)
2. Segui i passaggi di verifica DNS mostrati da LiteStartup
3. Una volta verificato, potrai inviare da indirizzi su quel dominio (ad es. `hello@yourdomain.com`)

### Verifica l’e-mail mittente

Per i test, puoi iniziare con un dominio che controlli oppure usare eventuali opzioni sandbox/test mostrate nella dashboard.

## Step 4: Invia la tua prima e-mail

### Con cURL

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

### Con Node.js

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

### Con Python

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

### Con PHP

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

### Con Ruby

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

### Con Java (JDK 11+)

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

### Con Go

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

### Con Rust

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

### Con .NET (C#)

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

### Con C++ (libcurl)

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

## Step 5: Controlla la dashboard

### Monitora lo stato dell’e-mail

1. Accedi alla dashboard di LiteStartup
2. Vai alla sezione **Emails**
3. Dovresti vedere l’e-mail inviata con:
   - Stato di consegna
   - Tracking delle aperture (se abilitato)
   - Tracking dei clic (se abilitato)
   - Timestamp

### Visualizza i dettagli dell’e-mail

Clicca su una qualsiasi e-mail per vedere:
- Indirizzo del destinatario
- Oggetto
- Orario di invio
- Stato di consegna
- Eventi di apertura/clic
- Eventuali errori

## Problemi comuni e soluzioni

### Errore "Invalid API Key"

**Problema**: ricevi un errore di autenticazione.

**Soluzione**:
- Verifica che la tua API key sia corretta
- Controlla di usare il prefisso `Bearer`: `Authorization: Bearer YOUR_KEY`
- Assicurati che la chiave non sia scaduta
- Genera una nuova chiave se necessario

### Errore "Domain Not Verified"

**Problema**: non riesci a inviare dal tuo dominio.

**Soluzione**:
- Vai alle impostazioni del dominio nella dashboard
- Verifica se il dominio risulta verificato
- Se non lo è, controlla che i record DNS siano stati aggiunti correttamente
- Attendi 5–15 minuti per la propagazione DNS
- Usa eventuali opzioni sandbox/test mostrate nella dashboard

### Errore "Rate Limit Exceeded"

**Problema**: hai inviato troppe e-mail in troppo poco tempo.

**Soluzione**:
- Attendi qualche secondo prima di inviare altre e-mail
- Effettua l’upgrade a un piano superiore per limiti più alti
- Implementa un backoff esponenziale nel tuo codice

### E-mail non ricevuta

**Problema**: il destinatario non ha ricevuto l’e-mail.

**Soluzione**:
- Controlla che l’e-mail sia stata consegnata (status = "delivered" in dashboard)
- Chiedi al destinatario di controllare la cartella spam
- Verifica che il dominio mittente sia autenticato
- Verifica che l’indirizzo del destinatario sia corretto
- Rivedi il contenuto dell’e-mail per evitare trigger di spam

## Prossimi passi

Ora che hai inviato la tua prima e-mail, esplora:

1. **[API Reference](/it/02-api-reference.md)** - Scopri tutti gli endpoint disponibili
2. **[Features Guide](/it/03-features.md)** - Esplora le funzionalità avanzate
3. **[Code Examples](/it/04-examples.md)** - Consulta altri esempi di implementazione
4. **[Pricing & Plans](/it/05-pricing.md)** - Comprendi fatturazione e opzioni di upgrade

## Best practice

### Contenuto e-mail

- ✓ Includi sempre sia la versione HTML sia quella testo
- ✓ Usa oggetti chiari e descrittivi
- ✓ Includi un link di disiscrizione per le e-mail marketing
- ✓ Testa le e-mail prima di inviare a liste grandi
- ✓ Usa AI Content Assistant per ottimizzare gli oggetti

### Integrazione

- ✓ Salva la API key in variabili d’ambiente
- ✓ Implementa gestione degli errori e retry
- ✓ Registra (log) gli eventi di invio per il debug
- ✓ Monitora tassi di consegna e bounce
- ✓ Usa eventuali opzioni di event tracking fornite da LiteStartup (se abilitate)

### Sicurezza

- ✓ Non hardcodare mai le API key
- ✓ Ruota periodicamente le API key
- ✓ Usa HTTPS per tutte le chiamate API
- ✓ Valida gli indirizzi e-mail prima dell’invio
- ✓ Implementa un rate limiting anche lato applicazione

## Troubleshooting

### Hai bisogno di aiuto?

- Consulta l’[API Reference](/it/02-api-reference.md) per la documentazione dettagliata
- Consulta i [Code Examples](/it/04-examples.md) per il tuo linguaggio
- Consulta il [Features Guide](/it/03-features.md) per aiuto specifico sulle funzionalità
- Contatta il supporto dalla dashboard

## Domande aperte (da confermare)

Per mantenere questa guida accurata al 100%, conferma:

1. Dove esattamente, nella dashboard, gli utenti creano le API key (percorso/nome menu)?
2. Qual è il flusso canonico per configurare il "sender domain" nella dashboard (percorso/nome menu)?
3. Esiste un mittente di test/sandbox ufficiale (ad es. un dominio già verificato) per testare subito?
4. Com’è fatta la risposta API per `POST /client/v2/emails` (ad es. ritorna `success`, un `id`, ecc.)?

---

**Vuoi approfondire?** Dai un’occhiata all’[API Reference](/it/02-api-reference.md) o ai [Code Examples](/it/04-examples.md)!
