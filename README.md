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

### 8. Threads and Parallelism

- **Thread:** A single flow of execution within a process.
- **Multithreading:** Multiple threads execute within one process while sharing resources such as code, data, heap, and opened files.
- **Thread-Specific Resources:** Each thread maintains its own program counter, CPU registers, and stack.
- **Thread Context Switching:** Switching between threads in the same process is generally cheaper than switching between processes because the address space remains unchanged.

**Thread Management Models:**
- **User-Level Threads:** Managed by a user-space library without direct kernel awareness.
- **Kernel-Level Threads:** Managed and scheduled individually by the operating system.
- **Thread Pool:** Pre-creates reusable threads to reduce repeated thread creation overhead.

**Concurrency vs. Parallelism:**
- Concurrency allows multiple tasks to make progress through interleaved execution.
- Parallelism allows multiple tasks to execute simultaneously on different CPU cores.

**Parallelism Types:**
- Data Parallelism: Different subsets of data are processed using the same operations.
- Task Parallelism: Different computations execute concurrently.

**POSIX Thread APIs:**
- `pthread_create()` creates a new thread.
- `pthread_join()` waits for a specified thread to terminate.

Multithreading improves responsiveness, resource sharing, and parallel execution efficiency.

### 9. Virtual Memory and Paging

- **Virtual Memory:** Provides each process with its own logical address space, supporting memory isolation, transparency, and efficient physical memory utilization.
- **Address Translation:** Converts virtual addresses into physical addresses using hardware support such as the Memory Management Unit (MMU).
- **Contiguous Allocation:** Allocates a continuous physical memory region to a process using base and bound registers.
- **Allocation Strategies:** First-fit, best-fit, and worst-fit determine where available memory is assigned.
- **Segmentation:** Divides a process into logical regions, such as code, heap, and stack, which can be placed separately in physical memory.

**Paging:**
- Virtual memory is divided into fixed-size pages.
- Physical memory is divided into equally sized frames.
- A page table maps Virtual Page Numbers (VPNs) to Physical Frame Numbers (PFNs).
- Each process maintains its own page table.
- Page Table Entries (PTEs) contain frame mappings and protection/status flags.

**Translation Lookaside Buffer (TLB):**
- Caches recently used page-to-frame mappings.
- Reduces page table lookup overhead and improves memory access performance.

**Page Table Designs:**
- Multilevel page tables reduce memory overhead through hierarchical structures.
- Inverted page tables maintain mappings from the perspective of physical frames.

**Memory Fragmentation:**
- External Fragmentation: Free memory exists but is divided into non-contiguous regions.
- Internal Fragmentation: Unused space remains inside allocated memory units.

Paging avoids external fragmentation but may still introduce internal fragmentation.


