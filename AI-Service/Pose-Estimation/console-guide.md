## AI Service > Pose Estimation > コンソール使用ガイド

コンソールに画像ファイルをアップロードして、すべての人物の領域を認識し、その領域の人体関節位置情報を取得できます。

## Pose Estimation

### 分析のための写真アップロード

分析する画像をアップロードします。

- 画像は次の2つの方法でアップロードできます。
    1. **画像アップロード**ボタンをクリック
    2. 画像をドラッグ&ドロップ

### 分析

写真をアップロードした後、**分析**ボタンをクリックすると、分析結果が画面右側にJSON形式で表示されます。

* [fileType]ファイル拡張子(.jpg, .png)
* [numberOfPerson]認識結果人数
* [keyPointList] 認識された人のリスト
    * [personId] 認識結果を区別するために付与されたID
    * [inferKeypointList] 認識された身体部位のリスト
        * [name] 身体部位の名前
        * [part] 身体部位が属する部分名(body, foot, face, hand)
        * [ x ] x座標
        * [ y ] y座標
        * [score]認識結果に対する信頼度


```json
{
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
```

* 分析結果のコピーおよびダウンロード(JSON)機能を提供します。
