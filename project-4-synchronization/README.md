# Project 4: Synchronization and Per-CPU Variables

This project explored kernel-level concurrency and synchronization. The objectives were to implement a lock-free counting mechanism using per-CPU variables (to avoid contention) and to develop a new synchronization primitive, the reentrant mutex.

## Key Features Implemented

* **Per-CPU System Call Counter:**
    * Designed a highly concurrent and efficient system call counter that avoids lock contention by using per-CPU variables.
    * Modified the `trap.c` file to increment a local counter for the *current* CPU on each system call.
    * Implemented a new system call that safely sums the counters from all CPUs to return a global, weighted total (e.g., `open` x3, `write` x2, others x1).

* **Reentrant Mutex (Recursive Lock):**
    * Implemented a reentrant mutex (`reentrantlock`) from scratch.
    * This lock allows the *same* process (the owner) to acquire the lock multiple times without causing a deadlock, which is crucial for recursive functions that need to protect a shared resource.
    * The implementation tracks the `struct proc *owner` and a `int recursion` depth.
    * Provided the complete interface: `initreentrantlock`, `acquirereentrantlock`, and `releasereentrantlock`.
    * A user-level test program using a recursive function was created to validate its correctness.
