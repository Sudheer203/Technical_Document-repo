# Django ORM – Understanding Aggregations

## 1. Introduction

In database systems, **aggregation** means performing **calculations on multiple rows of data to produce a single result**.

Examples of common aggregation operations include:

* Counting records
* Finding the sum of values
* Calculating the average
* Finding the maximum value
* Finding the minimum value

Django ORM provides built-in **aggregation functions** that allow developers to perform these calculations easily using Python code.

---

# 2. Why Aggregations Are Important

Aggregations are useful when working with large datasets.

They help answer questions such as:

* How many users are registered?
* What is the total sales amount?
* What is the average salary?
* What is the highest score in a class?

Instead of manually calculating values in Python, Django lets the **database perform these calculations efficiently**.

---

# 3. Aggregation Functions in Django

Django provides several built-in aggregation functions in:

```python
django.db.models
```

Common aggregation functions include:

| Function  | Purpose                  |
| --------- | ------------------------ |
| `Count()` | Counts number of records |
| `Sum()`   | Calculates total value   |
| `Avg()`   | Calculates average value |
| `Max()`   | Finds maximum value      |
| `Min()`   | Finds minimum value      |

---

# 4. Importing Aggregation Functions

Before using aggregations, import them:

```python
from django.db.models import Count, Sum, Avg, Max, Min
```

---

# 5. Example Model

Example model:

```python
class Student(models.Model):
    name = models.CharField(max_length=100)
    marks = models.IntegerField()
```

This model represents a table of students and their marks.

---

# 6. Count Aggregation

Counts the total number of records.

### ORM Query

```python
Student.objects.aggregate(Count('id'))
```

### Example Output

```python
{'id__count': 10}
```

This means there are **10 student records** in the database.

---

# 7. Sum Aggregation

Calculates the total value of a field.

### ORM Query

```python
Student.objects.aggregate(Sum('marks'))
```

### Example Output

```python
{'marks__sum': 850}
```

This means the **total marks of all students = 850**.

---

# 8. Average Aggregation

Calculates the average value.

### ORM Query

```python
Student.objects.aggregate(Avg('marks'))
```

### Example Output

```python
{'marks__avg': 85}
```

This means the **average marks = 85**.

---

# 9. Maximum Value

Finds the highest value.

### ORM Query

```python
Student.objects.aggregate(Max('marks'))
```

### Example Output

```python
{'marks__max': 98}
```

---

# 10. Minimum Value

Finds the smallest value.

### ORM Query

```python
Student.objects.aggregate(Min('marks'))
```

### Example Output

```python
{'marks__min': 60}
```

---

# 11. Multiple Aggregations

You can perform multiple calculations in a single query.

Example:

```python
Student.objects.aggregate(
    total_marks=Sum('marks'),
    average_marks=Avg('marks'),
    highest_marks=Max('marks')
)
```

Example output:

```python
{
 'total_marks': 850,
 'average_marks': 85,
 'highest_marks': 98
}
```

---

# 12. Aggregation vs Annotation

Django also supports **annotation**, which is related to aggregation.

| Feature | Aggregation                 | Annotation                               |
| ------- | --------------------------- | ---------------------------------------- |
| Result  | Single summary value        | Adds calculated field to each row        |
| Example | Total marks of all students | Marks per student with extra calculation |

Example of annotation:

```python
Student.objects.annotate(total=Sum('marks'))
```

---

# 13. Advantages of Aggregations

* Efficient database calculations
* Reduces data processing in Python
* Faster queries for large datasets
* Useful for analytics and reporting

---

# 14. Conclusion

Aggregations in Django ORM allow developers to perform **mathematical calculations on database records**.

Key points:

* Aggregations summarize data
* Django provides functions such as `Count`, `Sum`, `Avg`, `Max`, and `Min`
* They help analyze large datasets efficiently
* They are commonly used in reports, dashboards, and analytics

Understanding aggregations helps developers build **data-driven Django applications** with powerful database queries.

---
