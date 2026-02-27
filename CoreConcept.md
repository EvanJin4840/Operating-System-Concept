what is the operating system?
core that manages the computer hardware but it’s also the foundation for all your application

The Kernel: consists of system program and application program.
This is the core part of the OS that remains running at all times on the computer.

Interface Provider: The kernel acts as a bridge, providing essential interfaces for both system programs and application programs to interact with the hardware.

The dominant architecture today is multiprocessor(parallel systems, multi-core systems)

1. Defining the Operating System (OS)
No Universal Definition: There is no single, universally accepted definition of what an operating system is.

2. Modern Computer System Architecture
Structure: A modern system consists of one or more CPUs and multiple device controllers (e.g., disk, USB, etc.).

The System Bus: All these components are connected through a common bus that provides access to shared memory.

Operational Logic: The CPU communicates with the RAM and various controllers (like the disk and USB controllers) through this bus to move data and execute tasks.

3. Computer Startup: Bootstrapping
Booting: The process of turning on a computer and starting the operating system is called "booting."

Bootstrap Program: To start the computer, a small initial program called the bootstrap program must be executed to initialize the system and load the kernel.

4. The Interrupt Mechanism
Definition: An interrupt is a signal sent to the CPU to inform it that a specific event has occurred.

Example: When you press the 'A' key on a keyboard, the hardware generates an interrupt to let the system know that an input event needs to be handled.

5. Von Neumann Architecture
* Key Principles of Von Neumann Architecture
- Instruction-Based Definition (Core Principle): This architecture defines a computer by its Instruction Set, where the hardware is built to execute a specific set of commands.

- Stored Program Concept: Both instructions (code) and data are stored in the same read-write memory. This allows a computer to be "reprogrammed" without changing its physical hardware.

- Uniform Memory Space: The CPU treats instructions and data the same way. They share a single address space and a single communication bus.

- Sequential Execution Cycle: By default, the CPU fetches and executes instructions one by one in a strict linear order, unless told otherwise (e.g., by a jump instruction).

- Binary Representation: All information—whether it is a number, a character, or a complex instruction—is represented in binary (0s and 1s).

- The Von Neumann Bottleneck: Since instructions and data share the same bus, the CPU must wait for memory access, creating a performance limit in modern high-speed computing.