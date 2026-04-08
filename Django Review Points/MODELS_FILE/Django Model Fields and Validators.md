# Django Model Fields and Validators 

## 1. Introduction

In Django, **models** define the structure of the database.
Inside a model, we use **fields** to define the type of data that each column will store.

Example:

```python
class Student(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()
```

In this example:

* `name` and `age` are **fields**
* They define **what kind of data** will be stored in the database.

To ensure data is correct and safe, Django also provides **validators**.

Validators check that the data **meets certain rules before saving it to the database**.

---

# 2. What are Fields in Django?

A **field** defines:

* The **type of data**
* The **database column type**
* The **validation rules**
* The **form representation**

Example:

```python
title = models.CharField(max_length=200)
```

This means:

* `title` stores text
* Maximum length = 200 characters

---

# 3. Common Django Fields

Below are some commonly used fields in Django models.

## 3.1 CharField

Used for **short text**.

Example:

```python
name = models.CharField(max_length=100)
```

Use cases:

* Names
* Titles
* Short descriptions

---

## 3.2 TextField

Used for **large text content**.

Example:

```python
description = models.TextField()
```

Use cases:

* Blog content
* Comments
* Articles

---

## 3.3 IntegerField

Stores **integer numbers**.

Example:

```python
age = models.IntegerField()
```

Use cases:

* Age
* Quantity
* Scores

---

## 3.4 FloatField

Stores **decimal numbers**.

Example:

```python
price = models.FloatField()
```

Use cases:

* Prices
* Measurements

---

## 3.5 BooleanField

Stores **True or False values**.

Example:

```python
is_active = models.BooleanField(default=True)
```

Use cases:

* Status flags
* Feature toggles

---

## 3.6 DateField

Stores **date values**.

Example:

```python
birth_date = models.DateField()
```

Options:

```
auto_now_add=True
auto_now=True
```

---

## 3.7 DateTimeField

Stores **date and time**.

Example:

```python
created_at = models.DateTimeField(auto_now_add=True)
```

Use cases:

* Timestamps
* Log entries

---

## 3.8 EmailField

Stores **email addresses**.

Example:

```python
email = models.EmailField()
```

Automatically validates email format.

---

## 3.9 URLField

Stores **website URLs**.

Example:

```python
website = models.URLField()
```

---

## 3.10 FileField / ImageField

Used for uploading files and images.

Example:

```python
profile_picture = models.ImageField(upload_to='images/')
```

Requires **Pillow library** for image processing.

---

## 3.11 ForeignKey

Creates a **relationship between tables**.

Example:

```python
author = models.ForeignKey(Author, on_delete=models.CASCADE)
```

---

# 4. Field Options

Fields can also include additional options.

Example:

```python
name = models.CharField(max_length=100, null=True, blank=True)
```

Common options:

| Option             | Description                 |
| ------------------ | --------------------------- |
| `null=True`        | Database can store NULL     |
| `blank=True`       | Field can be empty in forms |
| `default=value`    | Default value               |
| `unique=True`      | Value must be unique        |
| `primary_key=True` | Sets primary key            |

---

# 5. What are Validators?

Validators are functions that **check whether the data entered is valid**.

They run **before saving data to the database**.

Example:

```python
from django.core.validators import MinValueValidator

age = models.IntegerField(validators=[MinValueValidator(18)])
```

This ensures age **must be at least 18**.

---

# 6. Built-in Validators in Django

Django provides many built-in validators.

## 6.1 MinValueValidator

Ensures the value is **greater than or equal to a minimum value**.

Example:

```python
from django.core.validators import MinValueValidator

age = models.IntegerField(validators=[MinValueValidator(18)])
```

---

## 6.2 MaxValueValidator

Ensures the value **does not exceed a maximum value**.

Example:

```python
from django.core.validators import MaxValueValidator

score = models.IntegerField(validators=[MaxValueValidator(100)])
```

---

## 6.3 MinLengthValidator

Ensures a **minimum length of text**.

Example:

```python
from django.core.validators import MinLengthValidator

username = models.CharField(max_length=50, validators=[MinLengthValidator(5)])
```

---

## 6.4 MaxLengthValidator

Ensures text **does not exceed a specified length**.

Example:

```python
from django.core.validators import MaxLengthValidator

title = models.CharField(max_length=200, validators=[MaxLengthValidator(200)])
```

---

## 6.5 EmailValidator

Ensures the value is a **valid email address**.

Example:

```python
from django.core.validators import EmailValidator

email = models.CharField(max_length=100, validators=[EmailValidator()])
```

---

## 6.6 URLValidator

Validates a **website URL**.

Example:

```python
from django.core.validators import URLValidator

website = models.URLField(validators=[URLValidator()])
```

---

# 7. Custom Validators

Developers can create **custom validation functions**.

Example:

```python
from django.core.exceptions import ValidationError

def validate_even(value):
    if value % 2 != 0:
        raise ValidationError("Only even numbers are allowed")
```

Use in a model:

```python
number = models.IntegerField(validators=[validate_even])
```

---

# 8. Why Fields and Validators are Important

They help:

* Maintain **data integrity**
* Prevent **invalid data**
* Improve **application reliability**
* Provide **automatic form validation**

---

# 9. Conclusion

Django models use **fields** to define the type of data stored in the database and **validators** to ensure the data is correct.

Key points:

* Fields define **data structure**
* Validators enforce **data rules**
* Django provides many built-in options
* Developers can also create custom validators

Understanding fields and validators helps build **secure, reliable, and well-structured Django applications**.

---
