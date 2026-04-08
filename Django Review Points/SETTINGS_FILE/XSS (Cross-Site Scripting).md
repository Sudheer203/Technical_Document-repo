# XSS (Cross-Site Scripting)

## 1. Introduction

**XSS (Cross-Site Scripting)** is a type of web security vulnerability where an attacker **injects malicious scripts** (usually JavaScript) into a website.

These scripts run in the **victim’s browser**, which can lead to:

* Stealing cookies or session data
* Modifying page content
* Redirecting users to malicious websites
* Performing actions on behalf of the user

Django provides built-in protections to prevent XSS attacks.

---

## 2. How XSS Works (Simple Explanation)

1. Attacker submits malicious code into a website input field
2. Website stores or displays the input without proper validation
3. Another user visits the page containing the malicious input
4. Browser executes the attacker’s script in the context of the victim
5. The attacker can steal cookies or manipulate the page

Example of malicious input:

```javascript
<script>alert("You are hacked!");</script>
```

---

## 3. XSS Protection in Django

Django protects against XSS **by default** using **automatic HTML escaping**.

### How it works:

* Any variable printed in a Django template is **escaped**:

  * `<` becomes `&lt;`
  * `>` becomes `&gt;`
* This prevents browsers from interpreting user input as executable code

Example:

```html
<p>{{ user_input }}</p>
```

If `user_input` contains `<script>alert('XSS')</script>`, it will be displayed as text, **not executed**.

---

## 4. Safe Practices in Templates

* **Never use `|safe`** on untrusted user input, because it disables escaping
* Always **validate and sanitize input** if you allow HTML
* Use **Django template tags** instead of rendering raw HTML

---

## 5. XSS in Forms

When accepting user input:

```python
<form method="post">
    {% csrf_token %}
    <input type="text" name="comment">
    <button type="submit">Submit</button>
</form>
```

* Django escapes input when rendering it in templates
* Combined with **CSRF protection**, this ensures safer user interactions

---

## 6. Additional XSS Protections

* **Content Security Policy (CSP):** restricts which scripts can run
* **HttpOnly cookies:** prevent JavaScript from accessing sensitive cookies
* **Input validation:** reject or clean dangerous characters (`<`, `>`, `"`)

Example CSP header in Django:

```python
SECURE_BROWSER_XSS_FILTER = True
```

Or using third-party libraries like **django-csp** for stricter controls.

---

## 7. Summary of Best Practices

1. Use **Django templates** with automatic escaping
2. Avoid using `|safe` on untrusted data
3. Validate and sanitize all user input
4. Enable **HttpOnly** and **Secure cookies**
5. Consider **Content Security Policy (CSP)** headers

---

## 8. Conclusion

XSS is one of the most common web attacks, but Django provides **strong built-in defenses**:

* Auto-escaping in templates
* CSRF protection (prevents some attack vectors)
* Security headers like XSS filter

Following best practices ensures that your Django application is **protected against malicious scripts** and keeps your users safe.

---
