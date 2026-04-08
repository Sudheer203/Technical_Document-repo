# Django ORM – Understanding Annotations

## 1. Introduction

In Django ORM, **annotations** are used to **add calculated fields to each object in a QuerySet**.

Annotations allow developers to perform **database calculations** and attach the results to every record returned by the query.

Unlike aggregations (which return a single summary result), annotations **add extra data to each row** in the result set.

---

# 2. Why Annotations Are Used

Annotations help when you want to:

* Calculate values related to each record
* Count related objects
* Add computed data to query results
* Perform grouping and analysis directly in the database

Annotations allow the **database to perform calculations efficiently** instead of doing them in Python.

---

# 3. Importing Annotation Functions

Annotations usually work with aggregation functions.

Import them from:

```python
from django.db.models import Count, Sum, Avg, Max, Min
```

---

# 4. Example Models

Example models:

```python
class Author(models.Model):
    name = models.CharField(max_length=100)


class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
```

Relationship:

```
Author → has many → Books
```

---

# 5. Basic Annotation Example

We want to know **how many books each author has written**.

### ORM Query

```python
from django.db.models import Count

Author.objects.annotate(book_count=Count('book'))
```

### Result

Each author object will now have an extra field called:

```
book_count
```

Example output:

| Author  | Book Count |
| ------- | ---------- |
| Sudheer | 5          |
| Ravi    | 3          |
| Anil    | 7          |

Here, `book_count` is **not stored in the database**, but it is calculated dynamically.

---

# 6. Example Using Sum

Example model:

```python
class Order(models.Model):
    product = models.CharField(max_length=100)
    price = models.IntegerField()
```

### Annotation Query

```python
Order.objects.annotate(total_price=Sum('price'))
```

Each row now contains a calculated `total_price`.

---

# 7. Example Using Average

Example:

```python
Student.objects.annotate(avg_marks=Avg('marks'))
```

This attaches the **average marks calculation** to each record.

---

# 8. Annotation with Grouping

Annotations often work together with `values()`.

Example:

```python
Book.objects.values('author').annotate(total_books=Count('id'))
```

Example result:

| Author | Total Books |
| ------ | ----------- |
| 1      | 5           |
| 2      | 3           |
| 3      | 7           |

This groups records by author and counts books.

---

# 9. Annotation vs Aggregation

| Feature     | Annotation              | Aggregation                   |
| ----------- | ----------------------- | ----------------------------- |
| Result Type | Adds field to each row  | Returns single summary result |
| Output      | QuerySet                | Dictionary                    |
| Use Case    | Per-record calculations | Overall statistics            |

Example:

### Aggregation

```python
Book.objects.aggregate(Count('id'))
```

Output:

```
{'id__count': 20}
```

---

### Annotation

```python
Author.objects.annotate(book_count=Count('book'))
```

Output:

```
Author objects with book_count field
```

---

# 10. Advantages of Annotations

Annotations allow developers to:

* Add calculated data to query results
* Reduce complex Python calculations
* Improve database query performance
* Perform advanced analytics directly in the database

---

# 11. Practical Example

Example:

```python
Author.objects.annotate(total_books=Count('book')).filter(total_books__gt=5)
```

This query:

* Counts books per author
* Returns authors who have **more than 5 books**

---

# 12. Conclusion

Annotations in Django ORM allow developers to **add calculated values to each object in a QuerySet**.

Key points:

* Annotations attach computed fields to query results
* They work with functions like `Count`, `Sum`, `Avg`, `Max`, and `Min`
* They are useful for grouping, analysis, and reporting
* Unlike aggregations, annotations return **data per record**

Understanding annotations helps developers build **powerful database queries and analytical features in Django applications**.

---
