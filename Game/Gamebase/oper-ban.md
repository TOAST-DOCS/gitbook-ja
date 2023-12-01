## Game > Gamebase > Console ご利用ガイド > 利用停止

アプリを不当に使用したり、アビュージング行為をするゲームユーザーに対してアプリの利用を制限することができる利用停止機能を提供します。
利用停止状態となったゲームユーザーがもう一度ログインしたりセッションを復旧する場合に利用停止に関するポップアップが表示され、ゲームの利用が制限されます。

利用停止の登録は、Gamebase Consoleから手動で登録することができ、NHN Cloud AppGuardを使用する場合は、パターン登録を利用して自動で登録することができます。

AppGuardを連携する方法は、[AppGuard](./oper-ban/#appguard)をご参考ください。


## Ban

利用停止履歴を照会したり、利用停止の登録、利用停止状態のゲームユーザーに対する利用停止の解除が可能です。

### Search Banned User

検索条件に合った利用停止状態/利用停止状態が解除されたゲームユーザーのリストを照会します。

![gamebase_ban_01_201812](https://static.toastoven.net/prod_gamebase/gamebase_ban_01_201812.png)

**検索条件**

- **状態**：(必須)検索したい利用停止状態を選択(利用停止/利用停止解除)。二つを同時に選択することはできず、 一つだけ必須項目として選択する必要があります。
- **登録日**：(必須)利用停止登録日の区間を選択(from-to)
- **ユーザーID**：利用停止状態/利用停止状態が解除されたGamebaseのユーザーID
- **テンプレート**：利用停止の登録に使用した特定のテンプレートを選択して照会
- **登録システム**：利用停止を登録したシステムを選択して照会。複数選択可能
    - **コンソール**：Gamebase Consoleを通して登録
    - **アプリガード**：AppGuard連携で自動登録
    - **外部サーバー**：アプリを運営するサーバーまたはその他の外部サーバーから登録
    - **その他**：上の場合を除くその他の利用停止登録(APIを直接呼び出すものなど)

> [参考]
> ユーザーに表示するメッセージを多国語で入力して簡単に再使用することができるようにテンプレートを提供します。
> 登録されたテンプレートは一つ以上でないと、利用停止の登録をすることができません。
> テンプレートを登録する方法は、[Template](./oper-ban/#template)をご参考ください。

**検索結果**

- **ユーザーID**：利用停止中のゲームユーザーID
- **期間**：利用停止期間。永久停止の場合、「永久停止」と表示される
- **テンプレート**：利用停止の登録に使用したテンプレート
- **理由**：利用停止を登録する際に運営者が入力した理由。該当する理由はユーザーに表示されず、運営履歴でのみ確認することができます。
- **登録者/登録日**：利用停止を登録した運営者のアカウント/利用停止登録日
- **解除理由**：利用停止を解除する際に運営者が登録した理由。該当する理由はユーザーに表示されず、運営履歴でのみ確認することができます。
- **解除登録者/解除登録日**：利用停止を解除した運営者のアカウント/利用停止解除日
- **解除**：利用停止状態のユーザーには、検索リストから利用停止を解除することができるよう、**利用解除**ボタンが表示されます。ボタンをクリックすると利用停止を解除する理由を入力するポップアップが表示され、利用停止を解除する理由を入力して**保存**ボタンをクリックすると、利用停止状態を解除することができます。
- **状態**
    - <font color="white" style="background-color:#FB8F37">利用停止</font>：ゲームユーザーが現在、アプリに接続できない状態
    - <font color="white" style="background-color:#A1A1A1">利用停止(期限切れ)</font>：ゲームユーザーの利用停止期間が終了したものの現在はログインをしていない状態。ゲームユーザーが再接続する際に状態が解除(期限切れ)に変更される
    - <font color="white" style="background-color:#88C637">解除</font>：運営者によってゲームユーザーの利用停止が解除された状態
    - <font color="white" style="background-color:#2AB1A6">解除(期限切れ)</font>：利用停止期間終了後、ゲームユーザーがゲームに再接続して利用停止が解除された状態


> [参考]
> **ファイルダウンロード**ボタンをクリックすると、検索結果をCSVファイルで保存することができます。

### Register Ban

利用停止照会画面から**登録**ボタンをクリックすると、利用停止の登録ができます。

![gamebase_ban_02_201812](https://static.toastoven.net/prod_gamebase/gamebase_ban_02_201812.png)
#### (1) ユーザーID
利用停止を登録するGamebaseのユーザーIDを入力します。一度に複数のユーザーを登録することができ、登録方法は次の二つです。

- **ユーザー入力**：登録するユーザーIDを入力ウィンドウに直接入力した後、**Enter**キーを押したり**追加**ボタンをクリックします。ユーザーIDの有効性をチェックするため、有効でないユーザーIDは入力が不可能です。
- **一括登録**：CSVファイルのみアップロードでき、サンプルファイルはConsole画面からダウンロードすることができます。一括登録は1回につき最大10,000人まで可能です。
  ![gamebase_ban_03_201812](https://static.toastoven.net/prod_gamebase/gamebase_ban_03_201812.png)

> [参考]</br>
> 一括登録を進行する途中に失敗すると、ポップアップが表示されます。該当するポップアップから**Download**ボタンをクリックすると、登録に失敗したユーザーリストをファイルでダウンロードすることができます。
> ![gamebase_ban_04_201812](https://static.toastoven.net/prod_gamebase/gamebase_ban_04_201812.png)

#### (2) 期間
ゲームユーザーの利用停止期間を設定します。利用停止が登録された時点からゲームユーザーはログインができなくなります。

- **永久利用停止**：永久利用停止にしたいときに選択します。
- **期間指定**：利用停止にする期間を入力します。日(day)と時間(hour) **予想期限**情報からユーザーの利用停止期間を先に確認することができます。

#### (3) 理由
ユーザーが利用停止になった理由を入力します。
該当する理由はユーザーに表示されず、運営履歴でのみ確認することができます。

#### (4) 表示するメッセージ
ユーザーに表示する利用停止メッセージを入力します。
ユーザーに表示するメッセージを多国語で入力して簡単に再使用できるようにするテンプレートを提供します。予め登録したテンプレートを選択して登録します。

> <font color="red">[重要]</font>
> 表示されたメッセージのテンプレートが登録された場合にのみ利用停止を登録することができます。
> テンプレートを登録していない場合、**BAN**メニューの**テンプレート**タブからまずテンプレートを登録してください。
> テンプレートを登録する方法は、[Template](./oper-ban/#template)をご参考ください。

#### (5)リーダーボード削除

利用停止を登録する時、該当ゲームユーザーのLeaderboardデータも一緒に削除するかどうかを設定します。
選択して登録すると、リーダーボードからゲームユーザーのデータが削除されます。<font color="red">データは復旧できないため</font>注意してください。

### Release Ban

利用停止照会画面から**解除**ボタンをクリックすると、利用停止を解除することができます。

![gamebase_ban_05_201812](https://static.toastoven.net/prod_gamebase/gamebase_ban_05_201812.png)

#### 解除理由
ユーザーの利用停止を解除する理由を入力します。
該当する理由はユーザーに表示されず、運営履歴でのみ確認することができます。

#### ユーザーID
利用停止を解除するGamebaseのユーザーIDを入力します。一度に複数のユーザーを登録することができ、 登録方法は次の二つです。

- **ユーザー入力**： 登録するユーザーIDを入力ウィンドウに直接入力した後、**Enter**キーを押したり**追加**ボタンをクリックします。ユーザーIDの有効性をチェックするため、有効でないユーザーIDは入力が不可能です。
- **一括登録**： CSVファイルのみアップロードでき、サンプルファイルはConsole画面からダウンロードすることができます。一括登録は1回につき最大10,000人まで可能です。

![gamebase_ban_06_201812](https://static.toastoven.net/prod_gamebase/gamebase_ban_06_201812.png)

> [参考]
> 一括登録を進行する途中に失敗すると、ポップアップが表示されます。該当するポップアップから**Download**ボタンをクリックすると、登録に失敗したユーザーリストをファイルでダウンロードすることができます。
> ![gamebase_ban_04_201812](https://static.toastoven.net/prod_gamebase/gamebase_ban_04_201812.png)

## Template
利用停止対象ユーザーに表示するメッセージを多国語で入力して簡単に再使用できるようにするテンプレートを提供します。予め登録したテンプレートを選択して登録します。
言語ごとに登録でき、利用停止対象ユーザーにはデバイスで設定された言語を基に利用停止メッセージが表示されます。

### Search

登録されたテンプレートリストを検索することができます。
新しいテンプレートを登録したり、登録されたテンプレートを修正することができ、登録されたテンプレートを削除することはできません。

![gamebase_ban_07_201812](https://static.toastoven.net/prod_gamebase/gamebase_ban_07_201812.png)

-テンプレートリスト画面の表示メッセージ項目には、テンプレート登録時に「基本言語」で入力した表示メッセージが表示されます。

### Register Template
![gamebase_app_01_202004](https://static.toastoven.net/prod_gamebase/gamebase_ban_08_202004.png)

#### (1) 名前
利用停止を登録する際にリストに表示するテンプレートの名前を入力します。

#### (2) 表示メッセージ
利用停止対象ユーザーに表示するメッセージを入力します。
複数の言語で登録することができ、入力した言語以外の言語を使用する対象ユーザーには「基本言語」に選択された言語が表示されます。右の**+**ボタンをクリックすると言語を追加でき、利用したい言語がない場合、[カスタマーセンター](https://toast.com/support/inquiry)までご連絡ください。新しい言語を追加することができます。
**基本言語で自動翻訳**ボタンをクリックすると、基本言語に入力された内容を翻訳して各項目に設定された言語に合わせて入力されます。

## AppGuard

> <font color="red">[重要]</font>
> AppGuard連動機能は、NHN Cloudで該当機能を適用しようとしているサービスと同じプロジェクトにNHN AppGuardサービスを有効化した場合にのみ利用できます。

![gamebase_ban_09_201812](https://static.toastoven.net/prod_gamebase/gamebase_ban_09_202101.png)

- **連携有無**：AppGuardで検知または制裁したユーザーを、自動的にGamebase利用停止ユーザーとして登録したい場合に有効にします。
- **自動利用停止**は**即時遮断**、**条件遮断**の2つがあります。
    - **即時遮断**による利用停止は、毎時間15分、45分に行われます。**即時遮断**は検知期間を設定することができず、検知回数は1回に固定されます。
    - **条件遮断**による利用停止は、1日1回0時に実行されます。
        - 例：改ざんの検知期間：5、検知回数：3と設定した場合
            - 1月14日～1月18日の間、特定ユーザーが改ざんによる検知が3回以上検出された場合、1月19日0時に利用停止と登録されます。
- **利用停止タイプ**は、**永久利用停止**、**条件利用停止**の2つがあります。
  - **永久利用停止**は自動利用停止条件に合ったユーザーを永久に利用停止します。
  - **条件利用停止**は、自動利用停止条件に合ったユーザーを設定した期間、利用停止します。
- **リーダーボード連動**項目を選すると、自動利用停止されたユーザーに対して、利用停止時にリーダーボードデータも一緒に削除します。

> [参考]
>
> AppGuard連携で利用停止が自動登録された場合、登録システムには「アプリガード」で登録されます。