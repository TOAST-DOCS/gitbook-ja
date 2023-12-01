## Notification > Push > Release Notes

### 2023. 03. 14.
#### [API]
##### 機能追加
* トークンリスト照会APIの追加
    * トークンリストを照会できるAPI(v2.4)が追加されました。 

### 2022. 12. 13.
#### [API]
##### 機能追加
* 一般ログ照会時、ページング機能追加
  * FieldにpageNumberが追加されました。
##### 機能改善
* 失敗したメッセージリスト照会時のlimit最大値を1000から100に変更

### 2022. 05. 10.
#### [API]
##### バグ修正
* v2.2 API呼び出し時に`X-SECRET-KEY`ヘッダがない場合にエラーが発生していた問題を修正
    * `X-User-Access-Key-ID`、`X-Secret-Access-Key`ヘッダでAPI認証が行えるようにエラーを修正しました。

### 2022. 03. 29.
#### [Console]
##### 機能追加
* トークンファイルをダウンロードする時、100万件を超える場合、ファイル分割後に圧縮されたファイルで提供する機能を追加
  * **トークン**タブで**トークンファイルダウンロード**機能を利用して保存されたトークンをファイルでダウンロードするとき、トークンの数が100万件を超える場合、ファイル分割後に圧縮されたファイルで提供する機能が追加されました。

### 2022. 02. 15.
#### [Console]
##### 機能追加
* トークンファイルダウンロード機能の追加
    * **トークン**タブで**トークンファイルダウンロード**機能を利用して保存されたトークンをファイルでダウンロードできる機能が追加されました。
##### エラー修正
* 送信履歴の保存時にUIDが「UNKNOWN」で保存されるエラーを修正
    * **設定**タブで**送信履歴保存**機能を使用した時、有効期限が切れたトークン履歴でUIDが「UNKOWN」で保存されるエラーを修正しました。
* 認証失敗案内メール重複送信エラーを修正
    * プッシュメッセージ送信時、認証に失敗した場合、案内メールが重複して送信されるエラーを修正しました

### 2022. 01. 11.
#### [API]
##### 機能追加
* ADM(Amazon Device Messaging)プッシュタイプに受信/確認機能を追加
    * ADM送信時にも受信/確認を行うことができるように機能が追加されました。
##### エラー修正
* FCMでiOSメッセージの送信に失敗した時の成功処理エラーを修正
    * Firebaseに無効なAPNS証明書を設定した後、メッセージ送信時に成功として処理されるエラーを修正しました。

### 2021. 10. 26.
#### [Console]
##### 機能追加
* トークン日時修正ポップアップ追加
    * 登録したトークンの日時を修正することができるポップアップが追加されました。
    * 広告受信同意事実案内メッセージ予約機能などをテストするためにトークンの同意日時を変更する時に使用できます。

#### [API]
##### 機能追加
* 統計照会API送信失敗イベントのextra2フィールドに失敗原因が追加されました。
* v2.4予約メッセージ照会APIに照会条件追加
    * 予約送信日時を基準に照会するための`deliveryFrom`、`deliveryTo`条件が追加されました。
    * `deliveryFrom`と`deliveryTo`の間に属すスケジュールがある予約メッセージが検索されます。
##### エラー修正
* v2.4予約メッセージ照会APIで照会条件処理エラーを修正
    * v2.4予約メッセージ照会APIでfrom、to照会条件が処理されないエラーが修正されました。

### 2021. 07. 27.
### [Console]
#### 機能追加
* 広告受信同意事実案内メッセージ予約機能
    * 広告メッセージの受信に同意してから満2年が経ったトークンに案内メッセージを送信する機能が追加されました。 
    * 毎月設定した日時に案内メッセージが対象トークンに送信されます。
    * 毎月設定した日時に案内メッセージが対象トークンに送信されます。
    * 広告性メッセージ受信同意日時識別子(###AD_AGREEMENT_DATE_TIME###)を本文に挿入すると、メッセージ送信時に該当トークンの同意日時に置換されます。
    * **設定**タブの**広告受信同意事実案内メッセージ予約**で設定できます。

### 2020. 12. 29.
### [API]
* v2.4統計合計API追加
    * 照会した統計データを合算することができる合計APIが追加されました。
        <a href="https://docs.toast.com/ja/Notification/Push/ja/api-guide/#stats-total-api" target="_blank">こちら</a>

### 2020. 06. 09
### [Console]
#### 機能追加
* APNS JWT認証追加
    * APNSプッシュメッセージ送信時の認証方法にJWTを追加しました。コンソール**証明書**タブでJWT認証に必要なキーID、チームID、トピック、暗号化キーを登録できます。
    * APNS JWT認証情報を登録すると、登録された証明書は削除されます。
    * <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns" target="_blank">Apple開発者ガイド</a>

### [Doc]
#### ガイド追加
* **APNS JWT認証情報取得**についてのガイドを追加
    * <a href="https://docs.toast.com/ko/Notification/Push/ko/console-guide/#get-apns-jwt" target="_blank">リンク</a>

### 2020. 03. 24
### [Console]
#### 機能追加
* 統計を改編しました。
    * **統計イベントキー管理** タブを追加しました。コンソールで新しい統計イベントキーを追加し、メッセージ送信時に設定できます。メッセージが送信されると設定した統計イベントキーを基準に統計データが蓄積され、新しい統計タブで検索できます。
        * <a href="https://docs.toast.com/ja/Notification/Push/ja/console-guide/#stats-event-key" target="_blank">リンク</a>

### [API]
* v2.4 API追加
    * 統計イベントキーで照会できる統計APIを追加しました。v2.3の統計関連APIは今後は提供しません。
        * <a href="https://docs.toast.com/ja/Notification/Push/ja/api-guide/#stats-api" target="_blank">リンク</a>
* トークンマルチテナント機能追加
   * トークンを複数のUIDが所有できるようにするマルチテナント機能を追加しました。トークン登録時、トークンの末尾に｢#tenant=テナント_情報｣をつけることができます。複数のUIDが同じトークンを使用してもテナント情報が異なればトークンが維持されます。
   

### 2019. 12. 24.
#### [Console]
##### 機能追加
* メッセージ送信ページにHTMLスタイル、メッセージクリックアクション、配置入力項目を追加
    * **HTMLスタイル**を使用すると、Android端末でタイトルと内容にHTMLを使用できます。iOS端末はサポートせず、HTMLが表示されません。**HTMLスタイル**を使用しない場合は、HTLMコードがそのままAndroid、iOSに表示されます。
    * **メッセージクリックアクション**を利用して、アプリで定義したスキーム(Scheme)やURLに移動できます。

### 2019.10.29
#### [API]
##### 機能追加

* Androidバッジ(badge)プロパティを追加
    * 今まではiOSにのみバッジプロパティを伝達していましたが、Androidにもバッジプロパティを伝達します。
    TOAST SDKを適用した場合、アプリアイコンに伝達されたバッジが自動的に表示されます。
* iOSでHTMLを除去したメッセージを表示する機能を追加
    * 現在iOSは、Androidと異なり、プッシュメッセージ内のHTMLを描写しません。
    'content.default.style.useHtmlStyle'を「true」に設定すると、iOSにHTMLを除去したメッセージを送信します。
* リッチメッセージで、Android、iOSにメディアを別々に指定できるように機能を改善
    * 'richMessage.media'の他に、'richMessage.androidMedia'、'richMessage.iosMedia'を追加しました。
    AndroidとiOSにメディアを別々に設定できるように、リッチメッセージ機能を改善しました。
* リッチメッセージのmediaの'sourceType'と'extension'を必須から任意に変更
    * 'richMessage.media.sourceType'、'richMessage.media.extension'を必須(Required)から任意(Optional)に変更しました。
  メディアが外部、内部に関わらず、メディアの拡張子を設定しなくても、リッチメッセージの送信が可能です。
* プッシュメッセージをクリックした時のアクションを定義する機能を追加
    * 'content.default.clickAction'に、プッシュメッセージをクリックした時に実行されるアクション(URL、Scheme)を定義できます。
    TOAST SDKを適用した場合、自動的にアクションが実行されます。

### 2019.09.24
#### [API]
##### バグ修正
* iOSリッチメッセージ送信エラーを修正
    * メッセージ受信/確認機能を使用しない状態でリッチメッセージを送信すると、iOSでイメージが表示されないエラーを修正しました。

#### [Console]
##### 機能追加
* トークンタブで、トークンリスト照会機能を追加
    * トークンタブで、検索条件がなくてもトークンを照会できるように改善しました。
* FCMを通してiOSにメッセージを送信する機能を追加
    * FCM SDKを使用するiOSアプリにメッセージを送信できます。
        *  <a href="https://firebase.google.com/docs/cloud-messaging/http-server-ref" target="_blank">FCMガイド</a>
    * メッセージ送信時、'notification'、'content_available'、'mutual_content'プロパティを使用すると、FCMを通してiOSアプリにメッセージが送信されます。


### 2019.05.28
#### [API]
* メッセージ受信/確認データ収集性能の改善
    * メッセージ受信/確認データを収集するサーバーの性能を改善しました。

### 2019.03.26
#### [API]
##### バグ修正
* 無効なトークン照会APIで、期間(from, to)設定が適用されないバグを修正
    * 無効なトークン照会APIで、期間を設定した時、from, toのどちらも設定していない場合に、設定が無視されるバグがありました。
    * from, toの片方のみ設定しても期間設定が適用されるように修正しました。

#### [Console]
##### 機能追加
* 重複メッセージ防止機能の追加
    * 内容が完全に同じメッセージを複数回送信リクエストしても、設定した時間中は送信されません。
    * 送信されなかったメッセージは失敗処理されます。送信失敗原因は'DUPLICATED_MESSAGE_TOKEN'になります。
    * 重複判断基準はメッセージタイプ、内容(コンテンツ)、発信連絡先、受信同意設定ガイド、広告表示文言位置、トークンです。
    * [設定]タブの[重複メッセージ防止設定]で設定できます。

### 2019.02.26
#### [API]
##### 機能追加
* v2.3 API追加
    * トークン削除APIを追加しました。Secret Keyなしで呼び出せます。
    * 新しいプッシュタイプ'FCM'を追加しました。API呼び出し時、'GCM'の代わりに'FCM'を使用する必要があります。

#### [Console]
##### バグ修正
* ツールチップエラー、誤字、リンクエラーを修正
    * [証明書]タブの一部のツールチップが正しく表示されないバグと誤字を修正しました。
    * [設定]タブの誤字を修正しました。
    * 無効なSDKガイドリンクを修正しました。

##### 機能追加
* ユーザーコンソールを追加しました。

### 2018.12.18
#### [API]
##### バグ修正
* 無効なVoIPトークンが正常に削除されないバグを修正
    * メッセージ送信時、無効なAPNS_VOIP、APNS_SANDBOXVOIPトークンが削除されないバグを修正しました。

### 2018.10.30
#### [Console]
##### 機能追加
* メッセージ送信ページにリッチメッセージ機能を追加
    * メッセージ送信ページでリッチメッセージを送信できます。
        * <a href="https://docs.toast.com/ko/Notification/Push/ko/console-guide/#_3" target="_blank">コンソールガイド</a>
    * プレビュー機能を提供し、Android、iOSでリッチメッセージがどのように表示されるかを確認できます。
* 広告表示文言位置設定機能を追加
    * 広告メッセージであることを表す文言を、タイトルまたは内容部分に表示するかどうかを設定できる機能を追加しました。
    * [設定]タブの[広告表示文言位置設定]で設定できます。

##### バグ修正
* トークン検索時、時間がUTCで表示されるバグを修正
    * トークン検索時、時間がUTCで表示されるバグがありました。ブラウザの現地時間で表示されるように修正しました。

#### [API]
##### 機能追加
* メッセージ送信APIにリッチメッセージ機能を追加
    * プッシュメッセージにボタン、メディア(画像、動画、音声)を表示できる機能を追加しました。
         * <a href="https://docs.toast.com/ko/Notification/Push/ko/api-guide/#7" target="_blank">APIガイド</a>
    * v2.0メッセージ送信API以降と、最新SDKが適用されたアプリで使用できます。

#### [SDK]
##### Android
* リッチメッセージ機能の追加
    * ボタン、画像、大アイコン、グループなどのリッチメッセージを送信できます。
* リッチメッセージの返信機能のためのAPIを追加
    * 返信ボタンの処理のためのリスナークラス登録APIを追加しました。
* Android 9対応
    * 対象(target)バージョンが28(Android 9)以上の場合、Android 9端末で受信/開封指標が収集されないバグを修正

##### iOS
* リッチメッセージ機能の追加
    * ボタン、画像、動画などのリッチメッセージを送信できます。
* カテゴリー設定機能の追加
    * 初期化でカテゴリーを設定し、メッセージ内に本人のカテゴリー識別子に設定すると、該当カテゴリーのアクションを受信できます。
* 指標収集方法の追加
    * アプリケーションのinfo.plistファイルに指標収集情報(AppKey)を入力して、初期化しなくても確認指標の収集が可能です。
ｄｄっｓ
* トークン登録機能の改善
    * 初期化せずにトークン登録リクエストシステムトークンのみ登録され、発行されたトークンをサービスサーバーでAPIを通して自由に登録できます。

##### バグ修正
* リスト照会APIで分まで照会すると、1～59秒までのデータが漏れるバグ
    * 例えば、10時11分までデータを照会すると、11分59秒のデータは漏れるバグがありました。
  この場合は、59秒まで含まれるように改善しました。

### 2018.08.28
#### [API]
##### 機能追加
* Logging API追加
    * Consoleで有効にできるLogging機能で保存されたデータを照会するAPIを追加しました。
    * 一般照会、大量照会という2つのタイプのAPIを提供します。
         * <a href="https://docs.toast.com/ko/Notification/Push/ko/api-guide/#_18" target="_blank">ログ照会</a>
* v2.2 APIアップデート
    * Logging APIの追加により最新APIバージョンをv2.2にアップデートしました。
    * v2.2からAPI認証のために'APIセキュリティ設定'を利用します。
         * <a href="https://toast.com/account/api_settings" target="_blank">APIセキュリティ設定</a>
    * サポートするAPIバージョン：v1.3、v2.0、v2.1、v2.2

##### バグ修正
* トークン設定でアプリタイプを'単一トークン'にした時、APNS_VOIPトークンが削除されるバグ
    * APNS_VOIPトークンはVoIPのためのトークンで、プッシュメッセージのためのGCM、APNSなどとは別個で管理される必要がありますが、
  単一トークンに設定すると、APNS_VOIPも他のトークンと同じように管理されて、APNS_VOIPトークンが削除されるバグがありました。
    * APNS_VOIPトークンとGCM、APNS、TENCENTトークンが別個で管理されるように修正しました。
* 一部プロジェクトで統計API Timeoutが発生するバグを改善
    * 一部プロジェクトで統計照会時にTimeoutが発生するバグがありましたが、最適化によりTimeoutが発生しなくなりました。

### 2018.07.24
#### [API]
##### 機能改善
* レスポンスメッセージ改善
    * Response Bodyのheader.resultMessageに失敗原因の詳細を追加しました。

#### [SDK]
##### Android
* Amazon Device Messagingサポート

##### iOS
* VoIPタイプサポート
* VoIPタイプ追加に伴う一部APIの変更

<br>

### 2018.06.26
#### [Console]
##### 機能追加
* ADM(Amazon Device Messaging)プッシュタイプの追加
    * Amazonデバイス(Kindle Fire)へプッシュメッセージを送信できるように、ADMプッシュタイプを追加しました。
    * Amazon開発者サイトでアプリを登録し、Client ID、Client Secretを発行して登録後に送信できます。
     <a href="https://docs.toast.com/ko/Notification/Push/ko/console-guide/#adm-client-id-client-secret" target="_blank">ADMガイド</a>

#### [API]
##### 機能追加
* ADM(Amazon Device Messaging)プッシュタイプの追加

##### バグ修正
* 広告性プッシュメッセージの送信時、一部の対象が漏れるバグを修正
    * 2018年05月30日hotfixで修正しました。
    * 広告性プッシュメッセージの送信時、送信ロジックエラーで一部の対象が漏れるバグを修正しました。
* 予約メッセージの送信時、現地時間機能を使用した場合、重複受信されるバグを修正
    * 現地時間機能を使用した場合、存在しない時間帯に予約メッセージを送信するバグを修正しました。

#### [SDK]
##### Android
* 最新Tencent SDK適用(3.2.3)
* API改善

##### iOS
* 指標収集および送信機能の改善
* メッセージ確認指標の収集および送信の自動化

<br>

### 2018.05.29
#### [Console]
##### 機能改善
* メッセージID追加
    * メッセージ選択時、ポップアップのDetails部分にメッセージIDを追加しました。

#### [API]
##### 機能追加
* v2.1トークン照会APIの追加
    * トークン登録時、一緒に収集するデバイスIDを確認できます。
    * 該当トークンの最終登録リクエスト日時を確認できます。

##### 機能改善
* 広告性メッセージ、広告表示文言の位置を変更
    * MessageTypeがADの広告性メッセージを送信する場合、韓国情報通信網法規定(第50条から第50条の8)に従い
 メッセージタイトルと内容に広告表示文言が追加されています。
    * 広告表示文言の位置が下記のように変更されます。

```
既存の表示位置、'(広告)'と連絡先がbodyに表示される
- title：タイトル
- body：'(広告)' '連絡先'\n内容\n'受信同意撤回方法'

新しい表示位置、'(広告)'と連絡先がtitleに表示される
- title：'(広告)'タイトル'連絡先'
- body：内容\n'受信同意撤回方法'
```

##### バグ修正
* 受信/確認統計API照会期間が無視されるバグを修正
    * メッセージIDと照会期間を同時に入力した場合、照会期間が無視されるバグを修正しました。

#### [SDK]
##### Android
* SDKユーザビリティの改善

<br>

### 2018.05.02
#### [SDK]
##### Android
* トークン登録のバグを修正
* 最小サポートバージョンの変更(API 9 → API 15)

##### iOS
* トークン登録バグの修正
* 最小サポートバージョンの変更(iOS 7.0 → iOS 8.0)
* SDKライブラリ形式の変更(static library → framework)

<br>

### 2018.04.24
#### [Console]
##### 機能追加
* トークン管理設定機能の追加
    * トークン終了期間設定
        * 設定した期間に登録リクエストがないトークンをメッセージ送信対象から除外します。
        * 設定した期間にアプリを使用していないユーザーのトークンがメッセージ送信対象から除外できるため、料金を節約できます。
    * アプリタイプ設定
        * 連携したアプリのタイプに応じてトークンを管理します。
        * アプリのユーザーが複数の端末にインストールされたアプリを同時に使用できる場合は、Multipleに設定する必要があります。(基本)
      Multipleに設定すると、ユーザーは複数のトークンを持つことになります。
    例えば、ユーザーが携帯電話とタブレットを使用している場合、2つの端末でプッシュメッセージを受信します。
        * ユーザーが一度に1つの端末でのみアプリを使用できる場合は、Singleに設定する必要があります。
      Singleに設定すると、ユーザーは1つのトークンのみ持つことになります。
    例えば、ユーザーが携帯電話とタブレットを使用している場合、どちらかの端末でのみプッシュメッセージを受信します。

##### 機能改善
* エラーメッセージの日本語化
    * プッシュConsole内エラー発生時、表示されるメッセージを日本語化しました。

#### [API]
##### 機能追加
* v2.0トークン登録API、deviceIdフィールドの追加
    * ユーザーの端末を区別できるように、deviceIdフィールドを追加しました。
    * トークン登録時、同じdeviceIdのトークンがある場合、既存のトークンを削除して新たに登録します。
    * iOSはIDFV(identifierForVendor)、AndroidはAndroid IDの設定を推奨します。
    * Device IDを収集する機能が追加されたSDKは、5月2日に配布予定です。

#### [ETC]
##### バグ修正
* [Mail]証明書終了案内メール内HTMLエラー
    * 証明書終了案内メール内のHTMLが間違っていたため、下段領域の背景色が表示されないバグを修正しました。

<br>

### 2018.03.22
#### [Console]
##### 機能改善
* サービスページ内にあったタブメニューをコンソールに移動
    * コンソールにタブメニューを移し、左のサブメニューや右上からページを移動できます。
* Uid照会時、トークンを最終登録順にソート
    * コンソールで、TokenタブでUid照会時、表示されるトークンの順序を最終登録順に変更しました。

#### [API]
##### 機能追加
* Uid API追加
    * UidにTagを追加/照会/修正/削除できるAPIを追加しました。
    * このAPIはSecret Keyが不要です。アプリから呼び出せるAPIです。
(呼び出し時、Secret Keyが必要なAPIをアプリから呼び出す場合、Secret Keyが外部に公開される場合があるため、推奨しません)

##### バグ修正
* タグ名にスペースを入力できるバグを修正
    * タグ作成APIでtagNameフィールドにスペースを入力できるバグを修正しました。

<br>

### 2018.02.22
#### [Console]
##### 機能追加
* iOS VoIP送信機能の追加
    * iOSにVoIPプッシュメッセージを送信する機能を追加しました。
    * SDKでは現在サポートしておらず、今後サポート予定です。
    * VoIP送信を行うためには、次のようなプロセスが必要です。
        1. VoIP証明書登録(VoIP専用証明書またはUniversal証明書登録可能)
        2. VoIPトークン登録およびプッシュメッセージ受信処理(トークンのプッシュタイプをAPNS_VOIPまたはAPNS_SANDBOXVOIPに設定)
        <a href="https://developer.apple.com/library/content/documentation/Performance/Conceptual/EnergyGuide-iOS/OptimizeVoIP.html" target="_blank">Apple iOS Pushkitガイド</a>
        3. メッセージ送信時、プッシュタイプ'APNS_VOIP'または'APNS_SANDBOXVOIP'を選択

##### 機能改善
* メッセージ送信ページ'RemoveGuide'の説明改善
    * 広告性メッセージ送信時、広告性プッシュ受信同意撤回方法入力欄に記入例を追加しました。
    '例、メニュー > 設定 > 通知設定'

#### [API]
##### 機能追加
* iOS VoIP送信機能の追加
* メッセージ照会API照会条件にdeliveryTypeを追加
    * deliveryTypeに設定できる値は次のとおりです。
     'INSTANT', 'RESERVATION'

##### 機能改善
* 送信履歴がある予約メッセージ削除の改善
    * 今までは予約メッセージを削除すると、すでに送信された内容があっても予約メッセージが削除されてしまい送信内容を確認するのが困難でした。
    * 送信内容がある予約メッセージの削除を試みた時、削除された状態を'CANCEL'に修正して管理するように改善しました。

##### バグ修正
* 予約メッセージ照会時、レスポンス時間が長くなりリストを取得できないバグを修正
    * 登録した予約メッセージが多い場合、レスポンス時間が長くなり、リストを取得できないバグを修正しました。
* 即時送信および予約メッセージ照会時、リスト数が一致しないバグを修正
    * メッセージ照会時、リスト数にフィルタリング条件が含まれず、リスト数が一致しないバグを修正しました。
* メッセージ受信/確認データ収集時、UTC基準マイナス(-)時間帯のデータが収集されないバグを修正
    * UTC時間処理時、マイナス(-)時間帯の時間が正常に処理されず、収集されないバグを修正しました。
* メッセージ受信/確認統計照会APIで、eventフィールドが適用されない問題を修正
    * eventフィールドに値を設定しても、フィルタリングされないバグを修正しました。
    eventに設定できる値は次のとおりです。
    'SENT', 'SENT_FAILED', 'RECEIVED', 'OPENED'

#### [ETC]
##### 機能改善
* 共通メッセージ送信改善
    * 今までは共通メッセージ送信時、コンテンツの言語コードとトークンの言語コードが完全に一致する時のみ該当言語コードで送信が行われました。
  これを言語コードの類似性を測定し、最も近い言語コードで送信されるように機能を改善しました。
  例、コンテンツの言語コードが'zh'でトークンの言語コードが'zh-Hans', 'zh-Hans-CN'でも'zh'で送信されます。

<br>

### 2017.12.12
#### [API]
##### バグ修正
* 現地時間で予約送信時、送信時間の計算が異常になるバグを修正
    * 予約送信で現地時間送信(isLocalTime = true)を使用する時、
 時間帯別送信時間計算ロジックのバグを修正しました。

#### [ETC]
##### 機能改善
* セキュリティ脆弱性ライブラリアップデート
    * セキュリティ脆弱性が見つかったライブラリを、修正バージョンにアップデートしました。

<br>

### 2017.11.23
#### [Console]
##### 機能追加
* Logging機能追加
    * メッセージ送信履歴をLog & Crash Searchに保存できる機能を追加しました。
 使用しているLog & Crash Searchのアプリケーションキー(Appkey)をSettingタブLoggingに登録して機能を有効にできます。
    * 保存されたメッセージ送信履歴は、Log & Crash Searchページで確認できます。
    * <a href="/ko/Notification/Push/ko/console-guide/#_9" target="_blank">メッセージ送信履歴保存説明</a>

##### バグ修正
* 低解像度でポップアップがサービス使用方法に隠れるバグを修正
    * 一部の低解像度画面でポップアップが表示された時、サービス使用方法に隠れてしまうバグを修正しました。
* ReservationタブでEdit、Deleteボタンのバグを修正
    * ReservationタブでEdit、Deleteボタンがクリックできない状態でクリックされるバグを修正しました。

#### [API]
##### 機能改善
* v2.0失敗したメッセージ照会API Limitの追加
    * 今までは失敗したメッセージの照会時、結果全体をレスポンスしました。
 結果サイズが大きい場合、Response Timeoutが発生することがあったため、一度に最大1,000個までレスポンスできるように修正しました。
    * 結果が1,000個以上の場合、異常レスポンスを返します。異常レスポンスの場合、from, to期間をより短くして照会する必要があります。
    * <a href="/ko/Notification/Push/ko/api-guide/#_15" target="_blank">API Reference</a>
        * メッセージ > 照会 > 失敗したメッセージリスト照会

#### [ETC]
##### バグ修正
* [Mail]証明書終了案内メールの送信時、無効なアプリケーションキーが表示されるバグ
    * プッシュサービス使用終了後に再度使用した場合、証明書終了案内メールの送信時に以前のアプリケーションキー(Appkey)が表示されるバグを修正しました。

<br>

### 2017.09.21
#### [Console]
##### バグ修正
* Tag照会時、ソート基準がないバグを修正
    * Tag照会時、作成日時基準の降順でソートされるように修正しました。
* 予約メッセージ登録時、曜日が3個以上選択されないバグを修正
    * 予約タイプを'EVERY_WEEK'に設定した時、曜日が3個以上選択されないバグを修正しました。

#### [API]
##### 機能改善
* Tag登録時、名前にスペースを入力できないように修正

<br>

### 2017.08.24
#### [Console]
##### 機能追加
* Tagメッセージ送信追加
    * メッセージ送信、予約メッセージ送信タブで、Tagを選択してメッセージを送信できます。
    * TargetのTypeを'TAG'に設定すると、登録されたTagを選択できます。
    * 選択されたTagを'OR'または'AND'条件を使ってメッセージを送信できます。
    * 例えば、'ソウル'、'30代'、'男性'Tagを選択し、'AND'条件でメッセージを送信すると
  ソウルに住む30代男性にメッセージが送信されます。
* Tokenタブの追加
    * Webコンソールで、登録されたTokenをUid、Tokenで検索できます。
    * Uid検索の場合、全体一致だけでなく部分一致検索も可能です。
    * 新しいトークンの追加や、検索したトークンの削除ができます。
* Tagタブの追加
    * Tagを管理できます。
    * Tagが追加されているUidを照会できます。
    * UidにTagを追加、削除できます。

##### 機能改善
* Channelメッセージ送信機能の削除
    * Tagメッセージ送信機能が追加され、CONSOLEからChannelメッセージ送信機能を削除しました。
    * 既存Channelメッセージ送信機能はv1.3メッセージ送信APIで利用できます。

#### [API]
##### 機能改善
* 通知/広告性/夜間広告性プッシュメッセージ受信対象基準の改善
    * 韓国情報通信網法規定((第50条から第50条の8)に従い、韓国ユーザーのトークンは受信に同意しているかに応じて、メッセージ送信時に自動フィルタリングされます。
    * 最近iOSで多様な言語コードが作成され、韓国ユーザートークンに分類されないことがある問題がありました。
    * 今までは言語コード'ko'、'ko-kr'のみ韓国ユーザートークンに分類しましたが、  
    'ko'、'kor'または'ko-'を含む言語コードを韓国ユーザートークンに分類するように改善しました。

##### バグ修正
* 予約メッセージの状態を変更できないバグを修正
    * 予約メッセージの送信が完了しても、v2.0予約APIで追加されたreservationStatusがCOMPLETED(完了)にアップデートされないバグを修正しました。
* トークン登録時、oldToken、tokenフィールドに同じ値が設定された場合に削除されるバグを修正
    * 2017年08月03日hotfixで修正しました。
    * oldTokenは、トークンの変更が発生した時や、サーバーに保存されたトークンを新しいトークンに変更するために使用するフィールドです。
    * oldTokenにtokenと同じ値を設定してトークン登録APIを呼び出す場合、削除後に登録が省略されるバグを修正しました。
    * パッチ後、oldTokenとtokenが同じであれば削除せずにトークンをアップデートします。

#### [SDK]
##### Android
* トークン登録機能の改善
* 初期化動作の改善

##### iOS
* トークン登録機能の改善

<br>

### 2017.07.20
#### [API]
##### 機能追加
* タグ(Tag) APIの追加  
    * Uidにタグを追加して管理できます。
    * Uidに連絡先(Contact)を追加して管理できます。
    * メッセージ送信時、タグと条件を設定してメッセージを送信できます。   
例、メッセージ送信時、target.typeを'TAG'、target.toを'男性、AND、30代'に設定すると、'男性'と'30代'タグがついたUidを対象にメッセージが送信されます。
    * APIが先に公開され、8月の定期メンテナンス後にCONSOLEでタグ機能を使用できます。
    <a href="/ko/Notification/Push/ko/api-guide/#_13" target="_blank">API Reference</a>
* 失敗処理されたメッセージ照会APIの追加
    * メッセージ送信時、失敗したメッセージを照会できるAPIを追加しました。
  このAPIを利用して、送信が失敗した原因を確認できます。    
    <a href="/ko/Notification/Push/ko/api-guide/#_15" target="_blank">API Reference</a>

##### バグ修正
* トークン修正時、新しいトークンが存在する時、既存トークンは削除されないバグを修正
    * トークン登録APIでoldTokenをtokenに変更する時、tokenが存在する場合にoldTokenが削除されないバグを修正しました。
* メッセージ照会時、Internal Errorレスポンスバグを修正
    * メッセージ照会時、from, toに無効な形式のDateTime(日時)を入力した場合、Internal Errorレスポンスを返していましたが、Client Errorレスポンスを返すように修正しました。
* 予約メッセージ修正時、createdDateTimeが誤って設定されるバグを修正
    * 予約メッセージ修正時、updatedDateTime(修正日時)だけでなく、createdDateTime(作成日時)までupdatedDateTime値にアップデートされるバグを修正しました。

<br>

### 2017.05.25
#### [SDK]
##### Android
* SDKバージョン確認のためのAPIを追加
* 指標関連APIの変更

##### iOS
* SDKバージョン確認のためのAPIを追加

<br>

### 2017.04.25
#### [Console]
##### 機能追加
* Dashboard, Settingタブの追加
    * メッセージ受信、確認統計を確認できる[Dashboard]タブを追加しました。
    * メッセージ受信、確認データ収集機能を設定できる[Settings]タブを追加しました。

#### [API]
#####機能追加
* メッセージ受信、確認データ収集(Message Delivery Receipt)、統計照会機能の追加
    * メッセージ送信後、端末に受信、ユーザーのメッセージ確認データを収集し、統計で照会できる機能を追加しました。
    * [CONSOLE] > [Settings]タブで有効にでき、v2.0 API Referenceで統計照会APIの説明を確認できます。
    * この機能は、v1.4以上のSDKが適用された場所でのみ使用できます。   
    <a href="/ko/Notification/Push/ko/sdk-guide/#_4" target="_blank">SDK受信および開封したかどうかの適用ガイド</a>
* v2.0 API追加
    * トークン統計APIを追加しました。
    * 予約メッセージAPIを追加しました。
    * メッセージ受信、確認統計照会APIを追加しました。
    * v1.3フィードバックAPIは、v2.0無効なトークンAPIに変更しました。
    * レスポンスメッセージをより詳細に出力します。
    <a href="/ko/Notification/Push/ko/api-guide" target="_blank">v2.0 API Reference</a>

<br>

### 2017.02.23
#### [API]
##### バグ修正
* 送信期間が1か月以上の予約メッセージが送信されないバグを修正
    * 2017年1月までに登録された予約メッセージのうち、送信終了日が2月以降の予約メッセージが送信されないバグを修正しました。

#### [SDK]
##### Android
* ビルド時、Warning Logを削除
* play-service依存性を変更

##### iOS
* 安定性の改善

<br>

### 2017.01.19
#### [API]
##### 機能の追加
* メッセージ照会API Response BodyにcreatedDateTime(メッセージ作成時間)フィールドを追加

#### [ETC]
##### 機能改善
* [Mail]証明書終了案内メールアカウントを変更(support@cloud.toast.com → noreply@cloud.toast.com)

<br>

### 2016.12.22
#### [API]
##### バグ修正
* [API]予約メッセージ登録から1か月過ぎた場合、送信されないバグを修正
* [API]毎月1日に送信される予約メッセージが送信されないバグを修正
* [API]新しいバージョンFCM API Keyが登録できないバグを修正
* [API]送信結果が'MismatchSenderId'、'NotRegistered'の場合、トークンが削除されないバグを修正

<br>

### 2016.11.24
#### [SDK]
##### Android
* チャンネルデフォルト値を変更
* GCMライブラリバージョンアップデート(9.6.0)
* エラーログの細分化
* バグ修正

##### iOS
* チャンネルデフォルト値を変更

<br>

### 2016.10.06
#### [API]
##### 機能改善
* MPS単位1,000個/秒から100個/秒に変更

<br>

### 2016.09.29
#### [Console]
##### 機能改善
* 証明書を削除せず、すぐに交換できるように修正
* APNS Universal Certificate APNS_SANDBOX(Development)に登録できないバグを修正

#### [API]
##### バグ修正
* UID基準トークン照会APIで、APNS_SANDBOXトークンが除外されるバグを修正
* トークン登録APIで、Empty String("")が登録されるバグを修正

#### [ETC]
##### ポリシー変更
* データ保管期間ポリシーを変更、過去30日まで保存(メッセージ、予約メッセージ、フィードバック)

<br>

### 2016.08.18
#### [Console]
##### バグ修正
* 予約メッセージ修正時、保存した内容と異なる曜日が表示されるバグを修正