# AWS Systems Manager

## 概要
- AWS及びオンプレを含むハイブリット環境向けオペレーションハブである
- Amazon EC2 Simple Systems Manager（SSM）が前身である

## 主な機能/特徴
- **Parameter Store**：構成データやシークレット情報を管理する
- **AppConfig**:アプリケーションの機能フラグ、設定値、構成データを管理する
- **Patch Manager**: オペレーティングシステムとアプリケーションの両方にパッチを適用することができる。

## Systems Managerの実装例
OSやソフトウェアをアップデートし、複数のEC2インスタンスの状態を保つ
1. Run CommandでEC2インスタンスに対してコマンドを実行する
2. DocumentにState Manager及びRun Commandの実行内容を定義し、保存する
3. AutomationでDocumentに記載された実行内容を自動化する

## 
https://docs.aws.amazon.com/ja_jp/systems-manager/latest/userguide/patch-manager.html