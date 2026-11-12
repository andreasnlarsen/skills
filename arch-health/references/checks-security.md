# Security

Aligned with OWASP Top 10 where applicable.

---

## SEC-01: Broken Access Control (OWASP A01)

**What:** Users can access resources or perform actions beyond their intended permissions.
**Detection:** static — check for authorization checks on every endpoint. Look for missing role/permission checks, direct object reference without ownership validation, an access model that fails to enforce the required permissions.
**Possible correction:** Enforce deny-by-default authorization with ownership checks on every protected path; test reachable unauthorized cases.

## SEC-02: Security Misconfiguration (OWASP A05)

**What:** Default configs, unnecessary features enabled, missing security headers, verbose error messages.
**Detection:** static — check for security headers (CSP, X-Frame-Options, X-Content-Type-Options, Referrer-Policy). Check for debug mode in production config. Check for default credentials.
**Possible correction:** Add security headers via middleware, disable debug mode and remove default credentials in production; tune policy values to the deployment.

## SEC-03: Supply Chain (OWASP A06)

**What:** Vulnerable or compromised dependencies, missing integrity checks.
**Detection:** dynamic — `npm audit` / `pip audit` / `cargo audit` / `gh api /repos/{owner}/{repo}/dependabot/alerts`. Static — check for lock file, Dependabot/Renovate config, subresource integrity for CDN scripts.
**Possible correction:** Update or mitigate the affected version once reachable exposure is established; enable Dependabot/Snyk scanning when it closes a detection gap.

## SEC-04: Cryptographic Failures (OWASP A02)

**What:** Weak cryptography, plaintext sensitive data, missing encryption.
**Detection:** static — search for weak algorithms (MD5, SHA1 for passwords, DES, RC4). Check for plaintext password storage. Look for hardcoded encryption keys. Check HTTPS usage.
**Possible correction:** Use bcrypt/argon2 for passwords, authenticated encryption (AES-GCM) and HTTPS; correct key storage through the credential owner.

## SEC-05: Injection (OWASP A03)

**What:** SQL injection, NoSQL injection, command injection, XSS via unsanitized input.
**Detection:** static — search for string concatenation in queries, dynamic code evaluation, raw HTML rendering without sanitization, raw SQL with user input, shell command construction with unescaped user input.
**Possible correction:** Use parameterized queries, structured process arguments and DOMPurify for accepted HTML; an ORM does not make raw queries safe.

## SEC-06: CORS Configuration

**What:** CORS settings expose browser-readable responses to unintended origins.
**Detection:** static — search for CORS configuration. Compare wildcard or reflected origins and credential behavior with the intended public/private response contract.
**Known failure:** CORS `*` with credentials.
**Possible correction:** Set an explicit origin allowlist with credentials only for intended callers; public unauthenticated data may allow a wildcard.

## SEC-07: Secrets in Source

**What:** API keys, tokens, passwords, private keys committed to the repository.
**Detection:** static — search for patterns: long base64 strings, cloud provider key prefixes, private key headers, password/secret/token assignments with literal string values.
**Known failure:** Any secret literal in source.
**Possible correction:** Remove and rotate through the authorized credential workflow, never reproducing the value; add a gitleaks pre-commit hook when recurrence is likely.

## SEC-08: Authentication Mechanism

**What:** Weak or flawed authentication implementation.
**Detection:** static — check for password hashing algorithm, session management, JWT configuration (algorithm, expiry, secret strength), MFA support for admin accounts.
**Known failure:** JWT `none` algorithm accepted.
**Possible correction:** Fix the specific weakness in the existing session or token model: slow hashing (bcrypt/argon2) for passwords, a strong algorithm and short expiry for tokens, MFA for admin access.

## SEC-09: Input Validation at Boundaries

**What:** Missing or insufficient input validation at system boundaries (API endpoints, form handlers, file uploads).
**Detection:** static — check for validation middleware on API routes. Look for unchecked file uploads (type, size), missing request body size limits, unvalidated URL parameters.
**Possible correction:** Validate shape, bounds and permissions with a schema library (zod, joi, pydantic) and set upload and body size limits when a boundary lacks them.

## SEC-10: Security Logging

**What:** Missing audit trail for security-relevant events.
**Detection:** static — check if auth events (login, logout, failed login, password change), authorization failures, and admin actions are logged.
**Possible correction:** Log auth events, authorization failures and admin actions with user ID, IP and timestamp; never log passwords or tokens.
