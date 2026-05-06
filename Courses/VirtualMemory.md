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