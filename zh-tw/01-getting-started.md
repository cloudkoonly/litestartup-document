# LiteStartup 快速開始指南

只需 5 分鐘即可開始使用 LiteStartup。本指南將帶您完成註冊、設定 API 金鑰，以及發送您的第一封郵件。

## 先決條件

在開始之前，您需要：

- 一個有效的電子郵件地址
- 一個網路瀏覽器
- REST API 的基礎知識（用於整合）
- 您的應用程式網域或一個測試網域

## 第 1 步：免費註冊

### 建立您的帳戶

1. 造訪 [LiteStartup.com](https://www.litestartup.com)
2. 點擊 **"Start Free Today"**（立即免費開始）按鈕
3. 輸入您的電子郵件地址
4. 建立一個強密碼
5. 點擊 **"Sign Up"**（註冊）

您將收到一封確認郵件。點擊連結以驗證您的帳戶。

### 您將獲得

- **免費方案**：每月 10,000 封郵件
- **完整 API 存取權**：可用所有功能
- **無需信用卡**：完全免費開始
- **隨時升級**：隨著業務成長隨時擴充

## 第 2 步：設定您的 API 金鑰

### 產生 API 憑證

1. 登入您的 LiteStartup 儀表板
2. 導覽至 **Settings**（設定） → **API Keys**（API 金鑰）
3. 點擊 **"Generate New API Key"**（產生新 API 金鑰）
4. 給您的金鑰取一個描述性的名稱（例如："Production API Key"）
5. 點擊 **"Create"**（建立）

您的 API 金鑰將只顯示一次。**請立即複製並安全保存**，之後將無法再次查看。

### 保護您的 API 金鑰

**重要**：切勿分享您的 API 金鑰或將其提交到版本控制系統。

將其儲存為環境變數：

```bash
# .env 檔案
LITESTARTUP_API_KEY=sk_live_xxxxxxxxxxxxx
```

或者在您的應用程式設定中：

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

## 第 3 步：設定您的寄件者信箱

### 新增寄件者網域

1. 前往 **Settings**（設定） → **Domains**（網域）
2. 點擊 **"Add Domain"**（新增網域）
3. 輸入您的網域（例如：`hello@yourdomain.com`）
4. 依照 DNS 驗證步驟操作：
   - 將提供的 DNS 記錄新增到您的網域
   - 等待驗證（通常 5-15 分鐘）
5. 一旦驗證通過，您就可以使用該網域發送郵件

### 驗證您的寄件者信箱

用於測試，您可以使用：

```
test@litestartup.com
```

這是一個測試網域，無需 DNS 驗證即可立即使用。

## 第 4 步：發送您的第一封郵件

### 使用 cURL

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

### 使用 PHP

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

### 使用 Python

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

### 使用 Node.js

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

## 第 5 步：檢查您的儀表板

### 監控郵件狀態

1. 登入您的 LiteStartup 儀表板
2. 前往 **Emails**（郵件）區塊
3. 您應該能看到您已發送的郵件，包含：
   - 投遞狀態
   - 開啟追蹤（若已啟用）
   - 點擊追蹤（若已啟用）
   - 時間戳記

### 查看郵件詳情

點擊任何郵件以查看：
- 收件人地址
- 主旨
- 發送時間
- 投遞狀態
- 開啟／點擊事件
- 任何錯誤

## 常見問題與解決方案

### "Invalid API Key"（無效 API 金鑰）錯誤

**問題**：您遇到了身分驗證錯誤。

**解決方案**：
- 驗證您的 API 金鑰是否正確
- 檢查您是否使用了 `Bearer` 前綴：`Authorization: Bearer YOUR_KEY`
- 確認金鑰未過期
- 若需要，產生新的金鑰

### "Domain Not Verified"（網域未驗證）錯誤

**問題**：您無法使用您的網域發送郵件。

**解決方案**：
- 前往 **Settings**（設定） → **Domains**（網域）
- 檢查您的網域是否顯示為 "Verified"（已驗證）
- 若沒有，確認 DNS 記錄是否新增正確
- 等待 5-15 分鐘讓 DNS 生效
- 使用 `test@litestartup.com` 進行測試

### "Rate Limit Exceeded"（超出速率限制）錯誤

**問題**：您發送郵件的速度太快或數量太多。

**解決方案**：
- 等待幾秒鐘後再發送更多郵件
- 升級到更高級的方案以獲得更高的速率限制
- 在您的程式碼中實作指數退避

### 郵件未收到

**問題**：收件人沒有收到郵件。

**解決方案**：
- 檢查郵件是否已投遞（儀表板中狀態 = "delivered"）
- 請收件人檢查垃圾郵件資料夾
- 確認寄件者網域是否已通過驗證
- 檢查收件人電子郵件地址是否正確
- 檢查郵件內容是否含有垃圾郵件觸發詞

## 下一步

現在您已經發送了第一封郵件，接下來可以探索：

1. **[API 參考](/zh-tw/02-api-reference.md)** - 了解所有可用端點
2. **[功能指南](/zh-tw/03-features.md)** - 探索進階功能
3. **[程式碼範例](/zh-tw/04-examples.md)** - 查看更多實作範例
4. **[價格方案](/zh-tw/05-pricing.md)** - 了解計費與升級選項

## 最佳實務

### 郵件內容

- ✓ 始終包含 HTML 與純文字版本
- ✓ 使用清晰、具描述性的主旨
- ✓ 行銷郵件請包含退訂連結
- ✓ 發送給大量名單前先測試郵件
- ✓ 使用 AI 內容助手最佳化主旨

### 整合

- ✓ 將 API 金鑰儲存在環境變數中
- ✓ 實作錯誤處理與重試機制
- ✓ 記錄郵件發送事件以便除錯
- ✓ 監控送達率與退信率
- ✓ 使用 Webhooks 追蹤郵件事件

### 安全

- ✓ 切勿硬編碼 API 金鑰
- ✓ 定期輪換 API 金鑰
- ✓ 所有 API 呼叫都使用 HTTPS
- ✓ 發送前先驗證電子郵件地址
- ✓ 在您端實作速率限制

## 疑難排解

### 需要協助？

- 查看 [API 參考](/zh-tw/02-api-reference.md) 取得詳細文件
- 查看適合您程式語言的 [程式碼範例](/zh-tw/04-examples.md)
- 查看 [功能指南](/zh-tw/03-features.md) 取得特定功能的協助
- 透過您的儀表板聯絡支援

---

**準備好探索更多了嗎？** 查看 [API 參考](/zh-tw/02-api-reference.md) 或 [程式碼範例](/zh-tw/04-examples.md)！
