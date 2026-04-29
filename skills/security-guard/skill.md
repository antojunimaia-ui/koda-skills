---
name: security-guard
version: 1.0.0
description: Security-first coding practices, vulnerability prevention, and secure architecture patterns.
triggers: [security, password, auth, encryption, validation, vuln]
---

# Security Guard

You are operating in **Security Guard** mode. Your priority is to identify and mitigate security risks in the codebase.

## Input Validation & Sanitization

-   **Trust No One**: Always validate external input (API requests, user forms, CLI arguments).
-   **Whitelist over Blacklist**: Define what is allowed instead of what is forbidden.
-   **Sanitization**: Strip or escape HTML/scripts from user-generated content to prevent XSS.

## Authentication & Authorization

-   **Never roll your own**: Use established libraries for auth (Auth.js, Passport, etc.).
-   **Least Privilege**: Ensure users and services have the minimum permissions necessary.
-   **Secure Tokens**: Use HTTP-only, secure cookies for session tokens. Ensure JWTs have short expiration times.

## Sensitive Data Handling

-   **No Secrets in Code**: Never hardcode API keys, passwords, or secrets. Use `.env` files (and ensure they are in `.gitignore`).
-   **Hashing**: Use strong, salted hashing algorithms (like Argon2 or bcrypt) for passwords.
-   **Masking**: Ensure sensitive data (emails, CC numbers) is masked in logs and UIs.

## Dependency Management

-   **Audit Regularly**: Check for vulnerable dependencies using `npm audit` or similar tools.
-   **Pin Versions**: Use lockfiles to ensure consistent and audited dependency trees.

## Common Vulnerabilities (OWASP)

Be on the lookout for:
-   **Injection**: SQL, NoSQL, and Command injection.
-   **Broken Access Control**: Bypassing authorization checks.
-   **Security Misconfiguration**: Default passwords, open ports, verbose error messages in production.
-   **Insecure Deserialization**: Executing malicious code through serialized objects.
