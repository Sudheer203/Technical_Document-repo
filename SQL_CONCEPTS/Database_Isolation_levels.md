# Database Isolation Levels – Technical Documentation

## Understanding Transaction Isolation in SQL

---

## Introduction

Isolation levels define how transactions interact with each other
in a concurrent database environment.

They control visibility of uncommitted data and prevent
concurrency anomalies.

Isolation is one of the ACID properties.

---

# 1. Why Isolation Levels Are Needed

In multi-user systems, multiple transactions may:

- Read the same data
- Modify the same rows
- Execute simultaneously

Without isolation control → data inconsistency occurs.

---

# 2. Concurrency Problems

## 🔹 Dirty Read
Reading uncommitted data from another transaction.

## 🔹 Non-Repeatable Read
Row data changes between two reads in same transaction.

## 🔹 Phantom Read
New rows appear when re-executing a query.

## 🔹 Lost Update
One transaction overwrites another transaction’s update.

---

# 3. Standard Isolation Levels (SQL Standard)

---

## 🔹 1. Read Uncommitted

- Allows dirty reads
- Lowest isolation
- Highest concurrency
- Rarely used in practice

---

## 🔹 2. Read Committed

- Prevents dirty reads
- Allows non-repeatable reads
- Default in many databases

Example:

    SET TRANSACTION ISOLATION LEVEL READ COMMITTED;

---

## 🔹 3. Repeatable Read

- Prevents dirty reads
- Prevents non-repeatable reads
- May allow phantom reads (depending on DB engine)

Example:

    SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;

---

## 🔹 4. Serializable

- Highest isolation level
- Prevents dirty reads
- Prevents non-repeatable reads
- Prevents phantom reads
- Transactions behave as if executed sequentially

Example:

    SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;

---

# 4. Isolation Level Comparison

| Isolation Level | Dirty Read | Non-Repeatable Read | Phantom Read |
|-----------------|------------|--------------------|--------------|
| Read Uncommitted | yes | yes | yes |
| Read Committed   | no| yes | yes|
| Repeatable Read  | no | no | - |
| Serializable     | no | no | no |

---

# 5. Implementation Mechanisms

Databases implement isolation using:

- Row-level locks
- Table-level locks
- Multi-Version Concurrency Control (MVCC)
- Two-Phase Locking (2PL)

---

# 6. Choosing the Right Isolation Level

- Use Read Committed for general applications  
- Use Repeatable Read for financial systems  
- Use Serializable for critical consistency  
- Avoid Read Uncommitted in production  

Higher isolation → Lower concurrency  
Lower isolation → Higher performance  

---

# 7. Conclusion

Isolation levels balance consistency and performance
in concurrent database systems.

---