# LiteStartup の紹介
 
 LiteStartup（Webサイト上では *Lite Email for Startups* として紹介）は、スタートアップ向けの **AI 駆動メールサービスプラットフォーム** です。**Workmail（ビジネスメール）**、**トランザクションメール**、**マーケティングメール** を 1 つのプロダクトに統合し、シンプルな REST API で数分で連携できます。
 
 ## LiteStartup とは？
 
 LiteStartup はスタートアップ向けの SaaS メールプラットフォームです。一言で言うと：
 
 - **AI 駆動のメールサービスモデル** により、メールワークフロー（コンテンツ、オートメーション、配信）を効率化
 - **ビジネスメール + トランザクションメール + マーケティングメール** を統合したスタックで、ベンダーの分散を削減
 - 標準的な RESTful API による **開発者フレンドリーな統合**（複雑な SDK 不要）
 
 連絡先ごとに課金する従来のメールマーケティングプラットフォームとは異なり、LiteStartup は **pay per email sent** を重視します。つまり、連絡先を保管するのではなく、実際に送信した分だけ支払います。
 
 ## LiteStartup の違い
 
 ### Gmail のような Workmail
 `support@yourcompany.com` のようなビジネスメールを数分で使える、唯一のメールマーケティングプラットフォームです。
 
 ### AI Content Assistant
 AI がマーケティングメールと A/B テスト用のバリエーションを生成し、作成と改善のスピードを高めます。
 
 ### 手頃な価格
 連絡先ではなく、送信したメール数に基づいて課金します。
 
 - **Pro**: $20/month for 110,000 emails/month
 - **Overage**: $0.20 per 1,000 emails after limit
 
 ### エンタープライズ品質のインフラ
 AWS と Google Cloud のエンジニアによって構築。SOC2 と GDPR に準拠し、稼働率 99.9% を提供します。
 
 ### 無料のメール通知
 `yourname@litestartup.net` のような無料メールを使って、アラート、レポート、更新情報を好みの受信箱に届けられます。
 
 ### AI Website Builder
 AI とチャットして、ランディングページ、ウェイトリストページ、ニュースレター、ブログを作成できます。コーディングは不要です。
 
 ### Ticket + Live Chat
 チケット（メール経由）とリアルタイムのライブチャットウィジェットで、顧客対応を一元管理できます。
 
 ### AI Automation
 常時稼働のオートメーション：ウェルカム、フォローアップ、アウトリーチのメールを自動化し、リード獲得と成長ワークフローを内蔵しています。
 
 ## LiteStartup はどんな人向け？
 
 LiteStartup は次のような方に最適です：
 
 - 初期段階で最初の顧客基盤を作っている **スタートアップ**
 - トランザクション + マーケティングメールを 1 つにまとめたい **SaaS プロダクト**
 - AI 支援コンテンツで実験を高速化したい **グロースチーム**
 - ランディングページやウェイトリストを運用する **プロダクトチーム**
 - 依存関係の少ないシンプルな REST API を好む **開発者**
 - ベンダーロックインを避け、将来的にプロバイダを切り替えたい **チーム**
 
 ## LiteStartup の仕組み
 
 ### 1. サインアップ
 アカウントを作成し、Free プラン（10,000 emails/month）から開始します。
 
 ### 2. API 認証情報を取得
 ダッシュボードから API key を取得します。
 
 ### 3. 連携
 RESTful API の呼び出しでメール送信します。言語やフレームワークは問いません。
 
 ### 4. メール送信
 トランザクションメール、マーケティングキャンペーン、自動化ワークフローを送信します。
 
 ### 5. 追跡と最適化
 基本的な分析を確認し、AI 支援で改善を回します。
 
 ## LiteStartup と従来のメールプラットフォームの比較
 
 | 機能 | LiteStartup | 従来のプラットフォーム |
 |---|---|---|
 | Workmail (Business Email) | ✓ Included | ✗ Separate service |
 | AI Content Assistant | ✓ Yes | ✗ No |
 | 料金モデル | Per email sent | Per contact |
 | セットアップ時間 | 5 minutes | 30+ minutes |
 | API 連携 | ✓ Simple REST API | ✓ Complex SDKs |
 | ベンダーロックイン | ✗ None | ✓ Yes |
 | 無料枠 | 10K emails/month | Limited |
 | 稼働率（Webサイト） | 99.9% | 99.9% |
 
 ## はじめに
 
 メール送信を始める準備はできましたか？次のステップはこちらです：
 
 1. **[Getting Started Guide](/ja/01-getting-started.md)** - 数分でサインアップして最初のメールを送信
 2. **[API Reference](/ja/02-api-reference.md)** - 完全な API ドキュメントとエンドポイント
 3. **[Features Guide](/ja/03-features.md)** - すべての機能を詳しく確認
 4. **[Code Examples](/ja/04-examples.md)** - 複数言語の実装例
 5. **[Pricing & Plans](/ja/05-pricing.md)** - 料金と請求を理解
 
 ## クイックスタート例
 
 数行のコードで最初のメールを送信できます：

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
 
 ## 主なメリット
 
 - **低コスト** - 連絡先ではなく送信したメール数に応じて課金
 - **高い生産性** - AI content assistance と AI automation で手作業を削減
 - **オールインワン** - Workmail + 送信 + ランディングページ/ウェイトリスト + Ticket/Live chat
 - **迅速な連携** - 複雑な SDK に依存しない REST API
 - **ロックインを軽減** - 標準 API でプロバイダの切り替えが容易
 
 ## サポートとリソース
 
 - **Documentation**: 完全なガイドと API リファレンス
 - **Code Examples**: 複数言語のすぐ使えるサンプル
 - **Community**: 他の LiteStartup ユーザーとつながる
 
 ## 次のステップ
 
 - [Getting Started Guide](/ja/01-getting-started.md) で始める
 - [API Reference](/ja/02-api-reference.md) を確認する
 - 使用言語の [Code Examples](/ja/04-examples.md) を参照する
 - [Pricing & Plans](/ja/05-pricing.md) で最適なプランを見つける

---
 
 **最初のメールを送る準備はできましたか？** [Getting Started Guide](/ja/01-getting-started.md) から始めましょう。
