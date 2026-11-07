# 20262R0136COSE34102
## Operating Systems Notes

### 1. Introduction to Operating Systems

An operating system manages hardware resources and provides services to applications. Its core responsibilities include process management, memory management, and resource allocation.

### 2. OS History and Core Concepts

- **Batch Processing:** Early operating systems executed jobs sequentially without user interaction during execution.
- **Spooling:** I/O requests can be buffered, allowing computation and I/O operations to overlap and improving system efficiency.
- **Multiprogramming:** Multiple programs are loaded into memory simultaneously. When one process waits for I/O, the CPU can execute another process to reduce idle time.
- **Time-Sharing:** CPU time is divided into time slices (time quanta). Processes take turns using the CPU, improving fairness and responsiveness.
- **Context Switching:** The operating system saves the execution state of the current process and restores another process's state to switch CPU execution.
These developments improved CPU utilization, resource sharing, and interactive computing.

### 3. OS Structure and System Calls

- **OS Design Goals:** Operating systems aim to achieve fairness, high performance, scalability, reliability, security, and usability. Trade-offs are necessary because these goals may conflict.
- **Policy vs. Mechanism:** A policy determines what the system should do, while a mechanism determines how to implement it.
- **Layering and Modularity:** Layering organizes components into hierarchical levels. Modularity divides the OS into functional units to manage complexity.
- **User Mode and Kernel Mode:** Applications normally execute in user mode, while the kernel runs with higher privileges to manage hardware and protected resources.
- **System Calls:** Applications request operating system services through system calls, which provide controlled access to kernel functionality.
- **Monolithic Kernel:** Kernel services operate in a shared kernel environment, reducing communication overhead but increasing dependencies.
- **Microkernel:** Services are separated into independent components, improving isolation and maintainability but introducing IPC overhead.
- **Virtualization:** Hypervisors enable multiple guest operating systems to share the hardware resources of a host machine.
