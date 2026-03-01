* Process vs. Thread: A process is a program in execution with its own address space. A thread is a unit of execution within a process that shares the process's resources.

* Context Switching: The process of saving the state of a CPU (in the PCB - Process Control Block) so it can be restored and resume execution later.

- Process Switch: High overhead because it requires flushing the TLB (Translation Lookaside Buffer) and reloading memory maps.
- Thread Switch: Low overhead because the address space remains the same, keeping the CPU cache and TLB valid.

* IPC (Inter-Process Communication): Mechanisms like Shared Memory or Message Passing that allow processes to communicate.

* Overhead: The "extra cost" (time/CPU cycles) of switching.

### Process States
Ready: In the queue, waiting for CPU allocation.
Running: Currently executing instructions on the CPU.
Waiting / Blocked: Waiting for an event (I/O, Lock, or Signal).
Note: In PDC, "Blocked" often specifically refers to waiting for a Mutex/Lock.
Zombie: Process finished execution but its PCB remains until the parent reads its exit status (Reaping).

### Synchronization (Crucial for PDC)
Race Condition: When multiple threads access shared data simultaneously, leading to unpredictable results.

Critical Section: The specific part of the code that accesses shared resources.

Mutual Exclusion (Mutex): A lock that ensures only one thread enters the Critical Section at a time.

Semaphore: A counter-based sync tool for managing multiple instances of a resource.

Deadlock: A "stale-mate" where threads are stuck waiting for each other to release resources.

### Advanced Hardware Concepts
Cache Coherence: Ensuring all CPU cores see the most recent data (e.g., MESI Protocol). It prevents different cores from having different values for the same variable in their local caches.

Memory Barrier (Fence): An instruction that prevents the CPU or Compiler from reordering memory operations. It ensures that operations before the barrier are completed before those after it.

### Semaphores
A Semaphore is a signaling mechanism used to manage access to critical sections for one or more processes.
1. Operations ($Wait$ & $Signal$)
- wait() ($P$ operation): Decreases the semaphore value. If the value becomes less than $0$, the process enters the waiting queue.
- signal() ($V$ operation): Increases the semaphore value. If there are waiting processes, it wakes one up.
2. Types of Semaphores
- Binary Semaphore: The value is restricted to $0$ or $1$. It is primarily used for Mutual Exclusion (Mutex).
- Counting Semaphore: The value can be greater than $1$. It is used to manage a limited number of identical resources (e.g., three available slots in a facility).
- 1.3 Execution OrderingSemaphores can enforce a specific execution sequence between processes.
Example: Process $P2$ can be designed to $wait()$ until Process $P1$ finishes its task and sends a $signal()$.
### Mutex vs. Binary Semaphore
While similar, these two mechanisms have distinct differences in ownership and priority management.

| Feature | Mutex | Binary Semaphore |
| :--- | :--- | :--- |
| **Ownership** | **Exists.** Only the process that locked it can unlock it. | **None.** Any process can send a $signal()$ to release it. |
| **Priority Inheritance** | **Supported.** Temporarily boosts priority to prevent inversion. | **Not Supported.** System cannot predict the releaser. |

* Conclusion: Use Mutex for simple mutual exclusion. Use Semaphores for resource counting or task synchronization.