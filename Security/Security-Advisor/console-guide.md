## Security > Security Advisor > コンソール使用ガイド

Security Advisorの機能と使用方法を説明します。

## ダッシュボード

Security Advisor点検項目で点検した結果を確認できます。
組織を点検した結果はリージョン選択に関係なく全て表示され、プロジェクトリソースは選択されたリージョンに作成されたリソースを点検した結果を表示します。

* **点検結果要約**は通知基準ごとに点検された項目の数を表示します。
  - ダッシュボードに説明がある**通知基準**は、危険度判断の基本水準です。
 個別点検項目の通知基準は項目ごとに異なって適用されています。
  - 選択点検結果の検出リソースのうち、点検例外に設定されたリソースの合計を例外に表示します。
  - 自動点検設定は設定メニューで設定した点検周期が表示されます。
* **点検結果リスト要約**は**危険、注意、関心**の基準で検出されたリソースが存在する項目を表示します。
  - 点検結果が**良好**である項目は表示しません。
  - 詳細表示列の**照会**をクリックすると、点検項目ページに移動して詳細情報を確認できます。
* **Excel保存**をクリックすると、点検結果をExcelファイルでダウンロードできます。
  - Excelファイルには、点検項目で最後に選択点検した結果(点検項目の基本情報と検出リソース、点検時間)が保存されています。
  - Excelファイルには例外リソースと設定情報は含まれません。
  - サービスを有効にした後、一度も選択点検を実施せず、点検結果が存在しない場合、Excelファイルのダウンロードはできますが、ファイルは開けません。
![画像3](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_03.png)


## 点検項目

提供される項目のうち、希望する項目をチェックして点検を実行し、その結果と措置ガイドを確認できます。
点検結果の詳細を確認し、点検が不要な項目を例外処理できます。
### 選択点検
1. 点検するリージョンを選択します。
  (組織で区分された項目はすべてのリージョンに同じように設定されているため、リージョンを変更しても結果は同じです。)
2. 点検する項目をチェック後、**選択点検**をクリックします。
3. 点検が完了したら、点検項目ごとに結果を確認します。
4. プロジェクトで区分された項目はリージョンを変更して選択点検します。
![画像4](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_04.png)

### 基本情報

* 点検項目の説明を確認できます。
* 検出リソース数、例外リソース数、最終点検日を確認できます。
* 通知基準を確認し、推奨措置を参考にして検出されたリソースを措置できます。
![画像5](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_05.png)

### 検出リソース

* 点検項目別のアラーム基準に基づいて検出されたリソースの詳細情報を確認できます。
* 検出されたリソースのうち、希望する項目をチェックして**選択例外**をクリックすると、次の点検時にそのリソースは例外処理されます。
![画像6](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_06.png)
![画像7](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_07.png)

### 例外リスト

* 点検例外処理された項目を確認できます。
* **変更**をクリックしてメモを作成できます。
* 希望する項目をチェックして**例外解除**をクリックすると、点検対象に含めることができます。
![画像10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_11.png)

## 設定

自動点検を設定して希望する時間に定期的に点検を行うように設定できます。
メールアドレスを入力すると、自動点検結果をメール受信者に配信します。自動点検を設定しても、メールアドレスを設定していない場合、点検結果はコンソールにのみ反映されます。
設定を変更した後、変更した値を適用するには必ず**保存**をクリックしてください。

### 管理者設定

* 点検結果を受信する管理者のメールアドレスを設定します。点検結果が配信されますので、メールアドレスを正確に入力してください。
* メールは必須入力値ではありません。
![画像8](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_08.png)
### 点検設定
* 希望する**点検周期**を設定して自動的に点検するように設定できます。点検された結果は自動的にコンソールに反映され、メールアドレスを設定した場合、メール受信者に結果が送信されます。
* **自動点検項目**を選択できます。
![画像9](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_securityadvisor/overview_jp_09.png)
