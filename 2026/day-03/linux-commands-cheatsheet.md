# Day 03 – Linux Commands Cheatsheet

## File System Commands

`pwd` – Shows the current directory.

`mkdir <name>` – Creates a new directory.

`ls` – Lists files and folders.

`ls -la` – Lists all files, including hidden files, with details.

`cd <directory>` – Changes into another directory.

`touch <file>` – Creates a new empty file.

`cat <file>` – Shows the content of a file.

`cp <source> <destination>` – Copies files or folders.

`mv <source> <destination>` – Moves or renames files or folders.

`rm <file>` – Deletes a file.

`rm -r <directory>` – Deletes a directory and its content.

## Process Management Commands

`ps aux` – Shows running processes.

`top` – Shows live CPU and memory usage.

`htop` – Shows an interactive process viewer.

`kill <PID>` – Stops a process by process ID.

`systemctl status <service>` – Shows the status of a systemd service.

`systemctl restart <service>` – Restarts a systemd service.

`journalctl -u <service>` – Shows logs for a specific service.

## Networking Troubleshooting Commands

`ping google.com` – Checks if a host is reachable.

`ip addr` – Shows IP addresses and network interfaces.

`curl google.com` – Sends a request to a website.

`nslookup <domain>` – Checks DNS and shows the IP address of a domain.

`dig <domain>` – Shows detailed DNS information for a domain.

## Disk and Memory Commands

`df -h` – Shows disk usage in a readable format.

`du -sh <directory>` – Shows the size of a directory.

`free -h` – Shows memory usage in a readable format.

## Why This Matters for DevOps

Linux commands are important for DevOps because many production issues are solved directly in the terminal. Commands like `journalctl`, `systemctl`, `ping`, `curl`, and `ip addr` help to check services, logs, networking, and system resources quickly.

