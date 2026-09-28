# Linux Architecture, Processes and systemd

## 1. Linux Architecture

### Kernel

* The kernel is the core of Linux and manages CPU, memory, processes, filesystems, networking and hardware.
* Applications communicate with the kernel through system calls instead of directly accessing hardware.

### User Space

* User space is where normal applications, shells and services run.
* Examples include Bash, Python, Docker, nginx and other applications.

### Init / systemd

* After the kernel starts, it starts the first userspace process.
* On most modern Linux systems, this process is `systemd` with PID 1.
* `systemd` initializes the system and manages services throughout the system's lifetime.

## 2. Processes

* A process is a running instance of a program and has a unique Process ID (PID).
* Processes can create child processes, forming a parent-child process hierarchy.
* Linux uses mechanisms such as `fork()` to create processes and `exec()` to run a different program in a process.

## 3. Process States

* **Running:** The process is currently executing or ready to execute on the CPU.
* **Sleeping:** The process is waiting for an event such as I/O, network data or a timer.
* **Stopped:** The process has been suspended and is not currently executing.
* **Zombie:** The process has finished execution but its parent has not yet collected its exit status.
* **Orphan:** A process whose parent has terminated; it is adopted by another process, commonly PID 1.

## 4. systemd

* `systemd` is the system and service manager used by many modern Linux distributions.
* It starts services during boot, manages their lifecycle and handles service dependencies.
* `systemctl` is used to interact with systemd.

```bash
systemctl status nginx
systemctl start nginx
systemctl stop nginx
systemctl restart nginx
```

* `journalctl` can be used to view systemd journal logs and troubleshoot service failures.

## 5. Five Useful Linux Commands

| Command                      | Purpose                      |
| ---------------------------- | ---------------------------- |
| `ps aux`                     | View running processes       |
| `top`                        | Monitor CPU and memory usage |
| `systemctl status <service>` | Check a service's status     |
| `journalctl -u <service>`    | View service logs            |
| `kill <PID>`                 | Send a signal to a process   |
