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

### 4. Computer System and Event Handling

- **Computer System Components:** A computer system consists of processors, memory, and I/O devices connected through communication buses.
- **Bus Architecture:** Hierarchical buses help reduce bottlenecks caused by differences in device speeds.
- **Instruction Execution:** The CPU repeatedly performs the fetch, decode, and execute cycle. The Program Counter (PC) identifies the next instruction to execute.
- **Trap:** A synchronous event caused by the currently executing instruction, such as a system call or division-by-zero exception.
- **Interrupt:** An asynchronous event triggered by external hardware, such as an I/O device or timer.
- **Event Handling:** The OS saves relevant execution state, transfers control to an appropriate kernel handler, and subsequently resumes execution or schedules another process.
- **Mode Switching:** Changes the CPU execution mode between user mode and kernel mode.
- **Context Switching:** Changes which process runs on the CPU by saving and restoring process execution state.

Context switching generally has higher overhead than mode switching because it involves changing process state and potentially address-space information.

### 5. Process Management

- **Program vs. Process:** A program is a collection of instructions stored as an executable file, while a process is a program currently in execution.
- **Program Execution:** Source code is compiled into object files, linked into an executable, and loaded into memory for execution.
- **Process Address Space:** A process contains memory regions such as the text segment, data segment, heap, and stack.
- **Memory Protection:** Each process operates within its own protected address space, preventing unauthorized access to other processes' memory.
- **Process Control Block (PCB):** The operating system maintains process information such as execution state, program counter, CPU registers, and resource-related information.
- **Process States:** Processes transition between states such as ready, running, and waiting, depending on CPU availability and I/O operations.
- **Context Switching:** The OS saves the current process's context and restores another process's context so execution can continue from its saved state.
Processes provide a fundamental abstraction for resource management, execution, and memory protection in an operating system.

### 6. CPU Scheduling

- **CPU Scheduling:** The operating system selects which ready process should execute on the CPU.
- **CPU and I/O Bursts:** Processes alternate between CPU computation and I/O waiting periods. CPU-intensive and I/O-intensive processes have different execution characteristics.
- **Preemptive Scheduling:** The OS can interrupt a running process and allocate the CPU to another process.
- **Non-Preemptive Scheduling:** A process retains the CPU until it blocks or terminates.

**Major Scheduling Algorithms:**
- **First-Come, First-Served (FCFS):** Executes processes in arrival order.
- **Shortest-Job-First (SJF):** Selects the process with the shortest CPU burst.
- **Priority Scheduling:** Allocates CPU time according to process priority.
- **Round Robin (RR):** Assigns each process a fixed time quantum.
- **Multilevel Queue / Feedback Queue:** Organizes processes into multiple scheduling queues.

**Scheduling Evaluation Criteria:**
- CPU Utilization: Percentage of time the CPU is actively used.
- Throughput: Number of processes completed per unit of time.
- Turnaround Time: Total time from arrival to completion.
- Waiting Time: Time spent waiting in the ready queue.
- Response Time: Time from arrival to the first CPU execution.
Different scheduling algorithms balance fairness, responsiveness, and system performance.

### 7. Interprocess Communication (IPC)

Interprocess Communication (IPC) enables processes to exchange data and cooperate while maintaining memory protection.

**Two Main IPC Models:**
- **Shared Memory:** Multiple processes access a shared memory region established by the kernel. Communication is efficient, but processes must coordinate concurrent access to avoid data inconsistency.
- **Message Passing:** Processes exchange messages through kernel-supported send and receive operations without directly sharing memory.

**Common IPC Mechanisms:**
- **Signals:** Notify processes about predefined events, such as SIGINT and SIGKILL.
- **Pipes:** Provide ordered, one-directional data communication between processes.
- **Message Queues:** Store messages in kernel-managed queues for asynchronous communication.
- **Sockets:** Enable communication between processes on the same or different machines, using protocols such as TCP or UDP.

**Synchronization:** Shared memory requires synchronization mechanisms, such as locks or semaphores, to prevent inconsistent results when processes access shared data concurrently.
IPC is essential for process cooperation, modular system design, and efficient data exchange.
