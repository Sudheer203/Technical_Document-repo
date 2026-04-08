# CSRF (Cross-Site Request Forgery) 

## 1. Introduction

**CSRF (Cross-Site Request Forgery)** is a type of web security attack where a **malicious website tricks a logged-in user** into performing an unwanted action on another website without their knowledge.

Example:
If a user is logged in to `bank.com`, a malicious website could trick them into transferring money without their consent.

**Django provides built-in protection** against CSRF attacks.

---

## 2. How CSRF Works (Simple Explanation)

1. User logs into a website (e.g., `example.com`)
2. A session cookie is stored in the browser
3. User visits a malicious site while logged in
4. Malicious site sends a **POST request** to `example.com` using the user's credentials
5. If no protection exists, the request is executed, and the user’s data is affected

---

## 3. CSRF Protection in Django

Django uses **CSRF tokens** to prevent these attacks.

* A CSRF token is a **unique random string** associated with a user session
* The token is included in **all POST, PUT, DELETE requests**
* Django verifies the token for every incoming request

If the token is missing or invalid, Django **rejects the request** with `403 Forbidden`.

---

## 4. How to Use CSRF in Django

### 4.1 Templates (HTML Forms)

Add `{% csrf_token %}` inside every form:

```html
<form method="post">
    {% csrf_token %}
    <input type="text" name="username">
    <button type="submit">Submit</button>
</form>
```

### 4.2 AJAX Requests

Include the CSRF token in request headers:

```javascript

function getCookie(name) {
    let cookieValue = null;
    if (document.cookie && document.cookie !== '') {
        const cookies = document.cookie.split(';');
        for (let cookie of cookies) {
            cookie = cookie.trim();
            if (cookie.startsWith(name + '=')) {
                cookieValue = decodeURIComponent(cookie.split('=')[1]);
                break;
            }
        }
    }
    return cookieValue;
}

const csrftoken = getCookie('csrftoken');

fetch('/submit/', {
    method: 'POST',
    headers: {
        'X-CSRFToken': csrftoken
    },
    body: JSON.stringify({name: 'Sudheer'})
});
```

---

## 5. CSRF Middleware

Django provides a middleware to handle CSRF automatically:

```python
MIDDLEWARE = [
    'django.middleware.csrf.CsrfViewMiddleware',
    ...
]
```

* It **checks tokens on every incoming POST, PUT, DELETE request**
* Returns `403 Forbidden` if the token is invalid

---

## 6. Disabling CSRF (Not Recommended)

You can disable CSRF for a specific view (only if necessary):

```python
from django.views.decorators.csrf import csrf_exempt

@csrf_exempt
def my_view(request):
    ...
```

**Warning:** Only use this for trusted APIs, not for forms or sensitive operations.

---

## 7. Common Security Tips

* Always include `{% csrf_token %}` in forms
* Never disable CSRF in production for user-interactive pages
* Use **HTTPS** to prevent session hijacking
* Combine CSRF with **secure cookies** (`SESSION_COOKIE_SECURE = True`)

---

## 8. Conclusion

**CSRF attacks** are common and dangerous, but Django provides strong **built-in protection**.

**Key takeaways:**

1. Use CSRF tokens in all POST, PUT, DELETE requests
2. Enable `CsrfViewMiddleware`
3. Avoid disabling CSRF unless absolutely necessary
4. Always combine CSRF with HTTPS and secure session management

By following these steps, Django developers can **effectively prevent CSRF attacks** and protect their users.

---
