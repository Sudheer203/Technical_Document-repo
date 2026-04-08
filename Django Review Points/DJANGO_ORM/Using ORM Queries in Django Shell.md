# Django ORM – Using ORM Queries in Django Shell

## 1. Introduction

**Django ORM (Object Relational Mapper)** is a feature that allows developers to interact with the database using **Python code instead of writing SQL queries**.

ORM converts **Python objects into database queries** automatically.

This makes database operations:

* Easier
* Safer
* More readable

Django provides a tool called **Django Shell** where developers can test ORM queries interactively.

---

# 2. What is Django Shell?

Django Shell is an **interactive Python environment** that allows you to run Django code and ORM queries directly.

It is useful for:

* Testing queries
* Debugging database operations
* Inspecting model data

### Start Django Shell

Run the following command inside the Django project folder:

```bash
python manage.py shell
```

Once opened, you can run Python and Django ORM commands.

---

# 3. Importing Models in Django Shell

Before running queries, you must import the models.

Example:

```python
from app_name.models import Student
```

Now you can access the `Student` table through the ORM.

---

# 4. Creating Data (Insert)

You can insert records using ORM.

Example:

```python
student = Student(name="Sudheer", age=22)
student.save()
```

Or using `create()`:

```python
Student.objects.create(name="Ravi", age=20)
```

Both commands add a new row in the database.

---

# 5. Reading Data (Select)

### Get all records

```python
Student.objects.all()
```

---

### Get a single record

```python
Student.objects.get(id=1)
```

---

### Filter records

```python
Student.objects.filter(age=20)
```

---

### Exclude records

```python
Student.objects.exclude(age=20)
```

---

# 6. Updating Data

To update an existing record:

```python
student = Student.objects.get(id=1)
student.age = 23
student.save()
```

This updates the value in the database.

---

# 7. Deleting Data

To delete a record:

```python
student = Student.objects.get(id=1)
student.delete()
```

To delete multiple records:

```python
Student.objects.filter(age=20).delete()
```

---

# 8. Common ORM Query Methods

| Method      | Purpose                               |
| ----------- | ------------------------------------- |
| `all()`     | Retrieve all records                  |
| `get()`     | Retrieve one record                   |
| `filter()`  | Retrieve records matching conditions  |
| `exclude()` | Retrieve records excluding conditions |
| `create()`  | Insert new record                     |
| `save()`    | Save changes                          |
| `delete()`  | Remove records                        |
| `count()`   | Count records                         |
| `first()`   | Get first record                      |
| `last()`    | Get last record                       |

Example:

```python
Student.objects.count()
```

---

# 9. Field Lookups

Django ORM allows powerful queries using **field lookups**.

Example:

### Greater than

```python
Student.objects.filter(age__gt=20)
```

---

### Less than

```python
Student.objects.filter(age__lt=20)
```

---

### Contains text

```python
Student.objects.filter(name__contains="Su")
```

---

### Case insensitive search

```python
Student.objects.filter(name__icontains="su")
```

---

# 10. Advantages of Using Django ORM

* No need to write raw SQL
* Database independent (works with PostgreSQL, MySQL, SQLite)
* Prevents SQL injection attacks
* Easier to read and maintain
* Integrates directly with Django models

---

# 11. Example Complete Workflow in Django Shell

Example session:

```python
from students.models import Student

Student.objects.create(name="Sudheer", age=22)

Student.objects.all()

Student.objects.filter(age=22)

student = Student.objects.get(name="Sudheer")

student.delete()
```

This demonstrates creating, reading, and deleting records using Django ORM.

---

# 12. Conclusion

Django ORM provides a **powerful and simple way to interact with databases using Python code**.

Using Django Shell, developers can:

* Test database queries
* Debug application data
* Quickly inspect database records

Key takeaways:

* ORM converts Python code into SQL queries
* Django Shell helps test ORM queries interactively
* ORM operations include **Create, Read, Update, and Delete (CRUD)**

Understanding Django ORM is essential for building **database-driven Django applications efficiently**.

---
