# Amazon S3

## 前提
|  項目  |  Object Storage  | Block Storage  | File Storage  |
| :--- | :--- |:--- |:--- |
| 特徴 | ・階層構造を持たず、データはフラットなアドレス空間に保存 </br> ・メタデータと一意の識別子を持つ</br> ・物理的に離れたサーバーを並列化して、一つのストレージプールとして保存 | ・物理マシンの記憶領域をボリューム単位で分割し、さらに固定長のブロックに切り出してデータを保存する </br> ・階層後続を持たない | ・階層的にデータを保存 </br> ・ファイル名、作成日、サイズあど最低限のメタデータを保存 |
| ユースケース | ・構造化データ、非構造化データ</br> ・幅広い用途 |・ファイルストレージやオブジェクトストレージより低いレイヤー</br> ・コンピュートサービス用| ・コンシューマ用OSで採用|
| AWSサービス | Amazon S3| Amazon EBS | Amazon EFS |

## 概要
- 高い耐久性や高い可用性を持ったオフジェクトストレージサービス
- データレイクやバックアップ、静的コンテンツのホスティングに利用される

## 主な機能/特徴
- **アクセス制御** :IAMポリシー、バケットポリシー、ACLで制御を行うことができる。IAMポリシーでアカウント単位で、バケットポリシーでバケット単位のアクセスを制御することが一般的である。ACLは通常使わない。
- **署名付きURL**：オブジェクトに有効期限、キー、署名などのメタデータを設定する。URLを知る者のみがアクセスすることができる。ダウンロードとアップロードが可能。
- **CORS（Cross-Origin Resource Sharing）**：別のドメイン（Cross Origin）のコンテンツを参照する際に、アクセス許可をする必要がある。
- **オブジェクトロック**：S3上のオブジェクトが削除または上書きされることを防ぐことができる（Write Once Read Many）
  - リテンションモード
    - ガバナンスモード：特権ユーザーのみ削除、上書き、ロック設定が可能。
    - コンプライアンスモード：rootユーザーを含むすべてのユーザーが上書き、削除ができない
  - リーガルホールド：法的な理由からオフジェクトを保護する目的で利用される。オブジェクトロックの保持期間からは独立している。保持期間が未定の場合に利用できる
- **バージョニング**：以前のバージョンのオブジェクトを取り出すことができる。バケット単位で設定が可能。
- **バッチオペレーション**：大量のオブジェクトに対して、一括して処理を行うことができる。オブジェクトのコピーやLambda関数のコール、ACLの置換などができる。
- **S3マルチパートアップロード**：容量の大きなオブジェクトを効率的にアップロードすることができる。

## Tips
- Snowball Edge デバイスから AWS Glacier にデータを直接コピーすることはできない。S3 バケットにコピーし、後でライフサイクルポリシーを使用して AWS Glacier に移行できる。
- バージョニング機能を有効にした状態でオブジェクトを削除すると、オブジェクトを完全に削除する代わりに、Amazon S3 は削除マーカーを挿入し、これが現在のオブジェクトバージョンとなる。