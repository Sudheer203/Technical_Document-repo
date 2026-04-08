# Clickjacking 

## 1. Introduction

**Clickjacking** is a type of web security attack where a malicious website **tricks a user into clicking something different from what they think they are clicking**.

In this attack, the attacker **loads a legitimate website inside an invisible iframe** and places fake buttons or links on top of it.

When the user clicks the visible element, they are actually clicking something on the hidden website.

This can lead to:

* Unauthorized actions
* Account changes
* Sending messages
* Financial transactions

Django provides **built-in protection against clickjacking attacks**.

---

## 2. How Clickjacking Works (Simple Explanation)

Step-by-step example:

1. User logs into a trusted website (example: a bank or social media site).
2. The user visits a malicious website created by an attacker.
3. The attacker loads the trusted website inside an **invisible iframe**.
4. The attacker places a **fake button** on top of the iframe.
5. When the user clicks the button, they unknowingly click a hidden action on the trusted site.

Example:

```
Malicious Website
-------------------------
| Click here to win!   |
|   (fake button)      |
-------------------------

Hidden Layer (iframe)
-------------------------
| Bank Transfer Button |
-------------------------
```

The user thinks they clicked the fake button, but actually triggered a **real action on another site**.

---

## 3. Risks of Clickjacking

Clickjacking can allow attackers to:

* Change account settings
* Like or share social media posts
* Transfer money
* Delete data
* Perform actions without user consent

Because the user is **already authenticated**, the action appears legitimate.

---

## 4. Clickjacking Protection in Django

Django protects against clickjacking using **XFrameOptionsMiddleware**.

This middleware adds an **HTTP header** called:

```
X-Frame-Options
```

This header tells the browser **whether the webpage is allowed to be displayed inside an iframe**.

---

## 5. Django Middleware for Clickjacking Protection

Django includes the following middleware by default:

```python
MIDDLEWARE = [
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```

This middleware automatically adds protection to all responses.

---

## 6. X-Frame-Options Settings

Django allows different protection levels using the `X_FRAME_OPTIONS` setting.

### DENY

```
X_FRAME_OPTIONS = 'DENY'
```

* The page **cannot be loaded in any iframe**
* Most secure option

---

### SAMEORIGIN

```
X_FRAME_OPTIONS = 'SAMEORIGIN'
```

* The page can only be embedded in an iframe **from the same website**
* Prevents external websites from framing your site

---

## 7. Allowing Specific Views in an iframe

Sometimes you may want a specific page to allow iframes.

Django provides decorators:

```python
from django.views.decorators.clickjacking import xframe_options_exempt

@xframe_options_exempt
def my_view(request):
    return render(request, "page.html")
```

This disables clickjacking protection **only for that view**.

---

## 8. Best Practices

To protect Django applications from clickjacking:

1. Enable `XFrameOptionsMiddleware`
2. Use `X_FRAME_OPTIONS = 'DENY'` for maximum protection
3. Only allow iframes when absolutely necessary
4. Use HTTPS for secure communication
5. Combine clickjacking protection with other security features such as CSRF protection

---

## 9. Example Security Configuration

Example secure settings in `settings.py`:

```python
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

X_FRAME_OPTIONS = 'DENY'
```

This configuration prevents your Django site from being embedded in malicious pages.

---

## 10. Conclusion

Clickjacking is a dangerous attack where users are **tricked into performing actions unknowingly**.

Django protects against this attack using:

* `XFrameOptionsMiddleware`
* `X-Frame-Options` HTTP header

Key takeaways:

* Prevent your pages from being loaded inside malicious iframes
* Use `DENY` or `SAMEORIGIN`
* Enable clickjacking middleware in Django

By following these practices, developers can **protect users from hidden UI manipulation attacks**.

---
