# AWS STS

## 概要
- 外部ユーザーに対してAWSリソースへの一時的なセキュリティ認証情報を付与できる
- 認証情報はユーザーと共に保存されず、動的に生成、提供される
- Security Token Serviceの略

## 主な機能/特徴
- **sts:AssumeRole**：IAMロールから一時認証情報（アクセスキーID、シークレットアクセスキー）を取得して付与できる
  