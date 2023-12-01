## Security > Security Advisor > 概要

Security Advisorは、顧客が作成したNHN Cloud組織およびプロジェクトリソースのセキュリティ設定状態を点検し、推奨ガイドを提示するサービスです。<br>安全なクラウド環境のために推奨ガイドを活用できます。<br>Security Advisorは、プロジェクト単位で有効化され、特定リージョンでサービスを有効にすると、他のすべてのリージョンでもサービスが有効になります。<br>ただし、リージョンごとに提供されるクラウドサービスが異なるため、点検対象および範囲には差があります。

## 主な機能
* NHN Cloud組織のガバナンス設定を点検し、推奨措置方法を適用してクラウド環境の安全性を高めることができます。
* NHN Cloudプロジェクトに属する長期未使用アカウントを点検し、推奨措置方法を案内します。
* Security Groupsを点検してインスタンスに適用されたセキュリティルールを確認できます。
* RDSへのアクセス設定を点検して不要なアクセスを遮断できます。
* 定期的な自動点検機能を提供し、結果をメールで送信できます。

## 対象リソース、サポートリージョン
### 選択点検リージョン別サポート範囲
|区分|サポートリージョン|
|---|---|
|組織で区分された 点検項目|韓国(パンギョ)リージョン, 韓国(ピョンチョン)リージョン、日本(東京)リージョン、米国(カリフォルニア)リージョン|
|プロジェクトで区分された 点検項目|韓国(パンギョ)リージョン、 韓国(ピョンチョン)リージョン、日本(東京)リージョン|

### 選択点検項目のプロジェクト項目点検対象リソース
|区分&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|点検項目|対象リソース|備考|
|---|---|---|---|
|プロジェクト &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |Security Groups点検|Instance, Security Groups|Database Instance、NKSクラスタ除外|
|プロジェクト &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|Database Security Groups点検|Database Instance(MS-SQL Instance, MySQL Instance, PostgreSQL Instance, CUBIRD Instance, MariaDB Instance, Tibero Instance, Redis Instance), Security Groups|
|プロジェクト &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |RDSアクセス制御点検 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|RDS for MySQL, RDS for MariaDB, RDS for MS-SQL|RDS for MariaDB, RDS for MS-SQLはパンギョリージョンでのみサービスされているため パンギョリージョンでのみ点検可能|

## プロジェクトメンバーのサービス利用ロール

Security Advisorはプロジェクトサービスです。
プロジェクト管理者は、プロジェクトに登録されたNHN Cloud会員またはIAMメンバーにロールを付与できます。

|サービス|ロール|説明&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|---|---|---|
|Security Advisor|ADMIN|Security Advisorのすべてのサービスを管理できます。<br> - Security AdvisorサービスCreate(作成)、Read(読み取り)、Update(更新)、Delete(削除)<br><br>Security Advisorサービスが提供するすべての機能を使用できます。<br>- ダッシュボード表示、Excel保存<br>- 点検項目の選択点検、点検項目の基本情報表示、検出リソースの表示、検出リソースの選択例外、例外リソースの表示、例外リソースの例外解除<br>- 結果受信設定、自動点検設定|
||PERMISSION|Security Advisorサービスを有効化または、無効化できます。<br>- サービスEnable(有効化)、Disable(無効化)|
||VIEWER|Security Advisorサービス点検結果を確認できます。<br>- ダッシュボードの表示、Excelダウンロード<br>- 点検項目の基本情報表示、検出リソースの表示、例外リソースの表示<br>*VIEWERロールには「設定」画面を提供しません。|

## サービスの使用手順
### サービスの有効化手順
サービスの有効化権限を持つアカウントでNHN Cloudにログインします。SecurityカテゴリーでSecurity Advisorをクリックしてサービスを有効にします。
![画像1](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_01.png)

### サービスの無効化手順
サービスの有効化権限を持つアカウントでNHN Cloudにログインします。プロジェクト名の横の歯車アイコンをクリックして**プロジェクト管理**メニューに入ります。
**利用中のサービス**でSecurity Advisor項目の**無効化**をクリックしてサービスを終了します。
![画像2](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_02.png)
