# SQL Indexes – Technical Documentation

## Understanding Database Indexing and Performance Optimization

---

## Introduction

An index in a database is a data structure that improves the speed of data retrieval operations on a table.

Indexes work similarly to an index in a book — instead of scanning the entire table,
the database engine can quickly locate the required rows.

---

# 1. Why Indexes Are Important

Without an index:

- The database performs a Full Table Scan
- Performance degrades for large tables
- Query response time increases

With an index:

- Faster SELECT queries
- Efficient filtering
- Improved JOIN performance

---

# 2. How Indexes Work

Most relational databases use:

- B-Tree (Balanced Tree) Indexes
- Hash Indexes (in some systems)

B-Tree indexes allow efficient:

- Equality searches
- Range searches
- Sorting operations

---

# 3. Types of Indexes

---

## 🔹 1. Single Column Index

Index created on one column.

Example:

    CREATE INDEX idx_employee_salary
    ON employees(salary);

---

## 🔹 2. Composite Index (Multi-column Index)

Index created on multiple columns.

Example:

    CREATE INDEX idx_employee_dept_salary
    ON employees(department, salary);

Order of columns matters.

---

## 🔹 3. Unique Index

Ensures all values in indexed column are unique.

Example:

    CREATE UNIQUE INDEX idx_employee_email
    ON employees(email);

---

## 🔹 4. Primary Key Index

Automatically created when defining a primary key.

Example:

    CREATE TABLE employees (
        id INT PRIMARY KEY,
        name VARCHAR(100)
    );

---

## 🔹 5. Full-Text Index

Used for text search operations.

Example:

    CREATE FULLTEXT INDEX idx_description
    ON products(description);

---

# 4. When to Use Indexes

✔ Columns used in WHERE clause  
✔ Columns used in JOIN conditions  
✔ Columns used in ORDER BY  
✔ Frequently searched columns  

---

# 5. When NOT to Use Indexes

- Very small tables  
- Columns with low selectivity (few unique values)  
- Columns frequently updated  

Indexes slow down:

- INSERT operations
- UPDATE operations
- DELETE operations

Because index structures must also be updated.

---

# 6. Example: Performance Difference

Without Index:

    SELECT * FROM employees WHERE salary = 80000;

→ Full table scan

With Index on salary:

→ Index lookup + faster retrieval

---

# 7. Checking Query Performance

Use:

    EXPLAIN SELECT * FROM employees WHERE salary = 80000;

This shows whether index is being used.

---

# 8. Advantages of Indexes

✔ Faster queries  
✔ Efficient filtering  
✔ Better JOIN performance  
✔ Optimized sorting  

---

# 9. Disadvantages of Indexes

- Extra storage space  
- Slower write operations  
- Maintenance overhead  

---

# Conclusion

Indexes are essential for database performance optimization.

Key Takeaways:

- Use indexes on frequently queried columns
- Avoid over-indexing
- Analyze performance using EXPLAIN
- Balance read vs write performance

---