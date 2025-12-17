# Primeros pasos con LiteStartup

Ponte en marcha con LiteStartup en solo 5 minutos. Esta guía te acompaña en el registro, la configuración de tu API key y el envío de tu primer email.

## Requisitos previos

Antes de empezar, necesitarás:

- Una dirección de email válida
- Un navegador web
- Conocimientos básicos de APIs REST (para la integración)
- El dominio de tu aplicación o un dominio de prueba

## Paso 1: Regístrate gratis

### Crea tu cuenta

1. Visita [LiteStartup.com](https://www.litestartup.com)
2. Haz clic en el botón **Comienza / Regístrate** para abrir la página de registro
3. O ve directamente a la página de registro: https://app.litestartup.com/signup?
4. Introduce tu dirección de email
5. Crea una contraseña segura
6. Completa el flujo de registro

Recibirás un email de confirmación. Haz clic en el enlace para verificar tu cuenta.

### Lo que obtienes

- **Plan Free**: 10,000 emails al mes
- **Límite diario (Free)**: 350 emails/día
- **Contactos (Free)**: 3,000 contactos
- **Dominios (Free)**: 1 dominio
- **Retención de datos (Free)**: 30 días
- **Analíticas básicas**
- **AI Website Builder**: Crea landing pages, páginas de lista de espera, newsletters y blogs con IA
- **Ticket & Live chat**: Gestiona conversaciones con clientes mediante tickets (por email) y un widget de live chat en tiempo real
- **AI Content Assistant**: La IA genera emails de marketing y variantes para pruebas A/B para acelerar la redacción y la iteración
- **AI Automation (Coming soon)**: Automatización siempre activa: emails de bienvenida, seguimiento y prospección, con captación de leads y workflows de crecimiento integrados

Puedes hacer upgrade en cualquier momento. Pro añade:

- **110,000 emails/month**
- **Sin límite diario**
- **Contactos ilimitados**
- **Hasta 10 dominios**
- **Mayor retención de datos (100 días)** y **analíticas avanzadas**
- **Overage**: $0.20 por 1,000 emails tras superar el límite

## Paso 2: Configura tu API key

### Genera credenciales de API

1. Inicia sesión en tu dashboard de LiteStartup
2. Abre el área de configuración de API / Developer
3. Crea una nueva API key
4. Asigna a tu clave un nombre descriptivo (por ejemplo, "Production API Key")
5. Haz clic en **"Crear"**

Tu API key se mostrará una sola vez. **Cópiala inmediatamente y guárdala de forma segura**: no podrás verla de nuevo.

### Protege tu API key

**Importante**: No compartas tu API key ni la subas a control de versiones.

Guárdala como variable de entorno:

```bash
# .env file
LITESTARTUP_API_KEY=sk_live_xxxxxxxxxxxxx
```

O en la configuración de tu aplicación:

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

## Paso 3: Configura tu email remitente

### Añade un dominio remitente

1. En tu dashboard, añade un dominio remitente (por ejemplo, `yourdomain.com`)
2. Sigue los pasos de verificación DNS que muestra LiteStartup
3. Una vez verificado, podrás enviar desde direcciones de ese dominio (por ejemplo, `hello@yourdomain.com`)

### Verifica tu email remitente

Para hacer pruebas, puedes empezar con un dominio que controles o usar cualquier opción de sandbox/pruebas que aparezca en tu dashboard.

## Paso 4: Envía tu primer email

### Usando cURL

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

### Usando Node.js

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

### Usando Python

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

### Usando PHP

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

### Usando Ruby

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

### Usando Java (JDK 11+)

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

### Usando Go

```go
package main

import (
  "bytes"
  "fmt"
  "io"
  "net/http"
)

func main() {
  const apiKey = "YOUR_API_KEY"
  const url = "https://api.litestartup.com/client/v2/emails"

  const json = "{\"to\":\"recipient@example.com\",\"from\":\"noreply@yourapp.com\",\"subject\":\"Welcome!\",\"html\":\"<h1>Hello</h1>\"}"

  req, err := http.NewRequest("POST", url, bytes.NewBuffer([]byte(json)))
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

### Usando Rust

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

### Usando .NET (C#)

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

### Usando C++ (libcurl)

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

## Paso 5: Revisa tu dashboard

### Monitoriza el estado del email

1. Inicia sesión en tu dashboard de LiteStartup
2. Ve a la sección **Emails**
3. Debes ver tu email enviado con:
   - Estado de entrega
   - Seguimiento de apertura (si está habilitado)
   - Seguimiento de clics (si está habilitado)
   - Marca de tiempo

### Ver detalles del email

Haz clic en cualquier email para ver:
- Dirección del destinatario
- Asunto
- Hora de envío
- Estado de entrega
- Eventos de apertura/clic
- Cualquier error

## Problemas comunes y soluciones

### Error "Invalid API Key"

**Problema**: Estás recibiendo un error de autenticación.

**Solución**:
- Verifica que tu API key sea correcta
- Comprueba que estás usando el prefijo `Bearer`: `Authorization: Bearer YOUR_KEY`
- Asegúrate de que la clave no haya expirado
- Genera una nueva clave si es necesario

### Error "Domain Not Verified"

**Problema**: No puedes enviar desde tu dominio.

**Solución**:
- Ve a la configuración de dominio en el dashboard
- Comprueba si tu dominio aparece como verificado
- Si no, verifica que los registros DNS se hayan añadido correctamente
- Espera 5-15 minutos para la propagación DNS
- Usa cualquier opción de pruebas/sandbox que aparezca en tu dashboard

### Error "Rate Limit Exceeded"

**Problema**: Has enviado demasiados emails en muy poco tiempo.

**Solución**:
- Espera unos segundos antes de enviar más emails
- Haz upgrade a un plan superior para obtener límites más altos
- Implementa exponential backoff en tu código

### Email no recibido

**Problema**: El destinatario no recibió el email.

**Solución**:
- Comprueba que el email se haya entregado (status = "delivered" en el dashboard)
- Pide al destinatario que revise la carpeta de spam
- Verifica que el dominio remitente esté autenticado
- Comprueba que la dirección de email del destinatario sea correcta
- Revisa el contenido del email por posibles disparadores de spam

## Próximos pasos

Ahora que ya enviaste tu primer email, explora:

1. **[Referencia de la API](/es/02-api-reference.md)** - Aprende todos los endpoints disponibles
2. **[Guía de funcionalidades](/es/03-features.md)** - Explora funciones avanzadas
3. **[Ejemplos de código](/es/04-examples.md)** - Mira más ejemplos de implementación
4. **[Precios y planes](/es/05-pricing.md)** - Entiende la facturación y las opciones de upgrade

## Buenas prácticas

### Contenido del email

- Incluye siempre versiones HTML y texto
- Usa asuntos claros y descriptivos
- Incluye un enlace de baja en emails de marketing
- Prueba los emails antes de enviar a listas grandes
- Usa AI Content Assistant para optimizar asuntos

### Integración

- Guarda la API key en variables de entorno
- Implementa manejo de errores y reintentos
- Registra eventos de envío para depuración
- Monitoriza tasas de entrega y rebotes
- Usa cualquier opción de event tracking que proporcione LiteStartup (si está habilitada)

### Seguridad

- No hardcodees API keys
- Rota las API keys periódicamente
- Usa HTTPS para todas las llamadas a la API
- Valida direcciones de email antes de enviar
- Implementa rate limiting de tu lado

## Solución de problemas

### ¿Necesitas ayuda?

- Consulta la [Referencia de la API](/es/02-api-reference.md) para documentación detallada
- Revisa [Ejemplos de código](/es/04-examples.md) para tu lenguaje de programación
- Consulta la [Guía de funcionalidades](/es/03-features.md) para ayuda específica por función
- Contacta con soporte desde tu dashboard

## Preguntas abiertas (por favor confirma)

Para mantener esta guía 100% precisa, por favor confirma:

1. ¿En qué parte exacta del dashboard los usuarios crean API keys (ruta/nombre del menú)?
2. ¿Cuál es el flujo canónico de configuración del "sender domain" en el dashboard (ruta/nombre del menú)?
3. ¿Existe un remitente sandbox/de prueba oficial (como un dominio pre-verificado) para pruebas inmediatas?
4. ¿Cómo es la respuesta de la API para `POST /client/v2/emails` (por ejemplo, si devuelve `success`, un `id`, etc.)?

---
 
**¿Listo para explorar más?** ¡Consulta la [Referencia de la API](/es/02-api-reference.md) o los [Ejemplos de código](/es/04-examples.md)!
