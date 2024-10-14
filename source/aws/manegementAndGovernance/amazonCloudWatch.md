# Amazon CloudWatch

## 概要
- インフラ監視とサービス監視などのシステム監視を行う統合的な運用監視サービスである
- CloudWatchイベントを発生させる
- CloudWatchメトリクスを監視

## 主な機能
- **CloudWatch Logs**：ログの一元管理、検索、フィルタリングが可能。ログの保持期間は無制限まで設定可能。
- **CloudWatch メトリクス**：CPU使用率やHTTPリクエストなどの標準メトリクスとカスタムメトリクスがある。CloudWatchエージェントをインストールすることでAWS以外のリソースのメトリクスを取得可能。
- **CloudWatch Alarm**:事前に設定した閾値の超過や機械学習による異常検知により、アラームを発生することができる。
- **CloudWatch Events**:イベントとルールに基づき、ターゲットに対しアクションを起こすことができる。スケジュール（毎週水曜日の0時ごとに、など）とイベント（CPU使用率が80％を超えたとき、など）の2種類がある。　　
→現在はAmazon EventBridgeになっている？

## 他サービスとの連携
- **CloudTrail,Route53,Lambdaなど**：AWSの各サービスと連携し、ログの収集を行う

## CloudWatch エージェントノセットアップ
1. 対象リソースにIAMポリシーをアタッチ
2. Systems ManagerからCloudWatchエージェントをインストール、設定
3. CloudWatchの設定
