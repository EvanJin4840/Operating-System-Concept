1. VAX/VMS: Overcoming Hardware LimitsDeveloped in the 1970s, VAX/VMS used clever software to hide hardware flaws.  Memory Pressure: Because VAX had very small 512-byte pages, page tables could become huge. To save memory, VMS placed user page tables in kernel virtual memory, allowing them to be swapped to disk.  Page Replacement: Since the hardware lacked a "reference bit," VMS used Segmented FIFO. It moved evicted pages to global "second-chance" lists (clean and dirty) so they could be reclaimed quickly if needed again.

2. Linux: Flexibility and ScaleLinux runs on everything from phones to massive datacenters.  Kernel Addresses: Linux uses Kernel Logical Addresses (directly mapped to physical memory for speed and DMA) and Kernel Virtual Addresses (for large, non-contiguous buffers).  Huge Pages: To improve performance for "big memory" apps, Linux supports Huge Pages (2MB or 1GB), which reduce TLB misses.  Page Cache: It uses a 2Q Replacement algorithm, which is better than standard LRU for handling large file scans.

3. Key Performance & Security FeaturesBoth systems use "lazy" optimizations and defensive measures.  
+ Lazy Optimizations:
- Demand Zeroing: Only zeroes out a memory page when a process actually touches it.  
- Copy-on-Write (COW): Shares memory pages between processes (like after a fork()) and only copies them if one process tries to write to them.  
+ Security Measures:
- NX Bit: Prevents malicious code from executing in the stack.  
- ASLR: Randomizes where code and data are located in memory to make hacking (like ROP attacks) much harder.  KPTI: Isolates kernel memory from user processes to protect against the Meltdown attack.
- KPTI: Isolates kernel memory from user processes to protect against the Meltdown attack.