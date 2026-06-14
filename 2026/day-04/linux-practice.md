# Day 04 – Linux Practice: Processes and Services

## Process Checks

### Command 1

```bash
ps aux | head
```

Output:

```text
PASTE YOUR OUTPUT HERE
```

Note:
This command shows running processes. I noticed that PID 1 is `/sbin/init`, which is the first process started by the system. I also saw kernel processes like `kthreadd` and `kworker`.

### Command 2

```bash
top -b -n 1 | head
```

Output:

```text
PASTE YOUR OUTPUT HERE
```

Note:
This command shows a snapshot of system resource usage, including CPU, memory, running tasks, and load average.

## Service Checks

Service inspected: `nginx`

### Command 3

```bash
systemctl status nginx --no-pager
```

Output:

```text
PASTE YOUR OUTPUT HERE
```

Note:
The nginx service is `active (running)`. This means nginx is currently running successfully as a systemd service.

### Command 4

```bash
systemctl list-units --type=service --state=running | head
```

Output:

```text
PASTE YOUR OUTPUT HERE
```

Note:
This command lists running systemd services. It helps to quickly see which services are active on the system.

## Log Checks

### Command 5

```bash
journalctl -u nginx --no-pager | tail
```

Note:
This command shows recent logs for the nginx service. Logs are useful for checking errors, restarts, and service behavior.

### Command 6

```bash
sudo tail -n 20 /var/log/nginx/access.log
```

Output:

```text
PASTE YOUR OUTPUT HERE
```

Note:
This command shows the last lines of the nginx access log. It can help confirm whether nginx received local or external requests.

## Mini Troubleshooting Steps

Goal: Check if nginx is running and responding.

1. Check the service status:

```bash
systemctl status nginx --no-pager
```

Result: nginx was `active (running)`.

2. Check recent service logs:

```bash
journalctl -u nginx --no-pager | tail
```

Result: I could inspect recent nginx log entries.

3. Test if nginx responds locally:

```bash
curl localhost
```

Result: If HTML output appears, nginx is responding correctly.

## What I Learned

I learned how to inspect running processes, check a systemd service, and read service logs. This is important for DevOps because troubleshooting often starts with checking whether a process or service is running and what the logs say.


