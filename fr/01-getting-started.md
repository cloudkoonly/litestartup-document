# Bien démarrer avec LiteStartup

Mettez LiteStartup en route en seulement 5 minutes. Ce guide vous accompagne pour vous inscrire, configurer votre clé API et envoyer votre premier e-mail.

## Prérequis

Avant de commencer, vous aurez besoin de :

- Une adresse e-mail valide
- Un navigateur web
- Des notions de base des API REST (pour l’intégration)
- Le domaine de votre application ou un domaine de test

## Étape 1 : s’inscrire gratuitement

### Créer votre compte

1. Rendez-vous sur [LiteStartup.com](https://www.litestartup.com)
2. Cliquez sur un bouton **Get Started / Sign Up** pour ouvrir la page d’inscription
3. Ou allez directement sur la page d’inscription : https://app.litestartup.com/signup?
4. Saisissez votre adresse e-mail
5. Créez un mot de passe robuste
6. Terminez le parcours d’inscription

Vous recevrez un e-mail de confirmation. Cliquez sur le lien pour vérifier votre compte.

### Ce que vous obtenez

- **Free Plan** : 10 000 e-mails par mois
- **Limite quotidienne (Free)** : 350 e-mails/jour
- **Contacts (Free)** : 3 000 contacts
- **Domaines (Free)** : 1 domaine
- **Rétention des données (Free)** : 30 jours
- **Analyses de base**
- **AI Website Builder** : Créez des landing pages, des pages de liste d’attente, des newsletters et des blogs avec l’IA
- **Ticket & Live chat** : Gérez les conversations client via des tickets (par e-mail) et un widget de chat en direct en temps réel
- **AI Content Assistant** : L’IA génère des e-mails marketing et des variantes pour tests A/B afin d’accélérer la rédaction et l’itération
- **AI Automation (Coming soon)** : Automatisation toujours active : e-mails de bienvenue, relances et outreach, avec capture de leads intégrée et workflows de croissance

Vous pouvez passer à un plan supérieur à tout moment. Le plan Pro ajoute :

- **110 000 e-mails/mois**
- **Aucune limite quotidienne**
- **Contacts illimités**
- **Jusqu’à 10 domaines**
- **Rétention plus longue (100 jours)** et **analyses avancées**
- **Dépassement** : 0,20 $ par 1 000 e-mails au-delà de la limite

## Étape 2 : configurer votre clé API

### Générer des identifiants API

1. Connectez-vous à votre tableau de bord LiteStartup
2. Ouvrez la section des paramètres API / Développeur
3. Créez une nouvelle clé API
4. Donnez à votre clé un nom explicite (ex. : « Production API Key »)
5. Cliquez sur **"Create"**

Votre clé API ne sera affichée qu’une seule fois. **Copiez-la immédiatement et stockez-la de manière sécurisée** : vous ne pourrez pas la revoir ensuite.

### Sécuriser votre clé API

**Important** : ne partagez jamais votre clé API et ne la committez jamais dans un dépôt.

Stockez-la comme variable d’environnement :

```bash
# .env file
LITESTARTUP_API_KEY=sk_live_xxxxxxxxxxxxx
```

Ou dans la configuration de votre application :

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

## Étape 3 : configurer votre e-mail d’expéditeur

### Ajouter un domaine d’expéditeur

1. Dans votre tableau de bord, ajoutez un domaine d’expéditeur (par ex. `yourdomain.com`)
2. Suivez les étapes de vérification DNS affichées par LiteStartup
3. Une fois vérifié, vous pouvez envoyer depuis des adresses de ce domaine (par ex. `hello@yourdomain.com`)

### Vérifier votre e-mail d’expéditeur

Pour les tests, vous pouvez commencer avec un domaine que vous contrôlez, ou utiliser toute option de sandbox/test proposée dans votre tableau de bord.

## Étape 4 : envoyer votre premier e-mail

### Avec cURL

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

### Avec Node.js

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

### Avec Python

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

### Avec PHP

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

### Avec Ruby

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

### Avec Java (JDK 11+)

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

### Avec Go

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

### Avec Rust

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

### Avec .NET (C#)

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

### Avec C++ (libcurl)

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

### Serverless : Cloudflare Workers

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

### Serverless : Vercel (route API)

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

## Étape 5 : vérifier votre tableau de bord

### Surveiller le statut des e-mails

1. Connectez-vous à votre tableau de bord LiteStartup
2. Allez dans la section **Emails**
3. Vous devriez voir votre e-mail envoyé avec :
   - Statut de livraison
   - Suivi des ouvertures (si activé)
   - Suivi des clics (si activé)
   - Horodatage

### Consulter le détail d’un e-mail

Cliquez sur n’importe quel e-mail pour voir :
- Adresse du destinataire
- Objet
- Heure d’envoi
- Statut de livraison
- Événements d’ouverture/clic
- Éventuelles erreurs

## Problèmes courants et solutions

### Erreur « Invalid API Key »

**Problème** : vous obtenez une erreur d’authentification.

**Solution** :
- Vérifiez que votre clé API est correcte
- Vérifiez que vous utilisez le préfixe `Bearer` : `Authorization: Bearer YOUR_KEY`
- Assurez-vous que la clé n’a pas expiré
- Générez une nouvelle clé si nécessaire

### Erreur « Domain Not Verified »

**Problème** : vous ne pouvez pas envoyer depuis votre domaine.

**Solution** :
- Allez dans les paramètres de domaine dans le tableau de bord
- Vérifiez si votre domaine apparaît comme vérifié
- Sinon, vérifiez que les enregistrements DNS ont bien été ajoutés
- Attendez 5 à 15 minutes pour la propagation DNS
- Utilisez toute option de test/sandbox proposée dans votre tableau de bord

### Erreur « Rate Limit Exceeded »

**Problème** : vous avez envoyé trop d’e-mails trop rapidement.

**Solution** :
- Attendez quelques secondes avant d’envoyer d’autres e-mails
- Passez à un plan supérieur pour des limites de débit plus élevées
- Implémentez un backoff exponentiel dans votre code

### E-mail non reçu

**Problème** : le destinataire n’a pas reçu l’e-mail.

**Solution** :
- Vérifiez que l’e-mail a été livré (statut = "delivered" dans le tableau de bord)
- Demandez au destinataire de vérifier le dossier spam
- Vérifiez que le domaine d’expéditeur est authentifié
- Vérifiez que l’adresse e-mail du destinataire est correcte
- Revoyez le contenu de l’e-mail pour éviter les déclencheurs de spam

## Prochaines étapes

Maintenant que vous avez envoyé votre premier e-mail, explorez :

1. **[Référence API](/fr/02-api-reference.md)** - Découvrir tous les endpoints disponibles
2. **[Guide des fonctionnalités](/fr/03-features.md)** - Explorer les fonctionnalités avancées
3. **[Exemples de code](/fr/04-examples.md)** - Voir davantage d’exemples d’implémentation
4. **[Tarifs & offres](/fr/05-pricing.md)** - Comprendre la facturation et les options de mise à niveau

## Bonnes pratiques

### Contenu des e-mails

- ✓ Incluez toujours une version HTML et une version texte
- ✓ Utilisez des objets clairs et descriptifs
- ✓ Incluez un lien de désinscription pour les e-mails marketing
- ✓ Testez vos e-mails avant d’envoyer à de grandes listes
- ✓ Utilisez AI Content Assistant pour optimiser les objets

### Intégration

- ✓ Stockez la clé API dans des variables d’environnement
- ✓ Implémentez la gestion d’erreurs et les retries
- ✓ Journalisez les envois d’e-mails pour le debug
- ✓ Surveillez les taux de délivrabilité et de rebond
- ✓ Utilisez toute option de suivi d’événements fournie par LiteStartup (si activée)

### Sécurité

- ✓ Ne hardcodez jamais les clés API
- ✓ Faites tourner les clés API périodiquement
- ✓ Utilisez HTTPS pour tous les appels API
- ✓ Validez les adresses e-mail avant l’envoi
- ✓ Implémentez une limitation de débit côté application

## Dépannage

### Besoin d’aide ?

- Consultez la [Référence API](/fr/02-api-reference.md) pour la documentation détaillée
- Consultez les [Exemples de code](/fr/04-examples.md) pour votre langage
- Consultez le [Guide des fonctionnalités](/fr/03-features.md) pour une aide par fonctionnalité
- Contactez le support via votre tableau de bord

## Questions ouvertes (merci de confirmer)

Pour que ce guide reste 100 % exact, merci de confirmer :

1. Où exactement, dans le tableau de bord, les utilisateurs créent-ils les clés API (chemin/nom du menu) ?
2. Quel est le flux canonique de configuration du « sender domain » dans le tableau de bord (chemin/nom du menu) ?
3. Existe-t-il un expéditeur de test/sandbox officiel (par ex. un domaine pré-vérifié) pour tester immédiatement ?
4. À quoi ressemble la réponse API pour `POST /client/v2/emails` (par ex. `success`, un `id`, etc.) ?

---

**Prêt à aller plus loin ?** Consultez la [Référence API](/fr/02-api-reference.md) ou les [Exemples de code](/fr/04-examples.md) !
