## Network > Peering Gateway > コンソール使用ガイド

コンソールでPeering Gatewayサービスを使用する方法を説明します。

## ピアリング

**ピアリング**は、2つの異なる**VPC**を接続する機能です。通常、VPCはネットワーク領域が異なるため通信ができません。**Floating IP**を利用して接続できますが、ネットワーク使用量に応じて追加費用を支払う必要があります。しかし、ピアリング機能を使えば追加費用を支払わずに2つの**VPC**を接続できます。

* ピアリングは、2つの異なるVPCを接続します。VPCを経由してまた別のVPCへの接続はサポートしません。 `A <-> B <-> C`接続で`A`と`C`は接続できません。
* ピアVPCを経由して別のVPCに接続したい場合は、ピアリングで提供される**ルート**設定を利用してVMインスタンスを経由してパケットが転送されるように設定する必要があります。
  > [参考]ルートの使い方は、以下の「共通機能 > ルート」の内容を参照してください。 
* 2つのVPCのIPアドレス領域が重なる場合は使用できません。<br>
  IPアドレス領域の一方がもう一方と包含関係にならないようにしてください。その場合、ピアリングの作成に失敗します。
* 韓国リージョンを除く他のリージョンでは**基本ルーティングテーブル**に接続されていないサブネットでは通信ができません。
    * 韓国リージョンはピアリングを作成した後、ピアリングした両方のVPCのルーティングテーブルに別途のルートを設定すると通信が可能です。
        * ルートの**対象CIDR**に相手VPCのIPアドレス領域を入力し、ゲートウェイリストでピアリングの名前を持つ**PEERING**項目を選択してルートを追加します。
        * ルートを追加したルーティングテーブルに接続されたサブネットでのみ通信が可能です。
        * 基本ルーティングテーブルではないルーティングテーブルもルートを追加するとルーティングテーブルに接続されたサブネットで通信が可能です。
        * ピアリング作成時、サブネットがないVPCを指定するとピアリングは作成に失敗します。

## リージョンピアリング

**リージョンピアリング**は異なるリージョンに作成された2つの**VPC**を接続する機能です。同じリージョンのVPCはピアリングを利用して接続できますが、リージョンが異なるVPCを接続することはできません。しかし、リージョンピアリングを利用するとリージョンが異なる2つのVPCを接続できます。

* リージョンピアリングは、2つの異なるリージョンVPCを接続します。別のVPCを経由してまた別のVPCへの接続はサポートしません。例えば`A <-> B <-> C`接続で`A`と`C`は接続できません。
* ピアVPCを経由して別のVPCに接続したい場合は、ピアリングで提供される**ルート**設定を利用してVMインスタンスを経由してパケットが転送されるように設定する必要があります。
  > [参考]ルートの使い方は、以下の「共通機能 > ルート」の内容を参照してください。 
* リージョンピアリングは韓国(ピョンチョン)リージョンと韓国(パンギョ)リージョンのVPCでのみ利用できます。
* 同じアカウント、同じプロジェクトの2つのVPCのみ接続できます。
* リージョンピアリングを作成すると、接続された他のリージョンで自動的に作成されます。
* リージョンピアリングを削除すると、接続された他のリージョンで自動的に削除されます。
* 2つのVPCのIPアドレス領域が重なる場合は使用できません。
* 重複したVPC接続は作成できません。
* ピアリングされた両方のVPCの**ルーティングテーブル**に別の**ルート**を設定すると通信が可能です。
    * ルートの**対象CIDR**に相手VPCのIPアドレス領域を入力し、ゲートウェイリストでリージョンピアリングの名前を持つ**INTER_REGION_PEERING**項目を選択してルートを追加します。
    * ルートを追加したルーティングテーブルに接続されたサブネットでのみ通信が可能です。
    * 基本ルーティングテーブルではないルーティングテーブルにルートを追加すると、ルーティングテーブルに接続されたサブネットでピアリング通信が可能です。
    * リージョンピアリング作成時、サブネットがないVPCを指定すると、リージョンピアリングは作成に失敗します。

### リージョンピアリングの作成

1. **Network > Peering Gateway > リージョンピアリング**に移動します。
2. **リージョンピアリング作成**ボタンをクリックします。
3. **名前**、**ローカルVPC**、**ピアリージョン**、**ピアVPC ID**を入力します。</br>
   > [参考]ピアVPC ID<br>
   > **ピアVPC ID**の確認方法は、以下の「ピアリージョンのVPC ID確認」内容を参照してください。 

### ピアリージョンのVPC IDを確認

リージョンピアリングを作成するには、他のリージョンでピアリング対象となるVPCの**VPC ID**を知る必要があります。ピアリージョンのVPC IDを確認する方法は次のとおりです。

1. ピアリージョンのコンソール画面に接続します。
2. **Network > VPC > 管理**に移動します。
3. ピアリング対象VPCを選択します。
4. **基本情報 > VPC名**に表示されているUUID値をコピーします。

## プロジェクトピアリング

**プロジェクトピアリング**は、異なるプロジェクトに作成された2つの**VPC**を接続する機能です。同じプロジェクトのVPCはピアリングを利用して接続できますが、プロジェクトが異なるVPCを接続することはできません。しかし、プロジェクトピアリング機能を利用するとプロジェクトが異なる2つのVPCを接続できます。

* プロジェクトピアリングは、2つの異なるプロジェクトのVPCを接続します。別のVPCを経由してまた別のVPCへの接続はサポートしません。例えば`A <-> B <-> C`接続で`A`と`C`は接続できません。
* ピアVPCを経由して別のVPCに接続したい場合は、ピアリングで提供される**ルート**設定を利用してVMインスタンスを経由してパケットが転送されるように設定する必要があります。
  > [参考]ルートの使い方は、以下の「共通機能 > ルート」の内容を参照してください。 
* プロジェクト間ピアリングは、韓国(ピョンチョン)リージョンと韓国(パンギョ)リージョンのVPCでのみ利用できます。
* 同じリージョンで異なるプロジェクトの2つのVPCのみ接続が可能です。
* プロジェクトピアリングを作成すると、接続された別のプロジェクトで自動的に作成されます。
* プロジェクトピアリングを削除すると、接続された別のプロジェクトで自動的に削除されます。
* 2つのVPCのIPアドレス領域が重なる場合は使用できません。
* 重複したVPC接続は作成できません。
* ピアリングされた両方のVPCの**ルーティングテーブル**に別の**ルート**を設定すると通信が可能です。
    * ルートの**対象CIDR**に相手VPCのIPアドレス領域を入力し、ゲートウェイリストからプロジェクトピアリングの名前を持つ**INTER_PROJECT_PEERING**項目を選択してルートを追加します。
        * ルートを追加したルーティングテーブルに接続されたサブネットでのみ通信が可能です。
    * 基本ルーティングテーブルではないルーティングテーブルにルートを追加すると、ルーティングテーブルに接続されたサブネットでピアリング通信が可能です。
    * プロジェクトピアリング作成時、サブネットがないVPCを指定するとプロジェクトピアリングは作成に失敗します。

### プロジェクトピアリングの作成

**プロジェクトピアリング**を作成するにはピアプロジェクトの**プロジェクトピアリング許可**に自分のプロジェクトの**テナントID**と**VPC ID**が許可されている必要があります。
プロジェクトピアリングを作成する前にピアプロジェクトの管理者に**テナントID**と**VPC ID**を伝え、**プロジェクトピアリング許可**に情報登録をリクエストする必要があります。
ピアプロジェクトで情報登録が完了したら、次の手順でプロジェクトピアリングを作成できます。

> [参考]プロジェクトピアリングを許可する方法は以下の「プロジェクトピアリング許可」内容を参照してください。 

1. **Network > Peering Gateway > プロジェクトピアリング**に移動します。
2. **プロジェクト間ピアリング作成**ボタンをクリックします。
3. **名前**、**ローカルVPC**、**ピアリージョン**、**ピアテナントID**、**ピアVPC ID**を入力します。</br>
   > [参考]ピアテナントID、ピアVPC ID <br>
   > ピアテナントIDとピアVPC IDの確認方法は、以下の「ピアプロジェクトのピアテナントID確認」内容を参照してください。

### プロジェクトピアリングを許可

**プロジェクトピアリング**リクエストを受ける側で設定します。リクエストを送る相手の**テナントID**と**VPC ID**を入力してピアが送るプロジェクトピアリングリクエストを受け入れられるようにします。

1. **Network > Peering Gateway > プロジェクトピアリング**に移動します。
2. **プロジェクトピアリング許可**ボタンをクリックします。
3. **名前**、**ピアテナントID**、**ピアVPC**を入力し、確認ボタンをクリックします。

### ピアプロジェクトのVPC IDの確認

**プロジェクトピアリング**を作成するには、ピアプロジェクトでピアリング対象となるVPCの**VPC ID**を知る必要があります。次の手順でピアプロジェクトの**VPC ID**を確認できます。

> [参考]ピアプロジェクトにアクセス権限がない場合はピアプロジェクトの管理者にVPC IDを教えてもらってください。

1. ピアプロジェクトのコンソール画面に接続
2. **Network > VPC > 管理**に移動
3. ピアリング対象VPCを選択
4. **基本情報 > VPC名**に表示されているUUID値をコピー

### ピアプロジェクトのテナントIDを確認

**プロジェクトピアリング**を作成するには、ピアプロジェクトで**テナントID**を知る必要があります。次の手順でピアプロジェクトの**テナントID**を確認できます。

> [参考]ピアプロジェクトにアクセス権限がない場合はピアプロジェクトの管理者にテナントIDを提供教えてもらってください。

1. ピアプロジェクトのコンソール画面に接続
2. **Network > VPC > 管理**に移動
3. ピアリング対象または画面に表示されるVPCのいずれか1つを選択
4. **基本情報 > テナントID**に表示されているID値をコピー

## 共通機能

ピアリング(ピアリング、リージョンピアリング、プロジェクトピアリング)で提供される共通機能を説明します。 

### ルート

ピアリングで提供する**ルート**設定を利用すると、ピアVPCのVMインスタンスを経由して他のVPCにトラフィックを転送するように構成できます。ピアリングのルートはピアリングから流入したすべてのトラフィックを処理するVMインスタンスのポートおよび仮想IPポートを指定して設定できます。ルートのゲートウェイとなるVMインスタンスにはNetwork Virtual Appliance VMをバッチしてVMインスタンス内部でトラフィックを制御し、他のピアリングにトラフィックを転送できます。
* ピアリングでハブ&スポーク(Hub & Spoke)形式のVPC接続を構成し、ハブVPCにあるNetwork Virtual Applianceですべてのトラフィックを制御したい構成はピアリングのルーティング機能を活用して構成できます。

> [参考]現在は韓国(ピョンチョン)、韓国(パンギョ)リージョンでのみ機能が提供されます。
#### ルート作成

1. ルート設定を行いたいピアリングを選択
2. 下部タブでルートを選択
3. **ルート作成**を選択
4. ピアリングの場合、**ゲートウェイ区分**を選択(プロジェクトピアリング、リージョンピアリングは項目がありません)
   > [参考] **ピアゲートウェイ**はピアリング作成時に選択した**ピアVPC**にルートを追加することを意味し、**ローカルゲートウェイ**は**ローカルVPC**の場所を意味します。<br>
5. ゲートウェイを選択したら、OKボタンをクリックします。
   > [参考]ゲートウェイはインスタンスと仮想IPのみ選択できます。<br>
#### ルートの削除

1. ルート設定を削除したいピアリングを選択
2. ルートを選択
3. **ルート削除**ボタンをクリックします。
