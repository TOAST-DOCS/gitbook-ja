
## Security > Secure Key Manager > API v1.2ガイド

Secure Key Managerは、ユーザーデータにアクセスできる多様なAPIを提供します。クライアントは鍵の保存場所に設定した認証をパスした後に、Secure Key Managerに保存したデータを使用できます。

v1.2では、**ユーザー認証に関連する必須のHTTPヘッダーフィールド**が追加され、**キーの追加/削除API**が導入されました。

## 基本情報

### EndPoint
```text
https://api-keymanager.nhncloudservice.com
```

### APIリスト

| Method | URI | 説明 |
|---|---|---|
| GET | /keymanager/v1.2/appkey/{appkey}/confirm | APIを呼び出したクライアント情報を提供します。|
| GET | /keymanager/v1.2/appkey/{appkey}/secrets/{keyid} | Secure Key Managerに保存した機密データを照会します。|
| POST | /keymanager/v1.2/appkey/{appkey}/symmetric-keys/{keyid}/encrypt | Secure Key Managerに保存した対称鍵でデータを暗号化します。|
| POST | /keymanager/v1.2/appkey/{appkey}/symmetric-keys/{keyid}/decrypt | Secure Key Managerに保存した対称鍵でデータを復号します。|
| POST | /keymanager/v1.2/appkey/{appkey}/symmetric-keys/{keyid}/create-local-key | クライアントがローカル環境でデータの暗号化/復号に使用できるAES-256対称鍵を作成します。|
| GET | /keymanager/v1.2/appkey/{appkey}/symmetric-keys/{keyid}/symmetric-key | Secure Key Managerに保存した対称鍵を照会します。 |
| POST | /keymanager/v1.2/appkey/{appkey}/asymmetric-keys/{keyid}/sign | Secure Key Managerに保存した非対称鍵でデータを署名します。|
| POST | /keymanager/v1.2/appkey/{appkey}/asymmetric-keys/{keyid}/verify | Secure Key Managerに保存した非対称鍵でデータと署名を検証します。|
| GET | /keymanager/v1.2/appkey/{appkey}/asymmetric-keys/{keyid}/privateKey | Secure Key Managerに保存した秘密鍵を照会します。 |
| GET | /keymanager/v1.2/appkey/{appkey}/asymmetric-keys/{keyid}/publicKey | Secure Key Managerに保存した公開鍵を照会します。 |
| POST | /keymanager/v1.0/appkey/{appkey}/keys/{secrets\|symmetric-keys\|asymmetric-keys}/create | Secure Key Managerに新規キーを追加します。 |
| PUT | /keymanager/v1.0/appkey/{appkey}/keys/{keyid}/delete | Secure Key Managerに保存したキーの削除をリクエストします。 |
| DELETE | /keymanager/v1.0/appkey/{appkey}/keys/{keyid} | Secure Key Managerに削除予定のキーを即時削除します。 |

[APIリクエストのHTTPヘッダ]

Secure Key ManagerのMACアドレス認証を使用するには、HTTPヘッダにクライアントMACアドレスを設定してリクエストする必要があります。
```
X-TOAST-CLIENT-MAC-ADDR: {MACアドレス}
```

v1.2では、HTTPヘッダーに必須フィールドが追加されます。
```
X-TC-AUTHENTICATION-ID: {User Access Key ID}
X-TC-AUTHENTICATION-SECRET: {Secret Access Key}
```

詳細は[コンソール使用ガイド](https://docs.nhncloud.com/ja/Security/Secure%20Key%20Manager/ja/console-guide/#api)を参照。

[APIリクエストのパス変数]

| 名前 | タイプ | 説明 |
|---|---|---|
| appkey | String | 使用したいデータを保存しているNHN Cloudプロジェクトのアプリケーションキー |
| keyid | String | 使用したいデータの識別子 |

[APIレスポンスのデータ共通ヘッダ]
```
{
    "header": {
        "resultCode": 0,
        "resultMessage": "success",
        "isSuccessful": true
    },
    "body": {
        ...
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| resultCode | Number | API呼び出し結果コード値 |
| resultMessage | String | API呼び出し結果メッセージ |
| isSuccessful | Boolean | API呼び出し成否 |

## クライアント情報照会
APIを呼び出したクライアント情報を照会する時に使用します。
```text
GET https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/confirm
```
[Response Body]

```
{
    "header": {
        ...
    },
    "body": {
        "clientIp": "0.0.0.0",
        "clientMacHeader": "00:00:00:00:00:00",
        "clientSentCerfificate": false
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| clientIp | String | APIを呼び出したクライアントのIPアドレス |
| clientMacHeader | String |APIを呼び出したクライアントのMACアドレスヘッダ値 |
| clientSentCertificate | Boolean | APIを呼び出したクライアントが証明書を使用しているかどうか |

## 機密データ

### 機密データ照会
Secure Key Managerに保存した機密データを照会する時に使用します。
```text
GET https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/secrets/{keyid}
```

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "secret": "data"
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| secret | String | 機密データ照会結果 |

## 対称鍵

### 対称鍵暗号化
Secure Key Managerに作成した対称鍵でデータを暗号化する時に使用します。ユーザーは32KB以下のテキストデータを転送して、Secure Key Managerに保存した対称鍵で暗号化できます。
```text
POST https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/symmetric-keys/{keyid}/encrypt
```

[Request Body]

```
{
    "plaintext": "data"
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| plaintext | String | 対称鍵で暗号化するデータ |

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "ciphertext": "AAAAABzGwQniNneKXmcOLhWnxEqC1rNY+UdVb3lyeX/4wSrP",
        "keyVersion": 1
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| ciphertext | String | 対称鍵でデータを暗号化した結果 |
| keyVersion | Number | APIリクエスト処理に使用した対称鍵バージョン |

### 対称鍵復号
Secure Key Managerに作成した対称鍵でデータを復号する時に使用します。ユーザーは暗号化されたテキストを転送して、Secure Key Managerに保存した対称鍵で復号できます。
```text
POST https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/symmetric-keys/{keyid}/decrypt
```

[Request Body]
```
{
    "ciphertext": "AAAAABzGwQniNneKXmcOLhWnxEqC1rNY+UdVb3lyeX/4wSrP"
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| ciphertext | String | 対称鍵で復号するデータ |

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "plaintext": "data",
        "keyVersion": 1
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| plaintext | String | 対称鍵でデータを復号した結果 |
| keyVersion | Number | APIリクエスト処理に使用した対称鍵バージョン |

### 対称鍵で暗号化したローカル対称鍵作成
クライアントがローカル環境で使用できるAES-256対称鍵を作成する時に使用します。localKeyPlaintextは、作成した対称鍵をBase64エンコードした形式で、Base64エンコード後すぐに使用できます。localKeyCiphertextは、作成した対称鍵をSecure Key Managerに保存した対称鍵で暗号化した後にBase64エンコードした形式で、ストレージに保存する時に使用します。ストレージに保存した対称鍵は、復号APIを使用して復号した後に使用できます。
```text
POST https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/symmetric-keys/{keyid}/create-local-key
```

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "localKeyPlaintext": "srV7MWkYIfYBknkASzwSEK1Z1y9Nx0f/RMZ3MSVIjm8=",
        "localKeyCiphertext": "v1s1WkiIj3KR+AafnupNv9xcX/JhL4GUzUr8mzLRpjbGuoAwU/GgboM/6QdRRY24",
        "keyVersion": 1
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| localKeyPlaintext | String | Base64エンコードしたAES-256対称鍵 |
| localKeyCiphertext | String | Secure Key Managerに保存した対称鍵で暗号化した後、Base64エンコードしたAES-256対称鍵 |
| keyVersion | Number | APIリクエスト処理に使用した対称鍵バージョン |

### 対称鍵照会

Secure Key Managerに保存した対称鍵(AES-256)を照会できます。

```text
GET https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/symmetric-keys/{keyid}/symmetric-key?keyVersion={keyVersion}
```

[Request Parameter]

| 名前 | タイプ | 説明 |
|---|---|---|
| keyVersion | Number | 照会する対称鍵のバージョン |

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "symmetricKey": "0x00, 0x20, 0x00, 0x41, 0x00, 0x20, 0x00, 0x73, 0x00, 0x69, 0x00, 0x6d, 0x00, 0x70, 0x00, 0x6c, 0x00, 0x65, 0x00, 0x20, 0x00, 0x4a, 0x00, 0x61, 0x00, 0x76, 0x00, 0x61, 0x00, 0x2e, 0x00, 0x20",
        "keyVersion": 1
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| symmetricKey | String | 対称鍵データ(16進数文字列形式) |
| keyVersion | Number | APIリクエスト処理に使用した対称鍵バージョン |

## 非対称鍵

### 非対称鍵で署名
Secure Key Managerに作成した非対称鍵で、データを署名する時に使用します。ユーザーは245Byte以下のテキストデータを転送して、Secure Key Managerに保存した非対称鍵で署名できます。
```text
POST https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/asymmetric-keys/{keyid}/sign
```

[Request Body]
```
{
    "plaintext": "data"
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| plaintext | String | 非対称鍵で署名するデータ |

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "signature": "AAAAAGI9zf831DX...",
        "keyVersion": 1
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| signature | String | 非対称鍵でデータを署名した署名値 |
| keyVersion | Number | APIリクエスト処理に使用した非対称鍵バージョン |

### 非対称鍵でデータ検証
Secure Key Managerに作成した非対称鍵で、データを検証する時に使用します。ユーザーはデータと署名値を転送して、Secure Key Managerに保存した非対称鍵でデータが改ざんされていないかを検証できます。
```text
POST https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/asymmetric-keys/{keyid}/verify
```

[Request Body]

```
{
    "plaintext": "data",
    "signature": "AAAAAGI9zf831DX..."
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| plaintext | String | 非対称鍵で検証するデータ |
| signature | String | 非対称鍵でデータを署名した署名値 |

[Response Body]

```
{
    "header": {
        ...
    },
    "body": {
        "result": true,
        "keyVersion": 1
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| result | Boolean | 非対称鍵でデータと署名値を検証した結果 |
| keyVersion | Number | APIリクエスト処理に使用した非対称鍵バージョン |

### 秘密鍵照会

Secure Key Managerに保存した非対称鍵のうち、秘密鍵を照会できます。

```text
GET https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/asymmetric-keys/{keyid}/privateKey?keyVersion={keyVersion}
```

[Request Parameter]

| 名前 | タイプ | 説明 |
|---|---|---|
| keyVersion | Number | 照会する非対称鍵のバージョン |

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "keyType": "PrivateKey",
        "key": "0x30, 0x82, 0x04, 0xbe, 0x02, 0x01, 0x00, 0x30, 0x0d, 0x06, 0x09, 0x2a, 0x86, 0x48, 0x86, 0xf7, 0x0d, 0x01, 0x01, 0x01, 0x05, 0x00, 0x04, 0x82, 0x04, 0xa8, 0x30, 0x82, 0x04, 0xa4, 0x02, 0x01, 0x00, 0x02, 0x82, 0x01, 0x01, 0x00, 0x8b, 0x07, 0x8e, 0xda, 0xc7, 0x83, 0x95, 0xc8, 0x43, 0xa7, 0xb8, 0x31, 0x6f, 0xf6, 0x25, 0x36, 0x89, 0x64, 0xc5, 0x38, 0x75, 0x4b, 0xa6, 0x80, 0xfe, 0x7c, 0xc5, 0x6a, 0x94, 0xf2,
                ... 後略 ...",
        "encodedKey": "MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQCLB47ax4OVyEOnuDFv9iU2iWTFOHVLpoD+fMVqlPJiiuJSwi5x/zd3LojWuUyr+dZ9Icxl23Alu4GwwKgUi4DL8qo8jD14THJoeUgIZ56wmYMvN+CkNnmkyqcGn6yT+AXtBJVGqS/2lssHLIGELi8XXkWdf6OBfig6HgsJAnix8Z+T/QdikEFUI5ZiuUWyHw2Bag9B4CoPF2EgXfu5HcW4GA4KH2PI92O4vNg8AmFVDk2E+ma2quSau7LjS3KY9s3Sq+JqvTPZmqHQJudv9ZYcnbyDG/
                       ... 後略 ...",
        "keyVersion": 0
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyType | String | 非対称鍵形式 |
| key | String | 秘密鍵データ(16進数文字列形式) |
| encodedKey | String | 秘密鍵データ(Base64エンコード形式) |
| keyVersion | Number | APIリクエスト処理に使用した非対称鍵のバージョン |

### 公開鍵照会

Secure Key Managerに保存した非対称鍵のうち、公開鍵を照会できます。
認証に関係なく照会できます。

```text
GET https://api-keymanager.nhncloudservice.com/keymanager/v1.2/appkey/{appkey}/asymmetric-keys/{keyid}/publicKey?keyVersion={keyVersion}
```

[Request Parameter]

| 名前 | タイプ | 説明 |
|---|---|---|
| keyVersion | Number | 照会する非対称鍵のバージョン |

[Response Body]
```
{
    "header": {
        ...
    },
    "body": {
        "keyType": "PublicKey",
        "key": "0x30, 0x82, 0x01, 0x22, 0x30, 0x0d, 0x06, 0x09, 0x2a, 0x86, 0x48, 0x86, 0xf7, 0x0d, 0x01, 0x01, 0x01, 0x05, 0x00, 0x03, 0x82, 0x01, 0x0f, 0x00, 0x30, 0x82, 0x01, 0x0a, 0x02, 0x82, 0x01, 0x01, 0x00, 0x8b, 0x07, 0x8e, 0xda, 0xc7, 0x83, 0x95, 0xc8, 0x43, 0xa7, 0xb8, 0x31, 0x6f, 0xf6, 0x25, 0x36, 0x89, 0x64, 0xc5, 0x38, 0x75, 0x4b, 0xa6, 0x80, 0xfe, 0x7c, 0xc5, 0x6a, 0x94, 0xf2, 0x62, 0x8a, 0xe2, 0x52, 0xc2,
                ... 後略 ...",
        "encodedKey": "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAiweO2seDlchDp7gxb/YlNolkxTh1S6aA/nzFapTyYoriUsIucf83dy6I1rlMq/nWfSHMZdtwJbuBsMCoFIuAy/KqPIw9eExyaHlICGeesJmDLzfgpDZ5pMqnBp+sk/gF7QSVRqkv9pbLByyBhC4vF15FnX+jgX4oOh4LCQJ4sfGfk/0HYpBBVCOWYrlFsh8NgWoPQeAqDxdhIF37uR3FuBgOCh9jyPdjuLzYPAJhVQ5NhPpmtqrkmruy40tymPbN0qviar0z2Zqh0Cbnb/WWHJ28gxv+d+iJCXJvm+fIg7hRYJ5C+mun/N6FB8QHv/
                       ... 後略 ...",
        "keyVersion": 0
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyType | String | 非対称鍵形式 |
| key | String | 公開鍵データ(16進数文字列形式) |
| encodedKey | String | 公開鍵データ(Base64エンコード形式) |
| keyVersion | Number | APIリクエスト処理に使用した非対称鍵のバージョン |

## キーの追加/削除

### キーの追加
Secure Key Managerに新規キーを追加できます。

#### 機密データの追加
```text
POST https://api-keymanager.nhncloudservice.com/keymanager/v1.0/appkey/{appkey}/keys/secrets/create
```

[Request Body]

```
{
    "keyStoreName" : "Store #1",
    "name" : "Key Sample #1",
    "description" : "Description #1",
    "secretValue" : "data"
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyStoreName | String | キーを保存するキーストア名 |
| name | String | キー名 |
| description | String | キーの説明 |
| secretValue | String | 機密データ値 |

[Response Body]

```
{
    "header": {
        ...
    },
    "body": {
        "keyId": "071dcc5c25614dffa52357e5cae3471f",
        "keyStatus": "ACTIVE"
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyId | String | 作成されたキーID |
| keyStatus | String | キーの状態メッセージ |

#### 対称鍵の追加
```text
POST https://api-keymanager.nhncloudservice.com/keymanager/v1.0/appkey/{appkey}/keys/symmetric-key/create
```

[Request Body]

```
{
    "keyStoreName" : "Store #1",
    "name" : "Key Sample #2",
    "description" : "Description #2",
    "autoRotationPeriod" : 0
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyStoreName | String | キーを保存するキーストア名 |
| name | String | キー名 |
| description | String | キーの説明 |
| autoRotationPeriod | Integer | ローテーション周期 |

[Response Body]

```
{
    "header": {
        ...
    },
    "body": {
        "keyId": "c2c49d986dfb4ca6afeaf67c39354c12",
        "keyStatus": "ACTIVE"
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyId | String | 作成されたキーID |
| keyStatus | String | キーの状態メッセージ |

#### 非対称鍵の追加
```text
POST https://api-keymanager.nhncloudservice.com/keymanager/v1.0/appkey/{appkey}/keys/asymmetric-key/create
```

[Request Body]

```
{
    "keyStoreName" : "Store #1",
    "name" : "Key Sample #3",
    "description" : "Description #3",
    "autoRotationPeriod" : 0
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyStoreName | String | キーを保存するキーストア名 |
| name | String | キー名 |
| description | String | キーの説明 |
| autoRotationPeriod | Integer | ローテーション周期 |

[Response Body]

```
{
    "header": {
        ...
    },
    "body": {
        "keyId": "ddd7d5275dfa462799418062bd25b49d",
        "keyStatus": "ACTIVE"
    }
}
```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyId | String | 作成されたキーID |
| keyStatus | String | キーの状態メッセージ |

### キーの削除
Secure Key Managerに保存されたキーの状態を**削除予定**状態に変更したり、**即時削除**できます。

#### キー削除リクエスト
キーを**削除予定**状態に変更します。
キーは7日後に自動的に削除され、**削除予定**状態のキーは照会できません。
```text
PUT https://api-keymanager.nhncloudservice.com/keymanager/v1.0/appkey/{appkey}/keys/{keyid}/delete
```

[Response Body]

```
{
    "header": {
        ...
    },
    "body": {
        "keyId": "071dcc5c25614dffa52357e5cae3471f",
        "deletionDateTime": "2023-11-20T22:00:00.00"
    }
}

```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyId | String | 作成されたキーID |
| deletionDateTime | String | キーの削除予定日 |

#### キーの即時削除
**即時削除**するキーは**削除予定**状態の時のみ**即時削除**が可能です。
有効状態のキーは**即時削除**できません。
```text
DELETE https://api-keymanager.nhncloudservice.com/keymanager/v1.0/appkey/{appkey}/keys/{keyid}
```

[Response Body]

```
{
    "header": {
        ...
    },
    "body": {
        "keyId": "071dcc5c25614dffa52357e5cae3471f",
        "deletionDateTime": "2023-11-14T10:05:24.312"
    }
}

```
| 名前 | タイプ | 説明 |
|---|---|---|
| keyId | String | 作成されたキーID |
| deletionDateTime | String | キーの削除時刻 |
