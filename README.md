# xv6 Operating Systems Projects (University of Tehran)

This repository contains all 5 projects for the Operating Systems Laboratory course. The curriculum involved a hands-on, deep dive into the **xv6 operating system**, a modern re-implementation of Dennis Ritchie's and Ken Thompson's Unix Version 6 (v6) for the x86 platform.

Through this series of projects, I gained practical experience in kernel-level development by modifying and extending a real, functioning OS kernel.

## Core Concepts & Technologies

* **Operating System:** xv6 (a teaching OS from MIT)
* **Language:** C (for kernel and user-space programs)
* **Architecture:** x86 Assembly (for bootloading and low-level context switching)
* **Tools:** QEMU (emulator), GDB (debugger), Makefile (build system)
* **Key Topics:**
    * System Calls & Trap Handling
    * Process Management & Scheduling
    * Memory Management (Paging & Segmentation)
    * Synchronization (Spinlocks, Mutexes, Per-CPU Variables)
    * Inter-Process Communication (Shared Memory)

---

## Project Overview

* **Project 1: Introduction to xv6 & Console Enhancements**
    * An introduction to the xv6 architecture and boot process. Implemented advanced console features like command history, cursor navigation, and user-level applications.

* **Project 2: System Call Implementation**
    * Explored the system call trap mechanism and implemented new syscalls for file operations (`move_file`) and process metadata tracking (`get_most_invoked_syscall`).

* **Project 3: Multi-Level Feedback Queue Scheduler**
    * Replaced the default Round Robin scheduler with a sophisticated Multi-Level Feedback Queue (MLFQ) scheduler featuring weighted time-slicing and an aging mechanism.

* **Project 4: Synchronization and Per-CPU Variables**
    * Implemented kernel-level synchronization primitives, including a reentrant mutex and a lock-free, per-CPU system call counter to avoid race conditions.

* **Project 5: Shared Memory Management**
    * Extended the `xv6` memory manager to support POSIX-style shared memory regions between processes, complete with new syscalls for managing the shared segments.

---

## How to Run (General)

Each project folder is self-contained. To run a specific project:

1.  **Navigate to the project directory:**
    ```bash
    cd <project-folder-name>/
    ```
2.  **Build the xv6 image:**
    ```bash
    make
    ```
3.  **Run xv6 in the QEMU emulator:**
    ```bash
    make qemu
    ```
    (You can also use `make qemu-nox` for a console-only instance).
