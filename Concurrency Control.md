- Complexity: Scheduling becomes more difficult as the number of CPUs increases.

- Homogeneous Processors: If all CPUs are identical, they can pull tasks from a common queue. However, complexity increases if a process must run on a specific processor.

- Load Sharing: A mechanism is needed to distribute the workload evenly across all processors. This can be done using separate queues for each CPU or a single shared queue.

- Symmetric Multiprocessing (SMP): Each processor is self-scheduling and manages its own tasks independently.

- Asymmetric Multiprocessing: A "Master-Slave" structure where one lead processor handles system data and scheduling, while others simply follow instructions.