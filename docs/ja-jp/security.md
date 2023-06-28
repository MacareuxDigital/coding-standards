# セキュリティとXSS対策

concrete5にとってセキュリティは非常に重要です。

ウェブアプリケーションを構築するためにconcete5を使用する開発者として、コードの安全性を確保する必要があります。幸いなことに、concrete5には、安全なコードを書くことが可能で、簡単にできるようにするためのヘルパーライブラリや関数が数多く含まれています。

- クロスサイト・リクエスト・フォージェリからの保護のために [トークン検証ライブラリ](https://documentation.concrete5.org/developers/security/protecting-against-csrf-with-token-validation).
- クロスサイトスクリプティングからの保護 [出力のフィルタリングとサニタイズ](https://documentation.concrete5.org/developers/security/protecting-against-xss-with-output-sanitization).
- 使用 [concrete API](https://documentation.concrete5.org/developers/security/guarding-against-sql-injection) or [doctrine placeholders](https://www.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/query-builder.html#security-safely-preventing-sql-injection) から守るために [SQLインジェクション](https://en.wikipedia.org/wiki/SQL_injection).
- [アップロードされたファイルの検証](https://documentation.concrete5.org/developers/security/validating-file-uploads).
- [サニタイズ](https://documentation.concrete5.org/developers/security/sanitizing-user-input) ユーザー入力。
- [暗号化](https://documentation.concrete5.org/developers/security/encryption-service) センシティブなデータ。
- 使用 [スパム対策とCaptcha](https://documentation.concrete5.org/developers/security/anti-spam-and-captcha) in public forms.


