## AI Service > Text To Speech > APIガイド

### 音声合成API

#### リクエスト

- {appKey}と{secretKey}はコンソール上部の**URL & Appkey** メニューで確認できます。

[URI]

| メソッド | URI |
|---|---|
| POST | https://speech.api.nhncloudservice.com/v1.0/appkeys/{appKey}/tts |

[リクエストヘッダ]

| 名前 | 値 | 説明 |
|---|---|---|
| Authorization | {secretKey} | コンソールで発行されたセキュリティキー |
| Content-Type | application/json | |

[リクエスト本文]
```
{
    "inputText": "入力テキスト",
    "fileType": "WAV",
    "language: "JA",
    "speaker": "MALE",
    "emotion": "NEUTRAL",
    "pitch": 0,
    "speed": 1,
    "volume": 0
}
```

[フィールド]

| 名前 | タイプ | 必須かどうか | デフォルト値 | 有効範囲 | 説明 |
|---|---|---|---|---|---|
| inputText | String | 必須 | | 最大1000文字 | 入力テキスト |
| fileType | String | 任意 | MP3 | MP3/WAV | ファイル形式(.mp3、.wav) |
| language | String | 任意 | KO | KO/EN/JA/ZH | 言語(韓国語、英語、日本語、中国語) |
| speaker | String | 任意 | FEMALE | MALE/FEMALE | 音声の種類(男性、女性) |
| emotion | String | 任意 | NEUTRAL | NEUTRAL/DARK/BRIGHT | 音声の感情(基本、暗い、明るい) |
| pitch | Float | 任意 | 0 | -12~12| 高低 |
| speed | Float | 任意 | 1 | 0.5~4 | 速度 |
| volume | Float | 任意 | 0 | -6~6 | 音量 |

#### レスポンス

[成功レスポンス]
* HTTP Status Code: 200
* Content-Type: audio/wavまたはaudio/mpeg
* Body: byte[]

[失敗レスポンス]
* Content-Type: application/json
```
{
    "header": {
        "isSuccessful": false,
        "resultCode": 400,
        "resultMessage": "Bad Request"
    },
    "errorList": [
        {
            "resultCode": 4000001,
            "resultTitle": "Invalid parameter.  (speed)",
            "resultMessage": "Must be equal to or less than  4 "
        },
        {
            "resultCode": 4000001,
            "resultTitle": "Invalid parameter.  (pitch)",
            "resultMessage": "Must be equal to or less than  12 "
        }
    ]
}
```
