# WSGI (Web Server Gateway Interface) 

## 1. Introduction

**WSGI (Web Server Gateway Interface)** is a **standard interface** between a **Python web application** and a **web server**.

It defines how a **web server communicates with Python applications** such as Django, Flask, or Pyramid.

In simple words:

* WSGI acts as a **bridge between the web server and the Python web application**.

---

## 2. Why WSGI is Needed

A web application cannot directly communicate with a web server.

Example:

* Web servers: **Apache, Nginx**
* Python web frameworks: **Django, Flask**

They work differently and need a **standard communication protocol**.

WSGI solves this problem by defining **how requests and responses should be passed between them**.

---

## 3. How WSGI Works (Simple Explanation)

The request-response flow works like this:

```
Browser
   ↓
Web Server (Nginx / Apache)
   ↓
WSGI Server (Gunicorn / uWSGI)
   ↓
Django Application
   ↓
Response back to Browser
```

### Step-by-step process

1. User sends a request from the browser.
2. The web server receives the request.
3. The request is forwarded to the **WSGI server**.
4. The WSGI server passes the request to the **Python application**.
5. The application processes the request and generates a response.
6. The response is sent back to the browser.

---

## 4. WSGI in Django

When you create a Django project, Django automatically generates a file called:

```
wsgi.py
```

Example:

```python
import os
from django.core.wsgi import get_wsgi_application

os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'myproject.settings')

application = get_wsgi_application()
```

### Purpose of this file

* Creates the **WSGI application object**
* Allows web servers to communicate with Django

---

## 5. WSGI Servers

A **WSGI server** runs Python web applications.

Common WSGI servers include:

| Server   | Description                           |
| -------- | ------------------------------------- |
| Gunicorn | Lightweight Python WSGI server        |
| uWSGI    | High-performance production server    |
| mod_wsgi | Apache module for running Python apps |
| Waitress | Pure Python WSGI server               |

Example command using Gunicorn:

```
gunicorn myproject.wsgi
```

---

## 6. Example of a Simple WSGI Application

A basic WSGI application looks like this:

```python
def application(environ, start_response):
    status = '200 OK'
    headers = [('Content-type', 'text/plain')]
    start_response(status, headers)

    return [b"Hello, World!"]
```

Explanation:

* `environ` contains request data
* `start_response` sends response status and headers
* The function returns the response body

---

## 7. WSGI vs ASGI

Modern Python frameworks also support **ASGI (Asynchronous Server Gateway Interface)**.

| Feature           | WSGI          | ASGI                     |
| ----------------- | ------------- | ------------------------ |
| Request handling  | Synchronous   | Asynchronous             |
| WebSockets        | Not supported | Supported                |
| Real-time apps    | Limited       | Better support           |
| Framework support | Django, Flask | Django Channels, FastAPI |

Django supports both:

* **WSGI** for traditional applications
* **ASGI** for async and real-time applications

---

## 8. Benefits of WSGI

* Standard interface for Python web apps
* Works with multiple web servers
* Reliable and stable architecture
* Easy deployment in production environments

---

## 9. Conclusion

**WSGI (Web Server Gateway Interface)** is a standard that allows **Python web applications to communicate with web servers**.

Key points:

* Acts as a bridge between server and application
* Used by frameworks like Django and Flask
* Enables deployment with servers such as Gunicorn or uWSGI
* Handles request-response communication

Understanding WSGI is important for **deploying Django applications in production environments**.

---
