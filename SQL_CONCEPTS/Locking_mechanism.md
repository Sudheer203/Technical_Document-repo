# SQL Locking Mechanism – Technical Documentation

## Understanding Concurrency Control and Locks in Databases

## Introduction

Locking is a concurrency control mechanism used by database systems
to ensure data consistency and isolation when multiple transactions
access the same data simultaneously.

Locks prevent conflicting operations from corrupting data.

---

# 1. Why Locking is Required

In multi-user environments:

- Multiple transactions may read/write same data
- Without locks → Dirty reads, lost updates, inconsistency
- Locks enforce isolation (ACID property)

---

# 2. Types of Locks

---

## 🔹 Shared Lock (S Lock)

- Used for read operations
- Multiple transactions can hold shared locks simultaneously
- Prevents data from being modified

Example:

    SELECT * FROM employees WHERE id = 1;

---

## 🔹 Exclusive Lock (X Lock)

- Used for write operations (INSERT, UPDATE, DELETE)
- Only one transaction can hold exclusive lock
- Prevents both reads and writes by others

Example:

    UPDATE employees SET salary = 70000 WHERE id = 1;

---

# 3. Lock Granularity

Lock granularity defines the level at which locks are applied.

- Row-level locking
- Page-level locking
- Table-level locking
- Database-level locking

Finer granularity → Better concurrency  
Coarser granularity → Less overhead

---

# 4. Intent Locks

Used in hierarchical locking (table → page → row).

Types:

- Intent Shared (IS)
- Intent Exclusive (IX)
- Shared with Intent Exclusive (SIX)

These indicate intention to place locks at lower levels.

---

# 5. Two-Phase Locking (2PL)

Ensures serializability.

Phases:

1. Growing Phase → Acquire locks
2. Shrinking Phase → Release locks

No lock can be acquired after a lock is released.

---

# 6. Deadlocks

A deadlock occurs when:

Transaction A waits for Transaction B  
Transaction B waits for Transaction A

Example:

T1 locks Row1 → waits for Row2  
T2 locks Row2 → waits for Row1  

Database resolves by aborting one transaction.

---

# 7. Locking vs MVCC

Some databases use Multi-Version Concurrency Control (MVCC):

- Readers do not block writers
- Writers do not block readers
- Uses row versions instead of strict locks

Improves performance in high-concurrency systems.

---

# 8. Advantages of Locking

✔ Ensures isolation  
✔ Prevents dirty reads  
✔ Maintains consistency  
✔ Supports ACID compliance  

---

# 9. Conclusion

Locking is essential for concurrency control in relational databases.

Understanding:

- Lock types
- Lock granularity
- Two-phase locking
- Deadlocks
---
