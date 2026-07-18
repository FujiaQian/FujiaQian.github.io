---
layout: page
title: Bustub
---

[GitHub Repository](https://github.com/FujiaQian/bustub)

## Overview

BusTub is an educational relational database management system developed by the CMU Database Systems Teaching Team. This project focuses on implementing the core components of a modern relational database, including storage management, indexing, query execution, and concurrency control.

The implementation emphasizes correctness, scalability, and performance under concurrent workloads while following the architecture of a production database system.

---

## Architecture

The implemented components are organized as follows:

```text
                    SQL Query
                        │
                        ▼
              Volcano Execution Engine
                        │
        ┌───────────────┴───────────────┐
        ▼                               ▼
 Concurrent B+ Tree Index      Table Heap / Storage
        │                               │
        └───────────────┬───────────────┘
                        ▼
            Buffer Pool Manager (ARC)
                        │
                        ▼
          Asynchronous Disk Scheduler
                        │
                        ▼
                   Disk Storage
```

---

## My Contributions

Implemented the following major database components:

- Thread-safe Buffer Pool Manager
- Adaptive Replacement Cache (ARC) with fine-grained frequency tracking
- Asynchronous Disk Scheduler
- Concurrent B+ Tree
- Volcano-style Query Execution Engine

The implementation focuses on building a concurrent storage engine with efficient page management and scalable indexing.

---

## Buffer Pool Manager

Implemented a thread-safe buffer pool manager responsible for managing cached database pages.

Major features include:

- Page allocation and fetching
- Pin count management
- Dirty page tracking
- Page eviction
- Integration with asynchronous disk scheduling
- Adaptive Replacement Cache (ARC)

Compared with the standard ARC algorithm, the implementation introduces more fine-grained frequency tracking to improve adaptability under mixed access patterns while preserving the overall ARC framework.

---

## Concurrent B+ Tree

Implemented a concurrent B+ Tree supporting:

- Point lookup
- Insertion
- Deletion
- Iterator traversal
- Node split and merge
- Key redistribution
- Root adjustment

Concurrency is achieved through page guards and latch coupling, allowing multiple threads to safely access and modify the index.

---

## Query Execution

Implemented a Volcano-style query execution engine supporting relational operators and optimized physical execution strategies.

Implemented operators including:

- Sequential Scan
- Insert, Update, and Delete
- Aggregation with hash-based grouping
- Nested Loop Join
- Nested Index Join
- Hash Join using in-memory hash tables
- External merge sort for external-memory query processing

The execution engine provides a modular iterator-based architecture that separates query processing logic from storage management and enables efficient execution of complex relational queries.

---

## Performance

Benchmarked using the official BusTub benchmark on:

- **CPU:** AMD Ryzen 7 PRO 8840HS (8 cores / 16 threads)
- **Memory:** 32 GB RAM

Measured performance:

| Component | Workload | Throughput |
|-----------|----------|-----------:|
| Buffer Pool Manager | Sequential Scan | ~40K ops/s |
| Buffer Pool Manager | Random Access (Zipf θ = 0.8) | ~8K ops/s |
| Concurrent B+ Tree | Read | ~200K ops/s |
| Concurrent B+ Tree | Write | ~400K ops/s |

The implementation was profiled using Linux `perf` to identify synchronization bottlenecks and guide optimizations for cache replacement, page management, and concurrent index operations.

---

## Future Work

Later stages of BusTub introduce a rule-based query optimizer and additional execution optimizations, including predicate pushdown and join transformations such as Nested Loop Join to Hash Join.

Although these components are beyond the current implementation, they represent a natural extension toward a complete relational database engine.

---

## Technologies

C++17 · Database Internals · Concurrency · Storage Engine