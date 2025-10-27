# Project 5: Shared Memory Management

This project extended the `xv6` memory management system to support POSIX-style shared memory. This allows multiple, independent processes to map the same region of physical memory into their respective virtual address spaces, enabling high-speed inter-process communication (IPC).

## Key Features Implemented

* **Global Shared Memory Table:**
    * Created a kernel-level table to manage all active shared memory segments.
    * Each entry tracks a unique ID, a pointer to the physical frame (page) allocated for it, and a reference counter to manage the segment's lifecycle.
    * The entire table is protected by a spinlock to ensure thread-safe access and modification from concurrent processes.

* **New System Calls:**
    * `open_sharedmem(int id)`: Allows a process to access (or create, if it's the first) a shared memory segment. It maps the corresponding physical page into the process's virtual address space and increments the reference count. It returns a `void*` pointer to the mapped memory.
    * `close_sharedmem(int id)`: Unmaps the shared memory from the process's address space and decrements the reference count. When the count reaches zero, the global table entry is removed and the physical page is freed.

* **User-Level Test Program:**
    * Developed an application to calculate factorials using multiple processes.
    * A parent process creates a shared memory space, and several child processes are forked to collaboratively read and write to this shared space to compute the result.
    * Synchronization primitives (e.g., a mutex from Project 4) were used to prevent race conditions on the shared data.
