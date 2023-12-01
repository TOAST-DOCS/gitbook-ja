## Compute > Instance > 概要

インスタンスは仮想のCPU、メモリ、ルートブロックストレージで構成された仮想サーバーです。このサーバーに顧客のサービスやアプリケーションをインストールしてNHN Cloudが提供する様々なサービスを組み合わせて使用します。

## インスタンス構成要素

インスタンスを構成する要素は次のとおりです。

- **イメージ**：インスタンスのオペレーションシステムを含む仮想ディスク
- **インスタンスタイプ**(flavor)：インスタンスの仮想ハードウェアの性能、仕様
- **アベイラビリティゾーン**(AZ、availability zone)：インスタンスが生成されるハードウェアの物理的な設置区分
- **キーペア**(key-pair)：インスタンスへの接続手段として使われるSSHキー
- **セキュリティグループ**(security group)：インスタンスのネットワークセキュリティ設定、アクセス制御を行う
- **ネットワーク**：インスタンスが接続する仮想ネットワーク

この情報に基づいてインスタンスの属性と使用方式が変わります。この情報のうち、イメージとアベイラビリティゾーンを除く設定はインスタンス生成後も変更できますが、一部のインスタンスの仕様(flavor)はインスタンス生成後に変更できません。インスタンス仕様変更については[コンソール使用ガイドのインスタンスタイプ変更](./console-guide/#_15)を参照してください。

### イメージ

イメージはオペレーションシステムを含む仮想ディスクです。NHN Cloudは現在CentOS、Debian、Ubuntu、Rocky、Windowsをサポートしています。サポートしているオペレーションシステムのバージョンは[トースト(NHN Cloud)サービス紹介](https://toast.com/service/compute/instance)を参照してください。

全てのイメージは、インスタンスの仮想ハードウェアで最適に実行されるよう設定されており、NHN Cloudのセキュリティ検証を経ているため、安全に使用できます。イメージの詳細な説明は[イメージ概要](/Compute/Image/ja/overview/)を参照してください。

### インスタンスタイプ(Instance flavor)

NHN Cloudは顧客の使用用途に合った様々なタイプのインスタンスタイプを提供します。運営するサービスまたはアプリケーションの特性に応じて適切な仕様のインスタンスを生成できます。すでに生成されたインスタンスタイプはウェブコンソールから簡単に変更できます。

| タイプ   | 説明                                                                                                                                              |
| ------- |--------------------------------------------------------------------------------------------------------------------------------------------------|
| m2 | CPUとメモリをバランスよく設定した仕様です。サービスやアプリケーションの性能の必須要件がはっきりしていない場合に使用します。                                                                               |
| c2 | CPUの性能を高く設定したインスタンスの仕様です。高性能演算性能が必要なウェブアプリケーションサーバーや分析システムに使用します。                                                                           |
| r2 | 他のリソースに比べてメモリの使用量が多い場合に使用できます。通常、メモリデータベースやキャッシュサーバーに使用します                                                                               |
| t2 | 安価なインスタンスです。作業負荷が高くないサーバーに使用します。                                                                                                          |
| u2 | 最も安価なインスタンスです。作業負荷が高くないサーバーで使用します。<br>ローカルブロックストレージを使用するため、相対的に他のインスタンスより安定性が落ちますが、低価格で利用できます。<br>このタイプのインスタンスはI/O性能を保障しません。 |
| x1 | ハイスペックのCPUとメモリをサポートしている仕様です。高い性能が必要なサービスやアプリケーションに使用します。                                                                                        |


### アベイラビリティゾーン(Availability zone)

NHN Cloudは物理ハードウェアの問題で発生する障害に備えるため、システム全体を複数のアベイラビリティゾーンに分けました。このアベイラビリティゾーンごとにストレージ、ネットワークスイッチ、ラック、電源装置が別々に構成されています。1つのアベイラビリティゾーン内で発生する障害は他のアベイラビリティゾーンに影響を与えないので、サービス全体の可用性が高くなります。インスタンスを複数のアベイラビリティゾーンに分けて構築すれば、サービスの可用性をさらに高めることができます。

異なるアベイラビリティゾーンの間には、次のような特性があります。

- 複数のアベイラビリティゾーンに分散して生成されたインスタンス同士ネットワーク通信が可能で、この時に発生するネットワーク使用費用はかかりません。
- 同じアベイラビリティゾーンに生成されたインスタンスの間では、ブロックストレージを共有できますが、異なるアベイラビリティゾーン間ではブロックストレージを共有できません。
- 異なるアベイラビリティゾーンでFloating IPを共有できます。もし1つのアベイラビリティゾーンで障害が発生しても、迅速に別のアベイラビリティゾーンにFloating IPを移動して障害時間を最小化できます。


### キーペア(Key-pair)

キーペアは公開鍵基盤構造([PKI](https://ja.wikipedia.org/wiki/%E5%85%AC%E9%96%8B%E9%8D%B5%E5%9F%BA%E7%9B%A4)、public key infrastructure)をベースにしたSSH公開鍵、秘密鍵のペアです。NHN Cloudで生成されたインスタンスに接続するにはセキュリティが脆弱なキーボード入力方式のID/パスワード認証の代わりにキーペアを利用する必要があります。ユーザーはキーペアの秘密鍵を利用してログイン情報をエンコードしてインスタンスに転送して接続認証を受けた後、安全にインスタンスに接続できます。キーペアを利用したインスタンス接続方法は[インスタンス接続方法](#_5)を参照してください。

キーペアはインスタンスを生成する時、NHN Cloudコンソールで新しく作成することもでき、顧客が直接作成したキーペアを登録して使用することもできます。キーペアの登録方法は[コンソールガイドのキーペアをインポート](./console-guide/#_16)を参照してください。

> [注意]
> キーペアを新たに作成すると、キーペアの秘密鍵をダウンロードします。秘密鍵は一度しか発行しないので、ダウンロードした秘密鍵は安全なディスクや外部記憶装置などに保管してください。秘密鍵が外部に流出すると、誰でもその秘密鍵で該当のインスタンスにアクセスできるので、慎重に管理する必要があります。

### セキュリティグループ(Security group)

セキュリティグループはインスタンスに伝達されるネットワークトラフィックを決定する仮想のファイアウォールです。セキュリティグループの詳細は[VPC概要](/Network/VPC/ja/overview/)を参照してください。

> [参考]
> 基本セキュリティグループは外部からのインバウンド(in-bound)ネットワークトラフィックを全て無視するようになっています。SSHでインスタンスに接続する時、インスタンスが属するセキュリティグループにSSHポートを開くように設定した後、インスタンスに接続します。

### ネットワーク

インスタンスが外部と通信するには、VPCで定義されたネットワークのうち少なくとも1つ以上に接続されている必要があります。ネットワークに接続されていないインスタンスにはアクセスできません。ネットワークを新たに作成したり変更したりするには[VPC概要](/Network/VPC/ja/overview/)を参照してください。

## 課金

インスタンス課金方式は次の通りです。

* インスタンスは生成した瞬間から課金されます。
* インスタンスルートブロックストレージはインスタンスと別にブロックストレージ課金基準で課金されます。
* インスタンスが停止すると、90日間Webサイト料金基準で90%割引された金額を適用します。停止状態が90日を超えると停止状態を維持したまま正常料金に切り替わります。
* 終了したインスタンスは課金されません。

課金の詳細については、サービス別[料金ページ](https://www.toast.com/kr/service/compute/instance#price)を参照してください。

## インスタンス接続方法

### Linuxインスタンス接続方法

Linuxインスタンスに接続する時はSSHクライアントを利用します。インスタンスのセキュリティグループにSSHアクセスポート(デフォルト値22)が開いていない場合は接続できません。SSHアクセスを許可する方法は[VPC概要](/Network/VPC/ja/overview/)を参照してください。インスタンスにFloating IPが割り当てられていない場合は、NHN Cloud外部からアクセスできません。Floating IPを割り当てる方法については[VPC概要](/Network/VPC/ja/overview/)を参照してください。

#### MacまたはLinuxのSSHクライアントでLinuxインスタンスに接続する方法

MacやLinuxには通常、SSHクライアントがデフォルトでインストールされています。SSHクライアントで下記のようにキーペアの秘密鍵を利用して接続します。

CentOSインスタンス

	$ ssh -i my_private_key.pem centos@<インスタンスのIP>

Ubuntuインスタンス

	$ ssh -i my_private_key.pem ubuntu@<インスタンスのIP>

Debianインスタンス

	$ ssh -i my_private_key.pem debian@<インスタンスのIP>

Rockyインスタンス

	$ ssh -i my_private_key.pem rocky@<インスタンスのIP>

#### WindowsでPuTTY SSHクライアントでLinuxインスタンスに接続する方法

PuTTY SSHクライアントはWindowsで多く使用されるSSHクライアントプログラムです。[PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)をインストールします。

WindowsのPuTTY SSH クライアントでLinuxインスタンスに接続するには、3段階を踏む必要があります。

* キーペアの秘密鍵をPuTTY用秘密鍵に変更
* PuTTY用秘密鍵をPuTTYに登録
* PuTTYでインスタンスに接続


##### 1. キーペアの秘密鍵をPuTTY用秘密鍵に変更

PuTTYではキーペアの秘密鍵をPuTTYの秘密鍵形式に変更して使用する必要があります。キー変換はPuTTYと一緒にインストールされているPuTTygenを利用します。

![イメージ1](http://static.toastoven.net/prod_instance/putty-ssh-001-en.png)

** PuTTY Key Generator**ダイアログボックスの一番下**パラメータ**の**「Type of key to generate」欄**で**RSA**を選択して**「Number of bits in a generated key」**はデフォルト値の「2048」を入力します。**Actions**下の**「Load an existing private key file 」**横の**「Load」**ボタンをクリックしてキーペアの秘密鍵ファイルを読み込みます。

![イメージ2](http://static.toastoven.net/prod_instance/putty002-en.png)

**Actions**下の**「Save the generated key」**横の**「Save private key」**ボタンをクリックしてPuTTY用に変換されたキーペアの秘密鍵を保存します。**「Key passphrase」欄**を空欄のまま秘密鍵を保存すると、**パスフレーズで保護しないままこのキーを保存しますか？* *というメッセージが表示されます。変換された秘密鍵をより安全に保存するにはパスフレーズを設定して保存します。

> [注意]
インスタンスに自動的にログインするように設定するには、パスフレーズを使用しないでください。パスフレーズを使用すると、ログインする時に秘密鍵のパスワードを直接入力する必要があります。

##### 2. PuTTY用秘密鍵をPuTTYに登録

こうして作ったPuTTY用秘密鍵は2つの方法で登録して使用できます。

* PuTTYで認証秘密鍵ファイルを登録して使用する方法
* pageant(PuTTY認証エージェント)に認証秘密鍵ファイルを登録して使用する方法

**A. PuTTYで認証秘密鍵ファイルを登録して使用する方法**


PuTTYを実行し、左の**カテゴリ**から** Connection > SSH > Auth**を選択します。右の**Authentication parameters**下の**Private key file for authentication**にPuTTY用の秘密鍵を登録します。

![イメージ3](http://static.toastoven.net/prod_instance/putty005-en.png)

秘密鍵を登録した後、接続情報を保存しておくと、毎回秘密鍵ファイルを再登録する必要がありません。接続情報を保存する方法は下の接続方法を参照してください。


**B. Pageant(PuTTY認証エージェント)に認証秘密鍵ファイルを登録して使用する方法**


PuTTYと一緒にインポートされているpageantを実行すると、下図のようにWindowsトレイにアイコンが表示されます。pageantアイコンを右クリックし、**Add key**メニューをクリックしてPuTTY用の秘密鍵を追加します。

![イメージ4](http://static.toastoven.net/prod_instance/putty006.png)

秘密鍵が追加されたことを確認するには**View keys**を選択します。キーが追加されていれば、下図のように追加されたキーが表示されます。

![イメージ5](http://static.toastoven.net/prod_instance/putty008-en.png)

Pageantは一度実行されると、Windowsトレイに残って実行されるのでインスタンスに接続する度に再実行する必要がありません。ただしWindowsを再起動した場合は再度実行する必要があります。

##### 3. PuTTYでインスタンスに接続

PuTTY用に変換された秘密鍵が登録されたらPuTTYを実行します。

![イメージ6](http://static.toastoven.net/prod_instance/putty009-en.png)

基本接続情報の**ホスト名**は次のように使用します。

CentOS

	centos@<インスタンスのIP>

Ubuntu

	ubuntu@<インスタンスのIP>

Debian

	debian@<インスタンスのIP>

Rocky

	rocky@<インスタンスのIP>

**ポート**はSSH基本ポートの22、**接続形式**は**SSH**を指定します。

全ての情報が正確であればセッションを保存します。**読込、保存、削除**で保存されたセッションの下のフィールドに保存するセッション名を書き、**保存**ボタンをクリックしてセッションを保存します。セッションを保存しない場合、2-Aで登録した秘密鍵設定も維持されません。

**開く**をクリックするとインスタンスに接続します。


### Windowsインスタンス接続方法

Windowsインスタンスに接続するには、NHN Cloudコンソールから接続するWindowsインスタンスを選択します。インスタンス詳細画面の**接続情報**タブで**パスワード確認**ボタンを押して、Windowsサーバーに設定されたパスワードを確認します。

**パスワード確認**で入力するキーペアの秘密鍵はサーバーに送信されず、ブラウザでパスワードを復号化する作業にのみ使用します。

**パスワード確認**横の**接続**ボタンをクリックしてリモートデスクトップ接続設定が保存された.rdpファイルをダウンロードして実行するとWindowsインスタンスに接続します。WindowsサーバーのIDは「Administrator」で、パスワードはNHN Cloudコンソールで確認したパスワードを利用します。