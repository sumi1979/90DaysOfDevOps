# Day 04 – Linux Practice: Processes and Services

## Process Checks

### Command 1

```bash
ps aux | head
```

Output:

```text
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.1  23340 14028 ?        Ss   Jun13   0:42 /sbin/init splash
root           2  0.0  0.0      0     0 ?        S    Jun13   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    Jun13   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   Jun13   0:00 [kworker/R-rcu_gp]
root           5  0.0  0.0      0     0 ?        I<   Jun13   0:00 [kworker/R-sync_wq]
root           6  0.0  0.0      0     0 ?        I<   Jun13   0:00 [kworker/R-kvfree_rcu_reclaim]
root           7  0.0  0.0      0     0 ?        I<   Jun13   0:00 [kworker/R-slub_flushwq]
root           8  0.0  0.0      0     0 ?        I<   Jun13   0:00 [kworker/R-netns]
root          10  0.0  0.0      0     0 ?        I<   Jun13   0:00 [kworker/0:0H-events_highpri]
```

Note:
This command shows running processes. I noticed that PID 1 is `/sbin/init`, which is the first process started by the system. I also saw kernel processes like `kthreadd` and `kworker`.

### Command 2

```bash
top -b -n 1 | head
```

Output:

```text
top - 14:46:19 up 1 day,  8:39,  1 user,  load average: 1.57, 1.55, 1.58
Tasks: 302 total,   1 running, 301 sleeping,   0 stopped,   0 zombie
%Cpu(s): 19.3 us, 12.3 sy,  0.0 ni, 68.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   7779.0 total,   1095.8 free,   4494.6 used,   3451.3 buff/cache     
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   3284.3 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
 100750 sumara-+  20   0   16036   6420   4208 R  26.7   0.1   0:00.10 top
  25295 root      20   0 1460652 261876  76164 S  13.3   3.3  20:26.36 kube-ap+
  11319 sumara-+  20   0 1448.2g 478424 156516 S   6.7   6.0  46:58.74 chrome

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
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
     Active: active (running) since Sat 2026-06-13 06:07:13 CEST; 1 day 8h ago
       Docs: man:nginx(8)
   Main PID: 2205 (nginx)
      Tasks: 5 (limit: 9174)
     Memory: 5.1M (peak: 5.5M)
        CPU: 75ms
     CGroup: /system.slice/nginx.service
             ├─2205 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
             ├─2206 "nginx: worker process"
             ├─2207 "nginx: worker process"
             ├─2208 "nginx: worker process"
             └─2209 "nginx: worker process"

Jun 13 06:07:13 sumara-khan-ThinkPad-T570-W10DG systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
Jun 13 06:07:13 sumara-khan-ThinkPad-T570-W10DG systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.

```

Note:
The nginx service is `active (running)`. This means nginx is currently running successfully as a systemd service.

### Command 4

```bash
systemctl list-units --type=service --state=running | head
```

Output:

```text
  UNIT                          LOAD   ACTIVE SUB     DESCRIPTION
  accounts-daemon.service       loaded active running Accounts Service
  avahi-daemon.service          loaded active running Avahi mDNS/DNS-SD Stack
  bluetooth.service             loaded active running Bluetooth service
  colord.service                loaded active running Manage, Install and Generate Color Profiles
  containerd.service            loaded active running containerd container runtime
  cron.service                  loaded active running Regular background program processing daemon
  cups-browsed.service          loaded active running Make remote CUPS printers available locally
  cups.service                  loaded active running CUPS Scheduler
  dbus.service                  loaded active running D-Bus System Message Bus

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
::1 - - [14/Jun/2026:14:21:28 +0200] "GET / HTTP/1.1" 200 615 "-" "curl/8.5.0"

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


