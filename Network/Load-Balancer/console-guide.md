## Network > Load Balancer > コンソール使用ガイド

## ロードバランサー管理

### ロードバランサー作成
NHN Cloudのロードバランサーコンソールで設定値を入力するだけで、簡単にロードバランサーを作成できます。

#### ロードバランサー情報
ロードバランサーの基本情報を入力します。必要な項目は次のとおりです。

* 名前：ロードバランサーの名前を入力します。
* 説明：ロードバランサーの説明を記述します。
* VPC、サブネット：ロードバランサーが接続されるVPCのサブネットを指定します。
* ロードバランシング方式：一般、専用、物理Basic、物理Premiumのいずれかを選択することができます。
* サブネット静的ルート：ロードバランサーが位置するサブネットの静的ルート設定をロードバランサーに適用するかどうかを選択します。

#### リスナー登録

ロードバランサーが処理するトラフィックの属性を定義します。NHN Cloudのロードバランサーは基本的に1つのリスナーを持ち、今後ロードバランサーの詳細画面で追加作成や削除を行えるようになります。

* ロードバランシング方式：ロードバランサーがトラフィックを分散する方式を決定します。 ROUND_ROBIN/LEAST_CONNECTIONS/SOURCE_IPの中から1つを選択します。
* プロトコル：ロードバランサーが処理するトラフィックのプロトコルを指定します。 TCP/HTTP/HTTPS/TERMINATED_HTTPSの中から1つを選択します。
* ロードバランサーポート：基本リスナーがトラフィックを受信するポートを指定します。
* インスタンスポート：ロードバランサーのメンバーのポートを指定します。ロードバランサーポートに流入するトラフィックは、メンバーインスタンスのインスタンスポートに伝達されます。

> [参考]ロードバランサーポートとインスタンスポートは、1から65535の間の値を持ちます。

> [注意]ロードバランサーポート、インスタンスポート、そしてプロトコルはリスナー作成後の変更ができません。

* SSL証明書：プロトコルにTERMINATED_HTTPSを選択する場合、使用する証明書を登録します。プロトコルにTERMINATED_HTTPSを選択した時のみ活性化します。

> [参考] TERMINATED_HTTPS証明書の登録方法
>
> ロードバランサーのリスナープロトコルをTERMINATED_HTTPSに指定した場合、SSL証明書を登録するボタンが有効になります。
>
> 登録する必要があるファイルは、‘証明書’と‘秘密鍵’です。‘秘密鍵’はサーバー証明書に含まれている公開鍵のペアになる秘密鍵を意味します。
>
> ‘証明書’は下記のようにx.509 PEM形式に従います。
>
>     -----BEGIN CERTIFICATE-----
>     (内容省略)
>     -----END CERTIFICATE-----
>
>
> サーバー証明書と中間証明書(Chain Certificate, Intermediate Certificate)を一緒に登録する必要がある時は、サーバー証明書と中間証明書を1つのファイルで作って登録する必要があります。
>
> 証明書ファイルを1つで作る時は、ファイルの最上段にサーバー証明書を記述し、その下に中間証明書を記述する必要があります。中間証明書は順序に関係なく記述できます。
>
>サーバー証明書1個と中間証明書2個を1つの証明書ファイルで作ると次のような形式になります。
>
>
>      -----BEGIN CERTIFICATE-----
>      (サーバー証明書の内容省略)
>      -----END CERTIFICATE-----
>      -----BEGIN CERTIFICATE-----
>      (中間証明書#1内容省略)
>      -----END CERTIFICATE-----
>      -----BEGIN CERTIFICATE-----
>      (中間証明書#2内容省略)
>      -----END CERTIFICATE-----
>
>
>
> ‘秘密鍵’は、サーバー証明書に含まれている公開鍵に対応する鍵ファイルです。
>
> PKCS#1またはPKCS#8 PEM形式のファイルを登録できます。
>
>
>
>      -----BEGIN RSA PRIVATE KEY-----
>      (秘密鍵の内容省略)
>      -----END RSA PRIVATE KEY-----
>
>または
>
>      -----BEGIN PRIVATE KEY-----
>      (秘密鍵の内容省略)
>      -----END PRIVATE KEY-----

##### Certificate Manager使用
リスナーでTERMINATED_HTTPSプロトコルを使用する場合、証明書の登録はCertificate Managerに登録した証明書を使用する方法と、直接登録する方法の2つがあります。

* Certificate Managerサービスに証明書を登録し、リスナーに証明書を接続すると、証明書の有効期限のアラームをメールで受信できます。
* リスナーに直接証明書を登録した場合は、証明書の有効期限のアラームがありません。(コンソールのリスナー画面で有効期限を確認できます)
> [注意事項]
> Certificate Managerサービスで証明書を更新した場合、影響を受けるリスナーの証明書も更新する必要があります。
> Certificate Managerに登録した証明書をリスナーに使用するには、「秘密鍵」のパスワードが除去されている必要があります。そしてPKCS#1またはPKCS#8 PEM形式にする必要があります。

##### ヘルスチェック

ヘルスチェックのための設定もリスナー作成時に決定します。 NHN Cloudのロードバランサーはリスナーごとにヘルスチェック動作を定義できます。必要な項目は次のとおりです。

* ヘルスチェックプロトコル：ヘルスチェック時に使用するプロトコルを決定します。TCP/HTTP/HTTPSの中から1つを選択します。
* ヘルスチェックポート：ヘルスチェックを行うメンバーインスタンスのポートを決定します。
* HTTPメソッド：ヘルスチェック時に使用するHTTPメソッドを選択します。ヘルスチェックプロトコルでHTTPまたはHTTPSを選択した時のみ活性化します。現在はGETのみをサポートしています。
* HTTP状態コード：ヘルスチェック時に正常レスポンスとみなすHTTP状態コードを入力します。ヘルスチェックプロトコルにHTTPまたはHTTPSを選択した時のみ活性化します。現在はGETのみをサポートしています。
* URL：ヘルスチェックを行うメンバーインスタンスのパスを指定します。ヘルスチェックプロトコルでHTTPまたはHTTPSを選択した時のみ活性化します。
* ヘルスチェックの周期：ヘルスチェックを行う周期を入力します。単位は秒で、指定された周期ごとにヘルスチェックを行います。
* 最大レスポンス待機時間：ヘルスチェック後、正常レスポンスを待機する最大時間を指定します。単位は秒で、指定された待機時間を超えると失敗とみなします。ヘルスチェック
* 最大再試行回数：ヘルスチェック時に繰り返し試行する最大回数を指定します。最大再試行回数が2以上の場合、ヘルスチェックに対する正常レスポンスがなかったからといって、すぐに失敗とはみなしません。失敗した回数が最大再試行回数に達した場合、そのインスタンスを負荷分散対象から除外します。
* ホストヘッダ：ヘルスチェック時にホストヘッダで使用するフィールド値を入力します。ヘルスチェックプロトコルにHTTPまたはHTTPSを選択したときのみ有効になります。

最後に接続に関する設定を指定します。

* セッション持続性：セッションを維持するため、リクエストに対するレスポンスを特定インスタンスでのみ行うように作成する設定です。 No Session Persistence/ APP_COOKIE/ HTTP_COOKIE/ SOURCE_IPの中から1つを選択できます。
* 接続制限：基本リスナーが同時に維持するTCP接続の数を指定します。値を入力していない場合、基本値の2000に設定されます。
* Keepalive  タイムアウト：クライアント及びサーバーとのセッション維持時間を秒単位で指定します。ロードバランサーは、相手側がセッションを維持する限り、この時間の間はセッションを維持します。インスタンスに設定したkeepalive timeoutの値をここに設定することを推奨します。基本値は300秒に設定されます。
* プロキシプロトコル：ロードバランサーがプロキシプロトコルをサポートするようにできます。インスタンスでクライアントのIPを知るためにプロキシプロトコルを使用するように設定した場合にのみ、この値を有効にする必要があります。TCPとHTTPSプロトコルを使用する場合にのみ利用できます。


#### メンバー登録
ロードバランサー作成時、メンバーに登録するインスタンスを指定します。メンバー登録はロードバランサー作成後に行ってもかまいません。ロードバランサーが接続されたVPCに属するインスタンスと、そのVPCとピアリング接続したVPCに属するインスタンスをメンバーに登録できます。
ただし、ロードバランサーとサブネットが他のインスタンスをメンバーに登録するにはルーティングテーブルに2つのサブネットを登録する必要があります。 

#### IPアクセス制御グループ
ロードバランサー作成時に適用するIPアクセス制御グループを指定します。 IPアクセス制御グループの中から、同じアクセス制御タイプを持つ複数のグループを選択できます。ロードバランサー作成後も、適用するIPアクセス制御グループを変更できます。

### ロードバランサーの詳細確認
ロードバランサーの作成を終えたら、再びロードバランサーリスト画面に戻ります。ロードバランサーリスト画面では作成されたロードバランサーの基本情報を確認できます。リスト画面に表示される項目は次のとおりです。

* 名前：ロードバランサー作成時に指定したロードバランサーの名前です。
* タイプ：ロードバランサーのタイプです。
* IPアドレス：ロードバランサーに接続されたVPCから割り当てられたプライベートIPです。 VPC内部ではこのIPを通してロードバランサーにアクセスできます。VPCの外部からロードバランサーにアクセスするためにはFloating IPを接続する必要があります。
* ロードバランサーポート/インスタンスポート：ロードバランサーに属するリスナーのポートとインスタンスポートのペアです。
* プロトコル：ロードバランサーに属するリスナーのプロトコルです。
* IPアクセス制御タイプ：ロードバランサーに指定されたIPアクセス制御グループのタイプを表します。アクセス制御グループが指定されていない場合は何も表示されず、指定されている場合は'許可'または'遮断'のどちらかのタイプを持ちます。
* ネットワーク：ロードバランサーに接続されたVPCの名前とサブネットCIDRです。
* 状態：ロードバランサーの作成状態を表します。ACTIVEと表示されていれば正常に作成されたということです。

> [参考]ロードバランサーの作成状態は次の中から1つが決定されます。

> | 状態 | 意味 |
> |--|--|
> | ACTIVE | ロードバランサー作成完了、正常動作中 |
> | PENDING_CREATE | ロードバランサー作成中 |
> | PENDING_UPDATE | ロードバランサーの設定修正中<br> 設定修正後、1時間以内にACTIVE状態に変わらない場合は、管理者にお問い合わせください。|
> | PENDING_DELETE | ロードバランサー削除中<br> 削除後、1時間以内にリストから消えない場合は、管理者にお問い合わせください。|
> | ERROR | ロードバランサー作成失敗 <br> 管理者にお問い合わせください。 |
> | ERROR_MIGRATE | ロードバランサー移行失敗<br> 管理者にお問い合わせください。 |


### ロードバランサーの修正および詳細情報
ロードバランサーリスト画面でロードバランサーを選択すると、画面下段に選択したロードバランサーの詳細画面が表示されます。詳細画面は3つのタブで区分されます。各々のタブの説明は次のとおりです。

* ロードバランサー詳細情報：選択したロードバランサーの詳細情報が表示されます。選択したロードバランサーの名前と説明、サブネット静的ルートを適用するかどうかを変更できます。
* リスナー：選択したロードバランサーに作成されたリスナーの詳細設定を確認できます。リスナーの新規追加や、既存リスナーの削除を行えます。
* インスタンス：選択したロードバランサーのメンバーに登録されたインスタンスリストを確認できます。新たなインスタンスをメンバーに登録したり、既存メンバーを除外したりできます。
* 統計：選択したロードバランサーの統計情報を確認できます。

> [参考]ロードバランサーが接続されたVPCとIPアドレスは変更できません。

#### リスナーの追加
ロードバランサーの詳細画面でリスナータブを選択した後、リスナー追加ボタンを押すと、リスナーを追加できます。リスナー追加に必要な項目は、ロードバランサー作成時に基本リスナーで必要な項目と同じです。リスナー追加時、既に存在していたリスナーが使用していたロードバランサーポートは使用できません。

#### リスナーの修正
修正したいリスナーの修正ボタンを押すと、リスナーの設定を修正できます。

> [参考]リスナーのプロトコル、ロードバランサーポートそしてインスタンスポートは変更できません。

#### リスナーの削除
削除したいリスナーの削除ボタンを押すと、そのリスナーは削除されます。ただし、選択したロードバランサーにリスナーが1つしか存在しない場合は削除できません。

> [注意]リスナーの追加/修正/削除時にロードバランサーが再起動します。再起動する過程で接続済みのセッションは維持されますが、新しいセッションは処理できません(約1秒未満)。したがって、サービスに影響を与えない時間に進行することを推奨します。

#### メンバーの追加
インスタンスタブで新しいインスタンスをロードバランサーのメンバーに登録できます。追加できるインスタンスは、ロードバランサーが接続されたVPCに属するインスタンスと、そのVPCとピアリング接続されたVPCに属するインスタンスです。

#### メンバーの無効化
メンバーインスタンスの特定インスタンスを一時的にサービスから除外できます。除外するインスタンスを選択し、`インスタンス無効化`ボタンをクリックして`確認`をクリックします。
除外されたインスタンスの使用項目は**False**、メンバーインスタンスの状態は**ONLINE**に変更されます。

> [参考]メンバーインスタンスの状態は次のいずれか1つに決定されます。
> 
> | 状態 | 意味 |
> |--|--|
> | ACTIVE | メンバーインスタンス接続完了、正常動作中 |
> | INACTIVE | メンバーインスタンスのヘルスチェックが行われていない状態 |
> | ONLINE | メンバーインスタンスが無効化になっている状態|
> | OFFLINE | メンバーインスタンス接続失敗 <br> 管理者にお問い合わせください。|

#### メンバーの削除
メンバーインスタンスのうち、今後使用しないインスタンスは削除できます。除外するインスタンスのインスタンス接続解除ボタンを押すと、選択したロードバランサーのメンバーから削除されます。ロードバランサーのメンバーから削除されても、インスタンスは削除されません。

> [注意]メンバーの追加/無効化/削除時にロードバランサーが再起動します。再起動する過程で接続済みのセッションは維持されますが、新しいセッションは処理できません(約1秒未満)。したがって、サービスに影響を与えない時間に進行することを推奨します。

### ロードバランサーの削除
ロードバランサーのリスト画面で、削除したいロードバランサーを選択した後に削除ボタンを押すと、そのロードバランサーが削除されます。

## IPアクセス制御グループ
IPアクセス制御機能の詳細は、[IPアクセス制御](/Network/Load%20Balancer/ja/overview/#ip)を参照してください。

#### IPアクセス制御グループの作成
IPアクセス制御グループを作成するために、アクセス制御グループ作成ボタンを押し、次の値を入力します。

* 名前：アクセス制御グループの名前を入力します。
* 説明：アクセス制御グループの説明を入力します。
* IPアクセス制御タイプ：遮断または許可のどちらかを選択します。
* IPアクセス制御対象の追加：アクセス制御対象になるIPと説明を入力します。右にある"+"ボタンを押し、複数のアクセス制御対象を一度に追加できます。多くの対象を簡単に入力するには、"大量入力"を選択します。この場合、1行に"IPアドレスまたはCIDR"と"説明"を入力します。一度に最大100個のアクセス制御対象を入力できます。


確認を押すと、アクセス制御グループと対象が作成されます。

> [参考] IPアクセス制御グループとIPアクセス制御対象の数
> 
> プロジェクトごとにアクセス制御グループを最大10個まで作成できます。
> プロジェクトごとにアクセス制御対象を最大1,000個まで作成できます。


#### IPアクセス制御グループの変更
IPアクセス制御グループのプロパティを変更できます。変更可能なプロパティは名前と説明です。"IPアクセス制御タイプ"プロパティは変更できません。

#### IPアクセス制御グループの削除
選択したIPアクセス制御グループを削除できます。グループを削除すると、グループに属するすべてのアクセス制御対象も削除されます。
IPアクセス制御グループを削除すると、このグループを使用するロードバランサーが該当ポリシーを使用しなくなります。

#### IPアクセス制御対象の追加
アクセス制御グループを選択すると、下部にアクセス制御対象メニューが表示されます。
アクセス制御グループに対象を追加すると、このアクセス制御グループを使用するすべてのロードバランサーに追加されたIPまたはCIDRにポリシーが反映されます。

#### IPアクセス制御対象の変更
アクセス制御対象のプロパティを変更できます。説明のみ変更できます。

#### IPアクセス制御対象の削除
アクセス制御グループを選択すると、下部にアクセス制御対象メニューが表示されます。
アクセス制御グループに属する対象を削除すると、このアクセス制御グループを使用するすべてのロードバランサーに、該当IPまたはCIDRのポリシーが削除されます。

#### IPアクセス制御グループの適用
IPアクセス制御グループを適用するロードバランサーを選択します。該当ロードバランサーに設定するグループを選択し、確認を押します。
"アクセス制御タイプ"が同じ複数のグループをロードバランサーに適用できます。

## 機器のメンテナンスのためのロードバランサー再起動ガイド

NHN Cloudは周期的にロードバランサーのソフトウェアをアップデートして、基本インフラサービスのセキュリティと安定性を向上させています。ロードバランサーのメンテナンスのためにメンテナンス対象機器で起動中のロードバランサーは再起動を行い、メンテナンスが完了したロードバランサーに移動する必要があります。

再起動が必要なロードバランサーは名前の横に**!再起動**ボタンが表示され、このボタンを使用して再起動できます。

メンテナンス対象に指定されたロードバランサーがあるプロジェクトに移動して、次の手順で再起動を行います。

1. メンテナンス対象ロードバランサーを確認します。
  ロードバランサー名の横に**!再起動**ボタンがあるロードバランサーが、メンテナンス対象のロードバランサーです。
   ![image-001](http://static.toastoven.net/prod_load_balancer/lb_p_migration_jp_1.png)
    **!再起動**ボタンにマウスオーバーすると、詳しいメンテナンス日程を確認できます。サービスに影響を与えない時間に実行してください。
   ![image-002](http://static.toastoven.net/prod_load_balancer/lb_p_migration_jp_2.png)
2. メンテナンス対象ロードバランサーを選択し、名前の横にある**!再起動**ボタンをクリックします。
3. ロードバランサーの再起動を確認するウィンドウが表示されたら、**確認**ボタンをクリックします。
   ![image-003](http://static.toastoven.net/prod_load_balancer/lb_p_migration_jp_3.png)
4. 状態表示灯が緑色に変わり、**!再起動**ボタンが消えるまで待機します。
  ロードバランサーの状態表示灯が変わらなかったり、**!再起動**ボタンが消えない場合は、「更新」を実行してみてください。
   ![image-004](http://static.toastoven.net/prod_load_balancer/lb_p_migration_jp_4.png)

ロードバランサーの再起動中は、該当ロードバランサーで何も操作ができません。
ロードバランサーの再起動が正常に完了しない場合は、自動的に管理者に報告され、NHN Cloudから別途連絡いたします。

## 物理ロードバランサーと一般ロードバランサーの違い
2021年4月、オンラインでリリースされる物理ロードバランサーと、既存ロードバランサーサービス(一般/専用)の違いは次の通りです。

* 物理ロードバランサーは韓国坪村リージョンでのみ提供されます。
* 物理ロードバランサーにはFloating IPを接続できません。物理ロードバランサーの作成時、自動的に割り当てられた1つのパブリックIPをバランシング対象トラフィックを受信するIPに使用します。このパブリックIPはサービスIPという名前でWebコンソールに表示されます。
* サブネットに使用されていない連続したIPが17個存在する時のみ、物理Basicロードバランサーを作成できます。この17個のIPは物理ロードバランサーに割り当てられ、予約IPという名前でWebコンソールに表示されます。
* サブネットに使用されていない連続したIPが50個存在する時のみ、物理Premiumロードバランサーを作成できます。この50個のIPは物理ロードバランサーに割り当てられ、予約IPという名前でWebコンソールに表示されます。
* 物理ロードバランサーはロードバランサープロキシプロトコル機能を提供しません。
* 物理ロードバランサーはロードバランサー統計機能を提供しません。
* 物理ロードバランサーはロードバランサーIPアクセス制御機能を提供しません。