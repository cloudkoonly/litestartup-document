# LiteStartup 简介
 
 LiteStartup（官网定位：*Lite Email for Startups*）是一套面向创业团队的 **AI 驱动邮件服务平台**，把 *Workmail（企业邮箱）*、*Transactional Email（事务邮件）*、*Marketing Email（营销邮件）* 等能力整合在一个产品里，并提供可直接调用的 REST API，帮助你用更低成本、更少配置完成邮件发送与增长触达。
 
 ## LiteStartup 是什么？
 
 LiteStartup 是一款 SaaS 邮件平台，核心定义可以概括为：
 
 - **用 AI 改造邮件工作流的邮件服务模型**：从内容生成到自动化触达，尽可能减少人工操作
 - **同时覆盖“企业邮箱 + 营销邮件 + 事务邮件”**：减少多供应商拼装
 - **面向开发者的简单集成**：无需复杂 SDK，通过标准 RESTful API 快速接入
 
 与传统按联系人计费的邮件平台不同，LiteStartup 主打 **按实际发送量计费（pay per email sent）**，而不是按联系人数量收费。
 
 ## 核心特性（What Makes Us Different）
 
 ### Workmail Like Gmail（企业邮箱）
 可在几分钟内开通类似 `support@yourcompany.com` 的企业邮箱能力，减少额外采购与配置成本。
 
 ### AI Content Assistant（AI 内容助手）
 AI 生成营销邮件内容，并给出 A/B 测试变体；从想法到发送可以更快完成。
 
 ### Affordable（按发送计费，更轻量）
 - **按邮件发送量计费**：不是按联系人计费
 - **超额费用**：$0.20 / 1,000 emails（超过套餐额度后）
 - **示例套餐**：Pro 为 $20/月，包含 110,000 emails/月
 
 ### Enterprise Infrastructure（企业级基础设施）
 官方描述为由 AWS 与 Google Cloud 工程师构建，提供较高可用与合规能力（SOC2 & GDPR）。
 
 ### Free Email Notifications（免费通知邮箱）
 提供类似 `yourname@litestartup.net` 的通知邮箱，用于告警、报表、更新等，减少通知系统搭建成本。
 
 ### AI Website Builder（AI 建站/落地页）
 通过与 AI 对话快速生成高转化落地页/Waitlist 页/Newsletter/Blog 等，无需写代码。
 
 ### Ticket + Live Chat（工单与在线客服）
 - Ticket：用邮件高效管理客户工单
 - Live Chat：网站实时聊天组件，提升线索转化
 
 ### AI Automation（AI 自动化增长）
 AI 自动发送欢迎、跟进与外呼邮件，并结合线索捕获等能力，形成“常开”的增长自动化。

 ## 谁适合使用 LiteStartup？

 LiteStartup 更适合以下人群/团队：

 - **早期创业团队**：需要快速搭建企业邮箱、营销触达与通知邮件
 - **SaaS 产品**：同时需要事务邮件与营销邮件，并希望用统一平台管理
 - **增长/市场团队**：希望用 AI 提升邮件内容产出效率与实验速度
 - **产品团队**：需要 Waitlist、落地页、早期访问邀请等能力
 - **开发者**：偏好标准 REST API、轻量接入、减少 SDK 依赖
 - **希望避免供应商锁定的团队**：更易迁移与替换邮件服务

 ## LiteStartup 如何工作

 ### 1. 注册
 创建账户即可开始使用（免费计划包含每月 10,000 emails）。

 ### 2. 获取 API 凭证
 在控制台获取 API Key。

 ### 3. 集成
 通过 RESTful API 调用发送邮件，适配任何语言/框架。

 ### 4. 发送邮件
 发送事务邮件、营销邮件或触发自动化工作流。

 ### 5. 追踪与优化
 查看基础分析数据，并结合 AI 能力持续迭代邮件内容与转化表现。

 ## LiteStartup vs 传统邮件平台
 
|特性|LiteStartup|传统邮件平台|
|------|------------|--------------|
|Workmail（企业邮箱）|✓ Included|✗ Separate service|
|AI Content Assistant|✓ Yes|✗ No|
|计费模型|Per email sent|Per contact|
|接入/配置|5 minutes|30+ minutes|
|API 集成|✓ Simple REST API|✓ Complex SDKs|
|供应商锁定|✗ None|✓ Yes|
|免费额度|10K emails/month|Limited|
|可用性（官网描述）|99.9%|99.9%|

 ## 开始使用
 
 准备开始发送邮件？你可以从下面几步开始：

1. **[快速入门指南](/zh-cn/01-getting-started.md)** - 注册并在 5 分钟内发送你的第一封邮件
2. **[API 文档](/zh-cn/02-api-reference.md)** - 完整的 API 文档和端点
3. **[功能指南](/zh-cn/03-features.md)** - 详细探索所有功能
4. **[代码示例](/zh-cn/04-examples.md)** - 多种语言的实现示例
5. **[定价与计划](/zh-cn/05-pricing.md)** - 了解定价和计费
 
 ## 快速调用示例
 
 用几行代码发送你的第一封邮件：

 ```bash
 curl -X POST https://api.litestartup.com/client/v2/emails \
   -H "Authorization: Bearer YOUR_API_KEY" \
   -H "Content-Type: application/json" \
   -d '{
     "to": "user@example.com",
     "from": "noreply@yourapp.com",
     "subject": "Welcome!",
     "html": "<h1>Hello</h1>"
   }'
 ```

 ## 关键价值
 
 - **成本更可控**：按邮件发送量计费，而不是按联系人计费
 - **生产力更高**：AI 内容助手与 AI 自动化减少人工操作
 - **一体化工具**：Workmail + 邮件发送 + 落地页/Waitlist + Ticket/Live Chat
 - **轻量集成**：REST API，无复杂 SDK 与依赖
 - **更少锁定**：标准 API 设计，迁移与替换成本更低

## 支持与资源

- **文档**：完整的指南和 API 参考

- **代码示例**：多种语言的即用型示例

- **社区**：与其他 LiteStartup 用户交流

## 下一步

- 阅读[入门指南](/zh-cn/01-getting-started.md)

- 浏览[API 参考](/zh-cn/02-api-reference.md)

- 查看[代码示例](/zh-cn/04-examples.md)，找到适合您编程语言的示例

- 查看[定价与套餐](/zh-cn/05-pricing.md)，选择合适的套餐
---

**准备发送你的第一封邮件？** 从 [快速入门指南](/zh-cn/01-getting-started.md) 开始。
