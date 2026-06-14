# Day 02 – Linux Architecture Notes

## Core Components of Linux

* **Kernel**: The core of Linux. It manages CPU, memory, devices, files, and processes.
* **User Space**: The area where user applications and commands run, for example `bash`, `ls`, `vim`, or `nginx`.
* **systemd**: The init system and service manager. It starts, stops, restarts, and monitors services.

## Processes

A process is a running program. Every command or application creates a process while it is running.

Common process states:

* **Running**: The process is active or ready to use the CPU.
* **Sleeping**: The process is waiting for something, like input or a file.
* **Stopped**: The process is paused.
* **Zombie**: The process has finished, but its parent process has not cleaned it up yet.

## Daily Linux Commands

* `ps aux` – Shows running processes.
* `top` – Shows live CPU and memory usage.
* `systemctl status <service>` – Checks the status of a service.
* `systemctl restart <service>` – Restarts a service.
* `journalctl -u <service>` – Shows logs for a specific service.

## Why This Matters for DevOps

Linux is the base operating system for many production servers. Understanding processes, systemd, and logs helps DevOps engineers debug crashed services, fix resource problems, and restore systems faster.

