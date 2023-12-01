## CloudTrail > コンソール使用ガイド

### 始める
CloudTrailは、組織を有効にするとデフォルトで提供されるサービスです。したがって、組織を作成している場合は別途行う作業はありません。
組織を作成した後、サービス選択でCloudTrailサービスを選択すると使用できます。

![cloudtrail_01](https://static.toastoven.net/prod_cloudtrail/IMG01_JA.png)

### リスト

CloudTrailサービスを選択すると、次のような画面が現れます。

![cloudtrail_02](https://static.toastoven.net/prod_cloudtrail/IMG02_JA.png)

該当組織内でユーザーイベントが記録され、これを確認できます。

### 検索およびソート機能

![cloudtrail_03](https://static.toastoven.net/prod_cloudtrail/IMG03_JA.png)

1. プロジェクトを検索します。名前単位でのみ検索できます。
2. ソース(イベントが発生した場所)単位で検索します。
    - ADMIN_CONSOLE：管理者コンソールで発生したイベント
    - API：システム内部的に発生したイベント 
        - [参考]パッチ作業や予約された作業、アラームなどのイベントが記録されます。
    - USER_CONSOLE：組織内部会員ユーザーコンソールで発生したイベント
3. サービス単位で検索します。 
    - サービスは複数の項目を検索できます。
    - [参考]サービスはNHN Cloudサービス単位です。
4. イベント単位で検索します。
    - イベントは複数の項目を検索できます。
5. ユーザーを検索します。
6. リクエスト、レスポンス値を検索します。
7. 検索範囲を指定します。24時間、1週間、2ヶ月、3ヶ月単位フィルタが提供され、直接指定できます。
    - [参考]イベントは最大3ヶ月間保存されます。
8. リスト表示単位を指定します。1画面に複数のリストを表示するか、20、50、100個単位に設定できます。

---

* ソート機能は時間項目でのみ使用できます。

### 詳細表示機能

![cloudtrail_04](https://static.toastoven.net/prod_cloudtrail/IMG04_JA.png)

行を選択すると該当の行が拡張され、詳細イベントが表示されます。

リクエストとレスポンス結果を表示し、どんなリクエストを送ったかを確認できます。


### ログ保存/ダウンロード設定
該当組織内で記録されたユーザーイベントログを外部Object Storageへ保存/ダウンロードできます。
**ログ保存/ダウンロード設定** ボタンを押した後、ダイアログボックスで使用するかどうかを選択します。

![cloudtrail_07](https://static.toastoven.net/prod_cloudtrail/IMG07_JA.png)

* 以下では[NHN Cloud Object Storage](/Storage/Object%20Storage/ko/Overview/)を利用したログ保存/ダウンロード方法を説明します。
    * **アクセスキー**、**シークレットキー**は[AWS S3 API](/Storage/Object%20Storage/ko/s3-api-guide/#_1)を利用した**EC2資格証明登録および照会**で確認できます。
    * **バケット名**はログが保存されるObject Storageコンテナの名前です。
    * **エンドポイント**、**リージョン**はログを保存するObject Storageを管理する情報で、[Amazon S3互換APIガイド - AWS SDK](/Storage/Object%20Storage/ko/s3-api-guide#aws-sdk)で確認できます。
    * 設定が完了すると、設定したObject Storageにログが保存されます。
    * 保存されたログは2時間～2時間半後、Object Storageにアップロードされてから確認可能です。
    * 3回以上アップロードに失敗すると、保存された認証情報が無効になります。**結果受信(メール)**に登録されたメールへ内容が配信されます
    * **外部ログ改ざん通知**は、Object Storage内のログが勝手に修正または削除されたとき、これをメールで通知する機能です。 
    * 外部ログ改ざん時、**結果受信(メール)**に登録されたメールに内容が通知されます。
    * **外部ログ改ざん通知**は、NHN CloudのObject Storageでのみ提供される機能です。
        * **テナントID**、**パスワード**はログが保存されるObject Storageの**APIエンドポイント設定**で確認できます。
        * **ユーザーID**の場合、該当Object Storageに権限があるNHN Cloudユーザーのメールを入力します。
