
### 1. Fundamental Concepts
* **Thread**: The basic unit of CPU utilization and a flow of execution within a process.
* **Shared Resources**: Code, data, and open files are shared by all threads in a process[cite: 22, 48].
* **Independent Resources**: Each thread maintains its own Thread ID, program counter (PC), register set, and stack[cite: 23, 24, 48].
* **TCB**: A data structure in the kernel used to manage thread-specific information like state and stack pointers[cite: 81, 82].

### 2. Primary Advantages
* **Responsiveness**: Keeps applications functional even during long-running or blocking tasks[cite: 112].
* **Economy**: Thread creation and switching are significantly cheaper than process-level operations[cite: 114].
* **Scalability**: Enables effective use of multi-core processors through parallel execution[cite: 115].

### 3. Parallelism vs. Concurrency
* **Parallelism**: Physically performing multiple tasks at the exact same time on multiple cores[cite: 134, 145].
* **Concurrency**: Managing multiple tasks so they all make progress, often via time-slicing on a single core[cite: 135, 140].
* **Amdahl's Law**: States that the serial portion of a program strictly limits the potential speedup from additional cores[cite: 172, 199].

### 4. Multithreading Models
* **Many-to-One**: Simple to implement but lacks parallelism and can cause total process blocking[cite: 271, 272].
* **One-to-One**: Provides high concurrency and is the standard for modern OSs like Linux and Windows[cite: 287, 290, 291].
* **Many-to-Many**: Offers flexibility by mapping multiple user threads to a pool of kernel threads[cite: 300, 301].

