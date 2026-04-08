# Django Models – Understanding `on_delete=models.CASCADE`

## 1. Introduction

In Django, the **models.py** file is used to define the **database structure** of an application.
Each model represents a **table in the database**, and each attribute represents a **column**.

Django models often use **relationships between tables**, such as:

* One-to-One
* One-to-Many
* Many-to-Many

When creating relationships using `ForeignKey` or `OneToOneField`, Django requires the **`on_delete` parameter**.

One of the most commonly used options is:

```
on_delete=models.CASCADE
```

---

# 2. What is `on_delete`?

`on_delete` defines **what should happen when the referenced (parent) object is deleted**.

It controls how Django handles **related records in the database**.

Example syntax:

```python
models.ForeignKey(ModelName, on_delete=models.CASCADE)
```

This tells Django **how to handle dependent objects** if the referenced object is removed.

---

# 3. What is `CASCADE`?

`CASCADE` means:

> When the **parent record is deleted**, all **related child records are also deleted automatically**.

This behavior is similar to **cascade delete in relational databases**.

---

# 4. Example of `CASCADE`

Example models:

```python
from django.db import models

class Author(models.Model):
    name = models.CharField(max_length=100)


class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
```

### Database Relationship

```
Author (Parent Table)
    |
    | 1 → many
    |
Book (Child Table)
```

---

# 5. What Happens During Deletion

Suppose the database contains:

### Authors

| id | name    |
| -- | ------- |
| 1  | Sudheer |

### Books

| id | title         | author_id |
| -- | ------------- | --------- |
| 1  | Django Basics | 1         |
| 2  | Python Guide  | 1         |

If we delete the author:

```python
Author.objects.get(id=1).delete()
```

### Result

Both books will also be deleted automatically.

```
Author → deleted
Books → deleted
```

This is called **cascade deletion**.

---

# 6. Why CASCADE is Used

`CASCADE` helps maintain **database integrity**.

Without it, the database may contain **orphan records**.

Example:

A book referencing an author that **no longer exists**.

Using `CASCADE` ensures that **dependent data is removed automatically**.

---

# 7. Other `on_delete` Options in Django

Django provides several behaviors for handling deletions.

| Option        | Description                               |
| ------------- | ----------------------------------------- |
| `CASCADE`     | Delete related objects                    |
| `PROTECT`     | Prevent deletion if related objects exist |
| `SET_NULL`    | Set the foreign key to NULL               |
| `SET_DEFAULT` | Set a default value                       |
| `DO_NOTHING`  | Take no action                            |
| `SET()`       | Set a custom value                        |

Example:

```python
author = models.ForeignKey(Author, on_delete=models.SET_NULL, null=True)
```

This keeps the book but removes the author reference.

---

# 8. When to Use CASCADE

Use `CASCADE` when:

* Child objects **cannot exist without the parent**
* Data should be removed automatically when the parent is deleted

Examples:

* Comments belonging to a blog post
* Order items belonging to an order
* Books belonging to an author

---

# 9. Best Practices

* Use `CASCADE` only when the child depends on the parent
* Be careful with important data because cascade deletion **cannot be reversed**
* Always test deletion behavior before deploying to production

---

# 10. Conclusion

`on_delete=models.CASCADE` is a rule used in Django models to define **how related objects behave when a parent object is deleted**.

Key points:

* It automatically deletes related records
* Maintains database integrity
* Prevents orphan data
* Commonly used in parent-child relationships

Understanding `CASCADE` is important when designing **reliable and consistent database models in Django**.

---
