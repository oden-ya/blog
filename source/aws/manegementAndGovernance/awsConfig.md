# AWS Config

## 概要
- AWSリソースの構成変更を記録し、評価するためのサービス
- 変更履歴を取得し、設定変更がAWSのベストプラクティスやコンプライアンス要件に準拠しているか評価することができる

## 主な機能/特徴
- **Configルール**：以下のいずれかのルールを設定し、準拠状況を確認することができる
  - AWS Managed Rules：AWS側で用意しているルール
  - Customer Managed Rules：ユーザー側でカスタマイズするルール
- **ルールの評価方法**：変更が発生するたびに記録する方法と変更が発生した際に日次で記録する方法がある
  
## 他サービスとの連携
- **Systems Manager**：Configルールに非準拠のリソースに対して、Automation機能を使用して自動修復することが可能