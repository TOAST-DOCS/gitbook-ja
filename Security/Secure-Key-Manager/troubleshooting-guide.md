## Security > Secure Key Manager > 問題解決ガイド
Secure Key Managerを使用中に発生することがある主な問題に対する解決方法を説明します。

### APIの呼び出しが失敗し、Invalid Appkeyエラーメッセージが返されます。
* APIの呼び出しに使用したアプリケーションキーが無効な時に発生します。
    * Secure Key Manager管理ページのURL & Appkeyウィンドウに表示される正しいアプリケーションキーを使用しているかを確認してください。

### APIの呼び出しが失敗し、Invalid Key Idエラーメッセージが返されます。
* APIの呼び出しに使用したKey Idが無効な時に発生します。
    * 正しいKey Idを使用しているかを確認してください。
    * Keyが使用中の状態かを確認してください。
    
### APIの呼び出しが失敗し、Invalid Key Versionエラーメッセージが返されます。
* APIの呼び出しに使用したKey Versionが無効な時に発生します。
    * 対称鍵復号APIで発生した場合、暗号化した時に使用していた鍵バージョンが存在するかを確認してください。
    * 非対称鍵検証APIで発生した場合、署名した時に使用していた鍵バージョンが存在するかを確認してください。

### APIの呼び出しが失敗し、Invalid User Dataエラーメッセージが返されます。
* APIの呼び出しに使用したユーザーデータが無効な時に発生します。
    * 対称鍵復号APIで発生した場合、復号対象データが正しいかを確認してください。
    * 非対称鍵検証APIで発生した場合、署名値が正しいかを確認してください。

### APIの呼び出しが失敗し、Invalid Key Statusエラーメッセージが返されます。
* APIの呼び出しに使用したKeyの状態が無効な時に発生します。
    * 対称鍵復号APIで発生した場合、暗号化した時に使用した鍵が'使用中'の状態かを確認してください。
    * 非対称鍵検証APIで発生した場合、署名した時に使用していた鍵が'使用中'の状態かを確認してください。

### APIの呼び出しが失敗し、Invalid Key Version Statusエラーメッセージが返されます。
* APIの呼び出しに使用したKey Versionの状態が無効な時に発生します。
    * 対称鍵復号APIで発生した場合、暗号化した時に使用していた鍵バージョンが'使用中'の状態かを確認してください。
    * 非対称鍵検証APIで発生した場合、署名した時に使用していた鍵バージョンが'使用中'の状態かを確認してください。
    
### APIの呼び出しが失敗し、IPv4 Auth Failureエラーメッセージが返されます。
* IPv4アドレス認証に失敗した時に発生します。
    * APIを呼び出すクライアントのIPv4アドレスをSecure Key Managerに登録したかを確認してください。
    * Secure Key Managerに登録したクライアントのIPv4アドレスが'使用中'の状態かを確認してください。

### APIの呼び出しが失敗し、MAC Auth Failureエラーメッセージが返されます。
* MACアドレス認証に失敗した時に発生します。
    * APIを呼び出すクライアントのMACアドレスをSecure Key Managerに登録しているかを確認してください。
    * Secure Key Managerに登録したクライアントのMACアドレスが'使用中'の状態かを確認してください。
    * APIを呼び出す時、X-TOAST-CLIENT-MAC-ADDRリクエストヘッダにクライアントのMACアドレスを追加したかを確認してください。

### APIの呼び出しが失敗し、Certificate Auth Failureエラーメッセージが返されます。
* クライアント証明書の認証に失敗した時に発生します。
    * Secure Key Managerで発行した証明書を使用しているかを確認してください。
    * Secure Key Managerに登録した証明書が'使用中'の状態かを確認してください。

### APIの呼び出しが失敗し、証明書関連エラーメッセージが返されます。
* 証明書が不正な時に発生します。
    * Secure Key Managerで発行した証明書を使用しているかを確認してください。
    * 証明書の有効期限を確認してください。
    
##### その他のAPIリクエスト中に発生したエラーについては、サポート([support@toast.com](mailto:support@toast.com))へお問い合わせください。