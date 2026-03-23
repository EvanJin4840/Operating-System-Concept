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

3. Context Switching
* Definition:
The mechanism of stopping one process, saving its current state, and starting or resuming another process. This transition is performed by the OS kernel.

- What is "Context"?
It is the minimum set of state information required to resume a process.

- Hardware Context: CPU registers like the Program Counter (PC) and Stack Pointer (SP).

- Software Context: Kernel data such as Page Tables (memory maps) and File Descriptors.

* Mapping Reality vs. Illusion

- The OS maintains a Page Table for each process. This table translates "Virtual Addresses" (which are identical for all processes) into unique "Physical Addresses" in RAM. This allows processes to run independently on a shared physical hardware.

4. Process vs. Thread Switching
- Process Context Switch:
Happens between threads of "different" processes. It is a "heavy" operation because the OS must switch the entire Virtual Address Space and flush the cache (TLB).

- Thread Context Switch:
Happens between threads within the "same" process. It is a "light" operation because the threads share the same address space. Only the CPU registers and stack information need to be swapped.

## Process States

**Running State**  
A process allocated to the processor and currently executing.

**Waiting State**  
A process waiting for an event (I/O completion, signal, etc.). Cannot execute immediately and must transition through Ready state.

**Ready State**  
A process ready for execution, waiting only for CPU allocation.

### Key Differences
- **Waiting → Ready → Running** (must pass through Ready)
- **Ready → Running** (immediate execution upon CPU allocation)

## Why PCB is Essential
PCB stores critical execution context:
- CPU registers (PC, SP, general registers)
- Memory management info
- I/O status, PID, scheduling info

Without PCB, resuming a preempted process would lose its execution state.

## Context Switching Process (PCB Perspective)

1. Process A (Running) → Interrupt occurs
- Save A's state to PCB_A (registers, PC, etc.)
- Change A to Waiting state
2. Scheduler selects Process B (from Ready queue)
- Restore B's previously saved state from - PCB_B to CPU registers
- Execute B starting from saved PC
3. Later, when A's waiting condition completes (I/O done, etc.)
- Change A to Ready state
- A waits in Ready queue for next CPU allocation

**Note**: 
- "Restore from PCB" implies the process **has been executed before** 
  (previously saved context exists)
- New processes use **PCB initialization** (PC = start address, registers = 0)
- **Context switching only occurs between processes with existing PCBs**