# LiteStartup 快速开始指南

只需 5 分钟即可开始使用 LiteStartup。本指南将带您完成注册、设置 API 密钥以及发送您的第一封邮件。

## 前提条件

在开始之前，您需要：

- 一个有效的电子邮箱地址
- 一个网络浏览器
- REST API 的基础知识（用于集成）
- 您的应用程序域名或一个测试域名

## 第 1 步：免费注册

### 创建您的账户

1. 访问 [LiteStartup.com](https://www.litestartup.com)
2. 点击 **"Start Free Today"**（立即免费开始）按钮
3. 输入您的电子邮箱地址
4. 创建一个强密码
5. 点击 **"Sign Up"**（注册）

您将收到一封确认邮件。点击链接以验证您的账户。

### 您将获得

- **免费计划**：每月 10,000 封邮件
- **完整 API 访问权限**：可用所有功能
- **无需信用卡**：完全免费开始
- **随时升级**：随着业务增长随时扩展

## 第 2 步：设置您的 API 密钥

### 生成 API 凭证

1. 登录您的 LiteStartup 仪表板
2. 导航至 **Settings**（设置） → **API Keys**（API 密钥）
3. 点击 **"Generate New API Key"**（生成新 API 密钥）
4. 给您的密钥起一个描述性的名字（例如，"Production API Key"）
5. 点击 **"Create"**（创建）

您的 API 密钥将只显示一次。**请立即复制并安全存储它** - 您将无法再次看到它。

### 保护您的 API 密钥

**重要**：切勿分享您的 API 密钥或将其提交到版本控制系统。

将其存储为环境变量：

```bash
# .env 文件
LITESTARTUP_API_KEY=sk_live_xxxxxxxxxxxxx
```

或者在您的应用程序配置中：

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

## 第 3 步：配置您的发件人邮箱

### 添加发件人域名

1.前往 **Settings**（设置） → **Domains**（域名）
2. 点击 **"Add Domain"**（添加域名）
3. 输入您的域名（例如，`hello@yourdomain.com`）
4. 按照 DNS 验证步骤操作：
   - 将提供的 DNS 记录添加到您的域名
   - 等待验证（通常 5-15 分钟）
5. 一旦验证通过，您就可以从该域名发送邮件

### 验证您的发件人邮箱

用于测试，您可以使用：

```
test@litestartup.com
```

这是一个测试域名，无需 DNS 验证即可立即工作。

## 第 4 步：发送您的第一封邮件

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

## 第 5 步：检查您的仪表板

### 监控邮件状态

1. 登录您的 LiteStartup 仪表板
2. 前往 **Emails**（邮件）部分
3. 您应该能看到您发送的邮件，包含：
   - 投递状态
   - 打开追踪（如果已启用）
   - 点击追踪（如果已启用）
   - 时间戳

### 查看邮件详情

点击任何邮件以查看：
- 收件人地址
- 主题行
- 发送时间
- 投递状态
- 打开/点击事件
- 任何错误

## 常见问题与解决方案

### "Invalid API Key"（无效 API 密钥）错误

**问题**：您遇到了身份验证错误。

**解决方案**：
- 验证您的 API 密钥是否正确
- 检查您是否使用了 `Bearer` 前缀：`Authorization: Bearer YOUR_KEY`
- 确保密钥未过期
- 如果需要，生成一个新密钥

### "Domain Not Verified"（域名未验证）错误

**问题**：您无法从您的域名发送邮件。

**解决方案**：
- 前往 **Settings**（设置） → **Domains**（域名）
- 检查您的域名是否显示为 "Verified"（已验证）
- 如果没有，验证 DNS 记录是否添加正确
- 等待 5-15 分钟让 DNS 生效
- 使用 `test@litestartup.com` 进行测试

### "Rate Limit Exceeded"（超出速率限制）错误

**问题**：您发送邮件的速度太快或数量太多。

**解决方案**：
- 等待几秒钟后再发送更多邮件
- 升级到更高级的计划以获得更高的速率限制
- 在您的代码中实施指数退避算法

### 邮件未收到

**问题**：收件人没有收到邮件。

**解决方案**：
- 检查邮件是否已投递（仪表板中状态 = "delivered"）
- 请收件人检查垃圾邮件文件夹
- 验证发件人域名是否已通过身份验证
- 检查收件人邮箱地址是否正确
- 检查邮件内容是否有垃圾邮件触发词

## 下一步

现在您已经发送了第一封邮件，接下来可以探索：

1. **[API 参考](02-api-reference.md)** - 了解所有可用端点
2. **[功能指南](03-features.md)** - 探索高级功能
3. **[代码示例](04-examples.md)** - 查看更多实现示例
4. **[价格方案](05-pricing.md)** - 了解计费和升级选项

## 最佳实践

### 邮件内容

- ✓ 始终包含 HTML 和纯文本版本
- ✓ 使用清晰、描述性的主题行
- ✓ 为营销邮件包含退订链接
- ✓ 在发送给大量列表之前测试邮件
- ✓ 使用 AI 内容助手优化主题行

### 集成

- ✓ 将 API 密钥存储在环境变量中
- ✓ 实施错误处理和重试机制
- ✓ 记录邮件发送事件以进行调试
- ✓ 监控送达率和退信率
- ✓ 使用 Webhooks 追踪邮件事件

### 安全

- ✓ 切勿硬编码 API 密钥
- ✓ 定期轮换 API 密钥
- ✓ 对所有 API 调用使用 HTTPS
- ✓ 在发送前验证邮箱地址
- ✓ 在您的一端实施速率限制

## 故障排除

### 需要帮助？

- 查看 [API 参考](02-api-reference.md) 获取详细文档
- 查看适合您编程语言的 [代码示例](04-examples.md)
- 查看 [功能指南](03-features.md) 获取特定功能的帮助
- 通过您的仪表板联系支持

---

**准备好探索更多了吗？** 查看 [API 参考](02-api-reference.md) 或 [代码示例](04-examples.md)！
