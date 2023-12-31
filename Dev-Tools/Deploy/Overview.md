## Dev Tools > Deploy > 概要

Deployサービスを使用すると、'1クリック'で素早くアプリケーションを配布できます。

* バイナリファイル
* マルチメディアファイル
* スクリプトファイル
* 実行ファイル
* その他ユーザーが定義したさまざまなファイル 

![[図1]サービス画像](https://static.toastoven.net/prod_tcdeploy/ja/01_ja.png)

## 利点

* 簡単で便利なバイナリ管理
* クライアントへのバイナリ配布通知
    * メール
    * 文字メッセージ  
* 配布バージョン別リアルタイムモニタリング
* 配布結果メール通知
* 配布前後のシナリオ設定
* ウェブコンソールサポート

![[図2]サービス画像](https://static.toastoven.net/prod_tcdeploy/ja/02_ja.png)

## 提供機能

### アップロード
さまざまなアップロード方式を使用して簡単にファイルをアップロードできます。
* アップロードインターフェイス
    * ウェブコンソール
    * Jenkinsプラグイン
    * REST API

### ダウンロード
ダウンロードリンク通知機能を使用して、簡単にアプリのインストール/アップデートができます。

### バイナリ照会
過去のバイナリデータを維持して、迅速にロールバックできます。

### 配布プロジェクト管理
プロジェクトのインフラ情報を連動して、簡単に設定できます。

### 配布シナリオ(実行)管理
ユーザー定義コマンドを使用して、配布後のサーバー状態を確認できます。

### 配布ヒストリー管理
配布ヒストリーで配布内容および以前のバイナリを管理するので、安定性を確保できます。

## 用語説明

| 用語 | 説明 |
| --- | --- |
| アーティファクト | 配布を管理するDeploy構成の基本単位 |
| サーバーグループ | シナリオ実行対象サーバーグループ |
| シナリオ| サーバーに実行するタスクの集合 |
| タスク | 配布プロセスの実行単位 |
| バイナリ | ユーザーがアップロードした配布対象ファイル |
| リソース | ウェブコンソールで作成、修正、履歴管理が可能な配布対象ファイル |
