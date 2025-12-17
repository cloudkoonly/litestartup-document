# LiteStartup を始める

LiteStartup は 5 分でセットアップして使い始められます。このガイドでは、サインアップ、API key の設定、最初のメール送信までを順に説明します。

## 事前準備

開始前に、次のものを用意してください：

- 有効なメールアドレス
- Web ブラウザ
- REST API の基本的な知識（連携時）
- アプリケーションのドメイン、またはテスト用ドメイン

## Step 1: 無料でサインアップ

### アカウントを作成

1. [LiteStartup.com](https://www.litestartup.com) にアクセス
2. **Get Started / Sign Up** ボタンをクリックしてサインアップページを開く
3. もしくは直接サインアップページへ： https://app.litestartup.com/signup?
4. メールアドレスを入力
5. 強力なパスワードを作成
6. サインアップフローを完了

確認メールが届きます。リンクをクリックしてアカウントを認証してください。

### 利用できる内容

- **Free Plan**: 10,000 emails per month
- **Daily limit (Free)**: 350 emails/day
- **Contacts (Free)**: 3,000 contacts
- **Domains (Free)**: 1 domain
- **Data retention (Free)**: 30 days
- **Basic analytics**
- **AI Website Builder**: AI でランディングページ、ウェイトリストページ、ニュースレター、ブログを作成
- **Ticket & Live chat**: チケット（メール）とリアルタイムのライブチャットウィジェットで顧客対応を管理
- **AI Content Assistant**: マーケティングメールや A/B テスト用のバリエーションを生成し、作成と改善を高速化
- **AI Automation (Coming soon)**: ウェルカム、フォローアップ、アウトリーチの常時稼働オートメーション（リード獲得と成長ワークフロー内蔵）

いつでもアップグレードできます。Pro では次の内容が追加されます：

- **110,000 emails/month**
- **No daily limit**
- **Unlimited contacts**
- **Up to 10 domains**
- **Longer data retention (100 days)** and **advanced analytics**
- **Overage**: $0.20 per 1,000 emails after limit

## Step 2: Set Up Your API Key

### API 認証情報を生成

1. LiteStartup のダッシュボードにログイン
2. API / Developer 設定画面を開く
3. 新しい API key を作成
4. 分かりやすい名前を付ける（例："Production API Key"）
5. Click **"Create"**

API key は 1 度だけ表示されます。**すぐにコピーして安全に保管してください**。後から再表示できません。

### API key を安全に保管

**重要**：API key を共有したり、バージョン管理にコミットしたりしないでください。

環境変数として保管します：

```bash
# .env file
LITESTARTUP_API_KEY=sk_live_xxxxxxxxxxxxx
```

またはアプリケーション側の設定で読み込みます：

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

## Step 3: 送信元メールを設定

### 送信ドメインを追加

1. ダッシュボードで送信ドメイン（例：`yourdomain.com`）を追加
2. LiteStartup に表示される DNS 検証手順に従う
3. 検証が完了すると、そのドメインのアドレス（例：`hello@yourdomain.com`）から送信可能になります

### 送信元メールの検証

テスト目的であれば、管理しているドメインで開始するか、ダッシュボードに表示される sandbox/test オプションを利用してください。

## Step 4: 最初のメールを送信

### cURL を使う

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

### Node.js を使う

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

### Python を使う

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

### PHP を使う

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

### Ruby を使う

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

### Java (JDK 11+) を使う

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

### Go を使う

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

### Rust を使う

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

### .NET (C#) を使う

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

### C++ (libcurl) を使う

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

### Serverless: Vercel（API Route）

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

## Step 5: ダッシュボードを確認

### メールステータスを監視

1. LiteStartup のダッシュボードにログイン
2. **Emails** セクションへ移動
3. 送信したメールに以下が表示されるはずです：
   - 配信ステータス
   - 開封トラッキング（有効時）
   - クリックトラッキング（有効時）
   - タイムスタンプ

### メール詳細を確認

任意のメールをクリックすると以下を確認できます：
- 宛先アドレス
- 件名
- 送信時刻
- 配信ステータス
- 開封/クリックイベント
- エラー（あれば）

## よくある問題と解決策

### "Invalid API Key" エラー

**問題**：認証エラーが発生する。

**解決策**：
- API key が正しいか確認する
- `Bearer` プレフィックスを付けているか確認：`Authorization: Bearer YOUR_KEY`
- キーが期限切れになっていないか確認する
- 必要なら新しいキーを発行する

### "Domain Not Verified" エラー

**問題**：自分のドメインから送信できない。

**解決策**：
- ダッシュボードのドメイン設定へ移動する
- ドメインが verified と表示されているか確認する
- されていない場合、DNS レコードが正しく追加されているか確認する
- DNS 反映に 5～15 分待つ
- ダッシュボードに表示される testing/sandbox オプションを利用する

### "Rate Limit Exceeded" エラー

**問題**：短時間に送信しすぎた。

**解決策**：
- 数秒待ってから再送する
- より高いレート制限のプランにアップグレードする
- コード側で指数バックオフを実装する

### メールが届かない

**問題**：受信者がメールを受け取っていない。

**解決策**：
- ダッシュボードで配信されているか確認（status = "delivered"）
- 迷惑メールフォルダを確認してもらう
- 送信ドメインが認証済みか確認する
- 宛先メールアドレスが正しいか確認する
- 迷惑メール判定されやすい表現がないか本文を見直す

## 次のステップ

最初のメールを送信できたら、次を確認しましょう：

1. **[API Reference](/ja/02-api-reference.md)** - 利用可能なすべてのエンドポイントを確認
2. **[Features Guide](/ja/03-features.md)** - 高度な機能を確認
3. **[Code Examples](/ja/04-examples.md)** - さらに多くの実装例を見る
4. **[Pricing & Plans](/ja/05-pricing.md)** - 請求とアップグレードオプションを理解

## ベストプラクティス

### メール内容

- ✓ HTML とテキスト両方のバージョンを常に含める
- ✓ 明確で説明的な件名を使う
- ✓ マーケティングメールには配信停止リンクを含める
- ✓ 大規模配信の前にテスト送信する
- ✓ AI Content Assistant で件名を最適化する

### 連携

- ✓ API key は環境変数に保存する
- ✓ エラーハンドリングとリトライを実装する
- ✓ デバッグのため送信イベントをログに残す
- ✓ 配信率とバウンス率を監視する
- ✓ LiteStartup が提供するイベントトラッキング（有効時）を利用する

### セキュリティ

- ✓ API key をハードコードしない
- ✓ API key を定期的にローテーションする
- ✓ すべての API 呼び出しで HTTPS を使用する
- ✓ 送信前にメールアドレスを検証する
- ✓ 自システム側でもレート制限を実装する

## トラブルシューティング

### 困ったときは

- 詳細は [API Reference](/ja/02-api-reference.md) を確認
- 使用言語の [Code Examples](/ja/04-examples.md) を確認
- 機能別のヘルプは [Features Guide](/ja/03-features.md) を参照
- ダッシュボードからサポートに問い合わせる

## 未確定事項（要確認）

このガイドを 100% 正確に保つため、次の点を確認してください：

1. ダッシュボードのどこで API key を作成しますか（メニューのパス/名称）？
2. ダッシュボード上の "sender domain" 設定フローの正しい手順は何ですか（メニューのパス/名称）？
3. すぐにテストできる公式の sandbox/test 送信元（事前検証済みドメイン等）はありますか？
4. `POST /client/v2/emails` の API レスポンスはどのような形式ですか（`success` や `id` などを返しますか）？

---

**もっと確認しますか？** [API Reference](/ja/02-api-reference.md) または [Code Examples](/ja/04-examples.md) を参照してください。
