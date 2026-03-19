1. Command Analysis: ./cpu A &
- The & Operator:
This symbol tells the shell to run the command in the "background." It allows the terminal to remain interactive while the process executes independently.

- Process Argument (A[example]):
The "A" is an input argument passed to the executable, used as a label to identify which process is printing the output.

- Observation and Learning:
When running multiple commands like "./cpu A & ./cpu B &", the OS interleaves their execution. You will see mixed output (e.g., A B A C...) because the OS is rapidly switching the CPU between them, demonstrating "Virtualization" and "Concurrency."

2. The Two Key Process Abstractions
- Logical Control Flow:

- Concept: Each process moves through instructions as if it has exclusive use of the CPU.

- Mechanism: Provided via "Time-sharing." The OS switches the CPU between processes so quickly that it creates an illusion of a continuous, uninterrupted flow of execution.

- Private Address Space:

- Concept: Each process perceives that it owns the entire memory range (from address 0 to the maximum) without interference from others.

- Mechanism: Provided via "Virtual Memory." The OS maps virtual addresses to different physical locations in RAM, ensuring isolation and security.

3. Context Switching and "Context"
* Definition:
The mechanism of stopping one process, saving its current state, and starting or resuming another process. This transition is performed by the OS kernel.

- What is "Context"?
It is the minimum set of state information required to resume a process.

- Hardware Context: CPU registers like the Program Counter (PC) and Stack Pointer (SP).

- Software Context: Kernel data such as Page Tables (memory maps) and File Descriptors.

4. Process vs. Thread Switching
- Process Context Switch:
Happens between threads of "different" processes. It is a "heavy" operation because the OS must switch the entire Virtual Address Space and flush the cache (TLB).

- Thread Context Switch:
Happens between threads within the "same" process. It is a "light" operation because the threads share the same address space. Only the CPU registers and stack information need to be swapped.