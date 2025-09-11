# Security & XSS Protection

Security is very important to Concrete CMS.

As a developer who uses Concrete CMS to build web applications, you'll need to ensure that your code is secure. Fortunately, Concrete CMS contains a number of helper libraries and functions to ensure writing secure code is possible and easy to do.

- Protect Against Cross-Site Request Forgery with the [Token Validation Library](https://documentation.concretecms.org/developers/security/protecting-against-csrf-with-token-validation).
- Protect Against Cross-Site-Scripting with [Output Filtering and Sanitization](https://documentation.concretecms.org/developers/security/protecting-against-xss-with-output-sanitization).
- Use [Concrete CMS API](https://documentation.concretecms.org/developers/security/guarding-against-sql-injection) or [doctrine placeholders](https://www.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/query-builder.html#security-safely-preventing-sql-injection) to guard against [SQL injection](https://en.wikipedia.org/wiki/SQL_injection).
- [Validate file uploads](https://documentation.concretecms.org/developers/security/validating-file-uploads).
- [Sanitize](https://documentation.concretecms.org/developers/security/sanitizing-user-input) user inputs.
- [Encrypt](https://documentation.concretecms.org/developers/security/encryption-service) sensitive data.
- Use [Anti-spam & Captcha](https://documentation.concretecms.org/developers/security/anti-spam-and-captcha) in public forms.






## 🔐 Security Guidelines for Local Development with Concrete CMS

### 🧱 Concrete CMS-Specific Security

#### 1. **Block & Controller Security**

- ✅ Use Concrete’s `Security`, `Request`, and `Database` classes for all input and data handling.
- ✅ Escape all output with `h()` or `$this->app->make('helper/text')->entities()`.
- ✅ Always implement CSRF tokens in custom forms.
- ❌ Never access `$_POST` or `$_GET` directly—use Concrete’s request objects.

#### 2. **Configuration Management**

- ❌ Never commit sensitive files like `application/config/database.php` to version control.
- ✅ Use environment variables or local config overrides for credentials.

---

## 🖥️ Local Server & File System Best Practices

### 1. **Backups & Sensitive Files**

- ❌ Never store backup files in public or any web-accessible directory.
- ❌ Avoid backup naming like `index.php.bak` or `index.php.20250625`—these may be executed if accessed.
    - ✅ Prefer names like `20250625_index.php` to prevent PHP execution.
- ✅ Store all backups outside the document root, ideally in a dedicated `backups` directory.

### 2. **File Permissions & Ownership**

- ✅ Set secure permissions: Files `644`, Directories `755`.
- ❌ Never use `777` permissions or run PHP/Apache as `root`.
- ✅ Ensure the web server runs as a restricted user (e.g., `apache`, `nginx`).

### 3. **Error Display & Logging**

- ❌ Never enable `display_errors` in production environments.
- ✅ Log errors to a secure, non-public directory outside the web root.

---

## 🌐 Network & Development Environment

### 1. **Database Handling**

- ❌ Never use production databases for local development.
- ✅ Use local databases with anonymized or dummy data.
- ✅ Store local DB credentials in files like `config/valet.database.php` (excluded from version control).

### 2. **Web Server Setup**

- ❌ Avoid installing unnecessary PHP modules—minimize the attack surface.
- ✅ Regularly update your local environment and dependencies.

---

**Tip:** Review Concrete CMS’s [official security documentation](https://documentation.concretecms.org/developers/security) for more best practices.
