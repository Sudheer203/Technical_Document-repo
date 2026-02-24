# CAP Theorem -- Technical Documentation

## Understanding Consistency, Availability, and Partition Tolerance

---

# 1. Introduction

The CAP Theorem was introduced by Eric Brewer in 2000 and later formally
proven by Seth Gilbert and Nancy Lynch.

CAP stands for:

-   **C** -- Consistency
-   **A** -- Availability
-   **P** -- Partition Tolerance

---

# 2. The CAP Theorem Statement

In the presence of a network partition, a distributed system must choose
between Consistency and Availability.

It is impossible to guarantee all three properties at the same time.

---

# 3. The Three Properties

## 🔹 Consistency (C)

Every read receives the most recent write or an error. All nodes see the
same data at the same time.

## 🔹 Availability (A)

Every request receives a response, even if some nodes are down. The
response may contain stale data.

## 🔹 Partition Tolerance (P)

The system continues operating despite network failures between nodes.

---

# 4. Why Partition Tolerance is Mandatory

In real distributed systems, network failures are unavoidable.
Therefore, systems must tolerate partitions and choose between:

-   CP (Consistency + Partition Tolerance)
-   AP (Availability + Partition Tolerance)

---

# 5. System Types

## CP Systems

-   Maintain strong consistency
-   Sacrifice availability during partitions

## AP Systems

-   Maintain availability
-   May return stale data during partitions

## CA Systems

-   Possible only when no partitions exist
-   Typically single-node systems

---

# 6. CAP vs ACID

  | Feature      |  ACID                     | CAP
  ---------------|---------------------------|--------------
  |Focus        |  Transaction Reliability  |  Distributed Trade-offs
  |Scope        | Single Database           | Distributed Systems
  |Failure Type | Crash Recovery            | Network Partition
  |Consistency  | Strong                    | Trade-off Based

---

# 7. Visual Representation

        Consistency
             ▲
             |

Availability -------- Partition Tolerance

During partition → choose Consistency or Availability.

------------------------------------------------------------------------

# 8. Conclusion

The CAP Theorem is fundamental for designing distributed systems. It
explains why trade-offs are necessary in large-scale architectures.

------------------------------------------------------------------------