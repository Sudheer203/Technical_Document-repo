# Default Django Apps

## 1. Introduction

When a new **Django project** is created using:

```
django-admin startproject project_name
```

Django automatically includes some **default applications** inside the `INSTALLED_APPS` section of the `settings.py` file.

These apps provide **core functionality** required for most web applications such as authentication, session management, admin interface, and static files handling.

Example:

# settings.py

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

These are called **built-in Django applications**.

---

# 2. List of Default Django Apps

Below are the default apps provided by Django and their purpose.

---

## 2.1 django.contrib.admin

### Purpose

Provides a **built-in administrative interface** for managing the database through a web browser.

### Features

* Add, edit, and delete database records
* Manage users and permissions
* Automatic admin dashboard
* Easy data management without writing custom code

### Example URL

```
http://127.0.0.1:8000/admin/
```

---

## 2.2 django.contrib.auth

### Purpose

Handles **authentication and authorization**.

### Features

* User login and logout
* Password hashing
* User permissions
* User groups
* Authentication system

### Example

```
User.objects.create_user()
authenticate()
login()
logout()
```

---

## 2.3 django.contrib.contenttypes

### Purpose

Tracks **all models installed in the project**.

It allows Django to create **generic relationships** between models.

### Why it is needed

Some Django features like:

* Permissions
* Generic foreign keys
* Admin system

depend on this app.

---

## 2.4 django.contrib.sessions

### Purpose

Manages **user sessions**.

A session allows Django to **remember users between requests**.

### Example

When a user logs in:

* Django stores session data
* The browser receives a **session cookie**

Example:

```
request.session['username'] = 'sudheer'
```

---

## 2.5 django.contrib.messages

### Purpose

Provides a **messaging framework** for displaying messages to users.

### Examples

* Login success message
* Error message
* Warning notification

Example:

```
from django.contrib import messages

messages.success(request, "Login successful")
```

---

## 2.6 django.contrib.staticfiles

### Purpose

Manages **static files** such as:

* CSS
* JavaScript
* Images

### Example static file structure

```
static/
    css/
    js/
    images/
```

This app helps Django **collect and serve static files** during development.

---

# 3. Are There More Built-in Django Apps?

Yes. Django provides **many additional optional apps** that can be installed if needed.

Some examples include:

| App                        | Purpose                                            |
| -------------------------- | -------------------------------------------------- |
| `django.contrib.sites`     | Supports multiple websites with one Django project |
| `django.contrib.humanize`  | Makes numbers and dates more readable              |
| `django.contrib.sitemaps`  | Helps generate sitemap.xml for SEO                 |
| `django.contrib.flatpages` | Create simple static pages                         |
| `django.contrib.redirects` | Manage URL redirects                               |
| `django.contrib.postgres`  | PostgreSQL specific features                       |

These apps are **not enabled by default**, but they are available in Django.

---

# 4. Custom Django Apps

In addition to built-in apps, developers usually create **custom apps** for project features.

Example command:

```
python manage.py startapp blog
```

Example structure:

```
project/
    manage.py
    project/
        settings.py
    blog/
        models.py
        views.py
        admin.py
```

Custom apps help organize large projects into **modular components**.

---

# 5. Why Django Uses Apps

Django follows the **modular architecture principle**.

Each app handles a specific responsibility such as:

* Authentication
* Admin interface
* Static file handling

This approach improves:

* Code organization
* Reusability
* Scalability
* Maintainability

---

# 6. Conclusion

Django provides several **default built-in apps** that implement core web application features such as authentication, session management, and admin interface.

### Default apps included in every Django project

* django.contrib.admin
* django.contrib.auth
* django.contrib.contenttypes
* django.contrib.sessions
* django.contrib.messages
* django.contrib.staticfiles

Developers can also install **additional Django apps** or create **custom apps** to extend functionality.

Understanding these apps is essential for building secure, scalable, and well-structured Django applications.

---
