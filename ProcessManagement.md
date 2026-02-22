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