
# AMA - QUESTIONS :

# DELETE and DROP in SQL

## DELETE
- Removes selected rows from a table.
- Table structure remains.

Example:
DELETE FROM students WHERE id = 1;

## DROP
- Deletes the entire table (structure + data).

Example:
DROP TABLE students;

Difference:
DELETE = Removes data only  
DROP = Removes full table  

---

# Aggregate Functions in SQL

Aggregate functions calculate values from multiple rows.

- COUNT() - Counts rows  
- SUM() - Adds values  
- AVG() - Finds average  
- MAX() - Highest value  
- MIN() - Lowest value  

Example:
SELECT COUNT(*) FROM students;

---

# Retrieve Data Without Primary Key

If no primary key:
- Use WHERE condition
- Use combination of columns
- Use LIMIT
- Use ROW_NUMBER()

Example:
SELECT * FROM students WHERE name = 'Ravi';

---

# RANK Function

RANK() gives ranking numbers based on ORDER BY.

If marks are:
90 - Rank 1  
85 - Rank 2  
85 - Rank 2  
80 - Rank 4  

Rank skips number after tie.

---

# Why We Use venv in Python

venv (Virtual Environment):
- Creates separate environment for each project.
- Avoids package conflicts.
- Keeps project clean.

---

# DML Commands

DML = Data Manipulation Language

- INSERT - Add data  
- UPDATE - Modify data  
- DELETE - Remove data  
- SELECT - Retrieve data  

---

# List Hidden Files (Linux)

Command:
ls .a

Hidden files start with '.'

---

# Break and Continue (Python)

break - Stops loop  
continue - Skips current iteration  

---

# Set Operations in SQL

- UNION - Combine, remove duplicates  
- UNION ALL - Combine, keep duplicates  
- INTERSECT - Common records  
- EXCEPT - Difference  

---

# remove() and pop() in Python

remove() - Removes value  
pop() - Removes using index  

---

# Dictionary in Python

Dictionary stores key-value pairs.

Example:
student = {
    "name": "Ravi",
    "age": 21
}

---

# Foreign Key

- Connects two tables.
- References primary key in another table.

---

# Primary Key

- Uniquely identifies each row.
- No NULL values.
- No duplicates.

---

# Indexing in SQL

- Improves search speed.
- Makes SELECT faster.

---

# List Methods in Python

- append()
- extend()
- insert()
- remove()
- pop()
- sort()
- reverse()
- clear()

---
