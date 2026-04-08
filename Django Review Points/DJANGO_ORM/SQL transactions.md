# SQL Transactions – Understanding Database Transactions (Non-ORM Concept)

## 1. Introduction

A **SQL transaction** is a sequence of one or more database operations that are treated as **a single unit of work**.

These operations may include:

* `INSERT`
* `UPDATE`
* `DELETE`
* `SELECT`

A transaction ensures that **all operations either succeed together or fail together**.

If any operation fails, the database can **rollback (undo) all previous operations in that transaction**.

In simple words:

> **A transaction guarantees that database changes are safe, complete, and consistent.**

---

# 2. Why SQL Transactions Are Important

Databases often handle **critical data**, such as:

* Banking transactions
* Order processing
* Payment systems
* Inventory management

Without transactions, partial updates could happen.

Example problem:

1. Money is deducted from Account A
2. Money is not added to Account B because of a failure

This causes **data inconsistency**.

Transactions prevent such issues by ensuring **all steps complete successfully**.

---

# 3. Basic Transaction Commands

SQL provides several commands to control transactions.

| Command                        | Purpose                                   |
| ------------------------------ | ----------------------------------------- |
| `BEGIN` or `START TRANSACTION` | Starts a transaction                      |
| `COMMIT`                       | Saves changes permanently                 |
| `ROLLBACK`                     | Cancels changes                           |
| `SAVEPOINT`                    | Creates a checkpoint inside a transaction |

---

# 4. Example of a Transaction

Example of transferring money between accounts.

```sql
START TRANSACTION;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 500
WHERE account_id = 2;

COMMIT;
```

Explanation:

1. Transaction begins
2. ₹500 is deducted from account 1
3. ₹500 is added to account 2
4. `COMMIT` saves both changes permanently

---

# 5. Example of Rollback

If something goes wrong, we can undo the transaction.

```sql
START TRANSACTION;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

ROLLBACK;
```

Here:

* The deduction is cancelled
* The database returns to its previous state

---

# 6. Savepoints in Transactions

A **savepoint** allows partial rollback within a transaction.

Example:

```sql
START TRANSACTION;

INSERT INTO orders VALUES (1, 'Laptop');

SAVEPOINT step1;

INSERT INTO orders VALUES (2, 'Phone');

ROLLBACK TO step1;

COMMIT;
```

Result:

* First insert remains
* Second insert is removed

---

# 7. ACID Properties of Transactions

SQL transactions follow four important properties called **ACID**.

| Property        | Meaning                                       |
| --------------- | --------------------------------------------- |
| **Atomicity**   | All operations succeed or none succeed        |
| **Consistency** | Database remains valid after transaction      |
| **Isolation**   | Transactions do not interfere with each other |
| **Durability**  | Once committed, changes are permanent         |

### Example

If a bank transfer is committed:

* The system guarantees the money transfer is **permanent and safe**.

---

# 8. Real-World Example

Consider an **online shopping system**.

Steps during checkout:

1. Create order record
2. Reduce product inventory
3. Process payment

These steps must be inside **one transaction**.

If payment fails:

* The order should not be created
* Inventory should not be reduced

Transactions guarantee this behavior.

---

# 9. Advantages of SQL Transactions

Transactions provide many benefits:

* Protect data integrity
* Prevent incomplete updates
* Maintain database consistency
* Allow rollback when errors occur
* Support safe multi-user operations

---

# 10. Transactions in Databases

Most relational databases support transactions:

* MySQL
* PostgreSQL
* Oracle
* SQL Server
* SQLite

Different databases may have small variations, but the **core concept remains the same**.

---

# 11. Conclusion

SQL transactions are a fundamental concept in database systems.

Key points:

* A transaction groups multiple database operations into a single unit
* It ensures operations are completed safely
* If something fails, changes can be rolled back
* Transactions follow the **ACID principles** for reliability

Understanding SQL transactions is important for building **secure and reliable database applications**.

---
