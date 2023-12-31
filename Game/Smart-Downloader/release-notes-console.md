## Game > Smart Downloader > リリースノート > Console


### 2020. 11. 24.
#### 機能改善/変更
* 一括、予約配布機能を追加。
    * Smart Downloader CDNを使用するサービスはリストページに一括、予約配布を行うことができるように機能を追加。
    * Smart Downloader CDNを使用するサービスは、個別配布時にも予約配布を行うことができるように機能を追加。
* サービス作成ウィザードのファイルアップロード画面でファイルアップロードを行わずにサービス作成ができるように修正。


### 2020. 07. 14.
#### 機能改善/変更
* ビルド配布機能修正。
    * ビルド配布時に5分間、同じプロジェクトのSmart Downloader CDNを使用するサービスの配布ができないように修正。
    * 配布ボタンの名称をサービスの状態に合わせて表示するように機能修正。


### 2020. 06. 11.
#### 機能改善/変更
* ビルド配布機能修正。
    * Smart Downloader CDNを使用する場合、ビルド配布実行時に原本ソースファイルとCDNに配布されたファイルを比較した後に配布完了処理するように機能修正。
    * ビルド配布実行時、ビルド配布ボタンがすぐに無効になるように機能修正。


### 2020. 04. 14.
#### 機能改善/変更
* Smart Downloader CDN修正
    * CDNベンダー社を変更するための移行作業を支援するためCDN修正が不可能に変更
* ファイルのアップロード
    * ファイルのアップロード制限を全体5GB以下で、単一のファイル5GB以下に変更

### 2020. 03. 24.
#### 機能改善/変更
* Smart Downloader CDN連携
    * CDNサービス地域を選択する機能を削除


### 2019. 12. 24.
#### 機能改善/変更
* サービス管理
    * CDNの作成に失敗した場合、失敗したCDNを削除して新しいCDNを作成するための機能を追加


### 2019. 01. 29.
#### 機能改善/変更
* 共通
    * ページの全てのメッセージに多言語(英語、日本語)を反映


### 2018. 12. 27.
#### 機能改善/変更
* 共通
    * ページの全てのメッセージに標準語検収結果を反映


### 2018. 10. 23.
#### バグ修正
* サービス管理
    * アップロードするリソースファイルの数が1個以上の場合、正常にアップロードできない問題を修正


### 2018. 07. 05.
#### 機能改善/変更
* 共通
    * ボタン
        * 最新ビルドの状態が**配布待機**または**配布失敗**状態の場合、**ビルド配布**ボタンが有効になるように修正
* サービスリスト
    * 最新ビルド領域を修正
        * 修正前：アップロード日時、Last Uploader、状態データを表示
        * 修正後：ビルド配布日時、リソースアップロード日時、状態データを表示。サービスリストの状態領域で**ビルド配布**ボタン使用可能


### 2018. 06. 26.
#### 機能改善/変更
* 共通
    * ネットワーク接続が切断された場合、ユーザーがわかるようにポップアップを追加
    * 文言修正
        * リソース配布URL -> オリジンサーバーURL
        * 内部CDN -> Smart Downloader CDN
        * 外部CDN -> 顧客企業CDN
* サービス管理
    * ビルドアップロード / 配布機能を分離
        * 修正前：リソースのアップロード時、即時にアップロードされたリソースがユーザーへ配布される
        * 修正後：リソースのアップロード後、サービス詳細表示で**ビルド配布**ボタンをクリックしてアップロードされたリソースを配布
    * サービス登録ウィザード(wizard)内実行時、リソースファイルのアップロードとCDN登録の作業順序を変更
    * サービス配布時、サービスおよび連携CDNの変更ができないように機能を追加
    * サービス詳細表示で、アップロード履歴表示を配布履歴表示に変更

#### バグ修正
* サービス管理
    * リソースのアップロード中に発生する一部エラーを修正
    * CDN設定中に発生する一部エラーを修正
    * 顧客企業CDNのURLが長すぎる場合、確認用URLがポップアップウィンドウの領域を超える問題を修正
    * Explorerにおいて、ビルド詳細情報表示で縦、横スクロールが同時に動く現象を修正


### 2018. 04. 24.
#### 機能改善/変更
* 共通。
    * サーバー内エラー発生時、ERRORページではなくServiceリストページへ移動した後、エラーポップアップが表示されるように機能を追加
* サービス管理
    * 1つのサービスでSmart Downloader CDNを重複して作成できないように機能を追加

#### バグ修正
* サービス管理
    * Mac用Chromeで、まれにファイルアップロードが失敗するエラーを修正
    * サービスを使用しない時(disable)ファイル保存場所やCDNで発生するエラーにより失敗する現象を修正
* モニタリング
    * サービスが登録されていない場合、モニタリングページでエラーが発生する問題を修正


### 2018. 03. 22.
#### 機能改善/変更
* サービス管理
    * CDN連携を行うための入力値のうち、referers項目に複数のドメイン情報(正規表現を含む)を入力できるように修正

#### バグ修正
* 共通
    * 韓国語以外の言語を選択した時、エラーページが表示される現象を修正
    * 他のタブでログアウトした時、ログインページがWebコンソールのサービス領域内に重複して作成される現象を修正
* サービス管理
    * ビルドのアップロード中にブラウザを閉じたり、更新を行った場合、ビルドの状態が登録中で維持される現象を修正
    * ビルド詳細情報の照会時、縦、横のスクロールバーが同時に移動する現象を修正
* モニタリング
    * モニタリングページの検索用のサービスリストがチャート領域に隠れて選択できない現象を修正
    * モニタリングページに作成されるポップアップの上に検索条件フィールドが表示される現象を修正
    * マップチャートで特定の国のツールチップがマウスカーソルよりかなり下に作成される現象を修正
    * Internet Explorer 10/11、Microsoft Edgeで発生するUIエラーを修正


### 2018. 02. 22.
#### 機能改善/変更
* Smart Downloader内の個別単位<b>サービス</b>を追加
* ユーザーの利便性向上
    * 新規ビルドアップロード/配布機能を追加
    * ビルド配布時、TOAST CDNを使用できるように機能を提供
    * リアルタイム/モニタリング指標を改善
    * ダウンロードエラー状況指標を詳細に


### 2017. 02. 23.
#### 機能改善/変更
* 各ページにアクセスできるタブを追加
* ダウンロード詳細検索時、検索対象データが多すぎる場合、検索項目を再度設定できるように機能を修正
* ダウンロード詳細検索時、ダウンロード失敗のみ選択した場合、「ダウンロード時間/速度」項目は選択されないように修正

### 2017. 01. 19.
#### 新規サービスリリース
* Smart Downloaderサービスリリース
    * Smart Downloaderはゲームに必要なリソースを効率的にダウンロードできるサービスです。
    * ゲームダウンロードデータをベースに、多様な統計データを提供しています。
