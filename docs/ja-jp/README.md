# Macareux Digitalのコーディング・スタンダード
## PHPのためのクリーンコードの概念

これは個人の好みの問題だと思います。コードがきれいなときは？そうでないときは？これは一概には言えませんが、コードを改善するための一般的なガイドラインはいくつかあります。以下に、私が使用している参考文献を紹介します。

### 👉[公式ドキュメント](https://documentation.concrete5.org/developers/appendix/coding-style-guidelines)

Follow the concrete5 [公式ドキュメント](https://documentation.concrete5.org/developers/appendix/coding-style-guidelines).

### 👉[クリーンコード PHP](https://github.com/jupeter/clean-code-php) 
Clean Code PHP([jupeter/clean-code-php](https://github.com/jupeter/clean-code-php)), is a guide based on the book Clean Code: A Handbook of Agile Software Craftmanship, a classic programming book about writing maintainable code by [Uncle Bob Martin](https://twitter.com/unclebobmartin). I recommend this as a `Must Read` guideline.

### 👉[PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)

Check their [official documentation](https://cs.symfony.com/) to integrate with your IDE. Also, concrete5 has a command (from 8.5.3) to use it. Please run `./concrete/bin/concrete5 c5:phpcs --help` for detail.

### 👉ヒントとコツ

- Writing [Clean Code In PHP](https://github.com/jupeter/clean-code-php).
- [PHP 8 tricks](https://latteandcode.medium.com/php-8-tricks-that-will-help-you-write-cleaner-code-374c71daffb6) that will help you write cleaner code.

## Package development

### 👉[Basic Requirements](https://documentation.concrete5.org/developers/packages/overview)

パッケージを作る際の基本的な条件は以下の通りです。

- すべてのフォーム、ajaxリクエスト、重要なアクションにトークンの検証を追加しました。 See [Security & XSS Protection](security.md).
- コントローラにフォーム入力のバリデーションを追加します。
- 基本的なHTML検証をビューに追加します。Javascriptでの検証も可能です。  
- データベースに保存する前に入力内容を消毒する。 See [Security & XSS Protection](security.md).
- 出力変数のサニタイズ。 See [Security & XSS Protection](security.md).
- Add a [confirmation dialog](https://documentation.concrete5.org/tutorials/how-to-create-alert-notifications-and-modals) to non-returnable actions.
- Try to keep your `controllers` and `views` slim as much as possible. Don't hesitate to create a new class or element. Use [Traits](https://www.php.net/manual/en/language.oop5.traits.php) to avoid code repeat.
- Add [README.md](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/about-readmes) & [CHANGELOG.md](https://changelog.md) files. You may use [https://www.makeareadme.com](https://www.makeareadme.com) to make a README file. And [https://keepachangelog.com](https://keepachangelog.com) to make a changelog.
- コントローラーにエイリアスを使わない。
- Don't use [deprecated codes](https://documentation.concrete5.org/developers/appendix/deprecated-code-reference-ongoing).
- Follow the [style guide](https://documentation.concrete5.org/developers/appendix/style-guide).
- プロジェクトのバージョン互換性に基づいて、最新の構文でPHPコードを書く。 e.g., Use [Type Declarations](https://www.php.net/manual/en/language.types.declarations.php) as much as possible. You may check [this list](https://mlocati.github.io/articles/php-type-hinting.html) to know about PHP version compatibility.


### 👉[Block Types](https://documentation.concrete5.org/developers/working-with-blocks)


### 👉[Config](https://documentation.concrete5.org/developers/framework/configuration-and-keyvalue-storage/storing-configuration-values)

- Contents (Block Types, Single Pages, Express Objects etc.) can be installed [Programmatically](https://documentation.concrete5.org/developers/packages/programmatically-creating-composer-forms-and-controls) or using [CIF](https://documentation.concrete5.org/developers/packages/concrete5-cif-format-1) files. `CIF` is the recommended way to use.
- Add an example config file (if any). e.g., `example.concrete.php`


### 👉[Routes]((https://documentation.concrete5.org/developers/framework/routing/introduction) )

- Follow the [official guide](https://documentation.concrete5.org/developers/framework/routing/including-routes-in-packages) to register routes.

### 👉[Single Pages](https://documentation.concrete5.org/developers/pages-themes/working-with-pages/single-pages/overview)

- Follow the [official guide](https://documentation.concrete5.org/developers/pages-themes/working-with-pages/single-pages/sending-data-to-a-page-view) to send data to and from a controller into the page view. Please avoid using ajax unnecessarily.

### 👉[MyPackage](https://github.com/biplobice/MyPackage)

パッケージ開発の出発点として、このスケルトンパッケージを作りました。ここからアイデアを得ることができます。このリポジトリを改善するためのプルリクエストもご自由にどうぞ。

## Performance
- Avoid duplicate MySQL queries.
- Use [Object Caching](https://documentation.concrete5.org/developers/framework/caching/overview) to improve performance.


## Test
- Write [PHPUnit](https://phpunit.de/) tests to test your package.


## Documentation
- Add [phpDocumentor tags](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.pkg.html) in DocBlocks.
- Use [phpDocumentor](https://www.phpdoc.org/) to generate the PHP code documentation.
- Use [ApiDocJS](https://apidocjs.com/) to generate the REST api doc.