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