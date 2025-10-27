# Project 3: Multi-Level Feedback Queue Scheduler

This project involved replacing the `xv6`'s default Round Robin (RR) scheduler with a comprehensive, three-level Multi-Level Feedback Queue (MLFQ) scheduler. The goal was to provide more sophisticated process priority management, prevent starvation, and fairly allocate CPU time.

## Key Features Implemented

* **Three-Level Queue Structure:**
    * **Level 1 (Highest Priority):** Round Robin (RR) with a 50ms time quantum.
    * **Level 2 (Medium Priority):** An approximate Shortest Job First (SJF) using a probabilistic "confidence" value.
    * **Level 3 (Lowest Priority):** Standard First Come First Served (FCFS).

* **Weighted Round Robin (WRR) Time-Slicing:**
    * Instead of a strict, fixed-priority system (where Level 1 must be empty to run Level 2), a WRR policy was implemented for time allocation *between* the queues.
    * Weights were assigned (L1=3, L2=2, L3=1) to ensure all levels get a share of CPU time, preventing starvation of lower-priority tasks.

* **Aging Mechanism:**
    * Implemented an aging system to promote processes. If a process waits for 800 ticks in a lower queue (L3 or L2), it is automatically promoted to the next-higher queue.

* **System Call Interface:**
    * Added new system calls to manage and observe the scheduler:
        * A syscall to set scheduler parameters (burst time, confidence) for processes in the SJF queue.
        * A syscall to manually change a process's queue.
        * A syscall to print a detailed table of all running processes, their current queue, wait time, and other scheduler-related statistics.
