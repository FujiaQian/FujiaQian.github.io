---
layout: page
title: RISC-V-CPU
---

[GitHub Repository](https://github.com/FujiaQian/RISC-V-CPU)

## Overview

This project implements a five-stage pipelined RISC-V processor from scratch in SystemVerilog and deploys it on an FPGA platform. The processor supports the RV32I base instruction set and implements a complete execution pipeline, branch prediction, exception handling, and virtual memory subsystem.

The project focuses on processor microarchitecture, control-flow optimization, memory hierarchy, and the hardware-software interface required to support operating systems.

---

## Architecture

The processor consists of the following major components:

- Five-stage instruction pipeline
- Pipeline control logic with hazard detection and forwarding
- Branch prediction unit with Branch Target Buffer (BTB)
- Exception and trap handling
- Instruction and data cache subsystem
- Virtual memory subsystem with MMU and TLB

```text
                    +-----------------------------+
                    |       Instruction Fetch     |
                    |                             |
                    |  Branch Prediction Unit     |
                    |          + BTB              |
                    +-----------------------------+
                                  |
                                  v
                    +-----------------------------+
                    |      Instruction Decode     |
                    +-----------------------------+
                                  |
                                  v
                    +-----------------------------+
                    |          Execute            |
                    | Branch Resolution           |
                    +-----------------------------+
                                  |
                                  v
                    +-----------------------------+
                    |       Memory Access         |
                    +-----------------------------+
                                  |
                                  v
                    +-----------------------------+
                    |        Write Back           |
                    +-----------------------------+


                    +-----------------------------+
                    | Pipeline Control Unit       |
                    | Hazard Detection            |
                    | Forwarding Logic            |
                    | Flush / Stall Control       |
                    +-----------------------------+

                                  |
                                  v

              Cache  <---->  MMU  <---->  TLB  <---->  Main Memory
```

---

## Pipeline Microarchitecture

Implemented a classic five-stage RISC-V pipeline:

- Instruction Fetch (IF)
- Instruction Decode (ID)
- Execute (EX)
- Memory Access (MEM)
- Write Back (WB)

Pipeline registers are inserted between stages to enable overlapped instruction execution and improve instruction throughput.

The pipeline implements comprehensive control mechanisms, including data hazard handling, operand forwarding, pipeline stalling, and control hazard mitigation.

---

## Branch Prediction

Implemented a Branch Target Buffer (BTB)-based branch prediction mechanism to reduce control hazards caused by branch instructions.

The branch prediction subsystem includes:

- Branch Target Buffer (BTB) for storing previously observed branch targets
- BTB lookup during the instruction fetch stage for early target prediction
- Predicted instruction fetch redirection without waiting for branch resolution
- BTB update logic after branch execution
- Branch misprediction detection and pipeline recovery

The BTB enables speculative instruction fetch along predicted control-flow paths, reducing branch penalties and improving pipeline utilization.

---

## Pipeline Control

Implemented pipeline control mechanisms required for correct execution:

- Data hazard detection between pipeline stages
- Operand forwarding to reduce unnecessary pipeline stalls
- Pipeline stalling for unresolved dependencies
- BTB-based branch prediction for control hazard mitigation
- Pipeline flushing after branch misprediction, exceptions, and control transfers

These mechanisms maintain precise execution semantics while improving overall processor throughput.

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

Implemented processor support for exception and trap handling.

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

- Instruction cache
- Data cache
- Memory access interface
- Cache management and control logic
- Memory access optimization

The cache subsystem reduces memory latency and improves execution efficiency.

---

## Virtual Memory

Implemented hardware support for virtual memory.

Features include:

- Multi-level page table translation
- Memory Management Unit (MMU)
- Translation Lookaside Buffer (TLB)
- Hardware page table walking
- Address translation and memory isolation

The implementation provides the memory protection and address translation mechanisms required by modern operating systems.

---

## FPGA Implementation

The processor is implemented entirely in SystemVerilog and synthesized for FPGA execution.

The modular RTL design separates pipeline stages, branch prediction logic, control units, and memory subsystems to improve maintainability, extensibility, and timing performance.

---

## Design Challenges

Major implementation challenges include:

- Coordinating pipeline control with hazard handling and branch prediction
- Designing BTB lookup and update logic within the instruction fetch stage
- Managing speculative instruction execution and pipeline recovery after branch misprediction
- Maintaining precise exceptions under pipelined execution
- Integrating virtual memory translation into the memory access pipeline
- Balancing modular RTL design with FPGA timing constraints

---

## Technologies

- SystemVerilog
- FPGA
- RISC-V (RV32I)
- Computer Architecture
- Pipeline Design
- Branch Prediction
- Branch Target Buffer (BTB)
- Speculative Execution
- Hazard Detection
- Forwarding
- Cache
- Virtual Memory
- MMU
- TLB