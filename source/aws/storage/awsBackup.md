# AWS Backup

## 前提
- RPO(Recovery Point Objective)：目標復旧時点。障害発生時点から前回バックアップ時点までの時間
- RTO（Recovery Time Objective）：目標復旧時間。障害が発生してから復旧するまでに要する時間

## 概要
- AWSリソースのデータのバックアップを作成、管理する統合型ソリューションである。
- 以下のサービスをサポートしている
  - EC2
  - DynamoDB,Neptune,DocumentDB,RDS
  - Storage Gateway,FSx,EBS,S3,EFS