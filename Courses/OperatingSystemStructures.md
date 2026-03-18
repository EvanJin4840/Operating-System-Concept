### 1. Operating System Services
Operating systems provide an environment for executing programs and offer services to both users and programs. 
* User-Oriented ServicesUser Interface: CLI, GUI, or Touchscreen interfaces. 
Program Execution: Loading and running programs.
I/O Operations: Managing input and output devices. 
File-system Manipulation: Reading, writing, and creating files/directories.
Communications: Exchange of information between processes. Error Detection: Detecting hardware/software errors (e.g., division by zero).
* System-Oriented Functions (Efficiency)
Resource Allocation: Assigning CPU, memory, and storage to multiple users/jobs. 
Logging/Accounting: Keeping track of resource usage.
Protection and Security: Ensuring controlled access to system resources.

### 2. System Calls
System calls provide an interface to the services made available by an OS.
- Mechanism: They function as "Function calls to the OS kernel" triggered via interrupts.
- Dual-Mode Transfer: They safely transfer control from User Mode (lesser privilege) to Kernel Mode (higher privilege).
- API vs. System Call: Most programs access services via high-level APIs (like the Standard C Library) rather than direct system calls.
- Common Examples (POSIX): open(), read(), write(), lseek(), fork(), wait().