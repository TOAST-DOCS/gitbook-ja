## Notification > KakaoTalk Bizmessage > 問題解決ガイド

### 配送照会ボタン文言

カカオメッセージに運送会社名と送り状番号を記載し、配送照会ボタンを追加すると、メッセージ内容から運送会社名と送り状番号を抽出して、各運送会社が提供する照会ページへのリンクが自動的に作成されます。カカオでサポートしていない運送会社と送り状番号がメッセージに含まれる場合は、配送照会ボタンが露出されません。

配送照会ボタンをサポートする運送会社リストは下記の通りです。

カカオトークで配送照会可能な運送会社リスト:

KGB택배 우체국택배 로젠택배 일양로지스 GTX로지스 FedEx 한진택배 경동택배 합동택배 롯데택배 농협택배 호남택배 CU 편의점택배 CVSnet편의점택배 TNT Express USPS EMS 천일택배 DHL 대신택배 건영택배 한덱스

<span style="color:red">**このリストは、カカオと各運送会社の契約に応じて変動する場合があります。**</span>
<b>CJ대한통운</b>
* 카카오 비즈메시지의 배송조회 버튼 관련 변경으로 인해, 메시지 내 CJ대한통운 송장번호가 포함된 경우, '배송조회' 버튼 없이 발송됩니다.(추후 카카오에서 변경 시, 재공지)

運送会別社送り状番号形式

```
우체국택배: 数字 13席 または 数字 6席 + 数字 7席(区切り記号 '-' または '_')
例示) 1234567890123, 123456-1234567, 123456_1234567

로젠택배: 数字 11席 または 数字 3席 + 数字 4席 + 数字 4席(区切り記号 '-' または '_'))
例示) 12345678901, 123-1234-1234, 123_1234_1234

일양로지스: 数字 9~11席
例示) 123456789, 1234567890, 12345678901

FedEx: 数字 12席
例示) 123456789012

한진택배: 数字 10席 または 数字 12席
例示) 1234567890, 123456789012

경동택배: 数字 9~16席 または 数字 4席 + 数字 3席 + 数字 6席(区切り記号 '-')
例示) 123456789, 1234567890123456, 1234-123-123456

합동택배: 数字 9~16席
例示) 123456789, 1234567890123456

롯데택배: 数字 12席 または 数字 4席 + 数字 4席 + 数字 4席(区切り記号 '-')
例示) 123456789012, 1234-1234-1234

농협택배: 数字 12席
例示) 123456789012

호남택배: 数字 10席
例示) 1234567890

천일택배: 数字 11席
例示) 12345678901

대신택배: 数字 13席
例示) 1234567890123

건영택배: 数字 10席
例示) 1234567890

CU편의점택배: 数字 10席 または 数字 12席 または 数字 4席 + 数字 4席 + 数字 4席(区切り記号 '-' または '_')
例示) 1234567890, 123456789012, 1234-1234-1234, 1234_1234_1234

CVSnet편의점택배: 数字 10席 または 数字 12席 または 数字 4席 + 数字 4席 + 数字 4席(区切り記号 '-' または '_')
例示) 1234567890, 123456789012, 1234-1234-1234, 1234_1234_1234

한덱스: 数字 10席 または 数字 14席
例示) 1234567890, 12345678901234

TNT Express: 数字 8~9席
例示) 12345678, 123456789

USPS: 数字 10席 または 数字 22席 または 大文字 アルファベット 2席 + 数字 9席 + 大文字 アルファベット 2席(区切り記号 無い)
例示) 1234567890, 1234567890123456789012, AB123456789AB

EMS: 大文字 アルファベット 2席 + 数字 9席 + 大文字 アルファベット 2席(区切り記号 無い)
例示) AB1234567890AB

DHL: 数字 10席
例示) 1234567890

굿투럭: 数字 4席 + 数字 4席 + 数字 4席(区切り記号 '-')
예시) 1234-1234-1234
```
