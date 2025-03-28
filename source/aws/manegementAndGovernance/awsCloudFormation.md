# AWS CloudFormation

## 概要
- リソースをテンプレートに定義することで、起動や管理を自動化するIaCサービスである

## 主な機能/特徴
- **Template**：リソースのスペックやデプロイ条件などを記載したJSON/YAMLファイル
- **Stack**：Templateを基に作成されたユニットで、実際にリソースの作成や削除を行うことができる
- **変更セット（Change set）**：リソースの修正に伴う影響を事前に確認することができる
- **ドリフト検出**：テンプレートと実際のAWSリソースの差分を検出できる
- **ロールバック**：異常が発生した場合に、スタックを以前の既知の状態に戻す
  - Retry:スタックを変更せずに再試行する。テンプレート以外の問題によって失敗した場合に有用である。
  - Update：スタックの展開を再試行する前に、テンプレートを修正して更新する
  - Rollback：最後の既知の安定的な状態に戻す
- **リソース属性**：リソースに対して、追加動作や関係を制御するための属性
  - CreationPolicy：リソースの作成完了をCloudFormationに通知する条件を指定
  - DeletionPolicy：リソースが削除される際の動作を定義
  - DependsOn：ほかのリソースへの依存関係を定義
  - Metadata：リソースに関連付けられた補足情報
  - UpdatePolicy：リソースが更新される際のプロセスを管理
  - UpdateReplacePolicy：リソースが置換更新された際にCloudFormationがとるべきアクションを定義
- **ヘルパースクリプト**：CloudFormationのカスタムリソースとしての操作を容易にするための一連のPythonスクリプト
  - cfn-init
    - サービスの開始で使用される
    - リソースメタデータの取得、パッケージのインストール、ファイルの作成など
  - cfn-signal
    - CreationPolicyまたはWaitConditionでシグナルを送信するために使用される
  - cfn-get-metadata
    - 特定のキーへのリソースまたはパスのメタデータを取得する
  - cfn-hup
    - メタデータへの更新を確認し、変更が検出されたときにカスタムフックを実行する