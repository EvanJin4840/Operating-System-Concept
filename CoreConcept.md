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
