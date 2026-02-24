# SQL Aggregations & Filters – Technical Documentation

## Understanding GROUP BY, Aggregate Functions, and WHERE/HAVING Clauses

---

## Introduction

Aggregations and filtering are fundamental concepts in SQL used to analyze,
summarize, and extract meaningful insights from data.

This document explains:

- Aggregate Functions
- GROUP BY clause
- WHERE clause
- HAVING clause
- Practical examples
- Performance considerations

---

# 1. Aggregate Functions

Aggregate functions perform calculations on multiple rows and return a single result.

Common Aggregate Functions:

- COUNT()
- SUM()
- AVG()
- MIN()
- MAX()

Example:

    SELECT COUNT(*) FROM employees;

    SELECT SUM(salary) FROM employees;

---

# 2. GROUP BY Clause

The GROUP BY clause groups rows that have the same values in specified columns.

Example:

    SELECT department, COUNT(*)
    FROM employees
    GROUP BY department;

This returns employee count per department.

---

# 3. WHERE Clause (Row Filtering)

The WHERE clause filters rows BEFORE aggregation.

Example:

    SELECT *
    FROM employees
    WHERE salary > 50000;

Example with aggregation:

    SELECT department, COUNT(*)
    FROM employees
    WHERE salary > 50000
    GROUP BY department;

✔ WHERE filters individual rows.

---

# 4. HAVING Clause (Group Filtering)

The HAVING clause filters AFTER aggregation.

Example:

    SELECT department, COUNT(*)
    FROM employees
    GROUP BY department
    HAVING COUNT(*) > 5;

✔ HAVING filters groups, not individual rows.

---

# 5. WHERE vs HAVING

| Feature | WHERE | HAVING |
|----------|--------|---------|
| Filters | Rows | Groups |
| Used With | SELECT | GROUP BY |
| Can Use Aggregates | No | Yes |
| Execution Order | Before GROUP BY | After GROUP BY |

---

# 6. Combining Aggregation & Filtering

Example:

    SELECT department, AVG(salary)
    FROM employees
    WHERE salary > 30000
    GROUP BY department
    HAVING AVG(salary) > 60000;

Execution Order:

1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY

---

# 7. Practical Examples

### Total Sales Per Year

    SELECT year, SUM(amount) AS total_sales
    FROM sales
    GROUP BY year;

### Top Performing Departments

    SELECT department, SUM(sales) AS total_sales
    FROM employees
    GROUP BY department
    HAVING SUM(sales) > 100000;

---

# 8. Conclusion

Aggregations and filters are essential for data analysis in SQL.

Key Concepts:

- Aggregate functions summarize data
- GROUP BY creates data groups
- WHERE filters rows
- HAVING filters groups

Mastering these concepts improves query performance
and analytical capability.

---