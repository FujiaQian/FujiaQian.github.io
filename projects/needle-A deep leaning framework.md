# Needle - A Deep Learning Framework

[link to my work](https://github.com/FujiaQian/DLSys_needle)

## Overview

Needle is a lightweight deep learning framework developed by the CMU Deep Learning Systems Teaching Team. This project focuses on implementing the core infrastructure of modern deep learning frameworks, including automatic differentiation, tensor runtime, backend execution, and GPU acceleration.

The implementation emphasizes modular framework design, efficient tensor computation, and extensibility across CPU and CUDA backends.

---

## Architecture

```text
              Neural Network Modules
                        │
                        ▼
              Automatic Differentiation
                        │
                        ▼
                 Tensor Runtime
                        │
         ┌──────────────┴──────────────┐
         ▼                             ▼
      CPU Backend                 CUDA Backend
         │                             │
         └──────────────┬──────────────┘
                        ▼
                 NDArray Storage
```

---

## My Contributions

Implemented the major components of the framework, including:

- Reverse-mode automatic differentiation engine
- NDArray runtime and tensor abstraction
- Tensor operator library
- CPU backend runtime
- CUDA backend runtime
- CUDA kernels for tensor operations
- Neural network modules
- Data loading and optimization utilities

The implementation provides a unified execution interface for deep learning workloads across heterogeneous hardware platforms.

---

## Automatic Differentiation

Implemented a reverse-mode automatic differentiation engine capable of constructing and traversing dynamic computation graphs.

Major features include:

- Dynamic computation graph construction
- Reverse graph traversal
- Automatic gradient propagation
- Gradient accumulation
- Broadcasting semantics
- Shape inference

The autograd engine serves as the foundation for neural network training.

---

## Tensor Runtime

Implemented the runtime responsible for tensor representation, memory layout, and backend dispatch.

Major components include:

- NDArray abstraction
- Shape, stride, and offset representation
- Zero-copy tensor views
- Compact tensor representation
- Backend-independent tensor interface
- Backend dispatch mechanism

The runtime enables efficient tensor manipulation while sharing a common execution interface across multiple backends.

---

## Tensor Operators

Implemented a comprehensive tensor operator library, including:

- Element-wise operators
- Matrix multiplication
- Broadcasting
- Reshape and transpose
- Stack and split
- Reduction operators

These operators serve as the computational foundation for higher-level neural network modules.

---

## CPU and CUDA Backend

Implemented both CPU and CUDA execution backends.

Major features include:

- Unified NDArray execution interface
- Device-specific memory allocation
- CUDA kernel launch infrastructure
- Efficient tensor indexing
- Parallel tensor execution

The backend architecture allows the same computational graph to execute transparently on either CPU or GPU.

---

## CUDA Optimization

Implemented optimized CUDA kernels for performance-critical tensor operations.

Optimization techniques include:

- Shared-memory optimization
- Warp-level parallel reduction
- Memory coalescing
- Thread/block-level parallel execution
- Optimized matrix multiplication kernels

These optimizations improve GPU utilization while maintaining a unified programming interface.

---

## Neural Network Modules

Implemented commonly used neural network components, including:

- Linear layers
- Activation functions
- Batch Normalization
- Layer Normalization
- Dropout
- Sequential containers
- Softmax-based loss functions
- SGD optimizer
- Adam optimizer

The framework supports training and inference for representative deep learning models, including MLPs, RNNs, and Transformer-based architectures.

---

## Validation

Validated the implementation using the official Needle test suite across both CPU and CUDA backends.

The framework maintains consistent execution behavior while supporting heterogeneous execution across CPU and GPU devices.

---

## Technologies

- Python
- CUDA
- Deep Learning Systems
- Automatic Differentiation
- Tensor Runtime
- GPU Computing
- Parallel Computing