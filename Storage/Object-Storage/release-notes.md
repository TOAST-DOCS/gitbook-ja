## Storage > Object Storage > release notes

### 2023. 11. 28.
#### 機能追加
* [API] Amazon S3互換API, AWS Signature V4 Chunked Uploadサポート
* [Console]署名されたURL作成機能を追加

### 2023. 03. 28.
#### 機能変更
* [API] APIエンドポイントの変更

#### バグ修正
* [API] PUBLICコンテナにアップロードされたマルチパートオブジェクトのセグメントオブジェクトが他のコンテナにある場合、トークンなしでダウンロードできない問題を修正しました。
* [API] Amazon S3互換APIを利用して同じ名前のマルチパートオブジェクトを更新したときに、以前のパートオブジェクトが削除されない問題を修正しました。

### 2022. 11. 29.
#### 機能追加
* [API]オブジェクトロックコンテナ設定機能を追加
* [Console]オブジェクトロックコンテナ設定機能を追加

### 2022. 10. 13.
#### 機能追加
* [Console]コンテナACL設定機能を提供

### 2022. 09. 27.
#### 機能追加
* [Console]暗号化コンテナ設定機能の追加
* [Console]オリジン間リソース共有(CORS)設定機能の追加

#### 機能改善
* [Console]コンテナ情報照会、設定UIの改善

### 2022. 08. 23.
#### 機能追加
* [API] RFCを遵守するETag形式の使用設定の追加

### 2022. 03. 29.
#### 機能追加
* [Console]リージョン間のコンテナ複製機能を追加

### 2022. 01. 25.
#### 機能追加
* [Console] S3 API認証情報発行機能の追加

#### 機能改善
* [Console]マルチパートオブジェクトを削除するとセグメントオブジェクト一括削除
* [API]コンテナ名に入力可能な文字制限
  * 一部特殊文字(' " < > ;)とスペース、相対パス文字(. ..)制限 

### 2021. 10. 26.

#### 機能改善
* [Console]静的Webサイト設定時の入力可能文字制限ルールを変更
    * 最大256バイト、英数字、一部特殊文字(- _ . /)のみ入力可能
* [Console]オブジェクトをコピーする時の入力制限ルールを変更
    * サブフォルダを含むパスを入力可能
    * {パスの最大長さ} = 1024 - {オブジェクト名の長さ} - 1

### 2021. 02. 23.
* [Console]コンテナ設定機能改善
    * コンテナ単位でアクセスポリシー、オブジェクトのライフサイクル、バージョン管理ポリシー、静的Webサイトなどを設定できるように機能改善

### 2020. 11. 24.

#### 機能改善
* [Console]前方一致検索
    * 入力した文字列で始まるコンテナ、フォルダ、オブジェクトを検索できるように検索機能を改善

### 2020. 02. 25.
#### 機能追加
* [API] Amazon S3互換APIを追加

### 2018. 04. 24.

#### 機能修正
* [Console]フォルダ名の特殊文字制限
    * コンテナおよびフォルダ名に使用できない特殊文字リストへスラッシュ(/)を追加

### 2017. 10. 26.

#### 機能修正
* フォルダ名の特殊文字制限
    * コンテナおよびフォルダ名に一部の特殊文字(., .., &, <, >, ", ', ;)と空白を使用不可に修正

### 2017. 03. 23.

#### 機能改善

* [Console]アップロード可能なファイルサイズを明示します。
    * 最大5GBまでアップロードできます。

### 2016. 12. 22.

#### バグ修正
* [Console]フォルダ名が「/」で始まるフォルダを作成した時、フォルダが表示されない問題を修正
* [Console]フォルダ名とファイル名が同じ時、ファイルの削除ができない問題を修正
* [Console]タイトルに「#」が含まれるファイルをダウンロードできない問題を修正
* [Console] API Endpoint設定ポップアップのコピーボタンが動作しない問題を修正
* [Console] 0Byteのファイルがダウンロードできない現象を修正

### 2016. 12. 08.

#### バグ修正
* [Console]リソースが残っている状態でサービスの利用を終了する時の案内文言を修正