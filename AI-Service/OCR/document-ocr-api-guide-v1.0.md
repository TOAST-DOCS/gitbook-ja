## AI Service > OCR > Document OCR > API v1.0ガイド

### 事業者登録証分析API

#### リクエスト

- {appKey}と{secretKey}はコンソール上部の**URL & Appkey**メニューで確認が可能です。

[URI]

| メソッド | URI |
|---|---|
| POST | https://ocr.api.nhncloudservice.com/v1.0/appkeys/{appKey}/business |

[リクエストヘッダ]

| 名前 | 値 | 説明             |
|---|---|-----------------|
| Authorization | {secretKey} | コンソールで発行されたセキュリティキー |

[Path Variable]

| 名前 | 値 | 説明           |
| --- | --- |-----------------|
| appKey | {appKey} | 統合AppkeyまたはサービスAppkey |

[リクエスト本文]

- 画像ファイルのBinary Dataを入れます。

```
curl -X POST 'https://ocr.api.nhncloudservice.com/v1.0/appkeys/{appKey}/business' \
-F 'image=@sample.png' \
-H 'Authorization: ${secretKey}'
```

[フィールド]

| 名前 | タイプ | 説明 |
|---|---|---|
| image | multipart/form–data | 画像ファイル |

#### レスポンス

[レスポンス本文]

```json
{
    "header": {
        "isSuccessful": true,
        "resultCode": 0,
        "resultMessage": "SUCCESS"
    },
    "result": {
        "fileType": "png",
        "unitType": "pixel",
        "keyValues": [
            {
                "key":"区分",
                "value":"簡易課税者",
                "conf":0.93
            },
            {
                "key":"登録番号",
                "value":"123-45-67890",
                "conf":1
            },
            ...
        ],
        "boxes": [
            {
                "x1": 340,
                "y1": 3231,
                "x2": 523,
                "y2": 3231,
                "x3": 523,
                "y3": 3297,
                "x4": 340,
                "y4": 3297
            },
            ...
        ],
        "resolution": "normal"
    }
}
```

[ヘッダ]

| 名前 | タイプ | 説明 |
|---|---|---|
| isSuccessful | Boolean | 分析API成否 |
| resultCode | Integer | 結果コード |
| resultMessage | String | 結果メッセージ(成功時はsuccess、失敗時はエラー内容) |

[フィールド]

| 名前 | タイプ | 説明 |
|---|---|---|
| fileType | String | ファイル拡張子(.pdf、.jpg、.png) |
| keyValues | List | 認識結果リスト |
| keyValues[0].key | String | 認識項目名 |
| keyValues[0].value | String | 認識内容 |
| keyValues[0].conf | Double | 認識結果の信頼度 |
| resolution | String | 推奨解像度(HD 1280*720px)以上の場合はnormal、推奨解像度未満はlow |
| unitType | String | boxes座標単位(基本pixel、PDFの場合point) |
| boxes | List | 認識領域(Bounding box)座標リスト |
| boxes[0] | Object  | 認識領域座標{ x1, y1, x2, y2, x3, y3, x4, y4 } |

* boxes[0]
 
    ![Bounding box](http://static.toastoven.net/prod_ocr/bbox.png)

### 事業者登録証 休/廃業照会API

#### リクエスト

- {appKey}と{secretKey}は、コンソール上部の**URL & Appkey**メニューで確認できます。

[URI]

| メソッド | URI                                                                       |
|---|---------------------------------------------------------------------------|
| POST | https://ocr.api.nhncloudservice.com/v1.0/appkeys/{appKey}/business/status |

[リクエストヘッダ]

| 名前 | 値 | 説明             |
|---|---|-----------------|
| Authorization | {secretKey} | コンソールで発行されたセキュリティキー |

[Path Variable]

| 名前 | 値 | 説明             |
| --- | --- |-----------------|
| appKey | {appKey} | 統合AppkeyまたはサービスAppkey |

[フィールド]

| 名前            | タイプ    | 説明 |
|----------------|--------|---|
| businessNumber | String | 事業者登録証の登録番号(10桁の数字) |

[リクエスト本文]

```
curl -X POST 'https://ocr.api.nhncloudservice.com/v1.0/appkeys/{appKey}/business/status' \
-H 'Authorization: ${secretKey}' \
--data-raw '{
  "businessNumber": "1234567890"
}'
```

#### レスポンス

[レスポンス本文]

```json
{
    "header": {
        "isSuccessful": true,
        "resultCode": 0,
        "resultMessage": "SUCCESS"
    },
    "result": {
        "statusCode": "00",
        "statusMessage": ""
    }
}
```


[ヘッダ]

| 名前 | タイプ | 説明                             |
| --- | --- |---------------------------------|
| isSuccessful | Boolean | 休業/廃業照会API成否              |
| resultCode | Integer | 結果コード                          |
| resultMessage | String | 結果メッセージ(成功時はsuccess、失敗時はエラー内容) |

[フィールド]

| 名前        | タイプ    | 説明 |
|-------------|--------| --- |
| statusCode | String | 事業者登録証のステータスコード(国税庁の結果コード) |
| statusMessage | String | 事業者登録証のステータスメッセージ |

* **"statusCode"別の事業者登録証の状態リスト**

| コード値 | 説明                                      |
|---|------------------------------------------|
| 00 | 事業を行っていない事業者                        |
| 01 | 付加価値税一般課税者                             |
| 02 | 付加価値税簡易課税者                             |
| 03 | 付加価値税免税事業者                             |
| 04 | 収益事業を営んでいない非営利法人または固有番号が付与された団体。国家機関 |
| 05 | 休業者                                      |
| 06 | 廃業者                                      |
| 09 | その他                                      |

### クレジットカード分析API

#### リクエスト

- {appKey}と{secretKey}はコンソール上部の**URL & Appkey**メニューから確認できます。

[URI]

| メソッド | URI |
|---|---|
| POST | https://ocr.api.nhncloudservice.com/v1.0/appkeys/{appKey}/credit-card |

[リクエストヘッダ]

| 名前 | 値 | 説明             |
|---|---|-----------------|
| Authorization | {secretKey} | コンソールで発行されたセキュリティキー |

[Path Variable]

| 名前 | 値 | 説明           |
| --- | --- |-----------------|
| appKey | {appKey} | 統合AppkeyまたはサービスAppkey |

[リクエスト本文]

- 画像ファイルのBinary Dataを入れます。

```
curl -X POST 'https://ocr.api.nhncloudservice.com/v1.0/appkeys/{appKey}/credit-card' \
-F 'image=@sample.png' \
-H 'Authorization: ${secretKey}'
```

[フィールド]

| 名前 | タイプ | 説明 |
|---|---|---|
| image | multipart/form–data | 画像ファイル |

#### レスポンス

[レスポンス本文]

```json
{
    "header": {
        "isSuccessful": true,
        "resultCode": 0,
        "resultMessage": "SUCCESS"
    },
    "result": {
        "fileType": "png",
        "resolution": "low",
        "cardNums": [
                    {
                        "value": "1111",
                        "conf": 0.87
                    },
                    {
                        "value": "2222",
                        "conf": 0.99
                    },
                    {
                        "value": "3333",
                        "conf": 0.97
                    },
                    {
                        "value": "4444",
                        "conf": 0.89
                    }
        ],
        "totalCardNum": "111222233334444",
        "cardNumBoxes": [
            {
                "x1": 62,
                "y1": 256,
                "x2": 192,
                "y2": 256,
                "x3": 192,
                "y3": 301,
                "x4": 62,
                "y4": 301
            },
            ...
        ],
        "validThru": {
            "value": "04/19",
            "conf": 0.53
        },
        "validThruBox": {
            "x1": 316,
            "y1": 315,
            "x2": 426,
            "y2": 315,
            "x3": 426,
            "y3": 347,
            "x4": 316,
            "y4": 347
        }
    }
}
```

[ヘッダ]

| 名前 | タイプ | 説明 |
|---|---|---|
| isSuccessful | Boolean | 分析API成否 |
| resultCode | Integer | 結果コード |
| resultMessage | String | 結果メッセージ(成功時はsuccess、失敗時はエラー内容) |

[フィールド]

| 名前 | タイプ | 説明 |
|---|---|---|
| fileType | String | ファイル拡張子(.jpg, .png) |
| resolution | String | 推奨解像度(760*480px)以上の場合はnormal、推奨解像度未満はlow |
| cardNums | List | カード番号認識結果リスト |
| cardNums[0].value | String | 認識結果 |
| cardNums[0].conf | Double | 認識結果の信頼度 |
| totalCardNum | List | カード番号全体認識結果 |
| cardNumBoxes | List | カード番号認識領域(Bounding box)座標リスト |
| cardNumBoxes[0] | Object  | 認識領域座標{ x1, y1, x2, y2, x3, y3, x4, y4 } |
| validThru.value | String | 有効期限認識内容 |
| validThru.conf | Double | 有効期限認識結果の信頼度 |
| validThruBox | Object  | 有効期限認識領域座標{ x1, y1, x2, y2, x3, y3, x4, y4 } |

* boxes[0]
 
    ![Bounding box](http://static.toastoven.net/prod_ocr/bbox.png)
