## Security > Webshell Threat Detector > コンソール使用ガイド

ここでは点検エージェント実行手順を説明します。 

## エージェント実行手順

インスタンスOSを選択してエージェント実行スクリプトを呼び出します。

![WebshellThreatDetector_01_20221129.png](https://static.toastoven.net/prod_webshellthreatdetector/WebshellThreatDetector_jp_01_20221129.png)

### Linux系列エージェント

1. 実行スクリプトをコピーするには**クリップボードにコピー**をクリックします。

2. 実行対象インスタンスターミナルに接続します。

3. 管理者権限でエージェントスクリプトを作成し、実行します。

* root権権限を取得します。
* viエディタなどでスクリプトを作成します。
* 作成したスクリプトファイルの権限を変更します。
* ファイルを実行します。
```
[root@centos7 ~]# cd ~
[root@centos7 ~]# sudo su
[root@centos7 ~]# vi installer.sh
[root@centos7 ~]# chmod 744 installer.sh
[root@centos7 ~]# ./installer.sh
Configure the work directory..
Configure the data directory..
Install Finished!
```

## エージェント無効化手順

1. 削除スクリプトをコピーします。

```
pkill pfcont && pkill pfmont && pkill pfrmont && pkill pfinstor && pkill pfsder && pkill acontroller && rm -rf /nwtd
```

2. 削除対象インスタンスターミナルに接続します。

3. 管理者権限で削除スクリプトを実行します。

* Webshell Threat Detectorプロセスを終了します。
* Webshell Threat Detectorファイルを削除します。

4. 正常に削除されたことを確認したい場合は/nwtdディレクトリが存在するか確認します。

## 運営に関するお問い合わせ

### お問い合わせ内容

1. エージェント実行失敗

2. 点検結果の誤用検出申告

### お問い合わせ方法

1. お問い合わせ方法：**サポート > 1:1お問い合わせ**

2. 対応時間：平日09:00～18:00
