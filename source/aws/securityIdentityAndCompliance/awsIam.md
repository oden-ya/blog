# AWS IAM

## 概要
- AWSリソースへのアクセス権限やプリンシパルの管理をするためのサービス
- Identity and Access Managementの略

## 主な機能/特徴
- **IAMユーザー**：IAMで定義したアイデンティティ。MFA（多要素認証）を有効にすることでより強固なセキュリティを実現できる。
- **IAMグループ**：IAMユーザーの集合体。個々のIAMユーザーの管理の手間や権限の誤設定のリスクを減らすことができる
- **ルートユーザー**：AWSアカウントの所有者。AWS OrganizationsのSCPで制限しない限りはAWSアカウントに対するすべての操作が可能である。<br>
AWSアカウントの設定変更、請求に関する設定などはルートユーザーでした操作ができない。
- **IAMポリシー**：どのリソースにどのようなアクションを許可するか。
  - アタッチ先による分類
    - アイデンティティベース：IAMユーザー、グループ、ロールをアタッチして、アクセス許可を設定
    - リソースベース：リソースにアタッチしてアクセス許可を設定
  - カスタマイズ方法による分類
    - インラインポリシー：IAMエンティティ（ユーザー、グループ、ロール）に埋め込むポリシー
    - AWS管理ポリシー：AWSが既定で用意しているポリシー（admin,PowerUser）
    - カスタマー管理ポリシー：ユーザーがカスタマイズする
- **ジョブ機能の管理ポリシー**：AWS管理ポリシーのうち、特定のジョブ機能と連携するように設計されたポリシー（Administrator,Billing,Database Administratorなど）
- **Pernmissions Boundary(アクセス権限の境界)**：IAMエンティティに対して通常のパーミッションを制限するためのポリシーである。IAMエンティティの権限はPernmissions PolicyとPernmissions BoundaryのAND部分が適用される。自由にIAMロールを作成可能な状態にしてしまうと、利用者に与えられている権限や禁止したい操作を超えたIAMロールを作成してスイッチすることができてしまうため、Pernmissions Boundaryを利用して阻止することができる。
- **スイッチロール**：特定のIAMユーザーから別のIAMロールに切り替えること。クロスアカウントでも設定が可能
- **混乱した代理問題**：アクションを実行する許可を持たないエンティティがより高い特権を持つ別のエンティティに代わってそのアクションを許可するセキュリティの脆弱性問題。<br>
最小権限の原則やアクションの明示的な拒否、STSによる期限設定、外部IDの設定などが回避策として挙げられる。
- **IAMアクセスアナライザー**：外部リソースの信頼関係の検証、ポリシーの検証などを行う。
- **AWS IAM Identity Center**: AWS Organizations上のすべてのアカウントに対するアクセス許可を一元管理し、シングルサインオンを実現できる。IDストアでユーザーIDを作成して管理する。
  
## クロスアカウントでの許可・拒否設定
アクションを実行するアイデンティティとアクションを受けるリソースが別々のAWSアカウントである。
- クロスアカウントの場合はアイデンティティ側のポリシーとリソース側のポリシーのAND条件で適用される<br>
→特定のアクションをAllowする場合は明示的なAllowが必要
- 単一アカウントの場合は、OR条件で適用される<br>
→特定のアクションをDenyしたい場合は、明示的なDenyが必要

## RBACとABAC
ポリシーによってRBAC（Roll-Based Access Control、ロールベースのアクセス制御）とABAC（Attribute-Based Access Control、属性ベースのアクセス制御）がある
代表的なRBACには、ジョブ機能の管理ポリシーがあり、ABACは属性（タグ）を設定することで定義することができる。
```json:abac-policy.json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                    "rds:DescribeDBInstances",
            ],
            "Resource": "*"
        },
        
        {
            "Effect": "Allow",
            "Action": [
                "rds:RebootDBInstance",
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "aws:PrincipalTag/Department": "DBAdmins",
                    "rds:db-tag/Environment": "Production"
                }
            }
        }
    ]
}



```

## ポリシーの評価論理
AWSアカウント内でのリクエストの許可または拒否の決定は以下のポリシーの評価倫理フローで判断することができる。
![policy-eval-denyallow](image/awsIam/policy-eval-denyallow.jpeg)

## Tips
- アイデンティティベースのポリシーは、IAM ユーザー、グループ、ロールにアタッチされる。これらのポリシーを使用すると、そのアイデンティティが実行できる内容 (そのアクセス許可) を指定できる。たとえば、John という名前の IAM ユーザーに Amazon EC2 RunInstances アクションを実行することを許可するポリシーをアタッチできる。
- リソースベースのポリシーはリソースにアタッチされる。例えば、リソースベースのポリシーをAmazon S3 バケット、Amazon SQS キュー、VPC エンドポイント、AWS Key Management Service 暗号化キー、Amazon DynamoDB テーブルとストリームにアタッチできる。
- 
## 参考
https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/access_policies_identity-vs-resource.html

https://qiita.com/tsukamoto/items/e069ca89d1b78a6e5c1f