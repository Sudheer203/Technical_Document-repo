# SQL Joins – Technical Documentation

## Understanding Different Types of Joins in SQL

---

## Introduction

SQL Joins are used to retrieve data from multiple tables based on related columns.
Joins combine rows from two or more tables using a common key.

---

# 1. Why Do We Need Joins?

In relational databases, data is stored in multiple normalized tables.
To retrieve meaningful information, we combine tables using JOIN operations.

Example Tables:

**customers**
- id
- name

**orders**
- order_id
- customer_id
- amount

---

# 2. Types of Joins

---

## 🔹 1. INNER JOIN

Returns only matching rows from both tables.

Syntax:

    SELECT columns
    FROM table1
    INNER JOIN table2
    ON table1.column = table2.column;

Example:

    SELECT c.name, o.amount
    FROM customers c
    INNER JOIN orders o
    ON c.id = o.customer_id;

✔ Only customers who placed orders are returned.

---

## 🔹 2. LEFT JOIN (LEFT OUTER JOIN)

Returns all rows from left table and matching rows from right table.

Syntax:

    SELECT columns
    FROM table1
    LEFT JOIN table2
    ON table1.column = table2.column;

✔ Customers without orders will show NULL values.

---

## 🔹 3. RIGHT JOIN (RIGHT OUTER JOIN)

Returns all rows from right table and matching rows from left table.

Syntax:

    SELECT columns
    FROM table1
    RIGHT JOIN table2
    ON table1.column = table2.column;

---

## 🔹 4. FULL JOIN (FULL OUTER JOIN)

Returns all rows when there is a match in either table.

Syntax:

    SELECT columns
    FROM table1
    FULL JOIN table2
    ON table1.column = table2.column;

✔ Includes unmatched rows from both tables.

---

## 🔹 5. CROSS JOIN

Returns Cartesian product of both tables.

Syntax:

    SELECT columns
    FROM table1
    CROSS JOIN table2;

If table1 has 3 rows and table2 has 4 rows,
result = 12 rows.

---

## 🔹 6. SELF JOIN

A table joined with itself.

Example:

    SELECT A.name, B.name
    FROM employees A
    JOIN employees B
    ON A.manager_id = B.id;

Used for hierarchical data.

---

# 3. Join Comparison Table

| Join Type | Returns |
|------------|----------|
| INNER JOIN | Matching rows only |
| LEFT JOIN | All left + matching right |
| RIGHT JOIN | All right + matching left |
| FULL JOIN | All rows from both tables |
| CROSS JOIN | Cartesian product |
| SELF JOIN | Table joined with itself |

---

# 4. Join Execution Concepts

Database engines process joins using:

- Nested Loop Join
- Hash Join
- Merge Join

Performance depends on:

- Indexes
- Table size
- Query optimizer
- Join conditions
---

# 5. Conclusion

SQL Joins are fundamental for relational database queries.
Understanding join types and execution strategies is essential
for writing efficient SQL queries.

---



















