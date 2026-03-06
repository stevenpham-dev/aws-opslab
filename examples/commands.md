# OpsLab Commands (SSM Session Manager)

This project uses **SSM Session Manager** instead of SSH for secure access.

## Basic system checks

```bash
uname -a
uptime
df -h
free -m
```

## Identify top CPU processes

```bash
top -o %CPU
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head
```

## Nginx checks

```bash
sudo systemctl status nginx --no-pager
curl -I http://localhost
sudo tail -n 50 /var/log/nginx/access.log
sudo tail -n 50 /var/log/nginx/error.log
```

## CPU load test (incident simulation)

If `stress-ng` is installed:

```bash
stress-ng --cpu 2 --timeout 120s
```

Stop early if needed with:

```bash
Ctrl + C
```

## CloudWatch Logs verification

Open **CloudWatch → Log groups** and confirm events are arriving in:

* AWS-OpsLab-nginx-access
* AWS-OpsLab-nginx-error