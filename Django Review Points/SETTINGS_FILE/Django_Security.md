# Django Security – Technical Guide

## 1. Introduction

Django is designed with **security in mind**. It provides **built-in protections** against many common web vulnerabilities.
However, developers must **understand and correctly configure these features** to ensure a secure application.

This document explains the **core security features in Django** and practical tips for using them.

---

## 2. Secret Key

* **Purpose:** Used for cryptographic signing (sessions, cookies, CSRF tokens, password resets)
* **Security tip:**

  * Never commit the secret key to GitHub
  * Use environment variables or `.env` files
* **Command to generate a secure key:**

  ```bash
  python -c "from django.core.management.utils import get_random_secret_key; 
  
  print(get_random_secret_key())"
  ```

---

## 3. User Authentication & Passwords

* Django uses **hashed passwords** (PBKDF2 by default)
* Provides built-in **login, logout, and password management**
* Security tips:

  * Require strong passwords using `AUTH_PASSWORD_VALIDATORS`
  * Never store plain-text passwords
  * Consider **two-factor authentication** with third-party packages

---

## 4. Cross-Site Request Forgery (CSRF)

* **CSRF attacks** trick users into submitting malicious requests
* Django provides `CsrfViewMiddleware` to prevent CSRF
* Security tips:

  * Include `{% csrf_token %}` in forms
  * Never disable CSRF protection in production

---

## 5. Cross-Site Scripting (XSS)

* **XSS attacks** inject malicious scripts into pages
* Django templates **auto-escape variables by default**
* Security tips:

  * Avoid using `|safe` unless necessary
  * Validate user input

---

## 6. SQL Injection

* Django ORM automatically **escapes queries**
* Security tips:

  * Always use **ORM methods** instead of raw SQL
  * If using raw SQL, use **parameterized queries**

---

## 7. Clickjacking

* **Clickjacking** tricks users into clicking hidden elements
* Django provides `XFrameOptionsMiddleware`
* Security tips:

  * Set `X_FRAME_OPTIONS = 'DENY'` or `'SAMEORIGIN'`

---

## 8. HTTPS / Secure Cookies

* Use HTTPS to encrypt data between client and server
* Security settings:

  ```python
  SECURE_SSL_REDIRECT = True
  SESSION_COOKIE_SECURE = True
  CSRF_COOKIE_SECURE = True
  ```
* These ensure cookies are only sent over secure connections

---

## 9. SecurityMiddleware

* Adds multiple security protections:

  * HSTS (HTTP Strict Transport Security)
  * X-Content-Type-Options
  * X-XSS-Protection (legacy)
* Always include `'django.middleware.security.SecurityMiddleware'` as the **first middleware**

---

## 10. Other Security Best Practices

* **Django DEBUG = False** in production
* Keep **Django and dependencies up to date**
* Use **environment variables** for sensitive information
* Limit **allowed hosts**:

  ```python
  ALLOWED_HOSTS = ['example.com', 'www.example.com']
  ```
* Validate all user inputs and use proper error handling

---

## 11. Optional Security Enhancements

* **Django Axes** – Protect against brute-force login attempts
* **Django Two-Factor Authentication** – Adds OTP-based login
* **Django Content Security Policy (CSP)** – Prevents XSS by restricting sources
* **Django Helmet / Security Headers** – Add additional HTTP headers

---

## 12. Conclusion

Django provides **strong built-in security features**, but developers must:

* Understand and configure them properly
* Follow best practices for production
* Regularly update the framework and dependencies

**Key Takeaways:**

1. Protect your **secret key**
2. Always use **CSRF tokens**
3. Use HTTPS and secure cookies
4. Prevent XSS and SQL injection via ORM and escaping
5. Monitor and update Django for security patches

---

This guide helps you **secure Django projects** while keeping things simple and maintainable.

---
