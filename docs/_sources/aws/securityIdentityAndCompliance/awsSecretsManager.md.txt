# AWS Sercrets Manager

## 概要
- シークレット（データベースの認証情報、パスワードなど）のライフサイクルを一元的に管理するサービス

## Secrets ManagerとSystems Managerの比較
|  項目  |  Secrets Manager  | Parameter Store</br>（Systems Manager） |
| :--- | :--- |:--- |
|  ユースケース  | シークレット情報を安全に保管  | システムパラメータやシークレットなど、幅広い文字列を保管 |
|  自動ローテーション |  あり  | なし |
|  コスト  |  有料（シークレット単位、APIコール単位） | なし |
|  対象サービス  | データベースサービス、APIキー  | ほぼすべてのサービス |

