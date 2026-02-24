# SQL Concepts – Technical Paper
## ACID Properties in Relational Database Systems

---

## Abstract

This technical paper provides a comprehensive explanation of the ACID
(Atomicity, Consistency, Isolation, Durability) properties that form the
foundation of reliable transaction processing in relational database systems.

The document explores theoretical foundations, internal mechanisms,
implementation techniques, real-world examples, and architectural components
that enable ACID compliance.

---

# 1. Introduction

Modern applications such as banking systems, e-commerce platforms, airline
reservation systems, and financial trading platforms require strict guarantees
for data correctness and reliability.

ACID properties ensure that:

- Transactions execute safely
- Data integrity is preserved
- Concurrent users do not corrupt data
- Committed data survives crashes

---

# 2. What is a Transaction?

A transaction is a sequence of SQL operations treated as a single logical unit
of work.

Example:

    BEGIN;
    UPDATE accounts SET balance = balance - 1000 WHERE account_id = 101;
    UPDATE accounts SET balance = balance + 1000 WHERE account_id = 202;
    COMMIT;

A transaction must either fully succeed or fully fail.

---

# 3. ACID Properties in Detail

---

## 3.1 🔹 Atomicity

### Definition
Atomicity guarantees that a transaction is indivisible —
either all operations succeed or none are applied.

### Failure Scenario

If the system crashes after debiting Account A but before crediting Account B,
the entire transaction is rolled back.

### Implementation Techniques

- Write-Ahead Logging (WAL)
- Undo Logs
- Transaction Logs
- Rollback Mechanisms

---

## 3.2 🔹 Consistency

### Definition
Consistency ensures the database transitions from one valid state to another.

All constraints must hold true:

- Primary Keys
- Foreign Keys
- CHECK constraints
- UNIQUE constraints
- NOT NULL constraints
- Triggers

Example:

    ALTER TABLE orders
    ADD CONSTRAINT fk_customer
    FOREIGN KEY (customer_id)
    REFERENCES customers(id);

---

## 3.3 🔹 Isolation

### Definition
Isolation ensures concurrent transactions do not interfere with each other.

### Concurrency Problems

- Dirty Reads
- Non-repeatable Reads
- Phantom Reads
- Lost Updates

### SQL Isolation Levels

1. Read Uncommitted
2. Read Committed
3. Repeatable Read
4. Serializable

Example:

    SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;

### Concurrency Control Mechanisms

- Row-Level Locking
- Table-Level Locking
- MVCC (Multi-Version Concurrency Control)
- Timestamp Ordering

---

## 3.4 🔹 Durability

### Definition
Durability guarantees that once a transaction commits, the changes are permanent.

### Implementation Techniques

- Write-Ahead Logging
- Redo Logs
- Checkpoints
- Disk Synchronization (fsync)
- Replication

After:

    COMMIT;

The data will survive power failure or system crash.

---

# 4. Internal Architecture Supporting ACID


### Components

**Transaction Manager** – Tracks transaction states  
**Lock Manager** – Controls concurrency  
**Log Manager** – Maintains recovery logs  
**Buffer Manager** – Handles memory-to-disk operations  

---

# 5. ACID Summary Table

| Property     | Guarantee |
|--------------|------------|
| Atomicity    | All or Nothing |
| Consistency  | Valid State Before & After |
| Isolation    | No Concurrent Interference |
| Durability   | Permanent After Commit |

---

# 6. Real-World Banking Example

    BEGIN;
    UPDATE accounts SET balance = balance - 500 WHERE id = 1;
    UPDATE accounts SET balance = balance + 500 WHERE id = 2;
    COMMIT;

| ACID Property | Applied Guarantee |
|--------------|-------------------|
| Atomicity | Both updates succeed or fail |
| Consistency | Total balance preserved |
| Isolation | No intermediate visibility |
| Durability | Changes survive crash |

---

# 7. ACID vs BASE (Brief Comparison)

| ACID | BASE |
|------|------|
| Strong Consistency | Eventual Consistency |
| Strict Transactions | High Availability |
| Immediate Integrity | Soft State |
| Used in RDBMS | Used in Distributed NoSQL |

---

# 8. Conclusion

ACID properties are the backbone of relational database reliability.

They ensure:

- Safe transaction execution
- Data integrity
- Controlled concurrency
- Crash recovery

Understanding ACID is essential for:

- Database Administrators
- Backend Developers
- Data Engineers
- System Architects

---

# References

- SQL Standard Documentation
- PostgreSQL Official Documentation
- Oracle Database Concepts Guide

---