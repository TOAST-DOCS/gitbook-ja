## Dooray! > Project > サービス連動ガイド

### サービス連動 
Doorayでは外部サービスとの連動のため、Doorayプロジェクトのイベントを外部サービスに知らせる発信フック(Outgoing Hook)だけでなく、外部の様々なサービスをDoorayに連動できる着信フック(Incoming Hook)も提供しています。着信フックは、よく使用する開発、配布、ソース管理、パフォーマンス管理ツールをDoorayに連動させ、外部サービスの様々な変更事項をDoorayプロジェクトまたはDoorayメッセンジャーのチャットルームに通知させる方法です。 Doorayでは、Jenkins、GitHub、Gitlab、Trello、NewRelic、JIRA、Bitbucket、IFTT、Grafanaにおいて、着信フックをサポートしています。
着信フックを行うには、Dooray「設定 > サービス連動 > サービス追加」から連動するサービスを選択します。 つまり、該当サービスの通知をDoorayで受け取るという意味で、連動URLは各サービスのWebフック設定画面から追加が必要です。 以下はGitHubプロジェクトでPushイベントが発生するとき、Doorayプロジェクトのタスクとして登録させる方法です。

#### GitHub連動
Dooray「設定 > サービス連動 > サービス追加」から「GitHub」を選択して、「連動追加」ボタンをクリックします。 GitHubのイベント発生時に連動させるDoorayサービスを選択します。Doorayプロジェクトの中から希望のプロジェクトを選択すると、GitHubのイベントを選択したプロジェクトのコメントで受信できます。連動チャットを選択すると、イベントを対象のチャットルームでメッセージとして受け取ることができます。

Bot名を入力して、連動URLをコピーした後、連動させるプロジェクトを選択して保存します。 

![연동](http://static.toastoven.net/prod_dooray_project/01_project_integration_jp.png)
<center>[図1] Doorayサービス連動設定</center>

Bot連動URLをコピーしたら、連動したいサービスにWebフックをかけましょう。GitHubの設定ページに移動します。Webhooks & servicesメニューをクリックしてWebフックを追加します。

![연동](http://static.toastoven.net/prod_dooray_project/02_project_integration_jp.png)
<center>[図2] GitHub設定</center>

Payload URLにコピーしたDoorayの連動URLを入力して保存します。

![연동](http://static.toastoven.net/prod_dooray_project/03_project_integration_jp.png)
<center>[図3] Webフック追加</center>

これでGitHubにコミットをプッシュするとき、コミットメッセージに「fix#my-dooray-project/1234」というフレーズがあれば、「#my-dooray-project/123」のタスクにプッシュ通知がコメントとして登録されます。プルリクエストをつけてマージすれば、対象のタスクは通知コメントと一緒に自動で完了します。

#### GitLab連動
Dooray「設定 > サービス連動 > サービス追加」から「GitLab」を選択して、「連動追加」ボタンをクリックします。GitLabのイベント発生時に連動させるDoorayサービスを選択します。

![연동](http://static.toastoven.net/prod_dooray_project/04_project_integration_jp.png)
<center>[図4] Doorayサービス連動設定</center>

GitLab Settings > IntegrationページにコピーしたDoorayの連動URLを入力し、トリガーを選択します。 トリガーはチェックボックスでチェックしたものが連動されます。連動するトリガーを選択して、Add webhookボタンをクリックします。 

![연동](http://static.toastoven.net/prod_dooray_project/05_project_integration_jp.png)
<center>[図5] Webフック追加</center>

コミットをプッシュするとき、メッセージに「fix#my-dooray-project/1234」というフレーズを入力すると、「my-dooray-projec」プロジェクトの「1234」のタスクにプッシュ通知がコメントとして登録されます。プルリクエストをつけてマージすれば、対象のタスクは通知コメントと一緒に自動で完了します。

コミット時、「fix」以外にも次のような単語を使用すると、自動コメント、完了処理が有効になります。
- fix, fixes, fixed
- close, closes, closed
- resolve, resolves, resolved
- 解決、完了
