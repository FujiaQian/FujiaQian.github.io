# rCore

[link to my work](https://github.com/FujiaQian/rCore)

## Overview

rCore is a Unix-like operating system implemented from scratch in Rust for the RISC-V architecture. This project explores the implementation of modern operating system kernels, including process management, virtual memory, trap handling, synchronization, and file systems.

The implementation follows a layered architecture consisting of user applications, a system call interface, kernel subsystems, and the RustSBI firmware layer.

```text
                   User Applications
                           │
                           │
                 System Call Interface
                  ← Implemented
                           │
        ┌──────────────────────────────────┐
        │              Kernel              │
        │                                  │
        │ ✓ Process Management             │
        │ ✓ Virtual Memory                 │
        │ ✓ Trap Handler                   │
        │ ✓ Synchronization                │
        │ ✓ File System                    │
        └──────────────────────────────────┘
                           │
                        RustSBI
                           │
                RISC-V Privileged ISA
                           │
                    RISC-V Hardware
```

---

## My Contributions

Implemented the core kernel subsystems and the system call interface, including:

- Process management and context switching
- Trap handling and privilege-level transition
- System call dispatch and kernel-user interaction
- Virtual memory based on SV39 page tables
- Kernel synchronization primitives
- File system support for user applications

---

## Process Management

Implemented process lifecycle management, including process creation, scheduling, context switching, waiting, and termination.

Major components include:

- Process Control Block (PCB)
- Context switching
- Scheduler
- Parent-child process relationships

---

## Virtual Memory

Implemented a virtual memory subsystem based on the RISC-V SV39 architecture.

Features include:

- Multi-level page tables
- Address space abstraction
- Virtual-to-physical address translation
- Memory protection
- User/kernel memory isolation

---

## Trap Handling and System Calls

Implemented the complete trap handling path from user mode into the kernel.

Features include:

- Trap context save/restore
- Exception handling
- Timer interrupts
- System call dispatch
- User/kernel privilege transitions

---

## Synchronization

Implemented synchronization primitives for concurrent kernel execution.

Including:

- Spin locks
- Mutexes
- Semaphores
- Condition variables

These primitives are used to protect shared kernel data structures and coordinate concurrent execution.

---

## File System

Implemented the kernel file system interface supporting:

- File abstraction
- File descriptors
- Read/write operations
- Directory traversal

---

## Technologies

Rust · RISC-V · Operating Systems · Virtual Memory · Concurrency · Kernel Development