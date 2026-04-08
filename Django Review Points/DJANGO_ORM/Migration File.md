# Django Migrations – What is a Migration File?

## 1. Introduction

In Django, a **migration file** is a file that records **changes made to database models**.

Whenever a developer creates or modifies a model in `models.py`, Django needs to update the **database structure (tables, columns, relationships)**.

Migration files help Django **track and apply these changes safely to the database**.

In simple terms:

> **Migration files are instructions that tell Django how to update the database when models change.**

---

# 2. Why Migration Files Are Needed

Databases must stay synchronized with the Django models.

When developers:

* Create new models
* Add new fields
* Delete fields
* Modify field types
* Change relationships

The database structure must also change.

Migration files ensure:

* Database schema updates happen correctly
* Changes are version controlled
* Developers can safely update or rollback database changes

Without migrations, managing database changes would be **very difficult and error-prone**.

---

# 3. How Migration Files Work

The migration process usually happens in **two steps**.

### Step 1 — Create Migration File

```bash
python manage.py makemigrations
```

This command:

* Looks at changes in `models.py`
* Generates a migration file describing those changes

Example output:

```
Migrations for 'students':
  students/migrations/0001_initial.py
```

---

### Step 2 — Apply Migration to Database

```bash
python manage.py migrate
```

This command:

* Executes the migration file
* Creates or updates database tables

---

# 4. Example Model

Example model:

```python
class Student(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()
```

When this model is created, Django generates a migration file that creates a **Student table** in the database.

---

# 5. Example Migration File

Example migration file:

```python
from django.db import migrations, models


class Migration(migrations.Migration):

    dependencies = []

    operations = [
        migrations.CreateModel(
            name='Student',
            fields=[
                ('id', models.BigAutoField(primary_key=True)),
                ('name', models.CharField(max_length=100)),
                ('age', models.IntegerField()),
            ],
        ),
    ]
```

This file contains instructions for Django to **create a database table**.

---

# 6. Types of Changes Handled by Migrations

Migration files track many types of changes:

| Change                    | Example                      |
| ------------------------- | ---------------------------- |
| Creating models           | Creating new database tables |
| Adding fields             | Adding a new column          |
| Removing fields           | Deleting a column            |
| Changing field type       | Integer → CharField          |
| Adding relationships      | ForeignKey                   |
| Renaming models or fields | Database schema update       |

---

# 7. Migration Folder Structure

Inside every Django app:

```
app_name/
    migrations/
        __init__.py
        0001_initial.py
        0002_add_age_field.py
```

Explanation:

* `0001_initial.py` → First migration
* `0002_*.py` → Later changes
* Each file represents a **step in database evolution**

---

# 8. Migration Version Control

Migration files are usually **committed to Git**.

This allows:

* Team collaboration
* Database schema tracking
* Consistent database structure across environments

---

# 9. Useful Migration Commands

Create migrations:

```bash
python manage.py makemigrations
```

Apply migrations:

```bash
python manage.py migrate
```

Show migrations:

```bash
python manage.py showmigrations
```

Undo migration:

```bash
python manage.py migrate app_name 0001
```

---

# 10. Advantages of Migrations

Migration files provide several benefits:

* Automatic database schema management
* Safe updates to production databases
* Version control for database structure
* Ability to rollback changes
* Collaboration between developers

---

# 11. Best Practices

When working with migrations:

* Always run `makemigrations` after changing models
* Review migration files before applying
* Commit migration files to version control
* Avoid editing migration files manually unless necessary

---

# 12. Conclusion

Migration files are an essential part of Django's database management system.

Key points:

* Migrations track changes to models
* They update the database schema safely
* They allow version control of database structure
* They support collaboration in development teams

Understanding migrations helps developers **maintain reliable and scalable Django applications**.

---
