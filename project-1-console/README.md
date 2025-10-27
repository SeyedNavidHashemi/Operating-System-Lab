# Project 1: Introduction to xv6 & Console Enhancements

This project served as the foundational introduction to the xv6 operating system. The objectives were to understand the kernel boot process, modify the console's input handling, and create new user-level applications that interact with the file system.

## Key Features Implemented

### 1. Kernel-Level Modifications

* **Custom Boot Message:**
    * Modified the kernel's `main.c` to display a custom message immediately after the standard boot messages.

* **Enhanced Console I/O:**
    * **Arrow Key Navigation:** Implemented cursor movement in the console, allowing the user to move the cursor left and right within the current command line.
    * **Command History:** Added a `history` command to display the last 10 commands. Users can also navigate this history using the **Up** and **Down** arrow keys to recall previous commands.
    * **Simple Copy/Paste:** Implemented a simple copy/paste buffer using `Ctrl+S` (to start recording) and `Ctrl+F` (to paste).
    * **Inline Arithmetic:** The console now automatically detects and evaluates simple numerical expressions (e.g., `a2+3b` is replaced with `a5b`).

### 2. User-Level Applications

* **Caesar Cipher:**
    * Developed two new user-level applications from scratch: `encode` and `decode`.
* **File I/O System Calls:**
    * Utilized fundamental file I/O system calls (`open`, `read`, `write`, `close`) to take string input and write the encrypted/decrypted output to a file named `result.txt`.
* **Build System Modification:**
    * Modified the xv6 `Makefile` to compile and link these new user-space programs into the bootable file system.
