## Container > NHN Container Service(NCS)  > リリースノート
### 2023. 11. 28.
#### 機能追加
* コンテナ設定機能が追加されました。
    * DNSサーバーアドレス設定
    * 状態点検(LivenessProbe, StartupProbe)設定
    * ライフサイクルフック(Lifecycle Hook)設定
    * ファイル(ConfigMap)設定
    * 秘密データ(Secret)設定
    * NASコンテナ接続パス設定
* GPUと臨時ストレージモニタリング機能が追加されました。
* ワークロード作成時にセキュリティグループを選択できます。
* NCS で発生したイベントを NHN CloudTrail で確認できます。

#### 機能改善
* Load Balancerが提供されます。
    * Load Balancer Instanceはサポートしません。
* コンテナポートにHTTPS, TERMINATED_HTTPSプロトコルが追加されました。
* ログタブが改善されました。
* コンテナの現在と最後の状態についての詳細な理由をイベントタブで確認できるように改善されました。

### 2023. 08. 29.
#### 機能追加
* ワークロード予約機能を追加しました。
* ワークロード停止/再起動機能を追加しました。

#### 機能改善
* NASストレージ接続失敗原因をイベントタブで確認できるように改善しました。

### 2023. 07. 25.
#### 機能改善
* コンテナの最大リソースサイズが増加しました。

### 2023. 05. 30.
#### 機能改善
* GPUタイプを選択できる機能が追加されました。
* コンテナポートにHTTPプロトコルが追加されました。
* Quota機能が追加されました。

### 2023. 03. 28.

#### 機能改善
* 内部構造を改善してサービスの安定性が向上しました。

### 2023. 02. 28.

#### 機能追加
* 権限細分化機能を追加しました。
* ワークロード変更機能を追加しました。

### 2023. 01. 31.

#### 機能追加
* モニタリング機能を追加しました。

### 2022. 12. 27.

#### 新規サービスリリース
* コンソールからコンテナを作成し、管理できます。