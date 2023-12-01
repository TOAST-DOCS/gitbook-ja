## NHN Cloud > リソース提供ポリシー
NHN Cloudは、全てのお客様に安定的なサービスを提供し、意図しないリソース生成によって発生する支出などからユーザーを保護するためにリソース使用量ポリシーを設定しています。 

### 組織/プロジェクトリソース提供ポリシー
組織のリソースは決済方法を登録した会員を基準に計算され、プロジェクトは組織を基準に計算されます。

|リソース | 会員タイプ | 提供基準 | 提供量 | 
|----|----|----|----|
|組織	| 個人 | 決済方法を登録した会員1人ごと|3個|
|	| 事業者 | 決済方法を登録した会員1人ごと|5個|
|プロジェクト	 | 個人 | 組織ごと |5個|
|	 | 事業者 | 組織ごと |10個|

### インフラサービスリソース提供ポリシー
リソース使用量はプロジェクトごとに計算され、リージョンごとにそれぞれのリソース使用量制限ポリシーが適用されます。

|リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
|CPU	| プロジェクトごと |100vCore| O | |
|メモリ	 | プロジェクトごと |256GB| O | |
| キーペア | プロジェクトごと | 100個 | O | |
|Block Storage| プロジェクトごと |10TB| O | |
|ボリューム当たりの最大サイズ| Volumeごと |2048GB| O | |
|Floating IP | プロジェクトごと |50個| O | |
|VPC | プロジェクトごと |3個| O | |
|サブネット | VPCごと |10個| O | |
|ルーティングテーブル | VPCごと |10個| O | |
|ルーティング | ルーティングテーブルごと |10個| O | 100個 |
|静的ルート | サブネットごと | 20個 | X | |
|リージョンピアリング | プロジェクトごと |10個 | O | | 
|プロジェクトピアリング | プロジェクトごと |10個 | O | | 
|インターネットゲイトウェイ | プロジェクトごと	|3個| O | |
|NATゲートウェイ | プロジェクトごと | 3個 | O | | 
|VPN ゲートウェイ(Site-to-Site VPN) | VPCごと | 1 | X | | 
|VPN ゲートウェイ(Site-to-Site VPN) 接続 | サブネットごと | 1 | X | |  
|サービスゲートウェイ | プロジェクトごと | 10個 | O | | 
|トラフィックミラーリングセッションの | プロジェクトごと | 10個 | O | | 
|トラフィックミラーリングフィルタグループ | プロジェクトごと | 10個 | O | | 
| Network Interface | プロジェクトごと | 500個 | O | | 
| Network ACL | プロジェクトごと | 10個 | O | | 
| Network ACLポリシー | プロジェクトごと | 100個 | O | | 
| Network ACLバインディング | プロジェクトごと | 100個 | O | | 
|Load Balancer | プロジェクトごと |10個| O | |
|IPアクセス制御グループ	| プロジェクトごと |10個| O | |
|IPアクセス制御対象 | IPアクセス制御グループごと |1000個| O | |
| NAS ボリューム | プロジェクトごと| 100個 | O | |
| NAS ボリュームサイズ | プロジェクトごと | 30TB | O | |
| NASボリューム当たりの最大サイズ | Volumeごと  | 10TB | O | |
| NAS volume Subnet | プロジェクトごと | 3個 | O | |
| トランジットハブ | プロジェクトごと | 10個 | O | |
| トランジットハブ接続 | プロジェクトごと | 20個 | O | |
| トランジットハブ許可リスト | プロジェクトごと | 10個 | O | |
| トランジットハブルーティングテーブル | プロジェクトごと | 20個 | O | |
| トランジットハブルーティング接続 | | 制限なし | | |
| トランジットハブルーティング配信	 | | 制限なし | | |
| トランジットハブルーティングルール | プロジェクトごと | 100個 | O | |
| トランジットハブマルチキャストドメイン | プロジェクトごと | 20個 | O | |
| トランジットハブマルチキャスト接続 | | 制限なし | | |
| トランジットハブマルチキャストグループ | プロジェクトごと | 100個 | O | |
| Private DNS Zone | プロジェクトごと | 100個 | O | |
| Private DNS レコードセット | プロジェクトごと | 500個 | O | |

### NHN Kubernetes Service(NKS)リソース提供ポリシー 
リソース使用量はプロジェクトごとに計算され、リージョンごとにポリシーが適用されます。

|リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
|クラスター	| プロジェクトごと |3個| O | |
|ワーカーノードグループ	 | クラスターごと |3個(基本ワーカーノードグループを含む)| O | |
|ワーカーノード数	 | ワーカーノードグループ毎 |10個| O | |

### NHN Container Registry(NCR)リソース提供ポリシー 
リソース使用量はプロジェクトごとに計算され、リージョンごとにポリシーが適用されます。

|リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
| レジストリ数 | プロジェクト毎 | 30個 | O | |
| イメージ数 | レジストリ毎 | 10000個 | O | |
| アーティファクト数 | イメージ毎 | 10000個 | O | |
| タグ数 | アーティファクト毎 | 1000個 | O | |
| 手動スキャン数 | イメージ毎1日 | 1個 | O | |


### NHN Container Service(NCS)リソース提供ポリシー 
リソース使用量はプロジェクトごとに計算され、リージョンごとにポリシーが適用されます。

|リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
| ワークロード	| プロジェクトごと |制限なし| O | |
| 作業 | ワークロードごと | 100個 | O | | 
| テンプレート | プロジェクトごと | 1,000個 | O | | 
| コンテナ | テンプレートごと | 10個 | O | |
| CPU | テンプレートごと | 16vCore | O | | 
| CPU | プロジェクトごと | 24vCore | O | | 
| メモリ | テンプレートごと |32,768 MiB | O | 230,400 MiB |
| メモリ | プロジェクトごと |	49,152 MiB | O | |
| GPU | テンプレートごと |  7Core | O | | 
| GPU | プロジェクトごと | 7Core | O | |


### DNS Plusサービスリソース提供ポリシー
リソース使用量はリージョンの区別なくプロジェクトごとに計算されます。

#### DNS
|リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
|レコードセット	| DNS Zoneごと |5,000個| O | |

#### GSLB
|リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
|GSLB	| プロジェクトごと | 20個| O | |
|Pool	| プロジェクトごと | 20個 | O | |
|Pool   | GSLBごと   | 16個 | O | |
|エンドポイント | プロジェクトごと | 20個 | O | |
|エンドポイント | Poolごと | 5個 | O | |
|ヘルスチェック	| プロジェクトごと | 5個 | O | |

### KakaoTalk Bizmessageサービスリソース提供ポリシー
| リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
| お知らせトーク送信数 |  KakaoTalk Channel 1日毎 | 1,000件 | O | |
| フレンドトーク送信数 |  KakaoTalk Channel 1日毎 | 1,000件 | O | |

### Face Recognitionサービスリソース提供ポリシー
| リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
| グループ数 |  Face Recognitionサービスごと | 5件 | O | |
| グループ 内の顔登録数 |  Face Recognitionサービスグループごと | 100,000件 | O | |

### OCRサービスリソース提供ポリシー
リソース使用量はリージョンの区別なくプロジェクトごとに計算されます。

| リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
| 身分証分析リクエスト件数 | OCRサービス毎 | 100,000件 | X | |

### API Gatewayサービスリソース提供ポリシー 
リソース使用量はプロジェクトごとに計算され、リージョンごとに区分してポリシーが適用されます。

| リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
| API Gatewayサービス | プロジェクト毎 | 10個 | O | |
| ステージ | API Gatewayサービス毎 | 10個 | O | |
| リソースメソッド | API Gatewayサービス毎 | 100個 | O | 300個 |

### Log & Crash Search サービスリソース提供ポリシー
リソース使用量はリージョンの区別なくプロジェクトごとに計算されます。

|リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
| ログ(一般ログ、クラッシュログ) 送信数 | 1日 | 20,000,000 件 | O | |
| ログ(一般ログ、クラッシュログ) 容量 | 1件 | 8MB | X | |

### DataFlow サービスリソース提供ポリシー
リソース使用量はリージョンの区別なくプロジェクトごとに計算されます。

|リソース | 提供基準 | 基本提供量 | 調整の可否 | 最大提供量 |
|----|----|----|----|----|
| 実行中のフロー数 | プロジェクト当たり | 10個 | O | |


### リソース提供量調整の申請
※　2020年4月以降、個人のお客様に対しての提供量調整はFloating IPのみ受け付けております。

基本提供量のほかに追加使用を希望する場合はNHN Cloudカスタマーサービス[1:1問い合わせ](https://nhncloud.com/kr/support/inquiry)を通じてお問い合わせください。
申請の際、追加を希望する項目と必要なリソース量を記入いただくと、相談がスムーズです。

お問い合わせ後手続きが完了するまでには2～5日程度要するため、実際必要なタイミングより前もってご相談いただくことをお勧めします。