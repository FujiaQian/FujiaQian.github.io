---
layout: page
title: RISC-V-CPU
---

[GitHub Repository](https://github.com/FujiaQian/RISC-V-CPU)

## Overview

This project implements a five-stage pipelined RISC-V processor from scratch in SystemVerilog and deploys it on an FPGA platform. The processor supports the RV32I base instruction set and implements a complete execution pipeline, exception handling, and virtual memory subsystem.

The project focuses on processor microarchitecture, memory hierarchy, and the hardware-software interface required to support operating systems.

---

## Architecture

The processor consists of the following major components:

- Five-stage instruction pipeline
- Pipeline control logic
- Exception and trap handling
- Memory subsystem
- Virtual memory subsystem

```text
                    +-------------------------+
                    |     Instruction Fetch   |
                    +-------------------------+
                                │
                                ▼
                    +-------------------------+
                    |    Instruction Decode   |
                    +-------------------------+
                                │
                                ▼
                    +-------------------------+
                    |         Execute         |
                    +-------------------------+
                                │
                                ▼
                    +-------------------------+
                    |      Memory Access      |
                    +-------------------------+
                                │
                                ▼
                    +-------------------------+
                    |       Write Back        |
                    +-------------------------+

                     ▲
                     │
         Pipeline Hazard Detection & Forwarding

                     │
                     ▼
          Exception / Trap Handling

                     │
                     ▼
      Cache ── MMU ── TLB ── Main Memory
```

---

## Pipeline Microarchitecture

Implemented a classic five-stage RISC-V pipeline:

- Instruction Fetch (IF)
- Instruction Decode (ID)
- Execute (EX)
- Memory Access (MEM)
- Write Back (WB)

Pipeline registers are inserted between stages to enable overlapped instruction execution.

---

## Pipeline Control

Implemented pipeline control mechanisms required for correct execution:

- Data hazard detection
- Operand forwarding
- Pipeline stalling
- Control hazard handling
- Pipeline flushing after exceptions and control transfers

These mechanisms improve processor throughput while maintaining correctness.

---

## Instruction Set Support

Implemented the RV32I base instruction set, including:

- Integer arithmetic and logical instructions
- Branch and jump instructions
- Load/store instructions
- Immediate operations

The processor correctly executes user programs compiled for the RV32I ISA.

---

## Exception and Trap Handling

Implemented processor support for exception handling.

Supported mechanisms include:

- Illegal instruction detection
- Environment calls (ECALL)
- Exception dispatch
- Trap vector control
- Context redirection after exceptions

The exception subsystem provides the hardware foundation required by an operating system.

---

## Memory Subsystem

Implemented the processor memory subsystem, including:

- Instruction and data cache
- Memory access interface
- Cache management
- Memory access optimization

The cache subsystem reduces memory latency and improves execution efficiency.

---

## Virtual Memory

Implemented hardware support for virtual memory.

Features include:

- Multi-level page table translation
- Memory Management Unit (MMU)
- Translation Lookaside Buffer (TLB)
- Paging mechanism

The implementation enables address translation and memory isolation required by modern operating systems.

---

## FPGA Implementation

The processor is implemented entirely in SystemVerilog and synthesized for FPGA execution.

The modular RTL design separates pipeline stages, control logic, and memory subsystems to improve maintainability and extensibility.

---

## Design Challenges

Major implementation challenges include:

- Coordinating pipeline control with hazard handling
- Maintaining precise exceptions under pipelined execution
- Integrating virtual memory translation into the memory access path
- Balancing modularity with timing constraints in RTL design

---

## Technologies

- SystemVerilog
- FPGA
- RISC-V (RV32I)
- Computer Architecture
- Pipeline Design
- Virtual Memory
- Cache
- MMU
- TLB