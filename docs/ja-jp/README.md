# Macareux Digitalのコーディング・スタンダード
## PHPのためのクリーンコードの概念

これは個人の好みの問題だと思います。コードがきれいなときは？そうでないときは？これは一概には言えませんが、コードを改善するための一般的なガイドラインはいくつかあります。以下に、私が使用している参考文献を紹介します。

### 👉[公式ドキュメント](https://documentation.concretecms.org/developers/appendix/coding-style-guidelines)

Concrete CMS の[公式ドキュメント](https://documentation.concretecms.org/developers/appendix/coding-style-guidelines)に従ってください。

### 👉[クリーンコード PHP](https://github.com/jupeter/clean-code-php) 
[Clean Code PHP](https://github.com/jupeter/clean-code-php) は、名著「Clean Code: A Handbook of Agile Software Craftsmanship」に基づくガイドです。著者は[Uncle Bob Martin](https://twitter.com/unclebobmartin)。保守しやすいコードを書くための基本が学べるため、必読のガイドラインとして強く推奨します。

### 👉[PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)

IDE 連携などの詳細は[公式ドキュメント](https://cs.symfony.com/)を参照してください。また、Concrete CMS には（8.5.3 以降）これを利用するためのコマンドが用意されています。`./concrete/bin/concrete5 c5:phpcs --help` を実行して詳細を確認できます。

### 👉ヒントとコツ

- PHP でクリーンコードを書くための資料: [Clean Code In PHP](https://github.com/jupeter/clean-code-php)
- よりクリーンに書くための [PHP 8 のコツ](https://latteandcode.medium.com/php-8-tricks-that-will-help-you-write-cleaner-code-374c71daffb6)

## Package development

### 👉[Basic Requirements](https://documentation.concretecms.org/developers/packages/overview)

パッケージを作る際の基本的な条件は以下の通りです。

- すべてのフォーム、Ajax リクエスト、重要なアクションに CSRF トークン検証を追加する（[Security & XSS Protection](security.md) を参照）。
- コントローラにフォーム入力のバリデーションを追加する。
- ビューに基本的な HTML 検証を追加する。JavaScript による検証があるとなお良い。  
- データベースに保存する前に入力をサニタイズする（[Security & XSS Protection](security.md) を参照）。
- 出力変数をサニタイズする（[Security & XSS Protection](security.md) を参照）。
- 取り消せない操作には[確認ダイアログ](https://documentation.concretecms.org/tutorials/how-to-create-alert-notifications-and-modals)を追加する。
- `controllers` と `views` は可能な限りスリムに保つ。必要ならクラスやエレメントを新規作成する。重複を避けるために [Traits](https://www.php.net/manual/en/language.oop5.traits.php) を活用する。
- [README.md](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/about-readmes) と [CHANGELOG.md](https://changelog.md) を用意する。[https://www.makeareadme.com](https://www.makeareadme.com) や [https://keepachangelog.com](https://keepachangelog.com) も参考に。
- コントローラでエイリアスを使用しない。
- [非推奨コード](https://documentation.concretecms.org/developers/appendix/deprecated-code-reference-ongoing)を使用しない。
- [スタイルガイド](https://documentation.concretecms.org/developers/appendix/style-guide)に従う。
- プロジェクトの PHP バージョン互換性に基づいて最新の文法で記述する（例: 可能な限り[型宣言](https://www.php.net/manual/en/language.types.declarations.php)を使用）。互換性は[こちらの一覧](https://mlocati.github.io/articles/php-type-hinting.html)が参考になります。


### 👉[Block Types](https://documentation.concretecms.org/developers/working-with-blocks)


### 👉[Config](https://documentation.concretecms.org/developers/framework/configuration-and-keyvalue-storage/storing-configuration-values)

- コンテンツ（ブロックタイプ、シングルページ、Express オブジェクト等）は、[プログラム的に](https://documentation.concretecms.org/developers/packages/programmatically-creating-composer-forms-and-controls)または [CIF](https://documentation.concretecms.org/developers/packages/concrete5-cif-format-1) を使ってインストールできます。一般的には `CIF` の利用を推奨します。
- 可能であればサンプルの設定ファイルを同梱する（例: `example.concrete.php`）。


### 👉[Routes](https://documentation.concretecms.org/developers/framework/routing/introduction)

- ルート登録は[公式ガイド](https://documentation.concretecms.org/developers/framework/routing/including-routes-in-packages)に従う。

### 👉[Single Pages](https://documentation.concretecms.org/developers/pages-themes/working-with-pages/single-pages/overview)

- コントローラとページビュー間でのデータの受け渡しは[公式ガイド](https://documentation.concretecms.org/developers/pages-themes/working-with-pages/single-pages/sending-data-to-a-page-view)を参照。不要な Ajax の使用は避ける。

### 👉[MyPackage](https://github.com/biplobice/MyPackage)

パッケージ開発の出発点として、このスケルトンパッケージを作りました。ここからアイデアを得ることができます。このリポジトリを改善するためのプルリクエストもご自由にどうぞ。

## Performance
- 重複した MySQL クエリを避ける。
- 性能向上のために[オブジェクトキャッシュ](https://documentation.concretecms.org/developers/framework/caching/overview)を活用する。


## Test
- パッケージのテストには [PHPUnit](https://phpunit.de/) を用いる。


## Documentation
- DocBlock に[phpDocumentor のタグ](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.pkg.html)を追加する。
- [phpDocumentor](https://www.phpdoc.org/) で PHP コードのドキュメントを生成する。
- [ApiDocJS](https://apidocjs.com/) で REST API のドキュメントを生成する。