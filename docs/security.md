# Security & XSS Protection

Security is very important to concrete5.

As a developer who uses concete5 to build web applications, you'll need to ensure that your code is secure. Fortunately, concrete5 contains a number of helper libraries and functions to ensure writing secure code is possible and easy to do.

- Protect Against Cross-Site Request Forgery with the [Token Validation Library](https://documentation.concrete5.org/developers/security/protecting-against-csrf-with-token-validation).
- Protect Against Cross-Site-Scripting with [Output Filtering and Sanitization](https://documentation.concrete5.org/developers/security/protecting-against-xss-with-output-sanitization).
- Use [concrete API](https://documentation.concrete5.org/developers/security/guarding-against-sql-injection) or [doctrine placeholders](https://www.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/query-builder.html#security-safely-preventing-sql-injection) to guard against [SQL injection](https://en.wikipedia.org/wiki/SQL_injection).
- [Validate file uploads](https://documentation.concrete5.org/developers/security/validating-file-uploads).
- [Sanitize](https://documentation.concrete5.org/developers/security/sanitizing-user-input) user inputs.
- [Encrypt](https://documentation.concrete5.org/developers/security/encryption-service) sensitive data.
- Use [Anti-spam & Captcha](https://documentation.concrete5.org/developers/security/anti-spam-and-captcha) in public forms.


