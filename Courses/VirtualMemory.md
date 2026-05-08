# Chapter 10: Virtual Memory Summary

## 1. Virtual Memory Fundamentals
* **Separation of Logical/Physical Memory**: Allows execution of programs that are only partially in physical memory.
* **Benefits**: 
    * Logical address space can be larger than physical memory.
    * Allows address spaces to be shared by several processes.
    * More efficient process creation.
* **Sparse Address Space**: Virtual address space can contain "holes" for growing stack or heap.

## 2. Demand Paging & Page Faults
* **Concept**: Load pages into memory only when they are specifically requested.
* **Valid-Invalid Bit**: 
    * `v` (valid): Page is in memory.
    * `i` (invalid): Page is on disk or invalid address.
* **Page-Fault Handling**:
    1. Trap to the OS.
    2. Find a free frame from the **Free-Frame List**.
    3. Read the page from disk into the frame.
    4. Update the page table and restart the instruction.
* **Effective Access Time (EAT)**: `EAT = (1 - p) * ma + p * (page fault time)`, where `p` is the page fault rate.

## 3. Copy-on-Write (COW)
* **Mechanism**: Parent and child processes share the same pages initially after `fork()`.
* **Action**: A private copy is created only if a process modifies a shared page.
* **Impact**: Significant reduction in process creation overhead.

## 4. Page Replacement Algorithms
* **FIFO (First-In-First-Out)**: Simple to implement but suffers from **Belady’s Anomaly** (page faults can increase as frames increase).
* **Optimal**: Replaces the page that will not be used for the longest time (requires future knowledge).
* **LRU (Least Recently Used)**: Replaces the page that has not been used for the longest period.
* **Second-Chance (Clock)**: Uses a reference bit to approximate LRU; if a page is pointed to and its bit is 1, it gets a second chance (bit cleared to 0).

## 5. Frame Allocation & NUMA
* **Allocation Strategies**:
    * **Equal Allocation**: Each process gets an equal share.
    * **Proportional Allocation**: Frames allocated based on process size.
* **Global vs. Local Replacement**: Global allows a process to take frames from others; Local restricts replacement to its own frames.
* **NUMA**: In systems with non-uniform memory access, OS tries to allocate memory "close to" the CPU where the thread is running to minimize latency.

# Virtual Memory - Advanced Topics

## 1. Thrashing
* **Definition**: A state where a process spends more time paging than executing.
* **Cause**: Occurs when a process does not have "enough" frames, leading to a high page-fault rate and low CPU utilization.
* **Locality Model**: Programs move from one locality (set of pages used together) to another.
* **Working-Set Model**: 
    * Based on locality using a working-set window ($\Delta$).
    * Prevents thrashing by ensuring the system provides enough frames to satisfy the sum of all working sets.
* **Page-Fault Frequency (PFF)**: A direct approach to control thrashing by establishing upper and lower bounds on the allowable page-fault rate.

## 2. Kernel Memory Allocation
* **Requirements**: Often requires physically contiguous memory for hardware interfaces or specific data structures.
* **Buddy System**: 
    * Allocates memory in units sized as powers of 2 (2KB, 4KB, 8KB, etc.).
    * Advantage: Quickly coalesces unused adjacent chunks (buddies).
    * Disadvantage: Can cause internal fragmentation.
* **Slab Allocation**:
    * Uses "caches" consisting of one or more "slabs" (contiguous pages).
    * Each cache is populated with objects for specific kernel data structures (e.g., `task_struct`).
    * Eliminates fragmentation and allows fast allocation/deallocation.

## 3. Practical Considerations
* **Prepaging**: Loading all or some of the pages a process will need before they are referenced to reduce initial page faults.
* **Page Size**: Choosing a page size involves trade-offs:
    * **Smaller pages**: Less fragmentation, better locality.
    * **Larger pages**: Smaller page tables, better I/O efficiency, improved TLB reach.
* **TLB Reach**: The total amount of memory accessible from the TLB ($TLB\ Entries \times Page\ Size$).
* **Program Structure**: The way data is accessed significantly affects performance. For example, nested loops should match the memory layout of arrays (Row-major vs. Column-major) to minimize page faults.
* **I/O Interlock**: Pages involved in I/O operations must be "locked" or "pinned" in memory so they aren't selected as victims for replacement.

## 4. Linux Virtual Memory
* **System Design**: The Linux VM system is highly sophisticated, focusing on scalability and efficient memory management (often cross-referenced with OSTEP materials).