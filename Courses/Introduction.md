## What is the Operating System?
- Operating system (OS) is system software that manages computer hardware and software resources, and provides common services for computer programs.
- An OS is intermediary between the user and H/W
- Kernel + additional programs
    * Kernel: core of OS that runs at all times (System/application programs are not included)

## What Operating System Do?
- OS provides environment
    - Performs no useful function by itself.
    - However, the user can do something easily in the environment provided by OS.
- OS manages system resources
    - Let the users and the programs share the system resources in time and space.
    - Let the user use the computer hardware in an efficient manner.

* OS is in charge of making sure the system operates correctly and efficiently!

## Interrupt-Driven Program
- Interrupt: an asynchronous signal from hardware or software indicating the need for attention
    - Supported by H/W
    - Each type of interrupt is associated with a number (IRQ number)
    - Handled by interrupt handler
- Seperate segments of code determine what action should be taken for each type of interrupt.
    - Table of interrupt handler: interrupt vector