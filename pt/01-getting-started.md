
# Primeiros passos com o LiteStartup

Comece a usar o LiteStartup em apenas 5 minutos. Este guia mostra como se cadastrar, configurar sua chave de API e enviar seu primeiro e-mail.

## Pré-requisitos

Antes de começar, você vai precisar de:

- Um endereço de e-mail válido
- Um navegador web
- Conhecimentos básicos de APIs REST (para integração)
- O domínio do seu aplicativo ou um domínio de teste

## Etapa 1: Cadastre-se gratuitamente

### Crie sua conta

1. Acesse [LiteStartup.com](https://www.litestartup.com)
2. Clique no botão **Get Started / Sign Up** para abrir a página de cadastro
3. Ou vá diretamente para a página de cadastro: https://app.litestartup.com/signup?
4. Informe seu endereço de e-mail
5. Crie uma senha forte
6. Conclua o fluxo de cadastro

Você receberá um e-mail de confirmação. Clique no link para verificar sua conta.

### O que você recebe

- **Free Plan**: 10,000 e-mails por mês
- **Daily limit (Free)**: 350 e-mails/dia
- **Contacts (Free)**: 3,000 contatos
- **Domains (Free)**: 1 domínio
- **Data retention (Free)**: 30 dias
- **Análises básicas**
- **AI Website Builder**: Crie landing pages, páginas de waitlist, newsletters e blogs com IA
- **Ticket & Live chat**: Gerencie conversas com clientes com tickets (via e-mail) e um widget de live chat em tempo real
- **AI Content Assistant**: A IA gera e-mails de marketing e variações para testes A/B para acelerar a escrita e a iteração
- **AI Automation (Em breve)**: Automação sempre ativa: e-mails de boas-vindas, follow-up e prospecção, com captura de leads e fluxos de crescimento integrados

Você pode fazer upgrade a qualquer momento. O Pro adiciona:

- **110,000 e-mails/mês**
- **Sem limite diário**
- **Contatos ilimitados**
- **Até 10 domínios**
- **Maior retenção de dados (100 days)** e **análises avançadas**
- **Overage**: $0.20 por 1,000 e-mails após o limite

## Etapa 2: Configure sua chave de API

### Gerar credenciais de API

1. Faça login no seu dashboard do LiteStartup
2. Abra a área de configurações de API / Developer
3. Crie uma nova chave de API
4. Dê à chave um nome descritivo (por exemplo, "Production API Key")
5. Clique em **"Create"**

Sua chave de API será exibida apenas uma vez. **Copie imediatamente e armazene com segurança** — você não conseguirá vê-la novamente.

### Proteja sua chave de API

**Importante**: Nunca compartilhe sua chave de API nem a faça commit no controle de versão.

Armazene como variável de ambiente:

```bash
# .env file
LITESTARTUP_API_KEY=sk_live_xxxxxxxxxxxxx
```

Ou na configuração do seu aplicativo:

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

## Etapa 3: Configure o e-mail do remetente

### Adicione um domínio de remetente

1. No seu dashboard, adicione um domínio de remetente (por exemplo, `yourdomain.com`)
2. Siga as etapas de verificação de DNS exibidas pelo LiteStartup
3. Após a verificação, você poderá enviar a partir de endereços desse domínio (por exemplo, `hello@yourdomain.com`)

### Verifique o e-mail do remetente

Para testes, você pode começar com um domínio que controla ou usar qualquer opção de sandbox/teste exibida no seu dashboard.

## Etapa 4: Envie seu primeiro e-mail

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

## Etapa 5: Verifique seu dashboard

### Monitore o status do e-mail

1. Faça login no seu dashboard do LiteStartup
2. Vá até a seção **Emails**
3. Você deverá ver o e-mail enviado com:
   - Status de entrega
   - Rastreamento de abertura (se habilitado)
   - Rastreamento de clique (se habilitado)
   - Timestamp

### Veja os detalhes do e-mail

Clique em qualquer e-mail para ver:
- Endereço do destinatário
- Assunto
- Horário de envio
- Status de entrega
- Eventos de abertura/clique
- Quaisquer erros

## Problemas comuns e soluções

### Erro "Invalid API Key"

**Problema**: Você está recebendo um erro de autenticação.

**Solução**:
- Verifique se sua chave de API está correta
- Confirme se você está usando o prefixo `Bearer`: `Authorization: Bearer YOUR_KEY`
- Garanta que a chave não expirou
- Gere uma nova chave, se necessário

### Erro "Domain Not Verified"

**Problema**: Você não consegue enviar a partir do seu domínio.

**Solução**:
- Vá até as configurações do seu domínio no dashboard
- Verifique se o seu domínio aparece como verificado
- Se não, confirme se os registros DNS foram adicionados corretamente
- Aguarde 5-15 minutos para a propagação do DNS
- Use qualquer opção de teste/sandbox exibida no seu dashboard

### Erro "Rate Limit Exceeded"

**Problema**: Você enviou muitos e-mails em um curto período.

**Solução**:
- Aguarde alguns segundos antes de enviar mais e-mails
- Faça upgrade para um plano superior para ter limites maiores
- Implemente backoff exponencial no seu código

### E-mail não recebido

**Problema**: O destinatário não recebeu o e-mail.

**Solução**:
- Verifique se o e-mail foi entregue (status = "delivered" no dashboard)
- Peça ao destinatário para verificar a pasta de spam
- Verifique se o domínio do remetente está autenticado
- Confirme se o endereço de e-mail do destinatário está correto
- Revise o conteúdo do e-mail para evitar gatilhos de spam

## Próximos passos

Agora que você enviou seu primeiro e-mail, explore:

1. **[API Reference](/pt/02-api-reference.md)** - Conheça todos os endpoints disponíveis
2. **[Features Guide](/pt/03-features.md)** - Explore recursos avançados
3. **[Code Examples](/pt/04-examples.md)** - Veja mais exemplos de implementação
4. **[Pricing & Plans](/pt/05-pricing.md)** - Entenda cobrança e opções de upgrade

## Boas práticas

### Conteúdo do e-mail

- ✓ Sempre inclua as versões HTML e texto
- ✓ Use assuntos claros e descritivos
- ✓ Inclua um link de descadastro (unsubscribe) para e-mails de marketing
- ✓ Teste os e-mails antes de enviar para listas grandes
- ✓ Use AI Content Assistant para otimizar linhas de assunto

### Integração

- ✓ Armazene a chave de API em variáveis de ambiente
- ✓ Implemente tratamento de erros e tentativas (retries)
- ✓ Registre eventos de envio para facilitar o debug
- ✓ Monitore taxas de entrega e de bounce
- ✓ Use qualquer opção de rastreamento de eventos fornecida pelo LiteStartup (se habilitada)

### Segurança

- ✓ Nunca hardcode chaves de API
- ✓ Faça rotação das chaves de API periodicamente
- ✓ Use HTTPS em todas as chamadas de API
- ✓ Valide endereços de e-mail antes de enviar
- ✓ Implemente rate limiting do seu lado

## Solução de problemas

### Precisa de ajuda?

- Confira o [API Reference](/pt/02-api-reference.md) para documentação detalhada
- Veja [Code Examples](/pt/04-examples.md) na sua linguagem
- Consulte o [Features Guide](/pt/03-features.md) para ajuda por recurso
- Entre em contato com o suporte pelo seu dashboard

## Perguntas em aberto (por favor, confirme)

Para manter este guia 100% preciso, por favor confirme:

1. Onde exatamente no dashboard os usuários criam chaves de API (caminho/nome do menu)?
2. Qual é o fluxo canônico de configuração de "sender domain" no dashboard (caminho/nome do menu)?
3. Existe um remetente oficial de sandbox/teste (como um domínio pré-verificado) para teste imediato?
4. Como é a resposta da API para `POST /client/v2/emails` (por exemplo, retorna `success`, um `id` etc.)?

---

**Pronto para explorar mais?** Confira o [API Reference](/pt/02-api-reference.md) ou [Code Examples](/pt/04-examples.md)!
