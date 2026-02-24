# SQL Transactions – Technical Documentation

## Understanding Database Transactions and Control Commands

---

## Introduction

A transaction in SQL is a sequence of one or more database operations
executed as a single logical unit of work.

Transactions ensure data integrity and reliability using ACID properties.

---

# 1. What is a Transaction?

A transaction groups multiple SQL statements so that:

- Either all statements succeed
- Or none of them are applied

Example:

    BEGIN;
    UPDATE accounts SET balance = balance - 1000 WHERE id = 1;
    UPDATE accounts SET balance = balance + 1000 WHERE id = 2;
    COMMIT;

---

# 2. Transaction Control Commands (TCL)

---

## 🔹 BEGIN / START TRANSACTION

Starts a new transaction.

    BEGIN;
    -- or
    START TRANSACTION;

---

## 🔹 COMMIT

Saves all changes permanently.

    COMMIT;

After COMMIT, changes cannot be rolled back.

---

## 🔹 ROLLBACK

Reverts all changes made during the transaction.

    ROLLBACK;

Used when an error occurs.

---

## 🔹 SAVEPOINT

Creates a checkpoint inside a transaction.

    SAVEPOINT sp1;

Rollback to savepoint:

    ROLLBACK TO sp1;

---

# 3. Example: Banking Transfer

    BEGIN;

    UPDATE accounts
    SET balance = balance - 500
    WHERE id = 1;

    UPDATE accounts
    SET balance = balance + 500
    WHERE id = 2;

    COMMIT;

If any update fails → ROLLBACK ensures consistency.

---

# 4. Autocommit Mode

Many databases use Autocommit by default.

In autocommit:

- Each SQL statement is treated as a separate transaction.
- Automatically committed after execution.

To disable:

    SET autocommit = 0;

---

# 5. Transaction States

1. Active
2. Partially Committed
3. Committed
4. Failed
5. Aborted

---

# 6. Isolation Levels in Transactions

    SET TRANSACTION ISOLATION LEVEL READ COMMITTED;

Isolation Levels:

- Read Uncommitted
- Read Committed
- Repeatable Read
- Serializable

These control concurrency behavior.

---

# 7. Advantages of Transactions

- Ensures data consistency  
- Prevents partial updates  
- Supports concurrency control  
- Enables safe error recovery  

---

# 8. Conclusion

Transactions are fundamental to reliable database systems.

They ensure:

- Data integrity
- Atomic execution
- Controlled concurrency
- Safe recovery from failures

---