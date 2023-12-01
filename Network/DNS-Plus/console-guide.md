## Network > DNS Plus > コンソール使用ガイド

ここではコンソールでDNS Zoneとレコードセットを管理する方法を説明します。

## DNS Zone管理

メニューの**DNS**画面でDNS Zoneを管理できます。

![image_01_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_01_ja_20210628.png)

### DNS Zone作成

1. DNS Zoneはレコードセットを書き込んでいく大枠となるもので、DNSがサービスするホストの経路情報をこの中に定義していきます。**DNS Zone作成**ボタンをクリックして作成します。

2. **DNS Zone名**と**説明**を入力し、**確認**ボタンをクリックします。

    - **DNS Zone名**にユーザーが所有しているドメインまたはサブドメインを[FQDN(fully qualified domain name)](https://en.wikipedia.org/wiki/Fully_qualified_domain_name)で入力します。
    - **DNS Zone名**は、ネームサーバーで唯一のものにする必要があります。ネームサーバーはゾーン作成と同時にNSレコードに登録されます。
    - 同じ**DNS Zone名**は、ネームサーバーの数だけ作成可能です。ネームサーバーはプライマリ、セカンダリがペアで登録され、サービス内では3組のネームサーバーがあります。（ns.toastdns-※※※.com. あるいは　ns.toastdns-※※※.net.というホスト名のネームサーバーで、2台が1組で提供されます。）
    - 作成が完了したら、デフォルトで作成されるNSレコードセットのネームサーバー情報をドメインに設定する必要があります。デフォルトで作成されるレコードセットは[レコードセット管理](./console-guide/#_1)で確認できます。
        - 新規で登録したドメインで作成した場合、ドメイン登録機関にネームサーバー情報を該当ネームサーバーに設定する必要があります。
        - 運営中のドメインのサブドメインで作成した場合、運営中のドメインにNSレコードセットをサブドメイン名と該当ネームサーバーに作成する必要があります。

![image_02_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_02_ja_20210628.png)

### DNS Zone修正

1. 修正するDNS Zoneを選択した後、**DNS Zone修正**ボタンをクリックします。

2. **説明**を修正し、**確認**ボタンをクリックします。

![image_03_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_03_ja_20210628.png)

### DNS Zone削除

1. 削除するDNS Zoneを全て選択した後、**DNS Zone削除**ボタンをクリックします。

2. **確認**ボタンをクリックします。DNS Zone内のすべてのレコードセットも削除され、一定時間がかかります。

![image_04_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_04_ja_20210628.png)


## レコードセット管理

メニューの**DNS**画面で、選択したDNS Zoneのレコードセットを管理できます。

- **DNS Zone名**またはサブネームに対するレコードセットを、レコードセットタイプ別に作成できます。
- **DNS Zone名**のSOAとNSレコードセットはデフォルトで作成され、修正および削除ができません。
- SOAレコードセットは作成/修正/削除できず、NSレコードセットは**DNS Zone名**で作成/修正/削除できません。

![image_05_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_05_ja_20210628.png)

### レコードセット作成

1. レコードセットはサービスされるホスト情報で、**レコードセット作成**ボタンをクリックして作成します。

2. レコードセット情報を入力します。

    - レコードセット名：サービスするホスト名で**DNS Zone名**またはサブネームになるように[FQDN](https://en.wikipedia.org/wiki/Fully_qualified_domain_name)で入力します。
    - レコードセットタイプ：ホストのタイプです。使用目的に応じてタイプを選択します。
    - TTL(秒)：Time to live。データの有効期間を表します。ネームサーバーでレコードセット情報の更新周期を秒単位で入力します。右側のボタンをクリックして簡単に入力できます。

3. レコードセットタイプに応じたレコード情報を入力します。

    - レコードセットタイプによって、異なるレコード値を入力する必要があります。作成画面下に表示される説明に従って入力します。
    - レコードセットタイプに応じて、複数のレコードを入力できます。画面右側の**+**ボタンをクリックするとレコードを追加でき、追加されたレコードの**-**ボタンをクリックするとレコードを削除できます。

4. 設定完了後、**確認**ボタンをクリックします。

5. レコードセットの作成数は制限されています。拡張が必要な場合は別途お問い合わせください。

    - [1:1お問い合わせ](https://www.toast.com/kr/support/inquiry?alias=tab3_02)

![image_06_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_06_ja_20210628.png)

### レコードセット大量作成

1. **レコードセット大量作成**ボタンをクリックします。

2. **テンプレートダウンロード**ボタンをクリックしてダウンロードしたテンプレートにレコードセット情報を入力した後、**ファイル選択**ボタンをクリックしてテンプレートを選択します。

3. テンプレートに入力した情報を画面で確認した後、**確認**ボタンをクリックします。

![image_06_2_ja_20210802](https://static.toastoven.net/prod_dnsplus/image_06_2_ja_20210802.png)

### レコードセット修正

1. 修正するレコードセットを選択した後、**レコードセット修正**ボタンをクリックします。

2. **レコードセット名**は修正できず、**レコードセットタイプ**と**TTL(秒)**、**レコード値**は修正できます。

3. 設定完了後、**確認**ボタンをクリックします。

![image_07_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_07_ja_20210628.png)

### レコードセット削除

1. 削除するレコードセットを全て選択した後、**レコードセット削除**ボタンをクリックします。

2. **確認**ボタンをクリックします。

![image_08_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_08_ja_20210628.png)

### レコードセット統計

1. 確認するレコードセットを選択した後、**レコードセット統計**ボタンをクリックします。

2. レコードセットの直近一週間のクエリー情報と平均レスポンス時間を確認できます。

![image_09_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_09_ja_20210628.png)

### 照会およびリスト表示

1. **タイプフィルタ**を利用して、選択したレコードセットタイプのみ表示できます。

2. 検索語を入力し、**Enter キー**または**検索**をクリックすると、レコードセット名で検索します。

    - 検索語を含むすべての値を検索します。

![image_10_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_10_ja_20210628.png)

## GSLBおよび接続されたPool管理

メニューの**GSLB**画面でGSLBを管理し、選択したGSLBのPool接続を管理できます。

![image_11_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_11_ja_20210628.png)

### GSLBの作成

**GSLBドメイン**は**ルーティングルール**に従って安定的にトラフィックがロードバランシングされます。

1. **GSLB作成**ボタンをクリックして作成します。

2. **GSLB**情報を入力します。

    - GSLBの名前：作成されるGSLBの名前は英字(大文字/小文字)、数字、(-)、(_)で入力可能です。
    - ルーティングルール：GSLBドメインに対するロードバランシング方法にFAILOVER、RANDOM、GEOLOCATIONを選択できます。
        - FAILOVER：接続されたPoolのうち、使用可能なPoolを優先順位でルーティングします。
        - RANDOM：接続されたPoolのうち、使用可能なPoolをランダムに選択してルーティングします。
        - GEOLOCATION：設定された地域のトラフィックを該当の接続されたPoolにルーティングします。地域設定がない場合は優先順位でルーティングします。
    - TTL(秒)：Time to liveでデータの有効期間を表します。GSLBドメインの更新周期を秒単位で入力します。右クリックして簡単に入力できます。
    - 状態：GSLBドメインを有効化するかどうかを選択します。

3. 設定完了後、**確認**ボタンをクリックします。

4. GSLBの作成数は制限されています。拡張が必要な場合は別途お問い合わせください。

    - [1:1お問い合わせ](https://www.toast.com/kr/support/inquiry?alias=tab3_02)

![image_12_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_12_ja_20210628.png)

### GSLBの修正

1. 修正するGSLBを選択した後、**GSLB修正**ボタンをクリックします。

2. **GSLBの名前**と**ルーティングルール**、**TTL(秒)**、**状態**を修正し、**確認**ボタンをクリックします。

![image_13_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_13_ja_20210628.png)

### GSLBの削除

1. 削除するGSLBを全て選択した後、**GSLB削除**ボタンをクリックします。

2. **確認**ボタンをクリックします。

![image_14_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_14_ja_20210628.png)

### Poolの接続

1. GSLBに接続するPoolを設定できます。**Pool接続**ボタンをクリックして接続します。

2. 接続するPoolを選択し、ルーティングルールに従って設定情報を入力します。

    - 優先順位：数字が小さいほどルーティング順序が高くなり、既に接続しているPoolと同じ優先順位を入力した場合、既存Poolのルーティング順序が低くなります。ルーティングルールがFAILOVERまたはGEOLOCATIONの時に設定します。
    - 地域：設定した地域のトラフィックを接続したPoolにルーティングします。ルーティングルールがGEOLOCATIONの時に設定します。
    - 例) GSLBに下記の表のようにPoolが接続されている場合
        - FAILOVERの時はPool-Aにルーティングされます。
        - GEOLOCATIONの時、クライアントがNortheast Asia地域にある場合、Pool-Bにルーティングされます。
        - GEOLOCATIONの時、クライアントがWestern North America地域にある場合、Pool-Cにルーティングされます。
        - GEOLOCATIONの時、クライアントがWestern Europe地域にある場合、設定された地域がないため、優先順位に従ってPool-Aにルーティングされます。

    | Poolの名前 | 優先順位 | 地域 |
    | --- | --- | --- |
    | Pool-A | 1 |  |
    | Pool-B | 2 | Northeast Asia、Southeast Asia |
    | Pool-C | 3 | Western North America |

3. **確認**ボタンをクリックします。

4. Poolの接続数は制限されています。拡張が必要な場合は別途お問い合わせください。

    - [1:1お問い合わせ](https://www.toast.com/kr/support/inquiry?alias=tab3_02)

![image_15_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_15_ja_20210628.png)

### Pool接続の修正

1. 修正するPoolを選択した後、**Pool接続修正**ボタンをクリックします。

2. **Pool**は修正できません。ルーティングルールに従って設定情報を修正できます。

3. **確認**ボタンをクリックします。

![image_16_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_16_ja_20210628.png)

### Pool接続の解除

1. 接続解除するPoolを全て選択した後、**Pool接続解除**ボタンをクリックします。

2. **確認**ボタンをクリックします。

![image_17_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_17_ja_20210628.png)

### 照会およびリスト表示

1. GSLBリストに検索ワードを入力し、**Enter Key**を押すか、**検索**をクリックするとGSLBの名前で検索します。

    - 検索ワードを含むすべての値を検索します。

2. 接続されたPoolリストで検索ワードを入力すると、現在のリスト内でフィルタリングされます。

    - **Poolの名前**、**優先順位**、**地域**項目の中に検索ワードを含むすべてのPoolをフィルタリングして表示します。

3. GSLB状態は下記のルールに従って表示され、接続されたPoolは[Pool](./console-guide/#_8)の状態を表示します。

| GSLB状態 | GSLB有効化/無効化 | Pool状態 |
| --- | --- | --- |
| 正常(緑) | 有効化 | 1個以上が正常状態 |
| エラー(赤) | 有効化 | 正常状態がなく、1個以上がエラー状態 |
| 不明(灰色) | 有効化 | 全て無効または不明な状態、<br>接続されたPoolがない状態 |
| 無効化(灰色) | 無効化 | 無関係 |

![image_18_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_18_ja_20210628.png)

## PoolおよびEndpoint管理

メニューの**GSLB**画面でPoolと、選択したPoolのEndpointを管理できます。

![image_19_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_19_ja_20210628.png)

### Poolの作成

1. エンドポイントをグルーピングする要素で、ルーティングルールが適用される最小単位です。**Pool作成**ボタンをクリックして作成します。

2. **Pool**情報を入力します。

    - Poolの名前：作成されるPoolの名前を英字(大文字/小文字)、数字、(-)、(_)で入力できます。
    - 状態：Poolを有効化するかどうかを選択します。
    - ヘルスチェック：Pool内のエンドポイントのアクセシビリティを確認するヘルスチェックを選択できます。    

3. **エンドポイント**情報を入力します。

    - 複数のエンドポイントを入力できます。画面右の**+**ボタンをクリックしてエンドポイントを追加できます。追加されたエンドポイントの**-**ボタンをクリックしてエンドポイントを削除できます。
    - エンドポイントアドレス：ドメインアドレスまたはIPv4アドレスで入力できます。[予約済のIPアドレス](https://en.wikipedia.org/wiki/Reserved_IP_addresses)は入力できません。Pool内でエンドポイントアドレスは重複して使用できません。
    - 重み：0～1.00で入力できます。Pool内の他のエンドポイントの重みと相対的に動作します。同じ重みはPool内で同じ比重を持ちます。
    - 状態：エンドポイントを有効化するかどうかを選択します。

4. 設定完了後、**確認**ボタンをクリックします。

5. Poolの作成数、Pool内のエンドポイント数、エンドポイントの総数は制限されています。拡張が必要な場合は別途お問い合わせください。

   - [1:1お問い合わせ](https://www.toast.com/kr/support/inquiry?alias=tab3_02)

![image_20_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_20_ja_20210628.png)

### Poolの修正

1. 修正するPoolを選択した後、**Pool修正**ボタンをクリックします。

2. **Poolの名前**と**状態**、**ヘルスチェック**、**エンドポイント**を修正します。

3. 設定完了後、**確認**ボタンをクリックします。

![image_21_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_21_ja_20210628.png)

### Poolの削除

1. 削除するPoolを全て選択した後、**Pool削除**ボタンをクリックします。

2. **確認**ボタンをクリックします。

![image_22_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_22_ja_20210628.png)

### 照会およびリスト表示

1. Poolリストに検索ワードを入力し、**Enter Key**を押すか、**検索**をクリックするとPoolの名前で検索します。 ードを含むすべての値を検索します。

2. エンドポイントリストに検索ワードを入力すると、現在のリスト内でフィルタリングされます。

    - **エンドポイントアドレス**、**重み**項目に検索ワードを含むすべてのエンドポイントをフィルタリングして表示します。

3. Poolの状態は下記のルールに従って表示されます。

| Pool状態 | Pool有効/無効 | ヘルスチェック設定 | エンドポイント状態 |
| --- | --- | --- | --- |
| 正常(緑) | 有効 | 接続 | 1個以上が正常状態 |
| エラー(赤) | 有効 | 接続 | 正常状態がなく、1個以上がエラー状態 |
| 不明(灰色) | 有効 | 接続なし<br>接続の場合はエンドポイントの状態に準ずる | 全て無効または不明な状態 |
| 無効化(灰色) | 無効 | 無関係 | 無関係 |

![image_23_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_23_ja_20210628.png)


## ヘルスチェックの管理

メニューの**GSLB**画面でヘルスチェックを管理できます。

![image_24_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_24_ja_20210628.png)

### ヘルスチェックの作成

1. 設定した値に応じてPool内のエンドポイントに対するアクセシビリティを確認できます。**ヘルスチェック作成**ボタンをクリックして作成します。

2. **ヘルスチェック**情報を入力します。

    - ヘルスチェックの名前：作成するヘルスチェックの名前を英字(大文字/小文字)、数字、(-)、(_)で入力できます。
    - プロトコル：ヘルスチェックを実行する時、使用するプロトコルにHTTPS/HTTP/TCPを選択できます。選択したプロトコルに応じて入力できる情報が異なります。
        - HTTPS入力可能項目：証明書検証しない、ポート、パス、予想ステータスコード、予想レスポンス本文
        - HTTP入力可能項目：ポート、パス、予想ステータスコード、予想レスポンス本文
        - TCP入力可能項目：ポート
    - 証明書検証しない：ヘルスチェックが実行される時、エンドポイントのTLS/SSL証明書が無効でも無視できる設定です。
    - ポート：ヘルスチェックを実行する時に使用するポートを入力します。
    - パス：ヘルスチェックを実行する時に使用するパスを入力します。最初の文字は'/'にする必要があります。
    - 予想ステータスコード：ヘルスチェックに対する予想[HTTP Status Code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)レスポンスを入力します。ワイルドカードに'x'文字を入力できます。一致する場合はエンドポイントを正常と判断します。(例) 2xx, 20x, 200
    - 予想レスポンス本文：ヘルスチェックに対する予想レスポンス本文を入力できます。
    - **予想ステータスコード**と**予想レスポンス本文**を判断する時、エンドポイントからリダイレクトされたページについてはサポートしません。

3. 設定完了後、**確認**ボタンをクリックします。

4. ヘルスチェックの作成数は制限されています。拡張が必要な場合は別途お問い合わせください。

    - [1:1お問い合わせ](https://www.toast.com/kr/support/inquiry?alias=tab3_02)

![image_25_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_25_ja_20210628.png)

### ヘルスチェックの修正

1. 修正するヘルスチェックを選択した後、**ヘルスチェック修正**ボタンをクリックします。

2. **ヘルスチェックの名前**と**プロトコル**、**証明書検証しない**、**ポート**、**パス**、**予想ステータスコード**、**予想レスポンス本文**を修正します。

3. 設定完了後、**確認**ボタンをクリックします。

![image_26_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_26_ja_20210628.png)

### ヘルスチェックの削除

1. 削除するヘルスチェックを全て選択した後、**ヘルスチェック削除**ボタンをクリックします。

2. **確認**ボタンをクリックします。

![image_27_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_27_ja_20210628.png)

### 照会および基本情報

1. ヘルスチェックリストに検索ワードを入力し、**Enter Key**を押すか、**検索**をクリックすると、ヘルスチェックの名前で検索します。

    - 検索ワードを含むすべての値を検索します。

2. ヘルスチェックを選択すると、ヘルスチェックに設定された**基本情報**を確認できます。

![image_28_ja_20210628](https://static.toastoven.net/prod_dnsplus/image_28_ja_20210628.png)