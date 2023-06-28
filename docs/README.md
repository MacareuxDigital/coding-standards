# Macareux Digital Coding Standards
## Clean Code Concepts for PHP

I think this is a matter of personal taste. When is the code clean? When is it not? This is hard to say, but there are some general guidelines which you can follow to help improve your code. Below I have given the references that I use, and they have helped me so far.

### 👉[Official Documentation](https://documentation.concrete5.org/developers/appendix/coding-style-guidelines)

Follow the concrete5 [official documentation](https://documentation.concrete5.org/developers/appendix/coding-style-guidelines).

### 👉[Clean Code PHP](https://github.com/jupeter/clean-code-php) 
Clean Code PHP([jupeter/clean-code-php](https://github.com/jupeter/clean-code-php)), is a guide based on the book Clean Code: A Handbook of Agile Software Craftmanship, a classic programming book about writing maintainable code by [Uncle Bob Martin](https://twitter.com/unclebobmartin). I recommend this as a `Must Read` guideline.

### 👉[PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)

Check their [official documentation](https://cs.symfony.com/) to integrate with your IDE. Also, concrete5 has a command (from 8.5.3) to use it. Please run `./concrete/bin/concrete5 c5:phpcs --help` for detail.

### 👉Tips & Tricks

- Writing [Clean Code In PHP](https://stackcoder.in/posts/writing-clean-code-in-php).
- [PHP 8 tricks](https://latteandcode.medium.com/php-8-tricks-that-will-help-you-write-cleaner-code-374c71daffb6) that will help you write cleaner code.

## Package development

### 👉[Basic Requirements](https://documentation.concrete5.org/developers/packages/overview)

The followings are the basic requirements when you make a package-

- Add token validation to all form, ajax request and important actions. See [Security & XSS Protection](security.md).
- Add form input validation to the controller.
- Add basic HTML validation to the view. Javascript validation would be plus.  
- Sanitize input before saving into the database. See [Security & XSS Protection](security.md).
- Sanitize output variables. See [Security & XSS Protection](security.md).
- Add a [confirmation dialog](https://documentation.concrete5.org/tutorials/how-to-create-alert-notifications-and-modals) to non-returnable actions.
- Try to keep your `controllers` and `views` slim as much as possible. Don't hesitate to create a new class or element. Use [Traits](https://www.php.net/manual/en/language.oop5.traits.php) to avoid code repeat.
- Please use [semantic versioning](https://semver.org/).
- Add [README.md](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/about-readmes) & [CHANGELOG.md](https://changelog.md) files. You may use [https://www.makeareadme.com](https://www.makeareadme.com) to make a README file. And [https://keepachangelog.com](https://keepachangelog.com) to make a changelog.
- Don't use aliases in controller.
- Don't use [deprecated codes](https://documentation.concrete5.org/developers/appendix/deprecated-code-reference-ongoing).
- Follow the [style guide](https://documentation.concrete5.org/developers/appendix/style-guide).
- Write PHP codes with updated syntax based on the project version compatibility. e.g., Use [Type Declarations](https://www.php.net/manual/en/language.types.declarations.php) as much as possible. You may check [this list](https://mlocati.github.io/articles/php-type-hinting.html) to know about PHP version compatibility.
- Use `md_` as a prefix of our packages handle.


### 👉[Block Types](https://documentation.concrete5.org/developers/working-with-blocks)


### 👉[Config](https://documentation.concrete5.org/developers/framework/configuration-and-keyvalue-storage/storing-configuration-values)

- Contents (Block Types, Single Pages, Express Objects etc.) can be installed [Programmatically](https://documentation.concrete5.org/developers/packages/programmatically-creating-composer-forms-and-controls) or using [CIF](https://documentation.concrete5.org/developers/packages/concrete5-cif-format-1) files. `CIF` is the recommended way to use.
- Add an example config file (if any). e.g., `example.concrete.php`


### 👉[Routes]((https://documentation.concrete5.org/developers/framework/routing/introduction) )

- Follow the [official guide](https://documentation.concrete5.org/developers/framework/routing/including-routes-in-packages) to register routes.

### 👉[Single Pages](https://documentation.concrete5.org/developers/pages-themes/working-with-pages/single-pages/overview)

- Follow the [official guide](https://documentation.concrete5.org/developers/pages-themes/working-with-pages/single-pages/sending-data-to-a-page-view) to send data to and from a controller into the page view. Please avoid using ajax unnecessarily.

### 👉[MyPackage](https://github.com/biplobice/MyPackage)

I've created this skeleton package  as a starting point to develop packages. You can get ideas from here. Feel free to make a pull request to improve this repository.

## Performance
- Avoid duplicate MySQL queries.
- Use [Object Caching](https://documentation.concrete5.org/developers/framework/caching/overview) to improve performance.


## Test
- Write [PHPUnit](https://phpunit.de/) tests to test your package.


## Documentation
- Add [phpDocumentor tags](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.pkg.html) in DocBlocks.
- Use [phpDocumentor](https://www.phpdoc.org/) to generate the PHP code documentation.
- Use [ApiDocJS](https://apidocjs.com/) to generate the REST api doc.
