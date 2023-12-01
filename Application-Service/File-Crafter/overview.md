## Application Service > File Crafter > 概要

- File CrafterはFileを利用して特定API URLに繰り返しリクエストを送ったり、APIレスポンス結果を収集してFileでダウンロードしたりできるサービスです。大容量処理に必要なメモリ管理、非同期 フロー管理など、難しくて煩雑な処理をサポートします。

### 特徴

- Fileを利用して特定API URLに繰り返しリクエストを送ったり、APIレスポンス結果を収集してFileでダウンロードしたりできます。
- 好きな形式のFileでデータを提供し、受け取ることができます。
- Export処理結果ファイルは顧客が指定したStorageにアップロードされます。

### 主要機能

- File Import
    - 好きな形式のFileで提供されたデータを顧客APIに繰り返し送って処理します。

- File Export
    - リクエストされた顧客APIを繰り返し呼び出して、受け取った結果レスポンスを好きな形式のFileに加工して顧客Storageにアップロードします。
    - 結果ファイルの規模が大きくて複数のファイルで作成される場合、圧縮してアップロードします。

- 処理状況照会
    - 顧客がリクエストしたImport/Exportの処理状況を照会できます。

- パスワードが適用されたExcelファイルを処理可能

### サービス対象

- 繰り返しAPI呼び出し、その結果をファイルで抽出する必要がある場合
- 大量の入力データを繰り返し処理する必要がある場合
- 大量データ処理に必要なメモリ管理、非同期フロー管理など、難しくて煩雑な処理を避けたい場合