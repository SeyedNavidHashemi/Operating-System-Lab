# Project 2: System Call Implementation

This project was a deep dive into the `xv6` system call mechanism. The project involved analyzing the trap-based transition from user-space to kernel-space and implementing a suite of new system calls to extend the kernel's functionality.

## Key Features Implemented

* **New Argument Passing (via Register):**
    * Implemented `create_palindrome(int num)`, which was modified to read its argument from a CPU register instead of the stack, providing insight into different Application Binary Interfaces (ABIs).

* **File System System Call:**
    * Implemented `move_file(const char* src_file, const char* dest_dir)` to perform a kernel-side file move operation, ensuring atomicity and correctness inside the kernel.

* **Process Metadata & Tracking:**
    * Modified the core process data structure (`struct proc`) to store metadata about system calls invoked by each process.
    * Implemented three new syscalls for process analysis and observability:
        * `sort_syscalls(int pid)`: Sorts the list of syscalls that have been invoked by a specific process.
        * `get_most_invoked_syscall(int pid)`: Returns the name and count of the most frequently used system call for a given process.
        * `list_all_processes()`: Lists all running processes, their PIDs, and their total system call counts.
