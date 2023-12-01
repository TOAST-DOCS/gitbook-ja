## Application Service > Maps > iOSマップSDKガイド
iOSプラットフォームでinaviマップを使用するためのプロジェクト基本設定方法を説明します。

### 事前準備
- inaviマップを使用するには認証用の**Appkey**が必要です。

#### サービス有効化
- **NHN Cloud Console**でサービスを選択してApplication Service > Mapsをクリックします

#### Appkey確認
- **Appkey**は、**NHN Cloud Console**上部の**URL & Appkey**メニューで確認できます。


### Project環境構成
inaviマップSDKを使用するには、次の順序でプロジェクトの環境を構成する必要があります。

#### Git LFSインストール
SDKの容量が大きいため、Pod依存性をインストールする前に[Git Large File Storage(LFS)](https://git-lfs.github.com/)のインストールが必要です。
> `git-lfsがインストールされていない場合、SDK依存性のインストールが正常に進行できず、ビルドの際にエラーが発生します。`

```
brew install git-lfs
git lfs install
```

#### Podfile構成
inaviマップSDKはCocoaPodsを通して配布されるため、次のようにプロジェクトのPodfileファイルにinaviマップSDKに対する依存性を追加します。

```ruby
# Podfile
target 'iNaviMapsDemo' do
  use_frameworks!
  ...
  pod 'inavi-maps-sdk'
  ...
end
```

#### SDKインストール
依存性設定を行った後、Terminalでプロジェクトpathに移動し、下記のコマンドを実行してinaviマップSDKをインストールします。
> `SDK依存性インストールが完了した時、フレームワークの容量は約100MBです。`
```
pod install --repo-update
```

#### CocoaPodsキャッシュ削除
もし以前ダウンロードしたSDK依存性のキャッシュが残っている場合、ビルドの際にエラーが発生する場合があります。
下記のコマンドでinaviマップSDKのCocoaPodsキャッシュを削除できます。
```
pod cache clean inavi-maps-sdk
pod update inavi-maps-sdk
```

### Appkey設定
発行したAppkeyを設定する方法は下記のとおりです。

> Appkeyが未設定の場合、マップ初期化段階で認証エラーが発生します。

#### 1. プロジェクトinfo.plistで設定
`info.plist`ファイル内部にAppkeyを設定できます。
```xml
<!-- info.plist -->
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	...
	<key>iNaviAppKey</key>
	<string>YOUR_APP_KEY</string>
	...
</dict>
</plist>
```

#### 2. INVMapSdk APIを呼び出して設定
Application作成時点で動的に[INVMapSdk]シングルトンオブジェクトの関数を呼び出してAppkeyを設定できます。

```swift
// Swift
INVMapSdk.sharedInstance().appKey = "YOUR_APP_KEY"
```

#### 認証失敗
マップ初期化段階で認証に失敗すると、SDK内部に登録されたCallbackにエラーコードとメッセージを伝達します。
失敗のCallbackを受け取るには、[INVMapSdk]シングルトンオブジェクトに[INVMapSdkDelegate]を下記のように設定する必要があります。
```swift
// Swift
INVMapSdk.sharedInstance().delegate = self

func authFailure(_ errorCode: Int, message: String) {
    // 認証失敗処理
}

```
認証失敗Callbackを別途設定していない場合、エラーコードとメッセージがポップアップ表示されます。

#### 認証エラーコード
| Code | Description |
| ------ | ------ |
| 300 | Appkeyが無効
| 401 | Appkeyが未設定 |
| 503 | サーバー接続失敗 |
| 504 | サーバー接続時間超過 |
| 500 | 不明なエラー |
| その他 | サーバーエラー(今後定義したらアップデート) |


### マップを作成する
アプリ画面にinaviマップを表示する方法を説明します。

#### マップ表示
UIViewControllerで直接[InaviMapView]を作成して追加する例です。
```swift
// Swift
import iNaviMaps

override func viewDidLoad() {
    super.viewDidLoad()

    let mapView = InaviMapView(frame: view.bounds)
    view.addSubview(mapView)
}
```
Interface Builderを使用してマップを追加するには、XIBまたはStoryboardにUIViewを追加した後
Identity InspectorパネルのCustom Class項目を[InaviMapView]に設定してください。

#### マップイベント設定
[INVMapViewDelegate]を実装し、[InaviMapView]の`delegate`プロパティを設定すると、マップクリック、ダブルクリックなどのマップとユーザー間のインタラクションに対するイベントを設定できます。
```swift
// Swift
override func viewDidLoad() {
    super.viewDidLoad()
    ...
    mapView.delegate = self
}

func didTapMapView(_ point: CGPoint, latLng latlng: INVLatLng) {
    // point :クリックした地点の画面上の座標
    // latLng ：クリックした地点のマップ上の座標
}
```

#### マーカー表示
マーカーオブジェクトを作成し、`position`プロパティと`map`プロパティを設定すると、マーカーが表示されます。
```swift
// Swift
let marker = INVMarker(position: INVLatLng(lat: 37.40219, lng : 127.11077))
marker.title = "タイトル"
marker.mapView = mapView
```

#### マーカー削除
マーカーオブジェクトのmapプロパティを`nil`に設定すると、マーカーが削除されます。
```swift
// Swift
marker.mapView = nil
```

#### カメラ移動
[INVCameraUpdate]のFactory Methodまたは[INVCameraUpdateParams]を通して[INVCameraUpdate]オブジェクトを作成した後
[moveCamera()]関数にパラメータを伝達して呼び出すと、カメラが移動します。

アニメーションとカメライベントに対するコールバックをサポートするため、カメラ移動を自由に実装できます。
```swift
// Swift
let camUpdate = INVCameraUpdate.init(targetTo: INVLatLng(lat: 36.99473, lng : 127.81832))
camUpdate.animation = .fly
camUpdate.animationDuration = 3
mapView.moveCamera(camUpdate)
```

#### 自分だけのマップスタイルの作成
`Map Studio`サービスを利用すると、フォントはもちろん、マップの色、凡例アイコンまで自由に変更して自分だけの特別なマップを作成できます。また最新バージョンのSDKで提供するAPIを利用すると、カスタムスタイルをマップに適用できます。
```swift
// Swift
INVMapSdk.sharedInstance().delegate = self
func authSuccess(_ customMapStyles: [INVMapStyle]) {
        // マップ初期化認証が完了すると、マップスタイルの配列をコールバックに渡す
}
// 保存されたカスタムスタイルの配列の最初のカスタムスタイルをマップに適用
mapView.customMapStyle = INVMapSdk.sharedInstance().savedCustomMapStyles.first
```

### 主要Maps SDK案内
Maps SDKの使用方法は[iNavi Maps APIセンター](http://imapsapi.inavi.com/)を参照してください。

[INVMapSdk] : [https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/INVMapSdk.html](https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/INVMapSdk.html)
[INVMapSdkDelegate] : [https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Protocols/INVMapSdkDelegate.html](https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Protocols/INVMapSdkDelegate.html)

[InaviMapView] : [https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/InaviMapView.html](https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/InaviMapView.html)

[INVMapViewDelegate] : [https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Protocols/INVMapViewDelegate.html](https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Protocols/INVMapViewDelegate.html)

[INVCameraUpdate] : [https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/INVCameraUpdate.html](https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/INVCameraUpdate.html)
[INVCameraUpdateParams] : [https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/INVCameraUpdateParams.html](https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/INVCameraUpdateParams.html)

[moveCamera()] : [https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/InaviMapView.html#/c:objc(cs)InaviMapView(im)moveCamera:](https://inavi-systems.github.io/inavi-maps-sdk-reference/ios/Classes/InaviMapView.html#/c:objc(cs)InaviMapView(im)moveCamera:)

[NHN Cloud Console] : [https://console.toast.com/](https://console.toast.com/)
