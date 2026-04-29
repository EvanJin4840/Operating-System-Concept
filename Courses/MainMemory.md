# Chapter 9: Main Memory

## 1. Advanced Page Table Structures
* **Hierarchical Paging**: Breaks the logical address space into multiple tables. A common solution is the two-level page table (forward-mapped page table).
* **Hashed Page Tables**: Common in large address spaces (> 32 bits). The virtual page number is hashed into a table that contains a chain of elements.
* **Inverted Page Table**: Tracks all physical pages instead of logical pages. Only one inverted page table exists in the whole system, significantly reducing memory overhead.

## 2. Swapping and Performance
* **Definition**: A process can be swapped temporarily out of memory to a backing store and brought back later for continued execution.
* **Context Switch Time**: The major part of swap time is transfer time, which is proportional to the amount of memory swapped.
* **Mobile Systems**: Swapping is typically not supported on mobile platforms due to flash memory limitations (limited write cycles and poor throughput).
* **Alternative Methods**: iOS and Android free memory by terminating apps or asking them to relinquish allocated memory.

## 3. Intel 32 and 64-bit Architectures
* **IA-32 (IA-32 Architecture)**: Supports both segmentation and paging. It uses a two-level paging scheme for 4 KB pages.
* **PAE (Page Address Extension)**: Enables 32-bit applications to access up to 64 GB of physical memory by expanding to a 3-level paging scheme.
* **x86-64**: The current generation architecture implemented with 48-bit addressing and four levels of paging hierarchy.
* Supports multiple page sizes: 4 KB, 2 MB, and 1 GB.