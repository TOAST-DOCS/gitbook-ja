## AI Service > Pose Estimation > APIガイド


### ポーズ認識API

#### リクエスト

- {appKey}と{secretKey}はコンソール上部の **URL & Appkey** メニューで確認できます。

[URI]

| メソッド | URI                                                                        |
|---|----------------------------------------------------------------------------|
| POST | https://pose-estimation.api.nhncloudservice.com/v1.0/appkeys/{appKey}/pose |

[リクエストヘッダ]

| 名前 | 値 | 説明            |
|---|---|-----------------|
| Authorization | {secretKey} | コンソールで発行されたセキュリティキー |

[Path Variable]

| 名前 | 値 | 説明            |
| --- | --- |-----------------|
| appKey | {appKey} | 統合AppkeyまたはサービスAppkey |

[リクエスト本文]

- 画像ファイルのBinary Dataを入れます。

```
curl -X POST 'https://pose-estimation.api.nhncloudservice.com/v1.0/appkeys/{appKey}/pose' \
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
    "numberOfPerson": 5,
    "keyPointList": [
      {
        "personId": "0",
        "inferKeypointList": [
          {
            "name": "nose",
            "part": "body",
            "x": 367.151489,
            "y": 79.552887,
            "score": 0.976
          },
          {
            "name": "left_eye",
            "part": "body",
            "x": 373.819214,
            "y": 73.5605469,
            "score": 0.985
          },
          ...
        ]
      },
      ...
      {
        "personId": 2,
        "inferKeypoints": [
          {
            "name": "nose",
            "part": "body",
            "x": 98.7361755,
            "y": 68.2939758,
            "score": 0.979
          },
          {
            "name": "left_eye",
            "part": "body",
            "x": 110.171448,
            "y": 56.0753479,
            "score": 0.983
          },
          ...
        ]
      },
    ]
  }
}
```

[ヘッダ]

| 名前 | タイプ | 説明                          |
|---|---|-------------------------------|
| isSuccessful | Boolean | 認識APIの成否                |
| resultCode | Integer | 結果コード                       |
| resultMessage | String | 結果メッセージ(成功時はsuccess、失敗時はエラー内容) |

[フィールド]

| 名前                                       | タイプ    | 説明                                    |
|--------------------------------------------|---------|-----------------------------------------|
| fileType                                   | String  | ファイル拡張子(.jpg, .png)                      |
| numberOfPerson                             | Integer | 認識結果人数                             |
| keyPointList[0].personId                   | String  | 認識結果区分のために付与されたID                     |
| keyPointList[0].inferKeypointList[0].name  | String  | 身体部位の名前                              |
| keyPointList[0].inferKeypointList[0].part  | String  | 身体部位が属する部分名(body, foot, face, hand) |
| keyPointList[0].inferKeypointList[0].x     | Double  | キーポイントx座標                             |
| keyPointList[0].inferKeypointList[0].y     | Double  | キーポイントy座標                             |
| keyPointList[0].inferKeypointList[0].score | Double  | キーポイント認識結果信頼度                        |
