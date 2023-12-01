## Data & Analytics > Log & Crash Search > リリースノート

### 2023. 08. 29.
#### 機能改善/変更
* [Console]ログアラーム設定時、一部フィールドの長さ制限が変更されました。
  * アラームタイトルの長さ制限が20文字から80文字に変更されました。
  * アラーム説明の長さ制限が80文字から255文字に変更されました。

### 2023. 05. 30.
#### バグ修正
* [Console]選択可能なフィールドでUserTxtDataフィールドが表示されないように変更
#### 機能改善/変更
* [Console]検索フィールドメニューでUserTxtDataフィールドがカスタムフィールドではなく、基本フィールドとして表示されるように変更

### 2023. 04. 26.
### バグ修正
* ユーザーベースのアラームが動作しないバグを修正

### 2022. 12. 27.
#### 機能改善/変更
* [Console]ログ検索自動更新機能の追加
* [Console]ログ検索結果チャートをドラッグしてログ検索期間条件を設定できる機能を追加

### 2022. 11. 29.
#### バグ修正
* [Console]ログ検索結果のログクリック検索機能を改善
  * txt*、bodyフィールドの単語をクリックして検索しても全フィールドの値が検索されるバグを修正
  * カスタムフィールドクリック検索を行った時、ハイライトが適用されないバグを修正

### 2022. 09. 27.
#### バグ修正
* [Console]保存クエリリストメニューでクエリを連続削除 するとエラーページに移動するバグを修正

### 2022. 08. 23.
#### 機能改善/変更
* [Console]グローバルユーティリティ関数呼び出し方式の変更

### 2022. 07. 26.
#### 機能改善/変更
* [Console]ログ検索結果画面のUI/UX改善
    * 列挙型で表示形式提供
#### バグ修正
* [Console]一部プラットフォームのクラッシュダンプデータがダウンロードできない問題を修正
* [Console]ログアラーム設定メニューで2ページ以降のアラーム状態変更ボタンが動作しない問題を修正

### 2022. 06. 30.
#### 機能改善/変更
* [Console]選択されたフィールドダイアログUI/UX改善
    * フィールドダイアログ位置修正
    * ページ当たりのアイテム数を変更してもスクロールが最上段に移動しません。
    * ページ当たりのアイテム数変更後にページを移動してもページ当たりのアイテム数が初期化されません。
* [Console]バグ修正
    * クエリに特定文字が含まれたアラームの設定を修正すると、保存されたクエリとは異なるものが表示されるバグを修正

### 2022. 05. 24.
#### 機能改善/変更
* [Console] WebコンソールのUI/UX改善
    * Webコンソール内の時間を表示する方式を統一
    * Webコンソール内にローディングイメージを追加
* [Console]バグ修正
    * アプリクラッシュイシュー詳細情報のエラーインスタンスメニューで、データが特定の値のときにエラーインスタンスリストが表示されないエラーを修正

### 2022. 04. 26.
#### 機能改善/変更
* [Console]ログアラーム設定ページUI/UXを改善
    * **アラーム設定追加**ダイアログボックスで**アラームタイプ**を **発生数**から**増減率**に変更すると画面が正常に表示されなかったバグを修正

### 2022. 03. 29.
#### 機能改善/変更
* [Console]ログ検索ページUI/UX改善
    * ログ検索「広げて表示」を行ったときのボタン位置を修正
    * ログ検索時、クエリオートコンプリート項目キーボードが選択できるように変更

### 2022. 02. 22.
#### 機能改善/変更
* [Console]ログ検索ページのUI/UXを改善
    * ログ検索結果「広げて表示」を行ったときの表示形式を変更
    * クラッシュログインの場合、ログ検索ページに**イシュー照会**ボタンを提供

### 2022. 01. 25.
#### 機能改善/変更
* [Console]ログ検索ページのUX改善
  * ログ検索結果テーブルヘッダ固定
  * 「選択したフィールド」内のフィールド名をクリックしたときに表示されるポップアップウィンドウの形態を変更

### 2021. 11. 23
#### 機能改善/変更
* [Console]新しいUI/UXが適用されたWebコンソールをデフォルトで適用し、既存Webコンソールに切り替え機能を削除
* [Console]ログ検索ページUXの改善
    * ログ検索結果テーブル内の展開表示カラムを左側(一番前に)移動
    * 「選択したフィールド」領域内のフィールド名右側に該当フィールドの値の種類数を表示
    * 「選択したフィールド」内のフィールド名をクリックした時に表示されるモーダルウィンドウで該当フィールドの値の種類数が100を超える場合、正確な数を表示

### 2021. 07. 27.
#### 機能改善/変更
* [Console] Webコンソールの全体的なUI/UXの改善および変更

### 2021. 04. 27.
#### 機能改善/変更
* [Console]ログ検索APIを提供
* [Console]ログのダウンロード時、運営管理者がプロジェクトに設定したフィールドにマスキングを適用

#### バグ修正
* [Console]ログ検索ページ中の本文にhtmlが含まれている場合、htmlの内容が解析されて表示される現象を修正
* [Console]多数のクラッシュイシュー状態を同時に変更する場合に発生するエラーを修正

### 2020. 12. 15.
#### 機能改善/変更
* [Console]アラーム設定のうち、タイトルと説明の最大入力文字数を表示および制限
* [Console]クラッシュアラームのうち、しきい値を0に修正すると保存できないバグを修正
* [Console]ログ保管期間6か月、1年項目を削除、4か月を追加

### 2020. 10. 27.
#### 機能改善/変更
* [Console]セッションなしでアクセス可能なイベント詳細ページを新規サポート
    * ログアラーム発生時、従来のコンソールリンクの代わりにイベント詳細ページリンクをサポート
    * SMSにもイベント詳細ページリンクを追加

### 2020. 10. 13.
#### 機能改善/変更
* ログ(一般ログ、クラッシュログ)1件の容量制限を2MBから8MBへ変更

### 2020. 09. 22.
#### 機能改善/変更
* [Console]メール、Doorayアラームにおいて、添付されたTOAST Log & Crash SearchアクセスリンクでIAMコンソールをサポート

### 2020. 08. 25
#### 機能改善/変更
* [Console]アラームコールバック/Webフック(webhook)から複数の対象を入力して実行できるように改善

### 2020. 07. 28.
#### 機能改善/変更
* [Console]外部保管ログのデータ完全性検証機能を追加
    * [Console使用ガイド参考](/Data%20&%20Analytics/Log%20&%20Crash%20Search/ko/console-guide/#_27)

### 2020. 06. 23.
#### 機能改善/変更
* [Console] Object、Arrayタイプのクエリー方式を変更
    * 文字列検索と同じ方法でクエリーを伝達する必要があります。
    * [Luceneクエリーガイド参考](/Data%20&%20Analytics/Log%20&%20Crash%20Search/ja/lucene-query-guide/)
    
### 2020. 05. 26.
#### 機能改善/変更
* [Console] Bitcodeを適用したiOSアプリクラッシュ分析をサポート
    * 同じバージョン内でアーキテクチャごとにシンボルファイルをアップロードして分析できるように修正

### 2020. 04. 28.
#### 機能改善/変更
* [Console]ログ検索時、照会できる期間を最大3か月に制限
* [API] Android NDKクラッシュ識別方式を変更
#### バグ修正
* [Console]保存したクエリーの修正時、特定条件で保存されない問題を修正


### 2020. 03. 24.
#### 機能改善/変更
* [Console] 保存されたクエリーの削除に失敗した時のエラー文言を修正

### 2020.02.25.
#### 機能改善/変更
* [Console] SDKログ転送設定画面のツールチップ文言を修正
* [Console] クエリー保存機能にLuceneクエリーの有効性検証プロセスを追加
#### バグ修正
* [Console] シンボルファイルアップロード機能で特定Windowsシンボルファイルを処理できないバグを修正 
    * 複数回のビルドによりWindows PDBのage値が11を超過した場合、それ以降に抽出されたシンボルファイルはguidが34文字以上になる場合があります。guidフィールドの33文字制限を解除しました。
* [Console] 30日が経過したログを検索する時、保存されたフィールドが正常に表示されないバグを修正

### 2020.01.21.
#### 機能改善/変更
* [Console] iOSクラッシュ発生位置を探す方法の変更
* [Console] iOSクラッシュ追加情報表記 (TOAST SDK iOS 0.21.0以上のバージョンが必要です。)

### 2019.10.29.
#### 機能改善/変更
* [Console] S3アップロード機能を追加
* [Console] 無効なアラームクエリーでアラームを有効にした時のエラー文言を変更

### 2019.08.27.
#### バグ修正
- [Console]クエリーリストで、特定のクエリーが検索されない現象を修正

### 2019.06.25.
#### 機能改善 / 変更
* 一部iOSのクラッシュログのシンボリケーション結果が(null) ((null))になるイシューを修正
* ログ(一般ログ、クラッシュログ)単件の容量制限を1MBから2MBに増加
* アラーム受信者リストで、実際の電話番号が表示されるように修正

#### バグ修正
* アラームの最終修正者がプロジェクトメンバーから除外された場合、修正されたアラームがリストで照会できない現象を修正

### 2019.05.28.
#### バグ修正
* [Console] Windows 10、Internet Explorer 11環境で一部のページが正常に動作しない現象を修正
* [Console]シンボルファイルをアップロードした時、一部のZIPファイルを解析できないイシューを修正
* [Console] Webコンソールで言語を変更した時、特定部分が即時に反映されない現象を修正
* [Console]アラームを設定した時、http/httpsコールバックのうち、httpsコールバックを設定できない現象を修正

### 2019.03.27
#### 기능 개선 / 변경
* [Console] iOS arm64e 기기에서 발생한 크래시 분석 지원 (호환이 되는 SDK가 필요합니다.)
* [Console] Android NDK 에서 발생한 크래시 분석 지원 (호환이 되는 SDK가 필요합니다.)
* [Console] 국제화 적용 (일본어)

### 2019.01.15
#### 기능 개선 / 변경
* [Console] User console 적용
* [Console] Unity 에서 발생한 크래시를 지표에서 제외
    * 앱 크래시 검색 > 앱 크래시 지표에 집계되지 않음
* [Console] 이슈트래커 등록 이후, 등록 이전 상태로 되돌리는 기능 추가
* [Console] 심볼 파일 관리 화면에서 심볼리케이션에 사용되는 실제 심볼이름 강조 표기

### 2018.11.27
#### 기능 개선 / 변경
* [Console] 안드로이드 크래시 중 크래시가 발생한 부분이 unity 이며, 크래시 유형이 'java.lang.Error' 로 기록된 경우 예외 종류 정상적으로 판단하지 못하는 이슈 수정
    * 웹콘솔 > 크래시 > 이슈 조회에서 상세화면으로 진입이 되지 않는 이슈 수정
    * 웹콘솔 > 크래시 > 이슈통계 버전별 이슈 개수 노출되지 않는 이슈 수정
* [Console] 알람 관련 기능 UX/UI 개선
    * 알람 등록
    * 알람 히스토리
    * 크래시 알람 등록
    * 크래시 알람 히스토리
    * 사용자 기반 알람 등록
    * 사용자 기반 알람 히스토리
* [Console] 웹콘솔 > 설정 > 심볼파일 업로드 화면에서 Android unity 심볼 파일 가이드 추가
* [Console] Network insight URL 유효성 검증 변경

### 2018.10.23
#### 기능 개선/ 변경
* [Console] (구) 로그 알람 종료
    * [관련공지](https://toast.com/support/notice/detail/1453435858K00594)

### 2018.09.18
#### 기능 개선/ 변경
* [Console] 저장 쿼리 공유하기

### 2018.09.04
#### 기능 개선/변경
* [SDK][[logback-3.0.2](/Download/#data-analytics-log-crash-search)]
    * Logncrash Appender의 예약어 중 기본값이 없는 항목이 empty, null일 경우, 예약어 항목이 추가되지 않도록 개선
    * Logncrash REST API 타임아웃 설정
    * Logback의 AsyncAppender 사용

#### 버그 수정
* [SDK][[logback-3.0.2](/Download/#data-analytics-log-crash-search)]
    * 일부 empty, null의 예약어 항목이 추가된 버그 수정

### 2018.07.24

#### 기능 개선/변경
* [Console] 설정 페이지 UI 변경

### 2018.06.26

#### 버그 수정
* [SDK][[iOS-2.7.1](/Download/#data-analytics-log-crash-search)]
    * 중복하여 초기화 수행시 크래시 발생하던 버그 수정

### 2018.06.05

#### 기능 개선/변경
* [SDK][[Android-2.6.7](/Download/#data-analytics-log-crash-search)]
    * 저장된 로그의 경우, 필터를 거치지 않고 전송하도록 동작 변경

#### 버그 수정
* [SDK][[iOS-2.7.0](/Download/#data-analytics-log-crash-search)]
    * SDK 내부 로직 개선
    
* [SDK][[Android-2.6.7](/Download/#data-analytics-log-crash-search)]
    * Android 4.1.2 이하 버전에서 로그가 전송되지 않던 버그 수정 ( Android-2.6.6 SDK 버그 )

* [SDK][[Unity-2.8.6](/Download/#data-analytics-log-crash-search)]
    * iOS 에서 Unity Crash Log 발생시 LogLevel 이 전부 FATAL로 설정되던 문제 수정

### 2018.05.29

* [Console] iOS 크래시 심볼리케이션 중 중복된 이름의 Bundle(ex. Framework.UIKit, Accessibility.UIKit)이 존재 할 경우 심볼리케이션이 정상적으로 되지 않는 문제 수정

### 2018.05.09

#### 버그 수정

* [SDK][[Unity-2.8.5](/Download/#data-analytics-log-crash-search)]
    * Unity Script에서 발생한 Crash logType 롤백
        * Unity Script에서 발생한 Crash를 HANDLED로 처리하는 로직이 적용되어 롤백합니다.

### 2018.05.02 

#### 기능 개선/변경

* [SDK][[AOS-2.6.6](/Download/#data-analytics-log-crash-search)]
    * IP Address 수집 필드 제거
        * 콘솔에 표시되는 "host" 값은 서버에서 수집한 정보를 사용합니다.

* [SDK][[Unity-2.8.4](/Download/#data-analytics-log-crash-search)]
    * Android Native SDK 호출 API 개선

#### 버그 수정

* [SDK][[AOS-2.6.6](/Download/#data-analytics-log-crash-search)] 
    * 중복 제거 필터 오류 수정

* [SDK][[iOS-2.6.10](/Download/#data-analytics-log-crash-search)]
    * 초기화 과정에서 UserID 의 값이 nil 일 때 Crash가 발생하던 문제 수정
    * 초기화 과정에서 enableSyncStart 의 값이 YES 일 경우 CPU 이용률이 100%까지 올라가는 문제 수정

### 2018.04.24

#### 버그수정
* [Console] 앱 크래시 Gitlab 이슈 연동 시, 이슈 번호가 잘못 채번되는 문제 수정
* [Console] 앱 크래시 용도의 심볼파일을 삭제 후 같은 버전으로 심볼파일 업로드 시, 정상적으로 심볼리케이션 되지 않는 문제 수정
* [Console] SMS 알람에서 특정 문자가 알람 내용에 포함되어 있을 때 알람이 전송되지 않는 문제 수정
* [Console] 앱 크래시에서 알람 수신자에 특정 국가코드가 포함되어 앱 크래시 SMS 알람이 전송되지 않는 문제 수정

### 2018.01.22
#### 기능 개선/변경
* [Console] Network Insights 신규 기능 출시

### 2017.12.21
#### 기능 개선/변경
* [Console] 쿼리 기반 신규 알람 기능 추가

### 2017.10.26
#### 기능 개선/변경
* [Console] 새로운 크래시 발생 시 알람 설정 기능 추가

#### 버그수정
* [console] 세션 만료 시 에러 메시지를 노출하도록 수정

### 2017.09.21
#### 기능 개선/변경
* [SDK] 초기화 과정에서 CrashHandler를 자동으로 등록하지 않는 함수 추가 (MultihandlerSample 참고)
* [SDK] 외부에서 등록한 CrashHandler를 통해 Unity Crash를 전송할 수 있도록 변경 (MultihandlerSample 참고)
* [SDK] Optimization 스크립트를 통한 필요없는 SDK 제거 ( Doc 문서 참고 )
* [SDK] 사용자가 Settings 객체를 원하는 시점에 저장할 수 있도록 변경
    * 수정버전: [toast-logncrash-unity-2.8.3](/Download/#data-analytics-log-crash-search)
* [Console] 로그 서치 시간 출력 방식 변경 (ms 단위 제거 및 timezone 명시)
* [Console] 특정 필드의 distinct count가 100을 넘으면 TOTAL count를 출력
* [Console] 트렌드 페이지에서 crash를 겪은 사용자 UI 삭제
* [Console] 크래시 알람 메일 포맷 변경(dmpData 삭제 및 DmpReport formatting)
* [Console] Unity 크래시 분류 기준 변경
    * Unity 발생되는 ERROR 레벨의 로그들에 대해서 크래시로 분류 하지 않도록 수정됨
        * Log Search 화면에서 검색 및 조회 가능

#### 버그수정
* [SDK] initialize를 여러번 호출하는 경우 SessionID가 갱신 되는 문제 수정
* [SDK] BackKey로 Activity를 종료한 경우, SDK에서 마지막 Activity 상태를 저장하고 있어 Activity가 메모리에서 해제 되지 않는 문제 수정
    * 수정버전: [toast-logncrash-android-2.6.4](/Download/#data-analytics-log-crash-search) / [toast-logncrash-unity-2.8.3](/Download/#data-analytics-log-crash-search)
* [SDK] PLCrashReporter가 Crash File을 생성하지 못하는 경우, 'EMPTY CRASH FILE'을 DmpData에 넣어 전송하도록 수정
    * 수정버전: [toast-logncrash-ios-mac-sdk-2.6.7](/Download/#data-analytics-log-crash-search) [toast-logncrash-unity-2.8.3](/Download/#data-analytics-log-crash-search)
* [SDK] iOS SDK에서 Native Crash 발생 시, CrashStyle, SymMethod가 잘못 표기되는 문제 수정
* [SDK] WebGL에서UserID가 설정되지 않던 문제 수정
* [SDK] unity ios wrapper class에서 https 프로토콜이 지정되지 않던 문제 수정
    * 수정버전: [toast-logncrash-unity-2.8.3](/Download/#data-analytics-log-crash-search)

### 2017.07.20
#### 기능 개선/변경
* [SDK] WebGL플랫폼 지원
    * 수정버전: [toast-logncrash-unity-2.7.4](/Download/#data-analytics-log-crash-search)
* [Console] 크래시 목록 화면 softing option에서 사용자수 제거

#### 버그수정
* [Console] 크래시 사용자 레이아웃 버그 수정

### 2017.06.22
#### 버그수정
* [SDK] 중복제어 큐가 최대 사이즈가 넘은 경우, LFU 동작의 Delete 버그로 인해 Crash가 발생하는 현상 수정
    * 수정버전: [toast-logncrash-cpp-windows-sdk-2.5.4](/Download/#data-analytics-log-crash-search) / [toast-logncrash-csharp-windows-sdk-2.5.4](/Download/#data-analytics-log-crash-search)/ [toast-logncrash-androidndk-sdk-2.6.2](/Download/#data-analytics-log-crash-search)
* [SDK] ReSend 로그 저장 시 2MB씩 총 20MB저장하는 방식에서 2MB만 저장하도록 변경
* [SDK] Send Queue 사이즈를 500개에서 2000개로 변경
* [SDK] 인터넷이 연결되어 있지 않은 경우, 전송 동작을 하지 않는 방식에서 파일로 저장하도록 변경
* [SDK]인터넷 연결이 끊겼다가 다시 연결된 경우, 파일에 저장했던 로그를 재전송 하도록 변경
    * 수정버전: [toast-logncrash-cpp-windows-sdk-2.5.4](/Download/#data-analytics-log-crash-search) / [toast-logncrash-csharp-windows-sdk-2.5.4](/Download/#data-analytics-log-crash-search)
* [SDK] 일부 필드(국가 코드, 플랫폼정보 등) 누락 현상 수정
    * 수정버전: [toast-logncrash-android-2.6.2](/Download/#data-analytics-log-crash-search)
* [SDK] 에러 내용을 errorCode와 txterrorCode 필드에 담아 전송하도록 변경
    * 수정버전: [toast-logncrash-logback-sdk-2.2.7](/Download/#data-analytics-log-crash-search) / [toast-logncrash-log4j-sdk-2.2.7](/Download/#data-analytics-log-crash-search)

### 2017.06.19
#### 버그수정
* [SDK] SendThread에 Sleep이 없어 CPU 사용률이 99%가 되는 현상 수정
* [SDK] 초당 100건의 로그를 보내는 경우, 메모리 해제가 정상적으로 되지 않는 현상 수정
    * 수정버전: [toast-logncrash-ios-unity-mac-sdk-2.6.6.1](/Download/#data-analytics-log-crash-search)

### 2017.05.25
#### 기능 개선/변경
* [Console] 로그서치 필드명 자동완성 기능 추가
* [Console] Crashes > 앱 크래시 지표 페이지 하단 테이블 UserID Column 표시 순서 변경 및 Gray 처리
* [Console] 세션로그 화면 노출 여부를 사용자가 on/off 할 수 있도록 기능 추가
* [SDK] Unity Android / Android 통합
    * 수정버전: [toast-logncrash-android-2.6.1](/Download/#data-analytics-log-crash-search)
* [SDK] hotfield Enable/ Disable추가
    * 수정버전: [toast-logncrash-android-2.6.1](/Download/#data-analytics-log-crash-search) / [toast-logncrash-androidndk-sdk-2.6.1](/Download/#data-analytics-log-crash-search)

#### 버그 수정
* [SDK] Unity Crash 재전송 시, Seesion 로그가 한 번 더 전송되는 동작 수정
* [SDK] DevicID 필드가 누락되는 버그 수정
    * 수정버전: [toast-logncrash-ios-unity-mac-sdk-2.6.5.1](/Download/#data-analytics-log-crash-search)

### 2017.04.20
#### 기능 개선/변경
* [Console] 앱크래시지표 화면 레이아웃 변경
    * 앱크래시지표 화면에 SDK버전 표시
    * 사용자 / 디바이스 정보 테이블에 같이 표시
    * 테이블 헤더 변경 "버전" -> "앱버전 (SDK버전)"
* [Console] 크래시맵 화면 레이아웃 변경 및 멥에 디바이스 수 추가
* [Console] 새창 열기 기능 활성화
* [Console] 알람 발송 포맷 변경(프로젝트 이름 대신 알람 이름 노출
* [SDK] 기능 추가
    * Init함수와 Log 전송 사이의 AddCustomField를 보장하기 위하며, SendThread Lock 기능 추가
        * 수정버전: [toast-logncrash-ios-unity-mac-sdk-2.6.0](/Download/#data-analytics-log-crash-search) / [toast-logncrash-android-unity-sdk-2.6.0](/Download/#data-analytics-log-crash-search) / [toast-logncrash-android-2.6.0](/Download/#data-analytics-log-crash-search)
* [SDK] 기능변경
    * Exception, errorCode, RequestHeader 필드를 콘솔에서 분석 가능한 형태로 전송
		* txtException, txterrorCode, txtRequestHeader 필드명으로 변경됨
		* 수정버전: [toast-logncrash-log4j-sdk-2.2.6](/Download/#data-analytics-log-crash-search) / [toast-logncrash-log4j2-sdk-2.2.6](/Download/#data-analytics-log-crash-search)/ [toast-logncrash-logback-sdk-2.2.6](/Download/#data-analytics-log-crash-search)
		* Exception,errorCode,RequestHeader 필드에 대해 알람설정이 된경우 2.6 적용 후 txt\* 필드로 수정이 필요함
    * 최대 2M까지 로그를 모아 전송하도록 Send 방식 변경
        * 수정버전: [toast-logncrash-ios-unity-mac-sdk-2.6.0](/Download/#data-analytics-log-crash-search) / [toast-logncrash-android-unity-sdk-2.6.0](/Download/#data-analytics-log-crash-search) / [toast-logncrash-android-2.6.0](/Download/#data-analytics-log-crash-search)
* [SDK] Unity-ios / ios SDK 통합
    * 변경사항은 SDK 파일내 README.md 파일 참고
    * [Toast-logncrash-ios-unity-mac-sdk-2.6.0](/Download/#data-analytics-log-crash-search)
    *  Toast-logncrash-unity-ios-sdk / toast-logncrash-ios-mac-sdk 삭제

#### 버그 수정
* 알람 주기가 1분이 아닌 경우 snooze 가 동작 하지 않는 무제 수정
### 2017.03.23
#### 기능 개선/변경
* [Console] 덤프 분석에 실패한 크래시도 UNKNOWN 크래시 형태로 통계 정보를 제공 하도록 기능 개선
* [Console] 스택 트레이스를 표시할 수 없을때, 스택 트레이스 화면에 안내 문구 표시
    * 심볼파일을 등록하지 않아서 스택 트레이스를 표시할 수 없을 때 (에러타입이 UNKNOWN일 때), 스택 트레이스 화면에 안내문구 표시

#### 버그 수정
* [Console] 영문 크래시 서치 화면에서 Real Time Monitoring 탭 깨지는 현상

### 2017.02.23
#### 기능 개선/변경
* [API] [log Bulk upload](/Data%20&%20Analytics/Log%20&%20Crash%20Search/ko/api-guide/) 기능 추가
    * REST API 로그 전송시 JSON array 형태로 로그 전송이 가능합니다.
* [API] long,double 옵션 추가
    * REST API 로그 전송시 long, double 로 시작하는 필드 사용시 long,double 타입으로 저장
    * 로그 검색 화면에서 long, double 타입 Range 검색이 가능합니다.
* [SDK] CrashCallback 기능 추가
    * [Windwos csharp SDK 2.5.2.1](/Download/#data-analytics-log-crash-search) / [Windows cpp SDK 2.5.2.1](/Download/#data-analytics-log-crash-search)

#### 버그 수정
* [WEB] 저장된 쿼리 보기 페이지에서 쿼리 삭제 불가능한 문제 수정
* [WEB] 이슈 상세에서 뒤로가기 클릭하면 이슈 목록 1페이지로 이동하지 않도록 pagination 개선
* [SDK] Thread간의 충돌 현상 수정
    * [unity-android-sdk 2.5.6.0](/Download/#data-analytics-log-crash-search)
* [SDK] 외부 라이브러리와 logncrash를 함께 빌드 시 binaryimagesort duplicate symbol 오류 수정
    * [unity-ios-sdk-2.5.2.6](/Download/#data-analytics-log-crash-search)
* [SDK] 일부 기기에서 breakpad 의 작업이 완료되기 전 어플리케이션이 강제로 종료 되는 현상 수정
    * [androidndk-sdk 2.4.7.0](/Download/#data-analytics-log-crash-search)
* [SDK] Async 모드에서 customField 가 추가되지 않는 현상 수정
    * [Log4j-sdk-2.2.5](/Download/#data-analytics-log-crash-search)/ [Logback-sdk-2.2.5](/Download/#data-analytics-log-crash-search)

### 2017.01.19
#### 기능 개선/변경
* 앱 크래시 지표 버전 표시 기준 변경
    * 앱 크래시 지표 > 크래시가 발생하지 않았지만 실행수가 존재하는 버전도 표시 되도록 수정
#### 버그 수정
* Log Search 화면에 로그 모두 보이기/숨기기 기능 수정

### 2016.12.22
#### 기능 개선/변경
* Web 화면에서 로그 파일 다운로드시 최대 10만개로 제한
    * 10만개 이상 시도시 팝업 알람
* [SDK] iOS/Android 의 네이티브 레벨 예외를 수집할수 있도록 기능 추가
    * 수정버전: unity-android-sdk-2.5.1, unity-ios-sdk-2.5.1
* [SDK] Log Duplicate Queue Size가 최대 1,000개로 제한
    * 수정버전: Android-2.4.3, Android-NDK-2.4.5, iOS-2.4.1, unity-android-2.5.1, unity-ios-2.5.1

### 2016.12.08
#### 기능 개선/변경
* 이슈 조회 > 이슈 상세 > 코멘트, 히스토리 탭에서 내용을 등록한 사용자가 프로젝트 멤버에서 삭제 된 경우
  이메일 노출 부분에 "[삭제된 멤버]"로 표시

#### 버그 수정
* 로그 알람 설정 시 필터링 규칙의 (비)포함 문자열에 "\"가 포함될 경우 로그 알람 목록이 조회되지 않는 버그 수정
* 크래시 알람 신규 저장 시 멤버 리스트가 없을 경우 실패 알람이 뜨도록 수정

### 2016.11.24
* [SDK] 일부 기기에서 host필드를 구하는데 사용되는 getaddrinfo 함수가 hang현상을 유발하여, host값은 내부 thread에서 구하도록 변경
  * 수정버전: Android-NDK 2.4.4

### 2016.11.04
#### 버그 수정
* [SDK] Android 2.4.1 버전에서 AsyncTask가 Cancel 되지 못하는 버그가 있어, 해당 로직을 Thread로 변경
  * 수정버전: Android 2.4.2

### 2016.10.20
#### 기능 개선/변경
* 기기의 고유 ID 값인 DeviceID 수집
    * 신규 SDK을 통한 Crash Log 전송시 DeviceID가 수집되어 Console > Log & Crash Search > Crashes > 앱 크래시 지표 화면에서
      DeviceID 기준으로 지표 확인이 가능합니다.
* [SDK] 로그 전송이 안되는 경우 파일로 저장 후 이후 정상 통신이 되는 경우 로그 파일 전송하도록 기능 변경됨.
* [SDK] 모든 로그에 대해 중복 로그 처리 루틴 적용
    * 중복 로그 기능이 켜져 있는 경우 Body 와 logLevel 의 내용이 같은 로그가 발생하면 전송하지 않습니다.
    * 필요한 경우 사용자가 별도의 API로 제어 가능하도록 기능 제공됨.
    * 상세내용은 Developer's Guide 참고.
* [Console] 앱 크래시 지표 화면 > '세션','사용자수' 타이틀 '실행 수' '크래시를 겪은 사용자'로 변경됨.

### 2016.09.29
#### 기능 개선/변경
* 알람 임계치 설정 및 http Callback 기능 추가
    * 알람 임계 값 비교 연산자 지원(>,>=,=,<=,<)
    * n 시간전 비교 이상/이하 기능 추가
    * Snooze 기능 추가
* Log Search 화면에서 다운로드 가능한 UserTxtData 필드 추가
    * "UserTxtData" 필드는 Log Search 화면에서 [다운로드|보기] 표시 하여 필드 내용을 바로 확인이 가능

#### 버그 수정
* [SDK] Exception이 발생한 경우 , 로그 전송 객체를 초기화 하지 못하여 반복적으로 초기화를 재시도 하던 버그 수정
    * 수정된 SDK: logback , log4j, log4j2
* [SDK] init 함수에 UserID를 세팅하면 로그에 값이 정상적으로 추가되지 않던 버그 수정
    * 수정된 SDK: iOS

### 2016.09.12
#### 버그 수정
* [SDK] Carrier와 Carrier 값이 null이 return되는 케이스에 대한 예외처리 코드 추가
    * 수정된 SDK: Unity(v.2.3.4)

### 2016.08.22
#### 기능 개선/변경
* Custom Field Default 옵션 및 길이 제한 변경
    * Custom 필드 생성시 analyzed(분석여부) false 로 변경
    * 전송 가능한 로그 길이 128byte -> 2Kbyte 변경
    * 2Kbyte 이상의 로그 전송이 필요한 경우 Field 명에 txt prefix 지정하여 Custom field 생성
    * txt*; string, 옵션 [in] 필드 이름이 txt로 시작하는 필드(txt_description 등)는 분석(analyzed) 필드로 저장<br>
      로그 검색 화면에서 필드 값의 일부 문자열로 검색이 가능


### 2016.08.18
#### 기능 개선/변경
* Log 전송 ON / OFF 기능 추가
    * Log & Crash Search 로 전송되는 로그(일반로그/크래시로그/세션로그)에 대해 사용자가 콘솔에서
      On/Off 설정, 수집여부를 결정할수 있습니다.
    * 수집되지 않은 로그는 화면에 노출되지 않고, API 및 Storage 요금에 포함되지 않습니다.
    * Log on/off 기능 추가로 SDK 업데이트 되었습니다.
        * 대상 SDK(v.2.3.0): Unity, Android , Windows, iOS

* [API] UserBinaryData 필드 추가
    * 로그 파일이나 바이너리 파일을 위 필드로 전송시 로그 검색 화면에 다운로드 가능

#### 버그 수정
* [Console] Crash 상세 페이지 로딩 속도 문제 수정


### 2016.08.04
#### 기능 개선/변경
* [SDK][Unity] 2.2.6 업데이트
    * SaveToFile 저장 포맷 변경
    * Regular Expression, JSON 라이브러리를 사용하여 변환하도록 수정
    * 파일 최대 저장 개수 100개 제한
    * 중복 제거 큐 100개 제한

#### 버그 수정
* [API] 특정 필드에 json array나 object를 전송한 경우 string으로 변환 되는 현상 수정
