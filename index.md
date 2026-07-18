# Fujia Qian's Projects

## RISC-V CPU on FPGA

A five-stage pipelined RISC-V processor implemented from scratch in SystemVerilog and deployed on FPGA.

Implemented the processor microarchitecture and hardware memory management subsystem, including:

- Five-stage pipeline with hazard detection, forwarding, stalling, and pipeline flushing
- RV32I instruction set and exception/trap handling
- Cache subsystem and memory access control
- Virtual memory support with paging, MMU, and TLB

Focused on processor microarchitecture, memory hierarchy, and hardware-software interfaces.

**Keywords:** SystemVerilog · FPGA · RISC-V · Computer Architecture · Virtual Memory

[More Details →](projects/RISC-V-CPU)

---

## rCore

A Unix-like operating system implemented from scratch in Rust for the RISC-V architecture.

Implemented core kernel subsystems, including:

- Kernel boot and privilege-level transitions
- Trap handling and system call interface
- Process management and context switching
- Virtual memory based on multi-level page tables
- Synchronization primitives and concurrent kernel data structures
- File system and user program support

Focused on operating system internals, virtual memory, concurrency, and kernel resource management.

**Keywords:** Rust · Operating Systems · RISC-V · Concurrency · Virtual Memory

[More Details →](projects/rCore)

---

## BusTub

A relational database management system developed on top of BusTub, an educational database system created by the CMU Database Systems Teaching Team.

Implemented major database engine components, including:

- Thread-safe Buffer Pool Manager with an enhanced Adaptive Replacement Cache (ARC) featuring fine-grained frequency tracking and asynchronous disk scheduling
- Concurrent B+ Tree with latch coupling and page guards
- Volcano-style query execution engine
- Rule-based query optimizer with logical-to-physical plan transformations
- External-memory operators including external merge sort and Grace hash join

Focused on storage engine design, concurrent indexing, query execution, and database performance.

**Keywords:** C++17 · Database Internals · Storage Engine · Query Processing · Concurrency

[More Details →](projects/bustub.md)

---

## Needle

A lightweight deep learning framework developed on top of Needle, an educational framework created by the CMU Deep Learning Systems Teaching Team.

Implemented the core infrastructure of a modern deep learning framework, including:

- Reverse-mode automatic differentiation engine
- NDArray runtime with shape, stride, backend dispatch, and zero-copy tensor views
- CPU and CUDA execution backends
- Optimized CUDA kernels for matrix multiplication, tensor reductions, and element-wise operators using shared memory, warp-level primitives, and memory coalescing
- Neural network modules, optimizers, and data loading utilities

Focused on tensor runtime design, automatic differentiation, and GPU acceleration for deep learning systems.

**Keywords:** Python · CUDA · Deep Learning Systems · Tensor Runtime · GPU Computing

[More Details →](projects/needle-A%20deep%20leaning%20framework)