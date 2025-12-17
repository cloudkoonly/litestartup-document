# 功能指南

探索 LiteStartup 提供的所有强大功能，帮助您的初创企业取得成功。

## Workmail - 企业邮箱

LiteStartup 内置了企业邮箱功能，无需再使用 Google Workspace 等独立的邮件服务。

### 什么是 Workmail？

Workmail 是一项直接集成到 LiteStartup 中的全功能企业邮箱服务。您可以直接使用自定义域名发送和接收邮件，无需额外订阅其他服务。

### 优势

- **省钱**：每个团队成员每年可节省 72-144 美元（对比 Google Workspace）
- **统一平台**：邮件和营销合二为一
- **专业形象**：使用您的自定义域名
- **功能齐全**：转发、别名、自动回复

### 开始使用 Workmail

1. 前往 **Settings**（设置） → **Workmail**
2. 添加您的域名（例如，`hello@yourdomain.com`）
3. 验证 DNS 记录
4. 为团队成员创建邮箱账户
5. 开始发送和接收邮件

### 创建邮箱账户

```
1. 点击 "Add Email Account"（添加邮箱账户）
2. 输入用户名（例如，"john"）
3. 设置密码
4. 分配给团队成员
5. 点击 "Create"（创建）
```

邮箱地址将是：`john@yourdomain.com`

### 邮件转发

设置自动转发：

```
1. 前往邮箱账户设置
2. 点击 "Forwarding"（转发）
3. 输入转发地址
4. 确认转发
5. 邮件现在将自动转发
```

### 自动回复

设置自动回复：

```
1. 前往邮箱账户设置
2. 点击 "Auto-Responder"（自动回复）
3. 启用自动回复
4. 设置消息和日期范围
5. 保存
```

## AI 内容助手

LiteStartup 的 AI 内容助手帮助您更快地写出更好的邮件。

### 功能

- **生成主题行**：AI 建议优化的主题行
- **邮件正文**：生成邮件正文内容
- **A/B 测试**：创建用于测试的变体
- **语气调整**：匹配您的品牌声音
- **优化**：提供提高打开率的建议

### 使用 AI 助手

#### 生成主题行

```
1. 在邮件编辑器中点击 "AI Assistant"（AI 助手）
2. 选择 "Generate Subject Lines"（生成主题行）
3. 描述您的邮件目的
4. AI 生成 5 个变体
5. 点击使用或重新生成
```

示例：
- 输入："Welcome email for new users"（新用户欢迎邮件）
- AI 建议：
  - "Welcome! Get started in 3 minutes"（欢迎！3分钟内开始使用）
  - "You're in! Here's what's next"（您已加入！接下来做什么）
  - "Welcome aboard - your journey starts now"（欢迎登船 - 您的旅程现在开始）

#### 生成邮件正文

```
1. 点击 "AI Assistant"
2. 选择 "Generate Email Body"（生成邮件正文）
3. 提供关键点
4. 选择语气（专业、友好、随意）
5. AI 生成邮件内容
6. 根据需要进行编辑和自定义
```

#### A/B 测试变体

```
1. 点击 "AI Assistant"
2. 选择 "Create A/B Variations"（创建 A/B 变体）
3. AI 生成替代版本
4. 选择要测试的版本
5. LiteStartup 追踪表现
```

### AI 写作技巧

- ✓ 明确您的目标
- ✓ 提及您的目标受众
- ✓ 指定期望的语气
- ✓ 提供包含的关键信息
- ✓ 审查并自定义 AI 的建议

## 自动化与工作流

创建智能工作流，根据用户行为自动发送邮件。

### 工作流类型

#### 欢迎系列

向新订阅者自动发送一系列邮件。

```
1. 前往 Automation（自动化） → Workflows（工作流）
2. 点击 "Create Workflow"（创建工作流）
3. 选择 "Welcome Series"（欢迎系列）
4. 添加邮件（1-5 封邮件）
5. 设置邮件之间的延迟
6. 激活工作流
```

欢迎系列示例：
- 邮件 1：欢迎（立即发送）
- 邮件 2：快速开始（1 天后）
- 邮件 3：功能亮点（3 天后）
- 邮件 4：成功案例（7 天后）

#### 重新互动营销

挽回不活跃的订阅者。

```
1. 创建工作流
2. 选择 "Re-engagement"（重新互动）
3. 设置不活跃阈值（例如，30 天）
4. 添加重新互动邮件
5. 设置后续动作
6. 激活
```

#### 挽回营销

针对近期未购买的客户。

```
1. 创建工作流
2. 选择 "Win-back"（挽回）
3. 定义不活跃期间
4. 创建有吸引力的优惠
5. 设置重试计划
6. 激活
```

#### 弃购挽回

提醒客户购物车中遗留的商品。

```
1. 创建工作流
2. 选择 "Abandoned Cart"（弃购挽回）
3. 设置延迟（例如，1 小时）
4. 自定义包含产品详情的邮件
5. 添加后续邮件
6. 激活
```

### 工作流触发器

工作流可以通过以下方式触发：

- **用户动作**：注册、购买、下载
- **基于时间**：特定日期/时间、纪念日
- **行为**：打开、点击、不活跃
- **自定义**：API 触发器、Webhooks

### 工作流条件

添加条件以控制工作流向：

```
IF user.plan == "pro" THEN send_email("pro_features")
IF user.location == "US" THEN send_email("us_offer")
IF user.opened_count > 5 THEN send_email("vip_offer")
```

### 工作流分析

监控工作流表现：

- 发送的邮件数
- 投递率
- 打开率
- 点击率
- 转化率
- 产生的收入

## 订阅表单

使用嵌入式注册表单建立您的订阅者列表。

### 创建订阅表单

```
1. 前往 Forms（表单） → Create Form（创建表单）
2. 选择表单类型：
   - 简单注册
   - 双重确认 (Double opt-in)
   - 自定义字段
3. 设计表单
4. 添加字段（邮箱、姓名、自定义字段）
5. 设置确认消息
6. 获取嵌入代码
```

### 表单类型

#### 简单注册

用于快速注册的单步表单。

```html
<iframe src="https://forms.litestartup.com/simple/form_id"></iframe>
```

#### 双重确认 (Double Opt-in)

用于合规的两步确认。

```
1. 用户输入邮箱
2. 发送确认邮件
3. 用户点击确认链接
4. 订阅已确认
```

#### 自定义字段

收集额外信息：

```
- 邮箱（必填）
- 姓名（可选）
- 公司（可选）
- 计划意向（下拉菜单）
- 预算（多选）
```

### 表单自定义

- **颜色**：匹配您的品牌
- **文本**：自定义标签和消息
- **字段**：添加/移除字段
- **重定向**：注册后重定向
- **Webhook**：将数据发送到您的系统

### 嵌入表单

#### 在网站上

```html
<div id="litestartup-form"></div>
<script>
  LiteStartup.loadForm('form_id', {
    container: '#litestartup-form',
    onSuccess: function() {
      console.log('User subscribed!');
    }
  });
</script>
```

#### 在着陆页上

```html
<!-- 直接嵌入 -->
<iframe src="https://forms.litestartup.com/form_id" 
        width="100%" height="500"></iframe>
```

#### 弹出表单

```javascript
LiteStartup.showPopup('form_id', {
  trigger: 'exit', // 在退出意图时显示
  delay: 5000,     // 5 秒后显示
  frequency: 'once' // 每个会话显示一次
});
```

## 等候名单管理

在发布前通过等候名单管理建立热度。

### 创建等候名单

```
1. 前往 Waitlist（等候名单） → Create Waitlist（创建等候名单）
2. 命名您的等候名单
3. 设置发布日期
4. 自定义注册页面
5. 生成注册链接
6. 分享给受众
```

### 等候名单功能

- **推荐追踪**：用户通过推荐朋友获得位置
- **邀请码**：发送个性化邀请码
- **排名**：显示用户在等候名单上的位置
- **邮件通知**：受邀时通知
- **分析**：追踪注册来源

### 推荐计划

允许用户通过推荐朋友获得早期访问权限：

```
1. 在等候名单设置中启用推荐
2. 用户获得唯一的推荐链接
3. 每次成功推荐 = 1 个位置
4. 排行榜显示顶级推荐人
5. 首先向顶级推荐人发送邀请
```

### 发送邀请

```
1. 前往 Waitlist（等候名单） → Manage（管理）
2. 选择要邀请的用户
3. 生成邀请码
4. 发送邀请邮件
5. 追踪接受情况
```

### 等候名单分析

监控等候名单增长：

- 总注册数
- 推荐注册数
- 转化率
- 顶级推荐人
- 注册来源
- 地理分布

## 邮件模板

创建和管理可复用的邮件模板。

### 模板库

访问预构建的模板：

- 欢迎邮件
- 促销邮件
- 交易邮件
- 通讯模板
- 活动邀请
- 密码重置

### 创建自定义模板

```
1. 前往 Templates（模板） → Create（创建）
2. 选择布局
3. 添加内容块
4. 插入变量 ({{name}}, {{company}})
5. 预览
6. 保存模板
```

### 模板变量

在模板中使用动态变量：

```
Hello {{first_name}},

Welcome to {{company_name}}!

Your account: {{email}}
Plan: {{plan_type}}

Best regards,
The {{company_name}} Team
```

### 模板测试

在发送前测试模板：

```
1. 点击 "Send Test"（发送测试）
2. 输入测试邮箱
3. 审查邮件
4. 进行调整
5. 发送给列表
```

## 联系人管理

组织和管理您的订阅者列表。

### 导入联系人

#### CSV 导入

```
1. 前往 Contacts（联系人） → Import（导入）
2. 上传 CSV 文件
3. 将列映射到字段
4. 审查预览
5. 导入
```

CSV 格式：
```
email,first_name,last_name,company,plan
john@example.com,John,Doe,Acme Inc,pro
jane@example.com,Jane,Smith,Tech Corp,free
```

#### API 导入

```php
$contacts = [
    ['email' => 'john@example.com', 'name' => 'John'],
    ['email' => 'jane@example.com', 'name' => 'Jane']
];

foreach ($contacts as $contact) {
    $response = $client->post('/contacts', [
        'email' => $contact['email'],
        'name' => $contact['name']
    ]);
}
```

### 组织联系人

#### 标签 (Tags)

使用标签组织联系人：

```
- "vip"
- "trial_user"（试用用户）
- "paying_customer"（付费客户）
- "inactive"（不活跃）
- "churned"（流失）
```

#### 分群 (Segments)

创建动态分群：

```
- 活跃用户（过去 30 天内打开过邮件）
- 高价值客户（消费 > $1000）
- 试用用户（注册 < 14 天前）
- 不活跃（无活动 > 60 天）
```

### 联系人数据

存储自定义属性：

```
- 公司
- 职位
- 行业
- 地点
- 计划类型
- 注册日期
- 最后购买
- 生命周期价值
```

## 分析与报告

使用详细的分析追踪邮件表现。

### 邮件指标

- **Sent**：发送总数
- **Delivered**：成功投递
- **Bounced**：硬/软退信
- **Opened**：独立打开
- **Clicked**：独立点击
- **Unsubscribed**：退订请求
- **Spam**：垃圾邮件投诉

### 营销活动分析

```
Campaign: Q1 Newsletter
├── Sent: 10,000
├── Delivered: 9,950 (99.5%)
├── Bounced: 50 (0.5%)
├── Opened: 4,500 (45.2%)
├── Clicked: 1,200 (12.0%)
├── Unsubscribed: 50 (0.5%)
└── Conversion: 150 (1.5%)
```

### 参与度追踪

追踪单个用户的参与度：

- 邮件打开
- 链接点击
- 购买历史
- 参与度评分
- 最后活动日期

### 自定义报告

创建自定义报告：

```
1. 前往 Reports（报告） → Create（创建）
2. 选择指标
3. 选择日期范围
4. 添加过滤器
5. 生成报告
6. 导出为 PDF/CSV
```

## 合规性与送达率

### GDPR 合规性

- ✓以此同意管理
- ✓ 数据导出
- ✓ 被遗忘权
- ✓ 隐私政策模板
- ✓ 审计日志

### CAN-SPAM 合规性

- ✓ 清晰的退订选项
- ✓ 准确的发件人信息
- ✓ 诚实的主题行
- ✓ 必须提供物理地址
- ✓ 10 天内处理退订

### 送达率功能

- ✓ SPF/DKIM/DMARC 设置
- ✓ 域名验证
- ✓ 退信管理
- ✓ 垃圾邮件测试
- ✓ IP 声誉监控

## 集成

### Webhook 事件

接收实时通知：

- 邮件已发送
- 邮件已投递
- 邮件已打开
- 链接被点击
- 邮件被退回
- 已退订

### API 集成

与您的应用程序集成：

```php
// Send email via API
$response = $client->post('/emails/send', [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
]);
```

### 第三方集成

连接流行工具：

- Zapier
- Make (Integromat)
- IFTTT
- Slack
- Discord
- 自定义 Webhooks

---

**下一步：** 查看 [代码示例](/zh-cn/04-examples.md) 或 [价格方案](/zh-cn/05-pricing.md)！
