# SQL Normalization – Technical Documentation

## Understanding Database Normalization & Normal Forms

---

## Introduction

Normalization is a database design technique used to organize tables
to reduce redundancy and improve data integrity.

Goals of Normalization:

- Eliminate duplicate data
- Ensure logical data storage
- Improve consistency
- Simplify maintenance

---

# 1. Why Normalization is Important

Without normalization:

- Data redundancy increases
- Update anomalies occur
- Insert anomalies occur
- Delete anomalies occur

Normalization helps create structured and efficient database schemas.

---

# 2. Types of Anomalies

## 🔹 Insert Anomaly
Cannot insert data without adding unrelated information.

## 🔹 Update Anomaly
Same data must be updated in multiple rows.

## 🔹 Delete Anomaly
Deleting one record removes unintended data.

---

# 3. Normal Forms

---

## 🔹 First Normal Form (1NF)

Rules:

- No repeating groups
- Each column contains atomic (indivisible) values
- Each record must be unique

Example (Not in 1NF):

| student_id | subjects        |
|------------|-----------------|
| 1          | Math, Science   |

Correct 1NF:

| student_id | subject |
|------------|----------|
| 1          | Math     |
| 1          | Science  |

---

## 🔹 Second Normal Form (2NF)

Rules:

- Must be in 1NF
- No partial dependency
- Non-key attributes must depend on the entire primary key

Example:

If table has composite key (student_id, course_id),
other columns must depend on both.

---

## 🔹 Third Normal Form (3NF)

Rules:

- Must be in 2NF
- No transitive dependency
- Non-key attributes should depend only on primary key

Example:

If:

student_id → department_id  
department_id → department_name  

Then department_name should be in a separate table.

---

## 🔹 Boyce-Codd Normal Form (BCNF)

Stronger version of 3NF.

Rule:

For every functional dependency:
X → Y

X must be a super key.

---

# 4. Higher Normal Forms (Brief)

- 4NF – Removes multi-valued dependencies
- 5NF – Removes join dependencies

Typically, databases are normalized up to 3NF or BCNF in practice.

---

# 5. Example: From Unnormalized to 3NF

Unnormalized Table:

| order_id | customer_name | product | price |

Problem:
Customer name repeats multiple times.

Step 1: Create Customers table

Customers:
| customer_id | customer_name |

Step 2: Create Orders table

Orders:
| order_id | customer_id |

Step 3: Create Products table

Products:
| product_id | product_name | price |

Step 4: Create Order_Items table

Order_Items:
| order_id | product_id |

Now database is normalized and redundancy reduced.

---

# 6. Advantages of Normalization

✔ Reduces redundancy  
✔ Improves data integrity  
✔ Simplifies updates  
✔ Saves storage space  
✔ Improves consistency  

---

# 7.Disadvantages of Normalization

- More joins required  
- Slightly complex queries  
- May reduce performance in heavy read systems  

Denormalization is sometimes used for performance optimization.

---

# 8. Conclusion

Normalization is a fundamental database design principle.

Key Takeaways:

- 1NF → Atomic values
- 2NF → No partial dependency
- 3NF → No transitive dependency
- BCNF → Stronger functional dependency rule

---