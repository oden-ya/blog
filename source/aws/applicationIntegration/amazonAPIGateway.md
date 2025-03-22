# Amazon API Gateway

## 概要
- ウェブアプリケーションで使われるインターフェース
- 簡単にAPIの作成、保護、公開、モニタリングが可能なフルマネージドサービス
- HTTP API、REST API、WebSocket APIをサポート

## 主な機能
- **統合リクエストの統合タイプ**：Lambda関数がリクエストを処理するLambda、EC2などのHTTPベースのパックエンドを指定するHTTPエンドポイント、VPC内にあるHTTPリソースへリクエストを送るプライベート、バックエンドとの統合を行わずにレスポンスを返すMockなどがある。
  
## 設定手順
1. API Gatewayの種類を選択する
   - HTTP API
   - REST API
   - WebSocket API
2. API名、エンドポイントタイプを指定
3. メソッドを設定
   - Any、Get、Head、Post、Delete
4. 統合タイプ
   - Lambda関数、HTTP、Mock、AWSサービス、VPCリンク
5. テスト
   - クエリ文字列を指定してAPIを実行
6. デプロイ
   - APIエンドポイントURLが生成される