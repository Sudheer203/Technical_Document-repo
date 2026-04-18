# AMA Questions and Answers

## Command to start app

In Django, to create a new app we use:
`python manage.py startapp app_name`

Example: `python manage.py startapp products`

This creates folders like models, views, admin, etc.

------------------------------------------------------------------------

## grep command

`grep` is a Linux command used to search text inside files.

Example: `grep "hello" file.txt`

It finds the word **hello** inside the file.

------------------------------------------------------------------------

## What is Primary Key

A **Primary Key** is a unique ID for each record in a database table.

Example: User table

  id   name
  ---- ------
  1    Ram
  2    Ravi

Here **id** is the primary key.

------------------------------------------------------------------------

## rsync command

`rsync` is used to copy or sync files between two locations or servers.

Example: `rsync -av folder1/ folder2/`

It copies files and keeps both folders updated.

------------------------------------------------------------------------

## How to use a block of code multiple times

We use **functions**.

Example in Python:

    def greet():
        print("Hello")

Now we can call it many times:

    greet()
    greet()

------------------------------------------------------------------------

## How to see history of SQL queries

In MySQL we can use:

`SHOW PROCESSLIST;`

or check logs like:

`mysql.log`

This shows previously executed queries.

Run the Django shell:
```
python manage.py shell
```
Always show details


Then use:

```
from django.db import connection
print(connection.queries)
```

Always show details


This shows the SQL queries executed.

------------------------------------------------------------------------

## How to make model access to admin

In Django we register the model in **admin.py**

Example:

    from django.contrib import admin
    from .models import Product

    admin.site.register(Product)

Now the model appears in the admin panel.

------------------------------------------------------------------------

## What is Django Model

A **Django Model** is a Python class used to create database tables.

Example:

    class Product(models.Model):
        name = models.CharField(max_length=100)
        price = models.IntegerField()

This creates a table in the database.

------------------------------------------------------------------------

## Difference between PUT and PATCH

PUT: Used to **update the whole object**.

PATCH: Used to **update only some fields**.

Example: Change only email → PATCH

Replace entire user data → PUT

------------------------------------------------------------------------

## Features of Admin Panel

Django Admin Panel allows:

-   Add data
-   Edit data
-   Delete data
-   Manage users
-   Manage models
-   Search and filter records

It is a ready-made backend dashboard.

------------------------------------------------------------------------

## What is requirements.txt

`requirements.txt` stores all project dependencies.

Example:

    Django==5.0
    djangorestframework==3.15

Install them using:

`pip install -r requirements.txt`

------------------------------------------------------------------------

## Difference between Django MVT and MVC

MVC: Model → View → Controller

Django uses **MVT**

MVT: Model → Template → View

Mapping:

  MVC          Django
  ------------ ----------
  Model        Model
  View         Template
  Controller   View

------------------------------------------------------------------------

## Command to change models

After modifying models run:

    python manage.py makemigrations
    python manage.py migrate

This updates the database structure.
