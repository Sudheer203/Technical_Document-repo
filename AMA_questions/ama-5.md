# AMA Questions and Answers

## 1. Syntax for Migrations in Django

Migrations are used to **apply changes in models to the database**.

### Steps / Commands

```bash
python manage.py makemigrations
```

Creates migration files based on model changes.

```bash
python manage.py migrate
```

Applies migrations to the database.

```bash
python manage.py showmigrations
```

Shows applied and pending migrations.

### Simple Meaning

Migrations keep the **database structure in sync with Django models**.

---

# 2. Difference between querySelector() and getElementById()

| querySelector()                    | getElementById()             |
| ---------------------------------- | ---------------------------- |
| Selects element using CSS selector | Selects element using ID     |
| Can select class, tag, id          | Only selects id              |
| Returns first matching element     | Returns element with that id |

### Example

```javascript
document.querySelector(".box")
document.getElementById("box")
```

### Simple Meaning

* **querySelector** → flexible selector
* **getElementById** → fastest way to select an element by id

---

# 3. What is HTTPS?

HTTPS means:

**Hyper Text Transfer Protocol Secure**

It is a **secure version of HTTP**.

### Features

* Data is **encrypted**
* Protects from hackers
* Used in secure websites

Example:

```
https://google.com
```

### Simple Meaning

HTTPS keeps **data safe between browser and server**.

---

# 4. Methods to Get All Records in Database

In Django ORM we use:

```python
Model.objects.all()
```

### Example

```python
students = Student.objects.all()
```

### Other Methods

```python
Model.objects.filter()
Model.objects.values()
```

### Simple Meaning

These methods **retrieve records from the database**.

---

# 5. What is Template?

A **template** is an **HTML file used to display data** in Django.

Example:

```
templates/home.html
```

Example Code:

```html
<h1>{{ name }}</h1>
```

### Simple Meaning

Templates are used to **show data to users in the browser**.

---

# 6. How to Create a Div Inside a Div (DOM)

### HTML Example

```html
<div id="parent">
    <div id="child"></div>
</div>
```

### JavaScript Example

```javascript
let parent = document.getElementById("parent")
let child = document.createElement("div")

parent.appendChild(child)
```

### Simple Meaning

We create a **child div and append it to parent div**.

---

# 7. Difference between innerHTML and textContent

| innerHTML          | textContent     |
| ------------------ | --------------- |
| Reads HTML content | Reads only text |
| Can include tags   | No HTML tags    |
| Slower             | Faster          |

### Example

```javascript
element.innerHTML = "<b>Hello</b>"
element.textContent = "Hello"
```

### Simple Meaning

* **innerHTML** → reads HTML
* **textContent** → reads plain text

---

# 8. What is HTTP?

HTTP means:

**Hyper Text Transfer Protocol**

It is used for **communication between browser and server**.

Example flow:

```
Browser → Request → Server
Server → Response → Browser
```

### Simple Meaning

HTTP helps **web pages load in the browser**.

---

# 9. What is typeof() in JavaScript?

`typeof()` checks the **data type of a variable**.

### Example

```javascript
typeof 10
```

Output

```
number
```

Example

```javascript
typeof "Hello"
```

Output

```
string
```

### Simple Meaning

It tells **what type of data a variable contains**.

---

# 10. What is Event Loop?

The **Event Loop** manages **asynchronous operations in JavaScript**.

It handles things like:

* API calls
* timers
* callbacks

Example

```javascript
setTimeout(() => {
    console.log("Hello")
}, 1000)
```

### Simple Meaning

Event Loop ensures **JavaScript runs tasks in the correct order**.

---

# 11. Ashok — Function Based View vs Class Based View

## Function Based View (FBV)

Uses a **simple function**.

Example

```python
def home(request):
    return HttpResponse("Hello")
```

## Class Based View (CBV)

Uses **Python classes**.

Example

```python
class HomeView(View):
    def get(self, request):
        return HttpResponse("Hello")
```

### Difference

| Function Based View | Class Based View |
| ------------------- | ---------------- |
| Simple              | More structured  |
| Easy to understand  | Reusable         |

---

# 12. What is ORM in Django?

ORM means:

**Object Relational Mapping**

It allows us to **work with database using Python code instead of SQL**.

Example

```python
Student.objects.all()
```

Instead of writing SQL:

```sql
SELECT * FROM student;
```

### Simple Meaning

ORM lets you **talk to database using Python**.

---

# 13. How to Enhance the Performance of Django

Ways to improve performance:

### 1. Use Database Indexing

Improves query speed.

### 2. Use Caching

Example

```
Redis
Memcached
```

### 3. Optimize Queries

Use

```python
select_related()
prefetch_related()
```

### 4. Use Gunicorn / Nginx for deployment

### Simple Meaning

Improve **database queries, caching, and server setup**.

---

# 14. Need of App Level URLs Even Though We Have Project URLs

In Django we use:

### Project URLs

```
project/urls.py
```

### App URLs

```
app/urls.py
```

Example

Project urls:

```python
path("blog/", include("blog.urls"))
```

App urls:

```python
path("home/", views.home)
```

### Why?

* Keeps code **organized**
* Makes project **modular**
* Easy to maintain

### Simple Meaning

App level URLs **separate routing for each app**.

---

