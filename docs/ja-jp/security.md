# セキュリティとXSS対策

Concrete CMSにとってセキュリティは非常に重要です。

ウェブアプリケーションを構築するためにConcrete CMSを使用する開発者として、コードの安全性を確保する必要があります。幸いなことに、Concrete CMSには、安全なコードを書くことが可能で、簡単にできるようにするためのヘルパーライブラリや関数が数多く含まれています。

- クロスサイト・リクエスト・フォージェリからの保護のために [トークン検証ライブラリ](https://documentation.concretecms.org/developers/security/protecting-against-csrf-with-token-validation).
- クロスサイトスクリプティングからの保護 [出力のフィルタリングとサニタイズ](https://documentation.concretecms.org/developers/security/protecting-against-xss-with-output-sanitization).
- 使用 [Concrete CMS API](https://documentation.concretecms.org/developers/security/guarding-against-sql-injection) or [doctrine placeholders](https://www.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/query-builder.html#security-safely-preventing-sql-injection) から守るために [SQLインジェクション](https://en.wikipedia.org/wiki/SQL_injection).
- [アップロードされたファイルの検証](https://documentation.concretecms.org/developers/security/validating-file-uploads).
- [サニタイズ](https://documentation.concretecms.org/developers/security/sanitizing-user-input) ユーザー入力。
- [暗号化](https://documentation.concretecms.org/developers/security/encryption-service) センシティブなデータ。
- 使用 [スパム対策とCaptcha](https://documentation.concretecms.org/developers/security/anti-spam-and-captcha) in public forms.


