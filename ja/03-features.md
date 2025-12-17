# 機能ガイド

LiteStartup が提供する強力な機能をすべて確認し、スタートアップの成功を後押ししましょう。

## Workmail - ビジネスメール

LiteStartup にはビジネスメール機能が標準で含まれており、Google Workspace のような別サービスを契約する必要がありません。

### Workmail とは？

Workmail は、LiteStartup に直接統合されたフル機能のビジネスメールサービスです。追加のサブスクリプションなしで、独自ドメインからメールの送受信ができます。

### メリット

- **コスト削減**: チームメンバー 1 人あたり年 $72-144（vs. Google Workspace）
- **統合プラットフォーム**: メールとマーケティングを 1 か所で
- **プロフェッショナルな印象**: 独自ドメインを利用
- **充実した機能**: 転送、エイリアス、自動返信

### Workmail を始める

1. **Settings** → **Workmail** に移動
2. ドメインを追加（例：`hello@yourdomain.com`）
3. DNS レコードを検証
4. チームメンバー用のメールアカウントを作成
5. メールの送受信を開始

### メールアカウントを作成

```
1. Click "Add Email Account"
2. Enter username (e.g., "john")
3. Set password
4. Assign to team member
5. Click "Create"
```

メールアドレスは次の形式になります：`john@yourdomain.com`

### メール転送

自動転送を設定します：

```
1. Go to email account settings
2. Click "Forwarding"
3. Enter forwarding address
4. Confirm forwarding
5. Emails now forward automatically
```

### 自動返信

自動返信を設定します：

```
1. Go to email account settings
2. Click "Auto-Responder"
3. Enable auto-responder
4. Set message and date range
5. Save
```

## AI Content Assistant

LiteStartup の AI Content Assistant は、より良いメールをより速く作成するのに役立ちます。

### 機能

- **件名生成**: AI が最適化された件名候補を提案
- **メール本文**: 本文コンテンツを生成
- **A/B テスト**: テスト用のバリエーションを作成
- **トーン調整**: ブランドの語り口に合わせる
- **最適化**: 開封率を改善するための提案

### AI アシスタントを使う

#### 件名を生成

```
1. Click "AI Assistant" in email editor
2. Select "Generate Subject Lines"
3. Describe your email purpose
4. AI generates 5 variations
5. Click to use or regenerate
```

例：
- Input: "Welcome email for new users"
- AI Suggestions:
  - "Welcome! Get started in 3 minutes"
  - "You're in! Here's what's next"
  - "Welcome aboard - your journey starts now"

#### メール本文を生成

```
1. Click "AI Assistant"
2. Select "Generate Email Body"
3. Provide key points
4. Choose tone (professional, friendly, casual)
5. AI generates email content
6. Edit and customize as needed
```

#### A/B テスト用のバリエーション

```
1. Click "AI Assistant"
2. Select "Create A/B Variations"
3. AI generates alternative versions
4. Choose which to test
5. LiteStartup tracks performance
```

### AI で書くコツ

- ✓ 目的を具体的にする
- ✓ ターゲット読者を明確にする
- ✓ 望むトーンを指定する
- ✓ 含めたい要点を提示する
- ✓ AI の提案を確認し、必要に応じて調整する

## オートメーションとワークフロー

ユーザー行動に基づいてメールを自動送信する、インテリジェントなワークフローを作成します。

### ワークフローの種類

#### ウェルカムシリーズ

新規購読者に対して、複数通のメールを自動で送信します。

```
1. Go to Automation → Workflows
2. Click "Create Workflow"
3. Select "Welcome Series"
4. Add emails (1-5 emails)
5. Set delays between emails
6. Activate workflow
```

ウェルカムシリーズの例：
- Email 1: Welcome (immediate)
- Email 2: Getting Started (1 day later)
- Email 3: Feature Highlight (3 days later)
- Email 4: Success Story (7 days later)

#### リエンゲージメントキャンペーン

非アクティブな購読者を呼び戻します。

```
1. Create workflow
2. Select "Re-engagement"
3. Set inactivity threshold (e.g., 30 days)
4. Add re-engagement emails
5. Set follow-up actions
6. Activate
```

#### Win-back キャンペーン

最近購入していない顧客を対象にします。

```
1. Create workflow
2. Select "Win-back"
3. Define inactive period
4. Create compelling offer
5. Set retry schedule
6. Activate
```

#### カゴ落ち（カート放棄）リカバリー

カートに残った商品を顧客にリマインドします。

```
1. Create workflow
2. Select "Abandoned Cart"
3. Set delay (e.g., 1 hour)
4. Customize email with product details
5. Add follow-up emails
6. Activate
```

### ワークフローのトリガー

ワークフローは次の条件でトリガーできます：

- **ユーザー操作**: Signup, purchase, download
- **時間ベース**: 特定日時、記念日
- **行動ベース**: opens, clicks, inactivity
- **カスタム**: API triggers, webhooks

### ワークフローの条件

条件を追加してワークフローの分岐を制御できます：

```
IF user.plan == "pro" THEN send_email("pro_features")
IF user.location == "US" THEN send_email("us_offer")
IF user.opened_count > 5 THEN send_email("vip_offer")
```

### ワークフロー分析

ワークフローのパフォーマンスを監視します：

- 送信数
- 配信率
- 開封率
- クリック率
- コンバージョン率
- 生成された売上

## 購読フォーム

埋め込み可能な登録フォームで購読者リストを増やします。

### 購読フォームを作成

```
1. Go to Forms → Create Form
2. Choose form type:
   - Simple signup
   - Double opt-in
   - Custom fields
3. Design form
4. Add fields (email, name, custom fields)
5. Set confirmation message
6. Get embed code
```

### フォームの種類

#### シンプル登録

素早く登録できる 1 ステップのフォームです。

```html
<iframe src="https://forms.litestartup.com/simple/form_id"></iframe>
```

#### ダブルオプトイン

コンプライアンス対応の 2 段階確認です。

```
1. User enters email
2. Confirmation email sent
3. User clicks confirmation link
4. Subscription confirmed
```

#### カスタム項目

追加情報を収集できます：

```
- Email (required)
- Name (optional)
- Company (optional)
- Plan Interest (dropdown)
- Budget (multiple choice)
```

### フォームのカスタマイズ

- **Colors**: ブランドに合わせる
- **Text**: ラベルやメッセージをカスタマイズ
- **Fields**: 項目の追加/削除
- **Redirect**: 登録後のリダイレクト
- **Webhook**: データを自社システムへ送信

### フォームの埋め込み

#### Webサイトに設置

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

#### ランディングページに設置

```html
<!-- Embed directly -->
<iframe src="https://forms.litestartup.com/form_id" 
        width="100%" height="500"></iframe>
```

#### ポップアップフォーム

```javascript
LiteStartup.showPopup('form_id', {
  trigger: 'exit', // Show on exit intent
  delay: 5000,     // Show after 5 seconds
  frequency: 'once' // Show once per session
});
```

## ウェイトリスト管理

ローンチ前にウェイトリストを運用して期待感を高めます。

### ウェイトリストを作成

```
1. Go to Waitlist → Create Waitlist
2. Name your waitlist
3. Set launch date
4. Customize signup page
5. Generate signup link
6. Share with audience
```

### ウェイトリスト機能

- **リファラル追跡**: 友達紹介で順位が上がる
- **招待コード**: 個別の招待コードを送信
- **ランキング**: 待ち順の位置を表示
- **メール通知**: 招待時に通知
- **分析**: 登録流入元を追跡

### リファラルプログラム

友達紹介で早期アクセスを獲得できるようにします：

```
1. Enable referral in waitlist settings
2. Users get unique referral link
3. Each successful referral = 1 spot
4. Leaderboard shows top referrers
5. Send invites to top referrers first
```

### 招待を送信

```
1. Go to Waitlist → Manage
2. Select users to invite
3. Generate invite codes
4. Send invite emails
5. Track acceptance
```

### ウェイトリスト分析

ウェイトリストの成長を監視します：

- 登録数合計
- リファラル経由の登録
- コンバージョン率
- 上位リファラー
- 登録流入元
- 地理分布

## メールテンプレート

再利用可能なメールテンプレートを作成・管理します。

### テンプレートライブラリ

あらかじめ用意されたテンプレートにアクセスできます：

- ウェルカムメール
- プロモーションメール
- トランザクションメール
- ニュースレターテンプレート
- イベント招待
- パスワードリセット

### カスタムテンプレートを作成

```
1. Go to Templates → Create
2. Choose layout
3. Add content blocks
4. Insert variables ({{name}}, {{company}})
5. Preview
6. Save template
```

### テンプレート変数

テンプレートでは動的変数を利用できます：

```
Hello {{first_name}},

Welcome to {{company_name}}!

Your account: {{email}}
Plan: {{plan_type}}

Best regards,
The {{company_name}} Team
```

### テンプレートのテスト

送信前にテンプレートをテストします：

```
1. Click "Send Test"
2. Enter test email
3. Review email
4. Make adjustments
5. Send to list
```

## 連絡先管理

購読者リストを整理・管理します。

### 連絡先をインポート

#### CSV インポート

```
1. Go to Contacts → Import
2. Upload CSV file
3. Map columns to fields
4. Review preview
5. Import
```

CSV 形式：
```
email,first_name,last_name,company,plan
john@example.com,John,Doe,Acme Inc,pro
jane@example.com,Jane,Smith,Tech Corp,free
```

#### API インポート

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

### 連絡先を整理

#### タグ

タグで連絡先を整理できます：

```
- "vip"
- "trial_user"
- "paying_customer"
- "inactive"
- "churned"
```

#### セグメント

動的セグメントを作成できます：

```
- Active users (opened email in last 30 days)
- High-value customers (spent > $1000)
- Trial users (signup < 14 days ago)
- Inactive (no activity > 60 days)
```

### 連絡先データ

カスタム属性を保存できます：

```
- Company
- Job title
- Industry
- Location
- Plan type
- Signup date
- Last purchase
- Lifetime value
```

## 分析とレポート

詳細な分析でメールのパフォーマンスを追跡します。

### メール指標

- **Sent**: 送信数合計
- **Delivered**: 配信成功数
- **Bounced**: バウンス（ハード/ソフト）
- **Opened**: ユニーク開封数
- **Clicked**: ユニーククリック数
- **Unsubscribed**: 配信停止リクエスト数
- **Spam**: 迷惑メール報告数

### キャンペーン分析

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

### エンゲージメント追跡

個々のユーザーのエンゲージメントを追跡します：

- 開封
- リンククリック
- 購入履歴
- エンゲージメントスコア
- 最終アクティビティ日時

### カスタムレポート

カスタムレポートを作成できます：

```
1. Go to Reports → Create
2. Select metrics
3. Choose date range
4. Add filters
5. Generate report
6. Export as PDF/CSV
```

## コンプライアンスと到達率

### GDPR 対応

- ✓ 同意管理
- ✓ データエクスポート
- ✓ 忘れられる権利（削除要求）
- ✓ プライバシーポリシーのテンプレート
- ✓ 監査ログ

### CAN-SPAM 対応

- ✓ 明確な配信停止オプション
- ✓ 正確な送信者情報
- ✓ 誤解を招かない件名
- ✓ 物理的な住所の記載
- ✓ 配信停止要求を 10 日以内に反映

### 到達率向上機能

- ✓ SPF/DKIM/DMARC の設定
- ✓ ドメイン検証
- ✓ バウンス管理
- ✓ スパムテスト
- ✓ IP レピュテーション監視

## 連携

### Webhook イベント

リアルタイム通知を受け取ります：

- メール送信
- メール配信
- メール開封
- リンククリック
- メールバウンス
- 配信停止

### API 連携

アプリケーションと連携します：

```php
// Send email via API
$response = $client->post('/emails/send', [
    'to' => 'user@example.com',
    'from' => 'hello@yourdomain.com',
    'subject' => 'Welcome!',
    'html' => '<h1>Hello</h1>'
]);
```

### 外部サービス連携

人気ツールと連携できます：

- Zapier
- Make (Integromat)
- IFTTT
- Slack
- Discord
- カスタム Webhook

---

**次へ:** [Code Examples](/ja/04-examples.md) または [Pricing & Plans](/ja/05-pricing.md) を確認してください。
